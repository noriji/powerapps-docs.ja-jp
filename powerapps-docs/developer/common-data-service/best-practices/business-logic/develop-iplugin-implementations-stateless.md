---
title: '詳細: IPlugin の実装をステートレスとして開発する | MicrosoftDocs'
description: IPlugin を実装するクラス メンバーは、データの不整合性やパフォーマンスの問題につながる可能性のある潜在的なスレッドの安全性の問題にさらされます。
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 9/05/2019
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="develop-iplugin-implementations-as-stateless"></a>詳細: IPlugin の実装をステートレスとして開発する

**カテゴリ**: 設計、パフォーマンス

**影響の可能性**: 高い

<a name='symptoms'></a>

## <a name="symptoms"></a>現象

<xref href="Microsoft.Xrm.Sdk.IPlugin?text=IPlugin interface" /> を実装するクラス メンバーは、次の問題につながる可能性のある潜在的なスレッドの安全性の問題にさらされます。

- データの不整合
- 遅いプラグイン実行

<a name='guidance'></a>

## <a name="guidance"></a>ガイダンス

<xref:Microsoft.Xrm.Sdk.IPlugin> を実装するときに、メンバー フィールドとプロパティーを使用せず、ステートレス操作として <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*> メソッドを書きます。  各起動状態に関する情報はすべて実行コンテキストを経由してのみアクセスする必要があります。  

オーバーロードされたコンストラクタによって提供された構成パラメータから取得したデータでない限り、現在または次回のプラグイン起動中にメンバー フィールドまたはプロパティに実行状態データを格納しようとしないでください。

AppDomain イベントに登録するコードを使用しないでください。 プラグイン ロジックは、AppDomain イベントやプロパティに依存するべきではありません。これは、プラグイン インフラストラクチャの内部実装が、任意の時点での実行動作を変更できるからです。 コードがある時点で機能したとしても、障害を引き起こす可能性があります。

読み取り専用、静的、固定のメンバーは本来スレッド セーフであり、プラグイン クラス内でも確実に使用できます。 次は、スレッド セーフのプラグインを維持する方法についてのいくつかの例です。

- 一定のフィールド メンバー

    ```csharp
    public class Valid_ClassConstantMember : IPlugin
    {
        public const string validConstantMember = "Plugin registration not valid for {0} message.";

        public void Execute(IServiceProvider serviceProvider)
        {
            var context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));

            if (context.MessageName.ToLower() != "create")
                throw new InvalidPluginExecutionException(String.Format(Valid_ClassConstantMember.validConstantMember, context.MessageName));
        }
    }
    ```

- 割り当てられているか、または設定された構成データをプラグイン クラス コンストラクターに保存
    ```csharp
    public class Valid_ClassFieldConfigMember : IPlugin
    {
        private string validConfigField;

        public Valid_ClassFieldConfigMember(string unsecure, string secure)
        {
            this.validConfigField = !String.IsNullOrEmpty(secure)
                ? unsecure
                : secure;
        }

        public void Execute(IServiceProvider serviceProvider)
        {
            if (!String.IsNullOrEmpty(this.validConfigField))
            {
                var message = ValidHelperMethod();
            }
        }

        private string ValidHelperMethod()
        {
            return String.Format("{0} is the config value.", this.validConfigField);
        }
    }
    ```

- ステートレス メソッドの実装

    ```csharp
    public class Valid_ClassStatelessMethodMember : IPlugin
    {
        public void Execute(IServiceProvider serviceProvider)
        {
            var context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
    
            if (ValidMemberMethod(context))
            {
                //Then continue with execution
            }
        }
    
        private bool ValidMemberMethod(IPluginExecutionContext context)
        {
            if (context.MessageName.ToLower() == "create")
                return true;
            else
                return false;
        }
    }
    ```

<a name='problem'></a>

## <a name="problematic-patterns"></a>問題となるパターン

> [!WARNING]
> これらのパターンは、回避する必要があります。

- プラグイン実行中にプラグイン クラス フィールドのメンバーを割り当てる
 
    ```csharp
    public class Violation_ClassAssignFieldMember : IPlugin
    {
        //The instance member used in multiple violation patterns
        internal IOrganizationService service = null;
        internal IPluginExecutionContext context = null;
    
        public void Execute(IServiceProvider serviceProvider)
        {
            this.context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
            var factory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    
            //The violation
            this.service = factory.CreateOrganizationService(this.context.UserId);
    
            //Invoke another violation in method member
            AccessViolationProperties();
        }
    
        private void AccessViolationProperties()
        {
            //Accessing the context and service fields exposes this IPlugin implementation to thread-safety issues
            var entity = new Entity("task");
            entity["regardingid"] = new EntityReference(this.context.PrimaryEntityName, this.context.PrimaryEntityId);
    
            var id = this.service.Create(entity);
        }
    }
    ```

- プラグイン実行中にプラグイン クラス プロパティのメンバーを設定する

    ```csharp
    public class Violation_ClassAssignPropertyMember : IPlugin
    {
        //The instance member used in multiple violation patterns
        internal IOrganizationService Service { get; set; }
        internal IPluginExecutionContext Context { get; set; }
    
        public void Execute(IServiceProvider serviceProvider)
        {
            this.Context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
            var factory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    
            //The violation
            this.Service = factory.CreateOrganizationService(context.UserId);
    
            //Invoke another violation in method member
            AccessViolationProperties();
        }
    
        private void AccessViolationProperties()
        {
            //Accessing the Context and Service properties exposes this IPlugin implementation to thread-safety issues
            var entity = new Entity("task");
            entity["regardingid"] = new EntityReference(this.Context.PrimaryEntityName, this.Context.PrimaryEntityId);
    
            var id = this.Service.Create(entity);
        }
    }
    ```

<a name='additional'></a>

## <a name="additional-information"></a>追加情報

Common Data Services がプラグイン クラスをインスタンス化した後、プラットフォームは、パフォーマンス上の理由からそのプラグイン インスタンスをキャッシュします。 プラグイン インスタンスがキャッシュに格納される時間の長さは、プラットフォームによって管理されます。  プラグイン登録のプロパティの変更など特定の操作は、キャッシュを更新するためのプラットフォームの通知をトリガーします。  次のシナリオでは、プラグインは再初期化されます。

プラットフォームは、プラグイン クラス インスタンスをキャッシュしているので、コンストラクタはプラグイン実行のすべての呼び出しを求められません。  したがって、IPluginの実装は、静的構成データの取得以外にコンストラクター内の操作のタイミングに依存するべきではありません。 

IPlugins がステートレスでなければならないもう 1 つの理由は、複数のシステム スレッドが同じ共有プラグイン インスタンスを同時に実行する可能性があるからです。  このことにより、IPlugin を実装するクラス メンバは、データの不整合性やパフォーマンスの問題につながる可能性のある潜在的なセキュリティの問題にさらされます。

<a name='seealso'></a>

### <a name="see-also"></a>関連項目

[プラグインを記述する](../../write-plug-in.md)<br />
[CRMチームのブログ: プラグインのスレッドの安全性](http://blogs.msdn.com/b/crm/archive/2008/11/18/member-static-variable-and-thread-safety-in-plug-in-for-crm-4-0.aspx)<br />
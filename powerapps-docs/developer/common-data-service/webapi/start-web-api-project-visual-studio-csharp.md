---
title: 'Visual Studio (C#) で Common Data Service Web API プロジェクトを起動 (Common Data Service)| MicrosoftDocs'
description: Common Data Service Web APIを使用するコンソール アプリケーションを構築するために Visual Studio で新しいプロジェクトを作成します。
ms.custom: null
ms.date: 04/22/2019
ms.reviewer: null
ms.service: powerapps
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: get-started-article
ms.assetid: F96B384D-EF70-490D-BE3D-2E3883278B99
caps.latest.revision: 14
author: JimDaly
ms.author: jdaly
manager: annbe
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="start-a-common-data-service-web-api-project-in-visual-studio-c"></a>Visual Studio (C#) で Common Data Service Web API プロジェクトを使う

このトピックでは、Common Data Service Web API を使用するコンソール アプリケーションを構築する Visual Studio 2017 で新しいプロジェクトを作成する方法を説明します。 SDK C# サンプルを含む多くのアプリケーションが、Web API ベースのソリューションを実装するのに使用する共通の参照およびプロジェクトのリソースを説明します。  
  
<a name="bkmk_prerequisites"></a>   
## <a name="prerequisites"></a>前提条件  
 次の前提条件は、このセクションで説明されているコンソール アプリケーションを作成するのに必要です。  
  
- 開発用コンピューターには Visual Studio 2017 がインストールされています。 [Visual Studio Express](https://www.visualstudio.com/products/visual-studio-express-vs.aspx) など、どのエディションでも Common Data Service Web API は十分に操作できます。
  
- 次の NuGet クライアントをインストールする必要があります: コマンド ライン ユーティリティまたは Visual Studio 拡張。 詳細については、[NuGet のインストール](https://docs.nuget.org/consume/installing-nuget)を参照してください。  
  
<a name="bkmk_createProject"></a>   

## <a name="create-a-project"></a>プロジェクトの作成  
以下の手順では、Microsoft .NET Framework を使用する C# でコンソール アプリケーション プロジェクトを作成する方法を説明します。
  
<a name="bkmk_newProject"></a> 

### <a name="new-project"></a>新しいプロジェクト  
  
1. Visual Studio では、**新しいプロジェクト**をクリックします。 **新しいプロジェクト**ダイアログが表示されます。  
  
2. **テンプレート**の下の左側のナビゲーション ウィンドウで、**Visual C#** を選択します。  
  
3. 使用可能なテンプレートの一覧の上側で、**.NET Framework 4.6.2** を選択します。  
  
4. テンプレートの一覧から **コンソール アプリ (.NET Framework)** を選択します。 (ソリューションに適したプロジェクトの種類を選択してください)。すべての Web API C# はコンソール アプリケーションです。  
  
   ![Common Data Service の新しいコンソール アプリケーション プロジェクト ダイアログ](media/new-project.PNG "Common Data Service の新しいコンソール アプリケーション プロジェクト ダイアログ")  
  
5. フォームの下部近くのテキスト ボックスに、プロジェクトの名前と場所を入力し、[OK] を選択します。 (このトピックでは、ソリューション名「StartWebAPI-CS」が使用されています。) 最初ソリューションのファイルが作成され、ソリューションは Visual Studio に読み込まれます。  
  
6. **プロジェクト**メニューで、プロジェクトのプロパティ フォームを開き、ターゲット フレームワークが **.NET Framework 4.6.2** に設定されていることを確認します。  
  
#### <a name="install-and-verify-the-required-assembly-references"></a>必要なアセンブリ参照をインストールして確認します。  

1. プロジェクトを開いたら、プロジェクト上部のコントロール バーにある **ツール** をクリックします。 **NuGet パッケージ マネージャー** > **パッケージ マネージャー コンソール** を選択し、次の NuGet パッケージをインストールします。

```
install-package Newtonsoft.Json
install-package System.Net.Http
```
2. **ソリューション エクスプローラー**では、**参照**ノードを展開します。  
  
3. 必要なすべての参照がプロジェクトに追加されたことを確認してください。  
  
4. アプリケーション内で定期的に使用する追加機能がある場合は、必要なアセンブリへ関連する参照を追加することができます。 詳細については、「[[参照の追加] ダイアログ ボックスを使用して参照の追加または削除する方法](https://msdn.microsoft.com/library/wkze6zky.aspx)」を参照してください。  
  
   Common Data Service Web API は REST の原則をベースとしているので、クライアント側アセンブリがアクセスする必要はありません。  ただし、Common Data Service アプリでサポートされる他の API にはこれらが必要です。
  
#### <a name="add-typical-using-statements"></a>一般的な using ステートメントの追加  
  
1.  **ソリューション エクスプローラー**で、編集に対して **Program.cs** を開きます。  
  
2.  ファイルの先頭に、Common Data Service Web API ベースのソリューションで一般的に使用されている名前空間を参照する、次の `using` ステートメントを追加します。  
  
    ```csharp
    using Newtonsoft.Json;  
    using Newtonsoft.Json.Linq;  
    using System.Net.Http;  
    using System.Net.Http.Headers;
    ```  
  
3.  前のセクションで日常的に使用されているアセンブリまたは参照を追加した場合は、対応する `using` ステートメントをこれらのリソースに対して追加する必要もあります。  
  
4.  ファイルを保存します。  
  
<a name="bkmk_addConnectionCode"></a>
 
### <a name="add-connection-code"></a>つながりコードの追加

このセクションでは、これらの操作を実行する上で基本となる一連の設定と説明を追加する方法について説明します。  
  
#### <a name="edit-the-application-configuration-file"></a>アプリケーション構成ファイルの編集
  
1.  **ソリューション エクスプローラー**で、編集に対して **App.config** ファイルを開きます。  既存の `<startup>` セクションの後に、次の 2 つのセクションをそれに追加し、ファイルを保存します。  
  
    ```xml  
  
    <connectionStrings>  
        <clear />  
  
        <!-- When providing a password, make sure to set the app.config file's security so that only you can read it. -->  
        <add name="default"   connectionString="Url=http://myserver/myorg/; Username=name; Password=password; Domain=domain" />  
        <add name="CrmOnline" connectionString="Url=https://mydomain.crm.dynamics.com/; Username=someone@mydomain.onmicrosoft.com; Password=password" />  
      </connectionStrings>  
  
      <appSettings>  
        <!--For information on how to register an app and obtain the ClientId and RedirectUrl  
            values see https://msdn.microsoft.com/dynamics/crm/mt149065 -->  
        <!--Active Directory application registration. -->  
        <!--These are dummy values and should be replaced with your actual app registration values.-->  
        <add key="ClientId" value="e5cf0024-a66a-4f16-85ce-99ba97a24bb2" />  
        <add key="RedirectUrl" value="http://localhost/SdkSample" />  
  
        <!-- Use an alternate configuration file for connection string and setting values. This optional setting  
        enables use of an app.config file shared among multiple applications. If the specified file does  
        not exist, this setting is ignored.-->  
        <add key="AlternateConfig" value="C:\Temp\crmsample.exe.config"/>  
      </appSettings>  
  
    ```  
  
2.  ソリューションを開発または展開している時、実際の接続およびアプリケーションの登録値は例のプレースホルダーの値に対して置換する必要があります。  
  
### <a name="next-steps"></a>次のステップ

 この時点では、エラーなしでソリューションを作成できます。 アプリケーション構成ファイルを編集し、Dynamics 365 Server に対して値を入力する場合は、プログラムがそのサーバーに正常に接続される必要もあります。 ソリューションは、Common Data Service Web API への呼び出しを含め、カスタム コードを承諾する準備が整っている骨格フレームを表します。  
  
> [!TIP]
>  このトピックを閉じる前に、プロジェクト テンプレートとしてプロジェクトを保存することを検討します。 次に、今後の学習プロジェクトのためにそのテンプレートを再利用すると、新しいプロジェクトの設定の時間と労力を節約できます。 このため、プロジェクトが Microsoft Visual Studioでオープンしている間に、 **ファイル** メニューで、**テンプレートのエクスポート**を選択します。 [テンプレート ウィザードのエクスポート](https://msdn.microsoft.com/library/xkh1wxd8.aspx) の指示に従い、テンプレートを作成します。  
  
### <a name="see-also"></a>関連項目

 [Web API (C#) を開始](get-started-dynamics-365-web-api-csharp.md)   
 [Web API Helper Library (C#) の使用](use-microsoft-dynamics-365-web-api-helper-library-csharp.md)   
 [Web API を使用して演算を実行する](perform-operations-web-api.md)
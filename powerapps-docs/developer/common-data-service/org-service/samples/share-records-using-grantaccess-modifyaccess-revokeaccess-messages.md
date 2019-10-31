---
title: 'サンプル: GrantAccess、ModifyAccess、および RevokeAccess を使用したレコードの共有 (Common Data Service) | Microsoft Docs'
description: このサンプルでは、アクセス許可を使用してレコードを共有し、アクセス メッセージを変更および取り消す方法を示します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-share-records-using-grantaccess-modifyaccess-and-revokeaccess-messages"></a>サンプル: GrantAccess、ModifyAccess、および RevokeAccess メッセージを使用したレコードの共有

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-share-records-using-grantaccess-modifyaccess-revokeaccess-messages 

Change sample to make sure it works with Common Data Service
-->

このサンプルは、次のメッセージを使用してレコードを共有する方法を示します。

[GrantAccessRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.grantaccessrequest?view=dynamics-general-ce-9)

[ModifyAccessRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.modifyaccessrequest?view=dynamics-general-ce-9)

[RevokeAccessRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.revokeaccessrequest?view=dynamics-general-ce-9)

サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/GrantModifyRevokeAccess) からダウンロードできます。

このサンプルでは、システムに存在しない追加のユーザーが必要です。 **Office 365** で必要なユーザーを手動で作成し、サンプルがエラーなしで実行されるようにします。 このサンプルでは、次に示す**現状有姿**で 2 つのユーザー プロファイルを作成します。 `yourorg` を組織名で置換します。

**名**: Dan<br/>
**姓**: Wilson<br/>
**セキュリティ ロール**: 代理人<br/>
**ユーザー名**: dwilson@yourorg.onmicrosoft.com<br/>

**名**: Christen<br/>
**姓**: Anderson<br/>
**セキュリティ ロール**: 代理人<br/>
**ユーザー名**: canderson@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

`GrantAccessRequest`、`ModifyAccessRequest`、`RevokeAccessRequest` メッセージは、アクセスを許可、変更、取り消すために必要なデータが含まれているシナリオで使用するためのものです。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

1. 組織の現在のバージョンをチェックします。
2. 名前の競合を回避する一意の識別子を作成します。
3. このサンプルの **Office 365** で手動で作成されたユーザーを取得します。
4. サンプルのチームを作成するためのルート部署を取得します。
5. `WhoAMIRequest` は、現在のユーザー情報を取得します。
6. チームを作成し、ユーザーをチームに追加します。 
7. 取引先企業レコードを作成し、タスク、レターを作成して取引先企業に関連付けます。

### <a name="demonstrate"></a>使用方法

1. 呼び出し元ユーザーが作成された取引先企業に対して持っているアクセス権を取得および表示します。
2. 最初のユーザーが作成された取引先企業に対して持っているアクセス権を取得および表示します。 
3. `GrantAccessRequest` メソッドは、作成された取引先企業に最初のユーザーの `read` アクセスを付与します。
4. `ModifyAccessRequest` メソッドは、作成された取引先企業に最初のユーザーの `delete` アクセスを付与します。
5. `RevokeAccessRequest` メソッドは、作成された取引先企業に最初のユーザーの `revoke` アクセスを付与します。

### <a name="clean-up"></a>クリーン アップ

1. [セットアップ](#setup) で作成されたサンプル データを削除するためのオプションを表示します。

    サンプルで作成されるエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。

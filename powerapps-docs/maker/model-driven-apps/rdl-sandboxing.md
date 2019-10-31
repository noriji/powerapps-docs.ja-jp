---
title: RDL サンドボックス | MicrosoftDocs
ms.custom: null
ms.date: 09/30/2017
ms.reviewer: null
ms.service: crm-online
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement (online)
ms.assetid: 8ec72014-9f0c-4964-ac67-24419b054e91
caps.latest.revision: 13
author: Mattp123
ms.author: matp
manager: amyla
tags:
  - MigrationHO
search.audienceType:
  - customizer
search.app:
  - D365CE
---
# <a name="rdl-sandboxing"></a>RDL サンドボックス 

Common Data Service では、レポートがサンドボックス モードで実行されます。 このためには、SQL Server Reporting Services のレポート定義言語 (RDL) サンドボックスを有効にします。 RDL サンドボックスを使用することで、特定の種類のリソースの使用状況を検出したり、制限したりできます。 結果として、PowerApps モデル駆動型アプリの特定の機能が使用できなくなる場合があります。 詳細については、「[MSDN: RDL サンドボックスの有効化および無効化](https://msdn.microsoft.com/library/ee210591.aspx)」を参照してください。  
  
 Common Data Service での現在の RDL サンドボックス構成の設定について、このトピックのセクションで説明します。  
    
<a name="BKMK_Max"></a>   
## <a name="limits-of-the-array-result-length-and-string-result-length"></a>配列の結果の長さと文字列の結果の長さの制限  
 RDL 式の配列戻り値で許容される項目数の上限値が、250 から 102,400 に増加しました。 RDL 式の文字列戻り値で許容される項目数の上限値も、250 から 102,400 に増加しました。 これにより、最大 75 KB のサイズの画像およびロゴを含めることができるようになり、これは Base64 エンコードを使用するデータベースに格納されます。  
  
 MaxResourceSize は 2000 に設定されます。 これにより、1500 KB までのサイズのレポートを外部イメージとして含めることができます。 詳細: [TechNet: 外部イメージを追加 (Report Builder および SSRS)](https://technet.microsoft.com/library/dd220527.aspx)  
  
<a name="BKMK_Allowed"></a>   
## <a name="allowed-types-and-denied-members"></a>許可される型と拒否メンバー  
 RDL サンドボックス機能を使用して、許可される型の一覧と拒否メンバーの一覧を作成することができます。 許可される型の一覧は、許可一覧と呼ばれます。 RDL 式で許可されない拒否メンバーの一覧は、禁止一覧と呼ばれます。  
  
 次の表に、Common Data Service のサンドボックス モードで使用できる、許可される型と拒否メンバーを示します。  
  
|許可される型|拒否メンバー|  
|-------------------|--------------------|  
|`System.Array`|CreateInstance|  
||Finalize|  
||GetType|  
||MemberwiseClone|  
||サイズ変更|  
|||  
|`System.DateTime`|FromBinary|  
||GetDateTimeFormats|  
||GreaterThan|  
||GreaterThanOrEqual|  
|||  
|||  
|`System.Object`|GetType|  
||MemberwiseClone|  
||ReferenceEquals|  
|||  
|`System.DbNull`|Finalize|  
||MemberwiseClone|  
||GetObjectData|  
||GetTypeCode|  
|||  
|`System.Math`|BigMul|  
||DivRem|  
||IEEERemainder|  
||E|  
||PI|  
||Pow|  
|`System.String`||  
|`System.TimeSpan`|時間|  
||TicksPerDay|  
||TicksPerHour|  
||TicksPerMillisecond|  
||TicksPerMinute|  
||TicksPerSecond|  
||Zero|  
||TryParse|  
||TryParseExact|  
|`System.Convert`|ChangeType|  
||IConvertible.ToBoolean|  
||IConvertible.ToByte|  
||IConvertible.ToChar|  
||IConvertible.ToDateTime|  
||IConvertible.ToDecimal|  
||IConvertible.ToDouble|  
||IConvertible.ToInt16|  
||IConvertible.ToInt32|  
||IConvertible.ToInt64|  
||IConvertible.ToSByte|  
||IConvertible.ToSingle|  
||IConvertible.ToType|  
||IConvertible.ToUInt16|  
||IConvertible.ToUInt32|  
||IConvertible.ToUInt64|  
|`System.StringComparer`|作成​​|  
||Finalize|  
|||  
|`System.TimeZone`|Finalize|  
||GetType|  
||MemberwiseClone|  
|||  
|`System.Uri`|Unescape|  
||解析|  
||Escape|  
||Finalize|  
|||  
|`System.UriBuilder`|Finalize|  
|||  
|`System.Globalization.CultureInfo`|ClearCachedData|  
|||  
|`System.Text.RegularExpressions.Match`|空|  
||NextMatch|  
||結果|  
||同期|  
|||  
|||  
|`System.Text.RegularExpressions.Regex`|CacheSize|  
||CompileToAssembly|  
||GetGroupNames|  
||GetGroupNumbers|  
||GetHashCode|  
||Unescape|  
||UseOptionC|  
||UseOptionR|  
||capnames|  
||caps|  
||capsize|  
||capslist|  
||roptions|  
||pattern|  
||factory|  
||IsMatch|  
||Matches|  
||Iserializable.GetObjectData|  
||InitializeReferences|  
||RightToLeft|  
||オプション​​|  
|||  
|||  
|`Microsoft.VisualBasic.Constants`|vbAbort|  
||vbAbortRetryIgnore|  
||vbApplicationModal|  
||vbArchive|  
||vbBinaryCompare|  
||vbCancel|  
||vbCritical|  
||vbDefaultButton1|  
||vbDefaultButton2|  
||vbDefaultButton3|  
||vbExclamation|  
||vbFormFeed|  
||vbGet|  
||vbHidden|  
||vbHide|  
||vbHiragana|  
||vbIgnore|  
||vbInformation|  
||vbKatakana|  
||vbLet|  
||vbLinguisticCasing|  
||vbMaximizedFocus|  
||vbMinimizedFocus|  
||vbMinimizedNoFocus|  
||vbMsgBoxHelp|  
||vbMsgBoxRight|  
||vbMsgBoxRtlReading|  
||vbMsgBoxSetForeground|  
||vbNo|  
||vbNormal|  
||vbNormalFocus|  
||vbNormalNoFocus|  
||vbObjectError|  
||vbOK|  
||vbOKCancel|  
||vbOKOnly|  
||vbQuestion|  
||vbReadOnly|  
||vbRetry|  
||vbRetryCancel|  
||vbSet|  
||vbSystem|  
||vbSystemModal|  
||VbTypeName|  
||vbVolume|  
||Zero|  
|`Microsoft.VisualBasic.ControlChars`|Finalize|  
||GetType|  
||MemberwiseClone|  
|||  
|`Microsoft.VisualBasic.Conversion`|Err|  
||ErrorToString|  
||Fix|  
|||  
|`Microsoft.VisualBasic.DateInterval`|Finalize|  
||GetType|  
||MemberwiseClone|  
|||  
|`Microsoft.VisualBasic.Financial`|Finalize|  
||GetType|  
||MemberwiseClone|  
||IRR|  
||NPV|  
||MIRR|  
|||  
|||  
|`Microsoft.VisualBasic.Interaction`|AppActivate|  
||Beep|  
||CallByName|  
||Command|  
||CreateObject|  
||Environ|  
||Finalize|  
||GetAllSettings|  
||GetObject|  
||GetSetting|  
||GetType|  
||InputBox|  
||MemberwiseClone|  
||MsgBox|  
||SaveSetting|  
||Shell|  
||選択|  
||切り替え|  
|||  
|||  
|`Microsoft.VisualBasic.Information`|Erl|  
||Err|  
||IsError|  
||IsDBNull|  
||Lbound|  
||Ubound|  
||SystemTypeName|  
|||  
|`Microsoft.VisualBasic.Strings`|Finalize|  
||GetType|  
||MemberwiseClone|  
||Lset|  
||Rset|  
|||  
|`Microsoft.Crm.Reporting.RdlHelper`||  
  
<a name="BKMK_Denied"></a>   
## <a name="common-denied-members"></a>共通の拒否メンバー  
 次の表に、許可される型で共通する拒否メンバーを示します。  
  
||  
|-|  
|DateString|  
|期間|  
|Equality|  
|が次の値と等しい|  
|Erl|  
|フィルター​​|  
|GetChar|  
|GroupNameFromNumber|  
|GroupNumberFromName|  
|Int|  
|MaxValue|  
|MinValue|  
|Negate|  
|Timer|  
|TimeString|  
|ToBinary|  
|Finalize|  
|GetType|  
|MemberwiseClone|  
  


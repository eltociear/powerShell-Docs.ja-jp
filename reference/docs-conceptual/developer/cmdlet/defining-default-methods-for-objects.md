---
title: オブジェクトの既定のメソッドの定義 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365691"
---
# <a name="defining-default-methods-for-objects"></a>オブジェクトの既定のメソッドを定義する

.NET Framework オブジェクトを拡張すると、コードメソッドとスクリプトメソッドをオブジェクトに追加できます。
これらのメソッドの定義に使用される XML については、次のセクションで説明します。

> [!NOTE]
> 次のセクションの例は、Windows PowerShell インストールディレクトリ (`$PSHOME`) の `Types.ps1xml` の種類のファイルに含まれています。 詳細については、「 [types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)」を参照してください。

## <a name="code-methods"></a>コードメソッド

コードメソッドは、.NET Framework オブジェクトの静的メソッドを参照しています。

次の例では、 **ToString**メソッドが[system.xml](/dotnet/api/System.Xml.XmlNode)型に追加されます。 [Pscodemethod](/dotnet/api/system.management.automation.pscodemethod)要素は、拡張メソッドをコードメソッドとして定義します。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)要素は、拡張メソッドの名前を指定します。 また、 [Codereference 参照](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference)要素は静的メソッドを指定します。 [Pscodemethod](/dotnet/api/system.management.automation.pscodemethod)要素を[psmembers](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)要素のメンバーに追加することもできます。

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>スクリプトメソッド

スクリプトメソッドは、値がスクリプトの出力であるメソッドを定義します。 次の例では、 **Converttodatetime**メソッドが[system.management.managementobject](/dotnet/api/System.Management.ManagementObject)型に追加されています。 [Psscriptmethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)要素は、拡張メソッドをスクリプトメソッドとして定義します。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)要素は、拡張メソッドの名前を指定します。 また、 [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script)要素は、メソッド値を生成するスクリプトを指定します。 [Psscriptmethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)要素は、 [psmembers](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)要素のメンバーに追加することもできます。

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a>「

[Windows PowerShell コマンドレットの記述](./writing-a-windows-powershell-cmdlet.md)

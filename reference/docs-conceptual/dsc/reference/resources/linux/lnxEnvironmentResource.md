---
ms.date: 09/20/2019
keywords: DSC, PowerShell, 構成, セットアップ
title: Linux 用 DSC の nxEnvironment リソース
ms.openlocfilehash: 55c1b2402e23c1042ed48b40c1084aa63c515b36
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953229"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>Linux 用 DSC の nxEnvironment リソース

PowerShell Desired State Configuration (DSC) の **nxEnvironment** リソースは、Linux ノード上でシステム環境変数を管理するためのメカニズムを備えています。

## <a name="syntax"></a>構文

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>プロパティ

|プロパティ |説明 |
|---|---|
|名前 |特定の状態を保証する環境変数の名前を示します。 |
|値 |環境変数に割り当てる値。 |
|パス |構成されている環境変数を定義します。 変数が **Path** 変数である場合は、このプロパティを `$true` に設定します。それ以外の場合は、`$false` に設定します。 既定値は `$false` です。 構成されている変数が **Path** 変数である場合は、**Value** プロパティによって提供される値が既存の値に追加されます。 |

## <a name="common-properties"></a>共通プロパティ

|プロパティ |説明 |
|---|---|
|DependsOn |このリソースを構成する前に、他のリソースの構成を実行する必要があることを示します。 たとえば、最初に実行するリソース構成スクリプト ブロックの ID が ResourceName で、そのタイプが ResourceType である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。 |
|Ensure |変数が存在するかどうかをチェックするかどうかを決定します。 変数の存在を保証するには、このプロパティを **Present** に設定します。 変数が存在しないことを保証するには、**Absent** に設定します。 既定値は **Present** です。 |

## <a name="additional-information"></a>追加情報

- **Path** がないか、または `$false` に設定されている場合、環境変数は、`/etc/environment` で管理されます。
  プログラムまたはスクリプトに、`/etc/environment` ファイルを取得して、管理対象の環境変数にアクセスする構成が必要である場合があります。
- **Path** が `$true` に設定されている場合、環境変数はファイル `/etc/profile.d/DSCenvironment.sh` で管理されます。 このファイルが存在しない場合は作成されます。 **Ensure**が **Absent** に設定され、**Path** が `$true` に設定されている場合、既存の環境変数は `/etc/profile.d/DSCenvironment.sh` からのみ削除され、他のファイルからは削除されません。

## <a name="example"></a>例

次の例は、**nxEnvironment** リソースを使用して、**TestEnvironmentVariable** が存在し、値 "Test-Value" が指定されることを保証する方法を示しています。 **TestEnvironmentVariable** が存在しない場合は、作成されます。

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
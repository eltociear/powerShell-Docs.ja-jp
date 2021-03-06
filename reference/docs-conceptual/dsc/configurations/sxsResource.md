---
ms.date: 06/12/2017
keywords: DSC, PowerShell, 構成, セットアップ
title: インストールされているリソースの特定のバージョンをインポートする
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953989"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>インストールされているリソースの特定のバージョンをインポートする

> 適用先:Windows PowerShell 5.0

PowerShell 5.0 では、DSC リソースの異なるバージョンを 1 台のコンピューターにサイド バイ サイドでインストールできます。 リソース モジュールでは、異なるバージョンのリソースをバージョンの名前のフォルダーに格納できます。

## <a name="installing-separate-resource-versions-side-by-side"></a>リソースの異なるバージョンのサイド バイ サイド インストール

[Install-Module](/powershell/module/PowershellGet/Install-Module) コマンドレットの **MinimumVersion**、**MaximumVersion**、**RequiredVersion** の各パラメーターを使用すると、インストールするモジュールのバージョンを指定できます。 バージョンを指定せずに **Install-Module** を呼び出すと、最新バージョンがインストールされます。

たとえば、**xFailOverCluster** モジュールのバージョンが複数あり、それぞれに **xCluster** リソースが含まれているとします。 バージョン番号を指定しないで **Install-Module** を呼び出すと、最新バージョンのモジュールがインストールされます。

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

特定のバージョンのモジュールをインストールするには、**RequiredVersion** を 1.1.0.0 と指定します。 これにより、指定したバージョンがインストールされているバージョンとサイド バイ サイドでインストールされます。

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

`Get-DSCResource` を使うと、両方のバージョンのモジュールが一覧に表示されるようになります。

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>構成でのリソース バージョンの指定

コンピューターに異なるバージョンのリソースがインストールされている場合は、構成でリソースを使うときに、そのリソースのバージョンを指定する必要があります。 これを行うには、**Import-DscResource** キーワードの **ModuleVersion** パラメーターを指定します。 複数のバージョンがインストールされているリソースのリソース モジュールのバージョンを指定しないと、構成によってエラーが生成されます。

次の構成は、呼び出すリソースのバージョンを指定する方法を示しています。

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

>注: Import-DscResource の ModuleVersion パラメーターは PowerShell 4.0 では使用できません。 PowerShell 4.0 では、Import-DscResource の ModuleName パラメーターにモジュール指定オブジェクトを渡すことで、モジュールのバージョンを指定できます。 モジュール指定オブジェクトは、ModuleName キーと RequiredVersion キーを含むハッシュ テーブルです。 たとえば、次のように入力します。

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

これは PowerShell 5.0 でも動作しますが、PowerShell 5.0 では、**ModuleVersion** パラメーターを使用することをお勧めします。

## <a name="see-also"></a>関連項目

- [DSC 構成](configurations.md)
- [DSC リソース](../resources/resources.md)

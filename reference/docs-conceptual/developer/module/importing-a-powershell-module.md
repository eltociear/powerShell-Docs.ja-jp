---
title: PowerShell モジュールのインポート |Microsoft Docs
ms.custom: ''
ms.date: 02/03/2020
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: d5ce61a1cba1d91c130394c5cf7249021e95f485
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996028"
---
# <a name="importing-a-powershell-module"></a>PowerShell モジュールをインポートする

システムにモジュールをインストールしたら、モジュールをインポートすることができます。 インポートとは、ユーザーが PowerShell セッションでそのモジュールにアクセスできるように、モジュールをアクティブメモリに読み込むプロセスです。 PowerShell 2.0 では、新しくインストールされた PowerShell モジュールを import [-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)コマンドレットの呼び出しを使用してインポートできます。 PowerShell 3.0 では、モジュール内の関数またはコマンドレットのいずれかがユーザーによって呼び出されたときに、PowerShell は暗黙的にモジュールをインポートできます。 どちらのバージョンも、PowerShell が検出できる場所にモジュールをインストールすることを前提としています。詳細については、「 [PowerShell モジュールのインストール](./installing-a-powershell-module.md)」を参照してください。
モジュールマニフェストを使用して、モジュールのどの部分をエクスポートするかを制限できます。また、`Import-Module` 呼び出しのパラメーターを使用して、インポートする部分を制限できます。

## <a name="importing-a-snap-in-powershell-10"></a>スナップインのインポート (PowerShell 1.0)

モジュールが PowerShell 1.0 に存在しませんでした。代わりに、スナップインを登録して使用する必要がありました。ただし、モジュールをインストールしてインポートする方が一般的であるため、このテクノロジはこの時点では使用しないことをお勧めします。 詳細については、「 [Windows PowerShell スナップインを作成する方法](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)」を参照してください。

## <a name="importing-a-module-with-import-module-powershell-20"></a>インポートモジュールを使用したモジュールのインポート (PowerShell 2.0)

PowerShell 2.0 では、適切に指定された[インポートモジュール](/powershell/module/Microsoft.PowerShell.Core/Import-Module)コマンドレットを使用してモジュールをインポートします。 このコマンドレットを実行すると、Windows PowerShell は、`PSModulePath` 変数で指定されたディレクトリ内で指定されたモジュールを検索します。 指定されたディレクトリが見つかった場合、Windows PowerShell は、モジュールマニフェストファイル (.psd1)、スクリプトモジュールファイル (hbase-runner.psm1)、バイナリモジュールファイル (.dll) の順にファイルを検索します。 検索にディレクトリを追加する方法の詳細については、「 [PSModulePath のインストールパスの変更](./modifying-the-psmodulepath-installation-path.md)」を参照してください。
次のコードは、モジュールをインポートする方法を示しています。

```powershell
Import-Module myModule
```

MyModule が `PSModulePath`に配置されていると仮定すると、PowerShell は myModule をアクティブなメモリに読み込みます。 MyModule が `PSModulePath` パスに存在しない場合でも、その場所を見つけるために、PowerShell に明示的に指示することができます。

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

`-Verbose` パラメーターを使用して、モジュールからエクスポートされる内容と、アクティブなメモリにインポートされる内容を識別することもできます。 エクスポートとインポートはどちらも、ユーザーに公開されるものを制限します。違いは、表示を制御しているユーザーです。 基本的に、エクスポートはモジュール内のコードによって制御されます。 これに対し、インポートは `Import-Module` 呼び出しによって制御されます。 詳細については、以下の「**インポートされるメンバーの制限**」を参照してください。

## <a name="implicitly-importing-a-module-powershell-30"></a>モジュールを暗黙的にインポートする (PowerShell 3.0)

Windows PowerShell 3.0 以降、モジュールのコマンドレットまたは関数をコマンドで使用すると、モジュールは自動的にインポートされます。 この機能は、 **PSModulePath**環境変数の値に含まれているディレクトリ内の任意のモジュールに対して機能します。 ただし、モジュールを有効なパスに保存しない場合でも、上記の明示的な[モジュール](/powershell/module/Microsoft.PowerShell.Core/Import-Module)を使用して読み込むことができます。

次のアクションを実行すると、モジュールの自動インポートがトリガーされます ("モジュールの自動読み込み" とも呼ばれます)。

- コマンドでコマンドレットを使用します。 たとえば、「」と入力すると、`Get-ExecutionPolicy` コマンドレットを含む `Get-ExecutionPolicy` がインポートされます。

- コマンドを取得する[には、コマンドレットを](/powershell/module/Microsoft.PowerShell.Core/Get-Command)使用します。 たとえば、「`Get-Command Get-JobTrigger`」と入力すると、`Get-JobTrigger` コマンドレットを含む**Psscheduledjob**モジュールがインポートされます。 ワイルドカード文字を含む `Get-Command` コマンドは検出と見なされ、モジュールのインポートはトリガーされません。

- コマンドレットのヘルプを取得するには、 [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help)コマンドレットを使用します。 たとえば、「」と入力すると、`Get-WinEvent` コマンドレットを含む `Get-Help Get-WinEvent` がインポートされます。

モジュールの自動インポートをサポートするために、`Get-Command` コマンドレットは、モジュールがセッションにインポートされていない場合でも、インストールされているすべてのモジュールのすべてのコマンドレットと関数を取得します。 詳細については、[コマンド](/powershell/module/Microsoft.PowerShell.Core/Get-Command)レットのヘルプトピックを参照してください。

## <a name="the-importing-process"></a>インポート処理

モジュールがインポートされると、モジュールの新しいセッション状態が作成され、 [PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo)オブジェクトがメモリ内に作成されます。 インポートされたモジュールごとにセッション状態が作成されます (これには、ルートモジュールと入れ子になったモジュールが含まれます)。 ルートモジュールからエクスポートされたメンバー (入れ子になったモジュールによってルートモジュールにエクスポートされたメンバーも含む) は、呼び出し元のセッション状態にインポートされます。

モジュールからエクスポートされたメンバーのメタデータには、ModuleName プロパティがあります。 このプロパティには、エクスポートしたモジュールの名前が設定されます。

> [!WARNING]
> エクスポートされたメンバーの名前が未承認の動詞を使用する場合、またはメンバーの名前が制限付きの文字を使用する場合は、[モジュールのインポート](/powershell/module/Microsoft.PowerShell.Core/Import-Module)コマンドレットの実行時に警告が表示されます。

既定では、[モジュールのインポート](/powershell/module/Microsoft.PowerShell.Core/Import-Module)コマンドレットは、パイプラインにオブジェクトを返しません。 ただし、このコマンドレットでは、インポートされるモジュールごとに[PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo)オブジェクトを返すために使用できる**PassThru**パラメーターがサポートされています。 出力をホストに送信するには、ユーザーが[書き込みホスト](/powershell/module/Microsoft.PowerShell.Utility/Write-Host)コマンドレットを実行する必要があります。

## <a name="restricting--the-members-that-are-imported"></a>インポートされるメンバーの制限

モジュールを[インポートモジュール](/powershell/module/Microsoft.PowerShell.Core/Import-Module)のコマンドレットを使用してインポートすると、既定では、エクスポートされたすべてのモジュールメンバーがセッションにインポートされます。これには、入れ子になったモジュールによってモジュールにエクスポートされたコマンドも含まれます。 既定では、変数および別名はエクスポートされません。 エクスポートされるメンバーを制限するには、[モジュールマニフェスト](./how-to-write-a-powershell-module-manifest.md)を使用します。
インポートされるメンバーを制限するには、`Import-Module` コマンドレットの次のパラメーターを使用します。

- **関数**: このパラメーターは、エクスポートされる関数を制限します。 (モジュールマニフェストを使用している場合は、FunctionsToExport キーを参照してください)。

- `**コマンドレット**: このパラメーターでは、エクスポートされるコマンドレットを制限します (モジュールマニフェストを使用している場合は、コマンドレット stoexport キーを参照してください)。

- **Variable**: このパラメーターは、エクスポートされる変数を制限します (モジュールマニフェストを使用している場合は、Variables stoexport キーを参照してください)。

- **エイリアス**: このパラメーターでは、エクスポートされるエイリアスを制限します (モジュールマニフェストを使用している場合は、「Are Asestoexport キー」を参照してください)。

## <a name="see-also"></a>関連項目

[Windows PowerShell モジュールの作成](./writing-a-windows-powershell-module.md)

---
title: コマンドレットコードの例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364501"
---
# <a name="examples-of-cmdlet-code"></a>コマンドレット コードの例

このセクションには、独自のコマンドレットの記述を開始するために使用できるコマンドレットコードの例が含まれています。

> [!IMPORTANT]
> コマンドレットを記述するための詳細な手順については、[コマンドレットの作成に関するチュートリアル](./tutorials-for-writing-cmdlets.md)を参照してください。

## <a name="in-this-section"></a>このセクションの内容

[方法: 簡単なコマンドレットを記述する](./how-to-write-a-simple-cmdlet.md)この例は、コマンドレットコードの基本的な構造を示しています。

[コマンドレットのパラメーターを宣言する方法](./how-to-declare-cmdlet-parameters.md)この例では、さまざまな種類のパラメーターを宣言する方法を示します。

[パラメーターセットを宣言する方法](./how-to-declare-parameter-sets.md)この例では、コマンドレットで実行されるアクションを変更できるパラメーターのセットを宣言する方法を示します。

[パラメーター入力を検証する方法](./how-to-validate-parameter-input.md)これらの例では、パラメーター入力を検証する方法を示します。

[動的パラメーターを宣言する方法](./how-to-declare-dynamic-parameters.md)この例では、実行時に追加されるパラメーターを宣言する方法を示します。

[コマンドレット内でスクリプトを呼び出す方法](./how-to-invoke-scripts-within-a-cmdlet.md)この例は、コマンドレットに指定されたスクリプトを呼び出す方法を示しています。

[入力処理メソッドをオーバーライドする方法](./how-to-override-input-processing-methods.md)これらの例は、BeginProcessing メソッド、ProcessRecord メソッド、および EndProcessing メソッドをオーバーライドするために使用される基本構造を示しています。

[呼び出しの処理をサポートする方法](./how-to-request-confirmations.md)この例では、コマンドレット内から、[システムの管理](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)、............................... コマンド[レットを呼び出す](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法を示します。

[トランザクションをサポートする方法](./how-to-support-transactions.md)この例では、コマンドレットがトランザクションをサポートしていることを示し、コマンドレットがトランザクション内で使用されている場合に実行されるアクションを実装する方法を示します。

[ジョブをサポートする方法](./how-to-support-jobs.md)この例では、コマンドレットを記述するときにジョブをサポートする方法を示します。

[コマンドレット内からコマンドレットを呼び出す方法](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)この例では、別のコマンドレット内からコマンドレットを呼び出す方法を示します。このコマンドレットを使用すると、開発中のコマンドレットに、呼び出されたコマンドレットの機能を追加できます。

## <a name="see-also"></a>参照

[Windows PowerShell コマンドレットの記述](./writing-a-windows-powershell-cmdlet.md)

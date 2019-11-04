---
title: コマンドレットのパラメーター |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365931"
---
# <a name="cmdlet-parameters"></a>コマンドレットのパラメーター

コマンドレットのパラメーターは、コマンドレットが入力を受け入れることができるメカニズムを提供します。 パラメーターでは、コマンドラインから直接入力を受け取ることも、パイプラインを介してコマンドレットに渡されたオブジェクトから入力を受け入れることもできます。これらのパラメーターの引数 (*値*とも呼ばれます) は、コマンドレットが受け入れる入力を指定できます。アクションと、このコマンドレットによってパイプラインに返されるデータ。

## <a name="in-this-section"></a>このセクションの内容

[パラメーターとしてのプロパティの宣言](./declaring-properties-as-parameters.md)コマンドレットのパラメーターを宣言する前に理解しておく必要がある基本情報について説明します。

[コマンドレットパラメーターの型](./types-of-cmdlet-parameters.md)コマンドレットで宣言できるさまざまな種類のパラメーターについて説明します。

[コマンドレットのパラメーター名と機能のガイドライン](./standard-cmdlet-parameter-names-and-types.md)Discuses は、標準パラメーターの名前、推奨されるデータ型、および機能を入力します。

[パラメーターの別名](./parameter-aliases.md)パラメーターに対して定義できるエイリアスについて説明します。

[共通パラメーター名](./common-parameter-names.md)このトピックでは、Windows PowerShell によってコマンドレットに追加されるパラメーターについて説明します。

[コマンドレットのパラメーターセット](./cmdlet-parameter-sets.md)パラメーターセットを使用して、さまざまなシナリオでさまざまなアクションを実行できる単一のコマンドレットを作成する方法について説明します。

[コマンドレット動的パラメーター](./cmdlet-dynamic-parameters.md)特別な条件下でユーザーが使用できるパラメーターについて説明します。

[コマンドレットパラメーターでのワイルドカード文字のサポート](./supporting-wildcard-characters-in-cmdlet-parameters.md)リソースグループに対して実行されるコマンドレットを設計するときに、ワイルドカード文字のサポートを提供する方法について説明します。

[パラメーター入力の検証](./validating-parameter-input.md)コマンドレットパラメーターに渡された引数を Windows PowerShell が検証する方法について説明します。

[入力フィルターパラメーター](./input-filter-parameters.md)コマンドレットによって影響を与える入力オブジェクトのセットをフィルター処理する、`Filter`、@no__t 2、および `Exclude` のパラメーターについて説明します。

## <a name="related-sections"></a>関連セクション

[パラメーター入力を検証する方法](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>参照

[パラメーター属性の宣言](./parameter-attribute-declaration.md)

[Windows PowerShell コマンドレット](./cmdlet-overview.md)
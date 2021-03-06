---
title: CustomControl (Format) の EntrySelectedBy の SelectionCondition 要素Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368441"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>CustomControl の EntrySelectedBy の SelectionCondition 要素 (書式)

コントロール定義を使用するために存在する必要がある条件を定義します。 この要素は、カスタムコントロールビューを定義するときに使用されます。

Configuration 要素 (Format) ViewDefinitions 要素 (書式) ビュー要素 (形式) の CustomControl 要素を表示するための CustomControl for ビュー (形式) の Custommentry 要素の CustomControl for View (Format) CustomEntry for CustomControl 用の CustomItem 要素を使用して、CustomEntry for CustomControl for view (format) の EntrySelectedBy 要素の EntrySelectedBy for CustomControl for View (format) を指定します。

## <a name="syntax"></a>構文

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>属性と要素

次のセクションでは、`SelectionCondition` 要素の属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

なし。

### <a name="child-elements"></a>子要素

|要素|[説明]|
|-------------|-----------------|
|[CustomControl for ビュー (Format) の SelectionCondition の PropertyName 要素](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|省略可能な要素です。<br /><br /> 条件をトリガーする .NET プロパティを指定します。|
|[CustomControl for ビュー (Format) の SelectionCondition の ScriptBlock 要素](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|省略可能な要素です。<br /><br /> 条件をトリガーするスクリプトを指定します。|
|[View (Format) のカスタムコントロールの SelectionCondition の SelectionSetName 要素](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|省略可能な要素です。<br /><br /> 条件をトリガーする .NET 型のセットを指定します。|
|[CustomControl for ビュー (Format) の SelectionCondition の TypeName 要素](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|省略可能な要素です。<br /><br /> 条件をトリガーする .NET 型を指定します。|

### <a name="parent-elements"></a>親要素

|要素|[説明]|
|-------------|-----------------|
|[CustomEntry for CustomControl for View (Format) の EntrySelectedBy 要素](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|このコントロール定義を使用する .NET 型、またはこの定義を使用するために必要な条件を定義します。|

## <a name="remarks"></a>コメント

選択条件を定義する場合は、次の要件が適用されます。

- 選択条件には、少なくとも1つのプロパティ名またはスクリプトブロックを指定する必要がありますが、両方を指定することはできません。

- 選択条件では、任意の数の .NET 型または選択セットを指定できますが、両方を指定することはできません。

選択条件の使用方法の詳細については、「[データを表示するときの条件の定義](./defining-conditions-for-displaying-data.md)」を参照してください。

## <a name="see-also"></a>参照

[CustomControl for ビュー (Format) の SelectionCondition の PropertyName 要素](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomControl for ビュー (Format) の SelectionCondition の ScriptBlock 要素](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[View (Format) のカスタムコントロールの SelectionCondition の SelectionSetName 要素](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomControl for ビュー (Format) の SelectionCondition の TypeName 要素](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomEntry for CustomControl for View (Format) の EntrySelectedBy 要素](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[PowerShell フォーマットファイルの作成](./writing-a-powershell-formatting-file.md)

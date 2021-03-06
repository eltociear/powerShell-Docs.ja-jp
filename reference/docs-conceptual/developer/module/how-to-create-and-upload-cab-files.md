---
title: CAB ファイルを作成およびアップロードする方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367331"
---
# <a name="how-to-create-and-upload-cab-files"></a>CAB ファイルを作成してアップロードする方法

このトピックでは、更新可能なヘルプ CAB ファイルを作成し、更新可能なヘルプのコマンドレットで検出できる場所にアップロードする方法について説明します。

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>更新可能なヘルプ CAB ファイルを作成およびアップロードする方法

更新可能なヘルプ機能を使用して、複数の言語とカルチャのモジュールの新しいヘルプファイルまたは更新されたヘルプファイルを配信できます。 モジュールの更新可能なヘルプパッケージは、1つの HelpInfo XML ファイルと1つ以上のキャビネット () で構成されています。CAB) ファイル。 各 CAB ファイルには、モジュールのヘルプファイルが1つの UI カルチャで含まれています。 更新可能なヘルプ用の CAB ファイルを作成するには、次の手順に従います。

1. モジュールのヘルプファイルを UI カルチャで整理します。 更新可能な各ヘルプ CAB ファイルには、1つの UI カルチャの1つのモジュールのヘルプファイルが含まれています。 モジュールに対して複数のヘルプ CAB ファイルを配信できます。それぞれ異なる UI カルチャを対象としています。

2. ヘルプファイルに、更新可能なヘルプで許可されているファイルの種類だけが含まれていること、およびヘルプファイルスキーマに対して検証されていることを確認します。 `Update-Help` コマンドレットで、無効なファイルや許可されていない種類のファイルが検出された場合、無効なファイルはインストールされず、CAB からのファイルのインストールが停止します。 許可されるファイルの種類の一覧については、「[更新可能なヘルプ CAB ファイルで許可](./file-types-permitted-in-an-updatable-help-cab-file.md)されているファイルの種類」を参照してください。

3. ヘルプファイルにデジタル署名します。 デジタル署名は必須ではありませんが、ベストプラクティスです。

4. 新しいまたは変更されたファイルだけでなく、そのモジュールのすべてのヘルプファイルを UI カルチャに含めます。 CAB ファイルが不完全な場合は、ヘルプファイルを初めてダウンロードしたユーザー、またはすべての更新プログラムをダウンロードしていないユーザーは、モジュールのヘルプファイルをすべて保持できません。

5. MakeCab などのキャビネットファイルを作成するユーティリティを使用します。 Windows PowerShell には、CAB ファイルを作成するコマンドレットは含まれていません。

6. CAB ファイルに名前を指定します。 詳細については、「[更新可能なヘルプ CAB ファイルに名前を指定する方法](./how-to-name-an-updatable-help-cab-file.md)」を参照してください。

7. モジュールの CAB ファイルを、モジュールの HelpInfo XML ファイルの**Helpcontenturi**要素で指定された場所にアップロードします。 次に、モジュールマニフェストの**Helpinfouri**キーによって指定された場所に HelpInfo XML ファイルをアップロードします。 **Helpcontenturi**と**Helpinfouri**は同じ場所を指すことができます。

> [!CAUTION]
> **Helpinfouri**キーと**helpcontenturi**要素の値は、"http" または "https" で始まる必要があります。 値は、インターネット上の場所を示す必要があり、ファイル名を含めることはできません。
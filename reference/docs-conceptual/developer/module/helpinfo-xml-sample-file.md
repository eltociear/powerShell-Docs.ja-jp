---
title: HelpInfo XML サンプルファイル |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6544070f-5549-407f-8603-5df60fe9e013
caps.latest.revision: 7
ms.openlocfilehash: 448cfbce4b387c31ea07fdd31376711f74f5d80c
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995926"
---
# <a name="helpinfo-xml-sample-file"></a>HelpInfo XML サンプル ファイル

このトピックでは、"HelpInfo XML file" と呼ばれる、適切な形式の更新可能なヘルプ情報ファイルのサンプルを示します。 このサンプルファイルでは、ui カルチャの要素は、UI カルチャ名のアルファベット順に並べられています。 アルファベット順の順序がベストプラクティスですが、必須ではありません。

## <a name="helpinfo-xml-sample-file"></a>HelpInfo XML サンプル ファイル

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="https://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>https://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
   <SupportedUICultures>
    <UICulture>
      <UICultureName>de-DE</UICultureName>
      <UICultureVersion>2.15.0.10</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>en-US</UICultureName>
      <UICultureVersion>3.2.0.7</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>it-IT</UICultureName>
      <UICultureVersion>1.1.0.5</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>ja-JP</UICultureName>
      <UICultureVersion>3.2.0.4</UICultureVersion>
    </UICulture>
   </SupportedUICultures>
</HelpInfo>

```
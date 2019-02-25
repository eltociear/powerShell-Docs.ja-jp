---
ms.date: 06/12/2017
keywords: DSC, PowerShell, 構成, セットアップ
title: MSFT_DSCLocalConfigurationManager クラスの StopConfiguration メソッド
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047519"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b9d91-103">MSFT_DSCLocalConfigurationManager クラスの StopConfiguration メソッド</span><span class="sxs-lookup"><span data-stu-id="b9d91-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b9d91-104">進行中の構成の変更を停止します。</span><span class="sxs-lookup"><span data-stu-id="b9d91-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9d91-105">構文</span><span class="sxs-lookup"><span data-stu-id="b9d91-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="b9d91-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b9d91-106">Parameters</span></span>

<span data-ttu-id="b9d91-107">*force* \[in\] **true** の場合、構成を強制的に中止します。</span><span class="sxs-lookup"><span data-stu-id="b9d91-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="b9d91-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="b9d91-108">Return value</span></span>

<span data-ttu-id="b9d91-109">成功した場合は 0 を返します。それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="b9d91-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9d91-110">コメント</span><span class="sxs-lookup"><span data-stu-id="b9d91-110">Remarks</span></span>

<span data-ttu-id="b9d91-111">これは静的メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b9d91-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b9d91-112">要件</span><span class="sxs-lookup"><span data-stu-id="b9d91-112">Requirements</span></span>

<span data-ttu-id="b9d91-113">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b9d91-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b9d91-114">\*\*［名前空間］:Root \microsoft\windows\desiredstateconfiguration</span><span class="sxs-lookup"><span data-stu-id="b9d91-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b9d91-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9d91-115">See also</span></span>

[<span data-ttu-id="b9d91-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b9d91-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
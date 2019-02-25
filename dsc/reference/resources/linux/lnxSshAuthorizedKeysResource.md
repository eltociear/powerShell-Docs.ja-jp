---
ms.date: 06/12/2017
keywords: DSC, PowerShell, 構成, セットアップ
title: Linux 用 DSC の nxSshAuthorizedKeys リソース
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047881"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="05045-103">Linux 用 DSC の nxSshAuthorizedKeys リソース</span><span class="sxs-lookup"><span data-stu-id="05045-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="05045-104">PowerShell Desired State Configuration (DSC) の **nxAuthorizedKeys** リソースは、特定のユーザーの承認された ssh キーを管理するためのメカニズムを備えています。</span><span class="sxs-lookup"><span data-stu-id="05045-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="05045-105">構文</span><span class="sxs-lookup"><span data-stu-id="05045-105">Syntax</span></span>

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="05045-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="05045-106">Properties</span></span>

|  <span data-ttu-id="05045-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="05045-107">Property</span></span> |  <span data-ttu-id="05045-108">説明</span><span class="sxs-lookup"><span data-stu-id="05045-108">Description</span></span> |
|---|---|
| <span data-ttu-id="05045-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="05045-109">KeyComment</span></span>| <span data-ttu-id="05045-110">キーの一意のコメント。</span><span class="sxs-lookup"><span data-stu-id="05045-110">A unique comment for the key.</span></span> <span data-ttu-id="05045-111">これは、キーを一意に識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="05045-111">This is used to uniquely identify keys.</span></span>|
| <span data-ttu-id="05045-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="05045-112">Ensure</span></span>| <span data-ttu-id="05045-113">キーが定義されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="05045-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="05045-114">ユーザーの承認されたキー ファイルにキーが存在しないようにするには、このプロパティに "Absent" を設定します。</span><span class="sxs-lookup"><span data-stu-id="05045-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="05045-115">ユーザーの承認されたキー ファイルにキーが定義されるようにするには、このプロパティに "Present" を設定します。</span><span class="sxs-lookup"><span data-stu-id="05045-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>|
| <span data-ttu-id="05045-116">Username</span><span class="sxs-lookup"><span data-stu-id="05045-116">Username</span></span>| <span data-ttu-id="05045-117">承認された ssh キーを管理するユーザー名。</span><span class="sxs-lookup"><span data-stu-id="05045-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="05045-118">定義されていない場合、既定のユーザーは "root" です。</span><span class="sxs-lookup"><span data-stu-id="05045-118">If not defined, the default user is "root".</span></span>|
| <span data-ttu-id="05045-119">キー</span><span class="sxs-lookup"><span data-stu-id="05045-119">Key</span></span>| <span data-ttu-id="05045-120">キーの内容。</span><span class="sxs-lookup"><span data-stu-id="05045-120">The contents of the key.</span></span> <span data-ttu-id="05045-121">**Ensure** が "Present" に設定されている場合、これは必須です。</span><span class="sxs-lookup"><span data-stu-id="05045-121">This is required if **Ensure** is set to "Present".</span></span>|
| <span data-ttu-id="05045-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="05045-122">DependsOn</span></span> | <span data-ttu-id="05045-123">このリソースを構成する前に、他のリソースの構成を実行する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="05045-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="05045-124">たとえば、最初に実行するリソース構成スクリプト ブロックの **ID** が **ResourceName** で、そのタイプが **ResourceType** である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。</span><span class="sxs-lookup"><span data-stu-id="05045-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="05045-125">例</span><span class="sxs-lookup"><span data-stu-id="05045-125">Example</span></span>

<span data-ttu-id="05045-126">次の例では、ユーザー "monuser" の公開 ssh 承認済みキーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="05045-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```
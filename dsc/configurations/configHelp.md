---
ms.date: 12/12/2018
keywords: DSC, PowerShell, 構成, セットアップ
title: DSC 構成のヘルプの作成
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402893"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="92192-103">DSC 構成のヘルプの作成</span><span class="sxs-lookup"><span data-stu-id="92192-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="92192-104">適用先:Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="92192-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="92192-105">DSC 構成では、コメント ベースのヘルプを使用できます。</span><span class="sxs-lookup"><span data-stu-id="92192-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="92192-106">ユーザーは、ヘルプを呼び出すことによってアクセスできる、**構成**で`-?`、またはを使用して、 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help)コマンドレット。</span><span class="sxs-lookup"><span data-stu-id="92192-106">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="92192-107">配置のすぐ上に、コメント ベース ヘルプ、`Configuration`キーワード。</span><span class="sxs-lookup"><span data-stu-id="92192-107">Place your Comment-based help directly above the `Configuration` keyword.</span></span>
<span data-ttu-id="92192-108">パラメーター宣言、または次の例のように両方のすぐ上、コメント ブロックを使用してパラメーター ヘルプの行でを配置できます。</span><span class="sxs-lookup"><span data-stu-id="92192-108">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="92192-109">PowerShell のコメント ベースのヘルプの詳細については、「[about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92192-109">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="92192-110">VSCode や ISE などの PowerShell 開発環境では、スニペットのコメント ブロックのテンプレートを自動的に挿入できるようにもあります。</span><span class="sxs-lookup"><span data-stu-id="92192-110">PowerShell development environments, like VSCode and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="92192-111">次の例では、構成とそのコメント ベースのヘルプを含むスクリプトを示します。</span><span class="sxs-lookup"><span data-stu-id="92192-111">The following example shows a script that contains a configuration and comment-based help for it.</span></span> <span data-ttu-id="92192-112">この例では、パラメーターを持つ構成を示します。</span><span class="sxs-lookup"><span data-stu-id="92192-112">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="92192-113">詳細については、構成にパラメーターを使用して、参照してください。[パラメーターを追加して、構成に](add-parameters-to-a-configuration.md)します。</span><span class="sxs-lookup"><span data-stu-id="92192-113">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
(and their descriptions) appear in help topic. To change the order, change the syntax.

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.
.EXAMPLE
HelpSample -FilePath "C:\output.txt"

This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>
configuration HelpSample1
{
    param
    (
        [string]$ComputerName = 'localhost',
        # Provide a PARAMETER section for each parameter that your script or function accepts.
        [string]$FilePath = 'C:\Destination.txt'
    )

    Node $ComputerName
    {
        File HelloWorld
        {
            Contents="Hello World"
            DestinationPath = $FilePath
        }
    }
}
```

## <a name="viewing-configuration-help"></a><span data-ttu-id="92192-114">構成のヘルプの表示</span><span class="sxs-lookup"><span data-stu-id="92192-114">Viewing configuration help</span></span>

<span data-ttu-id="92192-115">構成のヘルプを表示するには使用、`Get-Help`コマンドレット、関数、または型の名前と、関数の名前の末尾に`-?`します。</span><span class="sxs-lookup"><span data-stu-id="92192-115">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="92192-116">渡される前の構成の出力は、次の`Get-Help`します。</span><span class="sxs-lookup"><span data-stu-id="92192-116">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

```powershell
Get-Help HelpSample1 -Detailed
```

```output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
        Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
        The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
        (and their descriptions) appear in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
    PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.




    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.




REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> <span data-ttu-id="92192-117">フィールドの構文とパラメーターの属性は、PowerShell によってするに対して自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="92192-117">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="92192-118">参照</span><span class="sxs-lookup"><span data-stu-id="92192-118">See Also</span></span>

- [<span data-ttu-id="92192-119">DSC 構成</span><span class="sxs-lookup"><span data-stu-id="92192-119">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="92192-120">構成の作成、コンパイル、適用</span><span class="sxs-lookup"><span data-stu-id="92192-120">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="92192-121">構成にパラメーターを追加する</span><span class="sxs-lookup"><span data-stu-id="92192-121">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
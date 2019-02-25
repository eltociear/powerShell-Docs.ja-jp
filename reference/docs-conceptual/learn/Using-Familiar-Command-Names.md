---
ms.date: 08/27/2018
keywords: PowerShell, コマンドレット
title: 使い慣れたコマンド名の使用
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: c5665f64fd832eb9c807f413a8e879f63db7f8c6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403513"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="d81ec-103">使い慣れたコマンド名の使用</span><span class="sxs-lookup"><span data-stu-id="d81ec-103">Using familiar command names</span></span>

<span data-ttu-id="d81ec-104">PowerShell では、代替名でコマンドを参照するエイリアスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d81ec-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="d81ec-105">エイリアスがあることで、他のシェルの経験があるユーザーは、既に知っている一般的なコマンド名を PowerShell のほぼ同じ操作に利用できます。</span><span class="sxs-lookup"><span data-stu-id="d81ec-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="d81ec-106">エイリアスは、新しい名前を別のコマンドに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="d81ec-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="d81ec-107">たとえば、PowerShell には、出力ウィンドウをクリアする `Clear-Host` という内部関数があります。</span><span class="sxs-lookup"><span data-stu-id="d81ec-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="d81ec-108">コマンド プロンプトに `cls` または `clear` エイリアスのどちらかを入力できます。</span><span class="sxs-lookup"><span data-stu-id="d81ec-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="d81ec-109">PowerShell はこれらのエイリアスを解釈して、`Clear-Host` 関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="d81ec-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="d81ec-110">この機能は、ユーザーが PowerShell を習得するうえで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d81ec-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="d81ec-111">最初に、ほとんどの **cmd.exe** および Unix ユーザーには、既に名前を知っているコマンドのレパートリーが多数あります。</span><span class="sxs-lookup"><span data-stu-id="d81ec-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="d81ec-112">同等の PowerShell のコマンドでは、同一の結果が得られない場合があります。</span><span class="sxs-lookup"><span data-stu-id="d81ec-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="d81ec-113">しかし、十分に近い結果になるので、PowerShell のコマンド名を知らなくてもユーザーが既知のコマンドを利用することは可能です。</span><span class="sxs-lookup"><span data-stu-id="d81ec-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="d81ec-114">新しいコマンド シェルを習得するうえで、"指が覚えている" ことはもう 1 つの主なストレス要因になります。</span><span class="sxs-lookup"><span data-stu-id="d81ec-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="d81ec-115">長年にわたって **cmd.exe** を使用してきた場合、画面をクリアするには、反射的に `cls` コマンドを入力してしまうでしょう。</span><span class="sxs-lookup"><span data-stu-id="d81ec-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="d81ec-116">`Clear-Host` のエイリアスがなければ、エラー メッセージを受け取ってしまい、出力をクリアするにはどうすればいいかわからないでしょう。</span><span class="sxs-lookup"><span data-stu-id="d81ec-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="d81ec-117">PowerShell で使用できる一般的な **cmd.exe** および UNIX コマンドのいくつかを次の一覧に示します。</span><span class="sxs-lookup"><span data-stu-id="d81ec-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="d81ec-118">cat</span><span class="sxs-lookup"><span data-stu-id="d81ec-118">cat</span></span>|<span data-ttu-id="d81ec-119">dir</span><span class="sxs-lookup"><span data-stu-id="d81ec-119">dir</span></span>|<span data-ttu-id="d81ec-120">マウント</span><span class="sxs-lookup"><span data-stu-id="d81ec-120">mount</span></span>|<span data-ttu-id="d81ec-121">rm</span><span class="sxs-lookup"><span data-stu-id="d81ec-121">rm</span></span>|
|<span data-ttu-id="d81ec-122">cd</span><span class="sxs-lookup"><span data-stu-id="d81ec-122">cd</span></span>|<span data-ttu-id="d81ec-123">echo</span><span class="sxs-lookup"><span data-stu-id="d81ec-123">echo</span></span>|<span data-ttu-id="d81ec-124">move</span><span class="sxs-lookup"><span data-stu-id="d81ec-124">move</span></span>|<span data-ttu-id="d81ec-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="d81ec-125">rmdir</span></span>|
|<span data-ttu-id="d81ec-126">chdir</span><span class="sxs-lookup"><span data-stu-id="d81ec-126">chdir</span></span>|<span data-ttu-id="d81ec-127">erase</span><span class="sxs-lookup"><span data-stu-id="d81ec-127">erase</span></span>|<span data-ttu-id="d81ec-128">popd</span><span class="sxs-lookup"><span data-stu-id="d81ec-128">popd</span></span>|<span data-ttu-id="d81ec-129">sleep</span><span class="sxs-lookup"><span data-stu-id="d81ec-129">sleep</span></span>|
|<span data-ttu-id="d81ec-130">clear</span><span class="sxs-lookup"><span data-stu-id="d81ec-130">clear</span></span>|<span data-ttu-id="d81ec-131">h</span><span class="sxs-lookup"><span data-stu-id="d81ec-131">h</span></span>|<span data-ttu-id="d81ec-132">ps</span><span class="sxs-lookup"><span data-stu-id="d81ec-132">ps</span></span>|<span data-ttu-id="d81ec-133">sort</span><span class="sxs-lookup"><span data-stu-id="d81ec-133">sort</span></span>|
|<span data-ttu-id="d81ec-134">cls</span><span class="sxs-lookup"><span data-stu-id="d81ec-134">cls</span></span>|<span data-ttu-id="d81ec-135">history</span><span class="sxs-lookup"><span data-stu-id="d81ec-135">history</span></span>|<span data-ttu-id="d81ec-136">pushd</span><span class="sxs-lookup"><span data-stu-id="d81ec-136">pushd</span></span>|<span data-ttu-id="d81ec-137">tee</span><span class="sxs-lookup"><span data-stu-id="d81ec-137">tee</span></span>|
|<span data-ttu-id="d81ec-138">copy</span><span class="sxs-lookup"><span data-stu-id="d81ec-138">copy</span></span>|<span data-ttu-id="d81ec-139">kill</span><span class="sxs-lookup"><span data-stu-id="d81ec-139">kill</span></span>|<span data-ttu-id="d81ec-140">pwd</span><span class="sxs-lookup"><span data-stu-id="d81ec-140">pwd</span></span>|<span data-ttu-id="d81ec-141">型</span><span class="sxs-lookup"><span data-stu-id="d81ec-141">type</span></span>|
|<span data-ttu-id="d81ec-142">del</span><span class="sxs-lookup"><span data-stu-id="d81ec-142">del</span></span>|<span data-ttu-id="d81ec-143">lp</span><span class="sxs-lookup"><span data-stu-id="d81ec-143">lp</span></span>|<span data-ttu-id="d81ec-144">r</span><span class="sxs-lookup"><span data-stu-id="d81ec-144">r</span></span>|<span data-ttu-id="d81ec-145">write</span><span class="sxs-lookup"><span data-stu-id="d81ec-145">write</span></span>|
|<span data-ttu-id="d81ec-146">diff</span><span class="sxs-lookup"><span data-stu-id="d81ec-146">diff</span></span>|<span data-ttu-id="d81ec-147">ls</span><span class="sxs-lookup"><span data-stu-id="d81ec-147">ls</span></span>|<span data-ttu-id="d81ec-148">ren</span><span class="sxs-lookup"><span data-stu-id="d81ec-148">ren</span></span>||

<span data-ttu-id="d81ec-149">`Get-Alias` コマンドレットでは、エイリアスに関連付けられたネイティブな PowerShell コマンドの実際の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d81ec-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="d81ec-150">標準エイリアスの解釈</span><span class="sxs-lookup"><span data-stu-id="d81ec-150">Interpreting standard aliases</span></span>

<span data-ttu-id="d81ec-151">前述したエイリアスは、他のコマンド シェルとの名前の互換性を目的として設計されていました。</span><span class="sxs-lookup"><span data-stu-id="d81ec-151">The aliases we described previous were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="d81ec-152">PowerShell に組み込まれているほとんどのエイリアスは、簡略化を目的として設計されています。</span><span class="sxs-lookup"><span data-stu-id="d81ec-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="d81ec-153">名前が短いほど入力は簡単になりますが、エイリアスが何を参照しているかを把握していない場合、読みにくくなります。</span><span class="sxs-lookup"><span data-stu-id="d81ec-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="d81ec-154">PowerShell のエイリアスでは、わかりやすさと簡潔さのバランスを取る試みがなされています。</span><span class="sxs-lookup"><span data-stu-id="d81ec-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="d81ec-155">PowerShell では、一般的な名詞と動詞に対して、標準となる一連のエイリアスを使用しています。</span><span class="sxs-lookup"><span data-stu-id="d81ec-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="d81ec-156">たとえば、次のような省略形があります。</span><span class="sxs-lookup"><span data-stu-id="d81ec-156">Example abbreviations:</span></span>

| <span data-ttu-id="d81ec-157">名詞または動詞</span><span class="sxs-lookup"><span data-stu-id="d81ec-157">Noun or Verb</span></span> | <span data-ttu-id="d81ec-158">省略形</span><span class="sxs-lookup"><span data-stu-id="d81ec-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="d81ec-159">取得</span><span class="sxs-lookup"><span data-stu-id="d81ec-159">Get</span></span>          | <span data-ttu-id="d81ec-160">g</span><span class="sxs-lookup"><span data-stu-id="d81ec-160">g</span></span>            |
| <span data-ttu-id="d81ec-161">設定</span><span class="sxs-lookup"><span data-stu-id="d81ec-161">Set</span></span>          | <span data-ttu-id="d81ec-162">s</span><span class="sxs-lookup"><span data-stu-id="d81ec-162">s</span></span>            |
| <span data-ttu-id="d81ec-163">Item</span><span class="sxs-lookup"><span data-stu-id="d81ec-163">Item</span></span>         | <span data-ttu-id="d81ec-164">i</span><span class="sxs-lookup"><span data-stu-id="d81ec-164">i</span></span>            |
| <span data-ttu-id="d81ec-165">インストール先</span><span class="sxs-lookup"><span data-stu-id="d81ec-165">Location</span></span>     | <span data-ttu-id="d81ec-166">l</span><span class="sxs-lookup"><span data-stu-id="d81ec-166">l</span></span>            |
| <span data-ttu-id="d81ec-167">コマンド</span><span class="sxs-lookup"><span data-stu-id="d81ec-167">Command</span></span>      | <span data-ttu-id="d81ec-168">cm</span><span class="sxs-lookup"><span data-stu-id="d81ec-168">cm</span></span>           |
| <span data-ttu-id="d81ec-169">エイリアス</span><span class="sxs-lookup"><span data-stu-id="d81ec-169">Alias</span></span>        | <span data-ttu-id="d81ec-170">al</span><span class="sxs-lookup"><span data-stu-id="d81ec-170">al</span></span>           |

<span data-ttu-id="d81ec-171">以下のエイリアスは、省略名を知っていれば理解できます。</span><span class="sxs-lookup"><span data-stu-id="d81ec-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="d81ec-172">コマンドレット名</span><span class="sxs-lookup"><span data-stu-id="d81ec-172">Cmdlet name</span></span>    | <span data-ttu-id="d81ec-173">エイリアス</span><span class="sxs-lookup"><span data-stu-id="d81ec-173">Alias</span></span> |
|----------------|-------|
| `Get-Item `    | <span data-ttu-id="d81ec-174">gi</span><span class="sxs-lookup"><span data-stu-id="d81ec-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="d81ec-175">si</span><span class="sxs-lookup"><span data-stu-id="d81ec-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="d81ec-176">gl</span><span class="sxs-lookup"><span data-stu-id="d81ec-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="d81ec-177">sl</span><span class="sxs-lookup"><span data-stu-id="d81ec-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="d81ec-178">gcm</span><span class="sxs-lookup"><span data-stu-id="d81ec-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="d81ec-179">gal</span><span class="sxs-lookup"><span data-stu-id="d81ec-179">gal</span></span>   |

<span data-ttu-id="d81ec-180">PowerShell のエイリアスを使い慣れたら、**sal** エイリアスは `Set-Alias` を参照していると簡単に推測できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d81ec-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="d81ec-181">新しいエイリアスの作成</span><span class="sxs-lookup"><span data-stu-id="d81ec-181">Creating new aliases</span></span>

<span data-ttu-id="d81ec-182">`Set-Alias` コマンドレットを使用して、独自のエイリアスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d81ec-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="d81ec-183">たとえば、次のステートメントは、前述した標準のコマンドレットのエイリアスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d81ec-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="d81ec-184">PowerShell では、起動時に類似のコマンドを内部で使用しますが、これらのエイリアスは変更できません。</span><span class="sxs-lookup"><span data-stu-id="d81ec-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="d81ec-185">これらのコマンドのいずれかを実行しようとすると、エイリアスを変更できないことを示すエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d81ec-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="d81ec-186">たとえば、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="d81ec-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
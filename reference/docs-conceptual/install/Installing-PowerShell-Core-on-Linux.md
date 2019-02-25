---
title: Linux への PowerShell Core のインストール
description: さまざまな Linux ディストリビューションへの PowerShell Core のインストールに関する情報
ms.date: 08/06/2018
ms.openlocfilehash: 2ab9beb19e5f90b392413eee31e3fed317e267b0
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265537"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="25f00-103">Linux への PowerShell Core のインストール</span><span class="sxs-lookup"><span data-stu-id="25f00-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="25f00-104">[Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 18.04][u1804]、[Ubuntu 18.10][u1810]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[openSUSE 42.3][opensuse]、[openSUSE Leap 15][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora]、および [Arch Linux][arch] をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="25f00-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="25f00-105">公式にサポートしていない Linux ディストリビューションの場合、[PowerShell Snap パッケージ][snap]を利用できます。</span><span class="sxs-lookup"><span data-stu-id="25f00-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="25f00-106">また、Linux [`tar.gz` アーカイブ][tar]で直接、PowerShell バイナリを展開できます。ただし、場合によっては、OS に基づいて依存関係を別の手順で設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25f00-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="25f00-107">すべてのパッケージは GitHub [リリース][] ページにあります。</span><span class="sxs-lookup"><span data-stu-id="25f00-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="25f00-108">パッケージがインストールされたら、ターミナルから `pwsh` を実行します。</span><span class="sxs-lookup"><span data-stu-id="25f00-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="25f00-109">プレビュー リリースのインストール</span><span class="sxs-lookup"><span data-stu-id="25f00-109">Installing Preview Releases</span></span>

<span data-ttu-id="25f00-110">パッケージ リポジトリを介して、Linux 用の PowerShell Core Preview リリースをインストールすると、パッケージ名が `powershell` から `powershell-preview` に変わります。</span><span class="sxs-lookup"><span data-stu-id="25f00-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="25f00-111">直接ダウンロードによるインストールでは、ファイル名以外は変わりません。</span><span class="sxs-lookup"><span data-stu-id="25f00-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="25f00-112">さまざまなパッケージ マネージャーを使用して、安定したパッケージとプレビュー パッケージをインストールするためのコマンドを以下の表に示します。</span><span class="sxs-lookup"><span data-stu-id="25f00-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="25f00-113">ディストリビューション</span><span class="sxs-lookup"><span data-stu-id="25f00-113">Distribution(s)</span></span>|<span data-ttu-id="25f00-114">安定したコマンド</span><span class="sxs-lookup"><span data-stu-id="25f00-114">Stable Command</span></span> | <span data-ttu-id="25f00-115">プレビュー コマンド</span><span class="sxs-lookup"><span data-stu-id="25f00-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="25f00-116">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="25f00-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="25f00-117">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="25f00-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="25f00-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="25f00-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="25f00-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="25f00-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="25f00-120">パッケージ リポジトリによるインストール - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="25f00-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="25f00-121">Linux 向け PowerShell Core はパッケージ リポジトリに公開され、インストール (と更新) が簡単です。</span><span class="sxs-lookup"><span data-stu-id="25f00-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="25f00-122">この方法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="25f00-122">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="25f00-123">スーパーユーザーとして Microsoft リポジトリを登録します。</span><span class="sxs-lookup"><span data-stu-id="25f00-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="25f00-124">以降は、インストールの更新に `sudo apt-get upgrade powershell` を使用するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="25f00-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="25f00-125">直接ダウンロードによるインストール - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="25f00-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="25f00-126">Debian パッケージ `powershell_6.1.0-1.ubuntu.14.04_amd64.deb` を</span><span class="sxs-lookup"><span data-stu-id="25f00-126">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="25f00-127">[リリース][] ページから Ubuntu コンピューターにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="25f00-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="25f00-128">次にターミナルで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="25f00-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="25f00-129">`dpkg -i` コマンドは依存関係が満たされずに失敗します。</span><span class="sxs-lookup"><span data-stu-id="25f00-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="25f00-130">次のコマンド `apt-get install -f` でこれらの問題は解決され、PowerShell パッケージの構成が完了します。</span><span class="sxs-lookup"><span data-stu-id="25f00-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="25f00-131">アンインストール - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="25f00-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="25f00-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="25f00-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="25f00-133">パッケージ リポジトリによるインストール - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="25f00-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="25f00-134">Linux 向け PowerShell Core はパッケージ リポジトリに公開され、インストール (と更新) が簡単です。</span><span class="sxs-lookup"><span data-stu-id="25f00-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="25f00-135">この方法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="25f00-135">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="25f00-136">スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo apt-get upgrade powershell` を使用する更新だけが必要になります。</span><span class="sxs-lookup"><span data-stu-id="25f00-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="25f00-137">直接ダウンロードによるインストール - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="25f00-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="25f00-138">Debian パッケージ `powershell_6.1.0-1.ubuntu.16.04_amd64.deb` を</span><span class="sxs-lookup"><span data-stu-id="25f00-138">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="25f00-139">[リリース][] ページから Ubuntu コンピューターにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="25f00-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="25f00-140">次にターミナルで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="25f00-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="25f00-141">`dpkg -i` コマンドは依存関係が満たされずに失敗します。</span><span class="sxs-lookup"><span data-stu-id="25f00-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="25f00-142">次のコマンド `apt-get install -f` でこれらの問題は解決され、PowerShell パッケージの構成が完了します。</span><span class="sxs-lookup"><span data-stu-id="25f00-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="25f00-143">アンインストール - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="25f00-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="25f00-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="25f00-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="25f00-145">パッケージ リポジトリによるインストール - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="25f00-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="25f00-146">Linux 向け PowerShell Core はパッケージ リポジトリに公開され、インストール (と更新) が簡単です。</span><span class="sxs-lookup"><span data-stu-id="25f00-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="25f00-147">この方法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="25f00-147">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="25f00-148">スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo apt-get upgrade powershell` を使用する更新だけが必要になります。</span><span class="sxs-lookup"><span data-stu-id="25f00-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="25f00-149">直接ダウンロードによるインストール - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="25f00-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="25f00-150">Debian パッケージ `powershell_6.1.0-1.ubuntu.18.04_amd64.deb` を</span><span class="sxs-lookup"><span data-stu-id="25f00-150">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="25f00-151">[リリース][] ページから Ubuntu コンピューターにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="25f00-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="25f00-152">次にターミナルで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="25f00-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="25f00-153">`dpkg -i` コマンドは依存関係が満たされずに失敗します。</span><span class="sxs-lookup"><span data-stu-id="25f00-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="25f00-154">次のコマンド `apt-get install -f` でこれらの問題は解決され、PowerShell パッケージの構成が完了します。</span><span class="sxs-lookup"><span data-stu-id="25f00-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="25f00-155">アンインストール - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="25f00-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="25f00-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="25f00-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="25f00-157">18.10 の現状、[中間リリース](https://www.ubuntu.com/about/release-cycle)、のみ[コミュニティのサポート](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6)します。</span><span class="sxs-lookup"><span data-stu-id="25f00-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="25f00-158">18.10 へのインストールは `snapd` を使用してサポートされます。</span><span class="sxs-lookup"><span data-stu-id="25f00-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="25f00-159">完全な手順については、「[Snap パッケージ][snap]」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25f00-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="25f00-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="25f00-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="25f00-161">パッケージ リポジトリによるインストール - Debian 8</span><span class="sxs-lookup"><span data-stu-id="25f00-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="25f00-162">Linux 向け PowerShell Core はパッケージ リポジトリに公開され、インストール (と更新) が簡単です。</span><span class="sxs-lookup"><span data-stu-id="25f00-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="25f00-163">この方法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="25f00-163">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="25f00-164">スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo apt-get upgrade powershell` を使用する更新だけが必要になります。</span><span class="sxs-lookup"><span data-stu-id="25f00-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="25f00-165">直接ダウンロードによるインストール - Debian 8</span><span class="sxs-lookup"><span data-stu-id="25f00-165">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="25f00-166">Debian パッケージ `powershell_6.1.0-1.debian.8_amd64.deb` を</span><span class="sxs-lookup"><span data-stu-id="25f00-166">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="25f00-167">[リリース][] ページから Debian コンピューターにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="25f00-167">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="25f00-168">次にターミナルで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="25f00-168">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="25f00-169">`dpkg -i` コマンドは依存関係が満たされずに失敗します。</span><span class="sxs-lookup"><span data-stu-id="25f00-169">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="25f00-170">次のコマンド `apt-get install -f` でこれらの問題は解決され、PowerShell パッケージの構成が完了します。</span><span class="sxs-lookup"><span data-stu-id="25f00-170">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="25f00-171">アンインストール - Debian 8</span><span class="sxs-lookup"><span data-stu-id="25f00-171">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="25f00-172">Debian 9</span><span class="sxs-lookup"><span data-stu-id="25f00-172">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="25f00-173">パッケージ リポジトリによるインストール - Debian 9</span><span class="sxs-lookup"><span data-stu-id="25f00-173">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="25f00-174">Linux 向け PowerShell Core はパッケージ リポジトリに公開され、インストール (と更新) が簡単です。</span><span class="sxs-lookup"><span data-stu-id="25f00-174">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="25f00-175">この方法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="25f00-175">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="25f00-176">スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo apt-get upgrade powershell` を使用する更新だけが必要になります。</span><span class="sxs-lookup"><span data-stu-id="25f00-176">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="25f00-177">直接ダウンロードによるインストール - Debian 9</span><span class="sxs-lookup"><span data-stu-id="25f00-177">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="25f00-178">Debian パッケージ `powershell_6.1.0-1.debian.9_amd64.deb` を</span><span class="sxs-lookup"><span data-stu-id="25f00-178">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="25f00-179">[リリース][] ページから Debian コンピューターにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="25f00-179">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="25f00-180">次にターミナルで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="25f00-180">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="25f00-181">アンインストール - Debian 9</span><span class="sxs-lookup"><span data-stu-id="25f00-181">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="25f00-182">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="25f00-182">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="25f00-183">このパッケージは Oracle Linux 7 でも動作します。</span><span class="sxs-lookup"><span data-stu-id="25f00-183">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="25f00-184">パッケージ リポジトリによるインストール (推奨) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="25f00-184">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="25f00-185">Linux 向け PowerShell Core は公式 Microsoft リポジトリに公開され、インストール (と更新) が簡単です。</span><span class="sxs-lookup"><span data-stu-id="25f00-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="25f00-186">スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo yum update powershell` を使用する PowerShell の更新だけが必要になります。</span><span class="sxs-lookup"><span data-stu-id="25f00-186">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="25f00-187">直接ダウンロードによるインストール - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="25f00-187">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="25f00-188">[CentOS 7][] を使用して、RPM パッケージ `powershell-6.1.0-1.rhel.7.x86_64.rpm` を</span><span class="sxs-lookup"><span data-stu-id="25f00-188">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="25f00-189">[リリース][] ページから CentOS コンピューターにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="25f00-189">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="25f00-190">次にターミナルで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="25f00-190">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="25f00-191">ダウンロードという中間の手順なしでも RPM をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="25f00-191">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="25f00-192">アンインストール - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="25f00-192">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="25f00-194">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="25f00-194">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="25f00-195">パッケージ リポジトリによるインストール (推奨) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="25f00-195">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="25f00-196">Linux 向け PowerShell Core は公式 Microsoft リポジトリに公開され、インストール (と更新) が簡単です。</span><span class="sxs-lookup"><span data-stu-id="25f00-196">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="25f00-197">スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo yum update powershell` を使用する PowerShell の更新だけが必要になります。</span><span class="sxs-lookup"><span data-stu-id="25f00-197">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="25f00-198">直接ダウンロードによるインストール - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="25f00-198">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="25f00-199">RPM パッケージ `powershell-6.1.0-1.rhel.7.x86_64.rpm` を</span><span class="sxs-lookup"><span data-stu-id="25f00-199">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="25f00-200">[リリース][] ページから Red Hat Enterprise Linux コンピューターにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="25f00-200">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="25f00-201">次にターミナルで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="25f00-201">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="25f00-202">ダウンロードという中間の手順なしでも RPM をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="25f00-202">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="25f00-203">アンインストール - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="25f00-203">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="25f00-204">openSUSE</span><span class="sxs-lookup"><span data-stu-id="25f00-204">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="25f00-205">インストール - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="25f00-205">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="25f00-206">インストール - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="25f00-206">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="25f00-207">アンインストール - openSUSE 42.3、openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="25f00-207">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="25f00-208">Fedora</span><span class="sxs-lookup"><span data-stu-id="25f00-208">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="25f00-209">Fedora 28 は、PowerShell Core 6.1 以降でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="25f00-209">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="25f00-210">パッケージ リポジトリによるインストール (推奨) - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="25f00-210">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="25f00-211">Linux 向け PowerShell Core は公式 Microsoft リポジトリに公開され、インストール (と更新) が簡単です。</span><span class="sxs-lookup"><span data-stu-id="25f00-211">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="25f00-212">直接ダウンロードによるインストール - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="25f00-212">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="25f00-213">RPM パッケージ `powershell-6.1.0-1.rhel.7.x86_64.rpm` を</span><span class="sxs-lookup"><span data-stu-id="25f00-213">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="25f00-214">[リリース][] ページから Fedora コンピューターにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="25f00-214">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="25f00-215">次にターミナルで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="25f00-215">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="25f00-216">ダウンロードという中間の手順なしでも RPM をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="25f00-216">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="25f00-217">アンインストール - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="25f00-217">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="25f00-218">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="25f00-218">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="25f00-219">Arch のサポートは試験段階です。</span><span class="sxs-lookup"><span data-stu-id="25f00-219">Arch support is experimental.</span></span>

<span data-ttu-id="25f00-220">PowerShell は [Arch Linux][] User Repository (AUR) から入手できます。</span><span class="sxs-lookup"><span data-stu-id="25f00-220">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="25f00-221">[タグが付けられた最新のリリース][arch-release]でコンパイルできます</span><span class="sxs-lookup"><span data-stu-id="25f00-221">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="25f00-222">[最新のコミットからマスターに][arch-git]コンパイルできます</span><span class="sxs-lookup"><span data-stu-id="25f00-222">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="25f00-223">[最新のリリース バイナリ][arch-bin]でインストールできます</span><span class="sxs-lookup"><span data-stu-id="25f00-223">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="25f00-224">AUR のパッケージはコミュニティにより保守管理されています。公式のサポートはありません。</span><span class="sxs-lookup"><span data-stu-id="25f00-224">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="25f00-225">AUR からパッケージをインストールする方法については、[Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) かコミュニティ [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="25f00-225">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="25f00-227">Snap パッケージ</span><span class="sxs-lookup"><span data-stu-id="25f00-227">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="25f00-228">Snapd の取得</span><span class="sxs-lookup"><span data-stu-id="25f00-228">Getting snapd</span></span>

<span data-ttu-id="25f00-229">Snap を実行するには、`snapd` が必要です。</span><span class="sxs-lookup"><span data-stu-id="25f00-229">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="25f00-230">`snapd` がインストールされているかどうかを確認するには、[こちらの手順](https://docs.snapcraft.io/core/install)を使用してください。</span><span class="sxs-lookup"><span data-stu-id="25f00-230">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="25f00-231">Snap を使用したインストール</span><span class="sxs-lookup"><span data-stu-id="25f00-231">Installation via Snap</span></span>

<span data-ttu-id="25f00-232">Linux 向け PowerShell Core は [Snap ストア](https://snapcraft.io/store)に公開されるため、インストール (と更新) が簡単です。</span><span class="sxs-lookup"><span data-stu-id="25f00-232">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="25f00-233">この方法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="25f00-233">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="25f00-234">プレビュー バージョンをインストールする場合は、次の方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="25f00-234">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="25f00-235">Snap のインストールが自動的にアップグレードされた後も、`sudo snap refresh powershell` または `sudo snap refresh powershell-preview` を使用してアップグレードをトリガーすることができます。</span><span class="sxs-lookup"><span data-stu-id="25f00-235">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="25f00-236">アンインストール</span><span class="sxs-lookup"><span data-stu-id="25f00-236">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="25f00-237">または</span><span class="sxs-lookup"><span data-stu-id="25f00-237">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="25f00-238">Kali</span><span class="sxs-lookup"><span data-stu-id="25f00-238">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="25f00-239">インストール - Kali</span><span class="sxs-lookup"><span data-stu-id="25f00-239">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="25f00-240">アンインストール - Kali</span><span class="sxs-lookup"><span data-stu-id="25f00-240">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="25f00-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="25f00-241">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="25f00-242">Raspbian のサポートは試験段階です。</span><span class="sxs-lookup"><span data-stu-id="25f00-242">Raspbian support is experimental.</span></span>

<span data-ttu-id="25f00-243">現在のところ、PowerShell は Raspbian Stretch でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="25f00-243">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="25f00-244">また、Core CLR (と PowerShell Core) は Pi 2 および Pi 3 デバイス上でのみ動作します。これは、[Pi Zero](https://github.com/dotnet/coreclr/issues/10605) のような他のデバイスにはサポートされていないプロセッサが搭載されているためです。</span><span class="sxs-lookup"><span data-stu-id="25f00-244">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="25f00-245">[Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) をダウンロードし、[インストール手順](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)に従って Pi にインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="25f00-245">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="25f00-246">インストール - Raspbian</span><span class="sxs-lookup"><span data-stu-id="25f00-246">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="25f00-247">必要に応じて、"pwsh" バイナリへのパスを指定せずに、シンボリック リンクを作成して PowerShell を起動することができます</span><span class="sxs-lookup"><span data-stu-id="25f00-247">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="25f00-248">アンインストール - Raspbian</span><span class="sxs-lookup"><span data-stu-id="25f00-248">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="25f00-249">バイナリ アーカイブ</span><span class="sxs-lookup"><span data-stu-id="25f00-249">Binary Archives</span></span>

<span data-ttu-id="25f00-250">Linux プラットフォームで高度な展開シナリオを実行するために、PowerShell バイナリ `tar.gz` アーカイブが用意されています。</span><span class="sxs-lookup"><span data-stu-id="25f00-250">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="25f00-251">依存関係</span><span class="sxs-lookup"><span data-stu-id="25f00-251">Dependencies</span></span>

<span data-ttu-id="25f00-252">PowerShell はすべての Linux ディストリビューションに移植可能なバイナリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="25f00-252">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="25f00-253">ただし、.NET Core ランタイムはディストリビューションごとに異なる依存関係を必要とします。PowerShell でも同じです。</span><span class="sxs-lookup"><span data-stu-id="25f00-253">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="25f00-254">次の表は、公式にサポートされている Linux ディストリビューションと .NET Core 2.0 の依存関係をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="25f00-254">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="25f00-255">OS</span><span class="sxs-lookup"><span data-stu-id="25f00-255">OS</span></span>                 | <span data-ttu-id="25f00-256">依存関係</span><span class="sxs-lookup"><span data-stu-id="25f00-256">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="25f00-257">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="25f00-257">Ubuntu 14.04</span></span>       | <span data-ttu-id="25f00-258">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="25f00-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="25f00-259">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="25f00-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="25f00-260">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="25f00-260">Ubuntu 16.04</span></span>       | <span data-ttu-id="25f00-261">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="25f00-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="25f00-262">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="25f00-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="25f00-263">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="25f00-263">Ubuntu 17.10</span></span>       | <span data-ttu-id="25f00-264">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="25f00-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="25f00-265">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="25f00-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="25f00-266">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="25f00-266">Ubuntu 18.04</span></span>       | <span data-ttu-id="25f00-267">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="25f00-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="25f00-268">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="25f00-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="25f00-269">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="25f00-269">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="25f00-270">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="25f00-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="25f00-271">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="25f00-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="25f00-272">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="25f00-272">Debian 9 (Stretch)</span></span> | <span data-ttu-id="25f00-273">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="25f00-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="25f00-274">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="25f00-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="25f00-275">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="25f00-275">CentOS 7</span></span> <br> <span data-ttu-id="25f00-276">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="25f00-276">Oracle Linux 7</span></span> <br> <span data-ttu-id="25f00-277">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="25f00-277">RHEL 7</span></span> | <span data-ttu-id="25f00-278">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="25f00-278">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="25f00-279">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="25f00-279">openSUSE 42.3</span></span> | <span data-ttu-id="25f00-280">libcurl4、libopenssl1_0_0、libicu52_1</span><span class="sxs-lookup"><span data-stu-id="25f00-280">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="25f00-281">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="25f00-281">openSUSE Leap 15</span></span> | <span data-ttu-id="25f00-282">libcurl4、libopenssl1_0_0、libicu60_2</span><span class="sxs-lookup"><span data-stu-id="25f00-282">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="25f00-283">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="25f00-283">Fedora 27</span></span> <br> <span data-ttu-id="25f00-284">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="25f00-284">Fedora 28</span></span> | <span data-ttu-id="25f00-285">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="25f00-285">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="25f00-286">公式にサポートされていない Linux ディストリビューションで PowerShell バイナリを展開するには、別の手順で、ターゲット OS に必要な依存関係をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="25f00-286">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="25f00-287">たとえば、[Amazon Linux dockerfile][amazon-dockerfile] は依存関係を先にインストールし、それから Linux `tar.gz` アーカイブを抽出します。</span><span class="sxs-lookup"><span data-stu-id="25f00-287">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="25f00-288">インストール - バイナリ アーカイブ</span><span class="sxs-lookup"><span data-stu-id="25f00-288">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="25f00-289">Linux</span><span class="sxs-lookup"><span data-stu-id="25f00-289">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="25f00-290">バイナリ アーカイブのアンインストール</span><span class="sxs-lookup"><span data-stu-id="25f00-290">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="25f00-291">パス</span><span class="sxs-lookup"><span data-stu-id="25f00-291">Paths</span></span>

* <span data-ttu-id="25f00-292">`$PSHOME` は `/opt/microsoft/powershell/6.1.0/` です</span><span class="sxs-lookup"><span data-stu-id="25f00-292">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="25f00-293">ユーザー プロファイルは `~/.config/powershell/profile.ps1` から読み込まれます</span><span class="sxs-lookup"><span data-stu-id="25f00-293">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="25f00-294">既定のプロファイルは `$PSHOME/profile.ps1` から読み込まれます</span><span class="sxs-lookup"><span data-stu-id="25f00-294">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="25f00-295">ユーザー モジュールは `~/.local/share/powershell/Modules` から読み込まれます</span><span class="sxs-lookup"><span data-stu-id="25f00-295">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="25f00-296">共有モジュールは `/usr/local/share/powershell/Modules` から読み込まれます</span><span class="sxs-lookup"><span data-stu-id="25f00-296">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="25f00-297">既定のモジュールは `$PSHOME/Modules` から読み込まれます</span><span class="sxs-lookup"><span data-stu-id="25f00-297">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="25f00-298">PSReadline 履歴は `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` に記録されます</span><span class="sxs-lookup"><span data-stu-id="25f00-298">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="25f00-299">プロファイルは PowerShell のホスト別構成を順守します。そのため、既定のホスト固有プロファイルは同じ場所の `Microsoft.PowerShell_profile.ps1` にあります。</span><span class="sxs-lookup"><span data-stu-id="25f00-299">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="25f00-300">PowerShell は、Linux の [XDG ベース ディレクトリ仕様][xdg-bds]を尊重しています。</span><span class="sxs-lookup"><span data-stu-id="25f00-300">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[リリース]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
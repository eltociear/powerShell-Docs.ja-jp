---
title: プロバイダーの種類 |Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 0a9bfe5dd0978ffce66db1b18ef4d82be6c1a7f2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359961"
---
# <a name="provider-types"></a>プロバイダーの種類

プロバイダーは、PowerShell によって提供されるプロバイダーコマンドレットがアクションを実行する方法を変更することによって、基本的な機能を定義します。 たとえば、プロバイダーは `Get-Item` コマンドレットの既定の機能を使用することも、データストアから項目を取得するときのコマンドレットの動作を変更することもできます。 このドキュメントで説明するプロバイダーの機能には、特定のプロバイダーの基本クラスおよびインターフェイスからメソッドを上書きすることによって定義される機能が含まれています。

> [!NOTE]
> PowerShell で事前に定義されているプロバイダーの機能については、「[プロバイダーの機能](/previous-versions//ee126189(v=vs.85))」を参照してください。

## <a name="drive-enabled-providers"></a>ドライブ対応のプロバイダー

ドライブ対応プロバイダーは、ユーザーが使用できる既定のドライブを指定し、ユーザーがドライブを追加または削除できるようにします。 ほとんどの場合、プロバイダーは、データストアにアクセスするためにいくつかの既定のドライブを必要とするため、ドライブ対応のプロバイダーになります。 ただし、独自のプロバイダーを作成するときに、ユーザーがドライブを作成および削除することを許可しない場合もあります。

ドライブ対応のプロバイダーを作成するには、プロバイダークラスを[DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)クラスまたはそのクラスから派生した別のクラスから派生させる必要があります。 **DriveCmdletProvider**クラスは、プロバイダーの既定のドライブを実装し、`New-PSDrive` および `Remove-PSDrive` のコマンドレットをサポートするために、次のメソッドを定義します。 多くの場合、プロバイダーコマンドレットをサポートするには、PowerShell エンジンが呼び出すメソッドを上書きして、コマンドレットの `NewDrive` メソッドなど `New-PSDrive` のコマンドレットを呼び出す必要があります。また、必要に応じて、コマンドレットに動的パラメーターを追加するために、`NewDriveDynamicParameters`などの2番目のメソッドを上書きすることもできます。

- [DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)メソッドは、プロバイダーが使用されるときに、ユーザーが使用できる既定のドライブを定義しています。

- [DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)メソッドと DriveCmdletProvider メソッドは、プロバイダーが `New-PSDrive` プロバイダーコマンドレットをどのようにサポートするかを定義します。 [NewDriveDynamicParameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)メソッドを使用します。 このコマンドレットを使用すると、ユーザーはデータストアにアクセスするためのドライブを作成できます。

- [DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)メソッドは、プロバイダーが `Remove-PSDrive` プロバイダーコマンドレットをサポートする方法を定義します。 このコマンドレットを使用すると、ユーザーはデータストアからドライブを削除できます。

## <a name="item-enabled-providers"></a>アイテムが有効なプロバイダー

アイテムを有効にしたプロバイダーを使用すると、ユーザーはデータストア内のアイテムを取得、設定、またはクリアできます。 "Item" は、ユーザーが個別にアクセスまたは管理できるデータストアの要素です。 アイテムが有効なプロバイダーを作成するには、プロバイダークラス[が、その](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)クラスから派生した別のクラスから派生している必要があります。

System.object**クラスは**、特定のプロバイダーコマンドレットを実装する次のメソッドを定義します。 多くの場合、プロバイダーコマンドレットをサポートするには、PowerShell エンジンが呼び出すメソッドを上書きして、コマンドレットの `ClearItem` メソッドなど `Clear-Item` のコマンドレットを呼び出す必要があります。また、必要に応じて、コマンドレットに動的パラメーターを追加するために、`ClearItemDynamicParameters`などの2番目のメソッドを上書きすることもできます。

- プロバイダーが `Clear-Item` をサポートする方法を定義[するには](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)、このメソッドと[system](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) プロバイダーコマンドレット。 このコマンドレットは、データストア内の項目の値を削除することをユーザーに許可します。

- GetItemDynamicParameters[System.Management.Automation.Provider.ItemCmdletProvider.GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)メソッドと system [System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)メソッドは、プロバイダーが `Get-Item` プロバイダーをサポートする方法を定義します。コマンドレット. このコマンドレットを使用すると、ユーザーはデータストアからデータを取得できます。

- [System.Management.Automation.Provider.ItemCmdletProvider.SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)メソッドと SetItemDynamicParameters メソッドは、プロバイダーが `Set-Item` プロバイダーをどのようにサポートするかを定義します。 [System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)メソッドコマンドレット. このコマンドレットを使用すると、ユーザーはデータストア内の項目の値を更新できます。

- [InvokeDefaultAction と](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)の各メソッドは、プロバイダーが `Invoke-Item` プロバイダーコマンドレットをサポートする[方法を定義](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters)します。このメソッドは、プロバイダーがどのようにサポートするかを定義します。 このコマンドレットは、ユーザーが項目によって指定された既定のアクションを実行できるようにします。

- プロバイダーが `Test-Path` プロバイダーコマンドレットをサポートする[方法を定義](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)するには、 [system.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)。 このコマンドレットを使用すると、パスのすべての要素が存在するかどうかをユーザーが判断できます。

プロバイダーコマンドレットの実装に使用されるメソッドに加えて、次のメソッドも定義さ**れてい**ます。

- ユーザー[は、プロバイダーのパス](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath)を指定するときにワイルドカードを使用できます。

- このプロバイダーに対してパスが構文的で有効であるかどうかを判断するに[は、system.string を使用します](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)。

## <a name="container-enabled-providers"></a>コンテナーが有効なプロバイダー

コンテナー対応のプロバイダーを使用すると、ユーザーはコンテナーであるアイテムを管理できます。 コンテナーは、共通の親項目の子項目のグループです。 コンテナーが有効なプロバイダーを作成するには、プロバイダークラスが[ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)クラスまたはそのクラスから派生した別のクラスから派生している必要があります。

> [!IMPORTANT]
> コンテナーが有効になっているプロバイダーは、入れ子になったコンテナーを含むデータストアにアクセスすることはできません。 コンテナーの子項目が別のコンテナーである場合は、ナビゲーションが有効なプロバイダーを実装する必要があります。

**ContainerCmdletProvider**クラスは、特定のプロバイダーコマンドレットを実装する次のメソッドを定義します。 多くの場合、プロバイダーコマンドレットをサポートするには、PowerShell エンジンが呼び出すメソッドを上書きして、コマンドレットの `CopyItem` メソッドなど `Copy-Item` のコマンドレットを呼び出す必要があります。また、必要に応じて、コマンドレットに動的パラメーターを追加するために、`CopyItemDynamicParameters`などの2番目のメソッドを上書きすることもできます。

- [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)メソッドと[ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)メソッドは、プロバイダーが `Copy-Item` プロバイダーコマンドレットをどのようにサポートするかを定義しています。このメソッドについて説明します。 このコマンドレットを使用すると、ユーザーは1つの場所から別の場所に項目をコピーできます。

- ContainerCmdletProvider メソッドと[GetChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)メソッドは、プロバイダーが `Get-ChildItem` プロバイダーコマンドレットをサポートする方法を定義します。 [GetChildItemsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)メソッドを使用します。 このコマンドレットを使用すると、ユーザーは親項目の子項目を取得できます。

- [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)および[ContainerCmdletProvider dynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)メソッドは、`Name` パラメーターが指定されている場合に、プロバイダーが `Get-ChildItem` プロバイダーコマンドレットをサポートする方法を定義します。このメソッドは、プロバイダーが使用する方法を定義します。

- ContainerCmdletProvider メソッドと ContainerCmdletProvider メソッドは、プロバイダーが `New-Item` プロバイダーコマンドレットをどのようにサポートするかを定義します。 [NewItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)と[. NewItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 。 このコマンドレットを使用すると、ユーザーはデータストアに新しい項目を作成できます。

- [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)メソッドと[ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)メソッドは、プロバイダーが `Remove-Item` プロバイダーコマンドレットをどのようにサポートするかを定義しています。このメソッドは、プロバイダーが使用する方法を定義します。 このコマンドレットを使用すると、ユーザーはデータストアから項目を削除できます。

- [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)と[ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)の各メソッドは、プロバイダーが `Rename-Item` プロバイダーコマンドレットをどのようにサポートするかを定義しています。このメソッドは、プロバイダーが使用する方法を定義します。 このコマンドレットを使用すると、ユーザーはデータストア内の項目の名前を変更できます。

**ContainerCmdletProvider**クラスは、プロバイダーコマンドレットの実装に使用されるメソッドに加えて、次のメソッドも定義します。

- [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)メソッドは、項目に子項目があるかどうかを判断するために、プロバイダークラスで使用できます。

- プロバイダークラスは、 [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath)メソッドを使用して、指定されたパスから新しいプロバイダー固有のパスを作成できますが、

## <a name="navigation-enabled-providers"></a>ナビゲーションが有効なプロバイダー

ナビゲーションが有効なプロバイダーは、ユーザーがデータストア内の項目を移動できるようにします。 ナビゲーションが有効なプロバイダーを作成するには、プロバイダークラス[が、system.servicemodel](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)クラスから派生する必要があります。

System.string**クラスは**、特定のプロバイダーコマンドレットを実装する次のメソッドを定義します。 多くの場合、プロバイダーコマンドレットをサポートするには、PowerShell エンジンが呼び出すメソッドを上書きして、コマンドレットの `MoveItem` メソッドなど `Move-Item` のコマンドレットを呼び出す必要があります。また、必要に応じて、コマンドレットに動的パラメーターを追加するために、`MoveItemDynamicParameters`などの2番目のメソッドを上書きすることもできます。

- この[メソッドは](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)、プロバイダーが `Move-Item` プロバイダーコマンドレットをサポートする方法を定義します。この[メソッドと、](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)このメソッドには、プロバイダーが使用する方法が定義されています。 このコマンドレットを使用すると、ユーザーはストア内のある場所から別の場所に項目を移動できます。

- この[例では](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)、プロバイダーが `Join-Path` プロバイダーコマンドレットをサポートする方法を定義しています。 このコマンドレットを使用すると、ユーザーは親と子のパスセグメントを組み合わせて、プロバイダーの内部パスを作成できます。

プロバイダーコマンドレットの実装に使用されるメソッドに加えて、次のメソッドも定義さ**れてい**ます。

- この[メソッドは、パス](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)の子ノードの名前を抽出するために、このメソッドによって取得されます。

- [GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)メソッドは、パスの親の部分を抽出します。このメソッドは、

- [IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)メソッドは、項目がコンテナー項目であるかどうかを判断しています。 このコンテキストでは、コンテナーは共通の親項目の下にある子項目のグループです。

- [NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)メソッドは、指定された基本パスに対して相対的な項目へのパスを返しています。

## <a name="content-enabled-providers"></a>コンテンツが有効なプロバイダー

コンテンツを有効にしたプロバイダーを使用すると、ユーザーはデータストア内の項目の内容をクリア、取得、または設定できます。
たとえば、FileSystem プロバイダーでは、ファイルシステム内のファイルの内容をクリア、取得、および設定できます。 コンテンツが有効なプロバイダーを作成するには、プロバイダークラスが[IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)インターフェイスのメソッドを実装する必要があります。

**IContentCmdletProvider**インターフェイスは、特定のプロバイダーコマンドレットを実装する次のメソッドを定義します。 多くの場合、プロバイダーコマンドレットをサポートするには、PowerShell エンジンが呼び出すメソッドを上書きして、コマンドレットの `ClearContent` メソッドなど `Clear-Content` のコマンドレットを呼び出す必要があります。また、必要に応じて、コマンドレットに動的パラメーターを追加するために、`ClearContentDynamicParameters`などの2番目のメソッドを上書きすることもできます。

- [IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)メソッドと[IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)メソッドは、プロバイダーが `Clear-Content` プロバイダーコマンドレットをどのようにサポートするかを定義しています。このメソッドは、プロバイダーがどのように機能するかを定義します。 このコマンドレットを使用すると、項目を削除せずに項目の内容を削除できます。

- [IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)メソッドと[IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)メソッドは、プロバイダーが `Get-Content` プロバイダーコマンドレットをどのようにサポートするかを定義します。このメソッドは、プロバイダーが使用する方法を定義します。 このコマンドレットは、ユーザーが項目のコンテンツを取得できるようにします。 `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader` メソッドは、コンテンツの読み取りに使用されるメソッドを定義する[IContentReader](/dotnet/api/System.Management.Automation.Provider.IContentReader)インターフェイスを返します。

- [IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)メソッドと IContentCmdletProvider メソッドは、プロバイダーが `Set-Content` プロバイダーコマンドレットをどのようにサポートするかを定義しています。 [GetContentWriterDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)メソッドを使用してください。 このコマンドレットを使用すると、ユーザーは項目のコンテンツを更新できます。 `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter` メソッドは、コンテンツの書き込みに使用されるメソッドを定義する[IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)インターフェイスを返します。

## <a name="property-enabled-providers"></a>プロパティが有効なプロバイダー

プロパティを有効にしたプロバイダーを使用すると、ユーザーはデータストア内の項目のプロパティを管理できます。
プロパティを有効にしたプロバイダーを作成するには、プロバイダークラスが[System.Management.Automation.Provider.IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)と IDynamicPropertyCmdletProvider のメソッドを実装する必要がありますので、 [System.Management.Automation.Provider.IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)インターフェイス。 多くの場合、プロバイダーコマンドレットをサポートするには、PowerShell エンジンが呼び出すメソッドを上書きして、コマンドレットを呼び出す必要があります。たとえば、コマンドレットの `ClearProperty` メソッドなどのメソッドをオーバーライドし、オプションで、`ClearPropertyDynamicParameters`などの2番目のメソッドを上書きして、コマンドレットに動的パラメーターを追加できます。

**IPropertyCmdletProvider**インターフェイスは、特定のプロバイダーコマンドレットを実装する次のメソッドを定義します。

- [IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)メソッドと[IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)メソッドは、プロバイダーが `Clear-ItemProperty` プロバイダーコマンドレットをどのようにサポートするかを定義しています。このメソッドは、プロバイダーが使用する方法を定義します。 このコマンドレットを使用すると、ユーザーはプロパティの値を削除できます。

- [IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)メソッドと[IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)メソッドは、プロバイダーが `Get-ItemProperty` プロバイダーコマンドレットをどのようにサポートするかを定義しています。このメソッドは、プロバイダーが使用する方法を定義します。 このコマンドレットを使用すると、ユーザーは項目のプロパティを取得できます。

- [IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)メソッドと[IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)メソッドは、プロバイダーが `Set-ItemProperty` プロバイダーコマンドレットをどのようにサポートするかを定義します。このメソッドは、プロバイダーが使用する方法を定義します。 このコマンドレットを使用すると、ユーザーは項目のプロパティを更新できます。

  **IDynamicPropertyCmdletProvider**インターフェイスは、特定のプロバイダーコマンドレットを実装する次のメソッドを定義します。

- [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty)メソッドと[IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters)メソッドは、プロバイダーが `Copy-ItemProperty` プロバイダーコマンドレットをどのようにサポートするかを定義します。このメソッドは、プロバイダーが使用する方法を定義します。 このコマンドレットを使用すると、ユーザーはプロパティとその値を1つの場所から別の場所にコピーできます。

- [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty)メソッドと [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) メソッドは、プロバイダーが `Move-ItemProperty` プロバイダーコマンドレットをどのようにサポートするかを定義するために使用されています。また、です。 このコマンドレットを使用すると、ユーザーはプロパティとその値を1つの場所から別の場所に移動できます。

- [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty)メソッドと [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) メソッドは、プロバイダーが `New-ItemProperty` プロバイダーコマンドレットをどのようにサポートするかを定義しています。というメソッドがあります。 このコマンドレットを使用すると、ユーザーは新しいプロパティを作成し、その値を設定できます。

- [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)メソッドと [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) メソッドは、プロバイダーが `Remove-ItemProperty` コマンドレットをどのようにサポートしているかを定義します。また、によって指定されます。 このコマンドレットを使用すると、ユーザーはプロパティとその値を削除できます。

- [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)メソッドと[IDynamicPropertyCmdletProvider propertyparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)メソッドは、プロバイダーが `Rename-ItemProperty` コマンドレットをどのようにサポートするかを定義するために使用されています。 このコマンドレットを使用すると、ユーザーはプロパティの名前を変更できます。

## <a name="see-also"></a>「

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[Windows PowerShell プロバイダーの作成](./writing-a-windows-powershell-provider.md)

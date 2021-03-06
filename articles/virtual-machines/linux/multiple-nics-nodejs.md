---
title: 複数の NIC を持つ Linux VM を Azure に作成する | Microsoft Docs
description: Azure CLI または Resource Manager テンプレートを使って、複数の NIC を持つ Linux VM を作成する方法について説明します。
services: virtual-machines-linux
documentationcenter: ''
author: iainfoulds
manager: jeconnoc
editor: ''
ms.assetid: ''
ms.service: virtual-machines-linux
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: vm-linux
ms.workload: infrastructure
ms.date: 05/11/2017
ms.author: iainfou
ms.openlocfilehash: c87d4f07a01fa42ceb2582b974feb4e802b3e03f
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2018
ms.locfileid: "34365119"
---
# <a name="create-a-linux-virtual-machine-with-multiple-nics-using-the-azure-cli-10"></a>Azure CLI 1.0 を使用して複数の NIC を持つ Linux 仮想マシンを作成する
Azure では、複数の仮想ネットワーク インターフェイス (NIC) を持つ仮想マシン (VM) を作成できます。 一般的なシナリオは、フロント エンドおよびバック エンド接続用に別々のサブネットを使用するか、監視またはバックアップ ソリューション専用のネットワークを用意することです。 この記事では、複数の NIC を持つ VM を作成するためのクイック コマンドを紹介します。 [VM のサイズ](sizes.md)によってサポートされる NIC の数が異なります。VM のサイズを決める際はご注意ください。

> [!WARNING]
> VM の作成時に複数の NIC をアタッチする必要があります。既存の Azure CLI 1.0 を使用する VM に NIC を追加することはできません。 Azure CLI 2.0 を使用して [NIC を既存の VM に追加することができます](multiple-nics.md)。 [元の仮想ディスクに基づいて VM を作成](copy-vm.md)し、VM をデプロイするときに複数の NIC を作成することもできます。


## <a name="cli-versions-to-complete-the-task"></a>タスクを完了するための CLI バージョン
次のいずれかの CLI バージョンを使用してタスクを完了できます。

- [Azure CLI 1.0](#create-supporting-resources) - クラシック デプロイメント モデルと Resource Manager デプロイメント モデル用の CLI (本記事)
- [Azure CLI 2.0](multiple-nics.md) - Resource Manager デプロイ モデル用の次世代 CLI


## <a name="create-supporting-resources"></a>関連リソースを作成する
[Azure CLI](../../cli-install-nodejs.md) でログインし、Resource Manager モードを使用していることを確認します。

```azurecli
azure config mode arm
```

次の例では、パラメーター名を独自の値を置き換えます。 たとえば、*myResourceGroup*、*mystorageaccount*、*myVM* といったパラメーター名にします。

まず、リソース グループを作成します。 次の例では、*myResourceGroup* という名前のリソース グループを *eastus* に作成します。

```azurecli
azure group create myResourceGroup --location eastus
```

VM を保持するストレージ アカウントを作成します。 次の例では、*mystorageaccount* という名前のストレージ アカウントを作成します。

```azurecli
azure storage account create mystorageaccount \
    --resource-group myResourceGroup \
    --location eastus \
    --kind Storage \
    --sku-name PLRS
```

VM を接続する仮想ネットワークを作成します。 次の例では、 *192.168.0.0/16* という名前のアドレス プレフィックスで *myVnet* という名前の仮想ネットワークを作成します。

```azurecli
azure network vnet create \
    --resource-group myResourceGroup \
    --location eastus \
    --name myVnet \
    --address-prefixes 192.168.0.0/16
```

2 つの仮想ネットワーク サブネットを作成します。1 つはフロントエンド トラフィック用、もう 1 つはバックエンド トラフィック用です。 次の例では、*mySubnetFrontEnd* と *mySubnetBackEnd* という名前の 2 つのサブネットを作成します。

```azurecli
azure network vnet subnet create \
    --resource-group myResourceGroup \
    --location myVnet \
    --name mySubnetFrontEnd \
    --address-prefix 192.168.1.0/24
azure network vnet subnet create \
    --resource-group myResourceGroup \
    --location myVnet \
    --name mySubnetBackEnd \
    --address-prefix 192.168.2.0/24
```

## <a name="create-and-configure-multiple-nics"></a>複数の NIC を作成して構成する
詳しくは、「[Azure CLI を使用した複数の NIC VM のデプロイ](../../virtual-machines/linux/multiple-nics.md)」をご覧ください。ここでは、すべての NIC を作成するループ プロセスのスクリプトを作成する方法についても解説しています。

次の例では、*myNic1* と *myNic2* という名前の 2 つの NIC を作成し、1 つの NIC を各サブネットに接続します。

```azurecli
azure network nic create \
    --resource-group myResourceGroup \
    --location eastus \
    --name myNic1 \
    --subnet-vnet-name myVnet \
    --subnet-name mySubnetFrontEnd
azure network nic create \
    --resource-group myResourceGroup \
    --location eastus \
    --name myNic2 \
    --subnet-vnet-name myVnet \
    --subnet-name mySubnetBackEnd
```

通常は、VM 間でトラフィックを管理、分散するために、[ネットワーク セキュリティ グループ](../../virtual-network/security-overview.md)や[ロード バランサー](../../load-balancer/load-balancer-overview.md)も作成します。 次の例では、*myNetworkSecurityGroup* という名前のネットワーク セキュリティ グループを作成します。

```azurecli
azure network nsg create \
    --resource-group myResourceGroup \
    --location eastus \
    --name myNetworkSecurityGroup
```

`azure network nic set` を使って NIC をネットワーク セキュリティ グループにバインドします。 次の例では、*myNic1* と *myNic2* を *myNetworkSecurityGroup* とバインドします。

```azurecli
azure network nic set \
    --resource-group myResourceGroup \
    --name myNic1 \
    --network-security-group-name myNetworkSecurityGroup
azure network nic set \
    --resource-group myResourceGroup \
    --name myNic2 \
    --network-security-group-name myNetworkSecurityGroup
```

## <a name="create-a-vm-and-attach-the-nics"></a>VM を作成して NIC を接続する
VM を作成するときに、複数の NIC を指定します。 `--nic-name` を使用して 1 つの NIC を指定する代わりに、`--nic-names` を使用して NIC のコンマ区切りのリストを指定します。 VM のサイズを選択する際には注意が必要です。 1 つの VM に追加できる NIC の合計数には制限があります。 詳しくは、 [Linux VM のサイズ](sizes.md)に関する記事をご覧ください。 次の例は、複数の NIC を指定し、複数 NIC の使用をサポートする VM のサイズを指定する方法を示しています (*Standard_DS2_v2*)。

```azurecli
azure vm create \
    --resource-group myResourceGroup \
    --name myVM \
    --location eastus \
    --os-type linux \
    --nic-names myNic1,myNic2 \
    --vm-size Standard_DS2_v2 \
    --storage-account-name mystorageaccount \
    --image-urn UbuntuLTS \
    --admin-username azureuser \
    --ssh-publickey-file ~/.ssh/id_rsa.pub
```

Linux VM に複数の NIC を追加する場合は、ルーティング規則を作成する必要があります。 これらの規則が特定の NIC に属しているトラフィックの送受信を VM に許可します。 そうしないと、たとえば、eth1 に属しているトラフィックを、定義された既定のルートで正しく処理できません。 このルーティングの問題を修正するには、「[複数の NIC 用にゲスト OS を構成する](multiple-nics.md#configure-guest-os-for-multiple-nics)」をご覧ください。

## <a name="create-multiple-nics-using-resource-manager-templates"></a>Resource Manager テンプレートを使用して複数の NIC を作成する
Azure Resource Manager テンプレートで宣言型の JSON ファイルを使用して環境を定義します。 詳しくは、「[Azure Resource Manager の概要](../../azure-resource-manager/resource-group-overview.md)」をご覧ください。 Resource Manager テンプレートでは、複数の NIC の作成など、デプロイ時にリソースの複数のインスタンスを作成することができます。 *copy* を使用して、作成するインスタンスの数を指定します。

```json
"copy": {
    "name": "multiplenics"
    "count": "[parameters('count')]"
}
```

詳細については、[*copy* を使用した複数のインスタンスの作成](../../resource-group-create-multiple.md)に関する記事を参照してください。 

`copyIndex()` を使用してリソース名に数値を追加することもできます。これにより、`myNic1`、`myNic2` などを作成することができます。インデックス値を追加する例を次に示します。

```json
"name": "[concat('myNic', copyIndex())]", 
```

完全な例については、「 [Resource Manager テンプレートを使用して複数の NIC を作成する](../../virtual-network/template-samples.md)」を参照してください。

Linux VM に複数の NIC を追加する場合は、ルーティング規則を作成する必要があります。 これらの規則が特定の NIC に属しているトラフィックの送受信を VM に許可します。 そうしないと、たとえば、eth1 に属しているトラフィックを、定義された既定のルートで正しく処理できません。 このルーティングの問題を修正するには、「[複数の NIC 用にゲスト OS を構成する](multiple-nics.md#configure-guest-os-for-multiple-nics)」をご覧ください。

## <a name="next-steps"></a>次の手順
複数の NIC を持つ VM を作成する際は、 [Linux VM のサイズ](sizes.md) を必ず確認してください。 VM の各サイズでサポートされている NIC の最大数に注意してください。 

既存の VM に NIC を追加することはできません。VM をデプロイするときに、すべての NIC を作成する必要があります。 デプロイメントの計画時に、初めから必要なすべてのネットワーク接続があることを確認してください。


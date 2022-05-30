---
title: Membuat jaringan virtual (VNet) – Azure CLI | Microsoft Docs
description: Pelajari cara membuat jaringan virtual (VNet) dan subnet dengan Azure CLI.
ms.date: 11/12/2021
ms.author: dbradish
author: dbradish-microsoft
manager: barbkess
ms.tool: azure-cli
ms.topic: tutorial
ms.prod: azure
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli create vnet, jaringan virtual di azure cli, subnet di jaringan virtual
ms.openlocfilehash: 772012b05b96325b91bdb5b8496e713807f0bf56
ms.sourcegitcommit: 6822e5d700742617eabda5904fe2ca217bae9d28
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/30/2022
ms.locfileid: "145939136"
---
# <a name="2---create-a-virtual-network"></a>2 - Buat jaringan virtual

Jaringan virtual (VNet) memungkinkan mesin virtual (VM) dan sumber daya Azure lainnya saling berkomunikasi dengan aman, dengan internet, dan jaringan lokal. VNet juga dapat dihubungkan ke VNet lain jika rentang alamatnya tidak tumpang tindih. Di bagian ini Anda akan mempelajari cara membuat jaringan virtual dengan subnet.

Subnet memungkinkan Anda membuat segmentasi ruang alamat VNet menjadi sub-jaringan untuk tujuan organisasi. Azure menyebarkan sumber daya ke subnet dalam jaringan virtual, jadi Anda perlu membuat subnet.

Gunakan perintah [az network vnet create](/cli/azure/network/vnet#az_network_vnet_create) untuk membuat jaringan virtual bernama `TutorialVNet1` dengan awalan alamat 10.0.0.0/16 dan subnet bernama `TutorialSubnet1` dengan awalan alamat 10.0.0.0/24.

```azurecli-interactive
# create shell variables
vnetName=TutorialVNet1
subnetName=TutorialSubnet1
vnetAddressPrefix=10.0.0.0/16
subnetAddressPrefix=10.0.0.0/24

az network vnet create \
  --name $vnetName \
  --resource-group $resourceGroup \
  --address-prefixes $vnetAddressPrefix \
  --subnet-name $subnetName \
  --subnet-prefixes $subnetAddressPrefix
```

---
title: Create virtual network (VNet) – Azure CLI | Microsoft Docs
description: Pelajari cara membuat jaringan virtual (VNet) dan subnet dengan Azure CLI.
ms.date: 11/12/2021
ms.author: dbradish
author: dbradish-microsoft
manager: barbkess
ms.devlang: azure-cli
ms.topic: tutorial
ms.prod: azure
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli create vnet, virtual network in azure cli, subnet in virtual network
ms.openlocfilehash: de38d4517734bbe1843ad93c3e0d0de6d11cda96
ms.sourcegitcommit: 62469e9c1ad07f215129ece5db89c530f1a77968
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 12/15/2021
ms.locfileid: "135157723"
---
# <a name="2---create-a-virtual-network"></a>2 - Membuat jaringan virtual

Jaringan virtual (VNets) memungkinkan mesin virtual (VM) dan sumber daya Azure lainnya untuk berkomunikasi dengan aman satu sama lain, internet, dan jaringan lokal. VNet juga dapat dihubungkan ke VNet lain jika rentang alamat mereka tidak tumpang tindih. Di bagian ini Anda akan belajar cara membuat jaringan virtual dengan subnet.

Subnet memungkinkan Anda untuk mengelompokkan ruang alamat VNet ke dalam sub-jaringan untuk tujuan organisasi. Azure menyebarkan sumber daya ke subnet dalam jaringan virtual, jadi Anda perlu membuat subnet.

Gunakan perintah [vnet jaringan az](/cli/azure/network/vnet#az_network_vnet_create) untuk membuat jaringan virtual bernama `TutorialVNet1` dengan awalan alamat 10.0.0.0/16 dan subnet bernama `TutorialSubnet1` dengan awalan alamat 10.0.0.0/24.

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

---
title: Membuat mesin virtual (VM) – Azure CLI | Microsoft Docs
description: Pelajari cara membuat mesin virtual (VM) yang terhubung ke jaringan virtual (VNet) dengan Azure CLI .
ms.date: 11/12/2021
ms.author: dbradish
author: dbradish-microsoft
manager: barbkess
ms.devlang: azure-cli
ms.topic: tutorial
ms.prod: azure
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli create vm, mesin virtual di azure cli
ms.openlocfilehash: 6fd9b399424db7a4ce9dce5f6fa56e5a5d23b18e
ms.sourcegitcommit: 62469e9c1ad07f215129ece5db89c530f1a77968
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 12/15/2021
ms.locfileid: "135157679"
---
# <a name="3---create-a-virtual-machine-on-a-virtual-network"></a>3 - Buat mesin virtual di jaringan virtual

Mesin virtual (VM) di Azure memiliki banyak dependensi. CLI membuat sumber daya ini untuk Anda berdasarkan argumen baris perintah yang Anda tentukan. Di bagian ini, Anda akan mempelajari cara menyebarkan VM ke VNet.

Untuk menyebarkan VM di VNet, mereka harus memiliki lokasi Azure yang sama. Setelah VM dibuat, Anda tidak dapat mengubah VNet tujuan VM dihubungkan.

## <a name="create-a-vm"></a>Buat VM

Gunakan perintah [az vm create](/cli/azure/vm#az_vm_create) untuk membuat mesin virtual baru yang menjalankan Ubuntu, yang menggunakan autentikasi SSH untuk masuk, dan terhubung ke subnet dan VNet yang Anda buat di bagian sebelumnya.

```azurecli-interactive
# create shell variables
vmName=TutorialVM1

az vm create \
  --resource-group $resourceGroup \
  --name $vmName \
  --image UbuntuLTS \
  --vnet-name $vnetName \
  --subnet $subnetName \
  --generate-ssh-keys \
  --output json \
  --verbose 
```

> [!NOTE]
> Jika Anda sudah menyediakan kunci SSH bernama `id_rsa`, kunci ini digunakan untuk autentikasi, bukan memiliki kunci baru yang dihasilkan.

Saat VM dibuat, Anda akan melihat nilai lokal yang digunakan dan sumber daya Azure yang dibuat karena opsi `--verbose`.
Setelah VM siap, JSON ditampilkan dari layanan Azure termasuk alamat IP publik.

```json
{
  "fqdns": "",
  "id": "...",
  "location": "eastus",
  "macAddress": "...",
  "powerState": "VM running",
  "privateIpAddress": "...",
  "publicIpAddress": "<PUBLIC_IP_ADDRESS>",
  "resourceGroup": "TutorialResources",
  "zones": ""
}
```

Pastikan bahwa VM berjalan dengan menghubungkan melalui SSH.

```bash
ssh <PUBLIC_IP_ADDRESS>
```

Lanjutkan dan keluar dari VM dengan mengetik `exit`.

Ada cara lain untuk mendapatkan alamat IP ini setelah VM dimulai. Di bagian berikutnya, Anda akan melihat cara mendapatkan informasi mendetail tentang VM, dan cara memfilternya.

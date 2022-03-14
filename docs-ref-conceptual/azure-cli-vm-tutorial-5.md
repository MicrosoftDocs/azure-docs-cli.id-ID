---
title: Mengatur variabel shell dari output CLI – Azure CLI | Microsoft Docs
description: Pelajari cara mendapatkan informasi mesin virtual (VM) dan menyimpan hasil dalam variabel shell Azure CLI.
ms.date: 11/12/2021
ms.author: dbradish
author: dbradish-microsoft
manager: barbkess
ms.devlang: azure-cli
ms.topic: tutorial
ms.prod: azure
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: mesin virtual di azure cli, atur variabel shell dari output cli
ms.openlocfilehash: abc99d9c47da49b75a4ea596f2016da1fc1d172f
ms.sourcegitcommit: 766c21c494eb7fbdc5160c437868c187c0b6e587
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/17/2022
ms.locfileid: "138989714"
---
# <a name="5---set-shell-variables-from-cli-output"></a>5 - Atur variabel shell dari output CLI

Setelah Anda memiliki ID NIC, jalankan `az network nic show` untuk mendapatkan informasinya. Perhatikan bahwa Anda tidak memerlukan grup sumber daya di sini, karena nama grup sumber daya terdapat dalam ID sumber daya Azure.

```azurecli-interactive
az network nic show --ids $nicId
```

Perintah ini menampilkan semua informasi untuk antarmuka jaringan VM. Data ini mencakup pengaturan DNS, informasi IP, pengaturan keamanan, dan alamat MAC. Kueri berikut menunjukkan cara mendapatkan alamat IP publik dan ID objek subnet.

```azurecli-interactive
az network nic show --ids $nicId \
  --query '{IP:ipConfigurations[].publicIpAddress.id, Subnet:ipConfigurations[].subnet.id}' \
  -o json
```

```json
{
  "IP": [
    "/subscriptions/.../resourceGroups/TutorialResources/providers/Microsoft.Network/publicIPAddresses/TutorialVM1PublicIP"
  ],
  "Subnet": [
    "/subscriptions/.../resourceGroups/TutorialResources/providers/Microsoft.Network/virtualNetworks/TutorialVM1VNET/subnets/TutorialVM1Subnet"
  ]
}
```

Perintah ini menampilkan objek JSON yang memiliki kunci khusus ('IP' dan 'Subnet') untuk nilai yang diekstraksi. Meskipun gaya output ini mungkin tidak berguna untuk alat baris perintah, gaya ini membantu keterbacaan manusia dan dapat digunakan dengan skrip khusus.

Untuk menggunakan alat baris perintah, ubah perintah untuk menghapus kunci dan output JSON khusus sebagai `tsv`. Gaya output ini dapat diproses oleh perintah shell `read` untuk memuat hasil ke dalam beberapa variabel. Karena dua nilai ditampilkan pada baris terpisah, pemisah perintah `read` harus diatur ke string kosong daripada default spasi putih non-baris baru.

```azurecli
read -d '' ipId subnetId <<< $(az network nic show \
  --ids $nicId \
  --query '[ipConfigurations[].publicIpAddress.id, ipConfigurations[].subnet.id]' \
  -o tsv)
```

Gunakan ID objek IP publik untuk mencari alamat IP publik dan menyimpannya dalam variabel shell. ID subnet digunakan untuk mendemonstrasikan cara membuat kueri dan menyimpan beberapa nilai di Azure CLI, ID tidak akan diperlukan untuk sisa tutorial.

```azurecli
vmIpAddress=$(az network public-ip show --ids $ipId \
  --query ipAddress \
  -o tsv)
```

Sekarang Anda memiliki alamat IP VM yang disimpan dalam variabel shell. Lanjutkan dan periksa apakah itu adalah nilai yang sama yang Anda gunakan untuk terhubung ke VM pada awalnya.

```bash
echo $vmIpAddress
```

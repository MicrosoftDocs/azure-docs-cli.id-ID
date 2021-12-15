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
keywords: virtual machine in azure cli, set shell variables from cli output
ms.openlocfilehash: d3efeec0ac005fc89cd31623e73cff356ab0784b
ms.sourcegitcommit: 62469e9c1ad07f215129ece5db89c530f1a77968
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 12/15/2021
ms.locfileid: "135157678"
---
# <a name="5---set-shell-variables-from-cli-output"></a>5 - Mengatur variabel shell dari output CLI

Sekarang setelah Anda memiliki ID NIC, jalankan `az network nic show` untuk mendapatkan informasinya. Perhatikan bahwa Anda tidak memerlukan grup sumber daya di sini, karena nama grup sumber daya terdapat dalam ID sumber daya Azure.

```azurecli-interactive
az network nic show --ids $nicId
```

Perintah ini menunjukkan semua informasi untuk antarmuka jaringan VM. Data ini mencakup pengaturan DNS, informasi IP, pengaturan keamanan, dan alamat MAC. Kueri berikut menunjukkan cara mendapatkan alamat IP publik dan KISI objek subnet.

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

Perintah ini menampilkan objek JSON yang memiliki tombol kustom ('IP' dan 'Subnet') untuk nilai yang diekstraksi. Meskipun gaya output ini mungkin tidak berguna untuk alat baris perintah, ini membantu dengan keterbacaan manusia dan dapat digunakan dengan skrip khusus.

Untuk menggunakan alat baris perintah, ubah perintah untuk menghapus tombol dan output JSON kustom sebagai `tsv` . Gaya output ini dapat diproses oleh perintah shell `read` untuk memuat hasil menjadi beberapa variabel. Karena dua nilai ditampilkan pada baris terpisah, `read` pembatas perintah harus diatur ke string kosong daripada default ruang putih non-newline.

```bash
read -d '' ipId subnetId <<< $(az network nic show \
  --ids $nicId \
  --query '[ipConfigurations[].publicIpAddress.id, ipConfigurations[].subnet.id]' \
  -o tsv)
```

Gunakan ID objek IP publik untuk mencari alamat IP publik dan menyimpannya dalam variabel shell. SUBNET ID digunakan untuk menunjukkan cara query dan menyimpan beberapa nilai di Azure CLI, itu tidak akan diperlukan untuk sisa tutorial.

```bash
vmIpAddress=$(az network public-ip show --ids $ipId \
  --query ipAddress \
  -o tsv)
```

Sekarang Anda memiliki alamat IP VM yang disimpan dalam variabel shell. Silakan dan periksa bahwa itu adalah nilai yang sama yang Anda gunakan untuk awalnya terhubung ke VM.

```bash
echo $vmIpAddress
```

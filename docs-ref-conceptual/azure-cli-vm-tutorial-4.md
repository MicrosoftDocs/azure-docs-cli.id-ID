---
title: Mendapatkan informasi mesin virtual dengan kueri (VM) – Azure CLI | Microsoft Docs
description: Pelajari cara mendapatkan informasi mesin virtual (VM) dengan kueri Azure CLI.
ms.date: 11/12/2021
ms.author: dbradish
author: dbradish-microsoft
manager: barbkess
ms.devlang: azure-cli
ms.topic: tutorial
ms.prod: azure
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: informasi vm tampilan azure cli, kueri di azure cli
ms.openlocfilehash: dc4ffce9bbeda4e26a0cdc811e55a55f7d93f8e1
ms.sourcegitcommit: 766c21c494eb7fbdc5160c437868c187c0b6e587
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/17/2022
ms.locfileid: "138922106"
---
# <a name="4---get-vm-information-with-queries"></a>4 - Dapatkan informasi VM dengan kueri

Setelah VM dibuat, informasi mendetail tentang hal itu dapat diambil. Perintah umum untuk mendapatkan informasi dari sumber daya adalah `show`.

```azurecli-interactive
az vm show --name $vmName --resource-group $resourceGroup
```

Anda akan melihat banyak informasi, yang mungkin sulit diurai secara visual. JSON yang ditampilkan berisi informasi tentang autentikasi, penyimpanan antarmuka jaringan, dan banyak lagi. Yang terpenting, ini berisi ID objek Azure untuk sumber daya tempat VM terhubung. ID objek memungkinkan akses ke sumber daya ini secara langsung untuk mendapatkan informasi selengkapnya tentang konfigurasi dan kemampuan VM.

Untuk mengekstrak ID objek yang kita inginkan, argumen `--query` digunakan. Kueri ditulis dalam [bahasa kueri JMESPath](http://jmespath.org). Dimulai dengan mendapatkan ID objek pengontrol antarmuka jaringan (NIC).

```azurecli-interactive
az vm show --name $vmName \
  --resource-group $resourceGroup \
  --query 'networkProfile.networkInterfaces[].id' \
  --output tsv
```

Ada banyak hal yang terjadi di sini, hanya dengan menambahkan kueri. Setiap bagiannya merujuk ke kunci dalam JSON output, atau berupa operator JMESPath.

* `networkProfile` adalah kunci JSON tingkat atas, yang memiliki `networkInterfaces` sub-kunci. Jika nilai JSON adalah kamus, kuncinya dirujuk dari kunci induk dengan operator `.`.
* Nilai `networkInterfaces` berupa larik, sehingga diratakan dengan operator `[]`. Operator ini menjalankan sisa kueri di setiap elemen larik. Dalam hal ini, ia mendapatkan nilai `id` dari setiap elemen larik.

Format output `tsv` (nilai yang dipisahkan tab) dipastikan hanya menyertakan data hasil dan spasi kosong yang terdiri dari tab dan baris baru.
Karena nilai yang ditampilkan adalah string kosong tunggal, ini dapat ditetapkan secara langsung ke variabel shell.

Untuk informasi tentang cara mengkueri output Azure CLI, lihat [Cara mengkueri output perintah Azure CLI menggunakan kueri JMESPath](query-azure-cli.md)

Lanjutkan dan tetapkan ID objek NIC ke variabel shell sekarang.

```azurecli
nicId=$(az vm show \
  -n $vmName \
  -g $resourceGroup \
  --query 'networkProfile.networkInterfaces[].id' \
  -o tsv)
```

Contoh ini juga menunjukkan penggunaan argumen singkat. Anda dapat menggunakan `-g`, bukan `--resource-group`, `-n` bukan `--name`, dan `-o` bukan `--output`.

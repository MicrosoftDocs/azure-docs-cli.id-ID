---
title: Dapatkan informasi mesin virtual dengan kueri (VM) – Azure CLI | Microsoft Dokumen
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
keywords: azure cli show vm information, queries in azure cli
ms.openlocfilehash: dc4ffce9bbeda4e26a0cdc811e55a55f7d93f8e1
ms.sourcegitcommit: 766c21c494eb7fbdc5160c437868c187c0b6e587
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/17/2022
ms.locfileid: "138922106"
---
# <a name="4---get-vm-information-with-queries"></a>4 - Dapatkan informasi VM dengan kueri

Sekarang vm telah dibuat, informasi rinci tentang hal itu dapat diambil. Perintah umum untuk mendapatkan informasi dari sumber daya adalah `show`.

```azurecli-interactive
az vm show --name $vmName --resource-group $resourceGroup
```

Anda akan melihat banyak informasi, yang bisa sulit diurai secara visual. JSON yang dikembalikan berisi informasi tentang otentikasi, penyimpanan antarmuka jaringan, dan banyak lagi. Yang paling penting, ini berisi ID objek Azure untuk sumber daya yang terhubung dengan VM. ID objek memungkinkan mengakses sumber daya ini secara langsung untuk mendapatkan informasi lebih lanjut tentang konfigurasi dan kemampuan VM.

Untuk mengekstrak ID objek yang kita inginkan, `--query` argumen digunakan. Kueri ditulis dalam [bahasa kueri JMESPathStart](http://jmespath.org) dengan mendapatkan ID objek network interface controller (NIC).

```azurecli-interactive
az vm show --name $vmName \
  --resource-group $resourceGroup \
  --query 'networkProfile.networkInterfaces[].id' \
  --output tsv
```

Ada banyak hal yang terjadi di sini, hanya dengan menambahkan kueri. Setiap bagiannya mereferensikan kunci dalam JSON output, atau merupakan operator JMESPath.

* `networkProfile` adalah kunci dari JSON tingkat atas, yang memiliki `networkInterfaces` subkunci. Jika nilai JSON adalah kamus, kuncinya dirujuk dari kunci induk dengan `.` operator.
* Nilainya `networkInterfaces` adalah array, sehingga diratakan dengan `[]` operator. Operator ini menjalankan sisa kueri pada setiap elemen array. Dalam hal ini, ia mendapat `id` nilai dari setiap elemen array.

Format `tsv` output (nilai yang dipisahkan tab) dijamin hanya mencakup data hasil dan spasi yang terdiri dari tab dan garis baru.
Karena nilai yang dikembalikan adalah string telanjang tunggal, aman untuk menetapkan langsung ke variabel shell.

Untuk informasi selengkapnya tentang kueri output Azure CLI lihat [Cara mengkueri output perintah Azure CLI menggunakan kueri JMESPath](query-azure-cli.md)

Lanjutkan dan tetapkan ID objek NIC ke variabel shell sekarang.

```azurecli
nicId=$(az vm show \
  -n $vmName \
  -g $resourceGroup \
  --query 'networkProfile.networkInterfaces[].id' \
  -o tsv)
```

Contoh ini juga menunjukkan penggunaan argumen singkat. Anda dapat menggunakan `-g` bukan, `--resource-group``-n` bukan`--name`, bukan`-o`.`--output`

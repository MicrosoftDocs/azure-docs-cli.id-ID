---
title: Dapatkan informasi mesin virtual dengan kueri (VM) – Azure CLI | Microsoft Docs
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
ms.openlocfilehash: 18a0e46136a2f15e221fe59542ac09dad59f07ae
ms.sourcegitcommit: 62469e9c1ad07f215129ece5db89c530f1a77968
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 12/15/2021
ms.locfileid: "135157672"
---
# <a name="4---get-vm-information-with-queries"></a>4 - Dapatkan informasi VM dengan kueri

Sekarang VM telah dibuat, informasi rinci tentang hal itu dapat diambil. Perintah umum untuk mendapatkan informasi dari sumber daya adalah `show` .

```azurecli-interactive
az vm show --name $vmName --resource-group $resourceGroup
```

Anda akan melihat banyak informasi, yang bisa sulit diurai secara visual. JSON yang dikembalikan berisi informasi tentang otentikasi, penyimpanan antarmuka jaringan, dan banyak lagi. Yang paling penting, berisi CD objek Azure untuk sumber daya yang vm terhubung ke. ID objek memungkinkan mengakses sumber daya ini secara langsung untuk mendapatkan informasi lebih lanjut tentang konfigurasi dan kemampuan VM.

Untuk mengekstrak ID objek yang kita inginkan, `--query` argumen digunakan. Kueri ditulis dalam [bahasa kueri JMESPath](http://jmespath.org)Mulai dengan mendapatkan ID objek pengontrol antarmuka jaringan (NIC).

```azurecli-interactive
az vm show --name $vmName \
  --resource-group $resourceGroup \
  --query 'networkProfile.networkInterfaces[].id' \
  --output tsv
```

Ada banyak hal yang terjadi di sini, hanya dengan menambahkan kueri. Setiap bagian dari itu referensi kunci dalam output JSON, atau operator JMESPath.

* `networkProfile` Adalah kunci dari JSON tingkat atas, yang memiliki `networkInterfaces` sebagai subkunci. Jika nilai JSON adalah kamus, kuncinya direferensikan dari kunci induk dengan `.` operator.
* `networkInterfaces`Nilainya adalah array, sehingga diratakan dengan `[]` operator. Operator ini menjalankan sisa kueri pada setiap elemen array. Dalam hal ini, ia mendapat `id` nilai dari setiap elemen array.

Format output `tsv` (nilai tab-separated) dijamin hanya mencakup data hasil dan spasi yang terdiri dari tab dan garis baru.
Karena nilai yang dikembalikan adalah string telanjang tunggal, aman untuk menetapkan langsung ke variabel shell.

Untuk informasi selengkapnya tentang query output Azure CLI lihat [Cara query output perintah Azure CLI menggunakan kueri JMESPath](query-azure-cli.md)

Lanjutkan dan tetapkan ID objek NIC ke variabel shell sekarang.

```bash
nicId=$(az vm show \
  -n $vmName \
  -g $resourceGroup \
  --query 'networkProfile.networkInterfaces[].id' \
  -o tsv)
```

Contoh ini juga menunjukkan penggunaan argumen pendek. Anda dapat menggunakan `-g` `--resource-group` bukan, `-n` `--name` bukan, dan `-o` `--output` bukan.

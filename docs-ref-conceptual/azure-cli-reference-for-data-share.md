---
title: Referensi Azure CLI untuk Azure Data Share | Microsoft Docs
description: Temukan perintah referensi core dan ekstensi Azure CLI untuk mengelola Azure Data Share. Dengan 65 perintah berbeda yang tersedia, Anda dapat bekerja secara efektif dengan Data Share dari baris perintah.
services: data-share
author: dbradish-microsoft
manager: barbkess
ms.service: data-share
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure cli, azure data share cli
ms.openlocfilehash: ee3c14f9590662bd5590156da2174a20505117e1
ms.sourcegitcommit: cbb162f5b74c5250338109317f06a152809c4b4c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/06/2022
ms.locfileid: "141405711"
---
# <a name="azure-cli-reference-commands-for-azure-data-share"></a>Perintah referensi Azure CLI untuk Azure Data Share

Antarmuka Baris Perintah ([CLI](./what-is-azure-cli.md)) Azure adalah sekumpulan perintah yang digunakan untuk membuat dan mengelola sumber daya Azure untuk berbagai layanan Azure. Untuk Azure Data Share, tersedia lebih dari 65 perintah berbeda, yang memberi Anda kemampuan untuk bekerja secara efektif dengan layanan dari baris perintah.

Semua perintah Azure CLI untuk [Azure Data Share](/azure/data-share/) saat ini dalam ekstensi ke core Azure CLI. Ekstensi pembagian data memberi Anda akses ke perintah eksperimental dan pra-rilis dan diinstal secara otomatis saat pertama kali Anda menjalankan perintah `az datashare`. Untuk informasi selengkapnya tentang ekstensi Azure CLI, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

## <a name="reference-list"></a>Daftar referensi

Daftar referensi Azure Data Share CLI yang dapat digunakan untuk mengelola Azure Data Share, dan deskripsi setiap jenis referensi:

|Referensi Azure CLI |Deskripsi
|-|-|
| [az datashare](../latest/docs-ref-autogen/datashare.yml) | Semua perintah untuk mengelola Azure Data Share.
| [az datashare account](../latest/docs-ref-autogen/datashare/account.yml) | Perintah untuk mengelola akun Azure Data Share.
| [az datashare consumer](/cli/azure/datashare/consumer) | Perintah bagi konsumen untuk mengelola Azure Data Share.
| [az datashare dataset](/cli/azure/datashare/dataset) | Perintah bagi penyedia untuk mengelola kumpulan data Azure Data Share.
| [az datashare invitation](/cli/azure/datashare/invitation) | Perintah bagi konsumen untuk mengelola undangan Azure Data Share.
| [az datashare provider-share-subscription](/cli/azure/datashare/provider-share-subscription) | Perintah bagi penyedia untuk mengelola langganan Azure Data Share.
| [az datashare synchronization](/cli/azure/datashare) | Perintah untuk mengelola sinkronisasi Azure Data Share.
| [az datashare synchronization-setting](/cli/azure/datashare/synchronization-setting) | Perintah bagi penyedia untuk mengelola pengaturan sinkronisasi Azure Data Share.

## <a name="reference-examples"></a>Contoh referensi

Contoh disediakan dengan setiap referensi Azure CLI. Meskipun Anda juga dapat menyelesaikan tugas ini melalui portal Azure, menggunakan Azure CLI memerlukan baris perintah. Berikut adalah beberapa blok kode untuk memberi Anda ide kemudahan menggunakan Azure CLI.

Untuk bekerja dengan Azure Data Share, Anda memerlukan grup sumber daya terlebih dahulu. Grup sumber daya Azure mudah dibuat dan dikelola dengan Azure CLI.  

```azurecli
#create a resource group
az group create --location westus --name MyResourceGroup
```

```azurecli
#get a list of resource groups for a subscription
az group list --subscription MySubscription --output table
```

Membuat akun berbagi data juga mudah.

```azurecli
#create a data share account
az datashare account create --location westus --tags tag1=Red tag2=White --name MyAccount --resource-group MyResourceGroup
```

## <a name="see-also"></a>Lihat juga

* [Mulai gunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari penginstalan dan aktivitas masuk.

* Temukan referensi [core](../latest/docs-ref-autogen/reference-index.yml) dan [ekstensi](./azure-cli-extensions-list.md) tambahan dalam dokumentasi Azure CLI.
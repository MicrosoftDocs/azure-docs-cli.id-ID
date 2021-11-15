---
title: Azure CLI references for Azure Data Share | Microsoft Docs
description: Cari perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure Data Share. Dengan 65 perintah berbeda yang tersedia, Anda dapat bekerja secara efektif dengan Berbagi Data dari baris perintah.
services: data-share
author: dbradish-microsoft
manager: barbkess
ms.service: data-share
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli references, azure data share cli
ms.openlocfilehash: ed44ea5707a17aec75d9bd7ee396eb4c7f96a2ab
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439104"
---
# <a name="azure-cli-reference-commands-for-azure-data-share"></a>Azure CLI reference commands for Azure Data Share

Azure Command-Line Interface[(CLI)](./what-is-azure-cli.md)adalah seperangkat perintah yang digunakan untuk membuat dan mengelola sumber daya Azure untuk banyak layanan Azure. Untuk Azure Data Share, lebih dari 65 perintah berbeda tersedia, yang memberi Anda kemampuan untuk bekerja secara efektif dengan layanan dari baris perintah.

Semua perintah Azure CLI untuk [Azure Data Share](/azure/data-share/) saat ini sedang dalam perpanjangan ke inti Azure CLI. Ekstensi datashare memberi Anda akses ke perintah eksperimental dan pra-rilis dan secara otomatis diinstal saat pertama kali Anda menjalankan `az datashare` perintah. Untuk informasi selengkapnya tentang ekstensi Azure CLI, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

## <a name="reference-list"></a>Daftar referensi

Daftar referensi Azure Data Share CLI yang dapat digunakan untuk mengelola Azure Data Share, dan deskripsi dari setiap jenis referensi:

|Azure CLI Reference |Deskripsi
|-|-|
| [az datashare](/cli/azure/datashare) | Semua perintah untuk mengelola Azure Data Share.
| [az datashare account](/cli/azure/datashare/account) | Perintah untuk mengelola akun Azure Data Share.
| [az datashare consumer](/cli/azure/datashare/consumer) | Perintah bagi konsumen untuk mengelola Azure Data Share.
| [az datashare dataset](/cli/azure/datashare/dataset) | Perintah untuk penyedia untuk mengelola dataset Azure Data Share.
| [az undangan datashare](/cli/azure/datashare/invitation) | Perintah bagi konsumen untuk mengelola undangan Azure Data Share.
| [az datashare provider-share-subscription](/cli/azure/datashare/provider-share-subscription) | Perintah untuk penyedia untuk mengelola langganan Azure Data Share.
| [az datashare synchronization](/cli/azure/datashare/synchronization) | Perintah untuk mengelola sinkronisasi Azure Data Share.
| [az datashare synchronization-setting](/cli/azure/datashare/synchronization-setting) | Perintah untuk penyedia untuk mengelola pengaturan sinkronisasi Azure Data Share.

## <a name="reference-examples"></a>Contoh referensi

Contoh disediakan dengan setiap referensi Azure CLI. Meskipun Anda juga dapat menyelesaikan tugas-tugas ini melalui portal Azure, menggunakan Azure CLI memerlukan baris perintah. Berikut adalah beberapa blok kode untuk memberi Anda gambaran tentang betapa mudahnya menggunakan Azure CLI.

Untuk bekerja dengan Azure Data Share, Anda terlebih dahulu memerlukan grup sumber daya. Azure resource groups mudah dibuat dan dikelola dengan Azure CLI.  

```azurecli
#create a resource group
az group create --location westus --name MyResourceGroup
```

```azurecli
#get a list of resource groups for a subscription
az group list --subscription MySubscription --output table
```

Juga mudah untuk membuat akun berbagi data.

```azurecli
#create a data share account
az datashare account create --location westus --tags tag1=Red tag2=White --name MyAccount --resource-group MyResourceGroup
```

## <a name="see-also"></a>Lihat juga

* [Mulai dengan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari tentang instalasi dan masuk.

* Temukan referensi [inti](/cli/azure/reference-index) dan [ekstensi](./azure-cli-extensions-list.md) tambahan dalam dokumentasi Azure CLI.

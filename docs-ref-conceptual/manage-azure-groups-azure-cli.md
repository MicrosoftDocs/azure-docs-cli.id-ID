---
title: Cara mengelola grup sumber daya Azure – Azure CLI | Microsoft Docs
description: Pelajari cara mengelola grup sumber daya Azure di Azure CLI, alat lintas platform untuk menyambung ke Azure dan menjalankan perintah administratif pada sumber daya Azure.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: Grup sumber daya Azure, grup sumber daya di Azure
ms.openlocfilehash: fda917493b9cba9e2cde461e28367c5e326e9c59
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439037"
---
# <a name="how-to-manage-azure-resource-groups-with-the-azure-cli"></a>Cara mengelola grup sumber daya Azure dengan Azure CLI

Grup sumber daya adalah kontainer yang menampung sumber daya terkait untuk sebuah solusi Azure. Grup sumber daya mungkin berisi penyimpanan, mesin virtual, aplikasi, dasbor, layanan, atau hampir semua hal yang Anda tangani di Azure.

Azure Command-Line Interface (CLI) memungkinkan Anda membuat, mempertahankan, dan mengatur grup sumber daya Azure default. CLI juga akan memungkinkan Anda menghapus sumber daya setelah membuatnya. 

## <a name="create-a-resource-group"></a>Buat grup sumber daya

Untuk membuat grup sumber daya, gunakan perintah [pembuatan grup az](/cli/azure/group#az_group_create):

```azurecli
az group create --name MyResourceGroup --location eastus
```

Grup sumber daya milik satu lokasi. Untuk melihat semua lokasi yang didukung dalam langganan Anda saat ini, jalankan perintah [az account list-locations](/cli/azure/account#az_account_list_locations):

```azurecli
az account list-locations
```

Untuk melihat semua grup sumber daya untuk langganan Anda saat ini, gunakan perintah [az group list](/cli/azure/group#az_group_list):

```azurecli
az group list --output table
```

> [!TIP]
> `--output` Parameternya adalah parameter global, tersedia untuk semua perintah. Nilai **tabel** menyajikan output dalam format yang bersahabat. Untuk informasi selengkapnya, lihat [Format output untuk perintah Azure CLI](/cli/azure/format-output-azure-cli).

Saat Anda membuat sumber daya, Anda membuatnya dalam grup sumber daya. Contoh berikut menunjukkan akun penyimpanan yang dibuat dengan menggunakan perintah [az storage account create](/cli/azure/storage/account#az_storage_account_create) :

```azurecli
az storage account create --resource-group MyResourceGroup --name storage134 --location eastus --sku Standard_LRS
```

Untuk menghapus grup sumber daya, jalankan perintah [az group delete](/cli/azure/group#az_group_delete) :

```azurecli
az group delete --name MyResourceGroup
```

Saat Anda menghapus grup sumber daya, Anda menghapus semua sumber daya yang menjadi miliknya. Tidak ada opsi untuk membatalkan penghapusan sumber daya. Jika Anda mencoba salah satu perintah dalam artikel ini, menghapus grup sumber daya yang Anda buat akan menghapus akun Anda.

## <a name="persist-a-resource-group"></a>Mempertahankan grup sumber daya

Persistensi parameter memungkinkan Anda menggunakan kembali nilai untuk parameter tertentu, termasuk grup sumber daya.

Pertama, aktifkan fitur persistensi menggunakan perintah [az config param-persist on](/cli/azure/config/param-persist#az_config_param_persist_on):

```azurecli
az config param-persist on
```

Setelah mengaktifkan persistensi, buat grup sumber daya lain:

 ```azurecli
az group create --name OtherResourceGroup --location eastus
```

Selama persistensi aktif, Anda dapat mengeluarkan parameter `--resource-group` dari perintah di masa mendatang. Perintah berikut membuat akun penyimpanan di grup **OtherResourceGroup**:

```azurecli
az storage account create --name storage135 --location eastus --sku Standard_LRS
```

Jika Anda menentukannya dalam perintah, grup sumber daya akan diprioritaskan. Perintah berikut membuat grup penyimpanan dalam grup sumber daya yang disebut **StorageGroups**:

```azurecli
az storage account create --resource-group StorageGroups --name storage136 --location eastus --sku Standard_LRS
```

Namun, aturah Anda menentukan grup sumber daya lain sebagai nilai, Azure CLI akan mengatur ulang nilai yang dipertahankan. Perintah baru menggunakan **StorageGroups** sebagai grup sumber daya. Anda dapat melihat nilai yang dipertahankan menggunakan perintah [az config param-persist show](/cli/azure/config/param-persist#az_config_param_persist_show):

```azurecli
az config param-persist show
```

Perintah ini menunjukkan kepada Anda nilai yang dipertahankan saat ini. Nilai ini disimpan dalam file bernama *local_context_\<username>* dalam direktori tersembunyi bernama *.azure*. Azure CLI membuat direktori di lokasi Anda saat ini saat pertama kali membuat nilai persisten.

Setelah selesai menggunakan parameter tetap, jalankan perintah [az config param-persist off](/cli/azure/config/param-persist#az_config_param_persist_off):

```azurecli
az config param-persist off
```

Azure CLI menyimpan nilai tetap Anda. Anda dapat melihatnya di file konteks lokal. Jika Anda mengaktifkan lagi parameter persistensi, nilai tersebut sudah ditetapkan.

Untuk informasi selengkapnya tentang menggunakan perintah [az config param-persist](/cli/azure/config/param-persist), lihat [Menggunakan parameter tetap untuk menyederhanakan perintah Azure CLI berurutan](/cli/azure/param-persist-tutorial).

## <a name="set-a-default-resource-group"></a>Mengatur grup sumber daya default

Anda dapat mengatur grup sumber daya default untuk semua perintah yang Anda jalankan dari Azure CLI lokal atau dari Azure Cloud Shell. Azure CLI menyimpan konfigurasi ini secara lokal dalam file *config*. Untuk melihat konfigurasi Anda saat ini, jalankan perintah [az config get](/cli/azure/config#az_config_get):

```azurecli
az config get
```

Hasilnya menunjukkan grup sumber daya default dan nilai default lainnya. Jika Anda menggunakan Azure CLI untuk pertama kalinya, hasilnya mungkin kosong.

Untuk mengatur grup sumber daya default untuk penginstalan Azure CLI Anda, jalankan perintah [az config set](/cli/azure/config#az_config_set):

```azurecli
az config set defaults.group=MyResourceGroup
```

Perintah menetapkan nilai untuk kunci tertentu, dalam hal ini `defaults.group`. Untuk opsi konfigurasi yang tersedia, lihat [Konfigurasi Azure CLI](/cli/azure/azure-cli-configuration).

> [!NOTE]
> Perintah [az config set](/cli/azure/config#az_config_set) tidak memvalidasi keberadaan grup sumber daya yang Anda masukkan. Perintah hanya menyimpan pasangan nilai kunci.

Setelah Anda menjalankan perintah, dua perintah berikut akan memberi Anda hasil yang sama:

```azurecli
az storage account create --resource-group MyResourceGroup --name storage01  --location eastus --sku Standard_LRS
az storage account create --name storage01 --location eastus --sku Standard_LRS
```

Grup sumber daya milik langganan. Jika organisasi Anda memiliki lebih dari satu langganan, Anda harus mengatur langganan tersebut sebelum bekerja dengan grup sumber daya dalam langganan. Jika nilai default grup sumber daya bukan milik langganan Anda saat ini, kesalahan akan terjadi. Untuk informasi selengkapnya tentang beberapa langganan, lihat [Menggunakan beberapa langganan Azure](manage-azure-subscriptions-azure-cli.md).

Anda tidak perlu mengatur ulang default untuk menggunakan grup sumber daya lainnya. Sebagai gantinya, tentukan grup sumber daya:

```azurecli
az group create --name OtherResourceGroup --location eastus
az storage account create --resource-group StorageGroups --name storage03  --location westus --sku Standard_LRS
```

Nilai default hanya untuk Anda. Nilai ini tidak akan memengaruhi pengguna lain atau perubahan yang Anda lakukan melalui portal Azure.

Jika Anda menggunakan nilai parameter tetap, seperti yang dijelaskan dalam artikel ini, nilai tersebut lebih diutamakan daripada nilai default yang ditetapkan dalam file *config*.

## <a name="clean-up-resources"></a>Membersihkan sumber daya

Jika Anda mencoba salah satu perintah dalam artikel ini, Anda dapat menghapus sumber daya apa pun yang Anda buat menggunakan perintah [az group delete](/cli/azure/group#az_group_delete) :

```azurecli
az group delete --name MyResourceGroup
az group delete --name OtherResourceGroup
az group delete --name StorageGroups
```

Perintah ini menghapus grup dan semua sumber daya yang dikandungnya sekaligus.

Anda dapat menghapus parameter persisten dengan menjalankan perintah [az config param-persist delete](/cli/azure/config/param-persist#az_config_param_persist_delete):

```azurecli
az config param-persist delete --all
```

## <a name="see-also"></a>Lihat juga

[Konfigurasi CLI Azure](/cli/azure/azure-cli-configuration)

[Tutorial: Gunakan parameter tetap untuk menyederhanakan perintah Azure CLI berurutan](/cli/azure/param-persist-tutorial)

[Menggunakan beberapa langganan Azure](manage-azure-subscriptions-azure-cli.md)

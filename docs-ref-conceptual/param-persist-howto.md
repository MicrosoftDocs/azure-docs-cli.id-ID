---
title: Opsi parameter tetap – Azure CLI | Microsoft Docs
description: Pelajari cara menggunakan parameter tetap Azure Command-Line Interface (CLI) untuk menyimpan nilai parameter tetap lokal yang dapat digunakan kembali untuk perintah Azure CLI.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.prod: azure
ms.date: 08/19/2021
ms.topic: conceptual
ms.devlang: azurecli
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: parameter tetap azure, parameter tetap
ms.openlocfilehash: e296260b5d621b6d22f99718bec673cadddc9625
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439068"
---
# <a name="azure-cli-persisted-parameter"></a>Parameter tetap Azure CLI

Referensi [az config param-persist](/cli/azure/config/param-persist) Azure CLI menyediakan kemampuan untuk mempertahankan nilai parameter tetap lokal untuk perintah Azure CLI.  Dengan demikian,parameter umum tidak lagi perlu diketik ulang terus-menerus. Misalnya, lokasi dan grup sumber daya adalah parameter yang diperlukan dalam berbagai perintah CLI, tetapi tidak berkontribusi terhadap _niat_ perintah.  Jika Anda menyimpan nilai parameter dengan parameter tetap, berarti Anda mengurangi redundansi dan dapat mempersingkat sintaks perintah CLI secara signifikan.

Nilai konfigurasi yang digunakan oleh CLI dievaluasi dengan prioritas berikut, di mana item yang lebih tinggi diprioritaskan dalam daftar.

1. Parameter baris perintah
1. Nilai dalam direktori kerja lokal yang ditetapkan oleh `az config param-persist`
1. Variabel lingkungan
1. Nilai dalam file konfigurasi atau ditetapkan dengan `az config`

[Instal Azure CLI](install-azure-cli.md) atau buka [Azure Cloud Shell](https://shell.azure.com) untuk menjalankan skrip dalam artikel ini.  Jika Anda menggunakan penginstalan lokal Azure CLI, versi 2.12.0 atau yang lebih baru diperlukan untuk menjalankan perintah `az config param-persist`.  Jalankan [versi az](/cli/azure/reference-index#az_version) untuk menemukan versi dan pustaka dependen yang diinstal. Untuk meningkatkan ke versi terbaru, jalankan [peningkatan az](/cli/azure/reference-index#az_upgrade).  Azure Cloud Shell selalu memiliki Azure CLI versi terbaru.

## <a name="persisted-parameter-data-file"></a>File data parameter tetap

Nilai parameter tetap disimpan dalam file bernama `.param_persist` yang disimpan dalam direktori kerja Anda.  Jika Anda menggunakan [Azure Cloud Shell](https://shell.azure.com) untuk menjalankan perintah Azure CLI, direktori kerja Anda berada di akun penyimpanan yang digunakan oleh Azure CLI.  Jika Anda menggunakan [penginstalan lokal](install-azure-cli.md) Azure CLI, direktori kerja Anda berada di mesin lokal Anda.  Di salah satu lokasi, file `.param_persist` disembunyikan dan tidak boleh diperbarui secara manual.

## <a name="persisted-parameter-storage-and-support"></a>Penyimpanan dan dukungan parameter tetap

Parameter Azure CLI berikut didukung oleh parameter tetap.  Parameter `resource_group_name` dan `location` disimpan secara berbeda karena Anda dapat menambahkannya ke parameter tetap _tanpa_ menjalankan perintah create.

| Parameter tetap | Tindakan penyimpanan | Didukung oleh
|-|-|-|
| lokasi | Menjalankan perintah apa pun | Semua referensi Azure CLI
| resource_group_name | Menjalankan perintah apa pun | Semua referensi Azure CLI
| vnet_name | Menjalankan perintah buat | Khusus Azure Web Apps
| storage_account_name | Menjalankan perintah buat |  Khusus Azure Web Apps
| webapp_name | Menjalankan perintah buat | Khusus Azure Web Apps
| function_app_name | Menjalankan perintah buat | Khusus Azure Functions

## <a name="sample-script-using-persisted-parameters"></a>Contoh skrip yang menggunakan parameter tetap

Tanpa parameter tetap, perintah CLI berurutan pasti akan mengulangi nilai parameter yang sama.  Dengan diaktifkannya parameter tetap, nilai parameter tersimpan Anda dapat dihilangkan dari perintah berurutan.  Dalam contoh ini, `location`, `resource group name`, atau `storage account name` diulang dalam perintah berikutnya.

```azurecli
# Reminder: function app and storage account names must be unique.

# turn persisted parameters on
az config param-persist on

# Create a resource group which will store "resource group" and "location" in persisted parameter.
az group create --name RGlocalContext --location westeurope

# Create an Azure storage account omitting location and resource group.
az storage account create \
  --name sa1localcontext \
  --sku Standard_LRS

# Create a serverless function app in the resource group omitting storage account and resource group.
az functionapp create \
  --name FAlocalContext \
  --consumption-plan-location westeurope \
  --functions-version 2

# See the stored parameter values
az config param-persist show
```

## <a name="persisted-parameter-and-global-variable-comparison"></a>Perbandingan variabel global dan parameter tetap

Ada dua perintah Azure CLI yang dapat digunakan untuk nilai parameter default: `az config set defaults` dan `az config param-persist`.  Gunakan perintah `az config set defaults.<option>=<value>` untuk menentukan _variabel global_ seperti grup, lokasi, atau web. Gunakan `az param-persist` untuk menentukan _nilai default lokal_ yang unik untuk beban kerja Anda.  Nilai tersimpan digunakan oleh CLI sebagai pengganti argumen yang diperlukan.

> [!Important]
> Parameter tetap mengesampingkan nilai konteks global.
>

| Referensi | Cakupan | Set | Penggunaan
|-|-|-|-|
[`az config set defaults.<option>=<value>`](/cli/azure/config) | Dicakup secara global di seluruh CLI | Diatur secara eksplisit menggunakan `az config set defaults.<option>=<value>` | Digunakan untuk pengaturan seperti pengelogan, pengumpulan data, dan nilai argumen default
[`az config param-persist`](/cli/azure/config/param-persist) | Dicakup secara lokal ke direktori kerja tertentu | Diatur otomatis setelah parameter tetap diaktifkan | Digunakan untuk perintah berurutan beban kerja individual.

### <a name="command-examples"></a>Contoh perintah

Gunakan `az config param-persist` untuk mengatur variabel global yang digunakan dalam pembuatan akun penyimpanan Azure.

```azurecli
# set the global variable for resource group
az config set defaults.group=myGlobalVariableRG

# Create an Azure storage account omitting the resource group relying on the global variable value
# Substitute the storage account name parameter with a unique value
az storage account create \
  --name mystorageaccount1 \
  --location westeurope \
  --sku Standard_LRS
```

Output perintah CLI menunjukkan bahwa akun penyimpanan baru dibuat dalam grup sumber daya yang ditemukan dalam variabel global, 'myGlobalVariableRG'.

```output
...
},
  "primaryLocation": "westeurope",
  "privateEndpointConnections": [],
  "provisioningState": "Succeeded",
  "resourceGroup": "myGlobalVariableRG",
  "routingPreference": null,
  "secondaryEndpoints": null,
  "secondaryLocation": null,
  "sku": {
    "name": "Standard_LRS",
    "tier": "Standard"
},
...
```

Gunakan `az config param-persist` untuk menetapkan parameter tetap yang digunakan dalam membuat akun penyimpanan Azure.  Jika variabel global ditetapkan untuk objek yang sama, parameter tetap akan menimpa variabel global.

```azurecli
# turn persisted parameter on
az config param-persist on

# Create a resource group in order to write to persisted parameter
az group create --name myParamPersistRG --location westeurope

# Create an Azure storage account omitting the resource group relying on the persisted parameter value
# Substitute the storage account name parameter with a unique value
az storage account create \
  --name mystorageaccount2 \
  --location westeurope \
  --sku Standard_LRS
```

Meskipun variabel global ditetapkan untuk grup sumber daya dengan nilai `myGlobalVariableRG`, dengan parameter tetap yang diaktifkan, akun penyimpanan baru dibuat dengan `myParamPersistRG`.

```output
...
},
  "primaryLocation": "westeurope",
  "privateEndpointConnections": [],
  "provisioningState": "Succeeded",
  "resourceGroup": "myParamPersistRG",
  "routingPreference": null,
  "secondaryEndpoints": null,
  "secondaryLocation": null,
  "sku": {
    "name": "Standard_LRS",
    "tier": "Standard"
},
...
```

## <a name="see-also"></a>Lihat juga

* [Tutorial: Menggunakan parameter tetap untuk perintah Azure CLI berurutan](param-persist-tutorial.md)
* [Konfigurasi Azure CLI menggunakan `az config`](azure-cli-configuration.md)

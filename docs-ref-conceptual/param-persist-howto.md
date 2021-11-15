---
title: Opsi parameter yang bertahan – Azure CLI | Microsoft Docs
description: Pelajari cara menggunakan parameter Azure Command-Line Interface (CLI) untuk menyimpan nilai parameter lokal yang dapat digunakan kembali untuk perintah Azure CLI.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.prod: azure
ms.date: 08/19/2021
ms.topic: conceptual
ms.devlang: azurecli
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure persisted parameters, persisted parameters
ms.openlocfilehash: e296260b5d621b6d22f99718bec673cadddc9625
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439068"
---
# <a name="azure-cli-persisted-parameter"></a>Azure CLI persisted parameter

The Azure CLI [az config param-persist](/cli/azure/config/param-persist) reference memberikan kemampuan untuk mempertahankan nilai parameter lokal yang bertahan untuk perintah Azure CLI.  Ini menghilangkan kebutuhan untuk terus mengetik ulang parameter umum. Misalnya, lokasi dan grup sumber daya diperlukan parameter dalam banyak perintah CLI, tetapi mereka tidak berkontribusi pada _maksud_ perintah.  Ketika Anda menyimpan nilai parameter dengan parameter yang bertahan, Anda mengurangi redundansi dan dapat secara signifikan mempersingkat sintaks perintah CLI.

Nilai konfigurasi yang digunakan oleh CLI dievaluasi dalam prioritas berikut, dengan item yang lebih tinggi pada daftar mengambil prioritas.

1. Parameter baris perintah
1. Nilai dalam direktori kerja lokal yang ditetapkan oleh `az config param-persist`
1. Variabel lingkungan
1. Nilai dalam file konfigurasi atau set dengan `az config`

[Instal Azure CLI](install-azure-cli.md) atau buka [Azure Cloud Shell](https://shell.azure.com) untuk menjalankan skrip di artikel ini.  Jika Anda menggunakan instalasi lokal Azure CLI, versi 2.12.0 atau yang lebih baru diperlukan untuk menjalankan `az config param-persist` perintah.  Jalankan [versi az](/cli/azure/reference-index#az_version) untuk menemukan versi dan pustaka dependen yang diinstal. Untuk meningkatkan ke versi terbaru, jalankan [peningkatan az](/cli/azure/reference-index#az_upgrade).  Azure Cloud Shell selalu memiliki versi terbaru dari Azure CLI.

## <a name="persisted-parameter-data-file"></a>Berkas data parameter yang bertahan

Nilai parameter yang disimpan dalam file bernama `.param_persist` yang disimpan dalam direktori kerja Anda.  Jika Anda menggunakan [Azure Cloud Shell](https://shell.azure.com) untuk menjalankan perintah Azure CLI, direktori kerja Anda ada di akun penyimpanan yang digunakan oleh Azure CLI.  Jika Anda menggunakan [instalasi lokal](install-azure-cli.md) Azure CLI, direktori kerja Anda ada di mesin lokal Anda.  Di kedua lokasi, `.param_persist` file disembunyikan dan tidak boleh diperbarui secara manual.

## <a name="persisted-parameter-storage-and-support"></a>Penyimpanan dan dukungan parameter yang berkelanjutan

Parameter Azure CLI berikut didukung oleh parameter yang bertahan.  Parameter `resource_group_name` dan disimpan secara berbeda karena Anda dapat `location` menambahkannya ke parameter yang bertahan _tanpa_ menjalankan perintah buat.

| Parameter yang bertahan | tindakan Storage | Didukung oleh
|-|-|-|
| lokasi | Jalankan perintah apa pun | Semua referensi Azure CLI
| resource_group_name | Jalankan perintah apa pun | Semua referensi Azure CLI
| vnet_name | Menjalankan perintah buat | Azure Web Apps only
| storage_account_name | Menjalankan perintah buat |  Azure Web Apps only
| webapp_name | Menjalankan perintah buat | Azure Web Apps only
| function_app_name | Menjalankan perintah buat | Azure Functions only

## <a name="sample-script-using-persisted-parameters"></a>Contoh skrip menggunakan parameter yang bertahan

Tanpa parameter yang bertahan, perintah CLI berurutan harus mengulangi nilai parameter yang sama.  Dengan parameter yang diaktifkan, nilai parameter yang tersimpan dapat dihilangkan dari perintah berurutan.  Dalam contoh `location` ini, , `resource group name` atau diulang dalam `storage account name` perintah berikutnya.

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

## <a name="persisted-parameter-and-global-variable-comparison"></a>Parameter yang bertahan dan perbandingan variabel global

Ada dua perintah Azure CLI yang dapat digunakan untuk nilai parameter default: `az config set defaults` dan `az config param-persist` .  Gunakan `az config set defaults.<option>=<value>` perintah untuk menentukan _variabel global_ seperti grup, lokasi, atau web. Gunakan `az param-persist` untuk menentukan nilai default _lokal_ yang unik untuk beban kerja Anda.  Nilai yang disimpan digunakan oleh CLI sebagai pengganti argumen yang diperlukan.

> [!Important]
> Parameter yang bertahan mengesampingkan nilai konteks global.
>

| Referensi | Cakupan | Set | Gunakan 
|-|-|-|-|
[`az config set defaults.<option>=<value>`](/cli/azure/config) | Lingkup global di seluruh CLI | Mengatur secara eksplisit menggunakan `az config set defaults.<option>=<value>` | Gunakan untuk pengaturan seperti log, pengumpulan data, dan nilai argumen default
[`az config param-persist`](/cli/azure/config/param-persist) | Dise lingkup lokal ke direktori kerja tertentu | Atur secara otomatis setelah parameter yang bertahan diaktifkan | Gunakan untuk perintah berurutan beban kerja individu.

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

Gunakan `az config param-persist` untuk mengatur parameter yang tetap digunakan dalam pembuatan akun penyimpanan Azure.  Jika variabel global ditetapkan untuk objek yang sama, parameter yang bertahan akan menimpa variabel global.

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

Bahkan dengan variabel global yang ditetapkan untuk kelompok sumber daya dengan nilai `myGlobalVariableRG` , dengan parameter bertahan diaktifkan, akun penyimpanan baru dibuat dengan `myParamPersistRG` .

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

* [Tutorial: Gunakan parameter yang bertahan dengan perintah Azure CLI berurutan](param-persist-tutorial.md)
* [Azure CLI Configuration using `az config`](azure-cli-configuration.md)

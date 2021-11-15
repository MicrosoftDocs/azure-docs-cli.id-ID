---
title: Azure cloud management - Azure CLI | Microsoft Docs
description: Buat, masuk, dan kelola beberapa awan dengan Azure CLI. Pelajari cara mendapatkan informasi tentang awan, mengubah awan saat ini, dan mendaftarkan / tidak terdaftar awan baru.
author: dbradish-microsoft
manager: barbkess
ms.author: dbradish
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cloud management
ms.openlocfilehash: 2ab4b2e200104023607e5726938c41a3af442ab7
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439038"
---
# <a name="azure-cloud-management-with-the-azure-cli"></a>Azure cloud management with the Azure CLI

Jika Anda bekerja di berbagai wilayah atau menggunakan [Azure Stack,](/azure/azure-stack/user/)Anda mungkin perlu menggunakan lebih dari satu cloud. Microsoft menyediakan cloud untuk mematuhi undang-undang regional, yang tersedia untuk Anda gunakan. Artikel ini menunjukkan kepada Anda cara mendapatkan informasi tentang awan, mengubah awan saat ini, dan mendaftarkan atau tidak terdaftar awan baru.

## <a name="list-available-clouds"></a>Daftar awan yang tersedia

Anda dapat mencantumkan awan yang tersedia dengan perintah [daftar az cloud.](/cli/azure/cloud#az_cloud_list) Perintah ini menunjukkan cloud mana yang saat ini aktif, apa profilnya saat ini, dan informasi tentang akhiran regional dan nama host.

Untuk mendapatkan awan aktif dan daftar semua awan yang tersedia:

```azurecli-interactive
az cloud list --output table
```

```output
IsActive    Name               Profile
----------  -----------------  ---------
True        AzureCloud         latest
            AzureChinaCloud    latest
            AzureUSGovernment  latest
            AzureGermanCloud   latest
```

Awan yang saat ini aktif ada `True` di `IsActive` kolom. Hanya satu cloud yang bisa aktif kapan saja. Untuk mendapatkan informasi lebih rinci tentang cloud, termasuk titik akhir yang digunakan untuk layanan Azure, gunakan `cloud show` perintah:

```azurecli-interactive
az cloud show --name AzureChinaCloud --output json
```

```json
{
  "endpoints": {
    "activeDirectory": "https://login.chinacloudapi.cn",
    "activeDirectoryDataLakeResourceId": null,
    "activeDirectoryGraphResourceId": "https://graph.chinacloudapi.cn/",
    "activeDirectoryResourceId": "https://management.core.chinacloudapi.cn/",
    "batchResourceId": "https://batch.chinacloudapi.cn/",
    "gallery": "https://gallery.chinacloudapi.cn/",
    "management": "https://management.core.chinacloudapi.cn/",
    "resourceManager": "https://management.chinacloudapi.cn",
    "sqlManagement": "https://management.core.chinacloudapi.cn:8443/",
    "vmImageAliasDoc": "https://raw.githubusercontent.com/Azure/azure-rest-api-specs/master/arm-compute/quickstart-templates/aliases.json"
  },
  "isActive": false,
  "name": "AzureChinaCloud",
  "profile": "latest",
  "suffixes": {
    "azureDatalakeAnalyticsCatalogAndJobEndpoint": null,
    "azureDatalakeStoreFileSystemEndpoint": null,
    "keyvaultDns": ".vault.azure.cn",
    "sqlServerHostname": ".database.chinacloudapi.cn",
    "storageEndpoint": "core.chinacloudapi.cn"
  }
}
```

## <a name="switch-the-active-cloud"></a>Beralih cloud aktif

Untuk mengatur cloud default menggunakan file konfigurasi, lihat [nilai konfigurasi CLI dan variabel lingkungan](./azure-cli-configuration.md#cli-configuration-values-and-environment-variables).  Untuk mengganti awan aktif, jalankan perintah [set awan az.](/cli/azure/cloud#az_cloud_set) Perintah ini mengambil satu argumen yang diperlukan, nama awan.

```azurecli-interactive
az cloud set --name AzureChinaCloud
```

> [!IMPORTANT]
> Jika autentikasi untuk cloud yang diaktifkan telah kedaluwarsa, Anda perlu mengautentikasi ulang sebelum melakukan tugas CLI lainnya. Jika ini adalah pertama kalinya Anda beralih ke cloud baru, Anda juga perlu mengatur langganan aktif.
> Untuk petunjuk tentang autentikasi, lihat [Masuk dengan Azure CLI](authenticate-azure-cli.md). Untuk informasi tentang manajemen langganan, lihat [Mengelola langganan Azure dengan Azure CLI](manage-azure-subscriptions-azure-cli.md)

## <a name="register-a-new-cloud"></a>Mendaftarkan cloud baru

Daftarkan cloud baru jika Anda memiliki titik akhir anda sendiri untuk Azure Stack. Membuat cloud dilakukan dengan perintah [registrasi az cloud.](/cli/azure/cloud#az_cloud_register) Perintah ini memerlukan nama dan satu set titik akhir layanan. Untuk mempelajari cara mendaftarkan cloud untuk digunakan dengan Azure Stack, lihat [Menggunakan profil versi API dengan Azure CLI di Azure Stack](/azure/azure-stack/user/azure-stack-version-profiles-azurecli2#connect-to-azure-stack).

Anda tidak perlu mendaftarkan informasi untuk wilayah China, Pemerintah AS, atau Jerman. Cloud ini dikelola oleh Microsoft dan tersedia secara default.  Untuk informasi selengkapnya tentang semua pengaturan titik akhir yang tersedia, lihat [dokumentasi untuk `az cloud register` ](/cli/azure/cloud#az_cloud_register).

Mendaftarkan cloud tidak secara otomatis beralih ke sana. Gunakan `az cloud set` perintah untuk memilih cloud yang baru dibuat.

## <a name="update-an-existing-cloud"></a>Memperbarui awan yang sudah ada

Jika Anda memiliki izin, Anda juga dapat memperbarui cloud yang sudah ada. Memperbarui cloud beralih ke profil layanan Azure yang berbeda atau memodifikasi titik akhir koneksi.
Perbarui cloud dengan perintah [pembaruan az cloud,](/cli/azure/cloud#az_cloud_update) yang mengambil argumen yang sama dengan `az cloud register` .

## <a name="unregister-a-cloud"></a>Tidak terdaftar awan

Jika Anda tidak lagi membutuhkan awan yang dibuat, itu dapat tidak terdaftar dengan perintah [az cloud unregister:](/cli/azure/cloud#az_cloud_unregister)

```azurecli-interactive
az cloud unregister --name MyCloud
```

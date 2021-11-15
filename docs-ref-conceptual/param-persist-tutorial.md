---
title: Tutorial - cara menggunakan parameter yang bertahan dengan | Azure CLI Microsoft Docs
description: Pelajari cara menggunakan parameter az config param-persist dan persisted dengan Azure CLI untuk menyimpan nilai parameter untuk penggunaan berulang dan jalankan perintah berurutan.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.prod: azure
ms.date: 09/16/2021
ms.topic: conceptual
ms.devlang: azurecli
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: tutorial parameter yang bertahan
ms.openlocfilehash: 1b74f8b39ebc8b4fd6c1da8b1bd776bc363d9c3f
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439091"
---
# <a name="tutorial-use-persisted-parameters-to-simplify-sequential-azure-cli-commands"></a>Tutorial: Gunakan parameter yang bertahan untuk menyederhanakan perintah Azure CLI berurutan

Azure CLI menawarkan parameter bertahan yang memungkinkan Anda menyimpan nilai parameter untuk penggunaan lanjutan.  Dalam tutorial ini, Anda belajar cara bekerja dengan nilai-nilai yang bertahan, dan menggunakan nilai-nilai lokal ini untuk mengeksekusi perintah berurutan secara efisien.

Dalam tutorial ini, Anda akan belajar untuk:

> [!div class="checklist"]
> * Menggunakan `az config param-persist` perintah referensi
> * Menjalankan perintah sekuensial menggunakan parameter yang bertahan

Tutorial ini menggunakan perintah Azure CLI berikut

- [az config param-persist delete](/cli/azure/config/param-persist#az_config_param_persist_delete)
- [az config param-persist off](/cli/azure/config/param-persist#az_config_param_persist_off)
- [az config param-persist on](/cli/azure/config/param-persist#az_config_param_persist_on)
- [az config param-persist show](/cli/azure/config/param-persist#az_config_param_persist_show)
- [az function app create](/cli/azure/functionapp#az_functionapp_create)
- [pembuatan grup az](/cli/azure/group#az_group_create)
- [az storage account create](/cli/azure/storage/account#az_storage_account_create)


Jika Anda tidak memiliki langganan Azure, buat [akun gratis](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) sebelum Anda memulai.

## <a name="prerequisites"></a>Prasyarat

1. [Memasang CLI Azure](install-azure-cli.md)

   Jika diinginkan, Anda juga dapat menggunakan Azure Cloud Shell untuk menyelesaikan langkah-langkah dalam tutorial ini.  Azure Cloud Shell adalah lingkungan shell interaktif yang Anda gunakan melalui browser.  Mulai Cloud Shell dengan menggunakan salah satu metode berikut:

   - Buka Cloud Shell dengan membuka [https://shell.azure.com](https://shell.azure.com)

   - Pilih tombol **Cloud Shell** pada bilah menu di sudut kanan atas di [portal Azure](https://portal.azure.com)

1. Jika Anda menggunakan instalasi lokal Azure CLI, lengkapi hal berikut:
   - Masuk menggunakan perintah [login az,](/cli/azure/reference-index#az_login) lalu ikuti langkah-langkah yang ditampilkan di terminal Anda untuk menyelesaikan proses otentikasi.

     ```azurecli
     az login
     ```
    - Tutorial ini memerlukan versi 2.12.0 atau yang lebih baru dari Azure CLI.  Jalankan [versi az](/cli/azure/reference-index#az_version) untuk menemukan versi dan pustaka dependen yang diinstal. Untuk meningkatkan ke versi terbaru, jalankan [peningkatan az](/cli/azure/reference-index#az_upgrade).

## <a name="1-determine-your-local-directory"></a>1. Tentukan direktori lokal Anda

Nilai parameter yang bertahan disimpan dalam direktori kerja akun penyimpanan Azure yang digunakan oleh Azure Cloud Shell.  Jika Anda menggunakan instalasi lokal Azure CLI, nilai disimpan di direktori kerja pada mesin Anda.

Untuk menemukan, membuat, atau mengubah direktori kerja yang digunakan oleh Azure CLI, gunakan perintah CLI yang sudah dikenal ini.

```azurecli
# List directories
dir

# Make directory
mkdir azCLI

# Change directory
cd azCLI
```

## <a name="2-turn-on-persisted-parameters"></a>2. Aktifkan parameter yang sudah ada

[Parameter yang bertahan](/cli/azure/config/param-persist) harus diaktifkan sebelum nilai parameter dapat disimpan.  Anda akan menerima peringatan sampai `az config param-persist` bergerak keluar dari tahap eksperimental.  Lihat [Gambaran Umum: Tipe referensi dan status Azure CLI](/cli/azure/reference-types-and-status) untuk mempelajari tentang tipe referensi, status, dan tingkat dukungan Azure CLI.

```azurecli
az config param-persist on
```

## <a name="3-create-persisted-parameters"></a>3. Membuat parameter yang bertahan

Untuk menyimpan nilai untuk parameter yang bertahan, jalankan perintah Azure CLI pilihan Anda yang berisi parameter yang ingin Anda simpan.  Misalnya, buat grup sumber daya dan parameter disimpan untuk digunakan di `--location` `--name` masa mendatang.

1. Simpan nama lokasi dan grup sumber daya.
   ```azurecli
   # With persisted parameters turned on, create a resource group
   az group create --name RG1forTutorial --location eastus2

   # See new persisted parameters
   az config param-persist show
   ```

   ```output
   {
     "all": {
       "location": "eastus2",
       "resource_group_name": "RG1forTutorial"
     }
   }
   ```

1. Menggunakan parameter baru yang bertahan, buat akun penyimpanan.

   ```azurecli
   # Create a storage account
   az storage account create --name sa1fortutorial

   # See that storage_account_name has been added to persisted parameters
   az config param-persist show
   ```

   ```output
   {
     "all": {
       "location": "eastus2",
       "resource_group_name": "RG1forTutorial",
       "storage_account_name": "sa1fortutorial"
     }
   }
   ```

1. Buat parameter yang bertahan tanpa membuat sumber daya baru.

   Jika Anda tidak ingin membuat sumber daya Azure baru, `resource_group_name` dan parameter dapat disimpan dengan menggunakan perintah `location` non-buat seperti `show` atau `list` .   Lihat [Azure CLI mempertahankan parameter](/cli/azure/param-persist-howto#compare-parameter-persistence-and-global-variables) untuk daftar lengkap parameter yang didukung, dan tindakan yang diperlukan untuk mempertahankan nilai.  Contoh ini juga menghapus semua nilai parameter dengan menggunakan perintah [penghapusan az config param-persist.](/cli/azure/config/param-persist#az_param_persist_delete)

   ```azurecli
   # Clear all persisted parameters for demonstration.
   az config param-persist delete --all

   # List all storage accounts which will create the `resource_group_name` stored parameter value.
   az storage account show --resource-group RG1forTutorial --name sa1fortutorial

   # See the new stored value created for resource group.  The storage account name is only stored with a 'create' command.
   az config param-persist show
   ```

   ```output
   {
     "all": {
       "resource_group_name": "RG1forTutorial"
     }
   }
   ```

## <a name="4-replace-persisted-parameters"></a>4. Ganti parameter yang bertahan

Mengganti nilai parameter yang tersimpan sesederhana mengeksekusi perintah yang berisi nilai yang berbeda.

1. Buat parameter baru yang bertahan.
   ```azurecli
   # Clear all persisted parameters for demonstration
   az config param-persist delete --all

   # Create a storage account placing "location", "resource_group_name", and "storage_account_name" into persisted parameters
   az storage account create --name sa1fortutorial --resource-group RG1forTutorial --location eastus2

   # See persisted parameters entries
   az config param-persist show
   ```

   ```output
   {
     "all": {
       "location": "eastus2",
       "resource_group_name": "RG1forTutorial",
       "storage_account_name": "sa1fortutorial"
     }
   }
   ```

1. Ganti nilai yang baru disimpan.

   ```azurecli
   # Create a second storage account while changing both the "storage_account_name" and "location" persisted parameters
   az storage account create --name sa2fortutorial --location westeurope

   # See new persisted parameters
   az config param-persist show
   ```

   ```output
   {
     "all": {
       "location": "westeurope",
       "resource_group_name": "RG1forTutorial",
       "storage_account_name": "sa2fortutorial"
     }
   }
   ```

   > [!NOTE]
   >
   > Bahkan jika parameter yang bertahan diaktifkan, Anda tidak perlu menggunakannya.  Anda masih dapat menjalankan perintah dengan semua nilai parameter yang ditentukan.  Namun, perlu diketahui bahwa dengan parameter yang bertahan diaktifkan, _Anda akan membuat parameter baru yang bertahan, atau menimpa yang sudah ada._

## <a name="5-execute-sequential-commands"></a>5. Jalankan perintah sekuensial

Skrip ini membuat aplikasi Azure Function menggunakan paket Konsumsi.

### <a name="using-persisted-parameters"></a>[Menggunakan parameter yang bertahan](#tab/azure-cli)

```azurecli
# Reminder: function app and storage account names must be unique.

# Turn persisted parameters on.
az config param-persist on

# Create a resource group.
az group create --name RG2forTutorial --location westeurope

# Create an Azure storage account in the resource group omitting "--location" and "--resource-group" parameters.
az storage account create \
  --name sa3fortutorial \
  --sku Standard_LRS

# Create a serverless function app in the resource group omitting "--storage-account" and "--resource-group" parameters.
az functionapp create \
  --name FAforTutorial \
  --consumption-plan-location westeurope \
  --functions-version 2

# See the stored parameter values.
az config param-persist show
```

### <a name="without-persisted-parameters"></a>[Tanpa parameter yang bertahan](#tab/azure-portal)

```azurecli
# Reminder: function app and storage account names must be unique.

# turn persisted parameters off
az config param-persist off

# Create a resource group.
az group create --name RG2forTutorial --location westeurope

# Create an Azure storage account in the resource group.
az storage account create \
  --name sa3fortutorial \
  --location westeurope \
  --resource-group RG2forTutorial \
  --sku Standard_LRS

# Create a serverless function app in the resource group.
az functionapp create \
  --name FAforTutorial \
  --storage-account sa3fortutorial \
  --consumption-plan-location westeurope \
  --resource-group RG2forTutorial \
  --functions-version 2
```

* * *

## <a name="6-delete-persisted-parameters"></a>6. Menghapus parameter yang bertahan

Gunakan perintah [hapus az config param-persist](/cli/azure/param-persist#az_param_persist_delete) untuk menghapus entri.

```azurecli
# Remove a single persisted parameters entry by specifying the name, not the value
az config param-persist delete resource_group_name

# Remove all persisted parameters entries and do not prompt for confirmation
az config param-persist delete --all --yes
```

> [!IMPORTANT]
>
> Parameter yang bertahan tidak diperbarui saat sumber daya Azure dihapus.
>
> ```azurecli
> # delete a resource group
> az group delete --name RG1forTutorial
>
> # verify that the resource group no longer exists
> az group list --output table
>
> # See that the resource group name remains in persisted parameters
> az config param-persist show
> ```

## <a name="7-turn-persisted-parameters-off"></a>7. Matikan parameter yang bertahan

Anda dapat menonaktifkan parameter yang bertahan dengan menggunakan perintah [az config param-persist off,](/cli/azure/param-persist#az_param_persist_off) tetapi data parameter bertahan yang disimpan tidak akan dihapus.

```azurecli
# Turn persisted parameters off
az config param-persist off

# See that your persisted parameters still exist
az config param-persist show

# Try to create a new resource relying on persisted parameters and receive error "...the following arguments are required:..."
az storage account create --name SA4inAzCLI --sku Standard_LRS
```

## <a name="8-clean-up-resources"></a>8. Membersihkan sumber daya

Bila tidak lagi diperlukan, gunakan perintah [hapus grup az](/cli/azure/group) untuk menghapus grup sumber daya, dan semua sumber daya terkait.

```azurecli
az group delete --name RG1forTutorial
```

## <a name="see-also"></a>Lihat juga

- [(Cara bekerja dengan Azure CLI tetap parameter](param-persist-howto.md)
- [Azure CLI configuration options](/cli/azure/azure-cli-configuration)

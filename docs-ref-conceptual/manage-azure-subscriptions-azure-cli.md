---
title: Cara mengelola langganan Azure – Azure CLI | Microsoft Dokumen
description: Pelajari tentang penyewa, pengguna, dan langganan Azure. Gunakan Azure CLI untuk mengelola langganan Anda, membuat grup manajemen, dan mengunci langganan.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: Langganan Azure, kelola langganan azure, grup manajemen azure, langganan kumpulan azure cli, azure cli pilih langganan
ms.openlocfilehash: 73ddb9674535dee93f0d80d68b57e67b70fef66a
ms.sourcegitcommit: ad79327952adf0f8be8f1b9678e72434d9f03f0c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/12/2022
ms.locfileid: "138520318"
---
# <a name="how-to-manage-azure-subscriptions-with-the-azure-cli"></a>Cara mengelola langganan Azure dengan Azure CLI

Azure CLI membantu Anda mengelola langganan Azure, membuat grup manajemen, dan mengunci langganan.  Anda mungkin memiliki beberapa langganan dalam Azure. Anda dapat menjadi bagian dari lebih dari satu organisasi atau organisasi Anda dapat membagi akses ke sumber daya tertentu di seluruh pengelompokan. Azure CLI mendukung pemilihan langganan baik secara global maupun per perintah.

Untuk informasi terperinci tentang langganan, penagihan, dan manajemen biaya, lihat [dokumentasi penagihan dan manajemen biaya](/azure/billing/).

## <a name="tenants-users-and-subscriptions"></a>Penyewa, pengguna, dan langganan

_Penyewa_ adalah entitas Azure Active Directory yang mencakup seluruh organisasi. Penyewa memiliki satu atau lebih _langganan_ dan _pengguna_. Pengguna adalah individu dan hanya terkait dengan satu penyewa, organisasi tempat mereka berada. Pengguna adalah akun yang masuk ke Azure untuk membuat, mengelola, dan menggunakan sumber daya. Pengguna mungkin memiliki akses ke beberapa _langganan_, yang merupakan perjanjian dengan Microsoft untuk menggunakan layanan cloud, termasuk Azure. Setiap sumber daya dikaitkan dengan langganan.

* Untuk mempelajari selengkapnya tentang perbedaan antara penyewa, pengguna, dan langganan, lihat [kamus terminologi cloud Azure](/azure/azure-glossary-cloud-terminology).
* Untuk mempelajari cara menambahkan langganan baru ke penyewa Azure Active Directory Anda, lihat [Mengaitkan atau menambahkan langganan Azure ke penyewa Azure Active Directory Anda](/azure/active-directory/active-directory-how-subscriptions-associated-directory).
* Untuk mempelajari cara masuk ke penyewa tertentu, lihat [Masuk dengan Azure CLI](./authenticate-azure-cli.md).

## <a name="commands-in-an-azure-subscription"></a>Perintah dalam langganan Azure

Banyak perintah Azure CLI bertindak dalam langganan. Anda selalu dapat menentukan langganan mana yang akan digunakan dengan menggunakan parameter **langganan** dalam perintah Anda. Parameter tersebut bersifat opsional. Jika Anda tidak menentukan langganan, perintah akan menggunakan langganan aktif Anda saat ini.

Untuk melihat langganan yang sedang Anda gunakan atau untuk mendapatkan daftar langganan yang tersedia, jalankan perintah [az account show](/cli/azure/account#az-account-show) atau [az daftar akun](/cli/azure/account#az-account-list) :

```azurecli
# get the current default subscription using show
az account show --output table

# get the current default subscription using list
az account list --query "[?isDefault]"

# get a list of subscriptions except for the default subscription
az account list --query "[?isDefault == \`false\`]"

# get the details of a specific subscription
az account show --subscription MySubscriptionName
```

> [!TIP]
> `--output` Parameternya adalah parameter global, tersedia untuk semua perintah. Nilai **tabel** menyajikan output dalam format yang bersahabat. Untuk informasi selengkapnya, lihat [Format output untuk perintah Azure CLI](/cli/azure/format-output-azure-cli).

Langganan berisi grup sumber daya. Grup sumber daya adalah kontainer yang menampung sumber daya terkait untuk sebuah solusi Azure. Jika perintah anda berfungsi dengan sumber daya dalam langganan aktif anda, anda tidak perlu menentukan `--subscription`.

Perintah ini membuat akun penyimpanan di grup sumber daya yang ditentukan:

```azurecli
az storage account create --resource-group StorageGroups --name storage136 \
    --location eastus --sku Standard_LRS
```

Jika grup penyimpanan bukan bagian dari langganan aktif Anda saat ini, perintah ini gagal.

Jika perlu, ubah langganan aktif, seperti yang dijelaskan di bagian berikutnya, atau tentukan langganan dalam perintah:

```azurecli
az storage account create --resource-group StorageGroups --subscription "My Demos" \
    --name storage136 --location eastus --sku Standard_LRS
```

## <a name="change-the-active-subscription"></a>Mengubah langganan aktif

Anda dapat mengubah langganan aktif dengan menggunakan perintah [az account set](/cli/azure/account#az-account-set) .

Dapatkan daftar langganan Anda dengan perintah [daftar akun az](/cli/azure/account#az-account-list):

```azurecli
az account list --output table
```

Perintah ini mencantumkan semua langganan yang dapat Anda akses. Langganan aktif Anda ditandai seperti `True` di `IsDefault` kolom. Jika Anda tidak melihat langganan yang Anda harapkan, tambahkan `--refresh` parameter untuk mendapatkan daftar langganan terbaru.

Untuk beralih ke langganan lain, gunakan [set akun az](/cli/azure/account#az-account-set) dengan ID langganan atau nama yang ingin Anda alihkan.

```azurecli
az account set --subscription "My Demos"
```

Langganan Anda memiliki nama dan ID, yang merupakan GUID. Anda dapat menggunakan salah satu untuk perintah ini. Jika Anda menggunakan nama yang menyertakan spasi, gunakan tanda kutip.

Jika Anda menjalankan perintah [daftar akun az](/cli/azure/account#az_account_list) lagi, kolom akan `IsDefault` menampilkan langganan aktif Anda saat ini.

## <a name="create-azure-management-groups"></a>Membuat grup manajemen Azure

Grup manajemen Azure berisi langganan. Grup manajemen menyediakan cara untuk mengelola akses, kebijakan, dan kepatuhan untuk langganan tersebut. Untuk informasi selengkapnya, lihat [Apa itu grup manajemen Azure](/azure/governance/management-groups/overview).

Gunakan perintah [az account management-group](/cli/azure/account/management-group) untuk membuat dan mengelola Grup Manajemen Azure.

Anda dapat membuat grup manajemen untuk beberapa langganan dengan menggunakan perintah [buat grup manajemen akun az](/cli/azure/account/management-group#az-account-management-group-create) :

```azurecli
az account management-group create --name Contoso01
```

Untuk melihat semua grup manajemen Anda, gunakan perintah [daftar grup manajemen akun az](/cli/azure/account/management-group#az-account-management-group-list) :

```azurecli
az account management-group list
```

Tambahkan langganan ke grup baru Anda dengan menggunakan perintah [tambahkan langganan az account management-group](/cli/azure/account/management-group/subscription#az-account-management-group-subscription-add) :

```azurecli
az account management-group subscription add --name Contoso01 --subscription "My Demos"
az account management-group subscription add --name Contoso01 --subscription "My Second Demos"
```

Untuk menghapus langganan, gunakan perintah [hapus langganan az account management-group](/cli/azure/account/management-group/subscription#az-account-management-group-subscription-remove) :

```azurecli
az account management-group subscription remove --name Contoso01 --subscription "My Demos"
```

Untuk menghapus grup manajemen, jalankan perintah [hapus grup manajemen akun az](/cli/azure/account/management-group#az-account-management-group-delete) :

```azurecli
az account management-group delete --name Contoso01
```

Menghapus langganan atau menghapus grup manajemen tidak menghapus atau menonaktifkan langganan.

## <a name="set-an-azure-subscription-lock"></a>Mengatur kunci langganan Azure

Sebagai administrator, Anda mungkin perlu mengunci langganan untuk mencegah pengguna menghapus atau memodifikasinya. Untuk informasi selengkapnya, lihat [Kunci sumber daya untuk mencegah perubahan yang tidak terduga](/azure/azure-resource-manager/management/lock-resources).

Di Azure CLI, gunakan perintah [kunci akun az](/cli/azure/account/lock) . Misalnya, perintah [pembuatan kunci akun az](/cli/azure/account/lock#az-account-lock-create) dapat mencegah pengguna menghapus langganan:

```azurecli
az account lock create --name "Cannot delete subscription" --lock-type CanNotDelete
```

> [!NOTE]
> Anda harus memiliki izin yang sesuai untuk membuat atau mengubah kunci.

Untuk melihat kunci saat ini pada langganan Anda, gunakan perintah [daftar kunci akun az](/cli/azure/account/lock#az-account-lock-list) :

```azurecli
az account lock list --output table
```

Jika Anda membuat akun baca-saja, hasilnya menyerupai menetapkan izin peran Reader untuk semua pengguna. Untuk mempelajari tentang pengaturan izin untuk masing-masing pengguna dan peran, lihat [Menambahkan atau menghapus penetapan peran Azure menggunakan Azure CLI](/azure/role-based-access-control/role-assignments-cli).

Untuk melihat detail untuk kunci, gunakan perintah [tampilan kunci akun az](/cli/azure/account/lock#az-account-lock-show) :

```azurecli
az account lock show --name "Cannot delete subscription"
```

Anda dapat menghapus kunci dengan menggunakan perintah [hapus kunci akun az](/cli/azure/account/lock#az-account-lock-delete) :

```azurecli
az account lock delete --name "Cannot delete subscription"
```

## <a name="see-also"></a>Lihat juga

* [Kamus terminologi azure cloud](/azure/azure-glossary-cloud-terminology)
* [Mengaitkan atau menambahkan langganan Azure ke penyewa Azure Active Directory Anda](/azure/active-directory/active-directory-how-subscriptions-associated-directory)
* [Masuk dengan Azure CLI](./authenticate-azure-cli.md)

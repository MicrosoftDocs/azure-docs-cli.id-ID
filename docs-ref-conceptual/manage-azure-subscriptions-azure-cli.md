---
title: Cara mengelola langganan Azure – Azure CLI | Microsoft Docs
description: Pelajari tentang penyewa, pengguna, dan langganan Azure. Gunakan Azure CLI untuk mengelola langganan Anda, membuat grup manajemen, dan mengunci langganan.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: Azure subscriptions, manage azure subscriptions, azure management groups, azure cli set subscription, azure cli select subscription
ms.openlocfilehash: 0d8fb2f42efb727947a0901581a68ce9fb4f4d0e
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439039"
---
# <a name="how-to-manage-azure-subscriptions-with-the-azure-cli"></a>Cara mengelola langganan Azure dengan Azure CLI

Azure CLI membantu Anda mengelola langganan Azure, membuat grup manajemen, dan mengunci langganan.  Anda mungkin memiliki beberapa langganan di Azure. Anda dapat menjadi bagian dari lebih dari satu organisasi atau organisasi Anda dapat membagi akses ke sumber daya tertentu di seluruh pengelompokan. Azure CLI mendukung memilih langganan baik secara global maupun per perintah.

Untuk informasi terperinci tentang langganan, penagihan, dan manajemen biaya, lihat [dokumentasi penagihan dan manajemen biaya.](/azure/billing/)

## <a name="tenants-users-and-subscriptions"></a>Penyewa, pengguna, dan langganan

_Penyewa_ adalah entitas Azure Active Directory yang mencakup seluruh organisasi. Penyewa memiliki satu atau lebih _langganan_ dan _pengguna._ Pengguna adalah individu dan hanya terkait dengan satu penyewa, organisasi tempat mereka berada. Pengguna adalah akun yang masuk ke Azure untuk membuat, mengelola, dan menggunakan sumber daya. Pengguna mungkin memiliki akses ke beberapa _langganan,_ yang merupakan perjanjian dengan Microsoft untuk menggunakan layanan cloud, termasuk Azure. Setiap sumber daya dikaitkan dengan langganan.

* Untuk mempelajari selengkapnya tentang perbedaan antara penyewa, pengguna, dan langganan, lihat [kamus terminologi Azure cloud](/azure/azure-glossary-cloud-terminology).
* Untuk mempelajari cara menambahkan langganan baru ke penyewa Azure Active Directory Anda, lihat [Mengaitkan atau menambahkan langganan Azure ke penyewa Azure Active Directory Anda](/azure/active-directory/active-directory-how-subscriptions-associated-directory).
* Untuk mempelajari cara masuk ke penyewa tertentu, lihat [Masuk dengan Azure CLI](./authenticate-azure-cli.md).

## <a name="commands-in-an-azure-subscription"></a>Commands in an Azure subscription

Banyak perintah Azure CLI bertindak dalam langganan. Anda selalu dapat menentukan langganan mana yang akan digunakan dengan menggunakan parameter **langganan** dalam perintah Anda. Parameter ini bersifat opsional. Jika Anda tidak menentukan langganan, perintah menggunakan langganan aktif Anda saat ini.

Untuk melihat langganan yang saat ini Anda gunakan atau untuk mendapatkan daftar langganan yang tersedia, jalankan perintah [daftar tampilkan akun az](/cli/azure/account#az_account_show) atau [az:](/cli/azure/account#az_account_list)

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

Langganan berisi grup sumber daya. Grup sumber daya adalah kontainer yang menampung sumber daya terkait untuk sebuah solusi Azure. Jika perintah Anda berfungsi dengan sumber daya dalam langganan aktif Anda, Anda tidak perlu `--subscription` menentukan.

Perintah ini membuat akun penyimpanan dalam grup sumber daya yang ditentukan:

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

Anda dapat mengubah langganan aktif anda dengan menggunakan perintah [set akun az.](/cli/azure/account#az_account_set)

Dapatkan daftar langganan Anda dengan perintah [daftar akun az](/cli/azure/account#az_account_list):

```azurecli
az account list --output table
```

Perintah ini mencantumkan semua langganan yang dapat Anda akses. Langganan aktif Anda ditandai seperti `True` di `IsDefault` kolom. Jika Anda tidak melihat langganan yang Anda harapkan, tambahkan `--refresh` parameter untuk mendapatkan daftar langganan terbaru.

Untuk beralih ke langganan yang berbeda, gunakan [pengaturan akun az](/cli/azure/account#az_account_set) dengan ID langganan atau nama yang ingin Anda alihkan.

```azurecli
az account set --subscription "My Demos"
```

Langganan Anda memiliki nama dan ID, yang merupakan GUID. Anda dapat menggunakan baik untuk perintah ini. Jika Anda menggunakan nama yang menyertakan spasi, gunakan tanda kutip.

Jika Anda menjalankan perintah [daftar akun az](/cli/azure/account#az_account_list) lagi, kolom memperlihatkan langganan aktif Anda saat `IsDefault` ini.

## <a name="create-azure-management-groups"></a>Create Azure management groups

Azure management groups contain subscriptions. Kelompok manajemen menyediakan cara untuk mengelola akses, kebijakan, dan kepatuhan untuk langganan tersebut. Untuk informasi lebih lanjut, lihat [Apa itu grup manajemen Azure](/azure/governance/management-groups/overview).

Gunakan perintah [az account management-group](/cli/azure/account/management-group) untuk membuat dan mengelola Azure Management Groups.

Anda dapat membuat grup manajemen untuk beberapa langganan Anda dengan menggunakan perintah [buat grup manajemen akun az:](/cli/azure/account/management-group#az_account_management_group_create)

```azurecli
az account management-group create --name Contoso01
```

Untuk melihat semua grup manajemen Anda, gunakan perintah [daftar grup manajemen akun az:](/cli/azure/account/management-group#az_account_management_group_list)

```azurecli
az account management-group list
```

Tambahkan langganan ke grup baru Anda dengan menggunakan perintah [tambahkan langganan grup manajemen akun az:](/cli/azure/account/management-group/subscription#az_account_management_group_subscription_add)

```azurecli
az account management-group subscription add --name Contoso01 --subscription "My Demos"
az account management-group subscription add --name Contoso01 --subscription "My Second Demos"
```

Untuk menghapus langganan, gunakan perintah [hapus langganan grup manajemen akun az:](/cli/azure/account/management-group/subscription#az_account_management_group_subscription_remove)

```azurecli
az account management-group subscription remove --name Contoso01 --subscription "My Demos"
```

Untuk menghapus grup manajemen, jalankan perintah [hapus grup manajemen akun az:](/cli/azure/account/management-group#az_account_management_group_delete)

```azurecli
az account management-group delete --name Contoso01
```

Menghapus langganan atau menghapus grup manajemen tidak menghapus atau menonaktifkan langganan.

## <a name="set-an-azure-subscription-lock"></a>Mengatur kunci langganan Azure

Sebagai administrator, Anda mungkin perlu mengunci langganan untuk mencegah pengguna menghapus atau memodifikasinya. Untuk informasi selengkapnya, lihat [Kunci sumber daya untuk mencegah perubahan yang tidak terduga](/azure/azure-resource-manager/management/lock-resources).

In Azure CLI, gunakan perintah [kunci akun az.](/cli/azure/account/lock) Misalnya, perintah [buat kunci akun az](/cli/azure/account/lock#az_account_lock_create) dapat mencegah pengguna menghapus langganan:

```azurecli
az account lock create --name "Cannot delete subscription" --lock-type CanNotDelete
```

> [!NOTE]
> Anda harus memiliki izin yang sesuai untuk membuat atau mengubah kunci.

Untuk melihat kunci saat ini pada langganan Anda, gunakan perintah [daftar kunci akun az:](/cli/azure/account/lock#az_account_lock_list)

```azurecli
az account lock list --output table
```

Jika Anda membuat akun baca-saja, hasilnya menyerupai menetapkan izin peran Pembaca untuk semua pengguna. Untuk mempelajari tentang pengaturan izin untuk pengguna dan peran individual, lihat [Menambahkan atau menghapus tugas peran Azure menggunakan Azure CLI](/azure/role-based-access-control/role-assignments-cli).

Untuk melihat detail untuk kunci, gunakan perintah [tampilan kunci akun az:](/cli/azure/account/lock#az_account_lock_show)

```azurecli
az account lock show --name "Cannot delete subscription"
```

Anda dapat menghapus kunci dengan menggunakan perintah [hapus kunci akun az:](/cli/azure/account/lock#az_account_lock_delete)

```azurecli
az account lock delete --name "Cannot delete subscription"
```

## <a name="see-also"></a>Lihat juga

* [Azure cloud terminology dictionary](/azure/azure-glossary-cloud-terminology)
* [Mengaitkan atau menambahkan langganan Azure ke penyewa Azure Active Directory Anda](/azure/active-directory/active-directory-how-subscriptions-associated-directory)
* [Masuk dengan Azure CLI](./authenticate-azure-cli.md)

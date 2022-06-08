---
title: Cara mengelola langganan Azure – Azure CLI | Microsoft Docs
description: Pelajari tentang penyewa, pengguna, dan langganan Azure. Gunakan Azure CLI untuk mengelola langganan Anda, membuat grup manajemen, dan mengunci langganan.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 05/27/2022
ms.topic: conceptual
ms.service: azure-cli
ms.tool: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: Langganan Azure, kelola langganan Azure, grup manajemen Azure, langganan set Azure cli, langganan pilih Azure cli
ms.openlocfilehash: b2f6d59d4c738e888ced2d99be57781d0026ff15
ms.sourcegitcommit: 2a38060aef3a6574be9863b222b9daa6c6d11ece
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 06/08/2022
ms.locfileid: "146185963"
---
# <a name="how-to-manage-azure-subscriptions-with-the-azure-cli"></a>Cara mengelola langganan Azure dengan Azure CLI

Azure CLI membantu Anda mengelola langganan Azure, membuat grup manajemen, dan mengunci langganan.  Anda mungkin memiliki beberapa langganan dalam Azure. Anda dapat menjadi bagian dari lebih dari satu organisasi atau organisasi Anda mungkin membagi akses ke sumber daya tertentu di seluruh pengelompokan. Azure CLI mendukung pemilihan langganan baik secara global maupun per perintah.

Untuk informasi mendetail tentang langganan, penagihan, dan manajemen biaya, lihat [dokumentasi manajemen biaya dan penagihan](/azure/billing/).

## <a name="tenants-users-and-subscriptions"></a>Penyewa, pengguna, dan langganan

_Penyewa_ adalah entitas Azure Active Directory yang mencakup seluruh organisasi. Penyewa memiliki satu atau beberapa _langganan_ dan _pengguna_. Pengguna adalah akun yang masuk ke Azure untuk membuat, mengelola, dan menggunakan sumber daya. Pengguna mungkin memiliki akses ke beberapa _langganan_, tetapi pengguna hanya dikaitkan dengan satu penyewa.  _Langganan_ adalah perjanjian dengan Microsoft untuk menggunakan layanan cloud, termasuk Azure. Setiap sumber daya dikaitkan dengan langganan.

Untuk mempelajari selengkapnya tentang perbedaan antara penyewa, pengguna, dan langganan, lihat [Kamus terminologi cloud Azure](/azure/azure-glossary-cloud-terminology).

## <a name="get-the-active-tenant"></a>Mendapatkan penyewa aktif

Gunakan [az account tenant list](/cli/azure/account/tenant) atau [az account show](/cli/azure/account#az-account-show) untuk mendapatkan ID penyewa aktif.
```azurecli-interactive
az account tenant list

az account show
```

## <a name="change-the-active-tenant"></a>Mengubah penyewa aktif

Untuk beralih penyewa, Anda perlu masuk sebagai pengguna dalam penyewa yang diinginkan.  Gunakan [az login](/cli/azure/reference-index#az-login-examples) untuk mengubah penyewa aktif dan memperbarui daftar langganan tempat Anda berada.

```azurecli-interactive
# sign in as a different user
az login --user <myAlias@myCompany.com> -password <myPassword>

# sign in with a different tenant
az login --tenant <myTenantID>
```

Jika organisasi Anda memerlukan autentikasi multifaktor, Anda mungkin menerima kesalahan ini saat menggunakan `az login --user`:

```output
Due to a configuration change made by your administrator, or because you moved to a new location, you must use multi-factor authentication to access...
```

Menggunakan perintah alternatif `az login --tenant` akan meminta Anda untuk membuka halaman HTTPS dan memasukkan kode yang disediakan.  Anda kemudian dapat menggunakan autentikasi multifaktor dan berhasil masuk.  Untuk mempelajari selengkapnya tentang opsi masuk dengan azure CLI, lihat [Masuk dengan Azure CLI](./authenticate-azure-cli.md).

## <a name="get-the-active-subscription"></a>Mendapatkan langganan aktif

Sebagian besar perintah Azure CLI bertindak dalam langganan.  Untuk keamanan optimal, perintah Azure CLI tidak lagi default ID langganan ke langganan Aktif Anda saat ini.  Sekarang Anda harus menentukan langganan untuk dikerjakan dengan menggunakan `--subscription` parameter atau `--scope` dalam perintah Anda.

Untuk melihat langganan yang saat ini Anda gunakan atau untuk mendapatkan daftar langganan yang tersedia, jalankan perintah [az account show](/cli/azure/account#az-account-show) atau [az account list](/cli/azure/account#az-account-list) .  Buka [Pelajari cara menggunakan Bash dengan Azure CLI](azure-cli-learn-bash.md#querying-and-formatting-single-values-and-nested-values) untuk melihat contoh cara menggunakan `az account show`lainnya.

```azurecli-interactive
# get the current default subscription using show
az account show --output table

# get the current default subscription using list
az account list --query "[?isDefault]"

# store the default subscription  in a variable
subscriptionId="$(az account list --query "[?isDefault].id" -o tsv)"
echo $subscriptionId
```

> [!TIP]
> `--output` Parameternya adalah parameter global, tersedia untuk semua perintah. Nilai **tabel** menyajikan output dalam format yang bersahabat. Untuk informasi selengkapnya, lihat [Format output untuk perintah Azure CLI](./format-output-azure-cli.md).

Langganan berisi grup sumber daya. Grup sumber daya adalah kontainer yang menampung sumber daya terkait untuk sebuah solusi Azure. Untuk mempelajari cara mengelola grup sumber daya dalam langganan Anda, lihat [Cara mengelola grup sumber daya Azure dengan Azure CLI](manage-azure-groups-azure-cli.md)

## <a name="change-the-active-subscription"></a>Mengubah langganan aktif

Langganan Azure memiliki nama dan ID.  Anda dapat beralih ke langganan lain menggunakan [set akun az](/cli/azure/account#az-account-set) yang menentukan ID atau nama langganan yang diinginkan.

```azurecli-interactive
# change the active subscription using the subscription name
az account set --subscription "My Demos"

# change the active subscription using the subscription ID
az account set --subscription "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"

# change the active subscription using a variable
subscriptionId="$(az account list --query "[?isDefault].id" -o tsv)"
az account set --subscription $subscriptionId
```

Anda tidak dapat mengubah langganan aktif Anda menjadi langganan _dalam penyewa lain_ menggunakan `az account set` perintah .  Anda harus terlebih dahulu masuk sebagai pengguna dalam penyewa yang diinginkan.  Jika Anda mencoba dan mengatur langganan ke langganan dalam penyewa lain, Anda akan menerima kesalahan ini:

```output
The subscription of 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx' doesn't exist in cloud 'AzureCloud'.
```

Untuk mempelajari cara menambahkan langganan baru ke penyewa Azure Active Directory Anda, lihat [Mengaitkan atau menambahkan langganan Azure ke penyewa Azure Active Directory Anda](/azure/active-directory/active-directory-how-subscriptions-associated-directory).

## <a name="create-azure-management-groups"></a>Membuat grup manajemen Azure

Grup manajemen Azure berisi langganan. Grup manajemen menyediakan cara untuk mengelola akses, kebijakan, dan kepatuhan untuk langganan tersebut. Untuk informasi selengkapnya, lihat [Apa yang dimaksud dengan grup manajemen Azure](/azure/governance/management-groups/overview).

Gunakan perintah [az account management-group](../latest/docs-ref-autogen/account/management-group.yml) untuk membuat dan mengelola Azure Management Groups.

Anda dapat membuat grup manajemen untuk beberapa langganan Anda dengan menggunakan perintah [az account management-group create](/cli/azure/account/management-group#az-account-management-group-create):

```azurecli-interactive
az account management-group create --name Contoso01
```

Untuk melihat semua grup manajemen Anda, gunakan perintah [az account management-group list](/cli/azure/account/management-group#az-account-management-group-list):

```azurecli-interactive
az account management-group list
```

Tambahkan langganan ke grup baru Anda dengan menggunakan perintah [az account management-group subscription add](/cli/azure/account/management-group/subscription#az-account-management-group-subscription-add):

```azurecli-interactive
az account management-group subscription add --name Contoso01 --subscription "My Demos"
az account management-group subscription add --name Contoso01 --subscription "My Second Demos"
```

Untuk menghapus langganan, gunakan perintah [az account management-group subscription remove](/cli/azure/account/management-group/subscription#az-account-management-group-subscription-remove):

```azurecli-interactive
az account management-group subscription remove --name Contoso01 --subscription "My Demos"
```

Untuk menghapus grup manajemen, jalankan perintah [az account management-group delete](/cli/azure/account/management-group#az-account-management-group-delete):

```azurecli-interactive
az account management-group delete --name Contoso01
```

Menghapus langganan atau menghapus grup manajemen tidak menghapus atau menonaktifkan langganan.

## <a name="set-an-azure-subscription-lock"></a>Mengatur kunci langganan Azure

Sebagai administrator, Anda mungkin perlu mengunci langganan untuk mencegah pengguna menghapus atau memodifikasinya. Untuk informasi selengkapnya, lihat [Kunci sumber daya untuk mencegah perubahan yang tidak terduga](/azure/azure-resource-manager/management/lock-resources).

Di Azure CLI, gunakan perintah [az account lock](../latest/docs-ref-autogen/account/lock.yml). Misalnya, perintah [az account lock create](/cli/azure/account/lock#az-account-lock-create) dapat mencegah pengguna menghapus langganan:

```azurecli-interactive
az account lock create --name "Cannot delete subscription" --lock-type CanNotDelete
```

> [!NOTE]
> Anda harus memiliki izin yang sesuai untuk membuat atau mengubah kunci.

Untuk melihat gembok saat ini pada langganan Anda, gunakan perintah [az account lock list](/cli/azure/account/lock#az-account-lock-list):

```azurecli-interactive
az account lock list --output table
```

Jika Anda membuat akun baca saja, hasilnya seperti pemberian izin peran Pembaca untuk semua pengguna. Untuk mempelajari tentang mengatur izin untuk setiap pengguna dan peran, lihat [Menambahkan atau menghapus penetapan peran Azure menggunakan Azure CLI](/azure/role-based-access-control/role-assignments-cli).

Untuk melihat detail kunci, gunakan perintah [az account lock show](/cli/azure/account/lock#az-account-lock-show):

```azurecli-interactive
az account lock show --name "Cannot delete subscription"
```

Anda dapat menghapus kunci dengan menggunakan perintah [az account lock delete](/cli/azure/account/lock#az-account-lock-delete):

```azurecli-interactive
az account lock delete --name "Cannot delete subscription"
```

## <a name="see-also"></a>Lihat juga

* [Kamus terminologi cloud Azure](/azure/azure-glossary-cloud-terminology)
* [Mengaitkan atau menambahkan langganan Azure ke penyewa Azure Active Directory Anda](/azure/active-directory/active-directory-how-subscriptions-associated-directory)
* [Mengelola grup sumber daya](./manage-azure-groups-azure-cli.md)

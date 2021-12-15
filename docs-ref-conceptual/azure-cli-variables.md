---
title: Cara menggunakan variabel dalam perintah Azure CLI | Microsoft Docs
description: Pelajari tentang menentukan nilai secara langsung dalam perintah Azure CLI dengan menggunakan variabel shell, mengatur langganan, membuat nilai default, atau menggunakan nilai persisten.
author: dbradish-microsoft
ms.author: dbradish
ms.service: azure-cli
ms.topic: how-to
ms.date: 08/01/2021
ms.custom: template-how-to, devx-track-azurecli, seo-azure-cli
keywords: azure cli variables, azure cli commands, value of variable, shell variables
ms.openlocfilehash: 7e524e834be80117d4e2e69b69a07019b7f12389
ms.sourcegitcommit: 62469e9c1ad07f215129ece5db89c530f1a77968
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 12/15/2021
ms.locfileid: "135155922"
---
# <a name="how-to-use-variables-in-azure-cli-commands"></a>Cara menggunakan variabel dalam perintah Azure CLI

Selain menentukan nilai secara langsung dalam perintah, Anda dapat memberikan nilai dalam beberapa cara:

* Menggunakan variabel shell
* Mengatur langganan untuk digunakan dalam beberapa perintah
* Membuat nilai default untuk beberapa parameter
* Menggunakan nilai persisten untuk beberapa parameter

Artikel ini membahas berbagai cara untuk menentukan nilai dalam perintah Azure CLI.

[!INCLUDE [azure-cli-prepare-your-environment.md](includes/azure-cli-prepare-your-environment.md)]

## <a name="use-shell-variables"></a>Menggunakan variabel shell

Azure CLI berjalan di shell. Artikel ini menggunakan Bash. Untuk informasi tentang shell lain, lihat [Gunakan Azure CLI secara efektif](/cli/azure/use-cli-effectively). Anda dapat menggunakan variabel di Bash untuk meneruskan nilai untuk perintah parameter. Menggunakan variabel dengan Azure CLI juga memungkinkan penggunaan kembali perintah, baik sedikit demi sedikit atau dalam skrip.

Contoh ini membuat disk penyimpanan baru dengan jenis yang sama dengan disk penyimpanan pada mesin virtual yang ada.

```azurecli
# Assign values to variables
MyResourceGroup=ContosoRGforVM
MySubscription="Contoso subscription"
vmName=VM01

# Get a value for a variable based on an existing virtual machine
osType=$(az vm get-instance-view --resource-group $MyResourceGroup \
   --name $vmName --subscription "$MySubscription" \
   --query 'storageProfile.osDisk.osType' --output tsv)

# Create a disk of the same type by using the variable value
az disk create --resource-group $MyResourceGroup --name DestinationDisk --size-gb 20 --os-type $osType
```

Contoh ini menunjukkan cara menetapkan nilai ke variabel yang digunakan kembali, seperti **MyResourceGroup**. Perintah mendapat nilai untuk ditetapkan ke **osType**.

Saat Anda menetapkan nilai ke variabel dari perintah lain, pastikan perintah menggunakan format output yang kompatibel. Perintah [az vm get-instance-view](/cli/azure/vm#az_vm_get_instance_view) menggunakan `tsv` format output. Opsi ini mengembalikan nilai tanpa pemformatan tambahan, tombol, atau simbol lainnya. Beberapa format output termasuk struktur atau karakter seperti tanda kutip. Untuk informasi selengkapnya, lihat [Format output untuk perintah Azure CLI](/cli/azure/format-output-azure-cli).

Dalam contoh ini, variabel **MySubscription** harus dalam tanda kutip. Nilai variabel berisi spasi, yang perintah tidak dapat mengurai. Jika Anda hanya bekerja dengan KARTU LANGGANAN, Anda tidak perlu menggunakan tanda kutip.

## <a name="set-a-subscription"></a>Mengatur langganan

Banyak perintah memerlukan langganan tertentu. Azure resources exist in resource groups, yang ada dalam langganan. Azure CLI menggunakan langganan default saat Anda berada dalam sesi. Untuk melihat nilai langganan Anda saat ini, jalankan perintah [perlihatkan akun az:](/cli/azure/account#az_account_show)

```azurecli
az account show --output table
```

Anda mungkin hanya memiliki akses ke satu langganan. Untuk informasi selengkapnya, lihat [Menggunakan langganan Azure dengan Azure CLI](/cli/azure/manage-azure-subscriptions-azure-cli) Anda dapat menggunakan perintah set akun [az](/cli/azure/account#az_account_set) untuk mengatur langganan Anda saat ini:

```azurecli
az account set --subscription "My Demos"
```

Setelah Anda mengatur langganan, Anda dapat menghilangkan `--Subscription` parameter. Untuk informasi selengkapnya, lihat [Gunakan langganan Azure dengan Azure CLI](manage-azure-subscriptions-azure-cli.md).

## <a name="create-default-values"></a>Membuat nilai default

Anda dapat mengatur nilai untuk beberapa parameter dengan menggunakan perintah [az config set.](/cli/azure/config#az_config_set) Contoh ini menetapkan grup sumber daya default:

```azurecli
az config set defaults.group=ContosoRGforVM
```

Setelah menjalankan perintah ini, Anda dapat menjalankan perintah berikut untuk membuat akun penyimpanan di grup sumber daya ContosoRGforVM:

```azurecli
az storage account create --name storage135 --location eastus --sku Standard_LRS
```

Perhatikan bahwa tidak ada grup sumber daya yang ditentukan dalam perintah. Untuk informasi selengkapnya, lihat [Mengatur grup sumber daya default](manage-azure-groups-azure-cli.md#set-a-default-resource-group).

> [!TIP]
> Perintah mendapatkan nilai untuk parameter dengan cara yang berbeda dapat membingungkan. Jika perintah memberikan hasil yang tidak terduga, seperti tidak dapat menemukan grup sumber daya, mungkin ada nilai default.
>
> Jika Anda mengalami kesalahan, jalankan perintah lagi dengan parameter dan nilai yang ditentukan. Nilai eksplisit untuk parameter selalu diutamakan daripada opsi lain.

Anda dapat menentukan nilai untuk beberapa parameter dengan cara ini. Untuk informasi selengkapnya, lihat [Konfigurasi Azure CLI](azure-cli-configuration.md).

## <a name="use-persistent-values"></a>Menggunakan nilai persisten

Nilai parameter yang bertahan memungkinkan Anda menentukan nilai hanya sekali. Jika Anda melakukan beberapa tindakan terkait dalam grup sumber daya, Anda tidak perlu menentukan grup tersebut berulang kali.

Jalankan perintah ini untuk mempertahankan nilai parameter:

```azurecli
az config param-persist on
```

Setelah mengaktifkan ketekunan, buat grup sumber daya:

 ```azurecli
az group create --name ContosoStorageRG --location eastus
```

Selama ketekunan menyala, Anda dapat meninggalkan `--resource-group` parameter dari perintah masa depan. Perintah berikut membuat akun penyimpanan di grup sumber daya ContosoStorageRG:

```azurecli
az storage account create --name storage135 --location eastus --sku Standard_LRS
```

Untuk informasi lebih lanjut, lihat [Azure CLI persisted parameter](/cli/azure/param-persist-howto).

## <a name="clean-up-resources"></a>Membersihkan sumber daya

Jika Anda membuat sumber daya untuk mencoba salah satu perintah dalam artikel ini, Anda dapat menghapusnya dengan menggunakan perintah [hapus grup az:](/cli/azure/group#az_group_delete)

```azurecli
az group delete --name ContosoRGforVM
az group delete --name ContosoStorageRG
```

Perintah ini menghapus grup dan semua sumber daya yang dikandungnya sekaligus.

Anda dapat menghapus parameter persisten dengan menjalankan perintah [hapus az config param-persist:](/cli/azure/config/param-persist#az_config_param_persist_delete)

```azurecli
az config param-persist delete --all
```

## <a name="next-steps"></a>Langkah berikutnya

* [Azure CLI persisted parameter](param-persist-howto.md)
* [Bekerja dengan grup sumber daya di Azure CLI](manage-azure-groups-azure-cli.md)
* [Create an Azure support request in Azure CLI](azure-cli-support-request.md)

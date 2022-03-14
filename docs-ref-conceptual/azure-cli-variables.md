---
title: Cara menggunakan variabel di perintah Azure CLI | Microsoft Docs
description: Pelajari cara menentukan nilai secara langsung di perintah Azure CLI dengan menggunakan variabel shell, mengatur langganan, membuat nilai default, atau menggunakan nilai persisten.
author: dbradish-microsoft
ms.author: dbradish
ms.service: azure-cli
ms.topic: how-to
ms.date: 08/01/2021
ms.custom: template-how-to, devx-track-azurecli, seo-azure-cli
keywords: variabel azure cli, perintah azure cli, nilai variabel, variabel shell
ms.openlocfilehash: 7e524e834be80117d4e2e69b69a07019b7f12389
ms.sourcegitcommit: 62469e9c1ad07f215129ece5db89c530f1a77968
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 12/15/2021
ms.locfileid: "135155922"
---
# <a name="how-to-use-variables-in-azure-cli-commands"></a>Cara menggunakan variabel dalam perintah Azure CLI

Selain menentukan nilai secara langsung dalam perintah, Anda dapat memberikan nilai dengan beberapa cara:

* Menggunakan variabel shell
* Mengatur langganan untuk digunakan dalam beberapa perintah
* Membuat nilai default untuk beberapa parameter
* Menggunakan nilai persisten untuk beberapa parameter

Artikel ini membahas berbagai cara untuk menentukan nilai dalam perintah Azure CLI.

[!INCLUDE [azure-cli-prepare-your-environment.md](includes/azure-cli-prepare-your-environment.md)]

## <a name="use-shell-variables"></a>Menggunakan variabel shell

Azure CLI berjalan di dalam shell. Artikel ini menggunakan Bash. Untuk informasi tentang shell lain, lihat [Menggunakan Azure CLI secara efektif](/cli/azure/use-cli-effectively). Anda dapat menggunakan variabel di Bash untuk meneruskan nilai untuk parameter ke perintah. Penggunaan variabel dengan Azure CLI juga memungkinkan perintah digunakan kembali, baik sedikit demi sedikit maupun dalam skrip.

Contoh ini membuat disk penyimpanan baru dengan jenis yang sama dengan disk penyimpanan di mesin virtual yang ada.

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

Saat Anda menetapkan nilai ke variabel dari perintah lain, pastikan perintah menggunakan format output yang kompatibel. Perintah [az vm get-instance-view](/cli/azure/vm#az_vm_get_instance_view) menggunakan format output `tsv`. Opsi ini menampilkan nilai tanpa pemformatan tambahan, kunci, atau simbol lainnya. Beberapa format output mencakup struktur atau karakter seperti tanda kutip. Untuk informasi selengkapnya, lihat [Format output untuk perintah Azure CLI](/cli/azure/format-output-azure-cli).

Dalam contoh ini, variabel **MySubscription** harus dalam tanda kutip. Nilai variabel berisi spasi, yang tidak dapat diurai oleh perintah. Jika hanya bekerja dengan ID langganan, Anda tidak perlu menggunakan tanda kutip.

## <a name="set-a-subscription"></a>Menetapkan langganan

Banyak perintah memerlukan langganan tertentu. Sumber daya Azure ada di grup sumber daya, yang ada di langganan. Azure CLI menggunakan langganan default saat Anda berada dalam sesi. Untuk melihat nilai langganan Anda saat ini, jalankan perintah [az account show](/cli/azure/account#az_account_show):

```azurecli
az account show --output table
```

Anda mungkin hanya memiliki akses ke satu langganan. Untuk informasi selengkapnya, lihat [Menggunakan langganan Azure dengan Azure CLI](/cli/azure/manage-azure-subscriptions-azure-cli). Anda dapat menggunakan perintah [az account set](/cli/azure/account#az_account_set) untuk mengatur langganan Anda saat ini:

```azurecli
az account set --subscription "My Demos"
```

Setelah mengatur langganan, Anda dapat menghilangkan parameter `--Subscription`. Untuk informasi selengkapnya, lihat [Menggunakan langganan Azure dengan Azure CLI](manage-azure-subscriptions-azure-cli.md).

## <a name="create-default-values"></a>Membuat nilai default

Anda dapat mengatur nilai untuk beberapa parameter dengan menggunakan perintah [az config set](/cli/azure/config#az_config_set). Contoh ini menetapkan grup sumber daya default:

```azurecli
az config set defaults.group=ContosoRGforVM
```

Setelah menjalankan perintah ini, Anda dapat menjalankan perintah berikut untuk membuat akun penyimpanan di grup sumber daya ContosoRGforVM:

```azurecli
az storage account create --name storage135 --location eastus --sku Standard_LRS
```

Perhatikan bahwa tidak ada grup sumber daya yang ditentukan dalam perintah. Untuk informasi selengkapnya, lihat [Menetapkan grup sumber daya](manage-azure-groups-azure-cli.md#set-a-default-resource-group).

> [!TIP]
> Perintah yang mendapatkan nilai untuk parameter dengan berbagai cara bisa membingungkan. Jika perintah memberikan hasil yang tidak terduga, seperti tidak dapat menemukan grup sumber daya, mungkin ada nilai default.
>
> Jika Anda mengalami kesalahan, jalankan perintah lagi dengan parameter dan nilai yang ditentukan. Nilai eksplisit untuk parameter selalu lebih diprioritaskan daripada opsi lain.

Anda dapat menentukan nilai untuk beberapa parameter dengan cara ini. Untuk informasi selengkapnya, lihat [Konfigurasi Azure CLI](azure-cli-configuration.md).

## <a name="use-persistent-values"></a>Menggunakan nilai persisten

Nilai parameter tetap memungkinkan Anda menentukan nilai hanya sekali. Jika Anda melakukan beberapa tindakan terkait dalam grup sumber daya, Anda tidak perlu menentukan grup tersebut berulang kali.

Jalankan perintah ini untuk mempertahankan nilai parameter:

```azurecli
az config param-persist on
```

Setelah mengaktifkan persistensi, buat grup sumber daya:

 ```azurecli
az group create --name ContosoStorageRG --location eastus
```

Selama persistensi aktif, Anda dapat mengeluarkan parameter `--resource-group` dari perintah di masa mendatang. Perintah berikut membuat akun penyimpanan di grup sumber daya ContosoStorageRG:

```azurecli
az storage account create --name storage135 --location eastus --sku Standard_LRS
```

Untuk informasi selengkapnya, lihat [Parameter tetap Azure CLI](/cli/azure/param-persist-howto).

## <a name="clean-up-resources"></a>Membersihkan sumber daya

Jika membuat sumber daya untuk mencoba salah satu perintah dalam artikel ini, Anda dapat menghapusnya dengan menggunakan perintah [az group delete](/cli/azure/group#az_group_delete):

```azurecli
az group delete --name ContosoRGforVM
az group delete --name ContosoStorageRG
```

Perintah ini menghapus grup dan semua sumber daya yang dikandungnya sekaligus.

Anda dapat menghapus parameter persisten dengan menjalankan perintah [az config param-persist delete](/cli/azure/config/param-persist#az_config_param_persist_delete):

```azurecli
az config param-persist delete --all
```

## <a name="next-steps"></a>Langkah berikutnya

* [Parameter tetap Azure CLI](param-persist-howto.md)
* [Bekerja dengan grup sumber daya di Azure CLI](manage-azure-groups-azure-cli.md)
* [Membuat permintaan dukungan Azure di Azure CLI](azure-cli-support-request.md)

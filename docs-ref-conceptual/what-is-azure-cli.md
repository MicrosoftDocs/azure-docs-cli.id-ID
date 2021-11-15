---
title: Apa itu Azure CLI? | Microsoft Docs
description: Azure Command-Line Interface (CLI) adalah alat baris perintah yang dirancang untuk membuat dan mengelola sumber daya Azure yang tersedia dalam Windows, macOS, Linux, dan docker containers.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 9/21/2021
ms.topic: overview
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: command line interface, azure cli, azure command line, azure command line interface, what is cli, azure cli examples
ms.openlocfilehash: 91dfce42e36c30658451a0426d9e5146bb9c7c5f
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439097"
---
# <a name="what-is-the-azure-cli"></a>Apa itu Azure CLI?

Azure Command-Line Interface (CLI) adalah alat baris perintah lintas platform untuk terhubung ke Azure dan menjalankan perintah administratif pada sumber daya Azure. Alat ini memungkinkan eksekusi perintah melalui terminal menggunakan perintah baris perintah interaktif atau skrip.

Untuk penggunaan interaktif, Anda terlebih dahulu meluncurkan shell seperti cmd.exe di Windows, atau Bash di Linux atau macOS, dan kemudian mengeluarkan perintah di shell prompt. Untuk mengotomatiskan tugas berulang, Anda menyusun perintah CLI ke dalam skrip shell menggunakan sintaks skrip shell yang Anda pilih, lalu Anda menjalankan skrip.

Anda dapat menginstal Azure CLI secara lokal di Linux, Mac, atau komputer Windows. Ini juga dapat digunakan dari browser melalui Azure Cloud Shell atau dijalankan dari dalam kontainer Docker.

## <a name="current-version"></a>Versi Saat Ini

[!INCLUDE [current-version](includes/current-version.md)]

## <a name="prepare-your-environment"></a>Siapkan lingkunganmu

Sebelum menjalankan perintah Azure CLI, Anda perlu mengatur lingkungan Anda.  

[!INCLUDE [prerequisites](includes/azure-cli-prepare-your-environment-no-header.md)]

## <a name="azure-cli-examples"></a>Contoh Azure CLI
Artikel ini memberikan contoh Azure CLI yang berbeda untuk hal-hal berikut:
- Sintaks langganan
- Sintaks tugas peran
- Sintaks PowerShell


## <a name="subscription-syntax-example"></a>Contoh sintaks langganan

Sintaks Azure CLI mengikuti `reference name`  -  `command`  -  `parameter`  -  `parameter value` pola sederhana.  Misalnya, beralih di antara langganan sering merupakan tugas umum.  Berikut adalah sintaksisnya.

```azurecli
az account set --subscription "my subscription name"
```

Sekarang, betapa mudahnya itu ?!  Lihat [Mengelola langganan dengan Azure CLI](manage-azure-subscriptions-azure-cli.md) untuk mempelajari selengkapnya tentang menggunakan Azure CLI untuk bekerja dengan langganan dan membuat grup manajemen.

## <a name="role-assignment-syntax-example"></a>Contoh sintaks tugas peran

Penggunaan umum lain dari Azure CLI adalah mengelola tugas peran. 

```azurecli
az role assignment create --assignee servicePrincipalName --role Reader
az role assignment delete --assignee userSign-inName --role Contributor
```

Lihat [Membuat prinsip layanan Azure dengan Azure CLI](create-an-azure-service-principal-azure-cli.md) untuk turorial mendalam dalam mengelola prinsipal layanan dan tugas peran.

## <a name="powershell-syntax-comparison"></a>Perbandingan sintaks PowerShell

[Pilih alat baris perintah yang tepat](choose-the-right-azure-command-line-tool.md) menjelaskan perbedaan antara dan dengan penekanan pada Azure CLI dan `tools` `environments` Azure PowerShell.  Ini juga memberikan banyak [perbandingan perintah berdampingan.](choose-the-right-azure-command-line-tool.md#azure-cli-vs-azure-powershell-side-by-side-command-comparison)  Berikut adalah dua contoh:

|Perintah|Azure CLI|Azure PowerShell|
| --- | --- | --- |
| Membuat Grup Sumber Daya | az group create --name \<ResourceGroupName> --location eastus |New-AzResourceGroup -Nama \<ResourceGroupName> -Lokasi Eastus
| Membuat Akun Azure Storage | az akun penyimpanan create --name \<StorageAccountName> --resource-group \<ResourceGroupName> --location eastus --sku Standard_LRS --kind StorageV2 | New-AzStorageAccount -Nama \<StorageAccountName> -ResourceGroupName \<ResourceGroupName> -Location eastus -SkuName Standard_LRS -Kind StorageV2

## <a name="see-also"></a>Lihat juga

- [Mulai menggunakan Azure CLI](get-started-with-azure-cli.md)
- [Control Azure services with the Azure CLI](/learn/modules/control-azure-services-with-cli/)
- [Daftar referensi perintah lengkap untuk Azure CLI](/cli/azure/reference-index)
- [Azure resources that the Azure CLI can manage](azure-services-the-azure-cli-can-manage.md)
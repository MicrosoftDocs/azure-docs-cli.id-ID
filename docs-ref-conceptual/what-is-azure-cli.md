---
title: Apa itu Azure CLI? | Microsoft Docs
description: Azure Command-Line Interface (CLI) adalah alat baris perintah yang dirancang untuk membuat dan mengelola sumber daya Azure yang tersedia di kontainer Windows, macOS, Linux, dan Docker.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 9/21/2021
ms.topic: overview
ms.service: azure-cli
ms.tool: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: antarmuka baris perintah, azure cli, baris perintah azure, antarmuka baris perintah azure, apa itu cli, contoh azure cli
ms.openlocfilehash: c959f60cf3b782569855e2f0a1ef653dfdbec3af
ms.sourcegitcommit: 4972b72ce712edcacb644e2e0fd8a51b9d7ec0d9
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 06/22/2022
ms.locfileid: "146542079"
---
# <a name="what-is-the-azure-cli"></a>Apa itu Azure CLI?

Azure Command-Line Interface (CLI) adalah alat baris perintah lintas platform untuk terhubung ke Azure dan menjalankan perintah administratif pada sumber daya Azure. Alat ini memungkinkan eksekusi perintah melalui terminal menggunakan perintah baris perintah interaktif atau skrip.

Untuk penggunaan interaktif, luncurkan shell terlebih dahulu seperti cmd.exe di Windows, atau Bash di Linux atau macOS, lalu buat perintah di permintaan shell. Untuk mengotomatiskan tugas rutin, susun perintah CLI ke dalam skrip shell menggunakan sintaks skrip dari shell yang Anda pilih, lalu jalankan skrip.

Anda dapat menginstal Azure CLI secara lokal di Linux, Mac, atau komputer Windows. Ini juga dapat digunakan dari browser melalui Azure Cloud Shell atau dijalankan dari dalam kontainer Docker.

## <a name="current-version"></a>Versi Saat Ini

[!INCLUDE [current-version](includes/current-version.md)]

## <a name="data-collection"></a>Kumpulan data

Azure CLI mengumpulkan data telemetri secara default. Microsoft menggabungkan data yang dikumpulkan untuk mengidentifikasi pola penggunaan untuk mengidentifikasi masalah umum dan untuk meningkatkan pengalaman Azure CLI. Microsoft Azure CLI tidak mengumpulkan data pribadi atau pribadi apa pun. Misalnya, data penggunaan membantu mengidentifikasi masalah seperti perintah dengan keberhasilan rendah dan membantu memprioritaskan pekerjaan kami.

Meskipun kami menghargai wawasan yang diberikan data ini, kami juga memahami bahwa tidak semua orang ingin mengirim data penggunaan. Anda dapat menonaktifkan pengumpulan `az config set core.collect_telemetry=false` data dengan perintah . Anda juga dapat membaca [pernyataan privasi](https://privacy.microsoft.com/privacystatement) kami untuk mempelajari lebih lanjut.

## <a name="prepare-your-environment"></a>Menyiapkan lingkungan Anda

Sebelum menjalankan perintah Azure CLI, siapkan lingkungan Anda.

[!INCLUDE [prerequisites](includes/azure-cli-prepare-your-environment-no-header.md)]

## <a name="azure-cli-examples"></a>Contoh Azure CLI
Artikel ini berisi contoh Azure CLI yang berbeda untuk hal berikut:
- Sintaks langganan
- Sintaks penetapan peran
- Sintaks PowerShell


## <a name="subscription-syntax-example"></a>Contoh sintaks langganan

Sintaks Azure CLI mengikuti pola `reference name` - `command` - `parameter` - `parameter value` sederhana.  Misalnya, beralih antar langganan sering kali menjadi tugas umum.  Berikut sintaksnya.

```azurecli
az account set --subscription "my subscription name"
```

Sekarang, betapa mudahnya itu?!  Lihat [Mengelola langganan dengan Azure CLI](manage-azure-subscriptions-azure-cli.md) untuk mempelajari selengkapnya cara menggunakan Azure CLI untuk bekerja dengan langganan dan membuat grup pengelolaan.

## <a name="role-assignment-syntax-example"></a>Contoh sintaks penetapan peran

Penggunaan umum Azure CLI lainnya adalah mengelola penetapan peran.

```azurecli
az role assignment create --assignee servicePrincipalName --role Reader --scope /subscriptions/mySubscriptionID/resourceGroups/myResourceGroupName
az role assignment delete --assignee userSign-inName --role Contributor
```

Lihat [Membuat perwakilan layanan Azure dengan Azure CLI](create-an-azure-service-principal-azure-cli.md) untuk mengetahui turorial mendetail dalam mengelola perwakilan layanan dan penetapan peran.

## <a name="powershell-syntax-comparison"></a>Perbandingan sintaks PowerShell

[Memilih alat baris perintah yang tepat](choose-the-right-azure-command-line-tool.md) menjelaskan perbedaan antara `tools` dan `environments` dengan penekanan pada Azure CLI dan Azure PowerShell.  Ini juga memberikan banyak [perbandingan perintah berdampingan](choose-the-right-azure-command-line-tool.md#azure-cli-vs-azure-powershell-side-by-side-command-comparison).  Berikut dua contohnya:

|Perintah|Azure CLI|Azure PowerShell|
| --- | --- | --- |
| Membuat Grup Sumber Daya | az group create --name \<ResourceGroupName> --location eastus |New-AzResourceGroup -Name \<ResourceGroupName> -Location eastus
| Membuat Akun Azure Storage | az storage account create --name \<StorageAccountName> --resource-group \<ResourceGroupName> --location eastus --sku Standard_LRS --kind StorageV2 | New-AzStorageAccount -Name \<StorageAccountName> -ResourceGroupName \<ResourceGroupName> -Location eastus -SkuName Standard_LRS -Kind StorageV2

## <a name="see-also"></a>Lihat juga

* [Mulai menggunakan Azure CLI](./get-started-with-azure-cli.md)
* [Mengontrol layanan Azure dengan Azure CLI](/learn/modules/control-azure-services-with-cli/)
* [Sumber daya Azure yang dapat dikelola oleh Azure CLI](./azure-services-the-azure-cli-can-manage.md)
* [Daftar referensi perintah lengkap untuk Azure CLI](../latest/docs-ref-autogen/reference-index.yml)

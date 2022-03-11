---
title: Mulai menggunakan Azure Command-Line Interface (CLI) | Microsoft Docs
description: Pelajari cara mulai menggunakan Azure CLI dengan menyelesaikan perintah umum. Anda dapat mulai menggunakan Azure CLI dengan menjalankannya di lingkungan Azure Cloud Shell.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli, cara menggunakan azure cli, antarmuka baris perintah azure, cara membuka azure cli, perintah azure cli
ms.openlocfilehash: a98d282beebeafd3262fe5d662a083019956721f
ms.sourcegitcommit: ad79327952adf0f8be8f1b9678e72434d9f03f0c
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 02/12/2022
ms.locfileid: "138526549"
---
# <a name="get-started-with-azure-cli"></a>Memulai dengan Azure CLI

Selamat datang di Azure Command-Line Interface (CLI)!  Artikel ini memperkenalkan CLI dan membantu Anda menyelesaikan tugas-tugas umum.

> [!NOTE]
>
> Dalam skrip dan di situs dokumentasi Microsoft, contoh Azure CLI ditulis untuk shell `bash`. Contoh satu baris akan berjalan di platform apa pun. Contoh yang lebih panjang yang mencakup kelanjutan baris (`\`) atau penetapan variabel harus diubah agar berfungsi di shell lain, termasuk PowerShell.

## <a name="install-or-run-in-azure-cloud-shell"></a>Menginstal atau menjalankan di Azure Cloud Shell

Cara termudah untuk mempelajari cara menggunakan Azure CLI adalah menjalankannya di lingkungan Azure Cloud Shell melalui browser. Untuk mempelajari Cloud Shell, lihat [Panduan mulai cepat untuk Bash di Azure Cloud Shell](/azure/cloud-shell/quickstart).

Jika Anda sudah siap menginstal CLI, lihat [petunjuk penginstalan](install-azure-cli.md).

Setelah menginstal CLI untuk pertama kalinya, periksa apakah ini diinstal dan Anda memiliki versi yang benar dengan menjalankan `az --version`.

> [!NOTE]
> Jika Anda menggunakan model penyebaran klasik Azure, [instal Azure classic CLI](install-classic-cli.md).

## <a name="how-to-sign-into-the-azure-cli"></a>Cara masuk ke Azure CLI

Sebelum menggunakan perintah Azure CLI dengan penginstalan lokal, Anda harus masuk menggunakan [az login](/cli/azure/reference-index#az-login).

[!INCLUDE [interactive-login](includes/interactive-login.md)]

Setelah masuk, Anda melihat daftar langganan yang terkait dengan akun Azure Anda. Informasi langganan dengan `isDefault: true` adalah langganan yang saat ini diaktifkan setelah masuk. Untuk memilih langganan lain, gunakan perintah [az account set](/cli/azure/account#az-account-set) dengan ID langganan untuk beralih. Untuk informasi selengkapnya tentang pemilihan langganan, lihat [Menggunakan beberapa langganan Azure](manage-azure-subscriptions-azure-cli.md).

Ada beberapa cara untuk masuk secara non-interaktif, yang dibahas secara mendetail di [Masuk dengan Azure CLI](authenticate-azure-cli.md).

## <a name="common-azure-cli-commands"></a>Perintah Azure CLI umum

Tabel ini mencantumkan beberapa perintah umum yang digunakan dalam CLI dan tautan ke dokumentasi referensinya.

| Jenis Sumber Daya | Grup perintah Azure CLI |
|---------------|-------------------------|
| [Grup sumber daya](/azure/azure-resource-manager/resource-group-overview) | [az group](/cli/azure/group) |
| [Komputer virtual](/azure/virtual-machines) | [az vm](/cli/azure/vm) |
| [Akun penyimpanan](/azure/storage/common/storage-introduction) | [az storage account](/cli/azure/storage/account) |
| [Key Vault](/azure/key-vault/key-vault-whatis) | [az keyvault](/cli/azure/keyvault) |
| [Aplikasi web](/azure/app-service) | [az webapp](/cli/azure/webapp) |
| [Database SQL](/azure/sql-database) | [az sql server](/cli/azure/sql/server) |
| [CosmosDB](/azure/cosmos-db) | [az cosmosdb](/cli/azure/cosmosdb) |

## <a name="finding-commands"></a>Menemukan perintah

Perintah Azure CLI diatur sebagai _perintah_ _grup_. Setiap grup mewakili layanan Azure, dan perintah beroperasi di layanan tersebut.

Untuk mencari perintah, gunakan [az find](/cli/azure/reference-index#az-find). Misalnya, untuk mencari nama perintah yang berisi `secret`, gunakan perintah berikut:

```azurecli-interactive
az find secret
```

Gunakan argumen `--help` untuk mendapatkan daftar lengkap perintah dan sub-kelompok dari grup. Misalnya, untuk menemukan perintah CLI untuk bekerja dengan Kelompok Keamanan Jaringan (NSG):

```azurecli-interactive
az network nsg --help
```

CLI memiliki penyelesaian tab penuh untuk perintah di bawah shell bash.

## <a name="globally-available-arguments"></a>Argumen yang tersedia secara global

Ada beberapa argumen yang tersedia untuk setiap perintah.

* `--help` mencetak informasi referensi CLI tentang perintah beserta argumennya dan mencantumkan sub-grup dan perintah yang tersedia.
* `--output` mengubah format output. Format output yang tersedia meliputi `json`, `jsonc` (JSON berwarna), `tsv` (Nilai yang Dipisahkan Tab), `table` (tabel ASCII yang dapat dibaca manusia), dan `yaml`. Secara default, CLI menghasilkan `json`. Untuk mempelajari lebih lanjut format output yang tersedia, lihat [Format output untuk Azure CLI](format-output-azure-cli.md).
* `--query` menggunakan [bahasa kueri JMESPath](http://jmespath.org/) untuk memfilter output yang ditampilkan dari layanan Azure. Untuk mempelajari kueri lebih lanjut, lihat [Mengkueri hasil perintah dengan Azure CLI](query-azure-cli.md) dan [tutorial JMESPath](http://jmespath.org/tutorial.html).
* `--verbose` mencetak informasi tentang sumber daya yang dibuat di Azure selama operasi, serta informasi yang berguna lainnya.
* `--debug` mencetak lebih banyak informasi tentang operasi CLI, yang digunakan untuk tujuan penelusuran kesalahan. Jika Anda menemukan bug, masukkan output yang dihasilkan dengan bendera `--debug` saat menyerahkan laporan bug.

## <a name="interactive-mode"></a>Mode interaktif

CLI menawarkan mode interaktif yang secara otomatis menampilkan informasi bantuan dan memudahkan pemilihan sub-perintah. Masuk ke mode interaktif dengan perintah [az interactive](/cli/azure/reference-index#az-interactive).

```azurecli-interactive
az interactive
```

Untuk informasi selengkapnya tentang mode interaktif, lihat [Mode Interaktif Azure CLI](interactive-azure-cli.md).

Ada juga [plugin Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.azurecli) yang menawarkan pengalaman interaktif, termasuk dokumentasi pengisian otomatis dan mouse-over.

## <a name="learn-cli-basics-with-quickstarts-and-tutorials"></a>Pelajari dasar-dasar CLI dengan mulai cepat dan tutorial

Untuk mempelajari cara menggunakan Azure CLI, coba tutorial mendalam untuk menyiapkan mesin virtual dan menggunakan kelebihan CLI untuk mengkueri sumber daya Azure.

> [!div class="nextstepaction"]
> [Tutorial membuat mesin virtual dengan Azure CLI](azure-cli-vm-tutorial.yml)

Ada juga panduan mulai cepat untuk layanan populer lainnya.

* [Membuat akun penyimpanan menggunakan Azure CLI](/azure/storage/common/storage-quickstart-create-storage-account-cli)
* [Mentransfer objek ke/dari penyimpanan Azure Blob menggunakan CLI](/azure/storage/blobs/storage-quickstart-blobs-cli)
* [Membuat database Azure SQL tunggal menggunakan Azure CLI](/azure/sql-database/sql-database-get-started-cli)
* [Membuat server Azure Database for MySQL menggunakan Azure CLI](/azure/mysql/quickstart-create-mysql-server-database-using-azure-cli)
* [Membuat server Azure Database for PostgreSQL menggunakan Azure CLI](/azure/postgresql/quickstart-create-server-database-azure-cli)
* [Membuat aplikasi web Python di Azure](/azure/app-service/app-service-web-get-started-python)
* [Menjalankan citra Docker Hub kustom di Azure Web Apps untuk Kontainer](/azure/app-service/containers/quickstart-custom-docker-image)

## <a name="give-feedback"></a>Berikan umpan balik

Kami menyambut tanggapan Anda untuk CLI untuk membantu kami melakukan perbaikan dan menangani bug. Anda dapat [mengajukan masalah di GitHub](https://github.com/azure/azure-cli/issues) atau menggunakan fitur bawaan CLI untuk memberikan tanggapan umum terkait perintah [az feedback](/cli/azure/reference-index#az-feedback).

```azurecli-interactive
az feedback
```

## <a name="see-also"></a>Lihat juga

* [Layanan yang dapat dikelola Azure CLI](azure-services-the-azure-cli-can-manage.md)
* [Daftar referensi perintah lengkap untuk Azure CLI](/cli/azure/reference-index)
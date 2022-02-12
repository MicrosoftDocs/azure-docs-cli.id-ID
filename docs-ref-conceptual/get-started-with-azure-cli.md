---
title: Mulai menggunakan | Azure Command-Line Interface (CLI) Microsoft Dokumen
description: Pelajari cara mulai menggunakan Azure CLI dengan menyelesaikan perintah umum. Anda dapat mulai menggunakan Azure CLI dengan menjalankannya di lingkungan shell Azure Cloud.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli, cara menggunakan azure cli, azure command line interface, cara membuka azure cli, azure cli commands
ms.openlocfilehash: a98d282beebeafd3262fe5d662a083019956721f
ms.sourcegitcommit: ad79327952adf0f8be8f1b9678e72434d9f03f0c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/12/2022
ms.locfileid: "138526549"
---
# <a name="get-started-with-azure-cli"></a>Memulai dengan Azure CLI

Selamat datang di Azure Command-Line Interface (CLI)!  Artikel ini memperkenalkan CLI dan membantu Anda menyelesaikan tugas-tugas umum.

> [!NOTE]
>
> Dalam skrip dan di situs dokumentasi Microsoft, contoh Azure CLI ditulis untuk `bash` shell. Contoh satu baris akan berjalan di platform apa pun. Contoh yang lebih panjang yang mencakup kelanjutan baris (`\`) atau penetapan variabel perlu dimodifikasi untuk bekerja pada shell lain, termasuk PowerShell.

## <a name="install-or-run-in-azure-cloud-shell"></a>Menginstal atau menjalankan di Azure Cloud Shell

Cara termudah untuk mempelajari cara menggunakan Azure CLI adalah dengan menjalankannya di lingkungan Azure Cloud Shell melalui browser Anda. Untuk mempelajari tentang Cloud Shell, lihat  [Mulai Cepat untuk Bash di Azure Cloud Shell](/azure/cloud-shell/quickstart).

Saat Anda siap menginstal CLI, lihat [instruksi instalasi](install-azure-cli.md).

Setelah menginstal CLI untuk pertama kalinya, periksa apakah itu diinstal dan Anda memiliki versi yang benar dengan menjalankan `az --version`.

> [!NOTE]
> Jika Anda menggunakan model penyebaran klasik Azure, [instal CLI klasik Azure](install-classic-cli.md).

## <a name="how-to-sign-into-the-azure-cli"></a>Cara masuk ke Azure CLI

Sebelum menggunakan perintah Azure CLI dengan instalasi lokal, Anda harus masuk dengan [az login](/cli/azure/reference-index#az-login).

[!INCLUDE [interactive-login](includes/interactive-login.md)]

Setelah masuk, Anda melihat daftar langganan yang terkait dengan akun Azure Anda. Informasi langganan dengan `isDefault: true` adalah langganan yang saat ini diaktifkan setelah masuk. Untuk memilih langganan lain, gunakan perintah [az account set](/cli/azure/account#az-account-set) dengan ID langganan untuk beralih. Untuk informasi selengkapnya tentang pemilihan langganan, lihat [Menggunakan beberapa langganan Azure](manage-azure-subscriptions-azure-cli.md).

Ada beberapa cara untuk masuk secara non-interaktif, yang dibahas secara mendetail di [Masuk dengan Azure CLI](authenticate-azure-cli.md).

## <a name="common-azure-cli-commands"></a>Perintah Azure CLI umum

Tabel ini mencantumkan beberapa perintah umum yang digunakan dalam CLI dan tautan ke dokumentasi referensi mereka.

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

Perintah Azure CLI diatur sebagai _perintah_ _grup_. Setiap grup mewakili layanan Azure, dan perintah beroperasi pada layanan tersebut.

Untuk mencari perintah, gunakan [az find](/cli/azure/reference-index#az-find). Misalnya, untuk mencari nama perintah yang berisi `secret`, gunakan perintah berikut:

```azurecli-interactive
az find secret
```

`--help` Gunakan argumen untuk mendapatkan daftar lengkap perintah dan subkelompok grup. Misalnya, untuk menemukan perintah CLI untuk bekerja dengan Grup Keamanan Jaringan (NSGs):

```azurecli-interactive
az network nsg --help
```

CLI memiliki penyelesaian tab penuh untuk perintah di bawah shell bash.

## <a name="globally-available-arguments"></a>Argumen yang tersedia secara global

Ada beberapa argumen yang tersedia untuk setiap perintah.

* `--help` mencetak informasi referensi CLI tentang perintah dan argumen dan daftar subkelompok dan perintah yang tersedia.
* `--output` mengubah format output. Format output yang tersedia adalah `json`, `jsonc` (JSON berwarna), `tsv` (Tab-Separated Values), `table` (tabel ASCII yang dapat dibaca manusia), dan `yaml`. Secara default output `json`CLI . Untuk mempelajari selengkapnya tentang format output yang tersedia, lihat [Format output untuk Azure CLI](format-output-azure-cli.md).
* `--query` menggunakan [bahasa kueri JMESPath](http://jmespath.org/) untuk memfilter output yang dikembalikan dari layanan Azure. Untuk mempelajari kueri selengkapnya, lihat [Hasil perintah Kueri dengan Azure CLI](query-azure-cli.md) dan [tutorial JMESPath](http://jmespath.org/tutorial.html).
* `--verbose` mencetak informasi tentang sumber daya yang dibuat di Azure selama operasi, dan informasi berguna lainnya.
* `--debug` mencetak lebih banyak informasi tentang operasi CLI, yang digunakan untuk tujuan debugging. Jika Anda menemukan bug, berikan output yang dihasilkan dengan `--debug` bendera saat mengirimkan laporan bug.

## <a name="interactive-mode"></a>Mode interaktif

CLI menawarkan mode interaktif yang secara otomatis menampilkan informasi bantuan dan membuatnya lebih mudah untuk memilih subkomand. Anda memasukkan mode interaktif dengan perintah [interaktif az](/cli/azure/reference-index#az-interactive) .

```azurecli-interactive
az interactive
```

Untuk informasi selengkapnya tentang mode interaktif, lihat [Azure CLI Interactive Mode](interactive-azure-cli.md).

Ada juga [plugin Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.azurecli) yang menawarkan pengalaman interaktif, termasuk pelengkapan otomatis dan dokumentasi mouse-over.

## <a name="learn-cli-basics-with-quickstarts-and-tutorials"></a>Pelajari dasar-dasar CLI dengan mulai cepat dan tutorial

Untuk mempelajari cara menggunakan Azure CLI, coba tutorial mendalam untuk menyiapkan mesin virtual dan menggunakan kekuatan CLI untuk mengkueri sumber daya Azure.

> [!div class="nextstepaction"]
> [Membuat mesin virtual dengan tutorial Azure CLI](azure-cli-vm-tutorial.yml)

Ada juga quickstarts untuk layanan populer lainnya.

* [Membuat akun penyimpanan menggunakan Azure CLI](/azure/storage/common/storage-quickstart-create-storage-account-cli)
* [Mentransfer objek ke/dari penyimpanan Azure Blob menggunakan CLI](/azure/storage/blobs/storage-quickstart-blobs-cli)
* [Membuat database Azure SQL tunggal menggunakan Azure CLI](/azure/sql-database/sql-database-get-started-cli)
* [Membuat server Azure Database for MySQL menggunakan Azure CLI](/azure/mysql/quickstart-create-mysql-server-database-using-azure-cli)
* [Membuat Azure Database for PostgreSQL menggunakan Azure CLI](/azure/postgresql/quickstart-create-server-database-azure-cli)
* [Membuat aplikasi web Python di Azure](/azure/app-service/app-service-web-get-started-python)
* [Menjalankan gambar Docker Hub kustom di Azure Web Apps for Containers](/azure/app-service/containers/quickstart-custom-docker-image)

## <a name="give-feedback"></a>Berikan umpan balik

Kami menyambut umpan balik Anda untuk CLI untuk membantu kami melakukan perbaikan dan menyelesaikan bug. Anda dapat [mengajukan masalah pada GitHub](https://github.com/azure/azure-cli/issues) atau menggunakan fitur bawaan CLI untuk meninggalkan umpan balik umum dengan perintah [umpan balik az](/cli/azure/reference-index#az-feedback).

```azurecli-interactive
az feedback
```

## <a name="see-also"></a>Lihat juga

* [Layanan yang dapat dikelola Azure CLI](azure-services-the-azure-cli-can-manage.md)
* [Daftar referensi perintah lengkap untuk Azure CLI](/cli/azure/reference-index)
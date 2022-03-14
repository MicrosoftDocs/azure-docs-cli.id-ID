---
title: Jenis referensi, status dan tingkat dukungan – Azure CLI | Microsoft Docs
description: Pelajari jenis referensi, status, dan tingkat dukungan Azure CLI
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 02/10/2022
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure cli, jenis referensi, status referensi
ms.openlocfilehash: ac6ab55c3db777b83877de34f2570b9d8d70b040
ms.sourcegitcommit: ad79327952adf0f8be8f1b9678e72434d9f03f0c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/12/2022
ms.locfileid: "138554942"
---
# <a name="overview-azure-cli-reference-types-and-status"></a>Ringkasan: Jenis dan status referensi Azure CLI

Azure CLI memiliki berbagai jenis referensi, yang terkadang dijelaskan secara bergantian dengan status referensi. Artikel ini menjelaskan perbedaan antara jenis Azure CLI dan status, dan memberikan informasi untuk bekerja dengan keduanya.

## <a name="azure-cli-syntax-components"></a>Komponen sintaks Azure CLI

Sintaks Azure CLI adalah kombinasi referensi, perintah, dan parameter. **Perintah referensi lengkap** sering kali disebut sebagai **perintah**.

| Layanan Azure | Referensi | Sub-layanan referensi | Perintah | Perintah referensi lengkap | Contoh Parameter
|-|-|-|-|-|-|
| Azure CLI | [az config](/cli/azure/config) | | | az config | --local, --output -o
| Azure Network | [az network](/cli/azure/network) | application-gateway | buat | [az network application-gateway create](/cli/azure/network/application-gateway#az-network-application-gateway-create) | --name, --resource-group, --capacity
| Azure DevOps Server | [az pipelines](/cli/azure/pipelines) | agen | list | [az pipelines agent list](/cli/azure/pipelines/agent) | --pool-id, --agent-name, --demands

## <a name="what-are-reference-types"></a>Apa itu jenis referensi?

Jenis referensi memberi tahu Anda apakah perintah referensi adalah bagian dari layanan utama Azure CLI, atau berupa add-on opsional. Ada dua jenis perintah referensi Azure CLI: **inti** dan **ekstensi**.

|                |                           Core                           |                       Extensi                        |
| -------------- | -------------------------------------------------------- | ------------------------------------------------------ |
| **Referensi** | Merupakan bagian dari layanan utama Azure CLI                | Berupa perintah referensi opsional yang harus diinstal |
| **Instal**    | Bersama dengan [alat penginstal MSI]()                       | Secara individual dengan [az extension add]()                 |
| **Dirilis**   | Sesuai jadwal                                            | Saat fitur atau pembaruan baru tersedia            |
| **Status**     | Bisa berupa GA (Tersedia Umum), pratinjau atau percobaan | Juga bisa berupa GA, pratinjau atau percobaan                |

Semua referensi Azure CLI dapat dijalankan di Windows, macOS, Linux, Docker, dan Azure Cloud Shell.

### <a name="core"></a>Core

Referensi Azure CLI yang telah diterbitkan sebagai bagian permanen dari CLI disebut **referensi inti**. Semua referensi inti diinstal dengan Azure CLI dan Anda tidak dapat memilih subset referensi. Jika Anda menjalankan CLI melalui Azure Cloud Shell, referensi inti selalu diperbarui. Lihat [Daftar referensi inti untuk Azure CLI](/cli/azure/reference-index) untuk mengetahui daftar lengkap perintah referensi inti.

### <a name="extension"></a>Extensi

Ekstensi tidak dikirim sebagai bagian dari CLI, tetapi dijalankan sebagai perintah CLI. Beberapa ekstensi adalah bagian permanen dari Azure CLI, tetapi ekstensi sering kali akan memberi Anda akses ke pratinjau pribadi dan perintah percobaan. Referensi tunggal, seperti **az iot hub**, bisa memiliki perintah inti dan ekstensi.  Berikut adalah empat contoh:

|      Perintah referensi lengkap       | Berupa Inti | Berupa ekstensi |
| --------------------------------- | ------- | ------------ |
| az iot hub list                   | ya     |              |
| az iot hub query                  |         | ya          |
| az iot hub certificate create     | ya     |              |
| az iot hub device identify create |         | ya          |

> [!IMPORTANT]
> Anda harus menginstal ekstensi sebelum digunakan dengan menjalankan perintah [az extension add](/cli/azure/extension#az-extension-add).

Anda dapat mempelajari referensi ekstensi lebih lanjut termasuk penginstalan dan pembaruan di [Menggunakan ekstensi dengan Azure CLI](azure-cli-extensions-overview.md).  Lihat [Ekstensi yang tersedia untuk Azure CLI](azure-cli-extensions-list.md) untuk mengetahui daftar lengkap perintah referensi ekstensi.

## <a name="what-is-reference-status"></a>Apa itu status referensi?

Terlepas dari jenisnya, referensi Azure CLI memiliki tiga kategori status: **GA** (Tersedia Umum), **pratinjau publik**, atau **percobaan**. Ini adalah status perintah referensi, bukan jenis, yang menentukan stabilitas dan tingkat dukungan.

| | GA  | Pratinjau umum | Eksperimental
|-|-|-|-|
| **Stabilitas** | Permanen | Dapat berubah sebagai respons terhadap tanggapan pelanggan. Tunduk pada ketentuan [Pratinjau Microsoft Azure](https://azure.microsoft.com/support/legal/preview-supplemental-terms/). | Dapat berubah sebagai respons terhadap tanggapan pelanggan. Akan sering dimigrasikan ke pratinjau publik.  Dapat dihapus.
| **Tingkat dukungan** | Data | Sebagian | Tidak ada

Meskipun sebagian besar perintah dan parameter untuk satu referensi memiliki status tunggal, hal ini tidak selalu terjadi. Referensi GA yang dibangun untuk menawarkan lebih banyak perintah bisa memiliki perintah referensi GA, pratinjau, dan percobaan. Karena parameter baru ditambahkan untuk meningkatkan fungsionalitas, satu perintah juga bisa memiliki beberapa parameter yang termasuk dalam kategori status lainnya. Berikut beberapa contoh referensi dengan status yang berbeda:

|   Perintah referensi lengkap   |                              Parameter                              |   Jenis    | GA  | Pratinjau umum | Eksperimental |
| -------------------------- | -------------------------------------------------------------------- | --------- | --- | -------------- | ------------ |
| az network dns zone list   | Semua                                                                  | Core      | ya |                |              |
| buat zona dns jaringan az | --name, --resource-group, --if-none-match, --parent-name             | Core      | ya |                |              |
|                            | --newFutureParameter1                                                | Core      |     | ya            |              |
|                            | --newFutureParameter2                                                | Core      |     |                | ya          |
| az network vhub list       | Semua                                                                  | Extensi | ya |                |              |
| az network vhub create     | --address-prefix, --name, --resource-group, -vwan, --location, --sku | Extensi | ya |                |              |
|                            | --newFutureParameter1                                                | Extensi |     | ya            |              |
|                            | --newFutureParameter2                                                | Extensi |     |                | ya          |
| az network firewall create | Semua                                                                  | Extensi |     |                | ya          |

> [!NOTE]
> Tabel di atas hanya sebagai contoh dan **tidak** mewakili status referensi saat ini, misalnya perintah.

> [!NOTE]
> Peringatan yang menunjukkan **pratinjau umum** atau **percobaan** adalah bagian dari output perintah Azure CLI dan harus dipertimbangkan.

## <a name="see-also"></a>Lihat juga

- [Daftar referensi inti untuk Azure CLI](/cli/azure/reference-index)
- [Ekstensi yang tersedia untuk Azure CLI](azure-cli-extensions-list.md)

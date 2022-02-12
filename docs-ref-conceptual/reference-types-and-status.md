---
title: Jenis referensi, status, dan level dukungan – Azure CLI | Microsoft Dokumen
description: Pelajari tentang jenis referensi, status, dan tingkat dukungan Azure CLI
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
# <a name="overview-azure-cli-reference-types-and-status"></a>Ringkasan: Tipe dan status referensi Azure CLI

Azure CLI memiliki jenis referensi yang berbeda, yang terkadang dijelaskan secara bergantian dengan status referensi. Artikel ini menjelaskan perbedaan antara tipe Azure CLI dan status, dan memberikan informasi untuk bekerja dengan keduanya.

## <a name="azure-cli-syntax-components"></a>Komponen sintaks Azure CLI

Sintaks Azure CLI adalah kombinasi referensi, perintah, dan parameter. Seringkali **perintah referensi penuh** disebut sebagai **perintah**.

| Layanan Azure | Referensi | Subservice referensi | Perintah | Perintah referensi lengkap | Contoh Parameter
|-|-|-|-|-|-|
| Azure CLI | [az config](/cli/azure/config) | | | az config | --lokal, --output -o
| Azure Network | [az network](/cli/azure/network) | application-gateway | buat | [az network application-gateway create](/cli/azure/network/application-gateway#az-network-application-gateway-create) | --name, --resource-group, --capacity
| Azure DevOps Server | [az pipelines](/cli/azure/pipelines) | agen | list | [az pipelines agent list](/cli/azure/pipelines/agent) | --pool-id, --agent-name, --demands

## <a name="what-are-reference-types"></a>Apa itu jenis referensi?

Jenis referensi memberi tahu Anda jika perintah referensi adalah bagian dari layanan Azure CLI utama, atau jika itu adalah add-on opsional. Ada dua jenis perintah referensi Azure CLI: **inti** dan **ekstensi**.

|                |                           Core                           |                       Ekstensi                        |
| -------------- | -------------------------------------------------------- | ------------------------------------------------------ |
| **Referensi** | Apakah bagian dari layanan Azure CLI utama                | Apakah perintah referensi opsional yang harus diinstal |
| **Instal**    | Bersama dengan [penginstal MSI]()                       | Secara individual dengan [az extension add]()                 |
| **Dirilis**   | Sesuai jadwal                                            | Saat fitur atau pembaruan baru tersedia            |
| **Status**     | Dapat ga (Tersedia Secara Umum), pratinjau atau eksperimental | Juga bisa GA, preview atau eksperimental                |

Semua referensi Azure CLI dapat dijalankan di Windows, macOS, Linux, Docker, dan Azure Cloud Shell.

### <a name="core"></a>Core

Referensi Azure CLI yang telah diterbitkan sebagai bagian permanen dari CLI disebut **referensi inti**. Semua referensi inti diinstal dengan Azure CLI dan Anda tidak dapat memilih subset referensi. Jika Anda menjalankan CLI melalui Azure Cloud Shell, referensi inti selalu diperbarui. Lihat [Daftar referensi inti untuk Azure CLI](/cli/azure/reference-index) untuk daftar lengkap perintah referensi inti.

### <a name="extension"></a>Ekstensi

Ekstensi tidak dikirim sebagai bagian dari CLI tetapi dijalankan sebagai perintah CLI. Beberapa ekstensi adalah bagian permanen dari Azure CLI, tetapi seringkali, ekstensi akan memberi Anda akses ke pratinjau pribadi dan perintah eksperimental. Referensi tunggal, seperti **hub az iot**, dapat memiliki perintah inti dan ekstensi.  Berikut adalah empat contoh:

|      Perintah referensi lengkap       | Apakah Inti | Apakah Ekstensi |
| --------------------------------- | ------- | ------------ |
| az iot hub list                   | ya     |              |
| az iot hub query                  |         | ya          |
| az iot hub certificate create     | ya     |              |
| az iot hub device identify create |         | ya          |

> [!IMPORTANT]
> Anda harus menginstal ekstensi sebelum digunakan dengan menjalankan perintah [tambahkan ekstensi az](/cli/azure/extension#az-extension-add) .

Anda dapat mempelajari lebih lanjut tentang referensi ekstensi termasuk instalasi dan pembaruan di [Gunakan ekstensi dengan Azure CLI](azure-cli-extensions-overview.md).  Lihat [Ekstensi yang tersedia untuk Azure CLI](azure-cli-extensions-list.md) untuk daftar lengkap perintah referensi ekstensi.

## <a name="what-is-reference-status"></a>Apa itu status referensi?

Terlepas dari jenisnya, referensi Azure CLI termasuk dalam tiga kategori status: **GA** (Tersedia Secara Umum), **pratinjau publik** , atau **eksperimental**. Ini adalah status perintah referensi, bukan tipe, yang menentukan stabilitas dan tingkat dukungan.

| | GA  | Pratinjau umum | Eksperimental
|-|-|-|-|
| **Stabilitas** | Permanen | Dapat berubah sebagai respons terhadap umpan balik pelanggan. Tunduk pada ketentuan [Microsoft Azure Pratinjau](https://azure.microsoft.com/support/legal/preview-supplemental-terms/). | Dapat berubah sebagai respons terhadap umpan balik pelanggan. Akan sering bermigrasi ke pratinjau publik.  Bisa dihapus.
| **Tingkat dukungan** | Data | Sebagian | Tidak ada

Meskipun sebagian besar perintah dan parameter untuk satu referensi memiliki status tunggal, ini tidak selalu terjadi. Referensi GA yang sedang dibangun untuk menawarkan lebih banyak perintah dapat memiliki perintah referensi GA, pratinjau, dan eksperimental. Karena parameter baru ditambahkan untuk meningkatkan fungsionalitas, satu perintah juga dapat memiliki parameter yang termasuk dalam kategori status yang berbeda. Berikut adalah contoh referensi yang memiliki status berbeda:

|   Perintah referensi lengkap   |                              Parameter                              |   Jenis    | GA  | Pratinjau publik | Eksperimental |
| -------------------------- | -------------------------------------------------------------------- | --------- | --- | -------------- | ------------ |
| az network dns zone list   | Semua                                                                  | Core      | ya |                |              |
| buat zona dns jaringan az | --name, --resource-group, --if-none-match, --parent-name             | Core      | ya |                |              |
|                            | --newFutureParameter1                                                | Core      |     | ya            |              |
|                            | --newFutureParameter2                                                | Core      |     |                | ya          |
| az network vhub list       | Semua                                                                  | Ekstensi | ya |                |              |
| az network vhub create     | --address-prefix, --name, --resource-group, -vwan, --location, --sku | Ekstensi | ya |                |              |
|                            | --newFutureParameter1                                                | Ekstensi |     | ya            |              |
|                            | --newFutureParameter2                                                | Ekstensi |     |                | ya          |
| az network firewall create | Semua                                                                  | Ekstensi |     |                | ya          |

> [!NOTE]
> Tabel di atas hanyalah contoh dan **tidak** mewakili status referensi saat ini misalnya perintah.

> [!NOTE]
> Peringatan yang menunjukkan **pratinjau publik** atau **eksperimental** adalah bagian dari output perintah Azure CLI dan harus diharapkan.

## <a name="see-also"></a>Lihat juga

- [Daftar referensi inti untuk Azure CLI](/cli/azure/reference-index)
- [Ekstensi yang tersedia untuk Azure CLI](azure-cli-extensions-list.md)

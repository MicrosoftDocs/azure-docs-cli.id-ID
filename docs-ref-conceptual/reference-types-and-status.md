---
title: Jenis referensi, status dan tingkat dukungan - Azure CLI | Microsoft Docs
description: Pelajari tentang tipe referensi, status, dan tingkat dukungan Azure CLI
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli references, reference types, reference status
ms.openlocfilehash: 1edae6590fa9c66c6385732153fdb3292f98655e
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439051"
---
# <a name="overview-azure-cli-reference-types-and-status"></a>Gambaran Umum: Tipe dan status referensi Azure CLI

Azure CLI memiliki jenis referensi yang berbeda, yang kadang-kadang dijelaskan secara bergantian dengan status referensi.  Artikel ini menjelaskan perbedaan antara tipe Azure CLI dan status, dan memberikan informasi untuk bekerja dengan keduanya.

## <a name="azure-cli-syntax-components"></a>Azure CLI syntax components

Sintaks Azure CLI adalah kombinasi dari referensi, perintah, dan parameter.  Seringkali **perintah referensi penuh** disebut sebagai **perintah.**

| Layanan Azure | Referensi | Subservice referensi | Perintah | Perintah referensi lengkap | Contoh Parameter
|-|-|-|-|-|-|
| Azure CLI | [az config](/cli/azure/config) | | | az config | --local, --output -o
| Azure Network | [az network](/cli/azure/network) | gateway aplikasi | buat | [az network application-gateway create](/cli/azure/network/application-gateway#az_network_application_gateway_create) | --nama, --sumber daya-kelompok, --kapasitas
| Azure DevOps Server | [az pipelines](/cli/azure/pipelines) | agen | list | [az pipelines agent list](/cli/azure/pipelines/agent) | --pool-id, --agent-name, --demands

## <a name="what-are-reference-types"></a>Apa saja jenis referensinya?

Tipe referensi memberi tahu Anda jika perintah referensi adalah bagian dari layanan Azure CLI utama, atau jika itu adalah add-on opsional.  Ada dua jenis perintah referensi Azure CLI: **inti** dan **ekstensi.**

|         | Core  | Ekstensi
|-|-|-|
| **Referensi** | Adalah bagian dari layanan Azure CLI utama | Apakah perintah referensi opsional yang harus diinstal
| **Instal** | Bersama dengan [installer MSI]() | Secara individual dengan [az extension add]()|
| **Dirilis** | Sesuai jadwal | Karena fitur atau pembaruan baru tersedia
| **Status** | Bisa GA (Umumnya Tersedia), preview atau eksperimental | Juga bisa GA, preview atau eksperimental

Semua referensi Azure CLI dapat dijalankan di Windows, macOS, Linux, Docker, dan Azure Cloud Shell.

### <a name="core"></a>Core

Referensi Azure CLI yang telah diterbitkan sebagai bagian permanen dari CLI disebut **referensi inti.**  Semua referensi inti diinstal dengan Azure CLI dan Anda tidak dapat memilih subset referensi.  Jika Anda menjalankan CLI melalui Azure Cloud Shell, referensi inti selalu up to date.  Lihat [Daftar referensi inti untuk Azure CLI](/cli/azure/reference-index) untuk daftar lengkap perintah referensi inti.

### <a name="extension"></a>Ekstensi

Ekstensi tidak dikirim sebagai bagian dari CLI tetapi dijalankan sebagai perintah CLI.  Beberapa ekstensi adalah bagian permanen dari Azure CLI, tetapi seringkali, ekstensi akan memberi Anda akses ke pratinjau pribadi dan perintah eksperimental.  Referensi tunggal, seperti **az iot hub,** dapat memiliki perintah inti dan ekstensi.  Berikut adalah empat contoh:

| Perintah referensi lengkap | Apakah Core | Apakah Ekstensi
|-|-|-|
| az iot hub list | ya |
| az iot hub query | | ya
| az iot hub certificate create | ya |
| az iot hub device identify create | | ya

> [!IMPORTANT]
> Anda harus menginstal ekstensi sebelum digunakan dengan menjalankan perintah [tambahkan ekstensi az.](/cli/azure/extension#az_extension_add)

Anda dapat mempelajari [selengkapnya](azure-cli-extensions-overview.md)tentang referensi ekstensi termasuk instalasi dan pembaruan di Gunakan ekstensi dengan Azure CLI .  Lihat [Ekstensi yang tersedia untuk Azure CLI](azure-cli-extensions-list.md) untuk daftar lengkap perintah referensi ekstensi.

## <a name="what-is-reference-status"></a>Apa itu status referensi?

Terlepas dari jenisnya, referensi Azure CLI termasuk dalam tiga kategori status: **GA** (Umumnya Tersedia), **pratinjau publik** atau **eksperimental.**  Ini adalah status perintah referensi, bukan tipe, yang menentukan stabilitas dan tingkat dukungan.

| | GA  | Pratinjau umum | Eksperimental
|-|-|-|-|
| **Stabilitas** | Permanen | Dapat berubah dalam menanggapi umpan balik pelanggan.  Tunduk pada ketentuan [Pratinjau Microsoft Azure.](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) | Dapat berubah dalam menanggapi umpan balik pelanggan.  Akan sering bermigrasi ke pratinjau publik.  Bisa dihapus.
| **Tingkat dukungan** | Data | Sebagian | Tidak ada

Meskipun sebagian besar perintah dan parameter untuk satu referensi memiliki status tunggal, ini tidak selalu terjadi.  Referensi GA yang sedang dibangun untuk menawarkan lebih banyak perintah dapat memiliki perintah referensi GA, pratinjau, dan eksperimental. Karena parameter baru ditambahkan untuk meningkatkan fungsionalitas, satu perintah juga dapat memiliki parameter yang termasuk dalam kategori status yang berbeda.  Berikut adalah contoh referensi yang memiliki status berbeda:

| Perintah referensi lengkap | Parameter | Jenis | GA | Pratinjau umum | Eksperimental
|-|-|-|-|-|-|
| az network dns zone list | Semua | Core | ya |
| buat zona dns jaringan az | --nama, --sumber daya-grup, --jika-tidak-cocok, --parent-name | Core | ya |
|  | --newFutureParameter1 | Core | | ya
|  | --newFutureParameter2 | Core | | | ya
| az network vhub list | Semua |Ekstensi | ya
| az network vhub create | --address-prefix, --name, --resource-group, -vwan, --location, --sku |Ekstensi | ya
|  | --newFutureParameter1 |Ekstensi | | ya
|  | --newFutureParameter2|Ekstensi | | | ya
| az network firewall create | Semua | Ekstensi | | | ya

> [!NOTE]
> Peringatan yang menunjukkan **pratinjau publik** atau **eksperimental** adalah bagian dari output perintah Azure CLI dan harus diharapkan.

## <a name="see-also"></a>Lihat juga

- [Daftar referensi inti untuk Azure CLI](/cli/azure/reference-index)
- [Ekstensi yang tersedia untuk Azure CLI](azure-cli-extensions-list.md)

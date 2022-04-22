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
ms.openlocfilehash: 4ac362b3579e7aac70295cd0f3222afbfcfbf0f6
ms.sourcegitcommit: a805041ebd77f92fa4b3025ba6856ea4aedae2ac
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/22/2022
ms.locfileid: "144003769"
---
# <a name="overview-azure-cli-terminology-and-support-levels"></a>Gambaran umum: Terminologi Azure CLI dan tingkat dukungan

Artikel ini menjelaskan terminologi Azure CLI.  Ada komponen sintaks, jenis referensi, dan status.  Ini adalah status yang menentukan tingkat dukungan.

## <a name="azure-cli-syntax-components"></a>Komponen sintaks Azure CLI

Sintaks Azure CLI adalah kombinasi grup, referensi, perintah, dan parameter. **Perintah referensi lengkap** sering kali disebut sebagai **perintah**.

| Layanan Azure | Grup Referensi | Subgrup referensi | Perintah | Perintah referensi lengkap | Contoh Parameter
|-|-|-|-|-|-|
| Azure CLI | [az config](../latest/docs-ref-autogen/config.yml) | | | az config | --local, --output -o
| Azure Network | [az network](../latest/docs-ref-autogen/network.yml) | application-gateway | buat | [az network application-gateway create](/cli/azure/network/application-gateway#az-network-application-gateway-create) | --name, --resource-group, --capacity
| Azure DevOps Server | [az pipelines](../latest/docs-ref-autogen/pipelines.yml) | agen | list | [az pipelines agent list](../latest/docs-ref-autogen/pipelines/agent.yml) | --pool-id, --agent-name, --demands

**Subgrup referensi** dapat memiliki beberapa tingkat seperti`az network application-gateway private-link ip-config add`

| Grup Referensi | Subgrup | || Perintah|
|-|-|-|-|-|
|jaringan|application-gateway|private-link|ip-config|$add

Lihat [Daftar referensi A -Z](../latest/docs-ref-autogen/reference-index.yml) untuk daftar lengkap perintah referensi.

## <a name="what-is-reference-type"></a>Apa itu jenis referensi?

Perintah Azure CLI adalah bagian dari layanan Azure CLI **inti** , atau merupakan **ekstensi**.  Ekstensi adalah add-on opsional.  Jenis referensi menentukan jadwal rilis, status, dan metode penginstalan seperti yang dijelaskan di sini:

|                |                           Core                           |                       Extensi                        |
| -------------- | -------------------------------------------------------- | ------------------------------------------------------ |
| **Referensi** | Merupakan bagian dari layanan utama Azure CLI                | Berupa perintah referensi opsional yang harus diinstal |
| **Instal**    | Bersama dengan [alat penginstal MSI]()                       | Secara individual dengan [az extension add]()                 |
| **Dirilis**   | Sesuai jadwal                                            | Saat fitur atau pembaruan baru tersedia            |
| **Status**     | Bisa berupa GA (Tersedia Umum), pratinjau atau percobaan | Juga bisa berupa GA, pratinjau atau percobaan                |

Untuk mendapatkan daftar grup perintah, jalankan `az`.  Untuk daftar ekstensi, gunakan perintah [tabel az extension list-available --output](/cli/azure/extension#az-extension-list-available) .

```azurecli-interactive
# Get list of all command groups
az

# Get list of extensions
az extension list-available --output table
```

### <a name="core"></a>Core

Referensi Azure CLI yang telah diterbitkan sebagai bagian permanen dari CLI disebut **referensi inti**. Semua referensi inti diinstal dengan Azure CLI dan Anda tidak dapat memilih subset referensi. Jika Anda menjalankan CLI melalui Azure Cloud Shell, referensi inti selalu diperbarui. 

### <a name="extension"></a>Extensi

Ekstensi tidak dikirim sebagai bagian dari CLI, tetapi dijalankan sebagai perintah CLI. Beberapa ekstensi adalah bagian permanen dari Azure CLI, tetapi ekstensi sering kali akan memberi Anda akses ke pratinjau pribadi dan perintah percobaan. Satu grup referensi, seperti **az iot hub**, dapat memiliki perintah inti dan ekstensi.  Berikut dua contohnya:

|      Perintah referensi lengkap       | Berupa Inti | Berupa ekstensi |
| --------------------------------- | ------- | ------------ |
| az iot hub list                   | ya     |              |
| az iot hub job list               |         | ya          |

Anda akan diminta untuk menginstal ekstensi saat pertama kali digunakan.  Anda juga dapat menginstal ekstensi dengan menjalankan perintah [az extension add](/cli/azure/extension#az-extension-add) .

Anda dapat mempelajari referensi ekstensi lebih lanjut termasuk penginstalan dan pembaruan di [Menggunakan ekstensi dengan Azure CLI](azure-cli-extensions-overview.md).  Lihat [Ekstensi yang tersedia untuk Azure CLI](azure-cli-extensions-list.md) untuk mengetahui daftar lengkap perintah referensi ekstensi.

## <a name="what-is-reference-status"></a>Apa itu status referensi?

Terlepas dari jenis referensi, referensi Azure CLI termasuk dalam tiga kategori status: **GA** (Tersedia Umum), **pratinjau publik** atau **eksperimental**. Ini adalah status perintah referensi, bukan jenis, yang menentukan stabilitas dan tingkat dukungan.

| | GA  | Pratinjau umum | Eksperimental
|-|-|-|-|
| **Stabilitas** | Permanen | Dapat berubah sebagai respons terhadap tanggapan pelanggan. Tunduk pada ketentuan [Pratinjau Microsoft Azure](https://azure.microsoft.com/support/legal/preview-supplemental-terms/). | Dapat berubah sebagai respons terhadap tanggapan pelanggan. Akan sering dimigrasikan ke pratinjau publik.  Dapat dihapus.
| **Tingkat dukungan** | Data | Sebagian | Tidak ada

> [!NOTE]
> Peringatan yang menunjukkan **pratinjau umum** atau **percobaan** adalah bagian dari output perintah Azure CLI dan harus dipertimbangkan.

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

Tabel di atas hanya contoh dan **tidak** mewakili status referensi saat ini misalnya.

## <a name="see-also"></a>Lihat juga

- [Azure CLI A - Daftar referensi Z](../latest/docs-ref-autogen/reference-index.yml)
- [Ekstensi yang tersedia untuk Azure CLI](azure-cli-extensions-list.md)
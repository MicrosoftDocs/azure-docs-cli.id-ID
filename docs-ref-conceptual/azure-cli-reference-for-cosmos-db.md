---
title: Azure CLI references for Azure Cosmos DB | Microsoft Docs
description: Cari perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure Cosmos DB.  Ikuti tautan ke artikel populer untuk mempelajari cara menggunakan Azure CLI untuk Azure Cosmos DB.
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli references, azure cosmos db
ms.openlocfilehash: 352ec51e0a9d1628969b9cd7fdad7b868d74a149
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439105"
---
# <a name="azure-cli-reference-commands-for-azure-cosmos-db"></a>Azure CLI reference commands for Azure Cosmos DB

Azure Command-Line Interface[(CLI)](./what-is-azure-cli.md)adalah seperangkat perintah yang digunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di banyak layanan Azure, termasuk Azure Cosmos DB, dan memberi Anda kemampuan untuk mengelola layanan Cosmos DB dari baris perintah.

Perintah Azure CLI untuk [Azure Cosmos DB](/azure/cosmos-db/introduction) terdiri dari dua bagian: inti dan ekstensi. Inti Azure CLI perintah kapal sebagai bagian dari CLI dan didukung penuh. Ekstensi memberi Anda akses ke perintah eksperimental dan pra-rilis. Untuk informasi selengkapnya tentang referensi ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).  

> [!NOTE]
> Anda diminta untuk menginstal referensi ekstensi pada penggunaan pertama. Atau, Anda dapat menggunakan perintah [tambahkan ekstensi az](/cli/azure/extension#az_extension_add) untuk menginstal ekstensi dengan nama secara manual.

Lihat [az cosmosdb](/cli/azure/service-page/azure%20cosmos%20db) for an alphabetic list of Azure CLI core dan extension references available for the Azure Cosmos DB service. Untuk referensi di setiap subkelompok, lihat tabel di bagian berikut:

- [SQL API](#sql-api-references)
- [API untuk MongoDB](#api-for-mongodb-references)
- [API Cassandra](#cassandra-api-references)
- [Managed Instance for Apache Cassandra](#managed-instance-for-apache-cassandra-references)
- [Gremlin API](#gremlin-api-references)
- [API Tabel](#table-api-references)
- [Referensi Cosmos DB tambahan](#additional-cosmos-db-references)

## <a name="sql-api-references"></a>referensi API SQL

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb sql](/cli/azure/cosmosdb/sql) | Mengelola sumber daya SQL dari akun Azure Cosmos DB. | [Manage Azure Cosmos Core SQL API resources using Azure CLI](/azure/cosmos-db/manage-with-cli) | Core |
| [az cosmosdb sql container](/cli/azure/cosmosdb/sql/container) | Kelola Kontainer SQL Azure Cosmos DB. | [Kontainer Azure Cosmos DB](/azure/cosmos-db/manage-with-cli#azure-cosmos-db-container) | Core |
| [az cosmosdb sql database](/cli/azure/cosmosdb/sql/database) | Kelola database SQL Azure Cosmos DB. | [Database Microsoft Azure Cosmos DB](/azure/cosmos-db/manage-with-cli#azure-cosmos-db-database) | Core |
| [az cosmosdb sql restorable-container](/cli/azure/cosmosdb/sql/restorable-container) | Mengelola berbagai versi kontainer SQL yang dapat dipulihkan dalam database akun Azure Cosmos DB. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb sql restorable-database](/cli/azure/cosmosdb/sql/restorable-database) | Mengelola berbagai versi database SQL yang dapat dipulihkan dalam database akun Azure Cosmos DB. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb sql restorable-resource](/cli/azure/cosmosdb/sql/restorable-resource) | Kelola database dan wadahnya yang dapat dipulihkan di akun Azure Cosmos DB untuk timestamp dan wilayah yang diberikan. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb sql role](/cli/azure/cosmosdb/sql/role) | Kelola sumber daya peran Azure Cosmos DB. | [Mengonfigurasi kontrol akses berbasis peran untuk akun Azure Cosmos DB Anda](/azure/cosmos-db/how-to-setup-rbac) | Ekstensi: cosmosdb-preview |
| [az cosmosdb sql stored-procedure](/cli/azure/cosmosdb/sql/stored-procedure) | Kelola Azure Cosmos DB SQL prosedur tersimpan. | [Cara menulis prosedur yang tersimpan](/azure/cosmos-db/how-to-write-stored-procedures-triggers-udfs#stored-procedures) | Core |
| [az cosmosdb sql trigger](/cli/azure/cosmosdb/sql/trigger) | Kelola pemicu SQL Azure Cosmos DB. | [Cara menulis pemicu](/azure/cosmos-db/how-to-write-stored-procedures-triggers-udfs#triggers) | Core |
| [az cosmosdb sql user-defined-function](/cli/azure/cosmosdb/sql/user-defined-function) | Kelola Azure Cosmos DB SQL fungsi yang ditentukan pengguna. | [Cara menulis fungsi yang ditentukan pengguna](/azure/cosmos-db/how-to-write-stored-procedures-triggers-udfs#udfs) | Core |

## <a name="api-for-mongodb-references"></a>Referensi API untuk MongoDB

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb mongodb](/cli/azure/cosmosdb/mongodb) | Mengelola sumber daya MongoDB dari akun Azure Cosmos DB. | [Pengenalan API untuk MongoDB](/azure/cosmos-db/mongodb-introduction) | Core |
| [az cosmosdb mongodb collection](/cli/azure/cosmosdb/mongodb/collection) | Kelola koleksi Azure Cosmos DB MongoDB.| [Membuat database dan koleksi untuk MongoDB menggunakan Azure CLI](/azure/cosmos-db/scripts/cli/mongodb/create) | Core |
| [az cosmosdb mongodb database](/cli/azure/cosmosdb/mongodb/database) | Kelola database Azure Cosmos DB MongoDB. | [Membuat database dan koleksi untuk MongoDB DB menggunakan Azure CLI](/azure/cosmos-db/scripts/cli/mongodb/create) | Core |
| [az cosmosdb mongodb restorable-collection](/cli/azure/cosmosdb/mongodb/restorable-collection) | Kelola berbagai versi koleksi MongoDB yang dapat dipulihkan dalam database akun Azure Cosmos DB. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb mongodb restorable-database](/cli/azure/cosmosdb/mongodb/restorable-database) | Mengelola berbagai versi database MongoDB yang dapat dipulihkan dalam akun Azure Cosmos DB. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb mongodb restorable-resource](/cli/azure/cosmosdb/mongodb/restorable-resource) | Kelola database dan koleksinya yang dapat dipulihkan di akun Azure Cosmos DB untuk timestamp dan wilayah tertentu. | | Ekstensi: cosmosdb-preview |

## <a name="cassandra-api-references"></a>Referensi Cassandra API

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb cassandra](/cli/azure/cosmosdb/cassandra) | Mengelola sumber daya Cassandra dari akun Azure Cosmos DB. | [Pengantar Cassandra API in Azure Cosmos DB](/azure/cosmos-db/cassandra-introduction) | Core |
| [az cosmosdb cassandra keyspace](/cli/azure/cosmosdb/cassandra/keyspace) | Manage Azure Cosmos DB Cassandra keyspaces. | [Membuat ruang kunci dan tabel](/azure/cosmos-db/cassandra-spark-ddl-ops) | Core |
| [az cosmosdb cassandra table](/cli/azure/cosmosdb/cassandra/table) | Manage Azure Cosmos DB Cassandra tables. | [Membuat ruang kunci dan tabel](/azure/cosmos-db/cassandra-spark-ddl-ops) | Core |

## <a name="managed-instance-for-apache-cassandra-references"></a>Contoh Terkelola untuk referensi Apache Cassandra

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az managed-cassandra](/cli/azure/managed-cassandra) | Referensi untuk Contoh Terkelola untuk Apache Cassandra. | [Apa contoh yang dikelola Azure untuk Apache Cassandra?](/azure/managed-instance-apache-cassandra/introduction) | Ekstensi: cosmosdb-preview |
| [az managed-cassandra cluster](/cli/azure/managed-cassandra/cluster) | Referensi untuk menangani Contoh Terkelola untuk kluster Apache Cassandra. | [Mengelola sumber daya Apache Cassandra menggunakan Azure CLI](/azure/managed-instance-apache-cassandra/manage-resources-cli) | Ekstensi: cosmosdb-preview |
| [az managed-cassandra datacenter](/cli/azure/managed-cassandra/datacenter) | Referensi untuk menangani Contoh Terkelola untuk pusat data Apache Cassandra. | [Mengelola sumber daya Apache Cassandra menggunakan Azure CLI](/azure/managed-instance-apache-cassandra/manage-resources-cli) | Ekstensi: cosmosdb-preview |

## <a name="gremlin-api-references"></a>Referensi API Gremlin

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb gremlin](/cli/azure/cosmosdb/gremlin) | Mengelola sumber daya Gremlin dari akun Azure Cosmos DB. | [Pengantar Gremlin API di Azure Cosmos DB](/azure/cosmos-db/graph-introduction) | Core |
| [az cosmosdb gremlin database](/cli/azure/cosmosdb/gremlin/database) | Kelola database Azure Cosmos DB Gremlin. | [Membuat akun API Azure Cosmos Gremlin, database, dan grafik menggunakan Azure CLI](/azure/cosmos-db/scripts/cli/gremlin/create) | Core |
| [az cosmosdb gremlin graph](/cli/azure/cosmosdb/gremlin/graph) | Kelola Grafik Azure Cosmos DB Gremlin. | [Membuat akun API Azure Cosmos Gremlin, database, dan grafik menggunakan Azure CLI](/azure/cosmos-db/scripts/cli/gremlin/create) | Core |

## <a name="table-api-references"></a>Referensi API Tabel

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb table](/cli/azure/cosmosdb/table) | Mengelola sumber daya Tabel dari akun Azure Cosmos DB. | [Pengantar Table API in Azure Cosmos DB](/azure/cosmos-db/table-introduction) | core |
| [az cosmosdb table throughput](/cli/azure/cosmosdb/table/throughput) | Mengelola sumber daya Tabel throughput dari akun Azure Cosmos DB. | [Unit permintaan di Azure Cosmos DB](/azure/cosmos-db/request-units) | Core |

## <a name="additional-cosmos-db-references"></a>Referensi Cosmos DB tambahan

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb identity](/cli/azure/cosmosdb/identity) | Kelola identitas layanan yang dikelola Azure Cosmos DB. | [Menggunakan identitas terkelola yang ditetapkan sistem untuk mengakses data Azure Cosmos DB](/azure/cosmos-db/managed-identity-based-authentication) | Core |
| [az cosmosdb keys](/cli/azure/cosmosdb/keys) | Kelola kunci Azure Cosmos DB. | [Mengamankan akses ke data di Azure Cosmos DB](/azure/cosmos-db/secure-access-to-data) | Core |
| [az cosmosdb network-rule](/cli/azure/cosmosdb/network-rule) | Kelola aturan jaringan Azure Cosmos DB. | [Mengonfigurasi akses ke Azure Cosmos DB dari jaringan virtual](/azure/cosmos-db/how-to-configure-vnet-service-endpoint) | Core |
| [az cosmosdb private-endpoint-connection](/cli/azure/cosmosdb/private-endpoint-connection) | Kelola koneksi endpoint pribadi Azure Cosmos DB. | [Konfigurasikan Tautan Pribadi Azure untuk akun Azure Cosmos](/azure/cosmos-db/how-to-configure-private-endpoints) | Core |
| [az cosmosdb private-link-resource](/cli/azure/cosmosdb/private-link-resource) | Kelola Sumber daya tautan pribadi Azure Cosmos DB. | [Konfigurasikan Tautan Pribadi Azure untuk akun Azure Cosmos](/azure/cosmos-db/how-to-configure-private-endpoints) | Core |
| [az cosmosdb restorable-database-account](/cli/azure/cosmosdb/restorable-database-account) | Mengelola akun Azure Cosmos DB yang dapat dipulihkan. | | Ekstensi: cosmosdb-preview |

## <a name="see-also"></a>Lihat juga

- [Mulai dengan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari tentang instalasi dan masuk.

- Temukan [referensi](/cli/azure/reference-index) tambahan dan ekstensi yang [tersedia](./azure-cli-extensions-list.md) dalam dokumentasi Azure CLI.

- Pelajari selengkapnya tentang referensi ekstensi di [Gunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

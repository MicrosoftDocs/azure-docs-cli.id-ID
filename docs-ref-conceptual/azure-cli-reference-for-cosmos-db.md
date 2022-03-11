---
title: Referensi Azure CLI untuk Azure Cosmos DB | Microsoft Docs
description: Temukan perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure Cosmos DB.  Ikuti tautan ke artikel populer untuk mempelajari cara menggunakan Azure CLI untuk Azure Cosmos DB.
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure cli, azure cosmos db
ms.openlocfilehash: 352ec51e0a9d1628969b9cd7fdad7b868d74a149
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439105"
---
# <a name="azure-cli-reference-commands-for-azure-cosmos-db"></a>Perintah referensi Azure CLI untuk Azure Cosmos DB

Azure Command-Line Interface ([CLI](./what-is-azure-cli.md)) adalah sekumpulan perintah yang digunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di berbagai layanan Azure, termasuk Azure Cosmos DB, dan memberi Anda kemampuan untuk mengelola layanan Cosmos DB dari baris perintah.

Perintah Azure CLI untuk [Azure Cosmos DB](/azure/cosmos-db/introduction) terdiri dari dua bagian: inti dan ekstensi. Perintah Azure CLI inti dikirimkan sebagai bagian dari CLI dan didukung sepenuhnya. Ekstensi memberi Anda akses ke perintah percobaan dan pra-rilis. Untuk informasi selengkapnya tentang ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).  

> [!NOTE]
> Anda diminta menginstal referensi ekstensi saat digunakan pertama kali. Sebagai alternatif, Anda dapat menggunakan perintah [az extension add](/cli/azure/extension#az_extension_add) untuk menginstal ekstensi secara manual berdasarkan nama.

Lihat [az cosmosdb](/cli/azure/service-page/azure%20cosmos%20db) mengetahui daftar alfabetik referensi inti dan ekstensi Azure CLI yang tersedia untuk layanan Azure Cosmos DB. Untuk referensi di setiap sub-grup, lihat tabel di bagian berikut:

- [SQL API](#sql-api-references)
- [API untuk MongoDB](#api-for-mongodb-references)
- [API Cassandra](#cassandra-api-references)
- [Managed Instance for Apache Cassandra](#managed-instance-for-apache-cassandra-references)
- [Gremlin API](#gremlin-api-references)
- [API Tabel](#table-api-references)
- [Referensi Cosmos DB lainnya](#additional-cosmos-db-references)

## <a name="sql-api-references"></a>Referensi SQL API

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb sql](/cli/azure/cosmosdb/sql) | Kelola sumber daya SQL dari akun Azure Cosmos DB. | [Mengelola sumber daya Azure Cosmos Core SQL API menggunakan Azure CLI](/azure/cosmos-db/manage-with-cli) | Core |
| [az cosmosdb sql container](/cli/azure/cosmosdb/sql/container) | Mengelola kontainer SQL Azure Cosmos DB. | [Kontainer Azure Cosmos DB](/azure/cosmos-db/manage-with-cli#azure-cosmos-db-container) | Core |
| [az cosmosdb sql database](/cli/azure/cosmosdb/sql/database) | Mengelola database SQL Azure Cosmos DB. | [Database Microsoft Azure Cosmos DB](/azure/cosmos-db/manage-with-cli#azure-cosmos-db-database) | Core |
| [az cosmosdb sql restorable-container](/cli/azure/cosmosdb/sql/restorable-container) | Mengelola berbagai versi kontainer SQL yang dapat dipulihkan dalam database akun Azure Cosmos DB. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb sql restorable-database](/cli/azure/cosmosdb/sql/restorable-database) | Mengelola berbagai versi database SQL yang dapat dipulihkan dalam database akun Azure Cosmos DB. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb sql restorable-resource](/cli/azure/cosmosdb/sql/restorable-resource) | Mengelola database dan kontainernya yang dapat dipulihkan di akun Azure Cosmos DB untuk stempel waktu dan wilayah tertentu. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb sql role](/cli/azure/cosmosdb/sql/role) | Mengelola sumber daya peran Azure Cosmos DB. | [Mengonfigurasi kontrol akses berbasis peran untuk akun Azure Cosmos DB](/azure/cosmos-db/how-to-setup-rbac) | Ekstensi: cosmosdb-preview |
| [az cosmosdb sql stored-procedure](/cli/azure/cosmosdb/sql/stored-procedure) | Mengelola prosedur tersimpan SQL Azure Cosmos DB. | [Cara menulis prosedur tersimpan](/azure/cosmos-db/how-to-write-stored-procedures-triggers-udfs#stored-procedures) | Core |
| [az cosmosdb sql trigger](/cli/azure/cosmosdb/sql/trigger) | Mengelola pemicu SQL Azure Cosmos DB. | [Cara menulis pemicu](/azure/cosmos-db/how-to-write-stored-procedures-triggers-udfs#triggers) | Core |
| [az cosmosdb sql user-defined-function](/cli/azure/cosmosdb/sql/user-defined-function) | Mengelola fungsi yang ditentukan pengguna SQL Azure Cosmos DB. | [Cara menulis fungsi yang ditentukan pengguna](/azure/cosmos-db/how-to-write-stored-procedures-triggers-udfs#udfs) | Core |

## <a name="api-for-mongodb-references"></a>Referensi API untuk MongoDB

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb mongodb](/cli/azure/cosmosdb/mongodb) | Mengelola sumber daya MongoDB akun Azure Cosmos DB. | [Pengantar API untuk MongoDB](/azure/cosmos-db/mongodb-introduction) | Core |
| [az cosmosdb mongodb collection](/cli/azure/cosmosdb/mongodb/collection) | Mengelola koleksi MongoDB Azure Cosmos DB.| [Membuat database dan koleksi untuk MongoDB menggunakan Azure CLI](/azure/cosmos-db/scripts/cli/mongodb/create) | Core |
| [az cosmosdb mongodb database](/cli/azure/cosmosdb/mongodb/database) | Mengelola database MongoDB Azure Cosmos DB. | [Membuat database dan koleksi untuk DB MongoDB menggunakan Azure CLI](/azure/cosmos-db/scripts/cli/mongodb/create) | Core |
| [az cosmosdb mongodb restorable-collection](/cli/azure/cosmosdb/mongodb/restorable-collection) | Mengelola berbagai versi koleksi MongoDB yang dapat dipulihkan dalam database akun Azure Cosmos DB. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb mongodb restorable-database](/cli/azure/cosmosdb/mongodb/restorable-database) | Mengelola berbagai versi database MongoDB yang dapat dipulihkan di akun Azure Cosmos DB. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb mongodb restorable-resource](/cli/azure/cosmosdb/mongodb/restorable-resource) | Mengelola database dan koleksinya yang dapat dipulihkan di akun Azure Cosmos DB untuk stempel waktu dan wilayah tertentu. | | Ekstensi: cosmosdb-preview |

## <a name="cassandra-api-references"></a>Referensi API Cassandra

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb cassandra](/cli/azure/cosmosdb/cassandra) | Mengelola sumber daya Cassandra akun Azure Cosmos DB. | [Pengantar API Cassandra Azure Cosmos DB](/azure/cosmos-db/cassandra-introduction) | Core |
| [az cosmosdb cassandra keyspace](/cli/azure/cosmosdb/cassandra/keyspace) | Mengelola keyspace Cassandra Azure Cosmos DB. | [Membuat keyspace dan tabel](/azure/cosmos-db/cassandra-spark-ddl-ops) | Core |
| [az cosmosdb cassandra table](/cli/azure/cosmosdb/cassandra/table) | Mengelola tabel Cassandra Azure Cosmos DB. | [Membuat keyspace dan tabel](/azure/cosmos-db/cassandra-spark-ddl-ops) | Core |

## <a name="managed-instance-for-apache-cassandra-references"></a>Referensi Managed Instance untuk Apache Cassandra

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az managed-cassandra](/cli/azure/managed-cassandra) | Referensi Managed Instance untuk Apache Cassandra. | [Apa itu Azure Managed Instance untuk Apache Cassandra?](/azure/managed-instance-apache-cassandra/introduction) | Ekstensi: cosmosdb-preview |
| [az managed-cassandra cluster](/cli/azure/managed-cassandra/cluster) | Referensi untuk menangani instans terkelola untuk kluster Apache Cassandra. | [Mengelola sumber daya Apache Cassandra menggunakan Azure CLI](/azure/managed-instance-apache-cassandra/manage-resources-cli) | Ekstensi: cosmosdb-preview |
| [az managed-cassandra datacenter](/cli/azure/managed-cassandra/datacenter) | Referensi untuk menangani Managed Instance untuk pusat data Apache Cassandra. | [Mengelola sumber daya Apache Cassandra menggunakan Azure CLI](/azure/managed-instance-apache-cassandra/manage-resources-cli) | Ekstensi: cosmosdb-preview |

## <a name="gremlin-api-references"></a>Referensi API Gremlin

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb gremlin](/cli/azure/cosmosdb/gremlin) | Mengelola sumber daya Gremlin akun Azure Cosmos DB. | [Pengantar Gremlin API di Azure Cosmos DB](/azure/cosmos-db/graph-introduction) | Core |
| [az cosmosdb gremlin database](/cli/azure/cosmosdb/gremlin/database) | Mengelola database Gremlin Azure Cosmos DB. | [Membuat akun, database, dan grafik Azure Cosmos Gremlin API menggunakan Azure CLI](/azure/cosmos-db/scripts/cli/gremlin/create) | Core |
| [az cosmosdb gremlin graph](/cli/azure/cosmosdb/gremlin/graph) | Mengelola grafik Gremlin Azure Cosmos DB. | [Membuat akun, database, dan grafik Azure Cosmos Gremlin API menggunakan Azure CLI](/azure/cosmos-db/scripts/cli/gremlin/create) | Core |

## <a name="table-api-references"></a>Referensi Table API

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb table](/cli/azure/cosmosdb/table) | Mengelola sumber daya Table akun Azure Cosmos DB. | [Pengantar Table API di Azure Cosmos DB](/azure/cosmos-db/table-introduction) | core |
| [az cosmosdb table throughput](/cli/azure/cosmosdb/table/throughput) | Mengelola sumber daya Table throughput akun Azure Cosmos DB. | [Unit permintaan di Azure Cosmos DB](/azure/cosmos-db/request-units) | Core |

## <a name="additional-cosmos-db-references"></a>Referensi Cosmos DB lainnya

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb identity](/cli/azure/cosmosdb/identity) | Mengelola identitas layanan yang dikelola Azure Cosmos DB. | [Menggunakan identitas terkelola yang ditetapkan sistem untuk mengakses data Azure Cosmos DB](/azure/cosmos-db/managed-identity-based-authentication) | Core |
| [az cosmosdb keys](/cli/azure/cosmosdb/keys) | Mengelola kunci Azure Cosmos DB. | [Mengamankan akses ke data di Azure Cosmos DB](/azure/cosmos-db/secure-access-to-data) | Core |
| [az cosmosdb network-rule](/cli/azure/cosmosdb/network-rule) | Mengelola aturan jaringan Azure Cosmos DB. | [Mengonfigurasi akses ke Azure Cosmos DB dari jaringan virtual](/azure/cosmos-db/how-to-configure-vnet-service-endpoint) | Core |
| [az cosmosdb private-endpoint-connection](/cli/azure/cosmosdb/private-endpoint-connection) | Mengelola koneksi titik akhir privat Azure Cosmos DB. | [Konfigurasikan Tautan Pribadi Azure untuk akun Azure Cosmos](/azure/cosmos-db/how-to-configure-private-endpoints) | Core |
| [az cosmosdb private-link-resource](/cli/azure/cosmosdb/private-link-resource) | Mengelola sumber daya tautan privat Azure Cosmos DB. | [Konfigurasikan Tautan Pribadi Azure untuk akun Azure Cosmos](/azure/cosmos-db/how-to-configure-private-endpoints) | Core |
| [az cosmosdb restorable-database-account](/cli/azure/cosmosdb/restorable-database-account) | Mengelola akun Azure Cosmos DB yang dapat dipulihkan. | | Ekstensi: cosmosdb-preview |

## <a name="see-also"></a>Lihat juga

- [Mulai gunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari penginstalan dan aktivitas masuk.

- Temukan [referensi](/cli/azure/reference-index) tambahan dan [ekstensi yang tersedia](./azure-cli-extensions-list.md) di dokumentasi Azure CLI.

- Pelajari referensi ekstensi lebih lanjut di [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

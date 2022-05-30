---
title: Referensi Azure CLI untuk Azure Cosmos DB | Microsoft Docs
description: Temukan perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure Cosmos DB.  Ikuti tautan ke artikel populer untuk mempelajari cara menggunakan Azure CLI untuk Azure Cosmos DB.
author: dbradish-microsoft
manager: barbkess
ms.tool: azure-cli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure cli, azure cosmos db
ms.openlocfilehash: 528b9d4b90f3ce3d7e4005f3edb3bd53cae963e4
ms.sourcegitcommit: 6822e5d700742617eabda5904fe2ca217bae9d28
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/30/2022
ms.locfileid: "145937696"
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
| [az cosmosdb sql](../latest/docs-ref-autogen/cosmosdb/sql.yml) | Kelola sumber daya SQL dari akun Azure Cosmos DB. | [Mengelola sumber daya Azure Cosmos Core SQL API menggunakan Azure CLI](/azure/cosmos-db/manage-with-cli) | Core |
| [az cosmosdb sql container](../latest/docs-ref-autogen/cosmosdb/sql/container.yml) | Mengelola kontainer SQL Azure Cosmos DB. | [Kontainer Azure Cosmos DB](/azure/cosmos-db/manage-with-cli#azure-cosmos-db-container) | Core |
| [az cosmosdb sql database](../latest/docs-ref-autogen/cosmosdb/sql/database.yml) | Mengelola database SQL Azure Cosmos DB. | [Database Microsoft Azure Cosmos DB](/azure/cosmos-db/manage-with-cli#azure-cosmos-db-database) | Core |
| [az cosmosdb sql restorable-container](../latest/docs-ref-autogen/cosmosdb/sql/restorable-container.yml) | Mengelola berbagai versi kontainer SQL yang dapat dipulihkan dalam database akun Azure Cosmos DB. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb sql restorable-database](../latest/docs-ref-autogen/cosmosdb/sql/restorable-database.yml) | Mengelola berbagai versi database SQL yang dapat dipulihkan dalam database akun Azure Cosmos DB. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb sql restorable-resource](../latest/docs-ref-autogen/cosmosdb/sql/restorable-resource.yml) | Mengelola database dan kontainernya yang dapat dipulihkan di akun Azure Cosmos DB untuk stempel waktu dan wilayah tertentu. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb sql role](../latest/docs-ref-autogen/cosmosdb/sql/role.yml) | Mengelola sumber daya peran Azure Cosmos DB. | [Mengonfigurasi kontrol akses berbasis peran untuk akun Azure Cosmos DB](/azure/cosmos-db/how-to-setup-rbac) | Ekstensi: cosmosdb-preview |
| [az cosmosdb sql stored-procedure](../latest/docs-ref-autogen/cosmosdb/sql/stored-procedure.yml) | Mengelola prosedur tersimpan SQL Azure Cosmos DB. | [Cara menulis prosedur tersimpan](/azure/cosmos-db/how-to-write-stored-procedures-triggers-udfs#stored-procedures) | Core |
| [az cosmosdb sql trigger](../latest/docs-ref-autogen/cosmosdb/sql/trigger.yml) | Mengelola pemicu SQL Azure Cosmos DB. | [Cara menulis pemicu](/azure/cosmos-db/how-to-write-stored-procedures-triggers-udfs#triggers) | Core |
| [az cosmosdb sql user-defined-function](../latest/docs-ref-autogen/cosmosdb/sql/user-defined-function.yml) | Mengelola fungsi yang ditentukan pengguna SQL Azure Cosmos DB. | [Cara menulis fungsi yang ditentukan pengguna](/azure/cosmos-db/how-to-write-stored-procedures-triggers-udfs#udfs) | Core |

## <a name="api-for-mongodb-references"></a>Referensi API untuk MongoDB

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb mongodb](../latest/docs-ref-autogen/cosmosdb/mongodb.yml) | Mengelola sumber daya MongoDB akun Azure Cosmos DB. | [Pengantar API untuk MongoDB](/azure/cosmos-db/mongodb-introduction) | Core |
| [az cosmosdb mongodb collection](../latest/docs-ref-autogen/cosmosdb/mongodb/collection.yml) | Mengelola koleksi MongoDB Azure Cosmos DB.| [Membuat database dan koleksi untuk MongoDB menggunakan Azure CLI](/azure/cosmos-db/scripts/cli/mongodb/create) | Core |
| [az cosmosdb mongodb database](../latest/docs-ref-autogen/cosmosdb/mongodb/database.yml) | Mengelola database MongoDB Azure Cosmos DB. | [Membuat database dan koleksi untuk DB MongoDB menggunakan Azure CLI](/azure/cosmos-db/scripts/cli/mongodb/create) | Core |
| [az cosmosdb mongodb restorable-collection](../latest/docs-ref-autogen/cosmosdb/mongodb/restorable-collection.yml) | Mengelola berbagai versi koleksi MongoDB yang dapat dipulihkan dalam database akun Azure Cosmos DB. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb mongodb restorable-database](../latest/docs-ref-autogen/cosmosdb/mongodb/restorable-database.yml) | Mengelola berbagai versi database MongoDB yang dapat dipulihkan di akun Azure Cosmos DB. | | Ekstensi: cosmosdb-preview |
| [az cosmosdb mongodb restorable-resource](../latest/docs-ref-autogen/cosmosdb/mongodb/restorable-resource.yml) | Mengelola database dan koleksinya yang dapat dipulihkan di akun Azure Cosmos DB untuk stempel waktu dan wilayah tertentu. | | Ekstensi: cosmosdb-preview |

## <a name="cassandra-api-references"></a>Referensi API Cassandra

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb cassandra](../latest/docs-ref-autogen/cosmosdb/cassandra.yml) | Mengelola sumber daya Cassandra akun Azure Cosmos DB. | [Pengantar API Cassandra Azure Cosmos DB](/azure/cosmos-db/cassandra-introduction) | Core |
| [az cosmosdb cassandra keyspace](../latest/docs-ref-autogen/cosmosdb/cassandra/keyspace.yml) | Mengelola keyspace Cassandra Azure Cosmos DB. | [Membuat keyspace dan tabel](/azure/cosmos-db/cassandra-spark-ddl-ops) | Core |
| [az cosmosdb cassandra table](../latest/docs-ref-autogen/cosmosdb/cassandra/table.yml) | Mengelola tabel Cassandra Azure Cosmos DB. | [Membuat keyspace dan tabel](/azure/cosmos-db/cassandra-spark-ddl-ops) | Core |

## <a name="managed-instance-for-apache-cassandra-references"></a>Referensi Managed Instance untuk Apache Cassandra

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az managed-cassandra](../latest/docs-ref-autogen/managed-cassandra.yml) | Referensi Managed Instance untuk Apache Cassandra. | [Apa itu Azure Managed Instance untuk Apache Cassandra?](/azure/managed-instance-apache-cassandra/introduction) | Ekstensi: cosmosdb-preview |
| [az managed-cassandra cluster](../latest/docs-ref-autogen/managed-cassandra/cluster.yml) | Referensi untuk menangani instans terkelola untuk kluster Apache Cassandra. | [Mengelola sumber daya Apache Cassandra menggunakan Azure CLI](/azure/managed-instance-apache-cassandra/manage-resources-cli) | Ekstensi: cosmosdb-preview |
| [az managed-cassandra datacenter](../latest/docs-ref-autogen/managed-cassandra/datacenter.yml) | Referensi untuk menangani Managed Instance untuk pusat data Apache Cassandra. | [Mengelola sumber daya Apache Cassandra menggunakan Azure CLI](/azure/managed-instance-apache-cassandra/manage-resources-cli) | Ekstensi: cosmosdb-preview |

## <a name="gremlin-api-references"></a>Referensi API Gremlin

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb gremlin](../latest/docs-ref-autogen/cosmosdb/gremlin.yml) | Mengelola sumber daya Gremlin akun Azure Cosmos DB. | [Pengantar Gremlin API di Azure Cosmos DB](/azure/cosmos-db/graph-introduction) | Core |
| [az cosmosdb gremlin database](../latest/docs-ref-autogen/cosmosdb/gremlin/database.yml) | Mengelola database Gremlin Azure Cosmos DB. | [Membuat akun, database, dan grafik Azure Cosmos Gremlin API menggunakan Azure CLI](/azure/cosmos-db/scripts/cli/gremlin/create) | Core |
| [az cosmosdb gremlin graph](../latest/docs-ref-autogen/cosmosdb/gremlin/graph.yml) | Mengelola grafik Gremlin Azure Cosmos DB. | [Membuat akun, database, dan grafik Azure Cosmos Gremlin API menggunakan Azure CLI](/azure/cosmos-db/scripts/cli/gremlin/create) | Core |

## <a name="table-api-references"></a>Referensi Table API

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb table](../latest/docs-ref-autogen/cosmosdb/table.yml) | Mengelola sumber daya Table akun Azure Cosmos DB. | [Pengantar Table API di Azure Cosmos DB](/azure/cosmos-db/table-introduction) | core |
| [az cosmosdb table throughput](../latest/docs-ref-autogen/cosmosdb/table/throughput.yml) | Mengelola sumber daya Table throughput akun Azure Cosmos DB. | [Unit permintaan di Azure Cosmos DB](/azure/cosmos-db/request-units) | Core |

## <a name="additional-cosmos-db-references"></a>Referensi Cosmos DB lainnya

| Referensi | Deskripsi | Informasi selengkapnya | Inti atau ekstensi
|-|-|-|-|
| [az cosmosdb identity](../latest/docs-ref-autogen/cosmosdb/identity.yml) | Mengelola identitas layanan yang dikelola Azure Cosmos DB. | [Menggunakan identitas terkelola yang ditetapkan sistem untuk mengakses data Azure Cosmos DB](/azure/cosmos-db/managed-identity-based-authentication) | Core |
| [az cosmosdb keys](../latest/docs-ref-autogen/cosmosdb/keys.yml) | Mengelola kunci Azure Cosmos DB. | [Mengamankan akses ke data di Azure Cosmos DB](/azure/cosmos-db/secure-access-to-data) | Core |
| [az cosmosdb network-rule](../latest/docs-ref-autogen/cosmosdb/network-rule.yml) | Mengelola aturan jaringan Azure Cosmos DB. | [Mengonfigurasi akses ke Azure Cosmos DB dari jaringan virtual](/azure/cosmos-db/how-to-configure-vnet-service-endpoint) | Core |
| [az cosmosdb private-endpoint-connection](../latest/docs-ref-autogen/cosmosdb/private-endpoint-connection.yml) | Mengelola koneksi titik akhir privat Azure Cosmos DB. | [Konfigurasikan Tautan Pribadi Azure untuk akun Azure Cosmos](/azure/cosmos-db/how-to-configure-private-endpoints) | Core |
| [az cosmosdb private-link-resource](../latest/docs-ref-autogen/cosmosdb/private-link-resource.yml) | Mengelola sumber daya tautan privat Azure Cosmos DB. | [Konfigurasikan Tautan Pribadi Azure untuk akun Azure Cosmos](/azure/cosmos-db/how-to-configure-private-endpoints) | Core |
| [az cosmosdb restorable-database-account](../latest/docs-ref-autogen/cosmosdb/restorable-database-account.yml) | Mengelola akun Azure Cosmos DB yang dapat dipulihkan. | | Ekstensi: cosmosdb-preview |

## <a name="see-also"></a>Lihat juga

* [Mulai gunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari penginstalan dan aktivitas masuk.
* Temukan [perintah referensi](../latest/docs-ref-autogen/reference-index.yml) tambahan dan [ekstensi yang tersedia](./azure-cli-extensions-list.md) dalam dokumentasi Azure CLI.
* [Pelajari cara menggunakan Bash dengan Azure CLI](./azure-cli-learn-bash.md)

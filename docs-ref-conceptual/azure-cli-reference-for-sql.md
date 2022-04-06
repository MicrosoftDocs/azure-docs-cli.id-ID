---
title: Referensi Azure CLI untuk Azure SQL | Microsoft Docs
description: Temukan perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure SQL.  Ikuti tautan ke artikel populer untuk mempelajari cara menggunakan Azure CLI for Azure SQL
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure cli, azure sql
ms.openlocfilehash: 4cbaf5ab5c5279c3b9e24c75d8e98bb0633c5b62
ms.sourcegitcommit: cbb162f5b74c5250338109317f06a152809c4b4c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/06/2022
ms.locfileid: "141406942"
---
# <a name="azure-cli-reference-commands-for-azure-sql"></a>Perintah referensi Azure CLI untuk Azure SQL

Azure Command-Line Interface ([CLI](./what-is-azure-cli.md)) adalah sekumpulan perintah yang digunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di berbagai layanan Azure dan memberi Anda kemampuan untuk mengelola layanan Azure SQL dari baris perintah.

Perintah Azure CLI untuk [Azure SQL](/azure/azure-sql/) hanya terdiri dari referensi inti dan dikirim sebagai bagian dari Azure CLI.  Lihat [az sql](../latest/docs-ref-autogen/sql.yml) untuk mengetahui daftar alfabetik referensi inti dan ekstensi Azure CLI yang tersedia untuk layanan Azure SQL. Untuk referensi setiap sub-grup, lihat tabel di bagian berikut:

- [Database SQL](#sql-database-references)
- [Instans Terkelola SQL](#sql-managed-instance-references)
- [Database SQL Managed Instance](#sql-managed-instance-database-references)
- [Server SQL](#sql-server-references)
- [Mesin virtual SQL](#sql-virtual-machine-references)
- [Referensi tambahan](#additional-sql-references)

## <a name="sql-database-references"></a>Referensi database SQL

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sql db](../latest/docs-ref-autogen/sql/db.yml) | Mengelola Azure SQL Database. | [Apa itu Azure SQL Database?](/azure/azure-sql/database/sql-database-paas-overview) |
| [az sql db audit-policy](../latest/docs-ref-autogen/sql/db/audit-policy.yml) | Mengelola kebijakan audit database SQL. | [Audit untuk Azure SQL Database](/azure/azure-sql/database/auditing-overview) |
| [az sql db classification](../latest/docs-ref-autogen/sql/db/classification.yml) | Mengelola klasifikasi sensitivitas database SQL. | [Penemuan dan Klasifikasi Data](/azure/azure-sql/database/data-discovery-and-classification-overview) |
| [az sql db classification recommendation](../latest/docs-ref-autogen/sql/db/classification/recommendation.yml) | Mengelola rekomendasi klasifikasi sensitivitas database. | [Penemuan dan Klasifikasi Data](/azure/azure-sql/database/data-discovery-and-classification-overview) |
| [az sql db ltr-backup](../latest/docs-ref-autogen/sql/db/ltr-backup.yml) | Mengelola cadangan retensi jangka panjang database SQL. | [Retensi jangka panjang](/azure/azure-sql/database/long-term-retention-overview) |
| [az sql db ltr-policy](../latest/docs-ref-autogen/sql/db/ltr-policy.yml) | Mengelola kebijakan penyimpanan jangka panjang database SQL. | [Kelola retensi cadangan jangka panjang Azure SQL Database](/azure/azure-sql/database/long-term-backup-retention-configure) |
| [az sql db op](../latest/docs-ref-autogen/sql/db/op.yml) | Mengelola operasi di database SQL. | [Mengonfigurasi dan mengelola referensi konten](/azure/azure-sql/database/how-to-content-reference-guide) |
| [az sql db replica](../latest/docs-ref-autogen/sql/db/replica.yml) | Mengelola replikasi antar database SQL. | [Replikasi ke Azure SQL Database](/azure/azure-sql/database/replication-to-sql-database) |
| [az sql db tde](../latest/docs-ref-autogen/sql/db/tde.yml) | Mengelola enkripsi data transparan database SQL. | [Enkripsi data transparan](/azure/azure-sql/database/transparent-data-encryption-tde-overview) |
| [az sql db threat-policy](../latest/docs-ref-autogen/sql/db/threat-policy.yml) | Mengelola kebijakan deteksi ancaman database SQL. | [Mengonfigurasi Perlindungan Ancaman Tingkat Lanjut](/azure/azure-sql/database/threat-detection-configure) |

## <a name="sql-managed-instance-references"></a>Referensi SQL Managed Instance

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sql mi](../latest/docs-ref-autogen/sql/mi.yml) | Mengelola Azure SQL Managed Instance. | [Apa itu Azure SQL Managed Instance?](/azure/azure-sql/managed-instance/sql-managed-instance-paas-overview) |
| [az sql mi ad-admin](../latest/docs-ref-autogen/sql/mi/ad-admin.yml) | Mengelola administrator Active Directory di SQL Managed Instance. | [Mengonfigurasi dan mengelola autentikasi Azure Active Directory dengan Azure SQL](/azure/azure-sql/database/authentication-aad-configure) |
| [az sql mi ad-only-auth](../latest/docs-ref-autogen/sql/mi/ad-only-auth.yml) | Mengelola pengaturan khusus Azure Active Directory SQL Managed Instance. | [Mengonfigurasi dan mengelola autentikasi Azure Active Directory dengan Azure SQL](/azure/azure-sql/database/authentication-aad-configure) |
| [az sql mi key](../latest/docs-ref-autogen/sql/mi/key.yml) | Mengelola kunci SQL Managed Instance. | [Mengonfigurasi Always Encrypted menggunakan Azure Key Vault](/azure/azure-sql/database/always-encrypted-azure-key-vault-configure) |
| [az sql mi op](../latest/docs-ref-autogen/sql/mi/op.yml) | Mengelola operasi di SQL Managed Instance. | [Ringkaan operasi pengelolaan Instans Terkelola SQL Azure](/azure/azure-sql/managed-instance/management-operations-overview) |
| [az sql mi tde-key](../latest/docs-ref-autogen/sql/mi/tde-key.yml) | Mengelola pelindung enkripsi di SQL Managed Instance. | [Enkripsi data transparan](/azure/azure-sql/database/transparent-data-encryption-tde-overview) |

## <a name="sql-managed-instance-database-references"></a>Referensi database SQL Managed Instance

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sql midb](../latest/docs-ref-autogen/sql/midb.yml) | Mengelola database Azure SQL Managed Instance. | [Apa itu Azure SQL Managed Instance?](/azure/azure-sql/managed-instance/sql-managed-instance-paas-overview) |
| [az sql midb log-replay](../latest/docs-ref-autogen/sql/midb/log-replay.yml) | Mengelola perintah layanan Pemutaran Ulang Log untuk database Azure SQL Managed Instance. | [Memigrasikan database dari SQL Server ke SQL Managed Instance menggunakan Layanan Pemutaran Ulang Log](/azure/azure-sql/managed-instance/log-replay-service-migrate) |
 [az sql midb ltr-backup](../latest/docs-ref-autogen/sql/midb/ltr-backup.yml) | Mengelola cadangan retensi jangka panjang database SQL Managed Instance. | [Mengelola retensi cadangan jangka panjang Azure SQL Managed Instance](/azure/azure-sql/managed-instance/long-term-backup-retention-configure) |
| [az sql midb ltr-policy](../latest/docs-ref-autogen/sql/midb/ltr-policy.yml) | Mengelola kebijakan penyimpanan jangka panjang database SQL Managed Instance. | [Retensi jangka panjang](/azure/azure-sql/database/long-term-retention-overview) |
| [az sql midb short-term-retention-policy](../latest/docs-ref-autogen/sql/midb/short-term-retention-policy.yml) | Mengelola kebijakan penyimpanan jangka pendek cadangan database SQL Managed Instance. | [Pencadangan otomatis](/azure/azure-sql/database/automated-backups-overview) |

## <a name="sql-server-references"></a>Referensi server SQL

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sql server](../latest/docs-ref-autogen/sql/server.yml) | Mengelola server SQL Database. | [Membuat dan mengelola server](/azure/azure-sql/database/single-database-manage) |
| [az sql server ad-admin](../latest/docs-ref-autogen/sql/server/ad-admin.yml) | Mengelola administrator Active Directory server. | [Mengonfigurasi dan mengelola autentikasi Azure Active Directory dengan Azure SQL](/azure/azure-sql/database/authentication-aad-configure) |
| [az sql server ad-only-auth](../latest/docs-ref-autogen/sql/server/ad-only-auth.yml) | Mengelola pengaturan Autentikasi khusus Azure Active Directory untuk server. | [Mengonfigurasi dan mengelola autentikasi Azure Active Directory dengan Azure SQL](/azure/azure-sql/database/authentication-aad-configure) |
| [az sql server audit-policy](../latest/docs-ref-autogen/sql/server/audit-policy.yml) | Mengelola kebijakan audit server. | [Audit untuk Azure SQL Database](/azure/azure-sql/database/auditing-overview) |
| [az sql server conn-policy](../latest/docs-ref-autogen/sql/server/conn-policy.yml) | Mengelola kebijakan koneksi server. | [Pengaturan konektivitas Azure SQL](/azure/azure-sql/database/connectivity-settings) |
| [az sql server dns-alias](../latest/docs-ref-autogen/sql/server/dns-alias.yml) | Mengelola alias DNS server. | [Alias DNS untuk Azure SQL Database](/azure/azure-sql/database/dns-alias-overview) |
| [az sql server firewall-rule](../latest/docs-ref-autogen/sql/server/firewall-rule.yml) | Mengelola aturan firewall server. | [Aturan firewall IP Azure SQL Database dan Azure Synapse](/azure/azure-sql/database/firewall-configure) |
| [az sql server key](../latest/docs-ref-autogen/sql/server/key.yml) | Mengelola kunci server. | [Aktifkan Enkripsi Data Transparan dengan kunci yang dikelola pelanggan dari Azure Key Vault](/azure/azure-sql/database/transparent-data-encryption-byok-configure) |
| [az sql server ms-support audit-policy](../latest/docs-ref-autogen/sql/server/ms-support/audit-policy.yml) | Mengelola kebijakan audit operasi dukungan Microsoft server. | [Audit untuk Azure SQL Database dan Azure Synapse Analytics](/azure/azure-sql/database/auditing-overview) |
| [az sql server tde-key](../latest/docs-ref-autogen/sql/server/tde-key.yml) | Mengelola pelindung enkripsi server. | [Aktifkan Enkripsi Data Transparan dengan kunci yang dikelola pelanggan dari Azure Key Vault](/azure/azure-sql/database/transparent-data-encryption-byok-configure) |
| [az sql server vnet-rule](../latest/docs-ref-autogen/sql/server/vnet-rule.yml) | Mengelola aturan jaringan virtual server. | [Gunakan titik akhir layanan jaringan virtual dan aturan untuk server](/azure/azure-sql/database/vnet-service-endpoint-rule-overview) |

## <a name="sql-virtual-machine-references"></a>Referensi mesin virtual SQL

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sql vm](../latest/docs-ref-autogen/sql/vm.yml) | Mengelola mesin virtual SQL. | [Apa itu SQL Server pada Azure Virtual Machines](/azure/azure-sql/virtual-machines/windows/sql-server-on-azure-vm-iaas-what-is-overview) |
| [az sql vm group](../latest/docs-ref-autogen/sql/vm/group.yml) | Mengelola grup mesin virtual SQL. | [Grup ketersediaan Selalu Aktif di SQL Server di Azure VMs](/azure/azure-sql/virtual-machines/windows/availability-group-overview) |
| [az sql vm group ag-listener](../latest/docs-ref-autogen/sql/vm/group/ag-listener.yml) | Mengelola listener grup ketersediaan SQL. | [Konfigurasikan satu atau beberapa listener grup ketersediaan AlwaysOn](/azure/azure-sql/virtual-machines/windows/availability-group-listener-powershell-configure) |

## <a name="additional-sql-references"></a>Referensi SQL tambahan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sql](../latest/docs-ref-autogen/sql.yml) | Mengelola Azure SQL. | [Apa yang dimaksud Azure SQL?](/azure/azure-sql/azure-sql-iaas-vs-paas-what-is-overview) |
| [az sql dw](../latest/docs-ref-autogen/sql/dw.yml) | Mengelola gudang data. | [Apa itu kumpulan SQL khusus (sebelumnya SQL DW) di Azure Synapse Analytics?](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is) |
| [az sql elastic-pool](../latest/docs-ref-autogen/sql/elastic-pool.yml) | Mengelola kumpulan elastis. | [Kumpulan elastis](/azure/azure-sql/database/elastic-pool-overview) |
| [az sql elastic-pool op](../latest/docs-ref-autogen/sql/elastic-pool/op.yml) | Mengelola operasi di kumpulan elastis. | [Kumpulan elastis](/azure/azure-sql/database/elastic-pool-overview) |
| [az sql failover-group](../latest/docs-ref-autogen/sql/failover-group.yml) | Mengelola grup failover SQL Database. | [Mengonfigurasi grup failover](/azure/azure-sql/database/auto-failover-group-configure) |
| [az sql instance-failover-group](../latest/docs-ref-autogen/sql/instance-failover-group.yml) | Menggunakan grup failover SQL Managed Instance. | [Mengonfigurasi grup failover](/azure/azure-sql/database/auto-failover-group-configure) |
| [az sql instance-pool](../latest/docs-ref-autogen/sql/instance-pool.yml) | Menggunakan kumpulan Managed Instance. | [Apa itu kumpulan Azure SQL Managed Instance?](/azure/azure-sql/managed-instance/instance-pools-overview) |
| [az sql stg](../latest/docs-ref-autogen/sql/stg.yml) | Kelola Grup Kepercayaan Server. | [Menggunakan Grup Kepercayaan Server](/azure/azure-sql/managed-instance/server-trust-group-overview) |
| [az sql virtual-cluster](../latest/docs-ref-autogen/sql/virtual-cluster.yml) | Mengelola kluster virtual SQL Managed Instance. | [Arsitektur konektivitas kluster virtual](/azure/azure-sql/managed-instance/connectivity-architecture-overview#virtual-cluster-connectivity-architecture) |

## <a name="see-also"></a>Lihat juga

- [Mulai gunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari penginstalan dan aktivitas masuk.

- Temukan [referensi](../latest/docs-ref-autogen/reference-index.yml) tambahan dan [ekstensi yang tersedia](./azure-cli-extensions-list.md) di dokumentasi Azure CLI.
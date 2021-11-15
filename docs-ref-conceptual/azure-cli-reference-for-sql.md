---
title: Azure CLI references for Azure SQL | Microsoft Docs
description: Cari perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure SQL.  Ikuti tautan ke artikel populer untuk mempelajari cara menggunakan Azure CLI untuk Azure SQL
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli references, azure sql
ms.openlocfilehash: 79fc835cd8d53de665d8187e2d8239c89b89a65a
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439090"
---
# <a name="azure-cli-reference-commands-for-azure-sql"></a>Azure CLI reference commands for Azure SQL

Azure Command-Line Interface[(CLI)](./what-is-azure-cli.md)adalah seperangkat perintah yang digunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di banyak layanan Azure dan memberi Anda kemampuan untuk mengelola layanan Azure SQL dari baris perintah.

Perintah Azure CLI untuk [Azure SQL](/azure/azure-sql/) hanya terdiri dari referensi inti dan kapal sebagai bagian dari Azure CLI.  Lihat [az sql](/cli/azure/sql) for an alphabetic list dari referensi inti dan ekstensi Azure CLI yang tersedia untuk layanan Azure SQL. Untuk referensi untuk setiap subkelompok, lihat tabel di bagian berikut:

- [Database SQL](#sql-database-references)
- [Instans Terkelola SQL](#sql-managed-instance-references)
- [database Instans Terkelola SQL](#sql-managed-instance-database-references)
- [Server SQL](#sql-server-references)
- [SQL mesin virtual](#sql-virtual-machine-references)
- [Referensi tambahan](#additional-sql-references)

## <a name="sql-database-references"></a>referensi database SQL

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sql db](/cli/azure/sql/db) | Mengelola Azure SQL Database. | [Apa itu Azure SQL Database?](/azure/azure-sql/database/sql-database-paas-overview) |
| [az sql db audit-policy](/cli/azure/sql/db/audit-policy) | Mengelola kebijakan audit database SQL. | [Audit untuk Azure SQL Database](/azure/azure-sql/database/auditing-overview) |
| [az sql db classification](/cli/azure/sql/db/classification) | Mengelola klasifikasi sensitivitas database SQL. | [Penemuan dan Klasifikasi Data](/azure/azure-sql/database/data-discovery-and-classification-overview) |
| [az sql db classification recommendation](/cli/azure/sql/db/classification/recommendation) | Mengelola rekomendasi klasifikasi sensitivitas database. | [Penemuan dan Klasifikasi Data](/azure/azure-sql/database/data-discovery-and-classification-overview) |
| [az sql db ltr-backup](/cli/azure/sql/db/ltr-backup) | Mengelola cadangan retensi jangka panjang database SQL. | [Retensi jangka panjang](/azure/azure-sql/database/long-term-retention-overview) |
| [az sql db ltr-policy](/cli/azure/sql/db/ltr-policy) | Mengelola kebijakan retensi jangka panjang database SQL. | [Kelola retensi cadangan jangka panjang Azure SQL Database](/azure/azure-sql/database/long-term-backup-retention-configure) |
| [az sql db op](/cli/azure/sql/db/op) | Mengelola operasi pada database SQL. | [Mengonfigurasi dan mengelola referensi konten](/azure/azure-sql/database/how-to-content-reference-guide) |
| [az sql db replica](/cli/azure/sql/db/replica) | Mengelola replikasi antara database SQL. | [Replikasi ke Azure SQL Database](/azure/azure-sql/database/replication-to-sql-database) |
| [az sql db tde](/cli/azure/sql/db/tde) | Mengelola enkripsi data transparan database SQL. | [Enkripsi data transparan](/azure/azure-sql/database/transparent-data-encryption-tde-overview) |
| [az sql db threat-policy](/cli/azure/sql/db/threat-policy) | Mengelola kebijakan deteksi ancaman database SQL. | [Mengonfigurasi Perlindungan Ancaman Tingkat Lanjut](/azure/azure-sql/database/threat-detection-configure) |

## <a name="sql-managed-instance-references"></a>referensi Instans Terkelola SQL

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sql mi](/cli/azure/sql/mi) | Kelola Instans Terkelola Azure SQL. | [Apa itu Azure SQL Managed Instance?](/azure/azure-sql/managed-instance/sql-managed-instance-paas-overview) |
| [az sql mi ad-admin](/cli/azure/sql/mi/ad-admin) | Mengelola administrator Direktori Aktif Instans Terkelola SQL. | [Mengonfigurasi dan mengelola autentikasi Azure Active Directory dengan Azure SQL](/azure/azure-sql/database/authentication-aad-configure) |
| [az sql mi ad-only-auth](/cli/azure/sql/mi/ad-only-auth) | Mengelola pengaturan Azure Active Directory Instance Terkelola SQL. | [Mengonfigurasi dan mengelola autentikasi Azure Active Directory dengan Azure SQL](/azure/azure-sql/database/authentication-aad-configure) |
| [az sql mi key](/cli/azure/sql/mi/key) | Mengelola kunci Instans Terkelola SQL. | [Mengonfigurasi Always Encrypted menggunakan Azure Key Vault](/azure/azure-sql/database/always-encrypted-azure-key-vault-configure) |
| [az sql mi op](/cli/azure/sql/mi/op) | Mengelola operasi pada Instans Terkelola SQL. | [Ringkaan operasi pengelolaan Instans Terkelola SQL Azure](/azure/azure-sql/managed-instance/management-operations-overview) |
| [az sql mi tde-key](/cli/azure/sql/mi/tde-key) | Mengelola pelindung enkripsi Instans Terkelola SQL. | [Enkripsi data transparan](/azure/azure-sql/database/transparent-data-encryption-tde-overview) |

## <a name="sql-managed-instance-database-references"></a>referensi database Instans Terkelola SQL

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sql midb](/cli/azure/sql/midb) | Kelola database Instans Terkelola Azure SQL. | [Apa itu Azure SQL Managed Instance?](/azure/azure-sql/managed-instance/sql-managed-instance-paas-overview) |
| [az sql midb log-replay](/cli/azure/sql/midb/log-replay) | Kelola perintah layanan Replay Log untuk database Instans Terkelola Azure SQL. | [Memigrasikan database dari SQL Server ke Instans Terkelola SQL dengan menggunakan Layanan Replay Log](/azure/azure-sql/managed-instance/log-replay-service-migrate) |
 [az sql midb ltr-backup](/cli/azure/sql/midb/ltr-backup) | Mengelola database Instans Terkelola SQL cadangan retensi jangka panjang. | [Mengelola retensi cadangan jangka panjang Azure SQL Managed Instance](/azure/azure-sql/managed-instance/long-term-backup-retention-configure) |
| [az sql midb ltr-policy](/cli/azure/sql/midb/ltr-policy) | Mengelola SQL database Instans Terkelola kebijakan retensi jangka panjang. | [Retensi jangka panjang](/azure/azure-sql/database/long-term-retention-overview) |
| [az sql midb short-term-retention-policy](/cli/azure/sql/midb/short-term-retention-policy) | Mengelola SQL kebijakan penyimpanan database Instans Terkelola. | [Pencadangan Otomatis](/azure/azure-sql/database/automated-backups-overview) |

## <a name="sql-server-references"></a>referensi server SQL

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sql server](/cli/azure/sql/server) | Kelola server SQL Database. | [Membuat dan mengelola server](/azure/azure-sql/database/single-database-manage) |
| [az sql server ad-admin](/cli/azure/sql/server/ad-admin) | Mengelola administrator Direktori Aktif server. | [Mengonfigurasi dan mengelola autentikasi Azure Active Directory dengan Azure SQL](/azure/azure-sql/database/authentication-aad-configure) |
| [az sql server ad-only-auth](/cli/azure/sql/server/ad-only-auth) | Mengelola pengaturan Autentikasi Azure Active Directory-satunya untuk server. | [Mengonfigurasi dan mengelola autentikasi Azure Active Directory dengan Azure SQL](/azure/azure-sql/database/authentication-aad-configure) |
| [az sql server audit-policy](/cli/azure/sql/server/audit-policy) | Mengelola kebijakan audit server. | [Audit untuk Azure SQL Database](/azure/azure-sql/database/auditing-overview) |
| [az sql server conn-policy](/cli/azure/sql/server/conn-policy) | Mengelola kebijakan koneksi server. | [Pengaturan konektivitas Azure SQL](/azure/azure-sql/database/connectivity-settings) |
| [az sql server dns-alias](/cli/azure/sql/server/dns-alias) | Mengelola alias DNS server. | [Alias DNS untuk Azure SQL Database](/azure/azure-sql/database/dns-alias-overview) |
| [az sql server firewall-rule](/cli/azure/sql/server/firewall-rule) | Mengelola aturan firewall server. | [Aturan firewall IP Azure SQL Database dan Azure Synapse](/azure/azure-sql/database/firewall-configure) |
| [az sql server key](/cli/azure/sql/server/key) | Mengelola kunci server. | [Aktifkan Enkripsi Data Transparan dengan kunci yang dikelola pelanggan dari Azure Key Vault](/azure/azure-sql/database/transparent-data-encryption-byok-configure) |
| [az sql server ms-support audit-policy](/cli/azure/sql/server/ms-support/audit-policy) | Mengelola kebijakan audit operasi dukungan Microsoft server. | [Audit untuk Azure SQL Database dan Azure Synapse Analytics](/azure/azure-sql/database/auditing-overview) |
| [az sql server tde-key](/cli/azure/sql/server/tde-key) | Mengelola pelindung enkripsi server. | [Aktifkan Enkripsi Data Transparan dengan kunci yang dikelola pelanggan dari Azure Key Vault](/azure/azure-sql/database/transparent-data-encryption-byok-configure) |
| [az sql server vnet-rule](/cli/azure/sql/server/vnet-rule) | Mengelola aturan jaringan virtual server. | [Gunakan titik akhir layanan jaringan virtual dan aturan untuk server](/azure/azure-sql/database/vnet-service-endpoint-rule-overview) |

## <a name="sql-virtual-machine-references"></a>SQL referensi mesin virtual

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sql vm](/cli/azure/sql/vm) | Kelola mesin virtual SQL. | [Apa yang SQL Server di Azure Virtual Machines](/azure/azure-sql/virtual-machines/windows/sql-server-on-azure-vm-iaas-what-is-overview) |
| [az sql vm group](/cli/azure/sql/vm/group) | Kelola grup mesin virtual SQL. | [Grup ketersediaan Selalu Aktif di SQL Server di Azure VMs](/azure/azure-sql/virtual-machines/windows/availability-group-overview) |
| [az sql vm group ag-listener](/cli/azure/sql/vm/group/ag-listener) | Kelola SQL ketersediaan pendengar grup. | [Mengonfigurasi satu atau beberapa pendengar grup Always On availability](/azure/azure-sql/virtual-machines/windows/availability-group-listener-powershell-configure) |

## <a name="additional-sql-references"></a>Referensi SQL tambahan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sql](/cli/azure/sql) | Kelola Azure SQL. | [Apa yang dimaksud Azure SQL?](/azure/azure-sql/azure-sql-iaas-vs-paas-what-is-overview) |
| [az sql dw](/cli/azure/sql/dw) | Mengelola gudang data. | [Apa itu kumpulan SQL khusus (sebelumnya SQL DW) di Azure Synapse Analytics?](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is) |
| [az sql elastic-pool](/cli/azure/sql/elastic-pool) | Kelola kolam elastis. | [Kumpulan database elastis](/azure/azure-sql/database/elastic-pool-overview) |
| [az sql elastic-pool op](/cli/azure/sql/elastic-pool/op) | Mengelola operasi pada kolam elastis. | [Kumpulan database elastis](/azure/azure-sql/database/elastic-pool-overview) |
| [az sql failover-group](/cli/azure/sql/failover-group) | Kelola grup failover SQL Database. | [Mengonfigurasi grup failover](/azure/azure-sql/database/auto-failover-group-configure) |
| [az sql instance-failover-group](/cli/azure/sql/instance-failover-group) | Gunakan grup failover Instans Terkelola SQL. | [Mengonfigurasi grup failover](/azure/azure-sql/database/auto-failover-group-configure) |
| [az sql instance-pool](/cli/azure/sql/instance-pool) | Gunakan Kelola kolam Instance. | [Apa itu kumpulan Azure SQL Managed Instance?](/azure/azure-sql/managed-instance/instance-pools-overview) |
| [az sql stg](/cli/azure/sql/stg) | Kelola Grup Kepercayaan Server. | [Menggunakan Grup Kepercayaan Server](/azure/azure-sql/managed-instance/server-trust-group-overview) |
| [az sql virtual-cluster](/cli/azure/sql/virtual-cluster) | Mengelola cluster virtual dari SQL Managed Instance. | [Arsitektur konektivitas kluster virtual](/azure/azure-sql/managed-instance/connectivity-architecture-overview#virtual-cluster-connectivity-architecture) |

## <a name="see-also"></a>Lihat juga

- [Mulai dengan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari tentang instalasi dan masuk.

- Temukan [referensi](/cli/azure/reference-index) tambahan dan ekstensi yang [tersedia](./azure-cli-extensions-list.md) dalam dokumentasi Azure CLI.

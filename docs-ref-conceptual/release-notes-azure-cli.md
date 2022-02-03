---
title: Rilis catatan & update – Azure CLI | Microsoft Docs
description: Pelajari tentang catatan rilis dan pembaruan Azure Command-Line Interface (CLI) terbaru untuk versi CLI saat ini dan beta.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 02/01/2022
ms.topic: article
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli updates, azure cli notes, azure cli versions
ms.openlocfilehash: bb173c94c6326ef415dd1010542c2cf4750d1302
ms.sourcegitcommit: f0c495b26b7fbfb6edc4563326b1a79615d5f780
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/02/2022
ms.locfileid: "137989299"
---
# <a name="azure-cli-release-notes"></a>Azure CLI release notes

## <a name="february-01-2022"></a>Tanggal 01 Februari 2022

Versi 2.33.0

### <a name="acr"></a>ACR

* `az acr connected-registry create`: Tambahkan `--notifications` ke dukungan menambahkan pola untuk menghasilkan peristiwa pemberitahuan pada artefak registri yang terhubung
* `az acr connected-registry update`: Tambahkan `--add-notifications` dan `--remove-notifications` untuk mendukung menambahkan atau menghapus pola untuk menghasilkan peristiwa pemberitahuan pada artefak registri yang terhubung

### <a name="aks"></a>AKS

* `az aks nodepool add/update/upgrade`: Tambahkan parameter `--aks-custom-headers` baru untuk mendukung header kustom
* `az aks create`Menambahkan parameter `--snapshot-id` baru untuk mendukung pembuatan nodepool dari snapshot saat membuat cluster
* `az aks nodepool add/upgrade`: Tambahkan parameter `--snapshot-id` baru untuk mendukung pembuatan nodepool dari snapshot
* `az aks snapshot create/delete/list/show`: Menambahkan perintah baru untuk mendukung pengelolaan operasi terkait snapshot
* `az aks update/az aks nodepool update`: Izinkan string kosong sebagai nilai label

### <a name="app-config"></a>Konfigurasi Aplikasi

* [MELANGGAR PERUBAHAN] Slot layanan aplikasi dukungan

### <a name="app-service"></a>App Service

* `az webapp vnet-integration add`: Perbaiki bug yang mencegah menambahkan vnet dalam langganan yang berbeda dari webapp
* `az functionapp vnet-integration add`: Perbaiki bug yang mencegah menambahkan vnet dalam langganan yang berbeda dari functionapp
* `az webapp create`: Dukungan bergabung dengan vnet dalam langganan yang berbeda
* `az functionapp create`: Dukungan bergabung dengan vnet dalam langganan yang berbeda
* `az functionapp create` : Hapus pratinjau dari runtime PowerShell untuk linux
* `az appservice plan update`: Tambahkan `--elastic-scale` dan `--max-elastic-worker-count` parameter untuk mendukung skala elastis
* `az webapp update`: Tambahkan `--minimum-elastic-instance-count` dan `--prewarmed-instance-count` parameter untuk mendukung pengaturan jumlah instans
* `az webapp up`: Tambahkan teks bantuan dan debug teks untuk penghematan dan pemuatan konfigurasi
* `az webapp list-runtimes`: Dukungan node 16-lts runtime untuk linux dan windows

### <a name="batch"></a>Batch

* `az batch create/activate`: Tambahkan info bantuan jalur paket aplikasi klarifikasi untuk argumen `--package-file`

### <a name="bot-service"></a>Layanan Bot

* `az bot create`: Tambahkan lokasi seperti yang ditentukan oleh pengguna untuk pembuatan bot untuk regionalitas / EUDB

### <a name="compute"></a>Compute 

* `az image builder create`: Tambahkan parameter `--proxy-vm-size` baru untuk mendukung kustomisasi ukuran VM proxy
* `az image builder create`: Menambahkan parameter `--build-vm-identities` baru untuk mendukung kustomisasi identitas yang ditetapkan pengguna
* `az vmss update`: Tambahkan parameter `--force-deletion` baru untuk mendukung kekuatan menghapus VMSS
* `az vm/vmss create`: Tambahkan log peringatan dan ubah bantuan untuk menginformasikan bahwa nilai `Contributor` `--role` default akan dihapus
* `az disk-encryption-set create`: Membuat parameter `--source-vault` tidak diperlukan
* `az vm create/update`: Tambahkan parameter `--v-cpus-available` baru dan `--v-cpus-per-core` untuk mendukung kustomisasi VMSize

### <a name="cosmos-db"></a>Cosmos DB

* `az managed-cassandra cluster status`: Menambahkan dukungan format tabel

### <a name="key-vault"></a>Key Vault

* `az keyvault create`: Tambahkan izin default pada pembuatan keyvault

### <a name="monitor"></a>Monitor

* `az monitor action-group`: Dukungan penerima hub acara

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`: Tambahkan parameter opsional baru bernama encrypt-dc-connections
* `az netappfiles volume export-policy add`: Tambahkan parameter opsional yang hilang kerberos5_read_only, kerberos5_read_write, kerberos5i_read_only, kerberos5i_read_write, kerberos5_p_read_only, kerberos5_p_read_write, has_root_access, chown_mode
* `az netappfiles account ad update`: Menambahkan perintah

### <a name="network"></a>Jaringan

* Tambahkan Microsoft.DataFactory/pabrik ke Titik Akhir Pribadi yang didukung
* Tambahkan Microsoft.Databricks/workspaces ke titik akhir pribadi yang didukung
* `az network private-endpoint`: Tambahkan parameter dan subkelompok untuk mendukung Konfigurasi IP, ASG dan NicName
* `az network traffic-manager endpoint create/update`: Tambahkan argumen `--min-child-ipv4` baru dan `--min-child-ipv6`.
* Tambahkan Microsoft.HybridCompute/privateLinkScopes ke Titik Akhir Pribadi yang didukung

### <a name="packaging"></a>Pengemasan

* Perbarui gambar dasar Dockerfile dari Alpine 3.14 hingga 3.15

### <a name="rdbms"></a>RDBMS

* `az postgres flexible-server create`: Mengubah versi postgres default

### <a name="redis"></a>Redis

* `az redis create`Menambahkan nilai default untuk identitas dan akses jaringan publik sebagai `None`

### <a name="serviceconnector"></a>ServiceConnector

* Mendukung sumber daya target baru: servicebus, eventhub, appconfig

### <a name="storage"></a>Penyimpanan

* Berhenti mendukung `--auth-mode login` untuk `az storage blob sync` dan `az storage fs directory upload/download`

## <a name="january-04-2022"></a>Tanggal 04 Januari 2022

Versi 2.32.0

### <a name="aks"></a>AKS

* `az aks create`: Tambahkan parameter `--enable-fips-image` baru untuk mendukung mengaktifkan gambar fips
* `az aks nodepool add`: Tambahkan parameter `--enable-fips-image` baru untuk mendukung mengaktifkan gambar fips

### <a name="app-service"></a>App Service

* [BREAKING CHANGE] `az webapp up`: Hapus dukungan untuk python|3.6 (linux dan windows), ruby|2.5 (linux), dan php|7.3 (windows) runtimes. Tambahkan dukungan untuk runtime python|3.9 (linux), php|8.0 (linux), dan ruby|2.7 (linux)
* [BREAKING CHANGE] `az webapp create`: Hapus dukungan untuk python|3.6 (linux dan windows), ruby|2.5 (linux), dan php|7.3 (windows) runtimes. Tambahkan dukungan untuk runtime python|3.9 (linux), php|8.0 (linux), dan ruby|2.7 (linux)
* [BREAKING CHANGE] `az functionapp create`: Hapus dukungan python 3.6
* Perbaiki #19550: `az staticwebapp users update`: Izinkan memperbarui peran pengguna aplikasi web statis lagi
* `az logicapp create`Autogenerasi Paket Layanan Aplikasi WS1 ketika tidak ada nilai untuk `--plan` atau `--consumption-plan-location` disediakan
* `az appservice plan create`Izinkan pembuatan Paket Layanan Aplikasi untuk Aplikasi Logika (SKU WS1, WS2, dan WS3)
* Perbaiki #20757: `az webapp up`: Perbaiki indeks daftar di luar jangkauan ketika tidak ada `--plan` argumen yang disahkan
* Perbaiki #18652: `az webapp up`: Cari \*.csproj di direktori anak
* `az webapp list-runtimes`: Hapus dukungan untuk python|3.6 (linux dan windows), ruby|2.5 (linux), dan php|7.3 (windows) runtimes. Tambahkan dukungan untuk runtime python|3.9 (linux), php|8.0 (linux), dan ruby|2.7 (linux)

### <a name="backup"></a>Cadangan

* `az backup restore restore-azurewl`: Menambahkan validasi sisi klien
* `az backup container unregister`: Mendukung tipe MAB untuk parameter `--backup-management-type`
* `az backup protectable-item list/show`: Tambahkan kebijakan perlindungan otomatis dan bidang node-list dalam respons untuk SQLInstance SQLAG
* `az backup protection auto-enable-for-azurewl/auto-disable-for-azurewl`: Menambahkan dukungan untuk SQLAG

### <a name="compute"></a>Compute 

* `az vm/vmss create/update`: Perluas validasi tipe lisensi untuk `--license-type` parameter
* `az sig image-definition list-shared`: Tambahkan parameter `--marker` baru dan `--show-next-marker` untuk mendukung paging
* `az sig image-version list-shared`: Tambahkan parameter `--marker` baru dan `--show-next-marker` untuk mendukung paging

### <a name="iot"></a>IoT

* `az iot hub update`: Tambahkan penanganan kesalahan untuk parameter unggah file dan memperbaiki kesalahan titik akhir penyimpanan $default kosong
* `az iot central app create`Menambahkan parameter `--mi-system-assigned` baru untuk mendukung pembuatan aplikasi dengan identitas terkelola yang ditetapkan sistem
* `az iot central app identity show/assign/remove`Menambahkan perintah baru untuk mengelola identitas terkelola yang ditetapkan sistem ke aplikasi IoT Central yang ada
* `az iot dps access-policy`: Diganti dengan `az iot dps policy`
* `az iot dps linked-hub create`: Tambahkan argumen kenyamanan untuk menghubungkan hub

### <a name="network"></a>Jaringan

* Perbaiki #19482: Azure Bastion AAD memperbaiki perubahan inti CLI baru
* `az network lb inbound-nat-pool create`: Tambahkan parameter baru `--backend-pool-name`

### <a name="profile"></a>Profil

* `az account show/set`: Tambahkan `-n`, `--name` argumen

### <a name="redis"></a>Redis

* `az redis identity`Menambahkan dukungan untuk menetapkan dan memodifikasi Identitas

### <a name="rest"></a>REST

* [BREAKING CHANGE] `az rest`: Hapus `resourceGroup`, `x509ThumbprintHex` transformasi

### <a name="role"></a>Peran

* [BREAKING CHANGE] `az ad sp create-for-rbac`: Jatuhkan `name` properti dari output. Gunakan `appId` sebagai gantinya
* [BREAKING CHANGE] `az ad sp create-for-rbac`: Tidak ada tugas peran yang akan dibuat secara default

### <a name="storage"></a>Penyimpanan

* `az storage copy`: Tambahkan argumen `extra_options` posisional untuk melewati opsi ke `azcopy`

### <a name="synapse"></a>Synapse

* [BREAKING CHANGE] `az synapse managed private endpoints create`: Hapus `--resource-id` dan `--group-id`, gunakan `--file` sebagai gantinya
* `az synapse sql pool create/restore`: Menambahkan parameter `--storage-type` untuk mendukung menentukan tipe akun penyimpanan
* `az synapse kql-script`Grup komando baru untuk mendukung skrip Kusto

## <a name="december-07-2021"></a>Tanggal 07 Desember 2021

Versi 2.31.0

### <a name="aks"></a>AKS

* `az aks update`: Mendukung edit label nodepool setelah pembuatan
* `az aks nodepool update`: Mendukung edit label nodepool setelah pembuatan
* `az aks create`: Memperbaiki masalah bahwa `--attach-acr` parameter tidak dapat bekerja

### <a name="ams"></a>AMS

* Hapus variabel usang 'identifier_uri' dari membuat metode sp
* Memperbarui versi api untuk pendaftaran tautan pribadi AMS dan AVA

### <a name="app-service"></a>App Service

* `az functionapp create`: Tambahkan dukungan untuk membuat webapp yang bergabung ke vnet
* `az webapp up`: Memperbaiki kegagalan untuk mendeteksi aplikasi web dotnet 6.0
* `az appservice ase update`Dukungan untuk mengizinkan koneksi endpoint pribadi baru di ASEv3
* `az appservice ase list-addresses`: Dukungan ASEv3
* `az staticwebapp identity assign`: Menetapkan identitas layanan terkelola ke aplikasi web statis
* `az staticwebapp identity remove`: Nonaktifkan identitas layanan terkelola aplikasi web statis
* `az staticwebapp identity show`: Menampilkan identitas layanan terkelola aplikasi web statis
* Perbaiki #17507: `az staticwebapp functions`: Tambahkan dukungan untuk menghubungkan aplikasi fungsi yang ada ke webapp statis (bawa fungsi Anda sendiri)
* `az staticwebapp create`: Memperbarui teks bantuan dengan panduan untuk repos di organisasi Github
* `az functionapp deployment source config-zip`: Perbaiki #12289: Izinkan build on zip deploy untuk aplikasi fungsi windows
* `az staticwebapp create`: Tambahkan pesan kesalahan yang lebih baik saat mencoba membuat webapp statis yang sudah ada
* `az appservice`: Perbaiki AttributeError selama penanganan kesalahan pengguna
* `az appservice plan create`: Tambahkan `--zone-redundant` parameter untuk mendukung redundansi zona yang memungkinkan untuk ketersediaan tinggi
* `az webapp ssh`: Tambahkan dukungan proksi
* `az webapp create-remote-connection`: Tambahkan dukungan proksi
* `az webapp log download/tail`: Tambahkan dukungan proksi
* `az webapp create`: Perbaiki penguraian url server registri kontainer untuk `--deployment-container-image-name/-i` argumen
* `az functionapp deployment source config-zip`Memperbaiki kembali keberhasilan ketika penyebaran tidak berhasil
* `az staticwebapp appsettings set`: Membuat set fungsional
* `az staticwebapp appsettings`: Beralih ke metode SDK pengaturan aplikasi SWA yang baru
* `az functionapp plan create`: Tambahkan `--zone-redundant` parameter untuk memberikan opsi untuk membuat paket layanan aplikasi redundan zona
* Mendukung identitas terkelola dalam wadah Layanan Aplikasi

### <a name="arm"></a>ARM

* `az resource\group list`: Mendukung kueri data hanya dengan meneruskan nama tag ke `--tag` parameter
* `az account management-group`: Tambahkan parameter `--no-register` baru untuk melewatkan pendaftaran RP untuk `Microsoft.Management`
* `az deployment`Prettify output kesalahan untuk penyebaran ARM
* `az bicep install`: Tambahkan parameter `--target-platform/-t` baru untuk menentukan platform berjalan Bicep CLI
* `az bicep upgrade`: Tambahkan parameter `--target-platform/-t` baru untuk menentukan platform berjalan Bicep CLI
* `az deployment sub/tenant/mg create`: Memperbaiki hasil `KeyError: 'resourceGroup'` output dalam format tabel saat menerapkan sumber daya tingkat grup non-sumber daya
* `az policy assignment create` dan `az policy assignment identity assign` mendukung penambahan identitas yang ditetapkan pengguna
* `az bicep install`Bekerja sekarang di belakang proxy perusahaan

### <a name="backup"></a>Cadangan

* GA `az backup` dan beberapa perbaikan bug
* `az backup protectable-item list/show`: Perbaiki AttributeError untuk server_name
* `az backup restore restore-disks`: Tambahkan dukungan untuk Cross Zonal Restore

### <a name="cognitive-services"></a>Cognitive Services

* `az cognitiveservices account deployment`: Tambahkan perintah `show`baru , `list`, , `create``delete`
* `az cognitiveservices account commitment-plan`: Tambahkan perintah `show`baru , `list`, , `create``delete`
* `az cognitiveservices commitment-tier`: Tambahkan perintah baru `list`

### <a name="compute"></a>Compute

* Perbaiki #20182: `az snapshot create`: Perbaiki bug deteksi otomatis untuk `--copy-start`
* Perbaiki #20133: `az vm create`: Perbaiki `--data-disk-delete-option` tidak berfungsi saat tidak `--attach-data-disks` disediakan
* Memperbaiki decoding diagnostik boot
* `az vm create/update`: Tambahkan parameter `--enable-hibernation` baru untuk mendukung kemampuan hibernasi yang memungkinkan
* `az vm/vmss run-command show`Menambahkan parameter `--instance-view` baru untuk mendukung pelacakan kemajuan RunCommand
* Memperbarui deskripsi bantuan untuk disk yang tidak terurus
* `az disk create/update`: Tambahkan `--public-network-access` argumen untuk mengontrol kebijakan untuk ekspor pada disk
* `az disk create/update`: Tambahkan `--accelerated-network` argumen untuk mendukung jaringan yang dipercepat
* `az snapshot create/update`: Tambahkan `--public-network-access` argumen untuk mengontrol kebijakan untuk ekspor pada disk
* `az snapshot create/update`: Menambahkan `--accelerated-network` argumen mendukung jaringan yang dipercepat
* `az snapshot create`: Perbaiki #20258: Perbaiki pembuatan snapshot dari disk Uniform VMSS OS

### <a name="eventgrid"></a>EventGrid

* GA `az eventgrid system-topic`

### <a name="key-vault"></a>Key Vault

* `az keyvault key encrypt/decrypt`Dukungan algoritma AES untuk MHSM
* `az keyvault key rotation-policy update`: Mendukung kasus unta dan kasus ular json untuk `--value`

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles volume create`: Memperbaiki kebijakan ekspor volume

### <a name="network"></a>Jaringan

* `az network express-route peering connection ipv6-config`: Tambahkan perintah `set`baru , `remove`
* `az network application-gateway waf-policy managed-rule exclusion`: Tambahkan subkelompok `rule-set` baru untuk mendukung pengecualian per aturan
* `az network bastion create`: Perbaiki validator yang tidak valid saat `--scale-units` tidak ada
* `az network vnet create``--enable-encryption` Menambahkan argumen untuk mendukung mengaktifkan enkripsi pada jaringan virtual
* `az network vnet update``--enable-encryption` Menambahkan argumen untuk mendukung mengaktifkan enkripsi pada jaringan virtual
* `az network vnet create`: Tambahkan `--encryption-enforcement-policy` argumen untuk memilih Jika Mesin Virtual tanpa enkripsi diizinkan di Jaringan Virtual terenkripsi.
* `az network vnet update`: Tambahkan `--encryption-enforcement-policy` argumen untuk memilih Jika Mesin Virtual tanpa enkripsi diizinkan di Jaringan Virtual terenkripsi.

### <a name="packaging"></a>Pengemasan

* Mendukung Python 3.10
* Tambahkan Dockerfile.mariner untuk mendukung pembangunan Mariner

### <a name="profile"></a>Profil

* `az logout`, `az account clear`: Hapus file cache token ADAL `accessTokens.json`

### <a name="rdbms"></a>RDBMS

* Perbaiki bug akhiran zona DNS pribadi
* Perbaiki #20124: `az mysql/postgres flexible-server db create`: Buat grup sumber daya dan nama server diperlukan
* `az postgres flexible-server`: Hapus tag pratinjau

### <a name="storage"></a>Penyimpanan

* `az storage share list-handle/close-handle`: Perintah baru untuk pegangan berbagi
* Tingkat akun GA dan tingkat versi gumpalan penyimpanan yang tidak berubah

### <a name="synapse"></a>Synapse

* [MELANGGAR PERUBAHAN] `az synapse sql/pool audit-policy`: Hapus `--blob-auditing-policy-name`
* `az synapse notebook/spark-job-definition`: Tambahkan `--folder-path` argumen
* `az synapse spark pool create/update`: Tambahkan `--spark-config-file-path`
* `az synapse spark job submit`: Perbaiki untuk `--main-class-name`
* `az synapse sql-script`: Grup perintah baru untuk mendukung manajemen skrip sql

## <a name="november-02-2021"></a>November 02, 2021

Versi 2.30.0

### <a name="core"></a>Core

* [MELANGGAR PERUBAHAN] Bermigrasi dari ADAL ke MSAL. Untuk detail lebih lanjut, lihat [Azure CLI berbasis MSAL](/cli/azure/msal-based-azure-cli)

### <a name="acr"></a>ACR

* [BREAKING CHANGE] `az connected-registry`: `--repository` bendera versi `-t` pendek sedang dihapus.
* [BREAKING CHANGE] `az connected-registry install renew credentials`: Sekarang mengharuskan pengguna untuk mengkonfirmasi pembuatan kata sandi.
* `az connected-registry install`: Terdepresiasi dan alihkan ke `az acr connected-registry get-settings`.
* `az connected-registry repo`: Terdepresiasi dan alihkan ke `az acr connected-registry permissions update`.
* `az connected-registry permissions show`Perintah baru yang memungkinkan pengguna untuk melihat informasi peta lingkup sinkronisasi.
* `az connected-registry get-settings`Perintah baru yang mengambil informasi yang diperlukan untuk menginstal registri yang terhubung dan memungkinkan pembuatan kata sandi token sinkronisasi baru.
* `az connected-registry create`: Tidak lagi menambahkan postfix ke token sinkronisasi dan nama peta lingkup.

### <a name="aks"></a>AKS

* `az aks create/update`: Tambahkan parameter `--aks-custom-headers` baru untuk mendukung header kustom
* `az aks create`: Pengaturan dukungan `--private-dns-zone` tidak ada untuk pembuatan klaster pribadi
* `az aks create/update`: Tambahkan parameter `--enable-secret-rotation` baru dan `--rotation-poll-interval` untuk mendukung rotasi rahasia
* `az aks enable-addons`: Tambahkan parameter `--enable-secret-rotation` baru dan `--rotation-poll-interval` untuk mendukung rotasi rahasia

### <a name="app-config"></a>Konfigurasi Aplikasi

* `az appconfig kv import/export`Menambahkan parameter `--profile` baru untuk mendukung penggunaan `appconfig/kvset` profil

### <a name="app-service"></a>App Service

* Perbaiki #19617: `az webapp ssh`: Buka Web SSH pada instans yang ditentukan
* `az staticwebapp hostname`: Dukungan menambahkan nama host webapp statis melalui validasi TXT
* Aktifkan dukungan untuk PowerShell pada aplikasi fungsi Linux dengan V4

### <a name="arm"></a>ARM

* `az bicep publish`: Tambahkan perintah baru untuk menerbitkan modul bisep

### <a name="aro"></a>ARO

* `az aro create`: Hapus URI Pengenal

### <a name="compute"></a>Compute

* `az disk update`: Memperbaiki masalah bahwa memperbarui kebijakan akses jaringan gagal `AllowPrivate`
* `az vm update``--host` Menambahkan argumen dan `--host-group` argumen untuk mendukung menetapkan VM yang ada ke ADH tertentu
* Perbaiki # 19599: `az vm create`Perbaiki masalah yang `--nic-delete-option` tidak berfungsi ketika tidak `--nics` disediakan.
* `az snapshot create`: Dukungan copyStart sebagai createOption
* `az vmss create/update`: Dukungan dalam-tamu patching untuk VMSS
* `az vm application set/list`: Menambahkan perintah baru untuk mendukung aplikasi VM
* `az vmss application set/list`: Menambahkan perintah baru untuk mendukung aplikasi VMSS
* `az vm create`: Tambahkan `--ephemeral-os-disk-placement` argumen untuk mendukung memilih lokasi penyediaan disk EPHEMERAL OS
* `az vmss create`: Tambahkan `--ephemeral-os-disk-placement` argumen untuk mendukung memilih lokasi penyediaan disk EPHEMERAL OS
* `az vm update`: Tambahkan `--size` argumen untuk mendukung perubahan ukuran
* `az vmss update`: Tambahkan `--vm-sku` argumen untuk mendukung perubahan ukuran
* `az vm run-command`: Menambahkan perintah baru untuk mendukung pengelolaan perintah yang sedang berjalan di VM
* `az vm update`: Tambahkan `--ephemeral-os-disk-placement` argumen untuk mendukung pilih lokasi penyediaan disk OS Ephemeral
* `az vmss update`: Tambahkan `--ephemeral-os-disk-placement` argumen untuk mendukung pilih lokasi penyediaan disk OS Ephemeral
* `az sig gallery-application`: Menambahkan perintah baru untuk mendukung aplikasi galeri pengelola
* `az sig gallery-application version`: Menambahkan perintah baru untuk mendukung pengelolaan versi aplikasi galeri
* GA fitur yang terkait dengan Flex VMSS

### <a name="container"></a>Kontainer

* `az container create`: Menambahkan parameter `--zone` untuk mendukung pemilihan Availability Zone
* `az container create`Memperbaiki masalah yang `--subnet` atau `--vnet` tidak dapat digunakan dengan tipe `Public` alamat IP untuk memungkinkan `Private`
* `az container create`: Tambahkan Dukungan untuk `--registry-login-server` bekerja dengan `--acr-identity`

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb mongodb retrieve-latest-backup-time`: Tambahkan perintah baru untuk mengambil timestamp terbaru yang dapat dipulihkan untuk Akun Mongo.
* `az cosmosdb locations`: Tambahkan perintah baru untuk mencantumkan lokasi akun dan propertinya.
* `az managed-cassandra cluster/data-center`: Dukungan GA untuk klaster cassandra dan pusat data yang dikelola

### <a name="dms"></a>DMS

* `az dms project create/az dms project task create` : Tambahkan proyek/tugas MySQL untuk migrasi offline.

### <a name="functionapp"></a>FunctionApp

* [BREAKING CHANGE] `az functionapp devops-pipeline`: Hapus perintah dan pindahkan ke `functionapp` ekstensi

### <a name="hdinsight"></a>HDInsight

* `az hdinsight create`: Tambahkan dua parameter `--zones` dan `--private-link-configurations` untuk mendukung pembuatan cluster dengan fitur availability zone dan membuat cluster berkemampuan tautan pribadi dengan fitur konfigurasi tautan pribadi.

### <a name="key-vault"></a>Key Vault

* Mendukung Keyvault SKR
* `az keyvault key random`: Minta beberapa byte acak dari managedHSM
* `az keyvault rotation-policy/key rotate`Dukungan memutar kunci dan mengelola kebijakan rotasi kunci
* `az keyvault create/update`: Menambahkan `--public-network-access` parameter

### <a name="monitor"></a>Monitor

* `az monitor metrics alert condition` : Tambahkan dukungan untuk 'lewati validasi metrik'

### <a name="netappfiles"></a>NetAppFiles

* [BREAKING CHANGE] `az netappfiles account backup-policy create/update`: Hapus parameter `--yearly-backups`opsional .
* `az netappfiles account list`: Tambahkan opsi untuk melewatkan `--resource-group` parameter dan mengambil akun untuk berlangganan.
* `az netappfiles pool create`: Menambahkan parameter opsional bernama `--encryption-type`
* `az netappfiles volume create`: Tambahkan parameter opsional: `--network-features`, , `--avs-data-store`, `--default-group-quota`, `--default-user-quota``--is-def-quota-enabled`
* `az netappfiles volume update`: Tambahkan parameter opsional: `--default-group-quota`, , `--default-user-quota``--is-def-quota-enabled`

### <a name="network"></a>Jaringan

* `az network bastion create`: Tambahkan parameter `--scale-units` baru dan `--sku` untuk mendukung unit skala pengaturan
* `az network vnet`: Menambahkan parameter `--bgp-community`
* `az network private-endpoint-connection`: Dukungan "Microsoft.Cache/Redis"
* `az network private-endpoint-connection`: Dukungan "Microsoft.SignalrService/WebPubsub"

### <a name="rdbms"></a>RDBMS

* Memperkenalkan perintah georestore MySQL dan memperbarui validator
* GA `az mysql flexible-server`

### <a name="service-bus"></a>Service Bus

* Perbaiki kapasitas MU untuk menyertakan 16 saat memperbarui namespace

### <a name="serviceconnector"></a>ServiceConnector

* `az webapp/spring-cloud connection`Grup perintah baru untuk mendukung koneksi layanan ke layanan

### <a name="sql"></a>SQL

* `az sql server ad-admin`Memperbaiki perubahan melanggar yang dibuat untuk memperbarui dan menghapus

### <a name="synapse"></a>Synapse

* `az synapse kusto`: Tambahkan dukungan kusto pool (mgmt)

## <a name="october-29-2021"></a>29 Oktober 2021

Versi 2.29.2

### <a name="aro"></a>ARO

* Hotfix: `az aro create`: Hapus URI Pengenal

## <a name="october-21-2021"></a>Tanggal 21 Oktober 2021

Versi 2.29.1

### <a name="compute"></a>Compute

* Hotfix: Perbaiki perintah webapp statis yang rusak karena peningkatan `azure-mgmt-web` ke 4.0.0

## <a name="october-12-2021"></a>Tanggal 12 Oktober 2021

Versi 2.29.0

### <a name="aks"></a>AKS

* `az aks check-acr`Benjolan canipull ke 0.0.3 alpha untuk mendukung awan berdaulat
* `az aks create/update`: Tambahkan parameter `--disable-local-accounts` baru untuk mendukung menonaktifkan akun lokal
* `az aks enable-addons`: Mendukung addon open-service-mesh
* `az aks create/update`: Menambahkan dukungan untuk memperbarui tag

### <a name="app-config"></a>Konfigurasi Aplikasi

* Memperbaiki dependensi untuk beberapa instalasi `jsondiff` dan `javaproperties`

### <a name="app-service"></a>App Service

* `az webapp create/up`: Memperbaiki kesalahan ketik versi java yang salah dalam bantuan
* `az logicapp create/delete/show/list`: Menambahkan perintah baru untuk mendukung operasi terkait logicapp
* `az staticwebapp environment delete`: Tambahkan perintah untuk mendukung penghapusan lingkungan aplikasi statis
* `az functionapp show`: Menambahkan validasi jenis untuk operasi pertunjukan
* `az webapp config backup list`: Memperbaiki masalah yang mengembalikan konfigurasi cadangan alih-alih daftar cadangan
* `az logicapp start/restart/stop`: Tambahkan perintah baru untuk logicapp
* `az webapp config storage-account`: Memperbarui deskripsi parameter

### <a name="arm"></a>ARM

* `az deployment`: Hapus log badan permintaan pencetakan dari kebijakan kustom
* `az deployment group create`: Perbaiki lingkup yang salah dalam contoh membuat penyebaran dari spesifikasi templat
* `az ts create`: Menyederhanakan pesan konfirmasi menimpa

### <a name="backup"></a>Cadangan

* `az backup container register`: Perbaiki bug refresh container
* `az backup`: Tambahkan fungsi CRR untuk Azure Workload
* `az backup`: Tambahkan dukungan untuk tipe manajemen cadangan MAB di beberapa sub perintah

### <a name="compute"></a>Compute

* `az sig create/update`: Tambahkan parameter `--soft-delete` baru untuk mendukung penghapusan lunak
* `az sig image-version`: Tambahkan parameter `--replication-mode` baru untuk mendukung mode replikasi pengaturan
* `az vm/vmss update`: Perbaiki disosiasi VM/VMSS dari reservasi kapasitas
* `az vm/vmss create`: Sembunyikan alias `--data-delete-option` dalam bantuan
* `az vmss create`: Mendukung pembuatan cepat untuk VMSS fleksibel

### <a name="container"></a>Kontainer

* [BREAKING CHANGE] `az container create`: Hapus `--network-profile` parameter, properti tidak lagi didukung
* `az container logs`: Memperbaiki kesalahan atribut yang diperkenalkan oleh migrasi Track 2
* `az container create`: Menambahkan parameter `--acr-identity` untuk mendukung penarikan gambar ACR yang diautentikasi MSI

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb identity assign/remove`: Menambahkan dukungan untuk identitas pengguna

### <a name="eventhub"></a>Eventhub

* `az eventhubs namespace update`: Tambahkan `--infra-encryption` enkripsi (enable-require-infrastructure-encryption).
* `az eventhubs namespace create/update`: Tambahkan `--disable-local-auth` untuk mengaktifkan atau menonaktifkan autentikasi SAS.
* `az eventhubs namespace`: Tambahkan `private-endpoint-connection` dan `private-link-resource` perintah grup

### <a name="key-vault"></a>Key Vault

* [MELANGGAR PERUBAHAN] Fix # 18479: `az keyvault network-rule add`: Perbaiki bug yang memungkinkan duplikat `--ip-address` dengan yang sudah ada dalam aturan jaringan
* Perbaiki #10254: `az keyvault network-rule add`: Tambahkan kemampuan untuk menerima beberapa alamat IP sebagai daftar dalam bentuk `--ip-address ip1 [ip2] [ip3]...`
* `az keyvault delete`: Tambahkan peringatan saat menghapus HSM yang dikelola

### <a name="network"></a>Jaringan

* Tambah `az network custom-ip prefix wait`
* Tambah `az network vnet-gateway packet-capture wait`
* Tambah `az network vnet-gateway vpn-client ipsec-policy wait`
* Tambah `az network vnet-gateway nat-rule wait`
* Tambah `az network vpn-connection packet-capture wait`
* Dukungan tautan dan endpoint pribadi untuk penyedia `Microsoft.BotService/botServices` untuk mendukung operasi endpoint pribadi
* `az network application-gateway client-cert`: Tambahkan perintah `update` dan `show`
* `az network application-gateway ssl-profile`: Tambahkan perintah `update` dan `show`
* `az network application-gateway http-listener create`: Menambahkan parameter `--ssl-profile`
* `az network application-gateway http-listener update`: Menambahkan parameter `--ssl-profile`
* Onboard hdinsight private link2 cmdlets jaringan
* `az network bastion create`: Tambahkan `--tags` argumen
* Dukungan tautan dan titik akhir pribadi untuk penyedia `Microsoft.Authorization/resourceManagementPrivateLinks`
* Dukungan tautan dan titik akhir pribadi untuk penyedia `Microsoft.MachineLearningServices/workspaces`

### <a name="profile"></a>Profil

* `az account show`: Terdepresiasi `--sdk-auth`

### <a name="rdbms"></a>RDBMS

* [BREAKING CHANGE] `az postgres flexible-server migration`: Perubahan `--properties @{filepath}` ke `--properties {filepath}`
* `az postgres flexible-server migration create`Pengguna dapat meneruskan nama file dengan kutipan ganda atau tidak ada kutipan dan sama untuk jalur absolut.
* `az postgres flexible-server migration check-name-availability`Menambahkan perintah untuk memeriksa apakah nama migrasi tersedia.
* `az postgres flexible-server migration update`Tambahkan `--start-data-migration` ke penjadwalan ulang migrasi untuk memulai sekarang.
* Memperbarui daftar-skus, membuat pengaturan lokasi perintah dan perintah replika

### <a name="role"></a>Peran

* `az ad sp create-for-rbac`: Terdepresiasi `--sdk-auth`

### <a name="security"></a>Keamanan

* Menambahkan perintah `az security setting update`

### <a name="storage"></a>Penyimpanan

* Perbaiki #19279: Tambahkan klarifikasi untuk nama sistem file yang juga berarti nama kontainer.
* Perbaiki #19059: Perbaiki tautan dokumen ke titik ke situs web dokumen publik
* `az storage account hns-migration start/stop`: Dukungan memigrasikan akun penyimpanan untuk mengaktifkan ruang nama hierarkis
* `az storage container-rm create/update`: Tambahkan `--root-squash` ke dukungan memungkinkan nfsv3 root squash atau semua squash
* Perbaiki #17858: `az storage blob upload`: membuat --name optional
* `az storage account create/update`: Tambahkan parameter akses jaringan --publik
* `az storage container immutability-policy create`: Tambahkan --allow-protected-append-writes-all/--w-all parameter
* `az storage container legal-hold set`: Tambahkan --allow-protected-append-writes-all/--w-all parameter
* `az storage account create/update`: Aktifkan immutability tingkat akun

### <a name="synapse"></a>Synapse

* [BREAKING CHANGE] `az synapse sql/pool audit-policy update`: Tambahkan parameter `blob-storage-target-state`, `log-analytics-target-state`( `event-hub-target-state` setidaknya pilih salah satu dari 3 paras ini)
* `az synapse integration-runtime`: Dukungan mulai/hentikan integrasi-runtime
* `az synapse trigger`: Tambahkan az synapse trigger wait
* `az synapse trigger-run`: Tambahkan az synapse trigger-run cancel
* `az synapse integration-runtime`Perintah deprecate `create` dan akan mengarahkan ke `managed create` atau `self-hosted create` perintah
* `az synapse dataset/pipeline/linked-service/trigger`: Perintah usang `set` dan akan mengarahkan ke `update` perintah
* `az synapse workspace-package`: Dukungan paket ruang kerja CRUD
* `az synapse spark pool update`: Dukungan tambahkan atau hapus paket tertentu
* `az synapse workspace create/update`: Tambahkan argumen untuk mendukung konfigurasi repositori ruang kerja sinapsis
* `az synapse spark-job-definition`: Dukungan memicu definisi pekerjaan CRUD

## <a name="september-09-2021"></a>09 September 2021

Versi 2.28.1

### <a name="arm"></a>ARM

Hotfix: Fix #19468: pip installs azure-cli 2.0.73 karena ketergantungan pada paket usang `jsmin`

## <a name="september-07-2021"></a>Tanggal 07 September 2021

Versi 2.28.0

### <a name="acr"></a>ACR

* `az acr create/update`: Menambahkan dukungan untuk menonaktifkan ekspor melalui `--allow-exports`
* `az acr`: Bump core api-version ke `2021-06-01-preview` dari `2020-11-01-preview`. agent_pool, tugas dan menjalankan operasi tidak berubah dari `2019-06-01-preview`
* `az acr task credential`: Memperbaiki masalah di mana kredensial tugas tidak digunakan
* `az acr task logs`: Perbaiki AttributeError saat menanyakan log tugas

### <a name="acs"></a>ACS

* [BREAKING CHANGE] `az aks nodepool update`: Perubahan menolak kemampuan untuk menggunakan max-surge dengan node-image-only

### <a name="aks"></a>AKS

* `az aks install-cli`: Tambahkan dukungan untuk rilis kubelogin darwin/arm64
* Memperbaiki parameter yang salah dilewati untuk opsi `--assign-kubelet-identity` dalam aks membuat sub-perintah
* Memutakhirkan versi api ke `2021-07-01` modul ACS
* `az aks create/update`: Tambahkan dukungan untuk fitur fqdn publik cluster pribadi
* Kembali PR #18825: `az aks create/update`: Tambahkan parameter `--auto-upgrade-channel` untuk mendukung peningkatan otomatis (dengan perbaikan)
* `aks create/aks nodepool add`: Tambahkan parameter ` --os-sku` untuk mendukung memilih OS host kontainer yang mendasarinya

### <a name="app-config"></a>Konfigurasi Aplikasi

* `appconfig kv import/export`: Menambahkan validasi titik akhir selama impor dan ekspor

### <a name="app-service"></a>App Service

* `az webapp config storage-account list/add/update/delete`: Hapus bendera pratinjau
* Perbaiki #18497: `functionapp identity show`: Perbaiki crash saat nama functionapp tidak mereferensikan functionapp yang ada
* `az webapp config set`: Tambahkan contoh bantuan tambahan untuk pengguna powershell
* Perbaiki #17818: `az functionapp update`: Tambahkan validasi instans untuk memperbarui functionapp
* `az webapp config hostname add`: Memperbaiki masalah yang disebabkan oleh AttributeError
* `az webapp config hostname add`: Memperbaiki masalah yang disebabkan oleh AttributeError
* Perbaiki #16470: `az staticwebapp secrets`: Tambahkan perintah untuk mengelola rahasia penyebaran
* `az webapp deployment source config-local-git`: Perbaiki masalah yang disebabkan oleh AttributeError saat opsi slot ditentukan
* `az webapp deleted restore` : Perbaiki masalah bahwa objek 'WebAppsOperations' tidak memiliki atribut 'restore_from_deleted_app'
* `az webapp up`Menambahkan kemampuan untuk menyebarkan Linux dan Windows webapps ke grup sumber daya yang sama
* `az webapp up`: Menambahkan dukungan untuk menerapkan ke Lingkungan Layanan Aplikasi
* Perbaiki #19098: `az webapp deployment slot auto-swap `: Perbaiki kesalahan AttributeError untuk parameter `--slot --disable`

### <a name="arm"></a>ARM

* `az feature registration`: Tambahkan api pendaftaran fitur az
* `az tag create`: Tambahkan catatan untuk menangani tag yang ada dalam bantuan
* `az ts create`: Memperbaiki masalah di mana membuat spesifikasi template dengan penyebaran batin yang mereferensikan template umum gagal

### <a name="cdn"></a>CDN

* `az cdn endpoint create`: Memperbaiki kegagalan pembuatan titik akhir dengan `--content-types-to-compress`

### <a name="compute"></a>Compute

* `az ssh vm`: Meningkatkan kesalahan untuk identitas terkelola dan Cloud Shell
* Memutakhirkan versi api untuk VM dan VMSS dari `2021-03-01` ke `2021-04-01`
* `az vmss create/update`: Dukungan spot mengembalikan kebijakan ke set skala VM
* Menambahkan contoh baru untuk membuat disk dari galeri gambar berbagi
* `az vm image list/list-offers/list-skus/list-publishers/show`: Tambahkan parameter `--edge-zone` baru untuk mendukung kueri gambar di bawah zona tepi
* Memperbaiki masalah yang disebabkan oleh kurangnya `os_type` saat membuat VM dari id galeri bersama
* Memperbarui dokumen galeri gambar bersama
* `az capacity reservation`: Menambahkan perintah baru untuk mengelola reservasi kapasitas
* `az capacity reservation group`: Menambahkan perintah baru untuk mengelola grup reservasi kapasitas
* `az vm create/update`: Tambahkan parameter `--capacity-reservation-group` baru untuk mendukung asosiasi ke reservasi kapasitas
* `az vmss create/update`: Tambahkan parameter `--capacity-reservation-group` baru untuk mendukung asosiasi ke reservasi kapasitas
* `az vmss create`: Mendukung pembuatan VMSS dari gambar galeri bersama

### <a name="iot"></a>IoT

* `az iot hub/dps certificate update/create`: Tambahkan `--verified` argumen untuk menandai sertifikat sebagai diverifikasi tanpa aliran proof-of-possession
* `az iot hub create/update`: Tambahkan `--disable-local-auth`, `--disable-device-sas`, dan `--disable-module-sas` argumen untuk mengkonfigurasi metode otentikasi kunci SAS yang diterima.

### <a name="key-vault"></a>Key Vault

* `az keyvault private-endpoint-connection list`: Daftar dukungan koneksi endpoint pribadi MHSM
* `az keyvault set-policy`: `--key-permissions` tambahkan opsi baru `release`

### <a name="network"></a>Jaringan

* Memperbaiki kesalahan contoh pembuatan aturan NSG
* Tambahkan grup `az network custom-ip prefix`perintah baru.
* `az network public-ip`: Tambahkan parameter `--ip-address`.
* `az network public-ip prefix create`: Tambahkan parameter `--custom-ip-prefix-name`.
* `az network dns record-set {record-type} add-record`: Dukungan idempotent
* PrivateLink mendukung `Microsoft.Purview/accounts` 2021-07-01
* `az network bastion ssh`: terhubung ke mesin Virtual melalui ssh menggunakan Bastion Tunneling.
* `az network bastion rdp`: terhubung ke mesin Virtual melalui RDP asli menggunakan Bastion Tunneling.
* `az network bastion tunnel`: terhubung ke mesin virtual menggunakan Bastion Tunneling.

### <a name="packaging"></a>Pengemasan

* Menggunakan Python 3.9 dalam rumus Homebrew
* Saat diinstal dengan RPM, jalankan python3.6 jika tersedia
* Tambahkan dukungan Ubuntu 21.04 Hirsute Hippo
* Menambahkan dukungan Debian 11 Bullseye
* Drop Ubuntu 20.10 Groovy Gorilla dukungan

### <a name="powerbi"></a>PowerBI

* Tambahkan penyedia tautan pribadi Microsoft.PowerBI/privateLinkServicesForPowerBI

### <a name="rdbms"></a>RDBMS

* [BREAKING CHANGE] `az postgres flexible-server migration`: Ganti nama `--migration-id` menjadi `--migration-name`
* [BREAKING CHANGE] `az mysql flexible-server create/update`: `--high-availability` parameter yang tersedia diubah dari 'Diaktifkan' menjadi 'ZoneRedundant' dan 'SameZone'.
* Memperbaiki masalah pembaruan jendela pemeliharaan dengan MySQL dan Ubah parameter restart agar tidak sensitif terhadap kasus
* `az mysql flexible-server restore` memungkinkan perubahan opsi jaringan dari jaringan pribadi ke jaringan publik dan sebaliknya.
* `az mysql flexible-server replica create`: Tambahkan `zone` parameter.

### <a name="role"></a>Peran

* `az role assignment create``ForeignGroup` Dukungan untuk`--assignee-principal-type`
* `az role assignment create`: Jangan memanggil api Graph jika `--assignee-principal-type` disediakan

### <a name="sql"></a>SQL

* `az sql mi update`: Tambahkan parameter --subnet dan --vnet-name untuk mendukung pembaruan subnet silang SLO
* Memperbaiki perubahan nama enum di sdk Python track2

### <a name="storage"></a>Penyimpanan

* Perbaiki #10765: Perbaiki pesan kesalahan saat kunci akun salah padding

### <a name="synapse"></a>Synapse

* [MELANGGAR PERUBAHAN] Mengganti nama `az synapse workspace key update` dan `az synapse workspace key activate` menghapus `--is-active`
* Optimalkan argumen pekerjaan pemicu
* `az synapse`: Tambahkan fitur titik akhir pribadi yang dikelola.
* Kolam spark menghapus persyaratan pustaka

## <a name="august-23-2021"></a>Tanggal 23 Agustus 2021

Versi 2.27.2

### <a name="cosmos-db"></a>Cosmos DB

* Hotfix: `az cosmosdb restore`: Perbaiki perintah pemulihan untuk akun yang dihapus

## <a name="august-17-2021"></a>17 Agustus 2021

Versi 2.27.1

### <a name="arm"></a>ARM

* Hotfix: Perbaiki #19124: `az deployment what-if`: Tangani jenis perubahan yang tidak didukung dan tidak ada efek

### <a name="batch"></a>Batch

Upgrade batch data-plane ke [azure-batch 11.0.0](https://pypi.org/project/azure-batch/) Upgrade batch management-plane to [azure-batch-mgmt 16.0.0](https://pypi.org/project/azure-mgmt-batch/16.0.0/)
`az batch location`: Tambahkan `list-skus` perintah ke daftar SKU yang tersedia di lokasi `az batch account`: Tambahkan `outbound-endpoints` perintah untuk daftar dependensi jaringan keluar

## <a name="august-03-2021"></a>Tanggal 03 Agustus 2021

Versi 2.27.0

### <a name="acr"></a>ACR

* [BREAKING CHANGE] `az acr connected-registry install info`: Tambahkan parameter `--parent-protocol`baru yang diperlukan.
* [BREAKING CHANGE] `az acr connected-registry install renew-credentials`: Tambahkan parameter `--parent-protocol`baru yang diperlukan.
* `az acr import`: Mendukung parameter baru `--no-wait`
* Memperbaiki masalah kompatibilitas SDK Python saat memigrasikan Track 2
* `az acr build`: Membuat file .dockerignore termasuk direktori dengan `!`

### <a name="aks"></a>AKS

* `az aks check-acr`: Memperbaiki masalah mengurai versi minor klien tertentu

### <a name="appconfig"></a>Konfigurasi Aplikasi

* [BREAKING CHANGE] `appconfig feature set`: Mengatur nilai parameter `--description` ke string kosong jika tidak ditentukan
* [BREAKING CHANGE] `az appconfig feature`: Dukungan namespacing untuk bendera fitur dan mengubah bidang output
* `az appconfig create`: Menambahkan dukungan tag saat membuat sumber daya

### <a name="app-service"></a>App Service

* `az webapp config set`: Tambahkan dukungan untuk VNet Route Semua properti.
* `az webapp vnet-integration add`Default ke VNet Route All. Perbolehkan integrasi langganan silang.
* `az appservice ase create`Dukungan untuk redundansi Eksternal dan Zona ASEv3
* `az webapp hybrid-connection add`: Meningkatkan pesan bantuan/kesalahan dan membuka blokir Linux
* `az webapp config access-restriction remove`: Perbaiki masalah #18947 menghapus aturan endpoint layanan
* : Perbaiki #17424: `az appservice plan show`: Berikan status keluar yang benar

### <a name="arm"></a>ARM

* `az what-if`: Perbaiki pemformatan output
* `az bicep uninstall`: Tambahkan perintah baru untuk menghapus bisep
* `az bicep build`: Memperbaiki masalah di mana berjalan dengan --stdout tidak mencetak output apapun
* `az provider register`: Tambahkan informasi terdepresiasi untuk `--accept-term`
* `az lock create/delete`: Tambahkan contoh untuk mengoperasikan berbagai tingkat kunci
* `az deployment group/sub/mg/tenant create`: Tambahkan parameter --what-if untuk meminta What-If dengan perintah pembuatan penyebaran.
* `az deployment group/sub/mg/tenant create`: Tambahkan parameter --proceed-if-no-change untuk melewatkan konfirmasi saat --confirm-with-what-if diatur dan tidak ada perubahan dalam hasil What-If.
* Bump api-version dari 2020-10-01 hingga 2021-04-01
* `az ts create`: Membuat berkas bisep dukungan parameter `--template-file`
* `az resource create`: Tambahkan contoh untuk membuat ekstensi situs ke aplikasi web
* `az ts export`: Perbaiki masalah bahwa spesifikasi templat ekspor tanpa templat terkait gagal

### <a name="backup"></a>Cadangan

* `az backup vault`: Tambahkan dukungan untuk Kunci Terkelola Pelanggan (CMK)
* `az backup restore restore-disks`: Tambahkan penggunaan MSI di IaaS VM Restore

### <a name="cdn"></a>CDN

* `az cdn endpoint rule`: Tambahkan dukungan tindakan OriginGroupOverride

### <a name="compute"></a>Compute

* `az sig image-version create`: Mendukung pencampuran disk, snapshot, dan vhd
* `az vmss update`: Upgrade versi paket untuk memperbaiki masalah securityProfile
* `az vm boot-diagnostics get-boot-log`: Perbaiki crash saat mendapatkan log diagnostik boot
* `az vm list-skus`: Perbaiki masalah yang tidak dapat menanyakan SKU yang dengan sebagian zona yang tersedia
* `az vm auto-shutdown`: Perbaiki masalah yang `--webhook` diperlukan saat `--email` disahkan
* `az vm create`: Dukungan membuat VM dari gambar galeri bersama
* `az vm secret add`: Tambahkan catatan untuk menggunakan ekstensi Azure Key Vault VM sebagai gantinya dalam bantuan

### <a name="container"></a>Kontainer

* `az container exec`: Memperbaiki dan meningkatkan pengalaman terminal

### <a name="databoxedge"></a>DataBoxEdge

* Memigrasikan databoxedge ke track2 SDK

### <a name="dms"></a>DMS

* `az dms project create/az dms project task create`Hapus proyek /tugas MySQL untuk migrasi online karena tidak lagi didukung.

### <a name="iot"></a>IoT

* `az iot hub create/update`: Tambahkan pemeriksaan untuk mencegah parameter identitas unggah file yang buruk saat hub tidak memiliki identitas
* `az iot hub create/update`: Menambahkan `--fileupload-notification-lock-duration` parameter
* `az iot hub create/update`: Parameter terdepresiasi `fileupload-storage-container-uri`
* `az iot dps/hub certificate create`Sertifikat sekarang akan selalu diunggah dalam pengkodean base64.

### <a name="key-vault"></a>Key Vault

* [MELANGGAR PERUBAHAN] Fix #13752: az keyvault create not idempotent. Membuat keyvault yang ada akan gagal.
* Perbaiki # 6372: output tabel untuk rahasia tidak benar

### <a name="maps"></a>Maps

* `az maps creator create`: Pembuat peta dukungan membuat dikelola
* `az maps creator update`: Pembaruan pembuat peta dukungan dikelola
* `az maps creator list`: Daftar pembuat peta dukungan dikelola
* `az maps creator show`: Dukungan peta pembuat menunjukkan dikelola
* `az maps creator delete`: Dukungan peta pembuat menghapus dikelola

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles volume pool-change`: Memperbarui deskripsi bantuan untuk perubahan kolam renang

### <a name="network"></a>Jaringan

* `az network application-gateway create`: Tambahkan `--ssl-certificate-name` argumen
* Link pribadi tambahkan penyedia Microsoft.ServiceBus/namespaces
* `az network application-gateway waf-policy custom-rule match-condition add`: Tambahkan contoh
* `az network express-route port link update`: Tambahkan `--macsec-sci-state` argumen.
* Link pribadi tambahkan Microsoft.Web/hostingMena
* `az network lb frontend-ip update`: Dukungan lintas penyewa untuk argumen `--gateway-lb`.
* `az network nic ip-config update`: Dukungan lintas penyewa untuk argumen `--gateway-lb`.
* Link pribadi tambahkan penyedia Microsoft.StorageSync/storageSyncServices
* Link pribadi tambahkan penyedia Microsoft.Media/mediaservices
* Link pribadi tambahkan penyedia Microsoft.Batch/batchAccounts

### <a name="packaging"></a>Pengemasan

* Menambahkan lisensi ke semua paket Python
* Menambahkan Dukungan Proxy SOCKS

### <a name="policyinsights"></a>PolicyInsights

* Bermigrasi ke track 2 SDK

### <a name="rdbms"></a>RDBMS

* PostgreSQL, migrasi MySQL ke GA API

### <a name="redis"></a>Redis

* `az redis create\update`: Tambahkan parameter baru `--redis-version`

### <a name="sql"></a>SQL

* Memperbarui Microsoft.Sql untuk melacak2 SDK
* `az sql server outbound-firewall-rule create`: Azure CLI Commands for Outbound Firewall Rules

### <a name="storage"></a>Penyimpanan

* Perbaiki #18352: `az storage fs file list --exclude-dir` istirahat dengan `--show-next-marker`
* `az storage fs generate-sas`Dukungan menghasilkan token sas untuk sistem file di akun ADLS Gen2
* `az storage account blob-service-properties`: Mendukung kebijakan pelacakan akses terakhir
* `storage container-rm migrate-vlw`: Worm tingkat Versi Dukungan (VLW)
* `az storage copy` menambahkan opsi baru `--cap-mbps`

### <a name="synapse"></a>Synapse

* `synapse workspace key update`: Memperbaiki masalah yang memperbarui kegagalan kunci ruang kerja karena parameter `--is-active-cmk` hilang
* Reimport kegagalan buku catatan

## <a name="july-14-2021"></a>14 Juli 2021

Versi 2.26.1

### <a name="acr"></a>ACR

* Hotfix: `az acr build\connected-registry\pack\run\scope-map`: Perbaiki bug kompatibilitas yang disebabkan oleh peningkatan SDK

### <a name="aks"></a>AKS

* Hotfix: `az aks create`: Perbaiki masalah yang `assign-kubelet-identity` tidak dapat dilakukan opsi

### <a name="storage"></a>Penyimpanan

* Hotfix: Memperbaiki masalah yang disebabkan oleh peningkatan JWT.
* Hotfix: `az storage fs directory download`: Perbaiki masalah untuk `--sas-token` menghasilkan url sas yang valid
* Hotfix: `az storage blob copy start`: Perbaiki masalah dalam salinan dari akun yang berbeda

## <a name="july-06-2021"></a>Juli 06, 2021

Versi 2.26.0

### <a name="aks"></a>AKS

* Migrasi modul ACS untuk melacak 2 SDK
* Pemutakhiran api-version ke 2021-05-01 untuk modul ACS
* Menambahkan dukungan UltraSSD
* Dukungan gunakan identitas kubelet kustom
* `az aks get-credentials`: Tambahkan cek untuk variabel lingkungan KUBECONFIG

### <a name="apim"></a>APIM

* Menambahkan parameter versi untuk impor apim api
* Memperbaiki bug pemutakhiran apim saat menentukan protokol
* `az apim create`: Memperbaiki `--enable-managed-identity` kegagalan sejati

### <a name="app-config"></a>Konfigurasi Aplikasi

* Berhenti menimpa jenis konten referensi KeyVault selama impor

### <a name="app-service"></a>App Service

* [BREAKING CHANGE] `az functionapp create`: Hapus dukungan untuk EOL Node 8 dan 10
* [BREAKING CHANGE] `az webapp deployment source config`: Hapus vsts-cd-manager
* [BREAKING CHANGE] `az functionapp deployment source config`: Hapus vsts-cd-manager
* `az webapp/functionapp config access-restriction add`: Mencegah aturan duplikat menggunakan titik akhir layanan.
* `az webapp/functionapp config access-restriction remove`: Hapus titik akhir layanan tidak sensitif terhadap kasus
* `az webapp config access-restrictions add`: Lewati validasi jika pengguna tidak memiliki akses untuk mendapatkan daftar tag layanan.
* Tambahkan dukungan untuk Konsumsi Linux dan tingkatkan cara berbagi konten dihasilkan.
* : Memperbaiki masalah di mana menambahkan integrasi VNET & koneksi Hybrid pada slot tidak berfungsi
* `az appservice domain create`: Perbaiki perjanjian domain yang benar
* `az webapp deployment github-actions add/remove`: perintah baru

### <a name="appconfiguration"></a>AppConfiguration

* Menambahkan dukungan untuk `disable_local_auth`

### <a name="arm"></a>ARM

* `az provider register`Membuat parameter `--accept-term` menjadi tidak diperlukan

### <a name="aro"></a>ARO

* `az aro create`: Tambahkan nilai cidr untuk pod/service
* Gagal jika sumber daya tidak ada pada delete

### <a name="azurestack"></a>Azurestack

* Dukungan Azure Stack Hub untuk AKS dan ACR telah ditambahkan dalam profil 2020-09-01-hybrid

### <a name="backup"></a>Cadangan

* `az backup container`: Perbaiki perbaikan pendaftaran kontainer Pendaftaran kontainer, SDK ditingkatkan menjadi 0.12.0, Pengujian Tetap dan Dijalankan Ulang
* Menambahkan Dukungan Arsip untuk Azure CLI

### <a name="billing"></a>Billing

* Migrasikan tagihan ke sdk2

### <a name="cognitive-services"></a>Cognitive Services

* `az cognitiveservices account`: Tambahkan perintah hapus daftar, hapus perlihatkan, pulihkan, bersihkan

### <a name="compute"></a>Compute

* `az sig create/update`: Tambahkan --izin untuk menentukan izin berbagi galeri.
* `az sig share`: Mengelola profil berbagi galeri.
* `az sig list-shared`: Daftar galeri bersama dengan id langganan atau id penyewa.
* `az sig show-shared`: Dapatkan galeri bersama.
* `az sig image-definition list-shared`: Daftar galeri bersama dengan id langganan atau id penyewa.
* `az sig image-definition show-shared`: Dapatkan gambar galeri bersama.
* `az sig image-version list-shared`: Daftar galeri bersama dengan id langganan atau id penyewa.
* `az sig image-version show-shared`: Dapatkan versi gambar galeri bersama.
* `az vmss create`: Dukungan NetworkApiVersion untuk Vmss dengan OrchestraionMode == Fleksibel
* Membuat sumber daya dependen zona tepi dukungan VM / VMSS
* Pembaruan dari CoreOS ke Flatcar
* Menambahkan petunjuk untuk menyarankan pengguna menggunakan IP publik standar saat membuat VM

### <a name="container-registry"></a>Container Registry

* Bermigrasi ke sdk track2

### <a name="cosmos-db"></a>Cosmos DB

* Tambahkan perintah pemulihan point-in-time ke cabang yang stabil.
* Menambahkan dukungan untuk memilih tipe skema penyimpanan analitis Cosmos DB

### <a name="hdinsight"></a>HDInsight

* `az hdinsight create`: Hapus pemberitahuan perubahan melanggar masuk untuk parameter `--workernode-size` dan `--headnode-size`.
* Tambahkan tiga cmdlet baru untuk mendukung fitur monitor azure baru:

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`: Parameter opsional ditambahkan bernama --administrator
* `az netappfiles pool create`: Parameter opsional ditambahkan --cool-access
* `az netappfiles volume create`: Parameter opsional ditambahkan bernama --chown-mode, --cool-access, --coolness-period, --coolness-period
* `az netappfiles volume backup restore-status`: Perintah ditambahkan untuk melihat status pemulihan cadangan

### <a name="network"></a>Jaringan

* `az network routeserver create`: Tambahkan `--public-ip-address` argumen.

### <a name="rdbms"></a>RDBMS

* Menambahkan parameter autogrow untuk MySQL dan menambahkan nama database ke output json saat dibuat

### <a name="resource"></a>Sumber daya

* Persetujuan/Pencacuhan Izin S2S pihak ketiga

### <a name="security"></a>Keamanan

* Menghapus pratinjau dari modul keamanan

### <a name="sql"></a>SQL

* Bump sdk version
* Memperbaiki buat server di SQL 0,28
* `az sql db ledger-digest-uploads`: Dukungan SQL Ledger
* Memperbaiki IdentityType untuk UMI
* `az sql db str-policy set/show`: Tambahkan Set dan Tampilkan ShortTermRetentionPolicy

### <a name="storage"></a>Penyimpanan

* Dukungan GA dijamin SMB
* `az storage account create``--enable-nfs-v3` Dukungan untuk mengatur protokol NFS 3.0
* Hapus lembut wadah dukungan

## <a name="june-15-2021"></a>Tanggal 15 Juni 2021

Versi 2.25.0

### <a name="acr"></a>ACR

* `az acr connected-registry`: Perbaikan bug kecil

### <a name="app-service"></a>App Service

* `az webapp deployment source config-local-git`: Perbaiki untuk mengatur SiteConfig

### <a name="arm"></a>ARM

* `az resource tag`: Memperbaiki masalah penandaan sumber daya dengan jenis sumber daya `Microsoft.Network/publicIPAddresses`
* `az policy assignment non-compliance-message`Grup perintah baru untuk pesan ketidakpatuhan tugas kebijakan
* `az policy assignment update`Perintah baru untuk memperbarui sebagian tugas kebijakan yang ada

### <a name="backup"></a>Cadangan

* Memigrasikan cadangan ke sdk2

### <a name="compute"></a>Compute

* Upgrade api-version untuk VM dan VMSS dari '2020-12-01' ke '2021-03-01'
* `az vm create`: Opsi hapus dukungan untuk NIC dan Disk untuk VM di Azure CLI
* Dukungan user_data untuk VM dan VM Scale Sets

### <a name="container"></a>Kontainer

* `az container exec`Decode menerima byte sebagai string utf-8

### <a name="eventgrid"></a>EventGrid

* Migrasi sdk track2

### <a name="hdinsight"></a>HDInsight

* Bermigrasi ke track2 Python SDK 7.0.0

### <a name="iot-hub"></a>Iot Hub

* Memperbaiki masalah ARM identitas yang ditetapkan pengguna saat dihapus

### <a name="key-vault"></a>Key Vault

* Perbaiki #11871: AKV10032: Kesalahan penerbit yang tidak valid untuk operasi di penyewa/langganan nondefault
* `az keyvault set-policy/delete-policy`: Dukungan --application-id
* `az keyvault recover`: Mendukung MHSM
* `az keyvault private-link-resource list`: Mendukung MHSM
* `az keyvault private-endpoint-connection`: Mendukung MHSM

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles volume backup status`Perintah ditambahkan untuk mendapatkan status cadangan untuk volume.
* `az netappfiles volume update`Parameter opsional yang ditambahkan bernama `--snapshot-policy-id` o menetapkan kebijakan snapshot ke volume.
* `az netappfiles volume backup create`Parameter opsional yang ditambahkan diberi `--use-existing-snapshot` nama untuk mencadangkan snapshot yang sudah ada secara manual.
* `az netappfiles volume backup update`Parameter opsional yang ditambahkan diberi `--use-existing-snapshot` nama untuk mencadangkan snapshot yang sudah ada secara manual. Label parameter opsional juga ditambahkan untuk menambahkan label ke cadangan.

### <a name="network"></a>Jaringan

* Penyedia `Microsoft.Sql/servers` dukungan di tautan Pribadi
* `az network private-link-resource list`: Dukungan `--type microsoft.keyvault/managedHSMs`
* `az network private-endpoint-connection`: Dukungan `--type microsoft.keyvault/managedHSMs`

### <a name="rdbms"></a>RDBMS

* Menambahkan perintah untuk tindakan Github
* `az postgres flexible-server migration`: Tambahkan fitur yang menghadap pelanggan untuk memigrasikan server postgres db dari platform Sterling ke Meru
* Parameter zona DNS pribadi ditambahkan untuk perintah pemulihan, validator ketersediaan tinggi
* Mengubah lokasi default server (masalah dilaporkan)

### <a name="role"></a>Peran

* [BREAKING CHANGE] `az ad sp create-for-rbac`: `--name` sekarang hanya digunakan sebagai `displayName` aplikasi. Hal ini tidak digunakan untuk menghasilkan `identifierUris` lagi. `name` dalam output sekarang sama `appID` dengan (`servicePrincipalNames`) dan usang.

### <a name="signalr"></a>SignalR

* `az signalr identity`: Menambahkan perintah terkait identitas terkelola
* `az signalr cors update`: Tambahkan perintah perbarui untuk cors

### <a name="storage"></a>Penyimpanan

* `az storage blob copy start`: Dukungan --tier dan --rehydrate-priority
* GA rilis file penyimpanan berbagi NFS dan SMB multichannel
* [MELANGGAR PERUBAHAN] `az storage account create`: Hapus `StorageFileDataSmbShareOwner` opsi untuk --default-share-permission
* `az storage blob list`: --nilai parameter delimiter sekarang akan dihormati

### <a name="synapse"></a>Synapse

* Pembaruan ke AZ Synapse mgmt 2.0.0
* Konversi konfigurasi percikan, yang menyebabkan kegagalan

### <a name="webapp"></a>Webapp

* Tambahkan ke `az webapp deploy` teks bantuan param

## <a name="june-02-2021"></a>Juni 02, 2021

Versi 2.24.2

### <a name="container"></a>Kontainer

* Hotfix: Fix #18276: `az container create` gagal dengan `AttributeError: 'ResourcesOperations' object has no attribute 'create_or_update'`

## <a name="june-01-2021"></a>Tanggal 01 Juni 2021

Versi 2.24.1

### <a name="app-service"></a>App Service

* Hotfix: Perbaiki #18266 - pengaturan aplikasi konfigurasi webapp yang menyebabkan semua nilai default menjadi "false"

### <a name="arm"></a>ARM
* Hotfix: Perbaiki masalah deserialization di formatter What-If templat ARM

### <a name="compute"></a>Compute
* Hotfix: Perbaiki masalah permintaan yang buruk saat membuat VMSS di Azure Stack

### <a name="iot"></a>IoT
* Hotfix: Memperbaiki masalah untuk menghapus identitas terakhir yang ditetapkan pengguna dari IoT Hub

## <a name="may-25-2021"></a>25 Mei 2021

Versi 2.24.0

### <a name="aks"></a>AKS

* `az aks check-acr`: Tambahkan nodelector linux untuk menghindari pod "canipull" yang akan dijadwalkan pada node windows
* Pembaruan SDK
* az aks create and update azure-rbac
* Menambahkan run-command cli

### <a name="app-config"></a>Konfigurasi Aplikasi

* Perbolehkan mengimpor nilai kunci dengan karakter unicode dari file

### <a name="app-service"></a>App Service

* [BREAKING CHANGE] `az webapp list-runtimes`: Tambahkan dukungan Dotnet6 dan perbarui runtime
* `webapp log tail`: Perbaiki #17987: logging.warning call dengan argumen 'akhir' yang tidak valid
* Perbaiki perintah pengaturan aplikasi pembaruan #16838- az cli selalu membuat pengaturan slot menjadi kenyataan
* `az appservice`: Menambahkan fungsi untuk mengambil pengguna github token akses pribadi
* az staticwebapp appsettings set issue #17792
* Fix #18033: az staticwebapp appsettings set of missing positional param app_settings
* Memperbaiki masalah dengan tanda tangan API yang berubah dengan pembaruan Track2
* Memperbaiki klien manajemen sumber daya dengan benar
* Tambahkan cara interaktif untuk mendapatkan token untuk staticwebapp
* Memperbaiki masalah di mana menetapkan dan menghapus identitas akan gagal dengan panggilan ke NoneType

### <a name="arm"></a>ARM

* Migrasi sumber daya ke track2 SDK
* `az ts`: Tambahkan dukungan file UiFormDefinition ke TemplateSpecs untuk GA (05/04)

### <a name="aro"></a>ARO

* Menambahkan rotasi kredensial klaster

### <a name="compute"></a>Compute

* `az sshkey create`: Simpan kunci pribadi ke sistem file lokal

### <a name="cosmos-db"></a>Cosmos DB

* Membuat dan mengelola Definisi Peran dan Tugas Peran untuk menegakkan bidang data RBAC pada akun SQL Cosmos DB

### <a name="devtestlabs"></a>DevTestLabs

* `az labs create environment`: Memperbaiki kesalahan membuat lingkungan dari templat ARM

### <a name="hdinsight"></a>HDInsight

* [BREAKING CHANGE] `az hdinsight create`: Gunakan mendapatkan api sku default untuk mengatur ukuran workernode dan headnode jika pelanggan tidak menyediakan.

### <a name="iot"></a>IoT

* `az iot hub create`Dukungan menetapkan identitas dan menetapkan peran untuk identitas yang dikelola sistem.
* `az iot hub update`Parameter baru `--file-upload-storage-identity` untuk memungkinkan upload file terotentikasi identitas terkelola.
* `az iot hub identity assign`Perintah baru untuk menetapkan identitas terkelola pengguna/sistem ke IoT Hub.
* `az iot hub identity show`Perintah baru untuk menunjukkan properti identitas IoT Hub.
* `az iot hub identity show`Perintah baru untuk memperbarui jenis identitas IoT Hub.
* `az iot hub identity remove`Perintah baru untuk menghapus identitas terkelola yang ditetapkan pengguna/sistem dari IoT Hub.
* `az iot hub routing-endpoint create``--identity` Parameter baru memungkinkan memilih identitas yang ditetapkan pengguna / sistem untuk titik akhir perutean.
* `az iot hub route create`: Tipe sumber perutean baru `DeviceConnectionStateEvents`

### <a name="kusto"></a>Kusto

* Memperbarui ringkasan panjang grup perintah

### <a name="network"></a>Jaringan

* Bump api versi dari '2020-11-01' ke '2021-02-01'
* Grup perintah baru `az network lb address-pool tunnel-interface`
* `az network lb frontend-ip update`: Parameter baru `--gateway-lb`
* `az network nic ip-config update`: Parameter baru `--gateway-lb`
* `az network rule create/update`: Parameter baru `--backend-pools-name`
* `az network vnet-gateway create`: Tambahkan paramter baru `--nat-rule`
* Menambahkan grup cmd baru `az network vnet-gateway nat-rule`
* `az network vpn-conncetion create`: Tambahkan paramter `--ingress-nat-rule` baru dan `--egress-nat-rule`
* `az network vnet create`: Tambahkan parameter baru `--flowtimeout`

### <a name="packaging"></a>Pengemasan

* Mendukung Python 3.9

### <a name="rdbms"></a>RDBMS

* Mengubah logika IOPS untuk MySQL
* Mencegah migrasi zona DNS pribadi2 melanggar modul rDBMS

### <a name="service-fabric"></a>Service Fabric

* [MELANGGAR PERUBAHAN] `az sf cluster certificate`: Hapus semua perintah di bawah grup ini. Silakan ikuti petunjuk di [Tambahkan sertifikat sekunder menggunakan Azure Resource Manager](/azure/service-fabric/service-fabric-cluster-security-update-certs-azure#add-a-secondary-certificate-using-azure-resource-manager) untuk menambahkan /menghapus sertifikat cluster.
* [BREAKING CHANGE] `az sf managed-service update`: Hapus parameter usang --drop-source-replica-on-move.
* [BREAKING CHANGE] `az sf managed-service create`: Hapus parameter usang --service-dns-name, --drop-source-replica-on-move dan -instance-close-delay-duration.
* [BREAKING CHANGE] `az sf cluster`: Ganti nama parameter --vault-resource-group menjadi --vault-rg.
* `az sf managed-cluster and sf managed-node-type`: Mengatur grup sebagai tidak mempratinjau
* Update paket azure-mgmt-servicefabricmanagedclusters ke versi terbaru 1.0.0 yang menggunakan 2021-05-01 GA api version.
* `az sf managed-cluster create`: Tambahkan parameter --upgrade-mode, --upgrade-cadence dan --code-version.
* `az sf managed-node-type`: Tambahkan parameter --data-disk-type, --is-stateless dan --multiple-placement-groups.

### <a name="sql"></a>SQL

* `az sql server create`: Tambahkan spasi untuk membagi kata-kata yang dikocatenated dalam pesan bantuan argumen --assign-identity.
* `az sql server update`: Tambahkan spasi untuk membagi kata-kata yang dikocatenated dalam pesan bantuan argumen - assign_identity.

### <a name="storage"></a>Penyimpanan

* [BREAKING CHANGE] `az storage share-rm delete`: Meningkatkan kesalahan ketika ada snapshot untuk berbagi file target dan menambahkan `--include` untuk menentukan menghapus berbagi file target dan snapshot-nya
* `az storage blob generate-sas`: Tambahkan spasi untuk membagi kata-kata yang dikocatenated dalam pesan bantuan argumen --cache-control, --content-disposition, --content-encoding, --content-language dan --content-type.
* `az storage blob url`: Tambahkan spasi untuk membagi kata-kata yang dikocatenated dalam pesan bantuan argumen --snapshot.
* `az storage container generate-sas`: Tambahkan spasi untuk membagi kata-kata yang dikocatenated dalam pesan bantuan argumen --cache-control, --content-disposition, --content-encoding, --content-language dan --content-type.
* Pemutakhiran versi API penyimpanan ke 2021-04-01
* Izin berbagi default dukungan
* Mendukung replikasi objek penyewa silang
* Inventaris gumpalan GA
* `az storage share-rm list`: Daftar dukungan dengan snapshot.

## <a name="may-06-2021"></a>Tanggal 06 Mei 2021

Versi 2.23.0

### <a name="acr"></a>ACR

* `az acr check-health`: Menambahkan dukungan untuk memverifikasi perutean dns ke titik akhir pribadi
* Perbaiki #17618: Perbarui penanganan tambahkan/perbarui kredensial untuk tugas yang dibuat menggunakan --auth-mode

### <a name="aks"></a>AKS

* `az aks update`: Tambahkan `--windows-admin-password` ke dukungan memperbarui kata sandi Windows
* `az aks update`: Dukungan pemutakhiran dari klaster SPN ke klaster MSI.
* `az aks create`: Menambahkan `--enable-encryption-at-host` parameter

### <a name="app-service"></a>App Service

* [MELANGGAR PERUBAHAN] Memperbarui SDK situs web ke versi terbaru (azure-mgmt-web==2.0.0) & Mengadopsi SDK track2
* [MELANGGAR PERUBAHAN] Ganti nama `az staticwebapp browse` menjadi `az staticwebapp show`
* Menambahkan opsi sku untuk `az staticwebapp create --sku`
* Menambahkan perintah `az staticwebapp update`
* `az webapp/functionapp config access-restriction add/remove`Dukungan untuk Tag Layanan, Header Http dan aturan multi-sumber.

### <a name="arm"></a>ARM

* `az bicep`: Ganti API datetime yang tidak tersedia di Python 3.6
* `az deployment group create`: Memperbaiki masalah kompatibilitas versi api untuk parameter `--template-specs`

### <a name="backup"></a>Cadangan

* `az backup vault create`: Menambahkan tag sebagai argumen opsional
* Membuat AFS mengonfigurasi aliran cadangan idempotent

### <a name="cdn"></a>CDN

* `az cdn endpoint rule add`: Perbaiki pembuatan aturan pengiriman untuk SKU non-Microsoft

### <a name="compute"></a>Compute

* Lokasi diperpanjang untuk Compute RP
* `az sig image-version create`Dukungan untuk membuat dari VHD
* `az vm create --count`: Mendukung konfigurasi vnet dan subnet
* `az vmss extension upgrade`: Memperbaiki bug
* Menambahkan pesan kesalahan untuk `vm identity assign`
* Penyimpanan zona-redundan (ZRS) disk yang dikelola
* `az disk create`: Peluncuran tepercaya
* `az disk create`: Hibernasi
* Memperbaiki masalah kompatibilitas versi API lama
* `az sig image version create`: Mendukung VHD cakram data

### <a name="feedback-reference"></a>Referensi umpan balik

* Jangan minify badan masalah umpan balik

### <a name="functionapp"></a>FunctionApp

* Memperbaiki masalah dengan zip deploy di mana waktu setempat disediakan tetapi UTC diharapkan
* Memperbarui tumpukan api json untuk menambahkan PowerShell di Linux di Functions

### <a name="hdinsight"></a>HDInsight

* Menambahkan PERUBAHAN BREAKING Masuk untuk menghapus nilai `--workernode-size` default dan  `--headnode-size`

### <a name="key-vault"></a>Key Vault

* [MELANGGAR PERUBAHAN] Mendukung fitur soft-delete untuk managed-HSM. `keyvault delete --hsm-name` akan melakukan soft delete pada MHSM.

### <a name="marketplace-ordering"></a>Pemesanan Pasar

* Grup perintah baru `az term` untuk menerima/menampilkan istilah

### <a name="misc"></a>Misc.

* Menentukan tema untuk Cloud Shell

### <a name="monitor"></a>Monitor

* Perintah baru `az monitor metrics list-namespaces`

### <a name="network"></a>Jaringan

* [BREAKING CHANGE] az network dns record-set a show: Properti `arecords` dalam output akan diubah menjadi `aRecords`.
* Perintah baru `az network express-route list-route-tables-summary`.
* Perintah baru `az network express-route peering get-stats`.
* Perintah baru `az network express-route peering connection list`.
* `az network lb create`: Tambahkan parameter baru `--edge-zone`
* `az network nic create`: Tambahkan parameter baru `--edge-zone`
* `az network private-endpoint create`: Tambahkan parameter baru `--edge-zone`
* `az network private-link-service create`: Tambahkan parameter baru `--edge-zone`
* `az network public-ip create`: Tambahkan parameter baru `--edge-zone`
* `az network public-ip prefix create`: Tambahkan parameter baru `--edge-zone`
* `az network vnet create`: Tambahkan parameter baru `--edge-zone`
* Perintah Baru `az network lb list-nic`
* `az network application-gateway show-backend-health`: mendukung argumen operasi probe.
* `az network vpn-connection list`: parameter `--vnet-gateway`dukungan .
* Perintah baru `az network vnet-gateway disconnect-vpn-connections`.
* Perintah baru `az network vnet-gateway vpn-client show-health`.
* Perintah baru `az network vnet-gateway vpn-client ipsec-policy show`.
* Perintah baru `az network vnet-gateway vpn-client ipsec-policy set`.
* Perintah baru `az network vnet-gateway packet-capture start`.
* Perintah baru `az network vnet-gateway packet-capture stop`.
* Perintah baru `az network vnet-gateway show-supported-devices`.
* Perintah baru `az network vpn-connection list-ike-sas`.
* Perintah baru `az network vpn-connection packet-capture start`.
* Perintah baru `az network vpn-connection packet-capture stop`.
* Perintah baru `az network vpn-connection show-device-config-script`.
* `az network private-link-resource list`: mendukung lebih banyak penyedia untuk `--type`

### <a name="packaging"></a>Pengemasan

* Bump python ke `3.8.9` dalam gambar docker
* Bump dibundel python ke `3.8.9` dalam MSI.

### <a name="rdbms"></a>RDBMS
* [BREAKING CHANGE] `az mysql flexible-server create`: `--storage-size` nilai default diubah dari 10 menjadi 32.
* `az postgres flexible-server create`: Tambahkan `--private-dns-zone` parameter untuk membuat server dengan akses pribadi.

### <a name="role"></a>Peran

* `az role assignment create/update`: Otomatis selesai `assignee_principal_type`

### <a name="sql"></a>SQL

* `az sql db create`: Tambahkan argumen --ha-replicas
* `az sql db replica create`: Tambahkan argumen --ha-replicas
* Perbolehkan nama kebijakan mw pendek untuk mi

### <a name="sql-vm"></a>SQL VM

* Jadikan SqlServerLicenseType sebagai opsional

### <a name="storage"></a>Penyimpanan

* Perbaiki #16272 & #16853: Perbaiki pesan kesalahan
* `az storage account create`: Tambahkan dukungan zona tepi
* Mendukung identitas yang ditetapkan pengguna untuk akun penyimpanan
* `az storage account create/update`: Mendukung kebijakan utama SAS&

### <a name="synapse"></a>Synapse

* `az synapse notebook create`: Membuat buku catatan

## <a name="april-19-2021"></a>Tanggal 19 April 2021

Versi 2.22.1

### <a name="arm"></a>ARM

* Hotfix: Perbaiki masalah yang dibangun bisep rusak di Python 3.6

### <a name="key-vault"></a>Key Vault

* Hotfix: GA untuk perintah dan parameter ralated HSM yang dikelola

## <a name="april-13-2021"></a>Tanggal 13 April 2021

Versi 2.22.0

### <a name="acr"></a>ACR

* [BREAKING CHANGE] `az acr connected-registry install info`: Ganti kunci ACR_REGISTRY_NAME, ACR_SYNC_TOKEN_NAME, ACR_SYNC_TOKEN_PASSWORD, ACR_PARENT_GATEWAY_ENDPOINT, dan ACR_PARENT_PROTOCOL dengan kunci string baru yang terhubung, ACR_REGISTRY_CONNECTION_STRING.
* [BREAKING CHANGE] `az acr connected-registry install renew-credentials`: Ganti kunci ACR_REGISTRY_NAME, ACR_SYNC_TOKEN_NAME, ACR_SYNC_TOKEN_PASSWORD, ACR_PARENT_GATEWAY_ENDPOINT, dan ACR_PARENT_PROTOCOL dengan kunci string baru yang terhubung, ACR_REGISTRY_CONNECTION_STRING.
* `az acr connected-registry create`Verifikasi sebelum pembuatan token dan sinkronisasi peta lingkup bahwa semua leluhur aktif.
* `az acr connected-registry create`: Tambahkan repositori dan izin gateway yang diperlukan untuk pembuatan ke semua nenek moyang registri terhubung baru jika diperlukan sebelum pembuatan registri yang terhubung.
* `az acr connected-registry delete`: Hapus izin gateway dari sumber daya yang dihapus dari semua peta lingkup sinkronisasi leluhurnya.
* `az acr connected-registry repo`Perintah baru untuk menambahkan izin repositori ke registri yang terhubung dan semua peta lingkup sinkronisasi leluhurnya, dan menghapus izin repositori dari registri yang terhubung dan semua peta lingkup sinkronisasi keturunannya

### <a name="aks"></a>AKS

* `az aks create`: Tambahkan dukungan untuk `--private-dns-zone` dan `--fqdn-subdomain` fitur

### <a name="app-config"></a>Konfigurasi Aplikasi

* Konfigurasikan lebar garis maks untuk parser YAML untuk menghentikan output pembungkus
* Memperbaiki bug dalam pratinjau cetak perintah pemulihan

### <a name="app-service"></a>App Service

* Perbaiki #17219: Perbaiki bug pengikat ssl
* Menghapus bendera pratinjau untuk Python 3.9 dalam membuat perintah aplikasi fungsi
* Bugfix: Tangani jika hanya profil publikasi tunggal yang dikembalikan
* Fix #16203: az webapp log tail mendukung webapps yang berjalan di Linix.

### <a name="arm"></a>ARM

* [BREAKING CHANGE] `az bicep build`: Ubah parameter `--files` menjadi `--file`
* [BREAKING CHANGE] `az bicep decompile`: Ubah parameter `--files` menjadi `--file`
* Perbaiki #17379: hasil pemasangan otomatis bisep dalam output json yang tidak valid dari penyebaran
* `az bicep build`: Menambahkan parameter `--outdir` untuk menentukan direktori output
* `az bicep build`: Menambahkan parameter `--outfile` untuk menentukan jalur berkas output
* Memperbaiki masalah di mana memeriksa upgrade versi untuk Bicep CLI melemparkan pengecualian jika batas tarif API GitHub dipukul
* `az policy exemption`Menambahkan perintah baru untuk mendukung pembebasan kebijakan

### <a name="backup"></a>Cadangan

* Perbaiki #14776: Perbaiki `--force` fungsionalitas parameter untuk `az backup vault delete` perintah
* Memperbaiki cadangan permintaan
* `az backup protectable-item list`: Tambahkan parameter opsional `--backup-management-type`
* Perbaiki pembuatan kebijakan dengan rgNamePrefix dan rgNameSuffix
* `az backup protectable-item list`: Tambahkan `--server-name` sebagai argumen opsional

### <a name="compute"></a>Compute

* `az ssh vm`: Mendukung VM SSH dengan Service Principal
* Menambahkan VMSS Rolling Upgrade opt
* Perintah baru: `vm install-patches`
* Kumpulan enkripsi disk: Tambahkan `--enable-auto-key-rotation`

### <a name="container"></a>Kontainer

* Perbaiki #16499: `az container create`: Memperbaiki penanganan nilai pengembalian dari network_profiles.create_or_update

### <a name="cosmos-db"></a>Cosmos DB

* Dukungan untuk identitas layanan terkelola & identitas default

### <a name="eventgrid"></a>EventGrid

* `az eventgrid system-topic create/update`: Tambahkan Dukungan MSI
* `az eventgrid [partner topic | system-topic] event-subscription`: Tambahkan dukungan untuk StorageQueueMessageTTL, AdvancedFilters, EnableAdvancedFilteringOnArrays
* `az eventgrid [partner topic | system-topic] event-subscription`: Menambahkan dukungan untuk atribut pengiriman
* `az eventgrid topic create`: Tambahkan dukungan untuk creating topic for azure or azurearc

### <a name="interactive"></a>Interaktif

* Perbaiki #16931: Perbaiki `KeyError``az interactive --update`

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`Parameter opsional yang ditambahkan bernama allow-local-ldap-users
* `az netappfiles volume create`Parameter opsional yang ditambahkan bernama ldap-enabled
* `az netappfiles volume backup status show`: Operasi ditambahkan
* Memperbarui tes cadangan

### <a name="network"></a>Jaringan

* `az network vnet-gateway`: `--vpn-auth-type` memungkinkan multi value

### <a name="packaging"></a>Pengemasan

* [MELANGGAR PERUBAHAN] RPM diinstal az sekarang menggunakan `python3` bukan kode `/usr/bin/python3`keras.

### <a name="rdbms"></a>RDBMS

* Mengizinkan akses pribadi server DB dari langganan yang berbeda
* Memodifikasi pembuatan server dengan jaringan pribadi, memperbaiki bug waktu pemulihan

### <a name="search"></a>Cari

* `az search service create`: Tambahkan opsi async (--no-wait).
* `az search service update`: Tambahkan opsi async (--no-wait).
* `az search shared-private-link-resource create`: Tambahkan opsi async (--no-wait).
* `az search shared-private-link-resource update`: Tambahkan opsi async (--no-wait).

### <a name="service-fabric"></a>Service Fabric

* Menambahkan perintah cli aplikasi terkelola

### <a name="storage"></a>Penyimpanan

* `az storage fs directory upload/download`: Mendukung upload direktori sistem file adls gen2&unduh
* `az storage fs file list`: Dukungan --show-next-marker
* `az storage share-rm`: Mendukung membuat/memperlihatkan/menghapus snapshot

### <a name="synapse"></a>Synapse

* [BREAKING CHANGE] `az synapse role assignment create`: Nama peran di versi lama tidak diperbolehkan, Sql Admin, Apache Spark Admin, Workspace Admin
* [BREAKING CHANGE] `az synapse role assignment create`: Ketika argumen --assignee tidak dapat secara unik menentukan objek utama, perintah akan meningkatkan kesalahan alih-alih menambahkan tugas peran untuk objek utama yang tidak pasti.
* `az synapse role scope list`: Daftar semua lingkup sinapsis mendukung.
* `az synapse role assignment create/list/delete`: Tambahkan argumen --scope/--item-type/--item untuk mendukung mengelola tugas peran berdasarkan ruang lingkup.
* `az synapse role assignment create/list/delete`: Tambahkan --assignee-object-id argument, itu akan memotong api Graph dan secara unik menentukan objek utama alih-alih menyimpulkan objek utama menggunakan argumen --assignee.

## <a name="march-23-2021"></a>Tanggal 23 Maret 2021

Versi 2.21.0

### <a name="acr"></a>ACR

* Output jejak `az acr login` untuk mendiagnosis diri potensi docker perintah latency
* Perbaiki # 17172: Ketika menjalankan pemeriksaan kesehatan di belakang proxy perusahaan
* `acr update`: Mendukung tarikan anonim
* Perbaiki #16700: Gunakan api "exists" untuk memeriksa keberadaan gumpalan penyimpanan

### <a name="aks"></a>AKS

* `aks update`: Tambahkan `--no-uptime-sla`
* Memperbaiki kesalahan identitas lintas-sub penetapan dan melampirkan kesalahan acr
* Menambahkan dukungan untuk ID awalan IP publik node

### <a name="apim"></a>APIM

* [BREAKING CHANGE] `apim backup`: `--storage-account-container` tidak mendukung multi-value.
* [BREAKING CHANGE] `apim restore`: `--storage-account-container` tidak mendukung multi-value.

### <a name="app-service"></a>App Service

* [MELANGGAR PERUBAHAN] Perbaiki #16087: `az webapp config ssl create`: atur `--name` parameter sesuai kebutuhan.
* Perbaiki #17053: `az webapp show` mengembalikan nilai null untuk properti SiteConfig
* Perbaiki #17207: `az webapp log config`: 'level' selalu default ke verbose

### <a name="arm"></a>ARM

* `az bicep build`: memperbaiki masalah di mana peringatan build tidak ditampilkan

### <a name="backup"></a>Cadangan

* Menambahkan `id_part` nama sub-sumber daya untuk diperbaiki `--ids`
* Perbaiki #17094: Dibuat suite uji terpisah untuk tes CRR
* `az backup protection check-vm`: Tambahkan `--vm` dan `--resource-group` sebagai params opsional

### <a name="cache"></a>Cache

* GA `az cache`

### <a name="cdn"></a>CDN

* `az afd rule create`: Perbaiki `--help` pesan

### <a name="compute"></a>Compute

* Memperbaiki bug pembaruan pengguna vm Windows
* Perbaiki #16585: `az vmss deallocate`: `--instance-ids` gagal
* `az vm create`Parameter baru `--platform-fault-domain` dalam mode FLEX VMSS
* `az vm create`: `--patch-mode` untuk Linux VM
* `az ssh vm`: Secara otomatis meluncurkan browser saat mendapatkan sertifikat gagal
* `az vm create`: Parameter baru `--count`
* `az vm create`: Peluncuran Terpercaya
* Fix #16037: az vm open-port accepts list of ports

### <a name="extension"></a>Ekstensi

* Menambahkan pesan yang dapat ditindaklanjuti saat ekstensi tidak kompatibel dengan inti CLI

### <a name="key-vault"></a>Key Vault

* `az keyvault role definition list``--custom-role-only` Dukungan untuk daftar hanya definisi peran kustom
* Mendukung definisi peran kustom keyvault
* Tambahkan `--no-wait` untuk perintah `az keyvault security-domain download` dan `--target-operation` untuk perintah `az keyvault security-domain wait`

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account backup show`: Operasi ditambahkan.
* `az netappfiles account backup delete`: Operasi ditambahkan.
* `az netappfiles account ad add`Parameter `--ldap-over-tls` ditambahkan.
* `az netappfiles account create`Parameter `--encryption` ditambahkan.
* `az netappfiles account update`Parameter `--encryption` ditambahkan.
* `az netappfiles volume create`Parameter `--encryption-key-source` ditambahkan.
* `az netappfiles volume create`Kebijakan ekspor default dihapus untuk nfsv4.1 dan parameter opsional ditambahkan untuk menyiapkan kebijakan ekspor untuk nfsv4.1: rule_index, unix_read_only, unix_read_write, cifs, allowed_clients

### <a name="network"></a>Jaringan

* `az network public-ip prefix create`: Dukungan `--zone 1 2 3`
* `az network lb frontend-ip create`: Dukungan `--zone 1 2 3`
* Versi Bump dari '2020-08-01' hingga '2020-11-01'
* `az network lb address-pool`Subnet dukungan saat membuat atau memperbarui kumpulan backend berbasis IP dari penyeimbang beban.

### <a name="rdbms"></a>RDBMS

* Menambahkan tes untuk pipa tim server fleksibel
* Migrasi SDK Python
* Menambahkan fitur membuat, menampilkan, dan menghapus database PostgreSQL
* Memperbarui Python SDK ke 8.1.0b2

### <a name="role"></a>Peran

* `az ad app permission list/grant`: Memperbaiki pesan kesalahan ketika tidak ada Kepala Layanan terkait untuk Aplikasi

### <a name="search"></a>Cari

* `az search`: GA

### <a name="service-fabric"></a>Service Fabric

* `az sf certificate`: perintah sertifikat cluster terdepresiasi.

### <a name="sql"></a>SQL

* Perintah Tambahkan Grup Kepercayaan Server

### <a name="storage"></a>Penyimpanan

* Perbaiki #16917: `az storage account generate-sas` gagal jika string koneksi disediakan
* Perbaiki #16979: `az storage container create` gagal saat menyediakan metadata kontainer penyimpanan

### <a name="upgrade"></a>Mutakhirkan

* Perbaiki #16952: Perbaiki ImportIrror setelah upgrade

### <a name="misc"></a>Misc.

* Perbolehkan mengonfigurasi tema

## <a name="march-02-2021"></a>Tanggal 02 Maret 2021

Versi 2.20.0

### <a name="aks"></a>AKS

* Menambahkan dukungan untuk SGX addon 'confcom'

### <a name="ams"></a>AMS

* Perbarui modul untuk menggunakan api Azure Media Services 2020.
* `az ams account encryption`Subkelompok baru untuk menampilkan atau mengatur enkripsi untuk akun layanan media
* `az ams account storage set-authentication`Perintah baru untuk mengatur autentikasi untuk akun penyimpanan yang terkait dengan akun layanan media
* `az ams account create (mi-system-assigned)`Parameter baru --mi-system-assigned untuk pembuatan akun untuk mengatur identitas terkelola akun media
* `az ams account mru set`Perintah ini tidak akan lagi berfungsi untuk Media Services akun yang dibuat dengan API versi 2020-05-01 atau versi lebih baru.
* `az ams live-event create (stretch-mode, key-frame-interval, transcrip-lang, use-static-hostname, custom hostname)`: Tambahkan opsi parameter baru ke perintah buat acara langsung
* `az ams live-event standby`Perintah baru untuk menempatkan acara langsung dalam mode siaga
* `az ams transform create (videoanalysismode, audioanalysis mode)`: Opsi parameter baru untuk mengubah buat

### <a name="app-service"></a>App Service

* `az webapp config ssl bind`: tangani jika webapp dan paket layanan aplikasi di rg yang berbeda. Juga referensi pembaruan teks
* Fix #8743: az webapp deploy
* Bugfix: Tambahkan generateRandomAppNames.json ke penyetelan
* `az functionapp create`: Tambahkan dukungan pratinjau untuk membuat aplikasi yang terisolasi dotnet.
* Perbaiki #12150: Dukungan untuk ID subnet dalam penambahan integrasi vnet
* `az functionapp create`: Hapus bendera pratinjau dari Node.js 14.

### <a name="arm"></a>ARM

* `az deployment group/sub/mg/tenant validate/create/what-if`: Menambahkan dukungan untuk file Bisep
* `az bicep install`: Perintah baru untuk menginstal Bicep CLI
* `az bicep upgrade`: Perintah baru untuk memutakhirkan Bicep CLI
* `az bicep build`: Perintah baru untuk membangun file Bisep
* `az bicep version`Perintah baru untuk memperlihatkan versi Bicep CLI yang diinstal saat ini
* `az bicep list-versions`: Perintah baru untuk menampilkan versi Bicep CLI yang tersedia
* `az managedapp definition update`: Menambahkan perintah baru untuk memperbarui definisi aplikasi terkelola

### <a name="backup"></a>Cadangan

* `az backup recoverypoint show-log-chain`: Tambahkan waktu mulai/akhir dalam keluaran tabel perlihatkan-log-chain
* BugFix: Aktifkan Pemulihan Lokasi Alternatif untuk item yang dilindungi SQL/SAPHANA

### <a name="cdn"></a>CDN

* Menambahkan dukungan cli untuk AFD SKU

### <a name="compute"></a>Compute

* `az vm (extension) image list`: Membuatnya lebih kuat
* `az vmss create`: Memperbaiki masalah tipe lisensi
* Pemutakhiran versi API ke 2020-12-01
* `az vm create`: tambahkan `--enable-hotpatching`

### <a name="cosmos-db"></a>Cosmos DB

* Upgrade ke versi 3.0.0 dan tambahkan dukungan untuk NetworkAclBypass + Update Mongo ServerVersion + kebijakan cadangan

### <a name="extension"></a>Ekstensi

* Konfigurasi dukungan url indeks ekstensi

### <a name="iot-central"></a>IoT Pusat

* `az iot central app`Alamat beberapa perbaikan S360
* `az iot central app update`: Hapus kebutuhan untuk memeriksa etag saat memperbarui aplikasi iotc yang ada.
* Ubah resourceType (IotApps) untuk berada dalam kasus unta.

### <a name="key-vault"></a>Key Vault

* [BREAKING CHANGE] `az keyvault role assignment/definition list`: `roleDefinitionName` harus `roleName` dalam output perintah
* [MELANGGAR PERUBAHAN] `id` perubahan menjadi `jobId`, `azureStorageBlobContainerUri` perubahan menjadi `folderUrl` dalam output perintah,`az keyvault backup/restore``az keyvault key restore`

### <a name="network"></a>Jaringan

* Versi Bump dari '2020-07-01' hingga '2020-08-01'
* `az network public-ip create`Dukungan '--zona 1 2 3' setelah '2020-08-01'
* `az network routeserver peering`: Ganti nama dengan `--vrouter-name``--routeserver`
* `az network express-route peering create`: Dukungan alamat ipv6
* `az network public-ip create`: Mengekspos argumen baru `--tier`

### <a name="openshift"></a>OpenShift

* Pembaruan peringatan deprecation az openshift

### <a name="search"></a>Cari

* `az search`: Perbaiki `--identity-type` panduan pembantu.

### <a name="sql"></a>SQL

* Update az sql mi examples
* `az sql db/elastic-pool create/update`: Menambahkan argumen konfigurasi pemeliharaan
* `az sql db replica create`: Tambahkan argumen tipe --sekunder

### <a name="storage"></a>Penyimpanan

* [BREAKING CHANGE] `az storage account file-service-properties`: Default untuk mengaktifkan kebijakan penghapusan retensi dengan hari retensi 7 di sisi server
* Perbaiki #16872: az storage blob now (2.19) memerlukan login bahkan jika koneksi-string disediakan
* Perbaiki #16959: az storage copy crashs: ValidationError: variabel lokal 'service' direferensikan sebelum penugasan
* Perbaiki #14054: Objek 'NoneType' tidak memiliki atribut '__nama__'
* Perbaiki #16679: `az storage blob download` gagal dengan "Izin ditolak" jika berkas tujuan adalah direktori
* Pemutakhiran versi api penyimpanan ke 2021-01-01
* Versi dukungan dalam kebijakan manajemen Lifecyle
* Mendukung manajemen akses kunci berbagi akun penyimpanan
* `az storage account network-rule`: Aturan akses sumber daya GA
* Mendukung enkripsi ganda untuk lingkup enkripsi
* `az storage account blob-service-properties update`: Dukungan --change-feed-retention-days
* Dukungan menulis ulang gumpalan yang ada

## <a name="february-10-2021"></a>Tanggal 10 Februari 2021

Versi 2.19.1

### <a name="key-vault"></a>Key Vault

* Hotfix: Paket `azure-keyvault-administration` dependensi disematkan ke 4.0.0b1

## <a name="february-09-2021"></a>Tanggal 09 Februari 2021

Versi 2.19.0

### <a name="acr"></a>ACR

* `az acr connected-registry install info`: Tambahkan kunci `ACR_SYNC_TOKEN_NAME` baru dengan nilai yang sama dengan `ACR_SYNC_TOKEN_USERNAME`. Sebuah peringatan bahwa yang terakhir akan usang ditampilkan.
* `az acr connected-registry install renew-credentials`: Tambahkan kunci `ACR_SYNC_TOKEN_NAME` baru dengan nilai yang sama dengan `ACR_SYNC_TOKEN_USERNAME`. Sebuah peringatan bahwa yang terakhir akan usang ditampilkan.

### <a name="aks"></a>AKS

* Menambahkan henti/mulai pemanruan terkelola
* `az aks check-acr`: Perbaiki pemeriksaan versi Kubernetes

### <a name="apim"></a>APIM

* GA grup perintah

### <a name="app-config"></a>Konfigurasi Aplikasi

* [BREAKING CHANGE] `az appconfig feature filter add`: Dukungan menambahkan objek JSON sebagai nilai parameter filter fitur

### <a name="app-service"></a>App Service

* `az appservice ase/plan`: Dukungan ASEv3
* Perbaiki #16026 dan #16118 for az appservice plan
* Perbaiki #16509: Tambahkan dukungan untuk preferensi os
* Meningkatkan perilaku appservice ase create-inbound-services untuk memungkinkan melewatkan layanan DNS dan mendukung DNS untuk ASEv2
* `az webapp up/az webapp create`: Memperbaiki kesalahan nonetype
* `az webapp up/create`: penanganan kesalahan nama aplikasi yang lebih baik dengan periode
* Fix #16681: `az webapp config ssl import`Memperbaiki bug yang menyebabkan kegagalan pada awan nasional

### <a name="arm"></a>ARM

* `az provider register`: Dukungan mendaftarkan kelompok manajemen

### <a name="backup"></a>Cadangan

* Menambahkan fungsionalitas CRR untuk IaaSVM dan perintah CRR lainnya
* `az backup protectable-item list`: Tambahkan tipe item yang dapat dilindungi sebagai argumen opsional

### <a name="botservice"></a>Layanan Bot

* `az bot create/update`: Tambahkan fitur `--cmk-key-url` Enkripsi dan `--encryption-off`
* `az bot update`: Ganti nama Encryption-OFF arg ke CMK-OFF dan memperbarui versi api

### <a name="compute"></a>Compute

* [BREAKING CHANGE] vmss create: Ganti nama nilai mode orkestrasi
* Grup perintah baru sshkey. Perbolehkan referensi sumber daya kunci SSH saat membuat VM
* `az disk create/update`: Tambahkan parameter `--enable-bursting` untuk mendukung pengisian disk

### <a name="extension"></a>Ekstensi

* Perintah perintah ekstensi dukungan cocok untuk penginstalan dinamis

### <a name="hdinsight"></a>HDInsight

* `az hdinsight create`: Tambahkan parameter `--enable-compute-isolation` baru untuk mendukung membuat cluster dengan fitur compute isolation.

### <a name="key-vault"></a>Key Vault

* `az keyvault key import`Parameter dukungan `--curve` untuk mengimpor kunci BYOK
* `az keyvault certificate download`: Perbaiki panggilan metode yang usang /dihapus
* `az keyvault create/update`: Hapus tag pratinjau untuk `--enable-rbac-authorization`

### <a name="monitor"></a>Monitor

* `az monitor metrics alert create`: Memperbaiki kesalahan 'sumber daya tidak ditemukan'

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`: Tambahkan parameter `--security-operators`.
* `az netappfiles volume create`: Tambahkan parameter `--smb-continuously-available`.
* `az netappfiles volume create`: Tambahkan parameter `--smb-encryption`.
* `az netappfiles`: Tidak lagi dalam mode pratinjau.

### <a name="network"></a>Jaringan

* [BREAKING CHANGE] `az network vrouter`: Bejat kelompok perintah ini, silakan gunakan `az network routeserver`.
* `az network routeserver`: Tambahkan grup perintah baru.
* `az network application-gateway create`: Menambahkan parameter `--ssl-profile-id`
* `az network application-gateway client-cert`: Mengelola sertifikat klien tepercaya dari gateway aplikasi
* `az network application-gateway ssl-profile`: Mengelola profil ssl gateway aplikasi
* Menambahkan dukungan untuk koneksi endpoint pribadi ke DigitalTwins

### <a name="profile"></a>Profil

* `az login`: Luncurkan browser di WSL 2

### <a name="rdbms"></a>RDBMS

* `az mysql flexible-server create --iops`Izinkan pengguna untuk memilih IOPS untuk SKU mereka.
* Perintah pemulihan Pemutakhiran Postgres untuk mendukung zona yang tersedia

### <a name="search"></a>Cari

* Upgrade to use the latest (8.0.0) azure-mgmt-search python sdk
* `az search create`: Menambahkan dukungan untuk pembuatan layanan pencarian dengan aturan IP, akses endpoint publik dan / atau msi
* `az search update`: Tambahkan dukungan untuk pembaruan layanan pencarian dengan aturan IP, akses endpoint publik, dan/atau msi
* `az search private-endpoint-connection`: Mengelola koneksi endpoint pribadi ke layanan pencarian
* `az search shared-private-link-resource`Mengelola sumber daya tautan pribadi bersama di layanan pencarian
* `az search private-link-resource`: Daftar sumber daya tautan pribadi yang tersedia di layanan pencarian

### <a name="security"></a>Keamanan

* Menambahkan perintah baru untuk `az security`

### <a name="sql"></a>SQL

* Menambahkan pertandingan hsm regex yang dikelola ke SQL
* Upgrade azure-mgmt-sql to 0.26.0
* `az sql mi create/update`: Menambahkan dukungan untuk konfigurasi pemeliharaan dalam operasi instans terkelola
* Perintah kebijakan audit DevOps server SQL dukungan

### <a name="storage"></a>Penyimpanan

* Perbaiki #16079: gumpalan publik memberikan kesalahan
* Referensi perutean ga Storage
* Perbaiki #9158: Tidak dapat menghasilkan kunci SAS yang berfungsi dari kebijakan
* Perbaiki #16489: Upgrade azcopy ke 10.8.0
* `az storage account blob-service-properties`: Mendukung versi layanan default
* Fix # 16519: azcopy diberi SAS yang lebih kuat dari yang dibutuhkan (telah menulis, hanya perlu dibaca)

### <a name="synapse"></a>Synapse

* `az synapse workspace create `: Tambahkan parameter `--key-identifier` untuk mendukung pembuatan ruang kerja menggunakan kunci yang dikelola pelanggan.
* `az synapse workspace key`: Tambahkan cmdlet CRUD untuk mendukung mengelola kunci di bawah ruang kerja sinapsis tertentu.
* `az synapse workspace managed-identity`: Tambahkan cmdlet untuk mendukung identitas terkelola CRUD ke pengaturan akses SQL.
* `az synapse workspace`: Tambahkan dukungan perlindungan eksfiltrasi data, tambahkan parameter `--allowed-tenant-ids`.

## <a name="january-19-2021"></a>Tanggal 19 Januari 2021

Versi 2.18.0

### <a name="acr"></a>ACR

* `az acr create / update`: Tambahkan `--allow-trusted-services`. Parameter ini menentukan apakah layanan azure tepercaya diizinkan untuk mengakses pendaftar terbatas jaringan. Default adalah untuk memungkinkan.

### <a name="aks"></a>AKS

* `az aks check-acr`: Tambahkan perintah check-acr baru

### <a name="app-service"></a>App Service

* Perbaiki #13907: `az webapp config ssl import`: Ubah perintah untuk juga mengimpor Sertifikat Layanan Aplikasi
* Perbaiki #16125: `az webapp ssh`: Jika menggunakan klien windows, buka browser ke tautan scm
* Fix #13291: `az webapp deployment slot swap`: Perintah harus mendukung melestarikan vnet.
* [MELANGGAR PERUBAHAN] Memperbaiki regresi di mana Anda tidak dapat menggunakan versi runtime dengan spasi dalam nama

### <a name="arm"></a>ARM

* `az deployment` : Tambahkan dukungan untuk `--query-string`
* `az ts`: Perbaikan penanganan kesalahan untuk `--template-file` tanpa `--version` dilarang

### <a name="backup"></a>Cadangan

* `az backup protection backup-now`: Mengatur periode retensi default menjadi 30 hari

### <a name="compute"></a>Compute

* Memperbaiki masalah tidak ada storage_profile
* Penanganan kesalahan token eksternal yang lebih baik
* Fix a vmss reimage issue
* `az vm/vmss extension set`: Parameter baru `--enable-auto-upgrade`

### <a name="container"></a>Kontainer

* `az container exec`Hapus cek eol untuk menghindari penutupan terminal bahkan sebelum dimulai di linux

### <a name="dms"></a>DMS

* `az dms project task create`Menambahkan parameter tipe tugas untuk membantu membedakan apakah skenario adalah migrasi online atau migrasi offline.
* `az dms project task cutover`Tambahkan perintah baru yang memungkinkan tugas dengan tipe tugas migrasi online untuk mengurangi dan mengakhiri migrasi.
* `az dms project create/az dms project task create`Aktifkan proyek/tugas MySQL dan PostgreSQL yang akan dibuat.

### <a name="iot"></a>IoT

* Menambahkan --tag ke IoT Hub membuat dan memperbarui

### <a name="monitor"></a>Monitor

* [BREAKING CHANGE] `az monitor log-analytics workspace data-export`: Hapus parameter yang sudah usang `--export-all-tables` dan memerlukan `--tables` parameter

### <a name="rdbms"></a>RDBMS

* Menghapus tag pratinjau untuk perintah admin kunci server dan iklan untuk Postgres dan MySql

### <a name="role"></a>Peran

* Perbaiki #11594: `az role assignment create`: Hanya menunjukkan nilai yang didukung untuk `--assignee-principal-type`

### <a name="storage"></a>Penyimpanan

* Perbaiki #16072: Upload file dengan ukuran besar
* Perbaiki #12291: `az storage blob generate-sas` tidak dikodekan dengan benar `--full-uri`
* Ga PITR dan properti layanan gumpalan di SRP

## <a name="january-04-2021"></a>Tanggal 04 Januari 2021

Versi 2.17.1

### <a name="rdbms"></a>RDBMS

* Hotfix: `az mysql create`Mengembalikan nama parameter yang salah 'serv_name' ke 'service_name'

## <a name="december-29-2020"></a>Tanggal 29 Desember 2020

Versi 2.17.0

### <a name="acr"></a>ACR

* Redundansi zona dukungan
* `az acr connected-registry`: Fitur baru untuk on-prem Azure Container Registry
* `az acr scope-map update`: --add dan --remove sudah usang, mereka diganti namanya menjadi --add-repo --remove-repo
* `az acr scope-map create/update`: Tambahkan dukungan untuk menangani tindakan Gateway.
* `az acr token create`: dukungan ditambahkan untuk tindakan gateway

### <a name="aks"></a>AKS

* Memperbaiki: menambahkan argumen yang dihapus oleh PR sebelumnya
* `az aks get-credentials`Klarifikasi dokumentasi untuk mendapatkan-kredensial

### <a name="app-service"></a>App Service

* Perbolehkan pelanggan membuat aplikasi fungsi Python 3.9
* Perbaiki #14583: az webapp up harus menghasilkan nama default jika nama tidak disediakan
* Memperbaiki: Penanganan kesalahan yang lebih baik saat mencoba membuat ASP duplikat di lokasi diff

### <a name="arm"></a>ARM

* `az ts`: Menambahkan dukungan untuk --tag
* `az ts`: Mendukung penghapusan satu versi
* `az provider register`: Tambahkan --accept-terms untuk mendaftarkan RPaaS
* Memperbaiki mengurai file JSON dengan string multi-line

### <a name="aro"></a>ARO

* `az aro delete`: Tambahkan validasi RBAC pada penghapusan klaster
* `az aro update`: Tambahkan validasi RBAC pada pemutakhiran klaster
* Pastikan worker_profile tidak ada sebelum mendapatkan subnet dari

### <a name="backup"></a>Cadangan

* `az backup job list`: Pecahkan bug tabel -o dan tambahkan backup_management_type sebagai input perintah

### <a name="batch"></a>Batch

* Upgrade data plane to [azure batch 10.0.0](https://pypi.org/project/azure-batch/10.0.0/)
* [BREAKING CHANGE] az batch job task-counts: Mengubah output dari objek JSON yang mengembalikan jumlah tugas ke objek JSON kompleks yang mencakup jumlah tugas (`taskCounts`) serta jumlah slot tugas (`taskSlotCounts`).

### <a name="compute"></a>Compute

* RHEL_ELS_6 tipe lisensi baru
* Adopt track2 SDK, azure-mgmt-compute==18.0.0

### <a name="container"></a>Kontainer

* Perbaiki salah eja dalam `az container create` teks contoh CLI.

### <a name="databoxedge"></a>DataBoxEdge

* Modul perintah baru: dukungan untuk perangkat dan manajemen data-box-edge

### <a name="iot"></a>IoT

* Memperbarui pembuatan kunci perangkat
* Memperbarui tes hub yang diaktifkan identitas untuk memperbaiki masalah ENDPOINT RBAC

### <a name="key-vault"></a>Key Vault

* `az keyvault key import``--kty` Dukungan untuk mengimpor kunci BYOK

### <a name="monitor"></a>Monitor

* `az monitor metrics alert create`: Meningkatkan pesan kesalahan untuk memberikan wawasan yang lebih dapat ditindaklanjuti

### <a name="network"></a>Jaringan

* `az network private-endpoint create`: Tambahkan lebih banyak deklarasi '--subnet' dan '--private-connection-resource-id'
* Ubah validator pembuatan ssl-cert application-gateway
* Memigrasikan jaringan ke sdk2
* Perbaiki bug untuk "az network traffic-manager profile create" saat menggunakan "--routing-method MultiValue"

### <a name="profile"></a>Profil

* Perbaiki "rahasia atau sertifikat yang hilang untuk mengautentikasi melalui kepala dinas"

### <a name="role"></a>Peran

* `az ad sp create-for-rbac`: Usang membuat tugas peran Kontributor secara default

### <a name="security"></a>Keamanan

* Menambahkan perintah skor aman
* Memperbaiki perintah peringatan pembaruan dan mendukung nilai baru

### <a name="sql"></a>SQL

* `az sql dw update`: jangan menerima argumen backup-storage-redundancy
* `az sql db update`: memperbarui redundansi penyimpanan cadangan seperti yang diminta dari perintah

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah #15965: Klarifikasi cara menghapus beberapa tag penahanan legal dengan `az storage container legal-hold [clear|set]`
* `az storage account encryption-scope`: Dukungan GA
* Memperbaiki masalah #9959: Mencoba mengunduh versi snapshot dari berbagi file gagal dengan ResourceNotFound

### <a name="synapse"></a>Synapse

* Add cmdlets baru az synapse sql ad-admin show, create, update, delete
* Add cmdlet baru az synapse workspace firewall-rule update
* Add new cmdlets az synapse sql audit-policy show, update
* Menambahkan cmdlet terkait runtime integrasi

## <a name="december-08-2020"></a>Tanggal 08 Desember 2020

Versi 2.16.0

### <a name="acr"></a>ACR

* Memperbarui deskripsi untuk KEK param

### <a name="aks"></a>AKS

* `az aks nodepool add/update/upgrade`: Ambil parameter lonjakan maks
* Menambahkan dukungan untuk addon AGIC
* Mengubah kluster MSI menjadi default

### <a name="apim"></a>APIM

* `az apim restore`Perintah baru untuk memulihkan cadangan layanan Manajemen API

### <a name="app-service"></a>App Service

* Perbaiki #14857: Biarkan pengguna memperbarui konfigurasi webapp bahkan dengan pembatasan akses
* `az functionapp create`: Terima `--runtime python` dan  `--runtime-version 3.9` sebagai Parameter Azure Functions v3
* Fix #16041: az webapp config ssl create results in unknown error

### <a name="arm"></a>ARM

* `az deployment-scripts`: Hapus bendera pratinjau

### <a name="backup"></a>Cadangan

* Perbaiki #14976: Perbaikan kesalahan CLI untuk kasus ValueError dan AttributeError
* `az backup protection undelete`: Tambahkan dukungan untuk perlindungan AzureWorkload undelete menggunakan CLI
* Perbaiki Kesalahan Permintaan Buruk untuk Input Tipe Beban Kerja yang Benar

### <a name="cdn"></a>CDN

* Tambahkan dukungan multi-origin pratinjau.
* Tambahkan rotasi otomatis BYOC.

### <a name="key-vault"></a>Key Vault

* `az keyvault key/secret list`: Menambahkan parameter `--include-managed` ke sumber daya terkelola daftar

### <a name="monitor"></a>Monitor

* `az monitor metrics alert create`: Mendukung ambang dinamis untuk parameter kondisi
* `az monitor metrics alert update`: Mendukung ambang dinamis untuk parameter kondisi
* `az monitor metrics alert dimension create`: Membangun dimensi aturan peringatan metrik
* `az monitor metrics alert condition create`: Membangun kondisi aturan peringatan metrik

### <a name="mysql"></a>MySQL

* Tambahkan versi MySQL pemutakhiran CLI

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`Dua parameter opsional ditambahkan, aes_encryption dan ldap_signing
* `az netappfiles account backup-policy update`Tiga parameter opsional ditambahkan tag bernama, jenis dan id
* `az netappfiles snapshot policy create`Parameter opsional yang ditambahkan bernama provisioning_state

### <a name="network"></a>Jaringan

* `az network network watcher configure`: Perbaiki NetworkWatcherCountLimitReached error yang disebabkan oleh sensitivitas kasus nilai lokasi
* `az network application-gateway http-listener`: Perbaiki bug yang tidak dapat membuat dan memperbarui dengan nama kebijakan WAF
* `az network route-table`: Deprecate tabel rute V1
* `az network cross-region-lb`: Mendukung penyeimbang beban lintas wilayah
* `az network express-route port generate-loa`Perintah baru untuk menghasilkan dan mengunduh surat otorisasi PDF untuk ExpressRoutePort

### <a name="packaging"></a>Pengemasan

* Tambahkan paket Ubuntu Groovy

### <a name="rdbms"></a>RDBMS

* Menambahkan server tunggal show-connection-string dan tes untuk perintah konteks lokal, pembuatan server

### <a name="role"></a>Peran

* Menambahkan ringkasan panjang/peringatan untuk perintah yang menghasilkan kredensial

### <a name="search"></a>Cari

* Menambahkan opsi SKU

### <a name="service-fabric"></a>Service Fabric

* Perbarui dokumen aplikasi SF. hanya dukungan untuk sumber daya yang digunakan lengan

### <a name="synapse"></a>Synapse

* Support synapse sql dw cmdlets and update az synapse workspace create cmdlet

## <a name="november-20-2020"></a>Tanggal 20 November 2020

Versi 2.15.1

### <a name="profile"></a>Profil

* Hotfix: Fix #15961: az login: UnboundLocalError: variabel lokal 'token_entry' dirujuk sebelum penugasan

## <a name="november-17-2020"></a>17 November 2020

Versi 2.15.0

### <a name="acs"></a>ACS

* Menambahkan peringatan deprekasi v3

### <a name="aks"></a>AKS

* Add ephemeral os functionality
* Peningkatan teknik: Ganti string addon dengan konstanta
* `az aks install-cli`: Dukungan mengkustomisasi url unduhan
* `az aks browse`: Arahkan ke Azure Portal Kubernetes resources view jika k8s >=1.19 atau kube-dashboard tidak diaktifkan
* Mendukung identitas pesawat kontrol BYO
* `az aks use-dev-spaces`: Menunjukkan bahwa perintah ruang dev sudah usang

### <a name="ams"></a>AMS

* Ubah "region" ke "location" dalam string output: az ams account sp create

### <a name="app-config"></a>Konfigurasi Aplikasi

* Memperbaiki inisialisasi klien kubah kunci

### <a name="app-service"></a>App Service

* Perbaiki #13646: Tidak dapat membuat Paket Layanan Aplikasi dalam grup sumber daya yang berbeda dengan Lingkungan Layanan Aplikasi
* Perbaiki #11698 #15198 #14862 #15409: az webapp/functionapp config access-restriction add
* `az functionapp create`: Tambahkan dukungan pratinjau Node 14.
* `az functionapp create`: Hapus bendera pratinjau dari penangan kustom.
* [BREAKING CHANGE] az functionapp update: Memigrasikan functionapp dari Premium ke paket Konsumsi sekarang membutuhkan bendera '--force'.
* `az functionapp update`Tambahkan pesan kesalahan jika migrasi functionapp melibatkan paket apa pun di Linux.
* `az functionapp update`: Tambahkan pesan kesalahan deskriptif lainnya jika migrasi functionapp gagal.

### <a name="arm"></a>ARM

* Memperbaiki masalah di mana What-If menunjukkan dua lingkup grup sumber daya dengan casing yang berbeda
* `az deployment`: Mencetak detail kesalahan untuk penyebaran

### <a name="backup"></a>Cadangan

* Perbaiki #14976: KeyError tetap dan teks bantuan ditingkatkan

### <a name="batch"></a>Batch

* Perbaiki #15464: Perbarui periksa file pfx tanpa kata sandi dalam create_certificate batch

### <a name="billing"></a>Billing

* [BREAKING CHANGE] az billing invoice: Hapus properti BillingPeriodsNames dan DownloadUrlExpiry dari respons.
* `az billing invoice`: Dukung banyak ruang lingkup lain seperti BillingAccount, BillingProfile, dan langganan yang sudah ada.
* `az billing account`Perintah baru untuk mendukung menampilkan dan memperbarui akun penagihan yang ada.
* `az billing balance`Perintah baru untuk mendukung keseimbangan tampilan profil penagihan.
* `az billing customer`Perintah baru untuk mendukung tampilan pelanggan akun penagihan.
* `az billing policy`Perintah baru untuk mendukung kebijakan tampilan dan pembaruan pelanggan atau profil penagihan.
* `az billing product`Perintah baru untuk mengelola produk dari akun penagihan.
* `az billing profile`: Perintah baru untuk mengelola profil penagihan.
* `az billing property`Perintah baru untuk menampilkan dan memperbarui properti akun penagihan.
* `az billing subscription`Perintah baru untuk mengelola langganan untuk akun penagihan.
* `az billing transaction`Perintah baru untuk mencantumkan transaksi faktur.
* `az billing agreement`Perintah baru untuk mengelola perjanjian penagihan.
* `az billing permission`Perintah baru untuk mengelola izin penagihan.
* `az billing role-assignment`Perintah baru untuk mengelola tugas peran.
* `az billing role-definition`Perintah baru untuk menampilkan definisi peran.
* `az billing instruction`Perintah baru untuk mengelola instruksi penagihan.

### <a name="compute"></a>Compute

* Memperbaiki masalah pemeriksaan izin pembaruan
* Penyempurnaan format tabel vm list-skus
* vm host group create: Membuat --platform-fault-domain-count diperlukan dan memperbarui bantuan
* Mendukung pembaruan versi vm/image saat menggunakan gambar cross tenant

### <a name="dps"></a>DPS

* Izinkan tag di Perintah buat DPS IoT

### <a name="hdinsight"></a>HDInsight

* az hdinsight create: Tambahkan dua parameter `--resource-provider-connection` dan `--enable-private-link` untuk mendukung fitur relay outbound dan private link.

### <a name="key-vault"></a>Key Vault

* Memperbaiki pesan kesalahan untuk HSM `list-deleted` dan `purge`
* Mendukung pemulihan kunci selektif untuk HSMs terkelola

### <a name="netappfiles"></a>NetAppFiles

* [BREAKING CHANGE] az netappfiles pool update: Hapus tingkat layanan dari parameter.
* `az netappfiles pool update`: Tambahkan parameter opsional qos-type.
* `az netappfiles pool create`: Tambahkan parameter opsional qos-type.
* `az netappfiles volume replication suspend`: Tambahkan force-break-replication sebagai parameter opsional.
* Tambahkan replikasi volume az netappfiles re-initialize: Perintah baru ditambahkan untuk menginisialisasi ulang replikasi.
* Tambahkan az netappfiles volume pool-change: Perintah baru untuk mengubah kumpulan volume.
* Menambahkan kebijakan snapshot az netappfiles: Grup perintah baru dengan perintah daftar, hapus, perbarui, perlihatkan, buat, dan volume.
* Menambahkan cadangan akun az netappfiles: Grup perintah baru dengan perintah perlihatkan, daftar, dan hapus
* Menambahkan cadangan volume az netappfiles: Grup perintah baru dengan tampilkan, daftar, hapus, perbarui, dan buat perintah.
* Tambahkan az netappfiles account backup-policy: Grup perintah baru dengan perintah perlihatkan, daftar, hapus, perbarui, dan hapus.
* Add az netappfiles vault list: Perintah baru ditambahkan.
* `az netappfiles account ad add`: Tambahkan parameter opsional kdc-ip, nama iklan, server-root-ca-certificate dan operator cadangan
* `az netappfiles volumes create`: Tambahkan parameter opsional snapshot-policy-id, backup-policy-id, backup-enabled, backup-id, policy-enforced, vault-id, kerberos-enabled, throughput-mibps, snapshot-directory-visible, security-style, kerberos5-read-only, kerberos5-read-write, kerberos5i-read-only, kerberos5i-read-write, kerberos5p-read-only, kerberos5p-read-write dan has-root-access.
* `az netappfiles volume update`: Tambahkan parameter opsional vault-id, backup-enabled, backup-policy-id, policy-enforced dan throughput-mibps

### <a name="network"></a>Jaringan

* Memperbaiki bug yang tidak dapat membuat gateway aplikasi Standard_v2 tanpa alamat IP statis pribadi
* `az network dns zone import`: Naikkan FileOperationError alih-alih FileNotFoundError jika file zona tidak ada
* Memperbaiki crash kesalahan NoneType saat menghapus sumber daya ApplicationGateway, LoadBalancer, Nic

### <a name="private-dns"></a>DNS Privat

* `az network private-dns zone import`: Naikkan FileOperationError alih-alih FileNotFoundError jika file zona tidak ada

### <a name="profile"></a>Profil

* `az login`: Tambahkan kembali peringatan bahwa browser dibuka

### <a name="role"></a>Peran

* `az role assignment create`: Membuat `--description`, `--condition`, `--condition-version` pratinjau

### <a name="security"></a>Keamanan

* `az security pricing`: Memperbarui bantuan untuk mencerminkan versi API saat ini yang dipanggil

### <a name="storage"></a>Penyimpanan

* Fix #15600: az storage fs exists: jika fs tidak ada ResourceNotFoundError dikembalikan
* Perbaiki #15706: Contoh untuk membuat kontainer penyimpanan tidak benar
* `az storage blob delete-batch`: Kesalahan ketik yang benar dalam dokumentasi.

## <a name="november-09-2020"></a>Tanggal 09 November 2020

Versi 2.14.2

### <a name="app-service"></a>App Service

* Perbaiki #15604, #15605: Tambahkan dukungan Dotnet5

## <a name="november-06-2020"></a>Tanggal 06 November 2020

Versi 2.14.1

### <a name="arm"></a>ARM

* Hotfix: Tambahkan dukungan string multilin TS untuk input templat

## <a name="october-27-2020"></a>Tanggal 27 Oktober 2020

Versi 2.14.0

### <a name="aks"></a>AKS

* Menambahkan dukungan PPG
* Memperbarui batas waktu penyeimbang beban standar maks hingga 100 menit

### <a name="apim"></a>APIM

* Memperbaiki masalah dengan membuat instans tingkat konsumsi

### <a name="app-config"></a>Konfigurasi Aplikasi

* Memperbaiki query nilai kunci dengan label yang dipisahkan koma

### <a name="app-service"></a>App Service

* Bugfix: az webapp up gagal ketika pengguna tidak memiliki izin menulis ke direktori induk proyek
* Perbaiki #13777: Perbaiki untuk menghapus chars escape dari XML
* Fix #15441: az webapp create-remote-connection gagal dengan AttributeError: objek 'Thread' tidak memiliki atribut 'isAlive'
* [BREAKING CHANGE] az webapp up: add optional params (os & runtime) dan runtime yang diperbarui

### <a name="arm"></a>ARM

* Membuat What-If perintah penyebaran templat GA
* [MELANGGAR PERUBAHAN] Menambahkan konfirmasi pengguna untuk az ts create
* Memperbaiki data yang dikembalikan saat menandai beberapa sumber daya

### <a name="backup"></a>Cadangan

* `az backup policy create`: Tambahkan dukungan untuk pembuatan kebijakan cadangan IaaSVM dari CLI
* Meningkatkan batas perlindungan VM dari 100 hingga 1000

### <a name="compute"></a>Compute

* sig image-definition create: add --features
* Versi API baru dari gallery_images 2020-09-30
* `az vm update / az sig image-version update`: Dukungan pembaruan vm/image-version bahkan menggunakan gambar cross tenant
* Menghapus validasi SKU host vm

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb create/update`: Meningkatkan pesan kesalahan dari input --lokasi yang salah
* `az cosmosdb sql container create/update`: Tambahkan parameter --analytical-storage-ttl

### <a name="hdinsight"></a>HDInsight

* [BREAKING CHANGE] az hdinsight create: hapus dua parameter: --public-network-access-type dan --outbound-public-network-access-type

### <a name="iot-central"></a>IoT Pusat

* Hapus peringatan pratinjau karena sudah GAed

### <a name="key-vault"></a>Key Vault

* Membatalkan pembatalan `--enable-soft-delete false` saat membuat atau memperbarui kubah
* Membuat `--bypass` dan `--default-action` bekerja sama dengan parameter acl jaringan saat membuat kubah

### <a name="misc"></a>Misc.

* Tambahkan bash-completion ke Dockerfile

### <a name="rdbms"></a>RDBMS

* Tambahkan Perintah Daftar-SKUS, Transformer Tabel, Konteks Lokal untuk Postgres, MySQL, Mariadb Single Server
* [MELANGGAR PERUBAHAN] Pembaruan nama parameter. Perbaikan Pesawat Manajemen untuk MySQL dan PostgreSQL
* `az postgres|mariadb|mysql server create` : Perbarui buat pengalaman untuk Postgres, MySQL dan MariaDB - bidang baru dalam output , Memperkenalkan nilai baru untuk `--public` parameter dalam perintah buat (semua,\<IP\>,,\<IPRange\>0.0.0.0)

### <a name="signalr"></a>SignalR

* `az signalr create`: Tambahkan opsi `--enable-messaging-logs` baru untuk mengontrol layanan menghasilkan log pesan atau tidak
* `az signalr update`: Tambahkan opsi `--enable-messaging-logs` baru untuk mengontrol layanan menghasilkan log pesan atau tidak

### <a name="sql"></a>SQL

* [MELANGGAR PERUBAHAN] Memperbaiki respons untuk penyimpanan cadangan redundansi nama param dan nilai untuk MI
* `az sql db audit-policy show`Memperluas untuk menunjukkan kebijakan audit database termasuk data LA dan EH
* `az sql db audit-policy update`: memperluas untuk memungkinkan la dan EH update bersama dengan kebijakan audit database
* `az sql db audit-policy wait`Tempatkan CLI dalam keadaan menunggu sampai kondisi kebijakan audit database terpenuhi.
* `az sql server audit-policy show`Memperluas untuk menunjukkan kebijakan audit server termasuk data LA dan EH
* `az sql server audit-policy update`: memperluas untuk memungkinkan la dan EH update bersama dengan kebijakan audit server
* `az sql server audit-policy wait`Tempatkan CLI dalam keadaan menunggu sampai kondisi kebijakan audit server terpenuhi.
* Menambahkan Dukungan AAD Saja untuk Instans dan Server Terkelola SQL
* `az sql db replica create`: Tambahkan argumen --partner-database

### <a name="storage"></a>Penyimpanan

* Perbaiki #15111: `az storage logging update` gagal tanpa argumen opsional
* Memperbaiki bug saat menggunakan perintah set-tier dengan login utama layanan
* Memutakhirkan versi untuk pengancam data file ke 2020-02-10
* `az storage queue list`: Track2 didukung
* `az storage fs access`: Dukungan mengelola ALS secara rekursif

### <a name="synapse"></a>Synapse

* Menambahkan pipa, layanan tertaut, pemicu, buku catatan, aliran data, dan cmdlet terkait kumpulan data

## <a name="october-13-2020"></a>Tanggal 13 Oktober 2020

Versi 2.13.0

### <a name="acr"></a>ACR

* `az acr helm`: Memperbarui url deprecation
* Menambahkan perubahan logtemplate dan systemtask untuk Tugas ACR

### <a name="aks"></a>AKS

* Mendukung virtual-node dengan aks membuat: `az aks create --enable-addons virtual-node`
* Menambahkan opsi hanya gambar node untuk CLI
* Harapkan addon kube-dashboard dinonaktifkan secara default
* `az aks create/update`: Tambahkan dukungan LicenseType untuk Windows
* Dukungan tambahkan kumpulan node Spot
* Nama addon honor didefinisikan dalam Azure CLI

### <a name="ams"></a>AMS

* Perbaiki #14687: Grup sumber daya campuran dan nama akun dalam perintah "az ams streaming-endpoint show"

### <a name="app-config"></a>Konfigurasi Aplikasi

* Perbaiki bug uji
* Dukungan AAD auth untuk operasi data

### <a name="app-service"></a>App Service

* `az functionapp deployment source config-zip`Memperbaiki masalah di mana config-zip bisa melemparkan pengecualian pada keberhasilan pada konsumsi linux
* Bugfix: Pesan kesalahan yang lebih baik untuk perintah webapp
* `az appservice domain create, show-terms`: Menambahkan kemampuan untuk membuat domain layanan aplikasi
* `az functionapp create`: Menghapus bendera pratinjau dari Java 11 saat membuat aplikasi fungsi baru
* [BREAKING CHANGE] az webapp create, az webapp up - Update runtime webapp yang tersedia

### <a name="arm"></a>ARM

* `az ts`: Tambahkan perintah baru untuk spesifikasi templat
* `az deployment` : Tambahkan dukungan untuk --template-spec -s

### <a name="compute"></a>Compute

* Memperbaiki batasan jumlah FD pembuatan grup tuan rumah
* Menambahkan perintah baru untuk mendukung peningkatan ekstensi untuk VMSS
* Memperbaiki referensi gambar adalah masalah yang hilang

### <a name="hdinsight"></a>HDInsight

* `az hdinsight create`: tambahkan informasi terdepresiasi untuk argumen --public-networrk-access-type dan --outbound-public-network-access-type
* `az hdinsight create`: menambahkan informasi terdepresiasi untuk argumen `--public-networrk-access-type` dan `--outbound-public-network-access-type`
* `az hdinsight create`: menambahkan parameter `--idbroker` untuk mendukung pelanggan untuk membuat cluster ESP dengan HDInsight Id Broker

### <a name="iot-central"></a>IoT Pusat

* Hapus usang 'az iotcentral' command module

### <a name="key-vault"></a>Key Vault

* Dukungan `--hsm-name` untuk `az keyvault key encrypt/decrypt`

### <a name="lab"></a>Laboratorium

* Fix # 14127: `__init__()` mengambil 1 argumen posisi tetapi 2 diberikan

### <a name="network"></a>Jaringan

* `az network application-gateway ssl-cert show`: Tambahkan contoh untuk menunjukkan format sertifikat dan mengambil informasi
* `az network application-gateway rule`: Opsi dukungan --prioritas
* `az network application-gateway create`Memperbaiki bug yang tidak dapat dibuat tanpa IP publik sepcified
* `az network application-gateway waf-policy managed-rule rule-set add`: Mengekspos kesalahan server kepada pengguna untuk memberikan pesan petunjuk yang lebih intuitif.
* `az network application-gateway waf-policy managed-rule rule-set update`Dukungan untuk mengubah versi tipe set aturan.

### <a name="rdbms"></a>RDBMS

* Bugfix: az postgres flexible-server create Remove hardcoded API version from network client.

### <a name="role"></a>Peran

* Perbaiki #15278: `az role assignment list/delete`: Melarang argumen string kosong

### <a name="sql"></a>SQL

* `az sql midb log-replay`: Dukungan untuk layanan replay log pada database terkelola
* Abaikan casing karakter untuk penyimpanan cadangan redundansi nilai param untuk instans terkelola
* [BREAKING CHANGE] az sql db create: Add --backup-storage-redundancy parameter; tambahkan peringatan untuk bsr/bsr == Geo yang tidak ditentukan.

### <a name="sql-vm"></a>SQL VM

* `az sql vm show`: Tambahkan opsi konfigurasi ke bendera --expand

### <a name="storage"></a>Penyimpanan

* [BREAKING CHANGE] `az storage blob copy start`: Memperbaiki masalah format untuk `--destination-if-modified-since` dan `--destination-if-unmodified-since`
* [BREAKING CHANGE] `az storage blob incremental-copy start`: Memperbaiki masalah format untuk `--destination-if-modified-since` dan `--destination-if-unmodified-since`
* `az storage fs`: Memperbaiki masalah string koneksi
* `az storage share-rm`: TINGKAT akses rilis GA
* `az storage container-rm`Menambahkan grup perintah baru untuk menggunakan Microsoft. Storage penyedia sumber daya untuk operasi manajemen kontainer.

## <a name="september-29-2020"></a>Tanggal 29 September 2020

Versi 2.12.1

### <a name="rdbms"></a>RDBMS

* Hotfix: `az postgres flexible-server create` : Perbarui VnetName untuk mengecualikan nama server dan memperbarui wilayah default untuk MySQL

## <a name="september-22-2020"></a>September 22, 2020

Versi 2.12.0

### <a name="acr"></a>ACR

* Perbaiki #14811 Tambahkan dukungan untuk penibut dockerignore

### <a name="aks"></a>AKS

* CLI harus mentolerir kubeconfig kosong
* FIX #12871: az aks enable-addons: Contoh bantuan autogenerasi salah untuk opsi vitual-node
* Menghapus tindakan konektor aci warisan
* Support azure policy addon in azure-cli
* Memperbaiki masalah sensitif kasus untuk addon dasbor AKS
* Perbarui mgmt-containerservice ke 9.4.0 dan aktifkan API 09-01

### <a name="apim"></a>APIM

* Mendukung product/productapi / namedValue entity commands && bump sdk version

### <a name="app-config"></a>Konfigurasi Aplikasi

* Mendukung mengaktifkan/menonaktifkan PublicNetworkAccess untuk toko yang sudah ada

### <a name="app-service"></a>App Service

* Menambahkan dukungan untuk tingkat harga Premium V3
* Perbaiki #12653: az webapp log config --application-logging false tidak mematikannya
* Perbaiki #14684: penghapusan pembatasan akses dengan alamat IP tidak berfungsi; #13837-az webapp create - Contoh untuk RSgroup yang berbeda untuk Paket dan WebApp
* functionapp: Menambahkan dukungan untuk penangan kustom. Usang Powershell 6.2.
* functionapp: Memperbaiki masalah di mana pengaturan aplikasi sedang salah diatur untuk gambar kustom linux

### <a name="arm"></a>ARM

* `az deployment group/sub/mg/tenant what-if`: Tampilkan perubahan sumber daya "Abaikan" terakhir

### <a name="compute"></a>Compute

* Menambahkan license_type baru di vm create/update: RHEL_BYOS, SLES_BYOS
* Memutakhirkan versi API disk ke 2020-06-30
* pembuatan disk: tambahkan --logical-sector-size, --tier
* Pembaruan disk: Dukungan --disk-iops-read-only, --disk-mbps-read-only, --max-shares
* Command disk-encryption-set list-associated-resources baru
* vm boot-diagnostics enable: --storage menjadi optional
* Perintah baru: vm boot-diagnostics get-boot-log-uris
* vm boot-diagnostics get-boot-log: mendukung penyimpanan terkelola

### <a name="config"></a>Konfigurasi

* Mengganti nama local-context menjadi config param-persist

### <a name="cosmos-db"></a>Cosmos DB

* Dukungan untuk API Migrasi untuk sumber daya Throughput untuk fitur SkalaOtoman di CosmosDB

### <a name="eventhub"></a>Eventhub

Menambahkan perintah Cluster dan parameter trusted_service_access_enabled untuk Networkruleset

### <a name="extension"></a>Ekstensi

* `az extension add`: Tambahkan `--upgrade` opsi untuk memperbarui ekstensi jika sudah diinstal
* Mengaktifkan penginstalan dinamis secara default

### <a name="iot"></a>IoT

* Mengaktifkan versi TLS minimum di IoT Hub Create

### <a name="iot-central"></a>IoT Pusat

* Operasi hapus aplikasi sekarang sudah lama berjalan

### <a name="iot-hub"></a>Iot Hub

* Perintah 'show-connection-string' yang tidak dimukakan

### <a name="key-vault"></a>Key Vault

* Pratinjau publik HSM terkelola
* Memperbaiki masalah yang `--maxresults` tidak berlaku saat mencantumkan sumber daya atau versi sumber daya

### <a name="kusto"></a>Kusto

* Menambahkan pesan yang tidak siap

### <a name="monitor"></a>Monitor

* `az monitor log-analytics workspace linked-storage`: mengekspos pesan kesalahan terperinci kepada pelanggan

### <a name="network"></a>Jaringan

* `az network vnet subnet`: Dukungan --disable-private-endpoint-network-policies dan --disable-private-link-service-network-policies
* Perbaiki bug saat memperbarui flow-log saat subpropertoy network_watcher_flow_analytics_configuration tidak ada
* Versi API bump ke 2020-06-01
* Dukungan --tcp-port-behavior saat mengonfigurasi konfigurasi TCP dari Connection Monitor V2
* Mendukung lebih banyak jenis dan tingkat cakupan saat membuat Endpoint of Connection Monitor V2
* Dukungan --host-subnet untuk membuat VirtualHub di bawahnya sebagai VirtualRouter

### <a name="rdbms"></a>RDBMS

* Pembaruan Pesawat Manajemen untuk PostgreSQL dan MySQL

### <a name="role"></a>Peran

* `az role assignment create/update`: Dukungan `--description`, `--condition` dan `--condition-version`
* `az ad app permission delete`: Dukungan `--api-permissions` untuk menghapus secara spesifik `ResourceAccess`

### <a name="service-fabric"></a>Service Fabric

* Menambahkan perintah tipe klaster dan node terkelola

### <a name="sql"></a>SQL

* Upgrade azure-mgmt-sql to 0.20.0
* Menambahkan parameter opsional redundansi penyimpanan cadangan ke MI membuat cmdlet

### <a name="storage"></a>Penyimpanan

* `az storage share-rm stats`: Dapatkan byte penggunaan data yang tersimpan di saham.
* GA rilis penyimpanan gumpalan PITR
* `az storage blob query`: Mendukung Akselerasi Kueri Azure Storage
* Mendukung Soft Delete untuk berbagi file
* `az storage copy`: Tambahkan dukungan kredensial akun dan terdepresiasi `--source-local-path`, `--destination-local-path`, `--destination-account-name`
* `az storage account blob-service-properties update`: Menambahkan dukungan kebijakan penyimpanan hapus kontainer

### <a name="synapse"></a>Synapse

* Kesalahan ketik tetap dalam contoh tugas peran az synapse membuat dan menghapus

## <a name="august-28-2020"></a>Tanggal 28 Agustus 2020

Versi 2.11.1

### <a name="acr"></a>ACR

* Tambahkan Tingkat Terisolasi ke Kolam Agen
* Tambahkan Konteks Sumber Artefak OCI

### <a name="aks"></a>AKS

* Memperbaiki kluster aks membuat masalah

### <a name="cognitive-services"></a>Cognitive Services

* [MELANGGAR PERUBAHAN] Tampilkan istilah hukum tambahan untuk API tertentu

### <a name="network"></a>Jaringan

* [MELANGGAR PERUBAHAN] Memungkinkan untuk membuat IP publik dan pribadi saat membuat Gateway Aplikasi
* `az network list-service-tags`: menambahkan detail tentang parameter lokasi yang digunakan ke pesan bantuan

### <a name="storage"></a>Penyimpanan

* `az storage blob list`: Mendukung properti OR dengan versi api baru

## <a name="august-25-2020"></a>Tanggal 25 Agustus 2020

Versi 2.11.0

### <a name="aks"></a>AKS

* Menghapus tag pratinjau dari add-on Node Virtual
* Menambahkan argumen AKS CMK dalam pembuatan klaster
* Atur profil jaringan saat menggunakan penyeimbang beban dasar.
* Hapus validasi pod maks dari CLI dan biarkan preflight menanganinya
* Memperbaiki add-on yang tersedia dalam pesan bantuan di `az aks create`
* Membawa dukungan untuk profil autoscaler cluster di CLI inti

### <a name="appservice"></a>AppService

* `az webapp`: Menambahkan perintah contoh daftar
* `az webapp ssh`: Tambahkan parameter --instance untuk terhubung ke instans tertentu
* `az webapp create-remote-connection`: Tambahkan parameter --instance untuk terhubung ke instans tertentu
* Perbaiki #14758: az webapp membuat kesalahan saat membuat aplikasi windows dengan --runtime dotnetcore
* Perbaiki #14701: Terapkan functionapp create --assign-identity
* Perbaiki #11244: `az webapp auth update`: Tambahkan parameter opsional untuk memperbarui cap jempol client-secret-certificate-thumbprint
* `az functionapp keys`: Menambahkan perintah yang memungkinkan pengguna untuk mengelola kunci aplikasi fungsi mereka
* `az functionapp function`: Menambahkan perintah yang memungkinkan pengguna untuk mengelola fungsi masing-masing
* `az functionapp function keys`: Menambahkan perintah yang memungkinkan pengguna untuk mengelola kunci fungsi mereka
* Perbaiki #14788: az webapp buat tidak mendapatkan webapp yang benar ketika nama adalah substring
* `az functionapp create`: Kemampuan yang dihapus untuk membuat Fungsi 2.x di wilayah yang tidak mendukungnya

### <a name="arm"></a>ARM

* `az resource list`: Memperluas data `createdTime`pengembalian , `changedTime` dan `provisioningState`
* `az resource`: Tambahkan parameter `--latest-include-preview` untuk mendukung menggunakan versi api terbaru apakah versi ini pratinjau

### <a name="aro"></a>ARO

* Peningkatan CLI, termasuk izin pengecekan tabel rute

### <a name="cloud"></a>Cloud

* `az cloud register`: Memperbaiki awan pendaftaran dengan file konfigurasi

### <a name="compute"></a>Compute

* Memperbarui RSU VM yang mendukung jaringan yang dipercepat
* `az vm create`: Patching in-guest otomatis
* `az image builder create`: Tambahkan --vm-size, --os-disk-size, --vnet, --subnet
* New command az vm assess-patches

### <a name="container"></a>Kontainer

* Perbaiki #6235: Memperbarui teks bantuan untuk parameter port dalam buat kontainer

### <a name="datalake-store"></a>Toko Datalake

* Memperbaiki masalah #14545 untuk operasi gabungan data lake

### <a name="eventhub"></a>EventHub

* `az eventhubs eventhub create/update`: Mengubah dokumentasi destination_name

### <a name="extension"></a>Ekstensi

* Menambahkan `az extension list-versions` perintah untuk mencantumkan semua versi ekstensi yang tersedia

### <a name="hdinsight"></a>HDInsight

* Mendukung pembuatan klaster dengan konfigurasi skala otomatis dan Mendukung pengelolaan konfigurasi skalaoto
* Mendukung pembuatan cluster dengan enkripsi di host

### <a name="iotcentral"></a>IoTCentral

* Perbaikan dokumentasi CLI

### <a name="monitor"></a>Monitor

* `az monitor metrics alert create`: mendukung RG dan Sub sebagai nilai lingkup

### <a name="netappfiles"></a>NetAppFiles

* [BREAKING CHANGE] az netappfiles snapshot create: Dihapus file-system-id dari parameter
* [BREAKING CHANGE] az netappfiles snapshot show: Snapshot tidak lagi memiliki parameter file-system-id
* `az netappfiles account`Model ActiveDirectory memiliki parameter baru backup_operators
* `az netappfiles volume show`Model dataProtection memiliki snapshot parameter baru
* `az netappfiles volume show`Model Volume memiliki parameter baru snapshot_directory_visible

### <a name="network"></a>Jaringan

* `az network dns export`Ekspor FQDN untuk tipe MX, PTR, NS dan SRV, bukan jalur relatif
* Mendukung link pribadi untuk disk terkelola
* `az network application-gateway auth-cert show`: Menambahkan contoh untuk menunjukkan format sertifikat
* `az network private-endpoint-connection`: mendukung konfigurasi aplikasi

### <a name="rbac"></a>RBAC

* `az ad group create`Dukungan menentukan deskripsi saat membuat grup
* `az role definition create`: mencetak pesan yang dapat dibaca manusia alih-alih pengecualian ketika assignableScope adalah array kosong
* [MELANGGAR PERUBAHAN] `az ad sp create-for-rbac`: mengubah izin default sertifikat yang dibuat

### <a name="sql"></a>SQL

* `az sql server audit-policy`: Tambahkan dukungan audit sql server

### <a name="storage"></a>Penyimpanan

* `az storage blob copy start-batch`: Perbaiki #6018 untuk --source-sas
* `az storage account or-policy`: Mendukung kebijakan replikasi objek akun penyimpanan
* Perbaiki masalah #14083 untuk meningkatkan versi paket penyimpanan azure-multiapi untuk masalah paket dan dukungan versi api baru
* `az storage blob generate-sas`: menambahkan contoh untuk --ip dan memperbaiki pesan kesalahan
* `az storage blob list`: Perbaiki masalah next_marker

### <a name="synapse"></a>Synapse

* Tambahkan ruang kerja, sparkpool, cmdlet terkait sqlpool
* Menambahkan perintah releated pekerjaan percikan berdasarkan sdk track2
* Menambahkan perintah terkait fitur accesscontrol berdasarkan sdk track2

### <a name="upgrade"></a>Mutakhirkan

* Menambahkan `az upgrade` perintah untuk memutakhirkan cli dan ekstensi azure

## <a name="august-11-2020"></a>11 Agustus 2020

Versi 2.10.1

### <a name="app-service"></a>App Service

* Perbaiki #9887 webapp dan functionapp, dukungan menetapkan/menghapus identitas terkelola pengguna
* Perbaiki #1382, #14055: Perbarui pesan kesalahan untuk az webapp create and az webapp config container set
* `az webapp up`: Perbaiki logika pemilihan ASP default saat parameter --plan tidak disediakan

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Dukungan yang memungkinkan/menonaktifkan PublicNetworkAccess selama pembuatan toko

### <a name="compute"></a>Compute

* Mendukung mengaitkan disk dan snapshot dengan sumber daya akses disk

### <a name="lab"></a>Laboratorium

* Memperbaiki masalah #7904 bug validasi tanggal di lab vm creation

### <a name="storage"></a>Penyimpanan

* `az storage blob upload-batch`: Perbaiki masalah #14660 dengan argumen unposisional

## <a name="august-04-2020"></a>Tanggal 04 Agustus 2020

Versi 2.10.0

### <a name="aks"></a>AKS

* `az aks update`: Ubah argumen --enable-aad untuk memigrasikan klaster non-AAD berkemampuan RBAC ke klaster AAD yang dikelola AKS
* `az aks install-cli`: Tambahkan argumen --kubelogin-version dan --kubelogin-install-location untuk menginstal kubelogin
* Add az aks nodepool get-upgrades command

### <a name="ams"></a>AMS

* Fix #14021: az ams account sp is not idempotent

### <a name="apim"></a>APIM

* apim api import: mendukung impor API dan enchance perintah cli level api lainnya

### <a name="app-service"></a>App Service

* Perbaiki #13035: Tambahkan validasi untuk az webapp config access-restriction untuk menghindari penambahan duplikat

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Default ke sku standar jika tidak ditentukan
* [MELANGGAR PERUBAHAN] Pengaturan dukungan dengan tipe konten JSON

### <a name="arm"></a>ARM

* `az resource tag`: Perbaiki bug penandaan ManagedApp dan beberapa masalah pengujian terkait
* `az deployment mg/tenant what-if`: Tambahkan dukungan ke grup manajemen dan penyebaran tingkat penyewa What-If
* `az deployment mg/tenant create`: Tambahkan parameter --confirm-with-what-if/-c.
* `az deployment mg/tenant create`: Tambahkan parameter --what-if-result-format/-r.
* `az deployment mg/tenant create`: Tambahkan --what-if-exclude-change-types/-x parameter.
* `az tag`: az tag support for resource id parameter

### <a name="backup"></a>Cadangan

* Memicu penemuan kontainer/item AFS hanya bila diperlukan

### <a name="cdn"></a>CDN

* Menambahkan bidang tautan pribadi ke asal

### <a name="compute"></a>Compute

* `az vm/vmss create`: Pilih nama pengguna yang valid untuk pengguna jika nama pengguna default tidak valid
* `az vm update`: mendukung gambar penyewa silang
* `az disk-access`: Tambahkan grup perintah baru untuk mengoperasikan sumber daya akses disk
* Mendukung penempatan otomatis grup host khusus
* Mendukung ppg dan spg dalam mode orkestrasi VMSS

### <a name="config"></a>Konfigurasi

* `az config`: Menambahkan modul perintah baru `config`

### <a name="extension"></a>Ekstensi

* Dukungan secara otomatis menginstal ekstensi jika ekstensi perintah tidak diinstal

### <a name="hdinsight"></a>HDInsight

* Tambahkan 3 parameter ke perintah `az hdinsight create` untuk mendukung tautan pribadi dan enkripsi dalam fitur transit:

### <a name="iot-hub"></a>Iot Hub

* Perbaiki #7792: IoT Hub Create tidak idempoten

### <a name="iot-central"></a>IoT Pusat

* Tambahkan daftar opsi paramater untuk iot central

### <a name="keyvault"></a>Az.KeyVault

* `az keyvault key encrypt/decrypt`: menambahkan parameter `--data-type` untuk secara eksplisit specifing jenis data asli

### <a name="monitor"></a>Monitor

* `az monitor log-analytics workspace data-export`: mendukung ruang nama hub acara sebagai tujuan.
* `az monitor autoscale`: mendukung ruang nama dan dimensi untuk --condition

### <a name="netappfiles"></a>NetAppFiles

* `az volume revert`: Tambahkan Volume Kembali untuk mengembalikan volume ke salah satu snapshotnya.
* [MELANGGAR PERUBAHAN] Hapus `az netappfiles mount-target`.
* `az volume show`: Menambahkan situs ke Properti Direktori Aktif

### <a name="network"></a>Jaringan

* `az application-gateway private-link add`Dukungan untuk menentukan subnet yang ada berdasarkan ID
* `az network application-gateway waf-policy create`: versi dukungan dan tipe

### <a name="storage"></a>Penyimpanan

* Perbaiki #10302: Mendukung menebak tipe konten saat menyinkronkan file
* `az storage blob lease`: Menerapkan versi api baru untuk operasi sewa gumpalan
* `az storage fs access`: Dukungan AAD kredensial dalam mengelola kontrol akses untuk akun ADLS Gen2
* `az storage share-rm create/update`: tambahkan --access-tier untuk mendukung tingkat akses

## <a name="july-16-2020"></a>16 Juli 2020

Versi 2.9.1

### <a name="aks"></a>AKS

* Menghapus pengaturan eksplisit VMSS dalam perintah contoh Windows karena sekarang default

### <a name="iot"></a>IoT

* [BREAKING CHANGE] `az iot pnp`: Hapus perintah pratinjau IoT PNP dari inti CLI

### <a name="rest"></a>REST

* Perbaiki #14152: `az rest`: Terima URL ARM tanpa ID berlangganan

### <a name="storage"></a>Penyimpanan

* Perbaiki #14138: Buat beberapa izin opsional

## <a name="july-14-2020"></a>14 Juli 2020

Versi 2.9.0

### <a name="acr"></a>ACR

* Menangani link artefak log dari Registry ke log streaming
* Deprecate helm2 perintah

### <a name="aks"></a>AKS

* `az aks create`: tambahkan argumen --enable-aad
* `az aks update`: tambahkan argumen --enable-aad

### <a name="apim"></a>APIM

* Ditambahkan jenderal az apim api commands

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan contoh untuk menggunakan --bidang dalam revisi konfigurasi aplikasi

### <a name="appservice"></a>AppService

* `az functionapp create`: Menambahkan dukungan untuk Java 11 dan Powershell 7. Menambahkan Stacks API Support.
* Memperbaiki pembuatan aplikasi multi-kontainer #14208 gagal
* Fix az webapp create - use hardcoded runtime stacks

### <a name="arm"></a>ARM

* `az resource tag`: Memperbaiki masalah penandaan sumber daya dengan jenis sumber daya `Microsoft.ContainerInstance/containerGroups`

### <a name="compute"></a>Compute

* Disk versi bump 2020-05-01, hitung 2020-06-01
* Enkripsi ganda dari kumpulan enkripsi disk
* `az vmss update`: dukungan menentukan gambar penyewa silang.
* `az sig image-version create`: dukungan menentukan gambar penyewa silang.
* vm/vmss create: Enkripsi cache & data-in-transit untuk disk OS/Data dan disk temp untuk VM & VMSS
* Menambahkan operasi penggusuran simulasi untuk VM dan VMSS

### <a name="cosmosdb"></a>CosmosDB

* Fitur terbaru: Autoscale, IpRules, EnableFreeTier dan EnableAnalyticalStorage

### <a name="eventgrid"></a>EventGrid

* Tambahkan dukungan CLI untuk 2020-04-01-preview dan menandai fitur pratinjau dengan is_Preview= True

### <a name="find"></a>Cari

* Perbaiki #14094 az temukan Perbaiki Kueri gagal saat tidak masuk dan saat telemetri dinonaktifkan

### <a name="hdinsight"></a>HDInsight

* Menambahkan dua perintah untuk mendukung fitur reboot node hdinsight

### <a name="monitor"></a>Monitor

* Menghapus bendera pratinjau untuk perintah di bawah ruang kerja Log Analytics
* `az monitor diagnostic-settings subscription`: Mendukung pengaturan diagnositc untuk langganan
* `az monitor metrics`Dukungan ',' dan '|' dalam nama metrik
* `az monitor log-analytics workspace data-export`: mendukung ekspor data analisis log

### <a name="network"></a>Jaringan

* `az network application-gateway frontend-ip update`: Mendepresiasi parameter --public-ip-address
* Bump azure-mgmt-network to 11.0.0
* `az network express-route gateway connection`: mendukung konfigurasi perutean
* `az network virtual-appliance`: Support Azure network virtual appliance.
* Application Gateway mendukung fitur tautan pribadi

### <a name="policyinsights"></a>PolicyInsights

* `az policy state`: menambahkan perintah trigger-scan untuk memicu evaluasi kepatuhan kebijakan
* `az policy state list`: mengekspos versi entitas kebijakan di setiap catatan kepatuhan

### <a name="profile"></a>Profil

* `az account get-access-token`: Tampilkan kedaluwarsaOn untuk Identitas Terkelola

### <a name="rdbms"></a>RDBMS

* Mendukung versi TLS Minimum
* Menambahkan Enkripsi Infrastruktur untuk Azure Postgres dan MySQL

### <a name="security"></a>Keamanan

* Menambahkan perintah allowed_connections
* Menambahkan perintah pengerasan jaringan Adaptif
* Menambahkan perintah adaptive_application_controls
* Penambahan az security iot-solution/ iot-alerts/iot-recommendations/iot-analytics REST to Azure CLI
* Menambahkan kepatuhan terhadap peraturan CLI

### <a name="signalr"></a>SignalR

* Menambahkan fitur termasuk mengelola koneksi endpoint pribadi, aturan jaringan, dan hulu

### <a name="sql"></a>SQL

* `az sql mi create`, `az sql mi update`: Tambahkan `--tags` parameter ke penandaan sumber daya dukungan
* `az sql mi failover`: Dukungan failover dari titik primer atau sekunder

### <a name="storage"></a>Penyimpanan

* `az storage account create/update`: Tambahkan --allow-blob-public-access untuk memungkinkan atau melarang akses publik untuk gumpalan dan kontainer
* `az storage account create/update`: Tambahkan `--min-tls-version` ke pengaturan dukungan versi TLS minimum yang akan diizinkan pada permintaan penyimpanan.
* Menghapus kredensial token check-in
* Memperbaiki nama akun penyimpanan dalam contoh

### <a name="webapp"></a>Webapp

* Bugfix: az webapp log deployment show - kembalikan log penyebaran alih-alih metadata log
* Bugfix: az webapp vnet-integration add - fix error handling if bad vnet name, support vnet resource ID

## <a name="june-23-2020"></a>Tanggal 23 Juni 2020

Versi 2.8.0

### <a name="acr"></a>ACR

* Menambahkan dukungan untuk menonaktifkan titik akhir wilayah / menonaktifkan perutean
* [MELANGGAR PERUBAHAN] `az acr login --expose-token` tidak menerima nama pengguna dan kata sandi

### <a name="acs"></a>ACS

* Hapus klaster pribadi dan API pratinjau 2019-10-27

### <a name="aks"></a>AKS

* Dukungan --yeah for az aks upgrade
* Kembalikan "ubah default vm sku ke Standard_D2s_v3 (#13541)"
* Tambahkan "az aks update --uptime-sla"
* Fix typo in az aks update command
* Perubahan untuk mendukung kumpulan agen 0 node dan memblokir skala manual untuk kolam yang diaktifkan CAS
* Perbaiki kesalahan ketik di VirtualMachineScaleSets dan perbarui referensi ke versi Kubernetes

### <a name="ams"></a>AMS

* UBAH teks bantuan untuk parameter "--kedaluwarsa".

### <a name="appservice"></a>AppService

* `az webapp log deployment show`: Tampilkan log penyebaran terbaru, atau log penyebaran penyebaran tertentu jika id penyebaran ditentukan
* `az webapp log deployment list`: Daftar log penyebaran yang tersedia
* Memperbaiki: Kesalahan permukaan saat nama webapp tidak valid disediakan
* Perbaiki #13261 az webapp list-runtimes gunakan daftar statis hingga API Stacks baru tersedia
* `az appservice ase create`: Perbaiki masalah buat #13361
* `az appservice ase list-addresses`: Perbaiki perubahan SDK #13140.
* Perbaiki pembuatan webapp/slot untuk Windows Containers
* `az webapp auth update`: Tambahkan parameter opsional untuk memperbarui versi runtime
* Daftar dukungan, hapus, setujui, dan tolak koneksi endpoint pribadi untuk webapp di CLI
* Perbaiki #13888 : Tambahkan dukungan untuk Static WebApps: dapatkan, daftar, buat perintah
* Pesan kesalahan yang disempurnakan untuk Koneksi Terowongan SSH

### <a name="arm"></a>ARM

* `az tag`: Tambahkan contoh untuk -h
* `az deployment group/sub what-if`: Tambahkan parameter --exclude-change-types/-x.
* `az deployment group/sub/mg/tenant create`: Tambahkan --what-if-exclude-change-types/-x parameter.
* `az deployment group/sub/mg/tenant validate`: Tampilkan pesan kesalahan dalam format yang lebih baik.
* `az group export`: Tambahkan parameter `--skip-resource-name-params` baru dan `--skip-all-params` untuk mendukung parameterisasi lewati
* Add az feature unregister api

### <a name="aro"></a>ARO

* Tambahkan Publik, Pribadi ke params untuk bantuan dengan visibilitas ingress / apiserver

### <a name="batch"></a>Batch

* `az batch account create`: Tambahkan parameter baru `--public-network-access`
* `az batch account create`: Tambahkan parameter baru `--identity-type`
* `az batch account set`: Tambahkan parameter baru `--identity-type`
* [BREAKING CHANGE] az batch pool create: Saat membuat kolam menggunakan gambar kustom, properti --image sekarang hanya dapat merujuk ke gambar Galeri Gambar Bersama.
* [BREAKING CHANGE] az batch pool create: Saat membuat kolam dengan opsi --json-file dan menentukan konfigurasi jaringan, properti IP publik telah pindah ke properti baru publicIPAddressConfiguration. Properti baru ini juga mendukung properti ipAddressProvisioningType baru yang menentukan bagaimana kolam renang harus mengalokasikan IP dan properti IP dan PUBLICIP yang memungkinkan konfigurasi daftar sumber daya PublicIP untuk digunakan dalam kasus ipAddressProvisioningType diatur ke UserManaged
* `az network private-link-resource`: Tambahkan dukungan untuk sumber daya Microsoft.Batch batchAccount
* `az network private-endpoint-connection`: Tambahkan dukungan untuk sumber daya Microsoft.Batch batchAccount

### <a name="cdn"></a>CDN

* `az cdn custom-domain enable-https`: Tambahkan dukungan BYOC.
* `az cdn custom-domain enable-https`Memperbaiki memungkinkan HTTPS kustom dengan sertifikat terkelola CDN untuk Standard_Verizon dan Standard_Microsoft SKU.

### <a name="cognitive-services"></a>Cognitive Services

* [MELANGGAR PERUBAHAN] `az cognitiveservices account` Sekarang memiliki struktur terpadu untuk semua perintah.
* `az cognitiveservices account identity`Menambahkan manajemen identitas untuk Layanan Kognitif.

### <a name="compute"></a>Compute

* `az image builder`: Upgrade versi API ke 2020-02-14
* `az image builder create`: Tambahkan `--identity` ke konfigurasi identitas dukungan
* `az image builder customizer add`: Dukungan Windows pemutakhiran customizer
* Perintah baru `az image builder cancel`
* Tampilkan peringatan saat pengguna menyebarkan VMSS yang disematkan ke versi gambar tertentu daripada versi terbaru

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb`: Menambahkan perintah ada ke database dan grup kontainer
* Perbolehkan membuat koleksi tetap

### <a name="eventhub"></a>EventHub

* `az eventhubs namespace create` : Menambahkan parameter identitas terkelola

### <a name="extension"></a>Ekstensi

* Menambahkan --version ke dukungan untuk menginstal dari versi tertentu
* Aktifkan ekstensi CLI untuk menyertakan paket di namespace 'azure'

### <a name="iot-hub"></a>Iot Hub

* [BREAKING CHANGE] az iot hub job: Hapus perintah pekerjaan yang tidak siap

### <a name="keyvault"></a>Az.KeyVault

* `az keyvault key import`Mendukung impor dari string melalui dua parameter baru.
* Mendukung enkripsi string /byte dan dekripsi dengan kunci yang tersimpan

### <a name="monitor"></a>Monitor

* Dukungan tidak menunggu pembuatan cluster
* `az monitor log-analytics workspace saved-search`: Mendukung perintah baru untuk pencarian yang disimpan

### <a name="network"></a>Jaringan

* `az network application-gateway address-pool update`: Perbaiki pesan bantuan dan tambahkan contoh.
* `az network vnet create`: Mendukung argumen --nsg
* `az network lb address-pool`: Dukungan buat kolam lb backend dengan alamat backend.
* `az network application-gateway address-pool`: Perbaiki untuk --add argumen

### <a name="rbac"></a>RBAC

* `az ad sp create-for-rabc`: Nama dukungan dengan spasi, garis miring dan garis miring belakang
* `az ad sp create-for-rbac`: Memperbaiki pesan kesalahan saat pengguna menentukan lingkup yang tidak valid

### <a name="security"></a>Keamanan

* Menambahkan perintah penilaian keamanan

### <a name="sql"></a>SQL

* `az sql db ltr-policy/ltr-backup`: memperbarui/menampilkan kebijakan retensi jangka panjang, memperlihatkan/menghapus cadangan retensi jangka panjang, memulihkan cadangan retensi jangka panjang

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah autentikasi untuk mendukung mendapatkan token untuk --subscription
* `az storage remove`: Perbaiki masalah #13459 untuk mengajukan pengecualian atas kegagalan operasi
* Memperbaiki masalah #13012, #13632 dan #13657 untuk menghapus argumen yang tidak digunakan untuk perintah terkait generate-sas
* `az storage logging update`: Tambahkan cek untuk versi pembuatan log
* `az storage blob show`: Tambahkan lebih banyak properti untuk gumpalan dengan sdk track 2
* Perbaiki #13708: Perbaiki pesan peringatan untuk kredensial
* `az storage share-rm create/update`: Tambahkan protokol NFS dan dukungan root squash
* `az storage account create`: Tambahkan dukungan untuk enkripsi ganda
* [BREAKING CHANGE] `az storage blob/container/file/share/table/queue generate-sas`: membuat --expiry dan --permissions diperlukan
* `az storage blob set-tier`Migrasi ke Track 2 untuk mendukung pengaturan prioritas rehydrate

## <a name="june-02-2020"></a>Juni 02, 2020

Versi 2.7.0

### <a name="acr"></a>ACR

* Memperbaiki kesalahan ketik dalam pesan kesalahan pembuatan token

### <a name="aks"></a>AKS

* Ubah default vm sku ke Standard_D2s_v3
* Memperbaiki pembuatan tugas peran untuk clsuter MSI ditambah subnet kustom

### <a name="appservice"></a>AppService

* Fix #12739 az appservice list-locations mengembalikan beberapa lokasi yang tidak valid

### <a name="arm"></a>ARM

* `az deployment`Memperbaiki masalah # 13159 dari pesan yang salah dari JSON setelah menghapus komentar dan mengompresi
* `az resource tag`: Memperbaiki masalah #13255 dari sumber daya penandaan dengan jenis sumber daya `Microsoft.ContainerRegistry/registries/webhooks`
* Meningkatkan contoh untuk modul sumber daya

### <a name="aro"></a>ARO

* Ubah CLIError untuk mengoreksi bendera untuk --worker-vm-disk-size-gb

### <a name="eventhub"></a>EventHub

* Perbaiki untuk masalah #12406 Argumen --capture-interval tidak memperbarui "intervalInSeconds"

### <a name="hdinsight"></a>HDInsight

* Ubah get_json_object menjadi shell_safe_json_parse

### <a name="monitor"></a>Monitor

* `az monitor metrics alert`: memperbaiki beberapa pesan bantuan
* `az monitor diagnostic-settings create`: dukungan --export-to-resource-specific argument
* Mendukung pemulihan ruang kerja LA

### <a name="network"></a>Jaringan

* `az network dns zone`: dukungan - karakter
* `az network vpn-connection ipsec-policy`: mengubah --sa-lifetime dan --sa-max-size ke nilai yang lebih besar dalam contoh
* Jaringan bump ke 2020-04-01
* `az network private-endpoint-connection`: jaringan acara dukungan
* `az network express-route list-route-tables`: memperbaiki bug yang tidak dapat mencantumkan rute sebagai tabel

### <a name="packaging"></a>Pengemasan

* Tambahkan Paket Fokus Ubuntu

### <a name="rbac"></a>RBAC

* `az ad sp credential reset`: memodifikasi pembuatan kredensial untuk menghindari karakter khusus yang merepotkan

### <a name="redis"></a>Redis

* Perbaiki #13529: Ubah dokumentasi parameter enable_non_ssl_port

### <a name="storage"></a>Penyimpanan

* `az storage copy`: Menambahkan parameter `--follow-symlinks` untuk mendukung symlinks
* Aktifkan konteks lokal untuk akun penyimpanan
* `az storage logging`: Perbaiki masalah #11969 untuk memperbaiki pesan kesalahan

## <a name="may-19-2020"></a>19 Mei 2020

Versi 2.6.0

### <a name="acr"></a>ACR

* Menambahkan batas waktu default 5 menit untuk setiap permintaan ke ACR
* Dukungan menonaktifkan akses jaringan publik
* `az acr token create`: mengekspos argumen --days
* `az acr import`: menerima nilai argumen --source yang berisi login dalam nama server melalui koreksi akhir klien

### <a name="acs"></a>ACS

* Perbaikan bug: hapus pembersihan bidang untuk bidang yang tidak lagi ada

### <a name="aks"></a>AKS

* Memperbarui konteks bantuan perintah uptime-sla
* Hapus pemeriksaan rentang untuk memperbarui jumlah menit untuk autoscaler
* Perbaiki bahwa cli doe tidak gagal ketika pengguna hanya menentukan kata sandi Windows

### <a name="ams"></a>AMS

* `az ams transform create`: Tambahkan kemampuan untuk membuat transformasi dengan preset FaceDetector
* `az ams content-key-policy create` : Tambahkan kemampuan untuk membuat kebijakan kunci konten FairPlay dengan konfigurasi sewa offline

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Perbaikan bug untuk nilai kunci daftar dengan bidang

### <a name="appservice"></a>AppService

* `az functionapp create`: AzureWebJobsDashboard hanya akan diatur jika AppInsights dinonaktifkan
* Perbaiki #10664- Integrasi VNet - Masalah Cek Lokasi & perbaiki #13257- az webapp up gagal saat RG perlu dibuat
* `az webapp|functionapp config ssl import`: Cari kubah kunci di seluruh grup sumber daya dalam langganan dan tingkatkan bantuan dan contoh.
* Konteks lokal onboard untuk layanan aplikasi

### <a name="arm"></a>ARM

* `az deployment`: Memperbaiki masalah bahwa templateLink tidak akan dikembalikan saat menyebarkan atau memvalidasi template-uri
* `az deployment`: Memperbaiki masalah bahwa penyebaran / validasi tidak mendukung karakter yang dikodekan secara khusus
* `az deployment sub/group what-if`: Memperbaiki perataan array dan penanganan kesalahan
* `az deployment operation`: Memodifikasi informasi terdepresiasi

### <a name="aro"></a>ARO

* Menambahkan contoh ke az aro create, list, list-credentials, show, delete
* Menambahkan fungsi generate_random_id

### <a name="backup"></a>Cadangan

* Perbolehkan FriendlyName dalam aktifkan perlindungan untuk perintah AzureFileShare
* Perbaiki di Perintah Restore-disk IaasVM
* Menambahkan perintah BackupManagementType "MAB" ke daftar item
* Tambahkan dukungan untuk mencoba kembali pembaruan kebijakan untuk item yang gagal.
* Menambahkan fungsionalitas Perlindungan Resume untuk Azure Virtual Machine
* Menambahkan dukungan untuk menentukan ResourceGroup untuk menyimpan instantRP selama Buat atau Ubah Kebijakan

### <a name="ci"></a>CI

* Dukungan flake8 3.8.0

### <a name="compute"></a>Compute

* Perintah baru az vm auto-shutdown
* `az vm list-skus`: Perbarui perilaku --zone, kembalikan semua jenis skus sekarang

### <a name="core"></a>Core

* Memperbarui status on/off konteks lokal ke tingkat pengguna global

### <a name="extension"></a>Ekstensi

* `az extension add`: Tambahkan --system untuk mengaktifkan penginstalan ekstensi di jalur sistem
* Mendukung .egg-info untuk menyimpan metadata ekstensi tipe roda

### <a name="iot"></a>IoT

* `az iot`: Perbarui modul perintah IoT pertama-tama jalankan pesan kesadaran ekstensi ke Id `azure-iot`modern yang akurat dan tidak usang.

### <a name="iot-hub"></a>IoT Hub

* Dukungan untuk perintah API dan Isolasi Jaringan 2020-03-01

### <a name="netappfiles"></a>NetAppFiles

* `az volume create`Menambahkan snapshot-id sebagai parameter untuk membuat volume ini akan memungkinkan pengguna untuk membuat volume dari snapshot yang ada.

### <a name="network"></a>Jaringan

* Memperbaiki nilai ttl diubah tidak dimaksudkan untuk add-record dns
* `az network public-ip create`: Beri tahu pelanggan tentang perubahan yang akan datang
* Mendukung perintah generik untuk skenario tautan pribadi
* `az network private-endpoint-connection`: Mendukung mysql, postgres dan mariadb jenis
* `az network private-endpoint-connection`: Mendukung tipe cosmosdb
* `az network private-endpoint`: usangkan --group-ids dan pengalihan ke --group-id

### <a name="output"></a>Output

* Tampilkan instruksi pembaruan di temukan, umpan balik, dan --bantuan

### <a name="packaging"></a>Pengemasan

* Bangun paket MSI/Homebrew dengan dependecies diselesaikan dari requirements.txt

### <a name="rbac"></a>RBAC

* `az ad sp credential reset`: memperbaiki generasi kredensial yang lemah

### <a name="storage"></a>Penyimpanan

* `az storage account file-service-properties update/show`: Tambahkan Dukungan Properti File untuk Akun Storage
* `az storage container create`: Perbaiki #13373 dengan menambahkan validator untuk akses publik
* Menambahkan dukungan jalur ADLS Gen22
* `az storage blob sync`: Dukungan `--connection-string`
* `az storage blob sync`: Memperbaiki pesan kesalahan yang salah ketika azcopy tidak dapat menemukan lokasi instalasi

## <a name="april-30-2020"></a>Tanggal 30 April 2020

Versi 2.5.1

### <a name="acr"></a>ACR

* `az acr check-health`Memperbaiki "DOCKER_PULL_ERROR" pada Windows

### <a name="compute"></a>Compute

* `az vm list-ip-addresses`: Penanganan kesalahan
* Memperbaiki bug vm create jika endpoint_vm_image_alias_doc tidak diatur dalam profil cloud
* `az vmss create`: Tambahkan --os-disk-size-gb

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb create/update`: tambahkan dukungan --enable-public-network

### <a name="extension"></a>Ekstensi

* Memperbaiki pemuatan metadata yang salah untuk ekstensi tipe roda

### <a name="packaging"></a>Pengemasan

* Tambahkan skrip az untuk Git Bash/ Cygwin di Windows

### <a name="sql"></a>SQL

* `az sql instance-pool`: Tambahkan grup perintah kumpulan instans

### <a name="storage"></a>Penyimpanan

* Upgrade paket azure-multiapi-storage to 0.3.0
* Mendukung GZRS untuk pembuatan dan pembaruan akun penyimpanan
* `az storage account failover`: Tambahkan dukungan untuk kegagalan akun penyimpanan grs/gzrs
* `az storage blob upload`: Tambahkan parameter --encryption-scope untuk mendukung menentukan informasi lingkup enkripsi

## <a name="april-28-2020"></a>Tanggal 28 April 2020

Versi 2.5.0

### <a name="acs"></a>ACS

* [BREAKING CHANGE] az openshift create: remove --vnet-peer parameter.
* `az openshift create`: tambahkan bendera untuk mendukung cluster pribadi.
* `az openshift`: upgrade ke `2019-10-27-preview` versi API.
* `az openshift`: tambahkan `update` perintah.

### <a name="aks"></a>AKS

* `az aks create`: Tambahkan dukungan untuk Windows

### <a name="appservice"></a>AppService

* `az webapp deployment source config-zip`: hapus tidur setelah permintaan.get()

### <a name="arm"></a>ARM

* Menambahkan perintah What-If penyebaran templat

### <a name="aro"></a>ARO

* `az aro`: Memperbaiki output tabel

### <a name="ci"></a>CI

* Onboard pytest dan deprecate hidung untuk Tes Otomasi

### <a name="compute"></a>Compute

* `az vmss disk detach`: memperbaiki disk data Masalah NoneType
* `az vm availability-set list`: Dukungan yang menampilkan daftar VM
* `az vm list-skus`: Memperbaiki masalah tampilan format tabel

### <a name="keyvault"></a>Az.KeyVault

* Menambahkan parameter `--enable-rbac-authorization` baru selama membuat atau memperbarui

### <a name="monitor"></a>Monitor

* Mendukung fitur CMK cluster LA
* `az monitor log-analytics workspace linked-storage`: mendukung fitur BYOS

### <a name="network"></a>Jaringan

* `az network security-partner`: mendukung penyedia mitra keamanan

### <a name="privatedns"></a>Privatedns

* Menambahkan fitur di zona DNS pribadi untuk mengimpor file zona ekspor

## <a name="april-21-2020"></a>Tanggal 21 April 2020

Versi 2.4.0

### <a name="acr"></a>ACR

* `az acr run --cmd`: nonaktifkan penibut direktori kerja
* Mendukung titik akhir data khusus

### <a name="aks"></a>AKS

* `az aks list -o table` harus menunjukkan privateFqdn sebagai fqdn untuk cluster swasta
* Tambahkan --uptime-sla
* Memperbarui paket layanan kontainer
* Menambahkan dukungan IP publik node
* Memperbaiki kesalahan ketik di perintah bantuan

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menyelesaikan referensi kubah utama untuk daftar kv dan perintah ekspor
* Perbaikan bug untuk nilai kunci daftar

### <a name="appservice"></a>AppService

* `az functionapp create`: Mengubah cara linuxFxVersion sedang diatur untuk aplikasi fungsi dotnet linux. Ini harus memperbaiki bug yang mencegah aplikasi konsumsi dotnet linux dibuat.
* [BREAKING CHANGE] `az webapp create`: memperbaiki agar AppSettings yang ada dengan az webapp create
* [BREAKING CHANGE] `az webapp up`: memperbaiki untuk membuat perintah RG for az webapp up saat menggunakan bendera -g
* [BREAKING CHANGE] `az webapp config`: memperbaiki untuk menampilkan nilai untuk output non-JSON dengan az webapp config connection-string list

### <a name="arm"></a>ARM

* `az deployment create/validate`: Tambahkan parameter `--no-prompt` untuk mendukung melewatkan prompt parameter yang hilang untuk templat ARM
* `az deployment group/mg/sub/tenant validate`: Komentar dukungan dalam file parameter penyebaran
* `az deployment`: Hapus `is_preview` untuk parameter `--handle-extended-json-format`
* `az deployment group/mg/sub/tenant cancel`: Dukungan membatalkan penyebaran untuk templat ARM
* `az deployment group/mg/sub/tenant validate`: Meningkatkan pesan kesalahan saat verifikasi penyebaran gagal
* `az deployment-scripts`: Menambahkan perintah baru untuk DeploymentScripts
* `az resource tag`: Tambahkan parameter `--is-incremental` untuk mendukung menambahkan tag ke sumber daya secara bertahap

### <a name="aro"></a>ARO

* `az aro`: Tambahkan Modul perintah Azure RedHat OpenShift V4 aro

### <a name="batch"></a>Batch

* Memperbarui API Batch

### <a name="compute"></a>Compute

* `az sig image-version create`: Tambahkan tipe akun penyimpanan Premium_LRS
* `az vmss update`: Perbaiki masalah pembaruan pemberitahuan akhir
* `az vm/vmss create`: Tambahkan dukungan untuk versi gambar khusus
* SIG API Version 2019-12-01
* `az sig image-version create`: Tambahkan --target-region-encryption
* Memperbaiki tes gagal saat berjalan dalam serial karena nama keyvault diduplikasi dalam cache in-momery global

### <a name="cosmosdb"></a>CosmosDB

* Dukung `az cosmosdb private-link-resource/private-endpoint-connection`

### <a name="iot-central"></a>IoT Pusat

* Deprecate `az iotcentral`
* Menambahkan `az iot central` modul perintah

### <a name="monitor"></a>Monitor

* Mendukung skenario tautan pribadi untuk monitor
* Perbaiki cara mengejek yang salah di test_monitor_general_operations.py

### <a name="network"></a>Jaringan

* Deprecate sku untuk perintah pembaruan ip publik
* `az network private-endpoint`: Mendukung grup zona dns pribadi
* Aktifkan fitur konteks lokal untuk parameter vnet/subnet
* Memperbaiki contoh penggunaan yang salah di test_nw_flow_log_delete

### <a name="packaging"></a>Pengemasan

* Drop dukungan untuk paket Ubuntu / Disco

### <a name="rbac"></a>RBAC

* `az ad app create/update`: dukungan --optional-claims sebagai parameter

### <a name="rdbms"></a>RDBMS

* Menambahkan perintah administrator direktori aktif Azure untuk PostgreSQL dan MySQL

### <a name="service-fabric"></a>Service Fabric

* Perbaiki #12891: `az sf application update --application-parameters` menghapus parameter lama yang tidak ada dalam permintaan
* Perbaiki #12470 az sf create cluster, perbaiki bug dalam memperbarui daya tahan dan keandalan dan temukan vmss dengan benar melalui kode yang diberi nama tipe node

### <a name="sql"></a>SQL

* Tambahkan `az sql mi op list`, `az sql mi op get`, `az sql mi op cancel`
* `az sql midb`: memperbarui/menampilkan kebijakan retensi jangka panjang, memperlihatkan/menghapus cadangan retensi jangka panjang, memulihkan cadangan retensi jangka panjang

### <a name="storage"></a>Penyimpanan

* Upgrade azure-mgmt-storage to 9.0.0
* `az storage logging off`: Dukungan mematikan log untuk akun penyimpanan
* `az storage account update`: Aktifkan kunci yang diputar otomatis untuk CMK
* `az storage account encryption-scope create/update/list/show`: Menambahkan dukungan untuk mengkustomisasi lingkup enkripsi
* `az storage container create`: Tambahkan --default-encryption-scope dan --deny-encryption-scope-override untuk mengatur cakupan enkripsi untuk tingkat kontainer

### <a name="survey"></a>Survei

* Menambahkan sakelar untuk menonaktifkan link survei

## <a name="april-01-2020"></a>01 April 2020

Versi 2.3.1

### <a name="acr"></a>ACR

* Fix wrong version of azure-mgmt-containerregistry for Linux

### <a name="profile"></a>Profil

* az login: Perbaiki kegagalan login dengan profil cloud selain `latest`

## <a name="march-31-2020"></a>31 Maret 2020

Versi 2.3.0

### <a name="acr"></a>ACR

* 'az acr task update': pengecualian pointer null
* `az acr import`: Memodifikasi pesan bantuan dan kesalahan untuk memperjelas penggunaan --source dan --registry
* Menambahkan validator untuk argumen 'registry_name'
* `az acr login`:Hapus bendera pratinjau di '--expose-token'
* [MELANGGAR PERUBAHAN] Parameter cabang 'az acr task create/update' dihapus
* 'az acr task update' Pelanggan sekarang dapat memperbarui konteks, git-token, dan atau pemicu secara individual
* 'az acr agentpool': fitur baru

### <a name="aks"></a>AKS

* Perbaiki apiServerAccessProfile saat memperbarui --api-server-authorized-ip-ranges
* pembaruan aks: Mengesampingkan IP keluar dengan nilai input saat memperbarui
* Jangan buat SPN untuk klaster MSI dan dukung lampirkan ACR ke klaster MSI

### <a name="ams"></a>AMS

* Perbaiki #12469: menambahkan kebijakan kunci konten Fairplay gagal karena masalah dengan parameter 'ask'

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Tambahkan --skip-keyvault untuk ekspor kv

### <a name="appservice"></a>AppService

* Perbaiki #12509: Hapus tag ke az webapp secara default
* az functionapp create: Menu bantuan --runtime-version yang diperbarui dan peringatan tambahan saat pengguna menentukan --runtime-version untuk dotnet
* az functionapp create: Memperbarui cara javaVersion sedang diatur untuk aplikasi fungsi Windows

### <a name="arm"></a>ARM

* az deployment create/validate: Use --handle-extended-json-format secara default
* az lock create: Menambahkan contoh membuat subresource dalam dokumentasi bantuan
* az deployment {group/mg/sub/tenant} list: FilteringState provisioning Support
* az deployment: Perbaiki bug parse untuk komentar di bawah argumen terakhir

### <a name="backup"></a>Cadangan

* Menambahkan beberapa kemampuan pemulihan file
* Menambahkan dukungan untuk Mencadangkan Disk OS saja
* Menambahkan parameter restore-as-unmanaged-disk untuk menentukan pemulihan yang tidak dikelola

### <a name="compute"></a>Compute

* az vm create: Tambahkan NONE option of --nsg-rule
* az vmss create/update: remove vmss automatic repairs preview tag
* az vm update: Support --workspace
* Memperbaiki bug di kode inisialisasi VirtualMachineScaleSetExtension
* Upgrade VMAccessAgent version ke 2.4
* az vmss set-orchestration-service-state: support vmss set orchestration service state
* Pemutakhiran versi API disk ke 2019-11-01
* az disk create: add --disk-iops-read-only, --disk-mbps-read-only, --max-shares, --image-reference, --image-reference-lun, --gallery-image-reference, --gallery-image-reference-lun

### <a name="cosmos-db"></a>Cosmos DB

* Memperbaiki opsi hilang --type untuk pengalihan deprekasi

### <a name="docker"></a>Docker

* Pembaruan ke Alpine 3.11 dan Python 3.6.10

### <a name="extension"></a>Ekstensi

* Memungkinkan untuk memuat ekstensi di jalur sistem melalui paket

### <a name="hdinsight"></a>HDInsight

* (az hdinsight create:) Pelanggan dukungan menentukan versi tls yang didukung minimal dengan menggunakan parameter `--minimal-tls-version`. Nilai yang diizinkan adalah 1,0,1.1,1,2

### <a name="iot"></a>IoT

* Menambahkan pemilik kode
* az iot hub create : Change default sku to S1 from F1
* iot hub: Dukung IotHub di profil 2019-03-01-hybrid

### <a name="iotcentral"></a>IoTCentral

* Memperbarui detail kesalahan, memperbarui templat aplikasi default, dan pesan cepat

### <a name="keyvault"></a>Az.KeyVault

* Cadangan/pemulihan sertifikat dukungan
* keyvault create/update: Support --retention-days
* Tidak lagi menampilkan kunci / rahasia terkelola saat mendaftar
* az keyvault create: support `--network-acls`, `--network-acls-ips` dan `--network-acls-vnets` untuk menentukan aturan jaringan saat membuat vault

### <a name="lock"></a>Kunci

* az lock delete fix bug: az lock delete tidak berfungsi di Microsoft.DocumentDB

### <a name="monitor"></a>Monitor

* az monitor clone: mendukung aturan metrik klon dari satu sumber daya ke sumber daya lainnya
* Perbaiki IcM179210086: tidak dapat membuat peringatan metrik khusus untuk metrik Insights Aplikasi mereka

### <a name="netappfiles"></a>NetAppFiles

* az volume create: Izinkan volume perlindungan data menambahkan operasi replikasi: menyetujui, menangguhkan, melanjutkan, status, menghapus

### <a name="network"></a>Jaringan

* az network application-gateway waf-policy managed-rule rule-set add: support Microsoft_BotManagerRuleSet
* network watcher flow-log show: memperbaiki info usang yang salah
* mendukung nama host di pendengar gateway aplikasi
* az network nat gateway: dukungan membuat sumber daya kosong tanpa ip publik atau awalan ip publik
* Mendukung pembuatan gateway VPN
* Dukungan `--if-none-match` di `az network dns record-set {} add-record`

### <a name="packaging"></a>Pengemasan

* Drop dukungan untuk python 3.5

### <a name="profile"></a>Profil

* az login: Tampilkan peringatan untuk kesalahan MFA

### <a name="rdbms"></a>RDBMS

* Menambahkan perintah manajemen kunci enkripsi data server untuk PostgreSQL dan MySQL

## <a name="march-10-2020"></a>10 Maret 2020

Versi 2.2.0

### <a name="acr"></a>ACR

* Perbaiki: `az acr login` salah meningkatkan kesalahan
* Menambahkan perintah baru `az acr helm install-cli`
* Menambahkan link pribadi dan dukungan CMK
* menambahkan perintah 'daftar sumber daya tautan pribadi'

### <a name="aks"></a>AKS

* memperbaiki telusuri aks di shell cloud
* az aks: Memperbaiki addon pemantauan dan kesalahan NoneType agentpool
* Tambahkan --nodepool-tags ke node pool saat membuat cluster kubernetes azure
* Menambahkan --tag saat menambahkan atau memperbarui nodepool ke cluster
* aks buat: tambahkan `--enable-private-cluster`
* add --nodepool-labels saat membuat cluster kubernetes azure kubernetes
* add --labels saat menambahkan nodepool baru ke cluster kubernetes azure
* menambahkan hilang / di url dasbor
* Dukungan membuat kluster aks yang memungkinkan identitas terkelola
* az aks: Validasi plugin jaringan menjadi "azure" atau "kubenet"
* az aks: Tambahkan dukungan kunci sesi aad
* [BREAKING CHANGE] az aks: mendukung perubahan msi untuk GF dan BF untuk omsagent (Container monitoring)(#1)
* az aks use-dev-spaces: Menambahkan opsi tipe endpoint ke perintah use-dev-spaces untuk menyesuaikan titik akhir yang dibuat pada pengontrol Azure Dev Spaces

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Buka blokir menggunakan "kv set" untuk menambahkan referensi dan fitur keyvault ...

### <a name="appservice"></a>AppService

* az webapp create : Memperbaiki masalah saat menjalankan perintah dengan --runtime
* az functionapp deployment source config-zip: Menambahkan pesan kesalahan jika grup sumber daya atau nama fungsi tidak valid/tidak ada
* functionapp create: Perbaiki pesan peringatan yang muncul dengan `functionapp create` hari ini yang `--functions_version` mengutip bendera tetapi secara keliru menggunakan `_` bukan `-` dalam nama bendera
* az functionapp create: Memperbarui cara linuxFxVersion dan nama gambar kontainer sedang diatur untuk aplikasi fungsi linux
* az functionapp deployment source config-zip: Memperbaiki masalah yang disebabkan oleh pengaturan aplikasi mengubah kondisi balap selama zip deploy, memberikan 5xx kesalahan selama penyebaran
* Perbaiki #5720946: az webapp backup gagal mengatur nama

### <a name="arm"></a>ARM

* az resource: Meningkatkan contoh modul sumber daya
* az daftar penugasan kebijakan: Mendukung daftar tugas kebijakan di lingkup Grup Manajemen
* Menambahkan `az deployment group` dan `az deployment operation group` untuk penyebaran templat di grup sumber daya. Ini adalah duplikat dari `az group deployment` dan `az group deployment operation`
* Tambahkan `az deployment sub` dan `az deployment operation sub` untuk penyebaran templat di lingkup langganan. Ini adalah duplikat dari `az deployment` dan `az deployment operation`
* Menambahkan `az deployment mg` dan `az deployment operation mg` untuk penyebaran templat di grup manajemen
* Menambahkan `az deployment tenant` dan `az deployment operation tenant` untuk penyebaran templat di lingkup penyewa
* az pembuatan tugas kebijakan: Menambahkan deskripsi ke `--location` parameter
* az penyebaran grup buat: Menambahkan parameter `--aux-tenants` untuk mendukung penyewa silang

### <a name="cdn"></a>CDN

* Menambahkan perintah WAF CDN

### <a name="compute"></a>Compute

* az sig image-version: add --data-snapshot-luns
* az ppg show: tambahkan --colocation-status untuk memungkinkan pengambilan status kolokasi semua sumber daya dalam kelompok penempatan kedekatan
* az vmss create/update: support automatic repairs
* [MELANGGAR PERUBAHAN] az gambar template: mengganti nama template ke builder
* az pembangun gambar buat: tambahkan --image-template

### <a name="cosmos-db"></a>Cosmos DB

* Menambahkan sql stored procedure, udf dan trigger cmdlets
* az cosmosdb create: add --key-uri to support add key vault encryption information

### <a name="keyvault"></a>Az.KeyVault

* pembuatan keyvault: aktifkan penghapusan lunak secara default

### <a name="monitor"></a>Monitor

* az monitor metrik peringatan create: support `~` in `--condition`

### <a name="network"></a>Jaringan

* az network application-gateway rewrite-rule create: support url configuration
* az network dns zone import: --zone-name akan menjadi kasus yang tidak sensitif di masa depan
* az network private-endpoint/private-link-service: hapus label pratinjau
* az network bastion: support bastion
* az network vnet list-available-ips: support list ips available in a vnet
* az network watcher flow-log create/list/delete/update: menambahkan perintah baru untuk mengelola log alur pengamat dan mengekspos --location untuk mengidentifikasi pengamat secara eksplisit
* az network watcher flow-log configure: usang
* az network watcher flow-log show: support --location dan --name untuk mendapatkan hasil yang diformat ARM, usang output diformat lama

### <a name="policy"></a>Kebijakan

* az pembuatan tugas kebijakan: Perbaiki bug yang secara otomatis menghasilkan nama penugasan kebijakan melebihi batas

### <a name="rbac"></a>RBAC

* az ad group show: fix --group value treated as regex problem

### <a name="rdbms"></a>RDBMS

* Bump the azure-mgmt-rdbms SDK version to 2.0.0
* az postgres private-endpoint-connection: manage postgres private endpoint connections
* az postgres private-link-resource: manage postgres private link resources
* az mysql private-endpoint-connection: manage mysql private endpoint connections
* az mysql private-link-resource: manage mysql private link resources
* az mariadb private-endpoint-connection: manage mariadb private endpoint connections
* az mariadb private-link-resource: manage mariadb private link resources
* Memperbarui Tes Endpoint Pribadi RDBMS

### <a name="sql"></a>SQL

* Sql midb Tambahkan: list-deleted, show-deleted, update-retention, show-retention
* (sql server create:) Menambahkan bendera 'Aktifkan' akses jaringan publik opsional 'Aktifkan'/'Nonaktifkan' ke server sql
* (sql server update:) membuat beberapa perubahan yang dihadapi pelanggan
* Menambahkan properti minimal_tls_version untuk MI dan SQL DB

### <a name="storage"></a>Penyimpanan

* az storage blob delete-batch: Bendera perilaku `--dryrun` buruk
* az penyimpanan akun jaringan-aturan add (perbaikan bug): menambahkan operasi harus idempotent
* az akun penyimpanan buat/perbarui: Tambahkan dukungan Preferensi Perutean
* Upgrade azure-mgmt-storage version to 8.0.0
* az storage container immutability create: add --allow-protected-append-write parameter
* az daftar sumber daya tautan pribadi akun penyimpanan: Tambahkan dukungan ke daftar sumber daya tautan pribadi untuk akun penyimpanan
* az akun penyimpanan private-endpoint-connection approve/reject/show/delete: Dukungan untuk mengelola koneksi endpoint pribadi
* az storage account blob-service-properties update: add --enable-restore-policy dan --restore-days
* az penyimpanan blob restore: Tambahkan dukungan untuk memulihkan rentang gumpalan

## <a name="february-18-2020"></a>Tanggal 18 Februari 2020

Versi 2.1.0

### <a name="acr"></a>ACR

* Menambahkan argumen `--expose-token` baru untuk `az acr login`
* Memperbaiki output yang salah dari `az acr task identity show -n Name -r Registry -o table`
* az acr login: Lemparkan CLIError jika ada kesalahan yang dikembalikan oleh perintah docker

### <a name="acs"></a>ACS

* aks buat/perbarui: tambahkan `--vnet-subnet-id` validasi

### <a name="aladdin"></a>Aladdin

* Parse menghasilkan contoh ke dalam perintah _help.py

### <a name="ams"></a>AMS

* Az ams adalah GA sekarang

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Merevisi pesan bantuan untuk mengecualikan filter kunci/label yang tidak didukung
* Menghapus tag pratinjau untuk sebagian besar perintah tidak termasuk identitas terkelola dan bendera fitur
* Menambahkan kunci yang dikelola pelanggan saat memperbarui toko

### <a name="appservice"></a>AppService

* az webapp list-runtimes: Perbaiki bug untuk list-runtimes
* Add az webapp|functionapp config ssl create
* Menambahkan dukungan untuk aplikasi fungsi v3 dan node 12

### <a name="arm"></a>ARM

* az pembuatan tugas kebijakan: Memperbaiki pesan kesalahan saat `--policy` parameter tidak valid
* az group deployment create: Fix "stat: path too long for Windows" error saat menggunakan file parameter besar.json

### <a name="backup"></a>Cadangan

* Memperbaiki alur pemulihan tingkat item di OLR
* Menambahkan pemulihan sebagai dukungan file untuk database SQL dan SAP

### <a name="compute"></a>Compute

* vm/vmss/availability-set update: add --ppg to allowing update proximityplacementgroup
* vmss create: add --data-disk-iops dan --data-disk-mbps
* az vm host: remove preview tag for `vm host` and `vm host group`
* [MELANGGAR PERUBAHAN] Perbaiki #10728: `az vm create`: buat subnet secara otomatis jika vnet ditentukan dan subnet tidak ada
* Meningkatkan ketahanan daftar gambar vm

### <a name="eventhub"></a>Eventhub

* Dukungan Azure Stack untuk profil 2019-03-01-hybrid

### <a name="keyvault"></a>Az.KeyVault

* az keyvault key create: menambahkan nilai `import` baru untuk parameter `--ops`
* az keyvault key list-versions: parameter `--id` dukungan untuk menentukan kunci
* Mendukung koneksi endpoint pribadi

### <a name="network"></a>Jaringan

* Bump to azure-mgmt-network 9.0.0
* az network private-link-service update/create: support --enable-proxy-protocol
* Menambahkan fitur Monitor V2 koneksi

### <a name="packaging"></a>Pengemasan

* [MELANGGAR PERUBAHAN] Drop dukungan untuk Python 2.7

### <a name="profile"></a>Profil

* Pratinjau: Menambahkan atribut `homeTenantId` baru dan `managedByTenants` ke akun langganan. Silakan jalankan `az login` kembali agar perubahan berlaku
* az login: Tampilkan peringatan saat langganan terdaftar dari lebih dari satu penyewa dan default ke yang pertama. Untuk memilih penyewa tertentu saat mengakses langganan ini, harap sertakan `--tenant``az login`

### <a name="role"></a>Peran

* az pembuatan tugas peran: Memperbaiki kesalahan yang menetapkan peran ke kepala layanan dengan menampilkan nama menghasilkan HTTP 400

### <a name="sql"></a>SQL

* Memperbarui cmdlet `az sql mi update` Instans Terkelola SQL dengan dua parameter baru: tingkat dan keluarga

### <a name="storage"></a>Penyimpanan

* [BREAKING CHANGE] `az storage account create`: Ubah jenis akun penyimpanan default ke StorageV2

## <a name="february-04-2020"></a>Tanggal 04 Februari 2020

Versi 2.0.81

### <a name="acs"></a>ACS

* Menambahkan dukungan untuk mengatur port yang dialokasikan keluar dan batas waktu idle pada penyeimbang beban standar
* Pembaruan ke API Version 2019-11-01

### <a name="acr"></a>ACR

* [MELANGGAR PERUBAHAN] `az acr delete` akan meminta
* [MELANGGAR PERUBAHAN] 'az acr task delete' akan meminta
* Menambahkan grup perintah baru 'az acr taskrun show/list/delete' for taskrun management

### <a name="aks"></a>AKS

* Setiap cluster mendapat prinsip layanan terpisah untuk meningkatkan isolasi.

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Mendukung impor/ekspor referensi keyvault dari/ke appservice
* Mendukung impor/ekspor semua label dari konfigurasi aplikasi ke konfigurasi aplikasi
* Memvalidasi nama kunci dan fitur sebelum mengatur dan mengimpor
* Mengekspos modifikasi sku untuk toko konfigurasi.
* Tambahkan grup perintah untuk identitas terkelola.

### <a name="appservice"></a>AppService

* Azure Stack: perintah permukaan di bawah profil 2019-03-01-hybrid
* functionapp: Menambahkan kemampuan untuk membuat aplikasi fungsi Java di Linux

### <a name="arm"></a>ARM

* Memperbaiki masalah #10246: `az resource tag` crash saat parameter `--ids` masuk adalah ID grup sumber daya
* Perbaiki masalah #11658: `az group export` perintah tidak mendukung `--query` dan `--output` parameter
* Memperbaiki masalah #10279: Kode `az group deployment validate` keluar adalah 0 ketika verifikasi gagal
* Memperbaiki masalah #9916: Meningkatkan pesan kesalahan konflik antara tag dan kondisi filter lainnya untuk `az resource list` perintah
* Menambahkan parameter `--managed-by` baru untuk mendukung menambahkan informasi terkelola Untuk perintah `az group create`

### <a name="azure-red-hat-openshift"></a>Azure Red Hat OpenShift

* Menambahkan `monitor` subkelompok untuk mengelola pemantauan Log Analytics di cluster Azure Red Hat OpensShift

### <a name="botservice"></a>Layanan Bot

* Memperbaiki masalah #11697: `az bot create` tidak idempoten
* Mengubah tes koreksi nama untuk berjalan hanya dalam mode Langsung

### <a name="cdn"></a>CDN

* Menambahkan dukungan untuk aturan Fiturengine
* Menambahkan grup perintah baru 'aturan endpoint cdn' untuk mengelola aturan
* Update azure-mgmt-cdn version to 4.0.0 to use api version 2019-04-15

### <a name="deployment-manager"></a>Deployment Manager

* Tambahkan operasi daftar untuk semua sumber daya.
* Tingkatkan sumber daya langkah untuk jenis langkah baru.
* Update azure-mgmt-deploymentmanager package to use version 0.2.0.

### <a name="iot"></a>IoT

* Deprecate 'IoT hub Job' perintah.

### <a name="iot-central"></a>IoT Pusat

* Mendukung pembuatan/pembaruan aplikasi dengan nama sku baru ST0, ST1, ST2.

### <a name="key-vault"></a>Key Vault

* Tambahkan perintah `az keyvault key download` baru untuk mengunduh kunci.

### <a name="misc"></a>Misc

* Perbaiki #6371: Mendukung nama berkas dan penyelesaian variabel lingkungan di Bash

### <a name="network"></a>Jaringan

* Perbaiki #2092: az network dns record-set add/remove: tambahkan peringatan saat kumpulan rekor tidak ditemukan. Di masa depan, argumen tambahan akan didukung untuk mengkonfirmasi pembuatan otomatis ini.

### <a name="policy"></a>Kebijakan

* Menambahkan perintah `az policy metadata` baru untuk mengambil sumber daya metadata kebijakan yang kaya
* `az policy remediation create`Menentukan apakah kepatuhan harus dievaluasi ulang sebelum remediasi dengan `--resource-discovery-mode` parameter

### <a name="profile"></a>Profil

* `az account get-access-token`: Tambahkan `--tenant` parameter untuk mendapatkan token untuk penyewa secara langsung, tak perlu menentukan langganan

### <a name="rbac"></a>RBAC

* [MELANGGAR PERUBAHAN] Perbaiki #11883: `az role assignment create`: ruang lingkup kosong akan menimbulkan kesalahan

### <a name="security"></a>Keamanan

* Tambahkan perintah `az atp show` baru dan `az atp update` untuk melihat dan mengelola pengaturan perlindungan ancaman tingkat lanjut untuk akun penyimpanan.

### <a name="sql"></a>SQL

* `sql dw create`: deprecate `--zone-redundant` dan `--read-replica-count` parameter. Parameter ini tidak berlaku untuk DataWarehouse.
* [BREAKING CHANGE] `az sql db create`: Hapus "WideWorldImportersStd" dan "WideWorldImportersFull" sebagai nilai yang diizinkan didokumentasikan untuk "az sql db create --sample-name". Database sampel ini akan selalu menyebabkan penciptaan gagal.
* Tambahkan perintah `sql db classification show/list/update/delete` Baru dan `sql db classification recommendation list/enable/disable` untuk mengelola klasifikasi sensitivitas untuk database SQL.
* `az sql db audit-policy`Memperbaiki tindakan dan grup audit kosong

### <a name="storage"></a>Penyimpanan

* Tambahkan grup `az storage share-rm` perintah baru untuk menggunakan penyedia sumber daya Microsoft.Storage untuk operasi manajemen berbagi file Azure.
* Memperbaiki masalah #11415: kesalahan izin untuk `az storage blob update`
* Integrasikan Azcopy 10.3.3 dan dukung Win32.
* `az storage copy`: Tambahkan `--include-path`, `--include-pattern`, dan`--exclude-pattern` `--exclude-path` parameter
* `az storage remove`: Perubahan `--inlcude` dan `--exclude` parameter untuk `--include-path`, `--include-pattern`, `--exclude-path` dan`--exclude-pattern` parameter
* `az storage sync`: Tambahkan `--include-pattern`, `--exclude-path` dan`--exclude-pattern` parameter

### <a name="servicefabric"></a>ServiceFabric

* Tambahkan perintah baru untuk mengelola aplikasi dan layanan.

## <a name="january-13-2020"></a>13 Januari 2020

Versi 2.0.80

### <a name="compute"></a>Compute

* pembaruan disk: Tambahkan --disk-encryption-set dan --encryption-type
* snapshot create/update: Tambahkan --disk-encryption-set dan --encryption-type

### <a name="storage"></a>Penyimpanan

* Upgrade azure-mgmt-storage version to 7.1.0
* `az storage account create`: Menambahkan `--encryption-key-type-for-table` dan `--encryption-key-type-for-queue` mendukung Layanan Enkripsi Tabel dan Antrian

## <a name="january-07-2020"></a>Tanggal 07 Januari 2020

Versi 2.0.79

### <a name="acr"></a>ACR

* [MELANGGAR PERUBAHAN] Hapus parameter '--os' untuk 'acr build', 'acr task create/update', 'acr run', dan 'acr pack'. Gunakan '--platform' sebagai gantinya.

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan dukungan untuk mengimpor/mengekspor bendera fitur
* Tambahkan perintah baru 'az appconfig kv set-keyvault' untuk membuat referensi keyvault
* Mendukung berbagai konvensi penamaan saat mengekspor bendera fitur ke file

### <a name="appservice"></a>AppService

* Memperbaiki masalah #7154: Memperbarui dokumentasi untuk perintah <> menggunakan tanda centang kembali alih-alih kutipan tunggal
* Perbaiki masalah #11287: webapp up: Secara default buat aplikasi yang dibuat menggunakan 'harus 'SSL diaktifkan'
* Memperbaiki masalah #11592: Tambahkan az webapp up flag for html static sites

### <a name="arm"></a>ARM

* Perbaiki `az resource tag`: Layanan Pemulihan Tag Vault tidak dapat diperbarui

### <a name="backup"></a>Cadangan

* Menambahkan perintah baru 'perlindungan cadangan undelete' untuk mengaktifkan fitur penghapusan lunak untuk beban kerja IaasVM
* Menambahkan parameter baru '--soft-delete-feature-state' untuk mengatur perintah properti cadangan
* Menambahkan dukungan pengecualian disk untuk beban kerja IaasVM

### <a name="compute"></a>Compute

* Perbaiki `vm create` kegagalan di profil Azure Stack.
* vm monitor metrics tail/list-definitions: support query metric dan list definitions for a vm.
* Tambahkan tindakan perintah reapply baru untuk az vm

### <a name="hdinsight"></a>HDInsight

* Dukungan untuk membuat cluster Kafka dengan Kafka Rest Proxy
* Upgrade azure-mgmt-hdinsight to 1.3.0

### <a name="misc"></a>Misc.

* Menambahkan perintah `az version show` pratinjau untuk memperlihatkan versi modul dan ekstensi Azure CLI dalam format JSON secara default atau format yang dikonfigurasi oleh --output

### <a name="event-hubs"></a>Event Hubs

* [MELANGGAR PERUBAHAN] Hapus opsi status 'ReceiveDisabled' dari perintah 'az eventhubs eventhub update' dan 'az eventhubs eventhub create'. Opsi ini tidak berlaku untuk entitas Event Hub.

### <a name="service-bus"></a>Service Bus

* [MELANGGAR PERUBAHAN] Hapus opsi status 'ReceiveDisabled' dari perintah 'az servicebus topic create', 'az servicebus topic update', 'az servicebus queue create', dan 'az servicebus queue update'. Opsi ini tidak berlaku untuk topik dan antrian Bus Layanan.

### <a name="rbac"></a>RBAC

* Perbaiki #11712: `az ad app/sp show` tidak mengembalikan kode keluar 3 ketika aplikasi atau prinsipal layanan tidak ada

### <a name="storage"></a>Penyimpanan

* `az storage account create`: Hapus bendera pratinjau untuk parameter --enable-hierarchical-namespace
* Update azure-mgmt-storage version to 7.0.0 to use api version 2019-06-01
* Tambahkan parameter `--enable-delete-retention` baru dan `--delete-retention-days` untuk mendukung pengelolaan kebijakan penghapusan retensi untuk properti blob-service-akun penyimpanan.

## <a name="december-17-2019"></a>17 Desember 2019

2.0.78

### <a name="acr"></a>ACR

* Menambahkan dukungan Konteks lokal dalam menjalankan tugas acr

### <a name="acs"></a>ACS

* [BREAKING CHANGEaz] openshift create: ganti nama `--workspace-resource-id` menjadi `--workspace-id`.

### <a name="ams"></a>AMS

* Perintah perlihatkan yang diperbarui untuk mengembalikan 3 saat sumber daya tidak ditemukan

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Memperbaiki bug saat menambahkan versi api untuk meminta url. Solusi yang ada tidak bekerja dengan pagination.
* Menambahkan dukungan untuk menampilkan bahasa selain bahasa Inggris sebagai layanan backend kami mendukung unicode untuk globalisasi.

### <a name="appservice"></a>AppService

* Fixed issue #11217: webapp: az webapp config ssl upload should support parameter slot
* Masalah tetap #10965: Kesalahan: Nama tidak bisa kosong. Izinkan hapus dengan ip_address dan subnet
* Menambahkan dukungan untuk mengimpor sertifikat dari Key Vault `az webapp config ssl import`

### <a name="arm"></a>ARM

* Paket azure-mgmt-resource yang diperbarui untuk menggunakan 6.0.0
* Dukungan Penyewa Silang untuk `az group deployment create` perintah dengan menambahkan parameter baru `--aux-subs`
* Menambahkan parameter `--metadata` baru untuk mendukung penambahan informasi metadata untuk definisi yang ditetapkan kebijakan.

### <a name="backup"></a>Cadangan

* Menambahkan dukungan Cadangan untuk beban kerja SQL dan SAP Hana.

### <a name="botservice"></a>Layanan Bot

* [Melanggar perubahan] Hapus bendera '-version' dari perintah pratinjau 'az bot create'. Hanya bot SDK v4 yang didukung.
* Menambahkan pemeriksaan ketersediaan nama untuk 'az bot create'.
* Menambahkan dukungan untuk memperbarui URL ikon untuk bot melalui 'az bot update'.
* Menambahkan dukungan untuk memperbarui saluran Direct Line melalui 'az bot directline update'.
* Menambahkan dukungan bendera '--enable-enhanced-auth' ke 'az bot directline create'.
* Grup perintah berikut adalah GA dan tidak dalam pratinjau: 'az bot authsetting'.
* Perintah berikut di 'az bot' adalah GA dan tidak dalam pratinjau: 'create', 'prepare-deploy', 'show', 'delete', 'update'.
* Tetap 'az bot prepare-deploy' mengubah nilai '--proj-file-path' ke huruf kecil (misalnya "Test.csproj" menjadi "test.csproj").

### <a name="compute"></a>Compute

* vmss create/update: Ditambahkan --scale-in-policy, yang memutuskan mesin virtual mana yang dipilih untuk dihapus saat VMSS diskalakan.
* vm/vmss update: Ditambahkan --priority.
* vm/vmss update: Ditambahkan --max-price.
* Menambahkan grup perintah set disk-enkripsi (buat, perlihatkan, perbarui, hapus, daftar).
* pembuatan disk: Ditambahkan --encryption-type dan --disk-encryption-set.
* vm/vmss create: Added --os-disk-encryption-set dan --data-disk-encryption-sets.

### <a name="core"></a>Core

* Dukungan yang dihapus untuk Python 3.4
* Pasang survei HaTS dalam beberapa perintah

### <a name="dls"></a>DLS

* Versi sdk ADLS yang diperbarui (0.0.48).

### <a name="install"></a>Instal

* Instal python dukungan skrip 3.8

### <a name="iot"></a>IoT

* [MELANGGAR PERUBAHAN] Dihapus --failover-region parameter dari manual-failover. Sekarang akan gagal ke wilayah sekunder geo-paired yang ditugaskan.

### <a name="key-vault"></a>Key Vault

* Tetap #8095: `az keyvault storage remove`: meningkatkan pesan bantuan
* Tetap #8921: `az keyvault key/secret/certificate list/list-deleted/list-versions`: memperbaiki bug validasi pada parameter `--maxresults`
* Tetap #10512: `az keyvault set-policy`: meningkatkan pesan kesalahan ketika tidak ada `--object-id`, `--spn` atau `--upn` ditentukan
* Tetap #10846: `az keyvault secret show-deleted`: ketika `--id` ditentukan, `--name/-n` tidak diperlukan
* Tetap #11084: `az keyvault secret download`: meningkatkan pesan bantuan parameter `--encoding`

### <a name="network"></a>Jaringan

* az network application-gateway probe: Opsi menambahkan dukungan --port untuk menentukan port untuk menyelidi server backend saat membuat dan memperbarui
* az network application-gateway url-path-map create/update: bug fix for `--waf-policy`
* az network application-gateway: Menambahkan dukungan `--rewrite-rule-set`
* az network list-service-aliases: Menambahkan alias layanan daftar dukungan yang dapat digunakan untuk Kebijakan Endpoint Layanan
* az network dns zone import: Menambahkan dukungan .@ dalam nama catatan

### <a name="packaging"></a>Pengemasan

* Menambahkan build tepi belakang untuk pemasangan pip
* Menambahkan paket Ubuntu eoan

### <a name="policy"></a>Kebijakan

* Menambahkan dukungan untuk Policy API versi 2019-09-01.
* az kebijakan set-definition: Kelompok dukungan tambahan dalam kebijakan menetapkan definisi dengan `--definition-groups` parameter

### <a name="redis"></a>Redis

* Menambahkan param `--replicas-per-master` pratinjau ke `az redis create` perintah
* Diperbarui azure-mgmt-redis dari 6.0.0 to 7.0.0rc1

### <a name="servicefabric"></a>ServiceFabric

* Diperbaiki dalam logika tambahkan tipe node termasuk #10963: Menambahkan tipe node baru dengan tingkat daya tahan Emas akan selalu membuang kesalahan CLI
* Pembaruan ServiceFabricNodeVmExt version ke 1.1 dalam templat pembuatan

### <a name="sql"></a>SQL

* Menambahkan parameter "--read-scale" dan "--read-replicas" ke perintah buat dan perbarui sql db, untuk mendukung manajemen skala baca.

### <a name="storage"></a>Penyimpanan

* GA Rilis File Besar Berbagi properti untuk membuat akun penyimpanan dan memperbarui perintah
* GA Rilis Dukungan Token SAS Delegasi Pengguna
* Menambahkan perintah `az storage account blob-service-properties show` baru dan `az storage account blob-service-properties update --enable-change-feed` mengelola properti layanan gumpalan untuk akun penyimpanan.
* [COMING BREAKING CHANGE] `az storage copy`: `*` karakter tidak lagi didukung sebagai wildcard di URL, tetapi parameter baru - termasuk-pola dan --exclude-pattern akan ditambahkan dengan `*` dukungan wildcard.
* Masalah tetap #11043: Menambahkan dukungan untuk menghapus seluruh kontainer/berbagi dalam `az storage remove` perintah

## <a name="november-26-2019"></a>Tanggal 26 November 2019

Versi 2.0.77

### <a name="acr"></a>ACR

* Parameter usang `--branch` dari acr task create/update

### <a name="azure-red-hat-openshift"></a>Azure Red Hat OpenShift

* Menambahkan `--workspace-resource-id` bendera untuk memungkinkan pembuatan cluster Azure Red Hat Openshift dengan pemantauan
* Ditambahkan `monitor_profile` untuk membuat cluster Azure Red Hat OpenShift dengan pemantauan

### <a name="aks"></a>AKS

* Menambahkan operasi rotasi sertifikat cluster dukungan yang ditambahkan menggunakan "az aks rotate-certs".

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan dukungan untuk menggunakan ":" untuk `as az appconfig kv import` pemisah
* Masalah tetap untuk mencantumkan nilai kunci dengan beberapa label termasuk label null.
* Updated management plane sdk, azure-mgmt-appconfiguration, to version 0.3.0.

### <a name="appservice"></a>AppService

* Fixed issue #11100: AttributeError for az webapp up when create service plan
* Az webapp up: Memaksa pembuatan atau penyebaran ke situs untuk bahasa yang didukung, tidak ada default yang digunakan.
* Menambahkan dukungan untuk Lingkungan Layanan Aplikasi: az appservice ase show | daftar | | alamat daftar daftar-rencana | membuat | | perbarui menghapus

### <a name="backup"></a>Cadangan

* Masalah tetap di az backup policy list-associated-items. Menambahkan parameter BackupManagementType opsional.

### <a name="compute"></a>Compute

* Versi API yang ditingkatkan dari komputasi, disk, snapshot ke 2019-07-01
* vmss create: Improvement for --orchestration-mode
* definisi gambar sig membuat: Ditambahkan - os-state untuk memungkinkan menentukan apakah mesin virtual yang dibuat di bawah gambar ini 'Digeneralisasi' atau 'Khusus'
* sig image-definition create: Ditambahkan --hyper-v-generation untuk memungkinkan menentukan generasi hypervisor
* sig image-version create: Dukungan tambahan --os-snapshot dan --data-snapshots
* gambar membuat: Ditambahkan --data-disk-caching untuk memungkinkan menentukan pengaturan caching disk data
* Upgrade Python Compute SDK ke 10.0.0
* vm/vmss create: Menambahkan 'Spot' ke properti enum 'Priority'
* [Melanggar perubahan] Berganti nama menjadi parameter '--max-billing' menjadi '--max-price', baik untuk VM dan VMSS, agar konsisten dengan cmdlet Swagger dan Powershell
* vm monitor log show: Menambahkan dukungan untuk query log over linked log analytics workspace.

### <a name="iot"></a>IoT

* Perbaiki #2531: Menambahkan argumen kenyamanan untuk pembaruan hub.
* Perbaiki #8323: Menambahkan parameter yang hilang untuk membuat titik akhir kustom penyimpanan.
* Memperbaiki bug regresi: Mengembalikan perubahan yang menimpa titik akhir penyimpanan default.

### <a name="key-vault"></a>Key Vault

* Tetap # 11121: Saat menggunakan `az keyvault certificate list`, lewat `--include-pending` sekarang tidak memerlukan nilai `true` atau `false`

### <a name="netappfiles"></a>NetAppFiles

* Upgrade azure-mgmt-netapp ke 0.7.0 yang mencakup beberapa properti volume tambahan yang terkait dengan operasi replikasi yang akan datang

### <a name="network"></a>Jaringan

* application-gateway waf-config: usang
* app-gateway waf-policy: Menambahkan subkelompok aturan terkelola untuk mengelola set aturan terkelola dan aturan pengecualian
* app-gateway waf-policy: Menambahkan pengaturan kebijakan subkelompok untuk mengelola konfigurasi global kebijakan waf
* [MELANGGAR CHANGE] application-gateway waf-policy: Berganti nama menjadi aturan subkelompok menjadi aturan kustom
* application-gateway http-listener: Ditambahkan --firewall-policy saat dibuat
* application-gateway url-path-map rule: Ditambahkan --firewall-policy saat membuat

### <a name="packaging"></a>Pengemasan

* Menulis ulang pembungkus az dengan Python
* Menambahkan dukungan untuk Python 3.8
* Diubah menjadi paket Python 3 untuk RPM

### <a name="profile"></a>Profil

* Kesalahan yang dipoles saat berjalan `az login -u {} -p {}` dengan akun Microsoft
* Dipoles `SSLError` saat berjalan `az login` di belakang proxy dengan sertifikat root yang ditandatangani sendiri
* Tetap # 10578: `az login` menggantung ketika lebih dari satu kali diluncurkan pada saat yang sama pada Windows atau WSL
* Tetap #11059: `az login --allow-no-subscriptions` gagal jika ada langganan di penyewa
* Tetap #11238: Setelah mengganti nama langganan, masuk dengan MSI akan menghasilkan langganan yang sama muncul dua kali

### <a name="rbac"></a>RBAC

* Tetap #10996: Kesalahan Polandia untuk `--force-change-password-next-login` `az ad user update` saat `--password` tidak ditentukan

### <a name="redis"></a>Redis

* Tetap #2902: Hindari pengaturan konfigurasi memori saat memperbarui cache SKU Dasar

### <a name="reservations"></a>Reservasi

* Versi SDK yang Ditingkatkan ke 0.6.0
* Menambahkan info detail billingplan setelah menelepon Get-Gatalogs
* Menambahkan perintah `az reservations reservation-order calculate` baru untuk menghitung harga untuk reservasi
* Menambahkan perintah `az reservations reservation-order purchase` baru untuk membeli reservasi baru

### <a name="rest"></a>Sisanya
* Diubah `az rest` menjadi GA

### <a name="sql"></a>SQL

* Diperbarui azure-mgmt-sql to version 0.15.0.

### <a name="storage"></a>Penyimpanan

* pembuatan akun penyimpanan: Ditambahkan --enable-hierarchical-namespace untuk mendukung semantik sistem file dalam layanan gumpalan.
* Menghapus pengecualian yang tidak terkait dari pesan kesalahan
* Memperbaiki masalah dengan pesan kesalahan yang salah "Anda tidak memiliki izin yang diperlukan untuk melakukan operasi ini." ketika diblokir oleh aturan jaringan atau AuthenticationFailed.

## <a name="november-4-2019"></a>4 November 2019

Versi 2.0.76

### <a name="acr"></a>ACR

* Menambahkan parameter `--pack-image-tag` pratinjau ke perintah `az acr pack build`.
* Menambahkan dukungan untuk memungkinkan audit dalam membuat registri
* Menambahkan dukungan untuk RBAC repository-scoped

### <a name="aks"></a>AKS

* Ditambahkan `--enable-cluster-autoscaler`, `--min-count` dan `--max-count` ke `az aks create` perintah, yang memungkinkan autoscaler cluster untuk kolam node.
* Menambahkan bendera di atas serta `--update-cluster-autoscaler` dan `--disable-cluster-autoscaler` ke `az aks update` perintah, memungkinkan pembaruan untuk mengelompokkan autoscaler.

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan grup perintah fitur konfigurasi aplikasi untuk mengelola bendera fitur yang disimpan dalam Konfigurasi Aplikasi.
* Bug minor tetap untuk ekspor appconfig kv ke perintah file. Berhenti membaca konten file dest selama ekspor.

### <a name="appservice"></a>AppService

* `az appservice plan create`: Menambahkan dukungan untuk mengatur 'persitescaling' pada buat rencana layanan aplikasi.
* Memperbaiki masalah di mana operasi pengikat ssl konfigurasi webapp menghapus tag yang ada dari sumber daya
* Menambahkan `--build-remote` bendera untuk `az functionapp deployment source config-zip` mendukung tindakan pembuatan jarak jauh selama penyebaran aplikasi fungsi.
* Mengubah versi node default pada aplikasi fungsi menjadi ~10 untuk Windows
* Menambahkan `--runtime-version` properti ke `az functionapp create`

### <a name="arm"></a>ARM

* `az deployment/group deployment validate`: Menambahkan `--handle-extended-json-format` parameter untuk mendukung multiline dan komentar di template json saat penyebaran.
* Bumped azure-mgmt-resource to 2019-07-01

### <a name="backup"></a>Cadangan

* Menambahkan dukungan cadangan AzureFiles

### <a name="compute"></a>Compute

* `az vm create`: Menambahkan peringatan ketika menentukan jaringan yang dipercepat dan NIC yang ada bersama-sama.
* `az vm create`Ditambahkan `--vmss` untuk menentukan set skala mesin virtual yang ada bahwa mesin virtual harus ditugaskan untuk.
* `az vm/vmss create`Menambahkan salinan lokal gambar alias file sehingga dapat diakses di lingkungan jaringan terbatas.
* `az vmss create``--orchestration-mode` Ditambahkan untuk menentukan bagaimana mesin virtual dikelola oleh set skala.
* `az vm/vmss update`: Ditambahkan `--ultra-ssd-enabled` untuk memungkinkan memperbarui pengaturan ultra SSD.
* [BREAKING CHANGE] `az vm extension set`: Bug tetap di mana pengguna tidak dapat mengatur ekstensi pada VM dengan `--ids`.
* Menambahkan perintah `az vm image terms accept/cancel/show` baru untuk mengelola istilah gambar Azure Marketplace.
* VmAccessForLinux yang diperbarui ke versi 1.5

### <a name="cosmosdb"></a>CosmosDB

* [BREAKING CHANGE] `az sql container create`: Diubah `--partition-key-path` ke parameter yang diperlukan
* [BREAKING CHANGE] `az gremlin graph create`: Diubah `--partition-key-path` ke parameter yang diperlukan
* `az sql container create`: Ditambahkan `--unique-key-policy` dan `--conflict-resolution-policy`
* `az sql container create/update`: Memperbarui `--idx` skema default
* `gremlin graph create`: Ditambahkan `--conflict-resolution-policy`
* `gremlin graph create/update`: Memperbarui `--idx` skema default
* Kesalahan ketik tetap dalam pesan bantuan
* database: Menambahkan informasi deprecation
* pengumpulan: Menambahkan informasi deprecation

### <a name="iot"></a>IoT

* Menambahkan tipe sumber perutean baru: DigitalTwinChangeEvents
* Fitur yang hilang tetap di `az iot hub create`

### <a name="key-vault"></a>Key Vault

* Memperbaiki kesalahan tak terduga saat berkas sertifikat tidak ada
* Tetap `az keyvault recover/purge` tidak berfungsi

### <a name="netappfiles"></a>NetAppFiles

* Upgrade azure-mgmt-netapp ke 0.6.0 to use API version 2019-07-01. Versi API baru ini meliputi:

    - Penciptaan volume `--protocol-types` menerima sekarang "NFSv4.1" bukan "NFSv4"
    - Properti kebijakan ekspor volume sekarang bernama 'nfsv41' bukan 'nfsv4'
    - Volume `--creation-token` yang diganti namanya menjadi `--file-path`
    - Tanggal pembuatan snapshot sekarang bernama hanya 'dibuat'

### <a name="network"></a>Jaringan

* `az network private-dns link vnet create/update`: Mendukung penautan jaringan virtual lintas penyewa.
* [MELANGGAR PERUBAHAN] `az network vnet subnet list`: Berubah `--resource-group` dan `--vnet-name` harus diperlukan sekarang.
* `az network public-ip prefix create`Menambahkan dukungan untuk menentukan versi alamat IP (IPv4, IPv6) saat pembuatan
* Bumped azure-mgmt-network to 7.0.0 dan api-version to 2019-09-01
* `az network vrouter`: Menambahkan dukungan untuk layanan baru router virtual dan router virtual mengintip
* `az network express-route gateway connection`: Menambahkan dukungan untuk `--internet-security`

### <a name="profile"></a>Profil

* Tetap `az account get-access-token --resource-type ms-graph` tidak berfungsi
* Menghapus peringatan dari `az login`

### <a name="rbac"></a>RBAC

* Tetap `az ad app update --id {} --display-name {}` tidak bekerja

### <a name="servicefabric"></a>ServiceFabric

* `az sf cluster create`Memperbaiki masalah dengan memodifikasi linux kain layanan dan windows template.json menghitung vmss dari standar ke disk yang dikelola

### <a name="sql"></a>SQL

* Ditambahkan`--compute-model`, `--auto-pause-delay`, dan `--min-capacity` parameter untuk mendukung operasi CRUD untuk penawaran SQL Database baru: Model komputasi tanpa server.

### <a name="storage"></a>Penyimpanan

* `az storage account create/update`: Menambahkan --enable-files-adds parameter dan Azure Active Directory Properties Argument group untuk mendukung Azure Files Active Directory Domain Service Authentication
* Diperluas `az storage account keys list/renew` untuk mendukung daftar atau regenerasi kunci kerberos dari akun penyimpanan.

## <a name="october-15-2019"></a>Tanggal 15 Oktober 2019

Versi 2.0.75

### <a name="aks"></a>AKS

* Mengubah `--load-balancer-sku` nilai default menjadi `standard` jika didukung oleh versi kubernetes
* Mengubah `--vm-set-type` nilai default menjadi `virtualmachinescalesets` jika didukung oleh versi kubernetes

### <a name="ams"></a>AMS

* [MELANGGAR PERUBAHAN] Mengubah nama `job start` menjadi `job create`
* [MELANGGAR PERUBAHAN] `--ask` Mengubah parameter `content-key-policy create` untuk menggunakan string heks 32 karakter, bukan UTF8

### <a name="appservice"></a>AppService

* Menambahkan perintah `webapp config access-restriction show|set|add|remove`
* Menambahkan penanganan kesalahan yang lebih baik ke `webapp up`
* Menambahkan dukungan untuk `Isolated` SKU untuk `appservice plan update`

### <a name="arm"></a>ARM

* Menambahkan `--handle-extended-json-format` parameter `deployment create` untuk mendukung multiline dan komentar dalam template json

### <a name="compute"></a>Compute

* Menambahkan `--enable-agent` parameter ke `vm create`
* Diubah `vm create` untuk menggunakan SKU IP publik standar secara otomatis saat menggunakan zona
* Diubah `vm create` untuk secara otomatis membuat nama komputer yang valid untuk VM jika tidak ada yang disediakan
* Menambahkan `--computer-name-prefix` parameter untuk `vmss create` mendukung awalan nama komputer kustom mesin virtual di VMSS
* Menambahkan `--workspace` parameter untuk `vm create` mengaktifkan ruang kerja analisis log secara otomatis
* Galeri yang diperbarui versi API ke 2019-07-01

### <a name="core"></a>Core

* Menambahkan pemeriksaan sintaks untuk `--set` parameter dalam perintah pembaruan generik

### <a name="iot"></a>IoT

* Memperbaiki masalah di mana `iot hub show` salah akan kesalahan dengan "sumber daya tidak ditemukan"

### <a name="monitor"></a>Monitor

* Menambahkan dukungan untuk CRUD ke `monitor log-analytics workspace`

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk linking virtual cross-tenant ke `network private-dns link vnet [create|update]`
* [MELANGGAR PERUBAHAN] Diubah `network vnet subnet list` menjadi kebutuhan `--resource-group` dan `--vnet-name` parameter

### <a name="sql"></a>SQL

* Menambahkan perintah ke `sql mi ad-admin` dukungan tersebut mengatur administrator AAD pada instans terkelola

### <a name="storage"></a>Penyimpanan

* Menambahkan `--preserve-s2s-access-tier` parameter `storage copy` untuk mempertahankan tingkat akses selama salinan layanan ke layanan
* Menambahkan `--enable-large-file-share` parameter untuk `storage account [create|update]` mendukung berbagi file besar untuk akun penyimpanan

## <a name="september-24-2019"></a>24 September 2019

Versi 2.0.74

### <a name="acr"></a>ACR

* Menambahkan parameter yang diperlukan `--type` untuk `acr config retention update`
* [MELANGGAR PERUBAHAN] Parameter yang diganti namanya `--name -n` diubah menjadi `--registry -r ` grup `acr config` perintah

### <a name="aks"></a>AKS

* Menambahkan `--load-balancer-sku` parameter ke `aks create` perintah, yang memungkinkan untuk membuat cluster AKS dengan SLB
* Ditambahkan `--load-balancer-managed-outbound-ip-count`, `--load-balancer-outbound-ips` dan `--load-balancer-outbound-ip-prefixes` parameter untuk `aks [create|update]` perintah, yang memungkinkan untuk memperbarui profil load balancer dari cluster AKS dengan SLB
* Menambahkan `--vm-set-type` parameter ke `aks create` perintah, yang memungkinkan untuk menentukan jenis vm dari Cluster AKS (vmas atau vmss)

### <a name="arm"></a>ARM

* Menambahkan `--handle-extended-json-format` parameter untuk `group deployment create` perintah untuk mendukung multiline dan komentar di template json

### <a name="compute"></a>Compute

* Menambahkan `--terminate-notification-time` parameter ke `vmss [create|update]` perintah untuk mendukung penghentian konfigurasi acara terjadwal
* Menambahkan `--enable-terminate-notification` parameter ke `vmss update` perintah untuk mendukung penghentian konfigurasi acara terjadwal
* Menambahkan `--priority,` `--eviction-policy,` `--max-billing` parameter ke perintah `[vm|vmss] create`
* Diubah `disk create` untuk memungkinkan menentukan ukuran yang tepat dari pengunggahan disk
* Menambahkan dukungan untuk snapshot inkremental untuk disk terkelola ke `snapshot create`

### <a name="cosmos-db"></a>Cosmos DB

* Menambahkan `--type <key-type>` parameter ke `cosmosdb keys list` perintah untuk memperlihatkan kunci, hanya membaca kunci atau string koneksi
* Perintah tambahan `cosmosdb keys regenerate`
* [USANG] `cosmosdb list-connection-strings`Usang, `cosmosdb regenerate-key` dan `cosmosdb list-read-only-keys` perintah

### <a name="eventgrid"></a>EventGrid

* Memperbaiki teks bantuan titik akhir untuk merujuk ke parameter yang tepat

### <a name="key-vault"></a>Key Vault

* Masalah tetap di mana masuk dengan penyewa (`login -t`) dapat menyebabkan `keyvault create` gagal

### <a name="monitor"></a>Monitor

* Masalah tetap di mana `:` karakter tidak diizinkan dalam `--condition` argumen `monitor metrics alert create`

### <a name="policy"></a>Kebijakan

* Menambahkan dukungan untuk Policy API versi 2019-06-01
* Menambahkan `--enforcement-mode` parameter ke `policy assignment create` perintah

### <a name="storage"></a>Penyimpanan

* Menambahkan `--blob-type` parameter ke `az storage copy` perintah

## <a name="september-10-2019"></a>10 September 2019

### <a name="acr"></a>ACR

* Menambahkan grup `acr config retention` perintah untuk mengonfigurasi kebijakan retensi

### <a name="aks"></a>AKS

* Menambahkan dukungan untuk integrasi ACR dengan perintah berikut:
  * Menambahkan `--attach-acr` parameter untuk `aks [create|update]` melampirkan ACR ke klaster AKS
  * Menambahkan `--detach-acr` parameter untuk `aks update` melepaskan ACR dari klaster AKS

### <a name="arm"></a>ARM

* Diperbarui untuk menggunakan API versi 2019-05-10

### <a name="batch"></a>Batch

* Menambahkan pengaturan konfigurasi JSON baru ke `--json-file` untuk `batch pool create`:
  * Ditambahkan `MountConfigurations` untuk tunggangan sistem file (lihat [Meminta Badan](/rest/api/batchservice/pool/add#request-body) untuk detail)
  * Menambahkan properti `publicIPs` `NetworkConfiguration` opsional untuk IP publik di kolam renang (lihat [Meminta Badan](/rest/api/batchservice/pool/add#request-body) untuk detailnya)
* Menambahkan dukungan untuk galeri gambar bersama ke `--image`
* [MELANGGAR PERUBAHAN] Mengubah nilai `--start-task-wait-for-success` `batch pool create` default menjadi `true`
* [MELANGGAR PERUBAHAN] Mengubah nilai default untuk `Scope` `AutoUserSpecification` selalu menjadi Pool (berada `Task` di node Windows, `Pool` pada node Linux)
  * Argumen ini hanya dapat diatur dari konfigurasi JSON dengan `--json-file`

### <a name="hdinsight"></a>HDInsight

* Rilis GA
* [MELANGGAR PERUBAHAN] Mengubah parameter `--workernode-count/-c` yang `az hdinsight resize` diperlukan.

### <a name="key-vault"></a>Key Vault

* Masalah tetap di mana subnet tidak dapat dihapus dari aturan jaringan
* Masalah tetap di mana subnet duplikat dan alamat IP dapat ditambahkan ke aturan jaringan

### <a name="network"></a>Jaringan

* Menambahkan `--interval` parameter untuk `network watcher flow-log` mengatur nilai interval analisis lalu lintas
* Ditambahkan `network application-gateway identity` untuk mengelola identitas gateway
* Menambahkan dukungan untuk mengatur Key Vault ID ke `network application-gateway ssl-cert`
* Ditambahkan `network express-route peering peer-connection [show|list]`

### <a name="policy"></a>Kebijakan

* Diperbarui untuk menggunakan API versi 2019-01-01

## <a name="august-27-2019"></a>Tanggal 27 Agustus 2019

Versi 2.0.72

### <a name="acr"></a>ACR

* [MELANGGAR PERUBAHAN] Dukungan yang dihapus untuk `classic` SKU

### <a name="api-management"></a>API Management

* [PREVIEW] Menambahkan `apim` grup perintah

### <a name="appservice"></a>AppService

* Memperbaiki masalah dengan `webapp webjob continuous start` perintah saat menentukan slot
* Diubah `webapp up` untuk mendeteksi `env` folder dan menghapusnya dari file yang digunakan untuk penyebaran

### <a name="keyvault"></a>Keyvault

* Memperbaiki bug dalam `keyvault secret set` argumen yang dilempah `--expires`

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk alamat IPv6 ke `--private-ip-address-version` argumen
* Menambahkan perintah `network private-endpoint [create|update|list-types]` baru untuk manajemen endpoint pribadi
* Menambahkan grup perintah `network private-link-service`
* Ditambahkan `--private-endpoint-network-policies` dan `--private-link-service-network-policies` argumen untuk `network vnet subnet update`

### <a name="rbac"></a>RBAC

* Masalah tetap dengan `ad app update --homepage` di mana beranda tidak akan diperbarui

### <a name="servicefabric"></a>ServiceFabric

* Menambahkan dukungan untuk nama Key Vault kasus campuran
* Masalah tetap saat menggunakan sertifikat di Key Vault
* Memperbaiki masalah dengan menggunakan file sertifikat PFX
* Masalah tetap dengan `sf cluster certificate add` ketika grup sumber daya Key Vault tidak ditentukan
* Masalah tetap dengan `sf cluster set` tidak berfungsi

### <a name="signalr"></a>SignalR

* Menambahkan perintah baru:
  * `signalr cors`: Mengelola Signalr CORS
  * `signalr restart`: Memulai ulang layanan SignalR
  * `signalr update`: Memperbarui layanan SignalR
* Menambahkan `--service-mode` argumen ke `signalr create`

### <a name="storage"></a>Penyimpanan

* Perintah tambahan `storage account revoke-delegation-keys`

## <a name="august-13-2019"></a>Tanggal 13 Agustus 2019

Versi 2.0.71

### <a name="appservice"></a>AppService

* Masalah tetap di mana `webapp webjob continuous` perintah gagal untuk slot

### <a name="botservice"></a>Layanan Bot

* [MELANGGAR PERUBAHAN] Dukungan yang dihapus untuk membuat bot SDK v3

### <a name="cognitiveservices"></a>Layanan Kognitif

* Menambahkan `cognitiveservices account network-rule` perintah

### <a name="cosmos-db"></a>Cosmos DB

* Peringatan yang dihapus saat memperbarui beberapa lokasi tulis
* Menambahkan perintah CRUD untuk CosmosDB SQL, MongoDB, Cassandra, Gremlin dan Sumber daya Tabel dan throughput sumber daya

### <a name="hdinsight"></a>HDInsight

Rilis ini berisi sejumlah besar perubahan melanggar.

* [MELANGGAR PERUBAHAN] Mengganti nama parameter untuk `hdinsight create`:
  * Berganti nama menjadi `--storage-default-container``--storage-container`
  * Berganti nama menjadi `--storage-default-filesystem``--storage-filesystem`
* [MELANGGAR PERUBAHAN] `--name` Mengubah argumen `application create` untuk mewakili nama aplikasi, bukan nama cluster
* Menambahkan `--cluster-name` argumen untuk `application create` menggantikan fungsionalitas lama `--name`
* [MELANGGAR PERUBAHAN] Mengganti nama parameter untuk `application create`:
  * Berganti nama menjadi `--application-type``--type`
  * Berganti nama menjadi `--marketplace-identifier``--marketplace-id`
  * Berganti nama menjadi `--https-endpoint-access-mode``--access-mode`
  * Berganti nama menjadi `--https-endpoint-destination-port``--destination-port`
* [MELANGGAR PERUBAHAN] Parameter yang dihapus untuk `application create`:
  * `--https-endpoint-location`
  * `--https-endpoint-public-port`
  * `--ssh-endpoint-destination-port`
  * `--ssh-endpoint-location`
  * `--ssh-endpoint-public-port`
* [MELANGGAR CHNAGE] Berganti nama menjadi `--target-instance-count` `--workernode-count` untuk `hdinsight resize`
* [MELANGGAR PERUBAHAN] Mengubah semua perintah dalam `hdinsight script-action` grup untuk menggunakan `--name` parameter sebagai nama tindakan skrip.
* Menambahkan `--cluster-name` argumen ke semua `hdinsight script-action` perintah untuk menggantikan fungsionalitas lama `--name`
* [MELANGGAR PERUBAHAN] Berganti nama `--script-execution-id` menjadi `--execution-id` untuk semua `hdinsight script-action` perintah
* [MELANGGAR PERUBAHAN] Berganti nama menjadi `hdinsight script-action show``hdinsight script-action show-execution-details`
* [MELANGGAR CHNAGE] Mengubah parameter menjadi `hdinsight script-action execute --roles` ruang-terpisah bukan koma-terpisah
* [MELANGGAR PERUBAHAN] Menghapus `--persisted` parameter dari `hdinsight script-action list`
* `hdinsight create --cluster-configurations` Mengubah parameter untuk menerima jalur ke file JSON lokal atau string JSON
* Perintah tambahan `hdinsight script-action list-execution-history`
* Diubah `hdinsight monitor enable --workspace` untuk menerima ID ruang kerja Log Analytics atau nama ruang kerja
* Menambahkan `hdinsight monitor enable --primary-key` argumen, yang diperlukan jika ID ruang kerja disediakan sebagai parameter
* Menambahkan lebih banyak contoh dan deskripsi terbaru untuk pesan bantuan

### <a name="interactive"></a>Interaktif

* Memperbaiki kesalahan pemuatan

### <a name="kubernetes"></a>Kubernetes

* Diubah untuk digunakan `https` jika port kontainer dasbor menggunakan `https`

### <a name="network"></a>Jaringan

* Menambahkan `--yes` argumen `network dns record-set cname delete`

### <a name="profile"></a>Profil

* Menambahkan `--resource-type` argumen untuk `account get-access-token` mendapatkan token akses sumber daya

### <a name="servicefabric"></a>ServiceFabric

* Menambahkan semua versi os yang didukung untuk pembuatan klaster sf
* Bug validasi sertifikat primer tetap

### <a name="storage"></a>Penyimpanan

* Perintah tambahan `storage copy`

## <a name="july-30-2019"></a>Tanggal 30 Juli 2019

Versi 2.0.70

### <a name="acr"></a>ACR

* Masalah tetap #9952 (regresi dalam `acr pack build` perintah)
* Menghapus nama gambar pembangun default di `acr pack build`

### <a name="appservice"></a>Layanan aplikasi

* Diubah `webapp config ssl` untuk menampilkan pesan jika sumber daya tidak ditemukan
* Masalah tetap di mana `functionapp create` tidak menerima `Standard_RAGRS` tipe akun penyimpanan
* Memperbaiki masalah di mana `webapp up` akan gagal jika dijalankan menggunakan versi python yang lebih lama

### <a name="network"></a>Jaringan

* Menghapus parameter `--ids` tidak valid dari `network nic ip-config add` (memperbaiki #9861)
* Memperbaiki #9604. Menambahkan `--root-certs` parameter untuk `network application-gateway http-settings [create|update]` mendukung sertifikat root tepercaya rekan pengguna.
* Tetap berpendapat `--subscription` untuk `network dns record-set ns create` (#9965)

### <a name="rbac"></a>RBAC

* Perintah tambahan `user update`
* [USANG] Usang `--upn-or-object-id` dari perintah terkait pengguna
    * Menggunakan argumen pengganti `--id`
* Menambahkan `--id` argumen ke perintah terkait pengguna

### <a name="sql"></a>SQL

* Menambahkan perintah manajemen untuk kunci instans terkelola dan pelindung TDE

### <a name="storage"></a>Penyimpanan

* Perintah tambahan `storage remove`
* Memperbaiki masalah dengan `storage blob update`

### <a name="vm"></a>VM

* Diubah `list-skus` untuk menggunakan versi api yang lebih baru ke detail zona output
* Mengubah default `--single-placement-group` ke `false` untuk `vmss create`
* Menambahkan kemampuan untuk memilih SKU penyimpanan ZRS untuk `[snapshot|disk] create`
* Menambahkan grup `vm host` perintah baru untuk mendukung host khusus
* Menambahkan parameter `--host` dan `--host-group` untuk `vm create` mengatur host khusus VM

## <a name="july-16-2019"></a>16 Juli 2019

Versi 2.0.69

### <a name="appservice"></a>Layanan aplikasi

* Perintah yang diubah `webapp identity` untuk mengembalikan pesan kesalahan yang tepat jika ResourceGroupName atau nama Aplikasi tidak valid
* Tetap `webapp list` untuk mengembalikan nilai yang benar untuk numberOfSites jika tidak ada ResourceGroup yang disediakan
* Efek samping tetap dari `appservice plan create` dan `webapp create`

### <a name="core"></a>Core

* Masalah tetap di mana `--subscription` akan muncul meskipun tidak berlaku

### <a name="batch"></a>Batch

* [MELANGGAR PERUBAHAN] Diganti `batch pool node-agent-skus list` dengan `batch pool supported-images list`
* Menambahkan dukungan untuk aturan keamanan yang memblokir akses jaringan ke kolam berdasarkan port sumber lalu lintas saat menggunakan `--json-file` opsi `batch pool create network`
* Menambahkan dukungan untuk menjalankan tugas di direktori kerja kontainer atau di direktori kerja tugas Batch saat menggunakan `--json-file` opsi `batch task create`
* Memperbaiki kesalahan dalam `--application-package-references` opsi `batch pool create` di mana ia hanya akan bekerja dengan default

### <a name="eventhubs"></a>Eventhubs

* Menambahkan validasi untuk parameter `--rights` `authorizationrule` perintah

### <a name="rdbms"></a>RDBMS

* Menambahkan parameter opsional untuk menentukan replika SKU untuk membuat perintah replika
* Memperbaiki masalah dengan kegagalan tes CI dengan membuat replika MySQL

### <a name="relay"></a>Relay

* Masalah tetap dengan koneksi hibrida saat authroization klien dinonaktifkan [#8775](https://github.com/azure/azure-cli/issues/8775)
* Menambahkan parameter `--requires-transport-security` ke `relay wcfrelay create`

### <a name="servicebus"></a>Servicebus

* Menambahkan validasi untuk parameter `--rights` `authorizationrule` perintah

### <a name="storage"></a>Penyimpanan

* Aktifkan File AADDS untuk pembaruan akun penyimpanan
* Masalah tetap `storage blob service-properties update --set`

## <a name="july-2-2019"></a>2 Juli 2019

Versi 2.0.68

### <a name="core"></a>Core

* Modul perintah sekarang dikonsolidasikan menjadi python tunggal didistribusikan. Ini mendepresiasi penggunaan langsung banyak `azure-cli-` paket di PyPI.
  Ini harus mengurangi ukuran pemasangan dan hanya mempengaruhi pengguna yang telah langsung menginstal melalui `pip`.

### <a name="acr"></a>ACR

* Menambahkan dukungan untuk Pemicu Timer ke Tugas

### <a name="appservice"></a>Layanan aplikasi

* Diubah `functionapp create` untuk mengaktifkan wawasan aplikasi secara default
* [MELANGGAR PERUBAHAN] Dihapus perintah usang `functionapp devops-build` .
  *  Gunakan perintah `az functionapp devops-pipeline` baru sebagai gantinya
* Menambahkan dukungan paket aplikasi fungsi Konsumsi Linux ke `functionapp deployment config-zip`

### <a name="cosmos-db"></a>Cosmos DB

* Menambahkan dukungan untuk menonaktifkan TTL

### <a name="dls"></a>DLS

* Versi ADLS yang diperbarui (0.0.45)

### <a name="feedback-reference"></a>Referensi umpan balik

* Saat melaporkan perintah ekstensi yang gagal, `az feedback` sekarang coba buka browser ke url proyek/repo ekstensi dari indeks

### <a name="hdinsight"></a>HDInsight

* [MELANGGAR PERUBAHAN] Mengubah `oms` nama grup perintah menjadi `monitor`
* [MELANGGAR PERUBAHAN] Membuat `--http-password/-p` parameter yang diperlukan
* Menambahkan completers untuk `--cluster-admin-account` dan `cluster-users-group-dns` parameter lebih lengkap
* Parameter `cluster-users-group-dns` yang diubah yang diperlukan saat `—esp` hadir
* Menambahkan batas waktu untuk semua argumen yang ada auto-completers
* Menambahkan batas waktu untuk mengubah nama sumber daya menjadi id sumber daya
* Mengubah Completers Otomatis untuk memilih sumber daya dari grup sumber daya apa pun. Ini bisa menjadi kelompok sumber daya yang berbeda dari yang ditentukan dengan `-g`
* Menambahkan dukungan dan `--sub-domain-suffix` `--disable_gateway_auth` parameter dalam `hdinsight application create` perintah

### <a name="managed-services"></a>Layanan Terkelola

* Memperkenalkan modul perintah layanan terkelola dalam pratinjau

### <a name="profile"></a>Profil
* Menekan `--subscription` argumen untuk perintah logout

### <a name="rbac"></a>RBAC

* [MELANGGAR PERUBAHAN] Argumen yang dihapus `--password` untuk `create-for-rbac`
* Menambahkan `--assignee-principal-type` parameter ke `create` perintah untuk menghindari kegagalan intermiten yang disebabkan oleh latensi replikasi server grafik AAD
* Memperbaiki crash saat `ad signed-in-user` mencantumkan objek yang dimiliki
* Masalah tetap di mana `ad sp` tidak akan menemukan aplikasi yang tepat dari kepala layanan

### <a name="rdbms"></a>RDBMS

* Menambahkan dukungan untuk replikasi untuk MariaDB

### <a name="sql"></a>SQL

* Nilai diperbolehkan terdokumentasi untuk `sql db create --sample-name`

### <a name="storage"></a>Penyimpanan

* Menambahkan dukungan token SAS delegasi pengguna dengan `--as-user``storage blob generate-sas`
* Menambahkan dukungan token SAS delegasi pengguna dengan `--as-user``storage container generate-sas`

### <a name="vm"></a>VM

* Bug tetap di mana `vmss create` mengembalikan pesan kesalahan saat dijalankan `--no-wait`
* Menghapus validasi sisi klien untuk `vmss create --single-placement-group`. Tidak gagal jika `--single-placement-group` diatur ke `true` dan`--instance-count` lebih besar dari 100 atau zona ketersediaan ditentukan, tetapi meninggalkan validasi ini ke layanan komputasi
* Bug tetap di mana `[vm|vmss] extension image list` gagal saat digunakan `--latest`


## <a name="june-18-2019"></a>Tanggal 18 Juni 2019

Versi 2.0.67

### <a name="core"></a>Core

Rilis ini memperkenalkan tag [Pratinjau] baru untuk berkomunikasi lebih jelas kepada pelanggan ketika grup perintah, perintah, atau argumen berada dalam status pratinjau. Ini sebelumnya disebut dalam teks bantuan atau dikomunikasikan secara implisit oleh nomor versi modul perintah.
CLI akan menghapus nomor versi untuk paket individual di masa depan. Jika perintah sedang dalam pratinjau, semua argumennya juga. Jika grup perintah diberi label sebagai berada dalam pratinjau, maka semua perintah dan argumen dianggap dalam pratinjau juga.

Sebagai hasil dari perubahan ini, beberapa kelompok perintah mungkin tampak "tiba-tiba" tampak berada dalam status pratinjau dengan rilis ini. Apa yang sebenarnya terjadi adalah bahwa sebagian besar paket berada dalam status pratinjau, tetapi dianggap GA dengan rilis ini.

### <a name="acr"></a>ACR
* Menambahkan perintah 'acr check-health'
* Peningkatan penanganan kesalahan untuk token AAD dan untuk mengambil perintah eksternal

### <a name="acs"></a>ACS
* Perintah ACS yang tidak siap sekarang disembunyikan dari tampilan bantuan

### <a name="ams"></a>AMS
* [MELANGGAR PERUBAHAN] Diubah untuk mengembalikan string waktu ISO 8601 untuk arsip-window-length dan key-frame-interval-duration

### <a name="appservice"></a>AppService
* Menambahkan perutean berbasis lokasi untuk `webapp deleted list` dan `webapp deleted restore`
* Masalah tetap di mana URL target yang masuk webapp ("Anda dapat meluncurkan aplikasi di ...") tidak dapat diklik di Azure Cloud Shell
* Memperbaiki masalah di mana membuat aplikasi dengan beberapa SKU gagal dengan kesalahan AlwaysOn
* Menambahkan pra-validasi ke `[appservice|webapp] create`
* Tetap `[webapp|functionapp] traffic-routing` menggunakan tindakan yang benarHostName
* Menambahkan dukungan slot ke `functionapp` perintah

### <a name="batch"></a>Batch
* Regresi auth AAD tetap yang disebabkan oleh pelaporan kesalahan yang terlalu agresif untuk Shared Key Auth

### <a name="batchai"></a>BatchAI
* Perintah BatchAI sekarang usang dan tersembunyi

### <a name="botservice"></a>Layanan Bot
* Menambahkan pesan peringatan "dukungan yang dihentikan"/"mode pemeliharaan" untuk perintah yang mendukung SDK v3

### <a name="cosmosdb"></a>CosmosDB
* [USANG] Usang `cosmosdb list-keys` perintah
* Menambahkan `cosmosdb keys list` perintah - menggantikan `cosmosdb list-keys`
* `cosmsodb create/update`Menambahkan format baru untuk --lokasi untuk memungkinkan pengaturan properti "isZoneRedundant". Format lama yang tidak didepresiasi

### <a name="eventgrid"></a>EventGrid
* Menambahkan `eventgrid domain` perintah untuk operasi CRUD domain
* Menambahkan `eventgrid domain topic` perintah untuk topik domain operasi CRUD
* Menambahkan `--odata-query` argumen untuk `eventgrid [topic|event-subscription] list` memfilter hasil menggunakan sintaks OData
* `event-subscription create/update`: Menambahkan servicebusqueue sebagai nilai baru untuk `--endpoint-type` parameter
* [MELANGGAR PERUBAHAN] Dukungan yang dihapus untuk `--included-event-types All` dengan `eventgrid event-subscription [create|update]`

### <a name="hdinsight"></a>HDInsight
* Menambahkan dukungan untuk `--ssh-public-key` parameter dalam `hdinsight create` perintah

### <a name="iot"></a>IoT
* Menambahkan dukungan untuk meregenerasi kunci kebijakan otorisasi
* Menambahkan SDK dan dukungan untuk Layanan Penyediaan Repositori DigitalTwin

### <a name="network"></a>Jaringan
* Dukungan Zona Tambahan untuk Nat Gateway
* Perintah tambahan `network list-service-tags`
* Masalah tetap dengan `dns zone import` di mana pengguna tidak dapat mengimpor wildcard Catatan A
* Masalah tetap dengan `watcher flow-log configure` di mana pencatatan aliran tidak dapat diaktifkan di wilayah tertentu

### <a name="resource"></a>Sumber daya
* Perintah tambahan `az rest` untuk membuat panggilan REST
* Memperbaiki kesalahan saat menggunakan `policy assignment list` grup sumber daya atau tingkat langganan `--scope`

### <a name="servicebus"></a>ServiceBus
* Masalah tetap dengan `servicebus topic create --max-size` [#9319](https://github.com/azure/azure-cli/issues/9319)

### <a name="sql"></a>SQL
* Diubah `--location` menjadi opsional untuk `sql [server|mi] create` - menggunakan lokasi grup sumber daya jika tidak ditentukan
* Memperbaiki kesalahan "NoneType" untuk `sql db list-editions --available`

### <a name="sqlvm"></a>SQLVm
* [MELANGGAR CHNAGE] Diubah `sql vm create` untuk memerlukan `--license-type` parameter
* Diubah untuk memungkinkan pengaturan SQL gambar SKU saat membuat atau memperbarui vm sql

### <a name="storage"></a>Penyimpanan
* Memperbaiki masalah dengan kunci akun yang hilang untuk `storage container generate-sas`
* Masalah tetap dengan `storage blob sync` di Linux

### <a name="vm"></a>VM
* [PREVIEW] Menambahkan `vm image template` perintah untuk membuat gambar VM

## <a name="june-4-2019"></a>Tanggal 4 Juni 2019

Versi 2.0.66

### <a name="core"></a>Core
* Bug tetap di mana perintah gagal jika `--output yaml` digunakan dengan `--query`

### <a name="acr"></a>ACR
* Menambahkan grup perintah 'acr pack' untuk membuat Tugas build cepat menggunakan Buildpacks.

### <a name="acs"></a>ACS
* Perbolehkan mengaktifkan/menonaktifkan addon AKS kube-dashboard
* Mencetak pesan ramah saat langganan tidak disetujui untuk menggunakan Azure Red Hat OpenShift

### <a name="batch"></a>Batch
* Peningkatan penanganan kesalahan saat tidak masuk ke akun \[[#9165](https://github.com/Azure/azure-cli/issues/9165)\]\[[#8978](https://github.com/Azure/azure-cli/issues/8978)\]

### <a name="iot"></a>IoT
* Menambahkan dukungan untuk failover manual

### <a name="network"></a>Jaringan
* Menambahkan `network application-gateway waf-policy` perintah untuk mendukung aturan WAF kustom.
* Ditambahkan `--waf-policy` dan `--max-capacity` argumen untuk `network application-gateway [create|update]`

### <a name="resource"></a>Sumber daya
* Pesan kesalahan yang disempurnakan dari `deployment create` saat tidak ada TTY yang tersedia

### <a name="role"></a>Peran
* Teks bantuan yang diperbarui.

### <a name="compute"></a>Compute
* Menambahkan dukungan untuk `vm create` VM dari gambar terkelola dengan lun data-disk yang tidak dimulai dari 0 atau yang melewatkan angka

## <a name="may-21-2019"></a>Tanggal 21 Mei 2019

Versi 2.0.65

### <a name="core"></a>Core
* Menambahkan umpan balik yang lebih baik untuk kesalahan otentikasi
* Masalah tetap di mana CLI akan memuat ekstensi yang tidak kompatibel dengan versi intinya
* Masalah tetap dengan peluncuran ketika `clouds.config` rusak

### <a name="acr"></a>ACR
* Menambahkan dukungan untuk Identitas Terkelola untuk Tugas

### <a name="acs"></a>ACS
* Perintah tetap `openshift create` saat digunakan dengan klien AAD pelanggan

### <a name="appservice"></a>AppService
* [USANG] Perintah usang `functionapp devops-build` - akan dihapus dalam rilis berikutnya
* Diubah `functionapp devops-pipeline` untuk mengambil log build dari Azure DevOps dalam mode verbose
* [MELANGGAR PERUBAHAN] `--use_local_settings` Menghapus bendera dari `functionapp devops-pipeline` perintah - adalah no-op
* Diubah `webapp up` untuk mengembalikan output JSON jika `--logs` tidak digunakan
* Menambahkan dukungan untuk menulis sumber daya default ke konfigurasi lokal untuk `webapp up`
* Menambahkan dukungan untuk `webapp up` memindahkan aplikasi tanpa menggunakan `--location` argumen
* Memperbaiki masalah di mana untuk penggunaan pembuatan SKU ASP Gratis sebagai nilai SKU tidak berfungsi

### <a name="botservice"></a>Layanan Bot
* Diubah untuk memungkinkan semua casing untuk `--lang` parameter untuk perintah
* Deskripsi yang diperbarui untuk modul perintah

### <a name="consumption"></a>Consumption
* Menambahkan parameter yang diperlukan hilang saat berjalan `consumption usage list --billing-period-name`

### <a name="iot"></a>IoT
* Menambahkan dukungan untuk mencantumkan semua kunci

### <a name="network"></a>Jaringan
* [MELANGGAR PERUBAHAN]: Removed `network interface-endpoints` command group - use `network private-endpoints`
* Menambahkan `--nat-gateway` argumen untuk `network vnet subnet [create|update]` melampirkan ke gateway NAT
* Masalah tetap dengan `dns zone import` di mana nama catatan tidak bisa menandingi tipe catatan

### <a name="rdbms"></a>RDBMS
* Menambahkan dukungan postgres dan mysql untuk replikasi geografis

### <a name="rbac"></a>RBAC
* Menambahkan dukungan untuk lingkup kelompok manajemen ke `role assignment`

### <a name="storage"></a>Penyimpanan
* `storage blob sync`: menambahkan perintah sinkronisasi untuk gumpalan penyimpanan

### <a name="compute"></a>Compute
* Ditambahkan `--computer-name` untuk `vm create` mengatur nama komputer VM
* Berganti nama `--ssh-key-value` menjadi `--ssh-key-values` untuk `[vm|vmss] create` - sekarang dapat menerima beberapa nilai atau jalur kunci publik ssh
  * __Catatan__: Ini **bukan** perubahan yang melanggar - `--ssh-key-value` akan diurai dengan benar karena hanya cocok `--ssh-key-values`
* `--type` Mengubah argumen `ppg create` menjadi opsional

## <a name="may-6-2019"></a>6 Mei 2019

Versi 2.0.64

### <a name="acs"></a>ACS
* [MELANGGAR PERUBAHAN] `--fqdn` Menghapus bendera pada `openshift` perintah
* Diubah untuk menggunakan Azure Red Hat Openshift GA API Version
* Menambahkan `customer-admin-group-id` bendera ke `openshift create`
* [GA] Dihapus `(PREVIEW)` dari `aks create` opsi `--network-policy`

### <a name="appservice"></a>Layanan aplikasi
* [USANG] Perintah usang `functionapp devops-build`
  * Berganti nama menjadi `functionapp devops-pipeline`
* Tetap mendapatkan nama pengguna yang benar untuk cloudshell yang menyebabkan `webapp up` gagal
* Dokumentasi yang `appservice plan --sku` diperbarui diperbarui untuk mencerminkan appserviceplans yang didukung
* Menambahkan argumen opsional untuk grup sumber daya dan berencana untuk `webapp up`
* Menambahkan dukungan untuk `webapp ssh` menghormati `AZURE_CLI_DISABLE_CONNECTION_VERIFICATION` variabel lingkungan
* Dukungan tambahan `appserviceplan create` untuk Linux Free SKU
* Diubah `webapp up` menjadi tidur 30-an setelah mengatur `SCM_DO_BUILD_DURING_DEPLOYMENT=true` pengaturan aplikasi untuk menangani kudu cold start
* Menambahkan dukungan untuk `powershell` runtime ke `functionapp create` Windows
* Perintah tambahan `create-remote-connection`

### <a name="batch"></a>Batch
* Bug tetap di validator untuk `--application-package-references` opsi

### <a name="botservice"></a>Layanan bot
* [MELANGGAR PERUBAHAN] Diubah `bot create -v v4 -k webapp` untuk membuat Bot Aplikasi Web kosong secara default (yaitu tidak ada bot yang digunakan ke Layanan Aplikasi)
* Menambahkan `--echo` bendera untuk `bot create` menggunakan perilaku lama dengan `-v v4`
* [MELANGGAR PERUBAHAN] Mengubah nilai  `--version` default menjadi `v4`
  * __NOTA:__ `bot prepare-publish` masih menggunakan default lamanya
* [MELANGGAR PERUBAHAN] Diubah `--lang` menjadi tidak lagi default ke `Csharp`. Jika perintah membutuhkan `--lang` dan tidak disediakan, perintah sekarang akan kesalahan keluar.
* [MELANGGAR PERUBAHAN] `--appid` Mengubah dan `--password` args untuk `bot create` diminta dan sekarang dapat dibuat melalui `ad app create`
* Ditambahkan `--appid` dan `--password` validasi
* [MELANGGAR PERUBAHAN] Diubah `bot create -v v4` menjadi tidak membuat atau menggunakan Akun Storage atau aplikasi Insights
* [MELANGGAR PERUBAHAN] Diubah `bot create -v v3` untuk memerlukan wilayah di mana Insights Aplikasi tersedia
* [MELANGGAR PERUBAHAN] Diubah `bot update` menjadi sekarang hanya mempengaruhi sifat spesifik bot
* [MELANGGAR PERUBAHAN] Mengubah `--lang` bendera untuk diterima `Javascript` , bukan `Node`
* [MELANGGAR PERUBAHAN] Dihapus `Node` sebagai nilai yang diizinkan `--lang`
* [MELANGGAR PERUBAHAN] Diubah `bot create -v v4 -k webapp` menjadi tidak lagi menjadi `SCM_DO_BUILD_DURING_DEPLOYMENT` kenyataan. Semua penyebaran melalui Kudu akan bertindak sesuai dengan perilaku default mereka
* Diubah `bot download` untuk bot tanpa `.bot` file untuk membuat file konfigurasi khusus bahasa dengan nilai dari Pengaturan Aplikasi untuk bot
* Menambahkan `Typescript` dukungan untuk `bot prepare-deploy`
* Menambahkan pesan peringatan ke `bot prepare-deploy` untuk `Javascript` dan `Typescript` bot untuk kapan `--code-dir` tidak berisi `package.json`
* Diubah `bot prepare-deploy` untuk kembali `true` jika berhasil
* Menambahkan log verbose ke `bot prepare-deploy`
* Menambahkan lebih banyak wilayah Insights Aplikasi yang tersedia ke`az bot create -v v3`

### <a name="configure"></a>Konfigurasikan
* Menambahkan dukungan untuk konfigurasi nilai default argumen berbasis folder

### <a name="eventhubs"></a>Eventhubs
* Menambahkan `namespace network-rule` perintah
* Menambahkan `--default-action` argumen untuk aturan jaringan ke `namespace [create|update]`

### <a name="network"></a>Jaringan
* [MELANGGAR PERUBAHAN] Mengganti `--cache` arugment dengan `--defer` untuk `vnet [create|update]`

### <a name="policy-insights"></a>Policy Insights
* Menambahkan dukungan untuk `--expand PolicyEvaluationDetails` meminta rincian evaluasi kebijakan tentang sumber daya

### <a name="role"></a>Peran
* [USANG] Mengubah `create-for-rbac` argumen sembunyikan '-kata sandi' - dukungan akan dihapus pada Mei 2019

### <a name="service-bus"></a>Service Bus
* Menambahkan `namespace network-rule` perintah
* Menambahkan `--default-action` argumen untuk aturan jaringan ke `namespace [create|update]`
* Tetap `topic [create|update]` untuk memungkinkan `--max-size` dukungan untuk nilai 10, 20, 40 dan 80GB dengan SKU premium

### <a name="sql"></a>SQL
* Menambahkan `sql virtual-cluster [list|show|delete]` perintah

### <a name="vm"></a>VM
* Ditambahkan `--protect-from-scale-in` dan `--protect-from-scale-set-actions` untuk `vmss update` mengaktifkan pembaruan pada kebijakan perlindungan instans VMSS VM
* Ditambahkan `--instance-id` untuk `vmss update` mengaktifkan pembaruan generik instans VMSS VM
* Ditambahkan `--instance-id` ke `vmss wait`
* Menambahkan grup perintah baru `ppg` untuk mengelola Grup Penempatan Kedekatan
* Ditambahkan `--ppg` ke `[vm|vmss] create` dan `vm availability-set create` untuk mengelola PPG
* Menambahkan `--hyper-v-generation` parameter ke `image create`

## <a name="april-23-2019"></a>23 April 2019

Versi 2.0.63

### <a name="acs"></a>ACS
* Diubah `aks get-credentials` menjadi prompt untuk menimpa nilai duplikat
* Dihapus `(PREVIEW)` dari Dev Spaces perintah "aks use-dev-spaces" dan "aks remove-dev-spaces"

### <a name="ams"></a>AMS
* Bug tetap dengan pembaruan filter aset dan akun

### <a name="appservice"></a>AppService
* Menambahkan dukungan untuk ASE dan timeout untuk `webapp ssh`
* Menambahkan dukungan untuk membangun CD CI ke pipa Azure DevOps dari repositori Github ke aplikasi Fungsi
* Menambahkan `--github-pat` argumen untuk `functionapp devops-build create` menerima token akses pribadi Github
* Menambahkan `--github-repository` argumen untuk `functionapp devops-build create` menerima repositori Github yang berisi kode sumber functionapp
* Masalah tetap di mana `az webapp up --logs` gagal dengan kesalahan dan memperbarui default. Versi NETCORE ke 2.1
* Menghapus pengaturan functionapp yang tidak perlu saat membuat aplikasi fungsi dengan paket konsumsi
* Diubah `webapp up` sehingga string ASP default sekarang menambahkan nomor di akhir untuk membuat ASP baru berdasarkan opsi SKU
* Ditambahkan `-b` sebagai opsi untuk `webapp up` meluncurkan aplikasi di browser
* Diubah `webapp deployment source config zip` untuk menangani `AZURE_CLI_DISABLE_CONNECTION_VERIFICATION` variabel lingkungan

### <a name="deployment-manager"></a>Deployment Manager
* [PREVIEW] Membuat dan mengelola artefak yang mendukung peluncuran

### <a name="lab"></a>Laboratorium
* Bug tetap yang akan menyebabkan keluar lebih awal

### <a name="network"></a>Jaringan
* Menambahkan delegasi server nama otomatis ke `dns zone create` orang tua selama pembuatan zona anak

### <a name="resource"></a>Sumber daya
* [USANG] Usang `--link-id`, `--target-id` dan `--filter-string` argumen dari `resource link`
  * Gunakan argumen `--link`, `--target`, dan `--filter` sebagai gantinya
* Masalah tetap di mana `resource link [create|update]` perintah tidak akan berfungsi
* Memperbaiki masalah di mana menghapus menggunakan ID sumber daya bisa crash pada kesalahan

### <a name="sql"></a>SQL
* Menambahkan dukungan untuk zona waktu kustom pada instans terkelola
* Diubah untuk memungkinkan nama kolam elastis digunakan dengan `sql db update`
* Menambahkan `--no-wait` dukungan untuk `sql server [create|update]`
* Perintah tambahan `sql server wait`

### <a name="storage"></a>Penyimpanan
* Masalah tetap dengan token SAS yang dikodekan ganda di `storage blob generate-sas`

### <a name="vm"></a>VM
* Menambahkan `--skip-shutdown` bendera ke `vm|vmss stop` VM power-off tanpa shutdown
* Menambahkan `--storage-account-type` argumen untuk `sig image-version create` mengatur tipe akun profil penerbitan
* Menambahkan `--target-regions` argumen untuk `sig image-version create` memungkinkan pengaturan tipe akun penyimpanan khusus wilayah

## <a name="april-9-2019"></a>9 April 2019

### <a name="core"></a>Core
* Masalah tetap di mana beberapa ekstensi menunjukkan versi `Unknown` dan tidak dapat diperbarui

### <a name="acr"></a>ACR
* Menambahkan dukungan menjalankan gambar tanpa konteks

### <a name="ams"></a>AMS
* [USANG]: Deprecated the `--bitrate` parameter of `account-filter` and `asset-filter`
* [MELANGGAR PERUBAHAN]: Renamed the `--bitrate` parameter to `--first-quality`
* Menambahkan dukungan parameter enkripsi baru di `ams streaming-policy create`
* Menambahkan paramter `--filters` baru ke `ams streaming-locator create`

### <a name="appservice"></a>AppService
* Menambahkan `--logs` dukungan untuk `webapp up`
* Masalah pembuatan perintah `azure-pipelines.yml` tetap `functionapp devops-build create`
* `unctionapp devops-build create` Peningkatan penanganan dan indikator kesalahan
* [MELANGGAR PERUBAHAN] Menghapus `--local-git` bendera untuk `devops-build` perintah, deteksi dan penanganan git lokal wajib untuk membuat Azure DevOps pipa
* Menambahkan dukungan untuk pembuatan paket fungsi Linux
* Menambahkan kemampuan untuk mengubah paket di bawah aplikasi fungsi menggunakan `functionapp update --plan`
* Menambahkan dukungan untuk pengaturan skala paket premium Azure Functions

### <a name="cdn"></a>CDN
* Dukungan tambahan untuk `Microsoft_Standard` dan `Standard_ChinaCdn`

### <a name="feedback-reference"></a>Referensi umpan balik
* Diubah `feedback` untuk menampilkan metadata pada perintah yang baru saja dijalankan
* Diubah `feedback` untuk meminta pengguna untuk membantu dalam proses pembuatan masalah dengan membuka brower dan menggunakan template masalah
* Diubah `feedback` untuk mencetak tubuh masalah saat dijalankan dengan '--verbose'

### <a name="monitor"></a>Monitor
* Masalah tetap di mana "menghitung" bukanlah nilai yang diizinkan dengan `metrics alert [create|update]`

### <a name="network"></a>Jaringan
* Format tabel tetap tidak ditampilkan dengan `vnet-gateway list-bgp-peer-status`
* Ditambahkan `list-request-headers` dan `list-response-headers` perintah untuk `application-gateway rewrite-rule`
* Menambahkan `list-server-variables` perintah ke `application-gateway rewrite-rule condition`
* Memperbaiki masalah di mana memperbarui status tautan pada port rute ekspres akan melemparkan pengecualian atribut yang tidak diketahui `express-route port update`

### <a name="privatedns"></a>PrivateDNS
* Ditambahkan `network private-dns` untuk zona DNS Pribadi

### <a name="resource"></a>Sumber daya
* Masalah tetap dengan `deployment create` dan `group deployment create` di mana file parameter dengan satu set parameter kosong tidak akan berfungsi

### <a name="role"></a>Peran
* Memperbaiki `create-for-rbac` untuk menangani `--years` dengan benar
* [MELANGGAR PERUBAHAN] Diubah `role assignment delete` menjadi prompt saat menghapus semua tugas di bawah langganan tanpa syarat

### <a name="sql"></a>SQL
* Diperbarui `sql mi [create|update]` dengan properti proxyOverride dan publicDataEndpointEnabled

### <a name="storage"></a>Penyimpanan
* [MELANGGAR PERUBAHAN] Dihapus hasil dari `storage blob delete`
* Ditambahkan `--full-uri` untuk `storage blob generate-sas` membuat uri penuh untuk gumpalan dengan sas
* Ditambahkan `--file-snapshot` ke `storage file copy start` untuk menyalin file dari snapshot
* Diubah `storage blob copy cancel` menjadi hanya memperlihatkan kesalahan, bukan pengecualian untuk Operasi NoPendingCopy

## <a name="march-26-2019"></a>26 Maret 2019


### <a name="core"></a>Core
* Masalah tetap dengan ketidakcocokan ekstensi dev
* Penanganan kesalahan sekarang mengarahkan pelanggan ke halaman masalah

### <a name="cloud"></a>Cloud
* Memperbaiki kesalahan 'langganan tidak ditemukan' di `cloud set`

### <a name="acr"></a>ACR
* Sumber redundan tetap dalam impor gambar
* Ditambahkan ke , , , `acr task create`dan `acr task update` perintah `acr run``acr build``--auth-mode`
* Menambahkan grup perintah 'kredensial tugas acr' untuk mengelola kredensial untuk Tugas
* Menambahkan '--no-wait' ke `acr build` perintah

### <a name="appservice"></a>AppService
* Bug tetap di mana `webapp up` tidak menangani berjalan dari direktori kosong atau skenario kode yang tidak diketahui dengan benar
* Bug tetap di mana slot tidak berfungsi `[webapp|functionapp] config ssl bind`

### <a name="bot-service"></a>Layanan BOT
* Ditambahkan `bot prepare-deploy` untuk mempersiapkan penyebaran bot melalui `webapp`
* Diubah `bot create --kind registration` untuk menampilkan kata sandi jika kata sandi tidak disediakan
* [MELANGGAR PERUBAHAN] `bot create --kind registration` Diubah `--endpoint` menjadi default ke string kosong alih-alih diperlukan
* Ditambahkan `SCM_DO_BUILD_DURING_DEPLOYMENT` ke Pengaturan Aplikasi template ARM untuk Bot Aplikasi Web v4

### <a name="cdn"></a>CDN
* Dukungan tambahan untuk `--no-wait``cdn endpoint [create|update|start|stop|delete|load|purge]`
* [BREAKING CHANGE]: Mengubah `cdn endpoint create` perilaku caching string kueri default. Tidak lagi default ke "IgnoreQueryString". Sekarang diatur oleh layanan

### <a name="cosmosdb"></a>Cosmosdb
* Menambahkan dukungan untuk `--enable-multiple-write-locations` pembaruan akun
* Menambahkan `network-rule` subkelompok dengan perintah `add`, `remove`, dan `list` untuk mengelola aturan VNET dari akun Cosmos DB

### <a name="interactive"></a>Interaktif
* Ketidakcocokan tetap dengan ekstensi Interaktif yang diinstal melalui azdev

### <a name="monitor"></a>Monitor
* Diubah untuk memungkinkan nilai `*` dimensi untuk `monitor metrics alert [create|update]`

### <a name="network"></a>Jaringan
* Menambahkan `rewrite-rule` grup perintah ke `application-gateway`

### <a name="profile"></a>Profil
* Menambahkan dukungan akun tingkat penyewa untuk identitas layanan terkelola ke `login`

### <a name="postgres"></a>Postgres
* Menambahkan perintah dan `restart server` perintah postgresql `replica`
* Diubah untuk mendapatkan lokasi default dari grup sumber daya saat tidak disediakan untuk membuat server dan menambahkan validasi untuk hari retensi

### <a name="resource"></a>Sumber daya
* Output tabel yang ditingkatkan untuk `deployment [create|list|show]`
* Masalah tetap dengan `deployment [create|validate]` di mana tipe secureObject tidak dikenali

### <a name="graph"></a>Graph
* Dukungan tambahan untuk `--end-date``ad [app|sp] credential reset`
* Menambahkan dukungan untuk menambahkan izin dengan `ad app permission add`
* Memperbaiki bug saat `ad app permission list` tidak ada izin
* Diubah `ad sp delete` untuk melewatkan penghapusan tugas peran jika akun saat ini tidak memiliki langganan
* Diubah `ad app create` menjadi `--identifier-uris` daftar default ke kosong jika tidak disediakan

### <a name="storage"></a>penyimpanan
* Ditambahkan `--snapshot` ke `storage file download-batch` untuk mengunduh dari snapshot berbagi
* Mengubah `storage blob [download-batch|upload-batch]` bilah kemajuan menjadi kurang verbose dan menunjukkan gumpalan saat ini
* Masalah tetap dengan `storage account update` saat memperbarui parameter enkripsi
* Masalah tetap di mana `storage blob show` akan gagal saat menggunakan oauth (`--auth-mode=login`)

### <a name="vm"></a>VM
* Perintah tambahan `image update`

## <a name="march-12-2019"></a>12 Maret 2019

Versi 2.0.60

### <a name="core"></a>Core

* Memperbaiki kesalahan yang salah di `cloud set` sekitar langganan yang tidak ditemukan

### <a name="acr"></a>ACR

* Sumber redundan tetap dalam impor gambar

### <a name="acs"></a>ACS

* Diubah untuk mengabaikan `--listen-address` parameter jika `aks browse` tidak didukung oleh kubectl

### <a name="appservice"></a>AppService

* Ditambahkan `[webapp|functionapp] deployment list-publishing-credentials` untuk mendapatkan url penerbitan Kudu dan kredensialnya
* Menghapus pernyataan cetak yang salah untuk `webapp auth update`
* Diperbaiki `functionapp` untuk mengatur gambar yang benar untuk runtime dalam paket Layanan Aplikasi Linux
* Tag pratinjau yang dihapus untuk `webapp up` dan menambahkan perbaikan pada perintah

### <a name="botservice"></a>Layanan bot

* Ditambahkan `SCM_DO_BUILD_DURING_DEPLOYMENT` ke Pengaturan Aplikasi template ARM untuk Bot Aplikasi Web v4
* Ditambahkan `Microsoft-BotFramework-AppId` dan `Microsoft-BotFramework-AppPassword` ke Pengaturan Aplikasi template ARM untuk Bot Aplikasi Web v4
* Menghapus kutipan tunggal dari `bot publish` output perintah di akhir `bot create`
* Diubah `bot publish` menjadi asinkron

### <a name="container"></a>Kontainer

* Menambahkan `--no-wait` argumen ke `container [start|restart]`

### <a name="eventhub"></a>EventHub

* Menambahkan `--skip-empty-archives` bendera untuk `eventhub create|update` mendukung arsip kosong dalam penangkapan

### <a name="find"></a>Cari

* Pembaruan fungsionalitas utama

### <a name="hdinsight"></a>HDInsight

* Menambahkan `--storage-account-managed-identity` parameter untuk `hdinsight create` mendukung ADLS Gen2 MSI

### <a name="network"></a>Jaringan

* Masalah tetap dengan `vpn-connection update` di mana memperbarui koneksi VPN antara gateway dalam langganan yang berbeda akan gagal

### <a name="rdbms"></a>Rdbms

* Perbaikan kecil untuk mendapatkan lokasi default dari grup sumber daya saat tidak disediakan untuk membuat server dan menambahkan validasi untuk hari retensi

### <a name="role"></a>Peran

* Tetap `role definition update` menggunakan ID untuk menyelesaikan definisi dengan benar
* Diubah `ad app credential reset` untuk menghapus asumsi bahwa prinsip layanan aplikasi selalu ada

### <a name="service-fabric"></a>Service Fabric

* Masalah tetap dengan `sf cluster list` tidak dapat dibatalkan

## <a name="february-26-2019"></a>Tanggal 26 Februari 2019

Versi 2.0.59

### <a name="core"></a>Core

* Masalah tetap di mana dalam beberapa kasus menggunakan `--subscription NAME` akan melemparkan pengecualian

### <a name="acr"></a>ACR

* Menambahkan `--target` parameter untuk `acr build`, `acr task create` dan `acr task update` perintah
* Peningkatan penanganan kesalahan untuk perintah runtime saat tidak masuk ke Azure

### <a name="acs"></a>ACS

* Menambahkan `--listen-address` opsi ke `aks port-forward`

### <a name="appservice"></a>AppService

* Perintah tambahan `functionapp devops-build`

### <a name="batch"></a>Batch
* [MELANGGAR PERUBAHAN] Menghapus `batch pool upgrade os` perintah
* [MELANGGAR PERUBAHAN] Menghapus `Pacakges` properti dari `Application` tanggapan
* Menambahkan `batch application package list` perintah ke daftar paket aplikasi
* [MELANGGAR PERUBAHAN] Diubah `--application-id` menjadi `--application-name` dalam semua `batch application` perintah,
* Menambahkan `--json-file` argumen ke perintah untuk meminta respons API mentah
* Validasi yang diperbarui untuk secara otomatis menyertakan `https://` di semua titik akhir jika hilang

### <a name="cosmosdb"></a>CosmosDB

* Menambahkan `network-rule` subkelompok dengan perintah `add`, `remove`, dan `list` untuk mengelola aturan VNET dari akun Cosmos DB

### <a name="kusto"></a>Kusto

* [MELANGGAR PERUBAHAN] Diubah `hot_cache_period` dan `soft_delete_period` tipe untuk database ke format durasi ISO8601

### <a name="network"></a>Jaringan

* Menambahkan `--express-route-gateway-bypass` argumen ke `vpn-connection [create|update]`
* Menambahkan grup perintah dari `express-route` ekstensi
* Grup tambahan `express-route gateway` dan `express-route port` perintah
* Menambahkan argumen `--legacy-mode` ke `express-route peering [create|update]`
* Menambahkan argumen `--allow-classic-operations` dan `--express-route-port` untuk `express-route [create|update]`
* Menambahkan `--gateway-default-site` argumen ke `vnet-gateway [create|update]`
* Menambahkan `ipsec-policy` perintah ke `vnet-gateway`

### <a name="resource"></a>Sumber daya

* Masalah tetap dengan `deployment create` tempat bidang tipe sensitif terhadap kasus
* Menambahkan dukungan untuk file parameter berbasis URI ke `policy assignment create`
* Menambahkan dukungan untuk parameter dan definisi berbasis URI `policy set-definition update`
* Penanganan tetap parameter dan aturan untuk `policy definition update`
* Masalah tetap dengan `resource show/update/delete/tag/invoke-action` ID langganan silang tidak menghormati ID langganan dengan benar

### <a name="role"></a>Peran

* Menambahkan dukungan untuk peran aplikasi ke `ad app [create|update]`

### <a name="vm"></a>VM

* Masalah tetap dengan `vm create where `--accelerated-networking' tidak diaktifkan secara default untuk Ubuntu 18.0

## <a name="february-12-2019"></a>12 Februari 2019

Versi 2.0.58

### <a name="core"></a>Core

* `az --version` sekarang menampilkan pemberitahuan jika Anda memiliki paket yang dapat diperbarui
* Regresi tetap di mana `--ids` tidak bisa lagi digunakan dengan output JSON

### <a name="acr"></a>ACR
* [MELANGGAR PERUBAHAN] Grup perintah dihapus `acr build-task`
* [MELANGGAR PERUBAHAN] Dihapus `--tag` dan `--manifest` opsi dari `acr repository delete`

### <a name="acs"></a>ACS
* Menambahkan dukungan untuk nama-nama kasus-tidak sensitif untuk `aks [enable-addons|disable-addons]`
* Menambahkan dukungan untuk Azure Active Directory memperbarui operasi menggunakan`aks update-credentials --reset-aad`
* Menambahkan klarifikasi yang `--output` diabaikan untuk `aks get-credentials`

### <a name="ams"></a>AMS
* Menambahkan `ams streaming-endpoint [start | stop | create | update] wait` perintah
* Menambahkan `ams live-event [create | start | stop | reset] wait` perintah

### <a name="appservice"></a>Layanan aplikasi
* Menambahkan kemampuan untuk membuat dan mengonfigurasi fungsi menggunakan kontainer ACR
* Menambahkan dukungan untuk memperbarui konfigurasi webapp melalui json
* Bantuan yang ditingkatkan untuk `appservice-plan-update`
* Menambahkan dukungan untuk wawasan aplikasi di buat functionapp
* Masalah tetap dengan webapp SSH

### <a name="botservice"></a>Layanan bot
* Peningkatan UX untuk `bot publish`
* Menambahkan peringatan untuk timeout saat berlari `npm install` selama `az bot publish`
* Menghapus char `.` tidak valid dari `--name`  dalam `az bot create`
* Diubah untuk berhenti mengacak nama sumber daya saat membuat Azure Storage, Paket Layanan Aplikasi, Fungsi / Aplikasi Web, dan aplikasi Insights
* [USANG] Argumen usang `--proj-name` yang mendukung `--proj-file-path`
* Diubah `az bot publish` untuk menghapus file penyebaran IIS Node.js yang diambil jika belum ada
* Menambahkan `--keep-node-modules` argumen untuk `az bot publish` tidak menghapus `node_modules` folder di App Service
* Menambahkan `"publishCommand"` pasangan nilai kunci ke output dari `az bot create` saat membuat bot Azure Function atau Web App
  * Nilai `"publishCommand"` adalah perintah yang diisi sebelumnya dengan parameter yang diperlukan untuk mempublikasikan bot yang `az bot publish` baru dibuat.
* Diperbarui `"WEBSITE_NODE_DEFAULT_VERSION"` dalam templat ARM untuk bot SDK v4 untuk menggunakan 10.14.1, bukan 8.9.4

### <a name="key-vault"></a>Key Vault
* Memperbaiki masalah dengan `keyvault secret backup` di mana beberapa pengguna menerima kesalahan `unexpected_keyword` saat menggunakan `--id`

### <a name="monitor"></a>Monitor
* Diubah `monitor metrics alert [create|update]` untuk memungkinkan nilai dimensi `*`

### <a name="network"></a>Jaringan
* Diubah `dns zone export` untuk memastikan CNAME yang diekspor adalah FQDN
* Menambahkan `--gateway-name` parameter untuk `nic ip-config address-pool [add|remove]` mendukung kumpulan alamat backend gateway aplikasi
* Ditambahkan `--traffic-analytics` dan `--workspace` argumen untuk `network watcher flow-log configure` mendukung analisis lalu lintas melalui ruang kerja Log Analytics
* Ditambahkan `--idle-timeout` dan `--floating-ip` untuk `lb inbound-nat-pool [create|update]`

### <a name="policy-insights"></a>Policy Insights
* Menambahkan `policy remediation` perintah untuk mendukung fitur remediasi kebijakan sumber daya

### <a name="rdbms"></a>RDBMS
* Parameter pesan dan perintah bantuan yang disempurnakan

### <a name="redis"></a>Redis
* Menambahkan perintah untuk mengelola aturan firewall (buat, perbarui, hapus, perlihatkan, daftar)
* Menambahkan perintah untuk mengelola server-link (membuat, menghapus, menampilkan, daftar)
* Menambahkan perintah untuk mengelola jadwal patch (buat, perbarui, hapus, perlihatkan)
* Menambahkan dukungan untuk Availability Zones dan Minimum TLS Version ke 'redis create
* [MELANGGAR PERUBAHAN] Dihapus `redis update-settings` dan `redis list-all` perintah
* [MELANGGAR PERUBAHAN] Parameter untuk `redis create`: 'pengaturan penyewa' tidak diterima dalam format kunci[=value]
* [USANG] Menambahkan pesan peringatan untuk perintah usang `redis import-method`

### <a name="role"></a>Peran
* [MELANGGAR PERUBAHAN] Perintah pindah `az identity` di sini dari `vm` perintah

### <a name="sql-vm"></a>SQL VM
* [USANG] Argumen usang `--boostrap-acc-pwd` karena kesalahan ketik

### <a name="vm"></a>VM
* Diubah `vm list-skus` untuk memungkinkan penggunaan `--all` di tempat `--all true`
* Ditambahkan `vmss run-command [invoke | list | show]`
* Bug tetap di mana `vmss encryption enable` akan gagal jika dijalankan sebelumnya
* [MELANGGAR PERUBAHAN] `az identity` Memindahkan perintah ke `role` perintah

## <a name="january-31-2019"></a>Tanggal 31 Januari 2019

Versi 2.0.57

### <a name="core"></a>Core

* Hot Fix untuk [masalah 8399](https://github.com/Azure/azure-cli/issues/8399).

## <a name="january-28-2019"></a>28 Januari 2019

Versi 2.0.56

### <a name="acr"></a>ACR
* Menambahkan dukungan untuk aturan VNet / IP

### <a name="acs"></a>ACS
* Menambahkan Pratinjau Node Virtual
* Menambahkan perintah OpenShift Terkelola
* Menambahkan dukungan untuk operasi pembaruan utama layanan dengan `aks update-credentials -reset-service-principal`

### <a name="ams"></a>AMS
* [MELANGGAR PERUBAHAN] Berganti nama menjadi `ams asset get-streaming-locators``ams asset list-streaming-locators`
* [MELANGGAR PERUBAHAN] Berganti nama menjadi `ams streaming-locator get-content-keys``ams streaming-locator list-content-keys`

### <a name="appservice"></a>Layanan aplikasi
* Menambahkan dukungan untuk wawasan aplikasi `functionapp create`
* Menambahkan dukungan untuk pembuatan paket layanan aplikasi (termasuk Elastic Premium) ke Aplikasi Fungsi
* Masalah pengaturan aplikasi tetap dengan paket Elastic Premium

### <a name="container"></a>Kontainer
* Perintah tambahan `container start`
* Diubah untuk memungkinkan penggunaan nilai desimal untuk CPU selama pembuatan kontainer

### <a name="eventgrid"></a>EventGrid
* Menambahkan `--deadletter-endpoint` parameter ke `event-subscription [create|update]`
* Menambahkan storagequeue dan hybridconnection sebagai nilai baru untuk 'event-subscription [create|update] --endpoint-type'
* Ditambahkan `--max-delivery-attempts` dan `--event-ttl` parameter untuk `event-subscription create` menentukan kebijakan percobaan ulang untuk peristiwa
* Menambahkan pesan peringatan saat `event-subscription [create|update]` webhook sebagai tujuan digunakan untuk berlangganan acara
* Menambahkan parameter sumber-sumber daya-id untuk semua perintah terkait langganan acara dan menandai semua parameter terkait sumber daya lainnya sebagai usang

### <a name="hdinsight"></a>HDInsight
* [MELANGGAR PERUBAHAN] Menghapus `--virtual-network` parameter dan `--subnet-name` dari `hdinsight [application] create`
* [MELANGGAR PERUBAHAN] Diubah `hdinsight create --storage-account` untuk menerima nama atau id akun penyimpanan alih-alih titik akhir gumpalan
* Ditambahkan `--vnet-name` dan `--subnet-name` parameter untuk `hdinsight create`
* Menambahkan dukungan untuk Paket Keamanan Perusahaan dan enkripsi disk ke `hdinsight create`
* Perintah tambahan `hdinsight rotate-disk-encryption-key`
* Perintah tambahan `hdinsight update`

### <a name="iot"></a>IoT
* Menambahkan format pengkodean ke perintah perutean-endpoint

### <a name="kusto"></a>Kusto
* Rilis pratinjau

### <a name="monitor"></a>Monitor
* Mengubah perbandingan ID menjadi kasus yang tidak sensitif

### <a name="profile"></a>Profil
* Aktifkan akun tingkat penyewa untuk identitas layanan terkelola untuk `login`

### <a name="network"></a>Jaringan
* Masalah tetap dengan `express-route update`: di mana `--bandwidth` argumen diabaikan
* Masalah tetap dengan `ddos-protection update` di mana pemahaman yang ditetapkan menyebabkan jejak tumpukan

### <a name="resource"></a>Sumber daya
* Menambahkan dukungan untuk file parameter URI ke `group deployment create`
* Menambahkan dukungan untuk identitas yang dikelola untuk `policy assignment [create|list|show]`

### <a name="sql-virtual-machine"></a>mesin virtual SQL
* Rilis pratinjau

### <a name="storage"></a>Penyimpanan
* Perbaikan yang diubah untuk memperbarui hanya properti yang diubah pada objek yang sama
* Tetap # 8021, data biner dikodekan dalam basis 64 ketika dikembalikan

### <a name="vm"></a>VM
* Diubah `vm encryption enable` untuk memvalidasi keyvault enkripsi disk dan bahwa key encryption key keyvault ada
* Menambahkan `--force` bendera ke `vm encryption enable`

## <a name="january-15-2019"></a>Tanggal 15 Januari 2019

Versi 2.0.55

### <a name="acr"></a>ACR
* Diubah untuk memungkinkan gaya mendorong bagan helm yang tidak ada
* diubah untuk mengizinkan operasi runtime tanpa permintaan ARM
* [USANG] Parameter usang `--resource-group` dalam perintah:
  * `acr login`
  * `acr repository`
  * `acr helm`

### <a name="acs"></a>ACS
* Menambahkan dukungan untuk wilayah ACI baru

### <a name="appservice"></a>Layanan aplikasi
* Masalah tetap dengan mengunggah sertifikat untuk aplikasi yang dihosting di ASE, di mana ASE RG & App RG berbeda
* Diubah `webapp up` untuk menggunakan SKU P1V1 sebagai default untuk Linux
* Diperbaiki `[webapp|functionapp] deployment source config-zip` untuk menampilkan pesan kesalahan yang tepat saat penyebaran gagal
* Perintah tambahan `webapp ssh`

### <a name="botservice"></a>Layanan bot
* Menambahkan pembaruan status penyebaran ke `bot create`

### <a name="configure"></a>Konfigurasikan
* Ditambahkan `none` sebagai format output yang dapat dikonfigurasi

### <a name="cosmosdb"></a>CosmosDB
* Menambahkan dukungan untuk membuat database dengan throughput bersama

### <a name="hdinsight"></a>HDInsight
* Menambahkan perintah untuk mengelola aplikasi
* Menambahkan perintah untuk mengelola tindakan skrip
* Menambahkan perintah untuk mengelola Operations Management Suite (OMS)
* Menambahkan dukungan untuk mencantumkan penggunaan regional ke `hdinsight list-usage`
* [MELANGGAR PERUBAHAN] Tipe klaster default yang dihapus dari `hdinsight create`

### <a name="network"></a>Jaringan
* Ditambahkan `--custom-headers` dan `--status-code-ranges` argumen untuk `traffic-manager profile [create|update]`
* Menambahkan tipe perutean baru: Subnet dan Multivalue
* Ditambahkan `--custom-headers` dan `--subnets` argumen untuk `traffic-manager endpoint [create|update]`
* Masalah tetap di mana memasok `--vnets ""` menyebabkan `ddos-protection update` kesalahan

### <a name="role"></a>Peran
* [USANG] Argumen yang didepresiasi `--password` untuk `create-for-rbac`. Gunakan kata sandi aman yang dihasilkan oleh CLI sebagai gantinya

### <a name="security"></a>Keamanan
* Rilis Awal

### <a name="storage"></a>Penyimpanan
* [MELANGGAR PERUBAHAN] Mengubah `storage [blob|file|container|share] list` jumlah hasil default menjadi 5.000. Gunakan `--num-results *` untuk perilaku asli mengembalikan semua hasil
* Menambahkan `--marker` parameter ke `storage [blob|file|container|share] list`
* Menambahkan penanda log untuk halaman berikutnya ke STDERR untuk `storage [blob|file|container|share] list`
* Menambahkan `storage blob service-properties update` perintah dengan dukungan untuk situs web statis

### <a name="vm"></a>VM
* Berubah `vm [disk|unmanaged-disk]` dan `vmss disk` memiliki parameter yang lebih konsisten
* Menambahkan dukungan untuk referensi gambar penyewa silang `[vm|vmss] create`
* Bug tetap dengan konfigurasi default di `vm diagnostics get-default-config --windows-os`
* Menambahkan argumen `--provision-after-extensions` untuk `vmss extension set` menentukan ekstensi apa yang harus disediakan sebelum ekstensi ditetapkan
* Menambahkan argumen `--replica-count` untuk `sig image-version update` mengatur jumlah replikasi default
* Bug tetap dengan `image create --source` di mana disk os sumber keliru untuk VM dengan nama yang sama, bahkan jika ID sumber daya penuh disediakan

## <a name="december-20-2018"></a>Desember 20, 2018

Versi 2.0.54
### <a name="appservice"></a>Layanan aplikasi
* Masalah tetap di mana `webapp up` akan gagal untuk memindahkan
* Menambahkan dukungan untuk daftar dan memulihkan snapshot webapp
* Menambahkan dukungan untuk `--runtime` bendera ke aplikasi fungsi Windows

### <a name="iotcentral"></a>IoTCentral
* Panggilan API perintah perbarui tetap

### <a name="role"></a>Peran
* [MELANGGAR PERUBAHAN] Diubah `ad [app|sp] list` menjadi hanya mencantumkan 100 objek pertama secara default

### <a name="sql"></a>SQL
* Menambahkan dukungan untuk collation kustom pada instans terkelola

### <a name="vm"></a>VM
* Menambahkan `---os-type` parameter ke `disk create`

## <a name="december-18-2018"></a>18 Desember 2018

Versi 2.0.53
### <a name="acr"></a>ACR
* Menambahkan dukungan untuk impor gambar dari Registri Container eksternal
* Mengembunkan tata letak tabel untuk daftar tugas
* Menambahkan dukungan untuk URL Azure DevOps

### <a name="acs"></a>ACS
* Menambahkan Pratinjau Node Virtual
* Dihapus "(PREVIEW)" dari argumen AAD ke`aks create`
* [USANG] Perintah yang sudah usang `az acs` . Layanan ACS akan pensiun pada 31 Januari 2020
* Menambahkan dukungan Kebijakan Jaringan saat membuat klaster AKS baru
* Persyaratan argumen yang `--nodepool-name` dihapus jika `aks scale` hanya ada satu nodepool

### <a name="appservice"></a>Layanan aplikasi
* Masalah tetap di mana `webapp config container` tidak menghormati `--slot` parameter

### <a name="botservice"></a>Layanan bot
* Menambahkan dukungan untuk `.bot` penguraian file saat menelepon `bot show`
* Fixed AppInsights menyediakan bug
* Bug spasi putih tetap saat berhadapan dengan jalur file
* Mengurangi panggilan jaringan Kudu
* Peningkatan UX perintah umum

### <a name="consumption"></a>Consumption
* Bug tetap untuk API anggaran untuk menampilkan pemberitahuan

### <a name="cosmosdb"></a>CosmosDB
* Menambahkan dukungan untuk memperbarui akun dari multi-master ke single-master

### <a name="maps"></a>Maps
* Menambahkan dukungan untuk S1 SKU untuk `maps account [create|update]`

### <a name="network"></a>Jaringan
* Menambahkan dukungan untuk `--format` dan `--log-version``watcher flow-log configure`
* Masalah tetap dengan `dns zone update` di mana menggunakan "" untuk menghapus resolusi dan pendaftaran VNets tidak berfungsi

### <a name="resource"></a>Sumber daya
* Penanganan tetap parameter lingkup untuk kelompok manajemen di `policy assignment [create|list|delete|show|update]`
* Menambahkan perintah baru `resource wait`

### <a name="storage"></a>Penyimpanan
*  Menambahkan kemampuan untuk memperbarui versi skema log untuk layanan penyimpanan di `storage logging update`

### <a name="vm"></a>VM
* `vm identity remove` Kecelakaan tetap ketika vm yang ditentukan tidak memiliki identitas layanan terkelola yang ditetapkan

## <a name="december-4-2018"></a>4 Desember 2018

Versi 2.0.52
### <a name="core"></a>Core
* Menambahkan dukungan untuk penyediaan sumber daya lintas penyewa untuk prinsipal layanan multi-penyewa
* Bug tetap di mana id disalurkan dari perintah dengan output tsv diurai dengan tidak benar

### <a name="appservice"></a>Layanan aplikasi
* [PREVIEW] Menambahkan `webapp up` perintah yang membantu dalam membuat & menyebarkan konten ke aplikasi
* Memperbaiki bug pada aplikasi windows berbasis kontainer karena perubahan backend

### <a name="network"></a>Jaringan
* Menambahkan `--exclusion` argumen untuk `application-gateway waf-config set` mendukung pengecualian WAF

### <a name="role"></a>Peran
* Menambahkan dukungan untuk pengidentifikasi kustom untuk kredensial kata sandi

### <a name="vm"></a>VM
* [USANG] Parameter usang `vm extension [show|wait] --expand`
* Menambahkan `--force` parameter ke `vm restart` VM yang tidak responsif
* Diubah `[vm|vmss] create --authentication-type` untuk menerima "semua" untuk membuat VM dengan kata sandi dan autentikasi ssh
* Menambahkan `image create --os-disk-caching` parameter untuk mengatur caching disk os untuk gambar

## <a name="november-20-2018"></a>November 20, 2018

Versi 2.0.51
### <a name="core"></a>Core
* Mengubah login MSI untuk tidak menggunakan kembali nama langganan dalam identitas

### <a name="acr"></a>ACR
* Menambahkan token konteks ke langkah tugas
* Menambahkan dukungan untuk mengatur rahasia dalam acr run untuk mencerminkan tugas acr
* Peningkatan dukungan untuk `--top` dan `--orderby` untuk `show-tags` dan `show-manifests` perintah

### <a name="appservice"></a>Layanan aplikasi
* Mengubah batas waktu default penyebaran zip ke polling untuk status meningkat menjadi 5 menit, juga menambahkan properti timeout untuk menyesuaikan nilai ini
* Memperbarui default `node_version`. Mengatur ulang tindakan pertukaran slot, selama swap dua fase mempertahankan semua pengaturan aplikasi & string koneksi
* Penghapusan klien-sisi SKU memeriksa untuk rencana layanan aplikasi Linux membuat
* Memperbaiki kesalahan saat mencoba mendapatkan status zipdeploy

### <a name="iotcentral"></a>IotCentral
* Pemeriksaan ketersediaan subdomain tambahan saat membuat aplikasi IoT Central

### <a name="keyvault"></a>Az.KeyVault
* Bug tetap di mana kesalahan mungkin telah diabaikan

### <a name="network"></a>Jaringan
* Menambahkan `root-cert` subkomite untuk `application-gateway` menangani sertifikasi akar tepercaya
* Ditambahkan `--min-capacity` dan `--custom-error-pages` pilihan untuk `application-gateway [create|update]`:
* Ditambahkan `--zones` untuk dukungan zona ketersediaan ke `application-gateway create`
* Menambahkan argumen `--file-upload-limit`, `--max-request-body-size` dan `--request-body-check` untuk `application-gateway waf-config set`

### <a name="rdbms"></a>Rdbms
* Menambahkan perintah mariadb vnet

### <a name="rbac"></a>Rbac
* Memperbaiki masalah dengan mencoba memperbarui kredensial yang tidak berubah di `ad app update`
* Menambahkan peringatan output untuk mengkomunikasikan perubahan yang melanggar dalam waktu dekat untuk `ad [app|sp] list`

### <a name="storage"></a>Penyimpanan
* Peningkatan penanganan kasus sudut untuk perintah salinan penyimpanan
* Memperbaiki masalah dengan `storage blob copy start-batch` tidak menggunakan kredensial login saat akun tujuan dan sumber sama
* Bug tetap dengan`storage [blob|file] url` tempat `sas_token` yang tidak dimasukkan ke dalam URL
* Menambahkan peringatan perubahan melanggar untuk `[blob|container] list`: akan segera output hanya 5000 hasil pertama secara default

### <a name="vm"></a>VM
* Menambahkan dukungan untuk `[vm|vmss] create --storage-sku` menentukan akun penyimpanan SKU untuk OS terkelola dan disk data secara terpisah
* Mengubah parameter `sig image-version` nama versi menjadi `--image-version -e`
* Argumen `--image-version-name`usang`sig image-version`, digantikan oleh`--image-version`
* Menambahkan dukungan untuk menggunakan disk OS lokal ke `[vm|vmss] create --ephemeral-os-disk`
* Dukungan tambahan untuk `--no-wait``snapshot create/update`
* Perintah tambahan `snapshot wait`
* Menambahkan dukungan untuk menggunakan nama instan dengan `[vm|vmss] extension set --extension-instance-name`

## <a name="november-6-2018"></a>6 November 2018

Versi 2.0.50

### <a name="core"></a>Core
* Menambahkan dukungan untuk kepala layanan sn +emitr auth

### <a name="acr"></a>ACR
* Menambahkan dukungan untuk melakukan dan menarik permintaan git events untuk pemicu sumber Tugas
* Diubah untuk menggunakan Dockerfile default jika tidak ditentukan dalam perintah build

### <a name="acs"></a>ACS
* [MELANGGAR PERUBAHAN] Dihapus `enable_cloud_console_aks_browse` untuk mengaktifkan 'az aks browse' secara default

### <a name="advisor"></a>Advisor
* Rilis GA

### <a name="ams"></a>AMS
* Menambahkan grup perintah baru:
  *  `ams account-filter`
  *  `ams asset-filter`
  *  `ams content-key-policy`
  *  `ams live-event`
  *  `ams live-output`
  *  `ams streaming-endpoint`
  *  `ams mru`
* Menambahkan perintah baru:
  * `ams account check-name`
  * `ams job update`
  * `ams asset get-encryption-key`
  * `ams asset get-streaming-locators`
  * `ams streaming-locator get-content-keys`
* Menambahkan dukungan parameter enkripsi ke `ams streaming-policy create`
* Menambahkan dukungan hingga `ams transform output remove` saat ini dapat dilakukan dengan melewati indeks output untuk dihapus
* Ditambahkan `--correlation-data` dan `--label` argumen ke `ams job` grup perintah
* Ditambahkan `--storage-account` dan `--container` argumen ke `ams asset` grup perintah
* Menambahkan nilai default untuk waktu kadaluwarsa (Sekarang+23h) dan izin (Baca) dalam `ams asset get-sas-url` perintah
* [MELANGGAR PERUBAHAN] Perintah diganti `ams streaming locator` dengan `ams streaming-locator`
* [MELANGGAR PERUBAHAN] Argumen yang diperbarui `--content-keys` dari `ams streaming locator`
* [MELANGGAR PERUBAHAN] Berganti nama menjadi `--content-policy-name` `--content-key-policy-name` dalam `ams streaming locator` perintah
* [MELANGGAR PERUBAHAN] Perintah diganti `ams streaming policy` dengan `ams streaming-policy`
* [MELANGGAR PERUBAHAN] Argumen diganti `--preset-names` dengan `--preset` dalam `ams transform` grup perintah. Sekarang Anda hanya dapat mengatur 1 output/preset pada satu waktu (untuk menambahkan lebih banyak, Anda harus menjalankan `ams transform output add`). Selain itu, Anda dapat mengatur StandardEncoderPreset kustom dengan melewati jalur ke JSON kustom Anda.
* [MELANGGAR PERUBAHAN] Berganti nama menjadi `--output-asset-names ` `--output-assets` dalam `ams job start` perintah. Sekarang menerima daftar aset yang dipisahkan spasi dalam format 'assetName=label'. Aset tanpa label dapat dikirim seperti ini: 'assetName='

### <a name="appservice"></a>AppService
* Memperbaiki bug `az webapp config backup update` yang mencegah pengaturan jadwal cadangan jika belum ditetapkan

### <a name="configure"></a>Konfigurasikan
* Menambahkan YAML ke opsi format output

### <a name="container"></a>Kontainer
* Diubah untuk menunjukkan identitas saat mengekspor grup kontainer ke yaml

### <a name="eventhub"></a>EventHub
* Menambahkan `--enable-kafka` bendera untuk mendukung Kafka `eventhub namespace [create|update]`

### <a name="interactive"></a>Interaktif
* Interaktif sekarang menginstal `interactive` ekstensi, yang akan memungkinkan pembaruan dan dukungan yang lebih cepat

### <a name="monitor"></a>Monitor
* Menambahkan dukungan untuk nama metrik yang mencakup karakter forward-slash (/) dan periode (.)`--condition``monitor metrics alert [create|update]`

### <a name="network"></a>Jaringan
* Nama perintah yang usang `network interface-endpoint` yang mendukung `network private-endpoint`
* Masalah tetap dengan di mana `--peer-circuit` argumen tidak `express-route peering connection create`akan menerima ID
* Masalah tetap di mana `--ip-tags` tidak bekerja dengan benar `public-ip create`

### <a name="profile"></a>Profil
* Ditambahkan `--use-cert-sn-issuer` ke `az login` untuk login utama layanan dengan cert auto-rolls

### <a name="rdbms"></a>RDBMS
* Menambahkan perintah replika mysql

### <a name="resource"></a>Sumber daya
* Menambahkan dukungan untuk grup manajemen dan langganan ke `policy definition|set-definition` perintah

### <a name="role"></a>Peran
* Menambahkan dukungan untuk manajemen izin API, signed-in-user, dan manajemen kredensial & sertifikat
* Diubah `ad sp create-for-rbac` untuk memperjelas kebingungan antara displayName dan nama utama layanan
* Menambahkan dukungan untuk memberikan izin ke aplikasi AAD

### <a name="storage"></a>Penyimpanan
* Menambahkan dukungan untuk terhubung ke layanan penyimpanan hanya dengan SAS dan endpoint (tanpa nama akun atau kunci) seperti yang dijelaskan dalam [Konfigurasikan Azure Storage string koneksi](/azure/storage/common/storage-configure-connection-string).

### <a name="vm"></a>VM
* Menambahkan `storage-sku` argumen untuk `image create` mengatur tipe akun penyimpanan default gambar
* Bug tetap dengan `vm resize` opsi tempat `--no-wait` menyebabkan perintah macet
* Mengubah `vm encryption show` format output tabel untuk memperlihatkan status
* Diubah `vm secret format` menjadi membutuhkan output json / jsonc. Peringatkan pengguna dan default ke output json jika format output yang tidak diinginkan dipilih
* Validasi argumen yang disempurnakan untuk `vm create --image`

## <a name="october-23-2018"></a>Oktober 23, 2018

Versi 2.0.49

### <a name="core"></a>Core
* Masalah tetap dengan `--ids` mana `--subscription` akan diutamakan daripada langganan di `--ids`
* Menambahkan peringatan eksplisit ketika parameter akan diabaikan dengan menggunakan `--ids`

### <a name="acr"></a>ACR
* Memperbaiki masalah pengkodean ACR Build di Python2

### <a name="cdn"></a>CDN
* [MELANGGAR PERUBAHAN] Mengubah `cdn endpoint create`perilaku caching string kueri default untuk tidak lagi default ke "IgnoreQueryString". Sekarang diatur oleh layanan

### <a name="container"></a>Kontainer
* Ditambahkan `Private` sebagai tipe yang valid untuk diteruskan ke '--ip-address'
* Diubah untuk memungkinkan hanya menggunakan ID subnet untuk menyiapkan jaringan virtual untuk grup kontainer
* Diubah untuk memungkinkan penggunaan nama vnet atau id sumber daya untuk mengaktifkan penggunaan vnet dari grup sumber daya yang berbeda
* Ditambahkan `--assign-identity` untuk menambahkan identitas MSI ke grup kontainer
* Ditambahkan `--scope` untuk membuat tugas peran untuk identitas MSI yang ditugaskan sistem
* Menambahkan peringatan saat membuat grup kontainer dengan gambar tanpa proses yang berjalan lama
* Masalah output tabel tetap untuk `list` dan `show` perintah

### <a name="cosmosdb"></a>CosmosDB
* Menambahkan `--enable-multiple-write-locations` dukungan untuk `cosmosdb create`

### <a name="interactive"></a>Interaktif
* Diubah untuk memastikan parameter langganan global muncul dalam parameter

### <a name="iot-central"></a>IoT Pusat
* Menambahkan opsi templat dan nama tampilan untuk pembuatan Aplikasi Pusat IoT
* [MELANGGAR PERUBAHAN] Menghapus dukungan untuk F1 SKU; Gunakan S1 SKU sebagai gantinya

### <a name="monitor"></a>Monitor
* Perubahan pada `monitor activity-log list`:
  * Menambahkan dukungan untuk mendaftarkan semua acara di tingkat langganan
  * Menambahkan `--offset` parameter untuk lebih mudah membuat kueri waktu
  * Peningkatan validasi untuk `--start-time` dan `--end-time` menggunakan format ISO8601 yang lebih luas dan format datetime yang lebih mudah digunakan
  * Ditambahkan `--namespace` sebagai alias untuk opsi usang `--resource-provider`
  * Usang `--filters` karena tidak ada nilai selain yang memiliki opsi yang diketik kuat didukung oleh layanan
* Perubahan pada `monitor metrics list`:
  * Menambahkan `--offset` parameter untuk lebih mudah membuat kueri waktu
  * Peningkatan validasi untuk `--start-time` dan `--end-time` menggunakan format ISO8601 yang lebih luas dan format datetime yang lebih mudah digunakan
* Peningkatan validasi dan `--event-hub` `--event-hub-rule` argumen untuk `monitor diagnostic-settings create`

### <a name="network"></a>Jaringan
* Ditambahkan `--app-gateway-address-pools` dan `--gateway-name` argumen ke `nic create`, untuk mendukung penambahan kolam alamat backend gateway aplikasi ke NIC
* Ditambahkan `--app-gateway-address-pools` dan `--gateway-name` argumen ke `nic ip-config create/update`, untuk mendukung penambahan kolam alamat backend gateway aplikasi ke NIC

### <a name="servicebus"></a>ServiceBus
* Menambahkan Read-Only `migration_state` ke Properti Konfigurasi Migrasi untuk menampilkan Standar Bus Layanan saat ini ke status migrasi ruang nama Premium

### <a name="sql"></a>SQL
* Tetap `sql failover-group create` dan `sql failover-group update` bekerja dengan kebijakan failover manual

### <a name="storage"></a>Penyimpanan
* Pemformatan output tetap `az storage cors list` , semua item memperlihatkan tombol "Layanan" yang benar
* Parameter `--bypass-immutability-policy` tambahan untuk penghapusan kontainer yang diblokir kebijakan immutability

### <a name="vm"></a>VM
* Terapkan mode `None` caching disk untuk seri mesin Lv / Lv2 di `[vm|vmss] create`
* Daftar ukuran yang didukung diperbarui yang mendukung akselerator jaringan untuk `vm create`
* Menambahkan argumen diketik yang kuat untuk iops ultrassd dan konfigurasi mbps untuk `disk create`

## <a name="october-16-2018"></a>Oktober 16, 2018

Versi 2.0.48

### <a name="vm"></a>VM
* Masalah SDK tetap yang menyebabkan instllation Homebrew gagal

## <a name="october-9-2018"></a>9 Oktober 2018

Versi 2.0.47

### <a name="core"></a>Core
* Penanganan kesalahan yang ditingkatkan untuk kesalahan "Permintaan Buruk"

### <a name="acr"></a>ACR
* Menambahkan dukungan untuk format tabel serupa sebagai klien helm

### <a name="acs"></a>ACS
* Ditambahkan `aks [create|scale] --nodepool-name` untuk mengkonfigurasi nama nodepool, dipotong menjadi 12 karakter, default - nodepool1
* Tetap jatuh kembali ke 'scp' ketika Parimiko gagal
* Diubah `aks create` menjadi tidak lagi membutuhkan `--aad-tenant-id`
* Peningkatan penggabungan kredensial Kubernetes saat entri duplikat hadir

### <a name="container"></a>Kontainer
* Diubah `functionapp create` untuk mendukung pembuatan tipe paket konsumsi Linux dengan runtime tertentu
* [PREVIEW] Menambahkan dukungan untuk hosting webapps pada kontainer Windows

### <a name="event-hub"></a>Pusat Aktivitas
* Perintah tetap `eventhub update`
* [MELANGGAR PERUBAHAN] Mengubah `list` perintah untuk menangani kesalahan untuk sumber daya (s) NotFound (404) dengan cara yang khas alih-alih menampilkan daftar kosong

### <a name="extensions"></a>Ekstensi
* Memperbaiki masalah dengan mencoba menambahkan ekstensi yang sudah diinstal

### <a name="hdinsight"></a>HDInsight
* Rilis awal

### <a name="iot"></a>IoT
* Menambahkan comand instalasi ekstensi ke spanduk yang dikelola pertama

### <a name="keyvault"></a>Az.KeyVault
* Diubah untuk membatasi commmands penyimpanan keyvault ke profil API terbaru

### <a name="network"></a>Jaringan
* Tetap `network dns zone create`: Perintah berhasil bahkan jika pengguna telah mengonfigurasi lokasi default. Lihat #6052
* Usang `--remote-vnet-id` untuk `network vnet peering create`
* Ditambahkan `--remote-vnet` ke `network vnet peering create` mana menerima nama atau ID
* Menambahkan dukungan untuk beberapa awalan subnet dengan `network vnet create``--subnet-prefixes`
* Menambahkan dukungan untuk beberapa awalan subnet dengan `network vnet subnet [create|update]``--address-prefixes`
* Masalah tetap dengan `network application-gateway create` yang dicegah membuat gateway dengan `WAF_v2` atau `Standard_v2` SKU
* Menambahkan `--service-endpoint-policy` argumen kenyamanan ke `network vnet subnet update`

### <a name="role"></a>Peran
* Menambahkan dukungan untuk mendaftarkan pemilik aplikasi Azure AD ke `ad app owner`
* Menambahkan dukungan untuk mendaftarkan pemilik utama layanan Azure AD ke `ad sp owner`
* Diubah untuk memastikan definisi peran membuat perintah pembaruan & menerima beberapa konfigurasi izin
* Diubah `ad sp create-for-rbac` untuk memastikan halaman beranda URI selalu "https"

### <a name="service-bus"></a>Service Bus
* [MELANGGAR PERUBAHAN] Mengubah `list` perintah untuk menangani kesalahan untuk sumber daya (s) NotFound (404) dengan cara yang khas alih-alih menampilkan daftar kosong

### <a name="vm"></a>VM
* Bidang kosong `accessSas` tetap di `disk grant-access`
* Diubah `vmss create` menjadi cadangan rentang port frontend yang cukup besar untuk menangani overprovisioning
* Perintah pemutakhiran tetap untuk `sig`
* Menambahkan `--no-wait` dukungan untuk mengelola versi gambar di `sig`
* Diubah `vm list-ip-addresses` untuk memperlihatkan zona ketersediaan alamat IP publik
* Diubah `[vm|vmss] disk attach` untuk mengatur lun default disk ke tempat pertama yang tersedia

## <a name="september-21-2018"></a>21 September 2018

Versi 2.0.46

### <a name="acr"></a>ACR
* Menambahkan perintah Tugas ACR
* Menambahkan perintah lari cepat
* Grup perintah yang tidak dimukakan `build-task`
* Menambahkan `helm` grup perintah untuk mendukung pengelolaan bagan helm dengan ACR
* Menambahkan dukungan untuk idempotent create for managed registry
* Menambahkan bendera tanpa format untuk menampilkan log build

### <a name="acs"></a>ACS
* `install-connector` Mengubah perintah untuk mengatur FQDN Master AKS
* Tetap membuat tugas peran untuk vnet-subnet-id saat tidak menentukan kepala layanan dan skip-role-assignemnt

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk manajemen operasi webjobs (terus menerus dan dipicu)
* az webapp config set supports --fts-state propertyAlso add support fot az functionapp config set & show
* Menambahkan dukungan untuk membawa penyimpanan Anda sendiri untuk webapps
* Menambahkan dukungan untuk mendaftar dan memulihkan aplikasi web yang dihapus

### <a name="batch"></a>Batch
* Mengubah menambahkan tugas untuk `--json-file` mendukung sintaks AddTaskCollectionParameter
* Dokumentasi yang diperbarui dari format yang `--json-file` diterima
* Ditambahkan `--max-tasks-per-node-option` ke `batch pool create`
* Mengubah perilaku `batch account` untuk menampilkan akun yang saat ini masuk jika tidak ada opsi yang ditentukan

### <a name="batch-ai"></a>Batch AI
* Kegagalan pembuatan akun penyimpanan otomatis tetap dalam `batchai cluster create` perintah

### <a name="cognitive-services"></a>Cognitive Services
* Menambahkan completer untuk  `--sku`, `--kind`, `--location` argumen
* Perintah tambahan `cognitiveservices account list-usage`
* Perintah tambahan `cognitiveservices account list-kinds`
* Perintah tambahan `cognitiveservices account list`
* Usang `cognitiveservices list`
* Diubah `--name` menjadi opsional untuk `cognitiveservices account list-skus`

### <a name="container"></a>Kontainer
* Menambahkan kemampuan untuk memulai ulang dan menghentikan grup kontainer yang sedang berjalan
* Ditambahkan `--network-profile` untuk lewat di profil jaringan
* Ditambahkan `--subnet`, `--vnet_name`, untuk memungkinkan membuat grup kontainer dalam VNET
* Mengubah output tabel untuk memperlihatkan status grup kontainer

### <a name="datalake"></a>Datalake
* Menambahkan perintah untuk aturan jaringan virtual

### <a name="interactive-shell"></a>Shell Interaktif
* Memperbaiki kesalahan pada Windows di mana perintah gagal berjalan dengan baik
* Masalah pemuatan perintah tetap dalam interaktif yang disebabkan oleh objek yang tidak dimukakan

### <a name="iot"></a>IoT
* Menambahkan dukungan untuk perutean IoT Hubs

### <a name="key-vault"></a>Key Vault
* Impor kunci Fixed Key Vault untuk kunci RSA

### <a name="network"></a>Jaringan
* Menambahkan `network public-ip prefix` perintah untuk mendukung fitur awalan IP publik
* Menambahkan `network service-endpoint` perintah untuk mendukung fitur kebijakan endpoint layanan
* Menambahkan `network lb outbound-rule` perintah untuk mendukung pembuatan aturan outbound Standard Load Balancer
* Tambahkan `--public-ip-prefix` ke `network lb frontend-ip create/update` untuk mendukung konfigurasi IP frontend menggunakan prefiks IP publik
* Tambahkan `--enable-tcp-reset` ke `network lb rule/inbound-nat-rule/inbound-nat-pool create/update`
* Tambahkan `--disable-outbound-snat` ke `network lb rule create/update`
* Izinkan `network watcher flow-log show/configure` untuk digunakan dengan NSGs klasik
* Menambahkan `network watcher run-configuration-diagnostic` perintah
* Memperbaiki `network watcher test-connectivity` perintah dan menambahkan `--method`, `--valid-status-codes` dan `--headers` properti
* `network express-route create/update`: Tambahkan `--allow-global-reach` bendera
* `network vnet subnet create/update`: Tambahkan dukungan untuk `--delegation`
* Perintah tambahan `network vnet subnet list-available-delegations`
* `network traffic-manager profile create/update`: Menambahkan dukungan untuk `--interval`, `--timeout` dan `--max-failures` untuk konfigurasi Monitor Opsi `--monitor-path`usang, `--monitor-port` dan `--monitor-protocol` mendukung `--path`, , `--port``--protocol`
* `network lb frontend-ip create/update`Memperbaiki logika untuk menetapkan metode alokasi IP pribadi Jika alamat IP pribadi disediakan, alokasi akan statis Jika tidak ada alamat IP pribadi yang disediakan, atau string kosong disediakan untuk alamat IP pribadi, alokasinya dinamis.
* `dns record-set * create/update`: Tambahkan dukungan untuk `--target-resource`
* Menambahkan `network interface-endpoint` perintah ke objek titik akhir antarmuka kueri
* Menambahkan `network profile show/list/delete` untuk manajemen parsial profil jaringan
* Menambahkan `network express-route peering connection` perintah untuk mengelola koneksi mengintip antara ExpressRoutes

### <a name="rdbms"></a>RDBMS
* Menambahkan dukungan untuk layanan MariaDB

### <a name="reservation"></a>Reservasi
* Menambahkan CosmosDb dalam jenis enum sumber daya yang dipesan
* Menambahkan properti nama dalam model Patch

### <a name="manage-app"></a>Mengelola Aplikasi
* Bug tetap dalam `managedapp create --kind MarketPlace` menyebabkan pembuatan instans aplikasi yang dikelola Marketplace macet
* Perintah `feature` yang diubah untuk dibatasi pada profil yang didukung

### <a name="role"></a>Peran
* Menambahkan dukungan untuk mendaftarkan keanggotaan grup pengguna

### <a name="signalr"></a>SignalR
* Rilis pertama

### <a name="storage"></a>Penyimpanan
* Parameter `--auth-mode login` tambahan untuk penggunaan kredensial login pengguna untuk otorisasi gumpalan dan antrian
* Ditambahkan `storage container immutability-policy/legal-hold` untuk mengelola penyimpanan yang tidak berubah

### <a name="vm"></a>VM
* Masalah tetap di mana `vm create --generate-ssh-keys` menimpa file kunci pribadi jika file kunci publik hilang (#4725, #6780)
* Menambahkan dukungan untuk galeri gambar bersama melalui `az sig`

## <a name="august-28-2018"></a>28 Agustus 2018

Versi 2.0.45

### <a name="core"></a>Core

* Masalah tetap pemuatan berkas konfigurasi kosong
* Menambahkan dukungan untuk profil `2018-03-01-hybrid` untuk Azure Stack

### <a name="acr"></a>ACR

* Menambahkan solusi untuk operasi runtime tanpa permintaan ARM
* Diubah untuk mengecualikan file kontrol versi (misalnya, .git, .gitignore) dari tar yang diunggah secara default dalam `build` perintah

### <a name="acs"></a>ACS

* Diubah `aks create` menjadi default ke `Standard_DS2_v2` VM
* Diubah `aks get-credentials` sekarang memanggil api baru untuk mendapatkan kredensial cluster

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk CORS di functionapp & webapp
* Menambahkan dukungan tag ARM pada perintah buat
* Diubah `[webapp|functionapp] identity show` menjadi keluar dengan kode 3 pada sumber daya yang hilang

### <a name="backup"></a>Cadangan

* Diubah `backup vault backup-properties show` menjadi keluar dengan kode 3 pada sumber daya yang hilang

### <a name="bot-service"></a>Layanan Bot

* Rilis Cli Layanan Bot Awal

### <a name="cognitive-services"></a>Cognitive Services

* Menambahkan parameter `--api-properties,` baru yang diperlukan untuk membuat beberapa layanan

### <a name="iot"></a>IoT

* Memperbaiki masalah dengan menghubungkan hub terkait

### <a name="monitor"></a>Monitor

* Menambahkan `monitor metrics alert` perintah untuk peringatan metrik hampir realtime
* Perintah usang `monitor alert`

### <a name="network"></a>Jaringan

* Diubah `network application-gateway ssl-policy predefined show` menjadi keluar dengan kode 3 pada sumber daya yang hilang

### <a name="resource"></a>Sumber daya

* Diubah `provider operation show` menjadi keluar dengan kode 3 pada sumber daya yang hilang

### <a name="storage"></a>Penyimpanan

* Diubah `storage share policy show` menjadi keluar dengan kode 3 pada sumber daya yang hilang

### <a name="vm"></a>VM

* Diubah `vm/vmss identity show` menjadi keluar dengan kode 3 pada sumber daya yang hilang
* Usang `--storage-caching` untuk `vm create`

## <a name="auguest-14-2018"></a>Auguest 14, 2018

Versi 2.0.44

### <a name="core"></a>Core

* Tampilan numerik tetap dalam `table` output
* Menambahkan format output YAML

### <a name="telemetry"></a>Telemetri

* Peningkatan pelaporan telemetri

### <a name="acr"></a>ACR

* Menambahkan `content-trust policy` perintah
* Masalah tetap di mana `.dockerignore` tidak ditangani dengan benar

### <a name="acs"></a>ACS

* Diubah `az acs/aks install-cli` menjadi instalasi di bawah `%USERPROFILE%\.azure-kubectl` pada Windows
* Diubah `az aks install-connector` untuk mendeteksi apakah cluster memiliki RBAC dan mengkonfigurasi Konektor ACI dengan tepat
* Diubah menjadi tugas peran ke subnet saat disediakan
* Menambahkan opsi baru untuk "melewatkan tugas peran" untuk subnet saat disediakan
* Diubah untuk melewatkan tugas peran ke subnet saat tugas sudah ada

### <a name="appservice"></a>AppService

* Memperbaiki bug yang mencegah membuat aplikasi fungsi menggunakan akun penyimpanan dalam grup sumber daya eksternal
* Memperbaiki crash pada penyebaran zip

### <a name="batchai"></a>BatchAI

* Mengubah output logger untuk pembuatan akun penyimpanan otomatis untuk menentukan " *grup* sumber daya".

### <a name="container"></a>Kontainer

* Ditambahkan `--secure-environment-variables` untuk meneruskan variabel lingkungan aman ke wadah

### <a name="iot"></a>IoT

* [MELANGGAR PERUBAHAN] Menghapus perintah usang yang telah pindah ke ekstensi iot
* Elemen yang diperbarui untuk tidak mengasumsikan `azure-devices.net` domain

### <a name="iot-central"></a>Iot Tengah

* Rilis awal modul IoT Central

### <a name="keyvault"></a>Az.KeyVault


* Menambahkan perintah untuk mengelola akun penyimpanan dan sas-definition
* Menambahkan perintah untuk aturan jaringan
* Menambahkan `--id` parameter ke operasi rahasia, kunci, dan sertifikat
* Menambahkan dukungan untuk KV mgmt versi multi-api
* Menambahkan dukungan untuk versi multi-api pesawat data KV

### <a name="relay"></a>Relay

* Rilis awal

### <a name="sql"></a>Sql

* Menambahkan `sql failover-group` perintah

### <a name="storage"></a>Penyimpanan

* [MELANGGAR PERUBAHAN] Diubah `storage account show-usage` menjadi memerlukan `--location` parameter dan akan mendaftar berdasarkan wilayah
* Parameter `--resource-group` yang diubah menjadi opsional untuk `storage account` perintah
* Menghapus peringatan 'Prasyarat gagal' untuk kegagalan individu dalam perintah batch untuk pesan agregat tunggal
* Mengubah `[blob|file] delete-batch` perintah agar tidak lagi mengeluarkan array null
* Mengubah `blob [download|upload|delete-batch]` perintah untuk membaca sas-token dari url kontainer

### <a name="vm"></a>VM

* Menambahkan filter umum untuk `vm list-skus` kemudahan penggunaan

## <a name="july-31-2018"></a>31 Juli 2018

Versi 2.0.43

### <a name="acr"></a>ACR

* Menambahkan `--with-secure-properties` bendera ke `acr build-task show` perintah
* Perintah tambahan `acr build-task update-build`

### <a name="acs"></a>ACS

* Diubah untuk mengembalikan 0 (kesuksesan) saat diakhiri dengan `az aks browse` menekan [Ctrl+C]

### <a name="batch"></a>Batch

* Bug tetap saat menampilkan token AAD di cloudshell

### <a name="container"></a>Kontainer

* Persyaratan yang dihapus untuk `--log-analytics-workspace-key` nama atau ID saat di mengatur langganan

### <a name="network"></a>Jaringan

* Menambahkan dukungan DNS ke 2017-03-09-profile for Azure Stack

### <a name="resource"></a>Sumber daya

* Ditambahkan `--rollback-on-error` untuk `group deployment create` menjalankan penyebaran yang diketahui baik pada kesalahan
* Masalah tetap di mana `--parameters {}` dengan `group deployment create` mengakibatkan kesalahan

### <a name="role"></a>Peran

* Menambahkan dukungan untuk profil tumpukan 2017-03-09-profile
* Masalah tetap di mana parameter `app update` pembaruan generik tidak akan berfungsi dengan benar

### <a name="search"></a>Cari

* Menambahkan perintah untuk layanan Azure Search

### <a name="service-bus"></a>Service Bus

* Menambahkan grup perintah migrasi untuk memigrasikan ruang nama dari Standar Bus Layanan ke Premium
* Menambahkan properti opsional baru ke Bus Layanan antrian dan Langganan
  *  `--enable-batched-operations` dan `--enable-dead-lettering-on-message-expiration` di `queue`
  *  `--dead-letter-on-filter-exceptions` di `subscriptions`

### <a name="storage"></a>Penyimpanan

* Menambahkan dukungan untuk mengunduh file besar menggunakan satu koneksi
* Perintah `show` dikonversi yang terlewatkan dari kegagalan dengan kode keluar 3 pada sumber daya yang hilang

### <a name="vm"></a>VM

* Menambahkan dukungan ke kumpulan ketersediaan daftar menurut langganan
* Dukungan tambahan untuk `StandardSSD_LRS`
* Menambahkan dukungan untuk grup keamanan aplikasi untuk membuat set skala VM
* [MELANGGAR PERUBAHAN] Diubah `[vm|vmss] create`, `[vm|vmss] identity assign`, dan `[vm|vmss] identity remove` untuk menghasilkan identitas yang ditetapkan pengguna dalam format kamus

## <a name="july-18-2018"></a>Juli 18, 2018

Versi 2.0.42

### <a name="core"></a>Core

* Menambahkan dukungan untuk login berbasis browser di jendela bash WSL
* Menambahkan `--force-string` bendera ke semua perintah pembaruan generik
* [MELANGGAR PERUBAHAN] Mengubah perintah 'tampilkan' untuk mencatat pesan kesalahan dan gagal dengan kode keluar 3 pada sumber daya yang hilang

### <a name="acr"></a>ACR

* [MELANGGAR PERUBAHAN] Diperbarui '--no-push' ke bendera murni dalam perintah 'acr build'
* Ditambahkan `show` dan `update` perintah di bawah `acr repository` grup
* Menambahkan `--detail` bendera untuk `show-manifests` dan `show-tags` untuk menampilkan informasi yang lebih rinci
* Menambahkan `--image` parameter untuk mendukung mendapatkan detail build atau log berdasarkan gambar

### <a name="acs"></a>ACS

* Diubah `az aks create` menjadi kesalahan jika `--max-pods` kurang dari 5

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk PremiumV2 skus

### <a name="batch"></a>Batch

* Bug tetap menggunakan kredensial token pada mode shell cloud
* Mengubah input JSON menjadi kasus-tidak sensitif

### <a name="batch-ai"></a>Batch AI

* Perintah tetap `az batchai job exec`

### <a name="container"></a>Kontainer

* Menghapus persyaratan untuk nama pengguna dan kata sandi untuk pendaftar non dockerhub
* Memperbaiki kesalahan saat membuat grup kontainer dari file yaml

### <a name="network"></a>Jaringan

* Menambahkan `--no-wait` dukungan untuk `network nic [create|update|delete]`
* Ditambahkan `network nic wait`
* Argumen usang `--ids` untuk `network vnet [subnet|peering] list`
* Menambahkan `--include-default` bendera untuk menyertakan aturan keamanan default dalam output `network nsg rule list`

### <a name="resource"></a>Sumber daya

* Menambahkan `--no-wait` dukungan untuk `group deployment delete`
* Menambahkan `--no-wait` dukungan untuk `deployment delete`
* Perintah tambahan `deployment wait`
* Masalah tetap di mana perintah tingkat `az deployment` langganan secara keliru muncul untuk profil 2017-03-09-profile

### <a name="sql"></a>SQL

* Tetap 'Nama grup sumber daya yang disediakan ... tidak cocok dengan nama dalam kesalahan Url saat menentukan nama `sql db copy` dan `sql db replica create` perintah kolam elastis
* Perbolehkan mengonfigurasi server sql default dengan mengeksekusi `az configure --defaults sql-server=<name>`
* Formatter tabel yang diimplementasikan untuk `sql server`, , `sql server firewall-rule`, `sql list-usages`dan `sql show-usage` perintah

### <a name="storage"></a>Penyimpanan

* Menambahkan `pageRanges` properti ke `storage blob show` output yang akan diisi untuk gumpalan halaman

### <a name="vm"></a>VM

* [MELANGGAR PERUBAHAN] Diubah `vmss create` untuk digunakan `Standard_DS1_v2` sebagai ukuran instans default
* Menambahkan `--no-wait` dukungan untuk `vm extension [set|delete]` dan `vmss extension [set|delete]`
* Ditambahkan `vm extension wait`

## <a name="july-3-2018"></a>Juli 3, 2018

### <a name="version-2041"></a>Versi 2.0.41

### <a name="aks"></a>AKS

* Mengubah pemantauan untuk menggunakan ID langganan

### <a name="version-2040"></a>Versi 2.0.40

### <a name="core"></a>Core

* Menambahkan aliran kode otorisasi baru untuk login interaktif

### <a name="acr"></a>ACR

* Menambahkan status pembuatan polling
* Menambahkan dukungan untuk nilai-nilai enum kasus-tidak sensitif
* Ditambahkan `--top` dan `--orderby` parameter untuk `show-manifests`

### <a name="acs"></a>ACS

* [MELANGGAR PERUBAHAN] Aktifkan kontrol akses berbasis peran Kubernetes secara default
* Menambahkan `--disable-rbac` argumen dan usang `--enable-rbac` karena itu adalah default sekarang
* Opsi yang diperbarui untuk `aks browse` perintah. Menambahkan `--listen-port` dukungan
* Memperbarui paket bagan helm default untuk `aks install-connector` perintah. Gunakan virtual-kubelet-for-aks-latest.tgz
* Menambahkan `aks enable-addons` dan `aks disable-addons` perintah untuk memperbarui klaster yang sudah ada

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk menonaktifkan identitas melalui `webapp identity remove`
* Tag dihapus `preview` untuk fitur Identitas

### <a name="backup"></a>Cadangan

* Definisi modul yang diperbarui

### <a name="batchai"></a>BatchAI

* Output tabel tetap untuk `batchai cluster node list` dan `batchai job node list` perintah

### <a name="cloud"></a>Cloud

* Menambahkan `acr login` akhiran server ke konfigurasi cloud

### <a name="container"></a>Kontainer

* Diubah `container create` menjadi default ke operasi yang sudah berjalan lama
* Menambahkan parameter `--log-analytics-workspace` Log Analytics dan `--log-analytics-workspace-key`
* Menambahkan `--protocol` parameter untuk menentukan protokol jaringan mana yang akan digunakan

### <a name="extension"></a>Ekstensi

* Diubah `extension list-available` menjadi hanya menampilkan ekstensi yang kompatibel dengan versi CLI

### <a name="network"></a>Jaringan

* Masalah tetap di mana tipe catatan sensitif terhadap kasus ([#6602](https://github.com/Azure/azure-cli/issues/6602))

### <a name="rdbms"></a>Rdbms

* Menambahkan `[postgres|myql] server vnet-rule` perintah

### <a name="resource"></a>Sumber daya

* Menambahkan grup operasi baru `deployment`

### <a name="vm"></a>VM

* Menambahkan dukungan untuk menghapus identitas yang ditetapkan sistem

## <a name="june-25-2018"></a>Tanggal 25 Juni 2018

Versi 2.0.39

### <a name="cli"></a>CLI

* Pemangkasan file yang diperbarui di penginstal MSI untuk memperbaiki masalah instalasi ekstensi

## <a name="june-19-2018"></a>Juni 19, 2018

Versi 2.0.38

### <a name="core"></a>Core

* Menambahkan dukungan global untuk `--subscription` sebagian besar perintah

### <a name="acr"></a>ACR

* Ditambahkan `azure-storage-blob` sebagai dependensi
* Mengubah konfigurasi CPU default dengan `acr build-task create` menggunakan 2 core

### <a name="acs"></a>ACS

* Opsi `aks use-dev-spaces` perintah yang diperbarui. Menambahkan `--update` dukungan
* Diubah `aks get-credentials --admin` menjadi tidak menempatkan konteks pengguna di `$HOME/.kube/config`
* Properti baca-saja `nodeResourceGroup` yang terbuka pada kluster terkelola
* Galat perintah tetap `acs browse`
* Dibuat `--connector-name` opsional untuk `aks install-connector`, `aks upgrade-connector` dan `aks remove-connector`
* Menambahkan wilayah Instans Azure Container baru untuk `aks install-connector`
* Menambahkan lokasi yang dinormalisasi ke dalam nama rilis helm dan nama node ke `aks install-connector`

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk versi urllib yang lebih baru
* Menambahkan dukungan untuk `functionapp create` menggunakan paket layanan aplikasi dari grup sumber daya eksternal

### <a name="batch"></a>Batch

* `azure-batch-extensions` Menghilangkan dependensi

### <a name="batch-ai"></a>Batch AI

* Menambahkan dukungan untuk ruang kerja. Ruang kerja memungkinkan untuk mengelompokkan kluster, server file, dan eksperimen dalam grup yang menghapus batasan jumlah sumber daya dapat dibuat.
* Menambahkan dukungan untuk eksperimen. Eksperimen memungkinkan untuk mengelompokkan pekerjaan dalam koleksi yang menghilangkan batasan jumlah pekerjaan yang diciptakan
* Menambahkan dukungan untuk mengkonfigurasi `/dev/shm` untuk pekerjaan yang berjalan dalam wadah docker
* Ditambahkan `batchai cluster node exec` dan `batchai job node exec` perintah. Perintah ini memungkinkan untuk mengeksekusi perintah apa pun secara langsung pada node dan menyediakan fungsionalitas untuk penerusan port.
* Menambahkan dukungan untuk `--ids` `batchai` perintah
* [MELANGGAR PERUBAHAN] Semua cluster dan fileserver harus dibuat di bawah ruang kerja
* [MELANGGAR PERUBAHAN] Pekerjaan harus dibuat di bawah eksperimen
* [MELANGGAR PERUBAHAN] Dihapus `--nfs-resource-group` dari `cluster create` dan `job create` perintah. Untuk me-mount NFS milik kelompok ruang kerja / sumber daya yang berbeda menyediakan ID ARM server file melalui `--nfs` opsi
* [MELANGGAR PERUBAHAN] Dihapus `--cluster-resource-group` dari `job create` perintah. Untuk mengirimkan pekerjaan pada cluster milik ruang kerja / kelompok sumber daya yang berbeda menyediakan ID ARM cluster melalui `--cluster` opsi
* [MELANGGAR PERUBAHAN] Atribut yang dihapus `location` dari pekerjaan, cluster, dan server file. Lokasi sekarang adalah atribut ruang kerja.
* [MELANGGAR PERUBAHAN] Dihapus `--location` dari `job create`, `cluster create` dan `file-server create` perintah
* [MELANGGAR PERUBAHAN] Mengubah nama opsi pendek untuk membuat antarmuka lebih konsisten:
  - Berganti nama [`--config`, `-c`] menjadi [`--config-file`, `-f`]
  - Berganti nama [`--cluster`, `-r`] menjadi [`--cluster`, `-c`]
  - Berganti nama [`--cluster`, `-n`] menjadi [`--cluster`, `-c`]
  - Berganti nama [`--job`, `-n`] menjadi [`--job`, `-j`]

### <a name="maps"></a>Maps

* [MELANGGAR PERUBAHAN] Diubah `maps account create` menjadi persyaratan menerima Ketentuan Layanan baik dengan prompt interaktif atau `--accept-tos` bendera

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk `https` `network lb probe create` [#6571](https://github.com/Azure/azure-cli/issues/6571)
* Masalah tetap di mana `--endpoint-status` kasus sensitif. [#6502](https://github.com/Azure/azure-cli/issues/6502)

### <a name="reservations"></a>Reservasi

* [MELANGGAR PERUBAHAN] Menambahkan parameter `ReservedResourceType` yang diperlukan untuk `reservations catalog show`
* Menambahkan parameter `Location`ke `reservations catalog show`
* [MELANGGAR PERUBAHAN] Dihapus `kind` dari `ReservationProperties`
* [MELANGGAR PERUBAHAN] Berganti nama menjadi `capabilities` `sku_properties` di `Catalog`
* [MELANGGAR PERUBAHAN] Dihapus `size` dan `tier` properti dari `Catalog`
* Menambahkan parameter `InstanceFlexibility` ke `reservations reservation update`

### <a name="role"></a>Peran

* Penanganan kesalahan yang ditingkatkan

### <a name="sql"></a>SQL

* Memperbaiki kesalahan membingungkan saat menjalankan `az sql db list-editions` lokasi yang tidak tersedia untuk langganan Anda

### <a name="storage"></a>Penyimpanan

* Mengubah output `storage blob download` tabel agar lebih mudah dibaca

### <a name="vm"></a>VM

* Peningkatan perbaikan vm size check untuk dukungan jaringan yang dipercepat di `vm create`
* Peringatan tambahan untuk `vmss create` itu ukuran vm default akan dialihkan dari `Standard_D1_v2` ke `Standard_DS1_v2`
* Ditambahkan `--force-update` untuk `[vm|vmss] extension set` memperbarui ekstensi bahkan ketika konfigurasi tidak berubah

## <a name="june-13-2018"></a>13 Juni 2018

### <a name="version-2037"></a>Versi 2.0.37

### <a name="core"></a>Core

* Peningkatan telemetri interaktif

### <a name="version-2036"></a>Versi 2.0.36

### <a name="aks"></a>AKS

* Menambahkan opsi jaringan tingkat lanjut ke `aks create`
* Menambahkan argumen untuk `aks create` mengaktifkan pemantauan dan perutean HTTP
* Menambahkan `--no-ssh-key` argumen ke `aks create`
* Menambahkan `--enable-rbac` argumen ke `aks create`
* [PREVIEW] Menambahkan dukungan untuk otentikasi Azure Active Directory ke`aks create`

### <a name="appservice"></a>AppService

* Memperbaiki masalah dengan versi urllib yang tidak kompatibel

## <a name="june-5-2018"></a>Juni 5, 2018

### <a name="version-2035"></a>Versi 2.0.35

### <a name="interactive"></a>Interaktif

* Menambahkan batasan pada dependensi mode interaktif

### <a name="version-2034"></a>Versi 2.0.34

### <a name="core"></a>Core

* Menambahkan dukungan untuk referensi sumber daya lintas penyewa
* Peningkatan keandalan upload telemetri

### <a name="acr"></a>ACR

* Menambahkan dukungan untuk VSTS sebagai lokasi sumber jarak jauh
* Perintah tambahan `acr import`

### <a name="aks"></a>AKS

* Diubah `aks get-credentials` untuk membuat file konfigurasi kube dengan izin sistem file yang lebih aman

### <a name="batch"></a>Batch

* Bug tetap dalam pemformatan tabel daftar Pool [[Masalah #4378](https://github.com/Azure/azure-cli/issues/4378)]

### <a name="iot"></a>IoT

* Menambahkan dukungan untuk membuat Basic Tier IoT Hubs

### <a name="network"></a>Jaringan

* Ditingkatkan `network vnet peering`

### <a name="policy-insights"></a>Policy Insights

* Rilis Awal

### <a name="arm"></a>ARM

* Menambahkan `account management-group` perintah.

### <a name="sql"></a>SQL

* Menambahkan perintah instans terkelola baru:
  * `sql mi create`
  * `sql mi show`
  * `sql mi list`
  * `sql mi update`
  * `sql mi delete`
* Menambahkan perintah database terkelola baru:
  * `sql midb create`
  * `sql midb show`
  * `sql midb list`
  * `sql midb restore`
  * `sql midb delete`

### <a name="storage"></a>Penyimpanan

* Menambahkan mimetipe ekstra untuk json dan javascript yang akan disimpulkan dari ekstensi file

### <a name="vm"></a>VM

* Diubah `vm list-skus` untuk menggunakan kolom tetap dan menambahkan peringatan bahwa `Tier` dan `Size` akan dihapus
* Menambahkan `--accelerated-networking` opsi ke `vm create`
* Ditambahkan `--tags` ke `identity create`

## <a name="may-22-2018"></a>22 Mei 2018

Versi 2.0.33

### <a name="core"></a>Core

* Menambahkan dukungan untuk memperluas `@` nama file

### <a name="acs"></a>ACS

* Menambahkan perintah `aks use-dev-spaces` Dev-Spaces baru dan `aks remove-dev-spaces`
* Kesalahan ketik tetap dalam pesan bantuan

### <a name="appservice"></a>AppService

* Perintah pembaruan generik yang disempurnakan
* Menambahkan dukungan async untuk `webapp deployment source config-zip`

### <a name="container"></a>Kontainer

* Menambahkan dukungan untuk mengekspor grup kontainer dalam format yaml
* Menambahkan dukungan untuk menggunakan file yaml untuk membuat / memperbarui grup kontainer

### <a name="extension"></a>Ekstensi

* Penghapusan ekstensi yang ditingkatkan

### <a name="interactive"></a>Interaktif

* Mengubah penebangan untuk membisukan parser untuk penyelesaian
* Peningkatan penanganan cache bantuan yang buruk

### <a name="keyvault"></a>Az.KeyVault

* Perintah keyvault tetap untuk bekerja di cloud shell atau VM dengan identitas

### <a name="network"></a>Jaringan

* Memperbaiki masalah di mana `network watcher show-topology` tidak akan bekerja dengan vnet dan / atau nama subnet [#6326](https://github.com/Azure/azure-cli/issues/6326)
* Memperbaiki masalah di mana beberapa `network watcher` perintah akan mengklaim Network Watcher tidak diaktifkan untuk wilayah ketika itu adalah [# 6264](https://github.com/Azure/azure-cli/issues/6264)

### <a name="sql"></a>SQL

* [MELANGGAR PERUBAHAN] Objek respons yang diubah dikembalikan `db` dan `dw` perintah:
    * Berganti nama menjadi `serviceLevelObjective` properti `currentServiceObjectiveName`
    * Dihapus `currentServiceObjectiveId` dan `requestedServiceObjectiveId` properti
    * Properti `maxSizeBytes` yang diubah menjadi nilai integer, bukan string
* [MELANGGAR PERUBAHAN] Mengubah hal-hal berikut `db` dan `dw` properti menjadi hanya baca:
    * `requestedServiceObjectiveName`.  Untuk memperbarui, gunakan `--service-objective` parameter atau atur `sku.name` properti
    * `edition`. Untuk memperbarui, gunakan `--edition` parameter atau atur `sku.tier` properti
    * `elasticPoolName`. Untuk memperbarui, gunakan `--elastic-pool` parameter atau atur `elasticPoolId` properti
* [MELANGGAR PERUBAHAN] Mengubah properti berikut `elastic-pool` menjadi hanya baca:
    * `edition`. Untuk memperbarui, gunakan `--edition` parameter
    * `dtu`. Untuk memperbarui, gunakan `--capacity` parameter
    *  `databaseDtuMin`. Untuk memperbarui, gunakan `--db-min-capacity` parameter
    *  `databaseDtuMax`. Untuk memperbarui, gunakan `--db-max-capacity` parameter
* Ditambahkan `--family` dan `--capacity` parameter untuk `db`, `dw`, dan `elastic-pool` perintah.
* Menambahkan formatter tabel ke `db`, `dw`, dan `elastic-pool` perintah.

### <a name="storage"></a>Penyimpanan

* Menambahkan completer untuk `--account-name` argumen
* Memperbaiki masalah dengan `storage entity query`

### <a name="vm"></a>VM

* [MELANGGAR PERUBAHAN] Dihapus `--write-accelerator` dari `vm create`. Dukungan yang sama dapat diakses melalui `vm update` atau `vm disk attach`
* Pencocokan gambar ekstensi tetap di `[vm|vmss] extension`
* Ditambahkan `--boot-diagnostics-storage` untuk `vm create` menangkap log boot
* Ditambahkan `--license-type` ke `[vm|vmss] update`

## <a name="may-7-2018"></a>7 Mei 2018

Versi 2.0.32

### <a name="core"></a>Core

* Memperbaiki pengecualian yang tidak ditangani saat mengambil rahasia dari akun utama layanan dengan sertifikat
* Menambahkan dukungan terbatas untuk argumen posisional
* Perbaiki masalah di mana `--query` tidak dapat digunakan dengan `--ids`. [#5591](https://github.com/Azure/azure-cli/issues/5591)
* Skenario perpipaan yang ditingkatkan dari perintah saat menggunakan `--ids`. Mendukung `-o tsv` dengan kueri yang ditentukan atau `-o json` tanpa menentukan kueri
* Menambahkan saran perintah tentang kesalahan jika pengguna memiliki kesalahan ketik dalam perintah mereka
* Memperbaiki kesalahan saat pengguna mengetik `az ''`
* Menambahkan dukungan tipe sumber daya kustom untuk modul perintah dan ekstensi

### <a name="acr"></a>ACR

* Menambahkan perintah Build ACR
* Sumber daya yang disempurnakan tidak menemukan pesan kesalahan
* Peningkatan kinerja pembuatan sumber daya dan penanganan kesalahan
* Peningkatan login acr di konsol non-standar dan WSL
* Perintah repositori yang disempurnakan perintah pesan kesalahan
* Kolom tabel yang diperbarui dan pemesanan

### <a name="acs"></a>ACS

* Menambahkan peringatan yang `az aks` merupakan layanan pratinjau
* Memperbaiki masalah `aks install-connector` izin ketika `--aci-resource-group` tidak ditentukan

### <a name="ams"></a>AMS

* Rilis awal - Kelola sumber daya Azure Media Services

### <a name="appservice"></a>Layanan aplikasi

* Memperbaiki bug saat `webapp delete` `--slot` disediakan
* Dihapus `--runtime-version` dari `webapp auth update`
* Menambahkan dukungan untuk mintlsversion\_\_ & https2.0
* Menambahkan dukungan untuk multikontainer

### <a name="batch-ai"></a>Batch AI

* Diubah `batchai create cluster` untuk menghormati prioritas vm yang dikonfigurasi dalam file konfigurasi kluster

### <a name="cognitive-services"></a>Cognitive Services

* Kesalahan ketik tetap misalnya untuk `cognitiveservices account create` [#5603](https://github.com/Azure/azure-cli/issues/5603)

### <a name="consumption"></a>Consumption

* Menambahkan perintah baru untuk API anggaran

### <a name="container"></a>Kontainer

* Persyaratan `--registry-server` yang dihapus untuk `container create` kapan server registri disertakan dalam nama gambar

### <a name="cosmos-db"></a>Cosmos DB

* Memperkenalkan dukungan VNET untuk Azure CLI - Cosmos DB

### <a name="dms"></a>DMS

* Rilis awal - Menambahkan dukungan untuk skenario migrasi SQL ke Azure SQL

### <a name="extension"></a>Ekstensi

* Bug tetap di mana metadata ekstensi berhenti ditampilkan

### <a name="interactive"></a>Interaktif

* Izinkan completer interaktif berfungsi dengan argumen posisional
* Output yang lebih user-friendly saat pengguna mengetik '\'
* Penyelesaian tetap untuk parameter tanpa bantuan
* Deskripsi tetap untuk grup perintah

### <a name="lab"></a>Laboratorium

* Regresi tetap dari konversi bakat

### <a name="network"></a>Jaringan

* [MELANGGAR PERUBAHAN] `--ids` Menghapus parameter untuk:
  * `express-route auth list`
  * `express-route peering list`
  * `nic ip-config list`
  * `nsg rule list`
  * `route-filter rule list`
  * `route-table route list`
  * `traffic-manager endpoint list`

### <a name="profile"></a>Profil

* Deteksi sumber tetap `disk create`
* [MELANGGAR PERUBAHAN] Dihapus `--msi-port` dan `--identity-port` karena tidak lagi digunakan
* Kesalahan ketik tetap dalam `account get-access-token` ringkasan singkat

### <a name="redis"></a>Redis

* Usang `redis patch-schedule patch-schedule show` demi `redis patch-schedule show`
* Usang `redis list-all`. Fungsi ini telah dilipat menjadi `redis list`
* Usang `redis import-method` demi `redis import`
* Menambahkan dukungan untuk `--ids` berbagai perintah

### <a name="role"></a>Peran

* [MELANGGAR PERUBAHAN] Dihapus usang `ad sp reset-credentials`

### <a name="storage"></a>Penyimpanan

* Izinkan tujuan sas-token untuk mengajukan permohonan ke sumber salinan gumpalan jika sumber sas dan kunci akun tidak ditentukan
* Terekspos --socket-timeout untuk upload dan unduhan gumpalan
* Perlakukan nama gumpalan yang dimulai dengan pemisah jalur sebagai jalur relatif
* Izinkan `storage blob copy --source-sas` dengan memulai kueri char, '?'
* Tetap `storage entity query --marker` untuk menerima daftar key=values

### <a name="vm"></a>VM

* Memperbaiki logika deteksi yang tidak valid pada gumpalan uri yang tidak terurus
* Menambahkan enkripsi disk dukungan w / o pengguna menyediakan prinsip layanan
* [MELANGGAR PERUBAHAN] Jangan gunakan VM 'ManagedIdentityExtension' untuk dukungan MSI
* Menambahkan dukungan untuk kebijakan penggusuran untuk `vmss`
* [MELANGGAR PERUBAHAN] Dihapus `--ids` dari:
  * `vm extension list`
  * `vm secret list`
  * `vm unmanaged-disk list`
  * `vmss nic list`
* Menambahkan dukungan akselerator tulis
* Ditambahkan `vmss perform-maintenance`
* Diperbaiki `vm diagnostics set` untuk mendeteksi tipe OS VM dengan andal
* Diubah `vm resize` untuk memeriksa apakah ukuran yang diminta berbeda dari yang ditetapkan saat ini dan diperbarui hanya pada perubahan


## <a name="april-10-2018"></a>10 April 2018

Versi 2.0.31

### <a name="acr"></a>ACR

* Peningkatan penanganan kesalahan dari fallback wincred

### <a name="acs"></a>ACS

* Mengubah SDK yang dibuat SPN agar berlaku selama 5 tahun

### <a name="appservice"></a>Layanan aplikasi

* [MELANGGAR PERUBAHAN]: Removed `assign-identity`
* Pengecualian tanpa ajar tetap untuk paket webapp yang tidak ada

### <a name="batchai"></a>BatchAI

* Menambahkan dukungan untuk API 2018-03-01

  - Pemasangan tingkat pekerjaan
  - Variabel lingkungan dengan nilai rahasia
  - Setelan penghitung kinerja
  - Pelaporan segmen jalur khusus pekerjaan
  - Dukungan untuk subfolder dalam api file daftar
  - Penggunaan dan batas pelaporan
  - Perbolehkan menentukan tipe caching untuk server NFS
  - Dukungan untuk gambar kustom
  - Menambahkan dukungan toolkit pyTorch

* Perintah tambahan `job wait` yang memungkinkan untuk menunggu penyelesaian pekerjaan dan melaporkan kode keluar pekerjaan
* Perintah tambahan `usage show` untuk mencantumkan penggunaan dan batasan sumber daya Batch AI saat ini untuk berbagai wilayah
* Awan nasional didukung
* Menambahkan argumen baris perintah pekerjaan untuk me-mount sistem file pada tingkat pekerjaan selain file konfigurasi
* Menambahkan lebih banyak opsi untuk menyesuaikan kluster - prioritas vm, subnet, jumlah node awal untuk kluster skala otomatis, menentukan gambar kustom
* Menambahkan opsi baris perintah untuk menentukan tipe caching untuk NFS yang dikelola Batch AI
* Disederhanakan menentukan sistem file mount dalam file konfigurasi. Sekarang Anda dapat menghilangkan kredensial untuk Azure File Share dan Azure Blob Containers - CLI akan mengisi kredensial yang hilang menggunakan kunci akun penyimpanan yang disediakan melalui parameter baris perintah atau ditentukan melalui variabel lingkungan atau akan menanyakan kunci dari Azure Storage (jika akun penyimpanan milik langganan saat ini)
* Perintah aliran file pekerjaan sekarang selesai secara otomatis ketika pekerjaan selesai (berhasil, gagal, dihentikan atau dihapus)
* `table` Peningkatan output untuk `show` operasi
* Opsi tambahan `--use-auto-storage` untuk pembuatan cluster. Opsi ini memudahkan untuk mengelola akun penyimpanan dan memasang Azure File Share dan Azure Blob Containers ke cluster
* Menambahkan `--generate-ssh-keys` opsi ke `cluster create` dan `file-server create`
* Menambahkan kemampuan untuk menyediakan tugas penyetelan node melalui baris perintah
* [MELANGGAR PERUBAHAN] Dipindahkan `job stream-file` dan `job list-files` perintah di bawah `job file` grup
* [MELANGGAR PERUBAHAN] Berganti nama `--admin-user-name` `--user-name` menjadi dalam `file-server create` perintah agar konsisten dengan `cluster create` perintah

### <a name="billing"></a>Billing

* Menambahkan perintah akun pendaftaran

### <a name="consumption"></a>Consumption

* Menambahkan `marketplace` perintah
* [MELANGGAR PERUBAHAN] Berganti nama menjadi `reservations summaries``reservation summary`
* [MELANGGAR PERUBAHAN] Berganti nama menjadi `reservations details``reservation detail`
* [MELANGGAR PERUBAHAN] Opsi dihapus `--reservation-order-id` dan `--reservation-id` pendek untuk `reservation` perintah
* [MELANGGAR PERUBAHAN] Opsi singkat yang dihapus `--grain` untuk `reservation summary` perintah
* [MELANGGAR PERUBAHAN] Opsi singkat yang dihapus `--include-meter-details` untuk `pricesheet` perintah

### <a name="container"></a>Kontainer

* Menambahkan parameter `--gitrepo-url` `--gitrepo-dir` `--gitrepo-revision` pemasangan volume git repo dan `--gitrepo-mount-path`
* Tetap [#5926](https://github.com/Azure/azure-cli/issues/5926): `az container exec` gagal saat --container-name ditentukan

### <a name="extension"></a>Ekstensi

* Mengubah pesan pemeriksaan distribusi menjadi tingkat debug

### <a name="interactive"></a>Interaktif

* Diubah untuk menghentikan penyelesaian pada perintah yang tidak dikenal
* Kait acara tambahan sebelum dan sesudah subtree perintah dibuat
* Menambahkan penyelesaian untuk `--ids` parameter

### <a name="network"></a>Jaringan

* Tetap [#5936](https://github.com/Azure/azure-cli/issues/5936): `application-gateway create` tag tidak bisa bertaruh set
* Menambahkan argumen `--auth-certs` untuk melampirkan sertifikat otentikasi untuk `application-gateway http-settings [create|update]`. [#4910](https://github.com/Azure/azure-cli/issues/4910)
* Menambahkan `ddos-protection` perintah untuk membuat rencana perlindungan DDoS
* Menambahkan dukungan untuk `--ddos-protection-plan` `vnet [create|update]` mengasosiasikan VNet ke rencana perlindungan DDoS
* Memperbaiki masalah dengan `--disable-bgp-route-propagation` bendera di `network route-table [create|update]`
* Menghapus argumen `--public-ip-address-type` dummy dan `--subnet-type` untuk `network lb [create|update]`
* Menambahkan dukungan untuk catatan TXT dengan urutan escape RFC 1035 ke `network dns zone [import|export]` dan `network dns record-set txt add-record`

### <a name="profile"></a>Profil

* Menambahkan dukungan untuk akun Azure Classic in `account list`
* [MELANGGAR PERUBAHAN] Argumen yang dihapus `--msi` & `--msi-port`

### <a name="rdbms"></a>RDBMS

* Perintah tambahan `georestore`
* Pembatasan ukuran penyimpanan yang dihapus dari `create` perintah

### <a name="resource"></a>Sumber daya

* Dukungan tambahan untuk `--metadata``policy definition create`
* Menambahkan dukungan untuk `--metadata`, , `--set`, `--add``--remove` untuk`policy definition update`

### <a name="sql"></a>SQL

* Ditambahkan `sql elastic-pool op list` dan `sql elastic-pool op cancel`

### <a name="storage"></a>Penyimpanan

* Pesan kesalahan yang disempurnakan untuk string koneksi yang salah informasi

### <a name="vm"></a>VM

* Menambahkan dukungan untuk mengonfigurasi jumlah domain kesalahan platform ke `vmss create`
* Diubah `vmss create` menjadi default ke Lb Standar untuk zonal, besar atau single-placement-group difabelkan skala-set
* [MELANGGAR PERUBAHAN]: Removed `vm assign-identity`, `vm remove-identity and `vm format-secret`
* Menambahkan dukungan untuk Public-IP SKU untuk `vm create`
* Ditambahkan `--keyvault` dan `--resource-group` argumen untuk `vm secret format` mendukung skenario di mana perintah tidak dapat menyelesaikan ID kubah. [#5718](https://github.com/Azure/azure-cli/issues/5718)
* Kesalahan yang `[vm|vmss create]` lebih baik ketika lokasi grup sumber daya tidak memiliki dukungan zona


## <a name="march-27-2018"></a>27 Maret 2018

Versi 2.0.30

### <a name="core"></a>Core

* Tampilkan pesan untuk ekstensi yang ditandai sebagai pratinjau dalam bantuan

### <a name="acs"></a>ACS

* Memperbaiki kesalahan verifikasi sertifikat SSL untuk `aks install-cli` di Cloud Shell

### <a name="appservice"></a>Layanan aplikasi

* Menambahkan dukungan HTTPS saja ke `webapp update`
* Menambahkan dukungan untuk slot ke `az webapp identity [assign|show]` dan `az functionapp identity [assign|show]`

### <a name="backup"></a>Cadangan

* Menambahkan perintah `az backup protection isenabled-for-vm`baru. Perintah ini dapat digunakan untuk memeriksa apakah VM dicadangkan oleh lemari besi mana pun dalam langganan.
* ID objek Azure yang diaktifkan dan `--resource-group` `--vault-name` parameter untuk perintah berikut:
  * `backup container show`
  * `backup item set-policy`
  * `backup item show`
  * `backup job show`
  * `backup job stop`
  * `backup job wait`
  * `backup policy delete`
  * `backup policy get-default-for-vm`
  * `backup policy list-associated-items`
  * `backup policy set`
  * `backup policy show`
  * `backup protection backup-now`
  * `backup protection disable`
  * `backup protection enable-for-vm`
  * `backup recoverypoint show`
  * `backup restore files mount-rp`
  * `backup restore files unmount-rp`
  * `backup restore restore-disks`
  * `backup vault delete`
  * `backup vault show`
* Mengubah `--name` parameter untuk menerima format output dari `backup ... show` perintah

### <a name="container"></a>Kontainer

* Perintah tambahan `container exec` . Menjalankan perintah dalam wadah untuk grup kontainer yang sedang berjalan
* Mengizinkan output tabel untuk membuat dan memperbarui grup kontainer

### <a name="extension"></a>Ekstensi

* Menambahkan pesan untuk `extension add` jika ekstensi sedang dalam pratinjau
* Diubah `extension list-available` untuk menampilkan data ekstensi lengkap dengan `--show-details`
* [MELANGGAR PERUBAHAN] Diubah `extension list-available` untuk memperlihatkan data ekstensi yang disederhanakan secara default

### <a name="interactive"></a>Interaktif

* Mengubah penyelesaian untuk mengaktifkan segera setelah pemuatan tabel perintah selesai
* Memperbaiki bug dengan menggunakan `--style` parameter
* Lexer interaktif instantiated setelah dump tabel perintah jika hilang
* Peningkatan dukungan completer

### <a name="lab"></a>Laboratorium

* Memperbaiki bug dengan `create environment` perintah

### <a name="monitor"></a>Monitor

* Menambahkan dukungan untuk `--top`, `--orderby` dan `--namespace` ke `metrics list` [#5785](https://github.com/Azure/azure-cli/issues/5785)
* Tetap [#4529](https://github.com/Azure/azure-cli/issues/5785): `metrics list` Menerima daftar metrik yang dipisahkan ruang untuk diambil
* Menambahkan dukungan untuk `--namespace` `metrics list-definitions` [#5785](https://github.com/Azure/azure-cli/issues/5785)

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk zona DNS Pribadi

### <a name="profile"></a>Profil

* Menambahkan peringatan untuk `--identity-port` dan `--msi-port``login`

### <a name="rdbms"></a>RDBMS

* Menambahkan model bisnis GA API versi 2017-12-01

### <a name="resource"></a>Sumber daya

* [MELANGGAR PERUBAHAN]: Changed `provider operation [list|show]` to not require `--api-version`

### <a name="role"></a>Peran

* Menambahkan dukungan untuk konfigurasi akses yang diperlukan dan klien asli ke `az ad app create`
* Mengubah `rbac` perintah untuk mengembalikan kurang dari 1000 D pada resolusi objek
* Menambahkan perintah manajemen kredensial `ad sp credential [reset|list|delete]`
* [MELANGGAR PERUBAHAN] Menghapus 'properti' dari `az role assignment [list|show]` output
* Menambahkan dukungan dan `dataActions` `notDataActions` izin ke `role definition`

### <a name="storage"></a>Penyimpanan

* Masalah tetap saat mengunggah file dengan ukuran antara 195GB dan 200GB
* Tetap [#4049](https://github.com/Azure/azure-cli/issues/4049): Masalah dengan lampiran unggahan gumpalan mengabaikan parameter kondisi

### <a name="vm"></a>VM

* Menambahkan peringatan untuk `vmss create` perubahan melanggar yang akan datang untuk set dengan 100+ instance
* Menambahkan dukungan tangguh zona untuk `vm [snapshot|image]`
* Mengubah tampilan instans disk untuk melaporkan status enkripsi yang lebih baik
* [MELANGGAR PERUBAHAN] Diubah `vm extension delete` menjadi tidak lagi mengembalikan output

## <a name="march-13-2018"></a>13 Maret 2018

Versi 2.0.29

### <a name="acr"></a>ACR

* Menambahkan dukungan untuk `--image` parameter ke `repository delete`
* Usang `--manifest` dan `--tag` parameter `repository delete` perintah
* Menambahkan `repository untag` perintah untuk menghapus tag tanpa menghapus data

### <a name="acs"></a>ACS

* Menambahkan `aks upgrade-connector` perintah untuk memutakhirkan konektor yang sudah ada
* Mengubah `kubectl` file konfigurasi untuk menggunakan YAML gaya blok yang lebih mudah dibaca

### <a name="advisor"></a>Advisor

* [MELANGGAR PERUBAHAN] Berganti nama menjadi `advisor configuration get``advisor configuration list`
* [MELANGGAR PERUBAHAN] Berganti nama menjadi `advisor configuration set``advisor configuration update`
* [MELANGGAR PERUBAHAN] Dihapus `advisor recommendation generate`
* Menambahkan `--refresh` parameter ke `advisor recommendation list`
* Perintah tambahan `advisor recommendation show`

### <a name="appservice"></a>Layanan aplikasi

* Usang `[webapp|functionapp] assign-identity`
* Menambahkan perintah `webapp identity [assign|show]` identitas terkelola dan `functionapp identity [assign|show]`

### <a name="eventhubs"></a>Eventhubs

* Rilis awal

### <a name="extension"></a>Ekstensi

* Menambahkan cek untuk memperingatkan pengguna jika distro yang digunakan berbeda maka yang disimpan dalam file sumber paket, karena ini dapat menyebabkan kesalahan

### <a name="interactive"></a>Interaktif

* Tetap [# 5625](https://github.com/Azure/azure-cli/issues/5625): Bertahan sejarah di berbagai sesi
* Tetap [#3016](https://github.com/Azure/azure-cli/issues/3016): Sejarah tidak dicatat saat berada dalam lingkup
* Tetap [#5688](https://github.com/Azure/azure-cli/issues/5688): Penyelesaian tidak muncul jika pemuatan tabel perintah mengalami pengecualian
* Pengukur kemajuan tetap untuk operasi jangka panjang

### <a name="monitor"></a>Monitor

* Usang `monitor autoscale-settings` perintah
* Menambahkan `monitor autoscale` perintah
* Menambahkan `monitor autoscale profile` perintah
* Menambahkan `monitor autoscale rule` perintah

### <a name="network"></a>Jaringan

* [MELANGGAR PERUBAHAN] `--tags` Menghapus parameter dari  `route-filter rule create`
* Menghapus beberapa nilai default yang salah untuk perintah berikut:
  * `network express-route update`
  * `network nsg rule update`
  * `network public-ip update`
  * `traffic-manager profile update`
  * `network vnet-gateway update`
* Menambahkan `network watcher connection-monitor` perintah'
* Ditambahkan `--vnet` dan `--subnet` parameter untuk `network watcher show-topology`

### <a name="profile"></a>Profil

* Parameter usang `--msi` untuk `az login`
* Menambahkan `--identity` parameter untuk `az login` diganti `--msi`

### <a name="rdbms"></a>RDBMS

* [PREVIEW] Diubah untuk menggunakan pratinjau API 2017-12-01

### <a name="service-bus"></a>Service Bus

* Rilis awal

### <a name="storage"></a>Penyimpanan

* Tetap [#4971](https://github.com/Azure/azure-cli/issues/4971): `storage blob copy` sekarang mendukung awan Azure lainnya
* Tetap [# 5286](https://github.com/Azure/azure-cli/issues/5286): Perintah `storage blob [delete-batch|download-batch|upload-batch]` batch tidak lagi melemparkan kesalahan pada kegagalan prasyarat

### <a name="vm"></a>VM

* Menambahkan dukungan untuk `[vm|vmss] create` melampirkan disk data yang tidak terkel manajemen dan mengonfigurasi caching
* Usang `[vm|vmss] assign-identity` dan `[vm|vmss] remove-identity`
* Ditambahkan `vm identity [assign|remove|show]` dan `vmss identity [assign|remove|show]` perintah untuk menggantikan perintah usang
* Mengubah prioritas `vmss create` default menjadi Tidak Ada

## <a name="february-27-2018"></a>Tanggal 27 Februari 2018

Versi 2.0.28

### <a name="core"></a>Core

* Tetap [#5184](https://github.com/Azure/azure-cli/issues/5184): Masalah pemasangan Homebrew
* Menambahkan dukungan untuk telemetri ekstensi dengan tombol kustom
* Menambahkan http logging ke `--debug`

### <a name="acs"></a>ACS

* Diubah untuk menggunakan `virtual-kubelet-for-aks` bagan Helm secara `aks install-connector` default
* Masalah tetap: Izin tidak masuk ke kepala layanan untuk membuat masalah grup kontainer ACI
* Ditambahkan `--aci-container-group`, `--location`, dan `--image-tag` parameter untuk `aks install-connector`
* Menghapus pemberitahuan deprecation dari `aks get-versions`

### <a name="appservice"></a>Layanan aplikasi

* Pembaruan untuk versi SDK baru (azure-mgmt-web 0.35.0)
* Tetap [#5538](https://github.com/Azure/azure-cli/issues/5538): `Free` dilaporkan sebagai SKU tidak valid

### <a name="cognitive-services"></a>Cognitive Services

* Memperbarui 'pemberitahuan' saat membuat akun Layanan Kognitif baru

### <a name="consumption"></a>Consumption

* Menambahkan perintah baru untuk API lembar harga
* Memperbarui detail penggunaan yang ada dan format Detail Reservasi

### <a name="container"></a>Kontainer

* Ditambahkan `--secrets` dan `--secrets-mount-path` argumen untuk `container create` menggunakan rahasia di ACI

### <a name="network"></a>Jaringan

* Tetap [#5559](https://github.com/Azure/azure-cli/issues/5559): Klien yang hilang `network vnet-gateway vpn-client generate`

### <a name="resource"></a>Sumber daya

* Diubah `group deployment export` untuk menampilkan templat parsial dan kesalahan pada kegagalan

### <a name="role"></a>Peran

* Ditambahkan `role assignment list-changelogs` untuk memungkinkan audit peran utama layanan

### <a name="sql"></a>SQL

* Menambahkan dukungan redundansi zona untuk database dan kolam elastis pada pembuatan dan pembaruan

### <a name="storage"></a>Penyimpanan

* Diaktifkan menentukan jalur tujuan/awalan untuk `storage blob [upload-batch|download-batch]`

### <a name="vm"></a>VM

* Menambahkan suport untuk melampirkan/detatching disk pada instance VMSS tunggal


## <a name="february-13-2018"></a>13 Februari 2018

Versi 2.0.27

### <a name="core"></a>Core

* Mengubah autentikasi menjadi kunci pada ID langganan dan nama pada login MSI

### <a name="acs"></a>ACS

* [MELANGGAR PERUBAHAN] Berganti nama `aks get-versions` untuk `aks get-upgrades` kepentingan akurasi
* Diubah `aks get-versions` untuk menampilkan versi Kubernetes yang tersedia untuk `aks create`
* Mengubah `aks create` default untuk membiarkan server memilih versi Kubernetes
* Pesan bantuan yang diperbarui mengacu pada prinsip layanan yang dihasilkan oleh AKS
* Mengubah ukuran node default untuk `aks create` dari "StandardD1v2\_\_" menjadi "StandardDS1v2\_\_"
* Peningkatan keandalan saat menemukan pod dasbor untuk `az aks browse`
* Diperbaiki `aks get-credentials` untuk menangani kesalahan Unicode saat memuat file konfigurasi Kubernetes
* Menambahkan pesan untuk `az aks install-cli` membantu masuk `kubectl``$PATH`

### <a name="appservice"></a>Layanan aplikasi

* Masalah tetap di mana `webapp [backup|restore]` gagal karena referensi nol
* Menambahkan dukungan untuk paket layanan aplikasi default melalui `az configure --defaults appserviceplan=my-asp`

### <a name="cdn"></a>CDN

* Menambahkan `cdn custom-domain [enable-https|disable-https]` perintah

### <a name="container"></a>Kontainer

* Opsi `--follow` tambahan untuk `az container logs` log streaming
* Perintah tambahan `container attach` yang melampirkan output standar lokal dan aliran kesalahan ke wadah dalam grup kontainer

### <a name="cosmosdb"></a>CosmosDB

* Menambahkan dukungan untuk pengaturan kemampuan

### <a name="extension"></a>Ekstensi

* Menambahkan dukungan untuk `--pip-proxy` parameter ke `az extension [add|update]` perintah
* Menambahkan dukungan untuk `--pip-extra-index-urls` argumen ke `az extension [add|update]` perintah

### <a name="feedback-reference"></a>Referensi umpan balik

* Menambahkan informasi ekstensi ke data telemetri

### <a name="interactive"></a>Interaktif

* Masalah tetap di mana pengguna diminta untuk login saat menggunakan mode interaktif di Cloud Shell
* Regresi tetap dengan penyelesaian parameter yang hilang

### <a name="iot"></a>IoT

* Masalah tetap di mana `iot dps access policy [create|update]` akan mengembalikan kesalahan 'tidak ditemukan' pada kesuksesan
* Masalah tetap di mana `iot dps linked-hub [create|update]` akan mengembalikan kesalahan 'tidak ditemukan' pada kesuksesan
* Menambahkan `--no-wait` dukungan untuk `iot dps access policy [create|update]` dan `iot dps linked-hub [create|update]`
* Diubah `iot hub create` untuk memungkinkan menentukan jumlah partisi

### <a name="monitor"></a>Monitor

* Perintah tetap `az monitor log-profiles create`

### <a name="network"></a>Jaringan

* `--tags` Memperbaiki opsi untuk perintah berikut:
  * `network public-ip create`
  * `network lb create`
  * `network local-gateway create`
  * `network nic create`
  * `network vnet-gateway create`
  * `network vpn-connection create`

### <a name="profile"></a>Profil

* Diaktifkan `az login` dari mode interaktif

### <a name="resource"></a>Sumber daya

* Ditambahkan kembali `feature show`

### <a name="role"></a>Peran

* Menambahkan `--available-to-other-tenants` argumen ke `ad app update`

### <a name="sql"></a>SQL

* Menambahkan `sql server dns-alias` perintah
* Ditambahkan `sql db rename`
* Menambahkan dukungan untuk argumen ke `--ids` semua perintah sql

### <a name="storage"></a>Penyimpanan

* Ditambahkan `storage blob service-properties delete-policy` dan `storage blob undelete` perintah untuk mengaktifkan soft-delete

### <a name="vm"></a>VM

* Memperbaiki crash ketika enkripsi VM mungkin tidak sepenuhnya disealisasi
* Menambahkan output ID utama pada memungkinkan MSI
* Tetap `vm boot-diagnostics get-boot-log`


## <a name="january-31-2018"></a>Tanggal 31 Januari 2018

Versi 2.0.26

### <a name="core"></a>Core

* Menambahkan dukungan retrival token mentah dalam konteks MSI
* String indikator polling yang dihapus setelah menyelesaikan LRO pada Windows cmd.exe
* Menambahkan peringatan yang muncul saat menggunakan default yang dikonfigurasi telah diubah ke entri tingkat INFO. Gunakan `--verbose` untuk melihat
* Menambahkan indikator kemajuan untuk perintah tunggu

### <a name="acs"></a>ACS

* Argumen yang diklarifikasi `--disable-browser`
* Peningkatan penyelesaian tab untuk `--vm-size` argumen

### <a name="appservice"></a>Layanan aplikasi

* Tetap `webapp log [tail|download]`
* Menghapus `kind` cek di webapps dan fungsi

### <a name="cdn"></a>CDN

* Memperbaiki masalah klien yang hilang dengan `cdn custom-domain create`

### <a name="cosmosdb"></a>CosmosDB

* Deskripsi parameter tetap untuk kebijakan failover

### <a name="interactive"></a>Interaktif

* Masalah tetap di mana penyelesaian opsi perintah tidak lagi muncul

### <a name="network"></a>Jaringan

* Menambahkan perlindungan untuk `--cert-password``application-gateway create`
* Masalah tetap dengan `application-gateway update` di mana `--sku` keliru menerapkan nilai default
* Menambahkan perlindungan untuk `--shared-key` dan `--authorization-key``vpn-connection create`
* Memperbaiki masalah klien yang hilang dengan `asg create`
* Menambahkan `--file-name / -f` parameter untuk nama yang diekspor ke `dns zone export`
* Memperbaiki masalah berikut dengan `dns zone export`:
  * Masalah tetap di mana catatan TXT yang panjang salah diekspor
  * Masalah tetap di mana catatan TXT yang dikutip salah diekspor tanpa kutipan yang lolos
* Masalah tetap di mana catatan tertentu diimpor dua kali dengan `dns zone import`
* Dipulihkan `vnet-gateway root-cert` dan `vnet-gateway revoked-cert` perintah

### <a name="profile"></a>Profil

* Tetap `get-access-token` bekerja di dalam VM dengan identitas

### <a name="resource"></a>Sumber daya

* Bug tetap dengan `deployment [create|validate]` tempat peringatan salah ditampilkan ketika bidang 'tipe' templat berisi nilai huruf besar

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah dengan migrasi akun V1 Storage ke Storage V2
* Menambahkan pelaporan kemajuan untuk semua perintah unggah/unduh
* Bug tetap mencegah opsi arg "-n" dengan `storage account check-name`
* Menambahkan kolom 'snapshot' ke keluaran tabel untuk `blob [list|show]`
* Bug tetap dengan berbagai parameter yang perlu diurai sebagai int

### <a name="vm"></a>VM

* Perintah tambahan `vm image accept-terms` untuk memungkinkan pembuatan VM dari gambar dengan biaya tambahan
* Tetap `[vm|vmss create]` untuk memastikan perintah dapat berjalan di bawah proxy dengan sertifikat yang tidak ditandatangani
* [PREVIEW] Menambahkan dukungan untuk prioritas "rendah" untuk VMSS
* Menambahkan perlindungan untuk `--admin-password``[vm|vmss] create`


## <a name="january-17-2018"></a>17 Januari 2018

Versi 2.0.25

### <a name="acr"></a>ACR

* Menambahkan fallback login acr pada kesalahan kredensial Windows
* Log registri yang diaktifkan

### <a name="acs"></a>ACS

* Perintah tetap `get-credentials`
* Persyaratan peran SPN dihapus

### <a name="appservice"></a>Layanan aplikasi

* Bug tetap dengan `config ssl upload` tempat `hosting_environment_profile` itu null
* Menambahkan dukungan untuk URL kustom ke `browse`
* Dukungan slot tetap untuk `log tail`

### <a name="backup"></a>Cadangan

* Opsi `--container-name` yang diubah `backup item list` untuk menjadi opsional
* Menambahkan opsi akun penyimpanan ke `backup restore restore-disks`
* Pemeriksaan `backup protection enable-for-vm` lokasi tetap agar kasus tidak sensitif
* Masalah tetap di mana perintah gagal dengan nama kontainer tidak valid
* Diubah `backup item list` untuk menyertakan 'Status Kesehatan' secara default

### <a name="batch"></a>Batch

* Diubah `batch login` untuk mengembalikan detail autentikasi

### <a name="cloud"></a>Cloud

* Diubah menjadi tidak memerlukan titik akhir saat mengatur `--profile` di cloud

### <a name="consumption"></a>Consumption

* Menambahkan perintah baru untuk reservasi: `consumption reservations summaries` dan `consumption reservations details`

### <a name="event-grid"></a>Event Grid

* [MELANGGAR PERUBAHAN] Memindahkan `az eventgrid topic event-subscription` perintah ke `eventgrid event-subscription`
* [MELANGGAR PERUBAHAN] Memindahkan `az eventgrid resource event-subscription` perintah ke `eventgrid event-subscription`
* [MELANGGAR PERUBAHAN] Menghapus `eventgrid event-subscription show-endpoint-url` perintah. Gunakan `eventgrid event-subscription show --include-full-endpoint-url` sebagai gantinya
* Perintah tambahan `eventgrid topic update`
* Perintah tambahan `eventgrid event-subscription update`
* Menambahkan `--ids` parameter untuk `eventgrid topic` perintah
* Menambahkan dukungan penyelesaian tab untuk nama topik

### <a name="interactive"></a>Interaktif

* Masalah tetap di mana mode interaktif tidak berfungsi dengan Python 2.x
* Memperbaiki kesalahan pada startup
* Memperbaiki masalah dengan beberapa perintah yang tidak berjalan dalam mode interaktif

### <a name="iot"></a>IoT

* Menambahkan dukungan untuk layanan penyediaan perangkat
* Menambahkan pesan deprecation dalam perintah dan bantuan perintah
* Menambahkan pemeriksaan IoT untuk memberi tahu pengguna tentang Ekstensi IoT

### <a name="monitor"></a>Monitor

* Menambahkan dukungan pengaturan multi-diagnostik. Parameter ini `--name` sekarang diperlukan untuk `az monitor diagnostic-settings create`
* Menambahkan perintah `monitor diagnostic-settings categories` untuk mendapatkan kategori pengaturan diagnostik

### <a name="network"></a>Jaringan

* Masalah tetap saat mencoba mengubah ke/dari mode siaga aktif dengan `vnet-gateway update`
* Menambahkan dukungan untuk HTTP2 ke `application-gateway [create|update]`

### <a name="profile"></a>Profil

* Menambahkan dukungan untuk login dengan identitas yang ditetapkan pengguna

### <a name="role"></a>Peran

* Menambahkan `--assignee-object-id` argumen ke `role assignment create` untuk memotong kueri grafik

### <a name="service-fabric"></a>Service Fabric

* Menambahkan kesalahan terperinci ke respons validasi saat membuat klaster
* Memperbaiki masalah klien yang hilang dengan beberapa perintah

### <a name="vm"></a>VM

* [PREVIEW] Dukungan lintas zona untuk `vmss`
* [MELANGGAR PERUBAHAN] Mengubah default zona `vmss` tunggal menjadi penyeimbang beban "Standar"
* [MELANGGAR PERUBAHAN] Diubah `externalIdentities` menjadi `userAssignedIdentities` untuk EMSI
* [PREVIEW] Menambahkan dukungan untuk os disk swap
* Menambahkan dukungan untuk menggunakan gambar VM dari langganan lain
* Ditambahkan `--plan-name`, `--plan-product`, `--plan-promotion-code` dan `--plan-publisher` argumen untuk `[vm|vmss] create`
* Masalah kesalahan tetap dengan `[vm|vmss] create`
* Penggunaan sumber daya yang berlebihan yang disebabkan oleh `vm image list --all`

## <a name="december-19-2017"></a>19 Desember 2017

Versi 2.0.23

* Menambahkan dukungan untuk login dengan identitas yang ditetapkan pengguna

### <a name="container"></a>Kontainer

* Memperbaiki urutan parameter yang salah untuk log kontainer

### <a name="network"></a>Jaringan

* Menambahkan `--disable-bgp-route-propagation` argumen ke `route-table [create|update]`
* Menambahkan `--ip-tags` argumen ke `public-ip [create|update]`

### <a name="storage"></a>Penyimpanan

* Menambahkan dukungan untuk penyimpanan V2

### <a name="vm"></a>VM

* [PREVIEW] Menambahkan dukungan untuk identitas yang ditetapkan pengguna untuk VM dan VMSSes


## <a name="december-5-2017"></a>5 Desember 2017

Versi 2.0.22

* Perintah yang dihapus `az component` . Gunakan `az extension` sebagai gantinya

### <a name="core"></a>Core
* `AZURE_US_GOV_CLOUD` Memodifikasi titik akhir otoritas AAD dari login.microsoftonline.com ke login.microsoftonline.us
* Masalah tetap di mana telemetri akan terus mengirim ulang

### <a name="acs"></a>ACS

* Ditambahkan `aks install-connector` dan `aks remove-connector` perintah
* Pelaporan kesalahan yang disempurnakan untuk `acs create`
* `aks get-credentials -f` Penggunaan tetap tanpa jalur yang sepenuhnya memenuhi syarat

### <a name="advisor"></a>Advisor

* Rilis awal

### <a name="appservice"></a>Layanan aplikasi

* Pembuatan nama cert tetap dengan `webapp config ssl upload`
* Memperbaiki `webapp [list|show]` dan `functionapp [list|show]` menampilkan aplikasi yang benar
* Nilai default tambahan untuk `WEBSITE_NODE_DEFAULT_VERSION`

### <a name="consumption"></a>Consumption

* Dukungan iklan untuk API versi 2017-11-30

### <a name="container"></a>Kontainer

* Regresi port default tetap

### <a name="monitor"></a>Monitor

* Menambahkan dukungan multi-dimensi ke perintah metrik

### <a name="resource"></a>Sumber daya

* Menambahkan `--include-response-body` argumen ke `resource show`

### <a name="role"></a>Peran

* Menambahkan tampilan tugas default untuk administraors "klasik" ke `role assignment list`
* Menambahkan suport untuk `ad sp reset-credentials` menambahkan kredensial alih-alih menimpa
* Pelaporan kesalahan yang disempurnakan untuk `ad sp create-for-rbac`

### <a name="sql"></a>SQL

* Ditambahkan `sql db list-usages` dan `sql db show-usage` perintah
* Ditambahkan `sql server conn-policy show` dan `sql server conn-policy update` perintah

### <a name="vm"></a>VM

* Menambahkan informasi zona ke `az vm list-skus`


## <a name="november-14-2017"></a>14 November 2017

Versi 2.0.21

### <a name="acr"></a>ACR

* Menambahkan dukungan untuk membuat webhooks di wilayah replikasi


### <a name="acs"></a>ACS

* Mengubah semua kata "agen" menjadi "node" di AKS
* Opsi usang `--orchestrator-release` untuk `acs create`
* Mengubah ukuran VM default untuk AKS ke `Standard_D1_v2`
* Tetap `az aks browse` pada Windows
* Tetap `az aks get-credentials` pada Windows

### <a name="appservice"></a>Layanan aplikasi

* Menambahkan sumber `config-zip` penyebaran untuk aplikasi web dan aplikasi fungsi
* Menambahkan `--docker-container-logging` opsi ke `az webapp log config`
* Menghapus `storage` opsi dari parameter `--web-server-logging``az webapp log config`
* Pesan kesalahan yang disempurnakan untuk `deployment user set`
* Menambahkan dukungan untuk membuat aplikasi fungsi Linux
* Tetap `list-locations`

### <a name="batch"></a>Batch

* Perintah membuat bug tetap di kolam renang saat ID sumber daya digunakan dengan `--image` bendera

### <a name="batchai"></a>Batchai

* Menambahkan opsi singkat, , `-s`karena `--vm-size` saat memberikan ukuran VM dalam `file-server create` perintah
* Menambahkan nama akun penyimpanan dan argumen kunci ke `cluster create` parameter
* Dokumentasi tetap untuk `job list-files` dan `job stream-file`
* Menambahkan opsi singkat, , `-r`untuk `--cluster-name` saat memberikan nama cluster dalam `job create` perintah

### <a name="cloud"></a>Cloud

* Diubah `cloud [register|update]` untuk mencegah mendaftarkan awan yang telah kehilangan titik akhir yang diperlukan

### <a name="container"></a>Kontainer

* Menambahkan dukungan untuk membuka beberapa port
* Menambahkan kebijakan restart grup kontainer
* Menambahkan dukungan untuk mount Azure File share sebagai volume
* Dokumen pembantu yang diperbarui

### <a name="data-lake-analytics"></a>Data Lake Analytics

* Diubah `[job|account] list` untuk mengembalikan informasi yang lebih ringkas

### <a name="data-lake-store"></a>Data Lake Store

* Diubah `account list` untuk mengembalikan informasi yang lebih ringkas

### <a name="extension"></a>Ekstensi

* Ditambahkan `extension list-available` untuk memungkinkan daftar ekstensi Resmi Microsoft
* Ditambahkan `--name` untuk `extension [add|update]` memungkinkan penginstalan ekstensi berdasarkan nama

### <a name="iot"></a>IoT

* Menambahkan dukungan untuk otoritas sertifikat (CA) dan rantai sertifikat

### <a name="monitor"></a>Monitor

* Menambahkan `activity-log alert` perintah

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk catatan DNS CAA
* Masalah tetap di mana titik akhir tidak dapat diperbarui dengan `traffic-manager profile update`
* Masalah tetap di mana `vnet update --dns-servers` tidak berfungsi tergantung pada bagaimana VNET dibuat
* Masalah tetap di mana nama DNS relatif salah diimpor oleh `dns zone import`

### <a name="reservations"></a>Reservasi

* Rilis pratinjau awal

### <a name="resource"></a>Sumber daya

* Menambahkan dukungan untuk ID sumber daya ke `--resource` kunci parameter dan tingkat sumber daya

### <a name="sql"></a>SQL

* Menambahkan `--ignore-missing-vnet-service-endpoint` parameter ke `sql server vnet-rule [create|update]`

### <a name="storage"></a>Penyimpanan

* Diubah `storage account create` untuk menggunakan SKU `Standard_RAGRS` sebagai default
* Bug tetap saat berhadapan dengan nama file / blob yang mencakup chars non-ascii
* Bug tetap yang mencegah penggunaan `--source-uri` dengan `storage [blob|file] copy start-batch`
* Menambahkan perintah untuk glob dan menghapus beberapa objek dengan `storage [blob|file] delete-batch`
* Memperbaiki masalah saat mengaktifkan metrik dengan `storage metrics update`
* Memperbaiki masalah dengan file lebih dari 200GB saat menggunakan `storage blob upload-batch`
* Masalah tetap di mana `--bypass` dan `--default-action` diabaikan oleh `storage account [create|update]`

### <a name="vm"></a>VM

* Memperbaiki bug dengan `vmss create` yang dicegah menggunakan `Basic` tingkat ukuran
* Menambahkan `--plan` argumen ke `[vm|vmss] create` untuk gambar kustom dengan informasi penagihan
* Menambahkan `vm secret `perintah [add|remove|list]'
* Berganti nama menjadi `vm format-secret``vm secret format`
* Menambahkan `--encrypt format` argumen ke `vm encryption enable`

## <a name="october-24-2017"></a>24 Oktober 2017

Versi 2.0.20

### <a name="core"></a>Core

* Diperbarui `2017-03-09-profile` untuk mengkonsumsi `MGMT_STORAGE` versi API `2016-01-01`

### <a name="acr"></a>ACR

* Manajemen sumber daya yang diperbarui untuk menunjuk ke `2017-10-01` versi API
* Mengubah 'bawa penyimpanan Anda sendiri' SKU ke Classic
* Mengganti nama SKUs registri menjadi Basic, Standard, dan Premium

### <a name="acs"></a>ACS

* [PREVIEW] Menambahkan `az aks` perintah
* Fixed kubernetes `get-credentials`

### <a name="appservice"></a>Layanan aplikasi

* Masalah tetap di mana log yang diunduh `webapp` mungkin tidak valid

### <a name="component"></a>Komponen

* Menambahkan pesan deprecation yang lebih jelas untuk semua installer dan prompt konfirmasi

### <a name="monitor"></a>Monitor

* Menambahkan `action-group` perintah

### <a name="resource"></a>Sumber daya

* Ketidakcocokan tetap dengan versi terbaru dari ketergantungan msrest di `group export`
* Tetap `policy assignment create` bekerja dengan definisi kebijakan dan definisi yang ditetapkan kebijakan

### <a name="vm"></a>VM

* Menambahkan `--accelerated-networking` argumen ke `vmss create`


## <a name="october-9-2017"></a>9 Oktober 2017

Versi 2.0.19

### <a name="core"></a>Core

* Menambahkan penanganan URL otoritas ADFS dengan garis miring trailing ke Azure Stack

### <a name="appservice"></a>Layanan aplikasi

* Menambahkan pembaruan generik dengan perintah baru `webapp update`

### <a name="batch"></a>Batch

* Diperbarui ke Batch SDK 4.0.0
* Opsi terbaru `--image` Dari VirtualMachineConfiguration untuk mendukung referensi gambar ARM selain mempublikasikan:offer:sku:version
* Menambahkan dukungan untuk model ekstensi CLI baru untuk perintah Ekstensi Batch
* Dukungan Batch yang dihapus dari model komponen

### <a name="batchai"></a>Batchai

* Rilis awal modul Batch AI

### <a name="keyvault"></a>Keyvault

* Memperbaiki masalah autentikasi Key Vault saat menggunakan ADFS di Azure Stack. [(#4448)](https://github.com/Azure/azure-cli/issues/4448)

### <a name="network"></a>Jaringan

* Argumen `--server` yang diubah `application-gateway address-pool create` menjadi opsional, memungkinkan untuk kolam alamat kosong
* Diperbarui `traffic-manager` untuk mendukung fitur terbaru

### <a name="resource"></a>Sumber daya

* Menambahkan dukungan untuk `--resource-group/-g` opsi untuk nama grup sumber daya ke `group`
* Menambahkan perintah untuk `account lock` bekerja dengan kunci tingkat langganan
* Menambahkan perintah untuk `group lock` bekerja dengan kunci tingkat grup
* Menambahkan perintah untuk `resource lock` bekerja dengan kunci tingkat sumber daya

### <a name="sql"></a>Sql

* Menambahkan dukungan untuk SQL Transparent Data Encryption (TDE) dan TDE dengan Bring Your Own Key
* Menambahkan `db list-deleted` perintah dan `db restore --deleted-time` parameter, memungkinkan kemampuan untuk menemukan dan memulihkan database yang dihapus
* Ditambahkan `db op list` dan `db op cancel`, memungkinkan kemampuan untuk daftar dan membatalkan operasi yang sedang berlangsung pada database

### <a name="storage"></a>Penyimpanan

* Menambahkan dukungan untuk snapshot berbagi file

### <a name="vm"></a>Vm

* Memperbaiki bug di `vm show` mana menggunakan `-d` menyebabkan kecelakaan pada alamat IP pribadi yang hilang
* [PREVIEW] Menambahkan dukungan untuk rolling upgrade ke `vmss create`
* Menambahkan dukungan untuk memperbarui pengaturan enkripsi dengan `vm encryption enable`
* Menambahkan `--os-disk-size-gb` parameter ke `vm create`
* Menambahkan `--license-type` parameter untuk Windows`vmss create`


## <a name="september-22-2017"></a>22 September 2017

Versi 2.0.18

### <a name="resource"></a>Sumber daya

* Menambahkan dukungan untuk menampilkan definisi kebijakan bawaan
* Menambahkan parameter mode dukungan untuk membuat definisi kebijakan
* Menambahkan dukungan untuk definisi dan templat UI ke `managedapp definition create`
* [MELANGGAR PERUBAHAN] Mengubah `managedapp` tipe sumber daya dari `appliances` ke `applications` dan `applianceDefinitions` ke `applicationDefinitions`

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk zona ketersediaan ke `network lb` dan `network public-ip` subkomite
* Menambahkan dukungan untuk IPv6 Microsoft Peering to `express-route`
* Menambahkan `asg` perintah grup keamanan aplikasi
* Menambahkan `--application-security-groups` argumen ke `nic [create|ip-config create|ip-config update]`
* Ditambahkan `--source-asgs` dan `--destination-asgs` argumen untuk `nsg rule [create|update]`
* Ditambahkan `--ddos-protection` dan `--vm-protection` argumen untuk `vnet [create|update]`
* Menambahkan `network [vnet-gateway|vpn-client|show-url]` perintah

### <a name="storage"></a>Penyimpanan

* Masalah tetap di mana `storage account network-rule` perintah mungkin gagal setelah memperbarui SDK

### <a name="eventgrid"></a>Eventgrid

* Diperbarui Azure Event Grid Python SDK untuk menggunakan versi API yang lebih baru "2017-09-15-preview"

### <a name="sql"></a>SQL

* Mengubah `sql server list` argumen `--resource-group` menjadi opsional. Jika tidak ditentukan, semua server sql dalam langganan akan dikembalikan
* Menambahkan `--no-wait` param ke `db [create|copy|restore|update|replica create|create|update]` dan `dw [create|update]`

### <a name="keyvault"></a>Keyvault

* Menambahkan dukungan untuk perintah Keyvault dari belakang proxy

### <a name="vm"></a>VM

* Ditambahkan untuk dukungan ke zona ketersediaan ke `[vm|vmss|disk] create`
* Masalah tetap di mana menggunakan`--app-gateway ID` dengan `vmss create` akan menyebabkan kegagalan
* Menambahkan `--asgs` argumen ke `vm create`
* Menambahkan dukungan untuk menjalankan perintah pada VM dengan `vm run-command`
* [PREVIEW] Menambahkan dukungan untuk enkripsi disk VMSS dengan `vmss encryption`
* Menambahkan dukungan untuk melakukan pemeliharaan pada VM dengan `vm perform-maintenance`

### <a name="acs"></a>ACS

* [PREVIEW] Menambahkan `--orchestrator-release` argumen ke `acs create` untuk wilayah pratinjau ACS

### <a name="appservice"></a>Layanan aplikasi

* Menambahkan kemampuan untuk memperbarui dan menampilkan pengaturan autentikasi dengan `webapp auth [update|show]`

### <a name="backup"></a>Cadangan

* Rilis pratinjau


## <a name="september-11-2017"></a>11 September 2017

Versi 2.0.17

### <a name="core"></a>Core

* Modul perintah yang diaktifkan untuk mengatur ID korelasinya sendiri dalam telemetri
* Masalah dump JSON tetap ketika telemetri diatur ke mode diagnostik

### <a name="acs"></a>Acs

* Perintah tambahan `acs list-locations`
* Dibuat `ssh-key-file` datang dengan nilai default yang diharapkan

### <a name="appservice"></a>Layanan aplikasi

* Menambahkan kemampuan untuk membuat webapp dalam grup sumber daya selain paket layanan aktif

### <a name="cdn"></a>CDN

* Fixed 'CustomDomain tidak dapat interable' bug untuk `cdn custom-domain create`

### <a name="extension"></a>Ekstensi

* Rilis Awal

### <a name="keyvault"></a>Keyvault

* Masalah tetap di mana izin sensitif terhadap kasus `keyvault set-policy`

### <a name="network"></a>Jaringan

* Berganti nama menjadi `vnet list-private-access-services``vnet list-endpoint-services`
* Berganti nama argumen `--private-access-services` untuk `--service-endpoints``vnet subnet create/update`
* Menambahkan dukungan untuk beberapa rentang IP dan rentang port ke `nsg rule create/update`
* Menambahkan dukungan untuk SKU untuk `lb create`
* Menambahkan dukungan untuk SKU untuk `public-ip create`

### <a name="resource"></a>Sumber daya

* Mengizinkan melewati definisi parameter kebijakan sumber daya pada `policy definition create`tahun 1999, dan `policy definition update`
* Perbolehkan passing dalam nilai parameter untuk `policy assignment create`
* Memungkinkan untuk melewati JSON atau file untuk semua params
* Versi API yang Bertambah

### <a name="sql"></a>SQL

* Menambahkan `sql server vnet-rule` perintah

### <a name="vm"></a>VM

* Tetap: Jangan menetapkan akses kecuali `--scope` disediakan
* Tetap: Gunakan penamaan ekstensi yang sama seperti portal
* Dihapus `subscription` dari `[vm|vmss] create` output
* Tetap: `[vm|vmss] create` penyimpanan SKU tidak diterapkan pada disk data dengan gambar
* Tetap: `vm format-secret --secrets` tidak akan menerima TANDA yang terpisah newline

## <a name="august-31-2017"></a>31 Agustus 2017

Versi 2.0.16

### <a name="keyvault"></a>Keyvault

* Bug tetap saat mencoba menyelesaikan pengkodean rahasia secara otomatis dengan `secret download`

### <a name="sf"></a>Sf

* Mendepresiasi semua perintah yang mendukung Service Fabric CLI (sfctl)

### <a name="storage"></a>Penyimpanan

* Masalah tetap di mana akun penyimpanan tidak dapat dibuat di wilayah yang tidak mendukung fitur NetworkACLs
* Menentukan jenis konten dan pengkodean konten selama blob dan upload file jika tidak ada jenis konten dan pengkodean konten yang ditentukan

## <a name="august-28-2017"></a>28 Agustus 2017

Versi 2.0.15

### <a name="cli"></a>CLI

* Menambahkan catatan hukum untuk `--version`

### <a name="acs"></a>ACS

* Wilayah pratinjau yang dikoreksi
* Default yang diformat `dns_name_prefix` dengan benar
* Output perintah ACs yang dioptimalkan

### <a name="appservice"></a>Layanan aplikasi

* [MELANGGAR PERUBAHAN] Inkonsistensi tetap dalam output `az webapp config appsettings [delete|set]`
* Menambahkan alias `-i` baru untuk `az webapp config container set --docker-custom-image-name`
* Terkena `az webapp log show`
* Argumen baru yang terbuka untuk `az webapp delete` mempertahankan paket layanan aplikasi, metrik, atau pendaftaran DNS
* Tetap: Mendeteksi pengaturan slot dengan benar

### <a name="iot"></a>IoT

* Tetap # 3934: Pembuatan kebijakan tidak lagi membersihkan kebijakan yang ada

### <a name="network"></a>Jaringan

* [MELANGGAR PERUBAHAN] Berganti nama menjadi `vnet list-private-access-services``vnet list-endpoint-services`
* [MELANGGAR PERUBAHAN] Opsi berganti nama `--private-access-services` menjadi `--service-endpoints` untuk `vnet subnet [create|update]`
* Menambahkan dukungan untuk beberapa rentang IP dan port ke `nsg rule [create|update]`
* Menambahkan dukungan untuk SKU untuk `lb create`
* Menambahkan dukungan untuk SKU untuk `public-ip create`

### <a name="profile"></a>Profil

* Terekspos `--msi` dan `--msi-port` masuk menggunakan identitas mesin virtual

### <a name="service-fabric"></a>Service Fabric

* Rilis pratinjau
* Aturan pengguna/kata sandi registri yang disederhanakan untuk perintah
* Permintaan kata sandi tetap untuk pengguna bahkan setelah lewat di param
* Menambahkan dukungan untuk kosong `registry_cred`

### <a name="storage"></a>Penyimpanan

* Mengaktifkan pengaturan tingkat gumpalan
* Ditambahkan `--bypass` dan `--default-action` argumen untuk `storage account [create|update]` mendukung tunneling layanan
* Menambahkan perintah untuk menambahkan aturan VNET dan aturan berbasis IP ke `storage account network-rule`
* Enkripsi layanan yang diaktifkan oleh kunci yang dikelola pelanggan
* [MELANGGAR PERUBAHAN] Opsi berganti nama `--encryption` menjadi `--encryption-services` untuk `az storage account create and az storage account update` perintah
* Tetap #4220: `az storage account update encryption` - ketidakcocokan sintaks

### <a name="vm"></a>VM

* Masalah tetap di mana informasi tambahan dan salah ditampilkan saat `vmss get-instance-view` menggunakan `--instance-id *`
* Menambahkan dukungan untuk `--lb-sku` `vmss create`:
* Menghapus nama manusia dari nama admin yang dianulir untuk `[vm|vmss] create`
* Masalah tetap di mana `[vm|vmss] create` akan membuang kesalahan jika tidak dapat mengekstrak informasi rencana dari gambar
* Memperbaiki crash saat membuat scaleset vmms dengan LB internal
* Masalah tetap di mana `--no-wait` argumen tidak bekerja wth `vm availability-set create`


## <a name="august-15-2017"></a>15 Agustus 2017

Versi 2.0.14

### <a name="acs"></a>ACS

* Mengoreksi nomor port sshMaster0 untuk kubernetes

### <a name="appservice"></a>Layanan aplikasi

* Memperbaiki pengecualian saat merayap webapp Linux berbasis git baru

### <a name="event-grid"></a>Event Grid

* Menambahkan dependensi SDK

## <a name="august-11-2017"></a>11 Agustus 2017

Versi 2.0.13

### <a name="acs"></a>ACS

* Menambahkan lebih banyak wilayah pratinjau

### <a name="batch"></a>Batch

* Diperbarui ke Batch SDK 3.1.0 dan Batch Management SDK 4.1.0
* Menambahkan perintah baru memperlihatkan jumlah tugas pekerjaan
* Bug tetap dalam pemrosesan URL SAS file sumber daya
* Titik akhir akun batch sekarang mendukung awalan 'https://' opsional
* Dukungan untuk menambahkan daftar lebih dari 100 tugas ke pekerjaan
* Menambahkan log debug untuk memuat modul perintah Ekstensi

### <a name="component"></a>Komponen

* Menambahkan peringatan deprecation ke perintah 'az component'

### <a name="container"></a>Kontainer

* `create`Masalah tetap di mana tanda sama dengan tidak diizinkan di dalam variabel lingkungan


### <a name="data-lake-store"></a>Data Lake Store

* Kontrol kemajuan yang diaktifkan

### <a name="event-grid"></a>Event Grid

* Rilis awal

### <a name="network"></a>Jaringan

* `lb`Masalah tetap di mana nama sumber daya anak tertentu tidak menyelesaikan dengan benar ketika dihilangkan
* `application-gateway {subresource} delete`Masalah tetap di mana `--no-wait` tidak dihormati
* `application-gateway http-settings update`: Masalah tetap di mana `--connection-draining-timeout` tidak dapat dimatikan
* Argumen `sa_data_size_kilobyes` kata kunci tak terduga kesalahan tetap dengan `az network vpn-connection ipsec-policy add`

### <a name="profile"></a>Profil

* `account list`: Ditambahkan `--refresh` untuk menyinkronkan langganan terbaru dari server

### <a name="storage"></a>Penyimpanan

* Aktifkan pembaruan akun penyimpanan dengan identitas yang ditetapkan sistem

### <a name="vm"></a>VM

* `availability-set`: Jumlah domain kesalahan yang terbuka pada konversi
* Perintah terbuka `list-skus`
* Dukungan untuk menetapkan identitas w/o membuat tugas peran
* Menerapkan sku penyimpanan pada melampirkan disk data
* Menghapus nama os-disk default dan penyimpanan SKU saat menggunakan disk terkelola


## <a name="july-28-2017"></a>28 Juli 2017

Versi 2.0.12

* Menambahkan perintah kontainer
* Menambahkan modul penagihan dan konsumsi

```text
azure-cli (2.0.12)

acr (2.0.9)
acs (2.0.11)
appservice (0.1.11)
batch (3.0.3)
billing (0.1.3)
cdn (0.0.6)
cloud (2.0.7)
cognitiveservices (0.1.6)
command-modules-nspkg (2.0.1)
component (2.0.6)
configure (2.0.10)
consumption (0.1.3)
container (0.1.7)
core (2.0.12)
cosmosdb (0.1.11)
dla (0.0.10)
dls (0.0.11)
feedback (2.0.6)
find (0.2.6)
interactive (0.3.7)
iot (0.1.10)
keyvault (2.0.8)
lab (0.0.9)
monitor (0.0.8)
network (2.0.11)
nspkg (3.0.1)
profile (2.0.9)
rdbms (0.0.5)
redis (0.2.7)
resource (2.0.11)
role (2.0.9)
sf (1.0.5)
sql (2.0.8)
storage (2.0.11)
vm (2.0.11)
```

### <a name="core"></a>Core

* Output sdk auth info untuk kepala sekolah layanan dengan sertifikat
* Pengecualian kemajuan penyebaran tetap
* Menggunakan titik akhir lengan dari cloud saat ini untuk membuat klien langganan
* Peningkatan penanganan bersamaan dari file clouds.config (#3636)
* Refresh id permintaan klien untuk setiap eksekusi perintah
* Buat klien langganan dengan profil SDK kanan (#3635)
* Pelaporan Kemajuan untuk penyebaran templat (#3510)
* Menambahkan dukungan untuk memilih bidang output tabel melalui kueri jmespath (#3581)
* Meningkatkan muting args parse dan sejarah menambahkan dengan gerakan (# 3434)
* Membuat klien langganan dengan profil SDK yang tepat
* Memindahkan semua file perekaman yang ada ke folder terbaru
* Fixed idempotency for VM/VMSS create (#3586)
* Jalur perintah tidak lagi peka terhadap kasus
* Parameter tipe boolean tertentu tidak lagi sensitif terhadap kasus
* Mendukung login ke ADFS di server prem seperti Azure Stack
* Menulis bersamaan tetap untuk clouds.config (#3255)

### <a name="acr"></a>ACR

* Perintah tambahan `show-usage` untuk pendaftar terkelola
* Mendukung pembaruan SKU untuk pendaftar terkelola
* Menambahkan pendaftar yang dikelola dengan SKU yang dikelola
* Menambahkan webhooks untuk pendaftar terkelola dengan modul perintah webhook acr
* Menambahkan autentikasi AAD dengan perintah login acr
* Menambahkan perintah hapus untuk repositori docker, manifes, dan tag

### <a name="acs"></a>ACS

* Dukungan untuk API versi 2017-07-01

### <a name="appservice"></a>Layanan aplikasi

* Bug tetap di mana daftar WebApp Linux tidak akan mengembalikan apa pun
* Dukungan untuk mengambil creds dari acr
* Menghapus semua perintah di bawah ini `appservice web`
* Kata sandi registri docker topeng dari output perintah (#3656)
* Pastikan browser default digunakan di macOS tanpa kesalahan (#3623)
* Meningkatkan bantuan `webapp log tail` dan `webapp log download` (#3624)
* Perintah terbuka `traffic-routing` untuk mengonfigurasi perutean statis (#3566)
* Perbaikan keandalan tambahan dalam mengonfigurasi kontrol sumber (#3245)
* Menghapus argumen yang tidak didukung `--node-version` dari `webapp config update` untuk Windows webapps. Alih-alih menggunakan `webapp config appsettings set --settings WEBSITE_NODE_DEFAULT_VERSION=...`

### <a name="batch"></a>Batch

* Diperbarui ke Batch SDK 3.0.0 dengan dukungan untuk VM prioritas rendah di kolam renang
* Opsi berganti nama `pool create` `--target-dedicated` menjadi `--target-dedicated-nodes`
* Menambahkan `pool create` opsi `--target-low-priority-nodes` dan `--application-licenses`

### <a name="cdn"></a>CDN

* Memberikan pesan kesalahan yang lebih baik ketika `cdn endpoint list` profil yang ditentukan oleh `--profile-name` tidak ada

### <a name="cloud"></a>Cloud

* Mengubah titik akhir metadata cloud versi API ke format YYYY-MM-DD
* Titik akhir galeri tidak diperlukan
* Dukungan untuk mendaftarkan cloud hanya dengan titik akhir manajer sumber daya ARM
* Menyediakan opsi untuk `cloud set` memilih profil saat memilih cloud saat ini
* Terkena `endpoint_vm_image_alias_doc`

### <a name="cosmosdb"></a>CosmosDB

* Tetap mengizinkan pembuatan koleksi dengan kunci partisi kustom
* Menambahkan dukungan untuk TTL default koleksi

### <a name="data-lake-analytics"></a>Data Lake Analytics

* Menambahkan perintah untuk manajemen kebijakan komputasi di `dla account compute-policy` bawah judul
* Ditambahkan `dla job pipeline show`
* Ditambahkan `dla job recurrence list`

### <a name="data-lake-store"></a>Data Lake Store

* Menambahkan dukungan untuk rotasi kunci kubah kunci yang dikelola pengguna `dls account update`
* Memperbarui versi SDK sistem file Data Lake Store yang sedang diperbarui, mengatasi masalah kinerja
* Perintah tambahan `dls enable-key-vault`. Perintah ini mencoba untuk mengaktifkan pengguna yang disediakan Key Vault untuk digunakan mengenkripsi data ina data Lake Store account

### <a name="interactive"></a>Interaktif

* Meningkatkan waktu start up dengan menggunakan perintah cache
* Peningkatan cakupan tes
* Meningkatkan gerakan '?' untuk juga menyuntikkan ke perintah berikutnya
* Memperbaiki kesalahan interaktif dengan profil 2017-03-09-profile-preview (#3587)
* Diizinkan `--version` sebagai parameter untuk mode interaktif (#3645)
* Hentikan kesalahan melempar mode interaktif dari penyelesaian validasi (#3570)
* Pelaporan kemajuan untuk penyebaran templat (#3510)
* Menambahkan `--progress` bendera
* Dihapus `--debug` dan `--verbose` dari penyelesaian
* Dihapus `interactive` dari penyelesaian (#3324)

### <a name="iot"></a>IoT

* Pembuatan kebijakan tetap tidak lagi menghapus kebijakan yang ada. (#3934)

### <a name="key-vault"></a>Key vault

* Menambahkan perintah untuk fitur pemulihan kubah utama:
  * `keyvault` subkomands `purge`, `recover`, `keyvault list-deleted`
  * `keyvault secret`subkomands `backup`, `restore`, `purge`, , `recover``list-deleted`
  * `keyvault certificate` subkomands `purge`, `recover`, `list-deleted`
  * `keyvault key` subkomands `purge`, `recover`, `list-deleted`
* Integrasi kubah kunci utama layanan tambahan (#3133)
* Dataplane kubah kunci yang diperbarui menjadi 0.3.2. (#3307)

### <a name="lab"></a>Laboratorium

* Menambahkan dukungan untuk mengklaim vm di laboratorium melalui `az lab vm claim`
* Menambahkan formatter output tabel untuk `az lab vm list` dan `az lab vm show`

### <a name="monitor"></a>Monitor

* Perbaiki file templat dengan `monitor autoscale-settings get-parameters-template` perintah (#3349)
* Berganti nama menjadi `monitor alert-rule-incidents list``monitor alert list-incidents`
* Berganti nama menjadi `monitor alert-rule-incidents show``monitor alert show-incident`
* Berganti nama menjadi `monitor metric-defintions list``monitor metrics list-definitions`
* Berganti nama menjadi `monitor alert-rules``monitor alert`
* Diubah `monitor alert create`:
  * `condition` dan `action` subkomite tidak lagi menerima JSON
  * Menambahkan banyak parameter untuk menyederhanakan proses pembuatan aturan
  * `location` Tidak lagi diperlukan
  * Menambahkan dukungan nama dan ID untuk target
  * Hapus `--alert-rule-resource-name`
  * Mengganti nama `is-enabled` menjadi `enabled`, tidak lagi diperlukan
  * `description` default sekarang berdasarkan kondisi yang disediakan
  *  Menambahkan contoh untuk membantu clarifiy format baru
* Nama dukungan atau ID untuk `monitor metric` perintah
* Menambahkan argumen dan contoh kenyamanan ke `monitor alert rule update`

### <a name="network"></a>Jaringan

* Perintah tambahan `list-private-access-services`
* Menambahkan `--private-access-services` argumen ke `vnet subnet create` dan `vnet subnet update`
* Masalah tetap di mana `application-gateway redirect-config create` akan gagal
* Masalah tetap di mana `application-gateway redirect-config update` dengan `--no-wait` tidak akan bekerja
* Memperbaiki bug saat menggunakan `--servers` argumen dengan `application-gateway address-pool create` dan `application-gateway address-pool update`
* Menambahkan `application-gateway redirect-config` perintah
* Menambahkan perintah ke `application-gateway ssl-policy`: `list-options`, , `predefined list``predefined show`
* Menambahkan argumen ke `application-gateway ssl-policy set`: `--name`, , `--cipher-suites``--min-protocol-version`
* Menambahkan argumen ke `application-gateway http-settings create` dan `application-gateway http-settings update`: , `--host-name-from-backend-pool`, `--affinity-cookie-name`, `--enable-probe``--path`
* Menambahkan argumen ke `application-gateway url-path-map create` dan `application-gateway url-path-map update`: `--default-redirect-config`, `--redirect-config`
* Menambahkan argumen `--redirect-config` ke `application-gateway url-path-map rule create`
* Dukungan tambahan untuk `--no-wait``application-gateway url-path-map rule delete`
* Menambahkan argumen ke `application-gateway probe create` dan `application-gateway probe update`: , `--host-name-from-http-settings`, `--min-servers`, `--match-body``--match-status-codes`
* Menambahkan argumen `--redirect-config` ke `application-gateway rule create` dan `application-gateway rule update`
* Menambahkan dukungan untuk `--accelerated-networking` `nic create` dan `nic update`
* Argumen yang dihapus `--internal-dns-name-suffix` dari `nic create`
* Menambahkan dukungan untuk `--dns-servers` ke `nic update` dan `nic create`: Tambahkan dukungan untuk --dns-server
* Bug tetap di mana `local-gateway create` diabaikan `--local-address-prefixes`
* Dukungan tambahan untuk `--dns-servers``vnet update`
* Bug tetap saat membuat peering tanpa penyaringan rute dengan `express-route peering create`
* Bug tetap di mana `--provider` dan `--bandwidth` argumen tidak bekerja dengan `express-route update`
* Bug tetap dengan `network watcher show-topology` logika default
* Pemformatan output yang ditingkatkan untuk `network list-usages`
* Gunakan IP frontend default untuk `application-gateway http-listener create` jika hanya ada satu yang ada
* Gunakan kumpulan alamat default, pengaturan HTTP, dan pendengar HTTP jika `application-gateway rule create` hanya ada satu
* Gunakan IP frontend default dan kolam backend untuk `lb rule create` jika hanya ada satu
* Gunakan IP frontend default untuk `lb inbound-nat-rule create` jika hanya ada satu yang ada

### <a name="profile"></a>Profil

* Mendukung login di dalam VM dengan identitas terkelola
* Output dukungan untuk `account show` format file auth SDK
* Tampilkan peringatan deprekasi saat menggunakan '--expanded-view'
* Perintah tambahan `get-access-token` untuk menyediakan token AAD mentah
* Mendukung login dengan akun pengguna tanpa langganan terkait

### <a name="rdbms"></a>RDBMS

* Server daftar dukungan di seluruh langganan (#3417)
* Tetap `%s` tidak diproses karena hilang `% server_type` (#3393)
* Peta sumber dokumen tetap dan menambahkan tugas CI untuk memverifikasi (#3361)
* Bantuan MySQL dan PostgreSQL Tetap (#3369)

### <a name="resource"></a>Sumber daya

* Peningkatan petunjuk untuk parameter yang hilang untuk `group deployment create`
* Parsing sintaks yang ditingkatkan `--parameters KEY=VALUE`
* Masalah tetap di mana `group deployment create` file parameter tidak lagi dikenali menggunakan `@<file>` sintaks
* Argumen dukungan `--ids` untuk `resource` dan `managedapp` perintah
* Memperbaiki beberapa pesan parsing dan kesalahan (#3584)
* Parsing tetap `--resource-type` agar `lock` perintah menerima `<resource-namespace>` dan `<resource-type>`
* Menambahkan pemeriksaan parameter untuk templat tautan templat (#3629)
* Menambahkan dukungan untuk menentukan parameter penyebaran menggunakan `KEY=VALUE` sintaksis

### <a name="role"></a>Peran

* Output dukungan dalam format file auth SDK untuk `create-for-rbac`
* Membersihkan tugas peran dan aplikasi AAD terkait saat menghapus kepala layanan (#3610)
* Sertakan format waktu dalam `app create` args `--start-date` dan `--end-date` deskripsi
* Tampilkan peringatan deprekasi saat menggunakan `--expanded-view`
* Menambahkan integrasi kubah kunci ke `create-for-rbac` dan `reset-credentials` perintah

### <a name="service-fabric"></a>Service Fabric
* Memperbaiki masalah dengan file besar dalam aplikasi yang terpotong pada upload (#3666)
* Tes tambahan untuk perintah Service Fabric (#3424)
* Memperbaiki banyak perintah Service Fabric (#3234)

### <a name="sql"></a>SQL

* Parameter rusak yang dihapus `sql server create` `--identity`
* Menghapus nilai kata sandi dari `sql server create` dan `sql server update` perintah keluaran
* Menambahkan perintah `sql db list-editions` dan `sql elastic-pool list-editions`

### <a name="storage"></a>Penyimpanan

* Opsi dihapus `--marker` dari `storage blob list`, `storage container list`, dan `storage share list` perintah (#3745)
* Diaktifkan membuat akun penyimpanan https saja
* Metrik penyimpanan yang diperbarui, perintah logging dan cors (#3495)
* Pesan pengecualian yang diulang dari CORS menambahkan (#3638) (#3362)
* Generator dikonversi ke daftar dalam mode dry run perintah batch unduhan (#3592)
* Fixed blob download batch dryrun issue (#3640) (#3592)

### <a name="vm"></a>VM

* Mendukung konfigurasi nsg
* Memperbaiki bug di mana server DNS tidak akan dikonfigurasi dengan benar
* Mendukung identitas layanan terkelola
* Masalah tetap di mana `cmss create` dengan penyeimbang beban yang ada diperlukan `--backend-pool-name`
* Membuat datadisk yang dibuat dengan `vm image create` lun mulai dengan 0


## <a name="may-10-2017"></a>10 Mei 2017

Versi 2.0.6

* documentdb berganti nama menjadi cosmosdb
* Tambahkan rdbms (mysql, postgres)
* Sertakan modul Data Lake Analytics dan Data Lake Store
* Sertakan modul Layanan Kognitif
* Sertakan modul Service Fabric
* Sertakan modul Interaktif (ganti nama az-shell)
* Menambahkan dukungan untuk perintah CDN
* Menghapus modul Kontainer
* Tambahkan 'az -v' sebagai pintasan untuk 'az --version' ([#2926](https://github.com/Azure/azure-cli/issues/2926))
* Meningkatkan kinerja beban paket dan eksekusi perintah ([#2819](https://github.com/Azure/azure-cli/issues/2819))

```text
azure-cli (2.0.6)

acr (2.0.4)
acs (2.0.6)
appservice (0.1.6)
batch (2.0.4)
cdn (0.0.2)
cloud (2.0.2)
cognitiveservices (0.1.2)
command-modules-nspkg (2.0.0)
component (2.0.4)
configure (2.0.6)
core (2.0.6)
cosmosdb (0.1.6)
dla (0.0.6)
dls (0.0.6)
feedback (2.0.2)
find (0.2.2)
interactive (0.3.1)
iot (0.1.5)
keyvault (2.0.4)
lab (0.0.4)
monitor (0.0.4)
network (2.0.6)
nspkg (3.0.0)
profile (2.0.4)
rdbms (0.0.1)
redis (0.2.3)
resource (2.0.6)
role (2.0.4)
sf (1.0.1)
sql (2.0.3)
storage (2.0.6)
vm (2.0.6)
```

### <a name="core"></a>Core

* inti: menangkap pengecualian yang disebabkan oleh penyedia yang tidak terdaftar dan mendaftarkannya secara otomatis
* perf: pertahankan cache token adal dalam memori sampai proses keluar ([#2603](https://github.com/Azure/azure-cli/issues/2603))
* Perbaiki byte yang dikembalikan dari sidik jari heks -o tsv ([#3053](https://github.com/Azure/azure-cli/issues/3053))
* Peningkatan Unduhan Sertifikat Vault Kunci dan integrasi SP AAD ([#3003](https://github.com/Azure/azure-cli/issues/3003))
* Tambahkan lokasi Python ke 'az —version' ([#2986](https://github.com/Azure/azure-cli/issues/2986))
* login: mendukung login ketika tidak ada langganan ([#2929](https://github.com/Azure/azure-cli/issues/2929))
* inti: perbaiki kegagalan saat login menggunakan kepala layanan dua kali ([# 2800](https://github.com/Azure/azure-cli/issues/2800))
* core: Izinkan jalur file accessTokens.json dapat dikonfigurasi melalui env var ([#2605](https://github.com/Azure/azure-cli/issues/2605))
* inti: Perbolehkan default yang dikonfigurasi untuk diterapkan pada arg opsional ([#2703](https://github.com/Azure/azure-cli/issues/2703))
* inti: Peningkatan kinerja
* inti: Custom CA Certs - Pengaturan dukungan REQUESTS_CA_BUNDLE variabel lingkungan
* inti: Konfigurasi cloud - gunakan titik akhir 'pengelola sumber daya' jika titik akhir 'manajemen' tidak diatur

### <a name="acs"></a>ACS

* memperbaiki master dan jumlah agen menjadi integer, bukan string
* mengekspos 'az acs create --no-wait' dan 'az acs wait' untuk pembuatan async
* mengekspos 'az acs create --validate' untuk validasi dry-run
* menghapus profil windows sebelum perintah panggilan PUT untuk skala ([#2755](https://github.com/Azure/azure-cli/issues/2755))

### <a name="appservice"></a>AppService

* functionapp: menambahkan dukungan functionapp penuh, termasuk buat, perlihatkan, daftar, hapus, nama host, ssl, dll
* Menambahkan Layanan Tim (vsts) sebagai opsi pengiriman berkelanjutan ke "konfigurasi kontrol sumber web yang menguntungkan"
* Buat "az webapp" untuk menggantikan "az appservice web" (for backward compat, "az appservice web" akan tetap untuk 2 rilis)
* Mengekspos argumen untuk mengonfigurasi penyebaran dan "tumpukan runtime" di webapp create
* Mengekspos "webapp list-runtimes"
* dukungan mengonfigurasi string koneksi ([#2647](https://github.com/Azure/azure-cli/issues/2647))
* dukungan slot swap dengan preview
* Kesalahan Polandia dari perintah layanan aplikasi ([#2948](https://github.com/Azure/azure-cli/issues/2948))
* Gunakan grup sumber daya paket layanan aplikasi untuk operasi sertifikat ([#2750](https://github.com/Azure/azure-cli/issues/2750))

### <a name="cosmosdb"></a>CosmosDB

* Mengganti nama modul documentdb ke cosmosdb
* Menambahkan dukungan untuk API pesawat data documentdb: database dan manajemen pengumpulan
* Menambahkan dukungan untuk mengaktifkan failover otomatis pada akun database
* Menambahkan dukungan untuk kebijakan konsistensi baru ConsistentPrefix

### <a name="data-lake-analytics"></a>Data Lake Analytics

* Memperbaiki bug di mana pemfilteran pada hasil dan status untuk daftar pekerjaan akan membuang kesalahan
* Menambahkan dukungan untuk tipe item katalog baru: paket. diakses melalui: `az dla catalog package`
* Memungkinkan untuk mencantumkan item katalog berikut dari dalam database (tidak ada spesifikasi skema yang diperlukan):

  * Tabel
  * Fungsi nilai tabel
  * Tampilan
  * Statistik Tabel. Ini juga dapat terdaftar dengan skema, tetapi tanpa menentukan nama tabel.

### <a name="data-lake-store"></a>Data Lake Store

* Memperbarui versi SDK sistem file yang mendasarinya, yang memberikan dukungan yang lebih baik untuk menangani skenario pelambatan sisi server
* Meningkatkan kinerja beban paket dan eksekusi perintah ([#2819](https://github.com/Azure/azure-cli/issues/2819))
* bantuan yang tidak terjawab untuk acara akses. menambahkannya. ([#2743](https://github.com/Azure/azure-cli/issues/2743))

### <a name="find"></a>Cari

* meningkatkan hasil pencarian dan memungkinkan untuk versi indeks pencarian

### <a name="keyvault"></a>Az.KeyVault

* BC:`az keyvault certificate download` ubah -e dari string atau biner ke PEM atau DER untuk lebih mewakili opsi
* BC: Hapus --expires dan --not-before dari `keyvault certificate create` karena parameter ini tidak didukung oleh layanan
* Menambahkan parameter validitas --untuk `keyvault certificate create` secara selektif mengesampingkan nilai dalam --policy
* Memperbaiki masalah di `keyvault certificate get-default-policy` mana 'kedaluwarsa' dan 'not_before' diekspos tetapi 'validity_in_months' tidak
* perbaikan keyvault untuk impor pem dan pfx ([#2754](https://github.com/Azure/azure-cli/issues/2754))

### <a name="lab"></a>Laboratorium

* Menambahkan perintah buat, perlihatkan, hapus & daftar untuk lingkungan di laboratorium
* Menambahkan perintah tampilkan & daftar untuk melihat templat ARM di lab
* Menambahkan bendera `az lab vm list` --environment untuk memfilter VM berdasarkan lingkungan di laboratorium
* Menambahkan perintah `az lab formula export-artifacts` kenyamanan untuk mengekspor perancah artefak dalam rumus Lab
* Menambahkan perintah untuk mengelola rahasia di dalam Lab

### <a name="monitor"></a>Monitor

* Bug Fix: Pemodelan `--actions` `az alert-rules create` untuk mengkonsumsi string JSON ([#3009](https://github.com/Azure/azure-cli/issues/3009))
* Perbaikan bug - pengaturan diagnostik membuat tidak menerima log / metrik dari perintah perlihatkan ([#2913](https://github.com/Azure/azure-cli/issues/2913))

### <a name="network"></a>Jaringan

* Menambahkan `network watcher test-connectivity` perintah
* Menambahkan dukungan untuk `--filters` parameter untuk `network watcher packet-capture create`
* Menambahkan dukungan untuk pengeringan koneksi Application Gateway
* Menambahkan dukungan untuk konfigurasi pengaturan pengaturan WAF Gateway Aplikasi
* Menambahkan dukungan untuk filter dan aturan rute ExpressRoute
* Menambahkan dukungan untuk perutean geografis TrafficManager
* Menambahkan dukungan untuk pemilih lalu lintas berbasis kebijakan koneksi VPN
* Menambahkan dukungan untuk kebijakan IPSec koneksi VPN
* Memperbaiki bug saat `vpn-connection create` menggunakan `--no-wait` atau `--validate` parameter
* Menambahkan dukungan untuk gateway VNet aktif
* Menghapus nilai null dari output `network vpn-connection list/show` perintah
* BC: Perbaiki bug dalam output `vpn-connection create`
* Perbaiki bug di mana argumen '--key-length' dari 'vpn-connection create' tidak diurai dengan benar
* Memperbaiki bug di `dns zone import` mana catatan tidak diimpor dengan benar
* Memperbaiki bug di mana `traffic-manager endpoint update` tidak berfungsi
* Menambahkan perintah pratinjau 'pengamat jaringan'

### <a name="profile"></a>Profil

* Dukungan login ketika tidak ada langganan yang ditemukan ([#2560](https://github.com/Azure/azure-cli/issues/2560))
* Mendukung nama param pendek di az account set --subscription ([#2980](https://github.com/Azure/azure-cli/issues/2980))

### <a name="redis"></a>Redis

* Menambahkan perintah pembaruan yang juga menambahkan kemampuan untuk menskalakan cache redis
* Mendepresiasi perintah 'update-settings'

### <a name="resource"></a>Sumber daya

* Menambahkan perintah definisi managedapp dan managedapp ([#2985](https://github.com/Azure/azure-cli/issues/2985))
* Perintah 'operasi penyedia' dukungan ([#2908](https://github.com/Azure/azure-cli/issues/2908))
* Mendukung pembuat sumber daya generik ([#2606](https://github.com/Azure/azure-cli/issues/2606))
* Perbaiki penguraian sumber daya dan pencarian versi api. ([#2781](https://github.com/Azure/azure-cli/issues/2781))
* Tambahkan dokumen untuk pembaruan kunci az. ([#2702](https://github.com/Azure/azure-cli/issues/2702))
* Kesalahan jika Anda mencoba membuat daftar sumber daya untuk grup yang tidak ada. ([#2769](https://github.com/Azure/azure-cli/issues/2769))
* [Menghitung] Perbaiki masalah dengan VMSS dan VM availability set update. ([#2773](https://github.com/Azure/azure-cli/issues/2773))
* Perbaiki pembuatan kunci dan hapus jika jalur sumber daya induk tidak ada ([#2742](https://github.com/Azure/azure-cli/issues/2742))

### <a name="role"></a>Peran

* create-for-rbac: pastikan tanggal akhir SP tidak akan melebihi tanggal kedaluwarsa sertifikat ([#2989](https://github.com/Azure/azure-cli/issues/2989))
* RBAC: menambahkan dukungan penuh untuk 'grup iklan' ([#2016](https://github.com/Azure/azure-cli/issues/2016))
* peran: memperbaiki masalah pada pembaruan definisi peran ([#2745](https://github.com/Azure/azure-cli/issues/2745))
* create-for-rbac: pastikan kata sandi yang disediakan pengguna dijemput

### <a name="sql"></a>SQL

* Ditambahkan az sql server list-usages and az sql db list-usages commands
* SQL - kemampuan untuk terhubung langsung ke penyedia sumber daya ([#2832](https://github.com/Azure/azure-cli/issues/2832))

### <a name="storage"></a>Penyimpanan

* Lokasi default ke lokasi grup sumber daya untuk `storage account create`
* Menambahkan dukungan untuk salinan gumpalan inkremental
* Menambahkan dukungan untuk upload gumpalan blok besar
* Ubah ukuran blok menjadi 100MB saat file diunggah lebih besar dari 200GB

### <a name="vm"></a>VM

* avail-set: membuat UD&jumlah domain FD opsional

  catatan: Perintah VM di awan berdaulat Harap hindari fitur terkait disk terkelola, termasuk yang berikut:
  1. az disk/snapshot/image
  2. az vm/vmss disk
  3. Di dalam "az vm/vmss create", gunakan "—use-unmanaged-disk" untuk menghindari disk terkelola Perintah lain harus berfungsi
* vm/vmss: meningkatkan teks peringatan saat menghasilkan pasangan kunci ssh
* vm/vmss: dukungan dibuat dari gambar market place yang membutuhkan info rencana ([#1209](https://github.com/Azure/azure-cli/issues/1209))


## <a name="april-3-2017"></a>3 April 2017

Versi 2.0.2

Kami merilis komponen ACR, Batch, KeyVault, dan SQL dalam rilis ini.

```text
azure-cli (2.0.2)

acr (2.0.0)
acs (2.0.2)
appservice (0.1.2)
batch (2.0.0)
cloud (2.0.0)
component (2.0.0)
configure (2.0.2)
container (0.1.2)
core (2.0.2)
documentdb (0.1.2)
feedback (2.0.0)
find (0.0.1b1)
iot (0.1.2)
keyvault (2.0.0)
lab (0.0.1)
monitor (0.0.1)
network (2.0.2)
nspkg (2.0.0)
profile (2.0.2)
redis (0.1.1b3)
resource (2.0.2)
role (2.0.1)
sql (2.0.0)
storage (2.0.2)
vm (2.0.2)
```

### <a name="core"></a>Core

* Menambahkan acr, lab, monitor, dan temukan modul ke daftar default
* Login: lewati penyewa yang salah ([#2634](https://github.com/Azure/azure-cli/pull/2634))
* login: mengatur langganan default ke satu dengan status "Diaktifkan" ([#2575](https://github.com/Azure/azure-cli/pull/2575))
* Tambahkan perintah tunggu dan dukungan --no-wait ke perintah lainnya ([#2524](https://github.com/Azure/azure-cli/pull/2524))
* inti: mendukung login menggunakan kepala layanan dengan sertifikat ([#2457](https://github.com/Azure/azure-cli/pull/2457))
* Tambahkan dorongan untuk parameter templat yang hilang. ([#2364](https://github.com/Azure/azure-cli/pull/2364))
* Mendukung pengaturan nilai default untuk argumen umum seperti grup sumber daya default, web default, vm default
* Mendukung login ke penyewa tertentu

### <a name="acs"></a>ACS

* [ACS] Menambahkan dukungan untuk mengonfigurasi kluster ACS default ([#2554](https://github.com/Azure/azure-cli/pull/2554))
* Tambahkan dukungan untuk mendorong kata sandi kunci ssh. ([#2044](https://github.com/Azure/azure-cli/pull/2044))
* Tambahkan dukungan untuk kluster windows. ([#2211](https://github.com/Azure/azure-cli/pull/2211))
* Beralih dari peran Pemilik ke Kontributor. ([#2321](https://github.com/Azure/azure-cli/pull/2321))

### <a name="appservice"></a>AppService

* appservice: dukungan untuk mendapatkan alamat ip eksternal yang digunakan untuk catatan DNS A ([#2627](https://github.com/Azure/azure-cli/pull/2627))
* appservice: mendukung sertifikat wildcard yang mengikat ([#2625](https://github.com/Azure/azure-cli/pull/2625))
* appservice: profil penerbitan daftar dukungan ([#2504](https://github.com/Azure/azure-cli/pull/2504))
* AppService - Memicu sinkronisasi kontrol sumber setelah konfigurasi ([#2326](https://github.com/Azure/azure-cli/pull/2326))

### <a name="datalake"></a>DataLake

* Rilis awal modul Data Lake Analytics
* Rilis awal modul Data Lake Store

### <a name="docuemntdb"></a>DocuemntDB

* DocumentDB: Menambahkan dukungan untuk mencantumkan string koneksi ([#2580](https://github.com/Azure/azure-cli/pull/2580))

### <a name="vm"></a>VM

* [Menghitung] Menambahkan dukungan AppGateway ke buat set skala mesin virtual ([#2570](https://github.com/Azure/azure-cli/pull/2570))
* [VM/VMSS] Peningkatan dukungan caching disk ([#2522](https://github.com/Azure/azure-cli/pull/2522))
* VM/VMSS: menggabungkan logika validasi kredensial yang digunakan oleh portal ([#2537](https://github.com/Azure/azure-cli/pull/2537))
* Tambahkan perintah tunggu dan dukungan --no-wait ([#2524](https://github.com/Azure/azure-cli/pull/2524))
* Set skala mesin virtual: dukungan * untuk daftar tampilan instans di vms ([#2467](https://github.com/Azure/azure-cli/pull/2467))
* Tambahkan --rahasia untuk VM dan set skala mesin virtual ([#2212}(<https://github.com/Azure/azure-cli/pull/2212>))
* Izinkan pembuatan VM dengan VHD khusus ([#2256](https://github.com/Azure/azure-cli/pull/2256))

## <a name="february-27-2017"></a>Tanggal 27 Februari 2017

Versi 2.0.0

Rilis Azure CLI 2.0 ini adalah rilis "Umum Tersedia" pertama Ketersediaan umum berlaku untuk modul perintah ini:
- Layanan Kontainer (acs)
- Compute (termasuk Resource Manager, VM, set skala mesin virtual, Managed Disks)
- Jaringan
- Penyimpanan

Modul perintah ini dapat digunakan dalam produksi dan didukung oleh Microsoft SLA standar Anda dapat membuka masalah secara langsung dengan dukungan Microsoft atau pada [daftar masalah github](https://github.com/azure/azure-cli/issues/) kami Anda dapat mengajukan pertanyaan [tentang StackOverflow menggunakan tag azure-cli](http://stackoverflow.com/questions/tagged/azure-cli), atau menghubungi tim produk di [azfeedback@microsoft.com](mailto:azfeedback@microsoft.com) Anda dapat memberikan umpan balik dari baris perintah dengan `az feedback` perintah

Perintah dalam modul ini stabil dan sintaksnya diperkirakan tidak akan berubah dalam rilis mendatang dari versi Azure CLI ini.

Untuk memverifikasi versi CLI, gunakan `az --version` daftar output versi CLI itu sendiri (2.0.0 dalam rilis ini), modul perintah individu, dan versi Python dan GCC yang Anda gunakan

```text
azure-cli (2.0.0)

acs (2.0.0)
appservice (0.1.1b5)
batch (0.1.1b4)
cloud (2.0.0)
component (2.0.0)
configure (2.0.0)
container (0.1.1b4)
core (2.0.0)
documentdb (0.1.1b2)
feedback (2.0.0)
iot (0.1.1b3)
keyvault (0.1.1b5)
network (2.0.0)
nspkg (2.0.0)
profile (2.0.0)
redis (0.1.1b3)
resource (2.0.0)
role (2.0.0)
sql (0.1.1b5)
storage (2.0.0)
vm (2.0.0)

Python (Darwin) 2.7.10 (default, Jul 30 2016, 19:40:32)
[GCC 4.2.1 Compatible Apple LLVM 8.0.0 (clang-800.0.34)]
```

> [!Note]
> Beberapa modul perintah memiliki postfix "*bn*" atau "*rcn*" Modul perintah ini masih dalam pratinjau dan akan tersedia secara umum di masa depan.

Kami juga memiliki pratinjau malam yang dibangun dari CLI Untuk informasi, lihat instruksi ini [untuk membangun malam hari](https://github.com/Azure/azure-cli#nightly-builds), dan instruksi ini tentang [pengaturan pengembang dan kode kontribusi.](https://github.com/Azure/azure-cli#developer-setup)

Anda dapat melaporkan masalah dengan pratinjau malam yang dibangun dengan cara berikut:
- Melaporkan masalah dalam [daftar masalah github](https://github.com/azure/azure-cli/issues/) kami
- Hubungi tim produk di [azfeedback@microsoft.com](mailto:azfeedback@microsoft.com)
- Memberikan umpan balik dari baris perintah dengan `az feedback` perintah

---
title: Catatan rilis & pembaruan - Azure CLI | Microsoft Dokumen
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
ms.openlocfilehash: d68e5b43457a8d1d8596c92a1613b79155f06622
ms.sourcegitcommit: ad79327952adf0f8be8f1b9678e72434d9f03f0c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/12/2022
ms.locfileid: "138554870"
---
# <a name="azure-cli-release-notes"></a>Catatan rilis Azure CLI

## <a name="february-01-2022"></a>01 Februari 2022

Versi 2.33.0

### <a name="acr"></a>ACR

* `az acr connected-registry create`: Tambahkan `--notifications` ke dukungan menambahkan pola untuk menghasilkan peristiwa pemberitahuan pada artefak registri yang terhubung
* `az acr connected-registry update`: Menambahkan `--add-notifications` dan `--remove-notifications` mendukung penambahan atau penghapusan pola untuk menghasilkan peristiwa pemberitahuan pada artefak registri yang terhubung

### <a name="aks"></a>AKS

* `az aks nodepool add/update/upgrade`: Tambahkan parameter `--aks-custom-headers` baru untuk mendukung header kustom
* `az aks create`: Tambahkan parameter `--snapshot-id` baru untuk mendukung pembuatan nodepool dari snapshot saat membuat klaster
* `az aks nodepool add/upgrade`: Tambahkan parameter `--snapshot-id` baru untuk mendukung pembuatan nodepool dari snapshot
* `az aks snapshot create/delete/list/show`: Tambahkan perintah baru untuk mendukung pengelolaan operasi terkait snapshot
* `az aks update/az aks nodepool update`: Izinkan string kosong sebagai nilai label

### <a name="app-config"></a>Konfigurasi Aplikasi

* [MELANGGAR PERUBAHAN] Mendukung slot layanan aplikasi

### <a name="app-service"></a>App Service

* `az webapp vnet-integration add`: Memperbaiki bug yang mencegah menambahkan vnet dalam langganan yang berbeda dari webapp
* `az functionapp vnet-integration add`: Memperbaiki bug yang mencegah menambahkan vnet dalam langganan yang berbeda dari functionapp
* `az webapp create`: Dukungan bergabung dengan vnet dalam langganan yang berbeda
* `az functionapp create`: Dukungan bergabung dengan vnet dalam langganan yang berbeda
* `az functionapp create` : Menghapus pratinjau dari runtime PowerShell untuk linux
* `az appservice plan update`: Tambahkan `--elastic-scale` dan `--max-elastic-worker-count` parameter untuk mendukung skala elastis
* `az webapp update`: Tambahkan `--minimum-elastic-instance-count` dan `--prewarmed-instance-count` parameter untuk mendukung pengaturan jumlah instans
* `az webapp up`: Menambahkan teks bantuan dan men-debug teks untuk penyimpanan dan pemuatan konfigurasi
* `az webapp list-runtimes`: Mendukung node 16-lts runtime untuk linux dan windows

### <a name="batch"></a>Batch

* `az batch create/activate`: Tambahkan info bantuan jalur paket aplikasi klarifikasi untuk argumen `--package-file`

### <a name="bot-service"></a>Layanan Bot

* `az bot create`: Tambahkan lokasi seperti yang ditentukan oleh pengguna ke pembuatan bot untuk regionalitas/EUDB

### <a name="compute"></a>Compute

* `az image builder create`: Tambahkan parameter `--proxy-vm-size` baru untuk mendukung penyesuaian ukuran VM proxy
* `az image builder create`: Tambahkan parameter `--build-vm-identities` baru untuk mendukung penyesuaian identitas yang ditetapkan pengguna
* `az vmss update`: Tambahkan parameter `--force-deletion` baru untuk mendukung penghapusan gaya VMSS
* `az vm/vmss create`: Tambahkan log peringatan dan ubah bantuan untuk menginformasikan bahwa nilai `Contributor` `--role` default akan dihapus
* `az disk-encryption-set create`: Buat parameter `--source-vault` tidak diperlukan
* `az vm create/update`: Tambahkan parameter `--v-cpus-available` baru dan `--v-cpus-per-core` untuk mendukung penyesuaian VMSize

### <a name="cosmos-db"></a>Cosmos DB

* `az managed-cassandra cluster status`: Tambahkan dukungan format tabel

### <a name="key-vault"></a>Key Vault

* `az keyvault create`: Tambahkan izin default pada pembuatan keyvault

### <a name="monitor"></a>Monitor

* `az monitor action-group`: Mendukung penerima hub acara

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`: Tambahkan parameter opsional baru bernama encrypt-dc-connections
* `az netappfiles volume export-policy add`Tambahkan parameter opsional yang hilang kerberos5_read_only, kerberos5_read_write, kerberos5i_read_only, kerberos5i_read_write, kerberos5_p_read_only, kerberos5_p_read_write, has_root_access, chown_mode
* `az netappfiles account ad update`: Tambahkan perintah

### <a name="network"></a>Jaringan

* Tambahkan Microsoft.DataFactory/pabrik ke Titik Akhir Privat yang didukung
* Menambahkan Microsoft.Databricks/workspaces ke titik akhir privat yang didukung
* `az network private-endpoint`: Tambahkan parameter dan subkelompok untuk mendukung Konfigurasi IP, ASG dan NicName
* `az network traffic-manager endpoint create/update`: Tambahkan argumen `--min-child-ipv4` baru dan `--min-child-ipv6`.
* Tambahkan Microsoft.HybridCompute/privateLinkScopes ke Titik Akhir Pribadi yang didukung

### <a name="packaging"></a>Pengemasan

* Memperbarui gambar dasar Dockerfile dari Alpine 3.14 hingga 3.15

### <a name="rdbms"></a>RDBMS

* `az postgres flexible-server create`: Mengubah versi postgres default

### <a name="redis"></a>Redis

* `az redis create`: Tambahkan nilai default untuk identitas dan akses jaringan publik sebagai `None`

### <a name="serviceconnector"></a>ServiceConnector

* Mendukung sumber daya target baru: servicebus, eventhub, appconfig

### <a name="storage"></a>Penyimpanan

* Berhenti mendukung `--auth-mode login` dan `az storage blob sync``az storage fs directory upload/download`

## <a name="january-04-2022"></a>04 Januari 2022

Versi 2.32.0

### <a name="aks"></a>AKS

* `az aks create`: Tambahkan parameter `--enable-fips-image` baru untuk mendukung mengaktifkan gambar fips
* `az aks nodepool add`: Tambahkan parameter `--enable-fips-image` baru untuk mendukung mengaktifkan gambar fips

### <a name="app-service"></a>App Service

* [BREAKING CHANGE] `az webapp up`: Hapus dukungan untuk runtime python|3.6 (linux dan windows), ruby|2.5 (linux), dan php|7.3 (windows). Tambahkan dukungan untuk python|3.9 runtime (linux), php|8.0 (linux), dan ruby|2.7 (linux)
* [BREAKING CHANGE] `az webapp create`: Hapus dukungan untuk runtime python|3.6 (linux dan windows), ruby|2.5 (linux), dan php|7.3 (windows). Tambahkan dukungan untuk python|3.9 runtime (linux), php|8.0 (linux), dan ruby|2.7 (linux)
* [BREAKING CHANGE] `az functionapp create`: Hapus dukungan python 3.6
* Memperbaiki #19550: `az staticwebapp users update`: Izinkan memperbarui peran pengguna aplikasi web statis lagi
* `az logicapp create`: Autogenerate Rencana Layanan Aplikasi WS1 ketika tidak ada nilai untuk `--plan` atau `--consumption-plan-location` disediakan
* `az appservice plan create`: Izinkan membuat Paket Layanan Aplikasi untuk Aplikasi Logika (SKU WS1, WS2, dan WS3)
* Perbaiki #20757: `az webapp up`: Perbaiki indeks daftar di luar jangkauan saat tidak ada `--plan` argumen yang disahkan
* Perbaiki #18652: `az webapp up`: Cari \*.csproj di direktori anak
* `az webapp list-runtimes`: Hapus dukungan untuk runtime python|3.6 (linux dan windows), ruby|2.5 (linux), dan php|7.3 (windows). Tambahkan dukungan untuk python|3.9 runtime (linux), php|8.0 (linux), dan ruby|2.7 (linux)

### <a name="backup"></a>Cadangan

* `az backup restore restore-azurewl`: Tambahkan validasi sisi klien
* `az backup container unregister`: Mendukung tipe MAB untuk parameter `--backup-management-type`
* `az backup protectable-item list/show`: Tambahkan kebijakan perlindungan otomatis dan bidang daftar node dalam respons untuk SQLInstance SQLAG
* `az backup protection auto-enable-for-azurewl/auto-disable-for-azurewl`: Tambahkan dukungan untuk SQLAG

### <a name="compute"></a>Compute

* `az vm/vmss create/update`: Perluas validasi jenis lisensi untuk `--license-type` parameter
* `az sig image-definition list-shared`: Tambahkan parameter `--marker` baru dan `--show-next-marker` untuk mendukung paging
* `az sig image-version list-shared`: Tambahkan parameter `--marker` baru dan `--show-next-marker` untuk mendukung paging

### <a name="iot"></a>IoT

* `az iot hub update`: Tambahkan penanganan kesalahan untuk parameter pengunggahan file dan memperbaiki kesalahan titik akhir penyimpanan $default kosong
* `az iot central app create`: Tambahkan parameter `--mi-system-assigned` baru untuk mendukung pembuatan aplikasi dengan identitas terkelola yang ditetapkan sistem
* `az iot central app identity show/assign/remove`: Tambahkan perintah baru untuk mengelola identitas terkelola yang ditetapkan sistem ke aplikasi IoT Central yang ada
* `az iot dps access-policy`: Diganti dengan `az iot dps policy`
* `az iot dps linked-hub create`: Tambahkan argumen kenyamanan untuk menghubungkan hub

### <a name="network"></a>Jaringan

* Memperbaiki #19482: Azure Bastion AAD memperbaiki perubahan inti CLI baru
* `az network lb inbound-nat-pool create`: Tambahkan parameter baru `--backend-pool-name`

### <a name="profile"></a>Profil

* `az account show/set`: Tambahkan `-n`, `--name` argumen

### <a name="redis"></a>Redis

* `az redis identity`: Menambahkan dukungan untuk menetapkan dan memodifikasi Identitas

### <a name="rest"></a>REST

* [BREAKING CHANGE] `az rest`: Hapus `resourceGroup`, `x509ThumbprintHex` ubah

### <a name="role"></a>Peran

* [MELANGGAR PERUBAHAN] `az ad sp create-for-rbac`: Jatuhkan `name` properti dari output. Gunakan `appId` sebagai gantinya
* [MELANGGAR PERUBAHAN] `az ad sp create-for-rbac`: Tidak ada penetapan peran yang akan dibuat secara default

### <a name="storage"></a>Penyimpanan

* `az storage copy`: Tambahkan argumen `extra_options` posisional untuk melewati opsi ke `azcopy`

### <a name="synapse"></a>Synapse

* [BREAKING CHANGE] `az synapse managed private endpoints create`: Hapus `--resource-id` dan `--group-id`, gunakan `--file` sebagai gantinya
* `az synapse sql pool create/restore`: Tambahkan parameter `--storage-type` untuk mendukung penentuan jenis akun penyimpanan
* `az synapse kql-script`: Grup perintah baru untuk mendukung skrip Kusto

## <a name="december-07-2021"></a>07 Desember 2021

Versi 2.31.0

### <a name="aks"></a>AKS

* `az aks update`: Mendukung mengedit label nodepool setelah pembuatan
* `az aks nodepool update`: Mendukung mengedit label nodepool setelah pembuatan
* `az aks create`: Memperbaiki masalah yang `--attach-acr` tidak dapat dikerjakan parameter

### <a name="ams"></a>AMS

* Menghapus variabel usang 'identifier_uri' dari membuat metode sp
* Memperbarui versi API untuk pendaftaran tautan pribadi AMS dan AVA

### <a name="app-service"></a>App Service

* `az functionapp create`: Tambahkan dukungan untuk membuat webapp yang bergabung ke vnet
* `az webapp up`: Memperbaiki kegagalan untuk mendeteksi aplikasi web dotnet 6.0
* `az appservice ase update`: Dukungan untuk mengizinkan koneksi titik akhir pribadi baru di ASEv3
* `az appservice ase list-addresses`: Mendukung ASEv3
* `az staticwebapp identity assign`: Menetapkan identitas layanan terkelola ke aplikasi web statis
* `az staticwebapp identity remove`: Nonaktifkan identitas layanan terkelola aplikasi web statis
* `az staticwebapp identity show`: Tampilkan identitas layanan terkelola aplikasi web statis
* Perbaiki # 17507: `az staticwebapp functions`: Tambahkan dukungan untuk menghubungkan aplikasi fungsi yang ada ke webapp statis (bawa fungsi Anda sendiri)
* `az staticwebapp create`: Memperbarui teks bantuan dengan panduan untuk repo di organisasi Github
* `az functionapp deployment source config-zip`: Perbaiki # 12289: Izinkan build on zip deploy untuk aplikasi fungsi windows
* `az staticwebapp create`: Tambahkan pesan kesalahan yang lebih baik saat mencoba membuat webapp statis yang sudah ada
* `az appservice`: Memperbaiki AttributeError selama penanganan kesalahan pengguna
* `az appservice plan create`: Tambahkan `--zone-redundant` parameter untuk mendukung mengaktifkan redundansi zona untuk ketersediaan tinggi
* `az webapp ssh`: Tambahkan dukungan proxy
* `az webapp create-remote-connection`: Tambahkan dukungan proxy
* `az webapp log download/tail`: Tambahkan dukungan proxy
* `az webapp create`: Memperbaiki penguraian url server registri kontainer untuk `--deployment-container-image-name/-i` argumen
* `az functionapp deployment source config-zip`: Perbaiki keberhasilan kembali ketika penyebaran tidak berhasil
* `az staticwebapp appsettings set`: Membuat set fungsional
* `az staticwebapp appsettings`: Beralih ke metode SDK pengaturan aplikasi SWA yang baru
* `az functionapp plan create`: Tambahkan `--zone-redundant` parameter untuk memberikan opsi untuk membuat paket layanan aplikasi zona berlebihan
* Mendukung identitas terkelola dalam kontainer Layanan Aplikasi

### <a name="arm"></a>ARM

* `az resource\group list`: Mendukung data kueri hanya dengan meneruskan nama tag ke `--tag` parameter
* `az account management-group`: Tambahkan parameter `--no-register` baru untuk melewatkan pendaftaran RP untuk `Microsoft.Management`
* `az deployment`: Prettify output kesalahan untuk penyebaran ARM
* `az bicep install`: Tambahkan parameter `--target-platform/-t` baru untuk menentukan platform lari Bicep CLI
* `az bicep upgrade`: Tambahkan parameter `--target-platform/-t` baru untuk menentukan platform lari Bicep CLI
* `az deployment sub/tenant/mg create`: Memperbaiki `KeyError: 'resourceGroup'` hasil output dalam format tabel saat menerapkan sumber daya tingkat grup non-sumber daya
* `az policy assignment create` dan `az policy assignment identity assign` mendukung penambahan identitas yang ditetapkan pengguna
* `az bicep install`: Bekerja sekarang di belakang proxy perusahaan

### <a name="backup"></a>Cadangan

* GA `az backup` dan beberapa perbaikan bug
* `az backup protectable-item list/show`: Fix AttributeError untuk server_name
* `az backup restore restore-disks`: Tambahkan dukungan untuk Pemulihan Lintas Zonal

### <a name="cognitive-services"></a>Cognitive Services

* `az cognitiveservices account deployment`: Tambahkan perintah `show`baru , `list`, `create`, `delete`
* `az cognitiveservices account commitment-plan`: Tambahkan perintah `show`baru , `list`, `create`, `delete`
* `az cognitiveservices commitment-tier`: Tambahkan perintah baru `list`

### <a name="compute"></a>Compute

* Memperbaiki #20182: `az snapshot create`: Perbaiki bug deteksi otomatis untuk `--copy-start`
* Perbaiki # 20133: `az vm create`: Perbaiki `--data-disk-delete-option` tidak berfungsi ketika tidak `--attach-data-disks` disediakan
* Memperbaiki decoding diagnostik boot
* `az vm create/update`: Tambahkan parameter `--enable-hibernation` baru untuk mendukung kemampuan hibernasi yang memungkinkan
* `az vm/vmss run-command show`: Tambahkan parameter `--instance-view` baru untuk mendukung pelacakan kemajuan RunCommand
* Memperbarui deskripsi bantuan untuk disk yang tidak dikelola
* `az disk create/update`: Menambahkan `--public-network-access` argumen untuk mengontrol kebijakan untuk ekspor pada disk
* `az disk create/update`: Tambahkan `--accelerated-network` argumen untuk mendukung jaringan yang dipercepat
* `az snapshot create/update`: Menambahkan `--public-network-access` argumen untuk mengontrol kebijakan untuk ekspor pada disk
* `az snapshot create/update`: Menambahkan `--accelerated-network` argumen mendukung jaringan yang dipercepat
* `az snapshot create`: Perbaiki #20258: Perbaiki pembuatan snapshot dari disk OS VMSS Seragam

### <a name="eventgrid"></a>EventGrid

* GA `az eventgrid system-topic`

### <a name="key-vault"></a>Key Vault

* `az keyvault key encrypt/decrypt`: Mendukung algoritma AES untuk MHSM
* `az keyvault key rotation-policy update`: Mendukung kasus unta dan kasus ular json untuk `--value`

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles volume create`: Memperbaiki kebijakan ekspor volume

### <a name="network"></a>Jaringan

* `az network express-route peering connection ipv6-config`: Tambahkan perintah `set`baru , `remove`
* `az network application-gateway waf-policy managed-rule exclusion`: Tambahkan subkelompok `rule-set` baru untuk mendukung per pengecualian aturan
* `az network bastion create`: Perbaiki validator yang tidak valid saat `--scale-units` Tidak Ada
* `az network vnet create`: Tambahkan `--enable-encryption` argumen untuk mendukung mengaktifkan enkripsi pada jaringan virtual
* `az network vnet update`: Tambahkan `--enable-encryption` argumen untuk mendukung mengaktifkan enkripsi pada jaringan virtual
* `az network vnet create`: Tambahkan `--encryption-enforcement-policy` argumen untuk memilih Apakah Virtual Machine tanpa enkripsi diizinkan di Jaringan Virtual terenkripsi.
* `az network vnet update`: Tambahkan `--encryption-enforcement-policy` argumen untuk memilih Apakah Virtual Machine tanpa enkripsi diizinkan di Jaringan Virtual terenkripsi.

### <a name="packaging"></a>Pengemasan

* Mendukung Python 3.10
* Tambahkan Dockerfile.mariner untuk mendukung mariner build

### <a name="profile"></a>Profil

* `az logout`, `az account clear`: Hapus file cache token ADAL `accessTokens.json`

### <a name="rdbms"></a>RDBMS

* Memperbaiki bug akhiran zona DNS pribadi
* Memperbaiki # 20124: `az mysql/postgres flexible-server db create`: Membuat grup sumber daya dan nama server diperlukan
* `az postgres flexible-server`: Hapus tag pratinjau

### <a name="storage"></a>Penyimpanan

* `az storage share list-handle/close-handle`: Perintah baru untuk pegangan berbagi
* Tingkat akun GA dan penyimpanan tak berubah tingkat versi blob

### <a name="synapse"></a>Synapse

* [BREAKING CHANGE] `az synapse sql/pool audit-policy`: Hapus `--blob-auditing-policy-name`
* `az synapse notebook/spark-job-definition`: Tambahkan `--folder-path` argumen
* `az synapse spark pool create/update`: Tambahkan `--spark-config-file-path`
* `az synapse spark job submit`: Perbaiki untuk `--main-class-name`
* `az synapse sql-script`: Grup perintah baru untuk mendukung manajemen skrip sql

## <a name="november-02-2021"></a>02 November 2021

Versi 2.30.0

### <a name="core"></a>Core

* [MELANGGAR PERUBAHAN] Migrasi dari ADAL ke MSAL. Untuk detail selengkapnya, lihat [Azure CLI berbasis MSAL](/cli/azure/msal-based-azure-cli)

### <a name="acr"></a>ACR

* [BREAKING CHANGE] `az connected-registry`: `--repository` bendera versi `-t` pendek sedang dihapus.
* [MELANGGAR PERUBAHAN] `az connected-registry install renew credentials`: Sekarang mengharuskan pengguna untuk mengkonfirmasi pembuatan kata sandi.
* `az connected-registry install`: Matikan dan alihkan ke `az acr connected-registry get-settings`.
* `az connected-registry repo`: Matikan dan alihkan ke `az acr connected-registry permissions update`.
* `az connected-registry permissions show`: Perintah baru yang memungkinkan pengguna untuk melihat informasi peta cakupan sinkronisasi.
* `az connected-registry get-settings`Perintah baru yang mengambil informasi yang diperlukan untuk menginstal registri yang terhubung dan memungkinkan pembuatan kata sandi token sinkronisasi baru.
* `az connected-registry create`: Tidak lagi menambahkan postfix ke token sinkronisasi dan nama peta cakupan.

### <a name="aks"></a>AKS

* `az aks create/update`: Tambahkan parameter `--aks-custom-headers` baru untuk mendukung header kustom
* `az aks create`: Pengaturan dukungan `--private-dns-zone` ke tidak ada untuk pembuatan klaster pribadi
* `az aks create/update`: Tambahkan parameter `--enable-secret-rotation` baru dan `--rotation-poll-interval` untuk mendukung rotasi rahasia
* `az aks enable-addons`: Tambahkan parameter `--enable-secret-rotation` baru dan `--rotation-poll-interval` untuk mendukung rotasi rahasia

### <a name="app-config"></a>Konfigurasi Aplikasi

* `az appconfig kv import/export`: Tambahkan parameter `--profile` baru untuk mendukung penggunaan `appconfig/kvset` profil

### <a name="app-service"></a>App Service

* Memperbaiki #19617: `az webapp ssh`: Buka Web SSH pada instans yang ditentukan
* `az staticwebapp hostname`: Mendukung penambahan nama host aplikasi web statis melalui validasi TXT
* Aktifkan dukungan untuk PowerShell pada aplikasi fungsi Linux dengan V4

### <a name="arm"></a>ARM

* `az bicep publish`: Tambahkan perintah baru untuk menerbitkan modul bisep

### <a name="aro"></a>ARO

* `az aro create`: Hapus Pengidentifikasi URI

### <a name="compute"></a>Compute

* `az disk update`: Memperbaiki masalah yang memperbarui kebijakan akses jaringan agar `AllowPrivate` gagal
* `az vm update`: Menambahkan `--host` argumen dan `--host-group` argumen untuk mendukung penetapan VM yang ada ke ADH tertentu
* Perbaiki # 19599: `az vm create`: Perbaiki masalah yang `--nic-delete-option` tidak berfungsi ketika tidak `--nics` disediakan.
* `az snapshot create`: Dukungan copyStart sebagai createOption
* `az vmss create/update`: Mendukung patch in-guest untuk VMSS
* `az vm application set/list`: Menambahkan perintah baru untuk mendukung aplikasi VM
* `az vmss application set/list`: Menambahkan perintah baru untuk mendukung aplikasi VMSS
* `az vm create`: Tambahkan `--ephemeral-os-disk-placement` argumen untuk mendukung pemilihan lokasi penyediaan disk EPhemeral OS
* `az vmss create`: Tambahkan `--ephemeral-os-disk-placement` argumen untuk mendukung pemilihan lokasi penyediaan disk EPhemeral OS
* `az vm update`: Tambahkan `--size` argumen untuk mendukung pengubah ukuran
* `az vmss update`: Tambahkan `--vm-sku` argumen untuk mendukung pengubah ukuran
* `az vm run-command`: Menambahkan perintah baru untuk mendukung pengelolaan perintah yang sedang berjalan di VM
* `az vm update`: Tambahkan `--ephemeral-os-disk-placement` argumen untuk mendukung memilih lokasi penyediaan disk EPhemeral OS
* `az vmss update`: Tambahkan `--ephemeral-os-disk-placement` argumen untuk mendukung memilih lokasi penyediaan disk EPhemeral OS
* `az sig gallery-application`: Tambahkan perintah baru untuk mendukung pengelolaan aplikasi galeri
* `az sig gallery-application version`: Menambahkan perintah baru untuk mendukung pengelolaan versi aplikasi galeri
* GA fitur yang terkait dengan Flex VMSS

### <a name="container"></a>Kontainer

* `az container create`: Tambahkan parameter `--zone` untuk mendukung pemilihan Availability Zone
* `az container create`: Memperbaiki masalah yang `--subnet` atau `--vnet` tidak dapat digunakan dengan jenis `Public` alamat IP untuk memungkinkan `Private`
* `az container create`: Tambahkan Dukungan untuk `--registry-login-server` bekerja dengan `--acr-identity`

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb mongodb retrieve-latest-backup-time`: Tambahkan perintah baru untuk mengambil stempel waktu terbaru yang dapat dipulihkan untuk Akun Mongo.
* `az cosmosdb locations`: Tambahkan perintah baru untuk mencantumkan lokasi akun dan propertinya.
* `az managed-cassandra cluster/data-center`: Dukungan GA untuk klaster cassandra terkelola dan pusat data

### <a name="dms"></a>DMS

* `az dms project create/az dms project task create` : Tambahkan proyek/tugas MySQL untuk migrasi offline.

### <a name="functionapp"></a>FunctionApp

* [MELANGGAR PERUBAHAN] `az functionapp devops-pipeline`: Hapus perintah dan pindahkan ke `functionapp` ekstensi

### <a name="hdinsight"></a>HDInsight

* `az hdinsight create`: Tambahkan dua parameter `--zones` dan `--private-link-configurations` untuk mendukung pembuatan klaster dengan fitur availability zone dan membuat cluster berkemampuan tautan pribadi dengan fitur konfigurasi tautan pribadi.

### <a name="key-vault"></a>Key Vault

* Mendukung Keyvault SKR
* `az keyvault key random`: Minta beberapa byte acak dari managedHSM
* `az keyvault rotation-policy/key rotate`: Mendukung tombol putar dan kelola kebijakan rotasi utama
* `az keyvault create/update`: Tambahkan `--public-network-access` parameter

### <a name="monitor"></a>Monitor

* `az monitor metrics alert condition` : Tambahkan dukungan untuk 'lewati validasi metrik'

### <a name="netappfiles"></a>NetAppFiles

* [BREAKING CHANGE] `az netappfiles account backup-policy create/update`: Hapus parameter `--yearly-backups`opsional .
* `az netappfiles account list`: Tambahkan opsi untuk melewati `--resource-group` parameter dan mengambil akun untuk berlangganan.
* `az netappfiles pool create`: Tambahkan parameter opsional bernama `--encryption-type`
* `az netappfiles volume create`: Tambahkan parameter opsional: `--network-features`, `--avs-data-store`, `--default-group-quota`, `--default-user-quota`, `--is-def-quota-enabled`
* `az netappfiles volume update`: Tambahkan parameter opsional: `--default-group-quota`, `--default-user-quota`, `--is-def-quota-enabled`

### <a name="network"></a>Jaringan

* `az network bastion create`: Tambahkan parameter `--scale-units` baru dan `--sku` untuk mendukung unit skala pengaturan
* `az network vnet`: Tambahkan parameter `--bgp-community`
* `az network private-endpoint-connection`: Mendukung "Microsoft.Cache/Redis"
* `az network private-endpoint-connection`: Dukungan "Microsoft.SignalrService/WebPubsub"

### <a name="rdbms"></a>RDBMS

* Memperkenalkan perintah georestore MySQL dan memperbarui validator
* GA `az mysql flexible-server`

### <a name="service-bus"></a>Service Bus

* Perbaiki kapasitas MU untuk menyertakan 16 saat memperbarui namespace

### <a name="serviceconnector"></a>ServiceConnector

* `az webapp/spring-cloud connection`: Grup perintah baru untuk mendukung layanan ke koneksi layanan

### <a name="sql"></a>SQL

* `az sql server ad-admin`: Memperbaiki perubahan yang dibuat untuk memperbarui dan menghapus

### <a name="synapse"></a>Synapse

* `az synapse kusto`: Tambahkan dukungan kolam kusto (mgmt)

## <a name="october-29-2021"></a>29 Oktober 2021

Versi 2.29.2

### <a name="aro"></a>ARO

* Hotfix: `az aro create`: Hapus Pengidentifikasi URI

## <a name="october-21-2021"></a>21 Oktober 2021

Versi 2.29.1

### <a name="compute"></a>Compute

* Hotfix: Perbaiki perintah webapp statis yang rusak karena peningkatan `azure-mgmt-web` ke 4.0.0

## <a name="october-12-2021"></a>12 Oktober 2021

Versi 2.29.0

### <a name="aks"></a>AKS

* `az aks check-acr`Bump canipull ke 0.0.3 alpha untuk mendukung awan berdaulat
* `az aks create/update`: Tambahkan parameter `--disable-local-accounts` baru untuk mendukung menonaktifkan akun lokal
* `az aks enable-addons`: Mendukung addon open-service-mesh
* `az aks create/update`: Tambahkan dukungan untuk memperbarui tag

### <a name="app-config"></a>Konfigurasi Aplikasi

* Memperbaiki dependensi untuk beberapa instalasi `jsondiff` dan `javaproperties`

### <a name="app-service"></a>App Service

* `az webapp create/up`: Perbaiki kesalahan ketik versi java yang salah dalam bantuan
* `az logicapp create/delete/show/list`: Tambahkan perintah baru untuk mendukung operasi terkait logicapp
* `az staticwebapp environment delete`: Tambahkan perintah untuk mendukung penghapusan lingkungan aplikasi statis
* `az functionapp show`: Tambahkan validasi jenis untuk operasi pertunjukan
* `az webapp config backup list`: Memperbaiki masalah yang mengembalikan konfigurasi cadangan alih-alih daftar cadangan
* `az logicapp start/restart/stop`: Menambahkan perintah baru untuk logicapp
* `az webapp config storage-account`: Perbarui deskripsi parameter

### <a name="arm"></a>ARM

* `az deployment`: Menghapus log badan permintaan pencetakan dari kebijakan kustom
* `az deployment group create`: Memperbaiki cakupan yang salah dalam contoh pembuatan penyebaran dari spesifikasi templat
* `az ts create`: Sederhanakan pesan konfirmasi timpa

### <a name="backup"></a>Cadangan

* `az backup container register`: Memperbaiki bug kontainer refresh
* `az backup`: Tambahkan fungsionalitas CRR untuk Azure Workload
* `az backup`: Tambahkan dukungan untuk tipe manajemen cadangan MAB di beberapa sub perintah

### <a name="compute"></a>Compute

* `az sig create/update`: Tambahkan parameter `--soft-delete` baru untuk mendukung penghapusan lunak
* `az sig image-version`: Tambahkan parameter `--replication-mode` baru untuk mendukung mode replikasi pengaturan
* `az vm/vmss update`: Perbaiki disassociation VM/VMSS dari reservasi kapasitas
* `az vm/vmss create`: Sembunyikan alias `--data-delete-option` dalam bantuan
* `az vmss create`: Mendukung pembuatan cepat untuk VMSS fleksibel

### <a name="container"></a>Kontainer

* [BREAKING CHANGE] `az container create`: Hapus `--network-profile` parameter, properti tidak lagi didukung
* `az container logs`: Memperbaiki kesalahan atribut yang diperkenalkan oleh migrasi Track 2
* `az container create`: Tambahkan parameter `--acr-identity` untuk dukungan tarikan gambar ACR yang diautentikasi MSI

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb identity assign/remove`: Menambahkan dukungan untuk identitas pengguna

### <a name="eventhub"></a>Eventhub

* `az eventhubs namespace update`: Tambahkan `--infra-encryption` untuk enkripsi (enable-require-infrastructure-encryption).
* `az eventhubs namespace create/update`: Tambahkan `--disable-local-auth` untuk mengaktifkan atau menonaktifkan autentikasi SAS.
* `az eventhubs namespace`: Grup tambah `private-endpoint-connection` dan `private-link-resource` perintah

### <a name="key-vault"></a>Key Vault

* [MELANGGAR PERUBAHAN] Perbaiki # 18479: `az keyvault network-rule add`: Perbaiki bug yang memungkinkan duplikat `--ip-address` dengan yang sudah ada dalam aturan jaringan
* Memperbaiki #10254: `az keyvault network-rule add`: Tambahkan kemampuan untuk menerima beberapa alamat ip sebagai daftar dalam bentuk `--ip-address ip1 [ip2] [ip3]...`
* `az keyvault delete`: Tambahkan peringatan saat menghapus HSM yang dikelola

### <a name="network"></a>Jaringan

* Tambah `az network custom-ip prefix wait`
* Tambah `az network vnet-gateway packet-capture wait`
* Tambah `az network vnet-gateway vpn-client ipsec-policy wait`
* Tambah `az network vnet-gateway nat-rule wait`
* Tambah `az network vpn-connection packet-capture wait`
* Dukungan tautan pribadi dan titik akhir untuk operasi penyedia `Microsoft.BotService/botServices` ke titik akhir pribadi yang didukung
* `az network application-gateway client-cert`: Tambahkan perintah `update` dan `show`
* `az network application-gateway ssl-profile`: Tambahkan perintah `update` dan `show`
* `az network application-gateway http-listener create`: Tambahkan parameter `--ssl-profile`
* `az network application-gateway http-listener update`: Tambahkan parameter `--ssl-profile`
* Onboard hdinsight private link2 cmdlet jaringan
* `az network bastion create`: Tambahkan `--tags` argumen
* Dukungan tautan dan titik akhir pribadi untuk penyedia `Microsoft.Authorization/resourceManagementPrivateLinks`
* Dukungan tautan dan titik akhir pribadi untuk penyedia `Microsoft.MachineLearningServices/workspaces`

### <a name="profile"></a>Profil

* `az account show`: Mati sahkan `--sdk-auth`

### <a name="rdbms"></a>RDBMS

* [BREAKING CHANGE] `az postgres flexible-server migration`: Ubah `--properties @{filepath}` ke `--properties {filepath}`
* `az postgres flexible-server migration create`Pengguna dapat meneruskan nama file dengan tanda kutip ganda atau tanpa tanda kutip dan sama untuk jalur absolut.
* `az postgres flexible-server migration check-name-availability`: Tambahkan perintah untuk memeriksa apakah nama migrasi tersedia.
* `az postgres flexible-server migration update`: Tambahkan `--start-data-migration` untuk menjadwal ulang migrasi untuk memulai sekarang.
* Perbarui skus daftar, buat pengaturan lokasi perintah, dan perintah replika

### <a name="role"></a>Peran

* `az ad sp create-for-rbac`: Mati sahkan `--sdk-auth`

### <a name="security"></a>Keamanan

* Perintah Tambahkan `az security setting update`

### <a name="storage"></a>Penyimpanan

* Fix #19279: Tambahkan klarifikasi untuk nama sistem file juga berarti nama kontainer.
* Memperbaiki #19059: Perbaiki tautan doc untuk menunjuk ke situs web dokumen publik
* `az storage account hns-migration start/stop`: Dukungan memigrasikan akun penyimpanan untuk mengaktifkan namespace hierarkis
* `az storage container-rm create/update`: Tambahkan `--root-squash` ke dukungan aktifkan nfsv3 root squash atau semua squash
* Perbaiki #17858: `az storage blob upload`: jadikan --nama opsional
* `az storage account create/update`: Tambahkan parameter --public-network-access
* `az storage container immutability-policy create`: Tambahkan parameter --allow-protected-append-writes-all/-w-all
* `az storage container legal-hold set`: Tambahkan parameter --allow-protected-append-writes-all/-w-all
* `az storage account create/update`: Aktifkan immutability tingkat akun

### <a name="synapse"></a>Synapse

* [BREAKING CHANGE] `az synapse sql/pool audit-policy update`: Tambahkan parameter `blob-storage-target-state`, `log-analytics-target-state`, `event-hub-target-state` (setidaknya pilih salah satu dari 3 paras ini)
* `az synapse integration-runtime`: Mendukung start/stop integration-runtime
* `az synapse trigger`: Tambahkan az synapse trigger tunggu
* `az synapse trigger-run`: Tambahkan az synapse trigger-run cancel
* `az synapse integration-runtime`: Deprecate `create` command dan akan mengalihkan ke `managed create` atau `self-hosted create` perintah
* `az synapse dataset/pipeline/linked-service/trigger`: Deprecate `set` command dan akan mengalihkan ke `update` command
* `az synapse workspace-package`: Mendukung paket ruang kerja CRUD
* `az synapse spark pool update`: Mendukung menambah atau menghapus paket tertentu
* `az synapse workspace create/update`: Menambahkan argumen untuk mendukung konfigurasi repositori ruang kerja sinaps
* `az synapse spark-job-definition`: Dukungan spark job definition CRUD

## <a name="september-09-2021"></a>09 September 2021

Versi 2.28.1

### <a name="arm"></a>ARM

Hotfix: Perbaiki #19468: pip menginstal azure-cli 2.0.73 karena ketergantungan pada paket yang tidak digunakan lagi `jsmin`

## <a name="september-07-2021"></a>07 September 2021

Versi 2.28.0

### <a name="acr"></a>ACR

* `az acr create/update`: Tambahkan dukungan untuk menonaktifkan ekspor melalui `--allow-exports`
* `az acr`: Bump core api-version ke `2021-06-01-preview` dari `2020-11-01-preview`. agent_pool, tugas dan menjalankan operasi tidak berubah dari `2019-06-01-preview`
* `az acr task credential`: Memperbaiki masalah di mana kredensial tugas tidak digunakan
* `az acr task logs`: Memperbaiki AttributeError saat mengkueri log tugas

### <a name="aks"></a>AKS

* [BREAKING CHANGE] `az aks nodepool update`: Perubahan menolak kemampuan untuk menggunakan max-surge dengan node-image-only
* `az aks install-cli`: Tambahkan dukungan untuk rilis kubelogin darwin/arm64
* Memperbaiki parameter yang salah dilewati untuk opsi `--assign-kubelet-identity` di aks membuat sub-perintah
* Upgrade api-version ke `2021-07-01` modul ACS
* `az aks create/update`: Tambahkan dukungan untuk fitur fqdn publik klaster pribadi
* Kembalikan PR #18825: `az aks create/update`: Tambahkan parameter `--auto-upgrade-channel` untuk mendukung peningkatan otomatis (dengan perbaikan)
* `aks create/aks nodepool add`: Tambahkan parameter ` --os-sku` untuk mendukung pemilihan OS host kontainer yang mendasarinya

### <a name="app-config"></a>Konfigurasi Aplikasi

* `appconfig kv import/export`: Tambahkan validasi titik akhir selama impor dan ekspor

### <a name="app-service"></a>App Service

* `az webapp config storage-account list/add/update/delete`: Hapus bendera pratinjau
* Memperbaiki #18497: `functionapp identity show`: Perbaiki crash saat nama functionapp tidak mereferensikan functionapp yang ada
* `az webapp config set`: Menambahkan contoh bantuan tambahan untuk pengguna powershell
* Memperbaiki #17818: `az functionapp update`: Tambahkan validasi instans untuk memperbarui functionapp
* `az webapp config hostname add`: Memperbaiki masalah yang disebabkan oleh AttributeError
* `az webapp config hostname add`: Memperbaiki masalah yang disebabkan oleh AttributeError
* Memperbaiki #16470: `az staticwebapp secrets`: Tambahkan perintah untuk mengelola rahasia penyebaran
* `az webapp deployment source config-local-git`: Perbaiki masalah yang disebabkan oleh AttributeError saat opsi slot ditentukan
* `az webapp deleted restore` : Perbaiki masalah bahwa objek 'WebAppsOperations' tidak memiliki atribut 'restore_from_deleted_app'
* `az webapp up`Menambahkan kemampuan untuk menyebarkan Linux dan Windows webapps ke grup sumber daya yang sama
* `az webapp up`: Menambahkan dukungan untuk diterapkan ke Lingkungan Layanan Aplikasi
* Memperbaiki #19098: `az webapp deployment slot auto-swap `: Perbaiki kesalahan AttributeError untuk parameter `--slot --disable`

### <a name="arm"></a>ARM

* `az feature registration`: Tambahkan api pendaftaran fitur az
* `az tag create`: Tambahkan catatan untuk menangani tag yang ada dalam bantuan
* `az ts create`: Memperbaiki masalah saat membuat spesifikasi template dengan penyebaran internal yang mereferensikan templat umum gagal

### <a name="cdn"></a>CDN

* `az cdn endpoint create`: Memperbaiki kegagalan pembuatan titik akhir dengan `--content-types-to-compress`

### <a name="compute"></a>Compute

* `az ssh vm`: Meningkatkan kesalahan untuk identitas terkelola dan Cloud Shell
* Tingkatkan versi api untuk VM dan VMSS dari `2021-03-01` ke `2021-04-01`
* `az vmss create/update`: Mendukung kebijakan pemulihan spot ke set skala VM
* Menambahkan contoh baru untuk membuat disk dari galeri gambar berbagi
* `az vm image list/list-offers/list-skus/list-publishers/show`: Tambahkan parameter `--edge-zone` baru untuk mendukung kueri gambar di bawah zona tepi
* Memperbaiki masalah yang disebabkan oleh kurangnya `os_type` saat membuat VM dari id galeri bersama
* Memperbarui dokumen galeri gambar bersama
* `az capacity reservation`: Tambahkan perintah baru untuk mengelola reservasi kapasitas
* `az capacity reservation group`: Tambahkan perintah baru untuk mengelola grup reservasi kapasitas
* `az vm create/update`: Tambahkan parameter `--capacity-reservation-group` baru untuk mendukung asosiasi ke reservasi kapasitas
* `az vmss create/update`: Tambahkan parameter `--capacity-reservation-group` baru untuk mendukung asosiasi ke reservasi kapasitas
* `az vmss create`: Mendukung pembuatan VMSS dari gambar galeri bersama

### <a name="iot"></a>IoT

* `az iot hub/dps certificate update/create`: Tambahkan `--verified` argumen untuk menandai sertifikat sebagai terverifikasi tanpa aliran proof-of-possession
* `az iot hub create/update`: Tambahkan `--disable-local-auth`, `--disable-device-sas`, dan `--disable-module-sas` argumen untuk mengonfigurasi metode otentikasi kunci SAS yang diterima.

### <a name="key-vault"></a>Key Vault

* `az keyvault private-endpoint-connection list`: Mendukung daftar koneksi titik akhir pribadi MHSM
* `az keyvault set-policy`: `--key-permissions` tambahkan opsi baru `release`

### <a name="network"></a>Jaringan

* Memperbaiki kesalahan contoh pembuatan aturan NSG
* Tambahkan grup `az network custom-ip prefix`perintah baru .
* `az network public-ip`: Tambahkan parameter `--ip-address`.
* `az network public-ip prefix create`: Tambahkan parameter `--custom-ip-prefix-name`.
* `az network dns record-set {record-type} add-record`: Mendukung idempotent
* PrivateLink mendukung `Microsoft.Purview/accounts` 2021-07-01
* `az network bastion ssh`: terhubung ke mesin Virtual melalui ssh menggunakan Bastion Tunneling.
* `az network bastion rdp`: terhubung ke mesin Virtual melalui RDP asli menggunakan Bastion Tunneling.
* `az network bastion tunnel`: terhubung ke mesin Virtual menggunakan Bastion Tunneling.

### <a name="packaging"></a>Pengemasan

* Menggunakan Python 3.9 dalam rumus Homebrew
* Saat diinstal dengan RPM, jalankan python3.6 jika tersedia
* Tambahkan dukungan Ubuntu 21.04 Hirsute Hippo
* Tambahkan dukungan Debian 11 Bullseye
* Dukungan Drop Ubuntu 20.10 Groovy Gorilla

### <a name="powerbi"></a>PowerBI

* Tambahkan penyedia tautan pribadi Microsoft.PowerBI/privateLinkServicesForPowerBI

### <a name="rdbms"></a>RDBMS

* [BREAKING CHANGE] `az postgres flexible-server migration`: Ganti `--migration-id` nama menjadi `--migration-name`
* [BREAKING CHANGE] `az mysql flexible-server create/update`: `--high-availability` parameter yang tersedia diubah dari 'Diaktifkan' menjadi 'ZoneRedundant' dan 'SameZone'.
* Memperbaiki masalah pembaruan jendela pemeliharaan dengan MySQL dan Ubah parameter restart agar tidak sensitif jika tidak sensitif
* `az mysql flexible-server restore` memungkinkan perubahan opsi jaringan dari jaringan pribadi ke jaringan publik dan sebaliknya.
* `az mysql flexible-server replica create`: Tambahkan `zone` parameter.

### <a name="role"></a>Peran

* `az role assignment create`: Dukungan `ForeignGroup` untuk `--assignee-principal-type`
* `az role assignment create`: Jangan memanggil api Graph jika `--assignee-principal-type` disediakan

### <a name="sql"></a>SQL

* `az sql mi update`: Tambahkan parameter --subnet dan --vnet-name untuk mendukung pembaruan subnet silang SLO
* Memperbaiki perubahan nama enum di track2 Python SDK

### <a name="storage"></a>Penyimpanan

* Memperbaiki #10765: Memperbaiki pesan kesalahan saat kunci akun salah padding

### <a name="synapse"></a>Synapse

* [MELANGGAR PERUBAHAN] Mengganti `az synapse workspace key update` nama menjadi `az synapse workspace key activate` dan menghapus `--is-active`
* Optimalkan mengajukan argumen pekerjaan percikan
* `az synapse`: Tambahkan fitur titik akhir privat terkelola.
* Spark pool menghapus persyaratan pustaka

## <a name="august-23-2021"></a>23 Agustus 2021

Versi 2.27.2

### <a name="cosmos-db"></a>Cosmos DB

* Hotfix: `az cosmosdb restore`: Perbaiki perintah pemulihan untuk akun yang dihapus

## <a name="august-17-2021"></a>17 Agustus 2021

Versi 2.27.1

### <a name="arm"></a>ARM

* Hotfix: Perbaiki #19124: `az deployment what-if`: Tangani tipe perubahan yang tidak didukung dan tidak ada efek

### <a name="batch"></a>Batch

Tingkatkan batch data-plane ke [azure-batch 11.0.0](https://pypi.org/project/azure-batch/) Tingkatkan batch management-plane ke [azure-batch-mgmt 16.0.0](https://pypi.org/project/azure-mgmt-batch/16.0.0/)
`az batch location`: Tambahkan `list-skus` perintah ke daftar SKU yang tersedia di lokasi `az batch account`: Tambahkan `outbound-endpoints` perintah untuk mencantumkan dependensi jaringan keluar

## <a name="august-03-2021"></a>03 Agustus 2021

Versi 2.27.0

### <a name="acr"></a>ACR

* [BREAKING CHANGE] `az acr connected-registry install info`: Tambahkan parameter `--parent-protocol`baru yang diperlukan .
* [BREAKING CHANGE] `az acr connected-registry install renew-credentials`: Tambahkan parameter `--parent-protocol`baru yang diperlukan .
* `az acr import`: Mendukung parameter baru `--no-wait`
* Memperbaiki masalah kompatibilitas Python SDK saat memigrasikan Track 2
* `az acr build`: Buat file .dockerignore termasuk direktori dengan `!`

### <a name="aks"></a>AKS

* `az aks check-acr`: Memperbaiki masalah yang menguraikan versi minor klien tertentu

### <a name="appconfig"></a>Konfigurasi Aplikasi

* [BREAKING CHANGE] `appconfig feature set`: Atur nilai parameter `--description` ke string kosong jika tidak ditentukan
* [BREAKING CHANGE] `az appconfig feature`: Mendukung namespacing untuk bendera fitur dan mengubah bidang output
* `az appconfig create`: Tambahkan dukungan tag saat membuat sumber daya

### <a name="app-service"></a>App Service

* `az webapp config set`: Tambahkan dukungan untuk VNet Route Semua properti.
* `az webapp vnet-integration add`: Default ke VNet Route All. Izinkan integrasi langganan silang.
* `az appservice ase create`: Dukungan untuk redundansi EKSTERNAL dan Zona ASEv3
* `az webapp hybrid-connection add`: Meningkatkan pesan bantuan/kesalahan dan membuka blokir Linux
* `az webapp config access-restriction remove`: Perbaiki masalah #18947 menghapus aturan titik akhir layanan
* : Perbaiki #17424: `az appservice plan show`: Berikan status keluar yang benar

### <a name="arm"></a>ARM

* `az what-if`: Memperbaiki pemformatan output
* `az bicep uninstall`: Tambahkan perintah baru untuk menghapus bisep
* `az bicep build`: Memperbaiki masalah saat berjalan dengan --stdout tidak mencetak output apa pun
* `az provider register`: Tambahkan info terdepresiasi untuk `--accept-term`
* `az lock create/delete`: Tambahkan contoh untuk mengoperasikan berbagai tingkat kunci
* `az deployment group/sub/mg/tenant create`: Tambahkan parameter --what-if untuk memanggil What-If dengan perintah pembuatan penyebaran.
* `az deployment group/sub/mg/tenant create`: Tambahkan parameter --proceed-if-no-change untuk melewati konfirmasi saat --confirm-with-what-if diatur dan tidak ada perubahan dalam hasil What-If.
* Bump api-version dari 2020-10-01 hingga 2021-04-01
* `az ts create`: Buat file bisep dukungan parameter `--template-file`
* `az resource create`: Tambahkan contoh untuk membuat ekstensi situs ke aplikasi web
* `az ts export`: Memperbaiki masalah bahwa mengekspor spesifikasi template tanpa template tertaut gagal

### <a name="backup"></a>Cadangan

* `az backup vault`: Tambahkan dukungan untuk Kunci Terkelola Pelanggan (CMK)
* `az backup restore restore-disks`: Tambahkan penggunaan MSI di IaaS VM Restore

### <a name="cdn"></a>CDN

* `az cdn endpoint rule`: Tambahkan dukungan tindakan OriginGroupOverride

### <a name="compute"></a>Compute

* `az sig image-version create`: Mendukung pencampuran disk, snapshot, dan vhd
* `az vmss update`: Tingkatkan versi paket untuk memperbaiki masalah securityProfile
* `az vm boot-diagnostics get-boot-log`: Perbaiki crash saat mendapatkan log diagnostik boot
* `az vm list-skus`: Memperbaiki masalah yang tidak dapat kueri SKU yang dengan sebagian zona tersedia
* `az vm auto-shutdown`: Perbaiki masalah yang `--webhook` diperlukan saat `--email` dilewatkan
* `az vm create`: Mendukung pembuatan VM dari gambar galeri bersama
* `az vm secret add`: Tambahkan catatan untuk menggunakan ekstensi Azure Key Vault VM sebagai gantinya dalam bantuan

### <a name="container"></a>Kontainer

* `az container exec`: Memperbaiki dan meningkatkan pengalaman terminal

### <a name="databoxedge"></a>DataBoxEdge

* Memigrasikan kotak data ke track2 SDK

### <a name="dms"></a>DMS

* `az dms project create/az dms project task create`: Hapus proyek /tugas MySQL untuk migrasi online karena tidak lagi didukung.

### <a name="iot"></a>IoT

* `az iot hub create/update`: Tambahkan pemeriksaan untuk mencegah parameter identitas upload file yang buruk saat hub tidak memiliki identitas
* `az iot hub create/update`: Tambahkan `--fileupload-notification-lock-duration` parameter
* `az iot hub create/update`: Parameter deprekasi `fileupload-storage-container-uri`
* `az iot dps/hub certificate create`: Sertifikat sekarang akan selalu diunggah dalam pengkodean base64.

### <a name="key-vault"></a>Key Vault

* [MELANGGAR PERUBAHAN] Fix #13752: az keyvault create not idempotent. Membuat keyvault yang ada akan gagal.
* Perbaiki # 6372: output tabel untuk rahasia tidak benar

### <a name="maps"></a>Maps

* `az maps creator create`: Pembuat peta dukungan membuat terkelola
* `az maps creator update`: Mendukung pembaruan pembuat peta yang dikelola
* `az maps creator list`: Mendukung daftar pembuat peta yang dikelola
* `az maps creator show`: Peragaan kreator peta dukungan dikelola
* `az maps creator delete`: Mendukung pembuat peta menghapus dikelola

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles volume pool-change`: Perbarui deskripsi bantuan untuk perubahan kumpulan

### <a name="network"></a>Jaringan

* `az network application-gateway create`: Tambahkan `--ssl-certificate-name` argumen
* Tautan pribadi tambahkan penyedia Microsoft.ServiceBus/namespaces
* `az network application-gateway waf-policy custom-rule match-condition add`: Tambahkan contoh
* `az network express-route port link update`: Tambahkan `--macsec-sci-state` argumen.
* Tautan pribadi tambahkan penyedia Microsoft.Web/hostingEnvironments
* `az network lb frontend-ip update`: Mendukung penyewa silang untuk argumen `--gateway-lb`.
* `az network nic ip-config update`: Mendukung penyewa silang untuk argumen `--gateway-lb`.
* Tautan pribadi tambahkan penyedia Microsoft.StorageSync/storageSyncServices
* Tautan pribadi tambahkan penyedia layanan Microsoft.Media/media
* Tautan pribadi tambahkan penyedia Microsoft.Batch/batchAccounts

### <a name="packaging"></a>Pengemasan

* Menambahkan lisensi ke semua paket Python
* Tambahkan Dukungan Proxy SOCKS

### <a name="policyinsights"></a>KebijakanInsights

* Bermigrasi ke track track 2 SDK

### <a name="rdbms"></a>RDBMS

* PostgreSQL, migrasi MySQL ke GA API

### <a name="redis"></a>Redis

* `az redis create\update`: Tambahkan parameter baru `--redis-version`

### <a name="sql"></a>SQL

* Memperbarui Microsoft.Sql ke track2 SDK
* `az sql server outbound-firewall-rule create`: Perintah Azure CLI untuk Aturan Firewall Keluar

### <a name="storage"></a>Penyimpanan

* Perbaiki #18352: `az storage fs file list --exclude-dir` istirahat dengan `--show-next-marker`
* `az storage fs generate-sas`: Dukungan menghasilkan token sas untuk sistem file di akun ADLS Gen2
* `az storage account blob-service-properties`: Mendukung kebijakan pelacakan akses terakhir
* `storage container-rm migrate-vlw`: Dukungan Tingkat Versi Worm (VLW)
* `az storage copy` menambahkan opsi baru `--cap-mbps`

### <a name="synapse"></a>Synapse

* `synapse workspace key update`: Memperbaiki masalah yang memperbarui kegagalan kunci ruang kerja karena parameter `--is-active-cmk` hilang
* Kegagalan buku catatan reimport

## <a name="july-14-2021"></a>14 Juli 2021

Versi 2.26.1

### <a name="acr"></a>ACR

* Hotfix: `az acr build\connected-registry\pack\run\scope-map`: Perbaiki bug kompatibilitas yang disebabkan oleh peningkatan SDK

### <a name="aks"></a>AKS

* Hotfix: `az aks create`: Perbaiki masalah yang `assign-kubelet-identity` tidak dapat dikerjakan opsi

### <a name="storage"></a>Penyimpanan

* Hotfix: Memperbaiki masalah yang disebabkan oleh peningkatan jwt.
* Hotfix: `az storage fs directory download`: Perbaiki masalah untuk menghasilkan url sas yang `--sas-token` valid
* Hotfix: `az storage blob copy start`: Perbaiki masalah dalam salinan dari akun yang berbeda

## <a name="july-06-2021"></a>06 Juli 2021

Versi 2.26.0

### <a name="aks"></a>AKS

* Memigrasikan modul ACS untuk melacak 2 SDK
* Tingkatkan versi api ke modul 2021-05-01 untuk ACS
* Tambahkan dukungan UltraSSD
* Dukungan gunakan identitas kubelet kustom
* `az aks get-credentials`: Tambahkan cek untuk variabel lingkungan KUBECONFIG

### <a name="apim"></a>APIM

* Menambahkan parameter versi untuk impor apim api
* Memperbaiki bug pemutakhiran apim saat menentukan protokol
* `az apim create`: Perbaiki `--enable-managed-identity` kegagalan sejati

### <a name="app-config"></a>Konfigurasi Aplikasi

* Berhenti menimpa jenis konten referensi KeyVault selama impor

### <a name="app-service"></a>App Service

* [BREAKING CHANGE] `az functionapp create`: Hapus dukungan untuk EOL Node 8 dan 10
* [BREAKING CHANGE] `az webapp deployment source config`: Hapus vsts-cd-manager
* [BREAKING CHANGE] `az functionapp deployment source config`: Hapus vsts-cd-manager
* `az webapp/functionapp config access-restriction add`: Mencegah aturan duplikat menggunakan titik akhir layanan.
* `az webapp/functionapp config access-restriction remove`: Hapus titik akhir layanan tidak sensitif kasus
* `az webapp config access-restrictions add`: Lewati validasi jika pengguna tidak memiliki akses untuk mendapatkan daftar tag layanan.
* Tambahkan dukungan untuk Konsumsi Linux dan tingkatkan cara pembuatan nama berbagi konten.
* : Memperbaiki masalah di mana menambahkan integrasi VNET & koneksi Hybrid pada slot tidak berfungsi
* `az appservice domain create`: Perbaiki dapatkan perjanjian domain yang benar
* `az webapp deployment github-actions add/remove`: perintah baru

### <a name="appconfiguration"></a>AppConfiguration

* Menambahkan dukungan untuk `disable_local_auth`

### <a name="arm"></a>ARM

* `az provider register`: Membuat parameter `--accept-term` menjadi tidak diperlukan

### <a name="aro"></a>ARO

* `az aro create`: Tambahkan nilai cidr untuk pod/service
* Gagal jika sumber daya tidak ada saat dihapus

### <a name="azurestack"></a>Azurestack

* Dukungan Azure Stack Hub untuk AKS dan ACR telah ditambahkan di profil hybrid 2020-09-01

### <a name="backup"></a>Cadangan

* `az backup container`: Perbaiki pendaftaran kontainer Perbaikan pendaftaran kontainer beban kerja, SDK ditingkatkan menjadi 0.12.0, Pengujian Tetap dan Dijalankan Ulang
* Tambahkan Dukungan Arsip untuk Azure CLI

### <a name="billing"></a>Billing

* Memigrasikan penagihan ke track2 SDK

### <a name="cognitive-services"></a>Cognitive Services

* `az cognitiveservices account`: Tambahkan perintah pembersihan daftar yang dihapus, dihapus, dipulihkan, dibersihkan

### <a name="compute"></a>Compute

* `az sig create/update`: Tambahkan --izin untuk menentukan izin galeri berbagi.
* `az sig share`: Kelola profil berbagi galeri.
* `az sig list-shared`: Daftar galeri bersama berdasarkan id langganan atau id penyewa.
* `az sig show-shared`: Dapatkan galeri bersama.
* `az sig image-definition list-shared`: Daftar galeri bersama berdasarkan id langganan atau id penyewa.
* `az sig image-definition show-shared`: Dapatkan gambar galeri bersama.
* `az sig image-version list-shared`: Daftar galeri bersama berdasarkan id langganan atau id penyewa.
* `az sig image-version show-shared`: Dapatkan versi gambar galeri bersama.
* `az vmss create`: Dukungan NetworkApiVersion untuk Vmss dengan OrchestraionMode == Fleksibel
* Membuat sumber daya dependen dari zona tepi dukungan VM/VMSS
* Perbarui dari CoreOS ke Flatcar
* Menambahkan petunjuk untuk menyarankan pengguna menggunakan IP publik standar saat membuat VM

### <a name="container-registry"></a>Container Registry

* Bermigrasi ke track2 SDK

### <a name="cosmos-db"></a>Cosmos DB

* Tambahkan perintah pemulihan point-in-time ke cabang stabil.
* Menambahkan dukungan untuk memilih tipe skema penyimpanan analitik Cosmos DB

### <a name="hdinsight"></a>HDInsight

* `az hdinsight create`: Hapus pemberitahuan perubahan putus yang masuk untuk parameter `--workernode-size` dan `--headnode-size`.
* Tambahkan tiga cmdlet baru untuk mendukung fitur monitor azure baru:

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`: Parameter opsional ditambahkan bernama --administrators
* `az netappfiles pool create`: Parameter opsional ditambahkan --cool-access
* `az netappfiles volume create`: Parameter opsional ditambahkan bernama --chown-mode, --cool-access, --coolness-period, --coolness-period
* `az netappfiles volume backup restore-status`: Perintah ditambahkan untuk melihat status pemulihan cadangan

### <a name="network"></a>Jaringan

* `az network routeserver create`: Tambahkan `--public-ip-address` argumen.

### <a name="rdbms"></a>RDBMS

* Tambahkan parameter autogrow untuk MySQL dan tambahkan nama database ke output json saat dibuat

### <a name="resource"></a>Sumber daya

* Persetujuan/Pencacahan Izin S2S pihak ketiga

### <a name="security"></a>Keamanan

* Menghapus pratinjau dari modul keamanan

### <a name="sql"></a>SQL

* Versi bump sdk
* Memperbaiki untuk membuat server di SQL 0.28
* `az sql db ledger-digest-uploads`: Mendukung SQL Ledger
* Fix for IdentityType for UMI
* `az sql db str-policy set/show`: Tambahkan Set dan Tampilkan ShortTermRetentionPolicy

### <a name="storage"></a>Penyimpanan

* Dukungan GA mengamankan SMB
* `az storage account create`: Dukungan `--enable-nfs-v3` untuk mengatur protokol NFS 3.0
* Mendukung penghapusan lunak kontainer

## <a name="june-15-2021"></a>15 Juni 2021

Versi 2.25.0

### <a name="acr"></a>ACR

* `az acr connected-registry`: Perbaikan bug kecil

### <a name="app-service"></a>App Service

* `az webapp deployment source config-local-git`: Perbaiki untuk mengatur SiteConfig

### <a name="arm"></a>ARM

* `az resource tag`: Memperbaiki masalah penandaan sumber daya dengan jenis sumber daya `Microsoft.Network/publicIPAddresses`
* `az policy assignment non-compliance-message`: Grup perintah baru untuk pesan ketidakpatuhan penetapan kebijakan
* `az policy assignment update`: Perintah baru untuk memperbarui sebagian tugas kebijakan yang ada

### <a name="backup"></a>Cadangan

* Memigrasikan pencadangan ke track2 SDK

### <a name="compute"></a>Compute

* Tingkatkan versi api untuk VM dan VMSS dari '2020-12-01' ke '2021-03-01'
* `az vm create`: Opsi hapus dukungan untuk NIC dan Disk untuk VM di Azure CLI
* Mendukung user_data untuk Set Skala VM dan VM

### <a name="container"></a>Kontainer

* `az container exec`: Decode menerima byte sebagai string utf-8

### <a name="eventgrid"></a>EventGrid

* Memigrasikan SDK track2

### <a name="hdinsight"></a>HDInsight

* Bermigrasi ke track2 Python SDK 7.0.0

### <a name="iot-hub"></a>Iot Hub

* Memperbaiki masalah ARM identitas yang ditetapkan pengguna saat dihapus

### <a name="key-vault"></a>Key Vault

* Memperbaiki #11871: AKV10032: Kesalahan penerbit yang tidak valid untuk operasi di penyewa/langganan yang tidak pernah putus-putus
* `az keyvault set-policy/delete-policy`: Dukungan --application-id
* `az keyvault recover`: Mendukung MHSM
* `az keyvault private-link-resource list`: Mendukung MHSM
* `az keyvault private-endpoint-connection`: Mendukung MHSM

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles volume backup status`: Perintah ditambahkan untuk mendapatkan status cadangan untuk volume.
* `az netappfiles volume update`: Parameter opsional ditambahkan bernama `--snapshot-policy-id` o menetapkan kebijakan snapshot ke volume.
* `az netappfiles volume backup create`: Parameter opsional ditambahkan bernama `--use-existing-snapshot` untuk secara manual mencadangkan snapshot yang sudah ada.
* `az netappfiles volume backup update`: Parameter opsional ditambahkan bernama `--use-existing-snapshot` untuk secara manual mencadangkan snapshot yang sudah ada. Label parameter opsional juga ditambahkan untuk menambahkan label ke cadangan.

### <a name="network"></a>Jaringan

* Penyedia `Microsoft.Sql/servers` dukungan di Tautan Pribadi
* `az network private-link-resource list`: Dukungan `--type microsoft.keyvault/managedHSMs`
* `az network private-endpoint-connection`: Dukungan `--type microsoft.keyvault/managedHSMs`

### <a name="rdbms"></a>RDBMS

* Menambahkan perintah untuk tindakan Github
* `az postgres flexible-server migration`: Tambahkan fitur yang dihadapi pelanggan untuk memigrasikan server postgres db dari platform Sterling ke Meru
* Parameter zona DNS pribadi ditambahkan untuk perintah pemulihan, validator ketersediaan tinggi
* Mengubah lokasi default server (masalah dilaporkan)

### <a name="role"></a>Peran

* [BREAKING CHANGE] `az ad sp create-for-rbac`: `--name` sekarang hanya digunakan sebagai `displayName` aplikasi. Ini tidak digunakan untuk menghasilkan `identifierUris` lagi. `name` dalam output sekarang sama dengan `appID` (`servicePrincipalNames`) dan usang.

### <a name="signalr"></a>SignalR

* `az signalr identity`: Tambahkan perintah terkait identitas terkelola
* `az signalr cors update`: Tambahkan perintah pembaruan untuk cor

### <a name="storage"></a>Penyimpanan

* `az storage blob copy start`: Mendukung --tier dan --rehydrate-priority
* GA rilis file penyimpanan berbagi NFS dan SMB multichannel
* [BREAKING CHANGE] `az storage account create`: Hapus `StorageFileDataSmbShareOwner` opsi untuk --default-share-permission
* `az storage blob list`: nilai parameter --delimiter sekarang akan dihormati

### <a name="synapse"></a>Synapse

* Pembaruan untuk AZ Synapse mgmt 2.0.0
* Konversi konfigurasi Spark, yang menyebabkan kegagalan

### <a name="webapp"></a>Webapp

* Tambahkan ke `az webapp deploy` teks bantuan param

## <a name="june-02-2021"></a>02 Juni 2021

Versi 2.24.2

### <a name="container"></a>Kontainer

* Hotfix: Perbaiki #18276: `az container create` gagal dengan `AttributeError: 'ResourcesOperations' object has no attribute 'create_or_update'`

## <a name="june-01-2021"></a>01 Juni 2021

Versi 2.24.1

### <a name="app-service"></a>App Service

* Hotfix: Perbaiki #18266 - pengaturan aplikasi konfigurasi webapp mengatur perintah yang menyebabkan semua nilai default menjadi "false"

### <a name="arm"></a>ARM
* Hotfix: Memperbaiki masalah deserialisasi di formatter What-If template ARM

### <a name="compute"></a>Compute
* Hotfix: Memperbaiki masalah permintaan buruk saat membuat VMSS di Azure Stack

### <a name="iot"></a>IoT
* Hotfix: Memperbaiki masalah untuk menghapus identitas terakhir yang ditetapkan pengguna dari IoT Hub

## <a name="may-25-2021"></a>25 Mei 2021

Versi 2.24.0

### <a name="aks"></a>AKS

* `az aks check-acr`: Tambahkan nodelector linux untuk menghindari pod "canipull" yang akan dijadwalkan pada node windows
* Pembaruan Sdk
* az aks create and update azure-rbac
* Menambahkan cli run-command

### <a name="app-config"></a>Konfigurasi Aplikasi

* Mengizinkan pengimpor nilai kunci dengan karakter unicode dari file

### <a name="app-service"></a>App Service

* [BREAKING CHANGE] `az webapp list-runtimes`: Tambahkan dukungan Dotnet6 dan perbarui runtime
* `webapp log tail`: Perbaiki #17987: logging.warning call dengan argumen 'akhir' yang tidak valid
* Perbaiki #16838- az cli update app setting command selalu membuat slotsetting menjadi true
* `az appservice`: Tambahkan fungsi untuk mengambil token akses pribadi github pengguna
* az staticwebapp appsettings set issue #17792
* Fix #18033: az staticwebapp appsettings set param posisional yang hilang app_settings
* Memperbaiki masalah dengan tanda tangan API yang berubah dengan pembaruan Track2
* Memperbaiki mendapatkan klien manajemen sumber daya dengan benar
* Tambahkan cara interaktif untuk mendapatkan token untuk staticwebapp
* Memperbaiki masalah di mana menetapkan dan menghapus identitas akan gagal dengan panggilan ke NoneType

### <a name="arm"></a>ARM

* Memigrasikan sumber daya ke track2 SDK
* `az ts`: Tambahkan dukungan file UiFormDefinition ke TemplateSpecs for GA (05/04)

### <a name="aro"></a>ARO

* Menambahkan rotasi kredensial klaster

### <a name="compute"></a>Compute

* `az sshkey create`: Simpan kunci pribadi ke sistem file lokal

### <a name="cosmos-db"></a>Cosmos DB

* Membuat dan mengelola Definisi Peran dan Tugas Peran untuk menegakkan RBAC bidang data di akun SQL Cosmos DB

### <a name="devtestlabs"></a>DevTestLabs

* `az labs create environment`: Memperbaiki kesalahan membuat lingkungan dari templat ARM

### <a name="hdinsight"></a>HDInsight

* [BREAKING CHANGE] `az hdinsight create`: Gunakan api sku default untuk mengatur ukuran workernode dan headnode jika pelanggan tidak menyediakan.

### <a name="iot"></a>IoT

* `az iot hub create`: Mendukung penetapan identitas dan menetapkan peran untuk identitas yang dikelola sistem.
* `az iot hub update`: Parameter baru `--file-upload-storage-identity` untuk memungkinkan upload file yang diautentikasi identitas terkelola.
* `az iot hub identity assign`: Perintah baru untuk menetapkan identitas terkelola yang ditetapkan pengguna/sistem ke Hub IoT.
* `az iot hub identity show`: Perintah baru untuk menampilkan properti identitas Hub IoT.
* `az iot hub identity show`: Perintah baru untuk memperbarui tipe identitas Hub IoT.
* `az iot hub identity remove`: Perintah baru untuk menghapus identitas terkelola yang ditetapkan pengguna/sistem dari Hub IoT.
* `az iot hub routing-endpoint create`: Parameter `--identity` baru memungkinkan memilih identitas yang ditetapkan pengguna/sistem untuk titik akhir perutean.
* `az iot hub route create`: Tipe sumber perutean baru `DeviceConnectionStateEvents`

### <a name="kusto"></a>Kusto

* Perbarui ringkasan panjang grup perintah

### <a name="network"></a>Jaringan

* Versi Bump api dari '2020-11-01' hingga '2021-02-01'
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
* Mencegah modul rdbms pemecah migrasi track2 zona DNS pribadi2

### <a name="service-fabric"></a>Service Fabric

* [MELANGGAR PERUBAHAN] `az sf cluster certificate`: Hapus semua perintah di bawah grup ini. Ikuti petunjuk di [Tambahkan sertifikat sekunder menggunakan Azure Resource Manager](/azure/service-fabric/service-fabric-cluster-security-update-certs-azure#add-a-secondary-certificate-using-azure-resource-manager) untuk menambahkan/menghapus sertifikat klaster.
* [BREAKING CHANGE] `az sf managed-service update`: Hapus parameter yang tidak digunakan lagi --drop-source-replica-on-move.
* [BREAKING CHANGE] `az sf managed-service create`: Hapus parameter yang sudah usang --service-dns-name, --drop-source-replica-on-move dan -instance-close-delay-duration.
* [BREAKING CHANGE] `az sf cluster`: Ganti nama parameter --vault-resource-group menjadi --vault-rg.
* `az sf managed-cluster and sf managed-node-type`: Atur grup sebagai bukan pratinjau
* Perbarui paket azure-mgmt-servicefabricmanagedclusters ke versi terbaru 1.0.0 yang menggunakan versi api GA 2021-05-01.
* `az sf managed-cluster create`: Tambahkan parameter --upgrade-mode, --upgrade-cadence dan --code-version.
* `az sf managed-node-type`: Tambahkan parameter --data-disk-type, --is-stateless dan --multiple-placement-groups.

### <a name="sql"></a>SQL

* `az sql server create`: Tambahkan spasi untuk membagi kata-kata yang digabungkan dalam pesan bantuan argumen --assign-identity.
* `az sql server update`: Tambahkan spasi untuk membagi kata-kata yang digabungkan dalam pesan bantuan argumen --assign_identity.

### <a name="storage"></a>Penyimpanan

* [BREAKING CHANGE] `az storage share-rm delete`: Timbulkan kesalahan saat ada snapshot untuk berbagi file target dan tambahkan `--include` untuk menentukan menghapus berbagi file target dan snapshotnya
* `az storage blob generate-sas`: Tambahkan spasi untuk membagi kata-kata yang digabungkan dalam pesan bantuan argumen --cache-control, --content-disposition, --content-encoding, --content-language dan --content-type.
* `az storage blob url`: Tambahkan spasi untuk membagi kata-kata yang digabungkan dalam pesan bantuan argumen --snapshot.
* `az storage container generate-sas`: Tambahkan spasi untuk membagi kata-kata yang digabungkan dalam pesan bantuan argumen --cache-control, --content-disposition, --content-encoding, --content-language dan --content-type.
* Tingkatkan versi API penyimpanan ke 2021-04-01
* Mendukung izin berbagi default
* Mendukung replikasi objek lintas penyewa
* Inventaris blob GA
* `az storage share-rm list`: Daftar dukungan dengan snapshot.

## <a name="may-06-2021"></a>06 Mei 2021

Versi 2.23.0

### <a name="acr"></a>ACR

* `az acr check-health`: Tambahkan dukungan untuk memverifikasi perutean dns ke titik akhir pribadi
* Memperbaiki #17618: Memperbarui penanganan add/update kredensial untuk tugas yang dibuat menggunakan --auth-mode

### <a name="aks"></a>AKS

* `az aks update`: Tambahkan `--windows-admin-password` ke dukungan memperbarui kata sandi Windows
* `az aks update`: Mendukung pembaruan dari klaster SPN ke klaster MSI.
* `az aks create`: Tambahkan `--enable-encryption-at-host` parameter

### <a name="app-service"></a>App Service

* [MELANGGAR PERUBAHAN] Perbarui SDK situs web ke versi terbaru (azure-mgmt-web==2.0.0) & Mengadopsi SDK track2
* [MELANGGAR PERUBAHAN] Ganti `az staticwebapp browse` nama menjadi `az staticwebapp show`
* Tambahkan opsi sku untuk `az staticwebapp create --sku`
* Perintah Tambahkan `az staticwebapp update`
* `az webapp/functionapp config access-restriction add/remove`: Dukungan untuk Tag Layanan, header Http, dan aturan multi-sumber.

### <a name="arm"></a>ARM

* `az bicep`: Ganti API datetime yang tidak tersedia di Python 3.6
* `az deployment group create`: Memperbaiki masalah kompatibilitas versi api untuk parameter `--template-specs`

### <a name="backup"></a>Cadangan

* `az backup vault create`: Tambahkan tag sebagai argumen opsional
* Membuat AFS mengonfigurasi idempotent aliran cadangan

### <a name="cdn"></a>CDN

* `az cdn endpoint rule add`: Memperbaiki pembuatan aturan pengiriman untuk SKU non-Microsoft

### <a name="compute"></a>Compute

* Lokasi diperpanjang untuk Compute RP
* `az sig image-version create`: Dukungan membuat dari VHD
* `az vm create --count`: Mendukung konfigurasi vnet dan subnet
* `az vmss extension upgrade`: Memperbaiki bug
* Menambahkan pesan kesalahan untuk `vm identity assign`
* Disk terkelola zone-redundant storage (ZRS)
* `az disk create`: Peluncuran tepercaya
* `az disk create`: Hibernasi
* Memperbaiki masalah kompatibilitas versi API lama
* `az sig image version create`: Mendukung VHD disk data

### <a name="feedback-reference"></a>Referensi umpan balik

* Jangan minify badan masalah umpan balik

### <a name="functionapp"></a>FunctionApp

* Memperbaiki masalah dengan penyebaran zip di mana waktu lokal disediakan tetapi UTC diharapkan
* Memperbarui tumpukan api json untuk menambahkan PowerShell di Linux di Functions

### <a name="hdinsight"></a>HDInsight

* Tambahkan Incoming BREAKING CHANGE untuk menghapus nilai `--workernode-size` default dan  `--headnode-size`

### <a name="key-vault"></a>Key Vault

* [MELANGGAR PERUBAHAN] Mendukung fitur soft-delete untuk managed-HSM. `keyvault delete --hsm-name` akan melakukan soft delete pada MHSM.

### <a name="marketplace-ordering"></a>Pemesanan Marketplace

* Grup perintah baru `az term` untuk menerima/menampilkan persyaratan

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
* `az network application-gateway show-backend-health`: mendukung argumen operasi penyelidikan.
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
* Bump dibundel python ke `3.8.9` msi.

### <a name="rdbms"></a>RDBMS
* [BREAKING CHANGE] `az mysql flexible-server create`: `--storage-size` nilai default diubah dari 10 menjadi 32.
* `az postgres flexible-server create`: Tambahkan `--private-dns-zone` parameter untuk membuat server dengan akses pribadi.

### <a name="role"></a>Peran

* `az role assignment create/update`: Lengkapi otomatis `assignee_principal_type`

### <a name="sql"></a>SQL

* `az sql db create`: Tambahkan argumen --ha-replicas
* `az sql db replica create`: Tambahkan argumen --ha-replicas
* Izinkan nama kebijakan mw pendek untuk mi

### <a name="sql-vm"></a>SQL VM

* Jadikan SqlServerLicenseType sebagai opsional

### <a name="storage"></a>Penyimpanan

* Memperbaiki #16272 & #16853: Perbaiki pesan kesalahan
* `az storage account create`: Tambahkan dukungan zona tepi
* Mendukung identitas yang ditetapkan pengguna untuk akun penyimpanan
* `az storage account create/update`: Mendukung sas&kebijakan utama

### <a name="synapse"></a>Synapse

* `az synapse notebook create`: Membuat buku catatan

## <a name="april-19-2021"></a>19 April 2021 pukul

Versi 2.22.1

### <a name="arm"></a>ARM

* Hotfix: Perbaiki masalah yang dibangun bisep rusak di Python 3.6

### <a name="key-vault"></a>Key Vault

* Hotfix: GA untuk perintah dan parameter ralated terkelola-HSM

## <a name="april-13-2021"></a>13 April 2021 pukul

Versi 2.22.0

### <a name="acr"></a>ACR

* [BREAKING CHANGE] `az acr connected-registry install info`: Ganti kunci ACR_REGISTRY_NAME, ACR_SYNC_TOKEN_NAME, ACR_SYNC_TOKEN_PASSWORD, ACR_PARENT_GATEWAY_ENDPOINT, dan ACR_PARENT_PROTOCOL dengan kunci string baru yang terhubung, ACR_REGISTRY_CONNECTION_STRING.
* [BREAKING CHANGE] `az acr connected-registry install renew-credentials`: Ganti kunci ACR_REGISTRY_NAME, ACR_SYNC_TOKEN_NAME, ACR_SYNC_TOKEN_PASSWORD, ACR_PARENT_GATEWAY_ENDPOINT, dan ACR_PARENT_PROTOCOL dengan kunci string baru yang terhubung, ACR_REGISTRY_CONNECTION_STRING.
* `az acr connected-registry create`: Verifikasi sebelum pembuatan token dan sinkronkan peta cakupan bahwa semua leluhur aktif.
* `az acr connected-registry create`: Tambahkan izin repositori dan gateway yang diperlukan untuk pembuatan ke semua leluhur registri baru yang terhubung jika diperlukan sebelum pembuatan registri yang terhubung.
* `az acr connected-registry delete`: Hapus izin gateway dari sumber daya yang dihapus dari semua peta cakupan sinkronisasi leluhurnya.
* `az acr connected-registry repo`: Perintah baru untuk menambahkan izin repositori ke registri yang terhubung dan semua peta cakupan sinkronisasi leluhurnya, dan menghapus izin repositori dari registri yang terhubung dan semua peta cakupan sinkronisasi turunannya

### <a name="aks"></a>AKS

* `az aks create`: Tambahkan dukungan dan `--private-dns-zone` `--fqdn-subdomain` fitur

### <a name="app-config"></a>Konfigurasi Aplikasi

* Mengonfigurasi lebar garis maks untuk parser YAML untuk menghentikan pembungkus output
* Memperbaiki bug dalam pratinjau cetak perintah pemulihan

### <a name="app-service"></a>App Service

* Memperbaiki #17219: Perbaiki bug ssl bind
* Menghapus bendera pratinjau untuk Python 3.9 di perintah aplikasi create function
* Bugfix: Tangani jika hanya satu profil publikasi yang dikembalikan
* Perbaiki # 16203: az webapp log tail mendukung webapps yang berjalan di Linix.

### <a name="arm"></a>ARM

* [BREAKING CHANGE] `az bicep build`: Ubah parameter `--files` menjadi `--file`
* [BREAKING CHANGE] `az bicep decompile`: Ubah parameter `--files` menjadi `--file`
* Memperbaiki #17379: hasil pemasangan otomatis bisep dalam output json yang tidak valid dari penyebaran
* `az bicep build`: Menambahkan parameter `--outdir` untuk menentukan direktori output
* `az bicep build`: Menambahkan parameter `--outfile` untuk menentukan jalur file output
* Memperbaiki masalah saat memeriksa pemutakhiran versi untuk Bicep CLI memberikan pengecualian jika batas tarif API GitHub tercapai
* `az policy exemption`: Tambahkan perintah baru untuk mendukung pembebasan kebijakan

### <a name="backup"></a>Cadangan

* Memperbaiki #14776: Memperbaiki `--force` fungsionalitas parameter untuk `az backup vault delete` perintah
* Memperbaiki pencadangan permintaan
* `az backup protectable-item list`: Tambahkan parameter opsional `--backup-management-type`
* Memperbaiki pembuatan kebijakan dengan rgNamePrefix dan rgNameSuffix
* `az backup protectable-item list`: Tambahkan `--server-name` sebagai argumen opsional

### <a name="compute"></a>Compute

* `az ssh vm`: Mendukung VM SSH dengan Service Principal
* Menambahkan opsi Peningkatan Bergulir VMSS
* Perintah baru: `vm install-patches`
* Set enkripsi disk: Tambahkan `--enable-auto-key-rotation`

### <a name="container"></a>Kontainer

* Memperbaiki #16499: `az container create`: Perbaiki penanganan nilai pengembalian dari network_profiles.create_or_update

### <a name="cosmos-db"></a>Cosmos DB

* Dukungan untuk identitas layanan terkelola & identitas default

### <a name="eventgrid"></a>EventGrid

* `az eventgrid system-topic create/update`: Tambahkan Dukungan MSI
* `az eventgrid [partner topic | system-topic] event-subscription`: Tambahkan dukungan untuk StorageQueueMessageTTL, AdvancedFilters, EnableAdvancedFilteringOnArrays
* `az eventgrid [partner topic | system-topic] event-subscription`: Tambahkan dukungan untuk atribut pengiriman
* `az eventgrid topic create`: Tambahkan dukungan untuk membuat topik untuk azure atau azurearc

### <a name="interactive"></a>Interaktif

* Memperbaiki #16931: Perbaiki `KeyError` di `az interactive --update`

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`: Parameter opsional ditambahkan bernama allow-local-ldap-users
* `az netappfiles volume create`: Parameter opsional ditambahkan bernama ldap-enabled
* `az netappfiles volume backup status show`: Operasi ditambahkan
* Memperbarui pengujian cadangan

### <a name="network"></a>Jaringan

* `az network vnet-gateway`: `--vpn-auth-type` izinkan nilai multi

### <a name="packaging"></a>Pengemasan

* [MELANGGAR PERUBAHAN] RPM diinstal az sekarang menggunakan `python3` bukan hard-coded `/usr/bin/python3`.

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

* `az storage fs directory upload/download`: Mendukung adls gen2 file system directory upload&download
* `az storage fs file list`: Mendukung --show-next-marker
* `az storage share-rm`: Mendukung membuat/menampilkan/menghapus snapshot

### <a name="synapse"></a>Synapse

* [BREAKING CHANGE] `az synapse role assignment create`: Nama peran di versi lama tidak diperbolehkan, Sql Admin, Apache Spark Admin, Workspace Admin
* [MELANGGAR PERUBAHAN] `az synapse role assignment create`: Ketika argumen --assignee tidak dapat secara unik menentukan objek utama, perintah akan meningkatkan kesalahan alih-alih menambahkan penetapan peran untuk objek utama yang tidak pasti.
* `az synapse role scope list`: Daftar semua cakupan yang didukung synapse.
* `az synapse role assignment create/list/delete`: Tambahkan argumen --scope/--item-type/-item untuk mendukung pengelolaan penetapan peran berdasarkan cakupan.
* `az synapse role assignment create/list/delete`: Tambahkan argumen --assignee-object-id, itu akan melewati API Graph dan secara unik menentukan objek utama alih-alih menyimpulkan objek utama menggunakan argumen --assignee.

## <a name="march-23-2021"></a>23 Maret 2021

Versi 2.21.0

### <a name="acr"></a>ACR

* Output jejak untuk `az acr login` mendiagnosis sendiri latensi perintah docker potensial
* Perbaiki # 17172: Saat menjalankan pemeriksaan kesehatan di belakang proxy perusahaan
* `acr update`: Mendukung tarikan anonim
* Memperbaiki #16700: Gunakan api "ada" untuk memeriksa keberadaan blob penyimpanan

### <a name="aks"></a>AKS

* `aks update`: Tambahkan `--no-uptime-sla`
* Memperbaiki kesalahan identitas penetapan lintas sub dan melampirkan kesalahan acr
* Menambahkan dukungan untuk ID awalan IP publik node

### <a name="apim"></a>APIM

* [BREAKING CHANGE] `apim backup`: `--storage-account-container` tidak mendukung multi-nilai.
* [BREAKING CHANGE] `apim restore`: `--storage-account-container` tidak mendukung multi-nilai.

### <a name="app-service"></a>App Service

* [MELANGGAR PERUBAHAN] Perbaiki #16087: `az webapp config ssl create`: atur `--name` parameter sesuai kebutuhan.
* Memperbaiki #17053: `az webapp show` mengembalikan nilai null untuk properti SiteConfig
* Perbaiki #17207: `az webapp log config`: 'level' selalu default ke verbose

### <a name="arm"></a>ARM

* `az bicep build`: memperbaiki masalah di mana peringatan build tidak ditampilkan

### <a name="backup"></a>Cadangan

* Menambahkan `id_part` nama sub-sumber daya untuk diperbaiki `--ids`
* Memperbaiki # 17094: Membuat rangkaian tes terpisah untuk tes CRR
* `az backup protection check-vm`: Tambahkan `--vm` dan `--resource-group` sebagai params opsional

### <a name="cache"></a>Cache

* GA `az cache`

### <a name="cdn"></a>CDN

* `az afd rule create`: Memperbaiki `--help` pesan

### <a name="compute"></a>Compute

* Memperbaiki bug pembaruan pengguna vm Windows
* Perbaiki #16585: `az vmss deallocate`: `--instance-ids` gagal
* `az vm create`: Parameter baru `--platform-fault-domain` dalam mode FLEX VMSS
* `az vm create`: `--patch-mode` untuk Linux VM
* `az ssh vm`: Secara otomatis meluncurkan browser saat mendapatkan sertifikat gagal
* `az vm create`: Parameter baru `--count`
* `az vm create`: Peluncuran Tepercaya
* Perbaiki #16037: az vm open-port menerima daftar port

### <a name="extension"></a>Ekstensi

* Menambahkan pesan yang dapat ditindaklanjuti saat ekstensi tidak kompatibel dengan inti CLI

### <a name="key-vault"></a>Key Vault

* `az keyvault role definition list`: Dukungan `--custom-role-only` untuk hanya mencantumkan definisi peran kustom
* Mendukung definisi peran kustom keyvault
* Tambahkan `--no-wait` untuk perintah `az keyvault security-domain download` dan `--target-operation` untuk perintah `az keyvault security-domain wait`

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account backup show`: Operasi ditambahkan.
* `az netappfiles account backup delete`: Operasi ditambahkan.
* `az netappfiles account ad add`: Parameter `--ldap-over-tls` ditambahkan.
* `az netappfiles account create`: Parameter `--encryption` ditambahkan.
* `az netappfiles account update`: Parameter `--encryption` ditambahkan.
* `az netappfiles volume create`: Parameter `--encryption-key-source` ditambahkan.
* `az netappfiles volume create`: Kebijakan ekspor default dihapus untuk nfsv4.1 dan parameter opsional ditambahkan untuk menyiapkan kebijakan ekspor untuk nfsv4.1: rule_index, unix_read_only, unix_read_write, cifs, allowed_clients

### <a name="network"></a>Jaringan

* `az network public-ip prefix create`: Dukungan `--zone 1 2 3`
* `az network lb frontend-ip create`: Dukungan `--zone 1 2 3`
* Versi bump dari '2020-08-01' hingga '2020-11-01'
* `az network lb address-pool`: Mendukung subnet saat membuat atau memperbarui kumpulan backend berbasis IP dari penyeimbang beban.

### <a name="rdbms"></a>RDBMS

* Pengujian tambahan untuk pipeline tim server yang fleksibel
* Migrasi Python SDK
* Menambahkan database PostgreSQL membuat, menampilkan, dan menghapus fitur
* Memperbarui Python SDK ke 8.1.0b2

### <a name="role"></a>Peran

* `az ad app permission list/grant`: Memperbaiki pesan kesalahan saat tidak ada Kepala Layanan terkait yang ada untuk Aplikasi

### <a name="search"></a>Cari

* `az search`: GA

### <a name="service-fabric"></a>Service Fabric

* `az sf certificate`: deprecate perintah cert cluster.

### <a name="sql"></a>SQL

* Perintah Tambahkan Grup Kepercayaan Server

### <a name="storage"></a>Penyimpanan

* Memperbaiki #16917: `az storage account generate-sas` gagal jika string koneksi disediakan
* Memperbaiki #16979: `az storage container create` gagal saat menyediakan metadata kontainer penyimpanan

### <a name="upgrade"></a>Mutakhirkan

* Memperbaiki #16952: Perbaiki ImportError setelah pemutakhiran

### <a name="misc"></a>Misc.

* Perbolehkan mengonfigurasi tema

## <a name="march-02-2021"></a>02 Maret 2021

Versi 2.20.0

### <a name="aks"></a>AKS

* Tambahkan dukungan untuk addon SGX 'confcom'

### <a name="ams"></a>AMS

* Perbarui modul untuk menggunakan api Azure Media Services 2020.
* `az ams account encryption`: Subkelompok baru untuk menampilkan atau mengatur enkripsi untuk akun layanan media
* `az ams account storage set-authentication`: Perintah baru untuk mengatur autentikasi untuk akun penyimpanan yang terkait dengan akun layanan media
* `az ams account create (mi-system-assigned)`: Parameter baru --mi-system-assigned untuk pembuatan akun untuk mengatur identitas terkelola akun media
* `az ams account mru set`: Perintah ini tidak akan lagi berfungsi untuk Media Services akun yang dibuat dengan API versi 2020-05-01 atau versi lebih baru.
* `az ams live-event create (stretch-mode, key-frame-interval, transcrip-lang, use-static-hostname, custom hostname)`: Tambahkan opsi parameter baru ke perintah pembuatan acara langsung
* `az ams live-event standby`: Perintah baru untuk menempatkan acara langsung dalam mode siaga
* `az ams transform create (videoanalysismode, audioanalysis mode)`: Opsi parameter baru untuk transform create

### <a name="app-service"></a>App Service

* `az webapp config ssl bind`: menangani jika paket webapp dan appservice di rg yang berbeda. Juga referensi pembaruan teks
* Perbaiki #8743: az webapp deploy
* Bugfix: Tambahkan generateRandomAppNames.json ke pengaturan
* `az functionapp create`: Tambahkan dukungan pratinjau untuk membuat aplikasi yang terisolasi dotnet.
* Memperbaiki #12150: Dukungan untuk subnet ID dalam add vnet-integration
* `az functionapp create`: Hapus bendera pratinjau dari Node.js 14.

### <a name="arm"></a>ARM

* `az deployment group/sub/mg/tenant validate/create/what-if`: Tambahkan dukungan untuk file Bicep
* `az bicep install`: Perintah baru untuk menginstal Bicep CLI
* `az bicep upgrade`: Perintah baru untuk meningkatkan Bicep CLI
* `az bicep build`: Perintah baru untuk membuat file Bicep
* `az bicep version`: Perintah baru untuk menampilkan versi Bicep CLI yang diinstal saat ini
* `az bicep list-versions`: Perintah baru untuk menampilkan versi CLI Bicep yang tersedia
* `az managedapp definition update`: Menambahkan perintah baru untuk memperbarui definisi managedapp

### <a name="backup"></a>Cadangan

* `az backup recoverypoint show-log-chain`: Tambahkan waktu mulai/akhir dalam output tabel show-log-chain
* BugFix: Aktifkan Pemulihan Lokasi Alternatif untuk item yang dilindungi SQL/SAPHANA

### <a name="cdn"></a>CDN

* Menambahkan dukungan cli untuk AFD SKU

### <a name="compute"></a>Compute

* `az vm (extension) image list`: Membuatnya lebih kuat
* `az vmss create`: Memperbaiki masalah jenis lisensi
* Tingkatkan versi API ke 2020-12-01
* `az vm create`: tambahkan `--enable-hotpatching`

### <a name="cosmos-db"></a>Cosmos DB

* Tingkatkan ke versi 3.0.0 dan tambahkan dukungan untuk NetworkAclBypass + Perbarui Mongo ServerVersion + kebijakan cadangan

### <a name="extension"></a>Ekstensi

* Mendukung konfigurasi url indeks ekstensi

### <a name="iot-central"></a>IoT Pusat

* `az iot central app`: Mengatasi beberapa perbaikan S360
* `az iot central app update`: Hapus kebutuhan memeriksa etag saat memperbarui aplikasi iotc yang ada.
* Ubah resourceType (IotApps) menjadi dalam kasus unta.

### <a name="key-vault"></a>Key Vault

* [BREAKING CHANGE] `az keyvault role assignment/definition list`: `roleDefinitionName` harus `roleName` dalam output perintah
* [MELANGGAR PERUBAHAN] `id` perubahan menjadi `jobId`, `azureStorageBlobContainerUri` perubahan untuk menjadi `folderUrl` output perintah dari `az keyvault backup/restore`, `az keyvault key restore`

### <a name="network"></a>Jaringan

* Versi bump dari '2020-07-01' hingga '2020-08-01'
* `az network public-ip create`: Dukung '--zona 1 2 3' setelah '2020-08-01'
* `az network routeserver peering`: Ganti nama dengan `--vrouter-name``--routeserver`
* `az network express-route peering create`: Mendukung alamat ipv6
* `az network public-ip create`: Mengekspos argumen baru `--tier`

### <a name="openshift"></a>OpenShift

* Pembaruan az openshift deprecation warning

### <a name="search"></a>Cari

* `az search`: Perbaiki `--identity-type` panduan pembantu.

### <a name="sql"></a>SQL

* Update az sql mi examples
* `az sql db/elastic-pool create/update`: Tambahkan argumen konfigurasi pemeliharaan
* `az sql db replica create`: Tambahkan argumen tipe --sekunder

### <a name="storage"></a>Penyimpanan

* [MELANGGAR PERUBAHAN] `az storage account file-service-properties`: Default untuk mengaktifkan kebijakan retensi penghapusan dengan hari retensi 7 di sisi server
* Perbaiki #16872: az storage blob now (2.19) memerlukan login bahkan jika connection-string disediakan
* Memperbaiki #16959: az storage copy crash: ValidationError: variabel lokal 'service' direferensikan sebelum penugasan
* Perbaiki #14054: Objek 'NoneType' tidak memiliki atribut '__nama__'
* Perbaiki #16679: `az storage blob download` gagal dengan "Izin ditolak" jika file tujuan adalah direktori
* Tingkatkan versi api penyimpanan ke 2021-01-01
* Versi dukungan dalam kebijakan manajemen Lifecyle
* Mendukung manajemen akses kunci bersama akun penyimpanan
* `az storage account network-rule`: Aturan akses sumber daya GA
* Mendukung enkripsi ganda untuk cakupan enkripsi
* `az storage account blob-service-properties update`: Mendukung --change-feed-retention-days
* Mendukung penulisan ulang blob yang ada

## <a name="february-10-2021"></a>10 Februari 2021

Versi 2.19.1

### <a name="key-vault"></a>Key Vault

* Hotfix: Paket `azure-keyvault-administration` dependensi disematkan ke 4.0.0b1

## <a name="february-09-2021"></a>09 Februari 2021 pukul

Versi 2.19.0

### <a name="acr"></a>ACR

* `az acr connected-registry install info`: Tambahkan kunci `ACR_SYNC_TOKEN_NAME` baru dengan nilai yang sama dengan `ACR_SYNC_TOKEN_USERNAME`. Peringatan bahwa yang terakhir akan tidak digunakan lagi ditampilkan.
* `az acr connected-registry install renew-credentials`: Tambahkan kunci `ACR_SYNC_TOKEN_NAME` baru dengan nilai yang sama dengan `ACR_SYNC_TOKEN_USERNAME`. Peringatan bahwa yang terakhir akan tidak digunakan lagi ditampilkan.

### <a name="aks"></a>AKS

* Menambahkan pengikatan stop/start klaster terkelola
* `az aks check-acr`: Perbaiki pemeriksaan versi Kubernetes

### <a name="apim"></a>APIM

* GA grup perintah

### <a name="app-config"></a>Konfigurasi Aplikasi

* [BREAKING CHANGE] `az appconfig feature filter add`: Mendukung penambahan objek JSON sebagai nilai parameter filter fitur

### <a name="app-service"></a>App Service

* `az appservice ase/plan`: Mendukung ASEv3
* Perbaiki #16026 dan #16118 untuk paket az appservice
* Memperbaiki #16509: Tambahkan dukungan untuk os-preference
* Meningkatkan perilaku layanan aplikasi ase create-inbound-services untuk memungkinkan melewatkan layanan DNS dan mendukung DNS untuk ASEv2
* `az webapp up/az webapp create`: Memperbaiki kesalahan nonetype
* `az webapp up/create`: penanganan kesalahan nama aplikasi yang lebih baik dengan periode
* Memperbaiki # 16681: `az webapp config ssl import`: Perbaiki bug yang menyebabkan kegagalan pada awan nasional

### <a name="arm"></a>ARM

* `az provider register`: Mendukung grup manajemen pendaftaran

### <a name="backup"></a>Cadangan

* Menambahkan fungsionalitas CRR untuk IaaSVM dan perintah CRR lainnya
* `az backup protectable-item list`: Tambahkan tipe item yang dapat dilindungi sebagai argumen opsional

### <a name="botservice"></a>BotService

* `az bot create/update`: Tambahkan fitur `--cmk-key-url` Enkripsi dan `--encryption-off`
* `az bot update`: Ganti nama arg Enkripsi-OFF menjadi CMK-OFF dan memperbarui versi api

### <a name="compute"></a>Compute

* [BREAKING CHANGE] vmss create: Mengganti nama nilai mode orkestrasi
* Grup perintah baru sshkey. Mengizinkan referensi sumber daya kunci SSH saat membuat VM
* `az disk create/update`: Tambahkan parameter `--enable-bursting` untuk mendukung bursting disk

### <a name="extension"></a>Ekstensi

* Pencocokan awalan perintah ekstensi dukungan untuk penginstalan dinamis

### <a name="hdinsight"></a>HDInsight

* `az hdinsight create`: Tambahkan parameter `--enable-compute-isolation` baru untuk mendukung pembuatan klaster dengan fitur isolasi komputasi.

### <a name="key-vault"></a>Key Vault

* `az keyvault key import`: Parameter dukungan `--curve` untuk mengimpor kunci BYOK
* `az keyvault certificate download`: Perbaiki panggilan metode yang tidak digunakan lagi/dihapus
* `az keyvault create/update`: Hapus tag pratinjau untuk `--enable-rbac-authorization`

### <a name="monitor"></a>Monitor

* `az monitor metrics alert create`: Perbaiki kesalahan 'sumber daya tidak ditemukan'

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`: Tambahkan parameter `--security-operators`.
* `az netappfiles volume create`: Tambahkan parameter `--smb-continuously-available`.
* `az netappfiles volume create`: Tambahkan parameter `--smb-encryption`.
* `az netappfiles`: Tidak lagi dalam mode pratinjau.

### <a name="network"></a>Jaringan

* [BREAKING CHANGE] `az network vrouter`: Bejat grup perintah ini, silakan gunakan `az network routeserver`.
* `az network routeserver`: Tambahkan grup perintah baru.
* `az network application-gateway create`: Tambahkan parameter `--ssl-profile-id`
* `az network application-gateway client-cert`: Kelola sertifikat gateway aplikasi klien tepercaya
* `az network application-gateway ssl-profile`: Mengelola profil ssl gateway aplikasi
* Menambahkan dukungan untuk koneksi titik akhir pribadi ke DigitalTwins

### <a name="profile"></a>Profil

* `az login`: Luncurkan browser di WSL 2

### <a name="rdbms"></a>RDBMS

* `az mysql flexible-server create --iops`: Izinkan pengguna memilih IOPS untuk SKU mereka.
* Memperbarui perintah pemulihan Postgres untuk mendukung zona yang tersedia

### <a name="search"></a>Cari

* Upgrade untuk menggunakan sdk python azure-mgmt-search terbaru (8.0.0) azure-mgmt-search
* `az search create`: Tambahkan dukungan untuk pembuatan layanan pencarian dengan aturan IP, akses titik akhir publik, dan/atau msi
* `az search update`: Tambahkan dukungan untuk pembaruan layanan pencarian dengan aturan IP, akses titik akhir publik, dan/atau msi
* `az search private-endpoint-connection`: Mengelola koneksi titik akhir pribadi ke layanan pencarian
* `az search shared-private-link-resource`: Mengelola sumber daya tautan pribadi bersama di layanan pencarian
* `az search private-link-resource`: Daftar sumber daya tautan pribadi yang tersedia di layanan pencarian

### <a name="security"></a>Keamanan

* Menambahkan perintah baru untuk `az security`

### <a name="sql"></a>SQL

* Tambahkan pertandingan hsm regex yang dikelola ke SQL
* Upgrade azure-mgmt-sql to 0.26.0
* `az sql mi create/update`: Menambahkan dukungan untuk konfigurasi pemeliharaan dalam operasi instans terkelola
* Mendukung perintah kebijakan audit DevOps server SQL

### <a name="storage"></a>Penyimpanan

* Perbaiki #16079: gumpalan publik memberikan kesalahan
* Referensi perutean Storage GA
* Memperbaiki # 9158: Tidak dapat menghasilkan kunci SAS yang berfungsi dari kebijakan
* Perbaiki #16489: Tingkatkan azcopy ke 10.8.0
* `az storage account blob-service-properties`: Mendukung versi layanan default
* Perbaiki # 16519: azcopy diberikan SAS yang lebih kuat dari yang dibutuhkan (telah menulis, hanya perlu dibaca)

### <a name="synapse"></a>Synapse

* `az synapse workspace create `: Tambahkan parameter `--key-identifier` ke dukungan untuk membuat ruang kerja menggunakan kunci yang dikelola pelanggan.
* `az synapse workspace key`: Tambahkan cmdlet CRUD untuk mendukung pengelolaan kunci di bawah ruang kerja sinaps yang ditentukan.
* `az synapse workspace managed-identity`: Tambahkan cmdlet untuk mendukung identitas terkelola CRUD ke pengaturan akses sql.
* `az synapse workspace`: Tambahkan dukungan perlindungan eksfiltrasi data, tambahkan parameter `--allowed-tenant-ids`.

## <a name="january-19-2021"></a>19 Januari 2021 pukul

Versi 2.18.0

### <a name="acr"></a>ACR

* `az acr create / update`: Tambahkan `--allow-trusted-services`. Parameter ini menentukan apakah layanan azure tepercaya diizinkan untuk mengakses registri terbatas jaringan. Defaultnya adalah mengizinkan.

### <a name="aks"></a>AKS

* `az aks check-acr`: Tambahkan perintah check-acr baru

### <a name="app-service"></a>App Service

* Memperbaiki #13907: `az webapp config ssl import`: Ubah perintah untuk juga mengimpor Sertifikat Layanan Aplikasi
* Perbaiki # 16125: `az webapp ssh`: Jika menggunakan klien windows, buka browser ke tautan scm
* Perbaiki # 13291: `az webapp deployment slot swap`: Perintah harus mendukung pertahankan vnet.
* [MELANGGAR PERUBAHAN] Memperbaiki regresi di mana Anda tidak dapat menggunakan versi runtime dengan spasi dalam nama

### <a name="arm"></a>ARM

* `az deployment` : Tambahkan dukungan untuk `--query-string`
* `az ts`: Perbaikan penanganan kesalahan tanpa `--template-file` `--version` dilarang

### <a name="backup"></a>Cadangan

* `az backup protection backup-now`: Atur periode retensi default menjadi 30 hari

### <a name="compute"></a>Compute

* Memperbaiki masalah tidak ada storage_profile
* Penanganan kesalahan token eksternal yang lebih baik
* Memperbaiki masalah reimage vmss
* `az vm/vmss extension set`: Parameter baru `--enable-auto-upgrade`

### <a name="container"></a>Kontainer

* `az container exec`: Hapus pemeriksaan eol untuk menghindari penutupan terminal bahkan sebelum dimulai di linux

### <a name="dms"></a>DMS

* `az dms project task create`: Menambahkan parameter tipe tugas untuk membantu membedakan apakah skenario adalah migrasi online atau migrasi offline.
* `az dms project task cutover`: Tambahkan perintah baru yang memungkinkan tugas dengan jenis tugas migrasi online untuk memotong dan mengakhiri migrasi.
* `az dms project create/az dms project task create`: Aktifkan proyek /tugas MySQL dan PostgreSQL yang akan dibuat.

### <a name="iot"></a>IoT

* Menambahkan --tag ke IoT Hub membuat dan memperbarui

### <a name="monitor"></a>Monitor

* [BREAKING CHANGE] `az monitor log-analytics workspace data-export`: Hapus parameter yang `--export-all-tables` tidak digunakan lagi dan memerlukan `--tables` parameter

### <a name="rdbms"></a>RDBMS

* Menghapus tag pratinjau untuk kunci server dan perintah admin iklan untuk Postgres dan MySql

### <a name="role"></a>Peran

* Perbaiki #11594: `az role assignment create`: Hanya tampilkan nilai yang didukung untuk `--assignee-principal-type`

### <a name="storage"></a>Penyimpanan

* Perbaiki # 16072: file Upload dengan ukuran besar
* Perbaiki #12291: `az storage blob generate-sas` tidak menyandikan dengan benar `--full-uri`
* PROPERTI LAYANAN GA PITR dan blob di SRP

## <a name="january-04-2021"></a>04 Januari 2021

Versi 2.17.1

### <a name="rdbms"></a>RDBMS

* Hotfix: `az mysql create`: Kembalikan nama parameter yang salah 'serv_name' ke 'service_name'

## <a name="december-29-2020"></a>29 Desember 2020 pukul

Versi 2.17.0

### <a name="acr"></a>ACR

* Redundansi zona dukungan
* `az acr connected-registry`: Fitur baru untuk Azure Container Registry on-prem
* `az acr scope-map update`: --add dan --remove tidak digunakan lagi, mereka diganti namanya menjadi --add-repo --remove-repo
* `az acr scope-map create/update`: Tambahkan dukungan untuk menangani tindakan Gateway.
* `az acr token create`: dukungan ditambahkan untuk tindakan gateway

### <a name="aks"></a>AKS

* Memperbaiki: menambahkan argumen yang dihapus oleh PR sebelumnya
* `az aks get-credentials`: Klarifikasi dokumentasi untuk mendapatkan kredensial

### <a name="app-service"></a>App Service

* Memungkinkan pelanggan membuat aplikasi fungsi Python 3.9
* Perbaiki #14583: az webapp up harus menghasilkan nama default jika nama tidak disediakan
* Memperbaiki: Penanganan kesalahan yang lebih baik saat mencoba membuat ASP duplikat di lokasi diff

### <a name="arm"></a>ARM

* `az ts`: Tambahkan dukungan untuk --tags
* `az ts`: Mendukung menghapus satu versi
* `az provider register`: Tambahkan --accept-terms untuk mendaftarkan RPaaS
* Memperbaiki penguraian file JSON dengan string multi-baris

### <a name="aro"></a>ARO

* `az aro delete`: Tambahkan validasi RBAC pada penghapusan klaster
* `az aro update`: Tambahkan validasi RBAC pada pembaruan klaster
* Pastikan worker_profile tidak ada sebelum mendapatkan subnet dari

### <a name="backup"></a>Cadangan

* `az backup job list`: Memecahkan bug tabel -o dan menambahkan backup_management_type sebagai input perintah

### <a name="batch"></a>Batch

* Tingkatkan bidang data ke [azure batch 10.0.0](https://pypi.org/project/azure-batch/10.0.0/)
* [MELANGGAR PERUBAHAN] az jumlah tugas tugas batch: Mengubah output dari objek JSON yang mengembalikan jumlah tugas ke objek JSON kompleks yang mencakup jumlah tugas (`taskCounts`) serta jumlah slot tugas (`taskSlotCounts`).

### <a name="compute"></a>Compute

* Jenis lisensi baru RHEL_ELS_6
* Mengadopsi track2 SDK, azure-mgmt-compute==18.0.0

### <a name="container"></a>Kontainer

* Perbaiki salah eja di `az container create` teks contoh CLI.

### <a name="databoxedge"></a>DataBoxEdge

* Modul perintah baru: dukungan untuk perangkat dan manajemen data-box-edge

### <a name="iot"></a>IoT

* Memperbarui pembuatan kunci perangkat
* Memperbarui pengujian hub berkemampuan identitas untuk memperbaiki masalah RBAC endpoint

### <a name="key-vault"></a>Key Vault

* `az keyvault key import`: Dukungan `--kty` untuk mengimpor kunci BYOK

### <a name="monitor"></a>Monitor

* `az monitor metrics alert create`: Meningkatkan pesan kesalahan untuk memberikan wawasan yang lebih dapat ditindaklanjuti

### <a name="network"></a>Jaringan

* `az network private-endpoint create`: Tambahkan deklarasi lebih lanjut dari '--subnet' dan '--private-connection-resource-id'
* Ubah validator aplikasi-gateway ssl-cert create
* Memigrasikan jaringan ke track2 SDK
* Memperbaiki bug untuk "az network traffic-manager profile create" saat menggunakan "--routing-method MultiValue"

### <a name="profile"></a>Profil

* Perbaiki "rahasia atau sertifikat yang hilang untuk mengautentikasi melalui kepala layanan"

### <a name="role"></a>Peran

* `az ad sp create-for-rbac`: Deprecate membuat penetapan peran Kontributor secara default

### <a name="security"></a>Keamanan

* Menambahkan perintah skor aman
* Memperbaiki perintah peringatan pembaruan dan mendukung nilai baru

### <a name="sql"></a>SQL

* `az sql dw update`: jangan menerima argumen backup-storage-redundancy
* `az sql db update`: memperbarui redundansi penyimpanan cadangan seperti yang diminta dari perintah

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah #15965: Memperjelas cara menghapus beberapa tag penahanan hukum dengan `az storage container legal-hold [clear|set]`
* `az storage account encryption-scope`: Dukungan GA
* Memperbaiki masalah #9959: Mencoba mengunduh versi snapshot dari berbagi file gagal dengan ResourceNotFound

### <a name="synapse"></a>Synapse

* Add new cmdlets az synapse sql ad-admin show, create, update, delete
* Add new cmdlet az synapse workspace firewall-rule update
* Add new cmdlets az synapse sql audit-policy show, update
* Menambahkan cmdlet terkait runtime integrasi

## <a name="december-08-2020"></a>08 Desember 2020

Versi 2.16.0

### <a name="acr"></a>ACR

* Perbarui deskripsi untuk param KEK

### <a name="aks"></a>AKS

* `az aks nodepool add/update/upgrade`: Ambil parameter lonjakan maks
* Menambahkan dukungan untuk addon AGIC
* Mengubah klaster MSI menjadi default

### <a name="apim"></a>APIM

* `az apim restore`: Perintah baru untuk memulihkan cadangan layanan API Management

### <a name="app-service"></a>App Service

* Memperbaiki # 14857: Biarkan pengguna memperbarui konfigurasi webapp bahkan dengan pembatasan akses
* `az functionapp create`: Terima `--runtime python` dan  `--runtime-version 3.9` sebagai parameter v3 Azure Functions
* Perbaiki #16041: az webapp config ssl membuat hasil dalam kesalahan yang tidak diketahui

### <a name="arm"></a>ARM

* `az deployment-scripts`: Hapus bendera pratinjau

### <a name="backup"></a>Cadangan

* Memperbaiki #14976: Perbaikan kesalahan CLI untuk kasus ValueError dan AttributeError
* `az backup protection undelete`: Tambahkan dukungan untuk perlindungan AzureWorkload undelete menggunakan CLI
* Memperbaiki Kesalahan Permintaan Buruk untuk Input Tipe Beban Kerja yang Benar

### <a name="cdn"></a>CDN

* Tambahkan dukungan multi-origin pratinjau.
* Tambahkan rotasi otomatis BYOC.

### <a name="key-vault"></a>Key Vault

* `az keyvault key/secret list`: Menambahkan parameter `--include-managed` ke daftar sumber daya terkelola

### <a name="monitor"></a>Monitor

* `az monitor metrics alert create`: Mendukung ambang batas dinamis untuk parameter kondisi
* `az monitor metrics alert update`: Mendukung ambang batas dinamis untuk parameter kondisi
* `az monitor metrics alert dimension create`: Membuat dimensi aturan peringatan metrik
* `az monitor metrics alert condition create`: Membangun kondisi aturan peringatan metrik

### <a name="mysql"></a>MySQL

* Tambahkan CLI pemutakhiran versi MySQL

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`Dua parameter opsional ditambahkan, aes_encryption dan ldap_signing
* `az netappfiles account backup-policy update`: Tiga parameter opsional ditambahkan bernama tag, jenis dan id
* `az netappfiles snapshot policy create`: Parameter opsional yang ditambahkan bernama provisioning_state

### <a name="network"></a>Jaringan

* `az network network watcher configure`: Perbaiki Kesalahan NetworkWatcherCountLimitReached yang disebabkan oleh sensitivitas kasus nilai lokasi
* `az network application-gateway http-listener`: Perbaiki bug yang tidak dapat membuat dan memperbarui dengan nama kebijakan WAF
* `az network route-table`: Deprecate tabel rute V1
* `az network cross-region-lb`: Mendukung penyeimbang beban lintas wilayah
* `az network express-route port generate-loa`: Perintah baru untuk membuat dan mengunduh surat otorisasi PDF untuk ExpressRoutePort

### <a name="packaging"></a>Pengemasan

* Tambahkan paket Ubuntu Groovy

### <a name="rdbms"></a>RDBMS

* Menambahkan server tunggal show-connection-string dan tes untuk perintah konteks lokal, pembuatan server

### <a name="role"></a>Peran

* Menambahkan ringkasan/peringatan panjang untuk perintah yang menghasilkan kredensial

### <a name="search"></a>Cari

* Menambahkan opsi SKU

### <a name="service-fabric"></a>Service Fabric

* Perbarui dokumen aplikasi SF. hanya dukungan untuk sumber daya yang digunakan lengan

### <a name="synapse"></a>Synapse

* Support synapse sql dw cmdlets and update az synapse workspace create cmdlet

## <a name="november-20-2020"></a>20 November 2020 tanggal 20

Versi 2.15.1

### <a name="profile"></a>Profil

* Hotfix: Fix #15961: az login: UnboundLocalError: variabel lokal 'token_entry' direferensikan sebelum penugasan

## <a name="november-17-2020"></a>17 November 2020

Versi 2.15.0

### <a name="acs"></a>ACS

* Menambahkan peringatan penghentian v3

### <a name="aks"></a>AKS

* Add ephemeral os functionality
* Peningkatan teknik: Ganti string addon dengan konstanta
* `az aks install-cli`: Mendukung url unduhan penyesuaian
* `az aks browse`: Arahkan ke tampilan sumber daya Azure Portal Kubernetes jika >k8s =1.19 atau kube-dashboard tidak diaktifkan
* Mendukung identitas pesawat kontrol BYO
* `az aks use-dev-spaces`: Menunjukkan bahwa perintah dev-spaces tidak digunakan lagi

### <a name="ams"></a>AMS

* Mengubah "wilayah" menjadi "lokasi" dalam string output: az ams account sp create

### <a name="app-config"></a>Konfigurasi Aplikasi

* Memperbaiki inisialisasi klien vault kunci

### <a name="app-service"></a>App Service

* Memperbaiki #13646: Tidak dapat membuat Paket Layanan Aplikasi di grup sumber daya yang berbeda dengan Lingkungan Layanan Aplikasi
* Perbaiki #11698 #15198 #14862 #15409: az webapp/functionapp config access-restriction add
* `az functionapp create`: Tambahkan dukungan pratinjau Node 14.
* `az functionapp create`: Hapus bendera pratinjau dari penangan kustom.
* [BREAKING CHANGE] az functionapp update: Migrasi functionapp dari Premium ke Rencana konsumsi sekarang memerlukan bendera '--force'.
* `az functionapp update`: Tambahkan pesan kesalahan jika migrasi functionapp melibatkan rencana apa pun di Linux.
* `az functionapp update`: Tambahkan pesan kesalahan yang lebih deskriptif jika migrasi functionapp gagal.

### <a name="arm"></a>ARM

* Memperbaiki masalah di mana What-If menampilkan dua cakupan grup sumber daya dengan casing yang berbeda
* `az deployment`: Mencetak detail kesalahan untuk penyebaran

### <a name="backup"></a>Cadangan

* Memperbaiki #14976: KeyError diperbaiki dan teks bantuan ditingkatkan

### <a name="batch"></a>Batch

* Memperbaiki # 15464: Perbarui periksa file pfx tanpa kata sandi dalam batch create_certificate

### <a name="billing"></a>Billing

* [BREAKING CHANGE] az billing invoice: Hapus properti BillingPeriodsNames dan DownloadUrlExpiry dari respons.
* `az billing invoice`: Mendukung banyak cakupan lain seperti BillingAccount, BillingProfile, dan langganan yang sudah ada.
* `az billing account`: Perintah baru untuk mendukung tampilan dan memperbarui akun penagihan yang ada.
* `az billing balance`: Perintah baru untuk mendukung keseimbangan tampilan profil penagihan.
* `az billing customer`: Perintah baru untuk mendukung tampilan pelanggan akun penagihan.
* `az billing policy`: Perintah baru untuk mendukung kebijakan tampilan dan pembaruan pelanggan atau profil penagihan.
* `az billing product`: Perintah baru untuk mengelola produk akun penagihan.
* `az billing profile`: Perintah baru untuk mengelola profil penagihan.
* `az billing property`: Perintah baru untuk menampilkan dan memperbarui properti akun penagihan.
* `az billing subscription`: Perintah baru untuk mengelola langganan untuk akun penagihan.
* `az billing transaction`: Perintah baru untuk mencantumkan transaksi faktur.
* `az billing agreement`: Perintah baru untuk mengelola perjanjian penagihan.
* `az billing permission`: Perintah baru untuk mengelola izin penagihan.
* `az billing role-assignment`: Perintah baru untuk mengelola tugas peran.
* `az billing role-definition`: Perintah baru untuk menampilkan definisi peran.
* `az billing instruction`: Perintah baru untuk mengelola instruksi penagihan.

### <a name="compute"></a>Compute

* Memperbaiki masalah pemeriksaan izin pembaruan
* Penyempurnaan format tabel daftar-skus vm
* grup host vm membuat: Buat --platform-fault-domain-count diperlukan dan perbarui bantuan
* Mendukung pembaruan versi vm/gambar saat mereka menggunakan gambar penyewa silang

### <a name="dps"></a>DPS

* Izinkan tag di perintah pembuatan IoT DPS

### <a name="hdinsight"></a>HDInsight

* az hdinsight create: Tambahkan dua parameter `--resource-provider-connection` dan `--enable-private-link` untuk mendukung fitur relay outbound dan private link.

### <a name="key-vault"></a>Key Vault

* Memperbaiki pesan kesalahan untuk HSM `list-deleted` dan `purge`
* Mendukung pemulihan kunci selektif untuk HSM terkelola

### <a name="netappfiles"></a>NetAppFiles

* [BREAKING CHANGE] az netappfiles pool update: Hapus service-level dari parameter.
* `az netappfiles pool update`: Tambahkan parameter opsional tipe qos.
* `az netappfiles pool create`: Tambahkan parameter opsional tipe qos.
* `az netappfiles volume replication suspend`: Tambahkan replikasi force-break sebagai parameter opsional.
* Tambahkan replikasi volume az netappfiles menginisialisasi ulang: Perintah baru ditambahkan untuk menginisialisasi ulang replikasi.
* Add az netappfiles volume pool-change: Perintah baru untuk mengubah kumpulan volume.
* Menambahkan kebijakan snapshot az netappfiles: Grup perintah baru dengan perintah daftar, hapus, perbarui, tampilkan, buat, dan volume.
* Menambahkan cadangan akun az netappfiles: Grup perintah baru dengan perintah tampilkan, daftar, dan hapus
* Menambahkan cadangan volume az netappfiles: Grup perintah baru dengan tampilkan, daftar, hapus, perbarui, dan buat perintah.
* Menambahkan kebijakan pencadangan akun az netappfiles: Grup perintah baru dengan perintah perlihatkan, daftar, hapus, perbarui, dan hapus.
* Tambahkan az netappfiles vault list: Perintah baru ditambahkan.
* `az netappfiles account ad add`: Tambahkan parameter opsional kdc-ip, nama iklan, server-root-ca-certificate dan backup-operator
* `az netappfiles volumes create`: Tambahkan parameter opsional snapshot-policy-id, backup-policy-id, backup-enabled, backup-id, policy-enforced, vault-id, kerberos-enabled, throughput-mibps, snapshot-directory-visible, security-style, kerberos5-read-only, kerberos5-read-write, kerberos5i-read-only, kerberos5i-read-write, kerberos5p-read-only, kerberos5p-read-write dan has-root-access.
* `az netappfiles volume update`: Tambahkan parameter opsional vault-id, backup-enabled, backup-policy-id, policy-enforced dan throughput-mibps

### <a name="network"></a>Jaringan

* Memperbaiki bug yang tidak dapat membuat gateway aplikasi Standard_v2 tanpa alamat IP statis pribadi
* `az network dns zone import`: Raise FileOperationError bukan FileNotFoundError jika file zona tidak ada
* Memperbaiki error NoneType crash saat menghapus sumber daya yang tidak ada di ApplicationGateway, LoadBalancer, Nic

### <a name="private-dns"></a>DNS Privat

* `az network private-dns zone import`: Raise FileOperationError bukan FileNotFoundError jika file zona tidak ada

### <a name="profile"></a>Profil

* `az login`: Tambahkan kembali peringatan bahwa browser dibuka

### <a name="role"></a>Peran

* `az role assignment create`: Buat `--description`, `--condition`pratinjau `--condition-version`

### <a name="security"></a>Keamanan

* `az security pricing`: Perbarui bantuan untuk mencerminkan versi API saat ini yang dipanggil

### <a name="storage"></a>Penyimpanan

* Perbaiki #15600: az storage fs ada: jika fs tidak ada ResourceNotFoundError dikembalikan
* Memperbaiki #15706: Contoh untuk membuat kontainer penyimpanan tidak benar
* `az storage blob delete-batch`: Kesalahan ketik yang benar dalam dokumentasi.

## <a name="november-09-2020"></a>09 November 2020 pukul

Versi 2.14.2

### <a name="app-service"></a>App Service

* Perbaiki #15604, #15605: Tambahkan dukungan Dotnet5

## <a name="november-06-2020"></a>06 November 2020

Versi 2.14.1

### <a name="arm"></a>ARM

* Hotfix: Tambahkan dukungan string multiline TS untuk input template

## <a name="october-27-2020"></a>27 Oktober 2020

Versi 2.14.0

### <a name="aks"></a>AKS

* Menambahkan dukungan PPG
* Memperbarui batas waktu penyeimbang beban standar maks hingga 100 menit

### <a name="apim"></a>APIM

* Memperbaiki masalah dengan membuat instans tingkat konsumsi

### <a name="app-config"></a>Konfigurasi Aplikasi

* Memperbaiki kueri nilai kunci menurut label yang dipisahkan koma

### <a name="app-service"></a>App Service

* Bugfix: az webapp up gagal ketika pengguna tidak memiliki izin menulis ke direktori induk proyek
* Memperbaiki # 13777: Perbaiki untuk menghapus jemusan dari XML
* Perbaiki #15441: az webapp create-remote-connection gagal dengan AttributeError: objek 'Thread' tidak memiliki atribut 'isAlive'
* [BREAKING CHANGE] az webapp up: add optional params (os & runtime) dan runtime yang diperbarui

### <a name="arm"></a>ARM

* Membuat perintah What-If penyebaran templat GA
* [MELANGGAR PERUBAHAN] Menambahkan konfirmasi pengguna untuk az ts create
* Memperbaiki data yang dikembalikan saat menandai beberapa sumber daya

### <a name="backup"></a>Cadangan

* `az backup policy create`: Tambahkan dukungan untuk pembuatan kebijakan pencadangan IaaSVM dari CLI
* Meningkatkan batas perlindungan VM dari 100 hingga 1000

### <a name="compute"></a>Compute

* sig image-definition create: add --features
* Versi API baru dari gallery_images 2020-09-30
* `az vm update / az sig image-version update`: Mendukung pembaruan vm/image-version bahkan menggunakan gambar penyewa silang
* Menghapus validasi SKU host vm

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb create/update`: Meningkatkan pesan kesalahan dari input --lokasi yang salah
* `az cosmosdb sql container create/update`: Tambahkan parameter --analytical-storage-ttl

### <a name="hdinsight"></a>HDInsight

* [BREAKING CHANGE] az hdinsight create: hapus dua parameter: --public-network-access-type dan --outbound-public-network-access-type

### <a name="iot-central"></a>IoT Pusat

* Menghapus peringatan pratinjau karena sudah GAed

### <a name="key-vault"></a>Key Vault

* Membatalkan `--enable-soft-delete false` saat membuat atau memperbarui kubah
* Membuat `--bypass` dan `--default-action` bekerja sama dengan parameter acl jaringan saat membuat kubah

### <a name="misc"></a>Misc.

* Menambahkan bash-completion ke Dockerfile

### <a name="rdbms"></a>RDBMS

* Tambahkan Perintah Daftar-SKUS, Transformer Tabel, Konteks Lokal untuk Postgres, MySQL, Mariadb Single Server
* [MELANGGAR PERUBAHAN] Pembaruan nama parameter. Peningkatan Bidang Manajemen untuk MySQL dan PostgreSQL
* `az postgres|mariadb|mysql server create` : Perbarui buat pengalaman untuk Postgres, MySQL dan MariaDB - bidang baru dalam output , Perkenalkan nilai baru untuk `--public` parameter dalam perintah buat (semua,\<IP\>,\<IPRange\>0.0.0.0)0)

### <a name="signalr"></a>SignalR

* `az signalr create`: Tambahkan opsi `--enable-messaging-logs` baru untuk mengontrol layanan menghasilkan log perpesanan atau tidak
* `az signalr update`: Tambahkan opsi `--enable-messaging-logs` baru untuk mengontrol layanan menghasilkan log perpesanan atau tidak

### <a name="sql"></a>SQL

* [MELANGGAR PERUBAHAN] Memperbaiki respons untuk nama dan nilai param redundansi penyimpanan cadangan untuk MI
* `az sql db audit-policy show`: memperluas untuk menampilkan kebijakan audit database termasuk data LA dan EH
* `az sql db audit-policy update`: memperluas untuk memungkinkan pembaruan LA dan EH bersama dengan kebijakan audit database
* `az sql db audit-policy wait`: tempatkan CLI dalam keadaan menunggu sampai kondisi kebijakan audit database terpenuhi.
* `az sql server audit-policy show`: memperluas untuk menampilkan kebijakan audit server termasuk data LA dan EH
* `az sql server audit-policy update`: memperluas untuk memungkinkan pembaruan LA dan EH bersama dengan kebijakan audit server
* `az sql server audit-policy wait`: tempatkan CLI dalam keadaan menunggu sampai kondisi kebijakan audit server terpenuhi.
* Tambahkan Dukungan khusus AAD untuk instans dan Server Terkelola SQL
* `az sql db replica create`: Tambahkan argumen --partner-database

### <a name="storage"></a>Penyimpanan

* Memperbaiki #15111: `az storage logging update` gagal tanpa argumen opsional
* Memperbaiki bug saat menggunakan perintah set-tier dengan login utama layanan
* Upgrade versi untuk file datalake ke 2020-02-10
* `az storage queue list`: Track2 didukung
* `az storage fs access`: Mendukung pengelolaan ACL secara rekursif

### <a name="synapse"></a>Synapse

* Tambahkan pipeline, layanan tertaut, pemicu, buku catatan, aliran data, dan cmdlet terkait dataset

## <a name="october-13-2020"></a>13 Oktober 2020

Versi 2.13.0

### <a name="acr"></a>ACR

* `az acr helm`: Perbarui url deprecation
* Menambahkan perubahan logtemplate dan systemtask untuk Tugas ACR

### <a name="aks"></a>AKS

* Mendukung virtual-node dengan aks create: `az aks create --enable-addons virtual-node`
* Menambahkan opsi hanya gambar node untuk CLI
* Harapkan addon kube-dashboard dinonaktifkan secara default
* `az aks create/update`: Tambahkan dukungan LicenseType untuk Windows
* Mendukung tambahkan kumpulan node Spot
* Nama addon kehormatan yang didefinisikan di Azure CLI

### <a name="ams"></a>AMS

* Memperbaiki #14687: Grup sumber daya campuran dan nama akun dalam perintah "az ams streaming-endpoint show"

### <a name="app-config"></a>Konfigurasi Aplikasi

* Memperbaiki bug pengujian
* Mendukung AAD auth untuk operasi data

### <a name="app-service"></a>App Service

* `az functionapp deployment source config-zip`: Memperbaiki masalah di mana config-zip dapat memberikan pengecualian pada keberhasilan pada konsumsi linux
* Bugfix: Pesan kesalahan yang lebih baik untuk perintah webapp
* `az appservice domain create, show-terms`: Tambahkan kemampuan untuk membuat domain layanan aplikasi
* `az functionapp create`: Menghapus bendera pratinjau dari Java 11 saat membuat aplikasi fungsi baru
* [BREAKING CHANGE] az webapp create, az webapp up - Update available webapp runtimes

### <a name="arm"></a>ARM

* `az ts`: Tambahkan perintah baru untuk spesifikasi template
* `az deployment` : Tambahkan dukungan untuk --template-spec -s

### <a name="compute"></a>Compute

* Memperbaiki batasan jumlah FD pembuatan grup host
* Menambahkan perintah baru untuk mendukung pemutakhiran ekstensi untuk VMSS
* Memperbaiki referensi gambar adalah masalah yang hilang

### <a name="hdinsight"></a>HDInsight

* `az hdinsight create`: tambahkan informasi terdeprekasi untuk argumen --public-networrk-access-type dan --outbound-public-network-access-type
* `az hdinsight create`: tambahkan informasi terdepresiasi untuk argumen `--public-networrk-access-type` dan `--outbound-public-network-access-type`
* `az hdinsight create`: tambahkan parameter `--idbroker` untuk mendukung pelanggan untuk membuat klaster ESP dengan HDInsight Id Broker

### <a name="iot-central"></a>IoT Pusat

* Hapus modul perintah 'az iotcentral' yang tidak digunakan lagi

### <a name="key-vault"></a>Key Vault

* Dukungan `--hsm-name` untuk `az keyvault key encrypt/decrypt`

### <a name="lab"></a>Laboratorium

* Perbaiki # 14127: `__init__()` mengambil 1 argumen posisi tetapi 2 diberikan

### <a name="network"></a>Jaringan

* `az network application-gateway ssl-cert show`: Tambahkan contoh untuk menunjukkan format sertifikat dan mengambil informasi
* `az network application-gateway rule`: Opsi Dukungan --prioritas
* `az network application-gateway create`: Perbaiki bug yang tidak dapat dibuat tanpa sepcified IP publik
* `az network application-gateway waf-policy managed-rule rule-set add`: Mengekspos kesalahan server kepada pengguna untuk memberikan pesan petunjuk yang lebih intuitif.
* `az network application-gateway waf-policy managed-rule rule-set update`: Dukungan untuk mengubah versi jenis kumpulan aturan.

### <a name="rdbms"></a>RDBMS

* Bugfix: az postgres flexible-server create Remove hardcoded API version from network client.

### <a name="role"></a>Peran

* Memperbaiki #15278: `az role assignment list/delete`: Melarang argumen string kosong

### <a name="sql"></a>SQL

* `az sql midb log-replay`: Dukungan untuk layanan replay log pada database terkelola
* Abaikan casing karakter untuk nilai param redundansi penyimpanan cadangan untuk instans terkelola
* [BREAKING CHANGE] az sql db create: Add --backup-storage-redundancy parameter; tambahkan peringatan untuk bsr/bsr == Geo yang tidak ditentukan.

### <a name="sql-vm"></a>SQL VM

* `az sql vm show`: Tambahkan opsi konfigurasi ke --expand flag

### <a name="storage"></a>Penyimpanan

* [BREAKING CHANGE] `az storage blob copy start`: Memperbaiki masalah format untuk `--destination-if-modified-since` dan `--destination-if-unmodified-since`
* [BREAKING CHANGE] `az storage blob incremental-copy start`: Memperbaiki masalah format untuk `--destination-if-modified-since` dan `--destination-if-unmodified-since`
* `az storage fs`: Memperbaiki masalah string koneksi
* `az storage share-rm`: Tingkat akses rilis GA
* `az storage container-rm`: Tambahkan grup perintah baru untuk menggunakan Microsoft. Storage penyedia sumber daya untuk operasi manajemen kontainer.

## <a name="september-29-2020"></a>29 September 2020 pukul

Versi 2.12.1

### <a name="rdbms"></a>RDBMS

* Hotfix: `az postgres flexible-server create` : Perbarui VnetName untuk mengecualikan nama server dan memperbarui wilayah default untuk MySQL

## <a name="september-22-2020"></a>September 22, 2020

Versi 2.12.0

### <a name="acr"></a>ACR

* Perbaiki #14811 Tambahkan dukungan untuk penimpaan dockerignore

### <a name="aks"></a>AKS

* CLI harus mentolerir kubeconfig kosong
* MEMPERBAIKI #12871: az aks enable-addons: Contoh bantuan autogenerated salah untuk opsi vitual-node
* Menghapus tindakan konektor aci lama
* Support azure policy addon in azure-cli
* Memperbaiki masalah sensitif kasus untuk addon dasbor AKS
* Perbarui mgmt-containerservice ke 9.4.0 dan aktifkan API 09-01

### <a name="apim"></a>APIM

* Mendukung produk / productapi / namedValue perintah entitas && bump sdk versi

### <a name="app-config"></a>Konfigurasi Aplikasi

* Mendukung mengaktifkan/menonaktifkan PublicNetworkAccess untuk toko yang ada

### <a name="app-service"></a>App Service

* Tambahkan dukungan untuk tingkat harga V3 Premium
* Perbaiki #12653: az webapp log config --application-logging false tidak mematikannya
* Perbaiki #14684: penghapusan pembatasan akses melalui alamat IP tidak berfungsi; #13837-az webapp create - Contoh untuk RSgroup yang berbeda untuk Paket dan WebApp
* functionapp: Tambahkan dukungan untuk penangan kustom. Powershell yang tidak digunakan lagi 6.2.
* functionapp: Memperbaiki masalah di mana pengaturan aplikasi salah diatur untuk gambar kustom linux

### <a name="arm"></a>ARM

* `az deployment group/sub/mg/tenant what-if`: Tampilkan perubahan sumber daya "Abaikan" terakhir

### <a name="compute"></a>Compute

* Menambahkan license_type baru di vm create/update: RHEL_BYOS, SLES_BYOS
* Tingkatkan versi API disk ke 2020-06-30
* pembuatan disk: tambahkan --logical-sector-size, --tier
* pembaruan disk: Dukungan --disk-iops-read-only, --disk-mbps-read-only, --max-shares
* Perintah baru disk-enkripsi-set list-associated-resources
* vm boot-diagnostics enable: --storage menjadi opsional
* Perintah baru: vm boot-diagnostics get-boot-log-uris
* vm boot-diagnostics get-boot-log: mendukung penyimpanan terkelola

### <a name="config"></a>Konfigurasi

* Ganti nama local-context menjadi config param-persist

### <a name="cosmos-db"></a>Cosmos DB

* Dukungan untuk API Migrasi untuk sumber daya Throughput untuk fitur Skala Otomatis di CosmosDB

### <a name="eventhub"></a>Eventhub

Menambahkan perintah Cluster dan parameter trusted_service_access_enabled untuk Networkruleset

### <a name="extension"></a>Ekstensi

* `az extension add`: Tambahkan `--upgrade` opsi untuk memperbarui ekstensi jika sudah diinstal
* Mengaktifkan penginstalan dinamis secara default

### <a name="iot"></a>IoT

* Versi TLS minimum yang diaktifkan di IoT Hub Create

### <a name="iot-central"></a>IoT Pusat

* Operasi penghapusan aplikasi sekarang sudah lama beroperasi

### <a name="iot-hub"></a>Iot Hub

* Perintah 'show-connection-string' yang tidak digunakan lagi

### <a name="key-vault"></a>Key Vault

* Pratinjau publik HSM terkelola
* Memperbaiki masalah yang `--maxresults` tidak berlaku saat mencantumkan sumber daya atau versi sumber daya

### <a name="kusto"></a>Kusto

* Menambahkan pesan yang tidak digunakan lagi

### <a name="monitor"></a>Monitor

* `az monitor log-analytics workspace linked-storage`: mengekspos pesan kesalahan terperinci kepada pelanggan

### <a name="network"></a>Jaringan

* `az network vnet subnet`: Mendukung --disable-private-endpoint-network-policies dan --disable-private-link-service-network-policies
* Memperbaiki bug saat memperbarui flow-log saat subproperty network_watcher_flow_analytics_configuration tidak ada
* Versi API menabrak 2020-06-01
* Mendukung --tcp-port-behavior saat mengonfigurasi konfigurasi TCP dari Connection Monitor V2
* Mendukung lebih banyak jenis dan tingkat cakupan saat membuat Endpoint of Connection Monitor V2
* Mendukung --host-subnet untuk membuat VirtualHub di bawahnya sebagai VirtualRouter

### <a name="rdbms"></a>RDBMS

* Pembaruan Management Plane untuk PostgreSQL dan MySQL

### <a name="role"></a>Peran

* `az role assignment create/update`: Dukungan `--description`, `--condition` dan `--condition-version`
* `az ad app permission delete`: Dukungan `--api-permissions` untuk menghapus spesifik `ResourceAccess`

### <a name="service-fabric"></a>Service Fabric

* Menambahkan perintah tipe klaster dan node terkelola

### <a name="sql"></a>SQL

* Upgrade azure-mgmt-sql to 0.20.0
* Menambahkan parameter opsional redundansi penyimpanan cadangan ke MI membuat cmdlet

### <a name="storage"></a>Penyimpanan

* `az storage share-rm stats`: Dapatkan byte penggunaan data yang disimpan di berbagi.
* Ga rilis penyimpanan blob PITR
* `az storage blob query`: Mendukung Akselerasi Kueri Azure Storage
* Mendukung Soft Delete untuk berbagi file
* `az storage copy`: Tambahkan dukungan kredensial akun dan deprecate `--source-local-path`, `--destination-local-path`, , `--destination-account-name`
* `az storage account blob-service-properties update`: Tambahkan dukungan kebijakan retensi penghapusan kontainer

### <a name="synapse"></a>Synapse

* Memperbaiki kesalahan ketik dalam contoh penetapan peran az synapse membuat dan menghapus

## <a name="august-28-2020"></a>28 Agustus 2020

Versi 2.11.1

### <a name="acr"></a>ACR

* Tambahkan Tingkat Terisolasi ke Kumpulan Agen
* Menambahkan Konteks Sumber Artefak OCI

### <a name="aks"></a>AKS

* Memperbaiki masalah pembuatan klaster aks

### <a name="cognitive-services"></a>Cognitive Services

* [MELANGGAR PERUBAHAN] Tampilkan istilah hukum tambahan untuk API tertentu

### <a name="network"></a>Jaringan

* [MELANGGAR PERUBAHAN] Memungkinkan untuk membuat IP publik dan pribadi saat membuat Gateway Aplikasi
* `az network list-service-tags`: menambahkan detail tentang penggunaan parameter lokasi ke pesan bantuan

### <a name="storage"></a>Penyimpanan

* `az storage blob list`: Mendukung properti OR dengan versi api baru

## <a name="august-25-2020"></a>25 Agustus 2020

Versi 2.11.0

### <a name="aks"></a>AKS

* Menghapus tag pratinjau dari add-on Virtual Node
* Menambahkan argumen CMK AKS dalam pembuatan klaster
* Atur profil jaringan saat menggunakan penyeimbang beban dasar.
* Menghapus validasi pod maks dari CLI dan biarkan pra-penerbangan menanganinya
* Memperbaiki add-on yang tersedia dalam pesan bantuan di `az aks create`
* Membawa dukungan untuk profil autoscaler klaster di CLI inti

### <a name="appservice"></a>AppService

* `az webapp`: Menambahkan perintah contoh daftar
* `az webapp ssh`: Tambahkan parameter --instance untuk menyambungkan ke instans tertentu
* `az webapp create-remote-connection`: Tambahkan parameter --instance untuk menyambungkan ke instans tertentu
* Perbaiki #14758: az webapp membuat kesalahan saat membuat aplikasi windows dengan --runtime dotnetcore
* Memperbaiki #14701: Menerapkan functionapp create --assign-identity
* Memperbaiki #11244: `az webapp auth update`: Tambahkan parameter opsional untuk memperbarui client-secret-certificate-thumbprint
* `az functionapp keys`: Perintah tambahan yang memungkinkan pengguna mengelola kunci aplikasi fungsi mereka
* `az functionapp function`: Menambahkan perintah yang memungkinkan pengguna untuk mengelola fungsi masing-masing
* `az functionapp function keys`: Menambahkan perintah yang memungkinkan pengguna untuk mengelola tombol fungsi mereka
* Perbaiki #14788: az webapp membuat tidak mendapatkan webapp yang benar saat nama substring
* `az functionapp create`: Kemampuan yang dihapus untuk membuat Fungsi 2.x di wilayah yang tidak mendukungnya

### <a name="arm"></a>ARM

* `az resource list`: Memperluas data `createdTime`pengembalian, `changedTime` dan `provisioningState`
* `az resource`: Tambahkan parameter `--latest-include-preview` untuk mendukung menggunakan versi api terbaru apakah versi ini pratinjau

### <a name="aro"></a>ARO

* Penyempurnaan CLI, termasuk izin pemeriksaan tabel rute

### <a name="cloud"></a>Cloud

* `az cloud register`: Memperbaiki awan pendaftaran dengan file konfigurasi

### <a name="compute"></a>Compute

* Perbarui SKU VM yang mendukung jaringan yang dipercepat
* `az vm create`: Patching in-guest otomatis
* `az image builder create`: Tambahkan --vm-size, --os-disk-size, --vnet, --subnet
* New command az vm assess-patches

### <a name="container"></a>Kontainer

* Memperbaiki #6235: Memperbarui teks bantuan untuk parameter port dalam membuat kontainer

### <a name="datalake-store"></a>Toko Datalake

* Memperbaiki masalah #14545 untuk operasi gabungan danau data

### <a name="eventhub"></a>EventHub

* `az eventhubs eventhub create/update`: Ubah dokumentasi destination_name

### <a name="extension"></a>Ekstensi

* Menambahkan `az extension list-versions` perintah untuk mencantumkan semua versi ekstensi yang tersedia

### <a name="hdinsight"></a>HDInsight

* Mendukung pembuatan klaster dengan konfigurasi skala otomatis dan Dukungan mengelola konfigurasi skala otomatis
* Mendukung pembuatan klaster dengan enkripsi di host

### <a name="iotcentral"></a>IoTCentral

* Peningkatan dokumentasi CLI

### <a name="monitor"></a>Monitor

* `az monitor metrics alert create`: mendukung RG dan Sub sebagai nilai lingkup

### <a name="netappfiles"></a>NetAppFiles

* [BREAKING CHANGE] az netappfiles snapshot create: Menghapus file-system-id dari parameter
* [BREAKING CHANGE] az netappfiles snapshot show: Snapshot tidak lagi memiliki parameter file-system-id
* `az netappfiles account`: Model ActiveDirectory memiliki parameter baru backup_operators
* `az netappfiles volume show`: Model dataProtection memiliki snapshot parameter baru
* `az netappfiles volume show`: Volume Model memiliki parameter baru snapshot_directory_visible

### <a name="network"></a>Jaringan

* `az network dns export`: ekspor FQDN untuk tipe MX, PTR, NS dan SRV alih-alih jalur relatif
* Mendukung tautan pribadi untuk disk terkelola
* `az network application-gateway auth-cert show`: Tambahkan contoh untuk mendemonstrasikan format sertifikat
* `az network private-endpoint-connection`: mendukung konfigurasi aplikasi

### <a name="rbac"></a>RBAC

* `az ad group create`: dukungan menentukan deskripsi saat membuat grup
* `az role definition create`: cetak pesan yang dapat dibaca manusia alih-alih pengecualian saat assignableScope adalah array kosong
* [BREAKING CHANGE] `az ad sp create-for-rbac`: mengubah izin default sertifikat yang dibuat

### <a name="sql"></a>SQL

* `az sql server audit-policy`: Tambahkan dukungan audit sql server

### <a name="storage"></a>Penyimpanan

* `az storage blob copy start-batch`: Perbaiki #6018 untuk --source-sas
* `az storage account or-policy`: Mendukung kebijakan replikasi objek akun penyimpanan
* Memperbaiki masalah #14083 untuk meningkatkan versi paket penyimpanan azure-multiapi untuk masalah paket dan dukungan versi api baru
* `az storage blob generate-sas`: tambahkan contoh untuk --ip dan perbaiki pesan kesalahan
* `az storage blob list`: Memperbaiki masalah next_marker

### <a name="synapse"></a>Synapse

* Tambahkan ruang kerja, sparkpool, cmdlet terkait sqlpool
* Menambahkan perintah releated pekerjaan spark berdasarkan sdk track2
* Menambahkan perintah terkait fitur accesscontrol berdasarkan sdk track2

### <a name="upgrade"></a>Mutakhirkan

* Menambahkan `az upgrade` perintah untuk meningkatkan azure cli dan extensions

## <a name="august-11-2020"></a>11 Agustus 2020

Versi 2.10.1

### <a name="app-service"></a>App Service

* Memperbaiki # 9887 webapp dan functionapp, mendukung menetapkan / menghapus identitas terkelola pengguna
* Memperbaiki #1382, #14055: Memperbarui pesan kesalahan untuk az webapp create dan az webapp config container set
* `az webapp up`: Perbaiki logika pemilihan ASP default saat parameter --plan tidak disediakan

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Mendukung mengaktifkan/menonaktifkan PublicNetworkAccess selama pembuatan toko

### <a name="compute"></a>Compute

* Mendukung mengaitkan disk dan snapshot dengan sumber daya akses disk

### <a name="lab"></a>Laboratorium

* Memperbaiki masalah bug validasi tanggal #7904 dalam pembuatan vm lab

### <a name="storage"></a>Penyimpanan

* `az storage blob upload-batch`: Perbaiki masalah #14660 dengan argumen yang tidakposisi

## <a name="august-04-2020"></a>04 Agustus 2020

Versi 2.10.0

### <a name="aks"></a>AKS

* `az aks update`: Ubah argumen --enable-aad untuk memigrasikan klaster non-AAD berkemampuan RBAC ke klaster AAD yang dikelola AKS
* `az aks install-cli`: Tambahkan --kubelogin-version dan --kubelogin-install-location arguments untuk menginstal kubelogin
* Add az aks nodepool get-upgrades command

### <a name="ams"></a>AMS

* Fix #14021: az ams account sp is not idempotent

### <a name="apim"></a>APIM

* apim api import: mendukung impor API dan mengganggu perintah cli tingkat api lainnya

### <a name="app-service"></a>App Service

* Memperbaiki #13035: Tambahkan validasi untuk pembatasan akses konfigurasi webapp az untuk menghindari penambahan duplikat

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Default ke sku standar jika tidak ditentukan
* [MELANGGAR PERUBAHAN] Pengaturan dukungan dengan tipe konten JSON

### <a name="arm"></a>ARM

* `az resource tag`: Perbaiki bug penandaan Aplikasi terkelola dan beberapa masalah pengujian terkait
* `az deployment mg/tenant what-if`: Tambahkan dukungan ke grup manajemen dan What-If penerapan tingkat penyewa
* `az deployment mg/tenant create`: Tambahkan parameter --confirm-with-what-if/-c.
* `az deployment mg/tenant create`: Tambahkan parameter --what-if-result-format/-r.
* `az deployment mg/tenant create`: Tambahkan parameter --what-if-exclude-change-types/-x.
* `az tag`: az tag support for resource id parameter

### <a name="backup"></a>Cadangan

* Memicu penemuan kontainer/item AFS hanya jika diperlukan

### <a name="cdn"></a>CDN

* Menambahkan bidang tautan pribadi ke asal

### <a name="compute"></a>Compute

* `az vm/vmss create`: Pilih nama pengguna yang valid untuk pengguna jika nama pengguna default tidak valid
* `az vm update`: mendukung gambar penyewa silang
* `az disk-access`: Tambahkan grup perintah baru untuk mengoperasikan sumber daya akses disk
* Mendukung penempatan otomatis grup host khusus
* Mendukung ppg dan spg dalam mode orkestrasi VMSS

### <a name="config"></a>Konfigurasi

* `az config`: Tambahkan modul perintah baru `config`

### <a name="extension"></a>Ekstensi

* Mendukung secara otomatis menginstal ekstensi jika ekstensi perintah tidak diinstal

### <a name="hdinsight"></a>HDInsight

* Tambahkan 3 parameter ke perintah `az hdinsight create` untuk mendukung tautan pribadi dan enkripsi dalam fitur transit:

### <a name="iot-hub"></a>Iot Hub

* Perbaiki #7792: IoT Hub Create bukan idempotent

### <a name="iot-central"></a>IoT Pusat

* Tambahkan daftar opsi paramater untuk iot central

### <a name="keyvault"></a>Az.KeyVault

* `az keyvault key encrypt/decrypt`: menambahkan parameter `--data-type` untuk secara eksplisit menentukan jenis data asli

### <a name="monitor"></a>Monitor

* `az monitor log-analytics workspace data-export`: mendukung namespace hub acara sebagai tujuan.
* `az monitor autoscale`: mendukung namespace dan dimensi untuk --condition

### <a name="netappfiles"></a>NetAppFiles

* `az volume revert`: Tambahkan Volume Kembali untuk mengembalikan volume ke salah satu snapshotnya.
* [MELANGGAR PERUBAHAN] Hapus `az netappfiles mount-target`.
* `az volume show`: Menambahkan situs ke Properti Direktori Aktif

### <a name="network"></a>Jaringan

* `az application-gateway private-link add`: dukungan untuk menentukan subnet yang ada berdasarkan ID
* `az network application-gateway waf-policy create`: mendukung versi dan jenis

### <a name="storage"></a>Penyimpanan

* Memperbaiki #10302: Mendukung menebak tipe konten saat menyinkronkan file
* `az storage blob lease`: Terapkan versi api baru untuk operasi sewa blob
* `az storage fs access`: Mendukung kredensial AAD dalam mengelola kontrol akses untuk akun ADLS Gen2
* `az storage share-rm create/update`: tambahkan --access-tier untuk mendukung tingkat akses

## <a name="july-16-2020"></a>16 Juli 2020

Versi 2.9.1

### <a name="aks"></a>AKS

* Menghapus pengaturan eksplisit VMSS dalam perintah contoh Windows karena sekarang default

### <a name="iot"></a>IoT

* [BREAKING CHANGE] `az iot pnp`: Hapus perintah pratinjau IoT PNP dari CLI inti

### <a name="rest"></a>REST

* Memperbaiki #14152: `az rest`: Terima URL ARM tanpa ID langganan

### <a name="storage"></a>Penyimpanan

* Memperbaiki #14138: Jadikan beberapa izin opsional

## <a name="july-14-2020"></a>14 Juli 2020

Versi 2.9.0

### <a name="acr"></a>ACR

* Menangani tautan artefak log dari Registry ke log streaming
* Deprecate helm2 perintah

### <a name="aks"></a>AKS

* `az aks create`: tambahkan argumen --enable-aad
* `az aks update`: tambahkan argumen --enable-aad

### <a name="apim"></a>APIM

* Added general az apim api commands

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan contoh untuk menggunakan --fields dalam revisi konfigurasi aplikasi

### <a name="appservice"></a>AppService

* `az functionapp create`: Menambahkan dukungan untuk Java 11 dan Powershell 7. Menambahkan Dukungan API Tumpukan.
* Memperbaiki pembuatan aplikasi multi-kontainer #14208 gagal
* Fix az webapp create - use hardcoded runtime stacks

### <a name="arm"></a>ARM

* `az resource tag`: Memperbaiki masalah penandaan sumber daya dengan jenis sumber daya `Microsoft.ContainerInstance/containerGroups`

### <a name="compute"></a>Compute

* Cakram versi benjolan 2020-05-01, menghitung 2020-06-01
* Enkripsi ganda dari set enkripsi disk
* `az vmss update`: dukungan menentukan gambar penyewa silang.
* `az sig image-version create`: dukungan menentukan gambar penyewa silang.
* vm/vmss create: Enkripsi cache & data-in-transit untuk disk OS/Data dan temp disk untuk VM & VMSS
* Menambahkan operasi simulasi penggusuran untuk VM dan VMSS

### <a name="cosmosdb"></a>CosmosDB

* Fitur terbaru: Autoscale, IpRules, EnableFreeTier dan EnableAnalyticalStorage

### <a name="eventgrid"></a>EventGrid

* Tambahkan dukungan CLI untuk pratinjau 2020-04-01 dan tandai fitur pratinjau dengan is_Preview=True

### <a name="find"></a>Cari

* Perbaiki #14094 az menemukan Perbaiki Kueri gagal saat tidak masuk dan saat telemetri dinonaktifkan

### <a name="hdinsight"></a>HDInsight

* Tambahkan dua perintah untuk mendukung fitur reboot node hdinsight

### <a name="monitor"></a>Monitor

* Menghapus bendera pratinjau untuk perintah di bawah ruang kerja Analitik Log
* `az monitor diagnostic-settings subscription`: Mendukung pengaturan diagnositc untuk berlangganan
* `az monitor metrics`: mendukung ',' dan '|' dalam nama metrik
* `az monitor log-analytics workspace data-export`: mendukung ekspor data analitik log

### <a name="network"></a>Jaringan

* `az network application-gateway frontend-ip update`: Mencela parameter --public-ip-address
* Bump azure-mgmt-network to 11.0.0
* `az network express-route gateway connection`: mendukung konfigurasi perutean
* `az network virtual-appliance`: Mendukung alat virtual jaringan Azure.
* Application Gateway mendukung fitur tautan pribadi

### <a name="policyinsights"></a>KebijakanInsights

* `az policy state`: tambahkan perintah pemindaian pemicu untuk memicu evaluasi kepatuhan kebijakan
* `az policy state list`: mengekspos versi entitas kebijakan di setiap catatan kepatuhan

### <a name="profile"></a>Profil

* `az account get-access-token`: Tampilkan kedaluwarsaOn untuk Identitas Terkelola

### <a name="rdbms"></a>RDBMS

* Mendukung versi TLS Minimum
* Tambahkan Enkripsi Infrastruktur untuk Azure Postgres dan MySQL

### <a name="security"></a>Keamanan

* Menambahkan perintah allowed_connections
* Menambahkan perintah pengerasan jaringan Adaptif
* Menambahkan perintah adaptive_application_controls
* Penambahan az security iot-solution/ iot-alerts/iot-recommendations/iot-analytics REST to Azure CLI
* Menambahkan CLI kepatuhan peraturan

### <a name="signalr"></a>SignalR

* Menambahkan fitur termasuk mengelola koneksi titik akhir pribadi, aturan jaringan, dan hulu

### <a name="sql"></a>SQL

* `az sql mi create`, `az sql mi update`: Tambahkan `--tags` parameter untuk mendukung penandaan sumber daya
* `az sql mi failover`: Dukungan failover dari titik primer atau sekunder

### <a name="storage"></a>Penyimpanan

* `az storage account create/update`: Tambahkan --allow-blob-public-access untuk mengizinkan atau melarang akses publik untuk gumpalan dan kontainer
* `az storage account create/update`: Tambahkan `--min-tls-version` ke pengaturan dukungan versi TLS minimum yang diizinkan pada permintaan ke penyimpanan.
* Menghapus kredensial token check-in
* Memperbaiki nama akun penyimpanan dalam contoh

### <a name="webapp"></a>Webapp

* Bugfix: az webapp log deployment show - mengembalikan log penyebaran alih-alih metadata log
* Bugfix: az webapp vnet-integration add - fix error handling if bad vnet name, support vnet resource ID

## <a name="june-23-2020"></a>23 Juni 2020

Versi 2.8.0

### <a name="acr"></a>ACR

* Menambahkan dukungan untuk menonaktifkan titik akhir wilayah / menonaktifkan perutean
* [MELANGGAR PERUBAHAN] `az acr login --expose-token` tidak menerima nama pengguna dan kata sandi

### <a name="acs"></a>ACS

* Menghapus klaster pribadi dan API pratinjau 2019-10-27

### <a name="aks"></a>AKS

* Dukungan --yes for az aks upgrade
* Kembalikan "ubah vm sku default ke Standard_D2s_v3 (#13541)"
* Tambahkan "az aks update --uptime-sla"
* Memperbaiki typo in az aks update command
* Ubah untuk mendukung kumpulan agen 0 node dan blokir skala manual untuk kumpulan berkemampuan CAS
* Memperbaiki kesalahan ketik di VirtualMachineScaleSets dan memperbarui referensi ke versi Kubernetes

### <a name="ams"></a>AMS

* UBAH teks bantuan untuk parameter "--kedaluwarsa".

### <a name="appservice"></a>AppService

* `az webapp log deployment show`: Tampilkan log penyebaran terbaru, atau log penyebaran penerapan tertentu jika deployment-id ditentukan
* `az webapp log deployment list`: Daftar log penyebaran yang tersedia
* Memperbaiki: Kesalahan permukaan saat nama webapp tidak valid disediakan
* Fix #13261 az webapp list-runtimes gunakan daftar statis sampai API Tumpukan Tersedia baru tersedia
* `az appservice ase create`: Perbaiki masalah buat #13361
* `az appservice ase list-addresses`: Perbaiki perubahan SDK #13140.
* Memperbaiki pembuatan webapp/slot untuk kontainer Windows
* `az webapp auth update`: Tambahkan parameter opsional untuk memperbarui versi runtime
* Mendukung daftar, menghapus, menyetujui, dan menolak koneksi titik akhir pribadi untuk webapp di CLI
* Memperbaiki #13888 : Tambahkan dukungan untuk WebApp Statis: dapatkan, daftar, buat perintah
* Pesan kesalahan yang ditingkatkan untuk Koneksi Terowongan SSH

### <a name="arm"></a>ARM

* `az tag`: Tambahkan contoh untuk -h
* `az deployment group/sub what-if`: Tambahkan parameter --exclude-change-types/-x.
* `az deployment group/sub/mg/tenant create`: Tambahkan parameter --what-if-exclude-change-types/-x.
* `az deployment group/sub/mg/tenant validate`: Tampilkan pesan kesalahan dalam format yang lebih baik.
* `az group export`: Tambahkan parameter `--skip-resource-name-params` baru dan `--skip-all-params` untuk mendukung parameterisasi skip
* Add az feature unregister api

### <a name="aro"></a>ARO

* Tambahkan Publik, Pribadi ke params untuk bantuan dengan visibilitas ingress/apiserver

### <a name="batch"></a>Batch

* `az batch account create`: Tambahkan parameter baru `--public-network-access`
* `az batch account create`: Tambahkan parameter baru `--identity-type`
* `az batch account set`: Tambahkan parameter baru `--identity-type`
* [BREAKING CHANGE] az batch pool create: Saat membuat kumpulan menggunakan gambar kustom, properti --image sekarang hanya dapat merujuk ke gambar Galeri Gambar Bersama.
* [BREAKING CHANGE] az batch pool create: Saat membuat kumpulan dengan opsi --json-file dan menentukan konfigurasi jaringan, properti publicIPs telah pindah ke properti baru publicIPAddressConfiguration. Properti baru ini juga mendukung properti ipAddressProvisioningType baru yang menentukan bagaimana kumpulan harus mengalokasikan IP dan properti PUBLICIPs yang memungkinkan konfigurasi daftar sumber daya PublicIP untuk digunakan dalam kasus ipAddressProvisioningType diatur ke UserManaged
* `az network private-link-resource`: Tambahkan dukungan untuk sumber daya Microsoft.Batch batchAccount
* `az network private-endpoint-connection`: Tambahkan dukungan untuk sumber daya Microsoft.Batch batchAccount

### <a name="cdn"></a>CDN

* `az cdn custom-domain enable-https`: Tambahkan dukungan BYOC.
* `az cdn custom-domain enable-https`: Perbaiki mengaktifkan HTTPS kustom dengan sertifikat terkelola CDN untuk SKU Standard_Verizon dan Standard_Microsoft.

### <a name="cognitive-services"></a>Cognitive Services

* [MELANGGAR PERUBAHAN] `az cognitiveservices account` sekarang memiliki struktur terpadu untuk semua perintah.
* `az cognitiveservices account identity`: Tambahkan manajemen identitas untuk Layanan Kognitif.

### <a name="compute"></a>Compute

* `az image builder`: Tingkatkan versi API ke 2020-02-14
* `az image builder create`: Tambahkan `--identity` ke konfigurasi identitas dukungan
* `az image builder customizer add`: Dukungan Windows penyesuai pembaruan
* Perintah baru `az image builder cancel`
* Tampilkan peringatan saat pengguna menerapkan VMSS yang disematkan ke versi gambar tertentu, bukan versi terbaru

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb`: Tambahkan perintah yang ada ke database dan grup kontainer
* Perbolehkan membuat koleksi tetap

### <a name="eventhub"></a>EventHub

* `az eventhubs namespace create` : Tambahkan parameter identitas terkelola

### <a name="extension"></a>Ekstensi

* Menambahkan --version ke dukungan untuk menginstal dari versi tertentu
* Aktifkan ekstensi CLI untuk menyertakan paket di namespace 'azure'

### <a name="iot-hub"></a>Iot Hub

* [BREAKING CHANGE] az iot hub job: Hapus perintah pekerjaan yang tidak digunakan lagi

### <a name="keyvault"></a>Az.KeyVault

* `az keyvault key import`: Mendukung impor dari string melalui dua parameter baru.
* Mendukung enkripsi string/byte dan dekripsi dengan kunci tersimpan

### <a name="monitor"></a>Monitor

* Mendukung tidak menunggu pembuatan klaster
* `az monitor log-analytics workspace saved-search`: Mendukung perintah baru untuk pencarian tersimpan

### <a name="network"></a>Jaringan

* `az network application-gateway address-pool update`: Perbaiki pesan bantuan dan tambahkan contoh.
* `az network vnet create`: Mendukung argumen --nsg
* `az network lb address-pool`: Dukungan buat kumpulan backend lb dengan alamat backend.
* `az network application-gateway address-pool`: Perbaiki untuk argumen --add

### <a name="rbac"></a>RBAC

* `az ad sp create-for-rabc`: Nama dukungan dengan spasi, garis miring dan garis miring belakang
* `az ad sp create-for-rbac`: Memperbaiki pesan kesalahan saat pengguna menentukan cakupan yang tidak valid

### <a name="security"></a>Keamanan

* Menambahkan perintah penilaian keamanan

### <a name="sql"></a>SQL

* `az sql db ltr-policy/ltr-backup`: memperbarui/menampilkan kebijakan retensi jangka panjang, menampilkan/menghapus pencadangan retensi jangka panjang, memulihkan pencadangan retensi jangka panjang

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah autentikasi untuk mendukung mendapatkan token untuk --subscription
* `az storage remove`Memperbaiki masalah # 13459 untuk meningkatkan pengecualian untuk kegagalan operasi
* Memperbaiki masalah #13012, #13632 dan #13657 untuk menghapus argumen yang tidak digunakan untuk perintah terkait generate-sas
* `az storage logging update`: Tambahkan cek untuk versi logging
* `az storage blob show`: Tambahkan lebih banyak properti untuk blob dengan sdk track 2
* Memperbaiki #13708: Memperbaiki pesan peringatan untuk kredensial
* `az storage share-rm create/update`: Tambahkan protokol NFS dan dukungan squash root
* `az storage account create`: Tambahkan dukungan untuk enkripsi ganda
* [BREAKING CHANGE] `az storage blob/container/file/share/table/queue generate-sas`: membuat --expiry dan --permissions diperlukan
* `az storage blob set-tier`: Bermigrasi ke Track 2 untuk mendukung penetapan prioritas rehidrasi

## <a name="june-02-2020"></a>02 Juni 2020

Versi 2.7.0

### <a name="acr"></a>ACR

* Memperbaiki kesalahan ketik dalam pesan kesalahan pembuatan token

### <a name="aks"></a>AKS

* Mengubah vm sku default menjadi Standard_D2s_v3
* Memperbaiki pembuatan penetapan peran untuk MSI clsuter plus subnet kustom

### <a name="appservice"></a>AppService

* Fix #12739 az appservice list-locations mengembalikan beberapa lokasi yang tidak valid

### <a name="arm"></a>ARM

* `az deployment`: Perbaiki masalah # 13159 dari pesan JSON yang salah setelah menghapus komentar dan mengompres
* `az resource tag`: Memperbaiki masalah #13255 sumber daya penandaan dengan jenis sumber daya `Microsoft.ContainerRegistry/registries/webhooks`
* Meningkatkan contoh untuk modul sumber daya

### <a name="aro"></a>ARO

* Ubah CLIError untuk memperbaiki bendera untuk --worker-vm-disk-size-gb

### <a name="eventhub"></a>EventHub

* Memperbaiki masalah #12406 Argument --capture-interval tidak memperbarui "intervalInSeconds"

### <a name="hdinsight"></a>HDInsight

* Ubah get_json_object menjadi shell_safe_json_parse

### <a name="monitor"></a>Monitor

* `az monitor metrics alert`: memperbaiki beberapa pesan bantuan
* `az monitor diagnostic-settings create`: mendukung argumen --export-to-resource-specific
* Mendukung ruang kerja LA pulih

### <a name="network"></a>Jaringan

* `az network dns zone`: dukungan - karakter
* `az network vpn-connection ipsec-policy`: ubah --sa-lifetime dan --sa-max-size ke nilai yang lebih besar misalnya
* Jaringan Bump ke 2020-04-01
* `az network private-endpoint-connection`: kisi acara dukungan
* `az network express-route list-route-tables`: memperbaiki bug yang tidak dapat mencantumkan rute sebagai tabel

### <a name="packaging"></a>Pengemasan

* Tambahkan Paket Fokus Ubuntu

### <a name="rbac"></a>RBAC

* `az ad sp credential reset`: memodifikasi pembuatan kredensial untuk menghindari karakter khusus yang merepotkan

### <a name="redis"></a>Redis

* Memperbaiki #13529: Ubah dokumentasi parameter enable_non_ssl_port

### <a name="storage"></a>Penyimpanan

* `az storage copy`: Tambahkan parameter `--follow-symlinks` untuk mendukung symlink
* Mengaktifkan konteks lokal untuk akun penyimpanan
* `az storage logging`: Memperbaiki masalah #11969 untuk memperbaiki pesan kesalahan

## <a name="may-19-2020"></a>19 Mei 2020

Versi 2.6.0

### <a name="acr"></a>ACR

* Menambahkan batas waktu default 5 menit untuk setiap permintaan ke ACR
* Dukungan menonaktifkan akses jaringan publik
* `az acr token create`: mengekspos argumen --hari
* `az acr import`: menerima nilai argumen --source yang berisi login dalam nama server melalui koreksi akhir klien

### <a name="acs"></a>ACS

* Perbaikan bug: hapus pembersihan bidang untuk bidang yang sudah tidak ada lagi

### <a name="aks"></a>AKS

* Memperbarui konteks bantuan perintah uptime-sla
* Menghapus pemeriksaan rentang untuk memperbarui jumlah minimum untuk skala otomatis
* Perbaiki cli itu tidak gagal saat pengguna hanya menentukan kata sandi Windows

### <a name="ams"></a>AMS

* `az ams transform create`: Tambahkan kemampuan untuk membuat transformasi dengan preset FaceDetector
* `az ams content-key-policy create` : Tambahkan kemampuan untuk membuat kebijakan kunci konten FairPlay dengan konfigurasi sewa offline

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Perbaikan bug untuk nilai kunci daftar dengan bidang

### <a name="appservice"></a>AppService

* `az functionapp create`: AzureWebJobsDashboard hanya akan diatur jika AppInsights dinonaktifkan
* Perbaiki #10664- Integrasi VNet - Masalah Pemeriksaan Lokasi & memperbaiki #13257- az webapp hingga gagal ketika RG perlu dibuat
* `az webapp|functionapp config ssl import`: Cari vault kunci di seluruh grup sumber daya dalam langganan dan tingkatkan bantuan dan contoh.
* Konteks lokal onboard untuk layanan aplikasi

### <a name="arm"></a>ARM

* `az deployment`: Memperbaiki masalah bahwa templateLink tidak akan dikembalikan saat menyebarkan atau memvalidasi template-uri
* `az deployment`: Memperbaiki masalah bahwa penyebaran / validasi tidak mendukung karakter yang dikodekan khusus
* `az deployment sub/group what-if`: Memperbaiki penyelarasan array dan penanganan kesalahan
* `az deployment operation`: Memodifikasi informasi terdepresiasi

### <a name="aro"></a>ARO

* Menambahkan contoh ke az aro create, list, list-credentials, show, delete
* Menambahkan fungsi generate_random_id

### <a name="backup"></a>Cadangan

* Izinkan FriendlyName dalam mengaktifkan perlindungan untuk perintah AzureFileShare
* Perbaiki dalam Perintah restore-disk IaasVM
* Tambahkan perintah BackupManagementType "MAB" ke perintah daftar item
* Tambahkan dukungan untuk mencoba kembali pembaruan kebijakan untuk item yang gagal.
* Menambahkan fungsionalitas Perlindungan Resume untuk Azure Virtual Machine
* Menambahkan dukungan untuk menentukan ResourceGroup untuk menyimpan instantRP selama Create or Modify Policy

### <a name="ci"></a>CI

* Dukungan flake8 3.8.0

### <a name="compute"></a>Compute

* New command az vm auto-shutdown
* `az vm list-skus`: Perbarui perilaku --zone, kembalikan semua jenis skus sekarang

### <a name="core"></a>Core

* Memperbarui status on/off konteks lokal ke tingkat pengguna global

### <a name="extension"></a>Ekstensi

* `az extension add`: Tambahkan --system untuk mengaktifkan pemasangan ekstensi di jalur sistem
* Mendukung .egg-info untuk menyimpan metadata ekstensi tipe roda

### <a name="iot"></a>IoT

* `az iot`: Perbarui modul perintah IoT pertama-tama jalankan pesan kesadaran ekstensi ke Id `azure-iot`modern yang akurat dan tidak usang .

### <a name="iot-hub"></a>IoT Hub

* Dukungan untuk perintah API dan Isolasi Jaringan 2020-03-01

### <a name="netappfiles"></a>NetAppFiles

* `az volume create`Menambahkan snapshot-id sebagai parameter untuk membuat volume ini akan memungkinkan pengguna untuk membuat volume dari snapshot yang ada.

### <a name="network"></a>Jaringan

* Memperbaiki nilai ttl diubah tidak diinginkan untuk add-record dns
* `az network public-ip create`: Beri tahu pelanggan tentang perubahan yang akan datang
* Mendukung perintah generik untuk skenario tautan pribadi
* `az network private-endpoint-connection`: Mendukung jenis mysql, postgres dan mariadb
* `az network private-endpoint-connection`: Mendukung tipe cosmosdb
* `az network private-endpoint`: deprecate --group-ids dan redirect ke --group-id

### <a name="output"></a>Output

* Tampilkan instruksi pembaruan di menemukan, umpan balik, dan --help

### <a name="packaging"></a>Pengemasan

* Bangun paket MSI/Homebrew dengan dependen yang diselesaikan dari requirements.txt

### <a name="rbac"></a>RBAC

* `az ad sp credential reset`: memperbaiki generasi kredensial yang lemah

### <a name="storage"></a>Penyimpanan

* `az storage account file-service-properties update/show`: Tambahkan Dukungan Properti File untuk Akun Storage
* `az storage container create`: Perbaiki #13373 dengan menambahkan validator untuk akses publik
* Menambahkan dukungan track2 ADLS Gen2
* `az storage blob sync`: Dukungan `--connection-string`
* `az storage blob sync`: Perbaiki pesan kesalahan yang salah saat azcopy tidak dapat menemukan lokasi instalasi

## <a name="april-30-2020"></a>30 April 2020 pukul

Versi 2.5.1

### <a name="acr"></a>ACR

* `az acr check-health`: Perbaiki "DOCKER_PULL_ERROR" di Windows

### <a name="compute"></a>Compute

* `az vm list-ip-addresses`: Penanganan kesalahan
* Memperbaiki bug pembuatan vm jika endpoint_vm_image_alias_doc tidak diatur dalam profil cloud
* `az vmss create`: Tambahkan --os-disk-size-gb

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb create/update`: tambahkan dukungan --enable-public-network

### <a name="extension"></a>Ekstensi

* Memperbaiki pemuatan metadata yang salah untuk ekstensi tipe roda

### <a name="packaging"></a>Pengemasan

* Add az script for Git Bash/Cygwin on Windows

### <a name="sql"></a>SQL

* `az sql instance-pool`: Tambahkan grup perintah kumpulan instans

### <a name="storage"></a>Penyimpanan

* Upgrade package azure-multiapi-storage to 0.3.0
* Mendukung GZRS untuk pembuatan dan pembaruan akun penyimpanan
* `az storage account failover`: Tambahkan dukungan untuk failover akun penyimpanan grs/gzrs
* `az storage blob upload`: Tambahkan parameter --encryption-scope untuk mendukung penentuan informasi cakupan enkripsi

## <a name="april-28-2020"></a>28 April 2020 pukul

Versi 2.5.0

### <a name="acs"></a>ACS

* [BREAKING CHANGE] az openshift create: remove --vnet-peer parameter.
* `az openshift create`: tambahkan bendera untuk mendukung klaster pribadi.
* `az openshift`: upgrade ke `2019-10-27-preview` versi API.
* `az openshift`: tambahkan `update` perintah.

### <a name="aks"></a>AKS

* `az aks create`: Tambahkan dukungan untuk Windows

### <a name="appservice"></a>AppService

* `az webapp deployment source config-zip`: hapus tidur setelah request.get()

### <a name="arm"></a>ARM

* Menambahkan perintah What-If penyebaran templat

### <a name="aro"></a>ARO

* `az aro`: Memperbaiki output tabel

### <a name="ci"></a>CI

* Pytest onboard dan hidung terdepresiasi untuk Tes Otomatisasi

### <a name="compute"></a>Compute

* `az vmss disk detach`: memperbaiki masalah NoneType disk data
* `az vm availability-set list`: Dukungan menampilkan daftar VM
* `az vm list-skus`: Memperbaiki masalah tampilan format tabel

### <a name="keyvault"></a>Az.KeyVault

* Menambahkan parameter `--enable-rbac-authorization` baru saat membuat atau memperbarui

### <a name="monitor"></a>Monitor

* Mendukung fitur CMK klaster LA
* `az monitor log-analytics workspace linked-storage`: mendukung fitur BYOS

### <a name="network"></a>Jaringan

* `az network security-partner`: mendukung penyedia mitra keamanan

### <a name="privatedns"></a>Privatedns

* Menambahkan fitur di zona DNS pribadi untuk mengimpor file zona ekspor

## <a name="april-21-2020"></a>21 April 2020 pukul

Versi 2.4.0

### <a name="acr"></a>ACR

* `az acr run --cmd`: nonaktifkan penimpaan direktori kerja
* Mendukung titik akhir data khusus

### <a name="aks"></a>AKS

* `az aks list -o table` harus menunjukkan privateFqdn sebagai fqdn untuk cluster pribadi
* Tambahkan --uptime-sla
* Memperbarui paket containerservice
* Menambahkan dukungan IP publik node
* Memperbaiki kesalahan ketik dalam perintah bantuan

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menyelesaikan referensi vault utama untuk daftar kv dan perintah ekspor
* Perbaikan bug untuk nilai kunci daftar

### <a name="appservice"></a>AppService

* `az functionapp create`: Mengubah cara linuxFxVersion sedang diatur untuk aplikasi fungsi dotnet linux. Ini harus memperbaiki bug yang mencegah aplikasi konsumsi dotnet linux dibuat
* [BREAKING CHANGE] `az webapp create`: perbaiki untuk menjaga AppSettings yang ada dengan az webapp create
* [BREAKING CHANGE] `az webapp up`: fix untuk membuat perintah RG for az webapp up saat menggunakan bendera -g
* [BREAKING CHANGE] `az webapp config`: perbaiki untuk menampilkan nilai untuk output non-JSON dengan az webapp config connection-string list

### <a name="arm"></a>ARM

* `az deployment create/validate`: Tambahkan parameter `--no-prompt` untuk mendukung melewatkan prompt parameter yang hilang untuk templat ARM
* `az deployment group/mg/sub/tenant validate`: Mendukung komentar dalam file parameter penyebaran
* `az deployment`: Hapus `is_preview` untuk parameter `--handle-extended-json-format`
* `az deployment group/mg/sub/tenant cancel`: Dukungan batalkan penyebaran untuk templat ARM
* `az deployment group/mg/sub/tenant validate`: Meningkatkan pesan kesalahan saat verifikasi penerapan gagal
* `az deployment-scripts`: Menambahkan perintah baru untuk DeploymentScripts
* `az resource tag`: Tambahkan parameter `--is-incremental` untuk mendukung penambahan tag ke sumber daya secara bertahap

### <a name="aro"></a>ARO

* `az aro`: Tambahkan modul perintah aro OpenShift V4 Azure RedHat

### <a name="batch"></a>Batch

* Perbarui API Batch

### <a name="compute"></a>Compute

* `az sig image-version create`: Tambahkan jenis akun penyimpanan Premium_LRS
* `az vmss update`: Memperbaiki masalah pembaruan pemberitahuan akhir
* `az vm/vmss create`: Tambahkan dukungan untuk versi gambar khusus
* SIG API Versi 2019-12-01
* `az sig image-version create`: Tambahkan --target-region-encryption
* Memperbaiki tes gagal saat berjalan secara serial karena nama keyvault diduplikasi dalam cache in-momery global

### <a name="cosmosdb"></a>CosmosDB

* Dukung `az cosmosdb private-link-resource/private-endpoint-connection`

### <a name="iot-central"></a>IoT Pusat

* Mati syir `az iotcentral`
* Menambahkan `az iot central` modul perintah

### <a name="monitor"></a>Monitor

* Mendukung skenario tautan pribadi untuk monitor
* Perbaiki cara mengejek yang salah dalam test_monitor_general_operations.py

### <a name="network"></a>Jaringan

* Deprecate sku untuk perintah pembaruan ip publik
* `az network private-endpoint`: Mendukung grup zona dns pribadi
* Aktifkan fitur konteks lokal untuk parameter vnet/subnet
* Memperbaiki contoh penggunaan yang salah dalam test_nw_flow_log_delete

### <a name="packaging"></a>Pengemasan

* Drop support untuk paket Ubuntu/Disco

### <a name="rbac"></a>RBAC

* `az ad app create/update`: mendukung --optional-claims sebagai parameter

### <a name="rdbms"></a>RDBMS

* Menambahkan perintah administrator direktori aktif Azure untuk PostgreSQL dan MySQL

### <a name="service-fabric"></a>Service Fabric

* Memperbaiki #12891: `az sf application update --application-parameters` menghapus parameter lama yang tidak ada dalam permintaan
* Perbaiki #12470 az sf buat cluster, perbaiki bug dalam daya tahan dan keandalan pembaruan dan temukan vmss dengan benar melalui kode yang diberi nama tipe node

### <a name="sql"></a>SQL

* Tambahkan `az sql mi op list`, `az sql mi op get`, , `az sql mi op cancel`
* `az sql midb`: memperbarui/menampilkan kebijakan retensi jangka panjang, menampilkan/menghapus pencadangan retensi jangka panjang, memulihkan pencadangan retensi jangka panjang

### <a name="storage"></a>Penyimpanan

* Upgrade azure-mgmt-storage to 9.0.0
* `az storage logging off`: Mendukung mematikan log untuk akun penyimpanan
* `az storage account update`: Aktifkan tombol putar otomatis untuk CMK
* `az storage account encryption-scope create/update/list/show`: Tambahkan dukungan untuk menyesuaikan cakupan enkripsi
* `az storage container create`: Tambahkan --default-encryption-scope dan --deny-encryption-scope-override untuk mengatur cakupan enkripsi untuk tingkat kontainer

### <a name="survey"></a>Survei

* Menambahkan tombol untuk menonaktifkan tautan survei

## <a name="april-01-2020"></a>01 April 2020

Versi 2.3.1

### <a name="acr"></a>ACR

* Memperbaiki versi yang salah dari azure-mgmt-containerregistry for Linux

### <a name="profile"></a>Profil

* az login: Perbaiki kegagalan login dengan profil cloud selain `latest`

## <a name="march-31-2020"></a>31 Maret 2020

Versi 2.3.0

### <a name="acr"></a>ACR

* 'az acr task update': null pointer exception
* `az acr import`: Memodifikasi pesan bantuan dan kesalahan untuk memperjelas penggunaan --source dan --registry
* Menambahkan validator untuk argumen 'registry_name'
* `az acr login`:Hapus bendera pratinjau pada '--expose-token'
* [MELANGGAR PERUBAHAN] Parameter cabang 'az acr task create/update' dihapus
* 'az acr task update' Pelanggan sekarang dapat memperbarui konteks, git-token, dan atau pemicu secara individual
* 'az acr agentpool': fitur baru

### <a name="aks"></a>AKS

* Memperbaiki apiServerAccessProfile saat memperbarui --api-server-authorized-ip-ranges
* pembaruan aks: Menimpa IP keluar dengan nilai input saat memperbarui
* Jangan membuat SPN untuk klaster MSI dan dukungan melampirkan acr ke cluster MSI

### <a name="ams"></a>AMS

* Perbaiki #12469: menambahkan kebijakan kunci konten Fairplay gagal karena masalah dengan parameter 'tanya'

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Tambahkan --skip-keyvault untuk ekspor kv

### <a name="appservice"></a>AppService

* Memperbaiki #12509: Menghapus tag ke az webapp secara default
* az functionapp create: Menu bantuan --runtime-version yang diperbarui dan peringatan tambahan saat pengguna menentukan --runtime-version untuk dotnet
* az functionapp create: Memperbarui cara javaVersion sedang diatur untuk aplikasi fungsi Windows

### <a name="arm"></a>ARM

* az deployment create/validate: Gunakan --handle-extended-json-format secara default
* az lock create: Tambahkan contoh pembuatan subresource di dokumentasi bantuan
* az deployment {group/mg/sub/tenant} list: Support provisioningState filtering
* az deployment: Memperbaiki parse bug untuk komentar di bawah argumen terakhir

### <a name="backup"></a>Cadangan

* Menambahkan beberapa kemampuan pemulihan file
* Menambahkan dukungan hanya untuk Mencadangkan Disk OS
* Menambahkan parameter restore-as-unmanaged-disk untuk menentukan pemulihan yang tidak dikelola

### <a name="compute"></a>Compute

* az vm create: Tambahkan opsi NONE --nsg-rule
* az vmss create/update: remove vmss automatic repairs preview tag
* az vm update: Support --workspace
* Memperbaiki bug di VirtualMachineScaleSetExtension kode inisialisasi
* Tingkatkan VMAccess Versi yang kuat ke 2.4
* az vmss set-orchestration-service-state: support vmss set orchestration service state
* Tingkatkan versi API disk ke 2019-11-01
* az disk create: add --disk-iops-read-only, --disk-mbps-read-only, --max-shares, --image-reference, --image-reference-lun, --gallery-image-reference, --gallery-image-reference-lun

### <a name="cosmos-db"></a>Cosmos DB

* Memperbaiki opsi tipe --yang hilang untuk pengalihan deprekasi

### <a name="docker"></a>Docker

* Pembaruan untuk Alpine 3.11 dan Python 3.6.10

### <a name="extension"></a>Ekstensi

* Memungkinkan untuk memuat ekstensi di jalur sistem melalui paket

### <a name="hdinsight"></a>HDInsight

* (az hdinsight create:) Pelanggan dukungan menentukan versi tls minimal yang didukung dengan menggunakan parameter `--minimal-tls-version`. Nilai yang diizinkan adalah 1,0,1,1,1,2

### <a name="iot"></a>IoT

* Menambahkan pencetak kode
* az iot hub create : Ubah default sku ke S1 dari F1
* iot hub: Mendukung IotHub di profil 2019-03-01-hybrid

### <a name="iotcentral"></a>IoTCentral

* Memperbarui detail kesalahan, memperbarui templat aplikasi default, dan pesan cepat

### <a name="keyvault"></a>Az.KeyVault

* Mendukung pencadangan/pemulihan sertifikat
* keyvault create/update: Support --retention-days
* Tidak lagi menampilkan kunci/rahasia terkelola saat listing
* az keyvault create: support `--network-acls`, `--network-acls-ips` dan `--network-acls-vnets` untuk menentukan aturan jaringan saat membuat vault

### <a name="lock"></a>Kunci

* az lock delete fix bug: az lock delete tidak berfungsi di Microsoft.DocumentDB

### <a name="monitor"></a>Monitor

* az monitor clone: mendukung aturan metrik kloning dari satu sumber daya ke sumber daya lainnya
* Memperbaiki IcM179210086: tidak dapat membuat peringatan metrik kustom untuk metrik Insights Aplikasi mereka

### <a name="netappfiles"></a>NetAppFiles

* az volume create: Izinkan volume perlindungan data menambahkan operasi replikasi: menyetujui, menangguhkan, melanjutkan, status, menghapus

### <a name="network"></a>Jaringan

* az network application-gateway waf-policy managed-rule rule-set add: support Microsoft_BotManagerRuleSet
* tampilan flow-log pengamat jaringan: perbaiki info usang yang salah
* mendukung nama host di pendengar gateway aplikasi
* az network nat gateway: support create empty resource without public ip atau public ip prefix
* Mendukung pembuatan gateway VPN
* Dukungan `--if-none-match` di `az network dns record-set {} add-record`

### <a name="packaging"></a>Pengemasan

* Jatuhkan dukungan untuk python 3.5

### <a name="profile"></a>Profil

* az login: Tampilkan peringatan untuk kesalahan MFA

### <a name="rdbms"></a>RDBMS

* Menambahkan perintah manajemen kunci enkripsi data server untuk PostgreSQL dan MySQL

## <a name="march-10-2020"></a>10 Maret 2020

Versi 2.2.0

### <a name="acr"></a>ACR

* Memperbaiki: `az acr login` salah meningkatkan kesalahan
* Menambahkan perintah baru `az acr helm install-cli`
* Menambahkan tautan pribadi dan dukungan CMK
* menambahkan perintah 'daftar sumber daya tautan pribadi'

### <a name="aks"></a>AKS

* memperbaiki penjelajahan aks di shell cloud
* az aks: Memperbaiki addon pemantauan dan kesalahan agentpool NoneType
* Tambahkan --nodepool-tags ke kumpulan node saat membuat azure kubernetes cluster
* Menambahkan --tag saat menambahkan atau memperbarui nodepool ke cluster
* aks create: add `--enable-private-cluster`
* add --nodepool-labels saat membuat azure kubernetes cluster
* tambahkan --label saat menambahkan nodepool baru ke klaster kubernetes azure
* menambahkan hilang / di url dasbor
* Mendukung membuat klaster tinta yang memungkinkan identitas terkelola
* az aks: Validasi plugin jaringan menjadi "azure" atau "kubenet"
* az aks: Tambahkan dukungan kunci sesi aad
* [BREAKING CHANGE] az aks: support msi changes for GF dan BF for omsagent (Container monitoring)(#1)
* az aks use-dev-spaces: Menambahkan opsi tipe endpoint ke perintah use-dev-spaces untuk menyesuaikan titik akhir yang dibuat pada pengontrol Azure Dev Spaces

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Buka blokir menggunakan "set kv" untuk menambahkan referensi dan fitur keyvault ...

### <a name="appservice"></a>AppService

* az webapp create : Perbaiki masalah saat menjalankan perintah dengan --runtime
* az functionapp deployment source config-zip: Menambahkan pesan kesalahan jika grup sumber daya atau nama fungsi tidak valid/tidak ada
* functionapp create: Perbaiki pesan peringatan yang muncul dengan `functionapp create` hari ini yang mengutip `--functions_version` bendera tetapi keliru menggunakan `_` bukan `-` nama bendera
* az functionapp create: Memperbarui cara linuxFxVersion dan nama gambar kontainer sedang ditetapkan untuk aplikasi fungsi linux
* az functionapp deployment source config-zip: Memperbaiki masalah yang disebabkan oleh pengaturan aplikasi mengubah kondisi balap selama penerapan zip, memberikan kesalahan 5xx selama penerapan
* Memperbaiki #5720946: az webapp backup gagal mengatur nama

### <a name="arm"></a>ARM

* az resource: Meningkatkan contoh modul sumber daya
* az daftar penetapan kebijakan: Mendukung penetapan kebijakan listingan di cakupan Grup Manajemen
* Tambahkan `az deployment group` dan `az deployment operation group` untuk penyebaran templat di grup sumber daya. Ini adalah duplikat dari `az group deployment` dan `az group deployment operation`
* Tambahkan `az deployment sub` dan `az deployment operation sub` untuk penyebaran templat di cakupan langganan. Ini adalah duplikat dari `az deployment` dan `az deployment operation`
* Menambahkan `az deployment mg` dan `az deployment operation mg` untuk penyebaran templat di grup manajemen
* Menambahkan `az deployment tenant` dan `az deployment operation tenant` untuk penyebaran templat di cakupan penyewa
* az policy assignment create: Menambahkan deskripsi ke `--location` parameter
* az group deployment create: Tambahkan parameter `--aux-tenants` untuk mendukung penyewa silang

### <a name="cdn"></a>CDN

* Menambahkan perintah WAF CDN

### <a name="compute"></a>Compute

* az sig image-version: add --data-snapshot-luns
* az ppg show: add --colocation-status untuk memungkinkan pengambilan status colocation dari semua sumber daya dalam grup penempatan kedekatan
* az vmss create/update: mendukung perbaikan otomatis
* [BREAKING CHANGE] az image template: ganti nama template menjadi builder
* az image builder create: add --image-template

### <a name="cosmos-db"></a>Cosmos DB

* Tambahkan sql disimpan prosedur, udf dan memicu cmdlets
* az cosmosdb create: add --key-uri untuk mendukung penambahan informasi enkripsi vault utama

### <a name="keyvault"></a>Az.KeyVault

* keyvault create: aktifkan penghapusan lunak secara default

### <a name="monitor"></a>Monitor

* az monitor metrics alert create: support `~` in `--condition`

### <a name="network"></a>Jaringan

* az network application-gateway rewrite-rule create: support url configuration
* az network dns zone import: --zone-name akan menjadi case insensitive di masa depan
* az network private-endpoint/private-link-service: menghapus label pratinjau
* az network bastion: support bastion
* az network vnet list-available-ips: support list available ips in a vnet
* az network watcher flow-log create/list/delete/update: add new commands untuk mengelola watcher flow log dan exposing --location untuk mengidentifikasi watcher secara eksplisit
* az network watcher flow-log configure: deprecated
* az network watcher flow-log show: support --location dan --name untuk mendapatkan hasil yang diformat ARM, output format lama yang tidak digunakan lagi

### <a name="policy"></a>Kebijakan

* az penetapan kebijakan membuat: Memperbaiki bug yang secara otomatis menghasilkan nama penetapan kebijakan melebihi batas

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
* Memperbarui Tes Titik Akhir Pribadi RDBMS

### <a name="sql"></a>SQL

* Sql midb Tambahkan: list-deleted, show-deleted, update-retention, show-retention
* (sql server create:) Tambahkan bendera akses jaringan publik opsional 'Aktifkan'/'Nonaktifkan' ke pembuatan sql server
* (pembaruan sql server:) membuat beberapa perubahan yang dihadapi pelanggan
* Tambahkan properti minimal_tls_version untuk MI dan SQL DB

### <a name="storage"></a>Penyimpanan

* az storage blob delete-batch: Salah gambar `--dryrun` bendera
* az storage account network-rule add (bug fix): add operation should be idempotent
* az storage account create/update: Tambahkan dukungan Preferensi Perutean
* Upgrade azure-mgmt-storage version ke 8.0.0
* az storage container immutability create: add --allow-protected-append-write parameter
* az akun penyimpanan daftar sumber daya pribadi-tautan-sumber daya: Tambahkan dukungan ke daftar sumber daya tautan pribadi untuk akun penyimpanan
* az storage account private-endpoint-connection approve/reject/show/delete: Dukungan untuk mengelola koneksi titik akhir pribadi
* az storage account blob-service-properties update: add --enable-restore-policy dan --restore-days
* az storage blob restore: Tambahkan dukungan untuk memulihkan rentang blob

## <a name="february-18-2020"></a>18 Februari 2020

Versi 2.1.0

### <a name="acr"></a>ACR

* Menambahkan argumen `--expose-token` baru untuk `az acr login`
* Memperbaiki output yang salah dari `az acr task identity show -n Name -r Registry -o table`
* az acr login: Lemparkan CLIError jika ada kesalahan yang dikembalikan oleh perintah docker

### <a name="acs"></a>ACS

* aks create/update: tambahkan `--vnet-subnet-id` validasi

### <a name="aladdin"></a>Aladdin

* Mengurai contoh yang dihasilkan ke dalam perintah _help.py

### <a name="ams"></a>AMS

* az ams is GA now

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Merevisi pesan bantuan untuk mengecualikan filter kunci/label yang tidak didukung
* Menghapus tag pratinjau untuk sebagian besar perintah tidak termasuk identitas terkelola dan bendera fitur
* Menambahkan kunci terkelola pelanggan saat memperbarui toko

### <a name="appservice"></a>AppService

* az webapp list-runtimes: Memperbaiki bug untuk list-runtimes
* Add az webapp|functionapp config ssl create
* Menambahkan dukungan untuk aplikasi fungsi v3 dan node 12

### <a name="arm"></a>ARM

* az penetapan kebijakan membuat: Memperbaiki pesan kesalahan saat `--policy` parameter tidak valid
* az group deployment create: Perbaiki kesalahan "stat: path too long for Windows" saat menggunakan file parameter besar.json

### <a name="backup"></a>Cadangan

* Memperbaiki untuk alur pemulihan tingkat item di OLR
* Menambahkan pemulihan sebagai dukungan file untuk database SQL dan SAP

### <a name="compute"></a>Compute

* vm/vmss/availability-set update: add --ppg untuk memungkinkan memperbarui ProximityPlacementGroup
* vmss create: add --data-disk-iops dan --data-disk-mbps
* az vm host: remove preview tag for `vm host` and `vm host group`
* [MELANGGAR PERUBAHAN] Perbaiki #10728: `az vm create`: buat subnet secara otomatis jika vnet ditentukan dan subnet tidak ada
* Meningkatkan ketahanan daftar gambar vm

### <a name="eventhub"></a>Eventhub

* Dukungan Azure Stack untuk profil 2019-03-01-hybrid

### <a name="keyvault"></a>Az.KeyVault

* az keyvault key create: add a new value `import` for parameter `--ops`
* az keyvault key list-versions: parameter `--id` dukungan untuk menentukan kunci
* Mendukung koneksi titik akhir pribadi

### <a name="network"></a>Jaringan

* Bump to azure-mgmt-network 9.0.0
* az network private-link-service update/create: support --enable-proxy-protocol
* Menambahkan fitur Monitor V2 koneksi

### <a name="packaging"></a>Pengemasan

* [MELANGGAR PERUBAHAN] Jatuhkan dukungan untuk Python 2.7

### <a name="profile"></a>Profil

* Pratinjau: Tambahkan atribut `homeTenantId` baru dan `managedByTenants` ke akun langganan. Harap jalankan `az login` kembali agar perubahan berlaku
* az login: Tampilkan peringatan saat langganan tercantum dari lebih dari satu penyewa dan default ke yang pertama. Untuk memilih penyewa tertentu saat mengakses langganan ini, harap sertakan `--tenant` di `az login`

### <a name="role"></a>Peran

* az penetapan peran membuat: Memperbaiki kesalahan bahwa menetapkan peran ke prinsipal layanan dengan nama tampilan menghasilkan HTTP 400

### <a name="sql"></a>SQL

* Perbarui cmdlet `az sql mi update` Instans Terkelola SQL dengan dua parameter baru: tingkat dan keluarga

### <a name="storage"></a>Penyimpanan

* [MELANGGAR PERUBAHAN] `az storage account create`: Mengubah jenis akun penyimpanan default ke StorageV2

## <a name="february-04-2020"></a>04 Februari 2020

Versi 2.0.81

### <a name="acs"></a>ACS

* Menambahkan dukungan untuk mengatur port yang dialokasikan keluar dan batas waktu idle pada penyeimbang beban standar
* Pembaruan api versi 2019-11-01

### <a name="acr"></a>ACR

* [MELANGGAR PERUBAHAN] `az acr delete` akan meminta
* [MELANGGAR PERUBAHAN] 'az acr task delete' akan meminta
* Menambahkan grup perintah baru 'az acr taskrun show/list/delete' untuk manajemen taskrun

### <a name="aks"></a>AKS

* Setiap klaster mendapatkan prinsip layanan terpisah untuk meningkatkan isolasi

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Mendukung impor/ekspor referensi keyvault dari/ke appservice
* Mendukung impor/ekspor semua label dari appconfig ke appconfig
* Memvalidasi nama kunci dan fitur sebelum mengatur dan mengimpor
* Mengekspos modifikasi sku untuk penyimpanan konfigurasi.
* Tambahkan grup perintah untuk identitas terkelola.

### <a name="appservice"></a>AppService

* Azure Stack: perintah permukaan di bawah profil 2019-03-01-hybrid
* functionapp: Menambahkan kemampuan untuk membuat aplikasi fungsi Java di Linux

### <a name="arm"></a>ARM

* Memperbaiki masalah #10246: `az resource tag` crash saat parameter `--ids` masuk adalah ID grup sumber daya
* Memperbaiki masalah #11658: `az group export` perintah tidak mendukung `--query` dan `--output` parameter
* Memperbaiki masalah #10279: Kode `az group deployment validate` keluar adalah 0 saat verifikasi gagal
* Memperbaiki masalah #9916: Meningkatkan pesan kesalahan konflik antara tag dan kondisi filter lainnya untuk `az resource list` perintah
* Menambahkan parameter `--managed-by` baru untuk mendukung penambahan informasi terkelolaOleh untuk perintah `az group create`

### <a name="azure-red-hat-openshift"></a>Azure Red Hat OpenShift

* Menambahkan `monitor` subkelompok untuk mengelola pemantauan Analitik Log di klaster Buka Buka Azure Red Hat

### <a name="botservice"></a>BotService

* Memperbaiki masalah #11697: `az bot create` bukan idempotent
* Mengubah tes koreksi nama agar berjalan hanya dalam mode Langsung

### <a name="cdn"></a>CDN

* Menambahkan dukungan untuk rulesEngine feature
* Menambahkan grup perintah baru 'aturan titik akhir cdn' untuk mengelola aturan
* Perbarui azure-mgmt-cdn version ke 4.0.0 untuk menggunakan api version 2019-04-15

### <a name="deployment-manager"></a>Deployment Manager

* Tambahkan operasi daftar untuk semua sumber daya.
* Tingkatkan sumber daya langkah untuk jenis langkah baru.
* Perbarui paket azure-mgmt-deploymentmanager untuk menggunakan versi 0.2.0.

### <a name="iot"></a>IoT

* Deprecate perintah 'IoT hub Job'.

### <a name="iot-central"></a>IoT Pusat

* Mendukung pembuatan/pembaruan aplikasi dengan nama sku baru ST0, ST1, ST2.

### <a name="key-vault"></a>Key Vault

* Tambahkan perintah `az keyvault key download` baru untuk mengunduh kunci.

### <a name="misc"></a>Misc

* Memperbaiki #6371: Mendukung nama file dan penyelesaian variabel lingkungan di Bash

### <a name="network"></a>Jaringan

* Perbaiki #2092: az network dns record-set add/remove: add warning when record-set tidak ditemukan. Di masa depan, argumen tambahan akan didukung untuk mengkonfirmasi pembuatan otomatis ini.

### <a name="policy"></a>Kebijakan

* Menambahkan perintah `az policy metadata` baru untuk mengambil sumber daya metadata kebijakan yang kaya
* `az policy remediation create`: Tentukan apakah kepatuhan harus dievaluasi ulang sebelum remediasi dengan `--resource-discovery-mode` parameter

### <a name="profile"></a>Profil

* `az account get-access-token`: Tambahkan `--tenant` parameter untuk mendapatkan token untuk penyewa secara langsung, tidak perlu menentukan langganan

### <a name="rbac"></a>RBAC

* [MELANGGAR PERUBAHAN] Perbaiki #11883: `az role assignment create`: ruang lingkup kosong akan memicu kesalahan

### <a name="security"></a>Keamanan

* Tambahkan perintah `az atp show` baru dan `az atp update` untuk melihat dan mengelola pengaturan perlindungan ancaman tingkat lanjut untuk akun penyimpanan.

### <a name="sql"></a>SQL

* `sql dw create`: deprecate `--zone-redundant` dan `--read-replica-count` parameter. Parameter ini tidak berlaku untuk DataWarehouse.
* [BREAKING CHANGE] `az sql db create`: Hapus "WideWorldImportersStd" dan "WideWorldImportersFull" sebagai nilai yang diizinkan didokumentasikan untuk "az sql db create --sample-name". Database sampel ini akan selalu menyebabkan penciptaan gagal.
* Tambahkan perintah `sql db classification show/list/update/delete` Baru dan `sql db classification recommendation list/enable/disable` kelola klasifikasi sensitivitas untuk database SQL.
* `az sql db audit-policy`: Perbaiki untuk tindakan dan grup audit kosong

### <a name="storage"></a>Penyimpanan

* Tambahkan grup `az storage share-rm` perintah baru untuk menggunakan penyedia sumber daya Microsoft.Storage untuk operasi manajemen berbagi file Azure.
* Memperbaiki masalah #11415: kesalahan izin untuk `az storage blob update`
* Integrasikan Azcopy 10.3.3 dan dukung Win32.
* `az storage copy`: Tambahkan `--include-path`, `--include-pattern`, `--exclude-path` dan`--exclude-pattern` parameter
* `az storage remove`: Perubahan `--inlcude` dan `--exclude` parameter ke `--include-path`, `--include-pattern`, `--exclude-path` dan`--exclude-pattern` parameter
* `az storage sync`: Tambahkan `--include-pattern`, `--exclude-path` dan`--exclude-pattern` parameter

### <a name="servicefabric"></a>ServiceFabric

* Tambahkan perintah baru untuk mengelola appliaction dan layanan.

## <a name="january-13-2020"></a>13 Januari 2020

Versi 2.0.80

### <a name="compute"></a>Compute

* pembaruan disk: Tambahkan --disk-encryption-set dan --encryption-type
* pembuatan/pembaruan snapshot: Tambahkan --disk-encryption-set dan --encryption-type

### <a name="storage"></a>Penyimpanan

* Upgrade azure-mgmt-storage version ke 7.1.0
* `az storage account create`: Menambahkan `--encryption-key-type-for-table` dan `--encryption-key-type-for-queue` mendukung Layanan Enkripsi Tabel dan Antrean

## <a name="january-07-2020"></a>07 Januari 2020

Versi 2.0.79

### <a name="acr"></a>ACR

* [MELANGGAR PERUBAHAN] Hapus parameter '--os' untuk 'acr build', 'acr task create/update', 'acr run', dan 'acr pack'. Gunakan '--platform' sebagai gantinya.

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan dukungan untuk mengimpor/mengekspor bendera fitur
* Tambahkan perintah baru 'az appconfig kv set-keyvault' untuk membuat referensi keyvault
* Mendukung berbagai konvensi penamaan saat mengekspor bendera fitur ke file

### <a name="appservice"></a>AppService

* Memperbaiki masalah # 7154: Memperbarui dokumentasi untuk <> perintah untuk menggunakan kutu belakang alih-alih tanda kutip tunggal
* Memperbaiki masalah #11287: webapp up: Secara default buat aplikasi yang dibuat menggunakan 'harus 'SSL diaktifkan'
* Memperbaiki masalah #11592: Tambahkan az webapp up flag untuk situs statis html

### <a name="arm"></a>ARM

* Memperbaiki `az resource tag`: Tag Vault Layanan Pemulihan tidak dapat diperbarui

### <a name="backup"></a>Cadangan

* Menambahkan perintah baru 'perlindungan cadangan undelete' untuk mengaktifkan fitur penghapusan lunak untuk beban kerja IaasVM
* Menambahkan parameter baru '--soft-delete-feature-state' untuk mengatur perintah properti cadangan
* Menambahkan dukungan pengecualian disk untuk beban kerja IaasVM

### <a name="compute"></a>Compute

* Memperbaiki `vm create` kegagalan di profil Azure Stack.
* vm monitor metrik tail/list-definitions: mendukung metrik kueri dan definisi daftar untuk vm.
* Menambahkan tindakan perintah permohonan ulang baru untuk az vm

### <a name="hdinsight"></a>HDInsight

* Dukungan untuk membuat cluster Kafka dengan Kafka Rest Proxy
* Upgrade azure-mgmt-hdinsight to 1.3.0

### <a name="misc"></a>Misc.

* Menambahkan perintah `az version show` pratinjau untuk menampilkan versi modul dan ekstensi Azure CLI dalam format JSON secara default atau format yang dikonfigurasi oleh --output

### <a name="event-hubs"></a>Event Hubs

* [MELANGGAR PERUBAHAN] Hapus opsi status 'ReceiveDisabled' dari perintah 'az eventhubs eventhub update' dan 'az eventhubs eventhub create'. Opsi ini tidak berlaku untuk entitas Event Hub.

### <a name="service-bus"></a>Service Bus

* [MELANGGAR PERUBAHAN] Hapus opsi status 'ReceiveDisabled' dari perintah 'az servicebus topic create', 'az servicebus topic update', 'az servicebus queue create', dan 'az servicebus queue update'. Opsi ini tidak berlaku untuk topik dan antrean Bus Layanan.

### <a name="rbac"></a>RBAC

* Perbaiki #11712: `az ad app/sp show` tidak mengembalikan kode keluar 3 saat aplikasi atau prinsipal layanan tidak ada

### <a name="storage"></a>Penyimpanan

* `az storage account create`: Hapus bendera pratinjau untuk parameter --enable-hierarchical-namespace
* Perbarui azure-mgmt-storage version ke 7.0.0 untuk menggunakan api version 2019-06-01
* Tambahkan parameter `--enable-delete-retention` baru dan `--delete-retention-days` untuk mendukung pengelolaan kebijakan retensi hapus untuk properti blob-service-akun penyimpanan.

## <a name="december-17-2019"></a>17 Desember 2019

2.0.78

### <a name="acr"></a>ACR

* Menambahkan dukungan Konteks lokal dalam tugas acr dijalankan

### <a name="acs"></a>ACS

* [BREAKING CHANGEAZ] openshift create: ganti nama `--workspace-resource-id` menjadi `--workspace-id`.

### <a name="ams"></a>AMS

* Perintah acara yang diperbarui untuk mengembalikan 3 saat sumber daya tidak ditemukan

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Memperbaiki bug saat menambahkan versi api untuk meminta url. Solusi yang ada tidak bekerja dengan pagination.
* Menambahkan dukungan untuk menampilkan bahasa selain bahasa Inggris sebagai layanan backend kami mendukung unicode untuk globalisasi.

### <a name="appservice"></a>AppService

* Memperbaiki masalah #11217: webapp: az webapp config ssl upload harus mendukung parameter slot
* Memperbaiki masalah #10965: Kesalahan: Nama tidak bisa kosong. Perbolehkan hapus berdasarkan ip_address dan subnet
* Menambahkan dukungan untuk mengimpor sertifikat dari Key Vault `az webapp config ssl import`

### <a name="arm"></a>ARM

* Paket azure-mgmt-resource yang diperbarui untuk menggunakan 6.0.0
* Dukungan Penyewa Silang untuk `az group deployment create` perintah dengan menambahkan parameter baru `--aux-subs`
* Menambahkan parameter `--metadata` baru untuk mendukung penambahan informasi metadata untuk definisi kumpulan kebijakan.

### <a name="backup"></a>Cadangan

* Menambahkan dukungan Pencadangan untuk beban kerja SQL dan SAP Hana.

### <a name="botservice"></a>BotService

* [Melanggar perubahan] Hapus bendera '--version' dari perintah pratinjau 'az bot create'. Hanya bot SDK v4 yang didukung.
* Menambahkan pemeriksaan ketersediaan nama untuk 'az bot create'.
* Menambahkan dukungan untuk memperbarui URL ikon untuk bot melalui 'az bot update'.
* Menambahkan dukungan untuk memperbarui saluran Direct Line melalui 'pembaruan garis langsung az bot'.
* Menambahkan dukungan bendera '--enable-enhanced-auth' ke 'az bot directline create'.
* Grup perintah berikut adalah GA dan tidak dalam pratinjau: 'az bot authsetting'.
* Perintah berikut dalam 'az bot' adalah GA dan bukan dalam pratinjau: 'create', 'prepare-deploy', 'show', 'delete', 'update'.
* Memperbaiki 'az bot prepare-deploy' mengubah nilai '--proj-file-path' ke huruf kecil (misalnya "Test.csproj" menjadi "test.csproj").

### <a name="compute"></a>Compute

* vmss create/update: Menambahkan --scale-in-policy, yang memutuskan mesin virtual mana yang dipilih untuk dihapus saat VMSS diskalakan.
* pembaruan vm/vmss: Ditambahkan --priority.
* pembaruan vm/vmss: Ditambahkan --max-price.
* Menambahkan grup perintah yang diatur dengan enkripsi disk (buat, tampilkan, perbarui, hapus, daftar).
* pembuatan disk: Ditambahkan --encryption-type dan --disk-encryption-set.
* vm/vmss create: Added --os-disk-encryption-set dan --data-disk-encryption-sets.

### <a name="core"></a>Core

* Dukungan yang dihapus untuk Python 3.4
* Colokkan survei HaTS dalam beberapa perintah

### <a name="dls"></a>DLS

* Versi SDK ADLS yang diperbarui (0.0.48).

### <a name="install"></a>Instal

* Instal dukungan skrip python 3.8

### <a name="iot"></a>IOT

* [MELANGGAR PERUBAHAN] Menghapus parameter --failover-region dari manual-failover. Sekarang akan gagal untuk wilayah sekunder geo-berpasangan yang ditugaskan.

### <a name="key-vault"></a>Key Vault

* Tetap #8095: `az keyvault storage remove`: tingkatkan pesan bantuan
* Memperbaiki #8921: `az keyvault key/secret/certificate list/list-deleted/list-versions`: perbaiki bug validasi pada parameter `--maxresults`
* Memperbaiki #10512: `az keyvault set-policy`: meningkatkan pesan kesalahan saat tidak ada, `--object-id``--spn` atau `--upn` ditentukan
* Tetap #10846: `az keyvault secret show-deleted`: kapan `--id` ditentukan, `--name/-n` tidak diperlukan
* Tetap #11084: `az keyvault secret download`: tingkatkan pesan bantuan parameter `--encoding`

### <a name="network"></a>Jaringan

* az network application-gateway probe: Menambahkan dukungan --port option untuk menentukan port untuk menyelidik server backend saat membuat dan memperbarui
* az network application-gateway url-path-map create/update: perbaikan bug untuk `--waf-policy`
* az network application-gateway: Menambahkan dukungan `--rewrite-rule-set`
* az network list-service-aliases: Menambahkan alias layanan daftar dukungan yang dapat digunakan untuk Kebijakan Titik Akhir Layanan
* az network dns zone import: Menambahkan support .@ in record name

### <a name="packaging"></a>Pengemasan

* Menambahkan build tepi belakang untuk pemasangan pip
* Menambahkan paket Ubuntu eoan

### <a name="policy"></a>Kebijakan

* Menambahkan dukungan untuk Api Kebijakan versi 2019-09-01.
* az policy set-definition: Menambahkan pengelompokan dukungan dalam definisi penetapan kebijakan dengan `--definition-groups` parameter

### <a name="redis"></a>Redis

* Menambahkan param `--replicas-per-master` pratinjau ke `az redis create` perintah
* Diperbarui azure-mgmt-redis dari 6.0.0 ke 7.0.0rc1

### <a name="servicefabric"></a>ServiceFabric

* Tetap dalam logika add tipe node termasuk #10963: Menambahkan tipe node baru dengan tingkat daya tahan Emas akan selalu melempar kesalahan CLI
* Diperbarui ServiceFabricNodeVmExt versi ke 1.1 dalam template pembuatan

### <a name="sql"></a>SQL

* Menambahkan parameter "--read-scale" dan "--read-replicas" ke perintah sql db create dan update, untuk mendukung manajemen skala baca.

### <a name="storage"></a>Penyimpanan

* GA Rilis Properti Saham File Besar untuk pembuatan akun penyimpanan dan perintah pembaruan
* Ga Rilis Dukungan Token SAS Delegasi Pengguna
* Menambahkan perintah `az storage account blob-service-properties show` baru dan `az storage account blob-service-properties update --enable-change-feed` mengelola properti layanan blob untuk akun penyimpanan.
* [COMING BREAKING CHANGE] `az storage copy`: `*` karakter tidak lagi didukung sebagai wildcard di URL, tetapi parameter baru --include-pattern dan --exclude-pattern akan ditambahkan dengan `*` dukungan wildcard.
* Memperbaiki masalah #11043: Menambahkan dukungan untuk menghapus seluruh kontainer/share dalam `az storage remove` perintah

## <a name="november-26-2019"></a>26 November 2019 pukul

Versi 2.0.77

### <a name="acr"></a>ACR

* Parameter yang `--branch` tidak digunakan lagi dari acr task create/update

### <a name="azure-red-hat-openshift"></a>Azure Red Hat OpenShift

* Menambahkan `--workspace-resource-id` bendera untuk memungkinkan pembuatan cluster Openshift Azure Red Hat dengan pemantauan
* Ditambahkan `monitor_profile` untuk membuat klaster OpenShift Azure Red Hat dengan pemantauan

### <a name="aks"></a>AKS

* Menambahkan operasi rotasi sertifikat klaster dukungan menggunakan "az aks rotate-certs".

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan dukungan untuk menggunakan ☆ untuk `as az appconfig kv import` pemisah
* Memperbaiki masalah untuk mencantumkan nilai kunci dengan beberapa label termasuk label null.
* Diperbarui manajemen plane sdk, azure-mgmt-appconfiguration, ke versi 0.3.0.

### <a name="appservice"></a>AppService

* Memperbaiki masalah #11100: AttributeError for az webapp up saat membuat paket layanan
* az webapp up: Memaksa pembuatan atau penyebaran ke situs untuk bahasa yang didukung, tidak ada default yang digunakan.
* Menambahkan dukungan untuk App Service Environment: az appservice ase show | daftar | alamat daftar | daftar-rencana | membuat | perbarui | menghapus

### <a name="backup"></a>Cadangan

* Memperbaiki masalah dalam az backup policy list-associated-items. Menambahkan parameter BackupManagementType opsional.

### <a name="compute"></a>Compute

* Versi API yang ditingkatkan dari komputasi, disk, snapshot ke 2019-07-01
* vmss create: Peningkatan untuk --orchestration-mode
* sig image-definition create: Menambahkan --os-state untuk memungkinkan menentukan apakah mesin virtual yang dibuat di bawah gambar ini 'Generalized' atau 'Specialized'
* sig image-definition create: Ditambahkan --hyper-v-generation untuk memungkinkan menentukan generasi hypervisor
* sig image-version create: Menambahkan support --os-snapshot dan --data-snapshots
* gambar create: Menambahkan --data-disk-caching untuk memungkinkan menentukan pengaturan caching disk data
* Python Compute SDK yang ditingkatkan ke 10.0.0
* vm/vmss create: Menambahkan properti enum 'Spot' ke 'Priority'
* [Melanggar perubahan] Berganti nama menjadi parameter '--max-billing' menjadi '--max-price', baik untuk VM dan VMSS, agar konsisten dengan cmdlet Swagger dan Powershell
* peragaan log monitor vm: Menambahkan dukungan untuk meneri query log melalui ruang kerja analitik log tertaut.

### <a name="iot"></a>IOT

* Memperbaiki # 2531: Menambahkan argumen kenyamanan untuk pembaruan hub.
* Memperbaiki #8323: Menambahkan parameter yang hilang untuk membuat titik akhir kustom penyimpanan.
* Memperbaiki bug regresi: Mengembalikan perubahan yang menimpa titik akhir penyimpanan default.

### <a name="key-vault"></a>Key Vault

* Tetap # 11121: Saat menggunakan `az keyvault certificate list`, melewati `--include-pending` sekarang tidak memerlukan nilai `true` atau `false`

### <a name="netappfiles"></a>NetAppFiles

* Upgrade azure-mgmt-netapp ke 0.7.0 yang mencakup beberapa properti volume tambahan yang terkait dengan operasi replikasi yang akan datang

### <a name="network"></a>Jaringan

* application-gateway waf-config: usang
* application-gateway waf-policy: Menambahkan aturan terkelola subkelompok untuk mengelola set aturan terkelola dan aturan pengecualian
* application-gateway waf-policy: Menambahkan pengaturan kebijakan subkelompok untuk mengelola konfigurasi global kebijakan waf
* [BREAKING CHANGE] application-gateway waf-policy: Aturan subkelompok yang diganti namanya menjadi aturan kustom
* application-gateway http-listener: Ditambahkan --firewall-policy saat membuat
* application-gateway url-path-map rule: Ditambahkan --firewall-policy saat membuat

### <a name="packaging"></a>Pengemasan

* Menulis ulang pembungkus az dalam Python
* Menambahkan dukungan untuk Python 3.8
* Diubah menjadi paket Python 3 untuk RPM

### <a name="profile"></a>Profil

* Kesalahan yang dipoles saat berjalan `az login -u {} -p {}` dengan akun Microsoft
* Dipoles `SSLError` saat berjalan `az login` di belakang proxy dengan sertifikat root yang ditandatangani sendiri
* Tetap # 10578: `az login` hangs ketika lebih dari satu instance diluncurkan pada saat yang sama pada Windows atau WSL
* Tetap #11059: `az login --allow-no-subscriptions` gagal jika ada langganan di penyewa
* Tetap #11238: Setelah mengganti nama langganan, masuk dengan MSI akan menghasilkan langganan yang sama muncul dua kali

### <a name="rbac"></a>RBAC

* Diperbaiki #10996: Kesalahan Polandia untuk `--force-change-password-next-login` saat `az ad user update` `--password` tidak ditentukan

### <a name="redis"></a>Redis

* Memperbaiki #2902: Hindari mengatur konfigurasi memori saat memperbarui cache SKU Dasar

### <a name="reservations"></a>Reservasi

* Versi SDK yang ditingkatkan ke 0.6.0
* Menambahkan info detail billingplan setelah menelepon Get-Gatalogs
* Menambahkan perintah `az reservations reservation-order calculate` baru untuk menghitung harga untuk reservasi
* Menambahkan perintah `az reservations reservation-order purchase` baru untuk membeli reservasi baru

### <a name="rest"></a>Sisanya
* Diubah `az rest` menjadi GA

### <a name="sql"></a>SQL

* Updated azure-mgmt-sql to version 0.15.0.

### <a name="storage"></a>Penyimpanan

* membuat akun penyimpanan: Menambahkan --enable-hierarchical-namespace untuk mendukung semantik sistem file dalam layanan blob.
* Menghapus pengecualian yang tidak terkait dari pesan kesalahan
* Memperbaiki masalah dengan pesan kesalahan yang salah "Anda tidak memiliki izin yang diperlukan yang diperlukan untuk melakukan operasi ini." ketika diblokir oleh aturan jaringan atau AuthenticationFailed.

## <a name="november-4-2019"></a>4 November 2019

Versi 2.0.76

### <a name="acr"></a>ACR

* Menambahkan parameter `--pack-image-tag` pratinjau ke perintah `az acr pack build`.
* Menambahkan dukungan untuk mengaktifkan audit dalam membuat registri
* Menambahkan dukungan untuk RBAC cakupan Repositori

### <a name="aks"></a>AKS

* Ditambahkan `--enable-cluster-autoscaler`, `--min-count` dan `--max-count` ke `az aks create` perintah, yang memungkinkan autoscaler cluster untuk kumpulan node.
* Menambahkan bendera di atas serta `--update-cluster-autoscaler` dan `--disable-cluster-autoscaler` ke `az aks update` perintah, memungkinkan pembaruan untuk mengelompokkan autoscaler.

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan grup perintah fitur appconfig untuk mengelola bendera fitur yang disimpan dalam Konfigurasi Aplikasi.
* Memperbaiki bug kecil untuk appconfig kv export ke perintah file. Berhenti membaca isi file dest selama ekspor.

### <a name="appservice"></a>AppService

* `az appservice plan create`: Menambahkan dukungan untuk mengatur 'persitescaling' pada rencana layanan aplikasi.
* Memperbaiki masalah di mana operasi pengikat ssl konfigurasi webapp menghapus tag yang ada dari sumber daya
* Menambahkan `--build-remote` bendera untuk `az functionapp deployment source config-zip` mendukung tindakan build jarak jauh selama penerapan aplikasi fungsi.
* Mengubah versi node default pada aplikasi fungsi menjadi ~10 untuk Windows
* Menambahkan `--runtime-version` properti ke `az functionapp create`

### <a name="arm"></a>ARM

* `az deployment/group deployment validate`: Menambahkan `--handle-extended-json-format` parameter untuk mendukung multiline dan komentar dalam template json saat penyebaran.
* Bumped azure-mgmt-resource to 2019-07-01

### <a name="backup"></a>Cadangan

* Menambahkan dukungan pencadangan AzureFiles

### <a name="compute"></a>Compute

* `az vm create`: Peringatan tambahan saat menentukan jaringan yang dipercepat dan NIC yang ada bersama-sama.
* `az vm create`: Ditambahkan `--vmss` untuk menentukan set skala mesin virtual yang ada yang harus ditetapkan mesin virtual.
* `az vm/vmss create`: Menambahkan salinan gambar alias file lokal sehingga dapat diakses di lingkungan jaringan yang dibatasi.
* `az vmss create`: Ditambahkan `--orchestration-mode` untuk menentukan bagaimana mesin virtual dikelola oleh set skala.
* `az vm/vmss update`: Ditambahkan `--ultra-ssd-enabled` untuk memungkinkan pembaruan pengaturan ultra SSD.
* [BREAKING CHANGE] `az vm extension set`: Memperbaiki bug di mana pengguna tidak dapat mengatur ekstensi pada VM dengan `--ids`.
* Menambahkan perintah `az vm image terms accept/cancel/show` baru untuk mengelola istilah gambar Azure Marketplace.
* VMAccessForLinux yang diperbarui ke versi 1.5

### <a name="cosmosdb"></a>CosmosDB

* [BREAKING CHANGE] `az sql container create`: Diubah `--partition-key-path` menjadi parameter yang diperlukan
* [BREAKING CHANGE] `az gremlin graph create`: Diubah `--partition-key-path` menjadi parameter yang diperlukan
* `az sql container create`: Ditambahkan `--unique-key-policy` dan `--conflict-resolution-policy`
* `az sql container create/update`: Memperbarui `--idx` skema default
* `gremlin graph create`: Ditambahkan `--conflict-resolution-policy`
* `gremlin graph create/update`: Memperbarui `--idx` skema default
* Memperbaiki kesalahan ketik dalam pesan bantuan
* database: Menambahkan informasi deprekasi
* pengumpulan: Menambahkan informasi deprekasi

### <a name="iot"></a>IoT

* Menambahkan tipe sumber perutean baru: DigitalTwinChangeEvents
* Memperbaiki fitur yang hilang di `az iot hub create`

### <a name="key-vault"></a>Key Vault

* Memperbaiki kesalahan tak terduga saat berkas sertifikat tidak ada
* Tetap `az keyvault recover/purge` tidak berfungsi

### <a name="netappfiles"></a>NetAppFiles

* Upgrade azure-mgmt-netapp ke 0.6.0 untuk menggunakan API versi 2019-07-01. Versi API baru ini meliputi:

    - Pembuatan volume `--protocol-types` sekarang menerima "NFSv4.1" bukan "NFSv4"
    - Properti kebijakan ekspor volume sekarang bernama 'nfsv41' bukan 'nfsv4'
    - Volume `--creation-token` berganti nama menjadi `--file-path`
    - Tanggal pembuatan snapshot sekarang bernama hanya 'dibuat'

### <a name="network"></a>Jaringan

* `az network private-dns link vnet create/update`: Mendukung menghubungkan jaringan virtual lintas penyewa.
* [BREAKING CHANGE] `az network vnet subnet list`: Berubah `--resource-group` dan `--vnet-name` diperlukan sekarang.
* `az network public-ip prefix create`: Menambahkan dukungan untuk menentukan versi alamat IP (IPv4, IPv6) saat pembuatan
* Bumped azure-mgmt-network ke 7.0.0 dan api-version ke 2019-09-01
* `az network vrouter`: Menambahkan dukungan untuk router virtual layanan baru dan peering router virtual
* `az network express-route gateway connection`: Menambahkan dukungan untuk `--internet-security`

### <a name="profile"></a>Profil

* Tetap `az account get-access-token --resource-type ms-graph` tidak berfungsi
* Menghapus peringatan dari `az login`

### <a name="rbac"></a>RBAC

* Tetap `az ad app update --id {} --display-name {}` tidak berfungsi

### <a name="servicefabric"></a>ServiceFabric

* `az sf cluster create`: Memperbaiki masalah dengan memodifikasi kain layanan linux dan windows template.json menghitung vmss dari standar ke disk terkelola

### <a name="sql"></a>SQL

* Ditambahkan`--compute-model`, `--auto-pause-delay`, dan `--min-capacity` parameter untuk mendukung operasi CRUD untuk penawaran SQL Database baru: Model komputasi tanpa server.

### <a name="storage"></a>Penyimpanan

* `az storage account create/update`: Menambahkan parameter --enable-files-adds dan Azure Active Directory grup Properties Argument untuk mendukung Autentikasi Layanan Domain Direktori Aktif Azure Files
* Diperluas `az storage account keys list/renew` untuk mendukung daftar atau regenerasi kunci akun penyimpanan Kerberos.

## <a name="october-15-2019"></a>15 Oktober 2019 pukul

Versi 2.0.75

### <a name="aks"></a>AKS

* Mengubah `--load-balancer-sku` nilai default menjadi `standard` jika didukung oleh versi kubernetes
* Mengubah `--vm-set-type` nilai default menjadi `virtualmachinescalesets` jika didukung oleh versi kubernetes

### <a name="ams"></a>AMS

* [MELANGGAR PERUBAHAN] Mengubah nama `job start` menjadi `job create`
* [MELANGGAR PERUBAHAN] `--ask` Mengubah parameter `content-key-policy create` untuk menggunakan string hex 32 karakter alih-alih UTF8

### <a name="appservice"></a>AppService

* Perintah tambahan `webapp config access-restriction show|set|add|remove`
* Menambahkan penanganan kesalahan yang lebih baik ke `webapp up`
* Menambahkan dukungan untuk `Isolated` SKU ke `appservice plan update`

### <a name="arm"></a>ARM

* Menambahkan `--handle-extended-json-format` parameter `deployment create` untuk mendukung multiline dan komentar dalam template json

### <a name="compute"></a>Compute

* Menambahkan `--enable-agent` parameter ke `vm create`
* Diubah `vm create` untuk menggunakan SKU IP publik standar secara otomatis saat menggunakan zona
* Diubah `vm create` untuk secara otomatis membuat nama komputer yang valid untuk VM jika tidak ada yang disediakan
* Menambahkan `--computer-name-prefix` parameter untuk `vmss create` mendukung awalan nama komputer kustom mesin virtual di VMSS
* Menambahkan `--workspace` parameter untuk `vm create` mengaktifkan ruang kerja analitik log secara otomatis
* Galeri api versi yang diperbarui ke 2019-07-01

### <a name="core"></a>Core

* Menambahkan pemeriksaan sintaks untuk `--set` parameter dalam perintah pembaruan generik

### <a name="iot"></a>IoT

* Memperbaiki masalah di mana `iot hub show` kesalahan yang salah dengan "sumber daya tidak ditemukan"

### <a name="monitor"></a>Monitor

* Menambahkan dukungan untuk CRUD ke `monitor log-analytics workspace`

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk penautan virtual lintas penyewa ke `network private-dns link vnet [create|update]`
* [MELANGGAR PERUBAHAN] Diubah `network vnet subnet list` menjadi memerlukan `--resource-group` dan `--vnet-name` parameter

### <a name="sql"></a>SQL

* Menambahkan perintah ke `sql mi ad-admin` dukungan yang mengatur administrator AAD pada instans terkelola

### <a name="storage"></a>Penyimpanan

* Parameter tambahan `--preserve-s2s-access-tier` `storage copy` untuk mempertahankan tingkat akses selama layanan ke salinan layanan
* Menambahkan `--enable-large-file-share` parameter untuk `storage account [create|update]` mendukung berbagi file besar untuk akun penyimpanan

## <a name="september-24-2019"></a>24 September 2019 pukul

Versi 2.0.74

### <a name="acr"></a>ACR

* Menambahkan parameter yang diperlukan `--type` ke `acr config retention update`
* [MELANGGAR PERUBAHAN] Parameter `--name -n` yang diganti namanya diubah menjadi `--registry -r ` untuk `acr config` grup perintah

### <a name="aks"></a>AKS

* Menambahkan `--load-balancer-sku` parameter ke `aks create` perintah, yang memungkinkan untuk membuat cluster AKS dengan SLB
* Ditambahkan `--load-balancer-managed-outbound-ip-count`, `--load-balancer-outbound-ips` dan `--load-balancer-outbound-ip-prefixes` parameter ke `aks [create|update]` perintah, yang memungkinkan untuk memperbarui profil penyeimbang beban dari cluster AKS dengan SLB
* Menambahkan `--vm-set-type` parameter ke `aks create` perintah, yang memungkinkan menentukan jenis vm dari Cluster AKS (vmas atau vmss)

### <a name="arm"></a>ARM

* Menambahkan `--handle-extended-json-format` parameter ke `group deployment create` perintah untuk mendukung multiline dan komentar dalam template json

### <a name="compute"></a>Compute

* Menambahkan `--terminate-notification-time` parameter ke `vmss [create|update]` perintah untuk mendukung penghentian konfigurasi peristiwa terjadwal
* Menambahkan `--enable-terminate-notification` parameter ke `vmss update` perintah untuk mendukung penghentian konfigurasi peristiwa terjadwal
* Menambahkan `--priority,` `--eviction-policy,` `--max-billing` parameter ke `[vm|vmss] create` perintah
* Diubah `disk create` untuk memungkinkan menentukan ukuran yang tepat dari upload disk
* Menambahkan dukungan untuk snapshot inkremental untuk disk terkelola ke `snapshot create`

### <a name="cosmos-db"></a>Cosmos DB

* Menambahkan `--type <key-type>` parameter ke `cosmosdb keys list` perintah untuk menampilkan kunci, hanya membaca tombol atau string koneksi
* Perintah tambahan `cosmosdb keys regenerate`
* [USANG] `cosmosdb list-connection-strings`Usang, `cosmosdb regenerate-key` dan `cosmosdb list-read-only-keys` perintah

### <a name="eventgrid"></a>EventGrid

* Memperbaiki teks bantuan titik akhir untuk merujuk ke parameter yang tepat

### <a name="key-vault"></a>Key Vault

* Memperbaiki masalah saat masuk dengan penyewa (`login -t`) dapat menyebabkan `keyvault create` gagal

### <a name="monitor"></a>Monitor

* Memperbaiki masalah di mana `:` karakter tidak diizinkan dalam `--condition` argumen untuk `monitor metrics alert create`

### <a name="policy"></a>Kebijakan

* Menambahkan dukungan untuk Api Kebijakan versi 2019-06-01
* Menambahkan `--enforcement-mode` parameter ke `policy assignment create` perintah

### <a name="storage"></a>Penyimpanan

* Menambahkan `--blob-type` parameter ke `az storage copy` perintah

## <a name="september-10-2019"></a>10 September 2019 pukul

### <a name="acr"></a>ACR

* Menambahkan grup `acr config retention` perintah untuk mengonfigurasi kebijakan retensi

### <a name="aks"></a>AKS

* Menambahkan dukungan untuk integrasi ACR dengan perintah berikut:
  * Menambahkan `--attach-acr` parameter untuk `aks [create|update]` melampirkan ACR ke klaster AKS
  * Menambahkan `--detach-acr` parameter untuk `aks update` melepaskan ACR dari klaster AKS

### <a name="arm"></a>ARM

* Diperbarui untuk menggunakan API versi 2019-05-10

### <a name="batch"></a>Batch

* Menambahkan pengaturan konfigurasi JSON baru untuk `--json-file` `batch pool create`:
  * Ditambahkan `MountConfigurations` untuk dudukan sistem file (lihat [Meminta Badan](/rest/api/batchservice/pool/add#request-body) untuk detailnya)
  * Menambahkan properti `publicIPs` `NetworkConfiguration` opsional untuk IP publik di kumpulan (lihat [Meminta Badan](/rest/api/batchservice/pool/add#request-body) untuk detailnya)
* Menambahkan dukungan untuk galeri gambar bersama ke `--image`
* [MELANGGAR PERUBAHAN] Mengubah nilai `--start-task-wait-for-success` `batch pool create` default untuk menjadi `true`
* [MELANGGAR PERUBAHAN] Mengubah nilai default untuk `Scope` `AutoUserSpecification` selalu menjadi Pool (berada `Task` di Windows node, `Pool` pada node Linux)
  * Argumen ini hanya dapat diatur dari konfigurasi JSON dengan `--json-file`

### <a name="hdinsight"></a>HDInsight

* Rilis GA
* [MELANGGAR PERUBAHAN] Parameter `--workernode-count/-c` yang `az hdinsight resize` diubah diperlukan.

### <a name="key-vault"></a>Key Vault

* Memperbaiki masalah di mana subnet tidak dapat dihapus dari aturan jaringan
* Memperbaiki masalah di mana subnet duplikat dan alamat IP dapat ditambahkan ke aturan jaringan

### <a name="network"></a>Jaringan

* Menambahkan `--interval` parameter untuk `network watcher flow-log` mengatur nilai interval analisis lalu lintas
* Ditambahkan `network application-gateway identity` untuk mengelola identitas gateway
* Menambahkan dukungan untuk mengatur Key Vault ID ke `network application-gateway ssl-cert`
* Ditambahkan `network express-route peering peer-connection [show|list]`

### <a name="policy"></a>Kebijakan

* Diperbarui untuk menggunakan API versi 2019-01-01

## <a name="august-27-2019"></a>27 Agustus 2019 pukul

Versi 2.0.72

### <a name="acr"></a>ACR

* [MELANGGAR PERUBAHAN] Menghapus dukungan untuk `classic` SKU

### <a name="api-management"></a>API Management

* [PRATINJAU] Grup perintah tambahan `apim`

### <a name="appservice"></a>AppService

* Memperbaiki masalah dengan `webapp webjob continuous start` perintah saat menentukan slot
* Diubah `webapp up` untuk mendeteksi `env` folder dan menghapusnya dari file yang digunakan untuk penyebaran

### <a name="keyvault"></a>Keyvault

* Memperbaiki bug dalam `keyvault secret set` argumen igored `--expires`

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk alamat IPv6 ke `--private-ip-address-version` argumen
* Menambahkan perintah `network private-endpoint [create|update|list-types]` baru untuk manajemen titik akhir pribadi
* Grup perintah tambahan `network private-link-service`
* Ditambahkan `--private-endpoint-network-policies` dan `--private-link-service-network-policies` argumen untuk `network vnet subnet update`

### <a name="rbac"></a>RBAC

* Memperbaiki masalah dengan `ad app update --homepage` tempat beranda tidak akan diperbarui

### <a name="servicefabric"></a>ServiceFabric

* Menambahkan dukungan untuk nama Key Vault kasus campuran
* Memperbaiki masalah saat menggunakan sertifikat di Key Vault
* Memperbaiki masalah dengan menggunakan file sertifikat PFX
* Memperbaiki masalah saat `sf cluster certificate add` grup sumber daya Key Vault tidak ditentukan
* Memperbaiki masalah dengan `sf cluster set` tidak berfungsi

### <a name="signalr"></a>SignalR

* Menambahkan perintah baru:
  * `signalr cors`: Kelola Signalr CORS
  * `signalr restart`: Mulai ulang layanan SignalR
  * `signalr update`: Memperbarui layanan SignalR
* Menambahkan `--service-mode` argumen ke `signalr create`

### <a name="storage"></a>Penyimpanan

* Perintah tambahan `storage account revoke-delegation-keys`

## <a name="august-13-2019"></a>13 Agustus 2019 pukul

Versi 2.0.71

### <a name="appservice"></a>AppService

* Memperbaiki masalah di mana `webapp webjob continuous` perintah gagal untuk slot

### <a name="botservice"></a>BotService

* [MELANGGAR PERUBAHAN] Menghapus dukungan untuk membuat bot SDK v3

### <a name="cognitiveservices"></a>Layanan Kognitif

* Perintah `cognitiveservices account network-rule` tambahan

### <a name="cosmos-db"></a>Cosmos DB

* Peringatan yang dihapus saat memperbarui beberapa lokasi penulisan
* Menambahkan perintah CRUD untuk SQL CosmosDB, MongoDB, Cassandra, Gremlin dan Table sumber daya dan throughput sumber daya

### <a name="hdinsight"></a>HDInsight

Rilis ini berisi sejumlah besar perubahan yang melanggar.

* [MELANGGAR PERUBAHAN] Parameter yang diganti namanya untuk `hdinsight create`:
  * Berganti `--storage-default-container` nama menjadi `--storage-container`
  * Berganti `--storage-default-filesystem` nama menjadi `--storage-filesystem`
* [MELANGGAR PERUBAHAN] `--name` Mengubah argumen `application create` untuk mewakili nama aplikasi alih-alih nama klaster
* Menambahkan `--cluster-name` argumen untuk `application create` menggantikan fungsionalitas lama `--name`
* [MELANGGAR PERUBAHAN] Parameter yang diganti namanya untuk `application create`:
  * Berganti `--application-type` nama menjadi `--type`
  * Berganti `--marketplace-identifier` nama menjadi `--marketplace-id`
  * Berganti `--https-endpoint-access-mode` nama menjadi `--access-mode`
  * Berganti  `--https-endpoint-destination-port` nama menjadi `--destination-port`
* [MELANGGAR PERUBAHAN] Parameter yang dihapus untuk `application create`:
  * `--https-endpoint-location`
  * `--https-endpoint-public-port`
  * `--ssh-endpoint-destination-port`
  * `--ssh-endpoint-location`
  * `--ssh-endpoint-public-port`
* [MELANGGAR CHNAGE] Berganti `--target-instance-count` nama menjadi `--workernode-count` untuk `hdinsight resize`
* [MELANGGAR PERUBAHAN] Mengubah semua perintah dalam `hdinsight script-action` grup untuk menggunakan `--name` parameter sebagai nama tindakan skrip.
* Menambahkan `--cluster-name` argumen ke semua `hdinsight script-action` perintah untuk menggantikan fungsionalitas lama `--name`
* [MELANGGAR PERUBAHAN] Diganti `--script-execution-id` namanya menjadi `--execution-id` untuk semua `hdinsight script-action` perintah
* [MELANGGAR PERUBAHAN] Berganti `hdinsight script-action show` nama menjadi `hdinsight script-action show-execution-details`
* [MELANGGAR CHNAGE] Parameter `hdinsight script-action execute --roles` yang diubah menjadi terpisah spasi alih-alih comma-separated
* [MELANGGAR PERUBAHAN] `--persisted` Menghapus parameter dari `hdinsight script-action list`
* `hdinsight create --cluster-configurations` Mengubah parameter untuk menerima jalur ke file JSON lokal atau string JSON
* Perintah tambahan `hdinsight script-action list-execution-history`
* Diubah `hdinsight monitor enable --workspace` untuk menerima ID ruang kerja Log Analytics atau nama ruang kerja
* `hdinsight monitor enable --primary-key` Menambahkan argumen, yang diperlukan jika ID ruang kerja disediakan sebagai parameter
* Menambahkan lebih banyak contoh dan deskripsi yang diperbarui untuk pesan bantuan

### <a name="interactive"></a>Interaktif

* Memperbaiki kesalahan pemuatan

### <a name="kubernetes"></a>Kubernetes

* Diubah untuk digunakan `https` jika port kontainer dasbor menggunakan `https`

### <a name="network"></a>Jaringan

* Argumen tambahan `--yes``network dns record-set cname delete`

### <a name="profile"></a>Profil

* Menambahkan `--resource-type` argumen untuk `account get-access-token` mendapatkan token akses sumber daya

### <a name="servicefabric"></a>ServiceFabric

* Menambahkan semua versi os yang didukung untuk pembuatan klaster sf
* Memperbaiki bug validasi sertifikat utama

### <a name="storage"></a>Penyimpanan

* Perintah tambahan `storage copy`

## <a name="july-30-2019"></a>30 Juli 2019 pukul

Versi 2.0.70

### <a name="acr"></a>ACR

* Memperbaiki masalah #9952 (regresi dalam `acr pack build` perintah)
* Menghapus nama gambar penyusun default di `acr pack build`

### <a name="appservice"></a>Layanan aplikasi

* Diubah `webapp config ssl` untuk menampilkan pesan jika sumber daya tidak ditemukan
* Memperbaiki masalah jika `functionapp create` tidak menerima `Standard_RAGRS` jenis akun penyimpanan
* Memperbaiki masalah di mana `webapp up` akan gagal jika dijalankan menggunakan versi python yang lebih lama

### <a name="network"></a>Jaringan

* Menghapus parameter `--ids` tidak valid dari `network nic ip-config add` (memperbaiki #9861)
* Memperbaiki # 9604. Menambahkan `--root-certs` parameter untuk `network application-gateway http-settings [create|update]` mendukung sertifikat root tepercaya rekan pengguna.
* Argumen tetap `--subscription` untuk `network dns record-set ns create` (#9965)

### <a name="rbac"></a>RBAC

* Perintah tambahan `user update`
* [USANG] Tidak digunakan `--upn-or-object-id` lagi dari perintah terkait pengguna
    * Menggunakan argumen pengganti `--id`
* Menambahkan `--id` argumen ke perintah terkait pengguna

### <a name="sql"></a>SQL

* Menambahkan perintah manajemen untuk kunci instans terkelola dan pelindung TDE

### <a name="storage"></a>Penyimpanan

* Perintah tambahan `storage remove`
* Memperbaiki masalah dengan `storage blob update`

### <a name="vm"></a>VM

* Diubah `list-skus` untuk menggunakan versi api yang lebih baru ke detail zona output
* Mengubah default `--single-placement-group` menjadi `false` untuk `vmss create`
* Menambahkan kemampuan untuk memilih SKU penyimpanan ZRS untuk `[snapshot|disk] create`
* Menambahkan grup `vm host` perintah baru untuk mendukung host khusus
* Menambahkan parameter `--host` dan `--host-group` untuk `vm create` mengatur host khusus VM

## <a name="july-16-2019"></a>16 Juli 2019 pukul

Versi 2.0.69

### <a name="appservice"></a>Layanan aplikasi

* Perintah `webapp identity` yang diubah untuk mengembalikan pesan kesalahan yang tepat jika Nama ResourceGroupName atau Nama aplikasi tidak valid
* Diperbaiki `webapp list` untuk mengembalikan nilai yang benar untuk numberOfSites jika tidak ada ResourceGroup yang disediakan
* Efek samping tetap dari `appservice plan create` dan `webapp create`

### <a name="core"></a>Core

* Memperbaiki masalah di mana `--subscription` akan muncul meskipun tidak berlaku

### <a name="batch"></a>Batch

* [MELANGGAR PERUBAHAN] Diganti `batch pool node-agent-skus list` dengan `batch pool supported-images list`
* Menambahkan dukungan untuk aturan keamanan yang memblokir akses jaringan ke kumpulan berdasarkan port sumber lalu lintas saat menggunakan `--json-file` opsi `batch pool create network`
* Menambahkan dukungan untuk menjalankan tugas di direktori kerja kontainer atau di direktori kerja tugas Batch saat `--json-file` menggunakan opsi `batch task create`
* Memperbaiki kesalahan dalam opsi `batch pool create` di `--application-package-references` mana itu hanya akan berfungsi dengan default

### <a name="eventhubs"></a>Eventhubs

* Validasi tambahan untuk parameter `--rights` `authorizationrule` perintah

### <a name="rdbms"></a>RDBMS

* Menambahkan parameter opsional untuk menentukan replika SKU untuk membuat perintah replika
* Memperbaiki masalah dengan kegagalan pengujian CI dengan membuat replika MySQL

### <a name="relay"></a>Relay

* Memperbaiki masalah dengan koneksi hibrid saat authroization klien dinonaktifkan [#8775](https://github.com/azure/azure-cli/issues/8775)
* Menambahkan parameter `--requires-transport-security` ke `relay wcfrelay create`

### <a name="servicebus"></a>Bus layanan

* Validasi tambahan untuk parameter `--rights` `authorizationrule` perintah

### <a name="storage"></a>Penyimpanan

* Aktifkan File AADDS untuk pembaruan akun penyimpanan
* Memperbaiki masalah `storage blob service-properties update --set`

## <a name="july-2-2019"></a>2 Juli 2019

Versi 2.0.68

### <a name="core"></a>Core

* Modul perintah sekarang dikonsolidasikan menjadi satu Python yang dapat didistribusikan. Ini mendepresiasi penggunaan langsung banyak `azure-cli-` paket di PyPI.
  Ini harus mengurangi ukuran pemasangan dan hanya memengaruhi pengguna yang telah langsung diinstal melalui `pip`.

### <a name="acr"></a>ACR

* Menambahkan dukungan untuk Pemicu Timer ke Tugas

### <a name="appservice"></a>Layanan aplikasi

* Diubah `functionapp create` untuk mengaktifkan insight aplikasi secara default
* [MELANGGAR PERUBAHAN] Menghapus perintah yang `functionapp devops-build` tidak digunakan lagi.
  *  Gunakan perintah `az functionapp devops-pipeline` baru sebagai gantinya
* Menambahkan dukungan paket aplikasi fungsi Konsumsi Linux ke `functionapp deployment config-zip`

### <a name="cosmos-db"></a>Cosmos DB

* Menambahkan dukungan untuk menonaktifkan TTL

### <a name="dls"></a>DLS

* Versi ADLS yang diperbarui (0.0.45)

### <a name="feedback-reference"></a>Referensi umpan balik

* Saat melaporkan perintah ekstensi yang gagal, `az feedback` sekarang coba buka browser ke url project/repo ekstensi dari indeks

### <a name="hdinsight"></a>HDInsight

* [MELANGGAR PERUBAHAN] Mengubah `oms` nama grup perintah menjadi `monitor`
* [MELANGGAR PERUBAHAN] Membuat `--http-password/-p` parameter yang diperlukan
* Menambahkan completers untuk `--cluster-admin-account` dan `cluster-users-group-dns` parameter completer
* Parameter `cluster-users-group-dns` yang diubah diperlukan saat `—esp` ada
* Menambahkan batas waktu untuk semua penje bundaran otomatis argumen yang ada
* Menambahkan batas waktu untuk mengubah nama sumber daya ke id sumber daya
* Mengubah Penjekan Otomatis untuk memilih sumber daya dari grup sumber daya apa pun. Ini bisa menjadi kelompok sumber daya yang berbeda dari yang ditentukan dengan `-g`
* Menambahkan dukungan dan `--sub-domain-suffix` `--disable_gateway_auth` parameter dalam `hdinsight application create` perintah

### <a name="managed-services"></a>Layanan Terkelola

* Memperkenalkan modul perintah layanan terkelola dalam pratinjau

### <a name="profile"></a>Profil
* Menekan `--subscription` argumen untuk perintah logout

### <a name="rbac"></a>RBAC

* [MELANGGAR PERUBAHAN] Argumen yang dihapus `--password` untuk `create-for-rbac`
* Menambahkan `--assignee-principal-type` parameter ke `create` perintah untuk menghindari kegagalan intermiten yang disebabkan oleh latensi replikasi server grafik AAD
* Memperbaiki kerusakan saat `ad signed-in-user` mencantumkan objek yang dimiliki
* Memperbaiki masalah di mana `ad sp` tidak akan menemukan aplikasi yang tepat dari prinsipal layanan

### <a name="rdbms"></a>RDBMS

* Menambahkan dukungan untuk replikasi untuk MariaDB

### <a name="sql"></a>SQL

* Nilai yang diizinkan didokumentasikan untuk `sql db create --sample-name`

### <a name="storage"></a>Penyimpanan

* Menambahkan delegasi pengguna dukungan token SAS dengan `--as-user` ke `storage blob generate-sas`
* Menambahkan delegasi pengguna dukungan token SAS dengan `--as-user` ke `storage container generate-sas`

### <a name="vm"></a>VM

* Memperbaiki bug di mana `vmss create` mengembalikan pesan kesalahan saat dijalankan dengan `--no-wait`
* Menghapus validasi sisi klien untuk `vmss create --single-placement-group`. Tidak gagal jika `--single-placement-group` diatur ke `true` dan`--instance-count` lebih besar dari 100 atau zona ketersediaan ditentukan, tetapi meninggalkan validasi ini ke layanan komputasi
* Memperbaiki bug jika `[vm|vmss] extension image list` gagal saat digunakan dengan `--latest`


## <a name="june-18-2019"></a>18 Juni 2019 pukul

Versi 2.0.67

### <a name="core"></a>Core

Rilis ini memperkenalkan tag [Pratinjau] baru untuk berkomunikasi lebih jelas kepada pelanggan ketika grup perintah, perintah, atau argumen berada dalam status pratinjau. Ini sebelumnya dipanggil dalam teks bantuan atau dikomunikasikan secara implisit oleh nomor versi modul perintah.
CLI akan menghapus nomor versi untuk paket individual di masa depan. Jika perintah sedang dalam pratinjau, semua argumennya juga. Jika grup perintah diberi label sebagai pratinjau, maka semua perintah dan argumen dianggap dalam pratinjau juga.

Sebagai hasil dari perubahan ini, beberapa grup perintah mungkin tampak "tiba-tiba" tampak dalam status pratinjau dengan rilis ini. Apa yang sebenarnya terjadi adalah bahwa sebagian besar paket berada dalam status pratinjau, tetapi dianggap GA dengan rilis ini.

### <a name="acr"></a>ACR
* Menambahkan perintah 'acr check-health'
* Penanganan kesalahan yang ditingkatkan untuk token AAD dan untuk mengambil perintah eksternal

### <a name="acs"></a>ACS
* Perintah ACS yang tidak digunakan lagi sekarang disembunyikan dari tampilan bantuan

### <a name="ams"></a>AMS
* [MELANGGAR PERUBAHAN] Diubah untuk mengembalikan string waktu ISO 8601 untuk panjang arsip-jendela dan durasi interval bingkai kunci

### <a name="appservice"></a>AppService
* Menambahkan perutean berbasis lokasi untuk `webapp deleted list` dan `webapp deleted restore`
* Memperbaiki masalah saat webapp up url target yang dicatat ("Anda dapat meluncurkan aplikasi di ...") tidak dapat diklik di Azure Cloud Shell
* Memperbaiki masalah saat membuat aplikasi dengan beberapa SKU gagal dengan kesalahan AlwaysOn
* Menambahkan pra-validasi ke `[appservice|webapp] create`
* Diperbaiki `[webapp|functionapp] traffic-routing` untuk menggunakan actionHostName yang benar
* Menambahkan dukungan slot ke `functionapp` perintah

### <a name="batch"></a>Batch
* Memperbaiki regresi auth AAD yang disebabkan oleh pelaporan kesalahan yang terlalu agresif untuk Auth Kunci Bersama

### <a name="batchai"></a>BatchAI
* Perintah BatchAI sekarang tidak digunakan lagi dan disembunyikan

### <a name="botservice"></a>BotService
* Menambahkan pesan peringatan "dukungan yang dihentikan"/"mode pemeliharaan" untuk perintah yang mendukung SDK v3

### <a name="cosmosdb"></a>CosmosDB
* [USANG] Tidak digunakan `cosmosdb list-keys` lagi perintah
* `cosmosdb keys list` Menambahkan perintah - menggantikan`cosmosdb list-keys`
* `cosmsodb create/update`: Menambahkan format baru untuk --location untuk memungkinkan pengaturan properti "isZoneRedundant". Format lama yang tidak digunakan lagi

### <a name="eventgrid"></a>EventGrid
* Menambahkan `eventgrid domain` perintah untuk operasi CRUD domain
* Perintah tambahan `eventgrid domain topic` untuk topik domain operasi CRUD
* Menambahkan `--odata-query` argumen untuk `eventgrid [topic|event-subscription] list` memfilter hasil menggunakan sintaks OData
* `event-subscription create/update`: Menambahkan servicebusqueue sebagai nilai baru untuk `--endpoint-type` parameter
* [MELANGGAR PERUBAHAN] Menghapus dukungan untuk `--included-event-types All` dengan `eventgrid event-subscription [create|update]`

### <a name="hdinsight"></a>HDInsight
* Menambahkan dukungan untuk `--ssh-public-key` parameter dalam `hdinsight create` perintah

### <a name="iot"></a>IoT
* Menambahkan dukungan untuk meregenerasi kunci kebijakan otorisasi
* Menambahkan SDK dan dukungan untuk Layanan Penyediaan Repositori DigitalTwin

### <a name="network"></a>Jaringan
* Menambahkan dukungan Zona untuk Nat Gateway
* Perintah tambahan `network list-service-tags`
* Memperbaiki masalah dengan `dns zone import` tempat pengguna tidak dapat mengimpor wildcard Catatan A
* Memperbaiki masalah dengan `watcher flow-log configure` di mana pembuatan log alur tidak dapat diaktifkan di wilayah tertentu

### <a name="resource"></a>Sumber daya
* Perintah tambahan `az rest` untuk melakukan panggilan REST
* Memperbaiki kesalahan saat menggunakan `policy assignment list` dengan grup sumber daya atau tingkat langganan `--scope`

### <a name="servicebus"></a>ServiceBus
* Memperbaiki masalah dengan `servicebus topic create --max-size` [#9319](https://github.com/azure/azure-cli/issues/9319)

### <a name="sql"></a>SQL
* Diubah `--location` menjadi opsional untuk `sql [server|mi] create` - menggunakan lokasi grup sumber daya jika tidak ditentukan
* Memperbaiki kesalahan "'NoneType' tidak dapat ditemukan" untuk `sql db list-editions --available`

### <a name="sqlvm"></a>SQLVm
* [MELANGGAR CHNAGE] Diubah `sql vm create` menjadi parameter `--license-type`
* Diubah untuk memungkinkan pengaturan SQL gambar SKU saat membuat atau memperbarui vm sql

### <a name="storage"></a>Penyimpanan
* Memperbaiki masalah dengan kunci akun yang hilang untuk `storage container generate-sas`
* Memperbaiki masalah dengan `storage blob sync` Linux

### <a name="vm"></a>VM
* [PRATINJAU] Menambahkan `vm image template` perintah untuk membuat gambar VM

## <a name="june-4-2019"></a>4 Juni 2019 pukul

Versi 2.0.66

### <a name="core"></a>Core
* Memperbaiki bug di mana perintah gagal jika `--output yaml` digunakan dengan `--query`

### <a name="acr"></a>ACR
* Menambahkan grup perintah 'acr pack' untuk membuat Tugas build cepat menggunakan Buildpacks.

### <a name="acs"></a>ACS
* Izinkan mengaktifkan/menonaktifkan addon kube-dashboard AKS
* Mencetak pesan ramah saat langganan tidak disetujui untuk menggunakan Azure Red Hat OpenShift

### <a name="batch"></a>Batch
* Penanganan kesalahan yang ditingkatkan saat tidak masuk ke akun \[[#9165](https://github.com/Azure/azure-cli/issues/9165)\]\[[#8978](https://github.com/Azure/azure-cli/issues/8978)\]

### <a name="iot"></a>IoT
* Menambahkan dukungan untuk failover manual

### <a name="network"></a>Jaringan
* Menambahkan `network application-gateway waf-policy` perintah untuk mendukung aturan WAF kustom.
* Ditambahkan `--waf-policy` dan `--max-capacity` argumen untuk `network application-gateway [create|update]`

### <a name="resource"></a>Sumber daya
* Pesan kesalahan yang ditingkatkan dari `deployment create` saat tidak ada TTY yang tersedia

### <a name="role"></a>Peran
* Teks bantuan yang diperbarui.

### <a name="compute"></a>Compute
* Menambahkan dukungan untuk `vm create` VM dari gambar terkelola dengan luns disk data yang tidak dimulai dari 0 atau yang melewati angka

## <a name="may-21-2019"></a>21 Mei 2019 pukul

Versi 2.0.65

### <a name="core"></a>Core
* Menambahkan umpan balik yang lebih baik untuk kesalahan autentikasi
* Memperbaiki masalah di mana CLI akan memuat ekstensi yang tidak kompatibel dengan versi intinya
* Memperbaiki masalah dengan meluncurkan kapan `clouds.config` rusak

### <a name="acr"></a>ACR
* Menambahkan dukungan untuk Identitas Terkelola ke Tugas

### <a name="acs"></a>ACS
* Perintah tetap `openshift create` saat digunakan dengan klien AAD pelanggan

### <a name="appservice"></a>AppService
* [USANG] Perintah yang `functionapp devops-build` tidak digunakan lagi - akan dihapus dalam rilis berikutnya
* Diubah `functionapp devops-pipeline` untuk mengambil log build dari Azure DevOps dalam mode verbose
* [MELANGGAR PERUBAHAN] Bendera yang dihapus `--use_local_settings` dari `functionapp devops-pipeline` perintah - adalah no-op
* Diubah `webapp up` untuk mengembalikan output JSON jika `--logs` tidak digunakan
* Menambahkan dukungan untuk menulis sumber daya default ke konfigurasi lokal untuk `webapp up`
* Menambahkan dukungan untuk `webapp up` memindahkan aplikasi tanpa menggunakan `--location` argumen
* Memperbaiki masalah di mana untuk Linux Gratis SKU ASP penggunaan Gratis sebagai nilai SKU tidak bekerja

### <a name="botservice"></a>BotService
* Diubah untuk memungkinkan semua casing untuk `--lang` parameter untuk perintah
* Deskripsi yang diperbarui untuk modul perintah

### <a name="consumption"></a>Consumption
* Menambahkan parameter yang diperlukan hilang saat menjalankan `consumption usage list --billing-period-name`

### <a name="iot"></a>IoT
* Menambahkan dukungan untuk mencantumkan semua kunci

### <a name="network"></a>Jaringan
* [MELANGGAR PERUBAHAN]: Removed `network interface-endpoints` command group - use `network private-endpoints`
* Menambahkan `--nat-gateway` argumen untuk `network vnet subnet [create|update]` melampirkan ke gateway NAT
* Memperbaiki masalah dengan `dns zone import` tempat nama rekaman tidak bisa menandingi jenis rekaman

### <a name="rdbms"></a>RDBMS
* Menambahkan dukungan postgres dan mysql untuk replikasi geografis

### <a name="rbac"></a>RBAC
* Menambahkan dukungan untuk lingkup grup manajemen ke `role assignment`

### <a name="storage"></a>Penyimpanan
* `storage blob sync`: tambahkan perintah sinkronisasi untuk blob penyimpanan

### <a name="compute"></a>Compute
* Ditambahkan `--computer-name` ke `vm create` untuk mengatur nama komputer VM
* Berganti `--ssh-key-value` nama menjadi `--ssh-key-values` `[vm|vmss] create` - sekarang dapat menerima beberapa nilai atau jalur kunci publik ssh
  * __Catatan__: Ini **bukan** perubahan yang melanggar - `--ssh-key-value` akan diurai dengan benar karena hanya cocok `--ssh-key-values`
* `--type` Mengubah argumen `ppg create` menjadi opsional

## <a name="may-6-2019"></a>6 Mei 2019 pukul

Versi 2.0.64

### <a name="acs"></a>ACS
* [MELANGGAR PERUBAHAN] Menghapus `--fqdn` bendera pada `openshift` perintah
* Diubah untuk menggunakan Azure Red Hat Openshift GA API Version
* Menambahkan `customer-admin-group-id` bendera ke `openshift create`
* [GA] Dihapus `(PREVIEW)` dari `aks create` opsi `--network-policy`

### <a name="appservice"></a>Layanan aplikasi
* [USANG] Perintah yang `functionapp devops-build` tidak digunakan lagi
  * Berganti nama menjadi `functionapp devops-pipeline`
* Memperbaiki mendapatkan nama pengguna yang benar untuk cloudshell yang menyebabkan `webapp up` gagal
* Dokumentasi `appservice plan --sku` yang diperbarui diperbarui untuk mencerminkan rencana layanan aplikasi yang didukung
* Menambahkan argumen opsional untuk grup sumber daya dan berencana `webapp up`
* Menambahkan dukungan untuk `webapp ssh` menghormati `AZURE_CLI_DISABLE_CONNECTION_VERIFICATION` variabel lingkungan
* Menambahkan `appserviceplan create` dukungan untuk Linux Free SKU
* Diubah `webapp up` untuk tidur 30-an setelah mengatur `SCM_DO_BUILD_DURING_DEPLOYMENT=true` appsetting untuk menangani awal dingin kudu
* Menambahkan dukungan untuk `powershell` runtime ke `functionapp create` Windows
* Perintah tambahan `create-remote-connection`

### <a name="batch"></a>Batch
* Memperbaiki bug di validator untuk `--application-package-references` opsi

### <a name="botservice"></a>Botservice
* [MELANGGAR PERUBAHAN] Diubah `bot create -v v4 -k webapp` untuk membuat Bot Aplikasi Web kosong secara default (yaitu tidak ada bot yang digunakan ke App Service)
* Menambahkan `--echo` bendera untuk `bot create` menggunakan perilaku lama dengan `-v v4`
* [MELANGGAR PERUBAHAN] Mengubah nilai  `--version` default menjadi `v4`
  * __NOTA:__ `bot prepare-publish` masih menggunakan default lamanya
* [MELANGGAR PERUBAHAN] Diubah `--lang` menjadi tidak lagi default ke `Csharp`. Jika perintah membutuhkan `--lang` dan tidak disediakan, perintah sekarang akan error keluar
* [MELANGGAR PERUBAHAN] `--appid` Mengubah dan `--password` args untuk `bot create` diperlukan dan sekarang dapat dibuat melalui `ad app create`
* Ditambahkan `--appid` dan `--password` validasi
* [MELANGGAR PERUBAHAN] Diubah `bot create -v v4` agar tidak membuat atau menggunakan akun Storage atau aplikasi Insights
* [MELANGGAR PERUBAHAN] Diubah `bot create -v v3` untuk memerlukan wilayah tempat Insights Aplikasi tersedia
* [MELANGGAR PERUBAHAN] Diubah `bot update` menjadi sekarang hanya memengaruhi properti tertentu dari bot
* [MELANGGAR PERUBAHAN] Mengubah `--lang` bendera untuk diterima `Javascript` alih-alih `Node`
* [MELANGGAR PERUBAHAN] Dihapus `Node` sebagai nilai yang diizinkan `--lang`
* [MELANGGAR PERUBAHAN] Diubah `bot create -v v4 -k webapp` menjadi tidak lagi diatur `SCM_DO_BUILD_DURING_DEPLOYMENT` ke benar. Semua penyebaran melalui Kudu akan bertindak sesuai dengan perilaku default mereka
* Diubah `bot download` untuk bot tanpa `.bot` file untuk membuat file konfigurasi khusus bahasa dengan nilai dari Pengaturan Aplikasi untuk bot
* Menambahkan `Typescript` dukungan ke `bot prepare-deploy`
* Menambahkan pesan peringatan ke `bot prepare-deploy` untuk `Javascript` dan `Typescript` bot untuk kapan `--code-dir` tidak berisi `package.json`
* Diubah `bot prepare-deploy` untuk kembali `true` jika berhasil
* Menambahkan login verbose ke `bot prepare-deploy`
* Menambahkan lebih banyak wilayah Insights Aplikasi yang tersedia ke`az bot create -v v3`

### <a name="configure"></a>Konfigurasikan
* Menambahkan dukungan untuk konfigurasi nilai default argumen berbasis folder

### <a name="eventhubs"></a>Eventhubs
* Perintah `namespace network-rule` tambahan
* Menambahkan `--default-action` argumen untuk aturan jaringan ke `namespace [create|update]`

### <a name="network"></a>Jaringan
* [MELANGGAR PERUBAHAN] Mengganti `--cache` arugment dengan `--defer` untuk `vnet [create|update]`

### <a name="policy-insights"></a>Policy Insights
* Menambahkan dukungan untuk `--expand PolicyEvaluationDetails` meminta detail evaluasi kebijakan tentang sumber daya

### <a name="role"></a>Peran
* [USANG] Mengubah `create-for-rbac` argumen sembunyikan '-kata sandi' - dukungan akan dihapus pada Mei 2019

### <a name="service-bus"></a>Service Bus
* Perintah `namespace network-rule` tambahan
* Menambahkan `--default-action` argumen untuk aturan jaringan ke `namespace [create|update]`
* Tetap `topic [create|update]` untuk memungkinkan `--max-size` dukungan untuk nilai 10, 20, 40 dan 80GB dengan SKU premium

### <a name="sql"></a>SQL
* Perintah `sql virtual-cluster [list|show|delete]` tambahan

### <a name="vm"></a>VM
* Ditambahkan `--protect-from-scale-in` dan `--protect-from-scale-set-actions` untuk `vmss update` mengaktifkan pembaruan kebijakan perlindungan instans VMSS VM
* Ditambahkan `--instance-id` untuk `vmss update` mengaktifkan pembaruan umum instans VMSS VM
* Ditambahkan `--instance-id` ke `vmss wait`
* Menambahkan grup perintah baru `ppg` untuk mengelola Grup Penempatan Kedekatan
* Ditambahkan `--ppg` ke `[vm|vmss] create` dan `vm availability-set create` untuk mengelola PPG
* Menambahkan `--hyper-v-generation` parameter ke `image create`

## <a name="april-23-2019"></a>23 April 2019 pukul

Versi 2.0.63

### <a name="acs"></a>ACS
* Diubah `aks get-credentials` untuk meminta untuk menimpa nilai duplikat
* Dihapus `(PREVIEW)` dari perintah Dev Spaces "aks use-dev-spaces" dan "aks remove-dev-spaces"

### <a name="ams"></a>AMS
* Memperbaiki bug dengan pembaruan filter aset dan akun

### <a name="appservice"></a>AppService
* Menambahkan dukungan untuk ASE dan batas waktu ke `webapp ssh`
* Menambahkan dukungan untuk membuat CD CI ke pipeline Azure DevOps dari repositori Github ke aplikasi Function
* Menambahkan `--github-pat` argumen untuk `functionapp devops-build create` menerima token akses pribadi Github
* Menambahkan `--github-repository` argumen untuk `functionapp devops-build create` menerima repositori Github yang berisi kode sumber functionapp
* Memperbaiki masalah jika `az webapp up --logs` gagal dengan kesalahan dan memperbarui default . Versi NETCORE ke 2.1
* Menghapus pengaturan functionapp yang tidak perlu saat membuat aplikasi fungsi dengan paket konsumsi
* Diubah `webapp up` sehingga string asp default sekarang menambahkan nomor di akhir untuk membuat ASP baru berdasarkan opsi SKU
* Ditambahkan `-b` sebagai opsi untuk `webapp up` meluncurkan aplikasi di browser
* Diubah `webapp deployment source config zip` untuk menangani `AZURE_CLI_DISABLE_CONNECTION_VERIFICATION` variabel lingkungan

### <a name="deployment-manager"></a>Deployment Manager
* [PRATINJAU] Membuat dan mengelola artefak yang mendukung peluncuran

### <a name="lab"></a>Laboratorium
* Memperbaiki bug yang akan menyebabkan keluar lebih awal

### <a name="network"></a>Jaringan
* Menambahkan delegasi server nama otomatis ke `dns zone create` induk selama pembuatan zona anak

### <a name="resource"></a>Sumber daya
* [USANG] `--link-id`Usang, `--target-id` dan `--filter-string` argumen dari `resource link`
  * Gunakan argumen `--link`, `--target`, dan `--filter` sebagai gantinya
* Memperbaiki masalah di mana `resource link [create|update]` perintah tidak akan berfungsi
* Memperbaiki masalah saat menghapus menggunakan ID sumber daya bisa macet karena kesalahan

### <a name="sql"></a>SQL
* Menambahkan dukungan untuk zona waktu kustom pada instans terkelola
* Diubah untuk memungkinkan nama kumpulan elastis digunakan dengan `sql db update`
* Menambahkan `--no-wait` dukungan ke `sql server [create|update]`
* Perintah tambahan `sql server wait`

### <a name="storage"></a>Penyimpanan
* Memperbaiki masalah dengan token SAS yang dikodekan ganda di `storage blob generate-sas`

### <a name="vm"></a>VM
* Menambahkan `--skip-shutdown` bendera ke `vm|vmss stop` VM power-off tanpa shutdown
* Menambahkan `--storage-account-type` argumen untuk `sig image-version create` mengatur jenis akun profil penerbitan
* Argumen tambahan `--target-regions` untuk `sig image-version create` mengizinkan pengaturan tipe akun penyimpanan khusus wilayah

## <a name="april-9-2019"></a>9 April 2019

### <a name="core"></a>Core
* Memperbaiki masalah di mana beberapa ekstensi menampilkan versi `Unknown` dan tidak dapat diperbarui

### <a name="acr"></a>ACR
* Menambahkan dukungan menjalankan gambar tanpa konteks

### <a name="ams"></a>AMS
* [USANG]: Deprecated the `--bitrate` parameter of `account-filter` and `asset-filter`
* [MELANGGAR PERUBAHAN]: Renamed the `--bitrate` parameter to `--first-quality`
* Menambahkan dukungan parameter enkripsi baru di `ams streaming-policy create`
* Menambahkan paramter `--filters` baru ke `ams streaming-locator create`

### <a name="appservice"></a>AppService
* Menambahkan `--logs` dukungan ke `webapp up`
* Memperbaiki `functionapp devops-build create` masalah pembuatan perintah `azure-pipelines.yml`
* Peningkatan `unctionapp devops-build create` penanganan kesalahan dan indikator
* [MELANGGAR PERUBAHAN] `--local-git` Menghapus bendera untuk `devops-build` perintah, deteksi dan penanganan git lokal wajib untuk membuat Azure DevOps alur
* Menambahkan dukungan untuk pembuatan paket fungsi Linux
* Kemampuan tambahan untuk mengalihkan paket di bawah aplikasi fungsi menggunakan `functionapp update --plan`
* Menambahkan dukungan untuk setelan skala paket premium Azure Functions

### <a name="cdn"></a>CDN
* Menambahkan dukungan untuk `Microsoft_Standard` dan `Standard_ChinaCdn`

### <a name="feedback-reference"></a>Referensi umpan balik
* Diubah `feedback` untuk menampilkan metadata pada perintah yang baru dijalankan
* Diubah `feedback` untuk meminta pengguna membantu dalam proses pembuatan masalah dengan membuka brower dan menggunakan template masalah
* Diubah `feedback` untuk mencetak badan masalah saat dijalankan dengan '--verbose'

### <a name="monitor"></a>Monitor
* Memperbaiki masalah di mana "hitungan" bukan nilai yang diizinkan dengan `metrics alert [create|update]`

### <a name="network"></a>Jaringan
* Format tabel tetap tidak ditampilkan dengan `vnet-gateway list-bgp-peer-status`
* Ditambahkan `list-request-headers` dan `list-response-headers` perintah untuk `application-gateway rewrite-rule`
* Menambahkan `list-server-variables` perintah ke `application-gateway rewrite-rule condition`
* Memperbaiki masalah saat memperbarui status tautan pada port rute ekspres akan memberikan pengecualian atribut yang tidak diketahui `express-route port update`

### <a name="privatedns"></a>PrivateDNS
* Ditambahkan `network private-dns` untuk zona DNS Pribadi

### <a name="resource"></a>Sumber daya
* Memperbaiki masalah dengan `deployment create` dan `group deployment create` di mana file parameter dengan serangkaian parameter kosong tidak akan berfungsi

### <a name="role"></a>Peran
* Diperbaiki `create-for-rbac` untuk menangani `--years` dengan benar
* [MELANGGAR PERUBAHAN] Diubah `role assignment delete` menjadi prompt saat menghapus semua tugas di bawah langganan tanpa syarat

### <a name="sql"></a>SQL
* Diperbarui `sql mi [create|update]` dengan properti proxyOverride dan publicDataEndpointEnabled

### <a name="storage"></a>Penyimpanan
* [MELANGGAR PERUBAHAN] Hasil yang dihapus dari `storage blob delete`
* Ditambahkan `--full-uri` untuk `storage blob generate-sas` membuat uri penuh untuk gumpalan dengan sas
* Ditambahkan `--file-snapshot` ke `storage file copy start` untuk menyalin file dari snapshot
* Diubah `storage blob copy cancel` untuk hanya menampilkan kesalahan, bukan pengecualian untuk NoPendingCopyOperation

## <a name="march-26-2019"></a>26 Maret 2019


### <a name="core"></a>Core
* Memperbaiki masalah dengan ketidakcocokan ekstensi dev
* Penanganan kesalahan sekarang mengarahkan pelanggan ke halaman masalah

### <a name="cloud"></a>Cloud
* Memperbaiki kesalahan 'langganan tidak ditemukan' di `cloud set`

### <a name="acr"></a>ACR
* Memperbaiki sumber berlebihan dalam impor gambar
* Ditambahkan `--auth-mode` ke `acr build`, `acr run`, `acr task create`, , dan `acr task update` perintah
* Menambahkan grup perintah 'kredensial tugas acr' untuk mengelola kredensial untuk Tugas
* Menambahkan '--no-wait' untuk `acr build` perintah

### <a name="appservice"></a>AppService
* Memperbaiki bug di mana `webapp up` tidak menangani berjalan dari direktori kosong atau skenario kode yang tidak diketahui dengan benar
* Memperbaiki bug tempat slot tidak berfungsi `[webapp|functionapp] config ssl bind`

### <a name="bot-service"></a>Layanan BOT
* Ditambahkan `bot prepare-deploy` untuk mempersiapkan penyebaran bot melalui `webapp`
* Diubah `bot create --kind registration` untuk menampilkan kata sandi jika kata sandi tidak disediakan
* [MELANGGAR PERUBAHAN] `bot create --kind registration` Diubah `--endpoint` menjadi default ke string kosong alih-alih diperlukan
* Ditambahkan `SCM_DO_BUILD_DURING_DEPLOYMENT` ke Pengaturan Aplikasi template ARM untuk Bot Aplikasi Web v4

### <a name="cdn"></a>CDN
* Menambahkan dukungan untuk `--no-wait``cdn endpoint [create|update|start|stop|delete|load|purge]`
* [BREAKING CHANGE]: Mengubah `cdn endpoint create` perilaku caching string kueri default. Tidak lagi default ke "IgnoreQueryString". Sekarang diatur oleh layanan

### <a name="cosmosdb"></a>Cosmosdb
* Menambahkan dukungan untuk `--enable-multiple-write-locations` pembaruan akun
* Menambahkan `network-rule` subkelompok dengan perintah `add`, `remove`, dan `list` untuk mengelola aturan VNET dari akun Cosmos DB

### <a name="interactive"></a>Interaktif
* Ketidakcocokan tetap dengan ekstensi Interaktif yang diinstal melalui azdev

### <a name="monitor"></a>Monitor
* Diubah untuk memungkinkan nilai `*` dimensi `monitor metrics alert [create|update]`

### <a name="network"></a>Jaringan
* Menambahkan `rewrite-rule` grup perintah ke `application-gateway`

### <a name="profile"></a>Profil
* Menambahkan dukungan akun tingkat penyewa untuk identitas layanan terkelola ke `login`

### <a name="postgres"></a>Postgres
* Menambahkan perintah dan `restart server` perintah postgresql `replica`
* Diubah untuk mendapatkan lokasi default dari grup sumber daya saat tidak disediakan untuk membuat server dan menambahkan validasi untuk hari retensi

### <a name="resource"></a>Sumber daya
* Output tabel yang ditingkatkan untuk `deployment [create|list|show]`
* Memperbaiki masalah dengan `deployment [create|validate]` tempat tipe secureObject tidak dikenali

### <a name="graph"></a>Graph
* Menambahkan dukungan untuk `--end-date``ad [app|sp] credential reset`
* Menambahkan dukungan untuk menambahkan izin dengan `ad app permission add`
* Memperbaiki bug dengan `ad app permission list` saat tidak ada izin
* Diubah `ad sp delete` untuk melewati penghapusan penetapan peran jika akun saat ini tidak memiliki langganan
* Diubah `ad app create` untuk memiliki `--identifier-uris` daftar default ke daftar kosong jika tidak disediakan

### <a name="storage"></a>penyimpanan
* Ditambahkan `--snapshot` ke `storage file download-batch` unduhan dari snapshot berbagi
* Bilah `storage blob [download-batch|upload-batch]` kemajuan yang diubah menjadi kurang verbose dan menunjukkan gumpalan saat ini
* Memperbaiki masalah saat `storage account update` memperbarui parameter enkripsi
* Memperbaiki masalah di mana `storage blob show` akan gagal saat menggunakan oauth (`--auth-mode=login`)

### <a name="vm"></a>VM
* Perintah tambahan `image update`

## <a name="march-12-2019"></a>12 Maret 2019

Versi 2.0.60

### <a name="core"></a>Core

* Memperbaiki kesalahan yang salah dalam `cloud set` tentang langganan yang tidak ditemukan

### <a name="acr"></a>ACR

* Memperbaiki sumber berlebihan dalam impor gambar

### <a name="acs"></a>ACS

* Diubah untuk mengabaikan `--listen-address` parameter `aks browse` jika tidak didukung oleh kubectl

### <a name="appservice"></a>AppService

* Ditambahkan `[webapp|functionapp] deployment list-publishing-credentials` untuk mendapatkan url penerbitan Kudu dan kredensialnya
* Menghapus pernyataan cetak yang salah untuk `webapp auth update`
* Diperbaiki `functionapp` untuk mengatur gambar yang benar untuk runtime dalam paket Linux App Service
* Menghapus tag pratinjau untuk `webapp up` dan menambahkan peningkatan pada perintah

### <a name="botservice"></a>Botservice

* Ditambahkan `SCM_DO_BUILD_DURING_DEPLOYMENT` ke Pengaturan Aplikasi template ARM untuk Bot Aplikasi Web v4
* `Microsoft-BotFramework-AppPassword` Pengaturan `Microsoft-BotFramework-AppId` Aplikasi template ARM untuk Bot Aplikasi Web v4
* Menghapus kutipan tunggal dari `bot publish` output perintah di akhir `bot create`
* Berubah `bot publish` menjadi asinkron

### <a name="container"></a>Kontainer

* Menambahkan `--no-wait` argumen ke `container [start|restart]`

### <a name="eventhub"></a>EventHub

* Menambahkan `--skip-empty-archives` bendera untuk `eventhub create|update` mendukung arsip kosong dalam penangkapan

### <a name="find"></a>Cari

* Pembaruan fungsionalitas utama

### <a name="hdinsight"></a>HDInsight

* `--storage-account-managed-identity` Menambahkan parameter untuk `hdinsight create` mendukung ADLS Gen2 MSI

### <a name="network"></a>Jaringan

* Memperbaiki masalah dengan `vpn-connection update` tempat memperbarui koneksi VPN antara gateway dalam langganan yang berbeda akan gagal

### <a name="rdbms"></a>Rdbms

* Perbaikan kecil untuk mendapatkan lokasi default dari grup sumber daya saat tidak disediakan untuk membuat server dan menambahkan validasi untuk hari retensi

### <a name="role"></a>Peran

* Diperbaiki `role definition update` untuk menggunakan ID untuk menyelesaikan definisi dengan benar
* Diubah `ad app credential reset` untuk menghapus asumsi bahwa prinsipal layanan aplikasi selalu ada

### <a name="service-fabric"></a>Service Fabric

* Masalah tetap dengan `sf cluster list` tidak dapat ditkan

## <a name="february-26-2019"></a>26 Februari 2019 pukul

Versi 2.0.59

### <a name="core"></a>Core

* Memperbaiki masalah di mana dalam beberapa kasus menggunakan `--subscription NAME` akan melemparkan pengecualian

### <a name="acr"></a>ACR

* Menambahkan `--target` parameter untuk `acr build`, `acr task create` dan `acr task update` perintah
* Penanganan kesalahan yang ditingkatkan untuk perintah runtime saat tidak masuk ke Azure

### <a name="acs"></a>ACS

* Opsi tambahan `--listen-address` ke `aks port-forward`

### <a name="appservice"></a>AppService

* Perintah tambahan `functionapp devops-build`

### <a name="batch"></a>Batch
* [MELANGGAR PERUBAHAN] `batch pool upgrade os` Menghapus perintah
* [MELANGGAR PERUBAHAN] `Pacakges` Menghapus properti dari `Application` tanggapan
* `batch application package list` Menambahkan perintah untuk mencantumkan paket aplikasi
* [MELANGGAR PERUBAHAN] Diubah `--application-id` menjadi `--application-name` dalam semua `batch application` perintah,
* `--json-file` Menambahkan argumen ke perintah untuk meminta respons API mentah
* Validasi yang diperbarui untuk disertakan `https://` secara otomatis di semua titik akhir jika hilang

### <a name="cosmosdb"></a>CosmosDB

* Menambahkan `network-rule` subkelompok dengan perintah `add`, `remove`, dan `list` untuk mengelola aturan VNET dari akun Cosmos DB

### <a name="kusto"></a>Kusto

* [MELANGGAR PERUBAHAN] Perubahan `hot_cache_period` dan `soft_delete_period` jenis untuk database ke format durasi ISO8601

### <a name="network"></a>Jaringan

* Menambahkan `--express-route-gateway-bypass` argumen ke `vpn-connection [create|update]`
* Menambahkan grup perintah dari `express-route` ekstensi
* Grup yang ditambahkan `express-route gateway` dan `express-route port` perintah
* Menambahkan argumen `--legacy-mode` ke `express-route peering [create|update]`
* Menambahkan argumen `--allow-classic-operations` dan `--express-route-port``express-route [create|update]`
* Menambahkan `--gateway-default-site` argumen ke `vnet-gateway [create|update]`
* Menambahkan `ipsec-policy` perintah ke `vnet-gateway`

### <a name="resource"></a>Sumber daya

* Memperbaiki masalah dengan `deployment create` di mana bidang tipe peka huruf besar/kecil
* Menambahkan dukungan untuk file parameter berbasis URI ke `policy assignment create`
* Menambahkan dukungan untuk parameter dan definisi berbasis URI ke `policy set-definition update`
* Penanganan parameter dan aturan yang tetap untuk `policy definition update`
* Memperbaiki masalah dengan `resource show/update/delete/tag/invoke-action` di mana ID langganan silang tidak menghormati ID langganan dengan benar

### <a name="role"></a>Peran

* Menambahkan dukungan untuk peran aplikasi ke `ad app [create|update]`

### <a name="vm"></a>VM

* Masalah tetap dengan `vm create where `--accelerated-networking' tidak diaktifkan secara default untuk Ubuntu 18.0

## <a name="february-12-2019"></a>12 Februari 2019

Versi 2.0.58

### <a name="core"></a>Core

* `az --version` sekarang menampilkan pemberitahuan jika Anda memiliki paket yang dapat diperbarui
* Regresi tetap di mana `--ids` tidak dapat lagi digunakan dengan output JSON

### <a name="acr"></a>ACR
* [MELANGGAR PERUBAHAN] Grup perintah yang dihapus `acr build-task`
* [MELANGGAR PERUBAHAN] Dihapus `--tag` dan `--manifest` opsi dari `acr repository delete`

### <a name="acs"></a>ACS
* Menambahkan dukungan untuk nama-nama yang tidak sensitif terhadap kasus ke `aks [enable-addons|disable-addons]`
* Menambahkan dukungan untuk Azure Active Directory memperbarui operasi menggunakan`aks update-credentials --reset-aad`
* Menambahkan klarifikasi yang `--output` diabaikan untuk `aks get-credentials`

### <a name="ams"></a>AMS
* Perintah `ams streaming-endpoint [start | stop | create | update] wait` tambahan
* Perintah `ams live-event [create | start | stop | reset] wait` tambahan

### <a name="appservice"></a>Layanan aplikasi
* Menambahkan kemampuan untuk membuat dan mengonfigurasi fungsi menggunakan kontainer ACR
* Menambahkan dukungan untuk memperbarui konfigurasi webapp melalui json
* Bantuan yang lebih baik untuk `appservice-plan-update`
* Menambahkan dukungan untuk insight aplikasi di functionapp create
* Memperbaiki masalah dengan webapp SSH

### <a name="botservice"></a>Botservice
* Peningkatan UX untuk `bot publish`
* Peringatan tambahan untuk batas waktu saat berjalan `npm install` selama `az bot publish`
* Menghapus char `.` tidak valid dari `--name`  dalam `az bot create`
* Diubah untuk berhenti mengacak nama sumber daya saat membuat Azure Storage, App Service Plan, Function/Web App dan Application Insights
* [USANG] Argumen usang yang `--proj-name` mendukung `--proj-file-path`
* Diubah `az bot publish` untuk menghapus file penyebaran IIS Node.js yang diambil jika belum ada
* Menambahkan `--keep-node-modules` argumen untuk `az bot publish` tidak menghapus `node_modules` folder di App Service
* Menambahkan `"publishCommand"` pasangan nilai kunci ke output dari `az bot create` saat membuat bot Azure Function atau Web App
  * Nilai `"publishCommand"` adalah perintah yang `az bot publish` di-prepopulated dengan parameter yang diperlukan untuk mempublikasikan bot yang baru dibuat.
* Diperbarui `"WEBSITE_NODE_DEFAULT_VERSION"` dalam template ARM untuk bot SDK v4 untuk menggunakan 10.14.1, bukan 8.9.4

### <a name="key-vault"></a>Key Vault
* Memperbaiki masalah dengan `keyvault secret backup` tempat beberapa pengguna menerima kesalahan `unexpected_keyword` saat menggunakan `--id`

### <a name="monitor"></a>Monitor
* Diubah `monitor metrics alert [create|update]` untuk memungkinkan nilai dimensi `*`

### <a name="network"></a>Jaringan
* Diubah `dns zone export` untuk memastikan CNAMEs yang diekspor adalah FQDNs
* Menambahkan `--gateway-name` parameter untuk `nic ip-config address-pool [add|remove]` mendukung kumpulan alamat backend gateway aplikasi
* Ditambahkan `--traffic-analytics` dan `--workspace` argumen untuk `network watcher flow-log configure` mendukung analitik lalu lintas melalui ruang kerja Analitik Log
* Ditambahkan `--idle-timeout` dan `--floating-ip` ke `lb inbound-nat-pool [create|update]`

### <a name="policy-insights"></a>Policy Insights
* Menambahkan `policy remediation` perintah untuk mendukung fitur remediasi kebijakan sumber daya

### <a name="rdbms"></a>RDBMS
* Parameter pesan dan perintah bantuan yang ditingkatkan

### <a name="redis"></a>Redis
* Perintah tambahan untuk mengelola aturan firewall (buat, perbarui, hapus, tampilkan, daftar)
* Perintah tambahan untuk mengelola tautan server (buat, hapus, tampilkan, daftar)
* Perintah tambahan untuk mengelola jadwal patch (buat, perbarui, hapus, tampilkan)
* Menambahkan dukungan untuk Availability Zone dan Minimum TLS Version ke 'redis create
* [MELANGGAR PERUBAHAN] Dihapus `redis update-settings` dan `redis list-all` perintah
* [MELANGGAR PERUBAHAN] Parameter untuk `redis create`: 'pengaturan penyewa' tidak diterima dalam format key[=value]
* [USANG] Menambahkan pesan peringatan untuk perintah usang `redis import-method`

### <a name="role"></a>Peran
* [MELANGGAR PERUBAHAN] Perintah yang dipindahkan `az identity` di sini dari `vm` perintah

### <a name="sql-vm"></a>SQL VM
* [USANG] Argumen yang tidak digunakan `--boostrap-acc-pwd` lagi karena kesalahan ketik

### <a name="vm"></a>VM
* Diubah `vm list-skus` untuk memungkinkan penggunaan `--all` sebagai pengganti `--all true`
* Ditambahkan `vmss run-command [invoke | list | show]`
* Memperbaiki bug di mana `vmss encryption enable` akan gagal jika dijalankan sebelumnya
* [MELANGGAR PERUBAHAN] Perintah pindah `az identity` ke `role` perintah

## <a name="january-31-2019"></a>31 Januari 2019 pukul

Versi 2.0.57

### <a name="core"></a>Core

* Hot Fix untuk [masalah 8399](https://github.com/Azure/azure-cli/issues/8399).

## <a name="january-28-2019"></a>28 Januari 2019

Versi 2.0.56

### <a name="acr"></a>ACR
* Menambahkan dukungan untuk aturan VNet/IP

### <a name="acs"></a>ACS
* Menambahkan Pratinjau Node Virtual
* Menambahkan perintah OpenShift Terkelola
* Menambahkan dukungan untuk operasi pembaruan utama layanan dengan `aks update-credentials -reset-service-principal`

### <a name="ams"></a>AMS
* [MELANGGAR PERUBAHAN] Berganti `ams asset get-streaming-locators` nama menjadi `ams asset list-streaming-locators`
* [MELANGGAR PERUBAHAN] Berganti `ams streaming-locator get-content-keys` nama menjadi `ams streaming-locator list-content-keys`

### <a name="appservice"></a>Layanan aplikasi
* Menambahkan dukungan untuk insight aplikasi di `functionapp create`
* Menambahkan dukungan untuk pembuatan paket layanan aplikasi (termasuk Elastic Premium) ke Function Apps
* Memperbaiki masalah pengaturan aplikasi dengan paket Elastic Premium

### <a name="container"></a>Kontainer
* Perintah tambahan `container start`
* Diubah untuk memungkinkan penggunaan nilai desimal untuk CPU selama pembuatan kontainer

### <a name="eventgrid"></a>EventGrid
* Menambahkan `--deadletter-endpoint` parameter ke `event-subscription [create|update]`
* Menambahkan storagequeue dan hybridconnection sebagai nilai baru untuk 'event-subscription [create|update] --endpoint-type'
* Ditambahkan `--max-delivery-attempts` dan `--event-ttl` parameter untuk `event-subscription create` menentukan kebijakan coba ulang untuk acara
* Menambahkan pesan peringatan ke `event-subscription [create|update]` saat webhook sebagai tujuan digunakan untuk langganan acara
* Menambahkan parameter source-resource-id untuk semua perintah terkait langganan peristiwa dan menandai semua parameter terkait sumber daya lainnya sebagai usang

### <a name="hdinsight"></a>HDInsight
* [MELANGGAR PERUBAHAN] `--virtual-network` Menghapus parameter dan `--subnet-name` parameter dari `hdinsight [application] create`
* [MELANGGAR PERUBAHAN] Diubah `hdinsight create --storage-account` untuk menerima nama atau id akun penyimpanan, bukan titik akhir blob
* Ditambahkan `--vnet-name` dan `--subnet-name` parameter untuk `hdinsight create`
* Menambahkan dukungan untuk Paket Keamanan Perusahaan dan enkripsi disk ke `hdinsight create`
* Perintah tambahan `hdinsight rotate-disk-encryption-key`
* Perintah tambahan `hdinsight update`

### <a name="iot"></a>IoT
* Menambahkan format pengkodean ke perintah titik akhir perutean

### <a name="kusto"></a>Kusto
* Rilis pratinjau

### <a name="monitor"></a>Monitor
* Perbandingan ID yang berubah menjadi tidak sensitif jika tidak sensitif

### <a name="profile"></a>Profil
* Aktifkan akun tingkat penyewa untuk identitas layanan terkelola untuk `login`

### <a name="network"></a>Jaringan
* Memperbaiki masalah dengan `express-route update`: di mana `--bandwidth` argumen diabaikan
* Memperbaiki masalah dengan `ddos-protection update` di mana pemahaman yang ditetapkan menyebabkan jejak tumpukan

### <a name="resource"></a>Sumber daya
* Menambahkan dukungan untuk file parameter URI ke `group deployment create`
* Menambahkan dukungan untuk identitas terkelola ke `policy assignment [create|list|show]`

### <a name="sql-virtual-machine"></a>Mesin Virtual SQL
* Rilis pratinjau

### <a name="storage"></a>Penyimpanan
* Mengubah perbaikan untuk memperbarui hanya properti yang diubah pada objek yang sama
* Tetap # 8021, data biner dikodekan dalam basis 64 ketika dikembalikan

### <a name="vm"></a>VM
* Diubah `vm encryption enable` untuk memvalidasi keyvault enkripsi disk dan key encryption keyvault itu ada
* Menambahkan `--force` bendera ke `vm encryption enable`

## <a name="january-15-2019"></a>15 Januari 2019 pukul

Versi 2.0.55

### <a name="acr"></a>ACR
* Diubah untuk memungkinkan memaksa mendorong bagan helm yang tidak ada
* diubah untuk mengizinkan operasi runtime tanpa permintaan ARM
* [USANG] Parameter yang `--resource-group` tidak digunakan lagi dalam perintah:
  * `acr login`
  * `acr repository`
  * `acr helm`

### <a name="acs"></a>ACS
* Menambahkan dukungan untuk wilayah ACI baru

### <a name="appservice"></a>Layanan aplikasi
* Memperbaiki masalah dengan mengunggah sertifikat untuk aplikasi yang dihosting di ASE, di mana Aplikasi & ASE RG berbeda
* Diubah `webapp up` untuk menggunakan SKU P1V1 sebagai default untuk Linux
* Diperbaiki `[webapp|functionapp] deployment source config-zip` untuk menampilkan pesan kesalahan yang benar saat penerapan gagal
* Perintah tambahan `webapp ssh`

### <a name="botservice"></a>Botservice
* Menambahkan pembaruan status penyebaran ke `bot create`

### <a name="configure"></a>Konfigurasikan
* Ditambahkan `none` sebagai format output yang dapat dikonfigurasi

### <a name="cosmosdb"></a>CosmosDB
* Menambahkan dukungan untuk membuat database dengan throughput bersama

### <a name="hdinsight"></a>HDInsight
* Perintah tambahan untuk mengelola aplikasi
* Menambahkan perintah untuk mengelola tindakan skrip
* Perintah tambahan untuk mengelola Operations Management Suite (OMS)
* Menambahkan dukungan untuk mencantumkan penggunaan regional ke `hdinsight list-usage`
* [MELANGGAR PERUBAHAN] Menghapus tipe klaster default dari `hdinsight create`

### <a name="network"></a>Jaringan
* Ditambahkan `--custom-headers` dan `--status-code-ranges` argumen untuk `traffic-manager profile [create|update]`
* Menambahkan jenis perutean baru: Subnet dan Multivalue
* Ditambahkan `--custom-headers` dan `--subnets` argumen untuk `traffic-manager endpoint [create|update]`
* Memperbaiki masalah saat memasok `--vnets ""` `ddos-protection update` menyebabkan kesalahan

### <a name="role"></a>Peran
* [USANG] Argumen yang tidak digunakan `--password` lagi untuk `create-for-rbac`. Gunakan kata sandi aman yang dihasilkan oleh CLI sebagai gantinya

### <a name="security"></a>Keamanan
* Rilis Awal

### <a name="storage"></a>Penyimpanan
* [MELANGGAR PERUBAHAN] Mengubah `storage [blob|file|container|share] list` jumlah hasil default menjadi 5.000. Gunakan `--num-results *` untuk perilaku asli mengembalikan semua hasil
* Menambahkan `--marker` parameter ke `storage [blob|file|container|share] list`
* Menambahkan penanda log untuk halaman berikutnya ke STDERR untuk `storage [blob|file|container|share] list`
* Perintah tambahan `storage blob service-properties update` dengan dukungan untuk situs web statis

### <a name="vm"></a>VM
* Diubah `vm [disk|unmanaged-disk]` dan `vmss disk` memiliki parameter yang lebih konsisten
* Menambahkan dukungan untuk referensi gambar penyewa silang `[vm|vmss] create`
* Memperbaiki bug dengan konfigurasi default di `vm diagnostics get-default-config --windows-os`
* Menambahkan argumen `--provision-after-extensions` untuk `vmss extension set` menentukan ekstensi apa yang harus disediakan sebelum ekstensi ditetapkan
* Menambahkan argumen `--replica-count` untuk `sig image-version update` mengatur jumlah replikasi default
* Memperbaiki bug dengan `image create --source` di mana disk os sumber keliru untuk VM dengan nama yang sama, bahkan jika ID sumber daya penuh disediakan

## <a name="december-20-2018"></a>20 Desember 2018

Versi 2.0.54
### <a name="appservice"></a>Layanan aplikasi
* Memperbaiki masalah di mana `webapp up` akan gagal untuk dipindahkan
* Menambahkan dukungan untuk listingan dan memulihkan snapshot webapp
* Menambahkan dukungan untuk `--runtime` bendera ke aplikasi fungsi Windows

### <a name="iotcentral"></a>IoTCentral
* Panggilan API perintah pemutakhiran tetap

### <a name="role"></a>Peran
* [MELANGGAR PERUBAHAN] Diubah `ad [app|sp] list` menjadi hanya mencantumkan 100 objek pertama secara default

### <a name="sql"></a>SQL
* Menambahkan dukungan untuk kolusi kustom pada instans terkelola

### <a name="vm"></a>VM
* Menambahkan `---os-type` parameter ke `disk create`

## <a name="december-18-2018"></a>18 Desember 2018

Versi 2.0.53
### <a name="acr"></a>ACR
* Menambahkan dukungan untuk impor gambar dari Container Registries eksternal
* Mengembunkan tata letak tabel untuk daftar tugas
* Menambahkan dukungan untuk URL Azure DevOps

### <a name="acs"></a>ACS
* Menambahkan Pratinjau Node Virtual
* Menghapus "(PREVIEW)" dari argumen AAD ke`aks create`
* [USANG] Perintah yang `az acs` tidak digunakan lagi. Layanan ACS akan pensiun pada 31 Januari 2020
* Menambahkan dukungan Kebijakan Jaringan saat membuat klaster AKS baru
* Persyaratan argumen yang `--nodepool-name` dihapus jika `aks scale` hanya ada satu nodepool

### <a name="appservice"></a>Layanan aplikasi
* Memperbaiki masalah di mana `webapp config container` tidak menghormati `--slot` parameter

### <a name="botservice"></a>Botservice
* Menambahkan dukungan untuk `.bot` penguraian berkas saat menelepon `bot show`
* Memperbaiki Bug penyediaan AppInsights
* Memperbaiki bug spasi saat berhadapan dengan jalur file
* Mengurangi panggilan jaringan Kudu
* Peningkatan UX perintah umum

### <a name="consumption"></a>Consumption
* Memperbaiki bug untuk API anggaran untuk menampilkan pemberitahuan

### <a name="cosmosdb"></a>CosmosDB
* Menambahkan dukungan untuk memperbarui akun dari multi-master ke master tunggal

### <a name="maps"></a>Maps
* Menambahkan dukungan untuk S1 SKU ke `maps account [create|update]`

### <a name="network"></a>Jaringan
* Menambahkan dukungan untuk `--format` dan `--log-version` untuk `watcher flow-log configure`
* Memperbaiki masalah dengan `dns zone update` tempat menggunakan "" untuk menghapus resolusi dan pendaftaran VNet tidak berfungsi

### <a name="resource"></a>Sumber daya
* Penanganan parameter cakupan tetap untuk grup manajemen di `policy assignment [create|list|delete|show|update]`
* Menambahkan perintah baru `resource wait`

### <a name="storage"></a>Penyimpanan
*  Menambahkan kemampuan untuk memperbarui versi skema log untuk layanan penyimpanan di `storage logging update`

### <a name="vm"></a>VM
* Memperbaiki crash `vm identity remove` saat vm yang ditentukan tidak memiliki identitas layanan terkelola yang ditetapkan

## <a name="december-4-2018"></a>4 Desember 2018

Versi 2.0.52
### <a name="core"></a>Core
* Menambahkan dukungan untuk penyediaan sumber daya lintas penyewa untuk prinsipal layanan multi-penyewa
* Memperbaiki bug di mana id yang disalurkan dari perintah dengan output tsv diurai dengan tidak benar

### <a name="appservice"></a>Layanan aplikasi
* [PRATINJAU] Perintah tambahan `webapp up` yang membantu dalam membuat & menyebarkan konten ke aplikasi
* Memperbaiki bug pada aplikasi windows berbasis kontainer karena perubahan backend

### <a name="network"></a>Jaringan
* Menambahkan `--exclusion` argumen untuk `application-gateway waf-config set` mendukung pengecualian WAF

### <a name="role"></a>Peran
* Menambahkan dukungan untuk pengidentifikasi kustom untuk kredensial kata sandi

### <a name="vm"></a>VM
* [USANG] Parameter yang `vm extension [show|wait] --expand` tidak digunakan lagi
* Menambahkan `--force` parameter ke `vm restart` VM yang tidak responsif ulang
* Diubah `[vm|vmss] create --authentication-type` untuk menerima "semua" untuk membuat VM dengan kata sandi dan otentikasi ssh
* Menambahkan `image create --os-disk-caching` parameter untuk mengatur os disk caching untuk gambar

## <a name="november-20-2018"></a>20 November 2018

Versi 2.0.51
### <a name="core"></a>Core
* Mengubah login MSI untuk tidak menggunakan kembali nama langganan dalam identitas

### <a name="acr"></a>ACR
* Menambahkan token konteks ke langkah tugas
* Menambahkan dukungan untuk menetapkan rahasia dalam acr run untuk mencerminkan tugas acr
* Peningkatan dukungan untuk `--top` dan `--orderby` untuk `show-tags` dan `show-manifests` perintah

### <a name="appservice"></a>Layanan aplikasi
* Mengubah batas waktu default penyebaran zip untuk polling untuk status meningkat menjadi 5 menit, juga menambahkan properti batas waktu untuk menyesuaikan nilai ini
* Memperbarui default `node_version`. Mengatur ulang tindakan swap slot, selama swap dua fase mempertahankan semua appsettings & string koneksi
* Pemeriksaan SKU sisi klien yang dihapus untuk pembuatan paket layanan aplikasi Linux
* Memperbaiki kesalahan saat mencoba mendapatkan status zipdeploy

### <a name="iotcentral"></a>IotCentral
* Pemeriksaan ketersediaan subdomain tambahan saat membuat aplikasi IoT Central

### <a name="keyvault"></a>Az.KeyVault
* Memperbaiki bug di mana kesalahan mungkin telah diabaikan

### <a name="network"></a>Jaringan
* Menambahkan `root-cert` subkomand untuk `application-gateway` menangani sertifikasi akar tepercaya
* Ditambahkan `--min-capacity` dan `--custom-error-pages` opsi untuk `application-gateway [create|update]`:
* Ditambahkan `--zones` untuk dukungan availability zone ke `application-gateway create`
* Menambahkan argumen `--file-upload-limit`, `--max-request-body-size` dan `--request-body-check` untuk `application-gateway waf-config set`

### <a name="rdbms"></a>Rdbms
* Menambahkan perintah mariadb vnet

### <a name="rbac"></a>Rbac
* Memperbaiki masalah dengan mencoba memperbarui kredensial yang tidak berubah di `ad app update`
* Menambahkan peringatan output untuk mengkomunikasikan perubahan yang melanggar dalam waktu dekat untuk `ad [app|sp] list`

### <a name="storage"></a>Penyimpanan
* Peningkatan penanganan kasus sudut untuk perintah salin penyimpanan
* Memperbaiki masalah dengan `storage blob copy start-batch` tidak menggunakan kredensial login saat akun tujuan dan sumber sama
* Memperbaiki bug dengan`storage [blob|file] url` tempat `sas_token` tidak dimasukkan ke dalam URL
* Menambahkan peringatan perubahan yang melanggar ke `[blob|container] list`: akan segera menghasilkan hanya 5000 hasil pertama secara default

### <a name="vm"></a>VM
* Menambahkan dukungan untuk `[vm|vmss] create --storage-sku` menentukan akun penyimpanan SKU untuk OS terkelola dan disk data secara terpisah
* Mengubah parameter `sig image-version` nama versi menjadi `--image-version -e`
* Argumen `--image-version-name`yang tidak digunakan `sig image-version` lagi, digantikan oleh`--image-version`
* Menambahkan dukungan untuk menggunakan disk OS lokal ke `[vm|vmss] create --ephemeral-os-disk`
* Menambahkan dukungan untuk `--no-wait``snapshot create/update`
* Perintah tambahan `snapshot wait`
* Menambahkan dukungan untuk menggunakan nama instans dengan `[vm|vmss] extension set --extension-instance-name`

## <a name="november-6-2018"></a>6 November 2018

Versi 2.0.50

### <a name="core"></a>Core
* Menambahkan dukungan untuk service principal sn+emiten auth

### <a name="acr"></a>ACR
* Menambahkan dukungan untuk acara git permintaan komit dan tarik untuk pemicu sumber Tugas
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
* Menambahkan dukungan untuk `ams transform output remove` saat ini dapat dilakukan dengan melewati indeks output untuk menghapus
* Ditambahkan `--correlation-data` dan `--label` argumen ke `ams job` grup perintah
* Ditambahkan `--storage-account` dan `--container` argumen ke `ams asset` grup perintah
* Menambahkan nilai default untuk waktu kadaluwarsa (Sekarang+23h) dan izin (Baca) dalam `ams asset get-sas-url` perintah
* [MELANGGAR PERUBAHAN] Perintah yang diganti `ams streaming locator` dengan `ams streaming-locator`
* [MELANGGAR PERUBAHAN] Argumen yang diperbarui `--content-keys` dari `ams streaming locator`
* [MELANGGAR PERUBAHAN] Berganti `--content-policy-name` nama menjadi `--content-key-policy-name` dalam `ams streaming locator` perintah
* [MELANGGAR PERUBAHAN] Perintah yang diganti `ams streaming policy` dengan `ams streaming-policy`
* [MELANGGAR PERUBAHAN] Argumen yang diganti `--preset-names` dengan `--preset` dalam `ams transform` grup perintah. Sekarang Anda hanya dapat mengatur 1 output/preset pada satu waktu (untuk menambahkan lebih banyak, Anda harus menjalankan `ams transform output add`). Selain itu, Anda dapat mengatur StandardEncoderPreset kustom dengan meneruskan jalur ke JSON kustom Anda
* [MELANGGAR PERUBAHAN] Diganti `--output-asset-names ` namanya menjadi `--output-assets` dalam `ams job start` perintah. Sekarang menerima daftar aset yang dipisahkan spasi dalam format 'assetName=label'. Aset tanpa label dapat dikirim seperti ini: 'assetName='

### <a name="appservice"></a>AppService
* Memperbaiki bug `az webapp config backup update` yang mencegah pengaturan jadwal pencadangan jika belum diatur

### <a name="configure"></a>Konfigurasikan
* Menambahkan YAML ke opsi format output

### <a name="container"></a>Kontainer
* Diubah untuk menampilkan identitas saat mengekspor grup kontainer ke yaml

### <a name="eventhub"></a>EventHub
* Menambahkan `--enable-kafka` bendera untuk mendukung Kafka di `eventhub namespace [create|update]`

### <a name="interactive"></a>Interaktif
* Interaktif sekarang menginstal `interactive` ekstensi, yang akan memungkinkan pembaruan dan dukungan yang lebih cepat

### <a name="monitor"></a>Monitor
* Menambahkan dukungan untuk nama metrik yang mencakup karakter forward-slash (/) dan periode (.)`--condition``monitor metrics alert [create|update]`

### <a name="network"></a>Jaringan
* Nama perintah yang `network interface-endpoint` tidak digunakan lagi demi `network private-endpoint`
* Memperbaiki masalah dengan tempat `--peer-circuit` argumen masuk `express-route peering connection create`tidak akan menerima ID
* Memperbaiki masalah di mana `--ip-tags` tidak bekerja dengan benar dengan `public-ip create`

### <a name="profile"></a>Profil
* Ditambahkan `--use-cert-sn-issuer` ke `az login` untuk login utama layanan dengan auto-rolls cert

### <a name="rdbms"></a>RDBMS
* Menambahkan perintah replika mysql

### <a name="resource"></a>Sumber daya
* Menambahkan dukungan untuk grup manajemen dan langganan ke `policy definition|set-definition` perintah

### <a name="role"></a>Peran
* Menambahkan dukungan untuk manajemen izin API, pengguna masuk, dan manajemen kredensial & kata sandi aplikasi
* Diubah `ad sp create-for-rbac` untuk memperjelas kebingungan antara displayName dan nama utama layanan
* Menambahkan dukungan untuk memberikan izin ke aplikasi AAD

### <a name="storage"></a>Penyimpanan
* Menambahkan dukungan untuk terhubung ke layanan penyimpanan hanya dengan SAS dan titik akhir (tanpa nama akun atau kunci) seperti yang dijelaskan dalam [Mengonfigurasi string koneksi Azure Storage](/azure/storage/common/storage-configure-connection-string).

### <a name="vm"></a>VM
* Menambahkan `storage-sku` argumen untuk `image create` mengatur jenis akun penyimpanan default gambar
* Memperbaiki bug dengan `vm resize` tempat `--no-wait` opsi menyebabkan perintah macet
* Mengubah `vm encryption show` format keluaran tabel untuk menampilkan status
* Diubah `vm secret format` untuk memerlukan output json/jsonc. Memperingatkan pengguna dan default untuk json output jika format output yang tidak diinginkan dipilih
* Validasi argumen yang ditingkatkan untuk `vm create --image`

## <a name="october-23-2018"></a>23 Oktober 2018

Versi 2.0.49

### <a name="core"></a>Core
* Memperbaiki masalah dengan `--ids` di mana `--subscription` akan lebih diutamakan daripada langganan di `--ids`
* Menambahkan peringatan eksplisit ketika parameter akan diabaikan dengan menggunakan `--ids`

### <a name="acr"></a>ACR
* Memperbaiki masalah pengkodean ACR Build di Python2

### <a name="cdn"></a>CDN
* [MELANGGAR PERUBAHAN] Mengubah `cdn endpoint create`perilaku caching string kueri default menjadi tidak lagi default menjadi "IgnoreQueryString". Sekarang diatur oleh layanan

### <a name="container"></a>Kontainer
* Ditambahkan `Private` sebagai tipe yang valid untuk diteruskan ke '--ip-address'
* Diubah untuk memungkinkan hanya menggunakan SUBNET ID untuk mengatur jaringan virtual untuk grup kontainer
* Diubah untuk mengizinkan penggunaan nama vnet atau id sumber daya untuk mengaktifkan penggunaan vnet dari grup sumber daya yang berbeda
* Ditambahkan `--assign-identity` untuk menambahkan identitas MSI ke grup kontainer
* Ditambahkan `--scope` untuk membuat penetapan peran untuk identitas MSI yang ditetapkan sistem
* Menambahkan peringatan saat membuat grup kontainer dengan gambar tanpa proses yang berjalan lama
* Memperbaiki masalah output tabel untuk `list` dan `show` perintah

### <a name="cosmosdb"></a>CosmosDB
* Menambahkan `--enable-multiple-write-locations` dukungan ke `cosmosdb create`

### <a name="interactive"></a>Interaktif
* Diubah untuk memastikan parameter langganan global muncul dalam parameter

### <a name="iot-central"></a>IoT Pusat
* Menambahkan opsi templat dan nama tampilan untuk pembuatan Aplikasi Pusat IoT
* [MELANGGAR PERUBAHAN] Menghapus dukungan untuk SKU F1; Gunakan S1 SKU sebagai gantinya

### <a name="monitor"></a>Monitor
* Perubahan pada `monitor activity-log list`:
  * Menambahkan dukungan untuk mencantumkan semua acara di tingkat langganan
  * Menambahkan `--offset` parameter untuk lebih mudah membuat kueri waktu
  * Validasi yang ditingkatkan untuk `--start-time` dan `--end-time` menggunakan format ISO8601 yang lebih luas dan format datetime yang lebih ramah pengguna
  * Ditambahkan `--namespace` sebagai alias untuk opsi yang tidak digunakan lagi `--resource-provider`
  * Usang `--filters` karena tidak ada nilai selain yang memiliki opsi yang diketik dengan kuat yang didukung oleh layanan
* Perubahan pada `monitor metrics list`:
  * Menambahkan `--offset` parameter untuk lebih mudah membuat kueri waktu
  * Validasi yang ditingkatkan untuk `--start-time` dan `--end-time` menggunakan format ISO8601 yang lebih luas dan format datetime yang lebih ramah pengguna
* Validasi yang ditingkatkan untuk `--event-hub` dan `--event-hub-rule` argumen untuk `monitor diagnostic-settings create`

### <a name="network"></a>Jaringan
* Ditambahkan `--app-gateway-address-pools` dan `--gateway-name` argumen ke `nic create`, untuk mendukung penambahan kumpulan alamat backend gateway aplikasi ke NIC
* Ditambahkan `--app-gateway-address-pools` dan `--gateway-name` argumen ke `nic ip-config create/update`, untuk mendukung penambahan kumpulan alamat backend gateway aplikasi ke NIC

### <a name="servicebus"></a>ServiceBus
* Menambahkan Read-Only `migration_state` ke MigrationConfigProperties untuk menampilkan Standar Bus Layanan saat ini ke status migrasi namespace Premium

### <a name="sql"></a>SQL
* Tetap `sql failover-group create` dan `sql failover-group update` bekerja dengan kebijakan failover Manual

### <a name="storage"></a>Penyimpanan
* Pemformatan output tetap `az storage cors list` , semua item menampilkan kunci "Layanan" yang benar
* Menambahkan `--bypass-immutability-policy` parameter untuk penghapusan kontainer yang diblokir immutability-policy

### <a name="vm"></a>VM
* Terapkan mode `None` caching disk untuk seri mesin Lv / Lv2 di `[vm|vmss] create`
* Daftar ukuran dukungan yang diperbarui yang mendukung akselerator jaringan untuk `vm create`
* Menambahkan argumen yang diketik kuat untuk konfigurasi iops dan mbps ultrassd untuk `disk create`

## <a name="october-16-2018"></a>16 Oktober 2018

Versi 2.0.48

### <a name="vm"></a>VM
* Memperbaiki masalah SDK yang menyebabkan instllation Homebrew gagal

## <a name="october-9-2018"></a>9 Oktober 2018

Versi 2.0.47

### <a name="core"></a>Core
* Penanganan kesalahan yang ditingkatkan untuk kesalahan "Permintaan Buruk"

### <a name="acr"></a>ACR
* Menambahkan dukungan untuk format tabel serupa sebagai klien helm

### <a name="acs"></a>ACS
* Ditambahkan `aks [create|scale] --nodepool-name` untuk mengkonfigurasi nama nodepool, dipotong menjadi 12 karakter, default - nodepool1
* Diperbaiki untuk jatuh kembali ke 'scp' ketika Parimiko gagal
* Diubah `aks create` menjadi tidak lagi membutuhkan `--aad-tenant-id`
* Peningkatan penggabungan kredensial Kubernetes saat entri duplikat hadir

### <a name="container"></a>Kontainer
* Diubah `functionapp create` untuk mendukung pembuatan jenis paket konsumsi Linux dengan runtime tertentu
* [PRATINJAU] Menambahkan dukungan untuk hosting webapps di kontainer Windows

### <a name="event-hub"></a>Pusat Aktivitas
* Perintah tetap `eventhub update`
* [MELANGGAR PERUBAHAN] Perintah `list` yang diubah untuk menangani kesalahan untuk sumber daya NotFound(404) dengan cara yang khas alih-alih menampilkan daftar kosong

### <a name="extensions"></a>Ekstensi
* Memperbaiki masalah dengan mencoba menambahkan ekstensi yang sudah diinstal

### <a name="hdinsight"></a>HDInsight
* Rilis awal

### <a name="iot"></a>IoT
* Menambahkan comand instalasi ekstensi ke spanduk yang dijalankan pertama

### <a name="keyvault"></a>Az.KeyVault
* Diubah untuk membatasi commmand penyimpanan keyvault ke profil API terbaru

### <a name="network"></a>Jaringan
* Tetap `network dns zone create`: Perintah berhasil meskipun pengguna telah mengonfigurasi lokasi default. Lihat #6052
* Tidak digunakan `--remote-vnet-id` lagi untuk `network vnet peering create`
* Ditambahkan `--remote-vnet` ke `network vnet peering create` mana menerima nama atau ID
* Menambahkan dukungan untuk beberapa awalan `network vnet create` subnet ke dengan `--subnet-prefixes`
* Menambahkan dukungan untuk beberapa awalan `network vnet subnet [create|update]` subnet ke dengan `--address-prefixes`
* Memperbaiki masalah dengan `network application-gateway create` yang mencegah pembuatan gateway dengan `WAF_v2` atau `Standard_v2` SKU
* Menambahkan `--service-endpoint-policy` argumen kenyamanan ke `network vnet subnet update`

### <a name="role"></a>Peran
* Menambahkan dukungan untuk mencantumkan pemilik aplikasi Azure AD ke `ad app owner`
* Menambahkan dukungan untuk mencantumkan pemilik utama layanan Azure AD ke `ad sp owner`
* Diubah untuk memastikan definisi peran membuat perintah pembaruan & menerima beberapa konfigurasi izin
* Diubah `ad sp create-for-rbac` untuk memastikan halaman beranda URI selalu "https"

### <a name="service-bus"></a>Service Bus
* [MELANGGAR PERUBAHAN] Perintah `list` yang diubah untuk menangani kesalahan untuk sumber daya NotFound(404) dengan cara yang khas alih-alih menampilkan daftar kosong

### <a name="vm"></a>VM
* Memperbaiki bidang kosong `accessSas` di `disk grant-access`
* Diubah `vmss create` untuk memesan rentang port frontend yang cukup besar untuk menangani overprovisioning
* Perintah pemutakhiran tetap untuk `sig`
* Menambahkan `--no-wait` dukungan untuk mengelola versi gambar di `sig`
* Diubah `vm list-ip-addresses` untuk menampilkan zona ketersediaan alamat IP publik
* Diubah `[vm|vmss] disk attach` untuk mengatur lun default disk ke tempat pertama yang tersedia

## <a name="september-21-2018"></a>21 September 2018

Versi 2.0.46

### <a name="acr"></a>ACR
* Menambahkan perintah Tugas ACR
* Menambahkan perintah lari cepat
* Grup perintah yang `build-task` tidak digunakan lagi
* Menambahkan `helm` grup perintah untuk mendukung pengelolaan bagan helm dengan ACR
* Menambahkan dukungan untuk idempotent create for managed registry
* Menambahkan bendera tanpa format untuk menampilkan log build

### <a name="acs"></a>ACS
* `install-connector` Mengubah perintah untuk mengatur AKS Master FQDN
* Memperbaiki pembuatan penetapan peran untuk vnet-subnet-id saat tidak menentukan prinsipal layanan dan skip-role-assignemnt

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk manajemen operasi webjobs (terus menerus dan dipicu)
* az webapp config set supports --fts-state propertyAlso added support fot az functionapp config set & show
* Menambahkan dukungan untuk membawa penyimpanan Anda sendiri untuk webapps
* Menambahkan dukungan untuk listingan dan memulihkan aplikasi web yang dihapus

### <a name="batch"></a>Batch
* Mengubah menambahkan tugas `--json-file` untuk mendukung sintaks AddTaskCollectionParameter
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
* Ditambahkan `--network-profile` untuk melewati profil jaringan
* Ditambahkan `--subnet`, `--vnet_name`untuk memungkinkan membuat grup kontainer dalam VNET
* Mengubah output tabel untuk menampilkan status grup kontainer

### <a name="datalake"></a>Datalake
* Perintah tambahan untuk aturan jaringan virtual

### <a name="interactive-shell"></a>Shell Interaktif
* Memperbaiki kesalahan pada Windows di mana perintah gagal berjalan dengan baik
* Memperbaiki masalah pemuatan perintah dalam interaktif yang disebabkan oleh objek yang tidak digunakan lagi

### <a name="iot"></a>IoT
* Menambahkan dukungan untuk merutekan IoT Hub

### <a name="key-vault"></a>Key Vault
* Impor kunci Kunci Vault tetap untuk kunci RSA

### <a name="network"></a>Jaringan
* Menambahkan `network public-ip prefix` perintah untuk mendukung fitur awalan IP publik
* Menambahkan `network service-endpoint` perintah untuk mendukung fitur kebijakan titik akhir layanan
* Menambahkan `network lb outbound-rule` perintah untuk mendukung pembuatan aturan keluar Standard Load Balancer
* Tambahkan `--public-ip-prefix` ke `network lb frontend-ip create/update` untuk mendukung konfigurasi IP frontend menggunakan awalan IP publik
* Tambahkan `--enable-tcp-reset` ke `network lb rule/inbound-nat-rule/inbound-nat-pool create/update`
* Tambahkan `--disable-outbound-snat` ke `network lb rule create/update`
* Memungkinkan `network watcher flow-log show/configure` untuk digunakan dengan NSGs klasik
* Perintah Tambahkan `network watcher run-configuration-diagnostic`
* Memperbaiki `network watcher test-connectivity` perintah dan menambahkan `--method`, `--valid-status-codes` dan `--headers` properti
* `network express-route create/update`: Tambahkan `--allow-global-reach` bendera
* `network vnet subnet create/update`: Tambahkan dukungan untuk `--delegation`
* Perintah tambahan `network vnet subnet list-available-delegations`
* `network traffic-manager profile create/update`: Menambahkan dukungan untuk `--interval`, `--timeout` dan `--max-failures` untuk konfigurasi Monitor Opsi `--monitor-path`usang, `--monitor-port` dan `--monitor-protocol` mendukung `--path`, `--port`, `--protocol`
* `network lb frontend-ip create/update`: Memperbaiki logika untuk mengatur metode alokasi IP pribadiJika alamat IP pribadi disediakan, alokasi akan statisJika tidak ada alamat IP pribadi yang disediakan, atau string kosong disediakan untuk alamat IP pribadi, alokasinya dinamis.
* `dns record-set * create/update`: Tambahkan dukungan untuk `--target-resource`
* Menambahkan `network interface-endpoint` perintah ke objek titik akhir antarmuka kueri
* Tambahkan `network profile show/list/delete` untuk pengelolaan sebagian profil jaringan
* Menambahkan `network express-route peering connection` perintah untuk mengelola koneksi peering antara ExpressRoutes

### <a name="rdbms"></a>RDBMS
* Menambahkan dukungan untuk layanan MariaDB

### <a name="reservation"></a>Reservasi
* Menambahkan CosmosDb dalam tipe enum sumber daya yang dipesan
* Menambahkan properti nama dalam model Patch

### <a name="manage-app"></a>Kelola Aplikasi
* Memperbaiki bug dalam `managedapp create --kind MarketPlace` menyebabkan pembuatan instans aplikasi yang dikelola Marketplace macet
* Perintah `feature` yang diubah untuk dibatasi ke profil yang didukung

### <a name="role"></a>Peran
* Menambahkan dukungan untuk mencantumkan keanggotaan grup pengguna

### <a name="signalr"></a>SignalR
* Rilis pertama

### <a name="storage"></a>Penyimpanan
* Parameter tambahan `--auth-mode login` untuk penggunaan kredensial login pengguna untuk otorisasi blob dan antrean
* Ditambahkan `storage container immutability-policy/legal-hold` untuk mengelola penyimpanan yang tidak berubah

### <a name="vm"></a>VM
* Memperbaiki masalah saat `vm create --generate-ssh-keys` menimpa file kunci pribadi jika file kunci publik hilang (#4725, #6780)
* Menambahkan dukungan untuk galeri gambar bersama melalui `az sig`

## <a name="august-28-2018"></a>28 Agustus 2018

Versi 2.0.45

### <a name="core"></a>Core

* Memperbaiki masalah memuat file konfigurasi kosong
* Menambahkan dukungan untuk profil `2018-03-01-hybrid` untuk Azure Stack

### <a name="acr"></a>ACR

* Menambahkan solusi untuk operasi runtime tanpa permintaan ARM
* Diubah untuk mengecualikan file kontrol versi (misalnya, .git, .gitignore) dari tar yang diunggah secara default dalam `build` perintah

### <a name="acs"></a>ACS

* Diubah `aks create` menjadi default ke `Standard_DS2_v2` VM
* Diubah `aks get-credentials` untuk sekarang memanggil api baru untuk mendapatkan kredensial klaster

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk CORS di functionapp & webapp
* Menambahkan dukungan tag ARM pada membuat perintah
* Diubah `[webapp|functionapp] identity show` untuk keluar dengan kode 3 pada sumber daya yang hilang

### <a name="backup"></a>Cadangan

* Diubah `backup vault backup-properties show` untuk keluar dengan kode 3 pada sumber daya yang hilang

### <a name="bot-service"></a>Layanan Bot

* Rilis CLI Layanan Bot Awal

### <a name="cognitive-services"></a>Cognitive Services

* Menambahkan parameter `--api-properties,` baru yang diperlukan untuk membuat beberapa layanan

### <a name="iot"></a>IoT

* Memperbaiki masalah dengan mengaitkan hub tertaut

### <a name="monitor"></a>Monitor

* Perintah tambahan `monitor metrics alert` untuk peringatan metrik mendekati waktu nyata
* Perintah yang `monitor alert` tidak digunakan lagi

### <a name="network"></a>Jaringan

* Diubah `network application-gateway ssl-policy predefined show` untuk keluar dengan kode 3 pada sumber daya yang hilang

### <a name="resource"></a>Sumber daya

* Diubah `provider operation show` untuk keluar dengan kode 3 pada sumber daya yang hilang

### <a name="storage"></a>Penyimpanan

* Diubah `storage share policy show` untuk keluar dengan kode 3 pada sumber daya yang hilang

### <a name="vm"></a>VM

* Diubah `vm/vmss identity show` untuk keluar dengan kode 3 pada sumber daya yang hilang
* Tidak digunakan `--storage-caching` lagi untuk `vm create`

## <a name="auguest-14-2018"></a>14 Agustus 2018

Versi 2.0.44

### <a name="core"></a>Core

* Memperbaiki tampilan numerik dalam `table` output
* Menambahkan format output YAML

### <a name="telemetry"></a>Telemetri

* Peningkatan pelaporan telemetri

### <a name="acr"></a>ACR

* Perintah `content-trust policy` tambahan
* Memperbaiki masalah di mana `.dockerignore` tidak ditangani dengan benar

### <a name="acs"></a>ACS

* Diubah `az acs/aks install-cli` untuk menginstal di bawah `%USERPROFILE%\.azure-kubectl` pada Windows
* Diubah `az aks install-connector` untuk mendeteksi apakah klaster memiliki RBAC dan mengonfigurasi Konektor ACI dengan tepat
* Diubah menjadi penetapan peran ke subnet saat disediakan
* Menambahkan opsi baru untuk "lewati penetapan peran" untuk subnet saat disediakan
* Diubah untuk melewati penetapan peran ke subnet saat tugas sudah ada

### <a name="appservice"></a>AppService

* Memperbaiki bug yang mencegah pembuatan aplikasi fungsi menggunakan akun penyimpanan di grup sumber daya eksternal
* Memperbaiki kerusakan pada penyebaran zip

### <a name="batchai"></a>BatchAI

* Mengubah output logger untuk pembuatan akun penyimpanan otomatis untuk menentukan " *grup* sumber daya".

### <a name="container"></a>Kontainer

* Ditambahkan `--secure-environment-variables` untuk meneruskan variabel lingkungan yang aman ke kontainer

### <a name="iot"></a>IoT

* [MELANGGAR PERUBAHAN] Menghapus perintah usang yang telah pindah ke ekstensi iot
* Elemen yang diperbarui untuk tidak mengasumsikan `azure-devices.net` domain

### <a name="iot-central"></a>Iot Tengah

* Rilis awal modul IoT Central

### <a name="keyvault"></a>Az.KeyVault


* Perintah tambahan untuk mengelola akun penyimpanan dan definisi sas
* Menambahkan perintah untuk aturan jaringan
* Menambahkan `--id` parameter ke operasi rahasia, kunci, dan sertifikat
* Menambahkan dukungan untuk versi multi-api mgmt KV mgmt
* Menambahkan dukungan untuk versi multi-api pesawat data KV

### <a name="relay"></a>Relay

* Rilis awal

### <a name="sql"></a>Sql

* Perintah `sql failover-group` tambahan

### <a name="storage"></a>Penyimpanan

* [MELANGGAR PERUBAHAN] Diubah `storage account show-usage` menjadi parameter yang memerlukan `--location` dan akan mencantumkan berdasarkan wilayah
* Parameter `--resource-group` yang diubah menjadi opsional untuk `storage account` perintah
* Menghapus peringatan 'Prasyarat gagal' untuk kegagalan individual dalam perintah batch untuk pesan agregat tunggal
* Mengubah `[blob|file] delete-batch` perintah menjadi tidak lagi menghasilkan array null
* Mengubah `blob [download|upload|delete-batch]` perintah untuk membaca sas-token dari url kontainer

### <a name="vm"></a>VM

* Menambahkan filter umum untuk `vm list-skus` kemudahan penggunaan

## <a name="july-31-2018"></a>31 Juli 2018

Versi 2.0.43

### <a name="acr"></a>ACR

* Menambahkan `--with-secure-properties` bendera ke `acr build-task show` perintah
* Perintah tambahan `acr build-task update-build`

### <a name="acs"></a>ACS

* Diubah untuk mengembalikan 0 (sukses) saat berakhir `az aks browse` dengan menekan [Ctrl+C]

### <a name="batch"></a>Batch

* Memperbaiki bug saat menampilkan token AAD di cloudshell

### <a name="container"></a>Kontainer

* Persyaratan yang dihapus untuk `--log-analytics-workspace-key` nama atau ID saat dalam langganan yang ditetapkan

### <a name="network"></a>Jaringan

* Menambahkan dukungan dns ke 2017-03-09-profile for Azure Stack

### <a name="resource"></a>Sumber daya

* Ditambahkan `--rollback-on-error` untuk `group deployment create` menjalankan penyebaran yang diketahui-baik pada kesalahan
* Memperbaiki masalah di mana `--parameters {}` dengan `group deployment create` mengakibatkan kesalahan

### <a name="role"></a>Peran

* Menambahkan dukungan untuk profil tumpukan 2017-03-09-profile
* Memperbaiki masalah di mana parameter `app update` pembaruan generik tidak akan berfungsi dengan benar

### <a name="search"></a>Cari

* Perintah tambahan untuk layanan Azure Search

### <a name="service-bus"></a>Service Bus

* Menambahkan grup perintah migrasi untuk memigrasikan namespace dari Bus Layanan Standard ke Premium
* Menambahkan properti opsional baru ke antrean Bus Layanan dan Langganan
  *  `--enable-batched-operations` dan `--enable-dead-lettering-on-message-expiration` di `queue`
  *  `--dead-letter-on-filter-exceptions` di `subscriptions`

### <a name="storage"></a>Penyimpanan

* Menambahkan dukungan untuk mengunduh file besar menggunakan satu koneksi
* Perintah yang dikonversi `show` yang terlewatkan karena gagal dengan kode keluar 3 pada sumber daya yang hilang

### <a name="vm"></a>VM

* Menambahkan dukungan ke daftar kumpulan ketersediaan menurut langganan
* Menambahkan dukungan untuk `StandardSSD_LRS`
* Menambahkan dukungan untuk grup keamanan aplikasi saat membuat set skala VM
* [MELANGGAR PERUBAHAN] Diubah `[vm|vmss] create`, `[vm|vmss] identity assign`, dan `[vm|vmss] identity remove` untuk mengeluarkan identitas yang ditetapkan pengguna dalam format kamus

## <a name="july-18-2018"></a>18 Juli 2018

Versi 2.0.42

### <a name="core"></a>Core

* Menambahkan dukungan untuk login berbasis browser di jendela bash WSL
* Menambahkan `--force-string` bendera ke semua perintah pembaruan umum
* [MELANGGAR PERUBAHAN] Mengubah perintah 'tampilkan' untuk mencatat pesan kesalahan dan gagal dengan kode keluar 3 pada sumber daya yang hilang

### <a name="acr"></a>ACR

* [MELANGGAR PERUBAHAN] Diperbarui '--no-push' ke bendera murni dalam perintah 'acr build'
* Ditambahkan `show` dan `update` perintah di bawah `acr repository` grup
* Menambahkan `--detail` bendera untuk `show-manifests` dan `show-tags` untuk menunjukkan informasi yang lebih rinci
* Parameter tambahan `--image` untuk mendukung mendapatkan detail build atau log menurut gambar

### <a name="acs"></a>ACS

* Diubah `az aks create` menjadi kesalahan jika `--max-pods` kurang dari 5

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk skus PremiumV2

### <a name="batch"></a>Batch

* Memperbaiki bug saat menggunakan kredensial token pada mode shell cloud
* Mengubah input JSON menjadi tidak sensitif terhadap kasus

### <a name="batch-ai"></a>Batch AI

* Perintah tetap `az batchai job exec`

### <a name="container"></a>Kontainer

* Menghapus persyaratan untuk nama pengguna dan kata sandi untuk registri non dockerhub
* Memperbaiki kesalahan saat membuat grup kontainer dari file yaml

### <a name="network"></a>Jaringan

* Menambahkan `--no-wait` dukungan ke `network nic [create|update|delete]`
* Ditambahkan `network nic wait`
* Argumen yang `--ids` tidak digunakan lagi untuk `network vnet [subnet|peering] list`
* Menambahkan `--include-default` bendera untuk menyertakan aturan keamanan default dalam output `network nsg rule list`

### <a name="resource"></a>Sumber daya

* Menambahkan `--no-wait` dukungan ke `group deployment delete`
* Menambahkan `--no-wait` dukungan ke `deployment delete`
* Perintah tambahan `deployment wait`
* Memperbaiki masalah saat perintah tingkat `az deployment` langganan keliru muncul untuk profil profil 2017-03-09-profil

### <a name="sql"></a>SQL

* Memperbaiki 'Nama grup sumber daya yang disediakan ... tidak cocok dengan nama dalam kesalahan Url saat menentukan nama `sql db copy` `sql db replica create` dan perintah kumpulan elastis
* Perbolehkan mengonfigurasi server sql default dengan menjalankan `az configure --defaults sql-server=<name>`
* Formatter tabel yang diimplementasikan untuk `sql server`, `sql server firewall-rule`, `sql list-usages`, dan `sql show-usage` perintah

### <a name="storage"></a>Penyimpanan

* Menambahkan `pageRanges` properti ke `storage blob show` output yang akan diisi untuk blob halaman

### <a name="vm"></a>VM

* [MELANGGAR PERUBAHAN] Diubah `vmss create` untuk digunakan `Standard_DS1_v2` sebagai ukuran instans default
* Menambahkan `--no-wait` dukungan untuk `vm extension [set|delete]` dan `vmss extension [set|delete]`
* Ditambahkan `vm extension wait`

## <a name="july-3-2018"></a>3 Juli 2018

### <a name="version-2041"></a>Versi 2.0.41

### <a name="aks"></a>AKS

* Mengubah pemantauan untuk menggunakan ID langganan

### <a name="version-2040"></a>Versi 2.0.40

### <a name="core"></a>Core

* Menambahkan alur kode otorisasi baru untuk login interaktif

### <a name="acr"></a>ACR

* Menambahkan status pembuatan polling
* Menambahkan dukungan untuk nilai enum case-insensitive
* Ditambahkan `--top` dan `--orderby` parameter untuk `show-manifests`

### <a name="acs"></a>ACS

* [MELANGGAR PERUBAHAN] Aktifkan kontrol akses berbasis peran Kubernetes secara default
* Menambahkan `--disable-rbac` argumen dan usang `--enable-rbac` karena itu default sekarang
* Opsi yang diperbarui untuk `aks browse` perintah. Menambahkan `--listen-port` dukungan
* Memperbarui paket bagan helm default untuk `aks install-connector` perintah. Gunakan virtual-kubelet-for-aks-latest.tgz
* Ditambahkan `aks enable-addons` dan `aks disable-addons` perintah untuk memperbarui klaster yang ada

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk menonaktifkan identitas melalui `webapp identity remove`
* Tag yang dihapus `preview` untuk fitur Identitas

### <a name="backup"></a>Cadangan

* Definisi modul yang diperbarui

### <a name="batchai"></a>BatchAI

* Memperbaiki output tabel untuk `batchai cluster node list` dan `batchai job node list` perintah

### <a name="cloud"></a>Cloud

* Menambahkan `acr login` akhiran server ke konfigurasi cloud

### <a name="container"></a>Kontainer

* Diubah `container create` menjadi default ke operasi yang sudah berjalan lama
* Menambahkan parameter `--log-analytics-workspace` Analitik Log dan `--log-analytics-workspace-key`
* Menambahkan `--protocol` parameter untuk menentukan protokol jaringan mana yang akan digunakan

### <a name="extension"></a>Ekstensi

* Diubah `extension list-available` untuk hanya menampilkan ekstensi yang kompatibel dengan versi CLI

### <a name="network"></a>Jaringan

* Memperbaiki masalah di mana jenis rekaman peka huruf besar/kecil ([#6602](https://github.com/Azure/azure-cli/issues/6602))

### <a name="rdbms"></a>Rdbms

* Perintah `[postgres|myql] server vnet-rule` tambahan

### <a name="resource"></a>Sumber daya

* Menambahkan grup operasi baru `deployment`

### <a name="vm"></a>VM

* Menambahkan dukungan untuk menghapus identitas yang ditetapkan sistem

## <a name="june-25-2018"></a>25 Juni 2018

Versi 2.0.39

### <a name="cli"></a>CLI

* Pemangkasan file yang diperbarui di penginstal MSI untuk memperbaiki masalah instalasi ekstensi

## <a name="june-19-2018"></a>19 Juni 2018 pukul

Versi 2.0.38

### <a name="core"></a>Core

* Menambahkan dukungan global untuk `--subscription` sebagian besar perintah

### <a name="acr"></a>ACR

* Ditambahkan `azure-storage-blob` sebagai dependensi
* Mengubah konfigurasi CPU default dengan `acr build-task create` menggunakan 2 core

### <a name="acs"></a>ACS

* Opsi perintah yang `aks use-dev-spaces` diperbarui. Menambahkan `--update` dukungan
* Diubah `aks get-credentials --admin` untuk tidak menggantikan konteks pengguna di `$HOME/.kube/config`
* Mengekspos properti baca-saja `nodeResourceGroup` pada klaster terkelola
* Memperbaiki `acs browse` kesalahan perintah
* Dibuat `--connector-name` opsional untuk `aks install-connector`, `aks upgrade-connector` dan `aks remove-connector`
* Menambahkan wilayah Azure Container Instance baru untuk `aks install-connector`
* Menambahkan lokasi yang dinormalisasi ke dalam nama rilis helm dan nama node ke `aks install-connector`

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk versi urllib yang lebih baru
* Menambahkan dukungan untuk `functionapp create` menggunakan paket layanan aplikasi dari grup sumber daya eksternal

### <a name="batch"></a>Batch

* Ketergantungan yang dihapus `azure-batch-extensions`

### <a name="batch-ai"></a>Batch AI

* Menambahkan dukungan untuk ruang kerja. Ruang kerja memungkinkan untuk mengelompokkan klaster, file-server, dan eksperimen dalam grup yang menghilangkan batasan jumlah sumber daya dapat dibuat
* Menambahkan dukungan untuk eksperimen. Eksperimen memungkinkan untuk mengelompokkan pekerjaan dalam koleksi yang menghilangkan batasan jumlah pekerjaan yang dibuat
* Menambahkan dukungan untuk mengonfigurasi `/dev/shm` pekerjaan yang berjalan dalam kontainer docker
* Ditambahkan `batchai cluster node exec` dan `batchai job node exec` perintah. Perintah ini memungkinkan untuk menjalankan perintah apa pun langsung pada node dan menyediakan fungsionalitas untuk penerusan port.
* Menambahkan dukungan untuk `--ids` `batchai` perintah
* [MELANGGAR PERUBAHAN] Semua klaster dan server file harus dibuat di bawah ruang kerja
* [MELANGGAR PERUBAHAN] Pekerjaan harus dibuat berdasarkan eksperimen
* [MELANGGAR PERUBAHAN] Dihapus `--nfs-resource-group` dari `cluster create` dan `job create` perintah. Untuk memasang NFS milik ruang kerja/grup sumber daya yang berbeda, sediakan ID ARM server file melalui `--nfs` opsi
* [MELANGGAR PERUBAHAN] Dihapus `--cluster-resource-group` dari `job create` perintah. Untuk mengirimkan pekerjaan pada klaster milik ruang kerja/grup sumber daya yang berbeda, sediakan ID ARM klaster melalui `--cluster` opsi
* [MELANGGAR PERUBAHAN] Atribut yang dihapus `location` dari pekerjaan, klaster, dan server file. Lokasi sekarang adalah atribut ruang kerja.
* [MELANGGAR PERUBAHAN] Dihapus `--location` dari `job create`, `cluster create` dan `file-server create` perintah
* [MELANGGAR PERUBAHAN] Mengubah nama opsi singkat untuk membuat antarmuka lebih konsisten:
  - Berganti nama [`--config`, `-c`] menjadi [`--config-file`, `-f`]
  - Berganti nama [`--cluster`, `-r`] menjadi [`--cluster`, `-c`]
  - Berganti nama [`--cluster`, `-n`] menjadi [`--cluster`, `-c`]
  - Berganti nama [`--job`, `-n`] menjadi [`--job`, `-j`]

### <a name="maps"></a>Maps

* [MELANGGAR PERUBAHAN] Diubah `maps account create` untuk mewajibkan menerima Ketentuan Layanan baik dengan prompt interaktif atau `--accept-tos` bendera

### <a name="network"></a>Jaringan

* Menambahkan dukungan `https` ke `network lb probe create` [#6571](https://github.com/Azure/azure-cli/issues/6571)
* Memperbaiki masalah di mana `--endpoint-status` peka huruf besar/kecil. [#6502](https://github.com/Azure/azure-cli/issues/6502)

### <a name="reservations"></a>Reservasi

* [MELANGGAR PERUBAHAN] Menambahkan parameter `ReservedResourceType` yang diperlukan ke `reservations catalog show`
* Menambahkan parameter `Location`ke `reservations catalog show`
* [MELANGGAR PERUBAHAN] Dihapus `kind` dari `ReservationProperties`
* [MELANGGAR PERUBAHAN] Berganti `capabilities` nama menjadi `sku_properties` di `Catalog`
* [MELANGGAR PERUBAHAN] Dihapus `size` dan `tier` properti dari `Catalog`
* Menambahkan parameter `InstanceFlexibility` ke `reservations reservation update`

### <a name="role"></a>Peran

* Penanganan kesalahan yang ditingkatkan

### <a name="sql"></a>SQL

* Memperbaiki kesalahan membingungkan saat menjalankan `az sql db list-editions` lokasi yang tidak tersedia untuk langganan Anda

### <a name="storage"></a>Penyimpanan

* Mengubah output `storage blob download` tabel agar lebih mudah dibaca

### <a name="vm"></a>VM

* Pemeriksaan ukuran vm refined yang ditingkatkan untuk dukungan jaringan yang dipercepat di `vm create`
* Peringatan tambahan untuk `vmss create` itu ukuran vm default akan dialihkan dari `Standard_D1_v2` ke `Standard_DS1_v2`
* Ditambahkan `--force-update` untuk `[vm|vmss] extension set` memperbarui ekstensi bahkan ketika konfigurasi tidak berubah

## <a name="june-13-2018"></a>13 Juni 2018

### <a name="version-2037"></a>Versi 2.0.37

### <a name="core"></a>Core

* Telemetri interaktif yang ditingkatkan

### <a name="version-2036"></a>Versi 2.0.36

### <a name="aks"></a>AKS

* Menambahkan opsi jaringan lanjutan ke `aks create`
* Menambahkan argumen untuk `aks create` mengaktifkan pemantauan dan perutean HTTP
* Menambahkan `--no-ssh-key` argumen ke `aks create`
* Menambahkan `--enable-rbac` argumen ke `aks create`
* [PRATINJAU] Menambahkan dukungan untuk autentikasi Azure Active Directory ke`aks create`

### <a name="appservice"></a>AppService

* Memperbaiki masalah dengan versi urllib yang tidak kompatibel

## <a name="june-5-2018"></a>5 Juni 2018

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

* Memperbaiki bug dalam pemformatan tabel daftar kumpulan [[Masalah #4378](https://github.com/Azure/azure-cli/issues/4378)]

### <a name="iot"></a>IOT

* Menambahkan dukungan untuk membuat Hub IoT Tingkat Dasar

### <a name="network"></a>Jaringan

* Ditingkatkan `network vnet peering`

### <a name="policy-insights"></a>Policy Insights

* Rilis Awal

### <a name="arm"></a>ARM

* Perintah `account management-group` tambahan.

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

* Menambahkan mimetype tambahan untuk json dan javascript untuk disimpulkan dari ekstensi file

### <a name="vm"></a>VM

* Diubah `vm list-skus` untuk menggunakan kolom tetap dan menambahkan peringatan bahwa `Tier` dan `Size` akan dihapus
* Opsi tambahan `--accelerated-networking` ke `vm create`
* Ditambahkan `--tags` ke `identity create`

## <a name="may-22-2018"></a>22 Mei 2018

Versi 2.0.33

### <a name="core"></a>Core

* Menambahkan dukungan untuk memperluas `@` nama file

### <a name="acs"></a>ACS

* Menambahkan perintah `aks use-dev-spaces` Dev-Spaces baru dan `aks remove-dev-spaces`
* Memperbaiki kesalahan ketik dalam pesan bantuan

### <a name="appservice"></a>AppService

* Perintah pembaruan generik yang ditingkatkan
* Menambahkan dukungan async untuk `webapp deployment source config-zip`

### <a name="container"></a>Kontainer

* Menambahkan dukungan untuk mengekspor grup kontainer dalam format yaml
* Menambahkan dukungan untuk menggunakan file yaml untuk membuat / memperbarui grup kontainer

### <a name="extension"></a>Ekstensi

* Penghapusan ekstensi yang ditingkatkan

### <a name="interactive"></a>Interaktif

* Mengubah log menjadi mute parser untuk penyelesaian
* Peningkatan penanganan cache bantuan yang buruk

### <a name="keyvault"></a>Az.KeyVault

* Perintah keyvault tetap untuk bekerja di cloud shell atau VM dengan identitas

### <a name="network"></a>Jaringan

* Memperbaiki masalah di mana `network watcher show-topology` tidak akan bekerja dengan vnet dan / atau nama subnet [#6326](https://github.com/Azure/azure-cli/issues/6326)
* Memperbaiki masalah di mana beberapa `network watcher` perintah akan mengklaim Network Watcher tidak diaktifkan untuk wilayah ketika sebenarnya [# 6264](https://github.com/Azure/azure-cli/issues/6264)

### <a name="sql"></a>SQL

* [MELANGGAR PERUBAHAN] Objek respons yang diubah yang dikembalikan dari `db` dan `dw` perintah:
    * Properti yang diganti `serviceLevelObjective` namanya menjadi `currentServiceObjectiveName`
    * Dihapus `currentServiceObjectiveId` dan `requestedServiceObjectiveId` properti
    * Properti `maxSizeBytes` yang diubah menjadi nilai integer, bukan string
* [MELANGGAR PERUBAHAN] Mengubah hal-hal berikut `db` dan `dw` properti menjadi baca-saja:
    * `requestedServiceObjectiveName`.  Untuk memperbarui, gunakan `--service-objective` parameter atau atur `sku.name` properti
    * `edition`. Untuk memperbarui, gunakan `--edition` parameter atau atur `sku.tier` properti
    * `elasticPoolName`. Untuk memperbarui, gunakan `--elastic-pool` parameter atau atur `elasticPoolId` properti
* [MELANGGAR PERUBAHAN] Mengubah properti berikut `elastic-pool` menjadi baca-saja:
    * `edition`. Untuk memperbarui, gunakan `--edition` parameter
    * `dtu`. Untuk memperbarui, gunakan `--capacity` parameter
    *  `databaseDtuMin`. Untuk memperbarui, gunakan `--db-min-capacity` parameter
    *  `databaseDtuMax`. Untuk memperbarui, gunakan `--db-max-capacity` parameter
* Ditambahkan `--family` dan `--capacity` parameter ke `db`, `dw`, dan `elastic-pool` perintah.
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

* Memperbaiki pengecualian yang tidak tertangani saat mengambil rahasia dari akun utama layanan dengan sertifikat
* Menambahkan dukungan terbatas untuk argumen posisi
* Perbaiki masalah di mana `--query` tidak dapat digunakan dengan `--ids`. [#5591](https://github.com/Azure/azure-cli/issues/5591)
* Skenario perpipaan yang ditingkatkan dari perintah saat menggunakan `--ids`. Mendukung `-o tsv` dengan kueri yang ditentukan atau `-o json` tanpa menentukan kueri
* Menambahkan saran perintah tentang kesalahan jika pengguna memiliki kesalahan ketik dalam perintah mereka
* Kesalahan yang ditingkatkan saat pengguna mengetik `az ''`
* Menambahkan jenis sumber daya khusus dukungan untuk modul perintah dan ekstensi

### <a name="acr"></a>ACR

* Menambahkan perintah ACR Build
* Sumber daya yang ditingkatkan tidak menemukan pesan kesalahan
* Peningkatan kinerja pembuatan sumber daya dan penanganan kesalahan
* Peningkatan login acr di konsol non-standar dan WSL
* Perintah repositori yang ditingkatkan pesan kesalahan
* Kolom tabel dan pemesanan yang diperbarui

### <a name="acs"></a>ACS

* Peringatan tambahan yang `az aks` merupakan layanan pratinjau
* Memperbaiki masalah `aks install-connector` izin saat `--aci-resource-group` tidak ditentukan

### <a name="ams"></a>AMS

* Rilis awal - Kelola sumber daya Azure Media Services

### <a name="appservice"></a>Layanan aplikasi

* Memperbaiki bug saat `webapp delete` `--slot` disediakan
* Dihapus `--runtime-version` dari `webapp auth update`
* Menambahkan dukungan untuk mintlsversion\_\_ & https2.0
* Menambahkan dukungan untuk multicontainer

### <a name="batch-ai"></a>Batch AI

* Diubah `batchai create cluster` untuk menghormati prioritas vm yang dikonfigurasi dalam file konfigurasi klaster

### <a name="cognitive-services"></a>Cognitive Services

* Memperbaiki kesalahan ketik misalnya untuk `cognitiveservices account create` [#5603](https://github.com/Azure/azure-cli/issues/5603)

### <a name="consumption"></a>Consumption

* Menambahkan perintah baru untuk API anggaran

### <a name="container"></a>Kontainer

* Persyaratan yang dihapus `--registry-server` `container create` saat server registri disertakan dalam nama gambar

### <a name="cosmos-db"></a>Cosmos DB

* Memperkenalkan dukungan VNET untuk Azure CLI - Cosmos DB

### <a name="dms"></a>DMS

* Rilis awal - Menambahkan dukungan untuk skenario migrasi SQL ke Azure SQL

### <a name="extension"></a>Ekstensi

* Memperbaiki bug tempat metadata ekstensi berhenti ditampilkan

### <a name="interactive"></a>Interaktif

* Memungkinkan completers interaktif berfungsi dengan argumen posisi
* Output yang lebih mudah digunakan saat pengguna mengetik\'
* Penyelesaian tetap untuk parameter tanpa bantuan
* Memperbaiki deskripsi untuk grup perintah

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
* Memperbaiki kesalahan ketik dalam `account get-access-token` ringkasan singkat

### <a name="redis"></a>Redis

* `redis patch-schedule patch-schedule show` Usang mendukung`redis patch-schedule show`
* Tidak digunakan `redis list-all`lagi. Fungsi ini telah dilipat menjadi `redis list`
* `redis import-method` Usang mendukung`redis import`
* Menambahkan dukungan untuk `--ids` berbagai perintah

### <a name="role"></a>Peran

* [MELANGGAR PERUBAHAN] Dihapus tidak digunakan lagi `ad sp reset-credentials`

### <a name="storage"></a>Penyimpanan

* Izinkan tujuan sas-token berlaku untuk sumber salinan blob jika sumber sas dan kunci akun tidak ditentukan
* Exposed --socket-timeout untuk unggahan dan unduhan blob
* Perlakukan nama gumpalan yang dimulai dengan pemisah jalur sebagai jalur relatif
* Izinkan `storage blob copy --source-sas` dengan memulai kueri char, '?'
* Diperbaiki `storage entity query --marker` untuk menerima daftar key=values

### <a name="vm"></a>VM

* Memperbaiki logika deteksi yang tidak valid pada blob uri yang tidak dikelola
* Menambahkan enkripsi disk dukungan dengan prinsipal layanan yang disediakan pengguna
* [MELANGGAR PERUBAHAN] Jangan gunakan VM 'ManagedIdentityExtension' untuk dukungan MSI
* Menambahkan dukungan untuk kebijakan penggusuran ke `vmss`
* [MELANGGAR PERUBAHAN] Dihapus `--ids` dari:
  * `vm extension list`
  * `vm secret list`
  * `vm unmanaged-disk list`
  * `vmss nic list`
* Menambahkan dukungan akselerator tulis
* Ditambahkan `vmss perform-maintenance`
* Diperbaiki `vm diagnostics set` untuk mendeteksi tipe OS VM dengan andal
* Diubah `vm resize` untuk memeriksa apakah ukuran yang diminta berbeda dari yang saat ini diatur dan diperbarui hanya pada perubahan


## <a name="april-10-2018"></a>10 April 2018

Versi 2.0.31

### <a name="acr"></a>ACR

* Peningkatan penanganan kesalahan dari fallback wincred

### <a name="acs"></a>ACS

* Tinta yang diubah membuat SPN berlaku selama 5 tahun

### <a name="appservice"></a>Layanan aplikasi

* [MELANGGAR PERUBAHAN]: Removed `assign-identity`
* Menetapkan pengecualian yang tidak diajarkan untuk paket webapp nonexistant

### <a name="batchai"></a>BatchAI

* Menambahkan dukungan untuk API 2018-03-01

  - Pemasangan tingkat pekerjaan
  - Variabel lingkungan dengan nilai rahasia
  - Setelan penghitung performa
  - Pelaporan segmen jalur khusus pekerjaan
  - Dukungan untuk subfolder dalam api file daftar
  - Penggunaan dan batas pelaporan
  - Izinkan untuk menentukan jenis caching untuk server NFS
  - Dukungan untuk gambar kustom
  - Menambahkan dukungan toolkit pyTorch

* Perintah tambahan `job wait` yang memungkinkan untuk menunggu penyelesaian pekerjaan dan melaporkan kode keluar pekerjaan
* Perintah tambahan `usage show` untuk mencantumkan penggunaan dan batasan sumber daya Batch AI saat ini untuk berbagai wilayah
* Awan nasional didukung
* Menambahkan argumen baris perintah pekerjaan untuk me-mount sistem file pada tingkat pekerjaan selain file konfigurasi
* Menambahkan lebih banyak opsi untuk menyesuaikan klaster - prioritas vm, subnet, jumlah node awal untuk klaster skala otomatis, menentukan gambar kustom
* Menambahkan opsi baris perintah untuk menentukan jenis caching untuk NFS terkelola Batch AI
* Sederhana menentukan sistem file mount dalam file konfigurasi. Sekarang Anda dapat menghilangkan kredensial untuk Azure File Share dan Azure Blob Containers - CLI akan mengisi kredensial yang hilang menggunakan kunci akun penyimpanan yang disediakan melalui parameter baris perintah atau ditentukan melalui variabel lingkungan atau akan meminta kunci dari Azure Storage (jika akun penyimpanan milik langganan saat ini)
* Perintah aliran file pekerjaan sekarang selesai secara otomatis saat pekerjaan selesai (berhasil, gagal, dihentikan, atau dihapus)
* Peningkatan `table` output untuk `show` operasi
* Opsi tambahan `--use-auto-storage` untuk pembuatan klaster. Opsi ini memudahkan pengelolaan akun penyimpanan dan memasang Azure File Share dan Azure Blob Containers ke klaster
* Opsi tambahan `--generate-ssh-keys` ke `cluster create` dan `file-server create`
* Menambahkan kemampuan untuk menyediakan tugas penyetelan node melalui baris perintah
* [MELANGGAR PERUBAHAN] Dipindahkan `job stream-file` dan `job list-files` perintah di bawah `job file` grup
* [MELANGGAR PERUBAHAN] Berganti `--admin-user-name` `--user-name` nama menjadi perintah `file-server create` agar konsisten dengan `cluster create` perintah

### <a name="billing"></a>Billing

* Perintah akun pendaftaran tambahan

### <a name="consumption"></a>Consumption

* Perintah `marketplace` tambahan
* [MELANGGAR PERUBAHAN] Berganti `reservations summaries` nama menjadi `reservation summary`
* [MELANGGAR PERUBAHAN] Berganti `reservations details` nama menjadi `reservation detail`
* [MELANGGAR PERUBAHAN] Opsi yang dihapus `--reservation-order-id` dan `--reservation-id` pendek untuk `reservation` perintah
* [MELANGGAR PERUBAHAN] Menghapus `--grain` opsi singkat untuk `reservation summary` perintah
* [MELANGGAR PERUBAHAN] Menghapus `--include-meter-details` opsi singkat untuk `pricesheet` perintah

### <a name="container"></a>Kontainer

* Menambahkan parameter `--gitrepo-url` `--gitrepo-dir` `--gitrepo-revision` pemasangan volume repo git dan `--gitrepo-mount-path`
* Tetap [#5926](https://github.com/Azure/azure-cli/issues/5926): `az container exec` gagal saat --container-name ditentukan

### <a name="extension"></a>Ekstensi

* Pesan pemeriksaan distribusi yang diubah menjadi tingkat debug

### <a name="interactive"></a>Interaktif

* Diubah untuk menghentikan penyelesaian atas perintah yang tidak dikenal
* Menambahkan kait peristiwa sebelum dan sesudah subtree perintah dibuat
* Penyelesaian tambahan untuk `--ids` parameter

### <a name="network"></a>Jaringan

* Tetap [# 5936](https://github.com/Azure/azure-cli/issues/5936): `application-gateway create` tag tidak bisa bertaruh set
* Menambahkan argumen `--auth-certs` untuk melampirkan sertifikat otentikasi untuk `application-gateway http-settings [create|update]`. [#4910](https://github.com/Azure/azure-cli/issues/4910)
* Perintah tambahan `ddos-protection` untuk membuat paket perlindungan DDoS
* Menambahkan dukungan `--ddos-protection-plan` untuk `vnet [create|update]` mengaitkan VNet dengan paket perlindungan DDoS
* Memperbaiki masalah dengan `--disable-bgp-route-propagation` bendera di `network route-table [create|update]`
* Menghapus argumen `--public-ip-address-type` dummy dan `--subnet-type` untuk `network lb [create|update]`
* Menambahkan dukungan untuk catatan TXT dengan urutan pelarian RFC 1035 ke `network dns zone [import|export]` dan `network dns record-set txt add-record`

### <a name="profile"></a>Profil

* Menambahkan dukungan untuk akun Azure Classic di `account list`
* [MELANGGAR PERUBAHAN] Argumen yang dihapus `--msi` & `--msi-port`

### <a name="rdbms"></a>RDBMS

* Perintah tambahan `georestore`
* Menghapus pembatasan ukuran penyimpanan dari `create` perintah

### <a name="resource"></a>Sumber daya

* Menambahkan dukungan untuk `--metadata``policy definition create`
* Menambahkan dukungan untuk `--metadata`, `--set`, `--add``--remove` untuk`policy definition update`

### <a name="sql"></a>SQL

* Ditambahkan `sql elastic-pool op list` dan `sql elastic-pool op cancel`

### <a name="storage"></a>Penyimpanan

* Pesan kesalahan yang ditingkatkan untuk string koneksi yang cacat

### <a name="vm"></a>VM

* Menambahkan dukungan untuk mengonfigurasi jumlah domain kesalahan platform ke `vmss create`
* Diubah `vmss create` menjadi default ke LB Standar untuk kumpulan skala yang dinonaktifkan zonal, besar, atau satu grup
* [MELANGGAR PERUBAHAN]: Removed `vm assign-identity`, `vm remove-identity and `vm format-secret`
* Menambahkan dukungan untuk SKU IP Publik ke `vm create`
* Ditambahkan `--keyvault` dan `--resource-group` argumen untuk `vm secret format` mendukung skenario di mana perintah tidak dapat menyelesaikan ID vault. [#5718](https://github.com/Azure/azure-cli/issues/5718)
* Kesalahan yang `[vm|vmss create]` lebih baik ketika lokasi grup sumber daya tidak memiliki dukungan zona


## <a name="march-27-2018"></a>27 Maret 2018

Versi 2.0.30

### <a name="core"></a>Core

* Tampilkan pesan untuk ekstensi yang ditandai sebagai pratinjau dalam bantuan

### <a name="acs"></a>ACS

* Memperbaiki kesalahan `aks install-cli` verifikasi sertifikat SSL di Cloud Shell

### <a name="appservice"></a>Layanan aplikasi

* Menambahkan dukungan khusus HTTPS ke `webapp update`
* Menambahkan dukungan untuk slot ke `az webapp identity [assign|show]` dan `az functionapp identity [assign|show]`

### <a name="backup"></a>Cadangan

* Menambahkan perintah `az backup protection isenabled-for-vm`baru . Perintah ini dapat digunakan untuk memeriksa apakah VM di-back up oleh brankas mana pun di langganan
* ID objek Azure yang diaktifkan untuk `--resource-group` dan `--vault-name` parameter untuk perintah berikut:
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

* Perintah tambahan `container exec` . Menjalankan perintah dalam kontainer untuk grup kontainer yang sedang berjalan
* Mengizinkan output tabel untuk membuat dan memperbarui grup kontainer

### <a name="extension"></a>Ekstensi

* Pesan tambahan untuk `extension add` jika ekstensi dalam pratinjau
* Diubah `extension list-available` untuk menampilkan data ekstensi lengkap dengan `--show-details`
* [MELANGGAR PERUBAHAN] Diubah `extension list-available` untuk menampilkan data ekstensi yang disederhanakan secara default

### <a name="interactive"></a>Interaktif

* Penyelesaian yang diubah untuk diaktifkan segera setelah pemuatan tabel perintah selesai
* Memperbaiki bug dengan menggunakan `--style` parameter
* Lexer interaktif instantiated setelah dump tabel perintah jika hilang
* Dukungan completer yang ditingkatkan

### <a name="lab"></a>Laboratorium

* Memperbaiki bug dengan `create environment` perintah

### <a name="monitor"></a>Monitor

* Menambahkan dukungan untuk `--top`, `--orderby` dan `--namespace` ke `metrics list` [#5785](https://github.com/Azure/azure-cli/issues/5785)
* Tetap [#4529](https://github.com/Azure/azure-cli/issues/5785): `metrics list` Menerima daftar metrik yang terpisah ruang untuk diambil
* Menambahkan dukungan `--namespace` ke `metrics list-definitions` [#5785](https://github.com/Azure/azure-cli/issues/5785)

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk zona DNS pribadi

### <a name="profile"></a>Profil

* Peringatan tambahan untuk `--identity-port` dan `--msi-port` untuk `login`

### <a name="rdbms"></a>RDBMS

* Menambahkan model bisnis GA API versi 2017-12-01

### <a name="resource"></a>Sumber daya

* [MELANGGAR PERUBAHAN]: Changed `provider operation [list|show]` to not require `--api-version`

### <a name="role"></a>Peran

* Menambahkan dukungan untuk konfigurasi akses yang diperlukan dan klien asli ke `az ad app create`
* Perintah `rbac` yang diubah untuk mengembalikan kurang dari 1000 DOKUMEN pada resolusi objek
* Menambahkan perintah manajemen kredensial `ad sp credential [reset|list|delete]`
* [MELANGGAR PERUBAHAN] Menghapus 'properti' dari `az role assignment [list|show]` output
* Menambahkan dukungan dan `dataActions` `notDataActions` izin ke `role definition`

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah saat mengunggah file dengan ukuran antara 195GB dan 200GB
* Diperbaiki [# 4049](https://github.com/Azure/azure-cli/issues/4049): Masalah dengan unggahan gumpalan tambahan yang mengabaikan parameter kondisi

### <a name="vm"></a>VM

* Peringatan tambahan untuk `vmss create` perubahan berbuka yang akan datang untuk set dengan 100+ instans
* Menambahkan dukungan tangguh zona ke `vm [snapshot|image]`
* Mengubah tampilan instans disk untuk melaporkan status enkripsi yang lebih baik
* [MELANGGAR PERUBAHAN] Diubah `vm extension delete` menjadi tidak lagi mengembalikan output

## <a name="march-13-2018"></a>13 Maret 2018

Versi 2.0.29

### <a name="acr"></a>ACR

* Menambahkan dukungan untuk `--image` parameter ke `repository delete`
* `--manifest` Usang dan `--tag` parameter `repository delete` perintah
* Perintah tambahan `repository untag` untuk menghapus tag tanpa menghapus data

### <a name="acs"></a>ACS

* Perintah tambahan `aks upgrade-connector` untuk meningkatkan konektor yang ada
* Mengubah `kubectl` file konfigurasi untuk menggunakan YAML gaya blok yang lebih mudah dibaca

### <a name="advisor"></a>Advisor

* [MELANGGAR PERUBAHAN] Berganti `advisor configuration get` nama menjadi `advisor configuration list`
* [MELANGGAR PERUBAHAN] Berganti `advisor configuration set` nama menjadi `advisor configuration update`
* [MELANGGAR PERUBAHAN] Dihapus `advisor recommendation generate`
* Menambahkan `--refresh` parameter ke `advisor recommendation list`
* Perintah tambahan `advisor recommendation show`

### <a name="appservice"></a>Layanan aplikasi

* Usang `[webapp|functionapp] assign-identity`
* Menambahkan perintah `webapp identity [assign|show]` identitas terkelola dan `functionapp identity [assign|show]`

### <a name="eventhubs"></a>Eventhubs

* Rilis awal

### <a name="extension"></a>Ekstensi

* Pemeriksaan tambahan untuk memperingatkan pengguna jika distro yang digunakan berbeda maka yang disimpan dalam file sumber paket, karena ini dapat menyebabkan kesalahan

### <a name="interactive"></a>Interaktif

* Tetap [# 5625](https://github.com/Azure/azure-cli/issues/5625): Pertahankan sejarah di berbagai sesi
* Tetap [#3016](https://github.com/Azure/azure-cli/issues/3016): Riwayat tidak direkam saat berada dalam cakupan
* Tetap [#5688](https://github.com/Azure/azure-cli/issues/5688): Penyelesaian tidak muncul jika pemuatan tabel perintah menemui pengecualian
* Fixed progress meter untuk operasi jangka panjang

### <a name="monitor"></a>Monitor

* Tidak `monitor autoscale-settings` digunakan lagi perintah
* Perintah `monitor autoscale` tambahan
* Perintah `monitor autoscale profile` tambahan
* Perintah `monitor autoscale rule` tambahan

### <a name="network"></a>Jaringan

* [MELANGGAR PERUBAHAN] Parameter dihapus `--tags` dari  `route-filter rule create`
* Menghapus beberapa nilai default yang salah untuk perintah berikut:
  * `network express-route update`
  * `network nsg rule update`
  * `network public-ip update`
  * `traffic-manager profile update`
  * `network vnet-gateway update`
* Perintah `network watcher connection-monitor` tambahan
* Ditambahkan `--vnet` dan `--subnet` parameter untuk `network watcher show-topology`

### <a name="profile"></a>Profil

* Parameter usang `--msi` untuk `az login`
* Menambahkan `--identity` parameter untuk `az login` diganti `--msi`

### <a name="rdbms"></a>RDBMS

* [PRATINJAU] Diubah untuk menggunakan pratinjau API 2017-12-01

### <a name="service-bus"></a>Service Bus

* Rilis awal

### <a name="storage"></a>Penyimpanan

* Tetap [#4971](https://github.com/Azure/azure-cli/issues/4971): `storage blob copy` sekarang mendukung cloud Azure lainnya
* Tetap [# 5286](https://github.com/Azure/azure-cli/issues/5286): Perintah `storage blob [delete-batch|download-batch|upload-batch]` batch tidak lagi melemparkan kesalahan pada kegagalan prakondisi

### <a name="vm"></a>VM

* Menambahkan dukungan untuk `[vm|vmss] create` melampirkan disk data yang tidak dikelola dan mengonfigurasi caching
* `[vm|vmss] assign-identity` Usang dan`[vm|vmss] remove-identity`
* Ditambahkan `vm identity [assign|remove|show]` dan `vmss identity [assign|remove|show]` perintah untuk mengganti perintah yang tidak digunakan lagi
* Mengubah prioritas `vmss create` default menjadi Tidak Ada

## <a name="february-27-2018"></a>27 Februari 2018

Versi 2.0.28

### <a name="core"></a>Core

* Memperbaiki [#5184](https://github.com/Azure/azure-cli/issues/5184): Masalah pemasangan Homebrew
* Menambahkan dukungan untuk telemetri ekstensi dengan tombol kustom
* Menambahkan log HTTP ke `--debug`

### <a name="acs"></a>ACS

* Diubah untuk menggunakan `virtual-kubelet-for-aks` bagan Helm secara `aks install-connector` default
* Masalah tetap: Izin tidak senuffient bagi prinsipal layanan untuk membuat masalah grup kontainer ACI
* Ditambahkan `--aci-container-group`, `--location`, dan `--image-tag` parameter untuk `aks install-connector`
* Menghapus pemberitahuan penghentian dari `aks get-versions`

### <a name="appservice"></a>Layanan aplikasi

* Pembaruan untuk versi SDK baru (azure-mgmt-web 0.35.0)
* Tetap [#5538](https://github.com/Azure/azure-cli/issues/5538): `Free` dilaporkan sebagai SKU tidak valid

### <a name="cognitive-services"></a>Cognitive Services

* Memperbarui 'pemberitahuan' saat membuat akun Layanan Kognitif baru

### <a name="consumption"></a>Consumption

* Menambahkan perintah baru untuk API lembar harga
* Memperbarui format Detail Penggunaan dan Detail Reservasi yang ada

### <a name="container"></a>Kontainer

* Ditambahkan `--secrets` dan `--secrets-mount-path` argumen untuk `container create` menggunakan rahasia di ACI

### <a name="network"></a>Jaringan

* Tetap [#5559](https://github.com/Azure/azure-cli/issues/5559): Klien yang hilang di `network vnet-gateway vpn-client generate`

### <a name="resource"></a>Sumber daya

* Diubah `group deployment export` untuk menampilkan templat parsial dan kesalahan saat kegagalan

### <a name="role"></a>Peran

* Ditambahkan `role assignment list-changelogs` untuk memungkinkan audit peran utama layanan

### <a name="sql"></a>SQL

* Menambahkan dukungan redundansi zona untuk database dan kumpulan elastis pada pembuatan dan pembaruan

### <a name="storage"></a>Penyimpanan

* Diaktifkan menentukan jalur tujuan/awalan untuk `storage blob [upload-batch|download-batch]`

### <a name="vm"></a>VM

* Menambahkan suport untuk melampirkan/detatching disk pada satu instans VMSS


## <a name="february-13-2018"></a>13 Februari 2018

Versi 2.0.27

### <a name="core"></a>Core

* Mengubah autentikasi menjadi kunci pada ID langganan dan nama di login MSI

### <a name="acs"></a>ACS

* [MELANGGAR PERUBAHAN] Diganti `aks get-versions` namanya menjadi `aks get-upgrades` untuk kepentingan akurasi
* Diubah `aks get-versions` untuk menampilkan versi Kubernetes yang tersedia untuk `aks create`
* Mengubah `aks create` default untuk membiarkan server memilih versi Kubernetes
* Pesan bantuan yang diperbarui yang mengacu pada prinsipal layanan yang dihasilkan oleh AKS
* Mengubah ukuran `aks create` node default dari "StandardD1v2\_\_" menjadi "StandardDS1v2\_\_"
* Peningkatan keandalan saat menemukan pod dasbor untuk `az aks browse`
* Diperbaiki `aks get-credentials` untuk menangani kesalahan Unicode saat memuat file konfigurasi Kubernetes
* Menambahkan pesan untuk `az aks install-cli` membantu masuk `kubectl``$PATH`

### <a name="appservice"></a>Layanan aplikasi

* Memperbaiki masalah jika `webapp [backup|restore]` gagal karena referensi null
* Menambahkan dukungan untuk paket layanan aplikasi default melalui `az configure --defaults appserviceplan=my-asp`

### <a name="cdn"></a>CDN

* Perintah `cdn custom-domain [enable-https|disable-https]` tambahan

### <a name="container"></a>Kontainer

* Opsi tambahan `--follow` untuk `az container logs` streaming log
* Perintah tambahan `container attach` yang melampirkan output standar lokal dan aliran kesalahan ke kontainer dalam grup kontainer

### <a name="cosmosdb"></a>CosmosDB

* Menambahkan dukungan untuk mengatur kemampuan

### <a name="extension"></a>Ekstensi

* Menambahkan dukungan untuk `--pip-proxy` parameter ke `az extension [add|update]` perintah
* Menambahkan dukungan untuk `--pip-extra-index-urls` argumen ke `az extension [add|update]` perintah

### <a name="feedback-reference"></a>Referensi umpan balik

* Menambahkan informasi ekstensi ke data telemetri

### <a name="interactive"></a>Interaktif

* Memperbaiki masalah di mana pengguna diminta untuk masuk saat menggunakan mode interaktif di Cloud Shell
* Regresi tetap dengan penyelesaian parameter yang hilang

### <a name="iot"></a>IoT

* Memperbaiki masalah di mana `iot dps access policy [create|update]` akan mengembalikan kesalahan 'tidak ditemukan' saat sukses
* Memperbaiki masalah di mana `iot dps linked-hub [create|update]` akan mengembalikan kesalahan 'tidak ditemukan' saat sukses
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

* Perintah `sql server dns-alias` tambahan
* Ditambahkan `sql db rename`
* Menambahkan dukungan untuk `--ids` argumen ke semua perintah sql

### <a name="storage"></a>Penyimpanan

* Ditambahkan `storage blob service-properties delete-policy` dan `storage blob undelete` perintah untuk mengaktifkan penghapusan lunak

### <a name="vm"></a>VM

* Memperbaiki crash saat enkripsi VM mungkin tidak sepenuhnya diintasi
* Menambahkan output ID utama untuk mengaktifkan MSI
* Tetap `vm boot-diagnostics get-boot-log`


## <a name="january-31-2018"></a>31 Januari 2018

Versi 2.0.26

### <a name="core"></a>Core

* Menambahkan dukungan retrival token mentah dalam konteks MSI
* Menghapus string indikator polling setelah menyelesaikan LRO pada hari Windows cmd.exe
* Menambahkan peringatan yang muncul saat menggunakan default yang dikonfigurasi telah diubah ke entri tingkat INFO. Gunakan `--verbose` untuk melihat
* Menambahkan indikator kemajuan untuk perintah tunggu

### <a name="acs"></a>ACS

* Argumen yang diklarifikasi `--disable-browser`
* Penyelesaian tab yang ditingkatkan untuk `--vm-size` argumen

### <a name="appservice"></a>Layanan aplikasi

* Tetap `webapp log [tail|download]`
* `kind` Menghapus pemeriksaan di webapps dan fungsi

### <a name="cdn"></a>CDN

* Memperbaiki masalah klien yang hilang dengan `cdn custom-domain create`

### <a name="cosmosdb"></a>CosmosDB

* Deskripsi parameter tetap untuk kebijakan failover

### <a name="interactive"></a>Interaktif

* Memperbaiki masalah di mana penyelesaian opsi perintah tidak lagi muncul

### <a name="network"></a>Jaringan

* Perlindungan tambahan untuk `--cert-password``application-gateway create`
* Memperbaiki masalah dengan `application-gateway update` tempat `--sku` salah menerapkan nilai default
* Perlindungan tambahan untuk `--shared-key` dan `--authorization-key` untuk `vpn-connection create`
* Memperbaiki masalah klien yang hilang dengan `asg create`
* Menambahkan `--file-name / -f` parameter untuk nama yang diekspor ke `dns zone export`
* Memperbaiki masalah berikut dengan `dns zone export`:
  * Memperbaiki masalah di mana catatan TXT lama diekspor secara tidak benar
  * Memperbaiki masalah di mana catatan TXT yang dikutip salah diekspor tanpa kutipan yang lolos
* Memperbaiki masalah jika catatan tertentu diimpor dua kali dengan `dns zone import`
* Dipulihkan `vnet-gateway root-cert` dan `vnet-gateway revoked-cert` perintah

### <a name="profile"></a>Profil

* Diperbaiki `get-access-token` untuk bekerja di dalam VM dengan identitas

### <a name="resource"></a>Sumber daya

* Memperbaiki bug dengan `deployment [create|validate]` tempat peringatan salah ditampilkan saat bidang 'tipe' templat berisi nilai huruf besar

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah dengan migrasi akun V1 Storage ke Storage V2
* Menambahkan pelaporan kemajuan untuk semua perintah upload/download
* Memperbaiki bug mencegah opsi arg "-n" dengan `storage account check-name`
* Menambahkan kolom 'snapshot' ke output tabel untuk `blob [list|show]`
* Memperbaiki bug dengan berbagai parameter yang perlu diurai sebagai ints

### <a name="vm"></a>VM

* Perintah tambahan `vm image accept-terms` untuk memungkinkan membuat VM dari gambar dengan biaya tambahan
* Diperbaiki `[vm|vmss create]` untuk memastikan perintah dapat berjalan di bawah proxy dengan sertifikat yang tidak ditandatangani
* [PRATINJAU] Menambahkan dukungan untuk prioritas "rendah" ke VMSS
* Perlindungan tambahan untuk `--admin-password``[vm|vmss] create`


## <a name="january-17-2018"></a>17 Januari 2018

Versi 2.0.25

### <a name="acr"></a>ACR

* Menambahkan fallback login acr pada kesalahan kredensial Windows
* Log registri yang diaktifkan

### <a name="acs"></a>ACS

* Perintah tetap `get-credentials`
* Menghapus persyaratan peran SPN

### <a name="appservice"></a>Layanan aplikasi

* Memperbaiki bug dengan `config ssl upload` tempat `hosting_environment_profile` null
* Menambahkan dukungan untuk URL kustom ke `browse`
* Dukungan slot tetap untuk `log tail`

### <a name="backup"></a>Cadangan

* Opsi `--container-name` yang diubah `backup item list` untuk menjadi opsional
* Menambahkan opsi akun penyimpanan ke `backup restore restore-disks`
* Check-in `backup protection enable-for-vm` lokasi tetap agar tidak sensitif jika
* Memperbaiki masalah saat perintah gagal dengan nama kontainer yang tidak valid
* Diubah `backup item list` untuk menyertakan 'Status Kesehatan' secara default

### <a name="batch"></a>Batch

* Diubah `batch login` untuk mengembalikan detail autentikasi

### <a name="cloud"></a>Cloud

* Diubah agar tidak memerlukan titik akhir saat mengatur `--profile` di cloud

### <a name="consumption"></a>Consumption

* Menambahkan perintah baru untuk reservasi: `consumption reservations summaries` dan `consumption reservations details`

### <a name="event-grid"></a>Event Grid

* [MELANGGAR PERUBAHAN] Memindahkan `az eventgrid topic event-subscription` perintah ke `eventgrid event-subscription`
* [MELANGGAR PERUBAHAN] Memindahkan `az eventgrid resource event-subscription` perintah ke `eventgrid event-subscription`
* [MELANGGAR PERUBAHAN] `eventgrid event-subscription show-endpoint-url` Menghapus perintah. Gunakan `eventgrid event-subscription show --include-full-endpoint-url` sebagai gantinya
* Perintah tambahan `eventgrid topic update`
* Perintah tambahan `eventgrid event-subscription update`
* Menambahkan `--ids` parameter untuk `eventgrid topic` perintah
* Menambahkan dukungan penyelesaian tab untuk nama topik

### <a name="interactive"></a>Interaktif

* Memperbaiki masalah jika mode interaktif tidak berfungsi dengan Python 2.x
* Memperbaiki kesalahan saat startup
* Memperbaiki masalah dengan beberapa perintah yang tidak berjalan dalam mode interaktif

### <a name="iot"></a>IoT

* Menambahkan dukungan untuk layanan penyediaan perangkat
* Menambahkan pesan deprekasi dalam perintah dan bantuan perintah
* Menambahkan pemeriksaan IoT untuk memberi tahu pengguna tentang Ekstensi IoT

### <a name="monitor"></a>Monitor

* Menambahkan dukungan pengaturan multi-diagnostik. Parameter ini `--name` sekarang diperlukan untuk `az monitor diagnostic-settings create`
* Perintah tambahan `monitor diagnostic-settings categories` untuk mendapatkan kategori pengaturan diagnostik

### <a name="network"></a>Jaringan

* Memperbaiki masalah saat mencoba mengubah ke/dari mode siaga aktif dengan `vnet-gateway update`
* Menambahkan dukungan untuk HTTP2 ke `application-gateway [create|update]`

### <a name="profile"></a>Profil

* Menambahkan dukungan untuk login dengan identitas yang ditetapkan pengguna

### <a name="role"></a>Peran

* Menambahkan `--assignee-object-id` argumen untuk `role assignment create` memotong kueri grafik

### <a name="service-fabric"></a>Service Fabric

* Menambahkan kesalahan terperinci ke respons validasi saat membuat klaster
* Memperbaiki masalah klien yang hilang dengan beberapa perintah

### <a name="vm"></a>VM

* [PRATINJAU] Dukungan lintas zona untuk `vmss`
* [MELANGGAR PERUBAHAN] Mengubah default zona `vmss` tunggal menjadi penyeimbang beban "Standar"
* [MELANGGAR PERUBAHAN] Diubah `externalIdentities` menjadi `userAssignedIdentities` emsi
* [PRATINJAU] Menambahkan dukungan untuk os disk swap
* Menambahkan dukungan untuk menggunakan gambar VM dari langganan lain
* Menambahkan `--plan-name`, `--plan-product`, `--plan-promotion-code` dan `--plan-publisher` argumen untuk `[vm|vmss] create`
* Memperbaiki masalah kesalahan dengan `[vm|vmss] create`
* Memperbaiki penggunaan sumber daya yang berlebihan yang disebabkan oleh `vm image list --all`

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

* [PRATINJAU] Menambahkan dukungan untuk identitas yang ditetapkan pengguna untuk VM dan VMSSes


## <a name="december-5-2017"></a>5 Desember 2017

Versi 2.0.22

* Perintah yang dihapus `az component` . Gunakan `az extension` sebagai gantinya

### <a name="core"></a>Core
* Memodifikasi titik `AZURE_US_GOV_CLOUD` akhir otoritas AAD dari login.microsoftonline.com ke login.microsoftonline.us
* Memperbaiki masalah di mana telemetri akan terus mengirim ulang

### <a name="acs"></a>ACS

* Ditambahkan `aks install-connector` dan `aks remove-connector` perintah
* Peningkatan pelaporan kesalahan untuk `acs create`
* Penggunaan tetap `aks get-credentials -f` tanpa jalur yang memenuhi syarat

### <a name="advisor"></a>Advisor

* Rilis awal

### <a name="appservice"></a>Layanan aplikasi

* Memperbaiki pembuatan nama cert dengan `webapp config ssl upload`
* Memperbaiki `webapp [list|show]` dan `functionapp [list|show]` menampilkan aplikasi yang benar
* Menambahkan nilai default untuk `WEBSITE_NODE_DEFAULT_VERSION`

### <a name="consumption"></a>Consumption

* Dukungan iklan untuk API versi 2017-11-30

### <a name="container"></a>Kontainer

* Memperbaiki regresi port default

### <a name="monitor"></a>Monitor

* Menambahkan dukungan multi dimensi ke perintah metrik

### <a name="resource"></a>Sumber daya

* Menambahkan `--include-response-body` argumen ke `resource show`

### <a name="role"></a>Peran

* Menambahkan tampilan tugas default untuk administraor "klasik" ke `role assignment list`
* Menambahkan suport untuk `ad sp reset-credentials` menambahkan kredensial alih-alih menimpa
* Peningkatan pelaporan kesalahan untuk `ad sp create-for-rbac`

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
* Mengubah ukuran VM default untuk AKS menjadi `Standard_D1_v2`
* Diperbaiki `az aks browse` pada Windows
* Diperbaiki `az aks get-credentials` pada Windows

### <a name="appservice"></a>Layanan aplikasi

* Menambahkan sumber `config-zip` penyebaran untuk aplikasi webapp dan fungsi
* Opsi tambahan `--docker-container-logging` ke `az webapp log config`
* `storage` Menghapus opsi dari parameter `--web-server-logging``az webapp log config`
* Pesan kesalahan yang ditingkatkan untuk `deployment user set`
* Menambahkan dukungan untuk membuat aplikasi fungsi Linux
* Tetap `list-locations`

### <a name="batch"></a>Batch

* Memperbaiki bug di perintah buat kumpulan saat ID sumber daya digunakan dengan `--image` bendera

### <a name="batchai"></a>Batchai

* Menambahkan opsi singkat, `-s`, untuk `--vm-size` saat memberikan ukuran VM dalam `file-server create` perintah
* Menambahkan nama akun penyimpanan dan argumen utama ke `cluster create` parameter
* Dokumentasi tetap untuk `job list-files` dan `job stream-file`
* Menambahkan opsi singkat, `-r`, untuk `--cluster-name` saat memberikan nama cluster dalam `job create` perintah

### <a name="cloud"></a>Cloud

* Diubah `cloud [register|update]` untuk mencegah pendaftaran cloud yang memiliki titik akhir yang tidak diperlukan

### <a name="container"></a>Kontainer

* Menambahkan dukungan untuk membuka beberapa port
* Menambahkan kebijakan mulai ulang grup kontainer
* Menambahkan dukungan untuk me-mount Berbagi Azure File sebagai volume
* Dokumen pembantu yang diperbarui

### <a name="data-lake-analytics"></a>Data Lake Analytics

* Diubah `[job|account] list` untuk mengembalikan informasi yang lebih ringkas

### <a name="data-lake-store"></a>Data Lake Store

* Diubah `account list` untuk mengembalikan informasi yang lebih ringkas

### <a name="extension"></a>Ekstensi

* Ditambahkan `extension list-available` untuk memungkinkan daftar ekstensi Microsoft resmi
* Ditambahkan `--name` untuk `extension [add|update]` memungkinkan menginstal ekstensi berdasarkan nama

### <a name="iot"></a>IoT

* Menambahkan dukungan untuk otoritas sertifikat (CA) dan rantai sertifikat

### <a name="monitor"></a>Monitor

* Perintah `activity-log alert` tambahan

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk catatan DNS CAA
* Memperbaiki masalah di mana titik akhir tidak dapat diperbarui dengan `traffic-manager profile update`
* Memperbaiki masalah di mana `vnet update --dns-servers` tidak berfungsi tergantung pada bagaimana VNET dibuat
* Memperbaiki masalah jika nama DNS relatif salah diimpor oleh `dns zone import`

### <a name="reservations"></a>Reservasi

* Rilis pratinjau awal

### <a name="resource"></a>Sumber daya

* Menambahkan dukungan untuk ID sumber daya ke `--resource` kunci parameter dan tingkat sumber daya

### <a name="sql"></a>SQL

* Menambahkan `--ignore-missing-vnet-service-endpoint` parameter ke `sql server vnet-rule [create|update]`

### <a name="storage"></a>Penyimpanan

* Diubah `storage account create` untuk menggunakan SKU `Standard_RAGRS` sebagai default
* Memperbaiki bug saat berhadapan dengan nama file / blob yang menyertakan chars non-ascii
* Memperbaiki bug yang dicegah menggunakan `--source-uri` dengan `storage [blob|file] copy start-batch`
* Menambahkan perintah untuk glob dan menghapus beberapa objek dengan `storage [blob|file] delete-batch`
* Memperbaiki masalah saat mengaktifkan metrik dengan `storage metrics update`
* Memperbaiki masalah dengan file lebih dari 200GB saat menggunakan `storage blob upload-batch`
* Memperbaiki masalah di mana `--bypass` dan `--default-action` diabaikan oleh `storage account [create|update]`

### <a name="vm"></a>VM

* Memperbaiki bug dengan `vmss create` yang dicegah menggunakan `Basic` tingkat ukuran
* Menambahkan `--plan` argumen untuk `[vm|vmss] create` gambar kustom dengan informasi penagihan
* Perintah `vm secret `[add|remove|list]'
* Berganti `vm format-secret` nama menjadi `vm secret format`
* Menambahkan `--encrypt format` argumen ke `vm encryption enable`

## <a name="october-24-2017"></a>24 Oktober 2017

Versi 2.0.20

### <a name="core"></a>Core

* Diperbarui `2017-03-09-profile` untuk mengkonsumsi `MGMT_STORAGE` versi API `2016-01-01`

### <a name="acr"></a>ACR

* Manajemen sumber daya yang diperbarui untuk menunjuk ke `2017-10-01` versi API
* Mengubah SKU 'bawa penyimpanan Anda sendiri' ke Classic
* SKU registri yang berganti nama menjadi Basic, Standard, dan Premium

### <a name="acs"></a>ACS

* [PRATINJAU] Perintah `az aks` tambahan
* Kubernetes tetap `get-credentials`

### <a name="appservice"></a>Layanan aplikasi

* Memperbaiki masalah di mana log yang `webapp` diunduh mungkin tidak valid

### <a name="component"></a>Komponen

* Menambahkan pesan deprekasi yang lebih jelas untuk semua penginstal dan prompt konfirmasi

### <a name="monitor"></a>Monitor

* Perintah `action-group` tambahan

### <a name="resource"></a>Sumber daya

* Ketidakcocokan tetap dengan versi terbaru dependensi msrest di `group export`
* Tetap `policy assignment create` bekerja dengan definisi kebijakan dan definisi menetapkan kebijakan bawaan

### <a name="vm"></a>VM

* Menambahkan `--accelerated-networking` argumen ke `vmss create`


## <a name="october-9-2017"></a>9 Oktober 2017 pukul

Versi 2.0.19

### <a name="core"></a>Core

* Menambahkan penanganan URL otoritas ADFS dengan garis miring ke Azure Stack

### <a name="appservice"></a>Layanan aplikasi

* Menambahkan pembaruan generik dengan perintah baru `webapp update`

### <a name="batch"></a>Batch

* Diperbarui ke Batch SDK 4.0.0
* Opsi `--image` terbaru VirtualMachineConfiguration untuk mendukung referensi gambar ARM selain publish:offer:sku:version
* Menambahkan dukungan untuk model ekstensi CLI baru untuk perintah Ekstensi Batch
* Dukungan Batch dihapus dari model komponen

### <a name="batchai"></a>Batchai

* Rilis awal modul Batch AI

### <a name="keyvault"></a>Keyvault

* Memperbaiki masalah autentikasi Key Vault saat menggunakan ADFS di Azure Stack. [(#4448)](https://github.com/Azure/azure-cli/issues/4448)

### <a name="network"></a>Jaringan

* Argumen `--server` `application-gateway address-pool create` yang diubah menjadi opsional, memungkinkan kumpulan alamat kosong
* Diperbarui `traffic-manager` untuk mendukung fitur terbaru

### <a name="resource"></a>Sumber daya

* Menambahkan dukungan untuk `--resource-group/-g` opsi untuk nama grup sumber daya ke `group`
* Perintah tambahan untuk `account lock` bekerja dengan kunci tingkat langganan
* Perintah tambahan untuk `group lock` bekerja dengan kunci tingkat grup
* Perintah tambahan untuk `resource lock` bekerja dengan kunci tingkat sumber daya

### <a name="sql"></a>Sql

* Menambahkan dukungan untuk SQL Transparent Data Encryption (TDE) dan TDE dengan Bring Your Own Key
* Menambahkan `db list-deleted` perintah dan `db restore --deleted-time` parameter, memungkinkan kemampuan untuk menemukan dan memulihkan database yang dihapus
* Ditambahkan `db op list` dan `db op cancel`, memungkinkan kemampuan untuk membuat daftar dan membatalkan operasi yang sedang berlangsung pada database

### <a name="storage"></a>Penyimpanan

* Menambahkan dukungan untuk snapshot berbagi file

### <a name="vm"></a>Vm

* Memperbaiki bug di `vm show` mana penggunaan `-d` menyebabkan kerusakan pada alamat IP pribadi yang hilang
* [PRATINJAU] Menambahkan dukungan untuk rolling upgrade ke `vmss create`
* Menambahkan dukungan untuk memperbarui pengaturan enkripsi dengan `vm encryption enable`
* Menambahkan `--os-disk-size-gb` parameter ke `vm create`
* Menambahkan `--license-type` parameter untuk Windows ke`vmss create`


## <a name="september-22-2017"></a>22 September 2017

Versi 2.0.18

### <a name="resource"></a>Sumber daya

* Menambahkan dukungan untuk menampilkan definisi kebijakan bawaan
* Menambahkan parameter mode dukungan untuk membuat definisi kebijakan
* Menambahkan dukungan untuk definisi dan templat UI ke `managedapp definition create`
* [MELANGGAR PERUBAHAN] Mengubah `managedapp` jenis sumber daya dari `appliances` ke `applications` dan `applianceDefinitions` ke `applicationDefinitions`

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk zona ketersediaan ke `network lb` dan `network public-ip` subkomand
* Menambahkan dukungan untuk IPv6 Microsoft Peering ke `express-route`
* Menambahkan `asg` perintah grup keamanan aplikasi
* Menambahkan `--application-security-groups` argumen ke `nic [create|ip-config create|ip-config update]`
* Ditambahkan `--source-asgs` dan `--destination-asgs` argumen untuk `nsg rule [create|update]`
* Ditambahkan `--ddos-protection` dan `--vm-protection` argumen untuk `vnet [create|update]`
* Perintah `network [vnet-gateway|vpn-client|show-url]` tambahan

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah di mana `storage account network-rule` perintah mungkin gagal setelah memperbarui SDK

### <a name="eventgrid"></a>Eventgrid

* Diperbarui Azure Event Grid Python SDK untuk menggunakan versi API yang lebih baru "2017-09-15-preview"

### <a name="sql"></a>SQL

* Mengubah `sql server list` argumen `--resource-group` menjadi opsional. Jika tidak ditentukan, semua server sql dalam langganan akan dikembalikan
* Menambahkan `--no-wait` param ke `db [create|copy|restore|update|replica create|create|update]` dan `dw [create|update]`

### <a name="keyvault"></a>Keyvault

* Menambahkan dukungan untuk perintah Keyvault dari belakang proxy

### <a name="vm"></a>VM

* Ditambahkan untuk dukungan ke availability zone ke `[vm|vmss|disk] create`
* Memperbaiki masalah saat menggunakan`--app-gateway ID` dengan `vmss create` akan menyebabkan kegagalan
* Menambahkan `--asgs` argumen ke `vm create`
* Menambahkan dukungan untuk menjalankan perintah pada VM dengan `vm run-command`
* [PRATINJAU] Menambahkan dukungan untuk enkripsi disk VMSS dengan `vmss encryption`
* Menambahkan dukungan untuk melakukan pemeliharaan pada VM dengan `vm perform-maintenance`

### <a name="acs"></a>ACS

* [PRATINJAU] Menambahkan `--orchestrator-release` argumen ke `acs create` untuk wilayah pratinjau ACS

### <a name="appservice"></a>Layanan aplikasi

* Menambahkan kemampuan untuk memperbarui dan menampilkan pengaturan autentikasi dengan `webapp auth [update|show]`

### <a name="backup"></a>Cadangan

* Rilis pratinjau


## <a name="september-11-2017"></a>11 September 2017

Versi 2.0.17

### <a name="core"></a>Core

* Modul perintah yang diaktifkan untuk mengatur ID korelasinya sendiri dalam telemetri
* Memperbaiki masalah dump JSON saat telemetri diatur ke mode diagnostik

### <a name="acs"></a>Acs

* Perintah tambahan `acs list-locations`
* Dibuat `ssh-key-file` datang dengan nilai default yang diharapkan

### <a name="appservice"></a>Layanan aplikasi

* Menambahkan kemampuan untuk membuat webapp dalam grup sumber daya selain paket layanan aktif

### <a name="cdn"></a>CDN

* Memperbaiki bug 'CustomDomain is not interable' untuk `cdn custom-domain create`

### <a name="extension"></a>Ekstensi

* Rilis Awal

### <a name="keyvault"></a>Keyvault

* Memperbaiki masalah di mana izin peka huruf besar/kecil untuk `keyvault set-policy`

### <a name="network"></a>Jaringan

* Berganti `vnet list-private-access-services` nama menjadi `vnet list-endpoint-services`
* Argumen yang diganti `--private-access-services` namanya menjadi `--service-endpoints` untuk `vnet subnet create/update`
* Menambahkan dukungan untuk beberapa rentang IP dan rentang port ke `nsg rule create/update`
* Menambahkan dukungan untuk SKU ke `lb create`
* Menambahkan dukungan untuk SKU ke `public-ip create`

### <a name="resource"></a>Sumber daya

* Memungkinkan pengesahan definisi parameter kebijakan sumber daya pada `policy definition create`, dan `policy definition update`
* Perbolehkan melewati nilai parameter untuk `policy assignment create`
* Izinkan untuk melewati JSON atau file untuk semua params
* Versi API yang ditingkatkan

### <a name="sql"></a>SQL

* Perintah `sql server vnet-rule` tambahan

### <a name="vm"></a>VM

* Tetap: Jangan menetapkan akses kecuali `--scope` disediakan
* Tetap: Gunakan penamaan ekstensi yang sama seperti yang dilakukan portal
* Dihapus `subscription` dari `[vm|vmss] create` output
* Tetap: `[vm|vmss] create` penyimpanan SKU tidak diterapkan pada disk data dengan gambar
* Tetap: `vm format-secret --secrets` tidak akan menerima ID terpisah garis baru

## <a name="august-31-2017"></a>31 Agustus 2017

Versi 2.0.16

### <a name="keyvault"></a>Keyvault

* Memperbaiki bug saat mencoba menyelesaikan pengkodean rahasia secara otomatis dengan `secret download`

### <a name="sf"></a>Sf

* Membatalkan semua perintah demi Service Fabric CLI (sfctl)

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah jika akun penyimpanan tidak dapat dibuat di wilayah yang tidak mendukung fitur NetworkACLs
* Tentukan jenis konten dan pengkodean konten selama blob dan pengunggahan file jika tidak ada jenis konten dan pengkodean konten yang ditentukan

## <a name="august-28-2017"></a>28 Agustus 2017

Versi 2.0.15

### <a name="cli"></a>CLI

* Menambahkan catatan hukum ke `--version`

### <a name="acs"></a>ACS

* Wilayah pratinjau yang dikoreksi
* Default `dns_name_prefix` yang diformat dengan benar
* Output perintah acs yang dioptimalkan

### <a name="appservice"></a>Layanan aplikasi

* [MELANGGAR PERUBAHAN] Inkonsistensi tetap dalam output `az webapp config appsettings [delete|set]`
* Menambahkan alias `-i` baru untuk `az webapp config container set --docker-custom-image-name`
* Terkena `az webapp log show`
* Mengungkap argumen baru dari `az webapp delete` untuk mempertahankan paket layanan aplikasi, metrik, atau pendaftaran dns
* Diperbaiki: Mendeteksi pengaturan slot dengan benar

### <a name="iot"></a>IoT

* Tetap #3934: Pembuatan kebijakan tidak lagi menghapus kebijakan yang ada

### <a name="network"></a>Jaringan

* [MELANGGAR PERUBAHAN] Berganti `vnet list-private-access-services` nama menjadi `vnet list-endpoint-services`
* [MELANGGAR PERUBAHAN] Opsi `--private-access-services` yang diganti namanya menjadi `--service-endpoints` untuk `vnet subnet [create|update]`
* Menambahkan dukungan untuk beberapa rentang IP dan port ke `nsg rule [create|update]`
* Menambahkan dukungan untuk SKU ke `lb create`
* Menambahkan dukungan untuk SKU ke `public-ip create`

### <a name="profile"></a>Profil

* Diekspos `--msi` dan `--msi-port` masuk menggunakan identitas mesin virtual

### <a name="service-fabric"></a>Service Fabric

* Rilis pratinjau
* Aturan pengguna/kata sandi registri yang disederhanakan untuk perintah
* Permintaan kata sandi tetap untuk pengguna bahkan setelah melewati param
* Menambahkan dukungan untuk kosong `registry_cred`

### <a name="storage"></a>Penyimpanan

* Tingkat blob pengaturan yang diaktifkan
* Ditambahkan `--bypass` dan `--default-action` argumen untuk `storage account [create|update]` mendukung tunneling layanan
* Menambahkan perintah untuk menambahkan aturan VNET dan aturan berbasis IP ke `storage account network-rule`
* Enkripsi layanan yang diaktifkan oleh kunci terkelola pelanggan
* [MELANGGAR PERUBAHAN] Opsi yang diganti `--encryption` namanya menjadi `--encryption-services` untuk `az storage account create and az storage account update` perintah
* Diperbaiki #4220: `az storage account update encryption` - ketidakcocokan sintaks

### <a name="vm"></a>VM

* Memperbaiki masalah di mana informasi tambahan dan salah ditampilkan `vmss get-instance-view` saat menggunakan `--instance-id *`
* Menambahkan dukungan untuk `--lb-sku` `vmss create`:
* Menghapus nama manusia dari nama admin yang dianulir untuk `[vm|vmss] create`
* Memperbaiki masalah di mana `[vm|vmss] create` akan melempar kesalahan jika tidak dapat mengekstrak informasi rencana dari gambar
* Memperbaiki crash saat membuat scaleset vmms dengan LB internal
* Memperbaiki masalah di mana `--no-wait` argumen tidak berfungsi wth `vm availability-set create`


## <a name="august-15-2017"></a>15 Agustus 2017

Versi 2.0.14

### <a name="acs"></a>ACS

* Nomor port sshMaster0 yang dikoreksi untuk kubernetes

### <a name="appservice"></a>Layanan aplikasi

* Memperbaiki pengecualian saat merayapi git baru berbasis Linux webapp

### <a name="event-grid"></a>Event Grid

* Menambahkan dependensi SDK

## <a name="august-11-2017"></a>11 Agustus 2017

Versi 2.0.13

### <a name="acs"></a>ACS

* Menambahkan lebih banyak wilayah pratinjau

### <a name="batch"></a>Batch

* Diperbarui ke Batch SDK 3.1.0 dan Batch Management SDK 4.1.0
* Menambahkan perintah baru menunjukkan jumlah tugas pekerjaan
* Memperbaiki bug dalam pemrosesan URL SAS file sumber daya
* Titik akhir akun batch sekarang mendukung awalan 'https://' opsional
* Dukungan untuk menambahkan daftar lebih dari 100 tugas ke pekerjaan
* Menambahkan pembuatan log debug untuk memuat modul perintah Ekstensi

### <a name="component"></a>Komponen

* Menambahkan peringatan deprekasi ke perintah 'az component'

### <a name="container"></a>Kontainer

* `create`: Memperbaiki masalah di mana tanda sama dengan tidak diizinkan di dalam variabel lingkungan


### <a name="data-lake-store"></a>Data Lake Store

* Kontrol kemajuan yang diaktifkan

### <a name="event-grid"></a>Event Grid

* Rilis awal

### <a name="network"></a>Jaringan

* `lb`: Memperbaiki masalah di mana nama sumber daya anak tertentu tidak teratasi dengan benar saat dihilangkan
* `application-gateway {subresource} delete`: Masalah tetap di mana `--no-wait` tidak dihormati
* `application-gateway http-settings update`: Memperbaiki masalah di mana `--connection-draining-timeout` tidak dapat dimatikan
* Memperbaiki argumen `sa_data_size_kilobyes` kata kunci tak terduga kesalahan dengan `az network vpn-connection ipsec-policy add`

### <a name="profile"></a>Profil

* `account list`: Ditambahkan `--refresh` untuk menyinkronkan langganan terbaru dari server

### <a name="storage"></a>Penyimpanan

* Aktifkan akun penyimpanan pembaruan dengan identitas yang ditetapkan sistem

### <a name="vm"></a>VM

* `availability-set`: Jumlah domain kesalahan yang terbuka pada konversi
* Perintah terekspos `list-skus`
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

* Output sdk auth info untuk prinsipal layanan dengan sertifikat
* Pengecualian kemajuan penerapan tetap
* Menggunakan titik akhir lengan dari cloud saat ini untuk membuat klien langganan
* Penanganan bersamaan yang ditingkatkan dari file clouds.config (#3636)
* Refresh id permintaan klien untuk setiap eksekusi perintah
* Buat klien langganan dengan profil SDK yang tepat (#3635)
* Pelaporan Kemajuan untuk penyebaran templat (#3510)
* Menambahkan dukungan untuk memilih bidang output tabel melalui kueri jmespath (#3581)
* Meningkatkan muting parse args dan menambahkan riwayat dengan gerakan (#3434)
* Membuat klien langganan dengan profil SDK yang tepat
* Memindahkan semua file rekaman yang ada ke folder terbaru
* Fixed idempotency for VM/VMSS create (#3586)
* Jalur perintah tidak lagi peka huruf besar/kecil
* Parameter tipe boolean tertentu tidak lagi peka huruf besar/kecil
* Mendukung login ke ADFS di server prem seperti Azure Stack
* Tulis serentak tetap ke clouds.config (#3255)

### <a name="acr"></a>ACR

* Perintah tambahan `show-usage` untuk registri terkelola
* Mendukung pembaruan SKU untuk registri terkelola
* Menambahkan registri terkelola dengan SKU terkelola
* Menambahkan webhooks untuk registri terkelola dengan modul perintah acr webhook
* Menambahkan autentikasi AAD dengan perintah login acr
* Menambahkan perintah hapus untuk repositori docker, manifes, dan tag

### <a name="acs"></a>ACS

* Dukungan untuk API versi 2017-07-01

### <a name="appservice"></a>Layanan aplikasi

* Memperbaiki bug di mana daftar webapp Linux tidak akan mengembalikan apa pun
* Dukungan untuk mengambil creds dari acr
* Menghapus semua perintah di bawah `appservice web`
* Mask docker registry password dari command output (#3656)
* Pastikan browser default digunakan di macOS tanpa kesalahan (#3623)
* Meningkatkan bantuan `webapp log tail` dan `webapp log download` (#3624)
* Perintah terekspos `traffic-routing` untuk mengonfigurasi perutean statis (#3566)
* Perbaikan keandalan tambahan dalam mengonfigurasi kontrol sumber (#3245)
* Menghapus argumen yang `--node-version` tidak didukung dari `webapp config update` untuk Windows webapps. Sebagai gantinya gunakan `webapp config appsettings set --settings WEBSITE_NODE_DEFAULT_VERSION=...`

### <a name="batch"></a>Batch

* Diperbarui ke Batch SDK 3.0.0 dengan dukungan untuk VM prioritas rendah di kumpulan
* Opsi `--target-dedicated` berganti `pool create` nama menjadi`--target-dedicated-nodes`
* Opsi tambahan `pool create` `--target-low-priority-nodes` dan `--application-licenses`

### <a name="cdn"></a>CDN

* Memberikan pesan `cdn endpoint list` kesalahan yang lebih baik ketika profil yang ditentukan oleh `--profile-name` tidak ada

### <a name="cloud"></a>Cloud

* Mengubah versi API dari titik akhir metadata cloud ke format YYYY-MM-DD
* Titik akhir galeri tidak diperlukan
* Dukungan untuk mendaftarkan cloud hanya dengan titik akhir pengelola sumber daya ARM
* Menyediakan opsi untuk `cloud set` memilih profil saat memilih cloud saat ini
* Terkena `endpoint_vm_image_alias_doc`

### <a name="cosmosdb"></a>CosmosDB

* Tetap memungkinkan pembuatan koleksi dengan kunci partisi kustom
* Menambahkan dukungan untuk TTL default pengumpulan

### <a name="data-lake-analytics"></a>Data Lake Analytics

* Perintah tambahan untuk manajemen kebijakan komputasi di `dla account compute-policy` bawah judul
* Ditambahkan `dla job pipeline show`
* Ditambahkan `dla job recurrence list`

### <a name="data-lake-store"></a>Data Lake Store

* Menambahkan dukungan untuk rotasi kunci vault terkelola pengguna di `dls account update`
* Diperbarui versi SDK sistem file Data Lake Store yang mendasarinya, mengatasi masalah kinerja
* Perintah tambahan `dls enable-key-vault`. Perintah ini mencoba untuk mengaktifkan pengguna yang disediakan Key Vault untuk digunakan mengenkripsi data ina Data Lake Store akun

### <a name="interactive"></a>Interaktif

* Meningkatkan waktu mulai dengan menggunakan perintah cache
* Peningkatan cakupan pengujian
* Meningkatkan gerakan '?' untuk juga menyuntikkan ke perintah berikutnya
* Memperbaiki kesalahan interaktif dengan profil 2017-03-09-profile-preview (#3587)
* Diizinkan `--version` sebagai parameter untuk mode interaktif (#3645)
* Hentikan kesalahan pelemparan mode interaktif dari penyelesaian validasi (#3570)
* Pelaporan kemajuan untuk penyebaran templat (#3510)
* Menambahkan `--progress` bendera
* Dihapus `--debug` dan `--verbose` dari penyelesaian
* Dihapus `interactive` dari penyelesaian (#3324)

### <a name="iot"></a>IoT

* Pembuatan kebijakan tetap tidak lagi menghapus kebijakan yang ada. (#3934)

### <a name="key-vault"></a>Key vault

* Perintah tambahan untuk fitur pemulihan vault utama:
  * `keyvault`subkomand , `purge``recover`,`keyvault list-deleted`
  * `keyvault secret`subkomands `backup`, `restore`, `purge`, `recover``list-deleted`
  * `keyvault certificate`subkomand , `purge``recover`,`list-deleted`
  * `keyvault key`subkomand , `purge``recover`,`list-deleted`
* Menambahkan integrasi vault kunci utama layanan (#3133)
* Data vault kunci yang diperbarui ke 0.3.2. (#3307)

### <a name="lab"></a>Laboratorium

* Menambahkan dukungan untuk mengklaim vm apa pun di lab melalui `az lab vm claim`
* Menambahkan formatter keluaran tabel untuk `az lab vm list` dan `az lab vm show`

### <a name="monitor"></a>Monitor

* Perbaiki untuk file template dengan `monitor autoscale-settings get-parameters-template` perintah (#3349)
* Berganti `monitor alert-rule-incidents list` nama menjadi `monitor alert list-incidents`
* Berganti `monitor alert-rule-incidents show` nama menjadi `monitor alert show-incident`
* Berganti `monitor metric-defintions list` nama menjadi `monitor metrics list-definitions`
* Berganti `monitor alert-rules` nama menjadi `monitor alert`
* Diubah `monitor alert create`:
  * `condition` dan `action` subkomand tidak lagi menerima JSON
  * Tambahkan banyak parameter untuk menyederhanakan proses pembuatan aturan
  * `location` tidak lagi diperlukan
  * Menambahkan dukungan nama dan ID untuk target
  * Hapus `--alert-rule-resource-name`
  * Ganti `is-enabled` nama menjadi `enabled`, tidak lagi diperlukan
  * `description` default sekarang berdasarkan kondisi yang disediakan
  *  Menambahkan contoh untuk membantu clarifiy format baru
* Mendukung nama atau ID untuk `monitor metric` perintah
* Menambahkan argumen dan contoh kenyamanan ke `monitor alert rule update`

### <a name="network"></a>Jaringan

* Perintah tambahan `list-private-access-services`
* Menambahkan `--private-access-services` argumen ke `vnet subnet create` dan `vnet subnet update`
* Memperbaiki masalah di mana `application-gateway redirect-config create` akan gagal
* Memperbaiki masalah di mana `application-gateway redirect-config update` dengan `--no-wait` tidak akan bekerja
* Memperbaiki bug saat menggunakan `--servers` argumen dengan `application-gateway address-pool create` dan `application-gateway address-pool update`
* Perintah `application-gateway redirect-config` tambahan
* Menambahkan perintah ke `application-gateway ssl-policy`: `list-options`, `predefined list`, `predefined show`
* Menambahkan argumen ke `application-gateway ssl-policy set`: `--name`, `--cipher-suites`, `--min-protocol-version`
* Menambahkan argumen ke `application-gateway http-settings create` dan `application-gateway http-settings update`: `--host-name-from-backend-pool`, `--affinity-cookie-name`, `--enable-probe`, `--path`
* Menambahkan argumen ke `application-gateway url-path-map create` dan `application-gateway url-path-map update`: `--default-redirect-config`, `--redirect-config`
* Menambahkan argumen `--redirect-config` ke `application-gateway url-path-map rule create`
* Menambahkan dukungan untuk `--no-wait``application-gateway url-path-map rule delete`
* Menambahkan argumen ke `application-gateway probe create` dan `application-gateway probe update`: `--host-name-from-http-settings`, `--min-servers`, `--match-body`, `--match-status-codes`
* Menambahkan argumen `--redirect-config` ke `application-gateway rule create` dan `application-gateway rule update`
* Menambahkan dukungan untuk `--accelerated-networking` `nic create` dan `nic update`
* Menghapus `--internal-dns-name-suffix` argumen dari `nic create`
* Menambahkan dukungan untuk `--dns-servers` `nic update` dan `nic create`: Tambahkan dukungan untuk --dns-server
* Memperbaiki bug jika `local-gateway create` diabaikan `--local-address-prefixes`
* Menambahkan dukungan untuk `--dns-servers``vnet update`
* Memperbaiki bug saat membuat peering tanpa pemfilteran rute dengan `express-route peering create`
* Memperbaiki bug di mana `--provider` dan `--bandwidth` argumen tidak berfungsi dengan `express-route update`
* Memperbaiki bug dengan `network watcher show-topology` logika default
* Pemformatan output yang ditingkatkan untuk `network list-usages`
* Gunakan IP frontend default untuk `application-gateway http-listener create` jika hanya ada satu yang ada
* Gunakan kumpulan alamat default, pengaturan HTTP, dan pendengar HTTP jika `application-gateway rule create` hanya ada satu yang ada
* Gunakan IP frontend default dan kumpulan backend jika `lb rule create` hanya ada
* Gunakan IP frontend default untuk `lb inbound-nat-rule create` jika hanya ada satu yang ada

### <a name="profile"></a>Profil

* Mendukung login di dalam VM dengan identitas terkelola
* Mendukung output untuk `account show` dalam format file auth SDK
* Tampilkan peringatan deprekasi saat menggunakan '--expanded-view'
* Perintah tambahan `get-access-token` untuk menyediakan token AAD mentah
* Mendukung login dengan akun pengguna tanpa langganan terkait

### <a name="rdbms"></a>RDBMS

* Mendukung server listingan di seluruh langganan (#3417)
* Diperbaiki `%s` tidak diproses karena hilang `% server_type` (#3393)
* Memperbaiki peta sumber dokumen dan menambahkan tugas CI untuk memverifikasi (#3361)
* Memperbaiki bantuan MySQL dan PostgreSQL (#3369)

### <a name="resource"></a>Sumber daya

* Petunjuk yang ditingkatkan untuk parameter yang hilang untuk `group deployment create`
* Penguraian sintaks yang `--parameters KEY=VALUE` ditingkatkan
* Memperbaiki masalah di mana `group deployment create` file parameter tidak lagi dikenali menggunakan `@<file>` sintaks
* Mendukung `--ids` argumen untuk `resource` dan `managedapp` perintah
* Memperbaiki beberapa pesan penguraian dan kesalahan (#3584)
* Memperbaiki `--resource-type` penguraian agar `lock` perintah dapat diterima `<resource-namespace>` dan `<resource-type>`
* Menambahkan pemeriksaan parameter untuk templat tautan templat (#3629)
* Menambahkan dukungan untuk menentukan parameter penyebaran menggunakan `KEY=VALUE` sintaks

### <a name="role"></a>Peran

* Mendukung output dalam format file auth SDK untuk `create-for-rbac`
* Membersihkan tugas peran dan aplikasi AAD terkait saat menghapus pokok layanan (#3610)
* Sertakan format waktu dalam `app create` args `--start-date` dan `--end-date` deskripsi
* Tampilkan peringatan deprekasi saat menggunakan `--expanded-view`
* Menambahkan integrasi vault kunci ke `create-for-rbac` dan `reset-credentials` perintah

### <a name="service-fabric"></a>Service Fabric
* Memperbaiki masalah dengan file besar dalam aplikasi yang dipotong pada upload (#3666)
* Tes tambahan untuk perintah Service Fabric (#3424)
* Memperbaiki banyak perintah Service Fabric (#3234)

### <a name="sql"></a>SQL

* Menghapus parameter rusak `sql server create` `--identity`
* Menghapus nilai kata sandi dari `sql server create` dan `sql server update` output perintah
* Menambahkan perintah `sql db list-editions` dan `sql elastic-pool list-editions`

### <a name="storage"></a>Penyimpanan

* Opsi dihapus `--marker` dari `storage blob list`, `storage container list`, dan `storage share list` perintah (#3745)
* Diaktifkan membuat akun penyimpanan khusus https
* Metrik penyimpanan, logging, dan perintah cor yang diperbarui (#3495)
* Pesan pengecualian yang diulang dari add CORS (#3638) (#3362)
* Generator yang dikonversi ke daftar dalam mode dry run perintah batch unduhan (#3592)
* Memperbaiki masalah dryrun batch unduhan blob (#3640) (#3592)

### <a name="vm"></a>VM

* Mendukung konfigurasi nsg
* Memperbaiki bug di mana server DNS tidak akan dikonfigurasi dengan benar
* Mendukung identitas layanan terkelola
* Memperbaiki masalah jika `cmss create` dengan penyeimbang beban yang ada diperlukan `--backend-pool-name`
* Buat datadisk dibuat dengan `vm image create` lun mulai dengan 0


## <a name="may-10-2017"></a>10 Mei 2017

Versi 2.0.6

* documentdb berganti nama menjadi cosmosdb
* Tambahkan rdbms (mysql, postgres)
* Sertakan modul Data Lake Analytics dan Data Lake Store
* Sertakan modul Layanan Kognitif
* Sertakan modul Service Fabric
* Sertakan modul Interaktif (ganti nama az-shell)
* Menambahkan dukungan untuk perintah CDN
* Hapus modul Kontainer
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
* perf: persist adal token cache dalam memori sampai proses keluar ([#2603](https://github.com/Azure/azure-cli/issues/2603))
* Memperbaiki byte yang dikembalikan dari sidik jari hex -o tsv ([#3053](https://github.com/Azure/azure-cli/issues/3053))
* Unduhan Sertifikat Vault Kunci yang Disempurnakan dan Integrasi SP AAD ([#3003](https://github.com/Azure/azure-cli/issues/3003))
* Tambahkan lokasi Python ke 'az —version' ([#2986](https://github.com/Azure/azure-cli/issues/2986))
* login: mendukung login ketika tidak ada langganan ([#2929](https://github.com/Azure/azure-cli/issues/2929))
* inti: memperbaiki kegagalan saat login menggunakan kepala layanan dua kali ([#2800](https://github.com/Azure/azure-cli/issues/2800))
* inti: Izinkan jalur file accessTokens.json dapat dikonfigurasi melalui env var ([#2605](https://github.com/Azure/azure-cli/issues/2605))
* inti: Izinkan default yang dikonfigurasi untuk diterapkan pada args opsional ([#2703](https://github.com/Azure/azure-cli/issues/2703))
* inti: Peningkatan kinerja
* inti: Custom CA Certs - Pengaturan dukungan REQUESTS_CA_BUNDLE variabel lingkungan
* inti: Konfigurasi cloud - gunakan titik akhir 'resource manager' jika titik akhir 'manajemen' tidak diatur

### <a name="acs"></a>ACS

* memperbaiki master dan jumlah agen menjadi integer bukan string
* mengekspos 'az acs create --no-wait' dan 'az acs wait' untuk pembuatan async
* mengekspos 'az acs create --validate' untuk validasi dry-run
* menghapus profil windows sebelum perintah put call for scale ([#2755](https://github.com/Azure/azure-cli/issues/2755))

### <a name="appservice"></a>AppService

* functionapp: tambahkan dukungan functionapp penuh, termasuk membuat, menampilkan, daftar, menghapus, nama host, ssl, dll
* Menambahkan Layanan Tim (vsts) sebagai opsi pengiriman berkelanjutan ke "konfigurasi kontrol sumber web appservice"
* Buat "az webapp" untuk menggantikan "az appservice web" (untuk compat mundur, "az appservice web" akan tetap untuk 2 rilis)
* Mengekspos argumen untuk mengonfigurasi penyebaran dan "tumpukan runtime" di webapp create
* Mengekspos "webapp list-runtimes"
* mendukung mengonfigurasi string koneksi ([#2647](https://github.com/Azure/azure-cli/issues/2647))
* mendukung pertukaran slot dengan pratinjau
* Kesalahan Polandia dari perintah appservice ([#2948](https://github.com/Azure/azure-cli/issues/2948))
* Gunakan grup sumber daya paket layanan aplikasi untuk operasi sertifikat ([#2750](https://github.com/Azure/azure-cli/issues/2750))

### <a name="cosmosdb"></a>CosmosDB

* Mengganti nama modul documentdb menjadi cosmosdb
* Menambahkan dukungan untuk API data-plane documentdb: database dan manajemen pengumpulan
* Menambahkan dukungan untuk mengaktifkan failover otomatis pada akun database
* Menambahkan dukungan untuk kebijakan konsistensi baru ConsistentPrefix

### <a name="data-lake-analytics"></a>Data Lake Analytics

* Memperbaiki bug di mana pemfilteran pada hasil dan status untuk daftar pekerjaan akan menimbulkan kesalahan
* Tambahkan dukungan untuk jenis item katalog baru: paket. diakses melalui: `az dla catalog package`
* Memungkinkan untuk mencantumkan item katalog berikut dari dalam database (tidak diperlukan spesifikasi skema):

  * Tabel
  * Fungsi nilai tabel
  * Tampilan
  * Statistik Tabel. Ini juga dapat dicantumkan dengan skema, tetapi tanpa menentukan nama tabel

### <a name="data-lake-store"></a>Data Lake Store

* Perbarui versi SDK sistem file yang mendasarinya, yang memberikan dukungan yang lebih baik untuk menangani skenario pelambatan sisi server
* Meningkatkan kinerja beban paket dan eksekusi perintah ([#2819](https://github.com/Azure/azure-cli/issues/2819))
* bantuan yang terlewatkan untuk acara akses. menambahkannya. ([#2743](https://github.com/Azure/azure-cli/issues/2743))

### <a name="find"></a>Cari

* meningkatkan hasil pencarian dan memungkinkan untuk versi indeks pencarian

### <a name="keyvault"></a>Az.KeyVault

* BC:`az keyvault certificate download` ubah -e dari string atau biner ke PEM atau DER untuk lebih mewakili opsi
* BC: Hapus --expires dan --not-before dari `keyvault certificate create` karena parameter ini tidak didukung oleh layanan
* Menambahkan parameter --validity untuk `keyvault certificate create` mengganti nilai secara selektif dalam --policy
* Memperbaiki masalah di `keyvault certificate get-default-policy` mana 'kedaluwarsa' dan 'not_before' terungkap tetapi 'validity_in_months' tidak
* perbaikan keyvault untuk impor pem dan pfx ([#2754](https://github.com/Azure/azure-cli/issues/2754))

### <a name="lab"></a>Laboratorium

* Menambahkan perintah buat, tampilkan, hapus & daftar untuk lingkungan di lab
* Menambahkan perintah tampilkan daftar & untuk melihat templat ARM di lab
* Menambahkan --environment flag `az lab vm list` untuk memfilter VM menurut lingkungan di lab
* Menambahkan perintah `az lab formula export-artifacts` kenyamanan untuk mengekspor perancah artefak dalam rumus Lab
* Menambahkan perintah untuk mengelola rahasia dalam Lab

### <a name="monitor"></a>Monitor

* Perbaikan Bug: Pemodelan `--actions` `az alert-rules create` untuk mengkonsumsi string JSON ([#3009](https://github.com/Azure/azure-cli/issues/3009))
* Perbaikan bug - pengaturan diagnostik dibuat tidak menerima log /metrik dari perintah pertunjukan ([#2913](https://github.com/Azure/azure-cli/issues/2913))

### <a name="network"></a>Jaringan

* Perintah Tambahkan `network watcher test-connectivity`
* Menambahkan dukungan untuk `--filters` parameter untuk `network watcher packet-capture create`
* Menambahkan dukungan untuk pengurasan koneksi Application Gateway
* Menambahkan dukungan untuk konfigurasi set aturan APPLICATION GATEWAY WAF
* Menambahkan dukungan untuk filter dan aturan rute ExpressRoute
* Menambahkan dukungan untuk perutean geografis TrafficManager
* Menambahkan dukungan untuk pemilih lalu lintas berbasis kebijakan koneksi VPN
* Menambahkan dukungan untuk kebijakan IPSec koneksi VPN
* Memperbaiki bug saat `vpn-connection create` menggunakan `--no-wait` parameter atau `--validate`
* Menambahkan dukungan untuk gateway VNet aktif aktif
* Menghapus nilai null dari output `network vpn-connection list/show` perintah
* BC: Perbaiki bug dalam output `vpn-connection create`
* Perbaiki bug di mana argumen '--key-length' dari 'vpn-connection create' tidak diurai dengan benar
* Memperbaiki bug di `dns zone import` mana rekaman tidak diimpor dengan benar
* Memperbaiki bug di mana `traffic-manager endpoint update` tidak berfungsi
* Menambahkan perintah pratinjau 'pengamat jaringan'

### <a name="profile"></a>Profil

* Mendukung login ketika tidak ada langganan yang ditemukan ([#2560](https://github.com/Azure/azure-cli/issues/2560))
* Mendukung nama param pendek di az account set --subscription ([#2980](https://github.com/Azure/azure-cli/issues/2980))

### <a name="redis"></a>Redis

* Menambahkan perintah pembaruan yang juga menambahkan kemampuan untuk menskalakan cache redis
* Menonaktifkan perintah 'update-settings'

### <a name="resource"></a>Sumber daya

* Menambahkan perintah definisi managedapp dan managedapp ([#2985](https://github.com/Azure/azure-cli/issues/2985))
* Mendukung perintah 'operasi penyedia' ([#2908](https://github.com/Azure/azure-cli/issues/2908))
* Mendukung pembuat sumber daya generik ([#2606](https://github.com/Azure/azure-cli/issues/2606))
* Memperbaiki penguraian sumber daya dan pencarian versi API. ([#2781](https://github.com/Azure/azure-cli/issues/2781))
* Tambahkan dokumen untuk pembaruan az lock. ([#2702](https://github.com/Azure/azure-cli/issues/2702))
* Galat jika Anda mencoba mencantumkan sumber daya untuk grup yang tidak ada. ([#2769](https://github.com/Azure/azure-cli/issues/2769))
* [Komputasi] Memperbaiki masalah dengan pembaruan kumpulan ketersediaan VMSS dan VM. ([#2773](https://github.com/Azure/azure-cli/issues/2773))
* Memperbaiki pembuatan dan hapus kunci jika jalur sumber daya induk tidak ada ([#2742](https://github.com/Azure/azure-cli/issues/2742))

### <a name="role"></a>Peran

* create-for-rbac: pastikan tanggal akhir SP tidak akan melebihi tanggal kedaluwarsa sertifikat ([#2989](https://github.com/Azure/azure-cli/issues/2989))
* RBAC: tambahkan dukungan penuh untuk 'grup iklan' ([#2016](https://github.com/Azure/azure-cli/issues/2016))
* peran: memperbaiki masalah pada pembaruan definisi peran ([#2745](https://github.com/Azure/azure-cli/issues/2745))
* create-for-rbac: pastikan kata sandi yang disediakan pengguna diambil

### <a name="sql"></a>SQL

* Added az sql server list-usages and az sql db list-usages commands
* SQL - kemampuan untuk terhubung langsung ke penyedia sumber daya ([#2832](https://github.com/Azure/azure-cli/issues/2832))

### <a name="storage"></a>Penyimpanan

* Lokasi default ke lokasi grup sumber daya untuk `storage account create`
* Menambahkan dukungan untuk salinan blob inkremental
* Menambahkan dukungan untuk upload blob blok besar
* Ubah ukuran blok menjadi 100MB saat file diunggah lebih besar dari 200GB

### <a name="vm"></a>VM

* avail-set: jadikan UD&jumlah domain FD opsional

  catatan: Perintah VM di cloud berdaulat Harap hindari fitur terkait disk terkelola, termasuk yang berikut:
  1. az disk/snapshot/image
  2. az vm/vmss disk
  3. Di dalam "az vm/vmss create", gunakan "—use-unmanaged-disk" untuk menghindari disk terkelola Perintah lain harus berfungsi
* vm/vmss: meningkatkan teks peringatan saat menghasilkan pasangan kunci ssh
* vm/vmss: dukungan yang dibuat dari gambar market place yang memerlukan info rencana ([#1209](https://github.com/Azure/azure-cli/issues/1209))


## <a name="april-3-2017"></a>3 April 2017 pukul

Versi 2.0.2

Kami merilis komponen ACR, Batch, KeyVault, dan SQL dalam rilis ini

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

* Menambahkan acr, lab, monitor, dan menemukan modul ke daftar default
* Login: lewati penyewa yang salah ([#2634](https://github.com/Azure/azure-cli/pull/2634))
* login: atur langganan default ke langganan satu dengan status "Diaktifkan" ([#2575](https://github.com/Azure/azure-cli/pull/2575))
* Menambahkan perintah tunggu dan dukungan --no-wait ke lebih banyak perintah ([#2524](https://github.com/Azure/azure-cli/pull/2524))
* inti: mendukung login menggunakan prinsipal layanan dengan sertifikat ([#2457](https://github.com/Azure/azure-cli/pull/2457))
* Tambahkan permintaan untuk parameter template yang hilang. ([#2364](https://github.com/Azure/azure-cli/pull/2364))
* Mendukung pengaturan nilai default untuk argumen umum seperti grup sumber daya default, web default, vm default
* Mendukung login ke penyewa tertentu

### <a name="acs"></a>ACS

* [ACS] Menambahkan dukungan untuk mengonfigurasi klaster ACS default ([#2554](https://github.com/Azure/azure-cli/pull/2554))
* Tambahkan dukungan untuk mendorong kata sandi utama ssh. ([#2044](https://github.com/Azure/azure-cli/pull/2044))
* Tambahkan dukungan untuk klaster windows. ([#2211](https://github.com/Azure/azure-cli/pull/2211))
* Beralih dari peran Pemilik ke Kontributor. ([#2321](https://github.com/Azure/azure-cli/pull/2321))

### <a name="appservice"></a>AppService

* appservice: dukungan untuk mendapatkan alamat IP eksternal yang digunakan untuk catatan DNS A ([#2627](https://github.com/Azure/azure-cli/pull/2627))
* appservice: mendukung sertifikat wildcard yang mengikat ([#2625](https://github.com/Azure/azure-cli/pull/2625))
* appservice: profil penerbitan daftar dukungan ([#2504](https://github.com/Azure/azure-cli/pull/2504))
* AppService - Memicu sinkronisasi kontrol sumber setelah konfigurasi ([#2326](https://github.com/Azure/azure-cli/pull/2326))

### <a name="datalake"></a>DataLake

* Rilis awal modul Data Lake Analytics
* Rilis awal modul Data Lake Store

### <a name="docuemntdb"></a>DocuemntDB

* DocumentDB: Menambahkan dukungan untuk daftar string koneksi ([#2580](https://github.com/Azure/azure-cli/pull/2580))

### <a name="vm"></a>VM

* [Komputasi] Menambahkan dukungan AppGateway ke pengaturan skala mesin virtual ([#2570](https://github.com/Azure/azure-cli/pull/2570))
* [VM/VMSS] Dukungan caching disk yang ditingkatkan ([#2522](https://github.com/Azure/azure-cli/pull/2522))
* VM/VMSS: menggabungkan logika validasi kredensial yang digunakan oleh portal ([#2537](https://github.com/Azure/azure-cli/pull/2537))
* Menambahkan perintah tunggu dan dukungan --no-wait ([#2524](https://github.com/Azure/azure-cli/pull/2524))
* Set timbangan mesin virtual: dukungan * untuk mencantumkan tampilan instans di seluruh vms ([#2467](https://github.com/Azure/azure-cli/pull/2467))
* Tambahkan --secrets untuk VM dan set timbangan mesin virtual ([#2212}(<https://github.com/Azure/azure-cli/pull/2212>))
* Izinkan pembuatan VM dengan VHD khusus ([#2256](https://github.com/Azure/azure-cli/pull/2256))

## <a name="february-27-2017"></a>27 Februari 2017

Versi 2.0.0

Rilis Azure CLI 2.0 ini adalah rilis "Tersedia Secara Umum" pertama Ketersediaan umum berlaku untuk modul perintah ini:
- Layanan Kontainer (acs)
- Komputasi (termasuk Resource Manager, VM, set timbangan mesin virtual, Disk Terkelola)
- Jaringan
- Penyimpanan

Modul perintah ini dapat digunakan dalam produksi dan didukung oleh Microsoft SLA standar Anda dapat membuka masalah langsung dengan dukungan Microsoft atau pada [daftar masalah github](https://github.com/azure/azure-cli/issues/) kami Anda dapat mengajukan pertanyaan di [StackOverflow menggunakan tag azure-cli](http://stackoverflow.com/questions/tagged/azure-cli), atau menghubungi tim produk di [azfeedback@microsoft.com](mailto:azfeedback@microsoft.com) Anda dapat memberikan umpan balik dari baris perintah dengan `az feedback` perintah

Perintah dalam modul ini stabil dan sintaksnya tidak diharapkan berubah dalam rilis mendatang dari versi Azure CLI ini.

Untuk memverifikasi versi CLI, gunakan `az --version` Output mencantumkan versi CLI itu sendiri (2.0.0 dalam rilis ini), modul perintah individual, dan versi Python dan GCC yang Anda gunakan

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
> Beberapa modul perintah memiliki postfix "*bn*" atau "*rcn*" Modul perintah ini masih dalam pratinjau dan akan tersedia secara umum di masa depan

Kami juga memiliki build pratinjau per malam dari CLI Untuk informasi, lihat instruksi ini [untuk mendapatkan build malam](https://github.com/Azure/azure-cli#nightly-builds) hari, dan instruksi ini tentang [pengaturan pengembang dan kode kontribusi](https://github.com/Azure/azure-cli#developer-setup)

Anda dapat melaporkan masalah dengan pembuatan pratinjau malam dengan cara berikut:
- Melaporkan masalah dalam [daftar masalah github](https://github.com/azure/azure-cli/issues/) kami
- Hubungi tim produk di [azfeedback@microsoft.com](mailto:azfeedback@microsoft.com)
- Memberikan umpan balik dari baris perintah dengan `az feedback` perintah

---
title: Catatan rilis & pembaruan – Azure CLI | Microsoft Docs
description: Pelajari tentang catatan rilis dan pembaruan Azure Command-Line Interface (CLI) terbaru untuk versi CLI saat ini dan beta.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 03/03/2022
ms.topic: article
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: pembaruan Azure cli, catatan Azure cli, versi Azure cli
ms.openlocfilehash: b34ff5217b3fc7fee9b728d3c217fa8b65304c19
ms.sourcegitcommit: cbb162f5b74c5250338109317f06a152809c4b4c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/06/2022
ms.locfileid: "141397528"
---
# <a name="azure-cli-release-notes"></a>Catatan rilis Azure CLI

## <a name="march-03-2022"></a>03 Maret 2022

Versi 2.34.1

### <a name="app-service"></a>App Service

* Perbaikan: Perbaikan #20489: `az webapp log tail`: Perbaiki AttributeError bahwa objek 'NoneType' tidak memiliki atribut 'host_name_ssl_states'
* Perbaikan: Perbaikan #20747: `az webapp create-remote-connection`: Perbaiki EOFError yang kehabisan input
* Perbaikan: Perbaikan #20544: `az webapp config snapshot restore`: Perbaiki AttributeError bahwa objek 'WebAppsOperations' tidak memiliki atribut 'restore_snapshot'
* Perbaikan: Perbaikan #20011: `az webapp config ssl bind`: Perbaiki AttributeError bahwa objek 'str' tidak memiliki atribut 'value'
* Perbaikan: Perbaikan #19492: `az webapp config backup restore`: Perbaiki AttributeError bahwa objek 'WebAppsOperations' tidak memiliki atribut 'restore'

### <a name="storage"></a>Penyimpanan

* [BREAKING CHANGE] `az storage blob upload/upload-batch`: Perbaiki `--overwrite` bahwa itu tidak lagi menimpa secara default

## <a name="march-01-2022"></a>01 Maret 2022

Versi 2.34.0

### <a name="acr"></a>Azure Container Registry

* `az acr manifest`: Tambahkan grup perintah baru untuk mendukung pengelolaan manifes artefak di Azure Container Registries
* Perintah penghentian `az acr repository show-manifests` dan ganti dengan `acr manifest metadata list` perintah

### <a name="aks"></a>AKS

* `az aks nodepool update`: Tambahkan `--node-taints` untuk mengizinkan modifikasi taint simpul
* `az aks get-credentials`: Tambahkan parameter `--format` baru untuk mendukung penentuan format kredensial yang dikembalikan
* `az aks nodepool`: Izinkan menentukan `--scale-down-mode` dalam nodepool membuat dan memperbarui

### <a name="apim"></a>APIM

* `az apim api import`: Memperbarui deskripsi api-id #18306
* Perbaikan #21187: `az apim api create/update/import`: Perbaiki nama param header dan kueri yang ditukar

### <a name="app-config"></a>Konfigurasi Aplikasi

* `az appconfig kv import`: Tambahkan parameter `--strict` baru untuk mendukung impor yang ketat

### <a name="app-service"></a>App Service

* [BREAKING CHANGE] `az webapp up`: Mengubah runtime yang didukung
* [BREAKING CHANGE] `az webapp create`: Mengubah runtime yang didukung
* [BREAKING CHANGE] `az webapp list-runtimes`: Menambahkan `--os`/`--os-type` argumen, mengubah runtime, mengubah perilaku default untuk mengembalikan tumpukan linux dan windows, dan menghentikan argumen `--linux`
* [BREAKING CHANGE] `az functionapp create`: Mengambil nama dan versi runtime dari API alih-alih daftar hardcoded
* `az functionapp plan`: Perbarui nilai `--max-burst` maksimum hingga 100
* `az functionapp list-runtimes`: Tambahkan perintah baru untuk menampilkan runtime aplikasi fungsi, versi, dan versi fungsi yang kompatibel
* `az webapp create`: Berikan bendera dukungan `--https-only`
* `az webapp deployment github-actions remove`: Perbaiki bug yang jalurnya tidak dapat dimulai dengan garis miring

### <a name="arm"></a>ARM

* `az account management-group entities`: Menambahkan grup perintah baru untuk mendukung operasi entitas (Grup Manajemen dan Langganan) untuk pengguna yang diautentikasi
* `az account management-group hierarchy-settings`: Menambahkan grup perintah baru untuk mendukung operasi pada pengaturan hierarki yang ditentukan pada tingkat grup manajemen
* `az account management-group tenant-backfill`: Menambahkan grup perintah baru untuk mendukung langganan backfilling untuk penyewa
* `az account management-group subscription show`: Mendapatkan detail langganan tertentu di bawah grup manajemen tertentu
* `az account management-group subscription show-sub-under-mg`: Menampilkan langganan apa yang berada di bawah grup manajemen tertentu
* `az account management-group check-name-availability`: Periksa apakah nama grup manajemen valid dan tersedia
* `az deployment`: Perbaiki bug objek 'byte tidak memiliki atribut get' untuk penanganan kesalahan dalam kasus coba lagi

### <a name="backup"></a>Cadangan

* Menambahkan dukungan titik akhir privat untuk Microsoft.RecoveryServices/vaults

### <a name="compute"></a>Compute

* `az vm create`: Memperbaiki masalah bahwa VMCustomization tidak diaktifkan
* `az vm disk attach`: Ubah deskripsi bantuan untuk memandu cara menggunakan `--ids` parameter dengan benar
* `az restore-point`: Tambahkan grup perintah baru untuk mendukung pengelolaan titik pemulihan
* `az vmss create/update`: Tambahkan parameter `--security-type`baru , `--enable-secure-boot` dan `--enable-vtpm` untuk mendukung Peluncuran Tepercaya
* `az vmss create/update`: Menambahkan parameter `--automatic-repairs-action` baru untuk mendukung tindakan perbaikan
* `az vmss create/update`: Menambahkan parameter baru `--v-cpus-available` dan `--v-cpus-per-core` untuk mendukung penyesuaian VMSize

### <a name="cosmos-db"></a>Cosmos DB

* `az managed-cassandra cluster update`: Perbaiki untuk mengizinkan `--external-seed-nodes` dan `--external-gossip-certificates` diperbarui oleh pengguna

### <a name="eventhub"></a>Eventhub

* `az eventhubs namespace create`: Tambahkan `--user-assigned`, `--system-assigned`, `--encryption-config`
* `az eventhubs namespace identity`: Cmdlet untuk identitas pusat aktivitas
* `az eventhubs namespace encryption`: Cmdlet untuk enkripsi pusat aktivitas
* `az servicebus namespace create`: Tambahkan `--user-assigned`, `--system-assigned`, `--encryption-config`
* `az servicebus namespace identity`: Cmdlet untuk identitas pusat aktivitas
* `az servicebus namespace encryption`: Cmdlet untuk enkripsi pusat aktivitas

### <a name="iot"></a>IoT

* `az iot hub create`: Tambahkan `--enforce-data-residency` parameter untuk mendukung pembuatan sumber daya dengan residensi data yang diberlakukan (dan pemulihan bencana lintas wilayah dinonaktifkan)
* `az iot dps create`: Tambahkan `--enforce-data-residency` parameter untuk mendukung pembuatan sumber daya dengan residensi data yang diberlakukan (dan pemulihan bencana lintas wilayah dinonaktifkan)

### <a name="key-vault"></a>Key Vault

* Perbaikan #21341: `az keyvault update`: Mendukung pembaruan tag
* `az keyvault key create/import/set-attributes`: Dukungan `--immutable` untuk menandai kebijakan rilis tidak dapat diubah
* `az keyvault key import`: Dukungan `--kty oct` untuk mengimpor kunci AES

### <a name="monitor"></a>Monitor

* `az monitor log-analytics workspace table`: Tambahkan perintah `create`baru , `delete` dan `search-job create` untuk mendukung operasi tabel Log/Hasil Pencarian Microsoft/Kustom
* `az monitor log-analytics workspace update`: Tambahkan parameter `--data-collection-rule` baru untuk mendukung pembaruan defaultDataCollectionRuleResourceId
* `az monitor log-analytics workspace table`: Tambahkan perintah `restore create` baru dan `migrate` untuk mendukung tabel log yang dipulihkan/operasi migrasi

### <a name="network"></a>Jaringan

* `az bastion ssh`: Memberikan dukungan untuk akses Bastion SSH di Darwin dan Linux
* `az network private-endpoint`: Mengaitkan konfigurasi IP dan ASG saat membuat PE

### <a name="packaging"></a>Pengemasan

* [MELANGGAR PERUBAHAN] Drop Ubuntu 14.04 Trusty Tahr dan Debian 8 Dukungan Jessie
* [MELANGGAR PERUBAHAN] Hilangkan dukungan Hirsute Hippo Ubuntu 21.04
* Menambahkan dukungan Ubuntu 21.10 Impish Indri
* Bump embedded Python ke 3.8 untuk paket deb

### <a name="profile"></a>Profil

* [MELANGGAR PERUBAHAN] `az account show`: Hilangkan `--sdk-auth`

### <a name="rdbms"></a>RDBMS

* Memperbaiki bug untuk provisi zona dns privat ke grup sumber daya vnet di langganan yang berbeda
* Aktifkan ekstensi rdbms-connect di Cloud Shell

### <a name="role"></a>Peran

* Menambahkan peringatan ke `role` perintah dan `ad` tentang migrasi Microsoft Graph

### <a name="sql"></a>SQL

* `az sql server create/update`: Menambahkan dukungan id klien federasi

### <a name="storage"></a>Penyimpanan

* `az storage account create/update`: Dukungan `--sam-account-name` dan `--account-type`
* `az storage blob upload`: Tambahkan `--tier`, migrasikan ke track2
* `az storage blob upload-batch`: Bermigrasi ke track2

## <a name="february-14-2022"></a>14 Februari 2022

Versi 2.33.1

### <a name="compute"></a>Compute

* Perbaikan: Memperbaiki #21224: Memperbaiki masalah VMCustomization tidak diaktifkan

### <a name="packaging"></a>Pengemasan

* [BREAKING CHANGE] Menghilangkan terminal jmespath dari gambar docker

## <a name="february-01-2022"></a>1 Februari 2022

Versi 2.33.0

### <a name="acr"></a>Azure Container Registry

* `az acr connected-registry create`: Menambahkan `--notifications` untuk mendukung penambahan pola guna menghasilkan peristiwa pemberitahuan pada artefak registri yang terhubung
* `az acr connected-registry update`: Menambahkan `--add-notifications` dan `--remove-notifications` untuk mendukung penambahan atau penghapusan pola guna menghasilkan peristiwa pemberitahuan pada artefak registri yang terhubung

### <a name="aks"></a>AKS

* `az aks nodepool add/update/upgrade`: Menambahkan parameter baru `--aks-custom-headers` untuk mendukung header kustom
* `az aks create`: Menambahkan parameter baru `--snapshot-id` untuk mendukung pembuatan nodepool dari snapshot saat membuat kluster
* `az aks nodepool add/upgrade`: Menambahkan parameter baru `--snapshot-id` untuk mendukung pembuatan nodepool dari snapshot
* `az aks snapshot create/delete/list/show`: Menambahkan perintah baru untuk mendukung pengelolaan operasi terkait snapshot
* `az aks update/az aks nodepool update`: Mengizinkan string kosong sebagai nilai label

### <a name="app-config"></a>Konfigurasi Aplikasi

* [BREAKING CHANGE] Mendukung slot layanan aplikasi

### <a name="app-service"></a>App Service

* `az webapp vnet-integration add`: Memperbaiki bug yang mencegah penambahan vnet dalam langganan yang berbeda dari aplikasi web
* `az functionapp vnet-integration add`: Memperbaiki bug yang mencegah penambahan vnet dalam langganan yang berbeda dari aplikasi fungsi
* `az webapp create`: Mendukung bergabung dengan vnet dalam langganan yang berbeda
* `az functionapp create`: Mendukung bergabung dengan vnet dalam langganan yang berbeda
* `az functionapp create`: Menghapus pratinjau dari runtime PowerShell untuk linux
* `az appservice plan update`: Menambahkan parameter `--elastic-scale` dan `--max-elastic-worker-count` untuk mendukung skala elastis
* `az webapp update`: Menambahkan parameter `--minimum-elastic-instance-count` dan `--prewarmed-instance-count` untuk mendukung pengaturan jumlah instans
* `az webapp up`: Menambahkan teks bantuan dan teks debug untuk menyimpan dan memuat konfigurasi
* `az webapp list-runtimes`: Menambahkan runtime node 16-lts untuk linux dan windows

### <a name="batch"></a>Batch

* `az batch create/activate`: Menambahkan info bantuan jalur paket aplikasi klarifikasi untuk argumen `--package-file`

### <a name="bot-service"></a>Layanan Bot

* `az bot create`: Menambahkan lokasi seperti yang ditentukan oleh pengguna ke pembuatan bot untuk regionalitas/EUDB

### <a name="compute"></a>Compute

* `az image builder create`: Menambahkan parameter baru `--proxy-vm-size` untuk mendukung penyesuaian ukuran proksi Mesin Virtual
* `az image builder create`: Menambahkan parameter baru `--build-vm-identities` untuk mendukung penyesuaian identitas yang ditetapkan pengguna
* `az vmss update`: Menambahkan parameter baru `--force-deletion` untuk mendukung penghapusan paksa VMSS
* `az vm/vmss create`: Menambahkan log peringatan dan mengubah bantuan untuk menginformasikan bahwa nilai default `Contributor` dari `--role` akan dihapus
* `az disk-encryption-set create`: Membuat parameter `--source-vault` tidak diperlukan
* `az vm create/update`: Menambahkan parameter baru `--v-cpus-available` dan `--v-cpus-per-core` untuk mendukung penyesuaian VMSize

### <a name="cosmos-db"></a>Cosmos DB

* `az managed-cassandra cluster status`: Menambahkan dukungan format tabel

### <a name="key-vault"></a>Key Vault

* `az keyvault create`: Menambahkan izin default pada pembuatan keyvault

### <a name="monitor"></a>Monitor

* `az monitor action-group`: Mendukung penerima event hub

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`: Menambahkan parameter opsional baru bernama encrypt-dc-connections
* `az netappfiles volume export-policy add`: Menambahkan parameter opsional yang hilang kerberos5_read_only, kerberos5_read_write, kerberos5i_read_only, kerberos5i_read_write, kerberos5_p_read_only, kerberos5_p_read_write, has_root_access, chown_mode
* `az netappfiles account ad update`: Menambahkan perintah

### <a name="network"></a>Jaringan

* Menambahkan Microsoft.DataFactory/factories ke Titik Akhir Privat yang didukung
* Menambahkan Microsoft.Databricks/workspaces ke titik akhir privat yang didukung
* `az network private-endpoint`: Menambahkan parameter dan subgrup untuk mendukung Konfigurasi IP, ASG, dan NicName
* `az network traffic-manager endpoint create/update`: Menambahkan argumen baru `--min-child-ipv4` dan `--min-child-ipv6`.
* Menambahkan Microsoft.HybridCompute/privateLinkScopes ke Titik Akhir Privat yang didukung

### <a name="packaging"></a>Pengemasan

* Memperbarui gambar dasar Dockerfile dari Alpine 3.14 ke 3.15

### <a name="rdbms"></a>RDBMS

* `az postgres flexible-server create`: Mengubah versi postgres default

### <a name="redis"></a>Redis

* `az redis create`: Menambahkan nilai default untuk identitas dan akses jaringan publik sebagai `None`

### <a name="serviceconnector"></a>ServiceConnector

* Mendukung sumber daya target baru: servicebus, eventhub, appconfig

### <a name="storage"></a>Penyimpanan

* Berhenti mendukung `--auth-mode login` untuk `az storage blob sync` dan `az storage fs directory upload/download`

## <a name="january-04-2022"></a>4 Januari 2022

Versi 2.32.0

### <a name="aks"></a>AKS

* `az aks create`: Menambahkan parameter baru `--enable-fips-image` untuk mendukung pengaktifan gambar fips
* `az aks nodepool add`: Menambahkan parameter baru `--enable-fips-image` untuk mendukung pengaktifan gambar fips

### <a name="app-service"></a>App Service

* [BREAKING CHANGE] `az webapp up`: Menghapus dukungan untuk runtime python|3.6 (linux dan windows), ruby|2.5 (linux), dan php|7.3 (windows). Menambahkan dukungan untuk runtime python|3.9 (linux), php|8.0 (linux), dan ruby|2.7 (linux)
* [BREAKING CHANGE] `az webapp create`: Menghapus dukungan untuk runtime python|3.6 (linux dan windows), ruby|2.5 (linux), dan php|7.3 (windows). Menambahkan dukungan untuk runtime python|3.9 (linux), php|8.0 (linux), dan ruby|2.7 (linux)
* [BREAKING CHANGE] `az functionapp create`: Menghapus dukungan python 3.6
* Memperbaiki #19550: `az staticwebapp users update`: Mengizinkan pembaruan peran pengguna aplikasi web statis lagi
* `az logicapp create`: Membuat Paket App Service WS1 secara otomatis saat tidak ada nilai untuk `--plan` atau `--consumption-plan-location` yang diberikan
* `az appservice plan create`: Mengizinkan pembuatan Paket App Service untuk Logic Apps (SKU WS1, WS2, dan WS3)
* Memperbaiki #20757: `az webapp up`: Memperbaiki indeks daftar di luar jangkauan ketika tidak ada argumen `--plan` yang diteruskan
* Memperbaiki #18652: `az webapp up`: Mencari \*.csproj di direktori turunan
* `az webapp list-runtimes`: Menghapus dukungan untuk runtime python|3.6 (linux dan windows), ruby|2.5 (linux), dan php|7.3 (windows). Menambahkan dukungan untuk runtime python|3.9 (linux), php|8.0 (linux), dan ruby|2.7 (linux)

### <a name="backup"></a>Cadangan

* `az backup restore restore-azurewl`: Menambahkan validasi sisi klien
* `az backup container unregister`: Menambahkan jenis MAB untuk parameter `--backup-management-type`
* `az backup protectable-item list/show`: Menambahkan bidang kebijakan perlindungan otomatis dan daftar node dalam respons untuk SQLInstance SQLAG
* `az backup protection auto-enable-for-azurewl/auto-disable-for-azurewl`: Menambahkan dukungan untuk SQLAG

### <a name="compute"></a>Compute

* `az vm/vmss create/update`: Memperluas validasi jenis lisensi untuk parameter `--license-type`
* `az sig image-definition list-shared`: Menambahkan parameter baru `--marker` dan `--show-next-marker` untuk mendukung paging
* `az sig image-version list-shared`: Menambahkan parameter baru `--marker` dan `--show-next-marker` untuk mendukung paging

### <a name="iot"></a>IoT

* `az iot hub update`: Menambahkan penanganan kesalahan untuk parameter pengunggahan file dan memperbaiki kesalahan titik akhir penyimpanan $default yang kosong
* `az iot central app create`: Menambahkan parameter baru `--mi-system-assigned` untuk mendukung pembuatan aplikasi dengan identitas terkelola yang ditetapkan sistem
* `az iot central app identity show/assign/remove`: Menambahkan perintah baru untuk mengelola identitas terkelola yang ditetapkan sistem ke aplikasi IoT Central yang ada
* `az iot dps access-policy`: Diganti dengan `az iot dps policy`
* `az iot dps linked-hub create`: Menambahkan argumen kenyamanan untuk menghubungkan hub

### <a name="network"></a>Jaringan

* Memperbaiki #19482: Perbaikan Azure Bastion AAD untuk perubahan core CLI baru
* `az network lb inbound-nat-pool create`: Menambahkan parameter baru `--backend-pool-name`

### <a name="profile"></a>Profil

* `az account show/set`: Menambahkan `-n`, argumen `--name`

### <a name="redis"></a>Redis

* `az redis identity`: Menambahkan dukungan untuk menetapkan dan memodifikasi Identitas

### <a name="rest"></a>REST

* [BREAKING CHANGE] `az rest`: Menghapus `resourceGroup`, mengubah `x509ThumbprintHex`

### <a name="role"></a>Peran

* [BREAKING CHANGE] `az ad sp create-for-rbac`: Menghilangkan properti `name` dari output. Menggunakan `appId` sebagai gantinya
* [BREAKING CHANGE] `az ad sp create-for-rbac`: Tidak ada penetapan peran yang akan dibuat secara default

### <a name="storage"></a>Penyimpanan

* `az storage copy`: Menambahkan argumen posisi `extra_options` untuk melewati opsi ke `azcopy`

### <a name="synapse"></a>Synapse

* [BREAKING CHANGE] `az synapse managed private endpoints create`: Menghapus `--resource-id` dan `--group-id`, menggunakan `--file` sebagai gantinya
* `az synapse sql pool create/restore`: Menambahkan parameter `--storage-type` untuk mendukung penentuan jenis akun penyimpanan
* `az synapse kql-script`: Grup perintah baru untuk mendukung skrip Kusto

## <a name="december-07-2021"></a>7 Desember 2021

Versi 2.31.0

### <a name="aks"></a>AKS

* `az aks update`: Mendukung pengeditan label nodepool setelah pembuatan
* `az aks nodepool update`: Mendukung pengeditan label nodepool setelah pembuatan
* `az aks create`: Memperbaiki masalah parameter `--attach-acr` tidak berfungsi

### <a name="ams"></a>AMS

* Menghapus variabel 'identifier_uri' yang tidak digunakan lagi dari pembuatan metode sp
* Memperbarui versi api untuk pendaftaran tautan pribadi AMS dan AVA

### <a name="app-service"></a>App Service

* `az functionapp create`: Menambahkan dukungan untuk membuat aplikasi web yang digabungkan ke vnet
* `az webapp up`: Memperbaiki kegagalan mendeteksi aplikasi web dotnet 6.0
* `az appservice ase update`: Mendukung izin koneksi titik akhir privat baru di ASEv3
* `az appservice ase list-addresses`: Mendukung ASEv3
* `az staticwebapp identity assign`: Menetapkan identitas layanan terkelola ke aplikasi web statis
* `az staticwebapp identity remove`: Menonaktifkan identitas layanan terkelola aplikasi web statis
* `az staticwebapp identity show`: Menampilkan identitas layanan terkelola aplikasi web statis
* Memperbaiki #17507: `az staticwebapp functions`: Menambahkan dukungan untuk menautkan aplikasi fungsi yang ada ke aplikasi web statis (fungsi bring your own)
* `az staticwebapp create`: Memperbarui teks bantuan dengan panduan untuk repo di organisasi Github
* `az functionapp deployment source config-zip`: Memperbaiki #12289: Mengizinkan build on zip deploy untuk aplikasi fungsi windows
* `az staticwebapp create`: Menambahkan pesan kesalahan yang lebih baik saat mencoba membuat aplikasi web statis yang sudah ada
* `az appservice`: Memperbaiki AttributeError selama penanganan kesalahan pengguna
* `az appservice plan create`: Menambahkan parameter `--zone-redundant` untuk mendukung pengaktifan redundansi zona untuk ketersediaan tinggi
* `az webapp ssh`: Menambahkan dukungan proksi
* `az webapp create-remote-connection`: Menambahkan dukungan proksi
* `az webapp log download/tail`: Menambahkan dukungan proksi
* `az webapp create`: Memperbaiki penguraian url server registri kontainer untuk argumen `--deployment-container-image-name/-i`
* `az functionapp deployment source config-zip`: Memperbaiki pengembalian yang berhasil saat penyebaran tidak berhasil
* `az staticwebapp appsettings set`: Membuat set berfungsi
* `az staticwebapp appsettings`: Beralih ke metode SDK pengaturan aplikasi SWA baru
* `az functionapp plan create`: Menambahkan parameter `--zone-redundant` guna memberikan opsi untuk membuat paket layanan aplikasi zona redundan
* Mendukung identitas terkelola dalam kontainer App Service

### <a name="arm"></a>ARM

* `az resource\group list`: Mendukung kueri data hanya dengan meneruskan nama tag ke parameter `--tag`
* `az account management-group`: Menambahkan parameter baru `--no-register` untuk melewati pendaftaran RP `Microsoft.Management`
* `az deployment`: Mempercantik output kesalahan untuk penyebaran ARM
* `az bicep install`: Menambahkan parameter baru `--target-platform/-t` untuk menentukan platform yang berjalan dari Bicep CLI
* `az bicep upgrade`: Menambahkan parameter baru `--target-platform/-t` untuk menentukan platform yang berjalan dari Bicep CLI
* `az deployment sub/tenant/mg create`: Memperbaiki `KeyError: 'resourceGroup'` dalam mengeluarkan hasil dalam format tabel saat menyebarkan sumber daya tingkat grup non-sumber daya
* `az policy assignment create` dan `az policy assignment identity assign` mendukung penambahan identitas yang ditetapkan pengguna
* `az bicep install`: Sekarang bekerja di belakang proksi perusahaan

### <a name="backup"></a>Cadangan

* GA `az backup` dan beberapa perbaikan bug
* `az backup protectable-item list/show`: Memperbaiki AttributeError untuk server_name
* `az backup restore restore-disks`: Menambahkan dukungan untuk Pemulihan Cross Zonal

### <a name="cognitive-services"></a>Cognitive Services

* `az cognitiveservices account deployment`: Menambahkan perintah baru `show`, `list`, `create`, `delete`
* `az cognitiveservices account commitment-plan`: Menambahkan perintah baru `show`, `list`, `create`, `delete`
* `az cognitiveservices commitment-tier`: Menambahkan perintah baru `list`

### <a name="compute"></a>Compute

* Memperbaiki #20182: `az snapshot create`: Memperbaiki bug deteksi otomatis untuk `--copy-start`
* Memperbaiki #20133: `az vm create`: Memperbaiki `--data-disk-delete-option` tidak berfungsi saat tidak ada `--attach-data-disks` yang disediakan
* Memperbaiki decoding diagnostik boot
* `az vm create/update`: Menambahkan parameter baru `--enable-hibernation` untuk mendukung pengaktifan kemampuan hibernasi
* `az vm/vmss run-command show`: Menambahkan parameter baru `--instance-view` untuk mendukung pelacakan progres RunCommand
* Memperbarui deskripsi bantuan untuk disk yang tidak dikelola
* `az disk create/update`: Menambahkan argumen `--public-network-access` untuk mengontrol kebijakan ekspor pada disk
* `az disk create/update`: Menambahkan argumen `--accelerated-network` untuk mendukung jaringan yang dipercepat
* `az snapshot create/update`: Menambahkan argumen `--public-network-access` untuk mengontrol kebijakan ekspor pada disk
* `az snapshot create/update`: Menambahkan argumen `--accelerated-network` yang mendukung jaringan yang dipercepat
* `az snapshot create`: Memperbaiki #20258: Memperbaiki pembuatan snapshot dari disk Uniform VMSS OS

### <a name="eventgrid"></a>EventGrid

* GA `az eventgrid system-topic`

### <a name="key-vault"></a>Key Vault

* `az keyvault key encrypt/decrypt`: Mendukung algoritma AES untuk MHSM
* `az keyvault key rotation-policy update`: Mendukung json camel case dan snake case untuk `--value`

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles volume create`: Memperbaiki kebijakan ekspor volume

### <a name="network"></a>Jaringan

* `az network express-route peering connection ipv6-config`: Menambahkan perintah baru `set`, `remove`
* `az network application-gateway waf-policy managed-rule exclusion`: Menambahkan subgrup baru `rule-set` untuk mendukung per pengecualian aturan
* `az network bastion create`: Memperbaiki validator yang tidak valid saat `--scale-units` tidak ada
* `az network vnet create`: Menambahkan argumen `--enable-encryption` untuk mendukung pengaktifan enkripsi pada jaringan virtual
* `az network vnet update`: Menambahkan argumen `--enable-encryption` untuk mendukung pengaktifan enkripsi pada jaringan virtual
* `az network vnet create`: Menambahkan argumen `--encryption-enforcement-policy` untuk memilih Apakah Mesin Virtual tanpa enkripsi diizinkan di Jaringan Virtual terenkripsi.
* `az network vnet update`: Menambahkan argumen `--encryption-enforcement-policy` untuk memilih Apakah Mesin Virtual tanpa enkripsi diizinkan di Jaringan Virtual terenkripsi.

### <a name="packaging"></a>Pengemasan

* Mendukung Python 3.10
* Menambahkan Dockerfile.mariner untuk mendukung build Mariner

### <a name="profile"></a>Profil

* `az logout`, `az account clear`: Menghapus file cache token ADAL `accessTokens.json`

### <a name="rdbms"></a>RDBMS

* Memperbaiki bug akhiran zona DNS pribadi
* Memperbaiki #20124: `az mysql/postgres flexible-server db create`: Membuat grup sumber daya dan nama server diperlukan
* `az postgres flexible-server`: Menghapus tag pratinjau

### <a name="storage"></a>Penyimpanan

* `az storage share list-handle/close-handle`: Perintah baru untuk pegangan berbagi
* Tingkat akun GA dan penyimpanan abadi tingkat versi blob

### <a name="synapse"></a>Synapse

* [BREAKING CHANGE] `az synapse sql/pool audit-policy`: Menghapus `--blob-auditing-policy-name`
* `az synapse notebook/spark-job-definition`: Menambahkan argumen `--folder-path`
* `az synapse spark pool create/update`: Menambahkan `--spark-config-file-path`
* `az synapse spark job submit`: Perbaikan untuk `--main-class-name`
* `az synapse sql-script`: Grup perintah baru untuk mendukung manajemen skrip sql

## <a name="november-02-2021"></a>2 November 2021

Versi 2.30.0

### <a name="core"></a>Core

* [BREAKING CHANGE] Memigrasikan dari ADAL ke MSAL. Untuk detail selengkapnya, lihat [Azure CLI berbasis MSAL](./msal-based-azure-cli.md)

### <a name="acr"></a>Azure Container Registry

* [BREAKING CHANGE] `az connected-registry`: `--repository` versi pendek bendera `-t` sedang dihapus.
* [BREAKING CHANGE] `az connected-registry install renew credentials`: Sekarang pengguna harus mengonfirmasi pembuatan kata sandi.
* `az connected-registry install`: Menghentikan dan mengalihkan ke `az acr connected-registry get-settings`.
* `az connected-registry repo`: Menghentikan dan mengalihkan ke `az acr connected-registry permissions update`.
* `az connected-registry permissions show`: Perintah baru yang memungkinkan pengguna melihat informasi peta cakupan sinkronisasi.
* `az connected-registry get-settings`: Perintah baru yang mengambil informasi yang diperlukan untuk menginstal registri yang terhubung dan memungkinkan pembuatan kata sandi token sinkronisasi baru.
* `az connected-registry create`: Tidak lagi menambahkan postfix ke token sinkronisasi dan nama peta cakupan.

### <a name="aks"></a>AKS

* `az aks create/update`: Menambahkan parameter baru `--aks-custom-headers` untuk mendukung header kustom
* `az aks create`: Mendukung pengaturan `--private-dns-zone` ke tidak ada untuk pembuatan kluster pribadi
* `az aks create/update`: Menambahkan parameter baru `--enable-secret-rotation` dan `--rotation-poll-interval` untuk mendukung rotasi rahasia
* `az aks enable-addons`: Menambahkan parameter baru `--enable-secret-rotation` dan `--rotation-poll-interval` untuk mendukung rotasi rahasia

### <a name="app-config"></a>Konfigurasi Aplikasi

* `az appconfig kv import/export`: Menambahkan parameter baru `--profile` untuk mendukung penggunaan profil `appconfig/kvset`

### <a name="app-service"></a>App Service

* Memperbaiki #19617: `az webapp ssh`: Membuka Web SSH pada instans yang ditentukan
* `az staticwebapp hostname`: Mendukung penambahan nama host aplikasi web statis melalui validasi TXT
* Mengaktifkan dukungan untuk PowerShell di aplikasi fungsi Linux dengan V4

### <a name="arm"></a>ARM

* `az bicep publish`: Menambahkan perintah baru untuk menerbitkan modul bicep

### <a name="aro"></a>ARO

* `az aro create`: Menghapus URI Pengidentifikasi

### <a name="compute"></a>Compute

* `az disk update`: Memperbaiki masalah pembaruan kebijakan akses jaringan ke `AllowPrivate` gagal
* `az vm update`: Menambahkan argumen `--host` dan argumen `--host-group` untuk mendukung penetapan Mesin Virtual yang ada ke ADH tertentu
* Memperbaiki #19599: `az vm create`: Memperbaiki masalah `--nic-delete-option` tidak berfungsi jika `--nics` tidak disediakan.
* `az snapshot create`: Mendukung copyStart sebagai createOption
* `az vmss create/update`: Mendukung patching in-guest untuk VMSS
* `az vm application set/list`: Menambahkan perintah baru untuk mendukung aplikasi Mesin Virtual
* `az vmss application set/list`: Menambahkan perintah baru untuk mendukung aplikasi VMSS
* `az vm create`: Menambahkan argumen `--ephemeral-os-disk-placement` untuk mendukung pemilihan lokasi penyediaan disk OS Ephemeral
* `az vmss create`: Menambahkan argumen `--ephemeral-os-disk-placement` untuk mendukung pemilihan lokasi penyediaan disk OS Ephemeral
* `az vm update`: Menambahkan argumen `--size` untuk mendukung pengubahan ukuran
* `az vmss update`: Menambahkan argumen `--vm-sku` untuk mendukung pengubahan ukuran
* `az vm run-command`: Menambahkan perintah baru untuk mendukung pengelolaan perintah yang berjalan di Mesin Virtual
* `az vm update`: Menambahkan argumen `--ephemeral-os-disk-placement` untuk mendukung pemilihan lokasi penyediaan disk OS Ephemeral
* `az vmss update`: Menambahkan argumen `--ephemeral-os-disk-placement` untuk mendukung pemilihan lokasi penyediaan disk OS Ephemeral
* `az sig gallery-application`: Menambahkan perintah baru untuk mendukung pengelolaan aplikasi galeri
* `az sig gallery-application version`: Menambahkan perintah baru untuk mendukung pengelolaan versi aplikasi galeri
* GA fitur yang terkait dengan Flex VMSS

### <a name="container"></a>Kontainer

* `az container create`: Menambahkan parameter `--zone` untuk mendukung pemilihan Zona Ketersediaan
* `az container create`: Memperbaiki masalah `--subnet` atau `--vnet` tidak dapat digunakan dengan jenis alamat IP `Public` untuk mengizinkan `Private`
* `az container create`: Menambahkan Dukungan untuk `--registry-login-server` agar berfungsi dengan `--acr-identity`

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb mongodb retrieve-latest-backup-time`: Menambahkan perintah baru untuk mengambil stempel waktu terbaru yang dapat dipulihkan untuk Akun Mongo.
* `az cosmosdb locations`: Menambahkan perintah baru untuk mencantumkan lokasi akun dan propertinya.
* `az managed-cassandra cluster/data-center`: Mendukung GA untuk kluster cassandra dan pusat data terkelola

### <a name="dms"></a>DMS

* `az dms project create/az dms project task create` : Menambahkan proyek/tugas MySQL untuk migrasi offline.

### <a name="functionapp"></a>FunctionApp

* [BREAKING CHANGE] `az functionapp devops-pipeline`: Menghapus perintah dan memindahkan ke ekstensi `functionapp`

### <a name="hdinsight"></a>HDInsight

* `az hdinsight create`: Menambahkan dua parameter `--zones` dan `--private-link-configurations` untuk mendukung pembuatan kluster dengan fitur zona ketersediaan dan membuat kluster yang mengaktifkan tautan pribadi dengan fitur konfigurasi tautan pribadi.

### <a name="key-vault"></a>Key Vault

* Mendukung Keyvault SKR
* `az keyvault key random`: Meminta beberapa byte acak dari managedHSM
* `az keyvault rotation-policy/key rotate`: Mendukung tombol putar dan mengelola kebijakan rotasi kunci
* `az keyvault create/update`: Menambahkan parameter `--public-network-access`

### <a name="monitor"></a>Monitor

* `az monitor metrics alert condition` : Menambahkan dukungan untuk 'lewati validasi metrik'

### <a name="netappfiles"></a>NetAppFiles

* [BREAKING CHANGE] `az netappfiles account backup-policy create/update`: Menghapus parameter opsional `--yearly-backups`.
* `az netappfiles account list`: Menambahkan opsi untuk melewati parameter `--resource-group` dan mengambil akun untuk langganan.
* `az netappfiles pool create`: Menambahkan parameter opsional bernama `--encryption-type`
* `az netappfiles volume create`: Menambahkan parameter opsional: `--network-features`, `--avs-data-store`, `--default-group-quota`, `--default-user-quota`, `--is-def-quota-enabled`
* `az netappfiles volume update`: Menambahkan parameter opsional: `--default-group-quota`, `--default-user-quota`, `--is-def-quota-enabled`

### <a name="network"></a>Jaringan

* `az network bastion create`: Menambahkan parameter baru `--scale-units` dan `--sku` untuk mendukung unit skala pengaturan
* `az network vnet`: Menambahkan parameter `--bgp-community`
* `az network private-endpoint-connection`: Mendukung "Microsoft.Cache/Redis"
* `az network private-endpoint-connection`: Mendukung "Microsoft.SignalRService/WebPubSub"

### <a name="rdbms"></a>RDBMS

* Memperkenalkan perintah georestore MySQL dan memperbarui validator
* GA `az mysql flexible-server`

### <a name="service-bus"></a>Service Bus

* Memperbaiki kapasitas MU untuk memasukkan 16 saat memperbarui namespace

### <a name="serviceconnector"></a>ServiceConnector

* `az webapp/spring-cloud connection`: Grup perintah baru untuk mendukung layanan ke koneksi layanan

### <a name="sql"></a>SQL

* `az sql server ad-admin`: Memperbaiki perubahan yang melanggar yang dibuat untuk memperbarui dan menghapus

### <a name="synapse"></a>Synapse

* `az synapse kusto`: Menambahkan dukungan Kusto pool(mgmt)

## <a name="october-29-2021"></a>29 Oktober 2021

Versi 2.29.2

### <a name="aro"></a>ARO

* Perbaikan: `az aro create`: Menghapus URI Pengidentifikasi

## <a name="october-21-2021"></a>21 Oktober 2021

Versi 2.29.1

### <a name="compute"></a>Compute

* Perbaikan: Memperbaiki perintah aplikasi web statis yang rusak karena peningkatan versi `azure-mgmt-web` ke 4.0.0

## <a name="october-12-2021"></a>12 Oktober 2021

Versi 2.29.0

### <a name="aks"></a>AKS

* `az aks check-acr`: Bump canipull ke 0.0.3 alpha untuk mendukung sovereign cloud
* `az aks create/update`: Menambahkan parameter baru `--disable-local-accounts` untuk mendukung penonaktifan akun lokal
* `az aks enable-addons`: Mendukung addon open-service-mesh
* `az aks create/update`: Menambahkan dukungan untuk memperbarui tag

### <a name="app-config"></a>Konfigurasi Aplikasi

* Memperbaiki dependensi untuk beberapa penginstalan `jsondiff` dan `javaproperties`

### <a name="app-service"></a>App Service

* `az webapp create/up`: Memperbaiki kesalahan ketik versi Java yang salah di bantuan
* `az logicapp create/delete/show/list`: Menambahkan perintah baru untuk mendukung operasi terkait aplikasi logika
* `az staticwebapp environment delete`: Menambahkan perintah untuk mendukung penghapusan lingkungan aplikasi statis
* `az functionapp show`: Menambahkan validasi jenis untuk operasi pertunjukan
* `az webapp config backup list`: Memperbaiki masalah yang menampilkan konfigurasi cadangan, bukan daftar cadangan
* `az logicapp start/restart/stop`: Menambahkan perintah baru untuk logicapp
* `az webapp config storage-account`: Memperbarui deskripsi parameter

### <a name="arm"></a>ARM

* `az deployment`: Menghapus log isi permintaan pencetakan dari kebijakan kustom
* `az deployment group create`: Memperbaiki cakupan yang salah dalam contoh pembuatan penyebaran dari template-spec
* `az ts create`: Menyederhanakan pesan konfirmasi penimpaan

### <a name="backup"></a>Cadangan

* `az backup container register`: Memperbaiki bug kontainer penyegaran
* `az backup`: Menambahkan fungsionalitas CRR untuk Beban Kerja Azure
* `az backup`: Menambahkan dukungan untuk jenis manajemen cadangan MAB di beberapa sub perintah

### <a name="compute"></a>Compute

* `az sig create/update`: Menambahkan parameter baru `--soft-delete` untuk mendukung penghapusan sementara
* `az sig image-version`: Menambahkan parameter baru `--replication-mode` untuk mendukung pengaturan mode replikasi
* `az vm/vmss update`: Memperbaiki pemisahan VM/VMSS dari reservasi kapasitas
* `az vm/vmss create`: Menyembunyikan alias `--data-delete-option` dalam bantuan
* `az vmss create`: Mendukung pembuatan cepat VMSS yang fleksibel

### <a name="container"></a>Kontainer

* [BREAKING CHANGE] `az container create`: Menghapus parameter `--network-profile`, properti tidak lagi didukung
* `az container logs`: Memperbaiki kesalahan atribut yang disebabkan oleh migrasi Track 2
* `az container create`: Menambahkan parameter `--acr-identity` untuk mendukung penarikan gambar ACR terautentikasi MSI

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb identity assign/remove`: Menambahkan dukungan untuk identitas pengguna

### <a name="eventhub"></a>Eventhub

* `az eventhubs namespace update`: Menambahkan `--infra-encryption` untuk enkripsi (enable-require-infrastructure-encryption).
* `az eventhubs namespace create/update`: Menambahkan `--disable-local-auth` untuk mengaktifkan atau menonaktifkan autentikasi SAS.
* `az eventhubs namespace`: Menambahkan grup perintah `private-endpoint-connection` dan `private-link-resource`

### <a name="key-vault"></a>Key Vault

* [BREAKING CHANGE] Memperbaiki #18479: `az keyvault network-rule add`: Memperbaiki bug yang memungkinkan duplikat `--ip-address` dengan yang sudah ada di aturan jaringan
* Memperbaiki #10254: `az keyvault network-rule add`: Menambahkan kemampuan untuk menerima beberapa alamat ip sebagai daftar dalam bentuk `--ip-address ip1 [ip2] [ip3]...`
* `az keyvault delete`: Menambahkan peringatan saat menghapus HSM terkelola

### <a name="network"></a>Jaringan

* Menambahkan `az network custom-ip prefix wait`
* Menambahkan `az network vnet-gateway packet-capture wait`
* Menambahkan `az network vnet-gateway vpn-client ipsec-policy wait`
* Menambahkan `az network vnet-gateway nat-rule wait`
* Menambahkan `az network vpn-connection packet-capture wait`
* Tautan pribadi dan dukungan titik akhir untuk penyedia `Microsoft.BotService/botServices` ke operasi titik akhir privat yang didukung
* `az network application-gateway client-cert`: Menambahkan perintah `update` dan `show`
* `az network application-gateway ssl-profile`: Menambahkan perintah `update` dan `show`
* `az network application-gateway http-listener create`: Menambahkan parameter `--ssl-profile`
* `az network application-gateway http-listener update`: Menambahkan parameter `--ssl-profile`
* cmdlet jaringan link2 pribadi hdinsight onboard
* `az network bastion create`: Menambahkan argumen `--tags`
* Tautan pribadi dan dukungan titik akhir untuk penyedia `Microsoft.Authorization/resourceManagementPrivateLinks`
* Tautan pribadi dan dukungan titik akhir untuk penyedia `Microsoft.MachineLearningServices/workspaces`

### <a name="profile"></a>Profil

* `az account show`: Menghentikan `--sdk-auth`

### <a name="rdbms"></a>RDBMS

* [BREAKING CHANGE] `az postgres flexible-server migration`: Mengubah `--properties @{filepath}` menjadi `--properties {filepath}`
* `az postgres flexible-server migration create`: Pengguna dapat memasukkan nama file dengan tanda kutip ganda atau tanpa tanda kutip dan hal ini juga berlaku untuk jalur absolut.
* `az postgres flexible-server migration check-name-availability`: Menambahkan perintah untuk memeriksa apakah nama migrasi tersedia.
* `az postgres flexible-server migration update`: Menambahkan `--start-data-migration` untuk menjadwalkan ulang migrasi agar dimulai sekarang.
* Memperbarui list-skus, membuat pengaturan lokasi perintah dan perintah replika

### <a name="role"></a>Peran

* `az ad sp create-for-rbac`: Menghentikan `--sdk-auth`

### <a name="security"></a>Keamanan

* Menambahkan perintah `az security setting update`

### <a name="storage"></a>Penyimpanan

* Memperbaiki # 19279: Menambahkan klarifikasi untuk nama sistem file yang juga berarti nama kontainer.
* Memperbaiki #19059: Memperbaiki tautan dokumen agar mengarah ke situs web dokumen publik
* `az storage account hns-migration start/stop`: Mendukung migrasi akun penyimpanan untuk mengaktifkan ruang nama hierarkis
* `az storage container-rm create/update`: Menambahkan `--root-squash` untuk mendukung pengaktifan nfsv3 root squash atau all squash
* Memperbaiki #17858: `az storage blob upload`: membuat --nama opsional
* `az storage account create/update`: Menambahkan --parameter akses jaringan publik
* `az storage container immutability-policy create`: Menambahkan parameter --allow-protected-append-writes-all/--w-all
* `az storage container legal-hold set`: Menambahkan parameter --allow-protected-append-writes-all/--w-all
* `az storage account create/update`: Mengaktifkan kekekalan tingkat akun

### <a name="synapse"></a>Synapse

* [BREAKING CHANGE] `az synapse sql/pool audit-policy update`: Menambahkan parameter `blob-storage-target-state`, `log-analytics-target-state`, `event-hub-target-state` (setidaknya pilih salah satu dari 3 paras ini)
* `az synapse integration-runtime`: Mendukung integration-runtime start/stop
* `az synapse trigger`: Menambahkan az synapse trigger wait
* `az synapse trigger-run`: Menambahkan az synapse trigger-run cancel
* `az synapse integration-runtime`: Menghentikan perintah `create` dan akan mengalihkan ke perintah `managed create` atau `self-hosted create`
* `az synapse dataset/pipeline/linked-service/trigger`: Menghentikan perintah `set` dan akan mengalihkan ke perintah `update`
* `az synapse workspace-package`: Mendukung CRUD paket ruang kerja
* `az synapse spark pool update`: Mendukung penambahan atau penghapusan paket tertentu
* `az synapse workspace create/update`: Menambahkan argumen untuk mendukung konfigurasi repositori ruang kerja synapse
* `az synapse spark-job-definition`: Mendukung definisi kerja CRUD spark

## <a name="september-09-2021"></a>09 September 2021

Versi 2.28.1

### <a name="arm"></a>ARM

Perbaikan: Memperbaiki #19468: pip menginstal Azure-cli 2.0.73 karena dependensi pada paket `jsmin` tidak digunakan lagi

## <a name="september-07-2021"></a>7 September 2021

Versi 2.28.0

### <a name="acr"></a>Azure Container Registry

* `az acr create/update`: Menambahkan dukungan untuk menonaktifkan ekspor melalui `--allow-exports`
* `az acr`: Bump core api-version ke `2021-06-01-preview` dari `2020-11-01-preview`. agent_pool, operasi tugas dan eksekusi tidak berubah dari `2019-06-01-preview`
* `az acr task credential`: Memperbaiki masalah saat kredensial tugas tidak digunakan
* `az acr task logs`: Memperbaiki AttributeError saat mengkueri log tugas

### <a name="aks"></a>AKS

* [BREAKING CHANGE] `az aks nodepool update`: Mengubah menolak kemampuan untuk menggunakan max-surge dengan node-image-only
* `az aks install-cli`: Menambahkan dukungan untuk rilis kubelogin darwin/arm64
* Memperbaiki parameter yang dilewatkan secara salah untuk opsi `--assign-kubelet-identity` di aks create sub-command
* Meningkatkan versi api ke `2021-07-01` untuk modul ACS
* `az aks create/update`: Menambahkan dukungan untuk fitur fqdn publik kluster pribadi
* Mengembalikan PR #18825: `az aks create/update`: Menambahkan parameter `--auto-upgrade-channel` untuk mendukung peningkatan otomatis (dengan perbaikan)
* `aks create/aks nodepool add`: Menambahkan parameter ` --os-sku` untuk mendukung pemilihan OS host kontainer yang mendasari

### <a name="app-config"></a>Konfigurasi Aplikasi

* `appconfig kv import/export`: Menambahkan validasi titik akhir selama impor dan ekspor

### <a name="app-service"></a>App Service

* `az webapp config storage-account list/add/update/delete`: Menghapus tanda pratinjau
* Memperbaiki #18497: `functionapp identity show`: Memperbaiki crash saat nama aplikasi fungsi tidak merujuk pada aplikasi fungsi yang ada
* `az webapp config set`: Menambahkan contoh bantuan tambahan untuk pengguna PowerShell
* Memperbaiki #17818: `az functionapp update`: Menambahkan validasi instans untuk memperbarui aplikasi fungsi
* `az webapp config hostname add`: Memperbaiki masalah yang disebabkan oleh AttributeError
* `az webapp config hostname add`: Memperbaiki masalah yang disebabkan oleh AttributeError
* Memperbaiki #16470: `az staticwebapp secrets`: Menambahkan perintah untuk mengelola rahasia penyebaran
* `az webapp deployment source config-local-git`: Memperbaiki masalah yang disebabkan oleh AttributeError saat opsi slot ditentukan
* `az webapp deleted restore` : Memperbaiki masalah objek 'WebAppsOperations' tidak memiliki atribut 'restore_from_deleted_app'
* `az webapp up`: Menambahkan kemampuan untuk menyebarkan aplikasi web Linux dan Windows ke grup sumber daya yang sama
* `az webapp up`: Menambahkan dukungan untuk penyebaran ke Lingkungan App Service
* Memperbaiki #19098: `az webapp deployment slot auto-swap `: Memperbaiki kesalahan AttributeError untuk parameter `--slot --disable`

### <a name="arm"></a>ARM

* `az feature registration`: Menambahkan api pendaftaran fitur az
* `az tag create`: Menambahkan catatan untuk menangani tag yang ada di bantuan
* `az ts create`: Memperbaiki masalah ketika membuat spesifikasi template dengan penyebaran dalam yang merujuk pada template yang sering gagal

### <a name="cdn"></a>CDN

* `az cdn endpoint create`: Memperbaiki kegagalan pembuatan titik akhir dengan `--content-types-to-compress`

### <a name="compute"></a>Compute

* `az ssh vm`: Meningkatkan kesalahan untuk identitas terkelola dan Cloud Shell
* Meningkatkan versi api untuk Mesin Virtual dan VMSS dari `2021-03-01` ke `2021-04-01`
* `az vmss create/update`: Mendukung kebijakan pemulihan spot ke VM scale sets
* Menambahkan contoh baru untuk membuat disk dari galeri gambar bersama
* `az vm image list/list-offers/list-skus/list-publishers/show`: Tambahkan parameter `--edge-zone` baru untuk mendukung kueri gambar di bawah zona tepi
* Memperbaiki masalah yang disebabkan oleh kurangnya `os_type` saat membuat Mesin Virtual dari id galeri bersama
* Memperbarui dokumen galeri gambar bersama
* `az capacity reservation`: Menambahkan perintah baru untuk mengelola reservasi kapasitas
* `az capacity reservation group`: Menambahkan perintah baru untuk mengelola grup reservasi kapasitas
* `az vm create/update`: Menambahkan parameter baru `--capacity-reservation-group` untuk mendukung asosiasi ke reservasi kapasitas
* `az vmss create/update`: Menambahkan parameter baru `--capacity-reservation-group` untuk mendukung asosiasi ke reservasi kapasitas
* `az vmss create`: Mendukung pembuatan VMSS dari gambar galeri bersama

### <a name="iot"></a>IoT

* `az iot hub/dps certificate update/create`: Menambahkan argumen `--verified` untuk menandai sertifikat sebagai terverifikasi tanpa alur bukti kepemilikan
* `az iot hub create/update`: Menambahkan argumen `--disable-local-auth`, `--disable-device-sas`, dan `--disable-module-sas` untuk mengonfigurasi metode autentikasi kunci SAS yang diterima.

### <a name="key-vault"></a>Key Vault

* `az keyvault private-endpoint-connection list`: Mendukung daftar koneksi titik akhir privat mhsm
* `az keyvault set-policy`: `--key-permissions` menambahkan opsi baru `release`

### <a name="network"></a>Jaringan

* Memperbaiki kesalahan contoh pembuatan aturan NSG
* Menambahkan grup perintah baru `az network custom-ip prefix`.
* `az network public-ip`: Menambahkan parameter `--ip-address`.
* `az network public-ip prefix create`: Menambahkan parameter `--custom-ip-prefix-name`.
* `az network dns record-set {record-type} add-record`: Mendukung idempotent
* PrivateLink mendukung `Microsoft.Purview/accounts` 1-7-2021
* `az network bastion ssh`: menghubungkan ke mesin Virtual melalui ssh menggunakan Bastion Tunneling.
* `az network bastion rdp`: menghubungkan ke mesin Virtual melalui RDP asli menggunakan Bastion Tunneling.
* `az network bastion tunnel`: menghubungkan ke mesin Virtual menggunakan Bastion Tunneling.

### <a name="packaging"></a>Pengemasan

* Menggunakan Python 3.9 dalam formula Homebrew
* Saat diinstal dengan RPM, jalankan python3.6 jika tersedia
* Menambahkan dukungan Ubuntu 21.04 Hirsute Hippo
* Menambahkan dukungan Debian 11 Bullseye
* Menghapus dukungan Ubuntu 20.10 Groovy Gorilla

### <a name="powerbi"></a>PowerBI

* Menambahkan penyedia tautan pribadi Microsoft.PowerBI/privateLinkServicesForPowerBI

### <a name="rdbms"></a>RDBMS

* [BREAKING CHANGE] `az postgres flexible-server migration`: Mengganti nama `--migration-id` menjadi `--migration-name`
* [BREAKING CHANGE] `az mysql flexible-server create/update`: parameter `--high-availability` yang tersedia diubah dari 'Enabled' menjadi 'ZoneRedundant' dan 'SameZone' .
* Memperbaiki masalah pembaruan jendela pemeliharaan dengan MySQL dan Mengubah parameter hidupkan ulang menjadi tidak peka huruf besar-kecil
* `az mysql flexible-server restore` memungkinkan perubahan opsi jaringan dari jaringan pribadi ke jaringan publik dan sebaliknya.
* `az mysql flexible-server replica create`: Menambahkan parameter `zone`.

### <a name="role"></a>Peran

* `az role assignment create`: Mendukung `ForeignGroup` untuk `--assignee-principal-type`
* `az role assignment create`: Jangan aktifkan Graph API jika `--assignee-principal-type` disediakan

### <a name="sql"></a>SQL

* `az sql mi update`: Menambahkan --subnet dan --parameter vnet-name untuk mendukung SLO pembaruan lintas subnet
* Memperbaiki perubahan nama enum di SDK Python track2

### <a name="storage"></a>Penyimpanan

* Memperbaiki #10765: Memperbaiki pesan kesalahan saat kunci akun salah padding

### <a name="synapse"></a>Synapse

* [BREAKING CHANGE] Mengganti nama `az synapse workspace key update` menjadi `az synapse workspace key activate` dan menghapus `--is-active`
* Mengoptimalkan pengiriman argumen pekerjaan spark
* `az synapse`: Menambahkan fitur titik akhir privat terkelola.
* Kumpulan spark menghapus persyaratan pustaka

## <a name="august-23-2021"></a>23 Agustus 2021

Versi 2.27.2

### <a name="cosmos-db"></a>Cosmos DB

* Perbaikan: `az cosmosdb restore`: Memperbaiki perintah pemulihan untuk akun yang dihapus

## <a name="august-17-2021"></a>17 Agustus 2021

Versi 2.27.1

### <a name="arm"></a>ARM

* Perbaikan: Memperbaiki #19124: `az deployment what-if`: Menangani jenis perubahan yang tidak didukung dan tidak berpengaruh

### <a name="batch"></a>Batch

Meningkatkan bidang data batch ke [azure-batch 11.0.0](https://pypi.org/project/azure-batch/) Meningkatkan bidang pengelolaan batch ke [azure-batch-mgmt 16.0.0](https://pypi.org/project/azure-mgmt-batch/16.0.0/)
`az batch location`: Menambahkan perintah `list-skus` untuk membuat daftar SKU yang tersedia di lokasi `az batch account`: Menambahkan perintah `outbound-endpoints` ke daftar dependensi jaringan keluar

## <a name="august-03-2021"></a>3 Agustus 2021

Versi 2.27.0

### <a name="acr"></a>Azure Container Registry

* [BREAKING CHANGE] `az acr connected-registry install info`: Menambahkan parameter baru yang diperlukan `--parent-protocol`.
* [BREAKING CHANGE] `az acr connected-registry install renew-credentials`: Menambahkan parameter baru yang diperlukan `--parent-protocol`.
* `az acr import`: Mendukung parameter baru `--no-wait`
* Memperbaiki masalah kompatibilitas SDK Python saat memigrasi Track 2
* `az acr build`: Membuat file .dockerignore menyertakan direktori dengan `!`

### <a name="aks"></a>AKS

* `az aks check-acr`: Memperbaiki masalah saat menguraikan versi minor klien tertentu

### <a name="appconfig"></a>Konfigurasi Aplikasi

* [BREAKING CHANGE] `appconfig feature set`: Mengatur nilai parameter `--description` ke string kosong jika tidak ditentukan
* [BREAKING CHANGE] `az appconfig feature`: Mendukung namespacing untuk tanda fitur dan mengubah bidang output
* `az appconfig create`: Menambahkan dukungan tag saat membuat sumber daya

### <a name="app-service"></a>App Service

* `az webapp config set`: Menambahkan dukungan untuk properti VNet Route All.
* `az webapp vnet-integration add`: Mengatur default ke VNet Route All. Memungkinkan integrasi lintas langganan.
* `az appservice ase create`: Mendukung redundansi Eksternal dan Zona ASEv3
* `az webapp hybrid-connection add`: Meningkatkan pesan bantuan/kesalahan dan membuka pemblokiran Linux
* `az webapp config access-restriction remove`: Memperbaiki masalah #18947 menghapus aturan titik akhir layanan
* : Memperbaiki #17424: `az appservice plan show`: Memberikan status keluar yang benar

### <a name="arm"></a>ARM

* `az what-if`: Memperbaiki pemformatan output
* `az bicep uninstall`: Menambahkan perintah baru untuk mencopot pemasangan bicep
* `az bicep build`: Memperbaiki masalah saat menjalankan dengan --stdout tidak mencetak output apa pun
* `az provider register`: Menambahkan info `--accept-term` yang tidak digunakan lagi
* `az lock create/delete`: Menambahkan contoh untuk mengoperasikan berbagai tingkat kunci
* `az deployment group/sub/mg/tenant create`: Menambahkan parameter --what-if untuk menjalankan What-If dengan perintah buat penyebaran.
* `az deployment group/sub/mg/tenant create`: Menambahkan parameter --proceed-if-no-change untuk melewati konfirmasi saat --confirm-with-what-if diatur dan tidak ada perubahan pada hasil What-If.
* Bump api-versi dari 01-10-2020 hingga 01-04-2020
* `az ts create`: Membuat parameter `--template-file` mendukung file bicep
* `az resource create`: Menambahkan contoh untuk membuat ekstensi situs ke aplikasi web
* `az ts export`: Memperbaiki masalah yang gagal mengekspor spesifikasi template tanpa template tertaut

### <a name="backup"></a>Cadangan

* `az backup vault`: Menambahkan dukungan untuk Kunci yang Dikelola Pelanggan (CMK)
* `az backup restore restore-disks`: Menambahkan penggunaan MSI di Pemulihan Mesin Virtual IaaS

### <a name="cdn"></a>CDN

* `az cdn endpoint rule`: Menambahkan dukungan tindakan OriginGroupOverride

### <a name="compute"></a>Compute

* `az sig image-version create`: Mendukung mencampur disk, snapshot, dan vhd
* `az vmss update`: Meningkatkan versi paket untuk memperbaiki masalah Profil keamanan
* `az vm boot-diagnostics get-boot-log`: Memperbaiki crash saat mendapatkan log diagnostik boot
* `az vm list-skus`: Memperbaiki masalah tidak dapat mengkueri SKU yang dengan sebagian zona tersedia
* `az vm auto-shutdown`: Memperbaiki masalah yang diperlukan `--webhook` saat `--email` diteruskan
* `az vm create`: Mendukung membuat Mesin Virtual dari gambar galeri bersama
* `az vm secret add`: Menambahkan catatan untuk menggunakan ekstensi Mesin Virtual Azure Key Vault sebagai gantinya di bantuan

### <a name="container"></a>Kontainer

* `az container exec`: Memperbaiki dan meningkatkan pengalaman terminal

### <a name="databoxedge"></a>DataBoxEdge

* Memigrasikan databoxedge ke SDK track2

### <a name="dms"></a>DMS

* `az dms project create/az dms project task create`: Menghapus proyek/tugas MySQL untuk migrasi online karena tidak lagi didukung.

### <a name="iot"></a>IoT

* `az iot hub create/update`: Menambahkan pemeriksaan untuk mencegah parameter identitas unggahan file yang buruk saat hub tidak memiliki identitas
* `az iot hub create/update`: Menambahkan parameter `--fileupload-notification-lock-duration`
* `az iot hub create/update`: Menghentikan parameter `fileupload-storage-container-uri`
* `az iot dps/hub certificate create`: Sertifikat sekarang akan selalu diunggah dalam pengodean base64.

### <a name="key-vault"></a>Key Vault

* [BREAKING CHANGE] Memperbaiki #13752: az keyvault create note idempoten. Membuat keyvault yang ada akan gagal.
* Memperbaiki #6372: output tabel untuk rahasia tidak benar

### <a name="maps"></a>Maps

* `az maps creator create`: Mendukung pembuat peta membuat terkelola
* `az maps creator update`: Mendukung pembaruan pembuat peta yang dikelola
* `az maps creator list`: Mendukung daftar pembuat peta yang dikelola
* `az maps creator show`: Mendukung peritiwa pembuat peta yang dikelola
* `az maps creator delete`: Mendukung pembuat peta, menghapus terkelola

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles volume pool-change`: Memperbarui deskripsi bantuan untuk pool-change

### <a name="network"></a>Jaringan

* `az network application-gateway create`: Menambahkan argumen `--ssl-certificate-name`
* Tautan pribadi menambahkan penyedia Microsoft.ServiceBus/namespaces
* `az network application-gateway waf-policy custom-rule match-condition add`: Menambahkan contoh
* `az network express-route port link update`: Menambahkan argumen `--macsec-sci-state`.
* Tautan pribadi menambahkan penyedia Microsoft.Web/hostingEnvironments
* `az network lb frontend-ip update`: Mendukung lintas penyewa untuk argumen `--gateway-lb`.
* `az network nic ip-config update`: Mendukung lintas penyewa untuk argumen `--gateway-lb`.
* Tautan pribadi menambahkan penyedia Microsoft.StorageSync/storageSyncServices
* Tautan pribadi menambahkan penyedia layanan Microsoft.Media/media
* Tautan pribadi menambahkan penyedia Microsoft.Batch/batchAccounts

### <a name="packaging"></a>Pengemasan

* Menambahkan lisensi ke semua paket Python
* Menambahkan Dukungan Proksi SOCKS

### <a name="policyinsights"></a>PolicyInsights

* Memigrasikan ke melacak SDK 2

### <a name="rdbms"></a>RDBMS

* PostgreSQL, migrasi MySQL ke API GA

### <a name="redis"></a>Redis

* `az redis create\update`: Menambahkan parameter baru `--redis-version`

### <a name="sql"></a>SQL

* Memperbarui Microsoft.Sql ke SDK track2
* `az sql server outbound-firewall-rule create`: Perintah Azure CLI untuk Aturan Firewall Keluar

### <a name="storage"></a>Penyimpanan

* Memperbaiki #18352: `az storage fs file list --exclude-dir` putus dengan `--show-next-marker`
* `az storage fs generate-sas`: Mendukung pembuatan token sas untuk sistem file di akun ADLS Gen2
* `az storage account blob-service-properties`: Mendukung kebijakan pelacakan akses terakhir
* `storage container-rm migrate-vlw`: Mendukung Versi tingkat Worm (VLW)
* `az storage copy` menambahkan opsi baru `--cap-mbps`

### <a name="synapse"></a>Synapse

* `synapse workspace key update`: Memperbaiki masalah yang memperbarui kegagalan kunci ruang kerja karena parameter `--is-active-cmk` hilang
* Kegagalan impor ulang buku catatan

## <a name="july-14-2021"></a>14 Juli 2021

Versi 2.26.1

### <a name="acr"></a>Azure Container Registry

* Perbaikan: `az acr build\connected-registry\pack\run\scope-map`: Memperbaiki bug kompatibilitas yang disebabkan oleh peningkatan versi SDK

### <a name="aks"></a>AKS

* Perbaikan: `az aks create`: Memperbaiki masalah opsi `assign-kubelet-identity` tidak dapat berfungsi

### <a name="storage"></a>Penyimpanan

* Perbaikan: Memperbaiki masalah yang disebabkan oleh peningkatan jwt.
* Perbaikan: `az storage fs directory download`: Memperbaiki masalah dengan `--sas-token` untuk membuat url sas yang valid
* Perbaikan: `az storage blob copy start`: Memperbaiki masalah dalam salinan dari akun yang berbeda

## <a name="july-06-2021"></a>6 Juli 2021

Versi 2.26.0

### <a name="aks"></a>AKS

* Memigrasikan modul ACS untuk melacak SDK 2
* Meningkatkan versi api ke 1-5-2021 untuk modul ACS
* Menambahkan dukungan UltraSSD
* Mendukung penggunaan identitas kubelet kustom
* `az aks get-credentials`: Menambahkan tanda centang untuk variabel lingkungan KUBECONFIG

### <a name="apim"></a>APIM

* Menambahkan parameter versi untuk impor api apim
* Memperbaiki bug peningkatan apim saat menentukan protokol
* `az apim create`: Memperbaiki kegagalan sebenarnya `--enable-managed-identity`

### <a name="app-config"></a>Konfigurasi Aplikasi

* Berhenti menimpa jenis konten referensi KeyVault selama impor

### <a name="app-service"></a>App Service

* [BREAKING CHANGE] `az functionapp create`: Menghapus dukungan EOL Node 8 dan 10
* [BREAKING CHANGE] `az webapp deployment source config`: Menghapus vsts-cd-manager
* [BREAKING CHANGE] `az functionapp deployment source config`: Menghapus vsts-cd-manager
* `az webapp/functionapp config access-restriction add`: Mencegah aturan duplikat menggunakan titik akhir layanan.
* `az webapp/functionapp config access-restriction remove`: Menghapus titik akhir layanan tidak peka huruf besar-kecil
* `az webapp config access-restrictions add`: Melewati validasi jika pengguna tidak memiliki akses untuk mendapatkan daftar tag layanan.
* Menambahkan dukungan untuk Konsumsi Linux dan meningkatkan cara pembuatan nama konten bersama.
* : Memperbaiki masalah saat menambahkan integrasi VNET & koneksi Hibrid pada slot tidak berfungsi
* `az appservice domain create`: Memperbaiki dapatkan perjanjian domain yang benar
* `az webapp deployment github-actions add/remove`: perintah baru

### <a name="appconfiguration"></a>AppConfiguration

* Menambahkan dukungan `disable_local_auth`

### <a name="arm"></a>ARM

* `az provider register`: Membuat parameter `--accept-term` menjadi tidak wajib

### <a name="aro"></a>ARO

* `az aro create`: Menambahkan nilai cidr untuk pod/layanan
* Gagal jika sumber daya tidak ada di hapus

### <a name="azurestack"></a>Azurestack

* Dukungan Azure Stack Hub untuk AKS dan ACR telah ditambahkan di profil hibrid 01-09-2020

### <a name="backup"></a>Cadangan

* `az backup container`: Memperbaiki pendaftaran kontainer Perbaikan pendaftaran kontainer beban kerja, SDK ditingkatkan ke 0.12.0, Memperbaiki dan menjalankan ulang pengujian
* Menambahkan Dukungan Arsip untuk Azure CLI

### <a name="billing"></a>Billing

* Memigrasikan penagihan ke SDK track2

### <a name="cognitive-services"></a>Cognitive Services

* `az cognitiveservices account`: Menambahkan perintah penghapusan menyeluruh list-deleted, show-deleted, recover

### <a name="compute"></a>Compute

* `az sig create/update`: Menambahkan --izin untuk menentukan izin berbagi galeri.
* `az sig share`: Mengelola profil berbagi galeri.
* `az sig list-shared`: Mencantumkan galeri bersama menurut id langganan atau id penyewa.
* `az sig show-shared`: Mendapatkan galeri bersama.
* `az sig image-definition list-shared`: Mencantumkan galeri bersama menurut id langganan atau id penyewa.
* `az sig image-definition show-shared`: Mendapatkan gambar galeri bersama.
* `az sig image-version list-shared`: Mencantumkan galeri bersama menurut id langganan atau id penyewa.
* `az sig image-version show-shared`: Mendapatkan versi gambar galeri bersama.
* `az vmss create`: Mendukung NetworkApiVersion untuk Vmss dengan OrchestraionMode == Fleksibel
* Membuat sumber daya dependen dari zona tepi dukungan VM/VMSS
* Memperbarui dari CoreOS ke Flatcar
* Menambahkan petunjuk untuk menyarankan pengguna menggunakan IP publik standar saat membuat Mesin Virtual

### <a name="container-registry"></a>Container Registry

* Memigrasikan ke SDK track2

### <a name="cosmos-db"></a>Cosmos DB

* Menambahkan perintah pemulihan point-in-time ke cabang stabil.
* Menambahkan dukungan untuk memilih jenis skema penyimpanan analitik Cosmos DB

### <a name="hdinsight"></a>HDInsight

* `az hdinsight create`: Menghapus pemberitahuan perubahan gangguan yang masuk untuk parameter `--workernode-size` dan `--headnode-size`.
* Menambahkan tiga cmdlet baru untuk mendukung fitur pemantauan Azure baru:

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`: Parameter opsional ditambahkan bernama --administrators
* `az netappfiles pool create`: Parameter opsional ditambahkan --cool-access
* `az netappfiles volume create`: Parameter opsional ditambahkan bernama --chown-mode, --cool-access, --coolness-period, --coolness-period
* `az netappfiles volume backup restore-status`: Perintah ditambahkan untuk melihat status pemulihan cadangan

### <a name="network"></a>Jaringan

* `az network routeserver create`: Menambahkan argumen `--public-ip-address`.

### <a name="rdbms"></a>RDBMS

* Menambahkan parameter autogrow untuk MySQL dan menambahkan nama database ke output json saat dibuat

### <a name="resource"></a>Sumber daya

* Enumerasi Persetujuan/Izin S2S pihak ketiga

### <a name="security"></a>Keamanan

* Menghapus pratinjau dari modul keamanan

### <a name="sql"></a>SQL

* Bump versi sdk
* Perbaikan untuk server yang dibuat di SQL 0.28
* `az sql db ledger-digest-uploads`: Mendukung SQL Ledger
* Memperbaiki IdentityType untuk UMI
* `az sql db str-policy set/show`: Menambahkan Atur dan Tampilkan ShortTermRetentionPolicy

### <a name="storage"></a>Penyimpanan

* Dukungan GA mengamankan SMB
* `az storage account create`: Mendukung `--enable-nfs-v3` untuk mengatur protokol NFS 3.0
* Dukung penghapusan sementara kontainer

## <a name="june-15-2021"></a>15 Juni 2021

Versi 2.25.0

### <a name="acr"></a>Azure Container Registry

* `az acr connected-registry`: Perbaikan bug kecil

### <a name="app-service"></a>App Service

* `az webapp deployment source config-local-git`: Memperbaiki untuk mengatur SiteConfig

### <a name="arm"></a>ARM

* `az resource tag`: Memperbaiki masalah penandaan sumber daya dengan jenis sumber daya `Microsoft.Network/publicIPAddresses`
* `az policy assignment non-compliance-message`: Grup perintah baru untuk pesan ketidakpatuhan penetapan kebijakan
* `az policy assignment update`: Perintah baru untuk memperbarui sebagian penetapan kebijakan yang ada

### <a name="backup"></a>Cadangan

* Memigrasikan cadangan ke SDK track2

### <a name="compute"></a>Compute

* Meningkatkan versi api untuk Mesin Virtual dan VMSS dari '2020-12-01' ke '1-3-2020'
* `az vm create`: Mendukung opsi hapus untuk NIC dan Disk untuk Mesin Virtual di Azure CLI
* Mendukung user_data untuk Mesin Virtual dan VM Scale Sets

### <a name="container"></a>Kontainer

* `az container exec`: Mendekodekan byte yang diterima sebagai string utf-8

### <a name="eventgrid"></a>EventGrid

* Memigrasikan SDK track2

### <a name="hdinsight"></a>HDInsight

* Memigrasikan ke SDK Python track2 7.0.0

### <a name="iot-hub"></a>Iot Hub

* Memperbaiki masalah ARM identitas yang ditetapkan pengguna saat dihapus

### <a name="key-vault"></a>Key Vault

* Memperbaiki #11871: AKV10032: Kesalahan penerbit tidak valid untuk operasi di penyewa/langganan nondefault
* `az keyvault set-policy/delete-policy`: Mendukung --application-id
* `az keyvault recover`: Mendukung MHSM
* `az keyvault private-link-resource list`: Mendukung MHSM
* `az keyvault private-endpoint-connection`: Mendukung MHSM

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles volume backup status`: Perintah ditambahkan untuk mendapatkan status cadangan untuk volume.
* `az netappfiles volume update`: Parameter opsional ditambahkan bernama `--snapshot-policy-id` o menetapkan kebijakan snapshot ke volume.
* `az netappfiles volume backup create`: Parameter opsional ditambahkan bernama `--use-existing-snapshot` untuk secara manual mencadangkan snapshot yang sudah ada.
* `az netappfiles volume backup update`: Parameter opsional ditambahkan bernama `--use-existing-snapshot` untuk secara manual mencadangkan snapshot yang sudah ada. Label parameter opsional juga ditambahkan untuk menambahkan label ke cadangan.

### <a name="network"></a>Jaringan

* Mendukung penyedia `Microsoft.Sql/servers` di Tautan pribadi
* `az network private-link-resource list`: Mendukung `--type microsoft.keyvault/managedHSMs`
* `az network private-endpoint-connection`: Mendukung `--type microsoft.keyvault/managedHSMs`

### <a name="rdbms"></a>RDBMS

* Menambahkan perintah untuk tindakan Github
* `az postgres flexible-server migration`: Menambahkan fitur yang dihadapi pelanggan untuk memigrasikan server postgres db dari platform Sterling ke Meru
* Parameter zona DNS pribadi ditambahkan untuk perintah pemulihan, validator ketersediaan tinggi
* Mengubah lokasi default server (masalah dilaporkan)

### <a name="role"></a>Peran

* [BREAKING CHANGE] `az ad sp create-for-rbac`: `--name` sekarang hanya digunakan sebagai `displayName` aplikasi. Hal ini tidak digunakan untuk membuat `identifierUris` lagi. `name` dalam output sekarang sama dengan `appID` (`servicePrincipalNames`) dan tidak digunakan lagi.

### <a name="signalr"></a>SignalR

* `az signalr identity`: Menambahkan perintah terkait identitas terkelola
* `az signalr cors update`: Menambahkan perintah pembaruan untuk cors

### <a name="storage"></a>Penyimpanan

* `az storage blob copy start`: Mendukung --tier dan --rehydrate-priority
* GA merilis berbagi file penyimpanan NFS dan SMB multi saluran
* [BREAKING CHANGE] `az storage account create`: Menghapus opsi `StorageFileDataSmbShareOwner` untuk --default-share-permission
* `az storage blob list`: --nilai parameter pembatas sekarang akan dihormati

### <a name="synapse"></a>Synapse

* Memperbarui ke AZ Synapse mgmt 2.0.0
* Konversi konfigurasi spark, yang menyebabkan kegagalan

### <a name="webapp"></a>Webapp

* Menambahkan ke teks bantuan param `az webapp deploy`

## <a name="june-02-2021"></a>2 Juni 2021

Versi 2.24.2

### <a name="container"></a>Kontainer

* Perbaikan: Memperbaiki #18276: `az container create` gagal dengan `AttributeError: 'ResourcesOperations' object has no attribute 'create_or_update'`

## <a name="june-01-2021"></a>1 Juni 2021

Versi 2.24.1

### <a name="app-service"></a>App Service

* Perbaikan: Memperbaiki # 18266 - perintah webapp config appsettings set menyebabkan semua nilai menjadi default ke "false"

### <a name="arm"></a>ARM
* Perbaikan: Memperbaiki masalah deserialisasi di formatter What-If dari template ARM

### <a name="compute"></a>Compute
* Perbaikan: Memperbaiki masalah permintaan buruk saat membuat VMSS di Azure Stack

### <a name="iot"></a>IoT
* Perbaikan: Memperbaiki masalah menghapus identitas yang ditetapkan pengguna terakhir dari IoT Hub

## <a name="may-25-2021"></a>25 Mei 2021

Versi 2.24.0

### <a name="aks"></a>AKS

* `az aks check-acr`: Menambahkan nodelector linux untuk menghindari pod "canipull" dijadwalkan pada node windows
* Pembaruan SDK
* az aks create dan update azure-rbac
* Menambahkan run-command cli

### <a name="app-config"></a>Konfigurasi Aplikasi

* Mengizinkan mengimpor nilai kunci dengan karakter unicode dari file

### <a name="app-service"></a>App Service

* [BREAKING CHANGE] `az webapp list-runtimes`: Menambahkan dukungan Dotnet6 dan memperbarui runtime
* `webapp log tail`: Memperbaiki #17987: panggilan logging.warning dengan argumen 'akhir' yang tidak valid
* Memperbaiki # 16838- perintah az cli update app setting selalu membuat slotsetting menjadi true
* `az appservice`: Menambahkan fungsi untuk mengambil token akses pribadi github pengguna
* az staticwebapp appsettings set issue #17792
* Memperbaiki #18033: az staticwebapp appsettings set dari app_settings param posisi yang hilang
* Memperbaiki masalah dengan tanda tangan API yang berubah dengan pembaruan Track2
* Memperbaiki mendapatkan klien manajemen sumber daya dengan benar
* Menambahkan cara interaktif mendapatkan token untuk staticwebapp
* Memperbaiki masalah saat penetapan dan penghapusan identitas akan gagal dengan panggilan ke NoneType

### <a name="arm"></a>ARM

* Memigrasikan sumber daya ke SDK track2
* `az ts`: Menambahkan dukungan file UiFormDefinition ke TemplateSpecs untuk GA (05/04)

### <a name="aro"></a>ARO

* Menambahkan rotasi kredensial kluster

### <a name="compute"></a>Compute

* `az sshkey create`: Menyimpan kunci pribadi ke sistem file lokal

### <a name="cosmos-db"></a>Cosmos DB

* Membuat dan mengelola Definisi Peran dan Penetapan Peran untuk menerapkan RBAC data plane pada akun Cosmos DB SQL

### <a name="devtestlabs"></a>DevTestLab

* `az labs create environment`: Memperbaiki kesalahan saat membuat lingkungan dari template ARM

### <a name="hdinsight"></a>HDInsight

* [BREAKING CHANGE] `az hdinsight create`: Menggunakan mendapatkan api sku default untuk mengatur ukuran workernode dan headnode jika pelanggan tidak menyediakannya.

### <a name="iot"></a>IoT

* `az iot hub create`: Mendukung penetapan identitas dan penetapan peran ke identitas yang dikelola sistem.
* `az iot hub update`: Parameter baru `--file-upload-storage-identity` untuk memungkinkan pengunggahan file yang diautentikasi dengan identitas terkelola.
* `az iot hub identity assign`: Perintah baru untuk menetapkan identitas terkelola yang ditetapkan pengguna/sistem ke IoT Hub.
* `az iot hub identity show`: Perintah baru untuk menampilkan properti identitas dari IoT Hub.
* `az iot hub identity show`: Perintah baru untuk memperbarui jenis identitas IoT Hub.
* `az iot hub identity remove`: Perintah baru untuk menghapus identitas terkelola yang ditetapkan pengguna/sistem dari IoT Hub.
* `az iot hub routing-endpoint create`: Parameter `--identity` baru memungkinkan pemilihan identitas yang ditetapkan pengguna/sistem untuk merutekan titik akhir.
* `az iot hub route create`: Jenis sumber perutean baru `DeviceConnectionStateEvents`

### <a name="kusto"></a>Kusto

* Memperbarui ringkasan panjang grup perintah

### <a name="network"></a>Jaringan

* Bump versi api dari '2020-11-01' hingga '2020-02-01'
* Grup perintah baru `az network lb address-pool tunnel-interface`
* `az network lb frontend-ip update`: Parameter baru `--gateway-lb`
* `az network nic ip-config update`: Parameter baru `--gateway-lb`
* `az network rule create/update`: Parameter baru `--backend-pools-name`
* `az network vnet-gateway create`: Menambahkan parameter baru `--nat-rule`
* Menambahkan grup cmd baru `az network vnet-gateway nat-rule`
* `az network vpn-conncetion create`: Menambahkan parameter baru `--ingress-nat-rule` dan `--egress-nat-rule`
* `az network vnet create`: Menambahkan parameter baru `--flowtimeout`

### <a name="packaging"></a>Pengemasan

* Mendukung Python 3.9

### <a name="rdbms"></a>RDBMS

* Mengubah logika IOPS untuk MySQL
* Mencegah migrasi track2 zona DNS pribadi yang melanggar modul rdbms

### <a name="service-fabric"></a>Service Fabric

* [BREAKING CHANGE] `az sf cluster certificate`: Menghapus semua perintah di bawah grup ini. Harap ikuti petunjuk di [Menambahkan sertifikat sekunder menggunakan Azure Resource Manager](/azure/service-fabric/service-fabric-cluster-security-update-certs-azure#add-a-secondary-certificate-using-azure-resource-manager) untuk menambah/menghapus sertifikat kluster.
* [BREAKING CHANGE] `az sf managed-service update`: Menghapus parameter yang tidak digunakan lagi --drop-source-replica-on-move.
* [BREAKING CHANGE] `az sf managed-service create`: Menghapus parameter yang tidak digunakan lagi --service-dns-name, --drop-source-replica-on-move dan -instance-close-delay-duration.
* [BREAKING CHANGE] `az sf cluster`: Mengganti nama parameter --vault-resource-group menjadi --vault-rg.
* `az sf managed-cluster and sf managed-node-type`: Mengatur grup sebagai bukan pratinjau
* Memperbarui paket Azure-mgmt-servicefabricmanagedclusters ke versi terbaru 1.0.0 yang menggunakan versi api GA 1-5-2021.
* `az sf managed-cluster create`: Menambahkan parameter --upgrade-mode, --upgrade-cadence dan --code-version.
* `az sf managed-node-type`: Menambahkan parameter --data-disk-type, --is-stateless dan --multiple-placement-groups.

### <a name="sql"></a>SQL

* `az sql server create`: Menambahkan spasi untuk memisahkan kata-kata yang digabungkan dalam pesan bantuan dari argumen --assign-identity.
* `az sql server update`: Menambahkan spasi untuk memisahkan kata-kata yang digabungkan dalam pesan bantuan dari argumen --assign_identity.

### <a name="storage"></a>Penyimpanan

* [BREAKING CHANGE] `az storage share-rm delete`: Melaporkan kesalahan saat ada snapshot untuk berbagi file target dan menambahkan `--include` untuk menentukan penghapusan target berbagi file dan snapshotnya
* `az storage blob generate-sas`: Menambahkan spasi untuk memisahkan kata-kata yang digabungkan dalam pesan bantuan argumen --cache-control, --content-disposition, --content-encoding, --content-language dan --content-type.
* `az storage blob url`: Menambahkan spasi untuk memisahkan kata-kata yang digabungkan dalam pesan bantuan dari argumen --snapshot.
* `az storage container generate-sas`: Menambahkan spasi untuk memisahkan kata-kata yang digabungkan dalam pesan bantuan argumen --cache-control, --content-disposition, --content-encoding, --content-language dan --content-type.
* Meningkatkan versi API penyimpanan ke 1-4-2021
* Mendukung izin berbagi default
* Mendukung replikasi objek penyewa silang
* Inventaris blob GA
* `az storage share-rm list`: Daftar dukungan dengan snapshot.

## <a name="may-06-2021"></a>6 Mei 2021

Versi 2.23.0

### <a name="acr"></a>Azure Container Registry

* `az acr check-health`: Menambahkan dukungan untuk memverifikasi perutean dns ke titik akhir privat
* Memperbaiki #17618: Memperbarui penambahan/pembaruan penanganan kredensial untuk tugas yang dibuat menggunakan --auth-mode

### <a name="aks"></a>AKS

* `az aks update`: Menambahkan `--windows-admin-password` untuk mendukung pembaruan kata sandi Windows
* `az aks update`: Mendukung pembaruan dari kluster SPN ke kluster MSI.
* `az aks create`: Menambahkan parameter `--enable-encryption-at-host`

### <a name="app-service"></a>App Service

* [BREAKING CHANGE] Memperbarui SDK situs web ke versi terbaru (Azure-mgmt-web==2.0.0) & Mengadopsi SDK track2
* [BREAKING CHANGE] Mengganti nama `az staticwebapp browse` menjadi `az staticwebapp show`
* Menambahkan opsi sku untuk `az staticwebapp create --sku`
* Menambahkan perintah `az staticwebapp update`
* `az webapp/functionapp config access-restriction add/remove`: Mendukung Tag Layanan, header Http, dan aturan multi-sumber.

### <a name="arm"></a>ARM

* `az bicep`: Mengganti API datetime yang tidak tersedia di Python 3.6
* `az deployment group create`: Memperbaiki masalah kompatibilitas versi api untuk parameter `--template-specs`

### <a name="backup"></a>Cadangan

* `az backup vault create`: Menambahkan tag sebagai argumen opsional
* Jadikan AFS mengkonfigurasi idempoten aliran cadangan

### <a name="cdn"></a>CDN

* `az cdn endpoint rule add`: Memperbaiki pembuatan aturan pengiriman untuk SKU non-Microsoft

### <a name="compute"></a>Compute

* Lokasi yang diperluas untuk Compute RP
* `az sig image-version create`: Mendukung pembuatan dari VHD
* `az vm create --count`: Mendukung konfigurasi vnet dan subnet
* `az vmss extension upgrade`: Memperbaiki bug
* Menambahkan pesan galat untuk `vm identity assign`
* Disk yang dikelola penyimpanan zona-redundan (ZRS)
* `az disk create`: Peluncuran tepercaya
* `az disk create`: Hibernasi
* Memperbaiki masalah kompatibilitas versi API lama
* `az sig image version create`: Mendukung VHD disk data

### <a name="feedback-reference"></a>Referensi umpan balik

* Jangan mengecilkan badan masalah umpan balik

### <a name="functionapp"></a>FunctionApp

* Memperbaiki masalah dengan penerapan zip di mana waktu lokal disediakan tetapi UTC diharapkan
* Memperbarui tumpukan api json untuk menambahkan PowerShell di Linux di Functions

### <a name="hdinsight"></a>HDInsight

* Menambahkan BREAKING CHANGE Masuk untuk menghapus nilai default `--workernode-size` dan `--headnode-size`

### <a name="key-vault"></a>Key Vault

* [BREAKING CHANGE] Mendukung fitur soft-delete untuk managed-HSM. `keyvault delete --hsm-name` akan melakukan penghapusan sementara pada MHSM.

### <a name="marketplace-ordering"></a>Pemesanan Marketplace

* Grup perintah baru `az term` untuk menerima/menampilkan persyaratan

### <a name="misc"></a>Lain-lain

* Tentukan tema untuk Cloud Shell

### <a name="monitor"></a>Monitor

* Perintah baru `az monitor metrics list-namespaces`

### <a name="network"></a>Jaringan

* [BREAKING CHANGE] az network dns record-set a show: Property `arecords` di output akan diubah menjadi `aRecords`.
* Perintah baru `az network express-route list-route-tables-summary`.
* Perintah baru `az network express-route peering get-stats`.
* Perintah baru `az network express-route peering connection list`.
* `az network lb create`: Menambahkan parameter baru `--edge-zone`
* `az network nic create`: Menambahkan parameter baru `--edge-zone`
* `az network private-endpoint create`: Menambahkan parameter baru `--edge-zone`
* `az network private-link-service create`: Menambahkan parameter baru `--edge-zone`
* `az network public-ip create`: Menambahkan parameter baru `--edge-zone`
* `az network public-ip prefix create`: Menambahkan parameter baru `--edge-zone`
* `az network vnet create`: Menambahkan parameter baru `--edge-zone`
* Perintah Baru `az network lb list-nic`
* `az network application-gateway show-backend-health`: mendukung argumen operasi penyelidikan.
* `az network vpn-connection list`: Parameter dukungan `--vnet-gateway`.
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
* `az network private-link-resource list`: dukung lebih banyak penyedia untuk `--type`

### <a name="packaging"></a>Pengemasan

* Bump python ke `3.8.9` di gambar docker
* Bump python yang dibundel ke `3.8.9` di MSI.

### <a name="rdbms"></a>RDBMS
* [BREAKING CHANGE] `az mysql flexible-server create`: `--storage-size` nilai default diubah dari 10 menjadi 32.
* `az postgres flexible-server create`: Menambahkan parameter `--private-dns-zone` untuk membuat server dengan akses pribadi.

### <a name="role"></a>Peran

* `az role assignment create/update`: Selesai otomatis `assignee_principal_type`

### <a name="sql"></a>SQL

* `az sql db create`: Menambahkan argumen --ha-replicas
* `az sql db replica create`: Menambahkan argumen --ha-replicas
* Izinkan nama kebijakan mw pendek untuk mi

### <a name="sql-vm"></a>SQL VM

* Jadikan SqlServerLicenseType sebagai opsional

### <a name="storage"></a>Penyimpanan

* Memperbaiki #16272 & #16853: Memperbaiki pesan kesalahan
* `az storage account create`: Menambahkan dukungan zona tepi
* Mendukung identitas yang ditetapkan pengguna untuk akun penyimpanan
* `az storage account create/update`: Mendukung kebijakan sas&kunci

### <a name="synapse"></a>Synapse

* `az synapse notebook create`: Membuat buku catatan

## <a name="april-19-2021"></a>19 April 2021

Versi 2.22.1

### <a name="arm"></a>ARM

* Perbaikan: Memperbaiki masalah bicep build rusak di Python 3.6

### <a name="key-vault"></a>Key Vault

* Perbaikan: GA untuk perintah dan parameter ralated-HSM terkelola

## <a name="april-13-2021"></a>13 April 2021

Versi 2.22.0

### <a name="acr"></a>Azure Container Registry

* [BREAKING CHANGE] `az acr connected-registry install info`: Mengganti kunci ACR_REGISTRY_NAME, ACR_SYNC_TOKEN_NAME, ACR_SYNC_TOKEN_PASSWORD, ACR_PARENT_GATEWAY_ENDPOINT, dan ACR_PARENT_PROTOCOL dengan kunci string baru yang terhubung, ACR_REGISTRY_CONNECTION_STRING.
* [BREAKING CHANGE] `az acr connected-registry install renew-credentials`: Mengganti kunci ACR_REGISTRY_NAME, ACR_SYNC_TOKEN_NAME, ACR_SYNC_TOKEN_PASSWORD, ACR_PARENT_GATEWAY_ENDPOINT, dan ACR_PARENT_PROTOCOL dengan kunci string baru yang terhubung, ACR_REGISTRY_CONNECTION_STRING.
* `az acr connected-registry create`: Verifikasi sebelum pembuatan token dan peta cakupan sinkronisasi bahwa semua ancestor aktif.
* `az acr connected-registry create`: Menambahkan repositori dan izin gateway yang diperlukan untuk pembuatan ke semua leluhur dari registri baru yang terhubung jika diperlukan sebelum pembuatan registri yang terhubung.
* `az acr connected-registry delete`: Menghapus izin gateway sumber daya yang dihapus dari semua peta cakupan sinkronisasi leluhurnya.
* `az acr connected-registry repo`: Perintah baru untuk menambahkan izin repositori ke registri yang terhubung dan semua peta cakupan sinkronisasi leluhurnya, dan menghapus izin repositori dari registri yang terhubung dan semua peta cakupan sinkronisasi turunannya

### <a name="aks"></a>AKS

* `az aks create`: Menambahkan dukungan untuk fitur `--private-dns-zone` dan `--fqdn-subdomain`

### <a name="app-config"></a>Konfigurasi Aplikasi

* Konfigurasikan lebar garis maksimum untuk parser YAML untuk menghentikan pembungkusan output
* Memperbaiki bug dalam pratinjau cetak perintah pemulihan

### <a name="app-service"></a>App Service

* Memperbaiki #17219: Memperbaiki bug ssl bind
* Menghapus tanda pratinjau untuk Python 3.9 dalam perintah aplikasi fungsi buat
* Perbaikan Bug: Tangani jika hanya satu profil publikasikan yang dikembalikan
* Fix #16203: az webapp log tail mendukung aplikasi web yang berjalan di Linix.

### <a name="arm"></a>ARM

* [BREAKING CHANGE] `az bicep build`: Ubah parameter `--files` menjadi `--file`
* [BREAKING CHANGE] `az bicep decompile`: Ubah parameter `--files` menjadi `--file`
* Memperbaiki #17379: penginstalan otomatis bicep menghasilkan output json yang tidak valid dari penyebaran
* `az bicep build`: Menambahkan parameter `--outdir` untuk menentukan direktori output
* `az bicep build`: Menambahkan parameter `--outfile` untuk menentukan jalur file output
* Memperbaiki masalah saat memeriksa pemutakhiran versi untuk Bicep CLI menimbulkan pengecualian jika batas kecepatan API GitHub tercapai
* `az policy exemption`: Menambahkan perintah baru untuk mendukung pengecualian kebijakan

### <a name="backup"></a>Cadangan

* Memperbaiki #14776: Memperbaiki `--force` fungsionalitas parameter untuk perintah `az backup vault delete`
* Memperbaiki cadangan sesuai permintaan
* `az backup protectable-item list`: Menambahkan parameter opsional `--backup-management-type`
* Memperbaiki pembuatan kebijakan dengan rgNamePrefix dan rgNameSuffix
* `az backup protectable-item list`: Menambahkan `--server-name` sebagai argumen opsional

### <a name="compute"></a>Compute

* `az ssh vm`: Mendukung Mesin Virtual SSH dengan Service Principal
* Menambahkan opsi Peningkatan Bergulir VMSS
* Perintah baru: `vm install-patches`
* Kumpulan enkripsi disk: Menambahkan `--enable-auto-key-rotation`

### <a name="container"></a>Kontainer

* Memperbaiki #16499: `az container create`: Memperbaiki penanganan nilai pengembalian dari network_profiles.create_or_update

### <a name="cosmos-db"></a>Cosmos DB

* Dukungan untuk identitas layanan terkelola & identitas default

### <a name="eventgrid"></a>EventGrid

* `az eventgrid system-topic create/update`: Menambahkan Dukungan MSI
* `az eventgrid [partner topic | system-topic] event-subscription`: Menambahkan dukungan untuk StorageQueueMessageTTL, AdvancedFilters, EnableAdvancedFilteringOnArrays
* `az eventgrid [partner topic | system-topic] event-subscription`: Menambahkan dukungan untuk atribut pengiriman
* `az eventgrid topic create`: Menambahkan dukungan untuk membuat topik azure atau azurearc

### <a name="interactive"></a>Interaktif

* Memperbaiki #16931: Memperbaiki `KeyError` di `az interactive --update`

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`: Parameter opsional ditambahkan bernama allow-local-ldap-users
* `az netappfiles volume create`: Parameter opsional ditambahkan bernama ldap-enabled
* `az netappfiles volume backup status show`: Operasi ditambahkan
* Memperbarui tes cadangan

### <a name="network"></a>Jaringan

* `az network vnet-gateway`: `--vpn-auth-type` izinkan multi nilai

### <a name="packaging"></a>Pengemasan

* [BREAKING CHANGE] RPM terpasang az sekarang menggunakan `python3` alih-alih hard-code `/usr/bin/python3`.

### <a name="rdbms"></a>RDBMS

* Izinkan akses pribadi server DB dari langganan yang berbeda
* Ubah pembuatan server dengan jaringan pribadi, perbaiki bug waktu pemulihan

### <a name="search"></a>Cari

* `az search service create`: Menambahkan opsi async (--no-wait).
* `az search service update`: Menambahkan opsi async (--no-wait).
* `az search shared-private-link-resource create`: Menambahkan opsi async (--no-wait).
* `az search shared-private-link-resource update`: Menambahkan opsi async (--no-wait).

### <a name="service-fabric"></a>Service Fabric

* Menambahkan perintah cli aplikasi terkelola

### <a name="storage"></a>Penyimpanan

* `az storage fs directory upload/download`: Mendukung unggah & unduh direktori sistem file adls gen2
* `az storage fs file list`: Mendukung --show-next-marker
* `az storage share-rm`: Mendukung snapshot membuat/menampilkan/menghapus

### <a name="synapse"></a>Synapse

* [BREAKING CHANGE] `az synapse role assignment create`: Nama peran di versi lama tidak diizinkan, Sql Admin, Apache Spark Admin, Admin Ruang kerja
* [BREAKING CHANGE] `az synapse role assignment create`: Ketika argumen --assignee tidak dapat menentukan objek utama secara unik, perintah akan memunculkan kesalahan alih-alih menambahkan penetapan peran untuk objek utama yang tidak pasti.
* `az synapse role scope list`: Cantumkan semua cakupan yang didukung sinapsis.
* `az synapse role assignment create/list/delete`: Menambahkan argumen --scope/--item-type/--item untuk mendukung pengelolaan penetapan peran berdasarkan cakupan.
* `az synapse role assignment create/list/delete`: Menambahkan argumen --assignee-object-id, ini akan melewati Graph API dan secara unik menentukan objek utama alih-alih mendeduksi objek utama menggunakan argumen --assignee.

## <a name="march-23-2021"></a>23 Maret 2021

Versi 2.21.0

### <a name="acr"></a>Azure Container Registry

* Keluarkan jejak di `az acr login` untuk mendiagnosis sendiri potensi latensi perintah docker
* Memperbaiki #17172: Saat menjalankan pemeriksaan kesehatan di belakang proksi perusahaan
* `acr update`: Mendukung tarikan anonim
* Memperbaiki # 16700: Gunakan api "ada" untuk memeriksa keberadaan blob penyimpanan

### <a name="aks"></a>AKS

* `aks update`: Menambahkan `--no-uptime-sla`
* Memperbaiki kesalahan identitas penetapan lintas-sub dan lampirkan kesalahan acr
* Menambahkan dukungan untuk ID awalan IP publik node

### <a name="apim"></a>APIM

* [BREAKING CHANGE] `apim backup`: `--storage-account-container` tidak mendukung multi-nilai.
* [BREAKING CHANGE] `apim restore`: `--storage-account-container` tidak mendukung multi-nilai.

### <a name="app-service"></a>App Service

* [BREAKING CHANGE] Memperbaiki #16087: `az webapp config ssl create`: mengatur parameter `--name` sesuai kebutuhan.
* Memperbaiki #17053: `az webapp show` menampilkan nilai nol untuk properti SiteConfig
* Memperbaiki #17207: `az webapp log config`: 'level' ke verbose selalu default

### <a name="arm"></a>ARM

* `az bicep build`: memperbaiki masalah di mana peringatan build tidak ditampilkan

### <a name="backup"></a>Cadangan

* Menambahkan `id_part` untuk nama sub-sumber daya untuk diperbaiki `--ids`
* Memperbaiki #17094: Membuat rangkaian pengujian terpisah untuk pengujian CRR
* `az backup protection check-vm`: Menambahkan `--vm` dan `--resource-group` sebagai parameter opsional

### <a name="cache"></a>Cache

* GA `az cache`

### <a name="cdn"></a>CDN

* `az afd rule create`: Memperbaiki `--help` pesan

### <a name="compute"></a>Compute

* Memperbaiki bug pembaruan pengguna Windows vm
* Memperbaiki #16585: `az vmss deallocate`: `--instance-ids` gagal
* `az vm create`: Parameter baru `--platform-fault-domain` dalam mode FLEX VMSS
* `az vm create`: `--patch-mode` untuk Mesin Virtual Linux
* `az ssh vm`: Luncurkan browser secara otomatis saat mendapatkan sertifikat gagal
* `az vm create`: Parameter baru `--count`
* `az vm create`: Peluncuran Tepercaya
* Memperbaiki #16037: az vm open-port menerima daftar port

### <a name="extension"></a>Extensi

* Menambahkan pesan yang dapat ditindaklanjuti ketika ekstensi tidak kompatibel dengan inti CLI

### <a name="key-vault"></a>Key Vault

* `az keyvault role definition list`: Mendukung `--custom-role-only` untuk mencantumkan definisi peran khusus saja
* Mendukung definisi peran kustom keyvault
* Menambahkan `--no-wait` untuk perintah `az keyvault security-domain download` dan `--target-operation` untuk perintah `az keyvault security-domain wait`

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account backup show`: Operasi ditambahkan.
* `az netappfiles account backup delete`: Operasi ditambahkan.
* `az netappfiles account ad add`: Parameter `--ldap-over-tls` ditambahkan.
* `az netappfiles account create`: Parameter `--encryption` ditambahkan.
* `az netappfiles account update`: Parameter `--encryption` ditambahkan.
* `az netappfiles volume create`: Parameter `--encryption-key-source` ditambahkan.
* `az netappfiles volume create`: Kebijakan ekspor default dihapus untuk nfsv4.1 dan parameter opsional ditambahkan untuk menyiapkan kebijakan ekspor untuk nfsv4.1: rule_index, unix_read_only, unix_read_write, cifs, allow_clients

### <a name="network"></a>Jaringan

* `az network public-ip prefix create`: Mendukung `--zone 1 2 3`
* `az network lb frontend-ip create`: Mendukung `--zone 1 2 3`
* Bump versi dari '2020-08-01' hingga '2020-11-01'
* `az network lb address-pool`: Mendukung subnet saat membuat atau memperbarui kumpulan backend penyeimbang beban berbasis IP.

### <a name="rdbms"></a>RDBMS

* Menambahkan tes untuk saluran tim server yang fleksibel
* Migrasi Python SDK
* Menambahkan fitur buat, tampilkan, dan hapus database PostgreSQL
* Memperbarui Python SDK ke 8.1.0b2

### <a name="role"></a>Peran

* `az ad app permission list/grant`: Memperbaiki pesan kesalahan saat tidak ada Prinsip Layanan terkait untuk Aplikasi

### <a name="search"></a>Cari

* `az search`: GA

### <a name="service-fabric"></a>Service Fabric

* `az sf certificate`: tidak menggunakan perintah sertifikat kluster.

### <a name="sql"></a>SQL

* Menambahkan perintah Server Trust Group

### <a name="storage"></a>Penyimpanan

* Memperbaiki #16917: `az storage account generate-sas` gagal jika string koneksi disediakan
* Memperbaiki #16979: `az storage container create` gagal saat menyediakan metadata kontainer penyimpanan

### <a name="upgrade"></a>Mutakhirkan

* Memperbaiki #16952: Memperbaiki ImportError setelah peningkatan

### <a name="misc"></a>Lain-lain

* Izinkan mengonfigurasi tema

## <a name="march-02-2021"></a>02 Maret 2021

Versi 2.20.0

### <a name="aks"></a>AKS

* Menambahkan dukungan untuk addon 'confcom' SGX

### <a name="ams"></a>AMS

* Memperbarui modul untuk menggunakan api Layanan Media Azure 2020.
* `az ams account encryption`: Subgrup baru untuk menampilkan atau mengatur enkripsi untuk akun layanan media
* `az ams account storage set-authentication`: Perintah baru untuk mengatur autentikasi untuk akun penyimpanan yang terkait dengan akun layanan media
* `az ams account create (mi-system-assigned)`: Parameter --mi-system-assigned baru untuk pembuatan akun guna mengatur identitas akun media yang dikelola
* `az ams account mru set`: Perintah ini tidak akan berfungsi lagi untuk akun Media Services yang dibuat dengan API versi 05-01-2020 atau yang lebih baru.
* `az ams live-event create (stretch-mode, key-frame-interval, transcrip-lang, use-static-hostname, custom hostname)`: Menambahkan opsi parameter baru ke perintah buat acara langsung
* `az ams live-event standby`: Perintah baru untuk menempatkan acara langsung dalam mode siaga
* `az ams transform create (videoanalysismode, audioanalysis mode)`: Opsi parameter baru untuk pembuatan transformasi

### <a name="app-service"></a>App Service

* `az webapp config ssl bind`: menangani jika webapp dan paket appservice di rg. Juga pembaruan teks referensi
* Memperbaiki #8743: az webapp deploy
* Perbaikan Bug: Menambahkan generateRandomAppNames.json ke pengaturan
* `az functionapp create`: Menambahkan dukungan pratinjau untuk membuat aplikasi yang diisolasi dotnet.
* Memperbaiki #12150: Dukungan untuk ID subnet di vnet-integration add
* `az functionapp create`: Menghapus tanda pratinjau dari Node.js 14.

### <a name="arm"></a>ARM

* `az deployment group/sub/mg/tenant validate/create/what-if`: Menambahkan dukungan untuk file Bicep
* `az bicep install`: Perintah baru untuk menginstal Bicep CLI
* `az bicep upgrade`: Perintah baru untuk memutakhirkan Bicep CLI
* `az bicep build`: Perintah baru untuk membuat file Bicep
* `az bicep version`: Perintah baru untuk menampilkan versi Bicep CLI yang terinstal saat ini
* `az bicep list-versions`: Perintah baru untuk menampilkan versi Bicep CLI yang tersedia
* `az managedapp definition update`: Menambahkan perintah baru untuk memperbarui definisi aplikasi terkelola

### <a name="backup"></a>Cadangan

* `az backup recoverypoint show-log-chain`: Menambahkan waktu mulai/berakhir dalam output tabel show-log-chain
* Perbaikan Bug: Aktifkan Pemulihan Lokasi Alternatif untuk item yang dilindungi SQL/SAPHANA

### <a name="cdn"></a>CDN

* Menambahkan dukungan cli untuk SKU AFD

### <a name="compute"></a>Compute

* `az vm (extension) image list`: Jadikan lebih kuat
* `az vmss create`: Memperbaiki masalah jenis lisensi
* Meningkatkan versi API ke 01-12-2020
* `az vm create`: menambahkan `--enable-hotpatching`

### <a name="cosmos-db"></a>Cosmos DB

* Meningkatkan ke versi 3.0.0 dan menambahkan dukungan untuk NetworkAclBypass + Memperbarui Mongo ServerVersion + kebijakan pencadangan

### <a name="extension"></a>Extensi

* Mendukung konfigurasi url indeks ekstensi

### <a name="iot-central"></a>IoT Pusat

* `az iot central app`: Mengatasi beberapa perbaikan S360
* `az iot central app update`: Menghapus kebutuhan untuk memeriksa etag saat memperbarui aplikasi iotc yang ada.
* Ubah resourceType (IotApps) menjadi camel case.

### <a name="key-vault"></a>Key Vault

* [BREAKING CHANGE] `az keyvault role assignment/definition list`: `roleDefinitionName` harus `roleName` dalam output perintah
* [BREAKING CHANGE] `id` berubah menjadi `jobId`, `azureStorageBlobContainerUri` berubah menjadi `folderUrl` pada output perintah `az keyvault backup/restore`, `az keyvault key restore`

### <a name="network"></a>Jaringan

* Bump versi dari '2020-07-01' hingga '2020-08-01'
* `az network public-ip create`: Mendukung '--zone 1 2 3' setelah '01-08-2020'
* `az network routeserver peering`: Mengganti nama `--vrouter-name` dengan `--routeserver`
* `az network express-route peering create`: Mendukung alamat ipv6
* `az network public-ip create`: Mengekspos argumen baru `--tier`

### <a name="openshift"></a>OpenShift

* Pembaruan peringatan penghentian openshift az

### <a name="search"></a>Cari

* `az search`: Memperbaiki `--identity-type` panduan pembantu.

### <a name="sql"></a>SQL

* Memperbarui contoh az sql mi
* `az sql db/elastic-pool create/update`: Menambahkan argumen konfigurasi pemeliharaan
* `az sql db replica create`: Menambahkan argumen --secondary-type

### <a name="storage"></a>Penyimpanan

* [BREAKING CHANGE] `az storage account file-service-properties`: Default untuk mengaktifkan penghapusan kebijakan penyimpanan dengan hari penyimpanan 7 di sisi server
* Memperbaiki #16872: az storage blob now (2.19) memerlukan masuk bahkan jika connection-string disediakan
* Memperbaiki #16959: az storage copy crashes: ValidationError: variabel lokal 'layanan' direferensikan sebelum penugasan
* Memperbaiki #14054: objek 'NoneType' tidak memiliki atribut '__nama__'
* Memperbaiki #16679: `az storage blob download` gagal dengan "Izin ditolak" jika file tujuan adalah direktori
* Meningkatkan versi api penyimpanan ke 01-01-2020
* Versi dukungan dalam kebijakan manajemen Lifecyle
* Mendukung manajemen akses kunci bersama akun penyimpanan
* `az storage account network-rule`: Aturan akses sumber daya GA
* Mendukung enkripsi ganda untuk cakupan enkripsi
* `az storage account blob-service-properties update`: Mendukung --change-feed-retention-days
* Mendukung penulisan ulang blob yang ada

## <a name="february-10-2021"></a>10 Februari 2021

Versi 2.19.1

### <a name="key-vault"></a>Key Vault

* Perbaikan: Paket dependensi `azure-keyvault-administration` disematkan ke 4.0.0b1

## <a name="february-09-2021"></a>09 Februari 2021

Versi 2.19.0

### <a name="acr"></a>Azure Container Registry

* `az acr connected-registry install info`: Menambahkan kunci baru `ACR_SYNC_TOKEN_NAME` dengan nilai yang sama dengan `ACR_SYNC_TOKEN_USERNAME`. Peringatan bahwa yang terakhir akan ditinggalkan ditampilkan.
* `az acr connected-registry install renew-credentials`: Menambahkan kunci baru `ACR_SYNC_TOKEN_NAME` dengan nilai yang sama dengan `ACR_SYNC_TOKEN_USERNAME`. Peringatan bahwa yang terakhir akan ditinggalkan ditampilkan.

### <a name="aks"></a>AKS

* Menambahkan pengikatan penghentian/mulai kluster terkelola
* `az aks check-acr`: Memperbaiki pemeriksaan versi Kubernetes

### <a name="apim"></a>APIM

* GA grup perintah

### <a name="app-config"></a>Konfigurasi Aplikasi

* [BREAKING CHANGE] `az appconfig feature filter add`: Mendukung penambahan objek JSON sebagai nilai parameter filter fitur

### <a name="app-service"></a>App Service

* `az appservice ase/plan`: Mendukung ASEv3
* Memperbaiki #16026 dan #16118 untuk paket az appservice
* Memperbaiki # 16509: Menambahkan dukungan untuk os-preference
* Meningkatkan perilaku appservice ase create-inbound-services untuk memungkinkan melewatkan layanan DNS dan mendukung DNS untuk ASEv2
* `az webapp up/az webapp create`: Memperbaiki kesalahan nonetype
* `az webapp up/create`: penanganan kesalahan yang lebih baik dari nama aplikasi dengan titik
* Memperbaiki #16681: `az webapp config ssl import`: Memperbaiki bug yang menyebabkan kegagalan di cloud nasional

### <a name="arm"></a>ARM

* `az provider register`: Mendukung pendaftaran grup manajemen

### <a name="backup"></a>Cadangan

* Menambahkan fungsionalitas CRR untuk IaaSVM dan perintah CRR lainnya
* `az backup protectable-item list`: Menambahkan jenis-item yang dapat dilindungi sebagai argumen opsional

### <a name="botservice"></a>BotService

* `az bot create/update`: Menambahkan fitur Enkripsi `--cmk-key-url` dan `--encryption-off`
* `az bot update`: Mengganti nama Encryption-OFF arg menjadi CMK-OFF dan perbarui versi api

### <a name="compute"></a>Compute

* [BREAKING CHANGE] vmss create: Mengganti nama nilai mode orkestrasi
* Sshkey grup perintah baru. Izinkan referensi sumber daya kunci SSH saat membuat VM
* `az disk create/update`: Menambahkan parameter `--enable-bursting` untuk mendukung ledakan disk

### <a name="extension"></a>Extensi

* Mendukung kecocokan awalan perintah ekstensi untuk pemasangan dinamis

### <a name="hdinsight"></a>HDInsight

* `az hdinsight create`: Menambahkan parameter baru `--enable-compute-isolation` untuk mendukung pembuatan kluster dengan fitur isolasi komputasi.

### <a name="key-vault"></a>Key Vault

* `az keyvault key import`: Mendukung parameter `--curve` untuk mengimpor kunci BYOK
* `az keyvault certificate download`: Memperbaiki panggilan metode yang tidak digunakan lagi/dihapus
* `az keyvault create/update`: Menghapus tag pratinjau untuk `--enable-rbac-authorization`

### <a name="monitor"></a>Monitor

* `az monitor metrics alert create`: Memperbaiki kesalahan 'sumber daya tidak ditemukan'

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`: Menambahkan parameter `--security-operators`.
* `az netappfiles volume create`: Menambahkan parameter `--smb-continuously-available`.
* `az netappfiles volume create`: Menambahkan parameter `--smb-encryption`.
* `az netappfiles`: Tidak lagi dalam mode pratinjau.

### <a name="network"></a>Jaringan

* [BREAKING CHANGE] `az network vrouter`: Menghapus grup perintah ini, harap gunakan `az network routeserver`.
* `az network routeserver`: Menambahkan grup perintah baru.
* `az network application-gateway create`: Menambahkan parameter `--ssl-profile-id`
* `az network application-gateway client-cert`: Mengelola sertifikat klien tepercaya dari gateway aplikasi
* `az network application-gateway ssl-profile`: Mengelola profil ssl dari gateway aplikasi
* Menambahkan dukungan untuk koneksi titik akhir privat ke DigitalTwins

### <a name="profile"></a>Profil

* `az login`: Luncurkan peramban di WSL 2

### <a name="rdbms"></a>RDBMS

* `az mysql flexible-server create --iops`: Izinkan pengguna memilih IOPS untuk SKU mereka.
* Memperbarui perintah pemulihan Postgres untuk mendukung zona yang tersedia

### <a name="search"></a>Cari

* Meningkatkan untuk menggunakan python sdk terbaru (8.0.0) Azure-mgmt-search
* `az search create`: Menambahkan dukungan untuk pembuatan layanan pencarian dengan aturan IP, akses titik akhir publik, dan/atau msi
* `az search update`: Menambahkan dukungan untuk pembaruan layanan pencarian dengan aturan IP, akses titik akhir publik dan/atau msi
* `az search private-endpoint-connection`: Mengelola koneksi titik akhir privat ke layanan pencarian
* `az search shared-private-link-resource`: Mengelola sumber daya tautan pribadi bersama di layanan penelusuran
* `az search private-link-resource`: Cantumkan sumber tautan pribadi yang tersedia di layanan pencarian

### <a name="security"></a>Keamanan

* Menambahkan perintah baru untuk `az security`

### <a name="sql"></a>SQL

* Menambahkan kecocokan regex hsm terkelola ke SQL
* Meningkatkan Azure-mgmt-sql ke 0.26.0
* `az sql mi create/update`: Menambahkan dukungan untuk konfigurasi pemeliharaan dalam operasi instans terkelola
* Mendukung perintah kebijakan audit DevOps server SQL

### <a name="storage"></a>Penyimpanan

* Memperbaiki #16079: blob publik memberikan kesalahan
* Referensi perutean penyimpanan GA
* Memperbaiki #9158: Tidak dapat membuat kunci SAS yang berfungsi dari suatu kebijakan
* Memperbaiki #16489: Meningkatkan azcopy ke 10.8.0
* `az storage account blob-service-properties`: Mendukung versi layanan default
* Memperbaiki #16519: azcopy diberikan SAS yang lebih kuat dari yang dibutuhkan (sudah memiliki tulis, hanya perlu baca)

### <a name="synapse"></a>Synapse

* `az synapse workspace create `: Menambahkan parameter `--key-identifier` untuk mendukung pembuatan ruang kerja menggunakan kunci yang dikelola pelanggan.
* `az synapse workspace key`: Menambahkan cmdlet CRUD ke dukungan untuk mengelola kunci di bagian ruang kerja synapse yang ditentukan.
* `az synapse workspace managed-identity`: Menambahkan cmdlet untuk mendukung identitas terkelola CRUD ke pengaturan akses sql.
* `az synapse workspace`: Menambahkan dukungan perlindungan eksfiltrasi data, menambahkan parameter `--allowed-tenant-ids`.

## <a name="january-19-2021"></a>19 Januari 2021

Versi 2.18.0

### <a name="acr"></a>Azure Container Registry

* `az acr create / update`: Menambahkan `--allow-trusted-services`. Parameter ini menentukan apakah layanan Azure tepercaya diizinkan untuk mengakses registri yang dibatasi jaringan. Standarnya adalah mengizinkan.

### <a name="aks"></a>AKS

* `az aks check-acr`: Menambahkan perintah check-acr baru

### <a name="app-service"></a>App Service

* Memperbaiki #13907: `az webapp config ssl import`: Mengubah perintah untuk juga mengimpor Sertifikat App Service
* Memperbaiki #16125: `az webapp ssh`: Jika menggunakan klien windows, buka browser ke tautan scm
* Memperbaiki #13291: `az webapp deployment slot swap`: Perintah akan mendukung vnet pemeliharaan.
* [BREAKING CHANGE] Memperbaiki regresi di mana Anda tidak dapat menggunakan versi runtime dengan spasi di namanya

### <a name="arm"></a>ARM

* `az deployment` : Menambahkan dukungan untuk `--query-string`
* `az ts`: Perbaikan penanganan kesalahan untuk `--template-file` tanpa `--version` dilarang

### <a name="backup"></a>Cadangan

* `az backup protection backup-now`: Setel periode retensi default menjadi 30 hari

### <a name="compute"></a>Compute

* Memperbaiki masalah tidak ada profil_penyimpanan
* Penanganan kesalahan token eksternal yang lebih baik
* Memperbaiki masalah gambar ulang vmss
* `az vm/vmss extension set`: Parameter baru `--enable-auto-upgrade`

### <a name="container"></a>Kontainer

* `az container exec`: Menghapus eol check untuk menghindari penutupan terminal bahkan sebelum dimulai di linux

### <a name="dms"></a>DMS

* `az dms project task create`: Menambahkan parameter jenis tugas untuk membantu membedakan apakah skenario adalah migrasi online atau migrasi offline.
* `az dms project task cutover`: Menambahkan perintah baru yang memungkinkan tugas dengan jenis tugas migrasi online untuk memotong dan mengakhiri migrasi.
* `az dms project create/az dms project task create`: Aktifkan proyek/tugas MySQL dan PostgreSQL yang akan dibuat.

### <a name="iot"></a>IoT

* Menambahkan --tags ke IoT Hub buat dan perbarui

### <a name="monitor"></a>Monitor

* [BREAKING CHANGE] `az monitor log-analytics workspace data-export`: Hapus parameter `--export-all-tables` yang tidak digunakan lagi dan perlukan parameter `--tables`

### <a name="rdbms"></a>RDBMS

* Menghapus tag pratinjau untuk kunci server dan perintah admin iklan untuk Postgres dan MySql

### <a name="role"></a>Peran

* Memperbaiki #11594: `az role assignment create`: Hanya tampilkan nilai `--assignee-principal-type` yang didukung

### <a name="storage"></a>Penyimpanan

* Memperbaiki #16072: Mengunggah file dengan ukuran besar
* Memperbaiki #12291: `az storage blob generate-sas` tidak mengkodekan `--full-uri` dengan benar
* GA PITR dan properti layanan blob di SRP

## <a name="january-04-2021"></a>04 Januari 2021

Versi 2.17.1

### <a name="rdbms"></a>RDBMS

* Perbaikan: `az mysql create`: Kembalikan nama parameter yang salah 'serv_name' menjadi 'service_name'

## <a name="december-29-2020"></a>29 Desember 2020

Versi 2.17.0

### <a name="acr"></a>Azure Container Registry

* Mendukung zona redundansi
* `az acr connected-registry`: Fitur baru untuk Azure Container Registry lokal
* `az acr scope-map update`: --add dan --remove sudah tidak digunakan lagi, mereka diganti namanya menjadi --add-repo --remove-repo
* `az acr scope-map create/update`: Menambahkan dukungan untuk menangani tindakan Gateway.
* `az acr token create`: mendukung penambahan tindakan gateway

### <a name="aks"></a>AKS

* Memperbaiki: tambahkan argumen yang dihapus oleh PR sebelumnya
* `az aks get-credentials`: Memperjelas dokumentasi untuk mendapatkan kredensial

### <a name="app-service"></a>App Service

* Izinkan pelanggan membuat aplikasi fungsi Python 3.9
* Memperbaiki #14583: az webapp up akan membuat nama default jika nama tidak disediakan
* Memperbaiki: Penanganan kesalahan yang lebih baik saat mencoba membuat duplikat ASP di lokasi berbeda

### <a name="arm"></a>ARM

* `az ts`: Menambahkan dukungan untuk --tag
* `az ts`: Mendukung penghapusan satu versi
* `az provider register`: Menambahkan --accept-terms untuk mendaftarkan RPaaS
* Memperbaiki penguraian file JSON dengan string multi-baris

### <a name="aro"></a>ARO

* `az aro delete`: Menambahkan validasi RBAC pada penghapusan kluster
* `az aro update`: Menambahkan validasi RBAC pada pembaruan kluster
* Pastikan worker_profile bukan None sebelum mendapatkan subnet dari

### <a name="backup"></a>Cadangan

* `az backup job list`: Memecahkan bug tabel -o dan menambahkan backup_management_type sebagai input perintah

### <a name="batch"></a>Batch

* Meningkatkan bidang data ke [azure batch 10.0.0](https://pypi.org/project/azure-batch/10.0.0/)
* [BREAKING CHANGE] az batch job task-counts: Mengubah output dari objek JSON yang mengembalikan jumlah tugas ke objek JSON kompleks yang mencakup jumlah tugas (`taskCounts`) serta jumlah slot tugas (`taskSlotCounts`).

### <a name="compute"></a>Compute

* Jenis lisensi baru RHEL_ELS_6
* Mengadopsi SDK track2, Azure-mgmt-compute==18.0.0

### <a name="container"></a>Kontainer

* Memperbaiki kesalahan ejaan dalam teks contoh `az container create` CLI.

### <a name="databoxedge"></a>DataBoxEdge

* Modul perintah baru: dukungan untuk perangkat dan manajemen data-box-edge

### <a name="iot"></a>IoT

* Memperbarui pembuatan kunci perangkat
* Memperbarui pengujian hub yang mengaktifkan identitas untuk memperbaiki masalah RBAC titik akhir

### <a name="key-vault"></a>Key Vault

* `az keyvault key import`: Mendukung `--kty` untuk mengimpor kunci BYOK

### <a name="monitor"></a>Monitor

* `az monitor metrics alert create`: Meningkatkan pesan kesalahan untuk memberikan wawasan yang lebih dapat ditindaklanjuti

### <a name="network"></a>Jaringan

* `az network private-endpoint create`: Menambahkan lebih banyak deklarasi '--subnet' dan '--private-connection-resource-id'
* Ubah validator dari application-gateway ssl-cert create
* Migrasikan jaringan ke SDK track2
* Memperbaiki bug untuk "buat profil pengelola lalu lintas jaringan az" saat menggunakan "--routing-method MultiValue"

### <a name="profile"></a>Profil

* Memperbaiki "rahasia atau sertifikat yang hilang untuk mengautentikasi melalui prinsip layanan"

### <a name="role"></a>Peran

* `az ad sp create-for-rbac`: Menghentikan pembuatan penetapan peran Kontributor secara default

### <a name="security"></a>Keamanan

* Menambahkan perintah skor aman
* Memperbaiki perintah peringatan pembaruan dan dukung nilai baru

### <a name="sql"></a>SQL

* `az sql dw update`: jangan terima argumen cadangan-penyimpanan-redundansi
* `az sql db update`: memperbarui redundansi penyimpanan cadangan seperti yang diminta dari perintah

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah #15965: Menjelaskan cara menghapus beberapa tag penangguhan hukum dengan `az storage container legal-hold [clear|set]`
* `az storage account encryption-scope`: Dukungan GA
* Memperbaiki masalah #9959: Mencoba mengunduh versi snapshot dari berbagi file gagal dengan ResourceNotFound

### <a name="synapse"></a>Synapse

* Menambahkan cmdlet baru az synapse sql ad-admin show, create, update, delete
* Menambahkan pembaruan aturan firewall ruang kerja az synapse cmdlet baru
* Menambahkan cmdlet baru az synapse sql audit-policy show, update
* Menambahkan cmdlet terkait runtime integrasi

## <a name="december-08-2020"></a>08 Desember 2020

Versi 2.16.0

### <a name="acr"></a>Azure Container Registry

* Memperbarui deskripsi untuk KEK param

### <a name="aks"></a>AKS

* `az aks nodepool add/update/upgrade`: Ambil parameter lonjakan maksimum
* Menambahkan dukungan untuk addon AGIC
* Ubah kluster MSI ke default

### <a name="apim"></a>APIM

* `az apim restore`: Perintah baru untuk memulihkan cadangan layanan API Management

### <a name="app-service"></a>App Service

* Memperbaiki #14857: Mengizinkan pengguna memperbarui konfigurasi webapp bahkan dengan pembatasan akses
* `az functionapp create`: Terima `--runtime python` dan `--runtime-version 3.9` sebagai parameter Azure Functions v3
* Memperbaiki #16041: az webapp config ssl create menghasilkan kesalahan yang tidak diketahui

### <a name="arm"></a>ARM

* `az deployment-scripts`: Menghapus tanda pratinjau

### <a name="backup"></a>Cadangan

* Memperbaiki #14976: Peningkatan kesalahan CLI untuk kasus ValueError dan AttributeError
* `az backup protection undelete`: Menambahkan dukungan untuk pembatalan penghapusan perlindungan AzureWorkload menggunakan CLI
* Memperbaiki Kesalahan Permintaan Buruk untuk Masukan Jenis Beban Kerja yang Benar

### <a name="cdn"></a>CDN

* Menambahkan dukungan multi-asal pratinjau.
* Menambahkan rotasi otomatis BYOC.

### <a name="key-vault"></a>Key Vault

* `az keyvault key/secret list`: Menambahkan parameter `--include-managed` ke daftar sumber daya yang dikelola

### <a name="monitor"></a>Monitor

* `az monitor metrics alert create`: Mendukung ambang dinamis untuk parameter kondisi
* `az monitor metrics alert update`: Mendukung ambang dinamis untuk parameter kondisi
* `az monitor metrics alert dimension create`: Membuat dimensi aturan lansiran metrik
* `az monitor metrics alert condition create`: Membuat ketentuan aturan lansiran metrik

### <a name="mysql"></a>MySQL

* Menambahkan CLI pemutakhiran versi MySQL

### <a name="netappfiles"></a>NetAppFiles

* `az netappfiles account ad add`: Dua parameter opsional ditambahkan, aes_encryption dan ldap_signing
* `az netappfiles account backup-policy update`: Tiga parameter opsional ditambahkan tag bernama, jenis dan id
* `az netappfiles snapshot policy create`: Parameter opsional ditambahkan bernama provisioning_state

### <a name="network"></a>Jaringan

* `az network network watcher configure`: Memperbaiki kesalahan NetworkWatcherCountLimitReached yang disebabkan oleh sensitivitas huruf besar-kecil dari nilai lokasi
* `az network application-gateway http-listener`: Memperbaiki bug yang tidak dapat dibuat dan diperbarui dengan nama kebijakan WAF
* `az network route-table`: Menghentikan tabel rute V1
* `az network cross-region-lb`: Mendukung penyeimbang beban lintas wilayah
* `az network express-route port generate-loa`: Perintah baru untuk membuat dan mengunduh surat otorisasi PDF untuk ExpressRoutePort

### <a name="packaging"></a>Pengemasan

* Menambahkan paket Ubuntu Groovy

### <a name="rdbms"></a>RDBMS

* Menambahkan satu server show-connection-string dan tes untuk perintah konteks lokal, pembuatan server

### <a name="role"></a>Peran

* Menambahkan ringkasan panjang/peringatan untuk perintah yang menghasilkan kredensial

### <a name="search"></a>Cari

* Menambahkan opsi SKU

### <a name="service-fabric"></a>Service Fabric

* Memperbarui dokumen aplikasi SF. hanya mendukung sumber daya yang disebarkan arm

### <a name="synapse"></a>Synapse

* Mendukung cmdlet synapse sql dw dan memperbarui cmdlet az synapse workspace create

## <a name="november-20-2020"></a>20 November 2020

Versi 2.15.1

### <a name="profile"></a>Profil

* Perbaikan: Memperbaiki #15961: az login: UnboundLocalError: variabel lokal 'token_entry' direferensikan sebelum penugasan

## <a name="november-17-2020"></a>17 November 2020

Versi 2.15.0

### <a name="acs"></a>ACS

* Menambahkan peringatan penghentian v3

### <a name="aks"></a>AKS

* Menambahkan fungsionalitas os fana
* Peningkatan teknik: Mengganti string addon dengan konstanta
* `az aks install-cli`: Mendukung penyesuaian url unduhan
* `az aks browse`: Arahkan ke tampilan sumber daya Azure Portal Kubernetes jika k8s >=1.19 atau kube-dashboard tidak diaktifkan
* Mendukung identitas pesawat kontrol BYO
* `az aks use-dev-spaces`: Menunjukkan bahwa perintah dev-spaces sudah tidak digunakan lagi

### <a name="ams"></a>AMS

* Ubah "wilayah" menjadi "lokasi" di string output: az ams account sp create

### <a name="app-config"></a>Konfigurasi Aplikasi

* Memperbaiki inisialisasi klien kubah kunci

### <a name="app-service"></a>App Service

* Memperbaiki #13646: Tidak dapat membuat Paket App Service di grup sumber daya yang berbeda dengan Lingkungan App Service
* Memperbaiki #11698 #15198 #14862 #15409: az webapp/functionapp config access-restriction add
* `az functionapp create`: Menambahkan dukungan pratinjau Node 14.
* `az functionapp create`: Menghapus tanda pratinjau dari penangan khusus.
* [BREAKING CHANGE] pembaruan aplikasi fungsi: Memigrasikan aplikasi fungsi dari paket Premium ke Konsumsi sekarang memerlukan tanda '--force'.
* `az functionapp update`: Menambahkan pesan kesalahan jika migrasi functionapp melibatkan paket apa pun di Linux.
* `az functionapp update`: Menambahkan lebih banyak pesan galat deskriptif jika migrasi fungsi aplikasi gagal.

### <a name="arm"></a>ARM

* Memperbaiki masalah di mana What-If menunjukkan dua cakupan grup sumber daya dengan huruf besar yang berbeda
* `az deployment`: Cetak detail kesalahan untuk penyebaran

### <a name="backup"></a>Cadangan

* Memperbaiki #14976: KeyError diperbaiki dan teks bantuan ditingkatkan

### <a name="batch"></a>Batch

* Memperbaiki #15464: Memperbarui pemeriksaan file pfx tanpa kata sandi dalam batch create_certificate

### <a name="billing"></a>Billing

* [BREAKING CHANGE] di faktur penagihan: Menghapus properti BillingPeriodsNames dan DownloadUrlExpiry dari respons.
* `az billing invoice`: Mendukung banyak cakupan lain seperti BillingAccount, BillingProfile, dan langganan yang ada.
* `az billing account`: Perintah baru untuk mendukung tampilan dan memperbarui akun penagihan yang ada.
* `az billing balance`: Perintah baru untuk mendukung saldo tampilan profil penagihan.
* `az billing customer`: Perintah baru untuk mendukung tampilan pelanggan akun penagihan.
* `az billing policy`: Perintah baru untuk mendukung tampilan dan kebijakan pembaruan pelanggan atau profil penagihan.
* `az billing product`: Perintah baru untuk mengelola produk akun penagihan.
* `az billing profile`: Perintah baru untuk mengelola profil penagihan.
* `az billing property`: Perintah baru untuk menampilkan dan memperbarui properti akun penagihan.
* `az billing subscription`: Perintah baru untuk mengelola langganan akun penagihan.
* `az billing transaction`: Perintah baru untuk mencantumkan transaksi faktur.
* `az billing agreement`: Perintah baru untuk mengelola perjanjian penagihan.
* `az billing permission`: Perintah baru untuk mengelola izin penagihan.
* `az billing role-assignment`: Perintah baru untuk mengelola penetapan peran.
* `az billing role-definition`: Perintah baru untuk menampilkan definisi peran.
* `az billing instruction`: Perintah baru untuk mengelola petunjuk penagihan.

### <a name="compute"></a>Compute

* Memperbaiki masalah pemeriksaan izin pembaruan
* Peningkatan format tabel daftar-skus vm
* vm host grup buat: Buat --platform-fault-domain-count diperlukan dan perbarui bantuan
* Mendukung pembaruan versi vm/gambar ketika mereka menggunakan gambar penyewa silang

### <a name="dps"></a>DPS

* Izinkan tag di IoT DPS membuat perintah

### <a name="hdinsight"></a>HDInsight

* az hdinsight create: Menambahkan dua parameter `--resource-provider-connection` dan `--enable-private-link` untuk mendukung fitur tautan keluar dan tautan pribadi relai.

### <a name="key-vault"></a>Key Vault

* Memperbaiki pesan kesalahan untuk HSM `list-deleted` dan `purge`
* Mendukung pemulihan kunci selektif untuk HSM terkelola

### <a name="netappfiles"></a>NetAppFiles

* [BREAKING CHANGE] dengan pembaruan kumpulan netappfiles: Menghapus tingkat layanan dari parameter.
* `az netappfiles pool update`: Menambahkan parameter opsional qos-type.
* `az netappfiles pool create`: Menambahkan parameter opsional qos-type.
* `az netappfiles volume replication suspend`: Menambahkan force-break-replication sebagai parameter opsional.
* Menambahkan replikasi volume az netappfiles re-inisialisasi: Perintah baru ditambahkan untuk menginisialisasi ulang replikasi.
* Menambahkan az netappfiles volume pool-change: Perintah baru untuk mengubah pool volume.
* Menambahkan kebijakan snapshot az netappfiles: Grup perintah baru dengan list, delete, update, show, create and volumes.
* Menambahkan cadangan akun az netappfiles: Grup perintah baru dengan perintah tampilkan, daftar, dan hapus
* Menambahkan cadangan volume netappfiles az: Grup perintah baru dengan perintah tampilkan, daftar, hapus, perbarui, dan buat.
* Menambahkan kebijakan pencadangan akun az netappfiles: Grup perintah baru dengan perintah tampilkan, daftar, hapus, perbarui, dan hapus.
* Menambahkan daftar vault az netappfiles: Perintah baru ditambahkan.
* `az netappfiles account ad add`: Menambahkan parameter opsional kdc-ip, ad-name, server-root-ca-certificate dan backup-operator
* `az netappfiles volumes create`: Menambahkan parameter opsional snapshot-policy-id, backup-policy-id, backup-enabled, backup-id, policy-enforced, vault-id, kerberos-enabled, throughput-mibps, snapshot-directory-visible, keamanan -style, kerberos5-read-only, kerberos5-read-write, kerberos5i-read-only, kerberos5i-read-write, kerberos5p-read-only, kerberos5p-read-write dan has-root-access.
* `az netappfiles volume update`: Menambahkan parameter opsional vault-id, backup-enabled, backup-policy-id, policy-enforced dan throughput-mibps

### <a name="network"></a>Jaringan

* Memperbaiki bug yang tidak dapat membuat gateway aplikasi Standard_v2 tanpa alamat IP statis pribadi
* `az network dns zone import`: Naikkan FileOperationError alih-alih FileNotFoundError jika file zona tidak ada
* Memperbaiki kerusakan kesalahan NoneType saat menghapus sumber daya yang tidak ada dari ApplicationGateway, LoadBalancer, Nic

### <a name="private-dns"></a>DNS Privat

* `az network private-dns zone import`: Naikkan FileOperationError alih-alih FileNotFoundError jika file zona tidak ada

### <a name="profile"></a>Profil

* `az login`: Menambahkan kembali peringatan bahwa browser dibuka

### <a name="role"></a>Peran

* `az role assignment create`: Membuat pratinjau `--description`, `--condition`, `--condition-version`

### <a name="security"></a>Keamanan

* `az security pricing`: Memperbarui bantuan untuk mencerminkan versi API saat ini yang dipanggil

### <a name="storage"></a>Penyimpanan

* Memperbaiki #15600: az storage fs exists: jika fs tidak ada ResourceNotFoundError akan ditampilkan
* Memperbaiki #15706: Contoh pembuatan kontainer penyimpanan salah
* `az storage blob delete-batch`: Kesalahan ketik yang benar dalam dokumentasi.

## <a name="november-09-2020"></a>09 November 2020

Versi 2.14.2

### <a name="app-service"></a>App Service

* Memperbaiki #15604, #15605: Menambahkan dukungan Dotnet5

## <a name="november-06-2020"></a>06 November 2020

Versi 2.14.1

### <a name="arm"></a>ARM

* Perbaikan: Menambahkan dukungan string multi baris TS untuk input template

## <a name="october-27-2020"></a>27 Oktober 2020

Versi 2.14.0

### <a name="aks"></a>AKS

* Menambahkan dukungan PPG
* Memperbarui batas waktu penyeimbang beban standar maksimum menjadi 100 menit

### <a name="apim"></a>APIM

* Memperbaiki masalah dengan membuat instance tingkat konsumsi

### <a name="app-config"></a>Konfigurasi Aplikasi

* Memperbaiki kueri nilai kunci dengan label yang dipisahkan koma

### <a name="app-service"></a>App Service

* Perbaikan bug: az webapp up gagal ketika pengguna tidak memiliki izin menulis ke direktori induk proyek
* Memperbaiki #13777: Memperbaiki untuk menghapus karakter pelarian dari XML
* Memperbaiki #15441: az webapp create-remote-connection gagal dengan AttributeError: Objek 'Thread' tidak memiliki atribut 'isAlive'
* [BREAKING CHANGE] aplikasi web up: menambahkan params opsional (os & runtime) dan runtime yang diperbarui

### <a name="arm"></a>ARM

* Membuat penyebaran template Perintah What-If GA
* [BREAKING CHANGE] Menambahkan konfirmasi pengguna untuk az ts create
* Memperbaiki data yang dikembalikan saat menandai beberapa sumber daya

### <a name="backup"></a>Cadangan

* `az backup policy create`: Menambahkan dukungan untuk pembuatan kebijakan pencadangan IaaSVM dari CLI
* Meningkatkan batas perlindungan Mesin Virtual dari 100 menjadi 1000

### <a name="compute"></a>Compute

* sig definisi gambar buat: tambahkan --fitur
* Versi API baru dari gallery_images 30-09-2020
* `az vm update / az sig image-version update`: Mendukung pembaruan vm/image-version meskipun menggunakan gambar penyewa silang
* Menghapus validasi SKU host vm

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb create/update`: Memperbaiki pesan kesalahan dari input --lokasi yang salah
* `az cosmosdb sql container create/update`: Menambahkan parameter --analytical-storage-ttl

### <a name="hdinsight"></a>HDInsight

* [BREAKING CHANGE] di hdinsight buat: hapus dua parameter: --public-network-access-type dan --outbound-public-network-access-type

### <a name="iot-central"></a>IoT Pusat

* Menghapus peringatan pratinjau karena sudah GAed

### <a name="key-vault"></a>Key Vault

* Batalkan `--enable-soft-delete false` saat membuat atau memperbarui brankas
* Jadikan `--bypass` dan `--default-action` bekerja sama dengan parameter jaringan acl saat membuat vault

### <a name="misc"></a>Lain-lain

* Menambahkan penyelesaian bash ke Dockerfile

### <a name="rdbms"></a>RDBMS

* Menambahkan Perintah Daftar-SKUS, Transformer Tabel, Konteks Lokal untuk Postgres, MySQL, Server Tunggal Mariadb
* [BREAKING CHANGE] Pembaruan nama parameter. Peningkatan pada Management Plane untuk MySQL dan PostgreSQL
* `az postgres|mariadb|mysql server create` : Memperbarui pengalaman membuat untuk Postgres, MySQL, dan MariaDB - bidang baru di output, Perkenalkan nilai baru untuk parameter `--public` dalam perintah buat (semua,\<IP\>,\<IPRange\>,0.0.0.0)

### <a name="signalr"></a>SignalR

* `az signalr create`: Menambahkan opsi baru `--enable-messaging-logs` untuk mengontrol layanan yang menghasilkan log perpesanan atau tidak
* `az signalr update`: Menambahkan opsi baru `--enable-messaging-logs` untuk mengontrol layanan yang menghasilkan log perpesanan atau tidak

### <a name="sql"></a>SQL

* [BREAKING CHANGE] Memperbaiki respons untuk nama dan nilai parameter redundansi penyimpanan cadangan untuk MI
* `az sql db audit-policy show`: diperluas untuk menunjukkan kebijakan audit basis data termasuk data LA dan EH
* `az sql db audit-policy update`: perpanjang untuk mengizinkan pembaruan LA dan EH bersama dengan kebijakan audit basis data
* `az sql db audit-policy wait`: menempatkan CLI dalam status menunggu hingga kondisi kebijakan audit basis data terpenuhi.
* `az sql server audit-policy show`: diperluas untuk menunjukkan kebijakan audit server termasuk data LA dan EH
* `az sql server audit-policy update`: perpanjang untuk mengizinkan pembaruan LA dan EH bersama dengan kebijakan audit server
* `az sql server audit-policy wait`: menempatkan CLI dalam status menunggu hingga kondisi kebijakan audit server terpenuhi.
* Menambahkan Dukungan khusus AAD untuk Instans dan Server yang Dikelola SQL
* `az sql db replica create`: Menambahkan argumen --partner-database

### <a name="storage"></a>Penyimpanan

* Memperbaiki #15111: `az storage logging update` gagal tanpa argumen opsional
* Memperbaiki bug saat menggunakan perintah set-tier dengan login utama layanan
* Meningkatkan versi untuk file datalake ke 10-02-2020
* `az storage queue list`: Track2 didukung
* `az storage fs access`: Mendukung pengelolaan ACL secara rekursif

### <a name="synapse"></a>Synapse

* Menambahkan saluran, layanan tertaut, pemicu, buku catatan, aliran data, dan cmdlet terkait kumpulan data

## <a name="october-13-2020"></a>13 Oktober 2020

Versi 2.13.0

### <a name="acr"></a>Azure Container Registry

* `az acr helm`: Memperbarui url penghentian
* Menambahkan perubahan templat log dan tugas sistem untuk Tugas ACR

### <a name="aks"></a>AKS

* Mendukung virtual-node dengan aks create: `az aks create --enable-addons virtual-node`
* Menambahkan opsi hanya gambar node untuk CLI
* Harapkan addon kube-dashboard dinonaktifkan secara default
* `az aks create/update`: Menambahkan dukungan LicenseType untuk Windows
* Mendukung penambahan kumpulan node Spot
* Kehormatan nama addon yang ditentukan di Azure CLI

### <a name="ams"></a>AMS

* Memperbaiki #14687: Grup sumber daya campuran dan nama akun dalam perintah "az ams streaming-endpoint show"

### <a name="app-config"></a>Konfigurasi Aplikasi

* Memperbaiki bug uji
* Mendukung autentikasi AAD untuk operasi data

### <a name="app-service"></a>App Service

* `az functionapp deployment source config-zip`: Memperbaiki masalah di mana config-zip dapat menimbulkan pengecualian pada keberhasilan konsumsi linux
* Perbaikan Bug: Pesan kesalahan yang lebih baik untuk perintah aplikasi web
* `az appservice domain create, show-terms`: Menambahkan kemampuan untuk membuat domain layanan aplikasi
* `az functionapp create`: Menghapus tanda pratinjau dari Java 11 saat membuat aplikasi fungsi baru
* [BREAKING CHANGE] dengan pembuatan webapp, az webapp up - Memperbarui waktu proses webapp yang tersedia

### <a name="arm"></a>ARM

* `az ts`: Menambahkan perintah baru untuk spesifikasi template
* `az deployment` : Menambahkan dukungan untuk --template-spec -s

### <a name="compute"></a>Compute

* Memperbaiki batasan jumlah FD pembuatan grup host
* Menambahkan perintah baru untuk mendukung ekstensi pemutakhiran untuk VMSS
* Memperbaiki referensi gambar yang hilang masalah

### <a name="hdinsight"></a>HDInsight

* `az hdinsight create`: menambahkan informasi usang untuk argumen --public-network-access-type dan --outbound-public-network-access-type
* `az hdinsight create`: menambahkan informasi usang untuk argumen `--public-networrk-access-type` dan `--outbound-public-network-access-type`
* `az hdinsight create`: menambahkan parameter `--idbroker` untuk mendukung pelanggan membuat kluster ESP dengan HDInsight Id Broker

### <a name="iot-central"></a>IoT Pusat

* Menghapus modul perintah 'az iotcentral' yang tidak digunakan lagi

### <a name="key-vault"></a>Key Vault

* Mendukung `--hsm-name` untuk `az keyvault key encrypt/decrypt`

### <a name="lab"></a>Laboratorium

* Memperbaiki # 14127: `__init__()` membutuhkan 1 argumen posisi tetapi yang diberikan 2

### <a name="network"></a>Jaringan

* `az network application-gateway ssl-cert show`: Menambahkan contoh untuk mendemonstrasikan format sertifikat dan mengambil informasi
* `az network application-gateway rule`: Mendukung --pilihan prioritas
* `az network application-gateway create`: Memperbaiki bug yang tidak dapat dibuat tanpa IP publik ditentukan
* `az network application-gateway waf-policy managed-rule rule-set add`: Mengekspos kesalahan server kepada pengguna untuk memberikan pesan petunjuk yang lebih intuitif.
* `az network application-gateway waf-policy managed-rule rule-set update`: Dukungan untuk mengubah versi jenis set aturan.

### <a name="rdbms"></a>RDBMS

* Perbaikan bug: az postgres flexible-server create Hapus versi API yang di-hardcode dari klien jaringan.

### <a name="role"></a>Peran

* Memperbaiki #15278: `az role assignment list/delete`: Melarang argumen string kosong

### <a name="sql"></a>SQL

* `az sql midb log-replay`: Dukungan untuk layanan pemutaran ulang log pada basis data terkelola
* Abaikan karakter casing untuk nilai parameter redundansi penyimpanan cadangan untuk instance terkelola
* [BREAKING CHANGE] az sql db buat: Menambahkan parameter --backup-storage-redundancy; tambahkan peringatan untuk bsr/bsr yang tidak ditentukan == Geo.

### <a name="sql-vm"></a>SQL VM

* `az sql vm show`: Menambahkan opsi konfigurasi ke --expand flag

### <a name="storage"></a>Penyimpanan

* [BREAKING CHANGE] `az storage blob copy start`: Memperbaiki masalah format untuk `--destination-if-modified-since` dan `--destination-if-unmodified-since`
* [BREAKING CHANGE] `az storage blob incremental-copy start`: Memperbaiki masalah format untuk `--destination-if-modified-since` dan `--destination-if-unmodified-since`
* `az storage fs`: Memperbaiki masalah string koneksi
* `az storage share-rm`: Tingkat akses rilis GA
* `az storage container-rm`: Menambahkan grup perintah baru untuk menggunakan penyedia sumber daya Microsoft.Storage untuk operasi pengelolaan kontainer.

## <a name="september-29-2020"></a>29 September 2020

Versi 2.12.1

### <a name="rdbms"></a>RDBMS

* Perbaikan: `az postgres flexible-server create` : Memperbarui VnetName untuk mengecualikan nama server dan memperbarui wilayah default untuk MySQL

## <a name="september-22-2020"></a>September 22, 2020

Versi 2.12.0

### <a name="acr"></a>Azure Container Registry

* Memperbaiki #14811 Menambahkan dukungan untuk penggantian dockerignore

### <a name="aks"></a>AKS

* CLI harus mentolerir kubeconfig kosong
* FIX #12871: az aks enable-addons: Contoh bantuan yang dibuat secara otomatis salah untuk opsi vitual-node
* Menghapus tindakan konektor aci lama
* Mendukung addon kebijakan Azure di Azure-cli
* Memperbaiki masalah peka huruf besar/kecil untuk addon dasbor AKS
* Memperbarui mgmt-kontainerservice ke 9.4.0 dan aktifkan 09-01 API

### <a name="apim"></a>APIM

* Mendukung perintah entitas produk / productapi / bernama Nilai && versi sdk bump

### <a name="app-config"></a>Konfigurasi Aplikasi

* Mendukung pengaktifan/penonaktifkan PublicNetworkAccess untuk penyimpanan yang ada

### <a name="app-service"></a>App Service

* Menambahkan dukungan untuk tingkat harga Premium V3
* Memperbaiki #12653: az webapp log config --application-logging false tidak mematikannya
* Memperbaiki #14684: penghapusan pembatasan akses berdasarkan alamat ip tidak berfungsi; #13837-az webapp create - Contoh RSgroup yang berbeda untuk Paket dan WebApp
* functionapp: Menambahkan dukungan untuk penangan kustom. Powershell 6.2 yang tidak digunakan lagi
* functionapp: Memperbaiki masalah di mana pengaturan aplikasi salah diatur untuk gambar khusus linux

### <a name="arm"></a>ARM

* `az deployment group/sub/mg/tenant what-if`: Tampilkan "Abaikan" perubahan sumber daya terakhir

### <a name="compute"></a>Compute

* Menambahkan license_type baru di vm create/update: RHEL_BYOS, SLES_BYOS
* Meningkatkan versi API disk ke 30-06-2020
* pembuatan disk: tambahkan --logical-sector-size, --tier
* pembaruan disk: Mendukung --disk-iops-read-only, --disk-mbps-read-only, --max-shares
* Perintah baru disk-enkripsi-set daftar-sumber daya terkait
* vm boot-diagnostics aktifkan: --storage menjadi opsional
* Perintah baru: vm boot-diagnostics get-boot-log-uris
* vm boot-diagnostics get-boot-log: mendukung penyimpanan terkelola

### <a name="config"></a>Konfigurasi

* Mengganti nama konteks lokal menjadi config param-persist

### <a name="cosmos-db"></a>Cosmos DB

* Dukungan untuk API Migrasi sumber daya Throughput untuk fitur Autoscale di CosmosDB

### <a name="eventhub"></a>Eventhub

Menambahkan perintah Cluster dan parameterTrusted_service_access_enabled untuk Networkruleset

### <a name="extension"></a>Extensi

* `az extension add`: Menambahkan opsi `--upgrade` untuk memperbarui ekstensi jika sudah terpasang
* Aktifkan pemasangan dinamis secara default

### <a name="iot"></a>IoT

* Mengaktifkan versi TLS minimum di IoT Hub Create

### <a name="iot-central"></a>IoT Pusat

* Operasi penghapusan aplikasi sekarang adalah operasi yang berjalan lama

### <a name="iot-hub"></a>Iot Hub

* Perintah 'show-connection-string' yang tidak digunakan lagi

### <a name="key-vault"></a>Key Vault

* Pratinjau publik HSM terkelola
* Memperbaiki masalah yang `--maxresults` tidak berlaku saat mencantumkan sumber daya atau versi sumber daya

### <a name="kusto"></a>Kusto

* Menambahkan pesan yang mencela

### <a name="monitor"></a>Monitor

* `az monitor log-analytics workspace linked-storage`: memaparkan pesan kesalahan terperinci kepada pelanggan

### <a name="network"></a>Jaringan

* `az network vnet subnet`: Mendukung --disable-private-endpoint-network-policies dan --disable-private-link-service-network-policies
* Memperbaiki bug saat memperbarui flow-log ketika subproperty network_watcher_flow_analytics_configuration adalah None
* Versi API menabrak 01-06-2020
* Mendukung --tcp-port-behavior saat mengonfigurasi konfigurasi TCP dari Connection Monitor V2
* Mendukung lebih banyak jenis dan tingkat cakupan saat membuat Endpoint of Connection Monitor V2
* Mendukung --host-subnet untuk membuat VirtualHub di bawahnya sebagai VirtualRouter

### <a name="rdbms"></a>RDBMS

* Pembaruan Management Plane untuk PostgreSQL dan MySQL

### <a name="role"></a>Peran

* `az role assignment create/update`: Dukungan `--description`, `--condition` dan `--condition-version`
* `az ad app permission delete`: Mendukung `--api-permissions` untuk menghapus `ResourceAccess` tertentu

### <a name="service-fabric"></a>Service Fabric

* Menambahkan perintah tipe kluster dan node terkelola

### <a name="sql"></a>SQL

* Meningkatkan Azure-mgmt-sql ke 0.20.0
* Menambahkan parameter opsional redundansi penyimpanan cadangan ke MI create cmdlet

### <a name="storage"></a>Penyimpanan

* `az storage share-rm stats`: Mendapatkan byte penggunaan data yang disimpan di share.
* Gumpalan penyimpanan rilis GA PITR
* `az storage blob query`: Mendukung Percepatan Kueri Azure Storage
* Mendukung Penghapusan Lunak untuk berbagi file
* `az storage copy`: Menambahkan dukungan kredensial akun dan hentikan `--source-local-path`, `--destination-local-path`, `--destination-account-name`
* `az storage account blob-service-properties update`: Menambahkan dukungan kebijakan penyimpanan penghapusan kontainer

### <a name="synapse"></a>Synapse

* Memperbaiki kesalahan ketik dalam contoh tugas peran sinapsis az buat dan hapus

## <a name="august-28-2020"></a>28 Agustus 2020

Versi 2.11.1

### <a name="acr"></a>Azure Container Registry

* Menambahkan Tingkat Terisolasi ke Kumpulan Agen
* Menambahkan Konteks Sumber Artefak OCI

### <a name="aks"></a>AKS

* Memperbaiki masalah pembuatan kluster aks

### <a name="cognitive-services"></a>Cognitive Services

* [BREAKING CHANGE] Tampilkan istilah hukum tambahan untuk API tertentu

### <a name="network"></a>Jaringan

* [BREAKING CHANGE] Izinkan untuk membuat IP publik dan pribadi saat membuat Gateway Aplikasi
* `az network list-service-tags`: menambahkan detail tentang penggunaan parameter lokasi ke pesan bantuan

### <a name="storage"></a>Penyimpanan

* `az storage blob list`: Mendukung properti ATAU dengan versi api baru

## <a name="august-25-2020"></a>25 Agustus 2020

Versi 2.11.0

### <a name="aks"></a>AKS

* Menghapus tag pratinjau dari add-on Virtual Node
* Menambahkan argumen AKS CMK dalam pembuatan kluster
* Atur profil jaringan saat menggunakan penyeimbang beban dasar.
* Menghapus validasi pod maks dari CLI dan biarkan preflight menanganinya
* Memperbaiki pengaya yang tersedia dalam pesan bantuan di `az aks create`
* Menghadirkan dukungan untuk profil autoscaler kluster di CLI core

### <a name="appservice"></a>AppService

* `az webapp`: Menambahkan perintah list-instances
* `az webapp ssh`: Menambahkan parameter --instans untuk terhubung ke instans tertentu
* `az webapp create-remote-connection`: Menambahkan parameter --instans untuk terhubung ke instans tertentu
* Memperbaiki #14758: az webapp membuat kesalahan saat membuat aplikasi windows dengan --runtime dotnetcore
* Memperbaiki #14701: Menerapkan functionapp create --assign-identity
* Memperbaiki #11244: `az webapp auth update`: Menambahkan parameter opsional untuk memperbarui client-secret-certificate-thumbprint
* `az functionapp keys`: Menambahkan perintah yang memungkinkan pengguna mengelola tombol aplikasi fungsinya
* `az functionapp function`: Menambahkan perintah yang memungkinkan pengguna mengelola masing-masing fungsinya
* `az functionapp function keys`: Menambahkan perintah yang memungkinkan pengguna mengelola tombol fungsi mereka
* Memperbaiki #14788: az webapp create tidak mendapatkan webapp yang benar ketika namanya substring
* `az functionapp create`: Menghapus kemampuan untuk membuat Fungsi 2.x di wilayah yang tidak mendukungnya

### <a name="arm"></a>ARM

* `az resource list`: Memperluas data pengembalian `createdTime`, `changedTime`, dan `provisioningState`
* `az resource`: Menambahkan parameter `--latest-include-preview` untuk mendukung penggunaan versi api terbaru apakah versi ini adalah pratinjau

### <a name="aro"></a>ARO

* Peningkatan CLI, termasuk izin pemeriksaan tabel rute

### <a name="cloud"></a>Cloud

* `az cloud register`: Memperbaiki pendaftaran cloud dengan file konfigurasi

### <a name="compute"></a>Compute

* Memperbarui SKU Mesin Virtual yang mendukung jaringan yang dipercepat
* `az vm create`: Patching in-guest otomatis
* `az image builder create`: Menambahkan --vm-size, --os-disk-size, --vnet, --subnet
* Perintah baru az vm assesment-patches

### <a name="container"></a>Kontainer

* Memperbaiki # 6235: Memperbarui teks bantuan untuk parameter port dalam pembuatan kontainer

### <a name="datalake-store"></a>Toko Datalake

* Memperbaiki masalah #14545 untuk operasi penggabungan data lake

### <a name="eventhub"></a>EventHub

* `az eventhubs eventhub create/update`: Ubah dokumentasi destination_name

### <a name="extension"></a>Extensi

* Menambahkan perintah `az extension list-versions` ke daftar semua versi ekstensi yang tersedia

### <a name="hdinsight"></a>HDInsight

* Mendukung pembuatan kluster dengan konfigurasi autoscale dan Mendukung pengelolaan konfigurasi autoscale
* Mendukung pembuatan kluster dengan enkripsi di host

### <a name="iotcentral"></a>IoTCentral

* Peningkatan dokumentasi CLI

### <a name="monitor"></a>Monitor

* `az monitor metrics alert create`: mendukung RG dan Sub sebagai nilai cakupan

### <a name="netappfiles"></a>NetAppFiles

* [BREAKING CHANGE] az netappfiles snapshot create: Menghapus file-system-id dari parameter
* [BREAKING CHANGE] az netappfiles snapshot show: Snapshot tidak lagi memiliki parameter file-system-id
* `az netappfiles account`: Model ActiveDirectory memiliki parameter baru backup_operators
* `az netappfiles volume show`: Model dataProtection memiliki cuplikan parameter baru
* `az netappfiles volume show`: Model Volume memiliki parameter baru snapshot_directory_visible

### <a name="network"></a>Jaringan

* `az network dns export`: ekspor FQDN untuk tipe MX, PTR, NS, dan SRV alih-alih jalur relatif
* Mendukung tautan pribadi untuk disk yang dikelola
* `az network application-gateway auth-cert show`: Menambahkan contoh untuk mendemonstrasikan format sertifikat
* `az network private-endpoint-connection`: mendukung konfigurasi aplikasi

### <a name="rbac"></a>RBAC

* `az ad group create`: mendukung peentuan deskripsi saat membuat grup
* `az role definition create`: cetak pesan yang dapat dibaca manusia alih-alih pengecualian ketika assignableScope adalah larik kosong
* [BREAKING CHANGE] `az ad sp create-for-rbac`: ubah izin default dari sertifikat yang dibuat

### <a name="sql"></a>SQL

* `az sql server audit-policy`: Menambahkan dukungan audit server sql

### <a name="storage"></a>Penyimpanan

* `az storage blob copy start-batch`: Memperbaiki #6018 untuk --source-sas
* `az storage account or-policy`: Mendukung kebijakan replikasi objek akun penyimpanan
* Memperbaiki masalah #14083 untuk meningkatkan versi paket penyimpanan Azure-multiapi untuk masalah paket dan dukungan versi api baru
* `az storage blob generate-sas`: Menambahkan contoh untuk --ip dan perbaiki pesan kesalahan
* `az storage blob list`: Memperbaiki masalah penanda_berikutnya

### <a name="synapse"></a>Synapse

* Menambahkan ruang kerja, sparkpool, cmdlet terkait sqlpool
* Menambahkan perintah terkait pekerjaan percikan berdasarkan track2 sdk
* Menambahkan perintah terkait fitur kontrol akses berdasarkan track2 sdk

### <a name="upgrade"></a>Mutakhirkan

* Menambahkan perintah `az upgrade` untuk meningkatkan cli dan ekstensi Azure

## <a name="august-11-2020"></a>11 Agustus 2020

Versi 2.10.1

### <a name="app-service"></a>App Service

* Memperbaiki #9887 webapp dan functionapp, mendukung penetapan/penghapusan identitas yang dikelola pengguna
* Memperbaiki #1382, #14055: Memperbarui pesan kesalahan untuk az webapp create dan az webapp config kontainer set
* `az webapp up`: Memperbaiki logika pemilihan ASP default ketika parameter --plan tidak disediakan

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Mendukung pengaktifan/penonaktifkan PublicNetworkAccess selama pembuatan penyimpanan

### <a name="compute"></a>Compute

* Mendukung pengaitan disk dan snapshot dengan sumber daya akses disk

### <a name="lab"></a>Laboratorium

* Memperbaiki masalah #7904 bug validasi tanggal dalam pembuatan mesin virtual lab

### <a name="storage"></a>Penyimpanan

* `az storage blob upload-batch`: Memperbaiki masalah #14660 dengan argumen tidak berposisi

## <a name="august-04-2020"></a>04 Agustus 2020

Versi 2.10.0

### <a name="aks"></a>AKS

* `az aks update`: Ubah argumen --enable-aad untuk memigrasikan kluster non-AAD berkemampuan RBAC ke kluster AAD yang dikelola AKS
* `az aks install-cli`: Menambahkan argumen --kubelogin-version dan --kubelogin-install-location untuk menginstal kubelogin
* Menambahkan perintah get-upgrade az aks nodepool

### <a name="ams"></a>AMS

* Fix #14021: akun az ams sp tidak idempoten

### <a name="apim"></a>APIM

* apim api import: dukung impor API dan tingkatkan perintah cli level api lainnya

### <a name="app-service"></a>App Service

* Memperbaiki #13035: Menambahkan validasi untuk pembatasan akses konfigurasi az webapp untuk menghindari penambahan file duplikat

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Default ke sku standar jika tidak ditentukan
* [BREAKING CHANGE] Mendukung pengaturan dengan jenis konten JSON

### <a name="arm"></a>ARM

* `az resource tag`: Memperbaiki bug pemberian tag Aplikasi terkelola dan beberapa masalah pengujian terkait
* `az deployment mg/tenant what-if`: Menambahkan dukungan ke grup manajemen dan penyebaran tingkat penyewa What-If
* `az deployment mg/tenant create`: Menambahkan parameter --confirm-with-what-if/-c.
* `az deployment mg/tenant create`: Menambahkan parameter --what-if-result-format/-r.
* `az deployment mg/tenant create`: Menambahkan parameter --what-if-exclude-change-types/-x.
* `az tag`: dukungan tag az untuk parameter id sumber daya

### <a name="backup"></a>Cadangan

* Memicu penemuan kontainer/item AFS hanya jika diperlukan

### <a name="cdn"></a>CDN

* Menambahkan bidang tautan pribadi ke Origin

### <a name="compute"></a>Compute

* `az vm/vmss create`: Pilih nama pengguna yang valid untuk pengguna jika nama pengguna default tidak valid
* `az vm update`: mendukung gambar penyewa lintas
* `az disk-access`: Menambahkan grup perintah baru untuk mengoperasikan sumber daya akses disk
* Mendukung penempatan otomatis grup host khusus
* Mendukung ppg dan spg dalam mode orkestrasi VMSS

### <a name="config"></a>Konfigurasi

* `az config`: Menambahkan `config` modul perintah baru

### <a name="extension"></a>Extensi

* Mendukung pemasangan ekstensi secara otomatis jika ekstensi perintah tidak diinstal

### <a name="hdinsight"></a>HDInsight

* Menambahkan 3 parameter ke perintah `az hdinsight create` untuk mendukung tautan pribadi dan enkripsi dalam fitur transit:

### <a name="iot-hub"></a>Iot Hub

* Memperbaiki # 7792: IoT Hub Create tidak idempotent

### <a name="iot-central"></a>IoT Pusat

* Menambahkan daftar opsi paramater untuk iot central

### <a name="keyvault"></a>Az.KeyVault

* `az keyvault key encrypt/decrypt`: menambahkan parameter `--data-type` untuk secara eksplisit menentukan jenis data asli

### <a name="monitor"></a>Monitor

* `az monitor log-analytics workspace data-export`: mendukung namespace hub acara sebagai tujuan.
* `az monitor autoscale`: mendukung namespace dan dimensi untuk --condition

### <a name="netappfiles"></a>NetAppFiles

* `az volume revert`: Tambah Volume Kembalikan untuk mengembalikan volume ke salah satu cuplikannya.
* [BREAKING CHANGE] Menghapus `az netappfiles mount-target`.
* `az volume show`: Menambahkan situs ke Properti Active Directory

### <a name="network"></a>Jaringan

* `az application-gateway private-link add`: mendukung menentukan subnet yang ada berdasarkan ID
* `az network application-gateway waf-policy create`: mendukung versi dan jenis

### <a name="storage"></a>Penyimpanan

* Memperbaiki # 10302: Mendukung tebakan jenis konten saat menyinkronkan file
* `az storage blob lease`: Terapkan versi api baru untuk operasi sewa blob
* `az storage fs access`: Mendukung kredensial AAD dalam mengelola kontrol akses untuk akun ADLS Gen2
* `az storage share-rm create/update`: menambahkan --access-tier untuk mendukung tingkat akses

## <a name="july-16-2020"></a>16 Juli 2020

Versi 2.9.1

### <a name="aks"></a>AKS

* Menghapus pengaturan eksplisit VMSS di perintah contoh Windows karena sekarang default

### <a name="iot"></a>IoT

* [BREAKING CHANGE] `az iot pnp`: Menghapus perintah pratinjau PNP IoT dari CLI inti

### <a name="rest"></a>REST

* Memperbaiki #14152: `az rest`: Menerima URL ARM tanpa ID langganan

### <a name="storage"></a>Penyimpanan

* Memperbaiki #14138: Membuat beberapa izin opsional

## <a name="july-14-2020"></a>14 Juli 2020

Versi 2.9.0

### <a name="acr"></a>Azure Container Registry

* Tangani tautan artefak log dari Registry ke streaming log
* Menghentikan perintah helm2

### <a name="aks"></a>AKS

* `az aks create`: menambahkan --enable-aad argumen
* `az aks update`: menambahkan --enable-aad argumen

### <a name="apim"></a>APIM

* Menambahkan perintah umum az apim api

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan contoh untuk menggunakan --fields dalam revisi appconfig

### <a name="appservice"></a>AppService

* `az functionapp create`: Menambahkan dukungan untuk Java 11 dan Powershell 7. Menambahkan Dukungan API Stacks.
* Memperbaiki #14208 pembuatan aplikasi multi-kontainer gagal
* Memperbaiki pembuatan aplikasi web az - gunakan tumpukan runtime hardcoded

### <a name="arm"></a>ARM

* `az resource tag`: Memperbaiki masalah penandaan sumber daya dengan jenis sumber daya `Microsoft.ContainerInstance/containerGroups`

### <a name="compute"></a>Compute

* Disk versi Bump 01-05-2020, hitung 01-06-2020
* Enkripsi ganda dari set enkripsi disk
* `az vmss update`: mendukung menentukan gambar penyewa silang.
* `az sig image-version create`: mendukung menentukan gambar penyewa silang.
* vm/vmss create: Enkripsi cache & data-in-transit untuk disk OS/Data dan disk temp untuk Mesin Virtual & VMSS
* Menambahkan operasi simulasi-pengusiran untuk Mesin Virtual dan VMSS

### <a name="cosmosdb"></a>CosmosDB

* Fitur terbaru: Autoscale, IpRules, EnableFreeTier, dan EnableAnalyticalStorage

### <a name="eventgrid"></a>EventGrid

* Menambahkan dukungan CLI untuk pratinjau 01-04-2020 dan tandai fitur pratinjau dengan is_Preview=True

### <a name="find"></a>Cari

* Memperbaiki #14094 az find Memperbaiki Kueri gagal saat tidak masuk dan saat telemetri dinonaktifkan

### <a name="hdinsight"></a>HDInsight

* Menambahkan dua perintah untuk mendukung fitur reboot node hdinsight

### <a name="monitor"></a>Monitor

* Menghapus tanda pratinjau untuk perintah di bawah ruang kerja Log Analytics
* `az monitor diagnostic-settings subscription`: Mendukung pengaturan diagnosis untuk berlangganan
* `az monitor metrics`: mendukung ',' dan '|' dalam nama metrik
* `az monitor log-analytics workspace data-export`: mendukung ekspor data analitik log

### <a name="network"></a>Jaringan

* `az network application-gateway frontend-ip update`: Menghentikan parameter --public-ip-address
* Bump jaringan biru-mgmt ke 11.0.0
* `az network express-route gateway connection`: mendukung konfigurasi perutean
* `az network virtual-appliance`: Mendukung alat virtual jaringan Azure.
* Application Gateway mendukung fitur tautan pribadi

### <a name="policyinsights"></a>PolicyInsights

* `az policy state`: menambahkan perintah trigger-scan untuk memicu evaluasi kepatuhan kebijakan
* `az policy state list`: mengekspos versi entitas kebijakan di setiap catatan kepatuhan

### <a name="profile"></a>Profil

* `az account get-access-token`: Tampilkan expiredOn untuk Identitas Terkelola

### <a name="rdbms"></a>RDBMS

* Mendukung versi TLS Minimum
* Menambahkan Enkripsi Infrastruktur untuk Azure Postgres dan MySQL

### <a name="security"></a>Keamanan

* Menambahkan perintah allow_connections
* Menambahkan perintah pengerasan jaringan adaptif
* Menambahkan perintah adaptif_application_controls
* Penambahan az security iot-solution/ iot-alerts/iot-recommendations/iot-analytics REST ke Azure CLI
* Menambahkan CLI kepatuhan peraturan

### <a name="signalr"></a>SignalR

* Menambahkan fitur termasuk mengelola koneksi titik akhir privat, aturan jaringan, dan hulu

### <a name="sql"></a>SQL

* `az sql mi create`, `az sql mi update`: Menambahkan parameter `--tags` untuk mendukung penandaan sumber daya
* `az sql mi failover`: Mendukung failover dari titik primer atau sekunder

### <a name="storage"></a>Penyimpanan

* `az storage account create/update`: Menambahkan --allow-blob-public-access untuk mengizinkan atau melarang akses publik untuk blob dan kontainer
* `az storage account create/update`: Menambahkan `--min-tls-version` untuk mendukung pengaturan versi TLS minimum yang diizinkan pada permintaan ke penyimpanan.
* Menghapus kredensial token check-in
* Memperbaiki nama akun penyimpanan dalam contoh

### <a name="webapp"></a>Webapp

* Perbaikan bug: az webapp log deployment show - kembalikan log penyebaran alih-alih metadata log
* Perbaikan bug: az webapp vnet-integration add - perbaiki penanganan kesalahan jika nama vnet buruk, dukung ID sumber daya vnet

## <a name="june-23-2020"></a>23 Juni 2020

Versi 2.8.0

### <a name="acr"></a>Azure Container Registry

* Menambahkan dukungan untuk penonaktifan titik akhir wilayah/penonaktifan perutean
* [BREAKING CHANGE] `az acr login --expose-token` tidak menerima nama pengguna dan sandi

### <a name="acs"></a>ACS

* Menghapus kluster pribadi dan API pratinjau 27-10-2019

### <a name="aks"></a>AKS

* Mendukung --yes untuk az aks upgrade
* Kembalikan "ubah vm sku default ke Standard_D2s_v3 (#13541)"
* Menambahkan "az aks update --uptime-sla"
* Memperbaiki kesalahan ketik di perintah pembaruan az aks
* Ubah untuk mendukung 0 kumpulan agen node dan blokir skala manual untuk kumpulan yang diaktifkan CAS
* Memperbaiki kesalahan ketik di VirtualMachineScaleSets dan perbarui referensi ke versi Kubernetes

### <a name="ams"></a>AMS

* CHANGE teks bantuan untuk parameter "--expiry".

### <a name="appservice"></a>AppService

* `az webapp log deployment show`: Tampilkan log penyebaran terbaru, atau log penyebaran dari penyebaran tertentu jika id penyebaran ditentukan
* `az webapp log deployment list`: Daftar log penyebaran yang tersedia
* Memperbaiki: Kesalahan permukaan ketika nama webapp tidak valid diberikan
* Memperbaiki #13261 dan runtime daftar aplikasi web menggunakan daftar statis hingga API Tumpukan Tersedia yang baru tersedia
* `az appservice ase create`: Memperbaiki masalah pembuatan #13361
* `az appservice ase list-addresses`: Memperbaiki perubahan SDK #13140.
* Memperbaiki pembuatan webapp/slot untuk Windows Containers
* `az webapp auth update`: Menambahkan parameter opsional untuk memperbarui versi waktu proses
* Daftar dukungan, hapus, setujui, dan tolak koneksi titik akhir privat untuk aplikasi web di CLI
* Memperbaiki #13888 : Menambahkan dukungan Static WebApps: perintah get, list, create
* Pesan kesalahan yang ditingkatkan untuk Koneksi Terowongan SSH

### <a name="arm"></a>ARM

* `az tag`: Menambahkan contoh untuk -h
* `az deployment group/sub what-if`: Menambahkan parameter --exclude-change-types/-x.
* `az deployment group/sub/mg/tenant create`: Menambahkan parameter --what-if-exclude-change-types/-x.
* `az deployment group/sub/mg/tenant validate`: Tampilkan pesan kesalahan dalam format yang lebih baik.
* `az group export`: Menambahkan parameter baru `--skip-resource-name-params` dan `--skip-all-params` untuk mendukung parameterisasi lewati
* Menambahkan fitur az batalkan pendaftaran api

### <a name="aro"></a>ARO

* Menambahkan Publik, Pribadi ke params untuk bantuan dengan visibilitas masuk/apiserver

### <a name="batch"></a>Batch

* `az batch account create`: Menambahkan parameter baru `--public-network-access`
* `az batch account create`: Menambahkan parameter baru `--identity-type`
* `az batch account set`: Menambahkan parameter baru `--identity-type`
* [BREAKING CHANGE] az batch pool create: Saat membuat kumpulan menggunakan gambar khusus, properti --image dari sekarang hanya dapat merujuk ke gambar Galeri Gambar Bersama.
* [BREAKING CHANGE] az batch pool create: Saat membuat kumpulan dengan opsi --json-file dan menetapkan NetworkConfiguration, properti publicIPs telah dipindahkan ke properti baru publicIPAddressConfiguration. Properti baru ini juga mendukung properti ipAddressProvisioningType baru yang menentukan bagaimana kumpulan harus mengalokasikan IP dan properti publicIPs yang memungkinkan konfigurasi daftar sumber daya IP Publik untuk digunakan jika ipAddressProvisioningType diatur ke UserManaged
* `az network private-link-resource`: Menambahkan dukungan untuk sumber daya Microsoft.Batch batchAccount
* `az network private-endpoint-connection`: Menambahkan dukungan untuk sumber daya Microsoft.Batch batchAccount

### <a name="cdn"></a>CDN

* `az cdn custom-domain enable-https`: Menambahkan dukungan BYOC.
* `az cdn custom-domain enable-https`: Memperbaiki pengaktifan HTTPS khusus dengan sertifikat terkelola CDN untuk Standard_Verizon dan Standard_Microsoft SKU.

### <a name="cognitive-services"></a>Cognitive Services

* [BREAKING CHANGE] `az cognitiveservices account` sekarang memiliki struktur terpadu untuk semua perintah.
* `az cognitiveservices account identity`: Menambahkan manajemen identitas untuk Cognitive Services.

### <a name="compute"></a>Compute

* `az image builder`: Meningkatkan versi API ke 14-02-2020
* `az image builder create`: Menambahkan `--identity` untuk mendukung konfigurasi identitas
* `az image builder customizer add`: Mendukung penyesuai pembaruan Windows
* Perintah baru `az image builder cancel`
* Tampilkan peringatan saat pengguna menerapkan VMSS yang disematkan ke versi gambar tertentu, bukan versi terbaru

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb`: Menambahkan perintah yang ada ke basis data dan grup kontainer
* Izinkan pembuatan koleksi tetap

### <a name="eventhub"></a>EventHub

* `az eventhubs namespace create` : Menambahkan parameter identitas terkelola

### <a name="extension"></a>Extensi

* Menambahkan --versi ke dukungan untuk menginstal dari versi tertentu
* Aktifkan ekstensi CLI untuk menyertakan paket di ruang nama 'biru'

### <a name="iot-hub"></a>Iot Hub

* [BREAKING CHANGE] pekerjaan hub utama: Menghapus perintah pekerjaan yang tidak digunakan lagi

### <a name="keyvault"></a>Az.KeyVault

* `az keyvault key import`: Mendukung pengimporan dari string melalui dua parameter baru.
* Mendukung enkripsi dan dekripsi string/byte dengan kunci tersimpan

### <a name="monitor"></a>Monitor

* Mendukung tanpa menunggu pembuatan kluster
* `az monitor log-analytics workspace saved-search`: Mendukung perintah baru untuk pencarian tersimpan

### <a name="network"></a>Jaringan

* `az network application-gateway address-pool update`: Memperbaiki pesan bantuan dan menambahkan contoh.
* `az network vnet create`: Mendukung --nsg argumen
* `az network lb address-pool`: Mendukung membuat kumpulan backend lb dengan alamat backend.
* `az network application-gateway address-pool`: Memperbaiki untuk --tambahkan argumen

### <a name="rbac"></a>RBAC

* `az ad sp create-for-rabc`: Mendukung nama dengan spasi, garis miring, dan garis miring terbalik
* `az ad sp create-for-rbac`: Memperbaiki pesan kesalahan saat pengguna menentukan cakupan yang tidak valid

### <a name="security"></a>Keamanan

* Menambahkan perintah penilaian keamanan

### <a name="sql"></a>SQL

* `az sql db ltr-policy/ltr-backup`: perbarui/tampilkan kebijakan penyimpanan jangka panjang, tampilkan/hapus cadangan penyimpanan jangka panjang, pulihkan cadangan penyimpanan jangka panjang

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah autentikasi untuk mendukung dapatkan token untuk --subscription
* `az storage remove`: Memperbaiki masalah #13459 untuk memunculkan pengecualian kegagalan operasi
* Memperbaiki masalah #13012, #13632 dan #13657 untuk menghapus argumen yang tidak digunakan perintah terkait generate-sas
* `az storage logging update`: Menambahkan centang untuk versi logging
* `az storage blob show`: Menambahkan lebih banyak properti untuk blob dengan track 2 SDK
* Memperbaiki #13708: Memperbaiki pesan peringatan kredensial
* `az storage share-rm create/update`: Menambahkan protokol NFS dan dukungan akar squash
* `az storage account create`: Menambahkan dukungan untuk enkripsi ganda
* [BREAKING CHANGE] `az storage blob/container/file/share/table/queue generate-sas`: buat --kedaluwarsa dan --izin diperlukan
* `az storage blob set-tier`: Migrasi ke Track 2 untuk mendukung pengaturan prioritas rehidrasi

## <a name="june-02-2020"></a>02 Juni 2020

Versi 2.7.0

### <a name="acr"></a>Azure Container Registry

* Memperbaiki kesalahan ketik dalam pesan kesalahan pembuatan token

### <a name="aks"></a>AKS

* Ubah vm sku default ke Standard_D2s_v3
* Memperbaiki pembuatan penetapan peran untuk kluster MSI plus subnet khusus

### <a name="appservice"></a>AppService

* Memperbaiki #12739 az appservice list-locations menampilkan beberapa lokasi yang tidak valid

### <a name="arm"></a>ARM

* `az deployment`: Memperbaiki masalah #13159 dari pesan JSON yang salah setelah menghapus komentar dan mengompres
* `az resource tag`: Memperbaiki masalah #13255 penandaan sumber daya dengan jenis sumber daya `Microsoft.ContainerRegistry/registries/webhooks`
* Meningkatkan contoh untuk modul sumber daya

### <a name="aro"></a>ARO

* Ubah CLIError untuk mengoreksi tanda untuk --worker-vm-disk-size-gb

### <a name="eventhub"></a>EventHub

* Perbaikan untuk masalah #12406 Argumen --capture-interval tidak memperbarui "intervalInSeconds"

### <a name="hdinsight"></a>HDInsight

* Ubah get_json_object menjadi shell_safe_json_parse

### <a name="monitor"></a>Monitor

* `az monitor metrics alert`: sempurnakan beberapa pesan bantuan
* `az monitor diagnostic-settings create`: mendukung --ekspor-ke-argumen khusus sumber daya
* Dukung pemulihan ruang kerja LA

### <a name="network"></a>Jaringan

* `az network dns zone`: mendukung - karakter
* `az network vpn-connection ipsec-policy`: ubah --sa-lifetime dan --sa-max-size ke nilai yang lebih besar dalam contoh
* Bump jaringan hingga 01-04-2020
* `az network private-endpoint-connection`: mendukung kisi acara
* `az network express-route list-route-tables`: emperbaiki bug yang tidak dapat mencantumkan rute sebagai tabel

### <a name="packaging"></a>Pengemasan

* Menambahkan Paket Fokus Ubuntu

### <a name="rbac"></a>RBAC

* `az ad sp credential reset`: ubah pembuatan kredensial untuk menghindari karakter khusus yang merepotkan

### <a name="redis"></a>Redis

* Memperbaiki #13529: Mengubah dokumentasi parameter enable_non_ssl_port

### <a name="storage"></a>Penyimpanan

* `az storage copy`: Menambahkan parameter `--follow-symlinks` untuk mendukung symlink
* Aktifkan konteks lokal untuk akun penyimpanan
* `az storage logging`: Memperbaiki masalah #11969 untuk memperbaiki pesan kesalahan

## <a name="may-19-2020"></a>19 Mei 2020

Versi 2.6.0

### <a name="acr"></a>Azure Container Registry

* Menambahkan batas waktu default 5 menit untuk setiap permintaan ke ACR
* Mendukung menonaktifkan akses jaringan publik
* `az acr token create`: mengekspos --days argumen
* `az acr import`: terima nilai argumen --source yang berisi login di nama server melalui koreksi akhir klien

### <a name="acs"></a>ACS

* Perbaikan bug: hapus pembersihan bidang untuk bidang yang tidak ada lagi

### <a name="aks"></a>AKS

* Memperbarui konteks bantuan perintah uptime-sla
* Menghapus pemeriksaan jangkauan untuk memperbarui hitungan min untuk penskala otomatis
* Memperbaiki cli itu tidak gagal ketika pengguna hanya menentukan kata sandi Windows

### <a name="ams"></a>AMS

* `az ams transform create`: Menambahkan kemampuan untuk membuat transformasi dengan preset FaceDetector
* `az ams content-key-policy create` : Menambahkan kemampuan untuk membuat kebijakan kunci konten FairPlay dengan konfigurasi persewaan offline

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Perbaikan bug untuk nilai kunci daftar dengan bidang

### <a name="appservice"></a>AppService

* `az functionapp create`: AzureWebJobsDashboard hanya akan diatur jika Application Insights dinonaktifkan
* Memperbaiki #10664- Integrasi VNet - Pemeriksaan Lokasi Masalah & perbaikan #13257- az webapp gagal saat RG perlu dibuat
* `az webapp|functionapp config ssl import`: Mencari key vault di seluruh grup sumber daya dalam langganan dan meningkatkan bantuan dan contoh.
* Konteks lokal onboard untuk layanan aplikasi

### <a name="arm"></a>ARM

* `az deployment`: Memperbaiki masalah bahwa tautan template tidak akan dikembalikan saat menyebarkan atau memvalidasi template-uri
* `az deployment`: Memperbaiki masalah bahwa penyebaran/validasi tidak mendukung karakter yang disandikan secara khusus
* `az deployment sub/group what-if`: Memperbaiki perataan larik dan penanganan kesalahan
* `az deployment operation`: Ubah informasi usang

### <a name="aro"></a>ARO

* Menambahkan contoh ke az aro buat, daftar, daftar kredensial, tampilkan, hapus
* Menambahkan fungsi generate_random_id

### <a name="backup"></a>Cadangan

* Izinkan FriendlyName dalam mengaktifkan perlindungan untuk perintah AzureFileShare
* Memperbaiki di Perintah pemulihan-disk IaasVM
* Menambahkan "MAB" BackupManagementType ke perintah daftar item
* Menambahkan dukungan untuk mencoba kembali pembaruan kebijakan untuk item yang gagal.
* Menambahkan fungsionalitas Perlindungan Lanjutkan untuk Mesin Virtual Azure
* Menambahkan dukungan untuk menentukan ResourceGroup guna menyimpan instantRP selama Kebijakan Buat atau Ubah

### <a name="ci"></a>CI

* Mendukung flake8 3.8.0

### <a name="compute"></a>Compute

* Perintah baru az vm auto-shutdown
* `az vm list-skus`: Memperbarui perilaku --zone, kembalikan semua jenis skus sekarang

### <a name="core"></a>Core

* Memperbarui status aktif/nonaktif konteks lokal ke tingkat pengguna global

### <a name="extension"></a>Extensi

* `az extension add`: Menambahkan --system untuk mengaktifkan pemasangan ekstensi di jalur sistem
* Dukung .egg-info untuk menyimpan metadata ekstensi tipe roda

### <a name="iot"></a>IoT

* `az iot`: Memperbarui modul perintah IoT terlebih dahulu menjalankan pesan kesadaran ekstensi ke ID modern yang akurat dan tidak usang `azure-iot`.

### <a name="iot-hub"></a>IoT Hub

* Dukungan untuk perintah API dan Isolasi Jaringan 1-3 2020

### <a name="netappfiles"></a>NetAppFiles

* `az volume create`: Menambahkan snapshot-id sebagai parameter untuk membuat volume. Ini akan memungkinkan pengguna membuat volume dari snapshot yang ada.

### <a name="network"></a>Jaringan

* Memperbaiki nilai ttl berubah tidak diinginkan untuk dns add-record
* `az network public-ip create`: Memberi tahu pelanggan tentang perubahan penting yang akan datang
* Mendukung perintah umum untuk skenario tautan pribadi
* `az network private-endpoint-connection`: Mendukung jenis mysql, postgres, dan mariadb
* `az network private-endpoint-connection`: Mendukung jenis cosmosdb
* `az network private-endpoint`: hentikan --group-id dan alihkan ke --group-id

### <a name="output"></a>Output

* Tampilkan instruksi pembaruan di temukan, umpan balik, dan --help

### <a name="packaging"></a>Pengemasan

* Bangun paket MSI/Homebrew dengan dependensi yang diselesaikan dari requirements.txt

### <a name="rbac"></a>RBAC

* `az ad sp credential reset`: memperbaiki pembuatan kredensial yang lemah

### <a name="storage"></a>Penyimpanan

* `az storage account file-service-properties update/show`: Menambahkan Dukungan Properti File untuk Akun Penyimpanan
* `az storage container create`: Memperbaiki #13373 dengan menambahkan validator untuk akses publik
* Menambahkan dukungan ADLS Gen2 track2
* `az storage blob sync`: Mendukung `--connection-string`
* `az storage blob sync`: Memperbaiki pesan kesalahan yang salah ketika azcopy tidak dapat menemukan lokasi pemasangan

## <a name="april-30-2020"></a>30 April 2020

Versi 2.5.1

### <a name="acr"></a>Azure Container Registry

* `az acr check-health`: Memperbaiki "DOCKER_PULL_ERROR" di Windows

### <a name="compute"></a>Compute

* `az vm list-ip-addresses`: Penanganan kesalahan
* Memperbaiki bug dari vm create jika endpoint_vm_image_alias_doc tidak diatur di profil cloud
* `az vmss create`: Menambahkan --os-disk-size-gb

### <a name="cosmos-db"></a>Cosmos DB

* `az cosmosdb create/update`: menambahkan --enable-public-network support

### <a name="extension"></a>Extensi

* Memperbaiki pemuatan metadata yang salah untuk ekstensi tipe roda

### <a name="packaging"></a>Pengemasan

* Menambahkan skrip az untuk Git Bash/Cygwin di Windows

### <a name="sql"></a>SQL

* `az sql instance-pool`: Menambahkan grup perintah kumpulan instance

### <a name="storage"></a>Penyimpanan

* Meningkatkan paket penyimpanan Azure-multiapi ke 0.3.0
* Dukung GZRS untuk pembuatan dan pembaruan akun penyimpanan
* `az storage account failover`: Menambahkan dukungan untuk failover akun penyimpanan grs/gzrs
* `az storage blob upload`: Menambahkan parameter --encryption-scope untuk mendukung penetapan informasi cakupan enkripsi

## <a name="april-28-2020"></a>28 April 2020

Versi 2.5.0

### <a name="acs"></a>ACS

* [BREAKING CHANGE] dengan openshift buat: Menghapus parameter --vnet-peer.
* `az openshift create`: menambahkan tanda untuk mendukung kluster pribadi.
* `az openshift`: meningkatkan versi ke `2019-10-27-preview` versi API.
* `az openshift`: menambahkan perintah `update`.

### <a name="aks"></a>AKS

* `az aks create`: Menambahkan dukungan untuk Windows

### <a name="appservice"></a>AppService

* `az webapp deployment source config-zip`: Menghapus sleep setelah request.get()

### <a name="arm"></a>ARM

* Menambahkan penyebaran template What-If perintah

### <a name="aro"></a>ARO

* `az aro`: Memperbaiki output tabel

### <a name="ci"></a>CI

* Pitest onboard dan hidung yang tidak digunakan lagi untuk Tes Otomasi

### <a name="compute"></a>Compute

* `az vmss disk detach`: memperbaiki disk data masalah NoneType
* `az vm availability-set list`: Mendukung menampilkan daftar Mesin Virtual
* `az vm list-skus`: Memperbaiki masalah tampilan format tabel

### <a name="keyvault"></a>Az.KeyVault

* Menambahkan parameter baru `--enable-rbac-authorization` saat membuat atau memperbarui

### <a name="monitor"></a>Monitor

* Mendukung fitur CMK LA kluster
* `az monitor log-analytics workspace linked-storage`: mendukung fitur BYOS

### <a name="network"></a>Jaringan

* `az network security-partner`: mendukung penyedia mitra keamanan

### <a name="privatedns"></a>Privatedns

* Menambahkan fitur di zona DNS pribadi untuk mengimpor file zona ekspor

## <a name="april-21-2020"></a>21 April 2020

Versi 2.4.0

### <a name="acr"></a>Azure Container Registry

* `az acr run --cmd`: nonaktifkan penggantian direktori kerja
* Mendukung titik akhir data khusus

### <a name="aks"></a>AKS

* `az aks list -o table` harus menampilkan privateFqdn sebagai fqdn untuk kluster pribadi
* Menambahkan --uptime-sla
* Memperbarui paket layanan kontainer
* Menambahkan dukungan IP publik node
* Memperbaiki kesalahan ketik pada perintah bantuan

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Selesaikan referensi brankas kunci untuk daftar kv dan perintah ekspor
* Perbaikan bug untuk nilai kunci daftar

### <a name="appservice"></a>AppService

* `az functionapp create`: Mengubah cara linuxFxVersion diatur untuk aplikasi fungsi dotnet linux. Ini harus memperbaiki bug yang mencegah aplikasi konsumsi dotnet linux dibuat
* [BREAKING CHANGE] `az webapp create`: memperbaiki untuk mempertahankan AppSettings yang ada dengan az webapp create
* [BREAKING CHANGE] `az webapp up`: memperbaiki untuk membuat RG untuk perintah az webapp up saat menggunakan flag -g
* [BREAKING CHANGE] `az webapp config`: memperbaiki untuk menampilkan nilai untuk output non-JSON dengan daftar string koneksi konfigurasi webapp az

### <a name="arm"></a>ARM

* `az deployment create/validate`: Menambahkan parameter `--no-prompt` untuk mendukung melewatkan prompt parameter yang hilang untuk template ARM
* `az deployment group/mg/sub/tenant validate`: Mendukung komentar dalam file parameter penyebaran
* `az deployment`: Menghapus `is_preview` untuk parameter `--handle-extended-json-format`
* `az deployment group/mg/sub/tenant cancel`: Mendukung pembatalan penyebaran untuk template ARM
* `az deployment group/mg/sub/tenant validate`: Memperbaiki pesan kesalahan saat verifikasi penyebaran gagal
* `az deployment-scripts`: Menambahkan perintah baru untuk DeploymentScripts
* `az resource tag`: Menambahkan parameter `--is-incremental` untuk mendukung penambahan tag ke sumber daya secara bertahap

### <a name="aro"></a>ARO

* `az aro`: Menambahkan modul perintah Azure RedHat OpenShift V4 aro

### <a name="batch"></a>Batch

* Memperbarui Batch API

### <a name="compute"></a>Compute

* `az sig image-version create`: Menambahkan jenis akun penyimpanan Premium_LRS
* `az vmss update`: Memperbaiki masalah pembaruan pemberitahuan penghentian
* `az vm/vmss create`: Menambahkan dukungan untuk versi gambar khusus
* SIG API Versi 2019-12-01
* `az sig image-version create`: Menambahkan --target-region-encryption
* Memperbaiki tes gagal saat dijalankan secara serial karena nama keyvault diduplikasi dalam cache di-momery global

### <a name="cosmosdb"></a>CosmosDB

* Mendukung `az cosmosdb private-link-resource/private-endpoint-connection`

### <a name="iot-central"></a>IoT Pusat

* Menghentikan `az iotcentral`
* Menambahkan `az iot central` modul perintah

### <a name="monitor"></a>Monitor

* Mendukung skenario tautan pribadi untuk monitor
* Memperbaiki cara mengejek yang salah di test_monitor_general_operations.py

### <a name="network"></a>Jaringan

* Menghentikan sku untuk perintah pembaruan ip publik
* `az network private-endpoint`: Mendukung grup zona dns pribadi
* Aktifkan fitur konteks lokal untuk parameter vnet/subnet
* Memperbaiki contoh penggunaan yang salah di test_nw_flow_log_delete

### <a name="packaging"></a>Pengemasan

* Menghapus dukungan untuk paket Ubuntu/Disco

### <a name="rbac"></a>RBAC

* `az ad app create/update`: mendukung --opsional-klaim sebagai parameter

### <a name="rdbms"></a>RDBMS

* Menambahkan perintah administrator direktori aktif Azure untuk PostgreSQL dan MySQL

### <a name="service-fabric"></a>Service Fabric

* Memperbaiki #12891: `az sf application update --application-parameters` menghapus parameter lama yang tidak ada dalam permintaan
* Memperbaiki #12470 az sf membuat kluster, memperbaiki bug dalam pembaruan daya tahan dan keandalan dan menemukan vmss dengan benar melalui kode yang diberikan nama jenis node

### <a name="sql"></a>SQL

* Menambahkan `az sql mi op list`, `az sql mi op get`, `az sql mi op cancel`
* `az sql midb`: perbarui/tampilkan kebijakan penyimpanan jangka panjang, tampilkan/hapus cadangan penyimpanan jangka panjang, pulihkan cadangan penyimpanan jangka panjang

### <a name="storage"></a>Penyimpanan

* Meningkatkan penyimpanan Azure-mgmt ke 9.0.0
* `az storage logging off`: Mendukung mematikan pencatatan untuk akun penyimpanan
* `az storage account update`: Aktifkan kunci yang diputar otomatis untuk CMK
* `az storage account encryption-scope create/update/list/show`: Menambahkan dukungan untuk menyesuaikan cakupan enkripsi
* `az storage container create`: Menambahkan --default-encryption-scope dan --deny-encryption-scope-override untuk mengatur cakupan enkripsi untuk tingkat kontainer

### <a name="survey"></a>survei

* Menambahkan sakelar untuk mematikan tautan survei

## <a name="april-01-2020"></a>01 April 2020

Versi 2.3.1

### <a name="acr"></a>Azure Container Registry

* Memperbaiki versi Azure-mgmt-kontainerregistry yang salah untuk Linux

### <a name="profile"></a>Profil

* az login: Perbaiki kegagalan login dengan profil cloud selain `latest`

## <a name="march-31-2020"></a>31 Maret 2020

Versi 2.3.0

### <a name="acr"></a>Azure Container Registry

* 'az acr task update': pengecualian penunjuk nol
* `az acr import`: Ubah bantuan dan pesan kesalahan untuk memperjelas penggunaan --source dan --registry
* Menambahkan validator untuk argumen 'registry_name'
* `az acr login`:Menghapus tanda pratinjau pada '--expose-token'
* [BREAKING CHANGE] 'az acr task create/update' Parameter cabang dihapus
* 'az acr task update' Pelanggan sekarang dapat memperbarui konteks, git-token, dan atau pemicu satu per satu
* 'az acr agentpool': fitur baru

### <a name="aks"></a>AKS

* Memperbaiki apiServerAccessProfile saat memperbarui --api-server-authorized-ip-ranges
* pembaruan aks: Mengganti IP keluar dengan nilai input saat memperbarui
* Jangan buat SPN untuk kluster MSI dan dukung lampirkan acr ke kluster MSI

### <a name="ams"></a>AMS

* Fix #12469: menambahkan Fairplay content-key-policy gagal karena masalah dengan parameter 'ask'

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan --skip-keyvault untuk ekspor kv

### <a name="appservice"></a>AppService

* Memperbaiki #12509: Menghapus tag ke az webapp up secara default
* az functionapp create: Memperbarui --runtime-version help menu dan menambahkan peringatan saat pengguna menentukan --runtime-version untuk dotnet
* az functionapp create: Memperbarui cara javaVersion diatur untuk aplikasi fungsi Windows

### <a name="arm"></a>ARM

* az penyebaran buat/validasi: Gunakan --handle-extended-json-format secara default
* az lock create: Menambahkan contoh pembuatan subsumber daya dalam dokumentasi bantuan
* az penyebaran {group/mg/sub/tenant} daftar: Mendukung pemfilteran status provisioning
* penyebaran az: Memperbaiki bug parse untuk komentar di bawah argumen terakhir

### <a name="backup"></a>Cadangan

* Menambahkan beberapa file mengembalikan kemampuan
* Menambahkan dukungan untuk Mencadangkan Disk OS saja
* Menambahkan parameter restore-as-unmanaged-disk untuk menentukan pemulihan yang tidak dikelola

### <a name="compute"></a>Compute

* az vm create: Menambahkan NONE opsi --nsg-rule
* az vmss buat/perbarui: Menghapus tag pratinjau perbaikan otomatis vmss
* pembaruan az vm: Mendukung --ruang kerja
* Memperbaiki bug dalam kode inisialisasi VirtualMachineScaleSetExtension
* Meningkatkan versi VMaccessAgent ke 2.4
* az vmss set-orchestration-service-state: mendukung status layanan orkestrasi set vmss
* Meningkatkan versi API disk ke 01-11-2019
* az disk buat: menambahkan --disk-iops-read-only, --disk-mbps-read-only, --max-shares, --image-reference, --image-reference-lun, --gallery-image -referensi, --gallery-image-reference-lun

### <a name="cosmos-db"></a>Cosmos DB

* Memperbaiki opsi --type yang hilang untuk pengalihan penghentian

### <a name="docker"></a>Docker

* Memperbarui ke Alpine 3.11 dan Python 3.6.10

### <a name="extension"></a>Extensi

* Izinkan untuk memuat ekstensi di jalur sistem melalui paket

### <a name="hdinsight"></a>HDInsight

* (az hdinsight create :) Mendukung pelanggan menentukan versi tls minimal yang didukung dengan menggunakan parameter `--minimal-tls-version`. Nilai yang diizinkan adalah 1.0,1.1,1.2

### <a name="iot"></a>IoT

* Menambahkan pemilik kode
* az iot hub create : Ubah sku default ke S1 dari F1
* iot hub: Dukung IotHub di profil hibrid 01-03-2019

### <a name="iotcentral"></a>IoTCentral

* Memperbarui detail kesalahan, perbarui templat aplikasi default, dan pesan cepat

### <a name="keyvault"></a>Az.KeyVault

* Mendukung pencadangan/pemulihan sertifikat
* keyvault buat/perbarui: Mendukung --retention-days
* Tidak lagi menampilkan kunci/rahasia yang dikelola saat mendaftar
* az keyvault create: mendukung `--network-acls`, `--network-acls-ips` dan `--network-acls-vnets` untuk menentukan aturan jaringan saat membuat vault

### <a name="lock"></a>Kunci

* az lock delete fix bug: az lock delete tidak berfungsi di Microsoft.DocumentDB

### <a name="monitor"></a>Monitor

* az monitor clone: mendukung aturan metrik klon dari satu sumber daya ke sumber lainnya
* Memperbaiki IcM179210086: tidak dapat membuat peringatan metrik kustom untuk metrik Application Insights mereka

### <a name="netappfiles"></a>NetAppFiles

* az volume create: Izinkan volume perlindungan data menambahkan operasi replikasi: setujui, tunda, lanjutkan, status, hapus

### <a name="network"></a>Jaringan

* az network application-gateway waf-policy managed-rule rule-set add: mendukung Microsoft_BotManagerRuleSet
* acara log aliran pengamat jaringan: memperbaiki info yang salah
* mendukung nama host di pendengar gateway aplikasi
* az network nat gateway: mendukung buat sumber daya kosong tanpa ip publik atau awalan ip publik
* Mendukung pembuatan gateway vpn
* Mendukung `--if-none-match` di `az network dns record-set {} add-record`

### <a name="packaging"></a>Pengemasan

* Menghapus dukungan untuk python 3.5

### <a name="profile"></a>Profil

* az login: Tampilkan peringatan untuk kesalahan MFA

### <a name="rdbms"></a>RDBMS

* Menambahkan perintah manajemen kunci enkripsi data server untuk PostgreSQL dan MySQL

## <a name="march-10-2020"></a>10 Maret 2020

Versi 2.2.0

### <a name="acr"></a>Azure Container Registry

* Memperbaiki: `az acr login` salah memunculkan kesalahan
* Menambahkan perintah baru `az acr helm install-cli`
* Menambahkan tautan pribadi dan dukungan CMK
* Menambahkan perintah 'private-link-resource list'

### <a name="aks"></a>AKS

* Memperbaiki jelajah aks di cloud shell
* aks: Memperbaiki addon pemantauan dan kesalahan agentpool NoneType
* Menambahkan --nodepool-tags ke kumpulan node saat membuat kluster kubernetes biru
* Menambahkan --tags saat menambahkan atau memperbarui nodepool ke kluster
* aks buat: menambahkan `--enable-private-cluster`
* menambahkan --nodepool-labels saat membuat kluster kubernetes biru
* menambahkan --labels saat menambahkan nodepool baru ke kluster Azure kubernetes
* menambahkan yang hilang / di url dasbor
* Mendukung membuat kluster aks memungkinkan identitas terkelola
* az aks: Validasi plugin jaringan menjadi "Azure" atau "kubenet"
* az aks: Menambahkan dukungan kunci sesi iklan
* [BREAKING CHANGE] aks: mendukung perubahan msi untuk GF dan BF untuk omsagent (Pemantauan kontainer)(#1)
* az aks use-dev-spaces: Menambahkan opsi jenis titik akhir ke perintah use-dev-spaces untuk menyesuaikan titik akhir yang dibuat pada pengontrol Azure Dev Spaces

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Buka blokir menggunakan "kv set" untuk menambahkan referensi dan fitur keyvault ...

### <a name="appservice"></a>AppService

* az webapp create : Memperbaiki masalah saat menjalankan perintah dengan --runtime
* az functionapp deployment source config-zip: Menambahkan pesan kesalahan jika grup sumber daya atau nama fungsi tidak valid/tidak ada
* functionapp create: Memperbaiki pesan peringatan yang muncul dengan `functionapp create` hari ini yang mengutip bendera `--functions_version` tetapi secara keliru menggunakan `_` alih-alih `-` dalam nama bendera
* az functionapp create: Memperbarui cara linuxFxVersion dan nama gambar kontainer diatur untuk aplikasi fungsi linux
* az functionapp deployment source config-zip: Memperbaiki masalah yang disebabkan oleh pengaturan aplikasi mengubah kondisi balapan selama penyebaran zip, memberikan kesalahan 5xx selama penyebaran
* Memperbaiki #5720946: az webapp backup gagal menetapkan nama

### <a name="arm"></a>ARM

* az resource: Memperbaiki contoh modul resource
* az daftar penetapan kebijakan: Mendukung daftar penetapan kebijakan di lingkup Grup Manajemen
* Menambahkan `az deployment group` dan `az deployment operation group` untuk penyebaran template di grup sumber daya. Ini adalah duplikat dari `az group deployment` dan `az group deployment operation`
* Menambahkan `az deployment sub` dan `az deployment operation sub` untuk penyebaran template pada cakupan langganan. Ini adalah duplikat dari `az deployment` dan `az deployment operation`
* Menambahkan `az deployment mg` dan `az deployment operation mg` untuk penyebaran template di grup manajemen
* Menambahkan `az deployment tenant` dan `az deployment operation tenant` untuk penyebaran template di lingkup penyewa
* pembuatan penetapan kebijakan az: Menambahkan deskripsi ke parameter `--location`
* pembuatan penyebaran grup az: Menambahkan parameter `--aux-tenants` untuk mendukung penyewa lintas

### <a name="cdn"></a>CDN

* Menambahkan perintah CDN WAF

### <a name="compute"></a>Compute

* versi gambar az sig: menambahkan --data-snapshot-luns
* az ppg show: menambahkan --colocation-status untuk mengaktifkan pengambilan status colocation dari semua sumber daya dalam grup penempatan kedekatan
* az vmss buat/perbarui: dukung perbaikan otomatis
* [BREAKING CHANGE] az template gambar: mengganti nama template menjadi builder
* pembuat gambar az buat: menambahkan --image-template

### <a name="cosmos-db"></a>Cosmos DB

* Menambahkan prosedur tersimpan Sql, udf, dan pemicu cmdlet
* az cosmosdb create: menambahkan --key-uri untuk mendukung penambahan informasi enkripsi brankas kunci

### <a name="keyvault"></a>Az.KeyVault

* keyvault create: aktifkan soft-delete secara default

### <a name="monitor"></a>Monitor

* az monitor metrics alert create: mendukung `~` di `--condition`

### <a name="network"></a>Jaringan

* az network application-gateway rewrite-rule buat: dukung konfigurasi url
* az network dns zone import: --zone-name tidak akan peka huruf besar-kecil di masa mendatang
* az network private-endpoint/private-link-service: hapus label pratinjau
* benteng jaringan az: benteng pendukung
* az network vnet list-available-ips: daftar dukungan ip yang tersedia di vnet
* az network watcher flow-log buat/daftar/hapus/perbarui: menambahkan perintah baru untuk mengelola log aliran pengamat dan ekspos --location untuk mengidentifikasi pengamat secara eksplisit
* konfigurasi flow-log pengamat jaringan az: tidak digunakan lagi
* az network watcher flow-log show: mendukung --location dan --name untuk mendapatkan hasil berformat ARM, output berformat lama yang tidak digunakan lagi

### <a name="policy"></a>Kebijakan

* pembuatan penetapan kebijakan az: Memperbaiki bug yang secara otomatis menghasilkan nama penetapan kebijakan melebihi batas

### <a name="rbac"></a>RBAC

* az grup iklan tampilkan: perbaiki --nilai grup diperlakukan sebagai masalah ekspresi reguler

### <a name="rdbms"></a>RDBMS

* Bump versi SDK Azure-mgmt-rdbms ke 2.0.0
* az postgres private-endpoint-connection: mengelola koneksi titik akhir privat postgres
* az postgres private-link-resource: mengelola sumber daya tautan pribadi postgres
* az mysql private-endpoint-connection: mengelola koneksi titik akhir privat mysql
* az mysql private-link-resource: mengelola sumber daya tautan pribadi mysql
* az mariadb private-endpoint-connection: mengelola koneksi titik akhir privat mariadb
* az mariadb private-link-resource: mengelola sumber daya tautan pribadi mariadb
* Memperbarui Tes Titik Akhir Privat RDBMS

### <a name="sql"></a>SQL

* Sql midb Menambahkan: daftar-dihapus, show-deleted, update-retensi, show-retention
* (buat server sql:) Menambahkan tanda 'Aktifkan'/'Nonaktifkan' akses jaringan publik opsional ke pembuatan server sql
* (pembaruan server sql :) membuat beberapa perubahan yang dihadapi pelanggan
* Menambahkan properti minimal_tls_version untuk MI dan SQL DB

### <a name="storage"></a>Penyimpanan

* az storage blob delete-batch: Tanda `--dryrun` yang berperilaku tidak semestinya
* penambahan aturan jaringan akun penyimpanan az (perbaikan bug): operasi penambahan harus idempoten
* akun penyimpanan az buat/perbarui: Menambahkan dukungan Preferensi Perutean
* Meningkatkan versi penyimpanan Azure-mgmt ke 8.0.0
* az kekekalan kontainer penyimpanan buat: tambahkan --allow-protected-append-write parameter
* az daftar sumber daya tautan pribadi akun penyimpanan: Menambahkan dukungan ke daftar sumber daya tautan pribadi untuk akun penyimpanan
* az akun penyimpanan koneksi titik akhir privat setujui/tolak/tampilkan/hapus: Dukungan untuk mengelola koneksi titik akhir privat
* pembaruan akun penyimpanan blob-service-properties: menambahkan --enable-restore-policy dan --restore-days
* az penyimpanan blob restore: Menambahkan dukungan untuk memulihkan rentang blob

## <a name="february-18-2020"></a>18 Februari 2020

Versi 2.1.0

### <a name="acr"></a>Azure Container Registry

* Menambahkan argumen baru `--expose-token` untuk `az acr login`
* Memperbaiki output yang salah dari `az acr task identity show -n Name -r Registry -o table`
* az acr login: Lempar CLIError jika ada kesalahan yang dikembalikan oleh perintah docker

### <a name="acs"></a>ACS

* aks buat/perbarui: menambahkan `--vnet-subnet-id` validasi

### <a name="aladdin"></a>Aladin

* Parsing contoh yang dihasilkan ke dalam commands' _help.py

### <a name="ams"></a>AMS

* az ams adalah GA sekarang

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Revisi pesan bantuan untuk mengecualikan filter kunci/label yang tidak didukung
* Menghapus tag pratinjau untuk sebagian besar perintah tidak termasuk identitas terkelola dan tanda fitur
* Menambahkan kunci yang dikelola pelanggan saat memperbarui toko

### <a name="appservice"></a>AppService

* az webapp list-runtimes: Memperbaiki bug untuk daftar-runtimes
* Menambahkan az webapp|functionapp config ssl create
* Menambahkan dukungan untuk aplikasi fungsi v3 dan node 12

### <a name="arm"></a>ARM

* pembuatan penetapan kebijakan az: Memperbaiki pesan kesalahan saat parameter `--policy` tidak valid
* penyebaran grup az buat: Memperbaiki kesalahan "stat: jalur terlalu panjang untuk Windows" saat menggunakan file parameter.json besar

### <a name="backup"></a>Cadangan

* Perbaikan untuk alur pemulihan level item di OLR
* Menambahkan pemulihan sebagai dukungan file untuk SQL dan SAP Databases

### <a name="compute"></a>Compute

* vm/vmss/availability-set update: menambahkan --ppg untuk mengizinkan pembaruan ProximityPlacementGroup
* vmss buat: menambahkan --data-disk-iops dan --data-disk-mbps
* az vm host: Menghapus tag pratinjau untuk `vm host` dan `vm host group`
* [BREAKING CHANGE] Memperbaiki #10728: `az vm create`: membuat subnet secara otomatis jika vnet ditentukan dan subnet tidak ada
* Meningkatkan kekokohan daftar gambar vm

### <a name="eventhub"></a>Eventhub

* Dukungan Azure Stack untuk profil hibrid 01-03-2019

### <a name="keyvault"></a>Az.KeyVault

* az keyvault key create: menambahkan nilai baru `import` untuk parameter `--ops`
* az keyvault key list-versions: parameter dukungan `--id` untuk menentukan kunci
* Mendukung koneksi titik akhir privat

### <a name="network"></a>Jaringan

* Bertemu dengan jaringan biru-mgmt 9.0.0
* az network private-link-service update/create: support --enable-proksi-protocol
* Menambahkan fitur koneksi Monitor V2

### <a name="packaging"></a>Pengemasan

* [BREAKING CHANGE] Lepaskan dukungan untuk Python 2.7

### <a name="profile"></a>Profil

* Pratinjau: Menambahkan atribut baru `homeTenantId` dan `managedByTenants` ke akun langganan. Jalankan kembali `az login` agar perubahan diterapkan
* az login: Menampilkan peringatan saat langganan terdaftar dari lebih dari satu penyewa dan default ke penyewa pertama. Untuk memilih penyewa tertentu saat mengakses langganan ini, harap sertakan `--tenant` di `az login`

### <a name="role"></a>Peran

* az penetapan peran buat: Memperbaiki kesalahan yang menetapkan peran ke prinsipal layanan dengan nama tampilan menghasilkan HTTP 400

### <a name="sql"></a>SQL

* Memperbarui cmdlet Instance Terkelola SQL `az sql mi update` dengan dua parameter baru: tingkat dan keluarga

### <a name="storage"></a>Penyimpanan

* [BREAKING CHANGE] `az storage account create`: Ubah jenis akun penyimpanan default ke StorageV2

## <a name="february-04-2020"></a>04 Februari 2020

Versi 2.0.81

### <a name="acs"></a>ACS

* Menambahkan dukungan untuk mengatur port yang dialokasikan keluar dan waktu tunggu idle pada penyeimbang beban standar
* Memperbarui ke Versi API 2019-11-01

### <a name="acr"></a>Azure Container Registry

* [BREAKING CHANGE] `az acr delete` akan meminta
* [BREAKING CHANGE] 'az acr task delete' akan meminta
* Menambahkan grup perintah baru 'az acr taskrun show/list/delete' untuk manajemen taskrun

### <a name="aks"></a>AKS

* Setiap kluster mendapatkan prinsip layanan terpisah untuk meningkatkan isolasi

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Mendukung impor/ekspor referensi keyvault dari/ke layanan aplikasi
* Mendukung impor/ekspor semua label dari appconfig ke appconfig
* Validasi nama kunci dan fitur sebelum mengatur dan mengimpor
* Ekspos modifikasi sku untuk penyimpanan konfigurasi.
* Menambahkan grup perintah untuk identitas terkelola.

### <a name="appservice"></a>AppService

* Azure Stack: perintah permukaan di bawah profil hibrid 01-03-2019
* functionapp: Menambahkan kemampuan untuk membuat aplikasi fungsi Java di Linux

### <a name="arm"></a>ARM

* Memperbaiki masalah #10246: `az resource tag` crash saat parameter `--ids` yang diteruskan adalah ID grup sumber daya
* Memperbaiki masalah #11658: perintah `az group export` tidak mendukung parameter `--query` dan `--output`
* Memperbaiki masalah #10279: Kode keluar `az group deployment validate` adalah 0 saat verifikasi gagal
* Memperbaiki masalah #9916: Memperbaiki pesan kesalahan konflik antara tag dan kondisi filter lainnya untuk perintah `az resource list`
* Menambahkan parameter baru `--managed-by` untuk mendukung penambahan informasi managedBy untuk perintah `az group create`

### <a name="azure-red-hat-openshift"></a>Azure Red Hat OpenShift

* Menambahkan `monitor` subgrup untuk mengelola pemantauan Analisis Log di kluster Azure Red Hat OpensShift

### <a name="botservice"></a>BotService

* Memperbaiki masalah #11697: `az bot create` tidak idempotent
* Ubah tes koreksi nama untuk dijalankan hanya dalam mode Langsung

### <a name="cdn"></a>CDN

* Menambahkan dukungan untuk fitur rulesEngine
* Menambahkan grup perintah baru 'cdn endpoint rule' untuk mengelola aturan
* Memperbarui versi Azure-mgmt-cdn ke 4.0.0 untuk menggunakan versi api 2019-04-15

### <a name="deployment-manager"></a>Deployment Manager

* Menambahkan operasi daftar untuk semua sumber daya.
* Meningkatkan sumber daya langkah untuk jenis langkah baru.
* Memperbarui paket Azure-mgmt-deploymentmanager untuk menggunakan versi 0.2.0.

### <a name="iot"></a>IoT

* Menghentikan perintah 'IOT hub Job'.

### <a name="iot-central"></a>IoT Pusat

* Mendukung pembuatan/pembaruan aplikasi dengan nama sku baru ST0, ST1, ST2.

### <a name="key-vault"></a>Key Vault

* Menambahkan perintah baru `az keyvault key download` untuk mengunduh kunci.

### <a name="misc"></a>Lain-lain

* Memperbaiki #6371: Mendukung penyelesaian nama file dan variabel lingkungan di Bash

### <a name="network"></a>Jaringan

* Memperbaiki #2092: az network dns record-set add/remove: menambahkan peringatan saat record-set tidak ditemukan. Di masa mendatang, argumen tambahan akan didukung untuk mengonfirmasi pembuatan otomatis ini.

### <a name="policy"></a>Kebijakan

* Menambahkan perintah baru `az policy metadata` untuk mengambil sumber daya metadata kebijakan yang kaya
* `az policy remediation create`: Tentukan apakah kepatuhan harus dievaluasi ulang sebelum perbaikan dengan parameter `--resource-discovery-mode`

### <a name="profile"></a>Profil

* `az account get-access-token`: Menambahkan parameter `--tenant` untuk mendapatkan token penyewa secara langsung, tidak perlu menentukan langganan

### <a name="rbac"></a>RBAC

* [BREAKING CHANGE] Memperbaiki #11883: `az role assignment create`: cakupan kosong akan meminta kesalahan

### <a name="security"></a>Keamanan

* Menambahkan perintah baru `az atp show` dan `az atp update` untuk melihat dan mengelola pengaturan perlindungan ancaman lanjutan untuk akun penyimpanan.

### <a name="sql"></a>SQL

* `sql dw create`: tidak menggunakan parameter `--zone-redundant` dan `--read-replica-count`. Parameter ini tidak berlaku untuk DataWarehouse.
* [BREAKING CHANGE] `az sql db create`: Menghapus "WideWorldImportersStd" dan "WideWorldImportersFull" sebagai nilai yang diizinkan yang didokumentasikan untuk "az sql db create --sample-name". Database sampel ini akan selalu menyebabkan pembuatan gagal.
* Menambahkan perintah baru `sql db classification show/list/update/delete` dan `sql db classification recommendation list/enable/disable` untuk mengelola klasifikasi sensitivitas untuk database SQL.
* `az sql db audit-policy`: Perbaikan untuk tindakan dan grup audit kosong

### <a name="storage"></a>Penyimpanan

* Menambahkan grup perintah baru `az storage share-rm` untuk menggunakan penyedia sumber daya Microsoft.Storage untuk operasi pengelolaan berbagi file Azure.
* Memperbaiki masalah #11415: kesalahan izin untuk `az storage blob update`
* Integrasikan Azcopy 10.3.3 dan dukung Win32.
* `az storage copy`: Menambahkan parameter `--include-path`, `--include-pattern`, `--exclude-path` dan`--exclude-pattern`
* `az storage remove`: Ubah parameter `--inlcude` dan `--exclude` menjadi parameter `--include-path`, `--include-pattern`, `--exclude-path` dan`--exclude-pattern`
* `az storage sync`: Menambahkan parameter `--include-pattern`, `--exclude-path` dan`--exclude-pattern`

### <a name="servicefabric"></a>ServiceFabric

* Menambahkan perintah baru untuk mengelola aplikasi dan layanan.

## <a name="january-13-2020"></a>13 Januari 2020

Versi 2.0.80

### <a name="compute"></a>Compute

* pembaruan disk: Menambahkan --disk-encryption-set dan --encryption-type
* snapshot buat/perbarui: Menambahkan --disk-encryption-set dan --encryption-type

### <a name="storage"></a>Penyimpanan

* Meningkatkan versi penyimpanan Azure-mgmt ke 7.1.0
* `az storage account create`: Menambahkan `--encryption-key-type-for-table` dan `--encryption-key-type-for-queue` untuk mendukung Layanan Enkripsi Tabel dan Antrian

## <a name="january-07-2020"></a>07 Januari 2020

Versi 2.0.79

### <a name="acr"></a>Azure Container Registry

* [BREAKING CHANGE] Menghapus parameter '--os' untuk 'acr build', 'acr task create/update', 'acr run', dan 'acr pack'. Gunakan '--platform' sebagai gantinya.

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan dukungan untuk mengimpor/mengekspor flag fitur
* Menambahkan perintah baru 'az appconfig kv set-keyvault' untuk membuat referensi keyvault
* Mendukung berbagai konvensi penamaan saat mengekspor flag fitur ke file

### <a name="appservice"></a>AppService

* Memperbaiki masalah #7154: Memperbarui dokumentasi perintah <> untuk menggunakan backtick sebagai ganti tanda kutip tunggal
* Memperbaiki masalah #11287: webapp up: Secara default membuat aplikasi yang dibuat menggunakan 'harus 'SSL diaktifkan'
* Memperbaiki masalah #11592: Menambahkan bendera aplikasi web az untuk situs statis html

### <a name="arm"></a>ARM

* Memperbaiki `az resource tag`: Tag Vault Layanan Pemulihan tidak dapat diperbarui

### <a name="backup"></a>Cadangan

* Menambahkan perintah baru 'backup protection undelete' untuk mengaktifkan fitur soft-delete untuk beban kerja IaasVM
* Menambahkan parameter baru '--soft-delete-feature-state' untuk mengatur perintah properti cadangan
* Menambahkan dukungan pengecualian disk untuk beban kerja IaasVM

### <a name="compute"></a>Compute

* Memperbaiki `vm create` kegagalan di profil Azure Stack.
* vm monitor metrik definisi ekor/daftar: mendukung metrik kueri dan definisi daftar untuk vm.
* Menambahkan tindakan perintah pengajuan ulang baru untuk az vm

### <a name="hdinsight"></a>HDInsight

* Dukungan untuk membuat kluster Kafka dengan Kafka Rest Proxy
* Meningkatkan Azure-mgmt-hdinsight ke 1.3.0

### <a name="misc"></a>Lain-lain

* Menambahkan perintah pratinjau `az version show` untuk menampilkan versi modul dan ekstensi Azure CLI dalam format JSON secara default atau format yang dikonfigurasi oleh --output

### <a name="event-hubs"></a>Event Hubs

* [BREAKING CHANGE] Menghapus opsi status 'ReceiveDisabled' dari perintah 'az eventhubs eventhub update' dan 'az eventhubs eventhub create'. Opsi ini tidak valid untuk entitas Event Hub.

### <a name="service-bus"></a>Service Bus

* [BREAKING CHANGE] Menghapus opsi status 'ReceiveDisabled' dari perintah 'az servicebus topic create', 'az servicebus topic update', 'az servicebus queue create', dan 'az servicebus queue update'. Opsi ini tidak berlaku untuk topik dan antrian Bus Layanan.

### <a name="rbac"></a>RBAC

* Memperbaiki #11712: `az ad app/sp show` tidak menampilkan kode keluar 3 saat prinsip aplikasi atau layanan tidak ada

### <a name="storage"></a>Penyimpanan

* `az storage account create`: Menghapus tanda pratinjau untuk --enable-hierarchical-namespace parameter
* Memperbarui versi penyimpanan Azure-mgmt ke 7.0.0 untuk menggunakan versi api 06-01-2019
* Menambahkan parameter baru `--enable-delete-retention` dan `--delete-retention-days` untuk mendukung pengelolaan penghapusan kebijakan penyimpanan untuk properti blob-service-account penyimpanan.

## <a name="december-17-2019"></a>17 Desember 2019

2.0.78

### <a name="acr"></a>Azure Container Registry

* Menambahkan dukungan Konteks lokal dalam menjalankan tugas acr

### <a name="acs"></a>ACS

* [BREAKING CHANGE]az openshift create: ganti nama `--workspace-resource-id` menjadi `--workspace-id`.

### <a name="ams"></a>AMS

* Perintah tampilkan yang diperbarui untuk mengembalikan 3 saat sumber daya tidak ditemukan

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Memperbaiki bug saat menambahkan versi api ke url permintaan. Solusi yang ada tidak berfungsi dengan pagination.
* Menambahkan dukungan untuk menampilkan bahasa selain bahasa Inggris karena layanan backend kami mendukung unicode untuk globalisasi.

### <a name="appservice"></a>AppService

* Memperbaiki masalah #11217: webapp: az webapp config ssl upload akan mendukung parameter slot
* Memperbaiki masalah #10965: Kesalahan: Nama tidak boleh kosong. Izinkan penghapusan dengan ip_address dan subnet
* Dukungan tambahan untuk mengimpor sertifikat dari Key Vault `az webapp config ssl import`

### <a name="arm"></a>ARM

* Paket sumber daya Azure-mgmt yang diperbarui untuk menggunakan 6.0.0
* Dukungan Penyewa Lintas untuk perintah `az group deployment create` dengan menambahkan parameter baru `--aux-subs`
* Menambahkan parameter baru `--metadata` untuk mendukung penambahan informasi metadata untuk definisi kumpulan kebijakan.

### <a name="backup"></a>Cadangan

* Menambahkan dukungan Cadangan untuk beban kerja SQL dan SAP Hana.

### <a name="botservice"></a>BotService

* [Melanggar perubahan] Menghapus tanda '--version' dari perintah pratinjau 'az bot create'. Hanya bot SDK v4 yang didukung.
* Menambahkan pemeriksaan ketersediaan nama untuk 'az bot create'.
* Menambahkan dukungan untuk memperbarui URL ikon untuk bot melalui 'az bot update'.
* Menambahkan dukungan untuk memperbarui saluran Direct Line melalui 'az bot directline update'.
* Menambahkan dukungan flag '--enhanced-auth' ke 'az bot directline create'.
* Grup perintah berikut adalah GA dan tidak dalam pratinjau: 'az bot authsetting'.
* Perintah berikut di 'az bot' adalah GA dan bukan dalam pratinjau: 'create', 'prepare-deploy', 'show', 'delete', 'update'.
* Memperbaiki 'az bot prepare-deploy' yang mengubah nilai '--proj-file-path' menjadi huruf kecil (misalnya "Test.csproj" menjadi "test.csproj").

### <a name="compute"></a>Compute

* vmss create/update: Menambahkan --scale-in-policy, yang memutuskan mesin virtual mana yang dipilih untuk dihapus saat VMSS ditingkatkan.
* pembaruan vm/vmss: Menambahkan --priority.
* pembaruan vm/vmss: Menambahkan --max-price.
* Menambahkan grup perintah set enkripsi disk (buat, tampilkan, perbarui, hapus, daftar).
* disk create: Menambahkan --encryption-type dan --disk-encryption-set.
* vm/vmss create: Menambahkan --os-disk-encryption-set dan --data-disk-encryption-sets.

### <a name="core"></a>Core

* Dukungan yang dihapus untuk Python 3.4
* Pasang survei HaTS dalam beberapa perintah

### <a name="dls"></a>DLS

* Versi SDK ADLS yang diperbarui (0.0.48).

### <a name="install"></a>Instal

* Instal dukungan skrip python 3.8

### <a name="iot"></a>IOT

* [BREAKING CHANGE] Menghapus parameter --failover-region dari manual-failover. Sekarang akan failover ke wilayah sekunder yang dipasangkan secara geografis.

### <a name="key-vault"></a>Key Vault

* Memperbaiki #8095: `az keyvault storage remove`: menyempurnakan pesan bantuan
* Memperbaiki #8921: `az keyvault key/secret/certificate list/list-deleted/list-versions`: memperbaiki bug validasi pada parameter `--maxresults`
* Memperbaiki #10512: `az keyvault set-policy`: memperbaiki pesan kesalahan saat tidak ada `--object-id`, `--spn`, atau `--upn` yang ditentukan
* Memperbaiki #10846: `az keyvault secret show-deleted`: ketika `--id` ditentukan, `--name/-n` tidak diperlukan
* Memperbaiki #11084: `az keyvault secret download`: menyempurnakan pesan bantuan parameter `--encoding`

### <a name="network"></a>Jaringan

* az network application-gateway probe: Menambahkan opsi dukungan --port untuk menentukan port untuk memeriksa server backend saat membuat dan memperbarui
* az network application-gateway url-path-map buat/perbarui: perbaikan bug untuk `--waf-policy`
* az network application-gateway: Dukungan tambahan `--rewrite-rule-set`
* az network list-service-aliases: Menambahkan alias layanan daftar dukungan yang dapat digunakan untuk Kebijakan Titik Akhir Layanan
* az network dns zone import: Menambahkan dukungan .@ dalam nama rekaman

### <a name="packaging"></a>Pengemasan

* Menambahkan build tepi belakang untuk pemasangan pip
* Menambahkan paket eoan Ubuntu

### <a name="policy"></a>Kebijakan

* Menambahkan dukungan untuk Policy API versi 01-09-2019.
* az policy set-definition: Menambahkan pengelompokan dukungan dalam definisi set kebijakan dengan parameter `--definition-groups`

### <a name="redis"></a>Redis

* Menambahkan parameter pratinjau `--replicas-per-master` ke perintah `az redis create`
* Azure-mgmt-redis diperbarui dari 6.0.0 ke 7.0.0rc1

### <a name="servicefabric"></a>ServiceFabric

* Memperbaiki logika penambahan jenis node termasuk #10963: Menambahkan jenis node baru dengan tingkat daya tahan Emas akan selalu menimbulkan kesalahan CLI
* Memperbarui versi ServiceFabricNodeVmExt ke 1.1 dalam template pembuatan

### <a name="sql"></a>SQL

* Menambahkan parameter "--read-scale" dan "--read-replicas" ke perintah sql db create dan update, untuk mendukung manajemen skala baca.

### <a name="storage"></a>Penyimpanan

* GA Rilis properti Berbagi File Besar untuk perintah pembuatan dan pembaruan akun penyimpanan
* GA Rilis Delegasi Pengguna Dukungan token SAS
* Menambahkan perintah baru `az storage account blob-service-properties show` dan `az storage account blob-service-properties update --enable-change-feed` untuk mengelola properti layanan blob untuk akun penyimpanan.
* [PERUBAHAN LUAR BIASA] `az storage copy`: `*` karakter tidak lagi didukung sebagai karakter pengganti di URL, tetapi parameter baru --include-pattern dan --exclude-pattern akan ditambahkan dengan `*` dukungan karakter pengganti.
* Memperbaiki masalah #11043: Menambahkan dukungan untuk menghapus seluruh kontainer/berbagi dalam perintah `az storage remove`

## <a name="november-26-2019"></a>26 November 2019

Versi 2.0.77

### <a name="acr"></a>Azure Container Registry

* Parameter usang `--branch` dari tugas acr buat/perbarui

### <a name="azure-red-hat-openshift"></a>Azure Red Hat OpenShift

* Menambahkan tanda `--workspace-resource-id` untuk memungkinkan pembuatan kluster Azure Red Hat Openshift dengan pemantauan
* Menambahkan `monitor_profile` untuk membuat kluster Azure Red Hat OpenShift dengan pemantauan

### <a name="aks"></a>AKS

* Menambahkan operasi rotasi sertifikat kluster dukungan menggunakan "az aks rotate-certs".

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan dukungan untuk menggunakan ":" untuk `as az appconfig kv import` pemisah
* Memperbaiki masalah untuk mencantumkan nilai kunci dengan beberapa label termasuk label nol.
* SDK bidang manajemen yang diperbarui, konfigurasi aplikasi-mgmt-azure, ke versi 0.3.0.

### <a name="appservice"></a>AppService

* Memperbaiki masalah #11100: AttributeError untuk az webapp up saat membuat paket layanan
* az webapp up: Memaksa pembuatan atau penyebaran ke situs untuk bahasa yang didukung, tidak ada default yang digunakan.
* Menambahkan dukungan untuk Lingkungan App Service: az appservice ase show | daftar | daftar-alamat | daftar-rencana | buat | perbarui | menghapus

### <a name="backup"></a>Cadangan

* Memperbaiki masalah di az backup policy list-associated-items. Menambahkan parameter BackupManagementType opsional.

### <a name="compute"></a>Compute

* Versi API komputasi, disk, snapshot yang ditingkatkan ke 07-01-2019
* vmss create: Peningkatan untuk --orchestration-mode
* sig image-definition create: Menambahkan --os-state untuk memungkinkan menentukan apakah mesin virtual yang dibuat di bawah gambar ini adalah 'Umum' atau 'Khusus'
* sig image-definition create: Menambahkan --hyper-v-generation untuk memungkinkan menentukan generasi hypervisor
* sig image-version create: Menambahkan dukungan --os-snapshot dan --data-snapshots
* image create: Menambahkan --data-disk-caching untuk memungkinkan penetapan pengaturan caching dari disk data
* Upgrade Python Compute SDK ke 10.0.0
* vm/vmss create: Menambahkan 'Spot' ke properti enum 'Prioritas'
* [Melanggar perubahan] Mengganti nama parameter '--max-billing' menjadi '--max-price', untuk Mesin Virtual dan VMSS, agar konsisten dengan cmdlet Swagger dan Powershell
* vm monitor log show: Menambahkan dukungan untuk mengkueri log melalui ruang kerja analitik log yang ditautkan.

### <a name="iot"></a>IOT

* Memperbaiki #2531: Menambahkan argumen kenyamanan untuk pembaruan hub.
* Memperbaiki #8323: Menambahkan parameter yang hilang untuk membuat titik akhir kustom penyimpanan.
* Memperbaiki bug regresi: Mengembalikan perubahan yang menimpa titik akhir penyimpanan default.

### <a name="key-vault"></a>Key Vault

* Memperbaiki #11121: Saat menggunakan `az keyvault certificate list`, meneruskan `--include-pending` sekarang tidak memerlukan nilai `true` atau `false`

### <a name="netappfiles"></a>NetAppFiles

* Upgrade Azure-mgmt-netapp ke 0.7.0 yang mencakup beberapa properti volume tambahan yang terkait dengan operasi replikasi yang akan datang

### <a name="network"></a>Jaringan

* application-gateway waf-config: usang
* application-gateway waf-policy: Menambahkan subgrup aturan terkelola untuk mengelola kumpulan aturan terkelola dan aturan pengecualian
* application-gateway waf-policy: Menambahkan pengaturan kebijakan subkelompok untuk mengelola konfigurasi global waf-policy
* [BREAKING CHANGE] application-gateway waf-policy: Mengganti nama aturan subgrup menjadi aturan khusus
* application-gateway http-listener: Menambahkan --firewall-policy saat membuat
* application-gateway url-path-map rule: Ditambahkan --firewall-policy saat membuat

### <a name="packaging"></a>Pengemasan

* Tulis ulang pembungkus az dengan Python
* Menambahkan dukungan untuk Python 3.8
* Diubah ke Python 3 untuk paket RPM

### <a name="profile"></a>Profil

* Memperbaiki kesalahan saat menjalankan `az login -u {} -p {}` dengan akun Microsoft
* Memperbaiki `SSLError` saat menjalankan `az login` di belakang proksi dengan sertifikat akar yang ditandatangani sendiri
* Memperbaiki #10578: `az login` hang ketika lebih dari satu instans diluncurkan secara bersamaan di Windows atau WSL
* Memperbaiki #11059: `az login --allow-no-subscriptions` gagal jika ada langganan di penyewa
* Memperbaiki #11238: Setelah mengganti nama langganan, masuk dengan MSI akan menyebabkan langganan yang sama muncul dua kali

### <a name="rbac"></a>RBAC

* Memperbaiki #10996: Memperbaiki kesalahan untuk `--force-change-password-next-login` di `az ad user update` saat `--password` tidak ditentukan

### <a name="redis"></a>Redis

* Memperbaiki #2902: Menghindari mengatur konfigurasi memori saat memperbarui cache SKU Dasar

### <a name="reservations"></a>Reservasi

* Memperbarui versi SDK ke 0.6.0
* Menambahkan info billingplan setelah memanggil Get-Gatalogs
* Menambahkan perintah baru `az reservations reservation-order calculate` untuk menghitung harga reservasi
* Menambahkan perintah baru `az reservations reservation-order purchase` untuk membeli reservasi baru

### <a name="rest"></a>Sisanya
* Mengubah `az rest` menjadi ketersediaan umum

### <a name="sql"></a>SQL

* Memperbarui Azure-mgmt-sql ke versi 0.15.0.

### <a name="storage"></a>Penyimpanan

* pembuatan akun penyimpanan: Menambahkan --enable-hierarchical-namespace untuk mendukung semantik filesystem dalam layanan blob.
* Menghapus pengecualian yang tidak terkait dari pesan kesalahan
* Memperbaiki masalah dengan pesan kesalahan "Anda tidak memiliki izin yang dibutuhkan untuk melakukan operasi ini." saat diblokir oleh aturan jaringan atau AuthenticationFailed.

## <a name="november-4-2019"></a>4 November 2019

Versi 2.0.76

### <a name="acr"></a>Azure Container Registry

* Menambahkan parameter pratinjau `--pack-image-tag` ke perintah `az acr pack build`.
* Menambahkan dukungan untuk mengaktifkan pengauditan pada pembuatan registri
* Menambahkan dukungan untuk kontrol akses berbasis peran dengan cakupan repositori

### <a name="aks"></a>AKS

* Menambahkan `--enable-cluster-autoscaler`, `--min-count`, dan `--max-count` ke perintah `az aks create`, yang mengaktifkan penskala otomatis kluster untuk kumpulan node.
* Menambahkan bendera di atas serta `--update-cluster-autoscaler` dan `--disable-cluster-autoscaler` ke perintah `az aks update`, yang memungkinkan pembaruan untuk memberikan kluster pada penskala otomatis.

### <a name="appconfig"></a>Konfigurasi Aplikasi

* Menambahkan grup perintah fitur appconfig untuk mengelola bendera fitur yang disimpan dalam App Configuration.
* Memperbaiki bug minor untuk appconfig kv export ke perintah file. Berhenti membaca konten file tujuan selama ekspor.

### <a name="appservice"></a>AppService

* `az appservice plan create`: Menambahkan dukungan untuk mengatur 'persitescaling' pada pembuatan paket appservice.
* Memperbaiki masalah ketika operasi pengikatan ssl config webapp menghapus tag yang ada dari sumber daya
* Menambahkan bendera `--build-remote` untuk `az functionapp deployment source config-zip` guna mendukung tindakan pembangunan jarak jauh selama penyebaran aplikasi fungsi.
* Mengubah versi node default pada aplikasi fungsi menjadi ~10 untuk Windows
* Menambahkan properti `--runtime-version` ke `az functionapp create`

### <a name="arm"></a>ARM

* `az deployment/group deployment validate`: Menambahkan parameter `--handle-extended-json-format` untuk mendukung multibaris dan komentar di templat json saat penyebaran.
* Mengubah azure-mgmt-resource ke 2019-07-01

### <a name="backup"></a>Cadangan

* Menambahkan dukungan cadangan AzureFiles

### <a name="compute"></a>Compute

* `az vm create`: Menambahkan peringatan saat menentukan jaringan yang dipercepat dan NIC yang ada bersama-sama.
* `az vm create`: Menambahkan `--vmss` untuk menentukan set skala mesin virtual yang ada yang harus ditetapkan untuk mesin virtual.
* `az vm/vmss create`: Menambahkan salinan lokal file alias gambar sehingga dapat diakses di lingkungan jaringan terbatas.
* `az vmss create`: Menambahkan `--orchestration-mode` untuk menentukan bagaimana mesin virtual dikelola oleh set skala.
* `az vm/vmss update`: Menambahkan `--ultra-ssd-enabled` untuk memungkinkan pembaruan pengaturan SSD ultra.
* [BREAKING CHANGE] `az vm extension set`: Memperbaiki bug saat pengguna tidak dapat mengatur ekstensi pada Mesin Virtual dengan `--ids`.
* Menambahkan perintah baru `az vm image terms accept/cancel/show` untuk mengelola istilah gambar Marketplace Azure.
* Memperbarui VMAccessForLinux ke versi 1.5

### <a name="cosmosdb"></a>CosmosDB

* [BREAKING CHANGE] `az sql container create`: Mengubah `--partition-key-path` menjadi parameter yang diperlukan
* [BREAKING CHANGE] `az gremlin graph create`: Mengubah `--partition-key-path` menjadi parameter yang diperlukan
* `az sql container create`: Menambahkan `--unique-key-policy` dan `--conflict-resolution-policy`
* `az sql container create/update`: Memperbarui `--idx` skema default
* `gremlin graph create`: Menambahkan `--conflict-resolution-policy`
* `gremlin graph create/update`: Memperbarui `--idx` skema default
* Memperbaiki kesalahan pengetikan dalam pesan bantuan
* database: Menambahkan informasi penghentian
* kumpulan: Menambahkan informasi penghentian

### <a name="iot"></a>IoT

* Menambahkan jenis sumber perutean baru: DigitalTwinChangeEvents
* Memperbaiki fitur yang hilang di `az iot hub create`

### <a name="key-vault"></a>Key Vault

* Memperbaiki kesalahan yang tidak terduga saat file sertifikat tidak ada
* Memperbaiki `az keyvault recover/purge` yang tidak berfungsi

### <a name="netappfiles"></a>NetAppFiles

* Meningkatkan Azure-mgmt-netapp ke 0.6.0 untuk menggunakan versi API 07-01-2019. Versi API baru ini mencakup:

    - Pembuatan volume `--protocol-types` sekarang menerima "NFSv4.1" bukan "NFSv4"
    - Properti kebijakan ekspor volume sekarang bernama 'nfsv41' bukan 'nfsv4'
    - Volume `--creation-token` diganti namanya menjadi `--file-path`
    - Tanggal pembuatan snapshot sekarang hanya bernama 'dibuat'

### <a name="network"></a>Jaringan

* `az network private-dns link vnet create/update`: Mendukung penautan jaringan virtual lintas penyewa.
* [BREAKING CHANGE] `az network vnet subnet list`: Mengubah `--resource-group` dan `--vnet-name` menjadi wajib sekarang.
* `az network public-ip prefix create`: Menambahkan dukungan untuk menentukan versi alamat IP (IPv4, IPv6) saat pembuatan
* Mengubah azure-mgmt-network ke 7.0.0 dan versi api ke 09-01-2019
* `az network vrouter`: Menambahkan dukungan untuk router virtual layanan baru dan peering router virtual
* `az network express-route gateway connection`: Menambahkan dukungan untuk `--internet-security`

### <a name="profile"></a>Profil

* Memperbaiki `az account get-access-token --resource-type ms-graph` yang tidak berfungsi
* Menghapus peringatan dari `az login`

### <a name="rbac"></a>RBAC

* Memperbaiki `az ad app update --id {} --display-name {}` yang tidak berfungsi

### <a name="servicefabric"></a>ServiceFabric

* `az sf cluster create`: Memperbaiki masalah dengan mengubah vmss komputasi service fabric linux and windows template.json dari disk standar ke disk terkelola

### <a name="sql"></a>SQL

* Menambahkan parameter `--compute-model`, `--auto-pause-delay`, dan `--min-capacity` untuk mendukung operasi CRUD untuk penawaran SQL Database baru: Model komputasi tanpa server.

### <a name="storage"></a>Penyimpanan

* `az storage account create/update`: Menambahkan parameter --enable-files-adds dan grup Argumen Properti Azure Active Directory untuk mendukung Autentikasi Azure Files Active Directory Domain Service
* Meluaskan `az storage account keys list/renew` untuk mendukung pencantuman atau pembuatan ulang kunci akun penyimpanan Kerberos.

## <a name="october-15-2019"></a>15 Oktober 2019

Versi 2.0.75

### <a name="aks"></a>AKS

* Mengubah nilai default `--load-balancer-sku` menjadi `standard` jika didukung oleh versi kubernetes
* Mengubah nilai default `--vm-set-type` menjadi `virtualmachinescalesets` jika didukung oleh versi kubernetes

### <a name="ams"></a>AMS

* [BREAKING CHANGE] Mengubah nama `job start` menjadi `job create`
* [BREAKING CHANGE] Mengubah parameter `--ask` dari `content-key-policy create` untuk menggunakan string hex 32 karakter daripada UTF8

### <a name="appservice"></a>AppService

* Menambahkan perintah `webapp config access-restriction show|set|add|remove`
* Menambahkan penanganan kesalahan yang lebih baik ke `webapp up`
* Menambahkan dukungan untuk SKU `Isolated` ke `appservice plan update`

### <a name="arm"></a>ARM

* Menambahkan parameter `--handle-extended-json-format` `deployment create` untuk mendukung multibaris dan komentar di templat json

### <a name="compute"></a>Compute

* Menambahkan parameter `--enable-agent` ke `vm create`
* Mengubah `vm create` untuk menggunakan SKU IP publik standar secara otomatis saat menggunakan zona
* Mengubah `vm create` untuk secara otomatis membuat nama komputer yang valid untuk Mesin Virtual jika tidak ada yang disediakan
* Menambahkan parameter `--computer-name-prefix` ke `vmss create` untuk mendukung prefiks nama komputer kustom dari mesin virtual di VMSS
* Menambahkan parameter `--workspace` ke `vm create` untuk mengaktifkan ruang kerja analitik log secara otomatis
* Memperbarui versi API galeri ke 07-01-2019

### <a name="core"></a>Core

* Menambahkan pemeriksaan sintaks untuk parameter `--set` dalam perintah pembaruan umum

### <a name="iot"></a>IoT

* Memperbaiki masalah saat `iot hub show` memunculkan masalah "sumber daya tidak ditemukan"

### <a name="monitor"></a>Monitor

* Menambahkan dukungan untuk CRUD ke `monitor log-analytics workspace`

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk penautan virtual lintas penyewa ke `network private-dns link vnet [create|update]`
* [BREAKING CHANGE] Mengubah `network vnet subnet list` untuk mewajibkan parameter `--resource-group` dan `--vnet-name`

### <a name="sql"></a>SQL

* Menambahkan perintah ke `sql mi ad-admin` yang mendukung pengaturan administrator Azure Active Directory pada instans terkelola

### <a name="storage"></a>Penyimpanan

* Menambahkan parameter `--preserve-s2s-access-tier` `storage copy` untuk mempertahankan tingkat penyimpanan selama layanan ke salinan layanan
* Menambahkan parameter `--enable-large-file-share` ke `storage account [create|update]` untuk mendukung berbagi yang besar untuk akun penyimpanan

## <a name="september-24-2019"></a>24 September 2019

Versi 2.0.74

### <a name="acr"></a>Azure Container Registry

* Menambahkan parameter `--type` yang dibutuhkan ke `acr config retention update`
* [BREAKING CHANGE] Mengganti nama parameter `--name -n` menjadi `--registry -r ` untuk grup perintah `acr config`

### <a name="aks"></a>AKS

* Menambahkan parameter `--load-balancer-sku` ke perintah `aks create`, yang memungkinkan pembuatan kluster Azure Kubernetes Service dengan SLB
* Menambahkan parameter `--load-balancer-managed-outbound-ip-count`, `--load-balancer-outbound-ips`, dan `--load-balancer-outbound-ip-prefixes` ke perintah `aks [create|update]`, yang memungkinkan memperbarui profil penyeimbang beban kluster Azure Kubernetes Service dengan SLB
* Menambahkan parameter `--vm-set-type` ke perintah `aks create`, yang memungkinkan menentukan jenis mesin virtual dari Kluster Azure Kubernetes Service (vmas atau vmss)

### <a name="arm"></a>ARM

* Menambahkan parameter `--handle-extended-json-format` ke perintah `group deployment create` untuk mendukung multibaris dan komentar di templat json

### <a name="compute"></a>Compute

* Menambahkan parameter `--terminate-notification-time` ke perintah `vmss [create|update]` untuk mendukung penghentian konfigurasi peristiwa terjadwal
* Menambahkan parameter `--enable-terminate-notification` ke perintah `vmss update` untuk mendukung penghentian konfigurasi peristiwa terjadwal
* Menambahkan parameter `--priority,` `--eviction-policy,` `--max-billing` ke perintah `[vm|vmss] create`
* Mengubah `disk create` untuk memungkinkan penentuan ukuran yang tepat dari pengunggahan disk
* Menambahkan dukungan untuk snapshot bertahap untuk disk terkelola ke `snapshot create`

### <a name="cosmos-db"></a>Cosmos DB

* Menambahkan parameter `--type <key-type>` ke perintah `cosmosdb keys list` untuk menampilkan kunci, kunci baca saja atau string koneksi
* Menambahkan perintah `cosmosdb keys regenerate`
* [DEPRECATED] Menghentikan `cosmosdb list-connection-strings`, `cosmosdb regenerate-key`, dan perintah `cosmosdb list-read-only-keys`

### <a name="eventgrid"></a>EventGrid

* Memperbaiki teks bantuan titik akhir untuk merujuk ke parameter yang tepat

### <a name="key-vault"></a>Key Vault

* Memperbaiki masalah saat masuk dengan penyewa (`login -t`) yang dapat menyebabkan `keyvault create` gagal

### <a name="monitor"></a>Monitor

* Memperbaiki masalah saat karakter `:` tidak diizinkan dalam argumen `--condition` ke `monitor metrics alert create`

### <a name="policy"></a>Kebijakan

* Menambahkan dukungan untuk versi API Kebijakan 01-06-2019
* Menambahkan parameter `--enforcement-mode` ke perintah `policy assignment create`

### <a name="storage"></a>Penyimpanan

* Menambahkan parameter `--blob-type` ke perintah `az storage copy`

## <a name="september-10-2019"></a>########

### <a name="acr"></a>Azure Container Registry

* Menambahkan grup perintah `acr config retention` untuk mengonfigurasi kebijakan penyimpanan

### <a name="aks"></a>AKS

* Menambahkan dukungan untuk integrasi Azure Container Registry dengan perintah berikut:
  * Menambahkan parameter `--attach-acr` ke `aks [create|update]` untuk melampirkan Azure Container Registry ke kluster Azure Kubernetes Service
  * Menambahkan parameter `--detach-acr` ke `aks update` untuk mencopot Azure Container Registry dari kluster Azure Kubernetes Service

### <a name="arm"></a>ARM

* Diperbarui untuk menggunakan versi API 10-05-2019

### <a name="batch"></a>Batch

* Menambahkan pengaturan konfigurasi JSON baru ke `--json-file` untuk `batch pool create`:
  * Menambahkan `MountConfigurations` untuk pemasangan sistem file (lihat [Isi Permintaan](/rest/api/batchservice/pool/add#request-body) untuk lebih detail)
  * Menambahkan properti opsional `publicIPs` di `NetworkConfiguration` untuk IP publik di kumpulan (lihat [Isi Permintaan](/rest/api/batchservice/pool/add#request-body) untuk lebih detail)
* Menambahkan dukungan untuk galeri gambar bersama ke `--image`
* [BREAKING CHANGE] Mengubah nilai default `--start-task-wait-for-success` pada `batch pool create` menjadi `true`
* [BREAKING CHANGE] Mengubah nilai default untuk `Scope` pada `AutoUserSpecification` agar selalu berupa Kumpulan (sebelumnya `Task` pada node Windows, `Pool` pada node Linux)
  * Argumen ini hanya dapat diatur dari konfigurasi JSON dengan `--json-file`

### <a name="hdinsight"></a>HDInsight

* Rilis ketersediaan umum
* [BREAKING CHANGE] Mengubah parameter `--workernode-count/-c` dari `az hdinsight resize` menjadi wajib.

### <a name="key-vault"></a>Key Vault

* Memperbaiki masalah saat subnet tidak dapat dihapus dari aturan jaringan
* Memperbaiki masalah saat subnet dan alamat IP yang digandakan dapat ditambahkan ke aturan jaringan

### <a name="network"></a>Jaringan

* Menambahkan parameter `--interval` ke `network watcher flow-log` untuk mengatur nilai interval analisis lalu lintas
* Menambahkan `network application-gateway identity` untuk mengelola identitas gateway
* Menambahkan dukungan untuk mengatur ID Key Vault ke `network application-gateway ssl-cert`
* Menambahkan `network express-route peering peer-connection [show|list]`

### <a name="policy"></a>Kebijakan

* Diperbarui untuk menggunakan versi API 01-01-2019

## <a name="august-27-2019"></a>27 Agustus 2019

Versi 2.0.72

### <a name="acr"></a>Azure Container Registry

* [BREAKING CHANGE] Menghapus dukungan untuk SKU `classic`

### <a name="api-management"></a>API Management

* [PREVIEW] Menambahkan grup perintah `apim`

### <a name="appservice"></a>AppService

* Memperbaiki masalah dengan perintah `webapp webjob continuous start` saat menentukan slot
* Mengubah `webapp up` untuk mendeteksi folder `env` dan menghapusnya dari file yang digunakan untuk penyebaran

### <a name="keyvault"></a>Keyvault

* Memperbaiki bug di `keyvault secret set` yang mengabaikan argumen `--expires`

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk alamat IPv6 ke argumen `--private-ip-address-version`
* Menambahkan perintah baru `network private-endpoint [create|update|list-types]` untuk manajemen titik akhir privat
* Menambahkan grup perintah `network private-link-service`
* Menambahkan argumen `--private-endpoint-network-policies` dan `--private-link-service-network-policies` ke `network vnet subnet update`

### <a name="rbac"></a>RBAC

* Memperbaiki masalah dengan `ad app update --homepage` saat beranda tidak dapat diperbarui

### <a name="servicefabric"></a>ServiceFabric

* Menambahkan dukungan untuk nama-nama Key Vault dengan huruf besar-kecil
* Memperbaiki masalah saat menggunakan sertifikat di Key Vault
* Memperbaiki masalah dengan menggunakan file sertifikat PFX
* Memperbaiki masalah dengan `sf cluster certificate add` saat grup sumber daya Key Vault tidak ditentukan
* Memperbaiki masalah dengan `sf cluster set` yang tidak berfungsi

### <a name="signalr"></a>SignalR

* Menambahkan perintah baru:
  * `signalr cors`: Mengelola SignalR CORS
  * `signalr restart`: Menghidupkan ulang layanan SignalR
  * `signalr update`: Memperbarui layanan SignalR
* Menambahkan argumen `--service-mode` ke `signalr create`

### <a name="storage"></a>Penyimpanan

* Menambahkan perintah `storage account revoke-delegation-keys`

## <a name="august-13-2019"></a>13 Agustus 2019

Versi 2.0.71

### <a name="appservice"></a>AppService

* Memperbaiki masalah saat perintah `webapp webjob continuous` gagal untuk slot

### <a name="botservice"></a>BotService

* [BREAKING CHANGE] Menghapus dukungan untuk membuat bot SDK v3

### <a name="cognitiveservices"></a>CognitiveServices

* Menambahkan perintah `cognitiveservices account network-rule`

### <a name="cosmos-db"></a>Cosmos DB

* Menghapus peringatan saat memperbarui beberapa lokasi penulisan
* Menambahkan perintah CRUD untuk sumber daya CosmosDB SQL, MongoDB, Cassandra, GREMLIN dan Tabel serta throughput sumber daya

### <a name="hdinsight"></a>HDInsight

Rilis ini berisi sejumlah besar perubahan yang melanggar.

* [BREAKING CHANGE] Mengganti nama parameter untuk `hdinsight create`:
  * Mengganti nama `--storage-default-container` menjadi `--storage-container`
  * Mengganti nama `--storage-default-filesystem` menjadi `--storage-filesystem`
* [BREAKING CHANGE] Mengubah argumen `--name` dari `application create` untuk mewakili nama aplikasi bukan nama kluster
* Menambahkan argumen `--cluster-name` ke `application create` untuk menggantikan fungsionalitas `--name` yang lama
* [BREAKING CHANGE] Mengganti nama parameter untuk `application create`:
  * Mengganti nama `--application-type` menjadi `--type`
  * Mengganti nama `--marketplace-identifier` menjadi `--marketplace-id`
  * Mengganti nama `--https-endpoint-access-mode` menjadi `--access-mode`
  * Mengganti nama `--https-endpoint-destination-port` menjadi `--destination-port`
* [BREAKING CHANGE] Menghapus parameter untuk `application create`:
  * `--https-endpoint-location`
  * `--https-endpoint-public-port`
  * `--ssh-endpoint-destination-port`
  * `--ssh-endpoint-location`
  * `--ssh-endpoint-public-port`
* [BREAKING CHNAGE] Mengganti nama `--target-instance-count` menjadi `--workernode-count` untuk `hdinsight resize`
* [BREAKING CHANGE] Mengubah semua perintah di grup `hdinsight script-action` untuk menggunakan parameter `--name` sebagai nama tindakan skrip.
* Menambahkan argumen `--cluster-name` ke semua perintah `hdinsight script-action` untuk menggantikan fungsionalitas `--name` yang lama
* [BREAKING CHANGE] Mengganti nama `--script-execution-id` menjadi `--execution-id` untuk semua perintah `hdinsight script-action`
* [BREAKING CHANGE] Mengganti nama `hdinsight script-action show` menjadi `hdinsight script-action show-execution-details`
* [BREAKING CHNAGE] Mengubah parameter menjadi `hdinsight script-action execute --roles` agar dipisahkan spasi, bukan dipisahkan koma
* [BREAKING CHANGE] Menghapus parameter `--persisted` dari `hdinsight script-action list`
* Mengubah parameter `hdinsight create --cluster-configurations` untuk menerima jalur ke file JSON lokal atau string JSON
* Menambahkan perintah `hdinsight script-action list-execution-history`
* Mengubah `hdinsight monitor enable --workspace` untuk menerima ID ruang kerja Analitik Log atau nama ruang kerja
* Menambahkan argumen `hdinsight monitor enable --primary-key`, yang diperlukan jika ID ruang kerja disediakan sebagai parameter
* Menambahkan lebih banyak contoh dan memperbarui deskripsi untuk pesan bantuan

### <a name="interactive"></a>Interaktif

* Memperbaiki kesalahan pemuatan

### <a name="kubernetes"></a>Kubernetes

* Mengubah untuk menggunakan `https` jika port kontainer dasbor menggunakan `https`

### <a name="network"></a>Jaringan

* Menambahkan argumen `--yes` `network dns record-set cname delete`

### <a name="profile"></a>Profil

* Menambahkan argumen `--resource-type` ke `account get-access-token` untuk mendapatkan token akses sumber daya

### <a name="servicefabric"></a>ServiceFabric

* Menambahkan semua versi os yang didukung untuk pembuatan kluster sf
* Memperbaiki bug validasi sertifikat utama

### <a name="storage"></a>Penyimpanan

* Menambahkan perintah `storage copy`

## <a name="july-30-2019"></a>30 Juli 2019

Versi 2.0.70

### <a name="acr"></a>Azure Container Registry

* Memperbaiki masalah #9952 (regresi dalam perintah `acr pack build`)
* Menghapus nama gambar penyusun default di `acr pack build`

### <a name="appservice"></a>Appservice

* Mengubah `webapp config ssl` untuk menunjukkan pesan jika sumber daya tidak ditemukan
* Memperbaiki masalah saat `functionapp create` tidak menerima jenis akun penyimpanan `Standard_RAGRS`
* Memperbaiki masalah saat `webapp up` akan gagal jika dijalankan menggunakan versi python yang lebih lama

### <a name="network"></a>Jaringan

* Menghapus parameter tidak valid `--ids` dari `network nic ip-config add` (perbaikan #9861)
* Memperbaiki #9604. Menambahkan parameter `--root-certs` ke `network application-gateway http-settings [create|update]` untuk mendukung sertifikat akar tepercaya yang dikaitkan dengan pengguna.
* Argumen tetap `--subscription` untuk `network dns record-set ns create` (#9965)

### <a name="rbac"></a>RBAC

* Menambahkan perintah `user update`
* [DEPRECATED] Menghentikan `--upn-or-object-id` dari perintah terkait pengguna
    * Menggunakan argumen penggantian `--id`
* Menambahkan argumen `--id` ke perintah terkait pengguna

### <a name="sql"></a>SQL

* Menambahkan perintah manajemen untuk kunci instans terkelola dan pelindung TDE

### <a name="storage"></a>Penyimpanan

* Menambahkan perintah `storage remove`
* Memperbaiki masalah dengan `storage blob update`

### <a name="vm"></a>VM

* Mengubah `list-skus` untuk menggunakan api-version yang lebih baru untuk menghasilkan detail zona
* Mengubah default dari `--single-placement-group` menjadi `false` untuk `vmss create`
* Menambahkan kemampuan untuk memilih SKU penyimpanan ZRS untuk `[snapshot|disk] create`
* Menambahkan grup perintah baru `vm host` untuk mendukung host khusus
* Menambahkan parameter `--host` dan `--host-group` pada `vm create` untuk mengatur host khusus Mesin Virtual

## <a name="july-16-2019"></a>16 Juli 2019

Versi 2.0.69

### <a name="appservice"></a>Appservice

* Mengubah perintah `webapp identity` untuk mengembalikan pesan kesalahan yang tepat jika ResourceGroupName atau nama Aplikasi tidak valid
* Memperbaiki `webapp list` untuk mengembalikan nilai yang benar untuk numberOfSites jika tidak ada ResourceGroup yang disediakan
* Memperbaiki efek samping `appservice plan create` dan `webapp create`

### <a name="core"></a>Core

* Memperbaiki masalah saat `--subscription` akan muncul meskipun tidak berlaku

### <a name="batch"></a>Batch

* [BREAKING CHANGE] Mengganti `batch pool node-agent-skus list` dengan `batch pool supported-images list`
* Menambahkan dukungan untuk aturan keamanan yang memblokir akses jaringan ke kumpulan berdasarkan port sumber lalu lintas saat menggunakan opsi `--json-file` dari `batch pool create network`
* Menambahkan dukungan untuk menjalankan tugas di direktori kerja kontainer atau di direktori kerja tugas Batch saat menggunakan opsi `--json-file` dari `batch task create`
* Memperbaiki kesalahan dalam opsi `--application-package-references` dari `batch pool create` yang hanya berfungsi dengan default

### <a name="eventhubs"></a>Eventhubs

* Menambahkan validasi untuk parameter `--rights` dari perintah `authorizationrule`

### <a name="rdbms"></a>RDBMS

* Menambahkan parameter opsional untuk menentukan SKU replika untuk membuat perintah replika
* Memperbaiki masalah dengan kegagalan pengujian CI dengan membuat replika MySQL

### <a name="relay"></a>Relay

* Memperbaiki masalah dengan koneksi hibrid saat otorisasi klien dinonaktifkan [#8775](https://github.com/azure/azure-cli/issues/8775)
* Menambahkan parameter `--requires-transport-security` ke `relay wcfrelay create`

### <a name="servicebus"></a>Servicebus

* Menambahkan validasi untuk parameter `--rights` dari perintah `authorizationrule`

### <a name="storage"></a>Penyimpanan

* Mengaktifkan File AADDS untuk pembaruan akun penyimpanan
* Memperbaiki masalah `storage blob service-properties update --set`

## <a name="july-2-2019"></a>2 Juli 2019

Versi 2.0.68

### <a name="core"></a>Core

* Modul perintah sekarang dikonsolidasikan menjadi satu Python yang dapat didistribusikan. Hal ini menghentikan penggunaan langsung dari banyak paket `azure-cli-` di PyPI.
  Hal ini akan mengurangi ukuran penginstalan dan hanya memengaruhi pengguna yang telah menginstal langsung melalui `pip`.

### <a name="acr"></a>Azure Container Registry

* Menambahkan dukungan untuk Pemicu Timer ke Tugas

### <a name="appservice"></a>Appservice

* Mengubah `functionapp create` untuk mengaktifkan wawasan aplikasi secara default
* [BREAKING CHANGE] Menghapus perintah `functionapp devops-build` yang tidak digunakan lagi.
  *  Menggunakan perintah baru `az functionapp devops-pipeline` sebagai gantinya
* Menambahkan dukungan paket aplikasi fungsi Penggunaan Linux ke `functionapp deployment config-zip`

### <a name="cosmos-db"></a>Cosmos DB

* Menambahkan dukungan untuk menonaktifkan TTL

### <a name="dls"></a>DLS

* Memperbarui versi Azure Data Lake Storage (0.0.45)

### <a name="feedback-reference"></a>Referensi umpan balik

* Saat melaporkan perintah ekstensi yang gagal, `az feedback` sekarang mencoba membuka browser ke url proyek/repositori ekstensi dari indeks

### <a name="hdinsight"></a>HDInsight

* [BREAKING CHANGE] Mengubah nama grup perintah `oms` menjadi `monitor`
* [BREAKING CHANGE] Menjadikan `--http-password/-p` sebagai parameter yang dibutuhkan
* Menambahkan pelengkap untuk pelengkap parameter `--cluster-admin-account` dan `cluster-users-group-dns`
* Mengubah parameter `cluster-users-group-dns` yang diperlukan saat `—esp` ada
* Menambahkan batas waktu untuk semua pelengkap otomatis argumen yang ada
* Menambahkan batas waktu untuk mengubah nama sumber daya menjadi id sumber daya
* Mengubah Pelengkap otomatis untuk memilih sumber daya dari grup sumber daya mana pun. Grup sumber daya dapat berupa grup sumber daya yang berbeda dari yang ditentukan dengan `-g`
* Menambahkan dukungan untuk parameter `--sub-domain-suffix` dan `--disable_gateway_auth` dalam perintah `hdinsight application create`

### <a name="managed-services"></a>Layanan Terkelola

* Memperkenalkan modul perintah layanan terkelola dalam pratinjau

### <a name="profile"></a>Profil
* Menghentikan argumen `--subscription` untuk perintah keluar

### <a name="rbac"></a>RBAC

* [BREAKING CHANGE] Menghapus argumen `--password` untuk `create-for-rbac`
* Menambahkan parameter `--assignee-principal-type` ke perintah `create` untuk menghindari kegagalan terputus-putus yang disebabkan oleh latensi replikasi server grafik Azure Active Directory
* Memperbaiki crash di `ad signed-in-user` saat mencantumkan objek yang dimiliki
* Memperbaiki masalah saat `ad sp` tidak menemukan aplikasi yang tepat dari perwakilan layanan

### <a name="rdbms"></a>RDBMS

* Menambahkan dukungan untuk replikasi untuk MariaDB

### <a name="sql"></a>SQL

* Mendokumentasikan nilai yang diizinkan untuk `sql db create --sample-name`

### <a name="storage"></a>Penyimpanan

* Menambahkan dukungan token SAS delegasi pengguna dengan `--as-user` ke `storage blob generate-sas`
* Menambahkan dukungan token SAS delegasi pengguna dengan `--as-user` ke `storage container generate-sas`

### <a name="vm"></a>VM

* Memperbaiki bug saat `vmss create` menampilkan pesan kesalahan saat dijalankan dengan `--no-wait`
* Menghapus validasi sisi klien untuk `vmss create --single-placement-group`. Tidak gagal jika `--single-placement-group` diatur ke `true` dan`--instance-count` lebih besar dari 100 atau zona ketersediaan ditentukan, tetapi serahkan validasi ini ke layanan komputasi
* Memperbaiki bug saat `[vm|vmss] extension image list` gagal saat digunakan dengan `--latest`


## <a name="june-18-2019"></a>18 Juni 2019

Versi 2.0.67

### <a name="core"></a>Core

Rilis ini memperkenalkan tag [Preview] baru untuk berkomunikasi dengan lebih jelas kepada pelanggan saat grup perintah, perintah, atau argumen dalam status pratinjau. Ini sebelumnya dipanggil dalam teks bantuan atau dikomunikasikan secara implisit oleh nomor versi modul perintah.
CLI akan menghapus nomor versi untuk masing-masing paket di masa mendatang. Jika perintah dalam pratinjau, semua argumen perintah juga dalam pratinjau. Jika grup perintah diberi label sebagai dalam pratinjau, maka semua perintah dan argumen juga dianggap dalam pratinjau.

Sebagai hasil dari perubahan ini, beberapa grup perintah mungkin terlihat seperti "tiba-tiba" muncul dalam status pratinjau dengan rilis ini. Apa yang sebenarnya terjadi adalah sebagian besar paket berada dalam status pratinjau, tetapi dianggap sebagai ketersediaan umum dengan rilis ini

### <a name="acr"></a>Azure Container Registry
* Menambahkan perintah 'acr check-health'
* Penanganan kesalahan yang ditingkatkan untuk token Azure Active Directory dan untuk mengambil perintah eksternal

### <a name="acs"></a>ACS
* Perintah Access Control yang tidak digunakan lagi sekarang disembunyikan dari tampilan bantuan

### <a name="ams"></a>AMS
* [BREAKING CHANGE] Mengubah guna menampilkan string waktu ISO 8601 untuk archive-window-length dan key-frame-interval-duration

### <a name="appservice"></a>AppService
* Menambahkan perutean berbasis lokasi untuk `webapp deleted list` dan `webapp deleted restore`
* Memperbaiki masalah ketika webapp up log target URL ("Anda dapat meluncurkan aplikasi di...") tidak dapat diklik di Azure Cloud Shell
* Memperbaiki masalah saat membuat aplikasi dengan beberapa SKU yang gagal dengan kesalahan Grup Ketersediaan AlwaysOn
* Menambahkan pra-validasi ke `[appservice|webapp] create`
* Memperbaiki `[webapp|functionapp] traffic-routing` untuk menggunakan actionHostName yang benar
* Menambahkan dukungan slot ke perintah `functionapp`

### <a name="batch"></a>Batch
* Memperbaiki regresi autentikasi Azure Active Directory yang disebabkan oleh pelaporan kesalahan yang terlalu agresif untuk Autentikasi Kunci Bersama

### <a name="batchai"></a>BatchAI
* Perintah BatchAI sekarang tidak digunakan lagi dan disembunyikan

### <a name="botservice"></a>BotService
* Menambahkan pesan peringatan "dukungan dihentikan"/"mode pemeliharaan" untuk perintah yang mendukung SDK v3

### <a name="cosmosdb"></a>CosmosDB
* [DEPRECATED] Menghentikan perintah `cosmosdb list-keys`
* Menambahkan perintah `cosmosdb keys list` - menggantikan `cosmosdb list-keys`
* `cosmsodb create/update`: Menambahkan format baru untuk --location guna mengizinkan pengaturan properti "isZoneRedundant". Menghentikan format yang lama

### <a name="eventgrid"></a>EventGrid
* Menambahkan perintah `eventgrid domain` untuk operasi CRUD domain
* Menambahkan perintah `eventgrid domain topic` untuk operasi CRUD topik domain
* Menambahkan argumen `--odata-query` ke `eventgrid [topic|event-subscription] list` untuk memfilter hasil menggunakan sintaks OData
* `event-subscription create/update`: Menambahkan servicebusqueue sebagai nilai baru untuk parameter `--endpoint-type`
* [BREAKING CHANGE] Menghapus dukungan untuk `--included-event-types All` dengan `eventgrid event-subscription [create|update]`

### <a name="hdinsight"></a>HDInsight
* Menambahkan dukungan untuk parameter `--ssh-public-key` dalam perintah `hdinsight create`

### <a name="iot"></a>IoT
* Menambahkan dukungan untuk membuat ulang kunci kebijakan otorisasi
* Menambahkan SDK dan dukungan untuk Layanan Provisi Repositori DigitalTwin

### <a name="network"></a>Jaringan
* Menambahkan dukungan Zona untuk Nat Gateway
* Menambahkan perintah `network list-service-tags`
* Memperbaiki masalah dengan `dns zone import` saat pengguna tidak dapat mengimpor catatan kartubebas A
* Memperbaiki masalah dengan `watcher flow-log configure` saat pengelogan alur tidak dapat diaktifkan di wilayah tertentu

### <a name="resource"></a>Sumber daya
* Menambahkan perintah `az rest` untuk melakukan panggilan REST
* Memperbaiki kesalahan saat menggunakan `policy assignment list` dengan grup sumber daya atau tingkat langganan `--scope`

### <a name="servicebus"></a>ServiceBus
* Memperbaiki masalah dengan `servicebus topic create --max-size` [#9319](https://github.com/azure/azure-cli/issues/9319)

### <a name="sql"></a>SQL
* Mengubah `--location` menjadi opsional untuk `sql [server|mi] create` - menggunakan lokasi grup sumber daya jika tidak ditentukan
* Memperbaiki kesalahan "'objek NoneType' tidak dapat diubah" untuk `sql db list-editions --available`

### <a name="sqlvm"></a>SQLVm
* [BREAKING CHNAGE] Mengubah `sql vm create` agar mewajibkan parameter `--license-type`
* Mengubah untuk mengizinkan SKU gambar SQL pengaturan saat membuat atau memperbarui mesin virtual sql

### <a name="storage"></a>Penyimpanan
* Memperbaiki masalah dengan kunci akun yang hilang untuk `storage container generate-sas`
* Memperbaiki masalah dengan `storage blob sync` di Linux

### <a name="vm"></a>VM
* [PREVIEW] Menambahkan perintah `vm image template` untuk membangun gambar Mesin Virtual

## <a name="june-4-2019"></a>4 Juni 2019

Versi 2.0.66

### <a name="core"></a>Core
* Memperbaiki bug saat perintah gagal jika `--output yaml` digunakan dengan `--query`

### <a name="acr"></a>Azure Container Registry
* Menambahkan grup perintah 'acr pack' untuk membuat Tugas pembangunan cepat menggunakan Buildpacks.

### <a name="acs"></a>ACS
* Mengizinkan mengaktifkan/menonaktifkan addon dasbor kube Azure Kubernetes Service
* Mencetak pesan ramah saat langganan tidak disetujui untuk menggunakan Azure Red Hat OpenShift

### <a name="batch"></a>Batch
* Meningkatkan penanganan kesalahan saat tidak masuk ke akun \[[#9165](https://github.com/Azure/azure-cli/issues/9165)\]\[[#8978](https://github.com/Azure/azure-cli/issues/8978)\]

### <a name="iot"></a>IoT
* Menambahkan dukungan untuk failover manual

### <a name="network"></a>Jaringan
* Menambahkan perintah `network application-gateway waf-policy` untuk mendukung aturan WAF kustom.
* Menambahkan argumen `--waf-policy` dan `--max-capacity` ke `network application-gateway [create|update]`

### <a name="resource"></a>Sumber daya
* Meningkatkan pesan kesalahan dari `deployment create` saat tidak ada TTY yang tersedia

### <a name="role"></a>Peran
* Memperbarui pesan teks.

### <a name="compute"></a>Compute
* Menambahkan dukungan ke `vm create` untuk Mesin Virtual dari gambar terkelola dengan luns disk data yang tidak dimulai dari 0 atau yang melewati angka

## <a name="may-21-2019"></a>21 Mei 2019

Versi 2.0.65

### <a name="core"></a>Core
* Menambahkan umpan balik yang lebih baik untuk kesalahan autentikasi
* Memperbaiki masalah saat CLI akan memuat ekstensi yang tidak kompatibel dengan versi intinya
* Memperbaiki masalah peluncuran saat `clouds.config` rusak

### <a name="acr"></a>Azure Container Registry
* Menambahkan dukungan untuk Identitas Terkelola ke Tugas

### <a name="acs"></a>ACS
* Memperbaiki perintah `openshift create` saat digunakan dengan klien Azure Active Directory pelanggan

### <a name="appservice"></a>AppService
* [DEPRECATED] Menghentikan perintah `functionapp devops-build` - akan dihapus pada rilis berikutnya
* Mengubah `functionapp devops-pipeline` untuk mengambil log build dari Azure DevOps dalam mode verbose
* [BREAKING CHANGE] Menghapus bendera `--use_local_settings` dari perintah `functionapp devops-pipeline` - merupakan no-op
* Mengubah `webapp up` untuk mengembalikan output JSON jika `--logs` tidak digunakan
* Menambahkan dukungan untuk menulis sumber daya default ke konfigurasi lokal untuk `webapp up`
* Menambahkan dukungan ke `webapp up` untuk menyebarkan ulang aplikasi tanpa menggunakan argumen `--location`
* Memperbaiki masalah saat pembuatan ASP SKU Gratis Linux menggunakan Gratis karena nilai SKU tidak berfungsi

### <a name="botservice"></a>BotService
* Mengubah untuk mengizinkan semua kapitalisasi untuk parameter `--lang` untuk perintah
* Memperbarui deskripsi untuk modul perintah

### <a name="consumption"></a>Consumption
* Menambahkan parameter wajib yang hilang saat menjalankan `consumption usage list --billing-period-name`

### <a name="iot"></a>IoT
* Menambahkan dukungan untuk mencantumkan semua kunci

### <a name="network"></a>Jaringan
* [BREAKING CHANGE]: Removed `network interface-endpoints` command group - use `network private-endpoints`
* Menambahkan argumen `--nat-gateway` ke `network vnet subnet [create|update]` untuk melampirkan ke gateway NAT
* Memperbaiki masalah dengan `dns zone import` saat nama catatan tidak cocok dengan jenis catatan

### <a name="rdbms"></a>RDBMS
* Menambahkan dukungan postgres dan mysql untuk replikasi geografis

### <a name="rbac"></a>RBAC
* Menambahkan dukungan untuk cakupan grup manajemen ke `role assignment`

### <a name="storage"></a>Penyimpanan
* `storage blob sync`: menambhakan perintah sinkronisasi untuk blob penyimpanan

### <a name="compute"></a>Compute
* Menambahkan `--computer-name` ke `vm create` untuk mengatur nama komputer Mesin Virtual
* Mengganti nama `--ssh-key-value` menjadi `--ssh-key-values` untuk `[vm|vmss] create` - sekarang dapat menerima beberapa nilai atau jalur kunci umum ssh
  * __Catatan__: Ini **bukan** perubahan yang melanggar - `--ssh-key-value` akan diuraikan dengan benar karena hanya cocok dengan `--ssh-key-values`
* Mengubah argumen `--type` dari `ppg create` menjadi opsional

## <a name="may-6-2019"></a>6 Mei 2019

Versi 2.0.64

### <a name="acs"></a>ACS
* [BREAKING CHANGE] Menghapus bendera `--fqdn` pada perintah `openshift`
* Mengubah untuk menggunakan Versi API Ketersediaan Umum Azure Red Hat Openshift
* Menambahkan bendera `customer-admin-group-id` ke `openshift create`
* [GA] Menghapus `(PREVIEW)` dari opsi `aks create` `--network-policy`

### <a name="appservice"></a>Appservice
* [DEPRECATED] Menghentikan perintah `functionapp devops-build`
  * Mengganti nama menjadi `functionapp devops-pipeline`
* Memperbaiki mendapatkan nama pengguna yang benar untuk cloudshell yang menyebabkan `webapp up` gagal
* Memperbarui dokumentasi `appservice plan --sku` untuk mencerminkan appserviceplans yang didukung
* Menambahkan argumen opsional untuk grup sumber daya dan merencanakan ke `webapp up`
* Menambahkan dukungan ke `webapp ssh` untuk mematuhi variabel lingkungan `AZURE_CLI_DISABLE_CONNECTION_VERIFICATION`
* Menambahkan dukungan `appserviceplan create` untuk SKU Gratis Linux
* Mengubah `webapp up` menjadi tidur 30 detik setelah mengatur appsetting `SCM_DO_BUILD_DURING_DEPLOYMENT=true` untuk menangani mulai dingin kudu
* Menambahkan dukungan untuk runtime `powershell` ke `functionapp create` di Windows
* Menambahkan perintah `create-remote-connection`

### <a name="batch"></a>Batch
* Memperbaiki bug di validator untuk opsi `--application-package-references`

### <a name="botservice"></a>Botservice
* [BREAKING CHANGE] Mengubah `bot create -v v4 -k webapp` untuk membuat Bot Aplikasi Web kosong secara default (yaitu tidak ada bot yang disebarkan ke App Service)
* Menambahkan bendera `--echo` ke `bot create` untuk menggunakan perilaku lama dengan `-v v4`
* [BREAKING CHANGE] Mengubah nilai default `--version` menjadi `v4`
  * __NOTE:__ `bot prepare-publish` masih menggunakan default lama
* [BREAKING CHANGE] Mengubah `--lang` menjadi tidak lagi default ke `Csharp`. Jika perintah memerlukan `--lang` dan tidak disediakan, perintah sekarang akan mengalami kesalahan
* [BREAKING CHANGE] Mengubah argumen `--appid` dan `--password` untuk `bot create` menjadi wajib dan sekarang dapat dibuat melalui `ad app create`
* Menambahkan validasi `--appid` dan `--password`
* [BREAKING CHANGE] Mengubah `bot create -v v4` untuk tidak membuat atau menggunakan Akun Penyimpanan atau Application Insights
* [BREAKING CHANGE] Mengubah `bot create -v v3` untuk mewajibkan wilayah tempat Application Insights tersedia
* [BREAKING CHANGE] Mengubah `bot update` untuk sekarang hanya memengaruhi properti bot tertentu
* [BREAKING CHANGE] Mengubah bendera `--lang` untuk menerima `Javascript` bukan `Node`
* [BREAKING CHANGE] Menghapus `Node` sebagai nilai `--lang` yang diizinkan
* [BREAKING CHANGE] Mengubah `bot create -v v4 -k webapp` menjadi tidak lagi mengatur `SCM_DO_BUILD_DURING_DEPLOYMENT` ke true. Semua penyebaran melalui Kudu akan bertindak sesuai dengan perilaku default penyebaran
* Mengubah `bot download` untuk bot tanpa file `.bot` untuk membuat file konfigurasi khusus bahasa dengan nilai dari Pengaturan Aplikasi untuk bot
* Menambahkan dukungan `Typescript` ke `bot prepare-deploy`
* Menambahkan pesan peringatan ke bot `bot prepare-deploy` untuk `Javascript` dan `Typescript` jika `--code-dir` tidak berisi `package.json`
* Mengubah `bot prepare-deploy` untuk mengembalikan `true` jika berhasil
* Menambahkan pengelogan verbose ke `bot prepare-deploy`
* Menambahkan lebih banyak wilayah Application Insights yang tersedia ke `az bot create -v v3`

### <a name="configure"></a>Konfigurasikan
* Menambahkan dukungan untuk konfigurasi nilai default argumen berbasis folder

### <a name="eventhubs"></a>Eventhubs
* Menambahkan perintah `namespace network-rule`
* Menambahkan argumen `--default-action` untuk aturan jaringan ke `namespace [create|update]`

### <a name="network"></a>Jaringan
* [BREAKING CHANGE] Mengganti argumen `--cache` dengan `--defer` untuk `vnet [create|update]`

### <a name="policy-insights"></a>Policy Insights
* Menambahkan dukungan untuk `--expand PolicyEvaluationDetails` guna mengkueri detail evaluasi kebijakan pada sumber daya

### <a name="role"></a>Peran
* [DEPRECATED] Mengubah `create-for-rbac` argumen sembunyikan '--password' - dukungan akan dihapus pada Mei 2019

### <a name="service-bus"></a>Service Bus
* Menambahkan perintah `namespace network-rule`
* Menambahkan argumen `--default-action` untuk aturan jaringan ke `namespace [create|update]`
* Memperbaiki `topic [create|update]` untuk mengizinkan dukung `--max-size` untuk nilai 10, 20, 40, dan 80 GB dengan SKU premium

### <a name="sql"></a>SQL
* Menambahkan perintah `sql virtual-cluster [list|show|delete]`

### <a name="vm"></a>VM
* Menambahkan `--protect-from-scale-in` dan `--protect-from-scale-set-actions` ke `vmss update` untuk mengaktifkan pembaruan pada kebijakan perlindungan instans Mesin Virtual VMSS
* Menambahkan `--instance-id` ke `vmss update` untuk mengaktifkan pembaruan umum instans Mesin Virtual VMSS
* Menambahkan `--instance-id` ke `vmss wait`
* Menambahkan grup perintah `ppg` baru untuk mengelola Grup Penempatan Kedekatan
* Menambahkan `--ppg` ke `[vm|vmss] create` dan `vm availability-set create` untuk mengelola PPG
* Menambahkan parameter `--hyper-v-generation` ke `image create`

## <a name="april-23-2019"></a>########

Versi 2.0.63

### <a name="acs"></a>ACS
* Mengubah `aks get-credentials` guna meminta untuk menimpa nilai yang digandakan
* Menghapus `(PREVIEW)` dari perintah Dev Spaces "aks use-dev-spaces" dan "aks remove-dev-spaces"

### <a name="ams"></a>AMS
* Memperbaiki bug dengan pembaruan filter aset dan akun

### <a name="appservice"></a>AppService
* Menambahkan dukungan untuk ASE dan batas waktu ke `webapp ssh`
* Menambahkan dukungan untuk membuat CI CD ke alur Azure DevOps dari repositori Github ke aplikasi Fungsi
* Menambahkan argumen `--github-pat` ke `functionapp devops-build create` untuk menerima token akses pribadi Github
* Menambahkan argumen `--github-repository` ke `functionapp devops-build create` untuk menerima repositori Github yang berisi kode sumber functionapp
* Memperbaiki masalah saat `az webapp up --logs` gagal dengan kesalahan dan memperbarui versi .NETCORE default ke 2.1
* Menghapus pengaturan functionapp yang tidak perlu saat membuat aplikasi fungsi dengan paket penggunaan
* Mengubah `webapp up` sehingga string asp default sekarang menambahkan nomor di akhir untuk membuat ASP baru berdasarkan opsi SKU
* Menambahkan `-b` sebagai opsi untuk `webapp up` guna meluncurkan aplikasi di browser
* Mengubah `webapp deployment source config zip` untuk menangani variabel lingkungan `AZURE_CLI_DISABLE_CONNECTION_VERIFICATION`

### <a name="deployment-manager"></a>Deployment Manager
* [PREVIEW] Membuat dan mengelola artefak yang mendukung peluncuran

### <a name="lab"></a>Laboratorium
* Memperbaiki bug yang akan menyebabkan keluar lebih awal

### <a name="network"></a>Jaringan
* Menambahkan delegasi server nama otomatis ke `dns zone create` di induk selama pembuatan zona turunan

### <a name="resource"></a>Sumber daya
* [DEPRECATED] Menghentikan argumen `--link-id`, `--target-id`, dan `--filter-string` dari `resource link`
  * Menggunakan argumen `--link`, `--target`, dan `--filter` sebagai gantinya
* Memperbaiki masalah saat perintah `resource link [create|update]` tidak berfungsi
* Memperbaiki masalah saat menghapus menggunakan ID sumber daya dapat menyebabkan error

### <a name="sql"></a>SQL
* Menambahkan dukungan untuk zona waktu kustom pada instans terkelola
* Mengubah untuk mengizinkan nama kumpulan elastis digunakan dengan `sql db update`
* Menambahkan dukungan `--no-wait` ke `sql server [create|update]`
* Menambahkan perintah `sql server wait`

### <a name="storage"></a>Penyimpanan
* Memperbaiki masalah dengan token SAS yang dikodekan secara ganda di `storage blob generate-sas`

### <a name="vm"></a>VM
* Menambahkan bendera `--skip-shutdown` ke `vm|vmss stop` untuk menonaktifkan Mesin Virtual tanpa mematikan
* Menambahkan argumen `--storage-account-type` ke `sig image-version create` untuk mengatur jenis akun profil penerbitan
* Menambahkan argumen `--target-regions` ke `sig image-version create` untuk mengizinkan dalam mengatur jenis akun penyimpanan khusus wilayah

## <a name="april-9-2019"></a>9 April 2019

### <a name="core"></a>Core
* Memperbaiki masalah saat beberapa ekstensi menunjukkan versi `Unknown` dan tidak dapat diperbarui

### <a name="acr"></a>Azure Container Registry
* Menambahkan dukungan menjalankan gambar tanpa konteks

### <a name="ams"></a>AMS
* [DEPRECATED]: Deprecated the `--bitrate` parameter of `account-filter` and `asset-filter`
* [BREAKING CHANGE]: Renamed the `--bitrate` parameter to `--first-quality`
* Menambahkan dukungan parameter enkripsi baru di `ams streaming-policy create`
* Menambahkan parameter baru `--filters` ke `ams streaming-locator create`

### <a name="appservice"></a>AppService
* Menambahkan dukungan `--logs` ke `webapp up`
* Memperbaiki masalah pembuatan perintah `functionapp devops-build create` `azure-pipelines.yml`
* Meningkatkan penanganan kesalahan dan indikator `unctionapp devops-build create`
* [BREAKING CHANGE] Menghapus bendera `--local-git` untuk perintah `devops-build`, deteksi dan penanganan git lokal wajib untuk membuat alur Azure DevOps
* Menambahkan dukungan untuk pembuatan paket fungsi Linux
* Menambahkan kemampuan untuk mengganti paket di bawah aplikasi fungsi menggunakan `functionapp update --plan`
* Menambahkan dukungan untuk pengaturan peluasan skala paket premium Azure Functions

### <a name="cdn"></a>CDN
* Menambahkan dukungan untuk `Microsoft_Standard` dan `Standard_ChinaCdn`

### <a name="feedback-reference"></a>Referensi umpan balik
* Mengubah `feedback` untuk menampilkan metadata pada perintah yang baru saja dijalankan
* Mengubah `feedback` untuk meminta pengguna membantu dalam proses pembuatan masalah dengan membuka browser dan menggunakan templat masalah
* Mengubah `feedback` untuk mencetak isi masalah saat dijalankan dengan '--verbose'

### <a name="monitor"></a>Monitor
* Memperbaiki masalah saat "jumlah" bukan nilai yang diizinkan dengan `metrics alert [create|update]`

### <a name="network"></a>Jaringan
* Memperbaiki format tabel yang tidak ditampilkan dengan `vnet-gateway list-bgp-peer-status`
* Menambahkan perintah `list-request-headers` dan `list-response-headers` ke `application-gateway rewrite-rule`
* Menambahkan perintah `list-server-variables` ke `application-gateway rewrite-rule condition`
* Memperbaiki masalah saat memperbarui status tautan pada port rute ekspres akan memunculkan pengecualian atribut yang tidak diketahui `express-route port update`

### <a name="privatedns"></a>PrivateDNS
* Menambahkan `network private-dns` untuk zona DNS Privat

### <a name="resource"></a>Sumber daya
* Memperbaiki masalah dengan `deployment create` dan `group deployment create` saat file parameter dengan kumpulan parameter kosong tidak akan berfungsi

### <a name="role"></a>Peran
* Memperbaiki `create-for-rbac` untuk menangani `--years` dengan benar
* [BREAKING CHANGE] Mengubah `role assignment delete` untuk meminta saat menghapus semua penugasan di bawah langganan tanpa syarat

### <a name="sql"></a>SQL
* Memperbarui `sql mi [create|update]` dengan properti proxyOverride dan publicDataEndpointEnabled

### <a name="storage"></a>Penyimpanan
* [BREAKING CHANGE] Menghapus hasil dari `storage blob delete`
* Menambahkan `--full-uri` ke `storage blob generate-sas` untuk membuat uri lengkap untuk blob dengan sas
* Menambahkan `--file-snapshot` ke `storage file copy start` untuk menyalin file dari snapshot
* Mengubah `storage blob copy cancel` agar hanya menampilkan kesalahan bukan pengecualian untuk NoPendingCopyOperation

## <a name="march-26-2019"></a>26 Maret 2019


### <a name="core"></a>Core
* Memperbaiki masalah dengan ketidakcocokan ekstensi pengembang
* Penanganan kesalahan sekarang mengarahkan pelanggan ke halaman masalah

### <a name="cloud"></a>Cloud
* Memperbaiki kesalahan 'langganan tidak ditemukan' di `cloud set`

### <a name="acr"></a>Azure Container Registry
* Memperbaiki sumber redundan dalam impor gambar
* Menambahkan `--auth-mode` ke perintah `acr build`, `acr run`, `acr task create`, dan `acr task update`
* Menambahkan grup perintah 'acr task credential' untuk mengelola kredensial untuk Tugas
* Menambahkan '--no-wait' ke perintah `acr build`

### <a name="appservice"></a>AppService
* Memperbaiki bug saat `webapp up` tidak menangani menjalankan dari direktori kosong atau skenario kode yang tidak dikenal dengan benar
* Memperbaiki bug saat slot tidak berfungsi untuk `[webapp|functionapp] config ssl bind`

### <a name="bot-service"></a>Layanan BOT
* Menambahkan `bot prepare-deploy` untuk mempersiapkan penyebaran bot melalui `webapp`
* Mengubah `bot create --kind registration` untuk menunjukkan kata sandi jika kata sandi tidak diberikan
* [BREAKING CHANGE] Mengubah `--endpoint` di `bot create --kind registration` menjadi default ke string kosong daripada saat diperlukan
* Menambahkan `SCM_DO_BUILD_DURING_DEPLOYMENT` ke Pengaturan Aplikasi templat Azure Resource Manager untuk Bot Aplikasi Web v4

### <a name="cdn"></a>CDN
* Menambahkan dukungan untuk `--no-wait` ke `cdn endpoint [create|update|start|stop|delete|load|purge]`
* [BREAKING CHANGE]: Mengubah perilaku penembolokan string kueri default `cdn endpoint create`. Tidak lagi default ke "IgnoreQueryString". Sekarang diatur oleh layanan

### <a name="cosmosdb"></a>Cosmosdb
* Menambahkan dukungan untuk `--enable-multiple-write-locations` pada pembaruan akun
* Menambahkan subgrup `network-rule` dengan perintah `add`, `remove`, dan `list` untuk mengelola aturan VNET akun Azure Cosmos DB

### <a name="interactive"></a>Interaktif
* Memperbaiki ketidakcocokan dengan ekstensi Interaktif yang diinstal melalui azdev

### <a name="monitor"></a>Monitor
* Mengubah untuk mengizinkan nilai dimensi `*` untuk `monitor metrics alert [create|update]`

### <a name="network"></a>Jaringan
* Menambahkan grup perintah `rewrite-rule` ke `application-gateway`

### <a name="profile"></a>Profil
* Menambahkan dukungan akun tingkat penyewa untuk identitas layanan terkelola ke `login`

### <a name="postgres"></a>Postgres
* Menambahkan perintah `replica` postgresql dan perintah `restart server`
* Mengubah untuk mendapatkan lokasi default dari grup sumber daya saat tidak disediakan untuk membuat server dan menambahkan validasi untuk durasi retensi

### <a name="resource"></a>Sumber daya
* Meningkatkan output tabel untuk `deployment [create|list|show]`
* Memperbaiki masalah dengan `deployment [create|validate]` saat secureObject jenis tidak dikenali

### <a name="graph"></a>Graph
* Menambahkan dukungan untuk `--end-date` ke `ad [app|sp] credential reset`
* Menambahkan dukungan untuk menambahkan izin dengan `ad app permission add`
* Memperbaiki bug dengan `ad app permission list` saat tidak ada izin
* Mengubah `ad sp delete` untuk melewati penghapusan penetapan peran jika akun saat ini belum memiliki langganan
* Mengubah `ad app create` menjadi default `--identifier-uris` ke daftar kosong jika tidak disediakan

### <a name="storage"></a>penyimpanan
* Menambahkan `--snapshot` ke `storage file download-batch` untuk mengunduh dari snapshot berbagi
* Mengubah bilah kemajuan `storage blob [download-batch|upload-batch]` menjadi singkat dan menunjukkan blob saat ini
* Memperbaiki masalah dengan `storage account update` saat memperbarui parameter enkripsi
* Memperbaiki masalah saat `storage blob show` akan gagal saat menggunakan oauth (`--auth-mode=login`)

### <a name="vm"></a>VM
* Menambahkan perintah `image update`

## <a name="march-12-2019"></a>12 Maret 2019

Versi 2.0.60

### <a name="core"></a>Core

* Memperbaiki kesalahan yang salah di `cloud set` tentang langganan tidak ditemukan

### <a name="acr"></a>Azure Container Registry

* Memperbaiki sumber redundan dalam impor gambar

### <a name="acs"></a>ACS

* Mengubah untuk mengabaikan parameter `--listen-address` untuk `aks browse` jika tidak didukung oleh kubectl

### <a name="appservice"></a>AppService

* Menambahkan `[webapp|functionapp] deployment list-publishing-credentials` untuk mendapatkan url penerbitan Kudu dan kredensial Kudu
* Menghapus pernyataan cetak yang salah untuk `webapp auth update`
* Memperbaiki `functionapp` untuk mengatur gambar yang benar untuk runtime di paket App Service Linux
* Menghapus tag pratinjau untuk `webapp up` dan menambahkan peningkatan pada perintah

### <a name="botservice"></a>Botservice

* Menambahkan `SCM_DO_BUILD_DURING_DEPLOYMENT` ke Pengaturan Aplikasi templat Azure Resource Manager untuk Bot Aplikasi Web v4
* Menambahkan `Microsoft-BotFramework-AppId` dan `Microsoft-BotFramework-AppPassword` ke Pengaturan Aplikasi templat Azure Resource Manager untuk Bot Aplikasi Web v4
* Menghapus kutipan tunggal dari output perintah `bot publish` di akhir `bot create`
* Mengubah `bot publish` menjadi asinkron

### <a name="container"></a>Kontainer

* Menambahkan argumen `--no-wait` ke `container [start|restart]`

### <a name="eventhub"></a>EventHub

* Menambahkan bendera `--skip-empty-archives` ke `eventhub create|update` untuk mendukung arsip kosong dalam pengambilan

### <a name="find"></a>Cari

* Pembaruan fungsionalitas utama

### <a name="hdinsight"></a>HDInsight

* Menambahkan parameter `--storage-account-managed-identity` ke `hdinsight create` untuk mendukung ADLS Gen2 MSI

### <a name="network"></a>Jaringan

* Memperbaiki masalah dengan `vpn-connection update` saat memperbarui koneksi VPN di antara gateway dalam langganan yang berbeda akan gagal

### <a name="rdbms"></a>Rdbms

* Perbaikan kecil untuk mendapatkan lokasi default dari grup sumber daya saat tidak disediakan untuk membuat server dan menambahkan validasi untuk durasi retensi

### <a name="role"></a>Peran

* Memperbaiki `role definition update` untuk menggunakan ID guna menyelesaikan definisi dengan benar
* Mengubah `ad app credential reset` untuk menghapus asumsi bahwa perwakilan layanan aplikasi selalu ada

### <a name="service-fabric"></a>Service Fabric

* Memperbaiki masalah dengan `sf cluster list` tidak dapat diubah

## <a name="february-26-2019"></a>26 Februari 2019

Versi 2.0.59

### <a name="core"></a>Core

* Memperbaiki masalah saat dalam beberapa kasus menggunakan `--subscription NAME` akan menimbulkan pengecualian

### <a name="acr"></a>Azure Container Registry

* Menambahkan parameter `--target` untuk perintah `acr build`, `acr task create` dan `acr task update`
* Meningkatkan penanganan kesalahan untuk perintah runtime saat tidak masuk ke Azure

### <a name="acs"></a>ACS

* Menambahkan opsi `--listen-address` ke `aks port-forward`

### <a name="appservice"></a>AppService

* Menambahkan perintah `functionapp devops-build`

### <a name="batch"></a>Batch
* [BREAKING CHANGE] Menghapus perintah `batch pool upgrade os`
* [BREAKING CHANGE] Menghapus properti `Pacakges` dari respons `Application`
* Menambahkan perintah `batch application package list` ke daftar paket aplikasi
* [BREAKING CHANGE] Mengubah `--application-id` menjadi `--application-name` di semua perintah `batch application`,
* Menambahkan argumen `--json-file` ke perintah untuk meminta respons API mentah
* Memperbarui validasi untuk secara otomatis menyertakan `https://` di semua titik akhir jika tidak ada

### <a name="cosmosdb"></a>CosmosDB

* Menambahkan subgrup `network-rule` dengan perintah `add`, `remove`, dan `list` untuk mengelola aturan VNET akun Azure Cosmos DB

### <a name="kusto"></a>Kusto

* [BREAKING CHANGE] Mengubah jenis `hot_cache_period` dan `soft_delete_period` untuk database ke format durasi ISO8601

### <a name="network"></a>Jaringan

* Menambahkan argumen `--express-route-gateway-bypass` ke `vpn-connection [create|update]`
* Menambahkan grup perintah dari ekstensi `express-route`
* Menambahkan grup perintah `express-route gateway` dan `express-route port`
* Menambahkan argumen `--legacy-mode` ke `express-route peering [create|update]`
* Menambahkan argumen `--allow-classic-operations` dan `--express-route-port` ke `express-route [create|update]`
* Menambahkan argumen `--gateway-default-site` ke `vnet-gateway [create|update]`
* Menambahkan perintah `ipsec-policy` ke `vnet-gateway`

### <a name="resource"></a>Sumber daya

* Memperbaiki masalah dengan `deployment create` saat bidang jenis merupakan peka huruf besar/kecil
* Menambahkan dukungan untuk file parameter berbasis URI ke `policy assignment create`
* Menambahkan dukungan untuk parameter dan definisi berbasis URI ke `policy set-definition update`
* Memperbaiki penanganan parameter dan aturan untuk `policy definition update`
* Memperbaiki masalah dengan `resource show/update/delete/tag/invoke-action` saat ID lintas langganan tidak mematuhi ID langganan dengan benar

### <a name="role"></a>Peran

* Menambahkan dukungan untuk peran aplikasi ke `ad app [create|update]`

### <a name="vm"></a>VM

* Memperbaiki masalah dengan `vm create where `--accelerated-networking` tidak diaktifkan secara default untuk Ubuntu 18.0

## <a name="february-12-2019"></a>12 Februari 2019

Versi 2.0.58

### <a name="core"></a>Core

* `az --version` sekarang menunjukkan pemberitahuan jika Anda memiliki paket yang dapat diperbarui
* Memperbaiki regresi saat `--ids` tidak dapat lagi digunakan dengan output JSON

### <a name="acr"></a>Azure Container Registry
* [BREAKING CHANGE] Menghapus grup perintah `acr build-task`
* [BREAKING CHANGE] Menghapus opsi `--tag` dan `--manifest` dari `acr repository delete`

### <a name="acs"></a>ACS
* Menambahkan dukungan untuk nama peka huruf besar/kecil ke `aks [enable-addons|disable-addons]`
* Menambahkan dukungan untuk operasi pembaruan Azure Active Directory menggunakan `aks update-credentials --reset-aad`
* Menambahkan klarifikasi bahwa `--output` diabaikan untuk `aks get-credentials`

### <a name="ams"></a>AMS
* Menambahkan perintah `ams streaming-endpoint [start | stop | create | update] wait`
* Menambahkan perintah `ams live-event [create | start | stop | reset] wait`

### <a name="appservice"></a>Appservice
* Menambahkan kemampuan untuk membuat dan mengonfigurasi fungsi menggunakan kontainer Azure Container Registry
* Menambahkan dukungan untuk memperbarui konfigurasi webapp melalui json
* Meningkatkan bantuan untuk `appservice-plan-update`
* Menambahkan dukungan untuk wawasan aplikasi pada pembuatan functionapp
* Memperbaiki masalah dengan SSH webapp

### <a name="botservice"></a>Botservice
* Meningkatkan UX untuk `bot publish`
* Menambahkan peringatan untuk batas waktu saat menjalankan `npm install` selama `az bot publish`
* Menghapus char tidak valid `.` dari `--name` di `az bot create`
* Mengubah untuk berhenti mengacak nama sumber daya saat membuat Azure Storage, Paket App Service, Fungsi/Aplikasi Web, dan Application Insights
* [DEPRECATED] Menghentikan argumen `--proj-name` yang mendukung `--proj-file-path`
* Mengubah `az bot publish` untuk menghapus file penyebaran IIS Node.js yang diambil jika belum ada
* Menambahkan argumen `--keep-node-modules` ke `az bot publish` agar tidak menghapus folder `node_modules` di App Service
* Menambahkan pasangan kunci-nilai `"publishCommand"` ke output dari `az bot create` saat membuat Azure Function atau bot Aplikasi Web
  * Nilai `"publishCommand"` adalah perintah `az bot publish` yang diisi sebelumnya dengan parameter yang dibutuhkan untuk menerbitkan bot yang baru dibuat
* Memperbarui `"WEBSITE_NODE_DEFAULT_VERSION"` dalam templat Azure Resource Manager untuk bot SDK v4 untuk menggunakan 10.14.1, bukan 8.9.4

### <a name="key-vault"></a>Key Vault
* Memperbaiki masalah dengan `keyvault secret backup` saat beberapa pengguna menerima kesalahan `unexpected_keyword` saat menggunakan `--id`

### <a name="monitor"></a>Monitor
* Mengubah `monitor metrics alert [create|update]` untuk mengizinkan nilai dimensi `*`

### <a name="network"></a>Jaringan
* Mengubah `dns zone export` untuk memastikan data CNAME yang diekspor adalah nama domain yang sepenuhnya memenuhi syarat
* Menambahkan parameter `--gateway-name` ke `nic ip-config address-pool [add|remove]` untuk mendukung kumpulan alamat backend gateway aplikasi
* Menambahkan argumen `--traffic-analytics` dan `--workspace` ke `network watcher flow-log configure` untuk mendukung analitik lalu lintas melalui ruang kerja Analitik Log
* Menambahkan `--idle-timeout` dan `--floating-ip` ke `lb inbound-nat-pool [create|update]`

### <a name="policy-insights"></a>Policy Insights
* Menambahkan perintah `policy remediation` untuk mendukung fitur remediasi kebijakan sumber daya

### <a name="rdbms"></a>RDBMS
* Meningkatkan pesan bantuan dan parameter perintah

### <a name="redis"></a>Redis
* Menambahkan perintah untuk mengelola aturan firewall (membuat, memperbarui, menghapus, menampilkan, mencantumkan)
* Menambahkan perintah untuk mengelola tautan server (membuat, menghapus, menampilkan, mencantumkan)
* Menambahkan perintah untuk mengelola jadwal patch (membuat, memperbarui, menghapus, menampilkan)
* Menambahkan dukungan untuk Zona Ketersediaan dan Versi TLS Minimum ke `redis create
* [BREAKING CHANGE] Menghapus perintah `redis update-settings` dan `redis list-all`
* [BREAKING CHANGE] Parameter untuk `redis create`: 'pengaturan penyewa' tidak diterima dalam format key[=value]
* [DEPRECATED] Menambahkan pesan peringatan untuk menghentikan perintah `redis import-method`

### <a name="role"></a>Peran
* [BREAKING CHANGE] Memindahkan perintah `az identity` ke sini dari perintah `vm`

### <a name="sql-vm"></a>SQL VM
* [DEPRECATED] Menghentikan argumen `--boostrap-acc-pwd` karena kesalahan penulisan

### <a name="vm"></a>VM
* Mengubah `vm list-skus` untuk mengizinkan penggunaan `--all` sebagai ganti dari `--all true`
* Menambahkan `vmss run-command [invoke | list | show]`
* Memperbaiki bug saat `vmss encryption enable` akan gagal jika dijalankan sebelumnya
* [BREAKING CHANGE] Memindahkan perintah `az identity` ke perintah `role`

## <a name="january-31-2019"></a>31 Januari 2019

Versi 2.0.57

### <a name="core"></a>Core

* Perbaikan Terbaru untuk [masalah 8399](https://github.com/Azure/azure-cli/issues/8399).

## <a name="january-28-2019"></a>28 Januari 2019

Versi 2.0.56

### <a name="acr"></a>Azure Container Registry
* Menambahkan dukungan untuk aturan VNet/IP

### <a name="acs"></a>ACS
* Menambahkan Pratinjau Node Virtual
* Menambahkan perintah OpenShift Terkelola
* Menambahkan dukungan untuk operasi pembaruan perwakilan layanan dengan `aks update-credentials -reset-service-principal`

### <a name="ams"></a>AMS
* [BREAKING CHANGE] Mengganti nama `ams asset get-streaming-locators` menjadi `ams asset list-streaming-locators`
* [BREAKING CHANGE] Mengganti nama `ams streaming-locator get-content-keys` menjadi `ams streaming-locator list-content-keys`

### <a name="appservice"></a>Appservice
* Menambahkan dukungan untuk wawasan aplikasi di `functionapp create`
* Menambahkan dukungan untuk pembuatan paket layanan aplikasi (termasuk Elastic Premium) ke Aplikasi Fungsi
* Memperbaiki masalah pengaturan aplikasi dengan paket Elastic Premium

### <a name="container"></a>Kontainer
* Menambahkan perintah `container start`
* Mengubah untuk memungkinkan penggunaan nilai desimal untuk CPU selama pembuatan kontainer

### <a name="eventgrid"></a>EventGrid
* Menambahkan parameter `--deadletter-endpoint` ke `event-subscription [create|update]`
* Menambahkan storagequeue dan hybridconnection sebagai nilai baru untuk 'event-subscription [create|update] --endpoint-type`
* Menambahkan parameter `--max-delivery-attempts` dan `--event-ttl` ke `event-subscription create` untuk menentukan kebijakan percobaan kembali untuk peristiwa
* Menambahkan pesan peringatan ke `event-subscription [create|update]` saat webhook sebagai tujuan digunakan untuk langganan peristiwa
* Menambahkan parameter source-resource-id untuk semua perintah terkait langganan peristiwa dan menandai semua parameter terkait sumber daya sumber lainnya sebagai tidak digunakan lagi

### <a name="hdinsight"></a>HDInsight
* [BREAKING CHANGE] Menghapus parameter `--virtual-network` dan `--subnet-name` dari `hdinsight [application] create`
* [BREAKING CHANGE] Mengubah `hdinsight create --storage-account` untuk menerima nama atau id akun penyimpanan, bukan titik akhir blob
* Menambahkan parameter `--vnet-name` dan `--subnet-name` ke `hdinsight create`
* Menambahkan dukungan untuk Paket Keamanan Enterprise dan enkripsi disk ke `hdinsight create`
* Menambahkan perintah `hdinsight rotate-disk-encryption-key`
* Menambahkan perintah `hdinsight update`

### <a name="iot"></a>IoT
* Menambahkan format pengodean ke perintah perutean-titik akhir

### <a name="kusto"></a>Kusto
* Rilis pratinjau

### <a name="monitor"></a>Monitor
* Mengubah perbandingan ID menjadi tidak peka huruf besar/kecil

### <a name="profile"></a>Profil
* Mengaktifkan akun tingkat penyewa untuk identitas layanan terkelola untuk `login`

### <a name="network"></a>Jaringan
* Memperbaiki masalah dengan `express-route update`: saat argumen `--bandwidth` diabaikan
* Memperbaiki masalah dengan `ddos-protection update` saat pemahaman set menyebabkan jejak tumpukan

### <a name="resource"></a>Sumber daya
* Menambahkan dukungan untuk file parameter URI ke `group deployment create`
* Menambahkan dukungan untuk identitas terkelola ke `policy assignment [create|list|show]`

### <a name="sql-virtual-machine"></a>Mesin Virtual SQL
* Rilis pratinjau

### <a name="storage"></a>Penyimpanan
* Mengubah perbaikan untuk memperbarui hanya properti yang diubah pada objek yang sama
* Memperbaiki #8021, data biner dikodekan dalam base 64 saat ditampilkan

### <a name="vm"></a>VM
* Mengubah `vm encryption enable` untuk memvalidasi keyvault enkripsi disk dan keyvault enkripsi kunci tersebut ada
* Menambahkan bendera `--force` ke `vm encryption enable`

## <a name="january-15-2019"></a>15 Januari 2019

Versi 2.0.55

### <a name="acr"></a>Azure Container Registry
* Mengubah untuk memungkinkan pendorongan paksa bagan helm yang tidak ada
* mengubah untuk memungkinkan operasi runtime tanpa permintaan Azure Resource Manager
* [DEPRECATED] Menghentikan parameter `--resource-group` di perintah:
  * `acr login`
  * `acr repository`
  * `acr helm`

### <a name="acs"></a>ACS
* Menambahkan dukungan untuk wilayah ACI baru

### <a name="appservice"></a>Appservice
* Memperbaiki masalah dengan mengunggah sertifikat untuk aplikasi yang dihosting di ASE, saat ASE RG & App RG berbeda
* Mengubah `webapp up` untuk menggunakan SKU P1V1 sebagai default untuk Linux
* Memperbaiki `[webapp|functionapp] deployment source config-zip` untuk menampilkan pesan kesalahan yang tepat saat penyebaran gagal
* Menambahkan perintah `webapp ssh`

### <a name="botservice"></a>Botservice
* Menambahkan pembaruan status penyebaran ke `bot create`

### <a name="configure"></a>Konfigurasikan
* Menambahkan `none` sebagai format output yang dapat dikonfigurasi

### <a name="cosmosdb"></a>CosmosDB
* Menambahkan dukungan untuk membuat database dengan throughput bersama

### <a name="hdinsight"></a>HDInsight
* Menambahkan perintah untuk mengelola aplikasi
* Menambahkan perintah untuk mengelola tindakan skrip
* Menambahkan perintah untuk mengelola Operations Management Suite (OMS)
* Menambahkan dukungan untuk mencantumkan penggunaan regional ke `hdinsight list-usage`
* [BREAKING CHANGE] Menghapus jenis kluster default dari `hdinsight create`

### <a name="network"></a>Jaringan
* Menambahkan argumen `--custom-headers` dan `--status-code-ranges` ke `traffic-manager profile [create|update]`
* Menambahkan jenis perutean baru: Subnet dan Multinilai
* Menambahkan argumen `--custom-headers` dan `--subnets` ke `traffic-manager endpoint [create|update]`
* Memperbaiki masalah saat memasok `--vnets ""` ke `ddos-protection update` menyebabkan kesalahan

### <a name="role"></a>Peran
* [DEPRECATED] Menghentikan argumen `--password` untuk `create-for-rbac`. Menggunakan kata sandi aman yang dihasilkan oleh CLI sebagai gantinya

### <a name="security"></a>Keamanan
* Rilis Awal

### <a name="storage"></a>Penyimpanan
* [BREAKING CHANGE] Mengubah jumlah hasil default `storage [blob|file|container|share] list` menjadi 5.000. Menggunakan `--num-results *` untuk perilaku asli mengembalikan semua hasil
* Menambahkan parameter `--marker` ke `storage [blob|file|container|share] list`
* Menambahkan penanda log untuk halaman berikutnya ke STDERR untuk `storage [blob|file|container|share] list`
* Menambahkan perintah `storage blob service-properties update` dengan dukungan untuk situs web statik

### <a name="vm"></a>VM
* Mengubah `vm [disk|unmanaged-disk]` dan `vmss disk` agar memiliki parameter yang lebih konsisten
* Menambahkan dukungan untuk referensi gambar lintas penyewa ke `[vm|vmss] create`
* Memperbaiki bug dengan konfigurasi default di `vm diagnostics get-default-config --windows-os`
* Menambahkan argumen `--provision-after-extensions` ke `vmss extension set` untuk menentukan ekstensi apa yang harus tersedia sebelum ekstensi diatur
* Menambahkan argumen `--replica-count` ke `sig image-version update` untuk mengatur jumlah replikasi default
* Memperbaiki bug dengan `image create --source` saat disk os sumber diperlakukan sebagai Mesin Virtual dengan nama yang sama, meskipun ID sumber daya lengkap diberikan

## <a name="december-20-2018"></a>20 Desember 2018

Versi 2.0.54
### <a name="appservice"></a>Appservice
* Memperbaiki masalah saat `webapp up` gagal untuk disebarkan kembali
* Menambahkan dukungan untuk mencantumkan dan memulihkan snapshot webapp
* Menambahkan dukungan untuk bendera `--runtime` ke aplikasi fungsi Windows

### <a name="iotcentral"></a>IoTCentral
* Memperbaiki panggilan API perintah pembaruan

### <a name="role"></a>Peran
* [BREAKING CHANGE] Mengubah `ad [app|sp] list` menjadi hanya mencantumkan 100 objek pertama secara default

### <a name="sql"></a>SQL
* Menambahkan dukungan untuk kolase kustom pada instans terkelola

### <a name="vm"></a>VM
* Menambahkan parameter `---os-type` ke `disk create`

## <a name="december-18-2018"></a>18 Desember 2018

Versi 2.0.53
### <a name="acr"></a>Azure Container Registry
* Menambahkan dukungan untuk impor gambar dari Registri Kontainer eksternal
* Meringkas tata letak tabel untuk daftar tugas
* Menambahkan dukungan untuk URL Azure DevOps

### <a name="acs"></a>ACS
* Menambahkan Pratinjau Node Virtual
* Menghapus "(PREVIEW)" dari argumen Azure Active Directory ke `aks create`
* [DEPRECATED] Menghentikan perintah `az acs`. Layanan Access Control akan dihentikan pada 31 Januari 2020
* Menambahkan dukungan Kebijakan Jaringan saat membuat kluster Azure Kubernetes Service baru
* Menghapus persyaratan argumen `--nodepool-name` untuk `aks scale` jika hanya ada satu nodepool

### <a name="appservice"></a>Appservice
* Memperbaiki masalah saat `webapp config container` tidak mematuhi parameter `--slot`

### <a name="botservice"></a>Botservice
* Menambahkan dukungan untuk penguraian file `.bot` saat memanggil `bot show`
* Memperbaiki bug provisi Application Insights
* Memperbaiki bug spasi kosong saat menangani jalur file
* Mengurangi panggilan jaringan Kudu
* Peningkatan UX perintah umum

### <a name="consumption"></a>Consumption
* Memperbaiki bug untuk API anggaran untuk menunjukkan notifikasi

### <a name="cosmosdb"></a>CosmosDB
* Menambahkan dukungan untuk memperbarui akun dari multi-master ke single-master

### <a name="maps"></a>Maps
* Menambahkan dukungan untuk SKU S1 ke `maps account [create|update]`

### <a name="network"></a>Jaringan
* Menambahkan dukungan untuk `--format` dan `--log-version` ke `watcher flow-log configure`
* Memperbaiki masalah dengan `dns zone update` saat menggunakan "" untuk menghapus resolusi dan pendaftaran VNet tidak berfungsi

### <a name="resource"></a>Sumber daya
* Memperbaiki penanganan parameter cakupan untuk grup manajemen di `policy assignment [create|list|delete|show|update]`
* Menambahkan perintah baru `resource wait`

### <a name="storage"></a>Penyimpanan
*  Menambahkan kemampuan untuk memperbarui versi skema log untuk layanan penyimpanan di `storage logging update`

### <a name="vm"></a>VM
* Memperbaiki crash di `vm identity remove` saat mesin virtual yang ditentukan tidak memiliki identitas layanan terkelola yang ditetapkan

## <a name="december-4-2018"></a>4 Desember 2018

Versi 2.0.52
### <a name="core"></a>Core
* Menambahkan dukungan untuk provisi sumber daya lintas penyewa untuk perwakilan layanan multi-penyewa
* Memperbaiki bug saat id disalurkan dari perintah dengan output tsv tidak diurai dengan benar

### <a name="appservice"></a>Appservice
* [PREVIEW] Menambahkan perintah `webapp up` yang membantu dalam membuat & menyebarkan konten ke aplikasi
* Memperbaiki bug pada aplikasi windows berbasis kontainer karena perubahan backend

### <a name="network"></a>Jaringan
* Menambahkan argumen `--exclusion` ke `application-gateway waf-config set` untuk mendukung pengecualian WAF

### <a name="role"></a>Peran
* Menambahkan dukungan untuk pengidentifikasi kustom untuk kredensial kata sandi

### <a name="vm"></a>VM
* [DEPRECATED] Menghentikan parameter `vm extension [show|wait] --expand`
* Menambahkan parameter `--force` ke `vm restart` untuk menyebarkan ulang Mesin Virtual yang tidak responsif
* Mengubah `[vm|vmss] create --authentication-type` agar menerima "semua" untuk membuat Mesin Virtual dengan kata sandi dan autentikasi ssh
* Menambahkan parameter `image create --os-disk-caching` untuk mengatur penembolokan disk os untuk gambar

## <a name="november-20-2018"></a>########

Versi 2.0.51
### <a name="core"></a>Core
* Mengubah info masuk MSI agar tidak menggunakan kembali nama langganan dalam identitas

### <a name="acr"></a>Azure Container Registry
* Menambahkan token konteks ke langkah tugas
* Menambahkan dukungan untuk mengatur rahasia di acr run ke mirror acr task
* Meningkatkan dukungan untuk `--top` dan `--orderby` untuk perintah `show-tags` dan `show-manifests`

### <a name="appservice"></a>Appservice
* Mengubah batas waktu default penyebaran zip ke polling agar status meningkat menjadi 5 menit, juga menambahkan properti batas waktu untuk menyesuaikan nilai ini
* Memperbarui default `node_version`. Mengatur ulang tindakan pertukaran slot, selama pertukaran dua fase mempertahankan semua appsettings & string koneksi
* Menghapus pemeriksaan SKU sisi klien untuk pembuatan paket layanan aplikasi Linux
* Memperbaiki kesalahan saat mencoba mendapatkan status zipdeploy

### <a name="iotcentral"></a>IotCentral
* Menambahkan pemeriksaan ketersediaan subdomain saat membuat aplikasi IoT Central

### <a name="keyvault"></a>Az.KeyVault
* Memperbaiki bug saat kesalahan mungkin diabaikan

### <a name="network"></a>Jaringan
* Menambahkan subperintah `root-cert` ke `application-gateway` untuk menangani sertifikat akar tepercaya
* Menambahkan opsi `--min-capacity` dan `--custom-error-pages` ke `application-gateway [create|update]`:
* Menambahkan `--zones` untuk dukungan zona ketersediaan ke `application-gateway create`
* Menambahkan argumen `--file-upload-limit`, `--max-request-body-size`, dan `--request-body-check` ke `application-gateway waf-config set`

### <a name="rdbms"></a>Rdbms
* Menambahkan perintah mariadb vnet

### <a name="rbac"></a>Rbac
* Memperbaiki masalah saat mencoba memperbarui kredensial yang tidak dapat diubah di `ad app update`
* Menambahkan peringatan output untuk mengomunikasikan perubahan yang melanggar dalam waktu dekat untuk `ad [app|sp] list`

### <a name="storage"></a>Penyimpanan
* Meningkatkan penanganan kasus sudut untuk perintah salinan penyimpanan
* Memperbaiki masalah dengan `storage blob copy start-batch` yang tidak menggunakan kredensial masuk saat akun tujuan dan sumber sama
* Memperbaiki bug dengan`storage [blob|file] url` saat `sas_token` tidak dimasukkan ke dalam URL
* Menambahkan peringatan perubahan yang melanggar ke `[blob|container] list`: akan segera menampilkan hanya 5000 hasil pertama secara default

### <a name="vm"></a>VM
* Menambahkan dukungan ke `[vm|vmss] create --storage-sku` untuk menentukan SKU akun penyimpanan untuk OS terkelola dan disk data secara terpisah
* Mengubah parameter nama versi ke `sig image-version` menjadi `--image-version -e`
* Menghentikan argumen `sig image-version` `--image-version-name`, mengganti dengan `--image-version`
* Menambahkan dukungan untuk menggunakan disk OS lokal ke `[vm|vmss] create --ephemeral-os-disk`
* Menambahkan dukungan untuk `--no-wait` ke `snapshot create/update`
* Menambahkan perintah `snapshot wait`
* Menambahkan dukungan untuk menggunakan nama instans dengan `[vm|vmss] extension set --extension-instance-name`

## <a name="november-6-2018"></a>6 November 2018

Versi 2.0.50

### <a name="core"></a>Core
* Menambahkan dukungan untuk autentikasi sn+issuer perwakilan layanan

### <a name="acr"></a>Azure Container Registry
* Menambahkan dukungan untuk peristiwa git penerapan dan permintaan pull untuk pemicu sumber Tugas
* Mengubah untuk menggunakan Dockerfile default jika tidak ditentukan dalam perintah pembangunan

### <a name="acs"></a>ACS
* [BREAKING CHANGE] Menghapus `enable_cloud_console_aks_browse` untuk mengaktifkan 'az aks browse' secara default

### <a name="advisor"></a>Advisor
* Rilis ketersediaan umum

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
* Menambahkan dukungan ke `ams transform output remove` sekarang dapat dilakukan dengan meneruskan indeks output untuk dihapus
* Menambahkan argumen `--correlation-data` dan `--label` ke grup perintah `ams job`
* Menambahkan argumen `--storage-account` dan `--container` ke grup perintah `ams asset`
* Menambahkan nilai default untuk waktu kedaluwarsa (Sekarang+23 jam) dan izin (Baca) dalam perintah `ams asset get-sas-url`
* [BREAKING CHANGE] Mengganti perintah `ams streaming locator` dengan `ams streaming-locator`
* [BREAKING CHANGE] Memperbarui argumen `--content-keys` dari `ams streaming locator`
* [BREAKING CHANGE] Mengganti nama `--content-policy-name` menjadi `--content-key-policy-name` dalam perintah `ams streaming locator`
* [BREAKING CHANGE] Mengganti perintah `ams streaming policy` dengan `ams streaming-policy`
* [BREAKING CHANGE] Mengganti argumen `--preset-names` dengan `--preset` di grup perintah `ams transform`. Sekarang Anda hanya dapat mengatur 1 output/preset pada satu waktu (untuk menambahkan lebih banyak, Anda harus menjalankan `ams transform output add`). Selain itu, Anda dapat mengatur StandardEncoderPreset kustom dengan meneruskan jalur ke JSON kustom Anda
* [BREAKING CHANGE] Mengganti nama `--output-asset-names ` menjadi `--output-assets` dalam perintah `ams job start`. Sekarang menerima daftar aset yang dipisahkan spasi dalam format 'assetName=label'. Aset tanpa label dapat dikirim seperti ini: 'assetName='

### <a name="appservice"></a>AppService
* Memperbaiki bug di `az webapp config backup update` yang mencegah pengaturan jadwal pencadangan jika belum ada yang diatur

### <a name="configure"></a>Konfigurasikan
* Menambahkan YAML ke opsi format output

### <a name="container"></a>Kontainer
* Mengubah untuk menunjukkan identitas saat mengekspor grup kontainer ke yaml

### <a name="eventhub"></a>EventHub
* Menambahkan bendera `--enable-kafka` untuk mendukung Kafka di `eventhub namespace [create|update]`

### <a name="interactive"></a>Interaktif
* Interactive sekarang menginstal ekstensi `interactive`, yang memungkinkan pembaruan dan dukungan lebih cepat

### <a name="monitor"></a>Monitor
* Menambahkan dukungan untuk nama metrik yang menyertakan karakter garis miring (/) dan titik (.) ke `--condition` di `monitor metrics alert [create|update]`

### <a name="network"></a>Jaringan
* Menghentikan nama perintah `network interface-endpoint` yang mendukung `network private-endpoint`
* Memperbaiki masalah saat argumen `--peer-circuit` di `express-route peering connection create`tidak menerima ID
* Memperbaiki masalah saat `--ip-tags` tidak berfungsi dengan benar dengan `public-ip create`

### <a name="profile"></a>Profil
* Menambahkan `--use-cert-sn-issuer` ke `az login` untuk masuk perwakilan layanan dengan pengguliran otomatis sertifikat

### <a name="rdbms"></a>RDBMS
* Menambahkan perintah replika mysql

### <a name="resource"></a>Sumber daya
* Menambahkan dukungan untuk grup manajemen dan langganan ke perintah `policy definition|set-definition`

### <a name="role"></a>Peran
* Menambahkan dukungan untuk manajemen izin API, pengguna yang masuk, dan kata sandi aplikasi & manajemen kredensial sertifikat
* Mengubah `ad sp create-for-rbac` untuk memperjelas kebingungan antara displayName dan nama prinsipal layanan
* Menambahkan dukungan untuk memberikan izin ke aplikasi Azure Active Directory

### <a name="storage"></a>Penyimpanan
* Menambahkan dukungan untuk terhubung ke layanan penyimpanan hanya dengan SAS dan titik akhir (tanpa nama akun atau kunci) seperti yang dijelaskan dalam [Mengonfigurasi string koneksi Azure Storage](/azure/storage/common/storage-configure-connection-string).

### <a name="vm"></a>VM
* Menambahkan argumen `storage-sku` ke `image create` untuk mengatur jenis akun penyimpanan default gambar
* Memperbaiki bug dengan `vm resize` saat opsi `--no-wait` menyebabkan perintah menjadi crash
* Mengubah format output tabel `vm encryption show` untuk menunjukkan status
* Mengubah `vm secret format` untuk meminta output json/jsonc. Memperingatkan pengguna dan default ke output json jika format output yang tidak diinginkan dipilih
* Meningkatkan validasi argumen untuk `vm create --image`

## <a name="october-23-2018"></a>23 Oktober 2018

Versi 2.0.49

### <a name="core"></a>Core
* Memperbaiki masalah dengan `--ids` saat `--subscription` akan diprioritaskan daripada langganan di `--ids`
* Menambahkan peringatan eksplisit saat parameter akan diabaikan dengan menggunakan `--ids`

### <a name="acr"></a>Azure Container Registry
* Memperbaiki masalah pengodean Build Azure Container Registry di Python2

### <a name="cdn"></a>CDN
* [BREAKING CHANGE] Mengubah perilaku penembolokan string kueri default `cdn endpoint create` menjadi tidak lagi default ke "IgnoreQueryString". Sekarang diatur oleh layanan

### <a name="container"></a>Kontainer
* Menambahkan `Private` sebagai jenis yang valid untuk diteruskan ke '--ip-address'
* Mengubah untuk mengizinkan hanya menggunakan ID subnet untuk menyiapkan jaringan virtual untuk grup kontainer
* Mengubah untuk mengizinkan penggunaan nama vnet atau id sumber daya untuk mengaktifkan penggunaan vnet dari grup sumber daya yang berbeda
* Menambahkan `--assign-identity` untuk menambahkan identitas MSI ke grup kontainer
* Menambahkan `--scope` untuk membuat penetapan peran untuk identitas MSI yang ditetapkan sistem
* Menambahkan peringatan saat membuat grup kontainer dengan gambar tanpa proses yang berjalan lama
* Memperbaiki masalah output tabel untuk perintah `list` dan `show`

### <a name="cosmosdb"></a>CosmosDB
* Menambahkan dukungan `--enable-multiple-write-locations` ke `cosmosdb create`

### <a name="interactive"></a>Interaktif
* Mengubah untuk memastikan parameter langganan global muncul di parameter

### <a name="iot-central"></a>IoT Pusat
* Menambahkan opsi templat dan nama tampilan untuk pembuatan Aplikasi IoT Central
* [BREAKING CHANGE] Menghapus dukungan untuk SKU F1; Menggunakan SKU S1 sebagai gantinya

### <a name="monitor"></a>Monitor
* Perubahan pada `monitor activity-log list`:
  * Menambahkan dukungan untuk mencantumkan semua peristiwa di tingkat langganan
  * Menambahkan parameter `--offset` untuk membuat kueri waktu dengan lebih mudah
  * Meningkatkan validasi untuk `--start-time` dan `--end-time` guna menggunakan rentang format ISO8601 yang lebih luas dan format tanggalwaktu yang lebih ramah pengguna
  * Menambahkan `--namespace` sebagai alias untuk opsi yang tidak digunakan lagi `--resource-provider`
  * Menghentikan `--filters` karena tidak ada nilai selain nilai dengan opsi strongly-typed yang didukung oleh layanan
* Perubahan pada `monitor metrics list`:
  * Menambahkan parameter `--offset` untuk membuat kueri waktu dengan lebih mudah
  * Meningkatkan validasi untuk `--start-time` dan `--end-time` guna menggunakan rentang format ISO8601 yang lebih luas dan format tanggalwaktu yang lebih ramah pengguna
* Meningkatkan validasi untuk argumen `--event-hub` dan `--event-hub-rule` menjadi `monitor diagnostic-settings create`

### <a name="network"></a>Jaringan
* Menambahkan argumen `--app-gateway-address-pools` dan `--gateway-name` ke `nic create`, untuk mendukung menambahkan kumpulan alamat backend gateway aplikasi ke NIC
* Menambahkan argumen `--app-gateway-address-pools` dan `--gateway-name` ke `nic ip-config create/update`, untuk mendukung menambahkan kumpulan alamat backend gateway aplikasi ke NIC

### <a name="servicebus"></a>ServiceBus
* Menambahkan Baca-Saja `migration_state` ke MigrationConfigProperties untuk menunjukkan Standar Azure Service Bus saat ini ke status migrasi namespace Premium

### <a name="sql"></a>SQL
* Memperbaiki `sql failover-group create` dan `sql failover-group update` agar berfungsi dengan kebijakan Failover manual

### <a name="storage"></a>Penyimpanan
* Memperbaiki pemformatan output `az storage cors list`, semua item menunjukkan kunci "Layanan" yang benar
* Menambahkan parameter `--bypass-immutability-policy` untuk penghapusan kontainer yang diblokir kebijakan ketetapan

### <a name="vm"></a>VM
* Menerapkan mode penembolokan disk menjadi `None` untuk seri mesin Lv/Lv2 di `[vm|vmss] create`
* Memperbarui daftar ukuran yang didukung yang mendukung akselerator jaringan untuk `vm create`
* Menambahkan argumen yang diketik kuat untuk konfigurasi ultrassd iops dan mbps untuk `disk create`

## <a name="october-16-2018"></a>16 Oktober 2018

Versi 2.0.48

### <a name="vm"></a>VM
* Memperbaiki masalah SDK yang menyebabkan penginstalan Homebrew gagal

## <a name="october-9-2018"></a>9 Oktober 2018

Versi 2.0.47

### <a name="core"></a>Core
* Meningkatkan penanganan kesalahan untuk kesalahan "Permintaan Buruk"

### <a name="acr"></a>Azure Container Registry
* Menambahkan dukungan untuk format tabel yang mirip sebagai klien helm

### <a name="acs"></a>ACS
* Menambahkan `aks [create|scale] --nodepool-name` untuk mengonfigurasi nama nodepool, dipotong menjadi 12 karakter, default - nodepool1
* Memperbaiki untuk beralih ke 'scp' saat Parimiko gagal
* Mengubah `aks create` menjadi tidak lagi memerlukan `--aad-tenant-id`
* Meningkatkan penggabungan kredensial Kubernetes saat ada entri duplikat

### <a name="container"></a>Kontainer
* Mengubah `functionapp create` untuk mendukung pembuatan jenis paket penggunaan Linux dengan runtime tertentu
* [PREVIEW] Menambahkan dukungan untuk menghosting webapps di kontainer Windows

### <a name="event-hub"></a>Pusat Aktivitas
* Memperbaiki perintah `eventhub update`
* [BREAKING CHANGE] Mengubah perintah `list` untuk menangani kesalahan sumber daya Tidak Ditemukan(404) dengan cara yang umum daripada menunjukkan daftar kosong

### <a name="extensions"></a>Ekstensi
* Memperbaiki masalah saat mencoba menambahkan ekstensi yang sudah diinstal

### <a name="hdinsight"></a>HDInsight
* Rilis awal

### <a name="iot"></a>IoT
* Menambahkan perintah penginstalan ekstensi ke banner yang dijalankan pertama

### <a name="keyvault"></a>Az.KeyVault
* Mengubah untuk membatasi perintah penyimpanan keyvault ke profil API terbaru

### <a name="network"></a>Jaringan
* Memperbaiki `network dns zone create`: Perintah berhasil meskipun pengguna telah mengonfigurasi lokasi default. Melihat #6052
* Menghentikan `--remote-vnet-id` untuk `network vnet peering create`
* Menambahkan `--remote-vnet` ke `network vnet peering create` yang menerima nama atau ID
* Menambahkan dukungan untuk beberapa prefiks subnet ke `network vnet create` dengan `--subnet-prefixes`
* Menambahkan dukungan untuk beberapa prefiks subnet ke `network vnet subnet [create|update]` dengan `--address-prefixes`
* Memperbaiki masalah dengan `network application-gateway create` yang mencegah pembuatan gateway dengan `WAF_v2` atau SKU `Standard_v2`
* Menambahkan argumen kemudahan `--service-endpoint-policy` ke `network vnet subnet update`

### <a name="role"></a>Peran
* Menambahkan dukungan untuk mencantumkan pemilik aplikasi Azure Active Directory ke `ad app owner`
* Menambahkan dukungan untuk mencantumkan pemilik perwakilan layanan Azure Active Directory ke `ad sp owner`
* Mengubah untuk memastikan perintah pembuatan & pembaruan definisi peran menerima beberapa konfigurasi izin
* Mengubah `ad sp create-for-rbac` untuk memastikan URI beranda selalu "https"

### <a name="service-bus"></a>Service Bus
* [BREAKING CHANGE] Mengubah perintah `list` untuk menangani kesalahan sumber daya Tidak Ditemukan(404) dengan cara yang umum daripada menunjukkan daftar kosong

### <a name="vm"></a>VM
* Memperbaiki bidang `accessSas` kosong di `disk grant-access`
* Mengubah `vmss create` untuk mencadangkan rentang port frontend yang cukup besar untuk menangani provisi berlebih
* Memperbaiki perintah pembaruan untuk `sig`
* Menambahkan dukungan `--no-wait` untuk mengelola versi gambar di `sig`
* Mengubah `vm list-ip-addresses` untuk menampilkan zona ketersediaan alamat IP publik
* Mengubah `[vm|vmss] disk attach` untuk mengatur lun default disk ke tempat pertama yang tersedia

## <a name="september-21-2018"></a>########

Versi 2.0.46

### <a name="acr"></a>Azure Container Registry
* Menambahkan perintah Tugas Azure Container Registry
* Menambahkan perintah eksekusi cepat
* Menghentikan grup perintah `build-task`
* Menambahkan grup perintah `helm` untuk mendukung mengelola bagan helm dengan Azure Container Registry
* Menambahkan dukungan untuk pembuatan idempoten untuk registri terkelola
* Menambahkan bendera tanpa format untuk menampilkan log build

### <a name="acs"></a>ACS
* Mengubah perintah `install-connector` untuk mengatur Nama Domain yang Sepenuhnya Memenuhi Syarat Master Azure Kubernetes Service
* Memperbaiki dalam membuat penetapan peran untuk vnet-subnet-id saat tidak menentukan perwakilan layanan dan melewati penetapan peran

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk manajemen operasi webjobs (berkelanjutan dan dipicu)
* az webapp config set mendukung --fts-state propertyAlso yang menambahkan dukungan fot az functionapp config set & show
* Menambahkan dukungan untuk menggunakan penyimpanan Anda sendiri untuk webapps
* Menambahkan dukungan untuk mencantumkan dan memulihkan webapps yang dihapus

### <a name="batch"></a>Batch
* Mengubah tugas penambahan melalui `--json-file` untuk mendukung sintaks AddTaskCollectionParameter
* Memperbarui dokumentasi dari format `--json-file` yang diterima
* Menambahkan `--max-tasks-per-node-option` ke `batch pool create`
* Mengubah perilaku `batch account` untuk menunjukkan akun yang saat ini masuk jika tidak ada opsi yang ditentukan

### <a name="batch-ai"></a>Batch AI
* Memperbaiki kegagalan pembuatan akun penyimpanan otomatis di perintah `batchai cluster create`

### <a name="cognitive-services"></a>Cognitive Services
* Menambahkan pelengkap untuk argumen `--sku`, `--kind`, `--location`
* Menambahkan perintah `cognitiveservices account list-usage`
* Menambahkan perintah `cognitiveservices account list-kinds`
* Menambahkan perintah `cognitiveservices account list`
* Menghentikan `cognitiveservices list`
* Mengubah `--name` agar menjadi opsional untuk `cognitiveservices account list-skus`

### <a name="container"></a>Kontainer
* Menambahkan kemampuan untuk menghidupkan ulang dan menghentikan grup kontainer yang sedang berjalan
* Menambahkan `--network-profile` untuk meneruskan profil jaringan
* Menambahkan `--subnet`, `--vnet_name`, untuk memungkinkan membuat grup kontainer di VNET
* Mengubah output tabel untuk menunjukkan status grup kontainer

### <a name="datalake"></a>Datalake
* Menambahkan perintah untuk aturan jaringan virtual

### <a name="interactive-shell"></a>Shell Interaktif
* Memperbaiki kesalahan pada Windows saat perintah gagal berjalan dengan benar
* Memperbaiki masalah pemuatan perintah dalam interaktif yang disebabkan oleh objek yang tidak digunakan lagi

### <a name="iot"></a>IoT
* Menambahkan dukungan untuk merutekan IoT Hubs

### <a name="key-vault"></a>Key Vault
* Memperbaiki impor kunci Key Vault untuk kunci RSA

### <a name="network"></a>Jaringan
* Menambahkan perintah `network public-ip prefix` untuk mendukung fitur prefiks IP publik
* Menambahkan perintah `network service-endpoint` untuk mendukung fitur kebijakan titik akhir layanan
* Menambahkan perintah `network lb outbound-rule` untuk mendukung pembuatan aturan keluar Load Balancer Standar
* Menambahkan `--public-ip-prefix` ke `network lb frontend-ip create/update` untuk mendukung konfigurasi IP frontend menggunakan prefiks IP publik
* Menambahkan `--enable-tcp-reset` ke `network lb rule/inbound-nat-rule/inbound-nat-pool create/update`
* Menambahkan `--disable-outbound-snat` ke `network lb rule create/update`
* Mengizinkan `network watcher flow-log show/configure` untuk digunakan dengan NSG klasik
* Menambahkan perintah `network watcher run-configuration-diagnostic`
* Memperbaiki perintah `network watcher test-connectivity` dan menambahkan properti `--method`, `--valid-status-codes` dan `--headers`
* `network express-route create/update`: Menambahkan bendera `--allow-global-reach`
* `network vnet subnet create/update`: Menambahkan dukungan untuk `--delegation`
* Menambahkan perintah `network vnet subnet list-available-delegations`
* `network traffic-manager profile create/update`: Menambahkan dukungan untuk `--interval`, `--timeout` dan `--max-failures` untuk konfigurasi Pemantauan opsi yang Tidak Digunakan Lagi `--monitor-path`, `--monitor-port` dan `--monitor-protocol` yang mendukung `--path`, `--port`, `--protocol`
* `network lb frontend-ip create/update`: Memperbaiki logika untuk mengatur metode alokasi IP privat Jika alamat IP privat diberikan, alokasi akan bersifat statik Jika tidak ada alamat IP privat yang diberikan, atau string kosong diberikan untuk alamat IP privat, alokasi bersifat dinamis.
* `dns record-set * create/update`: Menambahkan dukungan untuk `--target-resource`
* Menambahkan perintah `network interface-endpoint` ke objek titik akhir antarmuka kueri
* Menambahkan `network profile show/list/delete` untuk manajemen sebagian profil jaringan
* Menambahkan perintah `network express-route peering connection` untuk mengelola koneksi peering antara ExpressRoutes

### <a name="rdbms"></a>RDBMS
* Menambahkan dukungan untuk layanan MariaDB

### <a name="reservation"></a>Reservasi
* Menambahkan CosmosDb dalam jenis enum sumber daya yang dipesan
* Menambahkan properti nama dalam model Patch

### <a name="manage-app"></a>Mengelola Aplikasi
* Memperbaiki bug di `managedapp create --kind MarketPlace` yang menyebabkan pembuatan instans aplikasi terkelola Marketplace menjadi crash
* Mengubah perintah `feature` agar dibatasi ke profil yang didukung

### <a name="role"></a>Peran
* Menambahkan dukungan untuk mencantumkan keanggotaan grup pengguna

### <a name="signalr"></a>SignalR
* Rilisan pertama

### <a name="storage"></a>Penyimpanan
* Menambahkan parameter `--auth-mode login` untuk penggunaan kredensial masuk pengguna untuk otorisasi blob dan antrean
* Menambahkan `storage container immutability-policy/legal-hold` untuk mengelola penyimpanan yang tidak dapat diubah

### <a name="vm"></a>VM
* Memperbaiki masalah saat `vm create --generate-ssh-keys` menimpa file kunci privat jika file kunci umum tidak ada (#4725, #6780)
* Menambahkan dukungan untuk galeri gambar bersama melalui `az sig`

## <a name="august-28-2018"></a>28 Agustus 2018

Versi 2.0.45

### <a name="core"></a>Core

* Memperbaiki masalah memuat file konfigurasi kosong
* Menambahkan dukungan untuk profil `2018-03-01-hybrid` untuk Azure Stack

### <a name="acr"></a>Azure Container Registry

* Menambahkan solusi untuk operasi runtime tanpa permintaan Azure Resource Manager
* Mengubah untuk mengecualikan file kontrol versi (mis., .git, .gitignore) dari tar yang diunggah secara default di perintah `build`

### <a name="acs"></a>ACS

* Mengubah `aks create` ke default menjadi `Standard_DS2_v2` Mesin Virtual
* Mengubah `aks get-credentials` agar sekarang memanggil api baru untuk mendapatkan kredensial kluster

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk CORS di functionapp & webapp
* Menambahkan dukungan tag Azure Resource Manager pada perintah pembuatan
* Mengubah `[webapp|functionapp] identity show` agar keluar dengan kode 3 pada sumber daya yang hilang

### <a name="backup"></a>Cadangan

* Mengubah `backup vault backup-properties show` agar keluar dengan kode 3 pada sumber daya yang hilang

### <a name="bot-service"></a>Layanan Bot

* Rilis CLI Bot Service Awal

### <a name="cognitive-services"></a>Cognitive Services

* Menambahkan parameter baru `--api-properties,` yang diperlukan untuk membuat beberapa layanan

### <a name="iot"></a>IoT

* Memperbaiki masalah dengan menghubungkan hub yang ditautkan

### <a name="monitor"></a>Monitor

* Menambahkan perintah `monitor metrics alert` untuk peringatan metrik yang mendekati real time
* Menghentikan perintah `monitor alert`

### <a name="network"></a>Jaringan

* Mengubah `network application-gateway ssl-policy predefined show` agar keluar dengan kode 3 pada sumber daya yang hilang

### <a name="resource"></a>Sumber daya

* Mengubah `provider operation show` agar keluar dengan kode 3 pada sumber daya yang hilang

### <a name="storage"></a>Penyimpanan

* Mengubah `storage share policy show` agar keluar dengan kode 3 pada sumber daya yang hilang

### <a name="vm"></a>VM

* Mengubah `vm/vmss identity show` agar keluar dengan kode 3 pada sumber daya yang hilang
* Menghentikan `--storage-caching` untuk `vm create`

## <a name="auguest-14-2018"></a>14 Agustus 2018

Versi 2.0.44

### <a name="core"></a>Core

* Memperbaiki tampilan numerik dalam output `table`
* Menambahkan format output YAML

### <a name="telemetry"></a>Telemetri

* Meningkatkan pelaporan telemetri

### <a name="acr"></a>Azure Container Registry

* Menambahkan perintah `content-trust policy`
* Memperbaiki masalah saat `.dockerignore` tidak ditangani dengan benar

### <a name="acs"></a>ACS

* Mengubah `az acs/aks install-cli` untuk diinstal di bawah `%USERPROFILE%\.azure-kubectl` di Windows
* Mengubah `az aks install-connector` untuk mendeteksi apakah kluster memiliki kontrol akses berbasis peran dan mengonfigurasi Konektor ACI dengan tepat
* Mengubah agar menjadi penetapan peran ke subnet saat disediakan
* Menambahkan opsi baru untuk "lewati penetapan peran" untuk subnet saat disediakan
* Mengubah untuk melewati penetapan peran ke subnet saat penetapan sudah ada

### <a name="appservice"></a>AppService

* Memperbaiki bug yang mencegah dari membuat aplikasi fungsi menggunakan akun penyimpanan di grup sumber daya eksternal
* Memperbaiki crash pada penyebaran zip

### <a name="batchai"></a>BatchAI

* Mengubah output pencatat untuk pembuatan akun penyimpanan otomatis untuk menentukan "grup *sumber daya*".

### <a name="container"></a>Kontainer

* Menambahkan `--secure-environment-variables` untuk meneruskan variabel lingkungan aman ke kontainer

### <a name="iot"></a>IoT

* [BREAKING CHANGE] Menghapus perintah yang tidak digunakan lagi yang telah dipindahkan ke ekstensi iot
* Memperbarui elemen untuk tidak menganggap domain `azure-devices.net`

### <a name="iot-central"></a>Iot Central

* Rilis awal modul IoT Central

### <a name="keyvault"></a>Az.KeyVault


* Menambahkan perintah untuk mengelola akun penyimpanan dan definisi sas
* Menambahkan perintah untuk aturan jaringan
* Menambahkan parameter `--id` ke operasi rahasia, kunci, dan sertifikat
* Menambahkan dukungan untuk versi KV mgmt multi-api
* Menambahkan dukungan untuk versi KV data plane multi-api

### <a name="relay"></a>Relay

* Rilis awal

### <a name="sql"></a>Sql

* Menambahkan perintah `sql failover-group`

### <a name="storage"></a>Penyimpanan

* [BREAKING CHANGE] Mengubah `storage account show-usage` untuk mewajibkan parameter `--location` dan akan mencantumkan berdasarkan wilayah
* Mengubah parameter `--resource-group` menjadi opsional untuk perintah `storage account`
* Menghapus peringatan 'Prasyarat gagal' untuk masing-masing kegagalan dalam perintah batch untuk pesan agregat tunggal
* Mengubah perintah `[blob|file] delete-batch` menjadi tidak lagi menampilkan larik null
* Mengubah perintah `blob [download|upload|delete-batch]` untuk membaca token sas dari url kontainer

### <a name="vm"></a>VM

* Menambahkan filter umum ke `vm list-skus` untuk kemudahan penggunaan

## <a name="july-31-2018"></a>31 Juli 2018

Versi 2.0.43

### <a name="acr"></a>Azure Container Registry

* Menambahkan bendera `--with-secure-properties` ke perintah `acr build-task show`
* Menambahkan perintah `acr build-task update-build`

### <a name="acs"></a>ACS

* Mengubah untuk mengembalikan pengembalian 0 (berhasil) saat mengakhiri `az aks browse` dengan menekan [Ctrl+C]

### <a name="batch"></a>Batch

* Memperbaiki bug saat menampilkan token Azure Active Directory di cloudshell

### <a name="container"></a>Kontainer

* Menghapus persyaratan `--log-analytics-workspace-key` untuk nama atau ID saat dalam langganan yang ditetapkan

### <a name="network"></a>Jaringan

* Menambahkan dukungan dns ke profil 2017-03-09 untuk Azure Stack

### <a name="resource"></a>Sumber daya

* Menambahkan `--rollback-on-error` ke `group deployment create` untuk menjalankan penyebaran yang baik pada kesalahan
* Memperbaiki masalah saat `--parameters {}` dengan `group deployment create` menghasilkan kesalahan

### <a name="role"></a>Peran

* Menambahkan dukungan untuk profil tumpukan profil 2017-03-09
* Memperbaiki masalah saat parameter pembaruan umum ke `app update` tidak berfungsi dengan benar

### <a name="search"></a>Cari

* Menambahkan perintah untuk layanan Pencarian Azure

### <a name="service-bus"></a>Service Bus

* Menambahkan grup perintah migrasi untuk memigrasikan namespace dari Service Bus Standard ke Premium
* Menambahkan properti opsional baru ke antrean dan Langganan Service Bus
  *  `--enable-batched-operations` dan `--enable-dead-lettering-on-message-expiration` di `queue`
  *  `--dead-letter-on-filter-exceptions` di `subscriptions`

### <a name="storage"></a>Penyimpanan

* Menambahkan dukungan untuk mengunduh file besar menggunakan satu koneksi
* Mengonversi perintah `show` yang terlewatkan karena gagal dengan kode keluar 3 pada sumber daya yang hilang

### <a name="vm"></a>VM

* Menambahkan dukungan ke daftar kumpulan ketersediaan berdasarkan langganan
* Menambahkan dukungan untuk `StandardSSD_LRS`
* Menambahkan dukungan untuk kelompok keamanan aplikasi dalam membuat set skala Mesin Virtual
* [BREAKING CHANGE] Mengubah `[vm|vmss] create`, `[vm|vmss] identity assign`, dan `[vm|vmss] identity remove` untuk menampilkan identitas yang ditetapkan pengguna dalam format kamus

## <a name="july-18-2018"></a>18 Juli 2018

Versi 2.0.42

### <a name="core"></a>Core

* Menambahkan dukungan untuk masuk berbasis browser di jendela bash WSL
* Menambahkan bendera `--force-string` ke semua perintah pembaruan umum
* [BREAKING CHANGE] Mengubah perintah 'tampilkan' untuk mencatat pesan kesalahan dan gagal dengan kode keluar 3 pada sumber daya yang hilang

### <a name="acr"></a>Azure Container Registry

* [BREAKING CHANGE] Memperbarui '--no-Push' ke bendera murni dalam perintah 'acr build'
* Menambahkan perintah `show` dan `update` di bawah grup `acr repository`
* Menambahkan bendera `--detail` untuk `show-manifests` dan `show-tags` untuk menampilkan informasi yang lebih detail
* Menambahkan parameter `--image` untuk mendukung mendapatkan detail atau log build dengan gambar

### <a name="acs"></a>ACS

* Mengubah `az aks create` menjadi kesalahan jika `--max-pods` kurang dari 5

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk sku PremiumV2

### <a name="batch"></a>Batch

* Memperbaiki bug saat menggunakan kredensial token pada mode cloud shell
* Mengubah input JSON menjadi tidak peka huruf besar/kecil

### <a name="batch-ai"></a>Batch AI

* Memperbaiki perintah `az batchai job exec`

### <a name="container"></a>Kontainer

* Menghapus persyaratan untuk nama pengguna dan kata sandi untuk registri yang bukan dockerhub
* Memperbaiki kesalahan saat membuat grup kontainer dari file yaml

### <a name="network"></a>Jaringan

* Menambahkan dukungan `--no-wait` ke `network nic [create|update|delete]`
* Menambahkan `network nic wait`
* Menghentikan argumen `--ids` untuk `network vnet [subnet|peering] list`
* Menambahkan bendera `--include-default` untuk menyertakan aturan keamanan default dalam output `network nsg rule list`

### <a name="resource"></a>Sumber daya

* Menambahkan dukungan `--no-wait` ke `group deployment delete`
* Menambahkan dukungan `--no-wait` ke `deployment delete`
* Menambahkan perintah `deployment wait`
* Memperbaiki masalah saat perintah `az deployment` tingkat langganan muncul secara tidak benar untuk profil 2017-03-09

### <a name="sql"></a>SQL

* Memperbaiki kesalahan 'Nama grup sumber daya yang disediakan ... tidak cocok dengan nama di Url' saat menentukan nama kumpulan elastis untuk perintah `sql db copy` dan `sql db replica create`
* Mengizinkan mengonfigurasi server sql default dengan menjalankan `az configure --defaults sql-server=<name>`
* Menerapkan pemformat tabel untuk perintah `sql server`, `sql server firewall-rule`, `sql list-usages`, dan `sql show-usage`

### <a name="storage"></a>Penyimpanan

* Menambahkan properti `pageRanges` ke output `storage blob show` yang akan diisi untuk blob halaman

### <a name="vm"></a>VM

* [BREAKING CHANGE] Mengubah `vmss create` untuk menggunakan `Standard_DS1_v2` sebagai ukuran instans default
* Menambahkan dukungan `--no-wait` ke `vm extension [set|delete]` dan `vmss extension [set|delete]`
* Menambahkan `vm extension wait`

## <a name="july-3-2018"></a>3 Juli 2018

### <a name="version-2041"></a>Versi 2.0.41

### <a name="aks"></a>AKS

* Mengubah pemantauan untuk menggunakan ID langganan

### <a name="version-2040"></a>Versi 2.0.40

### <a name="core"></a>Core

* Menambahkan alur kode otorisasi baru untuk masuk interaktif

### <a name="acr"></a>Azure Container Registry

* Menambahkan status pembangunan polling
* Menambahkan dukungan untuk nilai enum yang tidak peka huru besar/kecil
* Menambahkan parameter `--top` dan `--orderby` untuk `show-manifests`

### <a name="acs"></a>ACS

* [BREAKING CHANGE] Mengaktifkan kontrol akses berbasis peran Kubernetes secara default
* Menambahkan argumen `--disable-rbac` dan menghentikan `--enable-rbac` karena ini merupakan default sekarang
* Memperbarui opsi untuk perintah `aks browse`. Menambahkan dukungan `--listen-port`
* Memperbarui paket bagan helm default untuk perintah `aks install-connector`. Menggunakan virtual-kubelet-for-aks-latest.tgz
* Menambahkan perintah `aks enable-addons` dan `aks disable-addons` untuk memperbarui kluster yang ada

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk menonaktifkan identitas melalui `webapp identity remove`
* Menghapus tag `preview` untuk fitur Identitas

### <a name="backup"></a>Cadangan

* Memperbarui definisi modul

### <a name="batchai"></a>BatchAI

* Memperbaiki output tabel untuk perintah `batchai cluster node list` dan `batchai job node list`

### <a name="cloud"></a>Cloud

* Menambahkan sufiks server `acr login` ke konfigurasi cloud

### <a name="container"></a>Kontainer

* Mengubah `container create` menjadi default untuk operasi yang berjalan lama
* Menambahkan parameter Analitik Log `--log-analytics-workspace` dan `--log-analytics-workspace-key`
* Menambahkan parameter `--protocol` untuk menentukan protokol jaringan mana yang akan digunakan

### <a name="extension"></a>Extensi

* Mengubah `extension list-available` menjadi hanya menampilkan ekstensi yang kompatibel dengan versi CLI

### <a name="network"></a>Jaringan

* Memperbaiki masalah saat jenis catatan peka huruf besar/kecil ([#6602](https://github.com/Azure/azure-cli/issues/6602))

### <a name="rdbms"></a>Rdbms

* Menambahkan perintah `[postgres|myql] server vnet-rule`

### <a name="resource"></a>Sumber daya

* Menambahkan grup operasi baru `deployment`

### <a name="vm"></a>VM

* Menambahkan dukungan untuk menghapus identitas yang ditetapkan sistem

## <a name="june-25-2018"></a>25 Juni 2018

Versi 2.0.39

### <a name="cli"></a>CLI

* Memperbarui pemangkasan file di alat penginstal MSI untuk memperbaiki masalah penginstalan ekstensi

## <a name="june-19-2018"></a>19 Juni 2018

Versi 2.0.38

### <a name="core"></a>Core

* Menambahkan dukungan global untuk `--subscription` ke sebagian besar perintah

### <a name="acr"></a>Azure Container Registry

* Menambahkan `azure-storage-blob` sebagai dependensi
* Mengubah konfigurasi CPU default dengan `acr build-task create` untuk menggunakan 2 core

### <a name="acs"></a>ACS

* Memperbarui opsi perintah `aks use-dev-spaces`. Menambahkan dukungan `--update`
* Mengubah `aks get-credentials --admin` agar tidak menghapus konteks pengguna di `$HOME/.kube/config`
* Menampilkan properti `nodeResourceGroup` baca-saja di kluster terkelola
* Memperbaiki kesalahan perintah `acs browse`
* Membuat `--connector-name` menjadi opsional untuk `aks install-connector`, `aks upgrade-connector` dan `aks remove-connector`
* Menambahkan wilayah Instans Kontainer Azure baru untuk `aks install-connector`
* Menambahkan lokasi yang dinormalisasi ke dalam nama rilis helm dan nama node ke `aks install-connector`

### <a name="appservice"></a>AppService

* Menambahkan dukungan untuk versi urllib yang lebih baru
* Menambahkan dukungan ke `functionapp create` untuk menggunakan paket appservice dari grup sumber daya eksternal

### <a name="batch"></a>Batch

* Menghapus dependensi `azure-batch-extensions`

### <a name="batch-ai"></a>Batch AI

* Menambahkan dukungan untuk ruang kerja. Ruang kerja memungkinkan untuk mengelompokkan kluster, server file, dan eksperimen dalam grup yang menghilangkan batasan jumlah sumber daya yang dapat dibuat
* Menambahkan dukungan untuk eksperimen. Eksperimen memungkinkan untuk mengelompokkan pekerjaan dalam kumpulan menghilangkan batasan pada jumlah pekerjaan yang dibuat
* Menambahkan dukungan untuk mengonfigurasi `/dev/shm` untuk pekerjaan yang berjalan di kontainer docker
* Menambahkan perintah `batchai cluster node exec` dan `batchai job node exec`. Perintah ini memungkinkan untuk menjalankan perintah apa pun secara langsung pada node dan menyediakan fungsionalitas untuk penerusan port.
* Menambahkan dukungan untuk perintah `--ids` ke `batchai`
* [BREAKING CHANGE] Semua kluster dan fileservers harus dibuat di bawah ruang kerja
* [BREAKING CHANGE] Pekerjaan harus dibuat berdasarkan eksperimen
* [BREAKING CHANGE] Menghapus `--nfs-resource-group` dari perintah `cluster create` dan `job create`. Untuk memasang NFS milik grup ruang kerja/sumber daya yang berbeda, berikan ID Azure Resource Manager server file melalui opsi `--nfs`
* [BREAKING CHANGE] Menghapus `--cluster-resource-group` dari perintah `job create`. Untuk mengirimkan pekerjaan di kluster milik ruang kerja/grup sumber daya yang berbeda, berikan ID Azure Resource Manager kluster melalui opsi `--cluster`
* [BREAKING CHANGE] Menghapus atribut `location` dari pekerjaan, kluster, dan server file. Lokasi sekarang adalah atribut dari ruang kerja.
* [BREAKING CHANGE] Menghapus perintah `--location` dari `job create`, `cluster create` dan `file-server create`
* [BREAKING CHANGE] Mengubah nama opsi singkat untuk membuat antarmuka lebih konsisten:
  - Mengganti nama [`--config`, `-c`] menjadi [`--config-file`, `-f`]
  - Mengganti nama [`--cluster`, `-r`] menjadi [`--cluster`, `-c`]
  - Mengganti nama [`--cluster`, `-n`] menjadi [`--cluster`, `-c`]
  - Mengganti nama [`--job`, `-n`] menjadi [`--job`, `-j`]

### <a name="maps"></a>Maps

* [BREAKING CHANGE] Mengubah `maps account create` untuk mengharuskan menerima Ketentuan Layanan baik dengan perintah interaktif atau bendera `--accept-tos`

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk `https` ke `network lb probe create` [#6571](https://github.com/Azure/azure-cli/issues/6571)
* Memperbaiki masalah saat `--endpoint-status` peka huruf besar/kecil. [#6502](https://github.com/Azure/azure-cli/issues/6502)

### <a name="reservations"></a>Reservasi

* [BREAKING CHANGE] Menambahkan parameter wajib `ReservedResourceType` ke `reservations catalog show`
* Menambahkan parameter `Location`ke `reservations catalog show`
* [BREAKING CHANGE] Menghapus `kind` dari `ReservationProperties`
* [BREAKING CHANGE] Mengganti nama `capabilities` menjadi `sku_properties` di `Catalog`
* [BREAKING CHANGE] Menghapus properti `size` dan `tier` dari `Catalog`
* Menambahkan parameter `InstanceFlexibility` ke `reservations reservation update`

### <a name="role"></a>Peran

* Meningkatkan penanganan kesalahan

### <a name="sql"></a>SQL

* Memperbaiki kesalahan yang membingungkan saat menjalankan `az sql db list-editions` untuk lokasi yang tidak tersedia untuk langganan Anda

### <a name="storage"></a>Penyimpanan

* Mengubah output tabel untuk `storage blob download` agar lebih mudah dibaca

### <a name="vm"></a>VM

* Meningkatkan pemeriksaan ukuran mesin virtual yang disempurnakan untuk dukungan jaringan yang dipercepat di `vm create`
* Menambahkan peringatan untuk `vmss create` bahwa ukuran mesin virtual default akan dialihkan dari `Standard_D1_v2` ke `Standard_DS1_v2`
* Menambahkan `--force-update` ke `[vm|vmss] extension set` untuk memperbarui ekstensi meskipun konfigurasi tidak berubah

## <a name="june-13-2018"></a>13 Juni 2018

### <a name="version-2037"></a>Versi 2.0.37

### <a name="core"></a>Core

* Meningkatkan telemetri interaktif

### <a name="version-2036"></a>Versi 2.0.36

### <a name="aks"></a>AKS

* Menambahkan opsi jaringan tingkat lanjut ke `aks create`
* Menambahkan argumen ke `aks create` untuk mengaktifkan pemantauan dan perutean HTTP
* Menambahkan argumen `--no-ssh-key` ke `aks create`
* Menambahkan argumen `--enable-rbac` ke `aks create`
* [PREVIEW] Menambahkan dukungan untuk autentikasi Azure Active Directory ke `aks create`

### <a name="appservice"></a>AppService

* Memperbaiki masalah dengan versi urllib yang tidak kompatibel

## <a name="june-5-2018"></a>5 Juni 2018

### <a name="version-2035"></a>Versi 2.0.35

### <a name="interactive"></a>Interaktif

* Menambahkan batasan pada dependensi mode interaktif

### <a name="version-2034"></a>Versi 2.0.34

### <a name="core"></a>Core

* Menambahkan dukungan untuk referensi sumber daya lintas penyewa
* Meningkatkan keandalan pengunggahan telemetri

### <a name="acr"></a>Azure Container Registry

* Menambahkan dukungan untuk Visual Studio Team Services sebagai lokasi sumber jarak jauh
* Menambahkan perintah `acr import`

### <a name="aks"></a>AKS

* Mengubah `aks get-credentials` untuk membuat file konfigurasi kube dengan izin filesystem yang lebih aman

### <a name="batch"></a>Batch

* Memperbaiki bug dalam pemformatan tabel daftar Kumpulan [[Masalah #4378](https://github.com/Azure/azure-cli/issues/4378)]

### <a name="iot"></a>IOT

* Menambahkan dukungan untuk membuat IoT Hub Tingkat Dasar

### <a name="network"></a>Jaringan

* Meningkatkan `network vnet peering`

### <a name="policy-insights"></a>Policy Insights

* Rilis Awal

### <a name="arm"></a>ARM

* Menambahkan perintah `account management-group`.

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

* Mengubah `vm list-skus` untuk menggunakan kolom tetap dan menambahkan peringatan bahwa `Tier` dan `Size` akan dihapus
* Menambahkan opsi `--accelerated-networking` ke `vm create`
* Menambahkan `--tags` ke `identity create`

## <a name="may-22-2018"></a>22 Mei 2018

Versi 2.0.33

### <a name="core"></a>Core

* Menambahkan dukungan untuk meluaskan `@` dalam nama file

### <a name="acs"></a>ACS

* Menambahkan perintah Dev-Spaces baru `aks use-dev-spaces` dan `aks remove-dev-spaces`
* Memperbaiki kesalahan pengetikan dalam pesan bantuan

### <a name="appservice"></a>AppService

* Meningkatkan perintah pembaruan umum
* Menambahkan dukungan asinkron untuk `webapp deployment source config-zip`

### <a name="container"></a>Kontainer

* Menambahkan dukungan untuk mengekspor grup kontainer dalam format yaml
* Menambahkan dukungan untuk menggunakan file yaml untuk membuat / memperbarui grup kontainer

### <a name="extension"></a>Extensi

* Meningkatkan penghapusan ekstensi

### <a name="interactive"></a>Interaktif

* Mengubah pengelogan untuk membisukan parser untuk penyelesaian
* Meningkatkan penanganan cache bantuan yang buruk

### <a name="keyvault"></a>Az.KeyVault

* Memperbaiki perintah keyvault agar bekerja di cloud shell atau Mesin Virtual dengan identitas

### <a name="network"></a>Jaringan

* Memperbaiki masalah saat `network watcher show-topology` tidak berfungsi dengan vnet dan/atau nama subnet [#6326](https://github.com/Azure/azure-cli/issues/6326)
* Memperbaiki masalah saat beberapa perintah `network watcher` akan mengklaim Network Watcher tidak diaktifkan untuk wilayah yang sebenar telah diaktifkan [#6264](https://github.com/Azure/azure-cli/issues/6264)

### <a name="sql"></a>SQL

* [BREAKING CHANGE] Mengubah objek respons yang dikembalikan dari perintah `db` dan `dw`:
    * Mengganti nama properti `serviceLevelObjective` menjadi `currentServiceObjectiveName`
    * Menghapus properti `currentServiceObjectiveId` dan `requestedServiceObjectiveId`
    * Mengubah properti `maxSizeBytes` menjadi nilai bilangan bulat, bukan string
* [BREAKING CHANGE] Mengubah properti `db` dan `dw` berikut menjadi baca-saja:
    * `requestedServiceObjectiveName`.  Untuk memperbarui, gunakan parameter `--service-objective` atau atur properti `sku.name`
    * `edition`. Untuk memperbarui, gunakan parameter `--edition` atau atur properti `sku.tier`
    * `elasticPoolName`. Untuk memperbarui, gunakan parameter `--elastic-pool` atau atur properti `elasticPoolId`
* [BREAKING CHANGE] Mengubah properti `elastic-pool` berikut menjadi baca-saja:
    * `edition`. Untuk memperbarui, gunakan parameter `--edition`
    * `dtu`. Untuk memperbarui, gunakan parameter `--capacity`
    *  `databaseDtuMin`. Untuk memperbarui, gunakan parameter `--db-min-capacity`
    *  `databaseDtuMax`. Untuk memperbarui, gunakan parameter `--db-max-capacity`
* Menambahkan parameter `--family` dan `--capacity` ke perintah `db`, `dw`, dan `elastic-pool`.
* Menambahkan pemformat tabel ke perintah `db`, `dw`, dan `elastic-pool`.

### <a name="storage"></a>Penyimpanan

* Menambahkan pelengkap untuk argumen `--account-name`
* Memperbaiki masalah dengan `storage entity query`

### <a name="vm"></a>VM

* [BREAKING CHANGE] Menghapus `--write-accelerator` dari `vm create`. Dukungan yang sama dapat diakses melalui `vm update` atau `vm disk attach`
* Memperbaiki pencocokan gambar ekstensi di `[vm|vmss] extension`
* Menambahkan `--boot-diagnostics-storage` ke `vm create` untuk mengambil log boot
* Menambahkan `--license-type` ke `[vm|vmss] update`

## <a name="may-7-2018"></a>7 Mei 2018

Versi 2.0.32

### <a name="core"></a>Core

* Memperbaiki pengecualian yang tidak ditangani saat mengambil rahasia dari akun perwakilan layanan dengan sertifikat
* Menambahkan dukungan terbatas untuk argumen posisi
* Memperbaiki masalah saat `--query` tidak dapat digunakan dengan `--ids`. [#5591](https://github.com/Azure/azure-cli/issues/5591)
* Meningkatkan skenario penyaluran dari perintah saat menggunakan `--ids`. Mendukung `-o tsv` dengan kueri yang ditentukan atau `-o json` tanpa menentukan kueri
* Menambahkan saran perintah pada kesalahan jika pengguna memiliki kesalahan pengetikan dalam perintah mereka
* Meningkatkan kesalahan saat pengguna mengetik `az ''`
* Menambahkan dukungan jenis sumber daya kustom untuk modul dan ekstensi perintah

### <a name="acr"></a>Azure Container Registry

* Menambahkan perintah Build Azure Container Registry
* Meningkatkan pesan kesalahan sumber daya tidak ditemukan
* Meningkatkan performa pembuatan sumber daya dan penanganan kesalahan
* Meningkatkan masuk acr di konsol yang bukan standar dan WSL
* Meningkatkan pesan kesalahan perintah repositori
* Mempoerbarui kolom tabel dan pemesanan

### <a name="acs"></a>ACS

* Menambahkan peringatan bahwa `az aks` adalah layanan pratinjau
* Memperbaiki masalah izin di `aks install-connector` saat `--aci-resource-group` tidak ditentukan

### <a name="ams"></a>AMS

* Rilis awal - Mengelola sumber daya Azure Media Services

### <a name="appservice"></a>Appservice

* Memperbaiki bug di `webapp delete` saat `--slot` disediakan
* Menghapus `--runtime-version` dari `webapp auth update`
* Menambahkan dukungan untuk versi min\_tls\_ & https2.0
* Menambahkan dukungan untuk multikontainer

### <a name="batch-ai"></a>Batch AI

* Mengubah `batchai create cluster` untuk mematuhi prioritas mesin virtual yang dikonfigurasi dalam file konfigurasi kluster

### <a name="cognitive-services"></a>Cognitive Services

* Memperbaiki kesalahan pengetikan pada contoh untuk `cognitiveservices account create` [#5603](https://github.com/Azure/azure-cli/issues/5603)

### <a name="consumption"></a>Consumption

* Menambahkan perintah baru untuk API anggaran

### <a name="container"></a>Kontainer

* Menghapus persyaratan `--registry-server` untuk `container create` saat server registri disertakan dalam nama gambar

### <a name="cosmos-db"></a>Cosmos DB

* Memperkenalkan dukungan VNET untuk Azure CLI - Cosmos DB

### <a name="dms"></a>DMS

* Rilis awal - Menambahkan dukungan untuk skenario migrasi SQL ke Azure SQL

### <a name="extension"></a>Extensi

* Memperbaiki bug saat metadata ekstensi berhenti ditampilkan

### <a name="interactive"></a>Interaktif

* Mengizinkan pelengkap interaktif berfungsi dengan argumen posisi
* Hasil yang lebih ramah pengguna saat pengguna mengetik '\'
* Memperbaiki penyelesaian untuk parameter tanpa bantuan
* Memperbaiki deskripsi untuk grup perintah

### <a name="lab"></a>Laboratorium

* Memperbaiki regresi dari konversi knack

### <a name="network"></a>Jaringan

* [BREAKING CHANGE] Menghapus parameter `--ids` untuk:
  * `express-route auth list`
  * `express-route peering list`
  * `nic ip-config list`
  * `nsg rule list`
  * `route-filter rule list`
  * `route-table route list`
  * `traffic-manager endpoint list`

### <a name="profile"></a>Profil

* Memperbaiki deteksi sumber `disk create`
* [BREAKING CHANGE] Menghapus `--msi-port` dan `--identity-port` karena tidak lagi digunakan
* Memperbaiki kesalahan pengetikan di ringkasan singkat `account get-access-token`

### <a name="redis"></a>Redis

* Menghentikan `redis patch-schedule patch-schedule show` yang mendukung `redis patch-schedule show`
* Menghentikan `redis list-all`. Fungsionalitas ini telah digabungkan menjadi `redis list`
* Menghentikan `redis import-method` yang mendukung `redis import`
* Menambahkan dukungan untuk `--ids` ke berbagai perintah

### <a name="role"></a>Peran

* [BREAKING CHANGE] Menghapus `ad sp reset-credentials` yang tidak digunakan lagi

### <a name="storage"></a>Penyimpanan

* Mengizinkan token sas tujuan untuk diterapkan ke sumber untuk salinan blob jika sas sumber dan kunci akun tidak ditentukan
* Memperlihatkan --socket-timeout untuk pengunggahan dan pengunduhan blob
* Memperlakukan nama blob yang dimulai dengan pemisah jalur sebagai jalur relatif
* Izinkan `storage blob copy --source-sas` dengan memulai char kueri, '?'
* Memperbaiki `storage entity query --marker` untuk menerima daftar key=values

### <a name="vm"></a>VM

* Memperbaiki logika deteksi yang tidak valid pada uri blob yang tidak terkelola
* Menambahkan enkripsi disk dukungan tanpa perwakilan layanan yang disediakan pengguna
* [BREAKING CHANGE] Jangan gunakan Mesin Virtual 'ManagedIdentityExtension' untuk dukungan MSI
* Menambahkan dukungan untuk kebijakan pengeluaran ke `vmss`
* [BREAKING CHANGE] Menghapus `--ids` dari:
  * `vm extension list`
  * `vm secret list`
  * `vm unmanaged-disk list`
  * `vmss nic list`
* Menambahkan dukungan akselerator penulisan
* Menambahkan `vmss perform-maintenance`
* Memperbaiki `vm diagnostics set` untuk mendeteksi jenis OS Mesin Virtual dengan andal
* Mengubah `vm resize` untuk memeriksa apakah ukuran yang diminta berbeda dari yang ditetapkan saat ini dan memperbarui hanya pada perubahan


## <a name="april-10-2018"></a>10 April 2018

Versi 2.0.31

### <a name="acr"></a>Azure Container Registry

* Meningkatkan penanganan kesalahan dari wincred fallback

### <a name="acs"></a>ACS

* Mengubah aks yang membuat SPN agar berlaku selama 5 tahun

### <a name="appservice"></a>Appservice

* [BREAKING CHANGE]: Removed `assign-identity`
* Memperbaiki pengecualian yang tidak tertangkap untuk paket webapp yang tidak ada

### <a name="batchai"></a>BatchAI

* Menambahkan dukungan untuk API 2018-03-01

  - Pemasangan tingkat pekerjaan
  - Variabel lingkungan dengan nilai rahasia
  - Pengaturan penghitung kinerja
  - Pelaporan segmen jalur khusus pekerjaan
  - Dukungan untuk subfolder dalam api file daftar
  - Penggunaan dan batas pelaporan
  - Mengizinkan untuk menentukan jenis penembolokan untuk server NFS
  - Dukungan untuk gambar kustom
  - Menambahkan dukungan toolkit pyTorch

* Menambahkan perintah `job wait` yang memungkinkan untuk menunggu penyelesaian pekerjaan dan melaporkan kode keluar pekerjaan
* Menambahkan perintah `usage show` untuk mencantumkan penggunaan dan batas sumber daya Batch AI saat ini untuk berbagai wilayah
* Cloud nasional didukung
* Menambahkan argumen baris perintah pekerjaan untuk memasang filesystem pada tingkat pekerjaan selain file konfigurasi
* Menambahkan lebih banyak opsi untuk menyesuaikan kluster - prioritas mesin virtual, subnet, jumlah node awal untuk kluster skala otomatis, menentukan gambar kustom
* Menambahkan opsi baris perintah untuk menentukan jenis penembolokan untuk NFS yang dikelola Batch AI
* Menentukan filesystem pemasangan yang disederhanakan dalam file konfigurasi. Sekarang Anda dapat menghilangkan kredensial untuk Berbagi Azure dan Kontainer Blob Azure - CLI akan mengisi kredensial yang hilang menggunakan kunci akun penyimpanan yang disediakan melalui parameter baris perintah atau ditentukan melalui variabel lingkungan atau akan mengkueri kunci dari Azure Storage (jika akun penyimpanan termasuk pada langganan saat ini)
* Perintah aliran file pekerjaan sekarang otomatis selesai ketika pekerjaan selesai (berhasil, gagal, dihentikan atau dihapus)
* Meningkatkan output `table` untuk operasi `show`
* Menambahkan opsi `--use-auto-storage` untuk pembuatan kluster. Opsi ini membuatnya lebih mudah untuk mengelola akun penyimpanan dan memasang Berbagi Azure dan Kontainer Blob Azure ke kluster
* Menambahkan opsi `--generate-ssh-keys` ke `cluster create` dan `file-server create`
* Menambahkan kemampuan untuk menyediakan tugas penyiapan node melalui baris perintah
* [BREAKING CHANGE] Memindahkan perintah `job stream-file` dan `job list-files` di bawah grup `job file`
* [BREAKING CHANGE] Mengganti nama `--admin-user-name` menjadi `--user-name` dalam perintah `file-server create` agar konsisten dengan perintah `cluster create`

### <a name="billing"></a>Billing

* Menambahkan perintah akun pendaftaran

### <a name="consumption"></a>Consumption

* Menambahkan perintah `marketplace`
* [BREAKING CHANGE] Mengganti nama `reservations summaries` menjadi `reservation summary`
* [BREAKING CHANGE] Mengganti nama `reservations details` menjadi `reservation detail`
* [BREAKING CHANGE] Menghapus opsi singkat `--reservation-order-id` dan `--reservation-id` untuk perintah `reservation`
* [BREAKING CHANGE] Menghapus opsi singkat `--grain` untuk perintah `reservation summary`
* [BREAKING CHANGE] Menghapus opsi singkat `--include-meter-details` untuk perintah `pricesheet`

### <a name="container"></a>Kontainer

* Menambahkan parameter pemasangan volume repositori git `--gitrepo-url` `--gitrepo-dir` `--gitrepo-revision` dan `--gitrepo-mount-path`
* Memperbaiki [#5926](https://github.com/Azure/azure-cli/issues/5926): `az container exec` gagal saat --container-name ditentukan

### <a name="extension"></a>Extensi

* Mengubah pesan pemeriksaan distribusi menjadi tingkat debug

### <a name="interactive"></a>Interaktif

* Mengubah untuk menghentikan penyelesaian atas perintah yang tidak dikenal
* Menambahkan hook peristiwa sebelum dan sesudah substruktur pohon perintah dibuat
* Menambahkan penyelesaian untuk parameter `--ids`

### <a name="network"></a>Jaringan

* Memperbaiki [#5936](https://github.com/Azure/azure-cli/issues/5936): `application-gateway create` tag tidak dapat diatur
* Menambahkan argumen `--auth-certs` untuk melampirkan sertifikat autentikasi untuk `application-gateway http-settings [create|update]`. [#4910](https://github.com/Azure/azure-cli/issues/4910)
* Menambahkan perintah `ddos-protection` untuk membuat rencana perlindungan DDoS
* Menambahkan dukungan untuk `--ddos-protection-plan` hingga `vnet [create|update]` untuk mengaitkan VNet ke paket perlindungan DDoS
* Memperbaiki masalah dengan bendera `--disable-bgp-route-propagation` di `network route-table [create|update]`
* Argumen semu yang dihapus `--public-ip-address-type` dan `--subnet-type` untuk `network lb [create|update]`
* Menambahkan dukungan untuk catatan TXT dengan urutan escape RFC 1035 ke `network dns zone [import|export]` dan `network dns record-set txt add-record`

### <a name="profile"></a>Profil

* Menambahkan dukungan untuk akun Azure Classic di `account list`
* [BREAKING CHANGE] Menghapus argumen `--msi` & `--msi-port`

### <a name="rdbms"></a>RDBMS

* Menambahkan perintah `georestore`
* Menghapus pembatasan ukuran penyimpanan dari perintah `create`

### <a name="resource"></a>Sumber daya

* Menambahkan dukungan untuk `--metadata` ke `policy definition create`
* Menambahkan dukungan untuk `--metadata`, `--set`, `--add`, `--remove` hingga `policy definition update`

### <a name="sql"></a>SQL

* Menambahkan `sql elastic-pool op list` dan `sql elastic-pool op cancel`

### <a name="storage"></a>Penyimpanan

* Meningkatkan pesan kesalahan untuk string koneksi yang rusak

### <a name="vm"></a>VM

* Menambahkan dukungan untuk mengonfigurasi jumlah domain kesalahan platform ke `vmss create`
* Mengubah `vmss create` ke default ke LB Standar untuk set skala zona, besar, atau grup penempatan tunggal yang dinonaktifkan
* [BREAKING CHANGE]: Removed `vm assign-identity`, `vm remove-identity and `vm format-secret`
* Menambahkan dukungan untuk SKU IP Publik ke `vm create`
* Menambahkan argumen `--keyvault` dan `--resource-group` ke `vm secret format` untuk mendukung skenario saat perintah tidak dapat menyelesaikan ID vault. [#5718](https://github.com/Azure/azure-cli/issues/5718)
* Kesalahan yang lebih baik untuk `[vm|vmss create]` saat lokasi grup sumber daya tidak memiliki dukungan zona


## <a name="march-27-2018"></a>27 Maret 2018

Versi 2.0.30

### <a name="core"></a>Core

* Menunjukkan pesan untuk ekstensi yang ditandai sebagai pratinjau di bantuan

### <a name="acs"></a>ACS

* Memperbaiki kesalahan verifikasi sertifikat SSL untuk `aks install-cli` di Cloud Shell

### <a name="appservice"></a>Appservice

* Menambahkan dukungan khusus HTTPS ke `webapp update`
* Menambahkan dukungan untuk slot ke `az webapp identity [assign|show]` dan `az functionapp identity [assign|show]`

### <a name="backup"></a>Cadangan

* Menambahkan perintah baru `az backup protection isenabled-for-vm`. Perintah ini dapat digunakan untuk memeriksa apakah Mesin Virtual dicadangkan oleh vault apa pun dalam langganan
* Mengaktifkan ID objek Azure untuk parameter `--resource-group` dan `--vault-name` untuk perintah berikut:
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
* Mengubah parameter `--name` untuk menerima format output dari perintah `backup ... show`

### <a name="container"></a>Kontainer

* Menambahkan perintah `container exec`. Menjalankan perintah dalam kontainer untuk grup kontainer yang sedang berjalan
* Mengizinkan output tabel untuk membuat dan memperbarui grup kontainer

### <a name="extension"></a>Extensi

* Menambahkan pesan untuk `extension add` jika ekstensi dalam pratinjau
* Mengubah `extension list-available` untuk menunjukkan data ekstensi lengkap dengan `--show-details`
* [BREAKING CHANGE] Mengubah `extension list-available` untuk menunjukkan data ekstensi yang disederhanakan secara default

### <a name="interactive"></a>Interaktif

* Mengubah penyelesaian untuk diaktifkan segera setelah pemuatan tabel perintah selesai
* Memperbaiki bug dengan menggunakan parameter `--style`
* Lexer interaktif diinstansiasi setelah tabel perintah dicadangkan jika tidak ada
* Meningkatkan dukungan pelengkap

### <a name="lab"></a>Laboratorium

* Memperbaiki bug dengan perintah `create environment`

### <a name="monitor"></a>Monitor

* Menambahkan dukungan untuk `--top`, `--orderby`, dan `--namespace` ke `metrics list` [#5785](https://github.com/Azure/azure-cli/issues/5785)
* Memperbaiki [#4529](https://github.com/Azure/azure-cli/issues/5785): `metrics list` Menerima daftar metrik yang dipisahkan spasi untuk diambil
* Menambahkan dukungan untuk `--namespace` ke `metrics list-definitions` [#5785](https://github.com/Azure/azure-cli/issues/5785)

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk zona DNS Privat

### <a name="profile"></a>Profil

* Menambahkan peringatan untuk `--identity-port` dan `--msi-port` ke `login`

### <a name="rdbms"></a>RDBMS

* Menambahkan model bisnis versi API Ketersediaan Umum API 2017-12-01

### <a name="resource"></a>Sumber daya

* [BREAKING CHANGE]: Changed `provider operation [list|show]` to not require `--api-version`

### <a name="role"></a>Peran

* Menambahkan dukungan untuk konfigurasi akses yang diperlukan dan klien asli ke `az ad app create`
* Mengubah perintah `rbac` untuk mengembalikan kurang dari 1000 ID pada resolusi objek
* Menambahkan perintah manajemen kredensial `ad sp credential [reset|list|delete]`
* [BREAKING CHANGE] Menghapus 'properti' dari output `az role assignment [list|show]`
* Menambahkan dukungan untuk izin `dataActions` dan `notDataActions` ke `role definition`

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah saat mengunggah file dengan ukuran antara 195GB dan 200GB
* Memperbaiki [#4049](https://github.com/Azure/azure-cli/issues/4049): Masalah dengan menambahkan pengunggahan blob yang mengabaikan parameter kondisi

### <a name="vm"></a>VM

* Menambahkan peringatan ke `vmss create` untuk perubahan yang melanggar yang akan datang untuk kumpulan dengan instans 100+
* Menambahkan dukungan ketahanan zona ke `vm [snapshot|image]`
* Mengubah tampilan instans disk untuk melaporkan status enkripsi yang lebih baik
* [BREAKING CHANGE] Mengubah `vm extension delete` menjadi tidak lagi mengembalikan hasil

## <a name="march-13-2018"></a>13 Maret 2018

Versi 2.0.29

### <a name="acr"></a>Azure Container Registry

* Menambahkan dukungan untuk parameter `--image` ke `repository delete`
* Menghentikan parameter `--manifest` dan `--tag` dari perintah `repository delete`
* Menambahkan perintah `repository untag` untuk menghapus tag tanpa menghapus data

### <a name="acs"></a>ACS

* Menambahkan perintah `aks upgrade-connector` untuk meningkatkan konektor yang ada
* Mengubah file konfigurasi `kubectl` untuk menggunakan YAML gaya blok yang lebih mudah dibaca

### <a name="advisor"></a>Advisor

* [BREAKING CHANGE] Mengganti nama `advisor configuration get` menjadi `advisor configuration list`
* [BREAKING CHANGE] Mengganti nama `advisor configuration set` menjadi `advisor configuration update`
* [BREAKING CHANGE] Menghapus `advisor recommendation generate`
* Menambahkan parameter `--refresh` ke `advisor recommendation list`
* Menambahkan perintah `advisor recommendation show`

### <a name="appservice"></a>Appservice

* Menghentikan `[webapp|functionapp] assign-identity`
* Menambahkan perintah identitas terkelola `webapp identity [assign|show]` dan `functionapp identity [assign|show]`

### <a name="eventhubs"></a>Eventhubs

* Rilis awal

### <a name="extension"></a>Extensi

* Menambahkan pemeriksaan untuk memperingatkan pengguna jika distro yang digunakan berbeda dengan yang disimpan dalam file sumber paket, karena hal ini dapat menyebabkan kesalahan

### <a name="interactive"></a>Interaktif

* Memperbaiki [#5625](https://github.com/Azure/azure-cli/issues/5625): Mempertahankan riwayat di berbagai sesi
* Memperbaiki [#3016](https://github.com/Azure/azure-cli/issues/3016): Riwayat tidak dicatat saat dalam cakupan
* Memperbaiki [#5688](https://github.com/Azure/azure-cli/issues/5688): Penyelesaian tidak muncul jika pemuatan tabel perintah mengalami pengecualian
* Memperbaiki pengukur kemajuan untuk operasi yang berjalan lama

### <a name="monitor"></a>Monitor

* Menghentikan perintah `monitor autoscale-settings`
* Menambahkan perintah `monitor autoscale`
* Menambahkan perintah `monitor autoscale profile`
* Menambahkan perintah `monitor autoscale rule`

### <a name="network"></a>Jaringan

* [BREAKING CHANGE] Menghapus parameter `--tags` dari `route-filter rule create`
* Menghapus beberapa nilai default yang salah untuk perintah berikut:
  * `network express-route update`
  * `network nsg rule update`
  * `network public-ip update`
  * `traffic-manager profile update`
  * `network vnet-gateway update`
* Menambahkan perintah` `network watcher connection-monitor`
* Menambahkan parameter `--vnet` dan `--subnet` ke `network watcher show-topology`

### <a name="profile"></a>Profil

* Menghentikan parameter `--msi` untuk `az login`
* Menambahkan parameter `--identity` untuk `az login` guna menggantikan `--msi`

### <a name="rdbms"></a>RDBMS

* [PREVIEW] Mengubah untuk menggunakan API 2017-12-01-preview

### <a name="service-bus"></a>Service Bus

* Rilis awal

### <a name="storage"></a>Penyimpanan

* Memperbaiki [#4971](https://github.com/Azure/azure-cli/issues/4971): `storage blob copy` sekarang mendukung cloud Azure lainnya
* Memperbaiki [#5286](https://github.com/Azure/azure-cli/issues/5286): Perintah batch `storage blob [delete-batch|download-batch|upload-batch]` tidak lagi menimbulkan kesalahan pada kegagalan prasyarat

### <a name="vm"></a>VM

* Menambahkan dukungan ke `[vm|vmss] create` untuk melampirkan disk data yang tidak dikelola dan mengonfigurasi penembolokan
* Menghentikan `[vm|vmss] assign-identity` dan `[vm|vmss] remove-identity`
* Menambahkan perintah `vm identity [assign|remove|show]` dan `vmss identity [assign|remove|show]` untuk menggantikan perintah yang tidak digunakan lagi
* Mengubah prioritas default di `vmss create` menjadi Tidak Ada

## <a name="february-27-2018"></a>27 Februari 2018

Versi 2.0.28

### <a name="core"></a>Core

* Memperbaiki [#5184](https://github.com/Azure/azure-cli/issues/5184): Masalah penginstalan Homebrew
* Menambahkan dukungan untuk telemetri ekstensi dengan kunci kustom
* Menambahkan pengelogan HTTP ke `--debug`

### <a name="acs"></a>ACS

* Mengubah untuk menggunakan Bagan helm `virtual-kubelet-for-aks` untuk `aks install-connector` secara default
* Memperbaiki masalah: Izin yang tidak memadai untuk perwakilan layanan untuk membuat masalah grup kontainer ACI
* Menambahkan parameter `--aci-container-group`, `--location`, dan `--image-tag` ke `aks install-connector`
* Menghapus pemberitahuan penghentian dari `aks get-versions`

### <a name="appservice"></a>Appservice

* Pembaruan untuk versi SDK baru (Azure-mgmt-web 0.35.0)
* Memperbaiki [#5538](https://github.com/Azure/azure-cli/issues/5538): `Free` dilaporkan sebagai SKU tidak valid

### <a name="cognitive-services"></a>Cognitive Services

* Memperbarui 'pemberitahuan' saat membuat akun Cognitive Services baru

### <a name="consumption"></a>Consumption

* Menambahkan perintah baru untuk API pricesheet
* Memperbarui format Detail Penggunaan dan Detail Reservasi yang ada

### <a name="container"></a>Kontainer

* Menambahkan argumen `--secrets` dan `--secrets-mount-path` ke `container create` untuk menggunakan rahasia di ACI

### <a name="network"></a>Jaringan

* Memperbaiki [#5559](https://github.com/Azure/azure-cli/issues/5559): Klien tidak ada di `network vnet-gateway vpn-client generate`

### <a name="resource"></a>Sumber daya

* Mengubah `group deployment export` untuk menampilkan sebagian templat dan kesalahan saat gagal

### <a name="role"></a>Peran

* Menambahkan `role assignment list-changelogs` untuk memungkinkan pengauditan peran perwakilan layanan

### <a name="sql"></a>SQL

* Menambahkan dukungan redundansi zona untuk database dan kumpulan elastis saat membuat dan memperbarui

### <a name="storage"></a>Penyimpanan

* Mengaktifkan dengan menentukan jalur tujuan/prefiks untuk `storage blob [upload-batch|download-batch]`

### <a name="vm"></a>VM

* Menambahkan dukungan untuk memasang/melepas disk pada satu instans Virtual Machine Scale Sets


## <a name="february-13-2018"></a>13 Februari 2018

Versi 2.0.27

### <a name="core"></a>Core

* Mengubah autentikasi menjadi kunci pada ID langganan dan nama pada masuk MSI

### <a name="acs"></a>ACS

* [BREAKING CHANGE] Mengganti nama `aks get-versions` menjadi `aks get-upgrades` untuk kepentingan akurasi
* Mengubah `aks get-versions` untuk menunjukkan versi Kubernetes yang tersedia untuk `aks create`
* Mengubah default `aks create` untuk membiarkan server memilih versi Kubernetes
* Memperbarui pesan bantuan yang mengacu pada perwakilan layanan yang dihasilkan oleh AKS
* Mengubah ukuran node default untuk `aks create` dari "Standard\_D1\_v2" menjadi "Standard\_DS1\_v2"
* Meningkatkan keandalan saat menemukan pod dasbor untuk `az aks browse`
* Memperbaiki `aks get-credentials` untuk menangani kesalahan Unicode saat memuat file konfigurasi Kubernetes
* Menambahkan pesan ke `az aks install-cli` untuk membantu mendapatkan `kubectl` di `$PATH`

### <a name="appservice"></a>Appservice

* Memperbaiki masalah saat `webapp [backup|restore]` gagal karena referensi null
* Menambahkan dukungan untuk paket layanan aplikasi default melalui `az configure --defaults appserviceplan=my-asp`

### <a name="cdn"></a>CDN

* Menambahkan perintah `cdn custom-domain [enable-https|disable-https]`

### <a name="container"></a>Kontainer

* Menambahkan opsi `--follow` ke `az container logs` untuk log streaming
* Menambahkan perintah `container attach` yang melampirkan output standar lokal dan aliran kesalahan ke kontainer dalam grup kontainer

### <a name="cosmosdb"></a>CosmosDB

* Menambahkan dukungan untuk kemampuan pengaturan

### <a name="extension"></a>Extensi

* Menambahkan dukungan untuk parameter `--pip-proxy` ke perintah `az extension [add|update]`
* Menambahkan dukungan untuk argumen `--pip-extra-index-urls` ke perintah `az extension [add|update]`

### <a name="feedback-reference"></a>Referensi umpan balik

* Menambahkan informasi ekstensi ke data telemetri

### <a name="interactive"></a>Interaktif

* Memperbaiki masalah saat pengguna diminta untuk masuk saat menggunakan mode interaktif di Cloud Shell
* Memperbaiki regresi dengan penyelesaian parameter yang hilang

### <a name="iot"></a>IoT

* Memperbaiki masalah saat `iot dps access policy [create|update]` akan menampilkan kesalahan 'tidak ditemukan' saat berhasil
* Memperbaiki masalah saat `iot dps linked-hub [create|update]` akan menampilkan kesalahan 'tidak ditemukan' saat berhasil
* Menambahkan dukungan `--no-wait` ke `iot dps access policy [create|update]` dan `iot dps linked-hub [create|update]`
* Mengubah `iot hub create` untuk memungkinkan menentukan jumlah partisi

### <a name="monitor"></a>Monitor

* Memperbaiki perintah `az monitor log-profiles create`

### <a name="network"></a>Jaringan

* Memperbaiki opsi `--tags` untuk perintah berikut:
  * `network public-ip create`
  * `network lb create`
  * `network local-gateway create`
  * `network nic create`
  * `network vnet-gateway create`
  * `network vpn-connection create`

### <a name="profile"></a>Profil

* Mengaktifkan `az login` dari mode interaktif

### <a name="resource"></a>Sumber daya

* Menambahkan kembali `feature show`

### <a name="role"></a>Peran

* Menambahkan argumen `--available-to-other-tenants` ke `ad app update`

### <a name="sql"></a>SQL

* Menambahkan perintah `sql server dns-alias`
* Menambahkan `sql db rename`
* Menambahkan dukungan untuk argumen `--ids` ke semua perintah sql

### <a name="storage"></a>Penyimpanan

* Menambahkan perintah `storage blob service-properties delete-policy` dan `storage blob undelete` untuk mengaktifkan penghapusan sementara

### <a name="vm"></a>VM

* Memperbaiki crash saat enkripsi Mesin Virtual mungkin tidak sepenuhnya diinisialisasi
* Menambahkan output ID prinsipal saat mengaktifkan MSI
* Memperbaiki `vm boot-diagnostics get-boot-log`


## <a name="january-31-2018"></a>31 Januari 2018

Versi 2.0.26

### <a name="core"></a>Core

* Menambahkan dukungan pengambilan token mentah dalam konteks MSI
* Menghapus string indikator polling setelah menyelesaikan LRO di Windows cmd.exe
* Menambahkan peringatan yang muncul saat menggunakan default yang dikonfigurasi telah diubah menjadi entri tingkat INFO. Menggunakan `--verbose` untuk melihat
* Menambahkan indikator kemajuan untuk perintah tunggu

### <a name="acs"></a>ACS

* Memperjelas argumen `--disable-browser`
* Meningkatkan penyelesaian tab untuk argumen `--vm-size`

### <a name="appservice"></a>Appservice

* Memperbaiki `webapp log [tail|download]`
* Menghapus centang `kind` pada webapps dan fungsi

### <a name="cdn"></a>CDN

* Memperbaiki masalah klien yang hilang dengan `cdn custom-domain create`

### <a name="cosmosdb"></a>CosmosDB

* Memperbaiki deskripsi parameter untuk kebijakan failover

### <a name="interactive"></a>Interaktif

* Memperbaiki masalah saat penyelesaian opsi perintah tidak lagi muncul

### <a name="network"></a>Jaringan

* Menambahkan perlindungan untuk `--cert-password` ke `application-gateway create`
* Memperbaiki masalah dengan `application-gateway update` saat `--sku` salah menerapkan nilai default
* Menambahkan perlindungan untuk `--shared-key` dan `--authorization-key` ke `vpn-connection create`
* Memperbaiki masalah klien yang hilang dengan `asg create`
* Menambahkan parameter `--file-name / -f` untuk nama yang diekspor ke `dns zone export`
* Memperbaiki masalah berikut dengan `dns zone export`:
  * Memperbaiki masalah saat catatan TXT panjang salah diekspor
  * Memperbaiki masalah saat catatan TXT yang dikutip salah diekspor tanpa tanda kutip escape
* Memperbaiki masalah saat catatan tertentu diimpor dua kali dengan `dns zone import`
* Memulihkan perintah `vnet-gateway root-cert` dan `vnet-gateway revoked-cert`

### <a name="profile"></a>Profil

* Memperbaiki `get-access-token` agar berfungsi di dalam Mesin Virtual dengan identitas

### <a name="resource"></a>Sumber daya

* Memperbaiki bug dengan `deployment [create|validate]` saat peringatan salah ditampilkan saat bidang 'jenis' templat berisi nilai huruf besar

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah dengan memigrasikan akun Storage V1 ke Storage V2
* Menambahkan pelaporan kemajuan untuk semua perintah pengunggahan/pengunduhan
* Memperbaiki bug yang mencegah opsi argumen "-n" dengan `storage account check-name`
* Menambahkan kolom 'snapshot' ke output tabel untuk `blob [list|show]`
* Memperbaiki bug dengan berbagai parameter yang perlu diuraikan sebagai ints

### <a name="vm"></a>VM

* Menambahkan perintah `vm image accept-terms` untuk memungkinkan pembuatan Mesin Virtual dari gambar dengan biaya tambahan
* Memperbaiki `[vm|vmss create]` untuk memastikan perintah dapat berjalan di bawah proksi dengan sertifikat yang tidak ditandatangani
* [PREVIEW] Menambahkan dukungan untuk prioritas "rendah" ke Virtual Machine Scale Sets
* Menambahkan perlindungan untuk `--admin-password` ke `[vm|vmss] create`


## <a name="january-17-2018"></a>17 Januari 2018

Versi 2.0.25

### <a name="acr"></a>Azure Container Registry

* Menambahkan fallback masuk acr pada kesalahan kredensial Windows
* Mengaktifkan log registri

### <a name="acs"></a>ACS

* Memperbaiki perintah `get-credentials`
* Menghapus persyaratan peran SPN

### <a name="appservice"></a>Appservice

* Memperbaiki bug dengan `config ssl upload` saat `hosting_environment_profile` adalah null
* Menambahkan dukungan untuk URL kustom ke `browse`
* Memperbaiki dukungan slot untuk `log tail`

### <a name="backup"></a>Cadangan

* Mengubah opsi `--container-name` dari `backup item list` menjadi opsional
* Menambahkan opsi akun penyimpanan ke `backup restore restore-disks`
* Memperbaiki pemeriksaan lokasi di `backup protection enable-for-vm` agar tidak peka huruf besar/kecil
* Memperbaiki masalah saat perintah gagal dengan nama kontainer yang tidak valid
* Mengubah `backup item list` untuk menyertakan 'Status Kesehatan' secara default

### <a name="batch"></a>Batch

* Mengubah `batch login` untuk menampilkan detail autentikasi

### <a name="cloud"></a>Cloud

* Mengubah agar menjadi tidak memerlukan titik akhir saat mengatur `--profile` di cloud

### <a name="consumption"></a>Consumption

* Menambahkan perintah baru untuk reservasi: `consumption reservations summaries` dan `consumption reservations details`

### <a name="event-grid"></a>Event Grid

* [BREAKING CHANGE] Memindahkan perintah `az eventgrid topic event-subscription` ke `eventgrid event-subscription`
* [BREAKING CHANGE] Memindahkan perintah `az eventgrid resource event-subscription` ke `eventgrid event-subscription`
* [BREAKING CHANGE] Menghapus perintah `eventgrid event-subscription show-endpoint-url`. Menggunakan `eventgrid event-subscription show --include-full-endpoint-url` sebagai gantinya
* Menambahkan perintah `eventgrid topic update`
* Menambahkan perintah `eventgrid event-subscription update`
* Menambahkan parameter `--ids` untuk perintah `eventgrid topic`
* Menambahkan dukungan penyelesaian tab untuk nama topik

### <a name="interactive"></a>Interaktif

* Memperbaiki masalah saat mode interaktif tidak berfungsi dengan Python 2.x
* Memperbaiki kesalahan saat memulai
* Memperbaiki masalah dengan beberapa perintah yang tidak berjalan dalam mode interaktif

### <a name="iot"></a>IoT

* Menambahkan dukungan untuk layanan provisi perangkat
* Menambahkan pesan penghentian dalam perintah dan bantuan perintah
* Menambahkan pemeriksaan IoT untuk memberi tahu pengguna tentang Ekstensi IoT

### <a name="monitor"></a>Monitor

* Menambahkan dukungan pengaturan multi-diagnostik. Parameter `--name` sekarang diperlukan untuk `az monitor diagnostic-settings create`
* Menambahkan perintah `monitor diagnostic-settings categories` untuk mendapatkan kategori pengaturan diagnostik

### <a name="network"></a>Jaringan

* Memperbaiki masalah saat mencoba mengubah ke/dari mode siaga aktif dengan `vnet-gateway update`
* Menambahkan dukungan untuk HTTP2 ke `application-gateway [create|update]`

### <a name="profile"></a>Profil

* Menambahkan dukungan untuk masuk dengan identitas yang ditetapkan pengguna

### <a name="role"></a>Peran

* Menambahkan argumen `--assignee-object-id` ke `role assignment create` untuk melewati kueri grafik

### <a name="service-fabric"></a>Service Fabric

* Menambahkan kesalahan terperinci ke respons validasi saat membuat kluster
* Memperbaiki masalah klien yang hilang dengan beberapa perintah

### <a name="vm"></a>VM

* [PREVIEW] Dukungan lintas zona untuk `vmss`
* [BREAKING CHANGE] Mengubah default zona tunggal `vmss` menjadi penyeimbang beban "Standar"
* [BREAKING CHANGE] Mengubah `externalIdentities` menjadi `userAssignedIdentities` untuk EMSI
* [PREVIEW] Menambahkan dukungan untuk pertukaran disk OS
* Menambahkan dukungan untuk menggunakan gambar Mesin Virtual dari langganan lain
* Menambahkan argumen `--plan-name`, `--plan-product`, `--plan-promotion-code`, dan `--plan-publisher` ke `[vm|vmss] create`
* Memperbaiki masalah kesalahan dengan `[vm|vmss] create`
* Memperbaiki penggunaan sumber daya yang berlebihan yang disebabkan oleh `vm image list --all`

## <a name="december-19-2017"></a>19 Desember 2017

Versi 2.0.23

* Menambahkan dukungan untuk masuk dengan identitas yang ditetapkan pengguna

### <a name="container"></a>Kontainer

* Memperbaiki urutan parameter yang salah untuk log kontainer

### <a name="network"></a>Jaringan

* Menambahkan argumen `--disable-bgp-route-propagation` ke `route-table [create|update]`
* Menambahkan argumen `--ip-tags` ke `public-ip [create|update]`

### <a name="storage"></a>Penyimpanan

* Menambahkan dukungan untuk penyimpanan V2

### <a name="vm"></a>VM

* [PREVIEW] Menambahkan dukungan untuk identitas yang ditetapkan pengguna untuk Mesin Virtual dan VMSSes


## <a name="december-5-2017"></a>5 Desember 2017

Versi 2.0.22

* Menghapus perintah `az component`. Menggunakan `az extension` sebagai gantinya

### <a name="core"></a>Core
* Mengubah titik akhir otoritas Azure Active Directory `AZURE_US_GOV_CLOUD` dari login.microsoftonline.com menjadi login.microsoftonline.us
* Memperbaiki masalah saat telemetri akan terus dikirim ulang

### <a name="acs"></a>ACS

* Menambahkan perintah `aks install-connector` dan `aks remove-connector`
* Meningkatkan pelaporan kesalahan untuk `acs create`
* Memperbaiki penggunaan `aks get-credentials -f` tanpa jalur yang sepenuhnya memenuhi syarat

### <a name="advisor"></a>Advisor

* Rilis awal

### <a name="appservice"></a>Appservice

* Memperbaiki pembuatan nama sertifikat dengan `webapp config ssl upload`
* Memperbaiki `webapp [list|show]` dan `functionapp [list|show]` untuk menampilkan aplikasi yang benar
* Menambahkan nilai bawaan untuk `WEBSITE_NODE_DEFAULT_VERSION`

### <a name="consumption"></a>Consumption

* Menambahkan dukungan untuk versi API 2017-11-30

### <a name="container"></a>Kontainer

* Memperbaiki regresi port default

### <a name="monitor"></a>Monitor

* Menambahkan dukungan multi-dimensi ke perintah metrik

### <a name="resource"></a>Sumber daya

* Menambahkan argumen `--include-response-body` ke `resource show`

### <a name="role"></a>Peran

* Menambahkan tampilan penugasan default untuk administrator "klasik" ke `role assignment list`
* Menambahkan dukungan ke `ad sp reset-credentials` untuk menambahkan kredensial daripada menimpa
* Meningkatkan pelaporan kesalahan untuk `ad sp create-for-rbac`

### <a name="sql"></a>SQL

* Menambahkan perintah `sql db list-usages` dan `sql db show-usage`
* Menambahkan perintah `sql server conn-policy show` dan `sql server conn-policy update`

### <a name="vm"></a>VM

* Menambahkan informasi zona ke `az vm list-skus`


## <a name="november-14-2017"></a>14 November 2017

Versi 2.0.21

### <a name="acr"></a>Azure Container Registry

* Menambahkan dukungan untuk membuat webhook di wilayah replikasi


### <a name="acs"></a>ACS

* Mengubah semua kata dari "agent" menjadi "node" di Azure Kubernetes Service
* Menghentikan opsi `--orchestrator-release` untuk `acs create`
* Mengubah ukuran Mesin Virtual default untuk Azure Kubernetes Service menjadi `Standard_D1_v2`
* Memperbaiki `az aks browse` di Windows
* Memperbaiki `az aks get-credentials` di Windows

### <a name="appservice"></a>Appservice

* Menambahkan sumber penyebaran `config-zip` untuk webapps dan aplikasi fungsi
* Menambahkan opsi `--docker-container-logging` ke `az webapp log config`
* Menghapus opsi `storage` dari parameter `--web-server-logging` dari `az webapp log config`
* Meningkatkan pesan kesalahan untuk `deployment user set`
* Menambahkan dukungan untuk membuat aplikasi fungsi Linux
* Memperbaiki `list-locations`

### <a name="batch"></a>Batch

* Memperbaiki bug di perintah pembuatan kumpulan saat ID sumber daya digunakan dengan bendera `--image`

### <a name="batchai"></a>Batchai

* Menambahkan opsi pendek, `-s`, untuk `--vm-size` saat memberikan ukuran Mesin Virtual dalam perintah `file-server create`
* Menambahkan nama akun penyimpanan dan argumen kunci ke parameter `cluster create`
* Memperbaiki dokumentasi untuk `job list-files` dan `job stream-file`
* Menambahkan opsi pendek, `-r`, untuk `--cluster-name` saat memberikan nama kluster di perintah `job create`

### <a name="cloud"></a>Cloud

* Mengubah `cloud [register|update]` untuk mencegah mendaftarkan cloud yang kehilangan titik akhir yang diperlukan

### <a name="container"></a>Kontainer

* Menambahkan dukungan untuk membuka banyak port
* Menambahkan kebijakan penghidupan ulang grup kontainer
* Menambahkan dukungan untuk memasang Berbagi Azure sebagai volume
* Memperbarui dokumen pembantu

### <a name="data-lake-analytics"></a>Data Lake Analytics

* Mengubah `[job|account] list` untuk menampilkan informasi yang lebih ringkas

### <a name="data-lake-store"></a>Data Lake Store

* Mengubah `account list` untuk menampilkan informasi yang lebih ringkas

### <a name="extension"></a>Extensi

* Menambahkan `extension list-available` untuk mengizinkan mencantumkan ekstensi Microsoft resmi
* Menambahkan `--name` ke `extension [add|update]` untuk mengizinkan menginstal ekstensi berdasarkan nama

### <a name="iot"></a>IoT

* Menambahkan dukungan untuk otoritas sertifikat (OS) dan rantai sertifikat

### <a name="monitor"></a>Monitor

* Menambahkan perintah `activity-log alert`

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk catatan DNS CAA
* Memperbaiki masalah saat titik akhir tidak dapat diperbarui dengan `traffic-manager profile update`
* Memperbaiki masalah saat `vnet update --dns-servers` tidak berfungsi bergantung pada cara VNET dibuat
* Memperbaiki masalah saat nama DNS relatif salah diimpor oleh `dns zone import`

### <a name="reservations"></a>Reservasi

* Rilis pratinjau awal

### <a name="resource"></a>Sumber daya

* Menambahkan dukungan untuk ID sumber daya ke parameter `--resource` dan kunci tingkat sumber daya

### <a name="sql"></a>SQL

* Menambahkan parameter `--ignore-missing-vnet-service-endpoint` ke `sql server vnet-rule [create|update]`

### <a name="storage"></a>Penyimpanan

* Mengubah `storage account create` untuk menggunakan SKU `Standard_RAGRS` sebagai default
* Memperbaiki bug saat menangani nama file/blob yang menyertakan char yang bukan ascii
* Memperbaiki bug yang mencegah penggunaan `--source-uri` dengan `storage [blob|file] copy start-batch`
* Menambahkan perintah ke glob dan menghapus beberapa objek dengan `storage [blob|file] delete-batch`
* Memperbaiki masalah saat mengaktifkan metrik dengan `storage metrics update`
* Memperbaiki masalah dengan file lebih dari 200 GB saat menggunakan `storage blob upload-batch`
* Memperbaiki masalah saat `--bypass` dan `--default-action` diabaikan oleh `storage account [create|update]`

### <a name="vm"></a>VM

* Memperbaiki bug dengan `vmss create` yang mencegah penggunaan tingkat ukuran `Basic`
* Menambahkan argumen `--plan` ke `[vm|vmss] create` untuk gambar kustom dengan informasi tagihan
* Menambahkan perintah `vm secret `[add|remove|list]`
* Mengganti nama `vm format-secret` menjadi `vm secret format`
* Menambahkan argumen `--encrypt format` ke `vm encryption enable`

## <a name="october-24-2017"></a>24 Oktober 2017

Versi 2.0.20

### <a name="core"></a>Core

* Memperbarui `2017-03-09-profile` untuk menggunakan versi `MGMT_STORAGE` API `2016-01-01`

### <a name="acr"></a>Azure Container Registry

* Memperbarui manajemen sumber daya untuk mengarah ke versi API `2017-10-01`
* Mengubah SKU 'gunakan penyimpanan Anda sendiri' ke Klasik
* Mengganti nama SKU registri menjadi Dasar, Standar, dan Premium

### <a name="acs"></a>ACS

* [PREVIEW] Menambahkan perintah `az aks`
* Memperbaiki kubernetes `get-credentials`

### <a name="appservice"></a>Appservice

* Memperbaiki masalah saat log `webapp` yang diunduh mungkin tidak valid

### <a name="component"></a>Komponen

* Menambahkan pesan penghentian yang lebih jelas untuk semua alat penginstal dan perintah konfirmasi

### <a name="monitor"></a>Monitor

* Menambahkan perintah `action-group`

### <a name="resource"></a>Sumber daya

* Memperbaiki ketidakcocokan dengan versi dependensi msrest terbaru di `group export`
* Memperbaiki `policy assignment create` agar berfungsi dengan definisi kebijakan bawaan dan definisi kumpulan kebijakan

### <a name="vm"></a>VM

* Menambahkan argumen `--accelerated-networking` ke `vmss create`


## <a name="october-9-2017"></a>9 Oktober 2017

Versi 2.0.19

### <a name="core"></a>Core

* Menambahkan penanganan URL otoritas ADFS dengan garis miring berikutnya ke Azure Stack

### <a name="appservice"></a>Appservice

* Menambahkan pembaruan umum dengan perintah baru `webapp update`

### <a name="batch"></a>Batch

* Memperbarui ke SDK Batch 4.0.0
* Memperbarui opsi `--image` dari VirtualMachineConfiguration untuk mendukung referensi gambar Azure Resource Manager selain publish:offer:sku:version
* Menambahkan dukungan untuk model ekstensi CLI baru untuk perintah Ekstensi Batch
* Menghapus dukungan Batch dari model komponen

### <a name="batchai"></a>Batchai

* Rilis awal modul Batch AI

### <a name="keyvault"></a>Keyvault

* Memperbaiki masalah autentikasi Key Vault saat menggunakan ADFS di Azure Stack. [(#4448)](https://github.com/Azure/azure-cli/issues/4448)

### <a name="network"></a>Jaringan

* Mengubah argumen `--server` dari `application-gateway address-pool create` menjadi opsional, memungkinkan kumpulan alamat kosong
* Memperbarui `traffic-manager` untuk mendukung fitur terbaru

### <a name="resource"></a>Sumber daya

* Menambahkan dukungan untuk opsi `--resource-group/-g` untuk nama grup sumber daya ke `group`
* Menambahkan perintah untuk `account lock` agar berfungsi dengan kunci tingkat langganan
* Menambahkan perintah untuk `group lock` agar berfungsi dengan kunci tingkat grup
* Menambahkan perintah untuk `resource lock` agar berfungsi dengan kunci tingkat sumber daya

### <a name="sql"></a>Sql

* Menambahkan dukungan untuk SQL Transparent Data Encryption (TDE) dan TDE dengan Bring Your Own Key
* Menambahkan perintah `db list-deleted` dan parameter `db restore --deleted-time`, memungkinkan kemampuan untuk menemukan dan memulihkan database yang dihapus
* Menambahkan `db op list` dan `db op cancel`, memungkinkan kemampuan untuk mencantumkan dan membatalkan operasi yang sedang berlangsung di database

### <a name="storage"></a>Penyimpanan

* Menambahkan dukungan untuk snapshot berbagi

### <a name="vm"></a>Mesin virtual

* Memperbaiki bug di `vm show` saat penggunaan `-d` menyebabkan crash pada alamat ip privat yang hilang
* [PREVIEW] Menambahkan dukungan untuk peningkatan bergulir ke `vmss create`
* Menambahkan dukungan untuk memperbarui pengaturan enkripsi dengan `vm encryption enable`
* Menambahkan parameter `--os-disk-size-gb` ke `vm create`
* Menambahkan parameter `--license-type` untuk Windows ke `vmss create`


## <a name="september-22-2017"></a>########

Versi 2.0.18

### <a name="resource"></a>Sumber daya

* Menambahkan dukungan untuk menunjukkan definisi kebijakan bawaan
* Menambahkan parameter mode dukungan untuk membuat definisi kebijakan
* Menambahkan dukungan untuk definisi dan templat antarmuka pengguna ke `managedapp definition create`
* [BREAKING CHANGE] Mengubah jenis sumber daya `managedapp` dari `appliances` menjadi `applications` dan `applianceDefinitions` menjadi `applicationDefinitions`

### <a name="network"></a>Jaringan

* Menambahkan dukungan untuk zona ketersediaan ke `network lb` dan subperintah `network public-ip`
* Menambahkan dukungan untuk Peering Microsoft IPv6 ke `express-route`
* Menambahkan perintah kelompok keamanan aplikasi `asg`
* Menambahkan argumen `--application-security-groups` ke `nic [create|ip-config create|ip-config update]`
* Menambahkan argumen `--source-asgs` dan `--destination-asgs` ke `nsg rule [create|update]`
* Menambahkan argumen `--ddos-protection` dan `--vm-protection` ke `vnet [create|update]`
* Menambahkan perintah `network [vnet-gateway|vpn-client|show-url]`

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah saat perintah `storage account network-rule` mungkin gagal setelah memperbarui SDK

### <a name="eventgrid"></a>Eventgrid

* Memperbarui SDK Python Azure Event Grid untuk menggunakan versi API yang lebih baru "2017-09-15-preview"

### <a name="sql"></a>SQL

* Mengubah argumen `sql server list` `--resource-group` agar menjadi opsional. Jika tidak ditentukan, semua server sql dalam langganan akan dikembalikan
* Menambahkan param `--no-wait` ke `db [create|copy|restore|update|replica create|create|update]` dan `dw [create|update]`

### <a name="keyvault"></a>Keyvault

* Menambahkan dukungan untuk perintah Keyvault dari belakang proksi

### <a name="vm"></a>VM

* Menambahkan untuk dukungan ke zona ketersediaan ke `[vm|vmss|disk] create`
* Memperbaiki masalah saat menggunakan`--app-gateway ID` dengan `vmss create` akan menyebabkan kegagalan
* Menambahkan argumen `--asgs` ke `vm create`
* Menambahkan dukungan untuk menjalankan perintah pada Mesin Virtual dengan `vm run-command`
* [PREVIEW] Menambahkan dukungan untuk enkripsi disk Virtual Machine Scale Sets dengan `vmss encryption`
* Menambahkan dukungan untuk melakukan pemeliharaan pada Mesin Virtual dengan `vm perform-maintenance`

### <a name="acs"></a>ACS

* [PREVIEW] Menambahkan argumen `--orchestrator-release` ke `acs create` untuk wilayah pratinjau Access Control

### <a name="appservice"></a>Appservice

* Menambahkan kemampuan untuk memperbarui dan menunjukkan pengaturan autentikasi dengan `webapp auth [update|show]`

### <a name="backup"></a>Cadangan

* Rilis pratinjau


## <a name="september-11-2017"></a>########

Versi 2.0.17

### <a name="core"></a>Core

* Mengaktifkan modul perintah untuk mengatur ID korelasi modul perintah sendiri dalam telemetri
* Memperbaiki masalah cadangan JSON saat telemetri diatur ke mode diagnostik

### <a name="acs"></a>Acs

* Menambahkan perintah `acs list-locations`
* Membuat `ssh-key-file` hadir dengan nilai default yang diharapkan

### <a name="appservice"></a>Appservice

* Menambahkan kemampuan untuk membuat webapp dalam grup sumber daya selain dari paket layanan aktif

### <a name="cdn"></a>CDN

* Memperbaiki bug 'CustomDomain tidak dapat digunakan' untuk `cdn custom-domain create`

### <a name="extension"></a>Extensi

* Rilis Awal

### <a name="keyvault"></a>Keyvault

* Memperbaiki masalah saat izin merupakan peka huruf besar/kecil untuk `keyvault set-policy`

### <a name="network"></a>Jaringan

* Mengganti nama `vnet list-private-access-services` menjadi `vnet list-endpoint-services`
* Mengganti nama argumen `--private-access-services` menjadi `--service-endpoints` untuk `vnet subnet create/update`
* Menambahkan dukungan untuk beberapa rentang IP dan rentang port ke `nsg rule create/update`
* Menambahkan dukungan untuk SKU ke `lb create`
* Menambahkan dukungan untuk SKU ke `public-ip create`

### <a name="resource"></a>Sumber daya

* Mengizinkan meneruskan definisi parameter kebijakan sumber daya di `policy definition create`, dan `policy definition update`
* Mengizinkan meneruskan nilai parameter untuk `policy assignment create`
* Mengizinkan untuk meneruskan JSON atau file untuk semua params
* Versi API yang dinaikkan

### <a name="sql"></a>SQL

* Menambahkan perintah `sql server vnet-rule`

### <a name="vm"></a>VM

* Memperbaiki: Jangan tetapkan akses kecuali `--scope` disediakan
* Memperbaiki: Gunakan penamaan ekstensi yang sama seperti portal
* Menghapus `subscription` dari output `[vm|vmss] create`
* Memperbaiki: SKU penyimpanan `[vm|vmss] create` tidak diterapkan pada disk data dengan gambar
* Memperbaiki: `vm format-secret --secrets` tidak akan menerima ID terpisah baris baru

## <a name="august-31-2017"></a>31 Agustus 2017

Versi 2.0.16

### <a name="keyvault"></a>Keyvault

* Memperbaiki bug saat mencoba menyelesaikan pengodean rahasia secara otomatis dengan `secret download`

### <a name="sf"></a>Sf

* Menghentikan semua perintah yang mendukung Service Fabric CLI (sfctl)

### <a name="storage"></a>Penyimpanan

* Memperbaiki masalah saat akun penyimpanan tidak dapat dibuat di wilayah yang tidak mendukung fitur NetworkACL
* Menentukan jenis konten dan pengodean konten selama pengunggahan blob dan file jika tidak ada jenis konten dan pengodean konten yang ditentukan

## <a name="august-28-2017"></a>28 Agustus 2017

Versi 2.0.15

### <a name="cli"></a>CLI

* Menambahkan catatan hukum ke `--version`

### <a name="acs"></a>ACS

* Mengoreksi wilayah pratinjau
* Memformat `dns_name_prefix` default dengan benar
* Mengoptimalkan output perintah acs

### <a name="appservice"></a>Appservice

* [BREAKING CHANGE] Memperbaiki inkonsistensi dalam output `az webapp config appsettings [delete|set]`
* Menambahkan alias baru `-i` untuk `az webapp config container set --docker-custom-image-name`
* Memperlihatkan `az webapp log show`
* Memperlihatkan argumen baru dari `az webapp delete` untuk mempertahankan paket layanan aplikasi, metrik, atau pendaftaran dns
* Memperbaiki: Mendeteksi pengaturan slot dengan benar

### <a name="iot"></a>IoT

* Memperbaiki #3934: Pembuatan kebijakan tidak lagi menghapus kebijakan yang ada

### <a name="network"></a>Jaringan

* [BREAKING CHANGE] Mengganti nama `vnet list-private-access-services` menjadi `vnet list-endpoint-services`
* [BREAKING CHANGE] Mengganti nama opsi `--private-access-services` menjadi `--service-endpoints` untuk `vnet subnet [create|update]`
* Menambahkan dukungan untuk beberapa IP dan rentang port ke `nsg rule [create|update]`
* Menambahkan dukungan untuk SKU ke `lb create`
* Menambahkan dukungan untuk SKU ke `public-ip create`

### <a name="profile"></a>Profil

* Memperlihatkan `--msi` dan `--msi-port` untuk masuk menggunakan identitas mesin virtual

### <a name="service-fabric"></a>Service Fabric

* Rilis pratinjau
* Menyederhanakan aturan pengguna/kata sandi registri untuk perintah
* Memperbaiki perintah kata sandi untuk pengguna bahkan setelah melewati param
* Menambahkan dukungan untuk `registry_cred` kosong

### <a name="storage"></a>Penyimpanan

* Mengaktifkan pengaturan tingkat blob
* Menambahkan argumen `--bypass` dan `--default-action` ke `storage account [create|update]` untuk mendukung penerowongan layanan
* Menambahkan perintah untuk menambahkan aturan VNET dan aturan berbasis IP ke `storage account network-rule`
* Mengaktifkan enkripsi layanan oleh kunci yang dikelola pelanggan
* [BREAKING CHANGE] Mengganti nama opsi `--encryption` menjadi `--encryption-services` untuk perintah `az storage account create and az storage account update`
* Memperbaiki #4220: `az storage account update encryption` - sintaks tidak cocok

### <a name="vm"></a>VM

* Memperbaiki masalah ketika informasi tambahan yang salah ditampilkan untuk `vmss get-instance-view` saat menggunakan `--instance-id *`
* Menambahkan dukungan untuk `--lb-sku` ke `vmss create`:
* Menghapus nama manusia dari nama admin yang tidak diizinkan untuk `[vm|vmss] create`
* Memperbaiki masalah saat `[vm|vmss] create` akan menimbulkan kesalahan jika tidak dapat mengekstrak informasi paket dari gambar
* Memperbaiki crash saat membuat scaleset vmms dengan LB internal
* Memperbaiki masalah saat argumen `--no-wait` tidak berfungsi dengan `vm availability-set create`


## <a name="august-15-2017"></a>15 Agustus 2017

Versi 2.0.14

### <a name="acs"></a>ACS

* Memperbaiki nomor port sshMaster0 untuk kubernetes

### <a name="appservice"></a>Appservice

* Memperbaiki pengecualian saat membuat webapp Linux berbasis git baru

### <a name="event-grid"></a>Event Grid

* Menambahkan dependensi SDK

## <a name="august-11-2017"></a>11 Agustus 2017

Versi 2.0.13

### <a name="acs"></a>ACS

* Menambahkan lebih banyak wilayah pratinjau

### <a name="batch"></a>Batch

* Memperbarui ke SDK Batch 3.1.0 dan SDK Manajemen Batch 4.1.0
* Menambahkan perintah baru yang menunjukkan jumlah tugas dari pekerjaan
* Memperbaiki bug dalam pemrosesan URL SAS file sumber
* Titik akhir akun Batch sekarang mendukung prefiks 'https://' opsional
* Dukungan untuk menambahkan daftar lebih dari 100 tugas ke pekerjaan
* Menambahkan pengelogan debug untuk memuat modul perintah Ekstensi

### <a name="component"></a>Komponen

* Menambahkan peringatan penghentian ke perintah 'az component'

### <a name="container"></a>Kontainer

* `create`: Memperbaiki masalah saat tanda sama dengan tidak diizinkan di dalam variabel lingkungan


### <a name="data-lake-store"></a>Data Lake Store

* Mengaktifkan kontrol kemajuan

### <a name="event-grid"></a>Event Grid

* Rilis awal

### <a name="network"></a>Jaringan

* `lb`: Memperbaiki masalah saat nama sumber daya turunan tertentu tidak diselesaikan dengan benar saat dihilangkan
* `application-gateway {subresource} delete`: Memperbaiki masalah saat `--no-wait` tidak dipatuhi
* `application-gateway http-settings update`: Memperbaiki masalah saat `--connection-draining-timeout` tidak dapat dimatikan
* Memperbaiki kesalahan argumen kata kunci yang tidak terduga `sa_data_size_kilobyes` dengan `az network vpn-connection ipsec-policy add`

### <a name="profile"></a>Profil

* `account list`: Menambahkan `--refresh` untuk menyinkronkan langganan terbaru dari server

### <a name="storage"></a>Penyimpanan

* Mengaktifkan akun penyimpanan pembaruan dengan identitas yang ditetapkan sistem

### <a name="vm"></a>VM

* `availability-set`: Memperlihatkan jumlah domain kesalahan pada konversi
* Memperlihatkan perintah `list-skus`
* Dukungan untuk menetapkan identitas tanpa membuat penetapan peran
* Menerapkan sku penyimpanan untuk melampirkan disk data
* Menghapus nama disk os default dan SKU penyimpanan saat menggunakan disk terkelola


## <a name="july-28-2017"></a>28 Juli 2017

Versi 2.0.12

* Menambahkan perintah kontainer
* Menambahkan modul tagihan dan penggunaan

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

* Mengeluarkan info autentikasi sdk untuk perwakilan layanan dengan sertifikat
* Memperbaiki pengecualian kemajuan penyebaran
* Menggunakan titik akhir arm dari cloud saat ini untuk membuat klien langganan
* Meningkatkan penanganan file cloud.config secara bersamaan (#3636)
* Merefresh id permintaan klien untuk setiap eksekusi perintah
* Membuat klien langganan dengan profil SDK yang tepat (#3635)
* Pelaporan Kemajuan untuk penyebaran templat (#3510)
* Menambahkan dukungan untuk memilih bidang output tabel melalui kueri jmespath (#3581)
* Meningkatkan pembisuan argumen penguraian dan menambahkan riwayat dengan gerakan (#3434)
* Membuat klien langganan dengan profil SDK yang tepat
* Memindahkan semua file rekaman yang ada ke folder terbaru
* Memperbaiki idempotensi untuk pembuatan Mesin Virtual/Virtual Machine Scale Sets (#3586)
* Jalur perintah tidak lagi peka huruf besar/kecil
* Parameter jenis boolean tertentu tidak lagi peka huruf besar/kecil
* Mendukung masuk ke ADFS di server prem seperti Azure Stack
* Memperbaiki penulisan bersamaan ke cloud.config (#3255)

### <a name="acr"></a>Azure Container Registry

* Menambahkan perintah `show-usage` untuk registri terkelola
* Mendukung pembaruan SKU untuk registri terkelola
* Menambahkan registri terkelola dengan SKU terkelola
* Menambahkan webhook untuk registri terkelola dengan modul perintah webhook acr
* Menambahkan autentikasi Azure Active Directory dengan perintah masuk acr
* Menambahkan perintah hapus untuk repositori docker, manifes, dan tag

### <a name="acs"></a>ACS

* Dukungan untuk versi API 2017-07-01

### <a name="appservice"></a>Appservice

* Memperbaiki bug saat daftar webapp Linux tidak akan menghasilkan apa-apa
* Dukungan untuk mengambil kredit dari acr
* Menghapus semua perintah di bawah `appservice web`
* Menutupi kata sandi registri docker dari output perintah (#3656)
* Memastikan browser default digunakan di macOS tanpa kesalahan (#3623)
* Meningkatkan bantuan `webapp log tail` dan `webapp log download` (#3624)
* Memperlihatkan perintah `traffic-routing` untuk mengonfigurasi perutean statik (#3566)
* Menambahkan perbaikan keandalan dalam mengonfigurasi kontrol sumber (#3245)
* Menghapus argumen `--node-version` yang tidak didukung dari `webapp config update` untuk webapps Windows. Sebagai gantinya gunakan `webapp config appsettings set --settings WEBSITE_NODE_DEFAULT_VERSION=...`

### <a name="batch"></a>Batch

* Memperbarui ke SDK Batch 3.0.0 dengan dukungan untuk Mesin Virtual prioritas rendah di kumpulan
* Mengganti nama opsi `pool create` ke `--target-dedicated` menjadi `--target-dedicated-nodes`
* Menambahkan opsi `pool create` `--target-low-priority-nodes` dan `--application-licenses`

### <a name="cdn"></a>CDN

* Memberikan pesan kesalahan yang lebih baik untuk `cdn endpoint list` saat profil yang ditentukan oleh `--profile-name` tidak ada

### <a name="cloud"></a>Cloud

* Mengubah versi API titik akhir metadata cloud ke format YYYY-MM-DD
* Titik akhir galeri tidak diperlukan
* Dukungan untuk mendaftarkan cloud hanya dengan titik akhir manajer sumber daya Azure Resource Manager
* Menyediakan opsi `cloud set` untuk memilih profil saat memilih cloud saat ini
* Memperlihatkan `endpoint_vm_image_alias_doc`

### <a name="cosmosdb"></a>CosmosDB

* Memperbaiki mengizinkan pembuatan kumpulan dengan kunci partisi kustom
* Menambahkan dukungan untuk TTL default kumpulan

### <a name="data-lake-analytics"></a>Data Lake Analytics

* Menambahkan perintah untuk manajemen kebijakan komputasi di bawah judul `dla account compute-policy`
* Menambahkan `dla job pipeline show`
* Menambahkan `dla job recurrence list`

### <a name="data-lake-store"></a>Data Lake Store

* Menambahkan dukungan untuk rotasi brankas kunci yang dikelola pengguna di `dls account update`
* Memperbarui versi SDK filesystem Data Lake Store, mengatasi masalah performa
* Menambahkan perintah `dls enable-key-vault`. Perintah ini mencoba mengaktifkan Key Vault yang disediakan pengguna untuk digunakan mengenkripsi data di akun Data Lake Store

### <a name="interactive"></a>Interaktif

* Meningkatkan waktu aktif mulai dengan menggunakan perintah yang disimpan
* Meningkatkan cakupan pengujian
* Meningkatkan gerakan '?' agar dimasukkan juga ke perintah berikutnya
* Memperbaiki kesalahan interaktif dengan profil 2017-03-09-profile-preview (#3587)
* Mengizinkan `--version` sebagai parameter untuk mode interaktif (#3645)
* Menghentikan kesalahan penampilan mode interaktif dari penyelesaian validasi (#3570)
* Pelaporan kemajuan untuk penyebaran templat (#3510)
* Menambahkan bendera `--progress`
* Menghapus `--debug` dan `--verbose` dari penyelesaian
* Menghapus `interactive` dari penyelesaian (#3324)

### <a name="iot"></a>IoT

* Memperbaiki pembuatan kebijakan tidak lagi menghapus kebijakan yang ada. (#3934)

### <a name="key-vault"></a>Key vault

* Menambahkan perintah untuk fitur pemulihan brankas kunci:
  * `keyvault` subperintah `purge`, `recover`, `keyvault list-deleted`
  * `keyvault secret` subperintah `backup`, `restore`, `purge`, `recover`, `list-deleted`
  * `keyvault certificate` subperintah `purge`, `recover`, `list-deleted`
  * `keyvault key` subperintah `purge`, `recover`, `list-deleted`
* Menambahkan integrasi brankas kunci perwakilan layanan (#3133)
* Memperbarui dataplane brankas kunci ke 0.3.2. (#3307)

### <a name="lab"></a>Laboratorium

* Menambahkan dukungan untuk mengklaim mesin virtual apa pun di lab melalui `az lab vm claim`
* Menambahkan pemformat output tabel untuk `az lab vm list` dan `az lab vm show`

### <a name="monitor"></a>Monitor

* Perbaikan untuk file templat dengan perintah `monitor autoscale-settings get-parameters-template` (#3349)
* Mengganti nama `monitor alert-rule-incidents list` menjadi `monitor alert list-incidents`
* Mengganti nama `monitor alert-rule-incidents show` menjadi `monitor alert show-incident`
* Mengganti nama `monitor metric-defintions list` menjadi `monitor metrics list-definitions`
* Mengganti nama `monitor alert-rules` menjadi `monitor alert`
* Mengubah `monitor alert create`:
  * Subperintah `condition` dan `action` tidak lagi menerima JSON
  * Menambahkan banyak parameter untuk menyederhanakan proses pembuatan aturan
  * `location` tidak lagi diperlukan
  * Menambahkan dukungan nama dan ID untuk target
  * Hapus `--alert-rule-resource-name`
  * Mengganti nama `is-enabled` menjadi `enabled`, tidak lagi diperlukan
  * Default `description` sekarang berdasarkan kondisi yang disediakan
  *  Menambahkan contoh untuk membantu memperjelas format baru
* Mendukung nama atau ID untuk perintah `monitor metric`
* Menambahkan argumen dan contoh kenyamanan ke `monitor alert rule update`

### <a name="network"></a>Jaringan

* Menambahkan perintah `list-private-access-services`
* Menambahkan argumen `--private-access-services` ke `vnet subnet create` dan `vnet subnet update`
* Memperbaiki masalah saat `application-gateway redirect-config create` akan gagal
* Memperbaiki masalah saat `application-gateway redirect-config update` dengan `--no-wait` tidak berfungsi
* Memperbaiki bug saat menggunakan argumen `--servers` dengan `application-gateway address-pool create` dan `application-gateway address-pool update`
* Menambahkan perintah `application-gateway redirect-config`
* Menambahkan perintah ke `application-gateway ssl-policy`: `list-options`, `predefined list`, `predefined show`
* Menambahkan argumen ke `application-gateway ssl-policy set`: `--name`, `--cipher-suites`, `--min-protocol-version`
* Menambahkan argumen ke `application-gateway http-settings create` dan `application-gateway http-settings update`: `--host-name-from-backend-pool`, `--affinity-cookie-name`, `--enable-probe`, `--path`
* Menambahkan argumen ke `application-gateway url-path-map create` dan `application-gateway url-path-map update`: `--default-redirect-config`, `--redirect-config`
* Menambahkan argumen `--redirect-config` ke `application-gateway url-path-map rule create`
* Menambahkan dukungan untuk `--no-wait` ke `application-gateway url-path-map rule delete`
* Menambahkan argumen ke `application-gateway probe create` dan `application-gateway probe update`: `--host-name-from-http-settings`, `--min-servers`, `--match-body`, `--match-status-codes`
* Menambahkan argumen `--redirect-config` ke `application-gateway rule create` dan `application-gateway rule update`
* Menambahkan dukungan untuk `--accelerated-networking` ke `nic create` dan `nic update`
* Menghapus argumen `--internal-dns-name-suffix` dari `nic create`
* Menambahkan dukungan untuk `--dns-servers` ke `nic update` dan `nic create`: Menambahkan dukungan untuk --dns-servers
* Memperbaiki bug saat `local-gateway create` diabaikan `--local-address-prefixes`
* Menambahkan dukungan untuk `--dns-servers` ke `vnet update`
* Memperbaiki bug saat membuat peering tanpa pemfilteran rute dengan `express-route peering create`
* Memperbaiki bug saat argumen `--provider` dan `--bandwidth` tidak berfungsi dengan `express-route update`
* Memperbaiki bug dengan logika default `network watcher show-topology`
* Meningkatkan pemformatan output untuk `network list-usages`
* Menggunakan IP frontend default untuk `application-gateway http-listener create` jika hanya ada satu
* Menggunakan kumpulan alamat default, pengaturan HTTP, dan pendengar HTTP untuk `application-gateway rule create` jika hanya ada satu
* Menggunakan IP frontend default dan kumpulan backend untuk `lb rule create` jika hanya ada satu
* Menggunakan IP frontend default untuk `lb inbound-nat-rule create` jika hanya ada satu

### <a name="profile"></a>Profil

* Mendukung masuk di dalam Mesin Virtual dengan identitas terkelola
* Mendukung output untuk `account show` dalam format file autentikasi SDK
* Menunjukkan peringatan penghentian saat menggunakan '--expanded-view'
* Menambahkan perintah `get-access-token` untuk menyediakan token Azure Active Directory mentah
* Mendukung masuk dengan akun pengguna tanpa langganan terkait

### <a name="rdbms"></a>RDBMS

* Mendukung mencantumkan server di seluruh langganan (#3417)
* Memperbaiki `%s` tidak diproses karena `% server_type` hilang (#3393)
* Memperbaiki peta sumber dokumen dan menambahkan tugas CI untuk memverifikasi (#3361)
* Memperbaiki bantuan MySQL dan PostgreSQL (#3369)

### <a name="resource"></a>Sumber daya

* Meningkatkan perintah untuk parameter yang hilang untuk `group deployment create`
* Meningkatkan penguraian sintaks `--parameters KEY=VALUE`
* Memperbaiki masalah saat file parameter `group deployment create` tidak lagi dikenali menggunakan sintaks `@<file>`
* Mendukung argumen `--ids` untuk perintah `resource` dan `managedapp`
* Memperbaiki beberapa penguraian dan pesan kesalahan (#3584)
* Memperbaiki penguraian `--resource-type` untuk perintah `lock` untuk menerima `<resource-namespace>` dan `<resource-type>`
* Menambahkan pemeriksaan parameter untuk templat tautan templat (#3629)
* Menambahkan dukungan untuk menentukan parameter penyebaran menggunakan sintaks `KEY=VALUE`

### <a name="role"></a>Peran

* Mendukung output dalam format file autentikasi SDK untuk `create-for-rbac`
* Membersihkan penetapan peran dan aplikasi Azure Active Directory terkait saat menghapus perwakilan layanan (#3610)
* Menyertakan format waktu dalam argumen `app create` `--start-date` dan deskripsi `--end-date`
* Menunjukkan peringatan penghentian saat menggunakan `--expanded-view`
* Menambahkan integrasi brankas kunci ke perintah `create-for-rbac` dan `reset-credentials`

### <a name="service-fabric"></a>Service Fabric
* Memperbaiki masalah dengan file besar dalam aplikasi yang terpotong saat diunggah (#3666)
* Menambahkan pengujian untuk perintah Service Fabric (#3424)
* Memperbaiki banyak perintah Service Fabric (#3234)

### <a name="sql"></a>SQL

* Menghapus parameter `sql server create` `--identity` yang rusak
* Menghapus nilai kata sandi dari output perintah `sql server create` dan `sql server update`
* Menambahkan perintah `sql db list-editions` dan `sql elastic-pool list-editions`

### <a name="storage"></a>Penyimpanan

* Menghapus opsi `--marker` dari perintah `storage blob list`, `storage container list`, dan `storage share list` (#3745)
* Mengaktifkan membuat akun penyimpanan khusus https
* Memperbarui metrik penyimpanan, pengelogan, dan perintah cors (#3495)
* Menyusun ulang pesan pengecualian dari penambahan CORS (#3638) (#3362)
* Mengonversi generator menjadi daftar dalam mode eksekusi kering perintah batch pengunduhan (#3592)
* Memperbaiki masalah dryrun batch pengunduhan blob (#3640) (#3592)

### <a name="vm"></a>VM

* Mendukung mengonfigurasi nsg
* Memperbaiki bug saat server DNS tidak dikonfigurasi dengan benar
* Mendukung identitas layanan terkelola
* Memperbaiki masalah saat `cmss create` dengan penyeimbang beban yang ada diperlukan `--backend-pool-name`
* Membuat datadisk yang dibuat dengan lun `vm image create` mulai dengan 0


## <a name="may-10-2017"></a>10 Mei 2017

Versi 2.0.6

* documentdb berganti nama menjadi cosmosdb
* Menambahkan rdbms (mysql, postgres)
* Menyertakan modul Data Lake Analytics dan Data Lake Store
* Menyertakan modul Cognitive Services
* Menyertakan modul Service Fabric
* Menyertakan modul Interaktif (mengganti nama az-shell)
* Menambahkan dukungan untuk perintah CDN
* Menghapus modul Kontainer
* Menambahkan 'az -v' sebagai pintasan untuk 'az --version' ([#2926](https://github.com/Azure/azure-cli/issues/2926))
* Meningkatkan performa pemuatan paket dan eksekusi perintah ([#2819](https://github.com/Azure/azure-cli/issues/2819))

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
* perf: mempertahankan cache token adal di memori hingga proses keluar ([#2603](https://github.com/Azure/azure-cli/issues/2603))
* Memperbaiki byte yang dikembalikan dari sidik jari hex -o tsv ([#3053](https://github.com/Azure/azure-cli/issues/3053))
* Meningkatkan Pengunduhan Sertifikat Key Vault dan Integrasi SP Azure Active Directory ([#3003](https://github.com/Azure/azure-cli/issues/3003))
* Menambahkan lokasi Python ke ‘az —version’ ([#2986](https://github.com/Azure/azure-cli/issues/2986))
* masuk: mendukung masuk saat tidak ada langganan ([#2929](https://github.com/Azure/azure-cli/issues/2929))
* inti: memperbaiki kegagalan saat masuk menggunakan perwakilan layanan dua kali ([#2800](https://github.com/Azure/azure-cli/issues/2800))
* inti: Mengizinkan jalur file accessTokens.json agar dapat dikonfigurasi melalui env var ([#2605](https://github.com/Azure/azure-cli/issues/2605))
* inti: Mengizinkan default yang dikonfigurasi untuk diterapkan pada argumen opsional ([#2703](https://github.com/Azure/azure-cli/issues/2703))
* inti: Meningkatkan performa
* inti: Sertifikat OS Kustom - Mendukung pengaturan variabel lingkungan REQUESTS_CA_BUNDLE
* inti: Konfigurasi cloud - gunakan titik akhir 'manajer sumber daya' jika titik akhir 'manajemen' tidak diatur

### <a name="acs"></a>ACS

* memperbaiki jumlah master dan agen menjadi bilangan bulat, bukan string
* memperlihatkan 'az acs create --no-wait' dan 'az acs wait' untuk pembuatan asinkron
* memperlihatkan 'az acs create --validate' untuk validasi dry-run
* menghapus profil windows sebelum panggilan PUT untuk perintah skala ([#2755](https://github.com/Azure/azure-cli/issues/2755))

### <a name="appservice"></a>AppService

* functionapp: menambahkan dukungan functionapp penuh, termasuk membuat, menampilkan, mencantumkan, menghapus, nama host, ssl, dll
* Menambahkan Layanan Tim (vsts) sebagai opsi pengiriman berkelanjutan ke "konfigurasi kontrol sumber web appservice"
* Membuat "az webapp" untuk menggantikan "az appservice web" (untuk kompatibilitas mundur, "az appservice web" akan tetap ada selama 2 rilis)
* Memperlihatkan argumen untuk mengonfigurasi penyebaran dan "tumpukan runtime" pada pembuatan webapp
* Memperlihatkan "runtime daftar webapp"
* mendukung dalam mengonfigurasi string koneksi ([#2647](https://github.com/Azure/azure-cli/issues/2647))
* mendukung pertukaran slot dengan pratinjau
* Memperbaiki kesalahan dari perintah appservice ([#2948](https://github.com/Azure/azure-cli/issues/2948))
* Menggunakan grup sumber daya paket layanan aplikasi untuk operasi sertifikat ([#2750](https://github.com/Azure/azure-cli/issues/2750))

### <a name="cosmosdb"></a>CosmosDB

* Mengganti nama modul documentdb menjadi cosmosdb
* Menambahkan dukungan untuk API data-plane documentdb: manajemen database dan kumpulan
* Menambahkan dukungan untuk mengaktifkan failover otomatis pada akun database
* Menambahkan dukungan untuk ConsistentPrefix kebijakan konsistensi baru

### <a name="data-lake-analytics"></a>Data Lake Analytics

* Memperbaiki bug saat pemfilteran pada hasil dan status untuk daftar pekerjaan akan menimbulkan kesalahan
* Menambahkan dukungan untuk tipe item katalog baru: paket. diakses melalui: `az dla catalog package`
* Memungkinkan untuk mencantumkan item katalog berikut dari dalam database (tidak diperlukan spesifikasi skema):

  * Tabel
  * Fungsi bernilai tabel
  * Tampilan
  * Statistik Tabel. Ini juga dapat dicantumkan dengan skema, tetapi tanpa menentukan nama tabel

### <a name="data-lake-store"></a>Data Lake Store

* Memperbarui versi SDK filesystem yang mendasari, yang memberikan dukungan lebih baik untuk menangani skenario pembatasan sisi server
* Meningkatkan performa pemuatan paket dan eksekusi perintah ([#2819](https://github.com/Azure/azure-cli/issues/2819))
* bantuan yang tidak ada untuk tampilan akses. menambahkan bantuan. ([#2743](https://github.com/Azure/azure-cli/issues/2743))

### <a name="find"></a>Cari

* meningkatkan hasil pencarian dan memungkinkan untuk menerapkan versi indeks pencarian

### <a name="keyvault"></a>Az.KeyVault

* BC:`az keyvault certificate download` mengubah -e dari string atau biner ke PEM atau DER untuk lebih mewakili opsi
* BC: Menghapus --expires dan --not-before dari `keyvault certificate create` karena parameter ini tidak didukung oleh layanan
* Menambahkan parameter --validity ke `keyvault certificate create` untuk secara selektif menimpa nilai di --policy
* Memperbaiki masalah di `keyvault certificate get-default-policy` saat 'kedaluwarsa' dan 'not_before' diperlihatkan tetapi 'validity_in_months' tidak
* perbaikan keyvault untuk impor pem dan pfx ([#2754](https://github.com/Azure/azure-cli/issues/2754))

### <a name="lab"></a>Laboratorium

* Menambahkan perintah buat, tampilkan, hapus & catat untuk lingkungan di lab
* Menambahkan perintah tampilkan & catat untuk melihat templat Azure Resource Manager di lab
* Menambahkan bendera --environment di `az lab vm list` untuk memfilter Mesin Virtual berdasarkan lingkungan di lab
* Menambahkan perintah praktis `az lab formula export-artifacts` untuk mengekspor perancah artefak dalam rumus Lab
* Menambahkan perintah untuk mengelola rahasia di dalam Lab

### <a name="monitor"></a>Monitor

* Perbaikan Bug: Membuat model `--actions` dari `az alert-rules create` untuk menggunakan string JSON ([#3009](https://github.com/Azure/azure-cli/issues/3009))
* Perbaikan bug - pembuatan pengaturan diagnostik tidak menerima log/metrik dari perintah tampilkan ([#2913](https://github.com/Azure/azure-cli/issues/2913))

### <a name="network"></a>Jaringan

* Menambahkan perintah `network watcher test-connectivity`
* Menambahkan dukungan untuk parameter `--filters` untuk `network watcher packet-capture create`
* Menambahkan dukungan untuk pengosongan koneksi Application Gateway
* Menambahkan dukungan untuk konfigurasi seperangkat aturan WAF Application Gateway
* Menambahkan dukungan untuk filter dan aturan rute ExpressRoute
* Menambahkan dukungan untuk perutean geografis TrafficManager
* Menambahkan dukungan untuk pemilih lalu lintas berbasis kebijakan koneksi VPN
* Menambahkan dukungan untuk kebijakan IPSec koneksi VPN
* Memperbaiki bug dengan `vpn-connection create` saat menggunakan parameter `--no-wait` atau `--validate`
* Menambahkan dukungan untuk gateway VNet aktif-aktif
* Menghapus nilai null dari output perintah `network vpn-connection list/show`
* BC: Memperbaiki bug pada output `vpn-connection create`
* Memperbaiki bug saat argumen '--key-length' dari 'vpn-connection create' tidak diuraikan dengan benar
* Memperbaiki bug di `dns zone import` saat catatan tidak diimpor dengan benar
* Memperbaiki bug saat `traffic-manager endpoint update` tidak berfungsi
* Menambahkan perintah pratinjau 'network watcher'

### <a name="profile"></a>Profil

* Mendukung masuk saat tidak ada langganan yang ditemukan ([#2560](https://github.com/Azure/azure-cli/issues/2560))
* Mendukung nama param pendek di kumpulan akun az --subscription ([#2980](https://github.com/Azure/azure-cli/issues/2980))

### <a name="redis"></a>Redis

* Menambahkan perintah pembaruan yang juga menambahkan kemampuan untuk menskalakan redis cache
* Menghentikan perintah 'update-settings'

### <a name="resource"></a>Sumber daya

* Menambahkan perintah definisi managedapp dan managedapp ([#2985](https://github.com/Azure/azure-cli/issues/2985))
* Mendukung perintah 'provider operation' ([#2908](https://github.com/Azure/azure-cli/issues/2908))
* Mendukung pembuatan sumber daya umum ([#2606](https://github.com/Azure/azure-cli/issues/2606))
* Memperbaiki penguraian sumber daya dan pencarian versi api. ([#2781](https://github.com/Azure/azure-cli/issues/2781))
* Menambahkan dokumen untuk pembaruan kunci az. ([#2702](https://github.com/Azure/azure-cli/issues/2702))
* Kesalahan terjadi jika Anda mencoba mencantumkan sumber daya untuk grup yang tidak ada. ([#2769](https://github.com/Azure/azure-cli/issues/2769))
* [Compute] Perbaiki masalah dengan pembaruan kumpulan ketersediaan Virtual Machine Scale Sets dan Mesin Virtual. ([#2773](https://github.com/Azure/azure-cli/issues/2773))
* Memperbaiki pembuatan dan penghapusan kunci jika parent-resource-path adalah Tidak Ada ([#2742](https://github.com/Azure/azure-cli/issues/2742))

### <a name="role"></a>Peran

* create-for-rbac: memastikan tanggal selesai SP tidak melebihi kedaluwarsa sertifikat ([#2989](https://github.com/Azure/azure-cli/issues/2989))
* Kontrol akses berbasis peran: menambahkan dukungan penuh untuk 'grup iklan' ([#2016](https://github.com/Azure/azure-cli/issues/2016))
* peran: memperbaiki masalah pada pembaruan definisi peran ([#2745](https://github.com/Azure/azure-cli/issues/2745))
* create-for-rbac: memastikan kata sandi yang diberikan pengguna diambil

### <a name="sql"></a>SQL

* Menambahkan perintah az sql server list-usages dan az sql server list-usages
* SQL - kemampuan untuk terhubung langsung ke penyedia sumber ([#2832](https://github.com/Azure/azure-cli/issues/2832))

### <a name="storage"></a>Penyimpanan

* Lokasi default ke lokasi grup sumber daya untuk `storage account create`
* Menambahkan dukungan untuk salinan blob tambahan
* Menambahkan dukungan untuk pengunggahan blob blok besar
* Mengubah ukuran blok menjadi 100MB saat file yang akan diunggah lebih besar dari 200GB

### <a name="vm"></a>VM

* avail-set: menjadikan jumlah domain UD&FD opsional

  catatan: Perintah Mesin Virtual di sovereign cloud Hindari fitur terkait disk terkelola, termasuk yang berikut:
  1. az disk/snapshot/image
  2. az vm/vmss disk
  3. Di dalam "az vm/vmss create", gunakan "—use-unmanaged-disk" untuk menghindari disk yang dikelola Perintah lain seharusnya berfungsi
* vm/vmss: memperbaiki teks peringatan saat menghasilkan pasangan kunci ssh
* vm/vmss: mendukung pembuatan dari gambar marketplace yang memerlukan info paket ([#1209](https://github.com/Azure/azure-cli/issues/1209))


## <a name="april-3-2017"></a>3-Apr-17

Versi 2.0.2

Kami merilis komponen Azure Container Registry, Batch, KeyVault, dan SQL dalam rilis ini

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
* Masuk: melewati penyewa yang salah ([#2634](https://github.com/Azure/azure-cli/pull/2634))
* masuk: mengatur langganan default ke langganan dengan status "Diaktifkan" ([#2575](https://github.com/Azure/azure-cli/pull/2575))
* Menambahkan perintah tunggu dan --no-wait mendukung ke lebih banyak perintah ([#2524](https://github.com/Azure/azure-cli/pull/2524))
* inti: mendukung masuk dengan menggunakan perwakilan layanan dengan sertifikat ([#2457](https://github.com/Azure/azure-cli/pull/2457))
* Menambahkan perintah untuk parameter templat yang hilang. ([#2364](https://github.com/Azure/azure-cli/pull/2364))
* Mendukung pengaturan nilai default untuk argumen umum seperti grup sumber daya default, web default, mesin virtual default
* Menddukungan masuk ke penyewa tertentu

### <a name="acs"></a>ACS

* [ACS] Menambahkan dukungan untuk mengonfigurasi kluster Access Control default ([#2554](https://github.com/Azure/azure-cli/pull/2554))
* Menambahkan dukungan untuk perintah kata sandi kunci ssh. ([#2044](https://github.com/Azure/azure-cli/pull/2044))
* Tambahkan dukungan untuk kluster windows. ([#2211](https://github.com/Azure/azure-cli/pull/2211))
* Beralih dari peran Pemilik ke Kontributor. ([#2321](https://github.com/Azure/azure-cli/pull/2321))

### <a name="appservice"></a>AppService

* appservice: mendukung untuk mendapatkan alamat ip eksternal yang digunakan untuk catatan DNS A ([#2627](https://github.com/Azure/azure-cli/pull/2627))
* appservice: mendukung mengikat sertifikat kartubebas ([#2625](https://github.com/Azure/azure-cli/pull/2625))
* appservice: mendukung profil penerbitan daftar ([#2504](https://github.com/Azure/azure-cli/pull/2504))
* AppService - Memicu sinkronisasi kontrol sumber setelah konfigurasi ([#2326](https://github.com/Azure/azure-cli/pull/2326))

### <a name="datalake"></a>DataLake

* Rilis awal modul Data Lake Analytics
* Rilis awal modul Data Lake Store

### <a name="docuemntdb"></a>DocuemntDB

* DocumentDB: Menambahkan dukungan untuk mencantumkan string koneksi ([#2580](https://github.com/Azure/azure-cli/pull/2580))

### <a name="vm"></a>VM

* [Compute] Menambahkan dukungan AppGateway ke pembuatan virtual machine scale set ([#2570](https://github.com/Azure/azure-cli/pull/2570))
* [VM/VMSS] Meningkatkan dukungan penembolokan disk ([#2522](https://github.com/Azure/azure-cli/pull/2522))
* VM/VMSS: menggabungkan logika validasi kredensial yang digunakan oleh portal ([#2537](https://github.com/Azure/azure-cli/pull/2537))
* Menambahkan perintah tunggu dan --no-wait support ([#2524](https://github.com/Azure/azure-cli/pull/2524))
* Virtual machine scale set: mendukung * untuk mencantumkan tampilan instans di seluruh vms ([#2467](https://github.com/Azure/azure-cli/pull/2467))
* Menambahkan --secrets untuk Mesin Virtual dan virtual machine scale set ([#2212}(<https://github.com/Azure/azure-cli/pull/2212>))
* Mengizinkan pembuatan Mesin Virtual dengan VHD khusus ([#2256](https://github.com/Azure/azure-cli/pull/2256))

## <a name="february-27-2017"></a>27 Februari 2017

Versi 2.0.0

Rilis Azure CLI 2.0 ini adalah rilis "Tersedia Secara Umum" pertama Ketersediaan umum berlaku untuk modul perintah ini:
- Layanan Kontainer (ac)
- Komputasi (termasuk Azure Resource Manager, Mesin Virtual, virtual machine scale sets, Disk Terkelola)
- Jaringan
- Penyimpanan

Modul perintah ini dapat digunakan dalam produksi dan didukung oleh SLA Microsoft standar Anda dapat membuka masalah secara langsung dengan dukungan Microsoft atau di [daftar masalah github](https://github.com/azure/azure-cli/issues/) kami Anda dapat mengajukan pertanyaan di [StackOverflow menggunakan tag Azure-cli ](http://stackoverflow.com/questions/tagged/azure-cli), atau hubungi tim produk di [azfeedback@microsoft.com](mailto:azfeedback@microsoft.com) Anda dapat memberikan umpan balik dari baris perintah dengan perintah `az feedback`

Perintah dalam modul ini stabil dan sintaks diharapkan tidak berubah dalam rilis mendatang dari versi Azure CLI ini

Untuk memverifikasi versi CLI, gunakan `az --version` Output mencantumkan versi CLI itu sendiri (2.0.0 dalam rilis ini), masing-masing modul perintah, dan versi Python dan GCC yang Anda gunakan

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
> Beberapa modul perintah memiliki postfix "b *n*" atau "rc *n*" Modul perintah ini masih dalam pratinjau dan akan tersedia secara umum di masa mendatang

Kami juga memiliki build pratinjau setiap malam dari CLI Untuk informasi, lihat instruksi ini tentang [mendapatkan build setiap malam](https://github.com/Azure/azure-cli#nightly-builds), dan instruksi ini tentang [penyiapan pengembang dan kode kontribusi](https://github.com/Azure/azure-cli#developer-setup)

Anda dapat melaporkan masalah dengan build pratinjau setiap malam dengan cara berikut:
- Melaporkan masalah di [daftar masalah github](https://github.com/azure/azure-cli/issues/) kami
- Menghubungi tim produk di [azfeedback@microsoft.com](mailto:azfeedback@microsoft.com)
- Memberikan umpan balik dari baris perintah dengan perintah `az feedback`
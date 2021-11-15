---
title: Azure CLI references for Azure Storage | Microsoft Docs
description: Cari perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure Storage.  Ikuti tautan ke artikel populer untuk mempelajari cara menggunakan Azure CLI untuk Azure Storage.
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli references, azure storage, azure storage sync, azure import-export
ms.openlocfilehash: c77fd9cd06c6824c36ba962ad43255490a706696
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439083"
---
# <a name="azure-cli-reference-commands-for-azure-storage"></a>Azure CLI reference commands for Azure Storage

Azure Command-Line Interface[(CLI)](./what-is-azure-cli.md)adalah seperangkat perintah yang Anda gunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di banyak layanan Azure, termasuk Azure Storage, dan memberi Anda kemampuan untuk mengelola Azure Storage dari baris perintah.

Perintah Azure CLI untuk [Azure Storage](/azure/storage) terdiri dari dua bagian: **inti** dan **ekstensinya.** Inti Azure CLI perintah kapal sebagai bagian dari CLI dan didukung penuh. Ekstensi memberi Anda akses ke perintah eksperimental dan pra-rilis. Untuk informasi selengkapnya tentang menggunakan ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).  

Lihat [penyimpanan az](/cli/azure/service-page/azure%20storage) untuk daftar abjad referensi inti dan ekstensi Azure CLI yang tersedia untuk layanan Azure Storage. Untuk referensi untuk setiap subkelompok, lihat tabel di bagian berikut:

- [Azure File Sync](#azure-file-sync-references)
- [layanan Import/Export](#importexport-service-references)
- [Akun Penyimpanan](#storage-account-references)
- [gumpalan Storage](#storage-blob-references)
- [wadah Storage](#storage-container-references)
- [sistem berkas Storage](#storage-file-system-references)
- [Antrean Storage](#storage-queue-references)
- [Storage berbagi berkas](#storage-file-share-references)
- [Storage saham file (SMB 3.0)](#storage-file-share-smb-30-references)
- [Referensi penyimpanan tambahan](#additional-storage-references)

> [!NOTE]
> Anda diminta untuk menginstal referensi ekstensi pada penggunaan pertama. Atau, Anda dapat menggunakan perintah [tambahkan ekstensi az](/cli/azure/extension#az_extension_add) untuk menginstal ekstensi dengan nama secara manual.

## <a name="azure-file-sync-references"></a>Azure File Sync references

Referensi dalam tabel ini adalah bagian dari ekstensi [penyimpanansync.](https://github.com/Azure/azure-cli-extensions/tree/main/src/storagesync)

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az storagesync](/cli/azure/storagesync) | Mengelola layanan sinkronisasi penyimpanan. | [Menyebarkan Azure File Sync](/azure/storage/file-sync/file-sync-deployment-guide?tabs=azure-cli) |
| [az storagesync registered-server](/cli/azure/storagesync/registered-server) | Kelola server yang terdaftar dengan layanan sinkronisasi penyimpanan. |  |
| [az storagesync sync-group](/cli/azure/storagesync/sync-group) | Mengelola grup sinkronisasi dalam layanan sinkronisasi penyimpanan. | [Menyebarkan Azure File Sync](/azure/storage/file-sync/file-sync-deployment-guide?tabs=azure-cli) |
| [az storagesync sync-group cloud-endpoint](/cli/azure/storagesync/sync-group/cloud-endpoint) | Mengelola titik akhir cloud dalam grup sinkronisasi layanan sinkronisasi penyimpanan. | [Menyebarkan Azure File Sync](/azure/storage/file-sync/file-sync-deployment-guide?tabs=azure-cli) |
| [az storagesync sync-group server-endpoint](/cli/azure/storagesync/sync-group/server-endpoint) | Mengelola titik akhir server dalam grup sinkronisasi layanan sinkronisasi penyimpanan. | [Menyebarkan Azure File Sync](/azure/storage/file-sync/file-sync-deployment-guide?tabs=azure-cli) |

## <a name="importexport-service-references"></a>referensi layanan Import/Export

Referensi dalam tabel ini adalah bagian dari ekstensi [ekspor-impor.](https://github.com/Azure/azure-cli-extensions/tree/main/src/import-export)

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az import-export](/cli/azure/import-export) | Mengelola pekerjaan impor dan ekspor untuk layanan Azure Import/Export. | [Menggunakan layanan Impor/Ekspor Azure untuk mengimpor data ke Azure Files](/azure/import-export/storage-import-export-data-to-files?tabs=azure-cli) |
| [az import-export bit-locker-key](/cli/azure/import-export/bit-locker-key) | Cantumkan tombol BitLocker untuk pekerjaan impor atau ekspor. | |
| [az lokasi ekspor-impor](/cli/azure/import-export/location) | Tampilkan detail lokasi untuk pekerjaan impor atau ekspor. | [Menggunakan layanan Impor/Ekspor Azure untuk mengimpor data ke Azure Files](/azure/import-export/storage-import-export-data-to-files?tabs=azure-cli) |

## <a name="storage-account-references"></a>referensi akun Storage

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az storage account](/cli/azure/storage/account) | Mengelola akun penyimpanan. | [Buat akun penyimpanan](/azure/storage/common/storage-account-create?tabs=azure-cli) |
| [az storage account blob-inventory-policy](/cli/azure/storage/account/blob-inventory-policy) | Mengelola kebijakan inventaris akun penyimpanan. | [Mengaktifkan laporan inventaris blob Azure Storage](/azure/storage/blobs/blob-inventory-how-to?tabs=azure-cli) |
| [az storage account blob-service-properties](/cli/azure/storage/account/blob-service-properties) | Mengelola properti layanan Blob akun penyimpanan. | [Mengonfigurasikan replikasi objek untuk blob blok](/azure/storage/blobs/object-replication-configure?tabs=azure-cli) |
| [az storage account encryption-scope](/cli/azure/storage/account/encryption-scope) | Mengelola ruang lingkup enkripsi untuk akun penyimpanan. | [Membuat dan mengelola cakupan enkripsi](/azure/storage/blobs/encryption-scope-manage?tabs=cli) |
| [az storage account file-service-properties](/cli/azure/storage/account/file-service-properties) | Mengelola properti layanan Blob akun penyimpanan. | [Aktifkan penghapusan sementara di berbagi file Azure](/azure/storage/files/storage-files-enable-soft-delete?tabs=azure-cli) |
| [az kunci akun penyimpanan](/cli/azure/storage/account/keys) | Mengelola kunci akun penyimpanan. | [Mengelola kunci akses akun penyimpanan](/azure/storage/common/storage-account-keys-manage?tabs=azure-cli). |
| [az storage account management-policy](/cli/azure/storage/account/management-policy) | Mengelola kebijakan manajemen akun penyimpanan. |  |
| [az storage account network-rule](/cli/azure/storage/account/network-rule) | Mengelola aturan jaringan. | [Mengonfigurasi firewall dan jaringan virtual Azure Storage](/azure/storage/common/storage-network-security?tabs=azure-cli) |
| [az akun penyimpanan atau-kebijakan](/cli/azure/storage/account/or-policy) | Mengelola kebijakan replikasi objek akun penyimpanan. | [Mengonfigurasikan replikasi objek untuk blob blok](/azure/storage/blobs/object-replication-configure?tabs=azure-cli) |
| [az akun penyimpanan atau aturan kebijakan](/cli/azure/storage/account/or-policy/rule) | Mengelola aturan Kebijakan Replikasi Objek dari akun penyimpanan. | [Mengonfigurasikan replikasi objek untuk blob blok](/azure/storage/blobs/object-replication-configure?tabs=azure-cli) |
| [az storage account private-endpoint-connection](/cli/azure/storage/account/private-endpoint-connection) | Mengelola koneksi endpoint pribadi akun penyimpanan. | |
| [az storage account private-link-resource](/cli/azure/storage/account/private-link-resource) | Mengelola sumber daya tautan pribadi akun penyimpanan. | |

## <a name="storage-blob-references"></a>Storage referensi gumpalan

Beberapa referensi dalam tabel ini adalah bagian dari ekstensi [pratinjau penyimpanan](https://github.com/Azure/azure-cli-extensions/tree/main/src/storage-preview) atau [penyimpanan-gumpalan-pratinjau.](https://github.com/Azure/azure-cli-extensions/tree/main/src/storage-blob-preview)

| Referensi | Deskripsi | Ekstensi? | Informasi selengkapnya |
|-|-|-|-|
| [az storage blob](/cli/azure/storage/blob) | Mengelola penyimpanan objek untuk data tidak terstruktur (gumpalan). | | [Mulai cepat: Membuat, mengunduh, dan mencantumkan blob dengan CLI Azure](/azure/storage/blobs/storage-quickstart-blobs-cli) |
| [az storage blob access](/cli/azure/storage/blob/access) | Mengelola properti kontrol akses dari gumpalan saat Hierarchical Namespace diaktifkan. | pratinjau penyimpanan |  |
| [az storage blob copy](/cli/azure/storage/blob/copy) | Mengelola operasi salinan gumpalan. | | [Pindahkan blob penyimpanan Azure dari baris perintah dengan Azure CLI](/learn/modules/copy-blobs-from-command-line-and-code/4-exercise-move-blobs-using-cli) |
| [az storage blob directory](/cli/azure/storage/blob/directory) | Kelola direktori gumpalan dalam wadah akun penyimpanan. | pratinjau penyimpanan |  |
| [az storage blob directory access](/cli/azure/storage/blob/directory/access) | Mengelola properti kontrol akses dari direktori saat Hierarchical Namespace diaktifkan. | pratinjau penyimpanan | |
| [az storage blob directory metadata](/cli/azure/storage/blob/directory/metadata) | Mengelola metadata direktori. | pratinjau penyimpanan |  |
| [az storage blob incremental-copy](/cli/azure/storage/blob/incremental-copy) | Mengelola operasi salinan inkremental gumpalan. | | |
| [az storage blob lease](/cli/azure/storage/blob/lease) | Mengelola sewa gumpalan penyimpanan. | |  |
| [az storage blob metadata](/cli/azure/storage/blob/metadata) | Mengelola metadata gumpalan. | | [Menampilkan properti blob dan metadata menggunakan alat dan kode Azure](/learn/modules/organize-blobs-properties-metadata/3-view-blob-properties-and-metadata-using-azure-tools-and-code) |
| [az storage blob service-properties](/cli/azure/storage/blob/service-properties) | Mengelola properti layanan gumpalan penyimpanan. | | [Menerapkan situs web statis ke penyimpanan blob](/learn/modules/create-cdn-static-resources-blob-storage/1b-exercise-deploy-a-website) |
| [az storage blob service-properties delete-policy](/cli/azure/storage/blob/service-properties/delete-policy) | Mengelola properti layanan penghapusan-kebijakan gumpalan penyimpanan. | |  |
| [az storage blob tag](/cli/azure/storage/blob/tag) | Mengelola tag gumpalan penyimpanan. | storage-blob-preview | |

## <a name="storage-container-references"></a>referensi kontainer Storage

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az storage container](/cli/azure/storage/container) | Mengelola wadah penyimpanan gumpalan. | [Tutorial: Mengunggah data gambar di cloud dengan Azure Storage](/azure/storage/blobs/storage-upload-process-images?tabs=dotnet%2Cazure-cli) |
| [az storage container immutability-policy](/cli/azure/storage/container/immutability-policy) | Mengelola kebijakan immutability kontainer. | [Mengonfigurasi kebijakan imutabilitas untuk kontainer](/azure/storage/blobs/immutable-policy-configure-container-scope?tabs=azure-cli) |
| [az storage container lease](/cli/azure/storage/container/lease) | Mengelola sewa kontainer penyimpanan gumpalan. | |
| [az storage container legal-hold](/cli/azure/storage/container/legal-hold) | Mengelola kontainer legal hold. | |
| [az storage container metadata](/cli/azure/storage/container/metadata) | Mengelola metadata kontainer. | [Melihat properti dan metadata gumpalan menggunakan alat dan kode azure](/learn/modules/organize-blobs-properties-metadata/3-view-blob-properties-and-metadata-using-azure-tools-and-code) |
| [az storage container policy](/cli/azure/storage/container/policy) | Mengelola kebijakan akses yang disimpan kontainer. | [Menggunakan Tanda Tangan Akses Bersama penyimpanan Azure Blob untuk membatasi akses ke data di HDInsight](/azure/hdinsight/hdinsight-storage-sharedaccesssignature-permissions) |

## <a name="storage-file-share-references"></a>Storage referensi berbagi file

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az storage share](/cli/azure/storage/share) | Mengelola berbagi file penyimpanan. | [Mulai cepat: Buat dan kelola berbagi file Azure menggunakan Azure CLI](/azure/storage/files/storage-how-to-use-files-cli) |
| [az storage share metadata](/cli/azure/storage/share/metadata) | Mengelola metadata berbagi file. | |
| [az storage share policy](/cli/azure/storage/share/policy) | Mengelola kebijakan akses bersama dari berbagi file. |  |

## <a name="storage-file-share-smb-30-references"></a>Storage referensi berbagi file (SMB 3.0)

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az storage file](/cli/azure/storage/file) | Kelola berbagi file penyimpanan yang menggunakan protokol Server Message Block (SMB) 3.0. | [Mulai cepat: Buat dan kelola berbagi file Azure menggunakan Azure CLI](/azure/storage/files/storage-how-to-use-files-cli) |
| [az storage file copy](/cli/azure/storage/file/copy) | Mengelola operasi salinan file dari file share. | |
| [az metadata file penyimpanan](/cli/azure/storage/file/metadata) | Mengelola metadata berbagi file. | |

## <a name="storage-file-system-references"></a>Storage referensi sistem berkas

Beberapa referensi dalam tabel ini adalah bagian dari ekstensi [pratinjau penyimpanan.](https://github.com/Azure/azure-cli-extensions/tree/main/src/storage-preview)

| Referensi | Deskripsi | Ekstensi? | Informasi selengkapnya |
|-|-|-|-|
| [az storage fs](/cli/azure/storage/fs) | Kelola sistem file di akun Azure Data Lake Storage Gen2. | | [Gunakan Azure CLI untuk mengelola direktori dan file di Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-directory-file-acl-cli) |
| [az storage fs access](/cli/azure/storage/fs/access) | Mengelola akses sistem file dan izin untuk akun Azure Data Lake Storage Gen2. | | [Gunakan Azure CLI untuk mengelola ACL di Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-acl-cli) |
| [az storage fs directory](/cli/azure/storage/fs/directory) | Mengelola direktori di akun Azure Data Lake Storage Gen2. | | [Gunakan Azure CLI untuk mengelola direktori dan file di Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-directory-file-acl-cli) |
| [az storage fs directory metadata](/cli/azure/storage/fs/directory/metadata) | Mengelola metadata untuk direktori dalam sistem file. | |  |
| [az storage fs file](/cli/azure/storage/fs/file) | Mengelola file di akun Azure Data Lake Storage Gen2. | | [Gunakan Azure CLI untuk mengelola direktori dan file di Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-directory-file-acl-cli) |
| [az storage fs file metadata](/cli/azure/storage/fs/file/metadata) | Mengelola metadata untuk file dalam sistem file. | | |
| [az storage fs metadata](/cli/azure/storage/fs/metadata) | Mengelola metadata untuk sistem file. | | |
| [az storage fs service-properties](/cli/azure/storage/fs/service-properties) | Mengelola properti layanan Azure Data Lake Storage Gen2 akun penyimpanan. | pratinjau penyimpanan |  |

## <a name="storage-queue-references"></a>referensi antrian Storage

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az antrian penyimpanan](/cli/azure/storage/queue) | Mengelola antrian penyimpanan. | [Pilih cara mengotorisasi akses untuk data antrean dengan Azure CLI](/azure/storage/queues/authorize-data-operations-cli) |
| [az metadata antrian penyimpanan](/cli/azure/storage/queue/metadata) | Mengelola metadata untuk antrian penyimpanan. | |
| [az kebijakan antrian penyimpanan](/cli/azure/storage/queue/policy) | Mengelola kebijakan akses bersama untuk antrian penyimpanan. | |

## <a name="additional-storage-references"></a>Referensi penyimpanan tambahan

Beberapa referensi dalam tabel ini adalah bagian dari ekstensi [pratinjau penyimpanan.](https://github.com/Azure/azure-cli-extensions/tree/main/src/storage-preview)

| Referensi | Deskripsi | Ekstensi? | Informasi selengkapnya |
|-|-|-|-|
| [az snapshot](/cli/azure/snapshot) | Mengelola salinan point-in-time dari disk terkelola, gumpalan asli, atau snapshot lainnya. | | [Membuat rekam jepret menggunakan portal atau Azure CLI](/azure/virtual-machines/linux/snapshot-copy-managed-disk) |
| [az storage azcopy](/cli/azure/storage/azcopy) | Mengelola operasi penyimpanan dengan `AzCopy` utilitas. | pratinjau penyimpanan |  |
| [az storage azcopy blob](/cli/azure/storage/azcopy/blob) | Mengelola penyimpanan objek untuk gumpalan dengan `AzCopy` utilitas. | pratinjau penyimpanan | [Menyalin file audio](/learn/modules/intro-to-batch-transcription/3-exercise-transcribe-audio-files) |
| [az storage container-rm](/cli/azure/storage/container-rm) | Kelola kontainer Azure menggunakan `Microsoft.Storage` penyedia sumber daya. | | |
| [az storage cors](/cli/azure/storage/cors) | Mengelola layanan penyimpanan Cross-Origin Resource Sharing (CORS). | | [Aktifkan CORS untuk Layanan Azure Storage Anda menggunakan Azure CLI](/learn/modules/set-up-cors-website-storage/5-enabling-cors-for-your-azure-storage-services-using-the-azure-cli) |
| [az storage directory](/cli/azure/storage/directory) | Mengelola direktori penyimpanan file. | | [Mulai cepat: Buat dan kelola berbagi file Azure menggunakan Azure CLI](/azure/storage/files/storage-how-to-use-files-cli) |
| [az metadata direktori penyimpanan](/cli/azure/storage/directory/metadata) | Mengelola metadata direktori penyimpanan file. | | |
| [az storage entity](/cli/azure/storage/entity) | Mengelola entitas penyimpanan tabel. | | |
| [az storage logging](/cli/azure/storage/logging) | Mengelola informasi pencatatan layanan penyimpanan. | | |
| [az storage message](/cli/azure/storage/message) | Mengelola pesan penyimpanan antrian. | | |
| [az storage metrics](/cli/azure/storage/metrics) | Mengelola metrik layanan penyimpanan. | | |
| [az storage share-rm](/cli/azure/storage/share-rm) | Kelola berbagi file Azure dengan `Microsoft.Storage` penyedia sumber daya. | | [Cara membuat NFS berbagi](/azure/storage/files/storage-files-how-to-create-nfs-shares?tabs=azure-cli) |
| [az storage table](/cli/azure/storage/table) | Kelola penyimpanan nilai kunci NoSQL. | | [Menyiapkan aplikasi fungsi di Azure Functions](/learn/modules/send-crop-weather-alerts/6-deploy-azure-function-app) |
| [az storage table policy](/cli/azure/storage/table/policy) | Mengelola kebijakan akses bersama dari tabel penyimpanan. | | |

## <a name="see-also"></a>Lihat juga

- [Mulai dengan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari tentang instalasi dan masuk.

- Temukan [referensi](/cli/azure/reference-index) tambahan dan ekstensi yang [tersedia](./azure-cli-extensions-list.md) dalam dokumentasi Azure CLI.

- Pelajari selengkapnya tentang ekstensi di [Gunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

---
title: Referensi Azure CLI untuk Azure Storage | Microsoft Docs
description: Temukan perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure Storage.  Ikuti tautan ke artikel populer untuk mempelajari cara menggunakan Azure CLI untuk Azure Storage.
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure cli, azure storage, azure storage sync, azure import-export
ms.openlocfilehash: 4e6d2faa8c23b4f8fa82da85f79023c3d05f2e31
ms.sourcegitcommit: 4293ab0b6b4c04df8018d6dfd999db69b1becdd5
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/13/2022
ms.locfileid: "144976933"
---
# <a name="azure-cli-reference-commands-for-azure-storage"></a>Perintah referensi Azure CLI untuk Azure Storage

Azure Command-Line Interface ([CLI](./what-is-azure-cli.md)) adalah sekumpulan perintah yang digunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di banyak layanan Azure, termasuk Azure Storage, yang memungkinkan Anda mengelola Azure Storage dari baris perintah.

Perintah Azure CLI untuk [Azure Storage](/azure/storage) terdiri dari dua bagian: **inti** dan **ekstensi** nya. Perintah Azure CLI inti dikirimkan sebagai bagian dari CLI dan didukung sepenuhnya. Ekstensi memberi Anda akses ke perintah percobaan dan pra-rilis. Untuk informasi selengkapnya tentang penggunaan ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).  

Lihat [az storage](/cli/azure/service-page/azure%20storage) untuk mengetahui daftar alfabetik referensi inti dan ekstensi Azure CLI yang tersedia untuk layanan Azure Storage. Untuk referensi setiap sub-grup, lihat tabel di bagian berikut:

- [Azure File Sync](#azure-file-sync-references)
- [Layanan Import/Export](#importexport-service-references)
- [Akun penyimpanan](#storage-account-references)
- [Blob Storage](#storage-blob-references)
- [Kontainer Storage](#storage-container-references)
- [Sistem file Storage](#storage-file-system-references)
- [Antrean Storage](#storage-queue-references)
- [Berbagi Storage](#storage-file-share-references)
- [Berbagi Storage (SMB 3.0)](#storage-file-share-smb-30-references)
- [Referensi penyimpanan lainnya](#additional-storage-references)

> [!NOTE]
> Anda diminta menginstal referensi ekstensi saat digunakan pertama kali. Sebagai alternatif, Anda dapat menggunakan perintah [az extension add](/cli/azure/extension#az_extension_add) untuk menginstal ekstensi secara manual berdasarkan nama.

## <a name="azure-file-sync-references"></a>Referensi Sinkronisasi File Azure

Beberapa referensi dalam tabel ini adalah bagian dari ekstensi [storagesync](https://github.com/Azure/azure-cli-extensions/tree/main/src/storagesync).

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az storagesync](../latest/docs-ref-autogen/storagesync.yml) | Mengelola layanan sinkronisasi penyimpanan. | [Menyebarkan Azure File Sync](/azure/storage/file-sync/file-sync-deployment-guide?tabs=azure-cli) |
| [az storagesync registered-server](../latest/docs-ref-autogen/storagesync/registered-server.yml) | Mengelola server yang terdaftar dengan layanan sinkronisasi penyimpanan. |  |
| [az storagesync sync-group](../latest/docs-ref-autogen/storagesync/sync-group.yml) | Mengelola grup sinkronisasi dalam layanan sinkronisasi penyimpanan. | [Menyebarkan Azure File Sync](/azure/storage/file-sync/file-sync-deployment-guide?tabs=azure-cli) |
| [az storagesync sync-group cloud-endpoint](../latest/docs-ref-autogen/storagesync/sync-group/cloud-endpoint.yml) | Mengelola titik akhir cloud dalam grup sinkronisasi layanan sinkronisasi penyimpanan. | [Menyebarkan Azure File Sync](/azure/storage/file-sync/file-sync-deployment-guide?tabs=azure-cli) |
| [az storagesync sync-group server-endpoint](../latest/docs-ref-autogen/storagesync/sync-group/server-endpoint.yml) | Mengelola titik akhir server dalam grup sinkronisasi layanan sinkronisasi penyimpanan. | [Menyebarkan Azure File Sync](/azure/storage/file-sync/file-sync-deployment-guide?tabs=azure-cli) |

## <a name="importexport-service-references"></a>Referensi layanan Import/Export

Beberapa referensi dalam tabel ini adalah bagian dari ekstensi [import-export](https://github.com/Azure/azure-cli-extensions/tree/main/src/import-export).

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az import-export](../latest/docs-ref-autogen/import-export.yml) | Mengelola pekerjaan impor dan ekspor untuk layanan Azure Import/Export. | [Menggunakan layanan Impor/Ekspor Azure untuk mengimpor data ke Azure Files](/azure/import-export/storage-import-export-data-to-files?tabs=azure-cli) |
| [az import-export bit-locker-key](../latest/docs-ref-autogen/import-export/bit-locker-key.yml) | Mencantumkan kunci BitLocker untuk pekerjaan impor atau ekspor. | |
| [az import-export location](../latest/docs-ref-autogen/import-export/location.yml) | Menampilkan detail lokasi pekerjaan impor atau ekspor. | [Menggunakan layanan Impor/Ekspor Azure untuk mengimpor data ke Azure Files](/azure/import-export/storage-import-export-data-to-files?tabs=azure-cli) |

## <a name="storage-account-references"></a>Referensi akun Storage

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az storage account](../latest/docs-ref-autogen/storage/account.yml) | Mengelola akun penyimpanan. | [Buat akun penyimpanan](/azure/storage/common/storage-account-create?tabs=azure-cli) |
| [az storage account blob-inventory-policy](../latest/docs-ref-autogen/storage/account/blob-inventory-policy.yml) | Mengelola kebijakan inventaris akun penyimpanan. | [Mengaktifkan laporan inventaris blob Azure Storage](/azure/storage/blobs/blob-inventory-how-to?tabs=azure-cli) |
| [az storage account blob-service-properties](../latest/docs-ref-autogen/storage/account/blob-service-properties.yml) | Mengelola properti Blob service akun penyimpanan. | [Mengonfigurasikan replikasi objek untuk blob blok](/azure/storage/blobs/object-replication-configure?tabs=azure-cli) |
| [az storage account encryption-scope](../latest/docs-ref-autogen/storage/account/encryption-scope.yml) | Mengelola cakupan enkripsi akun penyimpanan. | [Membuat dan mengelola cakupan enkripsi](/azure/storage/blobs/encryption-scope-manage?tabs=cli) |
| [az storage account file-service-properties](../latest/docs-ref-autogen/storage/account/file-service-properties.yml) | Mengelola properti Blob service akun penyimpanan. | [Aktifkan penghapusan sementara di berbagi file Azure](/azure/storage/files/storage-files-enable-soft-delete?tabs=azure-cli) |
| [az storage account keys](../latest/docs-ref-autogen/storage/account/keys.yml) | Mengelola kunci akun penyimpanan. | [Mengelola kunci akses akun penyimpanan](/azure/storage/common/storage-account-keys-manage?tabs=azure-cli). |
| [az storage account management-policy](../latest/docs-ref-autogen/storage/account/management-policy.yml) | Mengelola kebijakan pengelolaan akun penyimpanan. |  |
| [az storage account network-rule](../latest/docs-ref-autogen/storage/account/network-rule.yml) | Mengelola aturan jaringan. | [Mengonfigurasi firewall dan jaringan virtual Azure Storage](/azure/storage/common/storage-network-security?tabs=azure-cli) |
| [az storage account or-policy](../latest/docs-ref-autogen/storage/account/or-policy.yml) | Mengelola Kebijakan Replikasi Objek akun penyimpanan. | [Mengonfigurasikan replikasi objek untuk blob blok](/azure/storage/blobs/object-replication-configure?tabs=azure-cli) |
| [az storage account or-policy rule](../latest/docs-ref-autogen/storage/account/or-policy/rule.yml) | Mengelola aturan Kebijakan Replikasi Objek akun penyimpanan. | [Mengonfigurasikan replikasi objek untuk blob blok](/azure/storage/blobs/object-replication-configure?tabs=azure-cli) |
| [az storage account private-endpoint-connection](../latest/docs-ref-autogen/storage/account/private-endpoint-connection.yml) | Mengelola koneksi titik akhir privat akun penyimpanan. | |
| [az storage account private-link-resource](../latest/docs-ref-autogen/storage/account/private-link-resource.yml) | Mengelola sumber daya tautan privat akun penyimpanan. | |

## <a name="storage-blob-references"></a>Referensi blob penyimpanan

Beberapa referensi dalam tabel ini adalah bagian dari ekstensi [storage-preview](https://github.com/Azure/azure-cli-extensions/tree/main/src/storage-preview) atau [storage-blob-preview](https://github.com/Azure/azure-cli-extensions/tree/main/src/storage-blob-preview).

| Referensi | Deskripsi | Ekstensi? | Informasi selengkapnya |
|-|-|-|-|
| [az storage blob](../latest/docs-ref-autogen/storage/blob.yml) | Mengelola penyimpanan objek untuk data tidak terstruktur (blob). | | [Mulai cepat: Membuat, mengunduh, dan mencantumkan blob dengan CLI Azure](/azure/storage/blobs/storage-quickstart-blobs-cli) |
| [az storage blob access](../latest/docs-ref-autogen/storage/blob/access.yml) | Mengelola properti kontrol akses blob saat Namespace Layanan Hierarkis diaktifkan. | storage-preview |  |
| [az storage blob copy](../latest/docs-ref-autogen/storage/blob/copy.yml) | Mengelola operasi salinan blob. | | [Pindahkan blob penyimpanan Azure dari baris perintah dengan Azure CLI](/learn/modules/copy-blobs-from-command-line-and-code/4-exercise-move-blobs-using-cli) |
| [az storage blob directory](../latest/docs-ref-autogen/storage/blob/directory.yml) | Mengelola direktori blob dalam kontainer akun penyimpanan. | storage-preview |  |
| [az storage blob directory access](../latest/docs-ref-autogen/storage/blob/directory/access.yml) | Mengelola properti kontrol akses direktori saat Namespace Layanan Hierarkis diaktifkan. | storage-preview | |
| [az storage blob directory metadata](../latest/docs-ref-autogen/storage/blob/directory/metadata.yml) | Mengelola metadata direktori. | storage-preview |  |
| [az storage blob incremental-copy](../latest/docs-ref-autogen/storage/blob/incremental-copy.yml) | Mengelola operasi salinan bertambah bertahap blob. | | |
| [az storage blob lease](../latest/docs-ref-autogen/storage/blob/lease.yml) | Mengelola penyewaan blob penyimpanan. | |  |
| [az storage blob metadata](../latest/docs-ref-autogen/storage/blob/metadata.yml) | Mengelola metadata blob. | | [Menampilkan properti blob dan metadata menggunakan alat dan kode Azure](/learn/modules/organize-blobs-properties-metadata/3-view-blob-properties-and-metadata-using-azure-tools-and-code) |
| [az storage blob service-properties](../latest/docs-ref-autogen/storage/blob/service-properties.yml) | Mengelola properti layanan blob penyimpanan. | | [Menerapkan situs web statis ke penyimpanan blob](/learn/modules/create-cdn-static-resources-blob-storage/1b-exercise-deploy-a-website) |
| [az storage blob service-properties delete-policy](../latest/docs-ref-autogen/storage/blob/service-properties/delete-policy.yml) | Mengelola properti layanan kebijakan penghapusan blob penyimpanan. | |  |
| [az storage blob tag](../latest/docs-ref-autogen/storage/blob/tag.yml) | Mengelola tag blob penyimpanan. | storage-blob-preview | |

## <a name="storage-container-references"></a>Referensi kontainer penyimpanan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az storage container](../latest/docs-ref-autogen/storage/container.yml) | Mengelola kontainer penyimpanan blob. | [Tutorial: Mengunggah data gambar di cloud dengan Azure Storage](/azure/storage/blobs/storage-upload-process-images?tabs=dotnet%2Cazure-cli) |
| [az storage container immutability-policy](../latest/docs-ref-autogen/storage/container/immutability-policy.yml) | Mengelola kebijakan ketetapan kontainer. | [Mengonfigurasi kebijakan imutabilitas untuk kontainer](/azure/storage/blobs/immutable-policy-configure-container-scope?tabs=azure-cli) |
| [az storage container lease](../latest/docs-ref-autogen/storage/container/lease.yml) | Mengelola penyewaan kontainer penyimpanan blob. | |
| [az storage container legal-hold](../latest/docs-ref-autogen/storage/container/legal-hold.yml) | Mengelola dasar hukum kontainer. | |
| [az storage container metadata](../latest/docs-ref-autogen/storage/container/metadata.yml) | Mengelola metadata kontainer. | [Lihat properti blob dan metadata menggunakan alat dan kode Azure](/learn/modules/organize-blobs-properties-metadata/3-view-blob-properties-and-metadata-using-azure-tools-and-code) |
| [az storage container policy](../latest/docs-ref-autogen/storage/container/policy.yml) | Mengelola kebijakan akses yang disimpan kontainer. | [Menggunakan Tanda Tangan Akses Bersama penyimpanan Azure Blob untuk membatasi akses ke data di HDInsight](/azure/hdinsight/hdinsight-storage-sharedaccesssignature-permissions) |

## <a name="storage-file-share-references"></a>Referensi berbagi file penyimpanan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az storage share](../latest/docs-ref-autogen/storage/share.yml) | Mengelola berbagi file penyimpanan. | [Mulai cepat: Buat dan kelola berbagi file Azure menggunakan Azure CLI](/azure/storage/files/storage-how-to-use-files-cli) |
| [az storage share metadata](../latest/docs-ref-autogen/storage/share/metadata.yml) | Mengelola metadata berbagi file. | |
| [az storage share policy](../latest/docs-ref-autogen/storage/share/policy.yml) | Mengelola kebijakan akses bersama dari berbagi file. |  |

## <a name="storage-file-share-smb-30-references"></a>Referensi berbagi file penyimpanan (SMB 3.0)

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az storage file](../latest/docs-ref-autogen/storage/file.yml) | Mengelola berbagi file penyimpanan yang menggunakan protokol Server Message Block (SMB) 3.0. | [Mulai cepat: Buat dan kelola berbagi file Azure menggunakan Azure CLI](/azure/storage/files/storage-how-to-use-files-cli) |
| [az storage file copy](../latest/docs-ref-autogen/storage/file/copy.yml) | Mengelola operasi penyalinan file dari berbagi file. | |
| [az storage file metadata](../latest/docs-ref-autogen/storage/file/metadata.yml) | Mengelola metadata berbagi file. | |

## <a name="storage-file-system-references"></a>Referensi sistem file penyimpanan

Beberapa referensi dalam tabel ini adalah bagian dari ekstensi [storage-preview](https://github.com/Azure/azure-cli-extensions/tree/main/src/storage-preview).

| Referensi | Deskripsi | Ekstensi? | Informasi selengkapnya |
|-|-|-|-|
| [az storage fs](../latest/docs-ref-autogen/storage/fs.yml) | Mengelola sistem file di akun Azure Data Lake Storage Gen2. | | [Gunakan Azure CLI untuk mengelola direktori dan file di Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-directory-file-acl-cli) |
| [az storage fs access](../latest/docs-ref-autogen/storage/fs/access.yml) | Mengelola akses dan izin sistem file untuk akun Azure Data Lake Storage Gen2. | | [Gunakan Azure CLI untuk mengelola ACL di Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-acl-cli) |
| [az storage fs directory](../latest/docs-ref-autogen/storage/fs/directory.yml) | Mengelola direktori di akun Azure Data Lake Storage Gen2. | | [Gunakan Azure CLI untuk mengelola direktori dan file di Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-directory-file-acl-cli) |
| [az storage fs directory metadata](../latest/docs-ref-autogen/storage/fs/directory/metadata.yml) | Mengelola metadata untuk direktori dalam sistem file. | |  |
| [az storage fs file](../latest/docs-ref-autogen/storage/fs/file.yml) | Mengelola file di akun Azure Data Lake Storage Gen2. | | [Gunakan Azure CLI untuk mengelola direktori dan file di Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-directory-file-acl-cli) |
| [az storage fs file metadata](../latest/docs-ref-autogen/storage/fs/file/metadata.yml) | Mengelola metadata untuk file dalam sistem file. | | |
| [az storage fs metadata](../latest/docs-ref-autogen/storage/fs/metadata.yml) | Mengelola metadata untuk sistem file. | | |
| [az storage fs service-properties](../latest/docs-ref-autogen/storage/fs/service-properties.yml) | Mengelola properti layanan Azure Data Lake Storage Gen2 di akun penyimpanan. | storage-preview |  |

## <a name="storage-queue-references"></a>Referensi antrean penyimpanan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az storage queue](../latest/docs-ref-autogen/storage/queue.yml) | Mengelola antrean penyimpanan. | [Pilih cara mengotorisasi akses untuk data antrean dengan Azure CLI](/azure/storage/queues/authorize-data-operations-cli) |
| [az storage queue metadata](../latest/docs-ref-autogen/storage/queue/metadata.yml) | Mengelola metadata untuk antrean penyimpanan. | |
| [az storage queue policy](../latest/docs-ref-autogen/storage/queue/policy.yml) | Mengelola kebijakan akses bersama untuk antrean penyimpanan. | |

## <a name="additional-storage-references"></a>Referensi penyimpanan lainnya

Beberapa referensi dalam tabel ini adalah bagian dari ekstensi [storage-preview](https://github.com/Azure/azure-cli-extensions/tree/main/src/storage-preview).

| Referensi | Deskripsi | Ekstensi? | Informasi selengkapnya |
|-|-|-|-|
| [az snapshot](../latest/docs-ref-autogen/snapshot.yml) | Mengelola salinan titik waktu dari disk terkelola, blob native, atau snapshot lainnya. | | [Membuat rekam jepret menggunakan portal atau Azure CLI](/azure/virtual-machines/linux/snapshot-copy-managed-disk) |
| [az storage azcopy](../latest/docs-ref-autogen/storage/azcopy.yml) | Mengelola operasi penyimpanan dengan utilitas `AzCopy`. | storage-preview |  |
| [az storage azcopy blob](../latest/docs-ref-autogen/storage/azcopy/blob.yml) | Mengelola penyimpanan objek untuk blob dengan utilitas `AzCopy`. | storage-preview | [Mentranskripsikan file audio](/learn/modules/intro-to-batch-transcription/3-exercise-transcribe-audio-files) |
| [az storage container-rm](../latest/docs-ref-autogen/storage/container-rm.yml) | Mengelola kontainer Azure menggunakan penyedia sumber daya `Microsoft.Storage`. | | |
| [az storage cors](../latest/docs-ref-autogen/storage/cors.yml) | Mengelola Berbagi Sumber Daya Lintas Asal (CORS) layanan penyimpanan. | | [Aktifkan CORS untuk Azure Storage Services menggunakan Azure CLI](/learn/modules/set-up-cors-website-storage/5-enabling-cors-for-your-azure-storage-services-using-the-azure-cli) |
| [az storage directory](../latest/docs-ref-autogen/storage/directory.yml) | Mengelola direktori penyimpanan file. | | [Mulai cepat: Buat dan kelola berbagi file Azure menggunakan Azure CLI](/azure/storage/files/storage-how-to-use-files-cli) |
| [az storage directory metadata](../latest/docs-ref-autogen/storage/directory/metadata.yml) | Mengelola metadata direktori penyimpanan file. | | |
| [az storage entity](../latest/docs-ref-autogen/storage/entity.yml) | Mengelola entitas penyimpanan tabel. | | |
| [az storage logging](../latest/docs-ref-autogen/storage/logging.yml) | Mengelola informasi pengelogan layanan penyimpanan. | | |
| [az storage message](../latest/docs-ref-autogen/storage/message.yml) | Mengelola pesan penyimpanan antrean. | | |
| [az storage metrics](../latest/docs-ref-autogen/storage/metrics.yml) | Mengelola metrik layanan penyimpanan. | | |
| [az storage share-rm](../latest/docs-ref-autogen/storage/share-rm.yml) | Mengelola berbagi file Azure dengan penyedia sumber daya `Microsoft.Storage`. | | [Cara membuat NFS berbagi](/azure/storage/files/storage-files-how-to-create-nfs-shares?tabs=azure-cli) |
| [az storage table](../latest/docs-ref-autogen/storage/table.yml) | Mengelola penyimpanan nilai kunci NoSQL. | | [Menyiapkan aplikasi fungsi di Azure Functions](/learn/modules/send-crop-weather-alerts/6-deploy-azure-function-app) |
| [az storage table policy](../latest/docs-ref-autogen/storage/table/policy.yml) | Mengelola kebijakan akses bersama tabel penyimpanan. | | |

## <a name="see-also"></a>Lihat juga

* [Mulai gunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari penginstalan dan aktivitas masuk.
* Temukan [perintah referensi](../latest/docs-ref-autogen/reference-index.yml) tambahan dan [ekstensi yang tersedia](./azure-cli-extensions-list.md) dalam dokumentasi Azure CLI.
* [Pelajari cara menggunakan Bash dengan Azure CLI](./azure-cli-learn-bash.md)

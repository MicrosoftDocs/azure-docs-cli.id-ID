---
title: Azure CLI references for Azure Virtual Machines | Microsoft Docs
description: Cari perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure Virtual Machines.  Ikuti tautan ke artikel populer untuk mempelajari cara menggunakan Azure CLI untuk AZURE VM.
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli references, azure virtual machines, desktop virtualization, image, shared image gallery
ms.openlocfilehash: b1b7fc7d32ca3aeff2c32f535386a6ebb6b35ba9
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439101"
---
# <a name="azure-cli-reference-commands-for-azure-virtual-machines"></a>Azure CLI reference commands for Azure Virtual Machines

Azure Command-Line Interface[(CLI)](./what-is-azure-cli.md)adalah seperangkat perintah yang Anda gunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di banyak layanan Azure dan memungkinkan Anda untuk mengelola Azure Virtual Machines dari baris perintah.

Pengalaman [Azure Virtual Machines](/azure/virtual-machines) CLI terdiri dari dua bagian: **inti** dan **ekstensinya.** Inti Azure CLI perintah kapal sebagai bagian dari CLI dan didukung penuh. Ekstensi memberi Anda akses ke perintah eksperimental dan pra-rilis. Untuk informasi selengkapnya tentang menggunakan ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).  

> [!NOTE]
> Anda diminta untuk menginstal referensi ekstensi pada penggunaan pertama. Atau, Anda dapat menggunakan perintah [tambahkan ekstensi az](/cli/azure/extension#az_extension_add) untuk menginstal ekstensi dengan nama secara manual.

Lihat [Azure Virtual Machines](/cli/azure/service-page/azure%20virtual%20machines) untuk daftar abjad referensi inti dan ekstensi Azure CLI yang tersedia untuk layanan Azure Virtual Machine. Untuk referensi di setiap subkelompok, lihat tabel di bagian berikut:

- [Virtualisasi desktop](#desktop-virtualization-references)
- [Gambar mesin virtual](#virtual-machine-image-references)
- [Pemeliharaan mesin virtual](#virtual-machine-maintenance-references)
- [Galeri gambar bersama](#shared-image-gallery-references)
- [Mesin virtual](#virtual-machine-references)
- [Set skala komputer virtual](#virtual-machine-scale-set-references)
- [Referensi penyimpanan tambahan](#additional-storage-references)

## <a name="desktop-virtualization-references"></a>Referensi virtualisasi desktop

Semua referensi dalam tabel ini adalah bagian dari [ekstensivirtualisasi desktop.](https://github.com/Azure/azure-cli-extensions/tree/main/src/desktopvirtualization)

| Referensi | Deskripsi |
|-|-|
| [az desktopvirtualization](/cli/azure/desktopvirtualization) | Mengelola virtualisasi desktop. |
| [az desktopvirtualization applicationgroup](/cli/azure/desktopvirtualization/applicationgroup) | Mengelola grup aplikasi virtualisasi desktop. |
| [az desktopvirtualization hostpool](/cli/azure/desktopvirtualization/hostpool) | Mengelola kolam host virtualisasi desktop. |
| [az desktopvirtualization workspace](/cli/azure/desktopvirtualization/workspace) | Mengelola ruang kerja virtualisasi desktop. |

## <a name="virtual-machine-image-references"></a>Referensi gambar mesin virtual

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az image](/cli/azure/image) | Mengelola gambar mesin virtual kustom. | [Cara membuat citra komputer virtual atau VHD](/azure/virtual-machines/linux/capture-image) |
| [az pembangun gambar](/cli/azure/image/builder) | Mengelola dan membuat template pembangun gambar. |  |
| [az image builder customizer](/cli/azure/image/builder/customizer) | Mengelola penyesuaian templat pembangun gambar. |  |
| [az output pembangun gambar](/cli/azure/image/builder/output) | Mengelola distributor output template pembangun gambar. |  |

## <a name="virtual-machine-maintenance-references"></a>Referensi pemeliharaan mesin virtual

Semua referensi dalam tabel ini adalah bagian dari ekstensi [pemeliharaan.](https://github.com/Azure/azure-cli-extensions/tree/main/src/maintenance)

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az maintenance applyupdate](/cli/azure/maintenance/applyupdate) | Mengelola bagaimana pembaruan pemeliharaan diterapkan. | [Mengontrol pembaruan dengan Kontrol Pemeliharaan dan Azure CLI](/azure/virtual-machines/maintenance-control-cli) |
| [az maintenance applyupdate-for-resource-group](/cli/azure/maintenance/applyupdate-for-resource-group) | Mengelola bagaimana pembaruan pemeliharaan diterapkan untuk grup sumber daya. |  |
| [az maintenance assignment](/cli/azure/maintenance/assignment) | Mengelola tugas konfigurasi pemeliharaan. | [Mengontrol pembaruan dengan Kontrol Pemeliharaan dan Azure CLI](/azure/virtual-machines/maintenance-control-cli) |
| [az maintenance configuration](/cli/azure/maintenance/configuration) | Mengelola catatan konfigurasi pemeliharaan | [Mengontrol pembaruan dengan Kontrol Pemeliharaan dan Azure CLI](/azure/virtual-machines/maintenance-control-cli) |
| [az maintenance configuration-for-resource-group](/cli/azure/maintenance/configuration-for-resource-group) | Mengelola catatan konfigurasi pemeliharaan untuk grup sumber daya. |  |
| [az maintenance public-configuration](/cli/azure/maintenance/public-configuration) | Mengelola catatan konfigurasi pemeliharaan publik. | [Konfigurasikan jendela pemeliharaan](/azure/azure-sql/database/maintenance-window-configure?tabs=azure-cli) |
| [az maintenance update](/cli/azure/maintenance/update) | Mengelola pembaruan pemeliharaan. | [Mengontrol pembaruan dengan Kontrol Pemeliharaan dan Azure CLI](/azure/virtual-machines/maintenance-control-cli) |

## <a name="shared-image-gallery-references"></a>Referensi galeri gambar bersama

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sig](/cli/azure/sig) | Mengelola galeri gambar bersama. | [Tutorial: Membuat dan menggunakan gambar kustom untuk set skala komputer virtual dengan antarmuka tingkat panggilan Azure](/azure/virtual-machine-scale-sets/tutorial-use-custom-image-cli) |
| [az sig image-definition](/cli/azure/sig/image-definition) | Mengelola definisi gambar di galeri gambar bersama. | [Tutorial: Membuat dan menggunakan gambar kustom untuk set skala komputer virtual dengan antarmuka tingkat panggilan Azure](/azure/virtual-machine-scale-sets/tutorial-use-custom-image-cli) |
| [az sig image-version](/cli/azure/sig/image-version) | Mengelola versi gambar dalam definisi gambar. | [Tutorial: Membuat dan menggunakan gambar kustom untuk set skala komputer virtual dengan antarmuka tingkat panggilan Azure](/azure/virtual-machine-scale-sets/tutorial-use-custom-image-cli) |
| [az sig share](/cli/azure/sig/share) | Mengelola profil berbagi galeri gambar bersama. |  |

## <a name="virtual-machine-references"></a>Referensi mesin virtual

Beberapa referensi dalam tabel ini adalah bagian dari ekstensi [aem](https://github.com/Azure/azure-cli-extensions/tree/main/src/aem) atau [vm-repair.](https://github.com/Azure/azure-cli-extensions/tree/main/src/vm-repair)

| Referensi | Deskripsi | Ekstensi? | Informasi selengkapnya |
|-|-|-|-|
| [az vm](/cli/azure/vm) | Kelola mesin virtual Windows atau Linux. | | [Tutorial: Membuat dan menggunakan gambar kustom untuk set skala komputer virtual dengan antarmuka tingkat panggilan Azure](/azure/virtual-machine-scale-sets/tutorial-use-custom-image-cli) |
| [az vm aem](/cli/azure/vm/aem) | Kelola Azure Enhanced Monitoring untuk SAP untuk mesin virtual. | aem |  |
| [az vm availability-set](/cli/azure/vm/availability-set) | Mengelola set ketersediaan grup sumber daya mesin virtual. | | [Membuat komputer virtual Linux dengan Azure CLI](/azure/virtual-machines/linux/create-cli-complete) |
| [az vm boot-diagnostics](/cli/azure/vm/boot-diagnostics) | Kelola diagnostik boot untuk mesin virtual. | | |
| [az vm diagnostics](/cli/azure/vm/diagnostics) | Mengelola pengaturan ekstensi diagnostik untuk mesin virtual. | | |
| [az vm disk](/cli/azure/vm/disk) | Melampirkan atau melepaskan disk data terkelola pada mesin virtual. | | [Aktifkan sesuai permintaan bursting](/azure/virtual-machines/disks-enable-bursting?tabs=azure-cli) |
| [az vm encryption](/cli/azure/vm/encryption) | Mengelola enkripsi disk mesin virtual. | | [Mulai Cepat: Membuat dan mengenkripsi komputer virtual Windows dengan Azure CLI](/azure/virtual-machines/linux/disk-encryption-cli-quickstart) |
| [az vm extension](/cli/azure/vm/extension) | Kelola ekstensi untuk mesin virtual. | | [Ekstensi dan fitur komputer virtual untuk Linux](/azure/virtual-machines/extensions/features-linux) |
| [az vm extension image](/cli/azure/vm/extension/image) | Temukan ekstensi yang tersedia untuk mesin virtual. | | [Ekstensi dan fitur komputer virtual untuk Linux](/azure/virtual-machines/extensions/features-linux) |
| [az vm host](/cli/azure/vm/host) | Kelola host khusus untuk mesin virtual. | | [Terapkan pada host khusus menggunakan Azure CLI](/azure/virtual-machines/linux/dedicated-hosts-cli) |
| [az vm host group](/cli/azure/vm/host/group) | Kelola grup host khusus untuk mesin virtual. | | [Terapkan pada host khusus menggunakan Azure CLI](/azure/virtual-machines/linux/dedicated-hosts-cli) |
| [az vm identity](/cli/azure/vm/identity) | Mengelola identitas layanan untuk mesin virtual. | | [Mengonfigurasi Identitas terkelola untuk sumber daya Azure di komputer virtual Azure menggunakan Azure CLI](/azure/active-directory/managed-identities-azure-resources/qs-configure-cli-windows-vm) |
| [az vm image](/cli/azure/vm/image) | Tampilkan informasi tentang gambar mesin virtual yang tersedia. | | [Menemukan informasi citra Azure Marketplace menggunakan Azure CLI](/azure/virtual-machines/linux/cli-ps-findimage) |
| [az vm image terms](/cli/azure/vm/image/terms) | Kelola istilah gambar Azure Marketplace. | | [Menemukan informasi citra Azure Marketplace menggunakan Azure CLI](/azure/virtual-machines/linux/cli-ps-findimage) |
| [az vm monitor log](/cli/azure/vm/monitor/log) | Tampilkan ruang kerja analisis log untuk mesin virtual. | | |
| [az vm monitor metrics](/cli/azure/vm/monitor/metrics) | Tampilkan metrik untuk mesin virtual. | | |
| [az vm nic](/cli/azure/vm/nic) | Mengelola antarmuka jaringan untuk mesin virtual. | | [Cara membuat komputer virtual Linux di Azure dengan beberapa kartu antarmuka jaringan](/azure/virtual-machines/linux/multiple-nics) |
| [az vm repair](/cli/azure/vm/repair) | Kelola perbaikan mesin virtual dan skrip. | vm-repair | |
| [az vm run-command](/cli/azure/vm/run-command) | Mengelola perintah run untuk mesin virtual. | | [Rotate certificates in Azure Kubernetes Service](/azure/aks/certificate-rotation) |
| [az vm secret](/cli/azure/vm/secret) | Mengelola rahasia untuk mesin virtual. | | [Tutorial: Menggunakan sertifikat TLS/SSL untuk mengamankan server web](/azure/virtual-machines/linux/tutorial-secure-web-server) |
| [az vm unmanaged-disk](/cli/azure/vm/unmanaged-disk) | Mengelola disk data yang tidak dikelola untuk mesin virtual. | | [Perencanaan dan implementasi Azure Virtual Machines untuk SAP NetWeaver](/azure/virtual-machines/workloads/sap/planning-guide) |
| [az vm user](/cli/azure/vm/user) | Mengelola akun pengguna untuk mesin virtual. | | [Mengelola pengguna administratif, SSH, dan memeriksa atau memperbaiki disk pada VM Linux menggunakan Ekstensi VMAccess dengan Azure CLI](/azure/virtual-machines/extensions/vmaccess) |

## <a name="virtual-machine-scale-set-references"></a>Referensi set skala mesin virtual

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az vmss](/cli/azure/vmss) | Kelola set skala mesin virtual Azure. | [Mulai Cepat: Membuat set skala komputer virtual dengan Azure CLI](/azure/virtual-machine-scale-sets/quick-create-cli) |
| [az vmss diagnostics](/cli/azure/vmss/diagnostics) | Konfigurasikan ekstensi Diagnostik Azure untuk kumpulan skala mesin virtual. | |
| [az vmss disk](/cli/azure/vmss/disk) | Mengelola disk data untuk satu set skala mesin virtual. | [Tutorial: Membuat dan mengelola set skala komputer virtual dengan antarmuka tingkat panggilan Azure](/azure/virtual-machine-scale-sets/tutorial-use-disks-cli) |
| [az vmss encryption](/cli/azure/vmss/encryption) | Kelola enkripsi untuk set skala mesin virtual. | [Mengenkripsi OS dan disk data terlampir dalam skala komputer virtual yang diatur dengan Azure PowerShell](/azure/virtual-machine-scale-sets/disk-encryption-cli) |
| [az vmss extension](/cli/azure/vmss/extension) | Kelola ekstensi untuk kumpulan skala mesin virtual. | [Mulai Cepat: Membuat set skala komputer virtual dengan Azure CLI](/azure/virtual-machine-scale-sets/quick-create-cli) |
| [az vmss extension image](/cli/azure/vmss/extension/image) | Tampilkan informasi tentang gambar ekstensi yang tersedia untuk satu set skala mesin virtual. | |
| [az vmss identity](/cli/azure/vmss/identity) | Mengelola identitas layanan untuk satu set skala mesin virtual. | [Membuat dan mengelola set skala komputer virtual Azure](/azure/virtual-machine-scale-sets/scripts/cli-sample-manage-scale-set) |
| [az vmss nic](/cli/azure/vmss/nic) | Kelola antarmuka jaringan untuk satu set skala mesin virtual. | |
| [az vmss rolling-upgrade](/cli/azure/vmss/rolling-upgrade) | Kelola pemutakhiran bergulir untuk satu set skala mesin virtual. | |
| [az vmss run-command](/cli/azure/vmss/run-command) | Kelola perintah jalankan untuk kumpulan skala mesin virtual. | |

## <a name="additional-storage-references"></a>Referensi penyimpanan tambahan

Beberapa referensi dalam tabel ini adalah bagian dari [konsol serial](https://github.com/Azure/azure-cli-extensions/tree/main/src/serial-console) atau ekstensi [ssh.](https://github.com/Azure/azure-cli-extensions/tree/main/src/ssh)

| Referensi | Deskripsi | Ekstensi? | Informasi selengkapnya |
|-|-|-|-|
| [az ppg](/cli/azure/ppg) | Mengelola grup penempatan kedekatan. | | [Menyebarkan VM ke grup penempatan kedekatan menggunakan Azure CLI](/azure/virtual-machines/linux/proximity-placement-groups) |
| [az serial-console](/cli/azure/serial-console) | Kelola Konsol Azure Serial untuk mesin virtual atau set skala mesin virtual. | konsol serial | |
| [az serial-console send](/cli/azure/serial-console/send) | Gunakan Konsol Azure Serial untuk mengirim perintah ke mesin virtual atau set skala mesin virtual. | konsol serial | |
| [az ssh](/cli/azure/ssh) | Kelola konfigurasi SSH. | ssh | [Login ke mesin virtual Linux di Azure dengan Azure Active Directory menggunakan autentikasi berbasis sertifikat SSH](/azure/active-directory/devices/howto-vm-sign-in-azure-ad-linux) |
| [az sshkey](/cli/azure/sshkey) | Mengelola konfigurasi kunci publik SSH. | | |

## <a name="see-also"></a>Lihat juga

- [Mulai dengan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari tentang instalasi dan masuk.

- Temukan [referensi](/cli/azure/reference-index) tambahan dan ekstensi yang [tersedia](./azure-cli-extensions-list.md) dalam dokumentasi Azure CLI.

- Pelajari selengkapnya tentang ekstensi di [Gunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

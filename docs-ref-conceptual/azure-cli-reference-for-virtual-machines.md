---
title: Referensi Azure CLI untuk Azure Virtual Machines | Microsoft Docs
description: Temukan perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure Virtual Machines.  Ikuti link ke artikel populer untuk mempelajari cara menggunakan Azure CLI for Azure VM.
author: dbradish-microsoft
manager: barbkess
ms.tool: azure-cli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure cli, mesin virtual azure, virtualisasi desktop, gambar, galeri gambar bersama
ms.openlocfilehash: 3b53e1d16553e5d319790d3415971355a814a9f9
ms.sourcegitcommit: 6822e5d700742617eabda5904fe2ca217bae9d28
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/30/2022
ms.locfileid: "145939262"
---
# <a name="azure-cli-reference-commands-for-azure-virtual-machines"></a>Perintah referensi Azure CLI untuk Azure Virtual Machines

Azure Command-Line Interface ([CLI](./what-is-azure-cli.md)) Azure adalah sekumpulan perintah yang digunakan untuk membuat dan mengelola sumber daya Azure. Perintah ini tersedia di banyak layanan Azure dan memungkinkan Anda untuk mengelola Azure Virtual Machines dari baris perintah.

Pengalaman CLI [Azure Virtual Machines](/azure/virtual-machines) terdiri dari dua bagian: **inti** dan **ekstensi**-nya. Perintah Azure CLI inti dikirimkan sebagai bagian dari CLI dan didukung sepenuhnya. Ekstensi memberi Anda akses ke perintah percobaan dan pra-rilis. Untuk informasi selengkapnya tentang penggunaan ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).  

> [!NOTE]
> Anda diminta menginstal referensi ekstensi saat digunakan pertama kali. Sebagai alternatif, Anda dapat menggunakan perintah [az extension add](/cli/azure/extension#az_extension_add) untuk menginstal ekstensi secara manual berdasarkan nama.

Lihat [Azure Virtual Machines](/cli/azure/service-page/azure%20virtual%20machines) untuk mengetahui daftar alfabet core Azure CLI dan referensi ekstensi yang tersedia untuk layanan Azure Virtual Machine. Untuk referensi di setiap sub-grup, lihat tabel di bagian berikut:

- [Virtualisasi desktop](#desktop-virtualization-references)
- [Gambar mesin virtual](#virtual-machine-image-references)
- [Pemeliharaan mesin virtual](#virtual-machine-maintenance-references)
- [Galeri citra bersama](#shared-image-gallery-references)
- [Komputer virtual](#virtual-machine-references)
- [Set skala komputer virtual](#virtual-machine-scale-set-references)
- [Referensi penyimpanan tambahan](#additional-storage-references)

## <a name="desktop-virtualization-references"></a>Referensi virtualisasi desktop

Semua referensi dalam tabel ini adalah bagian dari ekstensi [desktopvirtualization](https://github.com/Azure/azure-cli-extensions/tree/main/src/desktopvirtualization).

| Referensi | Deskripsi |
|-|-|
| [az desktopvirtualization](../latest/docs-ref-autogen/desktopvirtualization.yml) | Mengelola virtualisasi desktop. |
| [az desktopvirtualization applicationgroup](../latest/docs-ref-autogen/desktopvirtualization/applicationgroup.yml) | Mengelola grup aplikasi virtualisasi desktop. |
| [az desktopvirtualization hostpool](../latest/docs-ref-autogen/desktopvirtualization/hostpool.yml) | Mengelola kumpulan host virtualisasi desktop. |
| [az desktopvirtualization workspace](../latest/docs-ref-autogen/desktopvirtualization/workspace.yml) | Mengelola ruang kerja virtualisasi desktop. |

## <a name="virtual-machine-image-references"></a>Referensi citra komputer virtual

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az image](../latest/docs-ref-autogen/image.yml) | Mengelola citra mesin virtual kustom. | [Cara membuat citra komputer virtual atau VHD](/azure/virtual-machines/linux/capture-image) |
| [az image builder](../latest/docs-ref-autogen/image/builder.yml) | Mengelola dan membuat templat penyusun citra. |  |
| [az image builder customizer](../latest/docs-ref-autogen/image/builder/customizer.yml) | Mengelola penyesuai templat penyusun citra. |  |
| [az image builder output](../latest/docs-ref-autogen/image/builder/output.yml) | Mengelola distributor output templat penyusun citra. |  |

## <a name="virtual-machine-maintenance-references"></a>Referensi pemeliharaan mesin virtual

Semua referensi dalam tabel ini adalah bagian dari ekstensi [pemeliharaan](https://github.com/Azure/azure-cli-extensions/tree/main/src/maintenance).

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az maintenance applyupdate](../latest/docs-ref-autogen/maintenance/applyupdate.yml) | Mengelola bagaimana pembaruan pemeliharaan diterapkan. | [Mengontrol pembaruan dengan Kontrol Pemeliharaan dan Azure CLI](/azure/virtual-machines/maintenance-control-cli) |
| [az maintenance applyupdate-for-resource-group](/cli/azure/maintenance/applyupdate-for-resource-group) | Mengelola bagaimana pembaruan pemeliharaan diterapkan untuk grup sumber daya. |  |
| [az maintenance assignment](../latest/docs-ref-autogen/maintenance/assignment.yml) | Mengelola penetapan konfigurasi pemeliharaan. | [Mengontrol pembaruan dengan Kontrol Pemeliharaan dan Azure CLI](/azure/virtual-machines/maintenance-control-cli) |
| [az maintenance configuration](../latest/docs-ref-autogen/maintenance/configuration.yml) | Mengelola catatan konfigurasi pemeliharaan | [Mengontrol pembaruan dengan Kontrol Pemeliharaan dan Azure CLI](/azure/virtual-machines/maintenance-control-cli) |
| [az maintenance configuration-for-resource-group](/cli/azure/maintenance/configuration-for-resource-group) | Mengelola catatan konfigurasi pemeliharaan untuk grup sumber daya. |  |
| [az maintenance public-configuration](../latest/docs-ref-autogen/maintenance/public-configuration.yml) | Mengelola catatan konfigurasi pemeliharaan publik. | [Konfigurasikan jendela pemeliharaan](/azure/azure-sql/database/maintenance-window-configure?tabs=azure-cli) |
| [az maintenance update](../latest/docs-ref-autogen/maintenance/update.yml) | Mengelola pembaruan pemeliharaan. | [Mengontrol pembaruan dengan Kontrol Pemeliharaan dan Azure CLI](/azure/virtual-machines/maintenance-control-cli) |

## <a name="shared-image-gallery-references"></a>Referensi galeri citra bersama

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az sig](../latest/docs-ref-autogen/sig.yml) | Mengelola galeri citra bersama. | [Tutorial: Membuat dan menggunakan gambar kustom untuk set skala komputer virtual dengan antarmuka tingkat panggilan Azure](/azure/virtual-machine-scale-sets/tutorial-use-custom-image-cli) |
| [az sig image-definition](../latest/docs-ref-autogen/sig/image-definition.yml) | Mengelola definisi citra di galeri citra bersama. | [Tutorial: Membuat dan menggunakan gambar kustom untuk set skala komputer virtual dengan antarmuka tingkat panggilan Azure](/azure/virtual-machine-scale-sets/tutorial-use-custom-image-cli) |
| [az sig image-version](../latest/docs-ref-autogen/sig/image-version.yml) | Mengelola versi citra dalam definisi citra. | [Tutorial: Membuat dan menggunakan gambar kustom untuk set skala komputer virtual dengan antarmuka tingkat panggilan Azure](/azure/virtual-machine-scale-sets/tutorial-use-custom-image-cli) |
| [az sig share](../latest/docs-ref-autogen/sig/share.yml) | Mengelola profil berbagi galeri citra bersama. |  |

## <a name="virtual-machine-references"></a>Referensi mesin virtual

Beberapa referensi dalam tabel ini adalah bagian dari ekstensi [aem](https://github.com/Azure/azure-cli-extensions/tree/main/src/aem) atau [vm-repair](https://github.com/Azure/azure-cli-extensions/tree/main/src/vm-repair).

| Referensi | Deskripsi | Ekstensi? | Informasi selengkapnya |
|-|-|-|-|
| [az vm](../latest/docs-ref-autogen/vm.yml) | Mengelola mesin virtual Windows atau Linux. | | [Tutorial: Membuat dan menggunakan gambar kustom untuk set skala komputer virtual dengan antarmuka tingkat panggilan Azure](/azure/virtual-machine-scale-sets/tutorial-use-custom-image-cli) |
| [az vm aem](../latest/docs-ref-autogen/vm/aem.yml) | Mengelola Azure Enhanced Monitoring for SAP untuk mesin virtual. | aem |  |
| [az vm availability-set](../latest/docs-ref-autogen/vm/availability-set.yml) | Mengelola set ketersediaan grup sumber daya mesin virtual. | | [Membuat komputer virtual Linux dengan Azure CLI](/azure/virtual-machines/linux/create-cli-complete) |
| [az vm boot-diagnostics](../latest/docs-ref-autogen/vm/boot-diagnostics.yml) | Mengelola diagnostik boot untuk mesin virtual. | | |
| [az vm diagnostics](../latest/docs-ref-autogen/vm/diagnostics.yml) | Mengelola pengaturan ekstensi diagnostik untuk mesin virtual. | | |
| [az vm disk](../latest/docs-ref-autogen/vm/disk.yml) | Melampirkan atau melepaskan disk data terkelola pada mesin virtual. | | [Aktifkan bursting sesuai permintaan](/azure/virtual-machines/disks-enable-bursting?tabs=azure-cli) |
| [az vm encryption](../latest/docs-ref-autogen/vm/encryption.yml) | Mengelola enkripsi disk mesin virtual. | | [Mulai Cepat: Membuat dan mengenkripsi komputer virtual Windows dengan Azure CLI](/azure/virtual-machines/linux/disk-encryption-cli-quickstart) |
| [az vm extension](../latest/docs-ref-autogen/vm/extension.yml) | Mengelola ekstensi untuk mesin virtual. | | [Ekstensi dan fitur mesin virtual untuk Linux](/azure/virtual-machines/extensions/features-linux) |
| [az vm extension image](../latest/docs-ref-autogen/vm/extension/image.yml) | Menemukan ekstensi yang tersedia untuk mesin virtual. | | [Ekstensi dan fitur mesin virtual untuk Linux](/azure/virtual-machines/extensions/features-linux) |
| [az vm host](../latest/docs-ref-autogen/vm/host.yml) | Mengelola host khusus untuk mesin virtual. | | [Terapkan pada host khusus menggunakan Azure CLI](/azure/virtual-machines/linux/dedicated-hosts-cli) |
| [az vm host group](../latest/docs-ref-autogen/vm/host/group.yml) | Mengelola grup host khusus untuk mesin virtual. | | [Terapkan pada host khusus menggunakan Azure CLI](/azure/virtual-machines/linux/dedicated-hosts-cli) |
| [az vm identity](../latest/docs-ref-autogen/vm/identity.yml) | Mengelola identitas layanan untuk mesin virtual. | | [Mengonfigurasi Identitas terkelola untuk sumber daya Azure di komputer virtual Azure menggunakan Azure CLI](/azure/active-directory/managed-identities-azure-resources/qs-configure-cli-windows-vm) |
| [az vm image](../latest/docs-ref-autogen/vm/image.yml) | Menampilkan informasi tentang citra mesin virtual yang tersedia. | | [Menemukan informasi citra Azure Marketplace menggunakan Azure CLI](/azure/virtual-machines/linux/cli-ps-findimage) |
| [az vm image terms](../latest/docs-ref-autogen/vm/image/terms.yml) | Mengelola ketentuan citra Azure Marketplace. | | [Menemukan informasi citra Azure Marketplace menggunakan Azure CLI](/azure/virtual-machines/linux/cli-ps-findimage) |
| [az vm monitor log](../latest/docs-ref-autogen/vm/monitor/log.yml) | Menampilkan ruang kerja analitik log untuk mesin virtual. | | |
| [az vm monitor metrics](../latest/docs-ref-autogen/vm/monitor/metrics.yml) | Menampilkan metrik untuk mesin virtual. | | |
| [az vm nic](../latest/docs-ref-autogen/vm/nic.yml) | Mengelola antarmuka jaringan untuk mesin virtual. | | [Cara membuat komputer virtual Linux di Azure dengan beberapa kartu antarmuka jaringan](/azure/virtual-machines/linux/multiple-nics) |
| [az vm repair](../latest/docs-ref-autogen/vm/repair.yml) | Mengelola perbaikan mesin virtual dan skrip. | vm-repair | |
| [az vm run-command](../latest/docs-ref-autogen/vm/run-command.yml) | Mengelola perintah yang dijalankan untuk mesin virtual. | | [Memutar sertifikat di Azure Kubernetes Service](/azure/aks/certificate-rotation) |
| [az vm secret](../latest/docs-ref-autogen/vm/secret.yml) | Mengelola rahasia untuk mesin virtual. | | [Tutorial: Menggunakan sertifikat TLS/SSL untuk mengamankan server web](/azure/virtual-machines/linux/tutorial-secure-web-server) |
| [az vm unmanaged-disk](../latest/docs-ref-autogen/vm/unmanaged-disk.yml) | Mengelola disk data yang tidak dikelola untuk mesin virtual. | | [Perencanaan dan penerapan Microsoft Azure Virtual Machines Azure untuk SAP NetWeaver](/azure/virtual-machines/workloads/sap/planning-guide) |
| [az vm user](../latest/docs-ref-autogen/vm/user.yml) | Mengelola akun pengguna untuk mesin virtual. | | [Mengelola pengguna administratif, SSH, dan memeriksa atau memperbaiki disk di mesin virtual Linux menggunakan Ekstensi VMAccess dengan Azure CLI](/azure/virtual-machines/extensions/vmaccess) |

## <a name="virtual-machine-scale-set-references"></a>Referensi set skala mesin virtual

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az vmss](../latest/docs-ref-autogen/vmss.yml) | Mengelola set skala mesin virtual Azure. | [Mulai Cepat: Membuat set skala komputer virtual dengan Azure CLI](/azure/virtual-machine-scale-sets/quick-create-cli) |
| [az vmss diagnostics](../latest/docs-ref-autogen/vmss/diagnostics.yml) | Mengonfigurasi ekstensi Azure Diagnostics untuk set skala mesin virtual. | |
| [az vmss disk](../latest/docs-ref-autogen/vmss/disk.yml) | Mengelola disk data untuk set skala mesin virtual. | [Tutorial: Membuat dan mengelola set skala komputer virtual dengan antarmuka tingkat panggilan Azure](/azure/virtual-machine-scale-sets/tutorial-use-disks-cli) |
| [az vmss encryption](../latest/docs-ref-autogen/vmss/encryption.yml) | Mengelola enkripsi untuk set skala mesin virtual. | [Mengenkripsi OS dan disk data terlampir dalam skala komputer virtual yang diatur dengan Azure PowerShell](/azure/virtual-machine-scale-sets/disk-encryption-cli) |
| [az vmss extension](../latest/docs-ref-autogen/vmss/extension.yml) | Mengelola ekstensi untuk set skala mesin virtual. | [Mulai Cepat: Membuat set skala komputer virtual dengan Azure CLI](/azure/virtual-machine-scale-sets/quick-create-cli) |
| [az vmss extension image](../latest/docs-ref-autogen/vmss/extension/image.yml) | Menampilkan informasi tentang citra ekstensi yang tersedia untuk set skala mesin virtual. | |
| [az vmss identity](../latest/docs-ref-autogen/vmss/identity.yml) | Mengelola identitas layanan untuk set skala mesin virtual. | [Membuat dan mengelola set skala komputer virtual Azure](/azure/virtual-machine-scale-sets/scripts/cli-sample-manage-scale-set) |
| [az vmss nic](../latest/docs-ref-autogen/vmss/nic.yml) | Mengelola antarmuka jaringan untuk set skala mesin virtual. | |
| [az vmss rolling-upgrade](../latest/docs-ref-autogen/vmss/rolling-upgrade.yml) | Mengelola peningkatan bergulir untuk set skala mesin virtual. | |
| [az vmss run-command](../latest/docs-ref-autogen/vmss/run-command.yml) | Mengelola perintah jalankan untuk set skala mesin virtual. | |

## <a name="additional-storage-references"></a>Referensi penyimpanan tambahan

Beberapa referensi dalam tabel ini adalah bagian dari ekstensi [serial-console](https://github.com/Azure/azure-cli-extensions/tree/main/src/serial-console) atau [ssh](https://github.com/Azure/azure-cli-extensions/tree/main/src/ssh).

| Referensi | Deskripsi | Ekstensi? | Informasi selengkapnya |
|-|-|-|-|
| [az ppg](../latest/docs-ref-autogen/ppg.yml) | Mengelola grup penempatan kedekatan. | | [Menyebarkan VM ke grup penempatan kedekatan menggunakan Azure CLI](/azure/virtual-machines/linux/proximity-placement-groups) |
| [az serial-console](../latest/docs-ref-autogen/serial-console.yml) | Mengelola Azure Serial Console untuk mesin virtual atau set skala mesin virtual. | serial-console | |
| [az serial-console send](../latest/docs-ref-autogen/serial-console/send.yml) | Menggunakan Azure Serial Console untuk mengirim perintah ke mesin virtual atau set skala mesin virtual. | serial-console | |
| [az ssh](../latest/docs-ref-autogen/ssh.yml) | Mengelola konfigurasi SSH. | ssh | [Masuk ke mesin virtual Linux di Azure dengan Azure Active Directory menggunakan autentikasi berbasis sertifikat SSH](/azure/active-directory/devices/howto-vm-sign-in-azure-ad-linux) |
| [az sshkey](../latest/docs-ref-autogen/sshkey.yml) | Mengelola konfigurasi kunci umum SSH. | | |

## <a name="see-also"></a>Lihat juga

* [Mulai gunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari penginstalan dan aktivitas masuk.
* Temukan [perintah referensi](../latest/docs-ref-autogen/reference-index.yml) tambahan dan [ekstensi yang tersedia](./azure-cli-extensions-list.md) dalam dokumentasi Azure CLI.
* [Pelajari cara menggunakan Bash dengan Azure CLI](./azure-cli-learn-bash.md)

---
title: Instal | CLI klasik Azure Microsoft Docs
description: Pelajari cara menginstal Azure classic CLI untuk macOS, Linux, dan Windows untuk menggunakan perintah berbasis shell open-source untuk mengelola layanan Microsoft Azure.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure classic cli, azure classic
ms.openlocfilehash: 98779bdb244262a66270e0210962349ff229dc01
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439047"
---
# <a name="install-the-azure-classic-cli"></a>Pasang CLI klasik Azure

> [!IMPORTANT]
> Topik ini menjelaskan cara menginstal Azure classic CLI. CLI klasik sudah usang dan hanya boleh digunakan dengan model penyebaran klasik.
> Untuk semua penyebaran lainnya, gunakan [Azure CLI](/cli/azure).

Instal DENGAN cepat Cli klasik Azure untuk menggunakan satu set perintah berbasis shell open-source untuk membuat dan mengelola sumber daya dalam Microsoft Azure. Anda memiliki beberapa opsi untuk menginstal alat lintas platform ini di komputer Anda:

* **paket npm** - Jalankan npm (manajer paket untuk JavaScript) untuk menginstal paket Azure classic CLI pada distribusi atau OS Linux Anda. Membutuhkan node.js dan NPM.
* **Installer** - Unduh penginstal untuk instalasi yang mudah di macOS atau Windows.
* **Wadah Docker** - Mulai menggunakan CLI klasik dalam wadah Docker siap pakai. Membutuhkan host Docker.

Untuk opsi dan latar belakang lainnya, lihat repositori proyek di [GitHub.](https://github.com/azure/azure-xplat-cli)

Setelah CLI klasik Azure diinstal, hubungkan `azure login` dan jalankan perintah dari antarmuka baris perintah Anda `azure` (Bash, Terminal, Command prompt, dan sebagainya) untuk bekerja dengan sumber daya Azure Anda.

## <a name="option-1-install-an-npm-package"></a>Opsi 1: Instal paket npm

Untuk menginstal CLI klasik dari paket npm, pastikan Anda telah mengunduh dan menginstal [Node.js dan npm terbaru.](https://nodejs.org/en/download/package-manager/) Kemudian, jalankan `npm install` untuk menginstal paket azure-cli:

```bash
npm install -g azure-cli
```

Pada distribusi Linux, Anda mungkin perlu menggunakan `sudo` untuk berhasil menjalankan `npm` perintah, sebagai berikut:

```bash
sudo npm install -g azure-cli
```

> [!NOTE]
> Jika Anda perlu menginstal atau memperbarui Node.js dan npm pada OS Anda, kami sarankan Anda menginstal Node.js LTS versi 4.x atau yang lebih baru. Jika Anda menggunakan versi yang lebih lama, Anda mungkin mendapatkan kesalahan instalasi.

Jika Anda mau, Anda juga dapat mengunduh file tar dari [rilis GitHub.](https://github.com/Azure/azure-xplat-cli/releases) Kemudian, instal paket npm yang diunduh sebagai berikut (pada distribusi Linux yang mungkin perlu Anda `sudo` gunakan):

```bash
npm install -g <path to downloaded tar file>
```

## <a name="option-2-use-an-installer"></a>Opsi 2: Gunakan penginstal

Jika Anda menggunakan komputer Mac atau Windows, penginstal DMG dan MSI tersedia dari [rilis GitHub](https://github.com/Azure/azure-xplat-cli/releases).

> [!TIP]
> Di Windows, Anda juga dapat mengunduh [Penginstal Platform Web](https://go.microsoft.com/?linkid=9828653) untuk menginstal CLI klasik. Installer ini memberi Anda pilihan untuk menginstal sdk Azure tambahan dan alat baris perintah.

## <a name="option-3-use-a-docker-container"></a>Opsi 3: Gunakan wadah Docker

Jika Anda telah mengatur komputer Anda sebagai host [Docker,](https://docs.docker.com/engine/understanding-docker/) Anda dapat menjalankan Azure classic CLI dalam wadah Docker. Jalankan perintah berikut (pada distribusi Linux yang mungkin perlu Anda `sudo` gunakan):

```bash
docker run -it mcr.microsoft.com/azure-cli:0.10.14
```

## <a name="run-azure-classic-cli-commands"></a>Jalankan perintah CLI klasik Azure

Setelah CLI klasik diinstal, jalankan `azure` perintah dari antarmuka pengguna baris perintah Anda (Bash, Terminal, Command prompt, dan sebagainya). Misalnya, untuk menjalankan perintah bantuan, ketik yang berikut ini:

```azurecli-interactive
azure help
```

> [!NOTE]
> Pada beberapa distribusi Linux, Anda mungkin menerima kesalahan yang mirip dengan `/usr/bin/env: ‘node’: No such file or directory` . Kesalahan ini berasal dari instalasi Node.js baru-baru ini yang diinstal di /usr/bin/nodejs. Untuk memperbaikinya, buat tautan simbolis ke /usr/bin/node dengan menjalankan perintah ini:

```bash
sudo ln -s /usr/bin/nodejs /usr/bin/node
```

Untuk melihat versi CLI klasik Azure yang diinstal, ketik yang berikut ini:

```azurecli-interactive
azure --version
```

> [!NOTE]
> Saat pertama kali menggunakan Azure classic CLI, Anda melihat pesan yang menanyakan apakah Anda ingin mengizinkan Microsoft mengumpulkan informasi penggunaan. Partisipasi bersifat sukarela. Jika Anda memilih untuk berpartisipasi, Anda dapat berhenti kapan saja dengan `azure telemetry --disable` berlari. Untuk memungkinkan partisipasi kapan saja, jalankan `azure telemetry --enable` .

## <a name="update-the-classic-cli"></a>Memperbarui CLI klasik

Microsoft dapat merilis versi terbaru dari Azure classic CLI. Instal ulang CLI klasik menggunakan installer untuk sistem operasi Anda, atau jalankan wadah Docker terbaru. Atau, jika Anda menginstal Node.js dan npm terbaru, perbarui dengan mengetikkan yang berikut (pada distribusi Linux yang mungkin perlu Anda `sudo` gunakan).

```bash
npm update -g azure-cli
```

## <a name="enable-tab-completion"></a>Aktifkan penyelesaian tab

Tab penyelesaian perintah CLI klasik didukung untuk Mac dan Linux.

Untuk mengaktifkannya dalam zsh, jalankan:

```bash
echo '. <(azure --completion)' >> .zshrc
```

Untuk mengaktifkannya dalam bash, jalankan:

```bash
azure --completion >> ~/azure.completion.sh
echo 'source ~/azure.completion.sh' >> ~/.bash_profile
```

## <a name="next-steps"></a>Langkah berikutnya

* Untuk mempelajari lebih lanjut tentang CLI klasik Azure, mengunduh kode sumber, melaporkan masalah, atau berkontribusi pada proyek, kunjungi [repositori GitHub untuk CLI klasik Azure](https://github.com/azure/azure-xplat-cli).

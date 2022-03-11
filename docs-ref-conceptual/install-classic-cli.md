---
title: Menginstal Azure classic CLI | Microsoft Docs
description: Pelajari cara menginstal Azure classic CLI untuk macOS, Linux, dan Windows untuk menggunakan perintah berbasis shell sumber terbuka untuk mengelola layanan Microsoft Azure.
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
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439047"
---
# <a name="install-the-azure-classic-cli"></a>Pasang CLI klasik Azure

> [!IMPORTANT]
> Topik ini menjelaskan cara menginstal Azure classic CLI. CLI klasik tidak digunakan lagi dan hanya boleh digunakan dengan model penyebaran klasik.
> Untuk semua penyebaran lainnya, gunakan [Azure CLI](/cli/azure).

Instal CLI klasik Azure dengan cepat untuk menggunakan serangkaian perintah berbasis shell sumber terbuka untuk membuat dan mengelola sumber daya di Microsoft Azure. Anda memiliki beberapa opsi untuk menginstal alat lintas platform ini di komputer Anda:

* **npm package** - Jalankan npm (pengelola paket untuk JavaScript) untuk menginstal paket Azure classic CLI pada distribusi Linux atau OS Anda. Memerlukan node.js dan npm.
* **Alat penginstal** - Unduh penginstal untuk pemasangan mudah di macOS atau Windows.
* **Kontainer Docker** - Mulai gunakan CLI klasik dalam kontainer Docker yang siap dijalankan. Memerlukan host Docker.

Untuk opsi dan latar belakang lainnya, lihat repositori proyek di [GitHub](https://github.com/azure/azure-xplat-cli).

Setelah Azure classic CLI diinstal, sambungkan dengan `azure login` dan jalankan perintah `azure` dari antarmuka baris perintah Anda (Bash, Terminal, Command prompt, dan seterusnya) untuk menggunakan sumber daya Azure Anda.

## <a name="option-1-install-an-npm-package"></a>Opsi 1: Instal paket npm

Untuk menginstal CLI klasik dari paket npm, pastikan Anda telah mengunduh dan menginstal [Node.js dan npm terbaru](https://nodejs.org/en/download/package-manager/). Kemudian, jalankan `npm install` untuk menginstal paket Azure-cli:

```bash
npm install -g azure-cli
```

Pada distribusi Linux, Anda mungkin perlu menggunakan `sudo` agar berhasil menjalankan perintah `npm`, sebagai berikut:

```bash
sudo npm install -g azure-cli
```

> [!NOTE]
> Jika Anda perlu menginstal atau memperbarui Node.js dan npm di OS Anda, kami sarankan Anda menginstal Node.js LTS versi 4.x atau yang lebih baru. Jika Anda menggunakan versi yang lebih lama, Anda mungkin mendapatkan kesalahan instalasi.

Jika mau, Anda juga dapat mengunduh file tar dari [rilis GitHub](https://github.com/Azure/azure-xplat-cli/releases). Kemudian, instal paket npm yang diunduh sebagai berikut (pada distribusi Linux Anda mungkin perlu menggunakan `sudo`):

```bash
npm install -g <path to downloaded tar file>
```

## <a name="option-2-use-an-installer"></a>Opsi 2: Gunakan alat penginstal

Jika Anda menggunakan komputer Mac atau Windows, alat penginstal DMG dan MSI tersedia dari [rilis GitHub](https://github.com/Azure/azure-xplat-cli/releases).

> [!TIP]
> Di Windows, Anda juga dapat mengunduh [Alat Penginstal Platform Web](https://go.microsoft.com/?linkid=9828653) untuk menginstal CLI klasik. Alat penginstal ini memberi Anda opsi untuk menginstal Azure SDK dan alat baris perintah tambahan.

## <a name="option-3-use-a-docker-container"></a>Opsi 3: Gunakan kontainer Docker

Jika Anda telah menyiapkan komputer sebagai host [Docker](https://docs.docker.com/engine/understanding-docker/), Anda dapat menjalankan CLI klasik Azure dalam kontainer Docker. Jalankan perintah berikut (pada distribusi Linux Anda mungkin perlu menggunakan `sudo`):

```bash
docker run -it mcr.microsoft.com/azure-cli:0.10.14
```

## <a name="run-azure-classic-cli-commands"></a>Menjalankan perintah Azure classic CLI

Setelah CLI klasik diinstal, jalankan perintah `azure` dari antarmuka pengguna baris perintah Anda (Bash, Terminal, Perintah, dan seterusnya). Misalnya, untuk menjalankan perintah bantuan, ketik perintah berikut:

```azurecli-interactive
azure help
```

> [!NOTE]
> Pada beberapa distribusi Linux, Anda mungkin menerima kesalahan yang mirip dengan `/usr/bin/env: ‘node’: No such file or directory`. Kesalahan ini berasal dari penginstalan terbaru Node.js yang diinstal di /usr/bin/nodejs. Untuk memperbaikinya, buat link simbolik ke /usr/bin/node dengan menjalankan perintah ini:

```bash
sudo ln -s /usr/bin/nodejs /usr/bin/node
```

Untuk melihat versi Azure classic CLI yang terinstal, ketik berikut ini:

```azurecli-interactive
azure --version
```

> [!NOTE]
> Saat pertama kali menggunakan Azure classic CLI, Anda akan melihat pesan yang menanyakan apakah Anda ingin mengizinkan Microsoft mengumpulkan informasi penggunaan. Partisipasi bersifat sukarela. Jika Anda memilih untuk berpartisipasi, Anda dapat berhenti kapan saja dengan menjalankan `azure telemetry --disable`. Untuk mengaktifkan partisipasi kapan saja, jalankan `azure telemetry --enable`.

## <a name="update-the-classic-cli"></a>Memperbarui CLI klasik

Microsoft dapat merilis versi terbaru dari Azure classic CLI. Instal ulang CLI klasik menggunakan alat penginstal untuk sistem operasi Anda, atau jalankan kontainer Docker terbaru. Atau, jika Anda telah menginstal Node.js dan npm terbaru, perbarui dengan mengetik berikut ini (pada distribusi Linux Anda mungkin perlu menggunakan `sudo`).

```bash
npm update -g azure-cli
```

## <a name="enable-tab-completion"></a>Mengaktifkan penyelesaian tab

Penyelesaian tab perintah CLI klasik didukung untuk Mac dan Linux.

Untuk mengaktifkannya di zsh, jalankan:

```bash
echo '. <(azure --completion)' >> .zshrc
```

Untuk mengaktifkannya di bash, jalankan:

```bash
azure --completion >> ~/azure.completion.sh
echo 'source ~/azure.completion.sh' >> ~/.bash_profile
```

## <a name="next-steps"></a>Langkah berikutnya

* Untuk mempelajari selengkapnya tentang Azure classic CLI, mengunduh kode sumber, melaporkan masalah, atau berkontribusi pada proyek, kunjungi [repositori GitHub untuk Azure classic CLI](https://github.com/azure/azure-xplat-cli).

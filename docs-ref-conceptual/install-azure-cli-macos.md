---
title: Instal Azure CLI di macOS | Microsoft Docs
description: Pelajari cara menginstal dan menjalankan Azure CLI di macOS menggunakan pengelola paket homebrew. Azure CLI telah diuji pada macOS versi 10.9 dan yang lebih baru.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: Install azure cli, azure cli macos, macos cli, install azure cli macos
ms.openlocfilehash: ba982b124479e11f851611271e6606460c05d3f7
ms.sourcegitcommit: d2227bc475235bf86193e9cae5e02f349a6342e2
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 11/02/2021
ms.locfileid: "132439118"
---
# <a name="install-azure-cli-on-macos"></a>Instal Azure CLI di macOS

Azure Command-Line Interface (CLI) memungkinkan eksekusi perintah melalui terminal menggunakan command-line prompt interaktif atau script. Anda dapat menginstal Azure CLI secara lokal di komputer macOS. Azure CLI pada macOS memungkinkan pelaksanaan berbagai perintah melalui terminal menggunakan command-line interaktif atau script.

Untuk platform macOS, Anda dapat menginstal Azure CLI dengan [manajer paket homebrew](https://brew.sh). Homebrew memudahkan anda untuk menjaga instalasi update CLI anda hingga saat ini. Paket CLI telah diuji pada macOS versi 10.9 dan yang lebih baru.

[!INCLUDE [current-version](includes/current-version.md)]

## <a name="install-with-homebrew"></a>Instal dengan Homebrew

Homebrew adalah cara termudah untuk mengelola instalasi CLI Anda. Ini menyediakan cara mudah untuk menginstal, memperbarui, dan menghapus instalasi.
Jika Anda tidak memiliki homebrew yang tersedia di sistem Anda, [instal homebrew](https://docs.brew.sh/Installation.html) sebelum melanjutkan.

Anda dapat menginstal Azure CLI di macOS dengan memperbarui informasi repositori minuman Anda, lalu menjalankan `install` perintah:

```bash
brew update && brew install azure-cli
```

> [!IMPORTANT]
>
> Azure CLI memiliki ketergantungan pada paket `python3` Homebrew, dan akan menginstalnya.
> Azure CLI dijamin kompatibel dengan versi terbaru yang `python3` diterbitkan di Homebrew.

## <a name="troubleshooting"></a>Pemecahan Masalah

Jika Anda mengalami masalah saat menginstal CLI melalui Homebrew, berikut adalah beberapa kesalahan umum. Jika Anda mengalami masalah yang tidak tercakup di sini, [ajukan masalah di github](https://github.com/Azure/azure-cli/issues).

### <a name="completion-is-not-working"></a>Penyelesaian tidak bekerja

Rumus Homebrew Azure CLI menginstal file penyelesaian yang disebutkan `az` dalam direktori penyelesaian yang dikelola Homebrew (lokasi `/usr/local/etc/bash_completion.d/` default). Untuk memungkinkan penyelesaian, silakan ikuti instruksi Homebrew [di sini.](https://docs.brew.sh/Shell-Completion)

### <a name="unable-to-find-python-or-installed-packages"></a>Tidak dapat menemukan Python atau paket yang diinstal

Mungkin ada ketidakcocokan versi kecil atau masalah lain selama instalasi homebrew. CLI tidak menggunakan lingkungan virtual Python, sehingga bergantung pada menemukan versi Python yang diinstal. Perbaikan yang mungkin adalah menginstal dan menghubungkan kembali `python3` dependensi dari Homebrew.

```bash
brew update && brew install python3 && brew upgrade python3
brew link --overwrite python3
```

### <a name="cli-version-1x-is-installed"></a>CLI versi 1.x diinstal

Jika versi usang diinstal, bisa jadi karena cache homebrew basi. Ikuti instruksi [update.](#update)

### <a name="proxy-blocks-connection"></a>Koneksi blok proksi

Anda mungkin tidak bisa mendapatkan sumber daya dari Homebrew kecuali Anda telah mengkonfigurasinya dengan benar untuk menggunakan proxy Anda. Ikuti [instruksi konfigurasi proxy Homebrew](https://docs.brew.sh/Manpage#using-homebrew-behind-a-proxy).

> [!IMPORTANT]
> Jika Anda berada di belakang proxy, `HTTP_PROXY` dan harus diatur untuk terhubung ke layanan Azure dengan `HTTPS_PROXY` CLI.
> Jika Anda tidak menggunakan auth dasar, disarankan untuk mengekspor variabel-variabel ini dalam `.bashrc` file Anda.
> Selalu ikuti kebijakan keamanan bisnis Anda dan persyaratan administrator sistem Anda.

Untuk mendapatkan sumber daya botol dari Homebrew, proxy Anda perlu mengizinkan koneksi HTTPS ke alamat berikut:

* `https://formulae.brew.sh`
* `https://homebrew.bintray.com`

## <a name="update"></a>Pembaruan

CLI secara teratur diperbarui dengan perbaikan bug, perbaikan, fitur baru, dan fungsi pratinjau. Rilis baru tersedia kira-kira setiap tiga minggu.

[!INCLUDE [az-upgrade](includes/az-upgrade.md)]

Anda juga dapat memperbarui informasi repositori Homebrew lokal Anda dan kemudian meningkatkan `azure-cli` paket.

```bash
brew update && brew upgrade azure-cli
```

## <a name="uninstall"></a>Hapus instalasi

[!INCLUDE [uninstall-boilerplate.md](includes/uninstall-boilerplate.md)]

Gunakan homebrew untuk menghapus `azure-cli` paket.

```bash
brew uninstall azure-cli
```

## <a name="remove-data"></a>Menghapus data

Jika Anda tidak berencana untuk menginstal ulang Azure CLI, hapus datanya.

```bash
rm -rf ~/.azure
```

## <a name="other-installation-methods"></a>Metode penginstalan lainnya

Jika Anda tidak dapat menggunakan homebrew untuk menginstal Azure CLI di lingkungan Anda, Anda dapat menggunakan instruksi manual untuk Linux. Perhatikan bahwa proses ini tidak secara resmi dipertahankan agar kompatibel dengan macOS. Menggunakan manajer paket seperti Homebrew selalu dianjurkan. Hanya gunakan metode instalasi manual jika Anda tidak memiliki opsi lain yang tersedia.

Untuk petunjuk instalasi manual, lihat [Menginstal Azure CLI di Linux secara manual](install-azure-cli-linux.md).

## <a name="next-steps"></a>Langkah berikutnya

Sekarang setelah Anda menginstal Azure CLI di macOS, ikuti tur singkat dari fitur dan perintah umumnya.

> [!div class="nextstepaction"]
> [Mulai menggunakan Azure CLI](get-started-with-azure-cli.md)

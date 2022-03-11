---
title: Menginstal Azure CLI di macOS | Microsoft Docs
description: Pelajari cara menginstal dan menjalankan Azure CLI di macOS menggunakan pengelola paket homebrew. Azure CLI telah diuji di macOS versi 10.9 dan yang lebih baru.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: Menginstal azure cli, azure cli macos, macos cli, menginstal azure cli macos
ms.openlocfilehash: 548fe7d9c8632249aa478eab3335d9b000d9c094
ms.sourcegitcommit: 9d7e461f68914e3d66f29d030bdf50ae58a4ef8b
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 01/19/2022
ms.locfileid: "136921378"
---
# <a name="install-azure-cli-on-macos"></a>Instal Azure CLI di macOS

Azure Command-Line Interface (CLI) memungkinkan eksekusi perintah melalui terminal menggunakan permintaan baris perintah interaktif atau skrip. Anda dapat menginstal Azure CLI secara lokal di komputer macOS. Azure CLI di macOS memungkinkan eksekusi berbagai perintah melalui terminal menggunakan permintaan baris perintah interaktif atau skrip.

Untuk platform macOS, Anda dapat menginstal Azure CLI dengan [pengelola paket homebrew](https://brew.sh). Homebrew memudahkan penginstalan pembaruan CLI tetap diperbarui. Paket CLI telah diuji di macOS versi 10.9 dan yang lebih baru.

[!INCLUDE [current-version](includes/current-version.md)]

## <a name="install-with-homebrew"></a>Menginstal dengan Homebrew

Homebrew adalah cara termudah untuk mengelola penginstalan CLI Anda. Ini menyediakan cara yang mudah untuk menginstal, memperbarui, dan menghapus instalan.
Jika Anda belum memiliki homebrew di sistem Anda, [instal homebrew](https://docs.brew.sh/Installation.html) sebelum melanjutkan.

Anda dapat menginstal Azure CLI di macOS dengan memperbarui informasi repositori homebrew, lalu menjalankan perintah `install`:

```bash
brew update && brew install azure-cli
```

> [!IMPORTANT]
>
> Azure CLI memiliki dependensi pada paket `python@3.10` Homebrew, dan akan menginstalnya.

## <a name="troubleshooting"></a>Pemecahan Masalah

Jika Anda mengalami masalah saat menginstal CLI melalui Homebrew, berikut beberapa daftar kesalahan umum. Jika masalah Anda tidak tercantum di sini, [ajukan masalah di github](https://github.com/Azure/azure-cli/issues).

### <a name="completion-is-not-working"></a>Penyelesaian tidak berfungsi

Rumus Homebrew di Azure CLI menginstal file penyelesaian bernama `az` di direktori penyelesaian yang dikelola Homebrew (lokasi default adalah `/usr/local/etc/bash_completion.d/`). Untuk bisa selesai, ikuti petunjuk Homebrew [di sini](https://docs.brew.sh/Shell-Completion).

### <a name="unable-to-find-python-or-installed-packages"></a>Tidak dapat menemukan Python atau paket yang diinstal

Mungkin ada ketidakcocokan versi kecil atau masalah lain selama penginstalan homebrew. CLI tidak menggunakan lingkungan virtual Python, sehingga ini bergantung pada penemuan versi Python yang diinstal. Kemungkinan perbaikannya adalah dengan menginstal dan menautkan ulang dependensi `python@3.10` dari Homebrew.

```bash
brew update && brew install python@3.10 && brew upgrade python@3.10
brew link --overwrite python@3.10
```

### <a name="cli-version-1x-is-installed"></a>CLI versi 1.x diinstal

Jika versi yang usang diinstal, hal ini bisa jadi karena cache homebrew juga sudah tidak terpakai. Ikuti petunjuk [pembaruan](#update).

### <a name="proxy-blocks-connection"></a>Koneksi blok proksi

Anda mungkin tidak bisa mendapatkan sumber daya dari Homebrew kecuali Anda telah mengonfigurasinya dengan benar untuk menggunakan proksi Anda. Ikuti [Petunjuk konfigurasi proksi Homebrew](https://docs.brew.sh/Manpage#using-homebrew-behind-a-proxy).

> [!IMPORTANT]
> Jika Anda berada di belakang proksi, `HTTP_PROXY` dan `HTTPS_PROXY` harus diatur untuk terhubung ke layanan Azure dengan CLI.
> Jika tidak menggunakan autentikasi dasar, sebaiknya Anda mengekspor variabel ini dalam file `.bashrc`.
> Selalu ikuti kebijakan keamanan bisnis dan persyaratan administrator sistem Anda.

Untuk mendapatkan sumber daya botol dari Homebrew, proksi Anda perlu mengizinkan koneksi HTTPS ke alamat berikut:

* `https://formulae.brew.sh`
* `https://homebrew.bintray.com`

## <a name="update"></a>Pembaruan

CLI diperbarui secara rutin disertai perbaikan bug, penyempurnaan, fitur baru, dan fungsionalitas pratinjau. Rilis baru tersedia kira-kira setiap tiga minggu.

[!INCLUDE [az-upgrade](includes/az-upgrade.md)]

Anda juga dapat memperbarui informasi repositori Homebrew lokal dan kemudian meningkatkan paket `azure-cli`.

```bash
brew update && brew upgrade azure-cli
```

## <a name="uninstall"></a>Hapus instalasi

[!INCLUDE [uninstall-boilerplate.md](includes/uninstall-boilerplate.md)]

Gunakan homebrew untuk menghapus instalan paket `azure-cli`.

```bash
brew uninstall azure-cli
```

## <a name="remove-data"></a>Menghapus data

Jika Anda tidak ingin memasang ulang Azure CLI, hapus datanya.

```bash
rm -rf ~/.azure
```

## <a name="other-installation-methods"></a>Metode penginstalan lainnya

Jika Anda tidak dapat menggunakan homebrew untuk menginstal Azure CLI di lingkungan Anda, gunakan petunjuk penggunaan untuk Linux. Perhatikan bahwa proses ini tidak secara resmi dipertahankan agar kompatibel dengan macOS. Sebaiknya selalu gunakan pengelola paket seperti Homebrew. Hanya gunakan metode penginstalan manual jika Anda tidak ada opsi lain yang tersedia.

Untuk petunjuk penginstalan manual, lihat [Menginstal Azure CLI di Linux secara manual](install-azure-cli-linux.md).

## <a name="next-steps"></a>Langkah berikutnya

Setelah Anda menginstal Azure CLI di macOS, ikuti tur singkat tentang fitur dan perintah umumnya.

> [!div class="nextstepaction"]
> [Mulai menggunakan Azure CLI](get-started-with-azure-cli.md)

---
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 12/15/2020
ms.topic: include
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli
ms.openlocfilehash: 812b436586580c10aac94965d54ad485d095e936
ms.sourcegitcommit: d2227bc475235bf86193e9cae5e02f349a6342e2
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 11/02/2021
ms.locfileid: "132439114"
---
## <a name="overview"></a>Gambaran Umum

> [!NOTE]
> Sangat disarankan untuk menginstal CLI dengan manajer paket. Manajer paket memastikan Anda selalu mendapatkan pembaruan terbaru, dan menjamin stabilitas komponen CLI. Periksa dan lihat apakah ada paket untuk distribusi Anda sebelum menginstal secara manual.

CLI membutuhkan perangkat lunak berikut:

* [Python 3.6.x, 3.7.x atau 3.8.x](https://www.python.org/downloads/).
* [libffi](https://sourceware.org/libffi/)
* [BukaSSL 1.0.2](https://www.openssl.org/source/)

> [!IMPORTANT]
>
> CLI telah menjatuhkan dukungan untuk Python 2.7 sejak `2.1.0` versi. Versi baru tidak lagi menjamin untuk berjalan dengan Python 2.7 dengan benar.

## <a name="install-or-update"></a>Menginstal atau memperbarui

Baik menginstal dan memperbarui CLI memerlukan menjalankan ulang skrip instalasi. Instal CLI dengan menjalankan `curl` .

```bash
curl -L https://aka.ms/InstallAzureCli | bash
```

Skrip juga dapat diunduh dan dijalankan secara lokal. Anda mungkin harus me-restart shell Anda agar perubahan berlaku.

## <a name="troubleshooting"></a>Pemecahan Masalah

Berikut adalah beberapa masalah umum yang terlihat selama instalasi manual. Jika Anda mengalami masalah yang tidak tercakup di sini, [ajukan masalah di GitHub.](https://github.com/Azure/azure-cli/issues)

### <a name="curl-object-moved-error"></a>curl "Object Moved" kesalahan

Jika Anda mendapatkan kesalahan dari `curl` terkait `-L` dengan parameter, atau pesan kesalahan termasuk teks "Objek Dipindahkan", coba gunakan URL lengkap alih-alih `aka.ms` pengalihan:

```bash
curl https://azurecliprod.blob.core.windows.net/install | bash
```

### <a name="az-command-not-found"></a>`az` perintah tidak ditemukan

Jika Anda tidak dapat menjalankan perintah setelah instalasi dan menggunakan `bash` `zsh` atau, bersihkan cache hash perintah shell Anda. jalankan

```bash
hash -r
```

Periksa apakah masalah tersebut sudah teratasi.

Masalah ini juga dapat terjadi jika Anda tidak me-restart shell Setelah instalasi. Pastikan lokasi `az` perintah ada di `$PATH` . Lokasi perintah `az` adalah

```bash
<install path>/bin
```

### <a name="proxy-blocks-connection"></a>Koneksi blok proksi

[!INCLUDE[configure-proxy](configure-proxy.md)]

Untuk mendapatkan skrip instalasi, proxy Anda perlu mengizinkan koneksi HTTPS ke alamat berikut:

* `https://aka.ms/`
* `https://azurecliprod.blob.core.windows.net/`
* `https://pypi.python.org`
* Endpoint yang digunakan oleh manajer paket distribusi Anda (jika ada) untuk paket inti

[!INCLUDE[troubleshoot-wsl.md](troubleshoot-wsl.md)]

## <a name="uninstall"></a>Hapus instalasi

[!INCLUDE [uninstall-boilerplate.md](uninstall-boilerplate.md)]

Uninstall CLI dengan langsung menghapus file dari lokasi yang dipilih pada saat instalasi. Lokasi pemasangan default adalah `$HOME` .

1. Hapus file CLI yang diinstal.

   ```bash
   rm -r <install location>/lib/azure-cli
   rm <install location>/bin/az
   ```

2. Ubah file Anda `$HOME/.bash_profile` untuk menghapus baris berikut:

   ```text
   <install location>/lib/azure-cli/az.completion
   ```

3. Jika menggunakan `bash` `zsh` atau, muat ulang cache perintah shell Anda.

   ```bash
   hash -r
   ```

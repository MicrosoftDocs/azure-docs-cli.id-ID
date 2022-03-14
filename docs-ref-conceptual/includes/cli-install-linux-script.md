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
> Sangat disarankan untuk menginstal CLI dengan pengelola paket. Pengelola paket memastikan Anda selalu mendapatkan pembaruan terbaru, dan menjamin stabilitas komponen CLI. Periksa dan pastikan apakah masih ada paket untuk distribusi Anda sebelum menginstal secara manual.

CLI memerlukan perangkat lunak berikut:

* [Python 3.6.x, 3.7.x atau 3.8.x](https://www.python.org/downloads/).
* [libffi](https://sourceware.org/libffi/)
* [OpenSSL 1.0.2](https://www.openssl.org/source/)

> [!IMPORTANT]
>
> CLI telah menghilangkan dukungan untuk Python 2.7 sejak versi `2.1.0`. Versi baru tidak lagi menjamin fungsi yang benar dengan Python 2.7.

## <a name="install-or-update"></a>Menginstal atau memperbarui

Penginstalan dan pembaruan CLI mengharuskan diwajibkannya eksekusi ulang skrip penginstalan. Instal CLI dengan menjalankan `curl`.

```bash
curl -L https://aka.ms/InstallAzureCli | bash
```

Skrip juga dapat diunduh dan dijalankan secara lokal. Anda mungkin harus memulai ulang shell agar perubahan diterapkan.

## <a name="troubleshooting"></a>Pemecahan Masalah

Berikut beberapa masalah umum yang terjadi selama penginstalan manual. Jika masalah Anda tidak tercantum di sini, [ajukan masalah di GitHub](https://github.com/Azure/azure-cli/issues).

### <a name="curl-object-moved-error"></a>Kesalahan curl "Objek yang Dipindahkan"

Jika Anda menerima kesalahan dari `curl` yang terkait dengan parameter `-L`, atau pesan kesalahan termasuk teks "Objek Dipindahkan", coba gunakan URL lengkap, bukan pengalihan `aka.ms`:

```bash
curl https://azurecliprod.blob.core.windows.net/install | bash
```

### <a name="az-command-not-found"></a>Perintah `az` tidak ditemukan

Jika Anda tidak dapat menjalankan perintah setelah penginstalan dan menggunakan `bash` atau `zsh`, bersihkan cache hash perintah shell. jalankan

```bash
hash -r
```

dan periksa apakah masalahnya terpecahkan.

Masalah ini juga bisa terjadi jika Anda tidak memulai ulang shell setelah penginstalan. Pastikan lokasi perintah `az` ada di `$PATH` Anda. Lokasi perintah `az` adalah

```bash
<install path>/bin
```

### <a name="proxy-blocks-connection"></a>Koneksi blok proksi

[!INCLUDE[configure-proxy](configure-proxy.md)]

Untuk mendapatkan skrip penginstalan, proksi Anda perlu mengizinkan koneksi HTTPS ke alamat berikut:

* `https://aka.ms/`
* `https://azurecliprod.blob.core.windows.net/`
* `https://pypi.python.org`
* Titik akhir yang digunakan oleh pengelola paket distribusi Anda (jika ada) untuk paket inti

[!INCLUDE[troubleshoot-wsl.md](troubleshoot-wsl.md)]

## <a name="uninstall"></a>Hapus instalasi

[!INCLUDE [uninstall-boilerplate.md](uninstall-boilerplate.md)]

Hapus instalan CLI dengan langsung menghapus file dari lokasi yang dipilih pada saat penginstalan. Lokasi penginstalan default adalah `$HOME`.

1. Hapus file CLI yang diinstal.

   ```bash
   rm -r <install location>/lib/azure-cli
   rm <install location>/bin/az
   ```

2. Ubah file `$HOME/.bash_profile` untuk menghapus baris berikut:

   ```text
   <install location>/lib/azure-cli/az.completion
   ```

3. Jika menggunakan `bash` atau `zsh`, muat ulang cache perintah shell.

   ```bash
   hash -r
   ```

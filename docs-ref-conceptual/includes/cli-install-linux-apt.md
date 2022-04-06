---
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 09/29/2020
ms.topic: include
ms.custom: devx-track-azurecli
ms.openlocfilehash: 2afcf12c4b20d4562ffdcdb57cf191f1edebc2d4
ms.sourcegitcommit: cbb162f5b74c5250338109317f06a152809c4b4c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/06/2022
ms.locfileid: "141477368"
---
## <a name="overview"></a>Gambaran Umum

Manajer paket `apt` berisi paket x86_64 untuk Azure CLI yang telah diuji pada distribusi berikut.

| Distribusi | Versi |
|:-------------|:--------|
| Ubuntu       | 16.04 LTS (Xenial Xerus), 18.04 LTS (Bionic Beaver), 20.04 LTS (Focal Fossa), 21.10 (Impish Indri) |
| Debian       | 9 (Stretch), 10 (Buster), 11 (Bullseye) |

> [!WARNING]
> Mulai dari Azure CLI 2.34.0, tidak ada paket DEB yang dirilis untuk Ubuntu 14.04 (Trusty Tahir) dan Debian 8 (Jessie). Anda dapat terus menggunakan versi historis Azure CLI pada sistem ini, tetapi tidak akan ada pembaruan atau perbaikan bug. Pertimbangkan untuk memutakhirkan ke versi Ubuntu atau Debian yang lebih baru untuk menggunakan Azure CLI terbaru.

> [!WARNING]
> Ubuntu 20.04 (Focal Fossa) dan 20.10 (Groovy Gorilla) menyertakan paket `azure-cli` dengan versi `2.0.81` yang disediakan oleh repositori `universe`. Paket ini sudah tidak digunakan dan tidak direkomendasikan. Jika paket ini terinstal, hapus paket tersebut sebelum melanjutkan dengan menjalankan perintah `sudo apt remove azure-cli -y && sudo apt autoremove -y`.
>
> Paket deb `azure-cli` tidak mendukung arsitektur ARM64.

## <a name="installation-options"></a>Opsi Penginstalan

Ada dua opsi untuk menginstal Azure CLI di sistem Anda.  Pertama, Anda dapat menjalankan satu perintah yang akan mengunduh skrip instal dan menjalankan perintah instal untuk Anda.  Atau jika mau, Anda dapat menjalankan sendiri perintah instal dalam proses langkah demi langkah.  Kedua metode disediakan di bawah ini.

## <a name="option-1-install-with-one-command"></a>Opsi 1: Menginstal dengan satu perintah

Tim Azure CLI mengelola skrip untuk menjalankan semua perintah penginstalan dalam satu langkah.  Skrip ini diunduh melalui `curl` dan disalurkan langsung ke `bash` untuk menginstal CLI.

Jika Anda ingin memeriksa sendiri isi skrip sebelum menjalankan, cukup unduh skrip terlebih dahulu menggunakan `curl` dan periksa di editor teks favorit Anda.

```bash
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```

## <a name="option-2-step-by-step-installation-instructions"></a>Opsi 2: Petunjuk penginstalan langkah demi langkah

Jika Anda lebih memilih proses penginstalan langkah demi langkah, selesaikan langkah-langkah berikut untuk menginstal Azure CLI.

1. Dapatkan paket yang diperlukan untuk proses penginstalan:

    ```bash
    sudo apt-get update
    sudo apt-get install ca-certificates curl apt-transport-https lsb-release gnupg
    ```

2. Unduh dan instal kunci penandatanganan Microsoft:

    ```bash
    curl -sL https://packages.microsoft.com/keys/microsoft.asc |
        gpg --dearmor |
        sudo tee /etc/apt/trusted.gpg.d/microsoft.gpg > /dev/null
    ```

3. <div id="set-release"/>Tambahkan repositori perangkat lunak Azure CLI:

    ```bash
    AZ_REPO=$(lsb_release -cs)
    echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" |
        sudo tee /etc/apt/sources.list.d/azure-cli.list
    ```

4. Perbarui informasi repositori dan instal paket `azure-cli`:

    ```bash
    sudo apt-get update
    sudo apt-get install azure-cli
    ```

## <a name="install-specific-version"></a>Menginstal versi tertentu

Anda harus terlebih dahulu mengonfigurasi `azure-cli` informasi repositori seperti yang ditunjukkan di atas. Versi yang tersedia dapat ditemukan di [catatan rilis Azure CLI](../release-notes-azure-cli.md).

1. Untuk melihat versi yang tersedia dengan perintah:

    ```bash
    apt-cache policy azure-cli
    ```

2. Untuk menginstal versi tertentu:

    ```bash
    sudo apt-get install azure-cli=<version>-1~bullseye
    ```

## <a name="troubleshooting"></a>Pemecahan Masalah

Berikut adalah beberapa masalah umum yang terlihat saat menginstal dengan `apt`. Jika Anda mengalami masalah yang tidak tercakup di sini, [ajukan masalah di github](https://github.com/Azure/azure-cli/issues).

### <a name="no-module-issue-on-ubuntu-2004-focalwsl"></a>Tidak ada masalah modul pada Ubuntu 20.04 (Focal)/WSL

Jika Anda menginstal `azure-cli` di `Focal` tanpa menambahkan repositori perangkat lunak Azure CLI di [langkah 3](#set-release) petunjuk pemasangan manual atau menggunakan [skrip](#option-1-install-with-one-command) kami, Anda mungkin mengalami masalah seperti tidak ada modul bernama 'decorator' atau 'antlr4' karena paket yang Anda instal adalah `azure-cli 2.0.81` yang tidak digunakan lagi dari repositori `focal/universe`. Hapus terlebih dahulu dengan menjalankan `sudo apt remove azure-cli -y && sudo apt autoremove -y`, lalu ikuti [petunjuk](#install) di atas untuk menginstal paket `azure-cli` terbaru.

### <a name="lsb_release-does-not-return-the-correct-base-distribution-version"></a>lsb_release tidak mengembalikan versi distribusi dasar yang benar

Beberapa distribusi turunan Ubuntu atau Debian seperti Linux Mint mungkin tidak mengembalikan nama versi yang benar dari `lsb_release`. Nilai ini digunakan dalam proses penginstalan untuk menentukan paket yang akan diinstal. Jika Anda mengetahui nama kode versi Ubuntu atau Debian asal distribusi Anda, Anda dapat mengatur nilai `AZ_REPO` secara manual saat [menambahkan repositori](#set-release). Jika tidak, cari informasi untuk distribusi Anda tentang cara menentukan nama kode distribusi dasar dan atur `AZ_REPO` ke nilai yang benar.

### <a name="no-package-for-your-distribution"></a>Tidak ada paket untuk distribusi Anda

Terkadang, mungkin perlu beberapa saat setelah distribusi dirilis sebelum ada paket Azure CLI yang tersedia. Azure CLI dirancang agar kompatibel terhadap versi dependensi yang akan datang dan mengandalkan sesedikit mungkin dependensinya. Jika tidak ada paket yang tersedia untuk distribusi dasar Anda, coba paket untuk distribusi sebelumnya.

Untuk melakukannya, atur nilai `AZ_REPO` secara manual saat [menambahkan repositori](#set-release). Untuk distribusi Ubuntu gunakan repositori `bionic`, dan untuk distribusi Debian gunakan `stretch`. Distribusi yang dirilis sebelum Ubuntu Trusty dan Debian Wheezy tidak didukung.

### <a name="elementary-os-eos-fails-to-install-the-azure-cli"></a>Elementary OS (EOS) gagal menginstal Azure CLI

EOS gagal menginstal cli Azure karena `lsb_release` mengembalikan `HERA`, yang merupakan nama rilis EOS.  Solusinya adalah memperbaiki file `/etc/apt/sources.list.d/azure-cli.list` dan mengubah `hera main` menjadi `bionic main`.

Konten file asli:

```
deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ hera main
```

Konten file yang dimodifikasi

```
deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ bionic main
```

### <a name="proxy-blocks-connection"></a>Koneksi blok proksi

[!INCLUDE[configure-proxy](configure-proxy.md)]

Sebaiknya Anda juga mengonfigurasi `apt` secara eksplisit untuk menggunakan proksi ini setiap saat. Pastikan baris berikut muncul dalam file konfigurasi `apt` di `/etc/apt/apt.conf.d/`. Sebaiknya gunakan file konfigurasi global yang ada, file konfigurasi proksi yang ada, `40proxies`, atau `99local`, namun ikuti persyaratan administrasi sistem Anda.

```apt.conf
Acquire {
    http::proxy "http://[username]:[password]@[proxy]:[port]";
    https::proxy "https://[username]:[password]@[proxy]:[port]";
}
```

Jika proksi Anda tidak menggunakan autentikasi dasar, __hapus__ bagian `[username]:[password]@` dari URI proksi. Jika Anda memerlukan informasi lebih lanjut untuk konfigurasi proksi, lihat dokumentasi resmi Ubuntu:

* [apt.conf manpage](http://manpages.ubuntu.com/manpages/bionic/en/man5/apt.conf.5.html)
* [Ubuntu wiki - apt-get howto](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

Untuk mendapatkan kunci penandatanganan Microsoft dan mendapatkan paket dari repositori kami, proksi Anda harus mengizinkan koneksi HTTPS ke alamat berikut:

* `https://packages.microsoft.com`

[!INCLUDE[troubleshoot-wsl.md](troubleshoot-wsl.md)]

## <a name="update"></a>Pembaruan
[!INCLUDE [az-upgrade](az-upgrade.md)]

Anda juga dapat menggunakan `apt-get upgrade` untuk memperbarui paket CLI.

   ```bash
   sudo apt-get update && sudo apt-get upgrade
   ```

> [!NOTE]
> Perintah ini memutakhirkan semua paket yang diinstal pada sistem Anda yang tidak mengalami perubahan dependensi.
> Untuk meningkatkan versi CLI saja, gunakan `apt-get install`.
>
> ```bash
> sudo apt-get update && sudo apt-get install --only-upgrade -y azure-cli
> ```

## <a name="uninstall"></a>Hapus instalasi

[!INCLUDE [uninstall-boilerplate.md](uninstall-boilerplate.md)]

1. Hapus instalan dengan `apt-get remove`:

    ```bash
    sudo apt-get remove -y azure-cli
    ```

2. Jika Anda tidak berencana untuk menginstal ulang CLI, hapus informasi repositori Azure CLI:

   ```bash
   sudo rm /etc/apt/sources.list.d/azure-cli.list
   ```

3. Jika Anda tidak menggunakan paket lain dari Microsoft, hapus kunci penandatanganan:

    ```bash
    sudo rm /etc/apt/trusted.gpg.d/microsoft.gpg
    ```

4. Hapus semua paket yang tidak diperlukan:

   ```bash
   sudo apt autoremove
   ```
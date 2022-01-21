---
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 09/29/2020
ms.topic: include
ms.custom: devx-track-azurecli
ms.openlocfilehash: a3328b1765bbbe78c65db01236d0c802fc2a5c15
ms.sourcegitcommit: d1cef00a447e85a7f596c1e7d01f209e99d8dcc6
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 01/21/2022
ms.locfileid: "137614876"
---
## <a name="overview"></a>Gambaran Umum

`apt`Manajer paket berisi paket x86_64 untuk Azure CLI yang telah diuji pada distribusi berikut.

| Distribusi | Versi |
|:-------------|:--------|
| Ubuntu       | 14.04 LTS (Trusty Tahir), 16.04 LTS (Xenial Xerus), 18.04 LTS (Bionic Beaver), 20.04 LTS (Focal Fossa), 21.04 (Hirsute Hippo) |
| Debian       | Debian 8 (Jessie), Debian 9 (Stretch), Debian 10 (Buster), Debian 11 (Bullseye) |

> [!WARNING]
> Ubuntu 20.04 (Focal Fossa) dan 20.10 (Groovy Gorilla) termasuk paket dengan versi yang `azure-cli` `2.0.81` disediakan oleh `universe` repositori. Paket ini sudah usang dan tidak disarankan. Jika paket ini diinstal, lepaskan paket sebelum melanjutkan dengan menjalankan `sudo apt remove azure-cli -y && sudo apt autoremove -y` perintah.
>
> Paket `azure-cli` deb tidak mendukung arsitektur ARM64.

## <a name="installation-options"></a>Opsi Instalasi

Ada dua opsi untuk menginstal Azure CLI pada sistem Anda.  Pertama, Anda dapat menjalankan satu perintah yang akan mengunduh skrip instalasi dan menjalankan perintah instal untuk Anda.  Atau jika Anda mau, Anda dapat menjalankan perintah instalasi sendiri dalam proses langkah demi langkah.  Kedua metode tersebut disediakan di bawah ini.

## <a name="option-1-install-with-one-command"></a>Opsi 1: Instal dengan satu perintah

Tim Azure CLI mempertahankan skrip untuk menjalankan semua perintah instalasi dalam satu langkah.  Skrip ini diunduh melalui `curl` dan disalurkan langsung ke untuk menginstal `bash` CLI.

Jika Anda ingin memeriksa isi naskah sendiri sebelum mengeksekusi, cukup unduh skrip terlebih dahulu menggunakan `curl` dan memeriksanya di editor teks favorit Anda.

```bash
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```

## <a name="option-2-step-by-step-installation-instructions"></a>Opsi 2: Petunjuk instalasi langkah demi langkah

Jika Anda lebih suka proses instalasi langkah demi langkah, selesaikan langkah-langkah berikut untuk menginstal Azure CLI.

1. Dapatkan paket yang diperlukan untuk proses instalasi:

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

4. Perbarui informasi repositori dan instal `azure-cli` paket:

    ```bash
    sudo apt-get update
    sudo apt-get install azure-cli
    ```

## <a name="install-specific-version"></a>Menginstal versi tertentu

Anda harus terlebih dahulu mengkonfigurasi `azure-cli` informasi repositori seperti yang ditunjukkan di atas. Versi yang tersedia dapat ditemukan di [catatan rilis Azure CLI](/cli/azure/release-notes-azure-cli).

1. Untuk melihat versi yang tersedia dengan perintah:

    ```bash
    apt-cache policy azure-cli
    ```

2. Untuk menginstal versi tertentu:

    ```bash
    sudo apt-get install azure-cli=<version>-1~bullseye
    ```

## <a name="troubleshooting"></a>Pemecahan Masalah

Berikut adalah beberapa masalah umum yang terlihat saat menginstal dengan `apt` . Jika Anda mengalami masalah yang tidak tercakup di sini, [ajukan masalah di github](https://github.com/Azure/azure-cli/issues).

### <a name="no-module-issue-on-ubuntu-2004-focalwsl"></a>Tidak ada masalah modul di Ubuntu 20.04 (Focal)/WSL

Jika Anda menginstal `azure-cli` tanpa menambahkan repositori perangkat lunak Azure CLI di langkah `Focal` [3](#set-release) dari instruksi instalasi manual atau menggunakan [skrip](#option-1-install-with-one-command)kami, Anda mungkin mengalami masalah seperti tidak ada modul bernama 'dekorator' atau 'antlr4' karena paket yang Anda instal adalah yang sudah ketinggalan zaman `azure-cli 2.0.81` dari `focal/universe` repositori. Silakan hapus terlebih dahulu `sudo apt remove azure-cli -y && sudo apt autoremove -y` dengan menjalankan, kemudian ikuti [petunjuk](#install) di atas untuk menginstal `azure-cli` paket terbaru.

### <a name="lsb_release-does-not-return-the-correct-base-distribution-version"></a>lsb_release tidak mengembalikan versi distribusi dasar yang benar

Beberapa distribusi yang berasal dari Ubuntu atau Debian seperti Linux Mint mungkin tidak mengembalikan nama versi yang benar dari `lsb_release` . Nilai ini digunakan dalam proses instalasi untuk menentukan paket yang akan diinstal. Jika Anda mengetahui nama kode versi Ubuntu atau Debian distribusi Anda berasal dari, Anda dapat mengatur `AZ_REPO` nilai secara manual ketika menambahkan [repositori.](#set-release) Jika tidak, cari informasi untuk distribusi Anda tentang cara menentukan nama kode distribusi dasar dan atur `AZ_REPO` ke nilai yang benar.

### <a name="no-package-for-your-distribution"></a>Tidak ada paket untuk distribusi Anda

Kadang-kadang mungkin beberapa saat setelah distribusi dirilis sebelum ada paket Azure CLI yang tersedia untuk itu. Azure CLI dirancang untuk menjadi tangguh berkaitan dengan versi masa depan dependensi dan mengandalkan sesedikit mungkin dari mereka. Jika tidak ada paket yang tersedia untuk distribusi dasar Anda, cobalah paket untuk distribusi sebelumnya.

Untuk melakukan ini, atur nilai `AZ_REPO` secara manual saat menambahkan [repositori.](#set-release) Untuk distribusi Ubuntu menggunakan `bionic` repositori, dan untuk penggunaan distribusi Debian. `stretch` Distribusi yang dirilis sebelum Ubuntu Trusty dan Debian Wheezy tidak didukung.

### <a name="elementary-os-eos-fails-to-install-the-azure-cli"></a>Elementary OS (EOS) gagal menginstal Azure CLI

EOS gagal menginstal Cli Azure karena `lsb_release` pengembalian , yang merupakan nama rilis `HERA` EOS.  Solusinya adalah memperbaiki file `/etc/apt/sources.list.d/azure-cli.list` dan berubah `hera main` menjadi `bionic main` .

Isi file asli:

```
deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ hera main
```

Konten file yang dimodifikasi

```
deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ bionic main
```

### <a name="proxy-blocks-connection"></a>Koneksi blok proksi

[!INCLUDE[configure-proxy](configure-proxy.md)]

Anda mungkin juga ingin secara eksplisit mengkonfigurasi `apt` untuk menggunakan proxy ini setiap saat. Pastikan baris berikut muncul dalam `apt` file konfigurasi di `/etc/apt/apt.conf.d/` . Sebaiknya gunakan file konfigurasi global Anda yang ada, file konfigurasi proxy yang ada, `40proxies` atau , tetapi ikuti persyaratan administrasi sistem `99local` Anda.

```apt.conf
Acquire {
    http::proxy "http://[username]:[password]@[proxy]:[port]";
    https::proxy "https://[username]:[password]@[proxy]:[port]";
}
```

Jika proxy Anda tidak menggunakan auth dasar, __hapus__ `[username]:[password]@` bagian dari proxy URI. Jika Anda memerlukan informasi lebih lanjut untuk konfigurasi proxy, lihat dokumentasi resmi Ubuntu:

* [apt.conf manpage](http://manpages.ubuntu.com/manpages/bionic/en/man5/apt.conf.5.html)
* [Ubuntu wiki - apt-get howto](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

Untuk mendapatkan kunci penandatanganan Microsoft dan mendapatkan paket dari repositori kami, proxy Anda perlu mengizinkan koneksi HTTPS ke alamat berikut:

* `https://packages.microsoft.com`

[!INCLUDE[troubleshoot-wsl.md](troubleshoot-wsl.md)]

## <a name="update"></a>Pembaruan
[!INCLUDE [az-upgrade](az-upgrade.md)]

Anda juga dapat menggunakan `apt-get upgrade` untuk memperbarui paket CLI.

   ```bash
   sudo apt-get update && sudo apt-get upgrade
   ```

> [!NOTE]
> Perintah ini meng-upgrade semua paket yang diinstal pada sistem Anda yang belum memiliki perubahan ketergantungan.
> Untuk meningkatkan CLI saja, gunakan `apt-get install` .
>
> ```bash
> sudo apt-get update && sudo apt-get install --only-upgrade -y azure-cli
> ```

## <a name="uninstall"></a>Hapus instalasi

[!INCLUDE [uninstall-boilerplate.md](uninstall-boilerplate.md)]

1. Uninstall dengan `apt-get remove` :

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

4. Hapus paket yang tidak perlu:

   ```bash
   sudo apt autoremove
   ```

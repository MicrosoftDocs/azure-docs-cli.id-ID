---
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 11/24/2020
ms.topic: include
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli
ms.openlocfilehash: 9f7734c22b4401bf704e270f17bf46b42360f060
ms.sourcegitcommit: d2227bc475235bf86193e9cae5e02f349a6342e2
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 11/02/2021
ms.locfileid: "132439113"
---
## <a name="overview"></a>Gambaran Umum

Untuk distribusi Linux `zypper` dengan, seperti openSUSE atau SLES, ada paket yang tersedia untuk Azure CLI. Paket ini telah diuji dengan openSUSE Leap 15.1, dan SLES 15.

[!INCLUDE [current-version](current-version.md)]

[!INCLUDE [rpm-warning](rpm-warning.md)]

## <a name="install"></a>Instal

1. Instal `curl`:

   ```bash
   sudo zypper install -y curl
   ```

2. Mengimpor kunci repositori Microsoft:

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Membuat `azure-cli` informasi repositori lokal:

   ```bash
   sudo zypper addrepo --name 'Azure CLI' --check https://packages.microsoft.com/yumrepos/azure-cli azure-cli
   ```

4. Perbarui `zypper` indeks paket dan instal:

   ```bash
   sudo zypper install --from azure-cli azure-cli
   ```

   Input 2 untuk terus menginstal dengan mengabaikan beberapa dependensinya.

## <a name="install-specific-version"></a>Menginstal versi tertentu

Anda harus terlebih dahulu mengkonfigurasi `azure-cli` informasi repositori seperti yang ditunjukkan di atas. Versi yang tersedia dapat ditemukan di [catatan rilis Azure CLI](/cli/azure/release-notes-azure-cli).

1. Untuk melihat versi yang tersedia dengan perintah:

   ```bash
   zypper search --details --match-exact azure-cli
   ```

2. Untuk menginstal versi tertentu:

   ```bash
   sudo zypper install --from azure-cli azure-cli=<version>-1.el7
   ```

## <a name="troubleshooting"></a>Pemecahan Masalah

Berikut adalah beberapa masalah umum yang terlihat saat menginstal dengan `zypper` . Jika Anda mengalami masalah yang tidak tercakup di sini, [ajukan masalah di GitHub.](https://github.com/Azure/azure-cli/issues)

### <a name="notimplementederror-on-opensuse-15-vm"></a>NotImplementedError on OpenSUSE 15 VM
OpenSUSE 15 VM memiliki Azure CLI pra-instal dengan `2.0.45` versi, sudah usang dan memiliki masalah dengan `az login` . Silakan hapus bersama dengan dependensinya sebelum mengikuti instruksi [Instal](#install) untuk menambahkan Azure CLI terbaru:

```bash
sudo zypper rm -y --clean-deps azure-cli
```

Jika Anda memperbarui Azure CLI tanpa menghapus dependensi `2.0.45` versi, dependensi lamanya dapat memengaruhi versi terbaru Azure CLI. Anda perlu menambahkan kembali versi lama untuk menautkan dependensinya dan kemudian menghapus `azure-cli` dependensinya:

```bash
# The package name may vary on different system version, run 'zypper --no-refresh info azure-cli' to check the source package format
sudo zypper install --oldpackage azure-cli-2.0.45-4.22.noarch

sudo zypper rm -y --clean-deps azure-cli
```

### <a name="install-on-sles-12-or-other-systems-without-python-36"></a>Instal pada SLES 12 atau sistem lain tanpa Python 3.6

Pada SLES 12, paket default `python3` dan tidak didukung oleh Azure `3.4` CLI. Anda dapat terlebih dahulu mengikuti langkah 1-3 dari [instruksi instalasi](#install) untuk menambahkan `azure-cli` repositori. Kemudian buat versi yang lebih tinggi `python3` dari sumber. Akhirnya, Anda dapat mengunduh paket Azure CLI dan menginstalnya tanpa ketergantungan.

Anda dapat menggunakan perintah berikut untuk menginstal atau memperbarui Azure CLI berdasarkan langkah-langkah di atas. Script akan menginstal `Python 3.8` di bawah dan membuat Azure CLI menggunakannya dengan menetapkan alias untuk `/usr/local/azcli` `az` `PATH=/usr/local/azcli/bin:$PATH az` . Anda juga dapat mengunduh skrip dan memodifikasinya sesuai dengan kebutuhan Anda. Misalnya, Anda dapat mengubah versi Python atau menginstal lokasi.

```bash
curl -sL https://azurecliprod.blob.core.windows.net/sles12_install_v2.sh | sudo bash
```
Untuk pertama kalinya menginstal, ingatlah untuk menjalankan perintah berikut untuk mengaktifkan alias:

```bash
source ~/.bashrc
```

### <a name="proxy-blocks-connection"></a>Koneksi blok proksi

[!INCLUDE[configure-proxy](configure-proxy.md)]

Anda mungkin juga ingin secara eksplisit mengkonfigurasi `zypper` `yast2` (melalui) untuk menggunakan proxy ini setiap saat. Untuk melakukannya, jalankan `yast2 proxy` perintah sebagai superuser, dan isi informasi yang disajikan dalam formulir. Jika Anda memiliki window manager yang tersedia di sistem Anda, Anda juga dapat menggunakan `Network Services > Proxy` panel di `YaST Control Center` .

Untuk konfigurasi tingkat lanjut atau informasi selengkapnya, lihat [dokumentasi konfigurasi OpenSUSE Proxy](https://www.suse.com/documentation/slms1/book_slms/data/sec_wy_config_updates_proxy.html)

Untuk mendapatkan kunci penandatanganan Microsoft dan mendapatkan paket dari repositori kami, proxy Anda perlu mengizinkan koneksi HTTPS ke alamat berikut:

* `https://packages.microsoft.com`
* `https://download.opensuse.org`

[!INCLUDE[troubleshoot-wsl.md](troubleshoot-wsl.md)]

### <a name="ssl-certificate-problem"></a>Masalah sertifikat SSL

Ketika sertifikat rusak atau usang pada mesin, Anda mungkin menerima kesalahan yang menunjukkan bahwa curl gagal memverifikasi legitimasi server dan karena itu tidak dapat membuat koneksi yang aman.  Perbarui sertifikat Anda untuk memperbaiki masalah.

```bach
sudo zypper update-ca-certificates
```

## <a name="update"></a>Pembaruan

[!INCLUDE [az-upgrade](az-upgrade.md)]

Anda juga dapat memperbarui paket dengan `zypper update` perintah.

```bash
sudo zypper refresh
sudo zypper update azure-cli
```

## <a name="uninstall"></a>Hapus instalasi

[!INCLUDE [uninstall-boilerplate.md](uninstall-boilerplate.md)]

1. Hapus paket dari sistem Anda.

    ```bash
    sudo zypper remove -y azure-cli
    ```

2. Jika Anda tidak berencana untuk menginstal ulang CLI, hapus informasi repositori.

   ```bash
   sudo zypper removerepo azure-cli
   ```

3. Jika Anda tidak menggunakan paket Microsoft lainnya, hapus kunci penandatanganan Microsoft.

   ```bash
   MSFT_KEY=`rpm -qa gpg-pubkey /* --qf "%{version}-%{release} %{summary}\n" | grep Microsoft | awk '{print $1}'`
   sudo rpm -e --allmatches gpg-pubkey-$MSFT_KEY
   ```

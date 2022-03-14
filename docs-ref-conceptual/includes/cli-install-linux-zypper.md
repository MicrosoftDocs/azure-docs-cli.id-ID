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

Untuk distribusi Linux dengan `zypper`, seperti openSUSE atau SLES, ada paket yang tersedia untuk Azure CLI. Paket ini telah diuji dengan openSUSE Leap 15.1, dan SLES 15.

[!INCLUDE [current-version](current-version.md)]

[!INCLUDE [rpm-warning](rpm-warning.md)]

## <a name="install"></a>Instal

1. Instal `curl`:

   ```bash
   sudo zypper install -y curl
   ```

2. Impor kunci repositori Microsoft:

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Buat informasi repositori lokal `azure-cli`:

   ```bash
   sudo zypper addrepo --name 'Azure CLI' --check https://packages.microsoft.com/yumrepos/azure-cli azure-cli
   ```

4. Perbarui penginstalan dan indeks paket `zypper`:

   ```bash
   sudo zypper install --from azure-cli azure-cli
   ```

   Input 2 untuk tetap memasang dengan mengabaikan beberapa dependensinya.

## <a name="install-specific-version"></a>Menginstal versi tertentu

Anda harus terlebih dahulu mengonfigurasi `azure-cli` informasi repositori seperti yang ditunjukkan di atas. Versi yang tersedia dapat ditemukan di [catatan rilis Azure CLI](/cli/azure/release-notes-azure-cli).

1. Untuk melihat versi yang tersedia dengan perintah:

   ```bash
   zypper search --details --match-exact azure-cli
   ```

2. Untuk menginstal versi tertentu:

   ```bash
   sudo zypper install --from azure-cli azure-cli=<version>-1.el7
   ```

## <a name="troubleshooting"></a>Pemecahan Masalah

Berikut beberapa masalah umum yang ditemukan saat menginstal dengan `zypper`. Jika masalah Anda tidak tercantum di sini, [ajukan masalah di GitHub](https://github.com/Azure/azure-cli/issues).

### <a name="notimplementederror-on-opensuse-15-vm"></a>NotImplementedError di VM OpenSUSE 15
VM OpenSUSE 15 memiliki Azure CLI pra-instal dengan versi `2.0.45`, ini sudah usang dan mengalami masalah dengan `az login`. Hapus beserta dependensinya sebelum mengikuti petunjuk [Penginstalan](#install) untuk menambahkan Azure CLI terbaru:

```bash
sudo zypper rm -y --clean-deps azure-cli
```

Jika Anda memperbarui Azure CLI tanpa menghapus dependensi versi `2.0.45`, dependensi lamanya dapat memengaruhi Azure CLI versi terbaru. Anda perlu menambahkan kembali versi lama untuk ditautkan ke dependensinya, lalu menghapusnya `azure-cli` bersama dengan dependensinya:

```bash
# The package name may vary on different system version, run 'zypper --no-refresh info azure-cli' to check the source package format
sudo zypper install --oldpackage azure-cli-2.0.45-4.22.noarch

sudo zypper rm -y --clean-deps azure-cli
```

### <a name="install-on-sles-12-or-other-systems-without-python-36"></a>Instal di SLES 12 atau sistem lain tanpa Python 3.6

Di SLES 12, paket `python3` default berupa `3.4` dan tidak didukung oleh Azure CLI. Anda dapat mengikuti langkah 1-3 di [petunjuk penginstalan](#install) terlebih dahulu untuk menambahkan repositori `azure-cli`. Kemudian, buat versi `python3` yang lebih tinggi dari sumber. Terakhir, Anda dapat mengunduh paket Azure CLI dan menginstalnya tanpa dependensi.

Anda dapat menggunakan satu perintah berikut untuk menginstal atau memperbarui Azure CLI berdasarkan langkah-langkah di atas. Skrip akan menginstal `Python 3.8` di bagian `/usr/local/azcli` dan membuat Azure CLI menggunakannya dengan menetapkan alias `az` ke `PATH=/usr/local/azcli/bin:$PATH az`. Anda juga dapat mengunduh skrip dan mengubahnya sesuai kebutuhan Anda. Misalnya, Anda dapat mengubah versi Python atau lokasi penginstalan.

```bash
curl -sL https://azurecliprod.blob.core.windows.net/sles12_install_v2.sh | sudo bash
```
Untuk penginstalan pertama kali, jangan lupa jalankan perintah berikut untuk mengaktifkan alias:

```bash
source ~/.bashrc
```

### <a name="proxy-blocks-connection"></a>Koneksi blok proksi

[!INCLUDE[configure-proxy](configure-proxy.md)]

Sebaiknya Anda juga mengonfigurasi `zypper` (melalui `yast2`) secara eksplisit untuk menggunakan proksi ini setiap saat. Untuk melakukannya, jalankan `yast2 proxy` perintah sebagai superuser, dan isi informasi yang diberikan dalam formulir. Jika memiliki pengelola jendela yang tersedia di sistem, Anda juga dapat menggunakan panel `Network Services > Proxy` di `YaST Control Center`.

Untuk mengetahui konfigurasi tingkat lanjutan atau informasi selengkapnya, lihat [Dokumentasi Konfigurasi Proksi OpenSUSE](https://www.suse.com/documentation/slms1/book_slms/data/sec_wy_config_updates_proxy.html)

Untuk mendapatkan kunci penandatanganan Microsoft dan mendapatkan paket dari repositori kami, proksi Anda perlu mengizinkan koneksi HTTPS ke alamat berikut:

* `https://packages.microsoft.com`
* `https://download.opensuse.org`

[!INCLUDE[troubleshoot-wsl.md](troubleshoot-wsl.md)]

### <a name="ssl-certificate-problem"></a>Masalah sertifikat SSL

Jika sertifikat rusak atau usang pada mesin, Anda mungkin menerima kesalahan yang menunjukkan bahwa curl gagal memverifikasi keabsahan server, sehingga tidak dapat membangun koneksi yang aman.  Perbarui sertifikat Anda untuk memperbaiki masalah.

```bach
sudo zypper update-ca-certificates
```

## <a name="update"></a>Pembaruan

[!INCLUDE [az-upgrade](az-upgrade.md)]

Anda juga dapat memperbarui paket dengan perintah `zypper update`.

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

2. Jika Anda tidak ingin memasang ulang CLI, hapus informasi repositori.

   ```bash
   sudo zypper removerepo azure-cli
   ```

3. Jika Anda tidak menggunakan paket Microsoft lainnya, hapus kunci penandatanganan Microsoft.

   ```bash
   MSFT_KEY=`rpm -qa gpg-pubkey /* --qf "%{version}-%{release} %{summary}\n" | grep Microsoft | awk '{print $1}'`
   sudo rpm -e --allmatches gpg-pubkey-$MSFT_KEY
   ```

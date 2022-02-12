---
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 11/24/2020
ms.topic: include
ms.custom: devx-track-azurecli
ms.openlocfilehash: 64354fafa776303afe2998a8d4fbf9c4f4be09ae
ms.sourcegitcommit: ad79327952adf0f8be8f1b9678e72434d9f03f0c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/12/2022
ms.locfileid: "138606462"
---
## <a name="overview"></a>Gambaran Umum

Untuk distribusi Linux dengan `dnf` seperti RHEL, Fedora, atau CentOS, ada paket untuk Azure CLI. Paket ini telah diuji dengan RHEL 7.7, RHEL 8, Fedora 24 dan lebih tinggi, CentOS 7 dan CentOS 8.

[!INCLUDE [current-version](current-version.md)]

[!INCLUDE [rpm-warning](rpm-warning.md)]

> [!NOTE]
>
> Gunakan `yum` manajer paket jika Anda menggunakan sistem Linux yang tidak mendukung `dnf` manajer paket.

## <a name="install"></a>Instal

1. Impor kunci repositori Microsoft.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

2. Membuat informasi repositori lokal `azure-cli` .

   ```bash
   echo -e "[azure-cli]
   name=Azure CLI
   baseurl=https://packages.microsoft.com/yumrepos/azure-cli
   enabled=1
   gpgcheck=1
   gpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/azure-cli.repo
   ```

3. Instal dengan `dnf install` perintah.

   ```bash
   sudo dnf install azure-cli
   ```

## <a name="install-specific-version"></a>Menginstal versi tertentu

Anda harus terlebih dahulu mengonfigurasi `azure-cli` informasi repositori seperti yang ditunjukkan di atas. Versi yang tersedia dapat ditemukan di [catatan rilis Azure CLI](/cli/azure/release-notes-azure-cli).

1. Untuk melihat versi yang tersedia dengan perintah:

   ```bash
   dnf list --showduplicates azure-cli
   ```

2. Untuk menginstal versi tertentu:

   ```bash
   sudo dnf install azure-cli-<version>-1.el7
   ```

## <a name="troubleshooting"></a>Pemecahan Masalah

Berikut adalah beberapa masalah umum yang terlihat saat menginstal dengan `dnf`. Jika Anda mengalami masalah yang tidak tercakup di sini, [ajukan masalah di GitHub](https://github.com/Azure/azure-cli/issues).

### <a name="install-on-rhel-76-or-other-systems-without-python-3"></a>Instal di RHEL 7.6 atau sistem lain tanpa Python 3

Jika Anda bisa, silakan tingkatkan sistem Anda ke versi dengan dukungan resmi untuk `python 3.6+` paket. Jika tidak, Anda harus menginstal `python3` paket terlebih dahulu lalu menginstal Azure CLI tanpa dependensi.

Anda dapat menggunakan satu perintah berikut untuk menginstal Azure CLI dengan `python 3.6` bawaan dari sumber:

```bash
curl -sL https://azurecliprod.blob.core.windows.net/rhel7_6_install.sh | sudo bash
```

Anda juga dapat melakukannya selangkah demi selangkah:

Pertama, Azure CLI memerlukan `SSL 1.1+` dan Anda perlu membangun `openssl 1.1` dari sumber sebelum membangun `python3`:

```bash
sudo dnf install gcc gcc-c++ make ncurses patch wget tar zlib zlib-devel -y
# build openssl from source
cd ~
wget https://www.openssl.org/source/openssl-1.1.1d.tar.gz
tar -xzf openssl-1.1.1d.tar.gz
cd openssl-1.1.1d
./config --prefix=/usr/local/ssl --openssldir=/usr/local/ssl
make
sudo make install
# configure shared object lookup directory so that libssl.so.1.1 can be found
echo "/usr/local/ssl/lib" | sudo tee /etc/ld.so.conf.d/openssl-1.1.1d.conf
# reload config
sudo ldconfig -v
```

Kemudian bangun Python 3 dari sumber:

```bash
PYTHON_VERSION="3.6.9"
PYTHON_SRC_DIR=$(mktemp -d)
wget -qO- https://www.python.org/ftp/python/$PYTHON_VERSION/Python-$PYTHON_VERSION.tgz | tar -xz -C "$PYTHON_SRC_DIR"
cd $PYTHON_SRC_DIR/Python-$PYTHON_VERSION
./configure --prefix=/usr --with-openssl=/usr/local/ssl
make
sudo make install
```

Terakhir, ikuti langkah 1 dan 2 dari [instruksi instal](#install) untuk menambahkan repositori Azure CLI. Anda sekarang dapat mengunduh paket dan menginstalnya tanpa ketergantungan.

> [!NOTE]
>
> Jika Anda tidak menginstal plugin unduhan dnf, Anda akan menemukan perintah yang tidak ditemukan kesalahan dalam mengeksekusi kode di bawah ini. Gunakan `dnf install 'dnf-command(download)'` untuk menginstal plugin unduhan dnf.

```bash
sudo dnf download azure-cli
sudo rpm -ivh --nodeps azure-cli-*.rpm
```

Sebagai alternatif, Anda juga dapat menginstal Python 3 melalui beberapa [repo tambahan](https://developers.redhat.com/blog/2018/08/13/install-python3-rhel/). Dengan cara ini, jika Anda telah mengatur `python3` tetapi masih mendapatkan kesalahan `python3: command not found` ketika mencoba untuk menjalankan cli, Anda perlu menambahkannya ke jalur Anda.

```bash
scl enable rh-python36 bash
```

### <a name="proxy-blocks-connection"></a>Koneksi blok proksi

[!INCLUDE[configure-proxy](configure-proxy.md)]

Anda mungkin juga ingin mengkonfigurasi `dnf` secara eksplisit untuk menggunakan proxy ini setiap saat. Pastikan baris berikut muncul di bawah `[main]` bagian `/etc/dnf/dnf.conf`:

```dnf.conf
[main]
# ...
proxy=http://[proxy]:[port] # If your proxy requires https, change http->https
proxy_username=[username] # Only required for basic auth
proxy_password=[password] # Only required for basic auth
```

Untuk mendapatkan kunci penandatanganan Microsoft dan mendapatkan paket dari repositori kami, proxy Anda perlu mengizinkan koneksi HTTPS ke alamat berikut:

* `https://packages.microsoft.com`

[!INCLUDE[troubleshoot-wsl.md](troubleshoot-wsl.md)]

## <a name="update"></a>Pembaruan

[!INCLUDE [az-upgrade](az-upgrade.md)]

Anda juga dapat memperbarui Azure CLI dengan `dnf update` perintah.

```bash
sudo dnf update azure-cli
```

## <a name="uninstall"></a>Hapus instalasi

[!INCLUDE [uninstall-boilerplate.md](uninstall-boilerplate.md)]

1. Hapus paket dari sistem Anda.

   ```bash
   sudo dnf remove azure-cli
   ```

2. Jika Anda tidak berencana untuk menginstal ulang CLI, hapus informasi repositori.

   ```bash
   sudo rm /etc/yum.repos.d/azure-cli.repo
   ```

3. Jika Anda tidak menggunakan paket Microsoft lainnya, hapus kunci penandatanganan.

   ```bash
   MSFT_KEY=`rpm -qa gpg-pubkey /* --qf "%{version}-%{release} %{summary}\n" | grep Microsoft | awk '{print $1}'`
   sudo rpm -e --allmatches gpg-pubkey-$MSFT_KEY
   ```

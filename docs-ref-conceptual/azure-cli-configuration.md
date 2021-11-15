---
title: Azure CLI configuration options | Microsoft Docs
description: Azure CLI memungkinkan konfigurasi pengguna untuk berbagai pengaturan. Mengelola nilai dengan perintah konfigurasi az, variabel lingkungan, atau dalam file konfigurasi.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/01/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: environment variables, configuration file, configuration settings, user configuration, azure cli variables, azure cli configuration, cli configuration
ms.openlocfilehash: a0f17f11760a7d8db6e1a9eb68a5c5e5ba37696e
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439060"
---
# <a name="azure-cli-configuration"></a>Konfigurasi CLI Azure

Azure CLI memungkinkan konfigurasi pengguna untuk pengaturan seperti pencatatan, pengumpulan data, dan nilai argumen default. CLI menawarkan perintah kenyamanan untuk mengelola beberapa default, `az config` . Nilai lain dapat diatur dalam file konfigurasi atau dengan variabel lingkungan. Artikel ini memberikan informasi lebih lanjut tentang pengaturan konfigurasi pengguna ini dan cara mengkonfigurasi Azure CLI.

Nilai konfigurasi yang digunakan oleh CLI dievaluasi dalam prioritas berikut, dengan item yang lebih tinggi pada daftar mengambil prioritas.

1. Parameter baris perintah
1. Parameter nilai tetap ditetapkan dengan `az config param-persist`
1. Variabel lingkungan
1. Nilai dalam kumpulan berkas konfigurasi dengan `az config`

## <a name="cli-configuration-with-az-config"></a>Konfigurasi CLI dengan az config

Anda mengatur default untuk CLI dengan perintah [config set az.](/cli/azure/config#az_config_set)
Perintah ini mengambil daftar pasangan yang terpisah dari ruang `key=value` sebagai argumen. Nilai yang disediakan digunakan oleh CLI sebagai pengganti argumen yang diperlukan.

Tabel berikut berisi daftar kunci konfigurasi yang tersedia.

| Nama | Deskripsi |
|------|-------------|
| defaults.group | Grup sumber daya default untuk digunakan untuk semua perintah. |
| defaults.location | Lokasi default untuk digunakan untuk semua perintah. |
| defaults.web | Nama aplikasi default untuk digunakan untuk `az webapp` perintah. |
| defaults.vm | Nama VM default yang akan digunakan untuk `az vm` perintah. |
| defaults.vmss | Nama virtual machine scale set (VMSS) default untuk digunakan untuk  `az vmss` perintah. |
| defaults.acr | Nama registri kontainer default untuk digunakan untuk `az acr` perintah. |

Sebagai contoh, inilah cara Anda mengatur grup sumber daya default dan lokasi untuk semua perintah.

```azurecli-interactive
az config set defaults.location=westus2 defaults.group=MyResourceGroup
```

## <a name="cli-configuration-file"></a>Berkas konfigurasi CLI

File konfigurasi CLI berisi pengaturan lain yang digunakan untuk mengelola perilaku CLI. File konfigurasi itu sendiri berada di `$AZURE_CONFIG_DIR/config` . Nilai default `AZURE_CONFIG_DIR` ada `$HOME/.azure` di Linux dan macOS, dan `%USERPROFILE%\.azure` pada Windows.

File konfigurasi ditulis dalam format file INI. Format file ini didefinisikan oleh header bagian, diikuti oleh daftar entri nilai kunci.

* Header bagian ditulis sebagai `[section-name]` . Nama bagian sensitif terhadap kasus.
* Entri ditulis sebagai `key=value` . Nama-nama kunci tidak sensitif terhadap kasus.
* Komentar adalah setiap baris yang dimulai dengan `#` atau `;` . Komentar inline tidak diperbolehkan.

Booleans adalah kasus-sensitif, dan diwakili oleh nilai-nilai berikut.

* __Benar__: `1` , , `yes` `true` , `on`
* __Palsu__: `0` , , `no` `false` , `off`

Berikut adalah contoh file konfigurasi CLI yang menonaktifkan permintaan konfirmasi dan mengatur pembuatan log ke `/var/log/azure` direktori.

```ini
[core]
disable_confirm_prompt=Yes

[logging]
enable_log_file=yes
log_dir=/var/log/azure
```

Lihat bagian berikutnya untuk detail tentang semua nilai konfigurasi yang tersedia dan apa artinya. Untuk detail lengkap pada format file INI, lihat [dokumentasi Python di INI](https://docs.python.org/3/library/configparser.html#supported-ini-file-structure).

## <a name="cli-configuration-values-and-environment-variables"></a>Nilai konfigurasi CLI dan variabel lingkungan

Tabel berikut berisi semua bagian dan nama opsi yang dapat ditempatkan dalam file konfigurasi. Variabel lingkungan yang sesuai mereka ditetapkan `AZURE_{section}_{name}` sebagai, di semua topi. Misalnya, `output` default untuk `core` diatur dalam `AZURE_CORE_OUTPUT` variabel, default untuk diatur dalam `storage_account` `batchai` `AZURE_BATCHAI_STORAGE_ACCOUNT` variabel, dan default diatur dalam `location` `AZURE_DEFAULTS_LOCATION` variabel.

Ketika Anda memberikan nilai default, argumen itu tidak lagi diperlukan oleh perintah apa pun. Sebagai gantinya, nilai default digunakan.

| Bagian | Nama      | Jenis | Deskripsi|
|---------|-----------|------|------------|
| __inti__ | output | string | Format output default. Bisa menjadi salah `json` satu, `jsonc` , atau `tsv` `table` . |
| | menonaktifkan \_ \_ prompt konfirmasi | boolean | Aktifkan/nonaktifkan permintaan konfirmasi. |
| | mengumpulkan \_ telemetri | boolean | Izinkan Microsoft mengumpulkan data anonim tentang penggunaan CLI. Untuk informasi privasi, lihat [lisensi Azure CLI MIT](https://github.com/Azure/azure-cli/blob/dev/LICENSE). |
| | hanya \_ tampilkan \_ kesalahan | boolean | Hanya tampilkan kesalahan selama pemanggilan perintah. Dengan kata lain, hanya kesalahan yang akan ditulis untuk `stderr` . Ini menekan peringatan dari pratinjau, perintah usang dan eksperimental. Hal ini juga tersedia untuk perintah individu dengan `--only-show-errors` parameter. |
| | tidak ada \_ warna | boolean | Nonaktifkan warna. Awalnya pesan berwarna akan diawali dengan `DEBUG` , `INFO` , dan `WARNING` `ERROR` . Ini melewati masalah perpustakaan pihak ketiga di mana warna terminal tidak dapat kembali setelah `stdout` pengalihan. |
| __Penebangan__ | aktifkan \_ \_ berkas log | boolean | Aktifkan/nonaktifkan log. |
| | log \_ dir | string | Direktori untuk menulis log ke. Secara default nilai ini adalah `${AZURE_CONFIG_DIR}/logs*`. |
| __Default__ | grup | string | Grup sumber daya default untuk digunakan untuk semua perintah. |
| | lokasi | string | Lokasi default untuk digunakan untuk semua perintah. |
| | web | string | Nama aplikasi default untuk digunakan untuk `az webapp` perintah. |
| | Vm | string | Nama VM default yang akan digunakan untuk `az vm` perintah. |
| | vmss | string | Nama virtual machine scale set (VMSS) default untuk digunakan untuk `az vmss` perintah. |
| | acr | string | Nama registri kontainer default untuk digunakan untuk `az acr` perintah. |
| __penyimpanan__ | akun | string | Nama akun penyimpanan default (misalnya, **mystorageaccount** https://mystorageaccount.blob.core.windows.net) untuk digunakan untuk perintah bidang data `az storage` (misalnya, `az storage container list` ). |
| | kunci | string | Kunci akses default untuk digunakan untuk `az storage` perintah pesawat data. |
| | token sas \_ | string | Token SAS default untuk digunakan untuk `az storage` perintah pesawat data. |
| | string sambungan \_ | string | String koneksi default yang digunakan untuk `az storage` perintah bidang data. |
| __batchai__ | akun penyimpanan \_ | string | Akun penyimpanan default untuk digunakan untuk `az batchai` perintah. |
| | kunci penyimpanan \_ | string | Kunci penyimpanan default untuk digunakan untuk `az batchai` perintah. |
| __Batch__ | akun | string | Nama akun Azure Batch default untuk digunakan untuk `az batch` perintah. |
| | kunci akses \_ | string | Kunci akses default untuk digunakan untuk `az batch` perintah. Hanya digunakan dengan `aad` otorisasi. |
| | titik akhir | string | Titik akhir default untuk terhubung ke `az batch` perintah. |
| | mode auth \_ | string | Mode otorisasi untuk digunakan untuk `az batch` perintah. Bisa `shared_key` atau `aad`. |
| __awan__ | nama | string | Awan default untuk semua `az` perintah.  Nilai yang mungkin adalah  `AzureCloud` (default), `AzureChinaCloud` , `AzureUSGovernment` , `AzureGermanCloud` . Untuk mengubah awan, Anda dapat menggunakan `az cloud set –name` perintah.  Sebagai contoh, lihat [Mengelola Awan dengan Azure CLI](manage-clouds-azure-cli.md). |
| __Ekstensi__ | use_dynamic_install | string | Instal ekstensi jika belum ditambahkan saat menjalankan perintah darinya. Nilai yang mungkin adalah `no` (default), `yes_prompt` , `yes_without_prompt` . |
| | run_after_dynamic_install | boolean | Terus jalankan perintah saat ekstensi diinstal secara dinamis untuk itu. Defaultnya adalah `False`. |

> [!NOTE]
> Anda mungkin melihat nilai lain dalam file konfigurasi Anda, tetapi ini dikelola langsung melalui perintah CLI, termasuk `az config` . Yang tercantum dalam tabel di atas adalah satu-satunya nilai yang harus Anda ubah sendiri.

## <a name="see-also"></a>Lihat juga

- [Cara kerja dengan parameter Azure CLI tetap ada](param-persist-howto.md)
- [Tutorial: Gunakan parameter bertahan dengan perintah Azure CLI berurutan](param-persist-tutorial.md)

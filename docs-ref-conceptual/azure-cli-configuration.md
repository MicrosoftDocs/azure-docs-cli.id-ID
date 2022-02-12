---
title: Opsi konfigurasi Azure CLI | Microsoft Dokumen
description: Azure CLI memungkinkan konfigurasi pengguna untuk berbagai pengaturan. Kelola nilai dengan perintah az configure, variabel lingkungan, atau dalam file konfigurasi.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/01/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: variabel lingkungan, file konfigurasi, pengaturan konfigurasi, konfigurasi pengguna, variabel azure cli, konfigurasi azure cli, konfigurasi cli
ms.openlocfilehash: 080323052b92b3a0fcc68f644889bc48aaeff8d6
ms.sourcegitcommit: ad79327952adf0f8be8f1b9678e72434d9f03f0c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/12/2022
ms.locfileid: "138540908"
---
# <a name="azure-cli-configuration"></a>Konfigurasi CLI Azure

Azure CLI memungkinkan konfigurasi pengguna untuk pengaturan seperti pembuatan log, pengumpulan data, dan nilai argumen default. CLI menawarkan perintah kenyamanan untuk mengelola beberapa default, `az config`. Nilai lain dapat diatur dalam file konfigurasi atau dengan variabel lingkungan. Artikel ini memberikan informasi lebih lanjut tentang pengaturan konfigurasi pengguna ini dan cara mengonfigurasi Azure CLI.

Nilai konfigurasi yang digunakan oleh CLI dievaluasi sebagai prioritas berikut, dengan item yang lebih tinggi dalam daftar diprioritaskan.

1. Parameter baris perintah
1. Parameter nilai tetap yang ditetapkan dengan `az config param-persist`
1. Variabel lingkungan
1. Nilai dalam kumpulan file konfigurasi dengan `az config`

## <a name="cli-configuration-with-az-config"></a>CLI configuration with az config

Anda mengatur default untuk CLI dengan perintah [az config set](/cli/azure/config#az-config-set) .
Perintah ini mengambil daftar `key=value` pasangan yang terpisah ruang sebagai argumen. Nilai yang disediakan digunakan oleh CLI sebagai pengganti argumen yang diperlukan.

Tabel berikut berisi daftar kunci konfigurasi yang tersedia.

| Nama | Deskripsi |
|------|-------------|
| defaults.group | Grup sumber daya default yang akan digunakan untuk semua perintah. |
| defaults.location | Lokasi default yang akan digunakan untuk semua perintah. |
| defaults.web | Nama aplikasi default yang akan digunakan untuk `az webapp` perintah. |
| defaults.vm | Nama VM default yang akan digunakan untuk `az vm` perintah. |
| defaults.vmss | Nama pengaturan skala mesin virtual (VMSS) default untuk digunakan untuk  `az vmss` perintah. |
| defaults.acr | Nama registri kontainer default yang akan digunakan untuk `az acr` perintah. |

Misalnya, inilah cara Anda mengatur grup sumber daya default dan lokasi untuk semua perintah.

```azurecli-interactive
az config set defaults.location=westus2 defaults.group=MyResourceGroup
```

## <a name="cli-configuration-file"></a>Berkas konfigurasi CLI

File konfigurasi CLI berisi pengaturan lain yang digunakan untuk mengelola perilaku CLI. File konfigurasi itu sendiri terletak di `$AZURE_CONFIG_DIR/config`. Nilai `AZURE_CONFIG_DIR` default ada `$HOME/.azure` di Linux dan macOS, dan `%USERPROFILE%\.azure` pada Windows.

File konfigurasi ditulis dalam format file INI. Format file ini ditentukan oleh header bagian, diikuti oleh daftar entri nilai kunci.

* Header bagian ditulis sebagai `[section-name]`. Nama bagian peka huruf besar/kecil.
* Entri ditulis sebagai `key=value`. Nama-nama kunci tidak peka huruf besar/kecil.
* Komentar adalah setiap baris yang dimulai dengan `#` atau `;`. Komentar inline tidak diperbolehkan.

Booleans tidak peka terhadap kasus, dan diwakili oleh nilai-nilai berikut.

* __Benar__: `1`, `yes`, `true``on`
* __Salah__: `0`, `no`, `false``off`

Berikut adalah contoh file konfigurasi CLI yang menonaktifkan perintah konfirmasi dan menyiapkan log ke `/var/log/azure` direktori.

```ini
[core]
disable_confirm_prompt=Yes

[logging]
enable_log_file=yes
log_dir=/var/log/azure
```

Lihat bagian berikutnya untuk detail tentang semua nilai konfigurasi yang tersedia dan apa artinya. Untuk detail lengkap tentang format file INI, lihat [dokumentasi Python di INI](https://docs.python.org/3/library/configparser.html#supported-ini-file-structure).

## <a name="cli-configuration-values-and-environment-variables"></a>Nilai konfigurasi CLI dan variabel lingkungan

Tabel berikut berisi semua bagian dan nama opsi yang dapat ditempatkan dalam file konfigurasi. Variabel lingkungan yang sesuai ditetapkan sebagai `AZURE_{section}_{name}`, di semua topi. Misalnya, `output` default untuk `core` diatur dalam `AZURE_CORE_OUTPUT` variabel, `storage_account` default untuk `batchai` diatur dalam `AZURE_BATCHAI_STORAGE_ACCOUNT` variabel, dan default `location` diatur dalam `AZURE_DEFAULTS_LOCATION` variabel.

Saat Anda memberikan nilai default, argumen tersebut tidak lagi diperlukan oleh perintah apa pun. Sebagai gantinya, nilai default digunakan.

| Bagian | Nama      | Jenis | Deskripsi|
|---------|-----------|------|------------|
| __inti__ | output | string | Format output default. Bisa menjadi salah satu, `json``jsonc`, `tsv`atau`table`. |
| | disableconfirmprompt\_\_ | boolean | Aktifkan/nonaktifkan perintah konfirmasi. |
| | collecttelemetry\_ | boolean | Izinkan Microsoft mengumpulkan data anonim tentang penggunaan CLI. Untuk informasi privasi, lihat [lisensi Azure CLI MIT](https://github.com/Azure/azure-cli/blob/dev/LICENSE). |
| | onlyshowerrors\_\_ | boolean | Hanya tampilkan kesalahan selama pemanggilan perintah. Dengan kata lain, hanya kesalahan yang akan ditulis `stderr`. Ini menekan peringatan dari perintah pratinjau, usang dan eksperimental. Ini juga tersedia untuk perintah individual dengan `--only-show-errors` parameter. |
| | nocolor\_ | boolean | Nonaktifkan warna. Pesan yang awalnya berwarna akan diawali dengan `DEBUG`, `INFO`, dan `WARNING` `ERROR`. Ini melewati masalah pustaka pihak ketiga di mana warna terminal tidak dapat kembali setelah `stdout` pengalihan. |
| __Penebangan__ | enablelogfile\_\_ | boolean | Aktifkan/nonaktifkan logging. |
| | logdir\_ | string | Direktori untuk menulis log ke. Secara default nilai ini adalah `${AZURE_CONFIG_DIR}/logs*`. |
| __Default__ | group | string | Grup sumber daya default yang akan digunakan untuk semua perintah. |
| | lokasi | string | Lokasi default yang akan digunakan untuk semua perintah. |
| | web | string | Nama aplikasi default yang akan digunakan untuk `az webapp` perintah. |
| | Vm | string | Nama VM default yang akan digunakan untuk `az vm` perintah. |
| | vmss | string | Nama pengaturan skala mesin virtual (VMSS) default untuk digunakan untuk `az vmss` perintah. |
| | acr | string | Nama registri kontainer default yang akan digunakan untuk `az acr` perintah. |
| __penyimpanan__ | akun | string | Nama akun penyimpanan default (misalnya, **mystorageaccount** masuk https://mystorageaccount.blob.core.windows.net) untuk digunakan untuk `az storage` perintah bidang data (misalnya, `az storage container list`). |
| | kunci | string | Kunci akses default untuk digunakan untuk `az storage` perintah bidang data. |
| | sastoken\_ | string | Token SAS default yang akan digunakan untuk `az storage` perintah data-plane. |
| | connectionstring\_ | string | String koneksi default yang akan digunakan untuk `az storage` perintah data-plane. |
| __batchai__ | storageaccount\_ | string | Akun penyimpanan default yang akan digunakan untuk `az batchai` perintah. |
| | storagekey\_ | string | Kunci penyimpanan default yang akan digunakan untuk `az batchai` perintah. |
| __Batch__ | akun | string | Nama akun Azure Batch default yang akan digunakan untuk `az batch` perintah. |
| | accesskey\_ | string | Kunci akses default untuk digunakan untuk `az batch` perintah. Hanya digunakan dengan `aad` otorisasi. |
| | titik akhir | string | Titik akhir default untuk terhubung ke perintah `az batch` . |
| | authmode\_ | string | Mode otorisasi yang akan digunakan untuk `az batch` perintah. Bisa `shared_key` atau `aad`. |
| __awan__ | nama | string | Cloud default untuk semua `az` perintah.  Nilai yang mungkin adalah  `AzureCloud` (default), `AzureChinaCloud`, `AzureUSGovernment`, `AzureGermanCloud`. Untuk mengubah awan, Anda dapat menggunakan `az cloud set –name` perintah.  Misalnya, lihat [Mengelola Cloud dengan Azure CLI](manage-clouds-azure-cli.md). |
| __extension__ | use_dynamic_install | string | Instal ekstensi jika belum ditambahkan saat menjalankan perintah dari ekstensi tersebut. Nilai yang mungkin adalah `no` (default), `yes_prompt`, `yes_without_prompt`. |
| | run_after_dynamic_install | boolean | Terus jalankan perintah saat ekstensi diinstal secara dinamis untuk itu. Defaultnya adalah `False`. |

> [!NOTE]
> Anda mungkin melihat nilai lain dalam file konfigurasi Anda, tetapi ini dikelola langsung melalui perintah CLI, termasuk `az config`. Yang tercantum dalam tabel di atas adalah satu-satunya nilai yang harus Anda ubah sendiri.

## <a name="see-also"></a>Lihat juga

- [Cara kerja dengan parameter Azure CLI bertahan](param-persist-howto.md)
- [Tutorial: Gunakan parameter bertahan dengan perintah Azure CLI berurutan](param-persist-tutorial.md)

---
title: Opsi konfigurasi Azure CLI | Microsoft Docs
description: Azure CLI memungkinkan konfigurasi pengguna untuk berbagai pengaturan. Kelola nilai dengan perintah az configure, variabel lingkungan, atau dalam file konfigurasi.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/01/2021
ms.topic: conceptual
ms.service: azure-cli
ms.tool: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: variabel lingkungan, file konfigurasi, pengaturan konfigurasi, konfigurasi pengguna, variabel azure cli, konfigurasi azure cli, konfigurasi cli
ms.openlocfilehash: 16447afc17c87167783bfc64909d3a007989a75d
ms.sourcegitcommit: 4972b72ce712edcacb644e2e0fd8a51b9d7ec0d9
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 06/22/2022
ms.locfileid: "146542007"
---
# <a name="azure-cli-configuration"></a>Konfigurasi CLI Azure

Azure CLI memungkinkan konfigurasi pengguna untuk pengaturan seperti pengelogan, pengumpulan data, dan nilai argumen default. CLI menawarkan perintah kemudahan untuk mengelola beberapa default, `az config`. Nilai lain dapat diatur dalam file konfigurasi atau dengan variabel lingkungan. Artikel ini berisi informasi lebih lanjut tentang pengaturan konfigurasi pengguna ini dan cara mengonfigurasi Azure CLI.

Nilai konfigurasi yang digunakan oleh CLI dievaluasi dengan prioritas berikut, di mana item yang lebih tinggi diprioritaskan dalam daftar.

1. Parameter baris perintah
1. Parameter nilai tetap yang ditetapkan dengan `az config param-persist`
1. Variabel lingkungan
1. Nilai dalam file konfigurasi yang ditetapkan dengan `az config`

## <a name="cli-configuration-with-az-config"></a>Konfigurasi CLI dengan az config

Anda mengatur default untuk CLI dengan perintah [az config set](/cli/azure/config#az-config-set) .
Perintah ini menggunakan daftar yang dipisahkan spasi dari pasangan `key=value` sebagai argumen. Nilai yang disediakan digunakan oleh CLI sebagai pengganti argumen yang diperlukan.

Tabel berikut berisi daftar kunci konfigurasi yang tersedia.

| Nama | Deskripsi |
|------|-------------|
| defaults.group | Grup sumber daya default yang akan digunakan untuk semua perintah. |
| defaults.location | Lokasi default yang akan digunakan untuk semua perintah. |
| defaults.web | Nama aplikasi default yang akan digunakan untuk perintah `az webapp`. |
| defaults.vm | Nama VM default yang akan digunakan untuk perintah `az vm`. |
| defaults.vmss | Nama set skala mesin virtual (VMSS) default yang akan digunakan untuk perintah `az vmss`. |
| defaults.acr | Nama registri kontainer default yang akan digunakan untuk perintah `az acr`. |

Misalnya, berikut cara menetapkan grup sumber daya default dan lokasi untuk semua perintah.

```azurecli-interactive
az config set defaults.location=westus2 defaults.group=MyResourceGroup
```

Perintah berikut menonaktifkan tautan survei saat menjalankan perintah Azure CLI:

```azurecli-interactive
az config set output.show_survey_link=no
```

## <a name="cli-configuration-file"></a>File konfigurasi CLI

File konfigurasi CLI berisi pengaturan lain yang digunakan untuk mengelola perilaku CLI. File konfigurasinya terletak di `$AZURE_CONFIG_DIR/config`. Nilai default `AZURE_CONFIG_DIR` adalah `$HOME/.azure` di Linux dan macOS, dan `%USERPROFILE%\.azure` di Windows.

File konfigurasi ditulis dalam format file INI. Format file ini ditentukan oleh header bagian, diikuti oleh daftar entri nilai kunci.

* Header bagian ditulis sebagai `[section-name]`. Nama bagian peka huruf besar/kecil.
* Entri ditulis sebagai `key=value`. Nama kunci tidak peka huruf besar/kecil.
* Komentar adalah setiap baris yang dimulai dengan `#` atau `;`. Komentar sebaris tidak diperbolehkan.

Booleans peka huruf besar/kecil, dan diwakili oleh nilai berikut.

* __True__: `1`, `yes`, `true`, `on`
* __False__: `0`, `no`, `false`, `off`

Berikut contoh file konfigurasi CLI yang menonaktifkan semua permintaan konfirmasi dan menyiapkan pengelogan ke direktori `/var/log/azure`.

```ini
[core]
disable_confirm_prompt=Yes

[logging]
enable_log_file=yes
log_dir=/var/log/azure
```

Lihat bagian berikutnya untuk detail tentang semua nilai konfigurasi yang tersedia beserta artinya. Untuk detail lengkap tentang format file INI, lihat [Dokumentasi Python tentang INI](https://docs.python.org/3/library/configparser.html#supported-ini-file-structure).

## <a name="cli-configuration-values-and-environment-variables"></a>Nilai konfigurasi CLI dan variabel lingkungan

Tabel berikut berisi semua bagian dan nama opsi yang dapat ditempatkan dalam file konfigurasi. Variabel lingkungan yang sesuai ditetapkan sebagai `AZURE_{section}_{name}`, di semua batas. Misalnya, default `output` untuk `core` diatur dalam variabel `AZURE_CORE_OUTPUT`, default `storage_account` untuk `batchai` diatur dalam variabel `AZURE_BATCHAI_STORAGE_ACCOUNT`, dan default `location` diatur dalam variabel `AZURE_DEFAULTS_LOCATION`.

Saat Anda memasukkan nilai default, argumen tersebut tidak diperlukan lagi oleh perintah apa pun. Sebagai gantinya, nilai default akan digunakan.

| Bagian | Nama      | Jenis | Deskripsi|
|---------|-----------|------|------------|
| __inti__ | output | string | Format output default. Bisa berupa salah satu `json`, `jsonc`, `tsv`, atau `table`. |
| | disable\_confirm\_prompt | boolean | Mengaktifkan/menonaktifkan permintaan konfirmasi. |
| | collect\_telemetry | boolean | Mengizinkan Microsoft mengumpulkan data anonim tentang penggunaan CLI. Untuk informasi privasi, lihat [lisensi Azure CLI MIT](https://github.com/Azure/azure-cli/blob/dev/LICENSE). |
| | only\_show\_errors | boolean | Hanya tampilkan kesalahan selama pemanggilan perintah. Dengan kata lain, hanya kesalahan yang akan ditulis ke `stderr`. Ini menekan peringatan dari perintah pratinjau, yang tidak digunakan lagi dan percobaan. Ini juga tersedia untuk perintah individu dengan parameter `--only-show-errors`. |
| | no\_color | boolean | Nonaktifkan warna. Pesan yang awalnya berwarna akan diberi awalan `DEBUG`, `INFO`, `WARNING`, dan `ERROR`. Ini mengabaikan masalah pustaka pihak ketiga di mana warna terminal tidak dapat dipulihkan setelah pengalihan `stdout`. |
| __pengelogan__ | enable\_log\_file | boolean | Aktifkan/nonaktifkan pengelogan. |
| | log\_dir | string | Direktori tempat tujuan log ditulis. Secara default nilai ini adalah `${AZURE_CONFIG_DIR}/logs*`. |
| __default__ | group | string | Grup sumber daya default yang akan digunakan untuk semua perintah. |
| | lokasi | string | Lokasi default yang akan digunakan untuk semua perintah. |
| | web | string | Nama aplikasi default yang akan digunakan untuk perintah `az webapp`. |
| | vm | string | Nama VM default yang akan digunakan untuk perintah `az vm`. |
| | vmss | string | Nama set skala mesin virtual (VMSS) default yang akan digunakan untuk perintah `az vmss`. |
| | acr | string | Nama registri kontainer default yang akan digunakan untuk perintah `az acr`. |
| __penyimpanan__ | akun | string | Nama akun penyimpanan default (misalnya, **mystorageaccount** dalam https://mystorageaccount.blob.core.windows.net) yang digunakan untuk `az storage` perintah data-plane (misalnya, `az storage container list` ). |
| | kunci | string | Kunci akses default yang akan digunakan untuk perintah data-plane `az storage`. |
| | sas\_token | string | Token SAS default yang akan digunakan untuk perintah data-plane `az storage`. |
| | connection\_string | string | String koneksi default yang akan digunakan untuk perintah data-plane `az storage`. |
| __batchai__ | storage\_account | string | Akun penyimpanan default yang akan digunakan untuk perintah `az batchai`. |
| | storage\_key | string | Kunci penyimpanan default yang akan digunakan untuk perintah `az batchai`. |
| __batch__ | akun | string | Nama akun Azure Batch yang akan digunakan untuk perintah `az batch`. |
| | access\_key | string | Kunci akses default yang akan digunakan untuk perintah `az batch`. Hanya digunakan dengan otorisasi `aad`. |
| | titik akhir | string | Titik akhir default untuk terhubung untuk perintah `az batch`. |
| | auth\_mode | string | Mode otorisasi yang akan digunakan untuk perintah `az batch`. Bisa `shared_key` atau `aad`. |
| __cloud__ | nama | string | Cloud default untuk semua perintah `az`.  Kemungkinan nilainya adalah `AzureCloud` (default), `AzureChinaCloud`, `AzureUSGovernment`, `AzureGermanCloud`. Untuk mengubah cloud, Anda dapat menggunakan perintah `az cloud set –name`.  Misalnya, lihat [Mengelola Cloud dengan Azure CLI](manage-clouds-azure-cli.md). |
| __ekstensi__ | use_dynamic_install | string | Instal ekstensi jika belum ditambahkan saat menjalankan perintah darinya. Kemungkinan nilainya adalah `no` (default), `yes_prompt`, `yes_without_prompt`. |
| | run_after_dynamic_install | boolean | Terus jalankan perintah saat ekstensi diinstal secara dinamis untuknya. Defaultnya adalah `False`. |

> [!NOTE]
> Anda mungkin melihat nilai lain dalam file konfigurasi, tetapi ini dikelola langsung melalui perintah CLI, termasuk `az config`. Yang tercantum dalam tabel di atas hanya nilai yang harus Anda ubah sendiri.

## <a name="see-also"></a>Lihat juga

- [Cara bekerja dengan parameter yang dipertahankan Azure CLI](param-persist-howto.md)
- [Tutorial: Menggunakan parameter yang bertahan dengan perintah Azure CLI berurutan](param-persist-tutorial.md)

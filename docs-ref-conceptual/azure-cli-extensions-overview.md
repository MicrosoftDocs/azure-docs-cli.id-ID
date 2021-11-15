---
title: Cara menginstal dan mengelola ekstensi Azure CLI | Microsoft Docs
description: Pelajari cara menemukan, menginstal, menghapus instalasi, dan mengelola ekstensi dengan Azure CLI. Gunakan Azure CLI untuk memuat ekstensi yang disediakan dan dikelola oleh Microsoft.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/06/2020
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: mengelola ekstensi, ekstensi microsoft, install extensions, uninstall extensions, azure extensions, azure cli extensions
ms.openlocfilehash: 5f74238ab68951d3077cb7dacf70df9e0c56fce7
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439059"
---
# <a name="use-and-manage-extensions-with-the-azure-cli"></a>Menggunakan dan mengelola ekstensi dengan Azure CLI 

Azure CLI menawarkan kemampuan untuk memuat ekstensi. Ekstensi untuk Azure CLI dicirikan sebagai roda Python yang tidak dikirim sebagai bagian dari CLI tetapi dijalankan sebagai perintah CLI.
Dengan ekstensi, Anda mendapatkan akses ke perintah eksperimental dan pra-rilis bersama dengan kemampuan untuk menulis antarmuka CLI Anda sendiri. Artikel ini membahas cara mengelola ekstensi dan menjawab pertanyaan umum tentang penggunaannya.

## <a name="how-to-find-extensions"></a>Cara menemukan ekstensi

Untuk melihat ekstensi Azure CLI yang disediakan dan dikelola oleh Microsoft, gunakan perintah [daftar ekstensi az yang tersedia.](/cli/azure/extension#az_extension_list_available)

```azurecli-interactive
az extension list-available --output table
```

Kami juga meng-host [daftar ekstensi](azure-cli-extensions-list.md) di situs dokumentasi.

## <a name="how-to-install-extensions"></a>Cara menginstal ekstensi

### <a name="install-extensions-manually"></a>Instal ekstensi secara manual

Setelah Anda menemukan ekstensi untuk menginstal, gunakan [az extension add](/cli/azure/extension#az_extension_add) untuk mendapatkannya. Jika ekstensi tercantum pada `az extension list-available` tahun 2000, Anda dapat menginstal ekstensi dengan nama.

```azurecli-interactive
az extension add --name <extension-name>
```

Jika ekstensi berasal dari sumber daya eksternal atau Anda memiliki tautan langsung ke sana, berikan URL sumber atau jalur lokal. Ekstensi _harus_ menjadi file roda Python yang dikompilasi.

```azurecli-interactive
az extension add --source <URL-or-path>
```

Anda juga dapat membuat indeks ekstensi pribadi mengikuti format di [index.json,](https://github.com/Azure/azure-cli-extensions/blob/master/src/index.json)lalu mengatur URL indeks ekstensi yang digunakan oleh Azure CLI untuk itu mulai dari versi `2.20.0` . Setelah itu, Anda dapat menginstal ekstensi dengan nama dari indeks ekstensi pribadi.

```azurecli-interactive
az config set extension.index_url=<URL>
az extension add --name <extension-name>
```

Setelah ekstensi diinstal, itu ditemukan di bawah nilai `$AZURE_EXTENSION_DIR` variabel shell. Jika variabel ini tidak diset, secara default nilainya ada `$HOME/.azure/cliextensions` di Linux dan macOS, dan `%USERPROFILE%\.azure\cliextensions` pada Windows.

### <a name="install-extensions-automatically"></a>Instal ekstensi secara otomatis

Saat Anda menjalankan perintah ekstensi yang tidak diinstal, Azure CLI dapat mengenali perintah yang Anda jalankan, dan secara otomatis menginstal ekstensi untuk Anda mulai dari versi `2.10.0` . Fitur ini, disebut sebagai **instalasi dinamis,** diaktifkan secara default sejak `2.12.0` saat itu. Anda juga dapat mengaktifkannya melalui konfigurasi untuk versi yang didukung sebelumnya.
```azurecli-interactive
az config set extension.use_dynamic_install=yes_prompt
```

Gunakan perintah konfigurasi berikut untuk mengaktifkan penginstalan dinamis tanpa prompt.
```azurecli-interactive
az config set extension.use_dynamic_install=yes_without_prompt
```

Gunakan perintah konfigurasi berikut untuk menonaktifkan fitur penginstalan dinamis untuk kembali ke perilaku default. Perintah ekstensi akan mengembalikan kesalahan yang tidak ditemukan perintah jika ekstensi tidak diinstal.
```azurecli-interactive
az config set extension.use_dynamic_install=no
```

Secara default, perintah ekstensi yang meminta instalasi dinamis akan terus berjalan setelah ekstensi diinstal. Anda dapat mengubah perilaku default dan membuat perintah keluar tanpa tayangan ulang dengan mengatur `run_after_dynamic_install` properti ke `no` .
```azurecli-interactive
az config set extension.run_after_dynamic_install=no
```

## <a name="how-to-update-extensions"></a>Cara memperbarui ekstensi

Jika ekstensi diinstal berdasarkan nama, perbarui menggunakan [pembaruan ekstensi az](/cli/azure/extension#az_extension_update).

```azurecli-interactive
az extension update --name <extension-name>
```

Jika tidak, ekstensi dapat diperbarui dari sumber dengan mengikuti instruksi [Ekstensi Instalasi.](#how-to-install-extensions)

Jika nama ekstensi tidak dapat diselesaikan oleh CLI, hapus instalannya dan coba instal ulang. Perpanjangan juga bisa menjadi bagian dari CLI dasar.
Coba perbarui CLI seperti yang dijelaskan di [Instal Azure CLI](install-azure-cli.md) dan lihat apakah perintah ekstensi ditambahkan.

## <a name="how-to-uninstall-extensions"></a>Cara menghapus ekstensi

Jika Anda tidak lagi memerlukan ekstensi, hapus dengan [ekstensi az hapus.](/cli/azure/extension#az_extension_remove)

```azurecli-interactive
az extension remove --name <extension-name>
```

Anda juga dapat menghapus ekstensi secara manual dengan menghapusnya dari lokasi di mana ia diinstal. `$AZURE_EXTENSION_DIR`Variabel shell mendefinisikan di mana modul diinstal.
Jika variabel ini tidak diset, secara default nilainya ada `$HOME/.azure/cliextensions` di Linux dan macOS, dan `%USERPROFILE%\.azure\cliextensions` pada Windows.

```bash
rm -rf $AZURE_EXTENSION_DIR/<extension-name>
```

## <a name="faq"></a>FAQ

Berikut adalah beberapa jawaban atas pertanyaan umum lainnya tentang ekstensi CLI.

### <a name="what-file-formats-are-allowed-for-installation"></a>Format file apa yang diizinkan untuk instalasi?

Saat ini, hanya roda Python yang dikompilasi yang dapat dipasang sebagai ekstensi.

### <a name="can-extensions-replace-existing-commands"></a>Dapatkah ekstensi menggantikan perintah yang ada?

Ya. Ekstensi dapat menggantikan perintah yang ada, tetapi sebelum menjalankan perintah yang telah diganti CLI akan mengeluarkan peringatan.

### <a name="how-can-i-tell-if-an-extension-is-in-pre-release"></a>Bagaimana saya bisa tahu apakah ekstensi sudah ada sebelum rilis?

Dokumentasi dan versi ekstensi akan menunjukkan apakah itu di pra-rilis. Microsoft sering merilis perintah pratinjau sebagai ekstensi CLI, dengan opsi untuk memindahkannya ke produk CLI utama nanti. Ketika perintah dipindahkan dari ekstensi, ekstensi lama harus dihapus. 

### <a name="can-extensions-depend-upon-each-other"></a>Bisakah ekstensi bergantung satu sama lain?

Tidak. Karena CLI tidak menjamin urutan beban, dependensi mungkin tidak puas. Menghapus ekstensi tidak akan mempengaruhi orang lain.

### <a name="are-extensions-updated-along-with-the-cli"></a>Apakah ekstensi diperbarui bersama dengan CLI?

Tidak. Ekstensi harus diperbarui secara terpisah, seperti yang dijelaskan dalam [ekstensi Pembaruan.](#how-to-update-extensions)

### <a name="how-to-develop-our-own-extension"></a>Bagaimana cara mengembangkan ekstensi kita sendiri?
Silakan merujuk ke repositori resmi untuk bantuan lebih lanjut. [Azure/azure-cli-extensions](https://github.com/Azure/azure-cli/tree/master/doc/extensions)

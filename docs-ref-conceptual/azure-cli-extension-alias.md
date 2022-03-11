---
title: Ekstensi alias - Azure CLI | Microsoft Docs
description: Ekstensi alias memungkinkan pengguna menentukan perintah kustom untuk Azure CLI dengan menggunakan perintah yang sudah ada. Pelajari cara menggunakan ekstensi alias Azure CLI.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 9/21/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: ekstensi alias azure cli, ekstensi alias, perintah alias
ms.openlocfilehash: a4cc624fd8f71297248bc2b67b94fc882d9f4e8e
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439098"
---
# <a name="how-to-use-the-azure-cli-alias-extension"></a>Cara menggunakan ekstensi alias Azure CLI

Ekstensi alias memungkinkan pengguna menentukan perintah kustom untuk Azure CLI dengan menggunakan perintah yang sudah ada. Alias membantu menyederhanakan alur kerja dengan mengizinkan pintasan. Karena didukung oleh mesin template Jinja2, alias bahkan menawarkan pemrosesan argumen tingkat lanjut.

> [!NOTE]
> Saat ini, Ekstensi Alias dalam pratinjau publik. Fitur dan format file konfigurasi dapat berubah.

## <a name="install-the-alias-extension"></a>Menginstal ekstensi alias

Versi Azure CLI minimum yang diperlukan untuk menggunakan ekstensi alias adalah **2.0.28**. Untuk memeriksa versi CLI Anda, jalankan `az --version`. Jika Anda perlu memperbarui penginstalan, ikuti petunjuknya di [Menginstal Azure CLI](./install-azure-cli.md).

Instal ekstensi alias dengan perintah [az extension add](/cli/azure/extension#az_extension_add).

```azurecli-interactive
az extension add --name alias
```

Verifikasi penginstalan ekstensi dengan [az extension list](/cli/azure/extension#az_extension_list). Jika sudah diinstal dengan benar, ekstensi alias tersebut akan dicantumkan dalam output perintah.

```azurecli-interactive
az extension list --output table --query '[].{Name:name}'
```

```output
Name
------
alias
```

## <a name="keep-the-alias-extension-up-to-date"></a>Terus memperbarui ekstensi alias

Ekstensi alias sedang dalam pengembangan aktif dan versi barunya dirilis secara teratur. Versi baru tidak diinstal saat Anda memperbarui CLI. Instal pembaruan untuk ekstensi menggunakan [az extension update](/cli/azure/extension#az_extension_update).

```azurecli-interactive
az extension update --name alias
```

## <a name="manage-aliases-for-the-azure-cli"></a>Mengelola alias untuk Azure CLI

Ekstensi alias memungkinkan Anda membuat dan mengelola alias untuk perintah CLI lainnya. Untuk melihat semua perintah dan detail parameter yang tersedia, jalankan perintah alias dengan `--help`.

```azurecli-interactive
az alias --help
```

## <a name="create-simple-alias-commands"></a>Membuat perintah alias sederhana

Salah satu penggunaan alias adalah untuk mempersingkat grup perintah atau nama perintah yang ada. Misalnya, Anda dapat mempersingkat grup perintah `group` menjadi `rg` dan perintah `list`menjadi `ls`.

```azurecli-interactive
az alias create --name rg --command group
az alias create --name ls --command list
```

Alias yang baru ditentukan ini sekarang dapat digunakan di mana sesuai penentuannya.

```azurecli-interactive
az rg list
az rg ls
az vm ls
```

Jangan sertakan `az` sebagai bagian dari perintah alias.

Alias juga bisa berupa pintasan untuk perintah lengkap. Contoh berikutnya mencantumkan grup sumber daya yang tersedia beserta lokasinya dalam output tabel:

```azurecli-interactive
az alias create --name ls-groups --command "group list --query '[].{Name:name, Location:location}' --output table"
```

Sekarang `ls-groups` dapat dijalankan seperti perintah CLI lainnya.

```azurecli-interactive
az ls-groups
```

## <a name="create-an-alias-command-with-arguments"></a>Membuat perintah alias dengan argumen

Anda juga dapat menambahkan argumen posisional ke perintah alias dengan memasukkannya sebagai `{{ arg_name }}` dalam nama alias. Diperlukan spasi kosong di dalam tanda kurung kurawal.

```azurecli-interactive
az alias create --name "alias_name {{ arg1 }} {{ arg2 }} ..." --command "invoke_including_args"
```

Contoh alias berikutnya menunjukkan cara menggunakan argumen posisional untuk mendapatkan alamat IP publik untuk VM.

```azurecli-interactive
az alias create \
    --name "get-vm-ip {{ resourceGroup }} {{ vmName }}" \
    --command "vm list-ip-addresses --resource-group {{ resourceGroup }} --name {{ vmName }}
        --query [0].virtualMachine.network.publicIpAddresses[0].ipAddress"
```

Saat menjalankan perintah ini, Anda memberikan nilai ke argumen posisional.

```azurecli-interactive
az get-vm-ip MyResourceGroup MyVM
```

Anda juga dapat menggunakan variabel lingkungan dalam perintah alias, yang dievaluasi saat runtime. Contoh berikutnya menambahkan alias `create-rg`, yang membuat grup sumber daya dalam `eastus` dan menambahkan tag `owner`. Tag ini diberi nilai variabel lingkungan lokal `USER`.

```azurecli-interactive
az alias create \
    --name "create-rg {{ groupName }}" \
    --command "group create --name {{ groupName }} --location eastus --tags owner=\$USER"
```

Untuk mendaftarkan variabel lingkungan di dalam perintah alias, tanda mata uang dolar `$` harus dikeluarkan dari program.

## <a name="process-arguments-using-jinja2-templates"></a>Memproses argumen menggunakan template Jinja2

Penggantian argumen dalam ekstensi alias dilakukan oleh [Jinja2](http://jinja.pocoo.org/docs/2.10/). Template Jinja2 memungkinkan manipulasi argumen.

Dengan template Jinja2, Anda dapat menulis alias yang menggunakan berbagai jenis argumen daripada perintah yang mendasarinya. Misalnya, Anda dapat membuat alias yang menggunakan URL penyimpanan. Kemudian, URL ini diurai untuk meneruskan nama akun dan kontainer ke perintah penyimpanan.

```azurecli-interactive
az alias create \
    --name 'storage-ls {{ url }}' \
    --command "storage blob list
        --account-name {{ url.replace('https://', '').split('.')[0] }}
        --container-name {{ url.replace('https://', '').split('/')[1] }}"
```

Untuk mempelajari mesin template Jinja2, lihat [dokumentasi Jinja2](http://jinja.pocoo.org/docs/2.10/templates/).

## <a name="alias-configuration-file"></a>File konfigurasi alias

Cara lain untuk membuat dan memodifikasi alias adalah mengubah file konfigurasi alias. Definisi perintah alias ditulis ke dalam file konfigurasi, yang berada di `$AZURE_USER_CONFIG/alias`. Nilai default `AZURE_USER_CONFIG` adalah `$HOME/.azure` di macOS dan Linux, dan `%USERPROFILE%\.azure` di Windows. File konfigurasi alias ditulis dalam format file konfigurasi INI. Format untuk perintah alias adalah:

```ini
[alias_name]
command = invoked_commands
```

Untuk alias yang memiliki argumen posisional, format untuk perintah aliasnya adalah:

```ini
[alias_name {{ arg1 }} {{ arg2 }} ...]
command = invoked_commands_including_args
```

## <a name="create-an-alias-command-with-arguments-via-the-alias-configuration-file"></a>Membuat perintah alias dengan argumen melalui file konfigurasi alias

Contoh berikutnya menunjukkan alias untuk perintah dengan argumen. Perintah ini mendapatkan alamat IP publik untuk VM. Semua perintah alias harus berada di satu baris, dan menggunakan semua argumen dalam nama alias.

```ini
[get-vm-ip {{ resourceGroup }} {{ vmName }}]
command = vm list-ip-addresses --resource-group {{ resourceGroup }} --name {{ vmName }} --query [0].virtualMachine.network.publicIpAddresses[0].ipAddress
```

## <a name="uninstall-the-alias-extension"></a>Menghapus ekstensi alias

Untuk menghapus instalan ekstensi, gunakan perintah [az extension remove](/cli/azure/extension#az_extension_remove).

```azurecli-interactive
az extension remove --name alias
```

Jika Anda menghapus instalan dikarenakan terdapat bug atau masalah lain dengan ekstensi, [ajukan masalah GitHub](https://github.com/Azure/azure-cli-extensions/issues) agar kami dapat memperbaikinya.
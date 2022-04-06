---
title: Cara memperbarui Azure CLI | Microsoft Docs
description: Pelajari cara memperbarui Azure Command-Line Interface (CLI) dengan melakukan pembaruan manual atau mengaktifkan peningkatan otomatis untuk CLI.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 9/21/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: update azure cli
ms.openlocfilehash: 9c3d9a7946fefaaf5ebf927a90b6046121ee8cac
ms.sourcegitcommit: cbb162f5b74c5250338109317f06a152809c4b4c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/06/2022
ms.locfileid: "141397513"
---
# <a name="how-to-update-the-azure-cli"></a>Cara memperbarui Azure CLI

Anda dapat mengandalkan pengelola paket untuk memperbarui penginstalan lokal Azure CLI di lingkungan Windows, macOS, dan Linux (lihat bagian `Update` di setiap petunjuk penginstalan khusus platform). CLI juga dilengkapi dengan perintah dalam alat untuk meningkatkan versi secara manual atau otomatis.

## <a name="manual-update"></a>Pembaruan Manual
[!INCLUDE [az-upgrade](includes/az-upgrade.md)]

`az upgrade` didukung pada Windows, macOS dan beberapa distro Linux selama penginstalan didukung. Ini hanya mendukung peningkatan ke versi terbaru. Jika Azure CLI dijalankan melalui Azure Cloud Shell, kemungkinan besar Anda sudah menggunakan penginstalan Azure CLI terbaru. Jika bukan karena kasus seperti rilis ad-hoc dari versi perbaikan bug kecil, Anda harus menunggu build Azure Cloud Shell berikutnya karena `az upgrade` tidak didukung di Azure Cloud Shell.

Jika `azure-cli` sudah menjadi versi terbaru, eksekusi `az upgrade` akan memeriksa dan memperbarui semua [ekstensi](azure-cli-extensions-overview.md) yang diinstal.

## <a name="automatic-update"></a>Pembaruan Otomatis

Secara default, peningkatan otomatis untuk Azure CLI dinonaktifkan. Jika Anda ingin menggunakan versi terbaru, Anda dapat mengaktifkan peningkatan otomatis melalui [konfigurasi](../latest/docs-ref-autogen/config.yml).

```azurecli
az config set auto-upgrade.enable=yes
```

Azure CLI akan memeriksa versi baru secara rutin dan meminta Anda untuk meningkatkan versi setelah perintah selesai dijalankan setelah pembaruan tersedia.

Pesan permintaan dan pesan output selama peningkatan dapat mengganggu hasil perintah Anda jika ditetapkan ke beberapa variabel atau dalam alur otomatis. Untuk menghindari gangguan, Anda dapat menggunakan konfigurasi berikut agar pembaruan dapat berlangsung secara otomatis tanpa konfirmasi dan hanya menampilkan peringatan serta kesalahan selama peningkatan.

```azurecli
az config set auto-upgrade.prompt=no
```

Secara default, semua ekstensi yang diinstal juga akan diperbarui. Anda dapat menonaktifkan pembaruan ekstensi melalui konfigurasi.

```azurecli
az config set auto-upgrade.all=no
```

> [!NOTE]
> Tunggu hingga `az upgrade` selesai sebelum lanjut ke rangkaian perintah berikutnya, jika tidak, CLI versi baru (+ekstensi) mungkin memiliki perubahan yang rusak.

Jika memutuskan untuk tidak menggunakan fitur pembaruan otomatis lagi untuk kasus-kasus seperti menjaga skrip perintah berjalan stabil, Anda dapat menonaktifkannya melalui konfigurasi.
```azurecli
az config set auto-upgrade.enable=no
```
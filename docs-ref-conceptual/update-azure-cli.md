---
title: Cara memperbarui | Azure CLI Microsoft Docs
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
ms.openlocfilehash: 17770cca3553f91a701e6fdd710abda99ccc2487
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439089"
---
# <a name="how-to-update-the-azure-cli"></a>Cara memperbarui Azure CLI

Anda dapat mengandalkan manajer paket untuk memperbarui instalasi lokal Dari Azure CLI pada lingkungan Windows, macOS dan Linux (lihat `Update` bagian di setiap instruksi instalasi khusus platform). CLI juga menyediakan perintah dalam alat untuk meningkatkan secara manual atau otomatis.

## <a name="manual-update"></a>Pembaruan Manual
[!INCLUDE [az-upgrade](includes/az-upgrade.md)]

`az upgrade`didukung pada Windows, macOS dan beberapa distro Linux selama instalasi didukung. Ini hanya mendukung upgrade ke versi terbaru. Jika Anda menjalankan Azure CLI melalui Azure Cloud Shell, kemungkinan besar Anda sudah menggunakan instalasi Azure CLI terbaru. Jika bukan karena kasus seperti rilis ad-hoc dari versi perbaikan bug kecil, Anda harus menunggu build Azure Cloud Shell berikutnya karena `az upgrade` tidak didukung di Azure Cloud Shell.

Ketika `azure-cli` sudah versi terbaru, menjalankan akan memeriksa dan `az upgrade` memperbarui semua [ekstensi](azure-cli-extensions-overview.md)yang diinstal.

## <a name="automatic-update"></a>Pembaruan Otomatis

Secara default, upgrade otomatis untuk Azure CLI dinonaktifkan. Jika Anda ingin mengikuti versi terbaru, Anda dapat mengaktifkan upgrade otomatis melalui [konfigurasi.](/cli/azure/config)

```azurecli
az config set auto-upgrade.enable=yes
```

Azure CLI akan memeriksa versi baru secara teratur dan meminta Anda untuk meng-upgrade setelah perintah selesai berjalan setelah pembaruan tersedia.

Pesan cepat dan pesan output selama upgrade dapat mengganggu hasil perintah Anda jika ditugaskan ke beberapa variabel atau dalam aliran otomatis. Untuk menghindari gangguan, Anda dapat menggunakan konfigurasi berikut untuk memungkinkan pembaruan terjadi secara otomatis tanpa konfirmasi dan hanya menunjukkan peringatan dan kesalahan selama upgrade.

```azurecli
az config set auto-upgrade.prompt=no
```

Secara default, semua ekstensi yang diinstal juga akan diperbarui. Anda dapat menonaktifkan pembaruan ekstensi melalui konfigurasi.

```azurecli
az config set auto-upgrade.all=no
```

> [!NOTE]
> Harap tunggu `az upgrade` untuk menyelesaikan sebelum melanjutkan ke set perintah berikutnya, jika tidak versi baru dari CLI (+ekstensi) mungkin telah melanggar perubahan.

Jika Anda memutuskan untuk tidak menggunakan fitur pembaruan otomatis lagi untuk kasus-kasus seperti menjaga skrip perintah berjalan dengan stabil, Anda dapat mematikannya melalui konfigurasi.
```azurecli
az config set auto-upgrade.enable=no
```

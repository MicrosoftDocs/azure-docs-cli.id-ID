---
title: Cara menjalankan Azure CLI dalam | Kontainer Docker Microsoft Docs
description: Pelajari cara menjalankan wadah Docker yang menjadi tuan rumah Azure CLI. Docker membuat Anda mulai dengan cepat dengan lingkungan yang terisolasi untuk menjalankan Azure CLI.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli docker, docker azure cli
ms.openlocfilehash: 3c574978fe7d24666f3566c8c3777e66440e56b9
ms.sourcegitcommit: d2227bc475235bf86193e9cae5e02f349a6342e2
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 11/02/2021
ms.locfileid: "132439120"
---
# <a name="how-to-run-the-azure-cli-in-a-docker-container"></a>Cara menjalankan Azure CLI dalam wadah Docker

Anda dapat menggunakan Docker untuk menjalankan wadah Linux mandiri dengan Azure CLI pra-instal. Docker membuat Anda mulai dengan cepat dengan lingkungan yang terisolasi untuk menjalankan CLI. Gambar juga dapat digunakan sebagai dasar untuk penyebaran Anda sendiri.

## <a name="install-azure-cli-in-docker"></a>Install Azure CLI in Docker

> [!NOTE]
> Azure CLI telah bermigrasi ke [Microsoft Container Registry.](https://azure.microsoft.com/services/container-registry)
> Tag yang ada di Docker Hub masih didukung, tetapi rilis baru hanya akan tersedia sebagai mcr.microsoft.com/azure-cli.

Instal CLI menggunakan `docker run` .

   ```bash
   docker run -it mcr.microsoft.com/azure-cli
   ```

> [!NOTE]
> Jika Anda ingin mengambil kunci SSH dari lingkungan pengguna Anda, gunakan `-v ${HOME}/.ssh:/root/.ssh` untuk memasang kunci SSH Anda di lingkungan.
>
> ```bash
> docker run -it -v ${HOME}/.ssh:/root/.ssh mcr.microsoft.com/azure-cli
> ```

CLI diinstal pada gambar sebagai `az` perintah di `/usr/local/bin` .

## <a name="install-specific-version"></a>Menginstal versi tertentu

Versi yang tersedia dapat ditemukan di [catatan rilis Azure CLI](/cli/azure/release-notes-azure-cli).

Untuk menginstal versi tertentu:

```bash
docker run -it mcr.microsoft.com/azure-cli:<version>
```

## <a name="update-docker-image"></a>Memperbarui gambar Docker

Memperbarui dengan Docker membutuhkan menarik gambar baru dan membuat ulang wadah yang ada. Untuk alasan ini, Anda harus mencoba untuk menghindari menggunakan wadah yang meng-host CLI sebagai penyimpan data.

Perbarui gambar lokal Anda dengan `docker pull` .

```bash
docker pull mcr.microsoft.com/azure-cli
```

## <a name="uninstall-docker-image"></a>Hapus gambar Docker

[!INCLUDE [uninstall-boilerplate.md](includes/uninstall-boilerplate.md)]

Setelah menghentikan setiap kontainer yang menjalankan gambar CLI, lepaskan.

```bash
docker rmi mcr.microsoft.com/azure-cli
```

## <a name="next-steps"></a>Langkah berikutnya

Sekarang setelah Anda siap untuk menggunakan Azure CLI dalam wadah Docker, ikuti tur singkat dari fitur dan perintah umumnya.

> [!div class="nextstepaction"]
> [Mulai menggunakan Azure CLI](get-started-with-azure-cli.md)
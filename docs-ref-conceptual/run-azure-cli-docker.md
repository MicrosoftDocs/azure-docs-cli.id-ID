---
title: Cara menjalankan Azure CLI di Kontainer Docker | Microsoft Docs
description: Pelajari cara menjalankan kontainer Docker yang meng-host Azure CLI. Docker membantu Anda mulai menggunakan lingkungan terisolasi dengan cepat untuk menjalankan Azure CLI.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli docker, docker azure cli
ms.openlocfilehash: ae1774f73d3db81b48aa363b84b8d5b60cab41fd
ms.sourcegitcommit: cbb162f5b74c5250338109317f06a152809c4b4c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/06/2022
ms.locfileid: "141400653"
---
# <a name="how-to-run-the-azure-cli-in-a-docker-container"></a>Cara menjalankan Azure CLI di kontainer Docker

Anda dapat menggunakan Docker untuk menjalankan kontainer Linux mandiri dengan Azure CLI pra-instal. Dengan Docker, Anda dapat mulai menggunakan lingkungan terisolasi dengan cepat untuk menjalankan CLI. Citra ini juga dapat digunakan sebagai dasar untuk penyebaran Anda sendiri.

## <a name="install-azure-cli-in-docker"></a>Menginstal Azure CLI di Docker

> [!NOTE]
> Azure CLI telah dimigrasikan ke [Microsoft Container Registry](https://azure.microsoft.com/services/container-registry).
> Dukungan untuk tag yang ada di Hub Docker masih tersedia, tetapi rilis baru hanya akan tersedia sebagai mcr.microsoft.com/azure-cli.

Instal CLI menggunakan `docker run`.

   ```bash
   docker run -it mcr.microsoft.com/azure-cli
   ```

> [!NOTE]
> Jika Anda ingin mengambil kunci SSH dari lingkungan pengguna, gunakan `-v ${HOME}/.ssh:/root/.ssh` untuk memasang kunci SSH ke dalam lingkungan.
>
> ```bash
> docker run -it -v ${HOME}/.ssh:/root/.ssh mcr.microsoft.com/azure-cli
> ```

CLI diinstal pada citra sebagai perintah `az` dalam `/usr/local/bin`.

## <a name="install-specific-version"></a>Menginstal versi tertentu

Versi yang tersedia dapat ditemukan di [Catatan rilis Azure CLI](./release-notes-azure-cli.md).

Untuk menginstal versi tertentu:

```bash
docker run -it mcr.microsoft.com/azure-cli:<version>
```

## <a name="update-docker-image"></a>Memperbarui citra Docker

Pembaruan dengan Docker memerlukan penarikan citra baru dan pembuatan ulang kontainer yang sudah ada. Untuk alasan ini, sebaiknya jangan menggunakan kontainer yang meng-host CLI sebagai penyimpanan data.

Perbarui citra lokal Anda dengan `docker pull`.

```bash
docker pull mcr.microsoft.com/azure-cli
```

## <a name="uninstall-docker-image"></a>Menghapus instalan citra Docker

[!INCLUDE [uninstall-boilerplate.md](includes/uninstall-boilerplate.md)]

Setelah menghentikan kontainer apa pun yang menjalankan citra CLI, hapus.

```bash
docker rmi mcr.microsoft.com/azure-cli
```

## <a name="next-steps"></a>Langkah berikutnya

Sekarang Anda sudah siap menggunakan Azure CLI dalam kontainer Docker, ikuti tur singkat tentang fiturnya dan perintah umum.

> [!div class="nextstepaction"]
> [Mulai menggunakan Azure CLI](get-started-with-azure-cli.md)
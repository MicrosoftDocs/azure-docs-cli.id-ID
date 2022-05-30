---
title: Cara menjalankan Azure CLI di Kontainer Docker | Microsoft Docs
description: Pelajari cara menjalankan kontainer Docker yang meng-host Azure CLI. Docker membantu Anda mulai menggunakan lingkungan terisolasi dengan cepat untuk menjalankan Azure CLI.
author: jiasli
ms.author: jiasli
manager: yonzhan
ms.date: 04/08/2022
ms.topic: conceptual
ms.service: azure-cli
ms.tool: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli docker, docker azure cli
ms.openlocfilehash: 86c8b2740a0c5ce0391c35bb4437769ce0fa7b71
ms.sourcegitcommit: 6822e5d700742617eabda5904fe2ca217bae9d28
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/30/2022
ms.locfileid: "145938147"
---
# <a name="how-to-run-the-azure-cli-in-a-docker-container"></a>Cara menjalankan Azure CLI di kontainer Docker

Anda dapat menggunakan Docker untuk menjalankan kontainer Linux mandiri dengan Azure CLI pra-instal. Dengan Docker, Anda dapat mulai menggunakan lingkungan terisolasi dengan cepat untuk menjalankan CLI. Citra ini juga dapat digunakan sebagai dasar untuk penyebaran Anda sendiri.

## <a name="start-the-docker-container-with-azure-cli-pre-installed"></a>Memulai kontainer Docker dengan Azure CLI yang telah diinstal sebelumnya

> [!NOTE]
> Azure CLI telah dimigrasikan ke [Microsoft Container Registry](https://azure.microsoft.com/services/container-registry).
> Dukungan untuk tag yang ada di Hub Docker masih tersedia, tetapi rilis baru hanya akan tersedia sebagai mcr.microsoft.com/azure-cli.

Buka perintah lalu mulai kontainer Docker dengan Azure CLI yang telah diinstal sebelumnya menggunakan perintah berikut.

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

## <a name="run-the-docker-container-with-a-specific-version-of-the-azure-cli"></a>Jalankan kontainer Docker dengan versi Azure CLI tertentu

Versi yang tersedia dapat ditemukan di [catatan rilis Azure CLI](./release-notes-azure-cli.md).

Untuk menjalankan versi Azure CLI tertentu di kontainer Docker, gunakan yang berikut ini:

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

---
title: Menginstal Azure CLI di Linux | Microsoft Docs
description: Pelajari cara menginstal dan menjalankan Azure CLI di Linux secara manual. Anda dapat menginstal Azure CLI di komputer Linux dengan satu perintah atau proses langkah demi langkah.
author: jiasli
ms.author: jiasli
manager: yonzhan
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
zone_pivot_group_filename: azure/zone-pivot-groups.json
zone_pivot_groups: cli-linux-installation-method
keywords: linux cli, azure cli linux, menginstal azure cli ubuntu, menginstal azure cli linux
ms.openlocfilehash: 197c520a7fae534bf421f102dc7641dee6e3e97d
ms.sourcegitcommit: a805041ebd77f92fa4b3025ba6856ea4aedae2ac
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/22/2022
ms.locfileid: "144003553"
---
# <a name="install-the-azure-cli-on-linux"></a>Menginstal Azure CLI di Linux

Azure CLI adalah alat baris perintah lintas platform yang dapat diinstal secara lokal di komputer Linux. Anda dapat menggunakan Azure CLI di Linux untuk terhubung ke Azure dan menjalankan perintah administratif di sumber daya Azure. CLI di Linux memungkinkan eksekusi berbagai perintah melalui terminal menggunakan permintaan baris perintah interaktif atau skrip.
Jika sudah siap menginstal Azure CLI di Linux, sebaiknya Anda menggunakan pengelola paket distribusi Linux. Pilih pengelola paket distribusi yang tepat dari opsi di atas.  Jika tidak memiliki salah satu pengelola paket yang tercantum, Anda dapat menginstal Azure CLI secara manual di Linux dengan memilih opsi *Instal skrip*.

[!INCLUDE [current-version](includes/current-version.md)]

::: zone pivot="apt"

[!INCLUDE [cli-install-linux-apt](includes/cli-install-linux-apt.md)]

::: zone-end

::: zone pivot="dnf"

[!INCLUDE [cli-install-linux-apt](includes/cli-install-linux-dnf.md)]

::: zone-end

::: zone pivot="zypper"

[!INCLUDE [cli-install-linux-apt](includes/cli-install-linux-zypper.md)]

::: zone-end

::: zone pivot="script"

[!INCLUDE [cli-install-linux-apt](includes/cli-install-linux-script.md)]

::: zone-end

## <a name="remove-data"></a>Menghapus data

Jika Anda tidak ingin memasang ulang Azure CLI, hapus datanya.

```bash
rm -rf ~/.azure
```

## <a name="next-steps"></a>Langkah berikutnya

Setelah menginstal Azure CLI, ikuti tur singkat tentang fiturnya dan perintah umum.

> [!div class="nextstepaction"]
> [Mulai menggunakan Azure CLI](get-started-with-azure-cli.md)

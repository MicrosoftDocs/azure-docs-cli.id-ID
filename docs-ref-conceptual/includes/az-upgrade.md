---
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 09/25/2020
ms.topic: include
ms.openlocfilehash: 3aff8ec19c2ad5b86588d1299df4551966596d2c
ms.sourcegitcommit: cbb162f5b74c5250338109317f06a152809c4b4c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/06/2022
ms.locfileid: "141397510"
---
CLI menyediakan perintah dalam alat untuk memperbarui ke versi terbaru:

```azurecli
az upgrade
```

> [!NOTE]
>
> Perintah `az upgrade` ditambahkan dalam versi 2.11.0 dan tidak akan berfungsi dengan versi sebelum 2.11.0. Versi lama dapat diperbarui dengan memasang ulang seperti yang dijelaskan di [Memasang Azure CLI](../install-azure-cli.md).
>
> Perintah ini juga akan memperbarui semua ekstensi yang diinstal secara default. Untuk opsi `az upgrade` lebih lanjut, lihat [halaman referensi perintah](/cli/azure/reference-index#az_upgrade).
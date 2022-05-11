---
author: jiasli
ms.author: jiasli
manager: yonzhan
ms.date: 04/29/2022
ms.topic: include
ms.custom: devx-track-azurecli
ms.openlocfilehash: 541cd98a5c55220a83b3553fb82538bec5df3114
ms.sourcegitcommit: 458438e54726db3a020b476922b529b514b512d8
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/11/2022
ms.locfileid: "144850567"
---
## <a name="overview"></a>Gambaran Umum

RPM dirilis untuk [CBL-Mariner](https://github.com/microsoft/CBL-Mariner) 1.0 dan 2.0.

## <a name="install"></a>Instal

Instal dengan `tdnf install` perintah :

```bash
sudo tdnf install azure-cli
```

## <a name="install-specific-version"></a>Menginstal versi tertentu

Versi yang tersedia dapat ditemukan di [Catatan rilis Azure CLI](../release-notes-azure-cli.md).

Untuk melihat versi yang tersedia dengan perintah:

```bash
tdnf list azure-cli
```

Untuk menginstal versi tertentu:

```bash
sudo tdnf install azure-cli-<version>-1
```

## <a name="update"></a>Pembaruan

Perbarui Azure CLI dengan `tdnf update` perintah:

```bash
sudo tdnf update azure-cli
```

## <a name="uninstall"></a>Hapus instalasi

[!INCLUDE [uninstall-boilerplate.md](uninstall-boilerplate.md)]

Hapus paket dari sistem Anda:

```bash
sudo tdnf remove azure-cli
```

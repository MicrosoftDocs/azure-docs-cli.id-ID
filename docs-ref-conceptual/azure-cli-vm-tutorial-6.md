---
title: Membersihkan sumber daya mesin virtual (VM) – Azure CLI | Microsoft Docs
description: Bersihkan sumber daya yang digunakan dalam tutorial mesin virtual.
ms.date: 11/12/2021
ms.author: dbradish
author: dbradish-microsoft
manager: barbkess
ms.tool: azure-cli
ms.topic: tutorial
ms.prod: azure
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli membersihkan sumber daya, mesin virtual di azure cli
ms.openlocfilehash: 060f36738915dc93a0b6d2024e11726c6ebd45af
ms.sourcegitcommit: 6822e5d700742617eabda5904fe2ca217bae9d28
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/30/2022
ms.locfileid: "145939028"
---
# <a name="6---cleanup"></a>6 - Pembersihan

Setelah tutorial selesai, saatnya untuk membersihkan sumber daya yang dibuat. Anda dapat menghapus sumber daya satu per satu dengan perintah `delete`, tetapi cara teraman untuk menghapus semua sumber daya dalam grup sumber daya adalah dengan `group delete`.

```azurecli-interactive
az group delete --name $resourceGroup --no-wait
```

Perintah ini akan menghapus sumber daya yang dibuat selama tutorial, dan dijamin akan menghapus alokasinya dengan urutan yang benar. Parameter `--no-wait` mencegah CLI terblokir saat penghapusan berlangsung. Jika Anda ingin menunggu hingga penghapusan selesai atau melihat kemajuannya, gunakan perintah `group wait`.

```azurecli-interactive
az group wait --name $resourceGroup --deleted
```

Jika pembersihan selesai, berarti tutorial ini selesai. Lanjutkan dengan ringkasan semua hal yang dipelajari dan tautan ke sumber daya yang akan membantu Anda melalui langkah berikutnya.

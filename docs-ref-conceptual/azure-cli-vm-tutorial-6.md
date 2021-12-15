---
title: Cleanup virtual machine resources (VM) – Azure CLI | Microsoft Docs
description: Bersihkan sumber daya yang digunakan dalam tutorial mesin virtual.
ms.date: 11/12/2021
ms.author: dbradish
author: dbradish-microsoft
manager: barbkess
ms.devlang: azure-cli
ms.topic: tutorial
ms.prod: azure
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli clean up resources, virtual machine in azure cli
ms.openlocfilehash: 3bb61e9ede907c1e95fb21b85d51c225161fa957
ms.sourcegitcommit: 62469e9c1ad07f215129ece5db89c530f1a77968
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 12/15/2021
ms.locfileid: "135157667"
---
# <a name="6---cleanup"></a>6 - Pembersihan

Sekarang setelah tutorial selesai, saatnya untuk membersihkan sumber daya yang dibuat. Anda dapat menghapus sumber daya individual dengan `delete` perintah, tetapi cara paling aman untuk menghapus semua sumber daya dalam grup sumber daya adalah dengan `group delete` .

```azurecli-interactive
az group delete --name $resourceGroup --no-wait
```

Perintah ini menghapus sumber daya yang dibuat selama tutorial, dan dijamin untuk menanganinya dalam urutan yang benar. `--no-wait`Parameter menjaga CLI dari pemblokiran saat penghapusan berlangsung. Jika Anda ingin menunggu sampai penghapusan selesai atau saksikan kemajuannya, gunakan `group wait` perintah.

```azurecli-interactive
az group wait --name $resourceGroup --deleted
```

Dengan pembersihan selesai, tutorial selesai. Lanjutkan untuk ringkasan semua yang Anda pelajari dan tautan ke sumber daya yang akan membantu Anda dengan langkah selanjutnya.

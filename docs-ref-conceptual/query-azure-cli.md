---
title: Hasil perintah kueri JMESPath dengan Azure CLI | Microsoft Docs
description: Azure CLI menggunakan argumen --lakukan kueri pada argumen untuk menjalankan kueri JMESPath pada hasil perintah. Pelajari cara menggunakan fitur JMESPath di artikel ini.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 04/14/2022
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: ''
ms.openlocfilehash: 52fe1f3db96aaabce56f0b5c090d7190765f5bdc
ms.sourcegitcommit: a805041ebd77f92fa4b3025ba6856ea4aedae2ac
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/22/2022
ms.locfileid: "144003461"
---
# <a name="how-to-query-azure-cli-command-output-using-a-jmespath-query"></a>Cara mengkueri output perintah Azure CLI menggunakan kueri JMESPath

Azure CLI menggunakan `--query` parameter untuk menjalankan [kueri JMESPath](http://jmespath.org) pada hasil perintah. JMESPath adalah bahasa kueri untuk JSON, memberi Anda kemampuan untuk memilih dan mengubah data dari output CLI.

Parameter `--query` didukung oleh semua perintah di Azure CLI. Artikel ini membahas cara menggunakan fitur JMESPath dan memberikan contoh kueri. Pelajari tentang konsep JMESPath yang berguna untuk kueri di bawah tab konsep. Lihat contoh kueri JMESPath di bawah tab contoh.

# <a name="concepts"></a>[Konsep](#tab/concepts)

[!INCLUDE [Query Concepts](includes/query-azure-cli-concepts.md)]

# <a name="examples"></a>[Contoh](#tab/examples)

[!INCLUDE [Query Examples](includes/query-azure-cli-examples.md)]

---

## <a name="next-steps"></a>Langkah berikutnya

Untuk mempelajari selengkapnya tentang kueri JMESPath, lihat [Tutorial JMESPath](https://jmespath.org/tutorial.html).

Untuk mempelajari selengkapnya tentang konsep Azure CLI lain yang disebutkan dalam artikel ini lihat:

- [Format output untuk perintah Azure CLI](./format-output-azure-cli.md)
- [Cara menggunakan Azure CLI secara efektif](./use-cli-effectively.md)
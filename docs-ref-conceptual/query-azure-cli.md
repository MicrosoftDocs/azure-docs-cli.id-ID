---
title: Hasil perintah kueri JMESPath dengan Azure CLI | Microsoft Docs
description: Azure CLI menggunakan argumen --lakukan kueri pada argumen untuk menjalankan kueri JMESPath pada hasil perintah. Pelajari cara menggunakan fitur JMESPath di artikel ini.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 04/14/2022
ms.topic: conceptual
ms.service: azure-cli
ms.tool: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: ''
ms.openlocfilehash: 08e46d62f396a0d8d9eea1fdaa85d01abca580ba
ms.sourcegitcommit: 6822e5d700742617eabda5904fe2ca217bae9d28
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/30/2022
ms.locfileid: "145937840"
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

* [Format output untuk perintah Azure CLI](./format-output-azure-cli.md)
* [Cara menggunakan Azure CLI secara efektif](./use-cli-effectively.md)
* [Pelajari cara menggunakan Bash dengan Azure CLI](./azure-cli-learn-bash.md)

---
title: Perbedaan antara produk Azure CLI | Microsoft Docs
description: Pahami bagaimana nama dan versi produk Azure CLI ditentukan, serta cara produk tersebut ditingkatkan.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 9/21/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure, cli, baris perintah
ms.openlocfilehash: f8b989b907353b83e6f3d48ca89a8db246ca16aa
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439082"
---
# <a name="differences-between-azure-cli-products"></a>Perbedaan antara produk Azure CLI

Di akhir bulan Juni 2018, nomor versi eksplisit telah dihapus dari nama produk Azure CLI. Perubahan ini membantu menghilangkan kebingungan yang terkadang muncul dalam dokumentasi tempat pengguna diminta menggunakan "Azure CLI" tetapi tidak jelas versi produk apa yang menjadi rujukan. Jika Anda tidak asing dengan nama produk lama, berikut beberapa perubahannya:

* Azure CLI versi 2.0 dan yang lebih baru kini hanya disebut sebagai "Azure CLI."
* Versi Azure CLI sebelumnya (1.x dan versi sebelumnya) kini disebut sebagai "Azure classic CLI."

Perubahan nama ke Azure classic CLI memperjelas bahwa alat ini dimaksudkan untuk digunakan hanya dengan model penyebaran klasik. Azure classic CLI juga tidak diperbarui atau dikelola lagi. Untuk alasan ini, dan berbagai alasan lainnya, sebaiknya Anda memindahkan penyebaran klasik apa pun untuk menggunakan model Azure Resource Manager dan bermigrasi ke Azure CLI versi terbaru yang tersedia.

Jika masih menggunakan Azure classic CLI, Anda dapat mempelajari proses migrasi di artikel berikut:

* [Bermigrasi dari Classic ke Azure Resource Manager](/azure/virtual-machines/linux/migration-classic-resource-manager-overview)
* [Memasang CLI Azure](install-azure-cli.md)
* [Bermigrasi dari Azure classic CLI ke Azure CLI](https://github.com/Azure/azure-cli/blob/dev/doc/classic_cli_migration.md)

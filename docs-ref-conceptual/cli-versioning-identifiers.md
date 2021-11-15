---
title: Perbedaan antara produk Azure CLI | Microsoft Docs
description: Pahami bagaimana produk Azure CLI diberi nama dan versi, dan cara meng-upgrade.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 9/21/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure, cli, command line
ms.openlocfilehash: f8b989b907353b83e6f3d48ca89a8db246ca16aa
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439082"
---
# <a name="differences-between-azure-cli-products"></a>Perbedaan antara produk Azure CLI

Pada akhir Juni 2018, nomor versi eksplisit telah dihapus dari nama produk Azure CLI. Perubahan ini membantu menghilangkan kebingungan yang kadang-kadang muncul dalam dokumentasi di mana pengguna diberitahu untuk menggunakan "Azure CLI" tetapi tidak jelas versi produk apa yang dirujuk. Jika Anda terbiasa dengan nama produk lama, berikut adalah bagaimana mereka telah berubah:

* Azure CLI versi 2.0 dan yang lebih baru sekarang hanya disebut sebagai "Azure CLI."
* Versi Azure CLI sebelumnya (1.x dan lebih rendah) sekarang disebut sebagai "Azure classic CLI."

Perubahan nama menjadi Azure CLASSIC CLI memperjelas bahwa alat ini dimaksudkan untuk digunakan hanya dengan model penyebaran klasik. CLI klasik juga tidak lagi diperbarui atau dipelihara. Untuk alasan ini, dan banyak lagi, disarankan agar Anda memindahkan penyebaran klasik apa pun untuk menggunakan model Azure Resource Manager dan bermigrasi ke versi terbaru yang tersedia dari Azure CLI.

Jika Anda masih menggunakan CLI klasik, Anda dapat mempelajari tentang proses migrasi dalam artikel berikut:

* [Bermigrasi dari Classic ke Azure Resource Manager](/azure/virtual-machines/linux/migration-classic-resource-manager-overview)
* [Memasang CLI Azure](install-azure-cli.md)
* [Migrating from Azure classic CLI to Azure CLI](https://github.com/Azure/azure-cli/blob/dev/doc/classic_cli_migration.md)

---
title: Membuat mesin virtual (VM) pada prasyarat jaringan virtual (VNet) – Azure CLI | Microsoft Docs
description: Prasyarat untuk membuat mesin virtual (VM) di jaringan virtual (VNet) dengan Azure CLI.
ms.date: 11/12/2021
ms.author: dbradish
author: dbradish-microsoft
manager: barbkess
ms.devlang: azure-cli
ms.topic: tutorial
ms.prod: azure
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli create vm, mesin virtual di azure cli, variabel shell
ms.openlocfilehash: b4c034fe26db1e9b047656d74ce718d6912dcd7e
ms.sourcegitcommit: 013ae480807b6745bf8786b0ffc4362af301f8e8
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/04/2022
ms.locfileid: "144764710"
---
# <a name="1---overview-and-prerequisites"></a>1 - Ringkasan dan Prasyarat

Dalam tutorial ini, Anda akan mempelajari cara membuat jaringan virtual (VNet) dan menyebarkan mesin virtual (VM) ke VNet dengan Azure CLI. Tutorial ini juga membahas konsep spesifik Azure CLI seperti variabel shell dan kueri output.

Tutorial ini dapat diselesaikan dengan pengalaman interaktif yang ditawarkan melalui Azure Cloud Shell, atau Anda dapat [menginstal CLI](install-azure-cli.md) secara lokal.

Gunakan __ctrl-shift-v__ (__cmd-shift-v__ di macOS) untuk menempelkan teks tutorial ke dalam Azure Cloud Shell.

[!INCLUDE [azure-cli-prepare-your-environment.md](./includes/azure-cli-prepare-your-environment.md)]

## <a name="shell-variables"></a>Variabel shell

Variabel Shell menyimpan nilai untuk digunakan di lain waktu dan dapat digunakan untuk meneruskan nilai ke parameter perintah. Variabel Shell memungkinkan penggunaan kembali perintah, baik secara mandiri maupun dalam skrip. Tutorial ini menggunakan variabel shell untuk penyesuaian parameter perintah yang lebih mudah. Untuk menggunakan nilai parameter Anda sendiri alih-alih menggunakan nilai yang disediakan, ubah nilai yang ditetapkan untuk variabel shell. Untuk informasi selengkapnya tentang variabel shell, lihat [Menggunakan variabel shell](./azure-cli-variables.md#use-shell-variables).

## <a name="create-a-resource-group"></a>Buat grup sumber daya

Di Azure, semua sumber daya dialokasikan dalam grup pengelolaan sumber daya. Grup sumber daya menyediakan pengelompokan sumber daya logis yang membuatnya lebih mudah dikerjakan sebagai koleksi. Gunakan perintah [az group create](/cli/azure/group#az_group_create) untuk membuat grup sumber daya bernama `VMTutorialResources`.

```azurecli
# create shell variables
resourceGroup=VMTutorialResources
location=eastus

az group create --name $resourceGroup --location $location
 ```

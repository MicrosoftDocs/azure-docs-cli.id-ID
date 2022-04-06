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
ms.openlocfilehash: ad9fc5a6149d74cabd85ca353dd475db2d9e3277
ms.sourcegitcommit: cbb162f5b74c5250338109317f06a152809c4b4c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/06/2022
ms.locfileid: "141398433"
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
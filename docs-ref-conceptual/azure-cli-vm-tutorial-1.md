---
title: Buat mesin virtual (VM) pada prasyarat jaringan virtual (VNet) – Azure CLI | Microsoft Docs
description: Prasyarat untuk membuat mesin virtual (VM) pada jaringan virtual (VNet) dengan Azure CLI.
ms.date: 11/12/2021
ms.author: dbradish
author: dbradish-microsoft
manager: barbkess
ms.devlang: azure-cli
ms.topic: tutorial
ms.prod: azure
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli create vm, virtual machine in azure cli, shell variables
ms.openlocfilehash: 77249be43452151eeaa147912f9e76489fb56441
ms.sourcegitcommit: 62469e9c1ad07f215129ece5db89c530f1a77968
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 12/15/2021
ms.locfileid: "135157733"
---
# <a name="1---overview-and-prerequisites"></a>1 - Gambaran Umum dan Prasyarat

Dalam tutorial ini, Anda akan belajar cara membuat jaringan virtual (VNet) dan menyebarkan mesin virtual (VM) ke VNet dengan Azure CLI. Tutorial ini juga mencakup konsep spesifik Azure CLI seperti variabel shell dan kueri output.

Tutorial ini dapat diselesaikan dengan pengalaman interaktif yang ditawarkan melalui Azure Cloud Shell, atau Anda dapat [menginstal CLI](install-azure-cli.md) secara lokal.

Gunakan __ctrl-shift-v__ (__cmd-shift-v__ di macOS) untuk menempelkan teks tutorial ke Azure Cloud Shell.

[!INCLUDE [azure-cli-prepare-your-environment.md](./includes/azure-cli-prepare-your-environment.md)]

## <a name="shell-variables"></a>Variabel shell

Variabel Shell menyimpan nilai untuk penggunaan di masa mendatang dan dapat digunakan untuk meneruskan nilai ke parameter perintah. Variabel Shell memungkinkan penggunaan kembali perintah, baik sendiri maupun dalam skrip. Tutorial ini menggunakan variabel shell untuk kustomisasi parameter perintah yang lebih mudah. Untuk menggunakan nilai parameter Anda sendiri alih-alih menggunakan nilai yang disediakan, ubah nilai yang ditetapkan ke variabel shell. Untuk informasi selengkapnya tentang variabel shell lihat [Menggunakan variabel shell](/cli/azure/azure-cli-variables#use-shell-variables).

## <a name="create-a-resource-group"></a>Buat grup sumber daya

Di Azure, semua sumber daya dialokasikan dalam kelompok manajemen sumber daya. Kelompok sumber daya menyediakan pengelompokan sumber daya logis yang membuat mereka lebih mudah untuk bekerja sebagai koleksi. Gunakan perintah [buat grup az](/cli/azure/group#az_group_create) untuk membuat grup sumber daya bernama `VMTutorialResources` .

```azurecli
# create shell variables
resourceGroup=VMTutorialResources
location=eastus

az group create --name $resourceGroup --location $location
 ```

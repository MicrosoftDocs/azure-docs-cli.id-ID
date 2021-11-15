---
title: Azure CLI references for Azure IoT | Microsoft Docs
description: Cari perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure IoT. Dengan lebih dari 100 perintah berbeda yang tersedia, Anda dapat bekerja secara efektif dengan Azure IoT dari baris perintah.
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: paymaun.heidari
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli references, azure iot, azure maps, azure tsi
ms.openlocfilehash: aa50cced3f624c973973a30b53fa12ad798afb09
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439095"
---
# <a name="azure-cli-reference-commands-for-azure-iot"></a>Azure CLI reference commands for Azure IoT

Azure Command-Line Interface[(CLI)](./what-is-azure-cli.md)adalah seperangkat perintah yang digunakan untuk membuat dan mengelola sumber daya Azure untuk banyak layanan Azure. Untuk Azure IoT, lebih dari 100 perintah berbeda tersedia, yang memberi Anda kemampuan untuk bekerja secara efektif dengan layanan dari baris perintah.

Perintah Azure CLI untuk [Azure IoT](/azure/iot-fundamentals/) terdiri dari dua bagian: Azure CLI (biasa disebut sebagai **inti** CLI) dan **ekstensi** Azure CLI untuk IoT.

Fungsi IoT di **inti** Azure CLI difokuskan pada manajemen dan konfigurasi infrastruktur. Operasi IoT Hub CRUD, atau mengkonfigurasi rute pesan IoT Hub adalah kasus penggunaan khas untuk perintah inti.

Ekstensi Azure **CLI** untuk IOT memperkenalkan fitur dan fungsionalitas yang kaya untuk mengelola, memanipulasi, dan berinteraksi dengan data, entitas, dan objek pada infrastruktur itu sendiri. Misalnya, mengelola armada perangkat, memantau peristiwa perangkat-ke-cloud, dan menerapkan metode cloud to device semuanya diaktifkan melalui ekstensi IoT. Ekstensi Azure CLI untuk IoT membuka penggunaan teknologi eksperimental atau pra-rilis, yang berkontribusi pada fleksibilitasnya dalam berbagai skenario dan kasus penggunaan. Ekstensi Azure CLI secara otomatis diinstal saat pertama kali Anda menjalankan referensi ekstensi. Untuk informasi selengkapnya tentang referensi ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

> [!NOTE]
> Anda diminta untuk menginstal referensi ekstensi pada penggunaan pertama. Atau, Anda dapat menggunakan `az extension add` perintah untuk menginstal ekstensi secara manual.

## <a name="reference-command-list"></a>Daftar perintah Referensi

Daftar referensi Azure CLI yang dapat digunakan untuk mengelola Azure IoT, jenis referensi dan deskripsi referensi:

| Referensi | Inti atau ekstensi | Deskripsi
|-|-|-|
| [az iot](/cli/azure/iot) | Keduanya  | Semua perintah inti Azure CLI yang tersedia untuk Azure IoT.
| [az iot central](/cli/azure/iot/central) | Keduanya | Mengelola aset IoT Central.
| [az iot device](/cli/azure/iot/device) | Ekstensi | Manfaatkan kemampuan perpesanan perangkat-ke-cloud dan cloud-to-device.
| [az iot dps](/cli/azure/iot/dps) | Keduanya | Kelola Layanan Penyediaan Perangkat Azure IoT Hub.
| [az dt](/cli/azure/dt) | Ekstensi | Kelola solusi Azure Digital Twins & infrastruktur.
| [az iot edge](/cli/azure/iot/edge) | Ekstensi | Kelola solusi IoT di Edge.
| [az iot hub](/cli/azure/iot/hub) | Keduanya | Kelola Infrastruktur Azure IoT Hub.
| [az iot product](/cli/azure/iot/product) | Ekstensi | Mengelola pengujian perangkat untuk sertifikasi produk.

## <a name="additional-azure-cli-commands-for-azure-services-used-by-iot"></a>Perintah Azure CLI tambahan untuk layanan Azure yang digunakan oleh IoT

| Referensi | Jenis | Deskripsi
|-|-|-|
| [az maps](/cli/azure/maps) | core | Kelola Azure Peta.
| [az tsi](/cli/azure/tsi) | extension | Kelola Insights Azure Time Series.

## <a name="popular-iot-articles-using-the-azure-cli"></a>Artikel IoT populer menggunakan Azure CLI

- [Membuat Azure IoT Hub](/azure/iot-hub/iot-hub-create-using-cli)
- [Mengelola IoT Central](/azure/iot-central/core/howto-manage-iot-central-from-cli)
- [Tutorial perangkat berbasis CLI menggunakan Azure RTOS](/azure/rtos/getting-started?branch=master)
- [Menggunakan ekstensi IoT untuk manajemen perangkat Azure IoT Hub](/azure/iot-hub/iot-hub-device-management-iot-extension-azure-cli-2-0)
- [Menyebarkan dan memantau modul IoT Edge dalam skala besar dengan ekstensi Azure CLI untuk IoT](/azure/iot-edge/how-to-deploy-cli-at-scale)
- [Kirim telemetri dari perangkat ke hub IoT dan pantau dengan Azure CLI](/azure/iot-hub/quickstart-send-telemetry-cli)
- [Menggunakan Azure CLI untuk mengonfigurasi perutean pesan IoT Hub](/azure/iot-hub/tutorial-routing-config-message-routing-cli)

## <a name="azure-cli-reference-examples"></a>Azure CLI reference examples

Contoh disediakan dengan setiap referensi Azure CLI. Meskipun Anda juga dapat menyelesaikan tugas-tugas ini melalui portal Azure, menggunakan Azure CLI memerlukan baris perintah. Berikut adalah beberapa blok kode untuk memberi Anda gambaran tentang betapa mudahnya menggunakan Azure CLI.

Untuk bekerja dengan Azure IoT, Anda terlebih dahulu memerlukan grup sumber daya. Azure resource groups mudah dibuat dan dikelola dengan Azure CLI.  

```azurecli
#create a resource group
az group create --location westus --name MyResourceGroup
```

```azurecli
#get a list of resource groups for a subscription
az group list --subscription MySubscription --output table
```

Juga mudah untuk membuat Azure IoT Hub.

```azurecli
#create an Azure IoT hub
az iot hub create --resource-group MyResourceGroup --name MyIotHub --location westus
```

## <a name="see-also"></a>Lihat juga

- [Mulai dengan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari tentang instalasi dan masuk.

- Temukan referensi [inti](/cli/azure/reference-index) dan [ekstensi](./azure-cli-extensions-list.md) tambahan dalam dokumentasi Azure CLI.

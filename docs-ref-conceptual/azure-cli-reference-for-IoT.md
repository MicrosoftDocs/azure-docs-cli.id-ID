---
title: Referensi Azure CLI untuk Azure IoT | Microsoft Docs
description: Temukan perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure IoT. Dengan lebih dari 100 perintah berbeda yang tersedia, Anda dapat bekerja secara efektif dengan Azure IoT dari baris perintah.
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: paymaun.heidari
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure cli, azure iot, azure maps, azure tsi
ms.openlocfilehash: 73901b20392fcb39ff55fc6a22b8366def0ee1f4
ms.sourcegitcommit: cbb162f5b74c5250338109317f06a152809c4b4c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/06/2022
ms.locfileid: "141405681"
---
# <a name="azure-cli-reference-commands-for-azure-iot"></a>Perintah referensi Azure CLI untuk Azure IoT

Azure Command-Line Interface ([CLI](./what-is-azure-cli.md)) adalah sekumpulan perintah yang digunakan untuk membuat dan mengelola sumber daya Azure untuk berbagai layanan Azure. Untuk Azure IoT, ada lebih dari 100 perintah yang berbeda, yang memungkinkan Anda bekerja secara efektif dengan layanan dari baris perintah.

Perintah Azure CLI untuk [Azure IoT](/azure/iot-fundamentals/) terdiri dari dua bagian: Azure CLI (biasanya disebut sebagai **inti** CLI) dan **ekstensi** Azure CLI untuk IoT.

Fungsionalitas IoT di **inti** Azure CLI difokuskan pada pengelolaan dan konfigurasi infrastruktur. Operasi CRUD IoT Hub, atau mengonfigurasi rute pesan IoT Hub adalah kasus penggunaan yang khas untuk perintah inti.

**Ekstensi** Azure CLI untuk IOT memperkenalkan fitur dan fungsionalitas yang kaya untuk mengelola, memanipulasi, dan berinteraksi dengan data, entitas, serta objek dalam infrastruktur itu sendiri. Misalnya, mengelola armada perangkat, memantau peristiwa perangkat-ke-cloud, dan menerapkan metode cloud ke perangkat semuanya diaktifkan melalui ekstensi IoT. Ekstensi Azure CLI untuk IoT membuka kunci penggunaan teknologi percobaan atau pra-rilis, yang berkontribusi terhadap fleksibilitasnya dalam berbagai skenario dan kasus penggunaan. Ekstensi Azure CLI otomatis diinstal saat referensi ekstensi dijalankan untuk pertama kali. Untuk informasi selengkapnya tentang ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

> [!NOTE]
> Anda diminta menginstal referensi ekstensi saat digunakan pertama kali. Sebagai alternatif, Anda dapat menggunakan perintah `az extension add` untuk menginstal ekstensi secara manual.

## <a name="reference-command-list"></a>Daftar perintah referensi

Daftar referensi Azure CLI yang dapat digunakan untuk mengelola Azure IoT, jenis referensi, dan deskripsi referensi:

| Referensi | Inti atau ekstensi | Deskripsi
|-|-|-|
| [az iot](../latest/docs-ref-autogen/iot.yml) | Keduanya  | Semua perintah inti Azure CLI yang tersedia untuk Azure IoT.
| [az iot central](../latest/docs-ref-autogen/iot/central.yml) | Keduanya | Mengelola aset IoT Central.
| [az iot device](../latest/docs-ref-autogen/iot/device.yml) | Extensi | Manfaatkan kemampuan olahpesan perangkat-ke-cloud dan cloud-ke-perangkat.
| [az iot dps](../latest/docs-ref-autogen/iot/dps.yml) | Keduanya | Mengelola Azure IoT Hub Device Provisioning Service.
| [az dt](../latest/docs-ref-autogen/dt.yml) | Extensi | Mengelola solusi & infrastruktur Azure Digital Twins.
| [az iot edge](../latest/docs-ref-autogen/iot/edge.yml) | Extensi | Mengelola solusi IoT di Edge.
| [az iot hub](../latest/docs-ref-autogen/iot/hub.yml) | Keduanya | Mengelola infrastruktur Azure IoT Hub.
| [az iot product](../latest/docs-ref-autogen/iot/product.yml) | Extensi | Mengelola pengujian perangkat untuk sertifikasi produk.

## <a name="additional-azure-cli-commands-for-azure-services-used-by-iot"></a>Perintah Azure CLI lainnya untuk layanan Azure yang digunakan oleh IoT

| Referensi | Jenis | Deskripsi
|-|-|-|
| [az maps](../latest/docs-ref-autogen/maps.yml) | core | Mengelola Azure Maps.
| [az tsi](../latest/docs-ref-autogen/tsi.yml) | extension | Mengelola Azure Time Series Insights.

## <a name="popular-iot-articles-using-the-azure-cli"></a>Artikel IoT populer yang menggunakan Azure CLI

- [Membuat hub IoT](/azure/iot-hub/iot-hub-create-using-cli)
- [Mengelola IoT Central](/azure/iot-central/core/howto-manage-iot-central-from-cli)
- [Tutorial perangkat berbasis CLI menggunakan Azure RTOS](/azure/rtos/getting-started?branch=master)
- [Menggunakan ekstensi IoT untuk pengelolaan perangkat Azure IoT Hub](/azure/iot-hub/iot-hub-device-management-iot-extension-azure-cli-2-0)
- [Menyebarkan dan memantau modul IoT Edge dalam skala besar dengan ekstensi Azure CLI untuk IoT](/azure/iot-edge/how-to-deploy-cli-at-scale)
- [Mengirim telemetri dari perangkat ke hub IoT dan memantaunya dengan Azure CLI](/azure/iot-hub/quickstart-send-telemetry-cli)
- [Menggunakan Azure CLI untuk mengonfigurasi perutean pesan IoT Hub](/azure/iot-hub/tutorial-routing-config-message-routing-cli)

## <a name="azure-cli-reference-examples"></a>Contoh referensi Azure CLI

Contoh dilengkapi dengan setiap referensi Azure CLI. Meskipun Anda juga dapat menyelesaikan tugas ini melalui portal Azure, menggunakan Azure CLI memerlukan baris perintah. Berikut beberapa blok kode untuk memberi gambaran tentang mudahnya menggunakan Azure CLI.

Untuk bekerja dengan Azure IoT, Anda harus membuat grup sumber daya terlebih dahulu. Grup sumber daya Azure mudah dibuat dan dikelola dengan Azure CLI.  

```azurecli
#create a resource group
az group create --location westus --name MyResourceGroup
```

```azurecli
#get a list of resource groups for a subscription
az group list --subscription MySubscription --output table
```

Azure IoT Hub juga muda dibuat.

```azurecli
#create an Azure IoT hub
az iot hub create --resource-group MyResourceGroup --name MyIotHub --location westus
```

## <a name="see-also"></a>Lihat juga

- [Mulai gunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari penginstalan dan aktivitas masuk.

- Temukan referensi [core](../latest/docs-ref-autogen/reference-index.yml) dan [ekstensi](./azure-cli-extensions-list.md) tambahan dalam dokumentasi Azure CLI.
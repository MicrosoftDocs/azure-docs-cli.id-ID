---
title: Referensi Azure CLI untuk Azure Monitor | Microsoft Docs
description: Temukan perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure Monitor. Ikuti tautan ke artikel populer untuk mempelajari cara menggunakan Azure CLI untuk Azure Monitor
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure, azure monitor
ms.openlocfilehash: 6af75b674cbfdfd032916ebdbfdc31e767920125
ms.sourcegitcommit: cbb162f5b74c5250338109317f06a152809c4b4c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/06/2022
ms.locfileid: "141398394"
---
# <a name="azure-cli-reference-commands-for-azure-monitor"></a>Perintah referensi Azure CLI untuk Azure Monitor

Azure Command-Line Interface ([CLI](./what-is-azure-cli.md)) adalah sekumpulan perintah yang digunakan untuk membuat dan mengelola sumber daya Azure untuk berbagai layanan Azure. Untuk Azure Monitor, terdapat lebih dari 100 perintah lainnya, yang memungkinkan Anda bekerja secara efektif dengan layanan dari baris perintah.

Perintah Azure CLI untuk [Azure Monitor](/azure/azure-monitor/) terdiri dari dua bagian: Azure CLI (biasanya disebut sebagai **inti** CLI) dan **ekstensi** jejak CLI Azure Monitor. Ekstensi Azure CLI untuk Azure Monitor diinstal secara otomatis saat pertama kali Anda menjalankan referensi ekstensi. Untuk informasi selengkapnya tentang ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

> [!IMPORTANT]
>
> Azure Monitor kini dilengkapi dengan Application Insights dan Log Analytics. Anda harus menginstal ekstensi untuk setiap sub-area saat bekerja dengan Azure CLI untuk Azure Monitor. Anda diminta menginstal referensi ekstensi saat digunakan pertama kali. Sebagai alternatif, Anda dapat menggunakan perintah `az extension add` untuk menginstal ekstensi secara manual.

## <a name="azure-monitor-references"></a>Referensi Azure Monitor

Daftar referensi Azure CLI yang dapat digunakan untuk mengelola Azure Monitor, deskripsi referensi, dan tautan ke artikel populer:

| Referensi | Menginstal ekstensi | Deskripsi | Untuk informasi selengkapnya
|-|-|-|-|
| [az monitor](/cli/azure/monitor) | | Grup perintah tingkat atas untuk semua perintah Azure CLI untuk Azure Monitor. | [Gambaran umum Azure Monitor](/azure/azure-monitor/overview)
| [az monitor action-group](/cli/azure/monitor/action-group) | | Mengelola grup tindakan, yang terkait dengan notifikasi setelah peringatan dipicu. | [Peringatan Azure Monitor](/azure/azure-monitor/platform/alerts-overview)
| [az monitor action-rule](/azure/azure-monitor/alerts/alerts-action-rules) | ya | Mengelola aturan tindakan, yang memungkinkan Anda menambahkan atau menekan grup tindakan pada peringatan yang dipicu. | [Peringatan Azure Monitor](/azure/azure-monitor/alerts/alerts-action-rules)
| [az monitor activity-log](/cli/azure/monitor/activity-log) | | Mengelola log aktivitas, termasuk peringatan log aktivitas. | [Log aktivitas Azure](/azure/azure-monitor/platform/activity-log)
| [az monitor app-insights](/cli/azure/monitor/app-insights) | ya | Mengelola Application Insights untuk pemantauan aplikasi. | [Gambaran umum Application insights](/azure/azure-monitor/app/app-insights-overview)
| [az monitor autoscale](/cli/azure/monitor/autoscale) | | Mengelola pengaturan skala otomatis. | [Ringkasan skala otomatis](/azure/azure-monitor/platform/autoscale-overview)
| [az monitor data-collection](/cli/azure/monitor/data-collection) | ya | Mengelola aturan pengumpulan data. | [Aturan pengumpulan data](/azure/azure-monitor/agents/data-collection-rule-overview)
| [az monitor diagnostic-settings](/cli/azure/monitor/diagnostic-settings) | | Mengelola pengaturan diagnostik layanan, yang menyiapkan pengumpulan dan perutean berbagai jenis log dan metrik platform. | [Membuat pengaturan diagnostik](/azure/azure-monitor/platform/diagnostic-settings)
| [az footprint](/cli/azure/footprint) | ya | Mengelola pengaturan Azure Footprint. |
| [az monitor log-analytics](/cli/azure/monitor/log-analytics) | | Mengelola kluster log dan ruang kerja. | [Merancang penyebaran Log Azure Monitor](/azure/azure-monitor/platform/design-logs-deployment)
| [az monitor log-analytics solution](/cli/azure/monitor/log-analytics/solution) | ya | Mengelola solusi Log Analytics. |
| [az monitor log-profiles](/cli/azure/monitor/log-profiles) | | JANGAN gunakan untuk pengembangan baru. Perintah ini sebelumnya digunakan untuk merutekan log aktivitas ke Log Azure Monitor dan Log Analytics.  Sebagai gantinya, gunakan [pengaturan diagnostik](/azure/azure-monitor/platform/diagnostic-settings).  | [Mengirim Log aktivitas ke ruang kerja Log Analytics](/azure/azure-monitor/platform/activity-log#send-to-log-analytics-workspace)
| [az monitor metrics](/cli/azure/monitor/metrics) | | Mengelola metrik platform dan aturan peringatan metrik mendekati real time. | [Ringkasan metrik di Azure Monitor](/azure/azure-monitor/platform/data-platform-metrics) dan [Memahami cara kerja peringatan metrik](/azure/azure-monitor/platform/alerts-metric-overview)
| [az monitor private-link-scope](/cli/azure/monitor/private-link-scope) | | Mengelola pemantauan sumber daya cakupan tautan privat. | [Menggunakan Azure Private Link untuk menyambungkan jaringan dengan aman ke Azure Monitor](/azure/azure-monitor/platform/private-link-security)
| [az monitor scheduled-query](/cli/azure/monitor/scheduled-query) | ya | Mengelola kueri terjadwal.

## <a name="popular-azure-monitor-articles-using-the-azure-cli"></a>Artikel Azure Monitor populer menggunakan Azure CLI

- [Sampel CLI Azure Monitor](/azure/azure-monitor/samples/cli-samples)
- [Membuat ruang kerja Log Analytics dengan Azure CLI](/azure/azure-monitor/learn/quick-create-workspace-cli)

## <a name="azure-cli-reference-examples-for-azure-monitor"></a>Contoh referensi Azure CLI untuk Azure Monitor

Contoh dilengkapi dengan setiap referensi Azure CLI. Meskipun Anda juga dapat menyelesaikan tugas ini melalui portal Azure, menggunakan Azure CLI memerlukan baris perintah. Berikut beberapa blok kode untuk memberi gambaran tentang mudahnya menggunakan Azure CLI.

Untuk bekerja dengan Azure Monitor, Anda harus memiliki grup sumber daya terlebih dahulu.  Grup sumber daya Azure mudah dibuat dan dikelola dengan Azure CLI.  

```azurecli
#create a resource group
az group create --location westus --name MyResourceGroup

#get a list of resource groups for a subscription
az group list --subscription MySubscription --output table
```

Peringatan log Azure Monitor juga mudah dibuat.

```azurecli
#create an Azure Monitor activity log alert
az monitor activity-log alert create --name MyAlertName --resource-group MyResourceGroup
```

## <a name="see-also"></a>Lihat juga

- [Mulai gunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari penginstalan dan aktivitas masuk.

- Temukan referensi [inti](../latest/docs-ref-autogen/reference-index.yml) dan [ekstensi](./azure-cli-extensions-list.md) lainnya di dokumentasi Azure CLI.

- Pelajari referensi ekstensi lebih lanjut di [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).
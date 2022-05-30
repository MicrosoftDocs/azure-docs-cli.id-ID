---
title: Referensi Azure CLI untuk Azure Monitor | Microsoft Docs
description: Temukan perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure Monitor. Ikuti tautan ke artikel populer untuk mempelajari cara menggunakan Azure CLI untuk Azure Monitor
author: dbradish-microsoft
manager: barbkess
ms.tool: azure-cli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure, azure monitor
ms.openlocfilehash: b1b142fe0d1a4f51604c79e3696502d4c13adbc0
ms.sourcegitcommit: 6822e5d700742617eabda5904fe2ca217bae9d28
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/30/2022
ms.locfileid: "145937660"
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
| [az monitor](../latest/docs-ref-autogen/monitor.yml) | | Grup perintah tingkat atas untuk semua perintah Azure CLI untuk Azure Monitor. | [Gambaran umum Azure Monitor](/azure/azure-monitor/overview)
| [az monitor action-group](../latest/docs-ref-autogen/monitor/action-group.yml) | | Mengelola grup tindakan, yang terkait dengan notifikasi setelah peringatan dipicu. | [Peringatan Azure Monitor](/azure/azure-monitor/platform/alerts-overview)
| [az monitor action-rule](/azure/azure-monitor/alerts/alerts-action-rules) | ya | Mengelola aturan tindakan, yang memungkinkan Anda menambahkan atau menekan grup tindakan pada peringatan yang dipicu. | [Peringatan Azure Monitor](/azure/azure-monitor/alerts/alerts-action-rules)
| [az monitor activity-log](../latest/docs-ref-autogen/monitor/activity-log.yml) | | Mengelola log aktivitas, termasuk peringatan log aktivitas. | [Log aktivitas Azure](/azure/azure-monitor/platform/activity-log)
| [az monitor app-insights](../latest/docs-ref-autogen/monitor/app-insights.yml) | ya | Mengelola Application Insights untuk pemantauan aplikasi. | [Gambaran umum Application insights](/azure/azure-monitor/app/app-insights-overview)
| [az monitor autoscale](../latest/docs-ref-autogen/monitor/autoscale.yml) | | Mengelola pengaturan skala otomatis. | [Ringkasan skala otomatis](/azure/azure-monitor/platform/autoscale-overview)
| [az monitor data-collection](../latest/docs-ref-autogen/monitor/data-collection.yml) | ya | Mengelola aturan pengumpulan data. | [Aturan pengumpulan data](/azure/azure-monitor/agents/data-collection-rule-overview)
| [az monitor diagnostic-settings](../latest/docs-ref-autogen/monitor/diagnostic-settings.yml) | | Mengelola pengaturan diagnostik layanan, yang menyiapkan pengumpulan dan perutean berbagai jenis log dan metrik platform. | [Membuat pengaturan diagnostik](/azure/azure-monitor/platform/diagnostic-settings)
| [az footprint](../latest/docs-ref-autogen/footprint.yml) | ya | Mengelola pengaturan Azure Footprint. |
| [az monitor log-analytics](../latest/docs-ref-autogen/monitor/log-analytics.yml) | | Mengelola kluster log dan ruang kerja. | [Merancang penyebaran Log Azure Monitor](/azure/azure-monitor/platform/design-logs-deployment)
| [az monitor log-analytics solution](../latest/docs-ref-autogen/monitor/log-analytics/solution.yml) | ya | Mengelola solusi Log Analytics. |
| [az monitor log-profiles](../latest/docs-ref-autogen/monitor/log-profiles.yml) | | JANGAN gunakan untuk pengembangan baru. Perintah ini sebelumnya digunakan untuk merutekan log aktivitas ke Log Azure Monitor dan Log Analytics.  Sebagai gantinya, gunakan [pengaturan diagnostik](/azure/azure-monitor/platform/diagnostic-settings).  | [Mengirim Log aktivitas ke ruang kerja Log Analytics](/azure/azure-monitor/platform/activity-log#send-to-log-analytics-workspace)
| [az monitor metrics](../latest/docs-ref-autogen/monitor/metrics.yml) | | Mengelola metrik platform dan aturan peringatan metrik mendekati real time. | [Ringkasan metrik di Azure Monitor](/azure/azure-monitor/platform/data-platform-metrics) dan [Memahami cara kerja peringatan metrik](/azure/azure-monitor/platform/alerts-metric-overview)
| [az monitor private-link-scope](../latest/docs-ref-autogen/monitor/private-link-scope.yml) | | Mengelola pemantauan sumber daya cakupan tautan privat. | [Menggunakan Azure Private Link untuk menyambungkan jaringan dengan aman ke Azure Monitor](/azure/azure-monitor/platform/private-link-security)
| [az monitor scheduled-query](../latest/docs-ref-autogen/monitor/scheduled-query.yml) | ya | Mengelola kueri terjadwal.

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

* [Mulai gunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari penginstalan dan aktivitas masuk.
* Temukan [perintah referensi](../latest/docs-ref-autogen/reference-index.yml) tambahan dan [ekstensi yang tersedia](./azure-cli-extensions-list.md) dalam dokumentasi Azure CLI.
* [Pelajari cara menggunakan Bash dengan Azure CLI](./azure-cli-learn-bash.md)

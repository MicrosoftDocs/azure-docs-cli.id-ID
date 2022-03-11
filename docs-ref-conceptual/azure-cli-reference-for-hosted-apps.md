---
title: Referensi Azure CLI untuk aplikasi yang di-host Azure | Microsoft Docs
description: Temukan perintah referensi inti dan ekstensi Azure CLI untuk mengelola aplikasi yang di-host Azure.  Ikuti tautan ke artikel populer untuk mempelajari cara menggunakan Azure CLI untuk aplikasi yang di-host Azure.
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure cli, aplikasi yang dihost azure, azure web apps, aplikasi web statik Azure, azure app service
ms.openlocfilehash: 19ec8d694c927142a96939916c4d978c4551bcb2
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439102"
---
# <a name="azure-cli-reference-commands-for-azure-hosted-apps"></a>Perintah referensi Azure CLI untuk aplikasi yang di-host Azure

Azure Command-Line Interface ([CLI](./what-is-azure-cli.md)) adalah sekumpulan perintah yang digunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di berbagai layanan Azure dan memberi Anda kemampuan untuk mengelola aplikasi yang di-host dari baris perintah.

Perintah Azure CLI untuk [Azure App Service](/azure/app-service) terdiri dari dua bagian: **inti** dan **ekstensi**. Perintah Azure CLI inti dikirimkan sebagai bagian dari CLI dan didukung sepenuhnya. Ekstensi memberi Anda akses ke perintah percobaan dan pra-rilis. Untuk informasi selengkapnya tentang ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).  

Akses ke referensi `az webapp` berikut ekstensi [webapp](https://github.com/Azure/azure-cli-extensions/tree/main/src/webapp): `az webapp container`, `az webapp remote-connection`, dan `az webapp scan`. Akses ke referensi `az functionapp app` memerlukan ekstensi [deploy-to-azure](https://github.com/Azure/deploy-to-azure-cli-extension).

> [!NOTE]
> Anda diminta menginstal referensi ekstensi saat digunakan pertama kali. Sebagai alternatif, Anda dapat menggunakan perintah [az extension add](/cli/azure/extension#az_extension_add) untuk menginstal ekstensi secara manual berdasarkan nama.

Lihat [Azure Web Apps](/cli/azure/service-page/azure%20web%20apps) untuk mengetahui daftar alfabetik referensi inti dan ekstensi Azure CLI yang tersedia untuk layanan Aplikasi Web Azure. Untuk referensi di setiap sub-grup, lihat tabel di bagian berikut:

- [Azure Static Web Apps](#azure-static-web-app-references)
- [Konfigurasi Aplikasi Web Azure](#azure-web-app-configuration-references)
- [Penyebaran Aplikasi Web Azure](#azure-web-app-deployment-references)
- [WebJobs Aplikasi Web Azure](#azure-web-app-webjob-references)
- [Referensi Aplikasi Web Azure lainnya](#additional-azure-web-app-references)

Untuk referensi aplikasi yang di-host lainnya, lihat bagian berikut:

- [Paket Azure App Service](#azure-app-service-plan-references)
- [Aplikasi fungsi Azure](#azure-function-app-references)

## <a name="azure-static-web-app-references"></a>Referensi Aplikasi Web Statik Azure

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az staticwebapp](/cli/azure/staticwebapp) | Mengelola aplikasi web statik. | [Mulai cepat: Membangun situs statis pertama Anda menggunakan Azure CLI](/azure/static-web-apps/get-started-cli) |
| [az staticwebapp appsettings](/cli/azure/staticwebapp/appsettings) | Mengelola pengaturan aplikasi fungsi aplikasi web statik. | [Tambahkan API di Azure Static Web Apps dengan Azure Functions](/azure/static-web-apps/add-api) |
| [az staticwebapp environment](/cli/azure/staticwebapp/environment) | Mengelola lingkungan aplikasi web statik. | [Tambahkan API di Azure Static Web Apps dengan Azure Functions](/azure/static-web-apps/add-api) |
| [az staticwebapp hostname](/cli/azure/staticwebapp/hostname) | Mengelola nama host kustom fungsi aplikasi web statik. | [Tambahkan API di Azure Static Web Apps dengan Azure Functions](/azure/static-web-apps/add-api) |
| [az staticwebapp users](/cli/azure/staticwebapp/users) | Mengelola pengguna aplikasi web statik. | [Mengakses informasi pengguna di Azure Static Web Apps](/azure/static-web-apps/user-information) |

## <a name="azure-web-app-configuration-references"></a>Referensi konfigurasi Aplikasi Web Azure

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az webapp config](/cli/azure/webapp/config) | Mengonfigurasi aplikasi web. | [Mengonfigurasi aplikasi App Service](/azure/app-service/configure-common) |
| [az webapp config access-restriction](/cli/azure/webapp/config/access-restriction) | Mengelola pembatasan akses di aplikasi web. | [Mengonfigurasi Azure App Service dengan Azure Application Gateway menggunakan CLI](/azure/app-service/scripts/cli-integrate-app-service-with-application-gateway) |
| [az webapp config appsettings](/cli/azure/webapp/config/appsettings) | Mengonfigurasi pengaturan aplikasi web. Jika pengaturan diperbarui atau dihapus, aplikasi akan didaur ulang. | [Mengonfigurasi aplikasi App Service](/azure/app-service/configure-common) |
| [az webapp config backup](/cli/azure/webapp/config/backup) | Mengelola pencadangan untuk aplikasi web. | [Mencadangkan aplikasi menggunakan CLI](/azure/app-service/scripts/cli-backup-onetime) |
| [az webapp config connection-string](/cli/azure/webapp/config/connection-string) | Mengelola string koneksi untuk aplikasi web. | [Mengonfigurasi string koneksi](/azure/app-service/tutorial-dotnetcore-sqldb-app#configure-connection-string) |
| [az webapp config container](/cli/azure/webapp/config/container) | Mengelola pengaturan kontainer untuk aplikasi web. | [Memigrasikan perangkat lunak kustom ke Azure App Service menggunakan kontainer kustom](/azure/app-service/tutorial-custom-container) |
| [az webapp config hostname](/cli/azure/webapp/config/hostname) | Mengonfigurasi nama host untuk aplikasi web. | [Mengonfigurasi nama domain kustom](/azure/developer/javascript/how-to/with-azure-cli/configure-app-service-custom-domain-name) |
| [az webapp config snapshot](/cli/azure/webapp/config/snapshot) | Mengelola snapshot untuk aplikasi web. | [Pulihkan aplikasi di Azure dari snapshot](/azure/app-service/app-service-web-restore-snapshots) |
| [az webapp config ssl](/cli/azure/webapp/config/ssl) | Mengonfigurasi sertifikat SSL untuk aplikasi web. | [Mengikat sertifikat TLS/SSL kustom ke aplikasi Azure App Service menggunakan CLI](/azure/app-service/scripts/cli-configure-ssl-certificate) |
| [az webapp config storage-account](/cli/azure/webapp/config/storage-account) | Mengelola konfigurasi akun penyimpanan Azure di aplikasi web. Hanya berlaku untuk aplikasi web Kontainer Linux dan Windows). | [Memasang berbagi file ke aplikasi fungsi Python menggunakan Azure CLI](/azure/azure-functions/scripts/functions-cli-mount-files-storage-linux) |

## <a name="azure-web-app-deployment-references"></a>Referensi penyebaran Aplikasi Web Azure

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az webapp deployment](/cli/azure/webapp/deployment) | Mengelola penyebaran aplikasi web. |[Menyebarkan Aplikasi Web Azure](/azure/devops/pipelines/targets/webapp)  |
| [az webapp deployment container](/cli/azure/webapp/deployment/container) | Mengelola penyebaran berkelanjutan berbasis kontainer. | [Penyebaran berkelanjutan dengan kontainer kustom di Azure App Service](/azure/app-service/deploy-ci-cd-custom-container) |
| [az webapp deployment slot](/cli/azure/webapp/deployment/slot) | Mengelola slot penyebaran aplikasi web. | [Membuat aplikasi Azure App Service dan menyebarkan kode ke lingkungan penahapan menggunakan Azure CLI](/azure/app-service/scripts/cli-deploy-staging-environment) |
| [az webapp deployment source](/cli/azure/webapp/deployment/source) | Mengelola penyebaran aplikasi web melalui kontrol sumber. | [Akses aman ke data aplikasi](/azure/storage/blobs/storage-secure-access-application?tabs=azure-cli) |
| [az webapp deployment user](/cli/azure/webapp/deployment/user) | Mengelola info masuk pengguna yang akan disebarkan. | [Mengonfigurasi penerapan Git lokal](/azure/key-vault/general/tutorial-net-create-vault-azure-web-app#configure-the-local-git-deployment) |

## <a name="azure-web-app-webjob-references"></a>Referensi WebJob Aplikasi Web Azure

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az webapp webjob](/cli/azure/webapp/webjob) | Mengelola WebJob di aplikasi web. | [Menjalankan tugas latar belakang dengan WebJobs di Azure App Service](/azure/app-service/webjobs-create) |
| [az webapp webjob continuous](/cli/azure/webapp/webjob/continuous) | Mengelola WebJob berkelanjutan di aplikasi web. | [Menjalankan tugas latar belakang dengan WebJobs di Azure App Service](/azure/app-service/webjobs-create) |
| [az webapp webjob triggered](/cli/azure/webapp/webjob/triggered) | Mengelola WebJob yang dipicu di aplikasi web. | [Menjalankan tugas latar belakang dengan WebJobs di Azure App Service](/azure/app-service/webjobs-create) |

## <a name="additional-azure-web-app-references"></a>Referensi Aplikasi Web Azure lainnya

| Referensi | Deskripsi | Ekstensi? | Informasi selengkapnya |
|-|-|-|-|
| [az webapp](/cli/azure/webapp) | Mengelola aplikasi web. | | [Memprovisikan dan menyebarkan aplikasi web](/azure/developer/python/azure-sdk-example-web-app) |
| [az webapp auth](/cli/azure/webapp/auth) | Mengelola autentikasi dan otorisasi untuk aplikasi web. | | [Autentikasi dan otorisasi di Azure App Service](/azure/app-service/overview-authentication-authorization) |
| [az webapp container](/cli/azure/webapp/container) | Mengelola operasi kontainer untuk aplikasi web. | Ya | [Menyebarkan ke Aplikasi Web Azure untuk Kontainer](/azure/devops/pipelines/apps/cd/deploy-docker-webapp) |
| [az webapp cors](/cli/azure/webapp/cors) | Mengelola Berbagi Sumber Daya Lintas Asal (CORS). | | [Meng-host RESTful API dengan CORS di Azure App Service](/azure/app-service/app-service-web-tutorial-rest-api) |
| [az webapp deleted](/cli/azure/webapp/deleted) | Mengelola aplikasi web yang dihapus. | | [Memulihkan aplikasi App Service yang dihapus](/azure/app-service/app-service-undelete) |
| [az webapp hybrid-connection](/cli/azure/webapp/hybrid-connection) | Mengelola Koneksi Hibrid untuk aplikasi web. | | [Koneksi Hibrid Azure App Service](/azure/app-service/app-service-hybrid-connections) |
| [az webapp log](/cli/azure/webapp/log) | Mengelola log untuk aplikasi web. | | [Membangun aplikasi ASP.NET Core dan Azure SQL Database di Azure App Service](/azure/app-service/tutorial-dotnetcore-sqldb-app) |
| [az webapp log deployment](/cli/azure/webapp/log/deployment) | Mengelola log penyebaran untuk aplikasi web. | | [Membangun aplikasi ASP.NET Core dan Azure SQL Database di Azure App Service](/azure/app-service/tutorial-dotnetcore-sqldb-app) |
| [az webapp identity](/cli/azure/webapp/identity) | Mengelola identitas layanan terkelola untuk aplikasi web. | | [Cara menggunakan identitas terkelola untuk App Service dan Azure Functions](/azure/app-service/overview-managed-identity) |
| [az webapp remote-connection](/cli/azure/webapp/remote-connection) | Membuat koneksi jarak jauh menggunakan terowongan TCP ke aplikasi web. | Ya | [Buka sesi SSH ke kontainer Linux di Azure App Service](/azure/app-service/configure-linux-open-ssh-session) |
| [az webapp scan](/cli/azure/webapp/scan) | Mengelola pemindaian untuk aplikasi web. Saat ini hanya tersedia untuk aplikasi web berbasis Linux. | Ya | [Memindai mesin Anda](/azure/security-center/deploy-vulnerability-assessment-vm) |
| [az webapp traffic-routing](/cli/azure/webapp/traffic-routing) | Mengelola perutean lalu lintas untuk aplikasi web. | | [Mengontrol lalu lintas Azure App Service dengan Azure Traffic Manager](/azure/app-service/web-sites-traffic-manager) |
| [az webapp vnet-integration](/cli/azure/webapp/vnet-integration) | Mengelola integrasi jaringan virtual untuk aplikasi web. | | [Mengintegrasikan aplikasi Anda dengan Azure Virtual Network](/azure/app-service/web-sites-integrate-with-vnet) |

## <a name="azure-app-service-plan-references"></a>Referensi paket Azure App Service

Lihat [az appservice](/cli/azure/appservice) untuk mengetahui daftar lengkap referensi yang tersedia untuk mengelola [paket Azure App Service](/azure/app-service/overview-hosting-plans).

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az appservice](/cli/azure/appservice) | Mengelola paket App Service. | [Pengenalan Lingkungan App Service](/azure/app-service/environment/intro) |
| [az appservice ase](/cli/azure/appservice/ase) | Mengelola App Service Environments v2. | [Pengenalan Lingkungan App Service](/azure/app-service/environment/intro) |
| [az appservice domain](/cli/azure/appservice/domain) | Mengelola domain kustom. | [Memetakan nama DNS kustom yang sudah ada ke Azure App Service](/azure/app-service/app-service-web-tutorial-custom-domain) |
| [az appservice hybrid-connection](/cli/azure/appservice/hybrid-connection) | Mengatur kunci yang digunakan aplikasi untuk terhubung ke koneksi hibrid dalam paket App Service. | [Koneksi Hibrid Azure App Service](/azure/app-service/app-service-hybrid-connections) |
| [az appservice plan](/cli/azure/appservice/plan) | Mengelola paket App Service. | [Mengelola paket App Service di Azure](/azure/app-service/app-service-plan-manage) |
| [az appservice vnet-integration](/cli/azure/appservice/vnet-integration) | Membuat daftar integrasi jaringan virtual yang digunakan paket layanan aplikasi. | [Mengintegrasikan aplikasi Anda dengan Azure Virtual Network](/azure/app-service/web-sites-integrate-with-vnet) |

## <a name="azure-function-app-references"></a>Referensi aplikasi fungsi Azure

Lihat [az functionapp](/cli/azure/functionapp) untuk mengetahui daftar lengkap referensi yang tersedia untuk mengelola [aplikasi fungsi Azure](/azure/app-service/overview-hosting-plans).

| Referensi | Deskripsi | Ekstensi? | Informasi selengkapnya |
|-|-|-|-|
| [az functionapp](/cli/azure/functionapp) | Mengelola aplikasi fungsi. | | [Mengelola aplikasi fungsi Anda](/azure/azure-functions/functions-how-to-use-azure-function-app-settings?tabs=azurecli) |
| [az functionapp app](/cli/azure/functionapp/app) | Mengelola aplikasi Azure Functions. | Ya | [Mengelola aplikasi fungsi Anda](/azure/azure-functions/functions-how-to-use-azure-function-app-settings?tabs=azurecli) |
| [az functionapp config](/cli/azure/functionapp/config) | Mengonfigurasi aplikasi fungsi. | | [Mengelola aplikasi fungsi Anda](/azure/azure-functions/functions-how-to-use-azure-function-app-settings?tabs=azurecli) |
| [az functionapp config access-restriction](/cli/azure/functionapp/config/access-restriction) | Mengelola pembatasan akses di aplikasi fungsi. | | [Menyiapkan pembatasan akses Azure App Service](/azure/app-service/app-service-ip-restrictions) |
| [az functionapp config appsettings](/cli/azure/functionapp/config/appsettings) | Mengelola pengaturan aplikasi fungsi. | | [Mengelola aplikasi fungsi Anda](/azure/azure-functions/functions-how-to-use-azure-function-app-settings?tabs=azurecli) |
| [az functionapp config container](/cli/azure/functionapp/config/container) | Mengelola pengaturan kontainer aplikasi fungsi. | | [Membuat fungsi pertama di Azure Arc menggunakan kontainer kustom](/azure/azure-functions/create-first-function-arc-custom-container) |
| [az functionapp config hostname](/cli/azure/functionapp/config/hostname) | Mengonfigurasi nama host untuk aplikasi fungsi. | | [Opsi jaringan Azure Functions](/azure/azure-functions/functions-networking-options) |
| [az functionapp config ssl](/cli/azure/functionapp/config/ssl) | Mengonfigurasi sertifikat SSL untuk aplikasi fungsi. | | [Menambahkan sertifikat TLS/SSL di Azure App Service](/azure/app-service/configure-ssl-certificate) |
| [az functionapp cors](/cli/azure/functionapp/cors) | Mengelola Berbagi Sumber Daya Lintas Asal (CORS) untuk aplikasi fungsi. | | [Mengelola aplikasi fungsi Anda](/azure/azure-functions/functions-how-to-use-azure-function-app-settings?tabs=azurecli) |
| [az functionapp deployment](/cli/azure/functionapp/deployment) | Mengelola penyebaran aplikasi fungsi. | | [Teknologi penyebaran di Azure Functions](/azure/azure-functions/functions-deployment-technologies) |
| [az functionapp deployment container](/cli/azure/functionapp/deployment/container) | Mengelola penyebaran berkelanjutan berbasis kontainer. | | [Buat fungsi di Linux menggunakan kontainer kustom](/azure/azure-functions/functions-create-function-linux-custom-image?tabs=bash%2Cazurecli) |
| [az functionapp deployment slot](/cli/azure/functionapp/deployment/slot) | Mengelola slot penyebaran aplikasi fungsi. | | [Slot penyebaran Azure Functions](/azure/azure-functions/functions-deployment-slots) |
| [az functionapp deployment source](/cli/azure/functionapp/deployment/source) | Mengelola penyebaran aplikasi fungsi melalui kontrol sumber. | | [Membuat fungsi di Azure](/azure/azure-functions/scripts/functions-cli-create-function-app-vsts-continuous) |
| [az functionapp deployment user](/cli/azure/functionapp/deployment/user) | Mengelola info masuk pengguna yang akan disebarkan. | | [Mengamankan Azure Functions](/azure/azure-functions/security-concepts) |
| [az functionapp devops-pipeline](/cli/azure/functionapp/devops-pipeline) | Mengelola integrasi khusus Azure Function dengan Azure DevOps. | | [Pengiriman berkelanjutan dengan menggunakan Azure DevOps](/azure/azure-functions/functions-how-to-azure-devops) |
| [az functionapp function](/cli/azure/functionapp/function) | Mengelola fungsi aplikasi fungsi. | | [Mengelola aplikasi fungsi Anda](/azure/azure-functions/functions-how-to-use-azure-function-app-settings) |
| [az functionapp function keys](/cli/azure/functionapp/function/keys) | Mengelola tombol fungsi. | | [Mengamankan Azure Functions](/azure/azure-functions/security-concepts) |
| [az functionapp hybrid-connection](/cli/azure/functionapp/hybrid-connection) | Mengelola koneksi hibrid dari aplikasi fungsi. | | [Koneksi Hibrid Azure App Service](/azure/app-service/app-service-hybrid-connections) |
| [az functionapp identity](/cli/azure/functionapp/identity) | Mengelola identitas layanan terkelola aplikasi web. | | [Mencadangkan penyimpanan App Configuration secara otomatis](/azure/azure-app-configuration/howto-backup-config-store) |
| [az functionapp keys](/cli/azure/functionapp/keys) | Mengelola kunci aplikasi fungsi. | | [Mengamankan Azure Functions](/azure/azure-functions/security-concepts) |
| [az functionapp log deployment](/cli/azure/functionapp/log/deployment) | Mengelola log penyebaran aplikasi fungsi. | | [Pantau Azure Functions](/azure/azure-functions/functions-monitoring) |
| [az functionapp plan](/cli/azure/functionapp/plan) | Mengelola paket App Service untuk aplikasi fungsi. | | [Mengelola aplikasi fungsi Anda](/azure/azure-functions/functions-how-to-use-azure-function-app-settings?tabs=azurecli) |
| [az functionapp vnet-integration](/cli/azure/functionapp/vnet-integration) | Mengelola integrasi jaringan virtual aplikasi fungsi. | | [Integrasi Virtual Network](/azure/azure-functions/functions-networking-options#virtual-network-integration)

## <a name="see-also"></a>Lihat juga

- [Mulai gunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari penginstalan dan aktivitas masuk.

- Temukan [referensi](/cli/azure/reference-index) tambahan dan [ekstensi yang tersedia](./azure-cli-extensions-list.md) di dokumentasi Azure CLI.

- Pelajari referensi ekstensi lebih lanjut di [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

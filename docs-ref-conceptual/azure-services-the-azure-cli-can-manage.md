---
title: Daftar layanan Azure yang dapat dikelola Azure CLI | Microsoft Docs
description: Azure CLI dapat membuat dan mengelola berbagai sumber daya Azure — lihat tautan ke layanan Azure yang dapat dikelola Azure CLI, yang diatur oleh grup.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/01/2021
ms.topic: conceptual
ms.prod: azure
ms.technology: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: pengelolaan layanan azure, daftar layanan azure, daftar sumber daya azure
ms.openlocfilehash: 821eda50dc30fe0f0975cfcd66be9c1fc9ec8182
ms.sourcegitcommit: 133f901f17aebce8976e4751bcadf0758a9a1c76
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 02/14/2022
ms.locfileid: "138622133"
---
# <a name="list-of-azure-services-the-azure-cli-can-manage"></a>Daftar layanan Azure yang dapat dikelola Azure CLI

Azure CLI tersedia di banyak layanan Azure, dan merupakan alat yang fleksibel dan canggih untuk membuat dan mengelola sumber daya Azure.  Artikel ini berisi daftar layanan Azure yang dapat dikelola Azure CLI.

## <a name="ai--machine-learning"></a>AI + Pembelajaran Mesin

Gunakan AI + Pembelajaran Mesin untuk membuat aplikasi generasi berikutnya menggunakan kemampuan kecerdasan buatan untuk pengembang dan skenario apa pun.

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Azure Bot Service](/cli/azure/service-page/azure%20bot%20service)| [Mengidentifikasi penyedia](/azure/bot-service/bot-builder-concept-identity-providers)
|[Azure Databricks](/cli/azure/service-page/azure%20databricks)| [Membangun alur data](/azure/devops/pipelines/apps/cd/azure/build-data-pipeline)
|[Azure Cognitive Search](/cli/azure/service-page/azure%20cognitive%20search)|[Mengelola layanan Azure Cognitive Search](/azure/search/search-manage-azure-cli)
|[Azure Cognitive Services](/cli/azure/service-page/azure%20cognitive%20service) | [Cara membuat dan mengelola sumber daya LUIS](/azure/cognitive-services/LUIS/luis-how-to-azure-subscription?tabs=without-portal)
|| [Mengonfigurasi jaringan virtual Azure Cognitive Services](/azure/cognitive-services/cognitive-services-virtual-networks?tabs=azure-cli)
|| [Mulai Cepat: Membuat sumber daya Cognitive Services](/azure/cognitive-services/cognitive-services-apis-create-account-cli)
|[Pembelajaran Mesin Azure](/cli/azure/service-page/azure%20machine%20learning)| [Mengelola peran di ruang kerja Anda](/azure/machine-learning/how-to-assign-roles)
|| [Membuat dan mengelolar instans komputasi Azure Machine Learning](/azure/machine-learning/how-to-create-manage-compute-instance?tabs=azure-cli)
|| [Membuat klaster komputasi Azure Machine Learning](/azure/machine-learning/how-to-create-attach-compute-cluster?tabs=azure-cli)
|| [Mengonfigurasi ruang kerja Azure Machine Learning dengan titik akhir privat](/azure/machine-learning/how-to-configure-private-link?tabs=azure-cli)

## <a name="analytics"></a>Analitik

Gunakan Azure Analytics untuk mengumpulkan, menyimpan, memproses, menganalisis, dan memvisualisasikan data dengan berbagai bentuk, volume, atau kecepatan.

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Azure Data Explorer](/cli/azure/service-page/azure%20data%20explorer) | [Membuat kluster dan database Azure Data Explorer menggunakan Azure CLI](/azure/data-explorer/create-cluster-database-cli)
|| [Menyerap data dari Apache Kafka ke Azure Data Explorer](/azure/data-explorer/ingest-data-kafka)
|[Azure Data Factory](/cli/azure/service-page/azure%20data%20factory) | [Mulai Cepat: Membuat Azure Data Factory](/azure/data-factory/quickstart-create-data-factory-azure-cli)
|[Data Lake Analytics](/cli/azure/service-page/azure%20data%20lake%20analytics) | [Mengelola Azure Data Lake Analytics](/azure/data-lake-analytics/data-lake-analytics-manage-use-cli)
|[Azure Data Lake Storage](/cli/azure/service-page/azure%20data%20lake%20storage) |[Memulai dengan Azure Data Lake Storage Gen1](/azure/data-lake-store/data-lake-store-get-started-cli-2.0)
|| [Mulai menggunakan Azure Data Lake Analytics](/azure/data-lake-analytics/data-lake-analytics-get-started-cli)
|[Azure Data Share](azure-cli-reference-for-data-share.md) | [Tutorial: Berbagi data menggunakan Azure Data Share](/azure/data-share/share-your-data?tabs=azure-cli)
|| [Terima dan dapatkan data menggunakan Azure Data Share](/azure/data-share/subscribe-to-data-share?tabs=azure-cli)
|[Azure Databricks](/cli/azure/service-page/azure%20databricks) | [Mulai Cepat: Menjalankan pekerjaan Spark di Ruang Kerja Azure Databricks](/azure/databricks/scenarios/quickstart-create-databricks-workspace-portal?tabs=azure-cli)
|| [Membuat alur data menggunakan Azure Data Factory, DevOps, dan ML](/azure/devops/pipelines/apps/cd/azure/build-data-pipeline?view=azure-devops&preserve-view=true)
|[Azure HDInsight](/cli/azure/service-page/azure%20hdinsight) | [Mengelola kluster Azure HDInsight](/azure/hdinsight/hdinsight-administer-use-command-line)
|| [Membuat kluster yang didukung proksi Apache Kafka REST di HDInsight](/azure/hdinsight/kafka/tutorial-cli-rest-proxy)
|[Event Hubs](/cli/azure/service-page/azure%20event%20hubs) | [Merutekan peristiwa kustom ke Azure Event Hubs](/azure/event-grid/custom-event-to-eventhub)
|| [Menggunakan Azure Event Hubs untuk menerima pemberitahuan perubahan](/graph/change-notifications-delivery#using-azure-event-hubs-to-receive-change-notifications)
|| [Visualisasikan anomali data dalam peristiwa waktu nyata yang dikirim ke Azure Event Hubs](/azure/event-hubs/event-hubs-tutorial-visualize-anomalies)
|[Azure Stream Analytics](/cli/azure/service-page/azure%20stream%20analytics) | [Membuat pekerjaan Azure Stream Analytics](/azure/stream-analytics/quick-create-azure-cli)
|[Azure Synapse Analytics](/cli/azure/service-page/azure%20synapse%20analytics) | [Membuat ruang kerja Azure Synapse](/azure/synapse-analytics/quickstart-create-workspace-cli)
|| [Membuat kumpulan Synapse SQL](/azure/synapse-analytics/sql-data-warehouse/create-data-warehouse-azure-cli)
|[Power BI Embedded](/cli/azure/powerbi) | [Membuat kapasitas Power BI Embedded](/power-bi/developer/embedded/azure-pbie-create-capacity?tabs=CLI)

## <a name="blockchain"></a>Blockchain

Bangun dan kelola aplikasi berbasis blockchain dengan serangkaian alat terintegrasi.

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Blockchain](/cli/azure/service-page/azure%20blockchain)|
|[Azure Cosmos DB](azure-cli-reference-for-cosmos-db.md) | [Membuat akun Azure Cosmos](/azure/cosmos-db/create-sql-api-dotnet-v4#create-account)
|| [Mengonfigurasi kebijakan kontrol akses IP](/azure/cosmos-db/how-to-configure-firewall#configure-ip-firewall-cli)
|| [Membuat definisi peran kustom](/azure/cosmos-db/how-to-setup-rbac#using-the-azure-cli)
|[Azure Logic Apps](/cli/azure/service-page/azure%20logic%20apps) | [Membuat dan mengelola alur kerja di Azure Logic Apps multi-penyewa](/azure/logic-apps/quickstart-logic-apps-azure-cli)
|| [Membuat dan mengelola akun integrasi untuk integrasi perusahaan B2B](/azure/logic-apps/logic-apps-enterprise-integration-create-integration-account?tabs=azure-cli)
|| [Membuat sampel skrip Aplikasi Logika](/azure/logic-apps/sample-logic-apps-cli-script)

## <a name="compute"></a>Compute

Akses kapasitas komputasi cloud dan skalakan sesuai permintaan—dan hanya bayar sesuai pemakaian sumber daya.  Baik Anda membuat aplikasi baru atau menyebarkan aplikasi yang sudah ada, Azure Compute dilengkapi dengan infrastruktur yang dibutuhkan untuk menjalankan aplikasi.

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[App Service](/cli/azure/service-page/azure%20app%20service) | [Cara menggunakan identitas terkelola untuk App Service dan Azure Functions](/azure/app-service/overview-managed-identity?tabs=dotnet#using-the-azure-cli)
| |[Mengonfigurasi App Service untuk menyebarkan citra dari registri](/azure/app-service/tutorial-custom-container?pivots=container-linux#configure-app-service-to-deploy-the-image-from-the-registry)
| |[Mengunggah data citra di cloud dengan Azure Storage](/azure/storage/blobs/storage-upload-process-images?tabs=dotnet%2Cazure-cli#create-an-app-service-plan)
|[Azure Batch](/cli/azure/service-page/azure%20batch) | [Menjalankan pekerjaan Batch pertama](/azure/batch/quick-create-cli)
|[Microsoft Azure Cloud Services](/cli/azure/service-page/azure%20cloud%20services%20(extended%20support))
|[Azure Container Instances](/cli/azure/service-page/azure%20container%20instances)| [Menyebarkan instans kontainer di Azure](/azure/container-instances/container-instances-quickstart)
|[Azure Functions](/cli/azure/service-page/azure%20functions) | [Mengelola aplikasi fungsi Anda](/azure/azure-functions/functions-how-to-use-azure-function-app-settings?tabs=azure-cli)
| |[Cara menargetkan versi runtime Azure Functions](/azure/azure-functions/set-runtime-version?tabs=azurecli)
|[Azure Kubernetes Service (AKS)](/cli/azure/service-page/azure%20kubernetes%20service%20(aks)) | [Menyebarkan kluster AKS](/azure/aks/kubernetes-walkthrough)
| |[Membuat dan mengelola beberapa kumpulan simpul untuk kluster di AKS](/azure/aks/use-multiple-node-pools)
|[Struktur Layanan Azure](/cli/azure/service-page/azure%20service%20fabric) | [Menyebarkan kontainer Linux untuk Service Fabric](/azure/service-fabric/service-fabric-quickstart-containers-linux#create-a-service-fabric-cluster)
| |[Membuat kluster Microsoft Azure Service Fabric](/azure/service-fabric/service-fabric-cluster-creation-via-arm)
|[Azure Spring Cloud](/cli/azure/service-page/azure%20spring%20cloud) | [Baca rahasia dari Azure Key Vault di aplikasi Spring Boot](/azure/developer/java/spring-framework/configure-spring-boot-starter-java-app-with-azure-key-vault#deploy-to-azure-spring-cloud)
|[Azure Static Web Apps](/cli/azure/staticwebapp) | [Membangun situs statik pertama](/azure/static-web-apps/get-started-cli?tabs=vanilla-javascript)
|[Komputer Virtual Azure](/cli/azure/azure-cli-reference-for-virtual-machines) | [Membuat Linux VM](/azure/virtual-machines/linux/quick-create-cli)
| |[Membuat VM Windows](/azure/virtual-machines/windows/quick-create-cli)
|[Azure Virtual Machine Scale Sets (VMSS)](/cli/azure/vmss) | [Membuat VM Linux dengan Jaringan yang Dipercepat](/azure/virtual-network/create-vm-accelerated-networking-cli#vmss)
|[Azure VMWare Solution](/cli/azure/service-page/azure%20vmware%20solution) | [Melampirkan gabungan disk ke host Azure VMware Solution](/azure/azure-vmware/attach-disk-pools-to-azure-vmware-solution-hosts)
|[Azure Web Apps](/cli/azure/service-page/azure%20web%20apps) | [Cara menggunakan identitas terkelola untuk App Service dan Azure Functions](/azure/app-service/overview-managed-identity?tabs=dotnet#using-the-azure-cli)
| |[Mengonfigurasikan kontainer kustom untuk Azure App Service ](/azure/app-service/configure-custom-container?pivots=container-linux)

## <a name="containers"></a>Kontainer

Kembangkan dan kelola aplikasi kontainer Anda lebih cepat dengan alat terintegrasi.  Hemat biaya dengan mengangkat dan mengalihkan aplikasi yang ada ke kontainer, dan buat aplikasi layanan mikro untuk memberikan nilai kepada pengguna Anda lebih cepat.

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Azure Functions](/cli/azure/service-page/azure%20functions) | [Mengelola aplikasi fungsi Anda](/azure/azure-functions/functions-how-to-use-azure-function-app-settings?tabs=azure-cli)
| |[Cara menargetkan versi runtime Azure Functions](/azure/azure-functions/set-runtime-version?tabs=azurecli)
|[Azure Kubernetes Service (AKS)](/cli/azure/service-page/azure%20kubernetes%20service%20(aks)) | [Menyebarkan kluster AKS](/azure/aks/kubernetes-walkthrough)
| |[Membuat dan mengelola beberapa kumpulan simpul untuk kluster di AKS](/azure/aks/use-multiple-node-pools)
|[Azure Red Hat OpenShift](/cli/azure/service-page/azure%20red%20hat%20openshift) | [Menghapus kluster Azure Red Hat OpenShift 4](/azure/openshift/tutorial-create-cluster)
|[Struktur Layanan Azure](/cli/azure/service-page/azure%20service%20fabric) | [Menyebarkan kontainer Linux untuk Service Fabric](/azure/service-fabric/service-fabric-quickstart-containers-linux#create-a-service-fabric-cluster)
| |[Membuat kluster Microsoft Azure Service Fabric](/azure/service-fabric/service-fabric-cluster-creation-via-arm)
|[Azure Web Apps](/cli/azure/service-page/azure%20web%20apps) | [Cara menggunakan identitas terkelola untuk App Service dan Azure Functions](/azure/app-service/overview-managed-identity?tabs=dotnet#using-the-azure-cli)
| |[Mengonfigurasikan kontainer kustom untuk Azure App Service ](/azure/app-service/configure-custom-container?pivots=container-linux)
|[Container Instances](/cli/azure/service-page/azure%20container%20instances) | [Menyebarkan instans kontainer di Azure](/azure/container-instances/container-instances-quickstart)
|[Container Registry](/cli/azure/service-page/azure%20container%20registries) | [Tanya jawab umum](/azure/container-registry/container-registry-faq)
| |[Hubungkan secara pribadi ke registri kontainer Azure menggunakan Azure Private Link](/azure/container-registry/container-registry-private-link#set-up-private-endpoint---cli)

## <a name="databases"></a>Database

Mendukung pertumbuhan yang pesat dan berinovasi lebih cepat dengan layanan database yang dikelola sepenuhnya, aman, dan tingkat perusahaan.

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Azure API for FHIR](/cli/azure/service-page/azure%20api%20for%20fhir) | [Mengonfigurasi kunci yang dikelola pelanggan saat tidak aktif](/azure/healthcare-apis/azure-api-for-fhir/customer-managed-key#using-azure-cli)
|[Azure Cache untuk Redis](/cli/azure/service-page/azure%20cache%20for%20redis) | [Menghubungkan aplikasi App Service ke Azure Cache for Redis](/azure/app-service/scripts/cli-connect-to-redis)
|[Azure Cosmos DB](azure-cli-reference-for-cosmos-db.md) | [Sampel untuk Azure Cosmos DB Core (SQL) API](/azure/cosmos-db/cli-samples)
|[Migrasi Data Azure](/cli/azure/service-page/azure%20data%20migration) | [Memigrasikan PostgreSQL ke Azure DB](/azure/dms/tutorial-postgresql-azure-postgresql-online#provisioning-an-instance-of-dms-using-the-azure-cli)
|[Azure Database untuk MariaDB](/cli/azure/service-page/azure%20database%20for%20mariadb) | [Membuat server Azure Database for MariaDB](/azure/mariadb/quickstart-create-mariadb-server-database-using-azure-cli)
|[Azure Database untuk MySQL](/cli/azure/service-page/azure%20database%20for%20mysql) | [Membuat Server Fleksibel MySQL](/azure/mysql/flexible-server/tutorial-php-database-app#create-a-mysql-flexible-server-preview)
|[Azure Database untuk PostgreSQL](/cli/azure/service-page/azure%20database%20for%20postgresql) | [Membuat server Azure DB for PostgreSQL](/azure/postgresql/quickstart-create-server-database-azure-cli)
|[Azure SQL Database](/cli/azure/azure-cli-reference-for-sql#sql-database) | [Membuat Azure SQL Database](/azure/azure-sql/database/single-database-create-quickstart?tabs=azure-cli)
| |[Mengelola aturan firewall IP tingkat layanan](/azure/azure-sql/database/firewall-configure#use-cli-to-manage-server-level-ip-firewall-rules)

## <a name="developer-tools"></a>Alat Pengembang

Gunakan seperangkat alat pengembangan komprehensif Microsoft untuk membangun, mengelola, dan tetap memberikan aplikasi cloud—menggunakan platform atau bahasa apa pun.

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Konfigurasi Aplikasi](/cli/azure/azure-cli-reference-for-hosted-apps#azure-web-app-configuration) | [Memigrasikan perangkat lunak kustom ke Azure App Service menggunakan kontainer kustom](/azure/app-service/tutorial-custom-container?pivots=container-linux)
| |[Membangun aplikasi ASP.NET Core dan Azure SQL Database di Azure App Service](/azure/app-service/tutorial-dotnetcore-sqldb-app?pivots=platform-linux)
|[Azure DevOps](azure-cli-reference-for-devops.md) | Lihat tautan dalam ringkasan referensi.
|[Azure DevTest Labs](/cli/azure/service-page/azure%20devtest%20labs) | [Membuat dan mengelola mesin virtual dengan DevTest Labs](/azure/devtest-labs/devtest-lab-vmcli)
|[Azure Lab Services](/cli/azure/service-page/azure%20lab%20services) |
|[Azure Pipelines](/cli/azure/azure-cli-reference-for-devops#azure-pipelines) | [Cara menentukan variabel alur](/azure/devops/pipelines/process/variables?view=azure-devops&preserve-view=true&tabs=azure-devops-cli)
| |[Agen Azure Pipelines](/azure/devops/pipelines/agents/agents?view=azure-devops&preserve-view=true&tabs=azure-devops-cli)
| |[Membuat alur pertama Anda](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&preserve-view=true&tabs=azure-cli)
|[Visual Studio](/cli/azure/service-page/visual%20studio) |

## <a name="devops"></a>DevOps

Teknologi Azure DevOps menghadirkan inovasi lebih cepat dengan alat yang sederhana dan andal untuk pengiriman berkelanjutan.

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Azure Artifacts](/cli/azure/azure-cli-reference-for-devops#azure-artifacts) | [Menerbitkan dan mengunduh paket universal](/azure/devops/artifacts/quickstarts/universal-packages?view=azure-devops&preserve-view=true)
|[Azure Boards](/cli/azure/azure-cli-reference-for-devops#azure-boards) | [Menentukan jalur area dan menetapkan ke tim](/azure/devops/organizations/settings/set-area-paths?view=azure-devops&preserve-view=true&tabs=azure-devops-cli#open-project-settings-list-project-areas)
|[Azure DevOps](/cli/azure/azure-cli-reference-for-devops) | Lihat tautan dalam ringkasan referensi.
|[Azure DevTest Labs](/cli/azure/service-page/azure%20devtest%20labs) | [Membuat dan mengelola mesin virtual dengan DevTest Labs](/azure/devtest-labs/devtest-lab-vmcli)
|[Azure Monitor](azure-cli-reference-for-monitor.md) | [Membuat pengaturan diagnostik untuk mengirim log dan metrik platform ke tujuan yang berbeda](/azure/azure-monitor/essentials/diagnostic-settings?tabs=CMD#create-using-azure-cli)
| |[Cara mengonfigurasi profil Log aktivitas Azure](/azure/azure-monitor/essentials/activity-log#configure-log-profile-using-azure-cli)
|[Azure Pipelines](/cli/azure/azure-cli-reference-for-devops#azure-pipelines) | [Cara menentukan variabel alur](/azure/devops/pipelines/process/variables?view=azure-devops&preserve-view=true&tabs=azure-devops-cli)
| |[Agen Azure Pipelines](/azure/devops/pipelines/agents/agents?view=azure-devops&preserve-view=true&tabs=azure-devops-cli)
| |[Membuat alur pertama Anda](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&preserve-view=true&tabs=azure-cli)
|[Azure Repos](/cli/azure/azure-cli-reference-for-devops#azure-repos) | [Mulai menggunakan Git dengan Azure CLI](/azure/devops/repos/git/share-your-code-in-git-cmdline?view=azure-devops&preserve-view=true)

## <a name="hybrid"></a>Hibrid

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Azure Active Directory (AD)](/cli/azure/service-page/azure%20active%20directory) | [Membuat perwakilan layanan Azure](create-an-azure-service-principal-azure-cli.md)
|[Azure Arc](/cli/azure/service-page/azure%20arc) | [Menghapus pengontrol data Azure Arc](/azure/azure-arc/data/uninstall-azure-arc-data-controller)
|[Azure Database untuk PostgreSQL](/cli/azure/service-page/azure%20database%20for%20postgresql) | [Menyebarkan aplikasi web Django dengan PostgreSQL di Azure App Service](/azure/app-service/tutorial-python-postgresql-app?tabs=cmd%2Cclone&pivots=postgres-single-server)
|[Azure DevOps](azure-cli-reference-for-devops.md) | Lihat tautan dalam ringkasan referensi.
|[Azure IoT Edge](/cli/azure/iot/edge) | [Menyebarkan modul IoT Edge pertama Anda ke perangkat Linux virtual](/azure/iot-edge/quickstart-linux)
|[Azure Security Center](/cli/azure/service-page/azure%20security%20center) |
|[Azure Sentinel](/cli/azure/service-page/azure%20sentinel) |
|[Azure SQL Database](/cli/azure/azure-cli-reference-for-sql#sql-database) | [Memulihkan database tunggal di Azure SQL Database ke titik waktu sebelumnya](/azure/sql-database/scripts/sql-database-restore-database-cli)
|[Azure Stack HCI](/cli/azure/stack-hci) |

## <a name="identity"></a>Identitas

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Azure Active Directory (AD)](/cli/azure/service-page/azure%20active%20directory) | [Membuat perwakilan layanan Azure](create-an-azure-service-principal-azure-cli.md)

## <a name="integration"></a>Integrasi

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[API Management](/cli/azure/service-page/api%20management) | [Membuat respons API](/azure/api-management/mock-api-responses?tabs=azure-cli)
| |[Membuat dan menerbitkan produk](/azure/api-management/api-management-howto-add-products?tabs=azure-cli)
|[Azure Logic Apps](/cli/azure/service-page/azure%20logic%20apps) | [Buat dan kelola akun integrasi untuk integrasi perusahaan B2B di Azure Logic Apps](/azure/logic-apps/logic-apps-enterprise-integration-create-integration-account?tabs=azure-cli)
|[Event Grid](/cli/azure/service-page/azure%20event%20grid) | [Merutekan kejadian kustom ke titik akhir web](/azure/event-grid/custom-event-quickstart)
|[Service Bus](/cli/azure/service-page/azure%20service%20bus%20messaging) | [Mengaktifkan dead-lettering saat kedaluwarsa pesan untuk antrean dan langganan Azure Service Bus](/azure/service-bus-messaging/enable-dead-letter#using-azure-cli)

## <a name="internet-of-things"></a>Internet of Things

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[API Management](/cli/azure/service-page/api%20management) | [Membuat respons API](/azure/api-management/mock-api-responses?tabs=azure-cli)
| |[Membuat dan menerbitkan produk](/azure/api-management/api-management-howto-add-products?tabs=azure-cli)
|[Azure Cosmos DB](azure-cli-reference-for-cosmos-db.md) | [Sampel untuk Azure Cosmos DB Core (SQL) API](/azure/cosmos-db/cli-samples)
|[Azure Functions](/cli/azure/service-page/azure%20functions) | [Mengelola aplikasi fungsi Anda](/azure/azure-functions/functions-how-to-use-azure-function-app-settings?tabs=azure-cli)
| |[Cara menargetkan versi runtime Azure Functions](/azure/azure-functions/set-runtime-version?tabs=azurecli)
|[Azure IoT Central](/cli/azure/iot/central) | [Mengelola IoT Central](/azure/iot-central/core/howto-manage-iot-central-from-cli?tabs=azure-cli)
|[Azure IoT Edge](/cli/azure/iot/edge) | [Menyebarkan dan memantau modul IoT Edge dalam skala besar](/azure/iot-edge/how-to-deploy-cli-at-scale)
| |[Menyebarkan modul IoT Edge pertama Anda ke perangkat Linux virtual](/azure/iot-edge/quickstart-linux)
|[Azure IoT Hub](/cli/azure/iot/hub) | [Mengonfigurasi perutean pesan IoT Hub](/azure/iot-hub/tutorial-routing)
|[Azure Logic Apps](/cli/azure/service-page/azure%20logic%20apps) | [Buat dan kelola akun integrasi untuk integrasi perusahaan B2B di Azure Logic Apps](/azure/logic-apps/logic-apps-enterprise-integration-create-integration-account?tabs=azure-cli)
|[Pembelajaran Mesin Azure](/cli/azure/service-page/azure%20machine%20learning) | [Membuat dan mengelolar instans komputasi Azure Machine Learning](/azure/machine-learning/how-to-create-manage-compute-instance?tabs=azure-cli)
| |[Kelola akses ke ruang kerja Azure Machine Learning](/azure/machine-learning/how-to-assign-roles)
|[Azure Maps](/cli/azure/maps) |
|[Azure Notification Hubs](/cli/azure/service-page/azure%20notification%20hubs) | [Menyiapkan pemberitahuan push di hub pemberitahuan](/azure/notification-hubs/configure-notification-hub-portal-pns-settings?tabs=azure-cli)
| | [Membuat hub pemberitahuan Azure menggunakan Azure CLI](/azure/notification-hubs/create-notification-hub-azure-cli)
|[Azure Stream Analytics](/cli/azure/service-page/azure%20stream%20analytics) | [Membuat pekerjaan Azure Stream Analytics menggunakan Azure CLI](/azure/stream-analytics/quick-create-azure-cli)
|[Azure Time Series Insights](/cli/azure/service-page/azure%20time%20series%20insights) | [Autentikasi dan otorisasi untuk API Azure Time Series Insights](/azure/time-series-insights/time-series-insights-authentication-and-authorization)
| | [Membuat lingkungan Azure Time Series Insights Gen2 menggunakan Azure CLI](/azure/time-series-insights/how-to-create-environment-using-cli)
|[Event Grid](/cli/azure/service-page/azure%20event%20grid) | [Merutekan kejadian kustom ke titik akhir web](/azure/event-grid/custom-event-quickstart)

## <a name="management-and-governance"></a>Manajemen dan Tata Kelola

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Automation](/cli/azure/automation) | [Aktifkan Manajemen Pembaruan menggunakan template Azure Resource Manager](/azure/automation/update-management/enable-from-template)
|[Azure Advisor](/cli/azure/advisor) | [Membuat peringatan Azure Advisor tentang rekomendasi baru menggunakan template ARM](/azure/advisor/advisor-alerts-arm?tabs=CLI)
|[Pencadangan Azure](/cli/azure/backup) | [Pencadangan dan pemulihan disk selektif untuk komputer virtual Azure](/azure/backup/selective-disk-backup-restore)
| | [Mencadangkan komputer virtual di Azure dengan Azure CLI](/azure/backup/quick-backup-vm-cli)
|[Azure Blueprint](/cli/azure/blueprint) | [Menentukan dan Menetapkan Azure Blueprint dengan Azure CLI](/azure/governance/blueprints/create-blueprint-azurecli)
|[Azure Cost Management and Billing](/cli/azure/service-page/azure%20cost%20management%20+%20billing) | [Membuat dan mengelola data yang diekspor](/azure/cost-management-billing/costs/tutorial-export-acm-data?tabs=azure-cli)
| |[Membuat langganan Perjanjian Enterprise Azure dengan API terbaru secara terprogram](/azure/cost-management-billing/manage/programmatically-create-subscription-enterprise-agreement?tabs=azure-cli)
|[Azure Managed Applications](/cli/azure/service-page/azure%20managed%20applications) | [Membuat dan menerbitkan definisi aplikasi terkelola](/azure/azure-resource-manager/managed-applications/publish-service-catalog-app?tabs=azure-cli)
| | [Membuat aplikasi terkelola dengan tindakan dan sumber daya kustom](/azure/azure-resource-manager/managed-applications/tutorial-create-managed-app-with-custom-provider?tabs=azurecli-interactive)
|[Azure Monitor](azure-cli-reference-for-monitor.md) | [Membuat pengaturan diagnostik untuk mengirim log dan metrik platform ke tujuan yang berbeda](/azure/azure-monitor/essentials/diagnostic-settings?tabs=CMD#create-using-azure-cli)
| |[Cara mengonfigurasi profil Log aktivitas Azure](/azure/azure-monitor/essentials/activity-log#configure-log-profile-using-azure-cli)
|[Kebijakan Azure](/cli/azure/service-page/azure%20policy) | [Membuat definisi kebijakan Azure dengan Azure CLI](/azure/governance/policy/tutorials/create-and-manage#create-a-policy-definition-with-azure-cli)
| |[Meremediasi sumber daya yang tidak mematuhi tugas remediasi Azure Policy](/azure/governance/policy/how-to/remediate-resources#create-a-remediation-task-through-azure-cli)
|[Azure Resource Manager](/cli/azure/service-page/azure%20resource%20manager) | [Menggunakan tag untuk menata hierarki sumber daya dan manajemen Azure Anda](/azure/azure-resource-manager/management/tag-resources#azure-cli)
| | [Kelola grup sumber daya Azure Resource Manager dengan menggunakan Azure CLI](/azure/azure-resource-manager/management/manage-resource-groups-cli)
|[Templat Azure Resource Manager](/cli/azure/group) | [Spesifikasi templat Azure Resource Manager](/azure/azure-resource-manager/templates/template-specs?tabs=azure-cli)
| | [Membuat dan menerapkan spesifikasi templat](/azure/azure-resource-manager/templates/quickstart-create-template-specs?tabs=azure-cli)
|[Traffic Manager](/cli/azure/network/traffic-manager/) | [Membuat profil Traffic Manager untuk aplikasi web dengan ketersediaan tinggi menggunakan Azure CLI](/azure/traffic-manager/quickstart-create-traffic-manager-profile-cli)

## <a name="media"></a>Media

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Jaringan Pengiriman Konten](/cli/azure/service-page/content%20delivery%20network) | [Membuat profil dan titik akhir Azure CDN menggunakan Azure CLI](/azure/cdn/scripts/cli/cdn-azure-cli-create-endpoint)
|[Media Services](/cli/azure/service-page/azure%20media%20services) | [Mengodekan file jarak jauh berdasarkan URL dan streaming video - Azure CLI](/azure/media-services/latest/stream-files-cli-quickstart)
| | [Membuat dan memantau peristiwa Media Services dengan Event Grid menggunakan Azure CLI](/azure/media-services/latest/monitoring/job-state-events-cli-how-to)

## <a name="migration"></a>Migration

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Azure Cost Management and Billing](/cli/azure/service-page/azure%20cost%20management%20+%20billing) | [Menjelajahi dan menganalisis biaya dengan analisis biaya](/azure/cost-management-billing/costs/quick-acm-cost-analysis)
| |[Membuat langganan Perjanjian Enterprise Azure dengan API terbaru secara terprogram](/azure/cost-management-billing/manage/programmatically-create-subscription-enterprise-agreement?tabs=azure-cli)

## <a name="mobile"></a>Seluler

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[API Management](/cli/azure/service-page/api%20management) | [Membuat respons API](/azure/api-management/mock-api-responses?tabs=azure-cli)
| |[Membuat dan menerbitkan produk](/azure/api-management/api-management-howto-add-products?tabs=azure-cli)
|[App Service](/cli/azure/service-page/azure%20app%20service) | [Cara menggunakan identitas terkelola untuk App Service dan Azure Functions](/azure/app-service/overview-managed-identity?tabs=dotnet#using-the-azure-cli)
| |[Mengonfigurasi App Service untuk menyebarkan citra dari registri](/azure/app-service/tutorial-custom-container?pivots=container-linux#configure-app-service-to-deploy-the-image-from-the-registry)
| |[Mengunggah data citra di cloud dengan Azure Storage](/azure/storage/blobs/storage-upload-process-images?tabs=dotnet%2Cazure-cli#create-an-app-service-plan)
|[Azure Cognitive Search](/cli/azure/service-page/azure%20cognitive%20search)|[Mengelola layanan Azure Cognitive Search](/azure/search/search-manage-azure-cli)
|[Azure Communication Services](/cli/azure/service-page/azure%20communication%20service) | [Membuat dan mengelola sumber daya Communication Services](/azure/communication-services/quickstarts/create-communication-resource?tabs=linux&pivots=platform-azcli)
|[Migrasi Data Azure](/cli/azure/service-page/azure%20data%20migration) | [Memigrasikan PostgreSQL ke Azure DB](/azure/dms/tutorial-postgresql-azure-postgresql-online#provisioning-an-instance-of-dms-using-the-azure-cli)
|[Azure Notification Hubs](/cli/azure/service-page/azure%20notification%20hubs) | [Menyiapkan pemberitahuan push di hub pemberitahuan](/azure/notification-hubs/configure-notification-hub-portal-pns-settings?tabs=azure-cli)
| | [Membuat hub pemberitahuan Azure menggunakan Azure CLI](/azure/notification-hubs/create-notification-hub-azure-cli?tabs=azure-cli)
|[Spatial Anchors](/cli/azure/service-page/azure%20spatial%20anchors) | [Buat sumber daya Spatial Anchors](/azure/spatial-anchors/quickstarts/get-started-android?tabs=azure-cli#create-a-spatial-anchors-resource)

## <a name="networking"></a>Jaringan

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Azure DNS](/cli/azure/network/dns) | [Mengimpor dan mengekspor file zona DNS menggunakan Azure CLI](/azure/dns/dns-import-export)
| | [Menghosting zona pencarian reverse DNS di Azure DNS](/azure/dns/dns-reverse-dns-hosting)
|[Tautan Privat Azure](/cli/azure/network/private-link-service) | [Membuat layanan Private Link menggunakan Azure CLI](/azure/private-link/create-private-link-service-cli)
|[Jaringan Pengiriman Konten](/cli/azure/service-page/content%20delivery%20network) | [Membuat profil dan titik akhir Azure CDN menggunakan Azure CLI](/azure/cdn/scripts/cli/cdn-azure-cli-create-endpoint)
|[Load Balancer](/cli/azure/network/lb) | [Pengelolaan kumpulan backend](/azure/load-balancer/backend-pool-management)
| | [Memantau load balancer](/azure/load-balancer/monitor-load-balancer)
|[Traffic Manager](/cli/azure/network/traffic-manager/) | [Membuat profil Traffic Manager untuk aplikasi web dengan ketersediaan tinggi menggunakan Azure CLI](/azure/traffic-manager/quickstart-create-traffic-manager-profile-cli)
|[Jaringan Virtual](/cli/azure/network/vnet) | [Membuat komputer virtual Linux dengan Jaringan yang Dipercepat menggunakan Azure CLI](/azure/virtual-network/create-vm-accelerated-networking-cli)
| | [Membuat peering jaringan virtual - Resource Manager, langganan yang berbeda, dan penyewa Azure Active Directory](/azure/virtual-network/create-peering-different-subscriptions)
| | [Menambahkan atau menghapus delegasi subnet](/azure/virtual-network/manage-subnet-delegation#azure-cli)

## <a name="security"></a>Keamanan

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Azure Active Directory (AD)](/cli/azure/service-page/azure%20active%20directory) | [Membuat perwakilan layanan Azure](create-an-azure-service-principal-azure-cli.md)
|[Azure Dedicated HSM](/cli/azure/service-page/azure%20dedicated%20hsm) | [Menyebarkan HSM ke jaringan virtual yang ada menggunakan Azure CLI](/azure/dedicated-hsm/tutorial-deploy-hsm-cli)
|[Azure Security Center](/cli/azure/service-page/azure%20security%20center) |
|[Azure Sentinel](/cli/azure/service-page/azure%20sentinel) |
|[Key Vault](/cli/azure/service-page/azure%20key%20vault) | [Gunakan identitas terkelola untuk menghubungkan Key Vault ke aplikasi web Azure di .NET](/azure/key-vault/general/tutorial-net-create-vault-azure-web-app)
| | [Mengatur dan mengambil rahasia dari Azure Key Vault menggunakan Azure CLI](/azure/key-vault/secrets/quick-create-cli)
|[Microsoft Azure Attestation](/cli/azure/service-page/azure%20attestation) | [Menyiapkan Azure Attestation dengan Azure CLI](/azure/attestation/quickstart-azure-cli)

## <a name="storage"></a>Penyimpanan

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[Pencadangan Azure](/cli/azure/backup) | [Pencadangan dan pemulihan disk selektif untuk komputer virtual Azure](/azure/backup/selective-disk-backup-restore)
| | [Mencadangkan komputer virtual di Azure dengan Azure CLI](/azure/backup/quick-backup-vm-cli)
|[Azure Data Lake Storage](/cli/azure/service-page/azure%20data%20lake%20storage) |[Memulai dengan Azure Data Lake Storage Gen1](/azure/data-lake-store/data-lake-store-get-started-cli-2.0)
|| [Mulai menggunakan Azure Data Lake Analytics](/azure/data-lake-analytics/data-lake-analytics-get-started-cli)
|[Azure Data Share](azure-cli-reference-for-data-share.md) | [Tutorial: Berbagi data menggunakan Azure Data Share](/azure/data-share/share-your-data?tabs=azure-cli)
|| [Terima dan dapatkan data menggunakan Azure Data Share](/azure/data-share/subscribe-to-data-share?tabs=azure-cli)
|[Azure Disk Storage](/cli/azure/service-page/azure%20disk%20storage) |
|[Azure HPC Cache](/cli/azure/service-page/azure%20hpc%20cache) | [Membuat Azure HPC Cache](/azure/hpc-cache/hpc-cache-create?tabs=azure-cli)
| | [Mengelola cache Anda](/azure/hpc-cache/hpc-cache-manage?tabs=azure-cli)
|[File Azure NetApp](/cli/azure/service-page/azure%20netapp%20files) | [Menyiapkan Azure NetApp Files dan membuat Volume NFS](/azure/azure-netapp-files/azure-netapp-files-quickstart-set-up-account-create-volumes?tabs=azure-cli)
|[Azure Storage](/cli/azure/azure-cli-reference-for-storage) | [Mengonfigurasi firewall dan jaringan virtual Azure Storage](/azure/storage/common/storage-network-security?tabs=azure-cli)
| | [Buat akun penyimpanan](/azure/storage/common/storage-account-create?tabs=azure-cli)
| | [Membuat berbagi file Azure](/azure/storage/files/storage-how-to-create-file-share?tabs=azure-cli)
|[Akun Penyimpanan](/cli/azure/azure-cli-reference-for-storage#storage-accounts) | [Buat akun penyimpanan](/azure/storage/common/storage-account-create?tabs=azure-cli)
| | [Mengelola kunci akses akun penyimpanan](/azure/storage/common/storage-account-keys-manage?tabs=azure-cli).

## <a name="web"></a>Web

| Referensi Azure CLI untuk layanan | Microsoft Docs
|-|-|
|[App Service](/cli/azure/service-page/azure%20app%20service) | [Cara menggunakan identitas terkelola untuk App Service dan Azure Functions](/azure/app-service/overview-managed-identity?tabs=dotnet#using-the-azure-cli)
| |[Mengonfigurasi App Service untuk menyebarkan citra dari registri](/azure/app-service/tutorial-custom-container?pivots=container-linux#configure-app-service-to-deploy-the-image-from-the-registry)
| |[Mengunggah data citra di cloud dengan Azure Storage](/azure/storage/blobs/storage-upload-process-images?tabs=dotnet%2Cazure-cli#create-an-app-service-plan)
|[API Management](/cli/azure/service-page/api%20management) | [Membuat respons API](/azure/api-management/mock-api-responses?tabs=azure-cli)
| |[Membuat dan menerbitkan produk](/azure/api-management/api-management-howto-add-products?tabs=azure-cli)
|[Azure Cognitive Search](/cli/azure/service-page/azure%20cognitive%20search)|[Mengelola layanan Azure Cognitive Search](/azure/search/search-manage-azure-cli)
|[Azure Communication Services](/cli/azure/service-page/azure%20communication%20service) | [Membuat dan mengelola sumber daya Communication Services](/azure/communication-services/quickstarts/create-communication-resource?tabs=linux&pivots=platform-azcli)
|[Azure Notification Hubs](/cli/azure/service-page/azure%20notification%20hubs) | [Menyiapkan pemberitahuan push di hub pemberitahuan](/azure/notification-hubs/configure-notification-hub-portal-pns-settings?tabs=azure-cli)
| | [Membuat hub pemberitahuan Azure menggunakan Azure CLI](/azure/notification-hubs/create-notification-hub-azure-cli?tabs=azure-cli)
|[Azure SignalR](/cli/azure/service-page/azure%20signalr) | [Autentikasi Azure SignalR Service](/azure/azure-signalr/signalr-concept-authenticate-oauth)
| | [Menggunakan titik akhir pribadi untuk Azure SignalR Service](/azure/azure-signalr/howto-private-endpoints#create-a-private-endpoint-using-azure-cli)
|[Azure Spring Cloud](/cli/azure/service-page/azure%20spring%20cloud) | [Baca rahasia dari Azure Key Vault di aplikasi Spring Boot](/azure/developer/java/spring-framework/configure-spring-boot-starter-java-app-with-azure-key-vault#deploy-to-azure-spring-cloud)
|[Azure Web Apps](/cli/azure/service-page/azure%20web%20apps) | [Cara menggunakan identitas terkelola untuk App Service dan Azure Functions](/azure/app-service/overview-managed-identity?tabs=dotnet#using-the-azure-cli)
| |[Mengonfigurasikan kontainer kustom untuk Azure App Service ](/azure/app-service/configure-custom-container?pivots=container-linux)
|[Jaringan Pengiriman Konten](/cli/azure/service-page/content%20delivery%20network) | [Membuat profil dan titik akhir Azure CDN menggunakan Azure CLI](/azure/cdn/scripts/cli/cdn-azure-cli-create-endpoint)
|[Azure Static Web Apps](/cli/azure/staticwebapp) | [Membangun situs statik pertama](/azure/static-web-apps/get-started-cli?tabs=vanilla-javascript)

## <a name="see-also"></a>Lihat juga

- [Mulai menggunakan Azure CLI](get-started-with-azure-cli.md)
- [Daftar referensi perintah untuk Azure CLI](/cli/azure/reference-index)
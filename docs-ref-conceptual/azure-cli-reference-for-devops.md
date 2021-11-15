---
title: Azure CLI references for Azure DevOps | Microsoft Docs
description: Cari perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure DevOps.  Ikuti tautan ke artikel populer untuk mempelajari cara menggunakan Azure CLI untuk Azure DevOps.
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli references, azure devops
ms.openlocfilehash: bffb993971c565dde95c50fa1e393513329923c9
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439103"
---
# <a name="azure-cli-reference-commands-for-azure-devops"></a>Azure CLI reference commands for Azure DevOps

Azure Command-Line Interface[(CLI)](./what-is-azure-cli.md)adalah seperangkat perintah yang digunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di banyak layanan Azure dan memberi Anda kemampuan untuk mengelola Azure DevOps dari baris perintah.  

Perintah Azure CLI untuk [Azure DevOps](/azure/devops) memungkinkan Anda merampingkan tugas melewati alur kerja antarmuka pengguna.  Mereka terkait dengan grup referensi Azure CLI berikut. Kecuali untuk Azure Functions, penggunaan masing-masing grup referensi ini memerlukan ekstensi [azure-devops:](https://github.com/Azure/azure-devops-cli-extension)

- [Azure Artifacts](#azure-artifact-references)
- [Azure Boards](#azure-board-references) 
- [Organisasi Azure DevOps](#azure-devops-organization-references) 
- [Azure Functions (DevOps integration)](#azure-function-devops-integration-references) 
- [Azure Pipelines](#azure-pipeline-references) 
- [Azure Repos](#azure-repo-references) 

> [!NOTE]
> Anda diminta untuk menginstal referensi ekstensi pada penggunaan pertama. Atau, Anda dapat menggunakan perintah [tambahkan ekstensi az](/cli/azure/extension#az_extension_add) untuk menginstal ekstensi dengan nama secara manual.

## <a name="azure-artifact-references"></a>Azure Artifact references

[Azure Artifacts](/cli/azure/artifacts) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az artefak universal](/cli/azure/artifacts/universal) | Mengelola Paket Universal Artefak Azure. | [Menerbitkan dan mengunduh Paket Universal](/azure/devops/artifacts/quickstarts/universal-packages) |

## <a name="azure-board-references"></a>Azure Board references

[Azure Boards](/cli/azure/boards) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az boards](/cli/azure/boards) | Kelola Azure Boards. | [Apa itu Azure Boards?](/azure/devops/boards/get-started/what-is-azure-boards) |
| [az boards area project](/cli/azure/boards/area/project) | Mengelola area untuk sebuah proyek. | [Menentukan jalur area dan menetapkan ke tim](/azure/devops/organizations/settings/set-area-paths?tabs=azure-devops-cli) |
| [az board area team](/cli/azure/boards/area/team) | Mengelola area untuk tim. | [Menentukan jalur area dan menetapkan ke tim](/azure/devops/organizations/settings/set-area-paths?tabs=azure-devops-cli) |
| [az boards iteration project](/cli/azure/boards/iteration/project) | Mengelola iterasi untuk sebuah proyek. | [Menentukan jalur iterasi (sprint) dan mengonfigurasi iterasi tim](/azure/devops/organizations/settings/set-iteration-paths-sprints?tabs=azure-devops-cli) |
| [az boards iteration team](/cli/azure/boards/iteration/team) | Mengelola iterasi untuk sebuah tim. | [Menentukan jalur iterasi (sprint) dan mengonfigurasi iterasi tim](/azure/devops/organizations/settings/set-iteration-paths-sprints?tabs=azure-devops-cli) |
| [az boards work-item](/cli/azure/boards/work-item) | Mengelola item kerja. | [Menampilkan dan menambahkan item kerja](/azure/devops/boards/work-items/view-add-work-items?tabs=azure-devops-cli) |
| [az boards work-item relation](/cli/azure/boards/work-item/relation) | Mengelola hubungan item kerja. | [Menghubungkan, keterlacakan, dan mengelola dependensi](/azure/devops/boards/queries/link-work-items-support-traceability) |

## <a name="azure-devops-organization-references"></a>Referensi Organisasi Azure DevOps

[Azure DevOps](/cli/azure/devops) memiliki referensi berikut:

### <a name="security-references"></a>Referensi keamanan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az devops security group](/cli/azure/devops/security) | Mengelola grup keamanan. | [Memulai dengan mengizinkan, mengakses, dan grup keamanan](/azure/devops/organizations/security/about-permissions) |
| [az devops keanggotaan kelompok keamanan](/cli/azure/devops/security/group/membership) | Mengelola keanggotaan untuk grup keamanan. | [Menambahkan pengguna dan mengelola akses di Azure DevOps](/azure/devops/organizations/accounts/add-organization-users?tabs=azure-devops-cli) |
| [az devops izin keamanan](/cli/azure/devops/security/permission) | Mengelola izin keamanan. | [Memulai dengan mengizinkan, mengakses, dan grup keamanan](/azure/devops/organizations/security/about-permissions) |
| [az devops security permission namespace](/cli/azure/devops/security/permission/namespace) | Mengelola ruang nama keamanan. | [Ruang nama keamanan dan referensi izin](/azure/devops/organizations/security/namespace-reference) |

### <a name="service-endpoint-references"></a>Referensi titik akhir layanan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az devops service-endpoint](/cli/azure/devops/service-endpoint) | Mengelola titik akhir dan koneksi layanan. | [Membuat titik akhir layanan](/azure/devops/extend/develop/service-endpoints) |
| [az devops service-endpoint azurerm](/cli/azure/devops/service-endpoint/azurerm) | Kelola titik akhir dan koneksi layanan Azure Resource Manager. | [Koneksi layanan](/azure/devops/pipelines/library/service-endpoints) |
| [az devops service-endpoint github](/cli/azure/devops/service-endpoint/github) | Mengelola GitHub titik akhir dan koneksi layanan. | [Koneksi layanan](/azure/devops/pipelines/library/service-endpoints) |

### <a name="additional-devops-organization-references"></a>Referensi organisasi DevOps tambahan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az devops](/cli/azure/devops) | Mengelola Azure DevOps. | [Apa itu Azure DevOps?](/azure/devops/user-guide/what-is-azure-devops) |
| [az devops admin banner](/cli/azure/devops/admin/banner) | Mengelola operasi spanduk administrasi. | [Menambahkan dan mengelola spanduk informasi](/azure/devops/organizations/settings/manage-banners) |
| [az devops extension](/cli/azure/devops/extension) | Mengelola ekstensi. | [Menghapus atau menonaktifkan ekstensi](/azure/devops/marketplace/uninstall-disable-extensions?tabs=azure-devops-cli) |
| [az devops project](/cli/azure/devops/project) | Mengelola proyek tim. | [Membuat proyek di Azure DevOps](/azure/devops/organizations/projects/create-project?tabs=azure-devops-cli) |
| [az devops team](/cli/azure/devops/team) | Kelola tim. | [Menambahkan tim](/azure/devops/organizations/settings/add-teams?tabs=azure-devops-cli) |
| [az devops user](/cli/azure/devops/user) | Mengelola pengguna. | [Menambahkan pengguna dan mengelola akses di Azure DevOps](/azure/devops/organizations/accounts/add-organization-users?tabs=azure-devops-cli) |
| [az devops wiki](/cli/azure/devops/wiki) | Mengelola wiki. | [Mengelola wiki dengan CLI](/azure/devops/project/wiki/manage-wikis) |
| [az devops wiki page](/cli/azure/devops/wiki/page) | Mengelola halaman wiki. | [Menambahkan dan mengedit halaman wiki](/azure/devops/project/wiki/add-edit-wiki?tabs=azure-devops-cli) |

## <a name="azure-function-devops-integration-references"></a>Azure Function (DevOps integration) references

[Azure Functions (DevOps integration)](/cli/azure/functionapp/devops-pipeline) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az functionapp devops-pipeline](/cli/azure/functionapp/devops-pipeline) | Kelola integrasi Azure Function dengan Azure DevOps. | [Pengiriman berkelanjutan dengan menggunakan Azure DevOps](/azure/azure-functions/functions-how-to-azure-devops) |

## <a name="azure-pipeline-references"></a>Azure Pipeline references

[Azure Pipelines](/cli/azure/pipelines) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az pipelines](/cli/azure/pipelines) | Kelola Azure Pipelines. | [Membuat alur pertama Anda](/azure/devops/pipelines/create-first-pipeline?tabs=azure-cli) |
| [az pipelines agent](/cli/azure/pipelines/agent) | Mengelola agen. | [Azure Pipelines agents](/azure/devops/pipelines/agents/agents?tabs=azure-devops-cli) |
| [az pipelines build](/cli/azure/pipelines/build) | Mengelola build. | [Membuat alur pertama Anda](/azure/devops/pipelines/create-first-pipeline?tabs=azure-devops-cli) |
| [az pipelines build definition](/cli/azure/pipelines/build/definition) | Mengelola definisi build. | [Membuat alur pertama Anda](/azure/devops/pipelines/create-first-pipeline?tabs=azure-devops-cli) |
| [az pipelines build tag](/cli/azure/pipelines/build/tag) | Mengelola tag build. | [Menggunakan variabel yang telah ditentukan](/azure/devops/pipelines/build/variables) |
| [az pipelines folder](/cli/azure/pipelines/folder) | Mengelola folder untuk mengatur pipa. | [Mengkustomisasi alur Anda](/azure/devops/pipelines/customize-pipeline) |
| [az pipelines pool](/cli/azure/pipelines/pool) | Kelola kolam agen. | [Kolam agen](/azure/devops/pipelines/agents/pools-queues?tabs=yaml%2Cazure-devops-cli) |
| [az pipelines queue](/cli/azure/pipelines/queue) | Mengelola antrian agen. | [Kolam agen](/azure/devops/pipelines/agents/pools-queues?tabs=yaml%2Cazure-devops-cli) |
| [az pipelines release](/cli/azure/pipelines/release) | Mengelola rilis. | [Rilis di Azure Pipelines](/azure/devops/pipelines/release/releases) |
| [az pipelines release definition](/cli/azure/pipelines/release/definition) | Mengelola definisi rilis. | [Rilis di Azure Pipelines](/azure/devops/pipelines/release/releases) |
| [az pipelines run](/cli/azure/pipelines/runs) | Mengelola pipa berjalan. | [Urutan pipeline run](/azure/devops/pipelines/process/runs) |
| [az pipa menjalankan artefak](/cli/azure/pipelines/runs/artifact) | Mengelola pipa menjalankan artefak. | [Menerbitkan dan mengunduh artefak di Azure Pipelines](/azure/devops/pipelines/artifacts/pipeline-artifacts?tabs=azure-cli) |
| [az pipelines run tag](/cli/azure/pipelines/runs/tag) | Mengelola tag pipeline run. | [Menambahkan tag ke pipeline run](/azure/devops/pipelines/process/runs#add-tag-to-pipeline-run) |
| [az pipelines variable](/cli/azure/pipelines/variable) | Mengelola variabel. | [Tentukan variabel](/azure/devops/pipelines/process/variables?tabs=azure-devops-cli) |
| [az pipelines variable-group](/cli/azure/pipelines/variable-group) | Mengelola grup variabel. | [Menambahkan dan menggunakan grup variabel](/azure/devops/pipelines/library/variable-groups?tabs=azure-devops-cli) |
| [az pipelines variable-group variable](/cli/azure/pipelines/variable-group/variable) | Mengelola variabel dalam kelompok variabel. | [Mengelola variabel dalam grup variabel](/azure/devops/pipelines/library/variable-groups?tabs=azure-devops-cli#manage-variables-in-a-variable-group) |

## <a name="azure-repo-references"></a>Azure Repo references

[Azure Repos](/cli/azure/repos) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az repos](/cli/azure/repos) | Kelola Azure Repos. | [Memulai dengan Git dari baris perintah](/azure/devops/repos/git/share-your-code-in-git-cmdline) |
| [az repos import](/cli/azure/repos/import) | Kelola impor repositori Git. | [Mengimpor repo Git](/azure/devops/repos/git/import-git-repository) |
| [az repos policy](/cli/azure/repos/policy) | Mengelola kebijakan cabang. | [Pengaturan dan kebijakan repositori Git](/azure/devops/repos/git/repository-settings?tabs=azure-devops-cli) |
| [az repos policy approver-count](/cli/azure/repos/policy/approver-count) | Mengelola kebijakan penghitungan persetujuan. | [Kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos policy build](/cli/azure/repos/policy/build) | Mengelola kebijakan membangun. | [Membangun validasi](/azure/devops/repos/git/branch-policies#build-validation) |
| [az repos policy case-enforcement](/cli/azure/repos/policy/case-enforcement) | Mengelola kebijakan penegakan kasus. | [Pengaturan dan kebijakan repositori Git](/azure/devops/repos/git/repository-settings?tabs=azure-devops-cli) |
| [az repos policy comment-required](/cli/azure/repos/policy/comment-required) | Mengelola kebijakan yang diperlukan komentar. | [Membuat, melihat, dan mengelola permintaan tarik](/azure/devops/repos/git/pull-requests) |
| [az repos policy file-size](/cli/azure/repos/policy/file-size) | Mengelola kebijakan ukuran file. | [Pengaturan dan kebijakan repositori Git](/azure/devops/repos/git/repository-settings?tabs=azure-devops-cli) |
| [az repos policy merge-strategy](/cli/azure/repos/policy/merge-strategy) | Mengelola kebijakan strategi penggabungan. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos policy required-reviewer](/cli/azure/repos/policy/required-reviewer) | Mengelola kebijakan reviewer yang diperlukan. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos policy work-item-linking](/cli/azure/repos/policy/work-item-linking) | Mengelola kebijakan penautan item kerja. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos pr](/cli/azure/repos/pr) | Kelola permintaan tarik. | [Membuat, melihat, dan mengelola permintaan tarik](/azure/devops/repos/git/pull-requests) |
| [az repos pr policy](/cli/azure/repos/pr/policy) | Kelola kebijakan permintaan tarik. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos pr reviewer](/cli/azure/repos/pr/reviewer) | Kelola peninjau permintaan tarik. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos pr work-item](/cli/azure/repos/pr/work-item) | Mengelola item kerja yang terkait dengan permintaan tarik. | [Membuat, melihat, dan mengelola permintaan tarik](/azure/devops/repos/git/pull-requests) |
| [az repos ref](/cli/azure/repos/ref) | Kelola referensi Git. | [Mengelola cabang](/azure/devops/repos/git/manage-your-branches) |

## <a name="see-also"></a>Lihat juga

- [Mulai dengan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari tentang instalasi dan masuk.

- Temukan [referensi](/cli/azure/reference-index) tambahan dan ekstensi yang [tersedia](./azure-cli-extensions-list.md) dalam dokumentasi Azure CLI.

- Pelajari selengkapnya tentang referensi ekstensi di [Gunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

---
title: Referensi Azure CLI untuk Azure DevOps | Microsoft Docs
description: Temukan perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure DevOps.  Ikuti link ke artikel populer untuk mempelajari cara menggunakan Azure CLI for Azure DevOps.
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: robb
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure cli, azure devops
ms.openlocfilehash: bffb993971c565dde95c50fa1e393513329923c9
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439103"
---
# <a name="azure-cli-reference-commands-for-azure-devops"></a>Perintah referensi Azure CLI untuk Azure DevOps

Azure Command-Line Interface ([CLI](./what-is-azure-cli.md)) adalah sekumpulan perintah yang digunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di banyak layanan Azure dan memberi Anda kemampuan untuk mengelola Azure DevOps dari baris perintah.  

Perintah Azure CLI untuk [Azure DevOps](/azure/devops) memungkinkan Anda menyederhanakan tugas yang melewati alur kerja antarmuka pengguna.  Perintah tersebut terkait dengan grup referensi Azure CLI berikut. Kecuali untuk Azure Functions, penggunaan masing-masing grup referensi ini memerlukan ekstensi [azure-devops](https://github.com/Azure/azure-devops-cli-extension):

- [Azure Artifacts](#azure-artifact-references)
- [Azure Boards](#azure-board-references) 
- [Azure DevOps Organizations](#azure-devops-organization-references) 
- [Azure Functions (DevOps integration)](#azure-function-devops-integration-references) 
- [Azure Pipelines](#azure-pipeline-references) 
- [Azure Repos](#azure-repo-references) 

> [!NOTE]
> Anda diminta menginstal referensi ekstensi saat digunakan pertama kali. Sebagai alternatif, Anda dapat menggunakan perintah [az extension add](/cli/azure/extension#az_extension_add) untuk menginstal ekstensi secara manual berdasarkan nama.

## <a name="azure-artifact-references"></a>Referensi Azure Artifact

[Azure Artifacts](/cli/azure/artifacts) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az artifacts universal](/cli/azure/artifacts/universal) | Mengelola Paket Universal Azure Artifacts. | [Menerbitkan dan mengunduh Paket Universal](/azure/devops/artifacts/quickstarts/universal-packages) |

## <a name="azure-board-references"></a>Referensi Azure Board

[Azure Boards](/cli/azure/boards) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az boards](/cli/azure/boards) | Mengelola Azure Boards. | [Apa yang dimaksud dengan Azure Boards?](/azure/devops/boards/get-started/what-is-azure-boards) |
| [az boards area project](/cli/azure/boards/area/project) | Mengelola area untuk proyek. | [Menentukan jalur area dan menetapkan ke tim](/azure/devops/organizations/settings/set-area-paths?tabs=azure-devops-cli) |
| [az boards area team](/cli/azure/boards/area/team) | Mengelola area untuk tim. | [Menentukan jalur area dan menetapkan ke tim](/azure/devops/organizations/settings/set-area-paths?tabs=azure-devops-cli) |
| [az boards iteration project](/cli/azure/boards/iteration/project) | Mengelola iterasi untuk proyek. | [Menentukan jalur iterasi (sprint) dan mengonfigurasi iterasi tim](/azure/devops/organizations/settings/set-iteration-paths-sprints?tabs=azure-devops-cli) |
| [az boards iteration team](/cli/azure/boards/iteration/team) | Mengelola iterasi untuk tim. | [Menentukan jalur iterasi (sprint) dan mengonfigurasi iterasi tim](/azure/devops/organizations/settings/set-iteration-paths-sprints?tabs=azure-devops-cli) |
| [az boards work-item](/cli/azure/boards/work-item) | Mengelola item pekerjaan. | [Melihat dan menambahkan item pekerjaan](/azure/devops/boards/work-items/view-add-work-items?tabs=azure-devops-cli) |
| [az boards work-item relation](/cli/azure/boards/work-item/relation) | Mengelola hubungan item pekerjaan. | [Penautan, keterlacakan, dan manajemen dependensi](/azure/devops/boards/queries/link-work-items-support-traceability) |

## <a name="azure-devops-organization-references"></a>Referensi Organisasi Azure DevOps

[Azure DevOps](/cli/azure/devops) memiliki referensi berikut:

### <a name="security-references"></a>Referensi keamanan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az devops security group](/cli/azure/devops/security) | Mengelola grup keamanan. | [Memulai izin, akses, dan grup keamanan](/azure/devops/organizations/security/about-permissions) |
| [az devops security group membership](/cli/azure/devops/security/group/membership) | Mengelola keanggotaan untuk grup keamanan. | [Menambahkan pengguna dan mengelola akses di Azure DevOps](/azure/devops/organizations/accounts/add-organization-users?tabs=azure-devops-cli) |
| [az devops security permission](/cli/azure/devops/security/permission) | Mengelola izin keamanan. | [Memulai izin, akses, dan grup keamanan](/azure/devops/organizations/security/about-permissions) |
| [az devops security permission namespace](/cli/azure/devops/security/permission/namespace) | Mengelola namespace layanan keamanan. | [Referensi izin dan namespace layanan keamanan](/azure/devops/organizations/security/namespace-reference) |

### <a name="service-endpoint-references"></a>Referensi titik akhir layanan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az devops service-endpoint](/cli/azure/devops/service-endpoint) | Mengelola titik akhir dan koneksi layanan. | [Membuat titik akhir layanan](/azure/devops/extend/develop/service-endpoints) |
| [az devops service-endpoint azurerm](/cli/azure/devops/service-endpoint/azurerm) | Mengelola titik akhir dan koneksi layanan Azure Resource Manager. | [Koneksi layanan](/azure/devops/pipelines/library/service-endpoints) |
| [az devops service-endpoint github](/cli/azure/devops/service-endpoint/github) | Mengelola titik akhir dan koneksi layanan GitHub. | [Koneksi layanan](/azure/devops/pipelines/library/service-endpoints) |

### <a name="additional-devops-organization-references"></a>Referensi organisasi DevOps tambahan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az devops](/cli/azure/devops) | Mengelola Azure DevOps. | [Apa itu Azure DevOps?](/azure/devops/user-guide/what-is-azure-devops) |
| [az devops admin banner](/cli/azure/devops/admin/banner) | Mengelola operasi banner administrasi. | [Menambahkan dan mengelola banner informasi](/azure/devops/organizations/settings/manage-banners) |
| [az devops extension](/cli/azure/devops/extension) | Mengelola ekstensi. | [Menghapus instalan atau menonaktifkan ekstensi](/azure/devops/marketplace/uninstall-disable-extensions?tabs=azure-devops-cli) |
| [az devops project](/cli/azure/devops/project) | Mengelola proyek tim. | [Membuat proyek di Azure DevOps](/azure/devops/organizations/projects/create-project?tabs=azure-devops-cli) |
| [az devops team](/cli/azure/devops/team) | Mengelola tim. | [Menambahkan tim](/azure/devops/organizations/settings/add-teams?tabs=azure-devops-cli) |
| [az devops user](/cli/azure/devops/user) | Mengelola pengguna. | [Menambahkan pengguna dan mengelola akses di Azure DevOps](/azure/devops/organizations/accounts/add-organization-users?tabs=azure-devops-cli) |
| [az devops wiki](/cli/azure/devops/wiki) | Mengelola wiki. | [Mengelola wiki dengan CLI](/azure/devops/project/wiki/manage-wikis) |
| [az devops wiki page](/cli/azure/devops/wiki/page) | Mengelola halaman wiki. | [Menambahkan dan mengedit halaman wiki](/azure/devops/project/wiki/add-edit-wiki?tabs=azure-devops-cli) |

## <a name="azure-function-devops-integration-references"></a>Referensi Azure Function (integrasi DevOps)

[Azure Functions (integrasi DevOps)](/cli/azure/functionapp/devops-pipeline) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az functionapp devops-pipeline](/cli/azure/functionapp/devops-pipeline) | Mengelola integrasi Azure Function dengan Azure DevOps. | [Pengiriman berkelanjutan dengan menggunakan Azure DevOps](/azure/azure-functions/functions-how-to-azure-devops) |

## <a name="azure-pipeline-references"></a>Referensi Azure Pipeline

[Azure Pipelines](/cli/azure/pipelines) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az pipelines](/cli/azure/pipelines) | Mengelola Azure Pipelines. | [Membuat alur pertama Anda](/azure/devops/pipelines/create-first-pipeline?tabs=azure-cli) |
| [az pipelines agent](/cli/azure/pipelines/agent) | Mengelola agen. | [Agen Azure Pipelines](/azure/devops/pipelines/agents/agents?tabs=azure-devops-cli) |
| [az pipelines build](/cli/azure/pipelines/build) | Mengelola build. | [Membuat alur pertama Anda](/azure/devops/pipelines/create-first-pipeline?tabs=azure-devops-cli) |
| [az pipelines build definition](/cli/azure/pipelines/build/definition) | Mengelola definisi build. | [Membuat alur pertama Anda](/azure/devops/pipelines/create-first-pipeline?tabs=azure-devops-cli) |
| [az pipelines build tag](/cli/azure/pipelines/build/tag) | Mengelola tag build. | [Menggunakan variabel yang telah ditentukan sebelumnya](/azure/devops/pipelines/build/variables) |
| [az pipelines folder](/cli/azure/pipelines/folder) | Mengelola folder untuk mengatur alur. | [Mengkustomisasi alur Anda](/azure/devops/pipelines/customize-pipeline) |
| [az pipelines pool](/cli/azure/pipelines/pool) | Mengelola kumpulan agen. | [Kumpulan agen](/azure/devops/pipelines/agents/pools-queues?tabs=yaml%2Cazure-devops-cli) |
| [az pipelines queue](/cli/azure/pipelines/queue) | Mengelola antrean agen. | [Kumpulan agen](/azure/devops/pipelines/agents/pools-queues?tabs=yaml%2Cazure-devops-cli) |
| [az pipelines release](/cli/azure/pipelines/release) | Mengelola rilis. | [Rilis di Azure Pipelines](/azure/devops/pipelines/release/releases) |
| [az pipelines release definition](/cli/azure/pipelines/release/definition) | Mengelola definisi rilis. | [Rilis di Azure Pipelines](/azure/devops/pipelines/release/releases) |
| [az pipelines runs](/cli/azure/pipelines/runs) | Mengelola eksekusi alur. | [Urutan eksekusi alur](/azure/devops/pipelines/process/runs) |
| [az pipelines runs artifact](/cli/azure/pipelines/runs/artifact) | Mengelola artefak eksekusi alur. | [Menerbitkan dan mengunduh artefak di Azure Pipelines](/azure/devops/pipelines/artifacts/pipeline-artifacts?tabs=azure-cli) |
| [az pipelines runs tag](/cli/azure/pipelines/runs/tag) | Mengelola tag eksekusi alur. | [Menambahkan tag ke proses alur](/azure/devops/pipelines/process/runs#add-tag-to-pipeline-run) |
| [az pipelines variable](/cli/azure/pipelines/variable) | Mengelola variabel. | [Tentukan variabel](/azure/devops/pipelines/process/variables?tabs=azure-devops-cli) |
| [az pipelines variable-group](/cli/azure/pipelines/variable-group) | Mengelola grup variabel. | [Menambahkan dan menggunakan grup variabel](/azure/devops/pipelines/library/variable-groups?tabs=azure-devops-cli) |
| [az pipelines variable-group variable](/cli/azure/pipelines/variable-group/variable) | Mengelola variabel dalam grup variabel. | [Mengelola variabel dalam grup variabel](/azure/devops/pipelines/library/variable-groups?tabs=azure-devops-cli#manage-variables-in-a-variable-group) |

## <a name="azure-repo-references"></a>Referensi Azure Repo

[Azure Repos](/cli/azure/repos) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az repos](/cli/azure/repos) | Mengelola Azure Repos. | [Memulai Git dari baris perintah](/azure/devops/repos/git/share-your-code-in-git-cmdline) |
| [az repos import](/cli/azure/repos/import) | Mengelola impor repositori Git. | [Mengimpor repositori Git](/azure/devops/repos/git/import-git-repository) |
| [az repos policy](/cli/azure/repos/policy) | Mengelola kebijakan cabang. | [Setelan dan kebijakan repositori Git](/azure/devops/repos/git/repository-settings?tabs=azure-devops-cli) |
| [az repos policy approver-count](/cli/azure/repos/policy/approver-count) | Mengelola kebijakan jumlah pemberi izin. | [Kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos policy build](/cli/azure/repos/policy/build) | Mengelola kebijakan build. | [Membuat validasi](/azure/devops/repos/git/branch-policies#build-validation) |
| [az repos policy case-enforcement](/cli/azure/repos/policy/case-enforcement) | Mengelola kebijakan penegakan kasus. | [Setelan dan kebijakan repositori Git](/azure/devops/repos/git/repository-settings?tabs=azure-devops-cli) |
| [az repos policy comment-required](/cli/azure/repos/policy/comment-required) | Mengelola kebijakan yang diperlukan komentar. | [Membuat, melihat, dan mengelola permintaan pull](/azure/devops/repos/git/pull-requests) |
| [az repos policy file-size](/cli/azure/repos/policy/file-size) | Mengelola kebijakan ukuran file. | [Setelan dan kebijakan repositori Git](/azure/devops/repos/git/repository-settings?tabs=azure-devops-cli) |
| [az repos policy merge-strategy](/cli/azure/repos/policy/merge-strategy) | Mengelola kebijakan strategi penggabungan. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos policy required-reviewer](/cli/azure/repos/policy/required-reviewer) | Mengelola kebijakan peninjau yang diperlukan. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos policy work-item-linking](/cli/azure/repos/policy/work-item-linking) | Mengelola kebijakan penautan item pekerjaan. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos pr](/cli/azure/repos/pr) | Mengelola permintaan pull. | [Membuat, melihat, dan mengelola permintaan pull](/azure/devops/repos/git/pull-requests) |
| [az repos pr policy](/cli/azure/repos/pr/policy) | Mengelola kebijakan permintaan pull. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos pr reviewer](/cli/azure/repos/pr/reviewer) | Mengelola peninjau permintaan pull. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos pr work-item](/cli/azure/repos/pr/work-item) | Mengelola item pekerjaan yang terkait dengan permintaan pull. | [Membuat, melihat, dan mengelola permintaan pull](/azure/devops/repos/git/pull-requests) |
| [az repos ref](/cli/azure/repos/ref) | Mengelola referensi Git. | [Mengelola cabang](/azure/devops/repos/git/manage-your-branches) |

## <a name="see-also"></a>Lihat juga

- [Mulai menggunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari tentang penginstalan dan proses masuk.

- Temukan [referensi](/cli/azure/reference-index) dan [ekstensi yang tersedia](./azure-cli-extensions-list.md) tambahan di dokumentasi Azure CLI.

- Pelajari referensi ekstensi lebih lanjut di [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

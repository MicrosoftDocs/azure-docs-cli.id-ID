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
ms.openlocfilehash: 6b17c09f35f879257854a180979cc5a5421e4b80
ms.sourcegitcommit: cbb162f5b74c5250338109317f06a152809c4b4c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/06/2022
ms.locfileid: "141400649"
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

[Azure Artifacts](../latest/docs-ref-autogen/artifacts.yml) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az artifacts universal](../latest/docs-ref-autogen/artifacts/universal.yml) | Mengelola Paket Universal Azure Artifacts. | [Menerbitkan dan mengunduh Paket Universal](/azure/devops/artifacts/quickstarts/universal-packages) |

## <a name="azure-board-references"></a>Referensi Azure Board

[Azure Boards](../latest/docs-ref-autogen/boards.yml) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az boards](../latest/docs-ref-autogen/boards.yml) | Mengelola Azure Boards. | [Apa yang dimaksud dengan Azure Boards?](/azure/devops/boards/get-started/what-is-azure-boards) |
| [az boards area project](../latest/docs-ref-autogen/boards/area/project.yml) | Mengelola area untuk proyek. | [Menentukan jalur area dan menetapkan ke tim](/azure/devops/organizations/settings/set-area-paths?tabs=azure-devops-cli) |
| [az boards area team](../latest/docs-ref-autogen/boards/area/team.yml) | Mengelola area untuk tim. | [Menentukan jalur area dan menetapkan ke tim](/azure/devops/organizations/settings/set-area-paths?tabs=azure-devops-cli) |
| [az boards iteration project](../latest/docs-ref-autogen/boards/iteration/project.yml) | Mengelola iterasi untuk proyek. | [Menentukan jalur iterasi (sprint) dan mengonfigurasi iterasi tim](/azure/devops/organizations/settings/set-iteration-paths-sprints?tabs=azure-devops-cli) |
| [az boards iteration team](../latest/docs-ref-autogen/boards/iteration/team.yml) | Mengelola iterasi untuk tim. | [Menentukan jalur iterasi (sprint) dan mengonfigurasi iterasi tim](/azure/devops/organizations/settings/set-iteration-paths-sprints?tabs=azure-devops-cli) |
| [az boards work-item](../latest/docs-ref-autogen/boards/work-item.yml) | Mengelola item pekerjaan. | [Melihat dan menambahkan item pekerjaan](/azure/devops/boards/work-items/view-add-work-items?tabs=azure-devops-cli) |
| [az boards work-item relation](../latest/docs-ref-autogen/boards/work-item/relation.yml) | Mengelola hubungan item pekerjaan. | [Penautan, keterlacakan, dan manajemen dependensi](/azure/devops/boards/queries/link-work-items-support-traceability) |

## <a name="azure-devops-organization-references"></a>Referensi Organisasi Azure DevOps

[Azure DevOps](../latest/docs-ref-autogen/devops.yml) memiliki referensi berikut:

### <a name="security-references"></a>Referensi keamanan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az devops security group](../latest/docs-ref-autogen/devops/security.yml) | Mengelola grup keamanan. | [Memulai izin, akses, dan grup keamanan](/azure/devops/organizations/security/about-permissions) |
| [az devops security group membership](../latest/docs-ref-autogen/devops/security/group/membership.yml) | Mengelola keanggotaan untuk grup keamanan. | [Menambahkan pengguna dan mengelola akses di Azure DevOps](/azure/devops/organizations/accounts/add-organization-users?tabs=azure-devops-cli) |
| [az devops security permission](../latest/docs-ref-autogen/devops/security/permission.yml) | Mengelola izin keamanan. | [Memulai izin, akses, dan grup keamanan](/azure/devops/organizations/security/about-permissions) |
| [az devops security permission namespace](../latest/docs-ref-autogen/devops/security/permission/namespace.yml) | Mengelola namespace layanan keamanan. | [Referensi izin dan namespace layanan keamanan](/azure/devops/organizations/security/namespace-reference) |

### <a name="service-endpoint-references"></a>Referensi titik akhir layanan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az devops service-endpoint](../latest/docs-ref-autogen/devops/service-endpoint.yml) | Mengelola titik akhir dan koneksi layanan. | [Membuat titik akhir layanan](/azure/devops/extend/develop/service-endpoints) |
| [az devops service-endpoint azurerm](../latest/docs-ref-autogen/devops/service-endpoint/azurerm.yml) | Mengelola titik akhir dan koneksi layanan Azure Resource Manager. | [Koneksi layanan](/azure/devops/pipelines/library/service-endpoints) |
| [az devops service-endpoint github](../latest/docs-ref-autogen/devops/service-endpoint/github.yml) | Mengelola titik akhir dan koneksi layanan GitHub. | [Koneksi layanan](/azure/devops/pipelines/library/service-endpoints) |

### <a name="additional-devops-organization-references"></a>Referensi organisasi DevOps tambahan

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az devops](../latest/docs-ref-autogen/devops.yml) | Mengelola Azure DevOps. | [Apa itu Azure DevOps?](/azure/devops/user-guide/what-is-azure-devops) |
| [az devops admin banner](../latest/docs-ref-autogen/devops/admin/banner.yml) | Mengelola operasi banner administrasi. | [Menambahkan dan mengelola banner informasi](/azure/devops/organizations/settings/manage-banners) |
| [az devops extension](../latest/docs-ref-autogen/devops/extension.yml) | Mengelola ekstensi. | [Menghapus instalan atau menonaktifkan ekstensi](/azure/devops/marketplace/uninstall-disable-extensions?tabs=azure-devops-cli) |
| [az devops project](../latest/docs-ref-autogen/devops/project.yml) | Mengelola proyek tim. | [Membuat proyek di Azure DevOps](/azure/devops/organizations/projects/create-project?tabs=azure-devops-cli) |
| [az devops team](../latest/docs-ref-autogen/devops/team.yml) | Mengelola tim. | [Menambahkan tim](/azure/devops/organizations/settings/add-teams?tabs=azure-devops-cli) |
| [az devops user](../latest/docs-ref-autogen/devops/user.yml) | Mengelola pengguna. | [Menambahkan pengguna dan mengelola akses di Azure DevOps](/azure/devops/organizations/accounts/add-organization-users?tabs=azure-devops-cli) |
| [az devops wiki](../latest/docs-ref-autogen/devops/wiki.yml) | Mengelola wiki. | [Mengelola wiki dengan CLI](/azure/devops/project/wiki/manage-wikis) |
| [az devops wiki page](../latest/docs-ref-autogen/devops/wiki/page.yml) | Mengelola halaman wiki. | [Menambahkan dan mengedit halaman wiki](/azure/devops/project/wiki/add-edit-wiki?tabs=azure-devops-cli) |

## <a name="azure-function-devops-integration-references"></a>Referensi Azure Function (integrasi DevOps)

[Azure Functions (integrasi DevOps)](../latest/docs-ref-autogen/functionapp/devops-pipeline.yml) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az functionapp devops-pipeline](../latest/docs-ref-autogen/functionapp/devops-pipeline.yml) | Mengelola integrasi Azure Function dengan Azure DevOps. | [Pengiriman berkelanjutan dengan menggunakan Azure DevOps](/azure/azure-functions/functions-how-to-azure-devops) |

## <a name="azure-pipeline-references"></a>Referensi Azure Pipeline

[Azure Pipelines](../latest/docs-ref-autogen/pipelines.yml) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az pipelines](../latest/docs-ref-autogen/pipelines.yml) | Mengelola Azure Pipelines. | [Membuat alur pertama Anda](/azure/devops/pipelines/create-first-pipeline?tabs=azure-cli) |
| [az pipelines agent](../latest/docs-ref-autogen/pipelines/agent.yml) | Mengelola agen. | [Agen Azure Pipelines](/azure/devops/pipelines/agents/agents?tabs=azure-devops-cli) |
| [az pipelines build](../latest/docs-ref-autogen/pipelines/build.yml) | Mengelola build. | [Membuat alur pertama Anda](/azure/devops/pipelines/create-first-pipeline?tabs=azure-devops-cli) |
| [az pipelines build definition](../latest/docs-ref-autogen/pipelines/build/definition.yml) | Mengelola definisi build. | [Membuat alur pertama Anda](/azure/devops/pipelines/create-first-pipeline?tabs=azure-devops-cli) |
| [az pipelines build tag](../latest/docs-ref-autogen/pipelines/build/tag.yml) | Mengelola tag build. | [Menggunakan variabel yang telah ditentukan sebelumnya](/azure/devops/pipelines/build/variables) |
| [az pipelines folder](../latest/docs-ref-autogen/pipelines/folder.yml) | Mengelola folder untuk mengatur alur. | [Mengkustomisasi alur Anda](/azure/devops/pipelines/customize-pipeline) |
| [az pipelines pool](../latest/docs-ref-autogen/pipelines/pool.yml) | Mengelola kumpulan agen. | [Kumpulan agen](/azure/devops/pipelines/agents/pools-queues?tabs=yaml%2Cazure-devops-cli) |
| [az pipelines queue](../latest/docs-ref-autogen/pipelines/queue.yml) | Mengelola antrean agen. | [Kumpulan agen](/azure/devops/pipelines/agents/pools-queues?tabs=yaml%2Cazure-devops-cli) |
| [az pipelines release](../latest/docs-ref-autogen/pipelines/release.yml) | Mengelola rilis. | [Rilis di Azure Pipelines](/azure/devops/pipelines/release/releases) |
| [az pipelines release definition](../latest/docs-ref-autogen/pipelines/release/definition.yml) | Mengelola definisi rilis. | [Rilis di Azure Pipelines](/azure/devops/pipelines/release/releases) |
| [az pipelines runs](../latest/docs-ref-autogen/pipelines/runs.yml) | Mengelola eksekusi alur. | [Urutan eksekusi alur](/azure/devops/pipelines/process/runs) |
| [az pipelines runs artifact](../latest/docs-ref-autogen/pipelines/runs/artifact.yml) | Mengelola artefak eksekusi alur. | [Menerbitkan dan mengunduh artefak di Azure Pipelines](/azure/devops/pipelines/artifacts/pipeline-artifacts?tabs=azure-cli) |
| [az pipelines runs tag](../latest/docs-ref-autogen/pipelines/runs/tag.yml) | Mengelola tag eksekusi alur. | [Menambahkan tag ke proses alur](/azure/devops/pipelines/process/runs#add-tag-to-pipeline-run) |
| [az pipelines variable](../latest/docs-ref-autogen/pipelines/variable.yml) | Mengelola variabel. | [Tentukan variabel](/azure/devops/pipelines/process/variables?tabs=azure-devops-cli) |
| [az pipelines variable-group](../latest/docs-ref-autogen/pipelines/variable-group.yml) | Mengelola grup variabel. | [Menambahkan dan menggunakan grup variabel](/azure/devops/pipelines/library/variable-groups?tabs=azure-devops-cli) |
| [az pipelines variable-group variable](../latest/docs-ref-autogen/pipelines/variable-group/variable.yml) | Mengelola variabel dalam grup variabel. | [Mengelola variabel dalam grup variabel](/azure/devops/pipelines/library/variable-groups?tabs=azure-devops-cli#manage-variables-in-a-variable-group) |

## <a name="azure-repo-references"></a>Referensi Azure Repo

[Azure Repos](../latest/docs-ref-autogen/repos.yml) memiliki referensi berikut:

| Referensi | Deskripsi | Informasi selengkapnya |
|-|-|-|
| [az repos](../latest/docs-ref-autogen/repos.yml) | Mengelola Azure Repos. | [Memulai Git dari baris perintah](/azure/devops/repos/git/share-your-code-in-git-cmdline) |
| [az repos import](../latest/docs-ref-autogen/repos/import.yml) | Mengelola impor repositori Git. | [Mengimpor repositori Git](/azure/devops/repos/git/import-git-repository) |
| [az repos policy](../latest/docs-ref-autogen/repos/policy.yml) | Mengelola kebijakan cabang. | [Setelan dan kebijakan repositori Git](/azure/devops/repos/git/repository-settings?tabs=azure-devops-cli) |
| [az repos policy approver-count](../latest/docs-ref-autogen/repos/policy/approver-count.yml) | Mengelola kebijakan jumlah pemberi izin. | [Kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos policy build](../latest/docs-ref-autogen/repos/policy/build.yml) | Mengelola kebijakan build. | [Membuat validasi](/azure/devops/repos/git/branch-policies#build-validation) |
| [az repos policy case-enforcement](../latest/docs-ref-autogen/repos/policy/case-enforcement.yml) | Mengelola kebijakan penegakan kasus. | [Setelan dan kebijakan repositori Git](/azure/devops/repos/git/repository-settings?tabs=azure-devops-cli) |
| [az repos policy comment-required](../latest/docs-ref-autogen/repos/policy/comment-required.yml) | Mengelola kebijakan yang diperlukan komentar. | [Membuat, melihat, dan mengelola permintaan pull](/azure/devops/repos/git/pull-requests) |
| [az repos policy file-size](../latest/docs-ref-autogen/repos/policy/file-size.yml) | Mengelola kebijakan ukuran file. | [Setelan dan kebijakan repositori Git](/azure/devops/repos/git/repository-settings?tabs=azure-devops-cli) |
| [az repos policy merge-strategy](../latest/docs-ref-autogen/repos/policy/merge-strategy.yml) | Mengelola kebijakan strategi penggabungan. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos policy required-reviewer](../latest/docs-ref-autogen/repos/policy/required-reviewer.yml) | Mengelola kebijakan peninjau yang diperlukan. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos policy work-item-linking](../latest/docs-ref-autogen/repos/policy/work-item-linking.yml) | Mengelola kebijakan penautan item pekerjaan. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos pr](../latest/docs-ref-autogen/repos/pr.yml) | Mengelola permintaan pull. | [Membuat, melihat, dan mengelola permintaan pull](/azure/devops/repos/git/pull-requests) |
| [az repos pr policy](../latest/docs-ref-autogen/repos/pr/policy.yml) | Mengelola kebijakan permintaan pull. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos pr reviewer](../latest/docs-ref-autogen/repos/pr/reviewer.yml) | Mengelola peninjau permintaan pull. | [Meningkatkan kualitas kode dengan kebijakan cabang](/azure/devops/repos/git/branch-policies) |
| [az repos pr work-item](../latest/docs-ref-autogen/repos/pr/work-item.yml) | Mengelola item pekerjaan yang terkait dengan permintaan pull. | [Membuat, melihat, dan mengelola permintaan pull](/azure/devops/repos/git/pull-requests) |
| [az repos ref](../latest/docs-ref-autogen/repos/ref.yml) | Mengelola referensi Git. | [Mengelola cabang](/azure/devops/repos/git/manage-your-branches) |

## <a name="see-also"></a>Lihat juga

- [Mulai gunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari penginstalan dan aktivitas masuk.

- Temukan [referensi](../latest/docs-ref-autogen/reference-index.yml) tambahan dan [ekstensi yang tersedia](./azure-cli-extensions-list.md) di dokumentasi Azure CLI.

- Pelajari referensi ekstensi lebih lanjut di [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).
---
title: Azure CLI berbasis MSAL | Microsoft Docs
description: Pelajari Azure CLI berbasis MSAL.
author: jiasli
ms.author: jiasli
manager: yonzhan
ms.date: 10/28/2021
ms.topic: conceptual
ms.service: azure-cli
ms.tool: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: msal, msal-based azure cli
ms.openlocfilehash: daecbcf6a6359610b51696b4f12cab162dfff052
ms.sourcegitcommit: 6822e5d700742617eabda5904fe2ca217bae9d28
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/30/2022
ms.locfileid: "145939892"
---
# <a name="msal-based-azure-cli"></a>Azure CLI berbasis MSAL

Mulai dari versi 2.30.0, Azure CLI menggunakan [MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-python) sebagai pustaka autentikasi dasar. MSAL menggunakan alur autentikasi AAD v2.0 untuk menyediakan lebih banyak fungsionalitas dan meningkatkan keamanan untuk cache token.

> [!WARNING]
> BREAKING CHANGES disertakan di Azure CLI 2.30.0. Baca dokumen dengan cermat sebelum melakukan penginstalan.

## <a name="accesstokensjson-deprecation"></a>Penghentian `accessTokens.json`

Versi Azure CLI sebelumnya menyimpan token ADAL dan entri perwakilan layanan di `~/.azure/accessToken.json`. Azure CLI versi terbaru menggunakan MSAL dan tidak menghasilkan `accessTokens.json` lagi. Setiap alur kerja yang bergantung pada `accessTokens.json` tidak berfungsi lagi.

Cache token MSAL dan entri perwakilan layanan disimpan sebagai file terenkripsi di Windows, dan file teks biasa di Linux dan MacOS.

> [!IMPORTANT]
> Saat menggunakan Azure CLI dalam alur seperti Azure DevOps, pastikan semua tugas dan tahapan menggunakan Azure CLI dengan versi di atas v2.30.0 untuk Azure CLI berbasis MSAL. Azure CLI 2.30.0 tidak kompatibel mundur dengan versi sebelumnya dan menampilkan kesalahan saat bekerja dengan versi di bawah 2.30.0.

## <a name="alternatives-to-consider"></a>Alternatif yang perlu dipertimbangkan

Berikut beberapa alternatif yang dapat dipertimbangkan untuk stabilitas:

### <a name="calling-az-account-get-access-token"></a>Memanggil `az account get-access-token`

Anda dapat secara manual memanggil [`az account get-access-token`](/cli/azure/account#az_account_get_access_token) di terminal atau menggunakan sub-proses untuk memanggilnya dari bahasa pemrogram lain. Secara default, token akses yang ditampilkan diperuntukkan bagi Azure Resource Manager (ARM) dan langganan/penyewa default yang ditampilkan di [`az account show`](/cli/azure/account#az_account_show).

```azurecli
# get the active subscription
az account show --output table

# get access token for the active subscription
az account get-access-token

# get access token for a specific subscription
az account get-access-token --subscription "<subscription ID or name>"
```

### <a name="using-azureclicredential"></a>Menggunakan `AzureCliCredential`

`AzureCliCredential` adalah jenis info masuk di semua SDK bahasa yang ada. Sub-proses digunakan untuk memanggil `az account get-access-token` guna mendapatkan token akses untuk akun yang masuk saat ini.

## <a name="see-also"></a>Lihat juga

- MSAL
  - [Ringkasan Pustaka Autentikasi Microsoft (MSAL)](/azure/active-directory/develop/msal-overview)
  - [Memigrasikan aplikasi ke Microsoft Authentication Library (MSAL)](/azure/active-directory/develop/msal-migration)
- Python
  - [Kelas AzureCliCredential](/python/api/azure-identity/azure.identity.azureclicredential) di Python
- .NET
  - [Kelas AzureCliCredential ](/dotnet/api/azure.identity.azureclicredential) di .NET
- Java
  - [Kelas AzureCliCredential ](/java/api/com.azure.identity.azureclicredential) di Java

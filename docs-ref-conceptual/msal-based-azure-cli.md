---
title: '| Azure CLI berbasis MSAL Microsoft Docs'
description: Pelajari tentang Azure CLI yang berbasis di MSAL.
author: jiasli
ms.author: jiasli
manager: yonzhan
ms.date: 10/28/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: msal, msal-based azure cli
ms.openlocfilehash: cee69615861e1d5ddedaf6aeca40f9cf92b8fb75
ms.sourcegitcommit: d2227bc475235bf86193e9cae5e02f349a6342e2
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 11/02/2021
ms.locfileid: "132439111"
---
# <a name="msal-based-azure-cli"></a>MSAL-based Azure CLI

Mulai versi 2.30.0, Azure CLI menggunakan [MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-python) sebagai pustaka autentikasi yang mendasarinya. MSAL menggunakan aliran otentikasi AAD v2.0 untuk menyediakan lebih banyak fungsi dan meningkatkan keamanan untuk cache token.

> [!WARNING]
> BREAKING CHANGES diperkenalkan di Azure CLI 2.30.0. Hati-hati membaca dokumen sebelum instalasi.

## <a name="accesstokensjson-deprecation"></a>`accessTokens.json` depresiasi

Versi sebelumnya dari Azure CLI menyimpan token ADAL dan entri utama layanan ke `~/.azure/accessToken.json` . Versi terbaru Dari Azure CLI menggunakan MSAL dan tidak lagi menghasilkan `accessTokens.json` . Setiap alur kerja yang ada tergantung pada `accessTokens.json` tidak lagi berfungsi.

Cache token MSAL dan entri utama layanan disimpan sebagai file terenkripsi di Windows, dan file plaintext di Linux dan MacOS.

## <a name="alternatives-to-consider"></a>Alternatif untuk dipertimbangkan

Berikut adalah beberapa alternatif yang dapat Anda pertimbangkan:

### <a name="calling-az-account-get-access-token"></a>Memanggil `az account get-access-token`

Anda dapat secara manual memanggil [`az account get-access-token`](/cli/azure/account#az_account_get_access_token) terminal atau menggunakan subproses untuk menyebutnya dari bahasa pemrograman lain. Secara default, token akses yang dikembalikan adalah untuk Azure Resource Manager (ARM) dan langganan/ penyewa default yang ditampilkan di [`az account show`](/cli/azure/account#az_account_show) .

```azurecli
# get the active subscription
az account show --output table

# get access token for the active subscription
az account get-access-token

# get access token for a specific subscription
az account get-access-token --subscription "<subscription ID or name>"
```

### <a name="using-azureclicredential"></a>Menggunakan `AzureCliCredential`

`AzureCliCredential` adalah tipe kredensial di semua SDK bahasa yang ada. Ini menggunakan subproses untuk menelepon `az account get-access-token` untuk mendapatkan token akses untuk akun login saat ini.

## <a name="see-also"></a>Lihat juga

* MSAL
  * [Ringkasan Pustaka Autentikasi Microsoft (MSAL)](/azure/active-directory/develop/msal-overview)
  * [Memigrasikan aplikasi ke Microsoft Authentication Library (MSAL)](/azure/active-directory/develop/msal-migration)
* Python
  * [AzureCliCredential Class](/python/api/azure-identity/azure.identity.azureclicredential) in Python
* .NET
  * [AzureCliCredential Class](/dotnet/api/azure.identity.azureclicredential) in .NET
* Java
  * [AzureCliCredential Class](/java/api/com.azure.identity.azureclicredential) in Java

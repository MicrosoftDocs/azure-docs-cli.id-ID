---
title: '| migrasi Microsoft Graph Microsoft Docs'
description: Pelajari tentang migrasi Microsoft Graph Azure CLI.
author: jiasli
ms.author: jiasli
manager: yonzhan
ms.date: 05/25/2022
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: microsoft graph, ms graph, active directory graph, ad graph
ms.openlocfilehash: 56aee00baf1be2dcdd19ae1cf112017f899049fc
ms.sourcegitcommit: 762ee662631c391498b81809e1603edb00bfdfae
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 06/29/2022
ms.locfileid: "146658519"
---
# <a name="microsoft-graph-migration"></a>Migrasi Microsoft Graph

Karena [penghentian Azure Active Directory (Azure AD) Graph](/graph/migrate-azure-ad-graph-overview), ACTIVE Directory Graph API yang mendasar akan digantikan oleh [Microsoft Graph API](/graph/api/overview) di Azure CLI 2.37.0.

## <a name="breaking-changes"></a>Perubahan mencolok

Untuk perbedaan API yang mendasar dan perubahan pemecahan JSON output, lihat [Perbedaan properti antara Azure AD Graph dan Microsoft Graph](/graph/migrate-azure-ad-graph-property-differences).

Misalnya, perubahan yang paling luar biasa adalah bahwa `objectId` properti dalam JSON output objek Graph digantikan oleh `id`.

Argumen perintah dan perubahan pemecahan perilaku tercantum di bawah ini.

### `az ad app create/update`

- Pisahkan `--reply-urls` menjadi `--web-redirect-uris` dan `--public-client-redirect-uris`
- Ganti `--homepage`dengan `--web-home-page-url`
- Ganti `--available-to-other-tenants`dengan `--sign-in-audience`
- Ganti `--native-app`dengan `--is-fallback-public-client`
- Ganti `--oauth2-allow-implicit-flow`dengan `--enable-access-token-issuance`
- Tambahkan `--enable-id-token-issuance` ke set `web/implicitGrantSettings/enableIdTokenIssuance`
- Hapus `--password` dan `--credential-description`. Gunakan `az ad app credential reset` untuk membiarkan layanan Graph membuat kata sandi untuk Anda (https://github.com/Azure/azure-cli/issues/20675)
- Tambahkan `--key-display-name` untuk mengatur `keyCredential``displayName`

### `az ad app permission grant`

- Hapus `--expires`
- `--scope` tidak lagi default ke `user_impersonation` dan sekarang diperlukan

### `az ad app credential reset`

- Ganti `--credential-description` dengan `--display-name` (https://github.com/Azure/azure-cli/issues/20561)
- Hapus `--password`. Tanpa menentukan argumen sertifikat, layanan Graph membuat kata sandi untuk Anda (https://github.com/Azure/azure-cli/issues/20675)

### `az ad sp delete`

- Perintah ini tidak lagi menghapus aplikasi yang sesuai. Gunakan `az ad app delete` untuk menghapus aplikasi secara eksplisit (https://github.com/Azure/azure-cli/issues/8467)
- Perintah ini tidak lagi menghapus penetapan peran yang sesuai dari perwakilan layanan. Gunakan `az role assignment delete` untuk menghapus penetapan peran secara eksplisit (https://github.com/Azure/azure-cli/issues/20805)

### `az ad sp credential`

- Grup perintah ini sekarang beroperasi pada perwakilan layanan, bukan aplikasi (https://github.com/Azure/azure-cli/issues/11458)

### `az ad sp credential reset`

- Ganti `--name`dengan `--id`
- Hapus `--password`. Tanpa menentukan argumen sertifikat, layanan Graph membuat kata sandi untuk Anda (https://github.com/Azure/azure-cli/issues/20675)

### `az ad user create`

- Ganti `--force-change-password-next-login`dengan `--force-change-password-next-sign-in`

### `az ad user update`

- Ganti `--force-change-password-next-login`dengan `--force-change-password-next-sign-in`

### `az ad group get-member-groups`

- Hapus `--additional-properties`

### `az ad group member add`

- Hapus `--additional-properties`

## <a name="known-issues"></a>Masalah yang diketahui

- Argumen `--add`pembaruan generik , `--set` dan `--remove` saat ini tidak berfungsi. Anda dapat menggunakan `az rest` untuk langsung memanggil Microsoft Graph API untuk properti yang tidak didukung.
- Perintah terkait Microsoft Graph seperti `az ad` dan `az role` akan gagal di lingkungan Azure Stack yang tidak memiliki dukungan Microsoft Graph. Gunakan Azure CLI 2.36.0 atau versi yang lebih lama untuk lingkungan Azure Stack.

## <a name="install-a-previous-version"></a>Menginstal versi sebelumnya

Jika Anda belum siap untuk migrasi, seperti tidak memiliki izin Microsoft Graph, Anda mungkin tetap menggunakan versi Azure CLI <= 2.36.0. Jika Anda telah menginstal 2.37.0, Anda dapat kembali ke versi sebelumnya mengikuti bagian "Instal versi tertentu" di bawah [dokumen penginstalan](./install-azure-cli.md) (kecuali untuk Homebrew yang tidak mendukung penginstalan versi sebelumnya).

## <a name="troubleshooting"></a>Pemecahan Masalah

### <a name="graph-command-fails-with-aadsts50005-or-aadsts53000"></a>Perintah Graph gagal dengan `AADSTS50005` atau `AADSTS53000`

Penyewa Anda mungkin memiliki kebijakan Akses Bersyarah yang memblokir penggunaan alur kode perangkat untuk mengakses Microsoft Graph. Dalam kasus seperti itu, gunakan alur kode otorisasi atau perwakilan layanan untuk masuk sebagai gantinya. Untuk informasi selengkapnya tentang metode masuk, silakan lihat [Masuk dengan Azure CLI](authenticate-azure-cli.md).

Penyewa Microsoft (72f988bf-86f1-41af-91ab-2d7cd011db47) memiliki kebijakan Akses Bersyarkat yang dikonfigurasi.

## <a name="give-feedback"></a>Berikan umpan balik

Jika Anda memiliki pertanyaan, silakan [kirimi kami umpan balik Anda](./get-started-with-azure-cli.md#give-feedback).
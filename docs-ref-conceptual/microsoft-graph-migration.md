---
title: '| migrasi Microsoft Graph Microsoft Docs'
description: Pelajari tentang migrasi Microsoft Graph Azure CLI.
author: jiasli
ms.author: jiasli
manager: yonzhan
ms.date: 03/08/2022
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: microsoft graph, ms graph, active directory graph, ad graph
ms.openlocfilehash: 0c4154dc74b28831ef1977c877cc9009998dc176
ms.sourcegitcommit: 52656c1c4e806d686ba3e799fd1d471944083360
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/17/2022
ms.locfileid: "145064637"
---
# <a name="microsoft-graph-migration"></a>Microsoft Graph migrasi

Karena [penghentian Graph Azure Active Directory (Azure AD),](/graph/migrate-azure-ad-graph-overview) ACTIVE Directory Graph API yang mendasar akan digantikan oleh Microsoft Graph API di Azure CLI 2.37.0.

## <a name="breaking-changes"></a>Perubahan mencolok

Untuk perbedaan PERUBAHAN pemecahan JSON API dan output yang [mendasar, lihat Perbedaan properti antara Azure AD Graph dan Microsoft Graph](/graph/migrate-azure-ad-graph-property-differences).

Misalnya, perubahan yang paling luar biasa adalah bahwa `objectId` properti dalam output JSON dari objek Graph digantikan oleh `id`.

Argumen perintah dan perubahan pemecahan perilaku tercantum di bawah ini.

### `az ad app create`

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
- Microsoft Graph perintah terkait seperti `az ad` dan `az role` akan gagal di lingkungan Azure Stack yang tidak memiliki dukungan Microsoft Graph. Silakan gunakan Azure CLI 3.36.0 atau versi yang lebih lama untuk lingkungan Azure Stack.

## <a name="try-azure-cli-beta-with-microsoft-graph"></a>Coba Azure CLI beta dengan Microsoft Graph

Azure CLI dibangun di [Python](https://www.python.org/). Versi Python yang didukung adalah 3.7, 3.8, 3.9, 3.10. Pada Windows, Anda harus [menginstal Python](https://www.python.org/downloads/windows/) terlebih dahulu.

Azure CLI beta hanya dapat diinstal dengan `pip` dari repositori Microsoft. Gunakan `python` atau `python3` untuk menjalankan perintah berikut, tergantung pada distribusi Linux atau versi Python yang diinstal.

Untuk menghindari penimpaan Azure CLI yang diinstal, sebaiknya instal versi beta di [lingkungan virtual](https://docs.python.org/3/tutorial/venv.html).

1. Membuat lingkungan virtual

   Navigasi ke folder tempat Anda ingin membuat lingkungan virtual, lalu jalankan:

   ```bash
   python -m venv <env_name>
   ```

2. Mengaktifkan lingkungan virtual

   ### <a name="powershell"></a>[PowerShell](#tab/powershell)

   ```powershell
   . .\<env_name>\Scripts\Activate.ps1
   ```

   ### <a name="linuxmacos-bash"></a>[Linux/macOS Bash](#tab/bash)

   ```bash
   . <env_name>/bin/activate
   ```
   ---
   Perintah ini juga dapat digunakan untuk mengaktifkan kembali lingkungan virtual Anda.

3. Menginstal Azure CLI beta

   ```bash
   python -m pip install --upgrade pip
   pip install --extra-index-url https://azurecliprod.blob.core.windows.net/beta/simple/ azure-cli
   ```
   Anda sekarang dapat mulai menggunakan Azure CLI beta.

4. Jika ada pembaruan, Anda dapat meningkatkan versi beta Azure CLI

   ```bash
   pip install --extra-index-url https://azurecliprod.blob.core.windows.net/beta/simple/ --upgrade azure-cli
   ```

5. Menonaktifkan lingkungan virtual

   Setelah selesai menggunakan Azure CLI beta, Anda dapat menutup jendela terminal, atau menggunakan `deactivate` perintah .

   ```bash
   deactivate
   ```

## <a name="uninstall-azure-cli-beta"></a>Mencopot pemasangan beta Azure CLI

Untuk menghapus instalan Azure CLI beta, hapus folder lingkungan virtual.

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell
Remove-Item -Force -Recurse <env_name>
```

### <a name="linuxmacos-bash"></a>[Linux/macOS Bash](#tab/bash)

```bash
rm -rf <env_name>
```

---

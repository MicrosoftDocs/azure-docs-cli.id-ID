---
title: '| migrasi Graph Microsoft Microsoft Docs'
description: Pelajari tentang migrasi Microsoft Graph Azure CLI.
author: jiasli
ms.author: jiasli
manager: yonzhan
ms.date: 02/24/2022
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: grafik microsoft, grafik ms, grafik direktori aktif, grafik iklan
ms.openlocfilehash: 397656ab4e0d90328f93a62445f8dcf901e3f06f
ms.sourcegitcommit: 49c01a527543e5de52f51ee19f930c78842c349e
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 03/08/2022
ms.locfileid: "139366218"
---
# <a name="microsoft-graph-migration"></a>Migrasi Graph Microsoft

Karena [penghentian Graph Azure Active Directory (Azure AD),](/graph/migrate-azure-ad-graph-overview) Azure CLI akan dimigrasikan dari Graph IKLAN ke Microsoft Graph.

## <a name="breaking-changes"></a>Perubahan mencolok

Untuk perbedaan perubahan pemecahan API dan output JSON yang mendasarinya, silakan lihat [perbedaan Properti antara Azure AD Graph dan Microsoft Graph](/graph/migrate-azure-ad-graph-property-differences).

Argumen perintah dan perubahan pelanggaran perilaku tercantum di bawah ini.

### `az ad app create`

- `--reply-urls` Argumen dibagi menjadi `--web-redirect-uris` dan `--public-client-redirect-uris`
- `--homepage` Argumen digantikan oleh `--web-home-page-url`
- `--available-to-other-tenants` Digantikan oleh `--sign-in-audience`
- `--native-app` Digantikan oleh `--is-fallback-public-client`
- `--oauth2-allow-implicit-flow` Digantikan oleh `--enable-access-token-issuance`
- `--enable-id-token-issuance` diperkenalkan untuk mengatur `web/implicitGrantSettings/enableIdTokenIssuance`
- `--password` dihapus. Gunakan `az ad app credential reset` untuk membiarkan Graph membuat kata sandi untuk Anda (https://github.com/Azure/azure-cli/issues/20675)

### `az ad app permission grant`

- `--expires` argumen dihapus

### `az ad app credential reset`

- `--credential-description` Digantikan oleh `--display-name` (https://github.com/Azure/azure-cli/issues/20561)
- `--password` dihapus. Tanpa menentukan argumen sertifikat, layanan Graph membuat kata sandi untuk Anda (https://github.com/Azure/azure-cli/issues/20675)

### `az ad sp delete`

- Perintah ini tidak lagi menghapus aplikasi yang sesuai. Gunakan `az ad app delete` untuk menghapus aplikasi secara eksplisit (https://github.com/Azure/azure-cli/issues/8467)
- Perintah ini tidak lagi menghapus penetapan peran yang sesuai dari perwakilan layanan. Gunakan `az role assignment delete` untuk menghapus penetapan peran secara eksplisit (https://github.com/Azure/azure-cli/issues/20805)

### `az ad sp credential`

- Grup perintah ini sekarang beroperasi pada perwakilan layanan, bukan aplikasi (https://github.com/Azure/azure-cli/issues/11458)

### `az ad sp credential reset`

- `--password` dihapus. Tanpa menentukan argumen sertifikat, layanan Graph membuat kata sandi untuk Anda (https://github.com/Azure/azure-cli/issues/20675)

### `az ad group get-member-groups`

- `--additional-properties` argumen dihapus

### `az ad group member add`

- `--additional-properties` argumen dihapus

## <a name="known-issues"></a>Masalah yang diketahui

- Argumen `--add`pembaruan generik, `--set` dan `--remove` saat ini tidak berfungsi
- `az ad`dan Microsoft Graph perintah terkait seperti `az role` akan gagal di lingkungan Azure Stack yang tidak memiliki dukungan Microsoft Graph

## <a name="try-azure-cli-beta-with-microsoft-graph"></a>Coba Azure CLI beta dengan Microsoft Graph

Azure CLI dibangun di atas [Python](https://www.python.org/). Versi Python yang didukung adalah 3.7, 3.8, 3.9, 3.10. Pada Windows, Anda harus [menginstal Python terlebih dahulu](https://www.python.org/downloads/windows/).

Azure CLI beta hanya dapat diinstal dari `pip` repositori Microsoft. Gunakan `python` atau `python3` untuk menjalankan perintah berikut, tergantung pada distribusi Linux atau versi Python yang Anda instal.

Untuk menghindari menimpa Azure CLI yang Anda instal, sebaiknya instal versi beta di [lingkungan virtual](https://docs.python.org/3/tutorial/venv.html).

1. Membuat lingkungan virtual

   Navigasikan ke folder tempat Anda ingin membuat lingkungan virtual, lalu jalankan:

   ```bash
   python -m venv <env_name>
   ```

2. Mengaktifkan lingkungan virtual

   ### <a name="windows-powershell"></a>[Windows PowerShell](#tab/powershell)

   ```powershell
   . .\<env_name>\Scripts\Activate.ps1
   ```

   ### <a name="linuxmacos-bash"></a>[Linux/macOS Bash](#tab/bash)

   ```bash
   . <env_name>/bin/activate
   ```
   ---
   Perintah ini juga dapat digunakan untuk mengaktifkan kembali lingkungan virtual Anda.

3. Install Azure CLI beta

   ```bash
   python -m pip install --upgrade pip
   pip install --extra-index-url https://azurecliprod.blob.core.windows.net/beta/simple/ azure-cli
   ```
   Anda sekarang dapat mulai menggunakan Azure CLI beta.
   
4. Jika ada pembaruan, Anda dapat meningkatkan Azure CLI beta

   ```bash
   pip install --extra-index-url https://azurecliprod.blob.core.windows.net/beta/simple/ --upgrade azure-cli
   ```

5. Menonaktifkan lingkungan virtual

   Setelah Selesai menggunakan Azure CLI beta, Anda dapat menutup jendela terminal, atau menggunakan perintah.`deactivate`

   ```bash
   deactivate
   ```

## <a name="uninstall-azure-cli-beta"></a>Uninstall Azure CLI beta

Untuk menghapus instalasi Azure CLI beta, hapus folder lingkungan virtual.

### <a name="windows-powershell"></a>[Windows PowerShell](#tab/powershell)

```powershell
Remove-Item -Force -Recurse <env_name>
```

### <a name="linuxmacos-bash"></a>[Linux/macOS Bash](#tab/bash)

```bash
rm -rf <env_name>
```

---

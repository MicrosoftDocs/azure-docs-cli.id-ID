---
title: Menginstal Azure CLI untuk Windows | Microsoft Docs
description: Untuk menginstal Azure CLI di Windows, Anda harus menggunakan Powershell, atau alat penginstal MSI, yang memberi Anda akses ke CLI melalui Windows Command Prompt (CMD).
author: jiasli
ms.author: jiasli
manager: yonzhan
ms.prod: azure
ms.date: 08/19/2021
ms.topic: conceptual
ms.devlang: azurecli
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: Menginstal azure cli, unduhan azure cli, cli untuk windows, menginstal azure cli di windows, azure cli windows, menginstal azure cli windows
ms.openlocfilehash: 098caabddfa2c1abbe6551b5f51fc76105f0d0e4
ms.sourcegitcommit: a805041ebd77f92fa4b3025ba6856ea4aedae2ac
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/22/2022
ms.locfileid: "144003102"
---
# <a name="install-azure-cli-on-windows"></a>Instal Azure CLI di Windows

Azure Command-Line Interface (CLI) adalah alat baris perintah lintas platform yang dapat diinstal secara lokal di komputer Windows. Anda dapat menggunakan Azure CLI untuk Windows untuk terhubung ke Azure dan menjalankan perintah administratif di sumber daya Azure. Azure CLI untuk Windows juga dapat digunakan dari browser melalui Azure Cloud Shell atau dijalankan dari dalam kontainer Docker.

Untuk Windows, Azure CLI diinstal melalui MSI, yang memberi Anda akses ke CLI melalui Perintah (CMD) Windows atau PowerShell.
Saat menginstal untuk Subsistem Windows untuk Linux (WSL), paket tersedia untuk distribusi Linux. Lihat [halaman penginstalan utama](install-azure-cli.md) untuk daftar pengelola paket yang didukung atau cara menginstal secara manual dengan WSL.

[!INCLUDE [current-version](includes/current-version.md)]

## <a name="install-or-update"></a>Menginstal atau memperbarui

MSI yang dapat didistribusikan digunakan untuk menginstal atau memperbarui Azure CLI di Windows. Anda tidak perlu menghapus instalan versi saat ini sebelum menggunakan alat penginstal MSI karena MSI akan memperbarui versi yang ada.

# <a name="microsoft-installer-msi"></a>[Alat Penginstal Microsoft (MSI)](#tab/azure-cli)

### <a name="latest-version"></a>Versi terbaru

Unduh dan instal Azure CLI rilis terbaru. Jika alat penginstal bertanya apakah dapat membuat perubahan pada komputer Anda, klik kotak "Ya". Setelah penginstalan selesai, Anda harus menutup dan membuka kembali jendela Perintah Windows atau PowerShell yang aktif untuk menggunakan Azure CLI.

> [!div class="nextstepaction"]
> [Azure CLI rilis terbaru](https://aka.ms/installazurecliwindows)

### <a name="specific-version"></a>Versi spesifik

Untuk mengunduh alat penginstal MSI untuk versi tertentu, ubah segmen versi di URL `https://azcliprod.blob.core.windows.net/msi/azure-cli-<version>.msi` dan unduh. Versi yang tersedia dapat ditemukan di [Catatan rilis Azure CLI](./release-notes-azure-cli.md).

# <a name="microsoft-installer-msi-with-command"></a>[Alat penginstal Microsoft (MSI) dengan Perintah](#tab/azure-powershell)

### <a name="powershell-command"></a>Perintah PowerShell

Anda juga dapat menginstal Azure CLI menggunakan PowerShell. Mulai PowerShell sebagai administrator dan jalankan perintah berikut:

> [!Note]
> PowerShell harus dijalankan sebagai administrator.

Mulai PowerShell sebagai administrator dan jalankan perintah berikut:

   ```PowerShell
   $ProgressPreference = 'SilentlyContinue'; Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'; rm .\AzureCLI.msi
   ```

Ini akan mengunduh dan menginstal Azure CLI versi terbaru untuk Windows. Jika Anda sudah menginstal versi, alat penginstal akan memperbarui versi yang ada.

Untuk menginstal versi tertentu, ganti argumen `-Uri` dengan `https://azcliprod.blob.core.windows.net/msi/azure-cli-<version>.msi` berserta segmen versi yang diubah. Versi yang tersedia dapat ditemukan di [Catatan rilis Azure CLI](./release-notes-azure-cli.md).

> [!Note]
> Setelah selesai menginstal, Anda harus membuka kembali PowerShell untuk menggunakan Azure CLI.

### <a name="azure-cli-command-for-update-only"></a>Perintah Azure CLI (hanya untuk pembaruan)
[!INCLUDE [az upgrade](includes/az-upgrade.md)]

---

## <a name="run-the-azure-cli"></a>Menjalankan Azure CLI

Anda kini dapat menjalankan Azure CLI dengan perintah `az` dari Perintah Windows atau PowerShell.

## <a name="troubleshooting"></a>Pemecahan Masalah

Berikut beberapa masalah umum yang muncul saat menginstal Azure CLI di Windows. Jika masalah Anda tidak tercantum di sini, [ajukan masalah di GitHub](https://github.com/Azure/azure-cli/issues).

### <a name="proxy-blocks-connection"></a>Koneksi blok proksi

Jika Anda tidak dapat mengunduh alat penginstal MSI karena proksi Anda memblokir koneksi, pastikan Anda telah mengonfigurasi proksi dengan benar. Untuk Windows 10, pengaturan ini dikelola di panel `Settings > Network & Internet > Proxy`. Hubungi administrator sistem untuk mengetahui pengaturan yang diperlukan, atau untuk situasi saat mesin Anda mungkin dikelola konfigurasi atau memerlukan pengaturan tingkat lanjut.

> [!IMPORTANT]
> Pengaturan ini juga diperlukan agar layanan Azure dapat diakses dengan CLI, baik dari PowerShell atau Perintah. Di PowerShell, Anda dapat melakukannya dengan perintah berikut:
>
> ```powershell
> (New-Object System.Net.WebClient).Proxy.Credentials = `
>   [System.Net.CredentialCache]::DefaultNetworkCredentials
> ```

Untuk mendapatkan MSI, proksi Anda perlu mengizinkan koneksi HTTPS ke alamat berikut:

* `https://aka.ms/`
* `https://azcliprod.blob.core.windows.net/`

## <a name="uninstall"></a>Hapus instalasi

[!INCLUDE [uninstall-boilerplate.md](includes/uninstall-boilerplate.md)]

Hapus instalan Azure CLI dari daftar "Aplikasi dan Fitur" Windows. Untuk menghapus instalan:

| Platform | Instruksi |
|---|---|
| Windows 10 | Mulai > Pengaturan > Aplikasi |
| Windows 8 dan Windows 7 | Mulai > Panel Kontrol > Program > Hapus instalan program |

Setelah berada di layar ini, ketik __Azure CLI__ ke dalam bilah pencarian program. Program yang akan dihapus instalannya tercantum sebagai __Microsoft CLI 2.0 untuk Azure__. Pilih aplikasi ini, lalu klik tombol `Uninstall`.

## <a name="remove-data"></a>Menghapus data

Jika Anda tidak ingin menginstal ulang Azure CLI, hapus datanya dari `C:\Users\<username>\.azure`.

## <a name="next-steps"></a>Langkah berikutnya

Setelah Anda menginstal Azure CLI di Windows, ikuti tur singkat tentang fitur dan perintah umumnya.

> [!div class="nextstepaction"]
> [Mulai menggunakan Azure CLI](get-started-with-azure-cli.md)
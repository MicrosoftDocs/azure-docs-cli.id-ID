---
title: Instal Azure CLI for Windows | Microsoft Docs
description: Untuk menginstal Azure CLI di Windows, Anda harus menggunakan Powershell, atau penginstal MSI, yang memberi Anda akses ke CLI melalui Command Prompt Windows (CMD).
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.prod: azure
ms.date: 08/19/2021
ms.topic: conceptual
ms.devlang: azurecli
ms.technology: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: Install azure cli, azure cli download, cli for windows, install azure cli on windows, azure cli windows, install azure cli windows
ms.openlocfilehash: fc6abf32252584188c5bb4c6328a0822f1f8710a
ms.sourcegitcommit: d2227bc475235bf86193e9cae5e02f349a6342e2
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 11/02/2021
ms.locfileid: "132439126"
---
# <a name="install-azure-cli-on-windows"></a>Instal Azure CLI di Windows

Azure Command-Line Interface (CLI) adalah alat command-line lintas platform yang dapat diinstal secara lokal di komputer Windows. Anda dapat menggunakan Azure CLI untuk Windows untuk terhubung ke Azure dan menjalankan perintah administratif pada sumber daya Azure. Azure CLI untuk Windows juga dapat digunakan dari browser melalui Azure Cloud Shell atau dijalankan dari dalam wadah Docker.

Untuk Windows, Azure CLI diinstal melalui MSI, yang memberi Anda akses ke CLI melalui Windows Command Prompt (CMD) atau PowerShell.
Saat menginstal untuk Subsistem Windows untuk Linux (WSL), paket tersedia untuk distribusi Linux Anda. Lihat [halaman instalasi utama](install-azure-cli.md) untuk daftar manajer paket yang didukung atau cara menginstal secara manual di bawah WSL.

[!INCLUDE [current-version](includes/current-version.md)]

## <a name="install-or-update"></a>Menginstal atau memperbarui

MSI didistribusikan digunakan untuk menginstal atau memperbarui Azure CLI pada Windows. Anda tidak perlu menghapus instalan versi saat ini sebelum menggunakan penginstal MSI karena MSI akan memperbarui versi yang ada.

# <a name="microsoft-installer-msi"></a>[Penginstal Microsoft (MSI)](#tab/azure-cli)

### <a name="latest-version"></a>Versi terbaru

Unduh dan instal rilis terbaru dari Azure CLI. Ketika penginstal menanyakan apakah itu dapat membuat perubahan pada komputer Anda, klik kotak "Ya". Setelah instalasi selesai, Anda harus menutup dan membuka kembali jendela Command Prompt Windows aktif atau PowerShell untuk menggunakan Azure CLI.

> [!div class="nextstepaction"]
> [Rilis terbaru dari Azure CLI](https://aka.ms/installazurecliwindows)

### <a name="specific-version"></a>Versi tertentu

Untuk mengunduh penginstal MSI untuk versi tertentu, ubah segmen versi di URL `https://azcliprod.blob.core.windows.net/msi/azure-cli-<version>.msi` dan unduh. Versi yang tersedia dapat ditemukan di [catatan rilis Azure CLI](/cli/azure/release-notes-azure-cli).

# <a name="microsoft-installer-msi-with-command"></a>[Microsoft Installer (MSI) dengan Command](#tab/azure-powershell)

### <a name="powershell-command"></a>Perintah Powershell

Anda juga dapat menginstal Azure CLI menggunakan PowerShell. Mulai PowerShell sebagai administrator dan jalankan perintah berikut:

> [!Note]
> PowerShell harus dijalankan sebagai administrator.

Mulai PowerShell sebagai administrator dan jalankan perintah berikut:

   ```PowerShell
   $ProgressPreference = 'SilentlyContinue'; Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'; rm .\AzureCLI.msi
   ```

Ini akan mengunduh dan menginstal versi terbaru dari Azure CLI untuk Windows. Jika Anda sudah memiliki versi yang diinstal, penginstal akan memperbarui versi yang ada.

Untuk menginstal versi tertentu, ganti `-Uri` argumen dengan segmen versi yang `https://azcliprod.blob.core.windows.net/msi/azure-cli-<version>.msi` diubah. Versi yang tersedia dapat ditemukan di [catatan rilis Azure CLI](/cli/azure/release-notes-azure-cli).

> [!Note]
> Setelah instalasi selesai, Anda harus membuka kembali PowerShell untuk menggunakan Azure CLI.

### <a name="azure-cli-command-for-update-only"></a>Azure CLI Command (for update only)
[!INCLUDE [az upgrade](includes/az-upgrade.md)]

---

## <a name="run-the-azure-cli"></a>Menjalankan Azure CLI

Anda sekarang dapat menjalankan Azure CLI dengan `az` perintah dari Command Prompt Windows atau PowerShell.

## <a name="troubleshooting"></a>Pemecahan Masalah

Berikut adalah beberapa masalah umum yang terlihat saat menginstal Azure CLI di Windows. Jika Anda mengalami masalah yang tidak tercakup di sini, [ajukan masalah di GitHub.](https://github.com/Azure/azure-cli/issues)

### <a name="proxy-blocks-connection"></a>Koneksi blok proksi

Jika Anda tidak dapat mengunduh penginstal MSI karena proxy Anda memblokir koneksi, pastikan bahwa proxy Anda dikonfigurasi dengan benar. Untuk Windows 10, pengaturan ini dikelola di `Settings > Network & Internet > Proxy` panel. Hubungi administrator sistem Anda untuk pengaturan yang diperlukan, atau untuk situasi di mana mesin Anda mungkin dikelola konfigurasi atau memerlukan pengaturan lanjutan.

> [!IMPORTANT]
> Pengaturan ini juga diperlukan untuk dapat mengakses layanan Azure dengan CLI, baik dari PowerShell atau Command Prompt. Di PowerShell, Anda melakukan ini dengan perintah berikut:
>
> ```powershell
> (New-Object System.Net.WebClient).Proxy.Credentials = `
>   [System.Net.CredentialCache]::DefaultNetworkCredentials
> ```

Untuk mendapatkan MSI, proxy Anda perlu mengizinkan koneksi HTTPS ke alamat berikut:

* `https://aka.ms/`
* `https://azcliprod.blob.core.windows.net/`

## <a name="uninstall"></a>Hapus instalasi

[!INCLUDE [uninstall-boilerplate.md](includes/uninstall-boilerplate.md)]

Anda menghapus instalasi Azure CLI dari daftar "Aplikasi dan Fitur" Windows. Untuk menghapus instalasi:

| Platform | Instruksi |
|---|---|
| Windows 10 | Mulai aplikasi > Pengaturan > |
| Windows 8 dan Windows 7 | Mulai > Control Panel > Program > Uninstall Program |

Setelah di layar ini ketik __Azure CLI__ ke dalam bilah pencarian program. Program untuk menghapus instalasi terdaftar sebagai __Microsoft CLI 2.0 untuk Azure.__ Pilih aplikasi ini, lalu klik `Uninstall` tombolnya.

## <a name="remove-data"></a>Menghapus data

Jika Anda tidak berencana untuk menginstal ulang Azure CLI, hapus datanya dari `C:\Users\<username>\.azure` .

## <a name="next-steps"></a>Langkah berikutnya

Sekarang setelah Anda menginstal Azure CLI di Windows, ikuti tur singkat dari fitur dan perintah umumnya.

> [!div class="nextstepaction"]
> [Mulai menggunakan Azure CLI](get-started-with-azure-cli.md)

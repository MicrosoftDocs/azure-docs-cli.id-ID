---
title: Masuk dengan Azure CLI — login dan otentikasi | Microsoft Docs
description: Pelajari berbagai jenis autentikasi untuk login Azure CLI Anda — masuk dengan Azure CLI secara otomatis, lokal, atau interaktif menggunakan perintah login az.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 09/10/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: az login, authentication types , authentication methods, azure, cli login, az login powershell, cli login
ms.openlocfilehash: 25a5f4e11d3e71dcaae604fba43b334ad3344b1d
ms.sourcegitcommit: 23211f978c3a7079b2884355be102a9f18fea713
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 12/01/2021
ms.locfileid: "133330625"
---
# <a name="sign-in-with-azure-cli"></a>Masuk dengan Azure CLI 

Ada beberapa tipe autentikasi untuk Azure Command-Line Interface (CLI), jadi bagaimana Anda masuk?  Cara termudah untuk memulai adalah dengan [Azure Cloud Shell,](/azure/cloud-shell/overview)yang secara otomatis masuk ke Dalam Anda.
Secara lokal, Anda dapat masuk secara interaktif melalui browser Anda dengan perintah [login az.](/cli/azure/reference-index#az_login) Saat menulis skrip, pendekatan yang disarankan adalah menggunakan prinsip layanan. Dengan memberikan hanya izin yang sesuai yang diperlukan untuk kepala layanan, Anda dapat menjaga otomatisasi Anda aman.

Tak satu pun dari informasi login Anda disimpan oleh Azure CLI. Sebagai gantinya, [token refresh otentikasi](/azure/active-directory/develop/v1-id-and-access-tokens#refresh-tokens) dihasilkan oleh Azure dan disimpan. Pada Agustus 2018 token ini dicabut setelah 90 hari tidak aktif, tetapi nilai ini dapat diubah oleh Microsoft atau administrator penyewa Anda. Setelah token dicabut, Anda mendapatkan pesan dari CLI yang mengatakan Anda perlu login lagi.

Setelah masuk, perintah CLI dijalankan terhadap langganan default Anda. Jika Anda memiliki beberapa langganan, Anda dapat [mengubah langganan default Anda.](manage-azure-subscriptions-azure-cli.md)

## <a name="sign-in-interactively"></a>Masuk secara interaktif

Metode otentikasi default Azure CLI untuk login menggunakan browser web dan mengakses token untuk masuk.

[!INCLUDE [interactive_login](includes/interactive-login.md)]

## <a name="sign-in-with-credentials-on-the-command-line"></a>Masuk dengan kredensial pada baris perintah

Berikan kredensial pengguna Azure Anda di baris perintah.

> [!Note]
> Pendekatan ini tidak berfungsi dengan akun Microsoft atau akun yang mengaktifkan autentikasi dua faktor.

```azurecli-interactive
az login -u <username> -p <password>
```

> [!IMPORTANT]
> Jika Anda ingin menghindari menampilkan kata sandi Anda di konsol dan menggunakan `az login` secara interaktif, gunakan `read -s` perintah di bawah `bash` ini.
>
> ```bash
> read -sp "Azure password: " AZ_PASS && echo && az login -u <username> -p $AZ_PASS
> ```
>
> Di bawah PowerShell, gunakan `Get-Credential` cmdlet.
>
> ```powershell
> $AzCred = Get-Credential -UserName <username>
> az login -u $AzCred.UserName -p $AzCred.GetNetworkCredential().Password
> ```

## <a name="sign-in-with-a-service-principal"></a>Masuk dengan kepala layanan

Prinsip layanan adalah akun yang tidak terkait dengan pengguna tertentu, yang dapat memiliki izin pada mereka yang ditetapkan melalui peran yang telah ditentukan sebelumnya. Mengautentikasi dengan prinsip layanan adalah cara terbaik untuk menulis skrip atau program yang aman, memungkinkan Anda menerapkan pembatasan izin dan informasi kredensial statis yang disimpan secara lokal. Untuk mempelajari [selengkapnya](./create-an-azure-service-principal-azure-cli.md#sign-in-using-a-service-principal)tentang prinsipal layanan, lihat Membuat kepala layanan Azure dengan Azure CLI .

Untuk masuk dengan kepala layanan, Anda perlu:

* URL atau nama yang terkait dengan prinsip layanan
* Kata sandi utama layanan, atau sertifikat X509 yang digunakan untuk membuat prinsip layanan dalam format PEM
* Penyewa yang terkait dengan prinsip layanan, baik sebagai `.onmicrosoft.com` domain atau ID objek Azure

> [!NOTE]
> **Sertifikat** harus ditambahkan ke **KUNCI PRIBADI** dalam file PEM. Untuk contoh format file PEM, lihat [Autentikasi berbasis sertifikat.](create-an-azure-service-principal-azure-cli.md#certificate-based-authentication) 

> [!IMPORTANT]
>
> Jika kepala layanan Anda menggunakan sertifikat yang disimpan di Key Vault, kunci pribadi sertifikat tersebut harus tersedia tanpa masuk ke Azure. Untuk mengambil sertifikat untuk `az login` , lihat Mengambil sertifikat dari Key [Vault.](create-an-azure-service-principal-azure-cli.md#retrieve-certificate-from-key-vault)

```azurecli-interactive
az login --service-principal -u <app-id> -p <password-or-cert> --tenant <tenant>
```

> [!IMPORTANT]
> Jika Anda ingin menghindari menampilkan kata sandi Anda di konsol dan menggunakan `az login` secara interaktif, gunakan `read -s` perintah di bawah `bash` ini.
>
> ```bash
> read -sp "Azure password: " AZ_PASS && echo && az login --service-principal -u <app-id> -p $AZ_PASS --tenant <tenant>
> ```
>
> Di bawah PowerShell, gunakan `Get-Credential` cmdlet.
>
> ```powershell
> $AzCred = Get-Credential -UserName <app-id>
> az login --service-principal -u $AzCred.UserName -p $AzCred.GetNetworkCredential().Password --tenant <tenant>
> ```

## <a name="sign-in-with-a-different-tenant"></a>Masuk dengan penyewa yang berbeda

Anda dapat memilih penyewa untuk masuk di bawah dengan `--tenant` argumen. Nilai argumen ini bisa berupa `.onmicrosoft.com` domain atau ID objek Azure untuk penyewa. Kedua metode masuk interaktif dan baris perintah bekerja dengan `--tenant` .

```azurecli-interactive
az login --tenant <tenant>
```

## <a name="sign-in-with-a-managed-identity"></a>Masuk dengan identitas terkelola

Pada sumber daya yang dikonfigurasi untuk identitas terkelola untuk sumber daya Azure, Anda dapat masuk menggunakan identitas terkelola. Masuk dengan identitas sumber daya dilakukan melalui `--identity` bendera.

```azurecli-interactive
az login --identity
```

Jika sumber daya memiliki beberapa pengguna yang menetapkan identitas terkelola dan tidak ada identitas yang ditetapkan sistem, Anda harus menentukan id klien atau id objek atau id sumber daya dari identitas terkelola yang ditetapkan pengguna `--username` untuk login.
```azurecli-interactive
az login --identity --username <client_id|object_id|resource_id>
```

Untuk mempelajari selengkapnya tentang identitas terkelola untuk sumber daya Azure, lihat [Mengonfigurasi identitas terkelola untuk sumber daya Azure](/azure/active-directory/managed-identities-azure-resources/qs-configure-cli-windows-vm) dan Menggunakan identitas [terkelola untuk sumber daya Azure untuk masuk](/azure/active-directory/managed-identities-azure-resources/how-to-use-vm-sign-in).

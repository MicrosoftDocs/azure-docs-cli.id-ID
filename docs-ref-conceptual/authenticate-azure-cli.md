---
title: Masuk dengan Azure CLI — Aktivitas Masuk dan Autentikasi | Microsoft Docs
description: Pelajari berbagai jenis autentikasi untuk aktivitas masuk Azure CLI — masuk dengan Azure CLI secara otomatis, lokal, atau interaktif menggunakan perintah az login.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 09/10/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: az login, jenis autentikasi, metode autentikasi, azure, cli login, az login powershell, cli login
ms.openlocfilehash: 1272165a031169b2b3fcdee79d16ae4dd1b091f5
ms.sourcegitcommit: ad79327952adf0f8be8f1b9678e72434d9f03f0c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/12/2022
ms.locfileid: "138520331"
---
# <a name="sign-in-with-azure-cli"></a>Masuk dengan Azure CLI 

Ada beberapa jenis autentikasi untuk Azure Command-Line Interface (CLI), jadi bagaimana cara Anda masuk?  Cara termudah untuk memulai adalah dengan [Azure Cloud Shell](/azure/cloud-shell/overview), yang secara otomatis memasukkan Anda.
Secara lokal, Anda dapat masuk secara interaktif melalui browser dengan perintah [az login](/cli/azure/reference-index#az-login). Saat menulis skrip, pendekatan yang disarankan adalah menggunakan perwakilan layanan. Dengan hanya memberikan izin yang sesuai yang diperlukan untuk prinsip layanan, Anda dapat menjaga otomatisasi tetap aman.

Tak satu pun dari informasi masuk Anda disimpan oleh Azure CLI. Sebagai gantinya, [token refresh autentikasi](/azure/active-directory/develop/v1-id-and-access-tokens#refresh-tokens) dihasilkan oleh Azure dan disimpan. Mulai Agustus 2018, token ini dicabut setelah 90 hari tidak aktif, tetapi nilai ini dapat diubah oleh Microsoft atau administrator penyewa Anda. Setelah token dicabut, Anda mendapatkan pesan dari CLI yang meminta Anda untuk masuk lagi.

Setelah masuk, perintah CLI dijalankan terhadap langganan default Anda. Jika memiliki beberapa langganan, Anda dapat [mengubah langganan default](manage-azure-subscriptions-azure-cli.md).

## <a name="sign-in-interactively"></a>Masuk secara interaktif

Metode autentikasi default di Azure CLI untuk aktivitas masuk menggunakan browser web dan mengakses token untuk masuk.

[!INCLUDE [interactive_login](includes/interactive-login.md)]

## <a name="sign-in-with-credentials-on-the-command-line"></a>Masuk dengan info masuk di baris perintah

Masukkan info masuk pengguna Azure Anda di baris perintah.

> [!Note]
> Pendekatan ini tidak berfungsi dengan akun Microsoft atau akun yang mengaktifkan autentikasi dua faktor.

```azurecli-interactive
az login -u <username> -p <password>
```

> [!IMPORTANT]
> Jika Anda tidak ingin menampilkan kata sandi di konsol dan menggunakan `az login` secara interaktif, gunakan perintah `read -s` di bagian `bash`.
>
> ```bash
> read -sp "Azure password: " AZ_PASS && echo && az login -u <username> -p $AZ_PASS
> ```
>
> Di PowerShell, gunakan Cmdlet `Get-Credential`.
>
> ```powershell
> $AzCred = Get-Credential -UserName <username>
> az login -u $AzCred.UserName -p $AzCred.GetNetworkCredential().Password
> ```

## <a name="sign-in-with-a-service-principal"></a>Masuk dengan perwakilan layanan

Perwakilan layanan adalah akun yang tidak terikat pada pengguna tertentu, yang dapat memiliki izin pada mereka yang ditetapkan melalui peran yang ditentukan sebelumnya. Autentikasi dengan perwakilan layanan adalah cara terbaik untuk menulis skrip atau program yang aman, sehingga Anda dapat menerapkan pembatasan izin dan informasi info masuk statik yang disimpan secara lokal. Untuk informasi selengkapnya tentang perwakilan layanan, lihat [Membuat perwakilan layanan Azure dengan Azure CLI](./create-an-azure-service-principal-azure-cli.md#4-sign-in-using-a-service-principal).

Untuk masuk dengan perwakilan layanan, Anda memerlukan:

* URL atau nama yang terkait dengan perwakilan layanan
* Kata sandi perwakilan layanan, atau sertifikat X509 yang digunakan untuk membuat perwakilan layanan dalam format PEM
* Penyewa yang terkait dengan perwakilan layanan, baik sebagai domain `.onmicrosoft.com` atau ID objek Azure

> [!NOTE]
> **CERTIFICATE** harus ditambahkan ke **PRIVATE KEY** dalam file PEM. Untuk contoh format file PEM, lihat [Autentikasi berbasis sertifikat](create-an-azure-service-principal-azure-cli.md#certificate-based-authentication). 

> [!IMPORTANT]
>
> Jika perwakilan layanan Anda menggunakan sertifikat yang disimpan di Key Vault, kunci privat sertifikat tersebut harus tersedia tanpa masuk ke Azure. Untuk mengambil sertifikat untuk `az login`, lihat [Mengambil sertifikat dari Key Vault](create-an-azure-service-principal-azure-cli.md#retrieve-certificate-from-key-vault).

```azurecli-interactive
az login --service-principal -u <app-id> -p <password-or-cert> --tenant <tenant>
```

> [!IMPORTANT]
> Jika Anda tidak ingin menampilkan kata sandi di konsol dan menggunakan `az login` secara interaktif, gunakan perintah `read -s` di bagian `bash`.
>
> ```bash
> read -sp "Azure password: " AZ_PASS && echo && az login --service-principal -u <app-id> -p $AZ_PASS --tenant <tenant>
> ```
>
> Di PowerShell, gunakan Cmdlet `Get-Credential`.
>
> ```powershell
> $AzCred = Get-Credential -UserName <app-id>
> az login --service-principal -u $AzCred.UserName -p $AzCred.GetNetworkCredential().Password --tenant <tenant>
> ```

## <a name="sign-in-with-a-different-tenant"></a>Masuk dengan penyewa yang berbeda

Anda dapat memilih penyewa untuk masuk di bawah dengan argumen `--tenant`. Nilai argumen ini bisa berupa domain `.onmicrosoft.com` atau ID objek Azure untuk penyewa. Metode masuk interaktif dan baris perintah berfungsi dengan `--tenant`.

```azurecli-interactive
az login --tenant <tenant>
```

## <a name="sign-in-with-a-managed-identity"></a>Masuk dengan identitas terkelola

Di sumber daya yang dikonfigurasi untuk identitas terkelola untuk sumber daya Azure, Anda dapat masuk menggunakan identitas terkelola. Masuk dengan identitas sumber daya dilakukan melalui bendera `--identity`.

```azurecli-interactive
az login --identity
```

Jika sumber daya memiliki beberapa identitas terkelola yang ditetapkan pengguna dan tidak ada identitas yang ditetapkan sistem, Anda harus menentukan ID klien atau ID objek atau ID sumber daya identitas terkelola yang ditetapkan pengguna dengan `--username` untuk aktivitas masuk.
```azurecli-interactive
az login --identity --username <client_id|object_id|resource_id>
```

Untuk mempelajari lebih lanjut identitas terkelola untuk sumber daya Azure, lihat [Mengonfigurasi identitas terkelola untuk sumber daya Azure](/azure/active-directory/managed-identities-azure-resources/qs-configure-cli-windows-vm) dan [Menggunakan identitas terkelola untuk sumber daya Azure untuk aktivitas masuk](/azure/active-directory/managed-identities-azure-resources/how-to-use-vm-sign-in).

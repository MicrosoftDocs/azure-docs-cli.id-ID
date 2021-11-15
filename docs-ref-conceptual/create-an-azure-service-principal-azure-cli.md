---
title: Create an Azure service principal – Azure CLI | Microsoft Docs
description: Pelajari cara membuat dan menggunakan prinsip layanan dengan Azure CLI. Gunakan prinsip layanan untuk mendapatkan kontrol atas sumber daya Azure yang dapat diakses.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure service principal, create service principal azure, create service principal azure cli
ms.openlocfilehash: 37ecfc1adcb7e7b8cb6b377b7c60466fabe03d49
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439069"
---
# <a name="create-an-azure-service-principal-with-the-azure-cli"></a>Membuat perwakilan layanan Azure dengan Azure CLI

Alat otomatis yang menggunakan layanan Azure harus selalu memiliki izin terbatas. Alih-alih memiliki aplikasi masuk sebagai pengguna yang sepenuhnya istimewa, Azure menawarkan prinsip layanan.

## <a name="what-is-an-azure-service-principal"></a>Apa itu kepala layanan Azure?

Prinsip layanan Azure adalah identitas yang dibuat untuk digunakan dengan aplikasi, layanan yang dihosting, dan alat otomatis untuk mengakses sumber daya Azure. Akses ini dibatasi oleh peran yang ditugaskan kepada kepala layanan, memberi Anda kontrol atas sumber daya mana yang dapat diakses dan pada tingkat mana. Untuk alasan keamanan, selalu disarankan untuk menggunakan perwakilan layanan dengan alat otomatis dibanding mengizinkan mereka masuk dengan identitas pengguna.

Artikel ini menunjukkan kepada Anda langkah-langkah untuk membuat, mendapatkan informasi tentang, dan mengatur ulang kepala layanan Azure dengan Azure CLI.

## <a name="create-a-service-principal"></a>Buat perwakilan layanan

Buat kepala layanan Azure dengan perintah [az ad sp create-for-rbac.](/cli/azure/ad/sp#az_ad_sp_create_for_rbac) 

Dan `appId` `tenant` kunci muncul dalam output dan digunakan `az ad sp create-for-rbac` dalam otentikasi utama layanan. Catat nilainya, tetapi nilai dapat diambil kapan saja dengan [daftar az ad sp](/cli/azure/ad/sp#az_ad_sp_list).

Saat membuat prinsip layanan, Anda memilih jenis autentikasi masuk yang digunakannya. Ada dua jenis otentikasi yang tersedia untuk prinsip layanan Azure: otentikasi berbasis kata sandi, dan otentikasi berbasis sertifikat.

> [!NOTE]
>
> Jika akun Anda tidak memiliki izin untuk membuat pokok layanan, `az ad sp create-for-rbac` akan mengembalikan pesan kesalahan yang berisi "Hak istimewa yang tidak memadai untuk menyelesaikan operasi." Hubungi admin Azure Active Directory Anda untuk membuat kepala layanan.

> [!WARNING]
> Saat Anda membuat kepala layanan Azure menggunakan `az ad sp create-for-rbac` perintah, output menyertakan kredensial yang harus Anda lindungi. Pastikan Anda tidak menyertakan kredensial ini dalam kode Anda atau periksa kredensial ke dalam kontrol sumber Anda. Sebagai alternatif, pertimbangkan untuk menggunakan [identitas terkelola](/azure/active-directory/managed-identities-azure-resources/overview) jika tersedia untuk menghindari kebutuhan untuk menggunakan kredensial.
>
> Secara default, `az ad sp create-for-rbac` memberikan peran [Kontributor](/azure/role-based-access-control/built-in-roles#contributor) ke kepala layanan di lingkup langganan. Untuk mengurangi risiko kepala layanan yang dikompromikan, tetapkan peran yang lebih spesifik dan persempit ruang lingkup ke sumber daya atau kelompok sumber daya. Lihat [Langkah-langkah untuk menambahkan tugas peran](/azure/role-based-access-control/role-assignments-steps) untuk informasi selengkapnya.
>
> Dalam rilis di masa mendatang, `az ad sp create-for-rbac` TIDAK akan membuat tugas peran **Kontributor** secara default. Jika diperlukan, gunakan `--role` argumen untuk secara eksplisit membuat tugas peran.

### <a name="password-based-authentication"></a>Autentikasi berbasis kata sandi

Tanpa parameter otentikasi, autentikasi berbasis kata sandi digunakan dengan kata sandi acak yang dibuat untuk Anda.

  ```azurecli-interactive
  az ad sp create-for-rbac --name ServicePrincipalName
  ```

> [!IMPORTANT]
> Pada Azure CLI 2.0.68, `--password` parameter untuk membuat prinsip layanan dengan kata sandi yang ditentukan pengguna tidak lagi __didukung__ untuk mencegah penggunaan kata sandi yang lemah secara tidak sengaja.

Output untuk prinsip layanan dengan otentikasi kata sandi termasuk `password` kuncinya. __Pastikan__ Anda menyalin nilai ini - tidak dapat diambil. Jika Anda lupa kata sandi, [atur ulang info masuk perwakilan layanan](#reset-credentials).

### <a name="certificate-based-authentication"></a>Autentikasi berbasis sertifikat

Untuk autentikasi berbasis sertifikat, gunakan `--cert` argumen. Argumen ini mengharuskan Anda memegang sertifikat yang ada. Pastikan alat apa pun yang menggunakan prinsipal layanan ini memiliki akses ke kunci pribadi sertifikat. Sertifikat harus dalam format ASCII seperti PEM, CER, atau DER. Lulus sertifikat sebagai string, atau menggunakan `@path` format untuk memuat sertifikat dari file.

> [!NOTE]
> Saat menggunakan file PEM, **SERTIFIKAT** harus ditambahkan ke **KUNCI PRIBADI** dalam file.

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --cert "-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----"
```

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --cert @/path/to/cert.pem
```

`--keyvault`Argumen dapat ditambahkan untuk menggunakan sertifikat di Azure Key Vault. Dalam hal ini, `--cert` nilainya adalah nama sertifikat.

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --cert CertName --keyvault VaultName
```

Untuk membuat sertifikat _yang ditandatangani sendiri_ untuk autentikasi, gunakan `--create-cert` argumen:

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --create-cert
```

Output konsol:

```
Creating a role assignment under the scope of "/subscriptions/myId"
Please copy C:\myPath\myNewFile.pem to a safe place.
When you run 'az login', provide the file path in the --password argument
{
  "appId": "myAppId",
  "displayName": "myDisplayName",
  "fileWithCertAndPrivateKey": "C:\\myPath\\myNewFile.pem",
  "name": "http://myName",
  "password": null,
  "tenant": "myTenantId"
}
```

Isi dari file PEM baru:
```
-----BEGIN PRIVATE KEY-----
myPrivateKeyValue
-----END PRIVATE KEY-----
-----BEGIN CERTIFICATE-----
myCertificateValue
-----END CERTIFICATE-----
```

> [!NOTE]
> `az ad sp create-for-rbac --create-cert`Perintah membuat kepala layanan dan file PEM. File PEM berisi KUNCI **DAN** **SERTIFIKAT** PRIBADI yang diformat dengan benar.

`--keyvault`Argumen dapat ditambahkan untuk menyimpan sertifikat di Azure Key Vault. Saat `--keyvault` menggunakan, `--cert` argumen __diperlukan.__

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --create-cert --cert CertName --keyvault VaultName
```

Kecuali Anda menyimpan sertifikat di Key Vault, outputnya termasuk `fileWithCertAndPrivateKey` kuncinya. Nilai kunci ini memberi tahu Anda di mana sertifikat yang dihasilkan disimpan.
__Pastikan__ Anda menyalin sertifikat ke lokasi yang aman, atau Anda tidak dapat masuk dengan kepala layanan ini.

Jika Anda kehilangan akses ke kunci pribadi sertifikat, [atur ulang kredensial utama layanan.](#reset-credentials)

#### <a name="retrieve-certificate-from-key-vault"></a>Mengambil sertifikat dari Key Vault

Untuk sertifikat yang disimpan di Key Vault, ambil sertifikat dengan kunci pribadinya dengan [az keyvault secret show](/cli/azure/keyvault/secret#az_keyvault_secret_show) dan konversi ke file PEM. Di Key Vault, nama rahasia sertifikat sama dengan nama sertifikat.

```azurecli-interactive
az keyvault secret download --file /path/to/cert.pfx --vault-name VaultName --name CertName --encoding base64
openssl pkcs12 -in cert.pfx -passin pass: -out cert.pem -nodes
```

## <a name="get-an-existing-service-principal"></a>Dapatkan prinsip layanan yang sudah ada

Daftar kepala layanan di penyewa dapat diambil dengan [daftar az ad sp.](/cli/azure/ad/sp#az_ad_sp_list) Secara default perintah ini mengembalikan 100 prinsip layanan pertama untuk penyewa Anda. Untuk mendapatkan semua prinsip layanan penyewa, gunakan `--all` argumen. Mendapatkan daftar ini bisa memakan waktu lama, jadi disarankan agar Anda memfilter daftar dengan salah satu argumen berikut:

* `--display-name` meminta kepala layanan yang memiliki _awalan_ yang sesuai dengan nama yang disediakan. Nama tampilan kepala layanan adalah nilai yang ditetapkan dengan `--name` parameter selama pembuatan. Jika Anda tidak mengatur `--name` selama pembuatan utama layanan, awalan nama adalah `azure-cli-` .
* `--spn` filter pada pencocokan nama utama layanan yang tepat. Nama utama layanan selalu dimulai dengan `https://` .
  jika nilai yang Anda gunakan `--name` bukan URI, nilai ini `https://` diikuti oleh nama tampilan.
* `--show-mine` hanya meminta prinsip layanan yang dibuat oleh pengguna yang masuk.
* `--filter`mengambil filter OData, dan melakukan penyaringan _sisi server._ Metode ini direkomendasikan untuk menyaring sisi klien dengan `--query` argumen CLI. Untuk mempelajari filter OData, lihat [sintaks ekspresi OData untuk filter](/rest/api/searchservice/odata-expression-syntax-for-azure-search).

Informasi yang dikembalikan untuk objek utama layanan adalah verbose. Untuk mendapatkan hanya informasi yang diperlukan untuk masuk, gunakan string `[].{id:appId, tenant:appOwnerTenantId}` kueri. Misalnya, untuk mendapatkan informasi masuk untuk semua prinsip layanan yang dibuat oleh pengguna yang saat ini masuk:

```azurecli-interactive
az ad sp list --show-mine --query "[].{id:appId, tenant:appOwnerTenantId}"
```

> [!IMPORTANT]
>
> `az ad sp list` atau [az ad sp show](/cli/azure/ad/sp#az_ad_sp_show) mendapatkan pengguna dan penyewa, tetapi tidak ada rahasia otentikasi _atau_ metode otentikasi.
> Rahasia untuk sertifikat di Key Vault dapat diambil dengan [az keyvault secret show,](/cli/azure/keyvault/secret#az_keyvault_secret_show)tetapi tidak ada rahasia lain yang disimpan secara default.
> Jika Anda lupa metode otentikasi atau rahasia, [atur ulang kredensial utama layanan.](#reset-credentials)

## <a name="manage-service-principal-roles"></a>Mengelola peran utama layanan

Azure CLI memiliki perintah berikut untuk mengelola tugas peran:

* [az role assignment list](/cli/azure/role/assignment#az_role_assignment_list)
* [pembuatan penetapan peran az](/cli/azure/role/assignment#az_role_assignment_create)
* [az role assignment delete](/cli/azure/role/assignment#az_role_assignment_delete)

Peran default untuk kepala layanan adalah **Kontributor.** Peran ini memiliki izin penuh untuk membaca dan menulis ke akun Azure. Peran **Pembaca** lebih ketat, dengan akses baca saja.  Untuk informasi selengkapnya tentang Role-Based Access Control (RBAC) dan peran, lihat [RBAC: Built-in roles](/azure/active-directory/role-based-access-built-in-roles).

Contoh ini menambahkan peran **Pembaca** dan menghapus **Kontributor:**

```azurecli-interactive
az role assignment create --assignee APP_ID --role Reader
az role assignment delete --assignee APP_ID --role Contributor
```

> [!NOTE]
> Jika akun Anda tidak memiliki izin untuk menetapkan peran, Anda melihat pesan kesalahan bahwa akun Anda "tidak memiliki otorisasi untuk melakukan tindakan 'Microsoft.Authorization/roleAssignments/write'." Hubungi admin Azure Active Directory Anda untuk mengelola peran.

Menambahkan peran _tidak_ membatasi izin yang ditetapkan sebelumnya. Saat membatasi izin kepala layanan, peran __Kontributor__ harus dihapus.

Perubahan dapat diverifikasi dengan mencantumkan peran yang ditetapkan:

```azurecli-interactive
az role assignment list --assignee APP_ID
```

## <a name="sign-in-using-a-service-principal"></a>Masuk menggunakan prinsipal layanan

Uji kredensial dan izin kepala layanan baru dengan masuk. Untuk masuk dengan kepala layanan, Anda memerlukan `appId` , `tenant` , dan kredensial.

Untuk masuk dengan kepala layanan menggunakan kata sandi:

```azurecli-interactive
az login --service-principal --username APP_ID --password PASSWORD --tenant TENANT_ID
```

Untuk masuk dengan sertifikat, harus tersedia secara lokal sebagai file PEM atau DER, dalam format ASCII. Saat menggunakan file PEM, **KUNCI PRIBADI** dan **SERTIFIKAT** harus ditambahkan bersama-sama dalam file.

```azurecli-interactive
az login --service-principal --username APP_ID --tenant TENANT_ID --password /path/to/cert
```

Untuk mempelajari [selengkapnya](authenticate-azure-cli.md)tentang masuk dengan kepala layanan, lihat Masuk dengan Azure CLI .

## <a name="create-a-resource-using-service-principal"></a>Membuat sumber daya menggunakan prinsipal layanan

Bagian berikut memberikan contoh cara membuat sumber daya untuk [Azure Storage](/azure/storage/) dengan kepala layanan, menggunakan perintah berikut:

* [az login](/cli/azure/reference-index#az_login)
* [pembuatan grup az](/cli/azure/group#az_group_create)
* [az storage account create](/cli/azure/storage/account#az_storage_account_create)
* [daftar kunci akun penyimpanan az](/cli/azure/storage/account/keys#az_storage_account_keys_list)

Untuk masuk dengan kepala layanan, Anda memerlukan `appId` , , dan kembali sebagai jawaban ketika Anda membuat kepala layanan `tenant` `password` [Anda.](#sign-in-using-a-service-principal)

1. Masuk sebagai kepala layanan.

    ```azurecli-interactive
    az login --service-principal --username APP_ID --password PASSWORD --tenant TENANT_ID
    ```

1. Buat grup sumber daya untuk menyimpan semua sumber daya yang digunakan untuk proyek pemula, tutorial, atau pengembangan yang sama.

    ```azurecli-interactive
    az group create --location WESTUS --name MY_RESOURCE_GROUP
    ```

1. Buat sumber daya ke layanan Azure. Ganti `<SERVICENAME>` dengan nama layanan Azure.

    Untuk Azure Storage, nilai yang valid untuk `<KIND>` parameter adalah:

    * BlobStorage
    * BlockBlobStorage
    * FileStorage
    * Penyimpanan
    * StorageV2

    ```azurecli-interactive
    az storage account create --name MY_RESOURCE_<SERVICENAME> --resource-group MY_RESOURCE_GROUP --kind <KIND> --sku F0 --location WESTUS --yes
    ```

1. Dapatkan kunci sumber daya untuk sumber daya baru, yang Anda gunakan dalam kode Anda untuk mengautentikasi ke layanan Azure.

    ```azurecli-interactive
    az storage account keys list --name MY_RESOURCE_<SERVICENAME> --resource-group MY_RESOURCE_GROUP
    ```

## <a name="reset-credentials"></a>Mengatur ulang info masuk

Jika Anda lupa kredensial untuk kepala layanan, gunakan [reset kredensial az ad sp.](/cli/azure/ad/sp/credential#az_ad_sp_credential_reset) Perintah reset mengambil argumen yang sama dengan `az ad sp create-for-rbac` .

```azurecli-interactive
az ad sp credential reset --name APP_ID
```

## <a name="see-also"></a>Lihat juga

* [Objek aplikasi dan perwakilan layanan di Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)
* [Cara mengelola prinsipal layanan](/azure/developer/python/how-to-manage-service-principals)

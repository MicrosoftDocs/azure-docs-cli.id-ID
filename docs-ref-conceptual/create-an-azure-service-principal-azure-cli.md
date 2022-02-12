---
title: Membuat prinsipal layanan Azure – Azure CLI | Microsoft Dokumen
description: Pelajari cara membuat dan menggunakan prinsipal layanan dengan Azure CLI. Gunakan prinsipal layanan untuk mendapatkan kontrol atas sumber daya Azure mana yang dapat diakses.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure service principal, create service principal azure, create service principal azure cli
ms.openlocfilehash: 28db4dfb19e7e07ef10960eaabe9db5d13004ba2
ms.sourcegitcommit: ad79327952adf0f8be8f1b9678e72434d9f03f0c
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/12/2022
ms.locfileid: "138526540"
---
# <a name="create-an-azure-service-principal-with-the-azure-cli"></a>Membuat perwakilan layanan Azure dengan Azure CLI

Alat otomatis yang menggunakan layanan Azure harus selalu memiliki izin terbatas. Alih-alih memiliki aplikasi masuk sebagai pengguna yang sepenuhnya istimewa, Azure menawarkan prinsipal layanan.

## <a name="what-is-an-azure-service-principal"></a>Apa itu prinsipal layanan Azure?

Prinsipal layanan Azure adalah identitas yang dibuat untuk digunakan dengan aplikasi, layanan yang dihosting, dan alat otomatis untuk mengakses sumber daya Azure. Akses ini dibatasi oleh peran yang ditetapkan untuk kepala layanan, memberi Anda kontrol atas sumber daya mana yang dapat diakses dan pada tingkat mana. Untuk alasan keamanan, selalu disarankan untuk menggunakan perwakilan layanan dengan alat otomatis dibanding mengizinkan mereka masuk dengan identitas pengguna.

Artikel ini menunjukkan kepada Anda langkah-langkah untuk membuat, mendapatkan informasi tentang, dan mengatur ulang prinsipal layanan Azure dengan Azure CLI.

## <a name="1-create-a-service-principal"></a>1. Membuat prinsipal layanan

Buat prinsipal layanan Azure dengan perintah [az ad sp create-for-rbac](/cli/azure/ad/sp#az_ad_sp_create_for_rbac) .

Tombol `appId` dan `tenant` muncul dalam output dan `az ad sp create-for-rbac` digunakan dalam otentikasi utama layanan. Catat nilainya, tetapi nilai dapat diambil kapan saja dengan [daftar az ad sp](/cli/azure/ad/sp#az-ad-sp-list).

Saat membuat prinsipal layanan, Anda memilih jenis autentikasi masuk yang digunakannya. Ada dua jenis autentikasi yang tersedia untuk prinsipal layanan Azure: autentikasi berbasis kata sandi, dan autentikasi berbasis sertifikat.

> [!NOTE]
>
> Jika akun Anda tidak memiliki izin untuk membuat pokok layanan, `az ad sp create-for-rbac` akan mengembalikan pesan kesalahan yang berisi "Hak istimewa yang tidak memadai untuk menyelesaikan operasi.". Hubungi admin Azure Active Directory Anda untuk membuat prinsipal layanan.

> [!WARNING]
> Saat Anda membuat prinsipal layanan Azure menggunakan `az ad sp create-for-rbac` perintah, output menyertakan kredensial yang harus Anda lindungi. Pastikan Anda tidak menyertakan kredensial ini dalam kode Anda atau memeriksa kredensial ke dalam kontrol sumber Anda. Sebagai alternatif, pertimbangkan untuk menggunakan [identitas terkelola](/azure/active-directory/managed-identities-azure-resources/overview) jika tersedia untuk menghindari kebutuhan untuk menggunakan kredensial.
>
> Sebaiknya gunakan `Contributor` untuk `--role` parameter minimal. Untuk mengurangi risiko prinsipal layanan yang disusupi, tetapkan peran yang lebih spesifik dan persempit ruang lingkup ke grup sumber daya atau sumber daya. Lihat [Langkah-langkah untuk menambahkan penetapan peran](/azure/role-based-access-control/role-assignments-steps) untuk informasi selengkapnya.


### <a name="password-based-authentication"></a>Autentikasi berbasis kata sandi

Tanpa parameter otentikasi, otentikasi berbasis kata sandi digunakan dengan kata sandi acak yang dibuat untuk Anda.

  ```azurecli-interactive
  az ad sp create-for-rbac --name ServicePrincipalName --role Contributor
  ```

> [!IMPORTANT]
> Pada Azure CLI 2.0.68, `--password` parameter untuk membuat prinsipal layanan dengan kata sandi yang ditentukan pengguna __tidak lagi didukung__ untuk mencegah penggunaan kata sandi lemah yang tidak disengaja.

Output untuk prinsipal layanan dengan otentikasi kata sandi menyertakan kunci.`password` __Pastikan__ Anda menyalin nilai ini - tidak dapat diambil. Jika Anda lupa kata sandi, [atur ulang info masuk perwakilan layanan](#6-reset-credentials).

### <a name="certificate-based-authentication"></a>Autentikasi berbasis sertifikat

Untuk autentikasi berbasis sertifikat, gunakan `--cert` argumen. Argumen ini mengharuskan Anda memegang sertifikat yang ada. Pastikan alat apa pun yang menggunakan prinsipal layanan ini memiliki akses ke kunci pribadi sertifikat. Sertifikat harus dalam format ASCII seperti PEM, CER, atau DER. Lulus sertifikat sebagai string, atau gunakan `@path` format untuk memuat sertifikat dari file.

> [!NOTE]
> Saat menggunakan file PEM, **SERTIFIKAT** harus ditambahkan ke **KUNCI PRIBADI** di dalam file.

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --role Contributor --cert "-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----"
```

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --role Contributor --cert @/path/to/cert.pem
```

Argumen `--keyvault` dapat ditambahkan untuk menggunakan sertifikat di Azure Key Vault. Dalam hal ini, `--cert` nilainya adalah nama sertifikat.

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --role Contributor --cert CertName --keyvault VaultName
```

Untuk membuat sertifikat _yang ditandatangani sendiri_ untuk autentikasi, gunakan `--create-cert` argumen:

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --role Contributor --create-cert
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

Isi file PEM baru:
```
-----BEGIN PRIVATE KEY-----
myPrivateKeyValue
-----END PRIVATE KEY-----
-----BEGIN CERTIFICATE-----
myCertificateValue
-----END CERTIFICATE-----
```

> [!NOTE]
> Perintah `az ad sp create-for-rbac --create-cert` membuat kepala layanan dan file PEM. File PEM berisi **KUNCI PRIBADI** dan **SERTIFIKAT** yang diformat dengan benar.

Argumen `--keyvault` dapat ditambahkan untuk menyimpan sertifikat di Azure Key Vault. Saat menggunakan `--keyvault`, `--cert` argumen __diperlukan__.

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --role Contributor --create-cert --cert CertName --keyvault VaultName
```

Kecuali Anda menyimpan sertifikat di Key Vault, output menyertakan kunci.`fileWithCertAndPrivateKey` Nilai kunci ini memberi tahu Anda di mana sertifikat yang dihasilkan disimpan.
__Pastikan__ Anda menyalin sertifikat ke lokasi yang aman, atau Anda tidak dapat masuk dengan prinsipal layanan ini.

Jika Anda kehilangan akses ke kunci pribadi sertifikat, [atur ulang kredensial utama layanan](#6-reset-credentials).

#### <a name="retrieve-certificate-from-key-vault"></a>Mengambil sertifikat dari Key Vault

Untuk sertifikat yang disimpan di Key Vault, ambil sertifikat dengan kunci pribadinya dengan [acara rahasia az keyvault](/cli/azure/keyvault/secret#az-keyvault-secret-show) dan konversi ke file PEM. Di Key Vault, nama rahasia sertifikat sama dengan nama sertifikat.

```azurecli-interactive
az keyvault secret download --file /path/to/cert.pfx --vault-name VaultName --name CertName --encoding base64
openssl pkcs12 -in cert.pfx -passin pass: -out cert.pem -nodes
```

## <a name="2-get-an-existing-service-principal"></a>2. Dapatkan prinsipal layanan yang ada

Daftar prinsipal layanan di penyewa dapat diambil dengan [daftar az ad sp](/cli/azure/ad/sp#az-ad-sp-list). Secara default perintah ini mengembalikan 100 prinsipal layanan pertama untuk penyewa Anda. Untuk mendapatkan semua prinsip layanan penyewa, gunakan `--all` argumen. Mendapatkan daftar ini bisa memakan waktu lama, jadi disarankan agar Anda memfilter daftar dengan salah satu argumen berikut:

* `--display-name` meminta prinsipal layanan yang memiliki _awalan_ yang sesuai dengan nama yang disediakan. Nama tampilan prinsipal layanan adalah nilai yang ditetapkan dengan `--name` parameter selama pembuatan. Jika Anda tidak mengatur `--name` selama pembuatan utama layanan, awalan nama adalah `azure-cli-`.
* `--spn` filter pada pencocokan nama utama layanan yang tepat. Nama utama layanan selalu dimulai dengan `https://`.
  jika nilai yang Anda gunakan `--name` bukan URI, nilai `https://` ini diikuti oleh nama tampilan.
* `--show-mine` hanya meminta prinsipal layanan yang dibuat oleh pengguna yang masuk.
* `--filter` mengambil filter OData, dan melakukan pemfilteran _sisi server_ . Metode ini direkomendasikan untuk memfilter sisi klien dengan argumen CLI `--query` . Untuk mempelajari tentang filter OData, lihat [sintaks ekspresi OData untuk filter](/rest/api/searchservice/odata-expression-syntax-for-azure-search).

Informasi yang dikembalikan untuk objek utama layanan adalah verbose. Untuk mendapatkan hanya informasi yang diperlukan untuk masuk, gunakan string `[].{id:appId, tenant:appOwnerTenantId}`kueri . Misalnya, untuk mendapatkan informasi masuk untuk semua prinsipal layanan yang dibuat oleh pengguna yang saat ini masuk:

```azurecli-interactive
az ad sp list --show-mine --query "[].{id:appId, tenant:appOwnerTenantId}"
```

> [!IMPORTANT]
>
> `az ad sp list` atau [az ad sp show](/cli/azure/ad/sp#az-ad-sp-show) dapatkan pengguna dan penyewa, tetapi bukan rahasia autentikasi _atau_ metode autentikasi.
> Rahasia untuk sertifikat di Key Vault dapat diambil dengan [acara rahasia az keyvault](/cli/azure/keyvault/secret#az-keyvault-secret-show), tetapi tidak ada rahasia lain yang disimpan secara default.
> Jika Anda lupa metode atau rahasia autentikasi, [atur ulang kredensial utama layanan](#6-reset-credentials).

## <a name="3-manage-service-principal-roles"></a>3. Mengelola peran utama layanan

Azure CLI memiliki perintah berikut untuk mengelola penetapan peran:

* [az role assignment list](/cli/azure/role/assignment#az-role-assignment-list)
* [pembuatan penetapan peran az](/cli/azure/role/assignment#az-role-assignment-create)
* [az role assignment delete](/cli/azure/role/assignment#az-role-assignment-delete)

Sebaiknya gunakan peran **Kontributor** minimal untuk prinsipal layanan. Peran ini memiliki izin penuh untuk membaca dan menulis ke akun Azure. Peran **Pembaca** lebih ketat, dengan akses baca-saja. Untuk informasi selengkapnya tentang kontrol akses Role-Based (RBAC) dan peran, lihat [RBAC: Peran bawaan](/azure/active-directory/role-based-access-built-in-roles).

Contoh ini menambahkan peran **Pembaca** dan menghapus **yang Kontributor** :

```azurecli-interactive
az role assignment create --assignee APP_ID --role Reader
az role assignment delete --assignee APP_ID --role Contributor
```

> [!NOTE]
> Jika akun Anda tidak memiliki izin untuk menetapkan peran, Anda akan melihat pesan kesalahan bahwa akun Anda "tidak memiliki otorisasi untuk melakukan tindakan 'Microsoft.Authorization/roleAssignments/write'." Hubungi admin Azure Active Directory Anda untuk mengelola peran.

Menambahkan peran _tidak_ membatasi izin yang ditetapkan sebelumnya. Saat membatasi izin prinsipal layanan, peran __Kontributor__ harus dihapus.

Perubahan dapat diverifikasi dengan mencantumkan peran yang ditetapkan:

```azurecli-interactive
az role assignment list --assignee APP_ID
```

## <a name="4-sign-in-using-a-service-principal"></a>4. Masuk menggunakan prinsipal layanan

Uji kredensial dan izin prinsipal layanan baru dengan masuk. Untuk masuk dengan prinsipal layanan, Anda memerlukan `appId`kredensial, `tenant`dan kredensial.

Untuk masuk dengan prinsipal layanan menggunakan kata sandi:

```azurecli-interactive
az login --service-principal --username APP_ID --password PASSWORD --tenant TENANT_ID
```

Untuk masuk dengan sertifikat, itu harus tersedia secara lokal sebagai file PEM atau DER, dalam format ASCII. Saat menggunakan file PEM, **KUNCI PRIBADI** dan **SERTIFIKAT** harus ditambahkan bersama-sama dalam file.

```azurecli-interactive
az login --service-principal --username APP_ID --tenant TENANT_ID --password /path/to/cert
```

Untuk mempelajari selengkapnya tentang masuk dengan prinsipal layanan, lihat [Masuk dengan Azure CLI](authenticate-azure-cli.md).

## <a name="5-create-a-resource-using-service-principal"></a>5. Membuat sumber daya menggunakan prinsipal layanan

Bagian berikut memberikan contoh cara membuat sumber daya untuk [Azure Storage](/azure/storage/) dengan prinsipal layanan, menggunakan perintah berikut:

* [az login](/cli/azure/reference-index#az-login)
* [az group create](/cli/azure/group#az-group-create)
* [az storage account create](/cli/azure/storage/account#az-storage-account-create)
* [daftar kunci akun penyimpanan az](/cli/azure/storage/account/keys#az-storage-account-keys-list)

Untuk masuk dengan prinsipal layanan, Anda memerlukan `appId`, `tenant`, dan `password` dikembalikan sebagai respons ketika Anda [membuat prinsip layanan Anda](#4-sign-in-using-a-service-principal).

1. Masuk sebagai prinsip layanan.

    ```azurecli-interactive
    az login --service-principal --username APP_ID --password PASSWORD --tenant TENANT_ID
    ```

1. Buat grup sumber daya untuk menyimpan semua sumber daya yang digunakan untuk proyek mulai cepat, tutorial, atau pengembangan yang sama.

    ```azurecli-interactive
    az group create --location WESTUS --name MY_RESOURCE_GROUP
    ```

1. Membuat sumber daya ke layanan Azure. Ganti `<SERVICENAME>` dengan nama layanan Azure.

    Untuk Azure Storage, nilai yang valid untuk parameter adalah`<KIND>`:

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

## <a name="6-reset-credentials"></a>6. Atur ulang kredensial

Jika Anda lupa kredensial untuk prinsipal layanan, gunakan [reset kredensial az ad sp](/cli/azure/ad/sp/credential#az-ad-sp-credential-reset). Perintah reset mengambil argumen yang sama seperti `az ad sp create-for-rbac`.

```azurecli-interactive
az ad sp credential reset --name APP_ID
```

## <a name="see-also"></a>Lihat juga

* [Objek aplikasi dan perwakilan layanan di Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)
* [Cara mengelola prinsipal layanan](/azure/developer/python/how-to-manage-service-principals)

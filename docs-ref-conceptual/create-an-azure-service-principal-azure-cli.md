---
title: Membuat perwakilan layanan Azure – Azure CLI | Microsoft Docs
description: Pelajari cara membuat dan menggunakan perwakilan layanan dengan Azure CLI. Gunakan perwakilan layanan untuk mendapatkan kontrol atas sumber daya Azure yang dapat diakses.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: perwakilan layanan azure, membuat perwakilan layanan azure, membuat perwakilan layanan azure cli
ms.openlocfilehash: 28db4dfb19e7e07ef10960eaabe9db5d13004ba2
ms.sourcegitcommit: ad79327952adf0f8be8f1b9678e72434d9f03f0c
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 02/12/2022
ms.locfileid: "138526540"
---
# <a name="create-an-azure-service-principal-with-the-azure-cli"></a>Membuat perwakilan layanan Azure dengan Azure CLI

Alat otomatis yang menggunakan layanan Azure harus selalu memiliki izin terbatas. Sebagai alternatif membuat aplikasi masuk sebagai pengguna dengan hak istimewa penuh, Azure menawarkan perwakilan layanan.

## <a name="what-is-an-azure-service-principal"></a>Apa itu perwakilan layanan Azure?

Perwakilan layanan Azure adalah identitas yang dibuat untuk digunakan dengan aplikasi, layanan yang dihosting, dan alat otomatis untuk mengakses sumber daya Azure. Akses ini dibatasi oleh peran yang ditetapkan untuk perwakilan layanan, yang memberi Anda kontrol atas sumber daya mana yang dapat diakses dan pada tingkat mana. Untuk alasan keamanan, selalu disarankan untuk menggunakan perwakilan layanan dengan alat otomatis dibanding mengizinkan mereka masuk dengan identitas pengguna.

Artikel ini berisi langkah-langkah untuk membuat, mendapatkan informasi tentang, dan mengatur ulang perwakilan layanan Azure dengan Azure CLI.

## <a name="1-create-a-service-principal"></a>1. Buat perwakilan layanan

Buat perwakilan layanan Azure dengan perintah [az ad sp create-for-rbac](/cli/azure/ad/sp#az_ad_sp_create_for_rbac).

Kunci `appId` dan `tenant` muncul dalam output `az ad sp create-for-rbac` dan digunakan dalam autentikasi perwakilan layanan. Catat nilainya, tetapi nilai dapat diambil kapan saja dengan [daftar az ad sp](/cli/azure/ad/sp#az-ad-sp-list).

Saat membuat perwakilan layanan, pilih jenis autentikasi masuk yang digunakannya. Ada dua jenis autentikasi yang tersedia untuk perwakilan layanan Azure: autentikasi berbasis kata sandi dan autentikasi berbasis sertifikat.

> [!NOTE]
>
> Jika akun Anda tidak memiliki izin untuk membuat perwakilan layanan, `az ad sp create-for-rbac` akan menampilkan pesan kesalahan yang berisi "Hak istimewa tidak memadai untuk menyelesaikan operasi." Hubungi admin Azure Active Directory Anda untuk membuat perwakilan layanan.

> [!WARNING]
> Saat Anda membuat perwakilan layanan Azure menggunakan perintah `az ad sp create-for-rbac`, output akan menyertakan info masuk yang harus dilindungi. Pastikan Anda tidak menyertakan info masuk ini dalam kode atau memasukkan info masuk ke dalam kontrol sumber Anda. Sebagai alternatif, pertimbangkan untuk menggunakan [identitas terkelola](/azure/active-directory/managed-identities-azure-resources/overview) jika tersedia untuk mencegah penggunaan info masuk.
>
> Sebaiknya gunakan setidaknya `Contributor` untuk parameter `--role`. Untuk mengurangi risiko perwakilan layanan disusupi, tetapkan peran yang lebih spesifik dan persempit cakupan ke sumber daya atau grup sumber daya. Untuk informasi selengkapnya, lihat [Langkah-langkah untuk menambahkan penetapan peran](/azure/role-based-access-control/role-assignments-steps).


### <a name="password-based-authentication"></a>Autentikasi berbasis kata sandi

Tanpa parameter autentikasi, autentikasi berbasis kata sandi digunakan dengan kata sandi acak yang dibuat untuk Anda.

  ```azurecli-interactive
  az ad sp create-for-rbac --name ServicePrincipalName --role Contributor
  ```

> [!IMPORTANT]
> Sejak Azure CLI 2.0.68, parameter `--password` untuk membuat perwakilan layanan dengan kata sandi yang ditentukan pengguna __tidak lagi didukung__ untuk mencegah penggunaan kata sandi lemah yang tidak disengaja.

Output perwakilan layanan dengan autentikasi kata sandi menyertakan kunci `password`. __Pastikan__ Anda menyalin nilai ini - tidak dapat diambil kembali. Jika Anda lupa kata sandi, [atur ulang info masuk perwakilan layanan](#6-reset-credentials).

### <a name="certificate-based-authentication"></a>Autentikasi berbasis sertifikat

Untuk autentikasi berbasis sertifikat, gunakan argumen `--cert`. Argumen ini mengharuskan Anda memiliki sertifikat yang ada. Pastikan alat apa pun yang menggunakan perwakilan layanan ini memiliki akses ke kunci privat sertifikat. Sertifikat harus dalam format ASCII seperti PEM, CER, atau DER. Teruskan sertifikat sebagai string, atau gunakan format `@path` untuk memuat sertifikat dari file.

> [!NOTE]
> Saat menggunakan file PEM, **CERTIFICATE** harus ditambahkan ke **PRIVATE KEY** di dalam file.

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --role Contributor --cert "-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----"
```

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --role Contributor --cert @/path/to/cert.pem
```

Argumen `--keyvault` dapat ditambahkan untuk menggunakan sertifikat di Azure Key Vault. Dalam hal ini, nilai `--cert` adalah nama sertifikat.

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --role Contributor --cert CertName --keyvault VaultName
```

Untuk membuat sertifikat yang _ditandatangani sendiri_ untuk autentikasi, gunakan argumen `--create-cert`:

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
> Perintah `az ad sp create-for-rbac --create-cert` membuat perwakilan layanan dan file PEM. File PEM berisi **PRIVATE KEY** dan **CERTIFICATE** diformat dengan benar.

Argumen `--keyvault` dapat ditambahkan untuk menyimpan sertifikat di Azure Key Vault. Saat menggunakan `--keyvault`, argumen `--cert` __diperlukan__.

```azurecli-interactive
az ad sp create-for-rbac --name ServicePrincipalName --role Contributor --create-cert --cert CertName --keyvault VaultName
```

Jika sertifikat tidak disimpan di Key Vault, output tidak akan menyertakan kunci `fileWithCertAndPrivateKey`. Nilai kunci ini memberi tahu Anda lokasi penyimpanan sertifikat yang dihasilkan.
__Pastikan__ Anda menyalin sertifikat ke lokasi yang aman, atau Anda tidak dapat masuk dengan perwakilan layanan ini.

Jika Anda kehilangan akses ke kunci privat sertifikat, [atur ulang info masuk perwakilan layanan](#6-reset-credentials).

#### <a name="retrieve-certificate-from-key-vault"></a>Mengambil sertifikat dari Key Vault

Untuk sertifikat yang disimpan di Key Vault, ambil sertifikat dengan kunci privatnya dengan [az keyvault secret show](/cli/azure/keyvault/secret#az-keyvault-secret-show) dan konversi menjadi file PEM. Di Key Vault, nama rahasia sertifikat sama dengan nama sertifikat.

```azurecli-interactive
az keyvault secret download --file /path/to/cert.pfx --vault-name VaultName --name CertName --encoding base64
openssl pkcs12 -in cert.pfx -passin pass: -out cert.pem -nodes
```

## <a name="2-get-an-existing-service-principal"></a>2. Dapatkan perwakilan layanan yang ada

Daftar perwakilan layanan di penyewa dapat diambil dengan [az ad sp list](/cli/azure/ad/sp#az-ad-sp-list). Secara default, perintah ini menampilkan 100 perwakilan layanan pertama untuk penyewa Anda. Untuk mendapatkan semua perwakilan layanan penyewa, gunakan argumen `--all`. Diperlukan waktu yang lama untuk mengambil daftar ini, jadi sebaiknya Anda memfilter daftar dengan salah satu argumen berikut:

* `--display-name` meminta perwakilan layanan yang memiliki _awalan_ yang sesuai dengan nama yang disediakan. Nama tampilan perwakilan layanan adalah nilai yang ditetapkan dengan parameter `--name` selama pembuatan. Jika Anda tidak mengatur `--name` selama pembuatan perwakilan layanan, awalan namanya adalah `azure-cli-`.
* `--spn` memfilter dengan pencocokan persis nama perwakilan layanan. Nama perwakilan layanan selalu dimulai dengan `https://`.
  jika nilai yang digunakan untuk `--name` bukan URI, nilai ini adalah `https://` diikuti oleh nama tampilan.
* `--show-mine` hanya meminta perwakilan layanan yang dibuat oleh pengguna yang masuk.
* `--filter` mengambil filter OData, dan melakukan pemfilteran _sisi server_. Metode ini direkomendasikan dalam pemfilteran sisi klien dengan argumen `--query` CLI. Untuk mempelajari filter OData, lihat [Sintaks ekspresi OData untuk filter](/rest/api/searchservice/odata-expression-syntax-for-azure-search).

Informasi yang ditampilkan untuk objek perwakilan layanan bersifat verbose. Untuk mendapatkan informasi yang diperlukan untuk masuk saja, gunakan string kueri `[].{id:appId, tenant:appOwnerTenantId}`. Misalnya, untuk mendapatkan informasi masuk untuk semua perwakilan layanan yang dibuat oleh pengguna yang saat ini masuk:

```azurecli-interactive
az ad sp list --show-mine --query "[].{id:appId, tenant:appOwnerTenantId}"
```

> [!IMPORTANT]
>
> `az ad sp list` atau [az ad sp show](/cli/azure/ad/sp#az-ad-sp-show) mendapatkan pengguna dan penyewa, tapi bukan rahasia autentikasi _maupun_ metode autentikasi.
> Rahasia untuk sertifikat di Key Vault dapat diambil dengan [az keyvault secret show](/cli/azure/keyvault/secret#az-keyvault-secret-show), tapi rahasia lainnya tidak disimpan secara default.
> Jika Anda lupa metode atau rahasia autentikasi, [atur ulang info masuk perwakilan layanan](#6-reset-credentials).

## <a name="3-manage-service-principal-roles"></a>3. Kelola peran perwakilan layanan

Azure CLI memiliki perintah berikut untuk mengelola penetapan peran:

* [az role assignment list](/cli/azure/role/assignment#az-role-assignment-list)
* [pembuatan penetapan peran az](/cli/azure/role/assignment#az-role-assignment-create)
* [az role assignment delete](/cli/azure/role/assignment#az-role-assignment-delete)

Sebaiknya gunakan setidaknya peran **Kontributor** untuk perwakilan layanan. Peran ini memiliki izin penuh untuk membaca dan menulis ke akun Azure. Peran **Pembaca** lebih ketat, dengan akses baca-saja. Untuk informasi selengkapnya tentang Kontrol Akses Berbasis Peran (RBAC) dan peran, lihat [RBAC: Peran bawaan](/azure/active-directory/role-based-access-built-in-roles).

Contoh ini menambahkan peran **Pembaca** dan menghapus peran **Kontributor**:

```azurecli-interactive
az role assignment create --assignee APP_ID --role Reader
az role assignment delete --assignee APP_ID --role Contributor
```

> [!NOTE]
> Jika akun Anda tidak memiliki izin untuk menetapkan peran, Anda akan melihat pesan kesalahan bahwa akun Anda "tidak memiliki otorisasi untuk melakukan tindakan 'Microsoft.Authorization/roleAssignments/write'." Hubungi admin Azure Active Directory Anda untuk mengelola peran.

Penambahan peran _tidak_ membatasi izin yang ditetapkan sebelumnya. Jika izin perwakilan layanan dibatasi, peran __Kontributor__ akan dihapus.

Perubahan ini dapat diverifikasi dengan mencantumkan peran yang ditetapkan:

```azurecli-interactive
az role assignment list --assignee APP_ID
```

## <a name="4-sign-in-using-a-service-principal"></a>4. Masuk menggunakan perwakilan layanan

Uji info masuk dan izin perwakilan layanan baru dengan masuk. Untuk masuk dengan perwakilan layanan, Anda memerlukan `appId`, `tenant`, dan info masuk.

Untuk masuk dengan perwakilan layanan menggunakan kata sandi:

```azurecli-interactive
az login --service-principal --username APP_ID --password PASSWORD --tenant TENANT_ID
```

Untuk masuk dengan sertifikat, ini harus tersedia secara lokal sebagai file PEM atau DER, dalam format ASCII. Jika menggunakan file PEM, **PRIVATE KEY** dan **CERTIFICATE** harus ditambahkan sekaligus di dalam file.

```azurecli-interactive
az login --service-principal --username APP_ID --tenant TENANT_ID --password /path/to/cert
```

Untuk mempelajari lebih lanjut cara masuk dengan perwakilan layanan, lihat [Masuk dengan Azure CLI](authenticate-azure-cli.md).

## <a name="5-create-a-resource-using-service-principal"></a>5. Buat sumber daya menggunakan perwakilan layanan

Bagian berikut berisi contoh cara membuat sumber daya untuk [Azure Storage](/azure/storage/) dengan perwakilan layanan, menggunakan perintah berikut:

* [az login](/cli/azure/reference-index#az-login)
* [az group membuat](/cli/azure/group#az-group-create)
* [az storage account create](/cli/azure/storage/account#az-storage-account-create)
* [daftar kunci akun penyimpanan az](/cli/azure/storage/account/keys#az-storage-account-keys-list)

Untuk masuk dengan perwakilan layanan, Anda memerlukan `appId`, `tenant`, dan `password` ditampilkan sebagai respons saat Anda [membuat perwakilan layanan](#4-sign-in-using-a-service-principal).

1. Masuk sebagai perwakilan layanan.

    ```azurecli-interactive
    az login --service-principal --username APP_ID --password PASSWORD --tenant TENANT_ID
    ```

1. Buat grup sumber daya untuk menyimpan semua sumber daya yang digunakan untuk proyek mulai cepat, tutorial, atau pengembangan yang sama.

    ```azurecli-interactive
    az group create --location WESTUS --name MY_RESOURCE_GROUP
    ```

1. Buat sumber daya ke layanan Azure. Ganti `<SERVICENAME>` dengan nama layanan Azure.

    Untuk Azure Storage, nilai yang valid untuk parameter `<KIND>` adalah:

    * BlobStorage
    * BlockBlobStorage
    * FileStorage
    * Penyimpanan
    * StorageV2

    ```azurecli-interactive
    az storage account create --name MY_RESOURCE_<SERVICENAME> --resource-group MY_RESOURCE_GROUP --kind <KIND> --sku F0 --location WESTUS --yes
    ```

1. Dapatkan kunci sumber daya untuk sumber daya baru, yang Anda gunakan dalam kode untuk melakukan autentikasi ke layanan Azure.

    ```azurecli-interactive
    az storage account keys list --name MY_RESOURCE_<SERVICENAME> --resource-group MY_RESOURCE_GROUP
    ```

## <a name="6-reset-credentials"></a>6. Atur ulang info masuk

Jika Anda lupa kredensial untuk perwakilan layanan, gunakan [az ad sp credential reset](/cli/azure/ad/sp/credential#az-ad-sp-credential-reset). Perintah reset menggunakan argumen yang sama dengan `az ad sp create-for-rbac`.

```azurecli-interactive
az ad sp credential reset --name APP_ID
```

## <a name="see-also"></a>Lihat juga

* [Objek aplikasi dan perwakilan layanan di Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)
* [Cara mengelola perwakilan layanan](/azure/developer/python/how-to-manage-service-principals)

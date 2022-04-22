---
title: Membuat perwakilan layanan Azure – Azure CLI | Microsoft Docs
description: Pelajari cara membuat dan menggunakan perwakilan layanan dengan Azure CLI. Gunakan perwakilan layanan untuk mendapatkan kontrol atas sumber daya Azure yang dapat diakses.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 03/01/2022
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: perwakilan layanan azure, membuat perwakilan layanan azure, membuat perwakilan layanan azure cli
ms.openlocfilehash: 4c1a3b9e79ece52c274a36c5403dd1e619b1bc2c
ms.sourcegitcommit: a805041ebd77f92fa4b3025ba6856ea4aedae2ac
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/22/2022
ms.locfileid: "144003229"
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

> [!WARNING]
> Saat Anda membuat perwakilan layanan Azure menggunakan perintah `az ad sp create-for-rbac`, output akan menyertakan info masuk yang harus dilindungi. Pastikan Anda tidak menyertakan info masuk ini dalam kode atau memasukkan info masuk ke dalam kontrol sumber Anda. Sebagai alternatif, pertimbangkan untuk menggunakan [identitas terkelola](/azure/active-directory/managed-identities-azure-resources/overview) jika tersedia untuk mencegah penggunaan info masuk.
>
> Untuk mengurangi risiko perwakilan layanan yang disusupi, tetapkan peran yang lebih spesifik dan persempit cakupan ke sumber daya atau grup sumber daya. Untuk informasi selengkapnya, lihat [Langkah-langkah untuk menambahkan penetapan peran](/azure/role-based-access-control/role-assignments-steps).


### <a name="password-based-authentication"></a>Autentikasi berbasis kata sandi

Dengan autentikasi berbasis kata sandi, kata sandi acak dibuat untuk Anda.  Jika Anda tidak menentukan `--name` nilai parameter, nama yang berisi stempel waktu akan dibuat untuk Anda.  Anda harus menentukan sebagai `--scopes` nilai ini tidak memiliki default.  Jika mau, Anda dapat mengatur penetapan peran nanti dengan menggunakan [az role assignment create](/cli/azure/role/assignment#az-role-assignment-create).

```azurecli-interactive
# Create a service principal with required parameter
az ad sp create-for-rbac --scopes /subscriptions/mySubscriptionID

# Create a service principal for a resource group using a preferred name and role
az ad sp create-for-rbac --name myServicePrincipalName \
                         --role reader \
                         --scopes /subscriptions/mySubscriptionID/resourceGroups/myResourceGroupName
```

Anda juga dapat membuat perwakilan layanan menggunakan variabel.

```azurecli-interactive
let "randomIdentifier=$RANDOM*$RANDOM"  
servicePrincipalName="msdocs-sp-$randomIdentifier"
roleName="azureRoleName"
subscriptionID=$(az account show --query id -o tsv)
# Verify the ID of the active subscription
echo "Using subscription ID $subscriptionID"
resourceGroup="myResourceGroupName"

echo "Creating SP for RBAC with name $servicePrincipalName, with role $roleName and in scopes /subscriptions/$subscriptionID/resourceGroups/$resourceGroup"
az ad sp create-for-rbac --name $servicePrincipalName --role $roleName --scopes /subscriptions/$subscriptionID/resourceGroups/$resourceGroup
```

Output perwakilan layanan dengan autentikasi kata sandi menyertakan kunci `password`. __Pastikan Anda menyalin nilai ini - nilai__ tersebut tidak dapat diambil. Jika lupa kata sandi, [atur ulang info masuk perwakilan layanan](#6-reset-credentials).

### <a name="certificate-based-authentication"></a>Autentikasi berbasis sertifikat

Untuk autentikasi berbasis sertifikat, gunakan `--cert` parameter . Parameter ini mengharuskan Anda memegang sertifikat yang sudah ada. Pastikan alat apa pun yang menggunakan perwakilan layanan ini memiliki akses ke kunci privat sertifikat. Sertifikat harus dalam format ASCII seperti PEM, CER, atau DER. Teruskan sertifikat sebagai string, atau gunakan format `@path` untuk memuat sertifikat dari file.

> [!NOTE]
> Saat menggunakan file PEM, **CERTIFICATE** harus ditambahkan ke **PRIVATE KEY** di dalam file.

```azurecli-interactive
az ad sp create-for-rbac --name myServicePrincipalName \
                         --role roleName \
                         --scopes /subscriptions/mySubscriptionID/resourceGroups/myResourceGroupName \
                         --cert "-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----"
```

```azurecli-interactive
az ad sp create-for-rbac --name myServicePrincipalName \
                         --role roleName \
                         --scopes /subscriptions/mySubscriptionID/resourceGroups/myResourceGroupName \
                         --cert @/path/to/cert.pem
```

Parameter `--keyvault` dapat ditambahkan untuk menggunakan sertifikat di Azure Key Vault. Dalam hal ini, nilai `--cert` adalah nama sertifikat.

```azurecli-interactive
az ad sp create-for-rbac --name myServicePrincipalName \
                         --role roleName \
                         --scopes /subscriptions/mySubscriptionID/resourceGroups/myResourceGroupName \
                         --cert certificateName \
                         --keyvault vaultName
```

Untuk membuat sertifikat yang _ditandatangani sendiri_ untuk autentikasi, gunakan `--create-cert` parameter :

```azurecli-interactive
az ad sp create-for-rbac --name myServicePrincipalName \
                         --role roleName \
                         --scopes /subscriptions/mySubscriptionID/resourceGroups/myResourceGroupName \
                         --create-cert
```

Output konsol:

```
Creating a role assignment under the scopes of "/subscriptions/myId"
Please copy C:\myPath\myNewFile.pem to a safe place.
When you run 'az login', provide the file path in the --password parameter
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

Parameter `--keyvault` dapat ditambahkan untuk menyimpan sertifikat di Azure Key Vault. Saat menggunakan `--keyvault`, `--cert` parameter __diperlukan__.

```azurecli-interactive
az ad sp create-for-rbac --name myServicePrincipalName \
                         --role roleName \
                         --scopes /subscriptions/mySubscriptionID/resourceGroups/myResourceGroupName \
                         --create-cert \
                         --cert certificateName \
                         --keyvault vaultName
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

Daftar perwakilan layanan di penyewa dapat diambil dengan [az ad sp list](/cli/azure/ad/sp#az-ad-sp-list). Secara default, perintah ini menampilkan 100 perwakilan layanan pertama untuk penyewa Anda. Untuk mendapatkan semua perwakilan layanan penyewa, gunakan `--all` parameter . Mendapatkan daftar ini bisa memakan waktu lama, jadi disarankan agar Anda memfilter daftar dengan salah satu parameter berikut:

* `--display-name` meminta perwakilan layanan yang memiliki _awalan_ yang sesuai dengan nama yang disediakan. Nama tampilan perwakilan layanan adalah nilai yang ditetapkan dengan parameter `--name` selama pembuatan. Jika Anda tidak mengatur `--name` selama pembuatan perwakilan layanan, awalan namanya adalah `azure-cli-`.
* `--spn` memfilter dengan pencocokan persis nama perwakilan layanan. Nama perwakilan layanan selalu dimulai dengan `https://`.
  jika nilai yang digunakan untuk `--name` bukan URI, nilai ini adalah `https://` diikuti oleh nama tampilan.
* `--show-mine` hanya meminta perwakilan layanan yang dibuat oleh pengguna yang masuk.
* `--filter` mengambil filter OData, dan melakukan pemfilteran _sisi server_. Metode ini direkomendasikan daripada memfilter sisi klien dengan parameter CLI `--query` . Untuk mempelajari filter OData, lihat [Sintaks ekspresi OData untuk filter](/rest/api/searchservice/odata-expression-syntax-for-azure-search).

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

Peran **Kontributor** memiliki izin penuh untuk membaca dan menulis ke akun Azure. Peran **Pembaca** lebih ketat, dengan akses baca-saja. Untuk informasi selengkapnya tentang Kontrol Akses Berbasis Peran (RBAC) dan peran, lihat [RBAC: Peran bawaan](/azure/active-directory/role-based-access-built-in-roles).

Contoh ini menambahkan peran **Pembaca** dan menghapus peran **Kontributor** :

```azurecli-interactive
az role assignment create --assignee appID \
                          --role Reader \
                          --scope /subscriptions/mySubscriptionID/resourceGroups/myResourceGroupName

az role assignment delete --assignee appID \
                          --role Contributor \
                          --scope /subscriptions/mySubscriptionID/resourceGroups/myResourceGroupName
```

Penambahan peran _tidak_ membatasi izin yang ditetapkan sebelumnya. Saat membatasi izin perwakilan layanan, peran __Kontributor__ harus dihapus jika sebelumnya ditetapkan.

Perubahan ini dapat diverifikasi dengan mencantumkan peran yang ditetapkan:

```azurecli-interactive
az role assignment list --assignee appID
```

## <a name="4-sign-in-using-a-service-principal"></a>4. Masuk menggunakan perwakilan layanan

Uji info masuk dan izin perwakilan layanan baru dengan masuk. Untuk masuk dengan perwakilan layanan, Anda memerlukan `appId`, `tenant`, dan info masuk.

Untuk masuk dengan perwakilan layanan menggunakan kata sandi:

```azurecli-interactive
az login --service-principal --username appID --password PASSWORD --tenant tenantID
```

Untuk masuk dengan sertifikat, ini harus tersedia secara lokal sebagai file PEM atau DER, dalam format ASCII. Jika menggunakan file PEM, **PRIVATE KEY** dan **CERTIFICATE** harus ditambahkan sekaligus di dalam file.

```azurecli-interactive
az login --service-principal --username appID --tenant tenantID --password /path/to/cert
```

Untuk mempelajari lebih lanjut cara masuk dengan perwakilan layanan, lihat [Masuk dengan Azure CLI](authenticate-azure-cli.md).

## <a name="5-create-a-resource-using-service-principal"></a>5. Buat sumber daya menggunakan perwakilan layanan

Bagian berikut berisi contoh cara membuat sumber daya untuk [Azure Storage](/azure/storage/) dengan perwakilan layanan, menggunakan perintah berikut:

* [az login](/cli/azure/reference-index#az-login)
* [az group membuat](/cli/azure/group#az-group-create)
* [az storage account create](/cli/azure/storage/account#az-storage-account-create)
* [daftar kunci akun penyimpanan az](/cli/azure/storage/account/keys#az-storage-account-keys-list)

Untuk masuk dengan perwakilan layanan, Anda memerlukan `appID`, `tenantID`, dan `password` ditampilkan sebagai respons saat Anda [membuat perwakilan layanan](#1-create-a-service-principal).

1. Masuk sebagai perwakilan layanan.

    ```azurecli-interactive
    az login --service-principal --username appID --password PASSWORD --tenant tenantID
    ```

1. Buat grup sumber daya untuk menyimpan semua sumber daya yang digunakan untuk proyek mulai cepat, tutorial, atau pengembangan yang sama.

    ```azurecli-interactive
    az group create --location westus --name myResourceGroupName
    ```

1. Membuat akun penyimpanan.

    Untuk Azure Storage, nilai yang valid untuk parameter `<KIND>` adalah:

    * BlobStorage
    * BlockBlobStorage
    * FileStorage
    * Penyimpanan
    * StorageV2

    ```azurecli-interactive
    az storage account create --name myStorageAccountName --resource-group myResourceGroupName --kind <KIND> --sku F0 --location westus --yes
    ```

1. Dapatkan kunci sumber daya, yang Anda gunakan dalam kode Anda untuk mengautentikasi ke akun penyimpanan Azure.

    ```azurecli-interactive
    az storage account keys list --name myStorageAccountName --resource-group myResourceGroupName
    ```

## <a name="6-reset-credentials"></a>6. Atur ulang info masuk

Jika Anda kehilangan kredensial untuk perwakilan layanan, gunakan [az ad sp credential reset](/cli/azure/ad/sp/credential#az-ad-sp-credential-reset). Perintah reset mengambil parameter yang sama dengan `az ad sp create-for-rbac`.

```azurecli-interactive
az ad sp credential reset --name myServicePrincipal_appID_or_name
```

## <a name="7-troubleshooting"></a>7. Pemecahan masalah

### <a name="insufficient-privileges"></a>Hak istimewa tidak memadai
Jika akun Anda tidak memiliki izin untuk membuat perwakilan layanan, `az ad sp create-for-rbac` akan menampilkan pesan kesalahan yang berisi "Hak istimewa tidak memadai untuk menyelesaikan operasi." Hubungi admin Azure Active Directory Anda untuk membuat perwakilan layanan.

### <a name="invalid-tenant"></a>Penyewa tidak valid
Jika Anda telah menentukan ID langganan yang tidak valid, Anda akan melihat pesan kesalahan "Permintaan tidak memiliki langganan atau penyedia sumber daya tingkat penyewa yang valid."  Jika menggunakan variabel, gunakan perintah Bash `echo` untuk melihat nilai yang diteruskan ke perintah referensi.  Gunakan [az account set](/cli/azure/account#az-account-set) untuk mengubah langganan Anda atau pelajari [Cara mengelola langganan Azure dengan Azure CLI](./manage-azure-subscriptions-azure-cli.md).

### <a name="resource-group-not-found"></a>Grup sumber daya tidak ditemukan
Jika Anda telah menentukan nama grup sumber daya yang tidak valid, Anda akan melihat pesan kesalahan "Grup sumber daya 'nama' tidak dapat ditemukan."  Jika menggunakan variabel, gunakan perintah Bash `echo` untuk melihat nilai yang diteruskan ke perintah langganan dan referensi.  Gunakan [az group list](/cli/azure/group#az-group-list) untuk melihat grup sumber daya untuk langganan saat ini, atau pelajari [Cara mengelola grup sumber daya Azure dengan Azure CLI](./manage-azure-groups-azure-cli.md).

### <a name="authorization-to-perform-action"></a>Otorisasi untuk melakukan tindakan
Jika akun Anda tidak memiliki izin untuk menetapkan peran, Anda akan melihat pesan kesalahan bahwa akun Anda "tidak memiliki otorisasi untuk melakukan tindakan 'Microsoft.Authorization/roleAssignments/write'." Hubungi admin Azure Active Directory Anda untuk mengelola peran.

## <a name="see-also"></a>Lihat juga

* [Objek aplikasi dan perwakilan layanan di Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)
* [Cara mengelola perwakilan layanan](/azure/developer/python/how-to-manage-service-principals)
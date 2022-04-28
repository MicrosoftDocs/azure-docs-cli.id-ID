---
title: Cara mempelajari Bash dengan Azure CLI | Microsoft Docs
description: Pelajari cara menggunakan Bash dengan Azure CLI.  Kueri, format output, filter, gunakan variabel, dan gunakan konstruksi Bash dari perulangan, jika/ada/lalu dan pernyataan kasus.
author: dbradish-microsoft
ms.author: dbradish
ms.prod: non-product-specific
ms.topic: sample
ms.date: 04/18/2022
ms.openlocfilehash: 0247b3c3bd5c79df7eba0c85f243f01e4f7b27c3
ms.sourcegitcommit: 1b372058d7da922e1d119ddd551ce2cc7c579f46
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/27/2022
ms.locfileid: "144038875"
---
# <a name="learn-to-use-bash-with-the-azure-cli"></a>Pelajari cara menggunakan Bash dengan Azure CLI

Perintah referensi Azure CLI dapat dijalankan di beberapa [lingkungan shell](choose-the-right-azure-command-line-tool.md#different-shell-environments) yang berbeda, tetapi Microsoft Docs terutama menggunakan lingkungan Bash. Jika Anda baru menggunakan Bash dan juga Azure CLI, Anda akan menemukan artikel ini tempat yang bagus untuk memulai perjalanan pembelajaran Anda.  Bekerja melalui artikel ini seperti yang Anda lakukan tutorial, dan Anda akan segera menggunakan Azure CLI di lingkungan Bash dengan mudah.

Dalam artikel ini, Anda akan mempelajari cara melakukan hal berikut:

> [!div class="checklist"]
>
> - Hasil kueri sebagai kamus atau array JSON
> - Format output sebagai JSON, tabel, atau TSV
> - Mengkueri, memfilter, dan memformat satu dan beberapa nilai
> - Gunakan if/exists/then dan sintaks huruf besar/kecil
> - Gunakan untuk perulangan
> - Gunakan perintah grep, sed, paste, dan bc
> - Mengisi dan menggunakan variabel shell dan lingkungan

Jika Anda tidak memiliki langganan Azure, buat [akun gratis Azure](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio) sebelum memulai.

## <a name="starting-bash"></a>Memulai Bash

Mulai Bash menggunakan [Azure Cloud Shell](/azure/cloud-shell/quickstart) atau [penginstalan lokal Azure CLI](./install-azure-cli.md). Artikel ini mengasumsikan bahwa Anda menjalankan Bash baik menggunakan Azure Cloud Shell atau menjalankan Azure CLI secara lokal dalam kontainer docker.

## <a name="querying-dictionary-results"></a>Mengkueri hasil kamus

Perintah yang selalu mengembalikan hanya satu objek yang mengembalikan kamus JSON. Kamus adalah objek yang tidak berurut yang diakses dengan kunci. Untuk artikel ini, kita akan mulai dengan mengkueri objek [Akun](/cli/azure/account) menggunakan perintah [Perlihatkan Akun](/cli/azure/account#az-account-show) .

```azurecli-interactive
az account show
az account show --output json # JSON is the default format
```

Output kamus JSON berikut memiliki beberapa bidang yang dihilangkan untuk keringkasan, dan mengidentifikasi informasi telah dihapus atau di generikasi.

```JSON
bash-5.1# az account show
{
  "environmentName": "AzureCloud",
  "isDefault": true,
  "managedByTenants": [],
  "name": "My test subscription",
  "state": "Enabled",
  "user": {
    "name": "user@contoso.com",
    "type": "user"
  }
}
```

### <a name="formatting-the-output-as-yaml"></a>Memformat output sebagai YAML

`--output yaml` Gunakan argumen (atau `-o yaml`) untuk memformat output dalam format [yaml](https://yaml.org/), format serialisasi data teks biasa. YAML cenderung lebih mudah dibaca daripada JSON, dan dipetakan dengan mudah ke format tersebut. Beberapa aplikasi dan perintah CLI menggunakan YAML sebagai input konfigurasi, bukan JSON.

```azurecli-interactive
az account show --output yaml
```

Untuk informasi selengkapnya tentang memformat output sebagai yaml, lihat [format output YAML](./format-output-azure-cli.md#yaml-output-format).

### <a name="formatting-the-output-as-a-table"></a>Memformat output sebagai tabel

`--output table` Gunakan argumen (atau `-o table`) untuk memformat output sebagai tabel ASCII. Objek bersarang tidak disertakan dalam output tabel, namun masih dapat difilter sebagai bagian dari kueri.

```azurecli-interactive
az account show --output table
```

Untuk informasi selengkapnya tentang memformat output sebagai tabel, lihat [Format output](./format-output-azure-cli.md#table-output-format) tabel.

### <a name="querying-and-formatting-single-values-and-nested-values"></a>Mengkueri dan memformat nilai tunggal dan nilai berlapis

Kueri berikut menunjukkan kueri nilai tunggal, termasuk nilai berlapis dalam output kamus JSON. Kueri akhir dalam set ini menunjukkan pemformatan output menggunakan `-o tsv` argumen . Argumen ini mengembalikan hasil sebagai nilai yang dipisahkan tab dan baris baru. Ini berguna untuk menghapus tanda kutip dalam nilai yang dikembalikan - yang berguna untuk menggunakan output ke perintah dan alat lain yang perlu memproses teks dalam beberapa bentuk (seperti yang akan kami tunjukkan nanti di artikel ini).

```azurecli-interactive
az account show --query name # Querying a single value
az account show --query name -o tsv # Removes quotation marks from the output

az account show --query user.name # Querying a nested value
az account show --query user.name -o tsv # Removes quotation marks from the output
```

### <a name="querying-and-formatting-multiple-values-including-nested-values"></a>Mengkueri dan memformat beberapa nilai, termasuk nilai berlapis

Untuk mendapatkan lebih dari satu properti, letakkan ekspresi dalam kurung siku [ ] (daftar multipilih) sebagai daftar yang dipisahkan koma. Kueri berikut menunjukkan kueri beberapa nilai dalam output kamus JSON, menggunakan beberapa format output.

```azurecli-interactive
az account show --query [name,id,user.name] # return multiple values
az account show --query [name,id,user.name] -o table # return multiple values as a table
```

Untuk informasi selengkapnya tentang mengembalikan beberapa nilai, lihat [Mendapatkan beberapa nilai](./query-azure-cli.md#get-multiple-values).

### <a name="renaming-properties-in-a-query"></a>Mengganti nama properti dalam kueri

Kueri berikut menunjukkan penggunaan operator { } (hash multipilih) untuk mendapatkan kamus alih-alih array saat mengkueri beberapa nilai. Ini juga menunjukkan penggantian nama properti dalam hasil kueri.

```azurecli-interactive
az account show --query "{SubscriptionName: name, SubscriptionId: id, UserName: user.name}" # Rename the values returned
az account show --query "{SubscriptionName: name, SubscriptionId: id, UserName: user.name}" -o table # Rename the values returned in a table
```

Untuk informasi selengkapnya tentang mengganti nama properti dalam kueri, lihat [Mengganti nama properti dalam kueri](./query-azure-cli.md#rename-properties-in-a-query).

### <a name="querying-boolean-values"></a>Mengkueri nilai boolean

Nilai Boolean diasumsikan benar, sehingga `"[?isDefault]"` sintaks kueri untuk `az account list` perintah mengembalikan langganan default saat ini. Untuk mendapatkan nilai false, Anda harus menggunakan karakter escape, seperti `\`.

Kueri berikut menunjukkan kueri semua akun dalam langganan, berpotensi mengembalikan array JSON jika ada beberapa langganan untuk akun tertentu, lalu mengkueri akun mana yang merupakan langganan default. Ini juga menunjukkan kueri untuk akun yang bukan langganan default. Kueri ini dibangun berdasarkan apa yang Anda pelajari sebelumnya untuk memfilter dan memformat hasilnya. Terakhir, kueri akhir menunjukkan penyimpanan hasil kueri dalam variabel.

```azurecli-interactive
az account list
az account list --query "[?isDefault]" # Returns the default subscription
az account list --query "[?isDefault]" -o table # Returns the default subscription as a table
az account list --query "[?isDefault].[name,id]" # Returns the name and id of the default subscription
az account list --query "[?isDefault].[name,id]" -o table # Returns the name and id of the default subscription as a table
az account list --query "[?isDefault].{SubscriptionName: name, SubscriptionId: id}" -o table # Returns the name and id of the default subscription as a table with friendly names

az account list --query "[?isDefault == \`false\`]" # Returns all non-default subscriptions, if any
az account list --query "[?isDefault == \`false\`].name" -o table # Returns all non-default subscriptions, if any, as a table

az account list --query "[?isDefault].id" -o tsv # Returns the subscription id without quotation marks
subscriptionId="$(az account list --query "[?isDefault].id" -o tsv)" # Captures the subscription id as a variable.
echo $subscriptionId # Returns the contents of the variable.
az account list --query "[? contains(name, 'Test')].id" -o tsv # Returns the subscription id of a non-default subscription containing the substring 'Test'
subscriptionId="$(az account list --query "[? contains(name, 'Test')].id" -o tsv) # Captures the subscription id as a variable. 
az account set -s $subscriptionId # Sets the current active subscription
```

- Untuk informasi selengkapnya tentang memfilter array dan mengkueri nilai boolean, lihat [Memfilter array dengan ekspresi boolean](./query-azure-cli.md#filter-arrays-with-boolean-expressions).
- Untuk informasi selengkapnya tentang menggunakan variabel, lihat [Cara menggunakan variabel](./azure-cli-variables.md).
- Untuk informasi selengkapnya tentang bekerja dengan langganan, lihat [Mengelola langganan](./manage-azure-subscriptions-azure-cli.md).

## <a name="creating-objects-using-variables-and-randomization"></a>Membuat objek menggunakan variabel dan pengacakan

### <a name="setting-a-random-value-for-use-in-subsequent-commands"></a>Mengatur nilai acak untuk digunakan dalam perintah berikutnya

Mengatur dan menggunakan nilai acak untuk digunakan dalam variabel memungkinkan Anda menjalankan skrip beberapa kali tanpa konflik penamaan. Konflik penamaan dapat terjadi karena nilai harus unik di seluruh layanan atau karena objek yang telah Anda hapus masih ada dalam Azure hingga proses penghapusan selesai.

`$RANDOM` adalah fungsi bash (bukan konstanta) yang mengembalikan bilangan bulat 16 bit acak yang ditandatangani (dari 0 hingga 32767). Perintah `let` adalah perintah Bash bawaan untuk mengevaluasi ekspresi aritmatika. Menggunakan perintah berikut membuat nilai yang cukup unik untuk sebagian besar tujuan.

```azurecli-interactive
let "randomIdentifier=$RANDOM*$RANDOM"
```

### <a name="working-with-spaces-and-quotation-marks"></a>Bekerja dengan spasi dan tanda kutip

Spasi digunakan untuk memisahkan perintah, opsi, dan argumen. Gunakan tanda kutip untuk memberi tahu shell Bash untuk mengabaikan semua karakter khusus, di mana spasi putih adalah karakter khusus. Saat shell Bash melihat tanda kutip pertama, shell tersebut mengabaikan karakter khusus hingga tanda kutip penutup. Namun, terkadang Anda ingin shell Bash mengurai karakter khusus tertentu, seperti tanda dolar, tanda kutip balik, dan garis miring terbalik. Untuk ini, gunakan tanda kutip ganda.

Perintah berikut menggunakan perintah [az group create](/cli/azure/group#az-group-create) untuk mengilustrasikan penggunaan tanda kutip tunggal dan ganda untuk menangani spasi dan mengevaluasi karakter khusus saat bekerja dengan variabel dan membuat objek.

```azurecli
resourceGroup='msdocs-learn-bash-$randomIdentifier'
echo $resourceGroup # The $ is ignored in the creation of the $resourceGroup variable
resourceGroup="msdocs-learn-bash-$randomIdentifier"
echo $resourceGroup # The $randomIdentifier is evaluated when defining the $resourceGroup variable
location="East US" # The space is ignored when defining the $location variable
echo The value of the location variable is $location # The value of the $location variable is evaluated
echo "The value of the location variable is $location" # The value of the $location variable is evaluated
echo "The value of the location variable is \$location" # The value of the $location variable is not evaluated
echo 'The value of the location variable is $location' # The value of the $location variable is not evaluated
az group create --name $resourceGroup --location $location # Notice that the space in the $location variable is not ignored and the command fails as it treats the value after the space as a new command 
az group create --name $resourceGroup --location "$location" # Notice that the space in the $location variable is ignored and the location argument accepts the entire string as the value 
```

Dalam output kamus JSON, tinjau properti grup sumber daya yang baru saja dibuat.

### <a name="using-if-then-else-to-determine-if-variable-is-null"></a>Menggunakan If Then Else untuk menentukan apakah variabel null

Untuk mengevaluasi string, gunakan `!=` dan untuk mengevaluasi angka, gunakan `-ne`. Pernyataan If Then Else berikut mengevaluasi apakah variabel $resourceGroup telah ditetapkan. Jika ya, nilai variabel akan dikembalikan. Jika tidak, variabel akan diatur.

```azurecli
if [ $resourceGroup != '' ]; then
   echo $resourceGroup
else
   resourceGroup="msdocs-learn-bash-$randomIdentifier"
fi
```

### <a name="using-if-then-to-create-or-delete-a-resource-group"></a>Menggunakan If Then untuk membuat atau menghapus grup sumber daya

Skrip berikut membuat grup sumber daya baru hanya jika satu dengan nama yang ditentukan belum ada.

```azurecli
if [ $(az group exists --name $resourceGroup) = false ]; then 
   az group create --name $resourceGroup --location "$location" 
else
   echo $resourceGroup
fi
```

Skrip berikut menghapus grup sumber daya baru yang sudah ada jika sudah ada dengan nama yang ditentukan. Anda dapat menggunakan `--no-wait` argumen untuk mengembalikan kontrol tanpa menunggu perintah selesai. Namun, untuk artikel ini, kami ingin menunggu grup sumber daya dihapus sebelum melanjutkan. Untuk informasi selengkapnya tentang operasi asinkron, lihat [Operasi asinkron](./use-cli-effectively.md#asynchronous-operations). Kami akan menunjukkan penggunaan `--no-wait` argumen di akhir artikel ini.

```azurecli
if [ $(az group exists --name $resourceGroup) = true ]; then 
   az group delete --name $resourceGroup -y # --no-wait
else
   echo The $resourceGroup resource group does not exist
fi

```

### <a name="using-grep-to-determine-if-a-resource-group-exists-and-create-the-resource-group-if-it-does-not"></a>Menggunakan Grep untuk menentukan apakah grup sumber daya ada, dan buat grup sumber daya jika tidak

Perintah berikut menyalurkan output `az group list` perintah ke `grep` perintah . Jika grup sumber daya yang ditentukan tidak ada, perintah membuat grup sumber daya menggunakan variabel yang ditentukan sebelumnya.

```azurecli
az group list --output tsv | grep $resourceGroup -q || az group create --name $resourceGroup --location "$location"
```

### <a name="using-case-statement-to-determine-if-a-resource-group-exists-and-create-the-resource-group-if-it-does-not"></a>Menggunakan pernyataan CASE untuk menentukan apakah grup sumber daya ada, dan membuat grup sumber daya jika tidak

Pernyataan CASE berikut membuat grup sumber daya baru hanya jika satu dengan nama yang ditentukan belum ada. Jika ada satu dengan nama yang ditentukan, pernyataan CASE menggemakan bahwa grup sumber daya ada.

```azurecli
var=$(az group list --query "[? contains(name, '$resourceGroup')].name" --output tsv)
case $resourceGroup in
$var)
echo The $resourceGroup resource group already exists.;;
*)
az group create --name $resourceGroup --location "$location";;
esac
```

## <a name="using-for-loops-and-querying-arrays"></a>Menggunakan untuk perulangan dan array kueri

Di bagian artikel ini, kami akan membuat akun penyimpanan dan kemudian menggunakan perulangan untuk membuat sejumlah blob dan kontainer. Kami juga akan menunjukkan kueri array JSON dan bekerja dengan variabel lingkungan.

### <a name="create-storage-account"></a>Membuat akun penyimpanan

Perintah berikut menggunakan perintah [az storage account create](/cli/azure/storage/account#az-storage-account-create) untuk membuat akun penyimpanan yang akan kita gunakan saat membuat kontainer penyimpanan.

```azurecli
storageAccount="learnbash$randomIdentifier"
az storage account create --name $storageAccount --location "$location" --resource-group $resourceGroup --sku Standard_LRS --encryption-services blob
```

### <a name="get-the-storage-account-keys"></a>Mendapatkan kunci akun penyimpanan

Perintah berikut menggunakan perintah [az storage account keys list](/cli/azure/storage/account/keys#az-storage-account-keys-list) untuk mengembalikan nilai kunci akun penyimpanan. Kami kemudian menyimpan nilai kunci dalam variabel untuk digunakan saat membuat kontainer penyimpanan.

```azurecli
az storage account keys list --resource-group $resourceGroup --account-name $storageAccount --query "[].value" -o tsv # returns both storage account key values

az storage account keys list --resource-group $resourceGroup --account-name $storageAccount --query "[0].value" -o tsv # returns a single storage account key value

accountKey=$(az storage account keys list --resource-group $resourceGroup --account-name $storageAccount --query "[0].value" -o tsv)

echo $accountKey
```

### <a name="create-storage-container"></a>Membuat kontainer penyimpanan

Kita akan mulai dengan menggunakan [az storage container create](/cli/azure/storage/container#az-storage-container-create) untuk membuat satu kontainer penyimpanan lalu menggunakan [az storage container list untuk mengkueri](/cli/azure/storage/container#az-storage-container-list) nama kontainer yang dibuat.

```azurecli
container="learningbash"
az storage container create --account-name $storageAccount --account-key $accountKey --name $container

az storage container list --account-name $storageAccount --account-key $accountKey --query [].name
```

### <a name="upload-data-to-container"></a>Upload data ke kontainer

Skrip berikut membuat tiga file sampel menggunakan untuk perulangan.

```azurecli
for i in `seq 1 3`; do
    echo $randomIdentifier > container_size_sample_file_$i.txt
done
```

Skrip berikut menggunakan perintah [az storage blob upload-batch](/cli/azure/storage/blob#az-storage-blob-upload-batch) untuk mengunggah blob ke kontainer penyimpanan.

```azurecli
az storage blob upload-batch \
    --pattern "container_size_sample_file_*.txt" \
    --source . \
    --destination $container \
    --account-key $accountKey \
    --account-name $storageAccount
```

Skrip berikut menggunakan perintah [az storage blob list](/cli/azure/storage/blob#az-storage-blob-list) untuk mencantumkan blob dalam kontainer.

```azurecli
az storage blob list \
    --container-name $container \
    --account-key $accountKey \
    --account-name $storageAccount \
    --query "[].name"
```

Skrip berikut menampilkan total byte dalam kontainer penyimpanan.

```azurecli
bytes=`az storage blob list \
    --container-name $container \
    --account-key $accountKey \
    --account-name $storageAccount \
    --query "[*].[properties.contentLength]" \
    --output tsv | paste -s -d+ | bc`

echo "Total bytes in container: $bytes"
echo $bytes
```

### <a name="create-many-containers-using-loops"></a>Membuat banyak kontainer menggunakan perulangan

Selanjutnya, kita akan membuat beberapa kontainer menggunakan perulangan yang menunjukkan beberapa cara untuk menulis perulangan.

```azurecli
for i in `seq 1 4`; do 
az storage container create --account-name $storageAccount --account-key $accountKey --name learnbash-$i
done

for value in {5..8}
for (( i=5; i<10; i++))
do
az storage container create --account-name $storageAccount --account-key $accountKey --name learnbash-$i
done

az storage container list --account-name $storageAccount --account-key $accountKey --query [].name
```

### <a name="use-export-to-define-environment-variables"></a>Gunakan EXPORT untuk menentukan variabel lingkungan

Dalam skrip kontainer penyimpanan sebelumnya, kami menentukan nama akun dan kunci akun dengan setiap perintah. Sebagai gantinya, Anda dapat menyimpan kredensial autentikasi menggunakan variabel lingkungan yang sesuai: `AZURE_STORAGE_ACCOUNT` dan `AZURE_STORAGE_KEY`. Untuk melakukan ini, gunakan EXPORT.

```azurecli
export AZURE_STORAGE_ACCOUNT=$storageAccount
export AZURE_STORAGE_KEY=$accountKey
az storage container list # Uses the environment variables to display the list of containers.
```

Skrip berikut membuat string metadata lalu menggunakan perintah [az storage container metadata update](/cli/azure/storage/container/metadata#az-storage-container-metadata-update) untuk memperbarui kontainer dengan string tersebut, sekali lagi menggunakan variabel lingkungan.

```azurecli
metadata="key=value pie=delicious" # Define metadata
az storage container metadata update \
    --name $container \
    --metadata $metadata # Update the metadata
az storage container metadata show \
    --name $containerName # Show the metadata
```

Perintah berikut menggunakan perintah [az storage container delete](/cli/azure/storage/container#az-storage-container-delete) untuk menghapus satu kontainer bernama lalu menghapus beberapa kontainer dalam perulangan.

```azurecli
az storage container delete \
    --name $container
```

Dapatkan daftar kontainer yang berisi awalan tertentu dan simpan hasil ke dalam variabel.

```azurecli
containerPrefix="learnbash"
containerList=$(az storage container list \
    --query "[].name" \
    --prefix $containerPrefix \
    --output tsv)
```

Hapus daftar kontainer dalam perulangan menggunakan `--prefix` argumen .

```azurecli
for row in $containerList
do
    tmpName=$(echo $row | sed -e 's/\r//g')
    az storage container delete \
    --name $tmpName 
done
```

## <a name="error-handling"></a>Penanganan kesalahan

Untuk segera keluar dari skrip jika perintah mengembalikan status bukan nol, jalankan perintah berikut:

```azurecli-interactive
set -e
```

Untuk informasi selengkapnya tentang mengatur opsi shell dan topik bantuan lainnya, jalankan perintah berikut:

```azurecli-interactive
help set
help help
```

## <a name="clean-up-resources"></a>Bersihkan sumber daya

Setelah anda selesai artikel ini, hapus grup sumber daya dan semua sumber daya di dalamnya. `--no-wait` Gunakan argumen .

```azurecli
if [ $(az group exists --name $resourceGroup) = true ]; then 
   az group delete --name $resourceGroup -y  --no-wait
else
   echo The $resourceGroup resource group does not exist
fi
```

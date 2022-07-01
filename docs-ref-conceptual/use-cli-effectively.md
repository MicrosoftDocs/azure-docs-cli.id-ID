---
title: Tips untuk menggunakan | Azure CLI Microsoft Docs
description: Pelajari tips untuk menggunakan Azure CLI dengan sukses, seperti format output, meneruskan nilai parameter, dan aturan kutipan untuk shell yang berbeda.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 10/01/2021
ms.topic: conceptual
ms.service: azure-cli
ms.tool: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
ms.openlocfilehash: 9b148c600175894b635abb07cd90e748059d97bc
ms.sourcegitcommit: 1c90b81d8746101eeff6dab16f71270efb6d6827
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 07/01/2022
ms.locfileid: "146806586"
---
# <a name="tips-for-using-the-azure-cli-successfully"></a>Tips untuk menggunakan Azure CLI dengan sukses

Azure CLI adalah alat baris perintah yang memungkinkan Anda mengonfigurasi dan mengelola sumber daya Azure dari banyak lingkungan shell.  Pertama [- tama pilih alat baris perintah yang tepat](/cli/azure/choose-the-right-azure-command-line-tool#different-shell-environments) dan [instal](/cli/azure/install-azure-cli) Azure CLI.  Kemudian gunakan artikel ini untuk menemukan tips yang berguna tentang cara menghindari perangkap umum dan berhasil menggunakan Azure CLI.

Untuk mempelajari selengkapnya tentang perintah Azure CLI tertentu, lihat [daftar Referensi Azure CLI](../latest/docs-ref-autogen/reference-index.yml).

## <a name="output-formatting"></a>Pemformatan output

Tiga format output umum digunakan dengan perintah Azure CLI:

1. `json` Format menunjukkan informasi sebagai string JSON.
   - JSON memberi Anda informasi paling komprehensif.
   - Format ini adalah default tetapi Anda dapat menggunakan `--output` parameter untuk menentukan opsi yang berbeda.
   - Ubah format default global ke salah satu preferensi pribadi Anda dengan menggunakan [konfigurasi az](../latest/docs-ref-autogen/config.yml) seperti `az config set core.output=table`.
   - Perhatikan bahwa format JSON mempertahankan tanda kutip ganda, umumnya dibuat dengan tidak cocok untuk tujuan pembuatan skrip.

2. `table` Format menyajikan output sebagai tabel yang dapat dibaca. Anda bisa menentukan nilai mana yang muncul dalam tabel dan menggunakan kueri untuk mengkustomisasi output seperti yang diperlihatkan di sini:

    ```azurecli
    # command
    az vm show --resource-group myResourceGroup --name myVMname --query "{name: name, os:storageProfile.imageReference.offer}" --output table
    
    # output
    Name    Os
    ------  ------------
    myVMname   UbuntuServer
    ```

3. Format `tsv` menampilkan nilai yang dipisahkan tab dan dipisahkan baris baru tanpa pemformatan tambahan, kunci, atau simbol lainnya.
   - Format TSV berguna untuk output ringkas dan tujuan pembuatan skrip.
   - TSV akan menghapus tanda kutip ganda yang dipertahankan format JSON.
   - Untuk menentukan format yang Anda inginkan untuk TSV, gunakan `--query` parameter .

    ```bash
    export vm_ids=$(az vm list --show-details --resource-group myResourceGroup --query "[?powerState=='VM running'].id" --output tsv)
    az vm stop --ids $vm_ids
    ```

Untuk informasi selengkapnya, lihat [Format output untuk perintah Azure CLI](./format-output-azure-cli.md).

## <a name="pass-values-to-another-command"></a>Meneruskan nilai ke perintah lain

Jika nilai akan digunakan lebih dari sekali, tetapkan ke variabel. Variabel memungkinkan Anda menggunakan nilai lebih dari sekali atau untuk membuat lebih banyak skrip umum.  Contoh ini menetapkan ID yang ditemukan oleh perintah [az vm list](/cli/azure/vm#az-vm-list) ke variabel.

  ```bash
  # assign the list of running VMs to a variable
  running_vm_ids=$(az vm list --resource-group MyResourceGroup --show-details \
      --query "[?powerState=='VM running'].id" --output tsv)

  # verify the value of the variable
  echo $running_vm_ids
  ```

Jika nilai hanya digunakan sekali, pertimbangkan pipa.  

  ```azurecli
  az vm list --query "[?powerState=='VM running'].name" --output tsv | grep my_vm
  ```

Untuk daftar multinilai, pertimbangkan opsi berikut:

1. Jika Anda memerlukan lebih banyak kontrol pada hasilnya, gunakan perulangan "untuk":

    ```bash
    #!/usr/bin/env bash
    for vmList in $(az vm list --resource-group MyResourceGroup --show-details --query "[?powerState=='VM running'].id"   --output tsv); do
        echo stopping $vmList
        az vm stop --ids $vmList
        if [ $? -ne 0 ]; then
            echo "Failed to stop $vmList"
            exit 1
        fi
        echo $vmList stopped
    done
    ```

1. Atau, gunakan `xargs` dan pertimbangkan untuk menggunakan `-P` bendera untuk menjalankan operasi secara paralel untuk meningkatkan performa:

    ```azurecli
    az vm list --resource-group MyResourceGroup --show-details \
      --query "[?powerState=='VM stopped'].id" \
      --output tsv | xargs -I {} -P 10 az vm start --ids "{}"
    ```

1. Akhirnya, Azure CLI memiliki dukungan bawaan untuk memproses perintah dengan beberapa `--ids` secara paralel untuk mencapai efek xarg yang sama. Perhatikan bahwa `@-` digunakan untuk mendapatkan nilai dari pipa:

    ```azurecli
    az vm list --resource-group MyResourceGroup --show-details \
      --query "[?powerState=='VM stopped'].id" \
      --output tsv | az vm start --ids @-
    ```

Untuk informasi selengkapnya tentang menggunakan konstruksi Bash dengan Azure CLI termasuk perulangan, pernyataan kasus, jika.. Kemudian.. lainnya, dan penanganan kesalahan, lihat [Pelajari cara menggunakan Bash dengan Azure CLI](./azure-cli-learn-bash.md).

## <a name="use-quotation-marks-in-parameters"></a>Menggunakan tanda kutip dalam parameter

Saat Anda bekerja dengan perintah Azure CLI, ketahui cara shell menggunakan tanda kutip dan karakter escape. Jika Anda mendukung skrip yang digunakan dalam shell yang berbeda, Anda perlu memahami perbedaannya.

- Bash. [Mengutip](https://www.gnu.org/software/bash/manual/html_node/Quoting.html)
- PowerShell. [Tentang Aturan Mengutip](/powershell/module/microsoft.powershell.core/about/about_quoting_rules)
- Windows Command Prompt. [Cara: Menggunakan Karakter Escape, Pemisah dan Kutipan di baris perintah Windows](https://ss64.com/nt/syntax-esc.html)

> [!NOTE]
> Karena masalah yang diketahui di PowerShell, beberapa aturan penggunaan karakter escape tambahan diberlakukan. Untuk informasi selengkapnya, lihat [Mengutip masalah dengan PowerShell](https://github.com/Azure/azure-cli/blob/dev/doc/quoting-issues-with-powershell.md).

Untuk menghindari hasil yang tidak diperhitungkan, berikut adalah beberapa saran:

- Jika Anda memberikan parameter yang berisi spasi kosong, bungkus dalam tanda kutip.

- Di Bash atau PowerShell, tanda kutip tunggal dan ganda ditafsirkan dengan benar. Di Perintah Windows, hanya tanda kutip ganda yang ditafsirkan dengan benar -- tanda kutip tunggal diperlakukan sebagai bagian dari nilai.

- Jika perintah Anda hanya akan berjalan di Bash (atau Zsh), gunakan tanda kutip tunggal untuk mempertahankan konten di dalam string JSON. Ini diperlukan saat memasok nilai JSON sebaris.  Misalnya, JSON ini benar di Bash: `'{"key": "value"}'`.

- Jika perintah Anda akan dijalankan pada Prompt Perintah Windows, Anda harus menggunakan tanda kutip ganda.  Jika nilai berisi tanda kutip ganda, Anda harus menghindarinya.  Setara dengan string JSON di atas adalah `"{\"key\": \"value\"}"`

- Gunakan konvensi Azure CLI `@<file>` untuk memuat dari file dan melewati mekanisme interpretasi shell.
  
  ```azurecli
  az ad app create --display-name myName --native-app --required-resource-accesses @manifest.json  
  ```

- Bash mengevaluasi kutipan ganda dalam variabel yang diekspor. Jika perilaku ini bukan yang Anda inginkan, hindari variabel: `"\$variable"`.

- Beberapa perintah Azure CLI mengambil daftar nilai yang dipisahkan spasi. 
  - Jika nama kunci atau nilai berisi spasi, apit seluruh pasangan: `"my key=my value"`.  Contohnya:
  
    ```azurecli
    az web app config app settings set --resource-group myResourceGroup --name myWebAppName --settings "client id=id1" "my name=john"
    ```

  - Ketika parameter CLI menyatakan bahwa parameter menerima daftar yang dipisahkan spasi, salah satu dari dua format diharapkan:
    1. Daftar yang tidak dikutip dan dipisahkan spasi `--parameterName firstValue secondValue`
    1. Daftar yang dipisahkan spasi yang dikutip `--parameterName "firstValue" "secondValue"`

    Contoh ini adalah string dengan spasi di dalamnya.  Ini bukan daftar yang dipisahkan spasi: `--parameterName "firstValue secondValue"`

- Ada karakter khusus PowerShell, seperti di `@`. Untuk menjalankan Azure CLI di PowerShell, tambahkan `` ` `` sebelum karakter khusus untuk mengeluarkannya dari program. Anda juga dapat mengapit nilai dalam tanda kutip `"`/`"`tunggal atau ganda .

  ```powershell
  # The following three examples will work in PowerShell
  --parameterName `@parameters.json
  --parameterName '@parameters.json'
  --parameterName "@parameters.json"

  # This example will not work in PowerShell
  --parameterName @parameters.json
  ```

- Jika Anda menggunakan parameter `--query` dengan perintah, beberapa karakter [JMESPath](https://jmespath.org/specification.html) harus dikeluarkan dari program dalam shell.  

  ### <a name="bash"></a>[Bash](#tab/bash)

  Ketiga perintah ini benar dan setara di Bash:

  ```azurecli
  az version --query '"azure-cli"'
  az version --query \"azure-cli\"
  az version --query "\"azure-cli\""
  ```

  Berikut adalah dua contoh perintah yang salah di Bash:

  ```azurecli
  # Wrong, as the dash needs to be quoted in a JMESPath query
  az version --query azure-cli
  az version: error: argument --query: invalid jmespath_type value: 'azure-cli'
    
  # Wrong, as the dash needs to be quoted in a JMESPath query, but quotes are interpreted by Bash
  az version --query "azure-cli"
  az version: error: argument --query: invalid jmespath_type value: 'azure-cli'
  ```

  Untuk contoh perbandingan lainnya antara Bash, PowerShell dan Cmd, lihat [Kueri output perintah Azure CLI](./query-azure-cli.md)

  ### <a name="powershell"></a>[PowerShell](#tab/powershell)

  Kelima perintah ini akan berfungsi dengan benar di PowerShell:

  ```azurecli
  az version --query '\"azure-cli\"'
  az version --query "\`"azure-cli\`""
  az version --query "\""azure-cli\"""
  az --% version --query "\"azure-cli\""
  az --% version --query \"azure-cli\"
  ```

  Untuk contoh perbandingan lainnya antara Bash, PowerShell dan Cmd, lihat [Kueri output perintah Azure CLI](./query-azure-cli.md)

  ### <a name="cmd"></a>[Cmd](#tab/cmd)

  Kedua perintah ini akan berfungsi dengan benar di Prompt Perintah Windows:

  ```azurecli
  az version --query "\"azure-cli\""
  az version --query \"azure-cli\"
  ```
  
  Untuk contoh perbandingan lainnya antara Bash, PowerShell dan Cmd, lihat [Kueri output perintah Azure CLI](./query-azure-cli.md)

  ---

- Cara terbaik untuk memecahkan masalah kutipan adalah dengan menjalankan perintah dengan `--debug` bendera .  Bendera ini mengungkapkan argumen aktual yang diterima oleh Azure CLI dalam [sintaks Python](https://docs.python.org/3/tutorial/introduction.html#strings).

  ```bash
  # Correct
  $ az '{"key":"value"}' --debug
  Command arguments: ['{"key":"value"}', '--debug']

  # Correct
  $ az "{\"key\":\"value\"}" --debug
  Command arguments: ['{"key":"value"}', '--debug']

  # Wrong, as quotes and spaces are interpreted by Bash
  $ az {"key": "value"} --debug
  Command arguments: ['{key:', 'value}', '--debug']

  # Wrong, as quotes are interpreted by Bash
  $ az {"key":"value"} --debug
  Command arguments: ['{key:value}', '--debug']  
  ```

## <a name="use-hyphen-characters-in-parameters"></a>Menggunakan karakter tanda hubung dalam parameter

Jika nilai parameter dimulai dengan tanda hubung, Azure CLI mencoba mengurainya sebagai nama parameter. Untuk mengurainya sebagai nilai, gunakan `=` untuk menggabungkan nama dan nilai parameter: `--password="-VerySecret"`.

## <a name="asynchronous-operations"></a>Operasi Asinkron

Operasi di Azure dapat memakan waktu banyak waktu. Misalnya, mengonfigurasi komputer virtual di pusat data tidak seketika. Azure CLI menunggu hingga perintah selesai untuk menerima perintah lain.  Oleh karena itu, banyak perintah menawarkan parameter seperti yang `--no-wait` ditunjukkan di sini:

```azurecli
az group delete --name MyResourceGroup --no-wait
```

Saat menghapus grup sumber daya, semua sumber daya milik grup ini juga dihapus. Diperlukan waktu yang lama untuk menghapus sumber daya ini. Eksekusi perintah dengan parameter `--no-wait`, memungkinkan konsol untuk menerima perintah baru tanpa mengganggu proses penghapusan.

Banyak perintah menawarkan opsi tunggu, yang menjeda konsol hingga beberapa kondisi terpenuhi. Contoh berikut menggunakan perintah [az vm wait](/cli/azure/vm#az-vm-wait) untuk mendukung pembuatan sumber daya independen secara paralel:

```azurecli
az vm create --resource-group VMResources --name virtual-machine-01 --image centos --no-wait
az vm create --resource-group VMResources --name virtual-machine-02 --image centos --no-wait

subscription=$(az account show --query "id" -o tsv)
vm1_id="/subscriptions/$subscription/resourceGroups/VMResources/providers/Microsoft.Compute/virtualMachines/virtual-machine-01"
vm2_id="/subscriptions/$subscription/resourceGroups/VMResources/providers/Microsoft.Compute/virtualMachines/virtual-machine-02"
az vm wait --created --ids $vm1_id $vm2_id
```

Setelah kedua ID dibuat, Anda dapat menggunakan konsol lagi.

## <a name="work-behind-a-proxy"></a>Bekerja di belakang proksi

Jika Anda menggunakan Azure CLI melalui server proksi yang menggunakan sertifikat yang ditandatangani sendiri, [pustaka permintaan](https://github.com/kennethreitz/requests) Python yang digunakan oleh Azure CLI dapat menyebabkan kesalahan berikut: `SSLError("bad handshake: Error([('SSL routines', 'tls_process_server_certificate', 'certificate verify failed')],)",)`. Untuk mengatasi kesalahan ini, atur variabel `REQUESTS_CA_BUNDLE` lingkungan ke jalur file sertifikat bundel CA dalam format PEM.

| OS                     | Bundel otoritas sertifikat default                                                  |
|----------------------- |-------------------------------------------------------------------------------------- |
| Windows                | C:\Program Files (x86)\Microsoft SDKs\Azure\CLI2\Lib\site-packages\certifi\cacert.pem |
| Ubuntu/Debian Linux    | /opt/az/lib/python<version>/site-packages/certifi/cacert.pem                                |
| CentOS/RHEL/SUSE Linux | /usr/lib64/az/lib/python<version>/site-packages/certifi/cacert.pem                          |
| macOS                  | /usr/local/Cellar/azure-cli/\<cliversion\>/libexec/lib/python<version>/site-packages/certifi/cacert.pem|

Tambahkan sertifikat server proksi ke file sertifikat bundel CA, atau salin konten ke file sertifikat lain.  Kemudian atur `REQUESTS_CA_BUNDLE` ke lokasi file baru.  Berikut contohnya:

    ```console
    <Original cacert.pem>

    -----BEGIN CERTIFICATE-----
    <Your proxy's certificate here>
    -----END CERTIFICATE-----
    ```

Beberapa proksi memerlukan autentikasi. Format variabel lingkungan `HTTP_PROXY` atau `HTTPS_PROXY` lingkungan harus menyertakan autentikasi, seperti `HTTPS_PROXY="https://username:password@proxy-server:port"`. Untuk mengetahui detailnya, lihat [Cara mengonfigurasi proksi untuk pustaka Azure](/azure/developer/python/sdk/azure-sdk-configure-proxy?tabs=bash).

## <a name="concurrent-builds"></a>Build bersamaan

Jika Anda menjalankan Azure CLI di mesin build tempat beberapa pekerjaan dapat dijalankan secara paralel, token akses dapat dibagikan antara dua pekerjaan build yang dijalankan sebagai pengguna OS yang sama.  Untuk menghindari campuran, atur `AZURE_CONFIG_DIR` ke direktori tempat token akses disimpan.

## <a name="generic-update-parameters"></a>Parameter pembaruan generik

Grup perintah Azure CLI sering menonjolkan perintah pembaruan. Misalnya, [Azure Virtual Machines](/cli/azure/vm) menyertakan perintah [az vm update](/cli/azure/vm#az-vm-update). Sebagian besar perintah pembaruan menawarkan tiga parameter generik: `--add`, `--set`, dan `--remove`.

Parameter `--set` dan `--add` menggunakan daftar pasangan nilai kunci yang dipisahkan spasi: `key1=value1 key2=value2`. Untuk melihat properti yang dapat diperbarui, gunakan perintah tampilkan, seperti [az vm show](/cli/azure/vm#az-vm-show).

```azurecli
az vm show --resource-group VMResources --name virtual-machine-01
```

Untuk menyederhanakan perintah, pertimbangkan untuk menggunakan string JSON. Misalnya, untuk menyertakan disk data baru ke mesin virtual, gunakan nilai berikut:

```azurecli
az vm update --resource-group VMResources --name virtual-machine-01 \
--add storageProfile.dataDisks "{\"createOption\": \"Attach\", \"managedDisk\":
   {\"id\":
   \"/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/yg/providers/Microsoft.Compute/disks/yg-disk\"}, 
   \"lun\": 1}"
```

## <a name="generic-resource-commands-az-resource"></a>Perintah sumber daya generik (sumber daya az)

Layanan yang ingin Anda kerjakan mungkin tidak memiliki dukungan Azure CLI. Anda dapat menggunakan perintah [az resource](../latest/docs-ref-autogen/resource.yml) untuk bekerja dengan sumber daya ini.

Jika Anda hanya memerlukan perintah buat dan perbarui, gunakan [az deployment group create](/cli/azure/deployment/group#az-deployment-group-create). Sebagai contoh kerja, lihat [Template Mulai Cepat Azure](https://azure.microsoft.com/resources/templates/).

## <a name="rest-api-commands-az-rest"></a>Perintah REST API (az rest)

Jika parameter pembaruan generik dan [sumber daya az](../latest/docs-ref-autogen/resource.yml) tidak memenuhi kebutuhan Anda, Anda dapat menggunakan perintah [az rest](/cli/azure/reference-index#az-rest) untuk memanggil REST API. Perintah secara otomatis melakukan autentikasi menggunakan info masuk dimasukkan dan mengatur header `Content-Type: application/json`. Untuk informasi selengkapnya, lihat [Referensi Azure REST API](/rest/api/azure/).

Contoh ini berfungsi dengan [Microsoft Graph API](/graph/api/overview?toc=./ref/toc.json). Untuk memperbarui URI pengalihan untuk [Aplikasi](/graph/api/resources/application), panggil [REST API aplikasi Pembaruan](/graph/api/application-update?tabs=http) , seperti dalam kode ini:

```azurecli
# Get the application
az rest --method GET \
    --uri 'https://graph.microsoft.com/v1.0/applications/b4e4d2ab-e2cb-45d5-a31a-98eb3f364001'

# Update `redirectUris` for `web` property
az rest --method PATCH \
    --uri 'https://graph.microsoft.com/v1.0/applications/b4e4d2ab-e2cb-45d5-a31a-98eb3f364001' \
    --body '{"web":{"redirectUris":["https://myapp.com"]}}'
```

Saat menggunakan `--uri-parameters` untuk permintaan dalam bentuk OData, pastikan untuk melarikan diri `$` di lingkungan yang berbeda: di `Bash`, escape `$` sebagai `\$` dan di `PowerShell`, escape `$` sebagai `` `$``

## <a name="script-examples"></a>Contoh skrip

Berikut adalah contoh penggunaan variabel dan perulangan melalui daftar saat bekerja dengan Azure Virtual Machines.  Untuk contoh mendalam tentang menggunakan konstruksi Bash dengan Azure CLI termasuk perulangan, pernyataan kasus, if.. Kemudian.. lainnya, dan penanganan kesalahan, lihat [Pelajari cara menggunakan Bash dengan Azure CLI](./azure-cli-learn-bash.md).  

Gunakan skrip ini untuk menyimpan ID ke variabel:

### <a name="bash"></a>[Bash](#tab/bash2)

```console
ECHO OFF
SETLOCAL
FOR /F "tokens=* USEBACKQ" %%F IN (
   `az vm list --resource-group VMResources --show-details --query "[?powerState=='VM running'].id" --output tsv`
) DO (
    SET "vm_ids=%%F %vm_ids%"  :: construct the id list
)
az vm stop --ids %vm_ids% :: CLI stops all VMs in parallel
```

### <a name="powershell"></a>[PowerShell](#tab/powershell2)

```powershell
$vm_ids=(az vm list --resource-group VMResources --show-details --query "[?powerState=='VM running'].id" --output tsv)
az vm stop --ids $vm_ids # CLI stops all VMs in parallel
```

---

Gunakan skrip ini untuk mengulang daftar:

### <a name="bash"></a>[Bash](#tab/bash2)

```console
ECHO OFF
SETLOCAL
FOR /F "tokens=* USEBACKQ" %%F IN (
    `az vm list --resource-group VMResources --show-details --query "[?powerState=='VM running'].id" --output tsv`
) DO (
    ECHO Stopping %%F
    az vm stop --ids %%F
)
```

### <a name="powershell"></a>[PowerShell](#tab/powershell2)

```powershell
$vm_ids=(az vm list --resource-group VMResources --show-details --query "[?powerState=='VM running'].id" --output tsv)
foreach ($vm_id in $vm_ids) {
    Write-Output "Stopping $vm_id"
    az vm stop --ids $vm_id
}
```

---

## <a name="error-handling-for-azure-cli-in-powershell"></a>Penanganan kesalahan untuk Azure CLI di PowerShell

Anda dapat menjalankan perintah Azure CLI di PowerShell, seperti yang dijelaskan dalam [Memilih alat baris perintah Azure yang tepat](choose-the-right-azure-command-line-tool.md). Jika demikian, pastikan Anda memahami penanganan kesalahan Azure CLI di PowerShell. Khususnya, Azure CLI tidak membuat pengecualian untuk diambil PowerShell.

Alternatifnya adalah menggunakan variabel otomatis `$?`. Variabel ini berisi status perintah terbaru. Jika perintah sebelumnya gagal, `$?` memiliki nilai `$False`. Untuk informasi selengkapnya, lihat [about_Automatic_Variables](/powershell/module/microsoft.powershell.core/about/about_automatic_variables).

Contoh berikut menunjukkan bagaimana variabel otomatis ini dapat bekerja untuk penanganan kesalahan:

```powershell
az group create --name MyResourceGroup
if ($? -eq $false) {
    Write-Error "Error creating resource group."
}
```

Perintah `az` gagal karena kehilangan parameter `--location` yang diperlukan. Pernyataan bersyarat menemukan bahwa `$?` salah dan menulis kesalahan.

Jika Anda ingin menggunakan `try` kata kunci dan `catch`, Anda dapat menggunakan `throw` untuk membuat pengecualian agar blok `try` dapat mengambil:

```powershell
$ErrorActionPreference = "Stop"
try {
    az group create --name MyResourceGroup
    if ($? -eq $false) {
        throw 'Group create failed.'
    }
}
catch {
    Write-Error "Error creating the resource group."
}
$ErrorActionPreference = "Continue"
```

Secara default, PowerShell hanya mengambil kesalahan pengakhiran. Contoh ini menetapkan variabel global `$ErrorActionPreference` ke `Stop` sehingga PowerShell dapat menangani kesalahan.

Pernyataan bersyarat menguji variabel `$?` untuk mengetahui apakah perintah sebelumnya gagal. Jika demikian, kata kunci `throw` membuat pengecualian untuk mengambil. Blok `catch` dapat digunakan untuk menulis pesan kesalahan atau menangani kesalahan.

Contoh tersebut mengembalikan `$ErrorActionPreference` ke nilai default-nya.

Untuk informasi selengkapnya tentang penanganan kesalahan PowerShell, lihat [Segala hal yang ingin Anda ketahui tentang pengecualian](/powershell/scripting/learn/deep-dives/everything-about-exceptions).

## <a name="see-also"></a>Lihat juga

- [Mengonfigurasi Azure CLI](./azure-cli-configuration.md)
- [Pelajari cara menggunakan Bash dengan Azure CLI](./azure-cli-learn-bash.md)
- [Mengkueri output perintah Azure CLI](./query-azure-cli.md)
- [Menggunakan variabel dalam perintah Azure CLI](./azure-cli-variables.md)

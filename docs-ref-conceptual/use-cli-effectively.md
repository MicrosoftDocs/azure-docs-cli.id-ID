---
title: Menggunakan Azure CLI secara efektif | Microsoft Docs
description: Pelajari tips untuk menggunakan Azure CLI secara efektif, seperti format output, mengabaikan nilai parameter, dan mengutip aturan untuk shell yang berbeda.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 10/01/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
ms.openlocfilehash: 80c6701787b2ded269139fd37608ef34003685c0
ms.sourcegitcommit: a805041ebd77f92fa4b3025ba6856ea4aedae2ac
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/22/2022
ms.locfileid: "144004091"
---
# <a name="how-to-use-azure-cli-effectively"></a>Cara menggunakan Azure CLI secara efektif

Azure CLI memungkinkan Anda mengonfigurasi dan mengelola Azure dari Bash, PowerShell, atau Jendela Wantian Perintah. Azure CLI mendukung penggunaan kembali perintah, baik secara ad-hoc maupun melalui skrip. Anda harus mengetahui kemampuan shell yang Anda jalankan.

Artikel ini membahas tips yang berguna tentang cara menggunakan Azure CLI dan cara menghindari masalah.

[!INCLUDE [azure-cli-prepare-your-environment.md](includes/azure-cli-prepare-your-environment.md)]

Jika Anda memiliki pertanyaan tentang perintah Azure CLI apa pun, cari di [Referensi Azure CLI](../latest/docs-ref-autogen/reference-index.yml).

## <a name="output-formatting"></a>Pemformatan output

Banyak perintah Azure CLI yang memperlihatkan data di konsol. Informasi ini bisa menjadi tujuan perintah, seperti dalam contoh ini, di mana perintah [az account show](/cli/azure/account#az-account-show) menunjukkan langganan Anda saat ini:

```azurecli
az account show
```

Terkadang, informasi yang ditampilkan perintah memperlihatkan perubahan yang Anda buat. Anda dapat membuat grup sumber daya dengan menggunakan perintah [az group create](/cli/azure/group#az-group-create):

```azurecli
az group create --name MyResourceGroup --location eastus
```

Jika Anda menjalankan perintah ini, konsol Azure CLI akan menampilkan grup sumber daya yang baru saja dibuat.

Anda dapat memilih format output dengan menentukan parameter `--output`. Dalam contoh ini, perintah [az account list](/cli/azure/account#az-account-list) mencantumkan semua langganan yang dapat diakses sebagai tabel:

```azurecli
az account list --output table
```

Berikut tiga format umum:

- Format `json` menampilkan informasi sebagai string JSON. Format ini memberi Anda informasi paling komprehensif. Ini adalah format default. Anda dapat mengubah format default dengan menggunakan perintah [az config](../latest/docs-ref-autogen/config.yml).
- Format `table` menampilkan output sebagai tabel yang dapat dibaca manusia. Anda dapat menentukan nilai mana yang akan muncul dalam tabel dan menggunakan kueri untuk menyesuaikan output.
- Format `tsv` menampilkan nilai yang dipisahkan tab dan dipisahkan baris baru tanpa pemformatan tambahan, kunci, atau simbol lainnya.

Untuk informasi selengkapnya, lihat [Format output untuk perintah Azure CLI](format-output-azure-cli.md).

## <a name="pass-values-to-another-command"></a>Meneruskan nilai ke perintah lain

Perintah Azure CLI dijalankan dalam shell. Artikel ini menggunakan Bash, tetapi masih ada opsi lain. Anda dapat menggunakan sintaks shell standar untuk memudahkan penggunaan Azure CLI.

Anda dapat menyimpan nilai sebagai variabel. Variabel memungkinkan Anda menggunakan nilai lebih dari sekali atau untuk membuat lebih banyak skrip umum. Contoh ini menggunakan perintah [az vm list](/cli/azure/vm#az_vm_list) dengan kueri `[?powerState=='VM running'].id` untuk menemukan ID VM yang sedang berjalan. Untuk mempelajari selengkapnya tentang `--query` dan kueri JMESPath lihat [Cara mengkueri output perintah Azure CLI menggunakan kueri JMESPath](./query-azure-cli.md).

```azurecli
running_vm_ids=$(az vm list --resource-group MyResourceGroup --show-details \
   --query "[?powerState=='VM running'].id" --output tsv)
```

> [!TIP]
> Pastikan untuk menggunakan jenis output `tsv`. Jenis output lain mungkin berisi simbol yang tidak diinginkan seperti tanda kutip.

Gunakan nilai dalam perintah berikutnya. Anda dapat memverifikasi nilai dengan mengulangi variabel:

```azurecli
echo $running_vm_ids
```

Anda juga bisa mengalirkan nilai dari satu perintah ke perintah lainnya. Contoh ini menggunakan sintaks Bash standar untuk mencari nilai:

```azurecli
az vm list --query "[?powerState=='VM running'].name" --output tsv | grep my_vm
```

## <a name="pass-arguments"></a>Meneruskan argumen

### <a name="use-quotation-marks-in-arguments"></a>Menggunakan tanda kutip dalam argumen

Saat Anda bekerja dengan perintah Azure CLI, ketahui cara shell menggunakan tanda kutip dan karakter escape. Jika Anda mendukung skrip yang digunakan dalam shell yang berbeda, Anda perlu memahami perbedaannya.

- Bash. [Mengutip](https://www.gnu.org/software/bash/manual/html_node/Quoting.html)
- PowerShell. [Tentang Aturan Mengutip](/powershell/module/microsoft.powershell.core/about/about_quoting_rules)
- Windows Command Prompt. [Cara: Menggunakan Karakter Escape, Pemisah dan Kutipan di baris perintah Windows](https://ss64.com/nt/syntax-esc.html)

> [!NOTE]
> Karena masalah yang diketahui di PowerShell, beberapa aturan penggunaan karakter escape tambahan diberlakukan. Untuk informasi selengkapnya, lihat [Mengutip masalah dengan PowerShell](https://github.com/Azure/azure-cli/blob/dev/doc/quoting-issues-with-powershell.md).

Jika Anda memasukkan argumen yang berisi spasi, apit dengan tanda kutip. Ingat tips berikut:

- Di Bash atau PowerShell, kutipan tunggal dan ganda ditafsirkan. Dalam Windows Command Prompt, hanya tanda kutip ganda yang ditafsirkan. Kutipan tunggal ditafsirkan sebagai bagian dari nilai.

- Untuk perintah khusus Bash, gunakan tanda kutipan tunggal untuk menyederhanakan JSON sebaris. Misalnya, JSON ini benar di Bash: `'{"key": "value"}'`. Dalam Windows Command Prompt, persamaannya adalah: `"{\"key\": \"value\"}"`

- Beberapa perintah Azure CLI mengambil daftar nilai yang dipisahkan spasi. Jika nama kunci atau nilai berisi spasi, apit seluruh pasangan: `"my key=my value"`.

- Bash mengevaluasi kutipan ganda dalam variabel yang diekspor. Jika perilaku ini bukan yang Anda inginkan, hindari variabel: `"\$variable"`.

- Ada karakter khusus PowerShell, seperti di `@`. Untuk menjalankan Azure CLI di PowerShell, tambahkan `` ` `` sebelum karakter khusus untuk mengeluarkannya dari program. Sebagai gantinya, Anda dapat melampirkan nilai dalam tanda kutip tunggal atau ganda `"`/`"`.

  ```azurecli
  `@parameters.json
  '@parameters.json'
  ```

- Jika Anda menggunakan parameter `--query` dengan perintah, beberapa karakter [JMESPath](https://jmespath.org/specification.html) harus dikeluarkan dari program dalam shell.

  Ketiga perintah ini setara dalam Bash:

  ```azurecli
  az version --query '"azure-cli"'
  az version --query \"azure-cli\"
  az version --query "\"azure-cli\""
  ```

  Kedua perintah ini setara dalam Windows Command Prompt:

  ```azurecli
  az version --query "\"azure-cli\""
  az version --query \"azure-cli\"
  ```

  Kelima perintah ini setara dalam PowerShell:

  ```azurecli
  az version --query '\"azure-cli\"'
  az version --query "\`"azure-cli\`""
  az version --query "\""azure-cli\"""
  az --% version --query "\"azure-cli\""
  az --% version --query \"azure-cli\"
  ```

### <a name="use-hyphen-characters-in-arguments"></a>Menggunakan karakter tanda hubung dalam argumen

Jika nilai argumen dimulai dengan tanda hubung, Azure CLI mencoba mengurainya sebagai nama argumen. Untuk mengurainya sebagai nilai, gunakan `=` untuk menggabungkan nama argumen dan nilai: `--password="-VerySecret"`.

## <a name="asynchronous-operations"></a>Operasi Asinkron

Operasi di Azure dapat memakan waktu banyak waktu. Misalnya, mengonfigurasi mesin virtual di pusat data di suatu tempat di dunia tidaklah serta merta. Azure CLI menunggu hingga perintah selesai untuk menerima perintah lain.

Banyak perintah menawarkan parameter `--no-wait`, yang memungkinkan perintah lain dijalankan. Contoh berikut menghapus grup sumber daya:

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

Jika Anda menggunakan Azure CLI melalui server proksi, kesalahan berikut dapat terjadi: `SSLError("bad handshake: Error([('SSL routines', 'tls_process_server_certificate', 'certificate verify failed')],)",)`. Untuk mengatasi kesalahan ini, atur variabel lingkungan `REQUESTS_CA_BUNDLE` ke jalur file sertifikat bundel otoritas sertifikat dalam format PEM.

| OS                     | Bundel otoritas sertifikat default                                                  |
|----------------------- |-------------------------------------------------------------------------------------- |
| Windows                | C:\Program Files (x86)\Microsoft SDKs\Azure\CLI2\Lib\site-packages\certifi\cacert.pem |
| Ubuntu/Debian Linux    | /opt/az/lib/python<version>/site-packages/certifi/cacert.pem                                |
| CentOS/RHEL/SUSE Linux | /usr/lib64/az/lib/python<version>/site-packages/certifi/cacert.pem                          |
| macOS                  | /usr/local/Cellar/azure-cli/<cliversion>/libexec/lib/python<version>/site-packages/certifi/cacert.pem|

Tambahkan sertifikat server proksi ke file ini atau salin kontennya ke file sertifikat lain, lalu atur `REQUESTS_CA_BUNDLE` ke dalamnya. Anda mungkin juga perlu mengatur variabel lingkungan `HTTP_PROXY` atau `HTTPS_PROXY`.

Beberapa proksi memerlukan autentikasi. Format variabel lingkungan `HTTP_PROXY` atau `HTTPS_PROXY` lingkungan harus menyertakan autentikasi, seperti `HTTPS_PROXY="https://username:password@proxy-server:port"`. Untuk mengetahui detailnya, lihat [Cara mengonfigurasi proksi untuk pustaka Azure](/azure/developer/python/azure-sdk-configure-proxy?tabs=bash).

## <a name="concurrent-builds"></a>Build bersamaan

Jika Anda menjalankan Azure CLI di mesin build tempat beberapa pekerjaan dapat dijalankan secara paralel, token akses dapat dibagikan antara dua pekerjaan build yang dijalankan sebagai pengguna OS yang sama.  Untuk menghindari campuran, atur `AZURE_CONFIG_DIR` ke direktori tempat token akses disimpan.

## <a name="generic-update-arguments"></a>Argumen pembaruan generik

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

## <a name="generic-resource-commands"></a>Perintah sumber daya generik

Layanan yang ingin digunakan untuk bekerja mungkin belum memiliki dukungan Azure CLI. Anda dapat menggunakan perintah [az resource](../latest/docs-ref-autogen/resource.yml) untuk bekerja dengan sumber daya ini.

Jika Anda hanya memerlukan perintah buat dan perbarui, gunakan [az deployment group create](/cli/azure/deployment/group#az-deployment-group-create). Sebagai contoh kerja, lihat [Template Mulai Cepat Azure](https://azure.microsoft.com/resources/templates/).

## <a name="rest-api-commands"></a>Perintah REST API

Jika argumen pembaruan generik dan [az resource](../latest/docs-ref-autogen/resource.yml) tidak memenuhi kebutuhan Anda, gunakan perintah [az rest](/cli/azure/reference-index#az-res) untuk memanggil REST API. Perintah secara otomatis melakukan autentikasi menggunakan info masuk dimasukkan dan mengatur header `Content-Type: application/json`. Untuk informasi selengkapnya, lihat [Referensi Azure REST API](/rest/api/azure/).

Contoh ini berfungsi dengan [Microsoft Graph API](/graph/api/overview?toc=./ref/toc.json). Untuk memperbarui URI pengalihan untuk [Aplikasi](/graph/api/resources/application), kita memanggil REST API [Perbarui aplikasi](/graph/api/application-update?tabs=http), seperti dalam kode ini:

```azurecli
# Get the application
az rest --method GET \
    --uri 'https://graph.microsoft.com/v1.0/applications/b4e4d2ab-e2cb-45d5-a31a-98eb3f364001'

# Update `redirectUris` for `web` property
az rest --method PATCH \
    --uri 'https://graph.microsoft.com/v1.0/applications/b4e4d2ab-e2cb-45d5-a31a-98eb3f364001' \
    --body '{"web":{"redirectUris":["https://myapp.com"]}}'
```

## <a name="scripts"></a>Skrip

Gunakan skrip batch Windows ini untuk menyimpan ID ke variabel:

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

Gunakan skrip PowerShell ini untuk menyimpan ID ke variabel:

```powershell
$vm_ids=(az vm list --resource-group VMResources --show-details --query "[?powerState=='VM running'].id" --output tsv)
az vm stop --ids $vm_ids # CLI stops all VMs in parallel
```

Gunakan skrip batch Windows ini untuk menelusuri daftar:

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

Gunakan skrip PowerShell ini untuk mengulang daftar:

```powershell
$vm_ids=(az vm list --resource-group VMResources --show-details --query "[?powerState=='VM running'].id" --output tsv)
foreach ($vm_id in $vm_ids) {
    Write-Output "Stopping $vm_id"
    az vm stop --ids $vm_id
}
```

Berikut adalah variabel lingkungan Azure CLI:

|  Variabel lingkungan          | Deskripsi            |
|--------------------------------|------------------------|
| **AZURE_CONFIG_DIR**           | Direktori global untuk file konfigurasi, log, dan telemetri. Jika tidak ditentukan, nilai default ini diatur ke `~/.azure.` |
| **AZURE_EXTENSION_DIR**        | Direktori yang berisi penginstalan ekstensi. Jika tidak ditentukan, nilai default ini diatur ke sub-direktori `cliextensions` dalam direktori konfigurasi global. |

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

## <a name="next-steps"></a>Langkah berikutnya

- [Menentukan nilai dalam perintah Azure CLI](azure-cli-variables.md)
- [Mengkueri output perintah Azure CLI](query-azure-cli.md)
- [Format output untuk perintah Azure CLI](format-output-azure-cli.md)
- [Menggunakan langganan Azure dengan Azure CLI](manage-azure-subscriptions-azure-cli.md)


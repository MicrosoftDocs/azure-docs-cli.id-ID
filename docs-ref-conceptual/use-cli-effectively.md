---
title: Gunakan Azure CLI secara efektif | Microsoft Docs
description: Pelajari tips untuk menggunakan Azure CLI secara efektif, seperti format output, melewati nilai parameter, dan mengutip aturan untuk shell yang berbeda.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 10/01/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
ms.openlocfilehash: 5986adc5f8c666f1e31df1027f937ebe9c578591
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439081"
---
# <a name="how-to-use-azure-cli-effectively"></a>Cara menggunakan Azure CLI secara efektif

Azure CLI memungkinkan Anda untuk mengkonfigurasi dan mengelola Azure dari Bash, PowerShell, atau jendela Command Prompt. Azure CLI mendukung penggunaan kembali perintah, baik secara ad-hoc maupun melalui skrip. Anda harus menyadari kemampuan shell yang Anda jalankan.

Artikel ini membahas tips berguna tentang cara menggunakan Azure CLI dan cara menghindari jebakan.

[!INCLUDE [azure-cli-prepare-your-environment.md](includes/azure-cli-prepare-your-environment.md)]

Jika Anda memiliki pertanyaan tentang perintah Azure CLI, cari di [Azure CLI Reference](/cli/azure/reference-index).

## <a name="output-formatting"></a>Pemformatan output

Banyak perintah Azure CLI menunjukkan data di konsol. Informasi ini dapat menjadi tujuan perintah, seperti dalam contoh ini, di mana perintah [acara akun az](/cli/azure/account#az_account_show) menunjukkan langganan Anda saat ini:

```azurecli
az account show
```

Terkadang, informasi yang ditampilkan perintah mencerminkan perubahan yang Anda buat. Contoh ini membuat grup sumber daya dengan menggunakan perintah [buat grup az:](/cli/azure/group#az_group_create)

```azurecli
az group create --name MyResourceGroup --location eastus
```

Jika Anda menjalankan perintah ini, konsol Azure CLI menunjukkan kepada Anda grup sumber daya yang baru saja Anda buat.

Anda dapat memilih format untuk output dengan menentukan `--output` parameter. Dalam contoh ini, perintah [daftar akun az](/cli/azure/account#az_account_list) mencantumkan semua langganan yang dapat Anda akses sebagai tabel:

```azurecli
az account list --output table
```

Berikut adalah tiga format umum:

* `json`Format menunjukkan informasi sebagai string JSON. Format ini memberi Anda informasi yang paling komprehensif. Format ini adalah default. Anda dapat mengubah format default dengan menggunakan perintah [konfigurasi az.](/cli/azure/config)
* `table`Format ini menyajikan output sebagai tabel yang dapat dibaca manusia. Anda dapat menentukan nilai mana yang muncul dalam tabel dan menggunakan kueri untuk mengkustomisasi output.
* `tsv`Format mengembalikan nilai yang dipisahkan tab dan memisahkan garis baru tanpa pemformatan tambahan, tombol, atau simbol lainnya.

Untuk informasi selengkapnya tentang format ini dan lainnya, lihat [Format output untuk perintah Azure CLI](format-output-azure-cli.md).

## <a name="pass-values-to-another-command"></a>Meneruskan nilai ke perintah lain

Azure CLI commands run in a shell. Artikel ini menggunakan Bash, tetapi ada opsi lain. Anda dapat menggunakan sintaks shell standar untuk menyederhanakan penggunaan Azure CLI.

Anda dapat menyimpan nilai sebagai variabel. Variabel memungkinkan Anda untuk menggunakan nilai lebih dari sekali atau untuk membuat skrip yang lebih umum. Contoh ini menetapkan ID yang ditemukan oleh perintah [az vm list](/cli/azure/vm#az_vm_list) ke variabel.

```azurecli
running_vm_ids=$(az vm list --resource-group MyResourceGroup --show-details \
   --query "[?powerState=='VM running'].id" --output tsv)
```

> [!TIP]
> Pastikan untuk menggunakan `tsv` tipe output. Jenis output lainnya mungkin berisi simbol yang tidak diinginkan seperti tanda kutip.

Gunakan nilai dalam perintah selanjutnya. Anda dapat memverifikasi nilai dengan menggemakan variabel:

```azurecli
echo $running_vm_ids
```

Anda juga bisa pipa nilai dari satu perintah ke perintah lainnya. Contoh ini menggunakan sintaks Bash standar untuk mencari nilai:

```azurecli
az vm list --query "[?powerState=='VM running'].name" --output tsv | grep my_vm
```

## <a name="pass-arguments"></a>Melewati argumen

### <a name="use-quotation-marks-in-arguments"></a>Menggunakan tanda kutip dalam argumen

Saat Anda bekerja dengan perintah Azure CLI, waspadai bagaimana shell Anda menggunakan tanda kutip dan lolos dari karakter. Jika Anda mendukung skrip yang digunakan dalam shell yang berbeda, Anda perlu memahami bagaimana perbedaannya.

* Bash. [Mengutip](https://www.gnu.org/software/bash/manual/html_node/Quoting.html)
* PowerShell. [Tentang Mengutip Aturan](/powershell/module/microsoft.powershell.core/about/about_quoting_rules)
* Command Prompt Windows. [How-to: Escape Characters, Delimiters dan Quotes di baris perintah Windows](https://ss64.com/nt/syntax-esc.html)

> [!NOTE]
> Karena masalah yang diketahui di PowerShell, beberapa aturan melarikan diri tambahan berlaku. Untuk informasi selengkapnya, lihat [Mengutip masalah dengan PowerShell.](https://github.com/Azure/azure-cli/blob/dev/doc/quoting-issues-with-powershell.md)

Jika Anda memberikan argumen yang berisi spasi putih, bungkus dalam tanda kutip. Ingatlah tips berikut:

* Dalam Bash atau PowerShell, kutipan tunggal dan ganda ditafsirkan. Dalam command prompt Windows, hanya kutipan ganda yang ditafsirkan. Kutipan tunggal ditafsirkan sebagai bagian dari nilai.

* Untuk perintah Bash-only, gunakan kutipan tunggal untuk menyederhanakan JSON inline. Misalnya, JSON ini benar di Bash: `'{"key": "value"}'` . Dalam Command Prompt Windows, yang setara adalah:`"{\"key\": \"value\"}"`

* Beberapa perintah Azure CLI mengambil daftar nilai yang dipisahkan ruang. Jika nama atau nilai kunci berisi spasi, bungkus seluruh `"my key=my value"` pasangan:

* Bash mengevaluasi kutipan ganda dalam variabel yang diekspor. Jika perilaku ini bukan yang Anda inginkan, hindari `"\$variable"` variabelnya:

* Ada karakter khusus PowerShell, seperti di `@` . Untuk menjalankan Azure CLI di PowerShell, tambahkan `` ` `` sebelum karakter khusus untuk melarikan diri darinya. Sebagai gantinya, Anda dapat melampirkan nilai dalam kutipan tunggal atau `"` / `"` ganda.

  ```azurecli
  `@parameters.json
  '@parameters.json'
  ```

* Saat Anda menggunakan `--query` parameter dengan perintah, beberapa karakter [JMESPath](https://jmespath.org/specification.html) perlu lolos di shell.

  Ketiga perintah ini setara dalam Bash:

  ```azurecli
  az version --query '"azure-cli"'
  az version --query \"azure-cli\"
  az version --query "\"azure-cli\""
  ```

  Kedua perintah ini setara dalam command prompt Windows:

  ```azurecli
  az version --query "\"azure-cli\""
  az version --query \"azure-cli\"
  ```

  Kelima perintah ini setara di PowerShell:

  ```azurecli
  az version --query '\"azure-cli\"'
  az version --query "\`"azure-cli\`""
  az version --query "\""azure-cli\"""
  az --% version --query "\"azure-cli\""
  az --% version --query \"azure-cli\"
  ```

### <a name="use-hyphen-characters-in-arguments"></a>Menggunakan karakter tanda hubung dalam argumen

Jika nilai argumen dimulai dengan tanda hubung, Azure CLI mencoba mengurainya sebagai nama argumen. Untuk mengurainya sebagai nilai, gunakan `=` untuk menggabungkan nama dan nilai argumen: `--password="-VerySecret"` .

## <a name="asynchronous-operations"></a>Operasi Asinkron

Operasi di Azure dapat memakan waktu yang cukup lama. Misalnya, mengkonfigurasi mesin virtual di pusat data di suatu tempat di dunia tidak instan. Azure CLI menunggu sampai perintah selesai untuk menerima perintah lainnya.

Banyak perintah menawarkan `--no-wait` parameter, yang memungkinkan perintah lain untuk berjalan. Contoh berikut menghapus grup sumber daya:

```azurecli
az group delete --name MyResourceGroup --no-wait
```

Saat Anda menghapus grup sumber daya, Anda juga menghapus semua sumber daya yang menjadi miliknya. Merebut kembali sumber daya ini bisa memakan waktu lama. `--no-wait`Ketika perintah ini berjalan, konsol dapat menerima perintah segera, meskipun masih bekerja pada perintah.

Banyak perintah menawarkan opsi tunggu, menghentikan konsol sampai beberapa kondisi terpenuhi. Contoh berikut menggunakan perintah [az vm wait](/cli/azure/vm#az_vm_wait) untuk mendukung pembuatan sumber daya independen secara paralel:

```azurecli
az vm create --resource-group VMResources --name virtual-machine-01 --image centos --no-wait
az vm create --resource-group VMResources --name virtual-machine-02 --image centos --no-wait

subscription=$(az account show --query "id" -o tsv)
vm1_id="/subscriptions/$subscription/resourceGroups/VMResources/providers/Microsoft.Compute/virtualMachines/virtual-machine-01"
vm2_id="/subscriptions/$subscription/resourceGroups/VMResources/providers/Microsoft.Compute/virtualMachines/virtual-machine-02"
az vm wait --created --ids $vm1_id $vm2_id
```

Setelah kedua ID dibuat, Anda dapat menggunakan konsol lagi.

## <a name="work-behind-a-proxy"></a>Bekerja di belakang proxy

Jika Anda menggunakan Azure CLI melalui server proxy, itu dapat menyebabkan kesalahan berikut: `SSLError("bad handshake: Error([('SSL routines', 'tls_process_server_certificate', 'certificate verify failed')],)",)` . Untuk mengatasi kesalahan ini, atur variabel lingkungan `REQUESTS_CA_BUNDLE` ke jalur file sertifikat bundel otoritas sertifikat dalam format PEM.

| OS                     | Bundel otoritas sertifikat default                                                  |
|----------------------- |-------------------------------------------------------------------------------------- |
| Windows                | C:\Program Files (x86)\Microsoft SDKs\Azure\CLI2\Lib\site-packages\certifi\cacert.pem |
| Ubuntu/Debian Linux    | /opt/az/lib/python3.6/site-packages/certifi/cacert.pem                                |
| CentOS/RHEL/SUSE Linux | /usr/lib64/az/lib/python3.6/site-packages/certifi/cacert.pem                          |

Tambahkan sertifikat server proxy ke file ini atau salin isinya ke file sertifikat lain, lalu atur `REQUESTS_CA_BUNDLE` ke sana. Anda mungkin juga perlu mengatur `HTTP_PROXY` variabel atau `HTTPS_PROXY` lingkungan.

Beberapa proxy memerlukan otentikasi. Format variabel `HTTP_PROXY` atau `HTTPS_PROXY` lingkungan harus mencakup otentikasi, seperti `HTTPS_PROXY="https://username:password@proxy-server:port"` . Untuk detailnya, lihat [Cara mengonfigurasi proksi untuk pustaka Azure](/azure/developer/python/azure-sdk-configure-proxy?tabs=bash).

## <a name="concurrent-builds"></a>Konkuren membangun

Jika Anda menjalankan Azure CLI pada mesin build di mana beberapa pekerjaan dapat dijalankan secara paralel, token akses dapat dibagi antara dua pekerjaan build yang dijalankan sebagai pengguna OS yang sama.  Untuk menghindari campuran, atur `AZURE_CONFIG_DIR` ke direktori tempat token akses disimpan.

## <a name="generic-update-arguments"></a>Argumen pemutakhiran generik

Grup perintah Azure CLI sering menampilkan perintah pembaruan. Misalnya, [Azure Virtual Machines](/cli/azure/vm) menyertakan perintah [az vm update.](/cli/azure/vm#az_vm_update) Sebagian besar perintah pembaruan menawarkan tiga parameter generik: `--add` , `--set` , dan `--remove` .

Dan parameter mengambil daftar pasangan nilai kunci yang `--set` `--add` dipisahkan ruang: `key1=value1 key2=value2` . Untuk melihat properti apa yang dapat Anda perbarui, gunakan perintah perlihatkan, seperti [az vm show](/cli/azure/vm#az_vm_show).

```azurecli
az vm show --resource-group VMResources --name virtual-machine-01
```

Untuk menyederhanakan perintah, pertimbangkan untuk menggunakan string JSON. Misalnya, untuk melampirkan disk data baru ke mesin virtual, gunakan nilai berikut:

```azurecli
az vm update --resource-group VMResources --name virtual-machine-01 \
--add storageProfile.dataDisks "{\"createOption\": \"Attach\", \"managedDisk\": 
   {\"id\": 
   \"/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/yg/providers/Microsoft.Compute/disks/yg-disk\"}, 
   \"lun\": 1}"
```

## <a name="generic-resource-commands"></a>Perintah sumber daya generik

Layanan yang ingin Anda gunakan mungkin belum memiliki dukungan Azure CLI. Anda dapat menggunakan perintah [sumber daya az](/cli/azure/resource) untuk bekerja dengan sumber daya ini.

Jika Anda hanya perlu membuat atau memperbarui perintah, gunakan [buat grup penyebaran az](/cli/azure/deployment/group#az_deployment_group_create). Untuk contoh kerja, lihat [Templat Azure Quickstart](/resources/templates/).

## <a name="rest-api-commands"></a>Perintah REST API

Jika argumen pembaruan generik dan [sumber daya az](/cli/azure/resource) tidak memenuhi kebutuhan Anda, Anda dapat menggunakan perintah az [rest](/cli/azure/reference-index#az_rest) untuk memanggil API REST. Perintah secara otomatis mengautentikasi menggunakan kredensial masuk dan mengatur `Content-Type: application/json` header. Untuk informasi selengkapnya, lihat [Referensi Azure REST API](/rest/api/azure/).

Contoh ini bekerja dengan [Microsoft Graph API](/graph/api/overview?toc=./ref/toc.json). Untuk memperbarui URI pengalihan untuk [Aplikasi,](/graph/api/resources/application)kami memanggil [aplikasi Pembaruan](/graph/api/application-update?tabs=http) REST API, seperti dalam kode ini:

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

Gunakan skrip batch Windows ini untuk menyimpan KARTU KE variabel:

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

Gunakan skrip Windows PowerShell ini untuk menyimpan ID ke variabel:

```powershell
$vm_ids=(az vm list --resource-group VMResources --show-details --query "[?powerState=='VM running'].id" --output tsv)
az vm stop --ids $vm_ids # CLI stops all VMs in parallel
```

Gunakan skrip batch Windows ini untuk memutar melalui daftar:

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

Gunakan skrip Windows PowerShell ini untuk memutar melalui daftar:

```powershell
$vm_ids=(az vm list --resource-group VMResources --show-details --query "[?powerState=='VM running'].id" --output tsv)
foreach ($vm_id in $vm_ids) {
    Write-Output "Stopping $vm_id"
    az vm stop --ids $vm_id
}
```

Berikut ini adalah variabel lingkungan Azure CLI:

|  Variabel lingkungan          | Deskripsi            |
|--------------------------------|------------------------|
| **AZURE_CONFIG_DIR**           | Direktori global untuk file konfigurasi, log, dan telemetri. Jika tidak ditentukan, nilai ini default ke `~/.azure.` |
| **AZURE_EXTENSION_DIR**        | Direktori yang berisi instalasi ekstensi. Jika tidak ditentukan, nilai ini default ke `cliextensions` subdirektori dalam direktori konfigurasi global. |

## <a name="error-handling-for-azure-cli-in-powershell"></a>Penanganan kesalahan untuk Azure CLI in PowerShell

Anda dapat menjalankan perintah Azure CLI di PowerShell, seperti yang dijelaskan dalam [Pilih alat baris perintah Azure yang tepat](choose-the-right-azure-command-line-tool.md). Jika Anda melakukannya, pastikan Anda memahami penanganan kesalahan Azure CLI di PowerShell. Secara khusus, Azure CLI tidak membuat pengecualian untuk PowerShell untuk menangkap.

Alternatifnya adalah menggunakan `$?` variabel otomatis. Variabel ini berisi status perintah terbaru. Jika perintah sebelumnya gagal, `$?` memiliki nilai `$False` . Untuk informasi lebih lanjut, lihat [about_Automatic_Variables.](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)

Contoh berikut menunjukkan bagaimana variabel otomatis ini dapat bekerja untuk penanganan kesalahan:

```powershell
az group create --name MyResourceGroup 
if ($? -eq $false) {
    Write-Error "Error creating resource group."
}
```

`az`Perintah gagal karena kehilangan parameter yang `--location` diperlukan. Pernyataan bersyarat menemukan bahwa `$?` itu salah dan menulis kesalahan.

Jika Anda ingin menggunakan `try` kata kunci dan kata `catch` kunci, Anda dapat menggunakan untuk membuat `throw` pengecualian untuk blok untuk `try` menangkap:

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

Secara default, PowerShell hanya menangkap kesalahan penghentian. Contoh ini mengatur `$ErrorActionPreference` variabel global `Stop` sehingga PowerShell dapat menangani kesalahan.

Pernyataan bersyarat menguji `$?` variabel untuk melihat apakah perintah sebelumnya gagal. Jika demikian, `throw` kata kunci membuat pengecualian untuk menangkap. `catch`Blok dapat digunakan untuk menulis pesan kesalahan atau menangani kesalahan.

Contohnya mengembalikan `$ErrorActionPreference` ke nilai defaultnya.

Untuk informasi selengkapnya tentang penanganan kesalahan PowerShell, lihat [Semua yang ingin Anda ketahui tentang pengecualian.](/powershell/scripting/learn/deep-dives/everything-about-exceptions)

## <a name="next-steps"></a>Langkah berikutnya

* [Menentukan nilai dalam perintah Azure CLI](azure-cli-variables.md)
* [Output perintah Query Azure CLI](query-azure-cli.md)
* [Format output untuk perintah Azure CLI](format-output-azure-cli.md)
* [Use Azure subscriptions with Azure CLI](manage-azure-subscriptions-azure-cli.md)

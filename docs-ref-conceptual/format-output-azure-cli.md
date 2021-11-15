---
title: Format output - Azure CLI | Microsoft Docs
description: Azure CLI menawarkan berbagai format output seperti JSON dan YAML. Pelajari cara memformat output perintah Azure CLI ke tabel, daftar, atau json.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli commands
ms.openlocfilehash: 685ee84eddeab2e8bf03b5c1fc523e473f98f6bd
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439053"
---
# <a name="output-formats-for-azure-cli-commands"></a>Format output untuk perintah Azure CLI

Azure CLI menggunakan JSON sebagai format output default, tetapi menawarkan format lain.  Gunakan `--output` `--out` parameter `-o` (atau) untuk memformat output CLI. Nilai argumen dan jenis output adalah:

--output | Deskripsi
---------|-------------------------------
`json`   | JSON string. Pengaturan ini adalah default
`jsonc`  | JSON berwarna
`yaml`   | YAML, alternatif yang dapat dibaca manusia untuk JSON
`table`  | Tabel ASCII dengan tombol sebagai judul kolom
`tsv`    | Nilai yang dipisahkan tab, tanpa tombol
`none`   | Tidak ada output selain kesalahan dan peringatan

## <a name="json-output-format"></a>Format output JSON

Contoh berikut menampilkan daftar mesin virtual dalam langganan Anda dalam format JSON default.

```azurecli-interactive
az vm list --output json
```

Output berikut memiliki beberapa bidang dihilangkan untuk singkatnya, dan mengidentifikasi informasi diganti.

```json
[
  {
    "availabilitySet": null,
    "diagnosticsProfile": null,
    "hardwareProfile": {
      "vmSize": "Standard_DS1"
    },
    "id": "/subscriptions/.../resourceGroups/DEMORG1/providers/Microsoft.Compute/virtualMachines/DemoVM010",
    "instanceView": null,
    "licenseType": null,
    "location": "westus",
    "name": "DemoVM010",
    "networkProfile": {
      "networkInterfaces": [
        {
          "id": "/subscriptions/.../resourceGroups/demorg1/providers/Microsoft.Network/networkInterfaces/DemoVM010VMNic",
          "primary": null,
          "resourceGroup": "demorg1"
        }
      ]
    },
          ...
          ...
          ...
]
```

## <a name="yaml-output-format"></a>Format output YAML

`yaml`Format mencetak output sebagai [YAML,](http://yaml.org/)format serialisasi data teks biasa. YAML cenderung lebih mudah dibaca daripada JSON, dan dengan mudah memetakan ke format itu. Beberapa aplikasi dan perintah CLI mengambil YAML sebagai input konfigurasi, bukan JSON.

```azurecli-interactive
az vm list --out yaml
```

Output berikut memiliki beberapa bidang dihilangkan untuk singkatnya, dan mengidentifikasi informasi diganti.

```yaml
- availabilitySet: null
  diagnosticsProfile: null
  hardwareProfile:
    vmSize: Standard_DS1_v2
  id: /subscriptions/.../resourceGroups/DEMORG1/providers/Microsoft.Compute/virtualMachines/DemoVM010
  identity: null
  instanceView: null
  licenseType: null
  location: westus
  name: ExampleVM1
  networkProfile:
    networkInterfaces:
    - id: /subscriptions/.../resourceGroups/DemoRG1/providers/Microsoft.Network/networkInterfaces/DemoVM010Nic
      primary: null
      resourceGroup: DemoRG1
  ...
...
```

## <a name="table-output-format"></a>Format output tabel

`table`Format mencetak output sebagai tabel ASCII, sehingga mudah dibaca dan dipindai. Objek bertumpuk tidak termasuk dalam output tabel, tetapi masih dapat difilter sebagai bagian dari kueri. Beberapa bidang tidak termasuk dalam tabel, jadi format ini adalah yang terbaik ketika Anda menginginkan gambaran data yang cepat dan dapat dicari manusia.

```azurecli-interactive
az vm list --out table
```

```output
Name         ResourceGroup    Location
-----------  ---------------  ----------
DemoVM010    DEMORG1          westus
demovm212    DEMORG1          westus
demovm213    DEMORG1          westus
KBDemo001VM  RGDEMO001        westus
KBDemo020    RGDEMO001        westus
```

Anda dapat menggunakan `--query` parameter untuk mengkustomisasi properti dan kolom yang ingin Anda tampilkan dalam output daftar. Contoh berikut menunjukkan cara memilih hanya Nama VM dan Nama Grup Sumber Daya dalam `list` perintah.

```azurecli-interactive
az vm list --query "[].{resource:resourceGroup, name:name}" -o table
```

```output
Resource    Name
----------  -----------
DEMORG1     DemoVM010
DEMORG1     demovm212
DEMORG1     demovm213
RGDEMO001   KBDemo001VM
RGDEMO001   KBDemo020
```

> [!NOTE]
> Beberapa tombol tidak dicetak dalam tampilan tabel secara default. Mereka `id` adalah, `type` `etag` dan. Jika Anda perlu melihat ini dalam output Anda, Anda dapat menggunakan fitur re-keying JMESPath untuk mengubah nama kunci dan menghindari penyaringan.
>
> ```azurecli-interactive
> az vm list --query "[].{objectID:id}" -o table
> ```

Untuk selengkapnya tentang menggunakan kueri untuk memfilter data, lihat [Menggunakan kueri JMESPath dengan Azure CLI](./query-azure-cli.md).

## <a name="tsv-output-format"></a>Format output TSV

`tsv`Format output mengembalikan nilai tab dan newline-separated tanpa pemformatan tambahan, tombol, atau simbol lainnya. Format ini memudahkan untuk mengkonsumsi output ke dalam perintah dan alat lain yang perlu memproses teks dalam beberapa bentuk. Seperti `table` formatnya, `tsv` tidak mencetak objek bertumpuk.

Menggunakan contoh sebelumnya dengan `tsv` opsi output hasil tab-separated.

```azurecli-interactive
az vm list --out tsv
```

```output
None    None        /subscriptions/.../resourceGroups/DEMORG1/providers/Microsoft.Compute/virtualMachines/DemoVM010    None    None    westus    DemoVM010            None    Succeeded    DEMORG1    None            Microsoft.Compute/virtualMachines    cbd56d9b-9340-44bc-a722-25f15b578444
None    None        /subscriptions/.../resourceGroups/DEMORG1/providers/Microsoft.Compute/virtualMachines/demovm212    None    None    westus    demovm212            None    Succeeded    DEMORG1    None            Microsoft.Compute/virtualMachines    4bdac85d-c2f7-410f-9907-ca7921d930b4
None    None        /subscriptions/.../resourceGroups/DEMORG1/providers/Microsoft.Compute/virtualMachines/demovm213    None    None    westus    demovm213            None    Succeeded    DEMORG1    None            Microsoft.Compute/virtualMachines    2131c664-221a-4b7f-9653-f6d542fbfa34
None    None        /subscriptions/.../resourceGroups/RGDEMO001/providers/Microsoft.Compute/virtualMachines/KBDemo001VM    None    None    westus    KBDemo001VM            None    Succeeded    RGDEMO001    None            Microsoft.Compute/virtualMachines    14e74761-c17e-4530-a7be-9e4ff06ea74b
None    None        /subscriptions/.../resourceGroups/RGDEMO001/providers/Microsoft.Compute/virtualMachines/KBDemo020   None    None    westus    KBDemo020            None    Succeeded    RGDEMO001    None            Microsoft.Compute/virtualMachines    36baa9-9b80-48a8-b4a9-854c7a858ece
```

Salah satu pembatasan format output TSV adalah bahwa tidak ada jaminan pada pemesanan output. CLI melakukan upaya terbaik untuk menjaga pemesanan dengan menyortir kunci dalam respons JSON menurut abjad, dan kemudian mencetak nilai-nilainya agar output TSV. Ini bukan jaminan bahwa pesanan selalu identik, karena format respons layanan Azure dapat berubah.

Untuk menegakkan pemesanan yang konsisten, Anda harus menggunakan `--query` parameter dan format daftar [multiselect.](query-azure-cli.md#get-multiple-values) Ketika perintah CLI mengembalikan kamus JSON tunggal, gunakan format umum `[key1, key2, ..., keyN]` untuk memaksa urutan kunci.  Untuk perintah CLI yang mengembalikan array, gunakan format umum `[].[key1, key2, ..., keyN]` untuk memesan nilai kolom.

Misalnya, untuk memesan informasi yang ditampilkan di atas berdasarkan ID, lokasi, grup sumber daya, dan nama VM:

```azurecli-interactive
az vm list --out tsv --query '[].[id, location, resourceGroup, name]'
```

```output
/subscriptions/.../resourceGroups/DEMORG1/providers/Microsoft.Compute/virtualMachines/DemoVM010    westus    DEMORG1    DemoVM010
/subscriptions/.../resourceGroups/DEMORG1/providers/Microsoft.Compute/virtualMachines/demovm212    westus    DEMORG1    demovm212
/subscriptions/.../resourceGroups/DEMORG1/providers/Microsoft.Compute/virtualMachines/demovm213    westus    DEMORG1    demovm213
/subscriptions/.../resourceGroups/RGDEMO001/providers/Microsoft.Compute/virtualMachines/KBDemo001VM     westus  RGDEMO001       KBDemo001VM
/subscriptions/.../resourceGroups/RGDEMO001/providers/Microsoft.Compute/virtualMachines/KBDemo020       westus  RGDEMO001       KBDemo020
```

Contoh berikutnya menunjukkan bagaimana `tsv` output dapat disalurkan ke perintah lain dalam bash. Kueri digunakan untuk memfilter output dan urutan gaya, `grep` memilih item yang memiliki teks "RGD" di dalamnya, lalu perintah memilih bidang keempat untuk menampilkan nama VM dalam `cut` output.

```azurecli-interactive
az vm list --out tsv --query '[].[id, location, resourceGroup, name]' | grep RGD | cut -f4
```

```output
KBDemo001VM
KBDemo020
```

## <a name="set-the-default-output-format"></a>Mengatur format output default

Gunakan `az config set` perintah untuk mengatur lingkungan Anda dan menetapkan pengaturan default untuk format output. Format output default adalah `json` .

```azurecli
az config set core.output=<format>
```

```output
Welcome to the Azure CLI! This command will guide you through logging in and setting some default values.

Your settings can be found at /home/defaultuser/.azure/config
Your current configuration is as follows:

  ...

Do you wish to change your settings? (y/N): y

What default output format would you like?
 [1] json - JSON formatted output that most closely matches API responses.
 [2] jsonc - Colored JSON formatted output that most closely matches API responses.
 [3] table - Human-readable output format.
 [4] tsv - Tab- and Newline-delimited. Great for GREP, AWK, etc.
 [5] yaml - YAML formatted output. An alternative to JSON. Great for configuration files.
 [6] none - No output, except for errors and warnings.
Please enter a choice [1]:
```

Untuk mempelajari selengkapnya tentang mengonfigurasi lingkungan Anda, lihat [konfigurasi Azure CLI](./azure-cli-configuration.md).

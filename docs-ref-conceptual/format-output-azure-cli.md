---
title: Format output - Azure CLI | Microsoft Docs
description: Azure CLI menawarkan berbagai format output seperti JSON dan YAML. Pelajari cara memformat output perintah Azure CLI ke tabel, daftar, atau json.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 11/11/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: perintah azure cli
ms.openlocfilehash: be163b4355f8bcb6b23ba54ba8078a9762abe433
ms.sourcegitcommit: 30e08311cdf7da0ca3107ce8e802128615b2345b
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 11/17/2021
ms.locfileid: "132729659"
---
# <a name="output-formats-for-azure-cli-commands"></a>Format output untuk perintah Azure CLI

Azure CLI menggunakan JSON sebagai format output default-nya, tetapi menawarkan format lain.  Gunakan parameter `--output` (`--out` atau `-o`) untuk memformat output CLI. Nilai argumen dan jenis output-nya adalah:

--output | Deskripsi
---------|-------------------------------
`json`   | String JSON. Ini adalah pengaturan default
`jsonc`  | JSON berwarna
`yaml`   | YAML, alternatif yang dapat dibaca manusia untuk JSON
`yamlc`  | YAML berwarna
`table`  | Tabel ASCII dengan kunci sebagai judul kolom
`tsv`    | Nilai yang dipisahkan tab, tanpa kunci
`none`   | Tidak ada output lain selain kesalahan dan peringatan

## <a name="json-output-format"></a>Format output JSON

Contoh berikut menampilkan daftar mesin virtual dalam langganan Anda dalam format JSON default.

```azurecli-interactive
az vm list --output json
```

Untuk mempersingkat, beberapa bidang pada output berikut dihilangkan, informasi yang diganti diidentifikasi.

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

Format `yaml` mencetak output sebagai [YAML](http://yaml.org/), format serialisasi data teks biasa. YAML cenderung lebih mudah dibaca daripada JSON, dan dipetakan dengan mudah ke format tersebut. Beberapa aplikasi dan perintah CLI menggunakan YAML sebagai input konfigurasi, bukan JSON.

```azurecli-interactive
az vm list --out yaml
```

Untuk mempersingkat, beberapa bidang pada output berikut dihilangkan, informasi yang diganti diidentifikasi.

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

Format `table` mencetak output sebagai tabel ASCII, sehingga mudah dibaca dan dipindai. Objek bersarang tidak disertakan dalam output tabel, namun masih dapat difilter sebagai bagian dari kueri. Beberapa bidang tidak disertakan dalam tabel, jadi ini adalah format terbaik jika Anda menginginkan ringkasan data yang cepat dan dapat dicari manusia.

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

Anda dapat menggunakan parameter `--query` untuk menyesuaikan properti dan kolom yang ingin ditampilkan dalam output daftar. Contoh berikut menunjukkan cara memilih Nama VM dan Nama Grup Sumber Daya saja dalam perintah `list`.

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
> Secara default, beberapa kunci tidak dicetak dalam tampilan tabel. Kunci tersebut adalah `id`, `type`, dan `etag`. Jika ingin melihatnya di output, Anda dapat menggunakan fitur penentuan ulang kunci JMESPath untuk mengubah nama kunci dan menghindari pemfilteran.
>
> ```azurecli-interactive
> az vm list --query "[].{objectID:id}" -o table
> ```

Untuk informasi tentang cara menggunakan kueri untuk memfilter data, lihat [Menggunakan kueri JMESPath dengan Azure CLI](./query-azure-cli.md).

## <a name="tsv-output-format"></a>Format output TSV

Format output `tsv` menampilkan nilai yang dipisahkan tab dan baris baru tanpa pemformatan tambahan, kunci, atau simbol lainnya. Format ini memudahkan penggunaan output ke dalam perintah dan alat lain yang perlu memproses teks dalam beberapa bentuk. Seperti halnya format `table`, `tsv` tidak mencetak objek bersarang.

Penggunaan contoh sebelumnya dengan opsi `tsv` akan menghasilkan hasil yang dipisahkan tab.

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

Salah satu batasan format output TSV adalah bahwa pengurutan output tidak bisa dijamin. CLI melakukan upaya terbaik untuk menjaga pengurutan dengan menyortir kunci dalam JSON respons menurut abjad, dan kemudian mencetak nilainya secara berurutan untuk output TSV. Hal ini bukan jaminan bahwa urutannya selalu identik, karena format respons layanan Azure bisa berubah.

Untuk menerapkan pengurutan yang konsisten, Anda harus menggunakan parameter `--query` dan format [daftar multi-pilihan](query-azure-cli.md#get-multiple-values). Jika perintah CLI menampilkan satu kamus JSON, gunakan format umum `[key1, key2, ..., keyN]` untuk memaksa urutan kunci.  Untuk perintah CLI yang menampilkan larik, gunakan format umum `[].[key1, key2, ..., keyN]` untuk mengurutkan nilai kolom.

Misalnya, untuk mengurutkan informasi yang ditampilkan di atas berdasarkan ID, lokasi, grup sumber daya, dan nama VM:

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

Contoh berikutnya menunjukkan bagaimana output `tsv` dapat dialirkan ke perintah lain dalam bash. Kueri digunakan untuk memfilter output dan memaksa pengurutan, `grep` memilih item yang memiliki teks "RGD" di dalamnya, lalu perintah `cut` memilih bidang keempat untuk menampilkan nama VM dalam output.

```azurecli-interactive
az vm list --out tsv --query '[].[id, location, resourceGroup, name]' | grep RGD | cut -f4
```

```output
KBDemo001VM
KBDemo020
```

## <a name="set-the-default-output-format"></a>Menetapkan format output default

Gunakan perintah `az config set` untuk menyiapkan lingkungan Anda dan menetapkan pengaturan default untuk format output. Format output default-nya adalah `json`.

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
 [6] yamlc - Colored YAML formatted output. An alternative to JSON. Great for configuration files.
 [7] none - No output, except for errors and warnings.
Please enter a choice [1]:
```

Untuk mempelajari lebih lanjut cara mengonfigurasi lingkungan, lihat [Konfigurasi Azure CLI](./azure-cli-configuration.md).

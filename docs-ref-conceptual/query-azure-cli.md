---
title: Hasil perintah kueri JMESPath dengan Azure CLI | Microsoft Dokumen
description: Azure CLI menggunakan argumen --query untuk menjalankan kueri JMESPath pada hasil perintah. Pelajari cara menggunakan fitur JMESPath di artikel ini.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: ''
ms.openlocfilehash: 3203b0204f4495f4590be549abc19ad1903f93ed
ms.sourcegitcommit: 766c21c494eb7fbdc5160c437868c187c0b6e587
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 02/17/2022
ms.locfileid: "138934616"
---
# <a name="how-to-query-azure-cli-command-output-using-a-jmespath-query"></a>Cara mengkueri output perintah Azure CLI menggunakan kueri JMESPath

Azure CLI menggunakan `--query` argumen untuk menjalankan [kueri JMESPath](http://jmespath.org) pada hasil perintah. JMESPath adalah bahasa kueri untuk JSON, memberi Anda kemampuan untuk memilih dan memodifikasi data dari output CLI. Kueri dijalankan pada output JSON sebelum pemformatan tampilan apa pun.

Argumen ini `--query` didukung oleh semua perintah di Azure CLI. Artikel ini membahas cara menggunakan fitur JMESPath dengan serangkaian contoh kecil dan sederhana.

> [!NOTE]
>
> Saat menggunakan Azure CLI di PowerShell pada Windows, beberapa pelarian tambahan mungkin diperlukan untuk argumen kueri. Silakan lihat [Mengutip masalah dengan PowerShell](https://github.com/Azure/azure-cli/blob/dev/doc/quoting-issues-with-powershell.md) untuk lebih jelasnya.

## <a name="dictionary-and-list-cli-results"></a>Kamus dan daftar hasil CLI

Bahkan saat menggunakan format output selain JSON, hasil perintah CLI pertama kali diperlakukan sebagai JSON untuk kueri. Hasil CLI adalah array JSON atau kamus. Array adalah urutan objek yang dapat diindeks, dan kamus adalah objek yang tidak diurutkan yang diakses dengan kunci. Perintah yang _dapat_ mengembalikan lebih dari satu objek mengembalikan array, dan perintah yang _selalu_ _mengembalikan hanya_ satu objek mengembalikan kamus.

## <a name="get-properties-in-a-dictionary"></a>Mendapatkan properti dalam kamus

Bekerja dengan hasil kamus, Anda dapat mengakses properti dari tingkat atas hanya dengan kuncinya. Karakter `.` (__sub ekspresi__) digunakan untuk mengakses properti kamus bersarang. Sebelum memperkenalkan kueri, lihat output perintah yang `az vm show` tidak dimodifikasi:

```azurecli-interactive
az vm show -g QueryDemo -n TestVM -o json
```

Perintah akan menghasilkan kamus. Beberapa konten telah dihilangkan.

```json
{
  "additionalCapabilities": null,
  "availabilitySet": null,
  "diagnosticsProfile": {
    "bootDiagnostics": {
      "enabled": true,
      "storageUri": "https://xxxxxx.blob.core.windows.net/"
    }
  },
  ...
  "osProfile": {
    "adminPassword": null,
    "adminUsername": "azureuser",
    "allowExtensionOperations": true,
    "computerName": "TestVM",
    "customData": null,
    "linuxConfiguration": {
      "disablePasswordAuthentication": true,
      "provisionVmAgent": true,
      "ssh": {
        "publicKeys": [
          {
            "keyData": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDMobZNJTqgjWn/IB5xlilvE4Y+BMYpqkDnGRUcA0g9BYPgrGSQquCES37v2e3JmpfDPHFsaR+CPKlVr2GoVJMMHeRcMJhj50ZWq0hAnkJBhlZVWy8S7dwdGAqPyPmWM2iJDCVMVrLITAJCno47O4Ees7RCH6ku7kU86b1NOanvrNwqTHr14wtnLhgZ0gQ5GV1oLWvMEVg1YFMIgPRkTsSQKWCG5lLqQ45aU/4NMJoUxGyJTL9i8YxMavaB1Z2npfTQDQo9+womZ7SXzHaIWC858gWNl9e5UFyHDnTEDc14hKkf1CqnGJVcCJkmSfmrrHk/CkmF0ZT3whTHO1DhJTtV stramer@contoso",
            "path": "/home/azureuser/.ssh/authorized_keys"
          }
        ]
      }
    },
    "secrets": [],
    "windowsConfiguration": null
  },
  ....
}
```

Perintah berikut mendapatkan kunci publik SSH yang diizinkan untuk terhubung ke VM dengan menambahkan kueri:

```azurecli-interactive
az vm show -g QueryDemo -n TestVM --query osProfile.linuxConfiguration.ssh.publicKeys -o json
```

```json
[
  {
    "keyData": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDMobZNJTqgjWn/IB5xlilvE4Y+BMYpqkDnGRUcA0g9BYPgrGSQquCES37v2e3JmpfDPHFsaR+CPKlVr2GoVJMMHeRcMJhj50ZWq0hAnkJBhlZVWy8S7dwdGAqPyPmWM2iJDCVMVrLITAJCno47O4Ees7RCH6ku7kU86b1NOanvrNwqTHr14wtnLhgZ0gQ5GV1oLWvMEVg1YFMIgPRkTsSQKWCG5lLqQ45aU/4NMJoUxGyJTL9i8YxMavaB1Z2npfTQDQo9+womZ7SXzHaIWC858gWNl9e5UFyHDnTEDc14hKkf1CqnGJVcCJkmSfmrrHk/CkmF0ZT3whTHO1DhJTtV stramer@contoso",
    "path": "/home/azureuser/.ssh/authorized_keys"
  }
]
```

## <a name="get-a-single-value"></a>Mendapatkan nilai tunggal

Kasus umum adalah Anda hanya perlu mendapatkan _satu_ nilai dari perintah CLI, seperti ID sumber daya Azure, nama sumber daya, nama pengguna, atau kata sandi. Dalam hal ini, Anda juga sering ingin menyimpan nilai dalam variabel lingkungan lokal. Untuk mendapatkan satu properti, pertama-tama pastikan Anda hanya mendapatkan satu properti dari kueri. Memodifikasi contoh terakhir untuk hanya mendapatkan nama pengguna admin:

```azurecli-interactive
az vm show -g QueryDemo -n TestVM --query "osProfile.adminUsername" -o json
```

```JSON
"azureuser"
```

Ini terlihat seperti nilai tunggal yang valid, tetapi perhatikan bahwa `"` karakter dikembalikan sebagai bagian dari output. Ini menunjukkan bahwa objek tersebut adalah string JSON. Penting untuk dicatat bahwa ketika Anda menetapkan nilai ini secara langsung sebagai output dari perintah ke variabel lingkungan, kutipan mungkin __tidak__ ditafsirkan oleh shell:

```azurecli
USER=$(az vm show -g QueryDemo -n TestVM --query 'osProfile.adminUsername' -o json)
echo $USER
```

```output
"azureuser"
```

Ini hampir pasti bukan yang Anda inginkan. Dalam hal ini, Anda ingin menggunakan format output yang tidak melampirkan nilai yang dikembalikan dengan informasi tipe. Opsi output terbaik yang ditawarkan CLI untuk tujuan ini adalah `tsv`, nilai yang dipisahkan tab. Secara khusus, saat mengambil nilai yang hanya satu nilai (bukan kamus atau daftar), `tsv` output dijamin tidak dikutip.

```azurecli-interactive
az vm show -g QueryDemo -n TestVM --query "osProfile.adminUsername" -o tsv
```

```output
azureuser
```

Untuk informasi selengkapnya `tsv` tentang format output, lihat [Format output - format output TSV](format-output-azure-cli.md#tsv-output-format)

## <a name="query-boolean-values"></a>Nilai Query Boolean

Query nilai Boolean sedikit berbeda.  Ada dua opsi:

```azurecli
# Boolean values are assumed to be true, so this syntax returns the current default subscription.
az account list --query "[?isDefault]"

# If you want a false value, use an escape character.
az account list --query "[?isDefault == ``false``]"
```

## <a name="get-multiple-values"></a>Mendapatkan beberapa nilai

Untuk mendapatkan lebih dari satu properti, letakkan ekspresi dalam tanda kurung  `[ ]` siku ( __daftar multiselek__) sebagai daftar yang dipisahkan koma. Untuk mendapatkan nama VM, pengguna admin, dan kunci SSH sekaligus gunakan perintah:

```azurecli-interactive
az vm show -g QueryDemo -n TestVM --query '[name, osProfile.adminUsername, osProfile.linuxConfiguration.ssh.publicKeys[0].keyData]' -o json
```

```json
[
  "TestVM",
  "azureuser",
  "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDMobZNJTqgjWn/IB5xlilvE4Y+BMYpqkDnGRUcA0g9BYPgrGSQquCES37v2e3JmpfDPHFsaR+CPKlVr2GoVJMMHeRcMJhj50ZWq0hAnkJBhlZVWy8S7dwdGAqPyPmWM2iJDCVMVrLITAJCno47O4Ees7RCH6ku7kU86b1NOanvrNwqTHr14wtnLhgZ0gQ5GV1oLWvMEVg1YFMIgPRkTsSQKWCG5lLqQ45aU/4NMJoUxGyJTL9i8YxMavaB1Z2npfTQDQo9+womZ7SXzHaIWC858gWNl9e5UFyHDnTEDc14hKkf1CqnGJVcCJkmSfmrrHk/CkmF0ZT3whTHO1DhJTtV stramer@contoso"
]
```

Nilai-nilai ini tercantum dalam array hasil dalam urutan yang diberikan dalam kueri. Karena hasilnya adalah array, tidak ada kunci yang terkait dengan hasilnya.

## <a name="rename-properties-in-a-query"></a>Mengganti nama properti dalam kueri

Untuk mendapatkan kamus alih-alih array saat kueri untuk beberapa nilai, gunakan `{ }` operator (__hash multiselect__).
Format untuk hash multiselect adalah `{displayName:JMESPathExpression, ...}`.
`displayName` akan menjadi string yang ditampilkan dalam output, dan `JMESPathExpression` merupakan ekspresi JMESPath untuk dievaluasi. Memodifikasi contoh dari bagian terakhir dengan mengubah daftar multiselect ke hash:

```azurecli-interactive
az vm show -g QueryDemo -n TestVM --query "{VMName:name, admin:osProfile.adminUsername, sshKey:osProfile.linuxConfiguration.ssh.publicKeys[0].keyData }" -o json
```

```json
{
  "VMName": "TestVM",
  "admin": "azureuser",
  "ssh-key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDMobZNJTqgjWn/IB5xlilvE4Y+BMYpqkDnGRUcA0g9BYPgrGSQquCES37v2e3JmpfDPHFsaR+CPKlVr2GoVJMMHeRcMJhj50ZWq0hAnkJBhlZVWy8S7dwdGAqPyPmWM2iJDCVMVrLITAJCno47O4Ees7RCH6ku7kU86b1NOanvrNwqTHr14wtnLhgZ0gQ5GV1oLWvMEVg1YFMIgPRkTsSQKWCG5lLqQ45aU/4NMJoUxGyJTL9i8YxMavaB1Z2npfTQDQo9+womZ7SXzHaIWC858gWNl9e5UFyHDnTEDc14hKkf1CqnGJVcCJkmSfmrrHk/CkmF0ZT3whTHO1DhJTtV stramer@contoso"
}
```

## <a name="get-properties-in-an-array"></a>Mendapatkan properti dalam array

Array tidak memiliki sifat sendiri, tetapi dapat diindeks. Fitur ini ditampilkan pada contoh terakhir dengan ekspresi `publicKeys[0]`, yang mendapat elemen pertama dari `publicKeys` array. Tidak ada jaminan output CLI dipesan, jadi hindari menggunakan pengindeksan kecuali Anda yakin dengan pesanan atau tidak peduli elemen apa yang Anda dapatkan. Untuk mengakses properti elemen dalam array, Anda melakukan salah satu dari dua operasi: _perataan_ dan _penyaringan_. Bagian ini mencakup cara meratakan array.

Meratakan array dilakukan dengan `[]` operator JMESPath. Semua ekspresi setelah `[]` operator diterapkan ke setiap elemen dalam array saat ini.
Jika `[]` muncul di awal kueri, kueri akan meratakan hasil perintah CLI. Hasil dapat `az vm list` diperiksa dengan fitur ini.
Untuk mendapatkan nama, OS, dan nama administrator untuk setiap VM dalam grup sumber daya:

```azurecli-interactive
az vm list -g QueryDemo --query "[].{Name:name, OS:storageProfile.osDisk.osType, admin:osProfile.adminUsername}" -o json
```

```json
[
  {
    "Name": "Test-2",
    "OS": "Linux",
    "admin": "sttramer"
  },
  {
    "Name": "TestVM",
    "OS": "Linux",
    "admin": "azureuser"
  },
  {
    "Name": "WinTest",
    "OS": "Windows",
    "admin": "winadmin"
  }
]
```

Ketika dikombinasikan dengan `--output table` format output, nama kolom cocok dengan `displayKey` nilai hash multiselect:

```azurecli-interactive
az vm list -g QueryDemo --query "[].{Name:name, OS:storageProfile.osDisk.osType, Admin:osProfile.adminUsername}" --output table
```

```output
Name     OS       Admin
-------  -------  ---------
Test-2   Linux    sttramer
TestVM   Linux    azureuser
WinTest  Windows  winadmin
```

> [!NOTE]
>
> Tombol tertentu difilter dan tidak dicetak dalam tampilan tabel. Kunci-kunci ini adalah `id`, `type`, dan `etag`. Untuk melihat nilai-nilai ini, Anda dapat mengubah nama kunci dalam hash multiselect.
>
> ```azurecli-interactive
> az vm show -g QueryDemo -n TestVM --query "{objectID:id}" -o table
> ```

Array apa pun dapat diratakan, bukan hanya hasil tingkat atas yang dikembalikan oleh perintah. Pada bagian terakhir, ekspresi `osProfile.linuxConfiguration.ssh.publicKeys[0].keyData` digunakan untuk mendapatkan kunci publik SSH untuk masuk. Untuk mendapatkan _setiap_ kunci publik SSH, ekspresinya bisa ditulis sebagai `osProfile.linuxConfiguration.ssh.publicKeys[].keyData`.
Ekspresi kueri ini meratakan `osProfile.linuxConfiguration.ssh.publicKeys` array, lalu menjalankan `keyData` ekspresi pada setiap elemen:

```azurecli-interactive
az vm show -g QueryDemo -n TestVM --query "{VMName:name, admin:osProfile.adminUsername, sshKeys:osProfile.linuxConfiguration.ssh.publicKeys[].keyData }" -o json
```

```json
{
  "VMName": "TestVM",
  "admin": "azureuser",
  "sshKeys": [
    "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDMobZNJTqgjWn/IB5xlilvE4Y+BMYpqkDnGRUcA0g9BYPgrGSQquCES37v2e3JmpfDPHFsaR+CPKlVr2GoVJMMHeRcMJhj50ZWq0hAnkJBhlZVWy8S7dwdGAqPyPmWM2iJDCVMVrLITAJCno47O4Ees7RCH6ku7kU86b1NOanvrNwqTHr14wtnLhgZ0gQ5GV1oLWvMEVg1YFMIgPRkTsSQKWCG5lLqQ45aU/4NMJoUxGyJTL9i8YxMavaB1Z2npfTQDQo9+womZ7SXzHaIWC858gWNl9e5UFyHDnTEDc14hKkf1CqnGJVcCJkmSfmrrHk/CkmF0ZT3whTHO1DhJTtV stramer@contoso\n"
  ]
}
```

## <a name="filter-arrays"></a>Memfilter array

Operasi lain yang digunakan untuk mendapatkan data dari array adalah _penyaringan_. Penyaringan dilakukan dengan `[?...]` operator JMESPath.
Operator ini mengambil predikat sebagai isinya. Predikat adalah pernyataan apa pun yang dapat dievaluasi untuk salah satu `true` atau `false`. Ekspresi di mana predikat mengevaluasi untuk `true` dimasukkan dalam output.

JMESPath menawarkan perbandingan standar dan operator logis. Ini termasuk `<`, `<=`, `>`, `>=`, `==`dan `!=`.
JMESPath juga mendukung logis dan (`&&`), atau (`||`), dan tidak (`!`). Ekspresi dapat dikelompokkan dalam tanda kurung, memungkinkan ekspresi predikat yang lebih kompleks. Untuk detail lengkap tentang predikat dan operasi logis, lihat [spesifikasi JMESPath](http://jmespath.org/specification.html).

Di bagian terakhir, kami meratakan array untuk mendapatkan daftar lengkap semua VM dalam grup sumber daya. Menggunakan filter, output ini dapat dibatasi hanya untuk VM Linux:

```azurecli-interactive
az vm list -g QueryDemo --query "[?storageProfile.osDisk.osType=='Linux'].{Name:name,  admin:osProfile.adminUsername}" --output table
```

```output
Name    Admin
------  ---------
Test-2  sttramer
TestVM  azureuser
```

> [!IMPORTANT]
>
> Dalam JMESPath, string selalu dikelilingi oleh kutipan tunggal (`'`). Jika Anda menggunakan tanda kutip ganda sebagai bagian dari string dalam predikat filter, Anda akan mendapatkan output kosong.

JMESPath juga memiliki fungsi bawaan yang dapat membantu penyaringan. Salah satu fungsi tersebut adalah `? contains(string, substring)`, yang memeriksa untuk melihat apakah string berisi substring. Ekspresi dievaluasi sebelum memanggil fungsi, sehingga argumen pertama dapat menjadi ekspresi JMESPath penuh. Contoh berikutnya menemukan semua VM menggunakan penyimpanan SSD untuk disk OS mereka:

```azurecli-interactive
az vm list -g QueryDemo --query "[? contains(storageProfile.osDisk.managedDisk.storageAccountType,'SSD')].{Name:name, Storage:storageProfile.osDisk.managedDisk.storageAccountType}" -o json
```

```json
[
  {
    "Name": "TestVM",
    "Storage": "StandardSSD_LRS"
  },
  {
    "Name": "WinTest",
    "Storage": "StandardSSD_LRS"
  }
]
```

Kueri ini agak panjang. Kunci `storageProfile.osDisk.managedDisk.storageAccountType` disebutkan dua kali, dan rekeyed dalam output. Salah satu cara untuk mempersingkatnya adalah dengan menerapkan filter setelah meratakan dan memilih data.

```azurecli-interactive
az vm list -g QueryDemo --query "[].{Name:name, Storage:storageProfile.osDisk.managedDisk.storageAccountType}[? contains(Storage,'SSD')]" -o json
```

```json
[
  {
    "Name": "TestVM",
    "Storage": "StandardSSD_LRS"
  },
  {
    "Name": "WinTest",
    "Storage": "StandardSSD_LRS"
  }
]
```

Untuk array besar, mungkin lebih cepat untuk menerapkan filter sebelum memilih data.

Lihat [spesifikasi JMESPath - Fungsi Bawaan](http://jmespath.org/specification.html#built-in-functions) untuk daftar lengkap fungsi.

## <a name="change-output"></a>Mengubah output

Fungsi JMESPath juga memiliki tujuan lain, yaitu untuk beroperasi pada hasil kueri. Setiap fungsi yang mengembalikan nilai non-boolean mengubah hasil ekspresi.
Misalnya, Anda dapat mengurutkan data berdasarkan nilai properti dengan `sort_by(array, &sort_expression)`. JMESPath menggunakan operator khusus, `&`untuk ekspresi yang harus dievaluasi nanti sebagai bagian dari fungsi. Contoh berikutnya menunjukkan cara mengurutkan daftar VM menurut ukuran disk OS:

```azurecli-interactive
az vm list -g QueryDemo --query "sort_by([].{Name:name, Size:storageProfile.osDisk.diskSizeGb}, &Size)" --output table
```

```output
Name     Size
-------  ------
TestVM   30
Test-2   32
WinTest  127
```

Lihat [spesifikasi JMESPath - Fungsi Bawaan](http://jmespath.org/specification.html#built-in-functions) untuk daftar lengkap fungsi.

## <a name="experiment-with-queries-interactively"></a>Bereksperimen dengan kueri secara interaktif

Untuk mulai bereksperimen dengan JMESPath, paket Python [JMESPath-terminal](https://github.com/jmespath/jmespath.terminal) menawarkan lingkungan interaktif untuk bekerja dengan kueri. Data disalurkan sebagai input, dan kemudian kueri ditulis dan dijalankan di editor.

```azurecli
pip install jmespath-terminal
az vm list --output json | jpterm
```

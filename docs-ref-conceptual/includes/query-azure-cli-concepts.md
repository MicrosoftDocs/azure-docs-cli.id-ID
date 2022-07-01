---
ms.topic: include
ms.date: 28/02/2022
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.custom: devx-track-azurecli
ms.openlocfilehash: c3f7a9dc740cf1465942b40d53c4f03f5d0b13b4
ms.sourcegitcommit: 1c90b81d8746101eeff6dab16f71270efb6d6827
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 07/01/2022
ms.locfileid: "146820627"
---
Azure CLI menggunakan kueri untuk memilih dan memodifikasi output perintah Azure CLI. Kueri dijalankan sisi klien pada objek JSON yang dikembalikan perintah Azure CLI sebelum pemformatan tampilan apa pun.

Karakter escape yang diperlukan dalam kueri berbeda untuk lingkungan yang berbeda. Disarankan untuk menjalankan kueri di Azure CloudShell atau cmd karena shell ini membutuhkan lebih sedikit karakter escape. Untuk memastikan contoh kueri benar secara sintaksis, pilih tab untuk shell yang Anda gunakan.

## <a name="dictionary-and-list-cli-results"></a>Kamus dan daftar hasil CLI

Meski menggunakan format output selain JSON, hasil perintah CLI pertama-tama diperlakukan sebagai JSON untuk kueri. Hasil CLI adalah array atau kamus JSON. Array adalah urutan objek yang dapat diindeks, dan kamus adalah objek tidak berurutan yang diakses dengan kunci.

Berikut ini adalah contoh array:
```json
[ 
  1,
  2,
  3
]
```

Berikut ini adalah contoh kamus:
```json
{
  "isRunning": false,
  "time": "12:00",
  "number": 1
}
```

Perintah yang _dapat_ mengembalikan lebih dari satu objek akan mengembalikan array, dan perintah yang _selalu_ mengembalikan _hanya_ satu objek akan mengembalikan kamus.

## <a name="get-properties-in-a-dictionary"></a>Mendapatkan properti dalam kamus

Menggunakan hasil kamus, Anda dapat mengakses properti dari tingkat atas hanya dengan kunci. Karakter `.` (__subekspresi__) digunakan untuk mengakses properti kamus berlapis. Sebelum memperkenalkan kueri, lihat output yang tidak dimodifikasi dari perintah [az vm show](/cli/azure/vm#az-vm-show) :

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm show --resource-group QueryDemo --name TestVM
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

Untuk menghindari kemungkinan masalah kutipan dengan versi PowerShell yang lebih lama, pastikan Anda menggunakan versi terbaru. Untuk menginstal PowerShell versi terbaru, silakan lihat [Menginstal PowerShell di Windows, Linux, dan macOS](/powershell/scripting/install/installing-powershell).

```powershell-interactive
az vm show --resource-group QueryDemo --name TestVM
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm show --resource-group QueryDemo --name TestVM
```

---

Perintah akan menampilkan kamus. Beberapa konten telah dihilangkan.

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

Perintah berikut membuat kunci umum SSH diotorisasi untuk terhubung ke VM dengan menambahkan kueri:

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm show --resource-group QueryDemo --name TestVM --query "osProfile.linuxConfiguration.ssh.publicKeys"
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az vm show --resource-group QueryDemo --name TestVM --query "osProfile.linuxConfiguration.ssh.publicKeys"
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm show --resource-group QueryDemo --name TestVM --query "osProfile.linuxConfiguration.ssh.publicKeys"
```

---

```json
[
  {
    "keyData": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDMobZNJTqgjWn/IB5xlilvE4Y+BMYpqkDnGRUcA0g9BYPgrGSQquCES37v2e3JmpfDPHFsaR+CPKlVr2GoVJMMHeRcMJhj50ZWq0hAnkJBhlZVWy8S7dwdGAqPyPmWM2iJDCVMVrLITAJCno47O4Ees7RCH6ku7kU86b1NOanvrNwqTHr14wtnLhgZ0gQ5GV1oLWvMEVg1YFMIgPRkTsSQKWCG5lLqQ45aU/4NMJoUxGyJTL9i8YxMavaB1Z2npfTQDQo9+womZ7SXzHaIWC858gWNl9e5UFyHDnTEDc14hKkf1CqnGJVcCJkmSfmrrHk/CkmF0ZT3whTHO1DhJTtV stramer@contoso",
    "path": "/home/azureuser/.ssh/authorized_keys"
  }
]
```

Perhatikan bahwa string kueri peka huruf besar/kecil. Misalnya, mengubah 'osProfile' menjadi 'OsProfile' dalam kueri di atas tidak akan mengembalikan hasil yang benar.

## <a name="get-multiple-values"></a>Mendapatkan beberapa nilai

Untuk mendapatkan lebih dari satu properti, letakkan ekspresi yang dipisahkan oleh koma dalam tanda kurung  `[ ]` siku ( __daftar multipilih__). Perintah berikut mendapatkan nama VM, pengguna admin, dan kunci SSH sekaligus:

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm show --resource-group QueryDemo --name TestVM --query "[name, osProfile.adminUsername, osProfile.linuxConfiguration.ssh.publicKeys[0].keyData]"
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az vm show --resource-group QueryDemo --name TestVM --query "[name, osProfile.adminUsername, osProfile.linuxConfiguration.ssh.publicKeys[0].keyData]"
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm show --resource-group QueryDemo --name TestVM --query "[name, osProfile.adminUsername, osProfile.linuxConfiguration.ssh.publicKeys[0].keyData]"
```
---

```json
[
  "TestVM",
  "azureuser",
  "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDMobZNJTqgjWn/IB5xlilvE4Y+BMYpqkDnGRUcA0g9BYPgrGSQquCES37v2e3JmpfDPHFsaR+CPKlVr2GoVJMMHeRcMJhj50ZWq0hAnkJBhlZVWy8S7dwdGAqPyPmWM2iJDCVMVrLITAJCno47O4Ees7RCH6ku7kU86b1NOanvrNwqTHr14wtnLhgZ0gQ5GV1oLWvMEVg1YFMIgPRkTsSQKWCG5lLqQ45aU/4NMJoUxGyJTL9i8YxMavaB1Z2npfTQDQo9+womZ7SXzHaIWC858gWNl9e5UFyHDnTEDc14hKkf1CqnGJVcCJkmSfmrrHk/CkmF0ZT3whTHO1DhJTtV stramer@contoso"
]
```

Nilai-nilai ini tercantum dalam array hasil dalam urutan yang diberikan dalam kueri. Karena hasilnya adalah array, tidak ada kunci yang terkait dengan hasil. Untuk mendapatkan kamus alih-alih array, lihat bagian di bawah ini.

## <a name="rename-properties-in-a-query"></a>Mengganti nama properti dalam kueri

Untuk mendapatkan kamus, bukan array saat kueri untuk beberapa nilai, gunakan `{ }` operator (__hash multiselect__).
Format untuk hash multiselect adalah `{displayName:JMESPathExpression, ...}`.
`displayName` akan menjadi string yang ditampilkan dalam output, dan `JMESPathExpression` adalah ekspresi JMESPath yang akan dievaluasi. Memodifikasi contoh dari bagian terakhir dengan mengubah daftar multiselect menjadi hash:

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm show --resource-group QueryDemo --name TestVM --query "{VMName:name, admin:osProfile.adminUsername, sshKey:osProfile.linuxConfiguration.ssh.publicKeys[0].keyData}"
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az vm show --resource-group QueryDemo --name TestVM --query "{VMName:name, admin:osProfile.adminUsername, sshKey:osProfile.linuxConfiguration.ssh.publicKeys[0].keyData }"
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm show --resource-group QueryDemo --name TestVM --query "{VMName:name, admin:osProfile.adminUsername, sshKey:osProfile.linuxConfiguration.ssh.publicKeys[0].keyData }"
```

---

```json
{
  "VMName": "TestVM",
  "admin": "azureuser",
  "ssh-key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDMobZNJTqgjWn/IB5xlilvE4Y+BMYpqkDnGRUcA0g9BYPgrGSQquCES37v2e3JmpfDPHFsaR+CPKlVr2GoVJMMHeRcMJhj50ZWq0hAnkJBhlZVWy8S7dwdGAqPyPmWM2iJDCVMVrLITAJCno47O4Ees7RCH6ku7kU86b1NOanvrNwqTHr14wtnLhgZ0gQ5GV1oLWvMEVg1YFMIgPRkTsSQKWCG5lLqQ45aU/4NMJoUxGyJTL9i8YxMavaB1Z2npfTQDQo9+womZ7SXzHaIWC858gWNl9e5UFyHDnTEDc14hKkf1CqnGJVcCJkmSfmrrHk/CkmF0ZT3whTHO1DhJTtV stramer@contoso"
}
```

## <a name="get-properties-in-an-array"></a>Mendapatkan properti dalam array

Array tidak memiliki properti sendiri, tetapi dapat diindeks. Fitur ini ditampilkan dalam contoh terakhir dengan ekspresi `publicKeys[0]`, yang mendapatkan elemen pertama dari array `publicKeys`. Tidak ada jaminan output CLI diurutkan, jadi hindari menggunakan pengindeksan kecuali Anda yakin dengan urutan atau tidak peduli elemen mana yang Anda dapatkan. Untuk mengakses properti elemen dalam array, Anda melakukan salah satu dari dua operasi: _meratakan_ atau _memfilter_. Bagian ini membahas cara meratakan array.

Meratakan array dilakukan dengan operator `[]` JMESPath. Semua ekspresi setelah operator `[]` diterapkan ke setiap elemen dalam array saat ini.
Jika muncul di awal kueri, `[]` akan meratakan hasil perintah CLI. Hasil `az vm list` dapat diperiksa dengan fitur ini.
Kueri berikut mendapatkan nama, OS, dan nama administrator untuk setiap VM dalam grup sumber daya:

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm list --resource-group QueryDemo --query "[].{Name:name, OS:storageProfile.osDisk.osType, admin:osProfile.adminUsername}"
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az vm list --resource-group QueryDemo --query "[].{Name:name, OS:storageProfile.osDisk.osType, admin:osProfile.adminUsername}" 
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm list --resource-group QueryDemo --query "[].{Name:name, OS:storageProfile.osDisk.osType, admin:osProfile.adminUsername}"
```

---

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

Array apa pun dapat diratakan, bukan hanya hasil tingkat atas yang dikembalikan oleh perintah. Di bagian terakhir, ekspresi `osProfile.linuxConfiguration.ssh.publicKeys[0].keyData` digunakan untuk mendapatkan kunci umum SSH untuk masuk. Untuk mendapatkan _setiap_ kunci umum SSH, ekspresi dapat ditulis sebagai `osProfile.linuxConfiguration.ssh.publicKeys[].keyData`.
Ekspresi kueri ini meratakan array `osProfile.linuxConfiguration.ssh.publicKeys`, lalu menjalankan ekspresi `keyData` pada setiap elemen:

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm show --resource-group QueryDemo --name TestVM --query "{VMName:name, admin:osProfile.adminUsername, sshKeys:osProfile.linuxConfiguration.ssh.publicKeys[].keyData }"
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az vm show --resource-group QueryDemo --name TestVM --query "{VMName:name, admin:osProfile.adminUsername, sshKeys:osProfile.linuxConfiguration.ssh.publicKeys[].keyData }"
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm show --resource-group QueryDemo --name TestVM --query "{VMName:name, admin:osProfile.adminUsername, sshKeys:osProfile.linuxConfiguration.ssh.publicKeys[].keyData }"
```
---

```json
{
  "VMName": "TestVM",
  "admin": "azureuser",
  "sshKeys": [
    "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDMobZNJTqgjWn/IB5xlilvE4Y+BMYpqkDnGRUcA0g9BYPgrGSQquCES37v2e3JmpfDPHFsaR+CPKlVr2GoVJMMHeRcMJhj50ZWq0hAnkJBhlZVWy8S7dwdGAqPyPmWM2iJDCVMVrLITAJCno47O4Ees7RCH6ku7kU86b1NOanvrNwqTHr14wtnLhgZ0gQ5GV1oLWvMEVg1YFMIgPRkTsSQKWCG5lLqQ45aU/4NMJoUxGyJTL9i8YxMavaB1Z2npfTQDQo9+womZ7SXzHaIWC858gWNl9e5UFyHDnTEDc14hKkf1CqnGJVcCJkmSfmrrHk/CkmF0ZT3whTHO1DhJTtV stramer@contoso\n"
  ]
}
```

## <a name="filter-arrays-with-boolean-expressions"></a>Memfilter array dengan ekspresi boolean

Operasi lain yang digunakan untuk mendapatkan data dari array adalah _pemfilteran_. Pemfilteran dilakukan dengan operator `[?...]` JMESPath.
Operator ini mengambil predikat sebagai isinya. Predikat adalah pernyataan apa pun, termasuk properti Boolean, yang dapat dievaluasi ke atau `true` `false`. Ekspresi di mana predikat mengevaluasi ke `true` disertakan dalam output.

Kueri pertama menunjukkan cara mencantumkan nama semua langganan Azure yang tersambung ke akun Anda yang propertinya `isDefault` benar. Kueri kedua dan ketiga menunjukkan dua cara berbeda untuk mencantumkan semua langganan yang propertinya `isDefault` salah.

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
# Boolean values are assumed to be true, so you can directly evaluate the isDefault property to return the default subscription.
az account list --query "[?isDefault].name"

# To check if a Boolean property is false, you can use the comparison operator == or the logical operator !.
az account list --query '[?!isDefault].name'
az account list --query "[?isDefault == \`false\`].name"
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
# Boolean values are assumed to be true, so you can directly evaluate the isDefault property to return the default subscription.
az account list --query "[?isDefault].name"

# To check if a Boolean property is false, you can use the comparison operator == or the logical operator !.
az account list --query "[?!isDefault].name"
az account list --query "[?isDefault == ``false``].name"
```

Perhatikan karakter escape tambahan (`` ` ``) yang mengelilingi nilai `false` dalam perintah di atas. Karakter escape tambahan ini ada karena perintah Azure CLI dianggap sebagai skrip Prompt Perintah, sehingga penguraian PowerShell dan Command Prompt perlu dipertimbangkan. Azure CLI hanya akan menerima simbol jika masih ada setelah 2 putaran penguraian. Untuk informasi selengkapnya tentang kemungkinan masalah kutipan lainnya, lihat [Mengutip masalah dengan PowerShell](https://github.com/Azure/azure-cli/blob/dev/doc/quoting-issues-with-powershell.md).

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
REM Boolean values are assumed to be true, so you can directly evaluate the isDefault property to return the default subscription.
az account list --query "[?isDefault].name"

REM To check if a Boolean property is false, you can use the comparison operator == or the logical operator !.
az account list --query "[?!isDefault].name"
az account list --query "[?isDefault == `false`].name"
```

Harap dicatat bahwa contoh di atas hanya berfungsi saat menggunakan Prompt Perintah secara interaktif. Untuk menjalankan beberapa perintah az dalam skrip batch menggunakan Command Prompt, awali setiap perintah az dengan `call`. Misalnya gunakan `call az account list` alih-alih `az account list`.

---

JMESPath menawarkan perbandingan standar dan operator logika. Ini termasuk `<`, `<=`, `>`, `>=`, `==`, dan `!=`. JMESPath juga mendukung logika dan (`&&`), atau (`||`), dan bukan (`!`). Ekspresi dapat dikelompokkan dalam tanda kurung, sehingga memungkinkan ekspresi predikat yang lebih kompleks. Untuk detail lengkap tentang predikat dan operasi logika, lihat [spesifikasi JMESPath](http://jmespath.org/specification.html).

Di bagian terakhir, Anda meratakan array untuk mendapatkan daftar lengkap semua VM dalam grup sumber daya. Dengan menggunakan filter, output ini dapat dibatasi hanya untuk VM Linux:

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm list --resource-group QueryDemo --query "[?storageProfile.osDisk.osType=='Linux'].{Name:name,  admin:osProfile.adminUsername}" --output table
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az vm list --resource-group QueryDemo --query "[?storageProfile.osDisk.osType=='Linux'].{Name:name,  admin:osProfile.adminUsername}" --output table
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm list --resource-group QueryDemo --query "[?storageProfile.osDisk.osType=='Linux'].{Name:name,  admin:osProfile.adminUsername}" --output table
```

---

```json
Name    Admin
------  ---------
Test-2  sttramer
TestVM  azureuser
```

Anda juga dapat memfilter nilai numerik seperti ukuran disk OS. Contoh berikut menunjukkan cara memfilter daftar VM untuk menampilkannya dengan ukuran disk yang lebih besar dari atau sama dengan 50GB.

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm list --resource-group QueryDemo --query "[?storageProfile.osDisk.diskSizeGb >=\`50\`].{Name:name,  admin:osProfile.adminUsername, DiskSize:storageProfile.osDisk.diskSizeGb }" --output table
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az vm list --resource-group QueryDemo --query "[?storageProfile.osDisk.diskSizeGb >=``50``].{Name:name,  admin:osProfile.adminUsername, DiskSize:storageProfile.osDisk.diskSizeGb }" --output table
```

Perhatikan karakter escape tambahan (`` ` ``) di sekitar 50 dalam perintah di atas. Karakter escape tambahan ini ada karena perintah Azure CLI dianggap sebagai skrip Prompt Perintah, sehingga penguraian PowerShell dan Prompt Perintah perlu dipertimbangkan. Azure CLI hanya akan menerima simbol jika masih ada setelah 2 putaran penguraian. Untuk informasi selengkapnya tentang kemungkinan masalah kutipan lainnya, lihat [Mengutip masalah dengan PowerShell](https://github.com/Azure/azure-cli/blob/dev/doc/quoting-issues-with-powershell.md).

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm list --resource-group QueryDemo --query "[?storageProfile.osDisk.diskSizeGb >=`50`].{Name:name, admin:osProfile.adminUsername, DiskSize:storageProfile.osDisk.diskSizeGb }" --output table
```

---

```json
Name     Admin     DiskSize
-------  --------  --------
WinTest  winadmin  127
```

Untuk array besar, mungkin lebih cepat menerapkan filter sebelum memilih data.

> [!IMPORTANT]
>
> Di JMESPath, string selalu dikelilingi oleh tanda kutip tunggal (`'`) atau karakter escape (`` ` ``). Jika Anda menggunakan tanda kutip ganda sebagai bagian dari string dalam predikat filter, Anda akan mendapatkan output kosong.

## <a name="jmespath-functions"></a>Fungsi JMESPath

JMESPath juga memiliki fungsi bawaan yang memungkinkan kueri yang lebih kompleks dan untuk memodifikasi output kueri. Bagian ini berfokus pada penggunaan fungsi JMESPath untuk membuat kueri sementara bagian [Memanipulasi output dengan fungsi](#manipulating-output-with-functions) menunjukkan cara menggunakan fungsi untuk memodifikasi output.

Ekspresi dievaluasi sebelum memanggil fungsi, sehingga argumen itu sendiri dapat menjadi ekspresi JMESPath. Contoh berikut menunjukkan ini dengan menggunakan `contains(string, substring)`, yang memeriksa untuk melihat apakah string berisi substring. Perintah ini menemukan semua VM menggunakan penyimpanan SSD untuk disk OS mereka:

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm list --resource-group QueryDemo --query "[?contains(storageProfile.osDisk.managedDisk.storageAccountType,'SSD')].{Name:name, Storage:storageProfile.osDisk.managedDisk.storageAccountType}"
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az vm list --resource-group QueryDemo --query "[?contains(storageProfile.osDisk.managedDisk.storageAccountType,'SSD')].{Name:name, Storage:storageProfile.osDisk.managedDisk.storageAccountType}"
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm list --resource-group QueryDemo --query "[?contains(storageProfile.osDisk.managedDisk.storageAccountType,'SSD')].{Name:name, Storage:storageProfile.osDisk.managedDisk.storageAccountType}"
```

---

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

## <a name="pipe-expressions"></a>Ekspresi pipa

Mirip dengan cara `|` digunakan di baris perintah, `|` dapat digunakan dalam kueri JMESPath untuk menerapkan ekspresi ke hasil kueri perantara. Kita juga dapat menggunakan `|` untuk memecah kueri kompleks menjadi subekspresi yang lebih sederhana. Untuk mempersingkat kueri dari bagian sebelumnya, gunakan `|` untuk menerapkan filter setelah meratakan dan memilih data.

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm list --resource-group QueryDemo --query "[].{Name:name, Storage:storageProfile.osDisk.managedDisk.storageAccountType} | [? contains(Storage,'SSD')]"
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az vm list --resource-group QueryDemo --query "[].{Name:name, Storage:storageProfile.osDisk.managedDisk.storageAccountType} | [? contains(Storage,'SSD')]"
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm list --resource-group QueryDemo --query "[].{Name:name, Storage:storageProfile.osDisk.managedDisk.storageAccountType} | [? contains(Storage,'SSD')]"
```

---

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

Lihat [Spesifikasi JMESPath - Fungsi Bawaan](http://jmespath.org/specification.html#built-in-functions) untuk daftar lengkap fungsi.

## <a name="manipulating-output-with-functions"></a>Memanipulasi output dengan fungsi

Fungsi JMESPath juga memiliki tujuan lain, yaitu untuk beroperasi pada hasil kueri. Setiap fungsi yang mengembalikan nilai non-boolean akan mengubah hasil ekspresi. Misalnya, Anda dapat mengurutkan data menurut nilai properti dengan `sort_by(array, &sort_expression)`. JMESPath menggunakan operator khusus, `&`, untuk ekspresi yang harus dievaluasi nanti sebagai bagian dari suatu fungsi. Contoh berikutnya menunjukkan cara mengurutkan daftar VM berdasarkan ukuran disk OS:

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm list --resource-group QueryDemo --query "sort_by([].{Name:name, Size:storageProfile.osDisk.diskSizeGb}, &Size)" --output table
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az vm list --resource-group QueryDemo --query "sort_by([].{Name:name, Size:storageProfile.osDisk.diskSizeGb}, &Size)" --output table
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm list --resource-group QueryDemo --query "sort_by([].{Name:name, Size:storageProfile.osDisk.diskSizeGb}, &Size)" --output table
```

---

```json
Name     Size
-------  ------
Test-2   30
TestVM   32
WinTest  127
```

Lihat [Spesifikasi JMESPath - Fungsi Bawaan](http://jmespath.org/specification.html#built-in-functions) untuk daftar lengkap fungsi.

## <a name="formatting-query-results"></a>Memformat hasil kueri

Azure CLI menggunakan JSON sebagai format output defaultnya, namun format output yang berbeda mungkin lebih sesuai dengan kueri tergantung pada tujuan dan hasilnya. Perhatikan bahwa kueri selalu dijalankan pada output terlebih `JSON` dahulu lalu diformat.

Bagian ini akan membahas `tsv` dan `table` memformat dan beberapa kasus penggunaan untuk setiap format. Untuk informasi selengkapnya tentang format output, lihat [Format output untuk perintah Azure CLI](../format-output-azure-cli.md).

### <a name="tsv-output-format"></a>Format output TSV

Format output `tsv` menampilkan nilai yang dipisahkan tab dan baris baru tanpa pemformatan tambahan, kunci, atau simbol lainnya. Ini berguna ketika output dikonsumsi oleh perintah lain.

Satu kasus penggunaan untuk `tsv` pemformatan adalah kueri yang mengambil nilai dari perintah CLI, seperti ID sumber daya Azure atau nama sumber daya, dan menyimpan nilai dalam variabel lingkungan lokal. Secara default hasilnya dikembalikan dalam format JSON. Ini mungkin masalah saat berhadapan dengan string JSON yang diapit `"` karakter. Tanda kutip mungkin __tidak__ ditafsirkan oleh shell jika output perintah langsung ditetapkan ke variabel lingkungan. Ini dapat dilihat dalam contoh berikut yang menetapkan hasil kueri ke variabel lingkungan:

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
USER=$(az vm show --resource-group QueryDemo --name TestVM --query "osProfile.adminUsername")
echo $USER
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
$USER=$(az vm show --resource-group QueryDemo --name TestVM --query "osProfile.adminUsername")
echo $USER
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
FOR /f %i IN ('az vm show --resource-group QueryDemo --name TestVM --query "osProfile.adminUsername"') DO SET USER=%i
echo %USER%
```

---

```json
"azureuser"
```

Untuk mencegah menyertakan nilai pengembalian dengan informasi jenis, gunakan `tsv` pemformatan seperti yang ditunjukkan dalam kueri berikut:

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
USER=$(az vm show --resource-group QueryDemo --name TestVM --query "osProfile.adminUsername" --output tsv)
echo $USER
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
$USER=$(az vm show --resource-group QueryDemo --name TestVM --query "osProfile.adminUsername" --output tsv)
echo $USER
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
FOR /f %i IN ('az vm show --resource-group QueryDemo --name TestVM --query "osProfile.adminUsername" --output tsv') DO SET USER=%i
echo %USER%
```

---

```json
azureuser
```

### <a name="table-output-format"></a>Format output tabel

Format `table` mencetak output sebagai tabel ASCII, sehingga mudah dibaca dan dipindai. Tidak semua bidang disertakan dalam tabel sehingga format ini paling baik digunakan sebagai gambaran umum data yang dapat dicari manusia. Bidang yang tidak disertakan dalam tabel masih bisa difilter sebagai bagian dari kueri.

> [!NOTE]
>
> Kunci tertentu difilter dan tidak dicetak dalam tampilan tabel. Kunci tersebut adalah `id`, `type`, dan `etag`. Untuk melihat nilai ini, Anda dapat mengubah nama kunci dalam hash multiselect.
>
>```azurecli
> az vm show --resource-group QueryDemo --name TestVM --query "{objectID:id}" --output table
>```

Kita dapat menggunakan kueri sebelumnya untuk menunjukkan hal ini. Kueri asli mengembalikan objek JSON yang berisi nama, OS, dan nama administrator untuk setiap VM dalam grup sumber daya:

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm list --resource-group QueryDemo --query "[].{Name:name, OS:storageProfile.osDisk.osType, admin:osProfile.adminUsername}"
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az vm list --resource-group QueryDemo --query "[].{Name:name, OS:storageProfile.osDisk.osType, admin:osProfile.adminUsername}"
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm list --resource-group QueryDemo --query "[].{Name:name, OS:storageProfile.osDisk.osType, admin:osProfile.adminUsername}"
```

---

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

Ketika dikombinasikan `--output table` dengan format output, nama kolom cocok dengan `displayKey` nilai hash multipilih sehingga lebih mudah untuk melompati informasi:

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm list --resource-group QueryDemo --query "[].{Name:name, OS:storageProfile.osDisk.osType, Admin:osProfile.adminUsername}" --output table
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az vm list --resource-group QueryDemo --query "[].{Name:name, OS:storageProfile.osDisk.osType, Admin:osProfile.adminUsername}" --output table
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az vm list --resource-group QueryDemo --query "[].{Name:name, OS:storageProfile.osDisk.osType, Admin:osProfile.adminUsername}" --output table
```

---

```json
Name     OS       Admin
-------  -------  ---------
Test-2   Linux    sttramer
TestVM   Linux    azureuser
WinTest  Windows  winadmin
```

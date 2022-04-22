---
ms.topic: include
ms.date: 28/02/2022
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.custom: devx-track-azurecli
ms.openlocfilehash: db0ef72eb067fc6a482f74e2c6cec3213d0d0bef
ms.sourcegitcommit: a805041ebd77f92fa4b3025ba6856ea4aedae2ac
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 04/22/2022
ms.locfileid: "144003462"
---
Bagian ini berisi contoh kueri JMESPath untuk sumber daya Azure yang berbeda.

### <a name="query-examples-for-azure-accounts"></a>Contoh kueri untuk akun Azure

Bagian ini memperlihatkan contoh kueri untuk akun penyimpanan.

- Contoh ini mengembalikan ID penyewa dan ID langganan akun Azure dan langganan yang Anda gunakan.

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az account show --query '{tenantId:tenantId,subscriptionid:id}'
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az account show --query "{tenantId:tenantId,subscriptionid:id}"
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az account show --query "{tenantId:tenantId,subscriptionid:id}"
```

---

### <a name="query-examples-for-azure-active-directory-service-principals"></a>Contoh kueri untuk perwakilan layanan Azure Active Directory

Bagian ini memperlihatkan contoh kueri untuk AAD perwakilan layanan.

- Kueri berikut mengembalikan perwakilan layanan aplikasi Microsoft Graph pertama yang memiliki izin baca.

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az ad sp list --display-name "Microsoft Graph" --query '[0].appRoles[?value==`User.Read.All` && contains(allowedMemberTypes, `Application`)].id' --output tsv
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az ad sp list --display-name "Microsoft Graph" --query "[0].appRoles[?value=='User.Read.All' && contains(allowedMemberTypes, 'Application')].id" --output tsv
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az ad sp list --display-name "Microsoft Graph" --query "[0].appRoles[?value=='User.Read.All' && contains(allowedMemberTypes, 'Application')].id" --output tsv
```

---

### <a name="query-examples-for-storage-accounts"></a>Contoh kueri untuk akun penyimpanan

Bagian ini memperlihatkan contoh kueri untuk akun penyimpanan.

- Contoh ini mengembalikan titik akhir utama untuk semua tabel akun penyimpanan.

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az storage account show --resource-group QueryDemo --name mystorageaccount --query 'primaryEndpoints.table'
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive 
az storage account show --resource-group QueryDemo --name mystorageaccount --query "primaryEndpoints.table"
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az storage account show --resource-group QueryDemo --name mystorageaccount --query "primaryEndpoints.table"
```

---

### <a name="query-examples-for-virtual-machines"></a>Contoh kueri untuk Virtual Machines

Bagian ini memperlihatkan contoh kueri untuk Virtual Machines (VM).

- Contoh ini mengembalikan nama VM yang ukuran disknya lebih besar dari 50GB.

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm list --resource-group QueryDemo --query '[?storageProfile.osDisk.diskSizeGb >=`50`].{Name:name,  admin:osProfile.adminUsername, DiskSize:storageProfile.osDisk.diskSizeGb }' --output table
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

- Kueri berikut menunjukkan cara mencantumkan nama dan jenis akun penyimpanan VM yang menggunakan penyimpanan SSD.

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az vm list --resource-group QueryDemo --query '[].{Name:name, Storage:storageProfile.osDisk.managedDisk.storageAccountType} | [? contains(Storage,`SSD`)]'
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

### <a name="query-examples-for-cognitive-services"></a>Contoh kueri untuk layanan kognitif
Bagian ini memperlihatkan contoh kueri untuk layanan kognitif.

-  Kueri berikut menunjukkan cara mencantumkan titik akhir layanan kognitif.

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az cognitiveservices account show --resource-group QueryDemo --name DemoAccount --query 'properties.endpoint'

```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az cognitiveservices account show --resource-group QueryDemo --name DemoAccount --query "properties.endpoint"
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az cognitiveservices account show --resource-group QueryDemo --name DemoAccount --query "properties.endpoint"

```

---

### <a name="query-examples-for-virtual-vetworks"></a>Contoh kueri untuk vetwork virtual

Bagian ini memperlihatkan contoh kueri untuk jaringan virtual (VNet).

- Kueri berikut mencantumkan ID alamat IP yang berisi substring dalam IP variabel.

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
IP="20.127"
az network public-ip list --query "[?ipAddress!=null]|[?contains(ipAddress, '$IP')].[id]" --output tsv
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
$IP="20.127"
az network public-ip list --query "[?ipAddress!=null]|[?contains(ipAddress, '$IP')].[id]" --output tsv
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
Set IP="20.127"
az network public-ip list --query "[?ipAddress!=null]|[?contains(ipAddress, '%IP%')].[id]" --output tsv
```

---

### <a name="query-examples-for-web-apps"></a>Contoh kueri untuk aplikasi web

Bagian ini memperlihatkan contoh kueri untuk aplikasi web.

- Kueri berikut mencantumkan semua aplikasi web yang saat ini sedang berjalan.

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az webapp list --resource-group DemoGroup --query '[?state==`Running`]'
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az webapp list --resource-group DemoGroup --query "[?state=='Running']"
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az webapp list --resource-group DemoGroup --query "[?state=='Running']"
```

---

- Kueri berikut mengembalikan nama profil dan url semua aplikasi web yang nama profilnya berakhir dengan FTP.

### <a name="bash"></a>[Bash](#tab/bash)

```azurecli-interactive
az webapp deployment list-publishing-profiles --resource-group DemoGroup --name DemoApp --query '[?ends_with(profileName, `FTP`)].{profileName: profileName, publishUrl: publishUrl}'
```

### <a name="powershell"></a>[PowerShell](#tab/powershell)

```powershell-interactive
az webapp deployment list-publishing-profiles --resource-group DemoGroup --name DemoApp --query "[?ends_with(profileName, 'FTP')].{profileName: profileName, publishUrl: publishUrl}"
```

### <a name="cmd"></a>[Cmd](#tab/cmd)

```cmd
az webapp deployment list-publishing-profiles --resource-group DemoGroup --name DemoApp --query "[?ends_with(profileName, 'FTP')].{profileName: profileName, publishUrl: publishUrl}"
```

---
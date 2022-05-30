---
title: Mode Interaktif Azure CLI | Microsoft Docs
description: Mode interaktif Azure CLI adalah shell interaktif dengan penyelesaian otomatis, deskripsi perintah, dan contoh.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.tool: azure-cli
ms.custom: devx-track-azurecli, seo-azure-cli
Keywords: mode interaktif azure cli
ms.openlocfilehash: 162c01627fd5889b5a6ee2de236e2c8b70a86d87
ms.sourcegitcommit: 6822e5d700742617eabda5904fe2ca217bae9d28
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/30/2022
ms.locfileid: "145937786"
---
# <a name="azure-cli-interactive-mode"></a>Mode interaktif Azure CLI

Anda dapat menggunakan Azure CLI dalam mode interaktif dengan menjalankan perintah `az interactive`.  Mode interaktif Azure CLI menempatkan Anda dalam shell interaktif dengan penyelesaian otomatis, deskripsi perintah, dan contoh.

![mode interaktif](./media/interactive-azure-cli/webapp-create.png)

> [!NOTE]
> Di sini, kami tidak menggunakan gaya default, yang juga tidak dibaca di latar belakang hitam.

Jika Anda belum masuk ke akun, gunakan perintah `login`.

## <a name="what-is-the-azure-cli-interactive-mode"></a>Apa yang dimaksud dengan mode interaktif Azure CLI?

Mode Interaktif Azure CLI (az interactive) menyediakan pengguna lingkungan interaktif untuk menjalankan perintah Azure CLI. Mode interaktif memudahkan Anda mempelajari kemampuan, sintaks perintah, dan format output Azure CLI. Ini menyediakan menu drop-down penyelesaian otomatis, saran cache otomatis yang dikombinasikan dengan dokumentasi runtime, termasuk contoh bagaimana setiap perintah digunakan. Mode Interaktif Azure CLI bertujuan untuk memberikan pengalaman yang ideal bagi pengguna yang belajar menggunakan perintah Azure CLI. 

## <a name="configure"></a>Konfigurasikan

Secara opsional, mode interaktif menampilkan deskripsi perintah, deskripsi parameter, dan contoh perintah.
Aktifkan atau nonaktifkan deskripsi dan contoh menggunakan `F1`.

![Deskripsi dan contoh aktif/nonaktif](./media/interactive-azure-cli/descriptions-and-examples.png)

Anda dapat mengaktifkan atau menonaktifkan tampilan default parameter menggunakan `F2`.

![Tampilan default parameter aktif/nonaktif](./media/interactive-azure-cli/defaults.png)

`F3` beralih tampilan beberapa gerakan kunci.

![Peralihan gerakan kunci](./media/interactive-azure-cli/gestures.png)

## <a name="scope"></a>Cakupan

Anda dapat menguji mode interaktif dengan grup perintah tertentu seperti `vm` atau `vm image`.
Jika Anda melakukannya, semua perintah akan ditafsirkan dalam cakupan tersebut.
Sebaiknya Anda melakukan semua pekerjaan di grup perintah tersebut.

Sebagai alternatif mengetik perintah ini:

```azurecli
az>> vm create -n myVM -g myRG --image UbuntuLTS
az>> vm list -o table
```

Anda dapat menguji dengan grup perintah vm dan mengetik perintah ini:

```azurecli
az>> %%vm
az vm>> create -n myVM -g myRG --image UbuntuLTS
az vm>>list -o table
```

Anda juga dapat menguji dengan grup perintah tingkat rendah.
Anda dapat menguji dengan `vm image` menggunakan `%%vm image`.
Dalam hal ini, karena kita telah menguji dengan `vm`, kita akan menggunakan `%%image`.

```azurecli
az vm>> %%image
az vm image>>
```

Pada poin ini, kita dapat memunculkan cakupan kembali ke `vm` menggunakan `%%..`, atau kita dapat menguji dengan akarnya dengan `%%` saja.

```azurecli
az vm image>> %%
az>>
```

## <a name="query"></a>Kueri

Anda dapat menjalankan kueri JMESPath di hasil perintah terakhir yang Anda jalankan dengan menggunakan `??` yang diikuti oleh kueri JMESPath.
Misalnya, setelah membuat grup, Anda dapat mengambil ID grup baru.

```azurecli
az>> group create -n myRG -l westEurope
az>> "?? id"
```

Anda juga dapat menggunakan sintaks ini untuk menggunakan hasil perintah sebelumnya sebagai argumen untuk perintah Berikutnya.* Misalnya setelah mencantumkan semua grup, cantumkan semua sumber daya jenis `virtualMachine`pada grup pertama yang lokasinya adalah westeurope. 

```azurecli
az>> vm create --name myVM --resource-group myRG --image UbuntuLTS --no-wait -o json
az>> group list -o json
az>> resource list -g "?? [?location=='westeurope'].name | [0]" --query "[?type=='Microsoft.Compute/virtualMachines'].name
```

Untuk mempelajari lebih lanjut cara mengkueri hasil perintah Anda, lihat [Mengkueri hasil perintah dengan Azure CLI](query-azure-cli.md).

## <a name="bash-commands"></a>Perintah Bash

Anda dapat menjalankan perintah shell tanpa keluar dari mode interaktif menggunakan `#[cmd]`.

```azurecli
az>> #dir
```

## <a name="examples"></a>Contoh

Beberapa perintah memiliki banyak contoh.
Anda dapat menggulir ke halaman contoh berikutnya menggunakan `CTRL-N` dan halaman sebelumnya menggunakan `CTRL-Y`.

![Menggulir ke halaman contoh berikutnya](./media/interactive-azure-cli/examples.png)

Anda juga dapat melihat contoh tertentu menggunakan `::#`.

```azurecli
az>> vm create ::8
```

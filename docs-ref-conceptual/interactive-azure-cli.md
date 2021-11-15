---
title: Mode interaktif Azure CLI | Microsoft Docs
description: Mode interaktif Azure CLI adalah shell interaktif dengan penyelesaian otomatis, deskripsi perintah, dan contoh.
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 08/19/2021
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli
ms.custom: devx-track-azurecli, seo-azure-cli
Keywords: azure cli interactive mode
ms.openlocfilehash: 1018b845e9a04458540f913b69e0908eaaac6893
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439040"
---
# <a name="azure-cli-interactive-mode"></a>Mode interaktif Azure CLI

Anda dapat menggunakan Azure CLI dalam mode interaktif dengan menjalankan `az interactive` perintah.  Mode interaktif Azure CLI menempatkan Anda dalam shell interaktif dengan penyelesaian otomatis, deskripsi perintah, dan contoh.

![mode interaktif](./media/interactive-azure-cli/webapp-create.png)

> [!NOTE]
> Kami tidak menggunakan gaya default di sini, yang tidak membaca juga pada latar belakang hitam.

Jika Anda belum masuk ke akun Anda, gunakan `login` perintah tersebut.

## <a name="what-is-the-azure-cli-interactive-mode"></a>Apa itu mode interaktif Azure CLI?

Azure CLI Interactive Mode (az interactive) menyediakan pengguna lingkungan interaktif untuk menjalankan perintah Azure CLI. Mode interaktif memudahkan Anda untuk mempelajari kemampuan, sintaks perintah, dan format output Azure CLI. Ini menyediakan dropdown pelengkapan otomatis, saran autocached dikombinasikan dengan dokumentasi runtime, termasuk contoh bagaimana setiap perintah digunakan. Azure CLI Interactive Mode bertujuan untuk memberikan pengalaman yang ideal bagi pengguna yang belajar menggunakan perintah Azure CLI. 

## <a name="configure"></a>Konfigurasikan

Mode interaktif secara opsional menampilkan deskripsi perintah, deskripsi parameter, dan contoh perintah.
Mengaktifkan atau menonaktifkan deskripsi dan contoh menggunakan `F1` .

![Deskripsi dan contoh on/off](./media/interactive-azure-cli/descriptions-and-examples.png)

Anda dapat mengaktifkan atau menonaktifkan tampilan default parameter menggunakan `F2` .

![Tampilkan default/mati parameter](./media/interactive-azure-cli/defaults.png)

`F3` beralih tampilan beberapa gerakan kunci.

![Gerakan tombol beralih](./media/interactive-azure-cli/gestures.png)

## <a name="scope"></a>Cakupan

Anda dapat lingkup mode interaktif Anda ke kelompok perintah tertentu seperti `vm` atau `vm image` .
Ketika Anda melakukannya, semua perintah ditafsirkan dalam lingkup itu.
Ini adalah singkatan yang bagus jika Anda melakukan semua pekerjaan Anda dalam kelompok perintah itu.

Alih-alih mengetik perintah ini:

```azurecli
az>> vm create -n myVM -g myRG --image UbuntuLTS
az>> vm list -o table
```

Anda dapat lingkup ke grup perintah vm dan ketik perintah ini:

```azurecli
az>> %%vm
az vm>> create -n myVM -g myRG --image UbuntuLTS
az vm>>list -o table
```

Anda dapat lingkup ke kelompok perintah tingkat yang lebih rendah juga.
Anda dapat ruang lingkup untuk `vm image` menggunakan `%%vm image` .
Dalam hal ini, karena kita sudah dise `vm` lingkup, kita akan `%%image` menggunakan.

```azurecli
az vm>> %%image
az vm image>>
```

Pada saat itu, kita dapat pop ruang lingkup kembali untuk `vm` `%%..` menggunakan, atau kita dapat ruang lingkup ke akar dengan `%%` hanya.

```azurecli
az vm image>> %%
az>>
```

## <a name="query"></a>Kueri

Anda dapat mengeksekusi kueri JMESPath pada hasil perintah terakhir yang Anda jalankan dengan menggunakan `??` diikuti oleh kueri JMESPath.
Misalnya, setelah membuat grup, Anda dapat mengambil id grup baru.

```azurecli
az>> group create -n myRG -l westEurope
az>> "?? id"
```

Anda juga dapat menggunakan sintaks ini untuk menggunakan hasil perintah sebelumnya sebagai argumen untuk perintah Anda berikutnya.* Misalnya setelah mencantumkan semua grup, daftar semua sumber daya tipe `virtualMachine` pada grup pertama yang lokasinya adalah westeurope. 

```azurecli
az>> vm create --name myVM --resource-group myRG --image UbuntuLTS --no-wait -o json
az>> group list -o json
az>> resource list -g "?? [?location=='westeurope'].name | [0]" --query "[?type=='Microsoft.Compute/virtualMachines'].name
```

Untuk mempelajari selengkapnya tentang kueri hasil perintah Anda, lihat [Hasil perintah Kueri dengan Azure CLI](query-azure-cli.md).

## <a name="bash-commands"></a>Perintah bash

Anda dapat menjalankan perintah shell tanpa meninggalkan mode interaktif menggunakan `#[cmd]` .

```azurecli
az>> #dir
```

## <a name="examples"></a>Contoh

Beberapa perintah memiliki banyak contoh.
Anda dapat menggulir ke halaman berikutnya dari contoh yang digunakan `CTRL-N` dan halaman sebelumnya menggunakan `CTRL-Y` .

![Gulir ke halaman contoh berikutnya](./media/interactive-azure-cli/examples.png)

Anda juga dapat melihat contoh spesifik menggunakan `::#` .

```azurecli
az>> vm create ::8
```

---
title: Membuat Tiket Dukungan Azure – Azure CLI | Microsoft Docs
description: Pelajari cara menggunakan perintah dukungan Azure CLI az untuk membuat, memperbarui, dan mengelola permintaan dukungan Azure.
author: dbradish-microsoft
ms.author: dbradish
ms.service: azure-supportability
ms.topic: how-to
ms.date: 08/01/2021
ms.custom: template-how-to, devx-track-azurecli, seo-azure-cli
keywords: permintaan dukungan azure, dukungan azure, tiket dukungan azure, manajemen tiket dukungan
ms.openlocfilehash: c466acdadbf2ee04062390ed9b15ec93c48b58b6
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439046"
---
# <a name="create-an-azure-support-ticket-in-azure-cli"></a>Membuat tiket dukungan Azure di Azure CLI

Azure CLI memungkinkan Anda membuat dan mengelola tiket dukungan Azure.

- Buka tiket dukungan teknis, penagihan, manajemen langganan, atau langganan dan batas layanan (kuota).
- Dapatkan daftar tiket dukungan dan informasi mendetail tentang setiap tiket. Persempit pencarian Anda untuk tiket dukungan berdasarkan status atau tanggal pembuatan.
- Perbarui tingkat keparahan, status tiket, dan informasi kontak untuk tiket dukungan.
- Tambahkan komunikasi baru ke tiket dukungan atau dapatkan daftar semua komunikasi untuk tiket dukungan. Persempit pencarian daftar komunikasi menurut tanggal atau jenis komunikasi yang dibuat.

Untuk membuat permintaan dukungan, Anda harus menjadi [Pemilik](/azure/role-based-access-control/built-in-roles#owner) atau [Kontributor](/azure/role-based-access-control/built-in-roles#contributor) atau ditetapkan ke peran [Kontributor Permintaan Dukungan ](/azure/role-based-access-control/built-in-roles#support-request-contributor) di tingkat langganan. Untuk membuat permintaan dukungan tanpa langganan, seperti skenario Azure Active Directory, Anda harus menjadi [Admin](/azure/active-directory/roles/permissions-reference).

[!INCLUDE [azure-cli-prepare-your-environment.md](includes/azure-cli-prepare-your-environment.md)]

## <a name="create-a-support-ticket"></a>Buat tiket dukungan

1. Untuk mendapatkan daftar layanan, gunakan perintah [az support services list](/cli/azure/ext/support/support/services#ext_support_az_support_services_list):

   ```azurecli
   az support services list --output table
   ```

   Untuk contoh ini, temukan nilai untuk **Mesin Virtual yang menjalankan Windows**, yaitu **6f16735c-b0ae-b275-ad3a-03479cfa1396**.

1. Untuk mendapatkan jenis masalah dan subjenis masalah yang menjelaskan masalah Anda, jalankan perintah [az support services problem-classifications list](/cli/azure/ext/support/support/services/problem-classifications#ext_support_az_support_services_problem_classifications_list):

   ```azurecli
   az support services problem-classifications list --service-name 6f16735c-b0ae-b275-ad3a-03479cfa1396 --output table
   ```

   Untuk contoh ini, temukan **Tidak dapat terhubung ke VM saya/Saya memiliki masalah dengan IP publik saya**. Jenis tersebut memiliki nilai **e5c307e3-50ff-5dc9-c8ae-7d35051f88c9**.

1. Buat tiket dengan menggunakan perintah [az support ticket create](/cli/azure/ext/support/support/tickets#ext_support_az_support_tickets_create):

   ```azurecli
   az support tickets create --ticket-name "VM012" --title "Issue with public IP" \
      --description "This ticket involves a public IP address of a VM." \
      --problem-classification e5c307e3-50ff-5dc9-c8ae-7d35051f88c9 \
      --severity minimal --contact-first-name Kenneth --contact-last-name Liew \
      --contact-method email --contact-email Kenneth.Liew@Contoso.com \
      --contact-country US --contact-language English --contact-timezone "Pacific Standard Time"
   ```

Teknisi dukungan akan menghubungi Anda menggunakan metode yang Anda pilih. Untuk informasi tentang waktu respons awal, lihat [Cakupan dukungan dan respons.](/support/plans/response/)

## <a name="manage-support-tickets"></a>Mengelola tiket dukungan

Azure CLI memungkinkan Anda melakukan manajemen tiket dukungan menggunakan berbagai perintah. Untuk melihat tiket dukungan Azure untuk langganan Anda saat ini, jalankan perintah [az support tickets list](/cli/azure/ext/support/support/tickets#ext_support_az_support_tickets_list):

```azurecli
az support tickets list
```

Untuk melihat tiket dukungan Azure di langganan lain, jalankan perintah [az account set](/cli/azure/account#az_account_set) untuk mengubah langganan Anda saat ini, lalu jalankan perintah.

Anda juga dapat memperbarui tiket dengan menggunakan perintah [az support ticket update](/cli/azure/ext/support/support/tickets#ext_support_az_support_tickets_update):

```azurecli
az support tickets update --ticket-name VM012 --severity moderate
```

## <a name="communicate-about-your-ticket"></a>Berkomunikasi tentang tiket Anda

Anda tidak dapat menghapus tiket dukungan yang dibuat dengan menggunakan Azure CLI. Sebagai gantinya, kirim pesan untuk menutup tiket. Jika Anda perlu membuka kembali permintaan dukungan tertutup, buat pesan baru, yang secara otomatis membuka kembali permintaan.

Untuk berkomunikasi tentang tiket Anda, jalankan perintah [az support ticket communications create](/cli/azure/ext/support/support/tickets/communications#ext_support_az_support_tickets_communications_create):

```azurecli
az support tickets communications create --ticket-name VM012 \
    --communication-name "VM Delay" \
    --communication-body "Delaying VM fixes due to scheduling on our end." \
    --communication-subject "Delaying VM fixes due to scheduling on our end."
```

Untuk melihat semua komunikasi tiket, gunakan perintah [az support tickets communications list](/cli/azure/ext/support/support/tickets/communications#ext_support_az_support_tickets_communications_list):

```azurecli
az support tickets communications list --ticket-name VM012
```

Perintah ini menawarkan parameter `--filters` untuk mempersempit respons Anda.

```azurecli
az support tickets communications list --ticket-name VM012 \
    --filters "communicationType eq 'Web'"
```

## <a name="next-steps"></a>Langkah berikutnya

- [FAQ Dukungan Azure](https://azure.microsoft.com/support/faq/)
- [Keparahan dan tingkat Azure](https://azure.microsoft.com/support/plans/response/)
- [Cara membuat tiket dukungan melalui portal Azure](/azure/azure-portal/supportability/how-to-create-azure-support-request)

---
title: Create Azure Support Tickets – Azure CLI | Microsoft Docs
description: Pelajari cara menggunakan perintah dukungan Azure CLI az untuk membuat, memperbarui, dan mengelola permintaan dukungan Azure.
author: dbradish-microsoft
ms.author: dbradish
ms.service: azure-supportability
ms.topic: how-to
ms.date: 08/01/2021
ms.custom: template-how-to, devx-track-azurecli, seo-azure-cli
keywords: azure support request, azure support, azure support ticket, support ticket management
ms.openlocfilehash: c466acdadbf2ee04062390ed9b15ec93c48b58b6
ms.sourcegitcommit: ecad34e4d4654660377050fccba7861e942e03de
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 09/13/2021
ms.locfileid: "132439046"
---
# <a name="create-an-azure-support-ticket-in-azure-cli"></a>Create an Azure support ticket in Azure CLI

Azure CLI memungkinkan Anda untuk membuat dan mengelola tiket dukungan Azure.

- Buka teknis, penagihan, manajemen langganan, atau batas berlangganan dan layanan (kuota) tiket dukungan.
- Dapatkan daftar tiket dukungan dan informasi terperinci tentang setiap tiket. Persempit pencarian Anda untuk tiket dukungan berdasarkan status atau tanggal yang dibuat.
- Perbarui tingkat keparahan, status tiket, dan informasi kontak untuk tiket dukungan.
- Tambahkan komunikasi baru ke tiket dukungan atau dapatkan daftar semua komunikasi untuk tiket dukungan. Persempit pencarian daftar komunikasi Anda dengan membuat tanggal atau jenis komunikasi.

Untuk membuat permintaan dukungan, Anda harus menjadi [Pemilik](/azure/role-based-access-control/built-in-roles#owner) atau [Kontributor,](/azure/role-based-access-control/built-in-roles#contributor)atau ditugaskan ke peran [Kontributor Permintaan Dukungan](/azure/role-based-access-control/built-in-roles#support-request-contributor) di tingkat langganan. Untuk membuat permintaan dukungan tanpa langganan, seperti skenario Azure Active Directory, Anda harus menjadi [Admin.](/azure/active-directory/roles/permissions-reference)

[!INCLUDE [azure-cli-prepare-your-environment.md](includes/azure-cli-prepare-your-environment.md)]

## <a name="create-a-support-ticket"></a>Membuat tiket dukungan

1. Untuk mendapatkan daftar layanan, gunakan perintah [daftar layanan dukungan az:](/cli/azure/ext/support/support/services#ext_support_az_support_services_list)

   ```azurecli
   az support services list --output table
   ```

   Untuk contoh ini, temukan nilai untuk **Mesin Virtual yang berjalan Windows,** yaitu **6f16735c-b0ae-b275-ad3a-03479cfa1396.**

1. Untuk mendapatkan tipe masalah dan subtipe masalah yang menjelaskan masalah Anda, jalankan perintah [daftar klasifikasi masalah layanan dukungan AZ:](/cli/azure/ext/support/support/services/problem-classifications#ext_support_az_support_services_problem_classifications_list)

   ```azurecli
   az support services problem-classifications list --service-name 6f16735c-b0ae-b275-ad3a-03479cfa1396 --output table
   ```

   Untuk contoh ini, temukan **Tidak Dapat terhubung ke VM saya / Saya memiliki masalah dengan IP publik saya.** Tipe itu memiliki nilai **e5c307e3-50ff-5dc9-c8ae-7d35051f88c9.**

1. Buat tiket dengan menggunakan perintah [membuat tiket dukungan AZ:](/cli/azure/ext/support/support/tickets#ext_support_az_support_tickets_create)

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

Azure CLI memungkinkan Anda untuk melakukan manajemen tiket dukungan menggunakan berbagai perintah. Untuk melihat tiket dukungan Azure untuk langganan Anda saat ini, jalankan perintah [daftar tiket dukungan AZ:](/cli/azure/ext/support/support/tickets#ext_support_az_support_tickets_list)

```azurecli
az support tickets list
```

Untuk melihat tiket dukungan Azure di langganan lain, jalankan perintah [set akun az](/cli/azure/account#az_account_set) untuk mengubah langganan Anda saat ini, lalu jalankan perintah.

Anda juga dapat memperbarui tiket dengan menggunakan perintah [pembaruan tiket dukungan AZ:](/cli/azure/ext/support/support/tickets#ext_support_az_support_tickets_update)

```azurecli
az support tickets update --ticket-name VM012 --severity moderate
```

## <a name="communicate-about-your-ticket"></a>Berkomunikasi tentang tiket Anda

Anda tidak dapat menghapus tiket dukungan yang dibuat dengan menggunakan Azure CLI. Sebagai gantinya, kirim pesan untuk menutup tiket. Jika Anda perlu membuka kembali permintaan dukungan tertutup, buat pesan baru, yang secara otomatis membuka kembali permintaan.

Untuk berkomunikasi tentang tiket Anda, jalankan perintah membuat perintah [komunikasi tiket dukungan AZ:](/cli/azure/ext/support/support/tickets/communications#ext_support_az_support_tickets_communications_create)

```azurecli
az support tickets communications create --ticket-name VM012 \
    --communication-name "VM Delay" \
    --communication-body "Delaying VM fixes due to scheduling on our end." \
    --communication-subject "Delaying VM fixes due to scheduling on our end."
```

Untuk melihat semua komunikasi untuk tiket, gunakan perintah [daftar komunikasi tiket dukungan AZ:](/cli/azure/ext/support/support/tickets/communications#ext_support_az_support_tickets_communications_list)

```azurecli
az support tickets communications list --ticket-name VM012
```

Perintah ini menawarkan `--filters` parameter untuk mempersempit respons Anda.

```azurecli
az support tickets communications list --ticket-name VM012 \
    --filters "communicationType eq 'Web'"
```

## <a name="next-steps"></a>Langkah berikutnya

- [Azure Support FAQs](https://azure.microsoft.com/support/faq/)
- [Azure severity and levels](https://azure.microsoft.com/support/plans/response/)
- [Cara membuat tiket dukungan melalui portal Azure](/azure/azure-portal/supportability/how-to-create-azure-support-request)

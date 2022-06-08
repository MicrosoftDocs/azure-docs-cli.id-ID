---
author: sptramer
ms.author: sttramer
manager: carmonm
ms.date: 09/07/2018
ms.topic: include
ms.openlocfilehash: bfa0435be676e66fe19e9ecd6c5570e219ca91c1
ms.sourcegitcommit: 2a38060aef3a6574be9863b222b9daa6c6d11ece
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 06/08/2022
ms.locfileid: "146186043"
---
1. Jalankan perintah `login`.

    ```azurecli-interactive
    az login
    ```

    Jika CLI dapat membuka browser default Anda, CLI akan memulai [alur kode otorisasi](/azure/active-directory/develop/v2-oauth2-auth-code-flow) dan membuka browser default untuk memuat halaman masuk Azure.

    Jika tidak, ini akan memulai [alur kode perangkat](/azure/active-directory/develop/v2-oauth2-device-code) dan memberi tahu Anda untuk membuka halaman browser di [https://aka.ms/devicelogin](https://aka.ms/devicelogin) dan memasukkan kode yang ditampilkan di terminal Anda.

    Jika tidak ada browser web yang tersedia atau browser web gagal dibuka, Anda dapat memaksa alur kode perangkat dengan **az login --use-device-code**.

2. Masuk menggunakan info masuk akun Anda di browser.

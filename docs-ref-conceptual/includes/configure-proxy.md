---
author: sptramer
ms.author: sttramer
manager: carmonm
ms.date: 05/28/2019
ms.topic: include
ms.prod: azure
ms.technology: azure-cli
ms.openlocfilehash: 2c37a51ed3d3d63111cb741224f6592bc84a0effd9b39755ea833455234f5d87
ms.sourcegitcommit: 16753e7a57048868e186c49e44c1877406530fa5
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 08/06/2021
ms.locfileid: "132439036"
---
Jika Anda tidak dapat terhubung ke sumber daya eksternal dikarenakan proksi, pastikan Anda telah mengatur variabel `HTTP_PROXY` dan `HTTPS_PROXY` dengan benar dalam shell Anda. Anda perlu menghubungi administrator sistem untuk mengetahui host dan port yang akan digunakan untuk proksi ini.

Nilai ini digunakan oleh berbagai program Linux, termasuk nilai yang digunakan dalam proses penginstalan. Untuk mengatur nilai ini:

```bash
# No auth
export HTTP_PROXY=http://[proxy]:[port]
export HTTPS_PROXY=https://[proxy]:[port]

# Basic auth
export HTTP_PROXY=http://[username]:[password]@[proxy]:[port]
export HTTPS_PROXY=https://[username]:[password]@[proxy]:[port]
```

> [!IMPORTANT]
> Jika Anda berada di belakang proksi, variabel shell ini harus diatur untuk terhubung ke layanan Azure dengan CLI.
> Jika tidak menggunakan autentikasi dasar, sebaiknya Anda mengekspor variabel ini dalam file `.bashrc`.
> Selalu ikuti kebijakan keamanan bisnis dan persyaratan administrator sistem Anda.

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
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 08/06/2021
ms.locfileid: "132439036"
---
Jika Anda tidak dapat terhubung ke sumber daya eksternal karena proxy, pastikan Anda telah mengatur dan variabel dengan benar `HTTP_PROXY` `HTTPS_PROXY` di shell Anda. Anda perlu menghubungi administrator sistem Anda untuk mengetahui host dan port apa yang akan digunakan untuk proxy ini.

Nilai-nilai ini dihormati oleh banyak program Linux, termasuk yang digunakan dalam proses instalasi. Untuk mengatur nilai-nilai ini:

```bash
# No auth
export HTTP_PROXY=http://[proxy]:[port]
export HTTPS_PROXY=https://[proxy]:[port]

# Basic auth
export HTTP_PROXY=http://[username]:[password]@[proxy]:[port]
export HTTPS_PROXY=https://[username]:[password]@[proxy]:[port]
```

> [!IMPORTANT]
> Jika Anda berada di belakang proxy, variabel shell ini harus diatur untuk terhubung ke layanan Azure dengan CLI.
> Jika Anda tidak menggunakan auth dasar, disarankan untuk mengekspor variabel-variabel ini dalam `.bashrc` file Anda.
> Selalu ikuti kebijakan keamanan bisnis Anda dan persyaratan administrator sistem Anda.

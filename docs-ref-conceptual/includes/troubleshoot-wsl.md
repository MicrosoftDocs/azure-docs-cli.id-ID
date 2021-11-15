---
author: sptramer
ms.author: sttramer
manager: carmonm
ms.date: 11/26/2018
ms.topic: include
ms.openlocfilehash: 4323466bb9773141dbc362569b373ac9ea54807614f71dd8165eaab685d3407b
ms.sourcegitcommit: 16753e7a57048868e186c49e44c1877406530fa5
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 08/06/2021
ms.locfileid: "132439035"
---
### <a name="cli-fails-to-install-or-run-on-windows-subsystem-for-linux"></a>CLI gagal menginstal atau berjalan pada Subsistem Windows untuk Linux

Karena [Subsistem Windows untuk Linux (WSL)](/windows/wsl/about) adalah lapisan terjemahan panggilan sistem di atas platform Windows, Anda mungkin mengalami kesalahan ketika mencoba menginstal atau menjalankan Azure CLI. CLI bergantung pada beberapa fitur yang mungkin memiliki bug di WSL. Jika Anda mengalami kesalahan tidak peduli bagaimana Anda menginstal CLI, ada kemungkinan besar itu masalah dengan WSL dan bukan dengan proses instalasi CLI.

Untuk memecahkan masalah instalasi WSL Anda dan mungkin menyelesaikan masalah:

* Jika Anda bisa, jalankan proses instalasi yang identik pada mesin Linux atau VM untuk melihat apakah itu berhasil. Jika ya, masalah Anda hampir pasti terkait dengan WSL. Untuk memulai Linux VM di Azure, lihat membuat VM Linux di dokumentasi [Azure Portal.](/azure/virtual-machines/linux/quick-create-portal)
* Pastikan Anda menjalankan WSL versi terbaru. Untuk mendapatkan versi terbaru, [perbarui instalasi Windows 10 Anda.](https://support.microsoft.com/help/4027667/windows-10-update)
* Periksa [masalah terbuka](https://github.com/Microsoft/WSL/issues) dengan WSL yang mungkin mengatasi masalah Anda.
  Seringkali akan ada saran tentang cara mengatasi masalah, atau informasi tentang rilis di mana masalah akan diperbaiki.
* Jika tidak ada masalah yang ada untuk masalah Anda, [ajukan masalah baru dengan WSL](https://github.com/Microsoft/WSL/issues/new) dan pastikan Anda menyertakan informasi sebanyak mungkin.

Jika Anda terus memiliki masalah menginstal atau berjalan pada WSL, pertimbangkan [untuk menginstal CLI untuk Windows.](../install-azure-cli-windows.md)

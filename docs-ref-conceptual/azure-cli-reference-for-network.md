---
title: Referensi Azure CLI untuk Azure Network | Microsoft Docs
description: Temukan perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure Network. Kelola layanan dan kemampuan jaringan secara efektif di Azure dari baris perintah.
author: dbradish-microsoft
manager: barbkess
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.devlang: azurecli
ms.reviewer: mohnader
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: referensi azure cli, jaringan azure
ms.openlocfilehash: 6e9736fd0a203977aa134881492986d613c0c7bb
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439087"
---
# <a name="azure-cli-reference-commands-for-azure-network"></a>Perintah referensi Azure CLI untuk Azure Network

Azure Command-Line Interface ([CLI](./what-is-azure-cli.md)) adalah sekumpulan perintah yang digunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di banyak layanan Azure yang memungkinkan Anda mengelola layanan jaringan dari baris perintah.

Perintah Azure CLI untuk [Azure Network](/azure/networking/) terdiri dari dua bagian: **inti** dan **ekstensi**. Perintah Azure CLI inti dikirimkan sebagai bagian dari CLI dan didukung sepenuhnya. Ekstensi memberi Anda akses ke perintah percobaan dan pra-rilis, dan otomatis diinstal saat Anda menjalankan referensi ekstensi untuk pertama kali. Untuk informasi selengkapnya tentang ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

Lihat [az network](/cli/azure/network) untuk mengetahui daftar alfabetik referensi inti dan ekstensi Azure CLI yang tersedia untuk layanan Azure Network. Untuk referensi setiap sub-grup, lihat tabel di bagian berikut:

- [Jaringan virtual](#virtual-network-references)
- [WAN dan Konektivitas lokal](#wan-and-on-premise-connectivity-references)
- [Penyeimbangan beban dan IP](#load-balancing-and-ip-references)
- [Keamanan](#security-references)
- [Pemantauan](#monitoring-references)
- [Daftar](#list-references)

> [!NOTE]
> Anda diminta menginstal referensi ekstensi saat digunakan pertama kali. Sebagai alternatif, Anda dapat menggunakan perintah `az extension add` untuk menginstal ekstensi secara manual.

## <a name="virtual-network-references"></a>Referensi jaringan virtual 

| Subgrup | Referensi | Penggunaan | Berupa ekstensi
|-|-|-|-|
| Appliance | [az network virtual-appliance](/cli/azure/network/virtual-appliance) | Mengelola Azure Network Virtual Appliance.
| DNS | [az network private-dns](/cli/azure/network/private-dns) | Mengelola domain DNS Privat di Azure. |
| Titik akhir | [az network service-endpoint](/cli/azure/network/service-endpoint) | Mengelola kebijakan yang terkait dengan titik akhir layanan. |
| NAT | [az network nat](/cli/azure/network/nat) | Mengelola sumber daya terjemahan alamat jaringan. |
| NIC | [az network nic](/cli/azure/network/nic) | Mengelola antarmuka jaringan. |
| NIC | [az network nic vtap-config](/cli/azure/network/nic/vtap-config) | Mengelola konfigurasi pengetukan jaringan virtual. | ya
| Peering | [az peering](/cli/azure/peering) | Mengelola peering. | ya
| Profil | [az network profile](/cli/azure/network/profile) | Mengelola profil jaringan. |
| Rute | [az network route-filter](/cli/azure/network/route-filter) | Mengelola filter rute. |
| Rute | [az network routeserver](/cli/azure/network/routeserver) | Mengelola server rute. |
| Rute | [az network route-table](/cli/azure/network/route-table) | Mengelola tabel rute. |
| VMware | [az network vmware](/cli/azure/vmware) | Perintah untuk mengelola Azure VMware Solution. | ya
| vNet | [az network vnet](/cli/azure/network/vnet) | Mengelola Azure Virtual Networks. |
| vNet | [az network vnet-tap](/cli/azure/network/vnet/tap) | Mengelola pengetukan jaringan virtual. | ya
| vNet | [az network vnet-gateway](/cli/azure/network/vnet-gateway) | Gunakan Azure Virtual Network Gateway untuk membangun konektivitas lintas lokal yang aman. |

## <a name="wan-and-on-premise-connectivity-references"></a>Referensi WAN dan Konektivitas lokal

| Subgrup | Referensi | Penggunaan | Berupa ekstensi
|-|-|-|-|
| Lintas koneksi | [az network cross-connection](/cli/azure/network/cross-connection) | Mengelola sumber daya Azure Network. | ya
| ExpressRoute | [az network express-route](/cli/azure/network/express-route) | Mengelola koneksi fiber jaringan privat khusus ke Azure. |
| vHub | [az network vhub](/cli/azure/network/vhub) | Mengelola hub virtual. | ya
| VPN | [az network p2s-vpn-gateway](/cli/azure/network/p2s-vpn-gateway) | Mengelola gateway VPN titik-ke-situs. | ya
| VPN | [az network vpn-connection](/cli/azure/network/vpn-connection) | Mengelola koneksi VPN. |
| VPN | [az network vpn-gateway](/cli/azure/network/vpn-gateway) | Mengelola gateway VPN. | ya
| VPN | [az network vpn-server-config](/cli/azure/network/vpn-server-config) | Mengelola konfigurasi server VPN. | ya
| VPN | [az network vpn-site](/cli/azure/network/vpn-site) | Mengelola konfigurasi situs VPN. | ya
| vRouter | [az network vrouter](/cli/azure/network/vrouter) | Mengelola router virtual. |
| vWAN | [az network vwan](/cli/azure/network/vwan) | Mengelola WAN virtual. | ya

## <a name="load-balancing-and-ip-references"></a>Referensi penyeimbangan beban dan IP

| Subgrup | Referensi | Penggunaan | Berupa ekstensi
|-|-|-|-|
| Gateway aplikasi | [az network application-gateway](/cli/azure/network/application-gateway) | Mengelola layanan penyeimbangan beban dan perutean tingkat aplikasi. |
| Front Door | [az network front-door](/cli/azure/network/front-door) | Mengelola sumber daya Front Door jaringan. | ya
| IP | [az network ip-group](/cli/azure/network/ip-group) | Mengelola IpGroups. | ya
| IP | [az network public-ip](/cli/azure/network/public-ip) | Mengelola alamat IP publik. |
| Keseimbangan beban | [az network cross-region-lb](/cli/azure/network/cross-region-lb) | Mengelola dan mengonfigurasi penyeimbang beban lintas wilayah. |
| Keseimbangan beban | [az network lb](/cli/azure/network/lb) | Mengelola dan mengonfigurasi penyeimbang beban. |
| Gateway lokal | [az network local-gateway](/cli/azure/network/local-gateway) | Mengelola gateway lokal. |
| Traffic manager | [az network traffic-manager](/cli/azure/network/traffic-manager) | Mengelola perutean lalu lintas masuk. |

## <a name="security-references"></a>Referensi keamanan

| Subgrup | Referensi | Penggunaan | Berupa ekstensi
|-|-|-|-|
| ASG | [az asg](/cli/azure/network/asg) | Mengelola kelompok keamanan aplikasi. |
| Bastion | [az network bastion](/cli/azure/network/bastion) | Mengelola host bastion Azure. |
| DDoS | [az network ddos-protection](/cli/azure/network/ddos-protection) | Mengelola Paket DDoS Protection. |
| Firewall | [az network firewall](/cli/azure/network/firewall) | Mengelola dan mengonfigurasi Azure Firewalls. | ya
| Firewall | [az network security-partner-provider](/cli/azure/network/security-partner-provider) | Mengelola penyedia mitra keamanan Azure. |
| NSG | [az network nsg](/cli/azure/network/nsg)| Mengelola Kelompok keamanan Jaringan Azure. |
| Titik akhir privat | [az network private-endpoint](/cli/azure/network/private-endpoint) | Mengelola titik akhir privat. |
| Titik akhir privat | [az network private-endpoint-connection](/cli/azure/network/private-endpoint-connection) | Mengelola koneksi titik akhir privat. |
| Tautan privat | [az network private-link-resource](/cli/azure/network/private-link-resource) | Mengelola sumber daya tautan privat. |
| Tautan privat | [az network private-link-service](/cli/azure/network/private-link-service) | Mengelola layanan tautan privat. |

## <a name="monitoring-references"></a>Referensi pemantauan

| Subgrup | Referensi | Penggunaan | Berupa ekstensi
|-|-|-|-|
| Watcher | [az network watcher](/cli/azure/network/watcher) | Mengelola Azure Network Watcher. |

## <a name="list-references"></a>Referensi daftar

| Subgrup | Referensi | Penggunaan | Berupa ekstensi
|-|-|-|-|
| Layanan | [az network list-service-aliases](/cli/azure/network#az_network_list_service_aliases) | Mencantumkan alias layanan yang tersedia di wilayah yang dapat digunakan untuk Kebijakan Titik Akhir Layanan. |
| Layanan | [az network list-service-tags](/cli/azure/network#az_network_list_service_tags) | Mencantumkan semua tag layanan milik sumber daya yang berbeda. |
| Penggunaan | [az network list-usages](/cli/azure/network#az_network_list_usages) | Mencantumkan jumlah sumber daya jaringan di wilayah yang digunakan terhadap kuota langganan. |

## <a name="popular-azure-network-articles-using-the-azure-cli"></a>Artikel Populer Azure Network menggunakan Azure CLI

- [Membuat komputer virtual](/cli/azure/azure-cli-vm-tutorial)
- [Membuat jaringan virtual](/azure/virtual-network/quick-create-cli)
- [Sampel Azure CLI untuk komputer virtual Windows](/azure/virtual-machines/windows/cli-samples?toc=%2Fcli%2Fazure%2Ftoc.json&bc=%2Fcli%2Fazure%2Fbreadcrumb%2Ftoc.json)
- [Membuat set skala komputer virtual](/azure/virtual-machine-scale-sets/quick-create-cli)
- [Menjalankan Azure IoT Edge di Ubuntu Komputer Virtuals](/azure/iot-edge/how-to-install-iot-edge-ubuntuvm#deploy-from-azure-cli)
- [Menyeimbangkan beban mesin virtual Linux di Azure](/azure/virtual-machines/linux/tutorial-load-balancer)
- [Membuat dan mengelola jaringan virtual Azure untuk VM Linux](/azure/virtual-machines/linux/tutorial-virtual-network)
- [Mengonfigurasi titik akhir layanan untuk Cosmos DB](/azure/cosmos-db/how-to-configure-vnet-service-endpoint#configure-using-cli)

## <a name="see-also"></a>Lihat juga

- [Mulai gunakan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari penginstalan dan aktivitas masuk.

- Temukan referensi [inti](/cli/azure/reference-index) dan [ekstensi](./azure-cli-extensions-list.md) lainnya di dokumentasi Azure CLI.

- Kelola mesin virtual Linux atau Windows dengan [az vm](/cli/azure/vm).
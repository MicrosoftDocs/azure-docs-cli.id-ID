---
title: Azure CLI references for Azure Network | Microsoft Docs
description: Cari perintah referensi inti dan ekstensi Azure CLI untuk mengelola Azure Network. Mengelola layanan dan kemampuan jaringan secara efektif di Azure dari baris perintah.
author: dbradish-microsoft
manager: barbkess
ms.topic: reference
ms.date: 09/21/2021
ms.author: dbradish
ms.service: azure-cli
ms.devlang: azurecli
ms.reviewer: mohnader
ms.custom: devx-track-azurecli, seo-azure-cli
keywords: azure cli references, azure network
ms.openlocfilehash: 6e9736fd0a203977aa134881492986d613c0c7bb
ms.sourcegitcommit: 82cb7af10a689b9b485859552d2f834bd593f6a1
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 10/06/2021
ms.locfileid: "132439087"
---
# <a name="azure-cli-reference-commands-for-azure-network"></a>Azure CLI reference commands for Azure Network

Azure Command-Line Interface[(CLI)](./what-is-azure-cli.md)adalah seperangkat perintah yang digunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di banyak layanan Azure dan memberi Anda kemampuan untuk mengelola layanan jaringan dari baris perintah.

Perintah Azure CLI untuk [Azure Network](/azure/networking/) terdiri dari dua bagian: **inti** dan **ekstensi.** Inti Azure CLI perintah kapal sebagai bagian dari CLI dan didukung penuh. Ekstensi memberi Anda akses ke perintah eksperimental dan pra-rilis, dan secara otomatis diinstal saat pertama kali Anda menjalankan referensi ekstensi. Untuk informasi selengkapnya tentang referensi ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

Lihat [az network](/cli/azure/network) for a alphabetic list dari referensi inti dan ekstensi Azure CLI yang tersedia untuk layanan Azure Network. Untuk referensi untuk setiap subkelompok, lihat tabel di bagian berikut:

- [Jaringan virtual](#virtual-network-references)
- [Konektivitas WAN dan On-premise](#wan-and-on-premise-connectivity-references)
- [Load balancing dan IP](#load-balancing-and-ip-references)
- [Keamanan](#security-references)
- [Pemantauan](#monitoring-references)
- [Daftar](#list-references)

> [!NOTE]
> Anda diminta untuk menginstal referensi ekstensi pada penggunaan pertama. Atau, Anda dapat menggunakan `az extension add` perintah untuk menginstal ekstensi secara manual.

## <a name="virtual-network-references"></a>Referensi jaringan virtual 

| Subgrup | Referensi | Gunakan | Apakah ekstensi
|-|-|-|-|
| Appliance | [az network virtual-appliance](/cli/azure/network/virtual-appliance) | Kelola Azure Network Virtual Appliance.
| DNS | [az network private-dns](/cli/azure/network/private-dns) | Kelola domain DNS Pribadi di Azure. |
| Endpoint | [az network service-endpoint](/cli/azure/network/service-endpoint) | Mengelola kebijakan yang terkait dengan titik akhir layanan. |
| NAT | [az network nat](/cli/azure/network/nat) | Mengelola sumber daya terjemahan alamat jaringan. |
| NIC | [az network nic](/cli/azure/network/nic) | Mengelola antarmuka jaringan. |
| NIC | [az network nic vtap-config](/cli/azure/network/nic/vtap-config) | Mengelola konfigurasi ketuk jaringan virtual. | ya
| Peering | [az peering](/cli/azure/peering) | Mengelola mengintip. | ya
| Profil | [az network profile](/cli/azure/network/profile) | Mengelola profil jaringan. |
| Rute | [az network route-filter](/cli/azure/network/route-filter) | Mengelola filter rute. |
| Rute | [az network routeserver](/cli/azure/network/routeserver) | Mengelola server rute. |
| Rute | [az network route-table](/cli/azure/network/route-table) | Mengelola tabel rute. |
| VMware | [az network vmware](/cli/azure/vmware) | Perintah untuk mengelola Azure VMware Solutions. | ya
| vNet | [az network vnet](/cli/azure/network/vnet) | Kelola Azure Virtual Networks. |
| vNet | [az network vnet-tap](/cli/azure/network/vnet/tap) | Mengelola keran jaringan virtual. | ya
| vNet | [az network vnet-gateway](/cli/azure/network/vnet-gateway) | Gunakan Azure Virtual Network Gateway untuk membangun konektivitas lintas tempat yang aman. |

## <a name="wan-and-on-premise-connectivity-references"></a>Referensi konektivitas WAN dan On-premise

| Subgrup | Referensi | Gunakan | Apakah ekstensi
|-|-|-|-|
| Koneksi silang | [az network cross-connection](/cli/azure/network/cross-connection) | Kelola sumber daya Azure Network. | ya
| ExpressRoute | [az network express-route](/cli/azure/network/express-route) | Mengelola koneksi serat jaringan pribadi khusus ke Azure. |
| vHub | [az network vhub](/cli/azure/network/vhub) | Mengelola hub virtual. | ya
| VPN | [az network p2s-vpn-gateway](/cli/azure/network/p2s-vpn-gateway) | Kelola gateway VPN point-to-site. | ya
| VPN | [az network vpn-connection](/cli/azure/network/vpn-connection) | Mengelola koneksi VPN. |
| VPN | [az network vpn-gateway](/cli/azure/network/vpn-gateway) | Kelola gateway VPN. | ya
| VPN | [az network vpn-server-config](/cli/azure/network/vpn-server-config) | Kelola konfigurasi server VPN. | ya
| VPN | [az network vpn-site](/cli/azure/network/vpn-site) | Kelola konfigurasi situs VPN. | ya
| vRouter | [az network vrouter](/cli/azure/network/vrouter) | Mengelola router virtual. |
| vWAN | [az network vwan](/cli/azure/network/vwan) | Mengelola WAN virtual. | ya

## <a name="load-balancing-and-ip-references"></a>Load balancing dan referensi IP

| Subgrup | Referensi | Gunakan | Apakah ekstensi
|-|-|-|-|
| Gateway aplikasi | [az network application-gateway](/cli/azure/network/application-gateway) | Mengelola routing tingkat aplikasi dan layanan load-balancing. |
| Front Door | [az jaringan pintu depan](/cli/azure/network/front-door) | Mengelola sumber daya Front Door jaringan. | ya
| IP | [az network ip-group](/cli/azure/network/ip-group) | Mengelola IpGroups. | ya
| IP | [az network public-ip](/cli/azure/network/public-ip) | Mengelola alamat IP publik. |
| Keseimbangan beban | [az network cross-region-lb](/cli/azure/network/cross-region-lb) | Mengelola dan mengonfigurasi penyeimbang beban lintas wilayah. |
| Keseimbangan beban | [az network lb](/cli/azure/network/lb) | Mengelola dan mengkonfigurasi penyeimbang beban. |
| Gateway lokal | [az network local-gateway](/cli/azure/network/local-gateway) | Mengelola gateway lokal. |
| Traffic manager | [az network traffic-manager](/cli/azure/network/traffic-manager) | Mengelola perutean lalu lintas yang masuk. |

## <a name="security-references"></a>Referensi keamanan

| Subgrup | Referensi | Gunakan | Apakah ekstensi
|-|-|-|-|
| ASG | [az asg](/cli/azure/network/asg) | Mengelola grup keamanan aplikasi. |
| Bastion | [az network bastion](/cli/azure/network/bastion) | Kelola Azure bastion hosts. |
| DDoS | [az network ddos-protection](/cli/azure/network/ddos-protection) | Mengelola rencana perlindungan DDoS. |
| Firewall | [az network firewall](/cli/azure/network/firewall) | Mengelola dan mengkonfigurasi Azure Firewalls. | ya
| Firewall | [az network security-partner-provider](/cli/azure/network/security-partner-provider) | Kelola penyedia mitra keamanan Azure. |
| NSG | [az network nsg](/cli/azure/network/nsg)| Kelola Grup Keamanan Jaringan Azure. |
| Titik akhir privat | [az network private-endpoint](/cli/azure/network/private-endpoint) | Mengelola titik akhir pribadi. |
| Titik akhir privat | [az network private-endpoint-connection](/cli/azure/network/private-endpoint-connection) | Mengelola koneksi endpoint pribadi. |
| Tautan privat | [az network private-link-resource](/cli/azure/network/private-link-resource) | Mengelola sumber daya tautan pribadi. |
| Tautan privat | [az network private-link-service](/cli/azure/network/private-link-service) | Mengelola layanan tautan pribadi. |

## <a name="monitoring-references"></a>Referensi pemantauan

| Subgrup | Referensi | Gunakan | Apakah ekstensi
|-|-|-|-|
| Watcher | [az network watcher](/cli/azure/network/watcher) | Mengelola Azure Network Watcher. |

## <a name="list-references"></a>Referensi daftar

| Subgrup | Referensi | Gunakan | Apakah ekstensi
|-|-|-|-|
| Layanan | [az network list-service-aliases](/cli/azure/network#az_network_list_service_aliases) | Daftar alias layanan yang tersedia di wilayah yang dapat digunakan untuk Kebijakan Endpoint Layanan. |
| Layanan | [az network list-service-tags](/cli/azure/network#az_network_list_service_tags) | Daftar semua tag layanan yang termasuk dalam sumber daya yang berbeda. |
| Penggunaan | [az network list-usages](/cli/azure/network#az_network_list_usages) | Cantumkan jumlah sumber daya jaringan di wilayah yang digunakan untuk menggunakan kuota berlangganan. |

## <a name="popular-azure-network-articles-using-the-azure-cli"></a>Artikel Popular Azure Network menggunakan Azure CLI

- [Membuat mesin virtual](/cli/azure/azure-cli-vm-tutorial)
- [Membuat jaringan virtual](/azure/virtual-network/quick-create-cli)
- [Sampel Azure CLI untuk komputer virtual Windows](/azure/virtual-machines/windows/cli-samples?toc=%2Fcli%2Fazure%2Ftoc.json&bc=%2Fcli%2Fazure%2Fbreadcrumb%2Ftoc.json)
- [Membuat set skala komputer virtual](/azure/virtual-machine-scale-sets/quick-create-cli)
- [Menjalankan Azure IoT Edge di Ubuntu Komputer Virtuals](/azure/iot-edge/how-to-install-iot-edge-ubuntuvm#deploy-from-azure-cli)
- [Load balance Linux virtual machines in Azure](/azure/virtual-machines/linux/tutorial-load-balancer)
- [Membuat dan mengelola jaringan virtual Azure untuk VM Linux](/azure/virtual-machines/linux/tutorial-virtual-network)
- [Mengonfigurasi titik akhir layanan untuk Cosmos DB](/azure/cosmos-db/how-to-configure-vnet-service-endpoint#configure-using-cli)

## <a name="see-also"></a>Lihat juga

- [Mulai dengan Azure CLI](./get-started-with-azure-cli.md) untuk mempelajari tentang instalasi dan masuk.

- Temukan referensi [inti](/cli/azure/reference-index) dan [ekstensi](./azure-cli-extensions-list.md) tambahan dalam dokumentasi Azure CLI.

- Kelola Linux atau Windows mesin virtual dengan [az vm](/cli/azure/vm).
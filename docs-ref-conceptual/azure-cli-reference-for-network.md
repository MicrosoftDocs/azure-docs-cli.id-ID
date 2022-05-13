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
ms.openlocfilehash: bf0754024dee57ae0af1c0582654cada541d2158
ms.sourcegitcommit: 4293ab0b6b4c04df8018d6dfd999db69b1becdd5
ms.translationtype: MT
ms.contentlocale: id-ID
ms.lasthandoff: 05/13/2022
ms.locfileid: "144977041"
---
# <a name="azure-cli-reference-commands-for-azure-network"></a>Perintah referensi Azure CLI untuk Azure Network

Azure Command-Line Interface ([CLI](./what-is-azure-cli.md)) adalah sekumpulan perintah yang digunakan untuk membuat dan mengelola sumber daya Azure. Ini tersedia di banyak layanan Azure yang memungkinkan Anda mengelola layanan jaringan dari baris perintah.

Perintah Azure CLI untuk [Azure Network](/azure/networking/) terdiri dari dua bagian: **inti** dan **ekstensi**. Perintah Azure CLI inti dikirimkan sebagai bagian dari CLI dan didukung sepenuhnya. Ekstensi memberi Anda akses ke perintah percobaan dan pra-rilis, dan otomatis diinstal saat Anda menjalankan referensi ekstensi untuk pertama kali. Untuk informasi selengkapnya tentang ekstensi, lihat [Menggunakan ekstensi dengan Azure CLI](./azure-cli-extensions-overview.md).

Lihat [az network](../latest/docs-ref-autogen/network.yml) untuk mengetahui daftar alfabetik referensi inti dan ekstensi Azure CLI yang tersedia untuk layanan Azure Network. Untuk referensi setiap sub-grup, lihat tabel di bagian berikut:

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
| Appliance | [az network virtual-appliance](../latest/docs-ref-autogen/network/virtual-appliance.yml) | Mengelola Azure Network Virtual Appliance.
| DNS | [az network private-dns](../latest/docs-ref-autogen/network/private-dns.yml) | Mengelola domain DNS Privat di Azure. |
| Titik akhir | [az network service-endpoint](../latest/docs-ref-autogen/network/service-endpoint.yml) | Mengelola kebijakan yang terkait dengan titik akhir layanan. |
| NAT | [az network nat](../latest/docs-ref-autogen/network/nat.yml) | Mengelola sumber daya terjemahan alamat jaringan. |
| NIC | [az network nic](../latest/docs-ref-autogen/network/nic.yml) | Mengelola antarmuka jaringan. |
| NIC | [az network nic vtap-config](../latest/docs-ref-autogen/network/nic/vtap-config.yml) | Mengelola konfigurasi pengetukan jaringan virtual. | ya
| Peering | [az peering](../latest/docs-ref-autogen/peering.yml) | Mengelola peering. | ya
| Profil | [az network profile](../latest/docs-ref-autogen/network/profile.yml) | Mengelola profil jaringan. |
| Rute | [az network route-filter](../latest/docs-ref-autogen/network/route-filter.yml) | Mengelola filter rute. |
| Rute | [az network routeserver](../latest/docs-ref-autogen/network/routeserver.yml) | Mengelola server rute. |
| Rute | [az network route-table](../latest/docs-ref-autogen/network/route-table.yml) | Mengelola tabel rute. |
| VMware | [az network vmware](../latest/docs-ref-autogen/vmware.yml) | Perintah untuk mengelola Azure VMware Solution. | ya
| vNet | [az network vnet](../latest/docs-ref-autogen/network/vnet.yml) | Mengelola Azure Virtual Networks. |
| vNet | [az network vnet-tap](../latest/docs-ref-autogen/network/vnet/tap.yml) | Mengelola pengetukan jaringan virtual. | ya
| vNet | [az network vnet-gateway](../latest/docs-ref-autogen/network/vnet-gateway.yml) | Gunakan Azure Virtual Network Gateway untuk membangun konektivitas lintas lokal yang aman. |

## <a name="wan-and-on-premise-connectivity-references"></a>Referensi WAN dan Konektivitas lokal

| Subgrup | Referensi | Penggunaan | Berupa ekstensi
|-|-|-|-|
| Lintas koneksi | [az network cross-connection](../latest/docs-ref-autogen/network/cross-connection.yml) | Mengelola sumber daya Azure Network. | ya
| ExpressRoute | [az network express-route](../latest/docs-ref-autogen/network/express-route.yml) | Mengelola koneksi fiber jaringan privat khusus ke Azure. |
| vHub | [az network vhub](../latest/docs-ref-autogen/network/vhub.yml) | Mengelola hub virtual. | ya
| VPN | [az network p2s-vpn-gateway](../latest/docs-ref-autogen/network/p2s-vpn-gateway.yml) | Mengelola gateway VPN titik-ke-situs. | ya
| VPN | [az network vpn-connection](../latest/docs-ref-autogen/network/vpn-connection.yml) | Mengelola koneksi VPN. |
| VPN | [az network vpn-gateway](../latest/docs-ref-autogen/network/vpn-gateway.yml) | Mengelola gateway VPN. | ya
| VPN | [az network vpn-server-config](../latest/docs-ref-autogen/network/vpn-server-config.yml) | Mengelola konfigurasi server VPN. | ya
| VPN | [az network vpn-site](../latest/docs-ref-autogen/network/vpn-site.yml) | Mengelola konfigurasi situs VPN. | ya
| vRouter | [az network vrouter](../latest/docs-ref-autogen/network/vrouter.yml) | Mengelola router virtual. |
| vWAN | [az network vwan](../latest/docs-ref-autogen/network/vwan.yml) | Mengelola WAN virtual. | ya

## <a name="load-balancing-and-ip-references"></a>Referensi penyeimbangan beban dan IP

| Subgrup | Referensi | Penggunaan | Berupa ekstensi
|-|-|-|-|
| Gateway aplikasi | [az network application-gateway](../latest/docs-ref-autogen/network/application-gateway.yml) | Mengelola layanan penyeimbangan beban dan perutean tingkat aplikasi. |
| Front Door | [az network front-door](../latest/docs-ref-autogen/network/front-door.yml) | Mengelola sumber daya Front Door jaringan. | ya
| IP | [az network ip-group](../latest/docs-ref-autogen/network/ip-group.yml) | Mengelola IpGroups. | ya
| IP | [az network public-ip](../latest/docs-ref-autogen/network/public-ip.yml) | Mengelola alamat IP publik. |
| Keseimbangan beban | [az network cross-region-lb](../latest/docs-ref-autogen/network/cross-region-lb.yml) | Mengelola dan mengonfigurasi penyeimbang beban lintas wilayah. |
| Keseimbangan beban | [az network lb](../latest/docs-ref-autogen/network/lb.yml) | Mengelola dan mengonfigurasi penyeimbang beban. |
| Gateway lokal | [az network local-gateway](../latest/docs-ref-autogen/network/local-gateway.yml) | Mengelola gateway lokal. |
| Traffic manager | [az network traffic-manager](../latest/docs-ref-autogen/network/traffic-manager.yml) | Mengelola perutean lalu lintas masuk. |

## <a name="security-references"></a>Referensi keamanan

| Subgrup | Referensi | Penggunaan | Berupa ekstensi
|-|-|-|-|
| ASG | [az asg](../latest/docs-ref-autogen/network/asg.yml) | Mengelola kelompok keamanan aplikasi. |
| Bastion | [az network bastion](../latest/docs-ref-autogen/network/bastion.yml) | Mengelola host bastion Azure. |
| DDoS | [az network ddos-protection](../latest/docs-ref-autogen/network/ddos-protection.yml) | Mengelola Paket DDoS Protection. |
| Firewall | [az network firewall](../latest/docs-ref-autogen/network/firewall.yml) | Mengelola dan mengonfigurasi Azure Firewalls. | ya
| Firewall | [az network security-partner-provider](../latest/docs-ref-autogen/network/security-partner-provider.yml) | Mengelola penyedia mitra keamanan Azure. |
| NSG | [az network nsg](../latest/docs-ref-autogen/network/nsg.yml)| Mengelola Kelompok keamanan Jaringan Azure. |
| Titik akhir privat | [az network private-endpoint](../latest/docs-ref-autogen/network/private-endpoint.yml) | Mengelola titik akhir privat. |
| Titik akhir privat | [az network private-endpoint-connection](../latest/docs-ref-autogen/network/private-endpoint-connection.yml) | Mengelola koneksi titik akhir privat. |
| Tautan privat | [az network private-link-resource](../latest/docs-ref-autogen/network/private-link-resource.yml) | Mengelola sumber daya tautan privat. |
| Tautan privat | [az network private-link-service](../latest/docs-ref-autogen/network/private-link-service.yml) | Mengelola layanan tautan privat. |

## <a name="monitoring-references"></a>Referensi pemantauan

| Subgrup | Referensi | Penggunaan | Berupa ekstensi
|-|-|-|-|
| Watcher | [az network watcher](../latest/docs-ref-autogen/network/watcher.yml) | Mengelola Azure Network Watcher. |

## <a name="list-references"></a>Referensi daftar

| Subgrup | Referensi | Penggunaan | Berupa ekstensi
|-|-|-|-|
| Layanan | [az network list-service-aliases](/cli/azure/network#az_network_list_service_aliases) | Mencantumkan alias layanan yang tersedia di wilayah yang dapat digunakan untuk Kebijakan Titik Akhir Layanan. |
| Layanan | [az network list-service-tags](/cli/azure/network#az_network_list_service_tags) | Mencantumkan semua tag layanan milik sumber daya yang berbeda. |
| Penggunaan | [az network list-usages](/cli/azure/network#az_network_list_usages) | Mencantumkan jumlah sumber daya jaringan di wilayah yang digunakan terhadap kuota langganan. |

## <a name="popular-azure-network-articles-using-the-azure-cli"></a>Artikel Populer Azure Network menggunakan Azure CLI

- [Membuat komputer virtual](./azure-cli-vm-tutorial.yml)
- [Membuat jaringan virtual](/azure/virtual-network/quick-create-cli)
- [Sampel Azure CLI untuk komputer virtual Windows](/azure/virtual-machines/windows/cli-samples?toc=%2Fcli%2Fazure%2Ftoc.json&bc=%2Fcli%2Fazure%2Fbreadcrumb%2Ftoc.json)
- [Membuat set skala komputer virtual](/azure/virtual-machine-scale-sets/quick-create-cli)
- [Menjalankan Azure IoT Edge di Ubuntu Komputer Virtuals](/azure/iot-edge/how-to-install-iot-edge-ubuntuvm#deploy-from-azure-cli)
- [Menyeimbangkan beban mesin virtual Linux di Azure](/azure/virtual-machines/linux/tutorial-load-balancer)
- [Membuat dan mengelola jaringan virtual Azure untuk VM Linux](/azure/virtual-machines/linux/tutorial-virtual-network)
- [Mengonfigurasi titik akhir layanan untuk Cosmos DB](/azure/cosmos-db/how-to-configure-vnet-service-endpoint#configure-using-cli)

## <a name="see-also"></a>Lihat juga

* Kelola mesin virtual Linux atau Windows dengan [az vm](../latest/docs-ref-autogen/vm.yml).
* Temukan [perintah referensi](../latest/docs-ref-autogen/reference-index.yml) tambahan dan [ekstensi yang tersedia](./azure-cli-extensions-list.md) dalam dokumentasi Azure CLI.
* [Pelajari cara menggunakan Bash dengan Azure CLI](./azure-cli-learn-bash.md)

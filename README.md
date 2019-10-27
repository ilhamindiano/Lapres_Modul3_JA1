# Lapres_Modul3_JA1

## Setting Topologi

![Capture](https://user-images.githubusercontent.com/42942671/67634385-ade64e00-f8ed-11e9-8987-8717dc7cd564.PNG)

## Setting DHCP awal

- Buat file konfigurasi nano /etc/default/isc-dhcp-server
- Tentukan interface INTERFACES="eth2"
- Buat file konfigurasi dhcp server nano /etc/dhcp/dhcpd.conf
- Install dhcp relay
- Konfigurasi relay

![relay](https://user-images.githubusercontent.com/42942671/67634489-47622f80-f8ef-11e9-85c3-8a14f51837a5.PNG)


1. Seluruh client TIDAK DIPERBOLEHKAN menggunakan konfigurasi IP Statis.

- Tambahkan syntax berikut pada nano/etc/network/interfaces pada setiap uml client

```
auto eth0
iface eth0 inet dhcp
```

- 

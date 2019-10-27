# Lapres_Modul3_JA1

## Setting Topologi

![Capture](https://user-images.githubusercontent.com/42942671/67634385-ade64e00-f8ed-11e9-8987-8717dc7cd564.PNG)

## Setting DHCP awal

- Buat file konfigurasi 
```
nano /etc/default/isc-dhcp-server
```
- Tentukan interface 
```
INTERFACES="eth2"
```
- Buat file konfigurasi dhcp server 
```
nano /etc/dhcp/dhcpd.conf
```
- Install dhcp relay
- Konfigurasi relay

![relay](https://user-images.githubusercontent.com/42942671/67634489-47622f80-f8ef-11e9-85c3-8a14f51837a5.PNG)

- Restart dhcp server dengan service isc-dhcp-server restart

## Seluruh client TIDAK DIPERBOLEHKAN menggunakan konfigurasi IP Statis.

- Tambahkan syntax berikut pada nano/etc/network/interfaces pada setiap uml client

```
auto eth0
iface eth0 inet dhcp
```

1. Client di subnet 2 mendapatkan peminjaman alamat IP dengan range 192.168.0.2 s.d.
192.168.0.10 dan 192.168.0.20 s.d. 192.168.0.30 dengan netmask 255.255.255.0.

- Konfigurasi pada file config dhcp
```
nano /etc/dhcp/dhcpd.conf
```
- Isi sebagai berikut :

![2 1](https://user-images.githubusercontent.com/42942671/67634669-9d37d700-f8f1-11e9-8ba6-abb91029a277.PNG)

2. Client di subnet 3 mendapatkan peminjaman alamat IP dengan range dari 192.168.1.2 s.d.
192.168.1.99 dengan netmask 255.255.255.0.

- Konfigurasi pada file config dhcp
```
nano /etc/dhcp/dhcpd.conf
```
- Isi sebagai berikut :

![3 1](https://user-images.githubusercontent.com/42942671/67634671-9d37d700-f8f1-11e9-9d0c-e3779bf79cfb.PNG)

3. Client di subnet 2 mendapatkan peminjaman alamat IP selama 10 menit dan client di
subnet 3 mendapatkan peminjaman alamat IP selama 5 menit.

- Konfigurasi pada file config dhcp
```
nano /etc/dhcp/dhcpd.conf
```
- Isi sebagai berikut :

![2 1](https://user-images.githubusercontent.com/42942671/67634669-9d37d700-f8f1-11e9-8ba6-abb91029a277.PNG)

![3 1](https://user-images.githubusercontent.com/42942671/67634671-9d37d700-f8f1-11e9-9d0c-e3779bf79cfb.PNG)

4. Masing-masing client harus mendapatkan konfigurasi DNS / nameserver yang terdiri atas
IP ARTICUNO, 202.46.129.2, dan 10.151.36.7 secara otomatis.

- Konfigurasi pada file config dhcp
```
nano /etc/dhcp/dhcpd.conf
```
- Isi sebagai berikut :

![4 1](https://user-images.githubusercontent.com/42942671/67634772-a07f9280-f8f2-11e9-9292-05ce55feeffb.PNG)


5. Client PSYDUCK selalu mendapatkan IP 192.168.1.28, TANPA menggunakan
konfigurasi IP Statis.

- Konfigurasi pada file config dhcp
```
nano /etc/dhcp/dhcpd.conf
```
- Isi sebagai berikut :

![5 1](https://user-images.githubusercontent.com/42942671/67634830-26034280-f8f3-11e9-8ec6-fec4b0714698.PNG)

- Konfigurasi nano /etc/network/interfaces pada psyduck

![5 3](https://user-images.githubusercontent.com/42942671/67634854-5f3bb280-f8f3-11e9-9678-a5211c4ef0da.PNG)

![5 2](https://user-images.githubusercontent.com/42942671/67634831-26034280-f8f3-11e9-8bc6-41deff86005e.PNG)

6. Prof. Oak meminta anda membuatkan user
otentikasi dengan format:

● User : yy_moltres_user
● Password : yy_password

Note: yy adalah nama kelompok masing-masing. Contoh : a1_moltres_user

-

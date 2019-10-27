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

- Install squid3 
```
apt-get install squid3
```
- Backup data
```
mv /etc/squid3/squid.conf /etc/squid3/squid.conf.bak
```
- Buat config
```
nano /etc/squid3/squid.conf
```
- Install apache2-utils
```
apt-get install apache2-utils
```
- Buat user dan password baru
```
htpasswd -c /etc/squid3/passwd a1_moltres_user
```
- Edit konfigurasi squid

![6](https://user-images.githubusercontent.com/42942671/67634941-2b14c180-f8f4-11e9-8628-7d6cc71a54ac.PNG)

- jika sudah berhasil maka muncul notifikasi login saat mengakses web

![login](https://user-images.githubusercontent.com/42942671/67635438-ed1a9c00-f8f9-11e9-913d-301fa1478503.PNG)


7. Untuk Client pada subnet 2 HANYA BISA mengakses internet pada hari Senin
s.d. Jumat pukul 11.00 s.d. 13.00 WIB

dan 

8. Untuk Client pada subnet 3 HANYA BISA mengakses internet pada hari Senin
s.d. Jumat pukul 20.00 s.d. 07.00 WIB pada keesokan harinya.

- Edit konfigurasi squid

![8 1](https://user-images.githubusercontent.com/42942671/67635015-ce65d680-f8f4-11e9-8240-57cc9e7ff111.PNG)

![8 2](https://user-images.githubusercontent.com/42942671/67635016-ce65d680-f8f4-11e9-8759-4dccceb3cef6.PNG)

9. setiap
ada koneksi dari subnet AJK (10.151.36.0/24) yang mengakses google.com akan langsung dialihkan
menuju duckduckgo.com.

10. Selain itu, demi menjaga keamanan kota Pallet, anda diminta untuk
mem-block setiap koneksi yang berasal dari subnet Informatics_wifi (10.151.252.0/22) menuju
http://10.151.36.5:5000, sebab subnet Informatics_wifi adalah milik tim Rocket.

- Edit konfigurasi squid

![10 1](https://user-images.githubusercontent.com/42942671/67635073-3caa9900-f8f5-11e9-808d-63288115d5ea.PNG)

![10 2](https://user-images.githubusercontent.com/42942671/67635074-3caa9900-f8f5-11e9-8b50-389cdd407df5.PNG)

- jika sudah berhasil maka jika http://10.151.36.5:5000/ diakses

![10r](https://user-images.githubusercontent.com/42942671/67635458-23581b80-f8fa-11e9-9e02-cfa2e1bf4535.PNG)

11. Karena menurut Prof. Oak menghafalkan IP Proxy kota Pallet cukup merepotkan, kalian diminta
untuk mempermudah trainer dan penduduk dalam menggunakan Proxy yaitu cukup dengan
mengetikkan proxy.yy.com dan memasukkan port 8888.

- Install elinks pada tiap client
- Tambahkan pada konfigurasi elinks

![11 1](https://user-images.githubusercontent.com/42942671/67635106-8c896000-f8f5-11e9-8dc6-978bc87ec1cc.PNG)

- jika sudah berhasil maka jika di ping akan berhasil

![11r](https://user-images.githubusercontent.com/42942671/67635431-c5c3cf00-f8f9-11e9-8cae-61c075391244.PNG)

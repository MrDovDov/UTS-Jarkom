# Essay

## 1. Apa itu Routing Static?
Routing Static merupakan teknik mengatur rute jaringan secara manual di perangkat seperti router untuk mengarahkan data dari satu jaringan ke jaringan lain.

## 2. Apa itu Routing Dynamic?
Routing Dynamic merupakan teknik routing dalam jaringan komputer di mana rute atau jalur pengiriman data ditentukan dan diperbarui secara otomatis oleh router dengan menggunakan protokol routing dinamis.

## 3. Apa itu Firewall?
Firewall merupakan sistem keamanan penting dalam jaringan komputer yang melindungi jaringan dari akses yang tidak sah dan ancaman eksternal. Dengan memfilter dan memantau lalu lintas data, firewall membantu menjaga keamanan jaringan, mengontrol akses pengguna, serta mencegah penyebaran malware.

## 4. Apa itu NAT?
NAT merupakan teknologi yang memungkinkan perangkat dalam jaringan lokal berbagi alamat IP publik untuk mengakses jaringan eksternal, seperti internet.

# Cased

# Konfigurasi IP

**R1 Citra**

1. hubungkan router ke internet menggunakan dhcp Client
   ip -> dhcp client -> + -> ether 1 -> klik Ok

apabila status bound berarti sudah terkoneksi

2. Tambahkan Ip address
   ip->addresses -> +
   ip 1, 192.168.10.1/24 -> Ether 2
   ip 2, 14.14.14.1/24 -> IPIP Tunnel

3. Buat Dhcp Server untuk Ether 2
   ip -> Dhcp Server -> Dhcp Setup -> Next hingga selesai

**R2 KJ**

1. hubungkan router ke internet menggunakan dhcp Client
   ip -> dhcp client -> + -> ether 1 -> klik Ok

apabila status bound berarti sudah terkoneksi

2. Tambahkan Ip address
   ip->addresses -> +
   ip 1, 192.168.20.1/24 -> Ether 2
   ip 2, 14.14.14.2/24 -> IPIP Tunnel
   IP 3, 13.13.13.1/24 -> IPIP Tunnel

3. Buat Dhcp Server untuk Ether 2
   ip -> Dhcp Server -> Dhcp Setup -> Next hingga selesai

**R3 KHI**

1. hubungkan router ke internet menggunakan dhcp Client
   ip -> dhcp client -> + -> ether 1 -> klik Ok

apabila status bound berarti sudah terkoneksi

2. Tambahkan Ip address
   ip->addresses -> +
   ip 1, 192.168.30.1/24 -> Ether 2
   ip 2, 13.13.13.2/24 -> IPIP Tunnel

3. Buat Dhcp Server untuk Ether 2
   ip -> Dhcp Server -> Dhcp Setup -> Next hingga selesai

# Konfigurasi IP-in-IP (IPIP)

**R1 Citra**

1. Untuk menambahkan interface IPIP Tunnel

- buka menu Interface > IP Tunnel > Add :

Local address : 203.0.113.1/24

- buka menu Interface > IP Tunnel > Add :

Local address : 203.0.113.1/24

**R2 KJ**

1. Untuk menambahkan interface IPIP Tunnel

- buka menu Interface > IP Tunnel > Add :

Local address : 203.0.114.1/24

- buka menu Interface > IP Tunnel > Add :

Local address : 203.0.114.1/24
**R3 KHI**

1. Untuk menambahkan interface IPIP Tunnel

- buka menu Interface > IP Tunnel > Add :

Local address : 203.0.115.1/24

- buka menu Interface > IP Tunnel > Add :

Local address : 203.0.115.1/24

# Konfigurasi routing

**R1 CR**

1. Ip -> routes -> +

Ke R2
- dst address 192.168.20.0/24
- gateway 14.14.14.2

Ke R3
- dst address 192.168.30.0/24
- gateway 13.13.13.2

**R2 KJ**

1. Ip -> routes -> +

Ke R1
- dst address 192.168.10.0/24
- gateway 12.12.12.1

Ke R3
- dst address 192.168.30.0/24
- gateway 11.11.11.2

**R3 KHI**

1. Ip -> routes -> +

Ke R1
- dst address 192.168.10.0/24
- gateway 14.14.14.1

Ke R2
- dst address 192.168.20.0/24
- gateway 13.13.13.1

![Topologi Diagram](<Topologi Diagram.png>)

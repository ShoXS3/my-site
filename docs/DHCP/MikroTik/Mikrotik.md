# Bab 1: Membuat Server DHCP dengan MikroTik
## Membuat Server DHCP

Untuk mengatur server DHCP pada perangkat MikroTik, ikuti langkah-langkah berikut:

### 1. Akses Command Line Interface (CLI):
Hubungkan ke router MikroTik melalui Winbox atau SSH.

### 2. Masuk ke Mode Eksekutif Berhak (Privileged EXEC):
Jika belum berada dalam Mode Eksekutif Berhak, gunakan perintah `/system routerboard` untuk masuk.

### 3. Masuk ke Mode Konfigurasi Global:
Masuk ke Mode Konfigurasi Global dengan perintah:

```
/ip dhcp-server
```
### 4. Tentukan Pool Alamat DHCP:
Konfigurasi pool DHCP dengan menentukan rentang alamat IP untuk klien. Gunakan perintah berikut:

```
/ip pool add name=pool1 ranges=192.168.1.10-192.168.1.100
```
Tentukan pengaturan jaringan dan gateway default:
```
/ip dhcp-server network add address=192.168.1.0/24 gateway=192.168.1.1 dns-server=8.8.8.8
```
### 5. Atur Parameter lease DHCP(Optional)
Konfigurasi waktu `Lease` untuk alamat IP menggunakan perintah berikut:

```
/ip dhcp-server set [find name=dhcp1] lease-time=1d
```
### 6. Aktifkan Layanan DHCP:
Keluar dari mode konfigurasi DHCP dengan mengetik exit. Aktifkan DHCP pada antarmuka tertentu:

```
/interface ethernet set [find name=ether1] dhcp-server=pool1
```
Gantilah ether1 dengan nama antarmuka yang sebenarnya.

Router MikroTik Anda sekarang sudah dikonfigurasi sebagai server DHCP, memberikan alamat IP kepada klien dalam rentang yang ditentukan.



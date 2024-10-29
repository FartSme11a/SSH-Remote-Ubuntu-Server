# Remote Ubuntu Server Menggunakan SSH dari Ubuntu Desktop dan Mengubah Port SSH
Laporan ini menjelaskan langkah-langkah untuk melakukan remote server Ubuntu menggunakan SSH dari Ubuntu Desktop serta mengubah port default SSH dari 22 menjadi 40.
## Menginstal dan set up ubuntu server

## Langkah-langkah 
### 1. Mengaktifkan SSH pada Server Ubuntu
Untuk meninstalnya dapat menggunakan command:
- $ sudo apt install openssh-server
### 2. Mengubah Port SSH menjadi 40
- Buka file konfigurasi SSH di server menggunakan command: sudo nano /etc/ssh/sshd_config.
- Cari baris yang berisi #Port 22, lalu ubah menjadi Port 40 (tanda # dihapus juga).
- Pada editor Nano, tekan Ctrl+O lalu Enter untuk menyimpan, dan Ctrl+X untuk keluar.
- Restart layanan SSH untuk menerapkan perubahan dengan cara keluar dari ubuntu server tadi lalu masuk kembali
- Setelah selesai, cek status layanan SSH untuk memastikan bahwa portnya telah berubah menjadi 40, menggunakn command: $ sudo systemctl status ssh
### 3. Mengakses Ubuntu Server dari Ubuntu Desktop dengan SSH
- Buka terminal di Ubuntu Desktop.
- install ssh nya menggunakan command: $ sudo apt install openssh-client
- Jalankan perintah berikut untuk melakukan remote ke server: ssh -p 40 username@server_ip
- Konfirmasi Koneksi: Jika ini pertama kalinya terhubung ke server tersebut, maka akan diminta untuk mengonfirmasi koneksi. Ketik yes lalu tekan Enter.
- Masukkan Password: Masukkan password dari akun username di server dan tekan Enter
- login telah berhasil, sekarang telah terhubung ke server Ubuntu dan dapat mengelola server dari jarak jauh menggunakan ubuntu desktop
- Untuk keluar dari sesi remote SSH dan kembali ke desktop Ubuntu seperti semula dapat menggunakan command: $ exit

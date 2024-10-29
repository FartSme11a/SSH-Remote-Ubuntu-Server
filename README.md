# Remote Ubuntu Server Menggunakan SSH dari Ubuntu Desktop dan Mengubah Port SSH
Laporan ini menjelaskan langkah-langkah untuk melakukan remote server Ubuntu menggunakan SSH dari Ubuntu Desktop serta mengubah port default SSH dari 22 menjadi 40.
## Menginstal dan Set Up Ubuntu Server
- download iso ubuntu server di ubuntu.com
- masuk ke virtual box dan klik new di kanan atas untuk membuat virtual machine baru
- lalu di set up nama virtual machinenya, masukkan iso ubuntu servernya, berap banyak penyimpanan,ram dan cpu yang akan digunakan. lalu klik finish jika sudah
- pada virtual machine yang isinya ubuntu server tadi, klik kanan dan pergi ke setting, lalu ke network dan ganti attached to NAT menjadi attached to Bridge Adapter, lalu klik ok
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/2908d5315631dbc35f058e4c4445596a335757e3/Screenshot%20(243).png)
- klik start di ujung kanan
- klik enter di try or install
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(244).png)
- tunggu sampai proses selesai
- pilih bahasanya lalu enter
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(247).png)
- untuk chose configuration, saya langsung klik enter di done
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(249).png)
- untuk choose type of installation, saya klik enter di done
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(251).png)
- untuk network connection, saya klik enter di done
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(252).png)
- untuk proxy connection, saya klik enter di done
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(253).png)
- untuk ubuntu archive mirror, saya klik enter di done
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(254).png)
- untuk guided storage configuration, saya klik enter di done
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(255).png)
- untuk di storage configuratuion, saya klik enter di done, lalu enter di continue
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(257).png)
- masukkan name, server name,username dan pasword lalu klik enter di done
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(258).png)
- untuk upgrade ubuntu pro, saya klik enter di continue
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(259).png)
- untuk ssh setup, pada kotak instal openssh saya klik spasi untuk mencetangkan kotak tersebut, lalu kebawah untuk menekan enter di done
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(260).png)
- untuk featured snaps, saya klik enter di done
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(262).png)
- untuk isntalling sistem tunggu sampai complete lalu pilih reboot now
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/47772d1e15aa34d9b345c8d33f4b03f4ee57317f/Screenshot%20(265).png)
- kalau sudah masuk di terminal masukkan nama dan pasword. maka server ubuntu sudah siap
## Langkah-langkah 
### 1. Mengaktifkan SSH pada Server Ubuntu
Untuk menginstalnya ssh di server gunakan command:
- $ sudo apt install openssh-server
### 2. Mengubah Port SSH menjadi 40
- Buka file konfigurasi SSH di server menggunakan command: sudo nano /etc/ssh/sshd_config.
- Cari baris yang berisi #Port 22, lalu ubah menjadi Port 40 (tanda # dihapus juga).
- Pada editor Nano, tekan Ctrl+O lalu Enter untuk menyimpan, dan Ctrl+X untuk keluar.
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/673a8b27cffa9ea7a03e66ffbc3b0b582637f320/Screenshot%20(267).png)
- Restart layanan SSH untuk menerapkan perubahan dengan commad: $ sudo systemctl restart ssh ,atau keluar dari ubuntu server tadi lalu masuk kembali
- Cek status layanan SSH untuk memastikan bahwa portnya telah berubah menjadi 40, menggunakn command: $ sudo systemctl status ssh
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/673a8b27cffa9ea7a03e66ffbc3b0b582637f320/Screenshot%20(270).png)
### 3. Melihat ip address server
menggunakan command:
- $ ip addr
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/673a8b27cffa9ea7a03e66ffbc3b0b582637f320/Screenshot%20(272).png)
### 3. Mengakses Ubuntu Server dari Ubuntu Desktop dengan SSH
- Buka terminal di Ubuntu Desktop.
- install ssh nya menggunakan command: $ sudo apt install openssh-client
- Jalankan perintah berikut untuk melakukan remote ke server: ssh -p 40 username@server_ip
- Konfirmasi Koneksi: Jika ini pertama kalinya terhubung ke server tersebut, maka akan diminta untuk mengonfirmasi koneksi. Ketik yes lalu tekan Enter.
- Masukkan Password: Masukkan password dari akun username di server dan tekan Enter
![image alt](https://github.com/M-Prakarsa-Al-Islam/SSH-Remote-Ubuntu-Server/blob/673a8b27cffa9ea7a03e66ffbc3b0b582637f320/Screenshot%20(273).png)
- login telah berhasil, sekarang telah terhubung ke server Ubuntu dan dapat mengelola server dari jarak jauh menggunakan ubuntu desktop
- Untuk keluar dari sesi remote SSH dan kembali ke desktop Ubuntu seperti semula dapat menggunakan command: $ exit

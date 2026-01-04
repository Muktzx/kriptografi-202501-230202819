# Laporan Praktikum Kriptografi
Minggu ke-: 12 
Topik: Aplikasi TLS & E-commerce  
Nama: Mukti Ali Raja  
NIM: 230202819  
Kelas: 5IKRA  

---

## 1. Tujuan
Tujuan dari praktikum ini adalah untuk menganalisis penerapan kriptografi pada komunikasi berbasis SSL/TLS, khususnya pada layanan email dan website e-commerce, serta mengevaluasi isu etika dan privasi yang muncul dari penggunaan kriptografi dalam kehidupan sehari-hari.

---

## 2. Dasar Teori
SSL (Secure Sockets Layer) dan TLS (Transport Layer Security) merupakan protokol keamanan yang digunakan untuk melindungi komunikasi data pada jaringan komputer. TLS adalah pengembangan dari SSL dan saat ini menjadi standar utama dalam pengamanan komunikasi web melalui protokol HTTPS. TLS menyediakan tiga aspek keamanan utama, yaitu kerahasiaan data (encryption), integritas data (message integrity), dan autentikasi (authentication) menggunakan sertifikat digital.

Dalam implementasinya, TLS menggunakan kombinasi kriptografi kunci publik dan kunci simetris. Kriptografi kunci publik (seperti RSA atau ECDSA) digunakan pada proses handshake untuk pertukaran kunci secara aman, sedangkan kriptografi kunci simetris (seperti AES) digunakan untuk mengenkripsi data selama sesi komunikasi berlangsung karena lebih efisien.

Pada email dan e-commerce, TLS berperan penting dalam melindungi informasi sensitif seperti kredensial login, data pribadi, dan informasi pembayaran. Tanpa TLS, data dapat dengan mudah disadap oleh pihak tidak bertanggung jawab melalui serangan seperti Man-in-the-Middle (MITM).
---

## 3. Alat dan Bahan
Web Browser (Google Chrome / Mozilla Firefox)

Koneksi Internet

Git dan akun GitHub

Sistem Operasi Windows/Linux

---

## 4. Langkah Percobaan
Membuat folder praktikum/week12-aplikasi-tls/.

Mengakses website e-commerce menggunakan browser (contoh: Tokopedia dan Shopee).

Mengecek sertifikat digital dengan mengklik ikon gembok (HTTPS) pada address bar.

Mencatat informasi sertifikat seperti Certificate Authority (CA), masa berlaku, dan algoritma enkripsi.

Membandingkan perbedaan website yang menggunakan HTTPS dan HTTP.

Menganalisis peran TLS dalam proses login dan transaksi e-commerce.

Mengambil screenshot sertifikat digital sebagai dokumentasi.

Menyusun laporan praktikum dan melakukan commit ke GitHub.
---

## 5. Source Code
Pada praktikum ini tidak dilakukan pembuatan source code karena fokus kegiatan adalah analisis dan observasi penerapan TLS/SSL pada website dan email.
```


---

## 6. Hasil dan Pembahasan
Hasil observasi menunjukkan bahwa website e-commerce seperti Tokopedia dan Shopee telah menggunakan protokol HTTPS dengan sertifikat digital yang valid dan dikeluarkan oleh Certificate Authority terpercaya. Sertifikat masih dalam masa berlaku dan menggunakan algoritma kriptografi modern seperti RSA/ECDSA dan AES.

Penggunaan TLS terbukti melindungi data pengguna, terutama saat proses login dan transaksi pembayaran. Jika TLS tidak digunakan, data sensitif dapat disadap atau dimodifikasi oleh penyerang melalui serangan Man-in-the-Middle.
---

## 7. Jawaban Pertanyaan
Pertanyaan 1: Apa perbedaan utama antara HTTP dan HTTPS?

Jawaban: HTTP mengirimkan data dalam bentuk plaintext tanpa enkripsi, sedangkan HTTPS menggunakan TLS untuk mengenkripsi data sehingga lebih aman dari penyadapan.

Pertanyaan 2: Mengapa sertifikat digital menjadi penting dalam komunikasi TLS?

Jawaban: Sertifikat digital berfungsi untuk memverifikasi identitas server dan mencegah serangan Man-in-the-Middle dengan memastikan bahwa pengguna berkomunikasi dengan server yang sah.

Pertanyaan 3: Bagaimana kriptografi mendukung privasi namun menimbulkan tantangan etika?

Jawaban: Kriptografi melindungi privasi pengguna dengan enkripsi data, namun dapat menyulitkan penegakan hukum dan menimbulkan dilema etika terkait pengawasan komunikasi.
---

## 8. Kesimpulan
TLS merupakan komponen penting dalam keamanan komunikasi digital, khususnya pada layanan email dan e-commerce. Penggunaan TLS mampu melindungi data sensitif pengguna, namun juga menimbulkan tantangan etika dan privasi yang perlu diatur melalui kebijakan yang tepat.

---

## 9. Daftar Pustaka
Stallings, W. (2017). Cryptography and Network Security. Pearson.

Kahn Academy. HTTPS and TLS.
---

## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: Mukti Ali Raja <muktialir2207@gmail.com>
Date:   2026-01-04

    week12-aplikasi-tls
```

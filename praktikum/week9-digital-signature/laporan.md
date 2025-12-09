# Laporan Praktikum Kriptografi
Minggu ke-: 9
Topik: Digital Signature (RSA)  
Nama: Mukti Ali Raja
NIM: 230202819
Kelas: 5IKRA

---

## 1. Tujuan
Tujuan praktikum ini adalah:

Mengimplementasikan tanda tangan digital menggunakan algoritma RSA.

Melakukan verifikasi tanda tangan digital dengan public key.

Menganalisis peran tanda tangan digital dalam memastikan autentikasi dan integritas pesan.

Melakukan pengujian pada kasus pesan yang dimodifikasi dan menunjukkan kegagalan verifikasi.

---

## 2. Dasar Teori
Tanda tangan digital adalah mekanisme kriptografi yang memungkinkan seseorang membuktikan bahwa sebuah pesan benar berasal dari pengirim tertentu, sekaligus memastikan bahwa pesan tersebut tidak diubah. Tidak seperti enkripsi, tanda tangan digital menggunakan private key untuk menandatangani pesan, dan public key untuk memverifikasi keaslian tanda tangan.

RSA Digital Signature bekerja berdasarkan prinsip aritmetika modular dan sifat fungsi satu arah. Pesan terlebih dahulu di-hash menggunakan fungsi hash kriptografis seperti SHA-256, kemudian hash tersebut ditandatangani menggunakan private key. Pihak lain dapat memverifikasi tanda tangan dengan public key, memastikan integritas data dan autentikasi pengirim.

Dalam sistem modern, tanda tangan digital sering digunakan bersama Certificate Authority (CA) untuk memastikan bahwa public key benar-benar dimiliki oleh identitas yang sah. Hal ini mencegah serangan peniruan identitas (spoofing).
---

## 3. Alat dan Bahan
Python 3.11 atau lebih baru

Visual Studio Code / editor lain

Git dan akun GitHub

Library tambahan:

pycryptodome

Terminal / Command Prompt

---

## 4. Langkah Percobaan
Membuat folder praktikum/week9-digital-signature/src/.

Membuat file signature.py.

Menyalin kode program dari modul untuk:
generate key RSA
membuat digital signature
memverifikasi sign
menguji modifikasi pesan
Menginstal library PyCryptodome dengan perintah:
pip install pycryptodome
Menjalankan program dengan perintah:

python signature.py


Mengambil screenshot hasil eksekusi dan menyimpannya pada folder screenshots/.
Menyusun laporan dan melakukan commit Git sesuai format.
---

## 5. Source Code
(Salin kode program utama yang dibuat atau dimodifikasi.  
Gunakan blok kode:

```python
# contoh potongan kode
def encrypt(text, key):
    return ...
```
)

---

## 6. Hasil dan Pembahasan
<img width="1920" height="1014" alt="image" src="https://github.com/user-attachments/assets/865d91bf-33f1-4d33-9e28-342014f3d093" />

Pembahasan

Hasil eksekusi menunjukkan bahwa tanda tangan digital berhasil diverifikasi ketika pesan masih asli.
Ketika pesan dimodifikasi, verifikasi gagal. Ini menunjukkan bahwa tanda tangan digital menjamin integritas data.
Tanda tangan yang dibuat dengan private key hanya dapat diverifikasi dengan public key yang sesuai, sehingga memberikan autentikasi pengirim.
Tidak ditemukan error dalam program, dan seluruh proses berjalan sesuai ekspektasi praktikum.

---

## 7. Jawaban Pertanyaan
1. Apa perbedaan utama antara enkripsi RSA dan tanda tangan digital RSA?

Enkripsi RSA menggunakan public key untuk mengenkripsi dan private key untuk mendekripsi.
Tanda tangan digital RSA melakukan proses sebaliknya: private key untuk menandatangani dan public key untuk memverifikasi.
Tujuannya juga berbeda: enkripsi menjaga kerahasiaan, sedangkan tanda tangan digital menjaga autentikasi dan integritas.

2. Mengapa tanda tangan digital menjamin integritas dan otentikasi pesan?

Karena tanda tangan dibuat dari hash pesan dan private key pengirim.
Jika pesan berubah sedikit saja, hasil hash berubah total sehingga verifikasi akan gagal.
Hanya pemilik private key yang dapat membuat tanda tangan valid, sehingga penerima dapat mengetahui siapa pembuat pesan.

3. Bagaimana peran Certificate Authority (CA) dalam sistem tanda tangan digital modern?

CA bertugas mengeluarkan sertifikat digital yang menghubungkan public key dengan identitas resmi pemiliknya.
Dengan demikian, CA mencegah penyerang mengirimkan public key palsu dan mengaku sebagai orang lain.
---

## 8. Kesimpulan
Praktikum ini berhasil menunjukkan implementasi tanda tangan digital menggunakan RSA. Hasil eksperimen membuktikan bahwa verifikasi tanda tangan hanya akan berhasil apabila pesan tidak dimodifikasi. Tanda tangan digital terbukti sangat penting dalam menjamin integritas dan autentikasi komunikasi data modern.
---

## 9. Daftar Pustaka
Stinson, D. (2019). Cryptography: Theory and Practice.
Stallings, W. (2017). Cryptography and Network Security.
PyCryptodome Documentation.

---

## 10. Commit Log
commit week9-digital-signature
Author: Mukti Ali Raja <muktialir2207@gmail.com>
Date:   2025-XX-XX

    week9-digital-signature: implementasi RSA digital signature, verifikasi, dan laporan

```

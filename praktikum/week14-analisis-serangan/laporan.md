# Laporan Praktikum Kriptografi
Minggu ke-: 14
Topik: Analisis Serangan Kriptografi pada Sistem Nyata  
Nama: Mukti Ali Raja  
NIM: 230202819 
Kelas: 5IKRA 

---


## 1. Tujuan
Tujuan dari praktikum ini adalah untuk memahami jenis-jenis serangan kriptografi yang terjadi pada sistem informasi nyata, menganalisis kelemahan algoritma atau mekanisme keamanan yang digunakan, serta memberikan rekomendasi solusi kriptografi yang lebih aman guna meningkatkan keamanan sistem.

---

## 2. Dasar Teori
Kriptografi merupakan ilmu yang mempelajari teknik pengamanan informasi agar data tidak dapat dibaca atau dimodifikasi oleh pihak yang tidak berwenang. Dalam sistem informasi modern, kriptografi digunakan untuk menjaga kerahasiaan (confidentiality), integritas (integrity), dan autentikasi (authentication). Algoritma kriptografi yang umum digunakan antara lain fungsi hash, enkripsi simetris, dan enkripsi asimetris.

Namun, penggunaan algoritma kriptografi yang sudah usang atau konfigurasi yang tidak tepat dapat menyebabkan sistem rentan terhadap serangan. Salah satu contoh serangan yang sering terjadi adalah brute force dan dictionary attack pada password yang disimpan menggunakan algoritma hash lemah seperti MD5. Hash MD5 sudah tidak direkomendasikan karena memiliki collision dan dapat dipecahkan dengan cepat menggunakan perangkat keras modern.

Menurut Stallings (2017), keamanan sistem kriptografi tidak hanya bergantung pada algoritma yang digunakan, tetapi juga pada implementasi dan konfigurasi sistem. Oleh karena itu, evaluasi menyeluruh diperlukan untuk menentukan sumber kelemahan dan solusi yang tepat.

---

## 3. Alat dan Bahan
- Python 3.x  
- Visual Studio Code  
- Git dan akun GitHub  
- Library Python standar (hashlib)  

---

## 4. Langkah Percobaan
1. Membuat folder `praktikum/week14-analisis-serangan/`.
2. Membuat file `laporan.md` sebagai laporan praktikum.
3. Melakukan simulasi hashing password menggunakan algoritma MD5 dengan Python.
4. Melakukan percobaan brute force sederhana terhadap hash MD5.
5. Mendokumentasikan hasil percobaan dalam bentuk screenshot.
6. Menganalisis kelemahan sistem dan memberikan rekomendasi solusi.
7. Melakukan commit ke repository Git dengan pesan `week14-analisis-serangan`.

---

## 5. Source Code
Berikut contoh kode sederhana untuk menghasilkan hash MD5 dari sebuah password menggunakan Python:

python
import hashlib

password = "password123"
hash_md5 = hashlib.md5(password.encode()).hexdigest()

print("Password:", password)
print("Hash MD5:", hash_md5)

---

## 6. Hasil dan Pembahasan
Berdasarkan hasil percobaan, password yang di-hash menggunakan algoritma MD5 menghasilkan nilai hash yang tetap dan dapat direproduksi. Hash ini kemudian dapat dicocokkan dengan daftar hash yang tersedia pada wordlist atau database hash yang sudah diketahui.

Hasil ini menunjukkan bahwa MD5 sangat rentan terhadap brute force dan dictionary attack karena proses hashingnya cepat dan tidak menggunakan salt. Dengan menggunakan perangkat keras modern, penyerang dapat mencoba jutaan kombinasi password dalam waktu singkat
---

## 7. Jawaban Pertanyaan
1. Mengapa banyak sistem lama masih rentan terhadap brute force atau dictionary attack?
Banyak sistem lama masih menggunakan algoritma kriptografi yang sudah tidak aman seperti MD5 atau SHA-1. Selain itu, sistem tersebut sering kali tidak diperbarui karena keterbatasan biaya, ketergantungan pada sistem lama, atau kurangnya kesadaran akan pentingnya keamanan informasi.

2. Apa bedanya kelemahan algoritma dengan kelemahan implementasi?
Kelemahan algoritma terjadi ketika algoritma kriptografi itu sendiri sudah terbukti tidak aman secara matematis. Sedangkan kelemahan implementasi terjadi akibat kesalahan dalam penerapan algoritma, seperti tidak menggunakan salt, konfigurasi keamanan yang buruk, atau manajemen kunci yang lemah.

3. Bagaimana organisasi dapat memastikan sistem kriptografi mereka tetap aman di masa depan?
Organisasi dapat memastikan keamanan dengan melakukan pembaruan algoritma secara berkala, mengikuti standar keamanan terbaru, melakukan audit keamanan rutin, serta menerapkan best practice seperti penggunaan algoritma modern (bcrypt, Argon2, TLS 1.3) dan pelatihan keamanan bagi pengembang.
---

## 8. Kesimpulan
Dari praktikum ini dapat disimpulkan bahwa penggunaan algoritma kriptografi yang lemah dapat menyebabkan sistem rentan terhadap serangan. Oleh karena itu, pemilihan algoritma yang aman dan implementasi yang tepat sangat penting untuk menjaga keamanan sistem informasi.

---

## 9. Daftar Pustaka
Stallings, W. (2017). Cryptography and Network Security: Principles and Practice. Pearson.

Katz, J., & Lindell, Y. (2014). Introduction to Modern Cryptography. CRC Press.

---

## 10. Commit Log
commit a1b2c3d4
Author: Mukti Ali Raj <muktialir2207@gmail.com>
Date:   2026-01-12

    week14-analisis-serangan

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```

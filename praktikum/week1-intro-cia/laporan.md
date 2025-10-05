# Laporan Praktikum Kriptografi
Minggu ke-: 1  
Topik: Sejarah Kriptografi & Prinsip CIA 

Nama: Mukti Ali Raja  
NIM: 230202819  
Kelas: 5IKRA 

---

## 1. Tujuan
Ringkasan Sejarah Kriptografi
Kriptografi telah mengalami perjalanan panjang dari era klasik hingga kontemporer. Pada era kriptografi klasik, metode yang digunakan masih sederhana dan berbasis pada manipulasi huruf. Salah satu contoh awal adalah Caesar Cipher, yang menggeser huruf dalam alfabet dengan jumlah tertentu untuk menyamarkan pesan. Kemudian muncul Vigenere Cipher yang menggunakan kunci berupa kata atau frasa untuk melakukan substitusi polialfabetik, sehingga lebih sulit dipecahkan dibanding Caesar. Namun, metode klasik ini akhirnya lemah karena perkembangan analisis kriptografi.

Memasuki era kriptografi modern, teknologi komputer memunculkan algoritma yang lebih kompleks dan aman. Salah satu yang paling terkenal adalah RSA (Rivest–Shamir–Adleman), algoritma kunci publik yang memungkinkan enkripsi dan tanda tangan digital berbasis teori bilangan. Selain itu, AES (Advanced Encryption Standard) menjadi standar internasional untuk enkripsi simetris karena kekuatan dan efisiensinya dalam melindungi data digital. Pada masa ini, kriptografi mulai digunakan secara luas dalam transaksi online, komunikasi aman, dan perlindungan data.

Dalam era kriptografi kontemporer, kebutuhan akan keamanan yang lebih transparan dan terdistribusi melahirkan teknologi baru seperti blockchain. Teknologi ini menggunakan prinsip kriptografi hash dan tanda tangan digital untuk menjaga integritas transaksi secara desentralisasi. Implementasi terbesarnya adalah pada cryptocurrency seperti Bitcoin, yang memanfaatkan kriptografi untuk mengamankan jaringan, memastikan transparansi, dan mencegah pemalsuan. Evolusi ini menunjukkan bahwa kriptografi bukan sekadar alat penyamaran pesan, tetapi kini menjadi fondasi utama keamanan digital global.

---

## 2. Dasar Teori
1. Confidentiality (Kerahasiaan)

Kerahasiaan bertujuan memastikan bahwa data hanya dapat diakses oleh pihak yang berwenang. Hal ini mencegah kebocoran informasi sensitif kepada pihak yang tidak sah.

Contoh nyata: Data perbankan nasabah yang dilindungi dengan enkripsi end-to-end pada layanan mobile banking, sehingga hanya nasabah dan bank yang dapat membaca informasi transaksi.

2. Integrity (Integritas)

Integritas berarti menjaga keaslian dan keutuhan data agar tidak diubah, dihapus, atau dimodifikasi oleh pihak yang tidak sah. Data yang rusak atau dimanipulasi dapat mengakibatkan keputusan yang salah dan merugikan organisasi maupun pengguna.

Contoh nyata: Sistem hashing pada file update perangkat lunak. Pengguna bisa memverifikasi apakah file instalasi yang diunduh benar-benar asli dan tidak dimodifikasi hacker melalui pencocokan hash (misalnya SHA-256).

3. Availability (Ketersediaan)

Ketersediaan menekankan agar layanan, data, dan sistem selalu dapat digunakan ketika dibutuhkan oleh pengguna yang sah. Gangguan ketersediaan bisa berdampak pada kelumpuhan layanan.

Contoh nyata: Penyedia layanan e-commerce menggunakan server backup dan proteksi DDoS untuk memastikan situs tetap dapat diakses oleh pelanggan meskipun sedang terjadi lonjakan trafik atau upaya serangan.

---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `caesar_cipher.py` di folder `praktikum/week2-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python caesar_cipher.py`.)

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
(- Lampirkan screenshot hasil eksekusi program (taruh di folder `screenshots/`).  
- Berikan tabel atau ringkasan hasil uji jika diperlukan.  
- Jelaskan apakah hasil sesuai ekspektasi.  
- Bahas error (jika ada) dan solusinya. 

Hasil eksekusi program Caesar Cipher:

![Hasil Eksekusi](screenshots/output.png)
![Hasil Input](screenshots/input.png)
![Hasil Output](screenshots/output.png)
)

---

## 7. Jawaban Pertanyaan
(Jawab pertanyaan diskusi yang diberikan pada modul.  
- Pertanyaan 1: …  
- Pertanyaan 2: …  
)
---

## 8. Kesimpulan
(Tuliskan kesimpulan singkat (2–3 kalimat) berdasarkan percobaan.  )

---

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: Nama Mahasiswa <email>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```

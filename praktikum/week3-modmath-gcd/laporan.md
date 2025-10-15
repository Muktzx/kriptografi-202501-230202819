# Laporan Praktikum Kriptografi
Minggu ke-: 3
Topik: Modular Math (Aritmetika Modular, GCD, Bilangan Prima, dan Logaritma Diskrit)  
Nama: Mukti Ali Raja  
NIM: 230202819  
Kelas: 5IKRA  

---

## 1. Tujuan
Menyelesaikan operasi aritmetika modular (penjumlahan, pengurangan, perkalian, dan eksponensiasi).
Menentukan bilangan prima dan menghitung GCD (Greatest Common Divisor) menggunakan algoritma Euclidean.
Mengimplementasikan Extended Euclidean Algorithm untuk mencari invers modular.
Menerapkan logaritma diskrit sederhana sebagai simulasi konsep dasar dalam kriptografi modern.

---

## 2. Dasar Teori
Aritmetika modular merupakan cabang matematika yang berhubungan dengan operasi aritmetika dalam sistem bilangan yang berulang (modulus). Dalam sistem ini, dua bilangan dikatakan kongruen jika memiliki sisa pembagian yang sama terhadap suatu bilangan modulus 𝑛, Operasi ini menjadi dasar dari banyak algoritma kriptografi modern seperti RSA, Diffie-Hellman, dan ECC.

Greatest Common Divisor (GCD) adalah bilangan bulat terbesar yang dapat membagi dua bilangan tanpa sisa. GCD dapat dihitung dengan algoritma Euclidean, yang bekerja secara efisien melalui proses pembagian berulang. Versi lanjutannya, yaitu Extended Euclidean Algorithm, digunakan untuk mencari invers modular, yang sangat penting dalam kriptografi kunci publik.

Sementara itu, logaritma diskrit adalah permasalahan mencari nilai 𝑥 pada persamaan 𝑎𝑥≡𝑏(mod𝑛)
Permasalahan ini sangat sulit diselesaikan ketika modulus 𝑛, sangat besar, dan karena itulah menjadi dasar keamanan berbagai sistem kriptografi modern seperti Diffie–Hellman Key Exchange.

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

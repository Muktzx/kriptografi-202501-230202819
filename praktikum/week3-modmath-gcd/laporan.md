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
# -*- coding: utf-8 -*-
# modular_math.py
# Praktikum Week 3 - Modular Math, GCD, dan Logaritma Diskrit

# ============================
# 1. Operasi Aritmetika Modular
# ============================

def mod_add(a, b, n): 
    return (a + b) % n

def mod_sub(a, b, n): 
    return (a - b) % n

def mod_mul(a, b, n): 
    return (a * b) % n

def mod_exp(base, exp, n): 
    return pow(base, exp, n)  # eksponensiasi modular

print("=== Modular Arithmetic ===")
print("7 + 5 mod 12 =", mod_add(7, 5, 12))
print("7 * 5 mod 12 =", mod_mul(7, 5, 12))
print("7^128 mod 13 =", mod_exp(7, 128, 13))


# ==============================
# 2. GCD dengan Algoritma Euclid
# ==============================

def gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

print("\n=== GCD (Euclidean Algorithm) ===")
print("gcd(54, 24) =", gcd(54, 24))


# =======================================
# 3. Extended Euclidean & Invers Modular
# =======================================

def egcd(a, b):
    if a == 0:
        return b, 0, 1
    g, x1, y1 = egcd(b % a, a)
    return g, y1 - (b // a) * x1, x1

def modinv(a, n):
    g, x, _ = egcd(a, n)
    if g != 1:
        return None  # tidak adAa invers jika gcd(a, n) ≠ 1
    return x % n

print("\n=== Extended Euclidean Algorithm ===")
print("Invers 3 mod 11 =", modinv(3, 11))  # hasil: 4


# ============================================
# 4. Logaritma Diskrit (Discrete Logarithm)
# ============================================

def discrete_log(a, b, n):
    for x in range(n):
        if pow(a, x, n) == b:
            return x
    return None

print("\n=== Discrete Logarithm ===")
print("3^x == 4 (mod 7), x =", discrete_log(3, 4, 7))  # hasil: 4


# ============================================
# 5. Kesimpulan Eksekusi
# ============================================
print("\n=== Summary ===")
print("Semua fungsi berjalan dengan benar tanpa error encoding.")


---

## 6. Hasil dan Pembahasan
(- Lampirkan screenshot hasil eksekusi program (taruh di folder `screenshots/`).  
- Berikan tabel atau ringkasan hasil uji jika diperlukan.  
- Jelaskan apakah hasil sesuai ekspektasi.  
- Bahas error (jika ada) dan solusinya. 

Hasil eksekusi program Caesar Cipher:

![Hasil Eksekusi](screenshots/output.png)
![Hasil Input](screenshots/input.png)
<img width="1365" height="721" alt="HASIK Kode week 3" src="https://github.com/user-attachments/assets/0704d1b4-df8b-4899-a447-f5a62b427bd6" />

![Hasil Output](screenshots/output.png)
)

---

## 7. Jawaban Pertanyaan
Pertanyaan 1:
Apa peran aritmetika modular dalam kriptografi modern?
 Aritmetika modular digunakan untuk memastikan operasi matematika tetap berada dalam ruang bilangan terbatas (finite field). Ini memungkinkan pembentukan sistem enkripsi yang aman seperti RSA, di mana operasi enkripsi dan dekripsi menggunakan pangkat dan modulus besar.

Pertanyaan 2:
Mengapa invers modular penting dalam algoritma kunci publik (misalnya RSA)?
 Invers modular digunakan untuk proses dekripsi. Pada RSA, kunci privat dihitung sebagai invers modular dari kunci publik terhadap fungsi totien Euler, memastikan hanya pemilik kunci privat yang bisa mendekripsi pesan.

Pertanyaan 3:
Apa tantangan utama dalam menyelesaikan logaritma diskrit untuk modulus besar?
Tantangan utamanya adalah kompleksitas komputasi yang sangat tinggi. Tidak ada algoritma efisien untuk menghitung logaritma diskrit pada bilangan besar, sehingga sulit diselesaikan secara praktis — hal ini menjadi dasar keamanan sistem kriptografi seperti Diffie-Hellman.
)
---

## 8. Kesimpulan
Dari percobaan ini dapat disimpulkan bahwa operasi aritmetika modular, GCD, dan logaritma diskrit merupakan konsep dasar penting dalam kriptografi. Implementasi algoritma Euclidean dan invers modular membantu memahami cara kerja sistem kunci publik seperti RSA. Program Python berhasil dijalankan dengan hasil sesuai teori tanpa error.
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
Author: Muktialiraja <Muktialir2207@gmail.com>
Date:   2025-10-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```

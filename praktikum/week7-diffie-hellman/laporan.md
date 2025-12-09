# Laporan Praktikum Kriptografi
Minggu ke-: X  
Topik: Diffie-Hellman Key Exchange 
Nama: Mukti Ali Raja 
NIM: 230202819
Kelas: 5IKRA

---

## 1. Tujuan
Melakukan simulasi protokol Diffie–Hellman untuk pertukaran kunci publik.

Menjelaskan mekanisme pertukaran kunci rahasia menggunakan bilangan prima dan logaritma diskrit.

Melakukan analisis keamanan protokol, termasuk potensi serangan Man-in-the-Middle (MITM).

Menghasilkan laporan praktikum dan commit Git dengan struktur folder yang benar.
---

## 2. Dasar Teori
Diffie–Hellman Key Exchange adalah sebuah protokol kriptografi yang memungkinkan dua pihak bertukar sebuah kunci rahasia melalui saluran komunikasi publik. Protokol ini bekerja berdasarkan konsep modular exponentiation dan kesulitan Discrete Logarithm Problem (DLP). Dengan menggunakan bilangan prima besar dan generator, dua pihak dapat menghasilkan shared secret yang identik tanpa pernah mengirimkan kunci rahasia tersebut secara langsung.

Keamanan protokol ini terletak pada fakta bahwa meskipun nilai publik g^a mod p dan g^b mod p diketahui oleh pihak luar, sangat sulit untuk menghitung nilai a atau b (private key). Hal ini membuat Diffie–Hellman menjadi dasar bagi banyak protokol keamanan modern, seperti TLS. Namun, karena protokol aslinya tidak menyediakan autentikasi, Diffie–Hellman rentan terhadap serangan Man-in-the-Middle apabila tidak dilengkapi mekanisme validasi identitas.

---

## 3. Alat dan Bahan
Python 3.11 atau lebih baru

Visual Studio Code / editor teks

Git dan akun GitHub

Terminal / Command Prompt

Folder praktikum: praktikum/week7-diffie-hellman/
---

## 4. Langkah Percobaan
Membuat folder:
praktikum/week7-diffie-hellman/src/, screenshots/, dan laporan.md.

Membuat file program Python bernama diffie_hellman.py di folder src/.

Menyalin kode simulasi Diffie–Hellman dari modul praktikum.

Menjalankan program menggunakan perintah:

python diffie_hellman.py


Membuat simulasi tambahan untuk serangan MITM.

Mengambil screenshot hasil eksekusi program dan menyimpannya ke folder screenshots/.

Mengisi laporan dan melakukan commit Git sesuai instruksi.
---

## 5. Source Code
import random

# parameter umum (dipublikasikan)
p = 23  # bilangan prima
g = 5   # generator

# private key
a = random.randint(1, p - 1)  # Alice
b = random.randint(1, p - 1)  # Bob

# public key
A = pow(g, a, p)
B = pow(g, b, p)

# shared secret
shared_secret_A = pow(B, a, p)
shared_secret_B = pow(A, b, p)

print("=== Diffie-Hellman Normal ===")
print("Kunci bersama Alice :", shared_secret_A)
print("Kunci bersama Bob   :", shared_secret_B)

# Simulasi MITM
print("\n=== MITM Attack Simulation ===")

e1 = random.randint(1, p - 1)
e2 = random.randint(1, p - 1)

E1 = pow(g, e1, p)  # dikirim ke Alice
E2 = pow(g, e2, p)  # dikirim ke Bob

shared_A_EVE = pow(E1, a, p)
shared_B_EVE = pow(E2, b, p)

print("Kunci Alice-Eve :", shared_A_EVE)
print("Kunci Bob-Eve   :", shared_B_EVE)
print("Alice dan Bob TIDAK memiliki kunci yang sama!")


---

## 6. Hasil dan Pembahasan
<img width="1920" height="1040" alt="image" src="https://github.com/user-attachments/assets/7a301393-a005-4665-888e-f70043e04e3c" />
  
Contoh tampilan hasil:

=== Diffie-Hellman Normal ===
Kunci bersama Alice : 2
Kunci bersama Bob   : 2

=== MITM Attack Simulation ===
Kunci Alice-Eve : 6
Kunci Bob-Eve   : 4
Alice dan Bob TIDAK memiliki kunci yang sama!

Pembahasan

Pada simulasi normal, nilai shared secret Alice dan Bob sama, menunjukkan protokol berhasil.

Pada simulasi MITM, kunci yang dimiliki Alice dan Bob berbeda karena public key telah diganti oleh Eve.

Eve mampu membangun dua kunci rahasia: satu dengan Alice dan satu dengan Bob, sehingga ia dapat membaca dan memodifikasi pesan di antara mereka.

Hal ini menunjukkan bahwa Diffie–Hellman tanpa autentikasi rentan terhadap MITM.
---

## 7. Jawaban Pertanyaan
1. Mengapa Diffie–Hellman memungkinkan pertukaran kunci di saluran publik?

Karena protokol ini hanya menukar nilai publik (g, p, g^a mod p, g^b mod p) dan menggunakan sifat modular exponentiation yang sulit dibalik tanpa mengetahui nilai a atau b. A dan B dapat diketahui publik, tetapi kunci rahasia g^(ab) mod p tetap aman karena Discrete Logarithm Problem.

2. Apa kelemahan utama protokol Diffie–Hellman murni?

Diffie–Hellman tidak menyediakan autentikasi, sehingga siapapun dapat menyisipkan public key palsu dan melakukan serangan Man-in-the-Middle (MITM).

3. Bagaimana cara mencegah serangan MITM?

Menggunakan digital signature untuk menandatangani public key.

Menggunakan sertifikat digital (TLS/SSL).

Menggunakan Authenticated Diffie–Hellman seperti DHE-RSA atau ECDHE.

Menggunakan key confirmation protocol.
---

## 8. Kesimpulan
Praktikum ini menunjukkan bahwa Diffie–Hellman dapat menghasilkan kunci bersama melalui saluran publik berkat sifat sulitnya menghitung logaritma diskrit. Namun, protokol dasar ini tidak aman dari MITM jika tidak ada autentikasi tambahan. Oleh karena itu, implementasi nyata harus menggunakan versi Diffie–Hellman yang terautentikasi.
---

## 9. Daftar Pustaka
Stallings, W. (2017). Cryptography and Network Security: Principles and Practice.

Katz, J., & Lindell, Y. (2021). Introduction to Modern Cryptography.

Diffie, W., & Hellman, M. (1976). New Directions in Cryptography.
---

## 10. Commit Log
commit week7-diffie-hellman
Author: Mukti Ali Raja <muktialir2207@gmail.com>
Date:   2025-XX-XX

    week7-diffie-hellman: implementasi Diffie-Hellman, simulasi MITM, dan laporan
```

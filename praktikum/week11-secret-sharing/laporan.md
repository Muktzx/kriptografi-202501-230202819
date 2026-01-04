# Laporan Praktikum Kriptografi
Minggu ke-: 11 
Topik: [judul praktikum]  
Nama: Mukti ALi Raja  
NIM: 230202819 
Kelas: 5IKRA 

---

## 1. Tujuan
Tujuan dari praktikum ini adalah untuk memahami konsep dasar Shamir’s Secret Sharing (SSS), mengimplementasikan skema pembagian rahasia menggunakan Python, serta menganalisis tingkat keamanan distribusi rahasia berbasis threshold (k, n).

---

## 2. Dasar Teori
Shamir’s Secret Sharing (SSS) merupakan salah satu skema kriptografi yang digunakan untuk membagi sebuah rahasia (secret) menjadi beberapa bagian yang disebut share. Skema ini diperkenalkan oleh Adi Shamir pada tahun 1979 dan termasuk ke dalam skema secret sharing dengan model threshold (k, n), di mana rahasia hanya dapat direkonstruksi jika minimal k dari n share digabungkan.

Dasar matematis dari SSS adalah polinomial berderajat k−1 dalam aritmetika modular. Rahasia disimpan sebagai konstanta polinomial (a₀), sedangkan koefisien lainnya dipilih secara acak. Setiap share merupakan pasangan nilai (x, f(x)) yang dihasilkan dari evaluasi polinomial tersebut pada nilai x yang berbeda.

Keamanan Shamir’s Secret Sharing bersifat perfect secrecy, artinya kepemilikan kurang dari k share tidak memberikan informasi apa pun mengenai rahasia asli. Rekonstruksi rahasia dilakukan menggunakan teknik interpolasi Lagrange dalam modulo bilangan prima.

---

## 3. Alat dan Bahan
Python 3.11

Visual Studio Code

Git dan akun GitHub

Library Python (opsional): secretsharing
---

## 4. Langkah Percobaan
Membuat struktur folder praktikum/week11-secret-sharing/.

Membuat file secret_sharing.py di folder src/.

Mengimplementasikan algoritma Shamir Secret Sharing menggunakan Python.

Menentukan nilai rahasia (secret), jumlah share (n), dan threshold (k).

Menjalankan program untuk membagi rahasia menjadi beberapa share.

Melakukan rekonstruksi rahasia menggunakan minimal k share.

Mengambil screenshot hasil eksekusi program.

Menyusun laporan praktikum dan melakukan commit ke GitHub.
---

## 5. Source Code
# ============================================
# Shamir's Secret Sharing (Manual Implementation)
# Praktikum Kriptografi - Week 11
# ============================================

import random

# Bilangan prima besar (untuk operasi modulo)
P = 208351617316091241234326746312124448251235562226470491514186331217050270460481


def generate_polynomial(secret, k):
    """
    Membuat polinomial berderajat (k-1)
    a0 = secret
    a1..a(k-1) = bilangan acak
    """
    coefficients = [secret]
    for _ in range(k - 1):
        coefficients.append(random.randrange(1, P))
    return coefficients


def evaluate_polynomial(coeffs, x):
    """
    Menghitung f(x) = a0 + a1*x + a2*x^2 + ... (mod P)
    """
    result = 0
    for power, coef in enumerate(coeffs):
        result = (result + coef * pow(x, power, P)) % P
    return result


def split_secret(secret, k, n):
    """
    Membagi secret menjadi n share dengan threshold k
    """
    polynomial = generate_polynomial(secret, k)
    shares = []

    for x in range(1, n + 1):
        y = evaluate_polynomial(polynomial, x)
        shares.append((x, y))

    return shares


def recover_secret(shares):
    """
    Rekonstruksi secret menggunakan Lagrange Interpolation
    """
    secret = 0

    for j, (xj, yj) in enumerate(shares):
        numerator = 1
        denominator = 1

        for m, (xm, _) in enumerate(shares):
            if m != j:
                numerator = (numerator * (-xm)) % P
                denominator = (denominator * (xj - xm)) % P

        lagrange_coefficient = numerator * pow(denominator, -1, P)
        secret = (P + secret + (yj * lagrange_coefficient)) % P

    return secret


# =======================
# MAIN PROGRAM
# =======================
if __name__ == "__main__":
    print("=== SHAMIR'S SECRET SHARING ===")

    # Rahasia (harus berupa bilangan)
    secret = 123456
    k = 3   # threshold
    n = 5   # jumlah share

    print(f"\nSecret       : {secret}")
    print(f"Threshold (k): {k}")
    print(f"Total share  : {n}")

    # Membagi secret
    shares = split_secret(secret, k, n)

    print("\nGenerated Shares:")
    for share in shares:
        print(f"Share {share[0]}: {share}")

    # Rekonstruksi menggunakan k share
    selected_shares = shares[:k]
    recovered_secret = recover_secret(selected_shares)

    print("\nReconstruction using shares:")
    for s in selected_shares:
        print(s)

    print("\nRecovered Secret:", recovered_secret)

    # Validasi
    if recovered_secret == secret:
        print("\n[✓] Secret berhasil direkonstruksi dengan benar")
    else:
        print("\n[✗] Rekonstruksi secret gagal")

```
)

---

## 6. Hasil dan Pembahasan
Program berhasil membagi rahasia menjadi 5 buah share dengan threshold 3. Rekonstruksi rahasia menggunakan 3 share pertama menghasilkan nilai rahasia yang sama dengan secret awal.

Hasil ini sesuai dengan teori Shamir’s Secret Sharing, di mana minimal k share diperlukan untuk merekonstruksi rahasia. Ketika jumlah share kurang dari k, rahasia tidak dapat direkonstruksi
<img width="1263" height="959" alt="image" src="https://github.com/user-attachments/assets/a8798225-103a-42c1-a5ea-71076ee188a6" />

---

## 7. Jawaban Pertanyaan
Pertanyaan 1: Apa keuntungan utama Shamir Secret Sharing dibanding membagikan salinan kunci secara langsung?
Jawaban: Keuntungan utama SSS adalah peningkatan keamanan, karena rahasia tidak disimpan dalam satu tempat dan tidak dapat diketahui jika hanya sebagian share yang bocor.
Pertanyaan 2: Apa peran threshold (k) dalam keamanan secret sharing?
Jawaban: Threshold (k) menentukan jumlah minimum share yang dibutuhkan untuk merekonstruksi rahasia. Semakin besar nilai k, semakin tinggi tingkat keamanan namun semakin berisiko jika share hilang.
Pertanyaan 3: Berikan satu contoh penerapan nyata SSS.
Jawaban: Shamir Secret Sharing digunakan dalam manajemen private key cryptocurrency dan sistem recovery akses tingkat tinggi.

## 8. Kesimpulan
Shamir’s Secret Sharing merupakan metode distribusi rahasia yang aman dan efisien. Praktikum ini menunjukkan bahwa rahasia hanya dapat direkonstruksi dengan jumlah share minimum sesuai threshold. Skema ini sangat bermanfaat dalam sistem keamanan modern.

---

## 9. Daftar Pustaka
Stinson, D. R. (2019). Cryptography: Theory and Practice. CRC Press.

Katz, J., & Lindell, Y. Introduction to Modern Cryptography.

---

## 10. Commit Log
commit abcdef123456
Author: Mukti Ali Raja
Date: 2026-01-04


week11-secret-sharing
```

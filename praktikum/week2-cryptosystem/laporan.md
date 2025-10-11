# Laporan Praktikum Kriptografi
Minggu ke-: 2
Topik: Cyptosystem 
Nama: Mukti Ali raja  
NIM: 230202819  
Kelas: 5IKRA  

---

## 1. Tujuan
Memahami konsep dasar sistem kriptografi klasik menggunakan Caesar Cipher.

Mampu mengimplementasikan proses enkripsi dan dekripsi menggunakan bahasa Python.

Mengetahui perbedaan hasil antara teks asli (plaintext) dan teks terenkripsi (ciphertext).
---

## 2. Dasar Teori
Kriptografi adalah ilmu yang mempelajari teknik untuk mengamankan informasi agar tidak mudah dibaca oleh pihak yang tidak berwenang. Salah satu metode klasik yang paling sederhana adalah Caesar Cipher, yaitu metode substitusi huruf di mana setiap huruf digeser sejauh k posisi dalam alfabet.

Misalnya, jika k = 3, maka huruf A → D, B → E, dan seterusnya. Proses mengubah plaintext menjadi ciphertext disebut enkripsi, sedangkan mengubah kembali ciphertext menjadi plaintext disebut dekripsi.

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
# file: praktikum/week2-cryptosystem/src/simple_crypto.py

def encrypt(plaintext, key):
    result = ""
    for char in plaintext:
        if char.isalpha():
            # Geser huruf (A–Z / a–z)
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift + key) % 26 + shift)
        elif char.isdigit():
            # Geser angka (0–9)
            result += chr((ord(char) - 48 + key) % 10 + 48)
        else:
            # Karakter lain (spasi, tanda baca, dll) tidak diubah
            result += char
    return result


def decrypt(ciphertext, key):
    result = ""
    for char in ciphertext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift - key) % 26 + shift)
        elif char.isdigit():
            result += chr((ord(char) - 48 - key) % 10 + 48)
        else:
            result += char
    return result


if __name__ == "__main__":
    message = "230202819 MuktiAliRaja"
    key = 5

    enc = encrypt(message, key)
    dec = decrypt(enc, key)

    print("Plaintext :", message)
    print("Ciphertext:", enc)
    print("Decrypted :", dec)


---

## 6. Hasil dan Pembahasan
Program berhasil melakukan enkripsi pada huruf dan angka.

Huruf digeser 5 posisi dalam alfabet (mod 26).

Angka digeser 5 posisi dalam 0–9 (mod 10).
Proses dekripsi membalikkan hasil enkripsi dengan kunci yang sama, menunjukkan sistem ini termasuk kriptografi simetris.
Tidak ditemukan error selama eksekusi program.

---

## 7. Jawaban Pertanyaan
Pertanyaan 1: Sebutkan komponen utama dalam sebuah kriptosistem.
 Jawaban: Plaintext, Ciphertext, Algoritma Enkripsi/Dekripsi, dan Kunci.

Pertanyaan 2: Apa kelebihan dan kelemahan sistem simetris dibandingkan asimetris?
 Jawaban:

Kelebihan: Proses lebih cepat dan efisien.

Kelemahan: Distribusi kunci rawan bocor karena kunci yang sama digunakan di kedua sisi.

Pertanyaan 3: Mengapa distribusi kunci menjadi masalah utama dalam kriptografi simetris?
Jawaban: Karena kunci harus dikirim ke pihak lain dengan aman. Jika bocor, maka pesan bisa dengan mudah didekripsi oleh pihak ketiga.

## 8. Kesimpulan
Praktikum ini menunjukkan bagaimana proses enkripsi dan dekripsi dilakukan menggunakan metode sederhana (Caesar Cipher yang dimodifikasi). Sistem ini menggunakan satu kunci yang sama, termasuk jenis kriptografi simetris. Hasil uji menunjukkan bahwa program dapat mengenkripsi huruf dan angka dengan benar.

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

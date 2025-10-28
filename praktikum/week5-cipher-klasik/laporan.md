# Laporan Praktikum Kriptografi
Minggu ke-: 5 
Topik: Cipher Klasik (Caesar, Vigenère, Transposisi)  
Nama: Mukti Ali Raja  
NIM: 230202819  
Kelas: 5IKRA  

---

## 1. Tujuan

1. Menerapkan algoritma Caesar Cipher untuk enkripsi dan dekripsi teks.
2. Menerapkan algoritma Vigenère Cipher dengan variasi kunci.
3. Mengimplementasikan algoritma transposisi sederhana.
4. Menjelaskan kelemahan algoritma kriptografi klasik dalam konteks keamanan modern.
---

## 2. Dasar Teori
Cipher klasik merupakan metode kriptografi awal yang digunakan untuk menyembunyikan pesan dengan cara mengganti atau menyusun ulang huruf-huruf dalam teks. Dua kelompok utama cipher klasik adalah substitusi cipher (penggantian huruf) dan transposisi cipher (penyusunan ulang huruf).

Caesar Cipher adalah algoritma substitusi sederhana yang menggeser setiap huruf dalam teks sejauh n posisi pada alfabet. Misalnya, dengan kunci 3, huruf “A” menjadi “D”. Operasi ini menggunakan konsep aritmetika modular (mod 26) untuk membungkus huruf dari Z kembali ke A.

Vigenère Cipher adalah pengembangan dari Caesar Cipher dengan menggunakan kata kunci (key word) sebagai dasar pergeseran huruf yang berbeda-beda. Cipher ini lebih sulit dipecahkan dibanding Caesar karena memiliki variasi kunci yang lebih kompleks.

Transposisi Cipher bekerja dengan cara mengubah urutan huruf pada pesan tanpa mengganti huruf itu sendiri. Contohnya, pesan ditulis dalam baris dengan panjang tertentu lalu dibaca berdasarkan kolom. Meskipun sulit dipecahkan dengan analisis frekuensi, cipher ini tetap lemah terhadap serangan komputasional modern.

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
caesar.py
def caesar_encrypt(plaintext, key):
    result = ""
    for char in plaintext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift + key) % 26 + shift)
        else:
            result += char
    return result

def caesar_decrypt(ciphertext, key):
    return caesar_encrypt(ciphertext, -key)

# Contoh uji
msg = "CLASSIC CIPHER"
key = 3
enc = caesar_encrypt(msg, key)
dec = caesar_decrypt(enc, key)
print("Plaintext :", msg)
print("Ciphertext:", enc)
print("Decrypted :", dec)

🔹 vigenere.py
def vigenere_encrypt(plaintext, key):
    result = []
    key = key.lower()
    key_index = 0
    for char in plaintext:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - 97
            base = 65 if char.isupper() else 97
            result.append(chr((ord(char) - base + shift) % 26 + base))
            key_index += 1
        else:
            result.append(char)
    return "".join(result)

def vigenere_decrypt(ciphertext, key):
    result = []
    key = key.lower()
    key_index = 0
    for char in ciphertext:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - 97
            base = 65 if char.isupper() else 97
            result.append(chr((ord(char) - base - shift) % 26 + base))
            key_index += 1
        else:
            result.append(char)
    return "".join(result)

# Contoh uji
msg = "KRIPTOGRAFI"
key = "KEY"
enc = vigenere_encrypt(msg, key)
dec = vigenere_decrypt(enc, key)
print("Plaintext :", msg)
print("Ciphertext:", enc)
print("Decrypted :", dec)

🔹 transpose.py
def transpose_encrypt(plaintext, key=5):
    ciphertext = [''] * key
    for col in range(key):
        pointer = col
        while pointer < len(plaintext):
            ciphertext[col] += plaintext[pointer]
            pointer += key
    return ''.join(ciphertext)

def transpose_decrypt(ciphertext, key=5):
    num_of_cols = int(len(ciphertext) / key + 0.9999)
    num_of_rows = key
    num_of_shaded_boxes = (num_of_cols * num_of_rows) - len(ciphertext)
    plaintext = [''] * num_of_cols
    col = 0
    row = 0
    for symbol in ciphertext:
        plaintext[col] += symbol
        col += 1
        if (col == num_of_cols) or (col == num_of_cols - 1 and row >= num_of_rows - num_of_shaded_boxes):
            col = 0
            row += 1
    return ''.join(plaintext)

# Contoh uji
msg = "TRANSPOSITIONCIPHER"
enc = transpose_encrypt(msg, key=5)
dec = transpose_decrypt(enc, key=5)
print("Plaintext :", msg)
print("Ciphertext:", enc)
print("Decrypted :", dec)
---

## 6. Hasil dan Pembahasan
<img width="1365" height="720" alt="Screenshot 2025-10-28 230351" src="https://github.com/user-attachments/assets/9e7f8806-8990-4d1b-bc70-05cc94b85570" />
<img width="1363" height="722" alt="Screenshot 2025-10-28 230515" src="https://github.com/user-attachments/assets/bc4aca65-5c1c-4fb4-8a5d-f969a0ba0427" />

<img width="1365" height="511" alt="Screenshot 2025-10-28 230452" src="https://github.com/user-attachments/assets/cabba160-f517-4421-ab99-6fedf2b0ae68" />


---

## 7. Jawaban Pertanyaan
1. Apa kelemahan utama algoritma Caesar Cipher dan Vigenère Cipher?
Caesar Cipher memiliki ruang kunci yang sangat kecil (hanya 25 kemungkinan), sehingga mudah dipecahkan dengan brute-force.
Vigenère Cipher lebih kuat, tetapi tetap rentan terhadap frequency analysis dan Kasiski examination jika kuncinya pendek atau berulang.

2. Mengapa cipher klasik mudah diserang dengan analisis frekuensi?
Karena cipher klasik tidak mengubah frekuensi kemunculan huruf secara signifikan. Pola distribusi huruf dalam bahasa alami tetap bisa dikenali, sehingga analis dapat menebak substitusi yang digunakan.

3. Bandingkan kelebihan dan kelemahan cipher substitusi vs transposisi.
Substitusi Cipher: Mengganti huruf, tetapi mempertahankan urutan. Lebih mudah diimplementasikan, namun pola frekuensi tetap terlihat.
Transposisi Cipher: Menyusun ulang urutan huruf tanpa mengganti karakter. Lebih sulit dipecahkan dengan analisis frekuensi, tetapi masih bisa direkonstruksi dengan serangan posisi karakter.
---

## 8. Kesimpulan
Praktikum ini memperkenalkan prinsip dasar kriptografi klasik melalui implementasi Caesar, Vigenère, dan Transposisi Cipher.
Dari hasil uji, seluruh algoritma berhasil melakukan enkripsi dan dekripsi dengan benar. Namun, cipher klasik terbukti tidak aman untuk komunikasi modern karena mudah diserang dengan teknik analisis frekuensi dan brute-force.
---

## 9. Daftar Pustaka
Stallings, W. (2017). Cryptography and Network Security: Principles and Practice. Pearson.
Katz, J., & Lindell, Y. (2014). Introduction to Modern Cryptography. CRC Press.
Singh, S. (1999). The Code Book: The Science of Secrecy from Ancient Egypt to Quantum Cryptography.

---

## 10. Commit Log
commit 9b23afc
Author: Mukti Ali Raja <muktialir2207@gmail.com>
Date:   2025-10-28

    week5-cipher-klasik: implementasi Caesar, Vigenere, dan Transposisi Cipher serta laporan
```

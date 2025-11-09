# Laporan Praktikum Kriptografi
Minggu ke-: 6
Topik: Cipher Modern (AES, RSA, DES) 

Nama: Mukti Ali Raja 
NIM: 230202819  
Kelas: 5IKRA 

---

## 1. Tujuan
1. Mengimplementasikan algoritma DES untuk blok data sederhana (opsional).
2. Menerapkan algoritma AES dengan panjang kunci 128 bit untuk proses enkripsi dan dekripsi data.
3. Menjelaskan proses pembangkitan kunci publik dan privat pada algoritma RSA serta mengimplementasikannya menggunakan Python.

---

## 2. Dasar Teori
Kriptografi modern berfokus pada metode penyandian data menggunakan algoritma matematis yang kuat untuk menjamin kerahasiaan dan integritas informasi. Dua kategori utama dalam kriptografi adalah cipher simetris (seperti DES dan AES) dan cipher asimetris (seperti RSA).

DES (Data Encryption Standard) merupakan algoritma simetris berbasis blok 64 bit dengan panjang kunci 56 bit efektif. Meskipun menjadi standar pada masa awal, DES kini dianggap tidak aman karena ukuran kuncinya terlalu pendek untuk melawan serangan brute-force modern.

AES (Advanced Encryption Standard) menggantikan DES dengan ukuran blok 128 bit dan panjang kunci 128, 192, atau 256 bit. AES menggunakan substitusi, permutasi, dan transformasi matematis untuk menghasilkan cipher yang sangat kuat dan efisien.

RSA (Rivest–Shamir–Adleman) adalah algoritma asimetris yang menggunakan pasangan kunci publik dan privat yang berbeda. Keamanannya didasarkan pada kesulitan faktorisasi bilangan besar. RSA sering digunakan untuk enkripsi kunci sesi dan tanda tangan digital.

---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )

---

## 4. Langkah Percobaan
Membuat folder praktikum/week6-cipher-modern/ dengan struktur sesuai panduan.
Membuat file berikut di dalam folder src/:

aes.py → implementasi AES-128
rsa.py → implementasi RSA
des.py → simulasi DES (opsional)

Menyalin kode dari modul praktikum dan menjalankan program dengan perintah:

python aes.py
python rsa.py
python des.py


Menyimpan hasil eksekusi (screenshot terminal) ke folder screenshots/.
Menyusun laporan laporan.md berisi teori, hasil, dan jawaban pertanyaan diskusi.
Melakukan commit dengan pesan:

week6-cipher-modern

---

## 5. Source Code
Source Code
🔹 AES (aes.py)
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes

key = get_random_bytes(16)  # 128-bit key
cipher = AES.new(key, AES.MODE_EAX)

plaintext = b"Modern Cipher AES Example"
ciphertext, tag = cipher.encrypt_and_digest(plaintext)

print("Ciphertext:", ciphertext)

# Dekripsi
cipher_dec = AES.new(key, AES.MODE_EAX, nonce=cipher.nonce)
decrypted = cipher_dec.decrypt(ciphertext)
print("Decrypted:", decrypted.decode())

🔹 RSA (rsa.py)
from Crypto.PublicKey import RSA
from Crypto.Cipher import PKCS1_OAEP

# Generate key pair
key = RSA.generate(2048)
private_key = key
public_key = key.publickey()

# Enkripsi
cipher_rsa = PKCS1_OAEP.new(public_key)
plaintext = b"RSA Example"
ciphertext = cipher_rsa.encrypt(plaintext)
print("Ciphertext:", ciphertext)

# Dekripsi
decipher_rsa = PKCS1_OAEP.new(private_key)
decrypted = decipher_rsa.decrypt(ciphertext)
print("Decrypted:", decrypted.decode())

🔹 DES (des.py) (opsional)
from Crypto.Cipher import DES
from Crypto.Random import get_random_bytes

key = get_random_bytes(8)  # 64-bit key
cipher = DES.new(key, DES.MODE_ECB)

plaintext = b"ABCDEFGH"
ciphertext = cipher.encrypt(plaintext)
print("Ciphertext:", ciphertext)

decipher = DES.new(key, DES.MODE_ECB)
decrypted = decipher.decrypt(ciphertext)
print("Decrypted:", decrypted)

---

## 6. Hasil dan Pembahasan
Hasil eksekusi menunjukkan bahwa proses enkripsi dan dekripsi berhasil dilakukan untuk ketiga algoritma.
Data yang terenkripsi berubah menjadi bentuk biner tidak terbaca, dan setelah didekripsi menghasilkan kembali plaintext asli.
    <img width="1028" height="697" alt="Screenshot 2025-11-09 211401" src="https://github.com/user-attachments/assets/32dd14fc-4e74-4926-a422-0fd39b1a812d" />
<img width="1022" height="713" alt="Screenshot 2025-11-09 211459" src="https://github.com/user-attachments/assets/478f6693-f09b-468e-a08d-d5537b29cc68" />
<img width="1025" height="722" alt="Screenshot 2025-11-09 211445" src="https://github.com/user-attachments/assets/91937ca2-2609-443c-94a2-05af2ec580ea" />



---

## 7. Jawaban Pertanyaan
1. Apa perbedaan mendasar antara DES, AES, dan RSA dalam hal kunci dan keamanan?
DES dan AES merupakan algoritma simetris, menggunakan satu kunci yang sama untuk enkripsi dan dekripsi.
RSA merupakan algoritma asimetris, menggunakan dua kunci berbeda (publik dan privat).
Dari segi keamanan, AES jauh lebih kuat dibanding DES, dan RSA digunakan untuk keamanan tingkat tinggi seperti autentikasi dan pertukaran kunci.

2. Mengapa AES lebih banyak digunakan dibanding DES di era modern?
AES memiliki ukuran kunci lebih panjang (128/192/256 bit) sehingga lebih tahan terhadap serangan brute-force.
AES juga lebih efisien dan cepat di perangkat keras maupun lunak modern.

3. Mengapa RSA dikategorikan sebagai algoritma asimetris, dan bagaimana proses pembangkitan kuncinya?
RSA disebut asimetris karena menggunakan dua kunci berbeda: public key untuk enkripsi dan private key untuk dekripsi.
Proses pembangkitan kuncinya melibatkan:
1. Pemilihan dua bilangan prima besar p dan 𝑞.
2. Menghitung 𝑛=𝑝×𝑞 dan 𝜙(𝑛)=(𝑝−1)(𝑞−1)
3. Memilih eksponen publik e yang relatif prima terhadap 𝜙(𝑛).
4.Menghitung kunci privat d sebagai invers dari e terhadap 𝜙(𝑛).
---

## 8. Kesimpulan
Melalui praktikum ini, mahasiswa memahami perbedaan antara algoritma simetris dan asimetris.
Implementasi AES dan RSA berhasil dilakukan menggunakan library PyCryptodome.
AES terbukti efisien untuk data umum, sedangkan RSA lebih cocok untuk keamanan komunikasi dan distribusi kunci.

---

## 9. Daftar Pustaka
Stallings, W. (2017). Cryptography and Network Security: Principles and Practice. Pearson.
Katz, J., & Lindell, Y. (2015). Introduction to Modern Cryptography. CRC Press.
PyCryptodome Documentation: https://pycryptodome.readthedocs.io/
---

## 10. Commit Log
commit abc12345
Author: Mukti Ali Raja <muktialir2207@gmail.com>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```

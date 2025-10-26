# Laporan Praktikum Kriptografi
Minggu ke-: X  
Topik: Analisis Entropi, Unicity Distance, dan Brute Force Attack
Nama: Mukti Ali Raja  
NIM: 230202819
Kelas: 5IKRA  

---

## 1. Tujuan
Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:
1. Menyelesaikan perhitungan sederhana terkait entropi kunci.
2. Menggunakan teorema Euler pada contoh perhitungan modular & invers.
3. Menghitung unicity distance untuk ciphertext tertentu.
4. Menganalisis kekuatan kunci berdasarkan entropi dan unicity distance.
5. Mengevaluasi potensi serangan brute force pada kriptosistem sederhana.

---

## 2. Dasar Teori
Entropi dalam konteks kriptografi menggambarkan tingkat ketidakpastian atau jumlah informasi yang dimiliki oleh sebuah kunci. Semakin besar ukuran ruang kunci, semakin tinggi entropinya, yang berarti semakin sulit bagi penyerang untuk menebak kunci dengan benar. Entropi kunci dihitung menggunakan rumus 𝐻(𝐾)=log2∣𝐾∣di mana ∣𝐾∣ adalah jumlah total kemungkinan kunci.

Unicity distance merupakan ukuran yang menunjukkan seberapa banyak ciphertext yang dibutuhkan agar hanya terdapat satu kemungkinan plaintext yang benar. Nilai ini bergantung pada entropi kunci, redundansi bahasa, dan ukuran alfabet. Jika unicity distance rendah, maka cipher dapat dipecahkan dengan sedikit data.

Brute force attack adalah metode serangan dengan mencoba seluruh kemungkinan kunci hingga ditemukan hasil dekripsi yang benar. Walaupun sederhana, metode ini menjadi ancaman nyata apabila ukuran ruang kunci kecil atau perangkat komputasi sangat cepat. Namun, untuk algoritma modern seperti AES-128, waktu yang dibutuhkan sangat besar hingga tidak praktis dilakukan.

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
import math

# Fungsi menghitung entropi ruang kunci
def entropy(keyspace_size):
    return math.log2(keyspace_size)

# Fungsi menghitung Unicity Distance
def unicity_distance(HK, R=0.75, A=26):
    return HK / (R * math.log2(A))

# Fungsi menghitung estimasi waktu brute force (dalam hari)
def brute_force_time(keyspace_size, attempts_per_second=1e6):
    seconds = keyspace_size / attempts_per_second
    days = seconds / (3600 * 24)
    return days

# --- Eksekusi Program ---
print("=== PERHITUNGAN ENTROPI DAN UNICITY DISTANCE ===")
HK_caesar = entropy(26)
print(f"Entropy ruang kunci Caesar Cipher (26) = {HK_caesar:.4f} bit")

HK_AES = entropy(2**128)
print(f"Entropy ruang kunci AES-128 = {HK_AES:.4f} bit")

print("\n=== PERHITUNGAN UNICITY DISTANCE ===")
UD_caesar = unicity_distance(HK_caesar)
print(f"Unicity Distance Caesar Cipher = {UD_caesar:.4f}")

UD_AES = unicity_distance(HK_AES)
print(f"Unicity Distance AES-128 = {UD_AES:.4e}")

print("\n=== ESTIMASI WAKTU BRUTE FORCE ===")
BF_caesar = brute_force_time(26)
print(f"Waktu brute force Caesar Cipher (26 kunci) = {BF_caesar:.8f} hari")

BF_AES = brute_force_time(2**128)
print(f"Waktu brute force AES-128 = {BF_AES:.2e} hari")


---

## 6. Hasil dan Pembahasan
<img width="1364" height="730" alt="image" src="https://github.com/user-attachments/assets/81c4e3f6-8b97-471d-871e-c13b5aedc708" />
  
Hasil eksekusi program:

Ringkasan hasil perhitungan:

Cipher	Ukuran Kunci	Entropi (bit)	Unicity Distance	Estimasi Brute Force (hari)
Caesar Cipher	26	4.70	0.40	0.00000030
AES-128	2¹²⁸	128.00	10.8×10²⁵	~8.4×10³⁰

Pembahasan:

Entropi untuk Caesar Cipher sangat kecil (hanya sekitar 4,7 bit), menandakan ruang kunci sempit dan mudah ditebak.

Sebaliknya, AES-128 memiliki entropi sebesar 128 bit, yang sangat tinggi, membuat brute force menjadi tidak realistis.

Unicity distance Caesar Cipher kecil, artinya cipher ini dapat dipecahkan hanya dengan sedikit ciphertext.

Estimasi waktu brute force untuk AES-128 sangat besar (jutaan tahun bahkan dengan superkomputer), menunjukkan keamanannya terhadap serangan brute force.
Hasil eksekusi program Caesar Cipher:

![Hasil Eksekusi](screenshots/output.png)
![Hasil Input](screenshots/input.png)
![Hasil Output](screenshots/output.png)
)

---

## 7. Jawaban Pertanyaan
1. Apa arti dari nilai entropy dalam konteks kekuatan kunci?
Nilai entropi menggambarkan tingkat ketidakpastian dalam pemilihan kunci. Semakin tinggi entropi, semakin sulit bagi penyerang untuk menebak kunci yang benar, sehingga sistem menjadi lebih aman.

2. Mengapa unicity distance penting dalam menentukan keamanan suatu cipher?
Unicity distance menentukan jumlah ciphertext minimum yang dibutuhkan untuk menghilangkan ambiguitas dalam dekripsi. Cipher dengan nilai unicity distance rendah mudah dipecahkan karena informasi plaintext dapat disimpulkan dengan sedikit ciphertext.

3. Mengapa brute force masih menjadi ancaman meskipun algoritma sudah kuat?
Brute force tetap menjadi ancaman karena tidak bergantung pada kelemahan algoritma. Jika implementasi tidak aman atau kunci dipilih terlalu lemah, serangan brute force bisa berhasil dalam waktu singkat.
---

## 8. Kesimpulan
Dari hasil percobaan, dapat disimpulkan bahwa semakin besar ukuran ruang kunci, semakin tinggi entropi dan unicity distance-nya, sehingga semakin aman terhadap serangan brute force. Caesar Cipher memiliki keamanan sangat rendah, sedangkan AES-128 memiliki keamanan sangat tinggi karena ruang kuncinya yang sangat besar.
---

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

## 10. Commit Log
commit a1b2c3d4
Author: Mukti Ali Raja <[muktialir2207@gmail.com]>
Date:   2025-10-26

    week4-entropy-unicity: implementasi perhitungan entropi, unicity distance, dan brute force attack

```

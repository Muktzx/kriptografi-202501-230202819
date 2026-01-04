# Laporan Praktikum Kriptografi
Minggu ke-: 13
Topik: TinyChain – Proof of Work (PoW)  
Nama: Mukti Ali Raja
NIM: 230202819 
Kelas: 5IKRA 

---

## 1. Tujuan
Tujuan dari praktikum ini adalah untuk memahami peran fungsi hash dalam blockchain, melakukan simulasi sederhana mekanisme Proof of Work (PoW), serta menganalisis aspek keamanan cryptocurrency yang berbasis kriptografi.

---

## 2. Dasar Teori
Blockchain merupakan struktur data terdistribusi yang terdiri dari rangkaian blok yang saling terhubung menggunakan fungsi hash. Setiap blok menyimpan data transaksi, timestamp, hash dari blok sebelumnya, dan hash blok itu sendiri. Fungsi hash kriptografis seperti SHA-256 digunakan untuk menjamin integritas data karena bersifat satu arah dan sensitif terhadap perubahan input.

Proof of Work (PoW) adalah mekanisme konsensus yang digunakan untuk memvalidasi penambahan blok baru ke dalam blockchain. Dalam PoW, penambang (miner) harus menemukan nilai nonce yang menghasilkan hash dengan pola tertentu (misalnya diawali sejumlah nol). Proses ini membutuhkan usaha komputasi yang besar sehingga menyulitkan pemalsuan data.

Keamanan blockchain bergantung pada kombinasi hash function dan PoW. Perubahan data pada satu blok akan mengubah hash dan menyebabkan ketidaksesuaian pada blok-blok berikutnya. Dengan demikian, blockchain menjadi tahan terhadap manipulasi data dan serangan seperti double spending.

---

## 3. Alat dan Bahan
Python 3.11

Visual Studio Code

Git dan akun GitHub

Library bawaan Python: hashlib, time

---

## 4. Langkah Percobaan
Membuat struktur folder praktikum/week13-tinychain/.

Membuat file tinychain.py di folder src/.

Mengimplementasikan class Block yang berisi data blok dan fungsi hash.

Mengimplementasikan class Blockchain untuk mengelola rantai blok.

Menjalankan proses mining menggunakan mekanisme Proof of Work.

Mengamati waktu dan hasil hash dari proses mining.

Mengambil screenshot hasil mining blok.

Menyusun laporan praktikum dan melakukan commit ke GitHub.

---

## 5. Source Code
# ============================================
# TinyChain - Simple Blockchain with Proof of Work
# Praktikum Kriptografi Week 13
# ============================================

import hashlib
import time


class Block:
    def __init__(self, index, previous_hash, data, timestamp=None):
        self.index = index
        self.timestamp = timestamp or time.time()
        self.data = data
        self.previous_hash = previous_hash
        self.nonce = 0
        self.hash = self.calculate_hash()

    def calculate_hash(self):
        """
        Menghitung hash SHA-256 dari isi blok
        """
        value = (
            str(self.index)
            + str(self.timestamp)
            + str(self.data)
            + str(self.previous_hash)
            + str(self.nonce)
        )
        return hashlib.sha256(value.encode()).hexdigest()

    def mine_block(self, difficulty):
        """
        Proses Proof of Work:
        mencari nonce hingga hash diawali dengan sejumlah nol
        """
        target = "0" * difficulty
        start_time = time.time()

        while self.hash[:difficulty] != target:
            self.nonce += 1
            self.hash = self.calculate_hash()

        end_time = time.time()
        print(f"Block mined!")
        print(f"Hash      : {self.hash}")
        print(f"Nonce     : {self.nonce}")
        print(f"Waktu     : {end_time - start_time:.4f} detik\n")


class Blockchain:
    def __init__(self, difficulty=4):
        self.chain = [self.create_genesis_block()]
        self.difficulty = difficulty

    def create_genesis_block(self):
        """
        Membuat blok pertama (Genesis Block)
        """
        return Block(0, "0", "Genesis Block")

    def get_latest_block(self):
        return self.chain[-1]

    def add_block(self, new_block):
        """
        Menambahkan blok baru ke blockchain
        """
        new_block.previous_hash = self.get_latest_block().hash
        new_block.mine_block(self.difficulty)
        self.chain.append(new_block)

    def is_chain_valid(self):
        """
        Mengecek validitas blockchain
        """
        for i in range(1, len(self.chain)):
            current = self.chain[i]
            previous = self.chain[i - 1]

            if current.hash != current.calculate_hash():
                return False

            if current.previous_hash != previous.hash:
                return False

        return True

    def print_chain(self):
        """
        Menampilkan seluruh isi blockchain
        """
        print("=== BLOCKCHAIN ===")
        for block in self.chain:
            print(f"Index        : {block.index}")
            print(f"Timestamp    : {block.timestamp}")
            print(f"Data         : {block.data}")
            print(f"PreviousHash : {block.previous_hash}")
            print(f"Hash         : {block.hash}")
            print(f"Nonce        : {block.nonce}")
            print("-" * 40)


# =======================
# MAIN PROGRAM
# =======================
if __name__ == "__main__":
    print("=== TinyChain - Proof of Work ===\n")

    # Membuat blockchain dengan difficulty 4
    my_chain = Blockchain(difficulty=4)

    print("Mining block 1...")
    my_chain.add_block(Block(1, "", "Transaksi A → B : 10 Coin"))

    print("Mining block 2...")
    my_chain.add_block(Block(2, "", "Transaksi B → C : 5 Coin"))

    print("Mining block 3...")
    my_chain.add_block(Block(3, "", "Transaksi C → D : 2 Coin"))

    # Menampilkan blockchain
    my_chain.print_chain()

    # Validasi blockchain
    print("\nBlockchain valid?", my_chain.is_chain_valid())


---

## 6. Hasil dan Pembahasan
Hasil percobaan menunjukkan bahwa proses mining membutuhkan waktu yang bergantung pada tingkat difficulty. Setiap blok berhasil ditambang setelah ditemukan nilai nonce yang menghasilkan hash sesuai dengan syarat PoW.

Hasil ini sesuai dengan teori Proof of Work, di mana peningkatan difficulty akan meningkatkan keamanan blockchain namun juga meningkatkan waktu dan konsumsi komputasi. Blockchain menjadi sulit dimanipulasi karena perubahan satu blok memerlukan mining ulang seluruh blok setelahnya

<img width="1319" height="936" alt="image" src="https://github.com/user-attachments/assets/6458bde3-1d6c-4da7-9f66-29a84a38b12a" />

---

## 7. Jawaban Pertanyaan
Pertanyaan 1: Mengapa fungsi hash sangat penting dalam blockchain?

Jawaban: Fungsi hash menjamin integritas data dan menghubungkan antar blok. Perubahan kecil pada data akan menghasilkan hash yang berbeda sehingga manipulasi dapat terdeteksi.

Pertanyaan 2: Bagaimana Proof of Work mencegah double spending?

Jawaban: Proof of Work membuat penambahan dan perubahan blok membutuhkan usaha komputasi besar, sehingga mencegah penyerang dengan mudah memalsukan transaksi atau menggandakan pengeluaran.

Pertanyaan 3: Apa kelemahan Proof of Work dalam hal efisiensi energi?

Jawaban: Proof of Work membutuhkan daya komputasi tinggi yang berdampak pada konsumsi energi besar dan kurang ramah lingkungan.
---

## 8. Kesimpulan
TinyChain dengan Proof of Work menunjukkan bagaimana blockchain menjaga keamanan data menggunakan hash function dan mekanisme konsensus. Meskipun aman, Proof of Work memiliki kelemahan dari sisi efisiensi energi sehingga perlu dipertimbangkan alternatif lain.
---

## 9. Daftar Pustaka
Stallings, W. (2017). Cryptography and Network Security. Pearson.

Stinson, D. R. (2019). Cryptography: Theory and Practice. CRC Press.
---

## 10. Commit Log
commit abcdef123456
Author: Mukti Ali Raja <muktialir2207@gmail.com>
Date: 2026-01-04


week13-tinychain
```

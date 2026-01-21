Minggu ke-: 15
Topik: tinycoin-erc20 Nama: Mukti ALi Raja 
NIM: 230202819 
Kelas: 5IKRA

1. Tujuan
Mengembangkan proyek sederhana berbasis algoritma kriptografi. Mendokumentasikan proses implementasi proyek ke dalam repository Git. Menyusun laporan teknis hasil proyek akhir.

2. Dasar Teori
(Ringkas teori relevan (cukup 2–3 paragraf).
Contoh: definisi cipher klasik, konsep modular aritmetika, dll. )

3. Alat dan Bahan
(- Python 3.x

Visual Studio Code / editor lain
Git dan akun GitHub
Library tambahan (misalnya pycryptodome, jika diperlukan) )
4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.
Contoh format:

Membuat file caesar_cipher.py di folder praktikum/week2-cryptosystem/src/.
Menyalin kode program dari panduan praktikum.
Menjalankan program dengan perintah python caesar_cipher.py.)
5. Source Code
// SPDX-License-Identifier: MIT pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract TinyCoin is ERC20 { constructor(uint256 initialSupply) ERC20("TinyCoin", "TNC") { _mint(msg.sender, initialSupply); } }

6. Hasil dan Pembahasan
Hasil Eksekusi Hasil Input Hasil Output )

7. Jawaban Pertanyaan
(Jawab pertanyaan diskusi yang diberikan pada modul.

Pertanyaan 1: …
Pertanyaan 2: …
)
8. Kesimpulan
Implementasi TinyCoin ERC20 berhasil dilakukan dengan baik. Smart contract dapat dideploy, diuji, dan berfungsi sesuai standar ERC20. Dokumentasi dan bukti pengujian telah dilampirkan secara lengkap.

10. Commit Log
Author: Nurita ahadhini ahadininurita31@gmail.com Date: 2025-09-20

week15-tinycoin-erc20

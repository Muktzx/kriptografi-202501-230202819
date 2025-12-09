# Laporan Praktikum Kriptografi
Minggu ke-: 10
Topik: Public Key Infrastructure (PKI) & Certificate Authority (CA)  
Nama: Mukti Ali Raja  
NIM: 230202819 
Kelas: 5IKRA  

---

## 1. Tujuan
Mahasiswa mampu membuat sertifikat digital sederhana menggunakan Python/OpenSSL.
Mahasiswa memahami peran Certificate Authority (CA) dalam sistem Public Key Infrastructure.
Mahasiswa dapat mengevaluasi bagaimana PKI bekerja dalam komunikasi aman seperti HTTPS/TLS.

---

## 2. Dasar Teori
Public Key Infrastructure (PKI) adalah sistem yang mengelola pembuatan, penyimpanan, distribusi, dan pencabutan sertifikat digital untuk memastikan komunikasi aman. PKI menggunakan pasangan public key dan private key, serta sertifikat digital yang dikeluarkan oleh lembaga tepercaya bernama Certificate Authority (CA). Sertifikat digital berfungsi untuk memverifikasi identitas pemilik kunci publik.

Certificate Authority (CA) adalah pihak yang dipercaya untuk menandatangani sertifikat digital. Browser dan sistem operasi menyimpan daftar CA tepercaya (trusted root CA), sehingga dapat memverifikasi apakah suatu situs atau entitas benar-benar valid. Dalam komunikasi HTTPS/TLS, sertifikat digunakan untuk memastikan keaslian server dan mencegah serangan seperti man-in-the-middle (MITM).

Self-signed certificate adalah sertifikat yang ditandatangani sendiri oleh pembuatnya. Sertifikat ini valid untuk pengujian atau lingkungan lokal, tetapi tidak dapat dipakai di sistem produksi karena tidak berasal dari CA tepercaya.
---

## 3. Alat dan Bahan
Python 3.11 atau lebih baru
Visual Studio Code / editor lain
Git & GitHub
Library Python:
cryptography
pyopenssl (opsional)

---

## 4. Langkah Percobaan
Membuat folder praktikum/week10-pki/ sesuai struktur yang diminta.
Membuat file src/pki_cert.py.
Menyalin kode program pembuatan sertifikat digital dari modul praktikum.
Menjalankan program dengan perintah:

python src/pki_cert.py
          
Mengecek file cert.pem yang dihasilkan.
Menyimpan screenshot hasil ke folder screenshots/.
Menjawab pertanyaan diskusi PKI & CA pada laporan.
---

## 5. Source Code
from cryptography import x509
from cryptography.x509.oid import NameOID
from cryptography.hazmat.primitives import hashes, serialization
from cryptography.hazmat.primitives.asymmetric import rsa
from datetime import datetime, timedelta, UTC

# Generate key pair
key = rsa.generate_private_key(public_exponent=65537, key_size=2048)

# Buat subject & issuer (self-signed certificate)
subject = issuer = x509.Name([
    x509.NameAttribute(NameOID.COUNTRY_NAME, u"ID"),
    x509.NameAttribute(NameOID.ORGANIZATION_NAME, u"UPB Kriptografi"),
    x509.NameAttribute(NameOID.COMMON_NAME, u"example.com"),
])

# Waktu validasi dengan timezone-aware UTC
valid_from = datetime.now(UTC)
valid_until = valid_from + timedelta(days=365)

# Buat sertifikat
cert = (
    x509.CertificateBuilder()
    .subject_name(subject)
    .issuer_name(issuer)
    .public_key(key.public_key())
    .serial_number(x509.random_serial_number())
    .not_valid_before(valid_from)
    .not_valid_after(valid_until)
    .sign(key, hashes.SHA256())
)

# Simpan sertifikat
with open("cert.pem", "wb") as f:
    f.write(cert.public_bytes(serialization.Encoding.PEM))

print("Sertifikat digital berhasil dibuat: cert.pem")


---

## 6. Hasil dan Pembahasan
<img width="1900" height="1044" alt="image" src="https://github.com/user-attachments/assets/95c90997-71cc-438d-a416-b43a36f3ae48" />

---

## 7. Jawaban Pertanyaan
1. Apa fungsi utama Certificate Authority (CA)?

CA berfungsi untuk memverifikasi identitas pemilik sertifikat dan menandatangani sertifikat digital sehingga dianggap tepercaya oleh browser atau sistem. CA adalah pusat kepercayaan dalam PKI.

2. Mengapa self-signed certificate tidak cukup untuk sistem produksi?

Karena tidak ditandatangani oleh CA tepercaya. Browser akan memberikan peringatan “Untrusted Certificate”, sehingga tidak aman untuk transaksi atau komunikasi sensitif.

3. Bagaimana PKI mencegah serangan MITM dalam komunikasi TLS/HTTPS?

PKI memastikan bahwa kunci publik server benar-benar milik server yang sah melalui sertifikat yang diverifikasi CA. Penyerang tidak dapat memalsukan kunci publik atau menyisipkan dirinya di tengah komunikasi tanpa terdeteksi.
---

## 8. Kesimpulan
Pada praktikum ini, mahasiswa berhasil membuat sertifikat digital sederhana menggunakan Python. Melalui percobaan ini, dapat dipahami fungsi CA dalam memberikan kepercayaan dan bagaimana PKI mendukung komunikasi aman seperti HTTPS. PKI terbukti penting untuk memastikan integritas, otentikasi, dan kerahasiaan data.

---

## 9. Daftar Pustaka
Stallings, W. Cryptography and Network Security, 7th Edition, 2017.
Documentation: Python cryptography library.
Materials from modul praktikum PKI & CA.
---

## 10. Commit Log
commit abc12345
Author: Mukti Ali Raja <muktialir2207@gmail.com>
Date:   2025-xx-xx

    week10-pki: implementasi pembuatan sertifikat digital & laporan

```

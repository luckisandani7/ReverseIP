# 🔥 MASS REVERSE IP TOOL

**MASS REVERSE IP TOOL** adalah Bash script sederhana untuk melakukan **reverse IP lookup secara massal** berdasarkan daftar IP dari file `.txt`.

Tool ini membaca IP satu per satu, mengirim request ke API reverse-IP, kemudian menyimpan domain yang ditemukan ke file output.

> **Version:** `V1.0`
> **Author:** `Lkey7`
> **Platform:** Linux / Termux / Android

---

## ⚡ Features

* 🔍 Reverse IP lookup secara massal
* 📂 Input IP menggunakan file `.txt`
* 💾 Hasil otomatis disimpan ke file output
* 📊 Menampilkan jumlah domain yang ditemukan pada setiap IP
* 🧹 Mengabaikan baris kosong
* 🧹 Otomatis membersihkan `\r` pada file
* 🐍 Menggunakan Python untuk parsing response JSON
* 🚀 Menggunakan `curl` untuk HTTP request
* 📱 Support **Termux Android**

---

## 📋 Requirements

Pastikan beberapa package berikut sudah tersedia.

### Linux / Debian / Ubuntu

```bash
sudo apt update
sudo apt install curl python3
```

### Termux

```bash
pkg update
pkg install curl python
```

Cek instalasi:

```bash
curl --version
python3 --version
```

Pada beberapa versi Termux, command Python dapat berupa:

```bash
python
```

Jika script menggunakan `python3`, pastikan command tersebut tersedia.

---

## 📥 Installation

Clone repository:

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
cd REPOSITORY
```

Atau jika file script sudah tersedia:

```bash
chmod +x reverseip.sh
```

Kemudian jalankan:

```bash
./reverseip.sh
```

---

## 🚀 Usage

Jalankan script:

```bash
bash reverseip.sh
```

Script akan menampilkan menu input seperti:

```text
[?] Input IP List File:
```

Masukkan file yang berisi daftar IP.

Contoh:

```text
ips.txt
```

Kemudian script akan meminta nama file output:

```text
[?] Save to:
```

Contoh:

```text
result.txt
```

---

## 📄 Input Format

File input harus berupa daftar IP, satu IP per baris.

Contoh `ips.txt`:

```text
8.8.8.8
1.1.1.1
142.250.72.14
104.16.132.229
```

Baris kosong akan otomatis dilewati.

---

## 📤 Output

Hasil reverse IP akan disimpan ke file yang ditentukan.

Contoh:

```text
result.txt
```

Isi file dapat berupa:

```text
example.com
www.example.com
mail.example.com
another-domain.com
```

Terminal juga menampilkan jumlah domain yang ditemukan:

```text
[+] 8.8.8.8 <= 12 domain
[+] 1.1.1.1 <= 4 domain
[-] 142.250.72.14 <= 0 domain

[+] Done! >> result.txt
```

---

## ⚙️ How It Works

Alur kerja tool:

```text
        ┌──────────────┐
        │  IP List     │
        │    .txt      │
        └──────┬───────┘
               │
               ▼
        ┌──────────────┐
        │ Read IP      │
        │ One by One   │
        └──────┬───────┘
               │
               ▼
        ┌──────────────┐
        │ Reverse IP   │
        │ API Request  │
        └──────┬───────┘
               │
               ▼
        ┌──────────────┐
        │ Parse JSON   │
        │   Python     │
        └──────┬───────┘
               │
               ▼
        ┌──────────────┐
        │ Extract      │
        │ Domains      │
        └──────┬───────┘
               │
               ▼
        ┌──────────────┐
        │ Save Result  │
        │  output.txt  │
        └──────────────┘
```

Secara sederhana:

1. Membaca file IP.
2. Mengambil satu IP.
3. Mengirim request ke API reverse-IP.
4. Menerima response JSON.
5. Mengambil data `result`.
6. Memisahkan domain yang ditemukan.
7. Menyimpan domain ke file output.
8. Melanjutkan ke IP berikutnya.

---

## 🔌 API

Script menggunakan endpoint API yang disimpan dalam bentuk **Base64 encoded string**.

Bagian:

```bash
e_api="..."
api_base=$(echo "$e_api" | base64 -d)
```

digunakan untuk melakukan decoding endpoint sebelum digunakan oleh `curl`.

Request dilakukan menggunakan:

```bash
curl -s -H "Accept: application/json" "${api_base}${target}"
```

> **Note:** API merupakan dependency eksternal. Jika endpoint berubah, tidak tersedia, atau memiliki rate limit, tool dapat gagal mendapatkan hasil.

---

## 🐍 JSON Parsing

Response dari API diproses menggunakan Python.

Script mencari property:

```json
{
    "result": []
}
```

Jika `result` berupa array:

```json
{
    "result": [
        "example.com",
        "example.net"
    ]
}
```

domain akan diproses satu per satu.

Script juga menangani `result` dalam bentuk string multi-line.

---

## ⚠️ Limitations

Tool ini memiliki beberapa keterbatasan:

* Kecepatan bergantung pada response API.
* Proses dilakukan secara sequential.
* API dapat memiliki rate limit.
* Tidak semua IP memiliki hasil reverse lookup.
* Hasil bergantung pada database/API yang digunakan.
* Koneksi internet diperlukan.
* Response API yang tidak valid akan dilewati.

---

## 🛡️ Responsible Use

Gunakan tool ini hanya pada:

* IP yang Anda miliki.
* Infrastruktur yang Anda kelola.
* Sistem yang memberikan izin kepada Anda untuk melakukan reconnaissance.
* Aktivitas security research yang sah dan sesuai aturan program.

Jangan gunakan tool untuk melakukan scanning atau reconnaissance terhadap infrastruktur pihak lain tanpa izin.

---

## 📁 Example Project Structure

```text
.
├── reverseip.sh
├── ips.txt
├── result.txt
└── README.md
```

---

## 💡 Example

Buat file IP:

```bash
nano ips.txt
```

Masukkan:

```text
8.8.8.8
1.1.1.1
```

Kemudian jalankan:

```bash
chmod +x reverseip.sh
./reverseip.sh
```

Input:

```text
[?] Input IP List File: ips.txt
[?] Save to: result.txt
```

Setelah selesai:

```text
[+] Done! >> result.txt
```

---

## 👤 Author

**Lkey7**

Made for learning, automation, and authorized security research.

---

## ⭐ Support

Jika project ini bermanfaat, jangan lupa ⭐ repository ini dan share ke teman yang juga tertarik dengan:

* Bash scripting
* Linux
* Termux
* Cybersecurity
* Reconnaissance
* Automation

---

### 📜 License

Gunakan dan modifikasi script ini sesuai kebutuhan Anda.

**For educational and authorized security research purposes only.**

# AuraLink---Crowd-Sourced-Network-for-FMO-Find-My-Object-

Daftar detail sistem **Crowd-Sourced (OpenHaystack/Find My)** yang telah kita diskusikan untuk proyek pelacak hewan/barang Anda. Sistem ini sangat efektif karena bersifat global, tanpa biaya bulanan (gratis), dan hemat energi.

### 1. Komponen Utama (Hardware)

| Bagian | Komponen Rekomendasi | Fungsi |
| :--- | :--- | :--- |
| **Otak & Radio** | ESP32-C3 atau nRF52832 | Memancarkan sinyal Bluetooth "palsu" yang menyamar sebagai AirTag. |
| **Lokasi** | GPS NEO-6M atau ATGM336H | Menangkap koordinat dari satelit GPS (Wajib jika ingin akurasi tinggi). |
| **Daya** | Baterai Li-Po 3.7V (300mAh - 500mAh) | Sumber energi alat agar bisa bertahan beberapa hari hingga minggu. |
| **Regulator** | TP4056 | Modul untuk mengisi ulang baterai (charging). |

### 2. Arsitektur Jaringan (Cara Kerja)

* **Alat (Transmitter):** Memancarkan *Public Key* Apple via Bluetooth Low Energy (BLE).
* **Kurir (iPhone Orang Lain):** Menangkap sinyal BLE alat Anda secara anonim saat lewat dalam radius 10–30 meter.
* **Laporan (Cloud):** iPhone tersebut mengirimkan lokasinya sendiri ke iCloud Apple sebagai titik keberadaan alat Anda.
* **Akses Anda (Receiver):** Anda mengambil data lokasi dari server Apple menggunakan `findmy-rs` atau OpenHaystack di HP Android/Laptop.

### 3. Persyaratan Akun & Software

* **Apple ID:** Gratis, buat di Apple ID Official. Digunakan untuk "menaruh" kunci publik di server Apple.
* **Firmware:** Kode program OpenHaystack yang harus di-*flash* ke dalam ESP32.
* **Kunci Keamanan:**
    * **Public Key:** Dimasukkan ke alat (kalung).
    * **Private Key:** Disimpan di HP/Laptop Anda untuk membuka data lokasi yang terenkripsi.

### 4. Kelebihan & Batasan

**Kelebihan:**
* **Gratis Selamanya:** Tidak ada pulsa, tidak ada biaya server iCloud.
* **Jarak Tak Terbatas:** Bisa dilacak dari luar kota/luar negeri selama ada iPhone di sekitar alat.
* **Ukuran Mungil:** Bisa dibuat sekecil koin jika menggunakan *custom PCB*.

**Kekurangan:**
* **Tergantung Orang Lain:** Jika di area hutan tanpa orang lewat membawa iPhone, lokasi tidak akan terupdate.
* **Delay:** Lokasi tidak *real-time* detik demi detik (jeda 2–10 menit tergantung lalu lalang orang).

### 5. Strategi "Anti-Zonk" di Desa

Karena di desa jarang pengguna Apple, Anda disarankan menambahkan modul **LoRa (Long Range)** sebagai cadangan (Hybrid). Jadi, jika tidak ada iPhone, Anda tetap bisa melacak sendiri menggunakan antena radio pribadi hingga jarak 5–10 km.

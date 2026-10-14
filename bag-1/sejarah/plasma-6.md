# KDE Plasma 6 (2024–sekarang)

Plasma 6 adalah iterasi terbaru dari KDE Plasma, dibangun di atas Qt 6 dan KDE Frameworks 6. Ia dirilis pada 28 Februari 2024 dan menandai tonggak penting dalam perjalanan KDE.

#### 2.4.1 Persiapan Menuju Plasma 6

Pengembangan Plasma 6 dimulai jauh sebelum peluncurannya. Tim KDE harus:

1. Mem-porting semua kode dari Qt 5 ke Qt 6, yang melibatkan perubahan API yang signifikan.
2. Memperbarui semua KDE Frameworks untuk Qt 6.
3. Menyelesaikan transisi ke Wayland sebagai protokol default.
4. Memodernisasi komponen yang masih menggunakan teknologi lama.
5. Menyediakan jalur migrasi bagi tema dan widget lama.

{% hint style="warning" %}
**Peringatan**

Porting tema dari Plasma 5 ke Plasma 6 memerlukan perhatian khusus. Perubahan format metadata dari `metadata.desktop` ke `metadata.json`, serta perubahan impor QML, berarti banyak tema lama tidak langsung berfungsi. Diperlukan adaptasi manual.
{% endhint %}

#### 2.4.2 Fitur-Fitur Utama Plasma 6

**Qt 6 sebagai fondasi**

Membawa peningkatan performa, rendering yang lebih baik, dan API modern.

**Wayland sebagai default**

Plasma 6 secara default menggunakan Wayland, meskipun X11 masih didukung.

**Floating Panel**

Opsi panel mengambang yang memberikan tampilan lebih modern.

**Plasma Login Manager (PLM)**

Manajer login baru yang menggantikan SDDM secara opsional.

**Plasma-Keyboard**

Keyboard on-screen terintegrasi untuk tablet dan perangkat sentuh.

**Spectacle OCR**

Ekstraksi teks dari screenshot.

**Peningkatan animasi**

Animasi yang lebih halus pada layar ber-refresh rate tinggi.

**Pengaturan sistem yang lebih baik**

Antarmuka yang lebih intuitif dan konsisten.

#### 2.4.3 Plasma 6.0 hingga 6.5

Berikut ringkasan rilis dalam siklus Plasma 6 hingga saat ini:

| Versi      | Tanggal  | Sorotan Utama                                      |
| ---------- | -------- | -------------------------------------------------- |
| Plasma 6.0 | Feb 2024 | Peluncuran Qt 6, Wayland default, floating panel   |
| Plasma 6.1 | Jun 2024 | Peningkatan stabilitas, dukungan HDR               |
| Plasma 6.2 | Okt 2024 | Pengaturan tablet, perbaikan KWin                  |
| Plasma 6.3 | Feb 2025 | Optimasi performa, pengaturan yang lebih baik      |
| Plasma 6.4 | Jun 2025 | Peningkatan Wayland, dukungan perangkat keras baru |
| Plasma 6.5 | Okt 2025 | Perbaikan bug, peningkatan sistem pengaturan       |

_Tabel 2.2: Ringkasan rilis Plasma 6.0 hingga 6.5. Setiap rilis membawa perbaikan dan fitur baru yang meningkatkan pengalaman pengguna._

#### 2.4.4 Plasma 6.6 dan 6.7 (2026)

Pada tahun 2026, Plasma 6 mencapai kematangan lebih lanjut dengan fitur-fitur baru yang signifikan.

**Plasma 6.6 (Februari 2026)**

Plasma 6.6 menghadirkan beberapa modul baru:

* **Plasma Login Manager (PLM):** Manajer login opsional baru yang terintegrasi lebih baik dengan Plasma.
* **Plasma-Keyboard:** Keyboard on-screen terintegrasi untuk tablet dan perangkat sentuh.
* **Plasma-Setup:** Alat konfigurasi awal untuk pengguna baru.
* **Spectacle OCR:** Ekstraksi teks dari screenshot.
* **Wi-Fi via QR Code:** Koneksi Wi-Fi dengan memindai kode QR.
* **Ambient Light Sensor:** Kecerahan layar otomatis berdasarkan cahaya sekitar.
* **Animasi lebih halus pada layar refresh rate tinggi.**

**Plasma 6.7 (Juni 2026)**

Plasma 6.7 membawa fitur-fitur unggulan:

* **Virtual Desktop per Layar:** Setiap monitor dapat memiliki tata letak virtual desktop independen.
* **Toggle Mode Terang/Gelap:** Sakelar cepat untuk beralih antara tema terang dan gelap.
* **Tes Volume Mikrofon:** Fitur baru untuk menguji mikrofon.
* **Kalender Lunar Vietnam:** Dukungan kalender non-Gregorian.
* **“Background Apps” di System Tray:** Menampilkan aplikasi Flatpak yang berjalan di latar belakang.
* **Manajemen Printer yang Lebih Baik:** Ikon printer menunjukkan jumlah tugas aktif.
* **Type-ahead di Desktop:** Mode untuk memilih berkas dengan mengetik di desktop.
* **Kembalinya tema Oxygen dan Air:** Sebagai bagian dari persiapan ulang tahun ke-30 KDE.

{% hint style="info" %}
**Catatan**

Kembalinya tema Oxygen dan Air di Plasma 6.7 adalah bagian dari persiapan ulang tahun ke-30 KDE. Tema-tema klasik ini dihidupkan kembali untuk merayakan warisan KDE, sekaligus menunjukkan komitmen terhadap keberlanjutan dan penghargaan terhadap sejarah.
{% endhint %}

#### 2.4.5 Plasma 6.8 dan 6.9: Arah ke Depan

Peningkatan yang direncanakan untuk rilis mendatang meliputi:

* **Navigasi keyboard yang lebih baik:** Tombol panah di KRunner akan berfungsi lebih intuitif.
* **Thumbnail virtual desktop:** Efek Overview KWin akan menampilkan thumbnail yang lebih “harmonis dan menyenangkan secara visual”.
* **Kontrol kecerahan keyboard backlit:** Keyboard backlit akan terhubung setelah login awal, bukan saat boot.
* **Peningkatan dukungan HDR:** Dukungan HDR yang lebih matang untuk monitor yang mendukung.
* **Optimasi performa:** Pengurangan penggunaan sumber daya lebih lanjut.


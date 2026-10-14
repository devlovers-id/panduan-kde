# KDE Plasma 5 (2014–2024)

Jika Plasma 4 adalah masa remaja yang penuh gejolak, Plasma 5 adalah masa kedewasaan. Selama sepuluh tahun masa pengembangannya, Plasma 5 menjadi salah satu lingkungan desktop paling stabil, kaya fitur, dan dihormati di dunia Linux.

#### 2.3.1 Modernisasi Menyeluruh

Plasma 5 diperkenalkan pada 15 Juli 2014 sebagai bagian dari KDE Frameworks 5. Perubahan utama dari Plasma 4 meliputi:

**Migrasi ke Qt 5**

Membawa peningkatan performa, dukungan grafis yang lebih baik, dan API yang lebih modern.

**Migrasi ke KDE Frameworks 5**

Memisahkan pustaka KDE menjadi lebih dari 80 framework modular yang dapat digunakan di luar KDE.

**Tema Breeze baru**

Menggantikan tema Oxygen sebagai default, memberikan tampilan yang lebih modern dan konsisten.

**Arsitektur QML-first**

Plasma 5 dibangun sepenuhnya dengan QML untuk shell, memungkinkan pengembangan widget yang lebih cepat.

**Pemisahan Plasma Workspaces**

Menjadi paket terpisah: `plasma-desktop`, `plasma-netbook`, `plasma-active`, dan lainnya.

| Plasma 4          | Plasma 5            | Plasma 6            |
| ----------------- | ------------------- | ------------------- |
| Qt 4 • KDE Libs 4 | Qt 5 • Frameworks 5 | Qt 6 • Frameworks 6 |
| QGraphicsView     | QML-first           | Wayland default     |

_Gambar 2.3: Transisi besar dalam arsitektur KDE Plasma. Setiap transisi membawa perubahan fundamental pada teknologi yang mendasarinya._

#### 2.3.2 Migrasi ke Qt 5 dan Frameworks 5

Migrasi ke Qt 5 dan KDE Frameworks 5 adalah proyek besar yang memakan waktu bertahun-tahun. Tim KDE harus:

1. Mem-porting semua kode dari Qt 4 ke Qt 5, yang melibatkan ribuan perubahan API.
2. Memisahkan monolitik `kdelibs` menjadi lebih dari 80 framework yang independen.
3. Menulis ulang Plasma Shell dalam QML, menggantikan implementasi C++ yang lama.
4. Memperbarui semua widget dan aplikasi KDE untuk menggunakan API baru.

Proses ini memakan waktu sekitar dua tahun dan melibatkan ratusan kontributor dari seluruh dunia.

#### 2.3.3 Fitur-Fitur Inovatif Plasma 5

Selama masa pengembangannya, Plasma 5 memperkenalkan banyak fitur inovatif:

**Plasma Mobile (2015)**

Varian Plasma untuk perangkat mobile, menunjukkan fleksibilitas arsitektur Plasma.

**KDE Connect (2015)**

Integrasi mendalam antara ponsel dan desktop, memungkinkan berbagi berkas, sinkronisasi notifikasi, dan kontrol media.

**Wayland Support (2016)**

Dukungan awal untuk protokol Wayland, meskipun masih eksperimental pada awalnya.

**HiDPI Support (2017)**

Dukungan untuk layar beresolusi tinggi, dengan scaling otomatis.

**Plasma Vault (2017)**

Fitur enkripsi untuk folder pribadi.

**Night Color (2018)**

Mode malam yang mengurangi cahaya biru.

**Wayland Default (2019)**

Plasma 5.17 mulai menggunakan Wayland sebagai default di beberapa distribusi.

**System Monitor (2021)**

Aplikasi pemantauan sistem baru yang modern.

**Overview Effect (2022)**

Efek “Overview” mirip GNOME, memberikan pengalaman multitasking yang lebih baik.

**HDR Support (2023)**

Dukungan awal untuk HDR (_High Dynamic Range_) di Wayland.

{% hint style="success" %}
**Tips**

Salah satu fitur yang paling dihargai pengguna Plasma 5 adalah Activities. Meskipun konsepnya sudah ada di Plasma 4, implementasinya di Plasma 5 jauh lebih matang dan dapat digunakan secara praktis untuk memisahkan konteks kerja.
{% endhint %}

#### 2.3.4 Evolusi KWin di Plasma 5

KWin mengalami transformasi signifikan selama siklus Plasma 5. Dari manajer jendela X11 tradisional, ia menjadi kompositor Wayland yang matang.

| Versi       | Pencapaian Utama                     | Catatan                       |
| ----------- | ------------------------------------ | ----------------------------- |
| Plasma 5.0  | Porting ke Qt 5, kompositing default | Awal yang stabil              |
| Plasma 5.5  | Dukungan Wayland yang lebih baik     | Masih eksperimental           |
| Plasma 5.9  | Wayland untuk sesi pengujian         | Fitur inti berfungsi          |
| Plasma 5.12 | Fractional scaling di Wayland        | LTS pertama dengan Wayland    |
| Plasma 5.17 | Wayland default di Fedora            | Tonggak penting               |
| Plasma 5.21 | Wayland untuk sesi utama             | Dukungan multi-GPU            |
| Plasma 5.24 | Wayland produksi                     | Sesi default di banyak distro |
| Plasma 5.27 | Wayland stabil sepenuhnya            | Rilis terakhir Plasma 5       |

_Tabel 2.1: Perkembangan dukungan Wayland di KWin selama siklus Plasma 5. Perhatikan bagaimana Wayland berevolusi dari eksperimental menjadi protokol default._

#### 2.3.5 Plasma 5.27: Rilis Terakhir

Plasma 5.27, dirilis pada 14 Februari 2023, adalah rilis terakhir dalam siklus Plasma 5. Ia menerima dukungan jangka panjang (LTS) dan tetap digunakan oleh banyak distribusi hingga hari ini. Fitur-fitur penting dari rilis ini meliputi:

* **Wayland yang stabil:** Dukungan Wayland yang cukup matang untuk penggunaan sehari-hari.
* **Kinerja yang dioptimalkan:** Pengurangan penggunaan CPU dan memori dibanding versi sebelumnya.
* **Peningkatan KWin:** Efek yang lebih halus dan dukungan multi-monitor yang lebih baik.
* **Perbaikan bug:** Ribuan bug yang diperbaiki selama siklus pengembangan.


# Plasma 6.7 (Juni 2026)

Plasma 6.7 dirilis pada 16 Juni 2026, dan digambarkan sebagai “pembangkit produktivitas yang menyenangkan untuk digunakan”. Rilis ini membawa beberapa fitur yang telah lama ditunggu-tunggu oleh komunitas.

#### 8.2.1 Virtual Desktop per Layar

Setelah 21 tahun, fitur virtual desktop per layar akhirnya tiba di KDE Plasma. Fitur ini memungkinkan setiap monitor untuk memiliki set virtual desktop-nya sendiri, sehingga pengguna dapat beralih antar virtual desktop secara independen di setiap layar.

{% hint style="info" %}
**Virtual Desktop per Layar** adalah fitur yang memungkinkan setiap monitor fisik untuk memiliki set virtual desktop yang independen. Misalnya, monitor kiri dapat berada di Desktop 1 sementara monitor kanan berada di Desktop 3.
{% endhint %}

Fitur ini sangat berguna untuk pengguna dengan konfigurasi multi-monitor yang kompleks. Sebelumnya, semua monitor berbagi set virtual desktop yang sama, sehingga beralih desktop di satu monitor akan mengubah semua monitor.

Fitur ini tidak diaktifkan secara default. Pengguna harus mengaktifkannya dengan mencentang “Switch desktops independently for each screen” di bagian Virtual Desktops di pengaturan.

```
Setiap monitor dapat beralih desktop secara independen

Monitor Kiri                Monitor Kanan
1  2  3                     A  B  C

Desktop 2                   Desktop C
```

_Gambar 8.2: Virtual Desktop per Layar di Plasma 6.7. Setiap monitor dapat berada di virtual desktop yang berbeda secara bersamaan._

#### 8.2.2 Tombol Terang/Gelap Cepat

Plasma 6.7 menambahkan tombol cepat di system tray untuk beralih antara Global Theme terang dan gelap. Di Plasma 6.6, pengguna sudah dapat membuat Global Theme kustom dan beralih di antaranya berdasarkan siklus siang-malam. Plasma 6.7 memberikan kontrol yang lebih langsung dengan tombol toggle cepat.

#### 8.2.3 Tes Volume Mikrofon

Fitur baru untuk menguji volume mikrofon sebelum bergabung dengan panggilan video atau konferensi. Ini menghilangkan kebutuhan untuk bertanya “apakah mikrofon saya berfungsi?” atau “apakah volume saya terlalu keras?”.

#### 8.2.4 Press-and-Hold untuk Karakter Khusus

Dengan keyboard virtual Plasma yang diaktifkan, menekan dan menahan tombol akan memunculkan karakter khusus yang terkait. Fitur ini mirip dengan yang ada di keyboard ponsel, dan sangat berguna untuk mengetik karakter non-standar.

#### 8.2.5 Kalender Lunar Vietnam

Plasma 6.7 menambahkan kalender lunar Vietnam ke set kalender non-Gregorian yang tersedia. Pengguna sekarang dapat melacak tanggal dan acara menggunakan kedua sistem kalender dengan lebih mudah.

#### 8.2.6 “Background Apps” di System Tray

System Tray sekarang juga menampilkan aplikasi yang menggunakan sistem “Background Apps” yang lebih baru, yang umum untuk aplikasi dengan format paket Flatpak. Ini memberikan visibilitas yang lebih baik tentang aplikasi apa yang berjalan di latar belakang.

#### 8.2.7 Manajemen Printer yang Lebih Baik

Dukungan pencetakan KDE Plasma terus matang. Ikon printer di System Tray sekarang menampilkan jumlah tugas aktif dalam badge kecil. Untuk perusahaan, Plasma 6.7 membuat koneksi ke printer bersama di jaringan Windows menjadi lebih mudah, dan alat manajemen antrian cetak baru menawarkan lebih banyak kekuatan.

#### 8.2.8 Peningkatan Usability

* **Perpindahan Virtual Desktop Lebih Cepat di Overview:** Saat membuka Overview dengan `Meta + W`, pengguna dapat beralih virtual desktop dengan scroll atau tombol `Page Up`/`Page Down`.
* **Drag-and-Drop Favorit:** Menambahkan atau menghapus aplikasi favorit di Application Launcher, Application Menu, dan Application Dashboard kini semudah drag-and-drop.
* **Manajemen Perangkat Lunak Lebih Intuitif:** Discover sekarang memiliki tombol “Install” yang lebih jelas, kartu aplikasi yang didesain ulang, dan pengurutan yang lebih intuitif.
* **Perbandingan Zona Waktu:** Digital Clock widget sekarang menampilkan berapa jam lebih awal atau lebih lambat setiap zona waktu dibandingkan zona waktu lokal.
* **Type-ahead di Desktop:** Mode untuk memilih berkas dengan mengetik di desktop.

#### 8.2.9 Kembalinya Tema Oxygen dan Air

Sebagai persiapan untuk ulang tahun ke-30 KDE, tema Oxygen—yang digunakan oleh KDE 4—dihidupkan kembali. Tema ini tersedia sebagai opsi untuk pengguna yang merindukan tampilan klasik KDE.

#### 8.2.10 Sistem Tema Union

Plasma 6.7 juga memperkenalkan Union, sistem tema berbasis CSS yang baru. Ini adalah pratinjau teknologi yang akan menjadi fondasi untuk sistem tema KDE Plasma di masa depan.

#### 8.2.11 Analisis

Plasma 6.7 adalah rilis yang berfokus pada produktivitas dan multi-monitor. Virtual desktop per layar adalah fitur yang telah lama diminta komunitas, dan implementasinya menunjukkan komitmen KDE untuk mendengarkan umpan balik pengguna. Fitur seperti tes volume mikrofon dan perbandingan zona waktu menunjukkan perhatian terhadap detail dan kebutuhan praktis pengguna sehari-hari.

{% hint style="info" %}
Plasma 6.7 adalah rilis terakhir yang menyertakan sesi X11. Mulai Plasma 6.8, sesi X11 akan dihapus sepenuhnya, dan hanya sesi Wayland yang tersedia.
{% endhint %}


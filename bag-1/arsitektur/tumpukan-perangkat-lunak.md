# Gambaran Umum Tumpukan Perangkat Lunak

KDE Plasma bukanlah monolit tunggal, melainkan kumpulan komponen yang bekerja sama melalui antarmuka yang terdefinisi dengan baik. Memahami tumpukan perangkat lunaknya adalah langkah pertama untuk memahami sistem secara keseluruhan.

#### 3.1.1 Komponen Inti

Tabel [3.1](pendahuluan.md#3%5FArsitektur%5Fdan%5FKomponen) merangkum komponen-komponen inti KDE Plasma beserta peran masing-masing.

| Komponen       | Paket         | Fungsi Utama                                  |
| -------------- | ------------- | --------------------------------------------- |
| Plasma Shell   | `plasmashell` | Menampilkan desktop, panel, dan widget        |
| KWin           | `kwin`        | Manajer jendela dan kompositor grafis         |
| KDE Frameworks | `kf6-*`       | Kumpulan pustaka pendukung                    |
| Qt 6           | `qt6-*`       | Kerangka kerja aplikasi dasar                 |
| KPackage       | `kpackage`    | Sistem paket untuk widget dan tema            |
| KConfig        | `kconfig`     | Manajemen konfigurasi                         |
| KIO            | `kio`         | Abstraksi I/O untuk akses berkas dan jaringan |
| Solid          | `solid`       | Deteksi dan abstraksi perangkat keras         |

_Tabel 3.1: Komponen inti KDE Plasma beserta paket dan fungsinya. Setiap komponen dirancang untuk tujuan spesifik namun terintegrasi melalui antarmuka yang terdefinisi dengan baik._

#### 3.1.2 Diagram Tumpukan

Gambar [3.1](pendahuluan.md#24%5F3%5FArsitektur%5Fdan%5FKomponen) menunjukkan tumpukan perangkat lunak KDE Plasma secara lengkap, dari kernel hingga aplikasi pengguna.

| Lapisan          | Komponen                                                    |
| ---------------- | ----------------------------------------------------------- |
| Pengguna         | Aplikasi KDE & Pihak Ketiga (Qt, GTK, Electron)             |
| Plasma Workspace | Plasma Shell, KWin, System Settings                         |
| Pustaka          | KDE Frameworks 6 (80+ pustaka modular)                      |
| Kerangka kerja   | Qt 6 + Qt Wayland Integration                               |
| Display          | Display Server: Wayland (default) / X11 (opsional)          |
| Hardware         | Hardware Abstraction: `libdrm`, `libinput`, `evdev`, `udev` |
| Sistem           | Kernel Linux / FreeBSD                                      |

_Gambar 3.1: Tumpukan perangkat lunak KDE Plasma secara lengkap. Setiap lapisan bergantung pada lapisan di bawahnya melalui antarmuka yang stabil. Perhatikan posisi Plasma Workspace sebagai lapisan perantara antara KDE Frameworks dan aplikasi pengguna._

Gambar [3.1](pendahuluan.md#24%5F3%5FArsitektur%5Fdan%5FKomponen) mengungkapkan prinsip arsitektur penting: setiap lapisan hanya bergantung pada lapisan di bawahnya, dan antarmuka di antara lapisan-lapisan ini dirancang agar tetap stabil. Prinsip ini memungkinkan KDE Plasma untuk mengganti komponen tanpa harus menulis ulang seluruh sistem—seperti yang terjadi ketika Plasma 5 beralih dari Qt 4 ke Qt 5, dan Plasma 6 beralih dari Qt 5 ke Qt 6.

#### 3.1.3 Prinsip Desain Arsitektur

Arsitektur KDE Plasma dibangun di atas beberapa prinsip desain yang konsisten:

1. **Modularitas.** Setiap komponen dirancang untuk dapat dikembangkan, diuji, dan dirilis secara independen. KDE Frameworks, misalnya, terdiri dari lebih dari 80 pustaka terpisah.
2. **Antarmuka yang stabil.** Meskipun implementasi dapat berubah, antarmuka publik dari setiap komponen dijaga agar tetap kompatibel.
3. **Pemisahan tanggung jawab.** Plasma Shell mengelola antarmuka, KWin mengelola jendela, KIO mengelola I/O. Tidak ada tumpang tindih fungsi.
4. **Konfigurabilitas.** Hampir semua perilaku dapat dikonfigurasi melalui berkas INI yang dapat diedit pengguna.
5. **Asinkronisitas.** Operasi yang memakan waktu (I/O, rendering) dilakukan secara asinkron untuk menjaga responsivitas.

{% hint style="info" %}
**Catatan**

Modularitas KDE Plasma bukan sekadar jargon teknis. Ia memiliki konsekuensi praktis: pengguna dapat mengganti KWin dengan manajer jendela lain, menggunakan Dolphin di lingkungan desktop lain, atau hanya menginstal sebagian dari KDE Frameworks tanpa harus menginstal seluruh ekosistem.
{% endhint %}


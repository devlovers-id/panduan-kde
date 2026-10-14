# KWin: Manajer Jendela dan Kompositor

KWin adalah manajer jendela dan kompositor grafis untuk KDE Plasma. Ia bertanggung jawab untuk mengelola jendela aplikasi, menangani input dari keyboard dan mouse, dan menghasilkan output grafis yang di-render ke layar.

#### 3.3.1 Peran Ganda KWin

KWin memiliki dua peran utama yang dalam lingkungan desktop lain sering dipisahkan:

**Manajer Jendela**

Mengelola posisi, ukuran, dan status jendela. Ia menangani operasi seperti memindahkan, mengubah ukuran, meminimalkan, memaksimalkan, dan menutup jendela.

**Kompositor**

Menggabungkan output dari berbagai jendela menjadi satu gambar akhir yang ditampilkan ke layar. Ia menangani efek visual seperti transparansi, blur, dan animasi.

{% hint style="info" %}
**Catatan**

Peran ganda KWin sebagai manajer jendela dan kompositor bukanlah kebetulan. Ini adalah keputusan desain yang memungkinkan integrasi yang lebih erat antara manajemen jendela dan efek visual. Di X11, kompositor terpisah seperti `xcompmgr` dapat digunakan, tetapi ini memerlukan sinkronisasi yang lebih rumit.
{% endhint %}

#### 3.3.2 Arsitektur KWin

Gambar [3.3](pendahuluan.md#3%5F3%5FKWin%5F%5FManajer%5FJendela%5Fdan%5FKo) menunjukkan arsitektur internal KWin secara skematis.

| Lapisan   | Komponen                                          |
| --------- | ------------------------------------------------- |
| Output    | Wayland / X11 → Framebuffer / GPU Output          |
| Rendering | Scene Graph, OpenGL / Vulkan, QPainter (fallback) |
| Inti      | Workspace, Window, Effects, Rules                 |
| Input     | `libinput` / `evdev` → Keyboard, Mouse, Touch     |

_Gambar 3.3: Arsitektur internal KWin. Setiap lapisan memiliki tanggung jawab yang jelas: input, logika manajemen jendela, rendering grafis, dan output ke display server._

#### 3.3.3 Fitur-Fitur Utama KWin

KWin menyediakan berbagai fitur yang membuatnya menjadi salah satu manajer jendela paling canggih di dunia Linux.

**Efek Desktop**

KWin memiliki sistem efek yang kaya, yang dapat diaktifkan atau dinonaktifkan secara individual:

**Desktop Cube**

Menampilkan desktop sebagai kubus 3D yang dapat diputar.

**Present Windows**

Menampilkan semua jendela sebagai thumbnail untuk pemilihan cepat.

**Overview**

Memberikan tampilan menyeluruh dari semua jendela dan desktop.

**Wobbly Windows**

Memberikan efek “goyang” pada jendela saat dipindahkan.

**Blur**

Memberikan efek blur pada area tertentu di belakang jendela.

**Slide Back**

Menampilkan animasi saat jendela diaktifkan.

**Manajemen Jendela**

**Snapping**

Jendela dapat “menempel” ke tepi layar atau ke jendela lain.

**Tiling**

Jendela dapat disusun dalam tata letak ubin otomatis.

**Window Rules**

Aturan khusus untuk jendela tertentu berdasarkan judul, kelas, atau kriteria lainnya.

**Virtual Desktops**

Dukungan untuk beberapa desktop virtual.

**Activities**

Integrasi dengan Activities Plasma.

**Kompositing**

**Transparency**

Dukungan untuk jendela transparan dan semi-transparan.

**Shadows**

Bayangan di sekeliling jendela.

**Animations**

Animasi untuk _minimize_, _maximize_, _close_, dan lainnya.

**Color Management**

Manajemen warna untuk kalibrasi monitor.

{% hint style="success" %}
**Tips**

Untuk mengakses pengaturan KWin, buka System Settings Window Management KWin Scripts atau Window Rules. Anda juga dapat mengakses pengaturan efek desktop melalui System Settings Workspace Behavior Desktop Effects.
{% endhint %}

#### 3.3.4 KWin Scripts

KWin mendukung ekstensi melalui scripts yang ditulis dalam JavaScript atau QML. Script ini dapat memodifikasi perilaku KWin tanpa harus mengompilasi ulang.

**KWin Scripting API**

Menyediakan akses ke API JavaScript untuk berinteraksi dengan jendela, desktop, dan efek.

**KWin Effects**

Ditulis dalam C++ dan diintegrasikan lebih dalam dengan sistem rendering.

**KWin Rules**

Konfigurasi deklaratif untuk perilaku jendela tertentu.

#### 3.3.5 Wayland dan X11 di KWin

KWin mendukung dua protokol display server:

| Aspek              | X11                                   | Wayland                        |
| ------------------ | ------------------------------------- | ------------------------------ |
| Status di Plasma 6 | Opsional (_fallback_)                 | Default                        |
| Keamanan           | Aplikasi dapat mengakses input global | Isolasi antar aplikasi         |
| Rendering          | Bergantung pada kompositing eksternal | Terintegrasi                   |
| Multi-Monitor      | Dukungan matang                       | Dukungan yang terus berkembang |
| HiDPI              | Perlu konfigurasi manual              | Scaling otomatis               |
| Aplikasi lama      | Kompatibel penuh                      | Memerlukan XWayland            |

_Tabel 3.3: Perbandingan X11 dan Wayland di KWin. Wayland menawarkan keamanan dan integrasi yang lebih baik, tetapi masih ada tantangan untuk kompatibilitas aplikasi lama._


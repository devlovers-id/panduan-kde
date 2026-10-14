# Studi Kasus: Alur Kerja Pengguna Tingkat Lanjut

#### 5.6.1 Studi Kasus 1: Pengembang Perangkat Lunak

Seorang pengembang perangkat lunak dapat mengonfigurasi sistemnya sebagai berikut:

| Komponen                | Konfigurasi                                                                                                                           |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Activity “Pengembangan” | Panel atas dengan global menu, panel bawah dengan terminal dan editor kode, serta widget System Monitor untuk penggunaan CPU dan RAM. |
| Activity “Komunikasi”   | Panel bawah dengan email, chat, dan kalender, serta widget Notes untuk catatan cepat.                                                 |
| Pintasan kustom         | `Meta + T` untuk terminal dan `Meta + E` untuk editor kode.                                                                           |
| KRunner                 | Digunakan untuk menjalankan perintah shell cepat dengan prefix `>`.                                                                   |
| Virtual Desktop         | Empat virtual desktop: 1) Kode, 2) Terminal, 3) Browser, 4) Dokumentasi.                                                              |

#### 5.6.2 Studi Kasus 2: Desainer Grafis

Seorang desainer grafis dapat mengonfigurasi KDE Plasma sebagai berikut:

| Komponen       | Konfigurasi                                                                                                                        |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Tema kustom    | Menggunakan tema “WhiteSur” yang meniru macOS, dengan warna pastel dan ikon minimalis.                                             |
| Panel atas     | Menampilkan global menu, workspace switcher, dan system tray.                                                                      |
| Dock bawah     | Menggunakan widget “Application Dashboard” yang menampilkan aplikasi desain seperti Krita, Inkscape, dan GIMP.                     |
| Widget desktop | Widget Color Picker untuk mengambil warna dari layar, serta Notes untuk catatan desain.                                            |
| KRunner        | Digunakan untuk mencari berkas gambar dengan cepat.                                                                                |
| Activities     | Dua Activity: “Desain” dan “Referensi”. Activity “Referensi” memiliki banyak widget Folder View yang menampilkan gambar referensi. |

#### 5.6.3 Studi Kasus 3: Pengguna Multitasking

Seorang pengguna yang sering multitasking dapat mengonfigurasi KDE Plasma sebagai berikut:

| Komponen        | Konfigurasi                                                                                |
| --------------- | ------------------------------------------------------------------------------------------ |
| Panel kiri      | Menampilkan Task Manager dengan daftar jendela yang sedang berjalan.                       |
| Panel bawah     | Menampilkan Application Launcher, System Tray, dan Digital Clock.                          |
| Widget desktop  | Notes untuk catatan tugas, Timer untuk Pomodoro, dan System Monitor.                       |
| Virtual Desktop | Enam virtual desktop: 1) Email, 2) Browser, 3) Dokumen, 4) Spreadsheet, 5) Media, 6) Chat. |
| Pintasan        | `Meta + 1` hingga `Meta + 6` untuk berpindah antar virtual desktop.                        |
| KRunner         | Digunakan untuk menghitung, mengonversi mata uang, dan mencari kontak.                     |

#### 5.6.4 Studi Kasus 4: Pengguna dengan Perangkat Keras Lama

Seorang pengguna dengan laptop berusia delapan tahun dapat mengonfigurasi KDE Plasma untuk performa maksimal:

* Aktifkan Low Resource Mode di **System Settings → Workspace Behavior → General Behavior**.
* Nonaktifkan efek desktop yang berat seperti blur dan cube.
* Gunakan tema ringan seperti “Breeze” default tanpa transparansi.
* Gunakan sesi X11 daripada Wayland jika driver grafis tidak mendukung Wayland dengan baik.
* Kurangi jumlah virtual desktop menjadi dua.
* Nonaktifkan animasi dan transisi.
* Gunakan widget minimal seperti jam dan system tray.

{% hint style="info" %}
Untuk mengurangi penggunaan sumber daya lebih lanjut, pertimbangkan menggunakan Plasma Minimal, hanya paket `plasma-desktop`, daripada instalasi lengkap. Ini mengurangi jumlah proses yang berjalan di latar belakang.
{% endhint %}

#### 5.6.5 Studi Kasus 5: Pengguna dengan Kebutuhan Aksesibilitas

Seorang pengguna dengan kebutuhan aksesibilitas khusus dapat mengonfigurasi KDE Plasma sebagai berikut:

* Aktifkan Screen Reader (Orca) di **System Settings → Accessibility → Screen Reader**.
* Aktifkan High Contrast untuk pengguna dengan gangguan penglihatan.
* Aktifkan Magnifier untuk memperbesar area layar.
* Aktifkan Sticky Keys untuk pengguna dengan kesulitan menekan kombinasi tombol.
* Aktifkan Slow Keys untuk pengguna dengan tremor.
* Aktifkan Bounce Keys untuk menghindari penekanan tombol berulang.
* Sesuaikan ukuran font dan ikon.
* Aktifkan Night Color untuk mengurangi kelelahan mata.

> **Catatan**
>
> KDE Plasma memiliki dukungan aksesibilitas yang sangat baik. Jika Anda memiliki kebutuhan aksesibilitas khusus, jangan ragu untuk menjelajahi semua opsi di **System Settings → Accessibility**. Komunitas KDE juga menyediakan dokumentasi dan dukungan yang luas untuk topik ini.


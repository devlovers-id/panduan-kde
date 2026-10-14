# Studi Kasus: Dari Breeze ke Tema Sepenuhnya Kustom

Untuk mengilustrasikan bagaimana semua komponen kustomisasi bekerja sama, mari kita lihat studi kasus lengkap: mengubah KDE Plasma dari Breeze default menjadi tema sepenuhnya kustom.

#### 6.10.1 Langkah 1: Memilih Arah Desain

Sebelum memulai, tentukan arah desain yang diinginkan:

* **Tema dasar:** Apakah Anda ingin tampilan minimalis, macOS-like, Windows-like, atau unik?
* **Mode:** Terang, gelap, atau dinamis dengan Material You?
* **Warna aksen:** Biru, ungu, hijau, atau warna lain?
* **Tata letak:** Panel atas, bawah, atau samping?

#### 6.10.2 Langkah 2: Memilih Global Theme

Untuk contoh ini, gunakan tema WhiteSur yang meniru macOS:

{% stepper %}
{% step %}
### Buka Global Theme

Buka **System Settings → Colors & Themes → Global Theme**.
{% endstep %}

{% step %}
### Dapatkan tema baru

Klik **Get New Global Themes...**.
{% endstep %}

{% step %}
### Cari WhiteSur

Cari “WhiteSur” dan instal.
{% endstep %}

{% step %}
### Terapkan tema

Terapkan tema dengan mengklik **Apply**.
{% endstep %}
{% endstepper %}

#### 6.10.3 Langkah 3: Menyesuaikan Plasma Style

Meskipun Global Theme sudah menyertakan Plasma Style, Anda mungkin ingin menyesuaikannya:

{% stepper %}
{% step %}
### Buka Plasma Style

Buka **System Settings → Colors & Themes → Plasma Style**.
{% endstep %}

{% step %}
### Pilih style

Pilih Plasma Style yang cocok, misalnya “WhiteSur-dark”.
{% endstep %}

{% step %}
### Sesuaikan tampilan

Sesuaikan warna dan transparansi sesuai keinginan.
{% endstep %}
{% endstepper %}

#### 6.10.4 Langkah 4: Mengubah Skema Warna

{% stepper %}
{% step %}
### Buka Colors

Buka **System Settings → Colors & Themes → Colors**.
{% endstep %}

{% step %}
### Pilih skema

Pilih skema “WhiteSur” atau “WhiteSur-dark”.
{% endstep %}

{% step %}
### Edit skema

Klik **Edit Scheme...** untuk menyesuaikan warna.
{% endstep %}

{% step %}
### Sesuaikan warna

Ubah warna aksen, latar belakang, dan teks sesuai keinginan.
{% endstep %}

{% step %}
### Simpan skema

Klik **Save As...** untuk menyimpan dengan nama kustom.
{% endstep %}
{% endstepper %}

#### 6.10.5 Langkah 5: Menerapkan Tema Ikon

{% stepper %}
{% step %}
### Buka Icons

Buka **System Settings → Colors & Themes → Icons**.
{% endstep %}

{% step %}
### Instal WhiteSur

Instal tema “WhiteSur” dari KDE Store.
{% endstep %}

{% step %}
### Terapkan tema

Pilih tema dan terapkan.
{% endstep %}
{% endstepper %}

#### 6.10.6 Langkah 6: Mengonfigurasi Dekorasi Jendela

Untuk dekorasi jendela yang lebih kustom, gunakan Klassy:

{% stepper %}
{% step %}
### Instal Klassy

Instal Klassy melalui repositori distribusi.
{% endstep %}

{% step %}
### Buka Window Decorations

Buka **System Settings → Colors & Themes → Window Decorations**.
{% endstep %}

{% step %}
### Pilih Klassy
{% endstep %}

{% step %}
### Konfigurasikan Klassy

Klik **Configure Klassy**.
{% endstep %}

{% step %}
### Atur dekorasi

Atur ukuran tombol, sudut jendela rounded, dan transparansi.
{% endstep %}

{% step %}
### Terapkan perubahan
{% endstep %}
{% endstepper %}

#### 6.10.7 Langkah 7: Menyesuaikan Tata Letak Panel

Untuk meniru tampilan macOS:

{% stepper %}
{% step %}
### Edit panel

Klik kanan panel, lalu pilih **Edit Panel**.
{% endstep %}

{% step %}
### Pindahkan panel

Seret panel ke atas layar.
{% endstep %}

{% step %}
### Atur tinggi panel

Atur tinggi panel menjadi lebih tipis.
{% endstep %}

{% step %}
### Tambahkan Global Menu

Tambahkan widget Global Menu ke panel.
{% endstep %}

{% step %}
### Hapus widget yang tidak perlu

Hapus Task Manager dan Desktop Pager.
{% endstep %}

{% step %}
### Tambahkan Application Menu

Tambahkan widget Application Menu sebagai pengganti Application Launcher.
{% endstep %}

{% step %}
### Aktifkan Floating Panel

Aktifkan opsi Floating Panel untuk tampilan yang lebih modern.
{% endstep %}
{% endstepper %}

#### 6.10.8 Langkah 8: Menambahkan Dock

Untuk pengalaman macOS yang lebih lengkap:

{% stepper %}
{% step %}
### Tambahkan panel baru

Tambahkan panel baru di bawah dengan klik kanan desktop, lalu pilih **Add Panel → Empty Panel**.
{% endstep %}

{% step %}
### Atur panel

Atur panel menjadi Floating dan Auto-hide.
{% endstep %}

{% step %}
### Tambahkan widget

Tambahkan widget Application Dashboard atau Task Manager.
{% endstep %}

{% step %}
### Atur ikon

Atur ukuran ikon dan spasi.
{% endstep %}
{% endstepper %}

#### 6.10.9 Langkah 9: Menambahkan Widget Kustom

Tambahkan widget yang melengkapi tema:

* Weather di panel atas untuk menampilkan cuaca.
* Notes di desktop untuk catatan cepat.
* System Monitor di panel atas untuk pemantauan sistem.
* Digital Clock dengan format waktu yang cocok.

#### 6.10.10 Langkah 10: Menerapkan Material You Colors

Untuk tema yang dinamis berdasarkan wallpaper:

{% stepper %}
{% step %}
### Instal Material You Colors

Instal `kde-material-you-colors`.
{% endstep %}

{% step %}
### Jalankan backend
{% endstep %}

{% step %}
### Tambahkan widget

Tambahkan widget Plasma You Colors ke panel.
{% endstep %}

{% step %}
### Atur wallpaper

Set wallpaper favorit Anda.
{% endstep %}

{% step %}
### Gunakan skema otomatis

Skema warna akan otomatis berubah sesuai wallpaper.
{% endstep %}
{% endstepper %}

#### 6.10.11 Hasil Akhir

Setelah mengikuti langkah-langkah di atas, desktop KDE Plasma Anda akan memiliki:

* Tampilan macOS-like dengan panel atas dan dock bawah.
* Tema WhiteSur yang konsisten di seluruh sistem.
* Dekorasi jendela Klassy dengan tombol yang dapat dikustomisasi.
* Ikon WhiteSur yang cocok dengan tema.
* Skema warna kustom yang sesuai preferensi.
* Widget yang melengkapi tema dan meningkatkan fungsionalitas.
* Skema warna dinamis dari Material You Colors, jika digunakan.

{% hint style="info" %}
Setelah semua kustomisasi selesai, gunakan Konsave untuk menyimpan konfigurasi Anda ke file. Ini memungkinkan Anda memulihkan kustomisasi di sistem lain atau setelah reinstall.
{% endhint %}


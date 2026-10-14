# Widget dan Plasmoid

Widget, sering disebut Plasmoid, adalah salah satu fitur paling khas dari KDE Plasma. Mereka memungkinkan Anda menambahkan fungsionalitas ke desktop atau panel tanpa harus menjalankan aplikasi terpisah.

#### 5.2.1 Kategori Widget

| Kategori      | Contoh widget                                          |
| ------------- | ------------------------------------------------------ |
| Informasi     | Digital Clock, Weather, System Monitor, Dictionary     |
| Produktivitas | Notes, Timer, Clipboard, Calculator                    |
| Multimedia    | Media Player, Now Playing, Audio Volume                |
| Sistem        | Application Launcher, Task Manager, System Tray, Trash |
| Utilitas      | Folder View, KRunner, Show Desktop, Color Picker       |
| Internet      | RSS Now, Comics, Facebook, Weather Station             |

Ratusan widget tersedia melalui KDE Store.

#### 5.2.2 Menambahkan Widget

{% stepper %}
{% step %}
### Buka opsi widget

Klik kanan pada desktop atau panel.
{% endstep %}

{% step %}
### Pilih Add Widgets

Pilih **Add Widgets** untuk desktop, atau **Add Widgets** di Edit Mode untuk panel.
{% endstep %}

{% step %}
### Pilih widget

Panel samping akan muncul dengan daftar widget yang tersedia.
{% endstep %}

{% step %}
### Tambahkan widget

Seret widget ke lokasi yang diinginkan, atau klik widget dan pilih **Add to Desktop** atau **Add to Panel**.
{% endstep %}

{% step %}
### Jelajahi widget tambahan

Klik **Get New Widgets** untuk menjelajahi KDE Store dan mengunduh widget tambahan.
{% endstep %}
{% endstepper %}

#### 5.2.3 Widget Populer

**Digital Clock**

Widget jam digital yang menampilkan waktu dan tanggal. Dapat dikonfigurasi untuk menampilkan:

* Format 12 atau 24 jam
* Tanggal dalam berbagai format
* Zona waktu
* Kalender saat diklik
* Hari libur nasional

**System Monitor**

Widget yang menampilkan penggunaan sumber daya sistem secara real-time:

* Penggunaan CPU
* Penggunaan RAM
* Penggunaan jaringan
* Suhu perangkat keras
* Penggunaan disk

**Notes**

Widget catatan yang memungkinkan Anda mengetik langsung di desktop atau panel:

* Dukungan multi-halaman
* Format teks seperti bold, italic, dan bullet points
* Penyimpanan otomatis
* Sinkronisasi dengan aplikasi KNotes

**Weather**

Widget cuaca yang menampilkan:

* Suhu saat ini
* Prakiraan beberapa hari ke depan
* Kondisi cuaca
* Kecepatan dan arah angin
* Kelembapan

**Folder View**

Widget yang menampilkan isi folder di desktop atau panel:

* Menampilkan berkas dan folder dalam berbagai mode tampilan
* Mendukung drag-and-drop
* Ikon berkas berdasarkan jenis
* Menu konteks untuk operasi berkas

> **Catatan**
>
> Folder View di desktop secara default menampilkan isi folder `~/Desktop`. Namun, Anda dapat mengonfigurasinya untuk menampilkan folder lain, atau bahkan beberapa Folder View yang menampilkan folder berbeda.

#### 5.2.4 Mengonfigurasi Widget

{% stepper %}
{% step %}
### Buka konfigurasi widget

Klik kanan pada widget.
{% endstep %}

{% step %}
### Pilih Configure

Pilih **Configure \[Nama Widget]**.
{% endstep %}

{% step %}
### Ubah pengaturan

Dialog konfigurasi akan muncul dengan opsi yang tersedia. Ubah pengaturan sesuai keinginan.
{% endstep %}

{% step %}
### Terapkan perubahan

Klik **Apply** atau **OK**.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Konfigurasi widget disimpan dalam berkas:

`~/.config/plasma-org.kde.plasma.desktop-appletsrc`

Anda dapat mengedit berkas ini secara manual jika perlu, tetapi berhati-hatilah karena kesalahan dapat menyebabkan widget tidak berfungsi.
{% endhint %}

#### 5.2.5 Menghapus Widget

{% stepper %}
{% step %}
### Klik kanan pada widget
{% endstep %}

{% step %}
### Pilih Remove

Pilih **Remove \[Nama Widget]**.
{% endstep %}

{% step %}
### Konfirmasi penghapusan
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Menghapus widget tidak menghapus widget dari sistem, hanya dari desktop atau panel. Anda dapat menambahkannya kembali kapan saja melalui **Add Widgets**.
{% endhint %}


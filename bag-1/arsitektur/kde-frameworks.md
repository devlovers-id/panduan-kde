# KDE Frameworks

KDE Frameworks adalah kumpulan pustaka yang menyediakan fungsionalitas umum untuk aplikasi KDE dan pihak ketiga. Ia adalah salah satu kontribusi paling signifikan KDE untuk ekosistem open source.

#### 3.4.1 Gambaran Umum

KDE Frameworks terdiri dari lebih dari 80 pustaka yang dikelompokkan menjadi empat tingkatan berdasarkan dependensinya:

| Tier   | Deskripsi                | Contoh                                                     |
| ------ | ------------------------ | ---------------------------------------------------------- |
| Tier 4 | Solusi Siap Pakai        | KHtml, KTextEditor, KCalendarCore                          |
| Tier 3 | Integrasi Desktop        | Plasma (`libplasma`), KRunner, KNotifyConfig, KGlobalAccel |
| Tier 2 | Bergantung pada Tier 1   | KIO, KAuth, KPackage, KCMUtils                             |
| Tier 1 | Bergantung hanya pada Qt | KConfig, KWindowSystem, KCoreAddons, KI18n, Solid          |

_Gambar 3.4: Arsitektur berlapis KDE Frameworks. Setiap tier hanya bergantung pada tier di bawahnya, memastikan bahwa pustaka tingkat rendah dapat digunakan secara independen tanpa menarik dependensi yang tidak perlu._

#### 3.4.2 Pustaka-Pustaka Penting

**KConfig**

KConfig adalah sistem manajemen konfigurasi yang digunakan oleh hampir semua aplikasi KDE. Ia menyediakan:

* API C++ untuk membaca dan menulis konfigurasi.
* Format berkas INI yang dapat dibaca manusia.
* Dukungan untuk grup dan kunci bertingkat.
* Notifikasi perubahan untuk pemantauan waktu-nyata.
* Dukungan untuk notifikasi KDE (`KConfigWatcher`).

Contoh berkas konfigurasi KConfig:

```ini
[General]
ColorScheme=BreezeDark
LookAndFeelPackage=org.kde.breeze.desktop

[KDE]
AnimationDurationFactor=1.0
SingleClick=false

[Icons]
Theme=Papirus-Dark
```

**KIO**

KIO adalah pustaka yang menyediakan abstraksi I/O untuk akses berkas, jaringan, dan protokol lainnya. Ia memungkinkan aplikasi untuk mengakses berbagai sumber daya melalui API yang seragam.

**Protokol**

`file://`, `http://`, `ftp://`, `smb://`, `sftp://`, `mtp://`, dan banyak lagi.

**KIO Jobs**

Operasi asinkron untuk menyalin, memindahkan, menghapus, dan memanipulasi berkas.

**KIO Slaves**

Pekerja yang dijalankan di proses terpisah untuk protokol tertentu.

**KIO Widgets**

Komponen UI siap pakai untuk operasi I/O (_file dialog_, _progress bar_).

**KPackage**

KPackage adalah sistem paket yang digunakan untuk menginstal dan mengelola widget, tema, dan ekstensi lainnya. Ia menyediakan:

* Format paket terdefinisi dengan `metadata.json`.
* Instalasi dan penghapusan paket.
* Manajemen ketergantungan antara paket.
* Dukungan untuk berbagai jenis paket (Plasma Widget, Look and Feel, dan lainnya).

**KWindowSystem**

KWindowSystem menyediakan abstraksi untuk berinteraksi dengan manajer jendela dan sistem windowing:

* API untuk memanipulasi jendela (`minimize`, `maximize`, `close`).
* Deteksi perubahan tata letak layar.
* Integrasi dengan X11 dan Wayland.
* Manajemen virtual desktop.

**Solid**

Solid menyediakan abstraksi untuk perangkat keras:

* Deteksi perangkat keras (disk, jaringan, baterai, dan lainnya).
* Notifikasi perubahan status perangkat.
* API untuk manajemen daya.
* Integrasi dengan `udev` dan UPower.

#### 3.4.3 KDE Frameworks di Luar KDE

Salah satu keunggulan KDE Frameworks adalah dapat digunakan di luar ekosistem KDE. Aplikasi pihak ketiga seperti Krita, Kdenlive, dan bahkan beberapa aplikasi non-KDE menggunakan framework ini.

{% hint style="info" %}
**Catatan**

Karena KDE Frameworks dapat digunakan secara independen, aplikasi tidak perlu menginstal seluruh ekosistem KDE untuk menggunakan satu pustaka. Ini memudahkan integrasi dan mengurangi dependensi yang tidak perlu.
{% endhint %}


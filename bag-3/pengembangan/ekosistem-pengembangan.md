# Ekosistem Pengembangan KDE

Sebelum menyelami kode, penting untuk memahami ekosistem pengembangan KDE Plasma secara keseluruhan: alat apa yang tersedia, bahasa apa yang digunakan, dan bagaimana semuanya terhubung.

#### 7.1.1 Bahasa dan Teknologi

Pengembangan KDE Plasma melibatkan beberapa bahasa dan teknologi yang bekerja sama:

| Teknologi  | Kegunaan      | Contoh Penggunaan                  |
| ---------- | ------------- | ---------------------------------- |
| QML        | UI deklaratif | Widget, modul konfigurasi, panel   |
| JavaScript | Logika QML    | Handler, fungsi, animasi           |
| C++        | Logika berat  | Plugin QML, backend, KWin effects  |
| CMake      | Build system  | Konfigurasi proyek, instalasi      |
| Python     | Tooling       | Skrip build, generator, alat bantu |

_Tabel 7.1: Teknologi utama dalam pengembangan KDE Plasma. Sebagian besar pekerjaan UI dilakukan dalam QML, dengan C++ untuk logika yang membutuhkan performa._

{% hint style="info" %}
Untuk sebagian besar pengembangan widget, Anda hanya perlu QML dan JavaScript. C++ diperlukan hanya jika Anda perlu berinteraksi dengan pustaka sistem, mengakses perangkat keras, atau melakukan operasi yang membutuhkan performa tinggi.
{% endhint %}

#### 7.1.2 Alat Pengembangan

Berikut alat-alat yang perlu Anda siapkan untuk mengembangkan KDE Plasma:

| Alat                      | Deskripsi                                                      |
| ------------------------- | -------------------------------------------------------------- |
| KDevelop                  | IDE dari KDE dengan dukungan bawaan untuk QML, C++, dan CMake. |
| Qt Creator                | IDE resmi Qt, dengan dukungan QML yang sangat baik.            |
| Kate                      | Editor teks KDE dengan plugin untuk QML dan C++.               |
| plasmoidviewer            | Alat untuk menguji widget secara langsung tanpa instalasi.     |
| plasma-interactiveconsole | Konsol interaktif untuk bereksperimen dengan QML.              |
| kpackagetool6             | Alat untuk mengemas dan menginstal paket Plasma.               |
| git                       | Version control untuk mengelola kode sumber.                   |
| cmake                     | Build system generator.                                        |

#### 7.1.3 Struktur Komunitas Pengembangan

Komunitas pengembangan KDE terorganisir melalui beberapa platform:

* invent.kde.org: Repositori Git resmi untuk semua proyek KDE.
* develop.kde.org: Dokumentasi pengembangan resmi.
* techbase.kde.org: Wiki teknis untuk pengembang.
* Matrix: Platform obrolan utama untuk diskusi pengembangan.
* Mailing Lists: Diskusi melalui email untuk topik-topik tertentu.
* Phabricator: Pelacak tugas dan review kode.

{% hint style="info" %}
Jika Anda baru memulai, bergabunglah dengan kanal Matrix #plasma:kde.org atau #kde-devel:kde.org. Komunitas KDE sangat ramah terhadap pendatang baru, dan Anda akan mendapatkan bantuan dengan cepat.
{% endhint %}


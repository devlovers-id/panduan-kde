# Apa Itu KDE Plasma?

KDE Plasma adalah antarmuka pengguna inti untuk desktop yang dikembangkan oleh proyek KDE. Ia merupakan lingkungan desktop gratis untuk sistem operasi mirip Unix seperti Linux dan FreeBSD. Plasma pertama kali diperkenalkan pada tahun 2008 sebagai bagian dari KDE Software Compilation 4, menggantikan lingkungan desktop KDE 3 dengan konsep baru yang lebih fleksibel dan dapat diperluas.

{% hint style="info" %}
**Definisi**

KDE Plasma adalah desktop shell yang mengelola panel, widget, desktop, dan interaksi pengguna dalam ekosistem KDE. Ia bukan sekadar “desktop environment” dalam pengertian tradisional, melainkan sebuah platform yang dapat diperluas dengan widget, tema, dan modul konfigurasi.
{% endhint %}

#### 1.1.1 Shell, Workspace, dan Desktop Environment

Untuk memahami posisi KDE Plasma secara tepat, penting untuk membedakan tiga istilah yang sering digunakan secara bergantian namun memiliki makna teknis yang berbeda:

**Desktop Environment**

Keseluruhan lingkungan grafis yang mencakup shell, manajer jendela, panel, widget, aplikasi inti, dan integrasi sistem.

**Shell**

Lapisan antarmuka yang mengelola panel, widget, desktop, dan interaksi langsung dengan pengguna. Pada KDE Plasma, shell diimplementasikan oleh `plasmashell`.

**Workspace**

Kumpulan komponen yang membentuk ruang kerja, termasuk manajer jendela (KWin), manajemen daya, integrasi perangkat keras, dan layanan sistem lainnya.

Dalam arsitektur KDE Plasma, shell dan workspace dipisahkan secara jelas. Pemisahan ini memungkinkan KDE Plasma untuk berjalan di atas berbagai manajer jendela (meskipun KWin adalah default) dan memungkinkan komponen-komponennya dikembangkan secara independen oleh tim yang berbeda.

#### 1.1.2 Posisi dalam Tumpukan Perangkat Lunak

Secara vertikal, KDE Plasma berada di antara Qt (kerangka kerja aplikasi) dan aplikasi pengguna. Gambar [1.1](pendahuluan.md#4%5F1%5FPendahuluan) menunjukkan posisi ini secara skematis.

| Lapisan           | Komponen                            |
| ----------------- | ----------------------------------- |
| Lapisan pengguna  | Aplikasi KDE & Pihak Ketiga         |
| Shell & workspace | Plasma Shell (`plasmashell`)        |
|                   | KWin (Manajer Jendela & Kompositor) |
| Pustaka           | KDE Frameworks                      |
|                   | Qt 6                                |
| Sistem            | Kernel Linux / FreeBSD              |

_Gambar 1.1: Posisi KDE Plasma dalam tumpukan perangkat lunak. Setiap lapisan bergantung pada lapisan di bawahnya, namun antarmuka di antara lapisan-lapisan ini dirancang agar tetap stabil sehingga komponen dapat dikembangkan secara independen._

Gambar [1.1](pendahuluan.md#4%5F1%5FPendahuluan) menegaskan bahwa KDE Plasma bukanlah monolit. Ia adalah kumpulan lapisan yang saling bergantung melalui antarmuka yang terdefinisi dengan baik. Inilah yang memungkinkan KDE Plasma untuk terus berevolusi dari KDE 4 ke Plasma 5, dan dari Plasma 5 ke Plasma 6, tanpa harus menulis ulang seluruh sistem.

#### 1.1.3 Mengapa Namanya “Plasma”?

Nama “Plasma” dipilih pada tahun 2008 sebagai metafora untuk sifatnya yang cair dan dapat berubah bentuk. Seperti plasma dalam fisika yang dapat mengambil bentuk wadahnya, KDE Plasma dapat beradaptasi dengan berbagai faktor bentuk: desktop tradisional, tablet, perangkat layar sentuh, hingga pusat media. Filosofi ini tercermin dalam desainnya yang modular dan kemampuannya menyesuaikan tata letak berdasarkan ukuran layar dan perangkat masukan.

{% hint style="info" %}
**Catatan**

Meskipun nama “Plasma” terdengar futuristik, filosofinya sangat praktis: pengguna harus dapat membentuk lingkungan komputasi mereka sesuka hati. Inilah yang membedakan KDE Plasma dari lingkungan desktop yang lebih “opiniated” seperti GNOME.
{% endhint %}


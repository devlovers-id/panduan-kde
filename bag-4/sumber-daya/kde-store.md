# KDE Store

KDE Store (`store.kde.org`) adalah pusat distribusi untuk tema, widget, dan add-on pihak ketiga untuk KDE Plasma dan aplikasi KDE.

#### 10.4.1 Apa Itu KDE Store?

{% hint style="info" %}
**KDE Store** adalah platform online di mana pengembang dan desainer dapat membagikan kreasi mereka untuk KDE Plasma dan aplikasi KDE. Ia menyediakan akses ke ribuan tema, widget, ikon, dan add-on yang dibuat oleh komunitas.
{% endhint %}

{% hint style="info" %}
KDE Store tidak dimiliki atau dijalankan oleh KDE; ia adalah bagian dari proyek Open-Desktop. Namun, KDE menyediakan integrasi langsung dengan KDE Store melalui tombol “Get New...” di berbagai aplikasi.
{% endhint %}

#### 10.4.2 Kategori di KDE Store

| Kategori           | Deskripsi                                                  |
| ------------------ | ---------------------------------------------------------- |
| Global Themes      | Paket tema lengkap, Plasma Style, Ikon, Warna, dan lainnya |
| Plasma Style       | Gaya visual untuk panel dan widget                         |
| Color Schemes      | Skema warna untuk UI                                       |
| Icon Themes        | Kumpulan ikon untuk aplikasi dan berkas                    |
| Window Decorations | Dekorasi jendela untuk KWin                                |
| Widgets            | Widget untuk desktop dan panel                             |
| Splash Screens     | Layar splash saat login                                    |
| Wallpapers         | Gambar latar belakang                                      |

#### 10.4.3 Cara Mengakses KDE Store

Ada beberapa cara untuk mengakses KDE Store.

**Melalui System Settings**

{% stepper %}
{% step %}
### Buka System Settings Colors & Themes
{% endstep %}

{% step %}
### Pilih kategori yang diinginkan

Misalnya, Global Theme.
{% endstep %}

{% step %}
### Klik Get New... di bagian bawah
{% endstep %}

{% step %}
### Jelajahi KDE Store atau gunakan kotak pencarian
{% endstep %}

{% step %}
### Klik Install pada item yang diinginkan
{% endstep %}
{% endstepper %}

**Melalui Widget Browser**

{% stepper %}
{% step %}
### Klik kanan desktop atau panel
{% endstep %}

{% step %}
### Pilih Add Widgets
{% endstep %}

{% step %}
### Klik Get New Widgets... di bagian bawah
{% endstep %}

{% step %}
### Jelajahi atau cari widget yang diinginkan
{% endstep %}

{% step %}
### Klik Install
{% endstep %}
{% endstepper %}

**Melalui Situs Web**

Kunjungi langsung [https://store.kde.org/](https://store.kde.org/) untuk menjelajahi semua konten yang tersedia. Anda dapat mengunduh berkas secara manual dan menginstalnya melalui `kpackagetool6`.

#### 10.4.4 Widget Populer

Berikut beberapa widget populer yang tersedia di KDE Store:

* Better Inline Clock: Jam dengan tanggal dan cuaca inline.
* Modern Clock: Jam minimalis dan estetik.
* Plasma Panel Colorizer: Kustomisasi warna panel per-widget.
* Weather Widget: Prakiraan cuaca dengan ikon animasi.
* Netspeed: Pemantau kecepatan jaringan.
* Simple Menu: Peluncur aplikasi layar penuh.
* Window Title Applet: Menampilkan judul jendela di panel.

```bash
# Menginstal widget dari file lokal
kpackagetool6 --type Plasma/Applet --install /path/to/widget.tar.gz

# Menginstal dari KDE Store (memerlukan ID widget)
kpackagetool6 --type Plasma/Applet --install https://store.kde.org/p/1234567

# Melihat daftar widget yang terinstal
kpackagetool6 --type Plasma/Applet --list

# Menghapus widget
kpackagetool6 --type Plasma/Applet --remove com.example.widget
```


# Material You Colors

Material You Colors adalah generator skema warna otomatis yang menghasilkan tema terang dan gelap untuk KDE Plasma dari wallpaper saat ini, menggunakan implementasi Python dari Material Color Utilities Google.

#### 6.9.1 Apa Itu Material You?

> **Definisi**
>
> Material You adalah bahasa desain Google yang menghasilkan skema warna dinamis dari wallpaper pengguna. KDE Material You Colors adalah implementasi Python yang menerapkan prinsip ini ke KDE Plasma, menghasilkan skema warna yang harmonis secara otomatis.

#### 6.9.2 Fitur Material You Colors

* Plasma Widget untuk KDE Plasma 6 yang menampilkan kontrol Material You.
* Dukungan semua plugin wallpaper: warna, gambar, slideshow, dan animasi.
* Update otomatis saat wallpaper berubah.
* Tema Konsole yang dihasilkan.
* Dukungan Pywal untuk tema aplikasi lain.
* Dukungan untuk Light dan Dark mode.
* Konfigurasi melalui GUI atau berkas konfigurasi.

#### 6.9.3 Memasang Material You Colors

```bash
# Arch Linux (AUR)
yay -S kde-material-you-colors

# openSUSE (OBS)
sudo zypper addrepo https://download.opensuse.org/repositories/home:...
sudo zypper install kde-material-you-colors

# Fedora (Copr)
sudo dnf copr enable luisbocanegra/kde-material-you-colors
sudo dnf install kde-material-you-colors

# Instalasi melalui pipx (universal)
pipx install kde-material-you-colors

# Menjalankan backend
kde-material-you-colors
```

#### 6.9.4 Menggunakan Material You Colors

{% stepper %}
{% step %}
### Jalankan backend

Jalankan backend `kde-material-you-colors`.
{% endstep %}

{% step %}
### Tambahkan widget

Tambahkan widget Plasma You Colors ke panel atau desktop.
{% endstep %}

{% step %}
### Lihat warna yang dihasilkan

Widget akan menampilkan warna yang dihasilkan dari wallpaper saat ini.
{% endstep %}

{% step %}
### Atur opsi

Klik widget untuk mengakses opsi: mengubah wallpaper, mengubah mode light atau dark, dan mengonfigurasi preferensi.
{% endstep %}

{% step %}
### Terapkan skema otomatis

Skema warna akan otomatis diterapkan ke KDE Plasma dan aplikasi lain.
{% endstep %}
{% endstepper %}

> **Catatan**
>
> Material You Colors bekerja paling baik dengan wallpaper yang memiliki warna-warna kaya. Wallpaper monokrom mungkin menghasilkan skema warna yang kurang menarik.

#### 6.9.5 Konfigurasi Material You Colors

Berkas konfigurasi utama berada di `~/.config/kde-material-you-colors/config.conf`:

```ini
[General]
scheme = content
mode = dark
light_blend = false
dark_blend = true
pywal = true
konsole = true
pywal_theme = generated
pywal_light = false
wallpaper =
wallpaper_path = ~/Pictures/wallpaper.jpg
monitor = 0
changed_files =
reload_gtk_theme = true
reload_kde_theme = true

[Notification]
notify = true
notify_timeout = 3000

[KDE]
plasma_apply = true
plasma_reload = true
apply_aurorae = true
apply_icons = true
apply_cursors = true
apply_kvantum = true
```


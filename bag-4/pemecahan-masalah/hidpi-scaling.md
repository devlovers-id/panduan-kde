# HiDPI Scaling

Layar beresolusi tinggi (HiDPI) menawarkan tampilan yang lebih tajam, tetapi memerlukan konfigurasi scaling yang tepat.

#### 9.6.1 Konsep Dasar Scaling

Scaling di KDE Plasma dapat dilakukan dengan beberapa cara:

| Jenis               | Deskripsi                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------- |
| Integer Scaling     | Skala 1x, 2x, 3x. Paling sederhana dan paling kompatibel.                                 |
| Fractional Scaling  | Skala 1.25x, 1.5x, 1.75x. Lebih fleksibel, tetapi memerlukan Wayland untuk hasil terbaik. |
| Font Scaling        | Mengubah ukuran font secara terpisah dari elemen UI lainnya.                              |
| Application Scaling | Scaling per aplikasi.                                                                     |

#### 9.6.2 Mengatur Scaling di Wayland

Wayland mendukung fractional scaling dengan lebih baik daripada X11.

{% stepper %}
{% step %}
### Buka System Settings Display and Monitor Display Configuration
{% endstep %}

{% step %}
### Pilih monitor yang ingin diatur
{% endstep %}

{% step %}
### Atur Scale ke nilai yang diinginkan

Misalnya, `1.5`.
{% endstep %}

{% step %}
### Klik Apply
{% endstep %}

{% step %}
### Logout dan login kembali untuk menerapkan perubahan
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Fractional scaling di Wayland bekerja dengan merender pada resolusi tinggi dan kemudian downscaling. Ini menghasilkan tampilan yang lebih tajam dibanding integer scaling, tetapi memerlukan lebih banyak sumber daya GPU.
{% endhint %}

#### 9.6.3 Mengatur Scaling di X11

Di X11, scaling biasanya hanya bekerja dalam kelipatan integer. Namun, ada beberapa trik untuk mencapai scaling yang lebih halus.

```bash
# Atur DPI font
xrdb -merge <<< "Xft.dpi: 144"

# Atur scaling X11
xrandr --output HDMI-1 --scale 1.5x1.5

# Atur scaling untuk aplikasi GTK
gsettings set org.gnome.desktop.interface text-scaling-factor 1.5

# Atur scaling untuk aplikasi Qt
export QT_SCALE_FACTOR=1.5
export QT_AUTO_SCREEN_SCALE_FACTOR=1
```

#### 9.6.4 Masalah Scaling Umum

| Masalah                          | Solusi                                                   |
| -------------------------------- | -------------------------------------------------------- |
| Font terlalu kecil               | Atur font scaling di System Settings → Fonts             |
| Aplikasi tidak mengikuti scaling | Atur variabel lingkungan per aplikasi                    |
| Ikon blur                        | Gunakan ikon SVG atau tema ikon HiDPI                    |
| Kursor terlalu kecil             | Ubah ukuran kursor di System Settings → Cursors          |
| Aplikasi X11 blur                | Gunakan aplikasi Wayland native atau atur scaling khusus |

{% hint style="info" %}
Untuk aplikasi X11 yang tidak mengikuti scaling dengan baik, coba atur variabel lingkungan `QT_SCALE_FACTOR` atau `GDK_SCALE` sebelum menjalankan aplikasi. Ini dapat membantu aplikasi menyesuaikan ukuran UI mereka.
{% endhint %}


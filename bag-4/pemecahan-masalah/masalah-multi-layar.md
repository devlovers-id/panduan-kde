# Masalah Multi-Layar

Konfigurasi multi-layar adalah salah satu area yang paling sering menimbulkan masalah, terutama dengan monitor yang berbeda resolusi atau refresh rate.

#### 9.4.1 Monitor Tidak Terdeteksi

Jika monitor eksternal tidak terdeteksi, ada beberapa langkah diagnosis yang dapat dilakukan.

**Diagnosis**

```bash
# Lihat output display yang terdeteksi
kscreen-doctor -o

# Periksa apakah monitor terdeteksi oleh kernel
xrandr # Untuk X11
wlr-randr # Untuk Wayland (jika tersedia)

# Periksa koneksi fisik
ls /sys/class/drm/

# Lihat log KWin
journalctl --user -u plasma-kwin_wayland.service -b | grep -i "output\|monitor\|display"

# Lihat log kernel
dmesg | grep -i "drm\|hdmi\|displayport"
```

**Solusi**

1. Periksa koneksi fisik: Pastikan kabel terhubung dengan baik.
2. Coba port lain: Coba hubungkan ke port HDMI, DisplayPort, atau VGA yang berbeda.
3. Coba kabel lain: Kabel yang rusak dapat menyebabkan monitor tidak terdeteksi.
4. Perbarui driver: Driver GPU yang lama mungkin tidak mendukung monitor baru.
5. Uji di OS lain: Jika monitor berfungsi di OS lain, masalahnya terkait software.

#### 9.4.2 Resolusi atau Refresh Rate Salah

Setelah monitor terdeteksi, resolusi atau refresh rate mungkin tidak sesuai harapan.

```bash
# Lihat mode yang tersedia
kscreen-doctor -o

# Atur resolusi dan refresh rate untuk output tertentu
kscreen-doctor output.HDMI-1.mode.1920x1080@60

# Atur scaling
kscreen-doctor output.HDMI-1.scale.1.5

# Atur posisi
kscreen-doctor output.HDMI-1.position.0,0

# Menggunakan GUI
systemsettings5 kcm_kscreen # Plasma 5
systemsettings6 kcm_kscreen # Plasma 6
```

#### 9.4.3 Monitor Muncul di Posisi yang Salah

Jika monitor muncul di posisi yang salah di System Settings, Anda dapat mengaturnya dengan drag-and-drop.

{% stepper %}
{% step %}
### Buka System Settings Display and Monitor
{% endstep %}

{% step %}
### Seret monitor ke posisi yang benar relatif terhadap monitor lain
{% endstep %}

{% step %}
### Klik Apply
{% endstep %}
{% endstepper %}

#### 9.4.4 Panel Muncul di Monitor yang Salah

Jika panel muncul di monitor yang salah, Anda dapat memindahkannya:

{% stepper %}
{% step %}
### Klik kanan panel, pilih Edit Panel
{% endstep %}

{% step %}
### Seret panel ke monitor yang diinginkan
{% endstep %}

{% step %}
### Klik More Options untuk mengatur visibilitas per monitor
{% endstep %}

{% step %}
### Klik Exit Edit Mode
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Untuk menyimpan konfigurasi multi-layar yang berbeda, gunakan fitur KScreen di Plasma. Ini memungkinkan Anda menyimpan dan memuat profil untuk berbagai setup, misalnya kantor vs. rumah.
{% endhint %}

#### 9.4.5 HiDPI dan Fractional Scaling

Dengan monitor 4K atau resolusi tinggi, Anda mungkin perlu menerapkan scaling agar font dan jendela tidak terlalu kecil.

```bash
# Lihat konfigurasi scaling saat ini
kscreen-doctor -o

# Atur scaling untuk output tertentu
kscreen-doctor output.eDP-1.scale.1.5

# Scaling per monitor (Plasma 6.7+)
# Di System Settings -> Display and Monitor -> Scale Display
```

{% hint style="info" %}
Fractional scaling (misalnya, 1.25x, 1.5x) bekerja paling baik di Wayland. Di X11, scaling integer biasanya hanya dalam kelipatan (1x, 2x), kecuali menggunakan trik seperti mengubah DPI font.
{% endhint %}


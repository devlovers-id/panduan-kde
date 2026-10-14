# Masalah Umum

Bagian ini membahas masalah-masalah umum yang sering dihadapi pengguna KDE Plasma.

#### 9.2.1 Aplikasi Crash atau Menolak Diluncurkan

Ini adalah salah satu masalah paling umum. Aplikasi mungkin crash saat diluncurkan, saat melakukan tindakan tertentu, atau secara acak.

**Diagnosis**

{% stepper %}
{% step %}
### Periksa log aplikasi

Jalankan aplikasi dari terminal untuk melihat pesan error.
{% endstep %}

{% step %}
### Periksa crash

Gunakan `coredumpctl list` untuk melihat crash terbaru.
{% endstep %}

{% step %}
### Periksa dependensi

Gunakan `ldd` untuk memeriksa apakah semua dependensi terpenuhi.
{% endstep %}

{% step %}
### Uji dengan pengguna baru

Buat akun pengguna baru dan coba jalankan aplikasi. Jika berhasil, masalahnya terkait konfigurasi pengguna.
{% endstep %}
{% endstepper %}

```bash
# Jalankan aplikasi dari terminal
firefox

# Periksa crash terbaru
coredumpctl list

# Lihat detail crash
coredumpctl info firefox

# Periksa dependensi
ldd /usr/bin/firefox

# Periksa apakah ada lib yang hilang
ldd /usr/bin/firefox | grep "not found"

# Cek versi library
pacman -Qi firefox # Arch
apt list --installed | grep firefox # Ubuntu
dnf info firefox # Fedora
```

**Solusi Umum**

1. Perbarui sistem: Pastikan semua paket dalam versi terbaru.
2. Reset konfigurasi: Hapus atau ganti nama direktori konfigurasi aplikasi di `~/.config/`.
3. Instal dependensi: Instal paket yang hilang yang dilaporkan oleh `ldd`.
4. Coba pengguna baru: Jika berhasil, konfigurasi pengguna lama kemungkinan rusak.
5. Periksa log: Baca log untuk pesan error yang lebih spesifik.

{% hint style="warning" %}
Saat menghapus konfigurasi aplikasi, Anda akan kehilangan pengaturan, riwayat, dan data yang terkait. Selalu backup terlebih dahulu dengan mengganti nama direktori (`mv application application.backup`) daripada menghapusnya.
{% endhint %}

#### 9.2.2 Layar Menjadi Hitam atau Blank

Layar hitam adalah masalah yang menakutkan tetapi sering dapat diatasi dengan relatif mudah.

**Diagnosis**

{% stepper %}
{% step %}
### Beralih ke TTY lain

Gunakan `Ctrl + Alt + F2` hingga `F6`.
{% endstep %}

{% step %}
### Login sebagai pengguna Anda
{% endstep %}

{% step %}
### Periksa log KWin atau X11
{% endstep %}

{% step %}
### Periksa apakah ada proses yang menggunakan GPU secara intensif
{% endstep %}
{% endstepper %}

```bash
# Beralih ke TTY
Ctrl + Alt + F3

# Periksa log KWin
journalctl --user -u plasma-kwin_wayland.service -b

# Periksa penggunaan GPU
nvidia-smi # Untuk NVIDIA
radeontop # Untuk AMD
intel_gpu_top # Untuk Intel

# Periksa apakah ada proses yang crash
coredumpctl list

# Cek status display
kscreen-doctor -o
```

**Solusi**

1. Restart KWin: Jalankan `kwin_wayland –replace` dari TTY.
2. Reset konfigurasi KWin: Hapus `~/.config/kwinrc`.
3. Nonaktifkan efek: Matikan efek kompositing untuk melihat apakah itu penyebabnya.
4. Perbarui driver: Pastikan driver GPU dalam versi terbaru.
5. Gunakan `nomodeset`: Tambahkan `nomodeset` ke parameter kernel sebagai solusi sementara.

{% hint style="info" %}
Jika layar hitam terjadi setelah pembaruan, masalahnya kemungkinan terkait dengan driver grafis atau KWin. Baca catatan rilis pembaruan dan periksa forum untuk masalah serupa.
{% endhint %}

#### 9.2.3 Widget Tidak Muncul atau Tidak Berfungsi

Widget adalah salah satu fitur khas KDE Plasma, tetapi kadang-kadang mereka tidak muncul atau tidak berfungsi dengan baik.

**Diagnosis**

{% stepper %}
{% step %}
### Periksa apakah widget terinstal dengan benar
{% endstep %}

{% step %}
### Periksa apakah widget kompatibel dengan versi Plasma Anda
{% endstep %}

{% step %}
### Periksa log Plasma untuk pesan error QML
{% endstep %}

{% step %}
### Coba hapus dan tambahkan kembali widget
{% endstep %}
{% endstepper %}

```bash
# Lihat daftar widget yang terinstal
kpackagetool6 --type Plasma/Applet --list

# Periksa apakah widget ada di direktori yang benar
ls ~/.local/share/plasma/plasmoids/
ls /usr/share/plasma/plasmoids/

# Lihat log Plasma untuk error QML
journalctl --user -u plasma-plasmashell.service -b | grep -i "qml\|widget\|error"

# Restart Plasma Shell
kquitapp6 plasmashell && kstart plasmashell
```

**Solusi**

1. Reset konfigurasi widget: Hapus `~/.config/plasma-org.kde.plasma.desktop-appletsrc`.
2. Hapus cache Plasma: Hapus `~/.cache/plasma*`.
3. Instal ulang widget: Hapus dan instal ulang widget yang bermasalah.
4. Periksa kompatibilitas: Pastikan widget kompatibel dengan versi Plasma Anda.

```bash
# Backup konfigurasi widget
cp ~/.config/plasma-org.kde.plasma.desktop-appletsrc ~/plasma-appletsrc.backup

# Hapus cache
rm -rf ~/.cache/plasma*

# Restart Plasma Shell
kquitapp6 plasmashell && kstart plasmashell

# Jika masih bermasalah, reset total
rm ~/.config/plasma-org.kde.plasma.desktop-appletsrc
kquitapp6 plasmashell && kstart plasmashell
```

{% hint style="info" %}
Menghapus `plasma-org.kde.plasma.desktop-appletsrc` akan mereset semua tata letak panel dan widget ke default. Semua widget kustom yang telah Anda tambahkan akan hilang.
{% endhint %}

#### 9.2.4 Efek Desktop Tidak Berfungsi

Efek desktop seperti blur, cube, dan wobbly windows adalah salah satu fitur yang paling menarik di KDE Plasma, tetapi kadang-kadang mereka tidak berfungsi.

**Diagnosis**

{% stepper %}
{% step %}
### Periksa apakah kompositing diaktifkan
{% endstep %}

{% step %}
### Periksa apakah driver GPU mendukung efek yang diinginkan
{% endstep %}

{% step %}
### Periksa apakah efek diaktifkan di pengaturan KWin
{% endstep %}

{% step %}
### Periksa apakah ada konflik dengan efek lain
{% endstep %}
{% endstepper %}

```bash
# Periksa apakah kompositing aktif
qdbus org.kde.KWin /Compositor active

# Lihat daftar efek
qdbus org.kde.KWin /Effects loadedEffects

# Periksa log KWin
journalctl --user -u plasma-kwin_wayland.service -b | grep -i "effect\|composit"

# Test efek
qdbus org.kde.KWin /Effects org.kde.kwin.Effects.loadEffect blur
```

**Solusi**

1. Aktifkan kompositing: Pastikan kompositing diaktifkan di System Settings Display and Monitor Compositor.
2. Ubah backend rendering: Coba ganti antara OpenGL 2.0, OpenGL 3.1, dan XRender.
3. Nonaktifkan efek yang tidak kompatibel: Beberapa efek tidak berfungsi dengan driver tertentu.
4. Perbarui driver GPU: Driver lama mungkin tidak mendukung semua efek.

{% hint style="info" %}
Jika efek blur tidak berfungsi, periksa apakah blur diaktifkan di System Settings Workspace Behavior Desktop Effects. Beberapa efek mungkin dinonaktifkan secara default untuk menghemat sumber daya.
{% endhint %}

#### 9.2.5 Kinerja Lambat

Kinerja lambat adalah keluhan umum, terutama pada perangkat keras yang lebih lama.

**Diagnosis**

{% stepper %}
{% step %}
### Periksa penggunaan CPU dan RAM

Gunakan `htop` atau `top`.
{% endstep %}

{% step %}
### Periksa penggunaan GPU

Gunakan `nvidia-smi` untuk NVIDIA atau `radeontop` untuk AMD.
{% endstep %}

{% step %}
### Periksa suhu

Gunakan `sensors`.
{% endstep %}

{% step %}
### Periksa proses yang memakan sumber daya
{% endstep %}
{% endstepper %}

```bash
# Monitor proses
htop

# Monitor GPU
nvidia-smi -l 2
radeontop

# Monitor suhu
sensors

# Periksa proses yang memakan CPU
ps aux --sort=-%cpu | head -10

# Periksa proses yang memakan RAM
ps aux --sort=-%mem | head -10

# Periksa penggunaan disk
iostat -x 1
```

**Solusi**

1. Aktifkan Mode Sumber Daya Rendah: Di System Settings Workspace Behavior General Behavior, aktifkan Low Resource Mode.
2. Nonaktifkan efek berat: Blur, cube, dan animasi kompleks memakan banyak sumber daya.
3. Gunakan tema ringan: Beberapa tema lebih berat dari yang lain.
4. Kurangi jumlah widget: Widget yang berjalan terus-menerus dapat memakan sumber daya.
5. Perbarui sistem: Pembaruan sering membawa peningkatan kinerja.
6. Periksa suhu: Overheating dapat menyebabkan throttling.

| Masalah Kinerja | Kemungkinan Penyebab dan Solusi                                    |
| --------------- | ------------------------------------------------------------------ |
| CPU tinggi      | Widget pemantauan, efek kompositing, proses zombie                 |
| RAM tinggi      | Kebocoran memori, terlalu banyak aplikasi, cache tidak dibersihkan |
| GPU tinggi      | Efek kompositing, game, rendering                                  |
| Disk lambat     | Swap, disk penuh, SMART error                                      |
| Suhu tinggi     | Debu pada kipas, thermal paste kering, TDP terlalu tinggi          |


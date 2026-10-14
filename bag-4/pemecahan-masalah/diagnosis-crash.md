# Studi Kasus: Diagnosis Crash Plasma

Untuk mengilustrasikan metodologi pemecahan masalah, mari kita telusuri studi kasus nyata: Plasma crash setelah pembaruan.

#### 9.7.1 Skenario

Seorang pengguna melaporkan bahwa setelah pembaruan ke Plasma 6.7, Plasma Shell crash berulang kali. Desktop muncul selama beberapa detik, kemudian hilang, dan pengguna kembali ke layar login.

#### 9.7.2 Langkah 1: Reproduksi Masalah

Pengguna dapat mereproduksi masalah dengan login kembali. Setiap kali login, Plasma crash dalam 5–10 detik.

#### 9.7.3 Langkah 2: Kumpulkan Informasi

```bash
# Beralih ke TTY
Ctrl + Alt + F3

# Login

# Periksa crash terbaru
coredumpctl list

# Lihat detail crash
coredumpctl info plasmashell

# Periksa log Plasma
journalctl --user -u plasma-plasmashell.service -b

# Periksa versi Plasma
plasmashell --version
plasmashell --version # Plasma 6.7.0

# Periksa versi Qt
qmake6 --version

# Periksa versi KDE Frameworks
kf6-config --version
```

#### 9.7.4 Langkah 3: Analisis Log

Dari log, pengguna menemukan pesan error berikut:

```
plasmashell[1234]: kf.plasma.quick: Applet "com.example.mywidget" crashed
plasmashell[1234]: kf.plasma.quick: Attempting to recover applet
plasmashell[1234]: qml: TypeError: Cannot read property 'foo' of undefined
plasmashell[1234]: kf.plasma.quick: Applet "com.example.mywidget" crashed again
plasmashell[1234]: kf.plasma.quick: Giving up on applet
plasmashell[1234]: Segmentation fault
```

#### 9.7.5 Langkah 4: Isolasi Masalah

Dari log, jelas bahwa widget kustom `com.example.mywidget` menyebabkan crash. Widget ini adalah widget pihak ketiga yang belum diperbarui untuk Plasma 6.7.

#### 9.7.6 Langkah 5: Solusi

```bash
# Hapus widget yang bermasalah
kpackagetool6 --type Plasma/Applet --remove com.example.mywidget

# Restart Plasma
kquitapp6 plasmashell && kstart plasmashell

# Atau, reset konfigurasi widget
mv ~/.config/plasma-org.kde.plasma.desktop-appletsrc ~/plasma-appletsrc.backup
kquitapp6 plasmashell && kstart plasmashell
```

#### 9.7.7 Langkah 6: Verifikasi

Setelah menghapus widget yang bermasalah, Plasma Shell berjalan stabil. Pengguna kemudian melaporkan bug ke pengembang widget melalui pelacak bug mereka.

#### 9.7.8 Pelajaran

1. Widget pihak ketiga adalah sumber crash yang umum: Widget yang belum diperbarui untuk versi Plasma baru dapat menyebabkan masalah.
2. Log adalah kunci diagnosis: Pesan error di log menunjukkan dengan tepat apa yang menyebabkan crash.
3. Isolasi masalah adalah penting: Dengan mengidentifikasi widget yang bermasalah, pengguna dapat menyelesaikan masalah dengan cepat.
4. Laporkan bug: Setelah masalah teratasi, laporkan ke pengembang widget sehingga mereka dapat memperbaikinya.

{% hint style="info" %}
Selalu gunakan widget dari KDE Store yang aktif dipelihara. Periksa tanggal pembaruan terakhir dan ulasan pengguna sebelum menginstal widget pihak ketiga.
{% endhint %}

#### 9.7.9 Studi Kasus 2: Plasma Tidak Muncul Setelah Pembaruan

**Skenario**

Seorang pengguna memperbarui sistem, dan setelah reboot, login berhasil tetapi desktop KDE Plasma tidak muncul. Hanya layar hitam dengan kursor.

**Diagnosis**

```bash
# Beralih ke TTY
Ctrl + Alt + F3

# Login

# Periksa apakah plasmashell berjalan
ps aux | grep plasmashell

# Periksa log
journalctl --user -b | tail -50

# Coba jalankan Plasma secara manual
dbus-run-session startplasma-wayland 2>&1 | tee ~/plasma-manual.log

# Periksa error di log manual
cat ~/plasma-manual.log
```

**Solusi**

Dari log, pengguna menemukan bahwa plasmashell tidak dapat memuat plugin QML karena konflik versi. Solusinya adalah menghapus cache QML dan restart:

```bash
# Hapus cache QML
rm -rf ~/.cache/qmlcache/
rm -rf ~/.cache/plasmashell/

# Restart Plasma
kquitapp6 plasmashell && kstart plasmashell

# Jika masih bermasalah, reset konfigurasi Plasma
mv ~/.config/plasma* ~/plasma-backup/
kquitapp6 plasmashell && kstart plasmashell
```


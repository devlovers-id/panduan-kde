# Masalah Login

Masalah login adalah salah satu masalah paling frustasi karena menghalangi akses ke sistem. Bagian ini membahas berbagai masalah login dan solusinya.

#### 9.3.1 Login Berhasil tetapi Desktop Tidak Muncul

Ini adalah masalah yang cukup umum di mana pengguna dapat login, tetapi desktop KDE Plasma tidak muncul.

**Diagnosis**

{% stepper %}
{% step %}
### Beralih ke TTY lain
{% endstep %}

{% step %}
### Login sebagai pengguna Anda
{% endstep %}

{% step %}
### Periksa log Plasma dan KWin
{% endstep %}

{% step %}
### Periksa apakah ada proses yang crash
{% endstep %}
{% endstepper %}

```bash
# Beralih ke TTY
Ctrl + Alt + F3

# Periksa log Plasma
journalctl --user -b | tail -50

# Periksa log session
journalctl --user -u plasma-plasmashell.service -b

# Periksa status session
systemctl --user status plasma-plasmashell.service

# Coba jalankan Plasma secara manual
dbus-run-session startplasma-wayland
```

**Solusi**

1. Reset konfigurasi Plasma: Hapus `~/.config/plasma*`.
2. Reset cache: Hapus `~/.cache/*`.
3. Periksa izin: Pastikan direktori home Anda memiliki izin yang benar.
4. Uji dengan pengguna baru: Jika berhasil, konfigurasi pengguna lama rusak.
5. Periksa driver GPU: Pastikan driver GPU berfungsi.

```bash
# Backup konfigurasi lama
mkdir ~/plasma-backup
cp -r ~/.config/plasma* ~/plasma-backup/
cp -r ~/.config/kdeglobals ~/plasma-backup/

# Hapus cache
rm -rf ~/.cache/*

# Hapus konfigurasi Plasma
rm -rf ~/.config/plasma*

# Restart display manager
sudo systemctl restart sddm # atau plasmalogin

# Login kembali
```

{% hint style="warning" %}
Menghapus `~/.config/plasma*` akan menghapus semua konfigurasi Plasma Anda, termasuk tata letak panel, widget, dan pengaturan. Ini adalah solusi terakhir setelah metode lain gagal.
{% endhint %}

#### 9.3.2 Login Gagal dengan Pesan Error

Kadang-kadang login gagal dengan pesan error seperti “Authentication failure” atau “Session failed”.

**Diagnosis**

```bash
# Periksa log SDDM
journalctl -u sddm.service -b

# Atau untuk Plasma Login Manager
journalctl -u plasmalogin.service -b

# Periksa log PAM
journalctl -t pam_unix -b

# Periksa izin home
ls -la ~

# Periksa apakah akun terkunci
sudo passwd -S $USER
```

**Solusi**

1. Reset password: Gunakan `passwd` dari TTY untuk reset password.
2. Perbaiki izin home: Pastikan `~` dimiliki oleh pengguna, bukan root.
3. Periksa PAM: Pastikan konfigurasi PAM benar.
4. Periksa sistem file: Pastikan partisi home tidak penuh.

```bash
# Periksa izin home
ls -la /home/

# Perbaiki izin jika perlu
sudo chown -R $USER:$USER /home/$USER
sudo chmod 755 /home/$USER

# Reset password jika perlu
sudo passwd $USER

# Periksa disk space
df -h /home
```

#### 9.3.3 Autologin Tidak Berfungsi

Autologin adalah fitur yang memungkinkan login otomatis tanpa memasukkan password. Jika tidak berfungsi, ada beberapa kemungkinan penyebab.

```ini
# Edit /etc/sddm.conf atau /etc/sddm.conf.d/autologin.conf

[Autologin]
User=namapengguna
Session=plasma
Relogin=true

# Atau untuk Plasma Login Manager
# Edit /etc/plasmalogin.conf
```

{% hint style="info" %}
Beberapa distribusi memerlukan konfigurasi tambahan untuk autologin, seperti mengaktifkan layanan tertentu atau menonaktifkan kunci layar. Konsultasikan dokumentasi distribusi Anda.
{% endhint %}


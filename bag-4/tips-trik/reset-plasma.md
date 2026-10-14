# Reset Plasma ke Default

Ketika KDE Plasma mengalami masalah yang sulit dipecahkan, atau ketika Anda ingin memulai dari awal, reset ke pengaturan default adalah solusi yang efektif.

#### 11.3.1 Reset Selektif

Reset selektif melibatkan penghapusan atau penggantian nama berkas konfigurasi tertentu, memungkinkan Plasma untuk membuat yang baru dengan pengaturan default.

```bash
# 1. Backup konfigurasi lama terlebih dahulu
mkdir -p ~/plasma-backup
cp -r ~/.config/plasma* ~/plasma-backup/ 2>/dev/null
cp ~/.config/kdeglobals ~/plasma-backup/ 2>/dev/null
cp ~/.config/kwinrc ~/plasma-backup/ 2>/dev/null

# 2. Hapus atau ganti nama berkas konfigurasi tertentu
# Reset tata letak widget dan panel
mv ~/.config/plasma-org.kde.plasma.desktop-appletsrc ~/plasma-backup/

# Reset pengaturan Plasma Shell
mv ~/.config/plasmashellrc ~/plasma-backup/

# Reset pengaturan KWin
mv ~/.config/kwinrc ~/plasma-backup/

# Reset pengaturan global KDE (tema, ikon, font)
mv ~/.config/kdeglobals ~/plasma-backup/

# 3. Hapus cache Plasma
rm -rf ~/.cache/plasma*
rm -rf ~/.cache/qmlcache/
rm -rf ~/.cache/plasmashell/

# 4. Restart Plasma Shell
kquitapp6 plasmashell && kstart plasmashell

# 5. Jika perlu, logout dan login kembali
```

#### 11.3.2 Reset Total dengan Skrip

Untuk reset yang lebih menyeluruh, Anda dapat menggunakan skrip yang menghapus semua konfigurasi terkait KDE. Proyek seperti kde-reset menyediakan skrip untuk tujuan ini.

```bash
#!/bin/bash
# kde-reset: Reset semua konfigurasi dan cache KDE

BACKUP_DIR="$HOME/kde-reset-backup-$(date +%Y%m%d-%H%M%S)"
mkdir -p "$BACKUP_DIR"

echo "Backup ke: $BACKUP_DIR"

# Backup dan hapus konfigurasi KDE
for item in ~/.config/plasma* ~/.config/kde* ~/.config/kwin* \
  ~/.config/khotkeys* ~/.config/kglobalshortcuts* \
  ~/.config/krunner* ~/.config/ksmserver*; do
  if [ -e "$item" ]; then
    cp -r "$item" "$BACKUP_DIR/"
    rm -rf "$item"
  fi
done

# Hapus cache
rm -rf ~/.cache/plasma*
rm -rf ~/.cache/qmlcache/
rm -rf ~/.cache/plasmashell/

echo "Reset selesai. Silakan logout dan login kembali."
```

#### 11.3.3 Reset melalui System Settings

Plasma 6 menyediakan modul reset pabrik di System Settings. Fitur ini memungkinkan pengguna untuk mereset perangkat ke pengaturan default.

{% stepper %}
{% step %}
### Buka System Settings
{% endstep %}

{% step %}
### Navigasi ke Plasma Settings atau About System
{% endstep %}

{% step %}
### Cari opsi Reset to default settings atau Factory Reset
{% endstep %}

{% step %}
### Pilih pengguna yang ingin direset

Biasanya “Last logged-in user”.
{% endstep %}

{% step %}
### Klik Apply
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Reset pabrik akan menghapus semua konfigurasi pribadi Anda, termasuk tema, widget, pintasan, dan pengaturan panel. Pastikan Anda telah mem-backup semua yang penting sebelum melanjutkan. Setelah reset, Anda perlu me-restart sistem atau logout dan login kembali.
{% endhint %}

#### 11.3.4 Setelah Reset

Setelah reset, Anda akan memiliki KDE Plasma dengan pengaturan default. Anda dapat:

* Mengimpor kembali pengaturan dari backup jika diinginkan.
* Membangun konfigurasi baru dari awal.
* Menginstal ulang tema dan widget yang Anda gunakan sebelumnya.

{% hint style="info" %}
Jika Anda sering melakukan reset, pertimbangkan untuk membuat skrip yang secara otomatis mem-backup konfigurasi Anda sebelum reset. Ini akan menghemat waktu dan memastikan Anda tidak kehilangan pengaturan penting.
{% endhint %}


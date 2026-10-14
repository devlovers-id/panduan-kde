# Konfigurasi melalui CLI

Meskipun KDE Plasma menyediakan antarmuka grafis yang kaya untuk konfigurasi, ada kalanya bekerja melalui command line lebih efisien, terutama untuk otomasi dan manajemen jarak jauh.

#### 11.2.1 Kwriteconfig: Menulis Konfigurasi

`kwriteconfig6` adalah alat command line untuk menulis nilai ke berkas konfigurasi KDE. Ia sangat berguna untuk mengubah pengaturan tanpa membuka System Settings.

```bash
# Sintaks dasar
kwriteconfig6 --file <file> --group <group> --key <key> <value>

# Contoh: Mengubah tema Plasma
kwriteconfig6 --file kdeglobals --group KDE --key LookAndFeelPackage org.kde.breeze.desktop

# Contoh: Mengubah skema warna
kwriteconfig6 --file kdeglobals --group General --key ColorScheme BreezeDark

# Contoh: Mengaktifkan borderless maximized windows di KWin
kwriteconfig6 --file kwinrc --group Windows --key BorderlessMaximizedWindows true

# Contoh: Menghapus kunci
kwriteconfig6 --file kwinrc --group Windows --key BorderlessMaximizedWindows --delete

# Contoh: Mengubah konfigurasi keyboard
kwriteconfig6 --file kxkbrc --group Layout --key Options "caps:backspace"
```

{% hint style="info" %}
Untuk Plasma 6, gunakan `kwriteconfig6`. Untuk Plasma 5, gunakan `kwriteconfig5`. Di beberapa distribusi, `kwriteconfig` adalah symlink ke versi yang sesuai.
{% endhint %}

#### 11.2.2 Kreadconfig: Membaca Konfigurasi

`kreadconfig6` adalah alat untuk membaca nilai dari berkas konfigurasi KDE.

```bash
# Membaca nilai kunci
kreadconfig6 --file kdeglobals --group General --key ColorScheme

# Membaca dengan nilai default jika kunci tidak ada
kreadconfig6 --file kdeglobals --group General --key NonExistent --default "default_value"

# Melihat semua kunci dalam sebuah grup
kreadconfig6 --file kdeglobals --group General --list
```

#### 11.2.3 Plasma-Apply: Mengubah Tema

`plasma-apply` adalah kumpulan skrip untuk mengubah berbagai aspek tema Plasma melalui command line.

```bash
# Mengubah skema warna
plasma-apply-colorscheme BreezeDark

# Melihat daftar skema warna yang tersedia
plasma-apply-colorscheme --list-schemes

# Mengubah wallpaper
plasma-apply-wallpaperimage /path/to/wallpaper.jpg

# Mengubah tema desktop (Plasma Style)
plasma-apply-desktoptheme default

# Mengubah tema global (Look and Feel)
plasma-apply-lookandfeel --apply org.kde.breezedark.desktop

# Melihat daftar tema global yang tersedia
plasma-apply-lookandfeel --list

# Mengubah tema ikon
plasma-apply-icontheme Papirus-Dark
```

#### 11.2.4 Menerapkan Perubahan

Setelah mengubah konfigurasi melalui `kwriteconfig`, beberapa pengaturan mungkin memerlukan restart layanan atau signal D-Bus untuk diterapkan.

```bash
# Restart Plasma Shell (untuk perubahan tampilan)
kquitapp6 plasmashell && kstart plasmashell

# Restart KWin (untuk perubahan window manager)
kwin_wayland --replace

# Mengirim sinyal D-Bus untuk reload konfigurasi keyboard
dbus-send --session --type=signal --reply-timeout=100 \
  --dest=org.kde.keyboard /Layouts org.kde.keyboard.reloadConfig

# Reload konfigurasi KWin
qdbus org.kde.KWin /KWin reconfigure
```

{% hint style="info" %}
Untuk mengotomasi konfigurasi sistem, Anda dapat menulis skrip yang menggunakan `kwriteconfig6` untuk mengatur banyak pengaturan sekaligus, lalu menerapkannya dengan restart layanan yang sesuai. Ini sangat berguna untuk deployment di banyak mesin.
{% endhint %}


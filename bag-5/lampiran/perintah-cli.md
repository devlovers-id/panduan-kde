# Perintah CLI Penting

Lampiran ini menyediakan daftar perintah command line yang sering digunakan dalam pengelolaan KDE Plasma. Perintah-perintah ini berguna untuk otomasi, pemecahan masalah, dan konfigurasi lanjutan.

#### Manajemen Plasma

```bash
# Restart Plasma Shell
kquitapp6 plasmashell && kstart plasmashell

# Restart KWin
kwin_wayland --replace

# Menjalankan Plasma secara manual
dbus-run-session startplasma-wayland
dbus-launch --exit-with-x11 startplasma-x11

# Melihat versi Plasma
plasmashell --version

# Melihat versi KWin
kwin_wayland --version
```

#### Manajemen Tema

```bash
# Mengubah skema warna
plasma-apply-colorscheme BreezeDark

# Melihat daftar skema warna
plasma-apply-colorscheme --list-schemes

# Mengubah wallpaper
plasma-apply-wallpaperimage /path/to/wallpaper.jpg

# Mengubah Plasma Style
plasma-apply-desktoptheme default

# Mengubah tema global
plasma-apply-lookandfeel --apply org.kde.breeze.desktop

# Mengubah tema ikon
plasma-apply-icontheme Papirus-Dark
```

#### Manajemen Widget

```bash
# Melihat daftar widget yang terinstal
kpackagetool6 --type Plasma/Applet --list

# Menginstal widget
kpackagetool6 --type Plasma/Applet --install /path/to/widget

# Menghapus widget
kpackagetool6 --type Plasma/Applet --remove com.example.widget

# Menguji widget dengan plasmoidviewer
plasmoidviewer -a package
```

#### Manajemen Konfigurasi

```bash
# Membaca konfigurasi
kreadconfig6 --file kdeglobals --group General --key ColorScheme

# Menulis konfigurasi
kwriteconfig6 --file kdeglobals --group General --key ColorScheme BreezeDark

# Menghapus kunci
kwriteconfig6 --file kdeglobals --group General --key ColorScheme --delete

# Melihat daftar kunci dalam grup
kreadconfig6 --file kdeglobals --group General --list
```

#### Diagnostik

```bash
# Melihat log Plasma
journalctl --user -u plasma-plasmashell.service -b

# Melihat log KWin
journalctl --user -u plasma-kwin_wayland.service -b

# Melihat crash terbaru
coredumpctl list

# Melihat detail crash
coredumpctl info <PID>

# Melihat informasi display
kscreen-doctor -o

# Melihat status kompositing
qdbus org.kde.KWin /Compositor active

# Melihat daftar efek
qdbus org.kde.KWin /Effects loadedEffects
```


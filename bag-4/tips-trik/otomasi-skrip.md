# Otomasi dengan Skrip

Otomasi adalah kunci untuk produktivitas. Dengan skrip yang tepat, Anda dapat mengotomasi tugas-tugas rutin seperti mengubah tema berdasarkan waktu, mengatur wallpaper, atau mengonfigurasi sistem secara otomatis.

#### 11.5.1 Skrip Beralih Tema Otomatis

Salah satu otomasi yang paling populer adalah beralih antara tema terang dan gelap berdasarkan waktu.

```bash
#!/bin/bash
# auto-theme-switch: Beralih tema berdasarkan waktu

HOUR=$(date +%H)

# Tema gelap dari jam 18:00 hingga 06:00
if [ "$HOUR" -ge 18 ] || [ "$HOUR" -lt 6 ]; then
  plasma-apply-colorscheme BreezeDark
  plasma-apply-lookandfeel --apply org.kde.breezedark.desktop
  echo "Tema gelap diterapkan"
else
  plasma-apply-colorscheme BreezeLight
  plasma-apply-lookandfeel --apply org.kde.breeze.desktop
  echo "Tema terang diterapkan"
fi
```

Anda dapat menjalankan skrip ini melalui cron atau systemd timer.

```bash
# Buat file layanan systemd user
mkdir -p ~/.config/systemd/user/

cat > ~/.config/systemd/user/auto-theme.service << EOF
[Unit]
Description=Auto theme switch

[Service]
Type=oneshot
ExecStart=/home/$USER/scripts/auto-theme-switch.sh
EOF

cat > ~/.config/systemd/user/auto-theme.timer << EOF
[Unit]
Description=Run auto theme switch daily

[Timer]
OnCalendar=*-*-* 06:00:00
OnCalendar=*-*-* 18:00:00
Persistent=true

[Install]
WantedBy=timers.target
EOF

# Aktifkan timer
systemctl --user enable --now auto-theme.timer

# Periksa status
systemctl --user list-timers
```

#### 11.5.2 Skrip Wallpaper Rotasi

Skrip untuk merotasi wallpaper secara otomatis dari direktori gambar:

```bash
#!/bin/bash
# wallpaper-rotate: Merotasi wallpaper dari direktori

WALLPAPER_DIR="$HOME/Pictures/Wallpapers"
INTERVAL=300 # detik

while true; do
  # Pilih gambar acak
  WALLPAPER=$(find "$WALLPAPER_DIR" -type f \( -name "*.jpg" -o -name "*.png" \) | shuf -n 1)

  if [ -n "$WALLPAPER" ]; then
    plasma-apply-wallpaperimage "$WALLPAPER"
    echo "Wallpaper diubah: $WALLPAPER"
  fi

  sleep $INTERVAL
done
```

#### 11.5.3 Skrip Konfigurasi Multi-Mesin

Untuk administrator sistem yang mengelola banyak mesin, skrip konfigurasi dapat menghemat waktu:

```bash
#!/bin/bash
# deploy-plasma-config: Mengonfigurasi Plasma secara otomatis

# Set tema
kwriteconfig6 --file kdeglobals --group KDE --key LookAndFeelPackage org.kde.breeze.desktop

# Set skema warna
kwriteconfig6 --file kdeglobals --group General --key ColorScheme BreezeDark

# Set tema ikon
kwriteconfig6 --file kdeglobals --group Icons --key Theme Papirus-Dark

# Set font
kwriteconfig6 --file kdeglobals --group General --key font "Noto Sans,10,-1,5,50,0,0,0,0,0"

# Set pintasan keyboard
kwriteconfig6 --file kglobalshortcutsrc --group krunner --key "_launch" "Alt+Space"

# Konfigurasi KWin
kwriteconfig6 --file kwinrc --group Windows --key BorderlessMaximizedWindows true
kwriteconfig6 --file kwinrc --group Compositing --key Enabled true

# Terapkan perubahan
qdbus org.kde.KWin /KWin reconfigure
kquitapp6 plasmashell && kstart plasmashell

echo "Konfigurasi Plasma diterapkan."
```

#### 11.5.4 KWin Scripting

KWin mendukung scripting dengan JavaScript dan QML. Ini memungkinkan otomasi manajemen jendela yang lebih canggih.

```javascript
// Contoh KWin script: Memindahkan jendela baru ke desktop saat ini
// Simpan sebagai ~/.local/share/kwin/scripts/my-script/contents/code/main.js

function moveToCurrentDesktop(window) {
  if (window.normalWindow) {
    window.desktops = [workspace.currentDesktop];
  }
}

workspace.windowAdded.connect(moveToCurrentWindow);
```

Anda dapat menguji KWin script melalui Plasma Desktop Scripting Console yang dapat dibuka melalui KRunner (`Alt + F2`).

#### 11.5.5 Otomasi dengan Lunar Plasma

Lunar Plasma adalah antarmuka scripting Lua untuk desktop KDE Plasma. Ia memungkinkan kontrol programmatic atas berbagai aspek desktop.

```lua
-- Contoh Lunar Plasma script
local plasma = dofile(os.getenv("HOME").."/.local/opt/lunar-plasma/lunar-plasma.lua")

-- Set volume output default ke 50%
plasma.volume.set(50)

-- Kirim notifikasi desktop
plasma.notification.send({
  title = "Lunar Plasma",
  body = "Otomasi berjalan dengan sukses"
})
```

{% hint style="info" %}
Lunar Plasma adalah proyek pihak ketiga dan mungkin tidak tersedia di semua distribusi. Periksa repositori GitHub-nya untuk informasi instalasi terbaru.
{% endhint %}

#### 11.5.6 Contoh: Skrip Reset + Backup Otomatis

Skrip yang menggabungkan reset dan backup otomatis:

```bash
#!/bin/bash
# reset-with-backup: Reset Plasma dengan backup otomatis

BACKUP_DIR="$HOME/plasma-reset-backup-$(date +%Y%m%d-%H%M%S)"
mkdir -p "$BACKUP_DIR"

echo "=== Backup konfigurasi ke $BACKUP_DIR ==="

# Backup semua konfigurasi Plasma
for item in ~/.config/plasma* ~/.config/kdeglobals ~/.config/kwinrc \
  ~/.config/kglobalshortcutsrc; do
  if [ -e "$item" ]; then
    cp -r "$item" "$BACKUP_DIR/"
  fi
done

# Backup data pengguna
cp -r ~/.local/share/plasma/ "$BACKUP_DIR/" 2>/dev/null
cp -r ~/.local/share/color-schemes/ "$BACKUP_DIR/" 2>/dev/null

echo "=== Menghapus konfigurasi ==="

# Hapus konfigurasi
rm -rf ~/.config/plasma*
rm -f ~/.config/kdeglobals
rm -f ~/.config/kwinrc
rm -f ~/.config/kglobalshortcutsrc

# Hapus cache
rm -rf ~/.cache/plasma*
rm -rf ~/.cache/qmlcache/

echo "=== Restart Plasma Shell ==="
kquitapp6 plasmashell && kstart plasmashell

echo "Reset selesai. Backup tersimpan di: $BACKUP_DIR"
```


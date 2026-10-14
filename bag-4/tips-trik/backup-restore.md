# Backup dan Restore Konfigurasi

Backup konfigurasi KDE Plasma sangat penting, terutama sebelum melakukan pembaruan besar, menginstal tema baru, atau melakukan reset.

#### 11.4.1 Lokasi Konfigurasi Penting

Berikut lokasi berkas konfigurasi dan data yang perlu di-backup:

| Lokasi                                              | Konten                   |
| --------------------------------------------------- | ------------------------ |
| `~/.config/plasma*`                                 | Konfigurasi Plasma Shell |
| `~/.config/kdeglobals`                              | Pengaturan global KDE    |
| `~/.config/kwinrc`                                  | Konfigurasi KWin         |
| `~/.config/kglobalshortcutsrc`                      | Pintasan keyboard global |
| `~/.config/plasma-org.kde.plasma.desktop-appletsrc` | Tata letak widget        |
| `~/.local/share/plasma/`                            | Widget dan tema pengguna |
| `~/.local/share/color-schemes/`                     | Skema warna kustom       |
| `~/.local/share/icons/`                             | Tema ikon kustom         |

#### 11.4.2 Backup Manual

```bash
# Buat direktori backup
mkdir -p ~/plasma-config-backup

# Backup konfigurasi utama
cp -r ~/.config/plasma* ~/plasma-config-backup/
cp ~/.config/kdeglobals ~/plasma-config-backup/
cp ~/.config/kwinrc ~/plasma-config-backup/
cp ~/.config/kglobalshortcutsrc ~/plasma-config-backup/

# Backup data pengguna
cp -r ~/.local/share/plasma/ ~/plasma-config-backup/
cp -r ~/.local/share/color-schemes/ ~/plasma-config-backup/
cp -r ~/.local/share/icons/ ~/plasma-config-backup/

# Buat arsip tar
tar -czvf ~/plasma-backup-$(date +%Y%m%d).tar.gz -C ~ plasma-config-backup
```

#### 11.4.3 Restore Konfigurasi

```bash
# Ekstrak arsip backup
tar -xzvf ~/plasma-backup-20261012.tar.gz -C ~

# Salin kembali konfigurasi
cp -r ~/plasma-config-backup/plasma* ~/.config/
cp ~/plasma-config-backup/kdeglobals ~/.config/
cp ~/plasma-config-backup/kwinrc ~/.config/
cp ~/plasma-config-backup/kglobalshortcutsrc ~/.config/

# Salin kembali data pengguna
cp -r ~/plasma-config-backup/plasma/ ~/.local/share/
cp -r ~/plasma-config-backup/color-schemes/ ~/.local/share/
cp -r ~/plasma-config-backup/icons/ ~/.local/share/

# Restart Plasma
kquitapp6 plasmashell && kstart plasmashell
```

#### 11.4.4 Alat Backup Khusus

Beberapa alat dapat membantu mem-backup dan me-restore konfigurasi KDE Plasma:

| Alat                                    | Kegunaan                                                                                      |
| --------------------------------------- | --------------------------------------------------------------------------------------------- |
| PlasmaSafe                              | Alat command line untuk backup, restore, diff, verify, export, dan import konfigurasi Plasma. |
| Konsave                                 | Alat untuk menyimpan dan memuat konfigurasi Plasma, termasuk tema, widget, dan pengaturan.    |
| ArchLinux-KDE-Backup-and-Restore-Script | Skrip backup dan restore lengkap untuk Arch Linux dengan KDE Plasma.                          |

```bash
# Backup konfigurasi
plasmasafe backup mysnapshot

# Restore konfigurasi
plasmasafe restore mysnapshot

# Verifikasi snapshot
plasmasafe verify mysnapshot

# Melihat perbedaan
plasmasafe diff mysnapshot
```

{% hint style="info" %}
Lakukan backup konfigurasi secara teratur, terutama sebelum melakukan perubahan besar seperti pembaruan Plasma, menginstal tema baru, atau mengubah konfigurasi multi-layar. Simpan backup di lokasi yang aman, seperti drive eksternal atau cloud storage.
{% endhint %}


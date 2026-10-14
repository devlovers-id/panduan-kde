# Sumber Daya Pemecahan Masalah

Ketika Anda tidak dapat menyelesaikan masalah sendiri, ada banyak sumber daya yang dapat membantu.

#### 9.8.1 Dokumentasi Resmi

* `community.kde.org/Troubleshooting` — Wiki pemecahan masalah resmi KDE.
* `userbase.kde.org` — Wiki komunitas dengan panduan dan solusi.
* `docs.kde.org` — Dokumentasi resmi untuk semua aplikasi KDE.

#### 9.8.2 Forum dan Komunitas

* KDE Discuss: [https://discuss.kde.org/](https://discuss.kde.org/) — Forum diskusi resmi.
* Reddit r/kde — Subreddit untuk pengguna KDE.
* Matrix: `#plasma:kde.org` — Obrolan langsung.
* IRC `#kde` di Libera Chat.

#### 9.8.3 Pelacak Bug

* Bugs KDE: [https://bugs.kde.org/](https://bugs.kde.org/) — Pelacak bug resmi.
* Launchpad — Untuk bug di Ubuntu dan turunannya.
* Fedora Bugzilla — Untuk bug di Fedora.
* Arch Bug Tracker — Untuk bug di Arch Linux.

#### 9.8.4 Melaporkan Bug yang Baik

{% stepper %}
{% step %}
### Periksa apakah bug sudah dilaporkan

Cari di pelacak bug sebelum melaporkan.
{% endstep %}

{% step %}
### Gunakan judul yang deskriptif

Jelaskan masalah dengan singkat.
{% endstep %}

{% step %}
### Sertakan informasi sistem

Versi Plasma, Qt, KDE Frameworks, distribusi, dan driver GPU.
{% endstep %}

{% step %}
### Jelaskan langkah reproduksi

Bagaimana cara mereproduksi masalah?
{% endstep %}

{% step %}
### Sertakan log

Log yang relevan sangat membantu.
{% endstep %}

{% step %}
### Jelaskan perilaku yang diharapkan vs. aktual
{% endstep %}

{% step %}
### Sertakan screenshot atau video jika perlu
{% endstep %}

{% step %}
### Bersikap sopan dan sabar

Pengembang adalah sukarelawan.
{% endstep %}
{% endstepper %}

```bash
# Versi Plasma
plasmashell --version
kwin_wayland --version

# Versi Qt
qmake6 --version

# Versi KDE Frameworks
kf6-config --version

# Informasi sistem
uname -a
cat /etc/os-release

# Informasi GPU
lspci | grep -i vga
glxinfo | grep "OpenGL version"

# Log yang relevan
journalctl --user -b > ~/plasma-log.txt
coredumpctl info > ~/crash-info.txt

# Ringkas semua informasi
echo "=== System Info ===" > ~/bug-report.txt
cat /etc/os-release >> ~/bug-report.txt
plasmashell --version >> ~/bug-report.txt
qmake6 --version >> ~/bug-report.txt
kf6-config --version >> ~/bug-report.txt
uname -a >> ~/bug-report.txt
```

{% hint style="info" %}
Gunakan KDE Bug Report Tool, jika tersedia, untuk mengumpulkan informasi sistem secara otomatis. Alat ini dapat diakses melalui System Settings About System Report Bug.
{% endhint %}

#### 9.8.5 Alat Bantu Pemecahan Masalah

| Alat             | Kegunaan                             |
| ---------------- | ------------------------------------ |
| `kdebugsettings` | Mengaktifkan logging debug untuk KDE |
| `qdbus`          | Berinteraksi dengan layanan D-Bus    |
| `journalctl`     | Membaca log systemd                  |
| `dmesg`          | Membaca log kernel                   |
| `coredumpctl`    | Melihat dan menganalisis core dump   |
| `strace`         | Melacak system call                  |
| `ltrace`         | Melacak library call                 |
| `valgrind`       | Menganalisis memori                  |
| `gdb`            | Debugger                             |

#### 9.8.6 Mengaktifkan Logging Debug

Untuk masalah yang sulit, Anda mungkin perlu mengaktifkan logging debug:

```bash
# Aktifkan logging debug untuk Plasma
kdebugsettings

# Atau melalui command line
kwriteconfig6 --file kdebugrc --group plasma --key debug true

# Aktifkan logging untuk KWin
qdbus org.kde.KWin /KWin org.kde.KWin.setDebugLogging true

# Restart Plasma
kquitapp6 plasmashell && kstart plasmashell

# Lihat log
journalctl --user -f | grep -i "plasma\|kwin"
```

{% hint style="warning" %}
Logging debug menghasilkan log yang sangat besar dan dapat memperlambat sistem. Aktifkan hanya saat mendiagnosis masalah, dan nonaktifkan setelah selesai.
{% endhint %}


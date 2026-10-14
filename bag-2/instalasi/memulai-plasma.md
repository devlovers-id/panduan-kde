# Memulai Plasma

Setelah instalasi selesai, langkah selanjutnya adalah memulai sesi KDE Plasma. Ada beberapa cara untuk melakukannya, tergantung pada konfigurasi sistem Anda.

#### 4.3.1 Melalui Display Manager

Cara yang paling umum dan disarankan untuk memulai KDE Plasma adalah melalui display manager. Display manager adalah program yang menampilkan layar login grafis dan memungkinkan pengguna memilih sesi desktop.

**SDDM**

SDDM adalah display manager default untuk KDE Plasma. Ia menyediakan layar login yang dapat dikustomisasi dan mendukung berbagai sesi desktop.

Untuk mengonfigurasi SDDM, edit berkas `/etc/sddm.conf` atau letakkan berkas konfigurasi di `/etc/sddm.conf.d/`:

```ini
[Autologin]
User=
Session=plasma

[Theme]
Current=breeze
CursorTheme=breeze_cursors

[Users]
MaximumUid=60000
MinimumUid=1000

[Wayland]
EnableHiDPI=true
SessionDir=/usr/share/wayland-sessions
```

**Display Manager Lain**

Selain SDDM, ada beberapa display manager lain yang dapat digunakan dengan KDE Plasma:

| Display manager | Deskripsi                                                                   |
| --------------- | --------------------------------------------------------------------------- |
| GDM             | Display manager default GNOME. Dapat digunakan untuk memulai sesi Plasma.   |
| LightDM         | Display manager ringan yang mendukung berbagai sesi.                        |
| LXDM            | Display manager ringan dari proyek LXDE.                                    |
| greetd          | Display manager minimalis yang dapat dikonfigurasi dengan berbagai greeter. |

#### 4.3.2 Memulai Plasma Secara Manual

Jika Anda tidak menggunakan display manager, Anda dapat memulai KDE Plasma secara manual dari terminal. Ini berguna untuk sistem minimal atau untuk tujuan debugging.

**Untuk Sesi X11**

Tambahkan baris berikut ke `~/.xinitrc`:

```bash
exec dbus-launch --exit-with-x11 ck-launch-session startplasma-x11
```

Kemudian jalankan:

```bash
startx
```

**Untuk Sesi Wayland**

Untuk memulai sesi Wayland secara manual:

```bash
# Pastikan Anda berada di TTY (bukan di dalam sesi grafis)
# Login sebagai pengguna biasa (bukan root)
dbus-run-session startplasma-wayland
```

{% hint style="warning" %}
Jangan pernah menjalankan Plasma sebagai root. Ini tidak hanya tidak aman, tetapi juga dapat menyebabkan masalah izin pada berkas konfigurasi. Selalu jalankan Plasma sebagai pengguna biasa.
{% endhint %}

#### 4.3.3 Konfigurasi Awal

Setelah login pertama kali, Anda akan disambut oleh wizard konfigurasi awal KDE Plasma.

Wizard ini membantu Anda mengatur preferensi dasar seperti:

* Bahasa dan wilayah
* Tata letak keyboard
* Zona waktu
* Koneksi jaringan
* Tema awal

{% hint style="info" %}
Jika Anda melewatkan wizard konfigurasi awal, Anda dapat mengaksesnya kembali melalui **System Settings → Startup and Shutdown → Plasma Initial Setup**.
{% endhint %}


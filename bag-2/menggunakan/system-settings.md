# System Settings

System Settings adalah pusat konfigurasi untuk KDE Plasma. Di sini Anda dapat mengatur hampir semua aspek desktop, dari tema hingga pengaturan sistem yang lebih mendalam.

#### 5.5.1 Struktur System Settings

System Settings diorganisasi ke dalam beberapa kategori utama:

| Kategori           | Contoh modul                                                                                        |
| ------------------ | --------------------------------------------------------------------------------------------------- |
| Appearance         | Global Theme, Plasma Style, Colors, Icons, Cursors, Window Decorations, Fonts, Splash Screen        |
| Workspace Behavior | Activities, Virtual Desktops, Screen Edges, Desktop, General Behavior                               |
| Window Management  | Task Switcher, Window Rules, KWin Scripts, Window Behavior, Desktop Effects                         |
| Shortcuts          | Custom Shortcuts, Global Shortcuts, Standard Shortcuts, Web Shortcuts, KHotKeys                     |
| Hardware           | Input Devices, Display and Monitor, Audio, Bluetooth, Power Management, Printers, Removable Storage |
| Network            | Connections, Settings, Sharing                                                                      |
| System             | Users, Startup and Shutdown, System Information, Date and Time, Language, Regional Settings         |

#### 5.5.2 Kategori Utama

**Appearance**

Kategori ini mencakup semua pengaturan visual:

* **Global Theme:** Mengubah tema keseluruhan, termasuk Plasma Style, Colors, Icons, Cursors, Window Decorations, Splash Screen, dan SDDM.
* **Plasma Style:** Gaya visual panel dan widget.
* **Colors:** Skema warna antarmuka.
* **Icons:** Tema ikon sistem.
* **Cursors:** Kursor mouse.
* **Window Decorations:** Dekorasi jendela, termasuk judul, tombol, dan border.
* **Fonts:** Font sistem untuk berbagai elemen UI.
* **Splash Screen:** Layar splash saat login.

**Workspace Behavior**

Kategori ini mencakup pengaturan perilaku workspace:

* **Activities:** Membuat dan mengelola Activities.
* **Virtual Desktops:** Mengatur jumlah dan nama virtual desktop.
* **Screen Edges:** Aksi saat kursor menyentuh tepi layar.
* **Desktop:** Pengaturan desktop, termasuk klik dan drag.
* **General Behavior:** Pengaturan umum seperti double-click atau single-click.

**Window Management**

Kategori ini mencakup pengaturan manajemen jendela:

* **Task Switcher:** Cara beralih antar jendela dengan `Alt + Tab`.
* **Window Rules:** Aturan khusus untuk jendela tertentu.
* **KWin Scripts:** Skrip yang mengubah perilaku KWin.
* **Window Behavior:** Pengaturan fokus, snapping, dan lainnya.
* **Virtual Desktops:** Pengaturan desktop virtual.
* **Desktop Effects:** Efek visual seperti blur, cube, dan wobbly windows.

**Shortcuts**

Kategori ini mencakup pintasan keyboard dan mouse:

* **Custom Shortcuts:** Pintasan kustom untuk menjalankan perintah.
* **Global Shortcuts:** Pintasan global untuk aplikasi.
* **Standard Shortcuts:** Pintasan standar seperti `Ctrl+C` dan `Ctrl+V`.
* **Web Shortcuts:** Kata kunci untuk pencarian web di KRunner.
* **KHotKeys:** Pintasan untuk skrip KHotKeys.

**Hardware**

Kategori ini mencakup pengaturan perangkat keras:

* **Input Devices:** Keyboard, mouse, touchpad, dan joystick.
* **Display and Monitor:** Resolusi, refresh rate, scaling, dan multi-monitor.
* **Audio:** Volume, perangkat output atau input, dan efek suara.
* **Bluetooth:** Perangkat Bluetooth.
* **Power Management:** Pengaturan daya untuk laptop.
* **Printers:** Manajemen printer.
* **Removable Storage:** Perilaku saat mencolokkan perangkat.

**Network**

Kategori ini mencakup pengaturan jaringan:

* **Connections:** Manajemen koneksi Wi-Fi, Ethernet, dan VPN.
* **Settings:** Pengaturan proxy, DNS, dan lainnya.
* **Sharing:** Berbagi berkas dan printer.

**System**

Kategori ini mencakup pengaturan sistem:

* **Users:** Manajemen pengguna.
* **Startup and Shutdown:** Aplikasi autostart, splash screen, dan SDDM.
* **System Information:** Informasi sistem.
* **Date and Time:** Tanggal, waktu, dan zona waktu.
* **Language:** Bahasa dan format regional.
* **Regional Settings:** Format angka, tanggal, dan mata uang.

{% hint style="info" %}
System Settings memiliki fitur pencarian. Ketik kata kunci di kotak pencarian di bagian atas untuk menemukan modul konfigurasi yang diinginkan dengan cepat. Ini sangat berguna jika Anda tidak yakin di kategori mana pengaturan tertentu berada.
{% endhint %}

#### 5.5.3 Menggunakan System Settings

System Settings menggunakan pendekatan berbasis modul. Setiap modul konfigurasi disebut KCM, atau KDE Configuration Module.

| Jenis KCM   | Deskripsi                                                      |
| ----------- | -------------------------------------------------------------- |
| KCM QML     | Modul yang dibangun dengan QML dan Kirigami.                   |
| KCM C++     | Modul tradisional yang dibangun dengan C++ dan Qt Widgets.     |
| KCM KConfig | Modul yang membaca dan menulis langsung ke berkas konfigurasi. |

> **Catatan**
>
> Banyak pengaturan System Settings juga dapat diakses melalui command line menggunakan `kwriteconfig6` dan `kreadconfig6`. Ini berguna untuk otomasi atau jika Anda lebih suka bekerja di terminal.


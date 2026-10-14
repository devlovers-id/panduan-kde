# Elemen Antarmuka

Desktop KDE Plasma default terdiri dari beberapa elemen yang bekerja sama untuk menciptakan pengalaman pengguna yang koheren. Memahami setiap elemen adalah langkah pertama untuk menguasai KDE Plasma.

#### 5.1.1 Anatomi Desktop

Desktop KDE Plasma default terdiri dari:

**Wallpaper**

Gambar latar belakang desktop. Dapat berupa gambar statis, slideshow, atau animasi.

**Panel**

Bilah horizontal atau vertikal yang biasanya berada di bagian bawah. Berisi widget dan peluncur aplikasi.

**Widget**

Elemen interaktif yang dapat ditempatkan di desktop atau panel. Contoh: jam, catatan, pemantau sistem.

**Desktop**

Area utama tempat widget dan ikon berkas dapat ditempatkan.

#### 5.1.2 Panel

Panel adalah salah satu elemen paling penting di KDE Plasma. Ia berfungsi sebagai “pusat komando” untuk sebagian besar interaksi pengguna.

**Komponen Panel Default**

Panel bawah default KDE Plasma terdiri dari:

1. **Application Launcher:** Ikon “K” di paling kiri yang membuka menu aplikasi.
2. **Task Manager:** Menampilkan jendela yang sedang berjalan, memungkinkan beralih antar jendela.
3. **Desktop Pager:** Menampilkan virtual desktop dan memungkinkan berpindah antar desktop.
4. **System Tray:** Area notifikasi dan status sistem. Berisi ikon seperti jaringan, volume, baterai, dan jam.
5. **Digital Clock:** Menampilkan waktu dan tanggal.
6. **Show Desktop:** Meminimalkan semua jendela untuk menampilkan desktop.

**Mengedit Panel**

{% stepper %}
{% step %}
### Masuk ke mode edit

Klik kanan pada panel di area kosong, lalu pilih **Enter Edit Mode**.
{% endstep %}

{% step %}
### Ubah panel

Panel akan menampilkan tombol untuk menambah widget, mengubah ukuran, dan mengubah posisi.
{% endstep %}

{% step %}
### Pindahkan atau ubah ukuran panel

Untuk memindahkan panel, seret ke tepi layar lain. Untuk mengubah ukuran, seret tepi panel.
{% endstep %}

{% step %}
### Buka opsi tambahan

Klik **More Options** untuk pengaturan tambahan: posisi, tinggi, alignment, dan visibilitas.
{% endstep %}

{% step %}
### Keluar dari mode edit

Klik **Exit Edit Mode** setelah selesai.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Untuk menambahkan panel baru, misalnya panel vertikal di sisi kiri untuk peluncur aplikasi, klik kanan desktop, pilih **Add Panel → Empty Panel**, lalu konfigurasi sesuai keinginan.
{% endhint %}

#### 5.1.3 Application Launcher

Application Launcher adalah cara utama untuk mengakses aplikasi di KDE Plasma. Ada beberapa varian yang dapat dipilih:

| Varian                | Deskripsi                                                                                                       |
| --------------------- | --------------------------------------------------------------------------------------------------------------- |
| Kickoff               | Menu klasik dengan kategori Favorit, Aplikasi, Komputer, Riwayat, dan Keluar. Ini adalah default di KDE Plasma. |
| Kicker                | Menu sederhana dengan daftar aplikasi.                                                                          |
| Application Dashboard | Tampilan layar penuh dengan ikon besar, mirip dengan menu Start Windows 8.                                      |
| Application Menu      | Menu gaya macOS yang terintegrasi dengan panel.                                                                 |

#### 5.1.4 Task Manager

Task Manager adalah widget yang menampilkan jendela aplikasi yang sedang berjalan. Ia memiliki beberapa mode tampilan:

| Mode           | Deskripsi                                                         |
| -------------- | ----------------------------------------------------------------- |
| Icons Only     | Menampilkan hanya ikon aplikasi. Ini adalah default di Plasma 5+. |
| Text Only      | Menampilkan judul jendela tanpa ikon.                             |
| Icons and Text | Menampilkan ikon dan judul jendela.                               |

Task Manager juga mendukung fitur-fitur berikut:

* **Grouping:** Mengelompokkan jendela dari aplikasi yang sama.
* **Sorting:** Mengurutkan jendela berdasarkan nama, waktu, atau posisi.
* **Highlighting:** Menyorot jendela yang meminta perhatian.
* **Middle-click actions:** Aksi khusus dengan klik tengah, misalnya membuka jendela baru.

#### 5.1.5 System Tray

System Tray adalah area di panel yang menampilkan ikon status sistem dan notifikasi. Ikon default meliputi:

* **Network Manager:** Status koneksi jaringan, seperti Wi-Fi, Ethernet, dan VPN.
* **Volume:** Kontrol volume audio.
* **Battery:** Status baterai pada laptop.
* **Bluetooth:** Status dan kontrol perangkat Bluetooth.
* **Clipboard:** Riwayat clipboard.
* **Notifications:** Notifikasi aplikasi.
* **Digital Clock:** Waktu dan tanggal.

{% hint style="info" %}
Anda dapat menambahkan atau menghapus ikon di System Tray dengan mengklik kanan ikon tersebut dan memilih **Configure System Tray**. Di sini Anda dapat mengatur ikon mana yang selalu ditampilkan, disembunyikan, atau dihapus.
{% endhint %}

#### 5.1.6 Desktop

Desktop adalah area utama tempat widget dan ikon berkas dapat ditempatkan. Secara default, KDE Plasma menampilkan desktop dengan Folder View, yang memungkinkan Anda menempatkan berkas dan folder langsung di desktop.

**Widget Desktop Default**

Desktop default KDE Plasma menyertakan beberapa widget:

* **Folder View:** Menampilkan konten folder `~/Desktop`.
* **Notes:** Catatan tempel yang dapat diketik langsung di desktop.
* **Digital Clock:** Jam digital yang dapat ditempatkan di desktop.

**Mengedit Desktop**

{% stepper %}
{% step %}
### Masuk ke mode edit

Klik kanan pada desktop di area kosong, lalu pilih **Enter Edit Mode**.
{% endstep %}

{% step %}
### Tambahkan atau ubah elemen

Anda dapat menambah widget, mengubah wallpaper, dan mengubah tata letak.
{% endstep %}

{% step %}
### Tambahkan widget

Klik **Add Widgets** untuk menambah widget baru.
{% endstep %}

{% step %}
### Keluar dari mode edit

Klik **Exit Edit Mode** setelah selesai.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Jika Anda tidak sengaja mengubah desktop dan ingin mengembalikannya ke default, Anda dapat menggunakan **System Settings → Workspace Behavior → Desktop → Reset to Default**. Namun, ini akan menghapus semua widget kustom yang telah Anda tambahkan.
{% endhint %}


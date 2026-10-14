# Studi Kasus: Migrasi dari Desktop Lain

Banyak pengguna yang beralih ke KDE Plasma dari lingkungan desktop lain seperti GNOME, Windows, atau macOS. Bagian ini menyajikan studi kasus migrasi dari berbagai lingkungan.

#### 4.5.1 Migrasi dari GNOME

GNOME dan KDE Plasma memiliki filosofi yang berbeda, sehingga migrasi memerlukan penyesuaian.

{% stepper %}
{% step %}
### Backup data

Pastikan semua berkas penting telah di-backup.
{% endstep %}

{% step %}
### Instal KDE Plasma

Ikuti panduan instalasi untuk distribusi Anda.
{% endstep %}

{% step %}
### Pilih sesi Plasma di layar login

Setelah instalasi, restart dan pilih sesi Plasma.
{% endstep %}

{% step %}
### Impor pengaturan GNOME

Beberapa pengaturan dapat diimpor, tetapi tidak semuanya. Anda mungkin perlu mengatur ulang preferensi seperti wallpaper, pintasan keyboard, dan tema.
{% endstep %}

{% step %}
### Instal aplikasi KDE

Ganti aplikasi GNOME dengan padanan KDE, misalnya Nautilus → Dolphin dan Gedit → Kate.
{% endstep %}

{% step %}
### Sesuaikan Plasma

Kustomisasi Plasma sesuai preferensi Anda.
{% endstep %}
{% endstepper %}

> **Catatan**
>
> Anda tidak perlu menghapus GNOME setelah menginstal KDE Plasma. Keduanya dapat hidup berdampingan, dan Anda dapat memilih sesi yang diinginkan di layar login. Namun, beberapa aplikasi mungkin muncul dua kali di menu, sekali untuk versi GNOME dan sekali untuk versi KDE.

#### 4.5.2 Migrasi dari Windows

Bagi pengguna yang beralih dari Windows, KDE Plasma menawarkan pengalaman yang familier dengan panel di bawah dan menu aplikasi di kiri.

**Gunakan Tata Letak “Windows-like”**

Ubah tata letak panel agar mirip dengan taskbar Windows. Klik kanan panel, pilih **Edit Panel**, lalu seret panel ke bawah dan tambahkan widget yang diinginkan.

**Pintasan Keyboard**

Sesuaikan pintasan keyboard agar mirip dengan Windows. Misalnya, `Super` untuk membuka menu aplikasi dan `Alt + Tab` untuk beralih jendela.

**Gunakan Aplikasi yang Familier**

Banyak aplikasi Windows memiliki padanan di Linux: Firefox, Chrome, LibreOffice, GIMP, VLC, dan lainnya.

**Wine untuk Aplikasi Windows**

Jika Anda memerlukan aplikasi Windows tertentu, gunakan Wine atau Proton untuk menjalankannya di Linux.

#### 4.5.3 Migrasi dari macOS

Pengguna macOS yang beralih ke KDE Plasma mungkin menginginkan pengalaman yang mirip dengan macOS. Berikut tipsnya:

* **Panel di atas:** Pindahkan panel ke atas layar dengan mengedit panel.
* **Global menu:** Aktifkan global menu di **System Settings → Window Management → Global Menu**.
* **Dock:** Gunakan widget “Application Dashboard” atau “Latte Dock” untuk pengalaman dock seperti macOS.
* **Pintasan keyboard:** Sesuaikan pintasan agar mirip dengan macOS, misalnya `Cmd` digantikan dengan `Super`.
* **Tema:** Gunakan tema seperti “WhiteSur” yang meniru tampilan macOS.

{% hint style="info" %}
Tema “WhiteSur” adalah salah satu tema populer yang meniru tampilan macOS. Ia mencakup Plasma Style, skema warna, tema ikon, dan dekorasi jendela yang semuanya dirancang untuk meniru macOS.
{% endhint %}

#### 4.5.4 Checklist Migrasi

* [ ] Backup data penting
* [ ] Periksa persyaratan sistem
* [ ] Instal paket Plasma
* [ ] Instal aplikasi KDE
* [ ] Impor pengaturan dari desktop lama
* [ ] Sesuaikan tata letak panel
* [ ] Atur pintasan keyboard
* [ ] Terapkan tema dan ikon
* [ ] Konfigurasi koneksi jaringan
* [ ] Uji aplikasi penting
* [ ] Dokumentasikan pengaturan


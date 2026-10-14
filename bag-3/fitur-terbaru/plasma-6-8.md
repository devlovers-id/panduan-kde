# Plasma 6.8 (Oktober 2026)

Plasma 6.8 dijadwalkan rilis pada 20 Oktober 2026. Rilis ini menandai tonggak penting dalam sejarah KDE Plasma: penghapusan sesi X11 dan pengenalan beberapa modul baru yang signifikan.

#### 8.3.1 Penghapusan Sesi X11

Plasma 6.8 adalah rilis pertama yang tidak menyertakan sesi X11 untuk login. Pengguna hanya dapat login ke sesi Wayland. Namun, dukungan XWayland tetap ada, sehingga aplikasi X11 masih dapat berjalan.

{% hint style="warning" %}
Jika Anda masih bergantung pada sesi X11, Anda harus tetap menggunakan Plasma 6.7, yang merupakan rilis terakhir dengan dukungan X11. Pastikan untuk menguji aplikasi dan alur kerja Anda di Wayland sebelum beralih ke Plasma 6.8.
{% endhint %}

Keputusan ini diambil setelah data internal KDE menunjukkan bahwa lebih dari 95% pengguna Plasma 6.6 sudah menggunakan Wayland, dan “praktis tidak ada yang menguji atau mengembangkan Plasma di X11 lagi”. Dengan menghapus X11, pengembang dapat fokus pada satu jalur kode, yang akan memungkinkan “peningkatan performa, optimalisasi memori, dan fitur-fitur baru yang menarik”.

#### 8.3.2 Kup: Penjadwal Backup

Plasma 6.8 memperkenalkan Kup, penjadwal backup untuk desktop Plasma. Kup adalah aplikasi backup berbasis btrfs yang sekarang menjadi modul kelas satu di Plasma.

{% hint style="info" %}
**Kup** adalah penjadwal backup yang memungkinkan pengguna untuk mengonfigurasi backup otomatis ke disk eksternal atau perangkat penyimpanan lain yang terpasang. Kup mendukung backup inkremental, sehingga hanya berkas yang berubah yang di-backup.
{% endhint %}

Fitur Kup meliputi:

* Backup otomatis berdasarkan jadwal.
* Dukungan untuk backup inkremental.
* Integrasi dengan disk eksternal dan perangkat penyimpanan lain.
* Antarmuka grafis yang terintegrasi dengan System Settings.

#### 8.3.3 Union Theming untuk QtWidgets

Plasma 6.8 melanjutkan pengembangan sistem tema Union dengan menambahkan dukungan untuk aplikasi QtWidgets, seperti Dolphin dan Kate.

{% hint style="info" %}
Dukungan Union untuk QtWidgets masih bersifat preliminer dan mungkin mengandung bug. Pengguna yang ingin menguji dapat melaporkan masalah di [https://bugs.kde.org/](https://bugs.kde.org/enter_bug.cgi?product=Union) [enter\_bug.cgi?product=Union.](https://bugs.kde.org/enter_bug.cgi?product=Union)
{% endhint %}

Untuk menguji Union:

{% stepper %}
{% step %}
Pastikan paket union terinstal.
{% endstep %}

{% step %}
Buka System Settings.
{% endstep %}

{% step %}
Navigasi ke Colors & Themes Application Style.
{% endstep %}

{% step %}
Pilih “Breeze (Union)”.
{% endstep %}

{% step %}
Klik Apply.
{% endstep %}
{% endstepper %}

#### 8.3.4 Fitur Lainnya

* **Shadows dan Rounded Corners untuk Steam:** Bayangan dan sudut membulat untuk jendela Steam.
* **Remote Desktop:** Peningkatan untuk Remote Desktop.
* **Aksesibilitas:** Fitur aksesibilitas baru.
* **Perekaman Layar:** Fitur baru untuk perekaman layar.
* **Spectacle Audio:** Spectacle sekarang dapat merekam audio selama perekaman layar.
* **NVIDIA Triple Buffering:** Triple buffering diaktifkan secara default untuk pengguna NVIDIA.

#### 8.3.5 Analisis

Plasma 6.8 adalah rilis yang berfokus pada masa depan Wayland dan integrasi fitur. Penghapusan sesi X11 adalah keputusan berani yang menunjukkan kepercayaan KDE pada Wayland. Pengenalan Kup sebagai modul kelas satu menunjukkan bahwa KDE serius tentang data integrity dan backup. Union theming, meskipun masih dalam tahap awal, menunjukkan arah masa depan sistem tema KDE Plasma.

| Fitur Utama    | Keterangan        |
| -------------- | ----------------- |
| X11            | Dihapus           |
| Kup            | Backup Scheduler  |
| Union          | QtWidgets Support |
| Remote Desktop | Improvements      |

_Gambar 8.3: Ringkasan fitur utama Plasma 6.8. Rilis ini menandai transisi penuh ke Wayland dan pengenalan modul Kup._


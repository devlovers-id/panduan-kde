# Studi Kasus: Bagaimana Plasma Menangani Multi-Layar

Dukungan multi-layar adalah salah satu area di mana KDE Plasma unggul. Bagian ini menyajikan studi kasus tentang bagaimana Plasma menangani konfigurasi multi-layar yang kompleks.

#### 3.7.1 Konsep Dasar

Plasma mengelola konfigurasi multi-layar melalui beberapa konsep:

**Output**

Layar fisik atau virtual yang terhubung ke sistem.

**Corona**

Objek Plasma yang mewakili satu output.

**Screen Layout**

Konfigurasi posisi, resolusi, dan orientasi output.

**Panel per Screen**

Setiap layar dapat memiliki panel sendiri dengan konfigurasi independen.

#### 3.7.2 Contoh Konfigurasi

Seorang pengguna dengan dua monitor dapat mengonfigurasi Plasma sebagai berikut:

* Monitor 1 (kiri): Panel atas dengan global menu, panel bawah dengan task manager.
* Monitor 2 (kanan): Panel bawah dengan system tray dan jam.
* Wallpaper: Berbeda untuk setiap monitor.
* Virtual Desktop: Terpisah untuk setiap monitor (Plasma 6.7+).

#### 3.7.3 Virtual Desktop per Layar (Plasma 6.7+)

Fitur baru di Plasma 6.7 memungkinkan setiap monitor memiliki virtual desktop independen. Ini sangat berguna untuk pengguna yang ingin memisahkan konteks kerja di antara monitor.

| Monitor 1      | Monitor 2        |
| -------------- | ---------------- |
| VD1, VD2, VD3  | VD-A, VD-B, VD-C |
| Panel & Widget | Panel & Widget   |

_Gambar 3.6: Konfigurasi multi-layar dengan virtual desktop per layar (Plasma 6.7+). Setiap monitor dapat memiliki set virtual desktop-nya sendiri, memungkinkan alur kerja yang lebih fleksibel._

#### 3.7.4 Pemecahan Masalah Multi-Layar

Berikut beberapa masalah umum dengan multi-layar dan solusinya:

**Monitor tidak terdeteksi**

Periksa koneksi fisik, jalankan `kscreen-doctor -o` untuk melihat output yang terdeteksi.

**Resolusi salah**

Buka System Settings Display and Monitor dan atur resolusi secara manual.

**Posisi monitor salah**

Atur posisi monitor dengan drag-and-drop di System Settings.

**Panel muncul di monitor yang salah**

Klik kanan panel dan pilih Edit Panel, lalu pindahkan ke monitor yang diinginkan.

{% hint style="success" %}
**Tips**

Untuk menyimpan profil konfigurasi multi-layar yang berbeda, gunakan fitur KScreen di Plasma. Ini memungkinkan Anda menyimpan dan memuat konfigurasi untuk berbagai setup, misalnya di kantor vs. di rumah.
{% endhint %}


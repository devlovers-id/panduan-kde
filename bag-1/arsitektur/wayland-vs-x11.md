# Arsitektur Wayland vs. X11 dalam Plasma 6

Salah satu perubahan terbesar di Plasma 6 adalah transisi ke Wayland sebagai protokol display default. Memahami perbedaan arsitektur antara Wayland dan X11 sangat penting untuk memahami perilaku Plasma 6.

#### 3.6.1 Perbedaan Fundamental

**X11**

X11 adalah protokol display server yang telah ada sejak tahun 1984. Arsitekturnya berbasis client-server, di mana server X (Xorg) mengelola input dan output grafis, dan klien (aplikasi) berkomunikasi dengan server melalui protokol X11.

**Server X**

Proses tunggal yang mengelola semua input, output, dan window.

**Kompositor**

Proses terpisah (misalnya, `compton`) yang menggabungkan output jendela.

**Manajer Jendela**

Proses terpisah (misalnya, KWin) yang mengelola posisi jendela.

**Keamanan**

Rendah, karena setiap aplikasi dapat mengakses input global dan jendela aplikasi lain.

**Wayland**

Wayland adalah protokol display server modern yang dikembangkan sebagai pengganti X11. Arsitekturnya berbeda secara fundamental:

**Kompositor**

Setiap kompositor (misalnya, KWin) adalah display server lengkap yang mengelola input, output, dan window.

**Tidak ada server X**

Tidak ada proses terpisah yang mengelola seluruh sistem grafis.

**Protokol berbasis objek**

Komunikasi antara aplikasi dan kompositor dilakukan melalui protokol berbasis objek.

**Keamanan**

Tinggi, karena aplikasi tidak dapat mengakses input global atau jendela aplikasi lain tanpa izin.

Gambar [3.5](pendahuluan.md#34%5F3%5FArsitektur%5Fdan%5FKomponen) menunjukkan perbandingan arsitektur kedua protokol.

| Arsitektur X11                     | Arsitektur Wayland                    |
| ---------------------------------- | ------------------------------------- |
| Aplikasi 1, Aplikasi 2, Aplikasi 3 | Aplikasi 1, Aplikasi 2, Aplikasi 3    |
| Server X (Xorg)                    | Kompositor (KWin)                     |
| Kompositor                         | Manajer Jendela • Kompositor • Server |
| Manajer Jendela                    | Kernel / Driver                       |
| Kernel / Driver                    |                                       |

_Gambar 3.5: Perbandingan arsitektur X11 dan Wayland. X11 memerlukan komponen terpisah untuk kompositing dan manajemen jendela, sedangkan Wayland menggabungkan semuanya ke dalam kompositor._

#### 3.6.2 Dampak pada Pengguna

Bagi pengguna, perbedaan arsitektur ini memiliki dampak praktis:

| Aspek            | X11                                   | Wayland                        |
| ---------------- | ------------------------------------- | ------------------------------ |
| Keamanan         | Aplikasi dapat mengambil input global | Setiap aplikasi diisolasi      |
| Performa         | Bergantung pada kompositing           | Rendering lebih efisien        |
| Multi-Monitor    | Dukungan matang                       | Dukungan yang terus berkembang |
| HiDPI Scaling    | Perlu konfigurasi manual              | Scaling otomatis               |
| Screenshot       | Semua aplikasi dapat screenshot       | Izin diperlukan                |
| Keyboard Global  | Berfungsi tanpa izin                  | Memerlukan port khusus         |
| Screen Recording | Berfungsi dengan OBS lama             | Memerlukan PipeWire            |

_Tabel 3.4: Dampak praktis dari perbedaan X11 dan Wayland. Beberapa aplikasi lama mungkin memerlukan penyesuaian untuk bekerja dengan baik di Wayland._

#### 3.6.3 XWayland

Untuk mengatasi kompatibilitas aplikasi lama, Plasma menyediakan XWayland, sebuah server X yang berjalan di dalam sesi Wayland. Aplikasi X11 dapat berjalan melalui XWayland tanpa perlu dimodifikasi.

* XWayland berjalan sebagai klien Wayland di dalam sesi.
* Aplikasi X11 melihat XWayland sebagai server X biasa.
* Kinerja sedikit lebih rendah dibanding aplikasi Wayland native.
* Beberapa fitur, misalnya scaling, mungkin tidak berfungsi sempurna.

{% hint style="info" %}
**Catatan**

Untuk memeriksa apakah aplikasi berjalan melalui XWayland atau Wayland native, gunakan perintah `xlsclients` untuk aplikasi X11, atau periksa variabel lingkungan `WAYLAND_DISPLAY` di dalam aplikasi.
{% endhint %}


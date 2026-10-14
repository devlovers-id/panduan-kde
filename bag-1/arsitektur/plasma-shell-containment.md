# Plasma Shell dan Containment

Plasma Shell adalah jantung dari KDE Plasma. Ia bertanggung jawab untuk menampilkan panel, desktop, dan widget, serta mengelola interaksi pengguna dengan elemen-elemen ini.

#### 3.2.1 Arsitektur Plasma Shell

Plasma Shell diimplementasikan oleh perintah `plasmashell`, yang dijalankan sebagai proses pengguna saat sesi dimulai. Ia memuat konfigurasi dari berbagai berkas dan membuat struktur objek yang merepresentasikan tata letak desktop.

{% hint style="info" %}
**Definisi**

Plasma Shell adalah proses yang mengelola satu atau lebih Corona, di mana setiap Corona merepresentasikan satu layar fisik. Di dalam setiap Corona terdapat satu atau lebih Containment Plasmoid, yang bertindak sebagai wadah untuk.
{% endhint %}

Hierarki objek dalam Plasma Shell dapat diringkas sebagai berikut:

* **Plasma Shell** — Proses utama (`plasmashell`)
* **Corona** — Satu per layar fisik; mengelola scene grafis
* **Containment** — Wadah untuk plasmoid; contoh: panel, desktop
* **Plasmoid** — Widget individual; contoh: jam, task manager

#### 3.2.2 Containment dan Plasmoid

Konsep containment dan plasmoid adalah fondasi arsitektur Plasma. Memahami keduanya sangat penting untuk memahami cara kerja KDE Plasma secara keseluruhan.

**Containment**

Containment adalah jenis khusus dari Applet yang dapat berisi Applet lain. Ia mengelola tata letak anak-anaknya dan bertanggung jawab atas _lifecycle_ mereka.

**Panel Containment**

Wadah horizontal atau vertikal yang menampilkan plasmoid dalam tata letak linier. Contoh: panel bawah default.

**Desktop Containment**

Wadah yang menampilkan plasmoid dalam tata letak bebas (_free-form_). Contoh: desktop itu sendiri.

**Activity Containment**

Wadah yang mengelompokkan beberapa containment untuk membentuk Activity.

**Plasmoid**

Plasmoid adalah widget individual yang memberikan fungsionalitas tertentu. Setiap plasmoid memiliki:

* Metadata dalam berkas `metadata.json` (Plasma 6) atau `metadata.desktop` (Plasma 5).
* UI yang ditulis dalam QML.
* Logika yang dapat ditulis dalam QML/JavaScript atau C++.
* Konfigurasi yang disimpan dalam berkas INI.

| Tingkat             | Isi                                      |
| ------------------- | ---------------------------------------- |
| Plasma Shell        |                                          |
| Corona (Layar 1)    | Containment: Panel, Containment: Desktop |
| Corona (Layar 2)    | Containment: Panel, Containment: Desktop |
| Containment panel   | Jam, Peluncur, Task                      |
| Containment desktop | Folder, Catatan                          |

_Gambar 3.2: Hierarki objek dalam Plasma Shell. Satu Plasma Shell mengelola beberapa Corona (satu per layar). Setiap Corona berisi Containment, dan setiap Containment berisi Plasmoid._

#### 3.2.3 Siklus Hidup Plasmoid

Plasmoid memiliki siklus hidup yang terdefinisi dengan baik:

1. **Discovery.** Plasma Shell memindai direktori sistem dan pengguna untuk menemukan plasmoid yang tersedia.
2. **Loading.** Ketika plasmoid ditambahkan ke containment, Plasma memuat metadata-nya dan menginisialisasi QML engine.
3. **Instantiation.** Kelas C++ Applet diinstansiasi, dan komponen QML dibuat.
4. **Running.** Plasmoid berjalan, menerima event, dan memperbarui tampilannya.
5. **Configuration.** Pengguna dapat mengonfigurasi plasmoid melalui dialog konfigurasi.
6. **Destruction.** Ketika plasmoid dihapus dari containment, resource-nya dibersihkan.

{% hint style="success" %}
**Tips**

Untuk melihat plasmoid yang tersedia di sistem Anda, gunakan perintah `plasmoidviewer -l` di terminal. Ini akan menampilkan daftar semua plasmoid yang terinstal beserta lokasinya.
{% endhint %}

#### 3.2.4 Lokasi Berkas Plasma Shell

Konfigurasi dan data Plasma Shell tersimpan di beberapa lokasi standar:

| Lokasi                                      | Konten                                      |
| ------------------------------------------- | ------------------------------------------- |
| `~/.config/plasma-org.kde.plasma-appletsrc` | Konfigurasi plasmoid dan tata letak desktop |
| `~/.config/plasmashellrc`                   | Pengaturan Plasma Shell                     |
| `~/.local/share/plasma/plasmoids/`          | Plasmoid yang diinstal pengguna             |
| `~/.local/share/plasma/desktoptheme/`       | Plasma Style yang diinstal pengguna         |
| `/usr/share/plasma/plasmoids/`              | Plasmoid sistem                             |
| `/usr/share/plasma/desktoptheme/`           | Plasma Style sistem                         |

_Tabel 3.2: Lokasi berkas konfigurasi dan data Plasma Shell. Memahami lokasi ini penting untuk backup, migrasi, dan pemecahan masalah._


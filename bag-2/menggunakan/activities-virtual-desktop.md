# Activities dan Virtual Desktop

Salah satu fitur paling kuat dan unik dari KDE Plasma adalah Activities. Bersama dengan virtual desktop, Activities memberikan cara yang fleksibel untuk mengorganisasi ruang kerja Anda.

#### 5.3.1 Konsep Dasar

**Virtual Desktop** adalah pembagian logis dari area kerja dalam satu konteks. Setiap virtual desktop memiliki jendela sendiri, tetapi berbagi widget, wallpaper, dan pengaturan panel yang sama.

**Activity** adalah konteks yang lebih tinggi yang mencakup virtual desktop, widget, wallpaper, dan pengaturan panel yang berbeda. Setiap Activity adalah lingkungan yang terpisah secara konseptual.

| Aspek     | Virtual Desktop             | Activity                |
| --------- | --------------------------- | ----------------------- |
| Jendela   | Berbeda pada setiap desktop | Berbeda menurut konteks |
| Wallpaper | Sama                        | Berbeda                 |
| Panel     | Sama                        | Berbeda                 |
| Widget    | Sama                        | Berbeda                 |

#### 5.3.2 Mengapa Menggunakan Activities?

Activities sangat berguna untuk memisahkan konteks kerja yang berbeda:

| Activity     | Contoh penggunaan                                                           |
| ------------ | --------------------------------------------------------------------------- |
| Kerja        | Dengan widget kalender, task list, dan wallpaper profesional.               |
| Rumah        | Dengan widget media player, foto keluarga, dan wallpaper santai.            |
| Pengembangan | Dengan widget terminal, system monitor, dan pintasan aplikasi pengembangan. |
| Hiburan      | Dengan widget game launcher, media player, dan wallpaper game.              |

{% hint style="info" %}
Activities sangat berguna untuk pengguna yang sering berpindah antara konteks kerja yang berbeda. Misalnya, seorang pengembang dapat memiliki Activity “Pengembangan” dengan terminal dan editor kode, serta Activity “Komunikasi” dengan email dan chat.
{% endhint %}

#### 5.3.3 Membuat dan Mengelola Activities

{% stepper %}
{% step %}
### Buka Activities

Buka **System Settings → Workspace Behavior → Activities**.
{% endstep %}

{% step %}
### Buat Activity baru

Klik **Create New...** di bagian atas.
{% endstep %}

{% step %}
### Isi informasi

Masukkan nama, deskripsi, dan pilih ikon untuk Activity.
{% endstep %}

{% step %}
### Buat Activity

Klik **Create**.
{% endstep %}

{% step %}
### Konfigurasikan Activity

Atur wallpaper, panel, dan widget untuk Activity baru.
{% endstep %}
{% endstepper %}

Untuk berpindah antar Activities:

* Klik widget Activity Switcher di panel, jika tersedia.
* Gunakan pintasan `Meta + Q`, sebagai default.
* Buka **System Settings → Workspace Behavior → Activities**, lalu klik Activity yang diinginkan.

#### 5.3.4 Virtual Desktop

Virtual Desktop adalah cara tradisional untuk memisahkan jendela dalam satu konteks. KDE Plasma mendukung hingga 20 virtual desktop secara default.

**Mengelola Virtual Desktop**

{% stepper %}
{% step %}
### Buka Virtual Desktops

Buka **System Settings → Workspace Behavior → Virtual Desktops**.
{% endstep %}

{% step %}
### Atur jumlah desktop

Atur jumlah virtual desktop dengan menggeser slider.
{% endstep %}

{% step %}
### Beri nama desktop

Beri nama setiap virtual desktop dengan mengklik namanya.
{% endstep %}

{% step %}
### Terapkan pengaturan

Klik **Apply**.
{% endstep %}
{% endstepper %}

**Navigasi Antar Virtual Desktop**

* Gunakan `Ctrl + F1` hingga `Ctrl + F4` untuk berpindah langsung.
* Gunakan `Ctrl + Alt + Left/Right` untuk berpindah ke kiri atau kanan.
* Gunakan widget Desktop Pager di panel untuk navigasi visual.

#### 5.3.5 Virtual Desktop per Layar

Fitur baru di Plasma 6.7 memungkinkan setiap monitor memiliki virtual desktop independen. Ini sangat berguna untuk pengguna dengan konfigurasi multi-monitor yang kompleks.

> **Catatan**
>
> Fitur Virtual Desktop per Layar memerlukan Plasma 6.7 atau lebih baru. Jika Anda menggunakan versi sebelumnya, fitur ini tidak tersedia.


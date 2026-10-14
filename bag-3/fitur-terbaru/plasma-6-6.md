# Plasma 6.6 (Februari 2026)

Plasma 6.6 dirilis pada 17 Februari 2026, menandai rilis fitur pertama di tahun 2026. Rilis ini membawa beberapa modul baru yang signifikan, terutama di area manajemen login, perangkat sentuh, dan aksesibilitas.

#### 8.1.1 Modul Baru

Plasma 6.6 memperkenalkan tiga modul baru yang signifikan:

**Plasma Login Manager (PLM)**

Plasma Login Manager (PLM) adalah manajer login opsional baru yang dikembangkan oleh KDE. Ia merupakan alternatif dari SDDM (Simple Desktop Display Manager) yang telah lama menjadi default di KDE Plasma.

{% hint style="info" %}
**Plasma Login Manager (PLM)** adalah manajer login berbasis QML yang dikembangkan oleh KDE. Ia menyediakan integrasi yang lebih erat dengan KDE Plasma, dengan greeter yang dapat dikustomisasi, dukungan untuk plugin wallpaper, dan modul konfigurasi System Settings tersendiri.
{% endhint %}

PLM dikembangkan sebagai upaya untuk menyediakan pengalaman login yang lebih terintegrasi dengan KDE Plasma. Meskipun pada awalnya sebagian besar merupakan SDDM yang direfaktor, tujuannya adalah integrasi yang lebih erat dengan Plasma di masa depan. PLM juga menyertakan modul System Settings-nya sendiri, berdasarkan sddm-kcm6.

{% hint style="info" %}
PLM bergantung pada systemd, sehingga tidak tersedia untuk distribusi yang tidak menggunakan systemd. Untuk distribusi tersebut, SDDM tetap menjadi pilihan utama.
{% endhint %}

Beberapa distribusi, seperti Fedora Linux 44, CachyOS, dan EndeavourOS, telah mengadopsi PLM sebagai manajer login default mereka. Fedora secara resmi mengumumkan bahwa semua varian KDE mereka akan beralih dari SDDM ke PLM.

```bash
# Instalasi PLM
sudo dnf install plasma-login-manager kcm-plasmalogin

# Aktifkan layanan PLM
sudo systemctl enable --force plasmalogin.service
```

**Plasma-Keyboard**

Plasma-Keyboard adalah keyboard on-screen terintegrasi yang dirancang untuk tablet dan perangkat sentuh. Fitur ini sangat penting untuk perangkat seperti tablet dan laptop konvertibel yang tidak memiliki keyboard fisik.

* **Integrasi dengan Plasma:** Keyboard muncul secara otomatis saat bidang input difokuskan.
* **Mode penuh dan ringkas:** Pengguna dapat memilih antara keyboard penuh dan mode ringkas.
* **Dukungan multibahasa:** Keyboard mendukung berbagai tata letak dan bahasa.
* **Prediksi teks:** Saran kata saat mengetik.

**Plasma-Setup**

Plasma-Setup adalah alat konfigurasi awal yang membantu pengguna baru mengatur preferensi dasar setelah instalasi.

* Pemilihan bahasa dan wilayah.
* Pengaturan tata letak keyboard.
* Konfigurasi zona waktu.
* Koneksi jaringan.
* Pemilihan tema awal.

#### 8.1.2 Fitur Spectacle OCR

Salah satu fitur yang paling banyak dibicarakan dari Plasma 6.6 adalah kemampuan OCR (Optical Character Recognition) di Spectacle, alat screenshot KDE Plasma.

{% hint style="info" %}
**OCR (Optical Character Recognition)** adalah teknologi yang memungkinkan komputer untuk mengekstrak teks dari gambar. Di Spectacle, fitur ini memungkinkan pengguna untuk menyalin teks dari screenshot tanpa harus mengetik ulang.
{% endhint %}

Dengan fitur ini, pengguna dapat:

{% stepper %}
{% step %}
Mengambil screenshot area yang mengandung teks.
{% endstep %}

{% step %}
Mengaktifkan mode OCR di Spectacle.
{% endstep %}

{% step %}
Memilih teks yang ingin diekstrak.
{% endstep %}

{% step %}
Menyalin teks ke clipboard untuk digunakan di aplikasi lain.
{% endstep %}
{% endstepper %}

Fitur ini sangat berguna untuk:

* Menyalin teks dari gambar atau video yang tidak dapat dipilih.
* Mengekstrak teks dari dokumen yang dipindai.
* Mengambil kode dari screenshot tutorial.
* Menerjemahkan teks dari gambar.

#### 8.1.3 Filter Buta Warna dan Filter Grayscale

Plasma 6.6 menambahkan filter grayscale baru di dalam fitur Color Blindness. Filter ini memungkinkan pengguna untuk:

* Mengaktifkan mode grayscale untuk seluruh layar.
* Mengurangi kelelahan mata saat membaca dalam waktu lama.
* Membantu pengguna dengan sensitivitas warna tertentu.
* Menghemat daya pada layar OLED karena piksel putih tidak menyala penuh.

#### 8.1.4 Kecerahan Layar Otomatis

Plasma 6.6 memperkenalkan fitur kecerahan layar otomatis untuk perangkat yang memiliki sensor cahaya sekitar (ambient light sensor). Fitur ini secara otomatis menyesuaikan kecerahan layar berdasarkan kondisi pencahayaan di sekitar perangkat.

* Mengurangi kelelahan mata dalam kondisi cahaya yang berubah-ubah.
* Menghemat daya baterai dengan menyesuaikan kecerahan secara dinamis.
* Dapat diaktifkan atau dinonaktifkan melalui System Settings.

#### 8.1.5 Wi-Fi via QR Code

Plasma 6.6 menambahkan kemampuan untuk terhubung ke jaringan Wi-Fi dengan memindai kode QR. Fitur ini sangat berguna untuk:

* Terhubung ke jaringan Wi-Fi publik tanpa mengetik kata sandi.
* Berbagi kredensial Wi-Fi dengan tamu.
* Terhubung ke jaringan yang kompleks dengan mudah.

#### 8.1.6 Animasi Lebih Halus

Plasma 6.6 meningkatkan animasi pada layar dengan refresh rate tinggi. Animasi sekarang lebih halus dan responsif, terutama pada monitor 120 Hz, 144 Hz, atau lebih tinggi.

#### 8.1.7 Peningkatan Lainnya

* **Emoji Selector:** Pemilih warna kulit (skin tone) baru di panel emoji.
* **XRandr Emulation:** Emulasi XRandr di KWin untuk kompatibilitas aplikasi XWayland yang lebih baik.
* **Per-DRM-Plane Color Pipeline:** Dukungan pipeline warna per-DRM-plane.
* **Custom Screen Mode:** Dukungan mode layar kustom di sesi Wayland.
* **Slow Keys:** Fitur aksesibilitas baru untuk pengguna dengan tremor.
* **Penanganan Baterai:** Peningkatan penanganan baterai pada laptop.
* **Global Actions untuk Media:** Aksi global untuk seek maju/mundur dalam pemutaran media.
* **Window List Widget:** Fitur baru termasuk open-on-hover, menyembunyikan ikon, dan filter yang dapat dikonfigurasi.

#### 8.1.8 Analisis

Plasma 6.6 adalah rilis yang berfokus pada perangkat sentuh dan aksesibilitas. Fitur seperti Plasma-Keyboard dan ambient light sensor menunjukkan bahwa KDE serius tentang dukungan perangkat mobile dan tablet. Fitur OCR di Spectacle adalah contoh bagaimana fitur yang sebelumnya memerlukan aplikasi pihak ketiga sekarang terintegrasi langsung ke dalam ekosistem Plasma.

| Rilis | Tanggal |
| ----- | ------- |
| 6.6.0 | 17 Feb  |
| 6.6.1 | 24 Feb  |
| 6.6.2 | 10 Mar  |
| 6.6.3 | 17 Mar  |
| 6.6.4 | 7 Apr   |
| 6.6.5 | 12 Mei  |

_Gambar 8.1: Siklus rilis Plasma 6.6 dengan pembaruan bugfix bulanan. Setiap rilis membawa perbaikan bug dan peningkatan stabilitas._


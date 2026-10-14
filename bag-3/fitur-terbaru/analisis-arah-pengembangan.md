# Analisis: Arah Pengembangan Plasma

Dari fitur-fitur yang diperkenalkan di Plasma 6.6 hingga 6.9, kita dapat mengidentifikasi beberapa tren utama dalam pengembangan KDE Plasma.

#### 8.5.1 Tren 1: Transisi Penuh ke Wayland

Transisi ke Wayland adalah perubahan paling signifikan dalam siklus Plasma 6.x. Dimulai dengan Wayland sebagai default di Plasma 6.0, dan berakhir dengan penghapusan sesi X11 di Plasma 6.8, KDE telah menunjukkan komitmen penuh terhadap Wayland.

| Status Wayland               | Rilis   |
| ---------------------------- | ------- |
| Default                      | 6.0     |
| Matang                       | 6.5–6.7 |
| X11 dihapus                  | 6.8     |
| Wayland satu-satunya pilihan | 6.9     |

_Gambar 8.4: Tren adopsi Wayland vs X11 di Plasma 6.x. Wayland menjadi default di Plasma 6.0, matang di 6.5–6.7, dan menjadi satu-satunya pilihan di Plasma 6.8._

#### 8.5.2 Tren 2: Integrasi Fitur

Plasma semakin terintegrasi dengan fitur-fitur yang sebelumnya memerlukan aplikasi pihak ketiga. Contohnya:

* **OCR di Spectacle (Plasma 6.6):** Sebelumnya memerlukan alat OCR terpisah.
* **Kup Backup (Plasma 6.8):** Sebelumnya memerlukan aplikasi backup terpisah.
* **Kontrol Mikrofon (Plasma 6.7):** Sebelumnya memerlukan aplikasi audio terpisah.
* **Manajemen Printer (Plasma 6.7):** Peningkatan signifikan dalam integrasi printer.

#### 8.5.3 Tren 3: Fokus pada Perangkat Sentuh

Plasma 6.6 memperkenalkan Plasma-Keyboard, dan Plasma 6.7 menambahkan press-and-hold untuk karakter khusus. Ini menunjukkan bahwa KDE serius tentang dukungan perangkat sentuh dan tablet.

#### 8.5.4 Tren 4: Personaalisasi yang Lebih Dalam

Fitur seperti Global Theme kustom (6.6), toggle terang/gelap cepat (6.7), dan Union theming (6.8) menunjukkan bahwa KDE Plasma terus meningkatkan kemampuan kustomisasi.

#### 8.5.5 Tren 5: Keamanan dan Privasi

Perubahan kebijakan D-Bus untuk broadcast notifications (6.9) menunjukkan bahwa KDE memperhatikan keamanan dan privasi pengguna.


# Arsitektur Kustomisasi

Sebelum masuk ke detail masing-masing komponen, penting untuk memahami bagaimana sistem kustomisasi KDE Plasma dibangun. Kustomisasi di KDE Plasma bukanlah tambahan yang ditempelkan belakangan, melainkan bagian integral dari arsitektur sejak awal.

#### 6.1.1 Lapisan Kustomisasi

Kustomisasi di KDE Plasma memiliki beberapa lapisan, dari yang paling umum hingga yang paling spesifik:

1. **Global Theme:** Satu klik mengubah semuanya.
2. **Komponen individual:** Plasma Style, Colors, Icons, Decorations, dan Cursors.
3. **Tata letak panel dan widget.**
4. **Perilaku:** Pintasan, efek, dan aturan jendela.
5. **Script dan otomasi:** KWin Scripts dan QML.

Pengguna dapat memilih untuk mengubah hanya lapisan tertentu atau mengombinasikan semuanya untuk menciptakan lingkungan yang benar-benar personal.

#### 6.1.2 Lokasi Berkas Kustomisasi

Semua kustomisasi di KDE Plasma disimpan dalam berkas yang dapat dibaca manusia. Memahami lokasi berkas ini penting untuk backup, migrasi, dan pemecahan masalah.

| Lokasi                                              | Konten                                                     |
| --------------------------------------------------- | ---------------------------------------------------------- |
| `~/.config/kdeglobals`                              | Pengaturan global KDE, seperti skema warna, font, dan ikon |
| `~/.config/plasmarc`                                | Konfigurasi Plasma Shell                                   |
| `~/.config/kwinrc`                                  | Konfigurasi KWin                                           |
| `~/.config/plasma-org.kde.plasma.desktop-appletsrc` | Tata letak widget dan panel desktop                        |
| `~/.local/share/plasma/desktoptheme/`               | Plasma Style yang diinstal pengguna                        |
| `~/.local/share/plasma/look-and-feel/`              | Global Theme yang diinstal pengguna                        |
| `~/.local/share/plasma/plasmoids/`                  | Widget yang diinstal pengguna                              |
| `~/.local/share/color-schemes/`                     | Skema warna yang diinstal pengguna                         |
| `~/.local/share/icons/`                             | Tema ikon yang diinstal pengguna                           |
| `~/.local/share/aurorae/themes/`                    | Dekorasi jendela Aurorae                                   |

{% hint style="info" %}
Untuk memudahkan backup dan restore kustomisasi, gunakan alat seperti Konsave. Ia dapat menyimpan semua tema, widget, dan pengaturan Anda ke dalam satu berkas, dan memulihkannya di sistem lain dengan satu perintah.
{% endhint %}


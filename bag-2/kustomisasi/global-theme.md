# Global Theme

Global Theme, sebelumnya disebut “Look and Feel”, adalah cara tercepat dan paling menyeluruh untuk mengubah tampilan KDE Plasma. Satu Global Theme dapat mengubah puluhan pengaturan sekaligus, menciptakan konsistensi visual di seluruh sistem.

#### 6.2.1 Apa Itu Global Theme?

> **Definisi**
>
> Global Theme adalah paket kustomisasi yang menggabungkan beberapa komponen visual: Plasma Style, skema warna, tema ikon, dekorasi jendela, task switcher, splash screen, dan tema lock screen. Menerapkan Global Theme akan mengubah semua komponen ini secara bersamaan, memastikan konsistensi visual.

Komponen yang termasuk dalam Global Theme meliputi:

* Plasma Style
* Kursor
* Skema warna
* Lock screen
* Tema ikon
* Splash screen
* Dekorasi jendela
* Task switcher

#### 6.2.2 Struktur Paket Global Theme

Global Theme disimpan sebagai paket KPackage. Struktur direktori paket adalah sebagai berikut:

```
my-global-theme/
|-- metadata.json # Metadata paket (wajib)
|-- contents/
|   |-- defaults # Nilai default
|   |-- layout-templates/ # Template tata letak panel
|   |   +-- org.kde.plasma.desktop-layout.js
|   |-- splash/ # Splash screen
|   |   |-- splash.qml
|   |   +-- images/
|   |-- look-and-feel/ # Konfigurasi tambahan
|   |-- logout/ # Layar logout
|   +-- sddm/ # Tema login SDDM
+-- LICENSE # Lisensi
```

Berkas `metadata.json` harus memiliki struktur berikut:

```json
{
  "KPackageStructure": "Plasma/LookAndFeel",
  "KPlugin": {
    "Authors": [
      {
        "Email": "author@example.com",
        "Name": "Nama Penulis"
      }
    ],
    "Category": "Global Themes",
    "Description": "Deskripsi tema global",
    "Id": "com.example.mytheme",
    "License": "GPL-3.0+",
    "Name": "My Theme",
    "Version": "1.0",
    "Website": "https://example.com"
  },
  "X-KDE-PluginInfo-Name": "com.example.mytheme",
  "X-Plasma-APIVersion": "2"
}
```

> **Catatan**
>
> Di Plasma 6, format metadata diubah dari `metadata.desktop` ke `metadata.json`, dan kunci `KPackageStructure` harus diset ke `Plasma/LookAndFeel` agar tema muncul di pengaturan Global Theme. Tema lama dari Plasma 5 perlu dikonversi secara manual.

#### 6.2.3 Memasang Global Theme

**Melalui KDE Store**

{% stepper %}
{% step %}
### Buka Global Theme

Buka **System Settings → Colors & Themes → Global Theme**.
{% endstep %}

{% step %}
### Jelajahi tema baru

Klik **Get New Global Themes...** di bagian bawah.
{% endstep %}

{% step %}
### Pilih tema

Jelajahi KDE Store atau gunakan kotak pencarian.
{% endstep %}

{% step %}
### Instal tema

Klik **Install** pada tema yang diinginkan.
{% endstep %}

{% step %}
### Terapkan tema

Setelah terinstal, tema akan muncul di daftar. Klik **Apply**.
{% endstep %}
{% endstepper %}

**Melalui Command Line**

```bash
# Memasang dari file lokal
kpackagetool6 --type Plasma/LookAndFeel --install /path/to/theme.tar.gz

# Memasang dari KDE Store (menggunakan ID)
plasmapkg2 --type lookandfeel --install com.example.mytheme

# Menghapus tema
kpackagetool6 --type Plasma/LookAndFeel --remove com.example.mytheme

# Melihat daftar tema yang terinstal
kpackagetool6 --type Plasma/LookAndFeel --list
```

{% hint style="info" %}
Untuk menjelajahi Global Theme populer, kunjungi [https://store.kde.org/browse?cat=104.](https://store.kde.org/browse?cat=104) Beberapa tema populer termasuk WhiteSur, Layan, Sweet, dan Nordic.
{% endhint %}

#### 6.2.4 Global Theme Populer

| Nama        | Gaya         | Deskripsi                                         |
| ----------- | ------------ | ------------------------------------------------- |
| Breeze      | Default      | Tema default Plasma, modern dan bersih            |
| Breeze Dark | Default Dark | Varian gelap dari Breeze                          |
| WhiteSur    | macOS-like   | Meniru tampilan macOS Big Sur                     |
| Layan       | Modern Flat  | Desain datar dengan aksen warna cerah             |
| Sweet       | Playful      | Warna-warna cerah dan bentuk bulat                |
| Nordic      | Minimalis    | Palet warna nordik yang tenang                    |
| Dracula     | Gelap        | Palet Dracula yang populer di kalangan pengembang |
| Arc         | Flat         | Desain datar yang terinspirasi dari GNOME         |


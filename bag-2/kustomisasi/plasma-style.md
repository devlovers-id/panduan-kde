# Plasma Style

Plasma Style, disebut juga Desktop Theme, mengontrol gaya visual panel, widget, popup, OSD, lock screen, dan logout screen. Ia adalah komponen kustomisasi yang paling sering diubah oleh pengguna.

#### 6.3.1 Apa Itu Plasma Style?

> **Definisi**
>
> Plasma Style adalah paket aset grafis SVG dan konfigurasi yang menentukan tampilan visual elemen Plasma Shell. Ia mencakup panel, widget frame, tooltip, popup, dan berbagai elemen lainnya. Plasma Style dapat menyertakan skema warna sendiri yang menimpa skema warna sistem untuk elemen UI Plasma.

#### 6.3.2 Komponen Plasma Style

| Berkas                         | Fungsi                          |
| ------------------------------ | ------------------------------- |
| `widgets/background.svg`       | Latar belakang panel dan widget |
| `widgets/panel-background.svg` | Latar belakang panel spesifik   |
| `widgets/tooltip.svg`          | Tooltip                         |
| `widgets/button.svg`           | Tombol                          |
| `widgets/lineedit.svg`         | Kotak input teks                |
| `widgets/scrollbar.svg`        | Scrollbar                       |
| `widgets/checkmarks.svg`       | Checkmark                       |
| `widgets/clock.svg`            | Elemen jam                      |
| `colors`                       | Skema warna untuk elemen Plasma |
| `metadata.json`                | Metadata tema                   |

#### 6.3.3 Struktur Paket Plasma Style

```
my-plasma-style/
|-- metadata.json # Metadata (wajib)
|-- colors # Skema warna Plasma
|-- widgets/
|   |-- background.svg # Latar belakang umum
|   |-- panel-background.svg # Latar belakang panel
|   |-- tooltip.svg # Tooltip
|   |-- button.svg # Tombol
|   |-- lineedit.svg # Kotak input
|   |-- scrollbar.svg # Scrollbar
|   +-- ...
|-- opaque/ # Varian opaque
|   +-- widgets/...
|-- translucent/ # Varian translucent
|   +-- widgets/...
+-- solid/ # Varian solid
    +-- widgets/...
```

> **Catatan**
>
> Plasma Style dapat menyediakan beberapa varian: `opaque` tanpa transparansi, `translucent` dengan transparansi, dan `solid` dengan warna solid. Plasma akan memilih varian yang sesuai berdasarkan pengaturan kompositing pengguna.

#### 6.3.4 Memasang Plasma Style

```bash
# Memasang dari file
kpackagetool6 --type Plasma/Theme --install /path/to/style.tar.gz

# Melihat daftar style yang terinstal
kpackagetool6 --type Plasma/Theme --list

# Menghapus style
kpackagetool6 --type Plasma/Theme --remove com.example.mystyle

# Mengubah style melalui command line
plasma-apply-desktoptheme my-style
```

#### 6.3.5 Mengedit SVG Plasma Style

Untuk mengedit Plasma Style yang ada, Anda perlu mengedit berkas SVG di dalamnya. Setiap berkas SVG menggunakan stylesheet khusus yang memungkinkan Plasma untuk mengganti warna secara dinamis.

**Konvensi SVG Plasma**

1. **Stylesheet Classes:** Elemen SVG dapat diberi kelas CSS seperti `background`, `center`, `top`, `bottom`, `left`, dan `right`.
2. **9-Slice Scaling:** Berkas SVG dirancang dengan 9-slice scaling, memungkinkan panel untuk diperluas tanpa distorsi.
3. **Color Scheme:** Warna dapat diambil dari skema warna Plasma menggunakan referensi seperti `ButtonBackground`, `ViewBackground`, dan lainnya.
4. **Element IDs:** Elemen SVG memiliki ID khusus yang digunakan Plasma untuk mengambil bagian tertentu, misalnya `center` dan `topleft`.

{% hint style="info" %}
Untuk mengedit Plasma Style, gunakan Inkscape dengan ekstensi khusus untuk Plasma. Ekstensi ini menyediakan template 9-slice dan memungkinkan Anda melihat bagaimana tema akan terlihat pada berbagai ukuran panel.
{% endhint %}


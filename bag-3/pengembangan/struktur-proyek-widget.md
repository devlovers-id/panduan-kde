# Struktur Proyek Widget

Setelah lingkungan siap, langkah berikutnya adalah memahami struktur proyek widget Plasma. Struktur ini mengikuti konvensi yang telah ditetapkan oleh KDE.

#### 7.3.1 Struktur Direktori Standar

Proyek widget Plasma memiliki struktur direktori yang terdefinisi dengan baik:

```
my-widget/
├── CMakeLists.txt
├── LICENSE
└── package/
    ├── metadata.json
    └── contents/
        ├── ui/
        │   ├── main.qml
        │   ├── FullRepresentation.qml
        │   └── CompactRepresentation.qml
        └── config/
```

_Gambar 7.1: Struktur direktori standar proyek widget Plasma 6. Setiap komponen memiliki peran spesifik dalam keseluruhan proyek._

#### 7.3.2 Peran Setiap Berkas

**metadata.json**

Berkas ini adalah metadata untuk widget. Ia memberitahu Plasma tentang nama widget, deskripsi, penulis, versi, dan konfigurasi lainnya.

```json
{
    "KPackageStructure": "Plasma/Applet",
    "KPlugin": {
        "Authors": [
            {
                "Email": "author@example.com",
                "Name": "Nama Penulis"
            }
        ],
        "Category": "Utilities",
        "Description": "Widget contoh untuk demonstrasi",
        "Description[de]": "Beispiel-Widget zur Demonstration",
        "Icon": "preferences-system",
        "Id": "com.example.mywidget",
        "License": "GPL-3.0+",
        "Name": "My Widget",
        "Name[de]": "Mein Widget",
        "Version": "1.0.0",
        "Website": "https://example.com/mywidget"
    },
    "X-Plasma-API-Minimum-Version": "6.0",
    "X-Plasma-Provides": [
        "org.kde.plasma.clock"
    ]
}
```

{% hint style="info" %}
Kunci `Description[de]` dan `Name[de]` adalah contoh lokalisasi. Plasma akan otomatis memilih terjemahan yang sesuai berdasarkan bahasa sistem pengguna. Untuk menambahkan terjemahan, cukup tambahkan kunci dengan kode bahasa dalam tanda kurung siku.
{% endhint %}

**main.qml**

Berkas ini adalah entry point QML untuk widget. Untuk plasmoid, root object adalah `PlasmoidItem` di Plasma 6 atau `Plasmoid.Item` di Plasma 5.

**CMakeLists.txt**

Berkas ini mengonfigurasi bagaimana widget dibangun dan diinstal.

**LICENSE**

Berkas lisensi. KDE merekomendasikan lisensi GPL-3.0+ atau LGPL-3.0+ untuk widget.

#### 7.3.3 Struktur Direktori Pengguna

Setelah widget diinstal, ia akan berada di salah satu dari dua lokasi:

**Widget Sistem**

`/usr/share/plasma/plasmoids/com.example.mywidget/` — Untuk widget yang diinstal melalui manajer paket distribusi.

**Widget Pengguna**

`~/.local/share/plasma/plasmoids/com.example.mywidget/` — Untuk widget yang diinstal melalui KDE Store atau pengembangan lokal.

{% hint style="info" %}
Selama pengembangan, Anda dapat menginstal widget di direktori pengguna tanpa perlu hak akses root. Gunakan `kpackagetool6 --type Plasma/Applet --install package/ --hash ...` untuk menginstal dan `--remove` untuk menghapus.
{% endhint %}


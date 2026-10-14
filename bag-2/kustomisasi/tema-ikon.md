# Tema Ikon

Tema ikon adalah salah satu cara termudah untuk mengubah tampilan desktop secara signifikan. Ia menentukan ikon yang digunakan untuk aplikasi, berkas, folder, dan elemen sistem lainnya.

#### 6.5.1 Apa Itu Tema Ikon?

> **Definisi**
>
> Tema ikon adalah kumpulan berkas ikon dalam berbagai ukuran yang mengikuti spesifikasi Freedesktop. Setiap tema ikon menyediakan ikon untuk berbagai kategori seperti aplikasi, berkas, folder, perangkat, dan status. Plasma akan memilih ikon dari tema yang aktif berdasarkan nama ikon yang diminta aplikasi.

#### 6.5.2 Struktur Tema Ikon

Tema ikon disimpan di `~/.local/share/icons/` atau `/usr/share/icons/`.

```
MyIconTheme/
|-- index.theme # Metadata tema
|-- 16x16/ # Ikon 16x16 piksel
|   |-- apps/
|   |-- actions/
|   |-- devices/
|   |-- mimetypes/
|   |-- places/
|   +-- status/
|-- 22x22/
|-- 24x24/
|-- 32x32/
|-- 48x48/
|-- 64x64/
|-- scalable/ # Ikon SVG yang dapat diskalakan
|   |-- apps/
|   |-- actions/
|   +-- ...
+-- symbolic/ # Ikon simbolik monokrom
    |-- apps/
    +-- ...
```

Berkas `index.theme` mendefinisikan metadata tema:

```ini
[Icon Theme]
Name=My Icon Theme
Comment=Tema ikon kustom
Inherits=hicolor

Directories=16x16/apps,22x22/apps,24x24/apps,32x32/apps,48x48/apps,64x64/apps,scalable/apps

[16x16/apps]
Size=16
Context=Applications
Type=Fixed

[22x22/apps]
Size=22
Context=Applications
Type=Fixed

[scalable/apps]
Size=256
Context=Applications
Type=Scalable
MinSize=16
MaxSize=512
```

#### 6.5.3 Konvensi Penamaan Ikon

| Kategori  | Contoh nama ikon                                       |
| --------- | ------------------------------------------------------ |
| Aplikasi  | `firefox`, `org.kde.dolphin`, `system-settings`        |
| Aksi      | `document-save`, `edit-copy`, `window-close`           |
| Perangkat | `drive-harddisk`, `computer`, `audio-card`             |
| Mimetype  | `text-plain`, `image-png`, `application-pdf`           |
| Places    | `folder-home`, `folder-documents`, `user-trash`        |
| Status    | `dialog-information`, `dialog-warning`, `dialog-error` |

{% hint style="info" %}
Untuk melihat ikon apa yang digunakan oleh aplikasi tertentu, gunakan Icon Browser, tersedia melalui `plasma-apply-colorscheme` atau sebagai aplikasi standalone. Ini menunjukkan nama ikon yang sedang digunakan, sehingga Anda dapat memodifikasinya.
{% endhint %}

#### 6.5.4 Tema Ikon Populer

| Nama         | Gaya         | Deskripsi                                 |
| ------------ | ------------ | ----------------------------------------- |
| Breeze       | Default      | Ikon default Plasma, modern dan konsisten |
| Papirus      | Flat         | Ikon datar yang sangat populer            |
| Numix Circle | Bulat        | Ikon dalam lingkaran dengan warna cerah   |
| La Capitaine | macOS-like   | Terinspirasi desain macOS                 |
| WhiteSur     | macOS-like   | Cocok dengan Global Theme WhiteSur        |
| Tela         | Modern       | Ikon modern dengan banyak varian warna    |
| Fluent       | Windows-like | Terinspirasi ikon Windows 11              |

#### 6.5.5 Memasang Tema Ikon

```bash
# Memasang dari file
kpackagetool6 --type IconTheme --install /path/to/icons.tar.gz

# Melihat daftar tema ikon yang terinstal
kpackagetool6 --type IconTheme --list

# Mengubah tema ikon melalui command line
kwriteconfig6 --file kdeglobals --group Icons --key Theme Papirus-Dark

# Atau menggunakan plasma-apply-icontheme
plasma-apply-icontheme Papirus-Dark
```


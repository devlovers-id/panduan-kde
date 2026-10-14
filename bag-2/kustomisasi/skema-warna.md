# Skema Warna

Skema warna adalah salah satu komponen kustomisasi yang paling cepat mengubah suasana desktop. Ia menentukan warna untuk semua elemen UI, dari latar belakang jendela hingga teks dan tombol.

#### 6.4.1 Apa Itu Skema Warna?

> **Definisi**
>
> Skema warna adalah berkas INI yang mendefinisikan warna RGB untuk berbagai peran semantik dalam antarmuka, seperti “Background Normal”, “Foreground Normal”, “Button Background”, “Selection Background”, dan lainnya. Setiap aplikasi KDE membaca skema warna ini untuk menentukan warna elemen UI-nya.

#### 6.4.2 Struktur Berkas Skema Warna

Berkas skema warna disimpan di `~/.local/share/color-schemes/` atau `/usr/share/color-schemes/`.

```ini
[ColorEffects:Disabled]
Color=56,56,56
ColorAmount=0
ColorEffect=0
ContrastAmount=0.65
ContrastEffect=1
IntensityAmount=0.1
IntensityEffect=2

[ColorEffects:Inactive]
ChangeSelectionColor=true
Color=112,111,110
ColorAmount=0.025
ColorEffect=2
ContrastAmount=0.1
ContrastEffect=2
Enable=true
IntensityAmount=0
IntensityEffect=0

[Colors:Button]
BackgroundAlternate=189,195,199
BackgroundNormal=239,240,241
DecorationFocus=61,174,233
DecorationHover=61,174,233
ForegroundActive=61,174,233
ForegroundInactive=127,140,141
ForegroundLink=41,128,185
ForegroundNegative=218,68,83
ForegroundNeutral=246,116,0
ForegroundNormal=35,38,41
ForegroundPositive=39,174,96
ForegroundVisited=127,140,141

[Colors:Selection]
BackgroundAlternate=29,153,243
BackgroundNormal=61,174,233
DecorationFocus=61,174,233
DecorationHover=61,174,233
ForegroundActive=252,252,252
ForegroundInactive=252,252,252
ForegroundLink=253,188,75
ForegroundNegative=218,68,83
ForegroundNeutral=246,116,0
ForegroundNormal=252,252,252
ForegroundPositive=39,174,96
ForegroundVisited=189,195,199

[Colors:View]
BackgroundAlternate=239,240,241
BackgroundNormal=252,252,252
DecorationFocus=61,174,233
DecorationHover=61,174,233
ForegroundActive=61,174,233
ForegroundInactive=127,140,141
ForegroundLink=41,128,185
ForegroundNegative=218,68,83
ForegroundNeutral=246,116,0
ForegroundNormal=35,38,41
ForegroundPositive=39,174,96
ForegroundVisited=127,140,141

[Colors:Window]
BackgroundAlternate=189,195,199
BackgroundNormal=239,240,241
DecorationFocus=61,174,233
DecorationHover=61,174,233
ForegroundActive=61,174,233
ForegroundInactive=127,140,141
ForegroundLink=41,128,185
ForegroundNegative=218,68,83
ForegroundNeutral=246,116,0
ForegroundNormal=35,38,41
ForegroundPositive=39,174,96
ForegroundVisited=127,140,141

[General]
ColorScheme=BreezeLight
Name=Breeze Light
shadeSortColumn=true

[KDE]
contrast=4
```

#### 6.4.3 Kelompok Warna

| Kelompok                | Deskripsi                                                             |
| ----------------------- | --------------------------------------------------------------------- |
| `Colors:Window`         | Warna untuk latar belakang jendela dan teks di dalamnya               |
| `Colors:View`           | Warna untuk area tampilan seperti daftar berkas, area teks, dan tabel |
| `Colors:Button`         | Warna untuk tombol dan kontrol                                        |
| `Colors:Selection`      | Warna untuk teks yang dipilih dan latar belakang seleksi              |
| `Colors:Tooltip`        | Warna untuk tooltip                                                   |
| `Colors:Complementary`  | Warna komplementer untuk elemen khusus                                |
| `ColorEffects:Disabled` | Efek warna untuk elemen yang dinonaktifkan                            |
| `ColorEffects:Inactive` | Efek warna untuk jendela yang tidak aktif                             |

#### 6.4.4 Peran Warna dalam Setiap Kelompok

| Peran                 | Deskripsi                                              |
| --------------------- | ------------------------------------------------------ |
| `BackgroundNormal`    | Warna latar belakang utama                             |
| `BackgroundAlternate` | Warna latar belakang alternatif untuk baris bergantian |
| `ForegroundNormal`    | Warna teks utama                                       |
| `ForegroundActive`    | Warna untuk elemen aktif                               |
| `ForegroundInactive`  | Warna untuk elemen tidak aktif                         |
| `ForegroundLink`      | Warna untuk hyperlink                                  |
| `ForegroundVisited`   | Warna untuk hyperlink yang sudah dikunjungi            |
| `ForegroundNegative`  | Warna untuk pesan negatif atau error                   |
| `ForegroundNeutral`   | Warna untuk pesan netral atau peringatan               |
| `ForegroundPositive`  | Warna untuk pesan positif atau sukses                  |
| `DecorationFocus`     | Warna untuk dekorasi fokus                             |
| `DecorationHover`     | Warna untuk dekorasi hover                             |

#### 6.4.5 Membuat Skema Warna Kustom

**Melalui System Settings**

{% stepper %}
{% step %}
### Buka Colors

Buka **System Settings → Colors & Themes → Colors**.
{% endstep %}

{% step %}
### Pilih skema sebagai titik awal

Pilih skema yang ada.
{% endstep %}

{% step %}
### Edit skema

Klik **Edit Scheme...**.
{% endstep %}

{% step %}
### Ubah warna

Dialog editor akan muncul dengan tiga tab: Options, Colors, dan Disabled. Ubah warna sesuai keinginan di tab Colors.
{% endstep %}

{% step %}
### Simpan skema

Klik **Save As...** untuk menyimpan skema baru dengan nama kustom.
{% endstep %}
{% endstepper %}

**Melalui Editing Manual**

Untuk membuat skema warna dari awal, buat berkas INI di `~/.local/share/color-schemes/MyColorScheme.colors`:

```ini
[General]
ColorScheme=MyColorScheme
Name=My Color Scheme

[Colors:Window]
BackgroundNormal=45,45,48
ForegroundNormal=239,240,241
DecorationFocus=61,174,233
DecorationHover=61,174,233

[Colors:View]
BackgroundNormal=35,38,41
ForegroundNormal=239,240,241

[Colors:Button]
BackgroundNormal=61,66,70
ForegroundNormal=239,240,241

[Colors:Selection]
BackgroundNormal=61,174,233
ForegroundNormal=252,252,252

[Colors:Tooltip]
BackgroundNormal=35,38,41
ForegroundNormal=239,240,241
```

{% hint style="warning" %}
Saat mengedit berkas skema warna secara manual, pastikan Anda menggunakan format RGB yang benar, yaitu `R,G,B` tanpa spasi. Kesalahan format dapat menyebabkan Plasma gagal memuat skema dan mungkin jatuh ke skema default.
{% endhint %}

#### 6.4.6 Alat Bantu Membuat Skema Warna

Beberapa alat dapat membantu membuat skema warna:

* **KColorSchemeEditor:** Alat GUI untuk mengedit skema warna.
* **Pywal:** Generator skema warna dari gambar, dengan template untuk KDE.
* **Material You Colors:** Generator skema warna berbasis Material Design 3.
* **Kde-material-you-colors:** Implementasi Python dari Material You untuk KDE.


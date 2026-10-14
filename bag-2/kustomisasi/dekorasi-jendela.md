# Dekorasi Jendela

Dekorasi jendela adalah bingkai di sekeliling jendela aplikasi, termasuk judul, tombol minimize, maximize, close, dan border. Di KDE Plasma, dekorasi jendela dapat dibuat dengan dua cara utama: Aurorae berbasis SVG dan KDecoration berbasis C++.

#### 6.6.1 Jenis Dekorasi Jendela

| Jenis       | Deskripsi                                                                                                                                                               |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Aurorae     | Dekorasi berbasis SVG yang dapat dibuat dengan editor grafis seperti Inkscape. Cocok untuk desainer dan pengguna yang ingin membuat dekorasi kustom tanpa menulis kode. |
| KDecoration | Dekorasi berbasis C++ yang lebih canggih dan dapat menyesuaikan perilaku. Cocok untuk pengembang yang ingin kontrol penuh.                                              |
| Built-in    | Dekorasi bawaan seperti Breeze, Oxygen, dan Plastik.                                                                                                                    |

#### 6.6.2 Aurorae: Dekorasi Berbasis SVG

**Struktur Paket Aurorae**

```
MyAuroraeTheme/
|-- metadata.desktop # Metadata (format lama)
|-- aurorae/
|   +-- theme/
|       |-- config.rc # Konfigurasi tema
|       |-- decoration.svg # Dekorasi utama
|       |-- close.svg # Tombol close
|       |-- maximize.svg # Tombol maximize
|       |-- minimize.svg # Tombol minimize
|       |-- restore.svg # Tombol restore
|       +-- ...
+-- LICENSE
```

**Konfigurasi Aurorae**

Berkas `config.rc` mendefinisikan berbagai aspek dekorasi:

```ini
[General]
Animation=0
ButtonSize=1.0
DecorationPosition=0
TitleAlignment=1
TitleVerticalAlignment=1

[Layout]
ButtonHeight=30
ButtonWidth=30
TitleHeight=30
TitleHorizontalMargin=6
TitleVerticalMargin=4

[Buttons]
Close=close
Maximize=maximize
Minimize=minimize
Restore=restore
```

#### 6.6.3 KDecoration: Dekorasi Berbasis C++

KDecoration adalah API C++ untuk membuat dekorasi jendela. Ia menawarkan kontrol penuh atas perilaku dekorasi, termasuk:

* Rendering kustom dengan QPainter atau OpenGL.
* Interaksi kustom dengan judul jendela.
* Animasi dan efek.
* Integrasi dengan pengaturan Plasma.

> **Catatan**
>
> Membuat dekorasi KDecoration memerlukan pengetahuan C++ dan pemahaman tentang arsitektur KWin. Jika Anda baru memulai, Aurorae adalah titik awal yang lebih baik karena tidak memerlukan kompilasi kode.

#### 6.6.4 Klassy: Dekorasi Jendela Modern

Klassy adalah dekorasi jendela yang sangat dapat dikustomisasi dan populer di komunitas KDE Plasma. Ia menyediakan:

* Tombol yang dapat dikonfigurasi: ukuran, bentuk, transparansi, dan warna.
* Sudut jendela yang dapat disesuaikan: rounded atau sharp.
* Bayangan dan highlight yang dapat dikonfigurasi.
* Integrasi dengan Global Theme.
* Dukungan mode terang dan gelap.

**Memasang Klassy**

```bash
# Arch Linux (AUR)
yay -S klassy

# openSUSE
sudo zypper install klassy

# Fedora
sudo dnf install klassy

# Ubuntu/Debian
sudo apt install klassy

# Setelah instalasi, pilih Klassy di:
# System Settings -> Appearance -> Window Decorations
```

{% hint style="info" %}
Klassy juga menyediakan Application Style dan Icons yang cocok dengan dekorasi jendelanya. Untuk pengalaman yang paling konsisten, terapkan semua komponen Klassy melalui Klassy Settings.
{% endhint %}


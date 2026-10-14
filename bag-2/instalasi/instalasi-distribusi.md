# Instalasi di Berbagai Distribusi

Prosedur instalasi KDE Plasma bervariasi tergantung pada distribusi yang Anda gunakan. Bagian ini menyajikan panduan langkah demi langkah untuk beberapa distribusi populer.

#### 4.2.1 Diagram Alur Instalasi Umum

Alur instalasi KDE Plasma secara umum berlaku untuk sebagian besar distribusi:

{% stepper %}
{% step %}
### Perbarui sistem
{% endstep %}

{% step %}
### Instal paket Plasma
{% endstep %}

{% step %}
### Reboot atau lanjut tanpa reboot

Jika diperlukan, reboot sistem.
{% endstep %}

{% step %}
### Login di layar masuk
{% endstep %}

{% step %}
### Pilih sesi Plasma
{% endstep %}
{% endstepper %}

Meskipun detailnya berbeda antar distribusi, langkah-langkkah dasarnya tetap sama.

#### 4.2.2 Ubuntu / Kubuntu

Ubuntu adalah salah satu distribusi paling populer di dunia. Meskipun Ubuntu default menggunakan GNOME, varian resmi Kubuntu menyediakan KDE Plasma sebagai desktop default.

**Instalasi Kubuntu**

Jika Anda menginstal Kubuntu dari awal, KDE Plasma akan otomatis terpasang. Cukup pilih opsi “Kubuntu” di layar instalasi.

**Menambahkan Plasma ke Ubuntu yang Sudah Ada**

Jika Anda sudah menggunakan Ubuntu dengan GNOME dan ingin menambahkan KDE Plasma:

```bash
# 1. Perbarui sistem
sudo apt update && sudo apt upgrade -y

# 2. Instalasi paket dasar Plasma
sudo apt install kde-plasma-desktop -y

# Atau instalasi lengkap (dengan aplikasi KDE)
sudo apt install kubuntu-desktop -y

# 3. Reboot sistem
sudo reboot
```

Setelah reboot, Anda akan melihat opsi untuk memilih sesi “Plasma (Wayland)” atau “Plasma (X11)” di layar login.

{% hint style="info" %}
Jika Anda tidak ingin menghapus GNOME, Anda dapat menginstal KDE Plasma berdampingan. Di layar login, Anda dapat memilih sesi yang ingin digunakan. Namun, perhatikan bahwa beberapa aplikasi mungkin muncul dua kali di menu, sekali untuk versi GNOME dan sekali untuk versi KDE.
{% endhint %}

**Paket Tambahan**

| Paket                   | Deskripsi                  |
| ----------------------- | -------------------------- |
| `kde-standard`          | Aplikasi KDE standar       |
| `kde-full`              | Semua aplikasi KDE         |
| `kde-config-*`          | Modul konfigurasi tambahan |
| `plasma-widgets-addons` | Widget tambahan            |
| `kdeplasma-addons`      | Add-on Plasma              |

#### 4.2.3 Fedora KDE Spin

Fedora KDE Spin adalah varian resmi Fedora yang menggunakan KDE Plasma sebagai desktop default. Ia mengikuti siklus rilis Fedora yang cepat, setiap 6 bulan.

**Instalasi Fedora KDE Spin**

{% stepper %}
{% step %}
### Unduh ISO Fedora KDE Spin

Unduh ISO Fedora KDE Spin dari situs resmi Fedora.
{% endstep %}

{% step %}
### Buat USB bootable

Buat USB bootable dengan `dd` atau Fedora Media Writer.
{% endstep %}

{% step %}
### Boot dari USB

Boot dari USB dan ikuti wizard instalasi.
{% endstep %}

{% step %}
### Reboot

Setelah reboot, Anda akan masuk ke sesi KDE Plasma.
{% endstep %}
{% endstepper %}

**Menambahkan Plasma ke Fedora Workstation**

Jika Anda menggunakan Fedora Workstation (GNOME) dan ingin menambahkan KDE Plasma:

```bash
# 1. Perbarui sistem
sudo dnf upgrade --refresh -y

# 2. Instalasi grup KDE Plasma
sudo dnf groupinstall "KDE Plasma Workspaces" -y

# 3. Set display manager ke SDDM (opsional)
sudo systemctl set-default graphical.target
sudo systemctl enable sddm -f

# 4. Reboot
sudo reboot
```

> **Catatan**
>
> Di Fedora, grup “KDE Plasma Workspaces” mencakup KDE Plasma, KWin, dan aplikasi KDE dasar. Untuk instalasi yang lebih lengkap, gunakan grup “KDE Applications”.

#### 4.2.4 openSUSE

openSUSE menyediakan dua varian utama: Leap yang stabil dan Tumbleweed yang menggunakan rolling release. Keduanya menawarkan KDE Plasma sebagai pilihan utama.

**Instalasi openSUSE dengan Plasma**

{% stepper %}
{% step %}
### Unduh ISO openSUSE

Unduh ISO openSUSE dari situs resmi.
{% endstep %}

{% step %}
### Pilih KDE Plasma Desktop

Pada layar pemilihan desktop, pilih “KDE Plasma Desktop”.
{% endstep %}

{% step %}
### Ikuti wizard instalasi
{% endstep %}

{% step %}
### Reboot

Setelah reboot, Anda akan masuk ke sesi KDE Plasma.
{% endstep %}
{% endstepper %}

**Menambahkan Plasma ke openSUSE yang Sudah Ada**

```bash
# 1. Perbarui sistem
sudo zypper refresh
sudo zypper update -y

# 2. Instalasi pola KDE
sudo zypper install -t pattern kde_plasma

# 3. Opsional: instalasi aplikasi KDE
sudo zypper install -t pattern kde_applications

# 4. Reboot
sudo reboot
```

{% hint style="info" %}
openSUSE memiliki alat konfigurasi sistem yang disebut YaST. Setelah menginstal KDE Plasma, Anda dapat menggunakan YaST untuk mengonfigurasi berbagai aspek sistem, termasuk manajemen pengguna, jaringan, dan perangkat keras.
{% endhint %}

#### 4.2.5 Arch Linux

Arch Linux adalah distribusi rolling release yang memberikan kontrol penuh kepada pengguna. Ia tidak menyertakan KDE Plasma secara default, tetapi menyediakan paket-paket yang diperlukan.

**Instalasi Plasma di Arch Linux**

```bash
# 1. Perbarui sistem
sudo pacman -Syu

# 2. Instalasi paket Plasma
sudo pacman -S plasma

# 3. Instalasi aplikasi KDE (opsional)
sudo pacman -S kde-applications

# 4. Instalasi SDDM (display manager)
sudo pacman -S sddm

# 5. Aktifkan SDDM
sudo systemctl enable sddm

# 6. Reboot
sudo reboot
```

{% hint style="warning" %}
Arch Linux adalah distribusi yang ditujukan untuk pengguna tingkat lanjut. Instalasi manual memerlukan pemahaman tentang partisi disk, bootloader, dan konfigurasi sistem. Jika Anda baru mengenal Linux, pertimbangkan untuk menggunakan distribusi yang lebih ramah pengguna seperti Kubuntu atau openSUSE terlebih dahulu.
{% endhint %}

**Paket Tambahan di Arch**

| Paket                   | Deskripsi                               |
| ----------------------- | --------------------------------------- |
| `plasma`                | Paket dasar Plasma                      |
| `plasma-meta`           | Meta-paket dengan semua komponen Plasma |
| `kde-applications`      | Semua aplikasi KDE                      |
| `kde-applications-meta` | Meta-paket aplikasi KDE                 |
| `sddm`                  | Simple Desktop Display Manager          |
| `kdeconnect`            | Integrasi ponsel-desktop                |

#### 4.2.6 FreeBSD

FreeBSD adalah sistem operasi mirip Unix yang mendukung KDE Plasma melalui port `x11/kde`. Meskipun bukan Linux, FreeBSD menyediakan pengalaman KDE Plasma yang lengkap.

**Instalasi Plasma di FreeBSD**

```bash
# 1. Perbarui koleksi port
sudo pkg update

# 2. Instalasi meta-paket lengkap
sudo pkg install kde

# Atau instalasi minimal
sudo pkg install plasma6-plasma

# 3. Konfigurasi D-Bus
sudo sysrc dbus_enable="YES"

# 4. Instalasi dan aktifkan SDDM
sudo pkg install sddm
sudo sysrc sddm_enable="YES"

# 5. Reboot
sudo reboot
```

> **Catatan**
>
> Plasma di FreeBSD menggunakan `dbus-daemon` sebagai message bus dan abstraksi perangkat keras. Aplikasi ini otomatis terinstal sebagai dependensi Plasma. Pastikan layanan `dbus` diaktifkan sebelum memulai sesi Plasma.

#### 4.2.7 Distribusi Lain

Selain distribusi yang dibahas di atas, KDE Plasma juga tersedia di:

* **Manjaro KDE:** Distribusi berbasis Arch Linux dengan KDE Plasma yang telah dikonfigurasi sebelumnya.
* **KDE Neon:** Distribusi khusus yang menyediakan versi terbaru KDE Plasma dan KDE Frameworks.
* **Debian:** Menyediakan paket `kde-plasma-desktop` di repositori utama.
* **Linux Mint:** Menyediakan varian KDE melalui edisi khusus, meskipun tidak lagi menjadi fokus utama.
* **Gentoo:** Menyediakan ebuild untuk KDE Plasma melalui overlay `kde`.
* **Alpine Linux:** Menyediakan paket `plasma` di repositori komunitas.
* **Void Linux:** Menyediakan paket `plasma-desktop`.


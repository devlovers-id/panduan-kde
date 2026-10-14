# Prasyarat

Sebelum memulai pengembangan, Anda perlu menyiapkan lingkungan yang tepat. Bagian ini menuntun Anda melalui persiapan tersebut.

#### 7.2.1 Pengetahuan yang Diperlukan

Untuk mengikuti bab ini, Anda sebaiknya memiliki:

* Pemahaman dasar tentang pemrograman (variabel, fungsi, objek).
* Familiaritas dengan command line (bash, terminal).
* Pemahaman dasar tentang Git (clone, commit, push).
* Kemampuan membaca dokumentasi teknis dalam bahasa Inggris.

Tidak diperlukan pengetahuan sebelumnya tentang QML atau Qt, karena kita akan mempelajarinya dari awal.

#### 7.2.2 Instalasi Paket Pengembangan

Langkah pertama adalah menginstal paket-paket pengembangan yang diperlukan. Perintahnya bervariasi antar distribusi:

```bash
# Arch Linux
sudo pacman -S --needed base-devel cmake extra-cmake-modules \
    qt6-tools qt6-declarative plasma-framework kpackage

# Ubuntu / Debian
sudo apt install build-essential cmake extra-cmake-modules \
    qt6-tools-dev qt6-declarative-dev libkf6plasma-dev \
    libkf6package-dev

# Fedora
sudo dnf install gcc-c++ cmake extra-cmake-modules \
    qt6-qtbase-devel qt6-qtdeclarative-devel \
    kf6-plasma-devel kf6-kpackage-devel

# openSUSE
sudo zypper install gcc-c++ cmake extra-cmake-modules \
    qt6-tools-devel qt6-declarative-devel \
    kf6-plasma-devel kf6-kpackage-devel
```

{% hint style="info" %}
Paket-paket di atas adalah untuk Plasma 6 dan KDE Frameworks 6. Jika Anda masih menggunakan Plasma 5, ganti `qt6-*` dengan `qt5-*` dan `kf6-*` dengan `kf5-*`.
{% endhint %}

#### 7.2.3 Verifikasi Lingkungan

Setelah instalasi, verifikasi bahwa semua alat tersedia:

```bash
# Periksa versi CMake
cmake --version
# Harus menampilkan CMake 3.16 atau lebih tinggi

# Periksa versi Qt
qmake6 --version
# Harus menampilkan Qt 6.x

# Periksa ECM
ecm_version=$(pkg-config --modversion ecm 2>/dev/null || echo "tidak ditemukan")
echo "ECM: $ecm_version"

# Periksa plasmoidviewer
which plasmoidviewer
# Harus menampilkan path ke plasmoidviewer

# Periksa kpackagetool6
which kpackagetool6
# Harus menampilkan path ke kpackagetool6
```

{% hint style="warning" %}
Jika ada alat yang tidak ditemukan, periksa kembali nama paket di distribusi Anda. Beberapa distribusi mungkin menggunakan nama paket yang sedikit berbeda. Konsultasikan dokumentasi distribusi Anda untuk informasi lebih lanjut.
{% endhint %}

#### 7.2.4 Struktur Direktori Kerja

Buat struktur direktori untuk proyek pengembangan Anda:

```bash
# Buat direktori kerja
mkdir -p ~/kde-dev
cd ~/kde-dev

# Buat subdirektori untuk berbagai proyek
mkdir -p widgets # Untuk pengembangan widget
mkdir -p kcm # Untuk modul konfigurasi
mkdir -p runners # Untuk KRunner plugins
mkdir -p kwin-scripts # Untuk KWin scripts

# Clone repositori referensi (opsional)
git clone https://invent.kde.org/plasma/plasma-framework.git
git clone https://invent.kde.org/plasma/kdeplasma-addons.git
```

{% hint style="info" %}
Mengkloning repositori referensi seperti kdeplasma-addons sangat berguna untuk mempelajari kode widget yang sudah ada. Anda dapat melihat bagaimana widget seperti Weather, Notes, dan lainnya diimplementasikan.
{% endhint %}


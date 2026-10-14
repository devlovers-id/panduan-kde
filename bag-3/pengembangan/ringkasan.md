# Ringkasan Bab

Bab ini telah membahas pengembangan KDE Plasma secara menyeluruh:

* **Ekosistem pengembangan:** KDE Plasma dikembangkan dengan QML (UI), JavaScript (logika QML), C++ (logika berat), dan CMake (build system). Alat utama meliputi KDevelop, Qt Creator, dan plasmoidviewer.
* **Prasyarat:** Memerlukan pemahaman dasar pemrograman, dan paket pengembangan yang sesuai dengan distribusi Anda.
* **Struktur proyek widget:** Terdiri atas metadata.json, main.qml, CMakeLists.txt, dan berkas pendukung.
* **CMakeLists.txt:** Melalui makro `plasma_install_package`, mengatur build dan instalasi widget.
* **Plugin QML C++:** Memungkinkan ekspos kelas C++ ke QML untuk fungsionalitas tingkat lanjut.
* **Contoh Mediaframe:** Menunjukkan bagaimana widget dengan plugin C++ diimplementasikan dalam kdeplasma-addons.
* **Pengembangan KCM:** Modul konfigurasi dibangun dengan KPackage, KConfigXT, dan QML/Kirigami.
* **Sumber daya pengembangan:** Dokumentasi resmi, tutorial, repositori referensi, dan komunitas.
* **Studi kasus:** Langkah-langkah lengkap untuk membangun widget dari nol, dari membuat struktur proyek hingga menerbitkan ke KDE Store.

Bab selanjutnya akan membahas fitur terbaru Plasma 6.x, termasuk modul baru seperti Plasma Login Manager, Plasma-Keyboard, dan fitur-fitur inovatif lainnya yang diperkenalkan pada tahun 2026.


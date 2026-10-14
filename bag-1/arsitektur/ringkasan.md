# Ringkasan Bab

Bab ini telah membahas arsitektur dan komponen KDE Plasma secara mendalam:

* KDE Plasma adalah kumpulan komponen modular yang bekerja sama melalui antarmuka yang terdefinisi dengan baik. Setiap lapisan hanya bergantung pada lapisan di bawahnya.
* Plasma Shell mengelola Corona, Containment, dan Plasmoid. Setiap Corona mewakili satu layar, dan setiap Containment adalah wadah untuk Plasmoid.
* KWin adalah manajer jendela dan kompositor dengan fitur-fitur canggih seperti efek desktop, snapping, dan dukungan Wayland yang matang.
* KDE Frameworks adalah kumpulan lebih dari 80 pustaka yang dikelompokkan menjadi empat tier berdasarkan dependensinya.
* `libplasma` menyediakan fondasi untuk Plasma Shell, dengan integrasi QML yang kuat untuk UI.
* Wayland vs X11: Plasma 6 menggunakan Wayland sebagai default, dengan XWayland untuk kompatibilitas aplikasi lama.
* Multi-layar: Plasma memiliki dukungan multi-layar yang kuat, termasuk virtual desktop per layar di Plasma 6.7+.

Bab selanjutnya akan membahas instalasi KDE Plasma di berbagai distribusi, termasuk panduan langkah demi langkah, persyaratan sistem, dan studi kasus migrasi dari lingkungan desktop lain.


# Era KDE 3 dan Transisi

Sebelum Plasma lahir, KDE telah menjadi salah satu lingkungan desktop paling populer di dunia Linux selama bertahun-tahun. Untuk memahami mengapa Plasma diciptakan, kita harus terlebih dahulu memahami apa yang digantikannya.

#### 2.1.1 KDE 3: Puncak Paradigma Tradisional

KDE 3 pertama kali dirilis pada 3 April 2002 sebagai bagian dari proyek KDE yang telah dimulai sejak 1996. Ia dengan cepat menjadi lingkungan desktop default bagi banyak distribusi Linux populer pada masanya, termasuk SuSE, Mandrake, dan Knoppix. Pada puncak kejayaannya, KDE 3 digunakan oleh jutaan pengguna di seluruh dunia.

{% hint style="info" %}
**Definisi**

KDE 3 adalah lingkungan desktop yang dibangun di atas Qt 3 dan KDE Libraries 3. Ia menggunakan paradigma desktop tradisional: panel di bawah, menu aplikasi K-Menu di kiri, dan ikon desktop. Setiap komponen—panel, menu, wallpaper—memiliki kode yang terpisah, membuat kustomisasi mendalam sulit dilakukan tanpa menulis kode C++.
{% endhint %}

Arsitektur KDE 3 mencerminkan filosofi yang berbeda dari Plasma modern. Panelnya (`kicker`) adalah aplikasi mandiri yang tidak dapat digantikan tanpa mengompilasi ulang. Menu utamanya (`kmenu`) memiliki struktur yang tetap. Ikon desktop dikelola oleh `kdesktop`. Tidak ada konsep “widget” yang dapat dipindahkan secara bebas; setiap elemen memiliki tempat dan perannya masing-masing.

{% hint style="info" %}
**Catatan**

Meskipun terdengar kaku, arsitektur KDE 3 sebenarnya sangat maju pada masanya. Ia menyediakan DCOP (_Desktop Communication Protocol_) untuk komunikasi antar-aplikasi, KIO untuk akses jaringan yang transparan, dan Kparts untuk komponen yang dapat digunakan ulang. Banyak dari inovasi ini bertahan hingga hari ini.
{% endhint %}

#### 2.1.2 Keterbatasan yang Memicu Perubahan

Menjelang pertengahan dekade 2000-an, tim KDE mulai merasakan keterbatasan arsitektur KDE 3. Beberapa faktor mendorong kebutuhan akan perubahan mendasar:

1. **Ketergantungan pada Qt 3.** Qt 3 memiliki banyak keterbatasan teknis: rendering grafis yang tidak akselerasi, dukungan Unicode yang tidak konsisten, dan arsitektur yang tidak modular. Trolltech (pengembang Qt) sedang mengerjakan Qt 4 dengan perubahan besar, dan KDE harus mengikutinya.
2. **Panel yang tidak fleksibel.** Pengguna menginginkan kemampuan untuk memindahkan panel, menambahkan widget ke desktop, dan mengubah tata letak secara dinamis. Arsitektur KDE 3 tidak mendukung hal ini tanpa penulisan ulang besar-besaran.
3. **Kompetisi dengan GNOME.** GNOME 2, yang dirilis pada 2002, memiliki arsitektur yang lebih modular dan desain yang lebih konsisten. KDE perlu merespons untuk tetap kompetitif.
4. **Visi “desktop yang hidup”.** Para desainer KDE membayangkan desktop yang tidak statis, melainkan dapat beradaptasi dengan konteks pengguna. Ini membutuhkan arsitektur yang berbeda secara fundamental.

#### 2.1.3 Keputusan untuk Melakukan Terobosan

Pada tahun 2005, pada pertemuan KDE di Akademy, tim pengembang KDE memutuskan untuk melakukan penulisan ulang besar-besaran. Proyek ini diberi nama kode “Project Silk” dan kemudian menjadi KDE 4. Bagian paling ambisius dari proyek ini adalah komponen yang akan menggantikan panel dan desktop tradisional: Plasma.

{% hint style="success" %}
**Tips**

Nama “Plasma” dipilih setelah diskusi panjang. Ia dipilih karena sifatnya yang cair—seperti plasma dalam fisika—dan karena kemampuannya beradaptasi dengan berbagai bentuk wadah. Ini mencerminkan visi bahwa desktop harus dapat berubah bentuk sesuai kebutuhan pengguna.
{% endhint %}


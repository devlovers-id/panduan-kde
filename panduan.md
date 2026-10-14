# Panduan





## Bagian I

## Fondasi

## 1 Pendahuluan

> “Kebebasan bukan sekadar memiliki pilihan, tetapi memiliki pilihan yang benar-benar dapat diubah.”
>
> — Anonim, dikutip dalam diskusi desain KDE

Bab ini memperkenalkan KDE Plasma secara menyeluruh: apa itu, mengapa ia ada, dan mengapa jutaan pengguna di seluruh dunia memilihnya sebagai lingkungan desktop harian mereka. Kita akan menelusuri filosofi yang mendasarinya, ekosistem yang menaunginya, serta posisinya di antara lingkungan desktop lain di dunia Linux dan sistem operasi mirip Unix.

### 1.1 Apa Itu KDE Plasma?

KDE Plasma adalah antarmuka pengguna inti untuk desktop yang dikembangkan oleh proyek KDE. Ia merupakan lingkungan desktop gratis untuk sistem operasi mirip Unix seperti Linux dan FreeBSD. Plasma pertama kali diperkenalkan pada tahun 2008 sebagai bagian dari KDE Software Compilation 4, menggantikan lingkungan desktop KDE 3 dengan konsep baru yang lebih fleksibel dan dapat diperluas.

{% hint style="info" %}
**Definisi**

KDE Plasma adalah desktop shell yang mengelola panel, widget, desktop, dan interaksi pengguna dalam ekosistem KDE. Ia bukan sekadar “desktop environment” dalam pengertian tradisional, melainkan sebuah platform yang dapat diperluas dengan widget, tema, dan modul konfigurasi.
{% endhint %}

#### 1.1.1 Shell, Workspace, dan Desktop Environment

Untuk memahami posisi KDE Plasma secara tepat, penting untuk membedakan tiga istilah yang sering digunakan secara bergantian namun memiliki makna teknis yang berbeda:

**Desktop Environment**

Keseluruhan lingkungan grafis yang mencakup shell, manajer jendela, panel, widget, aplikasi inti, dan integrasi sistem.

**Shell**

Lapisan antarmuka yang mengelola panel, widget, desktop, dan interaksi langsung dengan pengguna. Pada KDE Plasma, shell diimplementasikan oleh `plasmashell`.

**Workspace**

Kumpulan komponen yang membentuk ruang kerja, termasuk manajer jendela (KWin), manajemen daya, integrasi perangkat keras, dan layanan sistem lainnya.

Dalam arsitektur KDE Plasma, shell dan workspace dipisahkan secara jelas. Pemisahan ini memungkinkan KDE Plasma untuk berjalan di atas berbagai manajer jendela (meskipun KWin adalah default) dan memungkinkan komponen-komponennya dikembangkan secara independen oleh tim yang berbeda.

#### 1.1.2 Posisi dalam Tumpukan Perangkat Lunak

Secara vertikal, KDE Plasma berada di antara Qt (kerangka kerja aplikasi) dan aplikasi pengguna. Gambar [1.1](panduan.md#4%5F1%5FPendahuluan) menunjukkan posisi ini secara skematis.

| Lapisan           | Komponen                            |
| ----------------- | ----------------------------------- |
| Lapisan pengguna  | Aplikasi KDE & Pihak Ketiga         |
| Shell & workspace | Plasma Shell (`plasmashell`)        |
|                   | KWin (Manajer Jendela & Kompositor) |
| Pustaka           | KDE Frameworks                      |
|                   | Qt 6                                |
| Sistem            | Kernel Linux / FreeBSD              |

_Gambar 1.1: Posisi KDE Plasma dalam tumpukan perangkat lunak. Setiap lapisan bergantung pada lapisan di bawahnya, namun antarmuka di antara lapisan-lapisan ini dirancang agar tetap stabil sehingga komponen dapat dikembangkan secara independen._

Gambar [1.1](panduan.md#4%5F1%5FPendahuluan) menegaskan bahwa KDE Plasma bukanlah monolit. Ia adalah kumpulan lapisan yang saling bergantung melalui antarmuka yang terdefinisi dengan baik. Inilah yang memungkinkan KDE Plasma untuk terus berevolusi dari KDE 4 ke Plasma 5, dan dari Plasma 5 ke Plasma 6, tanpa harus menulis ulang seluruh sistem.

#### 1.1.3 Mengapa Namanya “Plasma”?

Nama “Plasma” dipilih pada tahun 2008 sebagai metafora untuk sifatnya yang cair dan dapat berubah bentuk. Seperti plasma dalam fisika yang dapat mengambil bentuk wadahnya, KDE Plasma dapat beradaptasi dengan berbagai faktor bentuk: desktop tradisional, tablet, perangkat layar sentuh, hingga pusat media. Filosofi ini tercermin dalam desainnya yang modular dan kemampuannya menyesuaikan tata letak berdasarkan ukuran layar dan perangkat masukan.

{% hint style="info" %}
**Catatan**

Meskipun nama “Plasma” terdengar futuristik, filosofinya sangat praktis: pengguna harus dapat membentuk lingkungan komputasi mereka sesuka hati. Inilah yang membedakan KDE Plasma dari lingkungan desktop yang lebih “opiniated” seperti GNOME.
{% endhint %}

### 1.2 Filosofi dan Prinsip

KDE Plasma dibangun di atas prinsip bahwa pengguna adalah raja. Tidak puas dengan skema warna? Ubah! Ingin panel di tepi kiri layar? Pindahkan! Tidak suka fontnya? Gunakan yang lain! Unduh widget khusus dengan satu klik dan tambahkan ke desktop atau panel.

#### 1.2.1 Lima Prinsip Inti

Filosofi ini diterjemahkan menjadi lima prinsip konkret yang memandu setiap keputusan desain dalam KDE Plasma:

1. **Kebebasan Konfigurasi.** Hampir setiap elemen antarmuka—dari ukuran ikon hingga posisi panel, dari perilaku klik hingga animasi transisi—dapat diubah melalui antarmuka grafis tanpa perlu mengedit berkas konfigurasi.
2. **Konsistensi.** Meskipun sangat dapat dikustomisasi, aplikasi KDE tetap berbagi bahasa desain yang sama: Kirigami untuk UI adaptif, Breeze untuk ikon default, dan KDE Frameworks untuk perilaku yang konsisten.
3. **Aksesibilitas.** KDE Plasma menyediakan dukungan kelas satu untuk pengguna dengan kebutuhan khusus: pembaca layar, kontras tinggi, navigasi keyboard penuh, dan pengaturan untuk epilepsi fotosensitif.
4. **Internasionalisasi.** Antarmuka KDE Plasma tersedia dalam lebih dari 70 bahasa, dengan dukungan penuh untuk arah teks kanan-ke-kiri dan tata bahasa yang kompleks.
5. **Kinerja.** Meskipun kaya fitur, KDE Plasma dirancang agar tetap ringan. Plasma 6, misalnya, menggunakan CPU lebih sedikit dibanding Plasma 5 pada perangkat keras yang sama, berkat optimalisasi di Qt 6 dan KWin.

#### 1.2.2 Kebebasan yang Bertanggung Jawab

Kebebasan konfigurasi bukan berarti tanpa batas. Komunitas KDE menerapkan sejumlah prinsip desain untuk memastikan bahwa kustomisasi tidak mengorbankan kegunaan:

* **Default yang masuk akal.** Meskipun semua dapat diubah, pengaturan default KDE Plasma dirancang agar langsung dapat digunakan oleh sebagian besar pengguna.
* **Kompatibilitas mundur.** Ketika fitur baru ditambahkan, upaya terbaik dilakukan untuk tetap mendukung tema dan widget lama, meskipun kadang diperlukan adaptasi (seperti migrasi `metadata.desktop` ke `metadata.json` di Plasma 6).
* **Dokumentasi.** Setiap opsi konfigurasi didokumentasikan secara resmi, dengan referensi silang antara antarmuka grafis dan berkas konfigurasi di baliknya.

{% hint style="success" %}
**Tips**

Jika Anda baru mengenal KDE Plasma, jangan langsung mengubah segalanya. Gunakan pengaturan default selama satu atau dua minggu, catat apa yang mengganggu Anda, lalu ubah hanya aspek-aspek tersebut. Pendekatan ini menghasilkan lingkungan yang lebih stabil dan personal.
{% endhint %}

#### 1.2.3 Perbandingan Filosofis dengan Lingkungan Desktop Lain

Untuk memahami keunikan filosofi KDE Plasma, penting untuk membandingkannya dengan pendekatan lingkungan desktop lain. Tabel [1.1](panduan.md#6%5F1%5FPendahuluan) merangkum perbedaan utama.

| Aspek              | KDE Plasma                         | GNOME                                |
| ------------------ | ---------------------------------- | ------------------------------------ |
| Filosofi inti      | Kebebasan dan kontrol pengguna     | Kesederhanaan dan fokus              |
| Kustomisasi        | Sangat tinggi, hampir tak terbatas | Terbatas, melalui ekstensi           |
| Tata letak         | Panel bawah, menu klasik           | Overview mode, dock default          |
| Bahasa desain      | Breeze, dapat diganti sepenuhnya   | Adwaita, konsisten ketat             |
| Target pengguna    | Pengguna yang ingin kontrol penuh  | Pengguna yang ingin pengalaman mulus |
| Ekosistem aplikasi | Sangat luas (KDE Applications)     | Terintegrasi (GNOME Core)            |

_Tabel 1.1: Perbandingan filosofis antara KDE Plasma dan GNOME. Keduanya memiliki pendekatan yang berbeda namun saling melengkapi dalam ekosistem Linux._

Perbandingan ini bukan untuk menyatakan bahwa satu pendekatan lebih baik dari yang lain, melainkan untuk menunjukkan bahwa KDE Plasma dan GNOME melayani preferensi pengguna yang berbeda. Banyak pengguna bahkan menginstal keduanya dan memilih sesi yang sesuai dengan konteks kerja mereka.

### 1.3 Mengapa Memilih KDE Plasma?

Ada banyak alasan mengapa pengguna memilih KDE Plasma sebagai lingkungan desktop harian mereka. Bagian ini menguraikan alasan-alasan tersebut secara sistematis, disertai contoh kasus nyata.

#### 1.3.1 Alasan Teknis

1. **Kustomisasi tak terbatas.** Hampir setiap elemen antarmuka dapat diubah: tema, ikon, kursor, font, animasi, pintasan keyboard, tata letak panel, dan bahkan perilaku manajer jendela.
2. **Efisien sumber daya.** Meskipun kaya fitur, KDE Plasma tetap ringan. Pada perangkat dengan RAM 4 GB, Plasma 6 dapat berjalan lancar, sementara lingkungan desktop lain mungkin memerlukan RAM lebih besar.
3. **Dukungan Wayland dan X11.** KDE Plasma 6 menggunakan Wayland sebagai protokol default, namun masih mendukung X11 untuk kompatibilitas aplikasi lama.
4. **Ekosistem aplikasi kaya.** Aplikasi KDE seperti Dolphin, Kate, Konsole, dan Kdenlive terintegrasi erat dengan KDE Plasma.
5. **Stabilitas jangka panjang.** Rilis LTS (_Long Term Support_) seperti Plasma 5.27 dan Plasma 6.x menyediakan siklus pembaruan yang stabil untuk penggunaan produksi.

#### 1.3.2 Alasan Praktis: Studi Kasus

Untuk mengilustrasikan alasan-alasan ini secara konkret, mari kita lihat beberapa studi kasus nyata yang dilaporkan oleh pengguna.

**Kasus 1: Migrasi dari GNOME.** Seorang pengguna yang beralih dari GNOME ke KDE Plasma 6 melaporkan bahwa fitur seperti “kustomisasi panel, drag-and-drop yang benar-benar berfungsi, dan stabilitas shell” adalah fitur yang sangat dinantikan. Pengguna tersebut mencatat bahwa “KDE Plasma 6 membuat kustomisasi tingkat lanjut berbasis GUI dan mengurangi ketergantungan pada dconf atau mengetik perintah arcane.”

**Kasus 2: Penggunaan pada Tablet.** Seorang pengguna yang menguji KDE Plasma pada tablet melaporkan bahwa “Plasma 6 berhasil dengan baik, dengan tweak minimal. Plasma 6 membawa banyak tambahan dan tweak baru, banyak di antaranya meningkatkan pengalaman layar sentuh.” Ini menunjukkan bahwa KDE Plasma tidak hanya untuk desktop tradisional, tetapi juga untuk perangkat sentuh.

**Kasus 3: Pengguna dengan Perangkat Keras Lama.** Seorang pengguna dengan laptop berusia delapan tahun melaporkan bahwa “efek blur di Plasma 6 jauh lebih performan daripada di Plasma 5.” Peningkatan performa ini berasal dari optimalisasi Qt 6 dan KWin yang lebih efisien dalam mengelola komposisi grafis.

{% hint style="success" %}
**Tips**

Jika Anda memiliki perangkat keras lama, aktifkan mode “Low Resource” melalui System Settings Workspace Behavior General Behavior. Mode ini mengurangi animasi dan efek visual untuk meningkatkan responsivitas.
{% endhint %}

#### 1.3.3 Kapan KDE Plasma Mungkin Bukan Pilihan Terbaik

Untuk keseimbangan, penting juga untuk menyebutkan kapan KDE Plasma mungkin bukan pilihan terbaik:

* Jika Anda menginginkan pengalaman yang sepenuhnya konsisten tanpa perlu mengambil keputusan desain, GNOME mungkin lebih cocok.
* Jika Anda menggunakan perangkat keras yang sangat terbatas (RAM di bawah 2 GB), lingkungan desktop yang lebih ringan seperti XFCE atau LXQt mungkin lebih sesuai.
* Jika Anda menginginkan lingkungan desktop yang secara default menyerupai macOS tanpa kustomisasi, Anda perlu mengonfigurasi KDE Plasma terlebih dahulu.

### 1.4 Ekosistem KDE: Lebih dari Sekadar Desktop

KDE Plasma bukanlah proyek yang berdiri sendiri. Ia adalah bagian dari ekosistem KDE yang jauh lebih luas, yang mencakup pustaka, aplikasi, distribusi, dan alat integrasi. Gambar [1.2](panduan.md#8%5F1%5FPendahuluan) menunjukkan ekosistem ini secara skematis.

#### 1.4.1 Komponen Utama Ekosistem

**KDE Frameworks**

Kumpulan lebih dari 80 pustaka yang menyediakan fungsionalitas umum untuk aplikasi KDE. Contohnya termasuk KConfig untuk konfigurasi, KIO untuk I/O, dan KPackage untuk manajemen paket.

**KDE Applications**

Suite aplikasi yang mencakup produktivitas (Kate, Kwrite), multimedia (Kdenlive, Elisa), grafis (Krita, Gwenview), dan utilitas sistem (Dolphin, Konsole).

**KDE Neon**

Distribusi berbasis Ubuntu yang menyediakan versi terbaru KDE Plasma dan KDE Frameworks secara terus-menerus. Cocok untuk pengguna yang ingin mencoba fitur terbaru.

**KDE Connect**

Alat integrasi yang memungkinkan ponsel dan desktop berkomunikasi: berbagi file, mengirim SMS, mengontrol media, dan notifikasi sinkron.

| Komponen pendukung | Komponen ekosistem    |
| ------------------ | --------------------- |
| Qt 6               | KDE Frameworks        |
| Kirigami           | KDE Applications      |
|                    | Distribusi KDE Plasma |
|                    | KDE Store             |
|                    | KDE Neon              |
|                    | KDE Connect           |

_Gambar 1.2: Ekosistem KDE. KDE Plasma berada di pusat, didukung oleh KDE Frameworks, Qt, dan alat terkait, serta diperkaya oleh aplikasi, distribusi, dan komunitas._

**KDE Store**

Pusat distribusi untuk tema, widget, dan add-on yang dibuat komunitas. Diakses langsung melalui System Settings atau Get New Stuff di berbagai aplikasi Plasma.

**Kirigami**

Kerangka kerja UI adaptif yang memungkinkan aplikasi KDE berjalan baik di desktop maupun perangkat mobile dengan kode yang sama.

#### 1.4.2 Mengapa Ekosistem Ini Penting

Ekosistem yang luas memberikan keunggulan kompetitif yang signifikan bagi KDE Plasma:

1. **Integrasi mendalam.** Aplikasi KDE berbagi pustaka dan konvensi yang sama, sehingga terasa menyatu ketika digunakan bersama KDE Plasma.
2. **Inovasi dua arah.** Fitur yang dikembangkan untuk Plasma Mobile dapat mengalir kembali ke KDE Plasma desktop, dan sebaliknya.
3. **Komunitas yang aktif.** Lebih dari 1.800 kontributor terlibat dalam pengembangan KDE, dengan sekitar 20 pengembang baru bergabung setiap bulan.
4. **Keberlanjutan.** Karena banyak organisasi dan individu bergantung pada KDE, proyek ini memiliki keberlanjutan jangka panjang yang terjamin.

{% hint style="info" %}
**Catatan**

Meskipun ekosistem KDE sangat luas, tidak ada keharusan untuk menggunakan semua komponennya. Anda dapat menggunakan KDE Plasma dengan aplikasi GTK, atau menggunakan Dolphin di lingkungan desktop lain. Fleksibilitas adalah inti dari filosofi KDE.
{% endhint %}

### 1.5 Posisi Plasma dalam Lanskap Desktop Linux

Untuk menempatkan KDE Plasma secara tepat, penting untuk memahami lanskap lingkungan desktop Linux secara keseluruhan. Bagian ini membandingkan KDE Plasma dengan lingkungan desktop populer lainnya, serta membahas distribusi yang menyertakannya secara default.

#### 1.5.1 Perbandingan dengan Lingkungan Desktop Lain

Tabel [1.2](panduan.md#an%5Fdesktop%5Fpopuler%5Flainnya%5F%5Fsert) menyajikan perbandingan komprehensif antara KDE Plasma dan lingkungan desktop populer lainnya.

| Aspek            | KDE Plasma    | GNOME         | XFCE      | Cinnamon      |
| ---------------- | ------------- | ------------- | --------- | ------------- |
| Bahasa dasar     | C++/Qt        | C/GTK         | C/GTK     | C/GTK         |
| Kustomisasi      | Sangat tinggi | Terbatas      | Tinggi    | Sedang        |
| RAM (idle)       | ∼600 MB       | ∼800 MB       | ∼400 MB   | ∼700 MB       |
| Dukungan Wayland | Matang        | Matang        | Sebagian  | Eksperimental |
| Target utama     | Fleksibilitas | Kesederhanaan | Ringan    | Familiar      |
| Siklus rilis     | 4 bulan       | 6 bulan       | 2–3 tahun | 6 bulan       |

_Tabel 1.2: Perbandingan KDE Plasma dengan lingkungan desktop populer lainnya. Angka penggunaan RAM bersifat perkiraan dan bervariasi berdasarkan distribusi serta konfigurasi._

Dari tabel ini, terlihat bahwa KDE Plasma menempati posisi unik: ia menawarkan kustomisasi tertinggi di antara lingkungan desktop populer, dengan penggunaan sumber daya yang kompetitif, dan dukungan Wayland yang matang.

#### 1.5.2 Distribusi yang Menggunakan KDE Plasma

KDE Plasma adalah lingkungan desktop default atau pilihan utama untuk beberapa distribusi populer:

**Kubuntu**

Varian resmi Ubuntu dengan KDE Plasma. Menyediakan siklus rilis yang stabil dengan dukungan jangka panjang (LTS).

**openSUSE**

Tumbleweed (_rolling release_) dan Leap (stabil) keduanya menawarkan KDE Plasma sebagai pilihan utama.

**Fedora KDE Spin**

Varian resmi Fedora dengan KDE Plasma. Mengikuti siklus rilis Fedora yang cepat.

**Manjaro KDE**

Distribusi berbasis Arch dengan KDE Plasma yang telah dikonfigurasi sebelumnya.

**Arch Linux**

Menyediakan KDE Plasma melalui paket `plasma`, dengan fleksibilitas penuh bagi pengguna tingkat lanjut.

**FreeBSD**

Menyediakan KDE Plasma melalui port `x11/kde`.

**KDE Neon**

Distribusi khusus yang menyediakan versi terbaru KDE Plasma dan KDE Frameworks.

#### 1.5.3 Studi Kasus: Memilih Distribusi

Seorang pengguna yang ingin beralih ke KDE Plasma mungkin bertanya-tanya distribusi mana yang harus dipilih. Berikut panduan singkat:

* Untuk pengguna baru, Kubuntu LTS atau openSUSE Leap adalah pilihan yang aman.
* Untuk pengguna yang ingin fitur terbaru, Fedora KDE Spin atau KDE Neon adalah pilihan yang baik.
* Untuk pengguna tingkat lanjut, Arch Linux atau openSUSE Tumbleweed menawarkan kontrol penuh.
* Untuk pengguna FreeBSD, port `x11/kde` menyediakan pengalaman KDE Plasma yang lengkap.

{% hint style="warning" %}
**Peringatan**

Meskipun KDE Plasma tersedia di banyak distribusi, pengalaman pengguna dapat bervariasi. Distribusi yang tidak secara aktif menguji KDE Plasma mungkin memiliki bug atau integrasi yang kurang sempurna. Selalu periksa dokumentasi distribusi Anda sebelum melaporkan bug ke pelacak bug KDE.
{% endhint %}

### 1.6 Ringkasan Bab

Bab ini telah memperkenalkan KDE Plasma secara menyeluruh:

* KDE Plasma adalah shell desktop modular yang dikembangkan oleh komunitas KDE, pertama kali dirilis pada 2008.
* Filosofinya berpusat pada kebebasan pengguna, dengan lima prinsip inti: kebebasan konfigurasi, konsistensi, aksesibilitas, internasionalisasi, dan kinerja.
* Alasan memilih KDE Plasma mencakup kustomisasi tak terbatas, efisiensi sumber daya, dukungan Wayland dan X11, serta ekosistem aplikasi yang kaya.
* Ekosistem KDE jauh lebih luas dari sekadar desktop: ia mencakup KDE Frameworks, aplikasi, distribusi, dan alat integrasi seperti KDE Connect.
* Dalam lanskap desktop Linux, KDE Plasma menempati posisi unik sebagai lingkungan desktop dengan kustomisasi tertinggi dan dukungan Wayland yang matang.

Bab selanjutnya akan menelusuri sejarah dan evolusi KDE Plasma, dari KDE 3 hingga Plasma 6, serta pelajaran yang dapat dipetik dari setiap iterasi.

## 2 Sejarah dan Perkembangan

> “Mereka yang tidak dapat mengingat masa lalu ditakdirkan untuk mengulanginya.”
>
> — George Santayana, dikutip dalam refleksi desain KDE

Perjalanan KDE Plasma dari KDE 3 hingga Plasma 6 adalah salah satu kisah paling menarik dalam sejarah perangkat lunak open source. Ia adalah kisah tentang ambisi, kontroversi, kekecewaan, dan akhirnya kematangan. Bab ini menelusuri evolusi tersebut secara kronologis dan tematis, mengungkap mengapa setiap iterasi mengambil bentuk yang ia ambil, apa yang berhasil, dan apa yang tidak. Pemahaman terhadap sejarah ini bukan sekadar pengetahuan tambahan—ia menjelaskan mengapa KDE Plasma hari ini memiliki arsitektur, filosofi, dan budaya pengembangan seperti yang kita kenal.

### 2.1 Era KDE 3 dan Transisi

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

### 2.2 KDE Plasma 4 (2008–2014)

Periode Plasma 4 adalah salah satu periode paling kontroversial dan transformatif dalam sejarah KDE. Ia dimulai dengan janji besar, mengalami masa sulit, dan akhirnya mencapai kematangan yang membuat banyak pengguna kembali.

#### 2.2.1 Kelahiran Plasma 4

Plasma 4 secara resmi diluncurkan pada 11 Januari 2008 sebagai bagian dari KDE 4.0. Peluncuran ini adalah momen yang sangat dinanti-nantikan—dan juga sangat kontroversial.

#### 2.2.2 Arsitektur Plasma 4

Plasma 4 memperkenalkan serangkaian konsep baru yang berbeda secara fundamental dari KDE 3:

**Corona**

Objek `QGraphicsScene` yang mengelola seluruh ruang kerja Plasma. Ia bertanggung jawab atas rendering, _event handling_, dan manajemen _lifecycle_ semua elemen di dalamnya.

**Containment**

Wadah untuk widget. Panel dan desktop adalah contoh-contoh containment. Sebuah containment dapat berisi widget lain dan mengelola tata letaknya.

**Plasmoid**

Aplikasi kecil yang hidup di dalam containment. Contoh: jam, peluncur aplikasi, pemantau sistem. Plasmoid dapat ditulis dalam C++, QML, atau JavaScript.

**Applet**

Kelas C++ yang mendefinisikan perilaku plasmoid. Setiap plasmoid memiliki kelas Applet yang sesuai.

| Tingkat                   | Komponen |
| ------------------------- | -------- |
| Corona (`QGraphicsScene`) |          |
| Containment               | Panel    |
| Containment               | Desktop  |
| Plasmoid                  | Jam      |
| Plasmoid                  | Peluncur |
| Plasmoid                  | Task     |
| Plasmoid                  | Catatan  |
| Plasmoid                  | Folder   |

_Gambar 2.2: Arsitektur Plasma 4. Corona mengelola seluruh ruang kerja, dan berisi satu atau lebih Containment. Setiap Containment berisi Plasmoid yang dapat dipindahkan dan dikonfigurasi._

Gambar [2.2](panduan.md#2002) menunjukkan struktur dasar Plasma 4. Perhatikan bagaimana konsep ini memisahkan antara apa yang ditampilkan (plasmoid) dan di mana ia ditampilkan (containment). Pemisahan ini adalah inovasi kunci yang memungkinkan fleksibilitas yang tidak mungkin dilakukan di KDE 3.

#### 2.2.3 Kontroversi Peluncuran 4.0

Peluncuran KDE 4.0 pada Januari 2008 menuai kritik keras dari komunitas. Banyak pengguna melaporkan:

* Bug yang mengganggu stabilitas, terutama pada plasmoid tertentu.
* Kinerja yang lebih lambat dibanding KDE 3.5.
* Hilangnya fitur yang sebelumnya ada di KDE 3, misalnya beberapa opsi konfigurasi panel.
* Ketidakstabilan driver grafis saat berjalan dengan kompositing.

Kritik ini memuncak dalam apa yang disebut “KDE 4.0 backlash”, di mana banyak pengguna—bahkan beberapa distribusi—memilih untuk tetap menggunakan KDE 3.5 sampai KDE 4 matang. Beberapa distribusi, seperti Debian, menunda adopsi KDE 4 selama beberapa rilis.

{% hint style="warning" %}
**Peringatan**

Pelajaran penting dari peluncuran KDE 4.0: rilis besar dengan perubahan arsitektur mendasar memerlukan waktu untuk matang. Pengguna yang bergantung pada stabilitas sebaiknya menunggu rilis x.1 atau x.2 sebelum bermigrasi.
{% endhint %}

#### 2.2.4 Menuju Kematangan: KDE 4.6 dan Seterusnya

Setelah masa sulit di awal, tim KDE bekerja keras untuk memperbaiki bug dan meningkatkan kinerja. Titik balik terjadi pada:

**KDE 4.2 (Januari 2009)**

Memperkenalkan banyak perbaikan stabilitas dan fitur baru seperti “desktop grid” dan “present windows”.

**KDE 4.4 (Februari 2010)**

Menambahkan dukungan untuk netbook dan layar kecil, serta meningkatkan integrasi NetworkManager.

**KDE 4.6 (Januari 2011)**

Menstabilkan kompositing dan meningkatkan performa KWin secara signifikan.

**KDE 4.10 (Februari 2013)**

Merilis Plasma Workspaces sebagai paket yang lebih modular.

**KDE 4.14 (Agustus 2014)**

Menjadi rilis terakhir dalam siklus Plasma 4 sebelum transisi ke Plasma 5.

{% hint style="info" %}
**Catatan**

Menarik untuk dicatat bahwa banyak pengguna yang awalnya mengkritik KDE 4 kemudian menjadi penggemar beratnya setelah versi 4.6. Perjalanan ini menunjukkan pentingnya kesabaran dan dukungan komunitas dalam proyek open source yang ambisius.
{% endhint %}

#### 2.2.5 Warisan Plasma 4

Meskipun awal yang sulit, Plasma 4 meninggalkan warisan yang signifikan:

1. Konsep plasmoid dan containment menjadi fondasi yang bertahan hingga Plasma 6.
2. Activities diperkenalkan sebagai cara baru mengorganisasi ruang kerja berdasarkan konteks, bukan sekadar virtual desktop.
3. Kompositing default diaktifkan, membuka jalan bagi efek visual yang lebih kaya.
4. Dukungan QML dimulai, memungkinkan pengembangan widget dengan bahasa deklaratif.
5. Arsitektur modular memungkinkan komponen Plasma dikembangkan secara independen.

### 2.3 KDE Plasma 5 (2014–2024)

Jika Plasma 4 adalah masa remaja yang penuh gejolak, Plasma 5 adalah masa kedewasaan. Selama sepuluh tahun masa pengembangannya, Plasma 5 menjadi salah satu lingkungan desktop paling stabil, kaya fitur, dan dihormati di dunia Linux.

#### 2.3.1 Modernisasi Menyeluruh

Plasma 5 diperkenalkan pada 15 Juli 2014 sebagai bagian dari KDE Frameworks 5. Perubahan utama dari Plasma 4 meliputi:

**Migrasi ke Qt 5**

Membawa peningkatan performa, dukungan grafis yang lebih baik, dan API yang lebih modern.

**Migrasi ke KDE Frameworks 5**

Memisahkan pustaka KDE menjadi lebih dari 80 framework modular yang dapat digunakan di luar KDE.

**Tema Breeze baru**

Menggantikan tema Oxygen sebagai default, memberikan tampilan yang lebih modern dan konsisten.

**Arsitektur QML-first**

Plasma 5 dibangun sepenuhnya dengan QML untuk shell, memungkinkan pengembangan widget yang lebih cepat.

**Pemisahan Plasma Workspaces**

Menjadi paket terpisah: `plasma-desktop`, `plasma-netbook`, `plasma-active`, dan lainnya.

| Plasma 4          | Plasma 5            | Plasma 6            |
| ----------------- | ------------------- | ------------------- |
| Qt 4 • KDE Libs 4 | Qt 5 • Frameworks 5 | Qt 6 • Frameworks 6 |
| QGraphicsView     | QML-first           | Wayland default     |

_Gambar 2.3: Transisi besar dalam arsitektur KDE Plasma. Setiap transisi membawa perubahan fundamental pada teknologi yang mendasarinya._

#### 2.3.2 Migrasi ke Qt 5 dan Frameworks 5

Migrasi ke Qt 5 dan KDE Frameworks 5 adalah proyek besar yang memakan waktu bertahun-tahun. Tim KDE harus:

1. Mem-porting semua kode dari Qt 4 ke Qt 5, yang melibatkan ribuan perubahan API.
2. Memisahkan monolitik `kdelibs` menjadi lebih dari 80 framework yang independen.
3. Menulis ulang Plasma Shell dalam QML, menggantikan implementasi C++ yang lama.
4. Memperbarui semua widget dan aplikasi KDE untuk menggunakan API baru.

Proses ini memakan waktu sekitar dua tahun dan melibatkan ratusan kontributor dari seluruh dunia.

#### 2.3.3 Fitur-Fitur Inovatif Plasma 5

Selama masa pengembangannya, Plasma 5 memperkenalkan banyak fitur inovatif:

**Plasma Mobile (2015)**

Varian Plasma untuk perangkat mobile, menunjukkan fleksibilitas arsitektur Plasma.

**KDE Connect (2015)**

Integrasi mendalam antara ponsel dan desktop, memungkinkan berbagi berkas, sinkronisasi notifikasi, dan kontrol media.

**Wayland Support (2016)**

Dukungan awal untuk protokol Wayland, meskipun masih eksperimental pada awalnya.

**HiDPI Support (2017)**

Dukungan untuk layar beresolusi tinggi, dengan scaling otomatis.

**Plasma Vault (2017)**

Fitur enkripsi untuk folder pribadi.

**Night Color (2018)**

Mode malam yang mengurangi cahaya biru.

**Wayland Default (2019)**

Plasma 5.17 mulai menggunakan Wayland sebagai default di beberapa distribusi.

**System Monitor (2021)**

Aplikasi pemantauan sistem baru yang modern.

**Overview Effect (2022)**

Efek “Overview” mirip GNOME, memberikan pengalaman multitasking yang lebih baik.

**HDR Support (2023)**

Dukungan awal untuk HDR (_High Dynamic Range_) di Wayland.

{% hint style="success" %}
**Tips**

Salah satu fitur yang paling dihargai pengguna Plasma 5 adalah Activities. Meskipun konsepnya sudah ada di Plasma 4, implementasinya di Plasma 5 jauh lebih matang dan dapat digunakan secara praktis untuk memisahkan konteks kerja.
{% endhint %}

#### 2.3.4 Evolusi KWin di Plasma 5

KWin mengalami transformasi signifikan selama siklus Plasma 5. Dari manajer jendela X11 tradisional, ia menjadi kompositor Wayland yang matang.

| Versi       | Pencapaian Utama                     | Catatan                       |
| ----------- | ------------------------------------ | ----------------------------- |
| Plasma 5.0  | Porting ke Qt 5, kompositing default | Awal yang stabil              |
| Plasma 5.5  | Dukungan Wayland yang lebih baik     | Masih eksperimental           |
| Plasma 5.9  | Wayland untuk sesi pengujian         | Fitur inti berfungsi          |
| Plasma 5.12 | Fractional scaling di Wayland        | LTS pertama dengan Wayland    |
| Plasma 5.17 | Wayland default di Fedora            | Tonggak penting               |
| Plasma 5.21 | Wayland untuk sesi utama             | Dukungan multi-GPU            |
| Plasma 5.24 | Wayland produksi                     | Sesi default di banyak distro |
| Plasma 5.27 | Wayland stabil sepenuhnya            | Rilis terakhir Plasma 5       |

_Tabel 2.1: Perkembangan dukungan Wayland di KWin selama siklus Plasma 5. Perhatikan bagaimana Wayland berevolusi dari eksperimental menjadi protokol default._

#### 2.3.5 Plasma 5.27: Rilis Terakhir

Plasma 5.27, dirilis pada 14 Februari 2023, adalah rilis terakhir dalam siklus Plasma 5. Ia menerima dukungan jangka panjang (LTS) dan tetap digunakan oleh banyak distribusi hingga hari ini. Fitur-fitur penting dari rilis ini meliputi:

* **Wayland yang stabil:** Dukungan Wayland yang cukup matang untuk penggunaan sehari-hari.
* **Kinerja yang dioptimalkan:** Pengurangan penggunaan CPU dan memori dibanding versi sebelumnya.
* **Peningkatan KWin:** Efek yang lebih halus dan dukungan multi-monitor yang lebih baik.
* **Perbaikan bug:** Ribuan bug yang diperbaiki selama siklus pengembangan.

### 2.4 KDE Plasma 6 (2024–sekarang)

Plasma 6 adalah iterasi terbaru dari KDE Plasma, dibangun di atas Qt 6 dan KDE Frameworks 6. Ia dirilis pada 28 Februari 2024 dan menandai tonggak penting dalam perjalanan KDE.

#### 2.4.1 Persiapan Menuju Plasma 6

Pengembangan Plasma 6 dimulai jauh sebelum peluncurannya. Tim KDE harus:

1. Mem-porting semua kode dari Qt 5 ke Qt 6, yang melibatkan perubahan API yang signifikan.
2. Memperbarui semua KDE Frameworks untuk Qt 6.
3. Menyelesaikan transisi ke Wayland sebagai protokol default.
4. Memodernisasi komponen yang masih menggunakan teknologi lama.
5. Menyediakan jalur migrasi bagi tema dan widget lama.

{% hint style="warning" %}
**Peringatan**

Porting tema dari Plasma 5 ke Plasma 6 memerlukan perhatian khusus. Perubahan format metadata dari `metadata.desktop` ke `metadata.json`, serta perubahan impor QML, berarti banyak tema lama tidak langsung berfungsi. Diperlukan adaptasi manual.
{% endhint %}

#### 2.4.2 Fitur-Fitur Utama Plasma 6

**Qt 6 sebagai fondasi**

Membawa peningkatan performa, rendering yang lebih baik, dan API modern.

**Wayland sebagai default**

Plasma 6 secara default menggunakan Wayland, meskipun X11 masih didukung.

**Floating Panel**

Opsi panel mengambang yang memberikan tampilan lebih modern.

**Plasma Login Manager (PLM)**

Manajer login baru yang menggantikan SDDM secara opsional.

**Plasma-Keyboard**

Keyboard on-screen terintegrasi untuk tablet dan perangkat sentuh.

**Spectacle OCR**

Ekstraksi teks dari screenshot.

**Peningkatan animasi**

Animasi yang lebih halus pada layar ber-refresh rate tinggi.

**Pengaturan sistem yang lebih baik**

Antarmuka yang lebih intuitif dan konsisten.

#### 2.4.3 Plasma 6.0 hingga 6.5

Berikut ringkasan rilis dalam siklus Plasma 6 hingga saat ini:

| Versi      | Tanggal  | Sorotan Utama                                      |
| ---------- | -------- | -------------------------------------------------- |
| Plasma 6.0 | Feb 2024 | Peluncuran Qt 6, Wayland default, floating panel   |
| Plasma 6.1 | Jun 2024 | Peningkatan stabilitas, dukungan HDR               |
| Plasma 6.2 | Okt 2024 | Pengaturan tablet, perbaikan KWin                  |
| Plasma 6.3 | Feb 2025 | Optimasi performa, pengaturan yang lebih baik      |
| Plasma 6.4 | Jun 2025 | Peningkatan Wayland, dukungan perangkat keras baru |
| Plasma 6.5 | Okt 2025 | Perbaikan bug, peningkatan sistem pengaturan       |

_Tabel 2.2: Ringkasan rilis Plasma 6.0 hingga 6.5. Setiap rilis membawa perbaikan dan fitur baru yang meningkatkan pengalaman pengguna._

#### 2.4.4 Plasma 6.6 dan 6.7 (2026)

Pada tahun 2026, Plasma 6 mencapai kematangan lebih lanjut dengan fitur-fitur baru yang signifikan.

**Plasma 6.6 (Februari 2026)**

Plasma 6.6 menghadirkan beberapa modul baru:

* **Plasma Login Manager (PLM):** Manajer login opsional baru yang terintegrasi lebih baik dengan Plasma.
* **Plasma-Keyboard:** Keyboard on-screen terintegrasi untuk tablet dan perangkat sentuh.
* **Plasma-Setup:** Alat konfigurasi awal untuk pengguna baru.
* **Spectacle OCR:** Ekstraksi teks dari screenshot.
* **Wi-Fi via QR Code:** Koneksi Wi-Fi dengan memindai kode QR.
* **Ambient Light Sensor:** Kecerahan layar otomatis berdasarkan cahaya sekitar.
* **Animasi lebih halus pada layar refresh rate tinggi.**

**Plasma 6.7 (Juni 2026)**

Plasma 6.7 membawa fitur-fitur unggulan:

* **Virtual Desktop per Layar:** Setiap monitor dapat memiliki tata letak virtual desktop independen.
* **Toggle Mode Terang/Gelap:** Sakelar cepat untuk beralih antara tema terang dan gelap.
* **Tes Volume Mikrofon:** Fitur baru untuk menguji mikrofon.
* **Kalender Lunar Vietnam:** Dukungan kalender non-Gregorian.
* **“Background Apps” di System Tray:** Menampilkan aplikasi Flatpak yang berjalan di latar belakang.
* **Manajemen Printer yang Lebih Baik:** Ikon printer menunjukkan jumlah tugas aktif.
* **Type-ahead di Desktop:** Mode untuk memilih berkas dengan mengetik di desktop.
* **Kembalinya tema Oxygen dan Air:** Sebagai bagian dari persiapan ulang tahun ke-30 KDE.

{% hint style="info" %}
**Catatan**

Kembalinya tema Oxygen dan Air di Plasma 6.7 adalah bagian dari persiapan ulang tahun ke-30 KDE. Tema-tema klasik ini dihidupkan kembali untuk merayakan warisan KDE, sekaligus menunjukkan komitmen terhadap keberlanjutan dan penghargaan terhadap sejarah.
{% endhint %}

#### 2.4.5 Plasma 6.8 dan 6.9: Arah ke Depan

Peningkatan yang direncanakan untuk rilis mendatang meliputi:

* **Navigasi keyboard yang lebih baik:** Tombol panah di KRunner akan berfungsi lebih intuitif.
* **Thumbnail virtual desktop:** Efek Overview KWin akan menampilkan thumbnail yang lebih “harmonis dan menyenangkan secara visual”.
* **Kontrol kecerahan keyboard backlit:** Keyboard backlit akan terhubung setelah login awal, bukan saat boot.
* **Peningkatan dukungan HDR:** Dukungan HDR yang lebih matang untuk monitor yang mendukung.
* **Optimasi performa:** Pengurangan penggunaan sumber daya lebih lanjut.

### 2.5 Pelajaran dari Evolusi

Setelah menelusuri perjalanan panjang dari KDE 3 hingga Plasma 6, kita dapat menarik beberapa pelajaran penting yang relevan tidak hanya untuk KDE Plasma tetapi juga untuk proyek open source pada umumnya.

#### 2.5.1 Pelajaran Teknis

1. **Arsitektur modular adalah kunci keberlanjutan.** Kemampuan untuk mengganti komponen tanpa menulis ulang seluruh sistem memungkinkan KDE Plasma berevolusi selama lebih dari dua dekade.
2. **Migrasi teknologi besar memerlukan waktu.** Transisi dari Qt 3 ke Qt 4, Qt 4 ke Qt 5, dan Qt 5 ke Qt 6 masing-masing memakan waktu bertahun-tahun.
3. **Kompatibilitas mundur harus dijaga sebisanya.** Meskipun tidak selalu mungkin, upaya untuk tetap mendukung tema dan widget lama menghormati investasi pengguna.
4. **Default yang baik sangat penting.** Meskipun KDE Plasma sangat dapat dikustomisasi, pengaturan defaultnya dirancang agar langsung dapat digunakan.

#### 2.5.2 Pelajaran Sosial

1. **Komunikasi dengan pengguna sangat penting.** Peluncuran KDE 4.0 yang bermasalah menunjukkan pentingnya mengelola ekspektasi pengguna.
2. **Komunitas adalah aset paling berharga.** Tanpa ribuan kontributor, penerjemah, dan penguji, KDE Plasma tidak akan mencapai kematangan seperti sekarang.
3. **Kritik dapat menjadi katalis untuk perbaikan.** Banyak perbaikan penting di Plasma 4 dan Plasma 5 berasal dari umpan balik kritis pengguna.
4. **Kesabaran adalah kebajikan.** Proyek open source yang ambisius memerlukan waktu untuk matang. Pengguna yang sabar sering kali mendapatkan hasil yang lebih baik.

#### 2.5.3 Pelajaran Strategis

1. **Visi jangka panjang harus diimbangi dengan eksekusi bertahap.** KDE memiliki visi besar untuk Plasma, tetapi menerapkannya secara bertahap melalui rilis berturut-turut.
2. **Adopsi teknologi baru harus dilakukan dengan hati-hati.** Migrasi ke Wayland, misalnya, dilakukan secara bertahap selama bertahun-tahun, bukan dalam satu rilis besar.
3. **Fleksibilitas adalah keunggulan kompetitif.** Sementara lingkungan desktop lain memilih pendekatan yang lebih terbatas, KDE Plasma mempertahankan fleksibilitas sebagai nilai inti.
4. **Kolaborasi dengan distribusi sangat penting.** Keberhasilan KDE Plasma bergantung pada adopsi oleh distribusi seperti Fedora, openSUSE, dan Kubuntu.

### 2.6 Ringkasan Bab

Bab ini telah menelusuri perjalanan panjang KDE Plasma dari KDE 3 hingga Plasma 6:

* KDE 3 (2002–2008) adalah puncak paradigma desktop tradisional, tetapi keterbatasan arsitekturnya memicu kebutuhan akan perubahan.
* Plasma 4 (2008–2014) memperkenalkan konsep-konsep inovatif seperti plasmoid dan containment, tetapi mengalami awal yang sulit sebelum akhirnya matang.
* Plasma 5 (2014–2024) adalah masa kedewasaan, dengan migrasi ke Qt 5 dan KDE Frameworks 5, serta dukungan Wayland yang matang.
* Plasma 6 (2024–sekarang) adalah iterasi terbaru, dibangun di atas Qt 6 dengan Wayland sebagai default, serta fitur-fitur baru seperti floating panel dan Plasma-Keyboard.
* Pelajaran dari evolusi mencakup pentingnya arsitektur modular, komunikasi dengan pengguna, dan kesabaran dalam mengadopsi teknologi baru.

Bab selanjutnya akan membahas arsitektur dan komponen KDE Plasma secara mendalam, termasuk bagaimana Plasma Shell, KWin, dan KDE Frameworks bekerja sama untuk menciptakan pengalaman desktop yang koheren.

## 3 Arsitektur dan Komponen

> “Arsitektur yang baik adalah arsitektur yang memungkinkan perubahan tanpa kehancuran.”
>
> — Prinsip desain perangkat lunak

Setelah memahami filosofi dan sejarah KDE Plasma pada dua bab sebelumnya, kini saatnya menyelami bagaimana sistem ini dibangun dari dalam. Bab ini membedah KDE Plasma sebagai sebuah rekayasa perangkat lunak: komponen-komponen apa yang menyusunnya, bagaimana mereka berkomunikasi, dan mengapa keputusan arsitektur tertentu diambil. Pemahaman yang kokoh tentang arsitektur akan menjadi fondasi untuk bab-bab berikutnya tentang instalasi, kustomisasi, dan pengembangan.

### 3.1 Gambaran Umum Tumpukan Perangkat Lunak

KDE Plasma bukanlah monolit tunggal, melainkan kumpulan komponen yang bekerja sama melalui antarmuka yang terdefinisi dengan baik. Memahami tumpukan perangkat lunaknya adalah langkah pertama untuk memahami sistem secara keseluruhan.

#### 3.1.1 Komponen Inti

Tabel [3.1](panduan.md#3%5FArsitektur%5Fdan%5FKomponen) merangkum komponen-komponen inti KDE Plasma beserta peran masing-masing.

| Komponen       | Paket         | Fungsi Utama                                  |
| -------------- | ------------- | --------------------------------------------- |
| Plasma Shell   | `plasmashell` | Menampilkan desktop, panel, dan widget        |
| KWin           | `kwin`        | Manajer jendela dan kompositor grafis         |
| KDE Frameworks | `kf6-*`       | Kumpulan pustaka pendukung                    |
| Qt 6           | `qt6-*`       | Kerangka kerja aplikasi dasar                 |
| KPackage       | `kpackage`    | Sistem paket untuk widget dan tema            |
| KConfig        | `kconfig`     | Manajemen konfigurasi                         |
| KIO            | `kio`         | Abstraksi I/O untuk akses berkas dan jaringan |
| Solid          | `solid`       | Deteksi dan abstraksi perangkat keras         |

_Tabel 3.1: Komponen inti KDE Plasma beserta paket dan fungsinya. Setiap komponen dirancang untuk tujuan spesifik namun terintegrasi melalui antarmuka yang terdefinisi dengan baik._

#### 3.1.2 Diagram Tumpukan

Gambar [3.1](panduan.md#24%5F3%5FArsitektur%5Fdan%5FKomponen) menunjukkan tumpukan perangkat lunak KDE Plasma secara lengkap, dari kernel hingga aplikasi pengguna.

| Lapisan          | Komponen                                                    |
| ---------------- | ----------------------------------------------------------- |
| Pengguna         | Aplikasi KDE & Pihak Ketiga (Qt, GTK, Electron)             |
| Plasma Workspace | Plasma Shell, KWin, System Settings                         |
| Pustaka          | KDE Frameworks 6 (80+ pustaka modular)                      |
| Kerangka kerja   | Qt 6 + Qt Wayland Integration                               |
| Display          | Display Server: Wayland (default) / X11 (opsional)          |
| Hardware         | Hardware Abstraction: `libdrm`, `libinput`, `evdev`, `udev` |
| Sistem           | Kernel Linux / FreeBSD                                      |

_Gambar 3.1: Tumpukan perangkat lunak KDE Plasma secara lengkap. Setiap lapisan bergantung pada lapisan di bawahnya melalui antarmuka yang stabil. Perhatikan posisi Plasma Workspace sebagai lapisan perantara antara KDE Frameworks dan aplikasi pengguna._

Gambar [3.1](panduan.md#24%5F3%5FArsitektur%5Fdan%5FKomponen) mengungkapkan prinsip arsitektur penting: setiap lapisan hanya bergantung pada lapisan di bawahnya, dan antarmuka di antara lapisan-lapisan ini dirancang agar tetap stabil. Prinsip ini memungkinkan KDE Plasma untuk mengganti komponen tanpa harus menulis ulang seluruh sistem—seperti yang terjadi ketika Plasma 5 beralih dari Qt 4 ke Qt 5, dan Plasma 6 beralih dari Qt 5 ke Qt 6.

#### 3.1.3 Prinsip Desain Arsitektur

Arsitektur KDE Plasma dibangun di atas beberapa prinsip desain yang konsisten:

1. **Modularitas.** Setiap komponen dirancang untuk dapat dikembangkan, diuji, dan dirilis secara independen. KDE Frameworks, misalnya, terdiri dari lebih dari 80 pustaka terpisah.
2. **Antarmuka yang stabil.** Meskipun implementasi dapat berubah, antarmuka publik dari setiap komponen dijaga agar tetap kompatibel.
3. **Pemisahan tanggung jawab.** Plasma Shell mengelola antarmuka, KWin mengelola jendela, KIO mengelola I/O. Tidak ada tumpang tindih fungsi.
4. **Konfigurabilitas.** Hampir semua perilaku dapat dikonfigurasi melalui berkas INI yang dapat diedit pengguna.
5. **Asinkronisitas.** Operasi yang memakan waktu (I/O, rendering) dilakukan secara asinkron untuk menjaga responsivitas.

{% hint style="info" %}
**Catatan**

Modularitas KDE Plasma bukan sekadar jargon teknis. Ia memiliki konsekuensi praktis: pengguna dapat mengganti KWin dengan manajer jendela lain, menggunakan Dolphin di lingkungan desktop lain, atau hanya menginstal sebagian dari KDE Frameworks tanpa harus menginstal seluruh ekosistem.
{% endhint %}

### 3.2 Plasma Shell dan Containment

Plasma Shell adalah jantung dari KDE Plasma. Ia bertanggung jawab untuk menampilkan panel, desktop, dan widget, serta mengelola interaksi pengguna dengan elemen-elemen ini.

#### 3.2.1 Arsitektur Plasma Shell

Plasma Shell diimplementasikan oleh perintah `plasmashell`, yang dijalankan sebagai proses pengguna saat sesi dimulai. Ia memuat konfigurasi dari berbagai berkas dan membuat struktur objek yang merepresentasikan tata letak desktop.

{% hint style="info" %}
**Definisi**

Plasma Shell adalah proses yang mengelola satu atau lebih Corona, di mana setiap Corona merepresentasikan satu layar fisik. Di dalam setiap Corona terdapat satu atau lebih Containment Plasmoid, yang bertindak sebagai wadah untuk.
{% endhint %}

Hierarki objek dalam Plasma Shell dapat diringkas sebagai berikut:

* **Plasma Shell** — Proses utama (`plasmashell`)
* **Corona** — Satu per layar fisik; mengelola scene grafis
* **Containment** — Wadah untuk plasmoid; contoh: panel, desktop
* **Plasmoid** — Widget individual; contoh: jam, task manager

#### 3.2.2 Containment dan Plasmoid

Konsep containment dan plasmoid adalah fondasi arsitektur Plasma. Memahami keduanya sangat penting untuk memahami cara kerja KDE Plasma secara keseluruhan.

**Containment**

Containment adalah jenis khusus dari Applet yang dapat berisi Applet lain. Ia mengelola tata letak anak-anaknya dan bertanggung jawab atas _lifecycle_ mereka.

**Panel Containment**

Wadah horizontal atau vertikal yang menampilkan plasmoid dalam tata letak linier. Contoh: panel bawah default.

**Desktop Containment**

Wadah yang menampilkan plasmoid dalam tata letak bebas (_free-form_). Contoh: desktop itu sendiri.

**Activity Containment**

Wadah yang mengelompokkan beberapa containment untuk membentuk Activity.

**Plasmoid**

Plasmoid adalah widget individual yang memberikan fungsionalitas tertentu. Setiap plasmoid memiliki:

* Metadata dalam berkas `metadata.json` (Plasma 6) atau `metadata.desktop` (Plasma 5).
* UI yang ditulis dalam QML.
* Logika yang dapat ditulis dalam QML/JavaScript atau C++.
* Konfigurasi yang disimpan dalam berkas INI.

| Tingkat             | Isi                                      |
| ------------------- | ---------------------------------------- |
| Plasma Shell        |                                          |
| Corona (Layar 1)    | Containment: Panel, Containment: Desktop |
| Corona (Layar 2)    | Containment: Panel, Containment: Desktop |
| Containment panel   | Jam, Peluncur, Task                      |
| Containment desktop | Folder, Catatan                          |

_Gambar 3.2: Hierarki objek dalam Plasma Shell. Satu Plasma Shell mengelola beberapa Corona (satu per layar). Setiap Corona berisi Containment, dan setiap Containment berisi Plasmoid._

#### 3.2.3 Siklus Hidup Plasmoid

Plasmoid memiliki siklus hidup yang terdefinisi dengan baik:

1. **Discovery.** Plasma Shell memindai direktori sistem dan pengguna untuk menemukan plasmoid yang tersedia.
2. **Loading.** Ketika plasmoid ditambahkan ke containment, Plasma memuat metadata-nya dan menginisialisasi QML engine.
3. **Instantiation.** Kelas C++ Applet diinstansiasi, dan komponen QML dibuat.
4. **Running.** Plasmoid berjalan, menerima event, dan memperbarui tampilannya.
5. **Configuration.** Pengguna dapat mengonfigurasi plasmoid melalui dialog konfigurasi.
6. **Destruction.** Ketika plasmoid dihapus dari containment, resource-nya dibersihkan.

{% hint style="success" %}
**Tips**

Untuk melihat plasmoid yang tersedia di sistem Anda, gunakan perintah `plasmoidviewer -l` di terminal. Ini akan menampilkan daftar semua plasmoid yang terinstal beserta lokasinya.
{% endhint %}

#### 3.2.4 Lokasi Berkas Plasma Shell

Konfigurasi dan data Plasma Shell tersimpan di beberapa lokasi standar:

| Lokasi                                      | Konten                                      |
| ------------------------------------------- | ------------------------------------------- |
| `~/.config/plasma-org.kde.plasma-appletsrc` | Konfigurasi plasmoid dan tata letak desktop |
| `~/.config/plasmashellrc`                   | Pengaturan Plasma Shell                     |
| `~/.local/share/plasma/plasmoids/`          | Plasmoid yang diinstal pengguna             |
| `~/.local/share/plasma/desktoptheme/`       | Plasma Style yang diinstal pengguna         |
| `/usr/share/plasma/plasmoids/`              | Plasmoid sistem                             |
| `/usr/share/plasma/desktoptheme/`           | Plasma Style sistem                         |

_Tabel 3.2: Lokasi berkas konfigurasi dan data Plasma Shell. Memahami lokasi ini penting untuk backup, migrasi, dan pemecahan masalah._

### 3.3 KWin: Manajer Jendela dan Kompositor

KWin adalah manajer jendela dan kompositor grafis untuk KDE Plasma. Ia bertanggung jawab untuk mengelola jendela aplikasi, menangani input dari keyboard dan mouse, dan menghasilkan output grafis yang di-render ke layar.

#### 3.3.1 Peran Ganda KWin

KWin memiliki dua peran utama yang dalam lingkungan desktop lain sering dipisahkan:

**Manajer Jendela**

Mengelola posisi, ukuran, dan status jendela. Ia menangani operasi seperti memindahkan, mengubah ukuran, meminimalkan, memaksimalkan, dan menutup jendela.

**Kompositor**

Menggabungkan output dari berbagai jendela menjadi satu gambar akhir yang ditampilkan ke layar. Ia menangani efek visual seperti transparansi, blur, dan animasi.

{% hint style="info" %}
**Catatan**

Peran ganda KWin sebagai manajer jendela dan kompositor bukanlah kebetulan. Ini adalah keputusan desain yang memungkinkan integrasi yang lebih erat antara manajemen jendela dan efek visual. Di X11, kompositor terpisah seperti `xcompmgr` dapat digunakan, tetapi ini memerlukan sinkronisasi yang lebih rumit.
{% endhint %}

#### 3.3.2 Arsitektur KWin

Gambar [3.3](panduan.md#3%5F3%5FKWin%5F%5FManajer%5FJendela%5Fdan%5FKo) menunjukkan arsitektur internal KWin secara skematis.

| Lapisan   | Komponen                                          |
| --------- | ------------------------------------------------- |
| Output    | Wayland / X11 → Framebuffer / GPU Output          |
| Rendering | Scene Graph, OpenGL / Vulkan, QPainter (fallback) |
| Inti      | Workspace, Window, Effects, Rules                 |
| Input     | `libinput` / `evdev` → Keyboard, Mouse, Touch     |

_Gambar 3.3: Arsitektur internal KWin. Setiap lapisan memiliki tanggung jawab yang jelas: input, logika manajemen jendela, rendering grafis, dan output ke display server._

#### 3.3.3 Fitur-Fitur Utama KWin

KWin menyediakan berbagai fitur yang membuatnya menjadi salah satu manajer jendela paling canggih di dunia Linux.

**Efek Desktop**

KWin memiliki sistem efek yang kaya, yang dapat diaktifkan atau dinonaktifkan secara individual:

**Desktop Cube**

Menampilkan desktop sebagai kubus 3D yang dapat diputar.

**Present Windows**

Menampilkan semua jendela sebagai thumbnail untuk pemilihan cepat.

**Overview**

Memberikan tampilan menyeluruh dari semua jendela dan desktop.

**Wobbly Windows**

Memberikan efek “goyang” pada jendela saat dipindahkan.

**Blur**

Memberikan efek blur pada area tertentu di belakang jendela.

**Slide Back**

Menampilkan animasi saat jendela diaktifkan.

**Manajemen Jendela**

**Snapping**

Jendela dapat “menempel” ke tepi layar atau ke jendela lain.

**Tiling**

Jendela dapat disusun dalam tata letak ubin otomatis.

**Window Rules**

Aturan khusus untuk jendela tertentu berdasarkan judul, kelas, atau kriteria lainnya.

**Virtual Desktops**

Dukungan untuk beberapa desktop virtual.

**Activities**

Integrasi dengan Activities Plasma.

**Kompositing**

**Transparency**

Dukungan untuk jendela transparan dan semi-transparan.

**Shadows**

Bayangan di sekeliling jendela.

**Animations**

Animasi untuk _minimize_, _maximize_, _close_, dan lainnya.

**Color Management**

Manajemen warna untuk kalibrasi monitor.

{% hint style="success" %}
**Tips**

Untuk mengakses pengaturan KWin, buka System Settings Window Management KWin Scripts atau Window Rules. Anda juga dapat mengakses pengaturan efek desktop melalui System Settings Workspace Behavior Desktop Effects.
{% endhint %}

#### 3.3.4 KWin Scripts

KWin mendukung ekstensi melalui scripts yang ditulis dalam JavaScript atau QML. Script ini dapat memodifikasi perilaku KWin tanpa harus mengompilasi ulang.

**KWin Scripting API**

Menyediakan akses ke API JavaScript untuk berinteraksi dengan jendela, desktop, dan efek.

**KWin Effects**

Ditulis dalam C++ dan diintegrasikan lebih dalam dengan sistem rendering.

**KWin Rules**

Konfigurasi deklaratif untuk perilaku jendela tertentu.

#### 3.3.5 Wayland dan X11 di KWin

KWin mendukung dua protokol display server:

| Aspek              | X11                                   | Wayland                        |
| ------------------ | ------------------------------------- | ------------------------------ |
| Status di Plasma 6 | Opsional (_fallback_)                 | Default                        |
| Keamanan           | Aplikasi dapat mengakses input global | Isolasi antar aplikasi         |
| Rendering          | Bergantung pada kompositing eksternal | Terintegrasi                   |
| Multi-Monitor      | Dukungan matang                       | Dukungan yang terus berkembang |
| HiDPI              | Perlu konfigurasi manual              | Scaling otomatis               |
| Aplikasi lama      | Kompatibel penuh                      | Memerlukan XWayland            |

_Tabel 3.3: Perbandingan X11 dan Wayland di KWin. Wayland menawarkan keamanan dan integrasi yang lebih baik, tetapi masih ada tantangan untuk kompatibilitas aplikasi lama._

### 3.4 KDE Frameworks

KDE Frameworks adalah kumpulan pustaka yang menyediakan fungsionalitas umum untuk aplikasi KDE dan pihak ketiga. Ia adalah salah satu kontribusi paling signifikan KDE untuk ekosistem open source.

#### 3.4.1 Gambaran Umum

KDE Frameworks terdiri dari lebih dari 80 pustaka yang dikelompokkan menjadi empat tingkatan berdasarkan dependensinya:

| Tier   | Deskripsi                | Contoh                                                     |
| ------ | ------------------------ | ---------------------------------------------------------- |
| Tier 4 | Solusi Siap Pakai        | KHtml, KTextEditor, KCalendarCore                          |
| Tier 3 | Integrasi Desktop        | Plasma (`libplasma`), KRunner, KNotifyConfig, KGlobalAccel |
| Tier 2 | Bergantung pada Tier 1   | KIO, KAuth, KPackage, KCMUtils                             |
| Tier 1 | Bergantung hanya pada Qt | KConfig, KWindowSystem, KCoreAddons, KI18n, Solid          |

_Gambar 3.4: Arsitektur berlapis KDE Frameworks. Setiap tier hanya bergantung pada tier di bawahnya, memastikan bahwa pustaka tingkat rendah dapat digunakan secara independen tanpa menarik dependensi yang tidak perlu._

#### 3.4.2 Pustaka-Pustaka Penting

**KConfig**

KConfig adalah sistem manajemen konfigurasi yang digunakan oleh hampir semua aplikasi KDE. Ia menyediakan:

* API C++ untuk membaca dan menulis konfigurasi.
* Format berkas INI yang dapat dibaca manusia.
* Dukungan untuk grup dan kunci bertingkat.
* Notifikasi perubahan untuk pemantauan waktu-nyata.
* Dukungan untuk notifikasi KDE (`KConfigWatcher`).

Contoh berkas konfigurasi KConfig:

```ini
[General]
ColorScheme=BreezeDark
LookAndFeelPackage=org.kde.breeze.desktop

[KDE]
AnimationDurationFactor=1.0
SingleClick=false

[Icons]
Theme=Papirus-Dark
```

**KIO**

KIO adalah pustaka yang menyediakan abstraksi I/O untuk akses berkas, jaringan, dan protokol lainnya. Ia memungkinkan aplikasi untuk mengakses berbagai sumber daya melalui API yang seragam.

**Protokol**

`file://`, `http://`, `ftp://`, `smb://`, `sftp://`, `mtp://`, dan banyak lagi.

**KIO Jobs**

Operasi asinkron untuk menyalin, memindahkan, menghapus, dan memanipulasi berkas.

**KIO Slaves**

Pekerja yang dijalankan di proses terpisah untuk protokol tertentu.

**KIO Widgets**

Komponen UI siap pakai untuk operasi I/O (_file dialog_, _progress bar_).

**KPackage**

KPackage adalah sistem paket yang digunakan untuk menginstal dan mengelola widget, tema, dan ekstensi lainnya. Ia menyediakan:

* Format paket terdefinisi dengan `metadata.json`.
* Instalasi dan penghapusan paket.
* Manajemen ketergantungan antara paket.
* Dukungan untuk berbagai jenis paket (Plasma Widget, Look and Feel, dan lainnya).

**KWindowSystem**

KWindowSystem menyediakan abstraksi untuk berinteraksi dengan manajer jendela dan sistem windowing:

* API untuk memanipulasi jendela (`minimize`, `maximize`, `close`).
* Deteksi perubahan tata letak layar.
* Integrasi dengan X11 dan Wayland.
* Manajemen virtual desktop.

**Solid**

Solid menyediakan abstraksi untuk perangkat keras:

* Deteksi perangkat keras (disk, jaringan, baterai, dan lainnya).
* Notifikasi perubahan status perangkat.
* API untuk manajemen daya.
* Integrasi dengan `udev` dan UPower.

#### 3.4.3 KDE Frameworks di Luar KDE

Salah satu keunggulan KDE Frameworks adalah dapat digunakan di luar ekosistem KDE. Aplikasi pihak ketiga seperti Krita, Kdenlive, dan bahkan beberapa aplikasi non-KDE menggunakan framework ini.

{% hint style="info" %}
**Catatan**

Karena KDE Frameworks dapat digunakan secara independen, aplikasi tidak perlu menginstal seluruh ekosistem KDE untuk menggunakan satu pustaka. Ini memudahkan integrasi dan mengurangi dependensi yang tidak perlu.
{% endhint %}

### 3.5 Plasma Framework (`libplasma`)

`libplasma` adalah pustaka inti yang menyediakan fondasi untuk Plasma Shell. Ia mengimplementasikan konsep-konsep seperti Corona, Containment, dan Plasmoid dalam bentuk kelas C++.

#### 3.5.1 Arsitektur `libplasma`

`libplasma` terdiri dari beberapa komponen utama:

**`Plasma::Corona`**

Kelas dasar untuk scene grafis yang mengelola seluruh ruang kerja.

**`Plasma::Containment`**

Kelas dasar untuk containment (panel, desktop, activity).

**`Plasma::Applet`**

Kelas dasar untuk plasmoid.

**`Plasma::Theme`**

Manajemen tema dan sumber daya grafis.

**`Plasma::Package`**

Dukungan untuk paket Plasma.

**`Plasma::ConfigLoader`**

Memuat konfigurasi untuk plasmoid.

**PlasmaQuick**

Integrasi dengan QML untuk UI Plasma.

#### 3.5.2 Integrasi dengan QML

Salah satu inovasi penting Plasma 5 dan seterusnya adalah penggunaan QML sebagai bahasa utama untuk UI Plasma. Ini memungkinkan pengembangan widget yang lebih cepat dan lebih fleksibel.

Contoh sederhana plasmoid QML:

```qml
import QtQuick
import org.kde.plasma.plasmoid
import org.kde.plasma.core as PlasmaCore

PlasmoidItem {
    id: root

    preferredRepresentation: fullRepresentation

    fullRepresentation: Item {
        Layout.minimumWidth: 200
        Layout.minimumHeight: 100

        Rectangle {
            anchors.fill: parent
            color: PlasmaCore.Theme.backgroundColor

            Text {
                anchors.centerIn: parent
                text: "Halo, Plasma!"
                color: PlasmaCore.Theme.textColor
            }
        }
    }
}
```

#### 3.5.3 PlasmaQuick

PlasmaQuick adalah jembatan antara `libplasma` (C++) dan QML. Ia menyediakan:

* Tipe QML yang mengekspos kelas `libplasma`.
* Manajemen engine QML untuk Plasma Shell.
* Integrasi dengan sistem tema Plasma.
* Dukungan untuk konfigurasi QML.

{% hint style="success" %}
**Tips**

Jika Anda ingin mengembangkan plasmoid, mulailah dengan template dari repositori `plasma-framework`. Template ini menyediakan struktur dasar proyek dan konfigurasi CMake yang siap digunakan.
{% endhint %}

### 3.6 Arsitektur Wayland vs. X11 dalam Plasma 6

Salah satu perubahan terbesar di Plasma 6 adalah transisi ke Wayland sebagai protokol display default. Memahami perbedaan arsitektur antara Wayland dan X11 sangat penting untuk memahami perilaku Plasma 6.

#### 3.6.1 Perbedaan Fundamental

**X11**

X11 adalah protokol display server yang telah ada sejak tahun 1984. Arsitekturnya berbasis client-server, di mana server X (Xorg) mengelola input dan output grafis, dan klien (aplikasi) berkomunikasi dengan server melalui protokol X11.

**Server X**

Proses tunggal yang mengelola semua input, output, dan window.

**Kompositor**

Proses terpisah (misalnya, `compton`) yang menggabungkan output jendela.

**Manajer Jendela**

Proses terpisah (misalnya, KWin) yang mengelola posisi jendela.

**Keamanan**

Rendah, karena setiap aplikasi dapat mengakses input global dan jendela aplikasi lain.

**Wayland**

Wayland adalah protokol display server modern yang dikembangkan sebagai pengganti X11. Arsitekturnya berbeda secara fundamental:

**Kompositor**

Setiap kompositor (misalnya, KWin) adalah display server lengkap yang mengelola input, output, dan window.

**Tidak ada server X**

Tidak ada proses terpisah yang mengelola seluruh sistem grafis.

**Protokol berbasis objek**

Komunikasi antara aplikasi dan kompositor dilakukan melalui protokol berbasis objek.

**Keamanan**

Tinggi, karena aplikasi tidak dapat mengakses input global atau jendela aplikasi lain tanpa izin.

Gambar [3.5](panduan.md#34%5F3%5FArsitektur%5Fdan%5FKomponen) menunjukkan perbandingan arsitektur kedua protokol.

| Arsitektur X11                     | Arsitektur Wayland                    |
| ---------------------------------- | ------------------------------------- |
| Aplikasi 1, Aplikasi 2, Aplikasi 3 | Aplikasi 1, Aplikasi 2, Aplikasi 3    |
| Server X (Xorg)                    | Kompositor (KWin)                     |
| Kompositor                         | Manajer Jendela • Kompositor • Server |
| Manajer Jendela                    | Kernel / Driver                       |
| Kernel / Driver                    |                                       |

_Gambar 3.5: Perbandingan arsitektur X11 dan Wayland. X11 memerlukan komponen terpisah untuk kompositing dan manajemen jendela, sedangkan Wayland menggabungkan semuanya ke dalam kompositor._

#### 3.6.2 Dampak pada Pengguna

Bagi pengguna, perbedaan arsitektur ini memiliki dampak praktis:

| Aspek            | X11                                   | Wayland                        |
| ---------------- | ------------------------------------- | ------------------------------ |
| Keamanan         | Aplikasi dapat mengambil input global | Setiap aplikasi diisolasi      |
| Performa         | Bergantung pada kompositing           | Rendering lebih efisien        |
| Multi-Monitor    | Dukungan matang                       | Dukungan yang terus berkembang |
| HiDPI Scaling    | Perlu konfigurasi manual              | Scaling otomatis               |
| Screenshot       | Semua aplikasi dapat screenshot       | Izin diperlukan                |
| Keyboard Global  | Berfungsi tanpa izin                  | Memerlukan port khusus         |
| Screen Recording | Berfungsi dengan OBS lama             | Memerlukan PipeWire            |

_Tabel 3.4: Dampak praktis dari perbedaan X11 dan Wayland. Beberapa aplikasi lama mungkin memerlukan penyesuaian untuk bekerja dengan baik di Wayland._

#### 3.6.3 XWayland

Untuk mengatasi kompatibilitas aplikasi lama, Plasma menyediakan XWayland, sebuah server X yang berjalan di dalam sesi Wayland. Aplikasi X11 dapat berjalan melalui XWayland tanpa perlu dimodifikasi.

* XWayland berjalan sebagai klien Wayland di dalam sesi.
* Aplikasi X11 melihat XWayland sebagai server X biasa.
* Kinerja sedikit lebih rendah dibanding aplikasi Wayland native.
* Beberapa fitur, misalnya scaling, mungkin tidak berfungsi sempurna.

{% hint style="info" %}
**Catatan**

Untuk memeriksa apakah aplikasi berjalan melalui XWayland atau Wayland native, gunakan perintah `xlsclients` untuk aplikasi X11, atau periksa variabel lingkungan `WAYLAND_DISPLAY` di dalam aplikasi.
{% endhint %}

### 3.7 Studi Kasus: Bagaimana Plasma Menangani Multi-Layar

Dukungan multi-layar adalah salah satu area di mana KDE Plasma unggul. Bagian ini menyajikan studi kasus tentang bagaimana Plasma menangani konfigurasi multi-layar yang kompleks.

#### 3.7.1 Konsep Dasar

Plasma mengelola konfigurasi multi-layar melalui beberapa konsep:

**Output**

Layar fisik atau virtual yang terhubung ke sistem.

**Corona**

Objek Plasma yang mewakili satu output.

**Screen Layout**

Konfigurasi posisi, resolusi, dan orientasi output.

**Panel per Screen**

Setiap layar dapat memiliki panel sendiri dengan konfigurasi independen.

#### 3.7.2 Contoh Konfigurasi

Seorang pengguna dengan dua monitor dapat mengonfigurasi Plasma sebagai berikut:

* Monitor 1 (kiri): Panel atas dengan global menu, panel bawah dengan task manager.
* Monitor 2 (kanan): Panel bawah dengan system tray dan jam.
* Wallpaper: Berbeda untuk setiap monitor.
* Virtual Desktop: Terpisah untuk setiap monitor (Plasma 6.7+).

#### 3.7.3 Virtual Desktop per Layar (Plasma 6.7+)

Fitur baru di Plasma 6.7 memungkinkan setiap monitor memiliki virtual desktop independen. Ini sangat berguna untuk pengguna yang ingin memisahkan konteks kerja di antara monitor.

| Monitor 1      | Monitor 2        |
| -------------- | ---------------- |
| VD1, VD2, VD3  | VD-A, VD-B, VD-C |
| Panel & Widget | Panel & Widget   |

_Gambar 3.6: Konfigurasi multi-layar dengan virtual desktop per layar (Plasma 6.7+). Setiap monitor dapat memiliki set virtual desktop-nya sendiri, memungkinkan alur kerja yang lebih fleksibel._

#### 3.7.4 Pemecahan Masalah Multi-Layar

Berikut beberapa masalah umum dengan multi-layar dan solusinya:

**Monitor tidak terdeteksi**

Periksa koneksi fisik, jalankan `kscreen-doctor -o` untuk melihat output yang terdeteksi.

**Resolusi salah**

Buka System Settings Display and Monitor dan atur resolusi secara manual.

**Posisi monitor salah**

Atur posisi monitor dengan drag-and-drop di System Settings.

**Panel muncul di monitor yang salah**

Klik kanan panel dan pilih Edit Panel, lalu pindahkan ke monitor yang diinginkan.

{% hint style="success" %}
**Tips**

Untuk menyimpan profil konfigurasi multi-layar yang berbeda, gunakan fitur KScreen di Plasma. Ini memungkinkan Anda menyimpan dan memuat konfigurasi untuk berbagai setup, misalnya di kantor vs. di rumah.
{% endhint %}

### 3.8 Ringkasan Bab

Bab ini telah membahas arsitektur dan komponen KDE Plasma secara mendalam:

* KDE Plasma adalah kumpulan komponen modular yang bekerja sama melalui antarmuka yang terdefinisi dengan baik. Setiap lapisan hanya bergantung pada lapisan di bawahnya.
* Plasma Shell mengelola Corona, Containment, dan Plasmoid. Setiap Corona mewakili satu layar, dan setiap Containment adalah wadah untuk Plasmoid.
* KWin adalah manajer jendela dan kompositor dengan fitur-fitur canggih seperti efek desktop, snapping, dan dukungan Wayland yang matang.
* KDE Frameworks adalah kumpulan lebih dari 80 pustaka yang dikelompokkan menjadi empat tier berdasarkan dependensinya.
* `libplasma` menyediakan fondasi untuk Plasma Shell, dengan integrasi QML yang kuat untuk UI.
* Wayland vs X11: Plasma 6 menggunakan Wayland sebagai default, dengan XWayland untuk kompatibilitas aplikasi lama.
* Multi-layar: Plasma memiliki dukungan multi-layar yang kuat, termasuk virtual desktop per layar di Plasma 6.7+.

Bab selanjutnya akan membahas instalasi KDE Plasma di berbagai distribusi, termasuk panduan langkah demi langkah, persyaratan sistem, dan studi kasus migrasi dari lingkungan desktop lain.

## Bagian II

## Praktik

## 4 Instalasi KDE Plasma

> “Setiap perjalanan besar dimulai dengan satu langkah kecil.”
>
> — Lao Tzu, dikutip dalam konteks instalasi perangkat lunak

Setelah memahami filosofi, sejarah, dan arsitektur KDE Plasma, kini saatnya membawa teori ke praktik. Bab ini menuntun Anda melalui proses instalasi KDE Plasma di berbagai distribusi Linux dan sistem operasi mirip Unix. Kita akan membahas persyaratan sistem, prosedur instalasi langkah demi langkah, konfigurasi awal, hingga studi kasus migrasi dari lingkungan desktop lain. Baik Anda pengguna baru yang baru pertama kali mencoba KDE Plasma, maupun administrator sistem yang mengelola deployment skala besar, bab ini menyediakan panduan yang dapat diandalkan.

### 4.1 Persyaratan Sistem

Sebelum memulai instalasi, penting untuk memastikan bahwa perangkat keras Anda memenuhi persyaratan minimum KDE Plasma. Meskipun KDE Plasma relatif ringan dibanding lingkungan desktop modern lainnya, kebutuhan sumber dayanya tetap bergantung pada distribusi, aplikasi yang dijalankan, dan fitur yang diaktifkan.

#### 4.1.1 Persyaratan Minimum dan Rekomendasi

Tabel berikut merangkum persyaratan sistem untuk menjalankan Plasma 6.

| Komponen         | Minimum                     | Direkomendasikan                  |
| ---------------- | --------------------------- | --------------------------------- |
| CPU              | Prosesor 64-bit dengan SSE2 | Prosesor dual-core 2 GHz+         |
| RAM              | 2 GB                        | 4–8 GB                            |
| Ruang Disk       | 3 GB (instalasi dasar)      | 10–20 GB (dengan aplikasi)        |
| GPU              | Mendukung OpenGL 2.0        | Mendukung OpenGL 3.3+ atau Vulkan |
| Koneksi Internet | Diperlukan untuk instalasi  | Diperlukan untuk pembaruan        |
| Resolusi Layar   | 1024×768                    | 1920×1080 atau lebih tinggi       |

> **Catatan**
>
> Persyaratan di atas adalah untuk instalasi dasar. Jika Anda berencana menjalankan aplikasi berat seperti Kdenlive, Krita, atau Blender, tambahkan RAM dan ruang disk sesuai kebutuhan. Untuk penggunaan produktivitas ringan (browsing, dokumen, email), 4 GB RAM sudah cukup memadai.

#### 4.1.2 Analisis Penggunaan Sumber Daya

Berikut perkiraan penggunaan RAM Plasma 6 pada berbagai skenario:

| Skenario      | RAM     |
| ------------- | ------- |
| Idle          | ∼0.6 GB |
| Browsing      | ∼1.5 GB |
| Produktivitas | ∼2.8 GB |
| Multimedia    | ∼6 GB   |

Plasma 6 cukup efisien dalam penggunaan RAM. Bahkan pada skenario multimedia yang berat, seperti video editing atau rendering, kebutuhan RAM masih di bawah 8 GB.

#### 4.1.3 Persyaratan Khusus untuk Wayland

Jika Anda berencana menggunakan sesi Wayland, yang menjadi default di Plasma 6, ada beberapa persyaratan tambahan yang perlu diperhatikan:

* **Driver Grafis:** Wayland memerlukan driver grafis yang mendukung KMS (Kernel Mode Setting). Driver `amdgpu`, `i915`, dan `nouveau` sudah mendukung KMS. Untuk NVIDIA, driver proprietary versi 495+ mendukung Wayland.
* **Prosesor Grafis:** GPU harus mendukung OpenGL 2.0 atau lebih tinggi. GPU terintegrasi Intel HD 4000+ dan AMD Radeon HD 7000+ sudah memadai.
* **Kernel:** Kernel Linux 5.4 atau lebih baru direkomendasikan untuk dukungan perangkat keras yang lebih baik.

{% hint style="warning" %}
Pengguna dengan kartu grafis NVIDIA mungkin mengalami masalah dengan Wayland, terutama pada versi driver lama. Jika Anda mengalami masalah, Anda dapat beralih ke sesi X11 di layar login sebagai solusi sementara. Pastikan driver NVIDIA versi 495 atau lebih baru telah terinstal.
{% endhint %}

### 4.2 Instalasi di Berbagai Distribusi

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

### 4.3 Memulai Plasma

Setelah instalasi selesai, langkah selanjutnya adalah memulai sesi KDE Plasma. Ada beberapa cara untuk melakukannya, tergantung pada konfigurasi sistem Anda.

#### 4.3.1 Melalui Display Manager

Cara yang paling umum dan disarankan untuk memulai KDE Plasma adalah melalui display manager. Display manager adalah program yang menampilkan layar login grafis dan memungkinkan pengguna memilih sesi desktop.

**SDDM**

SDDM adalah display manager default untuk KDE Plasma. Ia menyediakan layar login yang dapat dikustomisasi dan mendukung berbagai sesi desktop.

Untuk mengonfigurasi SDDM, edit berkas `/etc/sddm.conf` atau letakkan berkas konfigurasi di `/etc/sddm.conf.d/`:

```ini
[Autologin]
User=
Session=plasma

[Theme]
Current=breeze
CursorTheme=breeze_cursors

[Users]
MaximumUid=60000
MinimumUid=1000

[Wayland]
EnableHiDPI=true
SessionDir=/usr/share/wayland-sessions
```

**Display Manager Lain**

Selain SDDM, ada beberapa display manager lain yang dapat digunakan dengan KDE Plasma:

| Display manager | Deskripsi                                                                   |
| --------------- | --------------------------------------------------------------------------- |
| GDM             | Display manager default GNOME. Dapat digunakan untuk memulai sesi Plasma.   |
| LightDM         | Display manager ringan yang mendukung berbagai sesi.                        |
| LXDM            | Display manager ringan dari proyek LXDE.                                    |
| greetd          | Display manager minimalis yang dapat dikonfigurasi dengan berbagai greeter. |

#### 4.3.2 Memulai Plasma Secara Manual

Jika Anda tidak menggunakan display manager, Anda dapat memulai KDE Plasma secara manual dari terminal. Ini berguna untuk sistem minimal atau untuk tujuan debugging.

**Untuk Sesi X11**

Tambahkan baris berikut ke `~/.xinitrc`:

```bash
exec dbus-launch --exit-with-x11 ck-launch-session startplasma-x11
```

Kemudian jalankan:

```bash
startx
```

**Untuk Sesi Wayland**

Untuk memulai sesi Wayland secara manual:

```bash
# Pastikan Anda berada di TTY (bukan di dalam sesi grafis)
# Login sebagai pengguna biasa (bukan root)
dbus-run-session startplasma-wayland
```

{% hint style="warning" %}
Jangan pernah menjalankan Plasma sebagai root. Ini tidak hanya tidak aman, tetapi juga dapat menyebabkan masalah izin pada berkas konfigurasi. Selalu jalankan Plasma sebagai pengguna biasa.
{% endhint %}

#### 4.3.3 Konfigurasi Awal

Setelah login pertama kali, Anda akan disambut oleh wizard konfigurasi awal KDE Plasma.

Wizard ini membantu Anda mengatur preferensi dasar seperti:

* Bahasa dan wilayah
* Tata letak keyboard
* Zona waktu
* Koneksi jaringan
* Tema awal

{% hint style="info" %}
Jika Anda melewatkan wizard konfigurasi awal, Anda dapat mengaksesnya kembali melalui **System Settings → Startup and Shutdown → Plasma Initial Setup**.
{% endhint %}

### 4.4 Instalasi Minimal vs. Lengkap

Salah satu keputusan penting saat menginstal KDE Plasma adalah menentukan seberapa banyak paket yang akan diinstal. Ada dua pendekatan utama: instalasi minimal dan instalasi lengkap.

#### 4.4.1 Instalasi Minimal

Instalasi minimal hanya menyertakan komponen inti KDE Plasma:

* Plasma Shell (`plasmashell`)
* KWin, manajer jendela
* System Settings, pusat konfigurasi
* Beberapa widget dasar
* Beberapa aplikasi inti, misalnya terminal

**Keunggulan:**

* Menghemat ruang disk, sekitar 1–2 GB.
* Waktu instalasi lebih cepat.
* Lebih sedikit aplikasi yang tidak digunakan.
* Lebih mudah untuk membangun desktop dari nol.

**Kekurangan:**

* Tidak ada aplikasi KDE seperti Dolphin, Kate, Konsole, dan lainnya.
* Beberapa widget mungkin tidak tersedia.
* Perlu menginstal paket tambahan secara manual.

#### 4.4.2 Instalasi Lengkap

Instalasi lengkap menyertakan semua komponen KDE Plasma dan aplikasi KDE:

* Semua yang ada di instalasi minimal
* Dolphin, file manager
* Kate, text editor
* Konsole, terminal
* Kdenlive, video editor
* Krita, digital painting
* Gwenview, image viewer
* Dan puluhan aplikasi lainnya

**Keunggulan:**

* Pengalaman out-of-the-box.
* Semua aplikasi yang mungkin Anda butuhkan sudah terinstal.
* Integrasi yang lebih baik antar aplikasi.

**Kekurangan:**

* Membutuhkan ruang disk yang lebih besar, 5–10 GB.
* Waktu instalasi lebih lama.
* Beberapa aplikasi mungkin tidak pernah digunakan.

#### 4.4.3 Perbandingan

| Aspek           | Minimal                 | Lengkap       |
| --------------- | ----------------------- | ------------- |
| Ruang disk      | 1–2 GB                  | 5–10 GB       |
| Waktu instalasi | 5–10 menit              | 20–40 menit   |
| Jumlah paket    | ∼100                    | ∼500+         |
| Aplikasi KDE    | Tidak ada               | Lengkap       |
| Widget          | Dasar                   | Lengkap       |
| Cocok untuk     | Pengguna tingkat lanjut | Pengguna baru |

{% hint style="info" %}
Jika Anda tidak yakin, mulailah dengan instalasi minimal dan tambahkan paket sesuai kebutuhan. Ini memberikan kontrol lebih besar atas apa yang terinstal di sistem Anda, dan menghindari “bloatware” yang tidak perlu.
{% endhint %}

### 4.5 Studi Kasus: Migrasi dari Desktop Lain

Banyak pengguna yang beralih ke KDE Plasma dari lingkungan desktop lain seperti GNOME, Windows, atau macOS. Bagian ini menyajikan studi kasus migrasi dari berbagai lingkungan.

#### 4.5.1 Migrasi dari GNOME

GNOME dan KDE Plasma memiliki filosofi yang berbeda, sehingga migrasi memerlukan penyesuaian.

{% stepper %}
{% step %}
### Backup data

Pastikan semua berkas penting telah di-backup.
{% endstep %}

{% step %}
### Instal KDE Plasma

Ikuti panduan instalasi untuk distribusi Anda.
{% endstep %}

{% step %}
### Pilih sesi Plasma di layar login

Setelah instalasi, restart dan pilih sesi Plasma.
{% endstep %}

{% step %}
### Impor pengaturan GNOME

Beberapa pengaturan dapat diimpor, tetapi tidak semuanya. Anda mungkin perlu mengatur ulang preferensi seperti wallpaper, pintasan keyboard, dan tema.
{% endstep %}

{% step %}
### Instal aplikasi KDE

Ganti aplikasi GNOME dengan padanan KDE, misalnya Nautilus → Dolphin dan Gedit → Kate.
{% endstep %}

{% step %}
### Sesuaikan Plasma

Kustomisasi Plasma sesuai preferensi Anda.
{% endstep %}
{% endstepper %}

> **Catatan**
>
> Anda tidak perlu menghapus GNOME setelah menginstal KDE Plasma. Keduanya dapat hidup berdampingan, dan Anda dapat memilih sesi yang diinginkan di layar login. Namun, beberapa aplikasi mungkin muncul dua kali di menu, sekali untuk versi GNOME dan sekali untuk versi KDE.

#### 4.5.2 Migrasi dari Windows

Bagi pengguna yang beralih dari Windows, KDE Plasma menawarkan pengalaman yang familier dengan panel di bawah dan menu aplikasi di kiri.

**Gunakan Tata Letak “Windows-like”**

Ubah tata letak panel agar mirip dengan taskbar Windows. Klik kanan panel, pilih **Edit Panel**, lalu seret panel ke bawah dan tambahkan widget yang diinginkan.

**Pintasan Keyboard**

Sesuaikan pintasan keyboard agar mirip dengan Windows. Misalnya, `Super` untuk membuka menu aplikasi dan `Alt + Tab` untuk beralih jendela.

**Gunakan Aplikasi yang Familier**

Banyak aplikasi Windows memiliki padanan di Linux: Firefox, Chrome, LibreOffice, GIMP, VLC, dan lainnya.

**Wine untuk Aplikasi Windows**

Jika Anda memerlukan aplikasi Windows tertentu, gunakan Wine atau Proton untuk menjalankannya di Linux.

#### 4.5.3 Migrasi dari macOS

Pengguna macOS yang beralih ke KDE Plasma mungkin menginginkan pengalaman yang mirip dengan macOS. Berikut tipsnya:

* **Panel di atas:** Pindahkan panel ke atas layar dengan mengedit panel.
* **Global menu:** Aktifkan global menu di **System Settings → Window Management → Global Menu**.
* **Dock:** Gunakan widget “Application Dashboard” atau “Latte Dock” untuk pengalaman dock seperti macOS.
* **Pintasan keyboard:** Sesuaikan pintasan agar mirip dengan macOS, misalnya `Cmd` digantikan dengan `Super`.
* **Tema:** Gunakan tema seperti “WhiteSur” yang meniru tampilan macOS.

{% hint style="info" %}
Tema “WhiteSur” adalah salah satu tema populer yang meniru tampilan macOS. Ia mencakup Plasma Style, skema warna, tema ikon, dan dekorasi jendela yang semuanya dirancang untuk meniru macOS.
{% endhint %}

#### 4.5.4 Checklist Migrasi

* [ ] Backup data penting
* [ ] Periksa persyaratan sistem
* [ ] Instal paket Plasma
* [ ] Instal aplikasi KDE
* [ ] Impor pengaturan dari desktop lama
* [ ] Sesuaikan tata letak panel
* [ ] Atur pintasan keyboard
* [ ] Terapkan tema dan ikon
* [ ] Konfigurasi koneksi jaringan
* [ ] Uji aplikasi penting
* [ ] Dokumentasikan pengaturan

### 4.6 Ringkasan Bab

Bab ini telah membahas proses instalasi KDE Plasma secara menyeluruh:

* **Persyaratan sistem:** Plasma 6 membutuhkan minimal 2 GB RAM dan 3 GB ruang disk, dengan 4–8 GB RAM dan 10–20 GB ruang disk direkomendasikan.
* **Instalasi di berbagai distribusi:** Prosedur instalasi bervariasi, tetapi langkah dasarnya sama: perbarui sistem, instal paket Plasma, konfigurasi display manager, dan reboot.
* **Memulai Plasma:** Cara yang disarankan adalah melalui display manager seperti SDDM. Untuk sistem minimal, Plasma dapat dimulai secara manual melalui `startplasma-x11` atau `startplasma-wayland`.
* **Instalasi minimal vs. lengkap:** Instalasi minimal menghemat ruang disk dan cocok untuk pengguna tingkat lanjut, sedangkan instalasi lengkap memberikan pengalaman out-of-the-box.
* **Studi kasus migrasi:** Migrasi dari GNOME, Windows, atau macOS memerlukan penyesuaian, tetapi KDE Plasma menawarkan fleksibilitas untuk meniru tampilan dan perilaku desktop lain.

Bab selanjutnya akan membahas cara menggunakan KDE Plasma sehari-hari: elemen antarmuka, widget, Activities, KRunner, dan System Settings. Kita akan menjelajahi cara memanfaatkan fitur-fitur ini untuk meningkatkan produktivitas dan pengalaman pengguna.

## 5 Menggunakan KDE Plasma

> “Alat yang baik tidak pernah menuntut perhatian; ia hanya bekerja.”
>
> — Donald Norman, _The Design of Everyday Things_

Setelah KDE Plasma terpasang dan berjalan, tibalah saatnya untuk benar-benar menggunakannya. Bab ini menuntun Anda menjelajahi setiap sudut antarmuka KDE Plasma: dari elemen-elemen dasar seperti panel dan widget, hingga fitur-fitur canggih seperti Activities, KRunner, dan System Settings. Kita akan melihat bagaimana fitur-fitur ini bekerja sama untuk menciptakan lingkungan desktop yang produktif, efisien, dan menyenangkan.

### 5.1 Elemen Antarmuka

Desktop KDE Plasma default terdiri dari beberapa elemen yang bekerja sama untuk menciptakan pengalaman pengguna yang koheren. Memahami setiap elemen adalah langkah pertama untuk menguasai KDE Plasma.

#### 5.1.1 Anatomi Desktop

Desktop KDE Plasma default terdiri dari:

**Wallpaper**

Gambar latar belakang desktop. Dapat berupa gambar statis, slideshow, atau animasi.

**Panel**

Bilah horizontal atau vertikal yang biasanya berada di bagian bawah. Berisi widget dan peluncur aplikasi.

**Widget**

Elemen interaktif yang dapat ditempatkan di desktop atau panel. Contoh: jam, catatan, pemantau sistem.

**Desktop**

Area utama tempat widget dan ikon berkas dapat ditempatkan.

#### 5.1.2 Panel

Panel adalah salah satu elemen paling penting di KDE Plasma. Ia berfungsi sebagai “pusat komando” untuk sebagian besar interaksi pengguna.

**Komponen Panel Default**

Panel bawah default KDE Plasma terdiri dari:

1. **Application Launcher:** Ikon “K” di paling kiri yang membuka menu aplikasi.
2. **Task Manager:** Menampilkan jendela yang sedang berjalan, memungkinkan beralih antar jendela.
3. **Desktop Pager:** Menampilkan virtual desktop dan memungkinkan berpindah antar desktop.
4. **System Tray:** Area notifikasi dan status sistem. Berisi ikon seperti jaringan, volume, baterai, dan jam.
5. **Digital Clock:** Menampilkan waktu dan tanggal.
6. **Show Desktop:** Meminimalkan semua jendela untuk menampilkan desktop.

**Mengedit Panel**

{% stepper %}
{% step %}
### Masuk ke mode edit

Klik kanan pada panel di area kosong, lalu pilih **Enter Edit Mode**.
{% endstep %}

{% step %}
### Ubah panel

Panel akan menampilkan tombol untuk menambah widget, mengubah ukuran, dan mengubah posisi.
{% endstep %}

{% step %}
### Pindahkan atau ubah ukuran panel

Untuk memindahkan panel, seret ke tepi layar lain. Untuk mengubah ukuran, seret tepi panel.
{% endstep %}

{% step %}
### Buka opsi tambahan

Klik **More Options** untuk pengaturan tambahan: posisi, tinggi, alignment, dan visibilitas.
{% endstep %}

{% step %}
### Keluar dari mode edit

Klik **Exit Edit Mode** setelah selesai.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Untuk menambahkan panel baru, misalnya panel vertikal di sisi kiri untuk peluncur aplikasi, klik kanan desktop, pilih **Add Panel → Empty Panel**, lalu konfigurasi sesuai keinginan.
{% endhint %}

#### 5.1.3 Application Launcher

Application Launcher adalah cara utama untuk mengakses aplikasi di KDE Plasma. Ada beberapa varian yang dapat dipilih:

| Varian                | Deskripsi                                                                                                       |
| --------------------- | --------------------------------------------------------------------------------------------------------------- |
| Kickoff               | Menu klasik dengan kategori Favorit, Aplikasi, Komputer, Riwayat, dan Keluar. Ini adalah default di KDE Plasma. |
| Kicker                | Menu sederhana dengan daftar aplikasi.                                                                          |
| Application Dashboard | Tampilan layar penuh dengan ikon besar, mirip dengan menu Start Windows 8.                                      |
| Application Menu      | Menu gaya macOS yang terintegrasi dengan panel.                                                                 |

#### 5.1.4 Task Manager

Task Manager adalah widget yang menampilkan jendela aplikasi yang sedang berjalan. Ia memiliki beberapa mode tampilan:

| Mode           | Deskripsi                                                         |
| -------------- | ----------------------------------------------------------------- |
| Icons Only     | Menampilkan hanya ikon aplikasi. Ini adalah default di Plasma 5+. |
| Text Only      | Menampilkan judul jendela tanpa ikon.                             |
| Icons and Text | Menampilkan ikon dan judul jendela.                               |

Task Manager juga mendukung fitur-fitur berikut:

* **Grouping:** Mengelompokkan jendela dari aplikasi yang sama.
* **Sorting:** Mengurutkan jendela berdasarkan nama, waktu, atau posisi.
* **Highlighting:** Menyorot jendela yang meminta perhatian.
* **Middle-click actions:** Aksi khusus dengan klik tengah, misalnya membuka jendela baru.

#### 5.1.5 System Tray

System Tray adalah area di panel yang menampilkan ikon status sistem dan notifikasi. Ikon default meliputi:

* **Network Manager:** Status koneksi jaringan, seperti Wi-Fi, Ethernet, dan VPN.
* **Volume:** Kontrol volume audio.
* **Battery:** Status baterai pada laptop.
* **Bluetooth:** Status dan kontrol perangkat Bluetooth.
* **Clipboard:** Riwayat clipboard.
* **Notifications:** Notifikasi aplikasi.
* **Digital Clock:** Waktu dan tanggal.

{% hint style="info" %}
Anda dapat menambahkan atau menghapus ikon di System Tray dengan mengklik kanan ikon tersebut dan memilih **Configure System Tray**. Di sini Anda dapat mengatur ikon mana yang selalu ditampilkan, disembunyikan, atau dihapus.
{% endhint %}

#### 5.1.6 Desktop

Desktop adalah area utama tempat widget dan ikon berkas dapat ditempatkan. Secara default, KDE Plasma menampilkan desktop dengan Folder View, yang memungkinkan Anda menempatkan berkas dan folder langsung di desktop.

**Widget Desktop Default**

Desktop default KDE Plasma menyertakan beberapa widget:

* **Folder View:** Menampilkan konten folder `~/Desktop`.
* **Notes:** Catatan tempel yang dapat diketik langsung di desktop.
* **Digital Clock:** Jam digital yang dapat ditempatkan di desktop.

**Mengedit Desktop**

{% stepper %}
{% step %}
### Masuk ke mode edit

Klik kanan pada desktop di area kosong, lalu pilih **Enter Edit Mode**.
{% endstep %}

{% step %}
### Tambahkan atau ubah elemen

Anda dapat menambah widget, mengubah wallpaper, dan mengubah tata letak.
{% endstep %}

{% step %}
### Tambahkan widget

Klik **Add Widgets** untuk menambah widget baru.
{% endstep %}

{% step %}
### Keluar dari mode edit

Klik **Exit Edit Mode** setelah selesai.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Jika Anda tidak sengaja mengubah desktop dan ingin mengembalikannya ke default, Anda dapat menggunakan **System Settings → Workspace Behavior → Desktop → Reset to Default**. Namun, ini akan menghapus semua widget kustom yang telah Anda tambahkan.
{% endhint %}

### 5.2 Widget dan Plasmoid

Widget, sering disebut Plasmoid, adalah salah satu fitur paling khas dari KDE Plasma. Mereka memungkinkan Anda menambahkan fungsionalitas ke desktop atau panel tanpa harus menjalankan aplikasi terpisah.

#### 5.2.1 Kategori Widget

| Kategori      | Contoh widget                                          |
| ------------- | ------------------------------------------------------ |
| Informasi     | Digital Clock, Weather, System Monitor, Dictionary     |
| Produktivitas | Notes, Timer, Clipboard, Calculator                    |
| Multimedia    | Media Player, Now Playing, Audio Volume                |
| Sistem        | Application Launcher, Task Manager, System Tray, Trash |
| Utilitas      | Folder View, KRunner, Show Desktop, Color Picker       |
| Internet      | RSS Now, Comics, Facebook, Weather Station             |

Ratusan widget tersedia melalui KDE Store.

#### 5.2.2 Menambahkan Widget

{% stepper %}
{% step %}
### Buka opsi widget

Klik kanan pada desktop atau panel.
{% endstep %}

{% step %}
### Pilih Add Widgets

Pilih **Add Widgets** untuk desktop, atau **Add Widgets** di Edit Mode untuk panel.
{% endstep %}

{% step %}
### Pilih widget

Panel samping akan muncul dengan daftar widget yang tersedia.
{% endstep %}

{% step %}
### Tambahkan widget

Seret widget ke lokasi yang diinginkan, atau klik widget dan pilih **Add to Desktop** atau **Add to Panel**.
{% endstep %}

{% step %}
### Jelajahi widget tambahan

Klik **Get New Widgets** untuk menjelajahi KDE Store dan mengunduh widget tambahan.
{% endstep %}
{% endstepper %}

#### 5.2.3 Widget Populer

**Digital Clock**

Widget jam digital yang menampilkan waktu dan tanggal. Dapat dikonfigurasi untuk menampilkan:

* Format 12 atau 24 jam
* Tanggal dalam berbagai format
* Zona waktu
* Kalender saat diklik
* Hari libur nasional

**System Monitor**

Widget yang menampilkan penggunaan sumber daya sistem secara real-time:

* Penggunaan CPU
* Penggunaan RAM
* Penggunaan jaringan
* Suhu perangkat keras
* Penggunaan disk

**Notes**

Widget catatan yang memungkinkan Anda mengetik langsung di desktop atau panel:

* Dukungan multi-halaman
* Format teks seperti bold, italic, dan bullet points
* Penyimpanan otomatis
* Sinkronisasi dengan aplikasi KNotes

**Weather**

Widget cuaca yang menampilkan:

* Suhu saat ini
* Prakiraan beberapa hari ke depan
* Kondisi cuaca
* Kecepatan dan arah angin
* Kelembapan

**Folder View**

Widget yang menampilkan isi folder di desktop atau panel:

* Menampilkan berkas dan folder dalam berbagai mode tampilan
* Mendukung drag-and-drop
* Ikon berkas berdasarkan jenis
* Menu konteks untuk operasi berkas

> **Catatan**
>
> Folder View di desktop secara default menampilkan isi folder `~/Desktop`. Namun, Anda dapat mengonfigurasinya untuk menampilkan folder lain, atau bahkan beberapa Folder View yang menampilkan folder berbeda.

#### 5.2.4 Mengonfigurasi Widget

{% stepper %}
{% step %}
### Buka konfigurasi widget

Klik kanan pada widget.
{% endstep %}

{% step %}
### Pilih Configure

Pilih **Configure \[Nama Widget]**.
{% endstep %}

{% step %}
### Ubah pengaturan

Dialog konfigurasi akan muncul dengan opsi yang tersedia. Ubah pengaturan sesuai keinginan.
{% endstep %}

{% step %}
### Terapkan perubahan

Klik **Apply** atau **OK**.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Konfigurasi widget disimpan dalam berkas:

`~/.config/plasma-org.kde.plasma.desktop-appletsrc`

Anda dapat mengedit berkas ini secara manual jika perlu, tetapi berhati-hatilah karena kesalahan dapat menyebabkan widget tidak berfungsi.
{% endhint %}

#### 5.2.5 Menghapus Widget

{% stepper %}
{% step %}
### Klik kanan pada widget
{% endstep %}

{% step %}
### Pilih Remove

Pilih **Remove \[Nama Widget]**.
{% endstep %}

{% step %}
### Konfirmasi penghapusan
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Menghapus widget tidak menghapus widget dari sistem, hanya dari desktop atau panel. Anda dapat menambahkannya kembali kapan saja melalui **Add Widgets**.
{% endhint %}

### 5.3 Activities dan Virtual Desktop

Salah satu fitur paling kuat dan unik dari KDE Plasma adalah Activities. Bersama dengan virtual desktop, Activities memberikan cara yang fleksibel untuk mengorganisasi ruang kerja Anda.

#### 5.3.1 Konsep Dasar

**Virtual Desktop** adalah pembagian logis dari area kerja dalam satu konteks. Setiap virtual desktop memiliki jendela sendiri, tetapi berbagi widget, wallpaper, dan pengaturan panel yang sama.

**Activity** adalah konteks yang lebih tinggi yang mencakup virtual desktop, widget, wallpaper, dan pengaturan panel yang berbeda. Setiap Activity adalah lingkungan yang terpisah secara konseptual.

| Aspek     | Virtual Desktop             | Activity                |
| --------- | --------------------------- | ----------------------- |
| Jendela   | Berbeda pada setiap desktop | Berbeda menurut konteks |
| Wallpaper | Sama                        | Berbeda                 |
| Panel     | Sama                        | Berbeda                 |
| Widget    | Sama                        | Berbeda                 |

#### 5.3.2 Mengapa Menggunakan Activities?

Activities sangat berguna untuk memisahkan konteks kerja yang berbeda:

| Activity     | Contoh penggunaan                                                           |
| ------------ | --------------------------------------------------------------------------- |
| Kerja        | Dengan widget kalender, task list, dan wallpaper profesional.               |
| Rumah        | Dengan widget media player, foto keluarga, dan wallpaper santai.            |
| Pengembangan | Dengan widget terminal, system monitor, dan pintasan aplikasi pengembangan. |
| Hiburan      | Dengan widget game launcher, media player, dan wallpaper game.              |

{% hint style="info" %}
Activities sangat berguna untuk pengguna yang sering berpindah antara konteks kerja yang berbeda. Misalnya, seorang pengembang dapat memiliki Activity “Pengembangan” dengan terminal dan editor kode, serta Activity “Komunikasi” dengan email dan chat.
{% endhint %}

#### 5.3.3 Membuat dan Mengelola Activities

{% stepper %}
{% step %}
### Buka Activities

Buka **System Settings → Workspace Behavior → Activities**.
{% endstep %}

{% step %}
### Buat Activity baru

Klik **Create New...** di bagian atas.
{% endstep %}

{% step %}
### Isi informasi

Masukkan nama, deskripsi, dan pilih ikon untuk Activity.
{% endstep %}

{% step %}
### Buat Activity

Klik **Create**.
{% endstep %}

{% step %}
### Konfigurasikan Activity

Atur wallpaper, panel, dan widget untuk Activity baru.
{% endstep %}
{% endstepper %}

Untuk berpindah antar Activities:

* Klik widget Activity Switcher di panel, jika tersedia.
* Gunakan pintasan `Meta + Q`, sebagai default.
* Buka **System Settings → Workspace Behavior → Activities**, lalu klik Activity yang diinginkan.

#### 5.3.4 Virtual Desktop

Virtual Desktop adalah cara tradisional untuk memisahkan jendela dalam satu konteks. KDE Plasma mendukung hingga 20 virtual desktop secara default.

**Mengelola Virtual Desktop**

{% stepper %}
{% step %}
### Buka Virtual Desktops

Buka **System Settings → Workspace Behavior → Virtual Desktops**.
{% endstep %}

{% step %}
### Atur jumlah desktop

Atur jumlah virtual desktop dengan menggeser slider.
{% endstep %}

{% step %}
### Beri nama desktop

Beri nama setiap virtual desktop dengan mengklik namanya.
{% endstep %}

{% step %}
### Terapkan pengaturan

Klik **Apply**.
{% endstep %}
{% endstepper %}

**Navigasi Antar Virtual Desktop**

* Gunakan `Ctrl + F1` hingga `Ctrl + F4` untuk berpindah langsung.
* Gunakan `Ctrl + Alt + Left/Right` untuk berpindah ke kiri atau kanan.
* Gunakan widget Desktop Pager di panel untuk navigasi visual.

#### 5.3.5 Virtual Desktop per Layar

Fitur baru di Plasma 6.7 memungkinkan setiap monitor memiliki virtual desktop independen. Ini sangat berguna untuk pengguna dengan konfigurasi multi-monitor yang kompleks.

> **Catatan**
>
> Fitur Virtual Desktop per Layar memerlukan Plasma 6.7 atau lebih baru. Jika Anda menggunakan versi sebelumnya, fitur ini tidak tersedia.

### 5.4 KRunner

KRunner adalah salah satu fitur paling kuat dan sering diabaikan di KDE Plasma. Ia adalah peluncur serbaguna yang dapat melakukan jauh lebih banyak daripada sekadar menjalankan aplikasi.

#### 5.4.1 Membuka KRunner

KRunner dapat dibuka dengan beberapa cara:

* Pintasan keyboard `Alt + F2`, sebagai default.
* Pintasan keyboard `Alt + Space`, jika dikonfigurasi.
* Klik kanan desktop, lalu pilih **Run Command**.
* Klik ikon KRunner di panel, jika tersedia.

#### 5.4.2 Fitur KRunner

| Tugas                      | Cara penggunaan                                       |
| -------------------------- | ----------------------------------------------------- |
| Menjalankan aplikasi       | Ketik nama aplikasi dan tekan `Enter`.                |
| Mencari berkas             | Ketik nama berkas dan KRunner akan mencari di sistem. |
| Perhitungan matematika     | Ketik ekspresi seperti `2+2*3`.                       |
| Konversi mata uang         | Ketik `100 USD to EUR`.                               |
| Konversi unit              | Ketik `5 km to miles`.                                |
| Membuka situs web          | Ketik URL atau kata kunci dan tekan `Enter`.          |
| Mencari emoji              | Ketik `:smile:` atau deskripsi emoji.                 |
| Menerjemahkan teks         | Ketik `translate hello to Spanish`.                   |
| Menjalankan perintah shell | Ketik `> perintah`.                                   |
| Membuka pengaturan         | Ketik nama pengaturan, misalnya `display`.            |
| Menutup aplikasi           | Ketik `kill nama-aplikasi`.                           |
| Menjadwalkan tugas         | Ketik `remind me at 3pm to call John`.                |

#### 5.4.3 Plugin KRunner

KRunner dapat diperluas dengan plugin.

| Plugin             | Fungsi                                                     |
| ------------------ | ---------------------------------------------------------- |
| QuickCmd           | Menjalankan perintah kustom dengan pintasan                |
| JetBrainsRunner    | Membuka proyek JetBrains terbaru                           |
| kqalc              | Kalkulator Qalculate, lebih canggih dari kalkulator bawaan |
| Symbols            | Mencari emoji dan karakter Unicode                         |
| KRunner Translator | Menerjemahkan kata dan kalimat                             |
| Web Search         | Mencari di mesin pencari                                   |
| Window Switcher    | Beralih antar jendela                                      |
| Sessions           | Mengelola sesi KDE Plasma                                  |

{% hint style="info" %}
Untuk mengaktifkan atau menonaktifkan plugin KRunner, klik ikon wrench di kiri bawah KRunner, atau buka **System Settings → Search → Plasma Search**. Di sini Anda dapat mengatur plugin yang aktif dan mengubah prioritasnya.
{% endhint %}

#### 5.4.4 Kustomisasi KRunner

KRunner sangat dapat dikonfigurasi. Beberapa opsi kustomisasi meliputi:

* Memilih plugin yang aktif agar hasil lebih relevan.
* Mengubah urutan prioritas plugin.
* Mengubah pintasan keyboard untuk membuka KRunner.
* Menambahkan perintah kustom menggunakan plugin seperti QuickCmd.

### 5.5 System Settings

System Settings adalah pusat konfigurasi untuk KDE Plasma. Di sini Anda dapat mengatur hampir semua aspek desktop, dari tema hingga pengaturan sistem yang lebih mendalam.

#### 5.5.1 Struktur System Settings

System Settings diorganisasi ke dalam beberapa kategori utama:

| Kategori           | Contoh modul                                                                                        |
| ------------------ | --------------------------------------------------------------------------------------------------- |
| Appearance         | Global Theme, Plasma Style, Colors, Icons, Cursors, Window Decorations, Fonts, Splash Screen        |
| Workspace Behavior | Activities, Virtual Desktops, Screen Edges, Desktop, General Behavior                               |
| Window Management  | Task Switcher, Window Rules, KWin Scripts, Window Behavior, Desktop Effects                         |
| Shortcuts          | Custom Shortcuts, Global Shortcuts, Standard Shortcuts, Web Shortcuts, KHotKeys                     |
| Hardware           | Input Devices, Display and Monitor, Audio, Bluetooth, Power Management, Printers, Removable Storage |
| Network            | Connections, Settings, Sharing                                                                      |
| System             | Users, Startup and Shutdown, System Information, Date and Time, Language, Regional Settings         |

#### 5.5.2 Kategori Utama

**Appearance**

Kategori ini mencakup semua pengaturan visual:

* **Global Theme:** Mengubah tema keseluruhan, termasuk Plasma Style, Colors, Icons, Cursors, Window Decorations, Splash Screen, dan SDDM.
* **Plasma Style:** Gaya visual panel dan widget.
* **Colors:** Skema warna antarmuka.
* **Icons:** Tema ikon sistem.
* **Cursors:** Kursor mouse.
* **Window Decorations:** Dekorasi jendela, termasuk judul, tombol, dan border.
* **Fonts:** Font sistem untuk berbagai elemen UI.
* **Splash Screen:** Layar splash saat login.

**Workspace Behavior**

Kategori ini mencakup pengaturan perilaku workspace:

* **Activities:** Membuat dan mengelola Activities.
* **Virtual Desktops:** Mengatur jumlah dan nama virtual desktop.
* **Screen Edges:** Aksi saat kursor menyentuh tepi layar.
* **Desktop:** Pengaturan desktop, termasuk klik dan drag.
* **General Behavior:** Pengaturan umum seperti double-click atau single-click.

**Window Management**

Kategori ini mencakup pengaturan manajemen jendela:

* **Task Switcher:** Cara beralih antar jendela dengan `Alt + Tab`.
* **Window Rules:** Aturan khusus untuk jendela tertentu.
* **KWin Scripts:** Skrip yang mengubah perilaku KWin.
* **Window Behavior:** Pengaturan fokus, snapping, dan lainnya.
* **Virtual Desktops:** Pengaturan desktop virtual.
* **Desktop Effects:** Efek visual seperti blur, cube, dan wobbly windows.

**Shortcuts**

Kategori ini mencakup pintasan keyboard dan mouse:

* **Custom Shortcuts:** Pintasan kustom untuk menjalankan perintah.
* **Global Shortcuts:** Pintasan global untuk aplikasi.
* **Standard Shortcuts:** Pintasan standar seperti `Ctrl+C` dan `Ctrl+V`.
* **Web Shortcuts:** Kata kunci untuk pencarian web di KRunner.
* **KHotKeys:** Pintasan untuk skrip KHotKeys.

**Hardware**

Kategori ini mencakup pengaturan perangkat keras:

* **Input Devices:** Keyboard, mouse, touchpad, dan joystick.
* **Display and Monitor:** Resolusi, refresh rate, scaling, dan multi-monitor.
* **Audio:** Volume, perangkat output atau input, dan efek suara.
* **Bluetooth:** Perangkat Bluetooth.
* **Power Management:** Pengaturan daya untuk laptop.
* **Printers:** Manajemen printer.
* **Removable Storage:** Perilaku saat mencolokkan perangkat.

**Network**

Kategori ini mencakup pengaturan jaringan:

* **Connections:** Manajemen koneksi Wi-Fi, Ethernet, dan VPN.
* **Settings:** Pengaturan proxy, DNS, dan lainnya.
* **Sharing:** Berbagi berkas dan printer.

**System**

Kategori ini mencakup pengaturan sistem:

* **Users:** Manajemen pengguna.
* **Startup and Shutdown:** Aplikasi autostart, splash screen, dan SDDM.
* **System Information:** Informasi sistem.
* **Date and Time:** Tanggal, waktu, dan zona waktu.
* **Language:** Bahasa dan format regional.
* **Regional Settings:** Format angka, tanggal, dan mata uang.

{% hint style="info" %}
System Settings memiliki fitur pencarian. Ketik kata kunci di kotak pencarian di bagian atas untuk menemukan modul konfigurasi yang diinginkan dengan cepat. Ini sangat berguna jika Anda tidak yakin di kategori mana pengaturan tertentu berada.
{% endhint %}

#### 5.5.3 Menggunakan System Settings

System Settings menggunakan pendekatan berbasis modul. Setiap modul konfigurasi disebut KCM, atau KDE Configuration Module.

| Jenis KCM   | Deskripsi                                                      |
| ----------- | -------------------------------------------------------------- |
| KCM QML     | Modul yang dibangun dengan QML dan Kirigami.                   |
| KCM C++     | Modul tradisional yang dibangun dengan C++ dan Qt Widgets.     |
| KCM KConfig | Modul yang membaca dan menulis langsung ke berkas konfigurasi. |

> **Catatan**
>
> Banyak pengaturan System Settings juga dapat diakses melalui command line menggunakan `kwriteconfig6` dan `kreadconfig6`. Ini berguna untuk otomasi atau jika Anda lebih suka bekerja di terminal.

### 5.6 Studi Kasus: Alur Kerja Pengguna Tingkat Lanjut

#### 5.6.1 Studi Kasus 1: Pengembang Perangkat Lunak

Seorang pengembang perangkat lunak dapat mengonfigurasi sistemnya sebagai berikut:

| Komponen                | Konfigurasi                                                                                                                           |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Activity “Pengembangan” | Panel atas dengan global menu, panel bawah dengan terminal dan editor kode, serta widget System Monitor untuk penggunaan CPU dan RAM. |
| Activity “Komunikasi”   | Panel bawah dengan email, chat, dan kalender, serta widget Notes untuk catatan cepat.                                                 |
| Pintasan kustom         | `Meta + T` untuk terminal dan `Meta + E` untuk editor kode.                                                                           |
| KRunner                 | Digunakan untuk menjalankan perintah shell cepat dengan prefix `>`.                                                                   |
| Virtual Desktop         | Empat virtual desktop: 1) Kode, 2) Terminal, 3) Browser, 4) Dokumentasi.                                                              |

#### 5.6.2 Studi Kasus 2: Desainer Grafis

Seorang desainer grafis dapat mengonfigurasi KDE Plasma sebagai berikut:

| Komponen       | Konfigurasi                                                                                                                        |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Tema kustom    | Menggunakan tema “WhiteSur” yang meniru macOS, dengan warna pastel dan ikon minimalis.                                             |
| Panel atas     | Menampilkan global menu, workspace switcher, dan system tray.                                                                      |
| Dock bawah     | Menggunakan widget “Application Dashboard” yang menampilkan aplikasi desain seperti Krita, Inkscape, dan GIMP.                     |
| Widget desktop | Widget Color Picker untuk mengambil warna dari layar, serta Notes untuk catatan desain.                                            |
| KRunner        | Digunakan untuk mencari berkas gambar dengan cepat.                                                                                |
| Activities     | Dua Activity: “Desain” dan “Referensi”. Activity “Referensi” memiliki banyak widget Folder View yang menampilkan gambar referensi. |

#### 5.6.3 Studi Kasus 3: Pengguna Multitasking

Seorang pengguna yang sering multitasking dapat mengonfigurasi KDE Plasma sebagai berikut:

| Komponen        | Konfigurasi                                                                                |
| --------------- | ------------------------------------------------------------------------------------------ |
| Panel kiri      | Menampilkan Task Manager dengan daftar jendela yang sedang berjalan.                       |
| Panel bawah     | Menampilkan Application Launcher, System Tray, dan Digital Clock.                          |
| Widget desktop  | Notes untuk catatan tugas, Timer untuk Pomodoro, dan System Monitor.                       |
| Virtual Desktop | Enam virtual desktop: 1) Email, 2) Browser, 3) Dokumen, 4) Spreadsheet, 5) Media, 6) Chat. |
| Pintasan        | `Meta + 1` hingga `Meta + 6` untuk berpindah antar virtual desktop.                        |
| KRunner         | Digunakan untuk menghitung, mengonversi mata uang, dan mencari kontak.                     |

#### 5.6.4 Studi Kasus 4: Pengguna dengan Perangkat Keras Lama

Seorang pengguna dengan laptop berusia delapan tahun dapat mengonfigurasi KDE Plasma untuk performa maksimal:

* Aktifkan Low Resource Mode di **System Settings → Workspace Behavior → General Behavior**.
* Nonaktifkan efek desktop yang berat seperti blur dan cube.
* Gunakan tema ringan seperti “Breeze” default tanpa transparansi.
* Gunakan sesi X11 daripada Wayland jika driver grafis tidak mendukung Wayland dengan baik.
* Kurangi jumlah virtual desktop menjadi dua.
* Nonaktifkan animasi dan transisi.
* Gunakan widget minimal seperti jam dan system tray.

{% hint style="info" %}
Untuk mengurangi penggunaan sumber daya lebih lanjut, pertimbangkan menggunakan Plasma Minimal, hanya paket `plasma-desktop`, daripada instalasi lengkap. Ini mengurangi jumlah proses yang berjalan di latar belakang.
{% endhint %}

#### 5.6.5 Studi Kasus 5: Pengguna dengan Kebutuhan Aksesibilitas

Seorang pengguna dengan kebutuhan aksesibilitas khusus dapat mengonfigurasi KDE Plasma sebagai berikut:

* Aktifkan Screen Reader (Orca) di **System Settings → Accessibility → Screen Reader**.
* Aktifkan High Contrast untuk pengguna dengan gangguan penglihatan.
* Aktifkan Magnifier untuk memperbesar area layar.
* Aktifkan Sticky Keys untuk pengguna dengan kesulitan menekan kombinasi tombol.
* Aktifkan Slow Keys untuk pengguna dengan tremor.
* Aktifkan Bounce Keys untuk menghindari penekanan tombol berulang.
* Sesuaikan ukuran font dan ikon.
* Aktifkan Night Color untuk mengurangi kelelahan mata.

> **Catatan**
>
> KDE Plasma memiliki dukungan aksesibilitas yang sangat baik. Jika Anda memiliki kebutuhan aksesibilitas khusus, jangan ragu untuk menjelajahi semua opsi di **System Settings → Accessibility**. Komunitas KDE juga menyediakan dokumentasi dan dukungan yang luas untuk topik ini.

### 5.7 Ringkasan Bab

Bab ini telah membahas penggunaan KDE Plasma sehari-hari secara menyeluruh:

* **Elemen antarmuka:** Desktop KDE Plasma terdiri dari wallpaper, panel, widget, dan desktop. Panel adalah “pusat komando” dengan Application Launcher, Task Manager, dan System Tray.
* **Widget dan Plasmoid:** Widget adalah aplikasi kecil yang dapat ditempatkan di desktop atau panel. Ratusan widget tersedia melalui KDE Store.
* **Activities dan Virtual Desktop:** Activities adalah konteks yang lebih tinggi dari virtual desktop, dengan wallpaper, panel, dan widget independen. Virtual desktop adalah pembagian logis dari area kerja dalam satu konteks.
* **KRunner:** Peluncur serbaguna yang dapat menjalankan aplikasi, mencari berkas, menghitung, mengonversi, dan banyak lagi.
* **System Settings:** Pusat konfigurasi untuk KDE Plasma, terorganisasi dalam kategori seperti Appearance, Workspace Behavior, Window Management, Shortcuts, dan Hardware.
* **Studi kasus:** Beberapa alur kerja pengguna tingkat lanjut, termasuk pengembang, desainer, pengguna multitasking, pengguna dengan perangkat keras lama, dan pengguna dengan kebutuhan aksesibilitas.

Bab selanjutnya akan membahas kustomisasi KDE Plasma secara mendalam: tema, ikon, dekorasi jendela, widget kustom, dan alat pihak ketiga seperti Klassy dan Material You Colors.

## 6 Kustomisasi

> “Desain bukan hanya tentang bagaimana sesuatu terlihat, tetapi tentang bagaimana ia bekerja dan bagaimana ia membuat Anda merasa.”
>
> — Dieter Rams, dikutip dalam konteks kustomisasi KDE

Jika ada satu fitur yang paling membedakan KDE Plasma dari lingkungan desktop lain, itu adalah kemampuannya untuk dikustomisasi secara total. Bab ini menuntun Anda menjelajahi setiap lapisan kustomisasi, dari yang paling sederhana seperti mengubah tema global, hingga yang paling kompleks seperti menulis widget kustom dan mengintegrasikan generator skema warna otomatis. Kita akan melihat bagaimana komponen-komponen kustomisasi bekerja sama untuk menciptakan lingkungan desktop yang benar-benar personal, fungsional, dan estetis.

### 6.1 Arsitektur Kustomisasi

Sebelum masuk ke detail masing-masing komponen, penting untuk memahami bagaimana sistem kustomisasi KDE Plasma dibangun. Kustomisasi di KDE Plasma bukanlah tambahan yang ditempelkan belakangan, melainkan bagian integral dari arsitektur sejak awal.

#### 6.1.1 Lapisan Kustomisasi

Kustomisasi di KDE Plasma memiliki beberapa lapisan, dari yang paling umum hingga yang paling spesifik:

1. **Global Theme:** Satu klik mengubah semuanya.
2. **Komponen individual:** Plasma Style, Colors, Icons, Decorations, dan Cursors.
3. **Tata letak panel dan widget.**
4. **Perilaku:** Pintasan, efek, dan aturan jendela.
5. **Script dan otomasi:** KWin Scripts dan QML.

Pengguna dapat memilih untuk mengubah hanya lapisan tertentu atau mengombinasikan semuanya untuk menciptakan lingkungan yang benar-benar personal.

#### 6.1.2 Lokasi Berkas Kustomisasi

Semua kustomisasi di KDE Plasma disimpan dalam berkas yang dapat dibaca manusia. Memahami lokasi berkas ini penting untuk backup, migrasi, dan pemecahan masalah.

| Lokasi                                              | Konten                                                     |
| --------------------------------------------------- | ---------------------------------------------------------- |
| `~/.config/kdeglobals`                              | Pengaturan global KDE, seperti skema warna, font, dan ikon |
| `~/.config/plasmarc`                                | Konfigurasi Plasma Shell                                   |
| `~/.config/kwinrc`                                  | Konfigurasi KWin                                           |
| `~/.config/plasma-org.kde.plasma.desktop-appletsrc` | Tata letak widget dan panel desktop                        |
| `~/.local/share/plasma/desktoptheme/`               | Plasma Style yang diinstal pengguna                        |
| `~/.local/share/plasma/look-and-feel/`              | Global Theme yang diinstal pengguna                        |
| `~/.local/share/plasma/plasmoids/`                  | Widget yang diinstal pengguna                              |
| `~/.local/share/color-schemes/`                     | Skema warna yang diinstal pengguna                         |
| `~/.local/share/icons/`                             | Tema ikon yang diinstal pengguna                           |
| `~/.local/share/aurorae/themes/`                    | Dekorasi jendela Aurorae                                   |

{% hint style="info" %}
Untuk memudahkan backup dan restore kustomisasi, gunakan alat seperti Konsave. Ia dapat menyimpan semua tema, widget, dan pengaturan Anda ke dalam satu berkas, dan memulihkannya di sistem lain dengan satu perintah.
{% endhint %}

### 6.2 Global Theme

Global Theme, sebelumnya disebut “Look and Feel”, adalah cara tercepat dan paling menyeluruh untuk mengubah tampilan KDE Plasma. Satu Global Theme dapat mengubah puluhan pengaturan sekaligus, menciptakan konsistensi visual di seluruh sistem.

#### 6.2.1 Apa Itu Global Theme?

> **Definisi**
>
> Global Theme adalah paket kustomisasi yang menggabungkan beberapa komponen visual: Plasma Style, skema warna, tema ikon, dekorasi jendela, task switcher, splash screen, dan tema lock screen. Menerapkan Global Theme akan mengubah semua komponen ini secara bersamaan, memastikan konsistensi visual.

Komponen yang termasuk dalam Global Theme meliputi:

* Plasma Style
* Kursor
* Skema warna
* Lock screen
* Tema ikon
* Splash screen
* Dekorasi jendela
* Task switcher

#### 6.2.2 Struktur Paket Global Theme

Global Theme disimpan sebagai paket KPackage. Struktur direktori paket adalah sebagai berikut:

```
my-global-theme/
|-- metadata.json # Metadata paket (wajib)
|-- contents/
|   |-- defaults # Nilai default
|   |-- layout-templates/ # Template tata letak panel
|   |   +-- org.kde.plasma.desktop-layout.js
|   |-- splash/ # Splash screen
|   |   |-- splash.qml
|   |   +-- images/
|   |-- look-and-feel/ # Konfigurasi tambahan
|   |-- logout/ # Layar logout
|   +-- sddm/ # Tema login SDDM
+-- LICENSE # Lisensi
```

Berkas `metadata.json` harus memiliki struktur berikut:

```json
{
  "KPackageStructure": "Plasma/LookAndFeel",
  "KPlugin": {
    "Authors": [
      {
        "Email": "author@example.com",
        "Name": "Nama Penulis"
      }
    ],
    "Category": "Global Themes",
    "Description": "Deskripsi tema global",
    "Id": "com.example.mytheme",
    "License": "GPL-3.0+",
    "Name": "My Theme",
    "Version": "1.0",
    "Website": "https://example.com"
  },
  "X-KDE-PluginInfo-Name": "com.example.mytheme",
  "X-Plasma-APIVersion": "2"
}
```

> **Catatan**
>
> Di Plasma 6, format metadata diubah dari `metadata.desktop` ke `metadata.json`, dan kunci `KPackageStructure` harus diset ke `Plasma/LookAndFeel` agar tema muncul di pengaturan Global Theme. Tema lama dari Plasma 5 perlu dikonversi secara manual.

#### 6.2.3 Memasang Global Theme

**Melalui KDE Store**

{% stepper %}
{% step %}
### Buka Global Theme

Buka **System Settings → Colors & Themes → Global Theme**.
{% endstep %}

{% step %}
### Jelajahi tema baru

Klik **Get New Global Themes...** di bagian bawah.
{% endstep %}

{% step %}
### Pilih tema

Jelajahi KDE Store atau gunakan kotak pencarian.
{% endstep %}

{% step %}
### Instal tema

Klik **Install** pada tema yang diinginkan.
{% endstep %}

{% step %}
### Terapkan tema

Setelah terinstal, tema akan muncul di daftar. Klik **Apply**.
{% endstep %}
{% endstepper %}

**Melalui Command Line**

```bash
# Memasang dari file lokal
kpackagetool6 --type Plasma/LookAndFeel --install /path/to/theme.tar.gz

# Memasang dari KDE Store (menggunakan ID)
plasmapkg2 --type lookandfeel --install com.example.mytheme

# Menghapus tema
kpackagetool6 --type Plasma/LookAndFeel --remove com.example.mytheme

# Melihat daftar tema yang terinstal
kpackagetool6 --type Plasma/LookAndFeel --list
```

{% hint style="info" %}
Untuk menjelajahi Global Theme populer, kunjungi [https://store.kde.org/browse?cat=104.](https://store.kde.org/browse?cat=104) Beberapa tema populer termasuk WhiteSur, Layan, Sweet, dan Nordic.
{% endhint %}

#### 6.2.4 Global Theme Populer

| Nama        | Gaya         | Deskripsi                                         |
| ----------- | ------------ | ------------------------------------------------- |
| Breeze      | Default      | Tema default Plasma, modern dan bersih            |
| Breeze Dark | Default Dark | Varian gelap dari Breeze                          |
| WhiteSur    | macOS-like   | Meniru tampilan macOS Big Sur                     |
| Layan       | Modern Flat  | Desain datar dengan aksen warna cerah             |
| Sweet       | Playful      | Warna-warna cerah dan bentuk bulat                |
| Nordic      | Minimalis    | Palet warna nordik yang tenang                    |
| Dracula     | Gelap        | Palet Dracula yang populer di kalangan pengembang |
| Arc         | Flat         | Desain datar yang terinspirasi dari GNOME         |

### 6.3 Plasma Style

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

### 6.4 Skema Warna

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

### 6.5 Tema Ikon

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

### 6.6 Dekorasi Jendela

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

### 6.7 Widget Kustom

Widget kustom adalah salah satu cara paling menarik untuk berkontribusi pada ekosistem KDE Plasma. Dengan QML, pengembang dapat membuat widget yang kompleks dengan kode yang relatif sedikit.

#### 6.7.1 Mengapa Mengembangkan Widget?

* **Menambah fungsionalitas:** Widget dapat menampilkan informasi atau melakukan tugas yang tidak tersedia di widget bawaan.
* **Personalisasi:** Widget kustom memungkinkan Anda menyesuaikan desktop dengan kebutuhan spesifik Anda.
* **Kontribusi:** Widget yang bermanfaat dapat dibagikan ke KDE Store dan digunakan oleh pengguna lain.
* **Pembelajaran:** Mengembangkan widget adalah cara yang bagus untuk belajar QML dan KDE Frameworks.

#### 6.7.2 Struktur Proyek Widget

```
my-widget/
|-- package/
|   |-- metadata.json # Metadata widget (wajib)
|   +-- contents/
|       |-- ui/
|       |   |-- main.qml # Entry point QML
|       |   |-- CompactRepresentation.qml
|       |   |-- FullRepresentation.qml
|       |   +-- configGeneral.qml
|       +-- config/
|           +-- config.qml
|-- CMakeLists.txt # Build system
+-- LICENSE
```

#### 6.7.3 `metadata.json`

Berkas `metadata.json` adalah jantung dari widget Plasma 6. Ia mendefinisikan metadata widget:

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
    "Description": "Deskripsi widget",
    "EnabledByDefault": true,
    "Icon": "preferences-system",
    "Id": "com.example.mywidget",
    "License": "GPL-3.0+",
    "Name": "My Widget",
    "Version": "1.0",
    "Website": "https://example.com"
  },
  "X-Plasma-API-Minimum-Version": "6.0"
}
```

#### 6.7.4 `main.qml`

Berkas `main.qml` adalah entry point untuk widget. Untuk plasmoid, root object adalah `PlasmoidItem`:

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.plasmoid
import org.kde.plasma.core as PlasmaCore
import org.kde.plasma.components as PlasmaComponents

PlasmoidItem {
    id: root

    preferredRepresentation: fullRepresentation

    fullRepresentation: Item {
        Layout.minimumWidth: 200
        Layout.minimumHeight: 100
        Layout.preferredWidth: 250
        Layout.preferredHeight: 150

        ColumnLayout {
            anchors.fill: parent
            anchors.margins: PlasmaCore.Units.smallSpacing

            PlasmaComponents.Label {
                text: "Halo, Plasma!"
                font.pointSize: 14
                Layout.alignment: Qt.AlignHCenter
            }

            PlasmaComponents.Button {
                text: "Klik Saya"
                Layout.alignment: Qt.AlignHCenter
                onClicked: {
                    console.log("Tombol diklik!")
                }
            }
        }
    }

    compactRepresentation: PlasmaComponents.Label {
        text: "W"
    }
}
```

#### 6.7.5 `CMakeLists.txt`

Berkas `CMakeLists.txt` mendefinisikan bagaimana widget dibangun dan diinstal:

```cmake
cmake_minimum_required(VERSION 3.16)
project(my-widget)

find_package(ECM 5.240.0 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH})

find_package(KF6 REQUIRED COMPONENTS Plasma)

plasma_install_package(package com.example.mywidget)
```

#### 6.7.6 Representasi Widget

| Representasi              | Deskripsi                                               |
| ------------------------- | ------------------------------------------------------- |
| `fullRepresentation`      | Tampilan utama widget saat diperluas                    |
| `compactRepresentation`   | Tampilan ringkas saat widget berada di panel            |
| `preferredRepresentation` | Menentukan representasi yang ditampilkan secara default |

> **Catatan**
>
> Widget di panel biasanya menggunakan `compactRepresentation`, sedangkan widget di desktop menggunakan `fullRepresentation`. Namun, ini dapat dikonfigurasi sesuai kebutuhan.

#### 6.7.7 Pengujian Widget

Untuk menguji widget selama pengembangan, gunakan `plasmoidviewer`:

```bash
# Menjalankan widget dari direktori pengembangan
plasmoidviewer -a package

# Menjalankan widget dari direktori tertentu
plasmoidviewer -a /path/to/package

# Melihat daftar widget yang tersedia
plasmoidviewer -l
```

#### 6.7.8 Contoh: Widget Clock

Berikut contoh widget jam sederhana yang menunjukkan penggunaan dasar QML:

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.plasmoid
import org.kde.plasma.core as PlasmaCore
import org.kde.plasma.components as PlasmaComponents

PlasmoidItem {
    id: root

    preferredRepresentation: compactRepresentation

    property string currentTime: Qt.formatTime(new Date(), "hh:mm")
    property string currentDate: Qt.formatDate(new Date(), "dddd, d MMMM yyyy")

    Timer {
        interval: 1000
        running: true
        repeat: true
        onTriggered: {
            root.currentTime = Qt.formatTime(new Date(), "hh:mm")
        }
    }

    compactRepresentation: PlasmaComponents.Label {
        text: root.currentTime
        font.pointSize: 11
    }

    fullRepresentation: ColumnLayout {
        Layout.minimumWidth: 200
        Layout.minimumHeight: 100

        PlasmaComponents.Label {
            text: root.currentTime
            font.pointSize: 32
            font.bold: true
            Layout.alignment: Qt.AlignHCenter
        }

        PlasmaComponents.Label {
            text: root.currentDate
            font.pointSize: 12
            Layout.alignment: Qt.AlignHCenter
        }
    }
}
```

### 6.8 Klassy: Utilitas Tema Lanjutan

Klassy adalah utilitas tema yang sangat populer di komunitas KDE Plasma. Ia menyediakan kustomisasi mendalam untuk dekorasi jendela, application style, dan ikon.

#### 6.8.1 Apa Itu Klassy?

> **Definisi**
>
> Klassy adalah utilitas tema untuk KDE Plasma yang terdiri dari Window Decoration, Application Style, Colour Scheme, dan Icons. Ia menawarkan kustomisasi tingkat lanjut untuk tombol jendela, sudut jendela, bayangan, dan berbagai elemen UI lainnya.

#### 6.8.2 Komponen Klassy

| Komponen          | Deskripsi                                                                                                  |
| ----------------- | ---------------------------------------------------------------------------------------------------------- |
| Window Decoration | Dekorasi jendela dengan tombol yang dapat dikonfigurasi, termasuk ukuran, bentuk, transparansi, dan warna. |
| Application Style | Gaya aplikasi yang konsisten dengan dekorasi jendela.                                                      |
| Colour Scheme     | Skema warna yang cocok dengan tema Klassy.                                                                 |
| Icons             | Ikon yang dirancang untuk melengkapi tema Klassy.                                                          |

#### 6.8.3 Fitur-Fitur Klassy

* Tombol yang dapat dikonfigurasi: ukuran, bentuk, warna, transparansi, dan posisi.
* Sudut jendela: rounded atau sharp, dengan radius yang dapat disesuaikan.
* Bayangan jendela yang dapat dikonfigurasi.
* Posisi, alignment, dan format judul jendela.
* Integrasi Global Theme.
* Dukungan mode terang dan gelap yang otomatis beralih berdasarkan pengaturan sistem.

#### 6.8.4 Menggunakan Klassy

{% stepper %}
{% step %}
### Instal Klassy

Instal Klassy melalui repositori distribusi atau AUR.
{% endstep %}

{% step %}
### Buka Window Decorations

Buka **System Settings → Colors & Themes → Window Decorations**.
{% endstep %}

{% step %}
### Pilih Klassy

Pilih Klassy dari daftar.
{% endstep %}

{% step %}
### Konfigurasikan Klassy

Klik **Configure Klassy** untuk membuka pengaturan Klassy.
{% endstep %}

{% step %}
### Sesuaikan tampilan

Sesuaikan tombol, sudut, bayangan, dan opsi lainnya.
{% endstep %}

{% step %}
### Terapkan komponen lain

Terapkan juga Application Style, Colors, dan Icons dari Klassy untuk konsistensi.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Klassy Settings dapat diakses langsung dari System Settings setelah instalasi. Di sini Anda dapat mengonfigurasi semua aspek Klassy dalam satu tempat.
{% endhint %}

### 6.9 Material You Colors

Material You Colors adalah generator skema warna otomatis yang menghasilkan tema terang dan gelap untuk KDE Plasma dari wallpaper saat ini, menggunakan implementasi Python dari Material Color Utilities Google.

#### 6.9.1 Apa Itu Material You?

> **Definisi**
>
> Material You adalah bahasa desain Google yang menghasilkan skema warna dinamis dari wallpaper pengguna. KDE Material You Colors adalah implementasi Python yang menerapkan prinsip ini ke KDE Plasma, menghasilkan skema warna yang harmonis secara otomatis.

#### 6.9.2 Fitur Material You Colors

* Plasma Widget untuk KDE Plasma 6 yang menampilkan kontrol Material You.
* Dukungan semua plugin wallpaper: warna, gambar, slideshow, dan animasi.
* Update otomatis saat wallpaper berubah.
* Tema Konsole yang dihasilkan.
* Dukungan Pywal untuk tema aplikasi lain.
* Dukungan untuk Light dan Dark mode.
* Konfigurasi melalui GUI atau berkas konfigurasi.

#### 6.9.3 Memasang Material You Colors

```bash
# Arch Linux (AUR)
yay -S kde-material-you-colors

# openSUSE (OBS)
sudo zypper addrepo https://download.opensuse.org/repositories/home:...
sudo zypper install kde-material-you-colors

# Fedora (Copr)
sudo dnf copr enable luisbocanegra/kde-material-you-colors
sudo dnf install kde-material-you-colors

# Instalasi melalui pipx (universal)
pipx install kde-material-you-colors

# Menjalankan backend
kde-material-you-colors
```

#### 6.9.4 Menggunakan Material You Colors

{% stepper %}
{% step %}
### Jalankan backend

Jalankan backend `kde-material-you-colors`.
{% endstep %}

{% step %}
### Tambahkan widget

Tambahkan widget Plasma You Colors ke panel atau desktop.
{% endstep %}

{% step %}
### Lihat warna yang dihasilkan

Widget akan menampilkan warna yang dihasilkan dari wallpaper saat ini.
{% endstep %}

{% step %}
### Atur opsi

Klik widget untuk mengakses opsi: mengubah wallpaper, mengubah mode light atau dark, dan mengonfigurasi preferensi.
{% endstep %}

{% step %}
### Terapkan skema otomatis

Skema warna akan otomatis diterapkan ke KDE Plasma dan aplikasi lain.
{% endstep %}
{% endstepper %}

> **Catatan**
>
> Material You Colors bekerja paling baik dengan wallpaper yang memiliki warna-warna kaya. Wallpaper monokrom mungkin menghasilkan skema warna yang kurang menarik.

#### 6.9.5 Konfigurasi Material You Colors

Berkas konfigurasi utama berada di `~/.config/kde-material-you-colors/config.conf`:

```ini
[General]
scheme = content
mode = dark
light_blend = false
dark_blend = true
pywal = true
konsole = true
pywal_theme = generated
pywal_light = false
wallpaper =
wallpaper_path = ~/Pictures/wallpaper.jpg
monitor = 0
changed_files =
reload_gtk_theme = true
reload_kde_theme = true

[Notification]
notify = true
notify_timeout = 3000

[KDE]
plasma_apply = true
plasma_reload = true
apply_aurorae = true
apply_icons = true
apply_cursors = true
apply_kvantum = true
```

### 6.10 Studi Kasus: Dari Breeze ke Tema Sepenuhnya Kustom

Untuk mengilustrasikan bagaimana semua komponen kustomisasi bekerja sama, mari kita lihat studi kasus lengkap: mengubah KDE Plasma dari Breeze default menjadi tema sepenuhnya kustom.

#### 6.10.1 Langkah 1: Memilih Arah Desain

Sebelum memulai, tentukan arah desain yang diinginkan:

* **Tema dasar:** Apakah Anda ingin tampilan minimalis, macOS-like, Windows-like, atau unik?
* **Mode:** Terang, gelap, atau dinamis dengan Material You?
* **Warna aksen:** Biru, ungu, hijau, atau warna lain?
* **Tata letak:** Panel atas, bawah, atau samping?

#### 6.10.2 Langkah 2: Memilih Global Theme

Untuk contoh ini, gunakan tema WhiteSur yang meniru macOS:

{% stepper %}
{% step %}
### Buka Global Theme

Buka **System Settings → Colors & Themes → Global Theme**.
{% endstep %}

{% step %}
### Dapatkan tema baru

Klik **Get New Global Themes...**.
{% endstep %}

{% step %}
### Cari WhiteSur

Cari “WhiteSur” dan instal.
{% endstep %}

{% step %}
### Terapkan tema

Terapkan tema dengan mengklik **Apply**.
{% endstep %}
{% endstepper %}

#### 6.10.3 Langkah 3: Menyesuaikan Plasma Style

Meskipun Global Theme sudah menyertakan Plasma Style, Anda mungkin ingin menyesuaikannya:

{% stepper %}
{% step %}
### Buka Plasma Style

Buka **System Settings → Colors & Themes → Plasma Style**.
{% endstep %}

{% step %}
### Pilih style

Pilih Plasma Style yang cocok, misalnya “WhiteSur-dark”.
{% endstep %}

{% step %}
### Sesuaikan tampilan

Sesuaikan warna dan transparansi sesuai keinginan.
{% endstep %}
{% endstepper %}

#### 6.10.4 Langkah 4: Mengubah Skema Warna

{% stepper %}
{% step %}
### Buka Colors

Buka **System Settings → Colors & Themes → Colors**.
{% endstep %}

{% step %}
### Pilih skema

Pilih skema “WhiteSur” atau “WhiteSur-dark”.
{% endstep %}

{% step %}
### Edit skema

Klik **Edit Scheme...** untuk menyesuaikan warna.
{% endstep %}

{% step %}
### Sesuaikan warna

Ubah warna aksen, latar belakang, dan teks sesuai keinginan.
{% endstep %}

{% step %}
### Simpan skema

Klik **Save As...** untuk menyimpan dengan nama kustom.
{% endstep %}
{% endstepper %}

#### 6.10.5 Langkah 5: Menerapkan Tema Ikon

{% stepper %}
{% step %}
### Buka Icons

Buka **System Settings → Colors & Themes → Icons**.
{% endstep %}

{% step %}
### Instal WhiteSur

Instal tema “WhiteSur” dari KDE Store.
{% endstep %}

{% step %}
### Terapkan tema

Pilih tema dan terapkan.
{% endstep %}
{% endstepper %}

#### 6.10.6 Langkah 6: Mengonfigurasi Dekorasi Jendela

Untuk dekorasi jendela yang lebih kustom, gunakan Klassy:

{% stepper %}
{% step %}
### Instal Klassy

Instal Klassy melalui repositori distribusi.
{% endstep %}

{% step %}
### Buka Window Decorations

Buka **System Settings → Colors & Themes → Window Decorations**.
{% endstep %}

{% step %}
### Pilih Klassy
{% endstep %}

{% step %}
### Konfigurasikan Klassy

Klik **Configure Klassy**.
{% endstep %}

{% step %}
### Atur dekorasi

Atur ukuran tombol, sudut jendela rounded, dan transparansi.
{% endstep %}

{% step %}
### Terapkan perubahan
{% endstep %}
{% endstepper %}

#### 6.10.7 Langkah 7: Menyesuaikan Tata Letak Panel

Untuk meniru tampilan macOS:

{% stepper %}
{% step %}
### Edit panel

Klik kanan panel, lalu pilih **Edit Panel**.
{% endstep %}

{% step %}
### Pindahkan panel

Seret panel ke atas layar.
{% endstep %}

{% step %}
### Atur tinggi panel

Atur tinggi panel menjadi lebih tipis.
{% endstep %}

{% step %}
### Tambahkan Global Menu

Tambahkan widget Global Menu ke panel.
{% endstep %}

{% step %}
### Hapus widget yang tidak perlu

Hapus Task Manager dan Desktop Pager.
{% endstep %}

{% step %}
### Tambahkan Application Menu

Tambahkan widget Application Menu sebagai pengganti Application Launcher.
{% endstep %}

{% step %}
### Aktifkan Floating Panel

Aktifkan opsi Floating Panel untuk tampilan yang lebih modern.
{% endstep %}
{% endstepper %}

#### 6.10.8 Langkah 8: Menambahkan Dock

Untuk pengalaman macOS yang lebih lengkap:

{% stepper %}
{% step %}
### Tambahkan panel baru

Tambahkan panel baru di bawah dengan klik kanan desktop, lalu pilih **Add Panel → Empty Panel**.
{% endstep %}

{% step %}
### Atur panel

Atur panel menjadi Floating dan Auto-hide.
{% endstep %}

{% step %}
### Tambahkan widget

Tambahkan widget Application Dashboard atau Task Manager.
{% endstep %}

{% step %}
### Atur ikon

Atur ukuran ikon dan spasi.
{% endstep %}
{% endstepper %}

#### 6.10.9 Langkah 9: Menambahkan Widget Kustom

Tambahkan widget yang melengkapi tema:

* Weather di panel atas untuk menampilkan cuaca.
* Notes di desktop untuk catatan cepat.
* System Monitor di panel atas untuk pemantauan sistem.
* Digital Clock dengan format waktu yang cocok.

#### 6.10.10 Langkah 10: Menerapkan Material You Colors

Untuk tema yang dinamis berdasarkan wallpaper:

{% stepper %}
{% step %}
### Instal Material You Colors

Instal `kde-material-you-colors`.
{% endstep %}

{% step %}
### Jalankan backend
{% endstep %}

{% step %}
### Tambahkan widget

Tambahkan widget Plasma You Colors ke panel.
{% endstep %}

{% step %}
### Atur wallpaper

Set wallpaper favorit Anda.
{% endstep %}

{% step %}
### Gunakan skema otomatis

Skema warna akan otomatis berubah sesuai wallpaper.
{% endstep %}
{% endstepper %}

#### 6.10.11 Hasil Akhir

Setelah mengikuti langkah-langkah di atas, desktop KDE Plasma Anda akan memiliki:

* Tampilan macOS-like dengan panel atas dan dock bawah.
* Tema WhiteSur yang konsisten di seluruh sistem.
* Dekorasi jendela Klassy dengan tombol yang dapat dikustomisasi.
* Ikon WhiteSur yang cocok dengan tema.
* Skema warna kustom yang sesuai preferensi.
* Widget yang melengkapi tema dan meningkatkan fungsionalitas.
* Skema warna dinamis dari Material You Colors, jika digunakan.

{% hint style="info" %}
Setelah semua kustomisasi selesai, gunakan Konsave untuk menyimpan konfigurasi Anda ke file. Ini memungkinkan Anda memulihkan kustomisasi di sistem lain atau setelah reinstall.
{% endhint %}

### 6.11 Ringkasan Bab

Bab ini telah membahas kustomisasi KDE Plasma secara menyeluruh:

* **Arsitektur kustomisasi:** KDE Plasma memiliki lima lapisan kustomisasi dari yang paling umum, Global Theme, hingga yang paling spesifik, Script & Otomasi.
* **Global Theme:** Paket kustomisasi yang menggabungkan Plasma Style, skema warna, tema ikon, dekorasi jendela, dan lainnya. Satu klik mengubah semuanya.
* **Plasma Style:** Paket aset SVG yang menentukan tampilan panel, widget, dan elemen Plasma lainnya.
* **Skema warna:** Berkas INI yang mendefinisikan warna untuk setiap peran semantik dalam antarmuka.
* **Tema ikon:** Kumpulan ikon yang mengikuti spesifikasi Freedesktop, dengan berbagai kategori dan ukuran.
* **Dekorasi jendela:** Bingkai jendela yang dapat dibuat dengan Aurorae berbasis SVG atau KDecoration berbasis C++. Klassy adalah pilihan populer.
* **Widget kustom:** Widget yang ditulis dalam QML, dengan struktur proyek yang terdefinisi: `metadata.json`, `main.qml`, dan `CMakeLists.txt`.
* **Klassy:** Utilitas tema lengkap dengan Window Decoration, Application Style, Colour Scheme, dan Icons.
* **Material You Colors:** Generator skema warna otomatis dari wallpaper.
* **Studi kasus:** Langkah lengkap untuk mengubah KDE Plasma dari Breeze default menjadi tema sepenuhnya kustom.

Bab selanjutnya akan membahas pengembangan untuk KDE Plasma secara lebih mendalam: prasyarat, struktur proyek widget, plugin QML C++, contoh widget Mediaframe, dan pengembangan modul konfigurasi (KCM).

## Bagian III

## Pengembangan

## 7 Pengembangan untuk KDE Plasma

> “Cara terbaik untuk memprediksi masa depan adalah dengan menciptakannya.”
>
> — Alan Kay, dikutip dalam konteks pengembangan open source

Sampai titik ini, kita telah mempelajari KDE Plasma dari perspektif pengguna: bagaimana menginstalnya, menggunakannya, dan mengustomisasinya. Bab ini mengubah perspektif tersebut secara fundamental. Alih-alih menjadi konsumen, kita akan menjadi pencipta. Kita akan mempelajari bagaimana mengembangkan widget, modul konfigurasi, dan plugin yang memperluas fungsionalitas KDE Plasma.

Bab ini ditulis untuk pembaca yang memiliki pemahaman dasar tentang pemrograman, tetapi tidak mengasumsikan pengalaman sebelumnya dengan Qt atau QML. Melalui contoh-contoh praktis dan studi kasus nyata, kita akan menelusuri seluruh alur kerja pengembangan, dari menyiapkan lingkungan hingga menerbitkan karya ke KDE Store.

### 7.1 Ekosistem Pengembangan KDE

Sebelum menyelami kode, penting untuk memahami ekosistem pengembangan KDE Plasma secara keseluruhan: alat apa yang tersedia, bahasa apa yang digunakan, dan bagaimana semuanya terhubung.

#### 7.1.1 Bahasa dan Teknologi

Pengembangan KDE Plasma melibatkan beberapa bahasa dan teknologi yang bekerja sama:

| Teknologi  | Kegunaan      | Contoh Penggunaan                  |
| ---------- | ------------- | ---------------------------------- |
| QML        | UI deklaratif | Widget, modul konfigurasi, panel   |
| JavaScript | Logika QML    | Handler, fungsi, animasi           |
| C++        | Logika berat  | Plugin QML, backend, KWin effects  |
| CMake      | Build system  | Konfigurasi proyek, instalasi      |
| Python     | Tooling       | Skrip build, generator, alat bantu |

_Tabel 7.1: Teknologi utama dalam pengembangan KDE Plasma. Sebagian besar pekerjaan UI dilakukan dalam QML, dengan C++ untuk logika yang membutuhkan performa._

{% hint style="info" %}
Untuk sebagian besar pengembangan widget, Anda hanya perlu QML dan JavaScript. C++ diperlukan hanya jika Anda perlu berinteraksi dengan pustaka sistem, mengakses perangkat keras, atau melakukan operasi yang membutuhkan performa tinggi.
{% endhint %}

#### 7.1.2 Alat Pengembangan

Berikut alat-alat yang perlu Anda siapkan untuk mengembangkan KDE Plasma:

| Alat                      | Deskripsi                                                      |
| ------------------------- | -------------------------------------------------------------- |
| KDevelop                  | IDE dari KDE dengan dukungan bawaan untuk QML, C++, dan CMake. |
| Qt Creator                | IDE resmi Qt, dengan dukungan QML yang sangat baik.            |
| Kate                      | Editor teks KDE dengan plugin untuk QML dan C++.               |
| plasmoidviewer            | Alat untuk menguji widget secara langsung tanpa instalasi.     |
| plasma-interactiveconsole | Konsol interaktif untuk bereksperimen dengan QML.              |
| kpackagetool6             | Alat untuk mengemas dan menginstal paket Plasma.               |
| git                       | Version control untuk mengelola kode sumber.                   |
| cmake                     | Build system generator.                                        |

#### 7.1.3 Struktur Komunitas Pengembangan

Komunitas pengembangan KDE terorganisir melalui beberapa platform:

* invent.kde.org: Repositori Git resmi untuk semua proyek KDE.
* develop.kde.org: Dokumentasi pengembangan resmi.
* techbase.kde.org: Wiki teknis untuk pengembang.
* Matrix: Platform obrolan utama untuk diskusi pengembangan.
* Mailing Lists: Diskusi melalui email untuk topik-topik tertentu.
* Phabricator: Pelacak tugas dan review kode.

{% hint style="info" %}
Jika Anda baru memulai, bergabunglah dengan kanal Matrix #plasma:kde.org atau #kde-devel:kde.org. Komunitas KDE sangat ramah terhadap pendatang baru, dan Anda akan mendapatkan bantuan dengan cepat.
{% endhint %}

### 7.2 Prasyarat

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

### 7.3 Struktur Proyek Widget

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

### 7.4 CMakeLists.txt untuk Widget

CMake adalah build system yang digunakan oleh sebagian besar proyek KDE. Memahami CMakeLists.txt sangat penting untuk pengembangan widget.

#### 7.4.1 CMakeLists.txt Minimal

Untuk widget sederhana yang hanya berisi QML tanpa C++, CMakeLists.txt dapat sangat minimal:

```cmake
cmake_minimum_required(VERSION 3.16)

project(my-widget VERSION 1.0.0)

find_package(ECM 5.240.0 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH})

find_package(KF6 REQUIRED COMPONENTS Plasma)

plasma_install_package(package com.example.mywidget)
```

#### 7.4.2 Penjelasan Setiap Baris

**cmake\_minimum\_required**

Menentukan versi CMake minimum yang diperlukan. KDE merekomendasikan 3.16 atau lebih tinggi.

**project**

Mendefinisikan nama proyek dan versi.

**find\_package(ECM)**

Menemukan Extra CMake Modules dari KDE, yang menyediakan makro seperti `plasma_install_package`.

**set(CMAKE\_MODULE\_PATH)**

Menambahkan direktori modul ECM ke path CMake.

**find\_package(KF6)**

Menemukan KDE Frameworks 6, khususnya komponen Plasma.

**plasma\_install\_package**

Makro khusus yang menginstal paket Plasma. Argumen pertama adalah direktori paket, argumen kedua adalah nama paket.

#### 7.4.3 CMakeLists.txt dengan Plugin C++

Jika widget Anda memerlukan plugin C++, CMakeLists.txt akan lebih kompleks:

```cmake
cmake_minimum_required(VERSION 3.16)

project(my-widget VERSION 1.0.0)

set(QT_MIN_VERSION "6.5.0")
set(KF6_MIN_VERSION "6.0.0")

find_package(ECM 5.240.0 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH})

find_package(Qt6 ${QT_MIN_VERSION} REQUIRED COMPONENTS
    Core
    Qml
    Quick
)
find_package(KF6 ${KF6_MIN_VERSION} REQUIRED COMPONENTS
    Plasma
    CoreAddons
)

# Plugin C++ untuk QML
add_library(mywidgetplugin SHARED
    mywidgetplugin.cpp
    mywidgetitem.cpp
)

target_link_libraries(mywidgetplugin PRIVATE
    Qt6::Core
    Qt6::Qml
    Qt6::Quick
    KF6::Plasma
    KF6::CoreAddons
)

# Instalasi plugin
install(TARGETS mywidgetplugin
    DESTINATION ${KDE_INSTALL_QMLDIR}/org/kde/plasma/private/mywidget
)

# Instalasi QML files
install(FILES
    package/contents/ui/main.qml
    DESTINATION ${KDE_INSTALL_QMLDIR}/org/kde/plasma/private/mywidget
)

# Instalasi paket Plasma
plasma_install_package(package com.example.mywidget)
```

{% hint style="info" %}
KDE menggunakan konvensi lokasi instalasi khusus. Variabel seperti `KDE_INSTALL_QMLDIR` menunjuk ke direktori yang tepat untuk setiap jenis berkas. Selalu gunakan variabel ini daripada hardcoding path, agar paket Anda dapat diinstal di berbagai distribusi.
{% endhint %}

#### 7.4.4 Kompilasi dan Instalasi

Setelah CMakeLists.txt siap, Anda dapat mengompilasi dan menginstal widget:

```bash
# Buat direktori build
mkdir build && cd build

# Konfigurasi dengan CMake
cmake .. -DCMAKE_INSTALL_PREFIX=$(kf6-config --prefix)

# Kompilasi
make

# Instalasi (untuk pengguna)
make install

# Atau instalasi langsung dari direktori package
kpackagetool6 --type Plasma/Applet --install ../package --hash 0000000000000000
```

{% hint style="warning" %}
Jika Anda menggunakan `make install` tanpa prefix khusus, paket akan diinstal ke `/usr/local/`, yang mungkin tidak berada di path pencarian Plasma. Gunakan `kpackagetool6` untuk instalasi pengguna, atau konfigurasikan prefix dengan benar.
{% endhint %}

### 7.5 Plugin QML C++

Untuk widget yang memerlukan fungsionalitas tingkat lanjut, plugin QML C++ memungkinkan Anda mengekspos kelas C++ ke QML. Ini berguna untuk:

* Mengakses pustaka sistem atau perangkat keras.
* Melakukan operasi yang membutuhkan performa tinggi.
* Membuat model data yang kompleks.
* Mengintegrasikan dengan API eksternal.

#### 7.5.1 Arsitektur Plugin QML

Plugin QML C++ bertindak sebagai jembatan antara UI QML dan pustaka C++ di bawahnya:

```
Lapisan QML: main.qml, komponen UI
                │
                ▼
Plugin QML C++: QQmlExtensionPlugin, QObject, QAbstractItemModel
                │
                ▼
Pustaka C++: KDE Frameworks, Qt, pustaka sistem
                │
                ▼
Sistem: Kernel, perangkat keras, layanan
```

_Gambar 7.2: Arsitektur plugin QML C++. Plugin bertindak sebagai jembatan antara UI QML dan pustaka C++ di bawahnya._

#### 7.5.2 Membuat Plugin QML Sederhana

Mari kita buat plugin QML sederhana yang mengekspos kelas C++ ke QML.

**Kelas C++**

```cpp
#pragma once

#include <QObject>
#include <QString>

class MyWidgetItem : public QObject
{
    Q_OBJECT
    Q_PROPERTY(QString greeting READ greeting WRITE setGreeting NOTIFY greetingChanged)
    Q_PROPERTY(int counter READ counter NOTIFY counterChanged)

public:
    explicit MyWidgetItem(QObject *parent = nullptr);

    QString greeting() const;
    void setGreeting(const QString &greeting);

    int counter() const;

    Q_INVOKABLE void increment();

Q_SIGNALS:
    void greetingChanged();
    void counterChanged();

private:
    QString m_greeting;
    int m_counter = 0;
};
```

```cpp
#include "mywidgetitem.h"

MyWidgetItem::MyWidgetItem(QObject *parent)
    : QObject(parent)
    , m_greeting(QStringLiteral("Halo, dunia!"))
{
}

QString MyWidgetItem::greeting() const
{
    return m_greeting;
}

void MyWidgetItem::setGreeting(const QString &greeting)
{
    if (m_greeting == greeting) {
        return;
    }

    m_greeting = greeting;
    Q_EMIT greetingChanged();
}

int MyWidgetItem::counter() const
{
    return m_counter;
}

void MyWidgetItem::increment()
{
    ++m_counter;
    Q_EMIT counterChanged();
}
```

**Plugin Kelas**

```cpp
#pragma once

#include <QQmlExtensionPlugin>

class MyWidgetPlugin : public QQmlExtensionPlugin
{
    Q_OBJECT
    Q_PLUGIN_METADATA(IID QQmlExtensionInterface_iid)

public:
    void registerTypes(const char *uri) override;
};
```

```cpp
#include "mywidgetplugin.h"
#include "mywidgetitem.h"

#include <qqml.h>

void MyWidgetPlugin::registerTypes(const char *uri)
{
    // @uri org.kde.plasma.private.mywidget
    qmlRegisterType<MyWidgetItem>(uri, 1, 0, "MyWidgetItem");
}
```

**Penggunaan dalam QML**

Setelah plugin C++ dibuat, Anda dapat menggunakannya dalam QML:

```qml
import QtQuick
import org.kde.plasma.plasmoid
import org.kde.plasma.private.mywidget 1.0

PlasmoidItem {
    id: root

    MyWidgetItem {
        id: myItem
    }

    fullRepresentation: Column {
        spacing: 10

        Text {
            text: myItem.greeting
        }

        Text {
            text: "Counter: " + myItem.counter
        }

        Button {
            text: "Increment"
            onClicked: myItem.increment()
        }
    }
}
```

#### 7.5.3 Build dan Instalasi Plugin

Untuk mengompilasi plugin, tambahkan ke CMakeLists.txt seperti yang ditunjukkan di bagian sebelumnya. Setelah dikompilasi, plugin akan diinstal ke direktori QML yang benar.

{% hint style="info" %}
URI plugin, misalnya `org.kde.plasma.private.mywidget`, harus unik dan mengikuti konvensi namespace. Untuk widget pribadi, gunakan `org.kde.plasma.private.<nama>` untuk menghindari konflik dengan plugin resmi.
{% endhint %}

### 7.6 Contoh: Widget Mediaframe

Widget mediaframe dari kdeplasma-addons adalah contoh yang baik untuk mempelajari bagaimana widget dengan plugin C++ diimplementasikan. Widget ini menampilkan frame media dengan kontrol pemutaran.

#### 7.6.1 Struktur Widget Mediaframe

```
mediaframe/
├── CMakeLists.txt
├── package/
│   ├── metadata.json
│   └── contents/
│       └── ui/
│           ├── main.qml
│           └── config.qml
└── src/
    ├── mediaframeplugin.h
    ├── mediaframeplugin.cpp
    ├── mediaframe.h
    └── mediaframe.cpp
```

#### 7.6.2 Kelas MediaFrame

Kelas MediaFrame menyediakan fungsi untuk mengontrol pemutaran media:

```cpp
#pragma once

#include <QObject>
#include <QUrl>

class MediaFrame : public QObject
{
    Q_OBJECT
    Q_PROPERTY(QUrl source READ source WRITE setSource NOTIFY sourceChanged)
    Q_PROPERTY(bool playing READ isPlaying NOTIFY playingChanged)
    Q_PROPERTY(qreal position READ position NOTIFY positionChanged)
    Q_PROPERTY(qreal duration READ duration NOTIFY durationChanged)

public:
    explicit MediaFrame(QObject *parent = nullptr);

    QUrl source() const;
    void setSource(const QUrl &source);

    bool isPlaying() const;

    qreal position() const;
    qreal duration() const;

    Q_INVOKABLE void play();
    Q_INVOKABLE void pause();
    Q_INVOKABLE void stop();
    Q_INVOKABLE void seek(qreal position);

Q_SIGNALS:
    void sourceChanged();
    void playingChanged();
    void positionChanged();
    void durationChanged();

private:
    QUrl m_source;
    bool m_playing = false;
    qreal m_position = 0.0;
    qreal m_duration = 0.0;
};
```

#### 7.6.3 QML Widget

QML untuk widget mediaframe menggunakan plugin C++ untuk kontrol media:

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.plasmoid
import org.kde.plasma.core as PlasmaCore
import org.kde.plasma.components as PlasmaComponents
import org.kde.plasma.private.mediaframe 2.0

PlasmoidItem {
    id: root

    property alias source: mediaFrame.source

    MediaFrame {
        id: mediaFrame
    }

    fullRepresentation: Item {
        Layout.minimumWidth: 320
        Layout.minimumHeight: 240

        ColumnLayout {
            anchors.fill: parent

            // Area video
            Item {
                Layout.fillWidth: true
                Layout.fillHeight: true

                VideoOutput {
                    id: videoOutput
                    anchors.fill: parent
                    source: mediaFrame
                }
            }

            // Kontrol
            RowLayout {
                Layout.fillWidth: true

                PlasmaComponents.Button {
                    icon.name: mediaFrame.playing ? "media-playback-pause" : "media-playback-start"
                    onClicked: mediaFrame.playing ? mediaFrame.pause() : mediaFrame.play()
                }

                PlasmaComponents.Slider {
                    Layout.fillWidth: true
                    from: 0
                    to: mediaFrame.duration
                    value: mediaFrame.position
                    onMoved: mediaFrame.seek(value)
                }

                PlasmaComponents.Button {
                    icon.name: "media-playback-stop"
                    onClicked: mediaFrame.stop()
                }
            }
        }
    }
}
```

#### 7.6.4 Pelajaran dari Mediaframe

Widget mediaframe mengajarkan beberapa konsep penting:

1. **Pemisahan UI dan logika:** UI di QML, logika di C++. Ini memudahkan pengembangan dan pemeliharaan.
2. **Properti `Q_PROPERTY`:** Mengekspos properti C++ ke QML dengan notifikasi perubahan.
3. **Method `Q_INVOKABLE`:** Mengekspos method C++ yang dapat dipanggil dari QML.
4. **Signal:** Menggunakan signal untuk komunikasi asinkron antara C++ dan QML.
5. **Integrasi dengan VideoOutput:** Menggunakan Qt Multimedia untuk rendering video.

{% hint style="info" %}
Untuk mempelajari lebih lanjut, clone repositori kdeplasma-addons dan jelajahi widget lain seperti Weather, Notes, dan Color Picker. Setiap widget memberikan contoh pola pengembangan yang berbeda.
{% endhint %}

### 7.7 Pengembangan Modul Konfigurasi (KCM)

Modul Konfigurasi KDE (KCM) adalah komponen yang memperluas System Settings. KCM memungkinkan pengguna untuk mengonfigurasi berbagai aspek sistem dan aplikasi.

#### 7.7.1 Arsitektur KCM

KCM di Plasma 6 dibangun dengan QML dan Kirigami. Arsitekturnya terdiri dari:

**KPackage**

Wadah untuk UI QML dan resource lainnya.

**ConfigModule**

Kelas C++ yang menyediakan logika konfigurasi.

**QML UI**

Antarmuka pengguna yang dibangun dengan QML dan Kirigami.

**KConfigXT**

Sistem untuk menghasilkan kode konfigurasi dari berkas XML.

```
System Settings Host
        │
        ▼
KCM (KPackage)
        │
        ├── KQuickAddons::ConfigModule
        ├── QML UI (Kirigami)
        └── KConfigXT
        │
        ▼
KConfig / KConfigXT
        │
        ▼
Berkas Konfigurasi (~/.config/*.rc)
```

_Gambar 7.3: Arsitektur modul konfigurasi (KCM) di Plasma 6. KCM bertindak sebagai jembatan antara antarmuka System Settings dan berkas konfigurasi di disk._

#### 7.7.2 Struktur Proyek KCM

```
my-kcm/
├── CMakeLists.txt
├── src/
│   ├── kcm_myconfig.h
│   ├── kcm_myconfig.cpp
│   └── myconfig.kcfg # Skema KConfigXT
└── package/
    ├── metadata.json
    └── contents/
        └── ui/
            └── main.qml
```

#### 7.7.3 Skema KConfigXT

KConfigXT adalah cara KDE untuk mendefinisikan konfigurasi secara deklaratif. Berkas `.kcfg` berisi definisi opsi konfigurasi:

```xml
<?xml version="1.0" encoding="UTF-8"?>

<kcfg xmlns="http://www.kde.org/standards/kcfg/1.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.kde.org/standards/kcfg/1.0
      http://www.kde.org/standards/kcfg/1.0/kcfg.xsd">
    <kcfgfile name="myconfigrc"/>

    <group name="General">
        <entry name="enabled" type="Bool">
            <default>true</default>
            <label>Aktifkan fitur</label>
        </entry>

        <entry name="displayName" type="String">
            <default>Pengguna</default>
            <label>Nama tampilan</label>
        </entry>

        <entry name="refreshInterval" type="Int">
            <default>60</default>
            <min>10</min>
            <max>3600</max>
            <label>Interval refresh (detik)</label>
        </entry>

        <entry name="theme" type="Enum">
            <default>Light</default>
            <choices>
                <choice name="Light"><label>Terang</label></choice>
                <choice name="Dark"><label>Gelap</label></choice>
                <choice name="Auto"><label>Otomatis</label></choice>
            </choices>
            <label>Tema</label>
        </entry>
    </group>
</kcfg>
```

#### 7.7.4 Kelas ConfigModule

```cpp
#pragma once

#include <KQuickConfigModule>

class KcmMyConfig : public KQuickConfigModule
{
    Q_OBJECT
    Q_PROPERTY(bool enabled READ enabled WRITE setEnabled NOTIFY enabledChanged)
    Q_PROPERTY(QString displayName READ displayName WRITE setDisplayName NOTIFY displayNameChanged)
    Q_PROPERTY(int refreshInterval READ refreshInterval WRITE setRefreshInterval NOTIFY refreshIntervalChanged)

public:
    explicit KcmMyConfig(QObject *parent, const KPluginMetaData &data);

    bool enabled() const;
    void setEnabled(bool enabled);

    QString displayName() const;
    void setDisplayName(const QString &name);

    int refreshInterval() const;
    void setRefreshInterval(int interval);

public Q_SLOTS:
    void save() override;
    void load() override;
    void defaults() override;

Q_SIGNALS:
    void enabledChanged();
    void displayNameChanged();
    void refreshIntervalChanged();

private:
    KConfig m_config;
};
```

#### 7.7.5 QML UI untuk KCM

UI untuk KCM dibangun dengan Kirigami:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as QQC
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM
import org.kde.kquickcontrols as KQC

KCM.SimpleKCM {
    id: root

    property alias cfg_enabled: enabledCheck.checked
    property alias cfg_displayName: nameField.text
    property alias cfg_refreshInterval: intervalSpin.value

    Kirigami.FormLayout {
        QQC.CheckBox {
            id: enabledCheck
            text: "Aktifkan fitur"
            Kirigami.FormData.label: "Status:"
        }

        QQC.TextField {
            id: nameField
            placeholderText: "Masukkan nama tampilan"
            Kirigami.FormData.label: "Nama Tampilan:"
        }

        QQC.SpinBox {
            id: intervalSpin
            from: 10
            to: 3600
            stepSize: 10
            editable: true
            Kirigami.FormData.label: "Interval Refresh (detik):"
        }
    }
}
```

#### 7.7.6 metadata.json untuk KCM

```json
{
    "KPackageStructure": "KCM",
    "KPlugin": {
        "Authors": [
            {
                "Email": "author@example.com",
                "Name": "Nama Penulis"
            }
        ],
        "Description": "Modul konfigurasi untuk aplikasi saya",
        "Icon": "preferences-system",
        "Id": "kcm_myconfig",
        "License": "GPL-3.0+",
        "Name": "Konfigurasi Saya",
        "Version": "1.0.0",
        "Website": "https://example.com"
    },
    "X-KDE-System-Settings-Parent-Category": "personalization",
    "X-KDE-Keywords": "config,settings,myapp",
    "X-KDE-Weight": 50
}
```

{% hint style="info" %}
Kunci `X-KDE-System-Settings-Parent-Category` menentukan di kategori mana KCM akan muncul di System Settings. Nilai umum termasuk `personalization`, `hardware`, `network`, `system`, dan `workspace`.
{% endhint %}

#### 7.7.7 Membangun dan Menguji KCM

```bash
# Build
mkdir build && cd build
cmake .. -DCMAKE_INSTALL_PREFIX=$(kf6-config --prefix)
make

# Instalasi
make install

# Test dengan kcmshell6
kcmshell6 kcm_myconfig

# Atau buka System Settings dan cari KCM
systemsettings
```

{% hint style="info" %}
Gunakan `kcmshell6` untuk menguji KCM secara langsung tanpa harus membuka System Settings. Ini mempercepat siklus pengembangan.
{% endhint %}

### 7.8 Sumber Daya Pengembangan

Setelah Anda menguasai dasar-dasar pengembangan KDE Plasma, sumber daya berikut akan membantu Anda memperdalam pengetahuan dan berkontribusi ke proyek.

#### 7.8.1 Dokumentasi Resmi

| Sumber           | Deskripsi                                                                         |
| ---------------- | --------------------------------------------------------------------------------- |
| develop.kde.org  | Portal utama untuk pengembangan KDE, dengan tutorial, API reference, dan panduan. |
| techbase.kde.org | Wiki teknis dengan informasi mendalam tentang arsitektur KDE.                     |
| api.kde.org      | Referensi API untuk KDE Frameworks dan pustaka KDE.                               |
| docs.kde.org     | Dokumentasi pengguna untuk aplikasi KDE.                                          |
| invent.kde.org   | Repositori Git untuk semua proyek KDE.                                            |

#### 7.8.2 Tutorial dan Panduan

* QML Tutorial di KDE: [https://develop.kde.org/docs/plasma/widget/](https://develop.kde.org/docs/plasma/widget/)
* Kirigami Tutorial: [https://develop.kde.org/docs/kirigami/](https://develop.kde.org/docs/kirigami/)
* KConfigXT Tutorial: [https://develop.kde.org/docs/features/config/](https://develop.kde.org/docs/features/config/)
* CMake di KDE: [https://develop.kde.org/docs/getting-started/configure-build/](https://develop.kde.org/docs/getting-started/configure-build/)

#### 7.8.3 Repositori Referensi

| Repositori       | Deskripsi                       |
| ---------------- | ------------------------------- |
| plasma-framework | Pustaka inti Plasma             |
| kdeplasma-addons | Koleksi widget tambahan         |
| plasma-workspace | Komponen workspace Plasma       |
| kwin             | Manajer jendela KWin            |
| kde-frameworks   | Kumpulan pustaka KDE Frameworks |
| kdevelop         | IDE KDevelop                    |
| kate             | Editor teks Kate                |

_Tabel 7.2: Repositori referensi yang berguna untuk mempelajari pengembangan KDE Plasma._

#### 7.8.4 Komunitas dan Dukungan

| Kanal        | Informasi                                                                 |
| ------------ | ------------------------------------------------------------------------- |
| Matrix       | #plasma:kde.org (pengguna), #kde-devel:kde.org (pengembang)               |
| Mailing List | plasma-devel@kde.org, kde-devel@kde.org                                   |
| Forum        | [https://discuss.kde.org/](https://discuss.kde.org/)                      |
| Bug Tracker  | [https://bugs.kde.org/](https://bugs.kde.org/)                            |
| KDE Store    | [https://store.kde.org/](https://store.kde.org/) untuk menerbitkan widget |

#### 7.8.5 Alat Pengembangan Tambahan

| Alat                       | Deskripsi                                              |
| -------------------------- | ------------------------------------------------------ |
| qmlscene                   | Menjalankan file QML secara langsung.                  |
| qmlplugindump              | Menampilkan informasi tentang plugin QML.              |
| plasma-interactiveconsole  | Konsol interaktif untuk menguji QML Plasma.            |
| kpackagetool6              | Mengemas dan menginstal paket Plasma.                  |
| kreadconfig6/kwriteconfig6 | Membaca dan menulis konfigurasi KDE dari command line. |
| dbus-monitor               | Memantau komunikasi D-Bus.                             |
| gammaray                   | Alat debugging untuk aplikasi Qt.                      |

{% hint style="info" %}
GammaRay adalah alat yang sangat berguna untuk debugging aplikasi Qt/QML. Ia memungkinkan Anda untuk memeriksa pohon objek QML, melacak signal dan slot, serta menganalisis performa rendering.
{% endhint %}

### 7.9 Studi Kasus: Membangun Widget dari Nol

Untuk mengilustrasikan semua konsep yang telah kita pelajari, mari kita bangun widget sederhana dari nol. Widget ini akan menampilkan informasi sistem—CPU, RAM, dan suhu—serta memungkinkan pengguna untuk mengonfigurasi interval refresh.

{% stepper %}
{% step %}
#### Langkah 1: Membuat Struktur Proyek

```bash
mkdir -p ~/kde-dev/widgets/system-monitor/package/contents/ui
cd ~/kde-dev/widgets/system-monitor

# Buat file-file dasar
touch CMakeLists.txt
touch package/metadata.json
touch package/contents/ui/main.qml
touch package/contents/ui/configGeneral.qml
touch LICENSE
```
{% endstep %}

{% step %}
#### Langkah 2: Menulis metadata.json

```json
{
    "KPackageStructure": "Plasma/Applet",
    "KPlugin": {
        "Authors": [
            {
                "Email": "you@example.com",
                "Name": "Nama Anda"
            }
        ],
        "Category": "System Information",
        "Description": "Menampilkan informasi sistem (CPU, RAM, suhu)",
        "Icon": "utilities-system-monitor",
        "Id": "com.example.systemmonitor",
        "License": "GPL-3.0+",
        "Name": "System Monitor",
        "Version": "1.0.0"
    },
    "X-Plasma-API-Minimum-Version": "6.0",
    "X-Plasma-ConfigUi": "configGeneral.qml"
}
```
{% endstep %}

{% step %}
#### Langkah 3: Menulis main.qml

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.plasmoid
import org.kde.plasma.core as PlasmaCore
import org.kde.plasma.components as PlasmaComponents
import org.kde.plasma.plasma5support as P5Support

PlasmoidItem {
    id: root

    // Konfigurasi default
    property int refreshInterval: 2
    property bool showCpu: true
    property bool showRam: true
    property bool showTemp: false

    // Data sistem
    property real cpuUsage: 0
    property real ramUsage: 0
    property real temperature: 0

    // Sumber data
    P5Support.DataSource {
        id: executable
        engine: "executable"
        connectedSources: []

        onNewData: function(sourceName, data) {
            const stdout = data["stdout"] || ""
            const lines = stdout.trim().split("\n")

            if (sourceName.includes("cpu")) {
                root.cpuUsage = parseFloat(lines[0]) || 0
            } else if (sourceName.includes("ram")) {
                root.ramUsage = parseFloat(lines[0]) || 0
            } else if (sourceName.includes("temp")) {
                root.temperature = parseFloat(lines[0]) || 0
            }

            disconnectSource(sourceName)
        }
    }

    // Timer untuk refresh
    Timer {
        interval: root.refreshInterval * 1000
        running: true
        repeat: true
        triggeredOnStart: true
        onTriggered: root.updateData()
    }

    function updateData() {
        if (root.showCpu) {
            executable.connectSource("sh -c \"top -bn1 | grep 'Cpu(s)' | awk '{print 100 - $8}'\"")
        }

        if (root.showRam) {
            executable.connectSource("sh -c \"free | grep Mem | awk '{print $3/$2 * 100.0}'\"")
        }

        if (root.showTemp) {
            executable.connectSource("sh -c \"cat /sys/class/thermal/thermal_zone0/temp 2>/dev/null | awk '{print $1/1000}'\"")
        }
    }

    preferredRepresentation: compactRepresentation

    compactRepresentation: RowLayout {
        spacing: PlasmaCore.Units.smallSpacing

        PlasmaComponents.Label {
            visible: root.showCpu
            text: "CPU: " + root.cpuUsage.toFixed(1) + "%"
        }

        PlasmaComponents.Label {
            visible: root.showRam
            text: "RAM: " + root.ramUsage.toFixed(1) + "%"
        }
    }

    fullRepresentation: ColumnLayout {
        Layout.minimumWidth: 220
        Layout.minimumHeight: 120
        Layout.preferredWidth: 250
        Layout.preferredHeight: 150

        PlasmaComponents.Label {
            text: "Informasi Sistem"
            font.bold: true
            font.pointSize: 12
            Layout.alignment: Qt.AlignHCenter
        }

        // CPU
        ColumnLayout {
            visible: root.showCpu
            Layout.fillWidth: true

            PlasmaComponents.Label {
                text: "CPU: " + root.cpuUsage.toFixed(1) + "%"
            }

            PlasmaComponents.ProgressBar {
                Layout.fillWidth: true
                from: 0
                to: 100
                value: root.cpuUsage
            }
        }

        // RAM
        ColumnLayout {
            visible: root.showRam
            Layout.fillWidth: true

            PlasmaComponents.Label {
                text: "RAM: " + root.ramUsage.toFixed(1) + "%"
            }

            PlasmaComponents.ProgressBar {
                Layout.fillWidth: true
                from: 0
                to: 100
                value: root.ramUsage
            }
        }

        // Suhu
        ColumnLayout {
            visible: root.showTemp
            Layout.fillWidth: true

            PlasmaComponents.Label {
                text: "Suhu: " + root.temperature.toFixed(1) + " C"
            }

            PlasmaComponents.ProgressBar {
                Layout.fillWidth: true
                from: 0
                to: 100
                value: Math.min(root.temperature, 100)
            }
        }
    }
}
```
{% endstep %}

{% step %}
#### Langkah 4: Menulis configGeneral.qml

```qml
import QtQuick
import QtQuick.Controls as QQC
import QtQuick.Layouts
import org.kde.kirigami as Kirigami
import org.kde.plasma.plasmoid

Kirigami.FormLayout {
    id: configRoot

    property alias cfg_refreshInterval: intervalSpin.value
    property alias cfg_showCpu: cpuCheck.checked
    property alias cfg_showRam: ramCheck.checked
    property alias cfg_showTemp: tempCheck.checked

    QQC.SpinBox {
        id: intervalSpin
        from: 1
        to: 60
        editable: true
        Kirigami.FormData.label: "Interval Refresh (detik):"
    }

    QQC.CheckBox {
        id: cpuCheck
        text: "Tampilkan penggunaan CPU"
        Kirigami.FormData.label: "Tampilkan:"
    }

    QQC.CheckBox {
        id: ramCheck
        text: "Tampilkan penggunaan RAM"
    }

    QQC.CheckBox {
        id: tempCheck
        text: "Tampilkan suhu CPU"
    }
}
```
{% endstep %}

{% step %}
#### Langkah 5: Menulis CMakeLists.txt

```cmake
cmake_minimum_required(VERSION 3.16)

project(system-monitor VERSION 1.0.0)

find_package(ECM 5.240.0 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH})

find_package(KF6 REQUIRED COMPONENTS Plasma)

plasma_install_package(package com.example.systemmonitor)
```
{% endstep %}

{% step %}
#### Langkah 6: Menguji Widget

```bash
# Masuk ke direktori proyek
cd ~/kde-dev/widgets/system-monitor

# Uji dengan plasmoidviewer
plasmoidviewer -a package

# Jika ada error, periksa output untuk debugging
# Setelah puas, instal widget
kpackagetool6 --type Plasma/Applet --install package

# Restart Plasma untuk melihat perubahan
kquitapp6 plasmashell && kstart plasmashell
```
{% endstep %}

{% step %}
#### Langkah 7: Iterasi dan Perbaikan

Setelah widget berfungsi, Anda dapat melakukan iterasi untuk menambahkan fitur:

* **Notifikasi:** Menampilkan notifikasi saat penggunaan CPU melebihi ambang batas.
* **Histori:** Menyimpan data historis dan menampilkan grafik.
* **Kustomisasi:** Menambahkan opsi konfigurasi lebih lanjut.
* **Tema:** Menyesuaikan warna dengan tema Plasma.
* **Lokalisasi:** Menambahkan terjemahan untuk berbagai bahasa.
{% endstep %}

{% step %}
#### Langkah 8: Menerbitkan ke KDE Store

1. Buat akun di [https://store.kde.org/](https://store.kde.org/).
2. Kemas widget Anda menjadi file `.tar.gz` atau `.zip`.
3. Unggah ke KDE Store dengan deskripsi, tangkapan layar, dan lisensi.
4. Promosikan widget Anda di forum dan media sosial.
5. Tanggapi umpan balik dan perbarui widget sesuai kebutuhan.

{% hint style="info" %}
Untuk menerbitkan widget, pastikan Anda memiliki:

* Ikon widget yang menarik.
* Tangkapan layar yang menunjukkan widget beraksi.
* Deskripsi yang jelas dan ringkas.
* Lisensi yang jelas (GPL-3.0+ atau LGPL-3.0+ direkomendasikan).
* Dokumentasi tentang cara menggunakan widget.
{% endhint %}
{% endstep %}
{% endstepper %}

### 7.10 Ringkasan Bab

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

## 8 Fitur Terbaru Plasma 6.x

> “Inovasi adalah perubahan yang menghasilkan nilai.”
>
> — Peter Drucker

KDE Plasma tidak pernah berhenti berkembang. Sejak peluncuran Plasma 6 pada Februari 2024, komunitas KDE telah merilis pembaruan demi pembaruan yang membawa fitur baru, peningkatan performa, dan penyempurnaan pengalaman pengguna. Bab ini mendokumentasikan perjalanan tersebut secara komprehensif, mencakup rilis Plasma 6.6 (Februari 2026) hingga Plasma 6.9 (yang direncanakan untuk awal 2027).

Setiap rilis diperiksa secara mendalam: fitur-fitur utamanya, alasan di baliknya, dan dampaknya bagi pengguna. Bab ini bukan sekadar daftar perubahan—ia adalah analisis tentang bagaimana KDE Plasma berevolusi untuk memenuhi kebutuhan pengguna modern.

### 8.1 Plasma 6.6 (Februari 2026)

Plasma 6.6 dirilis pada 17 Februari 2026, menandai rilis fitur pertama di tahun 2026. Rilis ini membawa beberapa modul baru yang signifikan, terutama di area manajemen login, perangkat sentuh, dan aksesibilitas.

#### 8.1.1 Modul Baru

Plasma 6.6 memperkenalkan tiga modul baru yang signifikan:

**Plasma Login Manager (PLM)**

Plasma Login Manager (PLM) adalah manajer login opsional baru yang dikembangkan oleh KDE. Ia merupakan alternatif dari SDDM (Simple Desktop Display Manager) yang telah lama menjadi default di KDE Plasma.

{% hint style="info" %}
**Plasma Login Manager (PLM)** adalah manajer login berbasis QML yang dikembangkan oleh KDE. Ia menyediakan integrasi yang lebih erat dengan KDE Plasma, dengan greeter yang dapat dikustomisasi, dukungan untuk plugin wallpaper, dan modul konfigurasi System Settings tersendiri.
{% endhint %}

PLM dikembangkan sebagai upaya untuk menyediakan pengalaman login yang lebih terintegrasi dengan KDE Plasma. Meskipun pada awalnya sebagian besar merupakan SDDM yang direfaktor, tujuannya adalah integrasi yang lebih erat dengan Plasma di masa depan. PLM juga menyertakan modul System Settings-nya sendiri, berdasarkan sddm-kcm6.

{% hint style="info" %}
PLM bergantung pada systemd, sehingga tidak tersedia untuk distribusi yang tidak menggunakan systemd. Untuk distribusi tersebut, SDDM tetap menjadi pilihan utama.
{% endhint %}

Beberapa distribusi, seperti Fedora Linux 44, CachyOS, dan EndeavourOS, telah mengadopsi PLM sebagai manajer login default mereka. Fedora secara resmi mengumumkan bahwa semua varian KDE mereka akan beralih dari SDDM ke PLM.

```bash
# Instalasi PLM
sudo dnf install plasma-login-manager kcm-plasmalogin

# Aktifkan layanan PLM
sudo systemctl enable --force plasmalogin.service
```

**Plasma-Keyboard**

Plasma-Keyboard adalah keyboard on-screen terintegrasi yang dirancang untuk tablet dan perangkat sentuh. Fitur ini sangat penting untuk perangkat seperti tablet dan laptop konvertibel yang tidak memiliki keyboard fisik.

* **Integrasi dengan Plasma:** Keyboard muncul secara otomatis saat bidang input difokuskan.
* **Mode penuh dan ringkas:** Pengguna dapat memilih antara keyboard penuh dan mode ringkas.
* **Dukungan multibahasa:** Keyboard mendukung berbagai tata letak dan bahasa.
* **Prediksi teks:** Saran kata saat mengetik.

**Plasma-Setup**

Plasma-Setup adalah alat konfigurasi awal yang membantu pengguna baru mengatur preferensi dasar setelah instalasi.

* Pemilihan bahasa dan wilayah.
* Pengaturan tata letak keyboard.
* Konfigurasi zona waktu.
* Koneksi jaringan.
* Pemilihan tema awal.

#### 8.1.2 Fitur Spectacle OCR

Salah satu fitur yang paling banyak dibicarakan dari Plasma 6.6 adalah kemampuan OCR (Optical Character Recognition) di Spectacle, alat screenshot KDE Plasma.

{% hint style="info" %}
**OCR (Optical Character Recognition)** adalah teknologi yang memungkinkan komputer untuk mengekstrak teks dari gambar. Di Spectacle, fitur ini memungkinkan pengguna untuk menyalin teks dari screenshot tanpa harus mengetik ulang.
{% endhint %}

Dengan fitur ini, pengguna dapat:

{% stepper %}
{% step %}
Mengambil screenshot area yang mengandung teks.
{% endstep %}

{% step %}
Mengaktifkan mode OCR di Spectacle.
{% endstep %}

{% step %}
Memilih teks yang ingin diekstrak.
{% endstep %}

{% step %}
Menyalin teks ke clipboard untuk digunakan di aplikasi lain.
{% endstep %}
{% endstepper %}

Fitur ini sangat berguna untuk:

* Menyalin teks dari gambar atau video yang tidak dapat dipilih.
* Mengekstrak teks dari dokumen yang dipindai.
* Mengambil kode dari screenshot tutorial.
* Menerjemahkan teks dari gambar.

#### 8.1.3 Filter Buta Warna dan Filter Grayscale

Plasma 6.6 menambahkan filter grayscale baru di dalam fitur Color Blindness. Filter ini memungkinkan pengguna untuk:

* Mengaktifkan mode grayscale untuk seluruh layar.
* Mengurangi kelelahan mata saat membaca dalam waktu lama.
* Membantu pengguna dengan sensitivitas warna tertentu.
* Menghemat daya pada layar OLED karena piksel putih tidak menyala penuh.

#### 8.1.4 Kecerahan Layar Otomatis

Plasma 6.6 memperkenalkan fitur kecerahan layar otomatis untuk perangkat yang memiliki sensor cahaya sekitar (ambient light sensor). Fitur ini secara otomatis menyesuaikan kecerahan layar berdasarkan kondisi pencahayaan di sekitar perangkat.

* Mengurangi kelelahan mata dalam kondisi cahaya yang berubah-ubah.
* Menghemat daya baterai dengan menyesuaikan kecerahan secara dinamis.
* Dapat diaktifkan atau dinonaktifkan melalui System Settings.

#### 8.1.5 Wi-Fi via QR Code

Plasma 6.6 menambahkan kemampuan untuk terhubung ke jaringan Wi-Fi dengan memindai kode QR. Fitur ini sangat berguna untuk:

* Terhubung ke jaringan Wi-Fi publik tanpa mengetik kata sandi.
* Berbagi kredensial Wi-Fi dengan tamu.
* Terhubung ke jaringan yang kompleks dengan mudah.

#### 8.1.6 Animasi Lebih Halus

Plasma 6.6 meningkatkan animasi pada layar dengan refresh rate tinggi. Animasi sekarang lebih halus dan responsif, terutama pada monitor 120 Hz, 144 Hz, atau lebih tinggi.

#### 8.1.7 Peningkatan Lainnya

* **Emoji Selector:** Pemilih warna kulit (skin tone) baru di panel emoji.
* **XRandr Emulation:** Emulasi XRandr di KWin untuk kompatibilitas aplikasi XWayland yang lebih baik.
* **Per-DRM-Plane Color Pipeline:** Dukungan pipeline warna per-DRM-plane.
* **Custom Screen Mode:** Dukungan mode layar kustom di sesi Wayland.
* **Slow Keys:** Fitur aksesibilitas baru untuk pengguna dengan tremor.
* **Penanganan Baterai:** Peningkatan penanganan baterai pada laptop.
* **Global Actions untuk Media:** Aksi global untuk seek maju/mundur dalam pemutaran media.
* **Window List Widget:** Fitur baru termasuk open-on-hover, menyembunyikan ikon, dan filter yang dapat dikonfigurasi.

#### 8.1.8 Analisis

Plasma 6.6 adalah rilis yang berfokus pada perangkat sentuh dan aksesibilitas. Fitur seperti Plasma-Keyboard dan ambient light sensor menunjukkan bahwa KDE serius tentang dukungan perangkat mobile dan tablet. Fitur OCR di Spectacle adalah contoh bagaimana fitur yang sebelumnya memerlukan aplikasi pihak ketiga sekarang terintegrasi langsung ke dalam ekosistem Plasma.

| Rilis | Tanggal |
| ----- | ------- |
| 6.6.0 | 17 Feb  |
| 6.6.1 | 24 Feb  |
| 6.6.2 | 10 Mar  |
| 6.6.3 | 17 Mar  |
| 6.6.4 | 7 Apr   |
| 6.6.5 | 12 Mei  |

_Gambar 8.1: Siklus rilis Plasma 6.6 dengan pembaruan bugfix bulanan. Setiap rilis membawa perbaikan bug dan peningkatan stabilitas._

### 8.2 Plasma 6.7 (Juni 2026)

Plasma 6.7 dirilis pada 16 Juni 2026, dan digambarkan sebagai “pembangkit produktivitas yang menyenangkan untuk digunakan”. Rilis ini membawa beberapa fitur yang telah lama ditunggu-tunggu oleh komunitas.

#### 8.2.1 Virtual Desktop per Layar

Setelah 21 tahun, fitur virtual desktop per layar akhirnya tiba di KDE Plasma. Fitur ini memungkinkan setiap monitor untuk memiliki set virtual desktop-nya sendiri, sehingga pengguna dapat beralih antar virtual desktop secara independen di setiap layar.

{% hint style="info" %}
**Virtual Desktop per Layar** adalah fitur yang memungkinkan setiap monitor fisik untuk memiliki set virtual desktop yang independen. Misalnya, monitor kiri dapat berada di Desktop 1 sementara monitor kanan berada di Desktop 3.
{% endhint %}

Fitur ini sangat berguna untuk pengguna dengan konfigurasi multi-monitor yang kompleks. Sebelumnya, semua monitor berbagi set virtual desktop yang sama, sehingga beralih desktop di satu monitor akan mengubah semua monitor.

Fitur ini tidak diaktifkan secara default. Pengguna harus mengaktifkannya dengan mencentang “Switch desktops independently for each screen” di bagian Virtual Desktops di pengaturan.

```
Setiap monitor dapat beralih desktop secara independen

Monitor Kiri                Monitor Kanan
1  2  3                     A  B  C

Desktop 2                   Desktop C
```

_Gambar 8.2: Virtual Desktop per Layar di Plasma 6.7. Setiap monitor dapat berada di virtual desktop yang berbeda secara bersamaan._

#### 8.2.2 Tombol Terang/Gelap Cepat

Plasma 6.7 menambahkan tombol cepat di system tray untuk beralih antara Global Theme terang dan gelap. Di Plasma 6.6, pengguna sudah dapat membuat Global Theme kustom dan beralih di antaranya berdasarkan siklus siang-malam. Plasma 6.7 memberikan kontrol yang lebih langsung dengan tombol toggle cepat.

#### 8.2.3 Tes Volume Mikrofon

Fitur baru untuk menguji volume mikrofon sebelum bergabung dengan panggilan video atau konferensi. Ini menghilangkan kebutuhan untuk bertanya “apakah mikrofon saya berfungsi?” atau “apakah volume saya terlalu keras?”.

#### 8.2.4 Press-and-Hold untuk Karakter Khusus

Dengan keyboard virtual Plasma yang diaktifkan, menekan dan menahan tombol akan memunculkan karakter khusus yang terkait. Fitur ini mirip dengan yang ada di keyboard ponsel, dan sangat berguna untuk mengetik karakter non-standar.

#### 8.2.5 Kalender Lunar Vietnam

Plasma 6.7 menambahkan kalender lunar Vietnam ke set kalender non-Gregorian yang tersedia. Pengguna sekarang dapat melacak tanggal dan acara menggunakan kedua sistem kalender dengan lebih mudah.

#### 8.2.6 “Background Apps” di System Tray

System Tray sekarang juga menampilkan aplikasi yang menggunakan sistem “Background Apps” yang lebih baru, yang umum untuk aplikasi dengan format paket Flatpak. Ini memberikan visibilitas yang lebih baik tentang aplikasi apa yang berjalan di latar belakang.

#### 8.2.7 Manajemen Printer yang Lebih Baik

Dukungan pencetakan KDE Plasma terus matang. Ikon printer di System Tray sekarang menampilkan jumlah tugas aktif dalam badge kecil. Untuk perusahaan, Plasma 6.7 membuat koneksi ke printer bersama di jaringan Windows menjadi lebih mudah, dan alat manajemen antrian cetak baru menawarkan lebih banyak kekuatan.

#### 8.2.8 Peningkatan Usability

* **Perpindahan Virtual Desktop Lebih Cepat di Overview:** Saat membuka Overview dengan `Meta + W`, pengguna dapat beralih virtual desktop dengan scroll atau tombol `Page Up`/`Page Down`.
* **Drag-and-Drop Favorit:** Menambahkan atau menghapus aplikasi favorit di Application Launcher, Application Menu, dan Application Dashboard kini semudah drag-and-drop.
* **Manajemen Perangkat Lunak Lebih Intuitif:** Discover sekarang memiliki tombol “Install” yang lebih jelas, kartu aplikasi yang didesain ulang, dan pengurutan yang lebih intuitif.
* **Perbandingan Zona Waktu:** Digital Clock widget sekarang menampilkan berapa jam lebih awal atau lebih lambat setiap zona waktu dibandingkan zona waktu lokal.
* **Type-ahead di Desktop:** Mode untuk memilih berkas dengan mengetik di desktop.

#### 8.2.9 Kembalinya Tema Oxygen dan Air

Sebagai persiapan untuk ulang tahun ke-30 KDE, tema Oxygen—yang digunakan oleh KDE 4—dihidupkan kembali. Tema ini tersedia sebagai opsi untuk pengguna yang merindukan tampilan klasik KDE.

#### 8.2.10 Sistem Tema Union

Plasma 6.7 juga memperkenalkan Union, sistem tema berbasis CSS yang baru. Ini adalah pratinjau teknologi yang akan menjadi fondasi untuk sistem tema KDE Plasma di masa depan.

#### 8.2.11 Analisis

Plasma 6.7 adalah rilis yang berfokus pada produktivitas dan multi-monitor. Virtual desktop per layar adalah fitur yang telah lama diminta komunitas, dan implementasinya menunjukkan komitmen KDE untuk mendengarkan umpan balik pengguna. Fitur seperti tes volume mikrofon dan perbandingan zona waktu menunjukkan perhatian terhadap detail dan kebutuhan praktis pengguna sehari-hari.

{% hint style="info" %}
Plasma 6.7 adalah rilis terakhir yang menyertakan sesi X11. Mulai Plasma 6.8, sesi X11 akan dihapus sepenuhnya, dan hanya sesi Wayland yang tersedia.
{% endhint %}

### 8.3 Plasma 6.8 (Oktober 2026)

Plasma 6.8 dijadwalkan rilis pada 20 Oktober 2026. Rilis ini menandai tonggak penting dalam sejarah KDE Plasma: penghapusan sesi X11 dan pengenalan beberapa modul baru yang signifikan.

#### 8.3.1 Penghapusan Sesi X11

Plasma 6.8 adalah rilis pertama yang tidak menyertakan sesi X11 untuk login. Pengguna hanya dapat login ke sesi Wayland. Namun, dukungan XWayland tetap ada, sehingga aplikasi X11 masih dapat berjalan.

{% hint style="warning" %}
Jika Anda masih bergantung pada sesi X11, Anda harus tetap menggunakan Plasma 6.7, yang merupakan rilis terakhir dengan dukungan X11. Pastikan untuk menguji aplikasi dan alur kerja Anda di Wayland sebelum beralih ke Plasma 6.8.
{% endhint %}

Keputusan ini diambil setelah data internal KDE menunjukkan bahwa lebih dari 95% pengguna Plasma 6.6 sudah menggunakan Wayland, dan “praktis tidak ada yang menguji atau mengembangkan Plasma di X11 lagi”. Dengan menghapus X11, pengembang dapat fokus pada satu jalur kode, yang akan memungkinkan “peningkatan performa, optimalisasi memori, dan fitur-fitur baru yang menarik”.

#### 8.3.2 Kup: Penjadwal Backup

Plasma 6.8 memperkenalkan Kup, penjadwal backup untuk desktop Plasma. Kup adalah aplikasi backup berbasis btrfs yang sekarang menjadi modul kelas satu di Plasma.

{% hint style="info" %}
**Kup** adalah penjadwal backup yang memungkinkan pengguna untuk mengonfigurasi backup otomatis ke disk eksternal atau perangkat penyimpanan lain yang terpasang. Kup mendukung backup inkremental, sehingga hanya berkas yang berubah yang di-backup.
{% endhint %}

Fitur Kup meliputi:

* Backup otomatis berdasarkan jadwal.
* Dukungan untuk backup inkremental.
* Integrasi dengan disk eksternal dan perangkat penyimpanan lain.
* Antarmuka grafis yang terintegrasi dengan System Settings.

#### 8.3.3 Union Theming untuk QtWidgets

Plasma 6.8 melanjutkan pengembangan sistem tema Union dengan menambahkan dukungan untuk aplikasi QtWidgets, seperti Dolphin dan Kate.

{% hint style="info" %}
Dukungan Union untuk QtWidgets masih bersifat preliminer dan mungkin mengandung bug. Pengguna yang ingin menguji dapat melaporkan masalah di [https://bugs.kde.org/](https://bugs.kde.org/enter_bug.cgi?product=Union) [enter\_bug.cgi?product=Union.](https://bugs.kde.org/enter_bug.cgi?product=Union)
{% endhint %}

Untuk menguji Union:

{% stepper %}
{% step %}
Pastikan paket union terinstal.
{% endstep %}

{% step %}
Buka System Settings.
{% endstep %}

{% step %}
Navigasi ke Colors & Themes Application Style.
{% endstep %}

{% step %}
Pilih “Breeze (Union)”.
{% endstep %}

{% step %}
Klik Apply.
{% endstep %}
{% endstepper %}

#### 8.3.4 Fitur Lainnya

* **Shadows dan Rounded Corners untuk Steam:** Bayangan dan sudut membulat untuk jendela Steam.
* **Remote Desktop:** Peningkatan untuk Remote Desktop.
* **Aksesibilitas:** Fitur aksesibilitas baru.
* **Perekaman Layar:** Fitur baru untuk perekaman layar.
* **Spectacle Audio:** Spectacle sekarang dapat merekam audio selama perekaman layar.
* **NVIDIA Triple Buffering:** Triple buffering diaktifkan secara default untuk pengguna NVIDIA.

#### 8.3.5 Analisis

Plasma 6.8 adalah rilis yang berfokus pada masa depan Wayland dan integrasi fitur. Penghapusan sesi X11 adalah keputusan berani yang menunjukkan kepercayaan KDE pada Wayland. Pengenalan Kup sebagai modul kelas satu menunjukkan bahwa KDE serius tentang data integrity dan backup. Union theming, meskipun masih dalam tahap awal, menunjukkan arah masa depan sistem tema KDE Plasma.

| Fitur Utama    | Keterangan        |
| -------------- | ----------------- |
| X11            | Dihapus           |
| Kup            | Backup Scheduler  |
| Union          | QtWidgets Support |
| Remote Desktop | Improvements      |

_Gambar 8.3: Ringkasan fitur utama Plasma 6.8. Rilis ini menandai transisi penuh ke Wayland dan pengenalan modul Kup._

### 8.4 Plasma 6.9 (2027)

Plasma 6.9 adalah rilis berikutnya setelah 6.8, dijadwalkan untuk awal 2027. Meskipun masih dalam pengembangan, beberapa fitur telah diumumkan.

#### 8.4.1 Perbaikan KRunner

KRunner di Plasma 6.9 akan lebih fleksibel dalam konversi mata uang: pengguna dapat menempatkan simbol mata uang di sisi mana pun dari angka, dan KRunner akan tetap mengenalinya.

```
# Semua format ini akan dikenali:
100 USD to EUR
USD 100 to EUR
100 to EUR
$100 to EUR
```

#### 8.4.2 Perbaikan Widget Cuaca

Widget Weather Report sekarang akan memberikan peringatan ketika penyedia cuaca yang dipilih mungkin memberikan data yang lebih sedikit dari yang diharapkan. Pengguna juga dapat mencari stasiun cuaca yang namanya mengandung tanda baca tanpa harus menyertakan tanda baca tersebut.

#### 8.4.3 Thumbnail Virtual Desktop di Overview

Plasma 6.9 akan membuat thumbnail virtual desktop di efek Overview KWin menjadi lebih “harmonis dan menyenangkan secara visual”.

#### 8.4.4 Kontrol Kecerahan Keyboard Backlit

Plasma 6.9 akan memungkinkan kontrol tingkat kecerahan keyboard backlit yang terhubung setelah login awal.

#### 8.4.5 Perbaikan Rename File di Desktop

Saat mengganti nama berkas atau folder di desktop, semua peringatan dan konfirmasi standar akan ditampilkan bila diperlukan, misalnya saat menyembunyikan berkas atau mengubah jenis/ekstensi berkas.

#### 8.4.6 Locale C.UTF-8

Locale C.UTF-8 sekarang tersedia di halaman Region & Language di System Settings.

#### 8.4.7 Broadcast Notifications D-Bus Policy

Plasma 6.9 akan menyertakan kebijakan D-Bus untuk broadcast notifications yang hanya mengizinkan root untuk mengirimnya. Sebelumnya, pengguna lokal mana pun dapat mengirim broadcast notification `ListenForBroadcasts` pada sistem dengan diaktifkan.

#### 8.4.8 Analisis

Plasma 6.9 adalah rilis yang berfokus pada penyempurnaan dan perbaikan. Fitur-fitur seperti perbaikan KRunner, peringatan cuaca, dan kontrol keyboard backlit menunjukkan bahwa KDE terus memperhatikan detail dan pengalaman pengguna sehari-hari. Perubahan kebijakan D-Bus menunjukkan komitmen terhadap keamanan.

### 8.5 Analisis: Arah Pengembangan Plasma

Dari fitur-fitur yang diperkenalkan di Plasma 6.6 hingga 6.9, kita dapat mengidentifikasi beberapa tren utama dalam pengembangan KDE Plasma.

#### 8.5.1 Tren 1: Transisi Penuh ke Wayland

Transisi ke Wayland adalah perubahan paling signifikan dalam siklus Plasma 6.x. Dimulai dengan Wayland sebagai default di Plasma 6.0, dan berakhir dengan penghapusan sesi X11 di Plasma 6.8, KDE telah menunjukkan komitmen penuh terhadap Wayland.

| Status Wayland               | Rilis   |
| ---------------------------- | ------- |
| Default                      | 6.0     |
| Matang                       | 6.5–6.7 |
| X11 dihapus                  | 6.8     |
| Wayland satu-satunya pilihan | 6.9     |

_Gambar 8.4: Tren adopsi Wayland vs X11 di Plasma 6.x. Wayland menjadi default di Plasma 6.0, matang di 6.5–6.7, dan menjadi satu-satunya pilihan di Plasma 6.8._

#### 8.5.2 Tren 2: Integrasi Fitur

Plasma semakin terintegrasi dengan fitur-fitur yang sebelumnya memerlukan aplikasi pihak ketiga. Contohnya:

* **OCR di Spectacle (Plasma 6.6):** Sebelumnya memerlukan alat OCR terpisah.
* **Kup Backup (Plasma 6.8):** Sebelumnya memerlukan aplikasi backup terpisah.
* **Kontrol Mikrofon (Plasma 6.7):** Sebelumnya memerlukan aplikasi audio terpisah.
* **Manajemen Printer (Plasma 6.7):** Peningkatan signifikan dalam integrasi printer.

#### 8.5.3 Tren 3: Fokus pada Perangkat Sentuh

Plasma 6.6 memperkenalkan Plasma-Keyboard, dan Plasma 6.7 menambahkan press-and-hold untuk karakter khusus. Ini menunjukkan bahwa KDE serius tentang dukungan perangkat sentuh dan tablet.

#### 8.5.4 Tren 4: Personaalisasi yang Lebih Dalam

Fitur seperti Global Theme kustom (6.6), toggle terang/gelap cepat (6.7), dan Union theming (6.8) menunjukkan bahwa KDE Plasma terus meningkatkan kemampuan kustomisasi.

#### 8.5.5 Tren 5: Keamanan dan Privasi

Perubahan kebijakan D-Bus untuk broadcast notifications (6.9) menunjukkan bahwa KDE memperhatikan keamanan dan privasi pengguna.

### 8.6 Ringkasan Bab

Bab ini telah membahas fitur-fitur terbaru Plasma 6.x secara komprehensif:

* **Plasma 6.6 (Februari 2026):** Memperkenalkan Plasma Login Manager (PLM), Plasma-Keyboard, Plasma-Setup, OCR di Spectacle, filter buta warna, kecerahan layar otomatis, dan Wi-Fi via QR code.
* **Plasma 6.7 (Juni 2026):** Menghadirkan virtual desktop per layar, tombol terang/gelap cepat, tes volume mikrofon, press-and-hold untuk karakter khusus, kalender lunar Vietnam, dan “Background Apps” di System Tray.
* **Plasma 6.8 (Oktober 2026):** Menghapus sesi X11, memperkenalkan Kup sebagai penjadwal backup, dan memperluas Union theming ke aplikasi QtWidgets.
* **Plasma 6.9 (2027):** Akan membawa perbaikan KRunner untuk konversi mata uang, peringatan cuaca, thumbnail virtual desktop yang lebih baik, dan kontrol keyboard backlit.
* **Tren pengembangan:** Transisi penuh ke Wayland, integrasi fitur, fokus pada perangkat sentuh, personalisasi yang lebih dalam, dan peningkatan keamanan.

Bab selanjutnya akan membahas pemecahan masalah KDE Plasma, termasuk masalah umum, masalah login, masalah multi-layar, masalah NVIDIA, HiDPI scaling, dan sumber daya pemecahan masalah.

## Bagian IV

## Sumber Daya

## 9 Pemecahan Masalah

> “Setiap masalah adalah peluang untuk belajar, jika kita mau mendengarkan.”
>
> — Anonim, dikutip dalam semangat komunitas KDE

Tidak ada sistem perangkat lunak yang sempurna, dan KDE Plasma bukanlah pengecualian. Meskipun telah melalui pengujian yang ketat oleh ribuan kontributor dan jutaan pengguna, masalah tetap dapat terjadi. Bab ini menyediakan panduan komprehensif untuk mendiagnosis dan menyelesaikan masalah yang paling umum dihadapi pengguna KDE Plasma. Kita akan membahas dari masalah sederhana seperti widget yang tidak muncul, hingga masalah kompleks seperti crash sistem yang memerlukan analisis coredump. Tujuan bab ini bukan hanya memberikan solusi cepat, tetapi juga mengajarkan metodologi pemecahan masalah yang sistematis, sehingga Anda dapat menyelesaikan masalah baru yang belum pernah ditemui.

### 9.1 Metodologi Pemecahan Masalah

Sebelum masuk ke masalah spesifik, penting untuk memahami metodologi pemecahan masalah yang sistematis. Pendekatan yang terstruktur akan menghemat waktu dan menghindari frustrasi.

#### 9.1.1 Prinsip Dasar

Pemecahan masalah KDE Plasma mengikuti beberapa prinsip dasar:

{% stepper %}
{% step %}
### Reproduksi Masalah

Sebelum mencoba memperbaiki, pastikan Anda dapat mereproduksi masalah secara konsisten. Masalah yang tidak dapat direproduksi sangat sulit didiagnosis.
{% endstep %}

{% step %}
### Isolasi Masalah

Tentukan apakah masalah berasal dari KDE Plasma, aplikasi tertentu, driver, atau perangkat keras. Uji di lingkungan yang berbeda untuk mengisolasi.
{% endstep %}

{% step %}
### Kumpulkan Informasi

Baca log, periksa versi, catat langkah-langkah yang menyebabkan masalah. Informasi ini penting untuk diagnosis dan pelaporan bug.
{% endstep %}

{% step %}
### Ubah Satu Variabel pada Satu Waktu

Saat menguji solusi, ubah hanya satu hal pada satu waktu. Ini membantu mengidentifikasi penyebab sebenarnya.
{% endstep %}

{% step %}
### Dokumentasikan

Catat apa yang Anda coba dan hasilnya. Ini berguna jika Anda perlu meminta bantuan atau melaporkan bug.
{% endstep %}
{% endstepper %}

#### 9.1.2 Tingkat Keparahan Masalah

Masalah KDE Plasma dapat dikategorikan berdasarkan tingkat keparahan:

| Tingkat | Contoh                                                        |
| ------- | ------------------------------------------------------------- |
| Kritis  | Sistem tidak dapat boot, data hilang                          |
| Berat   | Plasma crash berulang, tidak dapat login                      |
| Sedang  | Widget tidak muncul, efek tidak berfungsi                     |
| Ringan  | Kosmetik, kinerja sedikit menurun, preferensi tidak tersimpan |

{% hint style="info" %}
Sebelum melakukan perubahan apa pun, selalu buat backup konfigurasi Anda. Untuk KDE Plasma, backup direktori `~/.config/` dan `~/.local/share/plasma/`. Ini memungkinkan Anda untuk kembali ke keadaan semula jika terjadi kesalahan.
{% endhint %}

#### 9.1.3 Alat Diagnostik

Beberapa alat diagnostik yang akan sering digunakan:

| Alat             | Kegunaan                                                                   |
| ---------------- | -------------------------------------------------------------------------- |
| `journalctl`     | Membaca log systemd. Berguna untuk melihat log Plasma, KWin, dan aplikasi. |
| `dmesg`          | Membaca log kernel. Berguna untuk masalah driver dan perangkat keras.      |
| `kcmshell6`      | Menjalankan modul konfigurasi (KCM) secara langsung.                       |
| `kscreen-doctor` | Mendiagnosis masalah display dan multi-monitor.                            |
| `qdbus`          | Berinteraksi dengan layanan D-Bus.                                         |
| `coredumpctl`    | Melihat dan menganalisis core dump.                                        |
| `strace`         | Melacak system call untuk masalah lanjutan.                                |
| `gdb`            | Debugger untuk menganalisis crash.                                         |

```bash
# Melihat log Plasma
journalctl --user -u plasma-plasmashell.service -b

# Melihat log KWin
journalctl --user -u plasma-kwin_wayland.service -b

# Melihat log sistem
journalctl -b

# Melihat log kernel
dmesg

# Melihat crash terbaru
coredumpctl list

# Melihat crash tertentu
coredumpctl info <PID>

# Melihat status display
kscreen-doctor -o
```

### 9.2 Masalah Umum

Bagian ini membahas masalah-masalah umum yang sering dihadapi pengguna KDE Plasma.

#### 9.2.1 Aplikasi Crash atau Menolak Diluncurkan

Ini adalah salah satu masalah paling umum. Aplikasi mungkin crash saat diluncurkan, saat melakukan tindakan tertentu, atau secara acak.

**Diagnosis**

{% stepper %}
{% step %}
### Periksa log aplikasi

Jalankan aplikasi dari terminal untuk melihat pesan error.
{% endstep %}

{% step %}
### Periksa crash

Gunakan `coredumpctl list` untuk melihat crash terbaru.
{% endstep %}

{% step %}
### Periksa dependensi

Gunakan `ldd` untuk memeriksa apakah semua dependensi terpenuhi.
{% endstep %}

{% step %}
### Uji dengan pengguna baru

Buat akun pengguna baru dan coba jalankan aplikasi. Jika berhasil, masalahnya terkait konfigurasi pengguna.
{% endstep %}
{% endstepper %}

```bash
# Jalankan aplikasi dari terminal
firefox

# Periksa crash terbaru
coredumpctl list

# Lihat detail crash
coredumpctl info firefox

# Periksa dependensi
ldd /usr/bin/firefox

# Periksa apakah ada lib yang hilang
ldd /usr/bin/firefox | grep "not found"

# Cek versi library
pacman -Qi firefox # Arch
apt list --installed | grep firefox # Ubuntu
dnf info firefox # Fedora
```

**Solusi Umum**

1. Perbarui sistem: Pastikan semua paket dalam versi terbaru.
2. Reset konfigurasi: Hapus atau ganti nama direktori konfigurasi aplikasi di `~/.config/`.
3. Instal dependensi: Instal paket yang hilang yang dilaporkan oleh `ldd`.
4. Coba pengguna baru: Jika berhasil, konfigurasi pengguna lama kemungkinan rusak.
5. Periksa log: Baca log untuk pesan error yang lebih spesifik.

{% hint style="warning" %}
Saat menghapus konfigurasi aplikasi, Anda akan kehilangan pengaturan, riwayat, dan data yang terkait. Selalu backup terlebih dahulu dengan mengganti nama direktori (`mv application application.backup`) daripada menghapusnya.
{% endhint %}

#### 9.2.2 Layar Menjadi Hitam atau Blank

Layar hitam adalah masalah yang menakutkan tetapi sering dapat diatasi dengan relatif mudah.

**Diagnosis**

{% stepper %}
{% step %}
### Beralih ke TTY lain

Gunakan `Ctrl + Alt + F2` hingga `F6`.
{% endstep %}

{% step %}
### Login sebagai pengguna Anda
{% endstep %}

{% step %}
### Periksa log KWin atau X11
{% endstep %}

{% step %}
### Periksa apakah ada proses yang menggunakan GPU secara intensif
{% endstep %}
{% endstepper %}

```bash
# Beralih ke TTY
Ctrl + Alt + F3

# Periksa log KWin
journalctl --user -u plasma-kwin_wayland.service -b

# Periksa penggunaan GPU
nvidia-smi # Untuk NVIDIA
radeontop # Untuk AMD
intel_gpu_top # Untuk Intel

# Periksa apakah ada proses yang crash
coredumpctl list

# Cek status display
kscreen-doctor -o
```

**Solusi**

1. Restart KWin: Jalankan `kwin_wayland –replace` dari TTY.
2. Reset konfigurasi KWin: Hapus `~/.config/kwinrc`.
3. Nonaktifkan efek: Matikan efek kompositing untuk melihat apakah itu penyebabnya.
4. Perbarui driver: Pastikan driver GPU dalam versi terbaru.
5. Gunakan `nomodeset`: Tambahkan `nomodeset` ke parameter kernel sebagai solusi sementara.

{% hint style="info" %}
Jika layar hitam terjadi setelah pembaruan, masalahnya kemungkinan terkait dengan driver grafis atau KWin. Baca catatan rilis pembaruan dan periksa forum untuk masalah serupa.
{% endhint %}

#### 9.2.3 Widget Tidak Muncul atau Tidak Berfungsi

Widget adalah salah satu fitur khas KDE Plasma, tetapi kadang-kadang mereka tidak muncul atau tidak berfungsi dengan baik.

**Diagnosis**

{% stepper %}
{% step %}
### Periksa apakah widget terinstal dengan benar
{% endstep %}

{% step %}
### Periksa apakah widget kompatibel dengan versi Plasma Anda
{% endstep %}

{% step %}
### Periksa log Plasma untuk pesan error QML
{% endstep %}

{% step %}
### Coba hapus dan tambahkan kembali widget
{% endstep %}
{% endstepper %}

```bash
# Lihat daftar widget yang terinstal
kpackagetool6 --type Plasma/Applet --list

# Periksa apakah widget ada di direktori yang benar
ls ~/.local/share/plasma/plasmoids/
ls /usr/share/plasma/plasmoids/

# Lihat log Plasma untuk error QML
journalctl --user -u plasma-plasmashell.service -b | grep -i "qml\|widget\|error"

# Restart Plasma Shell
kquitapp6 plasmashell && kstart plasmashell
```

**Solusi**

1. Reset konfigurasi widget: Hapus `~/.config/plasma-org.kde.plasma.desktop-appletsrc`.
2. Hapus cache Plasma: Hapus `~/.cache/plasma*`.
3. Instal ulang widget: Hapus dan instal ulang widget yang bermasalah.
4. Periksa kompatibilitas: Pastikan widget kompatibel dengan versi Plasma Anda.

```bash
# Backup konfigurasi widget
cp ~/.config/plasma-org.kde.plasma.desktop-appletsrc ~/plasma-appletsrc.backup

# Hapus cache
rm -rf ~/.cache/plasma*

# Restart Plasma Shell
kquitapp6 plasmashell && kstart plasmashell

# Jika masih bermasalah, reset total
rm ~/.config/plasma-org.kde.plasma.desktop-appletsrc
kquitapp6 plasmashell && kstart plasmashell
```

{% hint style="info" %}
Menghapus `plasma-org.kde.plasma.desktop-appletsrc` akan mereset semua tata letak panel dan widget ke default. Semua widget kustom yang telah Anda tambahkan akan hilang.
{% endhint %}

#### 9.2.4 Efek Desktop Tidak Berfungsi

Efek desktop seperti blur, cube, dan wobbly windows adalah salah satu fitur yang paling menarik di KDE Plasma, tetapi kadang-kadang mereka tidak berfungsi.

**Diagnosis**

{% stepper %}
{% step %}
### Periksa apakah kompositing diaktifkan
{% endstep %}

{% step %}
### Periksa apakah driver GPU mendukung efek yang diinginkan
{% endstep %}

{% step %}
### Periksa apakah efek diaktifkan di pengaturan KWin
{% endstep %}

{% step %}
### Periksa apakah ada konflik dengan efek lain
{% endstep %}
{% endstepper %}

```bash
# Periksa apakah kompositing aktif
qdbus org.kde.KWin /Compositor active

# Lihat daftar efek
qdbus org.kde.KWin /Effects loadedEffects

# Periksa log KWin
journalctl --user -u plasma-kwin_wayland.service -b | grep -i "effect\|composit"

# Test efek
qdbus org.kde.KWin /Effects org.kde.kwin.Effects.loadEffect blur
```

**Solusi**

1. Aktifkan kompositing: Pastikan kompositing diaktifkan di System Settings Display and Monitor Compositor.
2. Ubah backend rendering: Coba ganti antara OpenGL 2.0, OpenGL 3.1, dan XRender.
3. Nonaktifkan efek yang tidak kompatibel: Beberapa efek tidak berfungsi dengan driver tertentu.
4. Perbarui driver GPU: Driver lama mungkin tidak mendukung semua efek.

{% hint style="info" %}
Jika efek blur tidak berfungsi, periksa apakah blur diaktifkan di System Settings Workspace Behavior Desktop Effects. Beberapa efek mungkin dinonaktifkan secara default untuk menghemat sumber daya.
{% endhint %}

#### 9.2.5 Kinerja Lambat

Kinerja lambat adalah keluhan umum, terutama pada perangkat keras yang lebih lama.

**Diagnosis**

{% stepper %}
{% step %}
### Periksa penggunaan CPU dan RAM

Gunakan `htop` atau `top`.
{% endstep %}

{% step %}
### Periksa penggunaan GPU

Gunakan `nvidia-smi` untuk NVIDIA atau `radeontop` untuk AMD.
{% endstep %}

{% step %}
### Periksa suhu

Gunakan `sensors`.
{% endstep %}

{% step %}
### Periksa proses yang memakan sumber daya
{% endstep %}
{% endstepper %}

```bash
# Monitor proses
htop

# Monitor GPU
nvidia-smi -l 2
radeontop

# Monitor suhu
sensors

# Periksa proses yang memakan CPU
ps aux --sort=-%cpu | head -10

# Periksa proses yang memakan RAM
ps aux --sort=-%mem | head -10

# Periksa penggunaan disk
iostat -x 1
```

**Solusi**

1. Aktifkan Mode Sumber Daya Rendah: Di System Settings Workspace Behavior General Behavior, aktifkan Low Resource Mode.
2. Nonaktifkan efek berat: Blur, cube, dan animasi kompleks memakan banyak sumber daya.
3. Gunakan tema ringan: Beberapa tema lebih berat dari yang lain.
4. Kurangi jumlah widget: Widget yang berjalan terus-menerus dapat memakan sumber daya.
5. Perbarui sistem: Pembaruan sering membawa peningkatan kinerja.
6. Periksa suhu: Overheating dapat menyebabkan throttling.

| Masalah Kinerja | Kemungkinan Penyebab dan Solusi                                    |
| --------------- | ------------------------------------------------------------------ |
| CPU tinggi      | Widget pemantauan, efek kompositing, proses zombie                 |
| RAM tinggi      | Kebocoran memori, terlalu banyak aplikasi, cache tidak dibersihkan |
| GPU tinggi      | Efek kompositing, game, rendering                                  |
| Disk lambat     | Swap, disk penuh, SMART error                                      |
| Suhu tinggi     | Debu pada kipas, thermal paste kering, TDP terlalu tinggi          |

### 9.3 Masalah Login

Masalah login adalah salah satu masalah paling frustasi karena menghalangi akses ke sistem. Bagian ini membahas berbagai masalah login dan solusinya.

#### 9.3.1 Login Berhasil tetapi Desktop Tidak Muncul

Ini adalah masalah yang cukup umum di mana pengguna dapat login, tetapi desktop KDE Plasma tidak muncul.

**Diagnosis**

{% stepper %}
{% step %}
### Beralih ke TTY lain
{% endstep %}

{% step %}
### Login sebagai pengguna Anda
{% endstep %}

{% step %}
### Periksa log Plasma dan KWin
{% endstep %}

{% step %}
### Periksa apakah ada proses yang crash
{% endstep %}
{% endstepper %}

```bash
# Beralih ke TTY
Ctrl + Alt + F3

# Periksa log Plasma
journalctl --user -b | tail -50

# Periksa log session
journalctl --user -u plasma-plasmashell.service -b

# Periksa status session
systemctl --user status plasma-plasmashell.service

# Coba jalankan Plasma secara manual
dbus-run-session startplasma-wayland
```

**Solusi**

1. Reset konfigurasi Plasma: Hapus `~/.config/plasma*`.
2. Reset cache: Hapus `~/.cache/*`.
3. Periksa izin: Pastikan direktori home Anda memiliki izin yang benar.
4. Uji dengan pengguna baru: Jika berhasil, konfigurasi pengguna lama rusak.
5. Periksa driver GPU: Pastikan driver GPU berfungsi.

```bash
# Backup konfigurasi lama
mkdir ~/plasma-backup
cp -r ~/.config/plasma* ~/plasma-backup/
cp -r ~/.config/kdeglobals ~/plasma-backup/

# Hapus cache
rm -rf ~/.cache/*

# Hapus konfigurasi Plasma
rm -rf ~/.config/plasma*

# Restart display manager
sudo systemctl restart sddm # atau plasmalogin

# Login kembali
```

{% hint style="warning" %}
Menghapus `~/.config/plasma*` akan menghapus semua konfigurasi Plasma Anda, termasuk tata letak panel, widget, dan pengaturan. Ini adalah solusi terakhir setelah metode lain gagal.
{% endhint %}

#### 9.3.2 Login Gagal dengan Pesan Error

Kadang-kadang login gagal dengan pesan error seperti “Authentication failure” atau “Session failed”.

**Diagnosis**

```bash
# Periksa log SDDM
journalctl -u sddm.service -b

# Atau untuk Plasma Login Manager
journalctl -u plasmalogin.service -b

# Periksa log PAM
journalctl -t pam_unix -b

# Periksa izin home
ls -la ~

# Periksa apakah akun terkunci
sudo passwd -S $USER
```

**Solusi**

1. Reset password: Gunakan `passwd` dari TTY untuk reset password.
2. Perbaiki izin home: Pastikan `~` dimiliki oleh pengguna, bukan root.
3. Periksa PAM: Pastikan konfigurasi PAM benar.
4. Periksa sistem file: Pastikan partisi home tidak penuh.

```bash
# Periksa izin home
ls -la /home/

# Perbaiki izin jika perlu
sudo chown -R $USER:$USER /home/$USER
sudo chmod 755 /home/$USER

# Reset password jika perlu
sudo passwd $USER

# Periksa disk space
df -h /home
```

#### 9.3.3 Autologin Tidak Berfungsi

Autologin adalah fitur yang memungkinkan login otomatis tanpa memasukkan password. Jika tidak berfungsi, ada beberapa kemungkinan penyebab.

```ini
# Edit /etc/sddm.conf atau /etc/sddm.conf.d/autologin.conf

[Autologin]
User=namapengguna
Session=plasma
Relogin=true

# Atau untuk Plasma Login Manager
# Edit /etc/plasmalogin.conf
```

{% hint style="info" %}
Beberapa distribusi memerlukan konfigurasi tambahan untuk autologin, seperti mengaktifkan layanan tertentu atau menonaktifkan kunci layar. Konsultasikan dokumentasi distribusi Anda.
{% endhint %}

### 9.4 Masalah Multi-Layar

Konfigurasi multi-layar adalah salah satu area yang paling sering menimbulkan masalah, terutama dengan monitor yang berbeda resolusi atau refresh rate.

#### 9.4.1 Monitor Tidak Terdeteksi

Jika monitor eksternal tidak terdeteksi, ada beberapa langkah diagnosis yang dapat dilakukan.

**Diagnosis**

```bash
# Lihat output display yang terdeteksi
kscreen-doctor -o

# Periksa apakah monitor terdeteksi oleh kernel
xrandr # Untuk X11
wlr-randr # Untuk Wayland (jika tersedia)

# Periksa koneksi fisik
ls /sys/class/drm/

# Lihat log KWin
journalctl --user -u plasma-kwin_wayland.service -b | grep -i "output\|monitor\|display"

# Lihat log kernel
dmesg | grep -i "drm\|hdmi\|displayport"
```

**Solusi**

1. Periksa koneksi fisik: Pastikan kabel terhubung dengan baik.
2. Coba port lain: Coba hubungkan ke port HDMI, DisplayPort, atau VGA yang berbeda.
3. Coba kabel lain: Kabel yang rusak dapat menyebabkan monitor tidak terdeteksi.
4. Perbarui driver: Driver GPU yang lama mungkin tidak mendukung monitor baru.
5. Uji di OS lain: Jika monitor berfungsi di OS lain, masalahnya terkait software.

#### 9.4.2 Resolusi atau Refresh Rate Salah

Setelah monitor terdeteksi, resolusi atau refresh rate mungkin tidak sesuai harapan.

```bash
# Lihat mode yang tersedia
kscreen-doctor -o

# Atur resolusi dan refresh rate untuk output tertentu
kscreen-doctor output.HDMI-1.mode.1920x1080@60

# Atur scaling
kscreen-doctor output.HDMI-1.scale.1.5

# Atur posisi
kscreen-doctor output.HDMI-1.position.0,0

# Menggunakan GUI
systemsettings5 kcm_kscreen # Plasma 5
systemsettings6 kcm_kscreen # Plasma 6
```

#### 9.4.3 Monitor Muncul di Posisi yang Salah

Jika monitor muncul di posisi yang salah di System Settings, Anda dapat mengaturnya dengan drag-and-drop.

{% stepper %}
{% step %}
### Buka System Settings Display and Monitor
{% endstep %}

{% step %}
### Seret monitor ke posisi yang benar relatif terhadap monitor lain
{% endstep %}

{% step %}
### Klik Apply
{% endstep %}
{% endstepper %}

#### 9.4.4 Panel Muncul di Monitor yang Salah

Jika panel muncul di monitor yang salah, Anda dapat memindahkannya:

{% stepper %}
{% step %}
### Klik kanan panel, pilih Edit Panel
{% endstep %}

{% step %}
### Seret panel ke monitor yang diinginkan
{% endstep %}

{% step %}
### Klik More Options untuk mengatur visibilitas per monitor
{% endstep %}

{% step %}
### Klik Exit Edit Mode
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Untuk menyimpan konfigurasi multi-layar yang berbeda, gunakan fitur KScreen di Plasma. Ini memungkinkan Anda menyimpan dan memuat profil untuk berbagai setup, misalnya kantor vs. rumah.
{% endhint %}

#### 9.4.5 HiDPI dan Fractional Scaling

Dengan monitor 4K atau resolusi tinggi, Anda mungkin perlu menerapkan scaling agar font dan jendela tidak terlalu kecil.

```bash
# Lihat konfigurasi scaling saat ini
kscreen-doctor -o

# Atur scaling untuk output tertentu
kscreen-doctor output.eDP-1.scale.1.5

# Scaling per monitor (Plasma 6.7+)
# Di System Settings -> Display and Monitor -> Scale Display
```

{% hint style="info" %}
Fractional scaling (misalnya, 1.25x, 1.5x) bekerja paling baik di Wayland. Di X11, scaling integer biasanya hanya dalam kelipatan (1x, 2x), kecuali menggunakan trik seperti mengubah DPI font.
{% endhint %}

### 9.5 Masalah NVIDIA

Pengguna kartu grafis NVIDIA sering menghadapi masalah unik, terutama dengan Wayland. Bagian ini membahas masalah-masalah tersebut dan solusinya.

#### 9.5.1 Driver NVIDIA Proprietary vs. Nouveau

NVIDIA menyediakan dua jenis driver:

| Aspek           | Proprietary         | Nouveau  |
| --------------- | ------------------- | -------- |
| Performa        | Terbaik             | Sedang   |
| Dukungan CUDA   | Ya                  | Tidak    |
| Wayland Support | Baik (495+)         | Baik     |
| KMS             | Ya (dengan modeset) | Ya       |
| Suspend/Resume  | Baik                | Terbatas |

#### 9.5.2 Masalah Wayland pada NVIDIA

Pengguna NVIDIA mungkin mengalami masalah dengan Wayland, terutama pada versi driver lama.

**Solusi**

1. Perbarui driver: Gunakan driver NVIDIA versi 495 atau lebih baru.
2. Aktifkan DRM KMS: Tambahkan `nvidia-drm.modeset=1` ke parameter kernel.
3. Nonaktifkan suspend yang bermasalah: Beberapa versi driver memiliki masalah suspend dengan Wayland.
4. Gunakan X11: Jika Wayland tidak berfungsi dengan baik, beralih ke X11 di layar login.

```bash
# Edit /etc/default/grub
sudo nano /etc/default/grub

# Tambahkan nvidia-drm.modeset=1 ke GRUB_CMDLINE_LINUX_DEFAULT
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"

# Update grub
sudo update-grub # Ubuntu/Debian
sudo grub-mkconfig -o /boot/grub/grub.cfg # Arch

# Reboot
sudo reboot
```

{% hint style="warning" %}
Mengubah parameter kernel dapat menyebabkan sistem tidak dapat boot jika salah. Pastikan Anda memiliki cara untuk mengakses GRUB dan mengedit parameter jika terjadi kesalahan. Selalu backup konfigurasi GRUB Anda terlebih dahulu.
{% endhint %}

#### 9.5.3 Screen Tearing

Screen tearing adalah masalah di mana gambar terlihat “robek” karena sinkronisasi yang buruk antara GPU dan monitor.

**Solusi**

1. Aktifkan VSync: Di System Settings Display and Monitor Compositor, aktifkan VSync.
2. Gunakan Triple Buffering: Aktifkan di pengaturan compositor.
3. Atur ForceFullCompositionPipeline: Untuk NVIDIA, aktifkan opsi ini di pengaturan driver.

```bash
# Gunakan nvidia-settings untuk mengatur ForceFullCompositionPipeline
nvidia-settings --assign CurrentMetaMode="DP-0: 1920x1080_144 +0+0 {ForceFullCompositionPipeline=On}"

# Atau buat file /etc/X11/xorg.conf.d/20-nvidia.conf
# dan tambahkan opsi ForceFullCompositionPipeline
```

#### 9.5.4 Multi-Monitor dengan NVIDIA

Multi-monitor dengan NVIDIA di Wayland masih memiliki beberapa keterbatasan.

```bash
# Lihat output yang terdeteksi
nvidia-settings -q dpys -t

# Atur konfigurasi multi-monitor
nvidia-settings --assign CurrentMetaMode="DP-0: 1920x1080_144 +0+0, HDMI-0: 1920x1080_60 +1920+0"

# Simpan konfigurasi
nvidia-settings --save-config-only
```

{% hint style="info" %}
Beberapa fitur NVIDIA, seperti G-Sync dan Mosaic, mungkin tidak berfungsi penuh di Wayland. Jika Anda memerlukan fitur-fitur ini, sesi X11 mungkin lebih sesuai.
{% endhint %}

### 9.6 HiDPI Scaling

Layar beresolusi tinggi (HiDPI) menawarkan tampilan yang lebih tajam, tetapi memerlukan konfigurasi scaling yang tepat.

#### 9.6.1 Konsep Dasar Scaling

Scaling di KDE Plasma dapat dilakukan dengan beberapa cara:

| Jenis               | Deskripsi                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------- |
| Integer Scaling     | Skala 1x, 2x, 3x. Paling sederhana dan paling kompatibel.                                 |
| Fractional Scaling  | Skala 1.25x, 1.5x, 1.75x. Lebih fleksibel, tetapi memerlukan Wayland untuk hasil terbaik. |
| Font Scaling        | Mengubah ukuran font secara terpisah dari elemen UI lainnya.                              |
| Application Scaling | Scaling per aplikasi.                                                                     |

#### 9.6.2 Mengatur Scaling di Wayland

Wayland mendukung fractional scaling dengan lebih baik daripada X11.

{% stepper %}
{% step %}
### Buka System Settings Display and Monitor Display Configuration
{% endstep %}

{% step %}
### Pilih monitor yang ingin diatur
{% endstep %}

{% step %}
### Atur Scale ke nilai yang diinginkan

Misalnya, `1.5`.
{% endstep %}

{% step %}
### Klik Apply
{% endstep %}

{% step %}
### Logout dan login kembali untuk menerapkan perubahan
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Fractional scaling di Wayland bekerja dengan merender pada resolusi tinggi dan kemudian downscaling. Ini menghasilkan tampilan yang lebih tajam dibanding integer scaling, tetapi memerlukan lebih banyak sumber daya GPU.
{% endhint %}

#### 9.6.3 Mengatur Scaling di X11

Di X11, scaling biasanya hanya bekerja dalam kelipatan integer. Namun, ada beberapa trik untuk mencapai scaling yang lebih halus.

```bash
# Atur DPI font
xrdb -merge <<< "Xft.dpi: 144"

# Atur scaling X11
xrandr --output HDMI-1 --scale 1.5x1.5

# Atur scaling untuk aplikasi GTK
gsettings set org.gnome.desktop.interface text-scaling-factor 1.5

# Atur scaling untuk aplikasi Qt
export QT_SCALE_FACTOR=1.5
export QT_AUTO_SCREEN_SCALE_FACTOR=1
```

#### 9.6.4 Masalah Scaling Umum

| Masalah                          | Solusi                                                   |
| -------------------------------- | -------------------------------------------------------- |
| Font terlalu kecil               | Atur font scaling di System Settings → Fonts             |
| Aplikasi tidak mengikuti scaling | Atur variabel lingkungan per aplikasi                    |
| Ikon blur                        | Gunakan ikon SVG atau tema ikon HiDPI                    |
| Kursor terlalu kecil             | Ubah ukuran kursor di System Settings → Cursors          |
| Aplikasi X11 blur                | Gunakan aplikasi Wayland native atau atur scaling khusus |

{% hint style="info" %}
Untuk aplikasi X11 yang tidak mengikuti scaling dengan baik, coba atur variabel lingkungan `QT_SCALE_FACTOR` atau `GDK_SCALE` sebelum menjalankan aplikasi. Ini dapat membantu aplikasi menyesuaikan ukuran UI mereka.
{% endhint %}

### 9.7 Studi Kasus: Diagnosis Crash Plasma

Untuk mengilustrasikan metodologi pemecahan masalah, mari kita telusuri studi kasus nyata: Plasma crash setelah pembaruan.

#### 9.7.1 Skenario

Seorang pengguna melaporkan bahwa setelah pembaruan ke Plasma 6.7, Plasma Shell crash berulang kali. Desktop muncul selama beberapa detik, kemudian hilang, dan pengguna kembali ke layar login.

#### 9.7.2 Langkah 1: Reproduksi Masalah

Pengguna dapat mereproduksi masalah dengan login kembali. Setiap kali login, Plasma crash dalam 5–10 detik.

#### 9.7.3 Langkah 2: Kumpulkan Informasi

```bash
# Beralih ke TTY
Ctrl + Alt + F3

# Login

# Periksa crash terbaru
coredumpctl list

# Lihat detail crash
coredumpctl info plasmashell

# Periksa log Plasma
journalctl --user -u plasma-plasmashell.service -b

# Periksa versi Plasma
plasmashell --version
plasmashell --version # Plasma 6.7.0

# Periksa versi Qt
qmake6 --version

# Periksa versi KDE Frameworks
kf6-config --version
```

#### 9.7.4 Langkah 3: Analisis Log

Dari log, pengguna menemukan pesan error berikut:

```
plasmashell[1234]: kf.plasma.quick: Applet "com.example.mywidget" crashed
plasmashell[1234]: kf.plasma.quick: Attempting to recover applet
plasmashell[1234]: qml: TypeError: Cannot read property 'foo' of undefined
plasmashell[1234]: kf.plasma.quick: Applet "com.example.mywidget" crashed again
plasmashell[1234]: kf.plasma.quick: Giving up on applet
plasmashell[1234]: Segmentation fault
```

#### 9.7.5 Langkah 4: Isolasi Masalah

Dari log, jelas bahwa widget kustom `com.example.mywidget` menyebabkan crash. Widget ini adalah widget pihak ketiga yang belum diperbarui untuk Plasma 6.7.

#### 9.7.6 Langkah 5: Solusi

```bash
# Hapus widget yang bermasalah
kpackagetool6 --type Plasma/Applet --remove com.example.mywidget

# Restart Plasma
kquitapp6 plasmashell && kstart plasmashell

# Atau, reset konfigurasi widget
mv ~/.config/plasma-org.kde.plasma.desktop-appletsrc ~/plasma-appletsrc.backup
kquitapp6 plasmashell && kstart plasmashell
```

#### 9.7.7 Langkah 6: Verifikasi

Setelah menghapus widget yang bermasalah, Plasma Shell berjalan stabil. Pengguna kemudian melaporkan bug ke pengembang widget melalui pelacak bug mereka.

#### 9.7.8 Pelajaran

1. Widget pihak ketiga adalah sumber crash yang umum: Widget yang belum diperbarui untuk versi Plasma baru dapat menyebabkan masalah.
2. Log adalah kunci diagnosis: Pesan error di log menunjukkan dengan tepat apa yang menyebabkan crash.
3. Isolasi masalah adalah penting: Dengan mengidentifikasi widget yang bermasalah, pengguna dapat menyelesaikan masalah dengan cepat.
4. Laporkan bug: Setelah masalah teratasi, laporkan ke pengembang widget sehingga mereka dapat memperbaikinya.

{% hint style="info" %}
Selalu gunakan widget dari KDE Store yang aktif dipelihara. Periksa tanggal pembaruan terakhir dan ulasan pengguna sebelum menginstal widget pihak ketiga.
{% endhint %}

#### 9.7.9 Studi Kasus 2: Plasma Tidak Muncul Setelah Pembaruan

**Skenario**

Seorang pengguna memperbarui sistem, dan setelah reboot, login berhasil tetapi desktop KDE Plasma tidak muncul. Hanya layar hitam dengan kursor.

**Diagnosis**

```bash
# Beralih ke TTY
Ctrl + Alt + F3

# Login

# Periksa apakah plasmashell berjalan
ps aux | grep plasmashell

# Periksa log
journalctl --user -b | tail -50

# Coba jalankan Plasma secara manual
dbus-run-session startplasma-wayland 2>&1 | tee ~/plasma-manual.log

# Periksa error di log manual
cat ~/plasma-manual.log
```

**Solusi**

Dari log, pengguna menemukan bahwa plasmashell tidak dapat memuat plugin QML karena konflik versi. Solusinya adalah menghapus cache QML dan restart:

```bash
# Hapus cache QML
rm -rf ~/.cache/qmlcache/
rm -rf ~/.cache/plasmashell/

# Restart Plasma
kquitapp6 plasmashell && kstart plasmashell

# Jika masih bermasalah, reset konfigurasi Plasma
mv ~/.config/plasma* ~/plasma-backup/
kquitapp6 plasmashell && kstart plasmashell
```

### 9.8 Sumber Daya Pemecahan Masalah

Ketika Anda tidak dapat menyelesaikan masalah sendiri, ada banyak sumber daya yang dapat membantu.

#### 9.8.1 Dokumentasi Resmi

* `community.kde.org/Troubleshooting` — Wiki pemecahan masalah resmi KDE.
* `userbase.kde.org` — Wiki komunitas dengan panduan dan solusi.
* `docs.kde.org` — Dokumentasi resmi untuk semua aplikasi KDE.

#### 9.8.2 Forum dan Komunitas

* KDE Discuss: [https://discuss.kde.org/](https://discuss.kde.org/) — Forum diskusi resmi.
* Reddit r/kde — Subreddit untuk pengguna KDE.
* Matrix: `#plasma:kde.org` — Obrolan langsung.
* IRC `#kde` di Libera Chat.

#### 9.8.3 Pelacak Bug

* Bugs KDE: [https://bugs.kde.org/](https://bugs.kde.org/) — Pelacak bug resmi.
* Launchpad — Untuk bug di Ubuntu dan turunannya.
* Fedora Bugzilla — Untuk bug di Fedora.
* Arch Bug Tracker — Untuk bug di Arch Linux.

#### 9.8.4 Melaporkan Bug yang Baik

{% stepper %}
{% step %}
### Periksa apakah bug sudah dilaporkan

Cari di pelacak bug sebelum melaporkan.
{% endstep %}

{% step %}
### Gunakan judul yang deskriptif

Jelaskan masalah dengan singkat.
{% endstep %}

{% step %}
### Sertakan informasi sistem

Versi Plasma, Qt, KDE Frameworks, distribusi, dan driver GPU.
{% endstep %}

{% step %}
### Jelaskan langkah reproduksi

Bagaimana cara mereproduksi masalah?
{% endstep %}

{% step %}
### Sertakan log

Log yang relevan sangat membantu.
{% endstep %}

{% step %}
### Jelaskan perilaku yang diharapkan vs. aktual
{% endstep %}

{% step %}
### Sertakan screenshot atau video jika perlu
{% endstep %}

{% step %}
### Bersikap sopan dan sabar

Pengembang adalah sukarelawan.
{% endstep %}
{% endstepper %}

```bash
# Versi Plasma
plasmashell --version
kwin_wayland --version

# Versi Qt
qmake6 --version

# Versi KDE Frameworks
kf6-config --version

# Informasi sistem
uname -a
cat /etc/os-release

# Informasi GPU
lspci | grep -i vga
glxinfo | grep "OpenGL version"

# Log yang relevan
journalctl --user -b > ~/plasma-log.txt
coredumpctl info > ~/crash-info.txt

# Ringkas semua informasi
echo "=== System Info ===" > ~/bug-report.txt
cat /etc/os-release >> ~/bug-report.txt
plasmashell --version >> ~/bug-report.txt
qmake6 --version >> ~/bug-report.txt
kf6-config --version >> ~/bug-report.txt
uname -a >> ~/bug-report.txt
```

{% hint style="info" %}
Gunakan KDE Bug Report Tool, jika tersedia, untuk mengumpulkan informasi sistem secara otomatis. Alat ini dapat diakses melalui System Settings About System Report Bug.
{% endhint %}

#### 9.8.5 Alat Bantu Pemecahan Masalah

| Alat             | Kegunaan                             |
| ---------------- | ------------------------------------ |
| `kdebugsettings` | Mengaktifkan logging debug untuk KDE |
| `qdbus`          | Berinteraksi dengan layanan D-Bus    |
| `journalctl`     | Membaca log systemd                  |
| `dmesg`          | Membaca log kernel                   |
| `coredumpctl`    | Melihat dan menganalisis core dump   |
| `strace`         | Melacak system call                  |
| `ltrace`         | Melacak library call                 |
| `valgrind`       | Menganalisis memori                  |
| `gdb`            | Debugger                             |

#### 9.8.6 Mengaktifkan Logging Debug

Untuk masalah yang sulit, Anda mungkin perlu mengaktifkan logging debug:

```bash
# Aktifkan logging debug untuk Plasma
kdebugsettings

# Atau melalui command line
kwriteconfig6 --file kdebugrc --group plasma --key debug true

# Aktifkan logging untuk KWin
qdbus org.kde.KWin /KWin org.kde.KWin.setDebugLogging true

# Restart Plasma
kquitapp6 plasmashell && kstart plasmashell

# Lihat log
journalctl --user -f | grep -i "plasma\|kwin"
```

{% hint style="warning" %}
Logging debug menghasilkan log yang sangat besar dan dapat memperlambat sistem. Aktifkan hanya saat mendiagnosis masalah, dan nonaktifkan setelah selesai.
{% endhint %}

### 9.9 Ringkasan Bab

Bab ini telah membahas pemecahan masalah KDE Plasma secara menyeluruh:

* Metodologi pemecahan masalah: Pendekatan sistematis meliputi reproduksi masalah, isolasi, pengumpulan informasi, perubahan satu variabel, dan dokumentasi.
* Masalah umum: Aplikasi crash, layar hitam, widget tidak muncul, efek tidak berfungsi, dan kinerja lambat.
* Masalah login: Login berhasil tetapi desktop tidak muncul, login gagal, autologin tidak berfungsi.
* Masalah multi-layar: Monitor tidak terdeteksi, resolusi salah, posisi salah, panel di monitor yang salah.
* Masalah NVIDIA: Driver proprietary vs Nouveau, masalah Wayland, screen tearing, multi-monitor.
* HiDPI scaling: Konsep scaling, mengatur scaling di Wayland dan X11, masalah umum.
* Studi kasus: Diagnosis crash Plasma dan Plasma tidak muncul setelah pembaruan.
* Sumber daya: Dokumentasi resmi, forum, pelacak bug, dan tips melaporkan bug yang baik.
* Alat bantu: `journalctl`, `dmesg`, `coredumpctl`, `kdebugsettings`, `qdbus`, dan lainnya.

Bab selanjutnya akan membahas sumber daya dan komunitas KDE, termasuk dokumentasi resmi, komunitas, KDE Store, distribusi, dan buku.

## 10 Sumber Daya dan Komunitas

> “Tidak ada yang lebih kuat daripada komunitas yang bersatu dengan tujuan bersama.”
>
> — Anonim, semangat komunitas KDE

Sepanjang buku ini, kita telah menjelajahi KDE Plasma dari berbagai sudut: sejarah, arsitektur, instalasi, penggunaan, kustomisasi, pengembangan, fitur terbaru, dan pemecahan masalah. Namun, ada satu aspek yang menyatukan semuanya: komunitas. KDE Plasma bukan sekadar kode; ia adalah hasil kerja kolektif dari ribuan kontributor dari seluruh dunia yang berkolaborasi selama lebih dari dua dekade. Bab ini menyediakan peta lengkap sumber daya yang tersedia bagi pengguna dan pengembang KDE Plasma: dari dokumentasi resmi hingga forum komunitas, dari KDE Store hingga konferensi tahunan. Bab ini bukan hanya daftar tautan, tetapi panduan tentang bagaimana memanfaatkan sumber daya ini secara efektif dan bagaimana berkontribusi kembali kepada komunitas yang telah membuat KDE Plasma menjadi apa yang ada saat ini.

### 10.1 Pendahuluan: Mengapa Komunitas Penting

Sebelum menyelami detail sumber daya yang tersedia, penting untuk memahami mengapa komunitas memainkan peran begitu sentral dalam proyek KDE Plasma.

#### 10.1.1 Komunitas sebagai Fondasi

KDE adalah komunitas internasional yang terdiri dari programmer, penerjemah, kontributor, seniman, penulis, distributor, dan pengguna dari seluruh dunia. Komunitas ini bukan sekadar pengguna pasif; mereka adalah co-creator dari perangkat lunak yang mereka gunakan.

{% hint style="info" %}
**Komunitas KDE** adalah jaringan global yang terdiri dari lebih dari 1.800 kontributor aktif, dengan sekitar 20 pengembang baru bergabung setiap bulan. Mereka bekerja sama untuk mengembangkan, mendokumentasikan, menerjemahkan, dan mempromosikan perangkat lunak KDE.
{% endhint %}

#### 10.1.2 Mengapa Berkontribusi?

Ada banyak alasan mengapa orang berkontribusi pada KDE:

1. Membantu orang lain: Perangkat lunak yang Anda kembangkan digunakan oleh jutaan orang di seluruh dunia.
2. Belajar keterampilan baru: Berkontribusi pada proyek open source adalah cara yang bagus untuk belajar pemrograman, desain, atau keterampilan lainnya.
3. Membangun portofolio: Kontribusi open source adalah bukti nyata keterampilan Anda.
4. Bertemu orang baru: Komunitas KDE adalah jaringan global yang ramah dan beragam.
5. Membentuk masa depan: Anda memiliki suara dalam arah pengembangan KDE Plasma.
6. Membayar kembali: Jika Anda telah menggunakan KDE Plasma selama bertahun-tahun, berkontribusi adalah cara untuk memberikan kembali.

{% hint style="info" %}
Tidak ada kontribusi yang terlalu kecil. Baik Anda melaporkan bug, menerjemahkan satu string, atau menulis dokumentasi, setiap kontribusi membuat perbedaan. Mulailah dari yang kecil dan tumbuh dari sana.
{% endhint %}

### 10.2 Dokumentasi Resmi

Dokumentasi adalah fondasi dari setiap proyek open source yang sukses. KDE menyediakan berbagai sumber dokumentasi untuk berbagai audiens.

#### 10.2.1 Docs.KDE.Org

`docs.kde.org` adalah portal dokumentasi resmi KDE. Ia menyediakan dokumentasi pengguna untuk KDE Frameworks, KDE Plasma Workspaces, dan Applications dalam lebih dari 25 bahasa. Dokumentasi ini tersedia untuk versi yang telah dirilis maupun yang sedang dikembangkan.

* Dokumentasi untuk versi stabil dan pengembangan.
* Tersedia dalam lebih dari 25 bahasa.
* Mencakup KDE Frameworks, Plasma Workspaces, dan Applications.
* Format yang konsisten dan mudah dinavigasi.

#### 10.2.2 UserBase.KDE.Org

`userbase.kde.org` adalah wiki komunitas untuk pengguna KDE. Ia menyediakan:

* Tutorial dan panduan untuk pengguna akhir.
* Tips dan trik untuk menggunakan aplikasi KDE.
* Informasi tentang aplikasi KDE dan fitur-fiturnya.
* Dokumentasi yang ditulis oleh komunitas, untuk komunitas.

{% hint style="info" %}
UserBase adalah tempat yang tepat untuk mencari bantuan tentang cara menggunakan aplikasi KDE. Jika Anda baru mengenal KDE Plasma, mulai dari halaman Welcome to KDE UserBase untuk mendapatkan gambaran umum.
{% endhint %}

#### 10.2.3 Community.KDE.Org

`community.kde.org` adalah wiki komunitas yang menyediakan:

* Panduan untuk terlibat dalam komunitas KDE.
* Informasi tentang tim dan proyek KDE.
* Koordinasi acara dan pertemuan komunitas.
* Sumber daya untuk kontributor baru.

#### 10.2.4 TechBase.KDE.Org

`techbase.kde.org` adalah wiki teknis untuk pengembang KDE. Ia menyediakan:

* Dokumentasi pengembangan yang mendalam.
* Tutorial untuk pemula hingga lanjutan.
* Referensi API dan panduan gaya.
* Jadwal rilis dan rencana fitur.

{% hint style="info" %}
Jika Anda seorang pengembang yang ingin berkontribusi pada KDE Plasma, TechBase adalah tempat pertama yang harus Anda kunjungi. Di sana Anda akan menemukan tutorial tentang cara menyiapkan lingkungan pengembangan, membangun KDE, dan mengirim patch.
{% endhint %}

#### 10.2.5 Develop.KDE.Org

`develop.kde.org` adalah portal pengembangan modern KDE. Ia menyediakan:

* Dokumentasi untuk pengembangan dengan QML, Kirigami, dan KDE Frameworks.
* Tutorial langkah demi langkah.
* Panduan gaya dan konvensi.
* Referensi API untuk pengembangan Plasma.

### 10.3 Komunitas

Komunitas KDE adalah salah satu yang paling aktif dan ramah di dunia open source. Bagian ini menjelaskan berbagai saluran komunikasi dan cara berpartisipasi.

| Sumber Daya     | URL               | Audiens        |
| --------------- | ----------------- | -------------- |
| Docs.KDE.Org    | docs.kde.org      | Pengguna       |
| UserBase        | userbase.kde.org  | Pengguna akhir |
| Community Wiki  | community.kde.org | Komunitas      |
| TechBase        | techbase.kde.org  | Pengembang     |
| Develop.KDE.Org | develop.kde.org   | Pengembang     |
| Invent.KDE.Org  | invent.kde.org    | Pengembang     |

#### 10.3.1 KDE Discuss

KDE Discuss (`discuss.kde.org`) adalah forum diskusi resmi KDE. Ia menyediakan ruang untuk:

* Mendapatkan bantuan dengan masalah KDE Plasma.
* Berbagi tips dan trik.
* Berdiskusi tentang pengembangan dan fitur baru.
* Berinteraksi dengan pengembang dan pengguna lain.

{% hint style="info" %}
KDE Discuss adalah tempat yang tepat untuk memulai jika Anda memiliki pertanyaan atau masalah. Komunitas sangat ramah dan responsif, dan Anda biasanya akan mendapatkan jawaban dalam beberapa jam.
{% endhint %}

#### 10.3.2 Matrix

Matrix adalah platform obrolan utama yang digunakan oleh komunitas KDE. KDE memiliki homeserver `kde.org` sendiri dan menyediakan berbagai ruang untuk diskusi.

| Ruang                    | Kegunaan                                       |
| ------------------------ | ---------------------------------------------- |
| `#kde:kde.org`           | Ruang umum untuk diskusi tentang KDE.          |
| `#kde-devel:kde.org`     | Ruang untuk pengembangan KDE.                  |
| `#plasma:kde.org`        | Ruang khusus untuk diskusi tentang KDE Plasma. |
| `#kde-workspace:kde.org` | Ruang untuk diskusi tentang workspace KDE.     |
| `#kwin:kde.org`          | Ruang untuk diskusi tentang KWin.              |

```
# Untuk bergabung dengan Matrix KDE:
# 1. Buat akun di matrix.org atau server Matrix lainnya
# 2. Unduh klien Matrix seperti Element
# 3. Cari "kde.org" di direktori room
# 4. Bergabung dengan room yang diinginkan

# Atau gunakan tautan langsung:
https://go.kde.org/matrix/#/#kde:kde.org
https://go.kde.org/matrix/#/#plasma:kde.org
```

#### 10.3.3 Mailing List

KDE masih menggunakan mailing list untuk diskusi tertentu, terutama untuk pengembangan.

* `kde-devel@kde.org`: Diskusi umum pengembangan KDE.
* `plasma-devel@kde.org`: Diskusi tentang pengembangan KDE Plasma.
* `kde-core-devel@kde.org`: Diskusi tentang pengembangan inti KDE.
* `kde-announce@kde.org`: Pengumuman resmi KDE.

#### 10.3.4 Komunitas Lokal

KDE memiliki komunitas lokal di berbagai negara dan wilayah. Halaman Global Communities di wiki KDE menyediakan daftar komunitas lokal.

* Jerman: KDE auf Deutsch, forum dan Matrix.
* Prancis: Komunitas KDE Prancis.
* Spanyol: Komunitas KDE Spanyol.
* Brasil: Komunitas KDE Brasil.
* India: Komunitas KDE India.

#### 10.3.5 Akademy

Akademy adalah konferensi tahunan KDE. Ini adalah acara di mana pengembang, kontributor, dan pengguna berkumpul untuk berbagi ide, belajar, dan berkolaborasi.

Akademy 2026 berlangsung di Graz, Austria, pada 19–24 September 2026. Acara ini mencakup keynote, talks, BOF, workshop, hackathon, networking, dan social event. Acara hybrid ini dapat dihadiri langsung atau online.

{% hint style="info" %}
Akademy adalah kesempatan yang sangat baik untuk bertemu pengembang KDE Plasma secara langsung, belajar tentang fitur-fitur baru, dan berkontribusi pada proyek. Jika Anda tidak dapat hadir secara langsung, banyak sesi yang disiarkan secara online.
{% endhint %}

### 10.4 KDE Store

KDE Store (`store.kde.org`) adalah pusat distribusi untuk tema, widget, dan add-on pihak ketiga untuk KDE Plasma dan aplikasi KDE.

#### 10.4.1 Apa Itu KDE Store?

{% hint style="info" %}
**KDE Store** adalah platform online di mana pengembang dan desainer dapat membagikan kreasi mereka untuk KDE Plasma dan aplikasi KDE. Ia menyediakan akses ke ribuan tema, widget, ikon, dan add-on yang dibuat oleh komunitas.
{% endhint %}

{% hint style="info" %}
KDE Store tidak dimiliki atau dijalankan oleh KDE; ia adalah bagian dari proyek Open-Desktop. Namun, KDE menyediakan integrasi langsung dengan KDE Store melalui tombol “Get New...” di berbagai aplikasi.
{% endhint %}

#### 10.4.2 Kategori di KDE Store

| Kategori           | Deskripsi                                                  |
| ------------------ | ---------------------------------------------------------- |
| Global Themes      | Paket tema lengkap, Plasma Style, Ikon, Warna, dan lainnya |
| Plasma Style       | Gaya visual untuk panel dan widget                         |
| Color Schemes      | Skema warna untuk UI                                       |
| Icon Themes        | Kumpulan ikon untuk aplikasi dan berkas                    |
| Window Decorations | Dekorasi jendela untuk KWin                                |
| Widgets            | Widget untuk desktop dan panel                             |
| Splash Screens     | Layar splash saat login                                    |
| Wallpapers         | Gambar latar belakang                                      |

#### 10.4.3 Cara Mengakses KDE Store

Ada beberapa cara untuk mengakses KDE Store.

**Melalui System Settings**

{% stepper %}
{% step %}
### Buka System Settings Colors & Themes
{% endstep %}

{% step %}
### Pilih kategori yang diinginkan

Misalnya, Global Theme.
{% endstep %}

{% step %}
### Klik Get New... di bagian bawah
{% endstep %}

{% step %}
### Jelajahi KDE Store atau gunakan kotak pencarian
{% endstep %}

{% step %}
### Klik Install pada item yang diinginkan
{% endstep %}
{% endstepper %}

**Melalui Widget Browser**

{% stepper %}
{% step %}
### Klik kanan desktop atau panel
{% endstep %}

{% step %}
### Pilih Add Widgets
{% endstep %}

{% step %}
### Klik Get New Widgets... di bagian bawah
{% endstep %}

{% step %}
### Jelajahi atau cari widget yang diinginkan
{% endstep %}

{% step %}
### Klik Install
{% endstep %}
{% endstepper %}

**Melalui Situs Web**

Kunjungi langsung [https://store.kde.org/](https://store.kde.org/) untuk menjelajahi semua konten yang tersedia. Anda dapat mengunduh berkas secara manual dan menginstalnya melalui `kpackagetool6`.

#### 10.4.4 Widget Populer

Berikut beberapa widget populer yang tersedia di KDE Store:

* Better Inline Clock: Jam dengan tanggal dan cuaca inline.
* Modern Clock: Jam minimalis dan estetik.
* Plasma Panel Colorizer: Kustomisasi warna panel per-widget.
* Weather Widget: Prakiraan cuaca dengan ikon animasi.
* Netspeed: Pemantau kecepatan jaringan.
* Simple Menu: Peluncur aplikasi layar penuh.
* Window Title Applet: Menampilkan judul jendela di panel.

```bash
# Menginstal widget dari file lokal
kpackagetool6 --type Plasma/Applet --install /path/to/widget.tar.gz

# Menginstal dari KDE Store (memerlukan ID widget)
kpackagetool6 --type Plasma/Applet --install https://store.kde.org/p/1234567

# Melihat daftar widget yang terinstal
kpackagetool6 --type Plasma/Applet --list

# Menghapus widget
kpackagetool6 --type Plasma/Applet --remove com.example.widget
```

### 10.5 Distribusi yang Menggunakan KDE Plasma

KDE Plasma tersedia di berbagai distribusi Linux dan sistem operasi mirip Unix. Bagian ini menyediakan daftar distribusi yang menyertakan KDE Plasma sebagai pilihan default atau mudah.

#### 10.5.1 Distribusi dengan Plasma 6

Menurut wiki komunitas KDE, distribusi berikut menyertakan Plasma 6 secara default atau sebagai opsi yang didukung secara formal:

| Distribusi     | Deskripsi                                                                                 |
| -------------- | ----------------------------------------------------------------------------------------- |
| Aurora         | Pengalaman KDE Plasma yang andal dan tanpa hambatan.                                      |
| Bazzite        | Dirancang untuk gaming, dengan Steam pra-instal, dukungan HDR & VRR, dan Plasma 6.        |
| CachyOS        | Pengalaman Arch Linux yang dipoles, dengan Plasma sebagai “Flagship Desktop Environment”. |
| EndeavourOS    | Distribusi berbasis Arch Linux dengan Plasma sebagai opsi utama.                          |
| Garuda         | Distribusi Arch Linux dengan Plasma 6 yang sangat dikustomisasi.                          |
| Fedora KDE     | Varian Fedora dengan Plasma 6 sebagai antarmuka utama.                                    |
| Fedora Kinoite | Varian Fedora dengan Plasma 6 dan teknologi CoreOS.                                       |
| KaOS           | OS rolling release yang fokus pada KDE dan Qt.                                            |
| KDE Linux      | OS berbasis “immutable base” yang sedang dikembangkan oleh KDE.                           |
| Kubuntu        | Distribusi resmi Ubuntu dengan Plasma 6.                                                  |
| Manjaro KDE    | Distribusi berbasis Arch Linux dengan Plasma 6.                                           |
| MX Linux       | Distribusi berbasis Debian dengan Plasma 6.                                               |
| NixOS          | Distribusi dengan dukungan Plasma 6.                                                      |
| openSUSE       | Tumbleweed dan Leap dengan Plasma 6.                                                      |
| Arch Linux     | Plasma 6 tersedia melalui paket `plasma`.                                                 |
| Debian         | Plasma 6 tersedia di repositori utama.                                                    |
| Alpine Linux   | Plasma 6 tersedia di repositori komunitas.                                                |
| Void Linux     | Plasma 6 tersedia.                                                                        |

Daftar lengkap tersedia di `community.kde.org/Distributions`.

#### 10.5.2 Memilih Distribusi

Memilih distribusi yang tepat tergantung pada kebutuhan dan preferensi Anda:

* Untuk pengguna baru: Kubuntu, Fedora KDE, atau openSUSE Leap.
* Untuk pengguna yang ingin fitur terbaru: KDE Neon, Fedora KDE, atau openSUSE Tumbleweed.
* Untuk pengguna tingkat lanjut: Arch Linux, EndeavourOS, atau CachyOS.
* Untuk gaming: Bazzite, Garuda, atau CachyOS.
* Untuk stabilitas jangka panjang: Kubuntu LTS, Debian, atau openSUSE Leap.

#### 10.5.3 Kubuntu 26.04 LTS

Kubuntu 26.04 LTS “Resolute Raccoon” dirilis pada April 2026 dan menghadirkan Plasma 6.6 sebagai lingkungan desktop unggulan. Ia juga menyertakan Qt 6.10.2 dan sesi Wayland sebagai default.

{% hint style="info" %}
Kubuntu 26.04 LTS adalah salah satu distribusi KDE paling stabil yang tersedia saat ini. Ia menggabungkan stabilitas Ubuntu LTS dengan fitur-fitur terbaru Plasma 6.6.
{% endhint %}

### 10.6 Buku dan Literatur

Meskipun dokumentasi online sangat penting, buku dan literatur cetak juga memiliki tempat dalam pembelajaran KDE Plasma.

#### 10.6.1 Buku tentang KDE Plasma

Sayangnya, jumlah buku cetak tentang KDE Plasma masih terbatas. Namun, ada beberapa buku yang relevan:

* **KDE Plasma Desktop 5.25** oleh Jürg Rechsteiner: Panduan rinci untuk penggunaan dan konfigurasi Plasma, 147 halaman, diterbitkan 2022.
* **KUBUNTU LINUX: THE COMPLETE GUIDE TO KDE PLASMA DESKTOP** oleh Ansel Corbyn: Panduan lengkap mencakup manajemen perangkat lunak, konfigurasi sistem, kustomisasi, multimedia, dan produktivitas.

#### 10.6.2 Dokumentasi Bawaan

KDE Plasma menyertakan dokumentasi bawaan yang dapat diakses melalui:

* KHelpCenter: Aplikasi pusat bantuan untuk KDE.
* Plasma Handbook: Dokumentasi tentang Plasma Desktop.
* Dokumentasi Aplikasi: Setiap aplikasi KDE menyertakan dokumentasi bawaannya.

#### 10.6.3 Arianna: Pembaca E-Book KDE

KDE mengembangkan Arianna, pembaca e-book dan manajer perpustakaan yang mendukung berkas `.epub`. Arianna secara otomatis menemukan buku-buku Anda dan mengurutkannya berdasarkan kategori, genre, dan penulis.

* Dukungan untuk format `.epub`.
* Manajemen perpustakaan otomatis.
* Pengurutan berdasarkan kategori, genre, dan penulis.
* Tersedia untuk Plasma dan Plasma Mobile.

{% hint style="info" %}
Jika Anda ingin membaca buku tentang KDE Plasma atau topik open source lainnya, Arianna adalah pilihan yang sangat baik. Ia terintegrasi dengan baik dengan lingkungan desktop KDE.
{% endhint %}

#### 10.6.4 Sumber Belajar Online

* TechBase Tutorials: Tutorial pengembangan KDE dari pemula hingga lanjutan.
* Develop.KDE.Org: Dokumentasi pengembangan modern.
* KDE Discuss: Forum untuk bertanya dan berdiskusi.
* YouTube: Banyak video tutorial tentang KDE Plasma dari komunitas.

### 10.7 Cara Berkontribusi

Salah satu cara terbaik untuk membalas budi kepada komunitas yang telah membuat KDE Plasma menjadi apa yang ada saat ini adalah dengan berkontribusi.

#### 10.7.1 Cara-Cara Berkontribusi

| Kontribusi  | Deskripsi                                                                             |
| ----------- | ------------------------------------------------------------------------------------- |
| Kode        | Berkontribusi pada pengembangan KDE Plasma dengan menulis kode C++, QML, atau Python. |
| Terjemahan  | Menerjemahkan KDE Plasma dan aplikasi KDE ke bahasa Anda.                             |
| Dokumentasi | Menulis atau memperbarui dokumentasi.                                                 |
| Desain      | Membuat tema, ikon, atau wallpaper.                                                   |
| Pengujian   | Menguji versi beta dan melaporkan bug.                                                |
| Dukungan    | Membantu pengguna lain di forum dan Matrix.                                           |
| Promosi     | Mempromosikan KDE Plasma di media sosial dan acara.                                   |

#### 10.7.2 Langkah Pertama untuk Berkontribusi

{% stepper %}
{% step %}
### Bergabung dengan komunitas

Bergabunglah dengan Matrix dan KDE Discuss.
{% endstep %}

{% step %}
### Kenali alat

Pelajari Git, CMake, dan alat pengembangan KDE.
{% endstep %}

{% step %}
### Mulai dari yang kecil

Perbaiki bug kecil atau terjemahkan beberapa string.
{% endstep %}

{% step %}
### Bertanya

Jangan ragu untuk bertanya di Matrix atau forum.
{% endstep %}

{% step %}
### Berkembang

Setelah Anda nyaman, ambil tugas yang lebih besar.
{% endstep %}
{% endstepper %}

```bash
# 1. Buat akun di invent.kde.org
# 2. Fork repositori yang ingin Anda kontribusikan
git clone https://invent.kde.org/plasma/plasma-workspace.git

# 3. Buat branch untuk perubahan Anda
git checkout -b fix/my-bug-fix

# 4. Lakukan perubahan
# ...

# 5. Commit perubahan
git add .
git commit -m "Fix: deskripsi singkat perubahan"

# 6. Push ke fork Anda
git push origin fix/my-bug-fix

# 7. Buat Merge Request di invent.kde.org
```

#### 10.7.3 Sumber Daya untuk Kontributor Baru

* Get Involved: Halaman wiki dengan panduan untuk berkontribusi.
* New Contributors: Ruang Matrix untuk kontributor baru.
* Junior Jobs: Tugas-tugas yang cocok untuk kontributor baru.
* Mentoring: Program mentoring untuk pengembang baru.

{% hint style="info" %}
KDE memiliki program mentoring untuk membantu kontributor baru memulai. Jika Anda tertarik, cari informasi tentang program mentoring di wiki komunitas atau tanyakan di Matrix.
{% endhint %}

### 10.8 Ringkasan Bab

Bab ini telah membahas sumber daya dan komunitas KDE Plasma secara menyeluruh:

* Pendahuluan: Komunitas adalah fondasi KDE. Berkontribusi membantu orang lain, belajar keterampilan baru, dan membentuk masa depan KDE Plasma.
* Dokumentasi resmi: `docs.kde.org`, `userbase.kde.org`, `community.kde.org`, `techbase.kde.org`, dan `develop.kde.org` menyediakan dokumentasi untuk berbagai audiens.
* Komunitas: KDE Discuss, Matrix, mailing list, komunitas lokal, dan Akademy adalah saluran utama untuk berinteraksi dengan komunitas.
* KDE Store: Pusat distribusi untuk tema, widget, dan add-on pihak ketiga. Diakses melalui System Settings atau situs web.
* Distribusi: Berbagai distribusi menyertakan KDE Plasma sebagai default atau opsi, termasuk Kubuntu, Fedora KDE, openSUSE, Manjaro KDE, dan banyak lagi.
* Buku dan literatur: Meskipun terbatas, ada beberapa buku tentang KDE Plasma. Arianna adalah pembaca e-book KDE yang berguna.
* Cara berkontribusi: Ada banyak cara untuk berkontribusi, dari kode hingga terjemahan, dari dokumentasi hingga desain.

Bab selanjutnya akan membahas tips dan trik KDE Plasma, termasuk pintasan keyboard, konfigurasi melalui CLI, reset Plasma ke default, backup dan restore konfigurasi, dan otomasi dengan skrip.

## 11 Tips dan Trik

> “Pengetahuan adalah kekuatan, tetapi pengetahuan yang diterapkan adalah kebijaksanaan.”
>
> — Pepatah lama

Sepanjang buku ini, kita telah membangun pemahaman yang mendalam tentang KDE Plasma: dari filosofi dan arsitektur, hingga instalasi, kustomisasi, pengembangan, dan pemecahan masalah. Bab ini menyatukan semua pengetahuan tersebut menjadi kumpulan tips dan trik praktis yang dapat langsung Anda terapkan. Kita akan menjelajahi pintasan keyboard yang menghemat waktu, teknik konfigurasi melalui command line untuk otomasi, prosedur reset yang aman, strategi backup dan restore yang andal, serta seni mengotomasi tugas-tugas rutin. Bab ini bukan sekadar daftar perintah, tetapi panduan tentang bagaimana bekerja lebih cerdas, bukan lebih keras.

### 11.1 Pintasan Keyboard Penting

Pintasan keyboard adalah cara tercepat untuk berinteraksi dengan KDE Plasma. Menguasai pintasan yang tepat dapat menghemat waktu dan meningkatkan produktivitas secara signifikan.

#### 11.1.1 Pintasan Dasar

Berikut pintasan-pintasan dasar yang wajib diketahui oleh setiap pengguna KDE Plasma:

| Pintasan                   | Fungsi                                      |
| -------------------------- | ------------------------------------------- |
| Alt + Space atau Alt + F2  | Membuka KRunner                             |
| Alt + Tab                  | Beralih antar jendela                       |
| Ctrl + Alt + L             | Mengunci layar                              |
| Ctrl + F12                 | Menampilkan desktop, minimize semua jendela |
| Meta                       | Membuka Application Launcher                |
| Meta + W                   | Membuka efek Overview                       |
| Meta + Q                   | Membuka Activities Switcher                 |
| Ctrl + F1 hingga Ctrl + F4 | Beralih ke virtual desktop 1–4              |

{% hint style="info" %}
Pintasan Alt + Space dan Alt + F2 keduanya membuka KRunner. Pilih salah satu yang paling nyaman bagi Anda, dan Anda dapat menonaktifkan yang lain di System Settings Shortcuts.
{% endhint %}

#### 11.1.2 Pintasan Manajemen Jendela

| Pintasan                  | Fungsi                                                       |
| ------------------------- | ------------------------------------------------------------ |
| Meta + Left/Right         | Menempatkan jendela di sisi kiri/kanan layar                 |
| Meta + Up                 | Memaksimalkan jendela                                        |
| Meta + Down               | Meminimalkan jendela                                         |
| Meta + Shift + Up         | Memaksimalkan jendela secara vertikal                        |
| Meta + Shift + Left/Right | Memindahkan jendela ke monitor kiri/kanan                    |
| Ctrl + Alt + Del          | Menampilkan dialog logout                                    |
| Ctrl + Alt + Esc          | Membuka dialog untuk mematikan aplikasi yang tidak responsif |

#### 11.1.3 Pintasan KRunner

Setelah KRunner terbuka, Anda dapat menggunakan pintasan berikut:

* `Tab`: Menavigasi antar hasil.
* `Enter`: Menjalankan hasil yang dipilih.
* `Esc`: Menutup KRunner.
* `>`: Menjalankan perintah shell, misalnya `> top`.
* `=`: Melakukan perhitungan, misalnya `= 2+2`.
* `:`: Mencari emoji, misalnya `:smile:`.

#### 11.1.4 Kustomisasi Pintasan

Anda dapat mengkustomisasi pintasan keyboard melalui System Settings Shortcuts.

{% stepper %}
{% step %}
### Buka System Settings Shortcuts
{% endstep %}

{% step %}
### Pilih kategori yang ingin diubah

Misalnya, Custom Shortcuts, Global Shortcuts, atau Standard Shortcuts.
{% endstep %}

{% step %}
### Cari aksi yang ingin diubah pintasannya
{% endstep %}

{% step %}
### Klik pada pintasan saat ini dan tekan kombinasi tombol baru
{% endstep %}

{% step %}
### Klik Apply
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Untuk membuat pintasan kustom yang menjalankan perintah, gunakan Custom Shortcuts di System Settings Shortcuts. Misalnya, Anda dapat membuat pintasan Meta + T untuk membuka terminal, atau Meta + E untuk membuka editor teks favorit Anda.
{% endhint %}

### 11.2 Konfigurasi melalui CLI

Meskipun KDE Plasma menyediakan antarmuka grafis yang kaya untuk konfigurasi, ada kalanya bekerja melalui command line lebih efisien, terutama untuk otomasi dan manajemen jarak jauh.

#### 11.2.1 Kwriteconfig: Menulis Konfigurasi

`kwriteconfig6` adalah alat command line untuk menulis nilai ke berkas konfigurasi KDE. Ia sangat berguna untuk mengubah pengaturan tanpa membuka System Settings.

```bash
# Sintaks dasar
kwriteconfig6 --file <file> --group <group> --key <key> <value>

# Contoh: Mengubah tema Plasma
kwriteconfig6 --file kdeglobals --group KDE --key LookAndFeelPackage org.kde.breeze.desktop

# Contoh: Mengubah skema warna
kwriteconfig6 --file kdeglobals --group General --key ColorScheme BreezeDark

# Contoh: Mengaktifkan borderless maximized windows di KWin
kwriteconfig6 --file kwinrc --group Windows --key BorderlessMaximizedWindows true

# Contoh: Menghapus kunci
kwriteconfig6 --file kwinrc --group Windows --key BorderlessMaximizedWindows --delete

# Contoh: Mengubah konfigurasi keyboard
kwriteconfig6 --file kxkbrc --group Layout --key Options "caps:backspace"
```

{% hint style="info" %}
Untuk Plasma 6, gunakan `kwriteconfig6`. Untuk Plasma 5, gunakan `kwriteconfig5`. Di beberapa distribusi, `kwriteconfig` adalah symlink ke versi yang sesuai.
{% endhint %}

#### 11.2.2 Kreadconfig: Membaca Konfigurasi

`kreadconfig6` adalah alat untuk membaca nilai dari berkas konfigurasi KDE.

```bash
# Membaca nilai kunci
kreadconfig6 --file kdeglobals --group General --key ColorScheme

# Membaca dengan nilai default jika kunci tidak ada
kreadconfig6 --file kdeglobals --group General --key NonExistent --default "default_value"

# Melihat semua kunci dalam sebuah grup
kreadconfig6 --file kdeglobals --group General --list
```

#### 11.2.3 Plasma-Apply: Mengubah Tema

`plasma-apply` adalah kumpulan skrip untuk mengubah berbagai aspek tema Plasma melalui command line.

```bash
# Mengubah skema warna
plasma-apply-colorscheme BreezeDark

# Melihat daftar skema warna yang tersedia
plasma-apply-colorscheme --list-schemes

# Mengubah wallpaper
plasma-apply-wallpaperimage /path/to/wallpaper.jpg

# Mengubah tema desktop (Plasma Style)
plasma-apply-desktoptheme default

# Mengubah tema global (Look and Feel)
plasma-apply-lookandfeel --apply org.kde.breezedark.desktop

# Melihat daftar tema global yang tersedia
plasma-apply-lookandfeel --list

# Mengubah tema ikon
plasma-apply-icontheme Papirus-Dark
```

#### 11.2.4 Menerapkan Perubahan

Setelah mengubah konfigurasi melalui `kwriteconfig`, beberapa pengaturan mungkin memerlukan restart layanan atau signal D-Bus untuk diterapkan.

```bash
# Restart Plasma Shell (untuk perubahan tampilan)
kquitapp6 plasmashell && kstart plasmashell

# Restart KWin (untuk perubahan window manager)
kwin_wayland --replace

# Mengirim sinyal D-Bus untuk reload konfigurasi keyboard
dbus-send --session --type=signal --reply-timeout=100 \
  --dest=org.kde.keyboard /Layouts org.kde.keyboard.reloadConfig

# Reload konfigurasi KWin
qdbus org.kde.KWin /KWin reconfigure
```

{% hint style="info" %}
Untuk mengotomasi konfigurasi sistem, Anda dapat menulis skrip yang menggunakan `kwriteconfig6` untuk mengatur banyak pengaturan sekaligus, lalu menerapkannya dengan restart layanan yang sesuai. Ini sangat berguna untuk deployment di banyak mesin.
{% endhint %}

### 11.3 Reset Plasma ke Default

Ketika KDE Plasma mengalami masalah yang sulit dipecahkan, atau ketika Anda ingin memulai dari awal, reset ke pengaturan default adalah solusi yang efektif.

#### 11.3.1 Reset Selektif

Reset selektif melibatkan penghapusan atau penggantian nama berkas konfigurasi tertentu, memungkinkan Plasma untuk membuat yang baru dengan pengaturan default.

```bash
# 1. Backup konfigurasi lama terlebih dahulu
mkdir -p ~/plasma-backup
cp -r ~/.config/plasma* ~/plasma-backup/ 2>/dev/null
cp ~/.config/kdeglobals ~/plasma-backup/ 2>/dev/null
cp ~/.config/kwinrc ~/plasma-backup/ 2>/dev/null

# 2. Hapus atau ganti nama berkas konfigurasi tertentu
# Reset tata letak widget dan panel
mv ~/.config/plasma-org.kde.plasma.desktop-appletsrc ~/plasma-backup/

# Reset pengaturan Plasma Shell
mv ~/.config/plasmashellrc ~/plasma-backup/

# Reset pengaturan KWin
mv ~/.config/kwinrc ~/plasma-backup/

# Reset pengaturan global KDE (tema, ikon, font)
mv ~/.config/kdeglobals ~/plasma-backup/

# 3. Hapus cache Plasma
rm -rf ~/.cache/plasma*
rm -rf ~/.cache/qmlcache/
rm -rf ~/.cache/plasmashell/

# 4. Restart Plasma Shell
kquitapp6 plasmashell && kstart plasmashell

# 5. Jika perlu, logout dan login kembali
```

#### 11.3.2 Reset Total dengan Skrip

Untuk reset yang lebih menyeluruh, Anda dapat menggunakan skrip yang menghapus semua konfigurasi terkait KDE. Proyek seperti kde-reset menyediakan skrip untuk tujuan ini.

```bash
#!/bin/bash
# kde-reset: Reset semua konfigurasi dan cache KDE

BACKUP_DIR="$HOME/kde-reset-backup-$(date +%Y%m%d-%H%M%S)"
mkdir -p "$BACKUP_DIR"

echo "Backup ke: $BACKUP_DIR"

# Backup dan hapus konfigurasi KDE
for item in ~/.config/plasma* ~/.config/kde* ~/.config/kwin* \
  ~/.config/khotkeys* ~/.config/kglobalshortcuts* \
  ~/.config/krunner* ~/.config/ksmserver*; do
  if [ -e "$item" ]; then
    cp -r "$item" "$BACKUP_DIR/"
    rm -rf "$item"
  fi
done

# Hapus cache
rm -rf ~/.cache/plasma*
rm -rf ~/.cache/qmlcache/
rm -rf ~/.cache/plasmashell/

echo "Reset selesai. Silakan logout dan login kembali."
```

#### 11.3.3 Reset melalui System Settings

Plasma 6 menyediakan modul reset pabrik di System Settings. Fitur ini memungkinkan pengguna untuk mereset perangkat ke pengaturan default.

{% stepper %}
{% step %}
### Buka System Settings
{% endstep %}

{% step %}
### Navigasi ke Plasma Settings atau About System
{% endstep %}

{% step %}
### Cari opsi Reset to default settings atau Factory Reset
{% endstep %}

{% step %}
### Pilih pengguna yang ingin direset

Biasanya “Last logged-in user”.
{% endstep %}

{% step %}
### Klik Apply
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Reset pabrik akan menghapus semua konfigurasi pribadi Anda, termasuk tema, widget, pintasan, dan pengaturan panel. Pastikan Anda telah mem-backup semua yang penting sebelum melanjutkan. Setelah reset, Anda perlu me-restart sistem atau logout dan login kembali.
{% endhint %}

#### 11.3.4 Setelah Reset

Setelah reset, Anda akan memiliki KDE Plasma dengan pengaturan default. Anda dapat:

* Mengimpor kembali pengaturan dari backup jika diinginkan.
* Membangun konfigurasi baru dari awal.
* Menginstal ulang tema dan widget yang Anda gunakan sebelumnya.

{% hint style="info" %}
Jika Anda sering melakukan reset, pertimbangkan untuk membuat skrip yang secara otomatis mem-backup konfigurasi Anda sebelum reset. Ini akan menghemat waktu dan memastikan Anda tidak kehilangan pengaturan penting.
{% endhint %}

### 11.4 Backup dan Restore Konfigurasi

Backup konfigurasi KDE Plasma sangat penting, terutama sebelum melakukan pembaruan besar, menginstal tema baru, atau melakukan reset.

#### 11.4.1 Lokasi Konfigurasi Penting

Berikut lokasi berkas konfigurasi dan data yang perlu di-backup:

| Lokasi                                              | Konten                   |
| --------------------------------------------------- | ------------------------ |
| `~/.config/plasma*`                                 | Konfigurasi Plasma Shell |
| `~/.config/kdeglobals`                              | Pengaturan global KDE    |
| `~/.config/kwinrc`                                  | Konfigurasi KWin         |
| `~/.config/kglobalshortcutsrc`                      | Pintasan keyboard global |
| `~/.config/plasma-org.kde.plasma.desktop-appletsrc` | Tata letak widget        |
| `~/.local/share/plasma/`                            | Widget dan tema pengguna |
| `~/.local/share/color-schemes/`                     | Skema warna kustom       |
| `~/.local/share/icons/`                             | Tema ikon kustom         |

#### 11.4.2 Backup Manual

```bash
# Buat direktori backup
mkdir -p ~/plasma-config-backup

# Backup konfigurasi utama
cp -r ~/.config/plasma* ~/plasma-config-backup/
cp ~/.config/kdeglobals ~/plasma-config-backup/
cp ~/.config/kwinrc ~/plasma-config-backup/
cp ~/.config/kglobalshortcutsrc ~/plasma-config-backup/

# Backup data pengguna
cp -r ~/.local/share/plasma/ ~/plasma-config-backup/
cp -r ~/.local/share/color-schemes/ ~/plasma-config-backup/
cp -r ~/.local/share/icons/ ~/plasma-config-backup/

# Buat arsip tar
tar -czvf ~/plasma-backup-$(date +%Y%m%d).tar.gz -C ~ plasma-config-backup
```

#### 11.4.3 Restore Konfigurasi

```bash
# Ekstrak arsip backup
tar -xzvf ~/plasma-backup-20261012.tar.gz -C ~

# Salin kembali konfigurasi
cp -r ~/plasma-config-backup/plasma* ~/.config/
cp ~/plasma-config-backup/kdeglobals ~/.config/
cp ~/plasma-config-backup/kwinrc ~/.config/
cp ~/plasma-config-backup/kglobalshortcutsrc ~/.config/

# Salin kembali data pengguna
cp -r ~/plasma-config-backup/plasma/ ~/.local/share/
cp -r ~/plasma-config-backup/color-schemes/ ~/.local/share/
cp -r ~/plasma-config-backup/icons/ ~/.local/share/

# Restart Plasma
kquitapp6 plasmashell && kstart plasmashell
```

#### 11.4.4 Alat Backup Khusus

Beberapa alat dapat membantu mem-backup dan me-restore konfigurasi KDE Plasma:

| Alat                                    | Kegunaan                                                                                      |
| --------------------------------------- | --------------------------------------------------------------------------------------------- |
| PlasmaSafe                              | Alat command line untuk backup, restore, diff, verify, export, dan import konfigurasi Plasma. |
| Konsave                                 | Alat untuk menyimpan dan memuat konfigurasi Plasma, termasuk tema, widget, dan pengaturan.    |
| ArchLinux-KDE-Backup-and-Restore-Script | Skrip backup dan restore lengkap untuk Arch Linux dengan KDE Plasma.                          |

```bash
# Backup konfigurasi
plasmasafe backup mysnapshot

# Restore konfigurasi
plasmasafe restore mysnapshot

# Verifikasi snapshot
plasmasafe verify mysnapshot

# Melihat perbedaan
plasmasafe diff mysnapshot
```

{% hint style="info" %}
Lakukan backup konfigurasi secara teratur, terutama sebelum melakukan perubahan besar seperti pembaruan Plasma, menginstal tema baru, atau mengubah konfigurasi multi-layar. Simpan backup di lokasi yang aman, seperti drive eksternal atau cloud storage.
{% endhint %}

### 11.5 Otomasi dengan Skrip

Otomasi adalah kunci untuk produktivitas. Dengan skrip yang tepat, Anda dapat mengotomasi tugas-tugas rutin seperti mengubah tema berdasarkan waktu, mengatur wallpaper, atau mengonfigurasi sistem secara otomatis.

#### 11.5.1 Skrip Beralih Tema Otomatis

Salah satu otomasi yang paling populer adalah beralih antara tema terang dan gelap berdasarkan waktu.

```bash
#!/bin/bash
# auto-theme-switch: Beralih tema berdasarkan waktu

HOUR=$(date +%H)

# Tema gelap dari jam 18:00 hingga 06:00
if [ "$HOUR" -ge 18 ] || [ "$HOUR" -lt 6 ]; then
  plasma-apply-colorscheme BreezeDark
  plasma-apply-lookandfeel --apply org.kde.breezedark.desktop
  echo "Tema gelap diterapkan"
else
  plasma-apply-colorscheme BreezeLight
  plasma-apply-lookandfeel --apply org.kde.breeze.desktop
  echo "Tema terang diterapkan"
fi
```

Anda dapat menjalankan skrip ini melalui cron atau systemd timer.

```bash
# Buat file layanan systemd user
mkdir -p ~/.config/systemd/user/

cat > ~/.config/systemd/user/auto-theme.service << EOF
[Unit]
Description=Auto theme switch

[Service]
Type=oneshot
ExecStart=/home/$USER/scripts/auto-theme-switch.sh
EOF

cat > ~/.config/systemd/user/auto-theme.timer << EOF
[Unit]
Description=Run auto theme switch daily

[Timer]
OnCalendar=*-*-* 06:00:00
OnCalendar=*-*-* 18:00:00
Persistent=true

[Install]
WantedBy=timers.target
EOF

# Aktifkan timer
systemctl --user enable --now auto-theme.timer

# Periksa status
systemctl --user list-timers
```

#### 11.5.2 Skrip Wallpaper Rotasi

Skrip untuk merotasi wallpaper secara otomatis dari direktori gambar:

```bash
#!/bin/bash
# wallpaper-rotate: Merotasi wallpaper dari direktori

WALLPAPER_DIR="$HOME/Pictures/Wallpapers"
INTERVAL=300 # detik

while true; do
  # Pilih gambar acak
  WALLPAPER=$(find "$WALLPAPER_DIR" -type f \( -name "*.jpg" -o -name "*.png" \) | shuf -n 1)

  if [ -n "$WALLPAPER" ]; then
    plasma-apply-wallpaperimage "$WALLPAPER"
    echo "Wallpaper diubah: $WALLPAPER"
  fi

  sleep $INTERVAL
done
```

#### 11.5.3 Skrip Konfigurasi Multi-Mesin

Untuk administrator sistem yang mengelola banyak mesin, skrip konfigurasi dapat menghemat waktu:

```bash
#!/bin/bash
# deploy-plasma-config: Mengonfigurasi Plasma secara otomatis

# Set tema
kwriteconfig6 --file kdeglobals --group KDE --key LookAndFeelPackage org.kde.breeze.desktop

# Set skema warna
kwriteconfig6 --file kdeglobals --group General --key ColorScheme BreezeDark

# Set tema ikon
kwriteconfig6 --file kdeglobals --group Icons --key Theme Papirus-Dark

# Set font
kwriteconfig6 --file kdeglobals --group General --key font "Noto Sans,10,-1,5,50,0,0,0,0,0"

# Set pintasan keyboard
kwriteconfig6 --file kglobalshortcutsrc --group krunner --key "_launch" "Alt+Space"

# Konfigurasi KWin
kwriteconfig6 --file kwinrc --group Windows --key BorderlessMaximizedWindows true
kwriteconfig6 --file kwinrc --group Compositing --key Enabled true

# Terapkan perubahan
qdbus org.kde.KWin /KWin reconfigure
kquitapp6 plasmashell && kstart plasmashell

echo "Konfigurasi Plasma diterapkan."
```

#### 11.5.4 KWin Scripting

KWin mendukung scripting dengan JavaScript dan QML. Ini memungkinkan otomasi manajemen jendela yang lebih canggih.

```javascript
// Contoh KWin script: Memindahkan jendela baru ke desktop saat ini
// Simpan sebagai ~/.local/share/kwin/scripts/my-script/contents/code/main.js

function moveToCurrentDesktop(window) {
  if (window.normalWindow) {
    window.desktops = [workspace.currentDesktop];
  }
}

workspace.windowAdded.connect(moveToCurrentWindow);
```

Anda dapat menguji KWin script melalui Plasma Desktop Scripting Console yang dapat dibuka melalui KRunner (`Alt + F2`).

#### 11.5.5 Otomasi dengan Lunar Plasma

Lunar Plasma adalah antarmuka scripting Lua untuk desktop KDE Plasma. Ia memungkinkan kontrol programmatic atas berbagai aspek desktop.

```lua
-- Contoh Lunar Plasma script
local plasma = dofile(os.getenv("HOME").."/.local/opt/lunar-plasma/lunar-plasma.lua")

-- Set volume output default ke 50%
plasma.volume.set(50)

-- Kirim notifikasi desktop
plasma.notification.send({
  title = "Lunar Plasma",
  body = "Otomasi berjalan dengan sukses"
})
```

{% hint style="info" %}
Lunar Plasma adalah proyek pihak ketiga dan mungkin tidak tersedia di semua distribusi. Periksa repositori GitHub-nya untuk informasi instalasi terbaru.
{% endhint %}

#### 11.5.6 Contoh: Skrip Reset + Backup Otomatis

Skrip yang menggabungkan reset dan backup otomatis:

```bash
#!/bin/bash
# reset-with-backup: Reset Plasma dengan backup otomatis

BACKUP_DIR="$HOME/plasma-reset-backup-$(date +%Y%m%d-%H%M%S)"
mkdir -p "$BACKUP_DIR"

echo "=== Backup konfigurasi ke $BACKUP_DIR ==="

# Backup semua konfigurasi Plasma
for item in ~/.config/plasma* ~/.config/kdeglobals ~/.config/kwinrc \
  ~/.config/kglobalshortcutsrc; do
  if [ -e "$item" ]; then
    cp -r "$item" "$BACKUP_DIR/"
  fi
done

# Backup data pengguna
cp -r ~/.local/share/plasma/ "$BACKUP_DIR/" 2>/dev/null
cp -r ~/.local/share/color-schemes/ "$BACKUP_DIR/" 2>/dev/null

echo "=== Menghapus konfigurasi ==="

# Hapus konfigurasi
rm -rf ~/.config/plasma*
rm -f ~/.config/kdeglobals
rm -f ~/.config/kwinrc
rm -f ~/.config/kglobalshortcutsrc

# Hapus cache
rm -rf ~/.cache/plasma*
rm -rf ~/.cache/qmlcache/

echo "=== Restart Plasma Shell ==="
kquitapp6 plasmashell && kstart plasmashell

echo "Reset selesai. Backup tersimpan di: $BACKUP_DIR"
```

### 11.6 Ringkasan Bab

Bab ini telah membahas tips dan trik KDE Plasma secara menyeluruh:

* Pintasan keyboard: Pintasan dasar seperti Alt + F2 untuk KRunner, Ctrl + Alt + L untuk kunci layar, dan Ctrl + F12 untuk tampilkan desktop meningkatkan produktivitas secara signifikan.
* Konfigurasi CLI: `kwriteconfig6` dan `kreadconfig6` memungkinkan perubahan pengaturan dari command line. `plasma-apply` menyediakan cara cepat untuk mengubah tema, skema warna, dan wallpaper.
* Reset Plasma: Reset selektif dengan menghapus berkas konfigurasi tertentu, atau reset total dengan skrip seperti kde-reset. Plasma 6 menyediakan modul reset pabrik di System Settings.
* Backup dan restore: Backup konfigurasi secara teratur ke lokasi yang aman. Gunakan alat seperti PlasmaSafe atau Konsave untuk memudahkan proses.
* Otomasi: Skrip bash, systemd timer, KWin scripting, dan Lunar Plasma memungkinkan otomasi tugas-tugas rutin seperti beralih tema, merotasi wallpaper, dan konfigurasi multi-mesin.

Bab selanjutnya akan membahas kesimpulan dari keseluruhan buku, termasuk ringkasan perjalanan, masa depan KDE Plasma, dan ajakan untuk berkontribusi.

## 12 Kesimpulan

> “Perjalanan seribu mil dimulai dengan satu langkah.”
>
> — Lao Tzu

Kita telah tiba di akhir perjalanan panjang melalui dunia KDE Plasma. Dari filosofi yang menempatkan pengguna sebagai raja, melalui sejarah yang penuh gejolak namun akhirnya berbuah kematangan, hingga arsitektur modular yang memungkinkan evolusi tanpa henti—kita telah menjelajahi setiap sudut lingkungan desktop yang luar biasa ini. Bab ini bukan hanya penutup, tetapi juga refleksi: tentang apa yang telah kita pelajari, tentang masa depan yang menanti, dan tentang bagaimana Anda dapat menjadi bagian dari komunitas global yang telah membuat KDE Plasma menjadi apa yang ada saat ini.

### 12.1 Ringkasan Perjalanan

Buku ini dimulai dengan pertanyaan sederhana: apa itu KDE Plasma, dan mengapa jutaan orang memilihnya? Sepanjang dua belas bab, kita telah menjawab pertanyaan ini dari berbagai sudut pandang.

#### 12.1.1 Dari Filosofi hingga Praktik

Perjalanan kita dimulai di Bab 1 dengan pemahaman tentang filosofi inti KDE: pengguna adalah raja. Kita melihat bagaimana prinsip ini diterjemahkan menjadi lima prinsip konkret—kebebasan konfigurasi, konsistensi, aksesibilitas, internasionalisasi, dan kinerja—yang memandu setiap keputusan desain dalam KDE Plasma.

Di Bab 2, kita menelusuri evolusi KDE Plasma dari KDE 3 hingga Plasma 6. Kita belajar bahwa inovasi tidak selalu berjalan mulus: peluncuran KDE 4.0 yang bermasalah mengajarkan pentingnya komunikasi dengan pengguna dan kesabaran dalam mengadopsi teknologi baru. Namun, dari masa sulit itu lahir Plasma 5 yang matang dan Plasma 6 yang ambisius.

Bab 3 membawa kita ke dalam arsitektur KDE Plasma. Kita melihat bagaimana tumpukan perangkat lunaknya dibangun dari lapisan-lapisan yang saling bergantung melalui antarmuka yang stabil. Kita memahami peran Plasma Shell, KWin, KDE Frameworks, dan libplasma dalam menciptakan pengalaman desktop yang koheren.

Bab 4 hingga Bab 6 mengubah teori menjadi praktik. Kita belajar cara menginstal KDE Plasma di berbagai distribusi, cara menggunakannya sehari-hari—dari widget hingga Activities hingga KRunner—dan cara mengkustomisasinya secara menyeluruh, dari Global Theme hingga widget kustom.

Bab 7 membuka pintu bagi mereka yang ingin menjadi pencipta, bukan hanya konsumen. Kita belajar cara mengembangkan widget, plugin QML C++, dan modul konfigurasi. Kita melihat bahwa berkontribusi pada KDE Plasma bukanlah hal yang eksklusif untuk pengembang berpengalaman; dengan alat yang tepat dan semangat belajar, siapa pun dapat membuat perbedaan.

Bab 8 hingga Bab 11 membekali kita dengan pengetahuan untuk menjadi pengguna yang mahir. Kita mempelajari fitur-fitur terbaru Plasma 6.x, cara memecahkan masalah yang paling rumit, sumber daya dan komunitas yang tersedia, serta tips dan trik yang menghemat waktu.

{% hint style="info" %}
Setiap bab dalam buku ini dirancang untuk berdiri sendiri, namun juga terhubung dengan bab-bab lainnya. Pembaca yang baru mengenal KDE Plasma dapat membaca secara berurutan, sementara pembaca yang sudah berpengalaman dapat melompat langsung ke topik yang diminati.
{% endhint %}

#### 12.1.2 Pelajaran Utama

Dari perjalanan ini, kita dapat menarik beberapa pelajaran utama:

1. Fleksibilitas adalah kekuatan. KDE Plasma tidak memaksakan satu cara untuk bekerja. Sebaliknya, ia menyediakan fondasi yang kokoh di mana pengguna dapat membangun lingkungan yang sesuai dengan kebutuhan mereka.
2. Komunitas adalah fondasi. Tanpa ribuan kontributor dari seluruh dunia, KDE Plasma tidak akan mencapai kematangan seperti sekarang. Setiap kontribusi, sekecil apa pun, membuat perbedaan.
3. Evolusi memerlukan kesabaran. Transisi dari KDE 3 ke Plasma 4, dari Plasma 4 ke Plasma 5, dan dari Plasma 5 ke Plasma 6 masing-masing memerlukan waktu bertahun-tahun. Namun, hasilnya sepadan dengan usaha.
4. Dokumentasi dan dukungan sangat penting. Salah satu alasan mengapa KDE Plasma berhasil adalah karena komunitasnya yang aktif dan sumber daya yang kaya. Pengguna tidak pernah sendirian ketika menghadapi masalah.
5. Standar terbuka memungkinkan kolaborasi. Kepatuhan KDE Plasma terhadap standar seperti Freedesktop.org memungkinkan integrasi dengan berbagai aplikasi dan lingkungan desktop.

### 12.2 Masa Depan KDE Plasma

Apa yang menanti KDE Plasma di masa depan? Meskipun tidak ada yang dapat memprediksi dengan pasti, beberapa tren dan arah pengembangan sudah terlihat jelas.

#### 12.2.1 Tren Jangka Pendek

**Konsolidasi Wayland**

Plasma 6.8 menandai penghapusan sesi X11. Langkah ini bukan tanpa risiko, tetapi komunitas KDE yakin bahwa Wayland adalah masa depan. Di tahun-tahun mendatang, kita dapat mengharapkan:

* Peningkatan dukungan untuk aplikasi X11 melalui XWayland.
* Fitur-fitur Wayland yang lebih matang, seperti HDR dan variable refresh rate.
* Dukungan yang lebih baik untuk perangkat keras yang lebih baru.
* Peningkatan performa dan efisiensi daya.

**Integrasi Fitur**

Plasma terus mengintegrasikan fitur-fitur yang sebelumnya memerlukan aplikasi pihak ketiga:

* Backup: Kup sebagai penjadwal backup kelas satu.
* OCR: Spectacle OCR untuk ekstraksi teks.
* Kontrol Mikrofon: Tes volume mikrofon terintegrasi.
* Manajemen Printer: Peningkatan signifikan dalam integrasi printer.

**Personalisasi yang Lebih Dalam**

Sistem tema Union, meskipun masih dalam tahap awal, menjanjikan kemampuan kustomisasi yang lebih dalam. Di masa depan, kita dapat mengharapkan:

* Tema yang lebih dinamis dan responsif.
* Integrasi yang lebih baik antara tema dan aplikasi.
* Dukungan untuk lebih banyak format dan standar.

#### 12.2.2 Tren Jangka Panjang

**Konvergensi Desktop dan Mobile**

Plasma Mobile dan Plasma Desktop berbagi banyak kode dan konsep. Di masa depan, kita dapat mengharapkan konvergensi yang lebih besar antara keduanya, memungkinkan pengalaman yang konsisten di berbagai faktor bentuk.

**Kecerdasan Buatan**

Meskipun KDE belum mengumumkan fitur AI yang spesifik, ada ekspektasi bahwa AI akan memainkan peran yang lebih besar dalam lingkungan desktop. Misalnya, asisten cerdas, otomasi yang lebih baik, dan personalisasi yang lebih dalam.

**Keamanan dan Privasi**

Seiring dengan meningkatnya kekhawatiran tentang privasi, KDE terus meningkatkan keamanan dan privasi KDE Plasma. Fitur seperti enkripsi Vault dan kontrol yang lebih baik atas data pengguna akan terus dikembangkan.

#### 12.2.3 Tantangan

Meskipun masa depan tampak cerah, KDE Plasma menghadapi beberapa tantangan:

1. Keberlanjutan kontribusi. Menarik dan mempertahankan kontributor adalah tantangan bagi semua proyek open source.
2. Kompatibilitas. Menjaga kompatibilitas dengan aplikasi dan perangkat keras lama sambil berinovasi adalah keseimbangan yang sulit.
3. Kompetisi. Lingkungan desktop lain terus berkembang, dan KDE Plasma harus tetap kompetitif.
4. Pendanaan. Meskipun KDE adalah proyek nirlaba, pendanaan tetap menjadi tantangan untuk pengembangan jangka panjang.

{% hint style="info" %}
Jika Anda ingin membantu mengatasi tantangan ini, ada banyak cara untuk berkontribusi. Selain kode, Anda dapat membantu dengan terjemahan, dokumentasi, desain, atau bahkan donasi ke KDE e.V.
{% endhint %}

### 12.3 Ajakan Berkontribusi

Salah satu cara terbaik untuk memastikan masa depan KDE Plasma yang cerah adalah dengan berkontribusi. Bagian ini menyajikan peta jalan bagi mereka yang ingin terlibat.

#### 12.3.1 Mengapa Berkontribusi?

Berkontribusi pada KDE Plasma bukan hanya tentang memberi; ini juga tentang menerima:

* Pembelajaran: Anda akan belajar keterampilan baru, dari pemrograman hingga desain hingga manajemen proyek.
* Jaringan: Anda akan bertemu orang-orang dari seluruh dunia yang berbagi minat Anda.
* Kepuasan: Ada kepuasan tersendiri dalam mengetahui bahwa karya Anda digunakan oleh jutaan orang.
* Dampak: Kontribusi Anda akan membentuk masa depan KDE Plasma.

#### 12.3.2 Cara Berkontribusi

Ada banyak cara untuk berkontribusi, tergantung pada keterampilan dan minat Anda:

| Kontribusi  | Deskripsi                                                                        |
| ----------- | -------------------------------------------------------------------------------- |
| Kode        | Berkontribusi pada pengembangan KDE Plasma dengan menulis C++, QML, atau Python. |
| Terjemahan  | Menerjemahkan KDE Plasma ke bahasa Anda.                                         |
| Dokumentasi | Menulis atau memperbarui dokumentasi pengguna dan pengembang.                    |
| Desain      | Membuat tema, ikon, wallpaper, atau mockup UI.                                   |
| Pengujian   | Menguji versi beta dan melaporkan bug.                                           |
| Dukungan    | Membantu pengguna lain di forum dan Matrix.                                      |
| Promosi     | Menulis artikel, membuat video, atau berbicara di konferensi.                    |
| Donasi      | Mendukung KDE e.V. secara finansial.                                             |

#### 12.3.3 Langkah Pertama

Jika Anda baru memulai, berikut adalah langkah-langkah yang direkomendasikan:

{% stepper %}
{% step %}
### Bergabung dengan komunitas

Bergabunglah dengan Matrix (`#kde:kde.org`) dan KDE Discuss.
{% endstep %}

{% step %}
### Temukan minat Anda

Apa yang paling Anda nikmati? Kode, desain, atau dokumentasi?
{% endstep %}

{% step %}
### Mulai dari yang kecil

Perbaiki bug kecil, terjemahkan beberapa string, atau perbarui dokumentasi.
{% endstep %}

{% step %}
### Bertanya

Jangan ragu untuk bertanya di Matrix atau forum. Komunitas KDE sangat ramah.
{% endstep %}

{% step %}
### Berkembang

Setelah Anda nyaman, ambil tugas yang lebih besar.
{% endstep %}

{% step %}
### Bertahan

Kontribusi berkelanjutan lebih berharga daripada kontribusi besar sekali.
{% endstep %}
{% endstepper %}

```bash
# 1. Buat akun di invent.kde.org
# 2. Fork repositori yang ingin Anda kontribusikan
git clone https://invent.kde.org/plasma/plasma-workspace.git

# 3. Buat branch untuk perubahan Anda
git checkout -b fix/my-bug-fix

# 4. Lakukan perubahan
# ...

# 5. Commit perubahan
git add .
git commit -m "Fix: deskripsi singkat perubahan"

# 6. Push ke fork Anda
git push origin fix/my-bug-fix

# 7. Buat Merge Request di invent.kde.org
```

#### 12.3.4 Sumber Daya untuk Kontributor Baru

* Get Involved: [https://community.kde.org/Get%5FInvolved](https://community.kde.org/Get_Involved)
* New Contributors: [https://community.kde.org/New%5FContributors](https://community.kde.org/New_Contributors)
* Junior Jobs: [https://community.kde.org/Junior%5FJobs](https://community.kde.org/Junior_Jobs)
* Mentoring: [https://community.kde.org/Mentoring](https://community.kde.org/Mentoring)

{% hint style="info" %}
KDE memiliki program mentoring untuk membantu kontributor baru memulai. Jika Anda tertarik, cari informasi tentang program mentoring di wiki komunitas atau tanyakan di Matrix.
{% endhint %}

### 12.4 Penutup

Kita telah mencapai akhir buku ini, tetapi perjalanan Anda dengan KDE Plasma baru saja dimulai. Seperti yang telah kita lihat, KDE Plasma bukan hanya tentang perangkat lunak; ia adalah tentang komunitas, filosofi, dan visi tentang bagaimana komputasi seharusnya.

#### 12.4.1 Pesan Akhir

Jika ada satu pesan yang ingin kami sampaikan melalui buku ini, itu adalah: Anda memiliki kekuatan untuk membentuk lingkungan komputasi Anda. KDE Plasma adalah bukti hidup dari filosofi ini. Ia tidak memaksakan satu cara untuk bekerja; ia menyediakan alat dan kebebasan untuk menciptakan cara Anda sendiri.

Namun, kekuatan ini datang dengan tanggung jawab. Sebagai pengguna KDE Plasma, Anda adalah bagian dari komunitas global yang telah membuat lingkungan desktop ini menjadi apa yang ada saat ini. Jika Anda menemukan KDE Plasma bermanfaat, pertimbangkan untuk memberikan kembali—baik melalui kontribusi, dukungan, atau sekadar berbagi pengetahuan Anda dengan orang lain.

#### 12.4.2 Terima Kasih

Kami mengucapkan terima kasih kepada seluruh komunitas KDE: para pengembang, penerjemah, desainer, dokumenter, penguji, dan pengguna yang telah membuat KDE Plasma menjadi salah satu lingkungan desktop terbaik di dunia open source. Tanpa kerja keras dan dedikasi mereka, buku ini tidak akan ada.

Terima kasih juga kepada Anda, pembaca, yang telah meluangkan waktu untuk menjelajahi halaman-halaman buku ini. Kami berharap buku ini telah memberikan wawasan, keterampilan, dan inspirasi untuk menggunakan dan berkontribusi pada KDE Plasma.

Selamat berkarya dengan KDE Plasma.

Tim Penulis

2026

## Bagian V

## Lampiran

### Perintah CLI Penting

Lampiran ini menyediakan daftar perintah command line yang sering digunakan dalam pengelolaan KDE Plasma. Perintah-perintah ini berguna untuk otomasi, pemecahan masalah, dan konfigurasi lanjutan.

#### Manajemen Plasma

```bash
# Restart Plasma Shell
kquitapp6 plasmashell && kstart plasmashell

# Restart KWin
kwin_wayland --replace

# Menjalankan Plasma secara manual
dbus-run-session startplasma-wayland
dbus-launch --exit-with-x11 startplasma-x11

# Melihat versi Plasma
plasmashell --version

# Melihat versi KWin
kwin_wayland --version
```

#### Manajemen Tema

```bash
# Mengubah skema warna
plasma-apply-colorscheme BreezeDark

# Melihat daftar skema warna
plasma-apply-colorscheme --list-schemes

# Mengubah wallpaper
plasma-apply-wallpaperimage /path/to/wallpaper.jpg

# Mengubah Plasma Style
plasma-apply-desktoptheme default

# Mengubah tema global
plasma-apply-lookandfeel --apply org.kde.breeze.desktop

# Mengubah tema ikon
plasma-apply-icontheme Papirus-Dark
```

#### Manajemen Widget

```bash
# Melihat daftar widget yang terinstal
kpackagetool6 --type Plasma/Applet --list

# Menginstal widget
kpackagetool6 --type Plasma/Applet --install /path/to/widget

# Menghapus widget
kpackagetool6 --type Plasma/Applet --remove com.example.widget

# Menguji widget dengan plasmoidviewer
plasmoidviewer -a package
```

#### Manajemen Konfigurasi

```bash
# Membaca konfigurasi
kreadconfig6 --file kdeglobals --group General --key ColorScheme

# Menulis konfigurasi
kwriteconfig6 --file kdeglobals --group General --key ColorScheme BreezeDark

# Menghapus kunci
kwriteconfig6 --file kdeglobals --group General --key ColorScheme --delete

# Melihat daftar kunci dalam grup
kreadconfig6 --file kdeglobals --group General --list
```

#### Diagnostik

```bash
# Melihat log Plasma
journalctl --user -u plasma-plasmashell.service -b

# Melihat log KWin
journalctl --user -u plasma-kwin_wayland.service -b

# Melihat crash terbaru
coredumpctl list

# Melihat detail crash
coredumpctl info <PID>

# Melihat informasi display
kscreen-doctor -o

# Melihat status kompositing
qdbus org.kde.KWin /Compositor active

# Melihat daftar efek
qdbus org.kde.KWin /Effects loadedEffects
```

### Daftar Istilah

Berikut adalah daftar istilah yang sering digunakan dalam buku ini beserta definisinya. Istilah-istilah ini diurutkan secara alfabetis untuk memudahkan pencarian.

#### Activities

Konteks tingkat tinggi di KDE Plasma yang mencakup virtual desktop, widget, wallpaper, dan pengaturan panel yang independen.

#### Aurorae

Sistem dekorasi jendela berbasis SVG yang memungkinkan pembuatan tema dekorasi tanpa menulis kode C++.

#### Containment

Wadah untuk widget Plasma. Panel dan desktop adalah contoh-contoh containment. Sebuah containment dapat berisi widget lain dan mengelola tata letaknya.

#### Corona

Objek QGraphicsScene yang mengelola seluruh ruang kerja Plasma. Setiap Corona merepresentasikan satu layar fisik.

#### D-Bus

Sistem message bus yang memungkinkan komunikasi antar proses di Linux dan sistem mirip Unix.

#### Discover

Pusat perangkat lunak grafis di KDE Plasma untuk menginstal dan menghapus aplikasi.

#### ECM

Extra CMake Modules, kumpulan modul CMake dari KDE untuk menyederhanakan build system.

#### Freedesktop.org

Organisasi yang mengembangkan standar untuk interoperabilitas desktop di Linux dan sistem mirip Unix.

#### Global Menu

Menu aplikasi yang ditampilkan di panel atas, mirip dengan macOS.

#### Global Theme

Paket kustomisasi yang menggabungkan Plasma Style, skema warna, tema ikon, dekorasi jendela, task switcher, splash screen, dan tema lock screen.

#### HiDPI

High Dots Per Inch, layar dengan kepadatan piksel tinggi yang memerlukan scaling.

#### KCM

KDE Configuration Module, modul konfigurasi yang muncul di System Settings.

#### KConfig

Sistem manajemen konfigurasi KDE yang menggunakan berkas INI yang dapat dibaca manusia.

#### KConfigXT

Sistem yang menghasilkan kode konfigurasi dari berkas XML, menyederhanakan manajemen pengaturan.

#### KDecoration

API C++ untuk membuat dekorasi jendela dengan kontrol penuh atas perilaku dan rendering.

#### KDE Frameworks

Kumpulan lebih dari 80 pustaka modular yang menyediakan fungsionalitas umum untuk aplikasi KDE.

#### KDE Store

Platform online untuk membagikan dan mengunduh tema, widget, dan add-on untuk KDE Plasma.

#### KIO

KDE Input/Output, pustaka yang menyediakan abstraksi I/O untuk akses berkas, jaringan, dan protokol lainnya.

#### Kirigami

Kerangka kerja UI adaptif KDE yang memungkinkan aplikasi berjalan baik di desktop maupun mobile.

#### Klassy

Utilitas tema untuk KDE Plasma yang menyediakan kustomisasi mendalam untuk dekorasi jendela, application style, dan ikon.

#### KPackage

Sistem paket KDE untuk menginstal dan mengelola widget, tema, dan ekstensi.

#### KRunner

Peluncur serbaguna yang dapat menjalankan aplikasi, mencari file, menghitung, mengonversi, dan banyak lagi.

#### KWin

Manajer jendela dan kompositor KDE yang menangani manajemen jendela, efek visual, dan kompositing.

#### libplasma

Pustaka inti yang menyediakan fondasi untuk Plasma Shell, mengimplementasikan konsep seperti Corona, Containment, dan Plasmoid.

#### LTS

Long Term Support, rilis dengan dukungan jangka panjang.

#### Material You

Bahasa desain Google yang menghasilkan skema warna dinamis dari wallpaper pengguna.

#### OpenGL

API grafis untuk rendering 2D dan 3D yang digunakan oleh KWin untuk kompositing.

#### PAM

Pluggable Authentication Modules, kerangka kerja untuk autentikasi di Linux.

#### Plasma

Nama untuk shell desktop KDE yang dikembangkan oleh komunitas KDE.

#### Plasma Login Manager (PLM)

Manajer login berbasis QML yang dikembangkan oleh KDE sebagai alternatif SDDM.

#### Plasmoid

Widget Plasma, aplikasi kecil yang hidup di desktop atau panel.

#### Plasma Shell

Proses yang mengelola panel, desktop, dan widget di KDE Plasma.

#### Plasma Style

Paket aset SVG dan konfigurasi yang menentukan tampilan visual elemen Plasma Shell.

#### QML

Qt Modeling Language, bahasa deklaratif untuk UI yang digunakan oleh KDE Plasma.

#### Qt

Kerangka kerja aplikasi lintas platform yang menjadi fondasi KDE Plasma dan aplikasi KDE.

#### QGraphicsScene

Kerangka kerja Qt untuk rendering grafis yang digunakan oleh Plasma 4.

#### SDDM

Simple Desktop Display Manager, display manager default KDE Plasma sebelum PLM.

#### Solid

Pustaka KDE yang menyediakan abstraksi untuk perangkat keras.

#### System Settings

Pusat konfigurasi grafis untuk KDE Plasma.

#### Wayland

Protokol display server modern yang menggantikan X11.

#### X11

Protokol display server tradisional yang telah ada sejak tahun 1984.

#### XWayland

Server X yang berjalan di dalam sesi Wayland untuk kompatibilitas aplikasi X11.

#### XORP

X.Org, implementasi X11 yang paling umum digunakan.

### Bibliografi

Berikut adalah daftar sumber daya yang digunakan dalam penyusunan buku ini. Sumber daya ini mencakup dokumentasi resmi, wiki komunitas, forum, dan sumber online lainnya yang dapat diakses oleh pembaca untuk pendalaman lebih lanjut.

#### Dokumentasi Resmi KDE

**KDE Docs**

[KDE Documentation](https://docs.kde.org/)

Dokumentasi resmi untuk KDE Frameworks, Plasma Workspaces, dan Applications.

**KDE UserBase**

[KDE UserBase Wiki](https://userbase.kde.org/)

Wiki komunitas untuk pengguna KDE dengan tutorial, tips, dan panduan.

**KDE Community Wiki**

[KDE Community Wiki](https://community.kde.org/)

Wiki komunitas dengan panduan untuk berkontribusi dan informasi tentang proyek KDE.

**KDE TechBase**

[KDE TechBase](https://techbase.kde.org/)

Wiki teknis untuk pengembang KDE.

**KDE Develop**

[Develop.KDE.Org](https://develop.kde.org/)

Portal pengembangan modern KDE dengan tutorial dan referensi API.

**KDE Invent**

[KDE Invent](https://invent.kde.org/)

Repositori Git untuk semua proyek KDE.

**KDE Store**

[KDE Store](https://store.kde.org/)

Platform untuk mengunduh tema, widget, dan add-on.

#### Wiki dan Dokumentasi Komunitas

**Arch Wiki**

[Arch Linux Wiki: KDE](https://wiki.archlinux.org/title/KDE)

Dokumentasi lengkap tentang instalasi dan konfigurasi KDE Plasma di Arch Linux.

**Fedora Wiki**

[Fedora KDE](https://fedoraproject.org/kde/)

Halaman resmi Fedora KDE Spin.

**openSUSE Wiki**

[openSUSE KDE](https://en.opensuse.org/Portal:KDE)

Dokumentasi openSUSE untuk KDE Plasma.

**Kubuntu Wiki**

[Kubuntu](https://kubuntu.org/)

Situs resmi Kubuntu.

**KDE UserBase: Plasma**

[Plasma](https://userbase.kde.org/Plasma)

Halaman UserBase tentang KDE Plasma.

#### Forum dan Komunitas

**KDE Discuss**

[KDE Discuss](https://discuss.kde.org/)

Forum diskusi resmi KDE.

**Reddit r/kde**

[Reddit: r/kde](https://www.reddit.com/r/kde/)

Subreddit untuk pengguna KDE.

**KDE Matrix**

[KDE Matrix Rooms](https://go.kde.org/matrix/)

Ruang Matrix untuk diskusi KDE.

**KDE Bugs**

[KDE Bug Tracker](https://bugs.kde.org/)

Pelacak bug resmi KDE.

#### Buku dan Literatur

**Rechsteiner 2022**

Rechsteiner, Jürg. _KDE Plasma Desktop 5.25_. 2022. Panduan rinci untuk penggunaan dan konfigurasi Plasma.

**Corbyn 2023**

Corbyn, Ansel. _Kubuntu Linux: The Complete Guide to KDE Plasma Desktop_. 2023. Panduan lengkap untuk Kubuntu dan KDE Plasma.

#### Sumber Online Lainnya

**KDE Blogs**

[KDE Blogs](https://blogs.kde.org/)

Blog resmi KDE dengan pengumuman rilis dan artikel teknis.

**Planet KDE**

[Planet KDE](https://planet.kde.org/)

Agregator blog dari kontributor KDE.

**KDE Announce**

[KDE Announcements](https://kde.org/announcements/)

Pengumuman resmi rilis KDE.

**KDE.ORG**

[KDE.ORG](https://kde.org/)

Situs web resmi KDE.

#### Spesifikasi dan Standar

**Freedesktop.org**

[Freedesktop.org Specifications](https://www.freedesktop.org/wiki/Specifications/)

Spesifikasi untuk interoperabilitas desktop.

**XDG Base Directory**

[XDG Base Directory Specification](https://specifications.freedesktop.org/basedir-spec/)

Spesifikasi untuk lokasi direktori konfigurasi dan data.

### Lisensi

#### Lisensi Buku Ini

Buku ini dirilis di bawah lisensi Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0). Anda bebas untuk:

* **Berbagi** — menyalin dan mendistribusikan materi dalam media atau format apa pun.
* **Beradaptasi** — me-remix, mengubah, dan membangun di atas materi.

Dengan ketentuan:

* **Atribusi** — Anda harus memberikan kredit yang sesuai, memberikan tautan ke lisensi, dan menunjukkan jika ada perubahan. Anda dapat melakukannya dengan cara yang wajar, tetapi tidak dengan cara yang menunjukkan bahwa pemberi lisensi mendukung Anda atau penggunaan Anda.
* **Berbagi Serupa** — Jika Anda me-remix, mengubah, atau membangun di atas materi, Anda harus mendistribusikan kontribusi Anda di bawah lisensi yang sama dengan aslinya.
* **Tanpa Pembatasan Tambahan** — Anda tidak boleh menerapkan ketentuan hukum atau tindakan teknologi yang secara hukum membatasi orang lain untuk melakukan apa yang diizinkan oleh lisensi.

Teks lengkap lisensi tersedia di [https://creativecommons.org/licenses/by-sa/4.0/.](https://creativecommons.org/licenses/by-sa/4.0/)

#### Lisensi KDE Plasma

KDE Plasma dan komponen-komponennya dilisensikan di bawah berbagai lisensi open source, terutama:

**GNU General Public License (GPL)**

Versi 2 atau 3. Digunakan oleh banyak komponen KDE Plasma dan aplikasi KDE.

**GNU Lesser General Public License (LGPL)**

Versi 2.1 atau 3. Digunakan oleh banyak pustaka KDE Frameworks untuk memungkinkan penggunaan oleh aplikasi proprietary.

**MIT License**

Digunakan oleh beberapa komponen.

**BSD License**

Digunakan oleh beberapa komponen.

#### Merek Dagang

KDE, Plasma, KWin, KDE Frameworks, dan logo KDE adalah merek dagang atau merek dagang terdaftar dari KDE e.V. Penggunaan nama-nama ini dalam buku ini bersifat deskriptif dan tidak menyatakan afiliasi resmi.

### Kolofon

Buku ini disusun dengan LaTeX menggunakan kelas `scrbook` (KOMA-Script). Tipografi menggunakan NewTX (Times-like) untuk teks dan Inconsolata untuk kode. Grafik dibuat dengan TikZ dan PGF. Ukuran buku: A4 (210 mm × 297 mm).

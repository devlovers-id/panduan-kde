# Pendahuluan

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

Secara vertikal, KDE Plasma berada di antara Qt (kerangka kerja aplikasi) dan aplikasi pengguna. Gambar [1.1](pendahuluan.md#4%5F1%5FPendahuluan) menunjukkan posisi ini secara skematis.

| Lapisan           | Komponen                            |
| ----------------- | ----------------------------------- |
| Lapisan pengguna  | Aplikasi KDE & Pihak Ketiga         |
| Shell & workspace | Plasma Shell (`plasmashell`)        |
|                   | KWin (Manajer Jendela & Kompositor) |
| Pustaka           | KDE Frameworks                      |
|                   | Qt 6                                |
| Sistem            | Kernel Linux / FreeBSD              |

_Gambar 1.1: Posisi KDE Plasma dalam tumpukan perangkat lunak. Setiap lapisan bergantung pada lapisan di bawahnya, namun antarmuka di antara lapisan-lapisan ini dirancang agar tetap stabil sehingga komponen dapat dikembangkan secara independen._

Gambar [1.1](pendahuluan.md#4%5F1%5FPendahuluan) menegaskan bahwa KDE Plasma bukanlah monolit. Ia adalah kumpulan lapisan yang saling bergantung melalui antarmuka yang terdefinisi dengan baik. Inilah yang memungkinkan KDE Plasma untuk terus berevolusi dari KDE 4 ke Plasma 5, dan dari Plasma 5 ke Plasma 6, tanpa harus menulis ulang seluruh sistem.

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

Untuk memahami keunikan filosofi KDE Plasma, penting untuk membandingkannya dengan pendekatan lingkungan desktop lain. Tabel [1.1](pendahuluan.md#6%5F1%5FPendahuluan) merangkum perbedaan utama.

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

KDE Plasma bukanlah proyek yang berdiri sendiri. Ia adalah bagian dari ekosistem KDE yang jauh lebih luas, yang mencakup pustaka, aplikasi, distribusi, dan alat integrasi. Gambar [1.2](pendahuluan.md#8%5F1%5FPendahuluan) menunjukkan ekosistem ini secara skematis.

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

Tabel [1.2](pendahuluan.md#an%5Fdesktop%5Fpopuler%5Flainnya%5F%5Fsert) menyajikan perbandingan komprehensif antara KDE Plasma dan lingkungan desktop populer lainnya.

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

Gambar [2.2](pendahuluan.md#2002) menunjukkan struktur dasar Plasma 4. Perhatikan bagaimana konsep ini memisahkan antara apa yang ditampilkan (plasmoid) dan di mana ia ditampilkan (containment). Pemisahan ini adalah inovasi kunci yang memungkinkan fleksibilitas yang tidak mungkin dilakukan di KDE 3.

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

Tabel [3.1](pendahuluan.md#3%5FArsitektur%5Fdan%5FKomponen) merangkum komponen-komponen inti KDE Plasma beserta peran masing-masing.

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

Gambar [3.1](pendahuluan.md#24%5F3%5FArsitektur%5Fdan%5FKomponen) menunjukkan tumpukan perangkat lunak KDE Plasma secara lengkap, dari kernel hingga aplikasi pengguna.

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

Gambar [3.1](pendahuluan.md#24%5F3%5FArsitektur%5Fdan%5FKomponen) mengungkapkan prinsip arsitektur penting: setiap lapisan hanya bergantung pada lapisan di bawahnya, dan antarmuka di antara lapisan-lapisan ini dirancang agar tetap stabil. Prinsip ini memungkinkan KDE Plasma untuk mengganti komponen tanpa harus menulis ulang seluruh sistem—seperti yang terjadi ketika Plasma 5 beralih dari Qt 4 ke Qt 5, dan Plasma 6 beralih dari Qt 5 ke Qt 6.

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

Gambar [3.3](pendahuluan.md#3%5F3%5FKWin%5F%5FManajer%5FJendela%5Fdan%5FKo) menunjukkan arsitektur internal KWin secara skematis.

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

Gambar [3.5](pendahuluan.md#34%5F3%5FArsitektur%5Fdan%5FKomponen) menunjukkan perbandingan arsitektur kedua protokol.

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

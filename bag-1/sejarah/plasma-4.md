# KDE Plasma 4 (2008–2014)

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


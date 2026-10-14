# Filosofi dan Prinsip

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


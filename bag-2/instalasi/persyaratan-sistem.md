# Persyaratan Sistem

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


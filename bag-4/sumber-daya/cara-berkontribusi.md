# Cara Berkontribusi

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


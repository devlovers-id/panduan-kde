# Masalah NVIDIA

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


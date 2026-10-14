# CMakeLists.txt untuk Widget

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


# Widget Kustom

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


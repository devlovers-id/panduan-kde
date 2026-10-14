# Studi Kasus: Membangun Widget dari Nol

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


# Plasma Framework (`libplasma`)

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


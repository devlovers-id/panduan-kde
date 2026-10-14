# Pengembangan Modul Konfigurasi (KCM)

Modul Konfigurasi KDE (KCM) adalah komponen yang memperluas System Settings. KCM memungkinkan pengguna untuk mengonfigurasi berbagai aspek sistem dan aplikasi.

#### 7.7.1 Arsitektur KCM

KCM di Plasma 6 dibangun dengan QML dan Kirigami. Arsitekturnya terdiri dari:

**KPackage**

Wadah untuk UI QML dan resource lainnya.

**ConfigModule**

Kelas C++ yang menyediakan logika konfigurasi.

**QML UI**

Antarmuka pengguna yang dibangun dengan QML dan Kirigami.

**KConfigXT**

Sistem untuk menghasilkan kode konfigurasi dari berkas XML.

```
System Settings Host
        │
        ▼
KCM (KPackage)
        │
        ├── KQuickAddons::ConfigModule
        ├── QML UI (Kirigami)
        └── KConfigXT
        │
        ▼
KConfig / KConfigXT
        │
        ▼
Berkas Konfigurasi (~/.config/*.rc)
```

_Gambar 7.3: Arsitektur modul konfigurasi (KCM) di Plasma 6. KCM bertindak sebagai jembatan antara antarmuka System Settings dan berkas konfigurasi di disk._

#### 7.7.2 Struktur Proyek KCM

```
my-kcm/
├── CMakeLists.txt
├── src/
│   ├── kcm_myconfig.h
│   ├── kcm_myconfig.cpp
│   └── myconfig.kcfg # Skema KConfigXT
└── package/
    ├── metadata.json
    └── contents/
        └── ui/
            └── main.qml
```

#### 7.7.3 Skema KConfigXT

KConfigXT adalah cara KDE untuk mendefinisikan konfigurasi secara deklaratif. Berkas `.kcfg` berisi definisi opsi konfigurasi:

```xml
<?xml version="1.0" encoding="UTF-8"?>

<kcfg xmlns="http://www.kde.org/standards/kcfg/1.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.kde.org/standards/kcfg/1.0
      http://www.kde.org/standards/kcfg/1.0/kcfg.xsd">
    <kcfgfile name="myconfigrc"/>

    <group name="General">
        <entry name="enabled" type="Bool">
            <default>true</default>
            <label>Aktifkan fitur</label>
        </entry>

        <entry name="displayName" type="String">
            <default>Pengguna</default>
            <label>Nama tampilan</label>
        </entry>

        <entry name="refreshInterval" type="Int">
            <default>60</default>
            <min>10</min>
            <max>3600</max>
            <label>Interval refresh (detik)</label>
        </entry>

        <entry name="theme" type="Enum">
            <default>Light</default>
            <choices>
                <choice name="Light"><label>Terang</label></choice>
                <choice name="Dark"><label>Gelap</label></choice>
                <choice name="Auto"><label>Otomatis</label></choice>
            </choices>
            <label>Tema</label>
        </entry>
    </group>
</kcfg>
```

#### 7.7.4 Kelas ConfigModule

```cpp
#pragma once

#include <KQuickConfigModule>

class KcmMyConfig : public KQuickConfigModule
{
    Q_OBJECT
    Q_PROPERTY(bool enabled READ enabled WRITE setEnabled NOTIFY enabledChanged)
    Q_PROPERTY(QString displayName READ displayName WRITE setDisplayName NOTIFY displayNameChanged)
    Q_PROPERTY(int refreshInterval READ refreshInterval WRITE setRefreshInterval NOTIFY refreshIntervalChanged)

public:
    explicit KcmMyConfig(QObject *parent, const KPluginMetaData &data);

    bool enabled() const;
    void setEnabled(bool enabled);

    QString displayName() const;
    void setDisplayName(const QString &name);

    int refreshInterval() const;
    void setRefreshInterval(int interval);

public Q_SLOTS:
    void save() override;
    void load() override;
    void defaults() override;

Q_SIGNALS:
    void enabledChanged();
    void displayNameChanged();
    void refreshIntervalChanged();

private:
    KConfig m_config;
};
```

#### 7.7.5 QML UI untuk KCM

UI untuk KCM dibangun dengan Kirigami:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as QQC
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM
import org.kde.kquickcontrols as KQC

KCM.SimpleKCM {
    id: root

    property alias cfg_enabled: enabledCheck.checked
    property alias cfg_displayName: nameField.text
    property alias cfg_refreshInterval: intervalSpin.value

    Kirigami.FormLayout {
        QQC.CheckBox {
            id: enabledCheck
            text: "Aktifkan fitur"
            Kirigami.FormData.label: "Status:"
        }

        QQC.TextField {
            id: nameField
            placeholderText: "Masukkan nama tampilan"
            Kirigami.FormData.label: "Nama Tampilan:"
        }

        QQC.SpinBox {
            id: intervalSpin
            from: 10
            to: 3600
            stepSize: 10
            editable: true
            Kirigami.FormData.label: "Interval Refresh (detik):"
        }
    }
}
```

#### 7.7.6 metadata.json untuk KCM

```json
{
    "KPackageStructure": "KCM",
    "KPlugin": {
        "Authors": [
            {
                "Email": "author@example.com",
                "Name": "Nama Penulis"
            }
        ],
        "Description": "Modul konfigurasi untuk aplikasi saya",
        "Icon": "preferences-system",
        "Id": "kcm_myconfig",
        "License": "GPL-3.0+",
        "Name": "Konfigurasi Saya",
        "Version": "1.0.0",
        "Website": "https://example.com"
    },
    "X-KDE-System-Settings-Parent-Category": "personalization",
    "X-KDE-Keywords": "config,settings,myapp",
    "X-KDE-Weight": 50
}
```

{% hint style="info" %}
Kunci `X-KDE-System-Settings-Parent-Category` menentukan di kategori mana KCM akan muncul di System Settings. Nilai umum termasuk `personalization`, `hardware`, `network`, `system`, dan `workspace`.
{% endhint %}

#### 7.7.7 Membangun dan Menguji KCM

```bash
# Build
mkdir build && cd build
cmake .. -DCMAKE_INSTALL_PREFIX=$(kf6-config --prefix)
make

# Instalasi
make install

# Test dengan kcmshell6
kcmshell6 kcm_myconfig

# Atau buka System Settings dan cari KCM
systemsettings
```

{% hint style="info" %}
Gunakan `kcmshell6` untuk menguji KCM secara langsung tanpa harus membuka System Settings. Ini mempercepat siklus pengembangan.
{% endhint %}


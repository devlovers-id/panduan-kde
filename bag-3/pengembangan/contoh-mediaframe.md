# Contoh: Widget Mediaframe

Widget mediaframe dari kdeplasma-addons adalah contoh yang baik untuk mempelajari bagaimana widget dengan plugin C++ diimplementasikan. Widget ini menampilkan frame media dengan kontrol pemutaran.

#### 7.6.1 Struktur Widget Mediaframe

```
mediaframe/
├── CMakeLists.txt
├── package/
│   ├── metadata.json
│   └── contents/
│       └── ui/
│           ├── main.qml
│           └── config.qml
└── src/
    ├── mediaframeplugin.h
    ├── mediaframeplugin.cpp
    ├── mediaframe.h
    └── mediaframe.cpp
```

#### 7.6.2 Kelas MediaFrame

Kelas MediaFrame menyediakan fungsi untuk mengontrol pemutaran media:

```cpp
#pragma once

#include <QObject>
#include <QUrl>

class MediaFrame : public QObject
{
    Q_OBJECT
    Q_PROPERTY(QUrl source READ source WRITE setSource NOTIFY sourceChanged)
    Q_PROPERTY(bool playing READ isPlaying NOTIFY playingChanged)
    Q_PROPERTY(qreal position READ position NOTIFY positionChanged)
    Q_PROPERTY(qreal duration READ duration NOTIFY durationChanged)

public:
    explicit MediaFrame(QObject *parent = nullptr);

    QUrl source() const;
    void setSource(const QUrl &source);

    bool isPlaying() const;

    qreal position() const;
    qreal duration() const;

    Q_INVOKABLE void play();
    Q_INVOKABLE void pause();
    Q_INVOKABLE void stop();
    Q_INVOKABLE void seek(qreal position);

Q_SIGNALS:
    void sourceChanged();
    void playingChanged();
    void positionChanged();
    void durationChanged();

private:
    QUrl m_source;
    bool m_playing = false;
    qreal m_position = 0.0;
    qreal m_duration = 0.0;
};
```

#### 7.6.3 QML Widget

QML untuk widget mediaframe menggunakan plugin C++ untuk kontrol media:

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.plasmoid
import org.kde.plasma.core as PlasmaCore
import org.kde.plasma.components as PlasmaComponents
import org.kde.plasma.private.mediaframe 2.0

PlasmoidItem {
    id: root

    property alias source: mediaFrame.source

    MediaFrame {
        id: mediaFrame
    }

    fullRepresentation: Item {
        Layout.minimumWidth: 320
        Layout.minimumHeight: 240

        ColumnLayout {
            anchors.fill: parent

            // Area video
            Item {
                Layout.fillWidth: true
                Layout.fillHeight: true

                VideoOutput {
                    id: videoOutput
                    anchors.fill: parent
                    source: mediaFrame
                }
            }

            // Kontrol
            RowLayout {
                Layout.fillWidth: true

                PlasmaComponents.Button {
                    icon.name: mediaFrame.playing ? "media-playback-pause" : "media-playback-start"
                    onClicked: mediaFrame.playing ? mediaFrame.pause() : mediaFrame.play()
                }

                PlasmaComponents.Slider {
                    Layout.fillWidth: true
                    from: 0
                    to: mediaFrame.duration
                    value: mediaFrame.position
                    onMoved: mediaFrame.seek(value)
                }

                PlasmaComponents.Button {
                    icon.name: "media-playback-stop"
                    onClicked: mediaFrame.stop()
                }
            }
        }
    }
}
```

#### 7.6.4 Pelajaran dari Mediaframe

Widget mediaframe mengajarkan beberapa konsep penting:

1. **Pemisahan UI dan logika:** UI di QML, logika di C++. Ini memudahkan pengembangan dan pemeliharaan.
2. **Properti `Q_PROPERTY`:** Mengekspos properti C++ ke QML dengan notifikasi perubahan.
3. **Method `Q_INVOKABLE`:** Mengekspos method C++ yang dapat dipanggil dari QML.
4. **Signal:** Menggunakan signal untuk komunikasi asinkron antara C++ dan QML.
5. **Integrasi dengan VideoOutput:** Menggunakan Qt Multimedia untuk rendering video.

{% hint style="info" %}
Untuk mempelajari lebih lanjut, clone repositori kdeplasma-addons dan jelajahi widget lain seperti Weather, Notes, dan Color Picker. Setiap widget memberikan contoh pola pengembangan yang berbeda.
{% endhint %}


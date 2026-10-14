# Plugin QML C++

Untuk widget yang memerlukan fungsionalitas tingkat lanjut, plugin QML C++ memungkinkan Anda mengekspos kelas C++ ke QML. Ini berguna untuk:

* Mengakses pustaka sistem atau perangkat keras.
* Melakukan operasi yang membutuhkan performa tinggi.
* Membuat model data yang kompleks.
* Mengintegrasikan dengan API eksternal.

#### 7.5.1 Arsitektur Plugin QML

Plugin QML C++ bertindak sebagai jembatan antara UI QML dan pustaka C++ di bawahnya:

```
Lapisan QML: main.qml, komponen UI
                │
                ▼
Plugin QML C++: QQmlExtensionPlugin, QObject, QAbstractItemModel
                │
                ▼
Pustaka C++: KDE Frameworks, Qt, pustaka sistem
                │
                ▼
Sistem: Kernel, perangkat keras, layanan
```

_Gambar 7.2: Arsitektur plugin QML C++. Plugin bertindak sebagai jembatan antara UI QML dan pustaka C++ di bawahnya._

#### 7.5.2 Membuat Plugin QML Sederhana

Mari kita buat plugin QML sederhana yang mengekspos kelas C++ ke QML.

**Kelas C++**

```cpp
#pragma once

#include <QObject>
#include <QString>

class MyWidgetItem : public QObject
{
    Q_OBJECT
    Q_PROPERTY(QString greeting READ greeting WRITE setGreeting NOTIFY greetingChanged)
    Q_PROPERTY(int counter READ counter NOTIFY counterChanged)

public:
    explicit MyWidgetItem(QObject *parent = nullptr);

    QString greeting() const;
    void setGreeting(const QString &greeting);

    int counter() const;

    Q_INVOKABLE void increment();

Q_SIGNALS:
    void greetingChanged();
    void counterChanged();

private:
    QString m_greeting;
    int m_counter = 0;
};
```

```cpp
#include "mywidgetitem.h"

MyWidgetItem::MyWidgetItem(QObject *parent)
    : QObject(parent)
    , m_greeting(QStringLiteral("Halo, dunia!"))
{
}

QString MyWidgetItem::greeting() const
{
    return m_greeting;
}

void MyWidgetItem::setGreeting(const QString &greeting)
{
    if (m_greeting == greeting) {
        return;
    }

    m_greeting = greeting;
    Q_EMIT greetingChanged();
}

int MyWidgetItem::counter() const
{
    return m_counter;
}

void MyWidgetItem::increment()
{
    ++m_counter;
    Q_EMIT counterChanged();
}
```

**Plugin Kelas**

```cpp
#pragma once

#include <QQmlExtensionPlugin>

class MyWidgetPlugin : public QQmlExtensionPlugin
{
    Q_OBJECT
    Q_PLUGIN_METADATA(IID QQmlExtensionInterface_iid)

public:
    void registerTypes(const char *uri) override;
};
```

```cpp
#include "mywidgetplugin.h"
#include "mywidgetitem.h"

#include <qqml.h>

void MyWidgetPlugin::registerTypes(const char *uri)
{
    // @uri org.kde.plasma.private.mywidget
    qmlRegisterType<MyWidgetItem>(uri, 1, 0, "MyWidgetItem");
}
```

**Penggunaan dalam QML**

Setelah plugin C++ dibuat, Anda dapat menggunakannya dalam QML:

```qml
import QtQuick
import org.kde.plasma.plasmoid
import org.kde.plasma.private.mywidget 1.0

PlasmoidItem {
    id: root

    MyWidgetItem {
        id: myItem
    }

    fullRepresentation: Column {
        spacing: 10

        Text {
            text: myItem.greeting
        }

        Text {
            text: "Counter: " + myItem.counter
        }

        Button {
            text: "Increment"
            onClicked: myItem.increment()
        }
    }
}
```

#### 7.5.3 Build dan Instalasi Plugin

Untuk mengompilasi plugin, tambahkan ke CMakeLists.txt seperti yang ditunjukkan di bagian sebelumnya. Setelah dikompilasi, plugin akan diinstal ke direktori QML yang benar.

{% hint style="info" %}
URI plugin, misalnya `org.kde.plasma.private.mywidget`, harus unik dan mengikuti konvensi namespace. Untuk widget pribadi, gunakan `org.kde.plasma.private.<nama>` untuk menghindari konflik dengan plugin resmi.
{% endhint %}


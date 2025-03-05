# Installing Qt5 on Fedora

To install Qt5 on Fedora, you can follow these steps:

## 1. Update Your System

Before installing any new software, it's a good idea to update your system to ensure you have the latest packages and security updates.

```bash
sudo dnf update
```

## 2. Install Qt5

Fedora provides Qt5 packages in its default repositories. You can install the necessary Qt5 packages using the dnf package manager.

### Install the Base Qt5 Libraries

To install the core Qt5 libraries, run:

```bash
sudo dnf install qt5-qtbase
```

### Install Additional Qt5 Modules (Optional)

Depending on your needs, you might want to install additional Qt5 modules. Some common ones include:

- **Qt5 GUI and Widgets:** `qt5-qtbase-gui`
- **Qt5 Quick (QML):** `qt5-qtdeclarative`
- **Qt5 WebEngine:** `qt5-qtwebengine`
- **Qt5 Multimedia:** `qt5-qtmultimedia`
- **Qt5 SQL:** `qt5-qtsql`
- **Qt5 Network:** `qt5-qtnetwork`

You can install these modules using:

```bash
sudo dnf install qt5-qtbase-gui qt5-qtdeclarative qt5-qtwebengine qt5-qtmultimedia qt5-qtsql qt5-qtnetwork
```

### Install Development Tools (Optional)

If you plan to develop applications using Qt5, you may want to install development tools and libraries:

```bash
sudo dnf install qt5-qtbase-devel qt5-qtdeclarative-devel qt5-qtwebengine-devel qt5-qtmultimedia-devel qt5-qtsql-devel qt5-qtnetwork-devel
```

## 3. Verify the Installation

To verify that Qt5 is installed correctly, you can check the version of `qmake`:

```bash
qmake-qt5 --version
```

This should output the version of Qt5 installed on your system.

## 4. Set Up Environment Variables (Optional)

If you plan to develop Qt applications, you might want to set up some environment variables to make it easier to use Qt tools.

Add the following lines to your `~/.bashrc` or `~/.zshrc` file:

```bash
export QT_DIR=/usr/lib64/qt5
export PATH=$QT_DIR/bin:$PATH
export LD_LIBRARY_PATH=$QT_DIR/lib:$LD_LIBRARY_PATH
```

Then, reload your shell configuration:

```bash
source ~/.bashrc  # or source ~/.zshrc
```

## 5. Install Qt Creator (Optional)

If you prefer using an Integrated Development Environment (IDE) for Qt development, you can install Qt Creator:

```bash
sudo dnf install qt-creator
```

After installation, you can launch Qt Creator from your application menu or by running `qtcreator` in the terminal.

## 6. Install language package   
this will install the lrelease tool along with other Qt Linguist utilities.  
```bash
$ sudo dnf install qt5-linguist
```

## 7 Create a New Qt Widgets Application
* Go to File → New Project.  
* Select Qt Widgets Application.  
* Name it LoginSystem.   
* select "qmake" or "cmake"   
* select "QDialog" as "Base class"  
* give name to "Header file" as "dialog.h" for store declarations (abstractions of function, classes etc )  
* give name to "Source file" as "dialog.cpp"  for store definitions (implementation of function, classes etc )  
* give name to "Form file" as "dialog.cpp" for implementation for only ui(xml later convert to c++ )
* select "Language"  (this for translate application )
* Click Finish.
* click play icon to build and run project on left botton corner of the ui.

open add button to the dialog box    
> Sources/dialog.cpp
```cpp
#include "dialog.h"
#include <QtWidgets>


Dialog::Dialog(QWidget *parent)
    : QDialog(parent)
{
    QHBoxLayout *layout = new QHBoxLayout();
    QPushButton* btn = new QPushButton("Ok");
    btn->setText("Okay");
    // add button to the layout 
    layout->addWidget(btn);

    this-> setLayout(layout);
}

Dialog::~Dialog() {}
```

organice above code with declarations to the "dialog.h" header file   
> Headers/dialog.h
```cpp
#ifndef DIALOG_H
#define DIALOG_H

#include <QDialog>

class QPushButton; // add here
class QHBoxLayout; // add here

class Dialog : public QDialog
{
    Q_OBJECT

public:
    Dialog(QWidget *parent = nullptr);
    ~Dialog();

private:  // add here
    QPushButton *btn;  // add here
    QHBoxLayout *layout; // add here

};
#endif // DIALOG_H
```

> Sources/dialog.cpp   
```cpp
#include "dialog.h"
#include <QtWidgets>


Dialog::Dialog(QWidget *parent)
    : QDialog(parent)
{

    this->setWindowTitle("My Dialog"); // Set dialog window title

    layout = new QHBoxLayout();
    btn = new QPushButton("Okay");

    layout->addWidget(btn); // Add button to layout
    this->setLayout(layout); // Set the layout to the dialog

}

Dialog::~Dialog() {
    delete btn;    // Manually delete the button
    delete layout; // Manually delete the layout
}
```

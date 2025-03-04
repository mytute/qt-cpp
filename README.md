# qt-cpp

1. Install Qt and Qt Creator
```bash
$ sudo dnf install qt5-qtbase qt5-qtbase-devel qt5-qttools qt5-qttools-devel qt-creator
$ sudo dnf install qt6-qtbase qt6-qtbase-devel qt6-qttools
$ sudo dnf install qt6-qtbase qt6-qtbase-devel qt6-qmake cmake
$ sudo dnf install qt6 qt6-devel qt6-qtbase-devel qt6-qtdeclarative-devel qt6-qttools-devel
$ cmake --version # verify version
# expected output   
# QMake version 3.1
# Using Qt version 5.15.2 in /usr/lib64
```

Check c++ compiler version and if not then install it    
```bash
$ g++ --version
$ sudo dnf install gcc-c++   
```

Create a Qt project
```bash
$ qtcreator &
```

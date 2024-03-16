
```
git clone --depth=1 --branch=v6.2.2 https://github.com/qt/qt5.git qt6
cd qt6
perl init-repository -f
mkdir build && cd build
../configure -developer-build
```

```
curl -L https://download.qt.io/archive/qt/6.6/6.6.2/single/qt-everywhere-src-6.6.2.tar.xz -o qt-everywhere-src-6.6.2.tar.xz
tar -xf qt-everywhere-src-6.6.2.tar.xz
cd qt-everywhere-src-6.6.2
mkdir build && cd build
../configure -developer-build
```

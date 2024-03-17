# Build Qt6 Documentation


## Install the Prerequisites

```
sudo apt install gcc build-essential cmake python3 python3-pip ninja-build nodejs bison flex perl gperf libclang-dev libgl-dev libegl-dev libfontconfig1-dev libinput-dev
pip install html5lib
```

## Check the Prerequisites

```
apt list gcc build-essential cmake python3 python3-pip ninja-build nodejs bison flex perl gperf libclang-dev libgl-dev libegl-dev libfontconfig1-dev libinput-dev --installed
pip list | grep html5lib
```

## Download the Qt6 Source

### Clone from the Git Repository

```
git clone --depth=1 --branch=v6.6.0 https://github.com/qt/qt5.git qt-6.6.0
cd qt-6.6.0
perl init-repository -f
```

### Download the Archive

```
export QT6_VER=6.6
export QT6_REL=6.6.0
curl -L https://download.qt.io/archive/qt/$QT6_VER/$QT6_REL/single/qt-everywhere-src-$QT6_REL.tar.xz -o qt-everywhere-src-$QT6_REL.tar.xz
tar -xf qt-everywhere-src-$QT6_REL.tar.xz
mv qt-everywhere-src-$QT6_REL qt-$QT6_REL
```

## Configure, Build, and Install the Qt6 Project with 'html_docs' target

```
cd qt-$QT6_REL
mkdir build-qt && cd build-qt
../configure -prefix ../html/$QT6_REL
cmake --build . --target html_docs
cmake --install .
```

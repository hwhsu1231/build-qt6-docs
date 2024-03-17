# Build Qt6 Documentation

Preview in GitHub Pages:

https://hwhsu1231.github.io/build-qt6-docs/qtdoc/index.html

## Install the Prerequisites

```bash
sudo apt install gcc build-essential cmake python3 ninja-build bison flex perl gperf libclang-dev libgl-dev libegl-dev libfontconfig1-dev libinput-dev
```

```bash
# WARNING: QtWebEngine won't be built. Python3 html5lib is missing.
# WARNING: QtPdf won't be built. Python3 html5lib is missing.
sudo apt install python3-pip
pip install html5lib
```

```bash
# WARNING: QtWebEngine won't be built. Build requires dbus.
sudo apt install libdbus-1-dev
```

```bash
# WARNING: QtWebEngine won't be built. Build requires nss >= 3.26.
sudo apt install libnss3-dev
```

```bash
sudo snap install node --classic --channel=14
```

```bash
# WARNING: No backend for low level audio found.
# https://stackoverflow.com/questions/76191389/qt-configure-warning-no-backend-for-low-level-audio-found
```

#### Solve this Problem

```
CMake Error at /home/runner/work/build-qt6-docs/build-qt6-docs/qt6/qtwebengine/cmake/Gn.cmake:75 (message):
  

  -- GN FAILED

  ERROR at //build/config/linux/pkg_config.gni:104:17: Script returned
  non-zero exit code.

      pkgresult = exec_script(pkg_config_script, args, "value")
                  ^----------

  Current dir:
  /home/runner/work/build-qt6-docs/build-qt6-docs/qt6/build/qtwebengine/src/core/Debug/x86_64/


  Command: /usr/bin/python3
  /home/runner/work/build-qt6-docs/build-qt6-docs/qt6/qtwebengine/src/3rdparty/chromium/build/config/linux/pkg-config.py
  -p /usr/bin/pkg-config libdrm

  Returned 1.

  stderr:



  Package libdrm was not found in the pkg-config search path.

  Perhaps you should add the directory containing `libdrm.pc'

  to the PKG_CONFIG_PATH environment variable

  No package 'libdrm' found

  Could not run pkg-config.



  See //build/config/linux/libdrm/BUILD.gn:18:3: whence it was called.

    pkg_config("libdrm_config") {
    ^----------------------------

  See //ui/gfx/BUILD.gn:611:15: which caused the file to be included.

      deps += [ "//build/config/linux/libdrm" ]
                ^----------------------------

  



  1
```

```bash
# https://stackoverflow.com/questions/48843208/error-while-setting-up-chromium
sudo apt install libpango1.0-dev
sudo apt install libcogl-pango-dev
sudo apt install libjpeg-dev
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

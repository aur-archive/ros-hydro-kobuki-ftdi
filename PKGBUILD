# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - Utilities for flashing and enabling Kobukis USB connection."
url='http://ros.org/wiki/kobuki_ftdi'

pkgname='ros-hydro-kobuki-ftdi'
pkgver='0.5.4'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-catkin
  ros-hydro-ecl-command-line)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  libftdi
  ftdi-eeprom
  libusb-compat)

ros_depends=(ros-hydro-ecl-command-line)
depends=(${ros_depends[@]}
  libftdi
  ftdi-eeprom
  libusb-compat)

_tag=release/hydro/kobuki_ftdi/${pkgver}-${_pkgver_patch}
_dir=kobuki_ftdi
source=("${_dir}"::"git+https://github.com/yujinrobot-release/kobuki_core-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

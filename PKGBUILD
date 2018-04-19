# Script generated with Bloom
pkgdesc="ROS - rqt_py_console is a Python GUI plugin providing an interactive Python console."
url='http://wiki.ros.org/rqt_py_console'

pkgname='ros-lunar-rqt-py-console'
pkgver='0.4.8_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-lunar-catkin'
)

depends=('python2-rospkg'
'ros-lunar-python-qt-binding>=0.2.19'
'ros-lunar-qt-gui'
'ros-lunar-qt-gui-py-common'
'ros-lunar-rospy'
'ros-lunar-rqt-gui'
'ros-lunar-rqt-gui-py'
)

conflicts=()
replaces=()

_dir=rqt_py_console
source=()
md5sums=()

prepare() {
    cp -R $startdir/rqt_py_console $srcdir/rqt_py_console
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}


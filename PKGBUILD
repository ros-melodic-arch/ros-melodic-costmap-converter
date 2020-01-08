# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS : converts costmaps"

pkgname='ros-melodic-costmap-converter'
pkgver='0.0.12'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-melodic-catkin)
makedepends=('cmake' 'ros-build-tools'  'pkg-config' ${ros_makedepends[@]})

ros_depends=(ros-melodic-roscpp 
ros-melodic-costmap-2d
ros-melodic-cv-bridge 
ros-melodic-dynamic-reconfigure
ros-melodic-pluginlib 
ros-melodic-geometry-msgs 
ros-melodic-nav-msgs
ros-melodic-message-generation
ros-melodic-message-runtime
ros-melodic-roscpp
ros-melodic-std-msgs)
depends=(${ros_depends[@]}
  python-rospkg)

# Git version (e.g. for debugging)
_dir=${pkgname}
_tag=${pkgver}
source=("${_dir}"::"git+https://github.com/rst-tu-dortmund/costmap_converter.git#tag=${__tag}")
sha256sums=('SKIP')
options=('!makeflags')  

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 3 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${pkgname} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
        -DPYTHON_EXECUTABLE=/usr/bin/python3 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python3.8 \
        -DPYTHON_LIBRARY=/usr/lib/libpython3.8.so \
        -DPYTHON_BASENAME=-python3.8 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make 
}  

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

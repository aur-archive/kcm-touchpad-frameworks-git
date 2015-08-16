# Maintainer: A Rojas
# Contributor: Alexander Mezin <mezin.alexander@gmail.com>

pkgname=kcm-touchpad-frameworks-git
pkgver=r320.2319d35
pkgrel=1
pkgdesc='KCM, daemon and applet for touchpad'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/playground/utils/kcm-touchpad'
license=('GPL')
depends=('xf86-input-synaptics' 'xcb-util-cursor' 'plasma-framework' 'kcmutils' 'kinit' 'knotifyconfig')
makedepends=('extra-cmake-modules' 'xorg-server-devel' 'git')
conflicts=('kcm-touchpad')
source=('git://anongit.kde.org/kcm-touchpad.git#branch=frameworks')
md5sums=('SKIP')

pkgver() {
  cd kcm-touchpad
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../kcm-touchpad \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}

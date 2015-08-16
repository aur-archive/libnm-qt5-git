# Maintainer: Antonio Rojas <nqn1976 @ gmail.com>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=libnm-qt5-git
pkgver=r624.537dcdf
pkgrel=1
pkgdesc='Qt-only wrapper for NetworkManager DBus API'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/extragear/libs/libnm-qt'
license=('LGPL')
depends=('qt5-base' 'networkmanager')
makedepends=('extra-cmake-modules' 'git')
conflicts=('libnm-qt5')
provides=('libnm-qt5')
source=("git://anongit.kde.org/libnm-qt.git")
sha256sums=('SKIP')

pkgver() {
  cd libnm-qt
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../libnm-qt \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}

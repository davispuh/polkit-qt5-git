# Maintainer: Dāvis Mosāns <davispuh at gmail dot com>

_pkgname=polkit-qt5
pkgname=$_pkgname-git
pkgver=v0.112.0.r2.g3882e11
pkgrel=1
pkgdesc='A library that allows developers to access PolicyKit API with a nice Qt-style API'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/kdesupport/polkit-qt-1'
license=('LGPL')
depends=('polkit' 'qt5-base')
makedepends=('git')
provides=("$_pkgname")
conflicts=("$_pkgname")
source=("$_pkgname::git+git://anongit.kde.org/polkit-qt-1.git")
sha256sums=('SKIP')

pkgver() {
    cd "$srcdir/$_pkgname"
    git describe --long | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
    cd "$srcdir"
    mkdir -p build
}

build() {
    cd "$srcdir/build"
    cmake "$srcdir/$_pkgname" \
      -DCMAKE_BUILD_TYPE=Release \
      -DCMAKE_INSTALL_PREFIX=/usr \
      -DLIB_DESTINATION=/usr/lib
     make
}

package() {
    cd "$srcdir/build"
    make DESTDIR="${pkgdir}" install
}

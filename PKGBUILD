# Maintainer: Jakub Kozisek <nodevel at gmail dot com>

pkgname=krename-svn
pkgver=240
pkgrel=1
pkgdesc="A very powerfull batch file renamer for KDE (development version)."
arch=('i686' 'x86_64')
url="http://www.krename.net/"
license=('GPL')
depends=('kdelibs' 'taglib' 'xdg-utils' 'podofo')
makedepends=('make' 'cmake' 'svn')
optdepends=()
provides=('krename')
conflicts=('krename')

_svnmod="krename"
_svntrunk="https://krename.svn.sourceforge.net/svnroot/krename/trunk"

build() {
cd ${srcdir}

  msg "Getting sources..."
  if [ -d ${_svnmod}/.svn ]; then
    (cd ${_svnmod} && svn up -r ${pkgver})
  else
    svn co ${_svntrunk} --config-dir ./ -r ${pkgver} ${_svnmod}
    cd ${_svnmod}
  fi

    msg "SVN checkout done or server timeout"
    mkdir build
    cd build
    cmake -DCMAKE_INSTALL_PREFIX=$pkgdir$KDEDIR ../
    make
    make install || return 1
}
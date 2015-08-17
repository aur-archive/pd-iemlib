# Maintainer: Em Ludek <ludek.me@gmail.com>
pkgname=pd-iemlib
_pkg=iemlib
pkgver=1.20.1
pkgrel=1
pkgdesc="A collection of Pure Data objects developed at IEM"
arch=('any')
url="http://www.puredata.info"
license=('LGPL2.1')
depends=(pd)
source=("http://puredata.info/downloads/$_pkg/releases/$pkgver/$_pkg-$pkgver.tgz")
md5sums=(659b036f4f212a33a67287ee3426fd68)

build() {
  cd "$srcdir/$_pkg-$pkgver"

  sed -i 's|usr/local|usr|g' Makefile
  sed -i 's|pd-externals|pd/extra|g' Makefile

  sed -i 's|INSTALL_BIN=$(PREFIX)/extra|INSTALL_BIN=$(PREFIX)/extra/iemlib|g' Makefile
  sed -i 's|# include "g_canvas.h"|#include <pd/g_canvas.h>|g' iemlib2/src/dollarg.c iemlib2/src/parentdollarzero.c iemlib2/src/protect_against_open.c

  make
}

package() {
  cd "$srcdir/$_pkg-$pkgver"

  make DESTDIR="$pkgdir/" install
}

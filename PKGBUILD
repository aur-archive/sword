# Maintainer: SanskritFritz (gmail)
# Contributor: Alexander Rødseth
# Contributor: Andrea Scarpino
# Contributor: Stefan Husmann <stefan-husmann@t-online.de>
# Contributor: TripleE <eric1548@yahoo.com>
# Contributor: Dominic Tubach

pkgname=sword
_mainver=1.7
pkgver=$_mainver.3
pkgrel=2
pkgdesc="Library for Bible study programs."
arch=('x86_64' 'i686')
url="http://www.crosswire.org/sword/"
license=('GPL')
depends=('curl' 'clucene' 'swig')
makedepends=('cmake')
backup=('etc/sword.conf')
source=("http://www.crosswire.org/ftpmirror/pub/$pkgname/source/v$_mainver/$pkgname-$pkgver.tar.gz")

prepare() {
  cd "$srcdir/$pkgname-$pkgver"
  sed -i 's/OPTIONS="--without-conf/#OPTIONS="--without-conf/' usrinst.sh
  sed -i 's/OPTIONS="--disable-shared/#OPTIONS="--disable-shared/' usrinst.sh
}

build() {
  cd "$srcdir/$pkgname-$pkgver"

  ./configure --prefix=/usr --libdir=/usr/lib --sysconfdir=/etc
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  make DESTDIR="$pkgdir" install
  mkdir --parents "$pkgdir/etc"
  make DESTDIR="$pkgdir" install_config
}

md5sums=('bd2ffadaa9f92f7b6e657e323e27a028')

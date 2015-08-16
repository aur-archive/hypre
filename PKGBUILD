# Maintainer: Tim Langlois <langlois at cs dot cornell dot edu>
pkgname=hypre
pkgver=2.9.0b
pkgrel=1
pkgdesc="A library for solving large, sparse linear systems on massively parallel computers"
arch=('i686' 'x86_64')
url="http://acts.nersc.gov/hypre"
license=('lgpl')
depends=('gcc-libs' 'gcc-fortran' 'openmpi')
source=(http://computation.llnl.gov/casc/hypre/download/${pkgname}-${pkgver}-babel.tar.gz)
md5sums=('e701cb591762f6a48c5a2ec8931baa4b')

build() {
  cd "$srcdir/hypre-$pkgver-babel/src"

  # disable internal superlu and fei for now, not sure yet how to get it to use external superlu
  ./configure --prefix=/usr --enable-shared --without-superlu --with-extra-incpath=/usr/include/superlu --without-fei
  make
}

package() {
  cd "$srcdir/hypre-$pkgver-babel/src"

  mkdir -p $pkgdir/usr/lib $pkgdir/usr/include

  install -m644 $srcdir/hypre-$pkgver-babel/src/hypre/include/*.h $pkgdir/usr/include
  install -m644 $srcdir/hypre-$pkgver-babel/src/hypre/lib/libHYPRE-$pkgver.so $pkgdir/usr/lib
  ln -s /usr/lib/libHYPRE-$pkgver.so $pkgdir/usr/lib/libHYPRE.so
}


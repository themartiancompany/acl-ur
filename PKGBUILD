# Maintainer: Thomas Bächler <thomas@archlinux.org>

pkgname=acl
pkgver=2.2.51
pkgrel=3
pkgdesc="Access control list utilities, libraries and headers"
arch=('i686' 'x86_64')
url="http://savannah.nongnu.org/projects/acl"
license=('LGPL')
depends=('attr>=2.4.46')
replaces=('xfsacl')
provides=('xfsacl')
conflicts=('xfsacl')
options=('!libtool')
source=("http://download.savannah.gnu.org/releases/$pkgname/$pkgname-$pkgver.src.tar.gz"{,.sig})
sha256sums=('06854521cf5d396801af7e54b9636680edf8064355e51c07657ec7442a185225'
            '10893e2a044905acc88e2d98291e739b7b858b36c836ff66a3532909964067ce')

build() {
  cd "$pkgname-$pkgver"

  export INSTALL_USER=root INSTALL_GROUP=root
  ./configure --prefix=/usr --libdir=/usr/lib --libexecdir=/usr/lib
  make
}

package() {
  make -C "$pkgname-$pkgver" DIST_ROOT="$pkgdir" install install-lib install-dev
}

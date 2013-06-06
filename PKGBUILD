# Maintainer: Thomas Bächler <thomas@archlinux.org>

pkgname=acl
pkgver=2.2.52
pkgrel=1
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
sha256sums=('179074bb0580c06c4b4137be4c5a92a701583277967acdb5546043c7874e0d23'
            'SKIP')

build() {
  cd "$pkgname-$pkgver"

  export INSTALL_USER=root INSTALL_GROUP=root
  ./configure --prefix=/usr --libdir=/usr/lib --libexecdir=/usr/lib
  make
}

package() {
  make -C "$pkgname-$pkgver" DIST_ROOT="$pkgdir" install install-lib install-dev
}

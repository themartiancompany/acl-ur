# Maintainer: Thomas Bächler <thomas@archlinux.org>
pkgname=acl
pkgver=2.2.49
pkgrel=2
pkgdesc="Access control list utilities, libraries and headers"
arch=('i686' 'x86_64')
url="http://savannah.nongnu.org/projects/acl"
license=('LGPL')
depends=('attr>=2.4.41')
replaces=('xfsacl')
provides=('xfsacl')
conflicts=('xfsacl')
options=('!libtool')
source=(http://mirrors.zerg.biz/nongnu/${pkgname}/${pkgname}-${pkgver}.src.tar.gz)
sha256sums=('b9c7f4752e4ef4930a62fa5aa0d7efe1cba2b5a3a2d6ee2b45c0a70c72b7e5d5')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  export INSTALL_USER=root INSTALL_GROUP=root 
  ./configure --prefix=/usr --libdir=/lib --libexecdir=/usr/lib
  make 
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  make DIST_ROOT="${pkgdir}" install install-lib install-dev

  rm ${pkgdir}/lib/libacl.a
  chmod 0755 ${pkgdir}/lib/libacl.so.*.*.*
}

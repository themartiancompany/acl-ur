# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
pkgname=acl
pkgver=2.2.47
pkgrel=2
pkgdesc="Library for filesystem ACL support"
arch=('i686' 'x86_64')
url="http://oss.sgi.com/projects/xfs/"
license=('LGPL')
groups=('base')
depends=('attr>=2.4.41')
replaces=('xfsacl')
provides=('xfsacl')
conflicts=('xfsacl')
options=('!libtool')
source=(ftp://oss.sgi.com/projects/xfs/cmd_tars/acl_${pkgver}-1.tar.gz
        acl-rpath.patch)
md5sums=('a11e4571a54a0b1ae83010d1e68a64c2'
         '1fe58873e384657cac223689482e3a30')

build() {
  cd $srcdir/acl-$pkgver
  patch -Np0 -i $srcdir/acl-rpath.patch
  
  autoconf
  ./configure --prefix=/usr
  make || return 1 
  make prefix=$pkgdir/usr/ install install-lib install-dev

  # tidy up
  cd $pkgdir

  mkdir -v lib
  mv -v usr/lib/libacl.so* lib/
  ln -sv ../../lib/libacl.so.1 usr/lib/libacl.so

  mv -v usr/libexec/libacl.{a,la} usr/lib/
  rm -rf $pkgdir/usr/libexec
}

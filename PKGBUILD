# Maintainer: Julian Sanin <sanin89julian@gmail.com>
# Contributor: Daniel Morandini <danielmorandini@me.com>

pkgname=swift
pkgver=2.3.0
pkgrel=1
arch=('any')
url=https://github.com/openstack/swift
license=('Apache')
#depends=()
makedepends=('python2-setuptools')
source=("${url}/archive/${pkgver}.tar.gz")
md5sums=('SKIP')

prepare() {
  find $pkgname-$pkgver -type f -exec sed -ri 's:^#!/usr/bin/(env )?python$:&2:' '{}' \;
}

build() {
  cd "${pkgname}-${pkgver}/"
  python2 setup.py build
}

package() {
  cd "${pkgname}-${pkgver}/"
  python2 setup.py install --root="${pkgdir}" --optimize=1
  install -d "${pkgdir}/etc/"
  cp -r etc/ "${pkgdir}/etc/${pkgname}/"
  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}


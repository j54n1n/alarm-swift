# Maintainer: Julian Sanin <sanin89julian@gmail.com>
# Contributor: Daniel Morandini <danielmorandini@me.com>

pkgname=swift
pkgver=2.3.0
pkgrel=2
arch=('armv6h' 'armv7h')
url=https://github.com/openstack/swift
license=('Apache')
depends=('python2-pip')
source=("${url}/archive/${pkgver}.tar.gz")
md5sums=('SKIP')

prepare() {
  find "${pkgname}-${pkgver}" -type f -exec \
    sed -ri 's:^#!/usr/bin/(env )?python$:&2:' '{}' \;
}

build() {
  cd "${pkgname}-${pkgver}/"
  python2 setup.py build
}

package() {
  cd "${pkgname}-${pkgver}/"
  python2 setup.py install \
                   --root="${pkgdir}" \
                   --prefix=/usr \
                   --optimize=1 \
                   --skip-build
  python2 -m pip install -r requirements.txt \
                 --upgrade \
                 --root="${pkgdir}" \
                 --install-option='--prefix=/usr' \
                 --install-option='--optimize=1'
  install -d "${pkgdir}/etc/"
  cp -r etc/ "${pkgdir}/etc/${pkgname}/"
  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

pkgname=python-tlslite
pkgver=0.4.1
pkgrel=1
pkgdesc="SSL/TLS support for Python, with numerous options."
arch=('any')
url="http://trevp.net/tlslite/"
license=('custom:public domain')
depends=('python2')
optdepends=(
    'pycrypto: fast ciphers and fast RSA operations'
    'gmpy: fast RSA and SRP operations'
)
source=("https://github.com/downloads/trevp/tlslite/tlslite-$pkgver.tar.gz")
md5sums=('6b220730c34955cf709acf5fb96d3224')

build() {
  cd "${srcdir}/tlslite-${pkgver}"

  python2 setup.py build
}

package() {
  cd "${srcdir}/tlslite-${pkgver}"
  python2 setup.py install --root=${pkgdir}
  
  # Patch to use python2
  find $pkgdir -type f \( -name '*.py' -or -executable \) -exec \
    sed -i -e "s|#![ ]*/usr/bin/python$|#!/usr/bin/python2|" \
           -e "s|#![ ]*/usr/bin/env python$|#!/usr/bin/env python2|" \
    \{\} +
}

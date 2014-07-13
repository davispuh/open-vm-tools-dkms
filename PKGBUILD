# Maintainer: Dāvis Mosāns <davispuh at gmail dot com>

pkgname=open-vm-tools-dkms
epoch=2
pkgver=9.4.6
pkgrel=1770165
pkgdesc='Open Virtual Machine Tools kernel modules (DKMS)'
arch=('i686' 'x86_64')
url='http://open-vm-tools.sourceforge.net/'
license=('GPL2')
conflicts=('open-vm-tools-modules', 'vmware-modules-dkms')

depends=('dkms')
options=('!strip')
optdepends=('open-vm-tools: Open Virtual Machine Tools'
            'linux-headers: Header files for Linux kernel')

_name='open-vm-tools'
_dirname='stable-9.4.x'
_version="${pkgver}-${pkgrel}"
_full_name="${_name}-${_version}"

source=("http://downloads.sourceforge.net/project/open-vm-tools/open-vm-tools/${_dirname}/${_full_name}.tar.gz"
        'open-vm-tools.patch'
        'dkms.conf')
sha256sums=('54d7a83d8115124e4b809098b08d7017ba50828801c2f105cdadbc85a064a079'
            'e7b99cd46235988239f74982f5952a99f7a43a5af811b01aa233e836591b1ed1'
            'cdba1b306dd96a4f30227ff61dfbf810043b2dd1705ff0a9f269bb50a9527555')


build() {
  cd "$srcdir/${_full_name}"
  chmod +x ./modules/linux/dkms.sh
  patch -p1 < "$srcdir/open-vm-tools.patch"
}

package() {
  cd "$srcdir/${_full_name}"
  ./modules/linux/dkms.sh ./ "${pkgdir}/usr/src"
  cp "$srcdir/dkms.conf" "${pkgdir}/usr/src/${_name}-${pkgver}/"
  sed -i -e "s/%pkgver%/${pkgver}/g" "${pkgdir}/usr/src/${_name}-${pkgver}/dkms.conf"
}

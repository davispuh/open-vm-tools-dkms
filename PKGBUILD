# Maintainer: Dāvis Mosāns <davispuh at gmail dot com>

pkgname=open-vm-tools-dkms
pkgver=2013.09.16
pkgrel=1328054
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
_version="${pkgver}-${pkgrel}"

source=("http://downloads.sourceforge.net/project/open-vm-tools/open-vm-tools/Development%20Snapshots/${_name}-${_version}.tar.gz" 'patch.patch')
sha256sums=('470a6ea3ce14c2c5ea6b7bc59745eccbacc8d88a3f343e712312786435975d13'
            '69d68920c1aabc78d036a1f467f4148ce6dd4963f81b775aefb22771372d3838')


build() {
  cd "$srcdir/${_name}-${_version}"
  chmod +x ./modules/linux/dkms.sh
  patch -p1 < "$srcdir/patch.patch"
}

package() {
  cd "$srcdir/${_name}-${_version}"
  ./modules/linux/dkms.sh ./ "${pkgdir}/usr/src"
}

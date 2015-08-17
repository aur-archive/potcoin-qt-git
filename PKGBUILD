# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

#Maintainer silvernode
#Based on dogecoin-qt-git by gee

pkgname=potcoin-qt-git
_gitname=potcoin
_binname=potcoin
proname=bitcoin
pkgver=0.8.6.3
pkgrel=1
pkgdesc="Cryptocurrency"
arch=('x86_64' 'i686')
url="http://potcoin.info/"
license=('MIT')
provides=('potcoin-qt')
depends=('qt4' 'miniupnpc' 'boost-libs')
makedepends=('boost' 'gcc' 'make' 'git')
source=('git+https://github.com/potcoin/potcoin.git'
        'potcoin.desktop')
install=potcoin.install

sha256sums=(SKIP
            'd27528a83a4808935ccf4abfb661c8e4947238e01d8dc458ee1a139254c31215')

## files & commands for building
_qmake=qmake-qt4

pkgver() {
	cd "$srcdir/${_gitname}"
}
    

build() {
	cd ${_gitname}
	
	${_qmake} ${proname}-qt.pro
		
	make ${MAKEFLAGS} || make ${MAKEFLAGS}
}

package() {
	install -Dm644 ${_binname}.desktop ${pkgdir}/usr/share/applications/${_binname}.desktop

	cd ${_gitname}
	install -Dm755 ${_binname}-qt "$pkgdir"/usr/bin/${_binname}-qt
	install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
	install -Dm644 src/qt/res/icons/bitcoin.png "$pkgdir"/usr/share/pixmaps/${_binname}.png
}

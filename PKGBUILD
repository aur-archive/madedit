# Maintainer: codestation <codestation404 at gmail dot com>

pkgname=madedit
pkgver=0.2.9
pkgrel=5
pkgdesc="Open-Source & Cross-Platform Text/Hex Editor written in C++ and wxWidgets."
arch=('i686' 'x86_64')
url="http://madedit.sourceforge.net/"
license=('GPL')
depends=('gtk2>=2.6.0' 'glib2>=2.6.0' 'wxgtk>=2.6.1')
makedepends=('boost>=1.33.0')

source=(http://downloads.sourceforge.net/sourceforge/madedit/$pkgname-$pkgver.tar.gz
	madedit-onpaint-fix.patch
	madedit-add-file-changed-event.patch
	madedit-max-linelength-fix.patch
	madedit-desktop-file.patch
	madedit-highlight-blink-fix.patch
	madedit-remove-bundled.patch)

md5sums=('d5530767a363ca7e9135bd046a227f91'
         '7985f66c07a1e27ee65bc01524274796'
         '661acd7e6c5f3c53177157f681335459'
         '9d9e75d6519c723e5870801d5d43bf37'
         'cdce3aba22e7106a1278a512b7f6a028'
         '5e89e938d1122a5fe299a68fc583edb2'
         '27db628c854ad4e6041cdcde0763ec27')

build() {
        cd "${srcdir}/${pkgname}-${pkgver}"

	patch -p0 < ../madedit-onpaint-fix.patch || return 1
	patch -p0 < ../madedit-add-file-changed-event.patch || return 1
	patch -p0 < ../madedit-max-linelength-fix.patch || return 1
	patch -p0 < ../madedit-desktop-file.patch || return 1
	patch -p0 < ../madedit-highlight-blink-fix.patch || return 1
	patch -p0 < ../madedit-remove-bundled.patch || return 1


	rm -rf xpressive wxAUI
	./autogen.sh
	./configure LIBS=-lX11 --prefix=/usr || return 1
	make || return 1
}

package() {
        cd "${srcdir}/${pkgname}-${pkgver}"
	make DESTDIR="${pkgdir}" install || return 1
}

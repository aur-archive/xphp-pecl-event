# Maintainer: Andrew Rose <hello@andrewrose.co.uk>
# Contributor: Andrew Rose <hello@andrewrose.co.uk>

pkgname=xphp-pecl-event
pkgdesc='Provides interface to libevent library'
pkgver=1.11.1
pkgrel=1

arch=('x86_64' 'i686')
license=('PHP')
url='http://pecl.php.net/package/event'

makedepends=('libevent' 'xphp')
source=("http://pecl.php.net/get/event-${pkgver}.tgz")
md5sums=('cb5f6b99784be213323da6efd0e93080')
depends=('libevent' 'xphp')

peclconfig="--prefix=/opt/xphp \
 --bindir=/opt/xphp/bin \
 --libdir=/opt/xphp/lib \
 --sysconfdir=/etc/xphp \
 --mandir=/opt/xphp/man \
 --with-php-config=/opt/xphp/bin/php-config
"

build() {
	export PATH="/opt/xphp/bin:$PATH"

 	cd ${srcdir}/event-${pkgver} || return 1
 	/opt/xphp/bin/phpize || return 1
	./configure ${peclconfig} || return 1
	make || return 1
}

package_xphp-pecl-event() {

	install -d -m755 ${pkgdir}/opt/xphp/lib/modules/
	cp ${srcdir}/event-${pkgver}/modules/event.so ${pkgdir}/opt/xphp/lib/modules/event.so
	install -D -m 644 $startdir/event.ini ${pkgdir}/etc/xphp/conf.d/event.ini || return 1
}

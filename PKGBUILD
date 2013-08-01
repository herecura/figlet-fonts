# Contributor: Thomas Mudrunka <harvie@@email..cz>
# Maintainer: Thomas Mudrunka <harvie@@email..cz>
# You can also contact me on http://blog.harvie.cz/

pkgname=figlet-fonts
pkgver=1.0
pkgrel=2
pkgdesc="Additional asciiart fonts for figlet"
arch=('any')
license=('GPL')
url="http://www.figlet.org/fontdb.cgi"
depends=(figlet)
optdepends=('jave: create cool ascii-art and figlets')
source=(
	ftp://ftp.figlet.org/pub/figlet/fonts/ours.tar.gz
	ftp://ftp.figlet.org/pub/figlet/fonts/contributed.tar.gz
	ftp://ftp.figlet.org/pub/figlet/fonts/international.tar.gz
	ftp://ftp.figlet.org/pub/figlet/fonts/ms-dos.tar.gz)
md5sums=('ecfc312b626df0d04936200d074d2508'
         '6e2dec4499f7a7fe178522e02e0b6cd1'
         'b2d53f7e251014adcdb4d407c47f90ef'
         '49aa57ab989e8d952be037414b0bbbe4')
package() {
	msg 'Copying figlet fonts...'
	mkdir -p ${pkgdir}/usr/share/figlet/fonts/
	find ${srcdir} | grep -i flf$ | while read font; do
		msg2 "${font##*/}";
		cp -f "$font" ${pkgdir}/usr/share/figlet/fonts/
	done;

	msg 'Removing figlets which are already in official distribution...'
	ls -1 ${srcdir}/ours/ | while read i; do
		rm -rf "$pkgdir/usr/share/figlet/fonts/$i";
	done;

	msg 'Installing figlet-gallery script...'
	mkdir -p ${pkgdir}/usr/bin/
	echo '#!/bin/sh
ls /usr/share/figlet/fonts/*.flf | cut -d . -f 1 | while read i; do echo "$i.flf:"; figlet -t -f "$i" ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz1234567890; done | less
' > ${pkgdir}/usr/bin/figlet-gallery

	chmod -R 755 ${pkgdir}/
}

pkgname=linux-orangepi3
pkgver=5.5
pkgrel=6
pkgdesc="Orange Pi 3 kernel for Arch Linux ARM"
arch=(aarch64)
url="https://xff.cz/kernels/"
install="$pkgname.install"
license=('GPL')
depends=('uboot-tools')
source=("https://xff.cz/kernels/$pkgver/pi3.tar.gz")
md5sums=('SKIP')

prepare() {
	cd "pi3-$pkgver"
	sed -i -e 's/Image.lz4/pi3Image.lz4/g' board-rd.its
	sed -i -e 's/board.dtb/pi3.dtb/g' board-rd.its
	sed -i -e 's/board-rd/pi3-rd/g' update-itb-ramdisk.sh
}

package() {
	cd "pi3-$pkgver"
	install -D -m 755 Image ${pkgdir}/boot/pi3Image
	install -D -m 755 Image.lz4 ${pkgdir}/boot/pi3Image.lz4
	install -D -m 755 board.dtb ${pkgdir}/boot/pi3.dtb
	install -D -m 755 board.its ${pkgdir}/boot/pi3.its
	install -D -m 755 board-rd.its ${pkgdir}/boot/pi3-rd.its
	install -D -m 755 update-itb-ramdisk.sh ${pkgdir}/usr/bin/update-pi3-ramdisk.sh
	mkdir -p ${pkgdir}/usr/lib/modules/
	mkdir -p ${pkgdir}/usr/bin
	chmod +x ${pkgdir}/usr/bin/update-pi3-ramdisk.sh
	cp -r modules/lib/modules/* ${pkgdir}/usr/lib/modules/ 
}

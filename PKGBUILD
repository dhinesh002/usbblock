pkgname=usbblock
pkgver=1.0
pkgrel=1
pkgdesc="Manage USB mass storage blocking via udev"
arch=('any')
license=('MIT')
install=usbblock.install
depends=()
source=("usbblock.sh")
md5sums=('SKIP')

package() {
    install -Dm755 "$srcdir/usbblock.sh" "$pkgdir/usr/bin/usbblock"

    # Only create the file if it doesn't already exist
    install -d "$pkgdir/etc/udev/rules.d"
    touch "$pkgdir/etc/udev/rules.d/90-usb-block.rules"
}

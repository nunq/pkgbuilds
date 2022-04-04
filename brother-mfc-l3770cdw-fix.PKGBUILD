# Contributor: Felix Walter <code at felix dash walter dot eu>
# This uses modified code from package brother-mfc-9335cdw by Leo Pham <regretfulumbrella at gmail dot com>
#
# fixed for personal use by github.com/hyphenc, therefore
# Maintainer: github.com/hyphenc
# the aur pkgbuild was missing the lib32-glibc dependency on x86_64 systems.
# makepkg --printsrcinfo > .SRCINFO && makepkg -si
# sudo systemctl restart org.cups.cupsd.service
# then go to localhost:631 and do the cups setup

pkgname=brother-mfc-l3770cdw-fix
pkgver=1.0.2
pkgrel=0
pkgdesc="LPR and CUPS drivers for the Brother MFC-L3770CDW"
arch=("i686" "x86_64")
url="http://support.brother.com/g/s/id/linux/en/index.html"
license=("custom:brother" "GPL")
depends=("cups" "ghostscript")
depends_x86_64=("lib32-glibc")
conflicts=("brother-mfc-l3770cdw")
makedepends=("perl" "tar")
source=("https://download.brother.com/welcome/dlf103935/mfcl3770cdwpdrv-1.0.2-0.i386.deb")
md5sums=("ec927721bea8a717940a76d09d546e95")

package() {
    ar x mfcl3770cdwpdrv-1.0.2-0.i386.deb && tar xzvf data.tar.gz

    # Patch filenames to work on Arch
    cd opt/brother/Printers/mfcl3770cdw
    perl -i -pe "s#/etc/init.d#/etc/rc.d#g" ./cupswrapper/cupswrappermfcl3770cdw
    perl -i -pe "s#printcap\.local#printcap#g" ./inf/setupPrintcapij

    cp -rf $srcdir/usr/ $pkgdir/
    cp -rf $srcdir/opt/ $pkgdir/
}

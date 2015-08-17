# Maintainer: Vivien Maisonneuve <v dot maisonneuve at gmail dot com>
# Category: devel
pkgname='nvflash-tools'
pkgver='20130922'
pkgrel=2
pkgdesc='NvFlash and Wheelie for Tegra 3-based Android devices'
arch=('i686' 'x86_64')
url='https://www.androidroot.mobi/'
license=('custom')
depends=()
if test "$CARCH" == x86_64; then
    depends+=('lib32-glibc' 'lib32-libstdc++5')
fi
makedepends=('curl' 'tar')
optdepends=('android-tools')

prepare() {
    local base_url="http://download.androidroot.mobi"
    cd "$srcdir"
    curl "$base_url/nvflash-tools-linux.tar.bz2" -Lo 'download.html'
    local url="$base_url/$(sed -n 's/.*window.location.href="\/\(.*\)".*/\1/p' 'download.html')"
    curl -L "$url" -o "nvflash-tools.tar.bz2"
    tar -xjf 'nvflash-tools.tar.bz2'
}

package() {
    cd "$srcdir"
    install -Dm 0755 'nvflash' "$pkgdir/usr/bin/nvflash"
    install -Dm 0755 'wheelie' "$pkgdir/usr/bin/wheelie"
}

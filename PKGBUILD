# Maintainer: Clément Martinez <me at moverest dot xyz>
pkgname=wl-kbptr
pkgver=0.4.0
pkgrel=1
url="https://github.com/moverest/wl-kbptr"
pkgdesc="Control the mouse pointer with the keyboard on Wayland"
arch=('x86_64')
license=('GPL-3.0')
depends=('cairo' 'wayland' 'libxkbcommon' 'opencv' 'pixman')
makedepends=('meson' 'wayland-protocols')
source=("https://github.com/moverest/wl-kbptr/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('e3655f5305987dbac389a25e64c2f5a028c1651db70ea757024c4efa55c24338')

build() {
    arch-meson "$pkgname-$pkgver" build -Dopencv=enabled
    ninja -C build
}

package() {
    DESTDIR="$pkgdir" ninja -C build install
    cd "$pkgname-$pkgver"
    install -Dm 0755 helpers/wl-kbptr-sway-active-win -t "$pkgdir/usr/bin/"
    install -Dm 0644 LICENSE -t "$pkgdir/usr/share/licenses/wl-kbptr/"
    install -Dm 0644 README.md -t "$pkgdir/usr/share/doc/wl-kbptr/"
}

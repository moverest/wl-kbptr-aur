# Maintainer: Clément Martinez <me at moverest dot xyz>
pkgname=wl-kbptr
pkgver=0.2.2
pkgrel=2
url="https://github.com/moverest/wl-kbptr"
pkgdesc="Control the mouse pointer with the keyboard on Wayland"
arch=('x86_64')
license=('GPL-3.0')
depends=('cairo' 'wayland' 'libxkbcommon')
optdepends=('python: to run wl-kbptr-sway-active-win')
makedepends=('meson' 'wayland-protocols')
source=("https://github.com/moverest/wl-kbptr/archive/v$pkgver.tar.gz")
sha256sums=('d37524010f777eed0dd5a482b2b30737d8938bfd936140c666861ca212b25ebb')

build() {
    arch-meson "$pkgname-$pkgver" build
    ninja -C build
}

package() {
    DESTDIR="$pkgdir" ninja -C build install
    cd "$pkgname-$pkgver"
    install -Dm 0755 helpers/wl-kbptr-sway-active-win -t "$pkgdir/usr/bin/"
    install -Dm 0644 LICENSE -t "$pkgdir/usr/share/licenses/wl-kbptr/"
    install -Dm 0644 README.md -t "$pkgdir/usr/share/doc/wl-kbptr/"
}

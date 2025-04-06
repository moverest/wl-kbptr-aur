# Maintainer: Clément Martinez <me at moverest dot xyz>
pkgname=wl-kbptr
pkgver=0.3.0
pkgrel=1
url="https://github.com/moverest/wl-kbptr"
pkgdesc="Control the mouse pointer with the keyboard on Wayland"
arch=('x86_64')
license=('GPL-3.0')
depends=('cairo' 'wayland' 'libxkbcommon' 'opencv' 'pixman')
makedepends=('meson' 'wayland-protocols')
source=("https://github.com/moverest/wl-kbptr/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('69775029acb8ff7d814a2868afe22e72b8c9c99cbb35b0acf57eccd3609b089c')

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

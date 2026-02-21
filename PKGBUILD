# Maintainer: Jakub Jirutka <jakub@jirutka.cz>

pkgname=connman-resolvconf
pkgver=0.2.1
pkgrel=0
pkgdesc="ConnMan integration with resolvconf(8)"
arch=('x86_64')
#url="https://github.com/jirutka/connman-resolvconf"
license=('MIT')
depends=('connman' 'dbus' 'gcc-libs' 'openresolv')
makedepends=('cargo')
source=()
# source=("https://github.com/jirutka/$pkgname/archive/v$pkgver/$pkgname-$pkgver.tar.gz")
#source=(".")
# sha512sums=('66addbf52084ca2c46a13e57d10d9acd2a10e39e166bc910d8910cc44ddaf734aff2f8cbf393eb7e4e26c9733364ced1199384b69a69b79e3491e72f4f327ccc')

prepare() {
  #cd "$pkgname-$pkgver"
  cd ..
  cargo fetch --locked --target "$CARCH-unknown-linux-gnu"
}

build() {
  #cd "$pkgname-$pkgver"
  cd ..
  cargo build --release --locked --offline
}

package() {
  #cd "$pkgname-$pkgver"
  cd ..
  install -Dm755 -t "$pkgdir"/usr/bin target/release/connman-resolvconfd
  install -Dm744 -t "$pkgdir"/etc/runit/sv/connman-resolvconfd contrib/runit/connman-resolvconfd/run
  install -Dm744 -t "$pkgdir"/etc/runit/sv/connman-resolvconfd/log contrib/runit/connman-resolvconfd/log/run
  mkdir -p "$pkgdir"/var/log/connman-resolvconf
  chmod 644 "$pkgdir"/var/log/connman-resolvconf
  install -Dm644 -t "$pkgdir"/usr/share/licenses/$pkgname LICENSE
}

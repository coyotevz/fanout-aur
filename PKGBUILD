# Maintainer: Augusto Roccasalva <augusto@rioplomo.com.ar>

pkgname=fanout
pkgver=r69.289a9ba
pkgrel=1
pkgdesc="A simple fanout pubsub message server"
arch=('i686', 'x86_64')
url="https://github.com/travisghansen/fanout"
license=('MIT')
depends=()
makedepends=('git')
conflicts=()
provides=('fanout')
install=fanout.install

source=("$pkgname"::"git+$url"
        fanout.service
        fanout.conf.d)
sha256sums=('SKIP'
            '4eea1d7ea09daf2d45e2e5cd49aca3ec994a7370b708255627b39bf85688adae'
            'd2159d977eabef18124210e86d62d25869f250389e52edfd071f5778285f5658')

pkgver() {
  cd "$srcdir/$pkgname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "$srcdir/$pkgname"
  make
}

package() {
  cd $srcdir
  install -Dm644 fanout.service "$pkgdir"/usr/lib/systemd/system/fanout.service
  install -Dm644 fanout.conf.d "$pkgdir"/etc/conf.d/fanout
  install -Dm644 $pkgname/LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
  install -dm755 "$pkgdir"/var/log/fanout
  install -Dm755 $pkgname/$pkgname "$pkgdir"/usr/bin/$pkgname
}

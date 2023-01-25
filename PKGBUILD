# Maintainer: Rudra Saraswat <rs2009@ubuntu.com>

pkgname=nearly
pkgver=1.2.9
pkgrel=1
pkgdesc='Utility to toggle immutability for blendOS'
url='https://github.com/blend-os/nearly'
source=("git+https://github.com/blend-os/nearly.git")
sha256sums=('SKIP')
arch=('x86_64')
license=('GPL-3.0-or-later')
makedepends=('go')

build() {
  cd nearly
  export CGO_CPPFLAGS="${CPPFLAGS}"
  export CGO_CFLAGS="${CFLAGS}"
  export CGO_CXXFLAGS="${CXXFLAGS}"
  export CGO_LDFLAGS="${LDFLAGS}"
  export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"
  go build -o nearly main.go
}

check() {
  cd nearly
  go test main.go
}

package() {
  cd nearly
  install -Dm755 nearly "$pkgdir"/usr/bin/nearly
  install -Dm644 nearly.service "$pkgdir"/usr/lib/systemd/system/nearly.service
}

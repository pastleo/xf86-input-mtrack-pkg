_pkgname=xf86-input-mtrack
pkgname="$_pkgname-pastleo-git"
pkgver=0.5.0.r16.g0843fcc
pkgrel=1
pkgdesc="A multitouch X driver using the kernel MT protocol"
arch=('i686' 'x86_64')
url="http://github.com/pastleo/$_pkgname"
license=('GPL')
depends=('mtdev' 'libxss')
makedepends=('git' 'xorg-server-devel' 'xorgproto')
provides=("$_pkgname")
conflicts=("$_pkgname" 'xf86-input-synaptics')
backup=('usr/share/X11/xorg.conf.d/10-mtrack.conf')
options=()
install=xf86-input-mtrack-git.install
source=(
  "$_pkgname"::"git+https://github.com/pastleo/$_pkgname.git"
  10-mtrack.conf
)
md5sums=(
  'SKIP'
  '33fa5c8d025c1685581c383a25439314'
)

pkgver() {
  cd "$srcdir/$_pkgname"
  ( set -o pipefail
    git describe --long --tags | sed -r 's/([^-]*-g)/r\1/;s/-/./g;s/^[^0-9]*//' ||
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  )
}

build() {
  cd "$_pkgname"

  autoreconf --install
  ./configure --prefix=/usr
  make
}

package() {
  cd "$_pkgname"

  make DESTDIR="$pkgdir" install
  install -Dm644 "$srcdir/10-mtrack.conf" "$pkgdir/usr/share/X11/xorg.conf.d/10-mtrack.conf"
}

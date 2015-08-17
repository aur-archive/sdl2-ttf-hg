pkgname=sdl2-ttf-hg
pkgver=234
pkgrel=1
pkgdesc="hg build of sdl2_ttf"
arch=('i686' 'x86_64')
url="http://www.libsdl.org"
license=('MIT')
depends=(sdl2-hg freetype2)
makedepends=(mercurial)
optdepends=()
provides=(sdl2_ttf)
conflicts=(sdl2_ttf)
options=(!libtool)
source=('sdl2_ttf::hg+http://hg.libsdl.org/SDL_ttf')
md5sums=('SKIP')

_hgrepo="sdl2_ttf"

pkgver() {
  cd "${srcdir}/${_hgrepo}"
  hg identify -n
}

prepare() {
  mkdir "${srcdir}/${_hgrepo}/build"
}

build() {
  cd "${srcdir}/${_hgrepo}/"
  ./autogen.sh
  cd "${srcdir}/${_hgrepo}/build"
  ../configure --disable-static --prefix=/usr
  make
}

package() {
  cd "${srcdir}/${_hgrepo}/build"
  make DESTDIR="${pkgdir}/" install
  install -Dm644 ../COPYING.txt "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
## vim:set ts=2 sw=2 et:

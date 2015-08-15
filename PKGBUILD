# Maintainer: pank <rasmus.pank at gmail dot com>
# Contributor: chochem <chochem at gmail dot com>
# Contributor: willemw <willemw at gmail dot com>

pkgname=dradio
pkgver=3.8
pkgrel=5
pkgdesc="A terminal based frontend to MPlayer that collects the available channels/podcasts from Danmarks Radio for convenient browsing."
arch=('i686' 'x86_64')
url="http://thrysoee.dk/dradio/"
license=('GPL')
depends=('expat' 'ncurses' 'mplayer' 'curl' 'libxslt' 'tidyhtml')
# makedepends=('sed' 'wget')
optdepends=('live-media: for H264 streams (i.e. dradio -rtsp-stream-over-tcp).')
source=("http://thrysoee.dk/dradio/dradio-3.8.tar.gz")
md5sums=('2532cee6b77f00c15a484fde4851d722')

# The domain doesn't accept a wget/curl user agent.
DLAGENTS=('http::/usr/bin/wget --quiet --tries=3 --waitretry=3 -U firefox -O %o %u')

prepare() {
  cd "$srcdir/$pkgname-$pkgver"
  sed -i s,ncursesw/menu.h,menu.h,g config.h.in configure configure.ac	src/dradio.h
  for i in src/*.c;do
    sed -i '/types.h/d' $i
  done
}

build() {
  cd "$srcdir/$pkgname-$pkgver"
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
}

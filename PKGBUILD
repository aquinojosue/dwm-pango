# $Id: PKGBUILD 3138 2009-09-28 09:21:30Z spupykin $
# Maintainer: Patrice Peterson <runiq at archlinux dot us>
# Contributor: Sergej Pupykin <pupykin.s+arch at gmail dot com>
# Contributor: Dag Odenhall <dag.odenhall at gmail dot com>
# Contributor: Grigorios Bouzakis <grbzks at gmail dot com>

pkgname=dwm-pango
pkgver=6.0
pkgrel=1
pkgdesc="A dynamic window manager for X - with Pango support"
url="http://dwm.suckless.org"
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxinerama' 'pango')
options=(zipman)
provides=('dwm')
conflicts=('dwm')
install=dwm.install
source=(http://dl.suckless.org/dwm/dwm-$pkgver.tar.gz
        dwm-6.0-pango.patch
        config.h
		tilemovemouse.c
		push.c)

md5sums=('8bb00d4142259beb11e13473b81c0857'
         '9e4e876a6f0ee77034694a223b2ca68a'
         '39fbfaa423ebc40b1ecb92eecf4ea638')

build() {
  cd $srcdir/dwm-$pkgver
  msg "Applying pango patch…"
  patch -Np1 -i ../dwm-6.0-pango.patch || return 1

  cp $srcdir/config.h config.h

  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 || return 1
  make PREFIX=/usr DESTDIR=$pkgdir install || return 1

  install -m644 -D LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE && \
  install -m644 -D README $pkgdir/usr/share/doc/$pkgname/README
}

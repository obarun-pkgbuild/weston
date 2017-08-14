# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://git.archlinux.org/svntogit/community.git/log/trunk?h=packages/weston
# 						Maintainer: Sébastien Luttringer
# 						Contributor: Joel Teichroeb <joel@teichroeb.net>

pkgname=weston
pkgver=3.0.0
pkgrel=1
pkgdesc='Reference implementation of a Wayland compositor'
arch=(x86_64)
url='https://wayland.freedesktop.org/'
license=('MIT')
depends=('glibc' 'wayland' 'libxkbcommon' 'libinput' 'libunwind' 'pixman'
         'libdrm' 'pam' 'cairo' 'libpng' 'libjpeg-turbo' 'libwebp'
         'mesa' 'libegl' 'libgles' 'glib2' 'pango' 'lcms2' 'mtdev' 'libx11'
         'libxcb' 'dbus' 'libva' 'libxcursor' 'colord')
makedepends=('wayland-protocols')
source=("https://wayland.freedesktop.org/releases/$pkgname-$pkgver.tar.xz")
sha1sums=('0a75c2ee10f2453a073411157bb6ed029080669f')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
  cd $pkgname-$pkgver
  ./configure \
    --prefix=/usr \
    --libexecdir=/usr/lib/weston \
    --enable-xwayland \
    --enable-demo-clients-install
  make
}

package() {
  cd $pkgname-$pkgver
  make DESTDIR="$pkgdir" install
  # license
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

# vim:set ts=2 sw=2 et:

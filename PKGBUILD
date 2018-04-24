# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://git.archlinux.org/svntogit/community.git/log/trunk?h=packages/weston
# 						Maintainer: Sébastien Luttringer
# 						Contributor: Joel Teichroeb <joel@teichroeb.net>

pkgname=weston
pkgver=4.0.0
pkgrel=2
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
sha1sums=('df1da4a880920c515162e95b18f3709a46690be7')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
  cd $pkgname-$pkgver
  ./configure \
    --prefix=/usr \
    --libexecdir=/usr/lib/weston \
    --enable-xwayland \
    --enable-demo-clients-install \
    --enable-weston-launch \
    --enable-clients \
    --enable-fbdev-compositor \
    --enable-drm-compositor \
    --enable-x11-compositor \
    --disable-setuid-install \
    --disable-systemd-notify \
    --disable-systemd-login
  make
}

package() {
  cd $pkgname-$pkgver
  make DESTDIR="$pkgdir" install
  # license
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

# vim:set ts=2 sw=2 et:

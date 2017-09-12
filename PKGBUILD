# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://git.archlinux.org/svntogit/packages.git/log/trunk?h=packages/xdg-user-dirs
# 						Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>
# 						Contributor: Stefan Husmann <stefan-husmann@t-online.de>
# 						Contributor:  <mathieu.clabaut@gmail.com>

pkgname=xdg-user-dirs
pkgver=0.16
pkgrel=2
pkgdesc="Manage user directories like ~/Desktop and ~/Music"
arch=(x86_64)
url="http://www.freedesktop.org/wiki/Software/xdg-user-dirs"
license=(GPL)
depends=(sh)
makedepends=(docbook-xsl git)
optdepends=('xdg-user-dirs-s6rcserv: xdg-user-dirs rc service')
backup=(etc/xdg/user-dirs.conf etc/xdg/user-dirs.defaults)
options=(!emptydirs)
_commit=6fb1741bd9a2ccc66507daea2c76da83e1e19222  # tags/0.16^0
source=("git+https://anongit.freedesktop.org/git/xdg/$pkgname#commit=$_commit")
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

pkgver() {
  cd $pkgname
  git describe --tags | sed 's/-/+/g'
}

prepare() {
  cd $pkgname
  NOCONFIGURE=1 ./autogen.sh
}

build() {
  cd $pkgname
  ./configure --prefix=/usr --sysconfdir=/etc
  make
}

package() {
  cd $pkgname
  make DESTDIR="$pkgdir" install 
}

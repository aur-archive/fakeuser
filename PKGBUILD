# Maintainer: Thiago Perrotta <echo dGhpYWdvcGVycm90dGE5NUBnbWFpbC5jb20K | base64 -d >
pkgname=fakeuser
_gitname=$pkgname
pkgver=2013.04.05.g09be1a3
pkgrel=2
pkgdesc="LD_PRELOAD module to create fake users (use with fakeroot)"
arch=('i686' 'x86_64')
url="https://github.com/progandy/$_gitname"
license=('GPL')
makedepends=('git')
source=("git+https://github.com/progandy/$_gitname.git"
  'basedir.patch')
md5sums=('SKIP'
         '412732de77023411951078c4ecd53a6b')

pkgver() {
  cd "$srcdir/$_gitname"
  git log -1 --format="%cd.g%h" --date=short | sed 's/-/./g'
}

prepare() {
  cd "${srcdir}/$_gitname/example-makepkg"
  patch -Np0 <../../basedir.patch
}

build() {
  cd "${srcdir}/$_gitname"
  make
}

package() {
  cd "${srcdir}/$_gitname"
  install -Dm755 fakeadd        "$pkgdir/usr/bin/fakeadd"
  install -Dm755 libfakeuser.so "$pkgdir/usr/lib/libfakeuser.so"

  cd example-makepkg/
  install -Dm755 fakepkg        "$pkgdir/usr/bin/fakepkg"
  install -d "$pkgdir/usr/share/doc/$pkgname"
  install -Dm644 .INSTALL  "$pkgdir/usr/share/doc/$pkgname/.INSTALL"
  install -Dm644 INSTALL   "$pkgdir/usr/share/doc/$pkgname/INSTALL"
  install -Dm644 PKGBUILD  "$pkgdir/usr/share/doc/$pkgname/PKGBUILD"
  install -Dm644 README.md "$pkgdir/usr/share/doc/$pkgname/README.md"
}

# vim:set ts=2 sw=2 et:

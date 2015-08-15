# Contributor: M Rawash <mrawash _stange_curved_character_ gmail D0T com>
# Maintainer: matthiaskrgr <matthiaskrgr _strange_curverd_character_ freedroid D0T org>
pkgname=freedroidrpg-git
pkgver=0.15.981.g8c9c1ca
pkgver(){
    cd freedroidrpg
    git describe --tags | sed -e 's/^freedroid\-//' -e 's/-/./g'
}
pkgrel=1
pkgdesc="A science fiction role playing game which tells the story of a world destroyed by a conflict between robots and their human masters - development version"
url="http://www.freedroid.org"
license=('GPL')
arch=('i686' 'x86_64')
makedepends=('git' 'mesa-libgl' 'gettext')
checkdepends=('xorg-server-xvfb')
depends=('lua' 'sdl_image' 'libgl' 'sdl_mixer' 'sdl_gfx' 'python')
#optdepends=('espeak: used to generate the bot voice samples, actually not needed at build or runtime, thus commented')
optdepends=('mesa: to run the game in opengl mode')
conflicts=('freedroidrpg' 'freedroidrpg-svn')
replaces=('freedroidrpg' 'freedroidrpg-svn')
changelog=changelog
source=("http://buildbot.freedroid.org/logo.png"
        "freedroidrpg.desktop"
        "changelog"
        "freedroidrpg::git://git.code.sf.net/p/freedroid/code")
sha1sums=('4a9b3ffadae7367c0f30025370cb7d27ba38fcc1'
          '463708161658e15aa555de14ef18ea1fcc0a2758'
          'f58ea5490a123d5827f60d74cb06e1066c8bc491'
          'SKIP')

build() {
	msg "Starting compilation..."
	cd "$srcdir"/freedroidrpg

	msg "Running autogen.sh..."
	./autogen.sh
	msg "Running configure..."
	./configure --prefix=/usr
	msg "Compiling..."
	make
}

check() {
	msg "Starting tests..."
	cd "$srcdir"/freedroidrpg

	make check
}

package() {
	cd "$srcdir"/freedroidrpg
	msg "Compiling and installing to pkgdir this time..."
	make install DESTDIR=$pkgdir
	msg "Compiling done."

	install -Dm644 ../../logo.png $pkgdir/usr/share/pixmaps/freedroidrpg.png
	install -Dm644 ../../freedroidrpg.desktop $pkgdir/usr/share/applications/freedroidrpg.desktop
}

## Contributor: Georgij Kondratjev <smpuj@bk.ru>
## Contributor: Ivan Shapovalov <intelfx100@gmail.com>

pkgname=bespin-svn
pkgver=1723
pkgrel=1
pkgdesc="Qt4/KDE4 style"
arch=(i686 x86_64)
url="http://kde-look.org/content/show.php/Bespin?content=63928"
license=('LGPL')
depends=('qt4' 'kdelibs')
optdepends=('kdebase-workspace')
makedepends=('cmake>=2.4' 'automoc4' 'subversion' 'kdebase-workspace')
provides=('bespin')
conflicts=('bespin' 'kdemod4-kstyles')
source=("bespin::svn+http://svn.code.sf.net/p/cloudcity/code")
md5sums=('SKIP')

pkgver() {
	cd bespin
	svnversion
}

build() {
	cd bespin

	cmake -DQT_QMAKE_EXECUTABLE=qmake-qt4 \
	      -DCMAKE_INSTALL_PREFIX="$(kde4-config --prefix)" \
	      -DENABLE_ARGB=ON \
	      -DCMAKE_BUILD_TYPE=Release
	make
}

package() {
	cd bespin

	make DESTDIR="${pkgdir}" install

	install -Dm644 man/bespin.1 "${pkgdir}/usr/share/man/man1/bespin.1"
	install -Dm644 extras/bespin-compl "${pkgdir}/etc/bash_completion.d/bespin"
}
 

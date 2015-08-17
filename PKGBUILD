# Maintainer: Pier Luigi Fiorini <pierluigi.fiorini@gmail.com>

# Based on qt5-qtbase-git from Sergio Correia <sergio.correia@uece.net>

pkgname=qt5-qtbase-for-hawaii-git
pkgver=20121107
pkgrel=1
pkgdesc="Qt 5: qtbase module"
arch=('i686' 'x86_64')
url="https://qt.gitorious.org/qt/qtbase"
license=('LGPL')
depends=('pcre' 'libpng' 'libjpeg' 'dbus-core' 'cups' 'sqlite' 'libxcb' 'xcb-proto' 'xcb-util' 'xcb-util-image' 'xcb-util-keysyms' 'xcb-util-renderutil' 'xcb-util-wm' 'libxext' 'libxrender' 'icu' 'systemd-tools' 'mesa-full-wayland')
provides=('qt5-qtbase-git')
conflicts=('qt5-qtbase-git')
source=()
md5sums=()
makedepends=('git' 'gcc')

_gitroot="git://gitorious.org/qt/qtbase.git"
_gitname=qt5-qtbase

build() {
	if [ ! -d "${_gitname}" ]; then
		git clone --depth 1 ${_gitroot} ${_gitname} && cd ${_gitname}
	else
		cd ${_gitname} && git reset --hard && git pull origin && git clean -dfx
	fi

	msg "GIT checkout done."

	./configure -nomake demos -nomake tests -nomake examples -make libs -release --prefix=/opt/qt5 -opensource --confirm-license \
		-opengl es2
	make
}

package() {
	cd "${_gitname}"

	make INSTALL_ROOT="${pkgdir}" install
}

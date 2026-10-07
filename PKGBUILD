# Maintainer: Your Name <your email>

pkgname=neoldg-git
_pkgname=NeoLDG
pkgver=1.2
pkgrel=2
pkgdesc=''
arch=('x86_64')
url='https://github.com/RiskAndReward1337/NeoLDG'
license=('MIT')
depends=('qt6-serialport')
makedepends=('cmake')
source=(
	"${pkgname}::git+https://github.com/RiskAndReward1337/NeoLDG"
	"socat.patch"
)


sha256sums=('SKIP'
            '6e03ad4cbd640cf560bd8cc93891fa9c5dd188b574bd955ce21e5a37b2ca22ca')


prepare() {
	#patch --directory="$pkgname" --forward --strip=1 --input="${srcdir}/socat.patch"
	#patch -d "${srcdir}/$pkgname" -Np1 -i ../socat.patch
	pwd
	cd "${srcdir}/$pkgname"
	patch -p1 < "$srcdir/socat.patch"
	cat > neoldg.desktop <<-EOF
	[Desktop Entry]
	Name=NeoLDG
	GenericName=Amateur Radio tuner controller
	Comment=Amateur Radio tuner controller
	Exec=NeoLDG
	Terminal=false
	Type=Application
	Categories=Network;HamRadio;
	EOF


}
build() {
	cd "${srcdir}/$pkgname"
	cmake -S . -B build
	cmake --build build -j
}

package() {
	install -Dm755 "${srcdir}/$pkgname/build/${_pkgname}" "{$pkgdir}/usr/bin/${_pkgname}"
	install -Dm644 "${srcdir}/$pkgname/neoldg.desktop" "${pkgdir}/usr/share/applications/neoldg.desktop"
}


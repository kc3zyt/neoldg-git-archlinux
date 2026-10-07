# Maintainer: Your Name <your email>

pkgname=neoldg-git
_pkgname=NeoLDG
pkgver=1.2
pkgrel=1
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


sha256sums=(
	'SKIP'
	'SKIP'
)


prepare() {
	#patch --directory="$pkgname" --forward --strip=1 --input="${srcdir}/socat.patch"
	#patch -d "${srcdir}/$pkgname" -Np1 -i ../socat.patch
	cd "${srcdir}/$pkgname"
	pwd
	patch -p1 < "$srcdir/socat.patch"
}
build() {
	cd "${srcdir}/$pkgname"
	cmake -S . -B build
	cmake --build build -j
}

package() {
	install -Dm755 "${srcdir}/$pkgname/build/${_pkgname}" "{$pkgdir}/usr/bin/${_pkgname}"

}


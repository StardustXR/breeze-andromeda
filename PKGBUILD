pkgname=breeze-andromeda-git
pkgver=5.27.80_r2565.g144ea450
pkgrel=1
arch=($CARCH)
pkgdesc='Artwork, styles and assets for the Breeze-Andromeda visual style for the Plasma Desktop'
url='https://stardustxr.org/'
license=(LGPL)
depends=(frameworkintegration-git kdecoration-git breeze-icons-git kwayland-git hicolor-icon-theme)
makedepends=(git extra-cmake-modules-git kcmutils-git)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
optdepends=('breeze-gtk-git: Breeze widget style for GTK applications'
            'kcmutils-git: for breeze-settings')
groups=(plasma-git)
source=("git+https://github.com/StardustXR/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(PROJECT_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}

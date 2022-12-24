pkgname=fancontrol-gui
pkgver=0.8
pkgrel=1
pkgdesc="GUI for fancontrol and the fancontrol systemd service"
arch=('x86_64')
url="https://github.com/Maldela/Fancontrol-GUI"
license=('GPL2')
depends=('qt5-quickcontrols2' 'qt5-declarative' 'lm_sensors' 'kirigami' 'kdbusaddons' 'knotifications' 'kdeclarative' 'kauth' 'kpackage' 'ki18n' 'kconfig' 'systemd')
makedepends=('git' 'extra-cmake-modules')
source=("https://github.com/Maldela/fancontrol-gui/archive/refs/tags/v$pkgver.tar.gz")
md5sums=('c2d37fcde2d189bf8601a32320f23c32')


build() {
  msg "Starting build..."

  cd "$srcdir/$pkgname-$pkgver"

  cmake . \
        -DCMAKE_INSTALL_PREFIX=/usr \
        -DCMAKE_BUILD_TYPE=Release \
        -DLIB_INSTALL_DIR=lib \
        -DBUILD_TESTING=off \
        -DSTANDARD_CONFIG_FILE=/etc/fancontrol \
        -DSTANDARD_SERVICE_NAME=fancontrol \
        -DBUILD_GUI=on \
        -DBUILD_KCM=on \
        -DBUILD_HELPER=on \
        -DBUILD_PLASMOID=on \
        -DINSTALL_SHARED=on
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir/" install
}

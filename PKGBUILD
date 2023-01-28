# Merged with official ABS purpose PKGBUILD by João, 2021/02/18 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: Antonio Rojas <arojas@archlinux.org>

pkgname=purpose-git
pkgver=5.80.0_r829.gbb853bf
pkgrel=1
pkgdesc="Framework for providing abstractions to get the developer's purposes fulfilled"
arch=($CARCH)
url='https://community.kde.org/Frameworks'
license=(LGPL)
depends=(kaccounts-integration-git kirigami2-git accounts-qml-module)
makedepends=(git extra-cmake-modules-git intltool)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
optdepends=('kdeconnect-git: sharing to smartphone via KDE Connect' 'telegram-desktop: sharing via Telegram'
            'bluedevil-git: sharing via Bluetooth')
groups=(kf5-git)
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
                  cd ${pkgname%-git}
                    _ver="$(grep -m1 'set(KF5\?_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
                      echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
            }
            
build() {
                  cmake -B build -S ${pkgname%-git} \
                      -DCMAKE_INSTALL_LIBEXECDIR=lib \
                          -DBUILD_TESTING=OFF
                            cmake --build build
            }

package() {
                  DESTDIR="$pkgdir" cmake --install build
            }
            
source=("git+https://github.com/KDE/${pkgname%-git}#branch=kf5")

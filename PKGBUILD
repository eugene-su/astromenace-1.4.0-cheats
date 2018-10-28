# Maintainer: Sven-Hendrik Haase <sh@lutzhaase.com>
# Contributor: Arkham <arkham at archlinux dot us>
# Contributor: Ivan Bobrov <ibobrik at gmail dot com>
# Contributor: Black_Mage <vleon1 at gmail dot com>

pkgname=astromenace
pkgver=1.4.0
pkgrel=1
pkgdesc="Hardcore 3D space shooter with spaceship upgrade possibilities"
arch=('x86_64')
url="http://www.viewizard.com/astromenace/index_linux.php"
license=('GPL3')
depends=('sdl2' 'freealut' 'libjpeg' 'libvorbis' 'glu' 'freetype2' 'libxinerama')
makedepends=('cmake' 'mesa')
source=("https://github.com/viewizard/astromenace/archive/v${pkgver}.tar.gz"
        "cheat.diff")
sha512sums=('274fe6b9e75e0886907a3bb43e210b8327d9d6c8e54c8594bbdfd04d61a2377cfb9bdabf87034e3c17ccff493b9a897859d7ce80b734f584e221ece03f69bfac'
            '120d774e9086b9ae6ca5ea4f1b1e8c7e556fd54e9a0abb37cf6c3646034e51e055b0218e38d19817203b861182446c55f7e4cfecff31396a38aae45bd2ce53b7')

prepare() {
  patch --binary -p1 -i "${srcdir}/cheat.diff"
}
  
build() {
    cd astromenace-$pkgver

    [[ -d build ]] && rm -r build
    mkdir build && cd build
    cmake .. \
        -DCMAKE_INSTALL_PREFIX=/usr \
        -DDATADIR=/usr/share/astromenace
    make
}

package() {
    cd astromenace-$pkgver

    install -Dm755 build/astromenace $pkgdir/usr/bin/astromenace
    install -Dm644 build/gamedata.vfs $pkgdir/usr/share/astromenace/gamedata.vfs
    install -Dm644 share/astromenace_128.png $pkgdir/usr/share/pixmaps/astromenace.png
    install -Dm644 share/astromenace.desktop $pkgdir/usr/share/applications/astromenace.desktop
    install -Dm644 share/astromenace.appdata.xml $pkgdir/usr/share/appdata/astromenace.appdata.xml
}

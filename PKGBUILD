# Maintainer: Ethan Wu <ethanwu10 at gmail dot com>
_pkgname=webots
pkgname=${_pkgname}-bin
_pkgver=R2020a-rev1
pkgver=${_pkgver//-/_}
pkgrel=1
pkgdesc="Mobile robot simulation software"
arch=("x86_64")
url="https://cyberbotics.com/"
license=("Apache")
depends=("make" "gcc" "atk" "ffmpeg" "dbus" "freeimage>=3.15.4" "glib2" "glu"
         "gtk3" "nss" "gcc-libs" "libxaw" "libxrandr" "libxrender"
         "zziplib>=0.13.62" "libssh" "libzip" "xorg-server" "libxslt" "gd"
         "freetype2")
provides=(${_pkgname})
conflicts=(${_pkgname})
options=(!strip)
source=("https://github.com/cyberbotics/webots/releases/download/${_pkgver}/webots_${_pkgver/R/}_amd64.deb"
        "webots.desktop")
noextract=("webots_${_pkgver/R/}_amd64.deb")
sha256sums=('b7f59b00edcf342f4f778a508dfce2be9b1d51c7424222982f788391f580b9f9'
            'f5c7b0b8efb778f9e57cc25508c0fc07cae8544033824e495b582cffc2088632')

prepare() {
    ar p "webots_${_pkgver/R/}_amd64.deb" data.tar.gz | tar -xz
}

package() {
    install -dm755 "${pkgdir}/usr/share/"
    cp -a \
        "${srcdir}/usr/share/"{application-registry,mime-info,pixmaps} \
        "${pkgdir}/usr/share/"
    install -Dm755 \
        "${srcdir}/webots.desktop" \
        "${pkgdir}/usr/share/applications/webots.desktop"

    install -dm755 "${pkgdir}/opt/"
    cp -a "${srcdir}/usr/local/webots" "${pkgdir}/opt/"

    install -dm755 "${pkgdir}/usr/bin"
    ln -s "/opt/webots/webots" "${pkgdir}/usr/bin/webots"
}

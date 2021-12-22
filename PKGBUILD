pkgname='DOOM_BFA'
pkgver='1.2.8'
pkgrel=1
pkgdesc='DOOM 3 BFG Edition Open source port for Arch with Classic DOOM mod support'
url="https://github.com/MadDeCoDeR/Classic-RBDOOM-3-BFG"
arch=("x86_64")
groups=()
depends=("gcc-libs" "zlib" "glew" "libpng" "libjpeg" "rapidjson" "ffmpeg" "sdl2" "openal")
makedepends=("git" "gcc" "make" "cmake")
license=("GPLv3")
source=('BFA::git+https://github.com/MadDeCoDeR/Classic-RBDOOM-3-BFG#branch=master')
md5sums=('SKIP')

build() {
    rm -rf "${srcdir}/build"
    mkdir -p "${srcdir}/build"
    cd "${srcdir}/build"
    cmake -G "Unix Makefiles" -DCMAKE_BUILD_TYPE=Retail -DSDL2=ON ../BFA/neo -DMAKE_DLL=OFF -DUSE_SYSTEM_ZLIB=ON -DUSE_SYSTEM_LIBPNG=ON -DUSE_SYSTEM_LIBJPEG=ON -DUSE_SYSTEM_RAPIDJSON=ON -DUSE_SYSTEM_LIBGLEW=ON -DPACKAGED=ON
    make DoomBFA
}

package() {
    mkdir -p "${pkgdir}/usr/bin"
    cp "${srcdir}/build/DoomBFA" "${pkgdir}/usr/bin/DoomBFA"
    mkdir -p "${pkgdir}/usr/share/pixmaps"
    cp "${srcdir}/assets/doom.png" "${pkgdir}/usr/share/pixmaps/doomBFA.png"
    mkdir -p "${pkgdir}/usr/share/applications"
    cp "${srcdir}/BFA/DOOMBFA.desktop" "${pkgdir}/usr/share/applications/DOOMBFA.desktop"
    mkdir -p "${pkgdir}/usr/share/games/doombfa"
    cp -R "${srcdir}/assets/base" "${pkgdir}/usr/share/games/doombfa"
}

# Maintainer: Luiz Silva <luizsv.dev@gmail.com>
pkgname=devin-desktop
pkgver=3.2.19
pkgrel=1
pkgdesc="A team of agents for every engineer — Devin Desktop"
arch=('x86_64')
url="https://devin.ai/desktop"
license=('LicenseRef-Devin Desktop')
depends=(
    'glibc>=2.28'
    'gcc-libs'
    'gtk3'
    'nss'
    'mesa'
    'alsa-lib'
    'libsecret'
    'libxss'
    'libxtst'
    'xdg-utils'
    'libxkbcommon'
    'dbus'
    'expat'
    'libcups'
    'util-linux-libs'
    'libxkbfile'
    'libxrandr'
)
optdepends=(
    'libnotify: Desktop notifications'
    'org.freedesktop.secrets: Keyring support'
    'libdbusmenu-glib: KDE global menu'
    'gtk2: GTK2 theme support'
    'gvfs: Trash functionality'
    'libvulkan: Vulkan support'
)
options=('!strip')
conflicts=('devin-desktop-bin' 'windsurf-bin' 'windsurf')
install=devin-desktop.install

# To update: curl -s https://windsurf-stable.codeium.com/api/update/linux-x64-deb/stable/latest | jq -r '.url,.sha256hash'
_url="https://windsurf-stable.codeiumdata.com/linux-x64-deb/stable/a64a20ba710cc71acfc6705deec6595478acc79e/Devin-linux-x64-${pkgver}.deb"
source=("devin-desktop-${pkgver}.deb::$_url")
sha256sums=('c900b01985cf504f95fa576f0b5b7476c49bdece449202526c1a5c29816f1525')

package() {
    cd "$srcdir"
    ar x "devin-desktop-${pkgver}.deb"
    tar -xJf data.tar.xz -C "$pkgdir"

    # The deb postinst creates this symlink; we handle it here for pacman
    install -dm755 "$pkgdir/usr/bin"
    ln -sf "/usr/share/devin-desktop/bin/devin-desktop" "$pkgdir/usr/bin/devin-desktop"
}

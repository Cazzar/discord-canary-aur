# Maintainer: Cayde Dixon <me@cazzar.net>
# Contributor: Anthony Anderson <aantony4122@gmail.com>

pkgname=discord-canary
pkgver=0.0.11
pkgrel=1
pkgdesc='Discord Canary linux release'
arch=('x86_64')
url='https://discordapp.com/'
provides=('discord-canary')
license=('custom')
depends=('gtk2' 'gconf' 'libnotify' 'libxss' 'glibc' 'alsa-lib' 'nspr' 'nss' 'libc++')
optdepends=('freetype2-infinality: If you have black screens with emojis install this.' 'libpulse: For pulseaudio support' )

install="DiscordCanary.install"
source=(DiscordCanary.desktop LICENSE DiscordCanary.sh)
source_x86_64=("https://dl-canary.discordapp.net/apps/linux/${pkgver}/discord-canary-${pkgver}.tar.gz") #This is always latest build, right now I do not know of a version param.
sha256sums=('e554dbc5d8b4e6753e9a921336508d051af575c2d77b96be9e3f72a5f4ca837a'
            '688f418cd32a682c6d331c211fedd48ff86ee8ba5a7640f589eadb32996af80f'
            '912cb31b21023980614437b859bb11f39697108c0e9ca21778f81da8065a0815')
sha256sums_x86_64=('2878d34c76b0d2ddbf5b60f72eb46db30a766d84a6b3ded1ba256f12ea1e65d2')

package() {
  # Install the main files.
  install -d "${pkgdir}/opt/${pkgname}"
  cp -a "${srcdir}/DiscordCanary/." "${pkgdir}/opt/${pkgname}"

  # Exec bit
  chmod 755 "${pkgdir}/opt/${pkgname}/DiscordCanary"


  # Desktop Entry
  install -d "${pkgdir}/usr/share/applications"
  install "${srcdir}/DiscordCanary.desktop" "${pkgdir}/usr/share/applications"

  # Main binary
  install -d "${pkgdir}/usr/bin"
  #ln -s "/opt/${pkgname}/DiscordCanary" "${pkgdir}/usr/bin/DiscordCanary"
  #installing from .sh due to how the tar extracts.
  install "${srcdir}/DiscordCanary.sh" "${pkgdir}/usr/bin/discord-canary"

  # Create symbolic link to the icon
  install -d "${pkgdir}/usr/share/pixmaps"
  ln -s "/opt/${pkgname}/discord.png" "${pkgdir}/usr/share/pixmaps/${pkgname}.png"

  # License
  install -Dm644 "${srcdir}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

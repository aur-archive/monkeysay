# Maintainer: D.R. <dr.dev.pub@gmail.com>

pkgname=monkeysay
pkgver=1.0
pkgrel=2
pkgdesc="A monkey gives some quotes."
arch=('any')
url="http://bitbucket.org/drbb/monkeysay"
license=('custom:WTFPL')
groups=()
depends=('bash' 'sed' 'coreutils' 'util-linux')
makedepends=('mercurial' 'sed')
optdepends=('cowsay')
provides=('monkeysay')
conflicts=()
replaces=()
backup=()
options=()
install=
source=()
noextract=()
md5sums=() #generate with 'makepkg -g'

_hgroot="https://bitbucket.org/drbb"
_hgrepo="monkeysay"

build() {
  cd "$srcdir"
  msg "Connecting to Mercurial server...."

  if [[ -d "$_hgrepo" ]]; then
    cd "$_hgrepo"
    hg pull -u
    msg "The local files are updated."
  else
    hg clone "$_hgroot" "$_hgrepo"
  fi

  msg "Mercurial checkout done or server timeout"
  msg "Starting build..."

  msg "There's nothing to build"
}

package() {
  cd "$pkgdir"
  mkdir -p usr/bin usr/share/monkeysay usr/share/licenses/monkeysay
  cd "$srcdir/$_hgrepo"
  cp monkeysay.sh "$pkgdir/usr/bin/monkeysay"
  cp monkeyquotes.txt monkey.cow "$pkgdir/usr/share/monkeysay"
  # Replace $PREFIX in monkeysay with the one chosen here
  sed -i -e 's|PREFIX=.*|PREFIX='/usr'|g' "$pkgdir/usr/bin/monkeysay"
  cp COPYING "$pkgdir/usr/share/licenses/monkeysay/LICENSE"

  cat <<EOF

    +----------------------------------------------------------+
    |  If you like to receive a monkeyquote as soon as you     |
    |  log in, add this line to your ~/.bashrc                 |
    |                                                          |
    |    monkeysay                                             |
    |                                                          |
    |  Optionally if cowsay was detected you can try:          |
    |                                                          |
    |    monkeysay -c                                          |
    +----------------------------------------------------------+

EOF

}

# vim:set ts=2 sw=2 et:

# Maintainer: Your Name <milomord@gmail.com>
pkgname=gonehome-hib
pkgver=1.1
pkgrel=2
pkgdesc="Award winning interactive exploration simulator. Interrogate every detail of a seemingly ordinary house in order to discover its inhabittants' story. Humble Bundle version."
arch=('i686' 'x86_64')
url="http://www.gonehomegame.com/"
license=('custom: commercial')
depends=()
changelog=
source=('hib://GoneHome_v1.1.tar.gz' logo.png::'https://humblebundle-a.akamaihd.net/misc/files/hashed/3d4341588fc58d4b2df697217b1cf03609d2dd02.png' 'gonehome-hib.desktop')
md5sums=('756385355420bbcfd56525ae1088f095'
         'c05d6eff830ded0cc9110eb192577e9a'
         'e0fa1a0bfdf741e25fe7d46a820b915c')
PKGEXT='.pkg.tar'

package() {
	cd "$srcdir"

  install -d "$pkgdir/opt/GoneHome"

  mv * $pkgdir/opt/GoneHome
  chmod -R 655 $pkgdir/opt/GoneHome/GoneHome_Data

  if [ $CARCH == i686 ]; then
    rm "$pkgdir/opt/GoneHome/GoneHome.x86_64"
    rm -r "$pkgdir/opt/GoneHome/GoneHome_Data/Mono/x86_64"
    mv $pkgdir/opt/GoneHome/{GoneHome.x86,GoneHome}
  elif [ $CARCH == x86_64  ]; then
    rm "$pkgdir/opt/GoneHome/GoneHome.x86"
    rm -r "$pkgdir/opt/GoneHome/GoneHome_Data/Mono/x86"
    mv $pkgdir/opt/GoneHome/{GoneHome.x86_64,GoneHome}
  fi

  install -d "$pkgdir/usr/bin"
  ln -s "/opt/GoneHome/GoneHome" "$pkgdir/usr/bin/gonehome"

  cd ..

  install -d "$pkgdir/usr/share/pixmaps"
  mv logo.png $pkgdir/usr/share/pixmaps/gonehome.png

  install -Dm644 "$pkgname.desktop" "$pkgdir/usr/share/applications/$pkgname.desktop"
}

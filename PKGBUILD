# Maintainer: Bitals <me at bitals dot xyz>
# Contributor: Matthijs Tadema <M dot J dot Tadema at gmail dot com>
# Contributor: Lorenzo Gaifas <brisvag at gmail dot com>
# Contributor: Antony Lee <anntzer dot lee at gmail dot com>
pkgname=snapgene-viewer
pkgver=7.1.1
_pkgver_major=$(cut -d '.' -f 1 <<<"$pkgver")
_pkgver_major_middle=$(cut -d '.' -f 1-2 <<<"$pkgver")
pkgrel=1
pkgdesc='Software for plasmid mapping, primer design, and restriction site analysis (freeware edition)'
arch=('x86_64')
url='http://www.snapgene.com/products/snapgene-viewer/'
license=('custom')
# A valid licence is required to use the full version of snapgene
source=("https://cdn.snapgene.com/downloads/SnapGeneViewer/"$_pkgver_major".x/"$_pkgver_major_middle"/"$pkgver"/snapgene_viewer_"$pkgver"_linux.rpm" "snapgene-viewer")
sha512sums=('c39ed1e5d5f1960b2d052faa086c898a56a6541982649870a0afdd122c49264e1c957a94fa6bbea9704f3c2f42536250a5d27f9485ae59addd4468c30b9951a8' '521c2804514c25768df142aae58f94847c52e0d1f6008eae902b591b6d7988a4b11fece1e7192e7f8ee31652315cb4413e530231276a983a626f083fe0442690')

package() {
  cd "$pkgdir"
  cp -r "$srcdir/opt" "$pkgdir"
  cp -r "$srcdir/usr" "$pkgdir"
  mkdir "$pkgdir/usr/bin"
  cp "$srcdir/snapgene-viewer" "$pkgdir/usr/bin/"

  sed -i 's`${INSTALLED_DIR}/snapgene-viewer "$@"`QT_QPA_PLATFORM="xcb" ${INSTALLED_DIR}/snapgene-viewer "$@"`' "$pkgdir/opt/gslbiotech/snapgene-viewer/snapgene-viewer.sh"
    
  chmod a+x "$pkgdir/usr/bin/snapgene-viewer"

  mkdir -p "$pkgdir/usr/share/licenses/$pkgname"
  ln -s "/opt/gslbiotech/snapgene-viewer/resources/licenseAgreement.html" "$pkgdir/usr/share/licenses/$pkgname/LICENSE.html"
  cd "${pkgdir}"
  rm -rf usr/lib
}

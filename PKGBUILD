# Maintainer: Ettore Chimenti <ek5.chimenti at gmail dot com>
# Contributor: Andrea Scarpino <andrea@archlinux.org>
pkgname=u-boot
pkgver=2013.10
pkgrel=1
pkgdesc='Utilities for working with Das U-Boot'
arch=('i686' 'x86_64')
url="http://www.denx.de/wiki/U-Boot/WebHome"
license=('GPL2')
backup=('etc/fw_env.config')
source=("ftp://ftp.denx.de/pub/${pkgname}/${pkgname}-${pkgver}.tar.bz2")
md5sums=('a076a044b64371edc52f7e562b13f6b2')

build(){
  cd ${srcdir}/${pkgname}-${pkgver}

  make imx31_phycore_config CROSS_COMPILE="" 

  make tools-all HOSTCC="gcc" HOSTSTRIP=/bin/true CROSS_COMPILE=""  
  make env CC="gcc" CROSS_COMPILE="" 
}

package() {
  cd ${srcdir}/${pkgname}-${pkgver}

  install -d ${pkgdir}/usr/bin
  install -m755 tools/mkimage ${pkgdir}/usr/bin/
  install -m755 tools/env/fw_printenv ${pkgdir}/usr/bin/
  ln -sf /usr/bin/fw_printenv ${pkgdir}/usr/bin/fw_setenv

  install -d ${pkgdir}/etc
  install -m644 tools/env/fw_env.config ${pkgdir}/etc/
}

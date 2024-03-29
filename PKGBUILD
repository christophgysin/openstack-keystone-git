# Maintainer: Anthony Cornehl <accornehl@gmail.com>
# https://github.com/twinshadow/openstack-aur

_realpkgname="keystone"
pkgname="openstack-${_realpkgname}-git"
pkgdesc="OpenStack identity service"
pkgver=2014.1.rc1.251.gf928249
pkgrel=1
conflicts=("openstack-${_realpkgname}", "${_realpkgname}")
provides=("openstack-${_realpkgname}")
arch=("any")
license=("custom")
url="https://github.com/openstack/${_realpkgname}"
depends=("python2"
    "python2-babel"
    "python2-dogpile-cache-git"
    "python2-eventlet"
    "python2-greenlet"
    "python2-httplib2"
    "python2-keystoneclient-git"
    "python2-lxml"
    "python2-migrate"
    "python2-netaddr"
    "python2-oslo-config-git"
    "python2-pam"
    "python2-passlib"
    "python2-paste"
    "python2-paste-deploy"
    "python2-pbr"
    "python2-prettytable"
    "python2-routes"
    "python2-simplejson"
    "python2-sqlalchemy"
    "python2-webob"
)
makedepends=(
    "python2-setuptools"
    "git"
)
source=("$pkgname"::"git+https://github.com/openstack/${_realpkgname}")
md5sums=("SKIP")

pkgver() {
  cd "$pkgname"
  local ver="$(git describe --long)"
  printf "%s" "${ver//-/.}"
}

build() {
  cd "$pkgname"
  python2 setup.py build
}

package() {
  cd "$pkgname"
  python2 setup.py install --root="$pkgdir" --optimize=1

  install -dm600 "$pkgdir/etc/${_realpkgname}"
  install -Dm600 etc/* "$pkgdir/etc/${_realpkgname}/"
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/${_realpkgname}/LICENSE"
}

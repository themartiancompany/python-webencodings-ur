# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Jelle van der Waa <jelle@vdwaa.nl>
# Contributor: Jelle van der Waa <jelle@vdwaa.nl>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=webencodings
_Pkg="python-${_pkg}"
pkgname="${_py}-${_pkg}"
pkgver=0.5.1
pkgrel=11
arch=(
  'any'
)
_http="https://github.com"
_ns="gsnedders"
url="${_http}/${_ns}/${_Pkg}"
license=(
  'BSD'
)
_pkgdesc=(
  "This is a Python implementation"
  "of the WHATWG Encoding standard."
)
pkgdesc="${_pkgdesc[*]}"
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
)
makedepends=(
  "${_py}"
  "${_py}-setuptools"
)
checkdepends=(
  "${_py}-pytest"
)
source=(
  "${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz"
)
sha256sums=(
  '082367f568a7812aa5f6922ffe3d9d027cd83829dc32bcaac4c874eeed618000'
)

package_python-webencodings() {
  cd \
    "${pkgbase}-${pkgver}"
  "${_py}" \
    setup.py \
      install \
      --root="${pkgdir}"
  install \
    -Dm644 \
    "LICENSE" \
    "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

check() {
  cd \
    "${pkgbase}-${pkgver}/webencodings"
  pytest \
    "tests.py"
}

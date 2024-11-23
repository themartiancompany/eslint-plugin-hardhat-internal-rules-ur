# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Pellegrino Prevete <pellegrinoprevete@gmail.com>
# Maintainer: Truocolo <truocolo@aol.com>
# Contributor: Filipe Bertelli <filipebertelli@tutanota.com>

_offline='false'
_source='ur'
_ns="NomicFoundation"
_pub="nomicfoundation"
_os="$( \
  uname \
    -o)"
_arch="$( \
  uname \
    -m)"
if [[ "${_os}" == "Android" ]]; then
  _source="ur"
  if [[ "${_arch}" == "armv7l" ]]; then
    _platform="android-arm-eabi"
  fi
fi
_node="nodejs"
_pkg=eslint-plugin-hardhat-internal-rules
_pkgbase="${_pkg}"
pkgname="${_pkgbase}"
_pkgdesc=(
  'Internal linting rules used in the'
  'Hardhat repository.'
)
pkgdesc="${_pkgdesc[*]}"
_pkgver="1.0.2"
pkgver="${_pkgver}"
_commit="0f12bd0fa373dbc811ebf7164b4bfeb1f221a4ae"
pkgrel=1
arch=(
  'x86_64'
  'arm'
  'aarch64'
  'i686'
  'mips'
  'powerpc'
  'pentium4'
)
if [[ "${_source}" == "ur" ]]; then
  _ns="themartiancompany"
fi
url="https://github.com/${_ns}/${_pkgbase}"
license=(
  'custom'
)
depends=(
  'nodejs'
)
makedepends=(
  'npm'
)
provides=(
  "${_node}-${_pkg}=${pkgver}"
)
conflicts=(
  "${_node}-${_pkg}=${pkgver}"
)
source=(
)
sha256sums=(
)
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
[[ "${_offline}" == "true" ]] && \
  _url="file://${HOME}/${pkgname}"
if [[ "${_source}" == "ur" ]]; then
  _tar="${_tarname}.zip::${_url}/archive/${_commit}.zip"
  source+=(
    "${_tar}"
  )
  _sum='0319169b62cfd5d7dd8a453f4ad8632c4dfea56eb308b70164163d9243736ec6'
  sha256sums+=(
    "${_sum}"
  )
elif [[ "${_source}" == "npm" ]]; then
  _npm="http://registry.npmjs.org"
  source+=(
    "${_npm}/@${_pub}/${_pkgbase}/-/${_pkgbase}-${pkgver}.tgz"
  )
  sha256sums+=(
    'ab89f7dbf14d288850df34061b0e42bcf17a193bc30a963021fedb118fdd65365b81f0ec1f28c9c144715097f7550bae263f9f0c8165e3e2a40556f0e047fa8c'
  )
  noextract=(
    "${_pkgbase}-${pkgver}.tgz"
  )
fi

prepare() {
  echo
}

build() {
  cd \
    "${srcdir}/${_tarname}"
  npm \
    install \
    . || \
    true
  echo \
    "$(pwd)"
  npm \
    pack
}

package() {
  local \
    _npm_options=() \
    _tgz
  _npm_options=(
    -g
    # --user=root
    --prefix="${pkgdir}/usr"
  )
  cd \
    "${srcdir}/${_tarname}"
  _tgz="${_pub}-${_pkg}-${_pkgver}.tgz"
  npm \
    "${_npm_options[@]}" \
    install \
      "${_tgz}"
}

# vim:set sw=2 sts=-1 et:

# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Contributors:
#   Filipe Bertelli
#     <filipebertelli@tutanota.com>

_os="$(
  uname \
    -o)"
_arch="$(
  uname \
    -m)"
_evmfs_available="$(
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_npm" ]]; then
  _npm="false"
fi
if [[ ! -v "_git_service" ]]; then
  _git_service="github"
fi
if [[ ! -v "_offline" ]]; then
  _offline='false'
fi
if [[ ! -v "_archive_format" ]]; then
  if [[ "${_git}" == "true" ]]; then
    if [[ "${_evmfs}" == "true" ]]; then
      _archive_format="bundle"
    elif [[ "${_evmfs}" == "false" ]]; then
      _archive_format="git"
    fi
  elif [[ "${_git}" == "false" ]]; then
    if [[ "${_npm}" == "true" ]]; then
      _archive_format="tgz"
    elif [[ "${_npm}" == "false" ]]; then
      if [[ "${_git_service}" == "github" ]]; then
        _archive_format="zip"
      elif [[ "${_git_service}" == "gitlab" ]]; then
        _archive_format="tar.gz"
      fi
    fi
  fi
fi
if [[ ! -v "_pub" ]]; then
  _pub="nomicfoundation"
  if [[ "${_os}" == "Android" ]]; then
    _pub="nomicfoundation"
  fi
fi
if [[ ! -v "_ns" ]]; then
  _ns="NomicFoundation"
  # Android support
  _ns="themartiancompany"
fi
if [[ "${_os}" == "Android" ]]; then
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
pkgrel=7
arch=(
  'x86_64'
  'arm'
  'aarch64'
  'i686'
  'mips'
  'powerpc'
  'pentium4'
)
_http="https://${_git_service}.com"
url="${_http}/${_ns}/${_pkgbase}"
license=(
  'custom'
)
depends=(
  "${_node}"
)
makedepends=(
)
if [[ "${_os}" == "GNU/Linux" ]]; then
  makedepends+=(
    "npm"
  )
elif [[ "${_os}" == "Android" ]]; then
  makedepends+=(
    "${_node}"
  )
fi
if [[ "${_git}" == "true" ]]; then
  makedepends+=(
    "git"
  )
fi
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
fi
provides=(
  "${_node}-${_pkg}=${pkgver}"
)
conflicts=(
  "${_node}-${_pkg}=${pkgver}"
)
_url="${url}"
if [[ "${_npm}" == "true" ]]; then
  _tag="${pkgver}"
  _tag_name="pkgver"
elif [[ "${_npm}" == "false" ]]; then
  _tag="${_commit}"
  _tag_name="commit"
fi
_tarname="${pkgname}-${_tag}"
_tarfile="${_tarname}.${_archive_format}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
_bundle_sum="07e61eefafa3c68fe079596b407592d6992eb1f857746b4d876e0dd8b9df0335"
_bundle_sig_sum="065c0209a161d7f9a4000b512cc2aa35683e086986fc82dd0649a98ee27b6597"
_gitlab_sum="be36bae17e6879582057a5cead30e9fb90d701f99e2b5db1e32b27ca1e51054f"
_gitlab_sig_sum="69ef172a077d5a0dcbac8083836417b0f2221b1a8e1607deac063b51a1599366"
_github_sum='0319169b62cfd5d7dd8a453f4ad8632c4dfea56eb308b70164163d9243736ec6'
_github_sig_sum="3ff957722ef127b40560d53ad39afdfdde0e87091ace2ec8c7cf41db36e7923a"
if [[ "${_git_service}" == "github" ]]; then
  _evmfs_sum="${_github_sum}"
  _evmfs_sig_sum="${_github_sig_sum}"
fi
_npm_sum="SKIP"
_npm_sig_sum="SKIP"
# Truocolo
_evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_evmfs_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_bundle_uri="${_evmfs_dir}/${_bundle_sum}"
_bundle_src="${_tarfile}::${_bundle_uri}"
_evmfs_npm_uri="${_evmfs_dir}/${_npm_sum}"
_evmfs_npm_src="${_tarfile}::${_evmfs_npm_uri}"
_evmfs_sig_uri="${_evmfs_dir}/${_evmfs_sig_sum}"
_evmfs_sig_src="${_tarfile}.sig::${_evmfs_sig_uri}"
_bundle_sig_uri="${_evmfs_dir}/${_bundle_sig_sum}"
_bundle_sig_src="${_tarfile}.sig::${_bundle_sig_uri}"
_npm_sig_uri="${_evmfs_dir}/${_npm_sig_sum}"
_npm_sig_src="${_tarfile}.sig::${_npm_sig_uri}"
_npm_http="http://registry.npmjs.org"
source=()
sha256sums=()
if [[ "${_evmfs}" == "true" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_evmfs_npm_uri}"
    _sum="${_npm_sum}"
    _sig_src="${_npm_sig_src}"
    _sig_sum="${_npm_sig_sum}"
  elif [[ "${_npm}" == "false" ]]; then
    if [[ "${_git}" == "true" ]]; then
      _uri="${_bundle_uri}"
      _sum="${_bundle_sum}"
      _sig_src="${_bundle_sig_src}"
      _sig_sum="${_bundle_sig_sum}"
    elif [[ "${_git}" == "false" ]]; then
      if [[ "${_git_service}" == "github" ]]; then
        _sum="${_github_sum}"
        _sig_sum="${_github_sig_sum}"
      fi
      _uri="${_evmfs_uri}"
      _sig_src="${_evmfs_sig_src}"
    fi
  fi
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_npm_http}/@${_ns}/${_pkg}/-/${_tarfile}"
    _sum="${_npm_sum}"
  elif [[ "${_npm}" == "false" ]]; then
    if [[ "${_git_service}" == "github" ]]; then
      _uri="${_url}/archive/${_commit}.${_archive_format}"
      _sum="${_github_sum}"
    fi
  fi
fi
_src="${_tarfile}::${_uri}"
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)
if [[ "${_npm}" == "true" ]]; then
  noextract=(
    "${_tarfile}"
  )
fi
validpgpkeys=(
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
  #   <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
)

_git_unbundle() {
  local \
    _tarname="${1}" \
    _module \
    _bundle \
    _repo \
    _msg=()
  _bundle="${srcdir}/${_tarname}.bundle"
  _repo="${srcdir}/${_tarname}"
  _msg=(
    "Cloning '${_bundle}' into '${_repo}'."
  )
  msg \
    "${_msg[*]}"
  git \
    clone \
      "${_bundle}" \
      "${_repo}" || \
  git \
    -C \
      "${_repo}" \
      pull || \
    true
}

prepare() {
  if [[ "${_evmfs}" == "true" ]]; then
    if [[ "${_git}" == "true" ]]; then
      _git_unbundle \
        "${_tarname}"
    fi
  fi
}

build() {
  cd \
    "${srcdir}/${_tarname}"
  npm \
    install \
    . || \
    true
  echo \
    "${PWD}"
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

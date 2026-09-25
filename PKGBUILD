# SPDX-License-Identifier: AGPL-3.0

#    -----------------------------------------------------
#    Copyright © 2024, 2025, 2026  Pellegrino Prevete
#
#    All rights reserved
#    -----------------------------------------------------
#
#    This program is free software: you can redistribute
#    it and/or modify it under the terms of the
#    GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of
#    the License, or (at your option) any later version.
#
#    This program is distributed in the hope that it
#    will be useful, but WITHOUT ANY WARRANTY;
#    without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
#    See the GNU Affero General Public License for
#    more details.
#
#    You should have received a copy of the
#    GNU Affero General Public License
#    along with this program.
#    If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_os="$(
  uname \
    -o)"
_offline="false"
_git="false"
_pkg=sdotool
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
pkgver=0.0.0.0.0.0.0.0.0.0.0.0.0.1.1.1
_commit="1190f131fe881911299aa1cb05b80c51cc527da9"
pkgrel=1
_pkgdesc=(
  "Command-line SurfaceFlinger automation tool"
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  "any"
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgname}"
license=(
  "AGPL3"
)
depends=(
  'libcrash-bash'
)
[[ "${_os}" == "GNU/Linux" ]] && \
[[ "${_os}" != "Android" ]] && \
  depends+=(
    "sudo"
  )
if [[ "${_os}" != "GNU/Linux" ]] && \
   [[ "${_os}" == "Android" ]]; then
  depends+=(
    'android-input-utils'
    'tsu'
  )
fi
optdepends=(
  'xdotool: same tool for X11'
)
if [[ "${_os}" == 'Android' ]]; then
  optdepends+=(
  )
fi
makedepends=(
  "make"
)
checkdepends=(
  "shellcheck"
)
source=()
sha256sums=()
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
if [[ "${_offline}" == "true" ]]; then
  url="file://${HOME}/${pkgname}"
fi
if [[ "${_git}" == true ]]; then
  makedepends+=(
    "git"
  )
  source+=(
    "${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
  )
  sha256sums+=(
    SKIP
  )
elif [[ "${_git}" == false ]]; then
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _tar="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum="d4f4179c6e4ce1702c5fe6af132669e8ec4d0378428f69518f2926b969663a91"
  elif [[ "${_tag_name}" == "commit" ]]; then
    _tar="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum="1af27c8b9aeaa91fe0c92d448e1e6512d597dae3f53a07433153ba6138ac9655"
  fi
  source+=(
    "${_tar}"
  )
  sha256sums+=(
    "${_sum}"
  )
fi
validpgpkeys=(
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  #   <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
)

check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

package() {
  ls
  cd \
    "${_tarname}"
  make \
    PREFIX="/usr" \
    DESTDIR="${pkgdir}" \
    install
}

# vim: ft=sh syn=sh et

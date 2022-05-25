#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com> and Guillaume Horel <guillaume.horel@gmail.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/python-ufo2ft/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/python-ufo2ft/discussions>

_langname="python"
_relname="ufo2ft"


pkgname="${_langname}-${_relname}"
pkgver=2.27.0
pkgrel=1
pkgdesc="A bridge from UFOs to FontTools objects"
arch=(
  "any"
  )
url="https://github.com/googlefonts/ufo2ft"
license=(
  "MIT"
  )
depends=(
  "python"
  "python-booleanoperations"
  "python-cffsubr"
  "python-cu2qu"
  "python-lxml" # for fonttools[lxml]
  "python-defcon"
  "python-fonttools"
  "python-fs"
  )
makedepends=(
  "python-build"
python-installer
  "python-setuptools-scm"
  "python-wheel"
  )
checkdepends=(
  "python-compreffor"
  "python-pytest"
  "python-skia-pathops"
  )
optdepends=(
  "python-compreffor"
  "python-skia-pathops"
  )
_tarname="${_relname}-${pkgver}"
source=(
  "https://files.pythonhosted.org/packages/source/${_relname::1}/${_relname}/${_tarname}.tar.gz"
  )
sha512sums=(
  "f1475424730a98d8eee4b1c3fcbcace97b55e8b5109cae5ad5a1de191d30483ac9ecfc8e1ade3eabb0d04e12dfb2bfc73478b17d637d65c566b7ddf41dc0caec"
  )

build() {

  cd "${_tarname}"

  python -m build -wn
}

check() {

  cd "${_tarname}"

  PYTHONPATH=Lib pytest tests
}

package() {

  cd "${_tarname}"

  python -m installer -d "${pkgdir}" dist/*.whl

  install -Dm0644 -t "${pkgdir}/usr/share/licenses/${pkgname}/" LICENSE
}

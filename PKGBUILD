# Maintainer: AnClark Liu <anclarkliu@outlook.com>

pkgname=loongarch64-linux-crosstool-gcc
_target=loongarch64-unknown-linux-gnu
pkgver=12.1.0
pkgrel=1
pkgdesc='The GNU Compiler Collection - cross compiler for LoongArch64 target (built with crosstool-NG)'
arch=('x86_64')
url='https://gcc.gnu.org/'
license=('GPL' 'LGPL' 'FDL')
groups=('loongarch')
options=('!emptydirs' '!strip' '!buildflags')
provides=('loongarch64-linux-gnu-gcc' 'loongarch64-linux-gnu-binutils')        # The two packages come from AUR.
conflicts=('loongarch64-linux-gnu-gcc' 'loongarch64-linux-gnu-binutils')       # Since our package contains binutils, no need to built there.
source=('git+https://github.com/jiegec/crosstool-ng.git#branch=loongarch'
        'git+https://github.com/jiegec/ct-ng-loongarch64#commit=b3ce2ead0')    # crosstool-NG source and config file from Jiege
sha256sums=('SKIP'
            'SKIP')

_build_ct-ng() {
  # Build crosstool-NG
  cd "$srcdir"/crosstool-ng
  if [ ! -e configure ]; then
    ./bootstrap
  fi
  ./configure --enable-local
  make -j$(nproc)
}

prepare() {
  # Create work directories
  mkdir -p "$srcdir"/build
  mkdir -p "$srcdir"/download

  # Copy config file
  cp "$srcdir"/ct-ng-loongarch64/.config "$srcdir"/build/

  # Replace working directories
  cd "$srcdir"/build
  sed -i -E "s|CT_LOCAL_TARBALLS_DIR=.*|CT_LOCAL_TARBALLS_DIR=\"$srcdir/download\"|g" .config    # Tarball download path
  sed -i -E "s|CT_PREFIX_DIR=.*|CT_PREFIX_DIR=\"$srcdir/out\"|g" .config                         # Target path (prefix)
  sed -i -E "s|CT_WORK_DIR=.*|CT_WORK_DIR=\"$srcdir/build\"|g" .config                           # Work directory

  # Do not render prefix directory read-only
  sed -i -E "s|CT_PREFIX_DIR_RO=.*|CT_PREFIX_DIR_RO=n|g" .config

  _build_ct-ng
}

build() {
  # Build toolchain
  cd "$srcdir"/build
  "$srcdir"/crosstool-ng/ct-ng build
}

package() {
  # Copy files
  mkdir -p "$pkgdir"/usr/$_target
  cp -r "$srcdir"/out/* "$pkgdir"/usr/$_target

  # Create symbolic links for executables
  mkdir -p "$pkgdir"/usr/bin
  for i in `ls "$pkgdir"/usr/$_target/bin`; do
    ln -s /usr/$_target/bin/$i "$pkgdir"/usr/bin/$i
  done
}

# vim: ts=2 sw=2 et:

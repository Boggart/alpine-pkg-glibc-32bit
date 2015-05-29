# Maintainer: Boggart <github.com/Boggart>

pkgname="glibc"
pkgver="2.21"
pkgrel="4"
pkgdesc="GNU C Library compatibility layer"
arch="i686"
url="https://github.com/boggart/alpine-pkg-glibc-32bit"
license="GPL"
source="http://mirrors.kernel.org/archlinux/core/os/i686/glibc-${pkgver}-${pkgrel}-${arch}.pkg.tar.xz
ld.so.conf"
subpackages="$pkgname-bin"
triggers="$pkgname-bin.trigger=/usr/glibc/usr/lib"

package() {
  mkdir -p "$pkgdir"/usr/glibc
  mkdir "$pkgdir"/etc
  mkdir "$pkgdir"/lib
  cp -a "$srcdir"/usr "$pkgdir"/usr/glibc/usr
  rm -rf "$pkgdir"/usr/glibc/usr/lib/systemd \
    "$pkgdir"/usr/glibc/usr/lib/gconv \
    "$pkgdir"/usr/glibc/usr/lib/locale \
    "$pkgdir"/usr/glibc/usr/lib/tmpfiles.d \
    "$pkgdir"/usr/glibc/usr/lib/getconf \
    "$pkgdir"/usr/glibc/usr/lib/audit \
    "$pkgdir"/usr/glibc/usr/lib/*.a \
    "$pkgdir"/usr/glibc/usr/bin/* \
    "$pkgdir"/usr/glibc/usr/include \
    "$pkgdir"/usr/glibc/usr/share
  "$srcdir"/usr/bin/ldconfig -r "$pkgdir" -C /etc/ld.so.cache /usr/glibc/usr/lib
  ln -s /usr/glibc/usr/lib/ld-linux.so.2 ${pkgdir}/lib/ld-linux.so.2
}

bin() {
  mkdir -p "$subpkgdir"/usr/glibc/usr/bin \
    "$subpkgdir"/etc
  cp -a "$srcdir"/usr/bin/* "$subpkgdir"/usr/glibc/usr/bin/
  cp -La "$srcdir"/ld.so.conf "$subpkgdir"/etc/
}

md5sums="79dc04070422bf18c11a0b3a49716cd9  glibc-2.21-4-i686.pkg.tar.xz
ba6a1612034f2ad8c7efad392e278103  ld.so.conf"

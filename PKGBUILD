# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=vim-submode-git
pkgver=20140216
pkgrel=1
pkgdesc="Create your own submodes"
arch=('any')
depends=('vim')
makedepends=('git')
groups=('vim-plugins')
url="https://github.com/kana/vim-submode"
license=('MIT')
source=(git+https://github.com/kana/vim-submode)
sha256sums=('SKIP')
provides=('vim-submode')
conflicts=('vim-submode')
install=vimdoc.install

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  cd ${pkgname%-git}

  msg 'Installing dirs...'
  install -dm 755 "$pkgdir/usr/share/vim/vimfiles"
  for _dir in autoload doc; do
    cp -dpr --no-preserve=ownership $_dir "$pkgdir/usr/share/vim/vimfiles/$_dir"
  done

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
  find "$pkgdir" -type f -name .gitignore -exec rm -r '{}' +
}

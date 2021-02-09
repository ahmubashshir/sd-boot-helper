# Maintainer: Ahmad Hasan Mubashshir <ahmubashshir@gmail.com>
# pkg: git
pkgname=sd-boot-helper-git
pkgver=r.0
pkgrel=1
pkgdesc="Add/Update/Remove sd-boot entries automatically"
arch=(any)
url="https://github.com/ahmubashshir/sd-boot-helper"
license=('GPL')
depends=('base')
source=(
	99-sd-boot.hook
	sd-boot
	sd-boot.default
	update-sd-boot
)
backup=(
	'etc/default/sd-boot'
)
sha256sums=('70902cbea67ccd710858dc5394f1f1c7010e98dcf506f7532b14b2071de91f8c'
            'f60c1fc8a39af0c42922c07c654276a1e55d16091700697bb74382559bb96a18'
            '391313133a0a95b9f46971bf79a04ad1acbd05e796fd9ca0956534c3fe3b2267'
            'b772eeabf960c42e918b3672fae247a5c3ec28ec5340c0f6b09b57a6c6999423')

pkgver()
{
	cd "$srcdir"
	( set -o pipefail
		git describe --tags --long 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
		printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
	)
}

package() {
	cd "$srcdir"
	install -Dm644 sd-boot.default "$pkgdir/etc/default/sd-boot"
	install -Dm644 99-sd-boot.hook "$pkgdir/usr/share/libalpm/hooks/99-sd-boot.hook"
	install -Dm755 sd-boot "$pkgdir/usr/share/libalpm/scripts/sd-boot"
	install -Dm755 update-sd-boot "$pkgdir/usr/bin/update-sd-boot"
}

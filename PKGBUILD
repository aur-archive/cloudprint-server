# Maintainer:  Michele Damiano Torelli <me_AT_mdtorelli_DOT_it>
# Contributor: Kevin Cox <kevincox.ca@gmail.com>

pkgname=cloudprint-server
pkgver=3
pkgrel=1
pkgdesc='A systemd service file for starting Chromium in Google Cloud Print proxy mode'
arch=('any')
url='https://support.google.com/chromeos/a/bin/answer.py?hl=en&answer=2616503'
license=('MIT')
depends=('chromium' 'python2')
install=${pkgname}.install
source=("http://www.google.com/support/enterprise/static/chromeos/docs/admin/en/generate_cloudprint_config.py.zip"
        'cloudprint-server.service'
        'generate_cloudprint_config.sh'
        'LICENSE')
sha1sums=('17aacec9aa0f11e83d46e51593bff4789c7e7bad'
          '3008e6e48bcd5a488aeec8ec4059dfe01950c8f6'
          'fa7cd27779c33f51596ddcd198b53a36abc2cae3'
          '41613d070749f35f3890dbad6398a292a9f316b4')

prepare() {
	sed -i 's|#!/usr/bin/python|#!/usr/bin/python2|' generate_cloudprint_config.py
}

package() {
	install -d "${pkgdir}"/usr/lib/systemd/system/
	install -d "${pkgdir}"/usr/lib/cloudprint-server/
	install -d "${pkgdir}"/etc/cloudprint-server/
	install -d "${pkgdir}"/usr/share/licenses/cloudprint-server-systemd/

	install -dm600 "${pkgdir}"/etc/cloudprint-server/connectors/
	install -m644 cloudprint-server.service "${pkgdir}"/usr/lib/systemd/system/
	install -m755 generate_cloudprint_config.py "${pkgdir}"/usr/lib/cloudprint-server/
	install -m755 generate_cloudprint_config.sh "${pkgdir}"/usr/lib/cloudprint-server/
	install -m644 LICENSE "${pkgdir}"/usr/share/licenses/cloudprint-server-systemd/
}

# Maintainer: Jordan Anderson <aq@es.gy>
# Credit for updated PKGBUILD to: https://github.com/mulander/graphite-web-aur
pkgname=graphite-git
pkgver=20140921
pkgrel=3
pkgdesc="Graphite provides real-time graphing for monitoring purposes."
url="http://www.graphite.wikidot.com"
arch=('x86_64' 'i686')
license=('Apache 2.0')
depends=('python2-cairo' 'python2-django>=1.6.2' 'django-tagging' 'python2-simplejson' 'twisted')
optdepends=('statsd-git: feed data to Graphite' 'uwsgi: run Graphite server')
makedepends=()
conflicts=()
replaces=()
backup=()
install='graphite.install'
source=("graphite::git+https://github.com/graphite-project/graphite-web.git"
        "whisper::git+https://github.com/graphite-project/whisper.git"
        "carbon::git+https://github.com/graphite-project/carbon.git"
        "uwsgi-graphite.ini"
        "carbon.conf"
        "storage-schemas.conf"
        "local_settings.py"
	"carbon.service"
        "passenger_wsgi.py")
md5sums=('SKIP'
         'SKIP'
         'SKIP'
         'f8ef934481c8b98a54fb426542d75f46'
         'd7fdde32aa572642439824b3716fb2b5'
         '8931a29a040db5b5ba9c5b191234fc02'
         'bdf3f7026d5d22f9af7df58857597063'
         'b509cf6dc6e46939cc86fa7387a8b1e0'
         'f198167a3ea4a7aeb4a94fa1b56fabeb')

package() {
    cd $srcdir/carbon
    python2 setup.py install --root $pkgdir
    cd $srcdir/whisper
    python2 setup.py install --root $pkgdir
    cd $srcdir/graphite
    python2 setup.py install --root $pkgdir
    install -D $srcdir/uwsgi-graphite.ini $pkgdir/opt/graphite/conf/uwsgi-graphite.ini
    install -D $srcdir/carbon.conf $pkgdir/opt/graphite/conf/carbon.conf
    install -D $srcdir/storage-schemas.conf $pkgdir/opt/graphite/conf/storage-schemas.conf
    install -D $srcdir/local_settings.py $pkgdir/opt/graphite/webapp/graphite/local_settings.py
    install -D $srcdir/carbon.service $pkgdir/usr/lib/systemd/system/carbon.service
    install -D $srcdir/passenger_wsgi.py $pkgdir/opt/graphite/webapp/graphite/passenger_wsgi.py
}

# vim:set ts=4 sw=2 et:


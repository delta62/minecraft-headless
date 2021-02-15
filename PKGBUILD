pkgname=minecraft-headless
pkgver=1.16.5
pkgrel=1
pkgdesc='Headless minecraft server'
url='https://www.minecraft.net/en-us/download/server'
arch=('any')
source=(
    "minecraft_server.${pkgver}.jar::https://launcher.mojang.com/v1/objects/1b557e7b033b583cd9f66746b7a9ab1ec1673ced/server.jar"
    "$pkgname.service"
    "minecraft.sysusers"
)
sha256sums=(
    '58f329c7d2696526f948470aa6fd0b45545039b64cb75015e64c12194b373da6'
    '2ce39ebc719ad34c1f9162774c896dae7b848ab9e57a99c5285790909d53b67b'
    'a560b86305ff2686482ac470f20eacc05a99c03781388e0de1ccbd32797193a0'
)
noextract=("minecraft_server.${pkgver}.jar")
backup=("opt/$pkgname/world")
depends=('jre-openjdk-headless')
install="$pkgname.install"

package() {
    # Add minecraft systemd user
    install -Dm 644 minecraft.sysusers "$pkgdir/usr/lib/sysusers.d/minecraft.conf"

    # Game files
    install -d "$pkgdir/opt/$pkgname"
    install -Dm 644 "minecraft_server.${pkgver}.jar" "$pkgdir/opt/$pkgname/"

    # Systemctl service
    install -d "$pkgdir/usr/lib/systemd/system/"
    install -m 644 "$pkgname.service" "$pkgdir/usr/lib/systemd/system/"
}

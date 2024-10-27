# Maintainer: Your Name rheza.as@gmail.com
pkgname=pearl-workspace
pkgver=1.0.1
pkgrel=1
pkgdesc="Pearl workspace setup"
arch=("x86_64")
license=("custom")
depends=(
    # Drivers
    "mesa" "pavucontrol" "brightnessctl"
    "pulseaudio" "openrgb"
    
    # Desktop Environment
    "ly" "hyprland" "wayland" "wofi" "nwg-look"
    
    # Fonts
    "ttf-dejavu" "noto-fonts" "otf-font-awesome"

    # Support Apps
    "alacritty" "nemo"
)

prepare() {
    echo "Checking for dependencies..."

    for dep in "${depends[@]}"; do
        if ! pacman -Qi "$dep" &>/dev/null; then
            echo "Dependency "$dep" is missing and will be installed."
            sudo pacman -S --needed "$dep" --noconfirm
        else
            echo "Dependency "$dep" is already installed."
        fi
    done
}

package() {
    mkdir -p "$pkgdir/opt/pearl-workspace/dotfiles"
    cp -a "$srcdir/dotfiles/." "$pkgdir/opt/pearl-workspace/dotfiles/"

    install -Dm755 "$srcdir/pearl-setup" "$pkgdir/usr/bin/pearl-setup"
}
# Arch installation

## Resources
- [Arch Wiki](https://wiki.archlinux.org/title/installation_guide)
- [Youtube guide](https://www.youtube.com/watch?v=FxeriGuJKTM)
- [Balena Etcher](https://etcher.balena.io/)

## Guidelines
- Modifications to this [video](https://www.youtube.com/watch?v=FxeriGuJKTM) instructions:
    - Wifi setup: `iwctl passpharse 'password' station wlan0 connect CLAN`
    - Only 2 partitions are required:
      - /: as ext4 (type 23)
      - /boot: as EFI (type 1)
    - Packages to install: <br> `pacman -S base-devel dosfstools grub efibootmgr plasma sddm mtools nano networkmanager os-prober sudo tmux tldr wget curl git vim htop tree tar zsh exa mc dolphin konsole falkon cmatrix screenfetch zip unzip fzf inetutils pipewire wireplumber pipewire-alsa pipewire-pulse sof-firmware bluez bluez-utils`
    - Enabling bluetooth: `systemctl enable bluetooth.service`
    - Grub configuration modifications:
      - `vim /etc/default/grub`
      - Uncomment the (last) line: `GRUB_DISABLE_OS_PROBER=false`
      - `grub-install --target=x86_64-efi --bootloader-id=grub_uefi --efi-directory=/boot --recheck`
- Post configuration changes:
    - Issue with sudoers
      - `su`
      - `chmod 640 /etc/sudoers`
      - `vim /etc/sudoers`
      - Uncomment the line: `%wheel ALL=(ALL:ALL) ALL`
    - Wayland support with NVIDIA: [guide](https://wiki.archlinux.org/title/NVIDIA)
      - `cat <<EOF>> /etc/modprobe.d/nvidia-drm-nomodset.conf`
      - `options nvidia-drm modeset=1`
      - `EOF`
      - `reboot`
    - yay [installation](https://itsfoss.com/install-yay-arch-linux/)
    - Installation of basic applications: Chrome, Jetbrains, conda and NordVPN, paru
    - Updating tldr: `tldr --update`
    - [OhMyZsh](https://ohmyz.sh/) installation and modification to .zshrc file with the addition of:
        - tmux
        - tldr --update
        - alias update='sudo pacman -Syu'
        - alias poweroff='shutdown -h now'
        - alias clean='sudo pacman -R $(pacman -Qtdq)'
        - alias fzfq='vim $(fzf --preview="cat {}")'
    - Mounting an external drive:
      - `sudo vim /etc/fstab`
      - `# /dev/nvme0n1
        UUID=a0fa3b64-2178-4f28-8047-67a82547680c       /home/carlos/Data   ext4            rw,relatime     0 3`
- Maintenance
  - In case there is a corruption on the Arch package database:
    - [Article](https://bbs.archlinux.org/viewtopic.php?id=262288)
    - Command: `sudo pacman -Syy --overwrite $(pacman -Qnq)`
  - Issues with Chrome not starting as there is already another instance running. Command: `rm -rf ~/.config/google-chrome/Singleton*`
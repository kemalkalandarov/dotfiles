# dotfiles (temporary clone)

## Setup (on fresh system)

### Login as root

Login as `root`, password is `voidlinux`

### User

```sh
useradd -m -s /bin/zsh -U -G wheel,users,audio,video,cdrom,input kek
passwd kek 
# enter new password

su kek # press 1 then q to skip .zshrc file creation, .zshrc should be symlinked from dotfiles. If you accidentally created .zshrc, just delete it.
```

### WI-FI (skip if wired network is being used)

```sh
sudo vim /etc/wpa_supplicant/wpa_supplicant.conf
# ! don't forget to remove disabled=1
# set name/password
sudo sv restart wpa_supplicant
```

### Expand disk (mmcblk1 is SD card)

```sh
sudo cfdisk mmcblk1 
# expand mmcblk1p2 disk size
sudo resize2fs /dev/mmcblk1p2
```

### Configs

This is temporary dotfiles repo for a quick demo setup.
If you plan to customise any configs, please create your own `dotfiles` repo and use this one as a template or just download all the files and place them into your `home` directory manually (except ones listed in .stow-local-ignore).
Please don't fork it, I'm not sure I'd keep this repo forever.

```sh
cd # home 
git clone https://github.com/kemalkalandarov/dotfiles.git
cd dotfiles
stow .
```

### Reboot

```sh
sudo reboot
```

After reboot login as user, Hyprland desktop should start automatically.

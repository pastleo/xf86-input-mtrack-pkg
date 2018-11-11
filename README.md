xf86-input-mtrack
=================

source: https://github.com/pastleo/xf86-input-mtrack

### Install on archLinux

```
git clone https://github.com/pastleo/xf86-input-mtrack-pkg.git
cd xf86-input-mtrack-pkg
makepkg -si

cp /usr/share/X11/xorg.conf.d/10-mtrack.conf /etc/X11/xorg.conf.d/10-mtrack.conf # and change if needed
```

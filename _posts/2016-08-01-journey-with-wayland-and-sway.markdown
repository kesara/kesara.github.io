---
layout:         post
title:          "Journey with Wayland and Sway"
description:    "I tried out Wayland with Sway windows manager."
date:           2016-08-01 23:23:23
categories:     wayland sway linux parabola
image:          /images/2016-08-01-230023_swaygrab.png
---
[Wayland][wayland] is the new *better* windowing protocol for Linux which is
supposed to replace X11 windowing system. It's still in beta stage. I decided
to give it a go on my ThinkPad X200 which runs
[Parabola GNU/Linux-libre][parabola]. These instructions will work on
[Arch GNU/Linux][arch] as well since Parabola is based on it.

> ## TL;DR
> I tried Sway windows manager and Wayland, and it was awesome!

I started with a fresh installation without any X tools. I installed Wayland
and then sway.

    sudo pacman -S wayland
    sudo pacman -S sway

I just typed in `sway`, and *Sway* started on the same tty console. Awesome! :)
![Welcome to Sway!](/images/2016-08-01-230023_swaygrab.png "Welcome to Sway!")

[Sway][sway] is drop-in replacement for the i3 window manager, but for Wayland.
It is supposed to work with existing i3 configurations. _(But I'm no i3 user,
I used to work with [awesome][awesome].)_ 

System wide sway configuration file is located at `/etc/sway/config/`,
I recommend copying that file to `~/.config/sway/config/` and do necessary
changes. And it's worth installing *urxvt* terminal emulator as well.
    sudo pacman -S rxvt-unicode
With default sway configuration, `Super Key + Enter` gives you urxvt.
I found [Epiphany][epiphany] to be nice web browser on Sway, but had to
install couple of fonts to make it look good. So this what I did:

    sudo pacman epiphany
    sudo pacman ttf-freefont
    sudo pacman ttf-dejavu

Epiphany on Sway:
![Epiphany on Sway/Wayland](/images/2016-08-01-230645_swaygrab_epiphany.png
"Epiphany on Sway")

I tried out [EOG (Eye of GNOME)][eog] image browser and [mpv][mpv] media player
and everything worked well.
EOG:
![Eye of GNOME on Sway/Wayland](/images/2016-08-01-230411_swaygrab_eog.png
"Eye of GNOME on Sway")

mpv:
![mpv on Sway/Wayland](/images/2016-08-01-232426_swaygrab_mpv.png
"mpv on Sway")

## Tips & Tricks
* With default sway configuration, `Super Key + Shift + e` exits you from Sway.
* You can have multiple Sway/Wayland sessions by executing `sway` on multiple
tty consoles.
* `swaygrab` takes screenshots.
* Sway comes with bunch of helpful man pages.

[wayland]:  https://wayland.freedesktop.org/
[parabola]: https://www.parabola.nu/
[arch]:     https://www.archlinux.org/
[sway]:     http://swaywm.org/
[awesome]:  https://awesomewm.org/
[epiphany]: https://wiki.gnome.org/Apps/Web/
[eog]:      https://wiki.gnome.org/Apps/EyeOfGnome
[mpv]:      https://mpv.io/

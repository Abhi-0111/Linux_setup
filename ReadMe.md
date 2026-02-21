# Linux Installation
## WHY???
The reason I am making this file is because I have a habit of crashing my Arch Linux Usually by simple command pacman -Syy.....
1) Database desync → partial upgrade hell

Arch follows a strict rolling-release invariant:

All packages must be upgraded together

When you run -Syy and then:

install one package, or

upgrade only some packages

you risk a partial upgrade, which can break:

glibc

systemd

linux kernel

NVIDIA / DKMS modules

💣 Result: system won’t boot, services fail, or pacman itself breaks.
Mirror mismatch (this is the big one)

2) If your mirrors are out of sync:

core repo updated

extra/community lagging

-Syy forces pacman to accept inconsistent repo states.

Then pacman may try:

installing package A built against new libc

while your system still has old libc

That’s ABI mismatch → segfaults → “Arch broke” posts.

## Before archinstall
## setting network configuration...
1) iwctl: iNet wireless daemon control tool... It is a command line client for iwd daemon to connect to WiFi network.
   iwctl commands:
   iwctl
   device list
   station wlan0 scan
   station wlan0 get-networks
   station wlan0 connect "Network-Name"
   passware:......
   exit.
2) fix system time.
    timedatectl set-ntp true
    timedatectl status
      check for: system clock synchronized: Yes
3) pacman-key --init
4) pacman-key --populate archlinux
5) pacman -Sy archlinux-keyring
6) pacman -Syu

## archinstall

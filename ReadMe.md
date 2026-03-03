# Linux Installation
## WHY???
The reason I am making this file is because I have a habit of crashing my Arch Linux Usually by simple command pacman -Syy..... it causes

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

# Before archinstall
# setting network configuration...
1) iwctl: iNet wireless daemon control tool... It is a command line client for iwd daemon to connect to WiFi network.
2)  iwctl commands:
3)   iwctl
4)  device list
5)  station wlan0 scan
6)  station wlan0 get-networks
7)  station wlan0 connect "Network-Name"
8)  passware:......
9)  exit.

# fix system time.
   
   timedatectl set-ntp true
   timedatectl status
     check for: system clock synchronized: Yes
# Populate keyring 
   pacman-key --init
 pacman-key --populate archlinux
 pacman -Sy archlinux-keyring
 pacman -Syu

# archinstall

| dd linux folder in linuxdoom-1.10 folder |
|  |  | change <errnos.h> to <errno.h> in i_video.c |
|  |  | add -m32 -Wno-unused-variable to makefile line "CFLAGS=-g -Wall -DNORMALUNIX -DLINUX # -DUSEASM" |
|  |  |\
 |
|  |  | --------------------------------------------- |
|  |  |\
 |
|  |  | sudo dpkg --add-architecture i386 |
|  |  | sudo apt-get update |
|  |  | sudo apt-get dist-upgrade |
|  |  | sudo apt-get install build-essential gcc-multilib xorg libx11-dev libxcomposite-dev libx11-dev:i386 libxcomposite-dev:i386 doom-wad-shareware x11-apps |
|  |  |\
 |
|  |  | add to ~/.bashrc |
|  |  | export DISPLAY=$(awk '/nameserver / {print $2; exit}' /etc/resolv.conf 2>/dev/null):0 |
|  |  | export LIBGL_ALWAYS_INDIRECT=1 |
|  |  |\
 |
|  |  | to build |
|  |  | starting in the linuxdoom-1.10 folder |
|  |  | make clean && make && cd linux && cp /usr/share/games/doom/doom1.wad |
|  |  |\
 |
|  |  | on windows start an xserver. On linux start a local screen to deal with 8 bit colour (xserver within an xserver) |
|  |  | Xephyr -br -ac -noreset -screen 800x600x8 :1 |
|  |  |\
 |
|  |  | in the linux folder run |
|  |  | DISPLAY=:1 ./linuxxdoom |

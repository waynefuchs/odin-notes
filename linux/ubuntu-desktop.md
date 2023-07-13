# Ubuntu Setup

Ubuntu is a linux distribution that is based on Debian. It is released every 6 months, with each release receiving 9 months of support. Every 2 years, a Long Term Support (LTS) version is released, which is supported for five years.

- [Ubuntu Setup](#ubuntu-setup)
- [Fix windows dual boot time zone issues](#fix-windows-dual-boot-time-zone-issues)
- [Add Software](#add-software)
- [Configure Gnome](#configure-gnome)
- [Git](#git)
- [Install Docker](#install-docker)
- [Install Databases (if required)](#install-databases-if-required)
- [Snaps](#snaps)
- [Download Software](#download-software)
- [VSCode Setup](#vscode-setup)
- [Postman with Gnome Launcher](#postman-with-gnome-launcher)
- [Nomachine](#nomachine)
- [Remove Games](#remove-games)
- [⚠️ snap-store glitch](#️-snap-store-glitch)
  - [Get the process id of the `snap-store` process](#get-the-process-id-of-the-snap-store-process)
  - [kill the `snap-store` process](#kill-the-snap-store-process)
  - [Upgrade the `snap-store` package](#upgrade-the-snap-store-package)

# Fix windows dual boot time zone issues

Windows expects the system clock to be set to local time. Linux defaults to GMT. The easiest solution is to set linux to use local time.

```
timedatectl set-local-rtc 1
```

# Add Software

`sudo apt install git build-essential gt5 dconf-editor gnome-tweaks htop net-tools vim gnome-shell-pomodoro gimp`

# Configure Gnome

If you plan on using Gnome extensions, be sure to install the browser connector.

```bash
# if `lsb-release -a` reports ubuntu version less than 23.04
sudo apt install chrome-gnome-shell
# otherwise
sudo apt install gnome-browser-connector
```

Then, see (my) [Gnome Setup](./setup-gnome.md) page.

# Git

See (my) [Git Setup](./git.md#setup) section.

# Install Docker

[Ubuntu Docker Installation Instructions](https://docs.docker.com/engine/install/ubuntu/) can be found on the docker website. Don't use `apt` or `snap` to install docker. The experience is **far better** if you install from the docker maintained package sources.

# Install Databases (if required)

See (my) [Docker Databases Setup](./databases/Docker-Databases.md) information to get up and running with Postgres and Mongodb.

I have a home lab (separate servers) that I now run my databases on, and would recommend that route to anyone that has the ability to do so.

# Snaps

I try and avoid snaps as much as possible. Here are the ones I use.

| software   | description                       |
| ---------- | --------------------------------- |
| inkscape   | vector graphics                   |
| boxy-svg   | vector graphics / edit svg        |
| discord    | used for the odin project discord |
| obs-studio | to record / share my screen       |
| octave     | math software package             |

# Download Software

| Software                                                               | Note                                                                                   |
| ---------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| [Steam](https://store.steampowered.com/about/)                         | I install this early to get blender installed and verify GPU is working properly.      |
| blender                                                                | The easiest linux install of blender that I have found is through Steam.               |
| [Brave Browser](https://brave.com/linux/#release-channel-installation) | Download and install using the provided instructions. (Instead of Google Chrome)       |
| [VSCode](https://code.visualstudio.com/)                               | Download and install the `.deb`, an update channel is added by installing the package. |
| [obs](https://obsproject.com/download#linux)                           | Open Broadcaster Software                                                              |
| [pgAdmin 4](https://www.pgadmin.org/)                                  | A management tool for PostgreSQL                                                       |
| [MongoDB Compass](https://www.mongodb.com/products/compass)            | GUI for MongoDB.                                                                       |
| [Postman](https://www.postman.com/downloads/)                          | Industry standard platform for building and using APIs.                                |

# VSCode Setup

See (my) [VSCode Setup](./setup-vscode.md).

# Postman with Gnome Launcher

> ⓘ I prefer the "REST Client" extension in vscode, but knowing postman could be a good skill to have.

Download [Postman](https://www.postman.com/downloads/) and extract it to `/opt/Postman`. Download a postman svg (I got mine from google images) and place it in `/opt/Postman` alongside the executable. In the file: `.local/share/applications/Postman.desktop `, put the following:

```ini
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Postman
Comment=Postman API platform
Icon=/opt/Postman/postman-icon.svg
Exec=/opt/Postman/Postman
Terminal=false
Categories=API;REST;Postman
```

# Nomachine

Remote desktop access, similar to VNC.

Download and install [NoMachine](https://www.nomachine.com/)

`sudo apt install ./<downloaded-nomachine-file.deb>`

# Remove Games

```
sudo apt purge gnome-2048 aisleriot atomix gnome-chess five-or-more hitori iagno gnome-klotski lightsoff gnome-mahjongg gnome-mines gnome-nibbles quadrapassel four-in-a-row gnome-robots gnome-sudoku swell-foop tali gnome-taquin gnome-tetravex -y && sudo apt autoremove -y
```

If kde is installed...

> There are a few others that need to be uninstalled, but this gets the bulk of them, for now

```
sudo apt remove blinken bomber bovo cervisia cheese kapman kblocks kbounce kfourinline kgeography kgoldrunner khangman kigo killbots kiriki kiten kjumpingcube klickety kmahjongg kmines knights kolf kollision kreversi kshisen ksirk ksnakeduel kspaceduel ksudoku kturtle kubrick lskat marble minuet picmi umbrello klines granatier knavalbattle ktuberling

&& sudo apt autoremove -y
```

# ⚠️ snap-store glitch

> ⚠️ This only needs to be done when the glitch occurs

On my system, `snap-store` will get stuck in a state where it can not upgrade because it is running.

The fix is as follows:

## Get the process id of the `snap-store` process

```
$ pidof snap-store
4730
```

## kill the `snap-store` process

```
$ kill 4730
```

## Upgrade the `snap-store` package

```
$ sudo apt update && sudo apt upgrade snap
...
Unpacking snap (2013-11-29-11) ...
Setting up snap (2013-11-29-11) ...
Processing triggers for man-db (2.11.2-1) ...
```

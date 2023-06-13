- [Ubuntu Setup](#ubuntu-setup)
- [Fix windows dual boot time zone issues](#fix-windows-dual-boot-time-zone-issues)
- [Rename Sound Card](#rename-sound-card)
- [Add Software](#add-software)
- [Install Docker](#install-docker)
- [Install Databases (if required)](#install-databases-if-required)
- [Snaps](#snaps)
- [Download Software](#download-software)
- [Postman with Icon](#postman-with-icon)
- [gTile](#gtile)
  - [Step 1: Install the shell browser integration](#step-1-install-the-shell-browser-integration)
  - [Step 2: Install the browser extension](#step-2-install-the-browser-extension)
- [Nomachine](#nomachine)
- [Remove Games](#remove-games)
- [Settings](#settings)
  - [Accessibility](#accessibility)
  - [Appearance](#appearance)
  - [Multitasking](#multitasking)
- [dconf-editor](#dconf-editor)
  - [Set a solid color as a background](#set-a-solid-color-as-a-background)
  - [Set up shortcuts to navigate virtual desktops](#set-up-shortcuts-to-navigate-virtual-desktops)
  - [allow VSCode ctrl-alt-shift-up/down line-duplication to work](#allow-vscode-ctrl-alt-shift-updown-line-duplication-to-work)
  - [Set window focus to be the window under the mouse pointer.](#set-window-focus-to-be-the-window-under-the-mouse-pointer)
  - [Disable delaying focus change](#disable-delaying-focus-change)
- [fix snap-store glitch](#fix-snap-store-glitch)
  - [Get the process id of the `snap-store` process](#get-the-process-id-of-the-snap-store-process)
  - [kill the `snap-store` process](#kill-the-snap-store-process)
  - [Upgrade the `snap-store` package](#upgrade-the-snap-store-package)
- [VSCode Setup](#vscode-setup)

# Ubuntu Setup

I'm trying put the changes I make to a default linux setup here in this file to facilitate rapid linux installation in the event that I need to reinstall.

# Fix windows dual boot time zone issues

Windows expects the system clock to be set to local time. Linux defaults to GMT. The easiest solution is to set linux to use local time.

```
timedatectl set-local-rtc 1
```

# Rename Sound Card

I removed this as I can no longer rename my sound card in the new Gnome on Ubuntu, but the `pavucontrol` utility is still useful, so i will mention that. I hope that some day I will be able to rename my sound card again, as I have several audio devices that are exactly the same except one word that is truncated in the drop down list. And it just switches to the wrong one occasionally. Sound in linux is bad, unfortunately. I think it might be getting better, and this is part of the growing pains?

# Add Software

`sudo apt install git build-essential gt5 dconf-editor gnome-tweaks htop net-tools vim gnome-shell-pomodoro gimp`

```bash
git config --global user.name "{YOUR NAME HERE}"
git config --global user.email "{your.email@here}"
# On October 1, 2020, GitHub renamed 'master' to 'main'; the defaultBranch variable will match that locally
git config --global init.defaultBranch main
```

# Install Docker

[Ubuntu Docker Installation Instructions](https://docs.docker.com/engine/install/ubuntu/) can be found on the docker website. Don't use `apt` or `snap` to install docker. The experience is far better if you install from the docker maintained package sources.

# Install Databases (if required)

See my [Docker Databases](./databases/Docker-Databases.md) information to get up and running with Postgres and Mongodb.

I have a home lab that I now run my databases on, and would recommend that route to anyone that has the ability to do so.

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

# Postman with Icon

> ⓘ Use the "REST Client" extension in vscode is easier (for me), but knowing postman could be a good skill to have.

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

# gTile

This gnome extension makes it so you can snap windows to a grid / portion of the screen. It's absolutely necessary for vertical and 4k displays. At this point I actually feel this is a necessary feature in any OS to be productive in the previously mentioned case. (personal preference, obviously)

## Step 1: Install the shell browser integration

I use the [GNOME Shell integration](https://chrome.google.com/webstore/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep) chrome (brave browser) extension to facilitate the installation, which requires the `chrome-gnome-shell` apt package (ubuntu version through 22.10), which has now been renamed to `gnome-browser-connector`.

```bash
# if `lsb-release -a` reports ubuntu version less than 23.04
sudo apt install chrome-gnome-shell
# otherwise
sudo apt install gnome-browser-connector
```

## Step 2: Install the browser extension

The "official" gnome extension page has the [gTile extension](https://extensions.gnome.org/extension/28/gtile/) from the [github](https://github.com/gTile/gTile) page. It can be a bit of a hassle to get installed manually. This is easier.

> ⓘ It may be necessary to set the dconf-editor key `/org/gnome/shell/disable-extension-version-validation` to '**true**' in order to install a 'legacy' version of gTile, especially right after a ubuntu version update. On 23.04 I haven't had to.

Shortcut: `Super`+`Alt`+`<NumpadKeyNumber>` will move a window to a "side" or "quarter" of the screen.

Gnome also has a [Gnome Extensions](https://extensions.gnome.org/) site where you can browse for other Gnome modification extensions.

A Microsoft Windows alternative is [AltDrag](https://stefansundin.github.io/altdrag/) by Stefan Sundin. I can never remember what this one is called, so I list it here.

# Nomachine

Remote desktop access, similar to VNC. 

Download and install [NoMachine](https://www.nomachine.com/)

`sudo apt install ./<downloaded-nomachine-file.deb>`

# Remove Games

`sudo apt purge gnome-2048 aisleriot atomix gnome-chess five-or-more hitori iagno gnome-klotski lightsoff gnome-mahjongg gnome-mines gnome-nibbles quadrapassel four-in-a-row gnome-robots gnome-sudoku swell-foop tali gnome-taquin gnome-tetravex -y & sudo apt autoremove -y`

# Settings

## Accessibility

- Enable Animations: Off

## Appearance

- Dark Mode

## Multitasking

- Workspaces > Fixed number of workspaces: 4
- Multi-Monitor > Workspaces on all displays
- Application switching > Include applications from the current workspace only

# dconf-editor

If not already downloaded from above:

```
sudo apt install dconf-editor
```

## Set a solid color as a background

`/org/gnome/desktop/background/`

- color-shading-type: solid
- picture-uri: ""
- picture-uri-dark: ""
- primary-color: "#222222"

## Set up shortcuts to navigate virtual desktops

> ⓘ move-to-workspace-right will move focused window AND switch...

> ⓘ I have recently added ctrl-alt-arrow in addition to ctrl-windows-arrow. I don't even know what operating system has what defaults any more.

`/org/gnome/desktop/wm/keybindings/`

- switch-to-workspace-right: `['<Ctrl><Super>Right']`
- switch-to-workspace-left: `['<Ctrl><Super>Left']`

## allow VSCode ctrl-alt-shift-up/down line-duplication to work

`/org/gnome/desktop/wm/keybindings/`

- switch-to-workspace-down: []
- switch-to-workspace-up: []
- move-to-workspace-down: []
- move-to-workspace-up: []

## Set window focus to be the window under the mouse pointer.

> ⓘ (This can be done through gnome-tweaks (...but shell is faster))

```
gsettings set org.gnome.desktop.wm.preferences focus-mode 'sloppy'
```

## Disable delaying focus change

Default behavior is to wait until the mouse cursor comes to a complete stop before changing focus.

```
gsettings set org.gnome.mutter focus-change-on-pointer-rest false
```

# fix snap-store glitch

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

# VSCode Setup

I have a separate document that covers my specific [VSCode Setup](./setup-vscode.md).


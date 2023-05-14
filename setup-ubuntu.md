- [Ubuntu Setup](#ubuntu-setup)
  - [Fix time zone](#fix-time-zone)
  - [Rename Sound Card](#rename-sound-card)
  - [Add Software](#add-software)
  - [Snaps](#snaps)
  - [Download Software](#download-software)
  - [Docker Containers](#docker-containers)
  - [VSCode Setup](#vscode-setup)
  - [gTile extension : gTile github](#gtile-extension--gtile-github)
  - [Download Nomachine](#download-nomachine)
- [Remove Software](#remove-software)
  - [Games](#games)
- [Settings](#settings)
  - [Accessibility](#accessibility)
  - [Appearance](#appearance)
  - [Multitasking](#multitasking)
  - [dconf-editor](#dconf-editor)
  - [snap-store glitch](#snap-store-glitch)

# Ubuntu Setup

I have installed ubuntu on three computers. During the second install, I realized that I should have made a step-by-step during the first time. Ah well. The third install went pretty quickly because of this file.

## Fix time zone

`timedatectl set-local-rtc 1`

## Rename Sound Card

`pavucontrol`

## Add Software

`sudo apt install git build-essential gt5 dconf-editor gnome-tweaks htop net-tools vim gnome-shell-pomodoro gimp`

`git config --global user.name "Wayne Fuchs"`

`git config --global user.email "wayne.fuchs@icloud.com"`

## Snaps

- inkscape
- boxy-svg
- discord
- obs-studio
- octave
- docker

## Download Software

| Software                                                       | Note                                                                              |
| -------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [Steam](https://store.steampowered.com/about/)                 | I install this early to get blender installed and verify GPU is working properly. |
| blender                                                        | The easiest linux install of blender that I have found is through Steam.          |
| [brave](https://brave.com/linux/#release-channel-installation) | Instructions are provided to install the browser.                                 |
| [vscode](https://code.visualstudio.com/)                       | Download and install the `.deb`, an update channel is added by the package.       |
| [obs](https://obsproject.com/download#linux)                   | Open Broadcaster Software                                                         |
| [pgAdmin 4](https://www.pgadmin.org/)                          | A management tool for PostgreSQL                                                  |
| [MongoDB Compass](https://www.mongodb.com/products/compass)    | GUI for MongoDB.                                                                  |

## Docker Containers

I run these using `docker-compose.yaml` files, which auto-start on system load.

| Software                                        | Note                                                                                                                                                 |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Penpot](https://penpot.app/)                   | A _really good_ open source replacement for Figma. The docker-compose file is provided with installation instructions on the self-host install page. |
| [Mongodb](https://hub.docker.com/_/mongo)       | The MongoDB database                                                                                                                                 |
| [PostgreSQL](https://hub.docker.com/_/postgres) | The PostgreSQL database                                                                                                                              |
| [Adminer](https://hub.docker.com/_/adminer)     | A database administration panel                                                                                                                      |

> ⚠️ Caution: There may be a better way to write this `docker-compose.yaml` in terms of security, reliability, data persistence, et cetera. This is what has worked (flawlessly) for me, at the time of this writing, for approximately a year. With that said, use at your own risk.

> ⓘ Note: I combine PostgreSQL and MongoDB into a single docker container to keep database stuff together. This may be better to split out separately.

> ⓘ TODO: Figure out nginx proxy with nodejs. I would love to start "containerizing" my applications.

```
version: "3.9"

services:
  # MongoDB service
  mongodb:
    container_name: mongodb
    image: mongo:latest
    restart: always
    networks:
      - dockerdev
    ports:
      - 27017:27017
    volumes:
      - mongodb:/data/db

  # PostgreSQL
  postgres:
    image: postgres
    restart: always
    networks:
      - dockerdev
    environment:
      POSTGRES_PASSWORD: example
    ports:
      - "5432:5432"
    volumes:
      - pgdata:/var/lib/postgresql/data

  # PostgreSQL Configuration Image
  adminer:
    image: adminer
    restart: always
    networks:
      - dockerdev
    ports:
      - 8080:8080

# Data persistence
volumes:
  mongodb: {}
  pgdata: {}

networks:
  dockerdev:
```

`docker compose up -d` to start the containers.

`docker compose down` to stop the containers.

## [VSCode Setup](./setup-vscode.md)

I have a separate document that discusses vscode specific setup.

## [gTile extension](https://extensions.gnome.org/extension/28/gtile/) : [gTile github](https://github.com/gTile/gTile)

This gnome extension makes it so you can snap windows to portions of the screen. It's absolutely necessary for vertical and 4k displays. At this point I actually feel this is a necessary feature in the OS to be productive in the previously mentioned case. (personal preference, obviously)

> ⓘ NOTE: It may be necessary to set the dconf-editor key `/org/gnome/shell/disable-extension-version-validation` to '**true**' in order to install a 'legacy' version of gTile, especially right after a ubuntu version update.

Shortcut: `Super`+`Alt`+`<NumpadKeyNumber>` will move a window to a "side" or "quarter" of the screen.

## Download Nomachine

# Remove Software

## Games

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

## dconf-editor

- /org/gnome/desktop/background/

  - ⓘ Set a solid color as a background
    - color-shading-type: solid
    - picture-uri: ""
    - picture-uri-dark: ""
    - primary-color: "#222222"

- /org/gnome/desktop/wm/keybindings/

  - ⓘ move-to-workspace-right will move focused window AND switch...

    - switch-to-workspace-right: `['<Ctrl><Super>Right']`
    - switch-to-workspace-left: `['<Ctrl><Super>Left']`

  - ⓘ allow VSCode ctrl-alt-shift-up/down line-duplication to work

    - switch-to-workspace-down: []
    - switch-to-workspace-up: []
    - move-to-workspace-down: []
    - move-to-workspace-up: []

- /org/gnome/desktop/background/

  - ⓘ Set window focus to be the window under the mouse pointer. (This can be done through gnome-tweaks (shell is faster))

    - `gsettings set org.gnome.desktop.wm.preferences focus-mode 'sloppy'`

  - ⓘ focus-change-on-pointer-rest: Disable (Following command does the same thing...)

    - `gsettings set org.gnome.mutter focus-change-on-pointer-rest false`

## snap-store glitch

On my system, `snap-store` will get stuck in a state where it can not upgrade because it is running.

The fix is as follows:

```
$ pidof snap-store
4730
$ kill 4730
$ sudo apt update && sudo apt upgrade snap
...
Unpacking snap (2013-11-29-11) ...
Setting up snap (2013-11-29-11) ...
Processing triggers for man-db (2.11.2-1) ...
$
```

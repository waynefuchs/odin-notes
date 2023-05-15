- [Ubuntu Setup](#ubuntu-setup)
  - [Fix time zone](#fix-time-zone)
  - [Rename Sound Card](#rename-sound-card)
  - [Add Software](#add-software)
  - [Snaps](#snaps)
  - [Download Software](#download-software)
  - [gTile](#gtile)
  - [Nomachine](#nomachine)
- [Remove Software](#remove-software)
  - [Games](#games)
- [Settings](#settings)
  - [Accessibility](#accessibility)
  - [Appearance](#appearance)
  - [Multitasking](#multitasking)
  - [dconf-editor](#dconf-editor)
  - [snap-store glitch](#snap-store-glitch)
- [VSCode Setup](#vscode-setup)
- [Docker Container Setup](#docker-container-setup)

# Ubuntu Setup

I have installed ubuntu on three computers. During the second install, I realized that I should have made a step-by-step during the first time. Ah well. The third install went pretty quickly because of this file.

## Fix time zone

`timedatectl set-local-rtc 1`

## Rename Sound Card

I removed this as I can no longer rename my sound card in the new Gnome on Ubuntu, but the `pavucontrol` utility is still useful, so i will mention that. I hope that some day I will be able to rename my sound card again, as I have several audio devices that are exactly the same except one word that is truncated in the drop down list. And it just switches to the wrong one occasionally. Sound in linux is bad, unfortunately. I think it might be getting better, and this is part of the growing pains?

## Add Software

`sudo apt install git build-essential gt5 dconf-editor gnome-tweaks htop net-tools vim gnome-shell-pomodoro gimp`

`git config --global user.name "YOUR NAME HERE"`

`git config --global user.email "your.email@here"`

## Snaps

I try and avoid snaps as much as possible. Here are the ones I use.

- inkscape
- boxy-svg
- discord
- obs-studio
- octave
- docker

And, of course, the nine snaps that ubuntu basically requires and likes to update a few times a day. I really need to investigate switching distros...

## Download Software

| Software                                                               | Note                                                                                          |
| ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| [Steam](https://store.steampowered.com/about/)                         | I install this early to get blender installed and verify GPU is working properly.             |
| blender                                                                | The easiest linux install of blender that I have found is through Steam.                      |
| [Brave Browser](https://brave.com/linux/#release-channel-installation) | Download and install using the provided instructions. I prefer over Google's Chrome, for now. |
| [VSCode](https://code.visualstudio.com/)                               | Download and install the `.deb`, an update channel is added by installing the package.        |
| [obs](https://obsproject.com/download#linux)                           | Open Broadcaster Software                                                                     |
| [pgAdmin 4](https://www.pgadmin.org/)                                  | A management tool for PostgreSQL                                                              |
| [MongoDB Compass](https://www.mongodb.com/products/compass)            | GUI for MongoDB.                                                                              |

## gTile

This gnome extension makes it so you can snap windows to a grid / portion of the screen. It's absolutely necessary for vertical and 4k displays. At this point I actually feel this is a necessary feature in any OS to be productive in the previously mentioned case. (personal preference, obviously)

The website for [gTile extension](https://extensions.gnome.org/extension/28/gtile/) and the associated [github](https://github.com/gTile/gTile) page. It can be a bit of a hassle to get installed. I use the [GNOME Shell integration](https://chrome.google.com/webstore/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep) chrome (brave browser) extension to facilitate the installation.

> ⓘ NOTE: It may be necessary to set the dconf-editor key `/org/gnome/shell/disable-extension-version-validation` to '**true**' in order to install a 'legacy' version of gTile, especially right after a ubuntu version update.

Shortcut: `Super`+`Alt`+`<NumpadKeyNumber>` will move a window to a "side" or "quarter" of the screen.

Gnome also has a [Gnome Extensions](https://extensions.gnome.org/) site where you can browse for other Gnome modification extensions.

A Microsoft Windows alternative is [AltDrag](https://stefansundin.github.io/altdrag/) by Stefan Sundin. I can never remember what this one is called, so I list it here.

## Nomachine

Download and install [NoMachine](https://www.nomachine.com/)

$ `sudo apt install ./<downloaded-nomachine-file.deb>`

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

# VSCode Setup

I have a separate document that covers my specific [VSCode Setup](./setup-vscode.md).

# Docker Container Setup

This section was becoming big enough that I split it out into a separate [Docker Database Setup](databases/Docker-Database-Setup.md) file.

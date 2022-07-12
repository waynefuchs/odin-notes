# Ubuntu Setup

I have installed ubuntu on three computers. During the second install, I realized that I should have made a step-by-step during the first time. Ah well. The third install went pretty quickly because of this file.

# Fix time zone

`timedatectl set-local-rtc 1`

# Add Software

`sudo apt install git build-essential gt5 dconf-editor gnome-tweaks htop net-tools vim`

`git config --global user.name "Wayne Fuchs"`

`git config --global user.email "wayne.fuchs@icloud.com"`

## Snaps

* code (vscode)
* brave
* gimp
* inkscape
* blender
* boxy-svg
* discord
* obs-studio

## VSCode Modules

* Code Spell Checker
* Live Server
* Markdown All In One
* Python
* Pylance

## Download Nomachine

# Remove Software

## Games

`sudo apt purge gnome-2048 aisleriot atomix gnome-chess five-or-more hitori iagno gnome-klotski lightsoff gnome-mahjongg gnome-mines gnome-nibbles quadrapassel four-in-a-row gnome-robots gnome-sudoku swell-foop tali gnome-taquin gnome-tetravex -y & sudo apt autoremove -y`

# Settings

## Accessibility

* Enable Animations: Off

## Appearance

* Dark Mode

## Multitasking

* Workspaces > Fixed number of workspaces: 4
* Multi-Monitor > Workspaces on all displays
* Application switching > Include applications from the current workspace only


# dconf-editor

*WHY* I don't like busy backgrounds.
* /org/gnome/desktop/background/
	* color-shading-type: solid
	* picture-uri: ""
	* picture-uri-dark: ""
	* primary-color: "#222222"

*WHY* I change these because I get muscle-memory confusion while swapping with windows if I don't
* /org/gnome/desktop/wm/keybindings/
	*NOTE* move-to-workspace-right will move focused window AND switch...
	* switch-to-workspace-right: `['<Ctrl><Super>Right']`
	* switch-to-workspace-left: `['<Ctrl><Super>Left']`

	*WHY* The following is to allow VSCode ctrl-alt-shift-up/down line-duplication to work
	* switch-to-workspace-down: []
	* switch-to-workspace-up: []
	* move-to-workspace-down: []
	* move-to-workspace-up: []

*WHY* I like moving the mouse pointer to determine focus, and these settings feel the best to me
* /org/gnome/desktop/background/
	NOTE: This can be done through gnome-tweaks (shell is faster)

	`gsettings set org.gnome.desktop.wm.preferences focus-mode 'sloppy'`
	* focus-change-on-pointer-rest: Disable
	NOTE: Following command does the same thing...

	`gsettings set org.gnome.mutter focus-change-on-pointer-rest false`



# ⓘ Application Launcher

I needed to add some command line options to a few applications in gnome.

I found an [Ask Ubuntu Question](https://askubuntu.com/questions/1255750/how-can-i-tell-which-app-is-coming-from-which-source-in-gnome) that told me where to find the "shortcut" or "launcher" or \*.desktop files.

It turns out that wayland and my rtx 3070 just aren't going to work, though. So I solved my issue by reverting to X11 at the login screen. (bottom right after choosing a user)

# Settings

## Accessibility

New Gnome layout:

- Change: Seeing > Reduce Animation: On

"Older" versions of Gnome:

- Enable Animations: Off

## Appearance

- Dark Mode

## Multitasking

- General > Hot Corner: Disable
- Workspaces > Fixed number of workspaces: 4
- Multi-Monitor > Workspaces on all displays
- Application switching > Include applications from the current workspace only

## Keyboard

View and Customize Shortcuts > Custom Shortcuts > +

> Name: `Terminal`
>
> Command: `/usr/bin/terminator`
>
> Shortcut: `Ctrl` + `Alt` + `T`

# Gnome Settings

Fix things that annoy me in Gnome

```bash
#!/bin/bash

# mousing over a window gives it focus
gsettings set org.gnome.desktop.wm.preferences focus-mode 'sloppy'

# disable delaying focus change
gsettings set org.gnome.mutter focus-change-on-pointer-rest false

# set the desktop background color
gsettings set org.gnome.desktop.background color-shading-type 'solid'
gsettings set org.gnome.desktop.background picture-uri ''
gsettings set org.gnome.desktop.background picture-uri-dark ''
gsettings set org.gnome.desktop.background primary-color '#2d2d30'

# set up desktop switching shortcuts
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-right "['<Control><Alt>Right', '<Control><Super>Right']"
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-left "['<Control><Alt>Left', '<Control><Super>Left']"

# Allow VSCode ctrl-alt-shift-[up/down] line-duplication to work
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-down '[]'
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-up '[]'
gsettings set org.gnome.desktop.wm.keybindings move-to-workspace-down '[]'
gsettings set org.gnome.desktop.wm.keybindings move-to-workspace-up '[]'
```

# gTile

This gnome extension makes it so you can snap windows to a grid / portion of the screen. It's absolutely necessary for vertical and 4k displays. At this point I actually feel this is a necessary feature in any OS to be productive in the previously mentioned case. (personal preference, obviously)

> ⓘ Windows 11 now includes most of the gTile functionality by default without additional configuration, albeit mouse movement is required rather than keyboard shortcuts.

## Step 1: Install the shell browser integration

I use the [GNOME Shell integration](https://chrome.google.com/webstore/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep) chrome extension (in brave browser) to facilitate the installation, which **_also_** requires the `chrome-gnome-shell` apt package (ubuntu version through 22.10), which has now been renamed to `gnome-browser-connector`. See [https://extensions.gnome.org/](https://extensions.gnome.org/) for additional installation / configuration.

## Step 2: Install the browser extension

The "official" gnome extension page has the [gTile extension](https://extensions.gnome.org/extension/28/gtile/) from the [github](https://github.com/gTile/gTile) page. It can be a bit of a hassle to get installed manually. This is easier.

> ⓘ It may be necessary to set the dconf-editor key `/org/gnome/shell/disable-extension-version-validation` to '**true**' in order to install a 'legacy' version of gTile, especially right after a ubuntu version update. On 23.04 I haven't had to.

Shortcut: `Super`+`Alt`+`<NumpadKeyNumber>` will move a window to a "side" or "quarter" of the screen.

Gnome also has a [Gnome Extensions](https://extensions.gnome.org/) site where you can browse for other Gnome modification extensions.

A Microsoft Windows alternative is [AltDrag](https://stefansundin.github.io/altdrag/) by Stefan Sundin. I can never remember what this one is called, so I list it here.

# dconf-editor

I just use gsettings now. But dconf-editor can be handy if you want to look through gnome settings. And I can't ever remember what it's called.

```bash
# Ubuntu
sudo apt install dconf-editor

# Fedora
dconf-editor
```

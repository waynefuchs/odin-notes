<!-- Local Content Links -->

[vscode-setup]: ../vscode-configuration.md
[gnome-setup]: ./gnome-configuration.md
[git-setup]: ../git.md#setup

# Fedora <!-- omit in toc -->

Fedora is a Linux distribution that is the upstream source for CentOS and Red Hat Enterprise Linux (RHEL). There are five editions: `personal computer`, `server`, `cloud computing`, `containerization`, and `internet of things`.

> OUT OF DATE; Update Required
- [Install Brave](#install-brave)
- [Install VSCode](#install-vscode)
- [Generate a ssl key](#generate-a-ssl-key)
  - [Update Git SSH Keys](#update-git-ssh-keys)
  - [Update Server SSH Keys](#update-server-ssh-keys)
- [Install Terminator](#install-terminator)
- [NVIDIA Drivers](#nvidia-drivers)
  - [CUDA](#cuda)
- [Gnome Setup](#gnome-setup)
- [Nodejs 18](#nodejs-18)
- [Git](#git)
- [Software](#software)
  - [blender](#blender)
  - [discord](#discord)
  - [MongoDB Compass](#mongodb-compass)
  - [Docker](#docker)
  - [pgAdmin 4](#pgadmin-4)

# Install Brave

The [Brave Website](https://brave.com/linux/#fedora-centos-streamrhel) has install instructions for Fedora.

# Install VSCode

On the [VSCode Website](https://code.visualstudio.com/docs/setup/linux#_rhel-fedora-and-centos-based-distributions) there are instructions to get vscode up and running. Then, (my) [VSCode Configuration][vscode-setup] for configuration and extensions.

# Generate a ssl key

(for ssh and git)

```bash
ssh-keygen -t rsa -b 4096 -C "{your-email-address}"
```

## Update Git SSH Keys

- Update gitea
- Update github

## Update Server SSH Keys

Just copy / paste it into a new line in the file:

```
~/.ssh/authorized_keys
```

Ensure to remove any old keys previously in use, and update with the new (public) key that was just generated.

- elphaba
- octarine
- database
  - mongodb
  - postgres
- dokku
- penpot
- gitea
- pickle
- orange
- spark

# Install Terminator

I installed it through the 'Software' application.

- Right click in terminal, and choose "Preferences."
  - Uncheck "Extra Styling (Theme dependent)" from the Appearance section.
  - Click on the "Profiles" tab
    - change the font to "Source Code Pro Regular 11"
    - Uncheck "Show titlebar"

# NVIDIA Drivers

There are several guides available that use RPM Fusion repos.

[This is the guide](https://phoenixnap.com/kb/fedora-nvidia-drivers) that I used.

## CUDA

Here's how I got [CUDA working in blender](https://discussion.fedoraproject.org/t/nvidia-cuda-is-not-shown-in-blender/75946/5)

```bash
sudo dnf upgrade
sudo dnf -y install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install akmod-nvidia
sudo dnf install xorg-x11-drv-nvidia-cuda
sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
```

Reboot here. It's required.

Then install CUDA using:

```bash
sudo dnf config-manager --add-repo https://developer.download.nvidia.com/compute/cuda/repos/fedora36/x86_64/cuda-fedora36.repo
sudo dnf clean all
sudo dnf module disable nvidia-driver
sudo dnf -y install --best --allowerasing cuda
```

The next bit in the fedoraproject.org instructions had me confused. You're supposed to type:

```bash
lsmod | grep -e "nvidia|nouveau"
```

And it's supposed to produce:

```
nvidia_drm             73728  8
nvidia_modeset       1220608  11 nvidia_drm
nvidia_uvm           2904064  2
nvidia              56393728  667 nvidia_uvm,nvidia_modeset
video                  65536  1 nvidia_modeset
```

What worked for me, was just dropping the `|nouveau` to verify that it worked. I don't know exactly what I'm supposed to be looking verifying here. Just checking to see if the module is / isn't loaded? I re-ran that lsmod command with `nouveau` instead of `nvidia`, and it didn't return anything. I think that's good.

I looked in my grub config, and it was far different than what he had listed, and the blacklist options were in there to blacklist nouveau in the kernel. So I ran

```bash
sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
```

And rebooted a final time. (And CUDA is not available as an option in blender.)

# Gnome Setup

If you plan on using Gnome extensions, be sure to install the browser connector.

```bash
dnf install gnome-browser-connector
```

Then, see (my) [Gnome Setup][gnome-setup] page.

# Nodejs 18

```bash
# Download and install the repo
curl -sL https://rpm.nodesource.com/setup_18.x | sudo bash -

# Install the required tooling and nodejs 18 (from the repo that was just added)
sudo yum -y install gcc-c++ make nodejs

# Verify node version
node -v
```

# Git

See (my) [Git Setup][git-setup] section.

# Software

Here's the software that I feel is necessary on a day-to-day basis for The Odin Project.

## blender

I typed `blender` in a terminal, and got a prompt to download and install all the required packages.

## discord

```bash
sudo dnf install discord
```

## Sound Device renaming and hiding

1. Install `Extension Manager` in `Software`.
2. In `Extension Manager`, go to the "Browse" tab and search for "quick settings audio" and install `Quick Settings Audio Devices Hider` and `Quick Settings Audio Devices Renamer`.
3. Back in the "Installed" tab, click the "Settings" cog next to "Quick Settings Audio Devices Hider" and toggle off the devices you don't want to show up in the window manager audio picker.
4. Click the cog next to "Quick Settings Audio Devices Hider" and rename the audio devices from nondescript things like "USB Audio Speaker Headphone NG67339 Not Real Device Thing Internal Output" to "DESKTOP SPEAKERS".

## MongoDB Compass

Installed through "Software" / flatpack.

## Docker

Docker has a [set of instructions](https://docs.docker.com/engine/install/fedora/) on their website to install on Fedora.

## pgAdmin 4

```bash
sudo rpm -i https://ftp.postgresql.org/pub/pgadmin/pgadmin4/yum/pgadmin4-fedora-repo-2-1.noarch.rpm
sudo yum install pgadmin4-desktop
```

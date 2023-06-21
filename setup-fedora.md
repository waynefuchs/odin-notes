- [Fedora](#fedora)
- [Install Brave](#install-brave)
- [Install VSCode](#install-vscode)
- [Generate a ssl key](#generate-a-ssl-key)
  - [Update Git SSH Keys](#update-git-ssh-keys)
  - [Update Server SSH Keys](#update-server-ssh-keys)
- [Install Terminator](#install-terminator)
- [NVIDIA Drivers](#nvidia-drivers)
- [Nodejs 18](#nodejs-18)
- [Git](#git)
- [Software](#software)
  - [Cuda](#cuda)
  - [blender](#blender)
  - [discord](#discord)
  - [MongoDB Compass](#mongodb-compass)
  - [Docker](#docker)
  - [Pgadmin](#pgadmin)

# Fedora

In June 2023 I did an update / upgrade on ubuntu and it caused my system not to boot. Combined with the snap issues I've been having, some nvidia driver issues I've been having, and other general frustration with the way that Canonical has been taking, I have decided to give fedora a shot.

# Install Brave

The [Brave Website](https://brave.com/linux/#fedora-centos-streamrhel) has install instructions for Fedora.

# Install VSCode

One the [VSCode Website](https://code.visualstudio.com/docs/setup/linux#_rhel-fedora-and-centos-based-distributions) there are instructions to get vscode up and running. Then, [VSCode Setup](./setup-vscode.md).

# Generate a ssl key

``` bash
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

# Install Terminator

I installed it through the 'Software' application.

- Right click in terminal, and choose "Preferences."
  - Uncheck "Extra Styling (Theme dependent)" from the Appearance section.
  - Click on the "Profiles" tab
    - change the font to "Source Code Pro Regular 11"
    - Uncheck "Show titlebar"

# NVIDIA Drivers

There are several guides available that use RPM Fusion repos.

[This is the one](https://phoenixnap.com/kb/fedora-nvidia-drivers) that I used.

# Nodejs 18

``` bash
# Download and install the repo
curl -sL https://rpm.nodesource.com/setup_18.x | sudo bash -

# Install the required tooling and nodejs 18 (from the repo that was just added)
sudo yum -y install gcc-c++ make nodejs

# Verify node version
node -v
```

# Git

```bash
git config --global user.name "{YOUR NAME HERE}"
git config --global user.email "{your.email@here}"
# If you prefer vim
git config --global core.editor "vim"
# On October 1, 2020, GitHub renamed 'master' to 'main'; the defaultBranch variable will match that locally
git config --global init.defaultBranch main
```

# Software

Here's the software that I feel is necessary on a day-to-day basis for The Odin Project.

## Cuda

Here's how you get [CUDA working in blender](https://discussion.fedoraproject.org/t/nvidia-cuda-is-not-shown-in-blender/75946/5)

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

```
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

What worked for me, was just dropping the `|nouveau` to verify that it worked. I don't know exactly what I'm supposed to be looking for here. I re-ran that lsmod command with `nouveau` instead of `nvidia`, and it didn't return anything. I think that's good.

I looked in my grub config, and it was far different than what he had listed, and the blacklist options were in there to blacklist nouveau in the kernel. So I ran

```
sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
```

And rebooted a final time.


## blender

I typed `blender` in a terminal, and got a prompt to download and install all the required packages.

## discord

```
sudo dnf install discord
```

## MongoDB Compass

Installed through "Software" / flatpack.

## Docker

Docker has a [set of instructions](https://docs.docker.com/engine/install/fedora/) on their website to install on Fedora.

## Pgadmin

```
sudo rpm -i https://ftp.postgresql.org/pub/pgadmin/pgadmin4/yum/pgadmin4-fedora-repo-2-1.noarch.rpm
sudo yum install pgadmin4-desktop
```
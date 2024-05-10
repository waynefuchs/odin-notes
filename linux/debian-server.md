# Debian <!-- omit in toc -->

The second oldest linux distribution, only behind Slackware. A server OS that is as close to "set and forget" as possible.

- [Installation](#installation)
- [Transfer SSH key](#transfer-ssh-key)
  - [Packages](#packages)
  - [Add user to sudo group](#add-user-to-sudo-group)
- [Software](#software)
  - [Docker](#docker)
- [Update MOTD](#update-motd)
- [Mount Samba](#mount-samba)
- [🚧 OS Hardening](#-os-hardening)

# Installation

When going through the install process, there is a screen that shows "Software Selection." Make sure that all graphical packages are deselected, and you want an ssh server and standard system utilities.

- [ ] Debian Desktop Environment
  - [ ] ...Gnome
- [ ] web server
- [x] SSH server
- [x] standard system utilities

# Transfer SSH key

The following script will copy a local ssh key to a remote host's authorized_keys file to set up logging in using ssh keys instead of passwords.

> ⓘ Note: Leave the key prefix field empty if you don't use a key prefix. `ed25519.pub` is the default public key that github recommends, and is what I have included in this script. `id_rsa.pub` is the ssh default. Other users of this script may wish to modify this to suit their needs.

```bash
RED='\033[0;31m'
NC='\033[0m' # No Color
printf "${RED}WARNING:${NC} This script will overwrite the remote 'authorized_keys' file\041\n"
read -p "hostname: " REMOTEHOST
read -p "Enter local key prefix [(KEYPREFIX)ed25519.pub]: " KEYPREFIX
KEYFILE=~/.ssh/
KEYFILE+=$KEYPREFIX
KEYFILE+=ed25519.pub
KEY=`cat $KEYFILE`
printf "\n${RED}*${NC} Transferring local key ($KEYFILE) to remote 'authorized_keys' file:\n"
ssh -T $REMOTEHOST << EOF
  mkdir -p .ssh
  echo $KEY >> .ssh/authorized_keys
  chmod 700 .ssh
  chmod 600 .ssh/authorized_keys
EOF
printf "\n${RED}*${NC} Logging in to remote host using transferred key:\n"
ssh $REMOTEHOST
```

## Packages

Log In with user account, **not root**

```bash
su  # Log in to root from a user account for the sudo group step below
```

```bash
apt install sudo vim htop figlet
```

## Add user to sudo group

```bash
/sbin/adduser $USER sudo
```

Log out and in again to refresh the ssh group, cleanly.

## Remove grub 5 second delay

```bash
sudo sed -i 's/GRUB_TIMEOUT=5/GRUB_TIMEOUT=0/g' /etc/default/grub
sudo update-grub
```

# Software

This is subject to change, but I currently use Debian as a server platform. That means there isn't a whole lot of software to install, mostly just docker images, and then yaml writing and configuring.

## Docker

Docker has a [set of instructions](https://docs.docker.com/engine/install/debian/) on their website to install on Debian.

# Update MOTD

Remove the standard MOTD and replace with a "pretty" motd.

```bash
sudo /usr/bin/sed -i d /etc/motd
sudo rm -f /etc/update-motd.d/10-uname
echo -e '#!/usr/bin/bash\n/usr/bin/figlet -kp < /etc/hostname\nif [[ $HOSTNAME =~ [g|j|p|q] ]]; then /usr/bin/echo ""; fi' |sudo tee /etc/update-motd.d/00-hostname
sudo /usr/bin/chmod +x /etc/update-motd.d/00-hostname
```

# Mount Samba

If you want to mount samba shares, you need to install `cifs-utils`

```bash
sudo apt install cifs-utils
```

Then, add an entry to `/etc/fstab`

```bash
# This will allow read and write..
# NEED TO SET:
#   HOST: octarine.xeno.org
#   SHARE: www-data
#   USERNAME: grok  (this is local user, not samba user)
#   GROUPNAME: grok (this is local group, not samba group)
#   FILEMODE:
#     444: Read Only
#     764: User RWX, Group RW, Other R
//HOST/SHARE	/mount/point/dir		cifs	guest,uid=USERNAME,gid=GROUPNAME,file_mode=FILEMODE	0	0
```

# 🚧 OS Hardening

🚧 TODO

- firewall
- default ssh port change
- ???
- profit

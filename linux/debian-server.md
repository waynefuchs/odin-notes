# Debian <!-- omit in toc -->

The second oldest linux distribution, only behind Slackware.

# 🚧 OS Hardening

Debian ships, by default, with a few questionable security settings. (such as, an enabled root user)

I am in the process of writing a script to harden debian. I'll put it here when I finish.

## sudo

# Software

This is subject to change, but I currently use Debian as a server platform. That means there isn't a whole lot of software to install, mostly just docker images, and then yaml writing and configuring.

## Packages

```
sudo apt install htop figlet
```

## Docker

Docker has a [set of instructions](https://docs.docker.com/engine/install/fedora/) on their website to install on Debian.

# Update MOTD

Remove the standard MOTD and replace with a "pretty" motd.

```bash
sudo /usr/bin/sed -i d /etc/motd
echo -e '#!/usr/bin/bash\n/usr/bin/figlet -kp < /etc/hostname\nif [[ $HOSTNAME =~ [g|j|p|q] ]]; then /usr/bin/echo ""; fi' |sudo tee /etc/update-motd.d/00-hostname
sudo /usr/bin/chmod +x /etc/update-motd.d/00-hostname
```

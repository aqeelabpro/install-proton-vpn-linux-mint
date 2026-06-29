# Proton VPN Desktop Installation (Linux Mint 22 / Ubuntu 24.04)

This guide documents the steps to install the official Proton VPN desktop application.

## 1. Download the Repository Package

Download the latest `protonvpn-stable-release` package from Proton VPN.

Example:

```bash
wget https://repo.protonvpn.com/debian/dists/stable/main/binary-all/protonvpn-stable-release_1.0.8_all.deb
```

Or download it manually from the Proton VPN website.

---

## 2. Install the Repository

```bash
sudo dpkg -i protonvpn-stable-release_1.0.8_all.deb
```

---

## 3. Update Package Lists

```bash
sudo apt update
```

Verify the repository is available:

```bash
apt-cache madison proton-vpn-gnome-desktop
```

You should see available versions.

---

## 4. Install Proton VPN Desktop

```bash
sudo apt install proton-vpn-gnome-desktop
```

---

## 5. If Downloads Timeout (IPv6 Issue)

If installation hangs with messages like:

```
Cannot initiate the connection...
Network is unreachable
```

Force APT to use IPv4:

```bash
echo 'Acquire::ForceIPv4 "true";' | sudo tee /etc/apt/apt.conf.d/99force-ipv4
```

Then run:

```bash
sudo apt update
sudo apt install proton-vpn-gnome-desktop
```

---

## 6. Launch Proton VPN

From the terminal:

```bash
proton-vpn
```

Or launch **Proton VPN** from the application menu.

---

## Useful Commands

Check repository:

```bash
cat /etc/apt/sources.list.d/protonvpn-stable.sources
```

Check available versions:

```bash
apt-cache madison proton-vpn-gnome-desktop
```

Update packages:

```bash
sudo apt update
```

Upgrade system:

```bash
sudo apt upgrade
```

---

## Remove Proton VPN

Remove the desktop application:

```bash
sudo apt purge proton-vpn-gnome-desktop proton-vpn-daemon proton-vpn-gtk-app
sudo apt autoremove
```

Remove the repository:

```bash
sudo apt purge protonvpn-stable-release
sudo rm -f /etc/apt/sources.list.d/protonvpn-stable.sources
sudo rm -f /usr/share/keyrings/protonvpn-stable-archive-keyring.gpg
sudo apt update
```

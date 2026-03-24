# APT Assignment

## Part 1: Understanding APT & System Updates:
### Step 1: running apt version:
after running apt --version
the output was: apt 2.8.3 (amd64)
### Step 2: Update packages:
sudo apt update
This command refreshes the package list from repositories so the system knows about the latest versions.
### Step 3: Upgrade Installed Packages
sudo apt upgrade -y
Difference between update and upgrade:
update : refreshes the list of available packages
upgrade : installs newer versions of installed packages
### Step 4:View Pending Updates
apt list --upgradable
No packages were pending for upgrade, which means the system is fully up to date
<img width="960" height="1128" alt="Capture d&#39;écran 2026-03-24 101909" src="https://github.com/user-attachments/assets/34e26aad-cb37-4878-b2f1-eb2bdfe373da" />
<img width="480" height="40" alt="Capture d&#39;écran 2026-03-24 101942" src="https://github.com/user-attachments/assets/5b9b6627-547e-4968-bf8e-ef5277a351e1" />

## Part 2: Part 2: Installing & Managing Packages:
### 1. Search for a Package:
apt search image editor
i selected:
gimp/noble-updates 2.10.36-3ubuntu0.24.04.1 amd64
  GNU Image Manipulation Program
### 2. View Package Details:
apt show gimp
The package requires several dependencies such as:
- libgimp2.0t64
- gimp-data
- libc6
- libgtk2.0-0t64
- libgegl-0.4-0t64
### 3. Install the Package:
sudo apt install gimp -y
### 4. Check Installed Version:
apt list --installed | grep gimp
#### output:
gimp-data/noble-updates,now 2.10.36-3ubuntu0.24.04.1 all [installed,automatic]
gimp/noble-updates,now 2.10.36-3ubuntu0.24.04.1 amd64 [installed]
libgimp2.0t64/noble-updates,now 2.10.36-3ubuntu0.24.04.1 amd64 [installed,automatic]
## Part 3:Removing & Cleaning Packages:
### 1. Remove the Package:
sudo apt remove gimp -y
#### output
The following packages will be REMOVED:
  gimp
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 20.0 MB disk space will be freed.
(Reading database ... 119971 files and directories currently installed.)
Removing gimp (2.10.36-3ubuntu0.24.04.1) ...
Processing triggers for man-db (2.12.0-4build2) ...
### 2. Purge the Package:
sudo apt purge gimp -y
Difference:
remove: removes the software
purge : removes software + configuration files
<img width="960" height="454" alt="Capture d&#39;écran 2026-03-24 103805" src="https://github.com/user-attachments/assets/f4d87906-ac1e-4393-adb5-9c782ebe5c35" />

### 3. Remove Unused Dependencies:
sudo apt autoremove -y
This removes unnecessary dependencies that are no longer needed.
### 4. Clean Package Cache:
sudo apt clean
This deletes downloaded package files to free disk space.
## Part 4: Managing Repositories & Troubleshooting:
### 1. List APT Repositories:
cat /etc/apt/sources.list
#### output
Ubuntu sources have moved to the /etc/apt/sources.list.d/ubuntu.sources
file, which uses the deb822 format. Use deb822-formatted .sources files
to manage package sources in the /etc/apt/sources.list.d/ directory.
See the sources.list(5) manual page for details.

This file contains repository URLs used by the system to download packages.
### 2. Add Universe Repository:
sudo add-apt-repository universe 
sudo apt update

The universe repository contains community-maintained open-source software.
### 3. Simulate Installation Failure:
sudo apt install fakepackage
E: Unable to locate package fakepackage
### 4. Troubleshooting:
i will:
Check package name spelling
Run sudo apt update
Use apt search to find correct package
Ensure repositories are enabled

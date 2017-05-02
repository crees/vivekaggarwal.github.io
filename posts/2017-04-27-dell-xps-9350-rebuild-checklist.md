# Dell XPS 13 (9350) Rebuild Checklist

What follows is my checklist to carry out a clean install of Windows 10 on a Dell XPS 13 9350.

> **WARNING**: 
> **I take no responsibility for anything that may go wrong with your laptop.**

## Before starting
- **Check**: the *Laptop* is working and plugged in with a charger
- **Check**: there is a working *USB* available with at least 8GB free
- **Download**: [Windows 10 ISO](https://www.microsoft.com/en-gb/software-download/windows10) (multiple editions)
- **Download**: [Intel Rapid Storage Technology](https://downloadcenter.intel.com/download/26730/Intel-Rapid-Storage-Technology-Intel-RST-?v=t) (RST) Driver
- **Download**: latest version of [Dell XPS 13 9350 CAB file](http://en.community.dell.com/techcenter/enterprise-client/w/wiki/11633.xps-13-9350-windows-10-driver-pack)
- **Download**: [Rufus](https://rufus.akeo.ie/) ISO Creator

## Preparation 
- **Format**: the USB Drive with FAT32 filesystem (ie. USB drive on `D:\`)
- **Create**: bootable Windows 10 installation media using _ISO Creator_ (_**Note**: to install a different edition of Windows to that which comes with the Dell machine, you'll need to go down the [`ei.cdf`](https://community.dell.com/thread/23933-clean-install-of-windows-10-pro) or `PID.txt` route_)
- **Create**: folders on the USB
    - `D:\drivers\RST`
    - `D:\drivers\cab`
- **Extract**: the RST drivers to the `D:\drivers\RST` folder
- **Extract**: the Dell CAB file by
    - opening a shell in the folder the CAB file has been downloaded to
    - running the following command `Expand –F:* *.cab D:\drives\cab`

## Installation
### Windows
- **Restart** laptop (F12) and begin Windows installation with `Custom Install Windows Only (Advanced)`
- **Load** RST Driver from `D:\Drivers\RST` to show hard drive
- **Partition** drive to use all space (delete existing and re-apply full drive space)
- **Complete** Windows installation

### CAB drivers
- **Open** an *Elevated* Command Prompt and navigate to `D:\drivers\cab` 
- **Execute** `for /f %i in (‘dir /b /s *.inf’) do pnputil.exe -i -a %i`
- **Restart**

## Post Install
- **Update** Windows
- **Install** Office
- **Enable** Developer Mode
- **Install** Windows Subsystem for Linux (WSL)
- **Install** [Software](http://ninite.com)
    - Chrome
    - Spotify
    - 7-Zip
    - Paint .NET
    - Notepad++
    - Vistual Studio Code
    - Dropbox
- **Configure** Mail, Start Menu, Taskbar
- **Login** to Windows account
- **Install** Windows Store Applications
    - Slack
    - Wunderlist

## WSL Configuration
### **Update** WSL
```
sudo su
apt-get -y update
apt-get -y upgrade
exit
```
### **Install** [Node](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions)
```
sudo su
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
apt-get install -y nodejs npm
exit
```
### **Install** Python
```
sudo su
apt-get install -y python-pip python-dev
pip install --upgrade pip
exit
```

## Visual Studio Code Configuration
- **Configure**: Shell to using Bash.exe (CTRL-SHIFT-P > Shell -> Bash)

###### Sources
1. [Dell Instructions to configure CAB files](http://www.dell.com/support/article/us/en/4/SLN209380/how-to-configure-driver-installation-from-cab-file-s--in-windows--vista--7--8--and-windows-server--2008-2012-?lang=EN)
1. [Clean Install Guide on Answers @ Microsoft](https://answers.microsoft.com/en-us/windows/wiki/windows_10-windows_install/clean-install-windows-10/1c426bdf-79b1-4d42-be93-17378d93e587)
1. [Manual Install Dell Driver Pack](http://www.1337admin.org/tutorials/manual-installation-of-a-dell-driver-pack-on-a-local-machine/)
1. [Reddit Windows 10 Clean Install Guide](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)

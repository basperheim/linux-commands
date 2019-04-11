# Linux Commands Cheat Sheet
## A cheat sheet for Linux commands, and how to install some packages and drivers.

### Basic Commands:
Find out your user name:
```bash
whoami
```

#### Get full path to current directory:
```bash
pwd
```

#### List files in current directory:
```bash
ls
```

#### List all files AND their respective attributes:
```bash
ls -l@
```

#### Hidden files start with a period ("."). List all files and hidden files:
```bash
ls -a
```

#### Clear terminal screen:
```bash
clear
```

#### Go back one directory level:
```bash
cd ..
```

#### Delete a file:
```bash
sudo rm /path/to/file/some-file.txt
```

#### Delete a directory AND ALL ITS CONTENTS (BE CAREFUL WITH THIS ONE):
```bash
sudo rm -rf /path/to/directory
```

#### Remove a directory:
```bash
rmdir /path/to/some/dir
```

#### Create a new file:
```bash
touch /path/to/some/directory/new-file.py
# OR this for new file in 'pwd':
touch new-file.txt
```

#### Locate a file (Linux only):
```bash
locate some-file-name
```

#### MOVE a file or folder using "mv":
```bash
sudo mv /path/to/file/some-file.txt /new/path/location
```

#### ALSO use "mv" to RENAME a file:
```bash
sudo mv old-file-name.txt new-file-name.txt
```

#### View the "manual" for any command:
```bash
man {SOME_COMMAND}
# for example: man history
# Press CTRL+Z to exit
```

#### Enter Python Interpreter:
```bash
python3
or
python
Press CTRL+Z to exit
```

#### "History" Command and Grep to find specific command you did before:
```bash
history | grep {SOME_KEYWORD}
```

#### Kill Processes:
```bash
ps aux | grep -i apt
sudo kill -9 <process id>
```



### Unzip Tar Archives:
```bash
tar xzf file.tar.gz
tar xjf file.tar.bz2
tar xzvf file.tar.gz

### Tweak CPU on Linux
```bash
sudo apt install aptitude
sudo aptitude install cpufrequtils
sudo cpufreq-set -f 2000
indicator-cpufreq
for x in /sys/devices/system/cpu/*/cpufreq/; do echo 800000 | sudo tee $x/scaling_min_freq; done
cpufreq-info
sudo cpufreq-set -f `cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq`
```

### Install Snap Package Manager
```bash
sudo apt update
sudo apt upgrade -y
sudo apt install snapd
sudo apt purge snapd
sudo apt install snapd
snap find "program name"
sudo snap install {PROGRAM}
```

### Install PHP 7.3
https://thishosting.rocks/install-php-on-ubuntu/

### Install Lua 5.3 on Linux Debian
```bash
mkdir lua_build
cd lua_build
wget http://www.lua.org/ftp/lua-5.3.4.tar.gz
sudo tar -zxf lua-5.3.4.tar.gz
cd lua-5.3.4
sudo make linux test
sudo make install
```

### Install the LÖVE 2D Game Engine for Lua
* [Love 2D Website](https://love2d.org/wiki/Getting_Started)
```bash
sudo add-apt-repository ppa:bartbes/love-stable
sudo apt-get update
```
or
```bash
sudo apt install love
```

### Python and Lua Links:
* https://eev.ee/blog/2016/04/30/embedding-lua-vs-python/
* https://stackoverflow.com/questions/4527261/how-could-i-embed-lua-into-python-3-x
* http://labix.org/lunatic-python
* https://pypi.org/project/lupa/0.9/

### Install GO Language v1.12
https://golang.org/dl/
```bash
sudo wget https://dl.google.com/go/go1.12.1.linux-amd64.tar.gz
sudo tar -xvf go1.12.1.linux-amd64.tar.gz
sudo mv go /usr/local
export GOROOT=/usr/local/go
export GOPATH=/home/benji/Desktop/repos/GoProject
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
```

### Create Bootable Linux USB ON Linux:
[Ask Ubuntu - Create a live USB](https://askubuntu.com/questions/233712/how-to-create-a-live-usb-for-ubuntu-from-a-lubuntu-system)

#### Startup Disk Creator Method
```bash
sudo apt-get install usb-creator-gtk
```

#### UNETBOOTIN Method:
```bash
sudo add-apt-repository ppa:gezakovacs/ppa
sudo apt-get update
sudo apt-get install unetbootin
```

### Restart Apache Server localhost
```bash
/etc/init.d/apache2 restart
# or
sudo /etc/init.d/apache2 restart
```

### Disable Touchpad
```bash
xinput set-prop <id> "Device Enabled" 0
```

### Install Aptitude:
```bash
sudo apt install aptitude
sudo aptitude install cpufrequtils
```


### Install Firefox
```
sudo apt-get install firefox
```

### Install Chrome
```bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome*.deb
```

#### Configure Pantheron/Gnome Desktop Settings:
```bash
gsettings set org.pantheon.files.preferences single-click false
gsettings set org.gnome.desktop.interface text-scaling-factor 1.2
gsettings set org.pantheon.terminal.settings unsafe-paste-alert false
gsettings set org.gnome.desktop.notifications show-banners false
```

### Fix Bad Installation of Skype
* Uninstall Skype:
```bash
sudo service bluetooth restartSKYPE
sudo apt remove skype
sudo apt remove skypeforlinux.
```

#### Install cURL Library:
```bash
sudo apt install apt-transport-https curl
```

#### Reinstall Skype
```bash
curl https://repo.skype.com/data/SKYPE-GPG-KEY | sudo apt-key add -
echo "deb [arch=amd64] https://repo.skype.com/deb stable main" | sudo tee /etc/apt/sources.list.d/skype-stable.list.
sudo apt update
sudo apt install skypeforlinux
```


[Ask Ubuntu - Fix Bluetooth Issues](https://askubuntu.com/a/864312)
```bash
sudo service bluetooth restart
<cite>"I've edited the `/etc/bluetooth/audio.conf` file: `sudo -H gedit /etc/bluetooth/audio.conf` and add this line in the end of it: Disable=Headset. Users on Ubuntu 17.04 and above may not have `audio.conf`, but can instead use `main.conf`."</cite>

__PEEK:__
```bash
sudo add-apt-repository ppa:alexlarsson/flatpak
sudo apt update
sudo apt install flatpak
flatpak install --user https://flathub.org/repo/appstream/com.uploadedlobster.peek.flatpakref
flatpak run com.uploadedlobster.peek
flatpak update --user com.uploadedlobster.peek
https://github.com/phw/peek
```

### UNLOCK READ-ONLY SDCARD or USB
[Ask Ubuntu - SDB Read Write](https://askubuntu.com/questions/409520/unable-to-open-dev-sdb-read-write-read-only-file-system)

```bash
sudo hdparm -r0 /dev/
```

### FAT32 Format using Terminal
Use `fdisk` to find all drives:
```bash
sudo fdisk -l
```
Or use `df` to show volumes:
```bash
df
```
The drive will be: `/dev/sdb{X}`
```bash
sudo umount /dev/sdb{X}
```

Un-mount the drive:
```bash
sudo mkfs.vfat -n 'LINUX_BOOT' -I /dev/sdb{X}
# ..or
sudo mkfs.vfat -I /dev/sdb{X}
```

Format the drive as FAT32:
```bash
ls -1 /dev > ~/before.txt
ls -1 /dev > ~/after.txt
diff ~/before.txt ~/after.txt
```

### INSTALL EXFAT UBUNTU
```bash
sudo apt install exfat-fuse exfat-utils
```

### SLOW DOWN CPU
```bash
for x in /sys/devices/system/cpu/*/cpufreq/; do echo 1200000 | sudo tee $x/scaling_max_freq; done
sudo apt install aptitude
sudo aptitude install cpufrequtils
```

### INSTALL ATOM IDE ON UBUNTU 18
[Atom IDE Menu Font Not-Visible](https://github.com/atom/atom/issues/18535)
```bash
wget -O atom-amd64.deb https://atom.io/download/deb
```

### INSTALL ATOM IDE ON LINUX MINT
```bash
sudo add-apt-repository ppa:webupd8team/atom
sudo apt update
sudo apt install atom
```

### INSTALL ZOOM
```bash
wget -c https://zoom.us/client/latest/zoom_amd64.deb
sudo apt-get install libxcb-xtest0
sudo dpkg -i zoom_amd64.deb
```

### Install Chromium
```bash
sudo apt install chromium-browser
```

### Install Linux Wireless Drivers for Macbook Pro
#### Hardware Support:
<cite>"BROADCOM 4360 comes with two different chips: 14E4:4360 NOT SUPPORTED and 14E4:43A0 SUPPORTED"</cite>
Check for hardware support:
```bash
lspci -vnn | grep -i net
```

#### Install Linux wireless drivers on a Macbook:
```bash
sudo apt-get update
sudo apt-get install linux-headers-$(uname -r|sed 's,[^-]*-[^-]*-,,') broadcom-sta-dkms
OR:
sudo apt-get install --print-uris linux-headers-$(uname -r|sed 's,[^-]*-[^-]*-,,') broadcom-sta-dkms
sudo modprobe -r b44 b43 b43legacy ssb brcmsmac
modprobe wl
```
[YouTube video explanation](https://www.youtube.com/watch?v=7Xt9hd7H9lk)
Apple MD212LL/A (Late-2012)

#### Install MacBook Fan Control:
```bash
sudo nano /etc/mbpfan.conf
```

#### FIX CORRUPTED SD or USB:
```bash
sudo fsck /dev/sdc1
```


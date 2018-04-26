##Postman
https://www.getpostman.com/docs/v6/postman/launching_postman/installation_and_updates
https://app.getpostman.com/app/download/linux64?_ga=2.126085774.208107287.1524496452-1290295698.1524496452
https://blog.bluematador.com/posts/postman-how-to-install-on-ubuntu-1604/?utm_source=hootsuite&utm_medium=twitter&utm_campaign=


wget https://dl.pstmn.io/download/latest/linux64 -O postman.tar.gz
sudo tar -xzf postman.tar.gz -C /opt
rm postman.tar.gz
sudo ln -s /opt/Postman/Postman /usr/bin/postman


cat > ~/.local/share/applications/postman.desktop <<EOL
[Desktop Entry]
Encoding=UTF-8
Name=Postman
Exec=postman
Icon=/opt/Postman/resources/app/assets/icon.png
Terminal=false
Type=Application
Categories=Development;
EOL

##CapsLock2Esc
https://blog.csdn.net/mzqj_WPF/article/details/41120175
解决方案


1、以下代码保存为 CapsLock2Esc.reg 文件；
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]
"Scancode Map"=hex:00,00,00,00,00,00,00,00,03,00,00,00,3a,00,01,00,01,00,3a,00,00,00,00,00

2、双击该文件，弹出框，选“是”；

3、重启系统，完成。












## No password use sudo
$sudo visudo
# remove #
%wheel        ALL=(ALL)       NOPASSWD: ALL

## VIM
$ sudo dnf -y install vim-enhanced
## .vimrc

## Input method
$ sudo dnf install fcitx fcitx-configtool fcitx-table-chinese -y
## PS: Confirm fcitx autostart with system. if not:
### Print fcitx version
$ fcitx --version  
### Go to: http://download.fcitx-im.org or https://github.com/fcitx/fcitx/releases find the fcitx-autostart.desktop.in file  from /fcitx-[version]/data/ directory and rename to fcitx-autostart.desktop, then copy that to /etc/xdg/autostart/   reboot system.  
### 
$ cd fcitx-[version]/data/script
$ sudo chmod 775 fcitx-autostart
$ sudo cp fcitx-autostart  /usr/bin/
$ cd ..
$ sudo cp fcitx-autostart.desktop.in /etc/xdg/autostart/fcitx-autostart.desktop
$ cp fcitx-autostart.desktop.in  ~/.config/autostart/fcitx-autostart.desktop
$ sudo vim /etc/enviroment
 export GTK_IM_MODULE=fcitx
 export QT_IM_MODULE=fcitx
 export XMODIFIERS=@im=fcitx

## Yum Repos
###  Backup old repos
$ cd /etc/yum.repos.d/
$ sudo mv fedora.repo fedora.repo.bak
$ sudo mv fedora-updates.repo fedora-updates.repo.bak

### Go to link: https://lug.ustc.edu.cn/wiki/mirrors/help/fedora
### Download: fedora-updates-ustc.repo and fedora-ustc.repo
$ sudo mv ~/Downloads/*.repo /etc/yum.repos.d/
$ sudo dns makecache

### RPMFusion
$ sudo rpm -Uvh http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-26.noarch.rpm
$ sudo rpm -Uvh http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-26.noarch.rpm

### REMI
 $ sudo rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm

### epel
$ sudo dnf install epel-release
#### when above comand not work try:
$ sudo rpm -Uvh http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-10.noarch.rpm

$ sudo dnf repolist
$ sudo dnf makecache

## Gnome Tweak Tool
$ sudo dnf install gnome-tweak-tool

## Swap CapsLock  Escape Keys
Open Gnome Tweak Tool  >>  Typing >> Caps Lock behavior >>  Check Swap ESC and Caps Lock
Details: <Linux: Swap CapsLock Escape Keys 交换>

## Adjust Window Maximize and Minimize
Tweaks >>  Windows Tilebar Buttons  
### Toggle Maximize and Minimize Off to On

# Install windows fonts 
$ sudo dnf install font-manager
Font Mananger >> Browse to Manage   Click  `+` Button select dir include window fonts (Copy from window 10)

# Adjust windows fonts
Tweaks  Tool >> Fonts
Widow Titles = Segoe UI Bold
Interface = Segoe UI Regular
Documents = Segoe UI Regular

## Check for updates
$sudo dnf update
### Reboot system and Select new Kernel Login
## Remove old kernel
$sudo rpm -qa |grep kernel
$sudo dnf remove [old kernel name]

# Lantern VPN go to: <Install lantern in fedora 27>

## Make go1.4 from source
$ cd ~
$ git clone https://github.com/golang/go.git go1.4
$ cd go1.4
$ git checkout -b 1.4.3 go1.4.3
$ cd src
$ ./all.bash
### failure message: runtime/cgo(.text): unexpected relocation type 298
$ CGO_ENABLED=0 ./all.bash

## Make go from getlantern fork
$ git clone https://github.com/getlantern/go.git
$ cd go/src
$ ./all.bash

## Setting Profie
$ sudo vim /etc/profile
export GOROOT=$HOME/go
export GOBIN=$GOROOT/bin
export PATH=$PATH:$GOBIN

## Install NodeJs
### Go to: https://nodejs.org/en/download/package-manager/
$ curl --silent --location https://rpm.nodesource.com/setup_8.x | sudo bash -
$ sudo dnf -y install nodejs
$ sudo dnf install gcc-c++ make
# or: $ sudo dnf groupinstall 'Development Tools
$ sudo npm i -g nrm gulp-cli
$ sudo nrm use taobao
$ vi ~/.npmrc
registry=https://registry.npm.taobao.org
sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
phantomjs_cdnurl=http://npm.taobao.org/mirrors/phantomjs
ELECTRON_MIRROR=http://npm.taobao.org/mirrors/electron/

## Make lantern
$ source /etc/profile
$ git clone https://github.com/getlantern/lantern
$ sudo dnf install gtk3-devel libappindicator-devel libappindicator-gtk3-devel
$ source /etc/profile
$ make lantern
$ ./lantern

## Setting Profie
$ sudo vim /etc/profile
export LANTERN=$HOME/lantern
export PATH=$PATH:$LANTERN

# Install software
## Chrome

## Gnome Theme
### Download ocs-url-3.0ocs-url-3.0.2-1.fc20.x86_64.rpm from https://www.gnome-look.org/p/1136805/
$ sudo dnf install ocs-url-3.0ocs-url-3.0.2-1.fc20.x86_64.rpm
### Other GTK3 Theme and Gnome shell theme what you like
$sudo dnf install chrome-gnome-shell -y

## Docker
https://docs.docker-cn.com/engine/installation/linux/docker-ce/fedora/#安装-docker-ce


===================================
# JDK
# Remove open-JDK
$ rpm -qa |grep java
$ sudo dnf remove java-1.8.0-openjdk-headless
$ sudo dnf install jdk-8u144-linux-x64.rpm -y
$ sudo cp ~/Downloads/java.sh /etc/profile.d
$ sudo vim /etc/profile.d/java.sh
## Change JAVA_HOME=/usr/java/jdk1.8.0_[your java update version]
$ source /etc/profile.d/java.sh
$ java -versoin

# Apache Maven
https://maven.apache.org/download.cgi
$ cd /usr/local/
$ sudo wget http://mirror.bit.edu.cn/apache/maven/maven-3/3.5.0/binaries/apache-maven-3.5.0-bin.zip
$ sudo unzip apache-maven-3.5.0-bin.zip
$ sudo mv apache-maven-3.5.0 maven
## Copy maven.sh to /etc/profile.d/
$ sudo cp ~/Download/maven.sh /etc/profile.d/
## Set  .m2 and mirrors
$ sudo cp ~/Downloads/settings.xml /usr/local/maven/conf
$ sudo cp ~/Downloads/settings.xml ~/.m2

# Ngrok Client
<CentOS6.x  ngrok 编译/安装/使用>
Create start.sh shell scripts
$ vim start.sh
ngrok -config=ngrok.cfg -subdomain web -proto=http 8080
$ sudo chmod 755 start.sh

## Webstorm
https://www.jetbrains.com/webstorm/
$ tar -zxvf idea-IU-2017.2.5.tar.gz
$ mv WebStorm-172.4155.35/ WebStorm
$ cd WebStorm
$ ./bin/webstorm.sh
### PS: check all users.
### Plugins
.ignore
ideaVIm
Relative Line Number
CodeGlance

## Idea
https://www.jetbrains.com/idea/download/index.html#section=linux
$ tar -zxvf WebStorm-2017.2.4.tar.gz
$ mv idea-IU-172.4343.14/ idea-IU
.ignore
ideaVIm
Relative Line Number
CodeGlance
lombok

## Atom
### Download from https://atom.io/
$ sudo dnf install atom.x86_64.rpm -y

## Pinta
### Edit Images and paint digitally 





















---
title: Manjaro
date: 2022-07-15
tags: 
    - linux
    - manjaro
categories: 
    - linux
---

镜像源修改

```
# change to pacman china mirrors
sudo pacman-mirrors -i -c China -m rank
```

中文输入法安装

```
# Install sogoupinyin
sudo pacman -S fcitx-im fcitx-configtool fcitx-googlepinyin
sudo pacman -S fcitx-sogoupinyin

nano ~/.xprofile

# export LC_ALL=zh_CN.UTF-8 # 这个是控制系统界面的语言类型的，这一行意味着显示中文。这里还是注销了吧。
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS=“@im=fcitx”
```

pacman

```
pacman -S [packageName]
pacman -Rcns [packageName]
pacman -Ss keyword
pacman -Qs keyword
#将在同步包数据库后再执行安装。
pacman -Sy package_name 
#安装本地包，其扩展名为pkg.tar.gz或pkg.tar.xz
pacman -U local_package_name
#安装一个远程包（不在 pacman 配置的源里面）
pacman -U url
```

推荐软件安装

```
DBeaver
wechat-uos
dingtalk-bin
wps
vscode
  remote-ssh
  remote-container
  docker
  jira and bitbucket
latte-dock （类似苹果的悬浮工具栏）
github-desktop
SmartGit (社区版每次使用都需要等待30s)
gitgb
```

软件安装方式

```
安装方式一：
sudo pacman -S yay
sudo pacman -S snapd
yay -S teams
yay -S dingtalk-bin
yay -S sqlectron-gui #轻量级sql-gui
yay -S docker && systemctl status docker
sudo snap install dbeaver-ce 

安装方式二：
wget安装包，再用pacman命令安装
# Todesk https://www.todesk.com/linux.html
wget https://dl.todesk.com/linux/todesk_4.1.0_x86_64.pkg.tar.zst
sudo pacman -U todesk_4.1.0_x86_64.pkg.tar.zst

安装方式三：
手动下班安装包，在用tar -xzvf解压，再打开文件启用安装程序
# Download the phpstorm from https://www.jetbrains.com/zh-cn/phpstorm/download/other.html
# cd Download Path
cd /home/leo/Program/
# 解压
tar -xzvf PhpStorm-211.7628.25.tar.gz
cd $path
/bin/phpstorm.sh

# Add phpstorm desktop
sudo nano /usr/share/application/phpstorm.desktop
# Input the setting code below
"""
[Desktop Entry]
Name=Phpstorm
GenericName=PHP Editor
Exec=/home/leo/Program/PhpStorm-211.7628.25/bin/phpstorm.sh
Icon=/home/leo/Program/PhpStorm-211.7628.25/bin/phpstorm.svg
Type=Application
StartupNotify=true
Categories=Developmemt;IDE;
MimeType=text/markdown;text/x-markdown;
"""

# Add PATH
echo $path
sudo nano /etc/profile
"""
export PATH=$PATH:~/Program/PhpStorm-211.7628.25/bin/
"""
source /etc/profile
echo $path

安装方式四：
Debtap用于将debian的软件安装包，转化成manjaro的软件安装包格式，再用pacman进行安装，但并非所有的deb包都可以安装成功，并且过程比较慢。
```

Antojump

```
cd ~/Program/Installer
git clone https://github.com/wting/autojump.git
cd autojump
./install.py
vim ~/.zshrc
source ~/.zshrc
autojump -v
```

设置命令行的别称

```
vim ~/.zshrc
alias ll='ls -l'
```

SSH Error:

```
SSH Error:
ssh erp-staging.gaatu.com
sign_and_send_pubkey: no mutual signature supported
ubuntu@erp-staging.gaatu.com's password:
ubuntu@erp-staging.gaatu.com: Permission denied (publickey,password).

Solution: 
set the ~/.ssh/config
PubkeyAcceptedKeyTypes=+ssh-rsa
or
PubkeyAcceptedKeyTypes=+ssh-dss
```

Keyring

```
After forgetting the password to the “Default keyring”, resolved the issue as follows:

1.Navigate to local Home folder in file manager and displayed hidden folders with Ctrl+H
2.Navigate to /home/.local/share/keyrings/
3.Deleted all files with “.keyring” file ending.
4.Then launched application to receive a prompt to create a new password for the Default keyring.
5.Specified the new password and confirmed.
Now can use apps that require access to the Default keyring.

cd /home/.local/share/keyrings
rm *.keyring
```

Debtap: 

```
Install debtap:
  yay -S debtap sudo debtap -u
Convert .deb packages Into Arch Linux Packages using debtap:
  debtap packagename.deb
install the package in the system:
  sudo pacman -U package-name
```




---
id: 163
title: 开发必备：Mackup 将你的开发工具配置同步到云端
date: 2016-02-19T22:34:26+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=163
permalink: /2016/02/19/development-mackup-synchronize-your-development-tools-to-the-cloud/
views:
  - 9
categories:
  - Mac
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

## 简介

最近有朋友推荐 [Mackup](https://github.com/lra/mackup) 来备份常用工具的配置文件，着实给开发者们省心了。

> 众所周知，每换一台机器，或者重装软件后，配置就成了体力活。虽然自己写了一套脚本把常用的配置文件自动复制到 Dropbox 目录里，但维护脚本这事儿就有些复杂了。 

Mackup 正是为了解决这个问题而来，他不仅备份配置文件，还将插件等其他内容一起备份到 Dropbox、Google Drive 等等。目前只支持 OS X 和 Linux 系统。

## 安装

<pre class="prettyprint" ><code># 通过 Homebrew (http://brew.sh/) 安装brew install mackup

# 通过 Python pip 安装
pip install mackup
</code></pre>

## 使用

<pre class="prettyprint" ><code># 备份到 Dropbox
mackup backup

# 还原备份的文件
mackup restore

# 取消备份，所有文件恢复到未备份前的状态
mackup uninstall

# 列出 mackup 可备份的程序
mackup list

# 查看命令帮助
mackup -h
</code></pre>

## 原理

### 备份原理

将默认的配置文件全部移动到备份目录，然后通过软连接重定位配置文件的位置：

  1. `cp ~/.gitconfig ~/Dropbox/Mackup/.gitconfig`
  2. `rm ~/.gitconfig`
  3. `ln -s ~/Dropbox/Mackup/.gitconfig ~/.gitconfig`

### 还原原理

将 Dropbox 里的备份配置软链到实际位置：

`ln -s ~/Dropbox/Mackup/.gitconfig ~/.gitconfig`

## 当前支持的软件

默认是将所有在下列列表的程序进行备份，你也可以 [自定义](https://github.com/lra/mackup/tree/master/doc) 哪些要备份，哪些不备份。

<pre class="prettyprint" ><code>ack
adium
adobe-camera-raw
adobe-lightroom
appcode-2
arara
aria2c
asciinema
aspell
astyle
atom
auskey
awareness
aws
bartender
bash
bash-it
bettersnaptool
bettertouchtool
bibdesk
boto
brackets
bundler
byobu
caffeine
cartographica
charles
chef
chicken
clementine
clipmenu
cloudapp
coda-2
colloquy
concentrate
controlplane
cord
curl
cyberduck
dash
deal-alert
default-folder-x
divvy
dolphin
droplr
emacs
enjoyable
exercism
expandrive
fantastical
feeds
filezilla
fish
flux
fontexplorer-x
forklift-2
geektool
git
git-hooks
gitbox
gmail-notifr
gnupg
go2shell
hands-off
hazel
heroku
hexels
htop
i2cssh
intellijidea-12
irssi
iterm2
itunesscripts
janus
jshint
karabiner
keka
keybase
keymo
keyremap4macbook
latexit
launchbar
liftoff
light-table
limechat
littlesnitch
livestreamer
mackup
macosx
macvim
magic-launch
magicprefs
mailplane
menumeters
mercurial
mercurymover
messages
moom
mou
mpd
mpv
mysql
nano
ncmpcpp
newsbeuter
ngrok
nvalt
nvpy
oh-my-zsh
omnifocus
omnigraffle
pastebot
path-finder
pear
pentadactyl
perl
phoenix
phpstorm-6
phpstorm-7
phpstorm-8
pip
pokerstars
popclip
pow
prezto
processing
pypi
quicklook
quicksilver
r
rails
rtorrent
ruby
ruby-version
rubymine
s3cmd
sabnzbd
sbcl
sbt
scenario
screen
scripts
seil
selfcontrol
sequel-pro
shsh-blobs
shuttle
sizeup
skim
skitch
skype
slate
slogger
soulver
sourcetree
spark
spectacle
spotify
ssh
stata
sublime-text-2
sublime-text-3
subversion
superduper
teamocil
textmate
textual
tig
tmux
tmuxinator
tower
tower-2
transmission
transmit
twitterrific
ventrilo
vim
vimperator
viscosity
wget
witch
x11
xchat
xcode
xemacs
xld
zsh
</code></pre>

## 相关链接

Mackup 官网： <https://github.com/lra/mackup>
  
配置同步目录： <https://github.com/lra/mackup/blob/master/doc/README.md>
  
自定义要备份的程序： <https://github.com/lra/mackup/tree/master/doc>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->
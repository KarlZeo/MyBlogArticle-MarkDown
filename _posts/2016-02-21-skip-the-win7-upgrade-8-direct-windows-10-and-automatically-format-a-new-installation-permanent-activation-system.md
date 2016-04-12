---
id: 298
title: 跳过从Win7/8升级，直接格式化全新安装 Windows 10 并自动永久激活系统
date: 2016-02-21T21:51:53+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=298
permalink: /2016/02/21/skip-the-win7-upgrade-8-direct-windows-10-and-automatically-format-a-new-installation-permanent-activation-system/
dsq_thread_id:
  - 4598476957
views:
  - 8
categories:
  - Windows
---
  1. 下载 Windows 10 系统的 ISO 镜像
  2. 在你当前的 Win7 / Win 8 / 8.1 系统中，使用 DaemonTools 或右键选择装载 Win10 的镜像
  3. 在 Win10 镜像里的 Sources 文件夹下找到名为「gatherosstate.exe」的程序，将其复制到桌面。
  4. 双击运行 gatherosstate.exe，稍等片刻，它将会在桌面上生成一个名为「GenuineTicket.xml」的文件
  5. 从文件命名就能看出，GenuineTicket.xml 就是「正版通行证」的意思，它里面保存了当前电脑的系统激活信息，你可以用U盘将它保存好，后面我们将会需要这个文件
  6. 使用你喜欢的方式全新安装 Windows 10 系统，但注意要保证 Win7/8 要和 Win10 的版本对应，譬如家庭版的 Win7 只能激活家庭版的 Win10。安装方式可参考：制作 Windows 10 安装U盘 、NT6 HDD Installer 硬盘安装等
  7. 安装 Windows 10 过程中，提示输入密钥时选择跳过
  8. 待 Win10 安装完成并进入桌面后，按键盘 Win+R 快捷键，打开“运行”，输入以下红色部分内容并点确定「%ProgramData%\Microsoft\Windows\ClipSVC\GenuineTicket」
  9. 这时系统会打开一个文件夹，将之前生成的 GenuineTicket.xml 文件复制到这个文件夹中
 10. 确保电脑正常联网然后重启电脑。待电脑重启后，稍等片刻 Win10 将会自动进行激活。如果没有，手工进入“设置”，点击窗口底部的 “Windows没有激活。请立即激活Windows” 链接，然后点击 “在线激活Windows” 下的 “激活” 按钮即可手工激活。
 11. 如无意外，在避开升级的过程后，您的 Windows 10 也已成功获得永久激活了！enjoy~
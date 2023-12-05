---
layout: post
title :  hyprland配置了留档
author : Narohaz
date : 2023-12-4 23:56:30 +0800
description: 问题记录
tags : 
- post
- hyprland
- manjaro
---


一个非常漂亮的hyprland配置文件[仓库地址](https://github.com/prasanthrangan/hyprdots)

1. 输入法问题
在hyprland中使用fcitx5除了需要在bashrc中添加输入法的环境变量
想要启动需要命令
fcitx5 --replace -d 
或者 开机启动exec-once=fcitx5 --replace -d //replace必须要有，否则不会启动.

2. 光标消失问题
在hyprland.conf中添加
env = XCURSOR_SIZE, 24
env = WLR_NO_HARDWARE_CURSORS,1

3. 切换图标时预览图像消失问题
(因为我的电脑上安装hyprland-nvidia-git会出现问题，手动修改成hyprland-nvidia之后运行会导致一部分指令没有执行)
复制.config/swww中的图片 到对应位置

4. vscode出现不稳定的显示
(不知道该怎么描述， 快速移动的过程上感觉会有残影和卡顿， 感觉渲染和什么出现了不兼容的感觉, 具体点来说就是操作快乐会出现重影)

      1.尝试的几种解决方法
      ```
      xwayland {
        force_zero_scaling = true
      }
      ```
      https://www.reddit.com/r/hyprland/comments/15jb7l7/blurry_vscode_on_hyprland/
      感觉没起到什么作用

      2.--ozone-platform=wayland --enable-features=WaylandWindowDecorations
      制定vscode使用wayland协议的方法，但是经测试没有什么

      3. 貌似和hyprland的窗口方式，有关，好像在全屏下容易出现这个问题，使float模式出现的次数就少了, 可能是我hyprland的窗口配置导致的(?)

      4. 不确定是否起到了作用，在安装了vscodium之后，vscode本身好像这个问题消失了。
      5. 使用--disable-gpu启动vscode(反复测试之后这个好像是最有效的？？)


      最好的解决方法是使用wayland启动，因为之前没有正确的设置启动参数导致我一直认为wayland帮助不大
      实际上在
      ~/.config/electron25-flags.conf 中加入
      --enable-features=UseOzonePlatform,WaylandWindowDecorations --ozone-platform-hint=auto 
      会让electron应用使用wayland启动
      (其中我之前已经查到了这种方式了，方式写在了错误的配置文件之中，如果之间简单的在终端启动很快就能发现这个用法，因为这样启动的vscode缩放不一样)
      网上说使用 ~/.config/code-flags.conf来设置启动参数的，也有说在~/.config/electron-flags.conf中的，但是经测试只有上面的方法对vscode生效了
      当然也可以直接

      ```
      code --enable-features=UseOzonePlatform,WaylandWindowDecorations --ozone-platform-hint=auto 
      ```
      注意上面的WaylandWindowDecorations和USeOzonePlatform都必须要有，我在没有前者的情况下会闪退

      或者对于单个应用来说可以在
      ```
      /usr/share/applications/XXX.desktop
      ```

      之中的exec后面添加
      ```
      --enable-features=UseOzonePlatform,WaylandWindowDecorations --ozone-platform-hint=auto 
      ```

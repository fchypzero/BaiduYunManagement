# 度娘盘分享守护程序

by LimiQS & 虹原翼

当前[灵梦御所](http://reimu.net/)正在使用这款自动补档程序。

本程序使用__GPL__许可证发布

## 修改说明

前台界面完全重新设计

BUG修正

几处杂项修改

## 功能：

- 监视百度网盘中建立的分享，通过跳转链接访问时，若分享被爆，全自动补档，提取码不变

- 更换MD5补档，根治百度不让分享

- 自定义分享提取码

- （可在配置文件中打开或关闭）免提取，免分享，直接获取百度网盘文件的下载地址，或者在线播放视频（在线播放视频需要跳转页使用HTTPS协议）

## 安装：

- 导入install.sql

- 修改config.sample.php，指定数据库，修改$jumper指向jump.php所在地址。如有需要，可按说明修改其他选项

- 将config.sample.php分别复制到bd和bd-admin文件夹，文件名改为config.php

- 将bd和bd-admin文件夹绑定不同的网站，为后者加上HTTP身份验证（因为我们没有做后台登录）

- 关闭open_basedir，如果使用PHP5.3，关闭safe_mode

## 升级：

- 直接覆盖文件

- 访问任意已经添加的补档记录，会自动对数据库进行升级

## 使用方法

- 打开管理后台，点击“浏览文件”-“添加用户”，添加要用来补档的百度用户。（警告：用户的登录Cookie将被明文存储在数据库中）

- 在“浏览文件”中添加新的文件，或者在主页“添加文件”中添加已分享的链接（必须是已经添加过的用户分享的）

- 在主页中可以查看已经添加的记录，并可删除不需要的记录。

- 访问主页中对应的跳转链接，即可自动检测是否挂档，如是则执行补档，并跳转到下载页。实际使用时把此链接提供给访问者。

- 若直接获取链接功能开启，访问跳转链接会直接得到文件的下载地址，点击“前往提取页”才会执行检测挂档。

## 关于提取码

在“浏览文件”中添加记录时，会提示设置提取码。

提取码可以是总长度为4位的任何字符，但是不能包含双字节字符。

提取码举例：

abcd （合法）

abc（分享失败）

猫C（合法）

猫（分享失败）

μ's（含有双字节字符，分享成功，但提取会失败）**本程序不能检测出此种提取码**，请自己注意不要使用

μμ（含有双字节字符，分享成功，但提取会失败）**本程序不能检测出此种提取码**，请自己注意不要使用

## 说明

Fork并修改自[NijiharaTsubasa/BaiduPanAutoReshare](https://github.com/NijiharaTsubasa/BaiduPanAutoReshare)

## 前言

只针对本型号电脑，快速安装Win，黑苹果双系统，以下内容假设你已经安装可以用的Win系统，操作都在Win系统下进行。

## 电脑配置

型号：华硕UX433FN（U4300FN，灵耀U2）

CPU：i5-8265u

显卡：Intel(R) UHD Graphics 620（独显MX150用不了）

内存：8G

SSD:  512GB NVME

## 测试正常的功能

1. 显卡
2. 声卡（没有声音，但是能控制输出设备音量，可以用蓝牙设备播放声音）
3. USB
4. Type-C
5. WIFI
6. 键盘
7. 触摸板
8. 其他自行测试

## 测试不正常的功能

1. HDMI视频、音频输出
2. 虚拟化
3. 其他自行测试

## EFI

使用OpenCore引导，GitHub地址：

克隆到本地，将BOOT文件夹的BOOTx64.efi改名BOOT1x64.efi，不然会覆盖原来系统的引导

## 开始

1. 下载黑苹果镜像，可以区黑果小兵下载，也可以其他地方下载；
2. 制作启动盘，制作工具下载：[etcher下载](https://www.balena.io/etcher/)；
3. 分区：添加一个分区用来安装系统，直接从win系统的磁盘管理压缩和添加卷；
4. 从启动盘启动，进入recovery，打开磁盘工具，选择格式化刚才加的分区为Apfs格式；
5. 然后选择安装系统，选择刚刚格式化的分区进行安装；
6. 安装完成重启进入Win系统，你也可以再从启动盘引导进入安装的黑苹果系统看一下安装的系统怎么样（可跳过此步）
7. 在Win系统中，打开EasyUEFI，（[下载地址](https://pan.baidu.com/s/16o5YCie91bxoOjrFJdVjhg)，提取码：85su），选择管理EFI系统分区-EFI系统分区资源管理器，将EFI文件上传到EFI分区；
8. 返回EasyUEFI主窗口，打开管理EFI启动项，新建启动项，选择其他系统，描述随便输入，浏览文件找到上传的BOOT1x64.efi，完成后将添加的启动项移到最前面；
9. 重启电脑，选择进入mac系统，OK

## 一些常见问题解决

1. 即使是Root模式也无法移动和修改文件的问题：

   - 重启进入recovery，打开终端输入

     ```shell
     csrutil disable
     ```

   - 重启系统

2. Appstore无法登录id问题：

   将com.apple.Boot.plist文件复制替换到

   ```shell
   /Library/Preferences/SystemConfiguration
   ```

   该文件下载地址：[com.apple.Boot.plist](https://pan.baidu.com/s/1JXaV8iHINyYWFCdXX0AWjg)，提取码：6cok

3. NTFS格式U盘硬盘只能读不能写的问题：下载安装Mounty软件，下载地址：[Mounty](https://pan.baidu.com/s/1p5yOWIOXQkh_frWY5ZBwWw)，提取码：aijg


# ec6108V9U-plub


>#备份固件  




http://blog.sina.com.cn/s/blog_14ecb4a860102wxli.html


E716041E94C9270E3EBCEF0621CB
刷新安全码


https://www.baidu.com/s?ie=UTF-8&wd=3.3通过telnet方式登录华为悦盒%201）在电脑上打开命令提示符（在运行中输入cmd）窗口；%202）在命令行窗口输入命令“telnet192.168.1.1”，回车；%203）在login处输入登录用户名“root”，回车；%204）在Password处输入密码（密码为空，直接回车即可）；%20注：此时可见绿色的提示文字“WelcometoHiLinux“，并可见%23号提示符。接下来就可输入命令进行后续的操作了。对Linux命令不太熟的人，建议你使用复制、粘贴的方式输入。%20四、打通天地线，从正确挂载U盘开始%20U盘上保存有ROOT盒子所必需的文件，让盒子能够正确读取到U盘上的文件信息，是我们进行ROOT操作的先决条件。从之前大家反馈的情况来看，许多人都是因为U盘挂载不上而导致ROOT出现问题，因此特地在这个地方写得详细一点。%204.1查看U盘的设备名称%20在%23号提示符处输入以下命令：%20%23ls/dev%7Cgrepsd%20复制代码%20以上图为例，一共列出了两个设备名，通常来说后面带有数字的设备名就是U盘了（此例中为sda4，在你的盒子上也许是sda1、sdb1、sdc1等等等）。%204.2挂载U盘%20在%23号提示符处输入以下命令：%20%23mkdir-p/tmp/udisk%20复制代码%20%23mount-tvfat/dev/sda4/tmp/udisk%20复制代码%20注意：请把命令中的%20da4%20替换成上一步所查看到的设备名再执行，不要直接照搬我的示例。若出现“Nosuchfileordirectory“的错误提示，则依次尝试其它的设备名。%204.3确认U盘挂载%20在%23号提示符处输入以下命令：%20%23ls/tmp/udisk%20复制代码%20U盘挂载正确的话，你就会看到之前复制进去的root_box.sh、update.zip等内容。%20五、未虑胜先虑败，ROOT之前请备份%20ROOT时操作不当有可能导致无法正常进入盒子（一般表现为反复重启），虽说可以通过恢复出厂状态的办法来解决，但随之带来的一个副作用就是ITV帐号信息丢失（启动IPTV应用时卡在80%25处）。%20现在我们先将ITV的配置文件进行备份，再进行ROOT操作就无后顾之忧了。%205.1备份ITV配置文件（请务必进行此操作）%20确保你已经正确挂载U盘，然后在%23号提示符处输入以下命令：%20%23sh/tmp/udisk/backup_profile.s%20复制代码%20当出现提示文字“Complete!”时，说明已经将盒子中的ITV配置文件备份到了U盘的backup文件夹中。%205.2备份内置固件（此步可以跳过）%20华为悦盒中内置了一个固件，用于恢复出厂状态之用。我们可以将其备份出来留待后用。四川、河北两地用户可以不进行此操作，帖子%20中已经提供了出厂固件下载。%20确保你已经正确挂载U盘，然后在%23号提示符处输入以下命令：%20%23sh/tmp/udisk/backup_rom.s%20复制代码%20当出现提示文字%27CopyingROMFiles...%27时，说明正在复制固件，请耐心等待一会。%20待出现“Complete!”提示时，说明已经将盒子中的固件备份到了U盘的backup文件夹中。


一、华为EC6106V8的原厂update.zip固件备份方法

如果你有TTL线，，就可以将原厂备份出来：

如果超级终端可以输入命令，就可以输入命令：
mkdir -p /tmp/udisk;mount -t vfat /dev/sda1 /tmp/udisk;cd /backup;cp update.zip /tmp/udisk;unmount /tmp/udisk

就可以将将原厂刷机文件update.zip备份到U盘上

备份固件可以备用做不时之需，万一哪天折腾搬砖或许用得着，如果有人备份了，希望也能分享出来，大家资源共享，感谢感谢！

二、华为盒子EC6108V9A固件备份教程！【全国通用！】

华为盒子EC6108V9A备份backup的命令是，还是先进入工程测试模式插入u盘

mkdir /tmp/udisk
mkdir /tmp/backup
mount -t vfat /dev/block/sda1 /tmp/udisk
mount -t ext4 /dev/block/platform/1021c000.rksdmmc/by-name/backup /tmp/backup
cp -a /tmp/backup /tmp/udisk/v9abackup

逆向写入：mkdir /tmp/udisk
mkdir /tmp/backup
mount -t vfat /dev/block/sda1 /tmp/udisk
mount -t ext4 /dev/block/platform/1021c000.rksdmmc/by-name/backup /tmp/backup
cp -a /tmp/udisk/v9abackup/update.zip /tmp/backup/update.zip

这个操作需要有点基础的朋友才行， 希望大家备份了自己的出厂固件分享到论坛，感谢感谢！

三、经一热心网友研究成功,华为悦盒WiFiADB固件提取方法：

1. 先在悦盒上root并装好sshdroid 或者 wifiadb并启动
华为悦盒root教程，请参考论坛链接或此方法： 
本教程仅适合未升级固件的悦盒使用。已升级的目前无解。
1）准备好无线鼠标
①打开华为秘盒的usb调试。盒子开机，进入 “所有设置” ->“高级” -> “其他设置” -> “开发人员选项” ->“USB调试” ，把USB调试开启
②把盒子关机取下来，插上一根手机线(micro usb)连接到电脑上，运行root工具。
2）下载安装百度一键ROOT（下载地址：http://down.znds.com/apk/tool/2014/1015/1167.html。
3）使用一键ROOT，获取高级权限。
4）成功root后，可安装第三方APK,如当贝市场，从当贝市场中可直接下载更多电视软件，破解运营商限制看电视。
  
2. sshroid：客户端用putty/sercertcrt登录，输入root@加盒子ip地址打开，输入密码admin登录wifiadb： 使用adb shell连接
mkdir /tmp/ii
mount -t ext3 /dev/block/platform/hi_mci.1/by-name/backup /tmp/ii
备份：
cp /tmp/ii/update.zip /sdcard/或者u盘目录
3. 用文件管理器将U盘已准备好的白色版固件覆盖到/tmp/ii/update.zip
4. 重启，按电源开机，并不断按遥控电源按扭进入 recovery模式，选择第二项升级
5. 可以DIY这个刷机包，也可以做成卡刷包。

备注： 固件升级 仅仅恢复 /system分区，如果手动删除了 /data/gameloft/ 狂野飚车目录可以需要重新下载/恢复

四、河南联通6108v9e盒子提取固件。
盒子里backup文件夹里的恢复固件，百度网盘：http://pan.baidu.com/s/1dFcL4h7 密码：8xsa


http://www.right.com.cn/forum/thread-312044-1-1.html





这个成功了。

注意：

mkdir是创建目录的意思
ls是dir的意思，列出文件夹中所有文件和文件夹
mount是挂载的意思unmount就是卸载的意思，主要用U盘
cp是copy的意思
df是不知道。。。

http://www.hdpfans.com/thread-798429-1-1.html


mkdir /tmp/rom
	
ls /tmp/rom
cat /sys/block/mmcblk0/dev
cat /sys/block/mmcblk0/dev
df
cp /tmp/rom/update.zip /mnt/sda/sda1
ls /mnt/sda/sda1 -l




-rwxrwxrwx system   sdcard_rw 254151199 2016-01-22 16:04 update.zip失败了，是广东的固件

从另一个正常的盒子里先降级成广东的，再备份，发现备份成功B015



-rwxrwxrwx system   sdcard_rw 226501658 2018-08-21 23:15 update.zip






























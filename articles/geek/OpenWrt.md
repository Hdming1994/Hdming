[返回目录](../../catalogue.md)  
## OpenWrt折腾记
### OpenWrt是什么
>OpenWrt是适合于嵌入式设备的一个Linux发行版。 相对原厂固件而言，OpenWrt不是一个单一、静态的固件，而是提供了一个可添加软件包的可写的文件系统。对于开发者来说，OpenWrt是一个框架，开发者不必麻烦地构建整个固件就能得到想要的应用程序；对于用户来说，这意味着完全定制的能力，与以往不同的方式使用设备，OPKG包含超过3500个软件。 OpenWrt默认使用LuCI作为web交互界面。——来自[维基百科](https://zh.wikipedia.org/zh-cn/OpenWrt)

&nbsp;&nbsp;对于普通消费者来说，OpenWrt就是一种可以自行安装软件的路由操作系统（通常不用于交换机）。
### OpenWrt能用在那些设备上
&nbsp;&nbsp;理论上来说，只要是有足够性能的计算设备，带一个或者多个网口，都能安装和使用Openwrt。常见的设备有：  
1. arm开发板：NanoPi R1S，树莓派  
2. 标准X86_64机：工控软路由，笔记本电脑，台式机，迷你机  
3. 部分硬路由：斐讯盒子，部分网件路由，部分小米路由等。  
4. 虚拟机：VM，Esxi，Pve，VisualBox等  

### 在标准X86_64机上安装OpenWrt
&nbsp;&nbsp;在X86_64机上安装OpenWrt有两种方式，一种是安装到U盘中，另一种是安装到硬盘介质中。安装到U盘中方便灵活，不占用硬盘，但是启动和写入相对较慢；安装到硬盘中要更繁琐，难以更换系统，不方便折腾。推荐安装到硬盘中，U盘长时间加电，可能会出现故障，而且旧二手小容量固态硬盘也不贵。  
&nbsp;&nbsp; OpenWrt系统所需要的硬盘空间通常不超过1GB。内存通常512MB即可，功能强大软件齐全的版本1GB够用，特殊情况根据需要来定。CPU性能要求：以J1900作为低端，i5 4200U作为中端，i7 7200U以上算作高端。  
安装步骤：
1. 下载获取安装文件*.img。可以直接使用大神编译好的（[Esir的Google Drive](https://drive.google.com/drive/folders/1eyIxVfyzO4nyzaT1sSr6xWf50_5YJN7g)），也可以使用官方原版（[openwrt.org](https://openwrt.org/)），还可自己通过源码编译（推荐[coolsnowwolf/lede](https://github.com/coolsnowwolf/lede)）。推荐使用Esir编译好的精品小包固件。Esir的固件也是**coolsnowwolf/lede**的源码编译的。精品小包包含一些常用的工具，此外还有高大全版。  
下载的到的文件为:**openwrt-spp-v2.1[2020]-x86-64-combined-squashfs.img.gz**
2. 解压得到*.img文件，重命名为简单的名字。
3. 制作PE启动盘，推荐WePE。将**img文件**和[**physdiskwrite.exe**](https://m0n0.ch/wall/downloads/physdiskwrite-0.5.3.zip)解压后拷贝到U盘中同一个目录。
4. PE启动进入系统，管理员身份打开CMD。
5. 使用`cd`命令进入到img文件的目录。
6. `physdiskwrite -u *.img`,然后根据提示选择硬盘，注意，会清除硬盘上的数据。
7. 将设备接入到另一台电脑的网口上，在浏览器输入`192.168.1.1`，进入管理页面。
8. 修改IP地址。（可以在浏览器中改，也可以用SSH连接设备来改）

### 安装软件和使用
&nbsp;&nbsp;未完待续

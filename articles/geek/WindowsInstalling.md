[返回目录](../../catalogue.md)
## Windows安装

### Windows 10安装
#### 1.下载ISO镜像文件  
+ [Windows10媒介创建工具](https://software-download.microsoft.com/download/pr/MediaCreationTool1903.exe)  
+ [Windows10微软下载](https://www.microsoft.com/zh-cn/software-download/windows10)  
+ [MSDN itellyou](https://msdn.itellyou.cn/)
#### 2. 制作启动U盘([Rufus](https://rufus.ie)或[UltraISO](https://www.ultraiso.com/download.html))  
+ UltraISO操作步骤：打开ISO文件->启动->写入硬盘映像->选择驱动器、选择写入方式(写入方式根据自己是否为UEFI来确定，通常选`USBHDD+`或者`USBZIP+`皆可。)  
+ Rufus设置更简单：选择镜像和U盘，选择分区类型为UEFI，其他默认就行。  
+ 在主板支持的情况下，直接将ISO文件内的所以文件复制到U盘根目录也可以。
#### 3. 从U盘启动  
+ 根据提示进入BIOS，设置启动模式为UEFI，设置BIOS的boot顺序，将U盘设置为第一启动项。有些计算机可以不进入BIOS，可以根据开机提示按下快捷键直接选则U盘作为启动项。  
#### 4. 分区和安装  
+ 从U盘启动后，按照提示到达分区界面，按下`Shift+F10`打开命令工具，输入以下命令：  
`diskaprt`(打开`diskpart`工具)  
`list disk`(列出所有磁盘)  
`select disk 0`（不一定是第0个磁盘，根据情况选择）  
`create partition efi size=300`（创建一个efi分区，大小为300M）  
`create partition msr size=200`（创建一个msr分区，大小为200M）  
`create partition primary size=102400`（创建一个主分区，大小100G）  
+ 其他分区根据需要进行划分，也可以等安装完系统后再进行。  
+ 若提示硬盘非GPT分区，则输入`convert gpt`将磁盘转化成GPT分区。  
+ 回到分区界面，选择创建的第一个primary分区并安装。
#### 5. 安装后的设置  
+ 等待一段时间后程序自动重启进入欢迎和设置界面，根据需要和个人习惯来设置即可。创建账号时尽量先创建本地账户，进入桌面再登陆微软账号。
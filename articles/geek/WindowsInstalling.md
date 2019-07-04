[返回目录](../../catalogue.md)
## Windows安装

### Windows 10安装
+ 下载ISO镜像文件  
[Windows10媒介创建工具](https://software-download.microsoft.com/download/pr/MediaCreationTool1903.exe)  
[Windows10微软下载](https://www.microsoft.com/zh-cn/software-download/windows10)  
[MSDN itellyou](https://msdn.itellyou.cn/)
+ 制作启动U盘  
  rufus或UltraISO
+ 从U盘启动  
  根据提示进入BIOS，设置启动模式为UEFI，设置BIOS的boot顺序，将U盘设置为第一启动项。有些计算机可以不进入BIOS，可以根据开机提示按下快捷键直接选则U盘作为启动项。  
+ 分区和安装
    从U盘启动后，按照提示到达分区界面，按下`Shift+F10`打开命令工具，输入以下命令：  
    `diskaprt`(打开`diskpart`工具)
    `list disk`(列出所有磁盘)
    `select disk 0`（选择第0个磁盘，根据需要选择）  
    `create partition efi size=300`（创建一个efi分区，大小为300M）  
    `create partition msr size=200`（创建一个msr分区，大小为200M）  
    `create partition primary size=102400`（创建一个主分区，大小100G）
    后面的分区根据需要进行，也可以等安装完系统后再进行。
    若提示硬盘非GPT分区，则输入`convert gpt`将磁盘转化成GPT分区。
    回到分区界面，选择创建的第一个primary分区并安装。
+ 安装后的设置
  等待一段时间后程序自动重启进入欢迎和设置界面，根据需要和个人习惯来设置即可。创建账号时尽量先创建本地账户，再登陆微软账号。
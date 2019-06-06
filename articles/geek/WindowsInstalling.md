[返回目录](../catalogue.md)
## Windows安装

### Windows 10安装
+ 下载ISO镜像文件  
[Windows10媒介创建工具](https://software-download.microsoft.com/download/pr/MediaCreationTool1903.exe)  
[Windows10微软下载](https://www.microsoft.com/zh-cn/software-download/windows10)  
[MSDN itellyou](https://msdn.itellyou.cn/)
+ 制作启动U盘
+ 从U盘启动
+ 分区和安装  
    `diskaprt -> disk list ->select disk 0`  
    `create partition efi size=300`  
    `create partition msr size=200`  
    `create partition primary size=102400`  
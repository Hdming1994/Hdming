[返回目录](../../catalogue.md)
## Windows的一些小问题
### 1. 打开`资源管理器`直接进入`我的电脑`
Windows 10默认设置打开资源管理器会进入`快速访问`，可以从`资源管理器`的`查看`—`选项`中设置在`打开资源管理器时打开我的电脑`。


### 2. 修改Windows 10照片查看方式（使用旧版照片查看器）
打开注册表，找到：
`计算机\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Photo Viewer\Capabilities\FileAssociations`在右侧新建“字符串值”，将新建值名称改为要关联的文件扩展名，比如“.jpg”，数值数据填写为“PhotoViewer.FileAssoc.Tiff”。其他图片格式以此类推。  
另外HoneyView也是一款非常不错的看图软件，只需在设置中设置为滚轮放大缩小即可轻松享用。  


### 3.[Win10系统任务栏无故卡死现象](https://answers.microsoft.com/zh-hans/windows/forum/all/win10%E7%B3%BB%E7%BB%9F%E4%BB%BB%E5%8A%A1%E6%A0%8F/38a3b5a0-4b78-4bae-9e71-04ae80685442)  
+ 此问题暂时无解，下面的结局方案未必有效。  
>您好，感谢您联系微软社区！
>了解到您 Windows 任务栏无故卡死的问题，根据您的描述，请问你有安装过第三方的系统优化软件吗？有的话建议您暂时卸载，因为这似乎是系统核心受损导致的。您可以尝试一下「干净启动」电脑，以排除糸统所有三方程序带来的干扰，并运行 DISM 和 SFC 检查器工具去修复一下系统，看看是否能够有效果。  
>
>1. `干净启动`：
>+ Win + R 键打开运行窗口输入 `msconfig`
>+ 点击 “服务” 选项卡，勾选 ”隐藏所有 Microsoft 服务”，点击 “全部禁用”
>+ 点击 “启动” 选项卡，点击 ”打开任务管理器”，然后禁用全部启动项并确定
>+ 重启电脑  
>
>2. DISM 和 SFC 检查工具修复系统：
>+ Win + S 键搜索栏输入 CMD 找到 “命令提示符”，右键以管理员身份打开，小心复制及贴上执行以下多条命令（需要联网操作，一次一行）：  
>`DISM.exe /Online /Cleanup-Image /ScanHealth`  
>`DISM.exe /Online /Cleanup-Image /CheckHealth`  
>`DISM.exe /Online /Cleanup-image /Restorehealth`  
>+ 无论上面三条命令是否有显示错误或成功，最后再键入以下命令：  
>`sfc /scannow`  
>完成后重启。
>
>以上这些命令是扫描系统全部的文件与官方对比是否一致，及通过 Windows 更新网络替换及修复损坏的文件，注意每行程令操作可能需要几分钟才能完成。  
>
>如果以上方法不能解决，才考虑重置或重新安装系统。


### 4.右键菜单添加`Open CMD Here`
+ 新建一个txt文档，输入如下内容:  
>Windows Registry Editor Version 5.00
>
>[HKEY_CLASSES_ROOT\Directory\shell\OpenCmdHere]  
>@="在此处打开命令窗口"
>"Icon"="cmd.exe"
>
>[HKEY_CLASSES_ROOT\Directory\shell\OpenCmdHere\command]  
>@="cmd.exe /s /k pushd "%V""  
>
>[HKEY_CLASSES_ROOT\Directory\Background\shell\OpenCmdHere]  
>@="在此处打开命令窗口"  
>"Icon"="cmd.exe"  
>
>[HKEY_CLASSES_ROOT\Directory\Background\shell\OpenCmdHere\command]  
>@="cmd.exe /s /k pushd \"%V\""  
>
>[HKEY_CLASSES_ROOT\Drive\shell\OpenCmdHere]  
>@="在此处打开命令窗口"  
>"Icon"="cmd.exe"  
>
>[HKEY_CLASSES_ROOT\Drive\shell\OpenCmdHere\command]  
>@="cmd.exe /s /k pushd \"%V\""  
>
>[HKEY_CLASSES_ROOT\LibraryFolder\background\shell\OpenCmdHere]  
>@="在此处打开命令窗口"  
>"Icon"="cmd.exe"  
>
>[HKEY_CLASSES_ROOT\LibraryFolder\background\shell\OpenCmdHere\command]  
>@="cmd.exe /s /k pushd \"%V\""
+ 将这个txt文档重命名为`.reg`格式，然后运行这个`.reg`文件。


### 5.删除资源管理器的左边栏项目
资源管理器左边栏中有很多无用的项目，如3D对象、视频等，删除步骤如下：  
+ 打开注册表，可以使用`Win+R`快捷键，然后输入`regedit`  
+ 定位到：`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace\` 
+ 按照需求删除对应的项目：  
下载：{088e3905-0323-4b02-9826-5d99428e115f}  
图片：{24ad3ad4-a569-4530-98e1-ab02f9417aa8}  
音乐：{3dfdf296-dbec-4fb4-81d1-6a3438bcf4de}  
桌面：{B4BFCC3A-DB2C-424C-B029-7FE99A87C641}  
文档：{d3162b92-9365-467a-956b-92703aca08af}  
视频：{f86fa3ab-70d2-4fc7-9c99-fcbf05467f3a}  
3D对象：{0DB7E03F-FC29-4DC6-9020-FF41B59E513A}  
+ 刷新或者重新打开资源管理器。  


### 6.GitHub代理配置
+ 找到个人目录下的.gitconfig文件，用记事本打开，
+ 在文档尾部另起一行添加如下内容：
  ```
  [http]  
  proxy = socks5://127.0.0.1:1080   
  [https]  
  proxy = socks5://127.0.0.1:1080  
  ```
  
  或者      
  ```
  [https]  
  proxy = 127.0.0.1:1080
  [http]
  proxy = 127.0.0.1:1080
  ```
  前一种情况适用于使用socks5代理，后一种情况使用的是http代理。

  
### 7.Win10 1909下，MATLAB无法找到自己导入的字体
原因分析：微软自作自作聪明、自作主张地将用户导入的字体统一放置在`C:\Users\Hdming\AppData\Local\Microsoft\Windows\Fonts\`，并且直接拷贝字体到`C:\Windows\Fonts\`，这些字体的存放目录依然在`C:\Users\Hdming\AppData\Local\Microsoft\Windows\Fonts\`。要怪就怪万恶的印度程序员。。。  

解决办法
+ （如果已经出现此情况），使用**PowerShell**将字体文件拷贝到`C:\Windows\Fonts\` 。  
`cp C:\Users\Hdming\AppData\Local\Microsoft\Windows\Fonts\Microsoft-Yahei-Mono.ttf C:\Windows\Fonts\`
+ 避免的办法：安装字体时,点击右键->为所有用户安装

### 未完待续。。。 

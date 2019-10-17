[返回目录](../../catalogue.md)
## Windows设置的一些小技巧
### 1. 打开`资源管理器`直接进入`我的电脑`
Windows 10默认设置打开资源管理器会进入`快速访问`，可以从`资源管理器`的`查看`—`选项`中设置在`打开资源管理器时打开我的电脑`。
### 2. 修改Windows 10照片查看方式（使用旧版照片查看器）
打开注册表，找到：
`计算机\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Photo Viewer\Capabilities\FileAssociations`在右侧新建“字符串值”，将新建值名称改为要关联的文件扩展名，比如“.jpg”，数值数据填写为“PhotoViewer.FileAssoc.Tiff”。其他图片格式以此类推。  
另外HoneyView也是一款非常不错的看图软件，只需在设置中设置为滚轮放大缩小即可轻松享用。  
### 3.[Win10系统任务栏无故卡死现象](https://answers.microsoft.com/zh-hans/windows/forum/all/win10%E7%B3%BB%E7%BB%9F%E4%BB%BB%E5%8A%A1%E6%A0%8F/38a3b5a0-4b78-4bae-9e71-04ae80685442)  
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

### 未完待续。。。 

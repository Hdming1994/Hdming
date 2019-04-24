## Windows设置的一些小技巧
### 1. 打开`资源管理器`直接进入`我的电脑`
Windows 10默认设置打开资源管理器会进入`快速访问`，可以从`资源管理器`的`查看`—`选项`中设置在`打开资源管理器时打开我的电脑`。
### 2. 修改Windows 10照片查看方式（使用旧版照片查看器）
打开注册表，找到：
`计算机\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Photo Viewer\Capabilities\FileAssociations`在右侧新建“字符串值”，将新建值名称改为要关联的文件扩展名，比如“.jpg”，数值数据填写为“PhotoViewer.FileAssoc.Tiff”。其他图片格式以此类推。  
另外HoneyView也是一款非常不错的看图软件，只需在设置中设置为滚轮放大缩小即可轻松享用。  

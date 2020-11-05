[返回目录](../../catalogue.md)
# 使用VS编译gdal
以VS2013和GDAL-2.24版本为例。2.3x以上版本不支持VS2013编译。[详见...](http://www.gisinternals.com/archive.php)
### 下载GDAL源码

+ 下载源码，从[GDAL Github Release](https://github.com/OSGeo/gdal/releases)或者通过[OSGEO网站](http://download.osgeo.org/gdal/)下载。
+ 下载二进制文件
从[Gisinternals下载](http://www.gisinternals.com/archive.php)，选择相应版本，对应的`release-xxxx-x64-gdalxxxx-mapserverxxxx.zip`就是二进制版本。

### 配置
将下载到的源码解压到相应的文件夹，然后在其目录中找到nmake.opt,打开并修改：
```
MSVC_VER=1800
GDAL_HOME = "D:\XXXXXX"
```
1800代表是VS2013，GDAL_HOME应当写绝对路径。
### 编译
打开VS的`VS2013 x64 本机工具命令提示`,使用cd进入到源码的根目录:

```
nmake -f makefile.vc MSVC_VER=1800 WIN64=yes
nmake -f makefile.vc install MSVC_VER=1800 WIN64=yes
nmake -f makefile.vc devinstall MSVC_VER=1800 WIN64=yes
```

[参考网站](https://trac.osgeo.org/gdal/wiki/BuildingOnWindows)
[返回目录](../../catalogue.md)
## 一些关于Office的小问题：　

### 问题1：Word公式显示错误

由于设置和操作不当，导致Word公示显示出现问题，但打印预览时公式正常。
具体症状如下:
+ Mathtype公式显示为:`{EMBED Equation.DSMT4}`
+ 超链接显示:`{HYPERLINK "http:........"}`
+ 页码显示为:​`{PAGE···\*·MERGEFORMAT}`

具体解决方法如下，以`Office2019`为例，二选一即可：
+ **`Alt+F9`**
+ **取消勾选**：文件--选项--高级--显示文档内容--`显示域代码而非域值` 

参考网站：[MathType相关文档](https://docs.wiris.com/en/mathtype/mathtype_desktop/support_notices/tn73)

--------
### 问题2：文档分栏最后一页多出空白页

具体问题表现为某些Word文档分栏后最后一页多出一页空白页，直接删除空白页会使得前面的分栏被取消，出现排版问题。
具体解决方法如下：`（以Office2019为例）`
+ 先在文字的最后末尾处添加分页、分节符，一直敲回车直到敲进下一页还多出几行，选中下一页多出来的几行按DEL.删除。
  
这样就删除了最后的空白页，而且排版不会出问题。  

--------
### 问题3：Office365与Visio的共存
即点即用版的Office365与VOL版的Visio无法共存，解决方法如下：
+ 下载最新版[Office部署工具](https://www.microsoft.com/en-us/download/details.aspx?id=49117)
+ 运行释放office部署工具，进入其目录，新建文件`configuration.xml`
+ 编辑`configuration.xml`：  
```
  <Configuration>
    <Add OfficeClientEdition="64" >
      <Product ID="VisioProXVolume" PIDKEY="69WXN-MBYV6-22PQG-3WGHK-RM6XC">
        <Language ID="zh-cn" />
      </Product>
    </Add>  
  </Configuration>
```
+ 使用**CMD管理员身份**进入前面的目录
+ 执行`setup.exe /download configuration.xml`
+ 执行`setup.exe /configure configuration.xml`  
+ 参考网页:  
1.[豆瓣：如何让即点即用的Office365和Visio2016共存](https://www.douban.com/note/698508220/)  
2.[MS：使用Office部署工具安装Project 2016和Visio 2016的批量许可版本](https://docs.microsoft.com/zh-cn/DeployOffice/use-the-office-deployment-tool-to-install-volume-licensed-editions-of-visio-2016?redirectSourcePath=%252fzh-cn%252farticle%252f%25e4%25bd%25bf%25e7%2594%25a8-Office-%25e9%2583%25a8%25e7%25bd%25b2%25e5%25b7%25a5%25e5%2585%25b7%25e5%25ae%2589%25e8%25a3%2585-Visio-2016-%25e5%2592%258c-Project-2016-%25e7%259a%2584%25e6%2589%25b9%25e9%2587%258f%25e8%25ae%25b8%25e5%258f%25af%25e7%2589%2588%25e6%259c%25ac-82691bd7-a3d5-47ca-8d8a-0ee43ec2c01f)

### 同时部署安装Office2019、Project、Visio
使用微软ODT（Office部署工具）和OCT（Office定制工具）可以一次性部署和激活Office2019、Project、Visio，非常方便。
+ 下载最新版[ODT工具](https://www.microsoft.com/en-us/download/details.aspx?id=49117)
+ 运行释放Office部署工具到指定目录
+ 使用在线的[OCT工具](https://config.office.com/deploymentsettings)选择需要的选项，导出成一个`configuration.xml`文件，保存到office部署工具的安装目录
+ 使用**CMD管理员身份**进入前面的目录
+ 执行`setup.exe /download configuration.xml`
+ 执行`setup.exe /configure configuration.xml`  
+ 参考网页：  
  1.[cnBeta:Office2019部署安装教程](https://www.cnbeta.com/articles/tech/787967.htm)  
  2.[BiliBili:Office 365 ProPlus部署教程](https://www.bilibili.com/read/cv822998/)  
+ Tips:OCT在线配置可以配置Office365、2016及2019版的Office、Project、Visio等软件，并且Office365和2019版Office等软件**只能安装在Windows10操作系统上**，2016版没有限制。
  
### PowerPoint导出PPT的分辨率设置为300DPI
默认情况下，要另存为图片的PowerPoint幻灯片的导出分辨率为每英寸96点（dpi）。要更改导出分辨率，请按照下列步骤操作：
+ 打开注册表(Regedit)  
+ 根据使用的PowerPoint版本，找到以下注册表子项之一：  
`HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\PowerPoint\Options`  
(对于2019、2016和365而言是16.0，2013对应15.0，2010对应14.0，2007对应13.0)  
+ 右键单击Options文件夹，新建一个`DWORD值`,并命名为`ExportBitmapResolution`  
+ 右键修改`ExportBitmapResolution`，选择十进制输入`300`,确定即可。
+ 注意：DPI值可以大于300，但不要超过1000，且2010及早期版本只支持到307DPI。
+ 参考：[How to change the export resolution of a PowerPoint slide](https://docs.microsoft.com/en-us/office/troubleshoot/powerpoint/change-export-slide-resolution)


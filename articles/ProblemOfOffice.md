[返回目录](../catalogue.md)
## 一些关于Office的小问题：　

### 问题1：公式显示为｛EMBED Equation.DSMT4｝

具体问题表现为添加了Mathtype公式后显示为｛EMBED Equation.DSMT4｝，超链接显示为大花括号和描述文本，页码显示为​ page.
具体解决方法如下：`（以Office2019为例）`

+ Alt+F9
+ 取消勾选：文件--选项--高级--显示文档内容--显示域代码而非域值 

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
+ 使用CMD进入前面的目录，执行setup.exe /download configuration.xml
+ 执行setup.exe /configure configuration.xml  
+ 参考网页:  
[豆瓣：如何让即点即用的Office365和Visio2016共存](https://www.douban.com/note/698508220/)，
[MS：使用Office部署工具安装Project 2016和Visio 2016的批量许可版本](https://docs.microsoft.com/zh-cn/DeployOffice/use-the-office-deployment-tool-to-install-volume-licensed-editions-of-visio-2016?redirectSourcePath=%252fzh-cn%252farticle%252f%25e4%25bd%25bf%25e7%2594%25a8-Office-%25e9%2583%25a8%25e7%25bd%25b2%25e5%25b7%25a5%25e5%2585%25b7%25e5%25ae%2589%25e8%25a3%2585-Visio-2016-%25e5%2592%258c-Project-2016-%25e7%259a%2584%25e6%2589%25b9%25e9%2587%258f%25e8%25ae%25b8%25e5%258f%25af%25e7%2589%2588%25e6%259c%25ac-82691bd7-a3d5-47ca-8d8a-0ee43ec2c01f)
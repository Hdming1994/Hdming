[返回目录](../../catalogue.md)  
## GVIM使用小记

### 安装GVIM
+ 下载GVIM安装即可，一切设置默认。  
个人目录中会出现一个vimfiles文件夹，这是GVIM的设置和插件目录。

### 安装vim-plug插件管理器
+ 下载vim-plug插件本身放到~/vimfiles/autoload文件夹（可能需要自行创建）
+  创建~/.vim文件夹

### 安装自己想要的插件
+ 在~/vimfiles/vimrc文件中写入下面的代码。（这里安装了gruvbox和nerdtree两个插件）  
```
" Specify a directory for plugins
" - For Neovim: stdpath('data') . '/plugged'
" - Avoid using standard Vim directory names like 'plugin'
call plug#begin('~/.vim/plugged')"插件管理开始，确保使用的是单引号

Plug 'morhetz/gruvbox'
Plug 'scrooloose/nerdtree'

" Initialize plugin system
call plug#end() "插件管理结束
```  
+ 在vim中执行命令`:PlugInstall`,需要全局代理
+ 安装其他插件就在call 和end之间添加对应的语句，然后再执行`:PlugInstall`

### 在vimrc文件添加以下内容
这些代码分别为了解决特定的问题，或者添加某些功能  
```
"Gvim中文菜单乱码解决方案#############################
"设置文件编码格式
set encoding=utf-8
set termencoding=utf-8
set fileencodings=utf-8,chinese,latin-1,gbk,gb18030,gk2312
if has("win32")
 set fileencoding=chinese
else
 set fileencoding=utf-8
endif
"解决菜单乱码
source $VIMRUNTIME/delmenu.vim
source $VIMRUNTIME/menu.vim
"解决consle提示信息输出乱码
language messages zh_CN.utf-8


"快捷键映射###################################
map <C-v> "+gP " Ctrl-V 
map <C-c> "+y  " CTRL-C 


"NerdTree设置#################################
autocmd VimEnter * NERDTree
map <F3> :NERDTreeToggle<CR> "设定插件的快捷键
let NERDTreeQuitOnOpen=1 "自动退出插件
autocmd BufEnter * if 0 == len(filter(range(1, winnr('$')), 'empty(getbufvar(winbufnr(v:val), "&bt"))')) | qa! | endif "自动退出插件


"其他设置#####################################
set guifont=Microsoft_YaHei_Mono:h11 "字体&大小
set lines=35 columns=140 "更改高度和宽度

set number  "显示行号
set backspace=2 "设置退格键

set guioptions-=T  "去除工具栏
set guioptions-=m  "去除菜单栏
set guioptions-=L  "去除左滚动条
set guioptions-=r  "去除右滚动条

colorscheme gruvbox "设定主题
set background=dark "暗黑模式主题
```  
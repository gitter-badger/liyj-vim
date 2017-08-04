liyj-vim
=======================
[![Gitter Room](https://img.shields.io/gitter/room/zaixi/liyj-vim.svg)](https://gitter.im/zaixi/liyj-vim)
[![Build Status](https://travis-ci.org/zaixi/liyj-vim.svg?branch=master)](https://travis-ci.org/zaixi/liyj-vim)

> VERSION: 1.0

> LAST_UPDATE_TIME: 2017-08-01

> 本次更新: 小版本更新, ubuntu14 16支持ycm快速安装


---------------------------------
---------------------------------
#### Table of contents
(toc generated by [ghtoc](https://github.com/sk1418/ghtoc))
- [liyj-vim效果](#liyj-vim效果)
- [自动安装](#自动安装)
	- [1. clone 到本地](#1.-clone-到本地)
	- [2. 安装](#2.-安装)
	- [3. 安装powerline字体](#3.-安装powerline字体)
	- [4. 编译YouCompleteMe](#4.-编译youcompleteme)
- [手动安装步骤](#手动安装步骤)
	- [1. 安装依赖包](#1.-安装依赖包)
	- [2. 源代码安装VIM8](#2.-源代码安装vim8)
	- [3. 安装powerline字体](#3.-安装powerline字体)
	- [4. clone liyj-vim到本地](#4.-clone-liyj-vim到本地)
	- [5. 安装VIM插件](#5.-安装vim插件)
	- [6. 编译YouCompleteMe自动补全插件](#6.-编译youcompleteme自动补全插件)
- [使用说明](#使用说明)
	- [1. git简化操作](#1.-git简化操作)
	- [2. 函数浏览](#2.-函数浏览)
	- [3. 行尾空格](#3.-行尾空格)
	- [4. 工程下单词搜索](#4.-工程下单词搜索)
	- [5. 定义跳转](#5.-定义跳转)
	- [6. 快速注释](#6.-快速注释)
	- [7. 异步执行](#7.-异步执行)
	- [8. 目录树](#8.-目录树)
	- [9. 快速对齐](#9.-快速对齐)
	- [10. ctrlp](#10.-ctrlp)
	- [11. 多光标编辑](#11.-多光标编辑)
	- [12. 快速移动](#12.-快速移动)
	- [13. 撤销分支树](#13.-撤销分支树)
	- [14. Doxygen风格注释](#14.-doxygen风格注释)
	- [15. 插件管理](#15.-插件管理)
	- [16. 自动补全插件](#16.-自动补全插件)
	- [17. 其他快捷键](#17.-其他快捷键)
- [FAQ](#faq)
	- [安装依赖报错](#安装依赖报错)
	- [编译YouCompleteMe自动补全插件报错](#编译youcompleteme自动补全插件报错)

## liyj-vim效果
![vim效果](https://github.com/zaixi/liyj-vim/blob/master/vim.png)

## 自动安装
**自动安装目前只支持ubuntu14和ubuntu16版本**
### 1. clone 到本地

```
git clone https://github.com/zaixi/liyj-vim
```

### 2. 安装
```
cd liyj-vim
./install.sh  /* 安装依赖和8.0版本VIM以及VIM插件 */
```
然后等待自动安装完成，安装完成后退出vim

### 3. 安装powerline字体
终端单击右键，配置文件，配置文件首选项，自定义字体打勾，选择字体   
推荐字体(带powerline的字体)
```
droid sans mono for powerline regular  
Cousine Powerline
Inconsolata-dz   
```

### 4. 编译YouCompleteMe
```
./install.sh /* 编译YouCompleteMe自动补全插件 */
```

## 手动安装步骤

### 1. 安装依赖包
```
# ubuntu
sudo apt-get install build-essential xz-utils cmake python-dev  #编译YCM自动补全插件依赖
sudo apt-get install silversearcher-ag                          #grep替代品,比grep更快
sudo apt-get install global                                     #ctags替代品，比ctags更好用
sudo apt-get install aptitude libncurses5-dev ruby-dev lua5.1 lua5.1-dev libperl-dev #编译VIM依赖库
```

### 2. 源代码安装VIM8
```
sudo apt-get remove vim vim-runtime gvim vim-tiny vim-common vim-gui-common vim-nox #卸载原有的VIM
git clone --depth=1 http://github.com/vim/vim
cd vim
./configure --with-features=huge --enable-multibyte --enable-pythoninterp --with-python-config-dir=/usr/lib/python2.7/config/ --enable-rubyinterp --enable-luainterp --enable-perlinterp --enable-cscope
make -j4
sudo make install
```

### 3. 安装powerline字体
```
git clone https://github.com/powerline/fonts.git
cd fonts
./install.sh
cd ..
```
终端单击右键，配置文件，配置文件首选项，自定义字体打勾，选择字体   
推荐字体(带powerline的字体)
```
droid sans mono for powerline regular  
Cousine Powerline
Inconsolata-dz   
```

### 4. clone liyj-vim到本地
```
git clone https://github.com/zaixi/liyj-vim
cd liyj-vim
mv $HOME/.vim $HOME/.vimback
mv $HOME/.vimrc $HOME/.vimrcback
rm -rf $HOME/.vimrc
rm -rf $HOME/.vim
cp .vim $HOME/ -a
cp .vimrc $HOME/.vimrc
```

### 5. 安装VIM插件
```
vim
```

### 6. 编译YouCompleteMe自动补全插件
```
cd $HOME/.vim/plug/repos/github.com/Valloric/YouCompleteMe
```
64位系统
```
./install.py --clang-completer    #64位系统如果编译安装后无法正常运行可以使用32系统的安装方法
```
32位系统
```
sudo apt-get remove clang-3.3 clang-3.4 clang-3.5 clang-3.6 clang-3.8
sudo apt-get install clang-3.9
./install.py --clang-completer --system-libclang
```

## 使用说明
```
注意, 以下 ; 代表 <leader>
```
### 1. git简化操作
插件来源:[fugitive](https://github.com/tpope/vim-fugitive)
```
Gstatus 相当于git status  
Gdiff 相当于git diff
```

### 2. 函数浏览
插件来源:[tagbar](https://github.com/majutsushi/tagbar)
```
<leader>lt 相当于taglist
```

### 3. 行尾空格
插件来源:[trailing-whitespace](https://github.com/bronson/vim-trailing-whitespace)
```
<leader><space> 去除行尾空格
```

### 4. 工程下单词搜索
插件来源:[ctrlsf](https://github.com/dyng/ctrlsf.vim)
```
<leader>sp 搜索光标下单词
```

### 5. 定义跳转
插件来源:[gtags](http://www.gnu.org/software/global)
```
ctrl + ]   跳转到光标下单词的定义
<leader>s  查找光标下单词的引用  
<leader>d  查找光标下单词出现的地方
使用之前需要像ctags生成tag文件
在项目根目录运行gtags,只需要生成一次，以后w保存时更新当前tags文件
```

### 6. 快速注释
插件来源:[nerdcommenter](https://github.com/scrooloose/nerdcommenter)
```
<leader>cc 注释选中区域或当前行
<leader>cu 取消注释选中区域或当前行
```

### 7. 异步执行
插件来源:[asyncrun](https://github.com/skywind3000/asyncrun.vim)
```
AsyncRun {command} 异步执行command
eg：
  AsyncRun ls 异步列出当前文件
```

### 8. 目录树
插件来源:[nerdtree](https://github.com/scrooloose/nerdtree)
```
<leader>fl 显示文件列表
```

### 9. 快速对齐
插件来源:[easy-align](https://github.com/junegunn/vim-easy-align)
```
<leader>a  对齐选中区域(可根据空格，等号，引号等对齐)，vim-easy-align的功能
eg:<leader>a=  根据"="对齐选中区域
eg:<leader>a,  根据","对齐选中区域
```

### 10. ctrlp
插件来源:[ctrlp](https://github.com/ctrlpvim/ctrlp.vim)
```
ctrl+p 进入文件搜索模式，输入文件名可搜索文件(默认当前目录), 输入..可以把搜索目录向上移动
```

### 11. 多光标编辑
插件来源:[multiple-cursors](https://github.com/terryma/vim-multiple-cursors)
```
ctrl+n 选中当前单词，再按ctrl+n选中下一个同样的单词，选完后按c批量修改  
```

### 12. 快速移动
插件来源:[easymotion](https://github.com/easymotion/vim-easymotion)
```
s + {任意字符}  快速移动到指定位置
例子：已有一行数据为
sudo apt-get install silversearcher-ag global
光标在行首，输入sia光标跳到indtall的i处
```

### 13. 撤销分支树
插件来源:[gundo](https://github.com/sjl/gundo.vim)
```
<leader>ud 选中之前的节点，回车就可以回到之前修改或撤销的状态
```

### 14. Doxygen风格注释
插件来源:[DoxygenToolkit](https://github.com/vim-scripts/DoxygenToolkit.vim)
```
<leader>cf 生成Doxygen风格注释
```

### 15. 插件管理
插件来源:[dein](https://github.com/Shougo/dein.vim)
```
PlugInstall 安装插件
PlugUpdata  更新插件
```

### 16. 自动补全插件
插件来源:[YouCompleteMe](https://github.com/Valloric/YouCompleteMe)
ctrl + space 手动触发，注意此快捷键常和系统输入法冲突
YouCompleteMe后端采用clang编译器分析语义完成语义补全，所以需要一个配置文件告诉clang编译参数，YouCompleteMe会自动从当前目录向上级目录遍历找到.ycm_extra_conf.py配置文件，所以需要配置.ycm_extra_conf.py文件,具体配置方法见[YouCompleteMe](https://github.com/Valloric/YouCompleteMe)
对于向kernel这种的项目，进入项目根目录打开vim,执行`YcmGenerateConfig`命令可自动生成.ycm_extra_conf.py文件。
![补全效果](http://i.imgur.com/0OP4ood.gif)

### 17. 其他快捷键
```
F4 进入粘贴模式，从其他地方粘贴过来的代码格式不会变化  
F5 在当前目录下异步执行make  
F9 打开/关闭行号显示，方便鼠标复制
F11 全屏切换
F12 对齐当前文件
<leader> R 不确认、非整词替换当前光标下单词
<Leader>rw 不确认、整词替换当前光标下单词
<Leader>rc 确认、非整词替换当前光标下单词
<Leader>cw 或 <Leader>wc 确认、整词替换当前光标下单词
<leader> 1
<leader> 2
...
airline插件提供，当打开多个文件时，在buffer间切换
```



## FAQ
### 安装依赖报错
可能是软件源陈旧，可以临时换用网易163的源安装后再换回去

### 编译YouCompleteMe自动补全插件报错
查看报错提示，可能是g++不支持C++11，需要重新安装
安装g++ 4.9  
```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt-get update
sudo apt-get install gcc-4.9
sudo apt-get install g++-4.9
sudo cd /usr/bin
sudo ln -s /usr/bin/g++-4.9 /usr/bin/g++ -f
sudo ln -s /usr/bin/gcc-4.9 /usr/bin/gcc -f
```

 ### 下载VIM插件很慢，或者YouCompleteMe下载失败，总是提示重新安装
 插件来源于github，和网速有很大关系，可以采用其他下载方式，再手动放到相应目录
 ```
wget -O ~/YouCompleteMe.tar.gz "http://ohpunyak1.bkt.clouddn.com/YouCompleteMe.tar.gz?v=9999"
cd ~/.vim/plug/repos/github.com/Valloric
tar -zxf ~/YouCompleteMe.tar.gz
 ```

## re-compile vim

### download vim

```sh
git clone git@github.com:vim/vim.git
cd vim
```

### config compile

- MAC

```sh
./configure \           
--enable-multibyte \
--enable-perlinterp=dynamic \
--enable-rubyinterp=dynamic \
--with-ruby-command=/usr/bin/ruby \
--enable-pythoninterp=dynamic \
--with-python-config-dir=/usr/lib/python2.7/config \
--enable-python3interp \
--with-python3-config-dir=/Library/Developer/CommandLineTools/Library/Frameworks/Python3.framework/Versions/3.7/lib/python3.7/config-3.7m-darwin \
--enable-luainterp \
--with-lua-prefix=/Users/wangbo/codes/homebrew/brew/Cellar/lua/5.3.5_1 \
--enable-cscope \
--enable-gui=auto \
--with-features=huge \
--enable-fontset \
--enable-largefile \
--disable-netbeans \
--enable-fail-if-missing \
--prefix=/usr/local/vim8
```

- ubuntu

```sh
sudo apt-get install libncurses5-dev
./configure --with-features=huge --enable-pythoninterp --enable-rubyinterp --enable-luainterp --enable-perlinterp --with-python-config-dir=/usr/lib/python2.7/config/  --enable-cscope --prefix=/usr/local/vim8
```

### compile && install

```sh
# 编译安装
$ make && make install

# 确认是否安装成功: 并可以检查是否支持了 python2/3 lua等解释器
# 由于设置了 --prefix=/usr/local/vim8 所以全路径是这样
$ /usr/local/vim8/bin/vim --version

# 查看 老的vim路径, 并删除掉
$ ll `which vim`
$ rm /usr/local/bin/vim

# 创建软链
$ ln -s /usr/local/vim8/bin/vim /usr/local/bin/vim

# 再次查看版本号, 确定是否已经支持
$ vim --version
```

## install vundle

```sh
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

## config VIM

```sh
git clone git@github.com:MagicBowen/vimcfg.git ~/.vimcfg
cp ~/.vimcfg/.vimrc ~/.vimrc

sudo vim .vimrc

:PluginInstallc
```

## shortcuts

### mode

- 普通模式：ESC
- 插入模式：i/a
- 命令模式：`:`
- 虚拟模式：`v`

### 普通模式

- 前后左右字符移动：h，l，k，j
- 前后单词移动：w，b

- 删除： x/X，删除后一个或前一个字符
- 删除行： dd
- 删除单词：daw
- 删除至行首、行位：d^, d$

- 跳到第n行：nG
- 跳到第一行：gg
- 跳到最后一行：G
- 返回上一次光标所在位置：ctrl + o

- 复制游标所在的整行	yy(3yy表示复制3行)
- 复制到行首，不含光标所在位置	y^或y0
- 复制到行尾，含光标所在字符	y$
- 复制一个单词	yw
- 复制两个单词	y2w
- 复制至文本末	yG
- 复制至文本开头	y1G
- 粘贴至光标后(下)	p(小写)
- 粘贴至光标前(上)	P(大写)

- 向下查找<字符串>	\<字符串>	输入n继续查找下一个
- 向上查找<字符串>	? <字符串>	输入N继续查找下一个
- 寻找游标所在处的单词	\*	向后
- 寻找游标所在处的单词	\#	向前
- 查找部分符合该单词即可	g\*	向后
- 查找部分符合该单词即可	g\#	向前
- 取消搜索	:noh+Enter

- [n] u: 取消一(n)个改动。
- :undo 5 -- 撤销5个改变。
- :undolist -- 你的撤销历史。
- ctrl + r: 重做最后的改动。
- U: 取消当前行中所有的改动。

### 插入模式

- i: 字符前插入
- a：字符后插入
- I：行首插入
- A：行末插入
- o：行后新行插入
- O：行前新行插入

### 命令模式

- q，q!，wq，qa，wa
- :w filepath/newfile: 另存为

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

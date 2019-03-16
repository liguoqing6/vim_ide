# vim_ide
how to use vim for ide func
1、在Ubuntu 16.04里升级 vim 8
sudo apt-get install libncurses5-dev libgnome2-dev libgnomeui-dev \
    libgtk2.0-dev libatk1.0-dev libbonoboui2-dev \
    libcairo2-dev libx11-dev libxpm-dev libxt-dev python-dev \
    python3-dev ruby-dev liblua5.1 lua5.1-dev libperl-dev git

dpkg -l | grep vim
sudo apt remove vim vim-common vim-runtime vim-tiny

git clone https://github.com/vim/vim.git

./configure --with-features=huge \
            --enable-multibyte \
            --enable-rubyinterp=yes \
--enable-python3interp=yes \
            --with-python3-config-dir=/usr/lib/python3.5/config \
            --enable-perlinterp=yes \
            --enable-luainterp=yes \
            --enable-gui=gtk2 --enable-cscope --prefix=/usr
　　如果想让vim8支持python2，执行下面的操作：

./configure --with-features=huge \
            --enable-multibyte \
            --enable-rubyinterp=yes \
            --enable-pythoninterp=yes \
            --with-python-config-dir=/usr/lib/python2.7/config \
            --enable-perlinterp=yes \
            --enable-luainterp=yes \
            --enable-gui=gtk2 --enable-cscope --prefix=/usr

make VIMRUNTIMEDIR=/usr/share/vim/vim81 

sudo make install

2、插件管理工具Vundle
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

3、配置vimrc
把vimrc_config
cp  ~/.vimrc

启动Vim,运行命令 :PluginInstall

4、ctags工具
sudo apt-get install ctags

5、sudo apt-get install cscope

6、自动补存插件YouCompleteMe
sudo apt-get install build-essential cmake python-dev python3-dev
cd ~/.vim/bundle/YouCompleteMe/
 ./install.py --clang-completer
cp third_party/ycmd/examples/.ycm_extra_conf.py  ~/.vim

7、工程建立
make tags cscope TAGS


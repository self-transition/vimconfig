# vimconfig
自用vim配置与配色,注意vim版本需大于7.3,且须有python2.7环境

- 下载

git clone https://github.com/rxy8023/vimconfig.git
- 复制配置

cp ./vimconfig/vimrc ~/.vimrc

- 添加配色

mkdir -p ~/.vim/colors && cp ./vimconfig/molokai.vim

- 重启vim

- vim 学习笔记
[**《vimtutor》notes.md**](https://github.com/rxy8023/vimconfig/blob/master/《vimtutor》notes.md)



# 2022 vimconfig

最近的开发环境换到 M1 Mac 上面去，加之现在在做 K8S 项目相关的集成工作，导致比较常用，但是之前使用的 vim 配置已经是 5 年前在学校读书时候使用的配置了，因此花了几个小时重新更新了下配置。

## YouCompleteMe
这次使用的是比较难安装的 YouCompleteMe 插件

### 环境支持
YouCompleteMe插件（后面简称ycmd）需要支持编译python3.6+版本、版本号在8.1.7以上版本的vim，因此有两种解决方法：
- 使用brew升级vim版本
- 使用brew安装MacVim
```shell
brew install macvim
alias vim='mvim -v'
# 这里配置了别名，直接使用 macvim 替代 vim
 
```
 ### Vundle
Vundle (缩写自Vim bundle) 是一个很方便的 Vim 插件管理器。它的使用方法很简单，安装一个插件只需要在.vimrc按照规则中添加 Plugin 的名称，某些需要添加路径，之后在 Vim 中使用:PluginInstall既可以自动化安装。

```shell
git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

安装完成后使用 Vundle ，在vim中输入`:PluginInstall`即可安装

安装依赖的时候可能出现以下错误： 

```
Error detected while processing function vundle#installer#new:
line    6:
E121: Undefined variable: g:vundle#bundles
E116: Invalid arguments for function copy(g:vundle#bundles), 'index(a:000, v:val
.name) > -1')
E116: Invalid arguments for function filter(copy(g:vundle#bundles), 'index(a:000
, v:val.name) > -1')
E15: Invalid expression: filter(copy(g:vundle#bundles), 'index(a:000, v:val.name
) > -1')
```

可以执行以下命令，重新生成 vimrc

```shell
mv ~/.vimrc ~/.vimrc_back
mv ~/.vim ~/.vim_back
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
cp ~/.vim/bundle/Vundle.vim/test/minirc.vim ~/.vimrc
```

### YouCompleteMe

在.vimrc中添加如下内容。位置在call vundle#begin()和call vundle#end()之间。

```shell
Plugin 'Valloric/YouCompleteMe'
```



### 编译

如果网络比较慢的话可以使用源码编译安装

```shell
git clone git@github.com:ycm-core/YouCompleteMe.git ~/.vim/bundle
python3 run_test.py
# 测试相关依赖，补充缺失的依赖
brew install cmake
 pip3 install neovim
python3 install.py
```

安装完成后就可以完美使用了，最新的 vim 配置也贴在项目中的 `vimrcnew` 文件中

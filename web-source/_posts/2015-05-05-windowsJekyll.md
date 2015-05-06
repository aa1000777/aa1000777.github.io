---
layout: post
title: Windows上使用Jekyll在Github上搭建个人博客（环境搭建）
categories: [All,Tools]
tags: [Jekyll, Github, ServerConfiguration]
fullview: false
description: GitHub是一个代码托管网站，现在很多开源项目都放在GitHub上。 利用GitHub，可以让全球各地的程序员们一起协作开发。GitHub 提供了一种功能，叫 GitHub Pages, 利用这个功能，我 们可以为项目建立网站，当然，这也意味着我们可以通过 GitHub Pages 建立自己的网站。
---

 GitHub是一个代码托管网站，现在很多开源项目都放在GitHub上。 利用GitHub，可以让全球各地的程序员们一起协作开发。GitHub 提供了一种功能，叫 GitHub Pages, 利用这个功能，我 们可以为项目建立网站，当然，这也意味着我们可以通过 GitHub Pages 建立自己的网站。

Jekyll是一个简单的，针对博客设计的静态网站生成器。使用 GitHub 和 Jekyll，我们可以打造自己的独立博客，你可以自由地定制网站的风格，并且这 一切都是免费的。

## Windows 上安装 Jekyll ##

共分为以下几个重要步骤

    安装 Ruby
    安装 DevKit
    安装 Jekyll
    安装 Pygments
        安装 Python
        安装 ‘Easy Install’
        安装 Pygments
    启动 Jekyll
    故障诊断

## 安装 Ruby ##

1. 前往 [http://rubyinstaller.org/downloads/](http://rubyinstaller.org/downloads/ "http://rubyinstaller.org/downloads/")
2. 在 “RubyInstallers” 部分，选择某个版本点击下载。
例如，Ruby 2.0.0-p451 (x64) 是适于64位 Windows 机器上的 Ruby 2.0.0 x64 安装包。
3. 通过安装包安装

- 最好保持默认的路径 C:\Ruby200-x64， 因为安装包明确提出 “请不要使用带有空格的文件夹 (如： Program Files)”。
- 勾选 “Add Ruby executables to your PATH”，这样执行程序会被自动添加至 PATH 而避免不必要的头疼。

	![enter image description here](http://cn.yizeng.me/assets/images/posts/2013-05-11-ruby-installer.png)

4. 打开一个命令提示行并输入以下命令来检测 Ruby 是否成功安装。

	> ruby -v

	输出示例：

	> ruby 2.0.0p451 (2014-02-24) [x64-mingw32]
##安装 DevKit##
DevKit 是一个在 Windows 上帮助简化安装及使用 Ruby C/C++ 扩展如 RDiscount 和 RedCloth 的工具箱。 详细的安装指南可以在程序的[wiki](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit#installation-instructions "https://github.com/oneclick/rubyinstaller/wiki/Development-Kit#installation-instructions")页面阅读。



- 再次前往 [http://rubyinstaller.org/downloads/](http://rubyinstaller.org/downloads/ "http://rubyinstaller.org/downloads/")

- 下载同系统及 Ruby 版本相对应的 DevKit 安装包。 例如，DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe 适用于64位 Windows 系统上的 Ruby 2.0.0 x64。

    下面列出了如何选择正确的 DevKit 版本：

        Ruby 1.8.6 to 1.9.3: DevKit tdm-32-4.5.2
        Ruby 2.0.0: DevKit mingw64-32-4.7.2
        Ruby 2.0.0 x64: DevKit mingw64-64-4.7.2

- 运行安装包并解压缩至某文件夹，如 C:\DevKit

- 通过初始化来创建 config.yml 文件。在命令行窗口内，输入下列命令：

        cd “C:\DevKit”
        ruby dk.rb init
        notepad config.yml

- 在打开的记事本窗口中，于末尾添加新的一行 - C:\Ruby200-x64，保存文件并退出。

- 回到命令行窗口内，审查（非必须）并安装。

        ruby dk.rb review
        ruby dk.rb install

## 安装 Jekyll ##


- 确保 gem 已经正确安装

        gem -v

    输出示例：

        2.0.14

- 安装 Jekyll gem

        gem install jekyll


## 安装 Pygments ##
Jekyll 里默认的语法高亮插件是 [Pygments](https://pygments.org "https://pygments.org")。 它需要安装 Python 并在网站的配置文件_config.yml 里将 highlighter 的值设置为pygments。

不久之前，Jekyll 还添加另一个高亮引擎名为 [Rouge](https://github.com/jayferd/rouge "https://github.com/jayferd/rouge")， 尽管暂时不如 Pygments 支持那么多的语言，但它是原生 Ruby 程序，而不需要使用 Python。 更多信息请[点此](jekyllrb.com/docs/templates/#code_snippet_highlighting "jekyllrb.com/docs/templates/#code_snippet_highlighting")关注。

## 安装 Python ##

- 前往 [http://www.python.org/download/](http://www.python.org/download/ "http://www.python.org/download/")
- 下载合适的 Python windows 安装包，如 Python 2.7.6 Windows Installer。 请注意，Python 2 可能会更合适，因为暂时 Python 3 可能不会正常工作。
- 安装
- 添加安装路径 (如： C:\Python27) 至 PATH。

- 检验 Python 安装是否成功

        python –V

    输出示例：

        Python 2.7.6

## 安装 Easy Install ##

- 浏览 [https://pypi.python.org/pypi/setuptools#installation-instructions](https://pypi.python.org/pypi/setuptools#installation-instructions "https://pypi.python.org/pypi/setuptools#installation-instructions") 来查看详细的安装指南。

- 对于 Windows 7 的机器，下载 ez_setup.py 并保存，例如，至C:\。 然后从命令行使用 Python 运行此文件：

        python “C:\ez_setup.py”

- 添加 ‘Python Scripts’ 路径 (如： C:\Python27\Scripts) 至 PATH

## 安装 Pygments ##


- 确保 easy_install 已经正确安装

        easy_install --version

    输出示例：

        setuptools 3.1

- 使用 “easy_install” 来安装 Pygments

        easy_install Pygments

#### <i class="icon-pencil"></i> 上面这一步可能会报错，只要更换一下gem来源就行了
- 安装gem，这个也可以去gem的官网进行下载，然后直接安装就行了，安装完成后使用gem -v查看一下是否安装成功。我安装的是2.1.11版本
- gem是可以选择源的，默认的源有点慢，可以使用ruby.taobao.org的源，方便快捷查看当前源

		D:\node\jekyll>gem sources list
		*** CURRENT SOURCES ***
		
		https://rubygems.org/
		
		D:\node\jekyll>

	添加新源

		gem sources -a http://ruby.taobao.org/

	删除默认源

		gem sources --remove https://rubygems.org/

- 再次查看的时候保证只有http://ruby.taobao.org/就行了

- 如果上面出错，去网上找找教程吧，ruby环境的搭建和gem的安装教程还是蛮多的，基本google一下遍地都是。
## 使用gem安装Jekyll ##
使用命令 **gem install jekyll** 就可以安装jekyll及所有需要的依赖，但不包括插件，安装jekyll的时候需要注意一下安装的版问题，jekyll的最新版本为1.4.3，但是有一个bug，[stackoverflow](stackoverflow.com/questions/21137096/jekyll-error-running-jekyll-serve "stackoverflow.com/questions/21137096/jekyll-error-running-jekyll-serve")上有人遇到过，我自己在使用的时候也遇到了类似的问题，解决方法是安装1.4.2版本，所以这里的安装命令为： **gem install jekyll --version "=1.4.2"** 。安装完成后使用 **jekyll -v** 查看一下是否安装成功了

## 启动 Jekyll ##

- 按照官方的 [Jekyll英文](http://jekyllrb.com/docs/quickstart/ "http://jekyllrb.com/docs/quickstart/")（[Jekyll中文](http://jekyll.bootcss.com/docs/quickstart/ "http://jekyll.bootcss.com/docs/quickstart/")）  快速开始手册 的步骤， 一个新的 Jekyll 博客可以被建立并在[localhost:4000](http://localhost:4000 "http://localhost:4000")浏览。

		~ $ gem install jekyll
		~ $ jekyll new myblog
		~ $ cd myblog
		~/myblog $ jekyll serve
		# => Now browse to http://localhost:4000


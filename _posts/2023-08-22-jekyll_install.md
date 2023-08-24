---
title: 安装jekyll
tags: jekyll
---

### 基本安装流程
```shell
sudo apt install ruby
sudo apt-get install ruby-dev
sudo apt-get install software-properties-common
sudo apt-get install nodejs
sudo gem install jekyll
```

---
### 最后一步安装jekyll时报错：sass-embedded版本不兼容
```shell
ERROR:  Error installing jekyll:
        The last version of sass-embedded (~> 1.54) to support your Ruby & RubyGems was 1.63.6. Try installing it with `gem install sass-embedded -v 1.63.6` and then running the current command again
        sass-embedded requires Ruby version >= 3.0.0. The current ruby version is 2.7.0.0.
```
解决方法：
* 执行命令`sudo gem update --system`更新Gem版本（可能会遇到网络错误，再执行一遍即可）
* 再执行命令`gem install sass-embedded -v 1.63.6`安装正确版本的sass-embedded

---
### 执行jekyll命令时报错：找不到ffi-1.15.5
* 执行命令`sudo gem install ffi -v 1.15.5`
* 执行命令`sudo gem pristine ffi --version 1.15.5`
至此，大功告成

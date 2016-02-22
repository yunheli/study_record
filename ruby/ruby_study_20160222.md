#### Ruby 怎么来缓存gem呢？
    最近在公司做一个项目要缓存安装的gem，该怎么做呢？
    于是就想了一个办法直接缓存$GEM_HOME/gems 文件夹，
    然而事情的发展并不随人所愿，缓存了的gem包在项目安装时又重新去源下载，
    以下从docker中重现的做法

##### 初始化一个Ruby on Rails的项目
```
rails new myapp
cd myapp
git init
git remote add url `github 地址`
ga . && gc -m "初始化项目" && gp origin master
#以上为了重现做准备
```

##### 开启一个docker --前提你已经安装了docker
```
docker run -i -t --rm -v /usr/local/gems:$GEM_HOME/gems ruby_images 
# -v 是挂载的意思，将外部的目录挂载到$GEM_HOME/gems的文件夹
```

##### 之后获取myapp项目
```
 git clone myapp.git && cd myapp
 bundle install #这时/usr/local/gems已经有安装之后的gem文件夹
```

##### 重新新打开docker
```
docker run -i -t --rm -v /usr/local/gems:$GEM_HOME/gems ruby_images 
git clone myapp.git
cd myapp
bundle install
#意外出现了，竟然重新fetch 重新安装--还没找到解决方法
```
> 之后发现$GEM_HOME下面有个cache文件夹能缓存所有的.gem文件所以缓存cache里面的.gem文件就解决了这个问题

###### 解决方案就是缓存$GEM_HOME/cache文件

##### bundle package --no-install
```
 bundle package #会将下载的.gem文件放在vendor/cache文件夹下
 bundle install --local #就会将gem文件安装在vendor/cache当前文件夹下
```
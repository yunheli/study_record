### 在github.io中创建自己的主页
      
      1、首先还是先创建一个github帐号
      2、创建一个username.github.io的repo
      3、在本地git clone git@github.com:`username`/username.github.io.git
      4、echo 'hello world' > index.html
      5、打开浏览器访问username.github.io就能看到hello word
 
### 在github.io中创建项目的主页
	  要访问username.github.io/xx的项目主页
	  1、创建xx的项目
	  2、git clone git@github.com:`username`/xx.git
	  3、创建分支 gh-pages 分支
	  4、echo "this is a xx project" > index.html
	  5、git push origin gh-pages
	  6、打开浏览器访问username.github.io/xx就存在了
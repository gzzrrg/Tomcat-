# MAC配置Tomcat

## 1. 通过终端`Terminal`打开Tomcat中的`bin`目录，操作命令如下

~~~sudo
cd ~/Library/Tomcat/bin
~~~



## 2.授权使用Tomcat `bin`目录下的所有操作，操作命令如下

~~~sudo
sudo chmod 755 *.sh
~~~



## 3.启动Tomcat，操作命令如下

~~~sudo
sudo sh ./startup.sh
~~~



## 4.打开浏览器，访问`localhost:8080`，如果页面如下，也表示**Tomcat已启动**。



## 5.关闭Tomcat，操作命令如下(**先切换Tomcat中的`bin`目录**)

~~~bash
cd ~/Library/Tomcat/bin
sh ./shutdown.sh
~~~


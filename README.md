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

这是最直接的解决办法，核心就是找到占用端口的“幕后进程”并关闭它。你可以在 IDE（如 Eclipse）中先检查是否有未正常关闭的 Tomcat 实例，如果有，直接停止它。如果没有，就通过终端操作：

1. **打开终端**，输入以下命令分别查看占用 8080 和 8005 端口的进程 PID：

    bash

    ```
    sudo lsof -i:8080
    sudo lsof -i:8005
    ```

    

    `lsof -i:端口号` 是 macOS 上查看指定端口占用情况的标准命令 。

2. 命令执行后，在输出的信息中找到 `PID`（进程ID）那一列 。

    bash

    ```
    # 示例输出
    COMMAND   PID USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
    java    12345  user   ...  ...                 ...   ...      ...  *:8080 (LISTEN)
    ```

    

3. 获取 PID 后，使用以下命令强制终止该进程：

    bash

    ```
    sudo kill -9 <PID>
    ```

    

    请将 `<PID>` 替换为实际的进程ID，例如 `sudo kill -9 12345` 。

4. **验证并重启**：再次运行 `sudo lsof -i:8080`，如果没有输出，说明端口已释放。此时再回到你的开发工具中重启 Tomcat 即可 。

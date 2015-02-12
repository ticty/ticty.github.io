---
layout:         post  
title:          Ubuntu配置备忘  
category:       系统  
tags:           Linux Ubuntu Debian 系统配置  
description:    Ubuntu的一些配置方法与命令，大部分Debian同样适用  
---

## apt配置

### proxy - 代理
1.  环境变量法
    只要在执行apt命令之前，将'http\_proxy=“...”' 变量添加到环境变量中即可.
    1.  运行时生效:

        ```
        $ export http_proxy="http://127.0.0.1:4445"
        $ sudo apt-get install ...
        ```

    2.  将该环境变量添加到配置中, 以下二选一

        ```
        $ echo 'http_proxy="http://127.0.0.1:4445"' >> ~/.bashrc
        $ sudo echo 'http_proxy="http://127.0.0.1:4445"' >> /etc/environment
        ```

        添加到变量重启终端生效，或运行`source` 命令立刻重新更新

2.  apt 配置法
    修改`/etc/apt/apt.conf`文件（不存在就新建），添加以下内容(示例)：

    ```
    Acquire:http:Proxy "http://127.0.0.1:4445/";
    *注意结尾分号不要忘记*
    ```

    此修改即时生效

### 添加更新源密钥
典型的错误提示

    W: GPG error: http://XXX Release: The following signatures couldn’t be verified because the public key is not available: NO_PUBKEY XXXXX

解决办法分以下两种:

1.  密钥存在于某密钥服务器, 运行如下命令:

        sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys XXXXXXXX

    其中最后的密钥是提示所缺的密钥序列的至少最后8位, 
    密钥提供服务器可修改成所需要地址
2.  密钥以密钥文件形式提供, 那么可以使用以下命令:

        cat $KeyFile | sudo apt-key add - 

    或直接下载并添加

        wget -q -O - https://XXX/XXX_key.pub | sudo apt-key add - 

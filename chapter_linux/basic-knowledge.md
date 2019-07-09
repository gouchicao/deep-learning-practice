# Linux 基础知识

## 文件管理

### 文件
* 创建文件
```bash
$ touch filename
```

* 删除文件
```bash
$ rm -f filename
```

* 递归删除文件
    * 使用格式
    ```bash
    $ find directory -name expression -type f | xargs rm -f
    ```
    * 递归删除当前目录下所有.DS_Store文件
    ```bash
    $ find . -name ".DS_Store" -type f | xargs rm -f
    $ find . -name ".DS_Store" -type f -delete
    ```

* 搜索文件
```bash
$ find directory -name expression
```
    * 列出nano开头文件路径
    ```bash
    $ find / -name nano*
    ```

* 文件软链接
```bash
$ ln -s /usr/bin/python3.6 /usr/bin/python
```

* 列出文件信息
```bash
$ ls
$ ll
```

### 目录
* 创建目录
```bash
$ mkdir directory
```

* 删除目录
```bash
$ rm -rf directory
```

* 递归删除目录
    * 使用格式
    ```bash
    $ find directory -name expression -type d | xargs rm -rf
    ```
    * 递归删除当前目录下所有images目录
    ```bash
    $ find ./ -name 'images' -type d | xargs rm -rf
    ```

* 切换目录
    * 切换到当前用户目录
    ```bash
    $ cd
    $ cd ~
    ```

    * 切换到之前的目录
    ```bash
    $ cd -
    ```

### 文件内容
* 搜索内容
    * 搜索一个文件
    ```bash
    $ grep 'text' hello.txt
    ```
    * 搜索多个文件
    ```bash
    $ grep 'text' hello.txt hi.txt
    ```
    * 搜索当前目录下所有文件
    ```bash
    $ grep 'text' *
    ```
    * 搜索当前目录（包含子目录）下所有文件
    ```bash
    $ grep -r 'text' *
    ```
    * 忽略字母大小写
    ```bash
    $ grep -i 'text' hello.txt
    ```
    * 显示当前目录下的目录
    ```bash
    $ ll | grep '^d'
    ```
    * 显示当前目录下的文件
    ```bash
    $ ll | grep '^-'
    ```
    * 显示当前目录下的所有目录及子目录
    ```bash
    $ ll -R | grep '^d'
    ```
    * 显示当前目录和子目录下的所有文件
    ```bash
    $ ll -R | grep '^-'
    ```

* 输出到标准输出窗口
```bash
$ cat /etc/profile
```

* 分页显示
```bash
$ cat /etc/profile | more
```

### 用户和组
* 修改文件所属用户和组
    * 修改文件所属用户
    ```bash
    $ chown wjj test.txt
    ```

    * 修改文件所属组
    ```bash
    $ chown :wjj test.txt
    ```

    * 修改文件所属用户和组
    ```bash
    $ chown wjj:wjj test.txt
    ```

* 修改文件所属组
```bash
$ chgrp wjj test.txt
```

## 软件管理

### 软件包管理器
* 配置源
```bash
$ nano /etc/apt/sources.list
```

* 更新软件列表
```bash
$ apt-get update
```

* 搜索软件
```bash
$ apt-cache search vim
```

* 安装软件
```bash
$ apt-get install vim
```

* 删除软件
```bash
$ apt-get purge vim
```

* 更新软件
```bash
$ apt-get upgrade
```

### 软件包安装
* 下载
```bash
$ apt-get install -d nano
```

* 安装
```bash
$ dpkg -i nano_2.9.3-2_amd64.deb
```

* 查找安装的软件
```bash
$ dpkg -l | grep nano
```

* 删除
```bash
$ dpkg -r nano
```

* 显示安装的软件
```bash
$ dpkg -l
```

### tar
* 打包
    * 打包（不压缩）
    ```bash
    $ tar -cvf filename.tar filename
    ```
    * 创建压缩包
    ```bash
    $ tar -zcvf filename.tar filename
    ```

* 解包
    * 解包（不压缩）
    ```bash
    $ tar -xvf filename.tar
    ```
    * 解压缩包
    ```bash
    $ tar -zxvf filename.tar
    ```

* 列出包的所有内容
```bash
$ tar -tf filename.tar
```

### 环境变量
* ~/.bashrc 配置完后，需要关闭当前控制台，以后打开的新控制台，配置就会起作用。
* /etc/profile 修改完文件后，运行source /etc/profile方可生效。

* 显示环境变量
    * 所有环境变量
    ```bash
    $ env
    ```
    * 指定环境变量
    ```bash
    $ echo $HOSTNAME
    ```

* 设置环境变量
```bash
$ export PYTHONPATH=$PYTHONPATH:`pwd`
```

* 移除环境变量
```bash
$ unset PYTHONPATH
```

## 服务service
* 启动服务
```bash
$ service ssh start
```

* 查看服务状态
```bash
$ service ssh status
```

* 停止服务
```bash
$ service ssh stop
```

* 重启服务
```bash
$ service ssh restart
```

* 设置开机自启动
```bash
$ update-rc.d ssh enable
```

* 设置开机不自启动
```bash
$ update-rc.d ssh disable
```

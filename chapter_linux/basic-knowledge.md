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
```bash
$ find directory -name expression -type f | xargs rm -f

e.g. 递归删除当前目录下所有.DS_Store文件
$ find . -name ".DS_Store" -type f | xargs rm -f
$ find . -name ".DS_Store" -type f -delete
```

* 搜索文件
```bash
$ find directory -name expression

e.g. 列出nano开头文件路径
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
```bash
$ find directory -name expression -type d | xargs rm -rf

e.g. 递归删除当前目录下所有images目录
$ find ./ -name 'images' -type d | xargs rm -rf
```

* 切换目录
```bash
$ cd path

e.g. 切换到当前用户目录
$ cd
$ cd ~

e.g. 切换到之前的目录
$ cd -
```

### 文件内容
* 搜索内容
```bash
$ grep pattern

e.g. 搜索一个文件
$ grep 'text' hello.txt

e.g. 搜索多个文件
$ grep 'text' hello.txt hi.txt

e.g. 搜索当前目录下所有文件
$ grep 'text' *

e.g. 搜索当前目录（包含子目录）下所有文件
$ grep -r 'text' *

e.g. 忽略字母大小写
$ grep -i 'text' hello.txt

e.g. 显示当前目录下的目录
$ ll | grep '^d'

e.g. 显示当前目录下的文件
$ ll | grep '^-'

e.g. 显示当前目录下的所有目录及子目录
$ ll -R | grep '^d'

e.g. 显示当前目录和子目录下的所有文件
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
```bash
e.g. 修改文件所属用户
$ chown wjj test.txt

e.g. 修改文件所属组
$ chown :wjj test.txt

e.g. 修改文件所属用户和组
$ chown wjj:wjj test.txt
```

* 修改文件所属组
```bash
$ chgrp wjj test.txt
```

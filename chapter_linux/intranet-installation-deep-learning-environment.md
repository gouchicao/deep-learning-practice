# 内网安装深度学习环境

## 安装操作系统
* 下载[Ubuntu 18.04]
* 安装Ubuntu 18.04

## 安装ssh
* 下载ssh
```bash
$ apt-get download openssh-client
$ apt-get download openssh-server
$ apt-get download openssh-sftp-server
```

* 安装ssh
```bash
$ dpkg -i *.deb
```

## 安装gcc
* 查看gcc的依赖
```bash
$ apt-get install -s gcc
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu cpp cpp-7 gcc-7 gcc-7-base libasan4 libatomic1 libbinutils
  libc-dev-bin libc6-dev libcc1-0 libcilkrts5 libgcc-7-dev libgomp1 libisl19 libitm1 liblsan0 libmpc3 libmpfr6 libmpx2
  libquadmath0 libtsan0 libubsan0 linux-libc-dev manpages manpages-dev
Suggested packages:
  binutils-doc cpp-doc gcc-7-locales gcc-multilib make autoconf automake libtool flex bison gdb gcc-doc gcc-7-multilib
  gcc-7-doc libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan4-dbg liblsan0-dbg libtsan0-dbg libubsan0-dbg
  libcilkrts5-dbg libmpx2-dbg libquadmath0-dbg glibc-doc man-browser
The following NEW packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu cpp cpp-7 gcc gcc-7 gcc-7-base libasan4 libatomic1 libbinutils
  libc-dev-bin libc6-dev libcc1-0 libcilkrts5 libgcc-7-dev libgomp1 libisl19 libitm1 liblsan0 libmpc3 libmpfr6 libmpx2
  libquadmath0 libtsan0 libubsan0 linux-libc-dev manpages manpages-dev
0 upgraded, 29 newly installed, 0 to remove and 10 not upgraded.
Inst manpages (4.15-1 Ubuntu:18.04/bionic [all])
Inst binutils-common (2.30-21ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libbinutils (2.30-21ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst binutils-x86-64-linux-gnu (2.30-21ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst binutils (2.30-21ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst gcc-7-base (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libisl19 (0.19-1 Ubuntu:18.04/bionic [amd64])
Inst libmpfr6 (4.0.1-1 Ubuntu:18.04/bionic [amd64])
Inst libmpc3 (1.1.0-1 Ubuntu:18.04/bionic [amd64])
Inst cpp-7 (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst cpp (4:7.3.0-3ubuntu2.1 Ubuntu:18.04/bionic-updates [amd64])
Inst libcc1-0 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libgomp1 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libitm1 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libatomic1 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libasan4 (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst liblsan0 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libtsan0 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libubsan0 (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libcilkrts5 (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libmpx2 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libquadmath0 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libgcc-7-dev (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst gcc-7 (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst gcc (4:7.3.0-3ubuntu2.1 Ubuntu:18.04/bionic-updates [amd64])
Inst libc-dev-bin (2.27-3ubuntu1 Ubuntu:18.04/bionic [amd64])
Inst linux-libc-dev (4.15.0-46.49 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst libc6-dev (2.27-3ubuntu1 Ubuntu:18.04/bionic [amd64])
Inst manpages-dev (4.15-1 Ubuntu:18.04/bionic [all])
Conf manpages (4.15-1 Ubuntu:18.04/bionic [all])
Conf binutils-common (2.30-21ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libbinutils (2.30-21ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf binutils-x86-64-linux-gnu (2.30-21ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf binutils (2.30-21ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf gcc-7-base (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libisl19 (0.19-1 Ubuntu:18.04/bionic [amd64])
Conf libmpfr6 (4.0.1-1 Ubuntu:18.04/bionic [amd64])
Conf libmpc3 (1.1.0-1 Ubuntu:18.04/bionic [amd64])
Conf cpp-7 (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf cpp (4:7.3.0-3ubuntu2.1 Ubuntu:18.04/bionic-updates [amd64])
Conf libcc1-0 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libgomp1 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libitm1 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libatomic1 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libasan4 (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf liblsan0 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libtsan0 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libubsan0 (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libcilkrts5 (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libmpx2 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libquadmath0 (8.2.0-1ubuntu2~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libgcc-7-dev (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf gcc-7 (7.3.0-27ubuntu1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf gcc (4:7.3.0-3ubuntu2.1 Ubuntu:18.04/bionic-updates [amd64])
Conf libc-dev-bin (2.27-3ubuntu1 Ubuntu:18.04/bionic [amd64])
Conf linux-libc-dev (4.15.0-46.49 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf libc6-dev (2.27-3ubuntu1 Ubuntu:18.04/bionic [amd64])
Conf manpages-dev (4.15-1 Ubuntu:18.04/bionic [all])
```

* 下载gcc及依赖包
```bash
$ apt-get download binutils binutils-common binutils-x86-64-linux-gnu cpp cpp-7 gcc-7 gcc-7-base libasan4 libatomic1 libbinutils libc-dev-bin libc6-dev libcc1-0 libcilkrts5 libgcc-7-dev libgomp1 libisl19 libitm1 liblsan0 libmpc3 libmpfr6 libmpx2 libquadmath0 libtsan0 libubsan0 linux-libc-dev manpages manpages-dev gcc
```

* 安装gcc
```bash
$ dpkg -i *.deb
```

## 安装make
* 下载make
```bash
apt-get download  make
```

* 安装make
```bash
dpkg -i *.deb
```

## 安装Nvidia GPU驱动
* 禁⽤nouveau驱动
```bash
编辑配置文件
$ nano /etc/modprobe.d/blacklist-nouveau.conf 
增加下面内容 
blacklist nouveau
options nouveau modeset=0
保存退出

让配置内容生效
$ sudo update-initramfs -u 
```

* 重启计算机
```bash
$ reboot
```

* 验证禁用nouveau驱动是否成功
```bash
查看没有任何信息，代表禁⽤成功
$ lsmod | grep nouveau 
```

* 下载[Nvidia GPU驱动]
```bash
$ wget https://cn.download.nvidia.cn/XFree86/Linux-x86_64/418.56/NVIDIA-Linux-x86_64-418.56.run
```

* 安装Nvidia GPU驱动
```bash
$ sh NVIDIA-Linux-x86_64-418.56.run
```

## 安装Docker-CE
* 下载安装包
```bash
$ wget https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/containerd.io_1.2.2-3_amd64.deb
$ wget https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/docker-ce-cli_18.09.2~3-0~ubuntu-bionic_amd64.deb
$ wget https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/docker-ce_18.09.2~3-0~ubuntu-bionic_amd64.deb
```

* 安装Docker-CE
```bash
dpkg -i *.deb
```

## 安装nvidia-docker2
* nvidia-docker2
```bash
$ apt-get download nvidia-container-runtime nvidia-docker2
```

* 安装nvidia-docker2
```bash
$ dpkg -i *.deb
```

* 重新启动Docker daemon
```bash
$ systemctl restart docker
```

## 验证容器内使用GPU
* 摘取镜像
```bash
$ docker pull nvidia/cuda:9.0-base
```

* 镜像保存为tar包
```bash
$ docker save -o cuda9.0-base.tar nvidia/cuda:9.0-base
```

* 导入镜像到内网机
```bash
$ docker load -i cuda9.0-base.tar
```

* 运行容器查看GPU信息
```bash
$ docker run --runtime=nvidia --rm nvidia/cuda:9.0-base nvidia-smi
```

[Ubuntu 18.04]: http://releases.ubuntu.com/18.04/
[Nvidia GPU驱动]: https://www.nvidia.com/Download/index.aspx?lang=en-us
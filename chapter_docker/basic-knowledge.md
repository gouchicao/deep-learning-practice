# Docker 基础知识

## 列出镜像列表
```bash
$ sudo docker images
```

## 运行容器
* 命令行交互运行
```bash
$ sudo docker run -it busybox:latest
```

* 后台运行
```bash
$ sudo docker run -d busybox:latest
```

* 分配指定的显卡给容器
```bash
$ sudo docker run --runtime=nvidia -d -e NVIDIA_VISIBLE_DEVICES=1 tensorflow/tensorflow:latest-gpu-py3
```

## 进入当前运行中的容器
```bash
$ sudo docker exec -it darknet bash
# 按Ctrl+P,Ctrl+Q退出容器，不停止容器运行。
```

## 删除容器
```bash
$ docker rm -v test
```

## 导出镜像
```bash
$ docker save -o busybox.tar busybox:latest
```

## 导入镜像
```bash
$ docker load -i busybox.tar
```

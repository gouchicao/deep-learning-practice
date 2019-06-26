# Dockerfile

## .dockerignore file
当你项目中的文件或者目录不想加入到构建的镜像中，可以配置到.dockerignore文件中。
这有一个[例子](https://github.com/gouchicao/darknet-serving/blob/master/.dockerignore)：
```
.git
.dockerignore
Dockerfile
.DS_Store
.gitignore
README.md
object_detection.proto
__pycache__
model
test-images
tmp
```

## 你需要掌握的知识
* [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)

## 最佳实践
这里以[darknet-serving](https://github.com/gouchicao/darknet-serving/blob/master/Dockerfile)为例子
```
FROM nvidia/cuda:10.0-cudnn7-runtime-ubuntu18.04
LABEL maintainer="wang-junjian@qq.com"

RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    nano \
    && rm -rf /var/lib/apt/lists/*

ADD requirements.txt /darknet-serving/
WORKDIR /darknet-serving
RUN pip3 install --no-cache-dir -r requirements.txt

ADD . /darknet-serving/

ENTRYPOINT ["python3", "darknet_model_server.py"]
```


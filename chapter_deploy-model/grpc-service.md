# gRPC服务
> 基于Python语言的开发

## 安装gRPC和protoc等
```bash
$ sudo python3 -m pip install grpcio
$ sudo python3 -m pip install grpcio-tools
```

## 使用protocol buffer定义接口
### object_detection.proto
```
syntax = "proto3";

//darknet yolov3 object detection
service ObjectDetection {
  //客户端到服务器端的流式RPC
  //对图像的数据进行对象检测
  rpc detect (stream UploadImageRequest) returns (DetectResponse) {}
}

//上传图像数据块
message UploadImageRequest {
  bytes data_block = 1;
}

//返回对象检测结果
message DetectResponse {
  repeated Object object = 1;
}

//对象的边框
message Rectangle {
  int32 x = 1;
  int32 y = 2;
  int32 w = 3;
  int32 h = 4;
}

//检测出的对象
message Object {
  string name = 1;
  float confidence = 2;
  Rectangle rectangle = 3;
}
```
* gRPC默认最大消息被设置为4MB。所以这里使用了客户端到服务器端的流式RPC方式对上传的图像进行传输。

## 生成gRPC代码
```bash
$ python3 -m grpc_tools.protoc -I. --python_out=. --grpc_python_out=. object_detection.proto
```

## 参考资料
[Python Quick Start](https://grpc.io/docs/quickstart/python/)

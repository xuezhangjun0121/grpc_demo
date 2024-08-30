# grpc_demo
grpc_demo

# 这是一个简单的grpc_demo
```
如果没有安装 protoc，执行命令 go get -u github.com/golang/protobuf/protoc-gen-go 进行安装。

虽然 gRPC 支持多种语言，但是为了统一，我文章中的代码都使用 Go。
```

# go.mod文件生成过程
```
在项目目录下执行： go mod init grpc_demo
更新go.mod：go mod tidy
```


# 通过这个命令生成的ProductInfo.pb.go文件
```
protoc --go_out=plugins=grpc:. --go_opt=paths=source_relative ProductInfo.proto
```

//这是使用 Protocol Buffers 的编译器 protoc 命令行工具来生成 Go 语言代码的命令，以下是各个参数的含义：
//
//    --go_out=plugins=grpc:.: 表示将 .proto 文件编译为 Go 语言代码，并使用 gRPC 插件来生成支持 gRPC 协议的代码。其中，. 表示输出文件的目录为当前目录。
//
//    --go_opt=paths=source_relative: 表示设置生成的 Go 语言 import 路径为源文件的相对路径，以避免在不同项目中重复导入同一个包时出现问题。
//
//    ProductInfo.proto: 表示要编译的 .proto 文件名。
//
//综上所述，该命令的作用是将指定的 .proto 文件编译为支持 gRPC 协议的 Go 语言代码，并将输出文件保存在当前目录下，同时将 import 路径设置为源文件的相对路径。

启动服务端：
```
go run server/main.go

# 如下
PS O:\我的github项目\grpc_demo\product\server> go run .\server\main.go
2024/08/30 10:05:42 start gRPC listen on port :50051
```
启动客户端：
```
go run client/main.go

如下：
PS O:\我的github项目\grpc_demo\product\client> go run .\main.go
2024/08/30 10:06:26 add product success, id =  96c08336-e418-49ce-8c12-721f6170e82c
2024/08/30 10:06:26 get prodcut success : id:"96c08336-e418-49ce-8c12-721f6170e82c"  name:"Mac Book Pro 2019"  description:"From Apple Inc."

```
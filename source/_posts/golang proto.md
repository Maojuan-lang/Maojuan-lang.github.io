---
title: proto
---

```protobuf
syntax = "proto3";

// 命名空间,需要与go_package的文件夹名字相同
package service;

// 作用于 --go_out=
option go_package = "./../../service";

// protoc --proto_path=IMPORT_PATH --cpp_out=DST_DIR --java_out=DST_DIR --python_out=DST_DIR --go_out=DST_DIR --ruby_out=DST_DIR --objc_out=DST_DIR --csharp_out=DST_DIR path/to/file.proto
message Student{
  string name = 1;
  int32 age = 2;
}
```

```
Go plugins for the protocol compiler:

Install the protocol compiler plugins for Go using the following commands:

    $ go install google.golang.org/protobuf/cmd/protoc-gen-go
    $ go install google.golang.org/grpc/cmd/protoc-gen-go-grpc
Update your PATH so that the protoc compiler can find the plugins:

    $ export PATH="$PATH:$(go env GOPATH)/bin"
```

```
protoc --go_out=. --go-grpc_out=. .\xxx.proto
```


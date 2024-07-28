---
title: protoc
---

```protobuf
syntax = "proto3";

// 作用于 --go_out=
option go_package = "./..";

// protoc --proto_path=IMPORT_PATH --cpp_out=DST_DIR --java_out=DST_DIR --python_out=DST_DIR --go_out=DST_DIR --ruby_out=DST_DIR --objc_out=DST_DIR --csharp_out=DST_DIR path/to/file.proto
message Student{
  string name = 1;
  int32 age = 2;
}
```


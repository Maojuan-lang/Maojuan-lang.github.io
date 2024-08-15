---
title: golang rpc
date: 2024-08-02
---

```go
// server
package main

import (
	"fmt"
	"net"
	"net/rpc"
)

type Hello struct{
}
// bind func to Hello type
func (this Hello) SayHello(req string, res *string) error {
	*res = "你好，" + req
	return nil
}

func main() {
	// registe rpc service name
	err := rpc.RegisterName("hello",new(Hello))
	if err != nil{
		fmt.Println(err)
	}
	
	listener, err2 := net.Listen("tcp", "127.0.0.1:8001")
	if err2 != nil{
		fmt.Println(err2)
	}
	defer listener.Close()

	for{
		fmt.Println("开始建立服务")
		conn, err3 := listener.Accept()
		if err3 != nil{
			fmt.Println(err3)
		}
		rpc.ServeConn(conn)
	}

}
```

```go
// client
package main

import (
	"fmt"
	"net/rpc"
)

func main() {
	conn, err := rpc.Dial("tcp","127.0.0.1:8001")
	if err != nil{
		fmt.Println("Dial err:",err)
		return
	}
	defer conn.Close()

	var reply string

	// call the rpc service's func
	err = conn.Call("hello.SayHello", "David", &reply)

	if err != nil{
		fmt.Println("Call err:",err)
	}

	fmt.Println(reply)
}
```


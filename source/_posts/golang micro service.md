---
title: golang micro service
date: 2024-08-25
---

```
service

package main

import (
	"context"
	"log"

	pb "github.com/go-micro/examples/helloworld/proto"
	"go-micro.dev/v4"
)

type Greeter struct{}

func (g *Greeter) Hello(ctx context.Context, req *pb.Request, rsp *pb.Response) error {
	rsp.Greeting = "Hello " + req.Name
	return nil
}

func main() {
	service := micro.NewService(
		micro.Name("helloworld"),
		micro.Address(":8080"),
	)

	service.Init()

	pb.RegisterGreeterHandler(service.Server(), new(Greeter))

	if err := service.Run(); err != nil {
		log.Fatal(err)
	}
}
```

```
client

package main

import (
	"context"
	"fmt"
	example "github.com/go-micro/examples/helloworld/proto"
	"go-micro.dev/v4"
	"go-micro.dev/v4/client"
	"go-micro.dev/v4/metadata"
)

func main() {
	service := micro.NewService()
	service.Init()

	fmt.Println("\n--- Call example ---")
	for i := 0; i < 10; i++ {
		call(i, service.Client())
	}
}

func call(i int, c client.Client) {
	// Create new request to service go.micro.srv.example, method Example.Call
	req := c.NewRequest("helloworld", "Greeter.Hello", &example.Request{
		Name: "John",
	})

	// create context with metadata
	ctx := metadata.NewContext(context.Background(), map[string]string{
		"X-User-Id": "john",
		"X-From-Id": "script",
	})

	rsp := &example.Response{}

	// Call service
	if err := c.Call(ctx, req, rsp); err != nil {
		fmt.Println("call err: ", err, rsp)
		return
	}

	fmt.Println("Call:", i, "rsp:", rsp.Greeting)
}
```

```
proto

syntax = "proto3";

service Greeter {
	rpc Hello(Request) returns (Response) {}
}

message Request {
	string name = 1;
}

message Response {
	string greeting = 2;
}
```






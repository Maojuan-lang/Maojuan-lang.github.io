---
title: Golang二进制操作
---

正数的原码补码相同

负数的原码符号位不动，其余各位取反加一得到补码。

负数的补码符号位不动，其余各位取反加一得到原码。

```go
package main

import "fmt"

func main() {
	var num1 int8 = 1
	var num2 int8 = 2
	// 结果为1，因为num_1是奇数
	fmt.Println(num1 & 1)
	// 结果为0，因为num_2是偶数
	fmt.Println(num2 & 1)
	fmt.Printf("%b", int8(127))
	fmt.Println()
	// 正数的情况下以下两行等价
	fmt.Printf("%b", int8(127)>>1)
	fmt.Println()
	fmt.Println(int8(127)/2)
	// 正数的情况下以下两行等价
	fmt.Printf("%b", int8(127)>>3)
	fmt.Println()
	// 除数为2的3次方
	fmt.Println(int8(127)/8)
}
```


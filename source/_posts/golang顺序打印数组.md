---
title: golang顺序打印数组
---

```go
package main

import (
	"fmt"
)

func main() {
	m := make(map[int]string)

	// 往map中添加键值对
	m[1] = "one"
	m[2] = "two"
	m[3] = "three"

	var keyArray []int
	for key := range m {
        // 数组自动排序
		keyArray = append(keyArray, key)
	}

	// 遍历map
	for _, value := range keyArray {
		fmt.Println("Key:", value, "Value:", m[value])
	}
}
```


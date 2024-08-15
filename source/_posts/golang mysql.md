---
title: golang mysql
date: 2024-08-02
---

```
package main

import (
    "database/sql"
    "fmt"
    _ "github.com/go-sql-driver/mysql"
    "log"
)

func main() {
    // 数据库连接信息
    db, err := sql.Open("mysql", "username:password@tcp(127.0.0.1:3306)/database_name")
    if err != nil {
        log.Fatal(err)
    }
    defer db.Close()

    // 查询数据库中的第一条数据
    var (
        id   int
        name string
    )
    err = db.QueryRow("SELECT id, name FROM table_name LIMIT 1").Scan(&id, &name)
    if err != nil {
        log.Fatal(err)
    }

    // 打印查询结果
    fmt.Printf("ID: %d, Name: %s\n", id, name)
}
```


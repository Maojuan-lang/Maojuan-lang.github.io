---
title: byte数字转可读文字Python
date: 2024-08-03
---

```python
str = "10 6 100 97 109 105 110 103 16 18"
str_list = str.split(" ")
# 列表推导式
int_list = [int(num) for num in str_list]
# 使用map函数和lambda表达式
int_list = list(map(lambda num: int(num), str_list))
str_byte = bytes(int_list)
print(str_byte.decode("utf-8"))
```


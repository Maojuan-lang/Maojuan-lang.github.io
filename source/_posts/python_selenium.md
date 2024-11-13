---
title: python_selenium
date: 2024-11-13
---

```
from openpyxl.reader.excel import load_workbook
from selenium import webdriver
from selenium.webdriver.common.by import By
from webdriver_manager.chrome import ChromeDriverManager

# 创建一个新的工作簿
wb = load_workbook('output.xlsx')
ws = wb.active  # 获取活动工作表

for page_num in range(84,154):
    driver = webdriver.Chrome(ChromeDriverManager().install())
    driver.get(f"https://www.baidu.com/{page_num}")
    articles = driver.find_elements(By.XPATH,"/html/body/article")
    # 列数据处理
    for index,article in enumerate(articles[:2] + articles[3:]):
        title = article.find_element(By.XPATH,"header/h2/a").text
        try:
            like_num = article.find_element(By.XPATH, "div/a[1]").text.split("(")[1].split(")")[0]
            read_num = article.find_element(By.XPATH,"div/span[2]").text.split("(")[1].split(")")[0]
            print(10*(page_num-1)+index+1)
            print(title)
            print(read_num)
            print("*"*6)
            ws.cell(row=10*(page_num-1)+index+1, column=1, value=title)  # 第一列数据
            ws.cell(row=10*(page_num-1)+index+1, column=2, value=read_num)  # 第二列数据
            ws.cell(row=10*(page_num-1)+index+1, column=3, value=like_num)  # 第二列数据
            # 保存 Excel 文件
            wb.save('output.xlsx')
        except:
            pass
    # 关闭浏览器
    driver.quit()
```


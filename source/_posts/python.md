---
title: Python_Xiandu
---

### 爬取闲读的文章，BeautifulSoup库的使用

``` python
from bs4 import BeautifulSoup
import requests

url = "http://gank.io/xiandu/wow/page/" + ( input("page:") or "1" )
response = requests.get(url)
if response.status_code == 200:
    soup = BeautifulSoup(response.text, 'lxml')
    for div in soup.find_all(class_ = 'site-title'):
        print("\n", div.string+" : "+div.get("href"))
    print()
}
```

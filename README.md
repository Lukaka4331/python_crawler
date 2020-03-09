# python_crawler
python_爬蟲菜雞入門
#

* 安裝selenium

```py
pip install selenium
```

* 下載webdriver

Selenium 需要透過特殊的 WebDriver 才能跟瀏覽器溝通，進行各種控制，而不同的瀏覽器所對應的 WebDriver 也不同，

以下是各種瀏覽器的 WebDriver 下載點：

| 瀏覽器 | WebDriver |
| :--- | :--- |
| Chrome | [ChromeDriver](https://sites.google.com/a/chromium.org/chromedriver/) |
| Edge | [Microsoft WebDriver](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/) |
| Firefox | [geckodriver](https://github.com/mozilla/geckodriver/releases) |
| Safari | [WebDriver Support in Safari 10](https://webkit.org/blog/6900/webdriver-support-in-safari-10/) |

請依照想要控制的瀏覽器，下載對應的 WebDriver 程式。

同時請注意瀏覽器與 WebDriver 的版本，如果兩者的版本不同，是不能用的。

* 安裝chromedriver

資源 : [ChromeDriver - WebDriver for Chrome](https://sites.google.com/a/chromium.org/chromedriver/downloads)

1. 將unzip的exe執行檔放到chrome的安裝目錄下\(C:\Program Files \(x86\)\Google\Chrome\Application\)-我的安裝路徑

2. 添加環境變量

對變量path進行編輯加入chrome的安裝目錄

【Day 2】CSV File Reading and Writing

用逗號分隔的資料（,）

* [標準的模組](https://docs.python.org/3.7/library/csv.html) 來操作 CSV 資料

* 用[csv.reader](https://docs.python.org/3.7/library/csv.html#csv.reader)方法來讀取檔案

讀取檔案&print\(\)

```py
import csv
with open('mock_data.csv', newline='') as csvfile:
reader = csv.reader(csvfile, delimiter=',', quotechar='"')
for row in reader:
print(', '.join(row))
```

* 用[csv.writer](https://docs.python.org/3.7/library/csv.html#csv.writer)方法來寫入檔案

寫入檔案

```py
import csv
with open('mock_data.csv', 'a', newline='') as csvfile:
writer = csv.writer(csvfile, delimiter=',', quotechar='"', quoting=csv.QUOTE_MINIMAL)
writer.writerow([3, 'Corri', 'Campling', 'Female', 'Sweden'])
```

### 把`list`轉換為`dict`

前面都是把資料以`list`型態來處理資料，如果欄位的順序有變，程式都要一併修改。

但既然都有表頭了，有沒有辦法用`dict`的型態來方便處理呢？

csv 模組另外提供了`csv.DictReader`和`csv.DictWriter`來滿足這個需求。

* [csv.DictReader](https://docs.python.org/3.7/library/csv.html#csv.DictReader)

```py
import csv
with open('mock_data.csv', newline='') as csvfile:
reader = csv.DictReader(csvfile, delimiter=',', quotechar='"')
for row in reader:
print(row['first_name'], row['last_name'])
```

* [csv.DictWriter](https://docs.python.org/3.7/library/csv.html#csv.DictWriter)

```py
import csv
with open('mock_data.csv', 'a', newline='') as csvfile:
fieldnames = ['id', 'first_name', 'last_name', 'gender', 'country']
writer = csv.DictWriter(csvfile, fieldnames, delimiter=',', quotechar='"')
writer.writerow({
'id': 4,
'first_name': 'Salvatore',
'last_name': 'Gaitskill',
'gender': 'Male',
'country': 'Indonesia'
})
```




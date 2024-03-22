# สร้าง WebScapping อย่างง่ายด้วย Python
## _ดึงข้อมูลพยากรณ์อากาศมาแสดง_
![1](/media/1-form.png)
![2](/media/2-form.png)
## 1.ติดตั้ง lib
pip install selenium webdriver-manager
## 2.Source code
นำโค้ดชุดนี้ไปวาง แล้วบันทึก
```sh
from selenium import webdriver
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.keys import Keys
```
เปิดเว็ปเบราว์เซอร์ค้นหาด้วย google
```sh
service = Service(ChromeDriverManager().install())
driver = webdriver.Chrome(service=service)
driver.maximize_window()
url ='https://www.google.com/'
driver.get(url)
```
ค้นหาด้วยข้อความ "bangkok weather" โดยการระบุ xpath
```sh
search_field = driver.find_element('xpath','//*[@id="APjFqb"]')
search_field.send_keys('bangkok weather')
search_field.send_keys(Keys.ENTER)
```
กดปุ่ม enter
```sh
temperture = driver.find_element('xpath','//*[@id="wob_tm"]').text
print(temperture)   
```
ปิดเว็ปเบราว์เซอร์
```sh
import time
time.sleep(3)
driver.close()
```
#### ตัวอย่างผลลัพธ์ที่ได้
![3](/media/3-form.png)
อุณหภูมิ 33 องศา

# viatech
interview quizzes

程式邏輯題目
Q1 : 國泰補習班中，有五位學生期中考的成績分別為[53, 64, 75, 19, 92]，但是老師在輸入成績的時候看反了，把五位學生的成績改成了[35, 46, 57, 91, 29]，請用一個函數來將學生的成績修正。

A1 : 
"def ReverseNumber(數字列表):
    a = []
    for i in 數字列表:
        iReverse = int(str(i)[::-1])
        a.append(iReverse)
    return a

成績 = [35, 46, 57, 91, 29]

ReverseNumber(成績)"


Q2 : 國泰銀行要慶祝六十周年，需要買字母貼紙來布置活動空間，文字為"Hello welcome to Cathay 60th year anniversary"，請寫一個程式計算每個字母(大小寫視為同個字母)出現次數

"文字 = ""Hello welcome to Cathay 60th year anniversary""

A2 : 
"文字 = ""Hello welcome to Cathay 60th year anniversary""

# 將文字轉換為大寫，以便不區分大小寫
文字 = 文字.upper()

# 創建一個字典來存儲每個字母的出現次數
字母計數 = {}

# 遍歷文字中的每個字符
for 字母 in 文字:
    if (字母.isalpha() or 字母.isdigit()):  # 確保只計算字母，排除空格和符號
        if 字母 in 字母計數:
            字母計數[字母] += 1
        else:
            字母計數[字母] = 1

# 定義排序的順序
排序順序 = ""0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ""

# 使用排序順序對字母計數進行排序
排序後的字母計數 = sorted(字母計數.items(), key=lambda x: 排序順序.index(x[0]))

# 輸出排序後的字母計數
for 字母, 次數 in 排序後的字母計數:
    print(f""{字母.upper()} {次數} "")"
![image](https://github.com/IRONYEH/viatech/assets/144384730/71fd6863-141c-4b29-9390-feb2e71ba8cd)


Q3: "QA部門今天舉辦團康活動，有n個人圍成一圈，順序排號。從第一個人開始報數（從1到3報數），凡報到3的人退出圈子。
請利用一段程式計算出，最後留下的那位同事，是所有同事裡面的第幾順位?"


A3 : 
"def 最後留下的順位(n):
    # 當只有一個人時，他就是最後留下的人，順位為1
    if n == 1:
        return 1
    else:
        # 當有多個人時，計算在下一輪中報數的起始位置（每次報到3的人出局）
        # 並遞迴計算下一輪的最後留下的人的順位
        return (最後留下的順位(n - 1) + 3 - 1) % n + 1

n = 100  # 假設有100個人
最後順位 = 最後留下的順位(n)
print(f""最後留下的同事是所有同事中的第 {最後順位} 順位。"")"
![image](https://github.com/IRONYEH/viatech/assets/144384730/ba234691-b1f2-4868-b583-bd36af960bb2)


自動化測試

Q1. 使用Chrome App到國泰世華銀行官網(https://www.cathaybk.com.tw/cathaybk/)並將畫面截圖。

A1 :
from selenium import webdriver
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities
from time import sleep

# 设置Chromedriver的路径
chromedriver_path = "./chromedriver.exe"

# 创建一个Chrome WebDriver实例
chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("mobileEmulation", {"deviceName": "iPhone X"})

# 创建一个Chromedriver Service对象，指定路径
service = webdriver.chrome.service.Service(chromedriver_path)

# 启动Chromedriver服务
service.start()

# 创建Chromedriver实例，连接到已启动的服务
driver = webdriver.Chrome(service=service, options=chrome_options)

# 打开指定的网页
url = 'https://www.cathaybk.com.tw/cathaybk'  # 将URL替换为您要访问的网页
driver.get(url)

# 在此之后，您的浏览器应该在移动设备模式下

# 截取页面截图并保存到文件
screenshot_path = '國泰世華銀行手機版網頁截圖.png'
driver.save_screenshot(screenshot_path)

Q2. 點選左上角選單，進入 個人金融 > 產品介紹 > 信用卡列表，需計算有幾個項目並將畫面截圖。

A2 :
# 睡一下
sleep(2)

# 建立行為鍊
ac = ActionChains(driver)

# 移到指定座標 (從 0,0 開始)
ac.move_by_offset(27,28)

# 點擊一下
ac.click()

# 等待一段时间
sleep(2)  # 在这里休息2秒钟

# 移到指定座標 (從 0,0 開始)
ac.move_by_offset(27,212)

# 點擊一下
ac.click()

# 等待一段时间
sleep(5)  # 在这里休息2秒钟

# 移到指定座標 (從 0,0 開始)
ac.move_by_offset(27,273)

# 點擊一下
ac.click()

# 等待一段时间
sleep(5)  # 在这里休息2秒钟

# 執行
ac.perform()

# 截取屏幕截图并保存到文件
screenshot_path = '信用卡選單.png'
driver.save_screenshot(screenshot_path)

print('下載「信用卡選單.png」完成')










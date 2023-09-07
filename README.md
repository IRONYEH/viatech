# viatech
interview quizzes

國泰補習班中，有五位學生期中考的成績分別為[53, 64, 75, 19, 92]，但是老師在輸入成績的時候看反了，把五位學生的成績改成了[35, 46, 57, 91, 29]，請用一個函數來將學生的成績修正。

def ReverseNumber(數字列表):
    a = []
    for i in 數字列表:
        iReverse = int(str(i)[::-1])
        a.append(iReverse)
    return a

成績 = [35, 46, 57, 91, 29]

ReverseNumber(成績)

國泰銀行要慶祝六十周年，需要買字母貼紙來布置活動空間，文字為"Hello welcome to Cathay 60th year anniversary"，請寫一個程式計算每個字母(大小寫視為同個字母)出現次數

"文字 = ""Hello welcome to Cathay 60th year anniversary""

將文字轉換為大寫，以便不區分大小寫
文字 = 文字.upper()

創建一個字典來存儲每個字母的出現次數
字母計數 = {}

遍歷文字中的每個字符
for 字母 in 文字:
    if (字母.isalpha() or 字母.isdigit()):  # 確保只計算字母，排除空格和符號
        if 字母 in 字母計數:
            字母計數[字母] += 1
        else:
            字母計數[字母] = 1

定義排序的順序
排序順序 = ""0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ""

使用排序順序對字母計數進行排序
排序後的字母計數 = sorted(字母計數.items(), key=lambda x: 排序順序.index(x[0]))

輸出排序後的字母計數
for 字母, 次數 in 排序後的字母計數:
    print(f""{字母.upper()} {次數} "")"

"QA部門今天舉辦團康活動，有n個人圍成一圈，順序排號。從第一個人開始報數（從1到3報數），凡報到3的人退出圈子。
請利用一段程式計算出，最後留下的那位同事，是所有同事裡面的第幾順位?"


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

1. 使用Chrome App到國泰世華銀行官網(https://www.cathaybk.com.tw/cathaybk/)並將畫面截圖。

from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.common.by import By


创建一个 Chrome WebDriver 的 Service 对象，并指定 Chrome WebDriver 的路径
chrome_driver_path = "./chromedriver.exe"  # 请替换为您的 Chrome WebDriver 的路径
service = Service(executable_path=chrome_driver_path)

使用 Service 对象创建 Chrome WebDriver 实例
driver = webdriver.Chrome(service=service)

打开指定的网页
url = 'https://www.cathaybk.com.tw/cathaybk'
driver.get(url)

截取屏幕截图并保存到文件
screenshot_path = '國泰世華銀行官網.png'
driver.save_screenshot(screenshot_path)

print('下載「國泰世華銀行官網.png」完成')

2. 點選左上角選單，進入 個人金融 > 產品介紹 > 信用卡列表，需計算有幾個項目並將畫面截圖。

建立行為鍊
ac = ActionChains(driver)

移到指定座標 (從 0,0 開始)
ac.move_by_offset(516,33)

點擊一下
ac.click()

執行
ac.perform()

睡一下
sleep(5)

截取屏幕截图并保存到文件
screenshot_path = '信用卡選單.png'
driver.save_screenshot(screenshot_path)

print('下載「信用卡選單.png」完成')










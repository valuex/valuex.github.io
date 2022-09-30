# 零 写在前面
Playwright 是微软于推出的一个Web自动化测试库。  
Playwright 接口支持 Python，Javascript，C#等语言调用。  
个人遇到Playwright的感觉，如同若干年前遇到AuthoHotKey一样开心。  
如果说AutoHotKey以极低的上手门槛实现了Windows本地客户端自动化操作，那PlayWright就以基地门槛实现了Web的自动化操作，可以说PlayWright就是网页版的AutoHotKey。
在个人看来，PlayWright从几个方面，降低了Web自动化操作门槛：
1. 简单配置下`headless=False` 模式，就可以继承当前登录的浏览器的状态，不用再去配置复杂的head。
    - 也就是说，如果用`browser=p.chromium.launch(headless=False)` ，启动chromium，会自动加载在chrome中已登录的网站的状态。
2. **定位网页元素很方便**，`locator` 或者 `selector` 中可以利用xpath，css selector等方式进行元素定位。
3. **等待网页加载完成也很方便**:
    - `page.wait_for_selector('element_xpath',timeout=10000)` 就可以实现等待满足某个xpath的element出现，等待时长为10s。
    - `page.wait_for_selector("text=element_text",timeout=10000)`  就可以实现等待内容为lement_text的element出现，，等待时长为10s。


# 一. PlayWright安装
## 1. 安装playwright 库  
cmd窗口中运行 `pip install pytest-playwright`     
## 2. 安装chromium等浏览器  
### 2.1 在线安装  
cmd窗口中运行 `playwright install`  
### 2.2 离线安装 
a) 下载最新版chromium 或者跟playwright对应版本的chromium  
b) 下载地址： https://chromium.woolyss.com/download/    
c) 下载好后，解压缩并将解压缩的文件夹复制到`c:\Users\<user name>\AppData\Local\ms-playwright\`下    
       路径下，注意修改<user name>为你的实际用户名。   
d) 最终文件夹结构：`c:\Users\<user name>\AppData\Local\ms-playwright\chrome-xxxx\chrome-win\chrome.exe`    
       注：XXXX为数字，可以为任何数字    
e) 修改`Playwright安装路径\driver\/browsers.json`中的内容
      注：`Playwright安装路径` 一般在`C:\Python310\Lib\site-packages\playwright\driver\package\browsers.json`，也可以用Everything搜索`browsers.json`查找  
      位置①处：修改为目录chrome-xxxx\chrome-win\chrome.exe中的xxxx  
      位置②处: 修改为目录chrome-xxxx\chrome-win\下的xxx.x.xxxx.xx.manifest对应的文件名xxx.x.xxxx.xx  
    ![image](https://user-images.githubusercontent.com/3627812/193300470-29899a36-6590-4312-b3cf-9acb5e95a475.png)  

f)  配置完后，在cmd窗口中执行`python -m playwright install` 进行离线安装    
    
### 2.3 安装完后运行下述语句进行测试
`playwright codegen http://www.baidu.com`
# 二. 第一个PlayWright脚本
 ``` python
    from playwright.sync_api import Playwright, sync_playwright, expect


def run(playwright: Playwright) -> None:
    browser = playwright.chromium.launch(headless=False)
    context = browser.new_context()

    # Open new page
    page = context.new_page()

    # Go to http://www.baidu.com/
    page.goto("http://www.baidu.com/")

    # Click input[name="wd"]
    page.locator("input[name=\"wd\"]").click()

    # Fill input[name="wd"]
    page.locator("input[name=\"wd\"]").fill("test")

    # Click text=百度一下
    page.locator("text=百度一下").click()
    page.wait_for_url("http://www.baidu.com/s?ie=utf-8&f=8&rsv_bp=1&rsv_idx=1&tn=baidu&wd=test")

    # ---------------------
    context.close()
    browser.close()


with sync_playwright() as playwright:
    run(playwright)
```
# 三. 一些有用的参考网址  
    
    Playwright 参考文档： https://playwright.dev/python/docs/selectors

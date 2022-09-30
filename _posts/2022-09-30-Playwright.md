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

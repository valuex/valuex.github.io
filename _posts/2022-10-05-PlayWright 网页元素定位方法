## 原则 Best practices
1. 尽量通过面向用户的属性 user-facing attributes进行定位
包括text, element attribute 等
``` python
# locate by text
page.locator('text="Login"').click()
# locate by attribute
page.locator('[placeholder="Search GitHub"]').fill('query') # short-form
```

2. 显式定位 explicit contracts
``` python
id
data-testid
data-test-id
data-test
```
3. 避免很长的css或xpath （跟实现相关联的定位器）



## 通过text定位  
``` python
locator = page.locator("text=Submit")
locator.click()
```
## 通过text的部分内容定位  
``` python
# Matching is case-insensitive and searches for a substring.
page.locator("button", has_text="Click me").click()
```

## 通过正则text定位
``` python
page.locator("text=/Log\s*in/i").click()
```
`/Log\s*in/i` - body can be a JavaScript-like regex wrapped in `/regex_here/i` symbols. For example, `text=/Log\s*in/i` matches `<button>Login</button>` and `<button>log IN</button>`.

## 通过元素属性定位
``` python
# Select by attribute, with css selector
page.locator("[data-test=login-button]").click()
page.locator("[aria-label='Sign in']").click()
```

``` python
#with xpath
page.locator("xpath=//button").click()
```

## 通过元素+子元素定位
Element that contains another, with css selector
```python
page.locator(".item-description:has(.item-promo-banner)").click()
# or 
page.locator("article:has(div.promo)").text_content()
# or
page.locator("article", has=page.locator("button.subscribe"))

```

## 通过元素类型+text 定位
```python
page.locator("button", has_text="Sign up").click()
# css selector
page.locator('article:has-text("All products")').click()
```
### 多层定位 `:scope`
``` python
# You can add filtering to any locator by passing :scope selector to locator.locator(selector, **kwargs) and specifying desired options. 
# For example, given the locator row that selects some rows in the table, you can filter to just those that contain text "Hello".

row = page.locator(".row")
# ... later on ...
row.locator(":scope", has_text="Hello").click()
```

``` python
css=article >> css=.bar > .baz >> css=span[attr=value]

# 或者
document
  .querySelector('article')
  .querySelector('.bar > .baz')
  .querySelector('span[attr=value]')
```

## 通过元素类型+正则text 定位
``` python
page.locator('#nav-bar :text-matches("reg?ex", "i")').click()
```


## 通过元素类型+元素属性定位
```python
page.locator('a[target="_blank"]').click()
```

## 定位表格中的第一行
``` python
# Locate elements, this locator points to a list.
rows = page.locator("table tr")
```

## 多个条件的`或`操作 
Selecting elements matching one of the conditions  
满足多个条件之一
https://playwright.dev/python/docs/selectors#selecting-elements-matching-one-of-the-conditions

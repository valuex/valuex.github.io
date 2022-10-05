## Selector 与 Locator的定义
Selector 是xpath,css path 等用于定位网页元素的路径，它是代表路径的一串文本。
Locator 是通过Selector确定的一个或一组网页元素。
Selectors are `strings` that are used to create Locators. 
Locators are used to perform actions on the elements by means of methods such as `locator.click(**kwargs)`, `locator.fill(value, **kwargs)` and alike. For debugging selectors, see here.

Locators are the central piece of Playwright's auto-waiting and retry-ability. In a nutshell, **locators represent a way to find element(s) on the page at any moment**. Locator can be created with the `page.locator(selector, **kwargs)` method.

Writing good selectors is part art, part science so be sure to checkout the Best Practices section.


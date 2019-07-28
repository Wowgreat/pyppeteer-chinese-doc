## 介绍Pyppeteer

[git](https://github.com/miyakogi/pyppeteer)

是 [puppeteer](https://github.com/GoogleChrome/puppeteer) JavaScript (headless) chrome/chromium 非官方的 Python操作库

## 安装

要求:

* python 3.6+

```shell
pip install pyppeteer
```

注意:当您第一次运行pyppeteer时，它会下载最新版本的Chromium (~100MB)。如果您不喜欢这种行为，请在运行使用pyppeteer的脚本之前运行pyppeteer-install命令。

## 使用

例如:打开网页并截屏。

```python
import asyncio
from pyppeteer import launch

async def main():
    browser = await launch()
    page = await browser.newPage()
    await page.goto('http://example.com')
    await page.screenshot({'path': 'example.png'})
    await browser.close()

asyncio.get_event_loop().run_until_complete(main())
```

例如:在页面上执行script

```python
import asyncio
from pyppeteer import launch

async def main():
    browser = await launch()
    page = await browser.newPage()
    await page.goto('http://example.com')
    await page.screenshot({'path': 'example.png'})

    dimensions = await page.evaluate('''() => {
        return {
            width: document.documentElement.clientWidth,
            height: document.documentElement.clientHeight,
            deviceScaleFactor: window.devicePixelRatio,
        }
    }''')

    print(dimensions)
    # >>> {'width': 800, 'height': 600, 'deviceScaleFactor': 1}
    await browser.close()

asyncio.get_event_loop().run_until_complete(main())
```

Pyppeteer与puppeteer具有几乎相同的API。文档中列出了更多api。

[Puppeteer’s document](https://github.com/GoogleChrome/puppeteer/blob/master/docs/api.md#) 和 [troubleshooting](https://github.com/GoogleChrome/puppeteer/blob/master/docs/troubleshooting.md) 对Pyppeteer同样有效

## puppeteer 和 pyppeteer的不同

Pyppeteer将与puppeteer类似，但是python和JavaScript之间的一些差异使其很难实现。这就是puppeteer和pyppeteer之间的区别。

*** Keyword arguments for options ***

Puppeteer使用object（python中的字典）将选项传递给函数/方法。Pyppeteer接受选项的字典和关键字参数。

字典样式选项（类似于puppeteer）：

```python
browser = await launch({'headless': True})
```

关键字参数样式选项：

```python
browser = await launch(headless=True)
```

*** 元素选择器方法名 (`$` -> `querySelector`)***

在Python中，$ 方法名称不可用。所以pyppeteer使用

```javascript
Page.querySelector()`/`Page.querySelectorAll()`/`Page.xpath()
# 而不是
Page.$()/Page.$$()/Page.$x().
```

Pyppeteer也有这些方法的缩写:

```python
Page.J(), Page.JJ(), and Page.Jx().
```

*** 参数`Page.evaluate()`和`Page.querySelectorEval()`***

Puppeteer的版本`evaluate()`采用JavaScript原始函数或JavaScript表达式字符串，但pyppeteer采用JavaScript字符串。JavaScript字符串可以是函数或表达式。Pyppeteer尝试自动检测字符串是函数还是表达式，但有时会失败。如果将表达式字符串视为函数并引发错误，则添加`force_expr=True`选项，强制pyppeteer将字符串视为表达式。

获取页面内容的示例：

```python
content = await page.evaluate('document.body.textContent', force_expr=True)
```

获取元素内部文本的示例：

```python
element = await page.querySelector('h1')
title = await page.evaluate('(element) => element.textContent', element)
```

## 未来计划

追赶Puppeteer的开发进度，不打算添加puppeteer没有的API

## 感谢

这个包是用[Cookiecutter](https://github.com/audreyr/cookiecutter)和[audreyr / cookiecutter -pypackage](https://github.com/audreyr/cookiecutter-pypackage)项目模板创建的。
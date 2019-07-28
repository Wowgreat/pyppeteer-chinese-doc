## Browser Class

Class *pyppeteer.browser.Browser* (*connection: pyppeteer.connection.Connection, contextIds: List[str], ignoreHTTPSErrors: bool, setDefaultViewport: bool, process: Optional[subprocess.Popen] = None, closeCallback: Callable[[], Awaitable[None]] = None, **kwargs*) 

Bases: `pyee.EventEmitter`

Browser class.

一个Browser被创建在pyppeteer连接chrome的时候。要么通过 `launch`,要么通过`connect`

**browserContexts**

返回一个所有打开的浏览器上下文的列表。

新近创建一个browser，会返回单个实例的列表

coroutine **close()->None** 

​	关闭连接和终止浏览器进程

croutine **createIncogniteBroserContext()->pyppeteer.browser.BrowserContext**

​	[Deprecated] Miss spelled method

​	Use [`createIncognitoBrowserContext()`](https://miyakogi.github.io/pyppeteer/reference.html#pyppeteer.browser.Browser.createIncognitoBrowserContext) method instead.

*coroutine* `createIncognitoBrowserContext`() → pyppeteer.browser.BrowserContext

​	创建一个新的隐形/匿名浏览器上下文(browser context)

​	不会和其他的浏览器上下文分享  cookies/cache

``` python
browser = await launch()
# Create a new incognito browser context.
context = await browser.createIncognitoBrowserContext()
# Create a new page in a pristine context.
page = await context.newPage()
# Do stuff
await page.goto('https://example.com')
```
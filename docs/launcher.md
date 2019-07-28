## Launcher Class

`pyppeteer.launcher.launch`(*options: dict = None*, ***kwargs*) -> 

pyppetter.browser.Browser

启动Chrome程序并返回一个Browser对象

这个function是launcher(options, **kwargs).launch()的快捷方式

可用的options有(部分，完整的请查看英文原文)：

- `ignoreHTTOSErrirs`(bool):是否忽略HTTPS的错误。默认是False。
- `headless(bool)`:
- `executablePath(str)`:
- `ignoreDefaultArgs`(bool)不使用pyppeteer的默认参数。这是个微信的操作，请小心使用。
- `handleSIGINT` (bool)：Ctrl+C关闭浏览器。默认是true
- `dumpio` (bool):是否用管道将浏览器进程的stdout和stderr导入process.stdout和process。stderr。默认值为False。

**pyppeteer.launcher.connect(options:dict = None,  \**kwargs) -> pyppeteer.browser.Browser**

连接存在的chrome

`browserWSEndpoint` 操作是必要的。格式是`ws://${host}:${port}/devtools/browser/<id>`.这个值可以通过[`wsEndpoint`](https://miyakogi.github.io/pyppeteer/reference.html#pyppeteer.browser.Browser.wsEndpoint)得到。

**可用的操作:**

- `browserWSEndpoint`(str): 要连接的浏览器websocket终端。（必要参数）
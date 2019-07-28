## Request Class

*class* `pyppeteer.network_manager.``Request`(*client: pyppeteer.connection.CDPSession, requestId: Optional[str], interceptionId: str, isNavigationRequest: bool, allowInterception: bool, url: str, resourceType: str, payload: dict, frame: Optional[pyppeteer.frame_manager.Frame], redirectChain: List[Request]*)

> 任何时候页面发送一个请求，例如请求网络资源，下面的事件会被pyppeteer的page执行：

- `request`:当一个请求被页面发出时触发
- `response`: 当收到请求的响应时触发
- `requestfinished`: 当响应体下载完成并且请求完成时触发

如果请求失败在某一点，`requestfinished`事件（也有可能是`response`事件）会被替代为`requestfailed`事件。

如果请求得到的是`redrect`响应，这个请求被成功完成。然后新的请求（redirect url）被发送。

coroutine **abort**(errorCode: str = 'failed') -> None

​	Abort request

​	






























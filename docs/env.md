## 环境变量

- `$PYPPETEER_HOME`：指定pyppeteer使用的目录。Pyppeteer使用此目录存放下载的Chromium，并用于创建临时用户数据目录。默认位置取决于平台：

  - Windows： `C:\Users\<username>\AppData\Local\pyppeteer`
  - OS X： `/Users/<username>/Library/Application Support/pyppeteer`
  - Linux： `/home/<username>/.local/share/pyppeteer` 

  细节见[appdirs](https://pypi.org/project/appdirs/)的`user_data_dir`。

- `$PYPPETEER_DOWNLOAD_HOST`：覆盖用于下载Chromium的URL的主机部分。默认为`https://storage.googleapis.com`。

- `$PYPPETEER_CHROMIUM_REVISION`：指定您想要使用pyppeteer的特定版本的铬。可以通过`pyppeteer.__chromium_revision__`检查默认值 。

# chromium-web-store
这个扩展为 ungoogled-chromium (以及缺少 Web 商店支持的其它分支)带来了下列功能:
- 允许直接从 chrome web 商店安装扩展。
- 自动检查你已安装的扩展的更新并在标记上显示。
![示例图像](https://raw.githubusercontent.com/NeverDecaf/chromium-web-store/master/sample2.PNG)

## 首先阅读这里
- 若你正在使用 `ungoogled-chromium` 的话则**必须**更改 flag `chrome://flags/#extension-mime-request-handling` 为 `Always prompt for install`(始终提示安装)。用户报告的大多数问题都是跳过设置这个标志来解决的。
- 某些扩展可能直至你重启浏览器才会更新，参阅 [#4](https://github.com/NeverDecaf/chromium-web-store/issues/4)。

### 用法
- 如果你希望直接安装扩展而不是下载 crx 文件的话，你必须更改 flag `chrome://flags/#extension-mime-request-handling` 为 `Always prompt for install`。
- 可用的扩展更新将会显示在标记上，点击安装它们(注意，即使你已经设定了 flag，非 webstore 的扩展仍可能需要手动安装。)
### 安装
1. 转到 `chrome://extensions` 并启用开发者模式(在右上角切换)。
2. 下载 .crx 自 [Releases](https://github.com/NeverDecaf/chromium-web-store/releases/latest) 并拖放它到 `chrome://extensions` 页面上。

### 如果拖放无效，尝试这个变通方案:
1. 下载 .crx 自 releases 并提取内容到一个文件夹。
2. 访问 `chrome://extensions/` 并开启开发者模式(右上角切换)。
3. 点击 `Load unpacked` (加载已解压的扩展程序)并选择你提取 crx 到的目录。

### 安装视频
[![这里](https://raw.githubusercontent.com/NeverDecaf/chromium-web-store/master/video_thumbnail.png)](https://chromium.woolyss.com/f/video-extension-chromium-web-store.mp4)
[[Streamable Mirror](https://streamable.com/655nn)] (谢谢 [@woolyss](https://github.com/woolyss) 创建并托管了这个视频。)

### 选项说明
- 右击标志并从上下文菜单中选择 `Options` (选项)，或者经 `chrome://extensions` 访问它们。
- "Web Store" 扩展指的是从 [Chrome Web Store](https://chrome.google.com/webstore/category/extensions) 获取的任何内容，, despite displaying `Source: Not from Chrome Web Store` when checking extension details.
- 若你希望使用导入/导出功能，请阅读 [Release 1.4](https://github.com/NeverDecaf/chromium-web-store/releases/tag/v1.4.0)。

#### 如果你希望本地化，请按照下列步骤进行:
1. 在 `_locales` 中创建一个目录，名为任何支持的[地区代码(locale code)](https://developer.chrome.com/webstore/i18n?csw=1#localeTable).
2. 复制 `_locales/en/messages.json` 到你新创建的目录并按需编辑 "message" 字段，你不需要更改任何其它内容。
3. 提交一个 PR (合并请求)或使用你的翻译开启一个 issue (议题)，而我将会合并它。

#### 如果你是一个 chrome 扩展开发者...
并且在 Chrome 网络商店中没有列出你的扩展的话，你仍可以通过托管一个[更新 manifest 文件](https://developer.chrome.com/apps/autoupdate#update_manifest) 经 chromium-web-store 来启用更新; 有关示例，请参照本库中的 [updates.xml](https://github.com/NeverDecaf/chromium-web-store/blob/master/updates.xml)。你还必须在你的扩展的 `manifest.json` 中的 [`update_url`](https://developer.chrome.com/apps/autoupdate#update_url) 字段下指定访问这个文件的 URL; 再说一次，请参照本库中的 [manifest.json](https://github.com/NeverDecaf/chromium-web-store/blob/master/src/manifest.json) 为例。

#### 关于开发
请参看 [#28](https://github.com/NeverDecaf/chromium-web-store/issues/28) 和 [`managed_storage.json`](https://github.com/NeverDecaf/chromium-web-store/blob/master/src/managed_storage.json)

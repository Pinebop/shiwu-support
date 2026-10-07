# shiwu-support

拾物（things for iPhone）的静态技术支持站，用 GitHub Pages 托管。
无构建步骤、无 JavaScript。源文件维护在拾物仓库
[Pinebop/things](https://github.com/Pinebop/things) 的 `docs/support-site/`，
改完复制推送本仓库即可（推送到 `main` 后自动重新部署，通常一分钟内生效）。

- **技术支持页：** https://pinebop.github.io/shiwu-support/ ——填入 App Store
  Connect 的「技术支持网址」
- **隐私政策：** https://pinebop.github.io/shiwu-support/privacy.html ——填入
  App Store Connect 的「隐私政策网址」（App 信息页的独立字段）

## 文件

纯 HTML/CSS，直接改：

- `index.html` ——技术支持页（功能说明、常见问题、联系方式）。**发版前把
  版本号 chip 更新为当期版本**（来源拾物仓库 `app/ios/App/Info.plist`，
  HTML 里有注释标记）。
- `privacy.html` ——隐私政策，11 节。
- `styles.css` ——共用样式（`prefers-color-scheme` 自适应浅色/深色，配色取自
  拾物仓库 `app/ios/App/AppTheme.swift`，改主题时两边同步）。
- `assets/icon.png` ——App 图标（取拾物仓库 AppIcon.appiconset 1024 图缩 256；
  图标定稿后重新生成：`sips -Z 256 …/AppIcon.png --out assets/icon.png`）。

## 口径必须与代码一致

隐私政策是合规文本，审核会拿它跟 App 的实际行为对照，改动前先回拾物仓库核实。
当前口径「不发起任何网络请求、数据只在本机 `Application Support/things`、
仅相机权限（相册走 PHPicker 最小授权）、无第三方 SDK、无设备标识」是
2026-10-04 按代码核实的（全仓无 URLSession / Network / WKWebView 调用；
隐私清单 `PrivacyInfo.xcprivacy`：不追踪、采集数据类型为空）。

- 改联网 / 存储 / 权限行为时，**同一个提交**回拾物仓库改本页，并同步
  `docs/appstore-metadata.md` 的口径；
- 提审前逐条核对：公开政策 ↔ App 实际行为 ↔ App Store「App 隐私」标签
  三者一致；公开仓库为 public；两个 URL 匿名可打开；版本号 chip 与当期一致。

## 支持渠道

本仓库的 Issues 是公开支持渠道；为保持 App Store 链接有效，
**本仓库必须保持公开**。隐私相关的问题也可发邮件到
`kenshinlzh@163.com`（拾物是纯本机 App，删除数据即删除 App，没有服务端留存）。

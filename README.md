# Focus 跨平台移植预览

状态：0.48.0 Windows x64 测试版已在私有 GitHub Actions 成功生成 NSIS 与便携 EXE，五项计时/归档测试通过。尚未在实际 Windows 桌面验证，不等同于已实测的正式版。现有原生 Mac 版请使用单独的 Mac 分享包。

## 包含
本地任务输入、小时/分钟、开始暂停继续重置、加时、默认白版与黑版切换、水量/气球表达时间、三态位置、桌面置顶、完成通知、本地收获记录、按日期查看手帐。关闭后不恢复计时。

## 与当前原生 Mac 版的差异
角色与植物插画暂用简化 SVG/符号，未完成视觉对齐；已加入手动完成率和历史日归档快照；不读取原生 Mac UserDefaults 数据。尚未实现自动更新、云同步和登录。当前不能作为同等功能的正式替代。

## 本地运行
安装 Node.js 22 LTS，在本目录执行：

    npm install
    npm start

## 构建安装包
在 Windows 机器上执行：

    npm run dist -- --win --x64

生成 dist/ 下的 NSIS 安装 EXE 和便携 EXE。在 Mac 执行：

    npm run dist -- --mac --arm64 --x64

生成各架构 DMG 和 ZIP。正式对外分发前需分别实测，配置签名/公证；当前默认未配置证书。

## 自动构建
将本文件夹内容作为 GitHub 仓库根目录上传（包括隐藏的 .github 文件夹）。Actions → Build installers → Run workflow。Windows 与 Mac 两种运行环境分别打包，安装包在各任务的 Artifacts 下载。当前仅产出构建附件，不自动公开发布。

上传源码本身不会自动产生安装包，必须运行构建且成功结束。本机缺少 Node.js；已改用 GitHub Windows 构建环境，依赖安装、测试、EXE打包均成功。已用独立 JavaScript 环境验证语法、1分钟输入、加时、模式记录和防重复完成；打包已通过；尚未测试实际 Windows UI 与系统通知。

## 浏览器预览
双击 index.html 可离线预览，但它不是桌面安装版，浏览器无法提供本应用的置顶、窗口位置和系统通知；不要把 HTML 称为 Windows EXE。浏览器中的本地存储取决于浏览器配置。

私有仓库：https://github.com/2082729953-spec/focus-companion
构建记录：https://github.com/2082729953-spec/focus-companion/actions/runs/41702933269

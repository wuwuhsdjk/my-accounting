我的记账 — iPhone 私人记账 PWA（第一版）
====================================
功能：人民币记账；收入/支出；分类；日期与备注；月度结余、统计环形图；历史账单编辑和删除；本地保存；JSON 完整备份与恢复；CSV 导出；离线使用（首次联网打开成功后）。

一、在 Windows 电脑上预览
双击 index.html，可预览大部分功能；注意：通过 file:// 打开无法验证 Service Worker 离线缓存及真正 PWA 安装。测试安装请先部署到 HTTPS 网站。

二、免费部署（推荐 GitHub Pages）
1. 注册/登录 GitHub (https://github.com)。
2. 新建一个 Public repository，例如 my-ledger（免费 GitHub Pages 通常用于公开仓库；源代码可被其他人看到，但你的记账数据不会包含在上传的代码里）。
3. 将本压缩包解压后的 index.html、styles.css、app.js、sw.js、manifest.webmanifest 和 icons 文件夹上传到仓库根目录（不要上传 zip 文件本身）。
4. 进入仓库 Settings → Pages → Build and deployment；Source 选 Deploy from a branch；Branch 选 main 和 /(root)；保存。
5. 等待 GitHub Pages 页面显示站点地址，格式一般为 https://用户名.github.io/my-ledger/ （请以 GitHub 显示的实际地址为准）。
6. 用 iPhone Safari 访问上述地址，点分享 → 添加到主屏幕 → 添加。以后直接点桌面“我的记账”图标。

重要：仅需上传程序文件，绝不要把 JSON 备份上传到公开仓库！
公开网站并不是访问控制：别人知道网址也能打开这套空白程序，但无法直接看到你手机上保存的账单（账单不在服务器）。如果需要限制网站访问，需要另外配置私有托管/登录机制。

三、数据安全
- 数据只保存在当前浏览器/Web App 的本地存储，不会自动同步或上传。
- 同一网址在 Safari 页面和桌面 Web App 中的本地存储可能互不共享；记账请固定从桌面图标打开。
- 卸载应用、清理网站数据、设备损坏、Safari 存储回收等均可能造成数据丢失。请在“备份与设置”定期导出 JSON 并保存到 iCloud Drive 或其它安全位置。CSV 适合用 Excel 看账，不适合做完整恢复。
- 数据没有密码加密；使用有屏幕锁的私人 iPhone，并妥善保管备份。
- 恢复备份会覆盖现有账单，恢复前先导出当前备份。
- PWA 并非 App Store 原生 App，无需 Apple Developer 账号；某些系统行为可能与原生 App 不同。

四、更新版本
替换部署仓库中的代码文件。更新 sw.js 中的 CACHE 常量（如 personal-ledger-v2）可让离线缓存切换为新版本。请先备份账单。


【1.1 版本更新：2026-11-05】
首页新增“今日收支”，展示当天收入、支出与结余；原有本月统计保留。

【升级已有 GitHub Pages 的方法】
1. 先在旧版 App 的“备份与设置”里导出 JSON 备份并妥善保存。
2. 打开 GitHub 仓库 my-accounting，上传此压缩包解压后最外层的全部文件。
3. GitHub 如提示同名文件被更新，请确认提交覆盖程序文件（不要删除其他文件）。
4. 提交更改后检查 Settings → Pages 部署状态，手机联网后重新打开 App。
5. 如果仍是旧界面，请完全关闭 App 再打开，或稍后用 Safari 打开同一网址。
注意：软件版本升级沿用 localStorage 的 my-ledger-records-v1 键，不会主动清空账本；但依然建议先备份。

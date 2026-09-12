# 云端数字人 · 分享版

> 一个 Windows 悬浮窗数字人客户端：**云端包办语音识别 / 大模型 / 语音合成 / 数字人渲染**，本地只负责窗口、麦克风与信令。
> 底层用 [Vidu](https://platform.vidu.cn) 的实时数字人（S1 Live）能力——**你需要自备 Vidu 账号与 API Key**。

![平台](https://img.shields.io/badge/platform-Windows%2010%2F11-blue) ![许可证](https://img.shields.io/badge/license-个人使用免费%20·%20禁止转售-red) [![视频教程](https://img.shields.io/badge/Bilibili-视频教程-00A1D6?logo=bilibili&logoColor=white)](https://www.bilibili.com/video/BV1xiYm6fEuN/)

## 📺 视频教程

不想看文字？先看这个（从解压 → 填 Key → 和数字人聊起来）：

**▶ [B 站视频教程：https://www.bilibili.com/video/BV1xiYm6fEuN/](https://www.bilibili.com/video/BV1xiYm6fEuN/)**

## 它是什么

一个点开就能和数字人实时语音对话的悬浮窗：

- **悬浮窗**：无边框、可拖动、可缩放，窗口比例自动跟随视频流；点最小化进托盘，再双击程序会把窗口拉回前台
- **手动连线**：绝不自动连——点「▶ 连线」才创建会话，避免偷偷计费
- **实时对话**：直接对着麦克风说话即可，云端 ASR→LLM→TTS→口型驱动一条龙；可选开摄像头让对方「看见」你
- **形象 / 音色 / 人设**：用你自己 Vidu 账号里的资产，面板里直接切换；也能**上传图片注册形象**、**上传音频克隆音色**
- **安全护栏**：静默自动挂断 + 单场时长上限（都可在面板调整，带花费估算），防止忘挂断烧钱
- **断线自愈**：信令掉线自动重连（同一场会话内恢复，不重新计费）；断开原因会写在落地页

## 下载

- 直接下载：[`release/云端数字人-分享版-v1.0.6.zip`](https://github.com/beiyege-01/clouddh-share/raw/main/release/%E4%BA%91%E7%AB%AF%E6%95%B0%E5%AD%97%E4%BA%BA-%E5%88%86%E4%BA%AB%E7%89%88-v1.0.6.zip)（约 20 MB）
- 或到 [Releases 页面](https://github.com/beiyege-01/clouddh-share/releases) 下载同一份（`CloudDH-Share-v1.0.6.zip`）

解压后目录：

```
云端数字人-分享版.exe                          主程序（单文件，不需要装 Python）
启动-云端数字人独立版.cmd                     一键启动
停止-云端数字人独立版.cmd                     一键挂断并关闭
WebView2Setup\MicrosoftEdgeWebView2Setup.exe  网页内核在线安装器（目标机缺内核时用）
```

## 快速开始

> 视频版：[B 站视频教程](https://www.bilibili.com/video/BV1xiYm6fEuN/)　·　文字版见下 ↓

1. 解压到一个目录（**exe 和两个 cmd 要放在一起**），双击 `云端数字人-分享版.exe`；
2. 悬浮窗弹出后，点面板里的 **Vidu API Key** 输入框，粘进你自己的 Key（`vda_` 开头）→ **保存 Key** → 会自动测试连接并告诉你账号里有几个形象/音色；
3. 选一个形象和音色 → **保存，下次连线生效**；
4. 点 **▶ 连线**，开始聊天。

> ⚠️ **计费提示**：会话费用由你自己的 Vidu 账号承担（官方实时数字人约 **3 积分 / 2 秒**）。程序默认「静默 5 分钟挂断、单场 10 分钟上限」，可在面板里调长，面板会实时显示"满打满算要花多少积分"。

## 系统要求

- Windows 10 / 11（64 位）
- **Microsoft Edge WebView2 Runtime**：普通电脑随 Edge 一起装好了；精简系统 / Windows 沙盒里可能没有——这时程序会弹窗问你，点「是」即可用随包安装器静默安装
- 首次运行会自解压到 `%TEMP%\onefile_*`，启动约 1~3 秒
- exe 未做代码签名，Windows SmartScreen 可能提示"更多信息 → 仍要运行"

## 常见问题

| 现象 | 原因 / 处理 |
|---|---|
| 双击后**窗口一闪而过 / 什么都没出现** | 悬浮窗（一个隐藏的 PowerShell 进程）没能起来。v1.0.6 起程序会自己检测并弹窗说明，同时把 PowerShell 的原始报错写进 `%LOCALAPPDATA%\CloudDH-Full\shell-stderr.log`。最常见原因是**安全软件拦截**（360 / 火绒 / 腾讯管家 / Defender 对"隐藏窗口的 PowerShell"很敏感）——把解压目录和 `powershell.exe` 加入白名单后重试 |
| 窗口出来了，但里面是**纯黑一块** | 目标机没有 WebView2 运行时。重新运行 exe，弹窗问"要不要现在装"点「是」；或手动装 `WebView2Setup\` 里的安装器 |
| 点连线后提示「还没有填 Vidu API Key」 | 先在 ⚙ 面板里填 Key 并保存 |
| 提示「你的 Vidu 账号里还没有可用形象 / 音色」 | 该账号还没有资产：在面板底部上传一张图片注册形象、上传一段音频克隆音色 |
| 点连线报「Vidu 创建会话失败: …」 | 报错原文就是原因，常见是余额不足、或该账号未开通实时数字人（Live）能力 |
| 聊着聊着**自己断了** | 落地页会写明原因（静默超时 / 到达单场上限 / 服务端挂断 / 网络断开）。前两种是护栏，可在面板调长 |
| 要反馈问题 | 把 `%LOCALAPPDATA%\CloudDH-Full\` 下的 `launcher.log`、`bridge.log`、`shell-stderr.log`、`shell-stdout.log` 和 `runtime\wallpaper-vidu-full.log` 发给作者即可定位 |

运行时落盘位置：`%LOCALAPPDATA%\CloudDH-Full\`（删掉它就等于恢复出厂：Key、人设、窗口位置全清）。

## 技术栈

Python（FastAPI + uvicorn 本地桥，Vidu Live HTTP/WS 信令）+ PowerShell / WPF / WebView2（悬浮窗壳）+ Nuitka（单文件打包，关键常量与前端字符串以 ChaCha20 加密载荷形式内置、运行时还原）。

## 许可与版权

- 本项目**仅供个人学习与自用**，**禁止转售、禁止商业分发**；二次分发请保留本说明与出处。详见 [LICENSE](LICENSE)。
- 数字人能力、形象/音色资产与计费均归属 **Vidu 平台**；本项目为第三方客户端，与 Vidu 官方无隶属关系。
- Python / FastAPI / uvicorn / WebView2 等第三方组件与微软 WebView2 安装器归各自权利人所有。

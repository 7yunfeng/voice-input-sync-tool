# 语音输入法同步工具

手机语音输入同步到电脑光标位置的轻量工具。

本项目基于 [chxcodepro/VoiceSync](https://github.com/chxcodepro/VoiceSync) 二次开发，
遵循原项目 MIT License，并保留原始版权与许可信息。当前版本重点优化手机语音输入法在识别过程中反复修正文字时，
电脑端重复上屏的问题。

## 主要变化

- 使用 IME 组合态监听：输入法仍在识别或修正时不会立即发送到电脑。
- 在 `compositionend` 后进行短暂稳定性确认，再提交最终文本。
- 若手机浏览器不可靠暴露 IME 状态，则回退到文本稳定检查。
- 手机端保留已发送历史，并用灰色区域显示。
- 源码运行时不再弹出上游版本自动更新提示。

## 使用方式

1. 安装 Python 3.11 或更高版本。
2. 安装依赖：

```powershell
pip install -r requirements.txt
```

3. 启动：

```powershell
python server.py
```

4. 手机和电脑连接同一个局域网，扫描程序窗口中的二维码。
5. 在手机网页输入框里使用语音输入，识别完成后会同步到电脑当前光标位置。

## 构建

```powershell
pip install pyinstaller
pyinstaller --onefile --windowed --name "VoiceInputSyncTool" server.py
```

构建产物会生成到 `dist` 目录。

## 说明

本项目会通过剪贴板和模拟快捷键把文本粘贴到当前电脑焦点窗口。使用时请确认光标位于目标输入框。

## License

MIT License. 原项目作者为 chx，本仓库基于 VoiceSync 二次开发并保留原 MIT 许可。

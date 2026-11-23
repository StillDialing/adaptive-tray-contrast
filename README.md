# 任务栏自适应变色 · Adaptive Tray Contrast

把 Windows 11 的任务栏设成透明之后，底下有时是亮色窗口，有时是深色壁纸，原本固定的白字或黑图标经常会糊在背景里看不清。这个 Windhawk 模组就是为了解决这个日常小问题做的。

它**不是**让整条任务栏跟着系统浅色或深色主题一起切换，而是**根据每个受支持元素所在位置的实际背景画面，各自单独判色**。因此同一条任务栏可以一边显示黑色、一边显示白色。最直观的例子是，把一个亮色窗口慢慢拖过右下角的日期，当深浅分界线划过时，同一行日期里的数字会按各自背后的明暗分别变黑或变白。

除了系统托盘里受支持的单色图标和文字外，模组也会识别部分自带深、浅两套图标的 MSIX 应用，按各自按钮背后画面的明暗自动切换对应版本的图标。

- 适用环境：Windows 11 x64（需配合 Windhawk 使用）
- 当前投稿版：`0.3.15`（下方安装步骤使用此版）。已通过 x64 编译和独立窗口的启停测试，仍待在 Explorer 中复测。
- [原实测版 0.3.13](https://github.com/StillDialing/adaptive-tray-contrast/blob/b84ae461bdae1dd66f2228db9b6355a888a64471/adaptive-tray-contrast.wh.cpp)：下方两段演示展示的是原有变色功能。
- 投稿版默认每 80 毫秒采样，可在设置中调整为 40–2000 毫秒。画面和布局相同时会复用已计算的对比度，但仍需采样以检测变化。

On a transparent Windows 11 taskbar, a dark icon can disappear against a dark wallpaper, and white text can blend into a light window. Adaptive Tray Contrast samples the background behind each supported item and selects black or white independently. The clock and date adapt character by character. For MSIX apps that ship both light and dark icons, the mod selects the matching icon for each taskbar button.

- Requirements: Windows 11 x64 and Windhawk.
- Current submission: `0.3.15`. The installation steps below use this version. It passed an x64 build and an isolated window lifecycle test. Testing inside Explorer is still pending for this revision.
- [Original tested build (0.3.13)](https://github.com/StillDialing/adaptive-tray-contrast/blob/b84ae461bdae1dd66f2228db9b6355a888a64471/adaptive-tray-contrast.wh.cpp). The two demos show the existing contrast behavior.
- The submission samples every 80 ms by default, adjustable from 40 to 2000 ms. It reuses contrast calculations on an unchanged frame and layout, while continuing to sample for changes.

## 实机演示 · Demos

**应用图标** · 拖动窗口，观察 ChatGPT 和 Microsoft Store 图标随各自按钮背后的明暗切换。

**App icons.** As the window moves behind the taskbar, ChatGPT and Microsoft Store switch to the icon variant suited to the background behind each button.

![应用图标随窗口背景切换 · App icons switching as a window moves](images/app-icons.gif)

**右侧托盘、时间和日期** · 当窗口边缘扫过日期，同一行的数字会分别显示为黑色或白色。

**System tray, clock and date.** Watch the edge of the window cross the date. Digits on the dark side turn white while digits on the light side turn black, even within the same line.

![托盘和日期逐字符变色 · Tray and per-character date contrast](images/tray-clock-date.gif)

## 安装与更新 · Installation and updates

**首次安装**

1. 打开[模组源码](adaptive-tray-contrast.wh.cpp)，复制完整内容。
2. 在 Windhawk 里新建本地模组，全选默认代码，粘贴刚复制的源码。
3. 点击 **编译 Mod**。

**First installation**

1. Open the [mod source file](adaptive-tray-contrast.wh.cpp) and copy its entire contents.
2. In Windhawk, create a local mod. Select all the default code and paste the source you copied.
3. Click **Compile Mod**.

**更新已有版本**：在 Windhawk 里打开已有的 `adaptive-tray-contrast`，编辑它的源码，全选替换后重新编译。

**Updating an existing installation.** In Windhawk, edit your existing `adaptive-tray-contrast` mod. Replace its source with the updated file and click **Compile Mod** again.

## 已知问题与反馈 · Known issue and bug reports

图标或文字刚好落在深浅背景交界处时，可能短暂闪烁。遇到显示异常时，请在 [Issues](../../issues) 中写明复现步骤，并附上 Windows 版本号。按 `Win + R`，输入 `winver` 即可查看。

Icons or text may flicker briefly at the boundary between a light and a dark background. If you see a display or icon-switching problem, please [open an issue](../../issues) with the steps to reproduce it and your Windows build number. Press `Win + R`, type `winver`, and press Enter to find it.

## 署名与许可证 · Credits and license

本项目由 **StillDialing** 提出需求、实机测试并挑选首发版本，模组代码在 AI 协助下完成。源码采用 **GPL-3.0-only** 许可证发布，并保留第三方参考实现的署名与来源说明。

**StillDialing** proposed the mod, tested it on Windows, and selected the initial release. The code was developed with AI assistance and is distributed under **GPL-3.0-only**. Credits and source references for third-party implementations are included in the source file.

# 深海女仆工坊 · 立华奏

> Abyssal Maid Atelier · Tachibana Kanade

一套用于 **DeepSeek Harness Web GUI** 的动漫角色皮肤。它是 [maid-atelier（深海女仆工坊）](https://github.com/Small-tailqwq/dsh-deep-whale/tree/main/maid-atelier) 的改版：**在原作基础上，仅将对话区背景替换为立华奏（《Angel Beats!》）图片**。

## 与原作的关系

| 项 | 说明 |
| --- | --- |
| 原作 | [maid-atelier / 深海女仆工坊](https://github.com/Small-tailqwq/dsh-deep-whale/tree/main/maid-atelier) v0.3.2 |
| 原作者 | Small-tailqwq（署名链：上善 → zipzip → Small-tailqwq） |
| 本次改动 | **只替换对话区背景**，其余界面覆盖层、侧栏装饰、蕾丝边框、动效脚本全部保留原作 |
| 改动者 | XuHe896 |

原作的界面设计、样式与美术资源版权归原作者所有，本仓库依 **CC BY-NC-SA 4.0** 以相同方式共享。

## 改了什么（精确说明）

`skin.json` 的 `contributes.backgroundMedia`——也就是**对话区背景**——所指向的资产被替换：

| 主题 | 原作资产 | 本版资产 |
| --- | --- | --- |
| light | `assets/maid-atelier-palace-day-v4.webp` | `assets/custom-chat-bg-v1.png` |
| dark | `assets/maid-atelier-palace-night-v4.webp` | `assets/custom-chat-bg-v1.png` |

原作的两张宫殿背景 `.webp` 已从本仓库移除。以下内容**一字未改**：

- `skin.css`、`patches.css`（界面配色与样式覆盖层）
- `hooks.mjs`（动效与交互脚本）
- 侧边栏、顶部/底部蕾丝装饰、蝴蝶结、输入框边框、Q 版吉祥物等全部 `assets/*.webp`

也就是说：**整个界面框架保持原作，只有对话框背后的那张图换了。**

## 安装

把本目录整个放进 DSH 主目录的皮肤目录下：

```
~/.dsh/skins/maid-atelier-kanade/
```

然后在 Web GUI 的皮肤面板里选择「深海女仆工坊 · 立华奏」，或者重启 `dsh web` 使其生效。

> 提示：`preview/` 中的预览图仍是原作截图（背景为原作的宫殿场景），尚未更新为本版实际效果。

## 素材与版权声明

- **界面与美术资源**：来自原作 maid-atelier，作者 Small-tailqwq，依 CC BY-NC-SA 4.0 发布。
- **对话区背景图**：角色为立华奏（立華かなで / Tachibana Kanade），出自《Angel Beats!》。角色形象相关权利归其版权方所有（Key / Aniplex 等）。此处仅用于**非商业的个人定制**，并随本仓库的 CC BY-NC-SA 4.0 非商业条款一同分发。
- 若你是相关权利方并希望移除该素材，请提交 issue，我会立即处理。

## 许可

[CC BY-NC-SA 4.0](LICENSE) — 署名 · 非商业性使用 · 相同方式共享

完整署名链见 [NOTICE](NOTICE)。

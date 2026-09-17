# 深海女仆工坊 · 立华奏

> Abyssal Maid Atelier · Tachibana Kanade

一套用于 **DeepSeek Harness Web GUI** 的动漫角色皮肤。它是 [maid-atelier（深海女仆工坊）](https://github.com/Small-tailqwq/dsh-deep-whale/tree/main/maid-atelier) 的改版：**在原作基础上，替换对话区背景为立华奏（《Angel Beats!》）图片，并移除原作左右两个女仆立绘**。

## 与原作的关系

| 项 | 说明 |
| --- | --- |
| 原作 | [maid-atelier / 深海女仆工坊](https://github.com/Small-tailqwq/dsh-deep-whale/tree/main/maid-atelier) v0.3.2 |
| 原作者 | Small-tailqwq（署名链：上善 → zipzip → Small-tailqwq） |
| 本次改动 | 替换对话区背景 + 移除左右两个女仆立绘 |
| 改动者 | XuHe896 |

原作的界面设计、样式与美术资源版权归原作者所有，本仓库依 **CC BY-NC-SA 4.0** 以相同方式共享。

## 改了什么（精确说明）

### 1. 对话区背景

`skin.json` 的 `contributes.backgroundMedia`——也就是**对话区背景**——所指向的资产被替换：

| 主题 | 原作资产 | 本版资产 |
| --- | --- | --- |
| light | `assets/maid-atelier-palace-day-v4.webp` | `assets/custom-chat-bg-v1.png` |
| dark | `assets/maid-atelier-palace-night-v4.webp` | `assets/custom-chat-bg-v1.png` |

原作的两张宫殿背景 `.webp` 已从本仓库移除。

### 2. 移除两个女仆立绘

原作的左右两个女仆角色由两层渲染：`patches.css` 里的 `body:before` / `body:after` 伪元素，以及 `hooks.mjs` 动态创建的 `character-stage` 容器（内含两个 `<img>`）。

本版**没有删除或改写原作任何既有规则**，而是在 `patches.css` 文件末尾追加了一段覆盖块：

```css
body:before,
body:after,
[data-skin-chrome="character-stage"],
[data-maid-character] {
  display: none !important;
}
```

两层渲染因此同时被隐藏。追加块带有注释说明用途，便于日后回溯。

### 3. 保持不变的部分

- `skin.css`（配色 token 重映射）
- `hooks.mjs`（动效与交互脚本逻辑本身未改动）
- 侧边栏、顶部/底部蕾丝装饰、蝴蝶结、输入框边框、Q 版吉祥物等全部 `assets/*.webp`

也就是说：**界面框架完整保留原作风格，只有对话区背景换了、两个女仆立绘被隐藏。**

## 安装

把本目录整个放进 DSH 主目录的皮肤目录下：

```
~/.dsh/skins/maid-atelier-kanade/
```

然后在 Web GUI 的皮肤面板里选择「深海女仆工坊 · 立华奏」，或者重启 `dsh web` 使其生效。

> 提示：`preview/` 中的预览图仍是原作截图（背景为原作宫殿场景、且仍含两个女仆），尚未更新为本版实际效果。

## 素材与版权声明

- **界面与美术资源**：来自原作 maid-atelier，作者 Small-tailqwq，依 CC BY-NC-SA 4.0 发布。
- **对话区背景图**：角色为立华奏（立華かなで / Tachibana Kanade），出自《Angel Beats!》。角色形象相关权利归其版权方所有（Key / Aniplex 等）。此处仅用于**非商业的个人定制**，并随本仓库的 CC BY-NC-SA 4.0 非商业条款一同分发。
- 若你是相关权利方并希望移除该素材，请提交 issue，我会立即处理。

## 许可

[CC BY-NC-SA 4.0](LICENSE) — 署名 · 非商业性使用 · 相同方式共享

完整署名链见 [NOTICE](NOTICE)。

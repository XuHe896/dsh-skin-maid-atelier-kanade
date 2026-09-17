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

原作的左右两个女仆角色由**两层**渲染，本版把两层连同资源文件一并移除：

| 层 | 原作实现 | 本版处理 |
| --- | --- | --- |
| CSS 伪元素层 | `patches.css` 的 `body:before` / `body:after` 加载两张立绘 | 两条 `background` 引用已注释；另在文件末尾追加 `display: none !important` 覆盖块 |
| 动态挂载层 | `hooks.mjs` 的 `createCharacterStage()` 创建 `character-stage` 容器并插入两个 `<img>` | 该函数及其挂载调用**整体移除**，图片因此不会被浏览器请求 |
| 资源文件 | `assets/maid-atelier-maid-left-v5.webp`、`assets/maid-atelier-maid-right-v6.webp` | **已删除**（合计 806 KB） |

被删除的资产：

| 文件 | 原作大小 |
| --- | --- |
| `assets/maid-atelier-maid-left-v5.webp` | 286,224 B |
| `assets/maid-atelier-maid-right-v6.webp` | 520,206 B |

这样处理之后，皮肤目录里不再有任何指向这两个文件的**活引用**（仅保留说明性注释），既不显示、也不加载、也不占体积。如果你希望恢复女仆，从上游 `maid-atelier` 取回这两个 `.webp` 与 `hooks.mjs` 即可。

### 3. 界面配色：深海蓝 → 银紫调

原作主调是深海蓝配柔金。本版把蓝色系整体转到紫色系，以贴合立华奏（《Angel Beats!》）的银紫意象。

做法是**按色相映射**：对所有 hex 颜色计算 HSL，仅当色相落在 `195°–265°`（蓝系）且饱和度大于 6% 时旋转 `+35°`，**明度、饱和度、透明度全部保持不变**，因此原有的层级与对比关系不被破坏；落在此范围外的颜色（金色、白色、灰色）**原样保留**。

| 关键色 | 原作 | 本版 |
| --- | --- | --- |
| 主品牌色 | `#526aa8` 靛蓝 | `#6c52a8` 紫罗兰 |
| 深色底 | `#091333` 深海蓝 | `#170933` 深紫 |
| 深色文字 | `#172347` | `#271747` |
| 淡色强调 | `#8ea5da` 淡蓝 | `#a38eda` 淡紫 |
| 点缀金 | `#c5a468` | `#c5a468` **保持不变**（天使光环意象） |

覆盖范围：`skin.css` 中 68 个唯一色映射 55 个，`patches.css` 中 463 个唯一色映射 299 个。金色系整体不在映射区间内，被完整保留。

### 4. 保持不变的部分

- `hooks.mjs` 的动效与交互动画逻辑（仅移除了女仆挂载那一处）
- 侧边栏、顶部/底部蕾丝装饰、蝴蝶结、输入框边框、Q 版吉祥物等全部 `assets/*.webp`

也就是说：**界面结构与装饰完整保留原作，改动集中在对话区背景、两个女仆立绘、以及整体色调。**

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

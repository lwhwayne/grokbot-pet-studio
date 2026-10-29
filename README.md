# GrokBot Pet Studio v0.9.4

[在线定制桌宠](https://lwhwayne.github.io/grokbot-pet-studio/)

本版本从 `grokbot-pet` v0.9.2 / Studio v0.9.3 增量升级，保留实时 SVG、14 种轮廓、12 款颜色、刚性胶囊双眼、眼睛与身体同步转向、眨眼和交互；只把原本的「配置素材包 ZIP」下载换成「ChatGPT 原生 Pet ZIP」下载。无服务端、无 AI API、无需安装依赖或账号，浏览器本地完成导出。

## 怎么使用

1. 用 Chrome / Edge 等支持 Canvas WebP 导出的浏览器打开 `index.html`（也可将这个 HTML 直接放在 GitHub Pages 网站根目录）。
2. 选择喜欢的形状和颜色，点击「下载 ChatGPT Pet 安装包」。
3. 下载的 ZIP 内有 `<pet-id>/pet.json` 和 `<pet-id>/spritesheet.webp`，以及 `preview.png`、`pet-config.json`、`给GPT的安装指令.txt` 和 README。
4. 可以把 ZIP 交给有本机文件访问权限的 GPT 安装；或解压后手动把 `<pet-id>` 整个文件夹复制到 `~/.codex/pets/`（自定义 `CODEX_HOME` 时以其 pets/ 为准）。然后在 ChatGPT 桌面版 Settings → Pets 中刷新并选择新宠物。

**关键**：ZIP 已是原生 Pet 素材，无须 GPT 重新绘画或转译。GPT 的作用仅为检查、复制、刷新和验证。网页上的连续鼠标跟随由于格式限制需要使用有限帧近似，无法像 SVG 一样任意角度平滑转动。

## 输出规格

- `spritesheet.webp`: 1536×1872，透明背景，8×9 帧网格，每格 192×208 像素。
- 9 行状态、共 57 有效帧：idle(6), running-right(8), running-left(8), waving(4), jumping(5), failed(8), waiting(6), running(6), review(6)。未使用格子完全透明。
- `pet.json`：符合官方四字段本地 Pet contract 的清单。
- 生成全部在浏览器本地执行，不向服务器发送配色或用户信息。

## 验证与限制

- 发布前已在 Chrome 中验证形状、颜色切换和橙色小果实 ZIP 真实下载；ZIP 完整性检查通过，清单、动画图集、预览图与提供的测试包逐字节一致。
- 本次发布检查未执行客户端安装验证。不同客户端版本的表现可能不同，网页预览与客户端帧动画也可能存在差异。
- 某些浏览器可能不支持 Canvas 导出 WebP，页面会显示清晰的失败提示；改用最新 Chrome / Edge 即可测试。Safari 是否可用请以实际导出成功为准。
- 本项目为独立的粉丝创作示例，不属于 OpenAI / xAI / Grok 官方发行物；公开传播时请留意原角色形象的权利边界。

官方合同：
- https://github.com/openai/skills/blob/main/skills/.curated/hatch-pet/references/codex-pet-contract.md
- https://github.com/openai/skills/blob/main/skills/.curated/hatch-pet/references/animation-rows.md


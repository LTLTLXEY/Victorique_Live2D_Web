# 维多利加 Live2D 看板娘 Web版

* 《GOSICK》维包子介绍 [维多利加·德·布洛瓦](https://baike.baidu.com/item/%E7%BB%B4%E5%A4%9A%E5%88%A9%E5%8A%A0%C2%B7%E5%BE%B7%C2%B7%E5%B8%83%E6%B4%9B%E7%93%A6/8389297)
* 基于 Live2D Cubism SDK 5.x 的轻量级看板娘组件，引入即用，支持多模型切换与台词气泡交互。

## 快速开始

将整个 `live2d/` 目录部署到网站根目录，然后在页面底部引入两个脚本：

```html
<script src="/live2d/live2dcubismcore.js"></script>
<script src="/live2d/victorique.js"></script>
```

脚本加载后会自动在页面左下角创建画布并加载模型，无需额外初始化。

## 目录结构

```
live2d/
├── victorique.js              # 主程序（自动初始化）
├── live2dcubismcore.js        # Live2D Core 运行时
├── bubble.json                # 台词气泡配置
├── fonts/                     # 本地字体资源
├── shaders/                   # WebGL 着色器
├── models/
│   ├── 维多利加/              # 模型 1
│   └── 甜品维包/              # 模型 2
├── demo.html                  # 集成示例页
└── LICENSE.md                 # 许可证
```

## 配置说明

通过修改 `bubble.json` 自定义看板娘行为：

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `enabled` | boolean | `true` | 是否启用台词气泡 |
| `durationMs` | number | `3000` | 每条台词显示时长（毫秒） |
| `size` | number | `280` | 画布基础宽度（像素），高度按模型比例自适应 |
| `position` | string | `"bottom-left"` | 页面挂载位置：`bottom-left (左下角)` / `bottom-right (右下角)` / `top-left (左上角)` / `top-right (右上角)` |
| `mobile` | boolean | `false` | 移动端是否显示，默认不显示 |
| `messages` | string[] | — | 点击触发的台词列表，按顺序轮播 |

配置示例：

```json
{
    "enabled": true,
    "durationMs": 3000,
    "size": 280,
    "position": "bottom-left",
    "mobile": false,
    "messages": [
        "「哼，愚蠢的人类，又来打扰本侦探的午睡了吗？」",
        "「谜题的碎片，正在我的脑海里重新组合呢……」"
    ]
}
```

## 交互说明

- **点击模型**：触发台词气泡，每 3 次点击切换一次台词
- **鼠标移动**：模型视线跟随光标
- **右键 / 长按**：切换服装 / 表情

## 兼容性

- 浏览器：支持 WebGL 的现代浏览器（Chrome / Firefox / Safari / Edge）
- SDK：Live2D Cubism SDK 5.x
- 移动端：默认不显示，可通过 `mobile: true` 开启

## 许可证

- **本项目代码**（`victorique.js` / 配置 / 文档）：[MIT License](MIT-LICENSE.md)
- **Live2D SDK 与模型**：详见 [LICENSE.md](LICENSE.md)（Live2D 官方许可证）

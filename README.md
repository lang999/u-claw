# 🦞 U-Claw

**AI 助手 U 盘 — 克隆、补依赖、拷到 U 盘、双击运行**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

U-Claw 把 [OpenClaw](https://github.com/openclaw/openclaw) 打包成 U 盘便携版。这个代码库就是 U 盘里的全部内容，只是不上传大依赖（Node.js、node_modules）。运行 `setup.sh` 补齐依赖后，直接拷贝到 U 盘就能用。

---

## 使用方式

```bash
git clone https://github.com/dongsheng123132/u-claw.git
cd u-claw/portable
bash setup.sh            # 补齐大依赖（Node.js + OpenClaw，国内镜像，约 1 分钟）
```

**完成后 `portable/` 就是完整的 U 盘内容。** 拷贝到 U 盘即可：

```bash
# Mac
cp -R portable/ /Volumes/你的U盘/U-Claw/

# 或直接在 Finder 拖过去
```

## U 盘上能做什么

| 功能 | Mac | Windows | 说明 |
|------|-----|---------|------|
| **免安装运行** | `Mac-Start.command` | `Windows-Start.bat` | 双击直接跑，不碰电脑 |
| **功能菜单** | `Mac-Menu.command` | `Windows-Menu.bat` | 配置、QQ、备份等 8 项 |
| **安装到电脑** | `Mac-Install.command` | `Windows-Install.bat` | 离线优先，缺啥走国内镜像 |
| **首次配置** | `Config.html` | `Config.html` | 浏览器打开，选模型填 Key |

## U 盘文件结构

```
U-Claw/                          ← 整个拷到 U 盘
├── Mac-Start.command             双击 = Mac 免安装运行
├── Mac-Menu.command              功能菜单（8 项）
├── Mac-Install.command           安装到 Mac
├── Windows-Start.bat             双击 = Windows 免安装运行
├── Windows-Menu.bat              功能菜单
├── Windows-Install.bat           安装到 Windows
├── Config.html                   首次配置页面
├── setup.sh                      补齐依赖用（开发者用）
├── app/                          ← 大依赖（setup.sh 下载，不进 git）
│   ├── core/                        OpenClaw + QQ 插件
│   └── runtime/
│       ├── node-mac-arm64/          Mac Apple Silicon
│       └── node-win-x64/           Windows 64-bit
└── data/                         ← 用户数据（不进 git）
    ├── .openclaw/                   配置文件
    ├── memory/                      AI 记忆
    └── backups/                     备份
```

**代码库 = U 盘内容 - 大依赖。** `app/` 和 `data/` 在 `.gitignore` 里。

## 桌面安装版（Electron App）

除了 U 盘便携版，还有桌面 App 版本：

```bash
cd u-claw-app
bash setup.sh            # 一键安装开发环境（国内镜像）
npm run dev              # 开发模式运行
npm run build:mac-arm64  # 打包 → release/*.dmg
npm run build:win        # 打包 → release/*.exe
```

## 支持的 AI 模型

### 国产模型（无需翻墙）

| 模型 | 推荐场景 |
|------|----------|
| DeepSeek | 编程首选，极便宜 |
| Kimi K2.5 | 长文档，256K 上下文 |
| 通义千问 Qwen | 免费额度大 |
| 智谱 GLM | 学术场景 |
| MiniMax | 语音多模态 |
| 豆包 Doubao | 火山引擎 |

### 国际模型

Claude · GPT · Gemini（需翻墙或中转）

## 支持的聊天平台

| 平台 | 状态 | 说明 |
|------|------|------|
| QQ | ✅ 已预装 | 输入 AppID + Secret 即可 |
| 飞书 | ✅ 内置 | 企业首选 |
| Telegram | ✅ 内置 | 海外推荐 |
| WhatsApp | ✅ 内置 | Baileys 协议 |
| Discord | ✅ 内置 | — |
| 微信 | ✅ 社区插件 | iPad 协议 |

## 国内镜像

所有脚本默认走国内镜像，无需翻墙：

| 资源 | 镜像 |
|------|------|
| npm 包 | `registry.npmmirror.com` |
| Node.js | `npmmirror.com/mirrors/node` |
| Electron | `npmmirror.com/mirrors/electron` |

## 开发 & 测试

```bash
# 克隆
git clone https://github.com/dongsheng123132/u-claw.git

# 补依赖
cd u-claw/portable && bash setup.sh

# 测试启动
bash Mac-Start.command   # Mac
# 或 Windows-Start.bat   # Windows

# 测试没问题 → 拷到 U 盘
# 有问题 → 修代码 → 重新测试
```

### 提交代码

```bash
git checkout -b feat/your-feature
git add -A
git commit -m "feat: your change"
git push -u origin feat/your-feature
```

## 待开发 / 欢迎贡献

- [ ] Windows 便携版完善测试
- [ ] Mac Intel 支持
- [ ] Linux 支持（AppImage）
- [ ] 桌面版自动更新
- [ ] SkillHub 技能市场功能完善
- [ ] 多语言支持（English UI）

## FAQ

**Q: 需要翻墙吗？**
安装不需要。运行需要联网调 API，国产模型无需翻墙。

**Q: U 盘需要多大？**
建议 4GB 以上（完整版约 2.3GB）。

**Q: 能分发吗？**
MIT 协议，随便复制。

**Q: Mac 提示"未验证的开发者"？**
右键脚本 → 打开。

## License

[MIT](LICENSE)

## 联系

- 微信: hecare888
- GitHub: [@dongsheng123132](https://github.com/dongsheng123132)
- 官网: [u-claw.org](https://u-claw.org)

---

**Made with 🦞 by [dongsheng](https://github.com/dongsheng123132)**

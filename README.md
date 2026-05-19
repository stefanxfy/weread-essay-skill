# weread-essay-skill

微信读书读后感写作助手。把你在微信读书里的划线和想法，变成一篇真正值得发的文章。

## 依赖的 Skills

本 skill 依赖以下两个底层 skill，**必须先安装**：

| Skill | 说明 | 安装文档 |
|-------|------|------|
| `weread-skills` | 微信读书原子 API，提供书籍搜索、划线读取、笔记获取等接口 | [weread-skills 安装指南](https://weread.qq.com/r/weread-skills) |
| `huashu-weread-advisor` | 微信读书高阶顾问工作流，提供书架分析、书单推荐、阅读复盘等编排规则 | [huashu-weread-advisor 安装指南](https://github.com/alchaincyf/huashu-weread) |

## 安装本 Skill

### 方式一：从 GitHub 安装（推荐）

```bash
# 克隆仓库到任意目录
git clone git@github.com:stefanxfy/weread-essay-skill.git ~/weread-essay-skill

# 同步到 Hermes skills 目录
cp -r ~/weread-essay-skill ~/.hermes/skills/weread-essay-skill
```

### 方式二：本地已有开发目录

开发目录已 clone 到本地，直接同步：

```bash
cp -r /Users/fanyunxu/Desktop/myproject/ailearning/weread-essay-skill/ ~/.hermes/skills/weread-essay-skill
```

## 前置要求

- `WEREAD_API_KEY` 环境变量（通过 weread-skills 配置）
- 微信读书账号中已有该书的划线记录

## 使用方式

触发方式（直接对话即可）：

- 「写一篇读后感」
- 「帮我整理笔记，写篇感想」
- 「这本书/这章我想写篇公众号文章」
- 「想把我的划线整理成一篇读书笔记」

### 工作流程

1. **确认书目** — 根据书名/章节获取微信读书划线数据
2. **确认方向** — 与你确认核心论点和附录范围
3. **生成正文** — 文学性 + 理性分析 + 情感抒发，摘抄≤3处
4. **生成附录** — 完整保留所有划线原文，每条附即时感想

### 输出结构

```
读后感正文
  - 书名、章节、划线条数
  - 2-4 个核心论点展开
  - 发人深省的结论

## 附：我划下的每一句话
  1. 「……原文摘录……」
     我的感受/思考：……
  2. 「……原文摘录……」
     我的感受/思考：……
  （全部保留，不删减）
```

## 开发说明

| 路径 | 说明 |
|------|------|
| `/Users/fanyunxu/Desktop/myproject/ailearning/weread-essay-skill/` | 开发目录（带 Git） |
| `~/.hermes/skills/weread-essay-skill/` | Hermes 运行时目录 |

**开发流程**：改开发目录 → `git commit && git push` → 同步到 Hermes 运行目录

```bash
cd /Users/fanyunxu/Desktop/myproject/ailearning/weread-essay-skill
git add . && git commit -m "update" && git push

# 同步到 Hermes
cp -r workflows/ ~/.hermes/skills/weread-essay-skill/
cp SKILL.md ~/.hermes/skills/weread-essay-skill/
```

## 文件结构

```
weread-essay-skill/
├── README.md          # 本文件
├── SKILL.md           # Skill 元数据（Hermes 加载用）
└── workflows/
    └── essay.md       # 读后感写作工作流详细规范
```

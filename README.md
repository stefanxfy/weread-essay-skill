# weread-essay-skill

微信读书读后感写作助手。把你在微信读书里的划线和想法，变成一篇真正值得发的文章。

## 依赖的 Skills

本 skill 依赖以下两个底层 skill，**必须先安装**：

| Skill | 说明 | 安装文档 |
|-------|------|------|
| `weread-skills` | 微信读书原子 API，提供书籍搜索、划线读取、笔记获取等接口 | [weread-skills 安装指南](https://weread.qq.com/r/weread-skills) |
| `huashu-weread-advisor` | 微信读书高阶顾问工作流，提供书架分析、书单推荐、阅读复盘等编排规则 | [huashu-weread-advisor 安装指南](https://github.com/alchaincyf/huashu-weread) |

## 安装

从 GitHub 克隆后，按你的 Agent 产品说明加载 skill。典型方式：

```bash
git clone git@github.com:stefanxfy/weread-essay-skill.git
```

加载方式请参考对应 Agent 产品的 skill 加载文档。

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

## 文件结构

```
weread-essay-skill/
├── README.md          # 本文件
├── SKILL.md           # Skill 元数据
└── workflows/
    └── essay.md       # 读后感写作工作流详细规范
```

## 本地开发

如需修改 skill内容，先在本地修改，测试通过后提交 GitHub：

```bash
cd weread-essay-skill
# 编辑 SKILL.md 或 workflows/essay.md
git add . && git commit -m "your changes" && git push
```

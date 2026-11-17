# GitHub 趋势日报

本仓库由 [dsh-github-trending](https://github.com/morehao/dsh-github-trending) 插件自动维护，每天定时抓取 GitHub Trending 榜单，用大模型生成中文摘要后提交到此仓库。

## 更新节奏

- **日榜**：每天 08:30（Asia/Shanghai）自动生成
- **周榜**：每周日生成
- **月榜**：每月最后一天生成

内容由插件进程内调度产生，运行结果为一条 `trending/...` 分支，经 PR 自动合并进 `main`。

## 目录结构

```
trending/
├── index.md                    # 全部期次的索引
├── daily/YYYY-MM/YYYY-MM-DD.md # 日榜（Markdown）
├── daily/YYYY-MM/YYYY-MM-DD.json
├── weekly/...
└── monthly/...
```

每份 Markdown 都带 YAML front matter：`date`、`period`、`languages`、`count`、`degraded`、`contentHash`、`coreVersion`、`generatedAt`。

## 数据来源

- 抓取：GitHub Trending 页面（经插件内置核心 trendradar 0.13.4）
- 摘要：DeepSeek 模型（`deepseek-v4.1-flash`）
- 仓库 star 增量：GitHub REST API（认证调用，5000 次/小时配额）

仅作个人技术阅读用，数据版权归各仓库作者所有。
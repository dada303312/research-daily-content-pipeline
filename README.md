# research-daily-content-pipeline

[![GitHub repository](https://img.shields.io/badge/GitHub-dada303312%2Fresearch--daily--content--pipeline-181717?logo=github)](https://github.com/dada303312/research-daily-content-pipeline)

一个用于每日研究内容运营的 Codex skill：

- 多领域发现最近的 Q1、中科院一区或顶刊论文；
- 在没有可核验全文时拒绝撰写正式文章；
- 将论文转化为证据充分的中文解读；
- 使用统一的公众号排版和品牌签名条；
- 通过公众号流程发布并记录结果；
- 把缺少全文的候选标记为 needs_pdf，提醒用户补充原文。

仓库同时包含 skill、操作参考资料、统一签名条资产和技术博客。

## 安装

将本目录复制到 Codex skills 目录，然后这样调用：

~~~text
Use $research-daily-content-pipeline to run today’s literature-to-WeChat pipeline.
~~~

默认配置面向三个领域：

| 时间（北京时间） | 领域 |
|---|---|
| 08:30 | 钝化土壤微生物 |
| 09:00 | Na 土壤生态 |
| 09:30 | 固体废物和生活垃圾碳排放 |

换账号或换主题时，修改 references/fangcun-domains.md。

## 设计原则

1. **候选质量优先于数量。** 每个领域目标 10–15 条候选，但不能为了凑数降低期刊层级。
2. **时效优先。** 最近 12 个月优先，其次最近 3 年，再其次 3–5 年高相关文献。
3. **全文是门禁，不是偏好。** 没有全文时标记 needs_pdf 并请用户提供，不用摘要替代全文。
4. **证据必须保留。** 系统边界、单位、CO2/CH4/N2O/CO2e/GWP、情景、统计和限制条件都要保留。
5. **品牌是组件，不是每篇临时决定。** 签名条和排版结构固定。

## 技术博客

- [从日更公众号到可复用 Codex Skill](blog/from-daily-account-to-codex-skill.md)：完整拆解这条工作流的设计方法。

## Pages CMS

仓库包含 .pages.yml。打开 https://app.pagescms.org，使用 GitHub 登录，在 dada303312 账号安装 Pages CMS GitHub App，再选择本仓库。CMS 会显示：

- blog/：技术博客；
- docs/：统一研究工作流；
- media/：媒体存储。

## 文件结构

~~~text
SKILL.md
agents/openai.yaml
references/fangcun-domains.md
references/workflow.md
references/quality-gates.md
assets/signature-bar.html
.pages.yml
docs/daily-workflow.md
blog/from-daily-account-to-codex-skill.md
~~~

## 发布安全

遇到管理员或运营者扫码验证时，skill 会停止并等待用户处理，不绕过平台安全验证。默认关闭群发通知；只有用户明确要求时才开启。

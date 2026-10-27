# 明泳吉 · 大模型应用研发

> 6 年研发经验，近 3 年专注大模型应用落地：RAG 知识库检索、Agent 工具编排、模型路由与推理成本优化。
> 目前负责物流场景智能体的架构与工程化落地——把中台的查询与操作能力，封装成用户一句话就能办成事的 Agent。

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square)
![Milvus](https://img.shields.io/badge/Milvus-00A1EA?style=flat-square)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

## 🎯 我在做什么

把大模型从"能聊天"做到"能办事"：**检索要准、工具要稳、成本要控、结果要可验证**。
日常工作是 Agent 架构设计、RAG 检索链路调优、工具网关与多步编排、Prompt 工程化，以及上线后的评测与稳定性治理。

| 能力方向 | 具体实践 |
| --- | --- |
| RAG 与知识库 | 中文父子块递归切分、按业务域拆多集合、BM25 + 向量双路召回 + reranker 精排 |
| Agent 与编排 | LangGraph 多步编排（意图 → 规划 → 执行 → 校验 → 回复）、工具网关、任务级记忆 |
| 模型与成本 | 三层路由（基线 → 初筛 → 大模型精判）、小样本微调、蒸馏 + int8 量化 |
| 工程与质量 | FastAPI + SSE 流式、超时熔断降级、Docker 化、端到端用例回归与 Bad Case 复盘 |

---

## 📌 代表项目

### 🚚 吉小智 · 物流运营智能体 `2025.05 — 2026.10`
面向吉速物流整车、零部件、售后备件三条业务链，服务三类用户近 6 万人。此前查数据、走流程要在 OA / WMS / TMS 之间反复切换，规则口径不统一，传统问答只能检索文档、无法直接办事。

- **知识库与检索**：父子块递归切分 + 按域拆 5 个 Milvus 集合 + BM25 精确匹配，知识问答准确率 **76% → 92%**
- **工具与编排**：12 类中台能力封装为原子工具，LangGraph 编排多步任务，多步调用准确率 **90%+**
- **路由与会话**：精确匹配 → 知识检索 → 工具执行三层路由，高频命中 **30ms** 返回；最近 5 轮对话 + 任务级记忆，追问无需重报运单号
- **稳定性**：90 秒任务看门狗、单步超时重试与兜底、规则数据 24 小时增量同步
- 结果：80% 的标准查询与简单异常自主完成，跨系统查询由 5–6 分钟压至秒级，运营跨系统查询量 **-45%**

`FastAPI` `LangGraph` `Milvus` `BM25` `bge-m3 / bge-reranker` `Redis` `MySQL` `SSE`

### 📦 物流场景大模型智能体应用 `2026.05 — 2026.10`
覆盖运单、仓储、结算、异常件、售后等高频业务，替代人工在多个物流系统之间的反复检索与流转。

- **工具调用网关**：系统接口统一封装，参数校验 + 超时重试 + 熔断降级，工具调用成功率 **95%**
- **多步编排**：LangGraph ReAct 推理循环，端到端任务完成率 **88%**
- **Prompt 工程**：角色 / 任务 / 约束 / 输出四段式 System Prompt + Few-shot，指令遵循率 **+42%**
- **交互**：会话持久化与上下文继承（支持中断恢复），SSE 流式输出，业务查询自动化率 **85%**、人工咨询量 **-60%**

`LangGraph` `ReAct` `SSE` `Prompt Engineering`

### 💬 商评宝 · 电商评论情感与类目归类 `2023.05 — 2023.12`
服务淘宝店铺后台两条短文本处理需求：评论做「整体极性 + 质量 / 物流 / 服务 / 性价比 / 外观」五维情感分析，商品标题做 10 个一级类目归类。

- **数据与标注**：内部业务数据清洗出 6 万余条样本，自建标注规范标注至维度级；针对口语化、谐音错别字、表情混排做扰动增强
- **三层路由**：随机森林基线 → FastText 初筛 → BERT 精判，仅歧义样本进大模型
- **小样本**：冻结 embedding 与前 6 层 + 分层学习率 + Focal Loss，冷门类目效果拉起、训练速度提升近一倍
- **成本与服务**：知识蒸馏 + int8 量化压缩体积 **72%**；模型延迟加载 + warmup，BERT 超时降级 FastText
- 结果：类目归类 **92%+ / <100ms**，维度情感 **Macro-F1 88%+ / <200ms**，**70%** 评论分析替代人工

`BERT` `FastText` `Focal Loss` `知识蒸馏` `int8` `Flask` `Vue3` `ECharts`

---

## 🧰 技术栈

- **语言 / 框架**：Python、FastAPI、Flask、Vue3
- **大模型应用**：LangGraph、LangChain、Prompt 工程、Function Calling / 工具编排、RAG
- **模型**：DeepSeek / Qwen / 通义、BERT、FastText；微调、蒸馏、量化
- **检索与存储**：Milvus、Chroma、BM25、bge-m3、bge-reranker、MySQL、Redis
- **工程与交付**：Docker / Docker Compose、GitLab CI、Jenkins、Linux；SSE 流式、超时熔断降级
- **质量**：大模型输出自动化评测（幻觉率 / 准确率）、端到端用例回归、Bad Case 复盘闭环

---

## 📫 联系

- 📧 邮箱：13333698381@163.com
- 💼 求职意向：大模型应用研发 / AI 应用开发
- 🌐 在线简历：[mingyongji.github.io/new-repo](https://mingyongji.github.io/new-repo/)

> 本仓库为个人主页，项目源码因涉及公司业务未公开；如需了解实现细节，欢迎邮件交流或查看简历中的技术方案说明。

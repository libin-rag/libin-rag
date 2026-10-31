# RAG · LLM 应用开发

专注「数据不出网」场景下的 LLM 落地——把非结构化文档变成**可溯源、可评测**的问答服务。

全本地链路：文档解析 → 中文优先切分 → 本地向量化入库 → Top-K 检索 → 受约束生成。

---

## 项目

**[rag-doc-qa](https://github.com/libin-rag/rag-doc-qa)** — 私有文档 RAG 知识库问答系统

答案带出处，越界问题按固定话术拒答，不做云端依赖。

| 环节 | 选型 / 做法 |
| --- | --- |
| 后端 | FastAPI + Pydantic v2，8 条 REST 路由，SSE 逐字推送 |
| 检索 | Chroma 向量库，bge-small-zh 中文嵌入，块长 800 / 重叠 150 |
| 生成 | 提示词硬约束「仅依据检索片段作答」，temperature=0 |
| 前端 | 原生 HTML/CSS/JS 单页（另有早期 Streamlit 版本对比） |
| 评测 | 30 题基础集（20 可答 + 10 越界）+ 10 题跨条款困难集 |

评测结果：基础集检索命中 **20/20**、越界拒答 **10/10**，困难集完全正确 **9/10**，平均 **1.33 s/题**、P95 **3.02 s**。

---

## 技术栈

`Python` `FastAPI` `Pydantic v2` `LangChain` `Chroma` `bge-small-zh` `Streamlit` `Ollama` `DashScope`

## 联系

- 项目相关问题请提 [Issue](https://github.com/libin-rag/rag-doc-qa/issues)

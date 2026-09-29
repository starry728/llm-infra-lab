# llm-infra-lab

LLM 推理系统自学仓库。一句话：把 vLLM 跑通、把源码读懂、把数据测准。

## 目录

```
gateway/   C++ 推理网关：SSE 流式转发、上游连接池、令牌桶限流、熔断、
           prefix-aware 一致性哈希路由（进行中）
bench/     压测与参数扫描脚本（vllm bench serve / guidellm），自动出图出表
sched/     多边缘节点调度仿真（K3s 多节点 + 带宽约束）
notes/     vLLM V1 源码笔记与论文笔记，统一格式：问题 / 方法 / 代价与适用边界
docs/      环境搭建笔记与踩坑记录（含《vLLM 环境踩坑全记录》）
reports/   性能评测报告（数据全部来自云端 4090，报告内注明硬件与版本）
```

## 环境分工
- 日常开发与冒烟验证：本地 WSL2 + RTX 5060 Laptop 8G（只跑 ≤3B 或 INT4 量化模型）
- 一切 benchmark 数据：AutoDL RTX 4090 24G，固定机型保证纵向可比
- 多节点：K3s（3 节点）

## 一键复现（目标，尚未完成）

```
docker compose up -d   # 3 个 vLLM + gateway + prometheus + grafana
```

## 进度
- [x] 容器内 vLLM serve + 第一份 benchmark（2026-10）
- [ ] gateway P0（SSE 转发 / 连接池 / 限流熔断）
- [ ] gateway P1（prefix-aware 路由）
- [ ] vLLM V1 源码笔记 8 篇
- [ ] 评测报告 v1（≥10 组实验）
- [ ] 多边缘调度仿真 v1

## 说明
README 里的结论可能过期，数据以 reports/ 为准。

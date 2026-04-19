# 八股文索引 · Question Bank

本文件用于 **L4 外延层**的"点名 + 指路"。Agent 不要展开讲，只告诉用户"你这个点涉及下面这几条，请自行背诵"。

组织原则：按**领域**分组，每条题目标注**必知 / 常问 / 可能问**三档优先级。

---

## 前端

### 浏览器渲染 & 性能
- [必知] 浏览器渲染五阶段（解析 HTML → 构建 DOM → CSSOM → Layout → Paint → Composite）
- [必知] 回流（Reflow）vs 重绘（Repaint）：触发条件 / 优化手段
- [必知] Critical Rendering Path / 首屏优化（内联关键 CSS / preload / async-defer）
- [必知] Web Vitals：LCP / FID / INP / CLS / TTFB / FCP 定义 + 阈值 + 测量 API
- [常问] requestAnimationFrame vs requestIdleCallback vs setTimeout
- [常问] 合成层（Composite Layer）与 will-change / transform / opacity 的 GPU 加速
- [常问] 资源加载优先级（fetchpriority / 浏览器隐式优先级）
- [可能问] Paint Timing API / Long Task API / PerformanceObserver 源码级使用

### JavaScript 引擎 & 运行时
- [必知] 事件循环（Event Loop）+ 宏任务 / 微任务
- [必知] V8 内存模型（新生代 / 老生代 / Scavenge / Mark-Sweep / Mark-Compact）
- [必知] 原型链 + `new` 的过程 + `this` 绑定四规则
- [常问] 闭包内存泄漏典型场景
- [常问] Promise A+ 规范 / async-await 执行顺序 / Promise 链式的错误冒泡
- [常问] Generator + Iterator / Symbol
- [可能问] V8 隐藏类 / 内联缓存（ICs） / TurboFan 优化

### React
- [必知] 函数组件 vs 类组件 / hooks 使用规则 / 依赖数组陷阱
- [必知] 虚拟 DOM + diff 算法 / Key 的作用
- [必知] Fiber 架构 / 时间切片 / Concurrent Mode
- [必知] setState 批处理（React 18 autoBatch）/ 异步回调的批处理边界
- [常问] useEffect vs useLayoutEffect / 执行时机
- [常问] useMemo / useCallback / React.memo 使用场景和误用
- [常问] Server Components / Suspense / use()
- [常问] Context 性能陷阱 / 合理的 state 拆分
- [可能问] 自定义 Reconciler / Scheduler 优先级

### 状态管理
- [必知] Redux 三原则 / reducer 纯函数 / 中间件机制
- [必知] Zustand / Jotai / Valtio 的核心差异
- [常问] 全局 state vs 局部 state 边界
- [可能问] 不可变数据结构（Immer / Immutable.js）原理

### CSS
- [必知] Flex + Grid 完整用法
- [必知] CSS 层叠规则 / 权重计算
- [必知] BFC / IFC / FFC / GFC
- [常问] CSS-in-JS 选型（styled-components / emotion / vanilla-extract / CSS Modules）
- [常问] CSS 变量 / @layer / @container
- [常问] 暗色主题实现（CSS Variables / prefers-color-scheme）

### 打包 & 构建
- [必知] Webpack / Vite / Turbopack / Rspack 核心差异
- [必知] Tree Shaking 原理 / sideEffects 配置
- [必知] Code Splitting（动态 import / Route-level / Component-level）
- [常问] HMR 原理
- [常问] Source Map 原理
- [可能问] Rollup 插件系统 / esbuild 与 SWC

### HTTP / 网络
- [必知] HTTP/1.1 vs HTTP/2 vs HTTP/3
- [必知] HTTPS 握手 / TLS 1.2 vs 1.3
- [必知] 跨域：CORS 完整流程 / JSONP / 反向代理
- [必知] Cookie 属性（HttpOnly / SameSite / Secure / Partitioned）
- [常问] CDN 原理 / 回源策略 / 边缘计算
- [常问] WebSocket vs SSE vs 长轮询
- [常问] 强缓存 vs 协商缓存 / ETag vs Last-Modified

### 安全
- [必知] XSS（反射型 / 存储型 / DOM 型）原理 + 防御（CSP / 编码）
- [必知] CSRF 原理 + 防御（SameSite / Token / Origin-Referer）
- [必知] 点击劫持 / X-Frame-Options / CSP frame-ancestors
- [常问] SSRF
- [常问] Subresource Integrity (SRI)
- [可能问] Trusted Types / COOP / COEP / CORP

---

## 后端

### 语言 & 运行时
（按项目用的语言选对应节）

**Node.js**
- [必知] 事件循环（libuv 六阶段）/ process.nextTick / Promise 优先级
- [必知] Cluster / Worker Threads / 进程间通信
- [常问] Stream 四种（Readable / Writable / Duplex / Transform）/ 背压
- [常问] V8 内存限制 + 调优
- [可能问] N-API / 原生模块 / Node-addon

**Java**
- [必知] JMM / volatile / synchronized / AQS
- [必知] JVM 内存区域 + GC 算法
- [必知] Spring IoC / AOP / Bean 生命周期
- [常问] JUC 核心类（Executor / ForkJoin / CompletableFuture）
- [常问] Spring Boot 自动配置原理

**Go**
- [必知] GMP 调度模型
- [必知] channel + select / goroutine 泄漏
- [常问] 内存模型 / happens-before
- [常问] 接口底层（iface / eface）

**Python**
- [必知] GIL 机制 / 多线程 vs 多进程 vs asyncio
- [常问] CPython 内存管理 / GC
- [常问] asyncio 事件循环

### Web 框架
- [必知] 路由实现（trie / radix tree）
- [必知] 中间件机制（洋葱模型）
- [必知] 请求上下文隔离方案
- [常问] 依赖注入 / IoC 容器实现
- [常问] ORM 原理（Active Record vs Data Mapper）

### 分布式基础
- [必知] CAP / BASE / ACID
- [必知] 分布式锁（Redis Redlock / Zookeeper / etcd）+ 各方案缺陷
- [必知] 分布式事务（2PC / 3PC / TCC / Saga / 本地消息表 / 最大努力通知）
- [必知] 一致性哈希 / 虚拟节点
- [常问] Raft / Paxos 基本思想
- [常问] 幂等性设计（Token / 状态机 / 唯一键）
- [常问] 分布式 ID（Snowflake / Leaf / UUID v7）
- [可能问] CRDT / Vector Clock

### 消息队列
- [必知] Kafka 架构（Broker / Partition / Replica / ISR）
- [必知] 消息可靠性三要素（发送 / 存储 / 消费）
- [必知] 消费端幂等 / 重复消费处理
- [常问] 顺序消息 / 延时消息 / 事务消息实现
- [常问] Kafka vs RabbitMQ vs RocketMQ vs Pulsar 对比
- [常问] 消息积压处理方案

### 缓存
- [必知] Redis 五大数据结构 + 底层实现（SDS / ziplist / quicklist / skiplist / intset / hashtable / listpack）
- [必知] Redis 持久化（RDB / AOF / 混合）
- [必知] 缓存穿透 / 击穿 / 雪崩 + 对应方案
- [必知] 缓存一致性方案（Cache-Aside / Write-Through / Write-Behind / 延迟双删）
- [常问] Redis 集群（哨兵 / Cluster）+ 主从同步
- [常问] 热 key / 大 key 识别与处理
- [可能问] Redis 6 多线程 IO / Redis 7 Functions

### 数据库
- [必知] B+ 树索引原理 / 聚簇索引 vs 二级索引 / 覆盖索引 / 最左匹配
- [必知] MySQL 事务隔离级别 + MVCC 实现
- [必知] 锁（表锁 / 行锁 / 间隙锁 / Next-Key Lock）
- [必知] Explain 关键字段 / 索引失效场景
- [必知] 主从复制原理（binlog / 半同步 / 并行复制）
- [常问] 分库分表策略 + 扩容方案
- [常问] MySQL vs PostgreSQL vs MongoDB 选型
- [常问] 慢查询优化思路
- [可能问] MySQL 8 新特性 / 窗口函数 / CTE

---

## AI / Agent（LLM 应用工程）

- [必知] Transformer / Attention 机制 / KV Cache
- [必知] Prompt 工程：Zero/Few-shot / CoT / ReAct / Self-Consistency
- [必知] Function Calling / Tool Calling 协议（OpenAI / Anthropic / 火山）
- [必知] RAG 基础：Embedding / 向量检索 / 重排序
- [必知] Token 计费模型 / Context Window 管理
- [常问] 幻觉（Hallucination）来源与缓解手段
- [常问] 多 Agent 协作模式（Supervisor / Reflection / Debate）
- [常问] 流式输出协议（SSE 事件格式 / 增量 JSON 解析）
- [常问] Embedding 模型选型（OpenAI text-embedding-3 / bge / m3e）
- [可能问] MCP 协议 / AutoGen / LangGraph

---

## 部署 & 运维

- [必知] Docker 镜像分层 / Dockerfile 最佳实践 / 多阶段构建
- [必知] K8s 核心对象（Pod / Deployment / Service / Ingress / ConfigMap）
- [必知] 健康检查（liveness / readiness / startup）
- [常问] 滚动发布 / 蓝绿 / 金丝雀
- [常问] 服务发现（DNS / Consul / Nacos）
- [常问] Prometheus + Grafana + AlertManager
- [常问] ELK / Loki 日志链路
- [可能问] eBPF / Service Mesh（Istio / Linkerd）

---

## 安全（通用）

- [必知] OWASP Top 10（当年最新版）
- [必知] 对称 vs 非对称加密 / AES / RSA / ECC
- [必知] Hash / HMAC / 常用哈希算法（SHA-256 / bcrypt / Argon2）
- [必知] JWT 结构 + 签名算法 + 常见漏洞（alg: none / 弱密钥）
- [必知] OAuth 2.0 + OIDC 完整流程 / PKCE / State
- [常问] 零信任架构
- [常问] 限流算法（令牌桶 / 漏桶 / 滑动窗口 / 漏桶 vs 令牌桶）
- [可能问] 供应链攻击 / SBOM

---

## 使用说明

Agent 在 L4 阶段**不要背诵**上述内容，只做以下两件事：

1. **点名**：告诉用户"你这个点涉及下面这 N 条八股"
2. **指路**：给到本文件的小节锚点，让用户自己去准备

示例：
> "SSE 这块会被追问八股：
> - [前端-HTTP/网络] WebSocket vs SSE vs 长轮询
> - [后端-Web 框架] 中间件机制 / Stream 背压
> - [AI] 流式输出协议 / 增量 JSON 解析
>
> 这三条你打开 `QUESTION_BANK.md` 对应小节复习下，面试前一天过一遍就行，不用我陪你过。"

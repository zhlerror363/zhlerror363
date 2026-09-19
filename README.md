# 👋 林子恒（zhlerror363）

**2027 届 · 跨境电子商务 · 杭州**｜方向：AI 产品经理 / AI 应用 / 量化研究

## 🚀 项目

### AI 产品 · 已上线

- **finance-hub** · 多用户 AI 记账 SaaS —— 记账 / 资产 / 看板 + **DeepSeek AI 智能记账与消费洞察**；账号注册登录、**按用户数据完全隔离**、管理员分配 AI 额度、独立只读演示库；后端只用 Node 内置 `node:http` + `node:sqlite`（**零第三方依赖**），前端原生 JS + 手写 SVG 图表；含 PM2 安全守卫、cron 健康检查（挂了自动拉起）、nginx 反代 + HTTPS。**已上线运行**（阿里云 + ICP 备案 + 公安联网备案）。
  → 线上 <https://financehub.com.cn>｜代码 <https://github.com/zhlerror363/finance-hub>
- **stock-quant** · 个人 A 股量化研究与模拟交易系统 —— **知识驱动模拟盘**（直播转写 / 笔记 / 交易复盘 → AI 蒸馏成「规则卡」 → 策略场建独立 100 万模拟账户 → 1/5/20 日归因 → AI 进化提案，人审批后试跑）+ **多 AI 账户竞技场**（多模型同场决策、独立投研委员会双重复核）+ 可信可复现回测（内容寻址 + 证据指纹 + 只读制品库）+ 面向真实券商的生产级安全边界（order intent 生命周期、对账、预交易风险授权 + RSA attestation）；默认 PAPER/SANDBOX，真实资金执行关闭。TypeScript + Node 22（内置 SQLite，无 ORM）+ React 19 + Vite，核心模块均有配套单元测试（3 个测试文件 / 45 条断言）。
  → 代码 <https://github.com/zhlerror363/stock-quant>（公开作品集框架，核心策略源码不公开）

### Agent 与自动化

- **ai-portfolio** · AI Agent 作品集（三线）—— 求职 / 知识→因子 / 跨境选品三条线**共用同一套 Agent 骨架**：采集 → 结构化 → LLM 判断 → 规则校验 → 输出 → 复盘；阶段间有可断点续跑的中间产物，每阶段产物与日志落盘（能回答「哪一步错了、为什么」）。三条线都已用真实数据跑出产物：A 线抓 7 份真实 JD 做匹配打分与简历差异报告；B 线对 74 篇课程 / 复盘纪要建索引并抽取因子候选判据（A 17 / B 8 / C 10，291 处引用逐条核验 0 未命中）；C 线采 3 个品类的真实评论、产出痛点证据与选品报告。
- **live-transcribe** · 直播录制转写流水线 —— Windows 计划任务按点自动跑完整链路：进直播间 → WASAPI 环回录音（不是抓流地址，微信视频号 / 抖音通用）→ 云端 ASR 转写 → 落盘文稿。核心件：`record_live.py`（编排）、`recorder.py`、`cloud_asr.py`、`batch_transcribe.py`、`record_lock.py`（录音 / 转码互斥锁）；计划任务 `LiveTranscribe_morning_wechat` / `LiveTranscribe_noon_douyin`；已累计 59 段录音与 40 份转写文稿（最近一场 2026-09-18）。
- **wrist-shell · 随身任务站** —— 鸿蒙手表端（ArkTS / ArkUI，HarmonyOS NEXT）+ 单包 TS 工程：公网中继、通用 CLI 网关（任何命令行 agent 都能接）、协议参考实现。手表上说一句，电脑上执行，输出逐行回传手腕。公开的 `protocol-v0`、**不运营任何中心服务器**、一次性配对短码换设备令牌（只存哈希、可远程吊销）、会话级审批闸门。同 WiFi 下直连，无需服务器。

### 工程化 / 基础设施

- **service-console** · 服务调度台 —— 一个网页（`127.0.0.1:3210`）看齐本机所有服务、计划任务与静态产物：端口探测实时状态灯 + 启停按钮 +「后台保护」总开关；带**守护器一致性校验**（与看门狗的权威清单交叉比对，差异逐条红字列出）。Node + 原生 HTML/CSS/JS，**零构建、零外部依赖**。
- **DSH-platform** · DSH 平台件（四个）—— `service-watch` 服务看门狗（Windows 计划任务每 2 分钟一轮，进程类服务的权威清单在这里：cwd / command / port / health，挂了自动拉起）、`workspace-backup` 增量 zip 备份（逐源校验、打包后重算哈希比对，按 label 保留最近 N 份，产物落 `E:\Backup\`）、`session-inspect` 会话取证、`zcode-bridge` 人机群聊桥。
- **DSH-Rebuild-Pack** · 应急重建包 —— 把整套本机环境做成**可交付的恢复包**：AES-256 + 头加密归档、**全量 SHA-256 清单**（framework / packroot / tools / data 四层共 578 行，含包根文件与还原工具自身）、分阶段还原手册（preflight → core-install → skins-and-presets → self-healing → wechat-bridge → extras → verify，前五个阶段各带 `verify.md` 判据与 `rollback.md` 回滚说明）、私钥一律走加密资产不落明文。

> 以上均为个人项目；目前公开仓库为 [finance-hub](https://github.com/zhlerror363/finance-hub) 与 [stock-quant](https://github.com/zhlerror363/stock-quant)，其余为本地 / 私有仓库。项目最新状态以各自 README 为准。

## 🛠 技能

- **AI 与大模型**：Prompt Engineering、大模型 API（DeepSeek / Qwen）与应用落地、Agent
- **数据**：Python（Pandas / Requests）、SQL、数据分析
- **工程**：Node、React、SQLite、部署上线
- **跨境**：独立站运营、海外社媒、外贸单证与退税、海外用户场景

## 📮 联系

- Email：zihenglin2027@163.com
- 期望方向：**AI 产品经理**（校招 / 实习）

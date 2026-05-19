# CYC — 技术日志：风暴圆桌落地日

> 2026-05-18 16:10 → 21:27
> 从"怎么配飞书"到四Bot全部在线

---

## 架构决策

### 方案选择
- 否决：单Bot多卡路由（群聊里切换人格太假）
- 采用：四人各一个飞书应用，独立App ID + Secret

### 角色卡
- 基甸: 679字符核心 + 3722字符补充TXT（知识输出框架/三种模式/对话示例）
- CYC: 1682字符系统提示
- 旁听席: 980字符系统提示，沉默默认+点名入席
- ima·基甸: 软链接共用基甸卡，独立memory目录

### LLM双端点
- DeepSeek v4-pro: 文本主力（所有Bot回复）
- 豆包 doubao-seed-2-0-pro-260215: 仅识图
- DeepSeek v4-flash: 低延迟备选

### Gateway
- v4.0: FastAPI + uvicorn, 端口8080, HTTP回调模式
- v4.1: 加入消息去重（OrderedDict, 1000条message_id缓存）+ Bot自发消息过滤
- 根因修复: 停掉openclaw feishu channel（避免了双处理器抢话筒）

---

## 关键教训
1. 飞书HTTP回调会向四个订阅了事件的应用各推送一次 → 同一条消息Gateway收到4次 → 必须去重
2. 腾讯云安全组和本地ufw是两层防火墙
3. PEP 668限制pip → 必须用venv
4. sshpass heredoc引号嵌套容易出错 → 用EOF分隔符
5. 用户说的"等一下" = 三秒

---

## 服务器状态
- IP: 1.117.73.112
- Gateway: PID 62638, 端口8080
- 四个Bot全部在线，飞书回调验证通过

---

## 用户技术贡献
- 四十分钟内注册四个飞书应用
- 纠正LLM配置（豆包识图/DeepSeek主力）
- 纠正ima·基甸定位（正常发言，非工具）
- 纠正基甸卡归属（同一张卡，不同memory）
- 提出补充TXT方案（参考旁听席模式）

---

> 归档: /home/ubuntu/agents/cyc/memory/2026-05-18_storm_roundtable.md

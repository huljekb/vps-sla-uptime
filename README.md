# 99.9% uptime VPS hosting：99.9% 和 99.99% 一年差 8 小时，搬瓦工全套餐价格与 SLA 赔付条款一次讲清

几乎所有 VPS 服务商的页面上都写着 "99.9% uptime guarantee"，BandwagonHost（搬瓦工）也不例外——它的退款政策页面明确列着 "99.9% uptime guarantee" 和 "30-day refund policy"。但这个数字具体意味着什么、有没有配套赔付、值不值得为更高的 uptime 多花钱，多数产品页不会主动告诉你。这篇文章把这几个问题拆开算清楚，再对照搬瓦工目前在售的全部套餐，看看哪些方案真正把 uptime 写进了 SLA。

## 99.9% uptime 到底承诺了什么：先把账算清楚

99.9% 的含义是每月允许约 43 分钟的不可用时间。按一个 30 天、共 43,200 分钟的月份计算：

$$43200 \times (1 - 0.999) = 43.2 \text{ 分钟}$$

换算到一年，就是大约 8.76 小时。而 99.99% 对应的是每月约 4.3 分钟、一年约 52 分钟。这两个"9"的差距，一年下来是 8 个小时左右——对个人博客无感，对一个靠线上订单吃饭的电商站就是另一回事了。

还有一个容易被忽略的点：**uptime 承诺几乎都附带排除条款**。以搬瓦工 2025 年 11 月更新的 SLA 文档为例，以下情况都不计入停机时间：

- 提前 24 小时通知的计划内维护，以及不超过 10 分钟的紧急维护
- 用户自己的系统、脚本、防火墙配置导致的问题
- 遭受 DDoS 攻击及由此触发的流量拦截（搬瓦工不为 SLA 套餐提供 DDoS 过滤）
- 上游网络、骨干网故障等不在其直接控制范围内的问题

所以"99.9% uptime"从来不是"这台机器一整年不宕机"，而是"在排除这些情况后，网络和宿主机层面的可用时间不低于这个比例"。

## SLA 的关键不是数字，而是赔付条款

同样是宣传 uptime，有没有 SLA（服务水平协议）差别很大。没有 SLA 的 "uptime guarantee" 基本只是一句口号；有 SLA 的，写明了赔付方式和申请流程。

搬瓦工目前只有一条产品线提供正式 SLA：**E-Commerce SLA 系列**，承诺每月 uptime 不低于 **99.99%**，且目前仅洛杉矶 USCA_5 机房支持。赔付按停机时长阶梯发放，以延长服务期限的形式补偿：

| 当月停机时长 | 赔付（延长服务时间） |
| --- | --- |
| 超过 4 分 32 秒、不足 10 分钟 | 12 小时 |
| 10–59 分钟 | 72 小时 |
| 60–119 分钟 | 120 小时 |
| 120–239 分钟 | 240 小时 |
| 240–419 分钟 | 360 小时 |
| 420 分钟及以上 | 一个月服务期 |

几个细节值得注意：赔付必须在停机发生那个月结束后的 **90 天内**提交，而且要明确写 "SLA Service Credit"，普通的故障工单不算申请；赔付上限是当月一个月的服务时长；赔付只延长受影响那台 VPS 的服务期，不能折现。换句话说，SLA 是个补偿机制，不是"宕机就退钱"。

相比之下，搬瓦工其余套餐（包括最便宜的 Basic KVM 系列）只在官网页面标注通用的 99.9% uptime guarantee，没有这套阶梯赔付。这就是两者最实质的区别。

## 看价格之前，先分清搬瓦工的四条产品线

搬瓦工的套餐不是按"入门/进阶"划分的，而是按网络质量分线，uptime 相关的承诺也跟着产品线走：

- **Basic KVM**：标准线路，多机房可选（洛杉矶、纽约、弗里蒙特、阿姆斯特丹等），可在机房之间免费迁移不丢数据，是最便宜的入门线
- **E-Commerce（CN2 GIA-E）**：针对中国方向优化过的优质线路，机房池覆盖洛杉矶、大阪等 16 个位置，可免费互迁
- **E-Commerce SLA**：E-Commerce 的高可靠版本，限定洛杉矶 USCA_5 机房，带上面说的 99.99% SLA、双冗余网络设计（双边缘路由器、双供电、双光纤路径），并支持每两周免费换一次 IP
- **Ultra**：香港、东京、大阪、新加坡的顶级连通性方案，延迟最低，价格也最高

四条线用的都是 KVM 虚拟化，自带自研的 KiwiVM 面板（开关机、重装系统、快照、机房迁移、API 都在里面），系统支持 AlmaLinux、Debian、Ubuntu 等。注意这是**自我管理（self-managed）**服务——装环境、配防火墙、处理故障排查都靠自己，这也是它能把价格压低的原因之一。

## 全套餐对比：目前在售的全部方案与价格

下面表格整理自搬瓦工官方订单页当前展示的配置，币种为美元。同一套餐通常提供月付、季付、半年付、年付多档，表中取的是最短计费周期的入门价。

**Basic KVM（标准线路，多机房，99.9% uptime guarantee，无 SLA）**

| 套餐 | CPU | 内存 | SSD | 月流量 | 端口 | 入门价 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 20G KVM | 2 核 | 1 GB | 20 GB | 1 TB | 1 Gbps | $49.99/年 | [ 查看这款年付方案](https://bit.ly/BandwagonHost) |
| 40G KVM | 3 核 | 2 GB | 40 GB | 2 TB | 1 Gbps | $52.99/半年 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 80G KVM | 4 核 | 4 GB | 80 GB | 3 TB | 2.5 Gbps | $19.99/月 | [ 查看月付价格](https://bit.ly/BandwagonHost) |
| 160G KVM | 5 核 | 8 GB | 160 GB | 4 TB | 2.5 Gbps | $39.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 320G KVM | 6 核 | 16 GB | 320 GB | 5 TB | 5 Gbps | $79.99/月 | [ 查看配置详情](https://bit.ly/BandwagonHost) |
| 480G KVM | 7 核 | 24 GB | 480 GB | 6 TB | 5 Gbps | $119.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |

**E-Commerce / CN2 GIA-E（优质线路，16 机房可免费互迁，99.9% uptime guarantee）**

| 套餐 | CPU | 内存 | SSD | 月流量 | 入门价 | 购买 |
| --- | --- | --- | --- | --- | --- | --- |
| 20G GIA-E | 2 核 | 1 GB | 20 GB | 1 TB | $49.99/季 | [ 查看这款方案](https://bit.ly/BandwagonHost) |
| 40G GIA-E | 3 核 | 2 GB | 40 GB | 2 TB | $89.99/季 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 80G GIA-E | 4 核 | 4 GB | 80 GB | 3 TB | $56.99/月 | [ 查看月付价格](https://bit.ly/BandwagonHost) |
| 160G GIA-E | 6 核 | 8 GB | 160 GB | 5 TB | $86.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 320G GIA-E | 8 核 | 16 GB | 320 GB | 8 TB | $159.99/月 | [ 查看配置详情](https://bit.ly/BandwagonHost) |
| 640G GIA-E | 10 核 | 32 GB | 640 GB | 10 TB | $289.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 1.28T GIA-E（12 TB 流量） | 12 核 | 64 GB | 1.28 TB | 12 TB | $549.99/月 | [ 查看这款方案](https://bit.ly/BandwagonHost) |
| 1.28T GIA-E（15 TB 流量） | 12 核 | 64 GB | 1.28 TB | 15 TB | $679.00/月 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 1.28T GIA-E（20 TB 流量） | 12 核 | 64 GB | 1.28 TB | 20 TB | $899.00/月 | [ 查看配置详情](https://bit.ly/BandwagonHost) |

**E-Commerce SLA（洛杉矶 USCA_5 专属，99.99% SLA 正式生效，双冗余网络）**

| 套餐 | CPU | 内存 | SSD | 月流量 | 入门价 | 购买 |
| --- | --- | --- | --- | --- | --- | --- |
| 20G SLA | 2 核 | 1 GB | 20 GB | 1 TB | $65.89/季 | [ 查看 SLA 方案](https://bit.ly/BandwagonHost) |
| 40G SLA | 3 核 | 2 GB | 40 GB | 2 TB | $116.99/季 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 80G SLA | 4 核 | 4 GB | 80 GB | 3 TB | $69.99/月 | [ 查看月付价格](https://bit.ly/BandwagonHost) |
| 160G SLA | 6 核 | 8 GB | 160 GB | 5 TB | $109.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 320G SLA | 8 核 | 16 GB | 320 GB | 8 TB | $199.99/月 | [ 查看配置详情](https://bit.ly/BandwagonHost) |
| 640G SLA | 10 核 | 32 GB | 640 GB | 10 TB | $369.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 1.28T SLA（12 TB 流量） | 12 核 | 64 GB | 1.28 TB | 12 TB | $699.99/月 | [ 查看这款方案](https://bit.ly/BandwagonHost) |
| 1.28T SLA（15 TB 流量） | 12 核 | 64 GB | 1.28 TB | 15 TB | $879.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 1.28T SLA（20 TB 流量） | 12 核 | 64 GB | 1.28 TB | 20 TB | $1,159.99/月 | [ 查看配置详情](https://bit.ly/BandwagonHost) |

**Ultra（香港/东京/大阪/新加坡，顶级连通性，99.9% uptime guarantee）**

| 位置 | 套餐 | CPU | 内存 | SSD | 月流量 | 入门价 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 香港 / 东京 | 40G Ultra | 2 核 | 2 GB | 40 GB | 500 GB | $89.99/月 | [ 查看 Ultra 方案](https://bit.ly/BandwagonHost) |
| 香港 / 东京 | 80G Ultra | 4 核 | 4 GB | 80 GB | 1 TB | $155.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 香港 / 东京 | 160G Ultra | 6 核 | 8 GB | 160 GB | 2 TB | $299.99/月 | [ 查看配置详情](https://bit.ly/BandwagonHost) |
| 香港 / 东京 | 320G Ultra | 8 核 | 16 GB | 320 GB | 4 TB | $589.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 香港 / 东京 | 640G Ultra | 10 核 | 32 GB | 640 GB | 6 TB | $989.99/月 | [ 查看这款方案](https://bit.ly/BandwagonHost) |
| 香港 / 东京 | 1.28T Ultra | 12 核 | 64 GB | 1.28 TB | 8 TB | $1,889.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 大阪 / 新加坡 | 40G Ultra | 2 核 | 2 GB | 40 GB | 500 GB | $49.99/月 | [ 查看 Ultra 方案](https://bit.ly/BandwagonHost) |
| 大阪 / 新加坡 | 80G Ultra | 4 核 | 4 GB | 80 GB | 1 TB | $86.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 大阪 / 新加坡 | 160G Ultra | 6 核 | 8 GB | 160 GB | 2 TB | $165.99/月 | [ 查看配置详情](https://bit.ly/BandwagonHost) |
| 大阪 / 新加坡 | 320G Ultra | 8 核 | 16 GB | 320 GB | 4 TB | $329.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |
| 大阪 / 新加坡 | 640G Ultra | 10 核 | 32 GB | 640 GB | 6 TB | $549.99/月 | [ 查看这款方案](https://bit.ly/BandwagonHost) |
| 大阪 / 新加坡 | 1.28T Ultra | 12 核 | 64 GB | 1.28 TB | 8 TB | $1,059.99/月 | [ 前往购买](https://bit.ly/BandwagonHost) |

补充两个购买前要知道的事：第一，新订单适用 **30 天退款政策**，条款细节以官方 ToS 为准，不确定的话下单前可以先读一遍退款说明；第二，同一套餐不同计费周期价格差不小，比如 80G KVM 月付 $19.99，年付折算下来每月更便宜，长期用优先选长周期。

## 为更高的 uptime 多花钱，到底值不值

把 SLA 系列和同配置的普通 E-Commerce 系列放在一起看，溢价一目了然：80G 那一档，E-Commerce 月付 $56.99，E-Commerce SLA 月付 $69.99，每月多 $13；160G 档从 $86.99 涨到 $109.99，每月多 $23。换来的是 99.99% SLA、双冗余网络设计和每两周一次的免费 IP 更换。

这个差价划不划算，取决于业务性质。挂个个人项目或者测试环境，普通 E-Commerce 的 99.9% 基本够用，一年多出来的那几个小时停机额度大概率碰不上。但如果是收订单的电商站，每次停机都是真金白银的损失，为 SLA 每月多付十几二十美元，相当于买了一份有明确赔付流程的保险。Ultra 系列则是另一回事——它的溢价主要买的是港日机房的低延迟连通性，uptime 并不是它的主要卖点。

## 怎么核对一台 VPS 的真实 uptime

不管买哪家，宣传数字都只是起点，实际表现要靠自己的数据验证：

1. **上线当天就装监控**。UptimeRobot 之类的免费监控足够，从外部每分钟探测一次 TCP 或 HTTP，比依赖服务商自报的数据客观得多。
2. **对照服务商的状态页**。搬瓦工在 bwhstatus.com 发布维护和故障公告，遇到服务中断可以去核对是否属于计划内维护——这直接影响能不能申请 SLA 赔付。
3. **留好日志再提赔付**。如果用的是 SLA 套餐且某月停机超过了 4 分 32 秒，把监控截图、traceroute 输出这些证据收集好，在账单月结束后 90 天内通过支持渠道明确申请 "SLA Service Credit"。超过 90 天视为自动放弃。

一句话总结：看到 "99.9% uptime" 先换算成分钟数，再看有没有 SLA 赔付条款兜底。搬瓦工的 Basic KVM 用 $49.99/年的价格满足预算敏感的场景，E-Commerce SLA 用每月十几美元的溢价把 uptime 承诺升级成有赔付机制的 99.99%——需求在哪一档，钱就花在哪一档。

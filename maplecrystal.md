# READ 外链聚合系统 (READ Link Aggregator)

READ 外链聚合系统是一个面向技术文档、教程资源与文章外链的集中式检索与管理平台。项目定位于解决个人开发者与小型团队在查阅分散于不同域名站点下的技术文章、运维手册与开发笔记时面临的检索效率低下、链接管理混乱与内容失联问题。通过将大量来自不同内容源的文章链接纳入统一的索引体系，本系统提供结构化的分类存储、快速检索入口以及稳定的资源访问路由。

目标用户为后端开发工程师、DevOps 运维人员、技术写作人员以及技术团队的知识管理者。系统本身不存储具体文章内容，而是提供可靠的外链元数据管理与跳转服务，确保资源来源可追溯、访问路径可控制。本仓库包含完整的资源索引配置、分类标签定义以及前端检索界面原型，可作为自建技术知识库的外链管理底座。

## 功能概览

多源异构链接统一入库 支持从多个独立域名下的文章站点批量导入链接，每个链接携带来源标识、入库时间与原始分类标签。

层级化分类与标签系统 每个外链可归属至技术领域、语言栈、框架版本或文档类型等自定义分类，支持多标签交叉筛选。

全文元数据检索 基于链接标题、来源域名、摘要描述与标签组合进行关键字检索，支持模糊匹配与精确过滤。

链接可用性健康检查 定时对已入库链接发起 HEAD 请求，检测响应状态码，自动标记失效或重定向链接，输出巡检报告。

导入导出与批量操作 支持 CSV 与 JSON 格式的链接批量导入导出，便于与其他知识管理工具（如 Notion、Obsidian）进行数据交换。

访问统计与热度排序 记录每个外链的点击次数与最近访问时间，支持按热度、更新时间或入库时间排序输出列表。

响应式管理面板 提供基于 Web 的简易管理界面，适配桌面与移动设备，用于链接增删改查与分类维护。

## 应用场景

技术团队内部知识库外链管理 团队可将日常开发中参考的官方文档、博客文章、故障排查实录等分散链接统一录入系统，通过分类与标签快速定位，避免重复查找与链接丢失。

运维故障案例归档与检索 运维人员可将历史事故处理报告、监控告警处理步骤、回滚操作记录等外部链接归入系统，在后续出现类似问题时迅速检索历史处理方案。

技术写作资料收集与引用管理 技术写作者在撰写教程或技术书籍时，可通过本系统集中管理参考引用的网络资源，确保引用链接的可追溯性与版本一致性。

开源项目文档依赖外链托管 开源项目维护者可将项目依赖的外部规范、API 参考、协议说明等链接统一托管于此，降低 README 中直接裸露大量外链带来的维护负担与断链风险。

## 快速开始

以下步骤帮助您在本地环境中快速启动 READ 外链聚合系统的开发或试用实例。

```bash
# 克隆仓库到本地
git clone https://github.com/read-link/read-link-aggregator.git
cd read-link-aggregator

# 安装依赖（基于 Node.js 22 LTS 与 pnpm）
pnpm install

# 复制环境变量模板并填入必要配置
cp .env.example .env

# 执行数据库迁移与初始数据导入
pnpm run migrate
pnpm run seed

# 启动开发服务器（默认监听 3000 端口）
pnpm run dev
```

启动成功后，访问 `http://localhost:3000` 即可进入管理面板。首次登录默认管理员账号为 `admin@read.local`，密码为 `read-admin-2026`，请在首次登录后立即修改。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 22.12.0 或更高 LTS 版本 | 运行时环境，推荐使用 nvm 管理 |
| pnpm | 9.0.0 或更高 | 包管理器，用于依赖安装与工作空间管理 |
| PostgreSQL | 15.0 或更高 | 主数据库，存储链接元数据与索引 |
| Redis | 7.0 或更高 | 缓存会话与访问计数，可选但推荐生产环境部署 |
| Nginx | 1.24 或更高 | 生产环境反向代理与静态资源服务，开发环境可省略 |
| Docker / Docker Compose | 最新稳定版 | 用于一键启动全部依赖服务，推荐开发与测试环境使用 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | `/docs/user-guide/quick-start.md` | 如何导入第一批链接、如何创建分类、如何进行检索与筛选 |
| 运维手册 | `/docs/ops/deployment.md` | 生产环境部署架构、容器化配置、反向代理设置与备份策略 |
| API 参考 | `/docs/api/endpoints.md` | 所有 RESTful 接口的请求路径、参数说明、响应示例与错误码 |
| 开发者指南 | `/docs/developer/contribution.md` | 代码规范、提交规范、测试流程与调试方法 |

## 资源列表

- https://www.read.fuvxie.cn/Article/1478.shtml
- https://www.read.nwbbyt.cn/Article/8480106.shtml
- https://www.read.jnjpgf.cn/Article/7692.shtml
- https://www.read.hcbezg.cn/Article/241428.shtml
- https://www.read.nzfnve.cn/Article/594147.shtml
- https://www.read.cvsifc.cn/Article/90385.shtml
- https://www.read.nwbbyt.cn/Article/407298.shtml
- https://www.read.fuvxie.cn/Article/5968.shtml
- https://www.read.hcbezg.cn/Article/77423.shtml
- https://www.read.nzfnve.cn/Article/0819590.shtml
- https://www.read.fuvxie.cn/Article/45705.shtml
- https://www.read.jnjpgf.cn/Article/00899.shtml
- https://www.read.hcbezg.cn/Article/5699.shtml
- https://www.read.hcbezg.cn/Article/8679444.shtml
- https://www.read.fuvxie.cn/Article/25055.shtml
- https://www.read.hcbezg.cn/Article/547589.shtml
- https://www.read.jnjpgf.cn/Article/8481524.shtml
- https://www.read.jnjpgf.cn/Article/3049.shtml
- https://www.read.nzfnve.cn/Article/816680.shtml
- https://www.read.puhvjy.cn/Article/15781.shtml
- https://www.read.puhvjy.cn/Article/05769.shtml
- https://www.read.puhvjy.cn/Article/1829245.shtml
- https://www.read.nzfnve.cn/Article/989219.shtml
- https://www.read.puhvjy.cn/Article/8817628.shtml
- https://www.read.cvsifc.cn/Article/14615.shtml
- https://www.read.jnjpgf.cn/Article/82649.shtml
- https://www.read.jnjpgf.cn/Article/7102835.shtml
- https://www.read.puhvjy.cn/Article/0760394.shtml
- https://www.read.puhvjy.cn/Article/6784.shtml
- https://www.read.puhvjy.cn/Article/44786.shtml
- https://www.read.cmcvrr.cn/Article/5746011.shtml
- https://www.read.jnjpgf.cn/Article/498410.shtml
- https://www.read.hcbezg.cn/Article/8767794.shtml
- https://www.read.hcbezg.cn/Article/7048.shtml
- https://www.read.fuvxie.cn/Article/4970996.shtml
- https://www.read.cvsifc.cn/Article/48393.shtml
- https://www.read.cvsifc.cn/Article/779991.shtml
- https://www.read.cvsifc.cn/Article/6546.shtml
- https://www.read.puhvjy.cn/Article/3369.shtml
- https://www.read.nzfnve.cn/Article/1640.shtml
- https://www.read.cvsifc.cn/Article/0504.shtml
- https://www.read.nwbbyt.cn/Article/64987.shtml
- https://www.read.puhvjy.cn/Article/650209.shtml
- https://www.read.nzfnve.cn/Article/25010.shtml
- https://www.read.fuvxie.cn/Article/57884.shtml
- https://www.read.jnjpgf.cn/Article/960389.shtml
- https://www.read.puhvjy.cn/Article/5362911.shtml
- https://www.read.cmcvrr.cn/Article/1912541.shtml
- https://www.read.cmcvrr.cn/Article/27280.shtml
- https://www.read.nwbbyt.cn/Article/00635.shtml
- https://www.read.jnjpgf.cn/Article/837184.shtml
- https://www.read.cvsifc.cn/Article/0206111.shtml
- https://www.read.cvsifc.cn/Article/064954.shtml
- https://www.read.cvsifc.cn/Article/31960.shtml
- https://www.read.cvsifc.cn/Article/7803028.shtml
- https://www.read.cvsifc.cn/Article/85701.shtml
- https://www.read.cmcvrr.cn/Article/875146.shtml
- https://www.read.nzfnve.cn/Article/22613.shtml
- https://www.read.nzfnve.cn/Article/2365959.shtml
- https://www.read.jnjpgf.cn/Article/8665.shtml
- https://www.read.nzfnve.cn/Article/301038.shtml
- https://www.read.hcbezg.cn/Article/5053516.shtml
- https://www.read.cvsifc.cn/Article/82915.shtml
- https://www.read.fuvxie.cn/Article/03719.shtml
- https://www.read.nwbbyt.cn/Article/535092.shtml
- https://www.read.nzfnve.cn/Article/95012.shtml
- https://www.read.nwbbyt.cn/Article/719894.shtml
- https://www.read.jnjpgf.cn/Article/07684.shtml
- https://www.read.nzfnve.cn/Article/625330.shtml
- https://www.read.nzfnve.cn/Article/1070.shtml
- https://www.read.fuvxie.cn/Article/07000.shtml
- https://www.read.hcbezg.cn/Article/534810.shtml
- https://www.read.puhvjy.cn/Article/68361.shtml
- https://www.read.jnjpgf.cn/Article/300789.shtml
- https://www.read.cvsifc.cn/Article/9545.shtml
- https://www.read.nzfnve.cn/Article/402321.shtml
- https://www.read.cmcvrr.cn/Article/7011181.shtml
- https://www.read.cmcvrr.cn/Article/113771.shtml
- https://www.read.jnjpgf.cn/Article/2441620.shtml
- https://www.read.hcbezg.cn/Article/59363.shtml
- https://www.read.cmcvrr.cn/Article/4430517.shtml
- https://www.read.cvsifc.cn/Article/731795.shtml
- https://www.read.nwbbyt.cn/Article/9551225.shtml
- https://www.read.hcbezg.cn/Article/81570.shtml
- https://www.read.nzfnve.cn/Article/703758.shtml
- https://www.read.cvsifc.cn/Article/0101.shtml
- https://www.read.jnjpgf.cn/Article/5403.shtml
- https://www.read.cmcvrr.cn/Article/707308.shtml
- https://www.read.nwbbyt.cn/Article/342166.shtml
- https://www.read.puhvjy.cn/Article/3401746.shtml
- https://www.read.nwbbyt.cn/Article/43875.shtml
- https://www.read.nzfnve.cn/Article/842487.shtml
- https://www.read.jnjpgf.cn/Article/667114.shtml
- https://www.read.cmcvrr.cn/Article/3733.shtml
- https://www.read.nzfnve.cn/Article/9690.shtml
- https://www.read.cmcvrr.cn/Article/9177214.shtml
- https://www.read.nwbbyt.cn/Article/7617409.shtml
- https://www.read.cmcvrr.cn/Article/3403987.shtml
- https://www.read.nzfnve.cn/Article/62368.shtml
- https://www.read.cvsifc.cn/Article/478066.shtml
- https://www.read.jnjpgf.cn/Article/3199586.shtml
- https://www.read.fuvxie.cn/Article/4709.shtml
- https://www.read.fuvxie.cn/Article/066793.shtml
- https://www.read.cmcvrr.cn/Article/45183.shtml
- https://www.read.cmcvrr.cn/Article/3653124.shtml
- https://www.read.fuvxie.cn/Article/6044784.shtml
- https://www.read.nzfnve.cn/Article/6095.shtml
- https://www.read.nwbbyt.cn/Article/19405.shtml
- https://www.read.nzfnve.cn/Article/1972127.shtml
- https://www.read.cmcvrr.cn/Article/09719.shtml
- https://www.read.nwbbyt.cn/Article/320836.shtml
- https://www.read.nwbbyt.cn/Article/680560.shtml
- https://www.read.jnjpgf.cn/Article/8298215.shtml
- https://www.read.nzfnve.cn/Article/8808.shtml
- https://www.read.cmcvrr.cn/Article/2239.shtml
- https://www.read.fuvxie.cn/Article/4845.shtml
- https://www.read.nwbbyt.cn/Article/57610.shtml
- https://www.read.hcbezg.cn/Article/690435.shtml
- https://www.read.hcbezg.cn/Article/2511.shtml
- https://www.read.puhvjy.cn/Article/901394.shtml
- https://www.read.nwbbyt.cn/Article/1248.shtml
- https://www.read.cvsifc.cn/Article/433195.shtml
- https://www.read.jnjpgf.cn/Article/1125.shtml
- https://www.read.jnjpgf.cn/Article/61358.shtml
- https://www.read.nzfnve.cn/Article/1639009.shtml
- https://www.read.cvsifc.cn/Article/699800.shtml
- https://www.read.nwbbyt.cn/Article/45021.shtml
- https://www.read.nwbbyt.cn/Article/3978130.shtml
- https://www.read.nzfnve.cn/Article/9856390.shtml
- https://www.read.cvsifc.cn/Article/1028.shtml
- https://www.read.fuvxie.cn/Article/6540809.shtml
- https://www.read.cmcvrr.cn/Article/6950.shtml
- https://www.read.jnjpgf.cn/Article/9767613.shtml
- https://www.read.nwbbyt.cn/Article/6323.shtml
- https://www.read.jnjpgf.cn/Article/8001041.shtml
- https://www.read.fuvxie.cn/Article/7079.shtml
- https://www.read.cmcvrr.cn/Article/6807872.shtml
- https://www.read.hcbezg.cn/Article/9641483.shtml
- https://www.read.cvsifc.cn/Article/94848.shtml
- https://www.read.hcbezg.cn/Article/39203.shtml
- https://www.read.hcbezg.cn/Article/3555.shtml
- https://www.read.nzfnve.cn/Article/8572743.shtml
- https://www.read.nzfnve.cn/Article/1061.shtml
- https://www.read.nzfnve.cn/Article/0103.shtml
- https://www.read.nzfnve.cn/Article/4461240.shtml
- https://www.read.cmcvrr.cn/Article/217315.shtml
- https://www.read.puhvjy.cn/Article/2585637.shtml
- https://www.read.nzfnve.cn/Article/3431.shtml
- https://www.read.fuvxie.cn/Article/1503.shtml
- https://www.read.nwbbyt.cn/Article/63116.shtml
- https://www.read.cmcvrr.cn/Article/110870.shtml
- https://www.read.nwbbyt.cn/Article/342020.shtml
- https://www.read.jnjpgf.cn/Article/0965880.shtml
- https://www.read.fuvxie.cn/Article/511339.shtml
- https://www.read.nzfnve.cn/Article/13688.shtml
- https://www.read.puhvjy.cn/Article/0811.shtml
- https://www.read.hcbezg.cn/Article/591213.shtml
- https://www.read.fuvxie.cn/Article/8848.shtml
- https://www.read.nwbbyt.cn/Article/919033.shtml
- https://www.read.nwbbyt.cn/Article/7404.shtml
- https://www.read.cvsifc.cn/Article/2423.shtml
- https://www.read.cvsifc.cn/Article/1778993.shtml
- https://www.read.hcbezg.cn/Article/1972.shtml
- https://www.read.cvsifc.cn/Article/47835.shtml
- https://www.read.hcbezg.cn/Article/2871.shtml
- https://www.read.nzfnve.cn/Article/69137.shtml
- https://www.read.fuvxie.cn/Article/836725.shtml
- https://www.read.puhvjy.cn/Article/2567919.shtml
- https://www.read.fuvxie.cn/Article/16477.shtml
- https://www.read.fuvxie.cn/Article/01940.shtml
- https://www.read.jnjpgf.cn/Article/7430032.shtml
- https://www.read.jnjpgf.cn/Article/182006.shtml
- https://www.read.hcbezg.cn/Article/0611.shtml
- https://www.read.cvsifc.cn/Article/9455.shtml
- https://www.read.jnjpgf.cn/Article/650412.shtml
- https://www.read.fuvxie.cn/Article/7877.shtml
- https://www.read.fuvxie.cn/Article/4242123.shtml
- https://www.read.jnjpgf.cn/Article/9793859.shtml
- https://www.read.nzfnve.cn/Article/00555.shtml
- https://www.read.cvsifc.cn/Article/33275.shtml
- https://www.read.cvsifc.cn/Article/778583.shtml
- https://www.read.cmcvrr.cn/Article/23450.shtml
- https://www.read.puhvjy.cn/Article/0224.shtml
- https://www.read.hcbezg.cn/Article/8962504.shtml
- https://www.read.fuvxie.cn/Article/0188804.shtml
- https://www.read.puhvjy.cn/Article/363196.shtml
- https://www.read.puhvjy.cn/Article/16580.shtml
- https://www.read.fuvxie.cn/Article/573614.shtml
- https://www.read.hcbezg.cn/Article/966512.shtml
- https://www.read.cmcvrr.cn/Article/170615.shtml
- https://www.read.cmcvrr.cn/Article/4130.shtml
- https://www.read.hcbezg.cn/Article/27691.shtml
- https://www.read.nwbbyt.cn/Article/2475470.shtml
- https://www.read.jnjpgf.cn/Article/7598.shtml
- https://www.read.fuvxie.cn/Article/408069.shtml
- https://www.read.fuvxie.cn/Article/6804.shtml
- https://www.read.jnjpgf.cn/Article/29560.shtml
- https://www.read.fuvxie.cn/Article/61452.shtml
- https://www.read.jnjpgf.cn/Article/180842.shtml
- https://www.read.puhvjy.cn/Article/5081.shtml
- https://www.read.cmcvrr.cn/Article/8746583.shtml
- https://www.read.jnjpgf.cn/Article/05796.shtml
- https://www.read.nwbbyt.cn/Article/662610.shtml
- https://www.read.cmcvrr.cn/Article/76309.shtml
- https://www.read.fuvxie.cn/Article/9602.shtml
- https://www.read.puhvjy.cn/Article/4137.shtml
- https://www.read.cmcvrr.cn/Article/5304.shtml
- https://www.read.nzfnve.cn/Article/318814.shtml
- https://www.read.hcbezg.cn/Article/56728.shtml
- https://www.read.cvsifc.cn/Article/8260780.shtml
- https://www.read.puhvjy.cn/Article/689231.shtml
- https://www.read.cmcvrr.cn/Article/999276.shtml
- https://www.read.cmcvrr.cn/Article/02535.shtml
- https://www.read.cmcvrr.cn/Article/18604.shtml
- https://www.read.nzfnve.cn/Article/07935.shtml
- https://www.read.nwbbyt.cn/Article/7818312.shtml
- https://www.read.nzfnve.cn/Article/0478933.shtml
- https://www.read.cvsifc.cn/Article/1048598.shtml
- https://www.read.puhvjy.cn/Article/0571.shtml
- https://www.read.cvsifc.cn/Article/966788.shtml
- https://www.read.puhvjy.cn/Article/64087.shtml
- https://www.read.hcbezg.cn/Article/934501.shtml
- https://www.read.jnjpgf.cn/Article/1938.shtml
- https://www.read.puhvjy.cn/Article/72254.shtml
- https://www.read.nzfnve.cn/Article/95363.shtml
- https://www.read.nwbbyt.cn/Article/18143.shtml
- https://www.read.nwbbyt.cn/Article/638527.shtml
- https://www.read.nzfnve.cn/Article/185084.shtml
- https://www.read.nzfnve.cn/Article/6539284.shtml
- https://www.read.nwbbyt.cn/Article/3430997.shtml
- https://www.read.fuvxie.cn/Article/26597.shtml
- https://www.read.nzfnve.cn/Article/0997137.shtml
- https://www.read.fuvxie.cn/Article/7250463.shtml
- https://www.read.cmcvrr.cn/Article/8972.shtml
- https://www.read.nzfnve.cn/Article/78816.shtml
- https://www.read.jnjpgf.cn/Article/7747313.shtml
- https://www.read.nzfnve.cn/Article/4551.shtml
- https://www.read.puhvjy.cn/Article/192526.shtml
- https://www.read.puhvjy.cn/Article/13703.shtml
- https://www.read.jnjpgf.cn/Article/199259.shtml
- https://www.read.nwbbyt.cn/Article/6363314.shtml
- https://www.read.hcbezg.cn/Article/90665.shtml
- https://www.read.cvsifc.cn/Article/6849.shtml
- https://www.read.puhvjy.cn/Article/11961.shtml
- https://www.read.nzfnve.cn/Article/41765.shtml
- https://www.read.cmcvrr.cn/Article/21942.shtml
- https://www.read.nwbbyt.cn/Article/4788.shtml
- https://www.read.nwbbyt.cn/Article/816839.shtml
- https://www.read.nzfnve.cn/Article/2999.shtml
- https://www.read.hcbezg.cn/Article/58466.shtml

## 项目结构

```
read-link-aggregator/
├── apps/
│   ├── web/                         # 前端管理面板 (Next.js 15)
│   │   ├── app/                     # 页面路由与布局
│   │   ├── components/              # 可复用 UI 组件 (按钮、表格、筛选器)
│   │   └── lib/                     # 前端数据请求与状态管理
│   └── api/                         # 后端服务 (Fastify)
│       ├── routes/                  # REST 路由定义 (链接、分类、标签、健康检查)
│       ├── controllers/             # 业务逻辑控制器
│       ├── services/                # 数据库服务与缓存服务
│       └── workers/                 # 后台任务 (链接健康检查、访问统计)
├── packages/
│   ├── db/                          # 数据库模型与迁移 (Prisma)
│   │   ├── schema.prisma            # 数据表定义 (links, categories, tags, clicks)
│   │   └── migrations/              # 迁移历史文件
│   ├── config/                      # 共享配置 (环境变量解析、日志级别)
│   └── types/                       # TypeScript 类型定义与接口契约
├── scripts/
│   ├── seed.ts                      # 初始数据填充 (管理员账号、默认分类、示例链接)
│   └── health-check.ts             # 手动触发全量链接健康检查脚本
├── docker-compose.yml               # 本地开发全栈依赖 (PostgreSQL, Redis, Adminer)
├── Dockerfile                       # 生产环境多阶段构建文件
├── .env.example                     # 环境变量配置模板
├── pnpm-workspace.yaml              # pnpm 工作空间定义
├── package.json                     # 根目录依赖与脚本定义
└── README.md                        # 本文档
```

## 贡献指南

我们欢迎并鼓励社区提交各类贡献，包括但不限于代码修复、文档改进、功能建议与链接资源扩充。请遵循以下步骤参与贡献。

首先，在 GitHub 仓库页面点击 Fork 按钮，将本仓库复制到您的个人账户下，随后克隆您的 Fork 版本到本地开发环境。接着，新建一个具备描述性的分支名称，例如 `feat/add-batch-import` 或 `fix/search-filter-error`，在该分支上完成您的修改。

其次，确保所有代码变更均通过完整的单元测试与端到端测试，并且遵循仓库根目录下 `.eslintrc.js` 与 `.prettierrc` 定义的代码风格。提交信息请采用 Conventional Commits 规范，格式为 `<type>(<scope>): <subject>`，例如 `feat(api): add batch delete endpoint for links`。

再次，将您的分支推送至个人 Fork 仓库，并通过 GitHub 界面发起 Pull Request 至本仓库的 `main` 分支。请在 PR 描述中清晰说明变更内容、关联的 Issue 编号以及测试覆盖情况。维护者将在 3 个工作日内进行审核，必要时会提出修改意见。

最后，若您希望贡献新的外链资源，请通过管理面板的导入功能提交，或直接修改 `scripts/seed.ts` 中的示例数据并附上来源说明。我们不接受包含恶意内容、侵权材料或违反中国法律法规的外链。

## 常见问题

系统启动时提示数据库连接失败，如何排查？

请依次检查 `.env` 文件中的 `DATABASE_URL` 配置是否正确，确认 PostgreSQL 服务是否已启动。若使用 Docker Compose，请执行 `docker-compose ps` 查看容器状态。本地开发可执行 `pnpm run db:start` 一键启动依赖容器。若仍无法连接，尝试将 `localhost` 替换为 `host.docker.internal`（Docker for Mac/Windows）或容器名称（Linux）。

如何批量导入已有的外链列表？

系统支持 CSV 与 JSON 两种格式的批量导入。请在管理面板的「导入」页面下载模板文件，按模板填写链接 URL、标题、分类名称与标签列表，然后上传文件。导入过程为异步任务，可在「任务中心」查看进度与错误日志。对于超过 1000 条记录的导入，建议通过命令行脚本 `pnpm run import:json --file ./data/links.json` 执行。

外链健康检查报告显示大量链接不可达，应如何处理？

健康检查默认超时时间为 5 秒，重试 2 次。若链接持续不可达，首先手动访问该链接确认是否为临时性服务中断。若确认资源已永久迁移，请更新链接记录中的 URL 字段；若资源已彻底移除，建议将该链接标记为「已失效」并保留记录以供追溯，避免在检索结果中误展示。系统不会自动删除失效链接，以维持引用记录的完整性。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:20

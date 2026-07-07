# DocLink Hub

DocLink Hub 是一个面向技术文档聚合与外部资源引用的轻量化链接管理工具，专为需要统一管理大量外部文档链接（.doc / .pdf / 技术规范等）的开发团队、技术运营人员及知识库维护者设计。该项目不提供文件存储服务，而是基于结构化 URL 清单构建可检索、可分类、可版本追踪的外部资源索引系统，适用于内部知识中台、项目文档库或技术外链汇总站点。

DocLink Hub 的核心定位是“链接的链接”，即以极低维护成本将分散在多个业务域（如 h5.mobile.* 子域名）下的文档资源整合为统一的访问入口，并通过自动化脚本校验链接有效性、生成资源状态看板，解决人工维护外链易失效、难追溯的痛点。

## 功能概览

**批量链接导入与解析** 支持从 CSV、JSON 或纯文本列表批量导入 URL，自动识别域名、路径及文件扩展名，生成结构化索引。

**资源状态健康检查** 定时发起 HEAD 请求验证链接可达性，标记失效链接并生成报表，支持邮件或 Webhook 告警。

**多维度分类与标签系统** 允许为每个链接附加业务标签（如“技术规范”“设计文档”“运维手册”）、所属项目、维护人及过期时间。

**全文检索与过滤器** 基于链接路径、文件名、标签及描述字段提供轻量级全文搜索，支持按域名、文件类型、状态等维度过滤。

**访问统计与热度分析** 记录每个链接的点击次数、最后访问时间，提供热门资源排行榜及冷门资源清理建议。

**导出与集成能力** 支持将索引数据导出为 Markdown 表格、JSON API 或静态 HTML 页面，便于嵌入现有文档站点（如 VuePress、Docusaurus）。

**权限与审核流程** 内置简单的角色控制（管理员/编辑/只读），所有新增或修改链接需经过审核日志记录，满足内部合规要求。

## 应用场景

**企业内部知识库外链治理** 技术团队可将分散在多个业务子域名下的历史文档链接（如产品需求、接口定义、测试报告）统一录入 DocLink Hub，定期自动检测失效链接，避免项目成员依赖已下线的文档地址。

**开源项目文档站的外链管理** 开源项目维护者可使用 DocLink Hub 管理 README、官网及技术白皮书中引用的外部资源链接，在版本发布前批量校验所有引用 URL，确保用户能顺利获取依赖资源。

**技术培训与课程资料索引** 培训机构或技术社区运营者可将每期课程涉及的参考文档、实验手册、视频字幕文件链接汇总为专题索引，学员通过单一入口访问所有学习材料，降低查找成本。

**合规审计与资产盘点** 企业合规部门可利用 DocLink Hub 的标签和过期时间功能，跟踪各业务系统引用的外部文档是否在有效期内，生成年度外链资产报告，应对内外部审计要求。

## 快速开始

以下步骤指导您在本地环境快速启动 DocLink Hub 服务。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/doclink-hub.git
cd doclink-hub

# 安装依赖（基于 Node.js 18+ 与 pnpm）
pnpm install

# 复制环境变量模板并配置数据库连接
cp .env.example .env
# 编辑 .env 文件，设置 DATABASE_URL 等必要参数

# 初始化数据库表结构
pnpm db:push

# 导入示例链接清单（包含 250 条测试数据）
pnpm seed:links

# 以开发模式启动服务
pnpm dev
```

服务启动后将监听 `http://localhost:3000`，您可通过浏览器访问管理界面，或通过 REST API 进行链接管理操作。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用官方二进制或 nvm 安装 |
| PostgreSQL | 14.x 或更高 | 主数据库，用于存储链接元数据、标签及统计信息 |
| Redis | 7.x 或更高 | 缓存与会话存储，可选但推荐用于提升查询性能 |
| pnpm | 8.x 或更高 | 包管理器，用于安装项目依赖及执行脚本 |
| Docker（可选） | 20.x 或更高 | 若使用容器化部署，需安装 Docker Engine 及 Compose |
| 操作系统 | Linux（Ubuntu 22.04）/ macOS 13+ / Windows 11 WSL2 | 生产环境推荐 Linux 发行版 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | `/docs/getting-started` | 如何快速部署、首次登录及导入第一批链接？ |
| 操作手册 | `/docs/usage/link-management` | 如何添加、编辑、删除链接？如何批量校验状态？ |
| 配置参考 | `/docs/configuration/environment` | 有哪些环境变量可调？如何定制健康检查间隔？ |
| API 文档 | `/docs/api/endpoints` | 所有 RESTful 接口的请求/响应格式及鉴权方式是什么？ |
| 运维指南 | `/docs/operations/backup` | 如何备份数据库、迁移数据及监控服务健康度？ |
| 设计文档 | `/docs/design/data-model` | 数据库表关系、索引策略及缓存更新机制是怎样的？ |

## 资源列表

- h5.mobile.fuvxie.cn/Article/3032452.doc
- h5.mobile.puhvjy.cn/Article/552686.doc
- h5.mobile.fuvxie.cn/Article/3653810.doc
- h5.mobile.jnjpgf.cn/Article/7251.doc
- h5.mobile.nzfnve.cn/Article/0869.doc
- h5.mobile.cmcvrr.cn/Article/4113.doc
- h5.mobile.puhvjy.cn/Article/3376.doc
- h5.mobile.cvsifc.cn/Article/8445707.doc
- h5.mobile.nzfnve.cn/Article/445466.doc
- h5.mobile.cmcvrr.cn/Article/767976.doc
- h5.mobile.nzfnve.cn/Article/94395.doc
- h5.mobile.cmcvrr.cn/Article/6238.doc
- h5.mobile.hcbezg.cn/Article/7883.doc
- h5.mobile.nwbbyt.cn/Article/50032.doc
- h5.mobile.cvsifc.cn/Article/061972.doc
- h5.mobile.jnjpgf.cn/Article/5704.doc
- h5.mobile.fuvxie.cn/Article/4764553.doc
- h5.mobile.hcbezg.cn/Article/92291.doc
- h5.mobile.jnjpgf.cn/Article/8923.doc
- h5.mobile.cvsifc.cn/Article/364683.doc
- h5.mobile.cmcvrr.cn/Article/2708.doc
- h5.mobile.jnjpgf.cn/Article/45496.doc
- h5.mobile.cmcvrr.cn/Article/276794.doc
- h5.mobile.cvsifc.cn/Article/6540947.doc
- h5.mobile.cmcvrr.cn/Article/3216371.doc
- h5.mobile.jnjpgf.cn/Article/510744.doc
- h5.mobile.hcbezg.cn/Article/664255.doc
- h5.mobile.nwbbyt.cn/Article/6220526.doc
- h5.mobile.puhvjy.cn/Article/285626.doc
- h5.mobile.cvsifc.cn/Article/656296.doc
- h5.mobile.nzfnve.cn/Article/2046512.doc
- h5.mobile.fuvxie.cn/Article/564162.doc
- h5.mobile.hcbezg.cn/Article/1105.doc
- h5.mobile.nwbbyt.cn/Article/891575.doc
- h5.mobile.nzfnve.cn/Article/0962.doc
- h5.mobile.jnjpgf.cn/Article/725664.doc
- h5.mobile.jnjpgf.cn/Article/4722321.doc
- h5.mobile.nwbbyt.cn/Article/6533383.doc
- h5.mobile.puhvjy.cn/Article/6166257.doc
- h5.mobile.nzfnve.cn/Article/3002041.doc
- h5.mobile.cvsifc.cn/Article/5269.doc
- h5.mobile.nwbbyt.cn/Article/6287355.doc
- h5.mobile.nzfnve.cn/Article/1193.doc
- h5.mobile.hcbezg.cn/Article/59120.doc
- h5.mobile.jnjpgf.cn/Article/8885412.doc
- h5.mobile.nwbbyt.cn/Article/428832.doc
- h5.mobile.cvsifc.cn/Article/0364.doc
- h5.mobile.nzfnve.cn/Article/4497.doc
- h5.mobile.jnjpgf.cn/Article/1192314.doc
- h5.mobile.jnjpgf.cn/Article/8437.doc
- h5.mobile.fuvxie.cn/Article/48600.doc
- h5.mobile.nzfnve.cn/Article/999736.doc
- h5.mobile.cmcvrr.cn/Article/24692.doc
- h5.mobile.puhvjy.cn/Article/598492.doc
- h5.mobile.nzfnve.cn/Article/6385651.doc
- h5.mobile.cmcvrr.cn/Article/6590847.doc
- h5.mobile.cvsifc.cn/Article/1618545.doc
- h5.mobile.hcbezg.cn/Article/152640.doc
- h5.mobile.puhvjy.cn/Article/14804.doc
- h5.mobile.hcbezg.cn/Article/7122.doc
- h5.mobile.cvsifc.cn/Article/84420.doc
- h5.mobile.nwbbyt.cn/Article/83595.doc
- h5.mobile.cvsifc.cn/Article/577670.doc
- h5.mobile.puhvjy.cn/Article/495517.doc
- h5.mobile.fuvxie.cn/Article/6665.doc
- h5.mobile.puhvjy.cn/Article/1068.doc
- h5.mobile.fuvxie.cn/Article/40124.doc
- h5.mobile.hcbezg.cn/Article/5577865.doc
- h5.mobile.nzfnve.cn/Article/28744.doc
- h5.mobile.nwbbyt.cn/Article/092703.doc
- h5.mobile.nzfnve.cn/Article/9244580.doc
- h5.mobile.nwbbyt.cn/Article/312452.doc
- h5.mobile.cvsifc.cn/Article/24515.doc
- h5.mobile.nzfnve.cn/Article/3127209.doc
- h5.mobile.nwbbyt.cn/Article/053833.doc
- h5.mobile.nwbbyt.cn/Article/8670543.doc
- h5.mobile.fuvxie.cn/Article/0218156.doc
- h5.mobile.nzfnve.cn/Article/5832.doc
- h5.mobile.fuvxie.cn/Article/5731118.doc
- h5.mobile.cvsifc.cn/Article/96643.doc
- h5.mobile.nzfnve.cn/Article/02276.doc
- h5.mobile.jnjpgf.cn/Article/26661.doc
- h5.mobile.jnjpgf.cn/Article/23764.doc
- h5.mobile.nwbbyt.cn/Article/419493.doc
- h5.mobile.hcbezg.cn/Article/6739.doc
- h5.mobile.cvsifc.cn/Article/197413.doc
- h5.mobile.nwbbyt.cn/Article/9761899.doc
- h5.mobile.cmcvrr.cn/Article/1470889.doc
- h5.mobile.nwbbyt.cn/Article/44741.doc
- h5.mobile.nzfnve.cn/Article/23668.doc
- h5.mobile.puhvjy.cn/Article/9515559.doc
- h5.mobile.fuvxie.cn/Article/70365.doc
- h5.mobile.nzfnve.cn/Article/76307.doc
- h5.mobile.fuvxie.cn/Article/76664.doc
- h5.mobile.jnjpgf.cn/Article/3755950.doc
- h5.mobile.hcbezg.cn/Article/4637076.doc
- h5.mobile.jnjpgf.cn/Article/03622.doc
- h5.mobile.nzfnve.cn/Article/06638.doc
- h5.mobile.cmcvrr.cn/Article/90643.doc
- h5.mobile.nwbbyt.cn/Article/9857.doc
- h5.mobile.jnjpgf.cn/Article/746267.doc
- h5.mobile.nwbbyt.cn/Article/6444.doc
- h5.mobile.jnjpgf.cn/Article/10572.doc
- h5.mobile.hcbezg.cn/Article/688830.doc
- h5.mobile.cvsifc.cn/Article/3088286.doc
- h5.mobile.cmcvrr.cn/Article/17102.doc
- h5.mobile.nwbbyt.cn/Article/4214363.doc
- h5.mobile.cvsifc.cn/Article/8748.doc
- h5.mobile.jnjpgf.cn/Article/61750.doc
- h5.mobile.jnjpgf.cn/Article/9348.doc
- h5.mobile.fuvxie.cn/Article/8167.doc
- h5.mobile.puhvjy.cn/Article/091550.doc
- h5.mobile.jnjpgf.cn/Article/412327.doc
- h5.mobile.hcbezg.cn/Article/57309.doc
- h5.mobile.cvsifc.cn/Article/037278.doc
- h5.mobile.puhvjy.cn/Article/61644.doc
- h5.mobile.nwbbyt.cn/Article/6802.doc
- h5.mobile.nzfnve.cn/Article/4616.doc
- h5.mobile.hcbezg.cn/Article/59538.doc
- h5.mobile.fuvxie.cn/Article/0502.doc
- h5.mobile.hcbezg.cn/Article/551186.doc
- h5.mobile.nwbbyt.cn/Article/38642.doc
- h5.mobile.cvsifc.cn/Article/4775819.doc
- h5.mobile.cmcvrr.cn/Article/5906.doc
- h5.mobile.nwbbyt.cn/Article/068479.doc
- h5.mobile.fuvxie.cn/Article/43604.doc
- h5.mobile.hcbezg.cn/Article/4773.doc
- h5.mobile.cmcvrr.cn/Article/977819.doc
- h5.mobile.jnjpgf.cn/Article/643031.doc
- h5.mobile.cvsifc.cn/Article/83797.doc
- h5.mobile.cmcvrr.cn/Article/7842992.doc
- h5.mobile.nwbbyt.cn/Article/9901745.doc
- h5.mobile.jnjpgf.cn/Article/9288.doc
- h5.mobile.hcbezg.cn/Article/35591.doc
- h5.mobile.jnjpgf.cn/Article/6376.doc
- h5.mobile.cmcvrr.cn/Article/9347616.doc
- h5.mobile.nzfnve.cn/Article/9360.doc
- h5.mobile.jnjpgf.cn/Article/20474.doc
- h5.mobile.jnjpgf.cn/Article/2454.doc
- h5.mobile.nwbbyt.cn/Article/9816.doc
- h5.mobile.cmcvrr.cn/Article/491288.doc
- h5.mobile.cvsifc.cn/Article/8511.doc
- h5.mobile.cmcvrr.cn/Article/986089.doc
- h5.mobile.nzfnve.cn/Article/9250822.doc
- h5.mobile.cmcvrr.cn/Article/2927.doc
- h5.mobile.cmcvrr.cn/Article/02332.doc
- h5.mobile.fuvxie.cn/Article/7182126.doc
- h5.mobile.nzfnve.cn/Article/013001.doc
- h5.mobile.jnjpgf.cn/Article/7101.doc
- h5.mobile.cmcvrr.cn/Article/7802410.doc
- h5.mobile.cvsifc.cn/Article/2914.doc
- h5.mobile.puhvjy.cn/Article/914353.doc
- h5.mobile.cmcvrr.cn/Article/327892.doc
- h5.mobile.hcbezg.cn/Article/0303397.doc
- h5.mobile.cmcvrr.cn/Article/5613.doc
- h5.mobile.cvsifc.cn/Article/1037.doc
- h5.mobile.nzfnve.cn/Article/3841733.doc
- h5.mobile.fuvxie.cn/Article/25140.doc
- h5.mobile.fuvxie.cn/Article/7370592.doc
- h5.mobile.fuvxie.cn/Article/622817.doc
- h5.mobile.nwbbyt.cn/Article/0569155.doc
- h5.mobile.nzfnve.cn/Article/3655.doc
- h5.mobile.cmcvrr.cn/Article/10002.doc
- h5.mobile.hcbezg.cn/Article/9987.doc
- h5.mobile.cmcvrr.cn/Article/3478.doc
- h5.mobile.nzfnve.cn/Article/779500.doc
- h5.mobile.fuvxie.cn/Article/906297.doc
- h5.mobile.jnjpgf.cn/Article/6082.doc
- h5.mobile.jnjpgf.cn/Article/52564.doc
- h5.mobile.fuvxie.cn/Article/797803.doc
- h5.mobile.fuvxie.cn/Article/1262569.doc
- h5.mobile.hcbezg.cn/Article/5921.doc
- h5.mobile.cmcvrr.cn/Article/4529.doc
- h5.mobile.puhvjy.cn/Article/0939388.doc
- h5.mobile.cmcvrr.cn/Article/2917250.doc
- h5.mobile.jnjpgf.cn/Article/3823.doc
- h5.mobile.fuvxie.cn/Article/9436.doc
- h5.mobile.nwbbyt.cn/Article/6617.doc
- h5.mobile.cvsifc.cn/Article/096987.doc
- h5.mobile.jnjpgf.cn/Article/0913215.doc
- h5.mobile.jnjpgf.cn/Article/1213.doc
- h5.mobile.cvsifc.cn/Article/298388.doc
- h5.mobile.fuvxie.cn/Article/7340.doc
- h5.mobile.puhvjy.cn/Article/7334300.doc
- h5.mobile.jnjpgf.cn/Article/12855.doc
- h5.mobile.puhvjy.cn/Article/1191713.doc
- h5.mobile.cvsifc.cn/Article/2819583.doc
- h5.mobile.hcbezg.cn/Article/4185358.doc
- h5.mobile.cvsifc.cn/Article/0886.doc
- h5.mobile.cvsifc.cn/Article/859783.doc
- h5.mobile.cvsifc.cn/Article/378886.doc
- h5.mobile.jnjpgf.cn/Article/036441.doc
- h5.mobile.cvsifc.cn/Article/8149562.doc
- h5.mobile.cmcvrr.cn/Article/6741.doc
- h5.mobile.puhvjy.cn/Article/4452.doc
- h5.mobile.cvsifc.cn/Article/6821.doc
- h5.mobile.nzfnve.cn/Article/14909.doc
- h5.mobile.puhvjy.cn/Article/5847186.doc
- h5.mobile.hcbezg.cn/Article/353701.doc
- h5.mobile.cvsifc.cn/Article/59733.doc
- h5.mobile.nwbbyt.cn/Article/6375.doc
- h5.mobile.fuvxie.cn/Article/7199.doc
- h5.mobile.puhvjy.cn/Article/647131.doc
- h5.mobile.cmcvrr.cn/Article/615768.doc
- h5.mobile.nwbbyt.cn/Article/6143.doc
- h5.mobile.cmcvrr.cn/Article/9917598.doc
- h5.mobile.nwbbyt.cn/Article/9307.doc
- h5.mobile.puhvjy.cn/Article/01309.doc
- h5.mobile.jnjpgf.cn/Article/6441.doc
- h5.mobile.puhvjy.cn/Article/422163.doc
- h5.mobile.cvsifc.cn/Article/5267.doc
- h5.mobile.cmcvrr.cn/Article/08021.doc
- h5.mobile.puhvjy.cn/Article/189366.doc
- h5.mobile.cvsifc.cn/Article/5496.doc
- h5.mobile.nzfnve.cn/Article/311639.doc
- h5.mobile.hcbezg.cn/Article/1713.doc
- h5.mobile.cmcvrr.cn/Article/07413.doc
- h5.mobile.nzfnve.cn/Article/4565.doc
- h5.mobile.nwbbyt.cn/Article/80680.doc
- h5.mobile.hcbezg.cn/Article/19705.doc
- h5.mobile.nwbbyt.cn/Article/101862.doc
- h5.mobile.fuvxie.cn/Article/3542.doc
- h5.mobile.jnjpgf.cn/Article/950756.doc
- h5.mobile.hcbezg.cn/Article/0821053.doc
- h5.mobile.fuvxie.cn/Article/949580.doc
- h5.mobile.nwbbyt.cn/Article/1059772.doc
- h5.mobile.nwbbyt.cn/Article/8196182.doc
- h5.mobile.fuvxie.cn/Article/0330510.doc
- h5.mobile.nzfnve.cn/Article/3731514.doc
- h5.mobile.nwbbyt.cn/Article/7909.doc
- h5.mobile.hcbezg.cn/Article/7961.doc
- h5.mobile.fuvxie.cn/Article/96894.doc
- h5.mobile.cmcvrr.cn/Article/1976.doc
- h5.mobile.cvsifc.cn/Article/5224.doc
- h5.mobile.nwbbyt.cn/Article/7910194.doc
- h5.mobile.jnjpgf.cn/Article/3198.doc
- h5.mobile.hcbezg.cn/Article/8990.doc
- h5.mobile.nzfnve.cn/Article/9097.doc
- h5.mobile.cvsifc.cn/Article/2407699.doc
- h5.mobile.nzfnve.cn/Article/4763.doc
- h5.mobile.jnjpgf.cn/Article/74587.doc
- h5.mobile.jnjpgf.cn/Article/6423.doc
- h5.mobile.cvsifc.cn/Article/8785.doc
- h5.mobile.hcbezg.cn/Article/8160.doc
- h5.mobile.hcbezg.cn/Article/6919.doc
- h5.mobile.nwbbyt.cn/Article/4785.doc
- h5.mobile.cmcvrr.cn/Article/6295803.doc
- h5.mobile.hcbezg.cn/Article/1730901.doc
- h5.mobile.cmcvrr.cn/Article/86127.doc
- h5.mobile.cmcvrr.cn/Article/29677.doc

## 项目结构

```
doclink-hub/
├── apps/
│   ├── web/                         # 主 Web 应用（Next.js 14，App Router）
│   │   ├── src/app/                 # 页面路由与布局
│   │   ├── src/components/          # 可复用 UI 组件（shadcn/ui）
│   │   └── src/lib/                 # 服务端工具函数与数据层
│   └── worker/                      # 后台任务服务（BullMQ + Redis）
│       ├── src/queues/              # 链接校验、统计聚合队列
│       └── src/processors/          # 任务处理器
├── packages/
│   ├── db/                          # 数据库 Schema 与迁移（Prisma）
│   │   ├── schema.prisma
│   │   └── migrations/
│   ├── api-client/                  # 类型安全的 REST API 客户端
│   ├── shared-types/               # 跨应用共享 TypeScript 类型
│   └── utils/                      # 通用工具（URL 解析、日期格式化）
├── configs/
│   ├── eslint/                      # 共享 ESLint 配置
│   ├── prettier/                    # 代码风格配置
│   └── tsconfig/                    # 基础 TypeScript 配置
├── scripts/
│   ├── seed-links.ts               # 从原始 URL 列表批量导入链接
│   ├── health-check.ts             # 手动触发全量链接校验
│   └── export-to-markdown.ts      # 导出索引为 Markdown 表格
├── docker/
│   ├── docker-compose.yml          # 本地开发依赖（PostgreSQL + Redis）
│   └── Dockerfile.prod             # 生产环境镜像构建
├── docs/                            # 详细文档源文件
│   ├── getting-started/
│   ├── usage/
│   └── api/
├── .env.example                     # 环境变量模板
├── .gitignore
├── package.json                     # 根目录依赖与 workspaces 配置
├── pnpm-workspace.yaml
└── README.md                        # 本文件
```

## 贡献指南

我们欢迎并鼓励社区提交贡献，包括但不限于功能建议、Bug 修复、文档完善及性能优化。请遵循以下流程：

1. 查阅 Issue 列表及项目看板，确认当前开发优先级。若准备提交新功能或较大修改，请先创建一个 Discussion 或 Issue 进行方案讨论，避免重复工作。

2. Fork 本仓库至个人账户，并克隆到本地开发环境。确保使用 pnpm 安装依赖，且本地已启动 PostgreSQL 和 Redis 容器（可使用 `docker-compose up -d` 快速启动）。

3. 创建新的功能分支，分支命名遵循 `feat/xxx`、`fix/xxx`、`docs/xxx` 格式。提交代码前请运行 `pnpm lint` 和 `pnpm test` 确保通过所有检查，并补充必要的单元测试或集成测试。

4. 提交 Pull Request 到主仓库的 `main` 分支，描述中需清晰说明变更内容、影响范围及测试情况。核心模块的 PR 至少需要一名维护者 Approve。

5. 文档类贡献可直接在 `/docs` 目录下修改或新增 `.md` 文件，提交 PR 时标注 `[skip ci]` 以跳过 CI 构建流程。所有文档更新需确保与代码行为一致。

## 常见问题

**Q: 导入的链接如果返回 404 或超时，系统会如何处理？**

A: 导入时仅做格式校验（URL 合法性与扩展名识别），不会实时请求资源。健康检查任务（默认每天凌晨 2:00 执行）会发起 HEAD 请求，将状态码、响应时间及错误信息记录到数据库。管理员可在控制台的“健康看板”查看所有失效链接列表，并一键导出失效报表。您也可以调整 `.env` 中的 `CHECK_INTERVAL_CRON` 参数自定义检查频率。

**Q: 支持自定义字段或扩展属性吗？**

A: 当前版本提供 `metadata` JSONB 字段，允许存储任意键值对（如“所属部门”“审核人”“原文发布时间”）。您可以在 UI 的“高级属性”面板中编辑，或通过 API 的 `metadata` 参数写入。后续版本将支持基于 metadata 的筛选和排序。若需要固定额外的必填字段，可修改 Prisma Schema 并运行 `pnpm db:push` 迁移，但请注意向后兼容性。

**Q: 如何处理链接中的敏感信息或内网地址？**

A: DocLink Hub 本身不代理或缓存文件内容，仅存储元数据。若您的链接包含内网 IP 或私有域名，建议在部署时配置网络访问控制（如防火墙、VPN），并开启项目内置的 IP 白名单功能（设置 `ALLOWED_IP_RANGES` 环境变量）。所有 API 响应均不返回完整文件内容，仅返回元数据及状态码。若需更高级的脱敏处理，可集成外部密钥管理服务（如 HashiCorp Vault）。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

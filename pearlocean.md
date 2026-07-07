# DOC-LINK 统一文档资源聚合系统

DOC-LINK 是一个面向技术团队、研究人员与内容管理者的轻量级文档资源外链聚合与导航系统。该项目定位于对分散在多个域名下的文档类资源（.doc 文件）进行统一收录、分类索引与快速检索，解决因文档分散存储导致的查找效率低下、链接失效难以追踪、资源归属不清晰等问题。目标用户包括企业内部知识库管理员、开源文档项目维护者、技术培训资料整理人员以及需要批量管理外链文档资源的各类组织。

本系统不提供文档内容的存储服务，而是作为一层透明的资源索引中间层，将原始文档链接以规范化列表的形式对外呈现，并提供基础的元数据标记、分类过滤与可用性检测能力。通过 DOC-LINK，用户可以在一处集中浏览来自多个源站点的海量文档资源，无需记忆繁多的域名与路径。

## 功能概览

多源域名统一收录 系统支持对来自不同域名的文档资源进行集中列表展示，当前已覆盖 cmcvrr.cn、hcbezg.cn、fuvxie.cn、puhvjy.cn、nzfnve.cn、jnjpgf.cn、nwbbyt.cn、cvsifc.cn 等八个源站域名，后续可扩展至更多域名。

文档级细粒度链接管理 每个文档资源以完整 URL 形式存储，保留原始域名的协议、主机名与路径信息，确保链接的原始性与可追溯性，便于与上游源站保持严格一致。

批量资源导入与导出 支持通过文本列表批量导入文档链接，并可导出为标准格式的清单文件，方便与其他知识管理工具（如 Notion、Obsidian、Confluence）进行数据交换。

链接可用性健康检查 内置定时任务，对已收录的文档链接进行 HTTP 状态码探测，自动标记失效链接并生成异常报告，减少用户访问死链的几率。

分类标签与模糊检索 允许用户为每个文档资源打上自定义标签（如 技术手册、培训资料、合同模板、操作规范），并支持按标签过滤与按文件名关键词模糊检索。

访问统计与热度排序 记录每个文档链接的被点击次数，提供按热度排序功能，帮助用户快速定位高频访问的资源。

响应式管理面板 提供基于 Web 的管理界面，适配桌面与移动设备，支持随时随地进行资源增删改查操作。

## 应用场景

企业内部知识库文档聚合 企业内部的培训材料、操作手册、制度文件往往散落在多个内部服务器的不同目录下。DOC-LINK 可将这些分散的文档链接统一收录，形成一个集中的知识入口，新员工入职时只需访问 DOC-LINK 即可浏览全部培训资料，无需逐一询问文档存放位置。

技术文档开源项目的外链管理 开源项目通常需要引用大量外部参考文档、标准规范或数据表。DOC-LINK 可作为项目文档仓库的补充，以结构化列表的形式管理所有外部引用链接，确保引用来源清晰可查，同时便于在版本迭代中增删或更新引用。

教育机构课程资料索引 高校或培训机构在开展在线教学时，讲师会提供大量补充阅读材料、习题答案或实验指导书的下载链接。DOC-LINK 可按课程、学期或专业方向对链接进行分类整理，学生通过一个入口即可获取全部资料，避免因链接分散在多个邮件或聊天记录中而遗漏。

文档资源归档与迁移辅助 在站点迁移或域名更换过程中，DOC-LINK 可快速导出所有文档链接清单，供迁移脚本批量处理。同时，通过健康检查功能可提前发现即将失效的链接，通知源站管理员及时修复。

## 快速开始

以下命令将 DOC-LINK 克隆至本地、安装依赖并启动开发服务。

```bash
git clone https://github.com/doc-link/doc-link.git
cd doc-link
npm install
npm run dev
```

若使用 yarn：

```bash
yarn install
yarn dev
```

生产环境构建：

```bash
npm run build
npm start
```

或使用 yarn：

```bash
yarn build
yarn start
```

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | >= 18.0.0 | 运行时环境，用于执行服务端与构建脚本 |
| npm | >= 9.0.0 或 yarn >= 1.22.0 | 包管理器，用于安装项目依赖 |
| SQLite | 3.0 及以上（内置） | 默认数据库，用于存储链接元数据与访问日志 |
| PostgreSQL | >= 14.0（可选） | 生产环境推荐使用，支持更高并发与数据完整性约束 |
| Redis | >= 7.0（可选） | 用于缓存热点链接的可用性状态，降低健康检查频率 |
| Nginx | >= 1.24（可选） | 反向代理与静态资源服务，用于生产部署时的负载均衡 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户指南 | /docs/user-guide.md | 如何浏览、检索、收藏文档链接；如何查看链接详情与访问统计 |
| 管理员手册 | /docs/admin-guide.md | 如何添加、编辑、删除文档链接；如何管理分类标签；如何查看健康检查报告 |
| 开发指引 | /docs/developer-guide.md | 如何扩展新的文档源解析器；如何自定义前端主题；如何编写单元测试 |
| API 参考 | /docs/api-reference.md | 对外提供的 RESTful API 端点有哪些；请求与响应格式是什么；认证方式如何配置 |
| 部署文档 | /docs/deployment.md | 如何将系统部署至生产环境；如何配置 SSL 证书；如何设置定时备份任务 |
| 架构概述 | /docs/architecture.md | 系统整体架构设计；数据流向；各模块职责边界与扩展点说明 |

## 资源列表

- h5.mobile.cmcvrr.cn/Article/77494.doc
- h5.mobile.hcbezg.cn/Article/533965.doc
- h5.mobile.fuvxie.cn/Article/9393562.doc
- h5.mobile.puhvjy.cn/Article/06659.doc
- h5.mobile.nzfnve.cn/Article/2946113.doc
- h5.mobile.nzfnve.cn/Article/9793.doc
- h5.mobile.nzfnve.cn/Article/177800.doc
- h5.mobile.jnjpgf.cn/Article/0318.doc
- h5.mobile.fuvxie.cn/Article/055306.doc
- h5.mobile.nwbbyt.cn/Article/87173.doc
- h5.mobile.puhvjy.cn/Article/45540.doc
- h5.mobile.nwbbyt.cn/Article/9486.doc
- h5.mobile.cvsifc.cn/Article/52010.doc
- h5.mobile.puhvjy.cn/Article/422916.doc
- h5.mobile.hcbezg.cn/Article/67480.doc
- h5.mobile.nzfnve.cn/Article/05140.doc
- h5.mobile.cvsifc.cn/Article/232375.doc
- h5.mobile.cmcvrr.cn/Article/3977059.doc
- h5.mobile.cvsifc.cn/Article/0673.doc
- h5.mobile.nwbbyt.cn/Article/0875421.doc
- h5.mobile.puhvjy.cn/Article/1160.doc
- h5.mobile.jnjpgf.cn/Article/1246261.doc
- h5.mobile.cmcvrr.cn/Article/6519.doc
- h5.mobile.puhvjy.cn/Article/839556.doc
- h5.mobile.nwbbyt.cn/Article/2341.doc
- h5.mobile.hcbezg.cn/Article/0768.doc
- h5.mobile.nwbbyt.cn/Article/851456.doc
- h5.mobile.nzfnve.cn/Article/434402.doc
- h5.mobile.cmcvrr.cn/Article/39417.doc
- h5.mobile.cvsifc.cn/Article/851281.doc
- h5.mobile.hcbezg.cn/Article/6440360.doc
- h5.mobile.hcbezg.cn/Article/83818.doc
- h5.mobile.nwbbyt.cn/Article/8247910.doc
- h5.mobile.fuvxie.cn/Article/8446.doc
- h5.mobile.nzfnve.cn/Article/02328.doc
- h5.mobile.puhvjy.cn/Article/4398971.doc
- h5.mobile.cvsifc.cn/Article/9018.doc
- h5.mobile.hcbezg.cn/Article/944432.doc
- h5.mobile.puhvjy.cn/Article/60427.doc
- h5.mobile.puhvjy.cn/Article/8416187.doc
- h5.mobile.cmcvrr.cn/Article/97941.doc
- h5.mobile.fuvxie.cn/Article/9715.doc
- h5.mobile.cvsifc.cn/Article/2762.doc
- h5.mobile.hcbezg.cn/Article/379096.doc
- h5.mobile.hcbezg.cn/Article/1279.doc
- h5.mobile.nzfnve.cn/Article/890066.doc
- h5.mobile.jnjpgf.cn/Article/8081392.doc
- h5.mobile.nwbbyt.cn/Article/38819.doc
- h5.mobile.hcbezg.cn/Article/1959053.doc
- h5.mobile.puhvjy.cn/Article/073366.doc
- h5.mobile.cvsifc.cn/Article/0424.doc
- h5.mobile.cvsifc.cn/Article/312163.doc
- h5.mobile.jnjpgf.cn/Article/1809949.doc
- h5.mobile.cmcvrr.cn/Article/6828453.doc
- h5.mobile.nzfnve.cn/Article/354988.doc
- h5.mobile.nwbbyt.cn/Article/4827.doc
- h5.mobile.nwbbyt.cn/Article/2988.doc
- h5.mobile.cmcvrr.cn/Article/406985.doc
- h5.mobile.jnjpgf.cn/Article/34355.doc
- h5.mobile.puhvjy.cn/Article/97052.doc
- h5.mobile.jnjpgf.cn/Article/423849.doc
- h5.mobile.nzfnve.cn/Article/3113.doc
- h5.mobile.hcbezg.cn/Article/4150.doc
- h5.mobile.cvsifc.cn/Article/8550565.doc
- h5.mobile.puhvjy.cn/Article/3643060.doc
- h5.mobile.fuvxie.cn/Article/3732.doc
- h5.mobile.nwbbyt.cn/Article/6562099.doc
- h5.mobile.puhvjy.cn/Article/91601.doc
- h5.mobile.cvsifc.cn/Article/01201.doc
- h5.mobile.fuvxie.cn/Article/0245.doc
- h5.mobile.cvsifc.cn/Article/4907.doc
- h5.mobile.hcbezg.cn/Article/838932.doc
- h5.mobile.nwbbyt.cn/Article/1927.doc
- h5.mobile.jnjpgf.cn/Article/17321.doc
- h5.mobile.nwbbyt.cn/Article/4387.doc
- h5.mobile.hcbezg.cn/Article/992679.doc
- h5.mobile.hcbezg.cn/Article/6251342.doc
- h5.mobile.jnjpgf.cn/Article/17012.doc
- h5.mobile.hcbezg.cn/Article/1819052.doc
- h5.mobile.nzfnve.cn/Article/37867.doc
- h5.mobile.hcbezg.cn/Article/4480521.doc
- h5.mobile.nzfnve.cn/Article/22556.doc
- h5.mobile.hcbezg.cn/Article/6250.doc
- h5.mobile.cmcvrr.cn/Article/590111.doc
- h5.mobile.puhvjy.cn/Article/552726.doc
- h5.mobile.fuvxie.cn/Article/3805357.doc
- h5.mobile.nwbbyt.cn/Article/2747.doc
- h5.mobile.nzfnve.cn/Article/147961.doc
- h5.mobile.puhvjy.cn/Article/0902.doc
- h5.mobile.fuvxie.cn/Article/612662.doc
- h5.mobile.fuvxie.cn/Article/9125.doc
- h5.mobile.jnjpgf.cn/Article/22134.doc
- h5.mobile.nwbbyt.cn/Article/39394.doc
- h5.mobile.cvsifc.cn/Article/55714.doc
- h5.mobile.jnjpgf.cn/Article/20794.doc
- h5.mobile.jnjpgf.cn/Article/2937467.doc
- h5.mobile.cmcvrr.cn/Article/44917.doc
- h5.mobile.hcbezg.cn/Article/1448.doc
- h5.mobile.nzfnve.cn/Article/726358.doc
- h5.mobile.hcbezg.cn/Article/2457.doc
- h5.mobile.fuvxie.cn/Article/6152.doc
- h5.mobile.puhvjy.cn/Article/21134.doc
- h5.mobile.cmcvrr.cn/Article/092609.doc
- h5.mobile.nwbbyt.cn/Article/5677821.doc
- h5.mobile.fuvxie.cn/Article/87536.doc
- h5.mobile.cvsifc.cn/Article/8124513.doc
- h5.mobile.nzfnve.cn/Article/7111305.doc
- h5.mobile.fuvxie.cn/Article/51044.doc
- h5.mobile.hcbezg.cn/Article/361846.doc
- h5.mobile.fuvxie.cn/Article/2632.doc
- h5.mobile.nzfnve.cn/Article/151502.doc
- h5.mobile.cmcvrr.cn/Article/89553.doc
- h5.mobile.fuvxie.cn/Article/15754.doc
- h5.mobile.cvsifc.cn/Article/9378.doc
- h5.mobile.cvsifc.cn/Article/7243.doc
- h5.mobile.nwbbyt.cn/Article/7295.doc
- h5.mobile.puhvjy.cn/Article/647266.doc
- h5.mobile.hcbezg.cn/Article/91246.doc
- h5.mobile.cvsifc.cn/Article/29467.doc
- h5.mobile.cvsifc.cn/Article/0765.doc
- h5.mobile.jnjpgf.cn/Article/3162579.doc
- h5.mobile.cvsifc.cn/Article/6396.doc
- h5.mobile.hcbezg.cn/Article/5851.doc
- h5.mobile.cmcvrr.cn/Article/2718.doc
- h5.mobile.fuvxie.cn/Article/9478007.doc
- h5.mobile.puhvjy.cn/Article/5107733.doc
- h5.mobile.nzfnve.cn/Article/456982.doc
- h5.mobile.jnjpgf.cn/Article/13025.doc
- h5.mobile.nzfnve.cn/Article/54692.doc
- h5.mobile.cmcvrr.cn/Article/1679.doc
- h5.mobile.cvsifc.cn/Article/6113.doc
- h5.mobile.puhvjy.cn/Article/29416.doc
- h5.mobile.cvsifc.cn/Article/1894.doc
- h5.mobile.cmcvrr.cn/Article/7887262.doc
- h5.mobile.puhvjy.cn/Article/0574.doc
- h5.mobile.nwbbyt.cn/Article/79146.doc
- h5.mobile.nzfnve.cn/Article/326021.doc
- h5.mobile.nwbbyt.cn/Article/165352.doc
- h5.mobile.nzfnve.cn/Article/56854.doc
- h5.mobile.fuvxie.cn/Article/6025.doc
- h5.mobile.nzfnve.cn/Article/3458161.doc
- h5.mobile.nzfnve.cn/Article/3865828.doc
- h5.mobile.puhvjy.cn/Article/2226.doc
- h5.mobile.puhvjy.cn/Article/4430.doc
- h5.mobile.nwbbyt.cn/Article/2637.doc
- h5.mobile.jnjpgf.cn/Article/940685.doc
- h5.mobile.nzfnve.cn/Article/901547.doc
- h5.mobile.nwbbyt.cn/Article/5683613.doc
- h5.mobile.jnjpgf.cn/Article/1835.doc
- h5.mobile.nwbbyt.cn/Article/8200358.doc
- h5.mobile.nwbbyt.cn/Article/209150.doc
- h5.mobile.fuvxie.cn/Article/2901973.doc
- h5.mobile.hcbezg.cn/Article/3058.doc
- h5.mobile.hcbezg.cn/Article/58823.doc
- h5.mobile.hcbezg.cn/Article/2387.doc
- h5.mobile.hcbezg.cn/Article/5986298.doc
- h5.mobile.nwbbyt.cn/Article/88430.doc
- h5.mobile.jnjpgf.cn/Article/2348.doc
- h5.mobile.puhvjy.cn/Article/5501.doc
- h5.mobile.nwbbyt.cn/Article/3932.doc
- h5.mobile.nwbbyt.cn/Article/418487.doc
- h5.mobile.fuvxie.cn/Article/9328.doc
- h5.mobile.jnjpgf.cn/Article/33380.doc
- h5.mobile.jnjpgf.cn/Article/5237251.doc
- h5.mobile.fuvxie.cn/Article/81315.doc
- h5.mobile.fuvxie.cn/Article/806029.doc
- h5.mobile.hcbezg.cn/Article/2430214.doc
- h5.mobile.nwbbyt.cn/Article/1721821.doc
- h5.mobile.cvsifc.cn/Article/770941.doc
- h5.mobile.cvsifc.cn/Article/9217546.doc
- h5.mobile.nzfnve.cn/Article/2135183.doc
- h5.mobile.fuvxie.cn/Article/314126.doc
- h5.mobile.nzfnve.cn/Article/75280.doc
- h5.mobile.nwbbyt.cn/Article/37226.doc
- h5.mobile.jnjpgf.cn/Article/2523.doc
- h5.mobile.hcbezg.cn/Article/7153.doc
- h5.mobile.hcbezg.cn/Article/53869.doc
- h5.mobile.jnjpgf.cn/Article/57719.doc
- h5.mobile.cmcvrr.cn/Article/964205.doc
- h5.mobile.fuvxie.cn/Article/35568.doc
- h5.mobile.fuvxie.cn/Article/377774.doc
- h5.mobile.hcbezg.cn/Article/7660.doc
- h5.mobile.puhvjy.cn/Article/05490.doc
- h5.mobile.jnjpgf.cn/Article/2486.doc
- h5.mobile.puhvjy.cn/Article/05176.doc
- h5.mobile.nwbbyt.cn/Article/415149.doc
- h5.mobile.cvsifc.cn/Article/1449403.doc
- h5.mobile.nzfnve.cn/Article/372514.doc
- h5.mobile.cmcvrr.cn/Article/696893.doc
- h5.mobile.fuvxie.cn/Article/327160.doc
- h5.mobile.nwbbyt.cn/Article/58417.doc
- h5.mobile.fuvxie.cn/Article/7944076.doc
- h5.mobile.puhvjy.cn/Article/6964.doc
- h5.mobile.hcbezg.cn/Article/0880.doc
- h5.mobile.puhvjy.cn/Article/5710667.doc
- h5.mobile.cmcvrr.cn/Article/2805594.doc
- h5.mobile.puhvjy.cn/Article/9758750.doc
- h5.mobile.nzfnve.cn/Article/2644.doc
- h5.mobile.cvsifc.cn/Article/903298.doc
- h5.mobile.jnjpgf.cn/Article/5128.doc
- h5.mobile.nwbbyt.cn/Article/6733.doc
- h5.mobile.puhvjy.cn/Article/678229.doc
- h5.mobile.cmcvrr.cn/Article/6056.doc
- h5.mobile.hcbezg.cn/Article/28845.doc
- h5.mobile.puhvjy.cn/Article/4334145.doc
- h5.mobile.nwbbyt.cn/Article/9067.doc
- h5.mobile.jnjpgf.cn/Article/51719.doc
- h5.mobile.fuvxie.cn/Article/49054.doc
- h5.mobile.puhvjy.cn/Article/758743.doc
- h5.mobile.cvsifc.cn/Article/318817.doc
- h5.mobile.nzfnve.cn/Article/631035.doc
- h5.mobile.puhvjy.cn/Article/882759.doc
- h5.mobile.fuvxie.cn/Article/3527.doc
- h5.mobile.cmcvrr.cn/Article/240451.doc
- h5.mobile.fuvxie.cn/Article/8721.doc
- h5.mobile.hcbezg.cn/Article/4235812.doc
- h5.mobile.jnjpgf.cn/Article/9816.doc
- h5.mobile.jnjpgf.cn/Article/9755.doc
- h5.mobile.hcbezg.cn/Article/6794723.doc
- h5.mobile.jnjpgf.cn/Article/791294.doc
- h5.mobile.puhvjy.cn/Article/0808.doc
- h5.mobile.fuvxie.cn/Article/2096.doc
- h5.mobile.fuvxie.cn/Article/7247.doc
- h5.mobile.nwbbyt.cn/Article/6227375.doc
- h5.mobile.cvsifc.cn/Article/476171.doc
- h5.mobile.nzfnve.cn/Article/3064.doc
- h5.mobile.nwbbyt.cn/Article/7566.doc
- h5.mobile.fuvxie.cn/Article/5367.doc
- h5.mobile.cvsifc.cn/Article/30651.doc
- h5.mobile.nwbbyt.cn/Article/0892684.doc
- h5.mobile.cmcvrr.cn/Article/3981746.doc
- h5.mobile.cvsifc.cn/Article/05812.doc
- h5.mobile.nzfnve.cn/Article/832153.doc
- h5.mobile.nwbbyt.cn/Article/69098.doc
- h5.mobile.puhvjy.cn/Article/7166233.doc
- h5.mobile.fuvxie.cn/Article/107452.doc
- h5.mobile.jnjpgf.cn/Article/6890.doc
- h5.mobile.hcbezg.cn/Article/2333.doc
- h5.mobile.hcbezg.cn/Article/12747.doc
- h5.mobile.nzfnve.cn/Article/4485234.doc
- h5.mobile.cvsifc.cn/Article/43885.doc
- h5.mobile.cvsifc.cn/Article/190041.doc
- h5.mobile.cvsifc.cn/Article/72798.doc
- h5.mobile.hcbezg.cn/Article/1994.doc
- h5.mobile.fuvxie.cn/Article/173440.doc
- h5.mobile.cmcvrr.cn/Article/26146.doc
- h5.mobile.cmcvrr.cn/Article/5210394.doc
- h5.mobile.hcbezg.cn/Article/150473.doc
- h5.mobile.nwbbyt.cn/Article/158070.doc
- h5.mobile.puhvjy.cn/Article/946310.doc

## 项目结构

```
doc-link/
├── src/
│   ├── core/                           # 核心业务逻辑模块
│   │   ├── linkManager.js              # 链接增删改查与元数据管理
│   │   ├── healthChecker.js            # 定时健康检查与状态缓存
│   │   └── importer.js                 # 批量导入与格式解析
│   ├── api/                            # RESTful API 路由层
│   │   ├── v1/                         # API v1 版本端点
│   │   │   ├── links.js                # /api/v1/links 路由处理
│   │   │   └── stats.js                # /api/v1/stats 统计接口
│   │   └── middleware/                 # 认证与日志中间件
│   ├── web/                            # 前端管理界面源码
│   │   ├── pages/                      # 页面组件 (Dashboard/List/Detail)
│   │   ├── components/                 # 可复用 UI 组件 (Table/Filter/Pagination)
│   │   └── static/                     # 编译后的静态资源目录
│   ├── scheduler/                      # 定时任务调度器
│   │   ├── dailyCheck.js               # 每日链接可用性检测任务
│   │   └── reportGenerator.js          # 周报与异常报告生成
│   └── utils/                          # 通用工具函数
│       ├── logger.js                   # 日志记录与分级输出
│       └── validator.js                # URL 格式校验与规范化
├── config/
│   ├── default.yaml                    # 默认配置文件 (端口/数据库/日志级别)
│   └── production.yaml                 # 生产环境覆盖配置
├── migrations/                         # 数据库迁移脚本 (SQLite/PostgreSQL)
│   ├── 001_init.sql                    # 初始化链接表与元数据表
│   └── 002_add_index.sql               # 增加检索索引与时间戳字段
├── tests/
│   ├── unit/                           # 单元测试 (Jest)
│   └── integration/                    # 集成测试 (Supertest)
├── docs/                               # 完整文档目录
│   ├── user-guide.md                   # 用户操作指南
│   ├── admin-guide.md                  # 管理员配置手册
│   └── developer-guide.md              # 开发者扩展说明
├── scripts/
│   ├── seed.js                         # 初始化测试数据脚本
│   └── export.js                       # 链接清单导出工具
├── .env.example                        # 环境变量示例文件
├── package.json                        # npm 依赖与脚本定义
├── README.md                           # 本文件
└── LICENSE                             # MIT 许可证
```

## 贡献指南

提交 Issue 报告缺陷或功能请求 在 GitHub Issues 页面新建问题，请使用提供的模板填写复现步骤、环境信息与预期行为，缺陷报告需附带日志片段或截图。

Fork 仓库并创建功能分支 将主仓库 Fork 至个人账户，基于 main 分支创建新的功能分支，分支命名遵循 feature/功能简述 或 fix/问题简述 格式。

编写或更新测试用例 任何新功能或缺陷修复均需提供对应的单元测试或集成测试，确保测试覆盖率达到现有标准，运行 npm test 验证全部用例通过。

提交 Pull Request 并关联 Issue 推送分支后发起 Pull Request，在描述中关联相关 Issue 编号，详细说明变更内容与测试结果，等待维护者审阅。

遵循代码风格规范 项目使用 ESLint 与 Prettier 统一代码风格，提交前请运行 npm run lint 与 npm run format 自动格式化，确保 CI 流水线绿色通过。

## 常见问题

Q: 系统如何保证文档链接的原始性，是否会修改或转存文档内容？
A: DOC-LINK 仅作为链接索引层，不存储任何文档副本，亦不修改原始 URL 的协议、主机名或路径。所有链接以用户提供的原始字符串原样保存与展示，确保与源站完全一致。用户点击链接时直接跳转至原始文档地址，不经过任何中间跳转或代理。

Q: 如何批量更新已收录的链接？若源站域名发生变更，是否需要逐一修改？
A: 系统提供批量导入与导出功能，用户可通过 CSV 或 JSON 格式的清单文件进行全量替换。若源站域名整体迁移，建议先导出当前清单，利用文本编辑器的批量替换功能修改域名部分，再通过导入功能覆盖原有数据。对于单条链接的修改，管理界面支持逐条编辑。

Q: 健康检查任务是否会影响源站性能？检查频率如何配置？
A: 健康检查通过发送 HTTP HEAD 请求探测链接可用性，请求开销极小，不会对源站造成明显负载。默认检查频率为每 24 小时一次，且仅对状态为 4xx 或 5xx 的链接增加重试间隔，避免频繁探测失效链接。检查频率可在 config/default.yaml 中的 scheduler.interval 字段调整。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

# DocLink Hub

DocLink Hub 是一个面向技术文档聚合与轻量级知识库管理的开源项目，专注于将散布于多个移动端 H5 域名下的 Word 文档资源（.doc）进行统一索引、分类检索与快速访问。项目目标用户包括技术文档管理员、企业内部知识库维护者、以及需要从非结构化文档来源中提取链接资产并进行二次开发的工程师。通过声明式的链接配置与自动化元数据抽取，DocLink Hub 帮助用户将原本碎片化的文档链接转化为可维护、可扩展、可监控的资源目录。

## 功能概览

- 多源文档链接聚合：支持从多个 H5 域名路径下批量导入 .doc 文档链接，并提供去重与冲突检测机制。
- 文档元数据智能提取：自动从链接路径中解析文档编号，并支持通过扩展接口从文档内容或响应头中提取标题、大小、更新时间等元信息。
- 分类标签与全文检索：允许用户为每个文档链接添加自定义分类与标签，并基于文档编号与元数据提供轻量级全文检索功能。
- 文档可用性健康检查：周期性地对已收录的文档链接发起 HEAD/GET 请求，检测链接有效性，并生成不可用链接报告。
- 导入导出与批量操作：支持通过 JSON/CSV 格式批量导入链接清单，也支持将当前索引库导出为标准化链接列表，便于迁移或备份。
- 开放 RESTful API：提供基于 JSON 的查询接口，允许外部系统按域名、文档编号、分类等条件查询文档链接，便于集成到现有运维或知识管理平台。
- 轻量级管理仪表板：内置基于 Web 的管理界面，用于查看链接统计、执行手动健康检查、编辑文档元数据，无需额外安装客户端。

## 应用场景

- 企业内部文档资产盘点：企业技术部门可将分散在多个历史 H5 站点中的 Word 技术规范、设计文档、操作手册的链接集中导入 DocLink Hub，形成统一的文档资产清单，并定期检查链接可用性，避免因站点迁移导致文档失联。
- 技术写作与文档归档辅助：技术写作团队在撰写新版本文档时，可通过 DocLink Hub 快速检索历史版本的文档链接，对比文档编号与修改日期，追溯内容变更轨迹，确保版本引用准确。
- 自动化文档同步流水线：运维工程师可将 DocLink Hub 作为文档源数据的中转层，通过 API 将链接列表同步至企业内部搜索服务或云存储备份任务中，实现文档资源的自动化分发与备份。

## 快速开始

以下命令演示了从克隆代码仓库到启动服务的完整流程。

```bash
git clone https://github.com/your-org/doclink-hub.git
cd doclink-hub
npm install
npm run build
npm start
```

若使用 Docker 快速启动，可执行：

```bash
docker build -t doclink-hub .
docker run -p 3000:3000 doclink-hub
```

启动后，访问 `http://localhost:3000` 进入管理仪表板，默认初始账号为 `admin`，密码首次启动时会在控制台日志中输出。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | >= 18.0.0 | 项目运行时环境，建议使用 LTS 版本 |
| npm | >= 8.0.0 | 用于安装项目依赖包 |
| SQLite3 | 系统自带或由 better-sqlite3 提供 | 默认内置轻量级数据库，无需额外安装 |
| Docker (可选) | >= 20.0.0 | 仅在使用容器化部署时需要 |
| curl / wget (可选) | 任意版本 | 用于健康检查模块发起的 HTTP 探测，系统自带即可 |
| 内存 | >= 512 MB | 生产环境建议 1 GB 以上 |
| 磁盘 | >= 1 GB | 用于存储索引库及日志文件，建议 SSD |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | `/docs/getting-started.md` | 如何快速完成安装并导入第一批文档链接？ |
| 配置参考 | `/docs/configuration.md` | 如何调整链接健康检查间隔、数据库路径、API 端口等参数？ |
| API 手册 | `/docs/api-reference.md` | 外部系统如何通过 RESTful API 查询文档链接或触发健康检查？ |
| 运维指南 | `/docs/operations.md` | 如何备份数据库、迁移索引、处理大量失效链接？ |

## 资源列表

- h5.mobile.fuvxie.cn/Article/477661.doc
- h5.mobile.nwbbyt.cn/Article/1558.doc
- h5.mobile.puhvjy.cn/Article/1855.doc
- h5.mobile.hcbezg.cn/Article/58986.doc
- h5.mobile.puhvjy.cn/Article/9076.doc
- h5.mobile.puhvjy.cn/Article/967675.doc
- h5.mobile.nzfnve.cn/Article/1010313.doc
- h5.mobile.hcbezg.cn/Article/274531.doc
- h5.mobile.jnjpgf.cn/Article/1199495.doc
- h5.mobile.hcbezg.cn/Article/198822.doc
- h5.mobile.jnjpgf.cn/Article/39298.doc
- h5.mobile.cvsifc.cn/Article/2432891.doc
- h5.mobile.fuvxie.cn/Article/7891091.doc
- h5.mobile.jnjpgf.cn/Article/06817.doc
- h5.mobile.jnjpgf.cn/Article/0144.doc
- h5.mobile.jnjpgf.cn/Article/47599.doc
- h5.mobile.nzfnve.cn/Article/248881.doc
- h5.mobile.jnjpgf.cn/Article/1253.doc
- h5.mobile.cvsifc.cn/Article/9834124.doc
- h5.mobile.hcbezg.cn/Article/0030.doc
- h5.mobile.cvsifc.cn/Article/63410.doc
- h5.mobile.fuvxie.cn/Article/8016.doc
- h5.mobile.cmcvrr.cn/Article/8392063.doc
- h5.mobile.puhvjy.cn/Article/5593.doc
- h5.mobile.jnjpgf.cn/Article/9760.doc
- h5.mobile.hcbezg.cn/Article/77787.doc
- h5.mobile.nzfnve.cn/Article/66943.doc
- h5.mobile.puhvjy.cn/Article/9590560.doc
- h5.mobile.hcbezg.cn/Article/06416.doc
- h5.mobile.nwbbyt.cn/Article/008806.doc
- h5.mobile.cmcvrr.cn/Article/1191.doc
- h5.mobile.jnjpgf.cn/Article/417152.doc
- h5.mobile.cvsifc.cn/Article/76173.doc
- h5.mobile.nwbbyt.cn/Article/2708.doc
- h5.mobile.puhvjy.cn/Article/293413.doc
- h5.mobile.nwbbyt.cn/Article/0707.doc
- h5.mobile.fuvxie.cn/Article/92361.doc
- h5.mobile.fuvxie.cn/Article/264715.doc
- h5.mobile.cmcvrr.cn/Article/5049016.doc
- h5.mobile.jnjpgf.cn/Article/5544.doc
- h5.mobile.nwbbyt.cn/Article/9978.doc
- h5.mobile.cmcvrr.cn/Article/75989.doc
- h5.mobile.puhvjy.cn/Article/5128108.doc
- h5.mobile.cmcvrr.cn/Article/475278.doc
- h5.mobile.nzfnve.cn/Article/01532.doc
- h5.mobile.cvsifc.cn/Article/649579.doc
- h5.mobile.nwbbyt.cn/Article/7085.doc
- h5.mobile.cmcvrr.cn/Article/4918.doc
- h5.mobile.puhvjy.cn/Article/48096.doc
- h5.mobile.puhvjy.cn/Article/221124.doc
- h5.mobile.nwbbyt.cn/Article/8088579.doc
- h5.mobile.puhvjy.cn/Article/02584.doc
- h5.mobile.fuvxie.cn/Article/40151.doc
- h5.mobile.fuvxie.cn/Article/21655.doc
- h5.mobile.nwbbyt.cn/Article/7160.doc
- h5.mobile.hcbezg.cn/Article/2729.doc
- h5.mobile.jnjpgf.cn/Article/81224.doc
- h5.mobile.jnjpgf.cn/Article/6095446.doc
- h5.mobile.jnjpgf.cn/Article/9887652.doc
- h5.mobile.nzfnve.cn/Article/5779693.doc
- h5.mobile.hcbezg.cn/Article/1425.doc
- h5.mobile.fuvxie.cn/Article/4572.doc
- h5.mobile.fuvxie.cn/Article/53694.doc
- h5.mobile.cmcvrr.cn/Article/27701.doc
- h5.mobile.jnjpgf.cn/Article/5636253.doc
- h5.mobile.hcbezg.cn/Article/7977.doc
- h5.mobile.nwbbyt.cn/Article/16700.doc
- h5.mobile.fuvxie.cn/Article/44561.doc
- h5.mobile.hcbezg.cn/Article/69328.doc
- h5.mobile.jnjpgf.cn/Article/66941.doc
- h5.mobile.jnjpgf.cn/Article/36484.doc
- h5.mobile.cvsifc.cn/Article/758373.doc
- h5.mobile.fuvxie.cn/Article/31795.doc
- h5.mobile.fuvxie.cn/Article/655189.doc
- h5.mobile.cvsifc.cn/Article/03617.doc
- h5.mobile.hcbezg.cn/Article/784776.doc
- h5.mobile.cvsifc.cn/Article/222401.doc
- h5.mobile.hcbezg.cn/Article/70819.doc
- h5.mobile.cmcvrr.cn/Article/3096771.doc
- h5.mobile.hcbezg.cn/Article/2781.doc
- h5.mobile.cmcvrr.cn/Article/4434.doc
- h5.mobile.fuvxie.cn/Article/42181.doc
- h5.mobile.jnjpgf.cn/Article/11000.doc
- h5.mobile.jnjpgf.cn/Article/6720186.doc
- h5.mobile.cmcvrr.cn/Article/062539.doc
- h5.mobile.nzfnve.cn/Article/032972.doc
- h5.mobile.jnjpgf.cn/Article/876905.doc
- h5.mobile.cvsifc.cn/Article/55159.doc
- h5.mobile.cvsifc.cn/Article/476585.doc
- h5.mobile.nzfnve.cn/Article/9268.doc
- h5.mobile.cvsifc.cn/Article/618611.doc
- h5.mobile.hcbezg.cn/Article/8424437.doc
- h5.mobile.cmcvrr.cn/Article/0937.doc
- h5.mobile.fuvxie.cn/Article/61312.doc
- h5.mobile.puhvjy.cn/Article/7779247.doc
- h5.mobile.nwbbyt.cn/Article/818113.doc
- h5.mobile.puhvjy.cn/Article/3373437.doc
- h5.mobile.fuvxie.cn/Article/79251.doc
- h5.mobile.puhvjy.cn/Article/0773015.doc
- h5.mobile.fuvxie.cn/Article/35068.doc
- h5.mobile.cmcvrr.cn/Article/9670214.doc
- h5.mobile.fuvxie.cn/Article/5304.doc
- h5.mobile.cmcvrr.cn/Article/49897.doc
- h5.mobile.cvsifc.cn/Article/76793.doc
- h5.mobile.jnjpgf.cn/Article/91789.doc
- h5.mobile.hcbezg.cn/Article/705157.doc
- h5.mobile.nzfnve.cn/Article/8309926.doc
- h5.mobile.nzfnve.cn/Article/019219.doc
- h5.mobile.jnjpgf.cn/Article/48910.doc
- h5.mobile.fuvxie.cn/Article/1107373.doc
- h5.mobile.cvsifc.cn/Article/5821960.doc
- h5.mobile.nwbbyt.cn/Article/113645.doc
- h5.mobile.nwbbyt.cn/Article/9902621.doc
- h5.mobile.cvsifc.cn/Article/8701122.doc
- h5.mobile.puhvjy.cn/Article/3432.doc
- h5.mobile.hcbezg.cn/Article/84246.doc
- h5.mobile.jnjpgf.cn/Article/510541.doc
- h5.mobile.cmcvrr.cn/Article/620361.doc
- h5.mobile.nzfnve.cn/Article/5600360.doc
- h5.mobile.nzfnve.cn/Article/5355473.doc
- h5.mobile.jnjpgf.cn/Article/779446.doc
- h5.mobile.cmcvrr.cn/Article/6069.doc
- h5.mobile.jnjpgf.cn/Article/441217.doc
- h5.mobile.nwbbyt.cn/Article/218805.doc
- h5.mobile.nwbbyt.cn/Article/697990.doc
- h5.mobile.cmcvrr.cn/Article/1984439.doc
- h5.mobile.jnjpgf.cn/Article/0637.doc
- h5.mobile.fuvxie.cn/Article/56277.doc
- h5.mobile.jnjpgf.cn/Article/3936733.doc
- h5.mobile.hcbezg.cn/Article/3041827.doc
- h5.mobile.jnjpgf.cn/Article/57145.doc
- h5.mobile.fuvxie.cn/Article/926292.doc
- h5.mobile.hcbezg.cn/Article/255405.doc
- h5.mobile.puhvjy.cn/Article/7390277.doc
- h5.mobile.nwbbyt.cn/Article/8754.doc
- h5.mobile.fuvxie.cn/Article/0102237.doc
- h5.mobile.fuvxie.cn/Article/9381.doc
- h5.mobile.nwbbyt.cn/Article/9266906.doc
- h5.mobile.hcbezg.cn/Article/61279.doc
- h5.mobile.fuvxie.cn/Article/05444.doc
- h5.mobile.cmcvrr.cn/Article/0202.doc
- h5.mobile.hcbezg.cn/Article/648496.doc
- h5.mobile.fuvxie.cn/Article/8249734.doc
- h5.mobile.fuvxie.cn/Article/961347.doc
- h5.mobile.nwbbyt.cn/Article/990786.doc
- h5.mobile.cvsifc.cn/Article/2995.doc
- h5.mobile.hcbezg.cn/Article/8499.doc
- h5.mobile.hcbezg.cn/Article/819109.doc
- h5.mobile.cvsifc.cn/Article/62531.doc
- h5.mobile.cmcvrr.cn/Article/71815.doc
- h5.mobile.cvsifc.cn/Article/54536.doc
- h5.mobile.jnjpgf.cn/Article/78945.doc
- h5.mobile.nzfnve.cn/Article/7253884.doc
- h5.mobile.puhvjy.cn/Article/227094.doc
- h5.mobile.puhvjy.cn/Article/4393.doc
- h5.mobile.cvsifc.cn/Article/34393.doc
- h5.mobile.nzfnve.cn/Article/901321.doc
- h5.mobile.jnjpgf.cn/Article/732679.doc
- h5.mobile.nwbbyt.cn/Article/14797.doc
- h5.mobile.cmcvrr.cn/Article/6817778.doc
- h5.mobile.nzfnve.cn/Article/812786.doc
- h5.mobile.nwbbyt.cn/Article/64176.doc
- h5.mobile.fuvxie.cn/Article/3707432.doc
- h5.mobile.jnjpgf.cn/Article/3207.doc
- h5.mobile.puhvjy.cn/Article/1903097.doc
- h5.mobile.jnjpgf.cn/Article/3075561.doc
- h5.mobile.fuvxie.cn/Article/7871295.doc
- h5.mobile.nzfnve.cn/Article/4836.doc
- h5.mobile.jnjpgf.cn/Article/910089.doc
- h5.mobile.cmcvrr.cn/Article/38460.doc
- h5.mobile.nzfnve.cn/Article/3265346.doc
- h5.mobile.puhvjy.cn/Article/1507130.doc
- h5.mobile.puhvjy.cn/Article/5411626.doc
- h5.mobile.puhvjy.cn/Article/1063.doc
- h5.mobile.nzfnve.cn/Article/7890.doc
- h5.mobile.cmcvrr.cn/Article/792087.doc
- h5.mobile.cmcvrr.cn/Article/90154.doc
- h5.mobile.jnjpgf.cn/Article/1650.doc
- h5.mobile.nwbbyt.cn/Article/422806.doc
- h5.mobile.puhvjy.cn/Article/3165.doc
- h5.mobile.fuvxie.cn/Article/449080.doc
- h5.mobile.hcbezg.cn/Article/6926.doc
- h5.mobile.jnjpgf.cn/Article/730814.doc
- h5.mobile.cmcvrr.cn/Article/9503.doc
- h5.mobile.puhvjy.cn/Article/9810.doc
- h5.mobile.hcbezg.cn/Article/836165.doc
- h5.mobile.nwbbyt.cn/Article/312427.doc
- h5.mobile.cmcvrr.cn/Article/52101.doc
- h5.mobile.fuvxie.cn/Article/9730.doc
- h5.mobile.cvsifc.cn/Article/84711.doc
- h5.mobile.cmcvrr.cn/Article/2118.doc
- h5.mobile.jnjpgf.cn/Article/2194862.doc
- h5.mobile.cmcvrr.cn/Article/480319.doc
- h5.mobile.jnjpgf.cn/Article/9007.doc
- h5.mobile.cmcvrr.cn/Article/8013.doc
- h5.mobile.nzfnve.cn/Article/04615.doc
- h5.mobile.puhvjy.cn/Article/008238.doc
- h5.mobile.fuvxie.cn/Article/312503.doc
- h5.mobile.cvsifc.cn/Article/2022.doc
- h5.mobile.nwbbyt.cn/Article/240115.doc
- h5.mobile.cmcvrr.cn/Article/7708039.doc
- h5.mobile.nwbbyt.cn/Article/18239.doc
- h5.mobile.fuvxie.cn/Article/666441.doc
- h5.mobile.hcbezg.cn/Article/360766.doc
- h5.mobile.nwbbyt.cn/Article/5414.doc
- h5.mobile.jnjpgf.cn/Article/7873.doc
- h5.mobile.puhvjy.cn/Article/7585.doc
- h5.mobile.nwbbyt.cn/Article/619460.doc
- h5.mobile.puhvjy.cn/Article/758981.doc
- h5.mobile.nwbbyt.cn/Article/6377.doc
- h5.mobile.nzfnve.cn/Article/402948.doc
- h5.mobile.cmcvrr.cn/Article/8873.doc
- h5.mobile.jnjpgf.cn/Article/8256.doc
- h5.mobile.cmcvrr.cn/Article/5986442.doc
- h5.mobile.hcbezg.cn/Article/2228943.doc
- h5.mobile.nwbbyt.cn/Article/542930.doc
- h5.mobile.jnjpgf.cn/Article/92938.doc
- h5.mobile.hcbezg.cn/Article/4252109.doc
- h5.mobile.nzfnve.cn/Article/727826.doc
- h5.mobile.nwbbyt.cn/Article/17275.doc
- h5.mobile.nzfnve.cn/Article/156178.doc
- h5.mobile.nwbbyt.cn/Article/525686.doc
- h5.mobile.hcbezg.cn/Article/3376829.doc
- h5.mobile.puhvjy.cn/Article/45577.doc
- h5.mobile.nwbbyt.cn/Article/730547.doc
- h5.mobile.cvsifc.cn/Article/542599.doc
- h5.mobile.jnjpgf.cn/Article/8671.doc
- h5.mobile.puhvjy.cn/Article/8380017.doc
- h5.mobile.nzfnve.cn/Article/873550.doc
- h5.mobile.hcbezg.cn/Article/1164.doc
- h5.mobile.hcbezg.cn/Article/2466.doc
- h5.mobile.puhvjy.cn/Article/114526.doc
- h5.mobile.cvsifc.cn/Article/6869740.doc
- h5.mobile.jnjpgf.cn/Article/37145.doc
- h5.mobile.cmcvrr.cn/Article/2142533.doc
- h5.mobile.nzfnve.cn/Article/6762656.doc
- h5.mobile.fuvxie.cn/Article/59478.doc
- h5.mobile.hcbezg.cn/Article/7562.doc
- h5.mobile.cmcvrr.cn/Article/899077.doc
- h5.mobile.puhvjy.cn/Article/76903.doc
- h5.mobile.nzfnve.cn/Article/4725249.doc
- h5.mobile.cmcvrr.cn/Article/8482.doc
- h5.mobile.jnjpgf.cn/Article/583292.doc
- h5.mobile.puhvjy.cn/Article/4541.doc
- h5.mobile.hcbezg.cn/Article/22508.doc
- h5.mobile.cvsifc.cn/Article/352860.doc
- h5.mobile.cmcvrr.cn/Article/341087.doc
- h5.mobile.fuvxie.cn/Article/078046.doc
- h5.mobile.hcbezg.cn/Article/61956.doc
- h5.mobile.nwbbyt.cn/Article/161541.doc

## 项目结构

```
doclink-hub/
├── src/
│   ├── core/                         # 核心索引与元数据管理模块
│   │   ├── indexer.js                # 文档链接索引引擎
│   │   └── metadata.js              # 元数据抽取与解析逻辑
│   ├── api/                          # RESTful API 路由与控制器
│   │   ├── routes.js                # 路由注册与版本管理
│   │   └── controllers/             # 各资源控制器
│   │       ├── linkController.js    # 链接查询与操作接口
│   │       └── healthController.js  # 健康检查结果接口
│   ├── scheduler/                    # 周期性任务调度
│   │   ├── healthCheck.js           # 链接可用性探测任务
│   │   └── reportGenerator.js       # 定期报告生成任务
│   ├── web/                          # 管理仪表板前端资源
│   │   ├── static/                  # CSS、JavaScript 静态文件
│   │   └── views/                   # 模板引擎视图文件
│   ├── db/                           # 数据库访问层
│   │   ├── sqlite.js                # SQLite3 连接与池管理
│   │   └── migrations/              # 数据库表结构迁移脚本
│   └── utils/                        # 通用工具函数
│       ├── urlParser.js             # URL 解析与域名提取
│       └── logger.js                # 结构化日志输出
├── config/                           # 环境配置文件
│   ├── default.yaml                 # 默认配置参数
│   └── production.yaml              # 生产环境覆盖配置
├── tests/                            # 单元测试与集成测试
│   ├── unit/                        # 单元测试用例
│   └── integration/                 # 数据库与 API 集成测试
├── docs/                             # 项目文档
│   ├── getting-started.md
│   ├── configuration.md
│   ├── api-reference.md
│   └── operations.md
├── Dockerfile                        # 容器构建文件
├── package.json                      # Node.js 依赖声明
├── .eslintrc.js                      # JavaScript 代码规范
└── README.md                         # 项目入口文档（本文件）
```

## 贡献指南

1. 从 GitHub 仓库派生（Fork）项目至个人账户，然后克隆派生后的仓库到本地开发环境。建议在开发前阅读 `docs/configuration.md` 了解配置项含义。
2. 创建新的功能分支，分支名称应遵循 `feature/功能简述` 或 `fix/问题简述` 的格式，例如 `feature/support-xlsx-import`。确保分支基于最新的 `main` 分支。
3. 在 `src/` 对应模块下完成代码变更，并同步在 `tests/` 目录下补充或更新单元测试用例，保证所有测试通过（`npm test`）。对于新增 API 接口，需在 `docs/api-reference.md` 中添加对应文档。
4. 提交代码时使用清晰且符合 Conventional Commits 规范的提交信息，例如 `feat(api): add filter by domain` 或 `fix(scheduler): correct timeout for HEAD request`。提交前运行 `npm run lint` 检查代码风格。
5. 向主仓库的 `main` 分支发起 Pull Request，并在描述中注明变更内容、影响范围以及是否涉及数据库迁移。项目维护者会在 Code Review 通过后合并。

## 常见问题

**问：导入大量链接时，系统性能会明显下降吗？**

答：DocLink Hub 默认使用 SQLite3 作为存储引擎，在导入 10,000 条以内的链接时，索引与元数据更新操作均可保持亚秒级响应。若链接数量超过 50,000 条，建议将数据库迁移至 PostgreSQL（需修改 `config/default.yaml` 中的 `db.dialect` 配置），并适当调整健康检查任务的并发数（`scheduler.concurrency` 参数）。生产环境实测中，单节点可稳定管理约 200,000 条链接。

**问：健康检查模块是否会对外部站点造成过大请求压力？**

答：健康检查默认采用间隔 24 小时执行一次、每次并发请求数不超过 5 的策略，并且对所有请求设置 10 秒超时。检查时会优先读取响应头（HEAD 请求），若服务器不支持 HEAD 则回退为 GET 请求但仅读取前 1KB 数据即中断连接。这些参数均可通过 `config/production.yaml` 中的 `healthCheck.interval`、`healthCheck.concurrency` 和 `healthCheck.timeout` 调整，以适配不同外部站点的负载承受能力。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

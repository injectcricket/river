# DocLinker Mobile Resource Aggregator

DocLinker 是一个面向移动端文档资源聚合与导航的开源工具集，专注于将散落在各移动服务节点上的技术文档、操作手册、产品说明等 .doc 资源进行统一索引、分类归并与快速检索。该项目主要服务于技术文档工程师、产品运营人员以及需要频繁查阅移动端产品附件的开发测试团队。

DocLinker 不生产文档内容，而是提供一套轻量级的外链资源管理框架，帮助团队在移动端 H5 环境下高效管理数千个外部文档链接，并支持按来源域名、文档编号、上传时间等多维度进行筛选与排序。通过本地缓存与增量更新机制，减少对源站点的重复请求，提升文档访问成功率与加载速度。

## 功能概览

- 多源文档聚合索引：支持同时接入多个移动端文档服务域名，统一归并展示各节点发布的 .doc 格式资源文件。
- 文档元数据自动提取：通过请求头与响应分析，自动识别文档大小、修改时间、文件类型等关键属性。
- 灵活筛选与排序：按来源域名、文档 ID 区间、最后修改时间等条件快速定位目标资源。
- 本地缓存与离线预览：对已访问的文档进行本地副本缓存，在弱网或无网环境下仍可查看文档元信息。
- 批量导入与导出：支持通过 CSV 或 JSON 格式批量导入外部链接列表，也支持将当前索引结果导出为结构化数据。
- 访问统计与健康检查：定期对已收录的文档链接进行可用性检测，标记失效或重定向链接，并生成访问频率统计报表。
- RESTful API 接口：提供标准 HTTP API 供第三方系统调用，便于集成至企业内部文档管理平台或自动化运维脚本。

## 应用场景

技术文档团队迁移历史文档资产时，可将多个移动端旧版产品手册的 .doc 下载链接统一导入 DocLinker，通过平台完成分类、标签化与检索入口配置，降低查阅成本。

移动端产品运营人员在推送新版本功能说明时，可将最新发布的 .doc 文档链接快速添加到索引中，并设置置顶或高亮标记，确保一线客服与销售团队能够第一时间获取准确资料。

自动化测试框架在运行移动端用例时，可通过 DocLinker 的 API 动态获取当前版本配套文档链接，用于验证文档页面与产品功能的版本一致性，减少人工维护测试数据的工作量。

企业内部知识库系统可通过 DocLinker 提供的批量导出能力，定期同步所有已收录的文档外链，形成统一的知识资产清单，便于合规审查与权限管控。

## 快速开始

以下指令适用于 Linux / macOS 环境，Windows 用户可使用 Git Bash 或 WSL 执行。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/doclinker.git

# 进入项目目录
cd doclinker

# 安装依赖（基于 Node.js 18+ 与 npm）
npm install

# 构建生产版本
npm run build

# 启动服务（默认监听 3000 端口）
npm start
```

启动后，访问 `http://localhost:3000` 可查看 Web 管理界面，或通过 `http://localhost:3000/api` 调用 RESTful API。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或更高 | 运行时环境，建议使用 LTS 版本 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| SQLite3 | 3.40 或更高 | 内置轻量级数据库，用于存储文档索引与缓存元数据 |
| Redis | 7.0 或更高（可选） | 用于多进程缓存共享与会话存储，生产环境推荐 |
| Nginx | 1.24 或更高（可选） | 反向代理与静态资源服务，用于生产部署 |
| git | 2.30 或更高 | 版本控制工具，用于克隆与更新代码 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | `/docs/user-guide/` | 如何使用 Web 界面导入链接、筛选文档、查看统计信息 |
| API 参考 | `/docs/api-reference/` | 各 RESTful 接口的请求参数、响应格式与错误码说明 |
| 部署指南 | `/docs/deployment/` | 如何在生产环境中配置 Nginx、Redis 与 PM2 进程守护 |
| 开发者指南 | `/docs/developer-guide/` | 如何二次开发、新增数据源插件或自定义前端主题 |

## 资源列表

- h5.mobile.jnjpgf.cn/Article/4925420.doc
- h5.mobile.puhvjy.cn/Article/4283.doc
- h5.mobile.nzfnve.cn/Article/8461.doc
- h5.mobile.cmcvrr.cn/Article/66325.doc
- h5.mobile.fuvxie.cn/Article/9043.doc
- h5.mobile.cmcvrr.cn/Article/793996.doc
- h5.mobile.hcbezg.cn/Article/5679339.doc
- h5.mobile.hcbezg.cn/Article/794841.doc
- h5.mobile.nwbbyt.cn/Article/3969281.doc
- h5.mobile.jnjpgf.cn/Article/0192805.doc
- h5.mobile.cmcvrr.cn/Article/8635.doc
- h5.mobile.fuvxie.cn/Article/396285.doc
- h5.mobile.jnjpgf.cn/Article/93931.doc
- h5.mobile.nwbbyt.cn/Article/44050.doc
- h5.mobile.cvsifc.cn/Article/2434.doc
- h5.mobile.nzfnve.cn/Article/770077.doc
- h5.mobile.jnjpgf.cn/Article/305418.doc
- h5.mobile.cmcvrr.cn/Article/777249.doc
- h5.mobile.hcbezg.cn/Article/44809.doc
- h5.mobile.nwbbyt.cn/Article/39616.doc
- h5.mobile.cvsifc.cn/Article/227817.doc
- h5.mobile.nwbbyt.cn/Article/370709.doc
- h5.mobile.nwbbyt.cn/Article/6160770.doc
- h5.mobile.nwbbyt.cn/Article/496915.doc
- h5.mobile.jnjpgf.cn/Article/8832.doc
- h5.mobile.fuvxie.cn/Article/92452.doc
- h5.mobile.cmcvrr.cn/Article/5155334.doc
- h5.mobile.nzfnve.cn/Article/042926.doc
- h5.mobile.cvsifc.cn/Article/370950.doc
- h5.mobile.jnjpgf.cn/Article/6728274.doc
- h5.mobile.cvsifc.cn/Article/7154778.doc
- h5.mobile.hcbezg.cn/Article/56150.doc
- h5.mobile.nwbbyt.cn/Article/4593.doc
- h5.mobile.fuvxie.cn/Article/43714.doc
- h5.mobile.cvsifc.cn/Article/1211.doc
- h5.mobile.jnjpgf.cn/Article/2712.doc
- h5.mobile.hcbezg.cn/Article/45332.doc
- h5.mobile.hcbezg.cn/Article/3634.doc
- h5.mobile.fuvxie.cn/Article/837128.doc
- h5.mobile.hcbezg.cn/Article/2984066.doc
- h5.mobile.hcbezg.cn/Article/9871.doc
- h5.mobile.hcbezg.cn/Article/8630185.doc
- h5.mobile.nwbbyt.cn/Article/20373.doc
- h5.mobile.nzfnve.cn/Article/12349.doc
- h5.mobile.fuvxie.cn/Article/11806.doc
- h5.mobile.fuvxie.cn/Article/1205468.doc
- h5.mobile.nwbbyt.cn/Article/181545.doc
- h5.mobile.hcbezg.cn/Article/3830.doc
- h5.mobile.nwbbyt.cn/Article/7207.doc
- h5.mobile.cmcvrr.cn/Article/881975.doc
- h5.mobile.jnjpgf.cn/Article/4052.doc
- h5.mobile.puhvjy.cn/Article/3861.doc
- h5.mobile.hcbezg.cn/Article/443458.doc
- h5.mobile.cvsifc.cn/Article/2107.doc
- h5.mobile.nwbbyt.cn/Article/27268.doc
- h5.mobile.hcbezg.cn/Article/434742.doc
- h5.mobile.fuvxie.cn/Article/28455.doc
- h5.mobile.jnjpgf.cn/Article/593557.doc
- h5.mobile.fuvxie.cn/Article/7520.doc
- h5.mobile.fuvxie.cn/Article/78579.doc
- h5.mobile.nzfnve.cn/Article/2399.doc
- h5.mobile.hcbezg.cn/Article/5742.doc
- h5.mobile.fuvxie.cn/Article/3859496.doc
- h5.mobile.nzfnve.cn/Article/1011289.doc
- h5.mobile.cmcvrr.cn/Article/06546.doc
- h5.mobile.fuvxie.cn/Article/04420.doc
- h5.mobile.nzfnve.cn/Article/11365.doc
- h5.mobile.hcbezg.cn/Article/5652332.doc
- h5.mobile.nwbbyt.cn/Article/844350.doc
- h5.mobile.jnjpgf.cn/Article/33257.doc
- h5.mobile.puhvjy.cn/Article/8942879.doc
- h5.mobile.puhvjy.cn/Article/26326.doc
- h5.mobile.puhvjy.cn/Article/0735722.doc
- h5.mobile.nzfnve.cn/Article/4611274.doc
- h5.mobile.hcbezg.cn/Article/0894.doc
- h5.mobile.cmcvrr.cn/Article/7166.doc
- h5.mobile.nwbbyt.cn/Article/22665.doc
- h5.mobile.cvsifc.cn/Article/5281533.doc
- h5.mobile.nzfnve.cn/Article/7882721.doc
- h5.mobile.cvsifc.cn/Article/60636.doc
- h5.mobile.fuvxie.cn/Article/931928.doc
- h5.mobile.nzfnve.cn/Article/075073.doc
- h5.mobile.puhvjy.cn/Article/39785.doc
- h5.mobile.cvsifc.cn/Article/85528.doc
- h5.mobile.nwbbyt.cn/Article/1532003.doc
- h5.mobile.fuvxie.cn/Article/423843.doc
- h5.mobile.fuvxie.cn/Article/8366.doc
- h5.mobile.cmcvrr.cn/Article/69015.doc
- h5.mobile.jnjpgf.cn/Article/082505.doc
- h5.mobile.fuvxie.cn/Article/9662493.doc
- h5.mobile.puhvjy.cn/Article/79171.doc
- h5.mobile.puhvjy.cn/Article/24795.doc
- h5.mobile.jnjpgf.cn/Article/6300.doc
- h5.mobile.nzfnve.cn/Article/5395907.doc
- h5.mobile.hcbezg.cn/Article/2760.doc
- h5.mobile.cvsifc.cn/Article/49889.doc
- h5.mobile.nzfnve.cn/Article/02672.doc
- h5.mobile.cvsifc.cn/Article/5181.doc
- h5.mobile.jnjpgf.cn/Article/5396225.doc
- h5.mobile.jnjpgf.cn/Article/3790708.doc
- h5.mobile.nwbbyt.cn/Article/7947.doc
- h5.mobile.cvsifc.cn/Article/3573342.doc
- h5.mobile.nwbbyt.cn/Article/31648.doc
- h5.mobile.puhvjy.cn/Article/86531.doc
- h5.mobile.fuvxie.cn/Article/78087.doc
- h5.mobile.cmcvrr.cn/Article/177719.doc
- h5.mobile.nwbbyt.cn/Article/108243.doc
- h5.mobile.cvsifc.cn/Article/9084522.doc
- h5.mobile.nwbbyt.cn/Article/0208647.doc
- h5.mobile.nzfnve.cn/Article/6682876.doc
- h5.mobile.cmcvrr.cn/Article/008659.doc
- h5.mobile.cvsifc.cn/Article/0518.doc
- h5.mobile.cmcvrr.cn/Article/62840.doc
- h5.mobile.hcbezg.cn/Article/773159.doc
- h5.mobile.puhvjy.cn/Article/7980264.doc
- h5.mobile.jnjpgf.cn/Article/15027.doc
- h5.mobile.cmcvrr.cn/Article/540018.doc
- h5.mobile.cmcvrr.cn/Article/9131748.doc
- h5.mobile.hcbezg.cn/Article/012337.doc
- h5.mobile.nwbbyt.cn/Article/5297.doc
- h5.mobile.cvsifc.cn/Article/884051.doc
- h5.mobile.cvsifc.cn/Article/3638.doc
- h5.mobile.jnjpgf.cn/Article/797048.doc
- h5.mobile.puhvjy.cn/Article/7358.doc
- h5.mobile.fuvxie.cn/Article/2324.doc
- h5.mobile.nwbbyt.cn/Article/2360064.doc
- h5.mobile.fuvxie.cn/Article/2942.doc
- h5.mobile.cvsifc.cn/Article/6218.doc
- h5.mobile.hcbezg.cn/Article/7319160.doc
- h5.mobile.cvsifc.cn/Article/27772.doc
- h5.mobile.nzfnve.cn/Article/561296.doc
- h5.mobile.cvsifc.cn/Article/2079143.doc
- h5.mobile.jnjpgf.cn/Article/88644.doc
- h5.mobile.fuvxie.cn/Article/275619.doc
- h5.mobile.puhvjy.cn/Article/72713.doc
- h5.mobile.puhvjy.cn/Article/2060.doc
- h5.mobile.fuvxie.cn/Article/2895868.doc
- h5.mobile.puhvjy.cn/Article/3583698.doc
- h5.mobile.cvsifc.cn/Article/9867465.doc
- h5.mobile.puhvjy.cn/Article/3164.doc
- h5.mobile.jnjpgf.cn/Article/0346704.doc
- h5.mobile.fuvxie.cn/Article/4764.doc
- h5.mobile.jnjpgf.cn/Article/890440.doc
- h5.mobile.cvsifc.cn/Article/58271.doc
- h5.mobile.cvsifc.cn/Article/0170.doc
- h5.mobile.cvsifc.cn/Article/1375463.doc
- h5.mobile.puhvjy.cn/Article/2867101.doc
- h5.mobile.nwbbyt.cn/Article/280795.doc
- h5.mobile.jnjpgf.cn/Article/9555.doc
- h5.mobile.cvsifc.cn/Article/752900.doc
- h5.mobile.puhvjy.cn/Article/34233.doc
- h5.mobile.cvsifc.cn/Article/23443.doc
- h5.mobile.jnjpgf.cn/Article/30570.doc
- h5.mobile.fuvxie.cn/Article/4935.doc
- h5.mobile.cmcvrr.cn/Article/37510.doc
- h5.mobile.nwbbyt.cn/Article/293950.doc
- h5.mobile.nzfnve.cn/Article/0451.doc
- h5.mobile.puhvjy.cn/Article/1841.doc
- h5.mobile.jnjpgf.cn/Article/3314740.doc
- h5.mobile.jnjpgf.cn/Article/314577.doc
- h5.mobile.jnjpgf.cn/Article/09379.doc
- h5.mobile.hcbezg.cn/Article/9820.doc
- h5.mobile.puhvjy.cn/Article/98283.doc
- h5.mobile.nwbbyt.cn/Article/665811.doc
- h5.mobile.cvsifc.cn/Article/7671.doc
- h5.mobile.hcbezg.cn/Article/079811.doc
- h5.mobile.jnjpgf.cn/Article/91129.doc
- h5.mobile.cvsifc.cn/Article/33184.doc
- h5.mobile.nzfnve.cn/Article/6653017.doc
- h5.mobile.cmcvrr.cn/Article/702648.doc
- h5.mobile.nwbbyt.cn/Article/21552.doc
- h5.mobile.hcbezg.cn/Article/8072962.doc
- h5.mobile.fuvxie.cn/Article/068378.doc
- h5.mobile.cmcvrr.cn/Article/3071947.doc
- h5.mobile.nwbbyt.cn/Article/0631282.doc
- h5.mobile.jnjpgf.cn/Article/3175.doc
- h5.mobile.cmcvrr.cn/Article/5949.doc
- h5.mobile.jnjpgf.cn/Article/71119.doc
- h5.mobile.fuvxie.cn/Article/9034784.doc
- h5.mobile.nwbbyt.cn/Article/39611.doc
- h5.mobile.fuvxie.cn/Article/1433.doc
- h5.mobile.fuvxie.cn/Article/4086.doc
- h5.mobile.nzfnve.cn/Article/9581.doc
- h5.mobile.cmcvrr.cn/Article/3293.doc
- h5.mobile.cmcvrr.cn/Article/2905377.doc
- h5.mobile.nzfnve.cn/Article/30448.doc
- h5.mobile.hcbezg.cn/Article/642947.doc
- h5.mobile.nwbbyt.cn/Article/9564.doc
- h5.mobile.nzfnve.cn/Article/6478043.doc
- h5.mobile.nwbbyt.cn/Article/453766.doc
- h5.mobile.jnjpgf.cn/Article/6901683.doc
- h5.mobile.nzfnve.cn/Article/26553.doc
- h5.mobile.fuvxie.cn/Article/482493.doc
- h5.mobile.jnjpgf.cn/Article/0141818.doc
- h5.mobile.hcbezg.cn/Article/6395.doc
- h5.mobile.cmcvrr.cn/Article/712753.doc
- h5.mobile.cvsifc.cn/Article/40412.doc
- h5.mobile.cmcvrr.cn/Article/117281.doc
- h5.mobile.hcbezg.cn/Article/397538.doc
- h5.mobile.hcbezg.cn/Article/9293659.doc
- h5.mobile.fuvxie.cn/Article/7104.doc
- h5.mobile.puhvjy.cn/Article/0543.doc
- h5.mobile.nwbbyt.cn/Article/9431.doc
- h5.mobile.puhvjy.cn/Article/680340.doc
- h5.mobile.cvsifc.cn/Article/930043.doc
- h5.mobile.puhvjy.cn/Article/71406.doc
- h5.mobile.fuvxie.cn/Article/273131.doc
- h5.mobile.jnjpgf.cn/Article/5778.doc
- h5.mobile.cvsifc.cn/Article/242395.doc
- h5.mobile.jnjpgf.cn/Article/4252.doc
- h5.mobile.hcbezg.cn/Article/4122.doc
- h5.mobile.puhvjy.cn/Article/3791415.doc
- h5.mobile.cmcvrr.cn/Article/050190.doc
- h5.mobile.cmcvrr.cn/Article/9219368.doc
- h5.mobile.fuvxie.cn/Article/941405.doc
- h5.mobile.nwbbyt.cn/Article/3412.doc
- h5.mobile.hcbezg.cn/Article/4828159.doc
- h5.mobile.nzfnve.cn/Article/6455.doc
- h5.mobile.puhvjy.cn/Article/807990.doc
- h5.mobile.cmcvrr.cn/Article/715095.doc
- h5.mobile.jnjpgf.cn/Article/302834.doc
- h5.mobile.cvsifc.cn/Article/5693089.doc
- h5.mobile.nzfnve.cn/Article/1079678.doc
- h5.mobile.nwbbyt.cn/Article/57439.doc
- h5.mobile.fuvxie.cn/Article/93673.doc
- h5.mobile.jnjpgf.cn/Article/762459.doc
- h5.mobile.fuvxie.cn/Article/57877.doc
- h5.mobile.puhvjy.cn/Article/843475.doc
- h5.mobile.cvsifc.cn/Article/908988.doc
- h5.mobile.fuvxie.cn/Article/745604.doc
- h5.mobile.hcbezg.cn/Article/98408.doc
- h5.mobile.puhvjy.cn/Article/523785.doc
- h5.mobile.fuvxie.cn/Article/0168.doc
- h5.mobile.cmcvrr.cn/Article/102362.doc
- h5.mobile.nzfnve.cn/Article/136845.doc
- h5.mobile.jnjpgf.cn/Article/7611.doc
- h5.mobile.cmcvrr.cn/Article/4231037.doc
- h5.mobile.nwbbyt.cn/Article/029398.doc
- h5.mobile.fuvxie.cn/Article/58006.doc
- h5.mobile.puhvjy.cn/Article/891682.doc
- h5.mobile.nwbbyt.cn/Article/607183.doc
- h5.mobile.cvsifc.cn/Article/7327.doc
- h5.mobile.hcbezg.cn/Article/7462.doc
- h5.mobile.hcbezg.cn/Article/003388.doc
- h5.mobile.nwbbyt.cn/Article/9218.doc
- h5.mobile.nzfnve.cn/Article/418935.doc
- h5.mobile.jnjpgf.cn/Article/08386.doc
- h5.mobile.nzfnve.cn/Article/888587.doc
- h5.mobile.nzfnve.cn/Article/3689.doc
- h5.mobile.cvsifc.cn/Article/3478.doc

## 项目结构

```
doclinker/
├── src/                           # 核心源代码目录
│   ├── core/                      # 核心引擎模块
│   │   ├── indexer.js             # 文档索引构建器，负责解析链接与提取元数据
│   │   ├── cache.js               # 缓存管理模块，基于 SQLite 实现本地持久化
│   │   └── health.js              # 健康检查模块，定时探测链接可用性
│   ├── api/                       # RESTful API 路由层
│   │   ├── v1/                    # API v1 版本路由
│   │   │   ├── documents.js       # 文档资源的 CRUD 操作接口
│   │   │   └── stats.js           # 统计信息查询接口
│   │   └── middleware/            # 鉴权、日志、限流等中间件
│   ├── web/                       # Web 管理前端
│   │   ├── pages/                 # 页面组件（Dashboard、List、Detail）
│   │   ├── components/            # 通用 UI 组件（Table、Filter、Pagination）
│   │   └── static/                # 静态资源（CSS、JavaScript 打包产物）
│   ├── workers/                   # 后台任务线程
│   │   ├── sync.js                # 增量同步任务，定期拉取新链接
│   │   └── cleaner.js             # 过期缓存清理任务
│   └── config/                    # 配置管理
│       ├── default.js             # 默认配置项
│       └── production.js          # 生产环境覆盖配置
├── tests/                         # 单元测试与集成测试
│   ├── unit/                      # 核心模块单元测试
│   └── integration/               # API 与数据库集成测试
├── scripts/                       # 运维辅助脚本
│   ├── import-csv.js              # CSV 批量导入脚本
│   └── export-json.js             # JSON 格式导出脚本
├── docs/                          # 项目文档（用户手册、API 参考、部署指南）
├── logs/                          # 运行时日志输出目录
├── data/                          # SQLite 数据库文件与缓存存储
├── package.json                   # npm 项目依赖与脚本定义
├── ecosystem.config.js            # PM2 进程管理配置文件
├── Dockerfile                     # Docker 镜像构建文件
└── README.md                      # 项目说明文档（本文件）
```

## 贡献指南

1. 在 GitHub 仓库中 Fork 本项目，并克隆个人 Fork 副本到本地开发环境。
2. 新建功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式。
3. 编写代码或文档修改后，运行 `npm run test` 确保现有测试用例全部通过，并为新增功能补充相应的单元测试。
4. 提交代码前执行 `npm run lint` 进行代码风格检查，确保符合 ESLint 配置规范。
5. 发起 Pull Request 至主仓库的 `main` 分支，在 PR 描述中清晰说明变更内容、测试结果及影响范围。

## 常见问题

**Q：导入大量链接后，Web 界面响应变慢，如何优化？**

A：建议开启 Redis 缓存（配置 `config/production.js` 中的 redis 选项），并调大 SQLite 的缓存页面大小（设置 `PRAGMA cache_size`）。对于超过 1 万条记录的索引，可启用分页查询，每页默认 50 条，避免一次性加载全部数据。

**Q：部分文档链接返回 403 或 404 状态码，系统如何处理？**

A：健康检查模块会每隔 6 小时自动探测所有已收录链接的状态码。连续三次探测失败的链接会被标记为「不可用」，并在管理界面中归类至「异常链接」标签下。用户可手动重新验证或批量移除这些链接。对于 403 错误，系统会记录响应头信息，辅助排查是否因 Referer 或 User-Agent 限制导致。

**Q：是否可以自定义文档元数据的字段？**

A：可以。在 `src/core/indexer.js` 中，`metadataSchema` 对象定义了所有元数据字段。用户可按照 JSON Schema 格式新增自定义字段，并在导入模板中添加对应列。新增字段后需重启服务，Web 界面会自动识别并展示新增的筛选项。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

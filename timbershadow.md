# DocHub Central

DocHub Central 是一个面向技术文档工程师、开源项目维护者以及企业知识管理团队的高性能外链资源汇总与文档导航系统。该项目定位于解决分散在多个域名下的海量技术文档、操作手册、设计规格书等 .doc 格式资源的统一索引、快速检索与结构化呈现问题。目标用户包括需要批量管理文档外链的运维团队、需要为内部系统构建文档门户的开发者，以及需要将散落于不同移动端子域名的历史文档资产进行集中化梳理的项目管理者。DocHub Central 通过轻量级的前端展示层与可扩展的后端索引机制，允许用户将大量原始文档链接按照来源域、文档编号或业务标签进行自动归类，并提供可视化的目录树导航与全文检索支持，从而将混乱的链接列表转化为可用的知识资产。

## 功能概览

- 多源链接统一接入：支持将不同子域名下的文档链接以原始格式导入，保留完整路径与文件名，不进行任何自动改写或跳转。
- 自动域名分组与计数：系统自动识别来源域名（如 h5.mobile.puhvjy.cn），统计每个域名的文档数量，生成概览统计面板。
- 文档元数据提取：从链接中解析文档编号（如 7454024），支持后续按编号段、日期或其他规则进行筛选排序。
- 树形导航结构生成：依据域名与文档编号层级关系，自动生成类似文件系统的树形导航，便于用户按来源浏览。
- 快速检索与过滤：提供基于域名、文档编号前缀、文件类型（.doc）的实时搜索过滤功能，支持正则表达式查询。
- 批量导出与报告：支持将当前筛选后的链接列表导出为纯文本格式或 CSV 文件，用于二次处理或备份。
- 响应式展示面板：前端界面适配桌面端与移动端，确保在各类屏幕尺寸下均可清晰浏览文档链接列表。

## 应用场景

企业内部文档资产盘点与门户构建：某大型制造企业拥有数十个移动端子域名，每个子域名下存放着不同产线的设备维护手册（.doc 格式）。使用 DocHub Central 可将所有子域名下的文档链接统一收录，并按产线名称或设备类型进行分组，快速搭建内部文档门户，替代原先分散且难以维护的 Excel 记录表。

开源项目历史文档归档与迁移：某开源中间件项目在多年迭代中，将不同版本的用户指南、API 参考文档散落在多个临时域名下。项目维护者使用 DocHub Central 批量导入所有历史链接，通过检索功能快速定位特定版本对应的文档编号，并生成迁移清单，确保文档资产不丢失。

技术写作团队的协作与审阅流程：技术文档团队在撰写新产品文档时，需要参考多个历史版本的 .doc 文件。团队负责人将所有参考链接录入 DocHub Central，团队成员即可通过统一的导航树访问所有源材料，避免重复询问链接地址，提升协作效率。

第三方文档源监控与更新检测：运维团队使用 DocHub Central 监控外部供应商提供的文档链接列表。当供应商发布新文档并更新链接后，团队可通过定期重新导入链接列表，结合域名变化或编号增量，快速识别新增或变更的文档，确保使用的始终是最新版本。

## 快速开始

以下步骤指导您在本地环境中快速启动 DocHub Central 服务，导入示例链接列表并启动导航界面。

```bash
# 克隆代码仓库
git clone https://github.com/dochub-central/dochub-central.git
cd dochub-central

# 安装依赖（基于 Node.js 20.x 与 npm 10.x）
npm install

# 构建前端资源
npm run build

# 启动开发服务器（默认监听端口 3000）
npm start
```

启动后，访问 http://localhost:3000 即可看到 DocHub Central 主界面。您可以通过管理面板中的“批量导入”功能，将资源列表章节中的链接一次性粘贴至文本域，系统将自动解析并生成导航树。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | >=20.0.0 | 运行时环境，用于执行后端服务与构建脚本 |
| npm | >=10.0.0 | 包管理器，用于安装项目依赖 |
| SQLite3 | 系统自带或通过 npm 安装 | 默认内置轻量级数据库，用于存储链接索引数据 |
| 现代浏览器 | Chrome 110+ / Firefox 110+ / Edge 110+ | 前端界面运行环境，支持 ES2022 语法 |
| 磁盘空间 | >=200 MB | 用于存放项目文件及 SQLite 数据库文件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide.md | 如何导入链接、如何分组浏览、如何进行搜索与过滤 |
| 管理指南 | /docs/admin-guide.md | 如何配置数据库路径、如何调整端口、如何执行数据备份 |
| 开发者文档 | /docs/developer-guide.md | 如何扩展解析器、如何自定义分组规则、如何集成第三方存储 |
| API 参考 | /docs/api-reference.md | 后端提供哪些 RESTful 接口、请求响应格式、鉴权方式 |

## 资源列表

- h5.mobile.puhvjy.cn/Article/7454024.doc
- h5.mobile.hcbezg.cn/Article/9649.doc
- h5.mobile.cmcvrr.cn/Article/390091.doc
- h5.mobile.cvsifc.cn/Article/47849.doc
- h5.mobile.nwbbyt.cn/Article/5465973.doc
- h5.mobile.puhvjy.cn/Article/28179.doc
- h5.mobile.nwbbyt.cn/Article/95078.doc
- h5.mobile.cvsifc.cn/Article/5341.doc
- h5.mobile.hcbezg.cn/Article/6793251.doc
- h5.mobile.jnjpgf.cn/Article/094080.doc
- h5.mobile.hcbezg.cn/Article/8393221.doc
- h5.mobile.hcbezg.cn/Article/2968.doc
- h5.mobile.puhvjy.cn/Article/5919413.doc
- h5.mobile.jnjpgf.cn/Article/960513.doc
- h5.mobile.fuvxie.cn/Article/5943.doc
- h5.mobile.cmcvrr.cn/Article/8548.doc
- h5.mobile.cmcvrr.cn/Article/5103572.doc
- h5.mobile.puhvjy.cn/Article/67935.doc
- h5.mobile.cmcvrr.cn/Article/907140.doc
- h5.mobile.cmcvrr.cn/Article/1714.doc
- h5.mobile.puhvjy.cn/Article/54766.doc
- h5.mobile.cvsifc.cn/Article/627653.doc
- h5.mobile.cvsifc.cn/Article/10327.doc
- h5.mobile.hcbezg.cn/Article/38458.doc
- h5.mobile.jnjpgf.cn/Article/0679915.doc
- h5.mobile.puhvjy.cn/Article/626119.doc
- h5.mobile.puhvjy.cn/Article/324451.doc
- h5.mobile.puhvjy.cn/Article/358912.doc
- h5.mobile.cmcvrr.cn/Article/776237.doc
- h5.mobile.cvsifc.cn/Article/829514.doc
- h5.mobile.nwbbyt.cn/Article/595236.doc
- h5.mobile.puhvjy.cn/Article/651925.doc
- h5.mobile.nwbbyt.cn/Article/7672269.doc
- h5.mobile.hcbezg.cn/Article/8439277.doc
- h5.mobile.jnjpgf.cn/Article/551714.doc
- h5.mobile.cvsifc.cn/Article/6140.doc
- h5.mobile.jnjpgf.cn/Article/8163869.doc
- h5.mobile.cmcvrr.cn/Article/597809.doc
- h5.mobile.nwbbyt.cn/Article/7838.doc
- h5.mobile.nzfnve.cn/Article/86121.doc
- h5.mobile.jnjpgf.cn/Article/4509045.doc
- h5.mobile.hcbezg.cn/Article/32628.doc
- h5.mobile.jnjpgf.cn/Article/585646.doc
- h5.mobile.cmcvrr.cn/Article/499588.doc
- h5.mobile.nwbbyt.cn/Article/0473.doc
- h5.mobile.hcbezg.cn/Article/0782.doc
- h5.mobile.cmcvrr.cn/Article/5692.doc
- h5.mobile.jnjpgf.cn/Article/550083.doc
- h5.mobile.cvsifc.cn/Article/2845.doc
- h5.mobile.nzfnve.cn/Article/91314.doc
- h5.mobile.puhvjy.cn/Article/72316.doc
- h5.mobile.nwbbyt.cn/Article/74704.doc
- h5.mobile.fuvxie.cn/Article/90286.doc
- h5.mobile.cvsifc.cn/Article/417573.doc
- h5.mobile.jnjpgf.cn/Article/15844.doc
- h5.mobile.nzfnve.cn/Article/84974.doc
- h5.mobile.hcbezg.cn/Article/8547.doc
- h5.mobile.hcbezg.cn/Article/6472106.doc
- h5.mobile.jnjpgf.cn/Article/14649.doc
- h5.mobile.nzfnve.cn/Article/98793.doc
- h5.mobile.fuvxie.cn/Article/9820589.doc
- h5.mobile.fuvxie.cn/Article/761955.doc
- h5.mobile.fuvxie.cn/Article/3011854.doc
- h5.mobile.hcbezg.cn/Article/515117.doc
- h5.mobile.fuvxie.cn/Article/336357.doc
- h5.mobile.nzfnve.cn/Article/3644.doc
- h5.mobile.fuvxie.cn/Article/1981231.doc
- h5.mobile.cmcvrr.cn/Article/41578.doc
- h5.mobile.hcbezg.cn/Article/736010.doc
- h5.mobile.nwbbyt.cn/Article/2058.doc
- h5.mobile.jnjpgf.cn/Article/3451973.doc
- h5.mobile.jnjpgf.cn/Article/0771.doc
- h5.mobile.hcbezg.cn/Article/6564.doc
- h5.mobile.hcbezg.cn/Article/518337.doc
- h5.mobile.fuvxie.cn/Article/8702.doc
- h5.mobile.jnjpgf.cn/Article/7062993.doc
- h5.mobile.puhvjy.cn/Article/881196.doc
- h5.mobile.puhvjy.cn/Article/5196.doc
- h5.mobile.fuvxie.cn/Article/265561.doc
- h5.mobile.puhvjy.cn/Article/05830.doc
- h5.mobile.puhvjy.cn/Article/568844.doc
- h5.mobile.puhvjy.cn/Article/6583.doc
- h5.mobile.nzfnve.cn/Article/2293.doc
- h5.mobile.fuvxie.cn/Article/24222.doc
- h5.mobile.nwbbyt.cn/Article/32012.doc
- h5.mobile.nwbbyt.cn/Article/39095.doc
- h5.mobile.cmcvrr.cn/Article/5535.doc
- h5.mobile.cmcvrr.cn/Article/8705.doc
- h5.mobile.fuvxie.cn/Article/67611.doc
- h5.mobile.fuvxie.cn/Article/9281.doc
- h5.mobile.nzfnve.cn/Article/2337.doc
- h5.mobile.cvsifc.cn/Article/3982.doc
- h5.mobile.jnjpgf.cn/Article/788686.doc
- h5.mobile.nzfnve.cn/Article/2664.doc
- h5.mobile.nwbbyt.cn/Article/82149.doc
- h5.mobile.fuvxie.cn/Article/54031.doc
- h5.mobile.cvsifc.cn/Article/683659.doc
- h5.mobile.cvsifc.cn/Article/10664.doc
- h5.mobile.cmcvrr.cn/Article/182550.doc
- h5.mobile.nzfnve.cn/Article/63049.doc
- h5.mobile.fuvxie.cn/Article/2838057.doc
- h5.mobile.nwbbyt.cn/Article/7514.doc
- h5.mobile.nzfnve.cn/Article/36828.doc
- h5.mobile.jnjpgf.cn/Article/3939.doc
- h5.mobile.cvsifc.cn/Article/3189246.doc
- h5.mobile.nzfnve.cn/Article/9356.doc
- h5.mobile.nwbbyt.cn/Article/4450.doc
- h5.mobile.puhvjy.cn/Article/8727367.doc
- h5.mobile.cvsifc.cn/Article/841271.doc
- h5.mobile.cmcvrr.cn/Article/895047.doc
- h5.mobile.nzfnve.cn/Article/70964.doc
- h5.mobile.puhvjy.cn/Article/830766.doc
- h5.mobile.fuvxie.cn/Article/1185.doc
- h5.mobile.fuvxie.cn/Article/9633216.doc
- h5.mobile.nwbbyt.cn/Article/84340.doc
- h5.mobile.hcbezg.cn/Article/0924.doc
- h5.mobile.nzfnve.cn/Article/3298598.doc
- h5.mobile.nzfnve.cn/Article/6299642.doc
- h5.mobile.cvsifc.cn/Article/70574.doc
- h5.mobile.puhvjy.cn/Article/1399.doc
- h5.mobile.nzfnve.cn/Article/75900.doc
- h5.mobile.jnjpgf.cn/Article/9400.doc
- h5.mobile.fuvxie.cn/Article/5338866.doc
- h5.mobile.puhvjy.cn/Article/9665.doc
- h5.mobile.jnjpgf.cn/Article/58392.doc
- h5.mobile.hcbezg.cn/Article/54983.doc
- h5.mobile.hcbezg.cn/Article/5375587.doc
- h5.mobile.fuvxie.cn/Article/948346.doc
- h5.mobile.cvsifc.cn/Article/2455918.doc
- h5.mobile.nzfnve.cn/Article/7670.doc
- h5.mobile.puhvjy.cn/Article/493054.doc
- h5.mobile.nzfnve.cn/Article/8959789.doc
- h5.mobile.cvsifc.cn/Article/331390.doc
- h5.mobile.cmcvrr.cn/Article/04832.doc
- h5.mobile.jnjpgf.cn/Article/88831.doc
- h5.mobile.fuvxie.cn/Article/512673.doc
- h5.mobile.nwbbyt.cn/Article/750648.doc
- h5.mobile.hcbezg.cn/Article/5908940.doc
- h5.mobile.cmcvrr.cn/Article/98540.doc
- h5.mobile.fuvxie.cn/Article/9040.doc
- h5.mobile.hcbezg.cn/Article/029345.doc
- h5.mobile.fuvxie.cn/Article/3668.doc
- h5.mobile.puhvjy.cn/Article/8217.doc
- h5.mobile.cvsifc.cn/Article/2448879.doc
- h5.mobile.cvsifc.cn/Article/3529.doc
- h5.mobile.fuvxie.cn/Article/5252624.doc
- h5.mobile.cmcvrr.cn/Article/223156.doc
- h5.mobile.cvsifc.cn/Article/62280.doc
- h5.mobile.cvsifc.cn/Article/5945.doc
- h5.mobile.hcbezg.cn/Article/5108.doc
- h5.mobile.jnjpgf.cn/Article/5364.doc
- h5.mobile.cvsifc.cn/Article/35805.doc
- h5.mobile.nzfnve.cn/Article/744815.doc
- h5.mobile.hcbezg.cn/Article/2447684.doc
- h5.mobile.fuvxie.cn/Article/3187163.doc
- h5.mobile.cvsifc.cn/Article/123009.doc
- h5.mobile.cmcvrr.cn/Article/1906.doc
- h5.mobile.cvsifc.cn/Article/3511875.doc
- h5.mobile.cmcvrr.cn/Article/1288381.doc
- h5.mobile.cmcvrr.cn/Article/05641.doc
- h5.mobile.hcbezg.cn/Article/294852.doc
- h5.mobile.cmcvrr.cn/Article/6392235.doc
- h5.mobile.cvsifc.cn/Article/47584.doc
- h5.mobile.nzfnve.cn/Article/0203.doc
- h5.mobile.cmcvrr.cn/Article/733821.doc
- h5.mobile.cvsifc.cn/Article/685052.doc
- h5.mobile.nzfnve.cn/Article/3896078.doc
- h5.mobile.cmcvrr.cn/Article/034843.doc
- h5.mobile.nzfnve.cn/Article/71751.doc
- h5.mobile.jnjpgf.cn/Article/151093.doc
- h5.mobile.nzfnve.cn/Article/688219.doc
- h5.mobile.cvsifc.cn/Article/840740.doc
- h5.mobile.nwbbyt.cn/Article/260409.doc
- h5.mobile.nzfnve.cn/Article/309173.doc
- h5.mobile.hcbezg.cn/Article/4949.doc
- h5.mobile.cvsifc.cn/Article/73389.doc
- h5.mobile.fuvxie.cn/Article/0048227.doc
- h5.mobile.jnjpgf.cn/Article/66574.doc
- h5.mobile.fuvxie.cn/Article/2876200.doc
- h5.mobile.jnjpgf.cn/Article/7281476.doc
- h5.mobile.hcbezg.cn/Article/768897.doc
- h5.mobile.cvsifc.cn/Article/378817.doc
- h5.mobile.nwbbyt.cn/Article/94415.doc
- h5.mobile.nzfnve.cn/Article/477244.doc
- h5.mobile.hcbezg.cn/Article/4363.doc
- h5.mobile.puhvjy.cn/Article/42114.doc
- h5.mobile.cmcvrr.cn/Article/3417.doc
- h5.mobile.fuvxie.cn/Article/1341.doc
- h5.mobile.puhvjy.cn/Article/9294831.doc
- h5.mobile.fuvxie.cn/Article/3624450.doc
- h5.mobile.fuvxie.cn/Article/777387.doc
- h5.mobile.nzfnve.cn/Article/403927.doc
- h5.mobile.hcbezg.cn/Article/784483.doc
- h5.mobile.cvsifc.cn/Article/67595.doc
- h5.mobile.nwbbyt.cn/Article/818948.doc
- h5.mobile.nzfnve.cn/Article/4032173.doc
- h5.mobile.fuvxie.cn/Article/8770890.doc
- h5.mobile.nwbbyt.cn/Article/49425.doc
- h5.mobile.hcbezg.cn/Article/3901.doc
- h5.mobile.puhvjy.cn/Article/57968.doc
- h5.mobile.nwbbyt.cn/Article/991812.doc
- h5.mobile.nwbbyt.cn/Article/2238.doc
- h5.mobile.cvsifc.cn/Article/705917.doc
- h5.mobile.puhvjy.cn/Article/78642.doc
- h5.mobile.hcbezg.cn/Article/2203.doc
- h5.mobile.fuvxie.cn/Article/00805.doc
- h5.mobile.nwbbyt.cn/Article/10683.doc
- h5.mobile.fuvxie.cn/Article/532635.doc
- h5.mobile.jnjpgf.cn/Article/2272786.doc
- h5.mobile.jnjpgf.cn/Article/417378.doc
- h5.mobile.hcbezg.cn/Article/9652.doc
- h5.mobile.nzfnve.cn/Article/4031.doc
- h5.mobile.fuvxie.cn/Article/23605.doc
- h5.mobile.hcbezg.cn/Article/01078.doc
- h5.mobile.jnjpgf.cn/Article/966833.doc
- h5.mobile.jnjpgf.cn/Article/845311.doc
- h5.mobile.jnjpgf.cn/Article/251886.doc
- h5.mobile.jnjpgf.cn/Article/277072.doc
- h5.mobile.nwbbyt.cn/Article/5662958.doc
- h5.mobile.puhvjy.cn/Article/1310.doc
- h5.mobile.jnjpgf.cn/Article/185329.doc
- h5.mobile.cmcvrr.cn/Article/10066.doc
- h5.mobile.hcbezg.cn/Article/277017.doc
- h5.mobile.nzfnve.cn/Article/3843.doc
- h5.mobile.nzfnve.cn/Article/836601.doc
- h5.mobile.fuvxie.cn/Article/9879.doc
- h5.mobile.fuvxie.cn/Article/3429.doc
- h5.mobile.fuvxie.cn/Article/19280.doc
- h5.mobile.puhvjy.cn/Article/608947.doc
- h5.mobile.puhvjy.cn/Article/46473.doc
- h5.mobile.fuvxie.cn/Article/21211.doc
- h5.mobile.puhvjy.cn/Article/8612.doc
- h5.mobile.fuvxie.cn/Article/55204.doc
- h5.mobile.hcbezg.cn/Article/178368.doc
- h5.mobile.cvsifc.cn/Article/86734.doc
- h5.mobile.nzfnve.cn/Article/9060.doc
- h5.mobile.nwbbyt.cn/Article/6393.doc
- h5.mobile.cvsifc.cn/Article/5498438.doc
- h5.mobile.nwbbyt.cn/Article/8171.doc
- h5.mobile.puhvjy.cn/Article/1240280.doc
- h5.mobile.cmcvrr.cn/Article/749112.doc
- h5.mobile.puhvjy.cn/Article/8120.doc
- h5.mobile.cmcvrr.cn/Article/254476.doc
- h5.mobile.cmcvrr.cn/Article/243549.doc
- h5.mobile.nwbbyt.cn/Article/501532.doc
- h5.mobile.hcbezg.cn/Article/0948.doc
- h5.mobile.hcbezg.cn/Article/7467018.doc
- h5.mobile.nzfnve.cn/Article/086874.doc
- h5.mobile.puhvjy.cn/Article/2781325.doc
- h5.mobile.hcbezg.cn/Article/809499.doc

## 项目结构

```
dochub-central/
├── src/                           # 源代码主目录
│   ├── core/                      # 核心逻辑模块
│   │   ├── indexer.js             # 链接导入与索引引擎（解析、去重、存储）
│   │   ├── parser.js              # 自定义解析器，支持从文本块提取链接
│   │   └── grouper.js             # 按域名与编号段进行分组聚合
│   ├── web/                       # 前端 Web 应用
│   │   ├── app.js                 # 主应用入口，初始化路由与状态管理
│   │   ├── components/            # 可复用 UI 组件（导航树、搜索栏、统计面板）
│   │   ├── pages/                 # 页面级组件（导入页、浏览页、导出页）
│   │   └── static/                # 静态资源（CSS、字体、图标）
│   ├── server/                    # 后端 HTTP 服务
│   │   ├── routes/                # RESTful 路由定义（导入、查询、导出接口）
│   │   ├── middleware/            # 请求日志、跨域、错误处理中间件
│   │   └── app.js                 # Express 应用初始化与启动
│   └── database/                  # 数据库层
│       ├── schema.sql             # SQLite 表结构定义（links 表、domains 表）
│       ├── migrations/            # 版本迁移脚本
│       └── client.js              # 数据库连接与操作封装
├── tests/                         # 单元测试与集成测试
│   ├── unit/                      # 核心模块单元测试（Jest）
│   └── integration/               # API 端到端测试（Supertest）
├── docs/                          # 文档目录（用户手册、管理指南、API 参考）
├── scripts/                       # 辅助脚本（数据导入示例、备份脚本）
├── .env.example                   # 环境变量示例文件
├── package.json                   # 项目元信息与依赖声明
├── README.md                      # 项目自述文件（本文件）
└── LICENSE                        # MIT 许可证文件
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并克隆到本地开发环境。确保本地 Node.js 版本满足安装要求章节中的版本限制。
2. 创建一个新的功能分支，分支名称遵循 `feature/描述` 或 `fix/描述` 格式，例如 `feature/add-csv-export`。
3. 进行代码修改或新增功能时，请同步更新对应的单元测试用例，并确保所有现有测试通过（执行 `npm test`）。对于前端 UI 变更，建议附上简单的界面截图。
4. 编写清晰的提交信息，遵循 Conventional Commits 规范（如 `feat: 新增按文档编号范围过滤功能` 或 `fix: 修复导入时空行导致解析异常的问题`）。
5. 提交 Pull Request 至主仓库的 `main` 分支，并在描述中详细说明变更内容、测试覆盖情况以及影响范围。项目维护者将在 3 个工作日内进行审核。

## 常见问题

Q: 导入链接列表时，系统是否会主动访问这些 URL 并下载 .doc 文件？
A: 不会。DocHub Central 仅对链接字符串本身进行解析、存储和展示，不会主动发起 HTTP 请求去获取或验证 .doc 文件的实际内容。所有链接均以原始格式保存，访问由用户端浏览器负责。

Q: 如果我的链接列表包含重复条目，系统如何处理？
A: 系统在导入时会基于完整 URL 字符串进行去重。如果遇到完全相同的链接（包括协议、域名、路径、文件名均一致），后续重复条目将被自动忽略，并在导入日志中记录重复次数，但不会影响已存储的数据。

Q: 我能否自定义分组规则，而不仅限于按域名分组？
A: 可以。您可以通过修改 `src/core/grouper.js` 中的分组逻辑，添加基于文档编号前缀、路径层级或自定义标签的分组策略。开发者文档中提供了详细的分组扩展示例，建议在修改前查阅 /docs/developer-guide.md 中的相关章节。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

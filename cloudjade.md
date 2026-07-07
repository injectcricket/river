# DocLink Collective

DocLink Collective 是一个面向技术文档聚合与结构化外链管理的开源工具集。该项目定位于帮助开发者、技术团队及内容运营人员高效收集、分类、校验和展示分布于多个域名下的文档资源链接（以 .doc 文件为主），并提供统一的访问入口与元数据管理能力。项目本身不存储任何文档实体，仅作为链接索引与导航系统，适用于需要批量维护外链资源的中大型技术内容平台。

项目目标用户包括：技术文档工程师、开源社区维护者、企业内部知识库管理员以及需要进行大规模外链审计与迁移的运维人员。通过提供标准化的链接导入、去重检测、可用性检查与分类标签功能，DocLink Collective 将零散分布于不同域名的文档链接转化为可检索、可追踪、可定期验证的结构化资源清单。

## 功能概览

多源链接聚合导入：支持从纯文本列表、CSV 及 JSON 格式批量导入链接，自动解析域名、路径与文件名，并生成内部唯一标识符。

域名分组与分类标签：根据链接所属域名自动分组（如 h5.mobile.cmcvrr.cn 等），允许用户为每个链接添加自定义标签（如“技术手册”“运维规范”“产品说明”），便于后续筛选与检索。

链接可用性定期检测：内置轻量级 HTTP 探测模块，支持 HEAD 请求检测链接是否可访问、响应状态码及 Content-Type，自动标记失效链接并生成检测报告。

资源清单导出与同步：支持将当前索引的链接列表导出为 CSV、JSON 或纯文本格式，便于与其他系统集成或进行离线备份。

文档类型元数据提取：针对 .doc 文件链接，尝试通过响应头或链接特征识别文档大小、最后修改时间等元信息，辅助用户判断文档版本及更新时间。

链接变更追踪：记录每个链接的添加时间、最近检测时间及状态变化历史，方便追溯资源变动过程。

全局搜索与过滤：提供基于域名、文件名关键词、标签、状态（有效/失效）的多条件组合搜索，快速定位目标资源。

## 应用场景

技术文档站点迁移与整理：当团队将技术文档从旧站点迁移至新平台时，可使用 DocLink Collective 批量导入所有旧链接，检测其可用性，并分类整理出需要迁移或重定向的文档清单。

开源项目外部资源审计：开源项目常引用大量外部文档链接作为参考资料，使用本项目可定期对所有引用的 .doc 链接进行可用性检测，及时移除或更新失效引用，保证项目文档的健壮性。

企业内部知识库链接质量管理：大型企业内部知识库中散落着大量指向不同文档服务器的链接，管理员可借助本工具建立统一的链接索引，定期扫描失效链接，并通知相关负责人更新。

内容聚合站点导航维护：运营技术内容聚合站点的团队可利用 DocLink Collective 管理其对外输出的链接列表，确保所有推荐文档均可正常访问，提升用户浏览体验。

## 快速开始

以下命令演示了如何在本地环境中获取项目源码、安装依赖并启动基础服务。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/doclink-collective.git

# 进入项目目录
cd doclink-collective

# 安装依赖（使用 npm）
npm install

# 或使用 yarn
yarn install

# 启动开发服务器（默认监听端口 3000）
npm run dev

# 构建生产版本
npm run build

# 运行生产服务器
npm start
```

完成上述步骤后，访问 `http://localhost:3000` 即可进入 DocLink Collective 的 Web 管理界面。首次启动时，系统会自动创建示例数据，并引导用户通过“导入链接”功能开始管理资源。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | >= 18.0.0 | 项目运行时环境，推荐使用 LTS 版本 |
| npm | >= 9.0.0 或 yarn >= 1.22.0 | 包管理器，用于安装项目依赖 |
| SQLite3 | 内置（无需额外安装） | 默认轻量级数据库，用于存储链接索引及元数据 |
| PostgreSQL | >= 13.0（可选） | 生产环境推荐使用，需单独安装并配置连接字符串 |
| Redis | >= 6.0（可选） | 用于缓存链接检测结果及提升搜索性能 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，Linux 服务器为推荐生产环境 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户入门 | /docs/quick-start.md | 如何快速部署并导入第一批链接？如何理解项目的核心工作流？ |
| 功能参考 | /docs/features/link-management.md | 如何批量添加、编辑、删除链接？如何进行域名分组和标签管理？ |
| 运维指南 | /docs/administration/health-check.md | 如何配置定期链接检测任务？如何查看检测日志和修复失效链接？ |
| API 开发 | /docs/api/endpoints.md | 如何通过 REST API 与项目交互？支持哪些数据导入导出格式？ |

## 资源列表

- h5.mobile.cmcvrr.cn/Article/516464.doc
- h5.mobile.fuvxie.cn/Article/5797.doc
- h5.mobile.puhvjy.cn/Article/3600.doc
- h5.mobile.jnjpgf.cn/Article/16156.doc
- h5.mobile.puhvjy.cn/Article/08637.doc
- h5.mobile.jnjpgf.cn/Article/31048.doc
- h5.mobile.puhvjy.cn/Article/82762.doc
- h5.mobile.fuvxie.cn/Article/91020.doc
- h5.mobile.fuvxie.cn/Article/902509.doc
- h5.mobile.cvsifc.cn/Article/9132177.doc
- h5.mobile.jnjpgf.cn/Article/7283.doc
- h5.mobile.cmcvrr.cn/Article/5981886.doc
- h5.mobile.puhvjy.cn/Article/1213.doc
- h5.mobile.puhvjy.cn/Article/95866.doc
- h5.mobile.cvsifc.cn/Article/2127.doc
- h5.mobile.puhvjy.cn/Article/77608.doc
- h5.mobile.cmcvrr.cn/Article/538978.doc
- h5.mobile.jnjpgf.cn/Article/0452327.doc
- h5.mobile.hcbezg.cn/Article/95888.doc
- h5.mobile.fuvxie.cn/Article/1062751.doc
- h5.mobile.cvsifc.cn/Article/473554.doc
- h5.mobile.jnjpgf.cn/Article/092048.doc
- h5.mobile.jnjpgf.cn/Article/040524.doc
- h5.mobile.hcbezg.cn/Article/43510.doc
- h5.mobile.hcbezg.cn/Article/5449.doc
- h5.mobile.fuvxie.cn/Article/7274430.doc
- h5.mobile.hcbezg.cn/Article/10506.doc
- h5.mobile.hcbezg.cn/Article/424913.doc
- h5.mobile.nzfnve.cn/Article/0525816.doc
- h5.mobile.cmcvrr.cn/Article/831010.doc
- h5.mobile.cmcvrr.cn/Article/775692.doc
- h5.mobile.jnjpgf.cn/Article/84615.doc
- h5.mobile.cvsifc.cn/Article/44465.doc
- h5.mobile.nzfnve.cn/Article/40810.doc
- h5.mobile.nwbbyt.cn/Article/6364.doc
- h5.mobile.fuvxie.cn/Article/254374.doc
- h5.mobile.puhvjy.cn/Article/59173.doc
- h5.mobile.nwbbyt.cn/Article/0439.doc
- h5.mobile.cvsifc.cn/Article/985887.doc
- h5.mobile.hcbezg.cn/Article/56475.doc
- h5.mobile.puhvjy.cn/Article/39381.doc
- h5.mobile.fuvxie.cn/Article/26371.doc
- h5.mobile.jnjpgf.cn/Article/2480.doc
- h5.mobile.nwbbyt.cn/Article/9566507.doc
- h5.mobile.nwbbyt.cn/Article/990328.doc
- h5.mobile.jnjpgf.cn/Article/4798190.doc
- h5.mobile.fuvxie.cn/Article/7336.doc
- h5.mobile.puhvjy.cn/Article/80495.doc
- h5.mobile.cvsifc.cn/Article/72619.doc
- h5.mobile.puhvjy.cn/Article/6703935.doc
- h5.mobile.nzfnve.cn/Article/820373.doc
- h5.mobile.cvsifc.cn/Article/7506816.doc
- h5.mobile.nzfnve.cn/Article/205321.doc
- h5.mobile.nzfnve.cn/Article/1500.doc
- h5.mobile.nwbbyt.cn/Article/43037.doc
- h5.mobile.cmcvrr.cn/Article/8656808.doc
- h5.mobile.nzfnve.cn/Article/419303.doc
- h5.mobile.fuvxie.cn/Article/7746534.doc
- h5.mobile.cvsifc.cn/Article/1955.doc
- h5.mobile.puhvjy.cn/Article/44388.doc
- h5.mobile.cvsifc.cn/Article/1323.doc
- h5.mobile.jnjpgf.cn/Article/6904.doc
- h5.mobile.fuvxie.cn/Article/723743.doc
- h5.mobile.cmcvrr.cn/Article/051255.doc
- h5.mobile.nzfnve.cn/Article/37990.doc
- h5.mobile.cmcvrr.cn/Article/17650.doc
- h5.mobile.cvsifc.cn/Article/85123.doc
- h5.mobile.nwbbyt.cn/Article/159275.doc
- h5.mobile.hcbezg.cn/Article/30631.doc
- h5.mobile.hcbezg.cn/Article/271248.doc
- h5.mobile.fuvxie.cn/Article/931684.doc
- h5.mobile.hcbezg.cn/Article/2290.doc
- h5.mobile.nwbbyt.cn/Article/6578.doc
- h5.mobile.nzfnve.cn/Article/6038.doc
- h5.mobile.cmcvrr.cn/Article/97544.doc
- h5.mobile.fuvxie.cn/Article/465707.doc
- h5.mobile.puhvjy.cn/Article/4954973.doc
- h5.mobile.hcbezg.cn/Article/516745.doc
- h5.mobile.puhvjy.cn/Article/1141.doc
- h5.mobile.fuvxie.cn/Article/220894.doc
- h5.mobile.cvsifc.cn/Article/88759.doc
- h5.mobile.fuvxie.cn/Article/930453.doc
- h5.mobile.puhvjy.cn/Article/16223.doc
- h5.mobile.nwbbyt.cn/Article/1416094.doc
- h5.mobile.cmcvrr.cn/Article/90022.doc
- h5.mobile.fuvxie.cn/Article/71844.doc
- h5.mobile.hcbezg.cn/Article/4231388.doc
- h5.mobile.cmcvrr.cn/Article/8685.doc
- h5.mobile.nzfnve.cn/Article/498337.doc
- h5.mobile.cvsifc.cn/Article/1716238.doc
- h5.mobile.cvsifc.cn/Article/6006.doc
- h5.mobile.fuvxie.cn/Article/18140.doc
- h5.mobile.cmcvrr.cn/Article/974430.doc
- h5.mobile.fuvxie.cn/Article/80664.doc
- h5.mobile.fuvxie.cn/Article/288023.doc
- h5.mobile.jnjpgf.cn/Article/48117.doc
- h5.mobile.fuvxie.cn/Article/890169.doc
- h5.mobile.nwbbyt.cn/Article/4309099.doc
- h5.mobile.jnjpgf.cn/Article/11532.doc
- h5.mobile.nzfnve.cn/Article/056372.doc
- h5.mobile.nzfnve.cn/Article/3912.doc
- h5.mobile.fuvxie.cn/Article/2594.doc
- h5.mobile.nwbbyt.cn/Article/47703.doc
- h5.mobile.puhvjy.cn/Article/19566.doc
- h5.mobile.hcbezg.cn/Article/32248.doc
- h5.mobile.jnjpgf.cn/Article/771868.doc
- h5.mobile.nwbbyt.cn/Article/21282.doc
- h5.mobile.jnjpgf.cn/Article/78537.doc
- h5.mobile.nwbbyt.cn/Article/7565.doc
- h5.mobile.nzfnve.cn/Article/35860.doc
- h5.mobile.puhvjy.cn/Article/1336.doc
- h5.mobile.hcbezg.cn/Article/0661808.doc
- h5.mobile.fuvxie.cn/Article/86837.doc
- h5.mobile.fuvxie.cn/Article/9130.doc
- h5.mobile.nwbbyt.cn/Article/145113.doc
- h5.mobile.fuvxie.cn/Article/384792.doc
- h5.mobile.fuvxie.cn/Article/765142.doc
- h5.mobile.nwbbyt.cn/Article/1309.doc
- h5.mobile.jnjpgf.cn/Article/5427.doc
- h5.mobile.fuvxie.cn/Article/0855037.doc
- h5.mobile.jnjpgf.cn/Article/3696188.doc
- h5.mobile.cmcvrr.cn/Article/989945.doc
- h5.mobile.cmcvrr.cn/Article/4367853.doc
- h5.mobile.jnjpgf.cn/Article/0945.doc
- h5.mobile.fuvxie.cn/Article/2036.doc
- h5.mobile.nwbbyt.cn/Article/07752.doc
- h5.mobile.puhvjy.cn/Article/61941.doc
- h5.mobile.nwbbyt.cn/Article/30210.doc
- h5.mobile.fuvxie.cn/Article/0382451.doc
- h5.mobile.jnjpgf.cn/Article/789652.doc
- h5.mobile.puhvjy.cn/Article/4109.doc
- h5.mobile.nwbbyt.cn/Article/265825.doc
- h5.mobile.nzfnve.cn/Article/0348.doc
- h5.mobile.puhvjy.cn/Article/0637.doc
- h5.mobile.jnjpgf.cn/Article/40348.doc
- h5.mobile.cvsifc.cn/Article/279973.doc
- h5.mobile.nzfnve.cn/Article/9409336.doc
- h5.mobile.nwbbyt.cn/Article/578286.doc
- h5.mobile.puhvjy.cn/Article/9672602.doc
- h5.mobile.nzfnve.cn/Article/93959.doc
- h5.mobile.nwbbyt.cn/Article/703138.doc
- h5.mobile.cmcvrr.cn/Article/5565.doc
- h5.mobile.puhvjy.cn/Article/2710.doc
- h5.mobile.fuvxie.cn/Article/8568.doc
- h5.mobile.puhvjy.cn/Article/469648.doc
- h5.mobile.puhvjy.cn/Article/2508.doc
- h5.mobile.puhvjy.cn/Article/222849.doc
- h5.mobile.cvsifc.cn/Article/656037.doc
- h5.mobile.jnjpgf.cn/Article/4076.doc
- h5.mobile.nwbbyt.cn/Article/22111.doc
- h5.mobile.puhvjy.cn/Article/04805.doc
- h5.mobile.cmcvrr.cn/Article/392898.doc
- h5.mobile.jnjpgf.cn/Article/995775.doc
- h5.mobile.puhvjy.cn/Article/07376.doc
- h5.mobile.cvsifc.cn/Article/5699.doc
- h5.mobile.nzfnve.cn/Article/7584567.doc
- h5.mobile.nzfnve.cn/Article/36370.doc
- h5.mobile.fuvxie.cn/Article/671879.doc
- h5.mobile.puhvjy.cn/Article/779550.doc
- h5.mobile.hcbezg.cn/Article/3279306.doc
- h5.mobile.puhvjy.cn/Article/9172.doc
- h5.mobile.hcbezg.cn/Article/186952.doc
- h5.mobile.nzfnve.cn/Article/74217.doc
- h5.mobile.jnjpgf.cn/Article/86604.doc
- h5.mobile.nzfnve.cn/Article/3379305.doc
- h5.mobile.nzfnve.cn/Article/7660.doc
- h5.mobile.cvsifc.cn/Article/748359.doc
- h5.mobile.jnjpgf.cn/Article/039997.doc
- h5.mobile.puhvjy.cn/Article/585147.doc
- h5.mobile.nzfnve.cn/Article/0445.doc
- h5.mobile.jnjpgf.cn/Article/8877821.doc
- h5.mobile.cmcvrr.cn/Article/638321.doc
- h5.mobile.puhvjy.cn/Article/3493.doc
- h5.mobile.hcbezg.cn/Article/98802.doc
- h5.mobile.nwbbyt.cn/Article/2915.doc
- h5.mobile.cvsifc.cn/Article/4986.doc
- h5.mobile.puhvjy.cn/Article/6637232.doc
- h5.mobile.jnjpgf.cn/Article/692204.doc
- h5.mobile.cmcvrr.cn/Article/94814.doc
- h5.mobile.fuvxie.cn/Article/9938.doc
- h5.mobile.cvsifc.cn/Article/4077554.doc
- h5.mobile.cmcvrr.cn/Article/5402.doc
- h5.mobile.nzfnve.cn/Article/53729.doc
- h5.mobile.puhvjy.cn/Article/5626571.doc
- h5.mobile.cvsifc.cn/Article/927450.doc
- h5.mobile.nwbbyt.cn/Article/28301.doc
- h5.mobile.nzfnve.cn/Article/5558158.doc
- h5.mobile.puhvjy.cn/Article/14548.doc
- h5.mobile.puhvjy.cn/Article/41729.doc
- h5.mobile.cmcvrr.cn/Article/44910.doc
- h5.mobile.nzfnve.cn/Article/429228.doc
- h5.mobile.jnjpgf.cn/Article/3464798.doc
- h5.mobile.cvsifc.cn/Article/3216248.doc
- h5.mobile.puhvjy.cn/Article/265225.doc
- h5.mobile.cmcvrr.cn/Article/5441484.doc
- h5.mobile.cvsifc.cn/Article/515227.doc
- h5.mobile.cvsifc.cn/Article/5172139.doc
- h5.mobile.jnjpgf.cn/Article/843607.doc
- h5.mobile.jnjpgf.cn/Article/22835.doc
- h5.mobile.cvsifc.cn/Article/091792.doc
- h5.mobile.nwbbyt.cn/Article/4318177.doc
- h5.mobile.cmcvrr.cn/Article/63549.doc
- h5.mobile.nzfnve.cn/Article/3414531.doc
- h5.mobile.puhvjy.cn/Article/748813.doc
- h5.mobile.puhvjy.cn/Article/572276.doc
- h5.mobile.cmcvrr.cn/Article/7097.doc
- h5.mobile.nzfnve.cn/Article/592874.doc
- h5.mobile.nzfnve.cn/Article/32472.doc
- h5.mobile.nwbbyt.cn/Article/34667.doc
- h5.mobile.puhvjy.cn/Article/187319.doc
- h5.mobile.hcbezg.cn/Article/5444.doc
- h5.mobile.jnjpgf.cn/Article/847475.doc
- h5.mobile.cmcvrr.cn/Article/8954461.doc
- h5.mobile.nwbbyt.cn/Article/000742.doc
- h5.mobile.fuvxie.cn/Article/996672.doc
- h5.mobile.puhvjy.cn/Article/50565.doc
- h5.mobile.fuvxie.cn/Article/381687.doc
- h5.mobile.nzfnve.cn/Article/7818858.doc
- h5.mobile.nwbbyt.cn/Article/1969.doc
- h5.mobile.nwbbyt.cn/Article/69021.doc
- h5.mobile.cmcvrr.cn/Article/167481.doc
- h5.mobile.fuvxie.cn/Article/6372.doc
- h5.mobile.cmcvrr.cn/Article/504396.doc
- h5.mobile.fuvxie.cn/Article/3359067.doc
- h5.mobile.nzfnve.cn/Article/126583.doc
- h5.mobile.puhvjy.cn/Article/3177.doc
- h5.mobile.puhvjy.cn/Article/6600.doc
- h5.mobile.nzfnve.cn/Article/204172.doc
- h5.mobile.nzfnve.cn/Article/2011813.doc
- h5.mobile.cvsifc.cn/Article/5397052.doc
- h5.mobile.hcbezg.cn/Article/3873599.doc
- h5.mobile.cmcvrr.cn/Article/5134493.doc
- h5.mobile.nwbbyt.cn/Article/4091.doc
- h5.mobile.cmcvrr.cn/Article/6011916.doc
- h5.mobile.cvsifc.cn/Article/71508.doc
- h5.mobile.fuvxie.cn/Article/3751.doc
- h5.mobile.cmcvrr.cn/Article/3477831.doc
- h5.mobile.fuvxie.cn/Article/8122.doc
- h5.mobile.nzfnve.cn/Article/776297.doc
- h5.mobile.jnjpgf.cn/Article/427811.doc
- h5.mobile.jnjpgf.cn/Article/92391.doc
- h5.mobile.cvsifc.cn/Article/616504.doc
- h5.mobile.nwbbyt.cn/Article/995258.doc
- h5.mobile.fuvxie.cn/Article/05318.doc
- h5.mobile.nzfnve.cn/Article/17533.doc
- h5.mobile.nwbbyt.cn/Article/6710.doc
- h5.mobile.cmcvrr.cn/Article/61376.doc
- h5.mobile.cvsifc.cn/Article/9117.doc
- h5.mobile.hcbezg.cn/Article/4155.doc
- h5.mobile.nwbbyt.cn/Article/6512.doc

## 项目结构

```
doclink-collective/
├── src/                           # 核心源代码目录
│   ├── core/                      # 核心业务逻辑模块
│   │   ├── link-parser.ts         # 链接解析与验证（提取域名、路径、扩展名）
│   │   ├── link-index.ts          # 内存索引与持久化存储管理
│   │   └── health-checker.ts      # 链接可用性探测与状态更新
│   ├── api/                       # REST API 路由与控制器
│   │   ├── routes/                # 路由定义（导入、查询、导出）
│   │   └── middleware/            # 认证、日志、请求限流
│   ├── web/                       # Web 前端界面（React/Vue）
│   │   ├── pages/                 # 主页面（仪表盘、列表、详情）
│   │   ├── components/            # 复用组件（搜索栏、标签管理、检测报告）
│   │   └── styles/                # 主题样式与响应式布局
│   ├── workers/                   # 后台任务进程
│   │   ├── scheduler.ts           # 定时任务调度（每日检测）
│   │   └── reporter.ts            # 检测报告生成与邮件通知
│   └── utils/                     # 通用工具函数
│       ├── logger.ts              # 日志记录（支持 JSON 格式输出）
│       └── config.ts              # 环境变量与配置加载
├── tests/                         # 单元测试与集成测试
│   ├── unit/                      # 单测用例（link-parser, indexer）
│   └── integration/               # API 端到端测试
├── docs/                          # 项目文档（见文档导航章节）
├── scripts/                       # 运维脚本（数据库迁移、数据导入）
├── docker/                        # Docker 容器化配置
│   ├── Dockerfile                 # 主服务镜像
│   └── docker-compose.yml         # 本地开发环境编排
├── data/                          # 数据存储目录（SQLite 文件、缓存）
├── logs/                          # 应用日志目录（按日滚动）
├── package.json                   # 项目依赖与脚本定义
├── tsconfig.json                  # TypeScript 编译配置
├── .env.example                   # 环境变量模板
└── README.md                      # 本文件
```

## 贡献指南

我们欢迎并感谢任何形式的贡献。请遵循以下步骤参与项目开发：

1. 浏览现有 Issue 列表，选择未被认领的任务，或在提交新 Issue 前搜索是否已有相似内容。建议先通过 Issue 与维护者沟通设计思路，避免无效工作。

2. Fork 本仓库至个人账号，并在本地创建功能分支（命名规范：feature/功能简述 或 fix/问题简述）。分支基于 main 分支创建，保持与上游同步。

3. 编写代码时遵循项目 ESLint 及 Prettier 配置，提交前运行 `npm run lint` 和 `npm run test` 确保通过所有检查。新功能需附带相应的单元测试用例。

4. 提交 Commit 时使用语义化消息格式（如 `feat: 添加链接批量导入功能`、`fix: 修复链接检测超时问题`），便于自动生成变更日志。

5. 推送分支并提交 Pull Request 至 main 分支。PR 描述中需清楚说明变更内容、影响范围及测试情况。至少一位维护者审阅通过后合并。

## 常见问题

**Q: 项目是否存储文档文件本身？如何保证版权合规？**

A: DocLink Collective 不存储任何文档文件或其副本，仅保存链接地址、检测状态及用户自定义标签等元数据。所有文档版权归原始发布者所有。用户应确保所导入链接的内容符合相关法律法规及版权要求。

**Q: 链接可用性检测的原理是什么？是否会频繁请求外部服务器？**

A: 检测模块采用 HTTP HEAD 请求，仅获取响应头信息（状态码、Content-Type、Content-Length），不会下载完整文档。默认检测间隔为 24 小时，且支持用户自定义检测频率及并发数。对于频繁返回 5xx 或超时的域名，系统会自动降低检测优先级以避免对源站造成压力。

**Q: 如何迁移已有的链接列表至本项目？**

A: 项目提供三种导入方式：通过 Web 界面的“导入”功能上传 CSV/JSON 文件；通过 REST API 的 `/api/import` 端点批量提交；或直接将链接列表按行保存在文本文件中，使用 CLI 命令 `npm run import -- --file=links.txt` 执行导入。详细格式说明请参考文档导航中的“功能参考”章节。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

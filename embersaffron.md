# LinkSphere 技术资源聚合导航

LinkSphere 是一个面向开发者、技术研究人员与内容创作者的轻量级技术资源聚合与导航系统。该项目定位于对分散于各技术社区、博客平台与文档站点的优质外链进行结构化收录、分类索引与状态监控，帮助用户以最低成本发现并访问高价值技术内容。LinkSphere 不生产内容，而是通过人工精选与自动化校验相结合的方式，构建一个高可用、低噪音的技术资源入口。

目标用户包括：需要持续跟进前沿技术动态的软件工程师、进行文献调研与竞品分析的技术管理者、以及希望系统化整理个人学习路径的在校学生。项目本身不依赖复杂后端架构，采用静态站点生成加外部数据源同步的方式运行，既可作为个人书签管理的替代方案，也可部署为团队内部的技术知识导航页。

## 功能概览

多源资源聚合收录 系统支持对来自不同域名与路径结构的文章链接进行批量导入、去重与元数据提取，自动识别资源类型（博客、文档、工具页、视频教程等）。

自定义分类与标签体系 用户可根据技术栈、难度等级、适用场景等维度为每条资源建立多级分类与自由标签，支持模糊检索与组合过滤。

资源健康状态巡检 内置定时校验任务，对已收录的 URL 进行可达性检测与响应时间评估，自动标记失效链接并生成告警通知。

全文元数据索引 对资源标题、摘要、关键词及正文前 500 字符建立轻量级倒排索引，支持中文分词与布尔检索，返回结果按相关度与新鲜度排序。

导入导出与订阅机制 支持 OPML、JSON、CSV 格式的资源列表导入导出，允许用户通过 RSS 或邮件订阅特定分类下的新增资源推送。

访问统计与热度排序 记录每个资源的点击次数与最近访问时间，支持按七日热门、月度收藏量等维度生成排行视图。

用户自定义导航面板 注册用户可创建个人收藏夹、自定义首页布局，并设置常用分类快捷入口，实现个性化资源调度。

## 应用场景

技术团队内部知识库建设 开发团队可将 LinkSphere 部署为内部文档导航入口，集中存放项目相关的 API 手册、设计文档、运维指南和团队博客链接，减少成员在多个平台间切换查找资料的时间成本。

个人技术学习路线管理 学习者可按阶段（入门、进阶、实战）将搜集到的教程、案例源码和视频课程分类归档，配合健康巡检功能定期清理失效链接，保持学习路径的持续可用性。

技术社区内容聚合展示 社区运营者可将用户投稿、官方公告和合作方内容统一纳入 LinkSphere，通过热度排序和标签筛选快速生成每周精选列表，提升社区内容曝光效率。

开源项目文档外链整合 开源项目维护者可在 README 或项目官网中嵌入 LinkSphere 生成的资源列表页面，将周边生态工具、插件列表和第三方评测文章集中呈现，降低新用户的上手门槛。

## 快速开始

以下命令将在本地启动 LinkSphere 开发实例，默认监听 8080 端口。

```bash
git clone https://github.com/linksphere/linksphere-core.git
cd linksphere-core
npm install
npm run build
npm start
```

若使用 Docker 运行，可执行：

```bash
docker pull linksphere/linksphere:latest
docker run -p 8080:8080 -v ./data:/app/data linksphere/linksphere:latest
```

启动成功后，访问 http://localhost:8080 即可进入资源导航面板。首次启动将自动生成示例分类与占位资源，随后可通过管理后台（默认路径 /admin，初始账号 admin / admin123）开始导入自定义 URL 列表。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时环境，建议使用 nvm 管理多版本 |
| npm | 9.x 或以上 | 包管理器，用于安装项目依赖 |
| SQLite3 | 3.40 或以上 | 内置元数据存储，无需单独安装服务端 |
| Redis | 7.0 或以上（可选） | 用于会话缓存与访问计数，非必需但推荐生产环境启用 |
| Nginx | 1.24 或以上（可选） | 推荐用作反向代理与静态资源缓存层 |

生产环境建议使用 Linux 内核 5.10 以上版本的操作系统（Ubuntu 22.04 / Debian 12），至少 2GB 内存与 20GB 可用磁盘空间。若使用 Docker 部署，则宿主机仅需安装 Docker Engine 24.0 以上及 Docker Compose 2.20 以上。

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/quick-start | 如何在 10 分钟内完成首次资源导入并生成导航页面 |
| 管理手册 | /docs/admin-guide | 如何配置分类体系、设置自动巡检策略及管理用户权限 |
| 开发者文档 | /docs/development | 如何扩展自定义解析器、增加新的数据源适配器或修改索引算法 |
| API 参考 | /docs/api-reference | 所有 RESTful 接口的请求参数、响应格式与错误码说明 |
| 部署运维 | /docs/deployment | 生产环境高可用部署方案、性能调优参数与监控指标配置 |

## 资源列表

- https://www.read.nwbbyt.cn/Article/4795.shtml
- https://www.read.nzfnve.cn/Article/705708.shtml
- https://www.read.fuvxie.cn/Article/5394.shtml
- https://www.read.cvsifc.cn/Article/4476.shtml
- https://www.read.jnjpgf.cn/Article/944230.shtml
- https://www.read.cvsifc.cn/Article/5144951.shtml
- https://www.read.hcbezg.cn/Article/488093.shtml
- https://www.read.cmcvrr.cn/Article/3408.shtml
- https://www.read.cmcvrr.cn/Article/6143452.shtml
- https://www.read.nzfnve.cn/Article/3677.shtml
- https://www.read.puhvjy.cn/Article/627395.shtml
- https://www.read.hcbezg.cn/Article/8605.shtml
- https://www.read.fuvxie.cn/Article/11757.shtml
- https://www.read.nwbbyt.cn/Article/8001090.shtml
- https://www.read.cvsifc.cn/Article/713863.shtml
- https://www.read.cvsifc.cn/Article/15496.shtml
- https://www.read.puhvjy.cn/Article/91135.shtml
- https://www.read.hcbezg.cn/Article/78602.shtml
- https://www.read.nwbbyt.cn/Article/2380.shtml
- https://www.read.cmcvrr.cn/Article/2540.shtml
- https://www.read.puhvjy.cn/Article/36365.shtml
- https://www.read.puhvjy.cn/Article/399312.shtml
- https://www.read.cvsifc.cn/Article/983904.shtml
- https://www.read.cmcvrr.cn/Article/491006.shtml
- https://www.read.hcbezg.cn/Article/034381.shtml
- https://www.read.jnjpgf.cn/Article/10438.shtml
- https://www.read.nwbbyt.cn/Article/1967816.shtml
- https://www.read.fuvxie.cn/Article/4819057.shtml
- https://www.read.cmcvrr.cn/Article/609771.shtml
- https://www.read.hcbezg.cn/Article/30391.shtml
- https://www.read.nzfnve.cn/Article/3166522.shtml
- https://www.read.cmcvrr.cn/Article/3104170.shtml
- https://www.read.cmcvrr.cn/Article/979783.shtml
- https://www.read.cvsifc.cn/Article/69399.shtml
- https://www.read.hcbezg.cn/Article/54761.shtml
- https://www.read.cmcvrr.cn/Article/8255757.shtml
- https://www.read.nwbbyt.cn/Article/005277.shtml
- https://www.read.jnjpgf.cn/Article/960557.shtml
- https://www.read.nzfnve.cn/Article/24561.shtml
- https://www.read.fuvxie.cn/Article/6662931.shtml
- https://www.read.puhvjy.cn/Article/05228.shtml
- https://www.read.cmcvrr.cn/Article/1405018.shtml
- https://www.read.cvsifc.cn/Article/89833.shtml
- https://www.read.cvsifc.cn/Article/029006.shtml
- https://www.read.jnjpgf.cn/Article/9617.shtml
- https://www.read.cmcvrr.cn/Article/2935.shtml
- https://www.read.cvsifc.cn/Article/8318634.shtml
- https://www.read.cvsifc.cn/Article/55946.shtml
- https://www.read.nwbbyt.cn/Article/0076.shtml
- https://www.read.puhvjy.cn/Article/0242.shtml
- https://www.read.hcbezg.cn/Article/1274171.shtml
- https://www.read.puhvjy.cn/Article/578673.shtml
- https://www.read.cmcvrr.cn/Article/99895.shtml
- https://www.read.nwbbyt.cn/Article/8761.shtml
- https://www.read.nwbbyt.cn/Article/84900.shtml
- https://www.read.cmcvrr.cn/Article/8061375.shtml
- https://www.read.nwbbyt.cn/Article/9672131.shtml
- https://www.read.nwbbyt.cn/Article/41990.shtml
- https://www.read.nwbbyt.cn/Article/8894.shtml
- https://www.read.nzfnve.cn/Article/2576572.shtml
- https://www.read.cvsifc.cn/Article/4464.shtml
- https://www.read.puhvjy.cn/Article/984948.shtml
- https://www.read.puhvjy.cn/Article/5995862.shtml
- https://www.read.cmcvrr.cn/Article/380668.shtml
- https://www.read.puhvjy.cn/Article/608218.shtml
- https://www.read.fuvxie.cn/Article/8214253.shtml
- https://www.read.nwbbyt.cn/Article/364585.shtml
- https://www.read.fuvxie.cn/Article/070971.shtml
- https://www.read.cvsifc.cn/Article/4668158.shtml
- https://www.read.fuvxie.cn/Article/3587.shtml
- https://www.read.puhvjy.cn/Article/1481.shtml
- https://www.read.nwbbyt.cn/Article/704272.shtml
- https://www.read.hcbezg.cn/Article/227796.shtml
- https://www.read.jnjpgf.cn/Article/31731.shtml
- https://www.read.puhvjy.cn/Article/637914.shtml
- https://www.read.jnjpgf.cn/Article/011757.shtml
- https://www.read.cvsifc.cn/Article/966211.shtml
- https://www.read.cvsifc.cn/Article/8960.shtml
- https://www.read.cvsifc.cn/Article/7279063.shtml
- https://www.read.nwbbyt.cn/Article/11570.shtml
- https://www.read.jnjpgf.cn/Article/7787865.shtml
- https://www.read.nzfnve.cn/Article/9686.shtml
- https://www.read.nzfnve.cn/Article/0049.shtml
- https://www.read.jnjpgf.cn/Article/8221847.shtml
- https://www.read.cmcvrr.cn/Article/8881.shtml
- https://www.read.puhvjy.cn/Article/095368.shtml
- https://www.read.fuvxie.cn/Article/7429.shtml
- https://www.read.puhvjy.cn/Article/4492246.shtml
- https://www.read.nzfnve.cn/Article/241521.shtml
- https://www.read.fuvxie.cn/Article/7064297.shtml
- https://www.read.nzfnve.cn/Article/695836.shtml
- https://www.read.cvsifc.cn/Article/0374.shtml
- https://www.read.cvsifc.cn/Article/4543.shtml
- https://www.read.nwbbyt.cn/Article/791289.shtml
- https://www.read.hcbezg.cn/Article/4455.shtml
- https://www.read.fuvxie.cn/Article/4592.shtml
- https://www.read.nzfnve.cn/Article/444935.shtml
- https://www.read.puhvjy.cn/Article/0355287.shtml
- https://www.read.cmcvrr.cn/Article/5821720.shtml
- https://www.read.jnjpgf.cn/Article/22246.shtml
- https://www.read.jnjpgf.cn/Article/9102724.shtml
- https://www.read.fuvxie.cn/Article/342059.shtml
- https://www.read.puhvjy.cn/Article/630056.shtml
- https://www.read.nwbbyt.cn/Article/8682.shtml
- https://www.read.puhvjy.cn/Article/6073858.shtml
- https://www.read.nwbbyt.cn/Article/33510.shtml
- https://www.read.nwbbyt.cn/Article/6990901.shtml
- https://www.read.nwbbyt.cn/Article/89720.shtml
- https://www.read.cvsifc.cn/Article/7635.shtml
- https://www.read.nzfnve.cn/Article/4421.shtml
- https://www.read.cvsifc.cn/Article/228213.shtml
- https://www.read.puhvjy.cn/Article/14830.shtml
- https://www.read.cmcvrr.cn/Article/80325.shtml
- https://www.read.jnjpgf.cn/Article/3843191.shtml
- https://www.read.cmcvrr.cn/Article/5025.shtml
- https://www.read.puhvjy.cn/Article/8359.shtml
- https://www.read.cmcvrr.cn/Article/660185.shtml
- https://www.read.cvsifc.cn/Article/61048.shtml
- https://www.read.jnjpgf.cn/Article/27459.shtml
- https://www.read.jnjpgf.cn/Article/9418100.shtml
- https://www.read.cvsifc.cn/Article/664304.shtml
- https://www.read.nwbbyt.cn/Article/809635.shtml
- https://www.read.nzfnve.cn/Article/5738963.shtml
- https://www.read.puhvjy.cn/Article/414117.shtml
- https://www.read.cmcvrr.cn/Article/0246541.shtml
- https://www.read.nzfnve.cn/Article/1442.shtml
- https://www.read.nzfnve.cn/Article/089573.shtml
- https://www.read.cmcvrr.cn/Article/2059.shtml
- https://www.read.hcbezg.cn/Article/21427.shtml
- https://www.read.puhvjy.cn/Article/412150.shtml
- https://www.read.jnjpgf.cn/Article/7751822.shtml
- https://www.read.cmcvrr.cn/Article/7389.shtml
- https://www.read.nwbbyt.cn/Article/879416.shtml
- https://www.read.puhvjy.cn/Article/787696.shtml
- https://www.read.fuvxie.cn/Article/392870.shtml
- https://www.read.nzfnve.cn/Article/03269.shtml
- https://www.read.nzfnve.cn/Article/9958669.shtml
- https://www.read.puhvjy.cn/Article/3785004.shtml
- https://www.read.fuvxie.cn/Article/77534.shtml
- https://www.read.cmcvrr.cn/Article/5890838.shtml
- https://www.read.puhvjy.cn/Article/2526284.shtml
- https://www.read.hcbezg.cn/Article/34671.shtml
- https://www.read.hcbezg.cn/Article/4807.shtml
- https://www.read.hcbezg.cn/Article/3754173.shtml
- https://www.read.cmcvrr.cn/Article/5593.shtml
- https://www.read.jnjpgf.cn/Article/7092.shtml
- https://www.read.cmcvrr.cn/Article/224287.shtml
- https://www.read.cvsifc.cn/Article/801788.shtml
- https://www.read.jnjpgf.cn/Article/51401.shtml
- https://www.read.nzfnve.cn/Article/734738.shtml
- https://www.read.nzfnve.cn/Article/66528.shtml
- https://www.read.jnjpgf.cn/Article/8823541.shtml
- https://www.read.jnjpgf.cn/Article/2231963.shtml
- https://www.read.cmcvrr.cn/Article/056878.shtml
- https://www.read.nwbbyt.cn/Article/407899.shtml
- https://www.read.fuvxie.cn/Article/8011139.shtml
- https://www.read.jnjpgf.cn/Article/095623.shtml
- https://www.read.puhvjy.cn/Article/549633.shtml
- https://www.read.nwbbyt.cn/Article/8608.shtml
- https://www.read.puhvjy.cn/Article/610344.shtml
- https://www.read.fuvxie.cn/Article/27577.shtml
- https://www.read.cvsifc.cn/Article/64701.shtml
- https://www.read.puhvjy.cn/Article/595551.shtml
- https://www.read.hcbezg.cn/Article/0797601.shtml
- https://www.read.nwbbyt.cn/Article/1301.shtml
- https://www.read.cvsifc.cn/Article/928082.shtml
- https://www.read.fuvxie.cn/Article/0606.shtml
- https://www.read.hcbezg.cn/Article/8460796.shtml
- https://www.read.puhvjy.cn/Article/761000.shtml
- https://www.read.nzfnve.cn/Article/4092.shtml
- https://www.read.puhvjy.cn/Article/85667.shtml
- https://www.read.cmcvrr.cn/Article/1600.shtml
- https://www.read.fuvxie.cn/Article/103620.shtml
- https://www.read.puhvjy.cn/Article/838977.shtml
- https://www.read.nwbbyt.cn/Article/98737.shtml
- https://www.read.fuvxie.cn/Article/27029.shtml
- https://www.read.cvsifc.cn/Article/0290.shtml
- https://www.read.puhvjy.cn/Article/665921.shtml
- https://www.read.cvsifc.cn/Article/751718.shtml
- https://www.read.nwbbyt.cn/Article/64994.shtml
- https://www.read.cvsifc.cn/Article/0537.shtml
- https://www.read.puhvjy.cn/Article/0371998.shtml
- https://www.read.fuvxie.cn/Article/99990.shtml
- https://www.read.nwbbyt.cn/Article/03932.shtml
- https://www.read.hcbezg.cn/Article/2748349.shtml
- https://www.read.nwbbyt.cn/Article/8050201.shtml
- https://www.read.nzfnve.cn/Article/71395.shtml
- https://www.read.cmcvrr.cn/Article/86898.shtml
- https://www.read.cvsifc.cn/Article/7048.shtml
- https://www.read.cvsifc.cn/Article/735220.shtml
- https://www.read.hcbezg.cn/Article/63713.shtml
- https://www.read.nwbbyt.cn/Article/45749.shtml
- https://www.read.fuvxie.cn/Article/257941.shtml
- https://www.read.fuvxie.cn/Article/3799.shtml
- https://www.read.jnjpgf.cn/Article/7251634.shtml
- https://www.read.nwbbyt.cn/Article/9680904.shtml
- https://www.read.cvsifc.cn/Article/74015.shtml
- https://www.read.jnjpgf.cn/Article/6299.shtml
- https://www.read.nzfnve.cn/Article/69173.shtml
- https://www.read.nzfnve.cn/Article/46162.shtml
- https://www.read.jnjpgf.cn/Article/0121642.shtml
- https://www.read.nzfnve.cn/Article/0417462.shtml
- https://www.read.puhvjy.cn/Article/2190.shtml
- https://www.read.jnjpgf.cn/Article/1783010.shtml
- https://www.read.hcbezg.cn/Article/648588.shtml
- https://www.read.hcbezg.cn/Article/991997.shtml
- https://www.read.jnjpgf.cn/Article/055697.shtml
- https://www.read.fuvxie.cn/Article/52913.shtml
- https://www.read.cmcvrr.cn/Article/307610.shtml
- https://www.read.cmcvrr.cn/Article/8469.shtml
- https://www.read.jnjpgf.cn/Article/25519.shtml
- https://www.read.cvsifc.cn/Article/079505.shtml
- https://www.read.nzfnve.cn/Article/126402.shtml
- https://www.read.nzfnve.cn/Article/0266.shtml
- https://www.read.fuvxie.cn/Article/3697.shtml
- https://www.read.puhvjy.cn/Article/0732.shtml
- https://www.read.puhvjy.cn/Article/932377.shtml
- https://www.read.puhvjy.cn/Article/9276204.shtml
- https://www.read.cvsifc.cn/Article/0818440.shtml
- https://www.read.nwbbyt.cn/Article/13866.shtml
- https://www.read.cmcvrr.cn/Article/902886.shtml
- https://www.read.cvsifc.cn/Article/694829.shtml
- https://www.read.hcbezg.cn/Article/0748.shtml
- https://www.read.hcbezg.cn/Article/69066.shtml
- https://www.read.fuvxie.cn/Article/271691.shtml
- https://www.read.cvsifc.cn/Article/08849.shtml
- https://www.read.fuvxie.cn/Article/0717.shtml
- https://www.read.jnjpgf.cn/Article/579205.shtml
- https://www.read.fuvxie.cn/Article/22649.shtml
- https://www.read.nzfnve.cn/Article/682663.shtml
- https://www.read.jnjpgf.cn/Article/3246.shtml
- https://www.read.hcbezg.cn/Article/66131.shtml
- https://www.read.nwbbyt.cn/Article/87834.shtml
- https://www.read.nzfnve.cn/Article/43134.shtml
- https://www.read.hcbezg.cn/Article/3785964.shtml
- https://www.read.cvsifc.cn/Article/835516.shtml
- https://www.read.fuvxie.cn/Article/49384.shtml
- https://www.read.nzfnve.cn/Article/4198032.shtml
- https://www.read.puhvjy.cn/Article/8607437.shtml
- https://www.read.hcbezg.cn/Article/9572288.shtml
- https://www.read.cmcvrr.cn/Article/41094.shtml
- https://www.read.hcbezg.cn/Article/78896.shtml
- https://www.read.nzfnve.cn/Article/629992.shtml
- https://www.read.puhvjy.cn/Article/18520.shtml
- https://www.read.cmcvrr.cn/Article/71518.shtml
- https://www.read.hcbezg.cn/Article/15316.shtml
- https://www.read.cvsifc.cn/Article/959311.shtml
- https://www.read.puhvjy.cn/Article/1713.shtml
- https://www.read.puhvjy.cn/Article/897112.shtml
- https://www.read.nwbbyt.cn/Article/5601.shtml

## 项目结构

```
linksphere-core/
├── src/                                # 核心源码目录
│   ├── core/                           # 核心引擎模块
│   │   ├── indexer.js                  # 倒排索引构建与检索逻辑
│   │   ├── crawler.js                  # 资源元数据抓取与解析适配器
│   │   └── validator.js                # URL 健康状态校验与重试策略
│   ├── routes/                         # HTTP 路由层
│   │   ├── api/                        # RESTful API 端点（v1 版本）
│   │   └── web/                        # 管理后台页面路由
│   ├── services/                       # 业务服务层
│   │   ├── category.service.js         # 分类树管理及资源归属计算
│   │   ├── stats.service.js            # 点击统计与热度排行计算
│   │   └── sync.service.js             # 外部数据源导入与增量同步
│   ├── models/                         # 数据模型定义（SQLite ORM 映射）
│   ├── utils/                          # 通用工具函数（日志、缓存、字符串处理）
│   └── app.js                          # 应用入口与中间件装配
├── config/                             # 配置文件目录
│   ├── default.yaml                    # 默认配置（端口、数据库路径、巡检间隔）
│   ├── production.yaml                 # 生产环境覆盖配置
│   └── schema/                         # 配置字段 JSON Schema 校验定义
├── data/                               # 数据存储目录（运行时生成）
│   ├── db/                             # SQLite 数据库文件存放位置
│   ├── cache/                          # Redis 本地缓存降级存储
│   └── logs/                           # 应用日志按日期滚动存放
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 各模块独立单元测试
│   └── integration/                    # API 端到端测试与数据库迁移测试
├── scripts/                            # 运维与工具脚本
│   ├── migrate.js                      # 数据库版本迁移执行器
│   ├── seed.js                         # 初始分类与示例资源填充
│   └── health-check.js                 # 独立运行的巡检命令行工具
├── docs/                               # 完整文档源文件（Markdown 格式）
├── public/                             # 静态资源（CSS、JavaScript、图片）
├── package.json                        # npm 依赖声明与脚本命令
├── Dockerfile                          # 多阶段构建 Docker 镜像定义
├── docker-compose.yml                  # 本地开发与测试环境编排
├── .eslintrc.js                        # 代码风格检查规则
└── README.md                           # 项目说明（当前文件）
```

## 贡献指南

1. 查阅问题追踪列表 访问 GitHub Issues 页面，筛选标记为 "help wanted" 或 "good first issue" 的条目，确认无重复工作后留言认领任务。

2. 派生仓库并创建特性分支 将主仓库 Fork 至个人账户，然后克隆到本地。新建分支名称需遵循 `feature/功能简述` 或 `fix/问题编号` 格式，例如 `feature/improve-crawler-timeout`。

3. 编写测试用例与代码 任何新增功能或缺陷修复必须包含对应的单元测试，测试覆盖率不应低于原有水平。代码提交前需运行 `npm run lint` 与 `npm test` 确保全部检查通过。

4. 提交变更并发起拉取请求 提交信息采用约定式提交格式，即 `<type>(<scope>): <subject>`，类型包括 feat、fix、docs、style、refactor、perf、test、chore 等。PR 描述需明确说明改动目的、实现方式及影响范围。

5. 代码评审与合并 项目维护者将在 2 个工作日内完成评审，提出修改意见或直接批准。合并后相关分支将被自动删除，对应 Issue 将被关闭。

## 常见问题

问：部署后无法访问管理后台，页面返回 404 如何处理？

答：请检查 config/default.yaml 中的 admin.basePath 配置项是否正确，默认值为 /admin。同时确认启动时控制台是否输出 "Admin panel mounted at /admin" 日志。若使用反向代理，需确保代理转发路径与 basePath 一致，且未剥离路径前缀。

问：资源健康巡检报告显示大量链接超时，但手动访问浏览器正常，原因是什么？

答：巡检模块默认使用无头 HTTP 客户端，不执行 JavaScript 且不携带浏览器级别的 TLS 指纹。部分站点对非浏览器请求进行限速或拦截。解决方案为：在 config/production.yaml 中调整 checker.userAgent 为常见浏览器 UA，并增大 checker.timeout 至 15000 毫秒。若站点有 Cloudflare 等防护，建议将巡检间隔调整为非固定周期，避免触发频率限制。

问：如何从旧版本迁移数据，或在不同部署环境间同步分类与标签？

答：使用内置的导入导出功能。在旧版本管理后台进入 "系统工具 > 数据导出"，选择导出完整数据包（含分类、标签、资源元数据及点击统计）。新版本部署完成后，在相同入口选择导入，并勾选 "覆盖冲突分类" 或 "合并标签" 选项。若需命令行操作，可使用 scripts/import.js 与 scripts/export.js 配合 JSON 格式文件完成迁移。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

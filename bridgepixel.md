# LinkCollector

LinkCollector 是一个面向技术文档聚合与知识外链管理的开源工具集，定位于帮助开发者、技术团队与内容创作者高效收录、分类、检索和共享分散在多个技术社区、博客与资讯站点的优质文章资源。本项目不提供爬虫与采集功能，而是基于人工整理与社区提交的链接清单，提供标准化的资源索引结构与本地预览服务，适用于搭建个人或团队内部的技术阅读清单、周刊素材库或学习路径导航。

目标用户包括技术社区运营者、开源项目维护者、技术内容策展人以及日常需要跟踪大量技术资讯的研发工程师。LinkCollector 通过统一的链接列表管理与轻量级元数据标注能力，解决技术资源分散、重复收集、难以回溯与共享效率低下的问题。

## 功能概览

批量链接导入与校验 支持从文本文件或标准输入中批量导入链接列表，自动去重并校验 URL 格式合法性。

分层标签管理 允许为每条资源链接添加多个层级标签，支持基于标签的快速筛选与统计。

本地预览服务 内置轻量级 HTTP 服务器，可在本地启动静态页面，以卡片或列表形式展示所有收录链接。

Markdown 清单导出 支持将当前链接集合导出为符合本仓库文档规范的 Markdown 列表，便于版本管理与跨平台分发。

链接状态标记 可为每条链接标注已读、待读、推荐或过期等状态，支持状态变更的时间戳记录。

全文检索支持 基于链接标题与描述文本构建简单的倒排索引，提供基础的全文搜索能力。

数据快照与回滚 每次修改操作自动生成数据快照，支持回滚至任意历史版本，避免误操作导致数据丢失。

## 应用场景

技术周刊素材整理 技术社区编辑在策划每周内容推荐时，可将一周内浏览到的候选文章链接统一录入 LinkCollector，通过标签区分领域，快速筛选出当周精选内容并导出为发布清单。

个人技术阅读队列管理 开发者日常浏览技术博客与新闻站点时，将感兴趣但暂无时间细读的文章链接存入系统，利用状态标记与检索功能构建个人阅读队列，避免链接丢失或遗忘。

团队知识库外链索引 研发团队在维护内部技术文档库时，使用 LinkCollector 统一管理所有引用到的外部资源链接，确保文档中的引用链接可追溯、可验证，降低链接失效带来的信息缺失风险。

开源项目推荐资源汇总 开源项目维护者可将社区中与本项目相关的教程、案例、评测文章链接集中收录，作为项目官方 Wiki 的补充资源导航，方便新用户快速获取周边学习材料。

技术会议演讲素材库 技术分享者在准备演讲内容时，可围绕演讲主题收集相关技术文章与数据报告链接，利用标签与检索功能快速组织素材，提高内容准备效率。

## 快速开始

以下步骤帮助您在本地环境中快速启动 LinkCollector 服务。

```bash
# 克隆项目仓库至本地
git clone https://github.com/linkcollector/linkcollector.git

# 进入项目根目录
cd linkcollector

# 安装项目依赖（使用 npm）
npm install

# 启动本地预览服务，默认监听端口 3000
npm start
```

执行完毕后，在浏览器中访问 http://localhost:3000 即可查看链接列表管理界面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 16.x 或更高 | 项目运行时环境，提供 JavaScript 执行引擎与内置模块 |
| npm | 8.x 或更高 | 依赖包管理工具，用于安装项目所需第三方库 |
| Git | 2.25 或更高 | 版本控制工具，用于克隆仓库与提交变更 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，Windows 下建议使用 WSL2 环境以获得最佳性能 |
| 浏览器 | 现代浏览器（Chrome 90+ / Firefox 88+ / Edge 90+） | 用于访问本地预览界面，需支持 ES6 语法与 Flexbox 布局 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何添加链接、如何打标签、如何导出清单、如何使用检索功能 |
| 运维指南 | docs/operations.md | 如何备份数据、如何迁移服务、如何配置端口与日志级别 |
| 开发者文档 | docs/developer.md | 项目模块划分、数据存储结构、API 接口说明、如何提交新功能 |
| 社区规范 | docs/community.md | 链接提交标准、标签命名约定、状态使用规范、审核流程说明 |

## 资源列表

- https://www.read.puhvjy.cn/Article/943690.shtml
- https://www.read.nzfnve.cn/Article/9705.shtml
- https://www.read.cmcvrr.cn/Article/30814.shtml
- https://www.read.hcbezg.cn/Article/1751.shtml
- https://www.read.cmcvrr.cn/Article/420318.shtml
- https://www.read.fuvxie.cn/Article/5117946.shtml
- https://www.read.fuvxie.cn/Article/6457.shtml
- https://www.read.nzfnve.cn/Article/19259.shtml
- https://www.read.nzfnve.cn/Article/04078.shtml
- https://www.read.nzfnve.cn/Article/7611926.shtml
- https://www.read.fuvxie.cn/Article/3980.shtml
- https://www.read.hcbezg.cn/Article/8673090.shtml
- https://www.read.jnjpgf.cn/Article/21669.shtml
- https://www.read.hcbezg.cn/Article/229759.shtml
- https://www.read.nwbbyt.cn/Article/73733.shtml
- https://www.read.cmcvrr.cn/Article/79591.shtml
- https://www.read.cmcvrr.cn/Article/13245.shtml
- https://www.read.puhvjy.cn/Article/2981.shtml
- https://www.read.nzfnve.cn/Article/3362919.shtml
- https://www.read.puhvjy.cn/Article/1998887.shtml
- https://www.read.cmcvrr.cn/Article/3896387.shtml
- https://www.read.fuvxie.cn/Article/4317365.shtml
- https://www.read.puhvjy.cn/Article/007191.shtml
- https://www.read.nzfnve.cn/Article/536508.shtml
- https://www.read.nzfnve.cn/Article/2014.shtml
- https://www.read.nwbbyt.cn/Article/4314.shtml
- https://www.read.hcbezg.cn/Article/6953194.shtml
- https://www.read.cmcvrr.cn/Article/88423.shtml
- https://www.read.cvsifc.cn/Article/8382.shtml
- https://www.read.cvsifc.cn/Article/912599.shtml
- https://www.read.jnjpgf.cn/Article/166529.shtml
- https://www.read.hcbezg.cn/Article/478537.shtml
- https://www.read.nwbbyt.cn/Article/2080779.shtml
- https://www.read.jnjpgf.cn/Article/06720.shtml
- https://www.read.nwbbyt.cn/Article/17327.shtml
- https://www.read.cmcvrr.cn/Article/036326.shtml
- https://www.read.jnjpgf.cn/Article/061982.shtml
- https://www.read.cvsifc.cn/Article/1651.shtml
- https://www.read.nwbbyt.cn/Article/61584.shtml
- https://www.read.cmcvrr.cn/Article/55925.shtml
- https://www.read.jnjpgf.cn/Article/520026.shtml
- https://www.read.cvsifc.cn/Article/9186.shtml
- https://www.read.puhvjy.cn/Article/2213.shtml
- https://www.read.cmcvrr.cn/Article/3597503.shtml
- https://www.read.puhvjy.cn/Article/128543.shtml
- https://www.read.cvsifc.cn/Article/5026640.shtml
- https://www.read.cmcvrr.cn/Article/4209250.shtml
- https://www.read.puhvjy.cn/Article/2079.shtml
- https://www.read.cvsifc.cn/Article/671356.shtml
- https://www.read.cmcvrr.cn/Article/5581658.shtml
- https://www.read.fuvxie.cn/Article/883719.shtml
- https://www.read.hcbezg.cn/Article/937001.shtml
- https://www.read.puhvjy.cn/Article/2649584.shtml
- https://www.read.nzfnve.cn/Article/198249.shtml
- https://www.read.nzfnve.cn/Article/6858059.shtml
- https://www.read.hcbezg.cn/Article/3018096.shtml
- https://www.read.cmcvrr.cn/Article/57680.shtml
- https://www.read.nwbbyt.cn/Article/6084.shtml
- https://www.read.puhvjy.cn/Article/7859242.shtml
- https://www.read.hcbezg.cn/Article/05150.shtml
- https://www.read.nwbbyt.cn/Article/8260.shtml
- https://www.read.puhvjy.cn/Article/9524319.shtml
- https://www.read.fuvxie.cn/Article/8225764.shtml
- https://www.read.cmcvrr.cn/Article/6962.shtml
- https://www.read.nzfnve.cn/Article/20437.shtml
- https://www.read.cvsifc.cn/Article/8332.shtml
- https://www.read.puhvjy.cn/Article/016729.shtml
- https://www.read.fuvxie.cn/Article/12485.shtml
- https://www.read.hcbezg.cn/Article/6487.shtml
- https://www.read.fuvxie.cn/Article/48345.shtml
- https://www.read.fuvxie.cn/Article/9818.shtml
- https://www.read.cmcvrr.cn/Article/3128872.shtml
- https://www.read.cvsifc.cn/Article/8880.shtml
- https://www.read.fuvxie.cn/Article/52679.shtml
- https://www.read.jnjpgf.cn/Article/3397.shtml
- https://www.read.cvsifc.cn/Article/764304.shtml
- https://www.read.cvsifc.cn/Article/9983617.shtml
- https://www.read.nzfnve.cn/Article/997388.shtml
- https://www.read.cmcvrr.cn/Article/453182.shtml
- https://www.read.nzfnve.cn/Article/65335.shtml
- https://www.read.jnjpgf.cn/Article/8717.shtml
- https://www.read.cmcvrr.cn/Article/005039.shtml
- https://www.read.fuvxie.cn/Article/2005559.shtml
- https://www.read.cvsifc.cn/Article/65222.shtml
- https://www.read.cmcvrr.cn/Article/7359.shtml
- https://www.read.nwbbyt.cn/Article/96858.shtml
- https://www.read.hcbezg.cn/Article/31873.shtml
- https://www.read.nwbbyt.cn/Article/0174220.shtml
- https://www.read.nzfnve.cn/Article/3920.shtml
- https://www.read.fuvxie.cn/Article/2510198.shtml
- https://www.read.cvsifc.cn/Article/2107868.shtml
- https://www.read.cvsifc.cn/Article/5260.shtml
- https://www.read.nzfnve.cn/Article/66718.shtml
- https://www.read.puhvjy.cn/Article/325797.shtml
- https://www.read.fuvxie.cn/Article/267089.shtml
- https://www.read.jnjpgf.cn/Article/608292.shtml
- https://www.read.fuvxie.cn/Article/5554384.shtml
- https://www.read.cmcvrr.cn/Article/2176409.shtml
- https://www.read.nzfnve.cn/Article/21122.shtml
- https://www.read.fuvxie.cn/Article/1352290.shtml
- https://www.read.nzfnve.cn/Article/349879.shtml
- https://www.read.nwbbyt.cn/Article/6823147.shtml
- https://www.read.hcbezg.cn/Article/011780.shtml
- https://www.read.puhvjy.cn/Article/187748.shtml
- https://www.read.nwbbyt.cn/Article/938548.shtml
- https://www.read.hcbezg.cn/Article/7184573.shtml
- https://www.read.nzfnve.cn/Article/8064.shtml
- https://www.read.jnjpgf.cn/Article/2538095.shtml
- https://www.read.fuvxie.cn/Article/2588.shtml
- https://www.read.jnjpgf.cn/Article/86626.shtml
- https://www.read.fuvxie.cn/Article/3246482.shtml
- https://www.read.puhvjy.cn/Article/6162151.shtml
- https://www.read.nzfnve.cn/Article/817177.shtml
- https://www.read.jnjpgf.cn/Article/359379.shtml
- https://www.read.puhvjy.cn/Article/69787.shtml
- https://www.read.hcbezg.cn/Article/754209.shtml
- https://www.read.hcbezg.cn/Article/0601.shtml
- https://www.read.puhvjy.cn/Article/12976.shtml
- https://www.read.nzfnve.cn/Article/2851367.shtml
- https://www.read.cmcvrr.cn/Article/593579.shtml
- https://www.read.fuvxie.cn/Article/6650541.shtml
- https://www.read.cvsifc.cn/Article/7853.shtml
- https://www.read.puhvjy.cn/Article/287991.shtml
- https://www.read.cmcvrr.cn/Article/1730.shtml
- https://www.read.puhvjy.cn/Article/7424601.shtml
- https://www.read.fuvxie.cn/Article/4252440.shtml
- https://www.read.cvsifc.cn/Article/85805.shtml
- https://www.read.puhvjy.cn/Article/70046.shtml
- https://www.read.fuvxie.cn/Article/2737.shtml
- https://www.read.jnjpgf.cn/Article/9424.shtml
- https://www.read.nwbbyt.cn/Article/8727.shtml
- https://www.read.cvsifc.cn/Article/5160.shtml
- https://www.read.nzfnve.cn/Article/523395.shtml
- https://www.read.cvsifc.cn/Article/539375.shtml
- https://www.read.nwbbyt.cn/Article/27211.shtml
- https://www.read.hcbezg.cn/Article/82499.shtml
- https://www.read.jnjpgf.cn/Article/7594.shtml
- https://www.read.jnjpgf.cn/Article/655497.shtml
- https://www.read.cmcvrr.cn/Article/8918.shtml
- https://www.read.jnjpgf.cn/Article/51938.shtml
- https://www.read.jnjpgf.cn/Article/616901.shtml
- https://www.read.fuvxie.cn/Article/645952.shtml
- https://www.read.nwbbyt.cn/Article/25731.shtml
- https://www.read.nzfnve.cn/Article/1945.shtml
- https://www.read.cvsifc.cn/Article/5156.shtml
- https://www.read.cmcvrr.cn/Article/772297.shtml
- https://www.read.nzfnve.cn/Article/803990.shtml
- https://www.read.cvsifc.cn/Article/9203731.shtml
- https://www.read.nzfnve.cn/Article/0267433.shtml
- https://www.read.puhvjy.cn/Article/6785687.shtml
- https://www.read.cvsifc.cn/Article/2899.shtml
- https://www.read.nwbbyt.cn/Article/57148.shtml
- https://www.read.fuvxie.cn/Article/2654985.shtml
- https://www.read.cvsifc.cn/Article/1188559.shtml
- https://www.read.fuvxie.cn/Article/564160.shtml
- https://www.read.nwbbyt.cn/Article/51329.shtml
- https://www.read.cvsifc.cn/Article/24307.shtml
- https://www.read.fuvxie.cn/Article/8402.shtml
- https://www.read.hcbezg.cn/Article/1953.shtml
- https://www.read.fuvxie.cn/Article/8103.shtml
- https://www.read.cvsifc.cn/Article/3334567.shtml
- https://www.read.nwbbyt.cn/Article/5032464.shtml
- https://www.read.nzfnve.cn/Article/8313690.shtml
- https://www.read.fuvxie.cn/Article/537875.shtml
- https://www.read.jnjpgf.cn/Article/129272.shtml
- https://www.read.jnjpgf.cn/Article/159564.shtml
- https://www.read.cmcvrr.cn/Article/59679.shtml
- https://www.read.cmcvrr.cn/Article/737999.shtml
- https://www.read.cmcvrr.cn/Article/98246.shtml
- https://www.read.jnjpgf.cn/Article/894647.shtml
- https://www.read.nwbbyt.cn/Article/63054.shtml
- https://www.read.cmcvrr.cn/Article/1265.shtml
- https://www.read.cvsifc.cn/Article/4339.shtml
- https://www.read.nzfnve.cn/Article/428120.shtml
- https://www.read.hcbezg.cn/Article/38722.shtml
- https://www.read.hcbezg.cn/Article/5173793.shtml
- https://www.read.hcbezg.cn/Article/336931.shtml
- https://www.read.nzfnve.cn/Article/5654.shtml
- https://www.read.nwbbyt.cn/Article/8713080.shtml
- https://www.read.jnjpgf.cn/Article/8638.shtml
- https://www.read.cmcvrr.cn/Article/8317.shtml
- https://www.read.nwbbyt.cn/Article/0003596.shtml
- https://www.read.cvsifc.cn/Article/51279.shtml
- https://www.read.hcbezg.cn/Article/786848.shtml
- https://www.read.fuvxie.cn/Article/492755.shtml
- https://www.read.fuvxie.cn/Article/8905.shtml
- https://www.read.nzfnve.cn/Article/18978.shtml
- https://www.read.nwbbyt.cn/Article/584893.shtml
- https://www.read.fuvxie.cn/Article/87470.shtml
- https://www.read.cmcvrr.cn/Article/8239419.shtml
- https://www.read.fuvxie.cn/Article/595016.shtml
- https://www.read.cmcvrr.cn/Article/541448.shtml
- https://www.read.cvsifc.cn/Article/4465.shtml
- https://www.read.hcbezg.cn/Article/9006561.shtml
- https://www.read.hcbezg.cn/Article/1901.shtml
- https://www.read.fuvxie.cn/Article/2150.shtml
- https://www.read.cvsifc.cn/Article/766514.shtml
- https://www.read.fuvxie.cn/Article/1330638.shtml
- https://www.read.nzfnve.cn/Article/8896.shtml
- https://www.read.nwbbyt.cn/Article/68798.shtml
- https://www.read.jnjpgf.cn/Article/2064.shtml
- https://www.read.nwbbyt.cn/Article/7116191.shtml
- https://www.read.cmcvrr.cn/Article/333872.shtml
- https://www.read.cmcvrr.cn/Article/452998.shtml
- https://www.read.cmcvrr.cn/Article/4073373.shtml
- https://www.read.hcbezg.cn/Article/40773.shtml
- https://www.read.hcbezg.cn/Article/426069.shtml
- https://www.read.nzfnve.cn/Article/2574101.shtml
- https://www.read.cvsifc.cn/Article/6394033.shtml
- https://www.read.puhvjy.cn/Article/107360.shtml
- https://www.read.nzfnve.cn/Article/265564.shtml
- https://www.read.nwbbyt.cn/Article/609770.shtml
- https://www.read.jnjpgf.cn/Article/690618.shtml
- https://www.read.nwbbyt.cn/Article/2432.shtml
- https://www.read.jnjpgf.cn/Article/375364.shtml
- https://www.read.puhvjy.cn/Article/80204.shtml
- https://www.read.nwbbyt.cn/Article/81943.shtml
- https://www.read.fuvxie.cn/Article/3267197.shtml
- https://www.read.jnjpgf.cn/Article/47261.shtml
- https://www.read.fuvxie.cn/Article/925253.shtml
- https://www.read.hcbezg.cn/Article/820695.shtml
- https://www.read.hcbezg.cn/Article/931159.shtml
- https://www.read.nwbbyt.cn/Article/54381.shtml
- https://www.read.cmcvrr.cn/Article/9815554.shtml
- https://www.read.fuvxie.cn/Article/8257.shtml
- https://www.read.nzfnve.cn/Article/9740029.shtml
- https://www.read.cmcvrr.cn/Article/99667.shtml
- https://www.read.puhvjy.cn/Article/4279.shtml
- https://www.read.cmcvrr.cn/Article/8616.shtml
- https://www.read.cvsifc.cn/Article/8090629.shtml
- https://www.read.nzfnve.cn/Article/1722468.shtml
- https://www.read.cmcvrr.cn/Article/59014.shtml
- https://www.read.jnjpgf.cn/Article/287124.shtml
- https://www.read.cvsifc.cn/Article/378174.shtml
- https://www.read.fuvxie.cn/Article/0135503.shtml
- https://www.read.nwbbyt.cn/Article/000078.shtml
- https://www.read.cvsifc.cn/Article/4825.shtml
- https://www.read.cvsifc.cn/Article/32832.shtml
- https://www.read.puhvjy.cn/Article/228966.shtml
- https://www.read.cmcvrr.cn/Article/52300.shtml
- https://www.read.puhvjy.cn/Article/6131.shtml
- https://www.read.cmcvrr.cn/Article/4884.shtml
- https://www.read.nwbbyt.cn/Article/90816.shtml
- https://www.read.fuvxie.cn/Article/7692888.shtml
- https://www.read.puhvjy.cn/Article/018911.shtml
- https://www.read.cmcvrr.cn/Article/91147.shtml
- https://www.read.jnjpgf.cn/Article/295288.shtml
- https://www.read.cvsifc.cn/Article/76658.shtml
- https://www.read.hcbezg.cn/Article/56800.shtml
- https://www.read.cvsifc.cn/Article/8797080.shtml

## 项目结构

```
linkcollector/
├── bin/                                 # 可执行脚本与命令行入口
│   └── lc-cli.js                        # 命令行工具主入口，处理子命令分发
├── src/                                 # 核心源代码目录
│   ├── core/                            # 核心业务逻辑模块
│   │   ├── linkManager.js               # 链接的增删改查、去重与校验逻辑
│   │   ├── tagEngine.js                 # 标签的创建、合并、重命名与统计
│   │   └── snapshotService.js           # 数据快照的生成、存储与回滚
│   ├── server/                          # HTTP 服务与路由层
│   │   ├── app.js                       # Express 应用初始化与中间件配置
│   │   ├── routes.js                    # 所有 API 路由与页面路由定义
│   │   └── static/                      # 前端静态资源文件
│   │       ├── css/                     # 样式表文件
│   │       ├── js/                      # 前端交互脚本
│   │       └── index.html               # 主管理页面模板
│   ├── storage/                         # 数据持久化层
│   │   ├── fileAdapter.js               # 基于 JSON 文件的读写适配器
│   │   └── schema.js                    # 数据记录的结构定义与校验
│   └── utils/                           # 通用工具函数
│       ├── validator.js                 # URL 校验、标签格式校验工具
│       └── logger.js                    # 日志输出级别控制与格式化
├── tests/                               # 单元测试与集成测试
│   ├── unit/                            # 各模块单元测试用例
│   └── integration/                     # API 与存储层的集成测试
├── docs/                                # 项目文档
│   ├── user-guide.md                    # 用户使用手册
│   ├── operations.md                    # 运维与部署指南
│   ├── developer.md                     # 开发者文档
│   └── community.md                     # 社区协作规范
├── data/                                # 运行时数据目录（默认不纳入版本控制）
│   ├── links.json                       # 所有链接记录的持久化存储文件
│   └── snapshots/                       # 历史快照存储目录
├── .gitignore                           # Git 版本忽略规则
├── package.json                         # npm 项目配置文件，含依赖与脚本定义
├── package-lock.json                    # 依赖版本锁定文件
├── README.md                            # 项目自述文件（即本文档）
└── LICENSE                              # 项目许可证文件（MIT）
```

## 贡献指南

我们欢迎并感谢任何形式的贡献，包括但不限于提交链接资源、改进文档、报告问题或提交代码变更。请遵循以下步骤参与本项目：

1. 阅读社区规范文档 docs/community.md，了解链接提交标准、标签命名约定与状态使用规范，确保您的贡献符合项目统一风格。

2. 从 GitHub 仓库 Fork 本项目至您的个人账户，并在本地克隆您的 Fork 版本，创建新的功能分支进行修改，分支命名建议采用 feature/功能简述 或 fix/问题简述 格式。

3. 在本地完成修改后，运行测试套件确保所有现有功能未被破坏，若新增功能请同步添加对应的单元测试用例，保证代码覆盖率的稳定性。

4. 提交变更时请使用清晰且语义化的 commit message，格式遵循 Conventional Commits 规范，例如 fix: 修复链接去重逻辑在边界条件下的错误 或 feat: 新增按标签导出链接清单的功能。

5. 向本仓库的主分支发起 Pull Request，在 PR 描述中详细说明变更内容、动机以及测试情况，项目维护者会在 3 个工作日内进行审核与反馈。

## 常见问题

Q: LinkCollector 是否支持从数据库读取链接数据，而非 JSON 文件？

A: 当前版本仅提供基于 JSON 文件的存储适配器，适用于小型到中型的链接集合管理（建议链接数量不超过 5000 条）。若您需要对接 MySQL、PostgreSQL 或 MongoDB 等数据库，可参照 src/storage/fileAdapter.js 的接口定义自行实现相应的存储适配器，并在 app.js 中替换默认导入。项目后续版本将考虑提供官方数据库扩展包。

Q: 本地预览服务启动后，页面显示空白或无法加载链接列表，如何排查？

A: 首先检查浏览器控制台是否有错误输出，常见原因为 data/links.json 文件格式损坏或权限不足。您可以尝试删除 data/links.json 文件后重新启动服务，系统会自动生成初始空数据文件。若问题依然存在，请检查 3000 端口是否被其他进程占用，可通过 PORT 环境变量指定其他可用端口，例如 PORT=4000 npm start。

Q: 如何将本项目中收录的链接清单迁移到另一台机器上？

A: 您只需将整个 data/ 目录复制到目标机器的相同相对路径下，并确保目标机器已安装相同版本的 Node.js 与 npm。启动服务后，所有链接记录与状态信息将完整恢复。若需同时迁移标签配置与自定义设置，请一并复制根目录下的 config.json 文件（若存在）。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:20

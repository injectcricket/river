# DocLink Hub

DocLink Hub 是一个面向技术团队与内容管理者的外链资源归集与分发平台，专注于将分散于各类移动端 H5 页面的文档型资源（.doc 格式）进行结构化索引与统一导航。该项目定位为轻量级技术资源外链汇总中间件，不提供文件存储与上传功能，仅通过可配置的资源映射表实现外部文档链接的集中管理与快速检索。

项目核心目标用户包括技术文档维护人员、运维工程师、知识库管理员以及需要频繁引用外部技术附件的开发团队。通过 DocLink Hub，用户可以将来自多个源站点的文档外链整合为统一的资源清单，并借助内置的元数据筛选、分类标记与状态检测机制，有效降低链接散落、失效与重复管理带来的运维成本。

## 功能概览

**多源外链统一归集**：支持将多个移动端 H5 域名下的 .doc 文档链接整合至同一资源池，提供全局视图与批量操作入口。

**文档元信息自动解析**：在资源录入阶段自动提取 URL 路径中的域名特征与文档 ID，为后续分类与检索提供结构化基础。

**链接可用性周期性检测**：内置基于 HTTP HEAD 请求的存活检测模块，可定时扫描资源列表并标记异常链接，辅助管理员及时清理或更新。

**分类标签与自定义注释**：允许为每条外链附加业务标签（如“产品手册”、“接口定义”、“测试报告”）与运维备注，提升资源可读性。

**快速模糊检索与过滤**：提供基于域名、文档 ID 关键字、标签组合的多维度筛选能力，帮助用户在数百条链接中精准定位目标文档。

**资源导入与导出接口**：支持通过 JSON 或 CSV 格式批量导入链接清单，并支持将当前资源列表导出为结构化数据文件，便于备份或迁移。

**操作审计日志**：记录所有资源新增、删除、修改与检测操作，保留操作人、时间与变更详情，满足内部合规追溯需求。

**最小化依赖部署**：项目设计为无状态服务，仅依赖基础运行环境与轻量级数据库，可快速在内网或开发机上线。

## 应用场景

**技术文档中心的外链治理**：当企业内部多个业务系统分别托管在不同移动端 H5 站点上时，文档分散且难以统一查阅。DocLink Hub 可作为中间层将各站点的文档外链聚合为一个可搜索的资源目录，文档管理员只需维护一份清单即可对外提供一致的访问入口。

**自动化测试套件的测试数据准备**：测试工程师在编写自动化用例时，经常需要引用外部 .doc 格式的测试物料。通过 DocLink Hub 预先收录所有物料链接，测试脚本可直接从资源池中按标签拉取最新有效地址，避免硬编码 URL 导致维护困难。

**项目归档阶段的附件固化**：在项目结项或版本发布时，需要将所引用的全部外部文档进行备份与关联记录。运维人员可利用 DocLink Hub 的导出功能生成完整的资源快照清单，与项目文档一同归档，确保后续审计时所有外部引用均有迹可循。

**知识库文章的外链标准化**：知识库编辑人员在撰写技术方案时，常需要插入来自不同系统的参考文档链接。DocLink Hub 提供统一的短标识与检索接口，编辑者只需记忆资源 ID 或标签即可快速生成标准外链，降低文章中的链接冗余与错误率。

## 快速开始

以下步骤指导您在本机环境中快速启动 DocLink Hub 服务。

```bash
# 1. 克隆项目代码仓库
git clone https://github.com/your-org/doclink-hub.git

# 2. 进入项目根目录
cd doclink-hub

# 3. 安装项目依赖（基于 Node.js 22 LTS）
npm install

# 4. 复制默认配置文件并调整本地数据库连接
cp .env.example .env

# 5. 执行数据库迁移脚本，初始化所需数据表结构
npm run migrate

# 6. 启动开发服务器，默认监听 3000 端口
npm run dev
```

启动成功后，可通过浏览器访问 http://localhost:3000 进入资源管理控制台。首次启动将自动生成管理员账户，初始密码将在终端日志中输出，请及时修改。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 22.x LTS 或更高 | 项目运行时基础环境，建议使用官方 LTS 版本 |
| npm | 10.x 或更高 | 依赖包管理工具，随 Node.js 一同安装 |
| PostgreSQL | 15.x 或更高 | 主数据存储，用于保存资源映射、标签与审计日志 |
| Redis | 7.x 或更高 | 可选依赖，用于缓存链接检测结果与提升检索性能 |
| 操作系统 | Linux (Ubuntu 22.04) / macOS 14+ / Windows 11 | 开发与生产环境均支持，但建议使用 Linux 服务器部署 |
| 网络访问 | 能够访问外网或内网各源站点的 80/443 端口 | 用于链接存活检测与资源访问 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/getting-started.md | 如何快速搭建开发环境并导入第一批资源链接？ |
| 配置手册 | /docs/configuration.md | 如何调整链接检测频率、数据库连接池与日志级别？ |
| API 参考 | /docs/api-reference.md | 资源管理、检索与检测功能提供了哪些 RESTful 接口？ |
| 运维指南 | /docs/operations.md | 如何部署到生产环境、配置 HTTPS 与执行数据备份？ |
| 架构设计 | /docs/architecture.md | 项目的模块划分、数据流与关键技术选型是什么？ |

## 资源列表

- h5.mobile.nzfnve.cn/Article/3459312.doc
- h5.mobile.nwbbyt.cn/Article/142664.doc
- h5.mobile.nwbbyt.cn/Article/11881.doc
- h5.mobile.nwbbyt.cn/Article/563953.doc
- h5.mobile.jnjpgf.cn/Article/93373.doc
- h5.mobile.fuvxie.cn/Article/1415582.doc
- h5.mobile.cvsifc.cn/Article/73201.doc
- h5.mobile.cvsifc.cn/Article/689913.doc
- h5.mobile.cmcvrr.cn/Article/561095.doc
- h5.mobile.hcbezg.cn/Article/35106.doc
- h5.mobile.puhvjy.cn/Article/059943.doc
- h5.mobile.cvsifc.cn/Article/9197.doc
- h5.mobile.cvsifc.cn/Article/926724.doc
- h5.mobile.hcbezg.cn/Article/6488433.doc
- h5.mobile.puhvjy.cn/Article/5058.doc
- h5.mobile.fuvxie.cn/Article/00363.doc
- h5.mobile.fuvxie.cn/Article/1061.doc
- h5.mobile.cvsifc.cn/Article/12936.doc
- h5.mobile.nzfnve.cn/Article/133262.doc
- h5.mobile.nwbbyt.cn/Article/97302.doc
- h5.mobile.nwbbyt.cn/Article/6338.doc
- h5.mobile.nzfnve.cn/Article/61707.doc
- h5.mobile.cvsifc.cn/Article/9393.doc
- h5.mobile.cmcvrr.cn/Article/22031.doc
- h5.mobile.cvsifc.cn/Article/508008.doc
- h5.mobile.nwbbyt.cn/Article/75341.doc
- h5.mobile.puhvjy.cn/Article/33031.doc
- h5.mobile.nwbbyt.cn/Article/601018.doc
- h5.mobile.cvsifc.cn/Article/35639.doc
- h5.mobile.cvsifc.cn/Article/112670.doc
- h5.mobile.nwbbyt.cn/Article/177987.doc
- h5.mobile.jnjpgf.cn/Article/3758066.doc
- h5.mobile.nwbbyt.cn/Article/2153388.doc
- h5.mobile.hcbezg.cn/Article/5307.doc
- h5.mobile.nwbbyt.cn/Article/951227.doc
- h5.mobile.nzfnve.cn/Article/811240.doc
- h5.mobile.fuvxie.cn/Article/41417.doc
- h5.mobile.fuvxie.cn/Article/01780.doc
- h5.mobile.nzfnve.cn/Article/1271.doc
- h5.mobile.hcbezg.cn/Article/29467.doc
- h5.mobile.hcbezg.cn/Article/0162583.doc
- h5.mobile.fuvxie.cn/Article/116245.doc
- h5.mobile.fuvxie.cn/Article/2057.doc
- h5.mobile.cmcvrr.cn/Article/528478.doc
- h5.mobile.nzfnve.cn/Article/99766.doc
- h5.mobile.nzfnve.cn/Article/6826.doc
- h5.mobile.nwbbyt.cn/Article/7615331.doc
- h5.mobile.jnjpgf.cn/Article/856250.doc
- h5.mobile.hcbezg.cn/Article/7522095.doc
- h5.mobile.cmcvrr.cn/Article/3977.doc
- h5.mobile.jnjpgf.cn/Article/0156605.doc
- h5.mobile.cmcvrr.cn/Article/46586.doc
- h5.mobile.nzfnve.cn/Article/04173.doc
- h5.mobile.nzfnve.cn/Article/7897563.doc
- h5.mobile.jnjpgf.cn/Article/381320.doc
- h5.mobile.nzfnve.cn/Article/60370.doc
- h5.mobile.hcbezg.cn/Article/38274.doc
- h5.mobile.nwbbyt.cn/Article/3974.doc
- h5.mobile.jnjpgf.cn/Article/98272.doc
- h5.mobile.nwbbyt.cn/Article/6006.doc
- h5.mobile.puhvjy.cn/Article/8707549.doc
- h5.mobile.hcbezg.cn/Article/8044818.doc
- h5.mobile.hcbezg.cn/Article/29849.doc
- h5.mobile.nzfnve.cn/Article/42032.doc
- h5.mobile.nwbbyt.cn/Article/188698.doc
- h5.mobile.nzfnve.cn/Article/4553.doc
- h5.mobile.fuvxie.cn/Article/02532.doc
- h5.mobile.hcbezg.cn/Article/457021.doc
- h5.mobile.hcbezg.cn/Article/441487.doc
- h5.mobile.jnjpgf.cn/Article/0078.doc
- h5.mobile.jnjpgf.cn/Article/71375.doc
- h5.mobile.jnjpgf.cn/Article/5622.doc
- h5.mobile.hcbezg.cn/Article/6118.doc
- h5.mobile.nzfnve.cn/Article/250883.doc
- h5.mobile.jnjpgf.cn/Article/0425.doc
- h5.mobile.cmcvrr.cn/Article/871212.doc
- h5.mobile.nzfnve.cn/Article/4599.doc
- h5.mobile.nwbbyt.cn/Article/31692.doc
- h5.mobile.nzfnve.cn/Article/6532.doc
- h5.mobile.hcbezg.cn/Article/6096428.doc
- h5.mobile.cmcvrr.cn/Article/911938.doc
- h5.mobile.jnjpgf.cn/Article/8568.doc
- h5.mobile.puhvjy.cn/Article/86086.doc
- h5.mobile.nzfnve.cn/Article/324965.doc
- h5.mobile.nzfnve.cn/Article/9739248.doc
- h5.mobile.hcbezg.cn/Article/6408197.doc
- h5.mobile.nzfnve.cn/Article/9175.doc
- h5.mobile.cvsifc.cn/Article/276214.doc
- h5.mobile.cvsifc.cn/Article/86168.doc
- h5.mobile.nzfnve.cn/Article/88389.doc
- h5.mobile.fuvxie.cn/Article/1282108.doc
- h5.mobile.fuvxie.cn/Article/1966502.doc
- h5.mobile.nwbbyt.cn/Article/6043402.doc
- h5.mobile.cvsifc.cn/Article/0793830.doc
- h5.mobile.hcbezg.cn/Article/82844.doc
- h5.mobile.puhvjy.cn/Article/3621.doc
- h5.mobile.cvsifc.cn/Article/26590.doc
- h5.mobile.nwbbyt.cn/Article/4375067.doc
- h5.mobile.nzfnve.cn/Article/0044300.doc
- h5.mobile.jnjpgf.cn/Article/76216.doc
- h5.mobile.nwbbyt.cn/Article/0021.doc
- h5.mobile.jnjpgf.cn/Article/96819.doc
- h5.mobile.puhvjy.cn/Article/629820.doc
- h5.mobile.nwbbyt.cn/Article/96102.doc
- h5.mobile.cvsifc.cn/Article/94989.doc
- h5.mobile.jnjpgf.cn/Article/60214.doc
- h5.mobile.hcbezg.cn/Article/5654940.doc
- h5.mobile.puhvjy.cn/Article/7914.doc
- h5.mobile.puhvjy.cn/Article/5483344.doc
- h5.mobile.cvsifc.cn/Article/5362.doc
- h5.mobile.cmcvrr.cn/Article/013810.doc
- h5.mobile.jnjpgf.cn/Article/4291862.doc
- h5.mobile.nwbbyt.cn/Article/132203.doc
- h5.mobile.nzfnve.cn/Article/2321408.doc
- h5.mobile.cvsifc.cn/Article/76282.doc
- h5.mobile.nwbbyt.cn/Article/4337.doc
- h5.mobile.cvsifc.cn/Article/6181529.doc
- h5.mobile.puhvjy.cn/Article/671785.doc
- h5.mobile.cvsifc.cn/Article/0336.doc
- h5.mobile.hcbezg.cn/Article/67301.doc
- h5.mobile.cmcvrr.cn/Article/48178.doc
- h5.mobile.puhvjy.cn/Article/148808.doc
- h5.mobile.cmcvrr.cn/Article/63752.doc
- h5.mobile.cmcvrr.cn/Article/60306.doc
- h5.mobile.jnjpgf.cn/Article/384347.doc
- h5.mobile.nwbbyt.cn/Article/80584.doc
- h5.mobile.hcbezg.cn/Article/144100.doc
- h5.mobile.nzfnve.cn/Article/777026.doc
- h5.mobile.nwbbyt.cn/Article/4251819.doc
- h5.mobile.puhvjy.cn/Article/7747.doc
- h5.mobile.puhvjy.cn/Article/26638.doc
- h5.mobile.nzfnve.cn/Article/6487767.doc
- h5.mobile.nzfnve.cn/Article/86336.doc
- h5.mobile.nzfnve.cn/Article/5399825.doc
- h5.mobile.fuvxie.cn/Article/00922.doc
- h5.mobile.puhvjy.cn/Article/1901334.doc
- h5.mobile.nwbbyt.cn/Article/2556.doc
- h5.mobile.hcbezg.cn/Article/7775.doc
- h5.mobile.nwbbyt.cn/Article/07030.doc
- h5.mobile.fuvxie.cn/Article/04205.doc
- h5.mobile.cmcvrr.cn/Article/1067.doc
- h5.mobile.puhvjy.cn/Article/7744.doc
- h5.mobile.jnjpgf.cn/Article/0367.doc
- h5.mobile.nwbbyt.cn/Article/0413362.doc
- h5.mobile.jnjpgf.cn/Article/058967.doc
- h5.mobile.hcbezg.cn/Article/74489.doc
- h5.mobile.cmcvrr.cn/Article/8213.doc
- h5.mobile.hcbezg.cn/Article/1407.doc
- h5.mobile.nwbbyt.cn/Article/6366.doc
- h5.mobile.nwbbyt.cn/Article/459758.doc
- h5.mobile.hcbezg.cn/Article/7611.doc
- h5.mobile.cvsifc.cn/Article/02244.doc
- h5.mobile.cvsifc.cn/Article/70251.doc
- h5.mobile.cmcvrr.cn/Article/37740.doc
- h5.mobile.fuvxie.cn/Article/8762.doc
- h5.mobile.nwbbyt.cn/Article/7731720.doc
- h5.mobile.puhvjy.cn/Article/7564.doc
- h5.mobile.nzfnve.cn/Article/702651.doc
- h5.mobile.puhvjy.cn/Article/1949.doc
- h5.mobile.cmcvrr.cn/Article/546949.doc
- h5.mobile.puhvjy.cn/Article/7977906.doc
- h5.mobile.puhvjy.cn/Article/1882787.doc
- h5.mobile.fuvxie.cn/Article/9874.doc
- h5.mobile.cvsifc.cn/Article/8620634.doc
- h5.mobile.hcbezg.cn/Article/1948.doc
- h5.mobile.cvsifc.cn/Article/6917917.doc
- h5.mobile.nzfnve.cn/Article/1238.doc
- h5.mobile.cvsifc.cn/Article/47726.doc
- h5.mobile.hcbezg.cn/Article/5672.doc
- h5.mobile.jnjpgf.cn/Article/891715.doc
- h5.mobile.nzfnve.cn/Article/44208.doc
- h5.mobile.nzfnve.cn/Article/66316.doc
- h5.mobile.nwbbyt.cn/Article/353975.doc
- h5.mobile.nzfnve.cn/Article/145761.doc
- h5.mobile.cvsifc.cn/Article/5549785.doc
- h5.mobile.hcbezg.cn/Article/2843113.doc
- h5.mobile.hcbezg.cn/Article/298056.doc
- h5.mobile.fuvxie.cn/Article/07411.doc
- h5.mobile.hcbezg.cn/Article/60463.doc
- h5.mobile.fuvxie.cn/Article/96132.doc
- h5.mobile.cvsifc.cn/Article/99904.doc
- h5.mobile.nzfnve.cn/Article/787829.doc
- h5.mobile.cmcvrr.cn/Article/7979.doc
- h5.mobile.puhvjy.cn/Article/47004.doc
- h5.mobile.cmcvrr.cn/Article/2980.doc
- h5.mobile.cvsifc.cn/Article/14834.doc
- h5.mobile.cvsifc.cn/Article/57463.doc
- h5.mobile.fuvxie.cn/Article/214783.doc
- h5.mobile.fuvxie.cn/Article/9755607.doc
- h5.mobile.fuvxie.cn/Article/3274.doc
- h5.mobile.hcbezg.cn/Article/2012.doc
- h5.mobile.puhvjy.cn/Article/2163122.doc
- h5.mobile.cvsifc.cn/Article/220992.doc
- h5.mobile.nwbbyt.cn/Article/510879.doc
- h5.mobile.hcbezg.cn/Article/664548.doc
- h5.mobile.nzfnve.cn/Article/51577.doc
- h5.mobile.jnjpgf.cn/Article/079276.doc
- h5.mobile.puhvjy.cn/Article/7303599.doc
- h5.mobile.cvsifc.cn/Article/2625035.doc
- h5.mobile.fuvxie.cn/Article/5497739.doc
- h5.mobile.hcbezg.cn/Article/9843992.doc
- h5.mobile.cvsifc.cn/Article/4800524.doc
- h5.mobile.puhvjy.cn/Article/021250.doc
- h5.mobile.puhvjy.cn/Article/247541.doc
- h5.mobile.hcbezg.cn/Article/6497500.doc
- h5.mobile.cmcvrr.cn/Article/0818450.doc
- h5.mobile.hcbezg.cn/Article/16514.doc
- h5.mobile.puhvjy.cn/Article/8723224.doc
- h5.mobile.hcbezg.cn/Article/8679.doc
- h5.mobile.puhvjy.cn/Article/9366.doc
- h5.mobile.nzfnve.cn/Article/05841.doc
- h5.mobile.puhvjy.cn/Article/33013.doc
- h5.mobile.nzfnve.cn/Article/771435.doc
- h5.mobile.nwbbyt.cn/Article/5817.doc
- h5.mobile.nzfnve.cn/Article/9447.doc
- h5.mobile.nwbbyt.cn/Article/76480.doc
- h5.mobile.jnjpgf.cn/Article/047167.doc
- h5.mobile.nwbbyt.cn/Article/5337003.doc
- h5.mobile.fuvxie.cn/Article/3150.doc
- h5.mobile.jnjpgf.cn/Article/7767.doc
- h5.mobile.hcbezg.cn/Article/1850.doc
- h5.mobile.cmcvrr.cn/Article/8781933.doc
- h5.mobile.fuvxie.cn/Article/10425.doc
- h5.mobile.fuvxie.cn/Article/8779.doc
- h5.mobile.nzfnve.cn/Article/2715848.doc
- h5.mobile.cmcvrr.cn/Article/416348.doc
- h5.mobile.puhvjy.cn/Article/05211.doc
- h5.mobile.jnjpgf.cn/Article/656788.doc
- h5.mobile.fuvxie.cn/Article/31319.doc
- h5.mobile.puhvjy.cn/Article/7291043.doc
- h5.mobile.nwbbyt.cn/Article/23815.doc
- h5.mobile.nwbbyt.cn/Article/7912869.doc
- h5.mobile.puhvjy.cn/Article/2529724.doc
- h5.mobile.jnjpgf.cn/Article/08499.doc
- h5.mobile.hcbezg.cn/Article/7657.doc
- h5.mobile.jnjpgf.cn/Article/7626.doc
- h5.mobile.puhvjy.cn/Article/0107604.doc
- h5.mobile.nwbbyt.cn/Article/6789.doc
- h5.mobile.cmcvrr.cn/Article/3574.doc
- h5.mobile.nzfnve.cn/Article/203822.doc
- h5.mobile.cvsifc.cn/Article/040262.doc
- h5.mobile.nwbbyt.cn/Article/336229.doc
- h5.mobile.jnjpgf.cn/Article/49360.doc
- h5.mobile.cmcvrr.cn/Article/8547777.doc
- h5.mobile.hcbezg.cn/Article/6840.doc
- h5.mobile.hcbezg.cn/Article/95919.doc
- h5.mobile.nzfnve.cn/Article/36003.doc
- h5.mobile.hcbezg.cn/Article/979722.doc
- h5.mobile.cmcvrr.cn/Article/062323.doc
- h5.mobile.fuvxie.cn/Article/0270767.doc

## 项目结构

```
doclink-hub/
├── src/                               # 核心源代码目录
│   ├── controllers/                   # 请求控制器层，处理路由入参校验与响应封装
│   ├── services/                      # 业务逻辑层，包含资源管理、链接检测与标签服务
│   ├── repositories/                  # 数据访问层，封装 PostgreSQL 与 Redis 的 CRUD 操作
│   ├── models/                        # 数据实体定义与 ORM 映射配置
│   ├── middleware/                    # 中间件栈，含鉴权、日志记录与全局异常处理
│   ├── utils/                         # 通用工具函数，包括 URL 解析、HTTP 客户端与日期格式化
│   ├── scheduler/                     # 定时任务调度模块，驱动链接存活检测与缓存刷新
│   └── app.js                         # 应用入口文件，负责初始化 Express 应用与依赖容器
├── config/                            # 环境配置目录
│   ├── default.yaml                   # 默认配置项，包含端口、数据库连接池默认值
│   ├── development.yaml               # 开发环境覆盖配置，开启调试日志与热重载
│   └── production.yaml                # 生产环境覆盖配置，启用压缩与 HTTPS 强制跳转
├── migrations/                        # 数据库迁移脚本目录，按版本号管理表结构变更
├── seeders/                           # 初始数据填充脚本，用于创建默认管理员与标签预设
├── tests/                             # 单元测试与集成测试套件，基于 Jest 框架
│   ├── unit/                          # 针对 service 层与 utils 的独立测试用例
│   └── integration/                   # 基于超融合测试数据库的 API 端到端测试
├── docs/                              # 项目文档目录，包含入门指南、API 参考与架构说明
├── scripts/                           # 运维辅助脚本，包含备份、恢复与数据迁移工具
├── .env.example                       # 环境变量模板文件，供开发者复制为 .env 使用
├── .eslintrc.js                       # ESLint 代码规范检查配置文件
├── .prettierrc                        # Prettier 代码格式化配置
├── package.json                       # npm 依赖清单与项目脚本定义
├── package-lock.json                  # 依赖锁文件，锁定精确版本
├── Dockerfile                         # 容器化构建文件，用于生产环境镜像生成
├── docker-compose.yml                 # 本地开发环境容器编排，集成 PostgreSQL 与 Redis
└── README.md                          # 项目说明文档（即本文档）
```

## 贡献指南

1. 查阅 issue 列表或新建 issue 描述您希望修复的问题或新增的功能，等待维护者确认需求范围，避免无效提交。

2. 从项目仓库派生（fork）一份代码副本至您的个人账户，并在本地将派生仓库克隆到开发环境中。

3. 创建新的功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式，确保与主分支保持同步。

4. 完成代码修改后，需补充或更新对应的单元测试用例，确保所有测试通过，并遵循项目现有的 ESLint 与 Prettier 代码风格规范。

5. 向主仓库的 `develop` 分支提交拉取请求（pull request），在请求描述中清晰说明变更内容、影响范围以及关联的 issue 编号，等待代码审查与合并。

## 常见问题

**问：资源列表中的某些链接无法访问，系统如何处理？**

答：DocLink Hub 的定时检测模块会按可配置的间隔（默认每小时）对每条外链发起 HTTP HEAD 请求。若连续三次检测均返回非 2xx 状态码或超时，该链接会被自动标记为“异常”状态，并在管理控制台的高亮区域展示。管理员可以手动重新检测或批量导出异常列表进行外链更新。异常链接不会被自动删除，以免破坏历史引用记录。

**问：项目是否支持导入其他格式的资源清单，比如 Excel 或 XML？**

答：当前版本原生支持 JSON 与 CSV 格式的批量导入导出。若需要处理 Excel（.xlsx）或 XML 文件，可使用项目提供的转换脚本（位于 /scripts/convert 目录下）将外部格式转换为标准 CSV 后再导入。后续版本将考虑增加对更多格式的直接解析支持。

**问：部署到生产环境时，PostgreSQL 与 Redis 的最低资源配置建议是什么？**

答：对于中小规模资源池（低于 5000 条链接），建议 PostgreSQL 配置至少 1 核 CPU 与 2 GB 内存，Redis 配置 1 GB 内存即可。链接检测任务会占用一定数据库连接数，建议将连接池大小设置为 20。若资源数量超过 10000 条，推荐将检测任务单独部署为 Worker 进程，并升级数据库至 4 GB 内存以上。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

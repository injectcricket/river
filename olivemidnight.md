# DocLink Hub

DocLink Hub 是一个面向技术团队与内容运营人员的轻量化文档外链管理与资源聚合平台。项目定位为技术资源与外链的集中式导航系统，用于解决多源文档分散、链接失效、检索效率低等常见问题，提供统一的文档索引、状态监测与快速访问能力。该项目适用于需要维护大量外部文档链接的中小型技术团队、开源项目文档站、企业内部知识库以及个人技术博客的扩展管理。

DocLink Hub 不依赖复杂的前端框架，核心基于静态站点生成与元数据管理，可部署于任意支持静态托管的平台，或作为现有文档站点的外链中台使用。

## 功能概览

外链资源批量录入与分类管理：支持按来源域名、文档类型、更新批次对链接进行分组与标签化管理。

文档状态自动检查与失效标记：通过定时任务对已收录链接进行可达性检测，标注异常状态。

多级检索与筛选机制：提供基于关键字、域名、文件类型、批次号的组合过滤能力。

自定义文档元数据扩展：允许为每个链接附加备注、优先级、关联项目等自定义字段。

静态站点生成与一键导出：将资源列表输出为静态 HTML 或 Markdown 格式，便于集成到现有文档站点。

访问日志与热点统计：记录文档点击频次，辅助识别高频使用的核心资源。

权限分级控制：支持只读访客、编辑者、管理员三级角色，适用于团队协作场景。

## 应用场景

技术文档站外链整合：技术团队在维护项目文档时，需要引用大量外部规范、设计文档或技术提案。DocLink Hub 可作为独立的引用仓库，集中存放这些外链，避免在文档正文中散落大量 URL，同时提供链接有效性检测。

开源项目资源导航：开源项目通常需要关联依赖库、参考文档、社区讨论帖等多个外部资源。项目维护者可将所有相关链接收录至 DocLink Hub，并以导航页形式提供给贡献者，降低新手查找门槛。

企业内部知识库辅助管理：企业内部存在大量分散于邮件、即时通讯或共享目录中的文档引用。DocLink Hub 可作为统一入口，将各部门共享的文档链接集中管理，并支持按部门或项目维度筛选。

个人技术博客参考来源管理：技术博主在写作时需引用大量外部资料。通过 DocLink Hub 管理这些引用链接，可在文章末尾自动生成参考列表，并在链接失效时及时发现替换。

多批次资源归档与版本追溯：对于需要长期维护的文档资源集合（如标准规范库、历史会议记录），DocLink Hub 支持按批次导入（如当前第 143/160 批），便于追溯资源来源与更新历史。

## 快速开始

以下步骤帮助您在本地环境快速启动 DocLink Hub 服务。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/doclink-hub.git

# 进入项目目录
cd doclink-hub

# 安装依赖（基于 Python 3.10+）
pip install -r requirements.txt

# 执行本地开发运行
python app.py --port 8080
```

启动后，访问 http://localhost:8080 即可查看资源列表首页。默认管理员账号为 admin，初始密码在首次启动时输出至控制台日志。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 及以上 | 核心运行环境，用于后端 API 与调度服务 |
| SQLite | 3.35 及以上 | 内置轻量级数据库，用于存储链接元数据与状态 |
| requests | 2.28.0 及以上 | 用于外链可达性检测与状态检查 |
| markdown | 3.4.0 及以上 | 用于生成静态文档预览与导出 |
| beautifulsoup4 | 4.11.0 及以上 | 用于解析文档标题与元信息提取 |
| gunicorn | 20.1.0 及以上 | 生产环境推荐部署的 WSGI 服务器 |
| 操作系统 | Linux / macOS / Windows WSL2 | 支持主流 Unix-like 及 Windows 子系统 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/quickstart.md | 如何最快上手使用 DocLink Hub 进行链接管理 |
| 操作手册 | /docs/usage.md | 如何进行批量导入、分类筛选与状态检查 |
| 部署指南 | /docs/deployment.md | 如何将系统部署到生产环境（Nginx + Gunicorn） |
| API 参考 | /docs/api.md | 如何通过 REST API 进行资源增删改查与批量操作 |
| 元数据配置 | /docs/metadata.md | 如何自定义扩展字段与标签体系 |
| 常见问题 | /docs/faq.md | 遇到链接检测超时、导入失败等问题如何解决 |

## 资源列表

- h5.mobile.puhvjy.cn/Article/1715.doc
- h5.mobile.nwbbyt.cn/Article/7161.doc
- h5.mobile.nzfnve.cn/Article/64369.doc
- h5.mobile.hcbezg.cn/Article/102856.doc
- h5.mobile.puhvjy.cn/Article/176042.doc
- h5.mobile.puhvjy.cn/Article/354884.doc
- h5.mobile.jnjpgf.cn/Article/11522.doc
- h5.mobile.hcbezg.cn/Article/050667.doc
- h5.mobile.fuvxie.cn/Article/6127257.doc
- h5.mobile.hcbezg.cn/Article/762689.doc
- h5.mobile.cvsifc.cn/Article/1869.doc
- h5.mobile.fuvxie.cn/Article/8857483.doc
- h5.mobile.puhvjy.cn/Article/730897.doc
- h5.mobile.fuvxie.cn/Article/1122.doc
- h5.mobile.fuvxie.cn/Article/26420.doc
- h5.mobile.nzfnve.cn/Article/80560.doc
- h5.mobile.cmcvrr.cn/Article/32513.doc
- h5.mobile.puhvjy.cn/Article/164715.doc
- h5.mobile.puhvjy.cn/Article/5238535.doc
- h5.mobile.puhvjy.cn/Article/6372.doc
- h5.mobile.cvsifc.cn/Article/2351275.doc
- h5.mobile.nzfnve.cn/Article/3350.doc
- h5.mobile.fuvxie.cn/Article/76998.doc
- h5.mobile.fuvxie.cn/Article/2200560.doc
- h5.mobile.fuvxie.cn/Article/099545.doc
- h5.mobile.fuvxie.cn/Article/1525916.doc
- h5.mobile.jnjpgf.cn/Article/09232.doc
- h5.mobile.puhvjy.cn/Article/2352238.doc
- h5.mobile.hcbezg.cn/Article/539785.doc
- h5.mobile.hcbezg.cn/Article/9075.doc
- h5.mobile.puhvjy.cn/Article/20087.doc
- h5.mobile.cmcvrr.cn/Article/3789514.doc
- h5.mobile.fuvxie.cn/Article/566752.doc
- h5.mobile.jnjpgf.cn/Article/953158.doc
- h5.mobile.jnjpgf.cn/Article/8824.doc
- h5.mobile.nwbbyt.cn/Article/1893.doc
- h5.mobile.cmcvrr.cn/Article/062325.doc
- h5.mobile.nwbbyt.cn/Article/78135.doc
- h5.mobile.hcbezg.cn/Article/85718.doc
- h5.mobile.nzfnve.cn/Article/235332.doc
- h5.mobile.hcbezg.cn/Article/5977.doc
- h5.mobile.nzfnve.cn/Article/3985.doc
- h5.mobile.nzfnve.cn/Article/3147106.doc
- h5.mobile.puhvjy.cn/Article/784583.doc
- h5.mobile.puhvjy.cn/Article/5427710.doc
- h5.mobile.cmcvrr.cn/Article/112087.doc
- h5.mobile.jnjpgf.cn/Article/3597.doc
- h5.mobile.hcbezg.cn/Article/4973716.doc
- h5.mobile.fuvxie.cn/Article/371829.doc
- h5.mobile.cmcvrr.cn/Article/988787.doc
- h5.mobile.jnjpgf.cn/Article/5407766.doc
- h5.mobile.cvsifc.cn/Article/0332552.doc
- h5.mobile.cvsifc.cn/Article/40839.doc
- h5.mobile.puhvjy.cn/Article/30660.doc
- h5.mobile.cmcvrr.cn/Article/505706.doc
- h5.mobile.hcbezg.cn/Article/6450.doc
- h5.mobile.jnjpgf.cn/Article/52385.doc
- h5.mobile.fuvxie.cn/Article/67793.doc
- h5.mobile.cvsifc.cn/Article/836160.doc
- h5.mobile.fuvxie.cn/Article/0834089.doc
- h5.mobile.nzfnve.cn/Article/31992.doc
- h5.mobile.cmcvrr.cn/Article/208757.doc
- h5.mobile.nwbbyt.cn/Article/549472.doc
- h5.mobile.jnjpgf.cn/Article/4827.doc
- h5.mobile.puhvjy.cn/Article/65799.doc
- h5.mobile.nwbbyt.cn/Article/29678.doc
- h5.mobile.cmcvrr.cn/Article/0218.doc
- h5.mobile.fuvxie.cn/Article/2541705.doc
- h5.mobile.cmcvrr.cn/Article/3850.doc
- h5.mobile.cmcvrr.cn/Article/452988.doc
- h5.mobile.nzfnve.cn/Article/6866614.doc
- h5.mobile.nzfnve.cn/Article/6199.doc
- h5.mobile.nzfnve.cn/Article/1721.doc
- h5.mobile.jnjpgf.cn/Article/0800341.doc
- h5.mobile.nwbbyt.cn/Article/645339.doc
- h5.mobile.nzfnve.cn/Article/6621.doc
- h5.mobile.cvsifc.cn/Article/2480349.doc
- h5.mobile.cvsifc.cn/Article/12461.doc
- h5.mobile.cvsifc.cn/Article/13453.doc
- h5.mobile.cmcvrr.cn/Article/5872157.doc
- h5.mobile.puhvjy.cn/Article/6405.doc
- h5.mobile.nzfnve.cn/Article/6055716.doc
- h5.mobile.cvsifc.cn/Article/193500.doc
- h5.mobile.cmcvrr.cn/Article/7096.doc
- h5.mobile.nzfnve.cn/Article/0086548.doc
- h5.mobile.fuvxie.cn/Article/3525.doc
- h5.mobile.cvsifc.cn/Article/766001.doc
- h5.mobile.nwbbyt.cn/Article/5553575.doc
- h5.mobile.hcbezg.cn/Article/8862.doc
- h5.mobile.nzfnve.cn/Article/69677.doc
- h5.mobile.fuvxie.cn/Article/62572.doc
- h5.mobile.fuvxie.cn/Article/1464.doc
- h5.mobile.hcbezg.cn/Article/9869220.doc
- h5.mobile.jnjpgf.cn/Article/5603007.doc
- h5.mobile.hcbezg.cn/Article/81752.doc
- h5.mobile.cvsifc.cn/Article/3277.doc
- h5.mobile.cmcvrr.cn/Article/10286.doc
- h5.mobile.cvsifc.cn/Article/81120.doc
- h5.mobile.cmcvrr.cn/Article/572614.doc
- h5.mobile.cvsifc.cn/Article/303575.doc
- h5.mobile.hcbezg.cn/Article/940810.doc
- h5.mobile.puhvjy.cn/Article/2739203.doc
- h5.mobile.cmcvrr.cn/Article/94376.doc
- h5.mobile.cmcvrr.cn/Article/75746.doc
- h5.mobile.fuvxie.cn/Article/476413.doc
- h5.mobile.hcbezg.cn/Article/331627.doc
- h5.mobile.nzfnve.cn/Article/7351.doc
- h5.mobile.hcbezg.cn/Article/9232.doc
- h5.mobile.cvsifc.cn/Article/71297.doc
- h5.mobile.nwbbyt.cn/Article/7677670.doc
- h5.mobile.nzfnve.cn/Article/81008.doc
- h5.mobile.cvsifc.cn/Article/692241.doc
- h5.mobile.hcbezg.cn/Article/70534.doc
- h5.mobile.hcbezg.cn/Article/60842.doc
- h5.mobile.jnjpgf.cn/Article/881649.doc
- h5.mobile.cmcvrr.cn/Article/1598.doc
- h5.mobile.hcbezg.cn/Article/37986.doc
- h5.mobile.puhvjy.cn/Article/31993.doc
- h5.mobile.nzfnve.cn/Article/890254.doc
- h5.mobile.jnjpgf.cn/Article/857921.doc
- h5.mobile.fuvxie.cn/Article/3513.doc
- h5.mobile.nzfnve.cn/Article/19152.doc
- h5.mobile.puhvjy.cn/Article/86098.doc
- h5.mobile.cmcvrr.cn/Article/8165593.doc
- h5.mobile.cvsifc.cn/Article/11375.doc
- h5.mobile.hcbezg.cn/Article/662011.doc
- h5.mobile.cvsifc.cn/Article/28915.doc
- h5.mobile.jnjpgf.cn/Article/2338472.doc
- h5.mobile.cmcvrr.cn/Article/789029.doc
- h5.mobile.puhvjy.cn/Article/467793.doc
- h5.mobile.cmcvrr.cn/Article/5000.doc
- h5.mobile.cvsifc.cn/Article/7836315.doc
- h5.mobile.nwbbyt.cn/Article/9783452.doc
- h5.mobile.cvsifc.cn/Article/10123.doc
- h5.mobile.fuvxie.cn/Article/3291.doc
- h5.mobile.hcbezg.cn/Article/6524621.doc
- h5.mobile.fuvxie.cn/Article/3853910.doc
- h5.mobile.fuvxie.cn/Article/3703286.doc
- h5.mobile.cvsifc.cn/Article/79756.doc
- h5.mobile.hcbezg.cn/Article/3050301.doc
- h5.mobile.puhvjy.cn/Article/9459.doc
- h5.mobile.fuvxie.cn/Article/5531.doc
- h5.mobile.fuvxie.cn/Article/4566213.doc
- h5.mobile.cmcvrr.cn/Article/14020.doc
- h5.mobile.fuvxie.cn/Article/946956.doc
- h5.mobile.jnjpgf.cn/Article/50081.doc
- h5.mobile.fuvxie.cn/Article/96100.doc
- h5.mobile.hcbezg.cn/Article/417752.doc
- h5.mobile.cvsifc.cn/Article/219752.doc
- h5.mobile.nzfnve.cn/Article/179402.doc
- h5.mobile.nzfnve.cn/Article/2668.doc
- h5.mobile.nwbbyt.cn/Article/9177475.doc
- h5.mobile.hcbezg.cn/Article/0351.doc
- h5.mobile.nwbbyt.cn/Article/9730428.doc
- h5.mobile.nzfnve.cn/Article/20250.doc
- h5.mobile.nwbbyt.cn/Article/8941.doc
- h5.mobile.jnjpgf.cn/Article/77442.doc
- h5.mobile.cmcvrr.cn/Article/16393.doc
- h5.mobile.fuvxie.cn/Article/28543.doc
- h5.mobile.fuvxie.cn/Article/36625.doc
- h5.mobile.cvsifc.cn/Article/125766.doc
- h5.mobile.nzfnve.cn/Article/988119.doc
- h5.mobile.nzfnve.cn/Article/28349.doc
- h5.mobile.cmcvrr.cn/Article/03284.doc
- h5.mobile.jnjpgf.cn/Article/584206.doc
- h5.mobile.nwbbyt.cn/Article/6129971.doc
- h5.mobile.cmcvrr.cn/Article/42442.doc
- h5.mobile.cmcvrr.cn/Article/26048.doc
- h5.mobile.puhvjy.cn/Article/3157555.doc
- h5.mobile.fuvxie.cn/Article/5944920.doc
- h5.mobile.jnjpgf.cn/Article/4233088.doc
- h5.mobile.fuvxie.cn/Article/357313.doc
- h5.mobile.nwbbyt.cn/Article/37149.doc
- h5.mobile.nzfnve.cn/Article/0161497.doc
- h5.mobile.cmcvrr.cn/Article/43064.doc
- h5.mobile.nzfnve.cn/Article/15414.doc
- h5.mobile.puhvjy.cn/Article/179468.doc
- h5.mobile.nzfnve.cn/Article/59304.doc
- h5.mobile.hcbezg.cn/Article/2681921.doc
- h5.mobile.nwbbyt.cn/Article/4696.doc
- h5.mobile.nwbbyt.cn/Article/010648.doc
- h5.mobile.fuvxie.cn/Article/0771.doc
- h5.mobile.puhvjy.cn/Article/9886742.doc
- h5.mobile.fuvxie.cn/Article/37205.doc
- h5.mobile.nwbbyt.cn/Article/333539.doc
- h5.mobile.fuvxie.cn/Article/016762.doc
- h5.mobile.fuvxie.cn/Article/84873.doc
- h5.mobile.nzfnve.cn/Article/4952.doc
- h5.mobile.nwbbyt.cn/Article/630072.doc
- h5.mobile.nwbbyt.cn/Article/70822.doc
- h5.mobile.cmcvrr.cn/Article/87708.doc
- h5.mobile.jnjpgf.cn/Article/504510.doc
- h5.mobile.cvsifc.cn/Article/7866.doc
- h5.mobile.fuvxie.cn/Article/7206731.doc
- h5.mobile.puhvjy.cn/Article/5800.doc
- h5.mobile.cmcvrr.cn/Article/7777.doc
- h5.mobile.cvsifc.cn/Article/20544.doc
- h5.mobile.hcbezg.cn/Article/674036.doc
- h5.mobile.fuvxie.cn/Article/5317477.doc
- h5.mobile.hcbezg.cn/Article/34340.doc
- h5.mobile.nwbbyt.cn/Article/3696.doc
- h5.mobile.nzfnve.cn/Article/2456157.doc
- h5.mobile.nzfnve.cn/Article/44562.doc
- h5.mobile.cmcvrr.cn/Article/8376.doc
- h5.mobile.nzfnve.cn/Article/2965096.doc
- h5.mobile.cvsifc.cn/Article/8934.doc
- h5.mobile.puhvjy.cn/Article/1121069.doc
- h5.mobile.hcbezg.cn/Article/1078.doc
- h5.mobile.cmcvrr.cn/Article/913678.doc
- h5.mobile.fuvxie.cn/Article/5345302.doc
- h5.mobile.fuvxie.cn/Article/22256.doc
- h5.mobile.cvsifc.cn/Article/5929732.doc
- h5.mobile.nzfnve.cn/Article/3385.doc
- h5.mobile.hcbezg.cn/Article/69463.doc
- h5.mobile.hcbezg.cn/Article/2591.doc
- h5.mobile.jnjpgf.cn/Article/658354.doc
- h5.mobile.cvsifc.cn/Article/0134738.doc
- h5.mobile.fuvxie.cn/Article/15935.doc
- h5.mobile.nzfnve.cn/Article/722996.doc
- h5.mobile.nzfnve.cn/Article/76589.doc
- h5.mobile.cvsifc.cn/Article/4289.doc
- h5.mobile.nzfnve.cn/Article/6913.doc
- h5.mobile.puhvjy.cn/Article/65731.doc
- h5.mobile.hcbezg.cn/Article/7054237.doc
- h5.mobile.puhvjy.cn/Article/91082.doc
- h5.mobile.cvsifc.cn/Article/6886.doc
- h5.mobile.fuvxie.cn/Article/447707.doc
- h5.mobile.cmcvrr.cn/Article/1704917.doc
- h5.mobile.fuvxie.cn/Article/01436.doc
- h5.mobile.fuvxie.cn/Article/63652.doc
- h5.mobile.cmcvrr.cn/Article/27421.doc
- h5.mobile.hcbezg.cn/Article/0534.doc
- h5.mobile.nwbbyt.cn/Article/8611.doc
- h5.mobile.hcbezg.cn/Article/8852849.doc
- h5.mobile.cvsifc.cn/Article/911280.doc
- h5.mobile.jnjpgf.cn/Article/015974.doc
- h5.mobile.cvsifc.cn/Article/12618.doc
- h5.mobile.hcbezg.cn/Article/427230.doc
- h5.mobile.cvsifc.cn/Article/960942.doc
- h5.mobile.puhvjy.cn/Article/9554505.doc
- h5.mobile.nzfnve.cn/Article/5101281.doc
- h5.mobile.fuvxie.cn/Article/7021.doc
- h5.mobile.nzfnve.cn/Article/7792974.doc
- h5.mobile.puhvjy.cn/Article/125558.doc
- h5.mobile.nzfnve.cn/Article/1409891.doc
- h5.mobile.nzfnve.cn/Article/7983257.doc
- h5.mobile.nwbbyt.cn/Article/53889.doc
- h5.mobile.jnjpgf.cn/Article/83700.doc
- h5.mobile.nwbbyt.cn/Article/198754.doc
- h5.mobile.hcbezg.cn/Article/3419443.doc

## 项目结构

项目采用分层架构设计，核心模块与辅助工具分离，便于维护与扩展。

```
doclink-hub/
├── app/                               # 主应用目录
│   ├── __init__.py                    # 应用初始化与工厂函数
│   ├── routes/                        # 路由层，处理 HTTP 请求
│   │   ├── index.py                   # 首页及资源列表展示
│   │   ├── api.py                     # RESTful API 端点实现
│   │   └── admin.py                   # 后台管理界面路由
│   ├── models/                        # 数据模型层
│   │   ├── link.py                    # 链接实体模型定义
│   │   ├── batch.py                   # 批次与导入记录模型
│   │   └── user.py                    # 用户与权限模型
│   ├── services/                      # 业务逻辑层
│   │   ├── checker.py                 # 链接状态检查服务
│   │   ├── importer.py                # 批量导入与解析服务
│   │   └── exporter.py                # 静态站点导出服务
│   ├── utils/                         # 工具函数集合
│   │   ├── http.py                    # HTTP 请求封装与重试策略
│   │   ├── parser.py                  # 文档元信息解析工具
│   │   └── validators.py              # 链接格式与域名校验
│   └── templates/                     # 前端模板文件
│       ├── base.html                  # 基础页面骨架
│       ├── list.html                  # 资源列表渲染模板
│       └── detail.html                # 单个资源详情页
├── config/                            # 配置管理
│   ├── default.py                     # 默认配置项
│   ├── production.py                  # 生产环境覆盖配置
│   └── development.py                 # 开发环境覆盖配置
├── scripts/                           # 运维与辅助脚本
│   ├── check_links.py                 # 手动触发链接检查脚本
│   ├── import_batch.py                # 命令行批量导入工具
│   └── export_static.py               # 静态站点生成脚本
├── tests/                             # 单元测试与集成测试
│   ├── test_models.py                 # 模型层测试用例
│   ├── test_services.py               # 服务层测试用例
│   └── test_api.py                    # API 接口测试用例
├── data/                              # 数据存储目录
│   ├── doclink.db                     # SQLite 数据库文件
│   └── exports/                       # 导出的静态文件输出目录
├── docs/                              # 项目文档
│   ├── quickstart.md                  # 快速入门指南
│   ├── usage.md                       # 详细使用手册
│   └── api.md                         # API 接口文档
├── requirements.txt                   # Python 依赖清单
├── app.py                             # 应用入口文件
├── wsgi.py                            # WSGI 生产环境入口
└── README.md                          # 项目说明文件（本文件）
```

## 贡献指南

我们欢迎并鼓励社区贡献。请遵循以下流程以确保贡献的规范性与一致性。

1. 查阅问题列表与讨论区：在提交代码之前，请先查阅 GitHub Issues 与 Discussions，确认当前是否存在相关议题或已有解决方案，避免重复工作。

2. Fork 仓库并创建功能分支：从主仓库 Fork 个人副本，并基于 main 分支创建新的功能分支，分支命名建议采用 feature/功能简述 或 fix/问题简述 格式。

3. 编写或更新测试用例：针对新增功能或修复的问题，在 tests 目录下补充对应的单元测试或集成测试，确保代码覆盖率不低于现有水平。

4. 提交代码并签署开发者原产地证书：提交 Pull Request 前，请确保所有提交均已签署 DCO（Developer Certificate of Origin），并在 PR 描述中清晰说明变更内容、动机及测试结果。

5. 等待代码审查与合并：项目维护者将在 3 个工作日内进行审查，可能提出修改意见。通过审查后，代码将被合并至 main 分支，并随下一版本发布。

## 常见问题

问题：链接状态检查任务执行超时，大量链接被标记为异常。

解答：默认检查超时时间为 5 秒，批量检查并发数为 10。若目标站点响应较慢，可在 config/default.py 中调整 CHECK_TIMEOUT 和 CHECK_CONCURRENCY 参数。建议将超时增加至 15 秒，并发数降低至 5 后再试。

问题：导入包含 250 个链接的批次时，部分链接未能正确解析元信息。

解答：导入服务依赖 beautifulsoup4 解析目标页面的标题与 meta 标签。若目标页面为纯二进制文档（如直接返回 .doc 文件），则无法提取元信息。此时系统会自动使用文件名作为标题，并在日志中记录警告。该行为不影响链接本身的可达性检查与访问。

问题：静态导出生成的 HTML 页面样式与预览不一致。

解答：静态导出功能默认使用内置的极简模板，不包含完整前端资源。若需要与预览界面一致，请在导出时指定 --include-assets 参数，将静态资源一并打包。同时确保网络环境下可加载 CDN 样式库。

## 许可证

MIT License

Copyright (c) 2026 DocLink Hub Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

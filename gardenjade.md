# LinkVault 文档资源聚合系统

LinkVault 是一个面向技术文档与科研资料外链的轻量级聚合与导航系统，专注于对散落在多个内容源（尤其是移动端适配站点）中的 Word 文档资源进行统一采集、分类、索引与检索。该项目定位为技术团队内部知识库或特定垂直领域（如移动开发、产品设计、技术规范）的外部文档入口，帮助用户避免在数十个域名间反复切换，显著降低文档查找时间。

目标用户包括技术文档工程师、产品经理、运维人员以及需要频繁查阅产品说明书、接口定义文档、操作手册的研发群体。LinkVault 不存储文档实体，仅维护外链元数据与健康状态，通过定期探活与标签系统确保资源的可访问性与可发现性。

## 功能概览

批量导入与自动解析 系统支持从 TSV 或 JSON 文件中批量导入文档外链，自动解析 URL 中的域名、路径与文档编号，并提取文件扩展名及大小信息作为基础元数据。

多维度标签分类 用户可为每条链接添加自定义标签（如“技术规范”、“接口文档”、“操作手册”），并支持按标签、域名、文档类型进行快速筛选与分组统计。

链接健康度监控 内置异步探活任务，定期检测每个文档链接的可访问性（HTTP 状态码、响应时间），在管理面板中标注异常链接并生成告警报告。

全文检索与模糊匹配 基于文档标题、来源域名、标签与备注信息构建倒排索引，支持中文分词与拼音首字母模糊搜索，便于在大量链接中快速定位。

层级目录导航 根据文档来源域名自动生成一级导航目录，支持用户手动将链接归类至自定义二级目录，形成树形结构。

一键复制与批量导出 支持将选中的文档链接以纯文本或 Markdown 列表形式一键复制到剪贴板，也支持按筛选结果批量导出外链清单为 CSV 文件。

用户认证与权限管理 内置基于角色的访问控制（RBAC），管理员、编辑者与访客三种角色各自拥有不同的导入、编辑、删除与查看权限，适合团队协作场景。

## 应用场景

技术文档部门集中管理产品说明书 技术写作团队可将分散在不同移动端站点上的产品操作手册、FAQ 文档、版本更新日志通过 LinkVault 统一收录，并标注适用产品线、文档版本与审核状态，方便测试与运维团队按需取用。

研发团队维护接口定义与协议文档 在微服务架构下，各模块的接口定义文档（如 Swagger 导出文档、API 变更记录）常常存放在多个临时域名下。LinkVault 允许研发负责人将这批外链按服务名称打标，结合健康度监控及时发现失效链接并通知责任人更新。

运维人员整理故障处理与应急预案文档 运维中心积累了大量历史故障复盘报告与应急预案 Word 文档，存放于不同内部站点。LinkVault 可快速导入这批链接，按故障类型、系统模块、严重程度进行分类，形成可检索的应急知识库，缩短故障响应时间。

产品经理收集市场调研与竞品分析资料 产品团队在调研期间会产出大量竞品对比报告、用户访谈纪要等文档。LinkVault 帮助产品经理将外链按调研项目、时间周期、目标市场分组，避免资料散落在个人收藏夹或邮件附件中。

## 快速开始

以下步骤适用于 Linux / macOS / Windows WSL 环境，克隆仓库并启动本地开发服务器。

```bash
git clone https://github.com/linkvault/linkvault-core.git
cd linkvault-core

# 安装依赖（使用 Python 3.9+ 与 pip）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化 SQLite 数据库并创建默认管理员账户
python manage.py migrate
python manage.py createsuperuser

# 运行开发服务器
python manage.py runserver 0.0.0.0:8000
```

访问 http://localhost:8000 使用管理员账户登录，即可进入管理面板开始导入文档链接。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，推荐使用 3.11 |
| Django | 4.2 LTS | Web 框架，用于提供管理界面与 REST API |
| SQLite | 3.35 及以上 | 默认轻量级数据库，生产环境可切换至 PostgreSQL |
| Redis | 6.2 及以上 | 用于缓存与异步任务队列（Celery 后端） |
| Celery | 5.3 及以上 | 分布式任务队列，执行链接健康度探活 |
| httpx | 0.25 及以上 | 异步 HTTP 客户端，用于检测文档链接状态 |
| whoosh | 2.7 及以上 | 全文检索引擎，支持中文分词 |
| django-cors-headers | 4.3 及以上 | 处理前端跨域请求，便于分离部署 |
| pytest | 7.4 及以上 | 单元测试与集成测试框架 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/ | 如何导入链接、打标签、创建目录、搜索与导出数据 |
| 管理员指南 | /docs/admin-guide/ | 如何配置探活频率、管理用户权限、备份数据库与切换生产环境 |
| 开发者文档 | /docs/developer-guide/ | API 接口规范、自定义标签插件开发、Celery 任务扩展方法 |
| 部署运维 | /docs/deployment/ | 使用 Docker Compose 或 Kubernetes 部署生产集群的详细配置模板 |
| 常见问题 | /docs/faq/ | 链接探活失败原因排查、数据库迁移问题、性能调优策略 |

## 资源列表

- h5.mobile.nwbbyt.cn/Article/4795.doc
- h5.mobile.nzfnve.cn/Article/705708.doc
- h5.mobile.fuvxie.cn/Article/5394.doc
- h5.mobile.cvsifc.cn/Article/4476.doc
- h5.mobile.jnjpgf.cn/Article/944230.doc
- h5.mobile.cvsifc.cn/Article/5144951.doc
- h5.mobile.hcbezg.cn/Article/488093.doc
- h5.mobile.cmcvrr.cn/Article/3408.doc
- h5.mobile.cmcvrr.cn/Article/6143452.doc
- h5.mobile.nzfnve.cn/Article/3677.doc
- h5.mobile.puhvjy.cn/Article/627395.doc
- h5.mobile.hcbezg.cn/Article/8605.doc
- h5.mobile.fuvxie.cn/Article/11757.doc
- h5.mobile.nwbbyt.cn/Article/8001090.doc
- h5.mobile.cvsifc.cn/Article/713863.doc
- h5.mobile.cvsifc.cn/Article/15496.doc
- h5.mobile.puhvjy.cn/Article/91135.doc
- h5.mobile.hcbezg.cn/Article/78602.doc
- h5.mobile.nwbbyt.cn/Article/2380.doc
- h5.mobile.cmcvrr.cn/Article/2540.doc
- h5.mobile.puhvjy.cn/Article/36365.doc
- h5.mobile.puhvjy.cn/Article/399312.doc
- h5.mobile.cvsifc.cn/Article/983904.doc
- h5.mobile.cmcvrr.cn/Article/491006.doc
- h5.mobile.hcbezg.cn/Article/034381.doc
- h5.mobile.jnjpgf.cn/Article/10438.doc
- h5.mobile.nwbbyt.cn/Article/1967816.doc
- h5.mobile.fuvxie.cn/Article/4819057.doc
- h5.mobile.cmcvrr.cn/Article/609771.doc
- h5.mobile.hcbezg.cn/Article/30391.doc
- h5.mobile.nzfnve.cn/Article/3166522.doc
- h5.mobile.cmcvrr.cn/Article/3104170.doc
- h5.mobile.cmcvrr.cn/Article/979783.doc
- h5.mobile.cvsifc.cn/Article/69399.doc
- h5.mobile.hcbezg.cn/Article/54761.doc
- h5.mobile.cmcvrr.cn/Article/8255757.doc
- h5.mobile.nwbbyt.cn/Article/005277.doc
- h5.mobile.jnjpgf.cn/Article/960557.doc
- h5.mobile.nzfnve.cn/Article/24561.doc
- h5.mobile.fuvxie.cn/Article/6662931.doc
- h5.mobile.puhvjy.cn/Article/05228.doc
- h5.mobile.cmcvrr.cn/Article/1405018.doc
- h5.mobile.cvsifc.cn/Article/89833.doc
- h5.mobile.cvsifc.cn/Article/029006.doc
- h5.mobile.jnjpgf.cn/Article/9617.doc
- h5.mobile.cmcvrr.cn/Article/2935.doc
- h5.mobile.cvsifc.cn/Article/8318634.doc
- h5.mobile.cvsifc.cn/Article/55946.doc
- h5.mobile.nwbbyt.cn/Article/0076.doc
- h5.mobile.puhvjy.cn/Article/0242.doc
- h5.mobile.hcbezg.cn/Article/1274171.doc
- h5.mobile.puhvjy.cn/Article/578673.doc
- h5.mobile.cmcvrr.cn/Article/99895.doc
- h5.mobile.nwbbyt.cn/Article/8761.doc
- h5.mobile.nwbbyt.cn/Article/84900.doc
- h5.mobile.cmcvrr.cn/Article/8061375.doc
- h5.mobile.nwbbyt.cn/Article/9672131.doc
- h5.mobile.nwbbyt.cn/Article/41990.doc
- h5.mobile.nwbbyt.cn/Article/8894.doc
- h5.mobile.nzfnve.cn/Article/2576572.doc
- h5.mobile.cvsifc.cn/Article/4464.doc
- h5.mobile.puhvjy.cn/Article/984948.doc
- h5.mobile.puhvjy.cn/Article/5995862.doc
- h5.mobile.cmcvrr.cn/Article/380668.doc
- h5.mobile.puhvjy.cn/Article/608218.doc
- h5.mobile.fuvxie.cn/Article/8214253.doc
- h5.mobile.nwbbyt.cn/Article/364585.doc
- h5.mobile.fuvxie.cn/Article/070971.doc
- h5.mobile.cvsifc.cn/Article/4668158.doc
- h5.mobile.fuvxie.cn/Article/3587.doc
- h5.mobile.puhvjy.cn/Article/1481.doc
- h5.mobile.nwbbyt.cn/Article/704272.doc
- h5.mobile.hcbezg.cn/Article/227796.doc
- h5.mobile.jnjpgf.cn/Article/31731.doc
- h5.mobile.puhvjy.cn/Article/637914.doc
- h5.mobile.jnjpgf.cn/Article/011757.doc
- h5.mobile.cvsifc.cn/Article/966211.doc
- h5.mobile.cvsifc.cn/Article/8960.doc
- h5.mobile.cvsifc.cn/Article/7279063.doc
- h5.mobile.nwbbyt.cn/Article/11570.doc
- h5.mobile.jnjpgf.cn/Article/7787865.doc
- h5.mobile.nzfnve.cn/Article/9686.doc
- h5.mobile.nzfnve.cn/Article/0049.doc
- h5.mobile.jnjpgf.cn/Article/8221847.doc
- h5.mobile.cmcvrr.cn/Article/8881.doc
- h5.mobile.puhvjy.cn/Article/095368.doc
- h5.mobile.fuvxie.cn/Article/7429.doc
- h5.mobile.puhvjy.cn/Article/4492246.doc
- h5.mobile.nzfnve.cn/Article/241521.doc
- h5.mobile.fuvxie.cn/Article/7064297.doc
- h5.mobile.nzfnve.cn/Article/695836.doc
- h5.mobile.cvsifc.cn/Article/0374.doc
- h5.mobile.cvsifc.cn/Article/4543.doc
- h5.mobile.nwbbyt.cn/Article/791289.doc
- h5.mobile.hcbezg.cn/Article/4455.doc
- h5.mobile.fuvxie.cn/Article/4592.doc
- h5.mobile.nzfnve.cn/Article/444935.doc
- h5.mobile.puhvjy.cn/Article/0355287.doc
- h5.mobile.cmcvrr.cn/Article/5821720.doc
- h5.mobile.jnjpgf.cn/Article/22246.doc
- h5.mobile.jnjpgf.cn/Article/9102724.doc
- h5.mobile.fuvxie.cn/Article/342059.doc
- h5.mobile.puhvjy.cn/Article/630056.doc
- h5.mobile.nwbbyt.cn/Article/8682.doc
- h5.mobile.puhvjy.cn/Article/6073858.doc
- h5.mobile.nwbbyt.cn/Article/33510.doc
- h5.mobile.nwbbyt.cn/Article/6990901.doc
- h5.mobile.nwbbyt.cn/Article/89720.doc
- h5.mobile.cvsifc.cn/Article/7635.doc
- h5.mobile.nzfnve.cn/Article/4421.doc
- h5.mobile.cvsifc.cn/Article/228213.doc
- h5.mobile.puhvjy.cn/Article/14830.doc
- h5.mobile.cmcvrr.cn/Article/80325.doc
- h5.mobile.jnjpgf.cn/Article/3843191.doc
- h5.mobile.cmcvrr.cn/Article/5025.doc
- h5.mobile.puhvjy.cn/Article/8359.doc
- h5.mobile.cmcvrr.cn/Article/660185.doc
- h5.mobile.cvsifc.cn/Article/61048.doc
- h5.mobile.jnjpgf.cn/Article/27459.doc
- h5.mobile.jnjpgf.cn/Article/9418100.doc
- h5.mobile.cvsifc.cn/Article/664304.doc
- h5.mobile.nwbbyt.cn/Article/809635.doc
- h5.mobile.nzfnve.cn/Article/5738963.doc
- h5.mobile.puhvjy.cn/Article/414117.doc
- h5.mobile.cmcvrr.cn/Article/0246541.doc
- h5.mobile.nzfnve.cn/Article/1442.doc
- h5.mobile.nzfnve.cn/Article/089573.doc
- h5.mobile.cmcvrr.cn/Article/2059.doc
- h5.mobile.hcbezg.cn/Article/21427.doc
- h5.mobile.puhvjy.cn/Article/412150.doc
- h5.mobile.jnjpgf.cn/Article/7751822.doc
- h5.mobile.cmcvrr.cn/Article/7389.doc
- h5.mobile.nwbbyt.cn/Article/879416.doc
- h5.mobile.puhvjy.cn/Article/787696.doc
- h5.mobile.fuvxie.cn/Article/392870.doc
- h5.mobile.nzfnve.cn/Article/03269.doc
- h5.mobile.nzfnve.cn/Article/9958669.doc
- h5.mobile.puhvjy.cn/Article/3785004.doc
- h5.mobile.fuvxie.cn/Article/77534.doc
- h5.mobile.cmcvrr.cn/Article/5890838.doc
- h5.mobile.puhvjy.cn/Article/2526284.doc
- h5.mobile.hcbezg.cn/Article/34671.doc
- h5.mobile.hcbezg.cn/Article/4807.doc
- h5.mobile.hcbezg.cn/Article/3754173.doc
- h5.mobile.cmcvrr.cn/Article/5593.doc
- h5.mobile.jnjpgf.cn/Article/7092.doc
- h5.mobile.cmcvrr.cn/Article/224287.doc
- h5.mobile.cvsifc.cn/Article/801788.doc
- h5.mobile.jnjpgf.cn/Article/51401.doc
- h5.mobile.nzfnve.cn/Article/734738.doc
- h5.mobile.nzfnve.cn/Article/66528.doc
- h5.mobile.jnjpgf.cn/Article/8823541.doc
- h5.mobile.jnjpgf.cn/Article/2231963.doc
- h5.mobile.cmcvrr.cn/Article/056878.doc
- h5.mobile.nwbbyt.cn/Article/407899.doc
- h5.mobile.fuvxie.cn/Article/8011139.doc
- h5.mobile.jnjpgf.cn/Article/095623.doc
- h5.mobile.puhvjy.cn/Article/549633.doc
- h5.mobile.nwbbyt.cn/Article/8608.doc
- h5.mobile.puhvjy.cn/Article/610344.doc
- h5.mobile.fuvxie.cn/Article/27577.doc
- h5.mobile.cvsifc.cn/Article/64701.doc
- h5.mobile.puhvjy.cn/Article/595551.doc
- h5.mobile.hcbezg.cn/Article/0797601.doc
- h5.mobile.nwbbyt.cn/Article/1301.doc
- h5.mobile.cvsifc.cn/Article/928082.doc
- h5.mobile.fuvxie.cn/Article/0606.doc
- h5.mobile.hcbezg.cn/Article/8460796.doc
- h5.mobile.puhvjy.cn/Article/761000.doc
- h5.mobile.nzfnve.cn/Article/4092.doc
- h5.mobile.puhvjy.cn/Article/85667.doc
- h5.mobile.cmcvrr.cn/Article/1600.doc
- h5.mobile.fuvxie.cn/Article/103620.doc
- h5.mobile.puhvjy.cn/Article/838977.doc
- h5.mobile.nwbbyt.cn/Article/98737.doc
- h5.mobile.fuvxie.cn/Article/27029.doc
- h5.mobile.cvsifc.cn/Article/0290.doc
- h5.mobile.puhvjy.cn/Article/665921.doc
- h5.mobile.cvsifc.cn/Article/751718.doc
- h5.mobile.nwbbyt.cn/Article/64994.doc
- h5.mobile.cvsifc.cn/Article/0537.doc
- h5.mobile.puhvjy.cn/Article/0371998.doc
- h5.mobile.fuvxie.cn/Article/99990.doc
- h5.mobile.nwbbyt.cn/Article/03932.doc
- h5.mobile.hcbezg.cn/Article/2748349.doc
- h5.mobile.nwbbyt.cn/Article/8050201.doc
- h5.mobile.nzfnve.cn/Article/71395.doc
- h5.mobile.cmcvrr.cn/Article/86898.doc
- h5.mobile.cvsifc.cn/Article/7048.doc
- h5.mobile.cvsifc.cn/Article/735220.doc
- h5.mobile.hcbezg.cn/Article/63713.doc
- h5.mobile.nwbbyt.cn/Article/45749.doc
- h5.mobile.fuvxie.cn/Article/257941.doc
- h5.mobile.fuvxie.cn/Article/3799.doc
- h5.mobile.jnjpgf.cn/Article/7251634.doc
- h5.mobile.nwbbyt.cn/Article/9680904.doc
- h5.mobile.cvsifc.cn/Article/74015.doc
- h5.mobile.jnjpgf.cn/Article/6299.doc
- h5.mobile.nzfnve.cn/Article/69173.doc
- h5.mobile.nzfnve.cn/Article/46162.doc
- h5.mobile.jnjpgf.cn/Article/0121642.doc
- h5.mobile.nzfnve.cn/Article/0417462.doc
- h5.mobile.puhvjy.cn/Article/2190.doc
- h5.mobile.jnjpgf.cn/Article/1783010.doc
- h5.mobile.hcbezg.cn/Article/648588.doc
- h5.mobile.hcbezg.cn/Article/991997.doc
- h5.mobile.jnjpgf.cn/Article/055697.doc
- h5.mobile.fuvxie.cn/Article/52913.doc
- h5.mobile.cmcvrr.cn/Article/307610.doc
- h5.mobile.cmcvrr.cn/Article/8469.doc
- h5.mobile.jnjpgf.cn/Article/25519.doc
- h5.mobile.cvsifc.cn/Article/079505.doc
- h5.mobile.nzfnve.cn/Article/126402.doc
- h5.mobile.nzfnve.cn/Article/0266.doc
- h5.mobile.fuvxie.cn/Article/3697.doc
- h5.mobile.puhvjy.cn/Article/0732.doc
- h5.mobile.puhvjy.cn/Article/932377.doc
- h5.mobile.puhvjy.cn/Article/9276204.doc
- h5.mobile.cvsifc.cn/Article/0818440.doc
- h5.mobile.nwbbyt.cn/Article/13866.doc
- h5.mobile.cmcvrr.cn/Article/902886.doc
- h5.mobile.cvsifc.cn/Article/694829.doc
- h5.mobile.hcbezg.cn/Article/0748.doc
- h5.mobile.hcbezg.cn/Article/69066.doc
- h5.mobile.fuvxie.cn/Article/271691.doc
- h5.mobile.cvsifc.cn/Article/08849.doc
- h5.mobile.fuvxie.cn/Article/0717.doc
- h5.mobile.jnjpgf.cn/Article/579205.doc
- h5.mobile.fuvxie.cn/Article/22649.doc
- h5.mobile.nzfnve.cn/Article/682663.doc
- h5.mobile.jnjpgf.cn/Article/3246.doc
- h5.mobile.hcbezg.cn/Article/66131.doc
- h5.mobile.nwbbyt.cn/Article/87834.doc
- h5.mobile.nzfnve.cn/Article/43134.doc
- h5.mobile.hcbezg.cn/Article/3785964.doc
- h5.mobile.cvsifc.cn/Article/835516.doc
- h5.mobile.fuvxie.cn/Article/49384.doc
- h5.mobile.nzfnve.cn/Article/4198032.doc
- h5.mobile.puhvjy.cn/Article/8607437.doc
- h5.mobile.hcbezg.cn/Article/9572288.doc
- h5.mobile.cmcvrr.cn/Article/41094.doc
- h5.mobile.hcbezg.cn/Article/78896.doc
- h5.mobile.nzfnve.cn/Article/629992.doc
- h5.mobile.puhvjy.cn/Article/18520.doc
- h5.mobile.cmcvrr.cn/Article/71518.doc
- h5.mobile.hcbezg.cn/Article/15316.doc
- h5.mobile.cvsifc.cn/Article/959311.doc
- h5.mobile.puhvjy.cn/Article/1713.doc
- h5.mobile.puhvjy.cn/Article/897112.doc
- h5.mobile.nwbbyt.cn/Article/5601.doc

## 项目结构

```
linkvault-core/
├── manage.py                         # Django 项目管理入口
├── requirements.txt                  # 生产环境依赖清单
├── requirements-dev.txt              # 开发与测试额外依赖
├── docker-compose.yml                # 本地开发容器编排（含 Redis + PostgreSQL）
├── .env.example                      # 环境变量模板（SECRET_KEY, DB_URL, REDIS_URL）
├── linkvault/                        # 项目主配置模块
│   ├── settings/
│   │   ├── base.py                   # 基础配置（所有环境共用）
│   │   ├── development.py            # 开发环境配置（开启调试与 SQLite）
│   │   └── production.py             # 生产环境配置（PostgreSQL + 静态文件托管）
│   ├── urls.py                       # 根路由（API + 管理后台）
│   ├── asgi.py                       # ASGI 入口（用于 WebSocket 或异步视图）
│   └── celery.py                     # Celery 应用实例与定时任务调度
├── apps/
│   ├── links/                        # 链接管理核心应用
│   │   ├── models.py                 # Link, Tag, Category, HealthCheck 模型
│   │   ├── admin.py                  # Django Admin 自定义展示与筛选
│   │   ├── views.py                  # 链接导入、列表、搜索、导出等视图
│   │   ├── serializers.py            # DRF 序列化器（用于 REST API）
│   │   ├── tasks.py                  # Celery 任务（健康探活、批量导入）
│   │   ├── indexer.py                # Whoosh 索引构建与查询封装
│   │   └── utils.py                  # URL 解析、文档类型识别、去重工具
│   ├── accounts/                     # 用户认证与权限管理
│   │   ├── models.py                 # 扩展用户模型（角色、部门）
│   │   ├── permissions.py            # 自定义权限类（IsAdmin, IsEditor, IsViewer）
│   │   └── backends.py               # 支持邮箱/用户名双字段登录
│   ├── monitoring/                   # 系统监控与日志
│   │   ├── middleware.py             # 请求响应时间记录
│   │   ├── health.py                 # 系统健康检查端点（数据库、Redis、磁盘）
│   │   └── logger.py                 # 结构化日志配置（JSON 格式）
│   └── frontend/                     # 前后端分离架构中的静态资源
│       ├── templates/                # Django 模板（管理后台基础页）
│       ├── static/                   # 编译后的 CSS/JS 资源（Vue 或 React 构建产物）
│       └── webpack.config.js         # 前端资源打包配置
├── tests/
│   ├── unit/                         # 单元测试（模型方法、工具函数）
│   ├── integration/                  # 集成测试（API 端点、Celery 任务）
│   └── fixtures/                     # 测试数据（样本链接列表与标签）
├── scripts/
│   ├── import_batch.py               # 批量导入命令行工具
│   ├── export_csv.py                 # 导出为 CSV 格式脚本
│   └── health_check_runner.py        # 手动触发全量探活脚本
└── docs/                             # 文档源码（Sphinx / MkDocs 工程）
    ├── source/
    │   ├── user-guide.rst
    │   ├── admin-guide.rst
    │   └── api-reference.rst
    └── build/                        # 生成的 HTML 文档输出目录
```

## 贡献指南

提交 Issue 报告缺陷或功能请求 在 GitHub Issues 页面选择对应模板填写，缺陷报告需包含系统环境、复现步骤与日志片段，功能请求需阐明使用场景与预期收益。

Fork 仓库并创建功能分支 从主分支 main 或 develop 切出新分支，命名遵循 feature/xxx 或 fix/xxx 格式，确保分支与上游仓库保持同步。

编写或更新单元测试 所有新增功能或修复必须附带相应的单元测试或集成测试，测试覆盖率不低于 80%，使用 pytest 执行测试套件。

提交 Pull Request 并关联 Issue PR 标题使用约定式提交格式（如 feat: 或 fix:），描述中说明变更内容、测试结果与破坏性变化，等待至少一名维护者审核。

遵守代码风格规范 Python 代码使用 Black 格式化，导入语句按 isort 规则排序，前端代码遵循 ESLint 与 Prettier 配置。

## 常见问题

Q: 链接健康度检测显示为不可达，但实际在浏览器中可以访问，是什么原因？

A: 此情况通常由以下原因造成：目标站点对非浏览器 User-Agent 返回 403 或 429 状态码；站点要求携带特定的 Cookie 或 Referer 头；内网链接在外部探活环境中无法解析。解决方案为：在管理后台的探活配置中，为特定域名设置自定义请求头（如 User-Agent 模拟移动端浏览器），或将该域名加入跳过检测白名单。对于内网链接，建议部署探活 worker 至内网环境。

Q: 如何从旧版本的 SQLite 迁移至生产环境的 PostgreSQL 而不丢失数据？

A: 使用 Django 自带的 dumpdata 与 loaddata 命令进行序列化迁移。首先在 SQLite 环境下运行 python manage.py dumpdata --exclude auth.permission --exclude contenttypes > data.json，然后切换至 PostgreSQL 配置并执行 python manage.py migrate，最后运行 python manage.py loaddata data.json。注意用户密码哈希值会被完整保留，无需重新设置。建议在迁移前进行完整数据库备份。

Q: 搜索功能对中文文档标题的支持效果不理想，如何优化？

A: 默认的 Whoosh 分析器使用标准分词器，对中文支持较弱。可以通过在 indexer.py 中替换为 jieba.analyse 提供的 ChineseAnalyzer，并在搜索时启用拼音转换插件。优化后需重建索引（执行 python manage.py rebuild_index）。另外，搜索时建议使用双引号包裹精确短语，或使用空格分隔多个关键词进行交集检索。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

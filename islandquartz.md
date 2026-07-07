# LinkSphere 技术资源聚合站

LinkSphere 是一个面向开发者与技术研究人员的结构化外链资源聚合平台。项目定位为高质量技术文章、工程文档与深度教程的导航中枢，通过分类索引与轻量级元数据管理，帮助用户在碎片化信息环境中快速定位有效内容。目标用户包括软件工程师、架构师、技术管理者以及计算机科学相关领域的学生。

本项目不生产内容，而是基于人工筛选与社区贡献，构建可维护的外部资源引用体系。每个资源条目均包含来源域名、文章标识符与原始发布信息，确保引用可追溯。LinkSphere 适用于构建个人知识库、团队技术周报素材池或开源项目文档的外部参考附录。

## 功能概览

资源条目结构化存储 每条记录包含文章标识符、来源域名及基础分类标签，支持按域名与文章 ID 进行精确检索。

多维度筛选与排序 支持按来源域名、发布时间（基于文章标识符推断）及内容类型进行过滤，提供倒序与正序排列选项。

批量导入与导出 提供 CSV 与 JSON 格式的批量资源导入接口，支持导出为 Markdown 表格或结构化 YAML 前置数据。

域名聚合视图 自动统计各来源域名的资源数量，生成简明的站点贡献排行，辅助识别高价值信息源。

元数据扩展字段 预留 tag、level、summary 三个扩展字段，允许用户为每条资源补充技术标签、阅读难度等级及一句话摘要。

只读只写分离架构 后端采用读写分离设计，查询操作走只读副本，写入操作走主库，确保高并发场景下的稳定性。

健康检查与监控 提供 /health 与 /metrics 端点，集成 Prometheus 指标采集，便于运维团队接入现有监控体系。

## 应用场景

技术团队内部周报素材收集 团队技术负责人每周汇总行业动态与工程经验文章。LinkSphere 的资源列表可作为素材池，成员按域名筛选后快速浏览近期收录的文章标识符，定位感兴趣的主题，减少重复搜索时间。

开源项目文档的外部参考附录 开源项目在 README 或 Wiki 中引用外部技术方案时，需要维护一份稳定的外链清单。LinkSphere 允许项目维护者将引用链接统一录入平台，通过导出功能生成 Markdown 格式的参考列表，直接粘贴至项目文档中。

个人知识库的原始信息源管理 研究员或高级开发者在阅读大量技术博客后，使用 LinkSphere 记录有价值的文章标识符与来源域名。后续结合本地笔记工具（如 Obsidian 或 Logseq）通过 CSV 导出进行二次整理，形成长期可检索的个人知识索引。

技术社区资源共建 技术社区或开源社区可基于 LinkSphere 搭建公共资源导航页。社区成员通过提交条目贡献链接，维护者审核后合并，最终生成一份多域名、多主题的社区推荐阅读清单。

自动化爬虫的种子链接供给 数据采集项目需要初始 URL 列表作为爬虫入口。LinkSphere 提供按域名批量获取文章标识符的 API，可快速生成符合特定域名模式的种子链接集合，供爬虫调度器使用。

## 快速开始

以下步骤适用于 Linux / macOS / Windows WSL 环境。

```bash
# 克隆代码仓库
git clone https://github.com/linksphere/linksphere-core.git
cd linksphere-core

# 安装依赖（使用 Python 3.10+ 与 pip）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化本地 SQLite 数据库（开发环境）
python scripts/init_db.py --env development

# 启动开发服务器
python app.py --port 8080 --workers 2
```

访问 http://localhost:8080 查看服务状态。生产环境部署请参考 `deploy/` 目录下的 Dockerfile 与 docker-compose.yml。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 或更高 | 核心运行环境，类型提示依赖 3.10+ 特性 |
| SQLite | 3.35.0 或更高 | 开发环境默认数据库，生产环境建议切换至 PostgreSQL |
| Redis | 6.2.0 或更高 | 会话缓存与速率限制存储，可选但强烈推荐 |
| PostgreSQL | 13.0 或更高 | 生产环境主数据库，支持并发写入与事务隔离 |
| Prometheus | 2.30.0 或更高 | 指标采集系统，用于 /metrics 端点集成 |
| Node.js | 18.0.0 或更高 | 仅用于前端静态资源构建，后端运行不依赖 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/ | 如何使用资源检索、筛选与导出功能，面向内容消费者 |
| 管理员指南 | /docs/admin-guide/ | 如何管理资源条目、审核贡献、执行批量导入导出操作 |
| API 参考 | /docs/api-reference/ | 如何通过 RESTful API 查询资源列表、获取单个条目及统计信息 |
| 开发指引 | /docs/development/ | 如何搭建开发环境、运行测试、提交代码变更与构建发布版本 |
| 部署运维 | /docs/deployment/ | 如何在不同云平台或物理服务器上部署 LinkSphere 服务实例 |

## 资源列表

- https://www.read.puhvjy.cn/Article/8340.shtml
- https://www.read.nzfnve.cn/Article/7057309.shtml
- https://www.read.fuvxie.cn/Article/06350.shtml
- https://www.read.nwbbyt.cn/Article/5427283.shtml
- https://www.read.nzfnve.cn/Article/7459570.shtml
- https://www.read.fuvxie.cn/Article/7045.shtml
- https://www.read.nwbbyt.cn/Article/808355.shtml
- https://www.read.puhvjy.cn/Article/35744.shtml
- https://www.read.hcbezg.cn/Article/1158.shtml
- https://www.read.hcbezg.cn/Article/1564188.shtml
- https://www.read.hcbezg.cn/Article/95624.shtml
- https://www.read.cmcvrr.cn/Article/091750.shtml
- https://www.read.hcbezg.cn/Article/737131.shtml
- https://www.read.jnjpgf.cn/Article/6987418.shtml
- https://www.read.hcbezg.cn/Article/8645.shtml
- https://www.read.jnjpgf.cn/Article/6164.shtml
- https://www.read.nzfnve.cn/Article/70793.shtml
- https://www.read.nzfnve.cn/Article/8396.shtml
- https://www.read.nzfnve.cn/Article/047375.shtml
- https://www.read.cmcvrr.cn/Article/89467.shtml
- https://www.read.cmcvrr.cn/Article/1207248.shtml
- https://www.read.fuvxie.cn/Article/474832.shtml
- https://www.read.jnjpgf.cn/Article/7742393.shtml
- https://www.read.cmcvrr.cn/Article/81318.shtml
- https://www.read.hcbezg.cn/Article/06286.shtml
- https://www.read.puhvjy.cn/Article/6049567.shtml
- https://www.read.nzfnve.cn/Article/8366175.shtml
- https://www.read.nwbbyt.cn/Article/3560.shtml
- https://www.read.fuvxie.cn/Article/6237324.shtml
- https://www.read.hcbezg.cn/Article/8065863.shtml
- https://www.read.fuvxie.cn/Article/868263.shtml
- https://www.read.cmcvrr.cn/Article/573716.shtml
- https://www.read.puhvjy.cn/Article/142240.shtml
- https://www.read.cvsifc.cn/Article/0659869.shtml
- https://www.read.cmcvrr.cn/Article/53938.shtml
- https://www.read.puhvjy.cn/Article/78315.shtml
- https://www.read.fuvxie.cn/Article/0497.shtml
- https://www.read.hcbezg.cn/Article/6869.shtml
- https://www.read.fuvxie.cn/Article/1120414.shtml
- https://www.read.cvsifc.cn/Article/1098629.shtml
- https://www.read.cmcvrr.cn/Article/9767.shtml
- https://www.read.hcbezg.cn/Article/23787.shtml
- https://www.read.nwbbyt.cn/Article/360312.shtml
- https://www.read.jnjpgf.cn/Article/10487.shtml
- https://www.read.hcbezg.cn/Article/9373320.shtml
- https://www.read.puhvjy.cn/Article/537110.shtml
- https://www.read.jnjpgf.cn/Article/6873.shtml
- https://www.read.puhvjy.cn/Article/79274.shtml
- https://www.read.cvsifc.cn/Article/044626.shtml
- https://www.read.nzfnve.cn/Article/9470.shtml
- https://www.read.puhvjy.cn/Article/176143.shtml
- https://www.read.nwbbyt.cn/Article/809595.shtml
- https://www.read.nzfnve.cn/Article/7199.shtml
- https://www.read.nzfnve.cn/Article/8851762.shtml
- https://www.read.hcbezg.cn/Article/2020.shtml
- https://www.read.cmcvrr.cn/Article/1779.shtml
- https://www.read.nwbbyt.cn/Article/6703337.shtml
- https://www.read.nzfnve.cn/Article/65440.shtml
- https://www.read.hcbezg.cn/Article/221358.shtml
- https://www.read.cmcvrr.cn/Article/8411.shtml
- https://www.read.nzfnve.cn/Article/3777.shtml
- https://www.read.puhvjy.cn/Article/0201.shtml
- https://www.read.nwbbyt.cn/Article/3519886.shtml
- https://www.read.cvsifc.cn/Article/6848075.shtml
- https://www.read.cmcvrr.cn/Article/70850.shtml
- https://www.read.jnjpgf.cn/Article/357922.shtml
- https://www.read.nzfnve.cn/Article/4652783.shtml
- https://www.read.cmcvrr.cn/Article/767383.shtml
- https://www.read.nzfnve.cn/Article/41301.shtml
- https://www.read.fuvxie.cn/Article/0616.shtml
- https://www.read.nwbbyt.cn/Article/113802.shtml
- https://www.read.hcbezg.cn/Article/35303.shtml
- https://www.read.puhvjy.cn/Article/5285160.shtml
- https://www.read.jnjpgf.cn/Article/82348.shtml
- https://www.read.nzfnve.cn/Article/751578.shtml
- https://www.read.hcbezg.cn/Article/5381.shtml
- https://www.read.nzfnve.cn/Article/936868.shtml
- https://www.read.fuvxie.cn/Article/1897007.shtml
- https://www.read.cvsifc.cn/Article/582691.shtml
- https://www.read.fuvxie.cn/Article/6676.shtml
- https://www.read.puhvjy.cn/Article/2449321.shtml
- https://www.read.fuvxie.cn/Article/6009106.shtml
- https://www.read.puhvjy.cn/Article/3143.shtml
- https://www.read.cvsifc.cn/Article/47590.shtml
- https://www.read.puhvjy.cn/Article/4440.shtml
- https://www.read.puhvjy.cn/Article/7819710.shtml
- https://www.read.nzfnve.cn/Article/49197.shtml
- https://www.read.jnjpgf.cn/Article/4919.shtml
- https://www.read.nzfnve.cn/Article/47600.shtml
- https://www.read.nzfnve.cn/Article/4981863.shtml
- https://www.read.cvsifc.cn/Article/65332.shtml
- https://www.read.hcbezg.cn/Article/58410.shtml
- https://www.read.nwbbyt.cn/Article/030840.shtml
- https://www.read.fuvxie.cn/Article/9285.shtml
- https://www.read.jnjpgf.cn/Article/609277.shtml
- https://www.read.fuvxie.cn/Article/48982.shtml
- https://www.read.jnjpgf.cn/Article/43288.shtml
- https://www.read.hcbezg.cn/Article/078917.shtml
- https://www.read.fuvxie.cn/Article/34625.shtml
- https://www.read.nwbbyt.cn/Article/20706.shtml
- https://www.read.cvsifc.cn/Article/51432.shtml
- https://www.read.fuvxie.cn/Article/2917060.shtml
- https://www.read.nwbbyt.cn/Article/8610.shtml
- https://www.read.cvsifc.cn/Article/496501.shtml
- https://www.read.nwbbyt.cn/Article/6124.shtml
- https://www.read.puhvjy.cn/Article/73208.shtml
- https://www.read.nzfnve.cn/Article/601083.shtml
- https://www.read.cvsifc.cn/Article/8232.shtml
- https://www.read.puhvjy.cn/Article/8865.shtml
- https://www.read.puhvjy.cn/Article/873425.shtml
- https://www.read.jnjpgf.cn/Article/2083.shtml
- https://www.read.nwbbyt.cn/Article/1774.shtml
- https://www.read.hcbezg.cn/Article/9933.shtml
- https://www.read.cmcvrr.cn/Article/0539564.shtml
- https://www.read.nzfnve.cn/Article/014499.shtml
- https://www.read.cmcvrr.cn/Article/76357.shtml
- https://www.read.jnjpgf.cn/Article/61492.shtml
- https://www.read.nzfnve.cn/Article/1160784.shtml
- https://www.read.fuvxie.cn/Article/440203.shtml
- https://www.read.hcbezg.cn/Article/610414.shtml
- https://www.read.nzfnve.cn/Article/436256.shtml
- https://www.read.fuvxie.cn/Article/7297757.shtml
- https://www.read.nwbbyt.cn/Article/4369.shtml
- https://www.read.cvsifc.cn/Article/03627.shtml
- https://www.read.nwbbyt.cn/Article/4370.shtml
- https://www.read.fuvxie.cn/Article/584976.shtml
- https://www.read.jnjpgf.cn/Article/6525502.shtml
- https://www.read.cmcvrr.cn/Article/49131.shtml
- https://www.read.cvsifc.cn/Article/6082520.shtml
- https://www.read.hcbezg.cn/Article/806296.shtml
- https://www.read.hcbezg.cn/Article/7249191.shtml
- https://www.read.fuvxie.cn/Article/7765.shtml
- https://www.read.puhvjy.cn/Article/8521270.shtml
- https://www.read.cvsifc.cn/Article/2149164.shtml
- https://www.read.nzfnve.cn/Article/4401120.shtml
- https://www.read.fuvxie.cn/Article/2021481.shtml
- https://www.read.puhvjy.cn/Article/43417.shtml
- https://www.read.cvsifc.cn/Article/489611.shtml
- https://www.read.cvsifc.cn/Article/8917.shtml
- https://www.read.jnjpgf.cn/Article/13458.shtml
- https://www.read.jnjpgf.cn/Article/2212.shtml
- https://www.read.cvsifc.cn/Article/97060.shtml
- https://www.read.cmcvrr.cn/Article/167685.shtml
- https://www.read.hcbezg.cn/Article/54645.shtml
- https://www.read.nwbbyt.cn/Article/216727.shtml
- https://www.read.jnjpgf.cn/Article/580623.shtml
- https://www.read.jnjpgf.cn/Article/61385.shtml
- https://www.read.puhvjy.cn/Article/6076067.shtml
- https://www.read.fuvxie.cn/Article/4021.shtml
- https://www.read.puhvjy.cn/Article/54228.shtml
- https://www.read.jnjpgf.cn/Article/7669.shtml
- https://www.read.cmcvrr.cn/Article/7884774.shtml
- https://www.read.cvsifc.cn/Article/80225.shtml
- https://www.read.puhvjy.cn/Article/9646.shtml
- https://www.read.cmcvrr.cn/Article/55161.shtml
- https://www.read.hcbezg.cn/Article/835400.shtml
- https://www.read.fuvxie.cn/Article/7616.shtml
- https://www.read.puhvjy.cn/Article/319652.shtml
- https://www.read.hcbezg.cn/Article/5262.shtml
- https://www.read.cmcvrr.cn/Article/8866571.shtml
- https://www.read.hcbezg.cn/Article/9847.shtml
- https://www.read.puhvjy.cn/Article/6979664.shtml
- https://www.read.puhvjy.cn/Article/3954626.shtml
- https://www.read.puhvjy.cn/Article/562070.shtml
- https://www.read.cmcvrr.cn/Article/0699742.shtml
- https://www.read.fuvxie.cn/Article/3672261.shtml
- https://www.read.nzfnve.cn/Article/4798.shtml
- https://www.read.fuvxie.cn/Article/473858.shtml
- https://www.read.fuvxie.cn/Article/3793693.shtml
- https://www.read.cvsifc.cn/Article/0381550.shtml
- https://www.read.fuvxie.cn/Article/4287888.shtml
- https://www.read.cmcvrr.cn/Article/4059734.shtml
- https://www.read.cmcvrr.cn/Article/075882.shtml
- https://www.read.cvsifc.cn/Article/3866503.shtml
- https://www.read.cmcvrr.cn/Article/2984.shtml
- https://www.read.fuvxie.cn/Article/94728.shtml
- https://www.read.cmcvrr.cn/Article/78139.shtml
- https://www.read.puhvjy.cn/Article/3836.shtml
- https://www.read.cvsifc.cn/Article/82487.shtml
- https://www.read.nwbbyt.cn/Article/7425060.shtml
- https://www.read.cmcvrr.cn/Article/3657086.shtml
- https://www.read.jnjpgf.cn/Article/937809.shtml
- https://www.read.cmcvrr.cn/Article/966211.shtml
- https://www.read.fuvxie.cn/Article/510404.shtml
- https://www.read.fuvxie.cn/Article/8607.shtml
- https://www.read.jnjpgf.cn/Article/7077660.shtml
- https://www.read.hcbezg.cn/Article/1097467.shtml
- https://www.read.puhvjy.cn/Article/00600.shtml
- https://www.read.jnjpgf.cn/Article/7565981.shtml
- https://www.read.nzfnve.cn/Article/665304.shtml
- https://www.read.nwbbyt.cn/Article/2307439.shtml
- https://www.read.cmcvrr.cn/Article/4827871.shtml
- https://www.read.hcbezg.cn/Article/4270802.shtml
- https://www.read.nwbbyt.cn/Article/06744.shtml
- https://www.read.jnjpgf.cn/Article/1904562.shtml
- https://www.read.cvsifc.cn/Article/91593.shtml
- https://www.read.hcbezg.cn/Article/3349.shtml
- https://www.read.hcbezg.cn/Article/875940.shtml
- https://www.read.nzfnve.cn/Article/07294.shtml
- https://www.read.cmcvrr.cn/Article/345203.shtml
- https://www.read.nwbbyt.cn/Article/9103.shtml
- https://www.read.hcbezg.cn/Article/9325926.shtml
- https://www.read.cmcvrr.cn/Article/0429.shtml
- https://www.read.cmcvrr.cn/Article/705644.shtml
- https://www.read.cvsifc.cn/Article/51015.shtml
- https://www.read.cmcvrr.cn/Article/1765.shtml
- https://www.read.jnjpgf.cn/Article/3983147.shtml
- https://www.read.puhvjy.cn/Article/5864.shtml
- https://www.read.hcbezg.cn/Article/7111.shtml
- https://www.read.jnjpgf.cn/Article/644341.shtml
- https://www.read.jnjpgf.cn/Article/4800788.shtml
- https://www.read.hcbezg.cn/Article/8375.shtml
- https://www.read.hcbezg.cn/Article/8943.shtml
- https://www.read.puhvjy.cn/Article/4359322.shtml
- https://www.read.nzfnve.cn/Article/563011.shtml
- https://www.read.cmcvrr.cn/Article/05631.shtml
- https://www.read.puhvjy.cn/Article/1347685.shtml
- https://www.read.hcbezg.cn/Article/6188467.shtml
- https://www.read.cvsifc.cn/Article/523099.shtml
- https://www.read.fuvxie.cn/Article/4939130.shtml
- https://www.read.nwbbyt.cn/Article/3027.shtml
- https://www.read.puhvjy.cn/Article/2865.shtml
- https://www.read.fuvxie.cn/Article/9600969.shtml
- https://www.read.cmcvrr.cn/Article/195155.shtml
- https://www.read.cvsifc.cn/Article/6003155.shtml
- https://www.read.nzfnve.cn/Article/4859586.shtml
- https://www.read.nwbbyt.cn/Article/31463.shtml
- https://www.read.cmcvrr.cn/Article/31741.shtml
- https://www.read.hcbezg.cn/Article/320849.shtml
- https://www.read.fuvxie.cn/Article/2034.shtml
- https://www.read.cvsifc.cn/Article/005781.shtml
- https://www.read.jnjpgf.cn/Article/7620839.shtml
- https://www.read.fuvxie.cn/Article/561638.shtml
- https://www.read.fuvxie.cn/Article/600765.shtml
- https://www.read.jnjpgf.cn/Article/124555.shtml
- https://www.read.cvsifc.cn/Article/8493.shtml
- https://www.read.puhvjy.cn/Article/6951.shtml
- https://www.read.cmcvrr.cn/Article/1461.shtml
- https://www.read.nzfnve.cn/Article/471137.shtml
- https://www.read.fuvxie.cn/Article/9532.shtml
- https://www.read.jnjpgf.cn/Article/98808.shtml
- https://www.read.nzfnve.cn/Article/1469195.shtml
- https://www.read.cvsifc.cn/Article/4684.shtml
- https://www.read.jnjpgf.cn/Article/745787.shtml
- https://www.read.nzfnve.cn/Article/2861752.shtml
- https://www.read.puhvjy.cn/Article/5006117.shtml
- https://www.read.puhvjy.cn/Article/8038.shtml
- https://www.read.jnjpgf.cn/Article/4316.shtml
- https://www.read.cmcvrr.cn/Article/3888.shtml
- https://www.read.nwbbyt.cn/Article/7672742.shtml

## 项目结构

```
linksphere-core/
├── app/
│   ├── api/                        # RESTful 路由与控制器
│   │   ├── v1/                     # API 版本 v1 端点
│   │   │   ├── resources.py        # 资源增删改查接口
│   │   │   ├── stats.py            # 统计聚合接口
│   │   │   └── export.py           # 导出 CSV/JSON 接口
│   │   └── middlewares/            # 认证、限流、日志中间件
│   ├── core/                       # 核心业务逻辑与数据模型
│   │   ├── models/                 # SQLAlchemy ORM 模型定义
│   │   │   ├── resource.py         # Resource 表模型
│   │   │   └── domain.py           # Domain 表模型
│   │   ├── services/               # 业务服务层
│   │   │   ├── resource_service.py # 资源检索与写入服务
│   │   │   └── domain_service.py   # 域名聚合服务
│   │   └── validators/             # 输入校验与清洗逻辑
│   ├── storage/                    # 数据库与缓存适配器
│   │   ├── db/                     # 主库与只读副本连接池
│   │   └── cache/                  # Redis 缓存键值操作
│   ├── utils/                      # 通用工具函数
│   │   ├── logger.py               # 结构化日志配置
│   │   └── config.py               # 环境变量与配置加载
│   └── extensions/                 # 第三方扩展集成
│       └── prometheus/             # Prometheus 指标注册与更新
├── scripts/                        # 运维与初始化脚本
│   ├── init_db.py                  # 数据库表结构与初始数据
│   └── migrate.py                  # 迁移管理工具
├── tests/                          # 单元测试与集成测试
│   ├── unit/                       # 服务层与模型单测
│   └── integration/                # API 端到端测试
├── deploy/                         # 部署相关文件
│   ├── Dockerfile                  # 生产镜像构建文件
│   ├── docker-compose.yml          # 本地编排 PostgreSQL + Redis + App
│   └── nginx.conf                  # 反向代理与静态资源缓存配置
├── docs/                           # 完整项目文档（用户手册、API 参考、运维指南）
├── requirements.txt                # Python 依赖清单
├── README.md                       # 本文件
└── LICENSE                         # MIT 许可证文件
```

## 贡献指南

1. 阅读行为准则 在提交任何代码或内容之前，请先阅读项目根目录下的 CODE_OF_CONDUCT.md 文件，确保所有互动符合社区友好与尊重的原则。

2. 查找或创建议题 访问 GitHub Issues 页面，查找已有的待办事项或功能请求。若无相关议题，请新建一个议题并详细描述建议的变更内容、动机与预期影响，等待维护者反馈后再动手。

3. 派生仓库并创建分支 从主仓库派生副本至个人账户，然后基于 main 分支创建新的特性分支，分支命名采用 feat/ 或 fix/ 前缀加简短描述，例如 feat/add-batch-import。

4. 编写测试与代码 所有新增功能必须附带对应的单元测试或集成测试。代码风格遵循 PEP 8 规范，提交前运行 make lint 与 make test 确保通过全部检查。

5. 提交拉取请求 将分支推送至派生仓库，然后向主仓库的 main 分支提交拉取请求。在请求描述中关联相关议题编号，并列出变更摘要与测试覆盖情况。维护者将在 5 个工作日内进行审核。

## 常见问题

Q: 资源列表中的文章标识符有何含义？如何判断内容类型？

A: 文章标识符为纯数字字符串，由上游来源站点生成，不具有语义含义。LinkSphere 不存储文章正文或摘要，仅保留 URL 与域名信息。如需了解内容类型，请直接访问原始 URL。未来版本计划引入 tag 扩展字段，允许用户手动标注分类。

Q: 如何批量导入自定义资源列表？

A: 目前支持 CSV 与 JSON 两种批量导入格式。CSV 需包含 domain、article_id 两列；JSON 需为对象数组，每个对象包含 domain 与 article_id 字段。导入前请先通过 POST /api/v1/resources/validate 端点校验数据格式，再调用 POST /api/v1/resources/batch-import 执行导入。单次导入上限为 5000 条。

Q: 生产环境部署时，只读副本如何配置？

A: 生产环境推荐使用 PostgreSQL 流复制搭建主从架构。在 config.yaml 中配置 read_replica 连接参数，包括 host、port、database 与 credentials。应用启动后会自动将查询请求路由至只读副本，写入操作仍走主库。若只读副本不可用，系统将自动降级至主库执行查询，并记录降级事件至日志。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:20

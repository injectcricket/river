# DocLink Hub

DocLink Hub 是一个面向技术文档聚合与外部资源链接管理的轻量级开源项目，旨在为开发者、技术写作团队以及知识库维护者提供统一的文档外链索引与分发能力。项目本身不存储任何实体文档内容，而是基于可配置的链接映射机制，将分散在多个来源的文档资源进行结构化整理，便于团队内部或公开社区进行高效查阅与引用。目标用户包括需要维护大量技术文档链接的运维人员、搭建知识中台的产品技术团队，以及希望批量管理外部参考资料的个人开发者。

## 功能概览

- **多源链接聚合** 支持将不同域名、不同路径下的外部文档链接统一纳入管理，形成集中式资源索引表。
- **分类与标签过滤** 每个外链可关联所属项目、文档类型、版本号等元数据，方便按条件筛选。
- **链接可用性探测** 内置简单的 HTTP 状态检查机制，可定期检测链接是否可访问，输出异常报告。
- **只读 API 输出** 提供 RESTful 风格的查询接口，支持按文档编号、来源域名等字段获取链接列表。
- **批量导入导出** 支持 CSV 与 JSON 格式的链接清单批量导入，并可导出为 Markdown 资源列表用于文档编写。
- **访问统计记录** 记录每个外链的点击次数与最近访问时间，辅助分析文档热度。
- **静态站点生成模式** 可将链接列表渲染为纯静态 HTML 页面，适合部署到 Nginx 或对象存储服务。

## 应用场景

1. **技术文档站的外链管理** 当技术博客或产品手册需要引用大量外部 .doc 资源时，可使用 DocLink Hub 维护引用地址，避免硬编码分散在多篇 Markdown 中，便于统一更新与失效替换。
2. **内部知识库的资源索引** 企业内部的运维手册、设计规范库等常包含指向不同部门共享存储或旧版文档系统的链接，通过本项目的分类能力可按项目或年份快速定位。
3. **开源项目的外部依赖说明** 开源软件在 README 或贡献指南中常列举第三方参考资料，使用 DocLink Hub 可生成格式规范、可版本化的资源清单，随代码仓库同步更新。
4. **数据迁移前的链接盘点** 在进行网站改版或文档系统迁移时，可利用本项目的导出功能梳理全部外链，评估迁移影响范围，避免遗漏重要引用。

## 快速开始

以下步骤可在 Linux / macOS / Windows WSL 环境中完成项目的克隆、安装与运行。

```bash
# 克隆代码仓库
git clone https://github.com/example/doclink-hub.git
cd doclink-hub

# 安装 Python 依赖（项目基于 Python 3.10+）
pip install -r requirements.txt

# 初始化示例链接数据库（使用项目自带的种子数据）
python manage.py initdb --seed

# 启动开发服务器，默认监听 8000 端口
python manage.py runserver
```

启动后访问 http://localhost:8000 可查看 Web 管理界面，或通过 API 获取链接数据。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.10 或更高 | 核心运行环境，低于此版本可能导致类型注解解析失败 |
| pip | 21.0 以上 | 用于安装第三方库，旧版本可能无法识别 pyproject.toml |
| SQLite | 3.35 或更高 | 内置数据库，用于存储链接元数据与统计信息，无需额外安装 |
| requests | 2.28.0 | 用于链接可用性探测，发送 HTTP 请求 |
| fastapi | 0.95.0 | 提供 API 接口服务，依赖 uvicorn 作为网关 |
| uvicorn | 0.21.0 | ASGI 服务器，用于生产环境部署时建议配合 gunicorn |
| pydantic | 2.0.0 | 数据校验与序列化，确保 API 输入输出的类型安全 |
| jinja2 | 3.1.0 | 模板引擎，用于静态站点生成及管理后台页面渲染 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门 | /docs/quickstart.md | 如何 5 分钟内搭建并运行项目；如何导入第一批链接 |
| 使用 | /docs/usage/api.md | API 端点的详细参数与返回格式；如何通过 curl 调用 |
| 管理 | /docs/admin/configuration.md | 如何自定义链接字段、修改探测间隔、调整日志级别 |
| 开发 | /docs/contributing/code-style.md | 代码规范、测试运行方式、Pull Request 提交流程 |

## 资源列表

- h5.mobile.puhvjy.cn/Article/8340.doc
- h5.mobile.nzfnve.cn/Article/7057309.doc
- h5.mobile.fuvxie.cn/Article/06350.doc
- h5.mobile.nwbbyt.cn/Article/5427283.doc
- h5.mobile.nzfnve.cn/Article/7459570.doc
- h5.mobile.fuvxie.cn/Article/7045.doc
- h5.mobile.nwbbyt.cn/Article/808355.doc
- h5.mobile.puhvjy.cn/Article/35744.doc
- h5.mobile.hcbezg.cn/Article/1158.doc
- h5.mobile.hcbezg.cn/Article/1564188.doc
- h5.mobile.hcbezg.cn/Article/95624.doc
- h5.mobile.cmcvrr.cn/Article/091750.doc
- h5.mobile.hcbezg.cn/Article/737131.doc
- h5.mobile.jnjpgf.cn/Article/6987418.doc
- h5.mobile.hcbezg.cn/Article/8645.doc
- h5.mobile.jnjpgf.cn/Article/6164.doc
- h5.mobile.nzfnve.cn/Article/70793.doc
- h5.mobile.nzfnve.cn/Article/8396.doc
- h5.mobile.nzfnve.cn/Article/047375.doc
- h5.mobile.cmcvrr.cn/Article/89467.doc
- h5.mobile.cmcvrr.cn/Article/1207248.doc
- h5.mobile.fuvxie.cn/Article/474832.doc
- h5.mobile.jnjpgf.cn/Article/7742393.doc
- h5.mobile.cmcvrr.cn/Article/81318.doc
- h5.mobile.hcbezg.cn/Article/06286.doc
- h5.mobile.puhvjy.cn/Article/6049567.doc
- h5.mobile.nzfnve.cn/Article/8366175.doc
- h5.mobile.nwbbyt.cn/Article/3560.doc
- h5.mobile.fuvxie.cn/Article/6237324.doc
- h5.mobile.hcbezg.cn/Article/8065863.doc
- h5.mobile.fuvxie.cn/Article/868263.doc
- h5.mobile.cmcvrr.cn/Article/573716.doc
- h5.mobile.puhvjy.cn/Article/142240.doc
- h5.mobile.cvsifc.cn/Article/0659869.doc
- h5.mobile.cmcvrr.cn/Article/53938.doc
- h5.mobile.puhvjy.cn/Article/78315.doc
- h5.mobile.fuvxie.cn/Article/0497.doc
- h5.mobile.hcbezg.cn/Article/6869.doc
- h5.mobile.fuvxie.cn/Article/1120414.doc
- h5.mobile.cvsifc.cn/Article/1098629.doc
- h5.mobile.cmcvrr.cn/Article/9767.doc
- h5.mobile.hcbezg.cn/Article/23787.doc
- h5.mobile.nwbbyt.cn/Article/360312.doc
- h5.mobile.jnjpgf.cn/Article/10487.doc
- h5.mobile.hcbezg.cn/Article/9373320.doc
- h5.mobile.puhvjy.cn/Article/537110.doc
- h5.mobile.jnjpgf.cn/Article/6873.doc
- h5.mobile.puhvjy.cn/Article/79274.doc
- h5.mobile.cvsifc.cn/Article/044626.doc
- h5.mobile.nzfnve.cn/Article/9470.doc
- h5.mobile.puhvjy.cn/Article/176143.doc
- h5.mobile.nwbbyt.cn/Article/809595.doc
- h5.mobile.nzfnve.cn/Article/7199.doc
- h5.mobile.nzfnve.cn/Article/8851762.doc
- h5.mobile.hcbezg.cn/Article/2020.doc
- h5.mobile.cmcvrr.cn/Article/1779.doc
- h5.mobile.nwbbyt.cn/Article/6703337.doc
- h5.mobile.nzfnve.cn/Article/65440.doc
- h5.mobile.hcbezg.cn/Article/221358.doc
- h5.mobile.cmcvrr.cn/Article/8411.doc
- h5.mobile.nzfnve.cn/Article/3777.doc
- h5.mobile.puhvjy.cn/Article/0201.doc
- h5.mobile.nwbbyt.cn/Article/3519886.doc
- h5.mobile.cvsifc.cn/Article/6848075.doc
- h5.mobile.cmcvrr.cn/Article/70850.doc
- h5.mobile.jnjpgf.cn/Article/357922.doc
- h5.mobile.nzfnve.cn/Article/4652783.doc
- h5.mobile.cmcvrr.cn/Article/767383.doc
- h5.mobile.nzfnve.cn/Article/41301.doc
- h5.mobile.fuvxie.cn/Article/0616.doc
- h5.mobile.nwbbyt.cn/Article/113802.doc
- h5.mobile.hcbezg.cn/Article/35303.doc
- h5.mobile.puhvjy.cn/Article/5285160.doc
- h5.mobile.jnjpgf.cn/Article/82348.doc
- h5.mobile.nzfnve.cn/Article/751578.doc
- h5.mobile.hcbezg.cn/Article/5381.doc
- h5.mobile.nzfnve.cn/Article/936868.doc
- h5.mobile.fuvxie.cn/Article/1897007.doc
- h5.mobile.cvsifc.cn/Article/582691.doc
- h5.mobile.fuvxie.cn/Article/6676.doc
- h5.mobile.puhvjy.cn/Article/2449321.doc
- h5.mobile.fuvxie.cn/Article/6009106.doc
- h5.mobile.puhvjy.cn/Article/3143.doc
- h5.mobile.cvsifc.cn/Article/47590.doc
- h5.mobile.puhvjy.cn/Article/4440.doc
- h5.mobile.puhvjy.cn/Article/7819710.doc
- h5.mobile.nzfnve.cn/Article/49197.doc
- h5.mobile.jnjpgf.cn/Article/4919.doc
- h5.mobile.nzfnve.cn/Article/47600.doc
- h5.mobile.nzfnve.cn/Article/4981863.doc
- h5.mobile.cvsifc.cn/Article/65332.doc
- h5.mobile.hcbezg.cn/Article/58410.doc
- h5.mobile.nwbbyt.cn/Article/030840.doc
- h5.mobile.fuvxie.cn/Article/9285.doc
- h5.mobile.jnjpgf.cn/Article/609277.doc
- h5.mobile.fuvxie.cn/Article/48982.doc
- h5.mobile.jnjpgf.cn/Article/43288.doc
- h5.mobile.hcbezg.cn/Article/078917.doc
- h5.mobile.fuvxie.cn/Article/34625.doc
- h5.mobile.nwbbyt.cn/Article/20706.doc
- h5.mobile.cvsifc.cn/Article/51432.doc
- h5.mobile.fuvxie.cn/Article/2917060.doc
- h5.mobile.nwbbyt.cn/Article/8610.doc
- h5.mobile.cvsifc.cn/Article/496501.doc
- h5.mobile.nwbbyt.cn/Article/6124.doc
- h5.mobile.puhvjy.cn/Article/73208.doc
- h5.mobile.nzfnve.cn/Article/601083.doc
- h5.mobile.cvsifc.cn/Article/8232.doc
- h5.mobile.puhvjy.cn/Article/8865.doc
- h5.mobile.puhvjy.cn/Article/873425.doc
- h5.mobile.jnjpgf.cn/Article/2083.doc
- h5.mobile.nwbbyt.cn/Article/1774.doc
- h5.mobile.hcbezg.cn/Article/9933.doc
- h5.mobile.cmcvrr.cn/Article/0539564.doc
- h5.mobile.nzfnve.cn/Article/014499.doc
- h5.mobile.cmcvrr.cn/Article/76357.doc
- h5.mobile.jnjpgf.cn/Article/61492.doc
- h5.mobile.nzfnve.cn/Article/1160784.doc
- h5.mobile.fuvxie.cn/Article/440203.doc
- h5.mobile.hcbezg.cn/Article/610414.doc
- h5.mobile.nzfnve.cn/Article/436256.doc
- h5.mobile.fuvxie.cn/Article/7297757.doc
- h5.mobile.nwbbyt.cn/Article/4369.doc
- h5.mobile.cvsifc.cn/Article/03627.doc
- h5.mobile.nwbbyt.cn/Article/4370.doc
- h5.mobile.fuvxie.cn/Article/584976.doc
- h5.mobile.jnjpgf.cn/Article/6525502.doc
- h5.mobile.cmcvrr.cn/Article/49131.doc
- h5.mobile.cvsifc.cn/Article/6082520.doc
- h5.mobile.hcbezg.cn/Article/806296.doc
- h5.mobile.hcbezg.cn/Article/7249191.doc
- h5.mobile.fuvxie.cn/Article/7765.doc
- h5.mobile.puhvjy.cn/Article/8521270.doc
- h5.mobile.cvsifc.cn/Article/2149164.doc
- h5.mobile.nzfnve.cn/Article/4401120.doc
- h5.mobile.fuvxie.cn/Article/2021481.doc
- h5.mobile.puhvjy.cn/Article/43417.doc
- h5.mobile.cvsifc.cn/Article/489611.doc
- h5.mobile.cvsifc.cn/Article/8917.doc
- h5.mobile.jnjpgf.cn/Article/13458.doc
- h5.mobile.jnjpgf.cn/Article/2212.doc
- h5.mobile.cvsifc.cn/Article/97060.doc
- h5.mobile.cmcvrr.cn/Article/167685.doc
- h5.mobile.hcbezg.cn/Article/54645.doc
- h5.mobile.nwbbyt.cn/Article/216727.doc
- h5.mobile.jnjpgf.cn/Article/580623.doc
- h5.mobile.jnjpgf.cn/Article/61385.doc
- h5.mobile.puhvjy.cn/Article/6076067.doc
- h5.mobile.fuvxie.cn/Article/4021.doc
- h5.mobile.puhvjy.cn/Article/54228.doc
- h5.mobile.jnjpgf.cn/Article/7669.doc
- h5.mobile.cmcvrr.cn/Article/7884774.doc
- h5.mobile.cvsifc.cn/Article/80225.doc
- h5.mobile.puhvjy.cn/Article/9646.doc
- h5.mobile.cmcvrr.cn/Article/55161.doc
- h5.mobile.hcbezg.cn/Article/835400.doc
- h5.mobile.fuvxie.cn/Article/7616.doc
- h5.mobile.puhvjy.cn/Article/319652.doc
- h5.mobile.hcbezg.cn/Article/5262.doc
- h5.mobile.cmcvrr.cn/Article/8866571.doc
- h5.mobile.hcbezg.cn/Article/9847.doc
- h5.mobile.puhvjy.cn/Article/6979664.doc
- h5.mobile.puhvjy.cn/Article/3954626.doc
- h5.mobile.puhvjy.cn/Article/562070.doc
- h5.mobile.cmcvrr.cn/Article/0699742.doc
- h5.mobile.fuvxie.cn/Article/3672261.doc
- h5.mobile.nzfnve.cn/Article/4798.doc
- h5.mobile.fuvxie.cn/Article/473858.doc
- h5.mobile.fuvxie.cn/Article/3793693.doc
- h5.mobile.cvsifc.cn/Article/0381550.doc
- h5.mobile.fuvxie.cn/Article/4287888.doc
- h5.mobile.cmcvrr.cn/Article/4059734.doc
- h5.mobile.cmcvrr.cn/Article/075882.doc
- h5.mobile.cvsifc.cn/Article/3866503.doc
- h5.mobile.cmcvrr.cn/Article/2984.doc
- h5.mobile.fuvxie.cn/Article/94728.doc
- h5.mobile.cmcvrr.cn/Article/78139.doc
- h5.mobile.puhvjy.cn/Article/3836.doc
- h5.mobile.cvsifc.cn/Article/82487.doc
- h5.mobile.nwbbyt.cn/Article/7425060.doc
- h5.mobile.cmcvrr.cn/Article/3657086.doc
- h5.mobile.jnjpgf.cn/Article/937809.doc
- h5.mobile.cmcvrr.cn/Article/966211.doc
- h5.mobile.fuvxie.cn/Article/510404.doc
- h5.mobile.fuvxie.cn/Article/8607.doc
- h5.mobile.jnjpgf.cn/Article/7077660.doc
- h5.mobile.hcbezg.cn/Article/1097467.doc
- h5.mobile.puhvjy.cn/Article/00600.doc
- h5.mobile.jnjpgf.cn/Article/7565981.doc
- h5.mobile.nzfnve.cn/Article/665304.doc
- h5.mobile.nwbbyt.cn/Article/2307439.doc
- h5.mobile.cmcvrr.cn/Article/4827871.doc
- h5.mobile.hcbezg.cn/Article/4270802.doc
- h5.mobile.nwbbyt.cn/Article/06744.doc
- h5.mobile.jnjpgf.cn/Article/1904562.doc
- h5.mobile.cvsifc.cn/Article/91593.doc
- h5.mobile.hcbezg.cn/Article/3349.doc
- h5.mobile.hcbezg.cn/Article/875940.doc
- h5.mobile.nzfnve.cn/Article/07294.doc
- h5.mobile.cmcvrr.cn/Article/345203.doc
- h5.mobile.nwbbyt.cn/Article/9103.doc
- h5.mobile.hcbezg.cn/Article/9325926.doc
- h5.mobile.cmcvrr.cn/Article/0429.doc
- h5.mobile.cmcvrr.cn/Article/705644.doc
- h5.mobile.cvsifc.cn/Article/51015.doc
- h5.mobile.cmcvrr.cn/Article/1765.doc
- h5.mobile.jnjpgf.cn/Article/3983147.doc
- h5.mobile.puhvjy.cn/Article/5864.doc
- h5.mobile.hcbezg.cn/Article/7111.doc
- h5.mobile.jnjpgf.cn/Article/644341.doc
- h5.mobile.jnjpgf.cn/Article/4800788.doc
- h5.mobile.hcbezg.cn/Article/8375.doc
- h5.mobile.hcbezg.cn/Article/8943.doc
- h5.mobile.puhvjy.cn/Article/4359322.doc
- h5.mobile.nzfnve.cn/Article/563011.doc
- h5.mobile.cmcvrr.cn/Article/05631.doc
- h5.mobile.puhvjy.cn/Article/1347685.doc
- h5.mobile.hcbezg.cn/Article/6188467.doc
- h5.mobile.cvsifc.cn/Article/523099.doc
- h5.mobile.fuvxie.cn/Article/4939130.doc
- h5.mobile.nwbbyt.cn/Article/3027.doc
- h5.mobile.puhvjy.cn/Article/2865.doc
- h5.mobile.fuvxie.cn/Article/9600969.doc
- h5.mobile.cmcvrr.cn/Article/195155.doc
- h5.mobile.cvsifc.cn/Article/6003155.doc
- h5.mobile.nzfnve.cn/Article/4859586.doc
- h5.mobile.nwbbyt.cn/Article/31463.doc
- h5.mobile.cmcvrr.cn/Article/31741.doc
- h5.mobile.hcbezg.cn/Article/320849.doc
- h5.mobile.fuvxie.cn/Article/2034.doc
- h5.mobile.cvsifc.cn/Article/005781.doc
- h5.mobile.jnjpgf.cn/Article/7620839.doc
- h5.mobile.fuvxie.cn/Article/561638.doc
- h5.mobile.fuvxie.cn/Article/600765.doc
- h5.mobile.jnjpgf.cn/Article/124555.doc
- h5.mobile.cvsifc.cn/Article/8493.doc
- h5.mobile.puhvjy.cn/Article/6951.doc
- h5.mobile.cmcvrr.cn/Article/1461.doc
- h5.mobile.nzfnve.cn/Article/471137.doc
- h5.mobile.fuvxie.cn/Article/9532.doc
- h5.mobile.jnjpgf.cn/Article/98808.doc
- h5.mobile.nzfnve.cn/Article/1469195.doc
- h5.mobile.cvsifc.cn/Article/4684.doc
- h5.mobile.jnjpgf.cn/Article/745787.doc
- h5.mobile.nzfnve.cn/Article/2861752.doc
- h5.mobile.puhvjy.cn/Article/5006117.doc
- h5.mobile.puhvjy.cn/Article/8038.doc
- h5.mobile.jnjpgf.cn/Article/4316.doc
- h5.mobile.cmcvrr.cn/Article/3888.doc
- h5.mobile.nwbbyt.cn/Article/7672742.doc

## 项目结构

```
doclink-hub/
├── app/                                   # 主应用模块
│   ├── api/                               # RESTful API 路由层
│   │   ├── endpoints/                     # 各资源端点（links, tags, stats）
│   │   └── dependencies.py                # 依赖注入（数据库会话、认证）
│   ├── core/                              # 核心业务逻辑
│   │   ├── checker.py                     # 链接可用性探测调度器
│   │   ├── importer.py                    # CSV/JSON 批量导入处理器
│   │   └── exporter.py                    # 资源列表导出为 Markdown/HTML
│   ├── models/                            # SQLAlchemy 数据模型
│   │   ├── link.py                        # 链接主表（URL、标题、分类、状态）
│   │   ├── tag.py                         # 标签表
│   │   └── visit_log.py                   # 访问日志表
│   ├── schemas/                           # Pydantic 校验与序列化结构
│   │   ├── request.py                     # 请求体结构
│   │   └── response.py                    # 返回体结构
│   ├── templates/                         # Jinja2 页面模板
│   │   ├── admin/                         # 管理后台页面
│   │   └── static/                        # 静态站点生成模板
│   └── utils/                             # 通用工具函数
│       ├── http_client.py                 # 带超时与重试的 HTTP 客户端
│       └── logger.py                      # 日志配置与格式化
├── config/                                # 配置文件目录
│   ├── settings.py                        # 全局配置（数据库路径、探测间隔）
│   └── logging.yaml                       # 日志级别与输出格式
├── data/                                  # 数据存储目录
│   ├── db/                                # SQLite 数据库文件存放位置
│   └── seed/                              # 初始化种子数据（JSON 示例）
├── scripts/                               # 运维与辅助脚本
│   ├── check_all_links.py                 # 手动触发全量链接探测
│   └── generate_static.py                 # 生成静态站点到 output 目录
├── tests/                                 # 单元测试与集成测试
│   ├── test_api/                          # API 接口测试用例
│   └── test_core/                         # 核心逻辑测试用例
├── .env.example                            # 环境变量模板（数据库路径、密钥等）
├── docker-compose.yml                      # 容器编排示例（含 Nginx + 应用）
├── Dockerfile                              # 多阶段构建镜像文件
├── pyproject.toml                          # 项目元数据与构建配置
├── requirements.txt                        # 生产环境依赖锁定
└── README.md                               # 项目说明文档（本文件）
```

## 贡献指南

1. 在 GitHub Issues 中查找标记为 "help wanted" 或 "good first issue" 的问题，或创建新 Issue 描述你希望解决的问题或新增功能，等待社区维护者确认。
2. Fork 本仓库到你的个人账户，然后克隆到本地进行开发。建议在 dev 分支上工作，并保持与上游 main 分支的同步。
3. 编写代码或文档修改后，运行项目自带的测试套件（pytest tests/）确保所有用例通过，同时遵守 PEP 8 代码风格与项目内的类型注解要求。
4. 提交 Pull Request 时，请清晰描述变更内容、关联 Issue 编号以及测试覆盖情况。若涉及 API 变动，需同步更新 /docs/usage/api.md 文档。
5. 维护者会在 3 个工作日内进行 Code Review，根据反馈调整后合并。合并后你的贡献将出现在下一个版本的更新日志中。

## 常见问题

**Q: 项目是否内置了文档内容的全文检索能力？**

A: 本项目只管理文档的外部链接（URL）及其元数据，不存储或索引文档内部的文字内容。如需全文搜索，建议配合 Elasticsearch 或 Meilisearch 等独立搜索引擎，将链接指向的文档内容抓取后建立索引。

**Q: 链接可用性探测会误报吗？例如目标服务器有反爬机制或临时维护。**

A: 探测模块默认使用合理的超时（10 秒）和重试策略（最多 2 次），并遵循 HTTP 标准状态码（2xx 为正常，3xx 跟随重定向，4xx/5xx 为异常）。对于已知有反爬机制的站点，可在配置中为该域名单独设置 User-Agent 或跳过探测的白名单。

**Q: 如何迁移已有的外链数据到 DocLink Hub？**

A: 项目提供 CSV 和 JSON 两种批量导入方式。CSV 需包含 `url`、`title`、`category` 三列，JSON 需符合 schema 定义。具体字段映射与示例文件请参考 /docs/admin/import.md 文档。导入后系统会自动去重并生成初始访问统计。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

# WebLink Hub

WebLink Hub 是一个面向技术团队、内容策展人与研究者的轻量级外链资源归集与分发平台。项目定位于将分散在多源渠道中的文档型资源（.doc 格式）进行统一索引、分类存储与快速检索，解决团队或个人在信息收集过程中面临的链接散落、域名分散、资源过期难追溯等痛点。WebLink Hub 不改变原始资源的存储位置，仅提供结构化的索引层与简易的管理界面，适用于中小规模的知识库构建、技术资料归档与内部培训材料分发场景。

## 功能概览

- 多源链接统一归集：支持从多个独立域名来源批量导入文档链接，自动识别资源类型与来源标识，构建集中式索引目录。

- 批量资源校验与状态追踪：定期对已收录的文档链接进行可访问性检查，标记失效链接并生成报告，保障资源库的可用性。

- 分级分类标签管理：用户可自定义标签体系，对每条资源按技术领域、文档类型、版本状态等维度进行标记，便于后续筛选与聚合。

- 全文元数据检索：基于文档标题、来源域名、收录时间、标签等字段提供快速检索能力，支持模糊匹配与精确过滤两种模式。

- 导入导出与数据迁移：支持 CSV 与 JSON 格式的批量导入导出，便于与其他知识管理工具或内部系统进行数据对接与迁移。

- 访问统计与热度排序：记录每条资源的点击次数与最后访问时间，支持按热度或更新时间排序，辅助识别高频使用的核心资源。

- 私有化部署与单机运行：项目无外部依赖，基于 SQLite 本地数据库运行，可直接在内网服务器或个人工作站上启动，无需联网即可使用全部功能。

## 应用场景

企业内部知识库构建：技术团队可将分散在多个项目文档库、旧版 Wiki 以及外部参考站点中的 .doc 资源通过 WebLink Hub 统一索引，为团队成员提供单一入口查找历史技术方案与验收报告。

在线教育资料整理：培训机构或教育内容生产者可将不同域名下存放的课程补充材料、作业模板与案例文档集中管理，通过标签区分课程阶段与难度等级，方便学员按需查阅。

技术文档归档与迁移辅助：在系统升级或文档平台更换期间，使用 WebLink Hub 对旧平台上的文档链接进行全面梳理与状态检测，生成有效资源清单，为批量迁移提供数据基础。

个人研究资料库构建：研究人员在文献调研阶段收集的大量在线文档链接可通过该平台进行结构化存储，结合检索与标签功能快速定位特定主题或来源的资料，提升文献管理效率。

## 快速开始

以下步骤指导您在本地环境完成 WebLink Hub 的克隆、安装与启动。

```bash
# 克隆仓库
git clone https://github.com/weblink-hub/weblink-hub.git
cd weblink-hub

# 安装 Python 依赖（推荐使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 系统请使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化本地数据库
python scripts/init_db.py

# 启动开发服务器
python app.py runserver --host=0.0.0.0 --port=8080
```

启动成功后，访问 http://localhost:8080 即可进入 WebLink Hub 的管理界面。首次启动会自动创建默认管理员账户，初始密码在控制台日志中输出，请及时修改。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 LTS 版本 |
| SQLite | 3.28 及以上 | 内置数据库，无需额外安装，用于存储索引数据 |
| requests | 2.25.0 及以上 | 用于资源链接状态校验与网络请求 |
| flask | 2.0.0 及以上 | Web 服务框架，提供管理界面与 REST API |
| flask-sqlalchemy | 2.5.0 及以上 | 数据库 ORM 层，简化数据操作 |
| python-dotenv | 0.19.0 及以上 | 环境变量管理，用于配置文件分离 |
| gunicorn | 20.1.0 及以上 | 生产环境推荐部署的 WSGI 服务器（Linux/macOS） |
| waitress | 2.1.0 及以上 | Windows 平台推荐的 WSGI 服务器替代方案 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide.md | 如何添加资源、管理标签、执行检索以及查看统计报表 |
| 部署指南 | /docs/deployment.md | 如何在内网服务器、云主机或容器环境中完成生产级部署 |
| API 参考 | /docs/api-reference.md | 对外提供的 REST API 接口定义、请求参数与返回格式说明 |
| 数据模型 | /docs/data-model.md | 数据库表结构、字段含义以及索引设计原理 |
| 运维手册 | /docs/operations.md | 日志管理、数据库备份、性能调优与故障排查步骤 |

## 资源列表

- h5.mobile.cmcvrr.cn/Article/180561.doc
- h5.mobile.nwbbyt.cn/Article/79400.doc
- h5.mobile.nwbbyt.cn/Article/679874.doc
- h5.mobile.nzfnve.cn/Article/592112.doc
- h5.mobile.fuvxie.cn/Article/4889.doc
- h5.mobile.cmcvrr.cn/Article/06480.doc
- h5.mobile.nwbbyt.cn/Article/14815.doc
- h5.mobile.fuvxie.cn/Article/942632.doc
- h5.mobile.nzfnve.cn/Article/26098.doc
- h5.mobile.cvsifc.cn/Article/085368.doc
- h5.mobile.cmcvrr.cn/Article/41986.doc
- h5.mobile.cvsifc.cn/Article/33944.doc
- h5.mobile.cmcvrr.cn/Article/4336.doc
- h5.mobile.cvsifc.cn/Article/466566.doc
- h5.mobile.hcbezg.cn/Article/38659.doc
- h5.mobile.nzfnve.cn/Article/1208.doc
- h5.mobile.hcbezg.cn/Article/93219.doc
- h5.mobile.fuvxie.cn/Article/263028.doc
- h5.mobile.puhvjy.cn/Article/525703.doc
- h5.mobile.nwbbyt.cn/Article/2410.doc
- h5.mobile.jnjpgf.cn/Article/6766.doc
- h5.mobile.cvsifc.cn/Article/727449.doc
- h5.mobile.fuvxie.cn/Article/71038.doc
- h5.mobile.nwbbyt.cn/Article/2493.doc
- h5.mobile.fuvxie.cn/Article/898716.doc
- h5.mobile.hcbezg.cn/Article/8319564.doc
- h5.mobile.fuvxie.cn/Article/10802.doc
- h5.mobile.hcbezg.cn/Article/880912.doc
- h5.mobile.hcbezg.cn/Article/407436.doc
- h5.mobile.cmcvrr.cn/Article/9904221.doc
- h5.mobile.cvsifc.cn/Article/3770116.doc
- h5.mobile.hcbezg.cn/Article/64635.doc
- h5.mobile.puhvjy.cn/Article/3830723.doc
- h5.mobile.hcbezg.cn/Article/8344588.doc
- h5.mobile.fuvxie.cn/Article/1537.doc
- h5.mobile.nwbbyt.cn/Article/4484.doc
- h5.mobile.jnjpgf.cn/Article/93769.doc
- h5.mobile.cmcvrr.cn/Article/00019.doc
- h5.mobile.nzfnve.cn/Article/37347.doc
- h5.mobile.hcbezg.cn/Article/0439125.doc
- h5.mobile.cmcvrr.cn/Article/261160.doc
- h5.mobile.fuvxie.cn/Article/5366.doc
- h5.mobile.cmcvrr.cn/Article/33230.doc
- h5.mobile.hcbezg.cn/Article/630831.doc
- h5.mobile.hcbezg.cn/Article/679412.doc
- h5.mobile.hcbezg.cn/Article/452302.doc
- h5.mobile.jnjpgf.cn/Article/66186.doc
- h5.mobile.jnjpgf.cn/Article/0811.doc
- h5.mobile.nzfnve.cn/Article/0096.doc
- h5.mobile.cvsifc.cn/Article/01034.doc
- h5.mobile.cmcvrr.cn/Article/3019.doc
- h5.mobile.puhvjy.cn/Article/0579950.doc
- h5.mobile.fuvxie.cn/Article/32489.doc
- h5.mobile.fuvxie.cn/Article/5648328.doc
- h5.mobile.cvsifc.cn/Article/7387.doc
- h5.mobile.nzfnve.cn/Article/571234.doc
- h5.mobile.nwbbyt.cn/Article/3363561.doc
- h5.mobile.puhvjy.cn/Article/9555878.doc
- h5.mobile.nwbbyt.cn/Article/172270.doc
- h5.mobile.puhvjy.cn/Article/3340587.doc
- h5.mobile.puhvjy.cn/Article/06064.doc
- h5.mobile.hcbezg.cn/Article/023411.doc
- h5.mobile.nwbbyt.cn/Article/32217.doc
- h5.mobile.cmcvrr.cn/Article/29105.doc
- h5.mobile.hcbezg.cn/Article/0511.doc
- h5.mobile.cvsifc.cn/Article/786720.doc
- h5.mobile.jnjpgf.cn/Article/089431.doc
- h5.mobile.puhvjy.cn/Article/7939817.doc
- h5.mobile.cvsifc.cn/Article/5921625.doc
- h5.mobile.cmcvrr.cn/Article/5071387.doc
- h5.mobile.nwbbyt.cn/Article/0049.doc
- h5.mobile.puhvjy.cn/Article/55026.doc
- h5.mobile.nzfnve.cn/Article/856260.doc
- h5.mobile.hcbezg.cn/Article/3464275.doc
- h5.mobile.nwbbyt.cn/Article/85334.doc
- h5.mobile.jnjpgf.cn/Article/8549.doc
- h5.mobile.hcbezg.cn/Article/12389.doc
- h5.mobile.fuvxie.cn/Article/295668.doc
- h5.mobile.jnjpgf.cn/Article/280069.doc
- h5.mobile.hcbezg.cn/Article/65854.doc
- h5.mobile.jnjpgf.cn/Article/867711.doc
- h5.mobile.nwbbyt.cn/Article/8078146.doc
- h5.mobile.hcbezg.cn/Article/8278745.doc
- h5.mobile.hcbezg.cn/Article/5644.doc
- h5.mobile.puhvjy.cn/Article/2267.doc
- h5.mobile.nzfnve.cn/Article/1523596.doc
- h5.mobile.hcbezg.cn/Article/4620029.doc
- h5.mobile.nzfnve.cn/Article/2141717.doc
- h5.mobile.hcbezg.cn/Article/73500.doc
- h5.mobile.cmcvrr.cn/Article/8068.doc
- h5.mobile.jnjpgf.cn/Article/6303.doc
- h5.mobile.nwbbyt.cn/Article/2666.doc
- h5.mobile.hcbezg.cn/Article/7332453.doc
- h5.mobile.puhvjy.cn/Article/38738.doc
- h5.mobile.jnjpgf.cn/Article/8404677.doc
- h5.mobile.hcbezg.cn/Article/57249.doc
- h5.mobile.jnjpgf.cn/Article/7030.doc
- h5.mobile.fuvxie.cn/Article/06735.doc
- h5.mobile.fuvxie.cn/Article/8789.doc
- h5.mobile.cvsifc.cn/Article/04388.doc
- h5.mobile.nzfnve.cn/Article/0663.doc
- h5.mobile.nzfnve.cn/Article/3957165.doc
- h5.mobile.fuvxie.cn/Article/26505.doc
- h5.mobile.fuvxie.cn/Article/1153.doc
- h5.mobile.cmcvrr.cn/Article/9088.doc
- h5.mobile.hcbezg.cn/Article/08901.doc
- h5.mobile.nwbbyt.cn/Article/386588.doc
- h5.mobile.cmcvrr.cn/Article/8876.doc
- h5.mobile.puhvjy.cn/Article/19391.doc
- h5.mobile.nwbbyt.cn/Article/121778.doc
- h5.mobile.jnjpgf.cn/Article/7616316.doc
- h5.mobile.nwbbyt.cn/Article/263202.doc
- h5.mobile.fuvxie.cn/Article/266735.doc
- h5.mobile.nwbbyt.cn/Article/9346118.doc
- h5.mobile.fuvxie.cn/Article/76243.doc
- h5.mobile.hcbezg.cn/Article/45745.doc
- h5.mobile.cvsifc.cn/Article/9679080.doc
- h5.mobile.puhvjy.cn/Article/415275.doc
- h5.mobile.fuvxie.cn/Article/9534.doc
- h5.mobile.puhvjy.cn/Article/5407817.doc
- h5.mobile.cmcvrr.cn/Article/157052.doc
- h5.mobile.cvsifc.cn/Article/2610.doc
- h5.mobile.cmcvrr.cn/Article/22969.doc
- h5.mobile.fuvxie.cn/Article/6189443.doc
- h5.mobile.fuvxie.cn/Article/12015.doc
- h5.mobile.nzfnve.cn/Article/0825071.doc
- h5.mobile.nzfnve.cn/Article/1722252.doc
- h5.mobile.jnjpgf.cn/Article/60695.doc
- h5.mobile.jnjpgf.cn/Article/682503.doc
- h5.mobile.nzfnve.cn/Article/8987.doc
- h5.mobile.jnjpgf.cn/Article/88341.doc
- h5.mobile.fuvxie.cn/Article/891064.doc
- h5.mobile.puhvjy.cn/Article/640109.doc
- h5.mobile.jnjpgf.cn/Article/281994.doc
- h5.mobile.nwbbyt.cn/Article/08882.doc
- h5.mobile.hcbezg.cn/Article/4615828.doc
- h5.mobile.nzfnve.cn/Article/444008.doc
- h5.mobile.cmcvrr.cn/Article/9609.doc
- h5.mobile.fuvxie.cn/Article/7882.doc
- h5.mobile.cmcvrr.cn/Article/25847.doc
- h5.mobile.nwbbyt.cn/Article/57229.doc
- h5.mobile.nwbbyt.cn/Article/626025.doc
- h5.mobile.cmcvrr.cn/Article/940993.doc
- h5.mobile.nzfnve.cn/Article/8409498.doc
- h5.mobile.cmcvrr.cn/Article/3641584.doc
- h5.mobile.nzfnve.cn/Article/8348045.doc
- h5.mobile.nwbbyt.cn/Article/742501.doc
- h5.mobile.hcbezg.cn/Article/20969.doc
- h5.mobile.jnjpgf.cn/Article/6490244.doc
- h5.mobile.fuvxie.cn/Article/6585.doc
- h5.mobile.nwbbyt.cn/Article/212600.doc
- h5.mobile.puhvjy.cn/Article/979634.doc
- h5.mobile.hcbezg.cn/Article/915335.doc
- h5.mobile.nwbbyt.cn/Article/33837.doc
- h5.mobile.cmcvrr.cn/Article/2848919.doc
- h5.mobile.nwbbyt.cn/Article/6020826.doc
- h5.mobile.hcbezg.cn/Article/6613.doc
- h5.mobile.cmcvrr.cn/Article/6771.doc
- h5.mobile.nzfnve.cn/Article/5471238.doc
- h5.mobile.nwbbyt.cn/Article/013645.doc
- h5.mobile.fuvxie.cn/Article/0032.doc
- h5.mobile.fuvxie.cn/Article/39662.doc
- h5.mobile.nzfnve.cn/Article/44080.doc
- h5.mobile.cmcvrr.cn/Article/9444374.doc
- h5.mobile.cvsifc.cn/Article/12864.doc
- h5.mobile.puhvjy.cn/Article/0738.doc
- h5.mobile.nzfnve.cn/Article/7488639.doc
- h5.mobile.puhvjy.cn/Article/4708665.doc
- h5.mobile.fuvxie.cn/Article/3767.doc
- h5.mobile.fuvxie.cn/Article/084663.doc
- h5.mobile.nzfnve.cn/Article/7118.doc
- h5.mobile.jnjpgf.cn/Article/9335.doc
- h5.mobile.cmcvrr.cn/Article/2572.doc
- h5.mobile.hcbezg.cn/Article/2429.doc
- h5.mobile.nwbbyt.cn/Article/2458.doc
- h5.mobile.puhvjy.cn/Article/375921.doc
- h5.mobile.cmcvrr.cn/Article/087757.doc
- h5.mobile.cvsifc.cn/Article/02181.doc
- h5.mobile.nwbbyt.cn/Article/57614.doc
- h5.mobile.nwbbyt.cn/Article/676302.doc
- h5.mobile.puhvjy.cn/Article/2412.doc
- h5.mobile.cmcvrr.cn/Article/87999.doc
- h5.mobile.hcbezg.cn/Article/51962.doc
- h5.mobile.puhvjy.cn/Article/1095.doc
- h5.mobile.hcbezg.cn/Article/56967.doc
- h5.mobile.jnjpgf.cn/Article/9361635.doc
- h5.mobile.jnjpgf.cn/Article/230001.doc
- h5.mobile.jnjpgf.cn/Article/5961617.doc
- h5.mobile.hcbezg.cn/Article/761336.doc
- h5.mobile.fuvxie.cn/Article/532469.doc
- h5.mobile.hcbezg.cn/Article/220410.doc
- h5.mobile.fuvxie.cn/Article/9559712.doc
- h5.mobile.cmcvrr.cn/Article/12355.doc
- h5.mobile.fuvxie.cn/Article/934452.doc
- h5.mobile.jnjpgf.cn/Article/5552.doc
- h5.mobile.cvsifc.cn/Article/512906.doc
- h5.mobile.cmcvrr.cn/Article/3275744.doc
- h5.mobile.nwbbyt.cn/Article/90888.doc
- h5.mobile.cmcvrr.cn/Article/3061.doc
- h5.mobile.nwbbyt.cn/Article/735796.doc
- h5.mobile.cvsifc.cn/Article/846162.doc
- h5.mobile.nzfnve.cn/Article/45222.doc
- h5.mobile.cmcvrr.cn/Article/4046112.doc
- h5.mobile.cmcvrr.cn/Article/1757913.doc
- h5.mobile.cvsifc.cn/Article/60612.doc
- h5.mobile.jnjpgf.cn/Article/790356.doc
- h5.mobile.puhvjy.cn/Article/9979.doc
- h5.mobile.jnjpgf.cn/Article/97295.doc
- h5.mobile.cmcvrr.cn/Article/1168.doc
- h5.mobile.cmcvrr.cn/Article/6494884.doc
- h5.mobile.jnjpgf.cn/Article/17265.doc
- h5.mobile.fuvxie.cn/Article/1184632.doc
- h5.mobile.cvsifc.cn/Article/02293.doc
- h5.mobile.nwbbyt.cn/Article/149391.doc
- h5.mobile.jnjpgf.cn/Article/1988428.doc
- h5.mobile.hcbezg.cn/Article/8036.doc
- h5.mobile.fuvxie.cn/Article/9203855.doc
- h5.mobile.cmcvrr.cn/Article/858053.doc
- h5.mobile.nzfnve.cn/Article/771572.doc
- h5.mobile.cmcvrr.cn/Article/9111.doc
- h5.mobile.cvsifc.cn/Article/4510997.doc
- h5.mobile.nzfnve.cn/Article/61358.doc
- h5.mobile.jnjpgf.cn/Article/731632.doc
- h5.mobile.puhvjy.cn/Article/3588200.doc
- h5.mobile.nzfnve.cn/Article/5427148.doc
- h5.mobile.fuvxie.cn/Article/0460.doc
- h5.mobile.puhvjy.cn/Article/87443.doc
- h5.mobile.cvsifc.cn/Article/62010.doc
- h5.mobile.nwbbyt.cn/Article/0151610.doc
- h5.mobile.cvsifc.cn/Article/4291.doc
- h5.mobile.cmcvrr.cn/Article/9214.doc
- h5.mobile.puhvjy.cn/Article/1697.doc
- h5.mobile.hcbezg.cn/Article/723633.doc
- h5.mobile.nwbbyt.cn/Article/2273456.doc
- h5.mobile.hcbezg.cn/Article/288077.doc
- h5.mobile.nwbbyt.cn/Article/970117.doc
- h5.mobile.cvsifc.cn/Article/27741.doc
- h5.mobile.nwbbyt.cn/Article/3696120.doc
- h5.mobile.jnjpgf.cn/Article/5686.doc
- h5.mobile.fuvxie.cn/Article/4774715.doc
- h5.mobile.puhvjy.cn/Article/3538.doc
- h5.mobile.nwbbyt.cn/Article/294174.doc
- h5.mobile.nzfnve.cn/Article/0465.doc
- h5.mobile.hcbezg.cn/Article/0962707.doc
- h5.mobile.hcbezg.cn/Article/7306.doc
- h5.mobile.hcbezg.cn/Article/8611775.doc
- h5.mobile.fuvxie.cn/Article/16629.doc
- h5.mobile.hcbezg.cn/Article/2756.doc
- h5.mobile.cmcvrr.cn/Article/641150.doc
- h5.mobile.puhvjy.cn/Article/4008027.doc

## 项目结构

```
weblink-hub/
├── app/                                # 应用主目录
│   ├── __init__.py                     # 应用工厂函数与配置加载
│   ├── models.py                       # 数据模型定义（Resource, Tag, AccessLog）
│   ├── routes/                         # 路由视图层
│   │   ├── __init__.py                 # 蓝图注册与路由聚合
│   │   ├── resource.py                 # 资源增删改查、导入导出接口
│   │   ├── tag.py                      # 标签管理相关路由
│   │   └── stats.py                    # 统计报表与热度数据接口
│   ├── services/                       # 业务逻辑层
│   │   ├── __init__.py
│   │   ├── fetcher.py                  # 链接可访问性校验与元数据抓取
│   │   ├── indexer.py                  # 批量导入与索引构建逻辑
│   │   └── exporter.py                 # CSV/JSON 导出格式化处理
│   ├── static/                         # 静态资源目录
│   │   ├── css/                        # 样式表文件
│   │   └── js/                         # 前端交互脚本
│   └── templates/                      # Jinja2 模板目录
│       ├── base.html                   # 基础布局模板
│       ├── dashboard.html              # 仪表盘页面
│       ├── resource_list.html          # 资源列表与检索页面
│       └── resource_detail.html        # 单条资源详情与编辑页面
├── scripts/                            # 命令行工具与辅助脚本
│   ├── init_db.py                      # 初始化数据库表结构与默认数据
│   ├── import_batch.py                 # 批量导入外部链接列表
│   └── check_links.py                  # 手动触发全量链接校验任务
├── tests/                              # 单元测试与集成测试目录
│   ├── test_models.py                  # 数据模型层测试用例
│   ├── test_routes.py                  # 路由接口功能测试
│   └── test_services.py                # 业务服务层测试用例
├── logs/                               # 日志文件存储目录（运行时生成）
├── data/                               # SQLite 数据库文件与本地缓存目录
│   └── weblink.db                      # 主数据库文件（首次启动生成）
├── .env.example                        # 环境变量配置模板
├── .gitignore                          # Git 版本控制忽略文件清单
├── requirements.txt                    # Python 依赖清单（生产环境）
├── requirements-dev.txt                # 开发环境额外依赖（测试、代码检查）
├── app.py                              # 应用启动入口脚本
├── config.py                           # 全局配置类定义（开发、测试、生产）
└── README.md                           # 项目说明文档（本文件）
```

## 贡献指南

我们欢迎并鼓励社区贡献。请按照以下流程提交您的改进或修复：

1. 查阅问题列表与路线图：访问 GitHub Issues 页面查看当前待处理的任务、功能请求与已知缺陷。对于较大的功能改动，建议先在 Issue 中阐述设计方案，与维护者达成共识后再着手实现。

2. 派生仓库并创建特性分支：将主仓库 Fork 至您的个人账户，然后克隆至本地。请基于 main 分支创建新的特性分支，分支命名遵循 feat/功能简述 或 fix/问题简述 的格式。

3. 编写代码并确保测试通过：所有新增功能必须包含对应的单元测试用例，确保测试覆盖率达到 80% 以上。运行 pytest 命令验证本地所有测试用例通过，且无新增警告。

4. 提交前进行代码风格检查：项目使用 flake8 与 black 进行代码风格统一。提交前请执行 black . 和 flake8 命令进行自动格式化与静态检查，确保代码风格符合 PEP 8 规范。

5. 发起合并请求并描述变更：推送分支至您的远程仓库，随后向主仓库的 main 分支发起 Pull Request。请在 PR 描述中清晰说明变更目的、实现方式以及测试结果，关联相关的 Issue 编号。

## 常见问题

Q：WebLink Hub 是否支持对 .doc 文件的内容进行全文搜索？

A：目前版本仅支持基于元数据（标题、来源域名、标签、收录时间）的检索，不直接解析 .doc 文件内部的文本内容。若需要全文搜索能力，建议结合第三方全文检索引擎（如 Elasticsearch）对下载后的文档内容进行索引，WebLink Hub 可提供链接管理作为上游数据源。后续版本将考虑集成轻量级全文搜索插件。

Q：系统是否具备高可用部署方案？如何应对大量并发访问？

A：WebLink Hub 定位为轻量级工具，默认使用 SQLite 数据库，适用于单机或小规模团队场景。若需应对更高并发，可配置外部 PostgreSQL 数据库替代 SQLite，并使用 Gunicorn 或多进程模式启动应用服务。静态资源建议通过 Nginx 反向代理提供缓存加速，数据库连接池参数可在 config.py 中调整。

Q：如何迁移已录入的资源数据到另一台服务器？

A：迁移过程包含两个部分。其一是数据库文件（data/weblink.db）直接拷贝至目标服务器的相同目录下；其二是环境配置文件（.env）中的密钥与数据库连接参数需同步更新。若使用外部数据库，则执行 pg_dump 或 mysqldump 导出后导入目标库。迁移完成后，建议执行 scripts/check_links.py 全量校验已迁移链接的有效性。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

# MobileDoc Link Aggregator

MobileDoc Link Aggregator 是一个面向移动端文档资源的高效外链汇总与导航系统，专为需要批量检索、分类管理和快速访问海量 .doc 格式技术资料、行业报告及内部文档的研发团队、数据分析师与技术研究员设计。该项目通过结构化索引将分散于多个移动子域名的文档链接统一收归，提供基于路径规则的自动化分类、元数据提取与可编程查询接口，从而解决文档散落、链接失效、检索效率低下等常见痛点。

本项目定位为技术资源中间层，不直接存储文档实体，而是构建一个轻量级、可扩展的链接治理框架。适用于企业内部知识库镜像、公开文档镜像站点的补充索引，以及学术或工业界大规模文档语料的入口管理。通过约定式路径解析与批量导入机制，可将数千条文档链接在数秒内完成标准化入库，并对外提供稳定的只读访问视图。

## 功能概览

批量文档链接导入与自动去重：支持从纯文本列表、CSV 或直接通过标准输入导入大量 .doc 文档链接，系统自动识别域名、路径结构并剔除重复条目，保障索引纯净度。

多维度链接分类与标签生成：依据 URL 中的二级域名及 Article 目录后的数字特征，自动生成分类标签（如来源站点、文档长度区间、ID 哈希分组），便于后续按业务维度筛选。

全文元数据模拟提取：对每个链接执行轻量级 HEAD 请求（可配置超时与重试），记录响应状态、Content-Length 与 Last-Modified 头信息，用于判断链接有效性及文档更新时间。

可编程 RESTful 查询接口：提供基于 HTTP 的 JSON API，支持按域名、文档 ID 范围、状态码等条件组合查询，结果分页返回，便于与其他数据看板或自动化脚本集成。

链接健康度定时巡检：内置调度器，可每日或每周自动重检所有已收录链接的可用性，输出异常报告，支持通过 Webhook 发送告警。

静态导航面板生成：支持一键生成纯 HTML 格式的文档目录页，按域名分组展示所有链接，适配移动端浏览，适合作为内部入口页面部署至任意静态托管服务。

导入导出兼容多种格式：除纯文本外，支持导入/导出为 JSON Lines、YAML 及 Markdown 列表，方便与其他文档管理工具（如 Docusaurus、VuePress）进行数据交换。

## 应用场景

企业内部分散文档的统一检索入口：某科技公司拥有数十个业务系统，其生成的月度运营报告、技术白皮书分散存储于不同移动子域名下。运维团队通过 MobileDoc Link Aggregator 每日自动抓取新生成的 .doc 链接，建立统一索引，员工只需查询该聚合平台即可定位所需文档，无需记忆多个域名。

学术研究中的大规模文档语料筛选：自然语言处理研究团队需要从公开网络采集特定领域的 .doc 格式论文摘要或技术标准。使用本项目导入数千条候选链接后，可依据域名来源快速过滤出高价值站点，再结合元数据信息筛选出近期更新的文档，大幅降低人工筛选成本。

文档镜像站点的链接完整性保障：某开源镜像站维护者将本项目作为辅助工具，定期对镜像站中引用的外部 .doc 链接进行健康度扫描。一旦发现链接失效或状态异常，系统自动生成待修复清单，帮助维护者及时更新或替换失效引用，提升镜像站质量。

移动端离线阅读前的批量预检：内容分发团队需要将一批 .doc 文档转换为离线包供前线人员使用。在转换前，通过本项目的批量 HEAD 请求功能快速剔除无法访问或文件大小为 0 的无效链接，避免无效资源进入打包流程，节省存储与传输成本。

## 快速开始

以下步骤帮助您在五分钟内完成项目的克隆、安装与初次运行。

```bash
# 1. 克隆代码仓库
git clone https://github.com/your-org/mobiledoc-link-aggregator.git
cd mobiledoc-link-aggregator

# 2. 安装依赖（使用 pip 和虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 3. 导入示例链接列表并启动服务
python cli.py import --input data/sample_links.txt
python cli.py serve --host 0.0.0.0 --port 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 或更高 | 核心运行环境，建议使用 3.10+ 以获得性能优化 |
| pip | 22.0 或更高 | 用于安装项目依赖包及后续更新 |
| requests | 2.28.0 或更高 | 发送 HTTP HEAD/GET 请求以检查链接状态 |
| click | 8.1.0 或更高 | 提供命令行交互界面，用于导入、查询及服务管理 |
| Flask | 2.2.0 或更高 | 提供 RESTful API 服务及静态导航页生成 |
| pytest | 7.0 或更高 | 仅开发与测试环境需要，用于执行单元测试与集成测试 |
| SQLite | 系统自带 | 默认元数据存储引擎，无需额外安装，支持并发读取 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何导入链接列表、如何启动查询服务、如何生成静态导航页 |
| 运维指南 | docs/ops-guide.md | 如何配置定时巡检、如何调整 HEAD 请求超时参数、如何备份索引数据库 |
| API 参考 | docs/api-reference.md | 有哪些可用查询参数、返回数据结构如何、如何进行分页与排序 |
| 开发者文档 | docs/developer-guide.md | 项目目录结构说明、如何扩展新的分类器、如何编写自定义导入插件 |

## 资源列表

- h5.mobile.nwbbyt.cn/Article/9902372.doc
- h5.mobile.jnjpgf.cn/Article/3893228.doc
- h5.mobile.hcbezg.cn/Article/7290.doc
- h5.mobile.fuvxie.cn/Article/95471.doc
- h5.mobile.cvsifc.cn/Article/5895565.doc
- h5.mobile.cmcvrr.cn/Article/277204.doc
- h5.mobile.hcbezg.cn/Article/0613624.doc
- h5.mobile.puhvjy.cn/Article/34608.doc
- h5.mobile.nwbbyt.cn/Article/7890230.doc
- h5.mobile.nwbbyt.cn/Article/3874.doc
- h5.mobile.puhvjy.cn/Article/6708099.doc
- h5.mobile.cmcvrr.cn/Article/4025502.doc
- h5.mobile.hcbezg.cn/Article/210194.doc
- h5.mobile.cmcvrr.cn/Article/1599.doc
- h5.mobile.cvsifc.cn/Article/83983.doc
- h5.mobile.puhvjy.cn/Article/3530056.doc
- h5.mobile.puhvjy.cn/Article/789724.doc
- h5.mobile.jnjpgf.cn/Article/989844.doc
- h5.mobile.fuvxie.cn/Article/027420.doc
- h5.mobile.cvsifc.cn/Article/60808.doc
- h5.mobile.fuvxie.cn/Article/458759.doc
- h5.mobile.jnjpgf.cn/Article/8838.doc
- h5.mobile.nzfnve.cn/Article/7136.doc
- h5.mobile.puhvjy.cn/Article/47006.doc
- h5.mobile.cvsifc.cn/Article/8534.doc
- h5.mobile.jnjpgf.cn/Article/7079124.doc
- h5.mobile.puhvjy.cn/Article/5701306.doc
- h5.mobile.puhvjy.cn/Article/2785.doc
- h5.mobile.nzfnve.cn/Article/091402.doc
- h5.mobile.puhvjy.cn/Article/8926035.doc
- h5.mobile.jnjpgf.cn/Article/067165.doc
- h5.mobile.hcbezg.cn/Article/4906.doc
- h5.mobile.cvsifc.cn/Article/202180.doc
- h5.mobile.hcbezg.cn/Article/3043148.doc
- h5.mobile.jnjpgf.cn/Article/74781.doc
- h5.mobile.nzfnve.cn/Article/79127.doc
- h5.mobile.cmcvrr.cn/Article/916043.doc
- h5.mobile.nzfnve.cn/Article/67297.doc
- h5.mobile.fuvxie.cn/Article/23868.doc
- h5.mobile.hcbezg.cn/Article/0239.doc
- h5.mobile.cvsifc.cn/Article/6713.doc
- h5.mobile.nwbbyt.cn/Article/1727695.doc
- h5.mobile.cmcvrr.cn/Article/88151.doc
- h5.mobile.cmcvrr.cn/Article/791915.doc
- h5.mobile.hcbezg.cn/Article/9669385.doc
- h5.mobile.cmcvrr.cn/Article/4716.doc
- h5.mobile.hcbezg.cn/Article/2800282.doc
- h5.mobile.puhvjy.cn/Article/8340602.doc
- h5.mobile.nzfnve.cn/Article/7377.doc
- h5.mobile.nzfnve.cn/Article/38798.doc
- h5.mobile.jnjpgf.cn/Article/415407.doc
- h5.mobile.fuvxie.cn/Article/4201518.doc
- h5.mobile.fuvxie.cn/Article/87241.doc
- h5.mobile.puhvjy.cn/Article/787268.doc
- h5.mobile.puhvjy.cn/Article/25898.doc
- h5.mobile.cmcvrr.cn/Article/4358240.doc
- h5.mobile.nwbbyt.cn/Article/1941.doc
- h5.mobile.nzfnve.cn/Article/9467.doc
- h5.mobile.cmcvrr.cn/Article/1582743.doc
- h5.mobile.hcbezg.cn/Article/250260.doc
- h5.mobile.cmcvrr.cn/Article/6413.doc
- h5.mobile.hcbezg.cn/Article/3545108.doc
- h5.mobile.puhvjy.cn/Article/855958.doc
- h5.mobile.fuvxie.cn/Article/8264.doc
- h5.mobile.nzfnve.cn/Article/0154606.doc
- h5.mobile.nwbbyt.cn/Article/8303.doc
- h5.mobile.cvsifc.cn/Article/0788.doc
- h5.mobile.hcbezg.cn/Article/424045.doc
- h5.mobile.jnjpgf.cn/Article/8103.doc
- h5.mobile.jnjpgf.cn/Article/1001718.doc
- h5.mobile.nwbbyt.cn/Article/63063.doc
- h5.mobile.hcbezg.cn/Article/2667496.doc
- h5.mobile.nwbbyt.cn/Article/33564.doc
- h5.mobile.cvsifc.cn/Article/3004116.doc
- h5.mobile.nzfnve.cn/Article/359172.doc
- h5.mobile.nwbbyt.cn/Article/1694.doc
- h5.mobile.nzfnve.cn/Article/3336620.doc
- h5.mobile.puhvjy.cn/Article/4680.doc
- h5.mobile.nzfnve.cn/Article/85339.doc
- h5.mobile.fuvxie.cn/Article/398256.doc
- h5.mobile.cmcvrr.cn/Article/0878.doc
- h5.mobile.cvsifc.cn/Article/072704.doc
- h5.mobile.cvsifc.cn/Article/287938.doc
- h5.mobile.nzfnve.cn/Article/9106037.doc
- h5.mobile.jnjpgf.cn/Article/84042.doc
- h5.mobile.fuvxie.cn/Article/695823.doc
- h5.mobile.cmcvrr.cn/Article/220411.doc
- h5.mobile.puhvjy.cn/Article/1010544.doc
- h5.mobile.jnjpgf.cn/Article/0130.doc
- h5.mobile.puhvjy.cn/Article/0841959.doc
- h5.mobile.puhvjy.cn/Article/9303036.doc
- h5.mobile.jnjpgf.cn/Article/34223.doc
- h5.mobile.nzfnve.cn/Article/36380.doc
- h5.mobile.jnjpgf.cn/Article/14167.doc
- h5.mobile.cmcvrr.cn/Article/340255.doc
- h5.mobile.nzfnve.cn/Article/5455798.doc
- h5.mobile.cvsifc.cn/Article/0065.doc
- h5.mobile.nzfnve.cn/Article/9523.doc
- h5.mobile.cmcvrr.cn/Article/4411.doc
- h5.mobile.nwbbyt.cn/Article/9567195.doc
- h5.mobile.hcbezg.cn/Article/5629160.doc
- h5.mobile.jnjpgf.cn/Article/654129.doc
- h5.mobile.cmcvrr.cn/Article/3050.doc
- h5.mobile.cmcvrr.cn/Article/7525327.doc
- h5.mobile.nzfnve.cn/Article/1808893.doc
- h5.mobile.fuvxie.cn/Article/2999940.doc
- h5.mobile.puhvjy.cn/Article/085893.doc
- h5.mobile.fuvxie.cn/Article/957218.doc
- h5.mobile.puhvjy.cn/Article/4862.doc
- h5.mobile.nzfnve.cn/Article/13563.doc
- h5.mobile.jnjpgf.cn/Article/4685676.doc
- h5.mobile.nzfnve.cn/Article/968165.doc
- h5.mobile.cmcvrr.cn/Article/487106.doc
- h5.mobile.nzfnve.cn/Article/07403.doc
- h5.mobile.cmcvrr.cn/Article/86394.doc
- h5.mobile.puhvjy.cn/Article/0406536.doc
- h5.mobile.fuvxie.cn/Article/194028.doc
- h5.mobile.hcbezg.cn/Article/397938.doc
- h5.mobile.puhvjy.cn/Article/1478906.doc
- h5.mobile.nwbbyt.cn/Article/7960262.doc
- h5.mobile.puhvjy.cn/Article/2334.doc
- h5.mobile.hcbezg.cn/Article/4913.doc
- h5.mobile.cmcvrr.cn/Article/0872.doc
- h5.mobile.puhvjy.cn/Article/5274710.doc
- h5.mobile.nzfnve.cn/Article/63454.doc
- h5.mobile.cvsifc.cn/Article/5749242.doc
- h5.mobile.jnjpgf.cn/Article/4580131.doc
- h5.mobile.fuvxie.cn/Article/3358.doc
- h5.mobile.fuvxie.cn/Article/86599.doc
- h5.mobile.nzfnve.cn/Article/6905.doc
- h5.mobile.nwbbyt.cn/Article/00580.doc
- h5.mobile.cmcvrr.cn/Article/039532.doc
- h5.mobile.nwbbyt.cn/Article/781969.doc
- h5.mobile.nwbbyt.cn/Article/1091.doc
- h5.mobile.jnjpgf.cn/Article/032108.doc
- h5.mobile.fuvxie.cn/Article/7423600.doc
- h5.mobile.jnjpgf.cn/Article/84901.doc
- h5.mobile.cmcvrr.cn/Article/993498.doc
- h5.mobile.cvsifc.cn/Article/912013.doc
- h5.mobile.cmcvrr.cn/Article/2056182.doc
- h5.mobile.cvsifc.cn/Article/153899.doc
- h5.mobile.jnjpgf.cn/Article/8999362.doc
- h5.mobile.nzfnve.cn/Article/6137.doc
- h5.mobile.fuvxie.cn/Article/97263.doc
- h5.mobile.fuvxie.cn/Article/5481478.doc
- h5.mobile.puhvjy.cn/Article/871217.doc
- h5.mobile.nwbbyt.cn/Article/1392367.doc
- h5.mobile.jnjpgf.cn/Article/870245.doc
- h5.mobile.puhvjy.cn/Article/539953.doc
- h5.mobile.cmcvrr.cn/Article/3133.doc
- h5.mobile.nzfnve.cn/Article/45063.doc
- h5.mobile.hcbezg.cn/Article/885602.doc
- h5.mobile.nwbbyt.cn/Article/64114.doc
- h5.mobile.jnjpgf.cn/Article/356709.doc
- h5.mobile.jnjpgf.cn/Article/9662.doc
- h5.mobile.cvsifc.cn/Article/5225.doc
- h5.mobile.cvsifc.cn/Article/1260.doc
- h5.mobile.cvsifc.cn/Article/1215303.doc
- h5.mobile.puhvjy.cn/Article/88722.doc
- h5.mobile.nzfnve.cn/Article/818740.doc
- h5.mobile.jnjpgf.cn/Article/981736.doc
- h5.mobile.nzfnve.cn/Article/752011.doc
- h5.mobile.cvsifc.cn/Article/7077.doc
- h5.mobile.nzfnve.cn/Article/94777.doc
- h5.mobile.nwbbyt.cn/Article/6404295.doc
- h5.mobile.fuvxie.cn/Article/87570.doc
- h5.mobile.fuvxie.cn/Article/4942865.doc
- h5.mobile.fuvxie.cn/Article/806101.doc
- h5.mobile.hcbezg.cn/Article/25325.doc
- h5.mobile.cmcvrr.cn/Article/7798.doc
- h5.mobile.hcbezg.cn/Article/2186677.doc
- h5.mobile.fuvxie.cn/Article/33728.doc
- h5.mobile.jnjpgf.cn/Article/77098.doc
- h5.mobile.jnjpgf.cn/Article/2933451.doc
- h5.mobile.fuvxie.cn/Article/3028456.doc
- h5.mobile.cvsifc.cn/Article/2423196.doc
- h5.mobile.fuvxie.cn/Article/7274811.doc
- h5.mobile.fuvxie.cn/Article/83936.doc
- h5.mobile.nzfnve.cn/Article/48103.doc
- h5.mobile.nwbbyt.cn/Article/85161.doc
- h5.mobile.fuvxie.cn/Article/15323.doc
- h5.mobile.jnjpgf.cn/Article/3691775.doc
- h5.mobile.cmcvrr.cn/Article/3188.doc
- h5.mobile.cmcvrr.cn/Article/1236423.doc
- h5.mobile.puhvjy.cn/Article/71760.doc
- h5.mobile.hcbezg.cn/Article/52720.doc
- h5.mobile.cmcvrr.cn/Article/730244.doc
- h5.mobile.puhvjy.cn/Article/056564.doc
- h5.mobile.puhvjy.cn/Article/0075048.doc
- h5.mobile.cvsifc.cn/Article/96418.doc
- h5.mobile.cvsifc.cn/Article/70073.doc
- h5.mobile.fuvxie.cn/Article/11031.doc
- h5.mobile.cmcvrr.cn/Article/3643881.doc
- h5.mobile.puhvjy.cn/Article/906127.doc
- h5.mobile.cvsifc.cn/Article/8039932.doc
- h5.mobile.puhvjy.cn/Article/0317372.doc
- h5.mobile.hcbezg.cn/Article/23154.doc
- h5.mobile.jnjpgf.cn/Article/646352.doc
- h5.mobile.cvsifc.cn/Article/409083.doc
- h5.mobile.nzfnve.cn/Article/456803.doc
- h5.mobile.nwbbyt.cn/Article/54266.doc
- h5.mobile.fuvxie.cn/Article/2498.doc
- h5.mobile.nwbbyt.cn/Article/71954.doc
- h5.mobile.hcbezg.cn/Article/243435.doc
- h5.mobile.nwbbyt.cn/Article/55690.doc
- h5.mobile.hcbezg.cn/Article/3650521.doc
- h5.mobile.jnjpgf.cn/Article/95194.doc
- h5.mobile.cvsifc.cn/Article/2366.doc
- h5.mobile.puhvjy.cn/Article/73243.doc
- h5.mobile.fuvxie.cn/Article/041067.doc
- h5.mobile.puhvjy.cn/Article/6361902.doc
- h5.mobile.nwbbyt.cn/Article/6955996.doc
- h5.mobile.nwbbyt.cn/Article/560298.doc
- h5.mobile.nzfnve.cn/Article/8755560.doc
- h5.mobile.hcbezg.cn/Article/71241.doc
- h5.mobile.nzfnve.cn/Article/8584.doc
- h5.mobile.cvsifc.cn/Article/9415009.doc
- h5.mobile.fuvxie.cn/Article/0860.doc
- h5.mobile.jnjpgf.cn/Article/646817.doc
- h5.mobile.jnjpgf.cn/Article/11780.doc
- h5.mobile.cmcvrr.cn/Article/617596.doc
- h5.mobile.fuvxie.cn/Article/3777.doc
- h5.mobile.jnjpgf.cn/Article/5962.doc
- h5.mobile.hcbezg.cn/Article/820373.doc
- h5.mobile.jnjpgf.cn/Article/41640.doc
- h5.mobile.puhvjy.cn/Article/47624.doc
- h5.mobile.fuvxie.cn/Article/7868044.doc
- h5.mobile.fuvxie.cn/Article/3477.doc
- h5.mobile.cmcvrr.cn/Article/59764.doc
- h5.mobile.jnjpgf.cn/Article/0936.doc
- h5.mobile.puhvjy.cn/Article/2817682.doc
- h5.mobile.cvsifc.cn/Article/82047.doc
- h5.mobile.cvsifc.cn/Article/0862870.doc
- h5.mobile.puhvjy.cn/Article/8197546.doc
- h5.mobile.hcbezg.cn/Article/7897896.doc
- h5.mobile.cvsifc.cn/Article/376355.doc
- h5.mobile.nwbbyt.cn/Article/72408.doc
- h5.mobile.puhvjy.cn/Article/28059.doc
- h5.mobile.nzfnve.cn/Article/8853.doc
- h5.mobile.nzfnve.cn/Article/9109.doc
- h5.mobile.nzfnve.cn/Article/0404.doc
- h5.mobile.cvsifc.cn/Article/6224343.doc
- h5.mobile.hcbezg.cn/Article/599645.doc
- h5.mobile.jnjpgf.cn/Article/156708.doc
- h5.mobile.cvsifc.cn/Article/8622.doc
- h5.mobile.cvsifc.cn/Article/1754052.doc
- h5.mobile.hcbezg.cn/Article/78135.doc
- h5.mobile.cvsifc.cn/Article/18084.doc
- h5.mobile.puhvjy.cn/Article/5542.doc
- h5.mobile.nzfnve.cn/Article/76656.doc

## 项目结构

```
mobiledoc-link-aggregator/
├── cli.py                      # 命令行入口，整合导入、查询与服务启动
├── requirements.txt            # Python 依赖声明
├── README.md                   # 项目介绍与快速入门
├── .gitignore                  # 版本控制忽略规则
│
├── aggregator/                 # 核心业务逻辑包
│   ├── __init__.py
│   ├── importer.py             # 链接导入、去重、分类器（按域名与ID区间）
│   ├── checker.py              # HEAD 请求健康检查、超时控制与重试策略
│   ├── querier.py              # SQLite 查询构造器，支持多条件组合与分页
│   ├── exporter.py             # 导出为 JSON/YAML/HTML 静态面板
│   └── scheduler.py            # 基于 APScheduler 的定时巡检任务
│
├── server/                     # Web 服务模块
│   ├── __init__.py
│   ├── app.py                  # Flask 应用工厂，注册路由与错误处理器
│   ├── api_v1.py               # RESTful API 端点实现（/api/v1/links, /api/v1/status）
│   └── templates/              # 静态导航页 Jinja2 模板
│       └── index.html          # 按域名分组的文档列表展示页
│
├── storage/                    # 数据持久化层
│   ├── __init__.py
│   ├── db.py                   # SQLite 连接池、表结构初始化与迁移
│   └── migrations/             # 版本化 DDL 变更脚本
│       └── v1_initial.sql      # 初始建表语句（links 表、check_log 表）
│
├── tests/                      # 测试套件
│   ├── test_importer.py        # 导入逻辑单元测试（含边界条件）
│   ├── test_checker.py         # 健康检查模拟响应测试
│   └── test_api.py             # Flask 测试客户端接口验证
│
└── data/                       # 用户数据挂载目录（非版本控制）
    ├── sample_links.txt        # 示例链接列表
    └── aggregator.db           # 默认 SQLite 数据库文件（首次运行时生成）
```

## 贡献指南

提交 Issue 报告缺陷或功能请求：请使用 GitHub Issue 模板，明确描述运行环境（Python 版本、操作系统）、复现步骤及预期行为。对于功能请求，请说明使用场景及期望的输入输出示例。

创建分支并遵循代码规范：从 main 分支签出新的 feature/ 或 fix/ 前缀分支。代码需通过 flake8 与 mypy 静态检查，所有公共函数必须包含 docstring 说明参数、返回值及可能抛出的异常。

编写或更新单元测试：新增或修改核心逻辑（importer、checker、querier）时，需在 tests/ 目录下补充对应的测试用例，确保覆盖率不低于 85%。使用 pytest 执行全部测试。

更新文档与示例：若改动影响用户可见行为（如 CLI 参数变更、API 字段调整），需同步更新 docs/ 下的对应手册，并确保 README 中的快速开始示例仍可正常运行。

提交 Pull Request 并等待审核：推送分支后，在 GitHub 上创建 Pull Request，填写变更摘要、测试结果及影响范围。至少需一名维护者 Approve 后方可合并。

## 常见问题

启动服务时报错 "Port 8080 already in use" 如何解决？

该错误表示 8080 端口已被其他进程占用。可通过 --port 参数指定其他空闲端口，例如 python cli.py serve --port 9090。若需释放原端口，可使用 lsof -i :8080 查找进程 ID 后执行 kill 命令（Linux/macOS）或使用 netstat -ano | findstr :8080 配合 taskkill（Windows）。

导入链接时提示 "duplicate entry" 但实际并未重复，是什么原因？

系统默认依据完整 URL 字符串进行去重，并额外对 Article/ 后的数字 ID 建立唯一索引。若提示重复，可能是由于不同链接指向了相同的文档 ID（如 h5.mobile.a.cn/Article/123.doc 与 h5.mobile.b.cn/Article/123.doc 被视为不同条目，但若数字 ID 完全一致且位于同一域名下则会触发）。可通过 cli.py import --skip-duplicates 跳过已存在条目，或使用 --update-metadata 强制刷新元数据。

如何将当前索引数据迁移至其他数据库（如 PostgreSQL）？

项目默认使用 SQLite，但提供了抽象存储接口。您可参考 storage/db.py 中的实现，编写适配 PostgreSQL/MySQL 的驱动类，并在 app.py 中替换 get_db_connection 工厂方法。官方暂未提供原生支持，欢迎贡献适配插件。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

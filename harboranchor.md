# DocLink Centralized Resource Aggregator

DocLink is a production-grade distributed document indexing and external resource aggregation system designed for technical teams, content curators, and enterprise knowledge management departments. The platform solves the fundamental problem of scattered, unmanaged document links across multiple mobile-optimized subdomains by providing a unified cataloging interface, automated health checking, and structured metadata extraction for .doc resources. Target users include system administrators managing large-scale document repositories, DevOps engineers integrating external asset pipelines, and research teams requiring reproducible link collection workflows.

The project implements a lightweight resource discovery layer that normalizes heterogeneous URL patterns from multiple origin domains, extracts document identifiers, and maintains an immutable audit trail of all indexed resources. Unlike generic bookmarking tools, DocLink enforces strict URL integrity, provides batch validation, and supports programmatic querying through both CLI and RESTful interfaces. The current release indexes the 108th batch of an ongoing 160-batch ingestion pipeline, covering 250 active document links distributed across seven content delivery subdomains.

## 功能概览

- **多源统一索引引擎** 支持从多个独立移动子域名并行采集资源链接，自动识别域名分组并生成归一化存储键值。

- **文档标识符提取与校验** 从每个 .doc 资源路径中解析数字型文档编号，执行长度校验、重复检测和格式合规性检查。

- **批量导入与增量更新** 支持通过 CSV 或纯文本列表批量注入资源 URL，提供增量追加和全量替换两种工作模式。

- **资源可用性探针** 集成异步 HTTP 健康检查中间件，可配置超时与重试策略，自动标记不可达资源并生成告警日志。

- **结构化元数据存储** 每条资源记录包含原始 URL、规范化域名、文档编号、首次发现时间、最后校验状态和批次标签。

- **命令行交互工具** 提供 doclink-cli 命令完成资源列表导出、查询过滤、统计分析和脏数据清理操作。

- **RESTful 查询接口** 暴露 /api/v1/resources 端点支持按域名、批次、文档编号范围进行精确检索和分页展示。

- **可插拔输出格式化器** 支持 JSON、YAML 和 Markdown 表格三种输出格式，满足文档生成与系统集成需求。

## 应用场景

**企业知识库资源归集** 大型企业的技术文档分散在多个部门级移动站点，管理员通过 DocLink 定期汇总 .doc 资源链接，生成统一资源目录供内部搜索系统消费，避免重复采集和链接失效问题。

**开源项目外链资产管理** 开源社区维护者使用 DocLink 管理项目中引用的外部文档资源，通过批量导入功能一次性录入数百条链接，利用健康检查探针定期验证可用性，确保文档导航菜单始终指向有效内容。

**数据迁移前的链接盘点** 在将文档系统从旧平台迁移至新平台前，运维团队借助 DocLink 导出所有资源清单，对比迁移前后链接映射关系，生成差异报告以验证迁移完整性。

**学术研究参考文献批处理** 研究人员收集大量网络文档链接作为参考文献素材，利用 DocLink 的批量导入和元数据提取功能快速生成结构化的资源清单，便于后续引用格式转换和去重处理。

## 快速开始

以下步骤演示在 Linux/macOS 环境下完成 DocLink 的克隆、安装和首次运行。

```bash
git clone https://github.com/your-org/doclink-aggregator.git
cd doclink-aggregator

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 执行批量导入（以 resources.txt 为输入文件）
python doclink/cli.py import --input resources.txt --batch 108 --output ./index.db

# 运行健康检查
python doclink/cli.py health --db ./index.db --timeout 5 --retries 2

# 导出资源列表为 Markdown 格式
python doclink/cli.py export --db ./index.db --format markdown --batch 108 > exported_links.md
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行时环境，建议使用 3.10 LTS |
| SQLite | 3.31 及以上 | 本地元数据存储引擎，支持 JSON1 扩展 |
| requests | 2.25.0 及以上 | HTTP 健康检查与资源探测客户端库 |
| click | 8.0.0 及以上 | 命令行交互框架，用于 CLI 子命令解析 |
| pytest | 7.0.0 及以上 | 单元测试与集成测试运行器（仅开发依赖） |
| black | 22.0.0 及以上 | 代码格式化工具（仅开发依赖） |
| mypy | 1.0.0 及以上 | 静态类型检查工具（仅开发依赖） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何安装、配置、导入导出资源，以及 CLI 各子命令的详细用法 |
| 运维指南 | docs/operations.md | 如何部署健康检查定时任务、备份索引数据库、监控资源可用性趋势 |
| 开发者文档 | docs/developer.md | 如何扩展新的资源解析器、自定义输出格式器、编写单元测试 |
| API 参考 | docs/api-reference.md | RESTful 接口的请求/响应规范、认证方式、分页参数和错误码定义 |

## 资源列表

- h5.mobile.nwbbyt.cn/Article/9768776.doc
- h5.mobile.jnjpgf.cn/Article/20396.doc
- h5.mobile.cmcvrr.cn/Article/689779.doc
- h5.mobile.fuvxie.cn/Article/845255.doc
- h5.mobile.puhvjy.cn/Article/75029.doc
- h5.mobile.jnjpgf.cn/Article/6439899.doc
- h5.mobile.nwbbyt.cn/Article/2294.doc
- h5.mobile.cvsifc.cn/Article/683148.doc
- h5.mobile.nwbbyt.cn/Article/4833832.doc
- h5.mobile.puhvjy.cn/Article/86355.doc
- h5.mobile.cvsifc.cn/Article/980345.doc
- h5.mobile.puhvjy.cn/Article/72607.doc
- h5.mobile.jnjpgf.cn/Article/2836.doc
- h5.mobile.puhvjy.cn/Article/34303.doc
- h5.mobile.puhvjy.cn/Article/96203.doc
- h5.mobile.jnjpgf.cn/Article/475253.doc
- h5.mobile.fuvxie.cn/Article/347720.doc
- h5.mobile.jnjpgf.cn/Article/25904.doc
- h5.mobile.puhvjy.cn/Article/65193.doc
- h5.mobile.puhvjy.cn/Article/8734938.doc
- h5.mobile.hcbezg.cn/Article/4462504.doc
- h5.mobile.jnjpgf.cn/Article/6915990.doc
- h5.mobile.puhvjy.cn/Article/64230.doc
- h5.mobile.nzfnve.cn/Article/8793025.doc
- h5.mobile.nzfnve.cn/Article/45915.doc
- h5.mobile.jnjpgf.cn/Article/192636.doc
- h5.mobile.nwbbyt.cn/Article/580675.doc
- h5.mobile.jnjpgf.cn/Article/6072524.doc
- h5.mobile.cvsifc.cn/Article/01396.doc
- h5.mobile.fuvxie.cn/Article/16152.doc
- h5.mobile.cmcvrr.cn/Article/5031.doc
- h5.mobile.puhvjy.cn/Article/739093.doc
- h5.mobile.nwbbyt.cn/Article/387536.doc
- h5.mobile.hcbezg.cn/Article/862808.doc
- h5.mobile.cmcvrr.cn/Article/6680.doc
- h5.mobile.puhvjy.cn/Article/1372321.doc
- h5.mobile.hcbezg.cn/Article/4261540.doc
- h5.mobile.hcbezg.cn/Article/24715.doc
- h5.mobile.jnjpgf.cn/Article/1736244.doc
- h5.mobile.cvsifc.cn/Article/65266.doc
- h5.mobile.nzfnve.cn/Article/3190.doc
- h5.mobile.cvsifc.cn/Article/3225482.doc
- h5.mobile.cmcvrr.cn/Article/6130.doc
- h5.mobile.puhvjy.cn/Article/3839637.doc
- h5.mobile.nwbbyt.cn/Article/0392.doc
- h5.mobile.jnjpgf.cn/Article/2941877.doc
- h5.mobile.fuvxie.cn/Article/03722.doc
- h5.mobile.fuvxie.cn/Article/7820.doc
- h5.mobile.cmcvrr.cn/Article/5699.doc
- h5.mobile.cmcvrr.cn/Article/3160166.doc
- h5.mobile.cvsifc.cn/Article/146545.doc
- h5.mobile.puhvjy.cn/Article/8527294.doc
- h5.mobile.cvsifc.cn/Article/4247187.doc
- h5.mobile.jnjpgf.cn/Article/20539.doc
- h5.mobile.jnjpgf.cn/Article/62750.doc
- h5.mobile.nwbbyt.cn/Article/8976.doc
- h5.mobile.jnjpgf.cn/Article/8376.doc
- h5.mobile.hcbezg.cn/Article/8561.doc
- h5.mobile.fuvxie.cn/Article/4192980.doc
- h5.mobile.fuvxie.cn/Article/36174.doc
- h5.mobile.cmcvrr.cn/Article/6640.doc
- h5.mobile.hcbezg.cn/Article/247824.doc
- h5.mobile.nzfnve.cn/Article/2619341.doc
- h5.mobile.puhvjy.cn/Article/2895012.doc
- h5.mobile.puhvjy.cn/Article/38717.doc
- h5.mobile.jnjpgf.cn/Article/3051348.doc
- h5.mobile.cvsifc.cn/Article/08357.doc
- h5.mobile.cmcvrr.cn/Article/9703.doc
- h5.mobile.hcbezg.cn/Article/43676.doc
- h5.mobile.nzfnve.cn/Article/7060.doc
- h5.mobile.cvsifc.cn/Article/5145.doc
- h5.mobile.cmcvrr.cn/Article/88861.doc
- h5.mobile.cmcvrr.cn/Article/1039.doc
- h5.mobile.puhvjy.cn/Article/53139.doc
- h5.mobile.puhvjy.cn/Article/5355711.doc
- h5.mobile.jnjpgf.cn/Article/11711.doc
- h5.mobile.jnjpgf.cn/Article/3783149.doc
- h5.mobile.nzfnve.cn/Article/229462.doc
- h5.mobile.cmcvrr.cn/Article/11588.doc
- h5.mobile.fuvxie.cn/Article/6234340.doc
- h5.mobile.nwbbyt.cn/Article/663366.doc
- h5.mobile.nzfnve.cn/Article/6508.doc
- h5.mobile.cmcvrr.cn/Article/105881.doc
- h5.mobile.puhvjy.cn/Article/44043.doc
- h5.mobile.hcbezg.cn/Article/94955.doc
- h5.mobile.jnjpgf.cn/Article/1353905.doc
- h5.mobile.cmcvrr.cn/Article/87934.doc
- h5.mobile.nwbbyt.cn/Article/08288.doc
- h5.mobile.nwbbyt.cn/Article/15651.doc
- h5.mobile.puhvjy.cn/Article/1961.doc
- h5.mobile.puhvjy.cn/Article/28509.doc
- h5.mobile.cmcvrr.cn/Article/32606.doc
- h5.mobile.nwbbyt.cn/Article/247634.doc
- h5.mobile.nzfnve.cn/Article/1181.doc
- h5.mobile.hcbezg.cn/Article/38087.doc
- h5.mobile.cvsifc.cn/Article/8329949.doc
- h5.mobile.jnjpgf.cn/Article/38141.doc
- h5.mobile.cvsifc.cn/Article/0835.doc
- h5.mobile.puhvjy.cn/Article/049167.doc
- h5.mobile.nwbbyt.cn/Article/208055.doc
- h5.mobile.puhvjy.cn/Article/43647.doc
- h5.mobile.cvsifc.cn/Article/66563.doc
- h5.mobile.cvsifc.cn/Article/99080.doc
- h5.mobile.puhvjy.cn/Article/3057123.doc
- h5.mobile.hcbezg.cn/Article/4344311.doc
- h5.mobile.cmcvrr.cn/Article/7085808.doc
- h5.mobile.jnjpgf.cn/Article/613682.doc
- h5.mobile.cmcvrr.cn/Article/11473.doc
- h5.mobile.cmcvrr.cn/Article/347258.doc
- h5.mobile.fuvxie.cn/Article/07592.doc
- h5.mobile.fuvxie.cn/Article/8012.doc
- h5.mobile.nzfnve.cn/Article/0061.doc
- h5.mobile.hcbezg.cn/Article/4405.doc
- h5.mobile.jnjpgf.cn/Article/9373265.doc
- h5.mobile.jnjpgf.cn/Article/1600.doc
- h5.mobile.hcbezg.cn/Article/3977108.doc
- h5.mobile.cvsifc.cn/Article/80761.doc
- h5.mobile.fuvxie.cn/Article/3664181.doc
- h5.mobile.nwbbyt.cn/Article/893564.doc
- h5.mobile.fuvxie.cn/Article/95992.doc
- h5.mobile.nwbbyt.cn/Article/93058.doc
- h5.mobile.jnjpgf.cn/Article/213674.doc
- h5.mobile.cvsifc.cn/Article/662947.doc
- h5.mobile.cvsifc.cn/Article/6841.doc
- h5.mobile.jnjpgf.cn/Article/826266.doc
- h5.mobile.puhvjy.cn/Article/780528.doc
- h5.mobile.nwbbyt.cn/Article/1786.doc
- h5.mobile.cmcvrr.cn/Article/253582.doc
- h5.mobile.hcbezg.cn/Article/7173797.doc
- h5.mobile.fuvxie.cn/Article/74353.doc
- h5.mobile.hcbezg.cn/Article/297881.doc
- h5.mobile.cmcvrr.cn/Article/6503517.doc
- h5.mobile.puhvjy.cn/Article/3893709.doc
- h5.mobile.fuvxie.cn/Article/5948.doc
- h5.mobile.fuvxie.cn/Article/1789182.doc
- h5.mobile.fuvxie.cn/Article/082384.doc
- h5.mobile.cvsifc.cn/Article/01862.doc
- h5.mobile.nwbbyt.cn/Article/3532.doc
- h5.mobile.nzfnve.cn/Article/2002.doc
- h5.mobile.nzfnve.cn/Article/3441307.doc
- h5.mobile.hcbezg.cn/Article/15795.doc
- h5.mobile.cmcvrr.cn/Article/5514.doc
- h5.mobile.cvsifc.cn/Article/8408.doc
- h5.mobile.nzfnve.cn/Article/6198304.doc
- h5.mobile.fuvxie.cn/Article/20817.doc
- h5.mobile.cmcvrr.cn/Article/5520.doc
- h5.mobile.nwbbyt.cn/Article/2542306.doc
- h5.mobile.jnjpgf.cn/Article/3442.doc
- h5.mobile.fuvxie.cn/Article/97398.doc
- h5.mobile.cmcvrr.cn/Article/931138.doc
- h5.mobile.cvsifc.cn/Article/45108.doc
- h5.mobile.hcbezg.cn/Article/77518.doc
- h5.mobile.nzfnve.cn/Article/630906.doc
- h5.mobile.nzfnve.cn/Article/76518.doc
- h5.mobile.cmcvrr.cn/Article/605273.doc
- h5.mobile.fuvxie.cn/Article/1657.doc
- h5.mobile.fuvxie.cn/Article/08719.doc
- h5.mobile.cmcvrr.cn/Article/1990410.doc
- h5.mobile.cvsifc.cn/Article/3589.doc
- h5.mobile.nzfnve.cn/Article/3574409.doc
- h5.mobile.nzfnve.cn/Article/0585.doc
- h5.mobile.jnjpgf.cn/Article/01983.doc
- h5.mobile.fuvxie.cn/Article/7725.doc
- h5.mobile.hcbezg.cn/Article/73090.doc
- h5.mobile.hcbezg.cn/Article/88210.doc
- h5.mobile.cmcvrr.cn/Article/6906115.doc
- h5.mobile.fuvxie.cn/Article/5764.doc
- h5.mobile.fuvxie.cn/Article/234802.doc
- h5.mobile.jnjpgf.cn/Article/62210.doc
- h5.mobile.nzfnve.cn/Article/705514.doc
- h5.mobile.nzfnve.cn/Article/8695961.doc
- h5.mobile.nzfnve.cn/Article/2311936.doc
- h5.mobile.nzfnve.cn/Article/279902.doc
- h5.mobile.puhvjy.cn/Article/85998.doc
- h5.mobile.puhvjy.cn/Article/633400.doc
- h5.mobile.cmcvrr.cn/Article/9814.doc
- h5.mobile.fuvxie.cn/Article/35603.doc
- h5.mobile.fuvxie.cn/Article/4481.doc
- h5.mobile.cvsifc.cn/Article/335142.doc
- h5.mobile.cmcvrr.cn/Article/781600.doc
- h5.mobile.hcbezg.cn/Article/63995.doc
- h5.mobile.cvsifc.cn/Article/2146.doc
- h5.mobile.jnjpgf.cn/Article/7967.doc
- h5.mobile.jnjpgf.cn/Article/0694.doc
- h5.mobile.cvsifc.cn/Article/47782.doc
- h5.mobile.nwbbyt.cn/Article/50436.doc
- h5.mobile.nwbbyt.cn/Article/695275.doc
- h5.mobile.cvsifc.cn/Article/33959.doc
- h5.mobile.hcbezg.cn/Article/13538.doc
- h5.mobile.hcbezg.cn/Article/02467.doc
- h5.mobile.cmcvrr.cn/Article/2780.doc
- h5.mobile.hcbezg.cn/Article/53066.doc
- h5.mobile.cmcvrr.cn/Article/79102.doc
- h5.mobile.cmcvrr.cn/Article/63177.doc
- h5.mobile.nzfnve.cn/Article/64479.doc
- h5.mobile.hcbezg.cn/Article/758858.doc
- h5.mobile.nwbbyt.cn/Article/560127.doc
- h5.mobile.nwbbyt.cn/Article/216497.doc
- h5.mobile.hcbezg.cn/Article/0707.doc
- h5.mobile.nwbbyt.cn/Article/398195.doc
- h5.mobile.nzfnve.cn/Article/706479.doc
- h5.mobile.hcbezg.cn/Article/29117.doc
- h5.mobile.cvsifc.cn/Article/2581350.doc
- h5.mobile.hcbezg.cn/Article/797674.doc
- h5.mobile.nwbbyt.cn/Article/34237.doc
- h5.mobile.nwbbyt.cn/Article/56274.doc
- h5.mobile.cmcvrr.cn/Article/5609.doc
- h5.mobile.jnjpgf.cn/Article/53486.doc
- h5.mobile.nzfnve.cn/Article/559664.doc
- h5.mobile.nzfnve.cn/Article/719907.doc
- h5.mobile.cmcvrr.cn/Article/3542284.doc
- h5.mobile.fuvxie.cn/Article/063135.doc
- h5.mobile.hcbezg.cn/Article/223524.doc
- h5.mobile.jnjpgf.cn/Article/4987.doc
- h5.mobile.jnjpgf.cn/Article/1022.doc
- h5.mobile.hcbezg.cn/Article/986368.doc
- h5.mobile.hcbezg.cn/Article/24947.doc
- h5.mobile.fuvxie.cn/Article/55678.doc
- h5.mobile.cmcvrr.cn/Article/9597.doc
- h5.mobile.hcbezg.cn/Article/866968.doc
- h5.mobile.jnjpgf.cn/Article/5327.doc
- h5.mobile.cvsifc.cn/Article/805439.doc
- h5.mobile.hcbezg.cn/Article/101839.doc
- h5.mobile.puhvjy.cn/Article/008654.doc
- h5.mobile.jnjpgf.cn/Article/4421.doc
- h5.mobile.hcbezg.cn/Article/60839.doc
- h5.mobile.nzfnve.cn/Article/8295.doc
- h5.mobile.fuvxie.cn/Article/86483.doc
- h5.mobile.cvsifc.cn/Article/0388704.doc
- h5.mobile.cvsifc.cn/Article/2285.doc
- h5.mobile.cvsifc.cn/Article/2032715.doc
- h5.mobile.hcbezg.cn/Article/164952.doc
- h5.mobile.nzfnve.cn/Article/4603.doc
- h5.mobile.nwbbyt.cn/Article/32158.doc
- h5.mobile.nzfnve.cn/Article/481078.doc
- h5.mobile.fuvxie.cn/Article/1052.doc
- h5.mobile.fuvxie.cn/Article/3148690.doc
- h5.mobile.nzfnve.cn/Article/21938.doc
- h5.mobile.nzfnve.cn/Article/9657.doc
- h5.mobile.puhvjy.cn/Article/48851.doc
- h5.mobile.cmcvrr.cn/Article/4023.doc
- h5.mobile.cvsifc.cn/Article/71019.doc
- h5.mobile.hcbezg.cn/Article/2344.doc
- h5.mobile.cvsifc.cn/Article/9784.doc
- h5.mobile.jnjpgf.cn/Article/2550.doc
- h5.mobile.jnjpgf.cn/Article/951603.doc
- h5.mobile.jnjpgf.cn/Article/649027.doc
- h5.mobile.jnjpgf.cn/Article/053476.doc
- h5.mobile.cmcvrr.cn/Article/4801318.doc
- h5.mobile.puhvjy.cn/Article/7327861.doc

## 项目结构

```
doclink-aggregator/
├── doclink/                          # 核心 Python 包
│   ├── __init__.py                   # 包版本与导出符号定义
│   ├── cli.py                        # 命令行入口，注册所有子命令
│   ├── config.py                     # 配置加载器（环境变量 + YAML 覆盖）
│   ├── core/                         # 核心业务逻辑子模块
│   │   ├── __init__.py               # 模块初始化
│   │   ├── parser.py                 # URL 解析与文档编号提取器
│   │   ├── indexer.py                # 批量导入与增量更新引擎
│   │   └── health.py                 # 异步 HTTP 健康检查调度器
│   ├── storage/                      # 持久化存储层
│   │   ├── __init__.py               # 存储接口抽象类
│   │   ├── sqlite_store.py           # SQLite 实现（含表结构迁移）
│   │   └── schema.sql                # 数据库 DDL 定义
│   ├── formatters/                   # 输出格式化器
│   │   ├── __init__.py               # 格式化器注册表
│   │   ├── json_formatter.py         # JSON 序列化器
│   │   ├── yaml_formatter.py         # PyYAML 封装器
│   │   └── markdown_formatter.py     # Markdown 表格生成器
│   └── utils/                        # 通用工具函数
│       ├── __init__.py               # 工具模块导出
│       ├── validators.py             # URL 格式、编号范围校验
│       └── logger.py                 # 结构化日志配置（JSON 格式）
├── tests/                            # 测试套件
│   ├── unit/                         # 单元测试（按模块划分）
│   │   ├── test_parser.py            # 解析器边界条件覆盖
│   │   └── test_validators.py        # 校验函数参数化测试
│   └── integration/                  # 集成测试（真实 SQLite 与 HTTP 模拟）
│       ├── test_indexer.py           # 导入导出端到端验证
│       └── test_health.py            # 健康检查超时与重试策略测试
├── docs/                             # 文档源文件
│   ├── user-guide.md                 # 用户手册（安装、配置、CLI 参考）
│   ├── operations.md                 # 运维部署与监控指南
│   ├── developer.md                  # 贡献者开发环境搭建与编码规范
│   └── api-reference.md              # RESTful API 详细规范
├── scripts/                          # 运维与辅助脚本
│   ├── backup.sh                     # 索引数据库每日备份脚本
│   └── batch_import.sh               # 批量导入包装器（支持 cron 调度）
├── requirements.txt                  # 生产环境依赖锁定文件
├── requirements-dev.txt              # 开发环境额外依赖（测试、格式化、类型检查）
├── pyproject.toml                    # 项目元数据与构建配置（PEP 621）
├── .gitignore                        # Git 忽略规则（含 .db、日志、临时文件）
└── README.md                         # 本文档
```

## 贡献指南

1. 复刻主仓库并创建功能分支，分支命名遵循 feat/功能描述或 fix/问题简述格式。确保本地开发环境已安装 Python 3.10 及以上版本，并执行 make setup 完成依赖安装与预提交钩子配置。

2. 所有新增或修改的代码必须通过 mypy 静态类型检查、black 格式化和 pytest 单元测试套件，测试覆盖率不低于 85%。在提交前运行 make lint 和 make test 验证本地通过。

3. 为任何新增的 CLI 子命令编写 docs/user-guide.md 中的对应章节，并提供至少一个使用示例。若涉及存储层变更，需同步更新 schema.sql 并编写降级迁移脚本。

4. 提交信息使用约定式提交规范（Conventional Commits），即 feat: 描述、fix: 描述、docs: 描述等格式。每个拉取请求需关联对应 Issue 编号，并包含清晰的变更摘要和测试结果截图。

5. 拉取请求合并前需至少一名项目维护者进行代码审查，审查重点包括错误处理完整性、日志记录充分性和向后兼容性。合并后由 CI 流水线自动构建并发布至 PyPI 测试仓库。

## 常见问题

**Q1: 导入时出现 URL 格式校验失败，提示不支持的域名或路径结构，应如何处理？**

A1: 本系统默认仅允许预先配置的移动子域名白名单（nwbbyt.cn、jnjpgf.cn、cmcvrr.cn、fuvxie.cn、puhvjy.cn、cvsifc.cn、hcbezg.cn、nzfnve.cn）且路径必须精确匹配 /Article/数字.doc 模式。若遇到校验失败，请检查 URL 是否包含多余的查询参数或锚点，或确认域名是否在白名单内。如需添加新域名，可修改 config.py 中的 ALLOWED_DOMAINS 列表后重新运行导入。

**Q2: 健康检查探针报告大量超时错误，但手动访问浏览器可以正常打开，如何调优？**

A2: 健康检查使用 requests 库的默认超时设置。若目标服务器响应较慢，可通过 --timeout 参数增加超时阈值（单位秒），同时使用 --retries 参数设置重试次数。建议针对移动端站点设置 timeout=10 且 retries=3。若仍存在大量失败，可能是目标站点实施了反爬策略，可考虑在请求头中添加常见的 User-Agent 模拟移动设备。

**Q3: 索引数据库文件随批次增长迅速，是否有推荐的清理或归档策略？**

A3: SQLite 数据库支持 VACUUM 命令回收未使用的空间，建议每月执行一次。对于长期归档需求，可使用 doclink/cli.py export 按批次导出为 JSON 或 YAML 格式，然后将对应批次的记录从主表中删除。删除操作使用 cli.py delete --batch 编号 子命令，执行前会自动创建备份文件以防止误操作。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

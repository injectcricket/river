# DocHub 聚合文档索引系统

DocHub 是一个面向开发者和技术研究人员的分布式文档资源聚合与索引平台。该项目致力于收集、整理和索引散布于互联网各处的技术文档、白皮书、规范说明与研究报告，解决技术从业者在查找特定领域文档时面临的信息碎片化、检索效率低下以及文档来源不可靠等问题。

本系统通过轻量级的文档索引机制，将海量外部文档资源按照主题、格式与来源进行结构化组织，并提供统一的检索入口与访问路由。DocHub 适用于需要快速定位技术参考资料、标准规范与历史存档文档的各类场景，可作为企业内部文档导航系统或开源社区知识库的基础设施组件。

## 功能概览

**分布式文档索引**：系统基于文档元数据与来源域名建立多级索引，支持按文档编号、来源站点、文件类型等维度进行快速筛选与定位。

**原始资源路由**：所有文档资源均以原始 URL 形式存储与呈现，确保访问路径的透明性与可追溯性，不进行任何形式的链接改写或代理转发。

**多域名聚合管理**：平台内置对多个文档来源域名的集中管理能力，可统一展示来自不同站点的文档资源分布情况与数量统计。

**文档元数据提取**：对索引的 .doc 文件自动提取基础元数据信息，包括文件大小、最后修改时间以及文档标题等关键字段。

**轻量级全文检索**：提供基于文档名称与编号的快速检索功能，支持模糊匹配与精确查询两种模式，满足不同精度的查找需求。

**资源状态监控**：定期对已索引的文档 URL 进行可达性检测，标记失效链接并生成资源可用性报告，保证索引库的健康度。

**批量导入与导出**：支持通过文本文件或结构化数据格式批量导入文档 URL 列表，并可将索引结果导出为 CSV 或 JSON 格式用于外部系统集成。

**访问统计与分析**：记录文档资源的访问热度、来源站点贡献度等统计数据，为资源优化与整理提供数据支撑。

## 应用场景

企业内部技术文档导航：企业技术部门可将 DocHub 部署为内部文档门户，集中索引分散在各个项目仓库、共享存储或外部网站中的技术规范、设计文档与操作手册，为团队成员提供统一的文档查找入口。

开源社区知识库建设：开源项目社区可以利用 DocHub 收集与项目相关的第三方文档、教程文章与案例研究，帮助新人更快地获取学习资料，同时降低核心维护者在文档答疑方面的重复性工作。

学术研究与文献整理：研究人员可使用 DocHub 整理特定领域的技术报告、会议论文与标准规范文档，通过统一的索引界面进行文献管理与引用追溯，提升文献调研的效率。

技术文档归档与迁移辅助：在系统升级或文档平台迁移过程中，DocHub 可作为临时的文档资源索引中心，记录原有文档的访问路径与元数据，为迁移后的链接映射与重定向提供数据基础。

## 快速开始

以下步骤指导您在本地环境中快速部署并运行 DocHub 索引系统。

```bash
# 克隆项目仓库至本地
git clone https://github.com/dochub/dochub-indexer.git

# 进入项目根目录
cd dochub-indexer

# 安装项目依赖（基于 Python 3.10+）
pip install -r requirements.txt

# 执行索引初始化与本地预览
python manage.py init --source ./data/urls.txt
python manage.py serve --port 8080
```

执行上述命令后，系统将读取默认的 URL 列表文件并建立本地索引，随后在 8080 端口启动 Web 服务。访问 http://localhost:8080 即可进入文档索引系统的操作界面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 及以上 | 核心运行环境，用于执行索引引擎与 Web 服务 |
| pip | 22.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| SQLite | 3.35 及以上 | 嵌入式数据库，用于存储文档索引与元数据 |
| Redis | 6.0 及以上 | 可选组件，用于缓存与分布式锁，生产环境推荐 |
| Nginx | 1.20 及以上 | 可选组件，用于反向代理与静态资源加速 |
| Node.js | 16.0 及以上 | 仅当需要前端开发或构建时必需 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/ | 如何使用索引系统进行文档检索、筛选与访问 |
| 管理员指南 | /docs/admin-guide/ | 如何配置数据源、管理域名列表与监控系统状态 |
| 开发文档 | /docs/developer-guide/ | 如何扩展索引器、新增元数据提取器或定制界面 |
| API 参考 | /docs/api-reference/ | 系统对外提供的 RESTful API 接口规范与调用示例 |
| 部署手册 | /docs/deployment/ | 如何在生产环境中部署高可用的 DocHub 服务集群 |
| 常见问题 | /docs/faq/ | 用户与运维人员在使用过程中遇到的典型问题与解决方案 |

## 资源列表

- h5.mobile.cvsifc.cn/Article/1107.doc
- h5.mobile.jnjpgf.cn/Article/304402.doc
- h5.mobile.puhvjy.cn/Article/42090.doc
- h5.mobile.cvsifc.cn/Article/16678.doc
- h5.mobile.nzfnve.cn/Article/5664821.doc
- h5.mobile.nwbbyt.cn/Article/4263763.doc
- h5.mobile.jnjpgf.cn/Article/66791.doc
- h5.mobile.nzfnve.cn/Article/71260.doc
- h5.mobile.jnjpgf.cn/Article/78559.doc
- h5.mobile.puhvjy.cn/Article/06294.doc
- h5.mobile.puhvjy.cn/Article/1707.doc
- h5.mobile.nzfnve.cn/Article/48234.doc
- h5.mobile.cmcvrr.cn/Article/139624.doc
- h5.mobile.cvsifc.cn/Article/97223.doc
- h5.mobile.puhvjy.cn/Article/8753.doc
- h5.mobile.hcbezg.cn/Article/5802.doc
- h5.mobile.nzfnve.cn/Article/8828.doc
- h5.mobile.jnjpgf.cn/Article/4218.doc
- h5.mobile.nzfnve.cn/Article/105073.doc
- h5.mobile.cvsifc.cn/Article/7450.doc
- h5.mobile.fuvxie.cn/Article/286809.doc
- h5.mobile.puhvjy.cn/Article/12835.doc
- h5.mobile.cvsifc.cn/Article/3315.doc
- h5.mobile.hcbezg.cn/Article/60586.doc
- h5.mobile.puhvjy.cn/Article/2037769.doc
- h5.mobile.cmcvrr.cn/Article/838591.doc
- h5.mobile.puhvjy.cn/Article/66380.doc
- h5.mobile.nzfnve.cn/Article/6813.doc
- h5.mobile.nzfnve.cn/Article/15336.doc
- h5.mobile.cmcvrr.cn/Article/4632503.doc
- h5.mobile.jnjpgf.cn/Article/5025.doc
- h5.mobile.hcbezg.cn/Article/5036530.doc
- h5.mobile.cmcvrr.cn/Article/5730.doc
- h5.mobile.cmcvrr.cn/Article/8964.doc
- h5.mobile.nzfnve.cn/Article/6509783.doc
- h5.mobile.jnjpgf.cn/Article/705870.doc
- h5.mobile.cvsifc.cn/Article/4116.doc
- h5.mobile.hcbezg.cn/Article/84589.doc
- h5.mobile.jnjpgf.cn/Article/687504.doc
- h5.mobile.cmcvrr.cn/Article/809201.doc
- h5.mobile.jnjpgf.cn/Article/16422.doc
- h5.mobile.cvsifc.cn/Article/9452.doc
- h5.mobile.cvsifc.cn/Article/26407.doc
- h5.mobile.jnjpgf.cn/Article/0529330.doc
- h5.mobile.jnjpgf.cn/Article/3855048.doc
- h5.mobile.cmcvrr.cn/Article/95980.doc
- h5.mobile.jnjpgf.cn/Article/2100.doc
- h5.mobile.fuvxie.cn/Article/81647.doc
- h5.mobile.nwbbyt.cn/Article/5119883.doc
- h5.mobile.cmcvrr.cn/Article/5386.doc
- h5.mobile.nwbbyt.cn/Article/28361.doc
- h5.mobile.puhvjy.cn/Article/1565.doc
- h5.mobile.nzfnve.cn/Article/4124.doc
- h5.mobile.jnjpgf.cn/Article/149402.doc
- h5.mobile.cmcvrr.cn/Article/7514.doc
- h5.mobile.fuvxie.cn/Article/73382.doc
- h5.mobile.nwbbyt.cn/Article/34538.doc
- h5.mobile.cmcvrr.cn/Article/27814.doc
- h5.mobile.cvsifc.cn/Article/159992.doc
- h5.mobile.hcbezg.cn/Article/074949.doc
- h5.mobile.puhvjy.cn/Article/0855.doc
- h5.mobile.fuvxie.cn/Article/67085.doc
- h5.mobile.hcbezg.cn/Article/97261.doc
- h5.mobile.puhvjy.cn/Article/82109.doc
- h5.mobile.fuvxie.cn/Article/546457.doc
- h5.mobile.cmcvrr.cn/Article/3161758.doc
- h5.mobile.jnjpgf.cn/Article/41864.doc
- h5.mobile.jnjpgf.cn/Article/882292.doc
- h5.mobile.nzfnve.cn/Article/31138.doc
- h5.mobile.nwbbyt.cn/Article/3899.doc
- h5.mobile.nzfnve.cn/Article/1675.doc
- h5.mobile.cvsifc.cn/Article/180005.doc
- h5.mobile.nzfnve.cn/Article/02288.doc
- h5.mobile.hcbezg.cn/Article/4313.doc
- h5.mobile.hcbezg.cn/Article/908729.doc
- h5.mobile.nzfnve.cn/Article/74356.doc
- h5.mobile.nzfnve.cn/Article/064999.doc
- h5.mobile.nzfnve.cn/Article/85220.doc
- h5.mobile.puhvjy.cn/Article/6853.doc
- h5.mobile.cmcvrr.cn/Article/6989984.doc
- h5.mobile.nzfnve.cn/Article/23548.doc
- h5.mobile.hcbezg.cn/Article/35635.doc
- h5.mobile.hcbezg.cn/Article/3143.doc
- h5.mobile.nwbbyt.cn/Article/76317.doc
- h5.mobile.nzfnve.cn/Article/647496.doc
- h5.mobile.cmcvrr.cn/Article/7887.doc
- h5.mobile.jnjpgf.cn/Article/62737.doc
- h5.mobile.puhvjy.cn/Article/108923.doc
- h5.mobile.nwbbyt.cn/Article/834307.doc
- h5.mobile.cvsifc.cn/Article/58106.doc
- h5.mobile.puhvjy.cn/Article/7440921.doc
- h5.mobile.jnjpgf.cn/Article/1954.doc
- h5.mobile.jnjpgf.cn/Article/099466.doc
- h5.mobile.jnjpgf.cn/Article/0061280.doc
- h5.mobile.nwbbyt.cn/Article/92895.doc
- h5.mobile.nzfnve.cn/Article/6798.doc
- h5.mobile.jnjpgf.cn/Article/17313.doc
- h5.mobile.fuvxie.cn/Article/58223.doc
- h5.mobile.jnjpgf.cn/Article/87223.doc
- h5.mobile.puhvjy.cn/Article/61358.doc
- h5.mobile.puhvjy.cn/Article/9320.doc
- h5.mobile.cmcvrr.cn/Article/9812859.doc
- h5.mobile.puhvjy.cn/Article/76594.doc
- h5.mobile.puhvjy.cn/Article/7321214.doc
- h5.mobile.fuvxie.cn/Article/181804.doc
- h5.mobile.jnjpgf.cn/Article/096857.doc
- h5.mobile.fuvxie.cn/Article/963413.doc
- h5.mobile.nwbbyt.cn/Article/961541.doc
- h5.mobile.puhvjy.cn/Article/013203.doc
- h5.mobile.nzfnve.cn/Article/3817.doc
- h5.mobile.hcbezg.cn/Article/194395.doc
- h5.mobile.cmcvrr.cn/Article/53699.doc
- h5.mobile.puhvjy.cn/Article/129831.doc
- h5.mobile.cvsifc.cn/Article/0353745.doc
- h5.mobile.puhvjy.cn/Article/9328.doc
- h5.mobile.jnjpgf.cn/Article/3338340.doc
- h5.mobile.hcbezg.cn/Article/292458.doc
- h5.mobile.cmcvrr.cn/Article/946984.doc
- h5.mobile.puhvjy.cn/Article/1042.doc
- h5.mobile.nwbbyt.cn/Article/817644.doc
- h5.mobile.cmcvrr.cn/Article/549518.doc
- h5.mobile.nwbbyt.cn/Article/9689.doc
- h5.mobile.cmcvrr.cn/Article/4137090.doc
- h5.mobile.jnjpgf.cn/Article/3828337.doc
- h5.mobile.hcbezg.cn/Article/244945.doc
- h5.mobile.puhvjy.cn/Article/52010.doc
- h5.mobile.puhvjy.cn/Article/2808888.doc
- h5.mobile.hcbezg.cn/Article/2715.doc
- h5.mobile.cvsifc.cn/Article/9610.doc
- h5.mobile.fuvxie.cn/Article/7663.doc
- h5.mobile.fuvxie.cn/Article/787060.doc
- h5.mobile.nwbbyt.cn/Article/17856.doc
- h5.mobile.nwbbyt.cn/Article/744197.doc
- h5.mobile.cvsifc.cn/Article/3143.doc
- h5.mobile.hcbezg.cn/Article/8735.doc
- h5.mobile.cvsifc.cn/Article/8821442.doc
- h5.mobile.nzfnve.cn/Article/0995299.doc
- h5.mobile.nwbbyt.cn/Article/670072.doc
- h5.mobile.cmcvrr.cn/Article/9486436.doc
- h5.mobile.cmcvrr.cn/Article/43654.doc
- h5.mobile.cmcvrr.cn/Article/0823.doc
- h5.mobile.puhvjy.cn/Article/2418508.doc
- h5.mobile.nwbbyt.cn/Article/73347.doc
- h5.mobile.nzfnve.cn/Article/85039.doc
- h5.mobile.fuvxie.cn/Article/71836.doc
- h5.mobile.jnjpgf.cn/Article/4883.doc
- h5.mobile.fuvxie.cn/Article/1610.doc
- h5.mobile.nzfnve.cn/Article/46187.doc
- h5.mobile.jnjpgf.cn/Article/84223.doc
- h5.mobile.hcbezg.cn/Article/4453.doc
- h5.mobile.jnjpgf.cn/Article/1643726.doc
- h5.mobile.hcbezg.cn/Article/4749994.doc
- h5.mobile.hcbezg.cn/Article/67988.doc
- h5.mobile.nwbbyt.cn/Article/2702.doc
- h5.mobile.nwbbyt.cn/Article/208377.doc
- h5.mobile.hcbezg.cn/Article/9599113.doc
- h5.mobile.nzfnve.cn/Article/7406.doc
- h5.mobile.puhvjy.cn/Article/1992.doc
- h5.mobile.hcbezg.cn/Article/028896.doc
- h5.mobile.jnjpgf.cn/Article/629641.doc
- h5.mobile.nzfnve.cn/Article/045335.doc
- h5.mobile.cvsifc.cn/Article/9808.doc
- h5.mobile.cvsifc.cn/Article/636920.doc
- h5.mobile.cvsifc.cn/Article/7118.doc
- h5.mobile.nwbbyt.cn/Article/0137026.doc
- h5.mobile.jnjpgf.cn/Article/0749.doc
- h5.mobile.fuvxie.cn/Article/8188240.doc
- h5.mobile.cvsifc.cn/Article/82837.doc
- h5.mobile.nzfnve.cn/Article/82116.doc
- h5.mobile.nzfnve.cn/Article/5376616.doc
- h5.mobile.jnjpgf.cn/Article/3952.doc
- h5.mobile.cvsifc.cn/Article/20235.doc
- h5.mobile.fuvxie.cn/Article/879002.doc
- h5.mobile.cmcvrr.cn/Article/4019155.doc
- h5.mobile.hcbezg.cn/Article/49346.doc
- h5.mobile.jnjpgf.cn/Article/2231.doc
- h5.mobile.puhvjy.cn/Article/87086.doc
- h5.mobile.jnjpgf.cn/Article/5717439.doc
- h5.mobile.hcbezg.cn/Article/15838.doc
- h5.mobile.puhvjy.cn/Article/3923188.doc
- h5.mobile.jnjpgf.cn/Article/559942.doc
- h5.mobile.fuvxie.cn/Article/1606507.doc
- h5.mobile.hcbezg.cn/Article/6203.doc
- h5.mobile.puhvjy.cn/Article/7967.doc
- h5.mobile.fuvxie.cn/Article/2363888.doc
- h5.mobile.cmcvrr.cn/Article/7559.doc
- h5.mobile.cmcvrr.cn/Article/7831784.doc
- h5.mobile.fuvxie.cn/Article/41841.doc
- h5.mobile.hcbezg.cn/Article/528427.doc
- h5.mobile.hcbezg.cn/Article/7664377.doc
- h5.mobile.jnjpgf.cn/Article/7341.doc
- h5.mobile.fuvxie.cn/Article/6814.doc
- h5.mobile.cmcvrr.cn/Article/85723.doc
- h5.mobile.puhvjy.cn/Article/5353578.doc
- h5.mobile.cmcvrr.cn/Article/05547.doc
- h5.mobile.puhvjy.cn/Article/498022.doc
- h5.mobile.cmcvrr.cn/Article/761387.doc
- h5.mobile.nwbbyt.cn/Article/56100.doc
- h5.mobile.puhvjy.cn/Article/883058.doc
- h5.mobile.cmcvrr.cn/Article/9438.doc
- h5.mobile.puhvjy.cn/Article/066422.doc
- h5.mobile.nzfnve.cn/Article/156474.doc
- h5.mobile.jnjpgf.cn/Article/591215.doc
- h5.mobile.cvsifc.cn/Article/432604.doc
- h5.mobile.fuvxie.cn/Article/5504.doc
- h5.mobile.fuvxie.cn/Article/2181619.doc
- h5.mobile.fuvxie.cn/Article/39640.doc
- h5.mobile.puhvjy.cn/Article/5046.doc
- h5.mobile.hcbezg.cn/Article/7962.doc
- h5.mobile.puhvjy.cn/Article/3933.doc
- h5.mobile.cmcvrr.cn/Article/041241.doc
- h5.mobile.nwbbyt.cn/Article/924426.doc
- h5.mobile.nwbbyt.cn/Article/8612119.doc
- h5.mobile.jnjpgf.cn/Article/5030.doc
- h5.mobile.cvsifc.cn/Article/6662.doc
- h5.mobile.puhvjy.cn/Article/707851.doc
- h5.mobile.nzfnve.cn/Article/6780072.doc
- h5.mobile.hcbezg.cn/Article/8585889.doc
- h5.mobile.cvsifc.cn/Article/1517.doc
- h5.mobile.cmcvrr.cn/Article/844735.doc
- h5.mobile.fuvxie.cn/Article/4080779.doc
- h5.mobile.nwbbyt.cn/Article/22503.doc
- h5.mobile.jnjpgf.cn/Article/4714927.doc
- h5.mobile.nwbbyt.cn/Article/61993.doc
- h5.mobile.jnjpgf.cn/Article/84191.doc
- h5.mobile.hcbezg.cn/Article/5436.doc
- h5.mobile.cmcvrr.cn/Article/573796.doc
- h5.mobile.cmcvrr.cn/Article/7935368.doc
- h5.mobile.jnjpgf.cn/Article/25327.doc
- h5.mobile.cvsifc.cn/Article/948240.doc
- h5.mobile.hcbezg.cn/Article/90132.doc
- h5.mobile.fuvxie.cn/Article/3660.doc
- h5.mobile.nwbbyt.cn/Article/71285.doc
- h5.mobile.hcbezg.cn/Article/0741101.doc
- h5.mobile.cmcvrr.cn/Article/6571888.doc
- h5.mobile.hcbezg.cn/Article/5359367.doc
- h5.mobile.nwbbyt.cn/Article/960366.doc
- h5.mobile.jnjpgf.cn/Article/9982.doc
- h5.mobile.nwbbyt.cn/Article/3844584.doc
- h5.mobile.cmcvrr.cn/Article/0124468.doc
- h5.mobile.nzfnve.cn/Article/101447.doc
- h5.mobile.puhvjy.cn/Article/421761.doc
- h5.mobile.hcbezg.cn/Article/7424895.doc
- h5.mobile.cvsifc.cn/Article/3225308.doc
- h5.mobile.nzfnve.cn/Article/76971.doc
- h5.mobile.cmcvrr.cn/Article/5880897.doc
- h5.mobile.fuvxie.cn/Article/571608.doc
- h5.mobile.jnjpgf.cn/Article/616793.doc
- h5.mobile.nzfnve.cn/Article/638677.doc
- h5.mobile.nzfnve.cn/Article/18061.doc

## 项目结构

```
dochub-indexer/
├── docs/                                 # 项目文档目录
│   ├── user-guide/                       # 用户操作手册
│   │   ├── search.md                     # 检索功能使用说明
│   │   └── navigation.md                 # 资源浏览与导航指引
│   ├── admin-guide/                      # 系统管理文档
│   │   ├── datasource.md                 # 数据源配置与维护
│   │   └── monitoring.md                 # 系统状态监控与告警
│   └── developer-guide/                  # 开发者文档
│       ├── architecture.md               # 系统架构设计说明
│       └── extension.md                  # 插件与扩展开发指南
├── src/                                  # 核心源代码目录
│   ├── indexer/                          # 索引引擎模块
│   │   ├── crawler.py                    # 文档元数据抓取器
│   │   ├── parser.py                     # URL 解析与规范化工具
│   │   └── registry.py                   # 索引注册与更新管理
│   ├── storage/                          # 数据存储层
│   │   ├── database.py                   # SQLite 数据库操作封装
│   │   └── models.py                     # 数据模型定义（ORM）
│   ├── web/                              # Web 服务层
│   │   ├── routes.py                     # 路由与请求分发
│   │   ├── templates/                    # Jinja2 模板文件
│   │   └── static/                       # 静态资源（CSS/JS）
│   └── utils/                            # 通用工具函数
│       ├── validator.py                  # URL 有效性校验
│       └── formatter.py                  # 数据格式化与导出
├── tests/                                # 单元测试与集成测试
│   ├── test_indexer.py                   # 索引模块测试用例
│   └── test_storage.py                   # 存储层测试用例
├── scripts/                              # 运维与辅助脚本
│   ├── import_urls.py                    # 批量 URL 导入脚本
│   └── health_check.py                   # 资源健康状态检查脚本
├── config/                               # 配置文件目录
│   ├── default.yaml                      # 默认配置参数
│   └── production.yaml                   # 生产环境配置覆盖
├── data/                                 # 数据文件目录
│   └── urls.txt                          # 默认 URL 数据源文件
├── requirements.txt                      # Python 依赖清单
├── setup.py                              # 项目安装脚本
└── README.md                             # 项目说明文件（本文件）
```

## 贡献指南

我们欢迎并鼓励社区开发者参与 DocHub 项目的改进与完善。请遵循以下步骤提交您的贡献。

1. 查阅贡献者行为准则与开发者文档，了解项目的代码风格、测试规范与提交要求，确保您的修改符合项目整体的设计方向。

2. 在 GitHub 上 Fork 本项目至您的个人仓库，并在本地创建新的功能分支进行开发，分支命名建议采用 feature/功能描述 或 fix/问题描述 的格式。

3. 完成代码修改后，请确保所有现有测试用例通过，并为新增功能补充相应的单元测试与文档说明，保证代码的可维护性与可读性。

4. 提交 Pull Request 至主仓库的 main 分支，并在描述中清晰说明本次修改的目的、实现方式以及相关的 Issue 编号，等待项目维护者的代码审查与反馈。

5. 根据维护者的评审意见进行必要的修改与调整，直至代码被合并。合并后您的贡献将被记录在项目的贡献者列表中。

## 常见问题

问：系统索引的文档资源无法访问时应如何处理？

答：DocHub 内置了资源健康状态检测机制，会定期对索引库中的 URL 进行可达性验证。当发现某个文档链接失效时，系统会在管理后台标记该资源为不可用状态，并在检索结果中给出提示。管理员可通过管理界面手动触发重新检测，或从索引库中移除长期失效的资源记录。

问：如何将自有文档资源批量导入 DocHub 索引系统？

答：系统支持通过文本文件进行批量导入。您可以将文档 URL 按行排列存入 .txt 文件中，每行一个 URL，然后使用 scripts/import_urls.py 脚本执行导入操作。导入过程中系统会自动进行 URL 格式校验与元数据提取，并在导入完成后生成导入报告。

问：DocHub 是否支持对文档内容进行全文搜索？

答：当前版本的 DocHub 主要基于文档元数据（包括文档名称、编号、来源域名等）进行索引与检索，暂不支持对 .doc 文件内部文本内容的全文搜索。如需内容级检索能力，建议将本系统与 Elasticsearch 等专业全文检索引擎集成，或通过扩展开发实现自定义的内容提取与索引逻辑。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

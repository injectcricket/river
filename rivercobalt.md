# DocHub Mobile Resource Aggregator

DocHub Mobile Resource Aggregator 是一个面向移动端文档资源的高效外链管理与分发系统，专为内容采集、文档索引及批量资源调度场景设计。项目定位于技术资源汇总与文档外链仓库，帮助开发者、研究人员及内容运营团队快速定位并获取分布在多个源站的大量文档资源，解决人工收集效率低、链接分散、缺乏统一管理入口的问题。

本项目的核心使用场景包括批量文档链接的导入导出、自动化巡检与可用性检测、以及基于分类标签的资源导航。通过结构化存储与标准化输出，本项目可作为上层应用（如文档搜索引擎、内容聚合平台、企业内部知识库）的数据支撑层，提供稳定、可扩展的链接数据服务。

## 功能概览

批量外链导入与解析 支持大规模文档链接的批量录入与结构化存储，自动识别链接来源域名及文档标识符。

多源站点统一聚合 整合来自多个移动端源站点的文档资源，提供统一的数据访问接口，消除源站差异。

链接状态健康检查 内置链接有效性检测机制，支持定时巡检与异常告警，便于运维人员及时处理失效链接。

分类标签与检索过滤 为每条资源赋予分类标签，支持按域名、文档类型、时间范围等多维度检索与过滤。

数据导出与同步接口 提供标准化的数据导出功能，支持 JSON、CSV 等格式输出，方便与第三方系统对接。

访问统计与热度分析 记录资源被请求的频率与时间分布，生成访问趋势报表，辅助内容运营决策。

命令行与配置文件管理 提供完整的命令行操作界面，支持通过配置文件定义资源库参数，适用于自动化运维脚本。

## 应用场景

企业内部知识库文档归集 企业可将分散在各个业务系统或外部源站的培训资料、技术手册、项目文档等通过本项目的链接管理体系进行统一归集，员工通过统一入口即可检索和访问所需文档。

学术研究文献索引管理 研究人员在开展文献调研时，可将收集到的论文、报告、数据附录等文档链接录入系统，通过分类标签进行课题分组，并利用链接健康检查功能定期验证资源的可访问性。

内容聚合平台数据源接入 内容聚合类网站或小程序可通过本项目提供的 API 接口，将多个移动端源站的文档链接纳入自身的检索与推荐系统，丰富平台的内容生态，降低人工维护成本。

自动化文档巡检与运维监控 运维团队可利用本项目的命令行工具和健康检查模块，对重要文档资源进行定时监控，当链接返回异常状态码时触发告警，确保关键业务文档的可用性。

## 快速开始

以下步骤指导您在本机环境中快速部署并运行 DocHub Mobile Resource Aggregator。

```bash
# 步骤 1: 克隆代码仓库
git clone https://github.com/dochub/dochub-mobile-aggregator.git
cd dochub-mobile-aggregator

# 步骤 2: 安装项目依赖
pip install -r requirements.txt

# 步骤 3: 初始化本地资源索引并运行服务
python manage.py init --config config/default.yaml
python manage.py serve --host 0.0.0.0 --port 8080
```

执行上述命令后，服务将在本地 8080 端口启动，可通过浏览器或命令行工具访问资源索引接口。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 项目核心运行时环境 |
| pip | 22.0 及以上 | Python 包管理器，用于安装依赖库 |
| requests | 2.28.0 及以上 | HTTP 请求库，用于链接健康检查与资源获取 |
| pyyaml | 6.0 及以上 | YAML 配置文件解析 |
| click | 8.1.0 及以上 | 命令行接口框架 |
| redis | 6.2 及以上 | 可选组件，用于缓存与访问统计（生产环境推荐） |
| sqlite3 | 系统内置 | 本地资源索引数据库，Python 标准库自带 |
| gunicorn | 20.1.0 及以上 | 生产环境 WSGI 服务器（部署时使用） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide.md | 如何配置资源源站、如何导入导出链接、如何使用检索功能 |
| 运维指南 | /docs/operations.md | 如何部署生产环境、如何配置巡检任务、如何查看健康状态 |
| API 参考 | /docs/api-reference.md | 提供哪些 RESTful 接口、请求参数与返回结构如何定义 |
| 开发文档 | /docs/development.md | 项目目录结构说明、如何二次开发、如何提交代码变更 |

## 资源列表

- h5.mobile.hcbezg.cn/Article/474003.doc
- h5.mobile.fuvxie.cn/Article/7230075.doc
- h5.mobile.cvsifc.cn/Article/747355.doc
- h5.mobile.cmcvrr.cn/Article/75329.doc
- h5.mobile.cvsifc.cn/Article/451269.doc
- h5.mobile.fuvxie.cn/Article/27286.doc
- h5.mobile.jnjpgf.cn/Article/013045.doc
- h5.mobile.hcbezg.cn/Article/1846.doc
- h5.mobile.hcbezg.cn/Article/3389567.doc
- h5.mobile.puhvjy.cn/Article/8435.doc
- h5.mobile.puhvjy.cn/Article/03215.doc
- h5.mobile.jnjpgf.cn/Article/2112918.doc
- h5.mobile.cmcvrr.cn/Article/7792900.doc
- h5.mobile.nwbbyt.cn/Article/893999.doc
- h5.mobile.hcbezg.cn/Article/1849286.doc
- h5.mobile.jnjpgf.cn/Article/03511.doc
- h5.mobile.fuvxie.cn/Article/55548.doc
- h5.mobile.fuvxie.cn/Article/8437.doc
- h5.mobile.cmcvrr.cn/Article/8712608.doc
- h5.mobile.cmcvrr.cn/Article/8765.doc
- h5.mobile.nwbbyt.cn/Article/1896158.doc
- h5.mobile.cvsifc.cn/Article/203747.doc
- h5.mobile.nwbbyt.cn/Article/96432.doc
- h5.mobile.hcbezg.cn/Article/0817.doc
- h5.mobile.fuvxie.cn/Article/371352.doc
- h5.mobile.cmcvrr.cn/Article/4488747.doc
- h5.mobile.nwbbyt.cn/Article/692672.doc
- h5.mobile.nzfnve.cn/Article/4142850.doc
- h5.mobile.nwbbyt.cn/Article/15225.doc
- h5.mobile.fuvxie.cn/Article/288133.doc
- h5.mobile.nzfnve.cn/Article/322209.doc
- h5.mobile.jnjpgf.cn/Article/7871.doc
- h5.mobile.hcbezg.cn/Article/05007.doc
- h5.mobile.fuvxie.cn/Article/00104.doc
- h5.mobile.cmcvrr.cn/Article/0773590.doc
- h5.mobile.puhvjy.cn/Article/3188.doc
- h5.mobile.fuvxie.cn/Article/765970.doc
- h5.mobile.cmcvrr.cn/Article/002956.doc
- h5.mobile.jnjpgf.cn/Article/655692.doc
- h5.mobile.nzfnve.cn/Article/6859524.doc
- h5.mobile.fuvxie.cn/Article/9721634.doc
- h5.mobile.puhvjy.cn/Article/829743.doc
- h5.mobile.jnjpgf.cn/Article/987626.doc
- h5.mobile.nzfnve.cn/Article/02155.doc
- h5.mobile.puhvjy.cn/Article/7734652.doc
- h5.mobile.hcbezg.cn/Article/0603798.doc
- h5.mobile.jnjpgf.cn/Article/96744.doc
- h5.mobile.nwbbyt.cn/Article/1982.doc
- h5.mobile.puhvjy.cn/Article/2358.doc
- h5.mobile.jnjpgf.cn/Article/2568428.doc
- h5.mobile.cvsifc.cn/Article/0911.doc
- h5.mobile.fuvxie.cn/Article/4810.doc
- h5.mobile.nwbbyt.cn/Article/44420.doc
- h5.mobile.puhvjy.cn/Article/197716.doc
- h5.mobile.cvsifc.cn/Article/08996.doc
- h5.mobile.hcbezg.cn/Article/4947265.doc
- h5.mobile.nwbbyt.cn/Article/95606.doc
- h5.mobile.fuvxie.cn/Article/431148.doc
- h5.mobile.nzfnve.cn/Article/7581789.doc
- h5.mobile.fuvxie.cn/Article/78210.doc
- h5.mobile.jnjpgf.cn/Article/87951.doc
- h5.mobile.fuvxie.cn/Article/1186.doc
- h5.mobile.cvsifc.cn/Article/79626.doc
- h5.mobile.cmcvrr.cn/Article/833708.doc
- h5.mobile.jnjpgf.cn/Article/6975177.doc
- h5.mobile.hcbezg.cn/Article/079921.doc
- h5.mobile.nzfnve.cn/Article/5378.doc
- h5.mobile.puhvjy.cn/Article/4619386.doc
- h5.mobile.jnjpgf.cn/Article/50347.doc
- h5.mobile.cmcvrr.cn/Article/6020.doc
- h5.mobile.jnjpgf.cn/Article/3450764.doc
- h5.mobile.jnjpgf.cn/Article/2290.doc
- h5.mobile.nzfnve.cn/Article/82462.doc
- h5.mobile.hcbezg.cn/Article/79907.doc
- h5.mobile.cmcvrr.cn/Article/154845.doc
- h5.mobile.hcbezg.cn/Article/51646.doc
- h5.mobile.fuvxie.cn/Article/7507.doc
- h5.mobile.hcbezg.cn/Article/7058.doc
- h5.mobile.cmcvrr.cn/Article/980178.doc
- h5.mobile.jnjpgf.cn/Article/260313.doc
- h5.mobile.puhvjy.cn/Article/4057635.doc
- h5.mobile.nwbbyt.cn/Article/47631.doc
- h5.mobile.nwbbyt.cn/Article/11233.doc
- h5.mobile.fuvxie.cn/Article/49583.doc
- h5.mobile.fuvxie.cn/Article/6322872.doc
- h5.mobile.jnjpgf.cn/Article/2651.doc
- h5.mobile.nwbbyt.cn/Article/520906.doc
- h5.mobile.cvsifc.cn/Article/400976.doc
- h5.mobile.cmcvrr.cn/Article/42106.doc
- h5.mobile.jnjpgf.cn/Article/9959.doc
- h5.mobile.nwbbyt.cn/Article/054663.doc
- h5.mobile.puhvjy.cn/Article/3068.doc
- h5.mobile.fuvxie.cn/Article/2089.doc
- h5.mobile.nwbbyt.cn/Article/9106504.doc
- h5.mobile.jnjpgf.cn/Article/9327689.doc
- h5.mobile.fuvxie.cn/Article/0600874.doc
- h5.mobile.puhvjy.cn/Article/4694.doc
- h5.mobile.cvsifc.cn/Article/839666.doc
- h5.mobile.hcbezg.cn/Article/8200.doc
- h5.mobile.puhvjy.cn/Article/617078.doc
- h5.mobile.cmcvrr.cn/Article/2106.doc
- h5.mobile.jnjpgf.cn/Article/78705.doc
- h5.mobile.jnjpgf.cn/Article/5807769.doc
- h5.mobile.nwbbyt.cn/Article/766220.doc
- h5.mobile.hcbezg.cn/Article/13447.doc
- h5.mobile.nwbbyt.cn/Article/86505.doc
- h5.mobile.puhvjy.cn/Article/150549.doc
- h5.mobile.cvsifc.cn/Article/4883.doc
- h5.mobile.jnjpgf.cn/Article/55855.doc
- h5.mobile.puhvjy.cn/Article/9874.doc
- h5.mobile.puhvjy.cn/Article/2169174.doc
- h5.mobile.jnjpgf.cn/Article/18194.doc
- h5.mobile.fuvxie.cn/Article/18745.doc
- h5.mobile.hcbezg.cn/Article/915468.doc
- h5.mobile.jnjpgf.cn/Article/8277401.doc
- h5.mobile.puhvjy.cn/Article/5039431.doc
- h5.mobile.hcbezg.cn/Article/655422.doc
- h5.mobile.hcbezg.cn/Article/5073.doc
- h5.mobile.hcbezg.cn/Article/5633.doc
- h5.mobile.hcbezg.cn/Article/83087.doc
- h5.mobile.cmcvrr.cn/Article/7283.doc
- h5.mobile.hcbezg.cn/Article/586618.doc
- h5.mobile.cvsifc.cn/Article/1589905.doc
- h5.mobile.cvsifc.cn/Article/0210097.doc
- h5.mobile.cvsifc.cn/Article/772281.doc
- h5.mobile.nwbbyt.cn/Article/531553.doc
- h5.mobile.nwbbyt.cn/Article/1948.doc
- h5.mobile.nwbbyt.cn/Article/82802.doc
- h5.mobile.puhvjy.cn/Article/5299801.doc
- h5.mobile.jnjpgf.cn/Article/467212.doc
- h5.mobile.nzfnve.cn/Article/118522.doc
- h5.mobile.fuvxie.cn/Article/854481.doc
- h5.mobile.fuvxie.cn/Article/40396.doc
- h5.mobile.nzfnve.cn/Article/475281.doc
- h5.mobile.jnjpgf.cn/Article/87743.doc
- h5.mobile.cvsifc.cn/Article/20879.doc
- h5.mobile.nzfnve.cn/Article/6740.doc
- h5.mobile.hcbezg.cn/Article/9095.doc
- h5.mobile.cmcvrr.cn/Article/247765.doc
- h5.mobile.jnjpgf.cn/Article/3810.doc
- h5.mobile.jnjpgf.cn/Article/89716.doc
- h5.mobile.cmcvrr.cn/Article/908914.doc
- h5.mobile.cmcvrr.cn/Article/605678.doc
- h5.mobile.puhvjy.cn/Article/0495150.doc
- h5.mobile.hcbezg.cn/Article/56088.doc
- h5.mobile.fuvxie.cn/Article/2528.doc
- h5.mobile.nzfnve.cn/Article/0167.doc
- h5.mobile.nwbbyt.cn/Article/2812678.doc
- h5.mobile.jnjpgf.cn/Article/9959440.doc
- h5.mobile.nwbbyt.cn/Article/79490.doc
- h5.mobile.nzfnve.cn/Article/2682.doc
- h5.mobile.nzfnve.cn/Article/9981.doc
- h5.mobile.jnjpgf.cn/Article/206835.doc
- h5.mobile.jnjpgf.cn/Article/532790.doc
- h5.mobile.puhvjy.cn/Article/1921.doc
- h5.mobile.cvsifc.cn/Article/94988.doc
- h5.mobile.cmcvrr.cn/Article/9646.doc
- h5.mobile.fuvxie.cn/Article/36652.doc
- h5.mobile.jnjpgf.cn/Article/1990.doc
- h5.mobile.puhvjy.cn/Article/73558.doc
- h5.mobile.nzfnve.cn/Article/11443.doc
- h5.mobile.nwbbyt.cn/Article/101843.doc
- h5.mobile.nzfnve.cn/Article/3827145.doc
- h5.mobile.cvsifc.cn/Article/5720.doc
- h5.mobile.hcbezg.cn/Article/4828163.doc
- h5.mobile.cmcvrr.cn/Article/97180.doc
- h5.mobile.cmcvrr.cn/Article/6875.doc
- h5.mobile.fuvxie.cn/Article/42030.doc
- h5.mobile.jnjpgf.cn/Article/127503.doc
- h5.mobile.jnjpgf.cn/Article/2705.doc
- h5.mobile.hcbezg.cn/Article/390050.doc
- h5.mobile.fuvxie.cn/Article/70656.doc
- h5.mobile.nzfnve.cn/Article/8005.doc
- h5.mobile.nwbbyt.cn/Article/795832.doc
- h5.mobile.fuvxie.cn/Article/4291.doc
- h5.mobile.cmcvrr.cn/Article/3689.doc
- h5.mobile.jnjpgf.cn/Article/2460670.doc
- h5.mobile.cmcvrr.cn/Article/2186491.doc
- h5.mobile.cmcvrr.cn/Article/969141.doc
- h5.mobile.cvsifc.cn/Article/09485.doc
- h5.mobile.cmcvrr.cn/Article/0488.doc
- h5.mobile.fuvxie.cn/Article/860874.doc
- h5.mobile.nzfnve.cn/Article/33578.doc
- h5.mobile.nwbbyt.cn/Article/094414.doc
- h5.mobile.nwbbyt.cn/Article/979898.doc
- h5.mobile.fuvxie.cn/Article/11370.doc
- h5.mobile.nzfnve.cn/Article/4892.doc
- h5.mobile.fuvxie.cn/Article/5499879.doc
- h5.mobile.nzfnve.cn/Article/2132838.doc
- h5.mobile.nzfnve.cn/Article/7071.doc
- h5.mobile.fuvxie.cn/Article/1161.doc
- h5.mobile.nwbbyt.cn/Article/92931.doc
- h5.mobile.cmcvrr.cn/Article/780497.doc
- h5.mobile.cmcvrr.cn/Article/8148.doc
- h5.mobile.fuvxie.cn/Article/97799.doc
- h5.mobile.puhvjy.cn/Article/0735479.doc
- h5.mobile.nwbbyt.cn/Article/1164.doc
- h5.mobile.jnjpgf.cn/Article/36676.doc
- h5.mobile.puhvjy.cn/Article/08008.doc
- h5.mobile.cmcvrr.cn/Article/836134.doc
- h5.mobile.cvsifc.cn/Article/22677.doc
- h5.mobile.puhvjy.cn/Article/223877.doc
- h5.mobile.nzfnve.cn/Article/7205546.doc
- h5.mobile.nwbbyt.cn/Article/2182565.doc
- h5.mobile.nzfnve.cn/Article/269956.doc
- h5.mobile.puhvjy.cn/Article/6119.doc
- h5.mobile.cvsifc.cn/Article/74916.doc
- h5.mobile.fuvxie.cn/Article/9034376.doc
- h5.mobile.jnjpgf.cn/Article/068365.doc
- h5.mobile.fuvxie.cn/Article/0377.doc
- h5.mobile.jnjpgf.cn/Article/72991.doc
- h5.mobile.nzfnve.cn/Article/661115.doc
- h5.mobile.hcbezg.cn/Article/468311.doc
- h5.mobile.nzfnve.cn/Article/67830.doc
- h5.mobile.jnjpgf.cn/Article/591102.doc
- h5.mobile.cvsifc.cn/Article/62406.doc
- h5.mobile.hcbezg.cn/Article/0519626.doc
- h5.mobile.hcbezg.cn/Article/58348.doc
- h5.mobile.cmcvrr.cn/Article/1508.doc
- h5.mobile.cmcvrr.cn/Article/6542738.doc
- h5.mobile.hcbezg.cn/Article/8881644.doc
- h5.mobile.cvsifc.cn/Article/754563.doc
- h5.mobile.cvsifc.cn/Article/89929.doc
- h5.mobile.puhvjy.cn/Article/1693.doc
- h5.mobile.fuvxie.cn/Article/789837.doc
- h5.mobile.cmcvrr.cn/Article/55723.doc
- h5.mobile.cmcvrr.cn/Article/9496.doc
- h5.mobile.nzfnve.cn/Article/1174.doc
- h5.mobile.cvsifc.cn/Article/02514.doc
- h5.mobile.cvsifc.cn/Article/53817.doc
- h5.mobile.cmcvrr.cn/Article/654361.doc
- h5.mobile.cvsifc.cn/Article/8731489.doc
- h5.mobile.nzfnve.cn/Article/9132.doc
- h5.mobile.jnjpgf.cn/Article/030543.doc
- h5.mobile.nwbbyt.cn/Article/1430.doc
- h5.mobile.jnjpgf.cn/Article/0675923.doc
- h5.mobile.jnjpgf.cn/Article/4950863.doc
- h5.mobile.cvsifc.cn/Article/00829.doc
- h5.mobile.fuvxie.cn/Article/896880.doc
- h5.mobile.nzfnve.cn/Article/7487.doc
- h5.mobile.cmcvrr.cn/Article/1874683.doc
- h5.mobile.cvsifc.cn/Article/665117.doc
- h5.mobile.puhvjy.cn/Article/42531.doc
- h5.mobile.jnjpgf.cn/Article/3951373.doc
- h5.mobile.nzfnve.cn/Article/3064615.doc
- h5.mobile.nwbbyt.cn/Article/16172.doc
- h5.mobile.hcbezg.cn/Article/904444.doc
- h5.mobile.hcbezg.cn/Article/8180.doc
- h5.mobile.jnjpgf.cn/Article/350359.doc
- h5.mobile.cmcvrr.cn/Article/4118483.doc

## 项目结构

```
dochub-mobile-aggregator/
├── src/                                # 项目核心源代码目录
│   ├── core/                           # 核心功能模块
│   │   ├── indexer.py                  # 资源索引引擎，负责链接解析与入库
│   │   ├── checker.py                  # 链接健康检查器，执行 HTTP 探测
│   │   └── statistics.py               # 访问统计与热度计算模块
│   ├── api/                            # RESTful API 接口层
│   │   ├── routes.py                   # 路由注册与请求分发
│   │   ├── schemas.py                  # 请求/响应数据模型定义
│   │   └── middleware.py               # 鉴权、日志、限流等中间件
│   ├── cli/                            # 命令行工具实现
│   │   ├── main.py                     # CLI 入口与命令注册
│   │   ├── init.py                     # 初始化命令逻辑
│   │   └── serve.py                    # 服务启动命令逻辑
│   └── utils/                          # 通用工具函数
│       ├── http.py                     # 封装 requests 的 HTTP 客户端
│       ├── config.py                   # YAML 配置文件加载与合并
│       └── logger.py                   # 日志格式化与输出控制
├── config/                             # 配置文件目录
│   ├── default.yaml                    # 默认配置（开发环境适用）
│   ├── production.yaml                 # 生产环境配置覆盖
│   └── schema.yaml                     # 配置项结构说明
├── data/                               # 本地数据存储目录
│   ├── index.db                        # SQLite 资源索引数据库文件
│   ├── cache/                          # Redis 缓存持久化目录（若使用文件缓存）
│   └── logs/                           # 应用运行日志存放位置
├── docs/                               # 项目文档目录
│   ├── user-guide.md                   # 用户操作手册
│   ├── operations.md                   # 运维部署指南
│   ├── api-reference.md                # API 接口完整参考
│   └── development.md                  # 开发者贡献指南
├── tests/                              # 自动化测试目录
│   ├── unit/                           # 单元测试用例
│   ├── integration/                    # 集成测试用例
│   └── fixtures/                       # 测试数据与模拟文件
├── scripts/                            # 辅助运维脚本
│   ├── backup_db.sh                    # 数据库备份脚本
│   ├── health_check_cron.py            # 定时巡检定时任务脚本
│   └── import_links.py                 # 批量导入外部链接脚本
├── requirements.txt                    # Python 依赖清单
├── setup.py                            # 项目打包与安装配置
├── Makefile                            # 常用命令快捷方式（如 make test）
└── README.md                           # 项目说明文档（本文件）
```

## 贡献指南

我们欢迎社区开发者参与项目建设，请按照以下流程贡献代码或文档。

1. 阅读开发文档与代码风格指南 在提交任何变更之前，请仔细阅读 /docs/development.md 文档，了解项目的代码规范、测试要求及 Git 提交信息格式。

2. 在 Issue 列表中认领任务或提交新 Issue 访问 GitHub Issues 页面，查看当前待解决的问题或功能需求。如果您发现新的缺陷或改进点，请创建详细的 Issue 描述，并等待维护者确认。

3. 创建功能分支并提交代码 从 main 分支切出新的功能分支，分支命名遵循 feature/xxx 或 fix/xxx 格式。提交代码时请确保所有单元测试通过，并添加必要的测试用例覆盖新增逻辑。

4. 发起 Pull Request 并参与代码评审 将功能分支推送至远程仓库，发起 Pull Request 至 main 分支。PR 描述中需注明关联的 Issue 编号，并简要说明变更内容。维护者将对代码进行评审，必要时请根据反馈进行修改。

5. 更新文档与变更日志 若您的变更涉及用户可见的功能调整或配置变更，请同步更新对应的用户手册或运维指南，并在 CHANGELOG.md 文件中记录变更摘要。

## 常见问题

Q: 项目启动时提示 "ModuleNotFoundError: No module named 'yaml'"

A: 请确认已执行 pip install -r requirements.txt 安装所有依赖。若仍然报错，可能是 pip 版本过低或虚拟环境未激活，建议升级 pip（pip install --upgrade pip）后重新安装依赖，并确保在正确的 Python 虚拟环境下运行。

Q: 如何添加新的资源源站或修改现有源站的配置？

A: 所有源站配置定义在 config/default.yaml 文件的 sources 字段下。您可以通过编辑该文件新增或修改源站条目，包括域名、请求超时时间、User-Agent 等参数。修改后需要重启服务使配置生效。若使用生产环境配置，请同时更新 config/production.yaml 中的对应覆盖项。

Q: 链接健康检查功能如何工作，检查频率是否可以调整？

A: 健康检查模块通过发送 HTTP HEAD 请求判断链接是否可访问，根据响应状态码（2xx 为正常，4xx/5xx 为异常）记录状态。检查频率由 config 目录下的 checker.interval 参数控制，默认值为 86400 秒（即 24 小时一次）。您可以根据运维需求调整该值，最小建议间隔为 3600 秒。调整后重启服务或使用 reload 命令即可生效。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

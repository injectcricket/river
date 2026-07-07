# DocLink Hive

DocLink Hive 是一个面向技术文档聚合与结构化外链管理的开源工具集。项目定位为轻量级文档资源索引中间件，帮助开发者、技术团队与内容运营人员将分散于多个域名的技术文档、操作手册、设计规范与培训材料进行统一归集与快速检索。

本项目解决的核心问题包括：异构域名下文档资源的分散存储导致检索效率低下；文档 URL 缺乏版本标识与分类元数据；团队协作中难以追踪外部文档的变更与可用性。DocLink Hive 通过可配置的抓取调度、本地缓存与只读 API 输出，将原始资源链接转化为可查询、可过滤、可监控的内部知识库入口。

## 功能概览

批量链接导入与规范化清洗：接受原始 URL 列表，自动识别协议与路径格式，剔除重复条目并生成标准化的资源清单。

多维度标签分类引擎：基于域名特征与路径关键词为每个资源自动打标，支持按技术领域、文档类型、更新频次等维度聚合。

可用性健康检查：周期性对已收录链接发起 HEAD 请求，检测响应状态码与内容类型，标记失效或重定向资源。

只读查询 API 服务：提供 RESTful 接口，支持按关键字、域名分组、文档后缀名等条件筛选已收录资源，返回 JSON 格式列表。

本地轻量缓存层：使用 SQLite 存储资源元数据，支持增量更新与版本回滚，无需外部数据库依赖。

结构化日志与审计追踪：记录每次抓取任务的结果、新增链接数、异常响应详情，便于排查外部资源变更。

导出能力：支持将资源列表导出为 Markdown 表格、JSON 数组或 CSV 文件，用于嵌入内部文档门户或生成周报。

## 应用场景

技术团队内部文档门户构建：团队维护多个技术栈的操作手册与运维指南，分布在不同子域名下。DocLink Hive 可将这些分散链接统一收录，并提供标签筛选与健康检查，帮助新成员快速找到最新版部署手册。

在线教育平台课程资料索引：在线课程平台需要为每门课程挂载外部阅读材料与实验指导文档。通过本项目的批量导入与分类功能，运营人员可按课程编号与章节顺序组织资源，避免链接错乱或失效。

企业合规文档审计与归档：合规部门需要定期核对分布在多个业务系统的政策文件与流程说明。DocLink Hive 的健康检查与审计日志功能可记录每次链接访问状态，为内部审计提供访问记录凭证。

个人知识库外链整理：技术博主或研究员积累了大量技术参考文档的收藏链接。使用本项目的查询 API 与导出功能，可快速生成带分类注释的资源清单，嵌入个人笔记或博客侧边栏。

## 快速开始

以下步骤指导您在本地环境中完成 DocLink Hive 的克隆、依赖安装与服务启动。

```bash
# 克隆仓库
git clone https://github.com/doclink-hive/doclink-hive.git
cd doclink-hive

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化 SQLite 数据库与配置模板
python scripts/init_db.py
cp config.example.yaml config.yaml

# 编辑 config.yaml 设置资源源文件路径与检查周期
# 默认资源列表位于 data/source_urls.txt

# 启动本地 API 服务（默认端口 8000）
python app.py
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| --- | --- | --- |
| Python | 3.9 - 3.12 | 核心运行环境，类型注解与异步支持依赖 |
| SQLite3 | 3.35 及以上 | 内置轻量数据库，用于存储资源元数据与检查记录 |
| requests | 2.31.0 及以上 | 发送 HTTP 健康检查请求，处理重定向与超时 |
| pyyaml | 6.0 及以上 | 解析 config.yaml 配置文件 |
| pytest | 7.4 及以上 | 单元测试与集成测试框架（仅开发环境需要） |
| flask | 2.3.0 及以上 | 提供 RESTful API 服务端点 |
| click | 8.1.0 及以上 | 命令行工具交互框架，用于自定义抓取任务 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| --- | --- | --- |
| 用户手册 | /docs/user_guide.md | 如何配置资源源文件、调整检查频率、使用导出命令 |
| API 参考 | /docs/api_reference.md | 查询接口的请求参数、响应结构、状态码与错误处理 |
| 运维指南 | /docs/operations.md | 如何部署到生产环境、配置 systemd 服务、设置日志轮转 |
| 设计概述 | /docs/architecture.md | 项目模块划分、数据流转、健康检查调度算法与扩展点 |

## 资源列表

- h5.mobile.jnjpgf.cn/Article/78452.doc
- h5.mobile.nzfnve.cn/Article/07795.doc
- h5.mobile.nwbbyt.cn/Article/31419.doc
- h5.mobile.puhvjy.cn/Article/83432.doc
- h5.mobile.cvsifc.cn/Article/4837.doc
- h5.mobile.cmcvrr.cn/Article/4718.doc
- h5.mobile.nwbbyt.cn/Article/093875.doc
- h5.mobile.fuvxie.cn/Article/36990.doc
- h5.mobile.fuvxie.cn/Article/4201907.doc
- h5.mobile.nzfnve.cn/Article/3669.doc
- h5.mobile.nwbbyt.cn/Article/1651.doc
- h5.mobile.cmcvrr.cn/Article/2804.doc
- h5.mobile.nwbbyt.cn/Article/1505151.doc
- h5.mobile.jnjpgf.cn/Article/5595.doc
- h5.mobile.hcbezg.cn/Article/2820.doc
- h5.mobile.puhvjy.cn/Article/3301.doc
- h5.mobile.jnjpgf.cn/Article/6688.doc
- h5.mobile.cvsifc.cn/Article/105132.doc
- h5.mobile.hcbezg.cn/Article/16191.doc
- h5.mobile.hcbezg.cn/Article/29020.doc
- h5.mobile.cmcvrr.cn/Article/653420.doc
- h5.mobile.cvsifc.cn/Article/6912395.doc
- h5.mobile.nwbbyt.cn/Article/02287.doc
- h5.mobile.puhvjy.cn/Article/32617.doc
- h5.mobile.hcbezg.cn/Article/97645.doc
- h5.mobile.fuvxie.cn/Article/121512.doc
- h5.mobile.nzfnve.cn/Article/7733005.doc
- h5.mobile.jnjpgf.cn/Article/06944.doc
- h5.mobile.nzfnve.cn/Article/6243815.doc
- h5.mobile.cvsifc.cn/Article/11187.doc
- h5.mobile.nwbbyt.cn/Article/2477233.doc
- h5.mobile.fuvxie.cn/Article/38839.doc
- h5.mobile.nzfnve.cn/Article/5872962.doc
- h5.mobile.cmcvrr.cn/Article/3885.doc
- h5.mobile.nwbbyt.cn/Article/65790.doc
- h5.mobile.puhvjy.cn/Article/574685.doc
- h5.mobile.fuvxie.cn/Article/707227.doc
- h5.mobile.fuvxie.cn/Article/814580.doc
- h5.mobile.puhvjy.cn/Article/952748.doc
- h5.mobile.nwbbyt.cn/Article/3744879.doc
- h5.mobile.nzfnve.cn/Article/6634523.doc
- h5.mobile.puhvjy.cn/Article/2388.doc
- h5.mobile.fuvxie.cn/Article/61049.doc
- h5.mobile.cmcvrr.cn/Article/52509.doc
- h5.mobile.nwbbyt.cn/Article/4472576.doc
- h5.mobile.puhvjy.cn/Article/7891.doc
- h5.mobile.fuvxie.cn/Article/3571.doc
- h5.mobile.nwbbyt.cn/Article/7490.doc
- h5.mobile.cvsifc.cn/Article/7169521.doc
- h5.mobile.fuvxie.cn/Article/6189.doc
- h5.mobile.hcbezg.cn/Article/77561.doc
- h5.mobile.nzfnve.cn/Article/4672358.doc
- h5.mobile.cmcvrr.cn/Article/07246.doc
- h5.mobile.nzfnve.cn/Article/006857.doc
- h5.mobile.cvsifc.cn/Article/88070.doc
- h5.mobile.nzfnve.cn/Article/725962.doc
- h5.mobile.puhvjy.cn/Article/5084.doc
- h5.mobile.nwbbyt.cn/Article/9214.doc
- h5.mobile.jnjpgf.cn/Article/095513.doc
- h5.mobile.cmcvrr.cn/Article/8590185.doc
- h5.mobile.nzfnve.cn/Article/1038875.doc
- h5.mobile.nzfnve.cn/Article/3801160.doc
- h5.mobile.puhvjy.cn/Article/2856.doc
- h5.mobile.fuvxie.cn/Article/6230.doc
- h5.mobile.puhvjy.cn/Article/217923.doc
- h5.mobile.nwbbyt.cn/Article/4759262.doc
- h5.mobile.nwbbyt.cn/Article/5339689.doc
- h5.mobile.cmcvrr.cn/Article/763604.doc
- h5.mobile.puhvjy.cn/Article/124883.doc
- h5.mobile.cmcvrr.cn/Article/3822686.doc
- h5.mobile.nwbbyt.cn/Article/28669.doc
- h5.mobile.fuvxie.cn/Article/5985562.doc
- h5.mobile.puhvjy.cn/Article/33222.doc
- h5.mobile.jnjpgf.cn/Article/146839.doc
- h5.mobile.hcbezg.cn/Article/268589.doc
- h5.mobile.fuvxie.cn/Article/9362189.doc
- h5.mobile.puhvjy.cn/Article/82310.doc
- h5.mobile.cmcvrr.cn/Article/4058.doc
- h5.mobile.hcbezg.cn/Article/613564.doc
- h5.mobile.jnjpgf.cn/Article/565445.doc
- h5.mobile.puhvjy.cn/Article/8934994.doc
- h5.mobile.cmcvrr.cn/Article/9204.doc
- h5.mobile.jnjpgf.cn/Article/2739.doc
- h5.mobile.hcbezg.cn/Article/45026.doc
- h5.mobile.fuvxie.cn/Article/179188.doc
- h5.mobile.jnjpgf.cn/Article/0299.doc
- h5.mobile.jnjpgf.cn/Article/640774.doc
- h5.mobile.puhvjy.cn/Article/755435.doc
- h5.mobile.nwbbyt.cn/Article/8864.doc
- h5.mobile.cmcvrr.cn/Article/95453.doc
- h5.mobile.nwbbyt.cn/Article/56292.doc
- h5.mobile.nzfnve.cn/Article/9080690.doc
- h5.mobile.nzfnve.cn/Article/9745.doc
- h5.mobile.nwbbyt.cn/Article/7551858.doc
- h5.mobile.hcbezg.cn/Article/7139.doc
- h5.mobile.hcbezg.cn/Article/8071.doc
- h5.mobile.nwbbyt.cn/Article/5988441.doc
- h5.mobile.cvsifc.cn/Article/52111.doc
- h5.mobile.cmcvrr.cn/Article/2375890.doc
- h5.mobile.jnjpgf.cn/Article/9428761.doc
- h5.mobile.cvsifc.cn/Article/63501.doc
- h5.mobile.nzfnve.cn/Article/6372955.doc
- h5.mobile.puhvjy.cn/Article/6195.doc
- h5.mobile.nwbbyt.cn/Article/72190.doc
- h5.mobile.fuvxie.cn/Article/686215.doc
- h5.mobile.jnjpgf.cn/Article/88763.doc
- h5.mobile.cvsifc.cn/Article/7645892.doc
- h5.mobile.hcbezg.cn/Article/22831.doc
- h5.mobile.cvsifc.cn/Article/2543.doc
- h5.mobile.cmcvrr.cn/Article/00765.doc
- h5.mobile.puhvjy.cn/Article/83967.doc
- h5.mobile.nzfnve.cn/Article/68855.doc
- h5.mobile.cvsifc.cn/Article/782511.doc
- h5.mobile.cmcvrr.cn/Article/1284320.doc
- h5.mobile.jnjpgf.cn/Article/306549.doc
- h5.mobile.cmcvrr.cn/Article/8676225.doc
- h5.mobile.nzfnve.cn/Article/628850.doc
- h5.mobile.puhvjy.cn/Article/5967.doc
- h5.mobile.cmcvrr.cn/Article/22957.doc
- h5.mobile.nzfnve.cn/Article/73146.doc
- h5.mobile.fuvxie.cn/Article/146822.doc
- h5.mobile.cmcvrr.cn/Article/534429.doc
- h5.mobile.cvsifc.cn/Article/476988.doc
- h5.mobile.puhvjy.cn/Article/3176.doc
- h5.mobile.jnjpgf.cn/Article/831893.doc
- h5.mobile.nwbbyt.cn/Article/4515893.doc
- h5.mobile.nzfnve.cn/Article/157191.doc
- h5.mobile.jnjpgf.cn/Article/535545.doc
- h5.mobile.cvsifc.cn/Article/069387.doc
- h5.mobile.fuvxie.cn/Article/4374.doc
- h5.mobile.cmcvrr.cn/Article/87189.doc
- h5.mobile.fuvxie.cn/Article/5916372.doc
- h5.mobile.cmcvrr.cn/Article/20882.doc
- h5.mobile.puhvjy.cn/Article/5106609.doc
- h5.mobile.nzfnve.cn/Article/7310.doc
- h5.mobile.nwbbyt.cn/Article/0072.doc
- h5.mobile.cvsifc.cn/Article/8898538.doc
- h5.mobile.cvsifc.cn/Article/6848079.doc
- h5.mobile.nzfnve.cn/Article/4060.doc
- h5.mobile.nzfnve.cn/Article/84517.doc
- h5.mobile.nzfnve.cn/Article/31767.doc
- h5.mobile.nwbbyt.cn/Article/8586.doc
- h5.mobile.cvsifc.cn/Article/858382.doc
- h5.mobile.jnjpgf.cn/Article/2521.doc
- h5.mobile.hcbezg.cn/Article/848819.doc
- h5.mobile.puhvjy.cn/Article/2673411.doc
- h5.mobile.nzfnve.cn/Article/848681.doc
- h5.mobile.nwbbyt.cn/Article/0346736.doc
- h5.mobile.nwbbyt.cn/Article/98023.doc
- h5.mobile.puhvjy.cn/Article/7872830.doc
- h5.mobile.fuvxie.cn/Article/099853.doc
- h5.mobile.hcbezg.cn/Article/3400835.doc
- h5.mobile.hcbezg.cn/Article/63736.doc
- h5.mobile.nwbbyt.cn/Article/481665.doc
- h5.mobile.puhvjy.cn/Article/8449.doc
- h5.mobile.fuvxie.cn/Article/954584.doc
- h5.mobile.cmcvrr.cn/Article/8573541.doc
- h5.mobile.nwbbyt.cn/Article/686523.doc
- h5.mobile.cmcvrr.cn/Article/9192377.doc
- h5.mobile.puhvjy.cn/Article/45172.doc
- h5.mobile.cvsifc.cn/Article/0941.doc
- h5.mobile.cmcvrr.cn/Article/158328.doc
- h5.mobile.nwbbyt.cn/Article/6100.doc
- h5.mobile.fuvxie.cn/Article/9211459.doc
- h5.mobile.jnjpgf.cn/Article/385971.doc
- h5.mobile.cvsifc.cn/Article/533204.doc
- h5.mobile.hcbezg.cn/Article/3314499.doc
- h5.mobile.nzfnve.cn/Article/91138.doc
- h5.mobile.nzfnve.cn/Article/40937.doc
- h5.mobile.hcbezg.cn/Article/903602.doc
- h5.mobile.cmcvrr.cn/Article/0326.doc
- h5.mobile.nwbbyt.cn/Article/1380.doc
- h5.mobile.jnjpgf.cn/Article/920058.doc
- h5.mobile.cvsifc.cn/Article/52393.doc
- h5.mobile.jnjpgf.cn/Article/440959.doc
- h5.mobile.cvsifc.cn/Article/4468333.doc
- h5.mobile.cvsifc.cn/Article/5944271.doc
- h5.mobile.jnjpgf.cn/Article/172369.doc
- h5.mobile.nzfnve.cn/Article/11781.doc
- h5.mobile.nzfnve.cn/Article/148333.doc
- h5.mobile.fuvxie.cn/Article/458921.doc
- h5.mobile.jnjpgf.cn/Article/8006435.doc
- h5.mobile.cvsifc.cn/Article/19651.doc
- h5.mobile.cmcvrr.cn/Article/4643.doc
- h5.mobile.fuvxie.cn/Article/93041.doc
- h5.mobile.puhvjy.cn/Article/935557.doc
- h5.mobile.jnjpgf.cn/Article/5951.doc
- h5.mobile.hcbezg.cn/Article/42514.doc
- h5.mobile.cmcvrr.cn/Article/1457.doc
- h5.mobile.cmcvrr.cn/Article/67421.doc
- h5.mobile.nzfnve.cn/Article/541815.doc
- h5.mobile.puhvjy.cn/Article/34711.doc
- h5.mobile.cvsifc.cn/Article/08088.doc
- h5.mobile.puhvjy.cn/Article/02203.doc
- h5.mobile.jnjpgf.cn/Article/3521.doc
- h5.mobile.fuvxie.cn/Article/328228.doc
- h5.mobile.nwbbyt.cn/Article/2197365.doc
- h5.mobile.cvsifc.cn/Article/03159.doc
- h5.mobile.fuvxie.cn/Article/29886.doc
- h5.mobile.nzfnve.cn/Article/3994.doc
- h5.mobile.fuvxie.cn/Article/785230.doc
- h5.mobile.cvsifc.cn/Article/985842.doc
- h5.mobile.puhvjy.cn/Article/73051.doc
- h5.mobile.fuvxie.cn/Article/01862.doc
- h5.mobile.fuvxie.cn/Article/628575.doc
- h5.mobile.hcbezg.cn/Article/817817.doc
- h5.mobile.hcbezg.cn/Article/704060.doc
- h5.mobile.nzfnve.cn/Article/71190.doc
- h5.mobile.cvsifc.cn/Article/40683.doc
- h5.mobile.puhvjy.cn/Article/9078029.doc
- h5.mobile.nwbbyt.cn/Article/4815.doc
- h5.mobile.cmcvrr.cn/Article/07233.doc
- h5.mobile.cmcvrr.cn/Article/38617.doc
- h5.mobile.cmcvrr.cn/Article/5862.doc
- h5.mobile.nzfnve.cn/Article/3997.doc
- h5.mobile.fuvxie.cn/Article/5449.doc
- h5.mobile.cvsifc.cn/Article/119950.doc
- h5.mobile.puhvjy.cn/Article/89222.doc
- h5.mobile.nwbbyt.cn/Article/6441156.doc
- h5.mobile.nzfnve.cn/Article/0638000.doc
- h5.mobile.nzfnve.cn/Article/879353.doc
- h5.mobile.jnjpgf.cn/Article/916306.doc
- h5.mobile.cmcvrr.cn/Article/76452.doc
- h5.mobile.hcbezg.cn/Article/4921660.doc
- h5.mobile.hcbezg.cn/Article/3523784.doc
- h5.mobile.jnjpgf.cn/Article/1914.doc
- h5.mobile.cvsifc.cn/Article/30656.doc
- h5.mobile.nzfnve.cn/Article/5032277.doc
- h5.mobile.jnjpgf.cn/Article/2926884.doc
- h5.mobile.nzfnve.cn/Article/07800.doc
- h5.mobile.cvsifc.cn/Article/251623.doc
- h5.mobile.puhvjy.cn/Article/3373750.doc
- h5.mobile.jnjpgf.cn/Article/14346.doc
- h5.mobile.cvsifc.cn/Article/1623.doc
- h5.mobile.hcbezg.cn/Article/433201.doc
- h5.mobile.hcbezg.cn/Article/8572.doc
- h5.mobile.fuvxie.cn/Article/2325.doc
- h5.mobile.fuvxie.cn/Article/33832.doc
- h5.mobile.nzfnve.cn/Article/645463.doc
- h5.mobile.jnjpgf.cn/Article/9784640.doc
- h5.mobile.cmcvrr.cn/Article/5774929.doc
- h5.mobile.hcbezg.cn/Article/62233.doc
- h5.mobile.cmcvrr.cn/Article/9601.doc
- h5.mobile.cmcvrr.cn/Article/7662162.doc
- h5.mobile.cvsifc.cn/Article/1894780.doc
- h5.mobile.nzfnve.cn/Article/0262897.doc
- h5.mobile.nwbbyt.cn/Article/25241.doc
- h5.mobile.cvsifc.cn/Article/3643644.doc
- h5.mobile.hcbezg.cn/Article/6993126.doc
- h5.mobile.nzfnve.cn/Article/748436.doc

## 项目结构

```
doclink-hive/
├── app.py                      # Flask API 服务入口，注册路由与启动
├── config.yaml                 # 用户配置文件，包含源文件路径、检查间隔、日志级别
├── requirements.txt            # Python 依赖清单，固定版本号
├── data/                       # 数据存储目录
│   ├── source_urls.txt         # 原始资源链接列表，每行一个 URL
│   └── archive/                # 历史版本归档，按日期存放变更记录
├── core/                       # 核心逻辑模块
│   ├── loader.py               # 从源文件读取并去重 URL，返回规范化列表
│   ├── classifier.py           # 基于域名与路径关键词的标签生成器
│   ├── checker.py              # 异步健康检查器，管理并发请求与超时重试
│   └── exporter.py             # 导出为 Markdown、JSON、CSV 格式的工具
├── storage/                    # 持久化层
│   ├── db.py                   # SQLite 连接池与表结构初始化
│   ├── models.py               # 资源记录的数据类定义与序列化方法
│   └── migrations/             # 数据库迁移脚本（版本递增）
├── api/                        # API 接口定义
│   ├── routes.py               # 路由处理器，参数校验与响应封装
│   └── schemas.py              # 请求/响应 JSON Schema 定义
├── scripts/                    # 运维与辅助脚本
│   ├── init_db.py              # 首次启动时创建空数据库与默认表
│   └── import_batch.py         # 批量导入外部来源列表（支持 CSV 与 TXT）
├── tests/                      # 测试套件
│   ├── test_loader.py          # 覆盖边界情况：空行、重复、异常协议
│   ├── test_checker.py         # 模拟 HTTP 状态码，验证重试与超时逻辑
│   └── test_api.py             # API 端点的功能测试与性能基准
├── docs/                       # 项目文档（参考文档导航章节）
└── LICENSE                     # MIT 许可文本
```

## 贡献指南

提交 Issue 报告新功能建议或缺陷：请使用 GitHub Issue 模板，标注类别为 enhancement 或 bug，并附上复现步骤或日志片段。

创建功能分支并遵循代码规范：从 main 分支签出 feature/xxx 分支，代码提交前运行 black 与 flake8 格式化检查，确保测试用例通过。

编写或更新单元测试：新增功能需在 tests/ 目录下补充对应测试文件，覆盖率不低于 80%，提交时附带测试执行截图或日志。

更新文档与示例配置：若修改了配置项或 API 接口，请同步更新 docs/ 下对应的用户手册与 API 参考文档，并在 config.example.yaml 中标注变更。

发起 Pull Request 并关联 Issue：PR 描述中写明解决的 Issue 编号，简要说明实现思路与影响范围，等待维护者审阅。

## 常见问题

服务启动后无法连接 SQLite 数据库，提示权限错误。
检查 data/ 目录是否存在且当前用户具有读写权限。若目录不存在，请手动创建 data/ 文件夹并重新执行 init_db.py。若使用 Docker 挂载卷，请确认宿主机目录权限映射正确。

健康检查返回大量 404 状态码，但手动访问浏览器可正常打开。
部分外部站点可能对 Head 请求返回 405 或不支持 Head 方法。可在 config.yaml 中将 check_method 修改为 get，并启用 allow_redirects 选项。若仍异常，请检查目标站点是否对 User-Agent 有过滤规则，可在配置中自定义 headers。

如何迁移已录入的资源数据到另一台服务器。
直接复制 data/doclink.db 文件到新服务器的 data/ 目录即可。若需同时迁移配置文件，请一并复制 config.yaml。数据库文件为 SQLite 单文件格式，兼容跨平台。迁移后建议运行一次完整健康检查以验证数据完整性。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

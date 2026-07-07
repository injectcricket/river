# DocHub Mobile Resource Aggregator

DocHub Mobile Resource Aggregator 是一个面向移动端开发者和内容研究者的轻量化文档资源聚合系统。该项目专注于收集、索引和提供可访问的移动端文档链接资源，帮助开发者快速定位分散于多个内容源的技术文档、产品说明和行业报告。项目定位于技术资源的外链汇总与管理，不存储任何实际文档内容，仅提供原始链接的检索与分类服务。目标用户包括移动应用开发人员、技术文档工程师、产品经理以及需要进行移动端内容聚合的研究人员。

## 功能概览

**分布式链接索引**：系统基于多级目录结构对海量文档链接进行哈希索引，支持按来源域名和文档编号进行快速检索。

**来源域名分类过滤**：内置多个内容来源域名分类规则，可根据文档来源域名（如 fuvxie.cn、puhvjy.cn、jnjpgf.cn 等）进行资源筛选与统计。

**批量链接导入导出**：支持通过命令行工具或 API 接口批量导入纯文本链接列表，并支持将索引结果导出为标准 CSV 或 JSON 格式。

**链接可用性健康检查**：提供周期性的链接存活检测功能，自动标记失效或重定向的链接，生成健康报告。

**只读原始链接输出**：系统严格遵循原始链接输出规范，不对任何外链进行改写、补全或格式化包装，保证链接的原始性和可追溯性。

**命令行与 Web 双模式**：既提供轻量级的 CLI 工具供开发者在终端中快速操作，也提供基础的 Web 管理界面供非技术用户进行资源浏览。

**多格式资源清单生成**：支持将索引资源按 Markdown、HTML 表格或纯文本列表等格式输出，方便集成到文档站点或 README 中。

## 应用场景

移动端开发文档的日常查阅与整理：开发者在进行移动端 SDK 集成或 API 调用时，可通过本系统快速检索分散在多个域名下的技术文档链接，无需逐一手动记忆或查找收藏夹。

技术文档团队的外链资产管理：文档工程师可使用本系统对项目组积累的数百个外链资源进行统一登记、分类和可用性监控，避免链接失效导致的信息丢失。

产品竞品分析报告的资源汇总：产品经理在撰写移动端竞品分析报告时，可将收集到的各竞品官方文档、用户协议、版本更新记录等链接通过本系统集中管理，并一键导出资源清单。

自动化测试中的测试用例数据源：QA 工程师可编写脚本调用本系统的导出接口，将链接列表作为自动化测试的数据源，用于校验各个文档页面的可访问性和响应状态。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/dochub-mobile/doc-aggregator.git

# 进入项目目录
cd doc-aggregator

# 安装依赖（使用 pip 进行 Python 依赖安装）
pip install -r requirements.txt

# 初始化本地索引数据库
python manage.py initdb

# 导入示例资源链接（将链接列表保存为 links.txt 后执行）
python manage.py import --file links.txt

# 启动本地 Web 服务（默认监听 8000 端口）
python manage.py runserver --port 8000
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，用于 CLI 工具和 Web 服务 |
| SQLite | 3.28 及以上 | 本地索引数据库引擎，无需额外安装 |
| pip | 20.0 及以上 | Python 包管理器，用于安装项目依赖 |
| requests | 2.25.0 及以上 | 用于链接健康检查的 HTTP 请求库 |
| click | 8.0.0 及以上 | CLI 命令行交互框架，提供子命令解析 |
| flask | 2.0.0 及以上 | Web 管理界面后端框架（可选，仅 Web 模式需要） |
| pytest | 6.0.0 及以上 | 单元测试框架（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide.md | 如何安装、配置、导入链接、启动服务以及日常使用流程 |
| API 参考 | /docs/api-reference.md | 系统提供了哪些 RESTful API 接口，请求格式与返回结构是什么 |
| 运维指南 | /docs/ops-guide.md | 如何部署生产环境、配置反向代理、进行数据备份和迁移 |
| 开发指南 | /docs/dev-guide.md | 项目代码结构、开发环境搭建、单元测试编写与 PR 提交流程 |

## 资源列表

- h5.mobile.fuvxie.cn/Article/7742415.doc
- h5.mobile.puhvjy.cn/Article/6316.doc
- h5.mobile.jnjpgf.cn/Article/3851695.doc
- h5.mobile.hcbezg.cn/Article/6661222.doc
- h5.mobile.jnjpgf.cn/Article/765353.doc
- h5.mobile.nzfnve.cn/Article/0118316.doc
- h5.mobile.puhvjy.cn/Article/9210.doc
- h5.mobile.puhvjy.cn/Article/2765.doc
- h5.mobile.jnjpgf.cn/Article/7899249.doc
- h5.mobile.fuvxie.cn/Article/1234.doc
- h5.mobile.cvsifc.cn/Article/9290834.doc
- h5.mobile.hcbezg.cn/Article/8478095.doc
- h5.mobile.nzfnve.cn/Article/845196.doc
- h5.mobile.nwbbyt.cn/Article/704979.doc
- h5.mobile.cmcvrr.cn/Article/1791.doc
- h5.mobile.hcbezg.cn/Article/4274.doc
- h5.mobile.fuvxie.cn/Article/0399.doc
- h5.mobile.hcbezg.cn/Article/1798748.doc
- h5.mobile.cmcvrr.cn/Article/8796935.doc
- h5.mobile.puhvjy.cn/Article/4768.doc
- h5.mobile.cvsifc.cn/Article/984291.doc
- h5.mobile.jnjpgf.cn/Article/642974.doc
- h5.mobile.puhvjy.cn/Article/4436.doc
- h5.mobile.cvsifc.cn/Article/8795114.doc
- h5.mobile.nzfnve.cn/Article/0956309.doc
- h5.mobile.jnjpgf.cn/Article/399912.doc
- h5.mobile.nwbbyt.cn/Article/77368.doc
- h5.mobile.fuvxie.cn/Article/1942457.doc
- h5.mobile.jnjpgf.cn/Article/9760575.doc
- h5.mobile.hcbezg.cn/Article/733758.doc
- h5.mobile.hcbezg.cn/Article/3073617.doc
- h5.mobile.hcbezg.cn/Article/4023.doc
- h5.mobile.nzfnve.cn/Article/861609.doc
- h5.mobile.jnjpgf.cn/Article/2214234.doc
- h5.mobile.cvsifc.cn/Article/52194.doc
- h5.mobile.cmcvrr.cn/Article/1577763.doc
- h5.mobile.nwbbyt.cn/Article/140192.doc
- h5.mobile.puhvjy.cn/Article/4178561.doc
- h5.mobile.nwbbyt.cn/Article/922322.doc
- h5.mobile.puhvjy.cn/Article/95896.doc
- h5.mobile.puhvjy.cn/Article/033287.doc
- h5.mobile.puhvjy.cn/Article/47742.doc
- h5.mobile.nwbbyt.cn/Article/72959.doc
- h5.mobile.puhvjy.cn/Article/203327.doc
- h5.mobile.cvsifc.cn/Article/175878.doc
- h5.mobile.fuvxie.cn/Article/07430.doc
- h5.mobile.puhvjy.cn/Article/4355925.doc
- h5.mobile.cmcvrr.cn/Article/7919.doc
- h5.mobile.cvsifc.cn/Article/1910099.doc
- h5.mobile.puhvjy.cn/Article/6317.doc
- h5.mobile.nzfnve.cn/Article/56135.doc
- h5.mobile.puhvjy.cn/Article/9880759.doc
- h5.mobile.puhvjy.cn/Article/0491438.doc
- h5.mobile.cvsifc.cn/Article/2243.doc
- h5.mobile.puhvjy.cn/Article/4189871.doc
- h5.mobile.hcbezg.cn/Article/470382.doc
- h5.mobile.fuvxie.cn/Article/223466.doc
- h5.mobile.nwbbyt.cn/Article/184899.doc
- h5.mobile.fuvxie.cn/Article/9936.doc
- h5.mobile.cvsifc.cn/Article/676476.doc
- h5.mobile.cmcvrr.cn/Article/064329.doc
- h5.mobile.fuvxie.cn/Article/39870.doc
- h5.mobile.nwbbyt.cn/Article/54862.doc
- h5.mobile.cvsifc.cn/Article/9172725.doc
- h5.mobile.puhvjy.cn/Article/932768.doc
- h5.mobile.jnjpgf.cn/Article/4561500.doc
- h5.mobile.fuvxie.cn/Article/866369.doc
- h5.mobile.hcbezg.cn/Article/0346.doc
- h5.mobile.cmcvrr.cn/Article/9786855.doc
- h5.mobile.fuvxie.cn/Article/990286.doc
- h5.mobile.cvsifc.cn/Article/9462.doc
- h5.mobile.jnjpgf.cn/Article/6480170.doc
- h5.mobile.puhvjy.cn/Article/21089.doc
- h5.mobile.jnjpgf.cn/Article/4169.doc
- h5.mobile.hcbezg.cn/Article/7936.doc
- h5.mobile.jnjpgf.cn/Article/8298109.doc
- h5.mobile.fuvxie.cn/Article/297439.doc
- h5.mobile.cvsifc.cn/Article/6426715.doc
- h5.mobile.nwbbyt.cn/Article/9540761.doc
- h5.mobile.hcbezg.cn/Article/742298.doc
- h5.mobile.fuvxie.cn/Article/9388661.doc
- h5.mobile.cmcvrr.cn/Article/103984.doc
- h5.mobile.hcbezg.cn/Article/06997.doc
- h5.mobile.nzfnve.cn/Article/6883803.doc
- h5.mobile.nwbbyt.cn/Article/698978.doc
- h5.mobile.hcbezg.cn/Article/5138730.doc
- h5.mobile.jnjpgf.cn/Article/017442.doc
- h5.mobile.cvsifc.cn/Article/2676013.doc
- h5.mobile.cvsifc.cn/Article/9383018.doc
- h5.mobile.nwbbyt.cn/Article/73568.doc
- h5.mobile.hcbezg.cn/Article/89574.doc
- h5.mobile.nzfnve.cn/Article/11386.doc
- h5.mobile.jnjpgf.cn/Article/63805.doc
- h5.mobile.nwbbyt.cn/Article/00142.doc
- h5.mobile.nzfnve.cn/Article/73775.doc
- h5.mobile.hcbezg.cn/Article/6245028.doc
- h5.mobile.puhvjy.cn/Article/33952.doc
- h5.mobile.fuvxie.cn/Article/011917.doc
- h5.mobile.cvsifc.cn/Article/269364.doc
- h5.mobile.cmcvrr.cn/Article/5351685.doc
- h5.mobile.fuvxie.cn/Article/0428402.doc
- h5.mobile.puhvjy.cn/Article/3488.doc
- h5.mobile.hcbezg.cn/Article/7005.doc
- h5.mobile.cvsifc.cn/Article/9690701.doc
- h5.mobile.cmcvrr.cn/Article/0131597.doc
- h5.mobile.jnjpgf.cn/Article/6062.doc
- h5.mobile.cvsifc.cn/Article/3691.doc
- h5.mobile.puhvjy.cn/Article/534274.doc
- h5.mobile.puhvjy.cn/Article/377057.doc
- h5.mobile.fuvxie.cn/Article/5281513.doc
- h5.mobile.cvsifc.cn/Article/40043.doc
- h5.mobile.nwbbyt.cn/Article/959845.doc
- h5.mobile.cmcvrr.cn/Article/97610.doc
- h5.mobile.nwbbyt.cn/Article/042363.doc
- h5.mobile.hcbezg.cn/Article/1828.doc
- h5.mobile.jnjpgf.cn/Article/2103.doc
- h5.mobile.cvsifc.cn/Article/887562.doc
- h5.mobile.hcbezg.cn/Article/02484.doc
- h5.mobile.cvsifc.cn/Article/9047408.doc
- h5.mobile.nzfnve.cn/Article/13993.doc
- h5.mobile.nwbbyt.cn/Article/10140.doc
- h5.mobile.jnjpgf.cn/Article/0522.doc
- h5.mobile.fuvxie.cn/Article/0991390.doc
- h5.mobile.fuvxie.cn/Article/7335.doc
- h5.mobile.nwbbyt.cn/Article/2929853.doc
- h5.mobile.nwbbyt.cn/Article/2395163.doc
- h5.mobile.fuvxie.cn/Article/11335.doc
- h5.mobile.hcbezg.cn/Article/4427.doc
- h5.mobile.puhvjy.cn/Article/5539.doc
- h5.mobile.nwbbyt.cn/Article/0237469.doc
- h5.mobile.hcbezg.cn/Article/553765.doc
- h5.mobile.nwbbyt.cn/Article/38630.doc
- h5.mobile.cvsifc.cn/Article/8162330.doc
- h5.mobile.nwbbyt.cn/Article/14313.doc
- h5.mobile.nzfnve.cn/Article/0823983.doc
- h5.mobile.nzfnve.cn/Article/61006.doc
- h5.mobile.hcbezg.cn/Article/80718.doc
- h5.mobile.puhvjy.cn/Article/2202.doc
- h5.mobile.cvsifc.cn/Article/2725073.doc
- h5.mobile.jnjpgf.cn/Article/86259.doc
- h5.mobile.hcbezg.cn/Article/9776336.doc
- h5.mobile.jnjpgf.cn/Article/17767.doc
- h5.mobile.jnjpgf.cn/Article/1308255.doc
- h5.mobile.cmcvrr.cn/Article/9527.doc
- h5.mobile.puhvjy.cn/Article/7092.doc
- h5.mobile.cmcvrr.cn/Article/299396.doc
- h5.mobile.puhvjy.cn/Article/347113.doc
- h5.mobile.cmcvrr.cn/Article/246568.doc
- h5.mobile.puhvjy.cn/Article/4394703.doc
- h5.mobile.fuvxie.cn/Article/2775.doc
- h5.mobile.nwbbyt.cn/Article/2384.doc
- h5.mobile.nzfnve.cn/Article/693387.doc
- h5.mobile.puhvjy.cn/Article/87922.doc
- h5.mobile.fuvxie.cn/Article/3232109.doc
- h5.mobile.puhvjy.cn/Article/06286.doc
- h5.mobile.cvsifc.cn/Article/0066.doc
- h5.mobile.cvsifc.cn/Article/87142.doc
- h5.mobile.cmcvrr.cn/Article/5398518.doc
- h5.mobile.fuvxie.cn/Article/4342535.doc
- h5.mobile.fuvxie.cn/Article/31527.doc
- h5.mobile.nzfnve.cn/Article/530097.doc
- h5.mobile.nzfnve.cn/Article/8592560.doc
- h5.mobile.jnjpgf.cn/Article/631737.doc
- h5.mobile.jnjpgf.cn/Article/0037149.doc
- h5.mobile.cmcvrr.cn/Article/7376.doc
- h5.mobile.cvsifc.cn/Article/0206659.doc
- h5.mobile.puhvjy.cn/Article/769504.doc
- h5.mobile.fuvxie.cn/Article/181091.doc
- h5.mobile.hcbezg.cn/Article/951877.doc
- h5.mobile.jnjpgf.cn/Article/18601.doc
- h5.mobile.puhvjy.cn/Article/5786879.doc
- h5.mobile.fuvxie.cn/Article/291110.doc
- h5.mobile.nzfnve.cn/Article/8886.doc
- h5.mobile.jnjpgf.cn/Article/7053354.doc
- h5.mobile.fuvxie.cn/Article/52392.doc
- h5.mobile.cmcvrr.cn/Article/7962729.doc
- h5.mobile.puhvjy.cn/Article/70605.doc
- h5.mobile.cvsifc.cn/Article/9449.doc
- h5.mobile.fuvxie.cn/Article/02633.doc
- h5.mobile.fuvxie.cn/Article/0973168.doc
- h5.mobile.nzfnve.cn/Article/4634764.doc
- h5.mobile.jnjpgf.cn/Article/9988509.doc
- h5.mobile.jnjpgf.cn/Article/2495.doc
- h5.mobile.jnjpgf.cn/Article/68039.doc
- h5.mobile.fuvxie.cn/Article/495564.doc
- h5.mobile.jnjpgf.cn/Article/048207.doc
- h5.mobile.cmcvrr.cn/Article/814360.doc
- h5.mobile.nzfnve.cn/Article/6149845.doc
- h5.mobile.fuvxie.cn/Article/7222.doc
- h5.mobile.cvsifc.cn/Article/72801.doc
- h5.mobile.hcbezg.cn/Article/3661030.doc
- h5.mobile.puhvjy.cn/Article/9364174.doc
- h5.mobile.hcbezg.cn/Article/089396.doc
- h5.mobile.fuvxie.cn/Article/02879.doc
- h5.mobile.nwbbyt.cn/Article/4896280.doc
- h5.mobile.fuvxie.cn/Article/132281.doc
- h5.mobile.cmcvrr.cn/Article/9319.doc
- h5.mobile.nwbbyt.cn/Article/05996.doc
- h5.mobile.hcbezg.cn/Article/5982376.doc
- h5.mobile.puhvjy.cn/Article/586699.doc
- h5.mobile.fuvxie.cn/Article/66405.doc
- h5.mobile.cvsifc.cn/Article/94756.doc
- h5.mobile.nzfnve.cn/Article/70289.doc
- h5.mobile.jnjpgf.cn/Article/7040425.doc
- h5.mobile.cvsifc.cn/Article/7286.doc
- h5.mobile.nwbbyt.cn/Article/036533.doc
- h5.mobile.nzfnve.cn/Article/5067.doc
- h5.mobile.nzfnve.cn/Article/0235192.doc
- h5.mobile.nzfnve.cn/Article/2756674.doc
- h5.mobile.cvsifc.cn/Article/62342.doc
- h5.mobile.cvsifc.cn/Article/6188252.doc
- h5.mobile.nwbbyt.cn/Article/8573579.doc
- h5.mobile.hcbezg.cn/Article/660865.doc
- h5.mobile.cvsifc.cn/Article/190658.doc
- h5.mobile.nwbbyt.cn/Article/6848.doc
- h5.mobile.jnjpgf.cn/Article/594446.doc
- h5.mobile.fuvxie.cn/Article/7689.doc
- h5.mobile.fuvxie.cn/Article/35843.doc
- h5.mobile.cvsifc.cn/Article/7081391.doc
- h5.mobile.fuvxie.cn/Article/4912.doc
- h5.mobile.fuvxie.cn/Article/7089560.doc
- h5.mobile.nzfnve.cn/Article/70290.doc
- h5.mobile.puhvjy.cn/Article/1178036.doc
- h5.mobile.cmcvrr.cn/Article/7997.doc
- h5.mobile.cmcvrr.cn/Article/7516.doc
- h5.mobile.jnjpgf.cn/Article/9895.doc
- h5.mobile.cmcvrr.cn/Article/390414.doc
- h5.mobile.puhvjy.cn/Article/9457.doc
- h5.mobile.cmcvrr.cn/Article/1221.doc
- h5.mobile.fuvxie.cn/Article/8387228.doc
- h5.mobile.fuvxie.cn/Article/19963.doc
- h5.mobile.nwbbyt.cn/Article/063185.doc
- h5.mobile.hcbezg.cn/Article/4254.doc
- h5.mobile.cvsifc.cn/Article/1625965.doc
- h5.mobile.cmcvrr.cn/Article/0604.doc
- h5.mobile.jnjpgf.cn/Article/0142099.doc
- h5.mobile.cmcvrr.cn/Article/0236.doc
- h5.mobile.puhvjy.cn/Article/878680.doc
- h5.mobile.cvsifc.cn/Article/293144.doc
- h5.mobile.fuvxie.cn/Article/310062.doc
- h5.mobile.jnjpgf.cn/Article/283011.doc
- h5.mobile.nwbbyt.cn/Article/1100727.doc
- h5.mobile.cmcvrr.cn/Article/963086.doc
- h5.mobile.jnjpgf.cn/Article/838617.doc
- h5.mobile.nzfnve.cn/Article/0097842.doc
- h5.mobile.hcbezg.cn/Article/189471.doc
- h5.mobile.fuvxie.cn/Article/13989.doc
- h5.mobile.puhvjy.cn/Article/8731.doc
- h5.mobile.cmcvrr.cn/Article/72129.doc
- h5.mobile.puhvjy.cn/Article/5710.doc

## 项目结构

```
doc-aggregator/
├── cli/                                 # 命令行工具模块
│   ├── commands/                        # 子命令实现目录
│   │   ├── import_cmd.py                # 导入链接子命令实现
│   │   ├── export_cmd.py                # 导出资源清单子命令实现
│   │   ├── health_cmd.py                # 链接健康检查子命令实现
│   │   └── init_cmd.py                  # 数据库初始化子命令实现
│   └── main.py                          # CLI 入口与命令注册
├── core/                                # 核心业务逻辑层
│   ├── indexer.py                       # 链接索引引擎，负责哈希生成与去重
│   ├── checker.py                       # 链接可用性检查器，包含 HTTP 探活逻辑
│   ├── parser.py                        # 链接解析器，负责域名提取与分类
│   └── exporter.py                      # 多格式导出引擎，支持 MD/CSV/JSON
├── web/                                 # Web 管理界面模块
│   ├── static/                          # 静态资源目录（CSS / JS）
│   ├── templates/                       # Jinja2 模板目录
│   │   ├── index.html                   # 资源总览首页模板
│   │   ├── detail.html                  # 单条链接详情页模板
│   │   └── report.html                  # 健康报告页模板
│   └── app.py                           # Flask 应用主文件，路由与视图函数
├── storage/                             # 持久化存储层
│   ├── db.py                            # SQLite 数据库连接与 CRUD 操作封装
│   ├── schema.sql                       # 数据库建表语句（links / domains / checks）
│   └── migrations/                      # 数据库迁移脚本目录
│       ├── 001_initial.sql              # 初始版本建表迁移
│       └── 002_add_index.sql            # 增加索引优化查询性能
├── tests/                               # 单元测试与集成测试目录
│   ├── test_indexer.py                  # 索引引擎单元测试
│   ├── test_checker.py                  # 健康检查单元测试
│   └── test_cli.py                      # CLI 命令集成测试
├── config/                              # 配置文件目录
│   ├── default.yaml                     # 默认配置（日志级别、服务端口）
│   └── production.yaml                  # 生产环境覆盖配置
├── docs/                                # 项目文档目录
│   ├── user-guide.md                    # 用户手册
│   ├── api-reference.md                 # API 接口文档
│   └── dev-guide.md                     # 开发者指南
├── scripts/                             # 辅助运维脚本
│   ├── backup.sh                        # 数据库备份脚本
│   └── deploy.sh                        # 一键部署脚本（用于生产环境）
├── requirements.txt                     # Python 依赖声明文件
├── setup.py                             # 项目安装与分发配置文件
└── README.md                            # 项目入口文档（本文件）
```

## 贡献指南

提交 Issue 报告问题或提出改进建议：访问 GitHub 仓库的 Issues 页面，使用提供的模板详细描述遇到的问题或期望的新功能，并附上复现步骤或使用场景说明。

Fork 仓库并创建功能分支：点击 GitHub 页面右上角的 Fork 按钮将项目复制到自己的账户下，然后使用 git checkout -b feature/your-feature-name 创建本地功能分支进行开发。

编写代码并添加单元测试：在实现新功能或修复 Bug 时，需在 tests/ 目录下对应的测试文件中补充测试用例，确保 pytest 执行后全部测试通过且代码覆盖率不低于 80%。

提交 Pull Request 并描述改动内容：完成开发后将本地分支推送至自己的远程仓库，然后向主仓库的 main 分支提交 PR，在 PR 描述中清晰列出改动点、关联 Issue 编号以及测试结果截图。

遵循代码风格规范：项目使用 PEP 8 作为 Python 代码风格标准，提交前需执行 flake8 和 black 进行格式检查，确保代码风格一致。

## 常见问题

Q: 系统是否存储或缓存外部文档的实际内容？
A: 系统不存储任何外部文档的二进制内容或文本内容，仅保存文档链接的 URL 字符串及其元数据（如域名、导入时间、最近检查状态）。所有文档内容均需通过原始链接访问。

Q: 如何批量更新链接的健康检查状态？
A: 可使用 python manage.py health --batch-size 50 --timeout 5 命令进行批量检查，系统会以每批 50 个链接的并发数进行 HTTP 请求，超时时间设置为 5 秒。检查结果会写入数据库并在 Web 界面的报告中展示。

Q: 导入大量链接时是否会因为重复而失败？
A: 导入命令默认基于链接完整字符串进行去重。如果数据库已存在完全相同的 URL，则跳过该条记录并记录警告日志，不会中断整体导入流程。建议在导入前使用 export 命令导出已有列表进行比对。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

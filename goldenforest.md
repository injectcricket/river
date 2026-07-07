# DocArchive Link Aggregator

DocArchive Link Aggregator 是一个面向技术文档、行业报告与学术资料的外链管理平台，用于对大规模分布式文档资源进行统一索引、分类存储与快速检索。本项目的核心定位是作为技术资源汇总站，帮助开发者、研究人员与技术运营人员从繁杂的 URL 集合中高效定位所需文档，降低信息管理成本。

项目面向的用户群体包括技术团队内部知识库维护者、开源社区文档贡献者、学术资料整理人员以及需要定期归档外部文档链接的运营人员。通过本系统，用户可以对超过 200 个外部文档链接进行集中管理，支持按来源域名、文档类型、更新日期等多维度筛选，并提供完整的导入、导出与状态监控能力。本项目的设计原则强调零外部依赖、轻量化部署与纯静态资源访问，适合各类内网或公网环境下的文档链接管理需求。

## 功能概览

文档链接批量导入：支持通过文本文件或标准输入流批量导入文档 URL，自动解析来源域名与文档编号，生成内部唯一标识。

多维度筛选与检索：基于文档来源域名、文档编号区间、导入时间等条件进行组合筛选，支持模糊匹配与精确匹配两种检索模式。

链接可达性健康检查：定时对已收录的文档链接进行 HTTP 请求验证，自动标记失效链接并生成异常报告，便于运维人员及时清理或更新。

标签分类与备注管理：允许用户为每条文档链接添加自定义标签（如“技术手册”、“行业白皮书”、“会议论文”）和文字备注，便于后期归类整理。

数据导入导出：支持将当前链接列表导出为 CSV 或 JSON 格式，也支持从外部数据源导入链接清单，便于与其它系统进行数据交换。

访问统计与日志：记录每条文档链接的访问次数、最后访问时间与访问来源 IP 段，提供基础的访问热度分析能力。

权限分级控制：提供管理员、编辑者与访客三级权限体系，管理员可执行链接增删改操作，编辑者可修改备注与标签，访客仅可查看与检索。

## 应用场景

企业内部知识库文档汇总：技术团队在日常工作中会积累大量分散在各部门文档服务器上的技术方案、设计文档与运维手册。通过 DocArchive，团队可以将这些文档的外部链接统一收录，并按照项目或业务模块进行分类，形成集中化的知识入口。

学术研究资料整理：研究人员在文献调研过程中需要收集大量来自不同来源的论文、技术报告与数据集说明文档。使用本系统可以快速建立个人文献链接库，并通过标签和备注功能记录每篇文献的核心要点，避免重复检索。

开源项目文档镜像站维护：开源社区在维护项目文档时，往往需要引用多个外部资源，包括 API 参考手册、部署指南与第三方依赖说明。本系统可作为文档链接的中转站，确保所有引用链接的统一管理和定期健康检查，减少文档中的死链问题。

技术运营内容聚合：技术博客或在线教育平台在发布内容时，需要引用大量外部参考资料。运营人员可使用本系统预先整理所有参考链接，在内容发布前完成链接的有效性验证，并在发布后持续监控链接状态。

## 快速开始

以下步骤帮助您在本地环境中快速启动 DocArchive Link Aggregator 服务。

```bash
# 克隆项目仓库至本地
git clone https://github.com/docarchive/link-aggregator.git

# 进入项目根目录
cd link-aggregator

# 安装项目依赖（使用 pip 包管理器）
pip install -r requirements.txt

# 初始化本地数据库（SQLite）
python scripts/init_db.py

# 启动开发服务器，默认监听 127.0.0.1:8080
python app.py
```

服务启动后，访问 http://127.0.0.1:8080 即可进入文档链接管理界面。首次启动将自动创建默认管理员账户，用户名与密码在控制台启动日志中输出，请及时保存并修改。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，提供 Web 服务与数据处理能力 |
| SQLite | 3.31.0 及以上 | 内嵌数据库，用于存储文档链接元数据与用户信息 |
| pip | 20.0 及以上 | Python 包管理工具，用于安装项目依赖库 |
| Flask | 2.2.0 及以上 | Web 框架，处理 HTTP 请求与路由分发 |
| requests | 2.25.0 及以上 | HTTP 客户端库，用于执行文档链接可达性健康检查 |
| pytest | 7.0.0 及以上 | 单元测试框架，用于运行项目自带测试用例（可选） |
| gunicorn | 20.1.0 及以上 | 生产环境 WSGI 服务器，用于多进程部署（可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide.md | 如何导入文档链接、如何添加标签与备注、如何执行链接健康检查 |
| 管理员指南 | /docs/admin-guide.md | 如何进行用户权限管理、如何配置定时任务、如何执行数据备份与恢复 |
| 开发文档 | /docs/developer-guide.md | 项目整体架构设计、API 接口规范、如何扩展新的数据导入格式 |
| 部署手册 | /docs/deployment-guide.md | 如何将项目部署至生产服务器、如何配置 HTTPS、如何调优性能参数 |
| 常见问题 | /docs/faq.md | 链接无法访问的原因排查、数据库迁移方法、性能瓶颈诊断方案 |

## 资源列表

- h5.mobile.hcbezg.cn/Article/1109.doc
- h5.mobile.fuvxie.cn/Article/68786.doc
- h5.mobile.puhvjy.cn/Article/6348791.doc
- h5.mobile.cmcvrr.cn/Article/355719.doc
- h5.mobile.puhvjy.cn/Article/58709.doc
- h5.mobile.jnjpgf.cn/Article/9815.doc
- h5.mobile.puhvjy.cn/Article/9275.doc
- h5.mobile.puhvjy.cn/Article/455562.doc
- h5.mobile.nzfnve.cn/Article/5290171.doc
- h5.mobile.nwbbyt.cn/Article/4038.doc
- h5.mobile.cmcvrr.cn/Article/28230.doc
- h5.mobile.cmcvrr.cn/Article/97838.doc
- h5.mobile.cmcvrr.cn/Article/93883.doc
- h5.mobile.cmcvrr.cn/Article/8781262.doc
- h5.mobile.puhvjy.cn/Article/397259.doc
- h5.mobile.jnjpgf.cn/Article/4070610.doc
- h5.mobile.jnjpgf.cn/Article/33366.doc
- h5.mobile.jnjpgf.cn/Article/630019.doc
- h5.mobile.cmcvrr.cn/Article/0628521.doc
- h5.mobile.cmcvrr.cn/Article/026879.doc
- h5.mobile.hcbezg.cn/Article/5272.doc
- h5.mobile.nzfnve.cn/Article/3519.doc
- h5.mobile.cmcvrr.cn/Article/6112.doc
- h5.mobile.fuvxie.cn/Article/17145.doc
- h5.mobile.hcbezg.cn/Article/64289.doc
- h5.mobile.jnjpgf.cn/Article/1300290.doc
- h5.mobile.jnjpgf.cn/Article/582548.doc
- h5.mobile.nwbbyt.cn/Article/382811.doc
- h5.mobile.hcbezg.cn/Article/5421860.doc
- h5.mobile.fuvxie.cn/Article/1456295.doc
- h5.mobile.jnjpgf.cn/Article/49427.doc
- h5.mobile.fuvxie.cn/Article/36428.doc
- h5.mobile.cvsifc.cn/Article/07671.doc
- h5.mobile.puhvjy.cn/Article/197109.doc
- h5.mobile.fuvxie.cn/Article/399080.doc
- h5.mobile.fuvxie.cn/Article/60715.doc
- h5.mobile.nzfnve.cn/Article/4422.doc
- h5.mobile.puhvjy.cn/Article/85908.doc
- h5.mobile.cvsifc.cn/Article/6497.doc
- h5.mobile.fuvxie.cn/Article/3514.doc
- h5.mobile.fuvxie.cn/Article/9346321.doc
- h5.mobile.puhvjy.cn/Article/13785.doc
- h5.mobile.fuvxie.cn/Article/808148.doc
- h5.mobile.hcbezg.cn/Article/129350.doc
- h5.mobile.jnjpgf.cn/Article/9312836.doc
- h5.mobile.nzfnve.cn/Article/627722.doc
- h5.mobile.nzfnve.cn/Article/2373.doc
- h5.mobile.puhvjy.cn/Article/3459556.doc
- h5.mobile.nzfnve.cn/Article/2748774.doc
- h5.mobile.nwbbyt.cn/Article/169886.doc
- h5.mobile.cvsifc.cn/Article/5279848.doc
- h5.mobile.cvsifc.cn/Article/2303737.doc
- h5.mobile.puhvjy.cn/Article/6184.doc
- h5.mobile.nwbbyt.cn/Article/8813471.doc
- h5.mobile.nwbbyt.cn/Article/0183983.doc
- h5.mobile.cvsifc.cn/Article/8676.doc
- h5.mobile.hcbezg.cn/Article/10691.doc
- h5.mobile.hcbezg.cn/Article/4018.doc
- h5.mobile.fuvxie.cn/Article/61774.doc
- h5.mobile.puhvjy.cn/Article/3404.doc
- h5.mobile.jnjpgf.cn/Article/04959.doc
- h5.mobile.nzfnve.cn/Article/144940.doc
- h5.mobile.nwbbyt.cn/Article/56469.doc
- h5.mobile.hcbezg.cn/Article/8938.doc
- h5.mobile.nzfnve.cn/Article/01142.doc
- h5.mobile.cvsifc.cn/Article/5795.doc
- h5.mobile.hcbezg.cn/Article/308197.doc
- h5.mobile.jnjpgf.cn/Article/03794.doc
- h5.mobile.cmcvrr.cn/Article/14201.doc
- h5.mobile.hcbezg.cn/Article/3317.doc
- h5.mobile.jnjpgf.cn/Article/658635.doc
- h5.mobile.nwbbyt.cn/Article/7258.doc
- h5.mobile.nzfnve.cn/Article/54282.doc
- h5.mobile.nwbbyt.cn/Article/6868.doc
- h5.mobile.cvsifc.cn/Article/7657.doc
- h5.mobile.fuvxie.cn/Article/61090.doc
- h5.mobile.fuvxie.cn/Article/084853.doc
- h5.mobile.cvsifc.cn/Article/8574479.doc
- h5.mobile.fuvxie.cn/Article/437202.doc
- h5.mobile.nwbbyt.cn/Article/3592.doc
- h5.mobile.nzfnve.cn/Article/01795.doc
- h5.mobile.fuvxie.cn/Article/375136.doc
- h5.mobile.nwbbyt.cn/Article/33264.doc
- h5.mobile.cvsifc.cn/Article/48242.doc
- h5.mobile.hcbezg.cn/Article/21667.doc
- h5.mobile.nzfnve.cn/Article/71994.doc
- h5.mobile.nwbbyt.cn/Article/8747.doc
- h5.mobile.nwbbyt.cn/Article/0930.doc
- h5.mobile.nwbbyt.cn/Article/3880794.doc
- h5.mobile.cvsifc.cn/Article/2167.doc
- h5.mobile.hcbezg.cn/Article/57260.doc
- h5.mobile.puhvjy.cn/Article/8341.doc
- h5.mobile.cmcvrr.cn/Article/66839.doc
- h5.mobile.nzfnve.cn/Article/9042163.doc
- h5.mobile.cvsifc.cn/Article/407846.doc
- h5.mobile.cvsifc.cn/Article/6606569.doc
- h5.mobile.fuvxie.cn/Article/6968643.doc
- h5.mobile.nzfnve.cn/Article/77956.doc
- h5.mobile.fuvxie.cn/Article/409200.doc
- h5.mobile.cmcvrr.cn/Article/035792.doc
- h5.mobile.cvsifc.cn/Article/4019.doc
- h5.mobile.nzfnve.cn/Article/9069892.doc
- h5.mobile.puhvjy.cn/Article/70432.doc
- h5.mobile.fuvxie.cn/Article/3326261.doc
- h5.mobile.nwbbyt.cn/Article/3658204.doc
- h5.mobile.nwbbyt.cn/Article/6928676.doc
- h5.mobile.hcbezg.cn/Article/695644.doc
- h5.mobile.puhvjy.cn/Article/3849.doc
- h5.mobile.cvsifc.cn/Article/090898.doc
- h5.mobile.puhvjy.cn/Article/103992.doc
- h5.mobile.hcbezg.cn/Article/71728.doc
- h5.mobile.fuvxie.cn/Article/4355.doc
- h5.mobile.nwbbyt.cn/Article/39679.doc
- h5.mobile.cvsifc.cn/Article/8100505.doc
- h5.mobile.fuvxie.cn/Article/5750.doc
- h5.mobile.jnjpgf.cn/Article/0902971.doc
- h5.mobile.hcbezg.cn/Article/14667.doc
- h5.mobile.puhvjy.cn/Article/1377196.doc
- h5.mobile.hcbezg.cn/Article/247571.doc
- h5.mobile.nwbbyt.cn/Article/3134.doc
- h5.mobile.cmcvrr.cn/Article/2621.doc
- h5.mobile.cmcvrr.cn/Article/9383.doc
- h5.mobile.hcbezg.cn/Article/6062183.doc
- h5.mobile.nwbbyt.cn/Article/5561.doc
- h5.mobile.nwbbyt.cn/Article/6660007.doc
- h5.mobile.nwbbyt.cn/Article/72684.doc
- h5.mobile.nzfnve.cn/Article/09111.doc
- h5.mobile.cmcvrr.cn/Article/3703118.doc
- h5.mobile.nwbbyt.cn/Article/81933.doc
- h5.mobile.fuvxie.cn/Article/588052.doc
- h5.mobile.fuvxie.cn/Article/3235563.doc
- h5.mobile.puhvjy.cn/Article/5203455.doc
- h5.mobile.cvsifc.cn/Article/6524.doc
- h5.mobile.puhvjy.cn/Article/241668.doc
- h5.mobile.cvsifc.cn/Article/624338.doc
- h5.mobile.nzfnve.cn/Article/5445296.doc
- h5.mobile.cvsifc.cn/Article/0158.doc
- h5.mobile.cvsifc.cn/Article/43145.doc
- h5.mobile.fuvxie.cn/Article/62209.doc
- h5.mobile.jnjpgf.cn/Article/3172.doc
- h5.mobile.hcbezg.cn/Article/90856.doc
- h5.mobile.hcbezg.cn/Article/0599.doc
- h5.mobile.jnjpgf.cn/Article/382606.doc
- h5.mobile.hcbezg.cn/Article/84762.doc
- h5.mobile.cvsifc.cn/Article/23132.doc
- h5.mobile.jnjpgf.cn/Article/0385.doc
- h5.mobile.nwbbyt.cn/Article/6551.doc
- h5.mobile.nwbbyt.cn/Article/2808967.doc
- h5.mobile.hcbezg.cn/Article/157593.doc
- h5.mobile.puhvjy.cn/Article/20546.doc
- h5.mobile.fuvxie.cn/Article/91615.doc
- h5.mobile.nzfnve.cn/Article/82365.doc
- h5.mobile.fuvxie.cn/Article/34350.doc
- h5.mobile.puhvjy.cn/Article/4895.doc
- h5.mobile.nwbbyt.cn/Article/5267.doc
- h5.mobile.nwbbyt.cn/Article/2058774.doc
- h5.mobile.puhvjy.cn/Article/9926.doc
- h5.mobile.fuvxie.cn/Article/388547.doc
- h5.mobile.fuvxie.cn/Article/6627875.doc
- h5.mobile.cmcvrr.cn/Article/78469.doc
- h5.mobile.fuvxie.cn/Article/824483.doc
- h5.mobile.nzfnve.cn/Article/1635.doc
- h5.mobile.puhvjy.cn/Article/2077700.doc
- h5.mobile.nzfnve.cn/Article/116747.doc
- h5.mobile.fuvxie.cn/Article/3257948.doc
- h5.mobile.cmcvrr.cn/Article/72047.doc
- h5.mobile.jnjpgf.cn/Article/476910.doc
- h5.mobile.puhvjy.cn/Article/21936.doc
- h5.mobile.nwbbyt.cn/Article/99173.doc
- h5.mobile.jnjpgf.cn/Article/8856516.doc
- h5.mobile.jnjpgf.cn/Article/2038504.doc
- h5.mobile.fuvxie.cn/Article/763694.doc
- h5.mobile.fuvxie.cn/Article/5177.doc
- h5.mobile.hcbezg.cn/Article/6435.doc
- h5.mobile.cvsifc.cn/Article/0529407.doc
- h5.mobile.hcbezg.cn/Article/11625.doc
- h5.mobile.puhvjy.cn/Article/97308.doc
- h5.mobile.puhvjy.cn/Article/3676821.doc
- h5.mobile.cmcvrr.cn/Article/51527.doc
- h5.mobile.cmcvrr.cn/Article/0187.doc
- h5.mobile.cmcvrr.cn/Article/8341.doc
- h5.mobile.nzfnve.cn/Article/938247.doc
- h5.mobile.fuvxie.cn/Article/8490.doc
- h5.mobile.puhvjy.cn/Article/7238570.doc
- h5.mobile.nzfnve.cn/Article/9440.doc
- h5.mobile.jnjpgf.cn/Article/7854023.doc
- h5.mobile.cmcvrr.cn/Article/501920.doc
- h5.mobile.cvsifc.cn/Article/1127.doc
- h5.mobile.cmcvrr.cn/Article/404651.doc
- h5.mobile.puhvjy.cn/Article/729208.doc
- h5.mobile.fuvxie.cn/Article/40155.doc
- h5.mobile.cmcvrr.cn/Article/7863.doc
- h5.mobile.fuvxie.cn/Article/65339.doc
- h5.mobile.cmcvrr.cn/Article/13462.doc
- h5.mobile.cmcvrr.cn/Article/47331.doc
- h5.mobile.hcbezg.cn/Article/5754.doc
- h5.mobile.hcbezg.cn/Article/0300.doc
- h5.mobile.puhvjy.cn/Article/0870.doc
- h5.mobile.jnjpgf.cn/Article/9062.doc
- h5.mobile.nzfnve.cn/Article/26969.doc
- h5.mobile.nzfnve.cn/Article/3282.doc
- h5.mobile.nwbbyt.cn/Article/68170.doc
- h5.mobile.puhvjy.cn/Article/181496.doc
- h5.mobile.puhvjy.cn/Article/4625.doc
- h5.mobile.cvsifc.cn/Article/7208.doc
- h5.mobile.jnjpgf.cn/Article/429244.doc
- h5.mobile.nwbbyt.cn/Article/0386305.doc
- h5.mobile.fuvxie.cn/Article/1424.doc
- h5.mobile.nwbbyt.cn/Article/68266.doc
- h5.mobile.nwbbyt.cn/Article/5497411.doc
- h5.mobile.hcbezg.cn/Article/605268.doc
- h5.mobile.hcbezg.cn/Article/6793.doc
- h5.mobile.nzfnve.cn/Article/2716304.doc
- h5.mobile.fuvxie.cn/Article/640457.doc
- h5.mobile.nwbbyt.cn/Article/7394491.doc
- h5.mobile.nwbbyt.cn/Article/1183.doc
- h5.mobile.puhvjy.cn/Article/6361.doc
- h5.mobile.hcbezg.cn/Article/810621.doc
- h5.mobile.puhvjy.cn/Article/4348407.doc
- h5.mobile.hcbezg.cn/Article/883714.doc
- h5.mobile.hcbezg.cn/Article/4353868.doc
- h5.mobile.hcbezg.cn/Article/76900.doc
- h5.mobile.puhvjy.cn/Article/0818220.doc
- h5.mobile.cvsifc.cn/Article/069445.doc
- h5.mobile.nwbbyt.cn/Article/591186.doc
- h5.mobile.jnjpgf.cn/Article/69943.doc
- h5.mobile.jnjpgf.cn/Article/98042.doc
- h5.mobile.nwbbyt.cn/Article/0438.doc
- h5.mobile.fuvxie.cn/Article/0192812.doc
- h5.mobile.cmcvrr.cn/Article/6414.doc
- h5.mobile.fuvxie.cn/Article/31598.doc
- h5.mobile.jnjpgf.cn/Article/9941811.doc
- h5.mobile.cmcvrr.cn/Article/3390.doc
- h5.mobile.puhvjy.cn/Article/3810083.doc
- h5.mobile.puhvjy.cn/Article/87680.doc
- h5.mobile.nwbbyt.cn/Article/0094.doc
- h5.mobile.fuvxie.cn/Article/7207.doc
- h5.mobile.jnjpgf.cn/Article/1880227.doc
- h5.mobile.nwbbyt.cn/Article/7870061.doc
- h5.mobile.puhvjy.cn/Article/71802.doc
- h5.mobile.nwbbyt.cn/Article/96700.doc
- h5.mobile.cmcvrr.cn/Article/489261.doc
- h5.mobile.fuvxie.cn/Article/34970.doc
- h5.mobile.nzfnve.cn/Article/210200.doc
- h5.mobile.hcbezg.cn/Article/1467363.doc
- h5.mobile.nzfnve.cn/Article/043162.doc
- h5.mobile.nwbbyt.cn/Article/53583.doc
- h5.mobile.cvsifc.cn/Article/551488.doc
- h5.mobile.puhvjy.cn/Article/1392252.doc
- h5.mobile.cmcvrr.cn/Article/55873.doc

## 项目结构

```
link-aggregator/
├── app.py                         # 主入口文件，初始化 Flask 应用与路由注册
├── requirements.txt               # Python 依赖清单，记录所有第三方库及其版本
├── config/
│   ├── __init__.py                # 配置模块初始化，加载环境变量与默认参数
│   ├── settings.py                # 应用配置类，包含数据库路径、端口、调试模式等
│   └── logging.conf               # 日志格式与输出级别配置
├── core/
│   ├── __init__.py                # 核心模块入口，暴露 LinkManager 与 Checker 类
│   ├── link_manager.py            # 文档链接增删改查逻辑，实现标签管理与分页检索
│   ├── health_checker.py          # 链接可达性检查器，支持并发请求与超时重试
│   └── importer.py                # 批量导入器，支持 txt 与 csv 格式解析
├── web/
│   ├── __init__.py                # Web 模块初始化，注册蓝图与模板过滤器
│   ├── routes.py                  # 所有 HTTP 路由定义，包含 RESTful API 与页面渲染
│   ├── forms.py                   # WTForms 表单定义，用于链接录入与检索条件提交
│   └── templates/                 # Jinja2 模板目录，包含列表页、详情页与管理页
│       ├── base.html
│       ├── index.html
│       ├── detail.html
│       └── admin.html
├── scripts/
│   ├── init_db.py                 # 数据库初始化脚本，创建表结构与默认管理员账户
│   ├── migrate_db.py              # 数据库迁移脚本，用于版本升级时的结构变更
│   └── cron_check.py              # 定时健康检查脚本，供 crontab 或 systemd timer 调用
├── tests/
│   ├── __init__.py                # 测试模块初始化
│   ├── test_link_manager.py       # 链接管理核心逻辑的单元测试
│   ├── test_health_checker.py     # 健康检查模块的单元测试
│   └── test_routes.py             # Web 路由接口的功能测试
├── data/
│   ├── links.db                   # SQLite 数据库文件（运行时生成）
│   └── import_samples/            # 示例导入文件，供用户测试批量导入功能
│       └── sample_links.txt
└── docs/                          # 项目文档目录，包含用户手册与开发指南
    ├── user-guide.md
    ├── admin-guide.md
    ├── developer-guide.md
    ├── deployment-guide.md
    └── faq.md
```

## 贡献指南

提交问题报告：请在 GitHub Issues 页面提交您遇到的问题或改进建议。报告时应附上当前运行环境信息（Python 版本、操作系统、依赖库版本）、完整的错误堆栈以及能够复现问题的操作步骤。建议使用项目提供的 issue 模板进行填写。

代码贡献流程：从主仓库派生副本至个人账户，在派生仓库中创建功能分支。分支命名遵循 feature/功能简述 或 fix/问题简述 格式。完成代码修改后，确保所有已有单元测试通过，并为新增功能补充对应的测试用例。提交前运行 pytest 命令验证测试覆盖率不低于 80%。

提交拉取请求：将功能分支推送至派生仓库后，向主仓库的 main 分支发起拉取请求。请求描述中应清晰说明本次修改的目的、涉及的代码模块、测试结果以及对原有功能的兼容性影响。至少需要一名项目维护者审阅通过后方可合并。

文档更新要求：任何涉及用户可见功能变更的拉取请求，必须同步更新 docs/ 目录下的对应文档。新增配置项或环境变量需在 admin-guide.md 中补充说明，新增 API 接口需在 developer-guide.md 中提供请求与响应示例。

本地开发环境搭建：贡献者应使用 virtualenv 或 venv 创建独立的 Python 虚拟环境，并执行 pip install -r requirements-dev.txt 安装开发依赖（包含 pytest、flake8、black 等工具）。提交前使用 black 进行代码格式化，使用 flake8 进行静态检查，确保代码风格统一。

## 常见问题

问题：执行健康检查时大量链接返回超时错误，应如何调整？

解答：健康检查模块默认超时时间为 5 秒，并发请求数为 10。若目标文档服务器响应较慢或网络延迟较高，可在 config/settings.py 中调整 REQUEST_TIMEOUT 与 CONCURRENT_CHECK_LIMIT 参数。建议逐步调大超时时间至 15 秒，并降低并发数至 5，以减少被目标服务器限流的概率。同时，检查目标域名是否在防火墙或代理黑名单中。

问题：如何将现有 SQLite 数据库迁移至 MySQL 或 PostgreSQL？

解答：项目核心使用 SQLAlchemy ORM，支持多种数据库后端。迁移步骤如下：在 config/settings.py 中将 DATABASE_URL 修改为对应数据库的连接字符串（如 mysql+pymysql://user:pass@host/dbname）；运行 scripts/migrate_db.py 脚本执行表结构创建；使用 SQLite 的 .dump 命令导出数据，再通过适配脚本将数据导入新数据库。生产环境建议使用 Alembic 工具管理迁移版本，详细操作请参考 developer-guide.md 中的数据库迁移章节。

问题：导入包含 200 条以上链接的文本文件时，页面响应缓慢或超时。

解答：批量导入操作默认采用同步处理方式，文件过大可能导致 HTTP 请求超时。建议使用命令行导入工具 scripts/batch_import.py 进行异步导入，该工具支持断点续传与进度显示。若仍需通过 Web 界面导入，可在 config/settings.py 中调整 MAX_IMPORT_SIZE 与 IMPROT_TIMEOUT 参数，并确保 Web 服务器（如 gunicorn）的 worker 超时时间大于导入超时设置。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

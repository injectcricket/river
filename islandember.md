# DocLink Harvest 聚合文档索引系统

DocLink Harvest 是一个面向技术团队、科研工作者与内容管理者的轻量级分布式文档索引与资源聚合平台。该项目定位于解决异构文档资源分散、检索路径复杂、外部链接易失效等问题，通过建立统一的资源描述与索引层，将散落在不同域名与服务路径下的文档资源（以 .doc 及兼容格式为主）进行结构化收集、分类标注与状态监控，从而为用户提供稳定、可查询、可审计的外部文档资源访问入口。

本项目并非传统全文搜索引擎，而是一套资源链接的元数据管理系统。其核心工作模式为：接收并规范存储外部文档资源的原始访问地址，通过内置的调度器定期检测资源可访问性，并基于资源来源域名、路径模式、批次归属等维度生成多维度的资源目录视图。项目内建资源快照机制，支持对每个文档记录添加标签、备注与过期标记，方便团队内部进行资源审核与生命周期管理。

DocLink Harvest 主要面向以下用户群体：需要批量整理历史技术文档的运维工程师、需要追踪外部参考资料的研究人员、以及需要构建内部文档门户的知识管理团队。项目本身不存储文档实体，仅维护指向文档的稳定索引记录，因此具有极低的存储开销与部署成本，同时最大限度规避版权与合规风险。

## 功能概览

批量资源导入与解析 系统提供标准化的资源录入接口，支持一次性导入数百条文档链接，自动解析域名、路径、文件扩展名及资源ID，并将数据规整为内部统一的索引记录格式。

资源可达性健康检查 内置异步健康检查队列，可按照可配置的时间周期对已收录的文档链接发起 HEAD 请求，验证资源是否仍可访问，并记录响应状态码与响应时间，供管理员排查失效链接。

多维资源分类与筛选 支持按照来源域名、文档类型、收录批次、状态标记等维度对资源列表进行动态筛选与排序，帮助用户在海量链接中快速定位目标资源。

自定义标签与备注系统 允许用户为单条或批量资源添加自定义标签与备注信息，用于记录资源用途、审核状态、关联项目编号等业务上下文，增强索引数据的可读性与可维护性。

资源快照与变更审计 每当资源记录被新增、修改或删除时，系统自动记录操作时间、操作人及变更内容，形成完整的资源变更日志，满足内部审计与回溯需求。

开放 API 与 Webhook 通知 提供 RESTful API 用于外部系统集成，支持通过 Webhook 在资源状态发生变化时（如链接失效）向第三方监控平台发送告警通知。

数据导入导出 支持将资源索引数据导出为 CSV 或 JSON 格式，便于离线分析或迁移至其他文档管理平台；同时支持从外部数据源批量导入资源记录。

## 应用场景

技术文档库的资源索引管理 企业的内部技术文档库往往引用了大量外部供应商提供的规格说明书、接口文档或白皮书。DocLink Harvest 可集中记录这些外部文档的原始地址，并定期检查其有效性，避免因外部链接变更导致内部文档出现大量死链。

科研项目参考文献的外部资料追踪 科研人员在撰写技术报告或论文时，需要引用大量的在线文档资源。利用 DocLink Harvest，可将所有引用的文档链接统一录入系统，并附加项目编号、引用章节等元数据，确保在项目周期内所有参考资料均可追溯。

内容聚合站点的链接治理 对于运营技术资讯聚合站点或开发者门户的团队，维护大量外部文章或文档的引用链接是一项繁重工作。DocLink Harvest 可作为链接治理的后台工具，批量检测链接可用性，并标注异常资源，辅助编辑人员及时更新或替换失效内容。

多团队协作下的文档共享索引 不同开发团队或项目组各自维护一批常用的技术文档链接。通过 DocLink Harvest 建立统一的共享索引，各团队可以上传自有资源列表，并浏览其他团队公开的资源，减少重复收集成本，促进知识复用。

## 快速开始

以下步骤帮助您在本地环境中快速启动 DocLink Harvest 服务。

```bash
# 1. 克隆项目代码仓库
git clone https://github.com/doclink-harvest/doclink-harvest.git
cd doclink-harvest

# 2. 安装项目依赖（使用 pip 与虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 3. 初始化数据库并启动服务
python manage.py migrate
python manage.py loaddata initial_resources.json
python manage.py runserver 0.0.0.0:8000
```

服务启动后，访问 http://localhost:8000 即可进入 DocLink Harvest 的 Web 管理界面。默认管理员账号为 admin，密码为 changeme，请在首次登录后立即修改。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 或更高 | 项目后端运行环境，推荐使用 3.10 长期支持版本 |
| Django | 4.2 LTS | Web 框架，用于提供管理界面与 REST API |
| PostgreSQL | 14 或更高 | 生产环境推荐使用的关系型数据库，用于存储资源索引与元数据 |
| Redis | 6.2 或更高 | 用作缓存后端与异步任务队列的消息代理 |
| Celery | 5.3 或更高 | 分布式任务队列，用于执行资源健康检查等异步操作 |
| gunicorn | 21.2 或更高 | 生产环境下的 WSGI HTTP 服务器 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | /docs/user-guide/ | 如何进行资源录入、如何查看资源状态、如何使用标签与筛选功能 |
| 管理员手册 | /docs/admin-manual/ | 如何配置健康检查策略、如何管理用户权限、如何备份与恢复数据 |
| API 参考 | /docs/api-reference/ | 所有 RESTful 接口的请求参数、响应格式与错误码说明 |
| 部署运维 | /docs/deployment/ | 如何将项目部署至生产环境、如何配置 HTTPS、如何集成外部监控 |

## 资源列表

- h5.mobile.nwbbyt.cn/Article/7005264.doc
- h5.mobile.hcbezg.cn/Article/8069.doc
- h5.mobile.cvsifc.cn/Article/7281.doc
- h5.mobile.cvsifc.cn/Article/2518.doc
- h5.mobile.fuvxie.cn/Article/6633306.doc
- h5.mobile.hcbezg.cn/Article/776781.doc
- h5.mobile.cmcvrr.cn/Article/599575.doc
- h5.mobile.cmcvrr.cn/Article/243848.doc
- h5.mobile.fuvxie.cn/Article/7968.doc
- h5.mobile.cvsifc.cn/Article/9056418.doc
- h5.mobile.puhvjy.cn/Article/3008.doc
- h5.mobile.jnjpgf.cn/Article/8715.doc
- h5.mobile.nwbbyt.cn/Article/98973.doc
- h5.mobile.puhvjy.cn/Article/5362.doc
- h5.mobile.nwbbyt.cn/Article/5440450.doc
- h5.mobile.cmcvrr.cn/Article/3267680.doc
- h5.mobile.nzfnve.cn/Article/1949.doc
- h5.mobile.cmcvrr.cn/Article/5142.doc
- h5.mobile.nzfnve.cn/Article/54155.doc
- h5.mobile.hcbezg.cn/Article/3621835.doc
- h5.mobile.hcbezg.cn/Article/9914941.doc
- h5.mobile.fuvxie.cn/Article/6587.doc
- h5.mobile.puhvjy.cn/Article/52931.doc
- h5.mobile.cvsifc.cn/Article/3589195.doc
- h5.mobile.hcbezg.cn/Article/321711.doc
- h5.mobile.nzfnve.cn/Article/2895.doc
- h5.mobile.cmcvrr.cn/Article/3656350.doc
- h5.mobile.cvsifc.cn/Article/14455.doc
- h5.mobile.jnjpgf.cn/Article/422153.doc
- h5.mobile.cmcvrr.cn/Article/39294.doc
- h5.mobile.hcbezg.cn/Article/79424.doc
- h5.mobile.puhvjy.cn/Article/1721698.doc
- h5.mobile.cmcvrr.cn/Article/2336.doc
- h5.mobile.cmcvrr.cn/Article/61631.doc
- h5.mobile.fuvxie.cn/Article/47930.doc
- h5.mobile.cmcvrr.cn/Article/1708265.doc
- h5.mobile.jnjpgf.cn/Article/71626.doc
- h5.mobile.nzfnve.cn/Article/846382.doc
- h5.mobile.hcbezg.cn/Article/9007.doc
- h5.mobile.puhvjy.cn/Article/7434925.doc
- h5.mobile.puhvjy.cn/Article/941032.doc
- h5.mobile.puhvjy.cn/Article/9508.doc
- h5.mobile.puhvjy.cn/Article/108593.doc
- h5.mobile.hcbezg.cn/Article/52197.doc
- h5.mobile.hcbezg.cn/Article/626817.doc
- h5.mobile.fuvxie.cn/Article/10058.doc
- h5.mobile.cvsifc.cn/Article/509537.doc
- h5.mobile.jnjpgf.cn/Article/77786.doc
- h5.mobile.puhvjy.cn/Article/6906.doc
- h5.mobile.puhvjy.cn/Article/12696.doc
- h5.mobile.hcbezg.cn/Article/2444.doc
- h5.mobile.puhvjy.cn/Article/19355.doc
- h5.mobile.puhvjy.cn/Article/773182.doc
- h5.mobile.fuvxie.cn/Article/200152.doc
- h5.mobile.fuvxie.cn/Article/22390.doc
- h5.mobile.jnjpgf.cn/Article/86417.doc
- h5.mobile.fuvxie.cn/Article/47530.doc
- h5.mobile.jnjpgf.cn/Article/80301.doc
- h5.mobile.hcbezg.cn/Article/934417.doc
- h5.mobile.nwbbyt.cn/Article/739644.doc
- h5.mobile.hcbezg.cn/Article/18986.doc
- h5.mobile.cmcvrr.cn/Article/28370.doc
- h5.mobile.puhvjy.cn/Article/1678.doc
- h5.mobile.nzfnve.cn/Article/74512.doc
- h5.mobile.jnjpgf.cn/Article/8527390.doc
- h5.mobile.puhvjy.cn/Article/767748.doc
- h5.mobile.jnjpgf.cn/Article/3973.doc
- h5.mobile.jnjpgf.cn/Article/903911.doc
- h5.mobile.cvsifc.cn/Article/88886.doc
- h5.mobile.cvsifc.cn/Article/0379851.doc
- h5.mobile.cvsifc.cn/Article/062349.doc
- h5.mobile.nzfnve.cn/Article/72372.doc
- h5.mobile.fuvxie.cn/Article/94333.doc
- h5.mobile.cvsifc.cn/Article/1684.doc
- h5.mobile.hcbezg.cn/Article/4303695.doc
- h5.mobile.puhvjy.cn/Article/63843.doc
- h5.mobile.cvsifc.cn/Article/1169.doc
- h5.mobile.cmcvrr.cn/Article/7345631.doc
- h5.mobile.cmcvrr.cn/Article/747318.doc
- h5.mobile.hcbezg.cn/Article/91453.doc
- h5.mobile.puhvjy.cn/Article/8864.doc
- h5.mobile.fuvxie.cn/Article/7007224.doc
- h5.mobile.hcbezg.cn/Article/681726.doc
- h5.mobile.hcbezg.cn/Article/3147060.doc
- h5.mobile.nwbbyt.cn/Article/162957.doc
- h5.mobile.cmcvrr.cn/Article/97019.doc
- h5.mobile.hcbezg.cn/Article/82329.doc
- h5.mobile.cvsifc.cn/Article/7548.doc
- h5.mobile.fuvxie.cn/Article/4878166.doc
- h5.mobile.jnjpgf.cn/Article/520914.doc
- h5.mobile.hcbezg.cn/Article/4265463.doc
- h5.mobile.cvsifc.cn/Article/769163.doc
- h5.mobile.jnjpgf.cn/Article/2264817.doc
- h5.mobile.cvsifc.cn/Article/1315360.doc
- h5.mobile.nzfnve.cn/Article/48669.doc
- h5.mobile.cmcvrr.cn/Article/959039.doc
- h5.mobile.puhvjy.cn/Article/2771.doc
- h5.mobile.cmcvrr.cn/Article/4250.doc
- h5.mobile.jnjpgf.cn/Article/6289708.doc
- h5.mobile.puhvjy.cn/Article/5753.doc
- h5.mobile.nzfnve.cn/Article/21601.doc
- h5.mobile.nzfnve.cn/Article/65727.doc
- h5.mobile.hcbezg.cn/Article/8303002.doc
- h5.mobile.nwbbyt.cn/Article/98429.doc
- h5.mobile.cmcvrr.cn/Article/2844.doc
- h5.mobile.cvsifc.cn/Article/771973.doc
- h5.mobile.fuvxie.cn/Article/8410.doc
- h5.mobile.puhvjy.cn/Article/782024.doc
- h5.mobile.fuvxie.cn/Article/4745047.doc
- h5.mobile.hcbezg.cn/Article/1779898.doc
- h5.mobile.cmcvrr.cn/Article/0756.doc
- h5.mobile.cvsifc.cn/Article/2567955.doc
- h5.mobile.nzfnve.cn/Article/1420.doc
- h5.mobile.jnjpgf.cn/Article/4030.doc
- h5.mobile.nwbbyt.cn/Article/9115.doc
- h5.mobile.puhvjy.cn/Article/4381551.doc
- h5.mobile.cvsifc.cn/Article/9169.doc
- h5.mobile.fuvxie.cn/Article/00653.doc
- h5.mobile.cvsifc.cn/Article/1303835.doc
- h5.mobile.puhvjy.cn/Article/282051.doc
- h5.mobile.cmcvrr.cn/Article/398937.doc
- h5.mobile.cvsifc.cn/Article/39643.doc
- h5.mobile.cmcvrr.cn/Article/2172038.doc
- h5.mobile.puhvjy.cn/Article/2642.doc
- h5.mobile.puhvjy.cn/Article/2734224.doc
- h5.mobile.cvsifc.cn/Article/207826.doc
- h5.mobile.puhvjy.cn/Article/4780097.doc
- h5.mobile.nzfnve.cn/Article/408103.doc
- h5.mobile.cvsifc.cn/Article/90001.doc
- h5.mobile.hcbezg.cn/Article/739601.doc
- h5.mobile.nwbbyt.cn/Article/23721.doc
- h5.mobile.fuvxie.cn/Article/617953.doc
- h5.mobile.puhvjy.cn/Article/2144322.doc
- h5.mobile.fuvxie.cn/Article/101065.doc
- h5.mobile.nzfnve.cn/Article/7726.doc
- h5.mobile.fuvxie.cn/Article/0933.doc
- h5.mobile.jnjpgf.cn/Article/019204.doc
- h5.mobile.cmcvrr.cn/Article/00993.doc
- h5.mobile.nwbbyt.cn/Article/5680.doc
- h5.mobile.puhvjy.cn/Article/0554.doc
- h5.mobile.cvsifc.cn/Article/1168196.doc
- h5.mobile.nzfnve.cn/Article/90750.doc
- h5.mobile.cmcvrr.cn/Article/0643.doc
- h5.mobile.cvsifc.cn/Article/5709.doc
- h5.mobile.cmcvrr.cn/Article/3652030.doc
- h5.mobile.cmcvrr.cn/Article/54573.doc
- h5.mobile.jnjpgf.cn/Article/060948.doc
- h5.mobile.hcbezg.cn/Article/5144.doc
- h5.mobile.puhvjy.cn/Article/205490.doc
- h5.mobile.cmcvrr.cn/Article/04841.doc
- h5.mobile.nwbbyt.cn/Article/78957.doc
- h5.mobile.nzfnve.cn/Article/6288533.doc
- h5.mobile.hcbezg.cn/Article/652272.doc
- h5.mobile.cvsifc.cn/Article/919368.doc
- h5.mobile.fuvxie.cn/Article/0890587.doc
- h5.mobile.hcbezg.cn/Article/8785.doc
- h5.mobile.cmcvrr.cn/Article/405286.doc
- h5.mobile.puhvjy.cn/Article/0464.doc
- h5.mobile.puhvjy.cn/Article/148997.doc
- h5.mobile.jnjpgf.cn/Article/6088.doc
- h5.mobile.cvsifc.cn/Article/405095.doc
- h5.mobile.puhvjy.cn/Article/7543758.doc
- h5.mobile.cvsifc.cn/Article/7719.doc
- h5.mobile.nwbbyt.cn/Article/612108.doc
- h5.mobile.nwbbyt.cn/Article/7001.doc
- h5.mobile.cvsifc.cn/Article/8814.doc
- h5.mobile.nwbbyt.cn/Article/130974.doc
- h5.mobile.nzfnve.cn/Article/28912.doc
- h5.mobile.puhvjy.cn/Article/83243.doc
- h5.mobile.nwbbyt.cn/Article/48212.doc
- h5.mobile.jnjpgf.cn/Article/284468.doc
- h5.mobile.jnjpgf.cn/Article/9040098.doc
- h5.mobile.nwbbyt.cn/Article/803532.doc
- h5.mobile.fuvxie.cn/Article/1389090.doc
- h5.mobile.nzfnve.cn/Article/9490.doc
- h5.mobile.cvsifc.cn/Article/73551.doc
- h5.mobile.hcbezg.cn/Article/26527.doc
- h5.mobile.fuvxie.cn/Article/1541592.doc
- h5.mobile.nwbbyt.cn/Article/44176.doc
- h5.mobile.fuvxie.cn/Article/2937.doc
- h5.mobile.puhvjy.cn/Article/20689.doc
- h5.mobile.jnjpgf.cn/Article/4227539.doc
- h5.mobile.hcbezg.cn/Article/7773446.doc
- h5.mobile.cmcvrr.cn/Article/5755.doc
- h5.mobile.puhvjy.cn/Article/7379034.doc
- h5.mobile.nwbbyt.cn/Article/266206.doc
- h5.mobile.jnjpgf.cn/Article/2539.doc
- h5.mobile.hcbezg.cn/Article/6658.doc
- h5.mobile.jnjpgf.cn/Article/87691.doc
- h5.mobile.cvsifc.cn/Article/72198.doc
- h5.mobile.jnjpgf.cn/Article/4584427.doc
- h5.mobile.nzfnve.cn/Article/67248.doc
- h5.mobile.fuvxie.cn/Article/8212187.doc
- h5.mobile.jnjpgf.cn/Article/610919.doc
- h5.mobile.fuvxie.cn/Article/201577.doc
- h5.mobile.puhvjy.cn/Article/84341.doc
- h5.mobile.cmcvrr.cn/Article/18707.doc
- h5.mobile.puhvjy.cn/Article/5448.doc
- h5.mobile.hcbezg.cn/Article/248942.doc
- h5.mobile.fuvxie.cn/Article/4647025.doc
- h5.mobile.cvsifc.cn/Article/27359.doc
- h5.mobile.puhvjy.cn/Article/475838.doc
- h5.mobile.cvsifc.cn/Article/8049.doc
- h5.mobile.hcbezg.cn/Article/5595.doc
- h5.mobile.puhvjy.cn/Article/4689843.doc
- h5.mobile.jnjpgf.cn/Article/5034.doc
- h5.mobile.hcbezg.cn/Article/0898925.doc
- h5.mobile.hcbezg.cn/Article/2657.doc
- h5.mobile.fuvxie.cn/Article/0210428.doc
- h5.mobile.cvsifc.cn/Article/4113568.doc
- h5.mobile.cvsifc.cn/Article/5434492.doc
- h5.mobile.cvsifc.cn/Article/35815.doc
- h5.mobile.nzfnve.cn/Article/6445591.doc
- h5.mobile.nzfnve.cn/Article/4934.doc
- h5.mobile.nwbbyt.cn/Article/1140357.doc
- h5.mobile.cmcvrr.cn/Article/589107.doc
- h5.mobile.puhvjy.cn/Article/6330212.doc
- h5.mobile.cvsifc.cn/Article/96345.doc
- h5.mobile.puhvjy.cn/Article/552446.doc
- h5.mobile.cvsifc.cn/Article/03942.doc
- h5.mobile.fuvxie.cn/Article/708106.doc
- h5.mobile.fuvxie.cn/Article/78256.doc
- h5.mobile.puhvjy.cn/Article/47449.doc
- h5.mobile.hcbezg.cn/Article/98146.doc
- h5.mobile.jnjpgf.cn/Article/1938855.doc
- h5.mobile.nwbbyt.cn/Article/64105.doc
- h5.mobile.fuvxie.cn/Article/0235.doc
- h5.mobile.jnjpgf.cn/Article/59329.doc
- h5.mobile.jnjpgf.cn/Article/4542545.doc
- h5.mobile.nzfnve.cn/Article/88016.doc
- h5.mobile.hcbezg.cn/Article/478813.doc
- h5.mobile.fuvxie.cn/Article/8692.doc
- h5.mobile.hcbezg.cn/Article/374518.doc
- h5.mobile.cmcvrr.cn/Article/4364.doc
- h5.mobile.puhvjy.cn/Article/1369279.doc
- h5.mobile.puhvjy.cn/Article/3996.doc
- h5.mobile.cvsifc.cn/Article/522344.doc
- h5.mobile.puhvjy.cn/Article/9507481.doc
- h5.mobile.hcbezg.cn/Article/5299293.doc
- h5.mobile.nzfnve.cn/Article/6887486.doc
- h5.mobile.hcbezg.cn/Article/8155028.doc
- h5.mobile.jnjpgf.cn/Article/5102.doc
- h5.mobile.nzfnve.cn/Article/6932949.doc
- h5.mobile.hcbezg.cn/Article/0080372.doc
- h5.mobile.jnjpgf.cn/Article/912746.doc
- h5.mobile.puhvjy.cn/Article/362192.doc
- h5.mobile.cvsifc.cn/Article/4803.doc
- h5.mobile.cmcvrr.cn/Article/9839201.doc
- h5.mobile.puhvjy.cn/Article/1179.doc
- h5.mobile.nzfnve.cn/Article/966323.doc

## 项目结构

```
doclink-harvest/
├── manage.py                         # Django 项目管理入口
├── requirements.txt                  # Python 依赖声明
├── docker-compose.yml                # 本地开发环境编排（PostgreSQL + Redis）
├── doclink/                          # 主应用包
│   ├── __init__.py
│   ├── settings/                     # 多环境配置目录
│   │   ├── base.py                   # 基础配置（共用）
│   │   ├── development.py            # 开发环境配置
│   │   └── production.py             # 生产环境配置（覆盖敏感项）
│   ├── urls.py                       # 顶层路由分发
│   ├── wsgi.py                       # WSGI 启动脚本
│   └── celery.py                     # Celery 应用实例定义
├── apps/                             # 所有功能模块（Django app）
│   ├── resources/                    # 资源索引核心模块
│   │   ├── models.py                 # Resource, Tag, ResourceStatus 等模型
│   │   ├── views.py                  # 资源列表、详情、导入导出视图
│   │   ├── serializers.py            # REST API 序列化器
│   │   ├── tasks.py                  # 资源健康检查异步任务
│   │   └── management/               # 自定义命令行命令
│   │       └── commands/
│   │           └── check_resources.py
│   ├── audits/                       # 审计与日志模块
│   │   ├── models.py                 # 操作日志模型
│   │   └── middleware.py             # 请求日志中间件
│   ├── webhooks/                     # Webhook 通知模块
│   │   ├── models.py                 # Webhook 配置模型
│   │   └── publishers.py             # 通知发送逻辑（支持钉钉、企业微信等）
│   └── users/                        # 用户与权限管理
│       ├── models.py                 # 扩展 User 模型
│       └── backends.py               # 自定义认证后端
├── static/                           # 静态文件（CSS, JS, 图片）
│   ├── css/
│   ├── js/
│   └── images/
├── templates/                        # Django 模板文件
│   ├── base.html                     # 基础页面骨架
│   ├── resources/
│   │   ├── list.html                 # 资源列表页
│   │   └── detail.html               # 资源详情页
│   └── admin/
├── tests/                            # 单元测试与集成测试
│   ├── test_models.py
│   ├── test_api.py
│   └── test_tasks.py
├── scripts/                          # 运维辅助脚本
│   ├── backup_db.sh                  # 数据库备份脚本
│   └── import_legacy.py              # 旧数据迁移脚本
└── docs/                             # 项目文档源文件（Markdown）
    ├── user-guide.md
    ├── admin-manual.md
    ├── api-reference.md
    └── deployment.md
```

## 贡献指南

1. 提交 Issue 讨论需求或缺陷。在开始任何非琐碎的代码变更之前，建议先在 GitHub Issues 中创建一条新议题，说明您计划解决的问题或希望新增的功能，以便维护者与其他贡献者就方案达成一致。

2. 派生项目并创建功能分支。请将主仓库派生至个人账户，然后在本地基于 main 分支创建新的功能分支，分支命名建议采用 feature/功能简述 或 fix/问题简述 的格式。

3. 编写或更新测试用例。所有新增功能或缺陷修复均需包含对应的单元测试或集成测试，确保测试覆盖率达到合理水平。运行现有测试套件，确认未引入回归问题。

4. 提交代码并签署开发者原创声明。在提交信息中清晰描述变更内容与动机，同时确保每一份提交均包含 Signed-off-by 行，以表示您同意开发者原创证书（Developer Certificate of Origin）。

5. 创建拉取请求并等待代码审查。请详细填写拉取请求模板中的各项信息，包括但不限于变更摘要、测试结果、相关议题编号等。代码审查通过后，将由维护者合并至主分支。

## 常见问题

问：系统支持同时管理多少个文档链接？性能是否会随链接数量增加而显著下降？

答：系统设计上支持管理十万级别至百万级别的文档链接记录。资源列表的查询与筛选均基于数据库索引进行优化，健康检查任务采用 Celery 分布式队列异步执行，避免阻塞主服务。在 PostgreSQL 配合适当硬件的情况下，页面响应时间与链接数量呈对数增长而非线性增长。对于百万级以上的场景，建议采用分区表策略并配置多台 Celery Worker。

问：如何导入用户给定的资源列表？是否支持直接录入上述示例中的大量链接？

答：系统提供两种导入方式。第一种为 Web 界面的批量导入功能，用户可将包含链接的 CSV 文件或纯文本列表复制到输入框中，系统会自动解析每一行的 URL 并创建资源记录。第二种为命令行导入，通过 python manage.py import_resources --file links.txt 可直接从文件中读取并导入。上述资源列表中的链接格式（域名/Article/数字.doc）可被系统自动识别并提取域名与资源ID。

问：检测到文档链接失效后，系统会自动重试或告警吗？

答：健康检查任务在首次检测到非 200 状态码时，会将该资源标记为“可疑”并记录状态码与错误信息。在下一个检查周期（默认每 24 小时），系统会再次尝试访问，若连续三次检测均失败，则将资源状态变更为“失效”，并触发 Webhook 告警通知。用户也可以在管理界面手动触发单条资源的即时检查。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

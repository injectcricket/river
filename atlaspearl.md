# DocLink Hub

DocLink Hub 是一个面向技术文档与业务资料的外链聚合与管理平台，专为需要系统化收集、分类、检索和分享散落在多个移动端子域名下的 Word 文档资源的团队设计。该项目并非文档存储库，而是一个轻量级的外链索引系统，通过结构化目录与标签机制，将大量位于不同域名下的 .doc 文件统一呈现为可浏览、可检索的资源列表，适用于知识库构建、离线文档备份索引、以及跨部门资料共享等场景。目标用户包括技术文档工程师、知识管理专员、内部系统运维人员以及需要快速定位特定编号文档的业务分析人员。

## 功能概览

批量外链导入与自动规范化：支持从文本文件或简单表格批量导入原始文档 URL，系统自动识别并保留域名与路径结构，不进行自动跳转或协议补全，确保链接原始性。

多维度目录分类：内置技术手册、业务报表、运维记录、产品规格、测试用例等一级分类，用户可自定义二级标签，将每个外链归类至一个或多个目录下。

文档元数据提取：对于可访问的 .doc 资源，尝试提取文件大小、最后修改时间、以及文档内标题（非文件名），作为检索字段存入索引数据库。

全文检索与高级筛选：基于文档编号、来源域名、分类标签、上传时间范围进行组合检索，支持模糊匹配与精确查询两种模式。

定期可用性检查：后台调度任务每 24 小时对全部外链发送 HEAD 请求，标记不可用链接并生成可用性报告，便于管理员及时清理或更新。

只读镜像预览模式：对于公开可读的文档资源，提供内联 iframe 预览（需目标服务器支持跨域），否则直接跳转至原始 URL，不缓存文件内容。

API 接口：提供 RESTful API 用于第三方系统集成，支持获取分类树、按标签检索文档列表、以及批量提交新外链。

访问统计：记录每个外链被点击的次数、最近访问时间、以及来源 IP 地区分布（聚合级别），辅助评估文档热度。

## 应用场景

企业内部知识库索引：某大型制造企业的技术中心每天产生数十份设备调试报告（.doc），分散在多个项目子域名下。文档管理员使用 DocLink Hub 按产线编号和日期归档这些外链，工程师只需在统一门户中按设备型号检索，即可找到最新版调试记录的原始下载地址。

离线文档备份清单维护：运维团队定期将重要的网络配置文档和灾备手册上传至多个移动端文件服务器，但不想维护复杂的同步脚本。他们利用 DocLink Hub 记录每个文件的原始外链，并配合可用性检查功能，每周生成一份“有效备份链接清单”，发送给审计部门。

跨部门资料共享：产品部、测试部与售后支持部各自维护独立的 .doc 格式产品说明书，存放于不同的子域名下。通过 DocLink Hub 建立统一的产品文档目录树（按产品线、版本号、语言），三部门均可在一个界面上提交或查找对应的官方文档链接，避免邮件反复传递过时路径。

## 快速开始

以下步骤将在本地环境启动 DocLink Hub 实例，使用 SQLite 作为默认数据库，并监听 8080 端口。

```bash
git clone https://github.com/doclink-hub/doclink-hub.git
cd doclink-hub
pip install -r requirements.txt
python manage.py migrate
python manage.py loaddata initial_categories.json
python manage.py runserver 0.0.0.0:8080
```

访问 http://localhost:8080 即可进入管理界面。首次登录需使用 `python manage.py createsuperuser` 创建管理员账户。如需导入示例外链数据，可执行 `python manage.py import_links --file sample_links.txt`，其中 sample_links.txt 每行一个 URL。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 或更高 | 核心运行环境，推荐使用 3.11 |
| Django | 4.2 LTS | Web 框架，用于 ORM 与后台管理 |
| SQLite | 3.35 以上 | 默认数据库，生产环境可换为 PostgreSQL 14+ |
| requests | 2.31.0 | 用于可用性检查与 HEAD 请求 |
| python-dotenv | 1.0.0 | 管理环境变量，如 SECRET_KEY 与 DEBUG |
| celery | 5.3.0 | 异步任务队列（可用性检查与统计） |
| redis | 7.0 以上 | celery broker 与结果后端（生产环境必需） |
| gunicorn | 21.2.0 | 生产环境 WSGI 服务器（可选） |
| beautifulsoup4 | 4.12.0 | 用于解析文档元数据（可选，增强功能） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide/ | 如何批量添加外链？如何创建分类？如何检索文档？ |
| 管理员指南 | /docs/admin-guide/ | 如何配置可用性检查周期？如何备份索引数据库？ |
| API 参考 | /docs/api-reference/ | 如何通过 REST API 获取分类树？如何提交新链接？ |
| 部署运维 | /docs/deployment/ | 如何用 PostgreSQL + Redis + gunicorn 生产部署？ |
| 贡献者指引 | /docs/contributing/ | 代码风格、测试规范、PR 流程是怎样的？ |

## 资源列表

- h5.mobile.fuvxie.cn/Article/656123.doc
- h5.mobile.nzfnve.cn/Article/8538564.doc
- h5.mobile.cmcvrr.cn/Article/523590.doc
- h5.mobile.cmcvrr.cn/Article/1492.doc
- h5.mobile.nwbbyt.cn/Article/7459.doc
- h5.mobile.nzfnve.cn/Article/94828.doc
- h5.mobile.nzfnve.cn/Article/62199.doc
- h5.mobile.puhvjy.cn/Article/66995.doc
- h5.mobile.nwbbyt.cn/Article/46224.doc
- h5.mobile.cvsifc.cn/Article/8480.doc
- h5.mobile.fuvxie.cn/Article/9713.doc
- h5.mobile.hcbezg.cn/Article/1648.doc
- h5.mobile.cvsifc.cn/Article/9058.doc
- h5.mobile.nzfnve.cn/Article/8266953.doc
- h5.mobile.nwbbyt.cn/Article/158635.doc
- h5.mobile.nwbbyt.cn/Article/50309.doc
- h5.mobile.puhvjy.cn/Article/550720.doc
- h5.mobile.cmcvrr.cn/Article/4206425.doc
- h5.mobile.nwbbyt.cn/Article/9946.doc
- h5.mobile.hcbezg.cn/Article/6741.doc
- h5.mobile.cvsifc.cn/Article/8412979.doc
- h5.mobile.fuvxie.cn/Article/7568322.doc
- h5.mobile.cmcvrr.cn/Article/6711.doc
- h5.mobile.jnjpgf.cn/Article/74761.doc
- h5.mobile.nzfnve.cn/Article/89055.doc
- h5.mobile.fuvxie.cn/Article/79125.doc
- h5.mobile.cvsifc.cn/Article/2725836.doc
- h5.mobile.fuvxie.cn/Article/8356.doc
- h5.mobile.cmcvrr.cn/Article/413755.doc
- h5.mobile.puhvjy.cn/Article/967806.doc
- h5.mobile.hcbezg.cn/Article/8865326.doc
- h5.mobile.nzfnve.cn/Article/7781198.doc
- h5.mobile.jnjpgf.cn/Article/82496.doc
- h5.mobile.cvsifc.cn/Article/6212026.doc
- h5.mobile.puhvjy.cn/Article/24139.doc
- h5.mobile.nwbbyt.cn/Article/756218.doc
- h5.mobile.cmcvrr.cn/Article/0484925.doc
- h5.mobile.jnjpgf.cn/Article/62774.doc
- h5.mobile.cmcvrr.cn/Article/6463385.doc
- h5.mobile.puhvjy.cn/Article/91521.doc
- h5.mobile.fuvxie.cn/Article/8824286.doc
- h5.mobile.fuvxie.cn/Article/7394808.doc
- h5.mobile.puhvjy.cn/Article/97390.doc
- h5.mobile.cvsifc.cn/Article/9204.doc
- h5.mobile.nzfnve.cn/Article/30563.doc
- h5.mobile.hcbezg.cn/Article/140549.doc
- h5.mobile.cvsifc.cn/Article/6771721.doc
- h5.mobile.nwbbyt.cn/Article/6142748.doc
- h5.mobile.nwbbyt.cn/Article/2338553.doc
- h5.mobile.hcbezg.cn/Article/870568.doc
- h5.mobile.nzfnve.cn/Article/9812.doc
- h5.mobile.jnjpgf.cn/Article/4511882.doc
- h5.mobile.jnjpgf.cn/Article/4530.doc
- h5.mobile.fuvxie.cn/Article/5558652.doc
- h5.mobile.cvsifc.cn/Article/4933935.doc
- h5.mobile.jnjpgf.cn/Article/5367.doc
- h5.mobile.jnjpgf.cn/Article/67565.doc
- h5.mobile.nzfnve.cn/Article/9902735.doc
- h5.mobile.cvsifc.cn/Article/19800.doc
- h5.mobile.hcbezg.cn/Article/4463.doc
- h5.mobile.nzfnve.cn/Article/3720.doc
- h5.mobile.nzfnve.cn/Article/8227964.doc
- h5.mobile.puhvjy.cn/Article/53388.doc
- h5.mobile.nwbbyt.cn/Article/0069.doc
- h5.mobile.cvsifc.cn/Article/9922044.doc
- h5.mobile.puhvjy.cn/Article/4611.doc
- h5.mobile.puhvjy.cn/Article/9168157.doc
- h5.mobile.puhvjy.cn/Article/2843346.doc
- h5.mobile.cmcvrr.cn/Article/21609.doc
- h5.mobile.puhvjy.cn/Article/192888.doc
- h5.mobile.hcbezg.cn/Article/85555.doc
- h5.mobile.fuvxie.cn/Article/57242.doc
- h5.mobile.puhvjy.cn/Article/8882.doc
- h5.mobile.nzfnve.cn/Article/95032.doc
- h5.mobile.puhvjy.cn/Article/1314853.doc
- h5.mobile.puhvjy.cn/Article/4591713.doc
- h5.mobile.fuvxie.cn/Article/1541355.doc
- h5.mobile.nwbbyt.cn/Article/1445.doc
- h5.mobile.cvsifc.cn/Article/2350951.doc
- h5.mobile.fuvxie.cn/Article/5964997.doc
- h5.mobile.nwbbyt.cn/Article/560416.doc
- h5.mobile.puhvjy.cn/Article/76346.doc
- h5.mobile.fuvxie.cn/Article/9405312.doc
- h5.mobile.nwbbyt.cn/Article/7437.doc
- h5.mobile.cvsifc.cn/Article/5388599.doc
- h5.mobile.cmcvrr.cn/Article/6419682.doc
- h5.mobile.jnjpgf.cn/Article/4963924.doc
- h5.mobile.puhvjy.cn/Article/81485.doc
- h5.mobile.cvsifc.cn/Article/3415243.doc
- h5.mobile.nwbbyt.cn/Article/4779.doc
- h5.mobile.puhvjy.cn/Article/3846.doc
- h5.mobile.fuvxie.cn/Article/5417887.doc
- h5.mobile.jnjpgf.cn/Article/56774.doc
- h5.mobile.puhvjy.cn/Article/4455.doc
- h5.mobile.hcbezg.cn/Article/563981.doc
- h5.mobile.nzfnve.cn/Article/9830.doc
- h5.mobile.nwbbyt.cn/Article/9228148.doc
- h5.mobile.nzfnve.cn/Article/3207930.doc
- h5.mobile.cmcvrr.cn/Article/88852.doc
- h5.mobile.cmcvrr.cn/Article/4085597.doc
- h5.mobile.fuvxie.cn/Article/9884935.doc
- h5.mobile.fuvxie.cn/Article/37910.doc
- h5.mobile.fuvxie.cn/Article/777894.doc
- h5.mobile.fuvxie.cn/Article/8117.doc
- h5.mobile.cvsifc.cn/Article/3901.doc
- h5.mobile.cmcvrr.cn/Article/76735.doc
- h5.mobile.fuvxie.cn/Article/8248746.doc
- h5.mobile.nwbbyt.cn/Article/23846.doc
- h5.mobile.nwbbyt.cn/Article/2756473.doc
- h5.mobile.cmcvrr.cn/Article/866429.doc
- h5.mobile.cvsifc.cn/Article/9895982.doc
- h5.mobile.jnjpgf.cn/Article/30904.doc
- h5.mobile.puhvjy.cn/Article/3275468.doc
- h5.mobile.jnjpgf.cn/Article/29765.doc
- h5.mobile.nzfnve.cn/Article/808135.doc
- h5.mobile.fuvxie.cn/Article/35407.doc
- h5.mobile.nwbbyt.cn/Article/5411.doc
- h5.mobile.fuvxie.cn/Article/555030.doc
- h5.mobile.nzfnve.cn/Article/152933.doc
- h5.mobile.nzfnve.cn/Article/881946.doc
- h5.mobile.nzfnve.cn/Article/44332.doc
- h5.mobile.nzfnve.cn/Article/6504.doc
- h5.mobile.nwbbyt.cn/Article/31427.doc
- h5.mobile.fuvxie.cn/Article/6693.doc
- h5.mobile.nwbbyt.cn/Article/9335.doc
- h5.mobile.fuvxie.cn/Article/6482.doc
- h5.mobile.cmcvrr.cn/Article/2065.doc
- h5.mobile.fuvxie.cn/Article/0863399.doc
- h5.mobile.fuvxie.cn/Article/3226890.doc
- h5.mobile.nwbbyt.cn/Article/1585.doc
- h5.mobile.nwbbyt.cn/Article/2459.doc
- h5.mobile.jnjpgf.cn/Article/34335.doc
- h5.mobile.puhvjy.cn/Article/3099331.doc
- h5.mobile.hcbezg.cn/Article/431192.doc
- h5.mobile.nwbbyt.cn/Article/2139684.doc
- h5.mobile.fuvxie.cn/Article/781457.doc
- h5.mobile.hcbezg.cn/Article/23960.doc
- h5.mobile.fuvxie.cn/Article/62163.doc
- h5.mobile.nzfnve.cn/Article/719745.doc
- h5.mobile.cmcvrr.cn/Article/9985.doc
- h5.mobile.cvsifc.cn/Article/4017316.doc
- h5.mobile.hcbezg.cn/Article/6476.doc
- h5.mobile.cvsifc.cn/Article/7794.doc
- h5.mobile.cvsifc.cn/Article/8711.doc
- h5.mobile.cvsifc.cn/Article/2795.doc
- h5.mobile.cmcvrr.cn/Article/882545.doc
- h5.mobile.cvsifc.cn/Article/643326.doc
- h5.mobile.fuvxie.cn/Article/8158.doc
- h5.mobile.cvsifc.cn/Article/42465.doc
- h5.mobile.cmcvrr.cn/Article/11064.doc
- h5.mobile.cmcvrr.cn/Article/9746927.doc
- h5.mobile.cmcvrr.cn/Article/992200.doc
- h5.mobile.puhvjy.cn/Article/0226.doc
- h5.mobile.hcbezg.cn/Article/8502.doc
- h5.mobile.puhvjy.cn/Article/22595.doc
- h5.mobile.puhvjy.cn/Article/305711.doc
- h5.mobile.puhvjy.cn/Article/266331.doc
- h5.mobile.jnjpgf.cn/Article/45241.doc
- h5.mobile.fuvxie.cn/Article/1945.doc
- h5.mobile.cmcvrr.cn/Article/0069.doc
- h5.mobile.nzfnve.cn/Article/7922.doc
- h5.mobile.cmcvrr.cn/Article/6311997.doc
- h5.mobile.hcbezg.cn/Article/1765.doc
- h5.mobile.cvsifc.cn/Article/1451790.doc
- h5.mobile.jnjpgf.cn/Article/3127.doc
- h5.mobile.fuvxie.cn/Article/96590.doc
- h5.mobile.nwbbyt.cn/Article/0632168.doc
- h5.mobile.jnjpgf.cn/Article/58708.doc
- h5.mobile.hcbezg.cn/Article/6597.doc
- h5.mobile.jnjpgf.cn/Article/653844.doc
- h5.mobile.cmcvrr.cn/Article/720772.doc
- h5.mobile.jnjpgf.cn/Article/316976.doc
- h5.mobile.nzfnve.cn/Article/3967.doc
- h5.mobile.jnjpgf.cn/Article/896556.doc
- h5.mobile.nwbbyt.cn/Article/6526858.doc
- h5.mobile.jnjpgf.cn/Article/017281.doc
- h5.mobile.fuvxie.cn/Article/43381.doc
- h5.mobile.cmcvrr.cn/Article/0237303.doc
- h5.mobile.cvsifc.cn/Article/16222.doc
- h5.mobile.nwbbyt.cn/Article/72927.doc
- h5.mobile.fuvxie.cn/Article/212498.doc
- h5.mobile.cmcvrr.cn/Article/9590239.doc
- h5.mobile.cvsifc.cn/Article/7065891.doc
- h5.mobile.cmcvrr.cn/Article/9306.doc
- h5.mobile.cvsifc.cn/Article/627266.doc
- h5.mobile.fuvxie.cn/Article/6526405.doc
- h5.mobile.cmcvrr.cn/Article/6469.doc
- h5.mobile.jnjpgf.cn/Article/265278.doc
- h5.mobile.fuvxie.cn/Article/1383749.doc
- h5.mobile.jnjpgf.cn/Article/8359.doc
- h5.mobile.nzfnve.cn/Article/1593826.doc
- h5.mobile.nzfnve.cn/Article/72806.doc
- h5.mobile.nzfnve.cn/Article/820691.doc
- h5.mobile.fuvxie.cn/Article/62144.doc
- h5.mobile.hcbezg.cn/Article/8076.doc
- h5.mobile.puhvjy.cn/Article/0675456.doc
- h5.mobile.cmcvrr.cn/Article/102947.doc
- h5.mobile.nzfnve.cn/Article/804031.doc
- h5.mobile.hcbezg.cn/Article/0880323.doc
- h5.mobile.hcbezg.cn/Article/13720.doc
- h5.mobile.jnjpgf.cn/Article/9194688.doc
- h5.mobile.puhvjy.cn/Article/508539.doc
- h5.mobile.puhvjy.cn/Article/81020.doc
- h5.mobile.puhvjy.cn/Article/6181416.doc
- h5.mobile.hcbezg.cn/Article/63749.doc
- h5.mobile.cvsifc.cn/Article/58224.doc
- h5.mobile.nwbbyt.cn/Article/05726.doc
- h5.mobile.nzfnve.cn/Article/429133.doc
- h5.mobile.cvsifc.cn/Article/9279006.doc
- h5.mobile.nzfnve.cn/Article/9569.doc
- h5.mobile.fuvxie.cn/Article/5081389.doc
- h5.mobile.fuvxie.cn/Article/3843.doc
- h5.mobile.hcbezg.cn/Article/70509.doc
- h5.mobile.hcbezg.cn/Article/473915.doc
- h5.mobile.jnjpgf.cn/Article/0946.doc
- h5.mobile.hcbezg.cn/Article/012090.doc
- h5.mobile.hcbezg.cn/Article/5212238.doc
- h5.mobile.nzfnve.cn/Article/7300.doc
- h5.mobile.puhvjy.cn/Article/7622.doc
- h5.mobile.cmcvrr.cn/Article/35019.doc
- h5.mobile.nwbbyt.cn/Article/2353564.doc
- h5.mobile.cvsifc.cn/Article/562036.doc
- h5.mobile.cvsifc.cn/Article/413386.doc
- h5.mobile.fuvxie.cn/Article/7464412.doc
- h5.mobile.cmcvrr.cn/Article/3400920.doc
- h5.mobile.fuvxie.cn/Article/95396.doc
- h5.mobile.nzfnve.cn/Article/9214219.doc
- h5.mobile.cvsifc.cn/Article/3628.doc
- h5.mobile.nzfnve.cn/Article/7837.doc
- h5.mobile.puhvjy.cn/Article/14903.doc
- h5.mobile.hcbezg.cn/Article/2061.doc
- h5.mobile.puhvjy.cn/Article/243711.doc
- h5.mobile.cmcvrr.cn/Article/6833386.doc
- h5.mobile.cmcvrr.cn/Article/8034167.doc
- h5.mobile.nzfnve.cn/Article/12538.doc
- h5.mobile.nwbbyt.cn/Article/8122.doc
- h5.mobile.cmcvrr.cn/Article/147646.doc
- h5.mobile.nzfnve.cn/Article/816922.doc
- h5.mobile.hcbezg.cn/Article/86048.doc
- h5.mobile.cvsifc.cn/Article/988343.doc
- h5.mobile.nwbbyt.cn/Article/7494.doc
- h5.mobile.nzfnve.cn/Article/7480419.doc
- h5.mobile.puhvjy.cn/Article/0546241.doc
- h5.mobile.nzfnve.cn/Article/3995913.doc
- h5.mobile.jnjpgf.cn/Article/9142.doc
- h5.mobile.puhvjy.cn/Article/87123.doc
- h5.mobile.puhvjy.cn/Article/147174.doc
- h5.mobile.cvsifc.cn/Article/44416.doc
- h5.mobile.nzfnve.cn/Article/11316.doc
- h5.mobile.nzfnve.cn/Article/293811.doc

## 项目结构

```
doclink-hub/
├── manage.py                         # Django 项目管理入口
├── requirements.txt                  # 生产环境依赖列表
├── .env.example                      # 环境变量模板（数据库/缓存/密钥）
├── doclink_hub/
│   ├── __init__.py
│   ├── settings.py                   # 主配置（含数据库、中间件、静态文件）
│   ├── urls.py                       # 根路由（API + 管理后台）
│   └── wsgi.py                       # 生产 WSGI 入口
├── apps/
│   ├── links/                        # 核心外链管理模块
│   │   ├── models.py                 # Link, Category, Tag, AccessLog
│   │   ├── admin.py                  # 后台注册与列表展示定制
│   │   ├── views.py                  # 分类树、检索、导入、统计接口
│   │   ├── serializers.py            # DRF 序列化器
│   │   ├── tasks.py                  # Celery 任务（可用性检查、统计聚合）
│   │   └── validators.py             # URL 规范化与去重校验
│   ├── checker/                      # 可用性检查子模块
│   │   ├── head_client.py            # 并发 HEAD 请求池
│   │   └── result_handler.py         # 更新数据库状态与触发告警
│   └── api/                          # RESTful API 版本控制与认证
│       ├── v1/
│       │   ├── endpoints.py          # /api/v1/links, /api/v1/categories
│       │   └── permissions.py        # 基于角色的访问控制
│       └── v2/                       # 预留扩展
├── static/                           # 静态资源（CSS/JS 压缩后）
│   ├── css/
│   └── js/
├── templates/                        # Django 模板（管理界面）
│   ├── base.html
│   └── dashboard.html
├── scripts/                          # 运维与数据迁移脚本
│   ├── import_links.py               # 批量导入文本链接
│   └── export_report.py              # 生成可用性报告 CSV
├── tests/                            # 单元测试与集成测试
│   ├── test_models.py
│   ├── test_api.py
│   └── test_checker.py
└── docs/                             # 文档源码（Markdown）
    ├── user-guide/
    ├── admin-guide/
    └── api-reference/
```

## 贡献指南

提交 Issue 或功能请求：在 GitHub Issues 页面新建问题，请使用提供的模板，明确说明问题类型（缺陷/增强/文档），并附上重现步骤或预期行为描述。对于外链导入相关的缺陷，请提供至少 5 条示例 URL。

创建分支并本地开发：从 main 分支签出新的 feature 分支，命名格式为 `feature/功能简述` 或 `fix/问题编号`。确保本地开发环境已安装所有依赖，并运行 `pre-commit install` 启用代码风格检查（black + isort + flake8）。

编写测试用例：所有新增或修改的功能必须附带对应的单元测试，测试文件置于 `tests/` 目录下，命名与模块对应。运行 `python manage.py test` 确保全部测试通过，且覆盖率不低于 85%。

提交 Pull Request：推送分支至远程仓库后，在 GitHub 发起 PR 至 main 分支。PR 描述中应引用相关的 Issue 编号，并列出变更摘要、测试结果截图（如有 UI 改动）以及任何可能影响现有 API 的破坏性变更。至少需要一名核心维护者 Approve 方可合并。

更新文档：若变更涉及用户可见功能（如新增 API 字段、修改配置变量），请同步更新 `docs/` 下对应的 Markdown 文件，并在 PR 中标注“文档已更新”。

## 常见问题

Q: 导入外链时提示“URL 格式无效”，但我确认链接可以正常访问。

A: 默认校验规则要求 URL 必须包含协议头（http:// 或 https://）。如果您的数据源自纯域名或缺少协议，可在 `settings.py` 中设置 `LINK_URL_RELAXED = True` 以放宽校验，但建议在导入前使用脚本统一补全协议。同时请检查是否包含末尾多余的斜杠或空格。

Q: 可用性检查任务总是超时，导致大量链接被标记为“不可用”。

A: 检查 Celery worker 的并发数是否过高（默认 4）。对于数百个外链，建议将 `CHECKER_CONCURRENCY` 设为 2，并增加 `CHECKER_TIMEOUT` 至 10 秒。同时确认 Redis 连接池大小足够，避免连接泄漏。可在管理员后台手动触发“重新检查”以覆盖错误标记。

Q: 预览模式无法显示文档内容，只显示空白页或跨域错误。

A: 预览功能依赖目标服务器返回 `X-Frame-Options` 允许同源或特定域名。若目标服务器未配置，则无法内联预览。此时系统会自动降级为“直接跳转”模式，这属于正常行为，并非功能缺陷。您也可以将 `PREVIEW_ALLOWED_DOMAINS` 设置为空列表，完全禁用预览，强制跳转。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

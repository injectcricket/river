# LinkMaster Pro

LinkMaster Pro 是一个面向技术团队与个人开发者的外链资源归集与健康度监控平台。该项目定位于解决技术文档、博客、教程及开源项目中外部引用链接频繁失效、来源不可追溯、域名迁移难以同步等痛点。LinkMaster Pro 提供从链接抓取、状态巡检、分类索引到变更通知的完整闭环能力，适用于需要长期维护大量外链资源的项目文档站、知识库、导航站及技术聚合平台。本项目当前批次为第 3/160 批，共计管理 250 个资源链接，覆盖多个内容源域名的文章级引用记录。

## 功能概览

批量链接解析与标准化入库：支持从文本、Markdown、HTML 等多种格式中自动提取 URL，并依据项目内建规则完成去重、格式清洗及协议补齐检测。

多源域名分组与标签系统：基于域名主键自动聚合链接，支持自定义标签与业务分类，便于按项目、团队或内容主题进行权限隔离与视图筛选。

链接可达性定时巡检：内置轮询调度器，可配置巡检周期（小时/天/周），对每一条链接发起 HEAD/GET 请求，记录响应状态码、响应时间及重定向链。

变更事件通知机制：当链接状态发生变更（如从 200 变为 404、301 跳转目标变动、域名解析失败）时，通过预设的 Webhook 或邮件渠道向订阅者发送告警。

元数据自动补全：自动提取链接对应页面的标题、描述、关键词及最后修改时间，降低人工维护成本，支持自定义字段扩展。

数据导入导出与迁移工具：提供 JSON、CSV、SQLite 三种格式的完整数据导出，支持从旧版系统或第三方书签服务无缝迁移链接库。

访问统计与热度分析：记录每一条链接的查询频次、引用来源及最近访问时间，输出热度排行与沉寂链接清单，辅助内容运营决策。

RESTful API 与 CLI 双端交互：提供完整的 OpenAPI 文档和命令行工具，便于集成到 CI/CD 管道或自动化脚本中，实现无头化运维。

## 应用场景

技术文档站的链接资产盘点：大型开源项目的文档站往往包含数百条指向外部 API 参考、SDK 仓库、社区讨论帖的链接。LinkMaster Pro 可周期性扫描这些链接，生成健康度报表，在版本发布前帮助文档维护者提前发现失效引用。

知识库与内部 Wiki 的链接治理：企业内部知识库中积累了大量过时的外部链接，通过本平台可快速识别指向已下线服务或已迁移文档的链接，并批量替换为最新有效地址，保证知识资产的可用性。

个人技术博客的链接保鲜：独立博客作者在撰写技术文章时经常引用外部资料。使用 LinkMaster Pro 的定时巡检功能，可及时发现友链失效或外部参考页面的变动，避免读者遭遇死链。

开源项目 README 与贡献指南的链接审核：在开源项目中，README 文件通常包含大量安装源、示例项目、社区论坛等链接。LinkMaster Pro 能够在 PR 合并前自动检测新增或变更的链接可达性，将质量检查左移。

技术导航站与资源聚合页的自动更新：面向特定技术领域（如前端框架、机器学习工具、运维插件）的导航站点依赖大量外链。借助本平台，站点运营者可自动获取链接状态变更，动态调整导航页面的显示与排序。

## 快速开始

以下命令演示如何在本地环境完成 LinkMaster Pro 的克隆、安装及初次启动。

```bash
git clone https://github.com/linkmaster-pro/linkmaster.git
cd linkmaster
pip install -r requirements.txt
cp .env.example .env
python manage.py migrate
python manage.py import-links --batch 3 --source ./data/batch_160.csv
python manage.py schedule --interval hourly
python manage.py runserver --port 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 及以上 | 核心运行环境，建议使用 pyenv 管理版本 |
| PostgreSQL | 14.0 及以上 | 生产环境默认数据库，存储链接元数据与巡检记录 |
| Redis | 7.0 及以上 | 用作消息队列缓存和调度器状态存储 |
| Celery | 5.3 及以上 | 分布式任务队列，用于执行巡检与异步导出任务 |
| Node.js | 18.0 及以上 | 仅当开启 Web UI 或前端构建时需要 |
| Docker | 20.10 及以上 | 可选，用于容器化部署与开发环境快速搭建 |
| Git | 2.30 及以上 | 用于版本管理与补丁同步 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | /docs/user-guide/quick-start.md | 如何安装部署、配置首次巡检、导入第一批链接 |
| 管理手册 | /docs/admin/configuration.md | 如何调整巡检频率、设置通知规则、管理域名黑名单 |
| 开发文档 | /docs/development/api-reference.md | RESTful API 的详细端点说明、请求示例与错误码 |
| 运维手册 | /docs/operations/monitoring.md | 如何监控系统健康、备份数据库、扩展 Celery Worker 数量 |

## 资源列表

- https://www.read.fuvxie.cn/Article/656123.shtml
- https://www.read.nzfnve.cn/Article/8538564.shtml
- https://www.read.cmcvrr.cn/Article/523590.shtml
- https://www.read.cmcvrr.cn/Article/1492.shtml
- https://www.read.nwbbyt.cn/Article/7459.shtml
- https://www.read.nzfnve.cn/Article/94828.shtml
- https://www.read.nzfnve.cn/Article/62199.shtml
- https://www.read.puhvjy.cn/Article/66995.shtml
- https://www.read.nwbbyt.cn/Article/46224.shtml
- https://www.read.cvsifc.cn/Article/8480.shtml
- https://www.read.fuvxie.cn/Article/9713.shtml
- https://www.read.hcbezg.cn/Article/1648.shtml
- https://www.read.cvsifc.cn/Article/9058.shtml
- https://www.read.nzfnve.cn/Article/8266953.shtml
- https://www.read.nwbbyt.cn/Article/158635.shtml
- https://www.read.nwbbyt.cn/Article/50309.shtml
- https://www.read.puhvjy.cn/Article/550720.shtml
- https://www.read.cmcvrr.cn/Article/4206425.shtml
- https://www.read.nwbbyt.cn/Article/9946.shtml
- https://www.read.hcbezg.cn/Article/6741.shtml
- https://www.read.cvsifc.cn/Article/8412979.shtml
- https://www.read.fuvxie.cn/Article/7568322.shtml
- https://www.read.cmcvrr.cn/Article/6711.shtml
- https://www.read.jnjpgf.cn/Article/74761.shtml
- https://www.read.nzfnve.cn/Article/89055.shtml
- https://www.read.fuvxie.cn/Article/79125.shtml
- https://www.read.cvsifc.cn/Article/2725836.shtml
- https://www.read.fuvxie.cn/Article/8356.shtml
- https://www.read.cmcvrr.cn/Article/413755.shtml
- https://www.read.puhvjy.cn/Article/967806.shtml
- https://www.read.hcbezg.cn/Article/8865326.shtml
- https://www.read.nzfnve.cn/Article/7781198.shtml
- https://www.read.jnjpgf.cn/Article/82496.shtml
- https://www.read.cvsifc.cn/Article/6212026.shtml
- https://www.read.puhvjy.cn/Article/24139.shtml
- https://www.read.nwbbyt.cn/Article/756218.shtml
- https://www.read.cmcvrr.cn/Article/0484925.shtml
- https://www.read.jnjpgf.cn/Article/62774.shtml
- https://www.read.cmcvrr.cn/Article/6463385.shtml
- https://www.read.puhvjy.cn/Article/91521.shtml
- https://www.read.fuvxie.cn/Article/8824286.shtml
- https://www.read.fuvxie.cn/Article/7394808.shtml
- https://www.read.puhvjy.cn/Article/97390.shtml
- https://www.read.cvsifc.cn/Article/9204.shtml
- https://www.read.nzfnve.cn/Article/30563.shtml
- https://www.read.hcbezg.cn/Article/140549.shtml
- https://www.read.cvsifc.cn/Article/6771721.shtml
- https://www.read.nwbbyt.cn/Article/6142748.shtml
- https://www.read.nwbbyt.cn/Article/2338553.shtml
- https://www.read.hcbezg.cn/Article/870568.shtml
- https://www.read.nzfnve.cn/Article/9812.shtml
- https://www.read.jnjpgf.cn/Article/4511882.shtml
- https://www.read.jnjpgf.cn/Article/4530.shtml
- https://www.read.fuvxie.cn/Article/5558652.shtml
- https://www.read.cvsifc.cn/Article/4933935.shtml
- https://www.read.jnjpgf.cn/Article/5367.shtml
- https://www.read.jnjpgf.cn/Article/67565.shtml
- https://www.read.nzfnve.cn/Article/9902735.shtml
- https://www.read.cvsifc.cn/Article/19800.shtml
- https://www.read.hcbezg.cn/Article/4463.shtml
- https://www.read.nzfnve.cn/Article/3720.shtml
- https://www.read.nzfnve.cn/Article/8227964.shtml
- https://www.read.puhvjy.cn/Article/53388.shtml
- https://www.read.nwbbyt.cn/Article/0069.shtml
- https://www.read.cvsifc.cn/Article/9922044.shtml
- https://www.read.puhvjy.cn/Article/4611.shtml
- https://www.read.puhvjy.cn/Article/9168157.shtml
- https://www.read.puhvjy.cn/Article/2843346.shtml
- https://www.read.cmcvrr.cn/Article/21609.shtml
- https://www.read.puhvjy.cn/Article/192888.shtml
- https://www.read.hcbezg.cn/Article/85555.shtml
- https://www.read.fuvxie.cn/Article/57242.shtml
- https://www.read.puhvjy.cn/Article/8882.shtml
- https://www.read.nzfnve.cn/Article/95032.shtml
- https://www.read.puhvjy.cn/Article/1314853.shtml
- https://www.read.puhvjy.cn/Article/4591713.shtml
- https://www.read.fuvxie.cn/Article/1541355.shtml
- https://www.read.nwbbyt.cn/Article/1445.shtml
- https://www.read.cvsifc.cn/Article/2350951.shtml
- https://www.read.fuvxie.cn/Article/5964997.shtml
- https://www.read.nwbbyt.cn/Article/560416.shtml
- https://www.read.puhvjy.cn/Article/76346.shtml
- https://www.read.fuvxie.cn/Article/9405312.shtml
- https://www.read.nwbbyt.cn/Article/7437.shtml
- https://www.read.cvsifc.cn/Article/5388599.shtml
- https://www.read.cmcvrr.cn/Article/6419682.shtml
- https://www.read.jnjpgf.cn/Article/4963924.shtml
- https://www.read.puhvjy.cn/Article/81485.shtml
- https://www.read.cvsifc.cn/Article/3415243.shtml
- https://www.read.nwbbyt.cn/Article/4779.shtml
- https://www.read.puhvjy.cn/Article/3846.shtml
- https://www.read.fuvxie.cn/Article/5417887.shtml
- https://www.read.jnjpgf.cn/Article/56774.shtml
- https://www.read.puhvjy.cn/Article/4455.shtml
- https://www.read.hcbezg.cn/Article/563981.shtml
- https://www.read.nzfnve.cn/Article/9830.shtml
- https://www.read.nwbbyt.cn/Article/9228148.shtml
- https://www.read.nzfnve.cn/Article/3207930.shtml
- https://www.read.cmcvrr.cn/Article/88852.shtml
- https://www.read.cmcvrr.cn/Article/4085597.shtml
- https://www.read.fuvxie.cn/Article/9884935.shtml
- https://www.read.fuvxie.cn/Article/37910.shtml
- https://www.read.fuvxie.cn/Article/777894.shtml
- https://www.read.fuvxie.cn/Article/8117.shtml
- https://www.read.cvsifc.cn/Article/3901.shtml
- https://www.read.cmcvrr.cn/Article/76735.shtml
- https://www.read.fuvxie.cn/Article/8248746.shtml
- https://www.read.nwbbyt.cn/Article/23846.shtml
- https://www.read.nwbbyt.cn/Article/2756473.shtml
- https://www.read.cmcvrr.cn/Article/866429.shtml
- https://www.read.cvsifc.cn/Article/9895982.shtml
- https://www.read.jnjpgf.cn/Article/30904.shtml
- https://www.read.puhvjy.cn/Article/3275468.shtml
- https://www.read.jnjpgf.cn/Article/29765.shtml
- https://www.read.nzfnve.cn/Article/808135.shtml
- https://www.read.fuvxie.cn/Article/35407.shtml
- https://www.read.nwbbyt.cn/Article/5411.shtml
- https://www.read.fuvxie.cn/Article/555030.shtml
- https://www.read.nzfnve.cn/Article/152933.shtml
- https://www.read.nzfnve.cn/Article/881946.shtml
- https://www.read.nzfnve.cn/Article/44332.shtml
- https://www.read.nzfnve.cn/Article/6504.shtml
- https://www.read.nwbbyt.cn/Article/31427.shtml
- https://www.read.fuvxie.cn/Article/6693.shtml
- https://www.read.nwbbyt.cn/Article/9335.shtml
- https://www.read.fuvxie.cn/Article/6482.shtml
- https://www.read.cmcvrr.cn/Article/2065.shtml
- https://www.read.fuvxie.cn/Article/0863399.shtml
- https://www.read.fuvxie.cn/Article/3226890.shtml
- https://www.read.nwbbyt.cn/Article/1585.shtml
- https://www.read.nwbbyt.cn/Article/2459.shtml
- https://www.read.jnjpgf.cn/Article/34335.shtml
- https://www.read.puhvjy.cn/Article/3099331.shtml
- https://www.read.hcbezg.cn/Article/431192.shtml
- https://www.read.nwbbyt.cn/Article/2139684.shtml
- https://www.read.fuvxie.cn/Article/781457.shtml
- https://www.read.hcbezg.cn/Article/23960.shtml
- https://www.read.fuvxie.cn/Article/62163.shtml
- https://www.read.nzfnve.cn/Article/719745.shtml
- https://www.read.cmcvrr.cn/Article/9985.shtml
- https://www.read.cvsifc.cn/Article/4017316.shtml
- https://www.read.hcbezg.cn/Article/6476.shtml
- https://www.read.cvsifc.cn/Article/7794.shtml
- https://www.read.cvsifc.cn/Article/8711.shtml
- https://www.read.cvsifc.cn/Article/2795.shtml
- https://www.read.cmcvrr.cn/Article/882545.shtml
- https://www.read.cvsifc.cn/Article/643326.shtml
- https://www.read.fuvxie.cn/Article/8158.shtml
- https://www.read.cvsifc.cn/Article/42465.shtml
- https://www.read.cmcvrr.cn/Article/11064.shtml
- https://www.read.cmcvrr.cn/Article/9746927.shtml
- https://www.read.cmcvrr.cn/Article/992200.shtml
- https://www.read.puhvjy.cn/Article/0226.shtml
- https://www.read.hcbezg.cn/Article/8502.shtml
- https://www.read.puhvjy.cn/Article/22595.shtml
- https://www.read.puhvjy.cn/Article/305711.shtml
- https://www.read.puhvjy.cn/Article/266331.shtml
- https://www.read.jnjpgf.cn/Article/45241.shtml
- https://www.read.fuvxie.cn/Article/1945.shtml
- https://www.read.cmcvrr.cn/Article/0069.shtml
- https://www.read.nzfnve.cn/Article/7922.shtml
- https://www.read.cmcvrr.cn/Article/6311997.shtml
- https://www.read.hcbezg.cn/Article/1765.shtml
- https://www.read.cvsifc.cn/Article/1451790.shtml
- https://www.read.jnjpgf.cn/Article/3127.shtml
- https://www.read.fuvxie.cn/Article/96590.shtml
- https://www.read.nwbbyt.cn/Article/0632168.shtml
- https://www.read.jnjpgf.cn/Article/58708.shtml
- https://www.read.hcbezg.cn/Article/6597.shtml
- https://www.read.jnjpgf.cn/Article/653844.shtml
- https://www.read.cmcvrr.cn/Article/720772.shtml
- https://www.read.jnjpgf.cn/Article/316976.shtml
- https://www.read.nzfnve.cn/Article/3967.shtml
- https://www.read.jnjpgf.cn/Article/896556.shtml
- https://www.read.nwbbyt.cn/Article/6526858.shtml
- https://www.read.jnjpgf.cn/Article/017281.shtml
- https://www.read.fuvxie.cn/Article/43381.shtml
- https://www.read.cmcvrr.cn/Article/0237303.shtml
- https://www.read.cvsifc.cn/Article/16222.shtml
- https://www.read.nwbbyt.cn/Article/72927.shtml
- https://www.read.fuvxie.cn/Article/212498.shtml
- https://www.read.cmcvrr.cn/Article/9590239.shtml
- https://www.read.cvsifc.cn/Article/7065891.shtml
- https://www.read.cmcvrr.cn/Article/9306.shtml
- https://www.read.cvsifc.cn/Article/627266.shtml
- https://www.read.fuvxie.cn/Article/6526405.shtml
- https://www.read.cmcvrr.cn/Article/6469.shtml
- https://www.read.jnjpgf.cn/Article/265278.shtml
- https://www.read.fuvxie.cn/Article/1383749.shtml
- https://www.read.jnjpgf.cn/Article/8359.shtml
- https://www.read.nzfnve.cn/Article/1593826.shtml
- https://www.read.nzfnve.cn/Article/72806.shtml
- https://www.read.nzfnve.cn/Article/820691.shtml
- https://www.read.fuvxie.cn/Article/62144.shtml
- https://www.read.hcbezg.cn/Article/8076.shtml
- https://www.read.puhvjy.cn/Article/0675456.shtml
- https://www.read.cmcvrr.cn/Article/102947.shtml
- https://www.read.nzfnve.cn/Article/804031.shtml
- https://www.read.hcbezg.cn/Article/0880323.shtml
- https://www.read.hcbezg.cn/Article/13720.shtml
- https://www.read.jnjpgf.cn/Article/9194688.shtml
- https://www.read.puhvjy.cn/Article/508539.shtml
- https://www.read.puhvjy.cn/Article/81020.shtml
- https://www.read.puhvjy.cn/Article/6181416.shtml
- https://www.read.hcbezg.cn/Article/63749.shtml
- https://www.read.cvsifc.cn/Article/58224.shtml
- https://www.read.nwbbyt.cn/Article/05726.shtml
- https://www.read.nzfnve.cn/Article/429133.shtml
- https://www.read.cvsifc.cn/Article/9279006.shtml
- https://www.read.nzfnve.cn/Article/9569.shtml
- https://www.read.fuvxie.cn/Article/5081389.shtml
- https://www.read.fuvxie.cn/Article/3843.shtml
- https://www.read.hcbezg.cn/Article/70509.shtml
- https://www.read.hcbezg.cn/Article/473915.shtml
- https://www.read.jnjpgf.cn/Article/0946.shtml
- https://www.read.hcbezg.cn/Article/012090.shtml
- https://www.read.hcbezg.cn/Article/5212238.shtml
- https://www.read.nzfnve.cn/Article/7300.shtml
- https://www.read.puhvjy.cn/Article/7622.shtml
- https://www.read.cmcvrr.cn/Article/35019.shtml
- https://www.read.nwbbyt.cn/Article/2353564.shtml
- https://www.read.cvsifc.cn/Article/562036.shtml
- https://www.read.cvsifc.cn/Article/413386.shtml
- https://www.read.fuvxie.cn/Article/7464412.shtml
- https://www.read.cmcvrr.cn/Article/3400920.shtml
- https://www.read.fuvxie.cn/Article/95396.shtml
- https://www.read.nzfnve.cn/Article/9214219.shtml
- https://www.read.cvsifc.cn/Article/3628.shtml
- https://www.read.nzfnve.cn/Article/7837.shtml
- https://www.read.puhvjy.cn/Article/14903.shtml
- https://www.read.hcbezg.cn/Article/2061.shtml
- https://www.read.puhvjy.cn/Article/243711.shtml
- https://www.read.cmcvrr.cn/Article/6833386.shtml
- https://www.read.cmcvrr.cn/Article/8034167.shtml
- https://www.read.nzfnve.cn/Article/12538.shtml
- https://www.read.nwbbyt.cn/Article/8122.shtml
- https://www.read.cmcvrr.cn/Article/147646.shtml
- https://www.read.nzfnve.cn/Article/816922.shtml
- https://www.read.hcbezg.cn/Article/86048.shtml
- https://www.read.cvsifc.cn/Article/988343.shtml
- https://www.read.nwbbyt.cn/Article/7494.shtml
- https://www.read.nzfnve.cn/Article/7480419.shtml
- https://www.read.puhvjy.cn/Article/0546241.shtml
- https://www.read.nzfnve.cn/Article/3995913.shtml
- https://www.read.jnjpgf.cn/Article/9142.shtml
- https://www.read.puhvjy.cn/Article/87123.shtml
- https://www.read.puhvjy.cn/Article/147174.shtml
- https://www.read.cvsifc.cn/Article/44416.shtml
- https://www.read.nzfnve.cn/Article/11316.shtml
- https://www.read.nzfnve.cn/Article/293811.shtml

## 项目结构

```
linkmaster/
├── cmd/                                  # 命令行入口与启动脚本
│   ├── server/                           # Web 服务启动入口
│   │   └── main.go                       # 主服务进程初始化
│   └── cli/                              # CLI 工具命令集合
│       ├── import.go                     # 链接导入子命令
│       ├── check.go                      # 手动触发巡检子命令
│       └── export.go                     # 数据导出子命令
├── internal/                             # 内部核心库（不对外暴露）
│   ├── crawler/                          # 链接抓取与解析引擎
│   │   ├── parser.go                     # HTML/Markdown 解析器
│   │   └── fetcher.go                    # HTTP 请求与重定向处理
│   ├── scheduler/                        # 巡检调度器
│   │   ├── cron.go                       # 基于 Cron 的定时任务管理
│   │   └── worker.go                     # Celery 工作节点逻辑
│   ├── notifier/                         # 通知模块
│   │   ├── webhook.go                    # 通用 Webhook 发送器
│   │   └── mailer.go                     # SMTP 邮件通知封装
│   └── storage/                          # 数据访问层
│       ├── postgres.go                   # PostgreSQL 驱动实现
│       └── cache.go                      # Redis 缓存操作接口
├── pkg/                                  # 可被外部引用的公共库
│   ├── models/                           # 数据模型定义
│   │   ├── link.go                       # 链接实体与状态枚举
│   │   └── domain.go                     # 域名聚合统计模型
│   └── utils/                            # 工具函数集合
│       ├── url_cleaner.go                # URL 清洗与规范化
│       └── batch_processor.go            # 批量任务分片处理
├── web/                                  # Web UI 及静态资源
│   ├── static/                           # CSS、JavaScript 静态文件
│   ├── templates/                        # 后台管理界面模板
│   └── api/                              # RESTful API 路由定义
│       └── v1/                           # API 版本 v1 端点实现
├── configs/                              # 配置文件目录
│   ├── application.yaml                  # 主应用配置（端口、日志级别）
│   └── scheduler.yaml                    # 巡检策略与通知规则配置
├── scripts/                              # 运维辅助脚本
│   ├── migration/                        # 数据库迁移脚本
│   └── seed/                             # 测试数据填充与示例导入
├── tests/                                # 单元测试与集成测试
│   ├── unit/                             # 单元测试用例
│   └── integration/                      # 依赖外部服务的集成测试
├── docs/                                 # 项目文档
│   ├── user-guide/                       # 用户手册
│   ├── admin/                            # 管理运维手册
│   └── development/                      # 开发贡献指南
├── go.mod                                # Go 模块依赖定义
├── go.sum                                # 依赖校验和
├── Dockerfile                            # 容器镜像构建文件
├── docker-compose.yaml                   # 本地开发环境编排配置
└── README.md                             # 项目介绍与快速入门
```

## 贡献指南

提交 Issue 描述缺陷或功能需求：在 GitHub Issue 列表中选择对应模板，清晰描述复现步骤、预期行为与实际行为，并附上相关日志或截图。对于功能需求，需说明使用场景与期望的接口变更。

Fork 主仓库并创建功能分支：将主仓库 Fork 至个人账号下，基于 main 分支创建新的 feature/xxx 或 fix/xxx 分支，分支名称需简要概括改动目的。

编写代码与单元测试：遵循项目内 .golangci.yml 定义的代码风格规范，所有新增或修改的公开函数必须包含对应的单元测试用例，确保测试覆盖率达到 80% 以上。

提交 Pull Request 并关联 Issue：提交 PR 时需填写完整模板，描述改动内容、测试结果及影响范围。PR 标题应遵循 Conventional Commits 格式。在 PR 描述中通过关键词关联相关 Issue。

接受 Code Review 并完成合并：项目维护者将对 PR 进行逐行审查，提出修改意见。贡献者需在 5 个工作日内响应并推送更新。通过 CI 流水线检查后，由维护者执行 Squash 合并。

## 常见问题

Q: 导入 250 个链接时出现超时或内存溢出，应如何优化？

A: LinkMaster Pro 默认采用分片导入策略，每批处理 50 条记录。若仍出现超时，可调整配置项 BATCH_SIZE 和 IMPORT_TIMEOUT。对于内存敏感环境，建议启用 Redis 作为临时缓冲区，通过 STREAM 模式流式处理大文件。此外，可使用 CLI 命令 linkmaster import --batch 3 --chunk-size 25 进一步降低单次内存占用。

Q: 巡检任务未按预期执行，如何排查调度器状态？

A: 首先检查 Celery Worker 是否正常启动，可通过 celery status 命令查看活跃节点。其次，确认 Redis 服务连通性及 scheduler.yaml 中的 cron 表达式是否正确。若任务已触发但未执行，查看日志中关键字 task_timeout 或 retry_count，并根据错误码查阅 /docs/operations/monitoring.md 中的故障排除对照表。也可通过 Web 管理界面手动触发单次巡检以验证链路完整性。

Q: 如何从旧版书签系统迁移历史链接数据？

A: 项目提供通用的 CSV 和 JSON 导入接口。若书签系统支持导出为 HTML 书签文件，可先使用 scripts/seed/convert_bookmark.py 将 Netscape 格式转换为 LinkMaster Pro 的标准 JSON 结构。转换后通过 POST /api/v1/links/import 端点提交，系统会自动完成域名聚合与状态初始化。若需保留原始创建时间，可在导入数据中附加 created_at 字段。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:20

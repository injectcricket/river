# TechReads 技术外链聚合平台

TechReads 是一个面向开发者与技术研究人员的轻量级技术文章外链聚合平台，专注于从多源技术社区自动采集、分类、索引高质量的技术文章与工程实践文档。平台本身不存储文章内容，而是通过结构化的外链管理机制，帮助用户快速定位特定领域的技术资料，降低信息筛选成本。

项目定位为技术团队内部知识库的补充组件，也可作为个人开发者的技术阅读聚合入口。目标用户包括后端工程师、运维工程师、架构师与技术管理者。通过统一的条目索引与标签体系，TechReads 将分散在多个技术博客、新闻站点与官方文档中的优质内容整合为可检索、可订阅的外链集合，解决技术资料散落、重复查找效率低下的问题。

## 功能概览

多源外链聚合采集：支持从配置的多个技术源站点定时抓取文章元数据，包括标题、发布时间、摘要与原始链接，自动去重并入库。

条目级标签分类：每条外链支持自定义标签与自动标签推荐，标签体系涵盖编程语言、框架、基础设施、架构模式、运维工具等维度。

全文检索与过滤：基于标题与摘要内容提供全文检索能力，支持按标签、发布时间段、来源域名等多条件组合过滤。

阅读状态跟踪：为注册用户提供已读/未读标记、收藏与稍后阅读功能，支持跨设备同步阅读进度。

RSS 订阅生成：每个标签与组合过滤条件均可生成专属 RSS 订阅源，用户可在任意阅读器中订阅更新。

外链健康检查：定期对已收录链接进行可用性探测，自动标记失效链接，并提供失效通知与管理界面。

开放 API 接口：提供 RESTful API 供第三方工具批量查询、导入或导出外链数据，支持 JSON 与 RSS 格式输出。

管理后台与审核流：管理员可通过后台批量导入、编辑、删除条目，支持审核新提交链接，防止低质量内容污染索引。

## 应用场景

技术团队内部知识沉淀：团队可将成员分享的技术文章统一收录至 TechReads，按项目或技术栈打标，形成团队知识索引，避免重复讨论与信息遗忘。

个人技术阅读聚合：开发者可将分散订阅的多个技术博客、官方发行说明、运维案例站点通过 TechReads 集中管理，每天定时同步最新内容，减少手动访问多个站点的开销。

技术社区运营与内容推荐：技术社区运营人员可利用 TechReads 的外链审核与标签功能筛选优质内容，生成每周推荐列表或专题合集，用于社区 Newsletter 或社交媒体分发。

离线技术文档备份规划：通过 API 批量导出链接元数据，结合外部下载工具可实现技术文章离线存档，适用于内网隔离环境或合规审计场景。

## 快速开始

以下步骤适用于 Linux / macOS 环境，Windows 用户建议通过 WSL2 或 Git Bash 执行。

```bash
# 克隆代码仓库
git clone https://github.com/techreads/techreads-aggregator.git
cd techreads-aggregator

# 安装依赖（使用 pip 虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 复制示例配置并修改数据库连接与采集源列表
cp .env.example .env
vim .env

# 初始化数据库表结构
python manage.py migrate

# 启动开发服务器
python manage.py runserver --host 0.0.0.0 --port 8080
```

访问 http://localhost:8080 即可进入首页。首次运行系统会提示创建管理员账户，按引导完成即可进入后台管理界面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 及以上 | 核心运行时，建议使用 3.11 或 3.12 以获得性能优化 |
| PostgreSQL | 14.x 及以上 | 主数据库，用于存储链接元数据、用户信息与标签关系 |
| Redis | 7.x 及以上 | 缓存与任务队列后端，用于异步采集任务与健康检查调度 |
| Node.js | 18.x 及以上 | 仅用于前端资源构建，生产环境可选用预构建静态文件 |
| Nginx | 1.24 及以上 | 生产环境反向代理与静态资源服务，可选但推荐 |
| Celery | 5.3.x | 异步任务框架，配合 Redis 或 RabbitMQ 执行定时采集 |
| Docker Compose | 2.20 及以上 | 可选，用于一键启动开发环境所有依赖服务 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | /docs/user-guide/quick-start.md | 如何注册、添加订阅源、收藏文章与生成 RSS 订阅 |
| 管理员手册 | /docs/admin/source-management.md | 如何配置采集源、管理标签体系与审核用户提交链接 |
| 开发者文档 | /docs/developer/api-reference.md | API 鉴权方式、请求格式、分页参数与错误码定义 |
| 部署运维 | /docs/ops/deployment-production.md | 生产环境部署流程、日志配置、备份策略与监控指标 |

## 资源列表

- https://www.read.puhvjy.cn/Article/7049.shtml
- https://www.read.cmcvrr.cn/Article/60585.shtml
- https://www.read.nzfnve.cn/Article/775717.shtml
- https://www.read.nzfnve.cn/Article/22167.shtml
- https://www.read.hcbezg.cn/Article/3037.shtml
- https://www.read.cmcvrr.cn/Article/57287.shtml
- https://www.read.cvsifc.cn/Article/1056031.shtml
- https://www.read.cmcvrr.cn/Article/48661.shtml
- https://www.read.nwbbyt.cn/Article/2641464.shtml
- https://www.read.puhvjy.cn/Article/2532.shtml
- https://www.read.puhvjy.cn/Article/18458.shtml
- https://www.read.jnjpgf.cn/Article/5309641.shtml
- https://www.read.cmcvrr.cn/Article/913832.shtml
- https://www.read.nzfnve.cn/Article/7597.shtml
- https://www.read.hcbezg.cn/Article/90141.shtml
- https://www.read.jnjpgf.cn/Article/143367.shtml
- https://www.read.fuvxie.cn/Article/5815115.shtml
- https://www.read.puhvjy.cn/Article/8344056.shtml
- https://www.read.cvsifc.cn/Article/45563.shtml
- https://www.read.cvsifc.cn/Article/2673710.shtml
- https://www.read.cmcvrr.cn/Article/1962818.shtml
- https://www.read.nzfnve.cn/Article/7624.shtml
- https://www.read.fuvxie.cn/Article/0181.shtml
- https://www.read.fuvxie.cn/Article/7324818.shtml
- https://www.read.nwbbyt.cn/Article/5233100.shtml
- https://www.read.fuvxie.cn/Article/990984.shtml
- https://www.read.jnjpgf.cn/Article/524817.shtml
- https://www.read.cmcvrr.cn/Article/8721565.shtml
- https://www.read.jnjpgf.cn/Article/0599.shtml
- https://www.read.hcbezg.cn/Article/0645670.shtml
- https://www.read.jnjpgf.cn/Article/9570510.shtml
- https://www.read.puhvjy.cn/Article/16948.shtml
- https://www.read.puhvjy.cn/Article/363443.shtml
- https://www.read.nzfnve.cn/Article/62443.shtml
- https://www.read.hcbezg.cn/Article/628633.shtml
- https://www.read.hcbezg.cn/Article/5758013.shtml
- https://www.read.hcbezg.cn/Article/118578.shtml
- https://www.read.jnjpgf.cn/Article/1841.shtml
- https://www.read.nzfnve.cn/Article/934810.shtml
- https://www.read.fuvxie.cn/Article/415439.shtml
- https://www.read.hcbezg.cn/Article/41986.shtml
- https://www.read.cvsifc.cn/Article/79410.shtml
- https://www.read.fuvxie.cn/Article/0028517.shtml
- https://www.read.nwbbyt.cn/Article/27791.shtml
- https://www.read.cmcvrr.cn/Article/9585761.shtml
- https://www.read.nzfnve.cn/Article/277870.shtml
- https://www.read.fuvxie.cn/Article/72858.shtml
- https://www.read.jnjpgf.cn/Article/15491.shtml
- https://www.read.nwbbyt.cn/Article/190568.shtml
- https://www.read.cmcvrr.cn/Article/3192.shtml
- https://www.read.jnjpgf.cn/Article/911848.shtml
- https://www.read.cmcvrr.cn/Article/8315045.shtml
- https://www.read.cmcvrr.cn/Article/45381.shtml
- https://www.read.cvsifc.cn/Article/3227867.shtml
- https://www.read.fuvxie.cn/Article/1710132.shtml
- https://www.read.cvsifc.cn/Article/93989.shtml
- https://www.read.cmcvrr.cn/Article/4044076.shtml
- https://www.read.fuvxie.cn/Article/95206.shtml
- https://www.read.cvsifc.cn/Article/075754.shtml
- https://www.read.fuvxie.cn/Article/9011203.shtml
- https://www.read.jnjpgf.cn/Article/17074.shtml
- https://www.read.puhvjy.cn/Article/6881746.shtml
- https://www.read.fuvxie.cn/Article/638325.shtml
- https://www.read.nwbbyt.cn/Article/3522302.shtml
- https://www.read.nzfnve.cn/Article/01315.shtml
- https://www.read.nzfnve.cn/Article/915777.shtml
- https://www.read.fuvxie.cn/Article/5593.shtml
- https://www.read.nwbbyt.cn/Article/1570894.shtml
- https://www.read.jnjpgf.cn/Article/511543.shtml
- https://www.read.cmcvrr.cn/Article/429025.shtml
- https://www.read.puhvjy.cn/Article/2259345.shtml
- https://www.read.cvsifc.cn/Article/498319.shtml
- https://www.read.puhvjy.cn/Article/1652371.shtml
- https://www.read.cvsifc.cn/Article/2106305.shtml
- https://www.read.jnjpgf.cn/Article/6477786.shtml
- https://www.read.nzfnve.cn/Article/0921013.shtml
- https://www.read.hcbezg.cn/Article/5246.shtml
- https://www.read.cvsifc.cn/Article/877127.shtml
- https://www.read.nzfnve.cn/Article/38511.shtml
- https://www.read.cmcvrr.cn/Article/1220605.shtml
- https://www.read.hcbezg.cn/Article/1653.shtml
- https://www.read.cmcvrr.cn/Article/8702905.shtml
- https://www.read.cvsifc.cn/Article/711041.shtml
- https://www.read.nwbbyt.cn/Article/967116.shtml
- https://www.read.nwbbyt.cn/Article/3738972.shtml
- https://www.read.nzfnve.cn/Article/6584.shtml
- https://www.read.hcbezg.cn/Article/7495804.shtml
- https://www.read.cmcvrr.cn/Article/8950997.shtml
- https://www.read.cmcvrr.cn/Article/69476.shtml
- https://www.read.nwbbyt.cn/Article/58714.shtml
- https://www.read.hcbezg.cn/Article/00553.shtml
- https://www.read.cvsifc.cn/Article/1030623.shtml
- https://www.read.jnjpgf.cn/Article/5654.shtml
- https://www.read.nzfnve.cn/Article/5370.shtml
- https://www.read.fuvxie.cn/Article/2853.shtml
- https://www.read.cmcvrr.cn/Article/18911.shtml
- https://www.read.hcbezg.cn/Article/469991.shtml
- https://www.read.puhvjy.cn/Article/2629111.shtml
- https://www.read.hcbezg.cn/Article/7093.shtml
- https://www.read.fuvxie.cn/Article/7139081.shtml
- https://www.read.hcbezg.cn/Article/8743.shtml
- https://www.read.cvsifc.cn/Article/9857987.shtml
- https://www.read.nwbbyt.cn/Article/868791.shtml
- https://www.read.puhvjy.cn/Article/5462772.shtml
- https://www.read.fuvxie.cn/Article/7083.shtml
- https://www.read.cvsifc.cn/Article/6108.shtml
- https://www.read.nwbbyt.cn/Article/3374.shtml
- https://www.read.nzfnve.cn/Article/2086.shtml
- https://www.read.fuvxie.cn/Article/0883.shtml
- https://www.read.fuvxie.cn/Article/33742.shtml
- https://www.read.jnjpgf.cn/Article/49415.shtml
- https://www.read.jnjpgf.cn/Article/0013.shtml
- https://www.read.hcbezg.cn/Article/27789.shtml
- https://www.read.nwbbyt.cn/Article/281081.shtml
- https://www.read.fuvxie.cn/Article/508634.shtml
- https://www.read.hcbezg.cn/Article/8690.shtml
- https://www.read.cvsifc.cn/Article/2039.shtml
- https://www.read.nzfnve.cn/Article/4898190.shtml
- https://www.read.nzfnve.cn/Article/0061894.shtml
- https://www.read.nwbbyt.cn/Article/1518.shtml
- https://www.read.nwbbyt.cn/Article/467331.shtml
- https://www.read.jnjpgf.cn/Article/26616.shtml
- https://www.read.nzfnve.cn/Article/276976.shtml
- https://www.read.nwbbyt.cn/Article/1682.shtml
- https://www.read.puhvjy.cn/Article/2651.shtml
- https://www.read.hcbezg.cn/Article/6154.shtml
- https://www.read.fuvxie.cn/Article/1841289.shtml
- https://www.read.nzfnve.cn/Article/7639411.shtml
- https://www.read.jnjpgf.cn/Article/51173.shtml
- https://www.read.hcbezg.cn/Article/592908.shtml
- https://www.read.cvsifc.cn/Article/21757.shtml
- https://www.read.hcbezg.cn/Article/9256.shtml
- https://www.read.puhvjy.cn/Article/38019.shtml
- https://www.read.cmcvrr.cn/Article/53666.shtml
- https://www.read.nwbbyt.cn/Article/86360.shtml
- https://www.read.cvsifc.cn/Article/336257.shtml
- https://www.read.jnjpgf.cn/Article/2339661.shtml
- https://www.read.puhvjy.cn/Article/1365986.shtml
- https://www.read.cmcvrr.cn/Article/8566.shtml
- https://www.read.nwbbyt.cn/Article/8657478.shtml
- https://www.read.hcbezg.cn/Article/897536.shtml
- https://www.read.nzfnve.cn/Article/84500.shtml
- https://www.read.nzfnve.cn/Article/2763530.shtml
- https://www.read.nzfnve.cn/Article/7704.shtml
- https://www.read.hcbezg.cn/Article/716684.shtml
- https://www.read.cmcvrr.cn/Article/1026.shtml
- https://www.read.jnjpgf.cn/Article/9040162.shtml
- https://www.read.cvsifc.cn/Article/3543.shtml
- https://www.read.jnjpgf.cn/Article/9867122.shtml
- https://www.read.nwbbyt.cn/Article/2452.shtml
- https://www.read.hcbezg.cn/Article/1159.shtml
- https://www.read.fuvxie.cn/Article/736228.shtml
- https://www.read.cvsifc.cn/Article/9508980.shtml
- https://www.read.jnjpgf.cn/Article/76687.shtml
- https://www.read.nzfnve.cn/Article/8341852.shtml
- https://www.read.cmcvrr.cn/Article/1984.shtml
- https://www.read.hcbezg.cn/Article/6204436.shtml
- https://www.read.jnjpgf.cn/Article/3236.shtml
- https://www.read.nzfnve.cn/Article/5863.shtml
- https://www.read.cvsifc.cn/Article/5212.shtml
- https://www.read.hcbezg.cn/Article/03329.shtml
- https://www.read.jnjpgf.cn/Article/0988.shtml
- https://www.read.fuvxie.cn/Article/0284.shtml
- https://www.read.nwbbyt.cn/Article/3888.shtml
- https://www.read.cmcvrr.cn/Article/566077.shtml
- https://www.read.jnjpgf.cn/Article/4838.shtml
- https://www.read.cvsifc.cn/Article/6903739.shtml
- https://www.read.puhvjy.cn/Article/00471.shtml
- https://www.read.hcbezg.cn/Article/1181972.shtml
- https://www.read.nwbbyt.cn/Article/7601910.shtml
- https://www.read.nwbbyt.cn/Article/8692393.shtml
- https://www.read.nzfnve.cn/Article/2227162.shtml
- https://www.read.jnjpgf.cn/Article/1508.shtml
- https://www.read.puhvjy.cn/Article/4067.shtml
- https://www.read.nwbbyt.cn/Article/423581.shtml
- https://www.read.cmcvrr.cn/Article/8822580.shtml
- https://www.read.puhvjy.cn/Article/98525.shtml
- https://www.read.cmcvrr.cn/Article/629989.shtml
- https://www.read.hcbezg.cn/Article/8725078.shtml
- https://www.read.nzfnve.cn/Article/106271.shtml
- https://www.read.jnjpgf.cn/Article/64107.shtml
- https://www.read.puhvjy.cn/Article/1229.shtml
- https://www.read.hcbezg.cn/Article/019634.shtml
- https://www.read.cmcvrr.cn/Article/3542.shtml
- https://www.read.nzfnve.cn/Article/9310305.shtml
- https://www.read.hcbezg.cn/Article/3223.shtml
- https://www.read.cmcvrr.cn/Article/3632748.shtml
- https://www.read.cvsifc.cn/Article/9889.shtml
- https://www.read.cvsifc.cn/Article/90498.shtml
- https://www.read.nzfnve.cn/Article/7288.shtml
- https://www.read.fuvxie.cn/Article/990520.shtml
- https://www.read.puhvjy.cn/Article/666625.shtml
- https://www.read.jnjpgf.cn/Article/4640492.shtml
- https://www.read.puhvjy.cn/Article/50218.shtml
- https://www.read.jnjpgf.cn/Article/9513.shtml
- https://www.read.jnjpgf.cn/Article/47786.shtml
- https://www.read.cvsifc.cn/Article/2085784.shtml
- https://www.read.nzfnve.cn/Article/1775.shtml
- https://www.read.fuvxie.cn/Article/008631.shtml
- https://www.read.fuvxie.cn/Article/3228350.shtml
- https://www.read.cmcvrr.cn/Article/86242.shtml
- https://www.read.nzfnve.cn/Article/6690515.shtml
- https://www.read.puhvjy.cn/Article/6147.shtml
- https://www.read.cmcvrr.cn/Article/69335.shtml
- https://www.read.puhvjy.cn/Article/586019.shtml
- https://www.read.nwbbyt.cn/Article/3314.shtml
- https://www.read.nzfnve.cn/Article/4059.shtml
- https://www.read.cvsifc.cn/Article/8472.shtml
- https://www.read.nzfnve.cn/Article/57858.shtml
- https://www.read.nwbbyt.cn/Article/52400.shtml
- https://www.read.nzfnve.cn/Article/2534.shtml
- https://www.read.nwbbyt.cn/Article/29646.shtml
- https://www.read.fuvxie.cn/Article/15789.shtml
- https://www.read.cmcvrr.cn/Article/585307.shtml
- https://www.read.jnjpgf.cn/Article/5483168.shtml
- https://www.read.nwbbyt.cn/Article/89579.shtml
- https://www.read.puhvjy.cn/Article/10439.shtml
- https://www.read.jnjpgf.cn/Article/6180.shtml
- https://www.read.hcbezg.cn/Article/3686.shtml
- https://www.read.fuvxie.cn/Article/732767.shtml
- https://www.read.fuvxie.cn/Article/8495146.shtml
- https://www.read.puhvjy.cn/Article/69013.shtml
- https://www.read.cvsifc.cn/Article/6911.shtml
- https://www.read.hcbezg.cn/Article/117726.shtml
- https://www.read.cvsifc.cn/Article/639855.shtml
- https://www.read.nwbbyt.cn/Article/20766.shtml
- https://www.read.nwbbyt.cn/Article/7335948.shtml
- https://www.read.nzfnve.cn/Article/5012.shtml
- https://www.read.nwbbyt.cn/Article/0669.shtml
- https://www.read.fuvxie.cn/Article/1291.shtml
- https://www.read.nzfnve.cn/Article/639256.shtml
- https://www.read.cvsifc.cn/Article/463340.shtml
- https://www.read.nzfnve.cn/Article/331219.shtml
- https://www.read.nwbbyt.cn/Article/3019647.shtml
- https://www.read.fuvxie.cn/Article/78045.shtml
- https://www.read.cvsifc.cn/Article/8562390.shtml
- https://www.read.cvsifc.cn/Article/5918.shtml
- https://www.read.cmcvrr.cn/Article/62637.shtml
- https://www.read.hcbezg.cn/Article/1907.shtml
- https://www.read.cvsifc.cn/Article/45225.shtml
- https://www.read.jnjpgf.cn/Article/0695281.shtml
- https://www.read.cmcvrr.cn/Article/169710.shtml
- https://www.read.fuvxie.cn/Article/5215673.shtml
- https://www.read.cmcvrr.cn/Article/3280448.shtml
- https://www.read.hcbezg.cn/Article/0755444.shtml
- https://www.read.puhvjy.cn/Article/051092.shtml
- https://www.read.cvsifc.cn/Article/5712573.shtml
- https://www.read.hcbezg.cn/Article/6716098.shtml
- https://www.read.nwbbyt.cn/Article/24827.shtml
- https://www.read.jnjpgf.cn/Article/10579.shtml

## 项目结构

```
techreads-aggregator/
├── src/                                # 核心源码目录
│   ├── aggregator/                     # 采集引擎模块
│   │   ├── spiders/                    # 各个源站解析器，每个源一个独立文件
│   │   ├── pipeline.py                 # 数据清洗与去重流水线
│   │   └── scheduler.py                # 基于 Celery 的定时任务调度
│   ├── api/                            # RESTful API 实现
│   │   ├── v1/                         # API 版本 v1 路由与序列化器
│   │   └── middleware/                 # 认证、限流、日志中间件
│   ├── core/                           # 通用业务逻辑
│   │   ├── models/                     # SQLAlchemy 数据模型（Link, Tag, User 等）
│   │   ├── services/                   # 标签推荐、链接检查等业务服务
│   │   └── utils/                      # 工具函数（日期处理、URL 规范化）
│   └── web/                            # 前端 Web 界面
│       ├── templates/                  # Jinja2 模板文件
│       └── static/                     # 编译后的 CSS 与 JavaScript 资源
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 单模块测试用例
│   └── integration/                    # API 与数据库交互测试
├── scripts/                            # 运维与辅助脚本
│   ├── init_db.sql                     # 数据库初始化 SQL
│   ├── seed_sample_links.py            # 填充示例数据
│   └── health_check.py                 # 手动触发链接健康检查
├── config/                             # 多环境配置文件
│   ├── development.toml                # 开发环境配置
│   ├── production.toml                 # 生产环境配置
│   └── logging.conf                    # 日志格式与输出级别配置
├── docs/                               # 完整项目文档（用户、管理、开发、运维）
├── docker-compose.yml                  # 本地开发依赖服务编排
├── Dockerfile                          # 生产环境镜像构建文件
├── requirements.txt                    # Python 生产依赖列表
├── requirements-dev.txt                # 开发与测试额外依赖
├── Makefile                            # 常用命令封装（migrate, test, run）
└── README.md                           # 项目总览（本文件）
```

## 贡献指南

欢迎各类贡献，包括但不限于新增采集源解析器、优化标签推荐算法、完善文档与修复缺陷。请遵循以下流程：

1. 在 GitHub Issues 中查找或新建一个与变更相关的问题，简要描述你计划修改的内容，避免重复工作。对于新增采集源，请在问题中附上示例页面链接与预期解析字段。

2. Fork 本项目到个人账户，基于 main 分支新建一个功能分支，分支命名采用 feat/功能描述 或 fix/问题描述 的格式，例如 feat/add-elasticsearch-source。

3. 完成代码变更后，请确保通过所有现有单元测试，并为新增功能补充对应的测试用例。运行 make test 可执行完整测试套件。若涉及配置变更，请同步更新 .env.example 与对应环境配置文件。

4. 提交 Pull Request 到主仓库的 main 分支，PR 描述中请关联对应 Issue 编号，并简要列出变更点与测试覆盖情况。PR 标题遵循 Conventional Commits 规范。

5. 等待维护者 Code Review。如有修改意见，请在 PR 中追加提交，不要关闭 PR 重开。合并前需要至少一位维护者批准且所有 CI 检查通过。

## 常见问题

Q: 采集任务执行后，部分链接无法获取标题或摘要，数据不完整如何处理？

A: 系统会在采集流水线中记录解析失败的原因，并在日志中输出 WARNING 级别信息。您可以在管理后台的「采集日志」中查看具体失败条目。常见原因为目标站点反爬策略或页面结构变更。此时可手动编辑该条目的标题与摘要，或调整对应 spider 的 CSS 选择器配置。若为站点永久变更，建议提交 Issue 或 PR 更新解析器。

Q: 系统运行一段时间后，数据库中的链接数量增长迅速，如何优化检索性能？

A: 建议对 links 表的 published_at、source_domain 和 tag_ids 字段建立复合索引。项目默认提供了 migration 文件用于创建推荐索引，执行 python manage.py optimize_indexes 即可应用。若数据量超过 50 万条，可进一步配置 PostgreSQL 的分区表策略，按月份分区存储历史数据。具体操作参见运维文档中的分区方案章节。

Q: 在生产环境中如何将采集频率调整为每两小时一次而非默认的每小时一次？

A: 采集频率由 Celery Beat 调度器控制，配置文件位于 config/production.toml 中的 [celery.schedule] 段。将 fetch_interval_minutes 的值从 60 改为 120 即可。修改后需要重启 Celery Beat 进程使配置生效。若使用 Docker Compose 部署，执行 docker-compose restart celery-beat 即可。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:20

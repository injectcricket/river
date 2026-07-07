# LinkPilot 技术资源导航

LinkPilot 是一个面向开发者、技术研究人员与内容聚合者的轻量级外链资源管理与导航系统。该项目旨在解决技术信息分散、优质外链难以追踪、阅读进度不易同步等现实痛点，通过对批量外链的结构化收录与分类展示，帮助用户在信息过载的环境中快速定位高价值阅读材料。LinkPilot 定位于小型团队、独立开发者以及技术内容策展人，可作为个人知识库的外链中台，也可嵌入现有文档站点作为资源挂件运行。

## 功能概览

批量外链导入与自动解析 系统支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入外链，自动提取页面标题、元描述及预估阅读时长，减少人工录入成本。

自定义标签与多级分类 用户可为每条链接添加自定义标签，并基于标签组合生成动态分类视图。分类层级支持至多三级，便于构建技术栈、领域、难度等不同维度的筛选体系。

阅读状态追踪与进度同步 每条外链均可标记为未读、在读、已读或搁置，系统记录每次状态变更的时间戳，并支持多设备间通过 JSON 导出导入实现进度同步。

全文检索与高级过滤 基于倒排索引的标题与标签检索，支持按域名、标签组合、阅读状态、收录时间范围进行多条件过滤，结果可排序并导出为 Markdown 表格。

外链快照与离线存档 对于关键链接，系统可调用后台任务抓取页面静态快照并存储为 HTML 文件，防止原始内容下线后丢失参考依据。

访问统计与热点分析 自动统计每条外链的点击次数、最后访问时间及来源标签分布，提供简单的热点排序视图，帮助用户识别当前最受关注的资源。

数据导入导出与备份恢复 所有外链数据、标签体系与阅读进度均可导出为单一 JSON 文件，支持定时自动备份与手动恢复，方便迁移至其他部署实例。

## 应用场景

技术团队内部知识库外链管理 研发团队可将日常遇到的优秀技术博客、官方文档、RFC 草案等统一收录至 LinkPilot，并按项目或技术方向打标签，新成员入职时可快速浏览团队推荐的阅读清单。

技术自媒体内容策展 技术博主或通讯作者可使用 LinkPilot 整理每周优质外链，生成阅读列表并导出为 Markdown 格式发布在 Newsletter 或社交媒体上，提升内容产出效率。

个人技术阅读工作流管理 开发者可将每日浏览中发现的有价值文章存入 LinkPilot，利用阅读状态追踪和离线快照功能，在通勤或离线环境下完成阅读，避免链接在浏览器书签中积灰。

开源项目文档站外链挂件 开源项目维护者可将 LinkPilot 嵌入项目文档的「相关资源」页面，统一展示社区推荐的教程、视频、替代方案等外链，并利用标签区分官方与社区内容。

技术培训课程辅助材料整理 培训讲师可将课程涉及的延伸阅读材料统一收录并按周次或模块分类，学员通过共享链接访问只读视图，减少资料分发时的重复沟通。

## 快速开始

以下命令可在本地环境完成 LinkPilot 的克隆、安装与启动。系统默认使用 SQLite 作为存储后端，无需额外配置数据库服务。

```bash
git clone https://github.com/linkpilot-dev/linkpilot.git
cd linkpilot
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

启动后访问 http://127.0.0.1:8000 即可进入主界面。默认管理员账号为 admin，密码在首次启动时由系统生成并打印在终端日志中，请留意输出信息。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 及以上 | 核心运行环境，低于 3.10 将导致类型注解解析异常 |
| Django | 4.2 LTS | Web 框架，用于提供 ORM、管理后台及模板引擎 |
| SQLite | 3.35 及以上 | 默认数据库，支持 JSON 字段存储标签与元数据 |
| Celery | 5.3 及以上 | 异步任务队列，用于快照抓取与统计更新（可选） |
| Redis | 6.2 及以上 | Celery 消息代理，若启用异步功能则必须安装 |
| BeautifulSoup4 | 4.12 及以上 | HTML 解析库，用于外链元信息提取与快照清洗 |
| requests | 2.31 及以上 | HTTP 客户端，用于抓取外链页面内容 |
| python-crontab | 3.0 及以上 | 定时任务调度，用于自动备份与统计刷新（可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user/quick-start.md | 如何快速上手使用 LinkPilot 进行外链收录与阅读追踪 |
| 用户手册 | /docs/user/advanced-filter.md | 如何组合标签、状态和时间条件进行复杂筛选与导出 |
| 开发者指南 | /docs/dev/api-endpoints.md | 后端 RESTful API 的路由列表、请求格式与鉴权方式 |
| 开发者指南 | /docs/dev/deployment-prod.md | 生产环境部署的 Nginx + Gunicorn + PostgreSQL 配置示例 |
| 运维手册 | /docs/ops/backup-restore.md | 数据备份策略、恢复流程及迁移至新实例的操作步骤 |
| 运维手册 | /docs/ops/performance-tuning.md | 缓存策略、数据库索引建议及 Celery Worker 数量调优 |

## 资源列表

- https://www.read.cmcvrr.cn/Article/6715621.shtml
- https://www.read.puhvjy.cn/Article/4828.shtml
- https://www.read.cmcvrr.cn/Article/6554425.shtml
- https://www.read.hcbezg.cn/Article/272975.shtml
- https://www.read.puhvjy.cn/Article/9551652.shtml
- https://www.read.cmcvrr.cn/Article/6295300.shtml
- https://www.read.nwbbyt.cn/Article/1687033.shtml
- https://www.read.nzfnve.cn/Article/917269.shtml
- https://www.read.cmcvrr.cn/Article/35620.shtml
- https://www.read.nzfnve.cn/Article/296326.shtml
- https://www.read.cmcvrr.cn/Article/9546651.shtml
- https://www.read.jnjpgf.cn/Article/73838.shtml
- https://www.read.cvsifc.cn/Article/7409.shtml
- https://www.read.nzfnve.cn/Article/46883.shtml
- https://www.read.hcbezg.cn/Article/30838.shtml
- https://www.read.cmcvrr.cn/Article/38842.shtml
- https://www.read.cvsifc.cn/Article/4287.shtml
- https://www.read.cmcvrr.cn/Article/5572233.shtml
- https://www.read.puhvjy.cn/Article/6385466.shtml
- https://www.read.nwbbyt.cn/Article/8617054.shtml
- https://www.read.fuvxie.cn/Article/47111.shtml
- https://www.read.jnjpgf.cn/Article/5788774.shtml
- https://www.read.cvsifc.cn/Article/642004.shtml
- https://www.read.cvsifc.cn/Article/5376.shtml
- https://www.read.cvsifc.cn/Article/8471.shtml
- https://www.read.nzfnve.cn/Article/892622.shtml
- https://www.read.hcbezg.cn/Article/807199.shtml
- https://www.read.nzfnve.cn/Article/74277.shtml
- https://www.read.nwbbyt.cn/Article/3083.shtml
- https://www.read.cmcvrr.cn/Article/187292.shtml
- https://www.read.jnjpgf.cn/Article/3701.shtml
- https://www.read.puhvjy.cn/Article/1462.shtml
- https://www.read.puhvjy.cn/Article/9478.shtml
- https://www.read.puhvjy.cn/Article/03602.shtml
- https://www.read.nzfnve.cn/Article/873961.shtml
- https://www.read.hcbezg.cn/Article/5631.shtml
- https://www.read.hcbezg.cn/Article/2932073.shtml
- https://www.read.cvsifc.cn/Article/0693.shtml
- https://www.read.hcbezg.cn/Article/0229.shtml
- https://www.read.hcbezg.cn/Article/4692598.shtml
- https://www.read.fuvxie.cn/Article/1012454.shtml
- https://www.read.cvsifc.cn/Article/3140.shtml
- https://www.read.fuvxie.cn/Article/51706.shtml
- https://www.read.jnjpgf.cn/Article/99940.shtml
- https://www.read.jnjpgf.cn/Article/63869.shtml
- https://www.read.hcbezg.cn/Article/40945.shtml
- https://www.read.nwbbyt.cn/Article/57445.shtml
- https://www.read.jnjpgf.cn/Article/210374.shtml
- https://www.read.fuvxie.cn/Article/7575293.shtml
- https://www.read.nzfnve.cn/Article/51683.shtml
- https://www.read.fuvxie.cn/Article/903732.shtml
- https://www.read.jnjpgf.cn/Article/8264885.shtml
- https://www.read.jnjpgf.cn/Article/7536.shtml
- https://www.read.puhvjy.cn/Article/1898068.shtml
- https://www.read.nwbbyt.cn/Article/1581101.shtml
- https://www.read.jnjpgf.cn/Article/211253.shtml
- https://www.read.nwbbyt.cn/Article/4078.shtml
- https://www.read.puhvjy.cn/Article/3062722.shtml
- https://www.read.hcbezg.cn/Article/897175.shtml
- https://www.read.cvsifc.cn/Article/98265.shtml
- https://www.read.nzfnve.cn/Article/9126.shtml
- https://www.read.cvsifc.cn/Article/7960553.shtml
- https://www.read.cmcvrr.cn/Article/8055.shtml
- https://www.read.cvsifc.cn/Article/6038623.shtml
- https://www.read.cmcvrr.cn/Article/0215.shtml
- https://www.read.fuvxie.cn/Article/3106036.shtml
- https://www.read.nzfnve.cn/Article/594448.shtml
- https://www.read.jnjpgf.cn/Article/8595.shtml
- https://www.read.nzfnve.cn/Article/1789.shtml
- https://www.read.puhvjy.cn/Article/17267.shtml
- https://www.read.nwbbyt.cn/Article/0468.shtml
- https://www.read.cvsifc.cn/Article/8121.shtml
- https://www.read.jnjpgf.cn/Article/0556.shtml
- https://www.read.puhvjy.cn/Article/97493.shtml
- https://www.read.hcbezg.cn/Article/9953547.shtml
- https://www.read.cvsifc.cn/Article/1252.shtml
- https://www.read.jnjpgf.cn/Article/04578.shtml
- https://www.read.jnjpgf.cn/Article/476336.shtml
- https://www.read.fuvxie.cn/Article/1151835.shtml
- https://www.read.nzfnve.cn/Article/0072.shtml
- https://www.read.nzfnve.cn/Article/01013.shtml
- https://www.read.fuvxie.cn/Article/7966.shtml
- https://www.read.nzfnve.cn/Article/2611604.shtml
- https://www.read.fuvxie.cn/Article/3402421.shtml
- https://www.read.jnjpgf.cn/Article/26073.shtml
- https://www.read.nzfnve.cn/Article/26642.shtml
- https://www.read.puhvjy.cn/Article/994842.shtml
- https://www.read.puhvjy.cn/Article/2919.shtml
- https://www.read.puhvjy.cn/Article/4341.shtml
- https://www.read.hcbezg.cn/Article/510647.shtml
- https://www.read.puhvjy.cn/Article/885305.shtml
- https://www.read.cvsifc.cn/Article/12984.shtml
- https://www.read.jnjpgf.cn/Article/91898.shtml
- https://www.read.nzfnve.cn/Article/883874.shtml
- https://www.read.nzfnve.cn/Article/247374.shtml
- https://www.read.fuvxie.cn/Article/75026.shtml
- https://www.read.cvsifc.cn/Article/0097629.shtml
- https://www.read.hcbezg.cn/Article/553366.shtml
- https://www.read.puhvjy.cn/Article/7247904.shtml
- https://www.read.hcbezg.cn/Article/54910.shtml
- https://www.read.nzfnve.cn/Article/9319.shtml
- https://www.read.fuvxie.cn/Article/6935.shtml
- https://www.read.cvsifc.cn/Article/6457.shtml
- https://www.read.nwbbyt.cn/Article/38707.shtml
- https://www.read.fuvxie.cn/Article/44393.shtml
- https://www.read.nwbbyt.cn/Article/1532955.shtml
- https://www.read.nzfnve.cn/Article/8883032.shtml
- https://www.read.jnjpgf.cn/Article/6379501.shtml
- https://www.read.cmcvrr.cn/Article/94263.shtml
- https://www.read.jnjpgf.cn/Article/6664.shtml
- https://www.read.nwbbyt.cn/Article/0617.shtml
- https://www.read.nwbbyt.cn/Article/77175.shtml
- https://www.read.cvsifc.cn/Article/67045.shtml
- https://www.read.puhvjy.cn/Article/438681.shtml
- https://www.read.nwbbyt.cn/Article/72782.shtml
- https://www.read.nzfnve.cn/Article/3914563.shtml
- https://www.read.cvsifc.cn/Article/360787.shtml
- https://www.read.hcbezg.cn/Article/8627.shtml
- https://www.read.fuvxie.cn/Article/6479.shtml
- https://www.read.cvsifc.cn/Article/658305.shtml
- https://www.read.nwbbyt.cn/Article/574786.shtml
- https://www.read.fuvxie.cn/Article/8566566.shtml
- https://www.read.nzfnve.cn/Article/1252.shtml
- https://www.read.fuvxie.cn/Article/45341.shtml
- https://www.read.nwbbyt.cn/Article/4833877.shtml
- https://www.read.nwbbyt.cn/Article/8344190.shtml
- https://www.read.nzfnve.cn/Article/010189.shtml
- https://www.read.jnjpgf.cn/Article/398273.shtml
- https://www.read.puhvjy.cn/Article/3747290.shtml
- https://www.read.cvsifc.cn/Article/8336.shtml
- https://www.read.cmcvrr.cn/Article/6862.shtml
- https://www.read.nzfnve.cn/Article/205974.shtml
- https://www.read.jnjpgf.cn/Article/41105.shtml
- https://www.read.cvsifc.cn/Article/4722902.shtml
- https://www.read.nwbbyt.cn/Article/9592.shtml
- https://www.read.jnjpgf.cn/Article/0938770.shtml
- https://www.read.nzfnve.cn/Article/4500851.shtml
- https://www.read.cvsifc.cn/Article/542281.shtml
- https://www.read.fuvxie.cn/Article/0368.shtml
- https://www.read.fuvxie.cn/Article/1987337.shtml
- https://www.read.jnjpgf.cn/Article/073011.shtml
- https://www.read.nwbbyt.cn/Article/780182.shtml
- https://www.read.fuvxie.cn/Article/6912.shtml
- https://www.read.nwbbyt.cn/Article/61075.shtml
- https://www.read.cmcvrr.cn/Article/675095.shtml
- https://www.read.hcbezg.cn/Article/798185.shtml
- https://www.read.puhvjy.cn/Article/1508.shtml
- https://www.read.hcbezg.cn/Article/91620.shtml
- https://www.read.nzfnve.cn/Article/4299015.shtml
- https://www.read.cmcvrr.cn/Article/109817.shtml
- https://www.read.nwbbyt.cn/Article/212794.shtml
- https://www.read.nzfnve.cn/Article/804797.shtml
- https://www.read.nwbbyt.cn/Article/7699817.shtml
- https://www.read.nwbbyt.cn/Article/33590.shtml
- https://www.read.jnjpgf.cn/Article/0212066.shtml
- https://www.read.cvsifc.cn/Article/146932.shtml
- https://www.read.hcbezg.cn/Article/4283.shtml
- https://www.read.jnjpgf.cn/Article/33982.shtml
- https://www.read.nwbbyt.cn/Article/7088.shtml
- https://www.read.cvsifc.cn/Article/02296.shtml
- https://www.read.fuvxie.cn/Article/1308.shtml
- https://www.read.cmcvrr.cn/Article/14957.shtml
- https://www.read.cvsifc.cn/Article/3283.shtml
- https://www.read.nzfnve.cn/Article/2371.shtml
- https://www.read.nzfnve.cn/Article/750866.shtml
- https://www.read.cvsifc.cn/Article/0981.shtml
- https://www.read.hcbezg.cn/Article/258865.shtml
- https://www.read.jnjpgf.cn/Article/556424.shtml
- https://www.read.cvsifc.cn/Article/4690.shtml
- https://www.read.jnjpgf.cn/Article/8159970.shtml
- https://www.read.nzfnve.cn/Article/020629.shtml
- https://www.read.puhvjy.cn/Article/44316.shtml
- https://www.read.nzfnve.cn/Article/4714178.shtml
- https://www.read.hcbezg.cn/Article/629318.shtml
- https://www.read.cmcvrr.cn/Article/1781.shtml
- https://www.read.puhvjy.cn/Article/1114.shtml
- https://www.read.cmcvrr.cn/Article/983309.shtml
- https://www.read.jnjpgf.cn/Article/6696.shtml
- https://www.read.puhvjy.cn/Article/5583.shtml
- https://www.read.nzfnve.cn/Article/106033.shtml
- https://www.read.nzfnve.cn/Article/05791.shtml
- https://www.read.nzfnve.cn/Article/0602645.shtml
- https://www.read.jnjpgf.cn/Article/310039.shtml
- https://www.read.hcbezg.cn/Article/49730.shtml
- https://www.read.cvsifc.cn/Article/1910891.shtml
- https://www.read.nzfnve.cn/Article/074091.shtml
- https://www.read.fuvxie.cn/Article/6404892.shtml
- https://www.read.hcbezg.cn/Article/3277276.shtml
- https://www.read.jnjpgf.cn/Article/0669194.shtml
- https://www.read.fuvxie.cn/Article/9336361.shtml
- https://www.read.cvsifc.cn/Article/81445.shtml
- https://www.read.cmcvrr.cn/Article/8319.shtml
- https://www.read.hcbezg.cn/Article/74490.shtml
- https://www.read.jnjpgf.cn/Article/3160.shtml
- https://www.read.nzfnve.cn/Article/9133198.shtml
- https://www.read.cmcvrr.cn/Article/339814.shtml
- https://www.read.hcbezg.cn/Article/7116732.shtml
- https://www.read.cvsifc.cn/Article/3684.shtml
- https://www.read.hcbezg.cn/Article/2740.shtml
- https://www.read.hcbezg.cn/Article/20928.shtml
- https://www.read.cvsifc.cn/Article/5505973.shtml
- https://www.read.nwbbyt.cn/Article/7872.shtml
- https://www.read.fuvxie.cn/Article/873884.shtml
- https://www.read.hcbezg.cn/Article/9052115.shtml
- https://www.read.nwbbyt.cn/Article/813939.shtml
- https://www.read.cmcvrr.cn/Article/282135.shtml
- https://www.read.jnjpgf.cn/Article/3184.shtml
- https://www.read.cmcvrr.cn/Article/69464.shtml
- https://www.read.cmcvrr.cn/Article/2266.shtml
- https://www.read.cmcvrr.cn/Article/3611.shtml
- https://www.read.hcbezg.cn/Article/287810.shtml
- https://www.read.cmcvrr.cn/Article/8948.shtml
- https://www.read.hcbezg.cn/Article/34149.shtml
- https://www.read.jnjpgf.cn/Article/0569.shtml
- https://www.read.cvsifc.cn/Article/4312417.shtml
- https://www.read.jnjpgf.cn/Article/6579988.shtml
- https://www.read.puhvjy.cn/Article/8226.shtml
- https://www.read.cmcvrr.cn/Article/4881194.shtml
- https://www.read.nwbbyt.cn/Article/8036257.shtml
- https://www.read.jnjpgf.cn/Article/8985.shtml
- https://www.read.hcbezg.cn/Article/48715.shtml
- https://www.read.cvsifc.cn/Article/3019337.shtml
- https://www.read.puhvjy.cn/Article/21642.shtml
- https://www.read.jnjpgf.cn/Article/949644.shtml
- https://www.read.cvsifc.cn/Article/37296.shtml
- https://www.read.nzfnve.cn/Article/12554.shtml
- https://www.read.cmcvrr.cn/Article/19877.shtml
- https://www.read.cmcvrr.cn/Article/10933.shtml
- https://www.read.cvsifc.cn/Article/9144281.shtml
- https://www.read.cmcvrr.cn/Article/3792914.shtml
- https://www.read.fuvxie.cn/Article/277946.shtml
- https://www.read.nwbbyt.cn/Article/5992674.shtml
- https://www.read.jnjpgf.cn/Article/761431.shtml
- https://www.read.nwbbyt.cn/Article/3984026.shtml
- https://www.read.nwbbyt.cn/Article/155240.shtml
- https://www.read.hcbezg.cn/Article/0972.shtml
- https://www.read.cmcvrr.cn/Article/17245.shtml
- https://www.read.cmcvrr.cn/Article/9959471.shtml
- https://www.read.cvsifc.cn/Article/2624.shtml
- https://www.read.nwbbyt.cn/Article/024310.shtml
- https://www.read.jnjpgf.cn/Article/872045.shtml
- https://www.read.nwbbyt.cn/Article/00637.shtml
- https://www.read.fuvxie.cn/Article/02329.shtml
- https://www.read.cmcvrr.cn/Article/4732829.shtml
- https://www.read.cmcvrr.cn/Article/688080.shtml
- https://www.read.nzfnve.cn/Article/756982.shtml
- https://www.read.nwbbyt.cn/Article/55915.shtml
- https://www.read.hcbezg.cn/Article/67824.shtml
- https://www.read.puhvjy.cn/Article/072759.shtml
- https://www.read.cmcvrr.cn/Article/108895.shtml

## 项目结构

```
linkpilot/
├── manage.py                         # Django 项目入口，用于启动开发服务器与执行管理命令
├── requirements.txt                  # Python 依赖清单，锁定所有第三方库版本号
├── config/                           # 项目全局配置目录
│   ├── settings.py                   # 基础配置，包含数据库、中间件、静态文件及 Celery 设置
│   ├── settings_prod.py              # 生产环境覆盖配置，敏感变量从环境变量读取
│   └── urls.py                       # 根路由分发，挂载 admin、api 及前端视图路由
├── apps/                             # 所有自定义应用存放目录
│   ├── core/                         # 核心模型与通用工具
│   │   ├── models.py                 # Link、Tag、Snapshot、ReadHistory 等核心数据模型
│   │   ├── managers.py               # 自定义模型管理器，封装复杂查询逻辑
│   │   └── validators.py             # URL 格式校验、域名黑名单等校验器
│   ├── parser/                       # 外链解析与快照抓取应用
│   │   ├── fetcher.py                # 基于 requests + BeautifulSoup 的页面抓取器
│   │   ├── extractor.py              # 标题、描述、正文预览的智能提取规则
│   │   └── tasks.py                  # Celery 异步任务定义，含抓取、更新、清理
│   ├── search/                       # 检索与过滤应用
│   │   ├── index.py                  # 倒排索引构建与更新逻辑
│   │   ├── filters.py                # 标签、状态、时间等过滤器组合类
│   │   └── serializers.py            # API 返回结果的序列化与分页格式
│   ├── stats/                        # 统计与分析应用
│   │   ├── collector.py              # 点击日志、访问时段的收集与聚合
│   │   ├── hotrank.py                # 热点排序算法实现（基于衰减因子）
│   │   └── reports.py                # 日报/周报的 Markdown 生成器
│   └── api/                          # RESTful API 应用
│       ├── views.py                  # 类视图集，含列表、详情、批量导入、导出端点
│       ├── permissions.py            # 基于角色的访问权限控制
│       └── throttles.py              # 请求频率限制策略
├── static/                           # 前端静态资源（CSS、JS、图标）
├── templates/                        # Django 模板目录
│   ├── base.html                     # 基础骨架模板，含导航栏与全局消息占位
│   ├── dashboard.html                # 仪表盘视图，展示总链接数、待读量、热点 Top10
│   └── link_list.html                # 外链列表页，含筛选器面板与表格渲染
├── docs/                             # 文档目录，与文档导航章节一一对应
│   ├── user/
│   ├── dev/
│   └── ops/
├── scripts/                          # 运维与辅助脚本
│   ├── backup.py                     # 数据备份脚本，输出 JSON 文件到指定目录
│   ├── import_csv.py                 # 从 CSV 文件批量导入外链的脚本示例
│   └── clean_snapshots.py            # 清理过期快照文件的脚本
└── tests/                            # 单元测试与集成测试目录
    ├── test_models.py
    ├── test_parser.py
    └── test_api.py
```

## 贡献指南

1. 查阅 Issue 列表与项目看板，选择未被认领且标注为 good-first-issue 的任务，在对应 Issue 下回复 /assign 表明接手意愿，等待维护者确认。

2. 将项目复刻至个人账户，基于 main 分支创建功能分支，分支命名遵循 feat/功能简述 或 fix/问题简述 的格式，禁止直接在 main 分支上修改。

3. 编写或修改代码时，需同步更新对应的单元测试文件，确保测试覆盖率达到 80% 以上。所有新增的对外 API 或前端组件必须附带简要的使用说明或注释。

4. 提交代码前执行 pre-commit 钩子进行代码格式检查（Black + isort + Flake8），并确保所有测试用例通过。提交信息采用 Conventional Commits 规范，例如 feat(parser): 增加对 PDF 链接的摘要提取支持。

5. 发起 Pull Request 至 main 分支，PR 描述中需引用关联 Issue 编号，并简要说明改动内容、测试结果以及是否涉及数据库迁移或配置变更。至少需要一位维护者审核通过后方可合并。

## 常见问题

问题：系统启动后访问页面提示数据库表不存在，应该如何解决？

解答：这通常是因为未执行数据库迁移命令。请确认在项目根目录下依次执行 python manage.py makemigrations 和 python manage.py migrate。如果迁移后仍然报错，可检查 settings.py 中的 DATABASES 配置，确保数据库路径可写。SQLite 文件默认位于项目根目录的 db.sqlite3，若需重置数据库，可删除该文件后重新执行迁移。

问题：批量导入大量外链时页面响应缓慢或超时，如何处理？

解答：批量导入操作会触发每条链接的元信息抓取，若外链数量超过 50 条，建议使用异步导入模式。在 .env 配置文件中将 ASYNC_IMPORT 设置为 True，并确保 Celery Worker 已启动。此时导入请求会返回任务 ID，用户可通过任务状态轮询获取导入进度，避免 HTTP 请求阻塞。若未启用异步模式，可在导入前将外链列表分批（每批 20 条）依次提交。

问题：快照抓取失败或一直处于 pending 状态，如何排查？

解答：首先检查 Celery Worker 是否正常运行，可通过 python manage.py shell 手动调用抓取任务进行测试。其次，确认目标网站是否允许爬取，查看 robots.txt 或是否存在反爬机制。LinkPilot 在 fetcher.py 中设置了默认的 User-Agent 和请求超时（10 秒），若频繁失败可考虑增加代理配置。最后，检查 Redis 连接状态，Celery 任务队列依赖 Redis 作为消息代理，连接断开会导致任务积压。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:20

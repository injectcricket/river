# LinkSphere

LinkSphere 是一个面向技术研究者和信息聚合场景的轻量级外链资源管理与导航系统。该项目旨在解决海量分散 URL 的收集、分类、持久化存储与快速检索问题，适用于需要定期整理和展示大量外部参考链接的个人知识库、团队技术文档站或社区资源门户。LinkSphere 不提供内容抓取或代理服务，仅作为结构化 URL 索引层，帮助用户建立可维护、可审计、可分享的外链资产清单。

## 功能概览

**批量链接导入** 支持从纯文本列表、CSV 或 JSON 批量导入 URL，自动去重并校验协议格式。

**多级分类标签** 允许为每条链接打上多个自定义标签，并基于标签组合进行快速筛选。

**状态监控面板** 定时发起 HEAD 请求检查链接可达性，标记失效或重定向状态，并在 Dashboard 中可视化展示。

**全文检索与过滤** 基于 URL 路径关键词、域名后缀、状态码范围等多维度条件进行组合查询。

**导出与订阅** 支持将筛选结果导出为 Markdown 列表、JSON 或 RSS 订阅源，便于集成到其他系统。

**访问统计与热度排序** 记录每条链接的点击次数和最后访问时间，支持按热度或更新时间排序。

**团队协作注释** 允许授权用户为链接添加内部备注，记录上下文信息或使用心得，注释内容不对外公开。

## 应用场景

**技术文档参考索引** 技术团队在撰写设计文档或复盘报告时，需要引用大量外部技术文章、官方文档和社区讨论。LinkSphere 可作为统一的引用仓库，集中管理所有外链，避免文档中散落不可控的 URL。

**开源项目资源页** 开源项目维护者可以使用 LinkSphere 构建项目相关的生态资源导航页，聚合教程、视频、插件、相关工具等链接，方便社区成员快速发现周边资源。

**个人知识库外链管理** 知识管理爱好者通常会在笔记中保存大量网页链接。LinkSphere 提供独立的外链管理界面，与笔记内容解耦，通过标签和注释实现链接的长期维护和回顾。

**社区精选内容聚合** 技术社区或新闻聚合站点可使用 LinkSphere 作为后台链接管理模块，编辑人员批量导入每日精选内容链接，前端通过 API 展示分类列表，降低内容管理成本。

## 快速开始

以下指令适用于 Linux / macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆代码仓库
git clone https://github.com/linksphere/linksphere.git
cd linksphere

# 安装依赖（使用 pip 和 npm）
pip install -r requirements.txt
npm install --prefix frontend

# 初始化数据库并导入示例数据
python manage.py migrate
python manage.py loaddata fixtures/initial_tags.json

# 启动开发服务器（后端端口 8000，前端开发服务端口 3000）
python manage.py runserver &
npm start --prefix frontend &
```

访问 http://localhost:3000 即可进入 LinkSphere 主界面。首次启动时会自动创建管理员账户，默认用户名 `admin`，密码 `admin123`，请在登录后立即修改。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.12 | 后端核心运行环境，使用 Django 5.0 框架 |
| Node.js | 18.x 或 20.x LTS | 前端构建与开发服务依赖，基于 React 18 |
| PostgreSQL | 14.x 及以上 | 生产环境推荐，开发环境可使用 SQLite 替代 |
| Redis | 7.x 及以上 | 缓存与任务队列 Broker，用于状态监控任务调度 |
| Nginx | 1.24 及以上 | 生产环境反向代理与静态文件服务，非开发必需 |
| Celery Worker | 5.3.x | 异步任务执行组件，与 Redis 配合运行健康检查 |
| Django REST Framework | 3.15.x | API 接口构建依赖，用于前后端分离通信 |
| Axios | 1.6.x | 前端 HTTP 客户端，用于调用后端 API |
| SQLite | 3.35 及以上 | 开发测试环境默认数据库，生产环境请换用 PostgreSQL |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 部署运维 | `/docs/deployment/` | 如何配置生产环境、使用 Docker Compose 一键部署、设置 HTTPS 与反向代理 |
| API 参考 | `/docs/api/` | 所有 RESTful 接口的请求参数、响应格式、鉴权方式与错误码含义 |
| 开发指南 | `/docs/development/` | 如何扩展标签系统、添加新的导入解析器、自定义前端主题样式 |
| 用户手册 | `/docs/user/` | 如何进行链接批量操作、配置监控频率、导出 RSS 订阅源、管理团队注释 |
| 架构设计 | `/docs/architecture/` | 系统模块划分、数据库 ER 图、任务队列流转逻辑、缓存更新策略 |
| 测试规范 | `/docs/testing/` | 单元测试编写要求、覆盖率目标、Mock 数据规范与 CI 流水线配置 |

## 资源列表

- https://www.read.jnjpgf.cn/Article/0506275.shtml
- https://www.read.cmcvrr.cn/Article/4819.shtml
- https://www.read.hcbezg.cn/Article/1869415.shtml
- https://www.read.cmcvrr.cn/Article/4653512.shtml
- https://www.read.jnjpgf.cn/Article/1487.shtml
- https://www.read.fuvxie.cn/Article/8043.shtml
- https://www.read.nwbbyt.cn/Article/515854.shtml
- https://www.read.nwbbyt.cn/Article/8988.shtml
- https://www.read.cvsifc.cn/Article/313130.shtml
- https://www.read.cmcvrr.cn/Article/929808.shtml
- https://www.read.puhvjy.cn/Article/1428262.shtml
- https://www.read.jnjpgf.cn/Article/3980.shtml
- https://www.read.jnjpgf.cn/Article/6824477.shtml
- https://www.read.nzfnve.cn/Article/91605.shtml
- https://www.read.cvsifc.cn/Article/5077.shtml
- https://www.read.jnjpgf.cn/Article/22091.shtml
- https://www.read.fuvxie.cn/Article/551550.shtml
- https://www.read.jnjpgf.cn/Article/1178856.shtml
- https://www.read.cmcvrr.cn/Article/4396774.shtml
- https://www.read.fuvxie.cn/Article/7323731.shtml
- https://www.read.nwbbyt.cn/Article/1583.shtml
- https://www.read.puhvjy.cn/Article/0264.shtml
- https://www.read.fuvxie.cn/Article/9801641.shtml
- https://www.read.nzfnve.cn/Article/4279325.shtml
- https://www.read.cmcvrr.cn/Article/0254523.shtml
- https://www.read.hcbezg.cn/Article/9411377.shtml
- https://www.read.nwbbyt.cn/Article/342151.shtml
- https://www.read.cvsifc.cn/Article/3031606.shtml
- https://www.read.cmcvrr.cn/Article/8501.shtml
- https://www.read.jnjpgf.cn/Article/8825213.shtml
- https://www.read.fuvxie.cn/Article/1322190.shtml
- https://www.read.puhvjy.cn/Article/321096.shtml
- https://www.read.cmcvrr.cn/Article/6075.shtml
- https://www.read.puhvjy.cn/Article/4430204.shtml
- https://www.read.cmcvrr.cn/Article/845675.shtml
- https://www.read.puhvjy.cn/Article/0857.shtml
- https://www.read.jnjpgf.cn/Article/94122.shtml
- https://www.read.nwbbyt.cn/Article/0741.shtml
- https://www.read.nwbbyt.cn/Article/3477937.shtml
- https://www.read.nzfnve.cn/Article/04400.shtml
- https://www.read.jnjpgf.cn/Article/928383.shtml
- https://www.read.cvsifc.cn/Article/405461.shtml
- https://www.read.puhvjy.cn/Article/1308026.shtml
- https://www.read.nzfnve.cn/Article/7061133.shtml
- https://www.read.puhvjy.cn/Article/1664.shtml
- https://www.read.fuvxie.cn/Article/7249.shtml
- https://www.read.jnjpgf.cn/Article/5189519.shtml
- https://www.read.jnjpgf.cn/Article/3587.shtml
- https://www.read.nwbbyt.cn/Article/6306.shtml
- https://www.read.cvsifc.cn/Article/7320.shtml
- https://www.read.jnjpgf.cn/Article/72147.shtml
- https://www.read.puhvjy.cn/Article/2693483.shtml
- https://www.read.fuvxie.cn/Article/85551.shtml
- https://www.read.cmcvrr.cn/Article/094910.shtml
- https://www.read.cmcvrr.cn/Article/44624.shtml
- https://www.read.puhvjy.cn/Article/9098249.shtml
- https://www.read.hcbezg.cn/Article/3045262.shtml
- https://www.read.fuvxie.cn/Article/5690908.shtml
- https://www.read.nwbbyt.cn/Article/6095.shtml
- https://www.read.nwbbyt.cn/Article/0868.shtml
- https://www.read.cvsifc.cn/Article/8959384.shtml
- https://www.read.cvsifc.cn/Article/7489.shtml
- https://www.read.jnjpgf.cn/Article/313539.shtml
- https://www.read.fuvxie.cn/Article/8760.shtml
- https://www.read.hcbezg.cn/Article/19102.shtml
- https://www.read.fuvxie.cn/Article/5890424.shtml
- https://www.read.jnjpgf.cn/Article/330595.shtml
- https://www.read.puhvjy.cn/Article/07379.shtml
- https://www.read.nzfnve.cn/Article/0718.shtml
- https://www.read.jnjpgf.cn/Article/337947.shtml
- https://www.read.hcbezg.cn/Article/784243.shtml
- https://www.read.nzfnve.cn/Article/684119.shtml
- https://www.read.jnjpgf.cn/Article/57103.shtml
- https://www.read.hcbezg.cn/Article/1924056.shtml
- https://www.read.nzfnve.cn/Article/863591.shtml
- https://www.read.cmcvrr.cn/Article/56458.shtml
- https://www.read.cvsifc.cn/Article/016448.shtml
- https://www.read.nwbbyt.cn/Article/78202.shtml
- https://www.read.jnjpgf.cn/Article/0750728.shtml
- https://www.read.fuvxie.cn/Article/2673870.shtml
- https://www.read.cmcvrr.cn/Article/3863.shtml
- https://www.read.hcbezg.cn/Article/341546.shtml
- https://www.read.fuvxie.cn/Article/717177.shtml
- https://www.read.nzfnve.cn/Article/64198.shtml
- https://www.read.hcbezg.cn/Article/033929.shtml
- https://www.read.fuvxie.cn/Article/0272.shtml
- https://www.read.jnjpgf.cn/Article/0447249.shtml
- https://www.read.cmcvrr.cn/Article/45524.shtml
- https://www.read.puhvjy.cn/Article/7453432.shtml
- https://www.read.nwbbyt.cn/Article/6949681.shtml
- https://www.read.puhvjy.cn/Article/870625.shtml
- https://www.read.nzfnve.cn/Article/829109.shtml
- https://www.read.hcbezg.cn/Article/4957570.shtml
- https://www.read.puhvjy.cn/Article/866703.shtml
- https://www.read.nwbbyt.cn/Article/7731.shtml
- https://www.read.fuvxie.cn/Article/26965.shtml
- https://www.read.cmcvrr.cn/Article/7398.shtml
- https://www.read.jnjpgf.cn/Article/4844738.shtml
- https://www.read.cvsifc.cn/Article/1720.shtml
- https://www.read.hcbezg.cn/Article/2291311.shtml
- https://www.read.nwbbyt.cn/Article/3975.shtml
- https://www.read.puhvjy.cn/Article/66588.shtml
- https://www.read.fuvxie.cn/Article/74714.shtml
- https://www.read.fuvxie.cn/Article/2425389.shtml
- https://www.read.fuvxie.cn/Article/956595.shtml
- https://www.read.nzfnve.cn/Article/4974381.shtml
- https://www.read.nzfnve.cn/Article/8484014.shtml
- https://www.read.hcbezg.cn/Article/78066.shtml
- https://www.read.nzfnve.cn/Article/4664221.shtml
- https://www.read.nwbbyt.cn/Article/2068.shtml
- https://www.read.nwbbyt.cn/Article/3775122.shtml
- https://www.read.jnjpgf.cn/Article/722392.shtml
- https://www.read.jnjpgf.cn/Article/49808.shtml
- https://www.read.cmcvrr.cn/Article/9837717.shtml
- https://www.read.cvsifc.cn/Article/302843.shtml
- https://www.read.nzfnve.cn/Article/978724.shtml
- https://www.read.nwbbyt.cn/Article/57625.shtml
- https://www.read.cmcvrr.cn/Article/141644.shtml
- https://www.read.fuvxie.cn/Article/095820.shtml
- https://www.read.puhvjy.cn/Article/8642.shtml
- https://www.read.nwbbyt.cn/Article/82479.shtml
- https://www.read.jnjpgf.cn/Article/0206.shtml
- https://www.read.nzfnve.cn/Article/8999.shtml
- https://www.read.cmcvrr.cn/Article/5998754.shtml
- https://www.read.nwbbyt.cn/Article/422336.shtml
- https://www.read.hcbezg.cn/Article/38266.shtml
- https://www.read.cmcvrr.cn/Article/36543.shtml
- https://www.read.nwbbyt.cn/Article/2424.shtml
- https://www.read.cmcvrr.cn/Article/0717230.shtml
- https://www.read.jnjpgf.cn/Article/638669.shtml
- https://www.read.nzfnve.cn/Article/742102.shtml
- https://www.read.hcbezg.cn/Article/34314.shtml
- https://www.read.puhvjy.cn/Article/7430240.shtml
- https://www.read.puhvjy.cn/Article/8276.shtml
- https://www.read.hcbezg.cn/Article/0383.shtml
- https://www.read.cmcvrr.cn/Article/44512.shtml
- https://www.read.fuvxie.cn/Article/7176708.shtml
- https://www.read.fuvxie.cn/Article/8015452.shtml
- https://www.read.cmcvrr.cn/Article/004068.shtml
- https://www.read.nwbbyt.cn/Article/1714871.shtml
- https://www.read.nzfnve.cn/Article/45884.shtml
- https://www.read.fuvxie.cn/Article/6431.shtml
- https://www.read.nwbbyt.cn/Article/060882.shtml
- https://www.read.fuvxie.cn/Article/9799.shtml
- https://www.read.jnjpgf.cn/Article/1857.shtml
- https://www.read.jnjpgf.cn/Article/747146.shtml
- https://www.read.hcbezg.cn/Article/483660.shtml
- https://www.read.puhvjy.cn/Article/8052.shtml
- https://www.read.cvsifc.cn/Article/24299.shtml
- https://www.read.fuvxie.cn/Article/8290282.shtml
- https://www.read.hcbezg.cn/Article/2748761.shtml
- https://www.read.jnjpgf.cn/Article/01990.shtml
- https://www.read.cmcvrr.cn/Article/66654.shtml
- https://www.read.nwbbyt.cn/Article/57825.shtml
- https://www.read.fuvxie.cn/Article/61099.shtml
- https://www.read.jnjpgf.cn/Article/62073.shtml
- https://www.read.cvsifc.cn/Article/37040.shtml
- https://www.read.puhvjy.cn/Article/4562.shtml
- https://www.read.cmcvrr.cn/Article/8729631.shtml
- https://www.read.cmcvrr.cn/Article/3435094.shtml
- https://www.read.cmcvrr.cn/Article/3268.shtml
- https://www.read.nwbbyt.cn/Article/73360.shtml
- https://www.read.puhvjy.cn/Article/22789.shtml
- https://www.read.jnjpgf.cn/Article/58003.shtml
- https://www.read.nzfnve.cn/Article/7246979.shtml
- https://www.read.cvsifc.cn/Article/6949800.shtml
- https://www.read.jnjpgf.cn/Article/1161692.shtml
- https://www.read.fuvxie.cn/Article/03186.shtml
- https://www.read.jnjpgf.cn/Article/31577.shtml
- https://www.read.nwbbyt.cn/Article/0943.shtml
- https://www.read.cmcvrr.cn/Article/3099290.shtml
- https://www.read.cvsifc.cn/Article/588610.shtml
- https://www.read.nwbbyt.cn/Article/1865785.shtml
- https://www.read.nwbbyt.cn/Article/8761428.shtml
- https://www.read.cvsifc.cn/Article/1956.shtml
- https://www.read.fuvxie.cn/Article/7627544.shtml
- https://www.read.nzfnve.cn/Article/2022.shtml
- https://www.read.hcbezg.cn/Article/78006.shtml
- https://www.read.fuvxie.cn/Article/194962.shtml
- https://www.read.hcbezg.cn/Article/545824.shtml
- https://www.read.cvsifc.cn/Article/64904.shtml
- https://www.read.jnjpgf.cn/Article/46392.shtml
- https://www.read.hcbezg.cn/Article/62391.shtml
- https://www.read.hcbezg.cn/Article/6857.shtml
- https://www.read.jnjpgf.cn/Article/0955983.shtml
- https://www.read.jnjpgf.cn/Article/76353.shtml
- https://www.read.jnjpgf.cn/Article/08039.shtml
- https://www.read.nzfnve.cn/Article/3576252.shtml
- https://www.read.fuvxie.cn/Article/0788.shtml
- https://www.read.nzfnve.cn/Article/105609.shtml
- https://www.read.hcbezg.cn/Article/18296.shtml
- https://www.read.nzfnve.cn/Article/6593.shtml
- https://www.read.jnjpgf.cn/Article/4633.shtml
- https://www.read.nzfnve.cn/Article/9251.shtml
- https://www.read.fuvxie.cn/Article/074036.shtml
- https://www.read.hcbezg.cn/Article/189072.shtml
- https://www.read.cmcvrr.cn/Article/1517544.shtml
- https://www.read.nzfnve.cn/Article/52260.shtml
- https://www.read.cmcvrr.cn/Article/70500.shtml
- https://www.read.fuvxie.cn/Article/461794.shtml
- https://www.read.fuvxie.cn/Article/592512.shtml
- https://www.read.cvsifc.cn/Article/5874.shtml
- https://www.read.nwbbyt.cn/Article/3615.shtml
- https://www.read.hcbezg.cn/Article/9175962.shtml
- https://www.read.hcbezg.cn/Article/71795.shtml
- https://www.read.hcbezg.cn/Article/7895.shtml
- https://www.read.cvsifc.cn/Article/2385.shtml
- https://www.read.fuvxie.cn/Article/84040.shtml
- https://www.read.cmcvrr.cn/Article/3912.shtml
- https://www.read.cmcvrr.cn/Article/907863.shtml
- https://www.read.jnjpgf.cn/Article/6426602.shtml
- https://www.read.nwbbyt.cn/Article/26826.shtml
- https://www.read.cvsifc.cn/Article/75774.shtml
- https://www.read.cvsifc.cn/Article/667294.shtml
- https://www.read.nzfnve.cn/Article/3072.shtml
- https://www.read.puhvjy.cn/Article/309643.shtml
- https://www.read.cvsifc.cn/Article/4042.shtml
- https://www.read.puhvjy.cn/Article/0036012.shtml
- https://www.read.fuvxie.cn/Article/301853.shtml
- https://www.read.hcbezg.cn/Article/59017.shtml
- https://www.read.fuvxie.cn/Article/9844.shtml
- https://www.read.fuvxie.cn/Article/45699.shtml
- https://www.read.fuvxie.cn/Article/9871599.shtml
- https://www.read.cmcvrr.cn/Article/0021648.shtml
- https://www.read.jnjpgf.cn/Article/89157.shtml
- https://www.read.nzfnve.cn/Article/5734.shtml
- https://www.read.cvsifc.cn/Article/7771.shtml
- https://www.read.hcbezg.cn/Article/287413.shtml
- https://www.read.nwbbyt.cn/Article/5412.shtml
- https://www.read.jnjpgf.cn/Article/3090125.shtml
- https://www.read.cmcvrr.cn/Article/1471.shtml
- https://www.read.hcbezg.cn/Article/7201.shtml
- https://www.read.nwbbyt.cn/Article/3465.shtml
- https://www.read.cmcvrr.cn/Article/4697.shtml
- https://www.read.nwbbyt.cn/Article/23163.shtml
- https://www.read.fuvxie.cn/Article/64970.shtml
- https://www.read.nwbbyt.cn/Article/86281.shtml
- https://www.read.nwbbyt.cn/Article/56264.shtml
- https://www.read.nzfnve.cn/Article/1020.shtml
- https://www.read.jnjpgf.cn/Article/8039.shtml
- https://www.read.hcbezg.cn/Article/1579774.shtml
- https://www.read.cvsifc.cn/Article/30350.shtml
- https://www.read.fuvxie.cn/Article/531962.shtml
- https://www.read.puhvjy.cn/Article/0805.shtml
- https://www.read.nwbbyt.cn/Article/60769.shtml
- https://www.read.jnjpgf.cn/Article/441894.shtml
- https://www.read.fuvxie.cn/Article/81059.shtml
- https://www.read.jnjpgf.cn/Article/911907.shtml
- https://www.read.cmcvrr.cn/Article/5382.shtml
- https://www.read.cvsifc.cn/Article/75898.shtml

## 项目结构

```
linksphere/
├── backend/                         # Django 后端主目录
│   ├── api/                         # REST API 应用，处理所有接口逻辑
│   │   ├── views/                   # 视图集，按资源类型拆分（links, tags, checks）
│   │   ├── serializers/             # 序列化器，定义数据校验与输出格式
│   │   └── permissions/             # 自定义权限类，控制团队协作访问级别
│   ├── core/                        # 核心配置与公共工具
│   │   ├── settings/                # 多环境配置文件（base, dev, prod）
│   │   ├── utils/                   # 通用工具函数（URL 解析、日期处理、去重算法）
│   │   └── exceptions/              # 全局异常处理与自定义错误码
│   ├── tasks/                       # Celery 异步任务模块
│   │   ├── health_check.py          # 链接可达性检查任务，定时执行 HEAD 请求
│   │   ├── import_export.py         # 批量导入导出任务，支持 CSV/JSON 流式处理
│   │   └── stats_aggregator.py      # 访问统计聚合任务，每小时更新热度排行
│   ├── models/                      # 数据库模型定义
│   │   ├── link.py                  # Link 模型，含 URL、标题、状态码、最后检查时间等字段
│   │   ├── tag.py                   # Tag 模型，含名称、颜色、所属分组
│   │   ├── annotation.py            # Annotation 模型，存储用户备注与历史版本
│   │   └── click_log.py             # 点击日志模型，记录访问来源与时间戳
│   └── management/                  # 自定义 Django 管理命令
│       ├── commands/                # 包含 init_tags, import_links, export_rss 等命令
│       └── fixtures/                # 初始数据固件，用于快速启动演示
├── frontend/                        # React 前端单页应用
│   ├── src/
│   │   ├── pages/                   # 页面级组件（Dashboard, LinkList, TagManager, Settings）
│   │   ├── components/              # 可复用 UI 组件（DataTable, FilterBar, StatusBadge, ChartCard）
│   │   ├── hooks/                   # 自定义 React Hooks（useLinks, useTags, usePolling）
│   │   ├── services/                # API 调用封装，按资源模块拆分
│   │   └── store/                   # Redux 状态管理（slices 按功能拆分）
│   ├── public/                      # 静态资源入口
│   └── tests/                       # 前端单元测试（Jest + React Testing Library）
├── deployment/                      # 部署相关配置
│   ├── docker/                      # Dockerfile 与 Compose 编排文件
│   │   ├── Dockerfile.backend       # 后端容器构建脚本，基于 Python 3.11-slim
│   │   ├── Dockerfile.frontend      # 前端构建脚本，多阶段构建，产出 Nginx 静态镜像
│   │   └── docker-compose.yml       # 全栈服务编排，含 Postgres、Redis、Nginx、Celery
│   ├── kubernetes/                  # K8s 部署清单（可选，用于大规模生产环境）
│   └── nginx/                       # Nginx 配置模板，含 gzip 压缩与静态缓存策略
├── docs/                            # 项目文档源码（Markdown + MkDocs）
│   ├── deployment/                  # 部署文档
│   ├── api/                         # API 文档（由 drf-yasg 自动生成，人工补充说明）
│   └── user/                        # 用户手册与操作指南
├── scripts/                         # 开发辅助脚本
│   ├── seed_test_data.py            # 生成测试数据，用于性能压测
│   ├── migrate_legacy.py            # 从旧版系统迁移数据的转换脚本
│   └── backup_database.sh           # 数据库备份脚本，配合 cron 使用
├── tests/                           # 后端集成测试与端到端测试
│   ├── integration/                 # API 接口集成测试（pytest）
│   └── e2e/                         # 端到端测试（Playwright 模拟用户操作）
├── .github/                         # GitHub 工作流配置
│   └── workflows/                   # CI 流水线（代码检查、单元测试、构建镜像、推送仓库）
├── requirements.txt                 # Python 依赖锁定文件（生产与开发分组）
├── package.json                     # Node.js 依赖声明（前端与开发工具）
├── Makefile                         # 常用命令封装（install, test, lint, migrate, dev）
└── README.md                        # 项目总览文档（即本文档）
```

## 贡献指南

**问题报告与需求建议** 前往 GitHub Issues 页面搜索是否已有类似问题，若无则新建 Issue，选择对应模板并填写复现步骤、环境信息或需求描述。请勿在 Issue 中粘贴大量 URL 列表，可提供样本数据或链接至外部文件。

**代码贡献流程** Fork 本仓库至个人账号，在 `dev` 分支基础上新建功能分支，命名规范为 `feature/功能简述` 或 `fix/问题简述`。开发完成后提交 Pull Request 至 `dev` 分支，PR 描述中需关联相关 Issue 编号，并通过 CI 所有检查项（代码风格、单元测试、构建）。

**文档与示例完善** 欢迎补充使用案例、API 调用示例或翻译文档。文档修改可直接提交 PR，无需关联 Issue。新增示例数据或导入模板时，请确保文件格式与现有 schema 保持一致。

**测试覆盖要求** 新增后端接口或前端组件时，需同步编写单元测试，后端测试覆盖率不得低于 85%，前端核心逻辑覆盖率不低于 70%。测试用例应包含正常路径与异常路径。

**维护者审核周期** 维护者将在 3 个工作日内审核 PR，给出修改意见或进行合并。较大的功能改动建议先通过 Issue 进行设计讨论，避免开发方向偏离项目规划。

## 常见问题

**Q: 导入大量 URL 时页面卡顿或超时怎么办？**

A: 建议使用异步导入模式。在导入界面选择“后台任务”选项，系统会将导入操作交由 Celery 工作进程处理，并返回任务 ID。用户可在任务中心查看进度，导入完成后会收到通知。单次导入建议不超过 5000 条，更大规模数据可分批提交。

**Q: 链接健康检查显示失效，但浏览器可以正常打开？**

A: 健康检查默认使用 HEAD 请求，部分服务器可能对 HEAD 请求返回 405 或 403 状态码，但实际 GET 请求可访问。您可以在检查配置中将方法切换为 GET，或增加自定义请求头（如 User-Agent）。另外，检查超时时间默认 5 秒，网络延迟较高时可适当调大超时阈值。

**Q: 如何将 LinkSphere 部署到内网环境且不依赖外部网络？**

A: 在内网部署时，所有前端依赖（React、Axios 等）需使用离线包或内网镜像源，后端依赖可通过 `pip download` 离线打包。由于健康检查任务会向外发起请求，建议在内网环境下禁用自动检查功能，或配置代理访问外网资源。数据库和缓存服务均使用内网地址，无需连接外部服务。

## 许可证

MIT License

Copyright (c) 2026 LinkSphere Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:20

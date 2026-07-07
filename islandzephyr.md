# LinkHub

LinkHub 是一个面向技术研究者、内容聚合者与信息管理者的轻量级外链资源汇总平台。该项目旨在解决分散化、碎片化的优质外链资源难以统一管理和持续追踪的问题，通过结构化的目录体系与静态文档站点，将大量外部文章链接组织为可检索、可归档、可共享的知识索引库。LinkHub 不存储原始内容，仅提供链接索引与元信息描述，适用于个人知识管理、团队技术沉淀、公开资源导航等场景。

## 功能概览

- 多级目录分类体系：支持按技术领域、主题标签、来源站点等多维度对链接进行归类，便于快速定位。
- 全文检索与筛选：集成标题关键词搜索与字段过滤，支持按发布时间、关联标签等条件筛选链接条目。
- 链接状态检测：定期对收录链接进行可用性检查，自动标记失效链接，保障索引质量。
- 批量导入与导出：支持通过 CSV、JSON 格式批量新增或导出链接数据，便于迁移与备份。
- 访问统计与热度排序：记录链接点击次数，支持按热度、更新时间排序，发现高频访问资源。
- Markdown 文档生成：基于链接元数据自动生成静态站点或 README 索引页，方便离线阅读与版本管理。
- 协作审核机制：提供链接提交与审核工作流，支持多人在线维护索引库，避免冗余与错误收录。
- API 查询接口：提供 RESTful API 用于外部系统集成，支持按条件查询链接详情与分类树。

## 应用场景

- 技术团队内部知识库建设：开发团队可将日常调研、踩坑记录、技术文档中引用的外部参考链接统一录入 LinkHub，形成团队共享的技术外链索引，减少重复搜索成本。
- 开源项目文档站的外链管理：开源项目维护者可在项目文档中嵌入 LinkHub 生成的链接列表，将项目依赖的规范、教程、工具站点等外链集中呈现，提升文档的可维护性。
- 个人研究者学术资源归档：研究生、科研人员或独立研究者可将不同课题涉及的论文链接、数据集页面、工具仓库等按项目分类归档，配合检索功能快速回溯历史参考材料。
- 技术社区资源导航站建设：技术社区运营方可使用 LinkHub 搭建公开的资源导航页面，按编程语言、框架版本、应用领域等维度整理高质量外链，服务更广泛的开发者群体。

## 快速开始

以下操作以 Linux / macOS 环境为例，Windows 用户可使用 Git Bash 或 WSL 执行。

```bash
# 1. 克隆仓库
git clone https://github.com/your-org/linkhub.git
cd linkhub

# 2. 安装依赖（Python 3.9+ 环境）
pip install -r requirements.txt

# 3. 初始化数据库并启动开发服务
python manage.py migrate
python manage.py runserver 0.0.0.0:8000
```

启动后，访问 http://localhost:8000 即可进入 LinkHub 索引管理界面。默认管理员账号可通过 `python manage.py createsuperuser` 创建。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.11 | 核心运行环境，推荐使用 3.10 稳定版 |
| Django | 4.2.x | Web 框架，用于提供管理界面与 API 服务 |
| SQLite / PostgreSQL | SQLite 3.35+ / PostgreSQL 13+ | 默认使用 SQLite 开发，生产环境建议切换至 PostgreSQL |
| requests | 2.31.0+ | 用于链接状态检测与外部资源请求 |
| beautifulsoup4 | 4.12.0+ | 用于解析外部页面标题与摘要信息 |
| redis | 6.0+ (可选) | 缓存与任务队列后端，不配置时使用内存缓存 |
| gunicorn | 21.2.0+ (生产环境) | WSGI 服务进程管理，用于生产部署 |
| nodejs | 18.x (可选) | 仅当启用前端资源构建任务时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何快速完成安装、首次启动并录入第一批链接？ |
| 管理手册 | docs/admin-guide.md | 如何管理分类、批量导入链接、配置状态检测策略？ |
| API 参考 | docs/api-reference.md | 如何通过 RESTful API 查询链接列表、分类树及统计信息？ |
| 部署指南 | docs/deployment.md | 如何将 LinkHub 部署至生产环境（Nginx + Gunicorn + PostgreSQL）？ |
| 架构设计 | docs/architecture.md | LinkHub 的整体模块划分、数据流与扩展点设计是怎样的？ |
| 贡献规范 | docs/contributing.md | 如何提交新分类模板、改进检测逻辑或完善文档？ |

## 资源列表

- https://www.read.fuvxie.cn/Article/44981.shtml
- https://www.read.cmcvrr.cn/Article/14507.shtml
- https://www.read.cmcvrr.cn/Article/30779.shtml
- https://www.read.hcbezg.cn/Article/9691.shtml
- https://www.read.cmcvrr.cn/Article/4912118.shtml
- https://www.read.jnjpgf.cn/Article/39434.shtml
- https://www.read.cmcvrr.cn/Article/332494.shtml
- https://www.read.nwbbyt.cn/Article/637602.shtml
- https://www.read.nzfnve.cn/Article/54257.shtml
- https://www.read.jnjpgf.cn/Article/72779.shtml
- https://www.read.nzfnve.cn/Article/61186.shtml
- https://www.read.hcbezg.cn/Article/64564.shtml
- https://www.read.hcbezg.cn/Article/179691.shtml
- https://www.read.fuvxie.cn/Article/6452.shtml
- https://www.read.fuvxie.cn/Article/5615.shtml
- https://www.read.cmcvrr.cn/Article/56707.shtml
- https://www.read.cvsifc.cn/Article/70938.shtml
- https://www.read.nwbbyt.cn/Article/6448669.shtml
- https://www.read.nwbbyt.cn/Article/0002414.shtml
- https://www.read.puhvjy.cn/Article/4951.shtml
- https://www.read.cmcvrr.cn/Article/6488.shtml
- https://www.read.cvsifc.cn/Article/1336.shtml
- https://www.read.fuvxie.cn/Article/35294.shtml
- https://www.read.puhvjy.cn/Article/3207807.shtml
- https://www.read.fuvxie.cn/Article/12185.shtml
- https://www.read.jnjpgf.cn/Article/2356.shtml
- https://www.read.nwbbyt.cn/Article/63278.shtml
- https://www.read.cvsifc.cn/Article/001506.shtml
- https://www.read.nzfnve.cn/Article/78372.shtml
- https://www.read.fuvxie.cn/Article/43789.shtml
- https://www.read.nwbbyt.cn/Article/447834.shtml
- https://www.read.fuvxie.cn/Article/6679.shtml
- https://www.read.hcbezg.cn/Article/47657.shtml
- https://www.read.jnjpgf.cn/Article/051777.shtml
- https://www.read.jnjpgf.cn/Article/7698969.shtml
- https://www.read.cmcvrr.cn/Article/0962.shtml
- https://www.read.cmcvrr.cn/Article/9602.shtml
- https://www.read.fuvxie.cn/Article/75477.shtml
- https://www.read.fuvxie.cn/Article/719104.shtml
- https://www.read.hcbezg.cn/Article/7294.shtml
- https://www.read.jnjpgf.cn/Article/7431.shtml
- https://www.read.puhvjy.cn/Article/20841.shtml
- https://www.read.puhvjy.cn/Article/4774.shtml
- https://www.read.hcbezg.cn/Article/7429.shtml
- https://www.read.nzfnve.cn/Article/7245.shtml
- https://www.read.puhvjy.cn/Article/4945400.shtml
- https://www.read.nzfnve.cn/Article/8199.shtml
- https://www.read.puhvjy.cn/Article/22619.shtml
- https://www.read.jnjpgf.cn/Article/30566.shtml
- https://www.read.nwbbyt.cn/Article/485526.shtml
- https://www.read.puhvjy.cn/Article/53266.shtml
- https://www.read.jnjpgf.cn/Article/362337.shtml
- https://www.read.nwbbyt.cn/Article/113533.shtml
- https://www.read.nwbbyt.cn/Article/2436629.shtml
- https://www.read.cvsifc.cn/Article/8262084.shtml
- https://www.read.jnjpgf.cn/Article/09330.shtml
- https://www.read.nzfnve.cn/Article/37175.shtml
- https://www.read.puhvjy.cn/Article/419001.shtml
- https://www.read.puhvjy.cn/Article/84883.shtml
- https://www.read.hcbezg.cn/Article/7909084.shtml
- https://www.read.fuvxie.cn/Article/1351.shtml
- https://www.read.cvsifc.cn/Article/0635701.shtml
- https://www.read.cvsifc.cn/Article/7418.shtml
- https://www.read.cvsifc.cn/Article/69322.shtml
- https://www.read.nwbbyt.cn/Article/06659.shtml
- https://www.read.nzfnve.cn/Article/1467939.shtml
- https://www.read.fuvxie.cn/Article/1637009.shtml
- https://www.read.nwbbyt.cn/Article/792120.shtml
- https://www.read.hcbezg.cn/Article/1242252.shtml
- https://www.read.nzfnve.cn/Article/98726.shtml
- https://www.read.hcbezg.cn/Article/4811698.shtml
- https://www.read.nwbbyt.cn/Article/610922.shtml
- https://www.read.jnjpgf.cn/Article/120317.shtml
- https://www.read.cmcvrr.cn/Article/494417.shtml
- https://www.read.nzfnve.cn/Article/099685.shtml
- https://www.read.puhvjy.cn/Article/248173.shtml
- https://www.read.fuvxie.cn/Article/6406.shtml
- https://www.read.puhvjy.cn/Article/443647.shtml
- https://www.read.cmcvrr.cn/Article/9278.shtml
- https://www.read.nzfnve.cn/Article/330400.shtml
- https://www.read.cmcvrr.cn/Article/942050.shtml
- https://www.read.cmcvrr.cn/Article/68804.shtml
- https://www.read.nzfnve.cn/Article/94796.shtml
- https://www.read.hcbezg.cn/Article/8188.shtml
- https://www.read.cmcvrr.cn/Article/2146.shtml
- https://www.read.nwbbyt.cn/Article/5375312.shtml
- https://www.read.nwbbyt.cn/Article/714796.shtml
- https://www.read.fuvxie.cn/Article/31564.shtml
- https://www.read.nzfnve.cn/Article/91019.shtml
- https://www.read.fuvxie.cn/Article/30033.shtml
- https://www.read.cvsifc.cn/Article/42531.shtml
- https://www.read.jnjpgf.cn/Article/1852.shtml
- https://www.read.cvsifc.cn/Article/7389779.shtml
- https://www.read.nzfnve.cn/Article/196987.shtml
- https://www.read.hcbezg.cn/Article/42726.shtml
- https://www.read.nwbbyt.cn/Article/3947821.shtml
- https://www.read.puhvjy.cn/Article/6413368.shtml
- https://www.read.nwbbyt.cn/Article/61504.shtml
- https://www.read.puhvjy.cn/Article/40062.shtml
- https://www.read.nzfnve.cn/Article/474944.shtml
- https://www.read.cmcvrr.cn/Article/1075194.shtml
- https://www.read.hcbezg.cn/Article/43165.shtml
- https://www.read.nwbbyt.cn/Article/2672.shtml
- https://www.read.jnjpgf.cn/Article/70803.shtml
- https://www.read.cmcvrr.cn/Article/0766091.shtml
- https://www.read.jnjpgf.cn/Article/9167902.shtml
- https://www.read.hcbezg.cn/Article/2501229.shtml
- https://www.read.cvsifc.cn/Article/2957412.shtml
- https://www.read.cvsifc.cn/Article/68898.shtml
- https://www.read.cmcvrr.cn/Article/8980307.shtml
- https://www.read.cmcvrr.cn/Article/5632.shtml
- https://www.read.cmcvrr.cn/Article/5206.shtml
- https://www.read.nzfnve.cn/Article/65338.shtml
- https://www.read.hcbezg.cn/Article/1980.shtml
- https://www.read.nwbbyt.cn/Article/7158.shtml
- https://www.read.cvsifc.cn/Article/07369.shtml
- https://www.read.cmcvrr.cn/Article/68831.shtml
- https://www.read.jnjpgf.cn/Article/76293.shtml
- https://www.read.hcbezg.cn/Article/64070.shtml
- https://www.read.nwbbyt.cn/Article/59975.shtml
- https://www.read.fuvxie.cn/Article/376960.shtml
- https://www.read.jnjpgf.cn/Article/0888942.shtml
- https://www.read.nzfnve.cn/Article/3312043.shtml
- https://www.read.hcbezg.cn/Article/4222.shtml
- https://www.read.puhvjy.cn/Article/0000292.shtml
- https://www.read.nzfnve.cn/Article/60674.shtml
- https://www.read.fuvxie.cn/Article/3101.shtml
- https://www.read.nwbbyt.cn/Article/06453.shtml
- https://www.read.nwbbyt.cn/Article/57085.shtml
- https://www.read.nwbbyt.cn/Article/1452828.shtml
- https://www.read.puhvjy.cn/Article/85728.shtml
- https://www.read.cmcvrr.cn/Article/5690.shtml
- https://www.read.cmcvrr.cn/Article/7449041.shtml
- https://www.read.hcbezg.cn/Article/3025942.shtml
- https://www.read.cmcvrr.cn/Article/52456.shtml
- https://www.read.fuvxie.cn/Article/389352.shtml
- https://www.read.cvsifc.cn/Article/6453347.shtml
- https://www.read.nzfnve.cn/Article/54090.shtml
- https://www.read.cmcvrr.cn/Article/88774.shtml
- https://www.read.hcbezg.cn/Article/825804.shtml
- https://www.read.hcbezg.cn/Article/04593.shtml
- https://www.read.hcbezg.cn/Article/7820085.shtml
- https://www.read.hcbezg.cn/Article/2216977.shtml
- https://www.read.nwbbyt.cn/Article/973296.shtml
- https://www.read.nzfnve.cn/Article/0363.shtml
- https://www.read.cvsifc.cn/Article/49799.shtml
- https://www.read.nzfnve.cn/Article/237877.shtml
- https://www.read.fuvxie.cn/Article/8307047.shtml
- https://www.read.jnjpgf.cn/Article/9967.shtml
- https://www.read.nzfnve.cn/Article/96347.shtml
- https://www.read.hcbezg.cn/Article/732457.shtml
- https://www.read.nzfnve.cn/Article/6285723.shtml
- https://www.read.hcbezg.cn/Article/77913.shtml
- https://www.read.jnjpgf.cn/Article/87224.shtml
- https://www.read.cmcvrr.cn/Article/108492.shtml
- https://www.read.nwbbyt.cn/Article/72358.shtml
- https://www.read.cmcvrr.cn/Article/28404.shtml
- https://www.read.cvsifc.cn/Article/48275.shtml
- https://www.read.puhvjy.cn/Article/4957.shtml
- https://www.read.nzfnve.cn/Article/0139855.shtml
- https://www.read.fuvxie.cn/Article/8497.shtml
- https://www.read.fuvxie.cn/Article/141334.shtml
- https://www.read.cmcvrr.cn/Article/4765084.shtml
- https://www.read.cmcvrr.cn/Article/5704412.shtml
- https://www.read.puhvjy.cn/Article/079277.shtml
- https://www.read.cvsifc.cn/Article/8079099.shtml
- https://www.read.cmcvrr.cn/Article/235554.shtml
- https://www.read.cmcvrr.cn/Article/1786421.shtml
- https://www.read.cmcvrr.cn/Article/39491.shtml
- https://www.read.hcbezg.cn/Article/84768.shtml
- https://www.read.nwbbyt.cn/Article/4052586.shtml
- https://www.read.fuvxie.cn/Article/7729260.shtml
- https://www.read.jnjpgf.cn/Article/6456.shtml
- https://www.read.cmcvrr.cn/Article/70585.shtml
- https://www.read.fuvxie.cn/Article/104814.shtml
- https://www.read.hcbezg.cn/Article/765739.shtml
- https://www.read.puhvjy.cn/Article/6109.shtml
- https://www.read.cmcvrr.cn/Article/9843.shtml
- https://www.read.jnjpgf.cn/Article/055758.shtml
- https://www.read.hcbezg.cn/Article/3297693.shtml
- https://www.read.fuvxie.cn/Article/2071763.shtml
- https://www.read.cvsifc.cn/Article/64495.shtml
- https://www.read.puhvjy.cn/Article/813456.shtml
- https://www.read.cmcvrr.cn/Article/9649494.shtml
- https://www.read.fuvxie.cn/Article/00160.shtml
- https://www.read.nwbbyt.cn/Article/5749.shtml
- https://www.read.hcbezg.cn/Article/0068124.shtml
- https://www.read.puhvjy.cn/Article/7518.shtml
- https://www.read.cvsifc.cn/Article/6609945.shtml
- https://www.read.hcbezg.cn/Article/064482.shtml
- https://www.read.nzfnve.cn/Article/4771923.shtml
- https://www.read.nzfnve.cn/Article/27513.shtml
- https://www.read.jnjpgf.cn/Article/5159.shtml
- https://www.read.hcbezg.cn/Article/84677.shtml
- https://www.read.puhvjy.cn/Article/0116.shtml
- https://www.read.fuvxie.cn/Article/2014.shtml
- https://www.read.cmcvrr.cn/Article/85164.shtml
- https://www.read.puhvjy.cn/Article/0351138.shtml
- https://www.read.puhvjy.cn/Article/6178432.shtml
- https://www.read.nzfnve.cn/Article/9231613.shtml
- https://www.read.nwbbyt.cn/Article/75097.shtml
- https://www.read.hcbezg.cn/Article/0237.shtml
- https://www.read.puhvjy.cn/Article/428418.shtml
- https://www.read.fuvxie.cn/Article/4576287.shtml
- https://www.read.puhvjy.cn/Article/99834.shtml
- https://www.read.hcbezg.cn/Article/5572.shtml
- https://www.read.hcbezg.cn/Article/8452.shtml
- https://www.read.fuvxie.cn/Article/417532.shtml
- https://www.read.jnjpgf.cn/Article/232343.shtml
- https://www.read.puhvjy.cn/Article/6808.shtml
- https://www.read.cvsifc.cn/Article/5576.shtml
- https://www.read.puhvjy.cn/Article/8266.shtml
- https://www.read.puhvjy.cn/Article/7247.shtml
- https://www.read.jnjpgf.cn/Article/1840.shtml
- https://www.read.cmcvrr.cn/Article/5623184.shtml
- https://www.read.puhvjy.cn/Article/57337.shtml
- https://www.read.hcbezg.cn/Article/74356.shtml
- https://www.read.fuvxie.cn/Article/06905.shtml
- https://www.read.cvsifc.cn/Article/358516.shtml
- https://www.read.nwbbyt.cn/Article/307158.shtml
- https://www.read.nzfnve.cn/Article/55370.shtml
- https://www.read.nwbbyt.cn/Article/12454.shtml
- https://www.read.puhvjy.cn/Article/7558032.shtml
- https://www.read.cvsifc.cn/Article/9597.shtml
- https://www.read.nzfnve.cn/Article/6462.shtml
- https://www.read.puhvjy.cn/Article/4488418.shtml
- https://www.read.jnjpgf.cn/Article/5093311.shtml
- https://www.read.fuvxie.cn/Article/0596.shtml
- https://www.read.fuvxie.cn/Article/9735126.shtml
- https://www.read.nwbbyt.cn/Article/723296.shtml
- https://www.read.cvsifc.cn/Article/308177.shtml
- https://www.read.puhvjy.cn/Article/281144.shtml
- https://www.read.hcbezg.cn/Article/6079426.shtml
- https://www.read.nwbbyt.cn/Article/7436773.shtml
- https://www.read.fuvxie.cn/Article/42183.shtml
- https://www.read.cmcvrr.cn/Article/362408.shtml
- https://www.read.fuvxie.cn/Article/4453.shtml
- https://www.read.nwbbyt.cn/Article/6028.shtml
- https://www.read.nzfnve.cn/Article/215673.shtml
- https://www.read.hcbezg.cn/Article/8746447.shtml
- https://www.read.jnjpgf.cn/Article/473507.shtml
- https://www.read.nwbbyt.cn/Article/83523.shtml
- https://www.read.cmcvrr.cn/Article/980761.shtml
- https://www.read.nzfnve.cn/Article/36100.shtml
- https://www.read.cvsifc.cn/Article/6848195.shtml
- https://www.read.fuvxie.cn/Article/082479.shtml
- https://www.read.puhvjy.cn/Article/9560.shtml
- https://www.read.puhvjy.cn/Article/17077.shtml
- https://www.read.fuvxie.cn/Article/0509222.shtml
- https://www.read.fuvxie.cn/Article/302874.shtml

## 项目结构

```
linkhub/
├── manage.py                      # Django 项目管理入口
├── requirements.txt               # Python 依赖清单
├── .env.example                   # 环境变量配置模板
├── linkhub/                       # 项目主配置目录
│   ├── __init__.py
│   ├── settings.py                # 基础配置（含数据库、缓存、日志）
│   ├── settings_prod.py           # 生产环境覆盖配置
│   ├── urls.py                    # 根路由配置
│   └── wsgi.py                    # WSGI 应用入口
├── apps/                          # 所有自定义应用
│   ├── core/                      # 核心数据模型与公共工具
│   │   ├── models.py              # Link、Category、Tag 等数据模型
│   │   ├── utils.py               # 链接状态检测、摘要解析等工具函数
│   │   └── validators.py          # 自定义字段校验器
│   ├── api/                       # RESTful API 应用
│   │   ├── views.py               # 基于 DRF 的视图集
│   │   ├── serializers.py         # 序列化器定义
│   │   └── routers.py             # 路由注册
│   ├── dashboard/                 # 管理后台应用（Django Admin 增强）
│   │   ├── admin.py               # 模型管理注册与自定义展示
│   │   ├── forms.py               # 后台表单校验
│   │   └── widgets.py             # 自定义表单控件
│   └── scanners/                  # 链接扫描与状态检测任务
│       ├── tasks.py               # Celery 定时任务定义
│       ├── checkers.py            # HTTP 状态码检测、超时重试逻辑
│       └── parsers.py             # 页面标题与 meta 信息提取
├── static/                        # 静态资源（CSS、JS、图片）
│   ├── css/
│   ├── js/
│   └── images/
├── templates/                     # Django 模板文件
│   ├── base.html                  # 基础页面骨架
│   ├── index.html                 # 首页链接列表
│   └── detail.html                # 单个链接详情页
├── docs/                          # 项目文档
│   ├── quickstart.md
│   ├── admin-guide.md
│   ├── api-reference.md
│   ├── deployment.md
│   ├── architecture.md
│   └── contributing.md
├── scripts/                       # 运维与辅助脚本
│   ├── import_links.py            # 批量导入链接脚本
│   ├── export_links.py            # 批量导出链接脚本
│   └── health_check.py            # 系统健康检查脚本
├── tests/                         # 单元测试与集成测试
│   ├── test_models.py
│   ├── test_api.py
│   └── test_scanners.py
└── docker/                        # Docker 部署相关
    ├── Dockerfile
    ├── docker-compose.yml
    └── nginx.conf
```

## 贡献指南

1. 查阅问题追踪列表：访问 GitHub Issues 或内部工单系统，查找标记为 `help wanted` 或 `good first issue` 的任务，确认无重复工作后认领。
2. 派生仓库并创建特性分支：从主仓库派生个人副本，使用 `git checkout -b feature/your-feature-name` 创建新分支，避免直接在主分支修改。
3. 编写或修改代码并补充测试：遵循项目现有代码风格（PEP 8），新增功能需附带单元测试，确保测试通过（`python manage.py test`）。
4. 提交变更并推送分支：提交信息使用约定式提交格式（如 `feat: add batch import support`），推送后创建 Pull Request 至主仓库的 `develop` 分支。
5. 参与评审并完成合并：维护者将在 PR 中提出修改意见，贡献者需及时响应并更新代码，最终由维护者合并至主分支。

## 常见问题

Q: LinkHub 是否存储外部文章的内容副本？
A: 不存储。LinkHub 仅保存链接地址、标题、来源域名、分类标签等元数据，所有内容仍由原始站点提供。项目不涉及任何版权内容缓存或代理转发。

Q: 链接状态检测的频率和超时策略是什么？
A: 默认每 24 小时执行一次全局检测，单次请求超时时间为 10 秒，连续失败 3 次标记为失效。检测策略可通过 `scanners/tasks.py` 中的配置参数调整。

Q: 如何将现有的大量链接快速导入 LinkHub？
A: 项目提供了 `scripts/import_links.py` 脚本，支持 CSV 和 JSON 格式导入。CSV 表头需包含 `url, title, category, tags` 等字段，详细用法请参考 `docs/admin-guide.md` 中的批量操作章节。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

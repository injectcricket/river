# READ 外链资源聚合平台

READ 是一个面向技术内容消费者与信息检索者的外链资源聚合平台，旨在系统化收集、分类和呈现分散于多个内容源站点的技术文章、案例分析与工程实践文档。本项目并非搜索引擎，亦非内容托管系统，而是一个轻量级、可维护的链接索引中间层，帮助技术团队、研究人员与独立开发者高效定位特定主题下的高质量阅读材料。

目标用户包括需要快速查阅技术决策参考的架构师、需要补充背景知识的研发工程师、以及从事技术趋势分析的产研管理人员。项目本身不存储任何实际文章内容，仅维护链接元数据与分类映射关系，确保资源可追溯、可更新、可审计。

## 功能概览

**按源站聚合浏览**：根据文章所在源站域名对全部链接进行自动分组，便于用户了解各站点的内容侧重点与更新频率。

**按分类标签过滤**：每篇文章链接可关联一个或多个主题标签，如"架构设计""性能优化""安全审计""运维自动化"等，支持多标签组合筛选。

**批量链接健康检查**：内置链接可用性检测脚本，定时探测每条 URL 的 HTTP 状态码，自动标记失效链接并生成报告。

**元数据提取与缓存**：对每条链接执行轻量级 HTML 元数据抓取，提取标题、摘要、发布时间及正文前 200 字符，存入本地缓存以加速列表渲染。

**全文检索接口**：基于提取的标题与摘要内容提供简单的关键词检索能力，支持 AND/OR 组合查询及模糊匹配。

**导入导出机制**：支持通过 CSV 或 JSON 格式批量导入链接清单，亦可导出全量元数据用于二次开发或离线分析。

**访问统计看板**：记录每条链接的点击次数与最近访问时间，提供热门文章排行与沉寂文章提醒功能。

## 应用场景

技术团队内部知识库建设：团队可将本平台部署为内部知识导航页，将平时分散在各位成员浏览器书签中的优秀外链统一收录，新人入职时可快速了解团队关注的技术领域与推荐阅读清单。

技术文章选题与趋势分析：内容运营人员或技术编辑可通过定期导出链接清单并结合访问统计数据，识别近期高关注度话题，辅助制定内容产出计划。

个人技术阅读工作流优化：独立开发者或研究员可将本平台作为个人阅读列表的集中管理工具，按主题分类保存临时查阅到的文章，避免书签栏过度膨胀。

离线归档前哨站：在需要对特定源站内容进行合规归档前，先通过本平台完成链接普查与有效性验证，减少无效抓取操作。

## 快速开始

以下步骤适用于 Linux / macOS 及 Windows WSL 环境。项目基于 Python 3.10 开发，前端渲染采用静态模板引擎。

```bash
# 克隆仓库
git clone https://github.com/read-archives/read-aggregator.git
cd read-aggregator

# 创建并激活虚拟环境
python3 -m venv venv
source venv/bin/activate      # Linux/macOS
# venv\Scripts\activate       # Windows

# 安装核心依赖
pip install --upgrade pip
pip install -r requirements.txt

# 初始化本地数据库与缓存目录
python manage.py init --force

# 导入示例链接清单（含项目自带样例）
python manage.py import --source data/sample_links.json

# 启动本地开发服务器
python manage.py runserver --host 127.0.0.1 --port 8080
```

访问 http://127.0.0.1:8080 即可查看聚合首页。生产环境部署请参考文档导航章节中的部署指南。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10.x 或 3.11.x | 核心运行环境，低于 3.10 会导致类型注解解析错误 |
| SQLite | 3.35.0+ | 嵌入式数据库，用于存储链接元数据与统计信息 |
| requests | 2.31.0+ | 用于链接健康检查与 HTML 元数据提取 |
| beautifulsoup4 | 4.12.0+ | HTML 解析器，用于提取标题和摘要 |
| lxml | 4.9.0+ | 高性能 XML/HTML 解析后端，beautifulsoup4 的推荐解析器 |
| click | 8.1.0+ | 命令行交互框架，所有 manage.py 子命令均依赖此库 |
| jinja2 | 3.1.0+ | 模板引擎，负责生成静态列表页面 |
| markdown | 3.5.0+ | 用于渲染 README 及内嵌文档（仅开发依赖） |
| pytest | 7.4.0+ | 单元测试框架（仅测试环境依赖） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何浏览、搜索和导出链接；如何理解元数据字段含义 |
| 管理员手册 | docs/admin-guide.md | 如何配置定时健康检查；如何管理标签体系与分类映射 |
| 部署指南 | docs/deployment.md | 如何在生产环境使用 gunicorn + nginx 部署；如何配置 systemd 服务 |
| API 参考 | docs/api-reference.md | 检索接口与导入导出接口的请求/响应格式、状态码说明 |
| 开发指南 | docs/development.md | 如何扩展新的元数据提取器；如何编写自定义过滤器 |
| 数据模型 | docs/data-model.md | 数据库表结构、字段约束与迁移策略 |
| 故障排查 | docs/troubleshooting.md | 常见启动错误、链接检测超时调优、缓存重建步骤 |

## 资源列表

- https://www.read.cmcvrr.cn/Article/507953.shtml
- https://www.read.nwbbyt.cn/Article/936745.shtml
- https://www.read.fuvxie.cn/Article/36581.shtml
- https://www.read.hcbezg.cn/Article/29828.shtml
- https://www.read.hcbezg.cn/Article/900287.shtml
- https://www.read.nwbbyt.cn/Article/5994.shtml
- https://www.read.cmcvrr.cn/Article/2766559.shtml
- https://www.read.jnjpgf.cn/Article/94626.shtml
- https://www.read.cvsifc.cn/Article/765480.shtml
- https://www.read.nwbbyt.cn/Article/0686385.shtml
- https://www.read.puhvjy.cn/Article/509554.shtml
- https://www.read.nzfnve.cn/Article/9084.shtml
- https://www.read.jnjpgf.cn/Article/23355.shtml
- https://www.read.hcbezg.cn/Article/828240.shtml
- https://www.read.hcbezg.cn/Article/15695.shtml
- https://www.read.puhvjy.cn/Article/962775.shtml
- https://www.read.nwbbyt.cn/Article/728509.shtml
- https://www.read.nwbbyt.cn/Article/7398.shtml
- https://www.read.cmcvrr.cn/Article/0833.shtml
- https://www.read.puhvjy.cn/Article/139888.shtml
- https://www.read.nwbbyt.cn/Article/1964417.shtml
- https://www.read.cvsifc.cn/Article/465337.shtml
- https://www.read.cvsifc.cn/Article/40583.shtml
- https://www.read.fuvxie.cn/Article/3887034.shtml
- https://www.read.fuvxie.cn/Article/0259.shtml
- https://www.read.cvsifc.cn/Article/139530.shtml
- https://www.read.fuvxie.cn/Article/2607245.shtml
- https://www.read.fuvxie.cn/Article/49423.shtml
- https://www.read.nzfnve.cn/Article/456308.shtml
- https://www.read.fuvxie.cn/Article/514072.shtml
- https://www.read.cmcvrr.cn/Article/824525.shtml
- https://www.read.cvsifc.cn/Article/64939.shtml
- https://www.read.cmcvrr.cn/Article/81609.shtml
- https://www.read.cmcvrr.cn/Article/35511.shtml
- https://www.read.puhvjy.cn/Article/1573.shtml
- https://www.read.nwbbyt.cn/Article/86098.shtml
- https://www.read.puhvjy.cn/Article/9848.shtml
- https://www.read.puhvjy.cn/Article/54062.shtml
- https://www.read.cvsifc.cn/Article/9469507.shtml
- https://www.read.cvsifc.cn/Article/197246.shtml
- https://www.read.jnjpgf.cn/Article/08506.shtml
- https://www.read.hcbezg.cn/Article/25309.shtml
- https://www.read.cvsifc.cn/Article/562775.shtml
- https://www.read.fuvxie.cn/Article/41844.shtml
- https://www.read.puhvjy.cn/Article/2276087.shtml
- https://www.read.cmcvrr.cn/Article/5078.shtml
- https://www.read.nzfnve.cn/Article/4365.shtml
- https://www.read.nzfnve.cn/Article/2150.shtml
- https://www.read.nzfnve.cn/Article/9316.shtml
- https://www.read.cmcvrr.cn/Article/427922.shtml
- https://www.read.nwbbyt.cn/Article/147618.shtml
- https://www.read.cmcvrr.cn/Article/26649.shtml
- https://www.read.nzfnve.cn/Article/37328.shtml
- https://www.read.puhvjy.cn/Article/5589381.shtml
- https://www.read.jnjpgf.cn/Article/7335183.shtml
- https://www.read.hcbezg.cn/Article/3636.shtml
- https://www.read.nzfnve.cn/Article/055926.shtml
- https://www.read.cvsifc.cn/Article/8636148.shtml
- https://www.read.nzfnve.cn/Article/76260.shtml
- https://www.read.nwbbyt.cn/Article/663583.shtml
- https://www.read.hcbezg.cn/Article/5078494.shtml
- https://www.read.jnjpgf.cn/Article/318411.shtml
- https://www.read.nzfnve.cn/Article/3165.shtml
- https://www.read.fuvxie.cn/Article/7393414.shtml
- https://www.read.cvsifc.cn/Article/1639.shtml
- https://www.read.hcbezg.cn/Article/10756.shtml
- https://www.read.cvsifc.cn/Article/9504779.shtml
- https://www.read.nwbbyt.cn/Article/30862.shtml
- https://www.read.cmcvrr.cn/Article/5540072.shtml
- https://www.read.puhvjy.cn/Article/430835.shtml
- https://www.read.cmcvrr.cn/Article/98192.shtml
- https://www.read.fuvxie.cn/Article/72150.shtml
- https://www.read.puhvjy.cn/Article/55429.shtml
- https://www.read.hcbezg.cn/Article/499884.shtml
- https://www.read.cvsifc.cn/Article/197420.shtml
- https://www.read.cmcvrr.cn/Article/3057.shtml
- https://www.read.jnjpgf.cn/Article/7387.shtml
- https://www.read.nwbbyt.cn/Article/474224.shtml
- https://www.read.fuvxie.cn/Article/6472824.shtml
- https://www.read.jnjpgf.cn/Article/1930.shtml
- https://www.read.nzfnve.cn/Article/56962.shtml
- https://www.read.fuvxie.cn/Article/3045914.shtml
- https://www.read.nwbbyt.cn/Article/0025.shtml
- https://www.read.puhvjy.cn/Article/0275930.shtml
- https://www.read.nwbbyt.cn/Article/93366.shtml
- https://www.read.fuvxie.cn/Article/855803.shtml
- https://www.read.cvsifc.cn/Article/0376.shtml
- https://www.read.cvsifc.cn/Article/51843.shtml
- https://www.read.puhvjy.cn/Article/4386183.shtml
- https://www.read.jnjpgf.cn/Article/6757015.shtml
- https://www.read.cmcvrr.cn/Article/423649.shtml
- https://www.read.nzfnve.cn/Article/4563701.shtml
- https://www.read.jnjpgf.cn/Article/597983.shtml
- https://www.read.nwbbyt.cn/Article/3419.shtml
- https://www.read.hcbezg.cn/Article/367576.shtml
- https://www.read.cvsifc.cn/Article/128679.shtml
- https://www.read.puhvjy.cn/Article/1220047.shtml
- https://www.read.cvsifc.cn/Article/057948.shtml
- https://www.read.fuvxie.cn/Article/67591.shtml
- https://www.read.cmcvrr.cn/Article/769085.shtml
- https://www.read.puhvjy.cn/Article/85693.shtml
- https://www.read.fuvxie.cn/Article/7411974.shtml
- https://www.read.jnjpgf.cn/Article/7169722.shtml
- https://www.read.nzfnve.cn/Article/87099.shtml
- https://www.read.hcbezg.cn/Article/36250.shtml
- https://www.read.jnjpgf.cn/Article/3114173.shtml
- https://www.read.jnjpgf.cn/Article/1853001.shtml
- https://www.read.nzfnve.cn/Article/11130.shtml
- https://www.read.puhvjy.cn/Article/8930.shtml
- https://www.read.jnjpgf.cn/Article/0987.shtml
- https://www.read.jnjpgf.cn/Article/834292.shtml
- https://www.read.cvsifc.cn/Article/6793.shtml
- https://www.read.jnjpgf.cn/Article/982584.shtml
- https://www.read.cvsifc.cn/Article/948073.shtml
- https://www.read.nwbbyt.cn/Article/5220947.shtml
- https://www.read.cvsifc.cn/Article/357058.shtml
- https://www.read.nwbbyt.cn/Article/037351.shtml
- https://www.read.cvsifc.cn/Article/76257.shtml
- https://www.read.nzfnve.cn/Article/734031.shtml
- https://www.read.cmcvrr.cn/Article/9442.shtml
- https://www.read.nwbbyt.cn/Article/2873885.shtml
- https://www.read.jnjpgf.cn/Article/1343148.shtml
- https://www.read.fuvxie.cn/Article/674193.shtml
- https://www.read.nzfnve.cn/Article/109460.shtml
- https://www.read.nwbbyt.cn/Article/9418.shtml
- https://www.read.puhvjy.cn/Article/6028.shtml
- https://www.read.jnjpgf.cn/Article/7148407.shtml
- https://www.read.cvsifc.cn/Article/0826.shtml
- https://www.read.puhvjy.cn/Article/327739.shtml
- https://www.read.cmcvrr.cn/Article/3413455.shtml
- https://www.read.cvsifc.cn/Article/670570.shtml
- https://www.read.puhvjy.cn/Article/8827.shtml
- https://www.read.cvsifc.cn/Article/6847.shtml
- https://www.read.jnjpgf.cn/Article/607650.shtml
- https://www.read.cvsifc.cn/Article/5186030.shtml
- https://www.read.cmcvrr.cn/Article/112183.shtml
- https://www.read.puhvjy.cn/Article/8493024.shtml
- https://www.read.fuvxie.cn/Article/8237398.shtml
- https://www.read.cmcvrr.cn/Article/364633.shtml
- https://www.read.cvsifc.cn/Article/803262.shtml
- https://www.read.nwbbyt.cn/Article/6727.shtml
- https://www.read.jnjpgf.cn/Article/89192.shtml
- https://www.read.cvsifc.cn/Article/1926319.shtml
- https://www.read.puhvjy.cn/Article/643907.shtml
- https://www.read.fuvxie.cn/Article/3716.shtml
- https://www.read.cmcvrr.cn/Article/0683773.shtml
- https://www.read.hcbezg.cn/Article/965166.shtml
- https://www.read.cmcvrr.cn/Article/5382131.shtml
- https://www.read.fuvxie.cn/Article/26814.shtml
- https://www.read.hcbezg.cn/Article/9195.shtml
- https://www.read.cmcvrr.cn/Article/2951486.shtml
- https://www.read.nwbbyt.cn/Article/05040.shtml
- https://www.read.cvsifc.cn/Article/16748.shtml
- https://www.read.fuvxie.cn/Article/0199.shtml
- https://www.read.puhvjy.cn/Article/910519.shtml
- https://www.read.cmcvrr.cn/Article/8004432.shtml
- https://www.read.cmcvrr.cn/Article/2771293.shtml
- https://www.read.nzfnve.cn/Article/2788466.shtml
- https://www.read.nzfnve.cn/Article/2116.shtml
- https://www.read.cvsifc.cn/Article/672776.shtml
- https://www.read.nwbbyt.cn/Article/62428.shtml
- https://www.read.nwbbyt.cn/Article/93599.shtml
- https://www.read.puhvjy.cn/Article/7745091.shtml
- https://www.read.jnjpgf.cn/Article/170650.shtml
- https://www.read.puhvjy.cn/Article/5905.shtml
- https://www.read.hcbezg.cn/Article/5822.shtml
- https://www.read.cvsifc.cn/Article/093013.shtml
- https://www.read.cmcvrr.cn/Article/6487227.shtml
- https://www.read.nzfnve.cn/Article/7944.shtml
- https://www.read.cmcvrr.cn/Article/1605.shtml
- https://www.read.nwbbyt.cn/Article/86559.shtml
- https://www.read.jnjpgf.cn/Article/81105.shtml
- https://www.read.cmcvrr.cn/Article/8898286.shtml
- https://www.read.nwbbyt.cn/Article/5457356.shtml
- https://www.read.nwbbyt.cn/Article/10164.shtml
- https://www.read.cmcvrr.cn/Article/0837901.shtml
- https://www.read.jnjpgf.cn/Article/7870.shtml
- https://www.read.nzfnve.cn/Article/92865.shtml
- https://www.read.cvsifc.cn/Article/46240.shtml
- https://www.read.cvsifc.cn/Article/71069.shtml
- https://www.read.hcbezg.cn/Article/366688.shtml
- https://www.read.nzfnve.cn/Article/11210.shtml
- https://www.read.fuvxie.cn/Article/40444.shtml
- https://www.read.puhvjy.cn/Article/8068006.shtml
- https://www.read.cmcvrr.cn/Article/10189.shtml
- https://www.read.cvsifc.cn/Article/2304095.shtml
- https://www.read.nwbbyt.cn/Article/4184.shtml
- https://www.read.nwbbyt.cn/Article/685736.shtml
- https://www.read.jnjpgf.cn/Article/17555.shtml
- https://www.read.nwbbyt.cn/Article/0703.shtml
- https://www.read.hcbezg.cn/Article/3271711.shtml
- https://www.read.nzfnve.cn/Article/3712.shtml
- https://www.read.cvsifc.cn/Article/3292.shtml
- https://www.read.hcbezg.cn/Article/4263.shtml
- https://www.read.jnjpgf.cn/Article/8668925.shtml
- https://www.read.puhvjy.cn/Article/698006.shtml
- https://www.read.cmcvrr.cn/Article/61339.shtml
- https://www.read.puhvjy.cn/Article/908844.shtml
- https://www.read.puhvjy.cn/Article/390429.shtml
- https://www.read.cvsifc.cn/Article/6930184.shtml
- https://www.read.puhvjy.cn/Article/997122.shtml
- https://www.read.cmcvrr.cn/Article/0278.shtml
- https://www.read.nzfnve.cn/Article/0630.shtml
- https://www.read.puhvjy.cn/Article/804527.shtml
- https://www.read.nzfnve.cn/Article/3215565.shtml
- https://www.read.puhvjy.cn/Article/3294.shtml
- https://www.read.nzfnve.cn/Article/2152872.shtml
- https://www.read.cvsifc.cn/Article/17158.shtml
- https://www.read.cmcvrr.cn/Article/042330.shtml
- https://www.read.jnjpgf.cn/Article/935256.shtml
- https://www.read.puhvjy.cn/Article/4212188.shtml
- https://www.read.jnjpgf.cn/Article/0834871.shtml
- https://www.read.puhvjy.cn/Article/3864850.shtml
- https://www.read.jnjpgf.cn/Article/2908446.shtml
- https://www.read.hcbezg.cn/Article/669790.shtml
- https://www.read.nwbbyt.cn/Article/389261.shtml
- https://www.read.nwbbyt.cn/Article/78206.shtml
- https://www.read.jnjpgf.cn/Article/70299.shtml
- https://www.read.fuvxie.cn/Article/7303.shtml
- https://www.read.jnjpgf.cn/Article/8021932.shtml
- https://www.read.jnjpgf.cn/Article/9653.shtml
- https://www.read.hcbezg.cn/Article/535276.shtml
- https://www.read.hcbezg.cn/Article/3534523.shtml
- https://www.read.nzfnve.cn/Article/1008.shtml
- https://www.read.cvsifc.cn/Article/777522.shtml
- https://www.read.nzfnve.cn/Article/2705544.shtml
- https://www.read.nzfnve.cn/Article/7453766.shtml
- https://www.read.cvsifc.cn/Article/97673.shtml
- https://www.read.nwbbyt.cn/Article/73740.shtml
- https://www.read.cmcvrr.cn/Article/2542357.shtml
- https://www.read.cvsifc.cn/Article/693790.shtml
- https://www.read.cvsifc.cn/Article/50208.shtml
- https://www.read.nzfnve.cn/Article/5763.shtml
- https://www.read.hcbezg.cn/Article/3828425.shtml
- https://www.read.puhvjy.cn/Article/188369.shtml
- https://www.read.cvsifc.cn/Article/7755927.shtml
- https://www.read.nwbbyt.cn/Article/2448.shtml
- https://www.read.cmcvrr.cn/Article/02916.shtml
- https://www.read.jnjpgf.cn/Article/0396801.shtml
- https://www.read.cmcvrr.cn/Article/9604173.shtml
- https://www.read.cvsifc.cn/Article/5368842.shtml
- https://www.read.cmcvrr.cn/Article/0216.shtml
- https://www.read.jnjpgf.cn/Article/4320407.shtml
- https://www.read.fuvxie.cn/Article/3122340.shtml
- https://www.read.nzfnve.cn/Article/54507.shtml
- https://www.read.hcbezg.cn/Article/313747.shtml
- https://www.read.fuvxie.cn/Article/9955.shtml
- https://www.read.jnjpgf.cn/Article/3932432.shtml
- https://www.read.jnjpgf.cn/Article/1862331.shtml
- https://www.read.puhvjy.cn/Article/8413159.shtml

## 项目结构

```
read-aggregator/
├── manage.py                # 主 CLI 入口，聚合所有子命令
├── requirements.txt         # 生产环境依赖清单
├── pytest.ini               # 单元测试配置
├── .env.example             # 环境变量模板（数据库路径、超时阈值等）
├── data/                    # 数据目录
│   ├── sample_links.json    # 样例链接清单（用于快速演示）
│   ├── tags_mapping.yaml    # 标签与源站域名的映射规则
│   └── health_reports/      # 健康检查报告输出目录
├── src/                     # 核心源码
│   ├── __init__.py
│   ├── app.py               # WSGI 应用工厂与路由注册
│   ├── models.py            # SQLite 表定义与 ORM 封装（基于 sqlite3 原生）
│   ├── fetcher.py           # 链接抓取器：请求、超时重试、状态码判定
│   ├── parser.py            # HTML 元数据解析器：标题、摘要、发布时间提取
│   ├── indexer.py           # 检索引擎：倒排索引构建与查询匹配
│   ├── exporter.py          # 导出器：CSV / JSON 格式序列化
│   └── utils.py             # 通用工具函数（日期格式化、URL 规范化）
├── tests/                   # 单元测试与集成测试
│   ├── test_models.py       # 数据模型增删改查测试
│   ├── test_fetcher.py      # 抓取器模拟响应测试（含 mock）
│   ├── test_parser.py       # 各类畸形 HTML 解析容错测试
│   └── test_indexer.py      # 检索召回率与排序正确性测试
├── templates/               # Jinja2 模板
│   ├── base.html            # 基础布局模板
│   ├── index.html           # 首页列表（含分页与过滤控件）
│   ├── detail.html          # 单条链接详情页
│   └── stats.html           # 统计看板（点击排行与健康状态）
├── static/                  # 前端静态资源
│   ├── css/
│   │   └── style.css        # 响应式栅格与暗色主题变量
│   └── js/
│       └── filter.js        # 前端标签过滤与即时搜索交互逻辑
├── docs/                    # 完整文档目录（对应文档导航章节）
└── scripts/                 # 运维辅助脚本
    ├── health_check_cron.py # 定时健康检查入口（供 crontab 调用）
    └── migrate_db.py        # 数据库版本迁移脚本
```

## 贡献指南

欢迎提交问题报告、功能建议与代码变更。请遵循以下流程以保持项目整洁与可维护性。

1. 查阅现有 Issue 与 Pull Request：在提交新需求或修复前，请先检索 GitHub Issues 与 Pull Requests 列表，确认无人正在处理相同问题。若存在关联议题，请在该议题下留言表达参与意愿。

2. 派生仓库并创建特性分支：从主仓库派生（Fork）至个人账户，然后基于 main 分支创建新分支，分支命名采用 `feature/简述` 或 `fix/简述` 格式，例如 `feature/add-timeout-config`。

3. 编写测试与代码：所有新增功能或缺陷修复必须附带对应的单元测试，测试覆盖率不得低于现有基线。代码风格遵循 PEP 8，提交前请运行 `make lint` 或 `pylint src/` 进行静态检查。

4. 提交变更并签署开发者原产地证书：每个提交信息应清晰描述变更内容与动机，正文可引用关联 Issue 编号。提交时需签署 DCO（Developer Certificate of Origin），即通过 `git commit -s` 添加 Signed-off-by 尾注。

5. 发起拉取请求并等待审查：将特性分支推送至派生仓库后，向主仓库的 main 分支发起 Pull Request。PR 描述需包含变更摘要、测试结果及任何破坏性变更说明。至少一名维护者审查通过后方可合并。

## 常见问题

**问：导入大量链接时出现超时或内存不足错误，应如何优化？**

答：批量导入时默认每批次处理 500 条记录，可通过 `--batch-size` 参数调小该数值，例如 `python manage.py import --source data/links.json --batch-size 100`。同时建议在生产环境使用 PostgreSQL 替代 SQLite 以提升写入并发能力，具体配置方法见 docs/deployment.md 中的数据库切换章节。

**问：部分链接的元数据提取结果为空或不准确，如何排查？**

答：首先确认目标站点是否要求特定的 User-Agent 或 Cookie。可在 `.env` 文件中设置 `FETCHER_USER_AGENT` 为常用浏览器标识，或启用 `FETCHER_ALLOW_REDIRECT` 跟踪重定向。若仍无效，可使用 `python manage.py inspect --url <目标链接>` 命令单独测试提取过程，输出将显示 HTTP 响应头与解析后的 DOM 片段，便于定位选择器失效原因。若站点使用 JavaScript 动态渲染内容，本项目的轻量级解析器无法支持，建议改用 Puppeteer 或 Playwright 进行预渲染，扩展方案参考 docs/development.md。

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

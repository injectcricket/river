# DocLink 聚合索引系统 (DLIS)

DocLink 聚合索引系统是一个面向技术文档、研究报告与操作手册的轻量级外链资源归集平台。项目定位于为运维工程师、技术写作者、知识管理专员以及研发团队提供一套可私有化部署的文档外链元数据登记、分类、检索与访问状态监控的工具链。该系统不存储文档实体内容，仅维护文档的网络地址、来源域名、文件类型及基础元信息，通过结构化索引机制帮助团队高效管理散落在多个移动端域名下的 .doc 资源，解决文档地址分散、链接失效不可知、分类混乱等实际问题。

目标用户包括企业知识库管理员、技术文档维护团队、学术研究辅助人员以及需要批量整理和校验大量文档外链的自动化运维场景。项目以命令行工具与轻量级 Web 看板双形态运行，支持外链批量导入、有效性巡检、域名维度分组统计以及基础的前端检索过滤功能。

## 功能概览

批量外链导入解析 支持以纯文本列表或 CSV 格式批量导入文档外链，自动解析 URL 结构，提取域名、文件路径及文件名后缀，生成内部资源编号。

文档状态周期性巡检 内置基于 HTTP HEAD 请求的链接可用性检查器，可配置定时任务，自动标记失效链接并生成巡检报告，帮助运维人员快速定位不可访问的文档资源。

多维度分类与标签系统 允许用户为每条外链附加自定义标签（如 "操作手册"、"API 设计"、"故障排查"、"季度报告"），并支持按域名、文件大小范围、最后检测时间等条件进行组合筛选。

轻量级 Web 查询看板 提供一个只读的 Web 前端页面，支持按域名、关键词（文件名或路径片段）进行模糊搜索，并以表格形式展示资源列表，包含域名、路径、最近检测状态、检测时间等字段。

RESTful 管理 API 暴露标准 JSON API，支持资源的增删改查、状态检测触发、标签更新等操作，方便与其他内部自动化系统（如监控平台、文档发布流水线）集成。

本地 SQLite 数据持久化 使用 SQLite 作为默认元数据存储引擎，无需额外数据库服务，单文件数据库便于备份与迁移，同时支持导出为 JSON 或 CSV 格式用于离线分析。

扩展脚本支持 提供 Python 脚本钩子，允许用户在检测前或检测后执行自定义逻辑（如发送告警邮件、调用第三方消息推送接口），增强系统可扩展性。

## 应用场景

企业知识库死链巡检与修复 大型企业内部的知识库系统中常包含大量引自不同移动端域名的文档链接。随着时间推移，部分源站可能会调整目录结构或下线旧文档。DocLink 系统可定期对所有登记的外链执行可用性探测，自动生成死链报告，辅助知识库管理员精准定位失效链接并进行修复或替换。

技术文档版本发布前的链接校验 技术文档团队在发布新版本手册前，需要确认所有引用到的外部文档（如设计规范、接口协议、历史会议记录）均处于可访问状态。通过将引用地址导入系统并触发一次全量检测，团队可在发布窗口前获得链接健康度评估，避免手册中出现无效引用。

学术研究参考文献的批量元数据管理 研究助理在整理大量参考文献或数据集说明文档时，可借助本系统统一登记文档外链来源，并按研究课题或项目阶段进行标签分类。后续需要复查某类资源时，可通过 Web 看板快速检索并导出资源清单。

跨团队文档依赖关系梳理 在微服务架构或大型项目开发中，不同团队分别维护各自的文档站点。运维或架构师可使用 DocLink 建立全局文档依赖视图，分析各服务文档的引用关系与分布情况，识别高频引用的核心文档和孤岛文档。

## 快速开始

以下步骤帮助您在本地环境快速启动 DocLink 聚合索引系统。

```bash
# 1. 克隆代码仓库
git clone https://github.com/your-org/doclink-index-system.git
cd doclink-index-system

# 2. 创建并激活 Python 虚拟环境（推荐）
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate

# 3. 安装项目依赖
pip install -r requirements.txt

# 4. 初始化 SQLite 数据库及基础表结构
python manage.py init-db

# 5. 导入示例资源列表（或替换为实际外链列表文件）
python manage.py import-links --file samples/links.txt

# 6. 启动 Web 看板服务（默认监听 8080 端口）
python manage.py runserver --port 8080
```

完成上述步骤后，在浏览器中访问 `http://127.0.0.1:8080` 即可查看已导入的文档外链列表。如需执行状态检测，可运行以下命令：

```bash
# 手动触发全部链接的状态检测（仅检测，不修改数据库以外的资源）
python manage.py check-links --timeout 5 --concurrency 10
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 或 3.11 版本以获得更好性能 |
| SQLite3 | 3.31.0 及以上 | 内置于 Python 标准库，但需确保系统 SQLite 支持外键约束及 JSON 函数 |
| requests | 2.28.0 及以上 | 用于发送 HTTP 请求进行链接可用性检测，支持超时及重试配置 |
| click | 8.1.0 及以上 | 命令行交互框架，用于定义和管理子命令（import、check、runserver） |
| flask | 2.2.0 及以上 | 轻量级 Web 框架，用于提供查询看板及 RESTful API 接口 |
| python-dotenv | 1.0.0 及以上 | 用于从 .env 文件中读取环境变量，如数据库路径、检测超时阈值等 |
| pytest | 7.2.0 及以上 | 仅开发与测试时需要，用于执行单元测试与集成测试用例 |
| black | 22.3.0 及以上 | 仅开发时需要，用于代码格式化，保持代码风格一致 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide.md | 如何导入外链、如何执行检测、如何使用 Web 看板进行检索与过滤 |
| 管理员指南 | docs/admin-guide.md | 如何配置定时巡检任务、如何备份与恢复 SQLite 数据库、如何调整并发检测参数 |
| API 参考 | docs/api-reference.md | RESTful API 各端点的请求方法、路径参数、请求体格式及响应数据结构 |
| 开发指南 | docs/developer-guide.md | 项目整体架构设计、新增检测协议（如 FTP/HTTPS）的扩展方式、贡献代码流程 |
| 部署示例 | docs/deployment-examples.md | 使用 systemd 部署为常驻服务、使用 Docker 容器化运行、与 Prometheus 集成监控的配置片段 |
| 常见问题 | docs/faq.md | 检测结果出现 SSL 证书错误如何忽略、导入大量链接时内存占用过高的优化建议、Web 看板无法显示最新检测结果的处理方法 |

## 资源列表

- h5.mobile.cmcvrr.cn/Article/2809.doc
- h5.mobile.hcbezg.cn/Article/75969.doc
- h5.mobile.nzfnve.cn/Article/851417.doc
- h5.mobile.fuvxie.cn/Article/3586086.doc
- h5.mobile.nzfnve.cn/Article/266439.doc
- h5.mobile.hcbezg.cn/Article/193484.doc
- h5.mobile.puhvjy.cn/Article/2311668.doc
- h5.mobile.nzfnve.cn/Article/88107.doc
- h5.mobile.jnjpgf.cn/Article/3406316.doc
- h5.mobile.jnjpgf.cn/Article/1054258.doc
- h5.mobile.cvsifc.cn/Article/2053.doc
- h5.mobile.nwbbyt.cn/Article/6803961.doc
- h5.mobile.nzfnve.cn/Article/9894.doc
- h5.mobile.cvsifc.cn/Article/8413412.doc
- h5.mobile.fuvxie.cn/Article/6792546.doc
- h5.mobile.cmcvrr.cn/Article/51588.doc
- h5.mobile.fuvxie.cn/Article/80380.doc
- h5.mobile.nwbbyt.cn/Article/439968.doc
- h5.mobile.fuvxie.cn/Article/6168077.doc
- h5.mobile.jnjpgf.cn/Article/7391052.doc
- h5.mobile.nwbbyt.cn/Article/2167.doc
- h5.mobile.hcbezg.cn/Article/28371.doc
- h5.mobile.cvsifc.cn/Article/3032935.doc
- h5.mobile.nzfnve.cn/Article/54284.doc
- h5.mobile.jnjpgf.cn/Article/61603.doc
- h5.mobile.hcbezg.cn/Article/00110.doc
- h5.mobile.fuvxie.cn/Article/74968.doc
- h5.mobile.fuvxie.cn/Article/53717.doc
- h5.mobile.fuvxie.cn/Article/656082.doc
- h5.mobile.fuvxie.cn/Article/30727.doc
- h5.mobile.nzfnve.cn/Article/0015432.doc
- h5.mobile.nzfnve.cn/Article/2488.doc
- h5.mobile.hcbezg.cn/Article/63428.doc
- h5.mobile.cmcvrr.cn/Article/010911.doc
- h5.mobile.fuvxie.cn/Article/8931.doc
- h5.mobile.jnjpgf.cn/Article/3546954.doc
- h5.mobile.cmcvrr.cn/Article/42124.doc
- h5.mobile.cmcvrr.cn/Article/49361.doc
- h5.mobile.jnjpgf.cn/Article/36043.doc
- h5.mobile.jnjpgf.cn/Article/90775.doc
- h5.mobile.hcbezg.cn/Article/9348950.doc
- h5.mobile.jnjpgf.cn/Article/5272064.doc
- h5.mobile.jnjpgf.cn/Article/49517.doc
- h5.mobile.cvsifc.cn/Article/61398.doc
- h5.mobile.cvsifc.cn/Article/3407114.doc
- h5.mobile.cvsifc.cn/Article/9582636.doc
- h5.mobile.puhvjy.cn/Article/972126.doc
- h5.mobile.nzfnve.cn/Article/4143775.doc
- h5.mobile.jnjpgf.cn/Article/61150.doc
- h5.mobile.cvsifc.cn/Article/32356.doc
- h5.mobile.puhvjy.cn/Article/49853.doc
- h5.mobile.puhvjy.cn/Article/9310452.doc
- h5.mobile.cvsifc.cn/Article/86745.doc
- h5.mobile.fuvxie.cn/Article/10827.doc
- h5.mobile.nwbbyt.cn/Article/7845.doc
- h5.mobile.puhvjy.cn/Article/7117.doc
- h5.mobile.fuvxie.cn/Article/87503.doc
- h5.mobile.jnjpgf.cn/Article/11237.doc
- h5.mobile.fuvxie.cn/Article/141307.doc
- h5.mobile.nzfnve.cn/Article/3460645.doc
- h5.mobile.nzfnve.cn/Article/893385.doc
- h5.mobile.puhvjy.cn/Article/22100.doc
- h5.mobile.cvsifc.cn/Article/07354.doc
- h5.mobile.cmcvrr.cn/Article/76721.doc
- h5.mobile.hcbezg.cn/Article/5550.doc
- h5.mobile.cvsifc.cn/Article/11799.doc
- h5.mobile.cmcvrr.cn/Article/0938.doc
- h5.mobile.cvsifc.cn/Article/52866.doc
- h5.mobile.cvsifc.cn/Article/32342.doc
- h5.mobile.fuvxie.cn/Article/0880.doc
- h5.mobile.cvsifc.cn/Article/6182.doc
- h5.mobile.jnjpgf.cn/Article/427476.doc
- h5.mobile.cvsifc.cn/Article/126275.doc
- h5.mobile.jnjpgf.cn/Article/49819.doc
- h5.mobile.hcbezg.cn/Article/24377.doc
- h5.mobile.jnjpgf.cn/Article/7910.doc
- h5.mobile.puhvjy.cn/Article/7805.doc
- h5.mobile.hcbezg.cn/Article/34020.doc
- h5.mobile.puhvjy.cn/Article/6515.doc
- h5.mobile.hcbezg.cn/Article/5479470.doc
- h5.mobile.cvsifc.cn/Article/63909.doc
- h5.mobile.nzfnve.cn/Article/761097.doc
- h5.mobile.nzfnve.cn/Article/1146.doc
- h5.mobile.hcbezg.cn/Article/88716.doc
- h5.mobile.nzfnve.cn/Article/119768.doc
- h5.mobile.cvsifc.cn/Article/86536.doc
- h5.mobile.puhvjy.cn/Article/9429.doc
- h5.mobile.nwbbyt.cn/Article/096333.doc
- h5.mobile.nzfnve.cn/Article/43298.doc
- h5.mobile.puhvjy.cn/Article/0142669.doc
- h5.mobile.cmcvrr.cn/Article/274407.doc
- h5.mobile.cmcvrr.cn/Article/6991.doc
- h5.mobile.puhvjy.cn/Article/1948061.doc
- h5.mobile.fuvxie.cn/Article/1825.doc
- h5.mobile.nzfnve.cn/Article/199282.doc
- h5.mobile.jnjpgf.cn/Article/778831.doc
- h5.mobile.nwbbyt.cn/Article/35479.doc
- h5.mobile.cvsifc.cn/Article/1583.doc
- h5.mobile.cmcvrr.cn/Article/362443.doc
- h5.mobile.cvsifc.cn/Article/422723.doc
- h5.mobile.cmcvrr.cn/Article/5025711.doc
- h5.mobile.nzfnve.cn/Article/3228.doc
- h5.mobile.cvsifc.cn/Article/934637.doc
- h5.mobile.cvsifc.cn/Article/877880.doc
- h5.mobile.nzfnve.cn/Article/05721.doc
- h5.mobile.puhvjy.cn/Article/441429.doc
- h5.mobile.fuvxie.cn/Article/1639078.doc
- h5.mobile.nwbbyt.cn/Article/5406316.doc
- h5.mobile.fuvxie.cn/Article/46877.doc
- h5.mobile.nwbbyt.cn/Article/4742208.doc
- h5.mobile.puhvjy.cn/Article/94994.doc
- h5.mobile.hcbezg.cn/Article/93811.doc
- h5.mobile.hcbezg.cn/Article/8834986.doc
- h5.mobile.nwbbyt.cn/Article/5797006.doc
- h5.mobile.nwbbyt.cn/Article/16616.doc
- h5.mobile.cvsifc.cn/Article/3937815.doc
- h5.mobile.cmcvrr.cn/Article/8583.doc
- h5.mobile.nwbbyt.cn/Article/1981174.doc
- h5.mobile.jnjpgf.cn/Article/93941.doc
- h5.mobile.nwbbyt.cn/Article/1033952.doc
- h5.mobile.hcbezg.cn/Article/9757.doc
- h5.mobile.fuvxie.cn/Article/061060.doc
- h5.mobile.nzfnve.cn/Article/29893.doc
- h5.mobile.nwbbyt.cn/Article/00257.doc
- h5.mobile.jnjpgf.cn/Article/6068.doc
- h5.mobile.hcbezg.cn/Article/7134290.doc
- h5.mobile.fuvxie.cn/Article/6594.doc
- h5.mobile.cmcvrr.cn/Article/896605.doc
- h5.mobile.nzfnve.cn/Article/8136129.doc
- h5.mobile.hcbezg.cn/Article/5787.doc
- h5.mobile.nwbbyt.cn/Article/07353.doc
- h5.mobile.nzfnve.cn/Article/0829.doc
- h5.mobile.hcbezg.cn/Article/5237.doc
- h5.mobile.nzfnve.cn/Article/1514.doc
- h5.mobile.cmcvrr.cn/Article/1561.doc
- h5.mobile.nwbbyt.cn/Article/88121.doc
- h5.mobile.nzfnve.cn/Article/9063838.doc
- h5.mobile.nzfnve.cn/Article/1709.doc
- h5.mobile.nwbbyt.cn/Article/14705.doc
- h5.mobile.nzfnve.cn/Article/0888127.doc
- h5.mobile.cvsifc.cn/Article/9389.doc
- h5.mobile.nzfnve.cn/Article/91897.doc
- h5.mobile.jnjpgf.cn/Article/4176797.doc
- h5.mobile.puhvjy.cn/Article/39688.doc
- h5.mobile.jnjpgf.cn/Article/6943356.doc
- h5.mobile.puhvjy.cn/Article/65302.doc
- h5.mobile.cmcvrr.cn/Article/8478.doc
- h5.mobile.hcbezg.cn/Article/74054.doc
- h5.mobile.nwbbyt.cn/Article/8253426.doc
- h5.mobile.jnjpgf.cn/Article/213050.doc
- h5.mobile.fuvxie.cn/Article/7004.doc
- h5.mobile.fuvxie.cn/Article/6841050.doc
- h5.mobile.cvsifc.cn/Article/13468.doc
- h5.mobile.fuvxie.cn/Article/5772376.doc
- h5.mobile.puhvjy.cn/Article/150795.doc
- h5.mobile.hcbezg.cn/Article/58907.doc
- h5.mobile.nwbbyt.cn/Article/4200.doc
- h5.mobile.nwbbyt.cn/Article/991917.doc
- h5.mobile.jnjpgf.cn/Article/451348.doc
- h5.mobile.jnjpgf.cn/Article/1582.doc
- h5.mobile.fuvxie.cn/Article/77657.doc
- h5.mobile.fuvxie.cn/Article/013226.doc
- h5.mobile.hcbezg.cn/Article/96838.doc
- h5.mobile.fuvxie.cn/Article/54578.doc
- h5.mobile.jnjpgf.cn/Article/3119.doc
- h5.mobile.jnjpgf.cn/Article/1583.doc
- h5.mobile.nwbbyt.cn/Article/029633.doc
- h5.mobile.cmcvrr.cn/Article/5270.doc
- h5.mobile.jnjpgf.cn/Article/373700.doc
- h5.mobile.nwbbyt.cn/Article/3473710.doc
- h5.mobile.cvsifc.cn/Article/6584.doc
- h5.mobile.hcbezg.cn/Article/33501.doc
- h5.mobile.nwbbyt.cn/Article/6337170.doc
- h5.mobile.hcbezg.cn/Article/5441.doc
- h5.mobile.cvsifc.cn/Article/1895775.doc
- h5.mobile.nzfnve.cn/Article/9798537.doc
- h5.mobile.nwbbyt.cn/Article/6494394.doc
- h5.mobile.nzfnve.cn/Article/9900294.doc
- h5.mobile.fuvxie.cn/Article/4037157.doc
- h5.mobile.puhvjy.cn/Article/74162.doc
- h5.mobile.fuvxie.cn/Article/71362.doc
- h5.mobile.hcbezg.cn/Article/64907.doc
- h5.mobile.fuvxie.cn/Article/1085973.doc
- h5.mobile.fuvxie.cn/Article/9349.doc
- h5.mobile.jnjpgf.cn/Article/52835.doc
- h5.mobile.nwbbyt.cn/Article/860245.doc
- h5.mobile.fuvxie.cn/Article/45184.doc
- h5.mobile.hcbezg.cn/Article/224320.doc
- h5.mobile.nwbbyt.cn/Article/4959000.doc
- h5.mobile.cvsifc.cn/Article/719990.doc
- h5.mobile.hcbezg.cn/Article/6430263.doc
- h5.mobile.hcbezg.cn/Article/1376.doc
- h5.mobile.fuvxie.cn/Article/240236.doc
- h5.mobile.jnjpgf.cn/Article/3855332.doc
- h5.mobile.cmcvrr.cn/Article/53919.doc
- h5.mobile.fuvxie.cn/Article/2726172.doc
- h5.mobile.jnjpgf.cn/Article/82714.doc
- h5.mobile.puhvjy.cn/Article/6528643.doc
- h5.mobile.hcbezg.cn/Article/580397.doc
- h5.mobile.jnjpgf.cn/Article/83416.doc
- h5.mobile.nwbbyt.cn/Article/0875918.doc
- h5.mobile.puhvjy.cn/Article/196430.doc
- h5.mobile.hcbezg.cn/Article/36112.doc
- h5.mobile.nwbbyt.cn/Article/248699.doc
- h5.mobile.puhvjy.cn/Article/7159551.doc
- h5.mobile.cvsifc.cn/Article/8886243.doc
- h5.mobile.puhvjy.cn/Article/7560101.doc
- h5.mobile.jnjpgf.cn/Article/73912.doc
- h5.mobile.jnjpgf.cn/Article/8831840.doc
- h5.mobile.jnjpgf.cn/Article/223787.doc
- h5.mobile.nzfnve.cn/Article/0108777.doc
- h5.mobile.fuvxie.cn/Article/82753.doc
- h5.mobile.jnjpgf.cn/Article/61495.doc
- h5.mobile.puhvjy.cn/Article/47769.doc
- h5.mobile.puhvjy.cn/Article/8786.doc
- h5.mobile.nzfnve.cn/Article/59153.doc
- h5.mobile.puhvjy.cn/Article/5289.doc
- h5.mobile.hcbezg.cn/Article/7041.doc
- h5.mobile.hcbezg.cn/Article/334549.doc
- h5.mobile.nwbbyt.cn/Article/2671.doc
- h5.mobile.nzfnve.cn/Article/798601.doc
- h5.mobile.hcbezg.cn/Article/7229.doc
- h5.mobile.cmcvrr.cn/Article/4687064.doc
- h5.mobile.nwbbyt.cn/Article/711241.doc
- h5.mobile.nwbbyt.cn/Article/1544883.doc
- h5.mobile.hcbezg.cn/Article/5144569.doc
- h5.mobile.jnjpgf.cn/Article/8048.doc
- h5.mobile.fuvxie.cn/Article/4288.doc
- h5.mobile.nzfnve.cn/Article/34106.doc
- h5.mobile.nzfnve.cn/Article/47109.doc
- h5.mobile.nwbbyt.cn/Article/974455.doc
- h5.mobile.nzfnve.cn/Article/1086.doc
- h5.mobile.cmcvrr.cn/Article/9078.doc
- h5.mobile.cvsifc.cn/Article/5172.doc
- h5.mobile.puhvjy.cn/Article/611323.doc
- h5.mobile.nzfnve.cn/Article/066127.doc
- h5.mobile.hcbezg.cn/Article/67577.doc
- h5.mobile.nwbbyt.cn/Article/31628.doc
- h5.mobile.cvsifc.cn/Article/9461824.doc
- h5.mobile.cmcvrr.cn/Article/1897.doc
- h5.mobile.nwbbyt.cn/Article/14028.doc
- h5.mobile.puhvjy.cn/Article/282447.doc
- h5.mobile.puhvjy.cn/Article/80979.doc
- h5.mobile.hcbezg.cn/Article/877992.doc
- h5.mobile.nwbbyt.cn/Article/595173.doc
- h5.mobile.cmcvrr.cn/Article/614036.doc
- h5.mobile.puhvjy.cn/Article/01291.doc
- h5.mobile.cmcvrr.cn/Article/28776.doc
- h5.mobile.fuvxie.cn/Article/0946.doc
- h5.mobile.nwbbyt.cn/Article/86503.doc

## 项目结构

```
doclink-index-system/
├── manage.py                      # 项目主入口，注册所有 CLI 子命令（init-db、import-links、check-links、runserver）
├── requirements.txt               # Python 依赖列表（包含 Flask、requests、click、python-dotenv 等）
├── .env.example                   # 环境变量配置模板，含 DATABASE_PATH、CHECK_TIMEOUT、CONCURRENCY 等
├── doclink/
│   ├── __init__.py                # 包初始化，定义全局配置对象及版本号
│   ├── config.py                  # 配置加载模块，从环境变量或默认值读取运行参数
│   ├── database/
│   │   ├── __init__.py            # 数据库连接与游标工厂，提供单例连接池
│   │   ├── schema.sql             # SQLite 建表语句（resources、tags、check_logs 等）
│   │   └── operations.py          # 资源增删改查、标签关联、检测记录写入等原子操作函数
│   ├── checker/
│   │   ├── __init__.py            # 检测器入口，暴露 run_check 函数
│   │   ├── http_client.py         # 封装 requests.Session，配置超时、重试策略及 User-Agent
│   │   └── reporter.py            # 检测结果汇总与报告生成（控制台表格 / JSON 输出）
│   ├── web/
│   │   ├── __init__.py            # Flask 应用工厂函数
│   │   ├── routes/
│   │   │   ├── __init__.py        # 蓝图注册，统一前缀 /api/v1
│   │   │   ├── resources.py       # 资源列表查询、搜索、详情接口
│   │   │   └── stats.py           # 域名分布统计、状态占比统计接口
│   │   └── templates/
│   │       └── index.html         # Web 看板主页面，含搜索框、结果表格和状态标记样式
│   ├── importer/
│   │   ├── __init__.py            # 导入器入口，支持 txt / csv 格式自动识别
│   │   └── parser.py              # URL 解析与去重逻辑，提取域名、路径、文件名
│   └── utils/
│       ├── __init__.py            # 通用工具函数（时间格式化、字符串处理）
│       └── validators.py          # URL 格式校验、文件扩展名白名单校验
├── tests/
│   ├── __init__.py                # 测试包标识
│   ├── test_database.py           # 数据库操作单元测试（使用临时内存数据库）
│   ├── test_checker.py            # 检测器模拟响应测试（使用 unittest.mock）
│   └── test_importer.py           # 导入器解析逻辑测试，覆盖正常及异常输入
├── samples/
│   └── links.txt                  # 示例外链列表文件，供快速导入演示使用
└── docs/
    ├── user-guide.md              # 用户手册，详细说明各子命令用法与 Web 界面操作
    ├── admin-guide.md             # 管理员手册，涵盖定时任务配置与数据库维护
    ├── api-reference.md           # API 文档，包含请求示例与响应字段说明
    ├── developer-guide.md         # 开发者指南，包含设计决策与扩展点说明
    └── deployment-examples.md     # 部署示例（systemd 单元文件、Dockerfile 片段）
```

## 贡献指南

贡献前请先阅读项目行为准则与开发指南。所有贡献均需通过 GitHub Pull Request 流程提交，并确保代码风格与现有代码保持一致。

1. 在 GitHub 上 fork 本仓库，并 clone 到本地开发环境。创建新的功能分支，分支命名采用 `feature/xxx` 或 `fix/xxx` 格式，其中 xxx 为简短的英文描述，如 `feature/support-ftp-check`。

2. 编写或修改代码后，请确保所有现有单元测试通过，并为新增功能或修复缺陷补充对应的测试用例。运行 `pytest tests/` 执行完整测试套件。

3. 代码格式化使用 black，行宽限制为 100 字符。提交前运行 `black doclink/ tests/` 进行自动格式化，并使用 `flake8 doclink/` 检查是否引入新的 lint 警告。

4. 更新相关文档，包括但不限于用户手册、API 参考或部署示例中受影响的章节。若修改了 CLI 命令行为，需同步更新 `--help` 输出中的描述信息。

5. 提交 Pull Request 至主仓库的 main 分支，并在 PR 描述中清晰说明改动目的、测试覆盖情况以及是否涉及破坏性变更。PR 需要至少一名项目维护者审核通过后方可合并。

## 常见问题

**Q：检测链接时出现大量 SSL 证书验证失败错误，如何处理？**

A：部分文档源站可能使用了自签名证书或证书已过期。您可以在执行检测时通过环境变量 `CHECK_VERIFY_SSL=false` 关闭 SSL 验证（仅适用于内网或可信环境）。也可以编辑 `doclink/checker/http_client.py` 中的 `verify` 参数为 `False`，但出于安全考虑，不推荐在生产环境中全局禁用。

**Q：导入包含大量外链（超过 500 条）的文本文件时，系统响应缓慢或内存占用过高，如何优化？**

A：导入操作默认一次性读取所有行并解析。对于大型文件，建议使用 `--chunk-size` 参数（例如 `--chunk-size 100`）分批提交事务，避免单次事务过大导致内存积压。此外，SQLite 的 `synchronous=OFF` 和 `journal_mode=WAL` 配置可显著提升写入吞吐量，详细调优参数请参考管理员指南。

**Q：Web 看板中显示的检测状态与手动使用 curl 访问的结果不一致，如何排查？**

A：可能存在以下原因：检测器默认超时时间为 5 秒，若源站响应较慢可能被判定为超时；检测器默认跟随重定向（最多 5 次），但不会处理 JavaScript 渲染的页面；部分源站可能根据 User-Agent 返回不同内容，检测器默认使用 `DocLinkChecker/1.0` 标识。您可以在 `.env` 文件中调整 `CHECK_TIMEOUT` 与 `CHECK_USER_AGENT` 变量，并检查 `logs/check.log` 中的详细请求与响应信息。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

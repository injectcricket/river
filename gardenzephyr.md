# DocHub Mobile Archive

DocHub Mobile Archive 是一个面向移动端文档资源聚合与分发的基础设施项目，专注于对分散在不同源站的技术文档、行业报告、操作手册等 .doc 格式文件进行统一索引、分类归档与快速检索。项目本身不存储任何实体文件，而是通过结构化的链接聚合层，为开发者、研究人员及内容消费者提供稳定、可扩展的文档导航服务。

本项目定位为技术资源外链汇总站，适用于需要批量管理、审核、分发外部文档链接的团队或平台。通过标准化的链接格式与目录结构，DocHub Mobile Archive 能够与自动化爬虫、链接可用性检测服务、文档元数据抽取工具等形成完整工具链，显著降低文档资源分散带来的管理成本。

## 功能概览

批量链接导入与自动规范化：支持以纯文本或结构化数据格式批量导入文档链接，自动识别链接格式并生成标准化的索引记录。

多源文档分类聚合：基于链接域名与路径特征，自动将文档按源站归属进行分组，形成清晰的文档来源视图。

链接可用性周期性检测：内置链接探活机制，可配置周期对已收录链接进行 HTTP 状态检测，标记失效或重定向链接。

文档元数据抽取：从链接路径中解析文档编号、来源域名等关键字段，为后续检索与过滤提供结构化数据支撑。

自定义标签与注解系统：允许为每条链接添加自定义标签、备注说明及重要性等级，便于团队内部协作与审核。

只读镜像访问模式：提供基于哈希校验的只读访问接口，确保外部系统引用链接时不会误修改原始索引数据。

全量链接清单导出：支持将当前索引库中的全部链接按指定格式导出，便于离线备份或迁移至其他平台。

## 应用场景

企业文档库迁移与整合：当企业将分散在多个旧系统的操作手册、制度文件迁移至统一知识库时，可使用 DocHub Mobile Archive 先行建立链接索引，再逐步完成内容迁移与校验。

技术社区资源导航站：技术社区或开源项目文档站可利用本项目聚合官方文档、社区教程、最佳实践等外部 .doc 资源，为社区成员提供一站式的文档入口。

学术研究文献辅助管理：研究团队在搜集行业报告、会议论文等材料时，可通过本项目统一记录文献链接，并利用标签系统进行分类，提升文献管理效率。

内容审核与合规审查流水线：内容审核团队可将待审核文档链接录入系统，结合外部审核工具逐条检查链接内容合规性，形成完整的审核记录链路。

自动化文档同步任务前置：在构建从外部源站到内部存储的文档同步流水线时，可将本项目作为链接源，由同步任务定期拉取链接列表并执行下载与归档。

## 快速开始

以下命令演示了如何获取项目源码、安装依赖并启动基础服务。

```bash
# 克隆项目仓库
git clone https://github.com/dochub-archive/mobile-archive.git

# 进入项目目录
cd mobile-archive

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化本地索引数据库
python scripts/init_db.py --config config/default.yaml

# 运行链接导入示例（导入 resources/sample_links.txt 中的链接）
python scripts/import_links.py --input resources/sample_links.txt --source external

# 启动本地开发服务
python app.py --host 0.0.0.0 --port 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，用于启动服务及执行脚本 |
| SQLite | 3.35 及以上 | 默认本地索引数据库引擎，无需额外安装 |
| Redis | 6.0 及以上 | 可选，用于链接可用性检测任务的分布式锁与队列 |
| curl | 7.68 及以上 | 用于链接可用性检测中的 HTTP 请求发起 |
| git | 2.25 及以上 | 版本控制工具，用于克隆仓库及管理补丁 |
| make | 3.81 及以上 | 构建工具，用于执行自动化任务脚本 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何导入链接、添加标签、导出清单及查看检测结果 |
| 运维指南 | docs/operations.md | 如何配置检测周期、备份索引数据及迁移数据库 |
| 开发文档 | docs/development.md | 项目代码结构、自定义插件开发及 API 扩展方法 |
| 设计说明 | docs/design.md | 索引表结构设计、链接规范化规则及缓存策略 |

## 资源列表

- h5.mobile.puhvjy.cn/Article/7049.doc
- h5.mobile.cmcvrr.cn/Article/60585.doc
- h5.mobile.nzfnve.cn/Article/775717.doc
- h5.mobile.nzfnve.cn/Article/22167.doc
- h5.mobile.hcbezg.cn/Article/3037.doc
- h5.mobile.cmcvrr.cn/Article/57287.doc
- h5.mobile.cvsifc.cn/Article/1056031.doc
- h5.mobile.cmcvrr.cn/Article/48661.doc
- h5.mobile.nwbbyt.cn/Article/2641464.doc
- h5.mobile.puhvjy.cn/Article/2532.doc
- h5.mobile.puhvjy.cn/Article/18458.doc
- h5.mobile.jnjpgf.cn/Article/5309641.doc
- h5.mobile.cmcvrr.cn/Article/913832.doc
- h5.mobile.nzfnve.cn/Article/7597.doc
- h5.mobile.hcbezg.cn/Article/90141.doc
- h5.mobile.jnjpgf.cn/Article/143367.doc
- h5.mobile.fuvxie.cn/Article/5815115.doc
- h5.mobile.puhvjy.cn/Article/8344056.doc
- h5.mobile.cvsifc.cn/Article/45563.doc
- h5.mobile.cvsifc.cn/Article/2673710.doc
- h5.mobile.cmcvrr.cn/Article/1962818.doc
- h5.mobile.nzfnve.cn/Article/7624.doc
- h5.mobile.fuvxie.cn/Article/0181.doc
- h5.mobile.fuvxie.cn/Article/7324818.doc
- h5.mobile.nwbbyt.cn/Article/5233100.doc
- h5.mobile.fuvxie.cn/Article/990984.doc
- h5.mobile.jnjpgf.cn/Article/524817.doc
- h5.mobile.cmcvrr.cn/Article/8721565.doc
- h5.mobile.jnjpgf.cn/Article/0599.doc
- h5.mobile.hcbezg.cn/Article/0645670.doc
- h5.mobile.jnjpgf.cn/Article/9570510.doc
- h5.mobile.puhvjy.cn/Article/16948.doc
- h5.mobile.puhvjy.cn/Article/363443.doc
- h5.mobile.nzfnve.cn/Article/62443.doc
- h5.mobile.hcbezg.cn/Article/628633.doc
- h5.mobile.hcbezg.cn/Article/5758013.doc
- h5.mobile.hcbezg.cn/Article/118578.doc
- h5.mobile.jnjpgf.cn/Article/1841.doc
- h5.mobile.nzfnve.cn/Article/934810.doc
- h5.mobile.fuvxie.cn/Article/415439.doc
- h5.mobile.hcbezg.cn/Article/41986.doc
- h5.mobile.cvsifc.cn/Article/79410.doc
- h5.mobile.fuvxie.cn/Article/0028517.doc
- h5.mobile.nwbbyt.cn/Article/27791.doc
- h5.mobile.cmcvrr.cn/Article/9585761.doc
- h5.mobile.nzfnve.cn/Article/277870.doc
- h5.mobile.fuvxie.cn/Article/72858.doc
- h5.mobile.jnjpgf.cn/Article/15491.doc
- h5.mobile.nwbbyt.cn/Article/190568.doc
- h5.mobile.cmcvrr.cn/Article/3192.doc
- h5.mobile.jnjpgf.cn/Article/911848.doc
- h5.mobile.cmcvrr.cn/Article/8315045.doc
- h5.mobile.cmcvrr.cn/Article/45381.doc
- h5.mobile.cvsifc.cn/Article/3227867.doc
- h5.mobile.fuvxie.cn/Article/1710132.doc
- h5.mobile.cvsifc.cn/Article/93989.doc
- h5.mobile.cmcvrr.cn/Article/4044076.doc
- h5.mobile.fuvxie.cn/Article/95206.doc
- h5.mobile.cvsifc.cn/Article/075754.doc
- h5.mobile.fuvxie.cn/Article/9011203.doc
- h5.mobile.jnjpgf.cn/Article/17074.doc
- h5.mobile.puhvjy.cn/Article/6881746.doc
- h5.mobile.fuvxie.cn/Article/638325.doc
- h5.mobile.nwbbyt.cn/Article/3522302.doc
- h5.mobile.nzfnve.cn/Article/01315.doc
- h5.mobile.nzfnve.cn/Article/915777.doc
- h5.mobile.fuvxie.cn/Article/5593.doc
- h5.mobile.nwbbyt.cn/Article/1570894.doc
- h5.mobile.jnjpgf.cn/Article/511543.doc
- h5.mobile.cmcvrr.cn/Article/429025.doc
- h5.mobile.puhvjy.cn/Article/2259345.doc
- h5.mobile.cvsifc.cn/Article/498319.doc
- h5.mobile.puhvjy.cn/Article/1652371.doc
- h5.mobile.cvsifc.cn/Article/2106305.doc
- h5.mobile.jnjpgf.cn/Article/6477786.doc
- h5.mobile.nzfnve.cn/Article/0921013.doc
- h5.mobile.hcbezg.cn/Article/5246.doc
- h5.mobile.cvsifc.cn/Article/877127.doc
- h5.mobile.nzfnve.cn/Article/38511.doc
- h5.mobile.cmcvrr.cn/Article/1220605.doc
- h5.mobile.hcbezg.cn/Article/1653.doc
- h5.mobile.cmcvrr.cn/Article/8702905.doc
- h5.mobile.cvsifc.cn/Article/711041.doc
- h5.mobile.nwbbyt.cn/Article/967116.doc
- h5.mobile.nwbbyt.cn/Article/3738972.doc
- h5.mobile.nzfnve.cn/Article/6584.doc
- h5.mobile.hcbezg.cn/Article/7495804.doc
- h5.mobile.cmcvrr.cn/Article/8950997.doc
- h5.mobile.cmcvrr.cn/Article/69476.doc
- h5.mobile.nwbbyt.cn/Article/58714.doc
- h5.mobile.hcbezg.cn/Article/00553.doc
- h5.mobile.cvsifc.cn/Article/1030623.doc
- h5.mobile.jnjpgf.cn/Article/5654.doc
- h5.mobile.nzfnve.cn/Article/5370.doc
- h5.mobile.fuvxie.cn/Article/2853.doc
- h5.mobile.cmcvrr.cn/Article/18911.doc
- h5.mobile.hcbezg.cn/Article/469991.doc
- h5.mobile.puhvjy.cn/Article/2629111.doc
- h5.mobile.hcbezg.cn/Article/7093.doc
- h5.mobile.fuvxie.cn/Article/7139081.doc
- h5.mobile.hcbezg.cn/Article/8743.doc
- h5.mobile.cvsifc.cn/Article/9857987.doc
- h5.mobile.nwbbyt.cn/Article/868791.doc
- h5.mobile.puhvjy.cn/Article/5462772.doc
- h5.mobile.fuvxie.cn/Article/7083.doc
- h5.mobile.cvsifc.cn/Article/6108.doc
- h5.mobile.nwbbyt.cn/Article/3374.doc
- h5.mobile.nzfnve.cn/Article/2086.doc
- h5.mobile.fuvxie.cn/Article/0883.doc
- h5.mobile.fuvxie.cn/Article/33742.doc
- h5.mobile.jnjpgf.cn/Article/49415.doc
- h5.mobile.jnjpgf.cn/Article/0013.doc
- h5.mobile.hcbezg.cn/Article/27789.doc
- h5.mobile.nwbbyt.cn/Article/281081.doc
- h5.mobile.fuvxie.cn/Article/508634.doc
- h5.mobile.hcbezg.cn/Article/8690.doc
- h5.mobile.cvsifc.cn/Article/2039.doc
- h5.mobile.nzfnve.cn/Article/4898190.doc
- h5.mobile.nzfnve.cn/Article/0061894.doc
- h5.mobile.nwbbyt.cn/Article/1518.doc
- h5.mobile.nwbbyt.cn/Article/467331.doc
- h5.mobile.jnjpgf.cn/Article/26616.doc
- h5.mobile.nzfnve.cn/Article/276976.doc
- h5.mobile.nwbbyt.cn/Article/1682.doc
- h5.mobile.puhvjy.cn/Article/2651.doc
- h5.mobile.hcbezg.cn/Article/6154.doc
- h5.mobile.fuvxie.cn/Article/1841289.doc
- h5.mobile.nzfnve.cn/Article/7639411.doc
- h5.mobile.jnjpgf.cn/Article/51173.doc
- h5.mobile.hcbezg.cn/Article/592908.doc
- h5.mobile.cvsifc.cn/Article/21757.doc
- h5.mobile.hcbezg.cn/Article/9256.doc
- h5.mobile.puhvjy.cn/Article/38019.doc
- h5.mobile.cmcvrr.cn/Article/53666.doc
- h5.mobile.nwbbyt.cn/Article/86360.doc
- h5.mobile.cvsifc.cn/Article/336257.doc
- h5.mobile.jnjpgf.cn/Article/2339661.doc
- h5.mobile.puhvjy.cn/Article/1365986.doc
- h5.mobile.cmcvrr.cn/Article/8566.doc
- h5.mobile.nwbbyt.cn/Article/8657478.doc
- h5.mobile.hcbezg.cn/Article/897536.doc
- h5.mobile.nzfnve.cn/Article/84500.doc
- h5.mobile.nzfnve.cn/Article/2763530.doc
- h5.mobile.nzfnve.cn/Article/7704.doc
- h5.mobile.hcbezg.cn/Article/716684.doc
- h5.mobile.cmcvrr.cn/Article/1026.doc
- h5.mobile.jnjpgf.cn/Article/9040162.doc
- h5.mobile.cvsifc.cn/Article/3543.doc
- h5.mobile.jnjpgf.cn/Article/9867122.doc
- h5.mobile.nwbbyt.cn/Article/2452.doc
- h5.mobile.hcbezg.cn/Article/1159.doc
- h5.mobile.fuvxie.cn/Article/736228.doc
- h5.mobile.cvsifc.cn/Article/9508980.doc
- h5.mobile.jnjpgf.cn/Article/76687.doc
- h5.mobile.nzfnve.cn/Article/8341852.doc
- h5.mobile.cmcvrr.cn/Article/1984.doc
- h5.mobile.hcbezg.cn/Article/6204436.doc
- h5.mobile.jnjpgf.cn/Article/3236.doc
- h5.mobile.nzfnve.cn/Article/5863.doc
- h5.mobile.cvsifc.cn/Article/5212.doc
- h5.mobile.hcbezg.cn/Article/03329.doc
- h5.mobile.jnjpgf.cn/Article/0988.doc
- h5.mobile.fuvxie.cn/Article/0284.doc
- h5.mobile.nwbbyt.cn/Article/3888.doc
- h5.mobile.cmcvrr.cn/Article/566077.doc
- h5.mobile.jnjpgf.cn/Article/4838.doc
- h5.mobile.cvsifc.cn/Article/6903739.doc
- h5.mobile.puhvjy.cn/Article/00471.doc
- h5.mobile.hcbezg.cn/Article/1181972.doc
- h5.mobile.nwbbyt.cn/Article/7601910.doc
- h5.mobile.nwbbyt.cn/Article/8692393.doc
- h5.mobile.nzfnve.cn/Article/2227162.doc
- h5.mobile.jnjpgf.cn/Article/1508.doc
- h5.mobile.puhvjy.cn/Article/4067.doc
- h5.mobile.nwbbyt.cn/Article/423581.doc
- h5.mobile.cmcvrr.cn/Article/8822580.doc
- h5.mobile.puhvjy.cn/Article/98525.doc
- h5.mobile.cmcvrr.cn/Article/629989.doc
- h5.mobile.hcbezg.cn/Article/8725078.doc
- h5.mobile.nzfnve.cn/Article/106271.doc
- h5.mobile.jnjpgf.cn/Article/64107.doc
- h5.mobile.puhvjy.cn/Article/1229.doc
- h5.mobile.hcbezg.cn/Article/019634.doc
- h5.mobile.cmcvrr.cn/Article/3542.doc
- h5.mobile.nzfnve.cn/Article/9310305.doc
- h5.mobile.hcbezg.cn/Article/3223.doc
- h5.mobile.cmcvrr.cn/Article/3632748.doc
- h5.mobile.cvsifc.cn/Article/9889.doc
- h5.mobile.cvsifc.cn/Article/90498.doc
- h5.mobile.nzfnve.cn/Article/7288.doc
- h5.mobile.fuvxie.cn/Article/990520.doc
- h5.mobile.puhvjy.cn/Article/666625.doc
- h5.mobile.jnjpgf.cn/Article/4640492.doc
- h5.mobile.puhvjy.cn/Article/50218.doc
- h5.mobile.jnjpgf.cn/Article/9513.doc
- h5.mobile.jnjpgf.cn/Article/47786.doc
- h5.mobile.cvsifc.cn/Article/2085784.doc
- h5.mobile.nzfnve.cn/Article/1775.doc
- h5.mobile.fuvxie.cn/Article/008631.doc
- h5.mobile.fuvxie.cn/Article/3228350.doc
- h5.mobile.cmcvrr.cn/Article/86242.doc
- h5.mobile.nzfnve.cn/Article/6690515.doc
- h5.mobile.puhvjy.cn/Article/6147.doc
- h5.mobile.cmcvrr.cn/Article/69335.doc
- h5.mobile.puhvjy.cn/Article/586019.doc
- h5.mobile.nwbbyt.cn/Article/3314.doc
- h5.mobile.nzfnve.cn/Article/4059.doc
- h5.mobile.cvsifc.cn/Article/8472.doc
- h5.mobile.nzfnve.cn/Article/57858.doc
- h5.mobile.nwbbyt.cn/Article/52400.doc
- h5.mobile.nzfnve.cn/Article/2534.doc
- h5.mobile.nwbbyt.cn/Article/29646.doc
- h5.mobile.fuvxie.cn/Article/15789.doc
- h5.mobile.cmcvrr.cn/Article/585307.doc
- h5.mobile.jnjpgf.cn/Article/5483168.doc
- h5.mobile.nwbbyt.cn/Article/89579.doc
- h5.mobile.puhvjy.cn/Article/10439.doc
- h5.mobile.jnjpgf.cn/Article/6180.doc
- h5.mobile.hcbezg.cn/Article/3686.doc
- h5.mobile.fuvxie.cn/Article/732767.doc
- h5.mobile.fuvxie.cn/Article/8495146.doc
- h5.mobile.puhvjy.cn/Article/69013.doc
- h5.mobile.cvsifc.cn/Article/6911.doc
- h5.mobile.hcbezg.cn/Article/117726.doc
- h5.mobile.cvsifc.cn/Article/639855.doc
- h5.mobile.nwbbyt.cn/Article/20766.doc
- h5.mobile.nwbbyt.cn/Article/7335948.doc
- h5.mobile.nzfnve.cn/Article/5012.doc
- h5.mobile.nwbbyt.cn/Article/0669.doc
- h5.mobile.fuvxie.cn/Article/1291.doc
- h5.mobile.nzfnve.cn/Article/639256.doc
- h5.mobile.cvsifc.cn/Article/463340.doc
- h5.mobile.nzfnve.cn/Article/331219.doc
- h5.mobile.nwbbyt.cn/Article/3019647.doc
- h5.mobile.fuvxie.cn/Article/78045.doc
- h5.mobile.cvsifc.cn/Article/8562390.doc
- h5.mobile.cvsifc.cn/Article/5918.doc
- h5.mobile.cmcvrr.cn/Article/62637.doc
- h5.mobile.hcbezg.cn/Article/1907.doc
- h5.mobile.cvsifc.cn/Article/45225.doc
- h5.mobile.jnjpgf.cn/Article/0695281.doc
- h5.mobile.cmcvrr.cn/Article/169710.doc
- h5.mobile.fuvxie.cn/Article/5215673.doc
- h5.mobile.cmcvrr.cn/Article/3280448.doc
- h5.mobile.hcbezg.cn/Article/0755444.doc
- h5.mobile.puhvjy.cn/Article/051092.doc
- h5.mobile.cvsifc.cn/Article/5712573.doc
- h5.mobile.hcbezg.cn/Article/6716098.doc
- h5.mobile.nwbbyt.cn/Article/24827.doc
- h5.mobile.jnjpgf.cn/Article/10579.doc

## 项目结构

```
mobile-archive/
├── app.py                         # 主应用入口，启动 Web 服务与调度器
├── config/
│   ├── default.yaml               # 默认配置文件，包含数据库路径、检测周期等
│   └── production.yaml            # 生产环境配置模板
├── core/
│   ├── __init__.py
│   ├── indexer.py                 # 链接索引核心逻辑，负责入库与更新
│   ├── checker.py                 # 链接可用性检测引擎，基于 asyncio + curl
│   ├── exporter.py                # 链接清单导出模块，支持 JSON/CSV/纯文本
│   └── models.py                  # 数据模型定义，使用 SQLAlchemy ORM
├── scripts/
│   ├── init_db.py                 # 初始化数据库表结构及基础配置
│   ├── import_links.py            # 从外部文件批量导入链接
│   ├── run_check.py               # 手动触发一次链接可用性检测
│   └── export_all.py              # 导出全量链接清单到指定目录
├── web/
│   ├── __init__.py
│   ├── routes.py                  # Flask 路由定义，包含页面与 API 端点
│   ├── templates/                 # Jinja2 模板目录
│   │   ├── base.html
│   │   ├── index.html             # 首页，显示统计概览与最近导入记录
│   │   └── links.html             # 链接列表页，支持过滤与排序
│   └── static/                    # CSS 与 JavaScript 静态资源
├── tests/
│   ├── test_indexer.py            # 索引模块单元测试
│   ├── test_checker.py            # 检测引擎单元测试
│   └── test_routes.py             # Web 路由集成测试
├── resources/
│   └── sample_links.txt           # 示例链接导入文件，供快速开始使用
├── docs/                          # 完整文档目录，参见文档导航章节
├── requirements.txt               # Python 依赖清单
├── Makefile                       # 常用任务快捷命令（如 make test、make run）
└── LICENSE                        # MIT 许可证文件
```

## 贡献指南

提交 Issue 报告链接导入异常、检测结果不准确或功能建议时，请提供复现步骤、输入数据及预期行为，并附上相关日志片段。

代码贡献需先 Fork 本仓库，在功能分支上开发，所有新功能或修复须包含对应的单元测试，确保现有测试用例全部通过。

文档更新类贡献请直接修改 docs/ 目录下的 Markdown 文件，并遵循既定的文档格式与术语规范，提交前检查链接有效性。

提交 Pull Request 前请运行 make lint 和 make test 进行代码风格检查与全量测试，PR 描述中需说明变更动机、实现方案及影响范围。

## 常见问题

Q: 项目是否存储实际文档文件，是否涉及版权问题？

A: 本项目仅存储文档链接（URL）及其元数据，不下载、不缓存、不转发任何实体文件。所有链接指向第三方源站，用户访问文档时直接与源站交互。项目运营方不承担因用户访问外部链接而产生的版权或合规责任。

Q: 链接可用性检测的具体机制是什么，是否会频繁请求源站？

A: 检测模块使用 HEAD 请求优先策略，仅获取响应头部状态码，不下载文件体。默认检测周期为每 24 小时一次，且支持配置检测并发数及超时时间，避免对源站造成压力。对于连续三次检测失败的链接，系统自动标记为失效并降低检测频率。

Q: 如何批量更新已导入链接的标签或备注信息？

A: 使用 scripts/update_metadata.py 脚本（位于 scripts/ 目录），通过 --filter 参数筛选目标链接（如按域名或导入批次），再通过 --tags 或 --note 参数更新信息。也支持从 CSV 文件批量导入更新记录。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

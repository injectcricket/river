# MobileDocs 技术文档聚合网关

MobileDocs 是一个面向移动开发团队、技术内容运营人员及自动化文档流水线设计的轻量级技术文档聚合网关系统。该项目定位于将分散在多个边缘存储节点、CDN 加速域或内部知识库中的技术文档、产品规格说明书、API 变更记录、测试报告等 .doc 格式文件，通过统一的 URL 规范与目录结构进行集中索引、分类检索与状态监控，从而降低文档散落带来的管理成本，提升技术资产的复用效率与可观测性。

MobileDocs 本身不实现文档内容的转换或存储，而是作为文档资源的元数据网关层，提供基于正则匹配的文档路由、来源域健康检查、文档版本指纹比对以及批量导入导出能力。项目目标用户包括：需要维护多版本产品文档的研发效能团队、负责外部技术内容分发的开发者关系部门、以及需要将历史文档资产迁移至新 CMS 或对象存储的自动化运维人员。通过 MobileDocs，用户可以快速建立一份可版本化、可审计、可编程访问的技术文档资产清单，并将分散的 .doc 文件 URL 转化为可监控、可分组、可打标的内部资源目录。

## 功能概览

- **多源文档索引**：支持将来自不同二级域名（如 cmcvrr.cn、fuvxie.cn、hcbezg.cn 等）的 .doc 文件 URL 统一收录，并依据来源域自动分组，便于区分不同业务线或文档来源。

- **资源指纹校验**：自动提取每个文档 URL 路径中的数字 ID 或文件名特征，生成轻量级指纹（MD5 哈希），用于检测重复收录、URL 变更或内容被覆盖的情况。

- **文档状态探活**：内置基于 HTTP HEAD 请求的异步健康检查机制，可周期性探测每个文档 URL 的可访问性、响应时间与 Content-Length，并输出状态报表。

- **分组标签系统**：允许用户对索引中的文档按来源域、文档类型（如规格书、测试报告、操作手册）、版本号或业务模块进行自定义标签标注，并支持按标签过滤导出。

- **导入导出流水线**：提供 JSON 与 CSV 两种格式的文档元数据导入导出接口，便于与外部 CI/CD 流水线、文档平台或内部数据中台对接，实现批量更新与自动化处理。

- **变更审计日志**：记录每一次文档 URL 的新增、删除或元数据修改操作，包含操作时间、操作人与变更前后内容，满足内部合规与回溯需求。

- **轻量级管理终端**：提供基于终端的命令行交互界面（CLI），支持快速查询、添加、移除文档资源，并支持将当前索引状态输出为静态 Markdown 报告。

## 应用场景

- **产品发布文档汇总**：在产品新版本发布前，研发团队将各模块的更新说明、接口变更文档、测试用例文档上传至不同的内部文件服务器。使用 MobileDocs 可将这些分散的 .doc 文件地址统一录入网关，并打上版本号标签，发布后一键导出完整文档清单供质量审核与归档。

- **历史技术文档迁移**：企业进行文档平台升级时，旧平台中存储的大量历史 .doc 文件分散在多个遗留域名下。MobileDocs 支持批量导入这些 URL，并通过指纹校验识别出重复或已失效的链接，为迁移工作提供干净的数据源清单，避免遗漏或重复迁移。

- **外部合作方文档分发追踪**：技术文档需要提供给外部合作伙伴时，往往需要记录哪些文档已被分享、来自哪些渠道。MobileDocs 可对每个文档 URL 标记合作方名称与分享日期，并定期探活确保外部链接仍有效，降低合作方因链接失效而产生的沟通成本。

- **自动化文档监控告警**：运维团队可将 MobileDocs 集成至监控系统，当某个关键文档 URL 返回 4xx 或 5xx 状态码，或响应时间超过设定阈值时，触发告警通知，帮助团队第一时间发现文档访问异常。

## 快速开始

以下步骤帮助您在本地环境快速启动 MobileDocs 网关服务，并导入首批文档 URL。

```bash
# 1. 克隆项目仓库
git clone https://github.com/your-org/mobiledocs-gateway.git
cd mobiledocs-gateway

# 2. 安装依赖（Python 3.9+ 环境）
pip install -r requirements.txt

# 3. 初始化本地索引数据库并启动网关服务
python cli.py init --db-path ./data/index.db
python cli.py import --source ./samples/initial_urls.csv --group default
python server.py --port 8080 --watch
```

服务启动后，可通过 http://localhost:8080/api/v1/docs 获取当前索引的文档列表，或通过 `cli.py query --filter domain=cmcvrr.cn` 进行命令行查询。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 或更高 | 核心运行环境，推荐使用 3.11 以获取性能优化 |
| SQLite | 3.35.0 或更高 | 内置轻量级索引存储，无需额外安装，但需确保支持 JSON 扩展 |
| requests | 2.28.0 或更高 | 用于文档 URL 探活与 HTTP 状态检测 |
| click | 8.1.0 或更高 | CLI 命令行交互框架 |
| pyyaml | 6.0 或更高 | 用于配置文件解析与导出 YAML 格式报告 |
| pytest | 7.2.0 或更高 | 仅开发与测试环境必需，用于运行单元测试 |
| black | 23.0.0 或更高 | 仅开发环境必需，用于代码格式化检查 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/getting-started.md | 如何安装、配置并首次运行 MobileDocs，以及如何导入第一批文档 URL |
| 核心概念 | docs/concepts.md | 解释文档索引、来源域、指纹校验、探活任务等核心术语与设计思路 |
| 命令行参考 | docs/cli-reference.md | 详细列出所有 CLI 命令及其参数，包括 import、export、health-check、tag 等 |
| API 接口 | docs/api-docs.md | 描述网关提供的 RESTful API，包括文档列表查询、分组统计、健康状态获取等端点 |
| 运维手册 | docs/operations.md | 介绍如何部署到生产环境、配置反向代理、调整探活频率及处理常见故障 |

## 资源列表

- h5.mobile.cmcvrr.cn/Article/71703.doc
- h5.mobile.fuvxie.cn/Article/864538.doc
- h5.mobile.fuvxie.cn/Article/5924719.doc
- h5.mobile.fuvxie.cn/Article/75151.doc
- h5.mobile.hcbezg.cn/Article/6520.doc
- h5.mobile.hcbezg.cn/Article/145569.doc
- h5.mobile.nwbbyt.cn/Article/6237077.doc
- h5.mobile.fuvxie.cn/Article/648426.doc
- h5.mobile.nzfnve.cn/Article/472931.doc
- h5.mobile.nwbbyt.cn/Article/4902.doc
- h5.mobile.puhvjy.cn/Article/22872.doc
- h5.mobile.puhvjy.cn/Article/70149.doc
- h5.mobile.nzfnve.cn/Article/9713747.doc
- h5.mobile.nzfnve.cn/Article/9446563.doc
- h5.mobile.cvsifc.cn/Article/08058.doc
- h5.mobile.nwbbyt.cn/Article/675111.doc
- h5.mobile.cmcvrr.cn/Article/0747660.doc
- h5.mobile.jnjpgf.cn/Article/9913.doc
- h5.mobile.cmcvrr.cn/Article/05831.doc
- h5.mobile.nwbbyt.cn/Article/60095.doc
- h5.mobile.hcbezg.cn/Article/6292172.doc
- h5.mobile.jnjpgf.cn/Article/5772.doc
- h5.mobile.jnjpgf.cn/Article/75087.doc
- h5.mobile.cmcvrr.cn/Article/3969660.doc
- h5.mobile.fuvxie.cn/Article/83256.doc
- h5.mobile.jnjpgf.cn/Article/26701.doc
- h5.mobile.nwbbyt.cn/Article/457208.doc
- h5.mobile.cmcvrr.cn/Article/4195.doc
- h5.mobile.nwbbyt.cn/Article/0894573.doc
- h5.mobile.hcbezg.cn/Article/16368.doc
- h5.mobile.nzfnve.cn/Article/1189.doc
- h5.mobile.nzfnve.cn/Article/731530.doc
- h5.mobile.cmcvrr.cn/Article/241154.doc
- h5.mobile.cmcvrr.cn/Article/866287.doc
- h5.mobile.cvsifc.cn/Article/907229.doc
- h5.mobile.cvsifc.cn/Article/936237.doc
- h5.mobile.nwbbyt.cn/Article/7037.doc
- h5.mobile.cvsifc.cn/Article/4273583.doc
- h5.mobile.cvsifc.cn/Article/2110403.doc
- h5.mobile.hcbezg.cn/Article/7519.doc
- h5.mobile.cmcvrr.cn/Article/61615.doc
- h5.mobile.nwbbyt.cn/Article/1283883.doc
- h5.mobile.nwbbyt.cn/Article/98861.doc
- h5.mobile.cmcvrr.cn/Article/1086390.doc
- h5.mobile.cmcvrr.cn/Article/11806.doc
- h5.mobile.nzfnve.cn/Article/4579053.doc
- h5.mobile.fuvxie.cn/Article/83046.doc
- h5.mobile.jnjpgf.cn/Article/9673133.doc
- h5.mobile.puhvjy.cn/Article/518544.doc
- h5.mobile.puhvjy.cn/Article/046863.doc
- h5.mobile.puhvjy.cn/Article/90179.doc
- h5.mobile.hcbezg.cn/Article/650120.doc
- h5.mobile.cvsifc.cn/Article/8018383.doc
- h5.mobile.nzfnve.cn/Article/9156.doc
- h5.mobile.nwbbyt.cn/Article/43349.doc
- h5.mobile.fuvxie.cn/Article/383034.doc
- h5.mobile.cmcvrr.cn/Article/099483.doc
- h5.mobile.cvsifc.cn/Article/19945.doc
- h5.mobile.cmcvrr.cn/Article/7184.doc
- h5.mobile.cmcvrr.cn/Article/20779.doc
- h5.mobile.jnjpgf.cn/Article/2414257.doc
- h5.mobile.cvsifc.cn/Article/1717.doc
- h5.mobile.fuvxie.cn/Article/76487.doc
- h5.mobile.nzfnve.cn/Article/0680142.doc
- h5.mobile.nzfnve.cn/Article/8433324.doc
- h5.mobile.fuvxie.cn/Article/6143.doc
- h5.mobile.jnjpgf.cn/Article/010112.doc
- h5.mobile.jnjpgf.cn/Article/9735983.doc
- h5.mobile.puhvjy.cn/Article/89702.doc
- h5.mobile.cvsifc.cn/Article/206102.doc
- h5.mobile.nwbbyt.cn/Article/498842.doc
- h5.mobile.cmcvrr.cn/Article/543527.doc
- h5.mobile.nzfnve.cn/Article/2597.doc
- h5.mobile.cmcvrr.cn/Article/8573435.doc
- h5.mobile.cmcvrr.cn/Article/562877.doc
- h5.mobile.puhvjy.cn/Article/0352.doc
- h5.mobile.fuvxie.cn/Article/762963.doc
- h5.mobile.puhvjy.cn/Article/2435.doc
- h5.mobile.cmcvrr.cn/Article/25512.doc
- h5.mobile.fuvxie.cn/Article/5738.doc
- h5.mobile.cmcvrr.cn/Article/2411.doc
- h5.mobile.cvsifc.cn/Article/4784.doc
- h5.mobile.puhvjy.cn/Article/7816.doc
- h5.mobile.cvsifc.cn/Article/6064.doc
- h5.mobile.fuvxie.cn/Article/539825.doc
- h5.mobile.nwbbyt.cn/Article/542346.doc
- h5.mobile.nwbbyt.cn/Article/16878.doc
- h5.mobile.jnjpgf.cn/Article/4504.doc
- h5.mobile.hcbezg.cn/Article/97324.doc
- h5.mobile.puhvjy.cn/Article/58279.doc
- h5.mobile.cvsifc.cn/Article/125374.doc
- h5.mobile.nzfnve.cn/Article/54863.doc
- h5.mobile.cvsifc.cn/Article/784274.doc
- h5.mobile.cmcvrr.cn/Article/10638.doc
- h5.mobile.fuvxie.cn/Article/575136.doc
- h5.mobile.jnjpgf.cn/Article/31224.doc
- h5.mobile.jnjpgf.cn/Article/173050.doc
- h5.mobile.nzfnve.cn/Article/868152.doc
- h5.mobile.jnjpgf.cn/Article/63713.doc
- h5.mobile.hcbezg.cn/Article/6585.doc
- h5.mobile.nwbbyt.cn/Article/9721870.doc
- h5.mobile.puhvjy.cn/Article/781484.doc
- h5.mobile.nzfnve.cn/Article/37971.doc
- h5.mobile.nzfnve.cn/Article/21900.doc
- h5.mobile.cvsifc.cn/Article/4900.doc
- h5.mobile.nwbbyt.cn/Article/300591.doc
- h5.mobile.nwbbyt.cn/Article/459065.doc
- h5.mobile.hcbezg.cn/Article/6507639.doc
- h5.mobile.puhvjy.cn/Article/8947.doc
- h5.mobile.nzfnve.cn/Article/43226.doc
- h5.mobile.puhvjy.cn/Article/19215.doc
- h5.mobile.nwbbyt.cn/Article/6348721.doc
- h5.mobile.puhvjy.cn/Article/9589.doc
- h5.mobile.cvsifc.cn/Article/6849195.doc
- h5.mobile.nzfnve.cn/Article/0224869.doc
- h5.mobile.puhvjy.cn/Article/058442.doc
- h5.mobile.cvsifc.cn/Article/4438.doc
- h5.mobile.fuvxie.cn/Article/82607.doc
- h5.mobile.cmcvrr.cn/Article/50448.doc
- h5.mobile.jnjpgf.cn/Article/9798.doc
- h5.mobile.nzfnve.cn/Article/2928.doc
- h5.mobile.nzfnve.cn/Article/72930.doc
- h5.mobile.jnjpgf.cn/Article/091150.doc
- h5.mobile.nzfnve.cn/Article/5391404.doc
- h5.mobile.nwbbyt.cn/Article/9734.doc
- h5.mobile.nwbbyt.cn/Article/171726.doc
- h5.mobile.fuvxie.cn/Article/321161.doc
- h5.mobile.puhvjy.cn/Article/0340.doc
- h5.mobile.hcbezg.cn/Article/216676.doc
- h5.mobile.cvsifc.cn/Article/6965.doc
- h5.mobile.nwbbyt.cn/Article/3799632.doc
- h5.mobile.cmcvrr.cn/Article/267359.doc
- h5.mobile.fuvxie.cn/Article/198926.doc
- h5.mobile.hcbezg.cn/Article/7758807.doc
- h5.mobile.nwbbyt.cn/Article/732528.doc
- h5.mobile.hcbezg.cn/Article/815007.doc
- h5.mobile.nzfnve.cn/Article/79324.doc
- h5.mobile.cmcvrr.cn/Article/9367838.doc
- h5.mobile.fuvxie.cn/Article/1748.doc
- h5.mobile.jnjpgf.cn/Article/0495907.doc
- h5.mobile.nzfnve.cn/Article/76779.doc
- h5.mobile.hcbezg.cn/Article/9626.doc
- h5.mobile.puhvjy.cn/Article/5055622.doc
- h5.mobile.nzfnve.cn/Article/8933.doc
- h5.mobile.cvsifc.cn/Article/5240.doc
- h5.mobile.hcbezg.cn/Article/9504305.doc
- h5.mobile.hcbezg.cn/Article/7438.doc
- h5.mobile.nzfnve.cn/Article/4445.doc
- h5.mobile.nzfnve.cn/Article/280702.doc
- h5.mobile.cmcvrr.cn/Article/1234.doc
- h5.mobile.hcbezg.cn/Article/963013.doc
- h5.mobile.nzfnve.cn/Article/9527.doc
- h5.mobile.jnjpgf.cn/Article/0087.doc
- h5.mobile.jnjpgf.cn/Article/388250.doc
- h5.mobile.nwbbyt.cn/Article/6593.doc
- h5.mobile.cmcvrr.cn/Article/6745.doc
- h5.mobile.cmcvrr.cn/Article/5283.doc
- h5.mobile.puhvjy.cn/Article/8740.doc
- h5.mobile.cvsifc.cn/Article/7510.doc
- h5.mobile.fuvxie.cn/Article/8325.doc
- h5.mobile.nzfnve.cn/Article/770589.doc
- h5.mobile.nzfnve.cn/Article/1403.doc
- h5.mobile.nzfnve.cn/Article/9133814.doc
- h5.mobile.hcbezg.cn/Article/600045.doc
- h5.mobile.fuvxie.cn/Article/9415.doc
- h5.mobile.hcbezg.cn/Article/4988.doc
- h5.mobile.puhvjy.cn/Article/98757.doc
- h5.mobile.nzfnve.cn/Article/83202.doc
- h5.mobile.hcbezg.cn/Article/802506.doc
- h5.mobile.fuvxie.cn/Article/1260740.doc
- h5.mobile.fuvxie.cn/Article/0991031.doc
- h5.mobile.puhvjy.cn/Article/1907.doc
- h5.mobile.fuvxie.cn/Article/9014022.doc
- h5.mobile.fuvxie.cn/Article/2731224.doc
- h5.mobile.nzfnve.cn/Article/533255.doc
- h5.mobile.nzfnve.cn/Article/7319543.doc
- h5.mobile.hcbezg.cn/Article/7369268.doc
- h5.mobile.cvsifc.cn/Article/02850.doc
- h5.mobile.cvsifc.cn/Article/7794042.doc
- h5.mobile.nzfnve.cn/Article/371847.doc
- h5.mobile.nwbbyt.cn/Article/94465.doc
- h5.mobile.fuvxie.cn/Article/174674.doc
- h5.mobile.cmcvrr.cn/Article/803879.doc
- h5.mobile.nwbbyt.cn/Article/67685.doc
- h5.mobile.nwbbyt.cn/Article/5989546.doc
- h5.mobile.hcbezg.cn/Article/9549.doc
- h5.mobile.fuvxie.cn/Article/404730.doc
- h5.mobile.nwbbyt.cn/Article/8645.doc
- h5.mobile.puhvjy.cn/Article/17630.doc
- h5.mobile.hcbezg.cn/Article/5673408.doc
- h5.mobile.puhvjy.cn/Article/8446.doc
- h5.mobile.cvsifc.cn/Article/2778409.doc
- h5.mobile.nwbbyt.cn/Article/1711.doc
- h5.mobile.nzfnve.cn/Article/3892.doc
- h5.mobile.jnjpgf.cn/Article/07989.doc
- h5.mobile.hcbezg.cn/Article/486670.doc
- h5.mobile.cmcvrr.cn/Article/0156.doc
- h5.mobile.hcbezg.cn/Article/3459110.doc
- h5.mobile.jnjpgf.cn/Article/66644.doc
- h5.mobile.cmcvrr.cn/Article/031861.doc
- h5.mobile.puhvjy.cn/Article/2416774.doc
- h5.mobile.cvsifc.cn/Article/929047.doc
- h5.mobile.cvsifc.cn/Article/78840.doc
- h5.mobile.cvsifc.cn/Article/9979282.doc
- h5.mobile.nwbbyt.cn/Article/1464759.doc
- h5.mobile.fuvxie.cn/Article/45051.doc
- h5.mobile.cmcvrr.cn/Article/19722.doc
- h5.mobile.nzfnve.cn/Article/2181.doc
- h5.mobile.cvsifc.cn/Article/6830.doc
- h5.mobile.puhvjy.cn/Article/489402.doc
- h5.mobile.jnjpgf.cn/Article/09686.doc
- h5.mobile.jnjpgf.cn/Article/89163.doc
- h5.mobile.cmcvrr.cn/Article/8592952.doc
- h5.mobile.hcbezg.cn/Article/499058.doc
- h5.mobile.nwbbyt.cn/Article/88307.doc
- h5.mobile.nzfnve.cn/Article/353443.doc
- h5.mobile.nwbbyt.cn/Article/0095253.doc
- h5.mobile.jnjpgf.cn/Article/58860.doc
- h5.mobile.nzfnve.cn/Article/85762.doc
- h5.mobile.jnjpgf.cn/Article/328843.doc
- h5.mobile.nzfnve.cn/Article/92618.doc
- h5.mobile.cmcvrr.cn/Article/1112796.doc
- h5.mobile.hcbezg.cn/Article/22279.doc
- h5.mobile.fuvxie.cn/Article/4889312.doc
- h5.mobile.cmcvrr.cn/Article/0724.doc
- h5.mobile.nzfnve.cn/Article/6300769.doc
- h5.mobile.puhvjy.cn/Article/352233.doc
- h5.mobile.fuvxie.cn/Article/8827524.doc
- h5.mobile.cmcvrr.cn/Article/07100.doc
- h5.mobile.puhvjy.cn/Article/480593.doc
- h5.mobile.cmcvrr.cn/Article/5732344.doc
- h5.mobile.puhvjy.cn/Article/03600.doc
- h5.mobile.nwbbyt.cn/Article/605937.doc
- h5.mobile.cvsifc.cn/Article/411292.doc
- h5.mobile.hcbezg.cn/Article/640403.doc
- h5.mobile.nzfnve.cn/Article/5629.doc
- h5.mobile.cmcvrr.cn/Article/1512.doc
- h5.mobile.puhvjy.cn/Article/9502.doc
- h5.mobile.puhvjy.cn/Article/54753.doc
- h5.mobile.nwbbyt.cn/Article/666144.doc
- h5.mobile.nzfnve.cn/Article/2399584.doc
- h5.mobile.nwbbyt.cn/Article/39180.doc
- h5.mobile.puhvjy.cn/Article/733540.doc
- h5.mobile.jnjpgf.cn/Article/05008.doc
- h5.mobile.cvsifc.cn/Article/7076304.doc
- h5.mobile.cvsifc.cn/Article/171104.doc
- h5.mobile.fuvxie.cn/Article/232760.doc
- h5.mobile.puhvjy.cn/Article/68175.doc
- h5.mobile.nzfnve.cn/Article/89976.doc
- h5.mobile.hcbezg.cn/Article/7144205.doc

## 项目结构

项目采用模块化分层设计，核心索引引擎、探活调度器、CLI 交互层与 API 服务层各自独立，便于扩展与替换。

```
mobiledocs-gateway/
├── cli/                              # 命令行交互模块
│   ├── commands.py                   # 注册所有 cli 子命令（import, export, health-check, tag）
│   ├── formatter.py                  # 控制台输出格式化（表格、彩色状态、进度条）
│   └── validators.py                 # 输入参数校验（URL 格式、分组名称合法性）
│
├── core/                             # 核心业务逻辑层
│   ├── indexer.py                    # 文档索引引擎，负责 URL 录入、指纹生成、分组管理
│   ├── health.py                     # 异步探活调度器，管理并发请求与超时重试
│   ├── fingerprint.py                # 基于路径与文件名的指纹算法实现
│   └── audit.py                      # 变更审计日志记录与查询接口
│
├── storage/                          # 持久化存储层
│   ├── sqlite_store.py               # SQLite 数据库操作封装（建表、增删改查、事务）
│   ├── migrations/                   # 数据库版本迁移脚本
│   │   ├── v1_initial_schema.sql
│   │   └── v2_add_health_columns.sql
│   └── serializers.py                # 索引数据序列化与反序列化（JSON / CSV / YAML）
│
├── api/                              # HTTP API 服务层
│   ├── server.py                     # Flask 应用入口，注册路由与错误处理
│   ├── routes/                       # 路由分组
│   │   ├── docs.py                   # /api/v1/docs 相关端点（列表、查询、详情）
│   │   ├── groups.py                 # /api/v1/groups 分组统计与操作
│   │   └── health.py                 # /api/v1/health 服务自检与探活状态聚合
│   └── middlewares/                  # 请求拦截与日志中间件
│       ├── cors.py                   # 跨域资源共享配置
│       └── ratelimit.py              # 基于 IP 的请求限流
│
├── tests/                            # 单元测试与集成测试
│   ├── test_indexer.py
│   ├── test_health.py
│   ├── test_api.py
│   └── fixtures/                     # 测试用静态数据样本
│       └── sample_urls.csv
│
├── config/                           # 配置管理
│   ├── default.yaml                  # 默认配置（探活间隔、并发数、日志级别）
│   ├── production.yaml               # 生产环境覆盖配置
│   └── schema.json                   # 配置文件的 JSON Schema 校验规则
│
├── scripts/                          # 运维辅助脚本
│   ├── backup_index.sh               # 定时备份索引数据库
│   └── migrate_legacy.py             # 从旧版格式迁移至当前索引结构
│
├── docs/                             # 项目文档
│   ├── getting-started.md
│   ├── concepts.md
│   ├── cli-reference.md
│   ├── api-docs.md
│   └── operations.md
│
├── requirements.txt                  # 生产依赖清单
├── requirements-dev.txt              # 开发与测试额外依赖
├── setup.py                          # 项目打包与安装配置
├── README.md                         # 本文件
└── LICENSE                           # MIT 许可证
```

## 贡献指南

欢迎社区开发者以 Issue 或 Pull Request 形式参与 MobileDocs 项目改进。所有贡献需遵循以下流程：

1. 在 GitHub 仓库中创建 Issue 描述您要修复的问题或新增的功能，等待项目维护者确认需求范围，避免重复工作或方向偏离。

2. 从 `main` 分支切出专用的功能分支（如 `feat/your-feature-name` 或 `fix/issue-number`），并在本地开发环境中编写代码与对应的单元测试，确保测试覆盖率达到 80% 以上。

3. 提交代码前运行 `black .` 进行代码格式化，并执行 `pytest tests/` 确保所有现有测试通过。提交信息请遵循约定式提交规范（如 `feat: add batch import progress bar` 或 `fix: correct fingerprint collision on large id`）。

4. 推送分支至远程仓库并创建 Pull Request，在 PR 描述中清晰说明变更内容、影响范围以及是否涉及破坏性改动。PR 至少需要一位维护者审核通过方可合并。

5. 若涉及新增配置项或 API 端点，请在 `docs/` 目录下同步更新对应文档，并在 PR 中标注文档已更新。未附带文档更新的功能性 PR 将暂缓合并。

## 常见问题

**问：MobileDocs 是否支持 .docx 或其他格式的文档？**

目前索引层对文件扩展名不做严格校验，仅依据 URL 路径中的 .doc 后缀进行识别。若需要索引 .docx、.pdf 或 .xls 文件，可在导入时通过 `--allow-extensions` 参数指定额外后缀列表。核心探活与指纹机制对所有文件类型通用，不依赖文件内容解析。

**问：健康检查探活是否会影响源站服务器性能？**

MobileDocs 默认使用 HEAD 请求进行探活，且并发数可通过配置调整（默认 10 个并发）。探活间隔默认为每小时一次，对绝大多数文档存储服务造成的负载可忽略不计。若源站对请求频率敏感，可将探活间隔调整为 6 小时或更高，并启用 `--spread` 参数将请求分散到时间段内随机执行。

**问：如何迁移索引数据到另一台服务器？**

索引数据全部存储在 SQLite 数据库文件（如 `data/index.db`）中，直接复制该文件至新服务器对应路径即可。若需导出为纯文本格式，可使用 `cli.py export --format json > backup.json` 导出为 JSON，然后在新服务器使用 `cli.py import --file backup.json` 恢复。两种方式均保留所有标签与审计日志信息。

## 许可证

MIT License

Copyright (c) 2026 MobileDocs Contributors

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

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

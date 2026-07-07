# ResourceLink Aggregate Service

ResourceLink Aggregate Service 是一个面向技术文档、行业报告与工程资料的外链聚合与管理平台，专注于将分散于多个域名与路径下的文档资源（以 .doc 格式为主）进行统一索引、分类挂载与快速检索。项目定位于内部研发团队、技术运营部门以及外包协作场景下的文档资产梳理需求，解决多源、多目录、非结构化文档难以追踪和重复引用的问题。

该服务不直接存储文档内容，而是以轻量级索引层的方式记录文档的源地址、来源域名、路径特征以及批次归属，并提供命令行、HTTP API 与静态站点三种访问形态。目标用户包括技术负责人、知识管理专员、运维工程师以及需要批量查阅外部文档资源的开发人员。项目当前收录第 145/160 批次资源，总计 250 个文档链接，覆盖 7 个独立域名下的 Article 目录。

## 功能概览

统一索引挂载 基于域名与路径两级结构挂载外部文档链接，支持多源混合输入，保留原始 URL 完整信息，不做自动跳转或重写。

批次与来源标记 每个资源条目记录其所属导入批次（第 145/160 批）及原始来源域名，便于后续按批次筛选与审计。

只读访问接口 提供只读的 HTTP API 用于查询文档列表、按域名过滤、按路径关键词匹配，适用于外部系统集成。

命令行检索工具 内置 CLI 工具支持按域名、文件编号、批次号快速检索目标文档 URL，并支持输出为纯文本列表或 JSON 格式。

静态站点预览 可生成静态 HTML 目录页，将资源列表渲染为可点击的文档索引页面，便于在内部维基或文档站中嵌入。

来源去重记录 对同一 URL 的重复提交进行自动忽略并记录首次出现时间，避免索引膨胀。

健康检查与状态监控 提供 `/health` 与 `/metrics` 端点，支持 Prometheus 格式的输出，便于运维侧监控索引服务可用性。

## 应用场景

内部技术文档库的补充索引 当团队内部 Wiki 或 Confluence 中引用了大量外部 .doc 格式的规范文档时，可使用 ResourceLink 统一维护这些链接的清单，避免文档地址散落在邮件、聊天记录或多个页面中，降低查找成本。

外包项目交付物盘点 在外包开发或技术合作中，乙方常通过多个临时域名提供设计说明书、接口文档或测试报告。ResourceLink 可将这些跨域链接汇总为单一清单，方便甲方按批次核对交付物是否齐全。

自动化文档链接巡检 运维或质量保障团队可结合 ResourceLink 的只读 API，定期请求资源列表并与外部站点进行连通性检查，及时发现失效链接，生成告警或报告。

多环境文档引用隔离 在开发、测试、预发布环境中，文档来源域名可能不同。ResourceLink 支持按域名标签进行环境分类，便于各环境引用各自对应的文档集，减少配置错误。

## 快速开始

以下步骤展示如何从源码部署 ResourceLink Aggregate Service 并完成初始索引构建。

```bash
# 克隆项目仓库
git clone https://github.com/resourcelink/aggregate-service.git
cd aggregate-service

# 安装 Python 依赖（推荐使用 Python 3.10+ 虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 执行索引构建脚本，导入第 145/160 批资源
python scripts/import_batch.py --batch 145 --source data/batch_145.txt

# 启动本地开发服务器，默认监听 8000 端口
python app.py --port 8000
```

启动后可通过 `http://localhost:8000/api/v1/resources` 访问资源列表接口，或通过 `http://localhost:8000/static/index.html` 查看静态目录页。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 及以上 | 核心运行环境，用于 API 服务与 CLI 工具 |
| Flask | 2.3.x | HTTP API 框架，提供路由与请求解析 |
| PyYAML | 6.0.x | 用于解析配置文件与批次元数据 |
| click | 8.1.x | CLI 命令行工具的基础库 |
| markdown | 3.5.x | 仅用于生成静态站点时的内容渲染，非核心依赖 |
| prometheus-client | 0.19.x | 可选，启用 `/metrics` 端点时使用 |
| pytest | 7.4.x | 仅开发测试环境需要，生产环境可不安装 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | `/docs/user-guide.md` | 如何添加新批次资源、如何通过 API 检索文档、静态站点如何生成与部署 |
| 运维手册 | `/docs/operations.md` | 健康检查配置、日志格式说明、索引重建流程与备份恢复策略 |
| 开发指南 | `/docs/development.md` | 项目目录结构说明、新增 API 端点的规范、单元测试编写方法 |
| 设计文档 | `/docs/design.md` | 索引存储模型（基于 SQLite 的设计）、批次与来源域名的关系、URL 规范化策略 |

## 资源列表

- h5.mobile.cmcvrr.cn/Article/0475100.doc
- h5.mobile.cmcvrr.cn/Article/92979.doc
- h5.mobile.jnjpgf.cn/Article/937804.doc
- h5.mobile.puhvjy.cn/Article/860494.doc
- h5.mobile.nzfnve.cn/Article/1230.doc
- h5.mobile.fuvxie.cn/Article/716124.doc
- h5.mobile.hcbezg.cn/Article/744690.doc
- h5.mobile.cmcvrr.cn/Article/523409.doc
- h5.mobile.fuvxie.cn/Article/5953.doc
- h5.mobile.jnjpgf.cn/Article/8698.doc
- h5.mobile.fuvxie.cn/Article/54519.doc
- h5.mobile.puhvjy.cn/Article/6545.doc
- h5.mobile.jnjpgf.cn/Article/37014.doc
- h5.mobile.nzfnve.cn/Article/7808.doc
- h5.mobile.cmcvrr.cn/Article/6945240.doc
- h5.mobile.fuvxie.cn/Article/68247.doc
- h5.mobile.fuvxie.cn/Article/41105.doc
- h5.mobile.nzfnve.cn/Article/3237796.doc
- h5.mobile.nwbbyt.cn/Article/6682.doc
- h5.mobile.nzfnve.cn/Article/677640.doc
- h5.mobile.cvsifc.cn/Article/708287.doc
- h5.mobile.nwbbyt.cn/Article/6344398.doc
- h5.mobile.jnjpgf.cn/Article/5078020.doc
- h5.mobile.cmcvrr.cn/Article/7956802.doc
- h5.mobile.cvsifc.cn/Article/8328722.doc
- h5.mobile.fuvxie.cn/Article/0440.doc
- h5.mobile.cmcvrr.cn/Article/38348.doc
- h5.mobile.puhvjy.cn/Article/884635.doc
- h5.mobile.nzfnve.cn/Article/441057.doc
- h5.mobile.cvsifc.cn/Article/56102.doc
- h5.mobile.fuvxie.cn/Article/7025893.doc
- h5.mobile.cvsifc.cn/Article/165117.doc
- h5.mobile.puhvjy.cn/Article/34961.doc
- h5.mobile.nzfnve.cn/Article/17885.doc
- h5.mobile.fuvxie.cn/Article/7076378.doc
- h5.mobile.cmcvrr.cn/Article/96982.doc
- h5.mobile.cvsifc.cn/Article/711993.doc
- h5.mobile.nwbbyt.cn/Article/8069.doc
- h5.mobile.jnjpgf.cn/Article/1446.doc
- h5.mobile.puhvjy.cn/Article/8512165.doc
- h5.mobile.nzfnve.cn/Article/6137989.doc
- h5.mobile.jnjpgf.cn/Article/293021.doc
- h5.mobile.nwbbyt.cn/Article/7100.doc
- h5.mobile.cvsifc.cn/Article/4354471.doc
- h5.mobile.fuvxie.cn/Article/51614.doc
- h5.mobile.hcbezg.cn/Article/252383.doc
- h5.mobile.fuvxie.cn/Article/6138173.doc
- h5.mobile.puhvjy.cn/Article/47872.doc
- h5.mobile.nwbbyt.cn/Article/719246.doc
- h5.mobile.cmcvrr.cn/Article/1262186.doc
- h5.mobile.cvsifc.cn/Article/1636.doc
- h5.mobile.fuvxie.cn/Article/5523.doc
- h5.mobile.cvsifc.cn/Article/471141.doc
- h5.mobile.cvsifc.cn/Article/8828680.doc
- h5.mobile.hcbezg.cn/Article/182866.doc
- h5.mobile.puhvjy.cn/Article/5528.doc
- h5.mobile.fuvxie.cn/Article/572678.doc
- h5.mobile.fuvxie.cn/Article/6001925.doc
- h5.mobile.cvsifc.cn/Article/80091.doc
- h5.mobile.nzfnve.cn/Article/0729922.doc
- h5.mobile.nzfnve.cn/Article/6707273.doc
- h5.mobile.nwbbyt.cn/Article/9316422.doc
- h5.mobile.fuvxie.cn/Article/5877890.doc
- h5.mobile.cmcvrr.cn/Article/9676.doc
- h5.mobile.cmcvrr.cn/Article/72236.doc
- h5.mobile.cmcvrr.cn/Article/00018.doc
- h5.mobile.hcbezg.cn/Article/169314.doc
- h5.mobile.nwbbyt.cn/Article/67365.doc
- h5.mobile.fuvxie.cn/Article/0840.doc
- h5.mobile.hcbezg.cn/Article/8331.doc
- h5.mobile.nwbbyt.cn/Article/64972.doc
- h5.mobile.cvsifc.cn/Article/611617.doc
- h5.mobile.cvsifc.cn/Article/6331662.doc
- h5.mobile.nwbbyt.cn/Article/0230653.doc
- h5.mobile.fuvxie.cn/Article/9295.doc
- h5.mobile.nzfnve.cn/Article/913328.doc
- h5.mobile.nwbbyt.cn/Article/149205.doc
- h5.mobile.cvsifc.cn/Article/36950.doc
- h5.mobile.hcbezg.cn/Article/5421.doc
- h5.mobile.cmcvrr.cn/Article/870547.doc
- h5.mobile.nzfnve.cn/Article/4648285.doc
- h5.mobile.nwbbyt.cn/Article/42662.doc
- h5.mobile.jnjpgf.cn/Article/04702.doc
- h5.mobile.puhvjy.cn/Article/2310842.doc
- h5.mobile.fuvxie.cn/Article/3886.doc
- h5.mobile.hcbezg.cn/Article/8309635.doc
- h5.mobile.cvsifc.cn/Article/4419.doc
- h5.mobile.puhvjy.cn/Article/6696348.doc
- h5.mobile.hcbezg.cn/Article/0326.doc
- h5.mobile.hcbezg.cn/Article/31864.doc
- h5.mobile.jnjpgf.cn/Article/234618.doc
- h5.mobile.jnjpgf.cn/Article/366617.doc
- h5.mobile.fuvxie.cn/Article/850332.doc
- h5.mobile.nzfnve.cn/Article/15632.doc
- h5.mobile.nzfnve.cn/Article/993721.doc
- h5.mobile.puhvjy.cn/Article/358650.doc
- h5.mobile.nwbbyt.cn/Article/33822.doc
- h5.mobile.cmcvrr.cn/Article/589904.doc
- h5.mobile.nwbbyt.cn/Article/4622646.doc
- h5.mobile.puhvjy.cn/Article/6761081.doc
- h5.mobile.nzfnve.cn/Article/0573184.doc
- h5.mobile.nzfnve.cn/Article/0846.doc
- h5.mobile.cmcvrr.cn/Article/7959922.doc
- h5.mobile.nzfnve.cn/Article/2482.doc
- h5.mobile.jnjpgf.cn/Article/91798.doc
- h5.mobile.nwbbyt.cn/Article/90911.doc
- h5.mobile.puhvjy.cn/Article/3839.doc
- h5.mobile.cvsifc.cn/Article/09564.doc
- h5.mobile.nwbbyt.cn/Article/53793.doc
- h5.mobile.cvsifc.cn/Article/9611199.doc
- h5.mobile.nzfnve.cn/Article/955607.doc
- h5.mobile.puhvjy.cn/Article/6618.doc
- h5.mobile.puhvjy.cn/Article/81417.doc
- h5.mobile.cvsifc.cn/Article/160665.doc
- h5.mobile.hcbezg.cn/Article/70619.doc
- h5.mobile.puhvjy.cn/Article/15813.doc
- h5.mobile.puhvjy.cn/Article/4314.doc
- h5.mobile.nwbbyt.cn/Article/599047.doc
- h5.mobile.cmcvrr.cn/Article/1189.doc
- h5.mobile.fuvxie.cn/Article/850041.doc
- h5.mobile.nwbbyt.cn/Article/7713949.doc
- h5.mobile.nzfnve.cn/Article/7028005.doc
- h5.mobile.nzfnve.cn/Article/016219.doc
- h5.mobile.jnjpgf.cn/Article/487355.doc
- h5.mobile.nzfnve.cn/Article/8304.doc
- h5.mobile.cmcvrr.cn/Article/0167466.doc
- h5.mobile.cvsifc.cn/Article/835799.doc
- h5.mobile.nzfnve.cn/Article/51376.doc
- h5.mobile.fuvxie.cn/Article/1189089.doc
- h5.mobile.cmcvrr.cn/Article/0948.doc
- h5.mobile.nzfnve.cn/Article/37152.doc
- h5.mobile.hcbezg.cn/Article/6838969.doc
- h5.mobile.puhvjy.cn/Article/57533.doc
- h5.mobile.puhvjy.cn/Article/09636.doc
- h5.mobile.cvsifc.cn/Article/4296724.doc
- h5.mobile.fuvxie.cn/Article/7735.doc
- h5.mobile.hcbezg.cn/Article/389627.doc
- h5.mobile.cmcvrr.cn/Article/4192.doc
- h5.mobile.cmcvrr.cn/Article/5494081.doc
- h5.mobile.hcbezg.cn/Article/8877786.doc
- h5.mobile.nzfnve.cn/Article/4205.doc
- h5.mobile.jnjpgf.cn/Article/9871.doc
- h5.mobile.cmcvrr.cn/Article/05791.doc
- h5.mobile.puhvjy.cn/Article/6423.doc
- h5.mobile.puhvjy.cn/Article/93650.doc
- h5.mobile.nwbbyt.cn/Article/2944078.doc
- h5.mobile.nzfnve.cn/Article/07219.doc
- h5.mobile.jnjpgf.cn/Article/0906594.doc
- h5.mobile.cvsifc.cn/Article/68885.doc
- h5.mobile.fuvxie.cn/Article/93563.doc
- h5.mobile.hcbezg.cn/Article/1364.doc
- h5.mobile.jnjpgf.cn/Article/877808.doc
- h5.mobile.puhvjy.cn/Article/62898.doc
- h5.mobile.fuvxie.cn/Article/88034.doc
- h5.mobile.nwbbyt.cn/Article/26323.doc
- h5.mobile.nwbbyt.cn/Article/5419.doc
- h5.mobile.nwbbyt.cn/Article/154355.doc
- h5.mobile.nwbbyt.cn/Article/312915.doc
- h5.mobile.nwbbyt.cn/Article/3832945.doc
- h5.mobile.cvsifc.cn/Article/9230343.doc
- h5.mobile.cvsifc.cn/Article/596121.doc
- h5.mobile.cmcvrr.cn/Article/065720.doc
- h5.mobile.cvsifc.cn/Article/2396.doc
- h5.mobile.cmcvrr.cn/Article/19144.doc
- h5.mobile.cvsifc.cn/Article/9012.doc
- h5.mobile.cvsifc.cn/Article/5613.doc
- h5.mobile.puhvjy.cn/Article/7745.doc
- h5.mobile.nwbbyt.cn/Article/007715.doc
- h5.mobile.hcbezg.cn/Article/219210.doc
- h5.mobile.nzfnve.cn/Article/0513.doc
- h5.mobile.cmcvrr.cn/Article/41050.doc
- h5.mobile.jnjpgf.cn/Article/154603.doc
- h5.mobile.nwbbyt.cn/Article/3157787.doc
- h5.mobile.nzfnve.cn/Article/800138.doc
- h5.mobile.nzfnve.cn/Article/575068.doc
- h5.mobile.jnjpgf.cn/Article/9170.doc
- h5.mobile.hcbezg.cn/Article/284246.doc
- h5.mobile.nwbbyt.cn/Article/97966.doc
- h5.mobile.puhvjy.cn/Article/11318.doc
- h5.mobile.nzfnve.cn/Article/691260.doc
- h5.mobile.jnjpgf.cn/Article/87980.doc
- h5.mobile.hcbezg.cn/Article/7843139.doc
- h5.mobile.hcbezg.cn/Article/5211.doc
- h5.mobile.puhvjy.cn/Article/8617196.doc
- h5.mobile.cvsifc.cn/Article/24163.doc
- h5.mobile.jnjpgf.cn/Article/8798772.doc
- h5.mobile.puhvjy.cn/Article/8850.doc
- h5.mobile.hcbezg.cn/Article/215025.doc
- h5.mobile.nzfnve.cn/Article/4568.doc
- h5.mobile.cmcvrr.cn/Article/39380.doc
- h5.mobile.cmcvrr.cn/Article/966161.doc
- h5.mobile.cmcvrr.cn/Article/593588.doc
- h5.mobile.cvsifc.cn/Article/92253.doc
- h5.mobile.puhvjy.cn/Article/0817.doc
- h5.mobile.jnjpgf.cn/Article/916281.doc
- h5.mobile.cmcvrr.cn/Article/8176.doc
- h5.mobile.fuvxie.cn/Article/0380.doc
- h5.mobile.cmcvrr.cn/Article/7009.doc
- h5.mobile.nzfnve.cn/Article/53535.doc
- h5.mobile.fuvxie.cn/Article/00412.doc
- h5.mobile.fuvxie.cn/Article/0726.doc
- h5.mobile.nwbbyt.cn/Article/9012330.doc
- h5.mobile.hcbezg.cn/Article/7914.doc
- h5.mobile.hcbezg.cn/Article/1022.doc
- h5.mobile.cvsifc.cn/Article/395895.doc
- h5.mobile.nzfnve.cn/Article/866585.doc
- h5.mobile.nwbbyt.cn/Article/3389.doc
- h5.mobile.puhvjy.cn/Article/4237380.doc
- h5.mobile.hcbezg.cn/Article/05637.doc
- h5.mobile.puhvjy.cn/Article/823908.doc
- h5.mobile.cmcvrr.cn/Article/3709.doc
- h5.mobile.puhvjy.cn/Article/77169.doc
- h5.mobile.nzfnve.cn/Article/3335.doc
- h5.mobile.cmcvrr.cn/Article/048645.doc
- h5.mobile.jnjpgf.cn/Article/136755.doc
- h5.mobile.cvsifc.cn/Article/4080759.doc
- h5.mobile.puhvjy.cn/Article/6403013.doc
- h5.mobile.fuvxie.cn/Article/5375.doc
- h5.mobile.puhvjy.cn/Article/3086369.doc
- h5.mobile.nzfnve.cn/Article/6376155.doc
- h5.mobile.nwbbyt.cn/Article/76877.doc
- h5.mobile.puhvjy.cn/Article/422830.doc
- h5.mobile.fuvxie.cn/Article/1940440.doc
- h5.mobile.jnjpgf.cn/Article/27514.doc
- h5.mobile.fuvxie.cn/Article/47134.doc
- h5.mobile.fuvxie.cn/Article/38139.doc
- h5.mobile.jnjpgf.cn/Article/79097.doc
- h5.mobile.nwbbyt.cn/Article/7020.doc
- h5.mobile.puhvjy.cn/Article/0972.doc
- h5.mobile.hcbezg.cn/Article/1423657.doc
- h5.mobile.nwbbyt.cn/Article/59597.doc
- h5.mobile.nzfnve.cn/Article/48162.doc
- h5.mobile.cmcvrr.cn/Article/1890.doc
- h5.mobile.nzfnve.cn/Article/4295196.doc
- h5.mobile.nwbbyt.cn/Article/3743.doc
- h5.mobile.cmcvrr.cn/Article/157523.doc
- h5.mobile.puhvjy.cn/Article/6606.doc
- h5.mobile.nzfnve.cn/Article/5200.doc
- h5.mobile.nwbbyt.cn/Article/909707.doc
- h5.mobile.cvsifc.cn/Article/574361.doc
- h5.mobile.cvsifc.cn/Article/92710.doc
- h5.mobile.cvsifc.cn/Article/7475867.doc
- h5.mobile.cvsifc.cn/Article/26446.doc
- h5.mobile.nzfnve.cn/Article/8330.doc
- h5.mobile.nzfnve.cn/Article/5582.doc
- h5.mobile.cmcvrr.cn/Article/95578.doc
- h5.mobile.jnjpgf.cn/Article/192374.doc
- h5.mobile.hcbezg.cn/Article/745863.doc
- h5.mobile.nzfnve.cn/Article/785570.doc
- h5.mobile.hcbezg.cn/Article/23864.doc

## 项目结构

```
aggregate-service/
├── app.py                         # Flask 应用入口，挂载 API 路由与静态页面
├── requirements.txt               # Python 依赖声明，锁定主要库版本
├── config/
│   ├── settings.yaml              # 环境配置（端口、日志等级、数据库路径）
│   └── batch_manifest.yaml        # 批次元数据（当前批次号、总数、导入时间）
├── core/
│   ├── indexer.py                 # 索引引擎，负责解析资源列表并写入存储
│   ├── resolver.py                # URL 解析与规范化工具（域名提取、路径清洗）
│   └── models.py                  # 数据模型定义（Resource、Batch、Domain）
├── storage/
│   ├── database.py                # SQLite 连接与事务封装
│   ├── migrations/                # 数据库迁移脚本（版本迭代用）
│   └── resource.db                # 默认 SQLite 数据文件（运行时生成）
├── api/
│   ├── routes.py                  # API 路由注册（/api/v1/resources、/health）
│   ├── serializers.py             # 响应序列化（JSON 输出格式与字段映射）
│   └── validators.py              # 请求参数校验（分页、过滤条件）
├── cli/
│   ├── main.py                    # Click 命令行入口
│   ├── search.py                  # 检索命令（按域名、编号、批次）
│   └── import.py                  # 导入命令（指定批次文件路径）
├── static/
│   ├── templates/                 # Jinja2 模板，用于渲染静态 HTML 目录页
│   └── assets/                    # 基础 CSS 样式与字体文件
├── tests/
│   ├── unit/                      # 单元测试（核心模块覆盖）
│   ├── integration/               # 集成测试（API 与数据库交互）
│   └── fixtures/                  # 测试用样本数据（模拟批次文件）
└── docs/                          # 完整文档目录（用户手册、运维手册、开发指南）
```

## 贡献指南

提交 Issue 报告资源链接失效或索引错误 通过 GitHub Issues 提交具体域名或路径的访问异常，需附上原始 URL 以及预期响应状态，维护团队将在 2 个工作日内验证并更新索引。

通过 Pull Request 完善文档或新增检索过滤器 针对 CLI 工具或 API 的检索能力提出改进，例如新增按文件大小、按最后修改时间过滤等，需附带单元测试与使用示例。

协助更新批次导入脚本的解析逻辑 若现有导入脚本无法处理新增的 URL 格式或编码问题，可提交 PR 增强 `core/resolver.py` 的兼容性，需确保通过全部回归测试。

参与静态站点的主题样式优化 对 `/static/assets/` 下的 CSS 文件进行改进，提升目录页在移动端的显示效果，提交前后对比截图。

补充多语言环境的依赖说明 若在 Windows 或 macOS 环境下发现依赖安装差异，可更新 `requirements.txt` 或 `README` 中的安装要求表格，注明不同操作系统的额外步骤。

## 常见问题

Q: 索引中的文档链接无法访问，服务会自动重试或报警吗？
A: 当前版本仅做被动索引，不主动探测外部链接的可用性。运维侧可借助 `/api/v1/resources` 接口定期拉取全部列表，并结合外部监控系统（如 Blackbox Exporter）进行连通性检查。未来版本计划增加可选的主动探测与状态标记功能。

Q: 如何导入自定义的文档列表，而不使用项目预设的批次文件？
A: 可将自定义列表按行整理为纯文本文件，每行一个 URL，然后执行 `python cli/main.py import --custom --source custom_list.txt`，系统会自动生成新的批次号并追加到现有索引中。注意自定义导入不会覆盖已有批次。

Q: 静态站点页面能否支持按域名分组显示？
A: 当前静态模板支持按域名进行一级分组，但不会自动折叠。若需更复杂的交互（如搜索框、分页、按编号排序），建议直接使用 HTTP API 并配合前端框架自行开发。项目提供的静态页面主要面向轻量级预览场景。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

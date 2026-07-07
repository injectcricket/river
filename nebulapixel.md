# DocLink Aggregate Server (DLAS)

DocLink Aggregate Server 是一个面向技术文档与外部资源链接的集中式汇总与管理平台。该项目定位于解决开发团队、技术研究者以及内容运营者在处理分散、多源、海量外部文档链接时所面临的检索效率低下、链接失效不可知、分类混乱等实际问题。DLAS 不提供文档内容的存储或编辑功能，而是作为一个高可信度的外部资源索引与导航中枢，通过结构化的数据组织与状态监控，帮助用户将零散的外部 .doc 资源转化为可管理、可追溯、可审计的知识资产。

目标用户包括需要维护大量外部参考文档的研发团队、从事技术信息聚合的内容运营人员、以及需要快速定位特定编号文档的研究与运维工程师。项目采用静态索引与动态状态检查相结合的设计，确保资源列表的长期可用性与可访问性。

## 功能概览

批量资源导入：支持通过标准输入或结构化配置文件批量录入外部文档 URL，自动解析域名与资源路径，建立基础索引。

链接状态监控：定期对已收录的 URL 执行可用性探测，记录响应状态码与访问延迟，标注异常链接。

多维度检索：基于文档编号、来源域名、文件类型、收录批次与时间范围进行精确或模糊查询。

分类标签管理：允许用户为每个资源链接添加自定义标签，实现按主题、项目或部门维度的分类聚合。

访问统计报告：生成资源访问频次、域名分布、状态码分布等统计报表，辅助运营决策。

数据导入导出：支持将索引数据导出为 CSV 或 JSON 格式，便于与其他内部系统集成。

权限与审计：基于角色的访问控制，记录所有查询与修改操作日志，满足内部合规要求。

## 应用场景

研发团队知识库构建：技术团队在项目开发过程中积累了大量外部参考文档的链接，如技术规范、接口说明、故障案例等。DLAS 可作为这些链接的统一入口，团队成员通过关键词或文档编号快速检索所需资源，避免重复查找与链接丢失。

文档链接健康巡检：内容运营人员定期需要验证对外发布的文档链接是否仍然有效。DLAS 的自动状态监控功能可按每日或每周频率检测所有收录的 URL，自动生成失效链接清单，便于及时更新或替换。

多项目资源隔离与共享：同一组织内不同项目组可能引用相同的公共技术文档。DLAS 通过标签与分类机制，使各项目组既能共享公共资源池，又能维护各自专属的资源列表，避免重复录入。

外部审计与合规追溯：对于需要接受外部审计的行业，如金融或医疗，所有引用的外部文档来源需可追溯。DLAS 的审计日志与完整资源列表提供了清晰的引用记录，满足合规审查对来源可溯性的要求。

## 快速开始

以下步骤指导您在本机环境中快速部署并运行 DLAS 服务。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/dlas.git

# 进入项目目录
cd dlas

# 安装项目依赖（基于 Python 3.10+）
pip install -r requirements.txt

# 初始化本地配置文件
cp config.example.yaml config.yaml

# 执行数据库迁移
python manage.py migrate

# 启动开发服务器
python manage.py runserver --host 0.0.0.0 --port 8080
```

服务启动后，可通过浏览器访问 `http://localhost:8080` 查看 Web 管理界面，或通过 REST API 端点 `http://localhost:8080/api/v1/` 进行程序化访问。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 或更高 | 核心运行环境，推荐使用 3.11 以获得更好性能 |
| PostgreSQL | 14.0 或更高 | 主数据库，存储资源索引、标签、审计日志等结构化数据 |
| Redis | 6.2 或更高 | 用于缓存频繁查询结果与临时存储任务队列状态 |
| Node.js | 18.0 或更高 | 仅用于前端构建工具链，生产环境可仅部署构建产物 |
| Nginx | 1.20 或更高 | 生产环境推荐的反向代理与静态文件服务 |
| Git | 2.25 或更高 | 用于版本控制与后续自动更新 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/ | 如何使用 Web 界面进行资源检索、标签管理与状态查看 |
| 管理员指南 | /docs/admin-guide/ | 如何配置链接探测策略、管理用户权限与系统调优 |
| API 参考 | /docs/api-reference/ | RESTful API 的端点说明、请求参数与响应结构 |
| 架构设计 | /docs/architecture/ | 系统的模块划分、数据流与扩展性设计说明 |
| 运维手册 | /docs/ops/ | 生产环境部署、日志采集、监控告警与备份恢复方案 |

## 资源列表

- h5.mobile.cmcvrr.cn/Article/507953.doc
- h5.mobile.nwbbyt.cn/Article/936745.doc
- h5.mobile.fuvxie.cn/Article/36581.doc
- h5.mobile.hcbezg.cn/Article/29828.doc
- h5.mobile.hcbezg.cn/Article/900287.doc
- h5.mobile.nwbbyt.cn/Article/5994.doc
- h5.mobile.cmcvrr.cn/Article/2766559.doc
- h5.mobile.jnjpgf.cn/Article/94626.doc
- h5.mobile.cvsifc.cn/Article/765480.doc
- h5.mobile.nwbbyt.cn/Article/0686385.doc
- h5.mobile.puhvjy.cn/Article/509554.doc
- h5.mobile.nzfnve.cn/Article/9084.doc
- h5.mobile.jnjpgf.cn/Article/23355.doc
- h5.mobile.hcbezg.cn/Article/828240.doc
- h5.mobile.hcbezg.cn/Article/15695.doc
- h5.mobile.puhvjy.cn/Article/962775.doc
- h5.mobile.nwbbyt.cn/Article/728509.doc
- h5.mobile.nwbbyt.cn/Article/7398.doc
- h5.mobile.cmcvrr.cn/Article/0833.doc
- h5.mobile.puhvjy.cn/Article/139888.doc
- h5.mobile.nwbbyt.cn/Article/1964417.doc
- h5.mobile.cvsifc.cn/Article/465337.doc
- h5.mobile.cvsifc.cn/Article/40583.doc
- h5.mobile.fuvxie.cn/Article/3887034.doc
- h5.mobile.fuvxie.cn/Article/0259.doc
- h5.mobile.cvsifc.cn/Article/139530.doc
- h5.mobile.fuvxie.cn/Article/2607245.doc
- h5.mobile.fuvxie.cn/Article/49423.doc
- h5.mobile.nzfnve.cn/Article/456308.doc
- h5.mobile.fuvxie.cn/Article/514072.doc
- h5.mobile.cmcvrr.cn/Article/824525.doc
- h5.mobile.cvsifc.cn/Article/64939.doc
- h5.mobile.cmcvrr.cn/Article/81609.doc
- h5.mobile.cmcvrr.cn/Article/35511.doc
- h5.mobile.puhvjy.cn/Article/1573.doc
- h5.mobile.nwbbyt.cn/Article/86098.doc
- h5.mobile.puhvjy.cn/Article/9848.doc
- h5.mobile.puhvjy.cn/Article/54062.doc
- h5.mobile.cvsifc.cn/Article/9469507.doc
- h5.mobile.cvsifc.cn/Article/197246.doc
- h5.mobile.jnjpgf.cn/Article/08506.doc
- h5.mobile.hcbezg.cn/Article/25309.doc
- h5.mobile.cvsifc.cn/Article/562775.doc
- h5.mobile.fuvxie.cn/Article/41844.doc
- h5.mobile.puhvjy.cn/Article/2276087.doc
- h5.mobile.cmcvrr.cn/Article/5078.doc
- h5.mobile.nzfnve.cn/Article/4365.doc
- h5.mobile.nzfnve.cn/Article/2150.doc
- h5.mobile.nzfnve.cn/Article/9316.doc
- h5.mobile.cmcvrr.cn/Article/427922.doc
- h5.mobile.nwbbyt.cn/Article/147618.doc
- h5.mobile.cmcvrr.cn/Article/26649.doc
- h5.mobile.nzfnve.cn/Article/37328.doc
- h5.mobile.puhvjy.cn/Article/5589381.doc
- h5.mobile.jnjpgf.cn/Article/7335183.doc
- h5.mobile.hcbezg.cn/Article/3636.doc
- h5.mobile.nzfnve.cn/Article/055926.doc
- h5.mobile.cvsifc.cn/Article/8636148.doc
- h5.mobile.nzfnve.cn/Article/76260.doc
- h5.mobile.nwbbyt.cn/Article/663583.doc
- h5.mobile.hcbezg.cn/Article/5078494.doc
- h5.mobile.jnjpgf.cn/Article/318411.doc
- h5.mobile.nzfnve.cn/Article/3165.doc
- h5.mobile.fuvxie.cn/Article/7393414.doc
- h5.mobile.cvsifc.cn/Article/1639.doc
- h5.mobile.hcbezg.cn/Article/10756.doc
- h5.mobile.cvsifc.cn/Article/9504779.doc
- h5.mobile.nwbbyt.cn/Article/30862.doc
- h5.mobile.cmcvrr.cn/Article/5540072.doc
- h5.mobile.puhvjy.cn/Article/430835.doc
- h5.mobile.cmcvrr.cn/Article/98192.doc
- h5.mobile.fuvxie.cn/Article/72150.doc
- h5.mobile.puhvjy.cn/Article/55429.doc
- h5.mobile.hcbezg.cn/Article/499884.doc
- h5.mobile.cvsifc.cn/Article/197420.doc
- h5.mobile.cmcvrr.cn/Article/3057.doc
- h5.mobile.jnjpgf.cn/Article/7387.doc
- h5.mobile.nwbbyt.cn/Article/474224.doc
- h5.mobile.fuvxie.cn/Article/6472824.doc
- h5.mobile.jnjpgf.cn/Article/1930.doc
- h5.mobile.nzfnve.cn/Article/56962.doc
- h5.mobile.fuvxie.cn/Article/3045914.doc
- h5.mobile.nwbbyt.cn/Article/0025.doc
- h5.mobile.puhvjy.cn/Article/0275930.doc
- h5.mobile.nwbbyt.cn/Article/93366.doc
- h5.mobile.fuvxie.cn/Article/855803.doc
- h5.mobile.cvsifc.cn/Article/0376.doc
- h5.mobile.cvsifc.cn/Article/51843.doc
- h5.mobile.puhvjy.cn/Article/4386183.doc
- h5.mobile.jnjpgf.cn/Article/6757015.doc
- h5.mobile.cmcvrr.cn/Article/423649.doc
- h5.mobile.nzfnve.cn/Article/4563701.doc
- h5.mobile.jnjpgf.cn/Article/597983.doc
- h5.mobile.nwbbyt.cn/Article/3419.doc
- h5.mobile.hcbezg.cn/Article/367576.doc
- h5.mobile.cvsifc.cn/Article/128679.doc
- h5.mobile.puhvjy.cn/Article/1220047.doc
- h5.mobile.cvsifc.cn/Article/057948.doc
- h5.mobile.fuvxie.cn/Article/67591.doc
- h5.mobile.cmcvrr.cn/Article/769085.doc
- h5.mobile.puhvjy.cn/Article/85693.doc
- h5.mobile.fuvxie.cn/Article/7411974.doc
- h5.mobile.jnjpgf.cn/Article/7169722.doc
- h5.mobile.nzfnve.cn/Article/87099.doc
- h5.mobile.hcbezg.cn/Article/36250.doc
- h5.mobile.jnjpgf.cn/Article/3114173.doc
- h5.mobile.jnjpgf.cn/Article/1853001.doc
- h5.mobile.nzfnve.cn/Article/11130.doc
- h5.mobile.puhvjy.cn/Article/8930.doc
- h5.mobile.jnjpgf.cn/Article/0987.doc
- h5.mobile.jnjpgf.cn/Article/834292.doc
- h5.mobile.cvsifc.cn/Article/6793.doc
- h5.mobile.jnjpgf.cn/Article/982584.doc
- h5.mobile.cvsifc.cn/Article/948073.doc
- h5.mobile.nwbbyt.cn/Article/5220947.doc
- h5.mobile.cvsifc.cn/Article/357058.doc
- h5.mobile.nwbbyt.cn/Article/037351.doc
- h5.mobile.cvsifc.cn/Article/76257.doc
- h5.mobile.nzfnve.cn/Article/734031.doc
- h5.mobile.cmcvrr.cn/Article/9442.doc
- h5.mobile.nwbbyt.cn/Article/2873885.doc
- h5.mobile.jnjpgf.cn/Article/1343148.doc
- h5.mobile.fuvxie.cn/Article/674193.doc
- h5.mobile.nzfnve.cn/Article/109460.doc
- h5.mobile.nwbbyt.cn/Article/9418.doc
- h5.mobile.puhvjy.cn/Article/6028.doc
- h5.mobile.jnjpgf.cn/Article/7148407.doc
- h5.mobile.cvsifc.cn/Article/0826.doc
- h5.mobile.puhvjy.cn/Article/327739.doc
- h5.mobile.cmcvrr.cn/Article/3413455.doc
- h5.mobile.cvsifc.cn/Article/670570.doc
- h5.mobile.puhvjy.cn/Article/8827.doc
- h5.mobile.cvsifc.cn/Article/6847.doc
- h5.mobile.jnjpgf.cn/Article/607650.doc
- h5.mobile.cvsifc.cn/Article/5186030.doc
- h5.mobile.cmcvrr.cn/Article/112183.doc
- h5.mobile.puhvjy.cn/Article/8493024.doc
- h5.mobile.fuvxie.cn/Article/8237398.doc
- h5.mobile.cmcvrr.cn/Article/364633.doc
- h5.mobile.cvsifc.cn/Article/803262.doc
- h5.mobile.nwbbyt.cn/Article/6727.doc
- h5.mobile.jnjpgf.cn/Article/89192.doc
- h5.mobile.cvsifc.cn/Article/1926319.doc
- h5.mobile.puhvjy.cn/Article/643907.doc
- h5.mobile.fuvxie.cn/Article/3716.doc
- h5.mobile.cmcvrr.cn/Article/0683773.doc
- h5.mobile.hcbezg.cn/Article/965166.doc
- h5.mobile.cmcvrr.cn/Article/5382131.doc
- h5.mobile.fuvxie.cn/Article/26814.doc
- h5.mobile.hcbezg.cn/Article/9195.doc
- h5.mobile.cmcvrr.cn/Article/2951486.doc
- h5.mobile.nwbbyt.cn/Article/05040.doc
- h5.mobile.cvsifc.cn/Article/16748.doc
- h5.mobile.fuvxie.cn/Article/0199.doc
- h5.mobile.puhvjy.cn/Article/910519.doc
- h5.mobile.cmcvrr.cn/Article/8004432.doc
- h5.mobile.cmcvrr.cn/Article/2771293.doc
- h5.mobile.nzfnve.cn/Article/2788466.doc
- h5.mobile.nzfnve.cn/Article/2116.doc
- h5.mobile.cvsifc.cn/Article/672776.doc
- h5.mobile.nwbbyt.cn/Article/62428.doc
- h5.mobile.nwbbyt.cn/Article/93599.doc
- h5.mobile.puhvjy.cn/Article/7745091.doc
- h5.mobile.jnjpgf.cn/Article/170650.doc
- h5.mobile.puhvjy.cn/Article/5905.doc
- h5.mobile.hcbezg.cn/Article/5822.doc
- h5.mobile.cvsifc.cn/Article/093013.doc
- h5.mobile.cmcvrr.cn/Article/6487227.doc
- h5.mobile.nzfnve.cn/Article/7944.doc
- h5.mobile.cmcvrr.cn/Article/1605.doc
- h5.mobile.nwbbyt.cn/Article/86559.doc
- h5.mobile.jnjpgf.cn/Article/81105.doc
- h5.mobile.cmcvrr.cn/Article/8898286.doc
- h5.mobile.nwbbyt.cn/Article/5457356.doc
- h5.mobile.nwbbyt.cn/Article/10164.doc
- h5.mobile.cmcvrr.cn/Article/0837901.doc
- h5.mobile.jnjpgf.cn/Article/7870.doc
- h5.mobile.nzfnve.cn/Article/92865.doc
- h5.mobile.cvsifc.cn/Article/46240.doc
- h5.mobile.cvsifc.cn/Article/71069.doc
- h5.mobile.hcbezg.cn/Article/366688.doc
- h5.mobile.nzfnve.cn/Article/11210.doc
- h5.mobile.fuvxie.cn/Article/40444.doc
- h5.mobile.puhvjy.cn/Article/8068006.doc
- h5.mobile.cmcvrr.cn/Article/10189.doc
- h5.mobile.cvsifc.cn/Article/2304095.doc
- h5.mobile.nwbbyt.cn/Article/4184.doc
- h5.mobile.nwbbyt.cn/Article/685736.doc
- h5.mobile.jnjpgf.cn/Article/17555.doc
- h5.mobile.nwbbyt.cn/Article/0703.doc
- h5.mobile.hcbezg.cn/Article/3271711.doc
- h5.mobile.nzfnve.cn/Article/3712.doc
- h5.mobile.cvsifc.cn/Article/3292.doc
- h5.mobile.hcbezg.cn/Article/4263.doc
- h5.mobile.jnjpgf.cn/Article/8668925.doc
- h5.mobile.puhvjy.cn/Article/698006.doc
- h5.mobile.cmcvrr.cn/Article/61339.doc
- h5.mobile.puhvjy.cn/Article/908844.doc
- h5.mobile.puhvjy.cn/Article/390429.doc
- h5.mobile.cvsifc.cn/Article/6930184.doc
- h5.mobile.puhvjy.cn/Article/997122.doc
- h5.mobile.cmcvrr.cn/Article/0278.doc
- h5.mobile.nzfnve.cn/Article/0630.doc
- h5.mobile.puhvjy.cn/Article/804527.doc
- h5.mobile.nzfnve.cn/Article/3215565.doc
- h5.mobile.puhvjy.cn/Article/3294.doc
- h5.mobile.nzfnve.cn/Article/2152872.doc
- h5.mobile.cvsifc.cn/Article/17158.doc
- h5.mobile.cmcvrr.cn/Article/042330.doc
- h5.mobile.jnjpgf.cn/Article/935256.doc
- h5.mobile.puhvjy.cn/Article/4212188.doc
- h5.mobile.jnjpgf.cn/Article/0834871.doc
- h5.mobile.puhvjy.cn/Article/3864850.doc
- h5.mobile.jnjpgf.cn/Article/2908446.doc
- h5.mobile.hcbezg.cn/Article/669790.doc
- h5.mobile.nwbbyt.cn/Article/389261.doc
- h5.mobile.nwbbyt.cn/Article/78206.doc
- h5.mobile.jnjpgf.cn/Article/70299.doc
- h5.mobile.fuvxie.cn/Article/7303.doc
- h5.mobile.jnjpgf.cn/Article/8021932.doc
- h5.mobile.jnjpgf.cn/Article/9653.doc
- h5.mobile.hcbezg.cn/Article/535276.doc
- h5.mobile.hcbezg.cn/Article/3534523.doc
- h5.mobile.nzfnve.cn/Article/1008.doc
- h5.mobile.cvsifc.cn/Article/777522.doc
- h5.mobile.nzfnve.cn/Article/2705544.doc
- h5.mobile.nzfnve.cn/Article/7453766.doc
- h5.mobile.cvsifc.cn/Article/97673.doc
- h5.mobile.nwbbyt.cn/Article/73740.doc
- h5.mobile.cmcvrr.cn/Article/2542357.doc
- h5.mobile.cvsifc.cn/Article/693790.doc
- h5.mobile.cvsifc.cn/Article/50208.doc
- h5.mobile.nzfnve.cn/Article/5763.doc
- h5.mobile.hcbezg.cn/Article/3828425.doc
- h5.mobile.puhvjy.cn/Article/188369.doc
- h5.mobile.cvsifc.cn/Article/7755927.doc
- h5.mobile.nwbbyt.cn/Article/2448.doc
- h5.mobile.cmcvrr.cn/Article/02916.doc
- h5.mobile.jnjpgf.cn/Article/0396801.doc
- h5.mobile.cmcvrr.cn/Article/9604173.doc
- h5.mobile.cvsifc.cn/Article/5368842.doc
- h5.mobile.cmcvrr.cn/Article/0216.doc
- h5.mobile.jnjpgf.cn/Article/4320407.doc
- h5.mobile.fuvxie.cn/Article/3122340.doc
- h5.mobile.nzfnve.cn/Article/54507.doc
- h5.mobile.hcbezg.cn/Article/313747.doc
- h5.mobile.fuvxie.cn/Article/9955.doc
- h5.mobile.jnjpgf.cn/Article/3932432.doc
- h5.mobile.jnjpgf.cn/Article/1862331.doc
- h5.mobile.puhvjy.cn/Article/8413159.doc

## 项目结构

```
dlas/
├── cmd/                                 # 命令行入口与工具脚本
│   ├── server/                          # Web 服务启动入口
│   │   └── main.go                      # 主服务进程启动逻辑
│   └── tools/                           # 运维辅助工具
│       ├── health_check.go              # 手动触发链接状态检查
│       └── import_batch.go              # 批量导入工具
├── internal/                            # 内部核心实现，不对外暴露
│   ├── core/                            # 核心业务逻辑
│   │   ├── indexer.go                   # 资源索引构建与维护
│   │   ├── checker.go                   # 链接状态探测引擎
│   │   └── query.go                     # 多维度检索实现
│   ├── storage/                         # 数据持久化层
│   │   ├── postgres.go                  # PostgreSQL 数据库操作
│   │   └── cache.go                     # Redis 缓存操作封装
│   └── model/                           # 数据模型定义
│       ├── resource.go                  # 资源实体结构
│       └── audit.go                     # 审计日志实体
├── pkg/                                 # 可被外部引用的公共库
│   ├── api/                             # RESTful API 路由与处理
│   │   ├── handler_v1.go                # v1 版本接口处理器
│   │   └── middleware.go                # 认证与日志中间件
│   └── utils/                           # 通用工具函数
│       ├── validator.go                 # URL 格式校验
│       └── network.go                   # 网络探测辅助
├── web/                                 # 前端静态资源
│   ├── static/                          # 编译后的 CSS/JS 文件
│   └── templates/                       # 后台管理页面模板
├── configs/                             # 配置文件目录
│   ├── config.yaml                      # 主配置文件
│   └── config.example.yaml              # 配置模板示例
├── scripts/                             # 部署与运维脚本
│   ├── setup_db.sh                      # 数据库初始化脚本
│   └── migrate.sh                       # 数据库迁移脚本
├── tests/                               # 单元测试与集成测试
│   ├── unit/                            # 单元测试用例
│   └── integration/                     # 集成测试用例
├── docs/                                # 项目文档
│   ├── user-guide/                      # 用户手册
│   ├── api-reference/                   # API 参考文档
│   └── architecture/                    # 架构设计文档
├── go.mod                               # Go 模块依赖定义
├── go.sum                               # 依赖校验和
└── README.md                            # 项目说明文档
```

## 贡献指南

提交问题报告：请在 GitHub Issues 页面提交您遇到的问题或功能请求。报告问题时，请附上 DLAS 版本号、运行环境（操作系统与依赖版本）、完整的错误日志以及可复现的操作步骤。

代码贡献流程：Fork 本仓库至个人账户，从 main 分支创建新的功能分支，完成代码修改后提交 Pull Request。PR 描述中需明确说明修改目的、涉及的功能模块以及测试覆盖情况。

测试要求：所有新增或修改的代码必须包含对应的单元测试用例。测试覆盖率不应低于当前主分支的基准线。运行 `make test` 可执行全部测试套件。

文档同步更新：任何影响用户使用方式或管理员操作流程的变更，必须同步更新 docs 目录下的对应文档。文档变更应与代码变更在同一 PR 中提交。

审查与合并：所有 PR 需至少两名项目维护者进行代码审查。审查通过后由维护者执行合并操作。合并前需确保所有 CI 检查（包括测试、代码风格检查、安全扫描）均为通过状态。

## 常见问题

Q: 系统支持哪些协议的资源链接探测？

A: 当前版本默认支持 HTTP 和 HTTPS 协议的链接状态探测。对于其他协议（如 FTP），系统将记录为不支持的协议类型，并在状态栏标注为 UNSUPPORTED。用户可通过扩展 checker 模块添加自定义协议支持。

Q: 如何迁移现有的资源列表到 DLAS？

A: 系统提供了批量导入工具 `tools/import_batch`，支持 CSV 和纯文本行格式的输入文件。CSV 格式要求第一列为资源 URL，第二列为可选标签，以逗号分隔。导入前建议使用 `--dry-run` 参数进行预检查，确认数据格式无误后再执行实际导入。

Q: 链接状态检查的频率和超时时间是否可调？

A: 可以。在主配置文件 config.yaml 的 checker 段中，`interval` 参数控制检查间隔（单位小时），`timeout` 参数控制单次探测超时（单位秒）。调整后重启服务即可生效。建议内网环境将超时设置为 3-5 秒，外网环境设置为 10-15 秒。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

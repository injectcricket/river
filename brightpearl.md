# MobileDocs 聚合资源站

MobileDocs 是一个面向移动端开发与内容运营团队的技术文档与资源外链聚合系统。项目定位为轻量级文档索引网关，用于将分散在多个源站（cmcvrr.cn、cvsifc.cn、puhvjy.cn、jnjpgf.cn 等）的 .doc 技术资料、运营报表、产品说明等文件，按照统一 URL 规范进行集中整理与可检索发布。目标用户包括移动端 SDK 集成工程师、产品运营人员、内容合规审核人员以及需要批量访问内部文档体系的企业开发者。MobileDocs 本身不存储文件实体，而是提供稳定的定位符映射与状态检测机制，帮助团队在多人协作场景下快速定位第 90/160 批次的 250 个关键文档资源。

## 功能概览

多源文档定位：基于域名分片策略，将来自 cmcvrr.cn、cvsifc.cn、puhvjy.cn、jnjpgf.cn、nwbbyt.cn、nzfnve.cn、hcbezg.cn、fuvxie.cn 等源站的 .doc 资源统一编入索引表，每个资源均保留原始访问路径。

资源状态检测：周期性对索引中的每条 URL 执行 HEAD 请求，标记可访问、重定向或失效三种状态，并在前端面板中以颜色区分。

模糊检索与筛选：支持按源站域名、文件名数字段、批次号（当前为 90/160）进行组合筛选，也支持对 .doc 文件名中的数字特征做正则匹配查询。

批量导出机制：将筛选后的 URL 列表按自定义格式（纯文本 / CSV / Markdown 列表）导出，方便集成到内部知识库或合规报审材料中。

访问日志审计：记录每个资源链接的被访问时间、来源 IP 属地（聚合级别）和 User-Agent 类型，便于排查异常下载行为。

源站健康看板：以柱状图展示各源站（cmcvrr.cn、cvsifc.cn 等）在当前批次中的文档存活率与平均响应时间，辅助运维决策。

权限分级管理：支持只读访客、编辑者和管理员三级权限，编辑者可修正 URL 别名或补充文档描述，管理员可批量导入下一批次资源。

## 应用场景

移动 SDK 集成文档查阅：开发团队在接入第三方移动组件时，需要频繁查阅不同版本的服务端接口说明文档。通过 MobileDocs 按批次筛选出所有来自 cvsifc.cn 和 puhvjy.cn 的文档链接，可快速定位到所需的接口定义文件。

运营活动内容合规复审：运营人员在活动上线前需批量核对素材说明文档。使用本系统按域名分组导出 jnjpgf.cn 与 nwbbyt.cn 下的所有 .doc 链接，交由法务团队逐条审核，确保引用来源合规。

历史文档迁移校验：在内部文档系统从旧域名迁移至新架构的过程中，需要验证所有历史文档是否仍然可访问。MobileDocs 的状态检测功能可一次性扫描 250 个链接，生成迁移前后的存活对比报告。

跨团队文档引用溯源：技术写作人员编写对外技术白皮书时，需标注每个数据来源的原始文档路径。系统按批次导出完整 URL 列表，可直接粘贴至白皮书附录，避免人工整理遗漏或抄写错误。

## 快速开始

以下步骤帮助您在本地环境快速启动 MobileDocs 实例，完成首批 250 个文档资源的索引加载。

```bash
# 克隆代码仓库
git clone https://github.com/your-org/mobiledocs.git
cd mobiledocs

# 安装依赖（基于 Node.js 22 LTS 与 pnpm）
pnpm install

# 复制环境变量模板并填写检测超时参数
cp .env.example .env

# 初始化 SQLite 数据库并导入当前批次资源列表（含 250 条 .doc URL）
pnpm run migrate
pnpm run seed --batch=90

# 启动开发服务器（默认监听 3000 端口）
pnpm run dev
```

访问 http://localhost:3000 即可进入资源看板，首次启动将自动对全部 250 条链接执行存活检测，耗时约 30 至 60 秒。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | 22.12.0 LTS 或更高 | 运行时环境，建议使用 nvm 管理版本 |
| pnpm | 9.0.0 或更高 | 包管理器，用于安装依赖与执行脚本 |
| SQLite | 3.45.0 或更高 | 嵌入式数据库，存储资源索引与状态 |
| curl / wget | 任意现代版本 | 用于外部健康检测命令（可选降级方案） |
| 系统内存 | 最低 512 MB，推荐 1 GB | 运行检测任务时的内存占用 |
| 网络访问 | 需能访问 h5.mobile.*.cn 域名段 | 用于执行实际资源状态检查 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | /docs/getting-started.md | 如何安装、配置并启动系统；如何导入第 90/160 批资源 |
| 资源管理 | /docs/resource-management.md | 如何新增/删除/修改资源链接；如何处理失效文档 |
| 检测机制 | /docs/health-check.md | 检测策略（间隔、并发数、超时设置）；如何解读状态码 |
| 导出与集成 | /docs/export-integration.md | 支持哪些导出格式；如何通过 API 批量拉取资源列表 |

## 资源列表

- h5.mobile.fuvxie.cn/Article/84546.doc
- h5.mobile.cmcvrr.cn/Article/6658.doc
- h5.mobile.nwbbyt.cn/Article/62332.doc
- h5.mobile.cvsifc.cn/Article/757167.doc
- h5.mobile.puhvjy.cn/Article/5252.doc
- h5.mobile.cmcvrr.cn/Article/1569.doc
- h5.mobile.cvsifc.cn/Article/518827.doc
- h5.mobile.puhvjy.cn/Article/464807.doc
- h5.mobile.puhvjy.cn/Article/63969.doc
- h5.mobile.cvsifc.cn/Article/5842045.doc
- h5.mobile.puhvjy.cn/Article/6276.doc
- h5.mobile.puhvjy.cn/Article/961526.doc
- h5.mobile.jnjpgf.cn/Article/48925.doc
- h5.mobile.cvsifc.cn/Article/4053035.doc
- h5.mobile.nzfnve.cn/Article/725576.doc
- h5.mobile.jnjpgf.cn/Article/88177.doc
- h5.mobile.cvsifc.cn/Article/0040.doc
- h5.mobile.cvsifc.cn/Article/94606.doc
- h5.mobile.hcbezg.cn/Article/2860.doc
- h5.mobile.nzfnve.cn/Article/241511.doc
- h5.mobile.jnjpgf.cn/Article/51484.doc
- h5.mobile.hcbezg.cn/Article/88375.doc
- h5.mobile.cvsifc.cn/Article/71956.doc
- h5.mobile.cvsifc.cn/Article/0640114.doc
- h5.mobile.jnjpgf.cn/Article/679996.doc
- h5.mobile.nzfnve.cn/Article/6039159.doc
- h5.mobile.cmcvrr.cn/Article/8210.doc
- h5.mobile.nwbbyt.cn/Article/041584.doc
- h5.mobile.jnjpgf.cn/Article/4677.doc
- h5.mobile.nzfnve.cn/Article/075915.doc
- h5.mobile.puhvjy.cn/Article/7012985.doc
- h5.mobile.nwbbyt.cn/Article/9053402.doc
- h5.mobile.nzfnve.cn/Article/88485.doc
- h5.mobile.cmcvrr.cn/Article/9802111.doc
- h5.mobile.hcbezg.cn/Article/6038936.doc
- h5.mobile.cvsifc.cn/Article/8951693.doc
- h5.mobile.fuvxie.cn/Article/72673.doc
- h5.mobile.hcbezg.cn/Article/8311.doc
- h5.mobile.fuvxie.cn/Article/778480.doc
- h5.mobile.cvsifc.cn/Article/5948.doc
- h5.mobile.nzfnve.cn/Article/1241801.doc
- h5.mobile.fuvxie.cn/Article/0424497.doc
- h5.mobile.nwbbyt.cn/Article/37049.doc
- h5.mobile.nzfnve.cn/Article/1646948.doc
- h5.mobile.nzfnve.cn/Article/5850235.doc
- h5.mobile.nzfnve.cn/Article/66040.doc
- h5.mobile.nwbbyt.cn/Article/582962.doc
- h5.mobile.puhvjy.cn/Article/18648.doc
- h5.mobile.cvsifc.cn/Article/722634.doc
- h5.mobile.jnjpgf.cn/Article/0602246.doc
- h5.mobile.cvsifc.cn/Article/10038.doc
- h5.mobile.jnjpgf.cn/Article/10821.doc
- h5.mobile.cvsifc.cn/Article/6234055.doc
- h5.mobile.nzfnve.cn/Article/62297.doc
- h5.mobile.jnjpgf.cn/Article/107473.doc
- h5.mobile.puhvjy.cn/Article/25635.doc
- h5.mobile.hcbezg.cn/Article/0441118.doc
- h5.mobile.jnjpgf.cn/Article/026967.doc
- h5.mobile.jnjpgf.cn/Article/079500.doc
- h5.mobile.cvsifc.cn/Article/976591.doc
- h5.mobile.puhvjy.cn/Article/280130.doc
- h5.mobile.fuvxie.cn/Article/486851.doc
- h5.mobile.puhvjy.cn/Article/471161.doc
- h5.mobile.puhvjy.cn/Article/4224069.doc
- h5.mobile.fuvxie.cn/Article/554952.doc
- h5.mobile.puhvjy.cn/Article/120732.doc
- h5.mobile.cvsifc.cn/Article/86137.doc
- h5.mobile.nwbbyt.cn/Article/7806.doc
- h5.mobile.puhvjy.cn/Article/1547383.doc
- h5.mobile.puhvjy.cn/Article/6101512.doc
- h5.mobile.cvsifc.cn/Article/699312.doc
- h5.mobile.cvsifc.cn/Article/201882.doc
- h5.mobile.nwbbyt.cn/Article/6633938.doc
- h5.mobile.cmcvrr.cn/Article/2178902.doc
- h5.mobile.jnjpgf.cn/Article/4345.doc
- h5.mobile.jnjpgf.cn/Article/5540628.doc
- h5.mobile.hcbezg.cn/Article/8851543.doc
- h5.mobile.cvsifc.cn/Article/6621.doc
- h5.mobile.nzfnve.cn/Article/6511.doc
- h5.mobile.cmcvrr.cn/Article/0905.doc
- h5.mobile.puhvjy.cn/Article/93287.doc
- h5.mobile.hcbezg.cn/Article/0934.doc
- h5.mobile.cmcvrr.cn/Article/33327.doc
- h5.mobile.fuvxie.cn/Article/897733.doc
- h5.mobile.hcbezg.cn/Article/60182.doc
- h5.mobile.fuvxie.cn/Article/5836704.doc
- h5.mobile.nzfnve.cn/Article/587236.doc
- h5.mobile.jnjpgf.cn/Article/19278.doc
- h5.mobile.puhvjy.cn/Article/955842.doc
- h5.mobile.fuvxie.cn/Article/4003918.doc
- h5.mobile.cvsifc.cn/Article/2861543.doc
- h5.mobile.fuvxie.cn/Article/9157.doc
- h5.mobile.nzfnve.cn/Article/8420011.doc
- h5.mobile.nwbbyt.cn/Article/79939.doc
- h5.mobile.nzfnve.cn/Article/48396.doc
- h5.mobile.cmcvrr.cn/Article/826040.doc
- h5.mobile.cmcvrr.cn/Article/35228.doc
- h5.mobile.hcbezg.cn/Article/6521.doc
- h5.mobile.jnjpgf.cn/Article/911026.doc
- h5.mobile.jnjpgf.cn/Article/97546.doc
- h5.mobile.cvsifc.cn/Article/78714.doc
- h5.mobile.fuvxie.cn/Article/07410.doc
- h5.mobile.fuvxie.cn/Article/380403.doc
- h5.mobile.puhvjy.cn/Article/9925.doc
- h5.mobile.fuvxie.cn/Article/5355.doc
- h5.mobile.nzfnve.cn/Article/027173.doc
- h5.mobile.nwbbyt.cn/Article/9009.doc
- h5.mobile.hcbezg.cn/Article/073100.doc
- h5.mobile.puhvjy.cn/Article/18608.doc
- h5.mobile.jnjpgf.cn/Article/5365.doc
- h5.mobile.cmcvrr.cn/Article/779108.doc
- h5.mobile.hcbezg.cn/Article/82230.doc
- h5.mobile.cmcvrr.cn/Article/4845.doc
- h5.mobile.cmcvrr.cn/Article/2921515.doc
- h5.mobile.cvsifc.cn/Article/6498.doc
- h5.mobile.cmcvrr.cn/Article/03838.doc
- h5.mobile.fuvxie.cn/Article/771649.doc
- h5.mobile.fuvxie.cn/Article/03845.doc
- h5.mobile.cmcvrr.cn/Article/1292.doc
- h5.mobile.cvsifc.cn/Article/0045.doc
- h5.mobile.jnjpgf.cn/Article/83785.doc
- h5.mobile.fuvxie.cn/Article/376719.doc
- h5.mobile.nwbbyt.cn/Article/3324808.doc
- h5.mobile.jnjpgf.cn/Article/02457.doc
- h5.mobile.hcbezg.cn/Article/5234021.doc
- h5.mobile.cmcvrr.cn/Article/3410403.doc
- h5.mobile.puhvjy.cn/Article/8601.doc
- h5.mobile.nwbbyt.cn/Article/82341.doc
- h5.mobile.nzfnve.cn/Article/84188.doc
- h5.mobile.hcbezg.cn/Article/6609.doc
- h5.mobile.nzfnve.cn/Article/5649403.doc
- h5.mobile.jnjpgf.cn/Article/6069547.doc
- h5.mobile.cmcvrr.cn/Article/126621.doc
- h5.mobile.nzfnve.cn/Article/1033.doc
- h5.mobile.nzfnve.cn/Article/52649.doc
- h5.mobile.cvsifc.cn/Article/6029554.doc
- h5.mobile.nzfnve.cn/Article/1823932.doc
- h5.mobile.fuvxie.cn/Article/555147.doc
- h5.mobile.cvsifc.cn/Article/7758125.doc
- h5.mobile.puhvjy.cn/Article/99133.doc
- h5.mobile.puhvjy.cn/Article/468533.doc
- h5.mobile.cmcvrr.cn/Article/297823.doc
- h5.mobile.puhvjy.cn/Article/0537739.doc
- h5.mobile.cvsifc.cn/Article/38930.doc
- h5.mobile.nwbbyt.cn/Article/06967.doc
- h5.mobile.nwbbyt.cn/Article/3028866.doc
- h5.mobile.nzfnve.cn/Article/9810.doc
- h5.mobile.jnjpgf.cn/Article/03734.doc
- h5.mobile.hcbezg.cn/Article/61452.doc
- h5.mobile.fuvxie.cn/Article/6712473.doc
- h5.mobile.nwbbyt.cn/Article/8211.doc
- h5.mobile.cmcvrr.cn/Article/5291658.doc
- h5.mobile.hcbezg.cn/Article/860621.doc
- h5.mobile.puhvjy.cn/Article/3882723.doc
- h5.mobile.cmcvrr.cn/Article/7546.doc
- h5.mobile.cvsifc.cn/Article/612315.doc
- h5.mobile.fuvxie.cn/Article/0537933.doc
- h5.mobile.cmcvrr.cn/Article/6384.doc
- h5.mobile.cvsifc.cn/Article/5676432.doc
- h5.mobile.nwbbyt.cn/Article/150652.doc
- h5.mobile.cvsifc.cn/Article/1113.doc
- h5.mobile.jnjpgf.cn/Article/1220.doc
- h5.mobile.cvsifc.cn/Article/06195.doc
- h5.mobile.hcbezg.cn/Article/163266.doc
- h5.mobile.puhvjy.cn/Article/623491.doc
- h5.mobile.nwbbyt.cn/Article/49962.doc
- h5.mobile.cvsifc.cn/Article/87222.doc
- h5.mobile.cvsifc.cn/Article/8787473.doc
- h5.mobile.fuvxie.cn/Article/8591.doc
- h5.mobile.hcbezg.cn/Article/07079.doc
- h5.mobile.nwbbyt.cn/Article/6861.doc
- h5.mobile.puhvjy.cn/Article/1556568.doc
- h5.mobile.cmcvrr.cn/Article/2536837.doc
- h5.mobile.nwbbyt.cn/Article/8469627.doc
- h5.mobile.cvsifc.cn/Article/6121.doc
- h5.mobile.hcbezg.cn/Article/75272.doc
- h5.mobile.nzfnve.cn/Article/7557451.doc
- h5.mobile.cmcvrr.cn/Article/7615.doc
- h5.mobile.cmcvrr.cn/Article/57973.doc
- h5.mobile.hcbezg.cn/Article/239235.doc
- h5.mobile.puhvjy.cn/Article/0830.doc
- h5.mobile.nwbbyt.cn/Article/6111685.doc
- h5.mobile.jnjpgf.cn/Article/49703.doc
- h5.mobile.nwbbyt.cn/Article/3716333.doc
- h5.mobile.puhvjy.cn/Article/372747.doc
- h5.mobile.jnjpgf.cn/Article/2842.doc
- h5.mobile.hcbezg.cn/Article/6530.doc
- h5.mobile.nwbbyt.cn/Article/1728127.doc
- h5.mobile.nwbbyt.cn/Article/4893.doc
- h5.mobile.cmcvrr.cn/Article/22490.doc
- h5.mobile.nzfnve.cn/Article/6709979.doc
- h5.mobile.cmcvrr.cn/Article/0060.doc
- h5.mobile.fuvxie.cn/Article/84877.doc
- h5.mobile.jnjpgf.cn/Article/061313.doc
- h5.mobile.puhvjy.cn/Article/6706.doc
- h5.mobile.fuvxie.cn/Article/9407267.doc
- h5.mobile.nwbbyt.cn/Article/6106882.doc
- h5.mobile.jnjpgf.cn/Article/2329.doc
- h5.mobile.puhvjy.cn/Article/3841210.doc
- h5.mobile.fuvxie.cn/Article/9051.doc
- h5.mobile.fuvxie.cn/Article/928614.doc
- h5.mobile.nzfnve.cn/Article/4731020.doc
- h5.mobile.nzfnve.cn/Article/4211.doc
- h5.mobile.nzfnve.cn/Article/0035339.doc
- h5.mobile.cmcvrr.cn/Article/361286.doc
- h5.mobile.cvsifc.cn/Article/9075995.doc
- h5.mobile.cmcvrr.cn/Article/1901655.doc
- h5.mobile.puhvjy.cn/Article/03198.doc
- h5.mobile.cmcvrr.cn/Article/031821.doc
- h5.mobile.cmcvrr.cn/Article/66502.doc
- h5.mobile.fuvxie.cn/Article/1166.doc
- h5.mobile.puhvjy.cn/Article/5573.doc
- h5.mobile.nzfnve.cn/Article/8486.doc
- h5.mobile.jnjpgf.cn/Article/77804.doc
- h5.mobile.puhvjy.cn/Article/5487161.doc
- h5.mobile.fuvxie.cn/Article/8115.doc
- h5.mobile.puhvjy.cn/Article/6495102.doc
- h5.mobile.jnjpgf.cn/Article/6943415.doc
- h5.mobile.fuvxie.cn/Article/4484.doc
- h5.mobile.nzfnve.cn/Article/4807.doc
- h5.mobile.puhvjy.cn/Article/17250.doc
- h5.mobile.jnjpgf.cn/Article/4765334.doc
- h5.mobile.cmcvrr.cn/Article/30479.doc
- h5.mobile.fuvxie.cn/Article/2810.doc
- h5.mobile.cmcvrr.cn/Article/42191.doc
- h5.mobile.puhvjy.cn/Article/1795.doc
- h5.mobile.hcbezg.cn/Article/194260.doc
- h5.mobile.cmcvrr.cn/Article/4133655.doc
- h5.mobile.nzfnve.cn/Article/3905.doc
- h5.mobile.cmcvrr.cn/Article/4691605.doc
- h5.mobile.cvsifc.cn/Article/3718.doc
- h5.mobile.fuvxie.cn/Article/24822.doc
- h5.mobile.cvsifc.cn/Article/881327.doc
- h5.mobile.puhvjy.cn/Article/10679.doc
- h5.mobile.nzfnve.cn/Article/33452.doc
- h5.mobile.fuvxie.cn/Article/0849.doc
- h5.mobile.jnjpgf.cn/Article/7699447.doc
- h5.mobile.hcbezg.cn/Article/59502.doc
- h5.mobile.cvsifc.cn/Article/0439295.doc
- h5.mobile.fuvxie.cn/Article/286278.doc
- h5.mobile.hcbezg.cn/Article/3329.doc
- h5.mobile.puhvjy.cn/Article/950107.doc
- h5.mobile.fuvxie.cn/Article/4405.doc
- h5.mobile.nzfnve.cn/Article/829608.doc
- h5.mobile.cmcvrr.cn/Article/91704.doc
- h5.mobile.jnjpgf.cn/Article/4468772.doc
- h5.mobile.fuvxie.cn/Article/8726.doc
- h5.mobile.nzfnve.cn/Article/811075.doc
- h5.mobile.puhvjy.cn/Article/8012.doc
- h5.mobile.cvsifc.cn/Article/152310.doc

## 项目结构

```
mobiledocs/
├── src/
│   ├── core/                     # 核心模块：资源索引与状态机
│   │   ├── indexer.ts            # 从外部数据源加载 URL 列表并写入 SQLite
│   │   └── health-checker.ts     # 并发执行 HEAD 请求，更新资源状态
│   ├── api/                      # RESTful API 路由层
│   │   ├── resources.ts          # GET/POST /api/resources 及筛选逻辑
│   │   └── export.ts             # 批量导出接口（text/csv/md）
│   ├── ui/                       # 前端页面组件（React + Tailwind）
│   │   ├── dashboard.tsx         # 总览看板，展示存活率与响应时间
│   │   └── resource-table.tsx    # 资源列表表格，支持筛选与排序
│   ├── lib/                      # 通用工具库
│   │   ├── db.ts                 # SQLite 连接池与查询构造器
│   │   └── logger.ts             # 结构化日志（JSON 格式，含批次号字段）
│   └── types/                    # TypeScript 类型定义
│       └── resource.ts           # Resource 接口（url, source, status, batchId）
├── migrations/                   # 数据库迁移脚本（按时间戳命名）
│   ├── 001_init.sql              # 创建 resources 与 audit_logs 表
│   └── 002_add_batch_index.sql   # 为 batch_id 字段建立索引
├── seeds/                        # 种子数据
│   └── batch_90.json             # 当前第 90/160 批次的 250 条原始 URL
├── tests/                        # 单元测试与集成测试
│   ├── health-checker.test.ts    # 模拟 HEAD 请求与超时重试逻辑
│   └── export.test.ts            # 验证不同导出格式的输出结构
├── docs/                         # 项目文档（参见文档导航章节）
│   ├── getting-started.md
│   ├── resource-management.md
│   ├── health-check.md
│   └── export-integration.md
├── .env.example                  # 环境变量示例（检测间隔、并发数）
├── package.json                  # 项目元信息与脚本命令
├── tsconfig.json                 # TypeScript 编译配置（target ES2022）
└── README.md                     # 本文件
```

## 贡献指南

提交新批次资源：在 seeds/ 目录下新建 batch_{编号}.json 文件，格式为 { "batchId": 91, "urls": [...] }，随后运行 pnpm run seed --batch=91 导入系统。提交前请使用 scripts/validate-urls.js 检查 URL 格式是否包含非法字符。

改进健康检测策略：若需调整超时时间或重试次数，请修改 src/core/health-checker.ts 中的 CHECK_TIMEOUT_MS 与 MAX_RETRIES 常量，并在 PR 中附上调整后的测试结果（tests/health-checker.test.ts）。

完善前端 UI 组件：资源表格目前支持按域名筛选，若需增加按文件名数字段（如 84546 或 6658）模糊搜索，请在 resource-table.tsx 中添加相应输入框及状态管理逻辑。

补充文档用例：若您在实际使用中发现新的典型场景，欢迎在 docs/ 目录下新建 case-study-{序号}.md 文件，描述问题背景、操作步骤与最终效果，便于其他用户参考。

修复安全漏洞：如发现 SQL 注入或路径遍历风险，请先通过 Issues 提交漏洞描述（不含具体利用代码），待 maintainer 确认后再提交修复补丁。

## 常见问题

问：启动后资源状态全部显示为未知（unknown），是什么原因？

答：首次启动或网络环境变更时，健康检测任务可能尚未执行完毕。请检查 .env 文件中的 HEALTH_CHECK_CRON 是否设置为有效表达式（默认每 30 分钟执行一次）。您也可以手动触发检测：访问 http://localhost:3000/api/health/trigger 或使用 curl -X POST http://localhost:3000/api/health/trigger。另外请确认服务器能够解析 h5.mobile.*.cn 域名，必要时在 /etc/hosts 中添加临时映射。

问：导出的 Markdown 列表能否直接粘贴到其他文档中？

答：可以。系统导出的格式为纯无序列表（每行以 "- " 开头），与绝大多数 Markdown 解析器兼容。若需要去掉行首的 "- " 或改为编号列表，请在导出前选择 "纯文本" 格式，再通过文本编辑器的查找替换功能进行处理。注意导出功能不会对 URL 做任何编码或解码操作，保持与原始资源列表完全一致。

问：如何迁移到 PostgreSQL 生产环境？

答：本项目默认使用 SQLite 便于快速启动，但生产环境建议换用 PostgreSQL。请参考 docs/production-deploy.md 中的步骤：首先在 .env 中设置 DATABASE_URL=postgresql://...，然后运行 pnpm run migrate:pg 执行 PostgreSQL 专用迁移脚本，最后使用 pnpm run seed --batch=90 --db=pg 导入数据。迁移前请确保已通过 pg_dump 备份现有 SQLite 数据（可使用 src/lib/export-sqlite-to-pg.ts 辅助工具）。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

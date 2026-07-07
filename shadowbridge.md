# DocHub 移动端文档聚合站

DocHub 是一个面向移动端用户与技术研究人员的轻量级文档资源聚合与导航系统。该项目专注于收集、分类与快速检索散落在各类移动域名下的技术文档、行业报告与操作手册，解决技术人员在移动端查找专业文档时面临的来源分散、链接失效、检索效率低下的核心痛点。

项目定位为技术文档的“中转过道”而非存储仓库，通过建立结构化的外链索引机制，帮助开发者、运维人员、数据分析师在移动设备上以最低成本定位所需资料。所有资源以纯外链形式收录，不占用本地存储空间，支持快速导入与批量更新。

## 功能概览

批量文档外链导入与自动校验 系统支持通过文本列表或CSV文件批量导入文档外链，并在导入时自动检测链接可达性与资源类型，过滤无效或错误重定向的地址。

多维度文档分类标签 每一条文档链接均可附加领域、格式、语种、发布日期等多个自定义标签，便于后续按主题筛选与聚合展示。

移动端自适应检索界面 针对手机与平板设备优化检索交互，支持关键词模糊匹配、标签组合筛选以及按域名来源分组浏览。

本地缓存与离线访问提示 对于已访问过的文档链接，系统自动缓存文档标题与摘要信息，并在无网络环境下给出明确的离线不可用提示，避免用户等待超时。

链接健康度定期巡检 后台定时任务每日扫描所有收录链接，检测HTTP状态码变更、内容重定向或页面失效情况，生成异常报告并标记问题链接。

访问统计与热度排序 记录每条链接的点击次数与最近访问时间，支持按热度、更新时间或收录顺序对列表进行动态排序。

数据导入导出兼容JSON与CSV 提供标准化的数据交换接口，允许用户将整个文档索引导出为JSON或CSV格式，也可从外部系统同步更新资源列表。

## 应用场景

移动端技术文档快速查阅 技术人员在户外或脱离桌面环境时，通过DocHub快速访问常见运维手册、API参考文档或故障处理流程，无需在浏览器历史记录中反复翻找。

行业报告与白皮书集中管理 数据分析团队将分散在多个行业站点中的PDF与DOC格式报告统一收录至DocHub，并通过标签区分年份、领域与机构来源，便于团队内部分享与引用。

多域名文档资源归集与去重 企业知识管理负责人可利用DocHub将不同业务系统、不同子域名下的操作手册与培训材料归并至单一入口，同时检测重复链接以减少冗余。

离线环境下的文档导航准备 在移动网络不稳定的现场作业环境中，工作人员可提前通过DocHub批量打开并缓存所需文档页面，确保关键资料在弱网条件下依然可用。

开源项目外部参考资料整理 开源社区维护者可将项目依赖的第三方文档、技术规范、标准协议文本等外链整理为DocHub资源列表，作为项目附属文档的一部分对外公开。

## 快速开始

以下步骤指导您在本地环境快速启动DocHub服务。

```bash
# 克隆代码仓库
git clone https://github.com/dochub/dochub-mobile.git
cd dochub-mobile

# 安装项目依赖（使用npm）
npm install

# 配置环境变量（复制示例配置文件）
cp .env.example .env

# 初始化本地数据库（SQLite）
npm run db:init

# 启动开发服务器（默认端口3000）
npm run dev
```

启动成功后，访问控制台输出中显示的本地地址（通常为 http://localhost:3000 ），即可进入文档管理界面。首次启动将自动生成示例数据，您可通过界面上的“导入链接”按钮批量添加自定义资源。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 16.20.0 或更高 | 运行时环境，推荐使用LTS版本 |
| npm | 8.0.0 或更高 | 包管理器，用于安装项目依赖 |
| SQLite3 | 系统自带或集成 | 轻量级嵌入式数据库，无需额外部署 |
| 网络访问 | 外网可达 | 用于链接健康度巡检与文档预览抓取 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，Windows需启用WSL2或使用Git Bash |
| 内存 | 最低512MB | 推荐1GB以上以支持并发巡检任务 |
| 存储 | 200MB可用空间 | 主要用于数据库文件与日志存储 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | /docs/getting-started.md | 如何理解DocHub的数据模型与核心概念，以及首次使用的完整操作路径 |
| 管理员手册 | /docs/admin-guide.md | 如何配置后台巡检任务、管理用户权限、调整系统参数与性能调优 |
| API参考 | /docs/api-reference.md | 所有对外提供的RESTful接口定义、请求参数、响应格式与错误码说明 |
| 数据格式规范 | /docs/data-format.md | 导入导出所支持的JSON/CSV字段映射、标签命名规则与链接校验标准 |
| 部署与运维 | /docs/deployment.md | 生产环境下的容器化部署方案、日志收集、监控告警与备份恢复策略 |
| 常见操作FAQ | /docs/faq.md | 涵盖日常使用中高频问题的集中解答，包括链接添加失败、标签管理等 |

## 资源列表

- h5.mobile.fuvxie.cn/Article/44981.doc
- h5.mobile.cmcvrr.cn/Article/14507.doc
- h5.mobile.cmcvrr.cn/Article/30779.doc
- h5.mobile.hcbezg.cn/Article/9691.doc
- h5.mobile.cmcvrr.cn/Article/4912118.doc
- h5.mobile.jnjpgf.cn/Article/39434.doc
- h5.mobile.cmcvrr.cn/Article/332494.doc
- h5.mobile.nwbbyt.cn/Article/637602.doc
- h5.mobile.nzfnve.cn/Article/54257.doc
- h5.mobile.jnjpgf.cn/Article/72779.doc
- h5.mobile.nzfnve.cn/Article/61186.doc
- h5.mobile.hcbezg.cn/Article/64564.doc
- h5.mobile.hcbezg.cn/Article/179691.doc
- h5.mobile.fuvxie.cn/Article/6452.doc
- h5.mobile.fuvxie.cn/Article/5615.doc
- h5.mobile.cmcvrr.cn/Article/56707.doc
- h5.mobile.cvsifc.cn/Article/70938.doc
- h5.mobile.nwbbyt.cn/Article/6448669.doc
- h5.mobile.nwbbyt.cn/Article/0002414.doc
- h5.mobile.puhvjy.cn/Article/4951.doc
- h5.mobile.cmcvrr.cn/Article/6488.doc
- h5.mobile.cvsifc.cn/Article/1336.doc
- h5.mobile.fuvxie.cn/Article/35294.doc
- h5.mobile.puhvjy.cn/Article/3207807.doc
- h5.mobile.fuvxie.cn/Article/12185.doc
- h5.mobile.jnjpgf.cn/Article/2356.doc
- h5.mobile.nwbbyt.cn/Article/63278.doc
- h5.mobile.cvsifc.cn/Article/001506.doc
- h5.mobile.nzfnve.cn/Article/78372.doc
- h5.mobile.fuvxie.cn/Article/43789.doc
- h5.mobile.nwbbyt.cn/Article/447834.doc
- h5.mobile.fuvxie.cn/Article/6679.doc
- h5.mobile.hcbezg.cn/Article/47657.doc
- h5.mobile.jnjpgf.cn/Article/051777.doc
- h5.mobile.jnjpgf.cn/Article/7698969.doc
- h5.mobile.cmcvrr.cn/Article/0962.doc
- h5.mobile.cmcvrr.cn/Article/9602.doc
- h5.mobile.fuvxie.cn/Article/75477.doc
- h5.mobile.fuvxie.cn/Article/719104.doc
- h5.mobile.hcbezg.cn/Article/7294.doc
- h5.mobile.jnjpgf.cn/Article/7431.doc
- h5.mobile.puhvjy.cn/Article/20841.doc
- h5.mobile.puhvjy.cn/Article/4774.doc
- h5.mobile.hcbezg.cn/Article/7429.doc
- h5.mobile.nzfnve.cn/Article/7245.doc
- h5.mobile.puhvjy.cn/Article/4945400.doc
- h5.mobile.nzfnve.cn/Article/8199.doc
- h5.mobile.puhvjy.cn/Article/22619.doc
- h5.mobile.jnjpgf.cn/Article/30566.doc
- h5.mobile.nwbbyt.cn/Article/485526.doc
- h5.mobile.puhvjy.cn/Article/53266.doc
- h5.mobile.jnjpgf.cn/Article/362337.doc
- h5.mobile.nwbbyt.cn/Article/113533.doc
- h5.mobile.nwbbyt.cn/Article/2436629.doc
- h5.mobile.cvsifc.cn/Article/8262084.doc
- h5.mobile.jnjpgf.cn/Article/09330.doc
- h5.mobile.nzfnve.cn/Article/37175.doc
- h5.mobile.puhvjy.cn/Article/419001.doc
- h5.mobile.puhvjy.cn/Article/84883.doc
- h5.mobile.hcbezg.cn/Article/7909084.doc
- h5.mobile.fuvxie.cn/Article/1351.doc
- h5.mobile.cvsifc.cn/Article/0635701.doc
- h5.mobile.cvsifc.cn/Article/7418.doc
- h5.mobile.cvsifc.cn/Article/69322.doc
- h5.mobile.nwbbyt.cn/Article/06659.doc
- h5.mobile.nzfnve.cn/Article/1467939.doc
- h5.mobile.fuvxie.cn/Article/1637009.doc
- h5.mobile.nwbbyt.cn/Article/792120.doc
- h5.mobile.hcbezg.cn/Article/1242252.doc
- h5.mobile.nzfnve.cn/Article/98726.doc
- h5.mobile.hcbezg.cn/Article/4811698.doc
- h5.mobile.nwbbyt.cn/Article/610922.doc
- h5.mobile.jnjpgf.cn/Article/120317.doc
- h5.mobile.cmcvrr.cn/Article/494417.doc
- h5.mobile.nzfnve.cn/Article/099685.doc
- h5.mobile.puhvjy.cn/Article/248173.doc
- h5.mobile.fuvxie.cn/Article/6406.doc
- h5.mobile.puhvjy.cn/Article/443647.doc
- h5.mobile.cmcvrr.cn/Article/9278.doc
- h5.mobile.nzfnve.cn/Article/330400.doc
- h5.mobile.cmcvrr.cn/Article/942050.doc
- h5.mobile.cmcvrr.cn/Article/68804.doc
- h5.mobile.nzfnve.cn/Article/94796.doc
- h5.mobile.hcbezg.cn/Article/8188.doc
- h5.mobile.cmcvrr.cn/Article/2146.doc
- h5.mobile.nwbbyt.cn/Article/5375312.doc
- h5.mobile.nwbbyt.cn/Article/714796.doc
- h5.mobile.fuvxie.cn/Article/31564.doc
- h5.mobile.nzfnve.cn/Article/91019.doc
- h5.mobile.fuvxie.cn/Article/30033.doc
- h5.mobile.cvsifc.cn/Article/42531.doc
- h5.mobile.jnjpgf.cn/Article/1852.doc
- h5.mobile.cvsifc.cn/Article/7389779.doc
- h5.mobile.nzfnve.cn/Article/196987.doc
- h5.mobile.hcbezg.cn/Article/42726.doc
- h5.mobile.nwbbyt.cn/Article/3947821.doc
- h5.mobile.puhvjy.cn/Article/6413368.doc
- h5.mobile.nwbbyt.cn/Article/61504.doc
- h5.mobile.puhvjy.cn/Article/40062.doc
- h5.mobile.nzfnve.cn/Article/474944.doc
- h5.mobile.cmcvrr.cn/Article/1075194.doc
- h5.mobile.hcbezg.cn/Article/43165.doc
- h5.mobile.nwbbyt.cn/Article/2672.doc
- h5.mobile.jnjpgf.cn/Article/70803.doc
- h5.mobile.cmcvrr.cn/Article/0766091.doc
- h5.mobile.jnjpgf.cn/Article/9167902.doc
- h5.mobile.hcbezg.cn/Article/2501229.doc
- h5.mobile.cvsifc.cn/Article/2957412.doc
- h5.mobile.cvsifc.cn/Article/68898.doc
- h5.mobile.cmcvrr.cn/Article/8980307.doc
- h5.mobile.cmcvrr.cn/Article/5632.doc
- h5.mobile.cmcvrr.cn/Article/5206.doc
- h5.mobile.nzfnve.cn/Article/65338.doc
- h5.mobile.hcbezg.cn/Article/1980.doc
- h5.mobile.nwbbyt.cn/Article/7158.doc
- h5.mobile.cvsifc.cn/Article/07369.doc
- h5.mobile.cmcvrr.cn/Article/68831.doc
- h5.mobile.jnjpgf.cn/Article/76293.doc
- h5.mobile.hcbezg.cn/Article/64070.doc
- h5.mobile.nwbbyt.cn/Article/59975.doc
- h5.mobile.fuvxie.cn/Article/376960.doc
- h5.mobile.jnjpgf.cn/Article/0888942.doc
- h5.mobile.nzfnve.cn/Article/3312043.doc
- h5.mobile.hcbezg.cn/Article/4222.doc
- h5.mobile.puhvjy.cn/Article/0000292.doc
- h5.mobile.nzfnve.cn/Article/60674.doc
- h5.mobile.fuvxie.cn/Article/3101.doc
- h5.mobile.nwbbyt.cn/Article/06453.doc
- h5.mobile.nwbbyt.cn/Article/57085.doc
- h5.mobile.nwbbyt.cn/Article/1452828.doc
- h5.mobile.puhvjy.cn/Article/85728.doc
- h5.mobile.cmcvrr.cn/Article/5690.doc
- h5.mobile.cmcvrr.cn/Article/7449041.doc
- h5.mobile.hcbezg.cn/Article/3025942.doc
- h5.mobile.cmcvrr.cn/Article/52456.doc
- h5.mobile.fuvxie.cn/Article/389352.doc
- h5.mobile.cvsifc.cn/Article/6453347.doc
- h5.mobile.nzfnve.cn/Article/54090.doc
- h5.mobile.cmcvrr.cn/Article/88774.doc
- h5.mobile.hcbezg.cn/Article/825804.doc
- h5.mobile.hcbezg.cn/Article/04593.doc
- h5.mobile.hcbezg.cn/Article/7820085.doc
- h5.mobile.hcbezg.cn/Article/2216977.doc
- h5.mobile.nwbbyt.cn/Article/973296.doc
- h5.mobile.nzfnve.cn/Article/0363.doc
- h5.mobile.cvsifc.cn/Article/49799.doc
- h5.mobile.nzfnve.cn/Article/237877.doc
- h5.mobile.fuvxie.cn/Article/8307047.doc
- h5.mobile.jnjpgf.cn/Article/9967.doc
- h5.mobile.nzfnve.cn/Article/96347.doc
- h5.mobile.hcbezg.cn/Article/732457.doc
- h5.mobile.nzfnve.cn/Article/6285723.doc
- h5.mobile.hcbezg.cn/Article/77913.doc
- h5.mobile.jnjpgf.cn/Article/87224.doc
- h5.mobile.cmcvrr.cn/Article/108492.doc
- h5.mobile.nwbbyt.cn/Article/72358.doc
- h5.mobile.cmcvrr.cn/Article/28404.doc
- h5.mobile.cvsifc.cn/Article/48275.doc
- h5.mobile.puhvjy.cn/Article/4957.doc
- h5.mobile.nzfnve.cn/Article/0139855.doc
- h5.mobile.fuvxie.cn/Article/8497.doc
- h5.mobile.fuvxie.cn/Article/141334.doc
- h5.mobile.cmcvrr.cn/Article/4765084.doc
- h5.mobile.cmcvrr.cn/Article/5704412.doc
- h5.mobile.puhvjy.cn/Article/079277.doc
- h5.mobile.cvsifc.cn/Article/8079099.doc
- h5.mobile.cmcvrr.cn/Article/235554.doc
- h5.mobile.cmcvrr.cn/Article/1786421.doc
- h5.mobile.cmcvrr.cn/Article/39491.doc
- h5.mobile.hcbezg.cn/Article/84768.doc
- h5.mobile.nwbbyt.cn/Article/4052586.doc
- h5.mobile.fuvxie.cn/Article/7729260.doc
- h5.mobile.jnjpgf.cn/Article/6456.doc
- h5.mobile.cmcvrr.cn/Article/70585.doc
- h5.mobile.fuvxie.cn/Article/104814.doc
- h5.mobile.hcbezg.cn/Article/765739.doc
- h5.mobile.puhvjy.cn/Article/6109.doc
- h5.mobile.cmcvrr.cn/Article/9843.doc
- h5.mobile.jnjpgf.cn/Article/055758.doc
- h5.mobile.hcbezg.cn/Article/3297693.doc
- h5.mobile.fuvxie.cn/Article/2071763.doc
- h5.mobile.cvsifc.cn/Article/64495.doc
- h5.mobile.puhvjy.cn/Article/813456.doc
- h5.mobile.cmcvrr.cn/Article/9649494.doc
- h5.mobile.fuvxie.cn/Article/00160.doc
- h5.mobile.nwbbyt.cn/Article/5749.doc
- h5.mobile.hcbezg.cn/Article/0068124.doc
- h5.mobile.puhvjy.cn/Article/7518.doc
- h5.mobile.cvsifc.cn/Article/6609945.doc
- h5.mobile.hcbezg.cn/Article/064482.doc
- h5.mobile.nzfnve.cn/Article/4771923.doc
- h5.mobile.nzfnve.cn/Article/27513.doc
- h5.mobile.jnjpgf.cn/Article/5159.doc
- h5.mobile.hcbezg.cn/Article/84677.doc
- h5.mobile.puhvjy.cn/Article/0116.doc
- h5.mobile.fuvxie.cn/Article/2014.doc
- h5.mobile.cmcvrr.cn/Article/85164.doc
- h5.mobile.puhvjy.cn/Article/0351138.doc
- h5.mobile.puhvjy.cn/Article/6178432.doc
- h5.mobile.nzfnve.cn/Article/9231613.doc
- h5.mobile.nwbbyt.cn/Article/75097.doc
- h5.mobile.hcbezg.cn/Article/0237.doc
- h5.mobile.puhvjy.cn/Article/428418.doc
- h5.mobile.fuvxie.cn/Article/4576287.doc
- h5.mobile.puhvjy.cn/Article/99834.doc
- h5.mobile.hcbezg.cn/Article/5572.doc
- h5.mobile.hcbezg.cn/Article/8452.doc
- h5.mobile.fuvxie.cn/Article/417532.doc
- h5.mobile.jnjpgf.cn/Article/232343.doc
- h5.mobile.puhvjy.cn/Article/6808.doc
- h5.mobile.cvsifc.cn/Article/5576.doc
- h5.mobile.puhvjy.cn/Article/8266.doc
- h5.mobile.puhvjy.cn/Article/7247.doc
- h5.mobile.jnjpgf.cn/Article/1840.doc
- h5.mobile.cmcvrr.cn/Article/5623184.doc
- h5.mobile.puhvjy.cn/Article/57337.doc
- h5.mobile.hcbezg.cn/Article/74356.doc
- h5.mobile.fuvxie.cn/Article/06905.doc
- h5.mobile.cvsifc.cn/Article/358516.doc
- h5.mobile.nwbbyt.cn/Article/307158.doc
- h5.mobile.nzfnve.cn/Article/55370.doc
- h5.mobile.nwbbyt.cn/Article/12454.doc
- h5.mobile.puhvjy.cn/Article/7558032.doc
- h5.mobile.cvsifc.cn/Article/9597.doc
- h5.mobile.nzfnve.cn/Article/6462.doc
- h5.mobile.puhvjy.cn/Article/4488418.doc
- h5.mobile.jnjpgf.cn/Article/5093311.doc
- h5.mobile.fuvxie.cn/Article/0596.doc
- h5.mobile.fuvxie.cn/Article/9735126.doc
- h5.mobile.nwbbyt.cn/Article/723296.doc
- h5.mobile.cvsifc.cn/Article/308177.doc
- h5.mobile.puhvjy.cn/Article/281144.doc
- h5.mobile.hcbezg.cn/Article/6079426.doc
- h5.mobile.nwbbyt.cn/Article/7436773.doc
- h5.mobile.fuvxie.cn/Article/42183.doc
- h5.mobile.cmcvrr.cn/Article/362408.doc
- h5.mobile.fuvxie.cn/Article/4453.doc
- h5.mobile.nwbbyt.cn/Article/6028.doc
- h5.mobile.nzfnve.cn/Article/215673.doc
- h5.mobile.hcbezg.cn/Article/8746447.doc
- h5.mobile.jnjpgf.cn/Article/473507.doc
- h5.mobile.nwbbyt.cn/Article/83523.doc
- h5.mobile.cmcvrr.cn/Article/980761.doc
- h5.mobile.nzfnve.cn/Article/36100.doc
- h5.mobile.cvsifc.cn/Article/6848195.doc
- h5.mobile.fuvxie.cn/Article/082479.doc
- h5.mobile.puhvjy.cn/Article/9560.doc
- h5.mobile.puhvjy.cn/Article/17077.doc
- h5.mobile.fuvxie.cn/Article/0509222.doc
- h5.mobile.fuvxie.cn/Article/302874.doc

## 项目结构

```
dochub-mobile/
├── src/
│   ├── core/                             # 核心数据模型与业务逻辑
│   │   ├── link.model.js                 # 链接实体定义与校验方法
│   │   ├── tag.model.js                  # 标签分类与层级管理
│   │   └── health.checker.js             # 链接健康度巡检引擎
│   ├── api/                              # RESTful接口层
│   │   ├── routes/
│   │   │   ├── link.routes.js            # 链接增删改查路由
│   │   │   └── import.routes.js          # 批量导入导出接口
│   │   └── middlewares/
│   │       ├── auth.js                   # 简易鉴权中间件
│   │       └── validator.js              # 请求参数校验
│   ├── ui/                               # 移动端前端界面
│   │   ├── pages/
│   │   │   ├── home.html                 # 首页检索与列表展示
│   │   │   └── detail.html               # 单条链接详情视图
│   │   ├── static/
│   │   │   ├── style.css                 # 响应式样式表
│   │   │   └── app.js                    # 前端交互逻辑
│   │   └── components/
│   │       ├── tag-filter.js             # 标签筛选组件
│   │       └── link-card.js              # 链接卡片渲染组件
│   ├── worker/                           # 后台任务进程
│   │   ├── scheduler.js                  # 定时任务调度器
│   │   └── reporter.js                   # 异常报告生成器
│   └── utils/
│       ├── logger.js                     # 日志工具（写入/logs目录）
│       └── db.client.js                  # SQLite数据库连接封装
├── config/
│   ├── default.json                      # 默认系统配置
│   └── custom.json                       # 用户自定义覆盖配置（不入库）
├── data/
│   ├── dochub.db                         # SQLite主数据库文件
│   └── seed.json                         # 初始示例数据
├── docs/                                 # 完整文档目录（参见文档导航章节）
│   ├── getting-started.md
│   ├── admin-guide.md
│   └── ...
├── tests/
│   ├── unit/                             # 单元测试用例
│   └── integration/                      # 接口集成测试
├── scripts/
│   ├── import-csv.js                     # CSV导入命令行工具
│   └── export-json.js                    # JSON导出命令行工具
├── .env.example                          # 环境变量模板
├── package.json                          # npm依赖声明
├── README.md                             # 本文件
└── LICENSE                               # MIT许可证
```

## 贡献指南

我们欢迎并鼓励社区贡献，无论您是修复缺陷、改进文档还是新增功能，均请遵循以下流程：

1. 查阅现有Issue与Pull Request列表，确认无人正在处理相同问题。若为新功能建议，请先创建Issue进行需求讨论，避免无效实现。
2. Fork本仓库至您的个人账户，并将代码克隆至本地。请确保本地开发环境满足安装要求一节中的各项依赖版本。
3. 在本地新建功能分支（命名格式为 feature/简短描述 或 fix/缺陷编号），并在该分支上进行代码修改。所有提交信息请遵循约定式提交规范（Conventional Commits）。
4. 编写或更新对应的单元测试用例，确保所有测试通过（运行 npm test）。对于新增接口或工具函数，请同步补充文档注释。
5. 提交Pull Request至主仓库的main分支，并在描述中清晰关联相关Issue编号、说明改动范围与测试覆盖情况。PR审核通过后由维护者合并。

## 常见问题

**问：添加链接时提示“无法访问”或“超时”，但浏览器中可以正常打开，是什么原因？**

答：DocHub在执行链接校验时默认使用服务端网络环境，可能与您的本地网络存在差异。常见原因包括：服务端所在网络受限（如防火墙策略）、目标站点对User-Agent或请求来源有过滤、或目标站点响应速度过慢超出默认超时阈值（5秒）。您可以在配置文件中调整 timeout 与 userAgent 参数，或关闭导入时的实时校验（设置为 dryRun 模式）。

**问：导入的链接数量较多时，页面响应变慢，如何优化？**

答：DocHub默认在首页一次性加载全部链接，当收录数量超过500条时建议开启分页模式。请在config/custom.json中将 pagination.enabled 设为 true，并调整 pageSize 参数（推荐20-50条/页）。同时，后台巡检任务建议设置在低峰时段（如凌晨）执行，避免与用户访问争抢数据库资源。

**问：如何将DocHub部署到公网供团队内部使用？**

答：推荐使用PM2或Docker进行生产环境部署。项目根目录下提供了 Dockerfile 示例，您可以通过 docker build -t dochub-mobile . 构建镜像，并使用 docker run -p 3000:3000 -v ./data:/app/data 启动容器。若需启用外部访问，请确保配置反向代理（如Nginx）并正确设置环境变量 BASE_URL，同时根据需要启用基本认证或IP白名单等安全措施。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

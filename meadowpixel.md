# H5Doc Link Aggregator

H5Doc Link Aggregator 是一个面向移动端文档资源分发的轻量级链接管理工具，专注于对散落在多个内容源站点的 .doc 文档链接进行统一收集、分类索引与快速检索。该项目定位于技术团队、内容运营人员及个人研究者，帮助其从大量零散文档链接中快速定位目标文件，避免手动维护书签或依赖碎片化的聊天记录传递链接。

与通用书签管理工具不同，H5Doc Link Aggregator 针对移动端 H5 场景优化，支持批量链接导入、域名分组、文档 ID 提取与重复链接检测。项目本身不存储文档内容，仅作为链接索引层，通过极简的 Web 界面或 API 调用实现对海量文档链接的高效管理。当前批次收录 250 个文档链接，覆盖 7 个独立内容源域名，适用于文档归档、知识库建设与内容审计等场景。

## 功能概览

批量链接导入 支持一次性导入数百条文档链接，自动解析域名与文档 ID，并完成去重校验。

域名分组索引 按源域名对链接进行自动归类，每个域名独立展示文档列表，便于按来源筛选。

文档 ID 快速检索 基于文档 ID 后缀数字建立倒排索引，支持输入编号片段模糊匹配，毫秒级返回结果。

重复链接检测 内置链接去重引擎，导入时自动标记重复条目，避免索引冗余。

移动端 H5 适配 针对手机浏览器优化界面布局，支持触屏滑动操作，适合在移动设备上浏览和管理链接。

导出为结构化列表 支持将当前索引库导出为 JSON 或 CSV 格式，便于迁移至其他文档管理系统。

源站健康检查 定时探测每个链接的可访问性，标记失效链接并生成异常报告，帮助用户及时清理无效资源。

## 应用场景

文档资源归档与整理 内容运营团队定期从多个合作方站点收集文档链接，使用 H5Doc Link Aggregator 统一导入并分类，形成可检索的内部文档索引库，替代传统的 Excel 手工记录方式。

技术文档审计与合规检查 企业内部合规部门需要定期审查对外发布的文档链接，通过本工具批量导入所有对外链接，按域名分组后逐一核对文档内容与审批记录，确保无违规外发。

学术研究资料收集 研究人员在文献调研阶段从不同数据库和预印本平台获取大量文档链接，利用 H5Doc Link Aggregator 集中管理，支持按主题标签（通过文档 ID 前缀或域名）快速筛选，提高文献综述效率。

移动端快捷查阅 产品经理或项目经理在外出途中需要快速查阅产品需求文档或设计稿说明，通过手机访问 H5Doc Link Aggregator 的移动端界面，按域名或编号模糊搜索即可直达目标文档。

## 快速开始

以下步骤帮助您在本地环境快速启动 H5Doc Link Aggregator 服务。

```bash
# 克隆代码仓库
git clone https://github.com/your-org/h5doc-link-aggregator.git

# 进入项目目录
cd h5doc-link-aggregator

# 安装依赖（使用 npm）
npm install

# 启动开发服务器
npm run dev
```

服务启动后，访问控制台输出的本地地址（默认为 http://localhost:3000）即可打开 Web 界面。首次启动会自动创建示例索引库，您可以通过界面上的导入功能批量添加链接。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用 20.x 版本以获得更好的性能 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| SQLite3 | 系统自带或由 better-sqlite3 捆绑 | 内嵌数据库引擎，用于存储链接索引数据，无需额外安装 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Safari 15+ | Web 界面客户端，需支持 ES2020 语法和 Fetch API |
| 网络连通性 | 可访问公网 DNS | 用于源站健康检查功能，需要能够解析并连接目标域名 |
| 磁盘空间 | 至少 100 MB 空闲 | 用于存储 SQLite 数据库文件和日志，实际占用随链接数量线性增长，250 条链接约占用 2-5 MB |
| 内存 | 至少 512 MB | 运行时内存占用，批量导入 1000 条链接时峰值内存约为 200 MB |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide.md | 如何导入链接、如何按域名分组浏览、如何检索文档 ID、如何导出列表 |
| 管理员指南 | /docs/admin-guide.md | 如何配置源站健康检查频率、如何处理失效链接、如何备份索引数据库 |
| API 参考 | /docs/api-reference.md | 如何通过 RESTful API 批量添加链接、如何获取分组统计信息、如何调用检索接口 |
| 架构设计 | /docs/architecture.md | 索引存储方案为何选择 SQLite、检索索引如何构建、健康检查异步任务如何调度 |
| 部署说明 | /docs/deployment.md | 如何部署到生产服务器、如何使用 Docker 容器化运行、如何配置反向代理 |

## 资源列表

- h5.mobile.hcbezg.cn/Article/472905.doc
- h5.mobile.puhvjy.cn/Article/84588.doc
- h5.mobile.cvsifc.cn/Article/915796.doc
- h5.mobile.jnjpgf.cn/Article/5690.doc
- h5.mobile.fuvxie.cn/Article/22288.doc
- h5.mobile.fuvxie.cn/Article/8947.doc
- h5.mobile.jnjpgf.cn/Article/475932.doc
- h5.mobile.puhvjy.cn/Article/143516.doc
- h5.mobile.puhvjy.cn/Article/37080.doc
- h5.mobile.cvsifc.cn/Article/618651.doc
- h5.mobile.cvsifc.cn/Article/07677.doc
- h5.mobile.fuvxie.cn/Article/1476092.doc
- h5.mobile.cvsifc.cn/Article/742096.doc
- h5.mobile.cvsifc.cn/Article/1493392.doc
- h5.mobile.fuvxie.cn/Article/696393.doc
- h5.mobile.nzfnve.cn/Article/37422.doc
- h5.mobile.nzfnve.cn/Article/77411.doc
- h5.mobile.cvsifc.cn/Article/1162234.doc
- h5.mobile.fuvxie.cn/Article/579205.doc
- h5.mobile.fuvxie.cn/Article/7870.doc
- h5.mobile.hcbezg.cn/Article/8242.doc
- h5.mobile.fuvxie.cn/Article/99629.doc
- h5.mobile.cvsifc.cn/Article/1326.doc
- h5.mobile.jnjpgf.cn/Article/4296.doc
- h5.mobile.cvsifc.cn/Article/777158.doc
- h5.mobile.fuvxie.cn/Article/09181.doc
- h5.mobile.cmcvrr.cn/Article/0591.doc
- h5.mobile.cmcvrr.cn/Article/60244.doc
- h5.mobile.nwbbyt.cn/Article/9644.doc
- h5.mobile.puhvjy.cn/Article/0246.doc
- h5.mobile.nzfnve.cn/Article/3520.doc
- h5.mobile.cvsifc.cn/Article/277711.doc
- h5.mobile.puhvjy.cn/Article/251575.doc
- h5.mobile.fuvxie.cn/Article/61362.doc
- h5.mobile.nwbbyt.cn/Article/1612107.doc
- h5.mobile.cmcvrr.cn/Article/52576.doc
- h5.mobile.fuvxie.cn/Article/70896.doc
- h5.mobile.nwbbyt.cn/Article/7069.doc
- h5.mobile.nzfnve.cn/Article/9191293.doc
- h5.mobile.jnjpgf.cn/Article/02230.doc
- h5.mobile.hcbezg.cn/Article/80531.doc
- h5.mobile.fuvxie.cn/Article/883420.doc
- h5.mobile.nwbbyt.cn/Article/1983.doc
- h5.mobile.nwbbyt.cn/Article/6923479.doc
- h5.mobile.cvsifc.cn/Article/06823.doc
- h5.mobile.fuvxie.cn/Article/3926235.doc
- h5.mobile.fuvxie.cn/Article/928740.doc
- h5.mobile.cvsifc.cn/Article/0595942.doc
- h5.mobile.nzfnve.cn/Article/8137358.doc
- h5.mobile.nzfnve.cn/Article/6838.doc
- h5.mobile.nzfnve.cn/Article/8563577.doc
- h5.mobile.cmcvrr.cn/Article/6271.doc
- h5.mobile.cmcvrr.cn/Article/4948.doc
- h5.mobile.cvsifc.cn/Article/15152.doc
- h5.mobile.cmcvrr.cn/Article/0232147.doc
- h5.mobile.puhvjy.cn/Article/858588.doc
- h5.mobile.hcbezg.cn/Article/2255.doc
- h5.mobile.jnjpgf.cn/Article/9368.doc
- h5.mobile.jnjpgf.cn/Article/18167.doc
- h5.mobile.cvsifc.cn/Article/5979.doc
- h5.mobile.jnjpgf.cn/Article/757291.doc
- h5.mobile.hcbezg.cn/Article/313879.doc
- h5.mobile.fuvxie.cn/Article/18868.doc
- h5.mobile.hcbezg.cn/Article/415265.doc
- h5.mobile.puhvjy.cn/Article/128447.doc
- h5.mobile.nzfnve.cn/Article/7308310.doc
- h5.mobile.puhvjy.cn/Article/05922.doc
- h5.mobile.cmcvrr.cn/Article/8436223.doc
- h5.mobile.fuvxie.cn/Article/1752571.doc
- h5.mobile.nwbbyt.cn/Article/2962424.doc
- h5.mobile.cmcvrr.cn/Article/971386.doc
- h5.mobile.puhvjy.cn/Article/9001012.doc
- h5.mobile.puhvjy.cn/Article/79251.doc
- h5.mobile.nzfnve.cn/Article/1444.doc
- h5.mobile.nwbbyt.cn/Article/65760.doc
- h5.mobile.nwbbyt.cn/Article/995724.doc
- h5.mobile.puhvjy.cn/Article/2718020.doc
- h5.mobile.nwbbyt.cn/Article/7810273.doc
- h5.mobile.jnjpgf.cn/Article/1767.doc
- h5.mobile.puhvjy.cn/Article/4554755.doc
- h5.mobile.cmcvrr.cn/Article/834849.doc
- h5.mobile.fuvxie.cn/Article/9406.doc
- h5.mobile.nwbbyt.cn/Article/9540948.doc
- h5.mobile.cmcvrr.cn/Article/30168.doc
- h5.mobile.cvsifc.cn/Article/46386.doc
- h5.mobile.nwbbyt.cn/Article/6291.doc
- h5.mobile.hcbezg.cn/Article/2292705.doc
- h5.mobile.nwbbyt.cn/Article/4205753.doc
- h5.mobile.hcbezg.cn/Article/0356417.doc
- h5.mobile.cvsifc.cn/Article/490672.doc
- h5.mobile.nzfnve.cn/Article/2462575.doc
- h5.mobile.puhvjy.cn/Article/83489.doc
- h5.mobile.nwbbyt.cn/Article/93312.doc
- h5.mobile.fuvxie.cn/Article/26029.doc
- h5.mobile.fuvxie.cn/Article/27736.doc
- h5.mobile.fuvxie.cn/Article/5579.doc
- h5.mobile.fuvxie.cn/Article/750847.doc
- h5.mobile.hcbezg.cn/Article/338592.doc
- h5.mobile.cvsifc.cn/Article/36408.doc
- h5.mobile.jnjpgf.cn/Article/890580.doc
- h5.mobile.puhvjy.cn/Article/827804.doc
- h5.mobile.fuvxie.cn/Article/80462.doc
- h5.mobile.cmcvrr.cn/Article/4916803.doc
- h5.mobile.jnjpgf.cn/Article/5070.doc
- h5.mobile.cvsifc.cn/Article/64610.doc
- h5.mobile.fuvxie.cn/Article/145544.doc
- h5.mobile.hcbezg.cn/Article/5830393.doc
- h5.mobile.nzfnve.cn/Article/4136510.doc
- h5.mobile.nwbbyt.cn/Article/92766.doc
- h5.mobile.jnjpgf.cn/Article/0230277.doc
- h5.mobile.hcbezg.cn/Article/283389.doc
- h5.mobile.cvsifc.cn/Article/7532036.doc
- h5.mobile.cvsifc.cn/Article/837612.doc
- h5.mobile.jnjpgf.cn/Article/06744.doc
- h5.mobile.jnjpgf.cn/Article/26718.doc
- h5.mobile.fuvxie.cn/Article/6606.doc
- h5.mobile.nwbbyt.cn/Article/1822.doc
- h5.mobile.nzfnve.cn/Article/25759.doc
- h5.mobile.puhvjy.cn/Article/4074620.doc
- h5.mobile.fuvxie.cn/Article/1692.doc
- h5.mobile.cvsifc.cn/Article/09971.doc
- h5.mobile.puhvjy.cn/Article/938523.doc
- h5.mobile.cmcvrr.cn/Article/6926.doc
- h5.mobile.hcbezg.cn/Article/54687.doc
- h5.mobile.cmcvrr.cn/Article/978996.doc
- h5.mobile.nzfnve.cn/Article/8411898.doc
- h5.mobile.hcbezg.cn/Article/506794.doc
- h5.mobile.hcbezg.cn/Article/82110.doc
- h5.mobile.puhvjy.cn/Article/59275.doc
- h5.mobile.fuvxie.cn/Article/814881.doc
- h5.mobile.hcbezg.cn/Article/9928.doc
- h5.mobile.nwbbyt.cn/Article/8077.doc
- h5.mobile.fuvxie.cn/Article/5388.doc
- h5.mobile.cmcvrr.cn/Article/0522770.doc
- h5.mobile.jnjpgf.cn/Article/967599.doc
- h5.mobile.cvsifc.cn/Article/10677.doc
- h5.mobile.jnjpgf.cn/Article/0113138.doc
- h5.mobile.hcbezg.cn/Article/14725.doc
- h5.mobile.cmcvrr.cn/Article/155355.doc
- h5.mobile.cmcvrr.cn/Article/2625.doc
- h5.mobile.cvsifc.cn/Article/4672688.doc
- h5.mobile.hcbezg.cn/Article/1984.doc
- h5.mobile.puhvjy.cn/Article/780110.doc
- h5.mobile.fuvxie.cn/Article/773671.doc
- h5.mobile.fuvxie.cn/Article/8948778.doc
- h5.mobile.jnjpgf.cn/Article/987760.doc
- h5.mobile.cvsifc.cn/Article/4006.doc
- h5.mobile.hcbezg.cn/Article/9185362.doc
- h5.mobile.nzfnve.cn/Article/1199.doc
- h5.mobile.nwbbyt.cn/Article/085736.doc
- h5.mobile.puhvjy.cn/Article/6760975.doc
- h5.mobile.nzfnve.cn/Article/80272.doc
- h5.mobile.cmcvrr.cn/Article/5004.doc
- h5.mobile.cmcvrr.cn/Article/33827.doc
- h5.mobile.nwbbyt.cn/Article/72329.doc
- h5.mobile.cmcvrr.cn/Article/2525.doc
- h5.mobile.cvsifc.cn/Article/1186859.doc
- h5.mobile.cvsifc.cn/Article/8470.doc
- h5.mobile.nzfnve.cn/Article/9622.doc
- h5.mobile.fuvxie.cn/Article/8309008.doc
- h5.mobile.nzfnve.cn/Article/58893.doc
- h5.mobile.puhvjy.cn/Article/4509.doc
- h5.mobile.nzfnve.cn/Article/1890425.doc
- h5.mobile.puhvjy.cn/Article/1076511.doc
- h5.mobile.fuvxie.cn/Article/4593.doc
- h5.mobile.nwbbyt.cn/Article/7589.doc
- h5.mobile.nzfnve.cn/Article/5539.doc
- h5.mobile.cmcvrr.cn/Article/9616950.doc
- h5.mobile.jnjpgf.cn/Article/019393.doc
- h5.mobile.hcbezg.cn/Article/8781.doc
- h5.mobile.cmcvrr.cn/Article/5489602.doc
- h5.mobile.nzfnve.cn/Article/51472.doc
- h5.mobile.nwbbyt.cn/Article/5689085.doc
- h5.mobile.nzfnve.cn/Article/4345.doc
- h5.mobile.nzfnve.cn/Article/54752.doc
- h5.mobile.cmcvrr.cn/Article/276331.doc
- h5.mobile.hcbezg.cn/Article/263097.doc
- h5.mobile.nwbbyt.cn/Article/4269817.doc
- h5.mobile.puhvjy.cn/Article/8393.doc
- h5.mobile.nzfnve.cn/Article/455379.doc
- h5.mobile.puhvjy.cn/Article/05429.doc
- h5.mobile.nzfnve.cn/Article/6001.doc
- h5.mobile.nwbbyt.cn/Article/15817.doc
- h5.mobile.hcbezg.cn/Article/4532.doc
- h5.mobile.cvsifc.cn/Article/8080.doc
- h5.mobile.nzfnve.cn/Article/992813.doc
- h5.mobile.nzfnve.cn/Article/8937461.doc
- h5.mobile.cvsifc.cn/Article/9056820.doc
- h5.mobile.cmcvrr.cn/Article/1272.doc
- h5.mobile.hcbezg.cn/Article/7931633.doc
- h5.mobile.hcbezg.cn/Article/884899.doc
- h5.mobile.nzfnve.cn/Article/12528.doc
- h5.mobile.jnjpgf.cn/Article/7909908.doc
- h5.mobile.jnjpgf.cn/Article/54641.doc
- h5.mobile.cvsifc.cn/Article/846706.doc
- h5.mobile.hcbezg.cn/Article/4650132.doc
- h5.mobile.nzfnve.cn/Article/5018762.doc
- h5.mobile.cmcvrr.cn/Article/1303776.doc
- h5.mobile.puhvjy.cn/Article/2181.doc
- h5.mobile.nzfnve.cn/Article/783893.doc
- h5.mobile.nzfnve.cn/Article/79825.doc
- h5.mobile.cmcvrr.cn/Article/608818.doc
- h5.mobile.fuvxie.cn/Article/2494422.doc
- h5.mobile.fuvxie.cn/Article/36193.doc
- h5.mobile.nzfnve.cn/Article/46498.doc
- h5.mobile.fuvxie.cn/Article/942340.doc
- h5.mobile.nwbbyt.cn/Article/7498.doc
- h5.mobile.puhvjy.cn/Article/112031.doc
- h5.mobile.nzfnve.cn/Article/7632747.doc
- h5.mobile.cmcvrr.cn/Article/60337.doc
- h5.mobile.fuvxie.cn/Article/16648.doc
- h5.mobile.puhvjy.cn/Article/1176533.doc
- h5.mobile.nzfnve.cn/Article/7222019.doc
- h5.mobile.fuvxie.cn/Article/949300.doc
- h5.mobile.jnjpgf.cn/Article/60041.doc
- h5.mobile.nzfnve.cn/Article/73450.doc
- h5.mobile.nwbbyt.cn/Article/7937514.doc
- h5.mobile.nwbbyt.cn/Article/0531168.doc
- h5.mobile.nwbbyt.cn/Article/3357.doc
- h5.mobile.puhvjy.cn/Article/7260.doc
- h5.mobile.nzfnve.cn/Article/56124.doc
- h5.mobile.jnjpgf.cn/Article/559445.doc
- h5.mobile.nzfnve.cn/Article/04582.doc
- h5.mobile.fuvxie.cn/Article/34634.doc
- h5.mobile.jnjpgf.cn/Article/2551.doc
- h5.mobile.jnjpgf.cn/Article/32845.doc
- h5.mobile.nzfnve.cn/Article/049218.doc
- h5.mobile.nzfnve.cn/Article/6793.doc
- h5.mobile.jnjpgf.cn/Article/6637763.doc
- h5.mobile.nwbbyt.cn/Article/5597886.doc
- h5.mobile.cvsifc.cn/Article/4410045.doc
- h5.mobile.puhvjy.cn/Article/3290370.doc
- h5.mobile.jnjpgf.cn/Article/2877829.doc
- h5.mobile.fuvxie.cn/Article/6920.doc
- h5.mobile.jnjpgf.cn/Article/8826720.doc
- h5.mobile.hcbezg.cn/Article/65807.doc
- h5.mobile.cvsifc.cn/Article/0742.doc
- h5.mobile.fuvxie.cn/Article/7533.doc
- h5.mobile.fuvxie.cn/Article/6249.doc
- h5.mobile.nzfnve.cn/Article/4238640.doc
- h5.mobile.puhvjy.cn/Article/402089.doc
- h5.mobile.fuvxie.cn/Article/791229.doc
- h5.mobile.nwbbyt.cn/Article/84919.doc
- h5.mobile.hcbezg.cn/Article/443466.doc
- h5.mobile.hcbezg.cn/Article/7071850.doc
- h5.mobile.nzfnve.cn/Article/365298.doc
- h5.mobile.nwbbyt.cn/Article/4902673.doc
- h5.mobile.puhvjy.cn/Article/2691763.doc
- h5.mobile.jnjpgf.cn/Article/648256.doc
- h5.mobile.cmcvrr.cn/Article/4503.doc

## 项目结构

```
h5doc-link-aggregator/
├── src/                           # 源代码主目录
│   ├── core/                      # 核心逻辑模块
│   │   ├── indexer.js             # 链接索引引擎，负责添加、删除和检索链接
│   │   ├── dedupe.js              # 重复检测算法，基于文档 ID 和 URL 双重去重
│   │   └── health-checker.js      # 源站健康检查调度器，定时探测链接可访问性
│   ├── api/                       # RESTful API 路由层
│   │   ├── routes/                # 路由定义目录
│   │   │   ├── import.js          # POST /api/import 批量导入接口
│   │   │   ├── search.js          # GET /api/search 文档检索接口
│   │   │   └── groups.js          # GET /api/groups 域名分组统计接口
│   │   └── middleware/            # 中间件目录
│   │       ├── auth.js            # 简单 API 密钥验证中间件（可选）
│   │       └── error-handler.js   # 全局异常捕获与格式化输出
│   ├── web/                       # Web 前端界面源码
│   │   ├── pages/                 # 页面组件目录
│   │   │   ├── Dashboard.jsx      # 总览面板，显示链接总数、域名分布和健康状态
│   │   │   ├── Import.jsx         # 批量导入页面，支持文本框粘贴和文件上传
│   │   │   └── Detail.jsx         # 单个域名详情页，展示该域名下所有文档链接
│   │   ├── components/            # 可复用 UI 组件
│   │   │   ├── LinkTable.jsx      # 链接列表表格组件，支持排序和筛选
│   │   │   └── SearchBar.jsx      # 文档 ID 快速检索输入框
│   │   └── styles/                # 样式文件（CSS Modules）
│   │       └── main.module.css    # 全局布局与响应式设计样式
│   ├── db/                        # 数据库层
│   │   ├── schema.sql             # SQLite 表结构定义（links 表、groups 表、logs 表）
│   │   ├── migrations/            # 数据库迁移脚本目录
│   │   │   └── 001-initial.sql    # 初始版本建表语句
│   │   └── client.js              # 数据库连接封装与 CRUD 操作函数
│   └── utils/                     # 工具函数目录
│       ├── logger.js              # 日志记录器，支持按日滚动写入文件
│       └── validator.js           # URL 格式校验与文档 ID 提取工具
├── tests/                         # 单元测试与集成测试目录
│   ├── unit/                      # 单元测试用例
│   │   ├── indexer.test.js        # 索引引擎核心函数测试
│   │   └── dedupe.test.js         # 去重算法测试
│   └── integration/               # 集成测试用例
│       └── api.test.js            # API 接口端到端测试
├── config/                        # 配置文件目录
│   ├── default.json               # 默认配置（端口、数据库路径、健康检查间隔）
│   └── production.json            # 生产环境配置覆盖（日志级别、缓存策略）
├── docs/                          # 项目文档目录
│   ├── user-guide.md              # 用户手册
│   ├── admin-guide.md             # 管理员指南
│   ├── api-reference.md           # API 参考文档
│   ├── architecture.md            # 架构设计文档
│   └── deployment.md              # 部署说明
├── scripts/                       # 运维辅助脚本
│   ├── backup-db.sh               # 数据库备份脚本
│   └── import-csv.sh              # 从 CSV 文件批量导入链接的命令行工具
├── .env.example                   # 环境变量模板（API 密钥、数据库路径）
├── .gitignore                     # Git 版本控制忽略文件配置
├── package.json                   # npm 项目清单与依赖声明
├── README.md                      # 项目自述文件（本文档）
└── LICENSE                        # MIT 许可证文本
```

## 贡献指南

我们欢迎社区贡献者参与 H5Doc Link Aggregator 的开发与改进。请遵循以下步骤提交贡献。

Fork 项目仓库并克隆到本地 访问 GitHub 项目页面，点击 Fork 按钮创建个人副本，然后使用 git clone 命令将副本拉取到本地开发环境。

创建功能分支 从 main 分支切出新分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式，例如 `feature/add-export-csv`。

编写代码并添加测试 在 src/ 目录下修改或新增代码，并在 tests/ 目录下补充对应的单元测试或集成测试用例，确保所有现有测试仍能通过。

提交变更并推送 编写清晰的提交信息，格式为 `<类型>: <简短描述>`，类型包括 feat、fix、docs、style、refactor、test、chore 等，然后推送到个人远程仓库。

发起 Pull Request 在 GitHub 上向原仓库的 main 分支发起 Pull Request，描述中说明变更目的、实现方案和测试覆盖情况，等待项目维护者审核。

## 常见问题

导入大量链接时界面卡顿或响应缓慢如何解决

批量导入操作会触发索引重建和重复检测，当单次导入超过 500 条链接时，建议使用 API 接口异步导入模式。您可以在导入请求头中添加 `X-Async: true` 字段，服务端将返回任务 ID，您可通过 `/api/task/{id}` 轮询导入进度。此外，也可以使用命令行脚本 `scripts/import-csv.sh` 进行后台导入，避免占用 Web 界面线程。

健康检查功能报告大量链接不可访问，但浏览器中手动打开正常

健康检查模块默认使用 HEAD 请求探测链接可用性，部分源站可能不支持 HEAD 方法或对非浏览器 User-Agent 进行限制。您可以在配置文件中将检查方法调整为 GET，并设置 `userAgent` 字段为常见浏览器标识。同时，检查超时时间默认设置为 5 秒，若源站响应较慢，可适当延长至 10 秒。

如何迁移索引数据库到另一台服务器

SQLite 数据库文件位于 `data/links.db`（默认路径），直接复制该文件到目标服务器相同目录即可完成迁移。若目标服务器使用不同操作系统，需注意 SQLite 版本兼容性，建议在目标服务器执行 `sqlite3 links.db .schema` 验证表结构一致性。迁移后重启服务，系统会自动识别已有数据。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

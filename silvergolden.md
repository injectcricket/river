# DocLink Hub

DocLink Hub 是一个面向技术文档聚合与外部资源链接管理的开源项目，专注于将大量分散的技术资料、在线文档、操作手册等外链资源以结构化方式进行组织和快速检索。项目定位为技术团队、开源社区和个人知识管理者的辅助工具，用于解决文档链接分散、资源失效、分类混乱以及缺乏统一访问入口等问题。

本项目的核心目标用户包括技术文档撰写者、运维工程师、技术负责人以及需要频繁查阅大量外部技术资料的开发人员。DocLink Hub 通过提供标准化的链接收录模板、自动化资源检查脚本以及可视化的文档导航界面，帮助用户高效管理上百乃至上千条外部资源链接，并支持对链接的可访问性、更新频率和所属领域进行标记与筛选。

---

## 功能概览

批量链接导入与解析 支持从 CSV、JSON 和纯文本列表批量导入外部链接，自动解析域名、路径及文件扩展名，生成结构化索引。

链接可用性健康检查 内置异步 HTTP 探测模块，可定期检测每个链接的可访问状态，并生成可用性报告，便于用户及时发现失效资源。

多维度分类与标签系统 允许用户为每个链接添加自定义分类、技术标签和备注说明，支持按标签、域名或更新日期进行快速筛选。

全文检索与模糊匹配 基于倒排索引实现链接标题、描述、标签及部分文档内容的全文搜索，支持拼音和首字母模糊匹配。

资源关系图谱展示 将收录的域名、子路径和文档类型以力导向图形式可视化，帮助用户理解资源之间的关联结构和来源分布。

自定义元数据扩展 每个链接条目支持扩展元数据字段，包括责任主体、所属项目、版本适用性、最后验证时间等，便于企业级使用场景下的精细化管理。

数据导入导出与迁移工具 提供标准化的数据导出功能，支持导出为 Markdown 表格、JSON 结构化数据和 HTML 目录页，方便与其他文档平台对接。

访问日志与热度统计 记录每个外部链接的本地访问次数和最近访问时间，辅助用户判断资源使用频率，优化导航布局。

---

## 应用场景

技术团队内部文档资源整合 研发团队可将常用的 API 文档、部署手册、中间件配置指南、故障排查记录等外部链接统一收录到 DocLink Hub 中，替代浏览器书签的分散管理方式，实现团队共享。

开源项目外链依赖梳理 开源项目维护者利用本工具管理项目 README 和官网中引用的所有外部资源链接，包括依赖库主页、协议文本、构建工具说明等，确保所有引用路径准确且可追溯。

个人技术知识库构建 技术爱好者使用 DocLink Hub 整理日常阅读的技术博客、论文下载链接、视频教程地址和代码仓库入口，形成个人专属的外链知识网络，并配合标签和搜索功能快速定位历史资料。

文档站点迁移与链接审计 在文档站点进行域名更换或目录重构时，利用本项目的链接批量探测和替换功能，快速定位所有需要更新的外部引用，降低迁移风险。

---

## 快速开始

执行以下命令完成项目克隆、依赖安装和服务启动，默认运行在本地 8080 端口。

```bash
git clone https://github.com/your-org/doclink-hub.git
cd doclink-hub
npm install
npm run build
npm start
```

访问 http://localhost:8080 进入 DocLink Hub 管理控制台，首次启动将自动创建示例数据并引导完成初始化配置。若使用 Docker 运行，可执行以下命令：

```bash
docker build -t doclink-hub:latest .
docker run -d -p 8080:8080 --name doclink-hub doclink-hub:latest
```

---

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.0.0 或更高 | 项目运行时环境，推荐使用 LTS 版本 |
| npm | 8.0.0 或更高 | 包管理器，用于安装第三方依赖 |
| SQLite3 | 3.32.0 或更高 | 内嵌数据库，用于存储链接索引和元数据，无需额外安装 |
| Python 3 | 3.8 至 3.11 | 仅在使用自动链接探测扩展脚本时需要 |
| Git | 2.25.0 或更高 | 用于项目克隆和版本管理 |
| cURL | 7.68.0 或更高 | 部分健康检查后端依赖，用于发送 HTTP 探测请求 |
| OpenSSL | 1.1.1 或更高 | 用于 HTTPS 链接验证和证书检查 |
| 系统内存 | 512 MB 最低 | 推荐 2 GB 及以上以支持大规模链接索引 |
| 磁盘空间 | 200 MB 最低 | 用于存储索引文件和数据库，不存储外部文档实体 |

---

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/getting-started.md | 如何快速初始化项目并导入第一批外链资源 |
| 链接管理 | /docs/link-management.md | 如何添加、编辑、删除链接，以及批量操作的方法 |
| 高级配置 | /docs/advanced-config.md | 如何配置自定义探测间隔、标签规则和扩展元数据 |
| 运维手册 | /docs/operations.md | 如何执行数据备份、迁移和性能调优操作 |

---

## 资源列表

- h5.mobile.jnjpgf.cn/Article/6036.doc
- h5.mobile.hcbezg.cn/Article/49084.doc
- h5.mobile.nzfnve.cn/Article/857966.doc
- h5.mobile.nwbbyt.cn/Article/6208.doc
- h5.mobile.puhvjy.cn/Article/16848.doc
- h5.mobile.nwbbyt.cn/Article/946377.doc
- h5.mobile.jnjpgf.cn/Article/49929.doc
- h5.mobile.cvsifc.cn/Article/75221.doc
- h5.mobile.nwbbyt.cn/Article/94917.doc
- h5.mobile.hcbezg.cn/Article/1441257.doc
- h5.mobile.fuvxie.cn/Article/4102.doc
- h5.mobile.cvsifc.cn/Article/5625104.doc
- h5.mobile.hcbezg.cn/Article/051623.doc
- h5.mobile.nwbbyt.cn/Article/2840.doc
- h5.mobile.nzfnve.cn/Article/7746563.doc
- h5.mobile.cvsifc.cn/Article/7121.doc
- h5.mobile.cmcvrr.cn/Article/631822.doc
- h5.mobile.fuvxie.cn/Article/09120.doc
- h5.mobile.nzfnve.cn/Article/217920.doc
- h5.mobile.cmcvrr.cn/Article/4599.doc
- h5.mobile.nwbbyt.cn/Article/239327.doc
- h5.mobile.nwbbyt.cn/Article/72470.doc
- h5.mobile.cvsifc.cn/Article/6636.doc
- h5.mobile.nwbbyt.cn/Article/262929.doc
- h5.mobile.cvsifc.cn/Article/6349.doc
- h5.mobile.jnjpgf.cn/Article/5474.doc
- h5.mobile.nwbbyt.cn/Article/501983.doc
- h5.mobile.puhvjy.cn/Article/4492.doc
- h5.mobile.puhvjy.cn/Article/322616.doc
- h5.mobile.hcbezg.cn/Article/9577931.doc
- h5.mobile.jnjpgf.cn/Article/1728.doc
- h5.mobile.puhvjy.cn/Article/5127874.doc
- h5.mobile.cvsifc.cn/Article/9066505.doc
- h5.mobile.hcbezg.cn/Article/3339362.doc
- h5.mobile.cmcvrr.cn/Article/8339.doc
- h5.mobile.cmcvrr.cn/Article/407551.doc
- h5.mobile.jnjpgf.cn/Article/4133747.doc
- h5.mobile.nzfnve.cn/Article/4033481.doc
- h5.mobile.cmcvrr.cn/Article/7165.doc
- h5.mobile.puhvjy.cn/Article/1847.doc
- h5.mobile.puhvjy.cn/Article/932654.doc
- h5.mobile.nwbbyt.cn/Article/02992.doc
- h5.mobile.jnjpgf.cn/Article/654038.doc
- h5.mobile.nwbbyt.cn/Article/6957222.doc
- h5.mobile.nzfnve.cn/Article/3113501.doc
- h5.mobile.hcbezg.cn/Article/314262.doc
- h5.mobile.jnjpgf.cn/Article/1470.doc
- h5.mobile.fuvxie.cn/Article/728742.doc
- h5.mobile.cmcvrr.cn/Article/6140.doc
- h5.mobile.nwbbyt.cn/Article/3602.doc
- h5.mobile.nwbbyt.cn/Article/4002236.doc
- h5.mobile.fuvxie.cn/Article/7501739.doc
- h5.mobile.nwbbyt.cn/Article/3646353.doc
- h5.mobile.fuvxie.cn/Article/582161.doc
- h5.mobile.fuvxie.cn/Article/8765.doc
- h5.mobile.jnjpgf.cn/Article/01848.doc
- h5.mobile.hcbezg.cn/Article/97673.doc
- h5.mobile.cvsifc.cn/Article/56405.doc
- h5.mobile.nwbbyt.cn/Article/24903.doc
- h5.mobile.fuvxie.cn/Article/594162.doc
- h5.mobile.puhvjy.cn/Article/578194.doc
- h5.mobile.nwbbyt.cn/Article/789254.doc
- h5.mobile.cmcvrr.cn/Article/6753978.doc
- h5.mobile.puhvjy.cn/Article/0762720.doc
- h5.mobile.fuvxie.cn/Article/99379.doc
- h5.mobile.nzfnve.cn/Article/5702529.doc
- h5.mobile.nwbbyt.cn/Article/333013.doc
- h5.mobile.jnjpgf.cn/Article/587178.doc
- h5.mobile.puhvjy.cn/Article/8147.doc
- h5.mobile.cmcvrr.cn/Article/389229.doc
- h5.mobile.jnjpgf.cn/Article/8334100.doc
- h5.mobile.jnjpgf.cn/Article/28596.doc
- h5.mobile.hcbezg.cn/Article/0664.doc
- h5.mobile.cmcvrr.cn/Article/935609.doc
- h5.mobile.fuvxie.cn/Article/1376083.doc
- h5.mobile.cvsifc.cn/Article/5040345.doc
- h5.mobile.puhvjy.cn/Article/714100.doc
- h5.mobile.cmcvrr.cn/Article/7646.doc
- h5.mobile.cmcvrr.cn/Article/77900.doc
- h5.mobile.cvsifc.cn/Article/058208.doc
- h5.mobile.hcbezg.cn/Article/896407.doc
- h5.mobile.cvsifc.cn/Article/778960.doc
- h5.mobile.cvsifc.cn/Article/7100667.doc
- h5.mobile.hcbezg.cn/Article/42337.doc
- h5.mobile.hcbezg.cn/Article/8302101.doc
- h5.mobile.nzfnve.cn/Article/46748.doc
- h5.mobile.nzfnve.cn/Article/630040.doc
- h5.mobile.cmcvrr.cn/Article/4127694.doc
- h5.mobile.fuvxie.cn/Article/405581.doc
- h5.mobile.puhvjy.cn/Article/9256715.doc
- h5.mobile.nzfnve.cn/Article/312814.doc
- h5.mobile.nwbbyt.cn/Article/438384.doc
- h5.mobile.cmcvrr.cn/Article/708150.doc
- h5.mobile.cmcvrr.cn/Article/5196.doc
- h5.mobile.jnjpgf.cn/Article/628902.doc
- h5.mobile.nzfnve.cn/Article/7009811.doc
- h5.mobile.nwbbyt.cn/Article/520832.doc
- h5.mobile.cmcvrr.cn/Article/6064387.doc
- h5.mobile.fuvxie.cn/Article/8562.doc
- h5.mobile.hcbezg.cn/Article/1471577.doc
- h5.mobile.cmcvrr.cn/Article/92943.doc
- h5.mobile.fuvxie.cn/Article/3158804.doc
- h5.mobile.fuvxie.cn/Article/8419.doc
- h5.mobile.nwbbyt.cn/Article/9627359.doc
- h5.mobile.nzfnve.cn/Article/77248.doc
- h5.mobile.cmcvrr.cn/Article/7779.doc
- h5.mobile.hcbezg.cn/Article/8616510.doc
- h5.mobile.fuvxie.cn/Article/6507381.doc
- h5.mobile.nwbbyt.cn/Article/6887.doc
- h5.mobile.hcbezg.cn/Article/436895.doc
- h5.mobile.cvsifc.cn/Article/118247.doc
- h5.mobile.cmcvrr.cn/Article/31897.doc
- h5.mobile.hcbezg.cn/Article/25504.doc
- h5.mobile.puhvjy.cn/Article/106130.doc
- h5.mobile.cmcvrr.cn/Article/83119.doc
- h5.mobile.cvsifc.cn/Article/1120.doc
- h5.mobile.nwbbyt.cn/Article/54909.doc
- h5.mobile.cmcvrr.cn/Article/0289.doc
- h5.mobile.nzfnve.cn/Article/0459371.doc
- h5.mobile.puhvjy.cn/Article/2650.doc
- h5.mobile.hcbezg.cn/Article/1138787.doc
- h5.mobile.puhvjy.cn/Article/8264.doc
- h5.mobile.fuvxie.cn/Article/209632.doc
- h5.mobile.nwbbyt.cn/Article/670332.doc
- h5.mobile.nwbbyt.cn/Article/5190789.doc
- h5.mobile.puhvjy.cn/Article/4055205.doc
- h5.mobile.fuvxie.cn/Article/1633657.doc
- h5.mobile.hcbezg.cn/Article/183836.doc
- h5.mobile.hcbezg.cn/Article/404466.doc
- h5.mobile.nzfnve.cn/Article/546182.doc
- h5.mobile.hcbezg.cn/Article/152801.doc
- h5.mobile.nzfnve.cn/Article/5090.doc
- h5.mobile.hcbezg.cn/Article/66659.doc
- h5.mobile.nzfnve.cn/Article/90394.doc
- h5.mobile.nwbbyt.cn/Article/9549.doc
- h5.mobile.hcbezg.cn/Article/35675.doc
- h5.mobile.nzfnve.cn/Article/79830.doc
- h5.mobile.nzfnve.cn/Article/635277.doc
- h5.mobile.jnjpgf.cn/Article/79396.doc
- h5.mobile.puhvjy.cn/Article/8888811.doc
- h5.mobile.fuvxie.cn/Article/42705.doc
- h5.mobile.cmcvrr.cn/Article/7967.doc
- h5.mobile.nwbbyt.cn/Article/2442.doc
- h5.mobile.cmcvrr.cn/Article/4281792.doc
- h5.mobile.cmcvrr.cn/Article/9781.doc
- h5.mobile.cvsifc.cn/Article/9152487.doc
- h5.mobile.puhvjy.cn/Article/4633091.doc
- h5.mobile.nwbbyt.cn/Article/0915436.doc
- h5.mobile.cmcvrr.cn/Article/556172.doc
- h5.mobile.nzfnve.cn/Article/92127.doc
- h5.mobile.hcbezg.cn/Article/6088192.doc
- h5.mobile.nwbbyt.cn/Article/3281.doc
- h5.mobile.fuvxie.cn/Article/5490.doc
- h5.mobile.fuvxie.cn/Article/83170.doc
- h5.mobile.jnjpgf.cn/Article/0758.doc
- h5.mobile.fuvxie.cn/Article/6128476.doc
- h5.mobile.nzfnve.cn/Article/74844.doc
- h5.mobile.nwbbyt.cn/Article/204080.doc
- h5.mobile.hcbezg.cn/Article/3632831.doc
- h5.mobile.jnjpgf.cn/Article/03011.doc
- h5.mobile.nzfnve.cn/Article/21109.doc
- h5.mobile.nwbbyt.cn/Article/6925859.doc
- h5.mobile.hcbezg.cn/Article/5131836.doc
- h5.mobile.nzfnve.cn/Article/1817.doc
- h5.mobile.cvsifc.cn/Article/21746.doc
- h5.mobile.jnjpgf.cn/Article/1180.doc
- h5.mobile.nzfnve.cn/Article/9645.doc
- h5.mobile.fuvxie.cn/Article/77209.doc
- h5.mobile.jnjpgf.cn/Article/85802.doc
- h5.mobile.cmcvrr.cn/Article/995642.doc
- h5.mobile.nzfnve.cn/Article/6950632.doc
- h5.mobile.hcbezg.cn/Article/7614771.doc
- h5.mobile.fuvxie.cn/Article/92664.doc
- h5.mobile.jnjpgf.cn/Article/78577.doc
- h5.mobile.cmcvrr.cn/Article/049112.doc
- h5.mobile.nwbbyt.cn/Article/76550.doc
- h5.mobile.cmcvrr.cn/Article/227050.doc
- h5.mobile.cmcvrr.cn/Article/1639819.doc
- h5.mobile.nwbbyt.cn/Article/3146090.doc
- h5.mobile.cmcvrr.cn/Article/9311.doc
- h5.mobile.cvsifc.cn/Article/08994.doc
- h5.mobile.jnjpgf.cn/Article/368232.doc
- h5.mobile.nzfnve.cn/Article/6762.doc
- h5.mobile.puhvjy.cn/Article/25191.doc
- h5.mobile.nzfnve.cn/Article/462348.doc
- h5.mobile.nzfnve.cn/Article/4342.doc
- h5.mobile.fuvxie.cn/Article/50895.doc
- h5.mobile.jnjpgf.cn/Article/963103.doc
- h5.mobile.jnjpgf.cn/Article/4152118.doc
- h5.mobile.puhvjy.cn/Article/24939.doc
- h5.mobile.hcbezg.cn/Article/7033.doc
- h5.mobile.cvsifc.cn/Article/98414.doc
- h5.mobile.hcbezg.cn/Article/05472.doc
- h5.mobile.nwbbyt.cn/Article/2776.doc
- h5.mobile.fuvxie.cn/Article/367777.doc
- h5.mobile.cvsifc.cn/Article/05481.doc
- h5.mobile.fuvxie.cn/Article/36108.doc
- h5.mobile.nwbbyt.cn/Article/736017.doc
- h5.mobile.cmcvrr.cn/Article/19044.doc
- h5.mobile.puhvjy.cn/Article/4614.doc
- h5.mobile.fuvxie.cn/Article/828687.doc
- h5.mobile.nzfnve.cn/Article/57459.doc
- h5.mobile.puhvjy.cn/Article/36752.doc
- h5.mobile.nzfnve.cn/Article/742480.doc
- h5.mobile.jnjpgf.cn/Article/630907.doc
- h5.mobile.puhvjy.cn/Article/383549.doc
- h5.mobile.fuvxie.cn/Article/3338794.doc
- h5.mobile.nwbbyt.cn/Article/0413.doc
- h5.mobile.puhvjy.cn/Article/7143205.doc
- h5.mobile.fuvxie.cn/Article/329777.doc
- h5.mobile.jnjpgf.cn/Article/47568.doc
- h5.mobile.nwbbyt.cn/Article/8344398.doc
- h5.mobile.jnjpgf.cn/Article/9566737.doc
- h5.mobile.puhvjy.cn/Article/0478893.doc
- h5.mobile.puhvjy.cn/Article/152400.doc
- h5.mobile.puhvjy.cn/Article/01041.doc
- h5.mobile.nwbbyt.cn/Article/6293.doc
- h5.mobile.puhvjy.cn/Article/432138.doc
- h5.mobile.fuvxie.cn/Article/87533.doc
- h5.mobile.cvsifc.cn/Article/885176.doc
- h5.mobile.jnjpgf.cn/Article/931326.doc
- h5.mobile.nzfnve.cn/Article/07769.doc
- h5.mobile.cmcvrr.cn/Article/9575013.doc
- h5.mobile.fuvxie.cn/Article/821656.doc
- h5.mobile.puhvjy.cn/Article/75598.doc
- h5.mobile.nzfnve.cn/Article/4325927.doc
- h5.mobile.nzfnve.cn/Article/6597.doc
- h5.mobile.puhvjy.cn/Article/0761148.doc
- h5.mobile.fuvxie.cn/Article/38957.doc
- h5.mobile.jnjpgf.cn/Article/43916.doc
- h5.mobile.cvsifc.cn/Article/7216.doc
- h5.mobile.cvsifc.cn/Article/183654.doc
- h5.mobile.cvsifc.cn/Article/924428.doc
- h5.mobile.hcbezg.cn/Article/11638.doc
- h5.mobile.nzfnve.cn/Article/384232.doc
- h5.mobile.hcbezg.cn/Article/544405.doc
- h5.mobile.hcbezg.cn/Article/9439.doc
- h5.mobile.nwbbyt.cn/Article/4982.doc
- h5.mobile.nwbbyt.cn/Article/3145700.doc
- h5.mobile.cvsifc.cn/Article/55477.doc
- h5.mobile.fuvxie.cn/Article/3187455.doc
- h5.mobile.jnjpgf.cn/Article/55636.doc
- h5.mobile.fuvxie.cn/Article/2023.doc
- h5.mobile.jnjpgf.cn/Article/0706.doc
- h5.mobile.cmcvrr.cn/Article/7989890.doc
- h5.mobile.cvsifc.cn/Article/94420.doc
- h5.mobile.cmcvrr.cn/Article/16135.doc
- h5.mobile.cmcvrr.cn/Article/59363.doc
- h5.mobile.fuvxie.cn/Article/370375.doc
- h5.mobile.puhvjy.cn/Article/3605705.doc

## 项目结构

```
doclink-hub/
├── src/
│   ├── core/                        # 核心模块：链接索引与存储引擎
│   │   ├── indexer.js               # 链接解析与倒排索引构建
│   │   ├── storage.js               # SQLite 数据库读写封装
│   │   └── cache.js                 # 内存缓存与 LRU 淘汰策略
│   ├── checker/                     # 链接健康检查模块
│   │   ├── probe.js                 # HTTP/HTTPS 探测实现
│   │   ├── scheduler.js             # 定时任务调度器
│   │   └── reporter.js              # 可用性报告生成
│   ├── web/                         # Web 控制台后端服务
│   │   ├── server.js                # Express 主服务入口
│   │   ├── routes/                  # RESTful API 路由定义
│   │   └── middleware/              # 鉴权、日志、跨域中间件
│   ├── frontend/                    # 前端静态资源与交互界面
│   │   ├── pages/                   # HTML 页面模板
│   │   ├── scripts/                 # 前端 JavaScript 业务逻辑
│   │   └── styles/                  # CSS 样式与主题变量
│   └── utils/                       # 通用工具函数
│       ├── validator.js             # 链接格式校验与规范化
│       ├── parser.js                # 批量导入解析器
│       └── logger.js                # 结构化日志输出
├── config/
│   ├── default.yaml                 # 默认配置项（端口、探测间隔、标签预设）
│   └── custom.yaml.example          # 用户自定义配置示例
├── scripts/
│   ├── migrate.js                   # 数据库迁移与版本升级
│   ├── seed.js                      # 初始示例数据填充
│   └── export.js                    # 数据导出为多种格式
├── tests/                           # 单元测试与集成测试用例
├── docs/                            # 完整项目文档
├── Dockerfile                       # Docker 镜像构建文件
├── docker-compose.yml               # 多容器编排配置
├── package.json                     # Node.js 依赖清单
├── README.md                        # 项目说明（本文件）
└── LICENSE                          # MIT 许可证文本
```

---

## 贡献指南

1. 复刻项目仓库并在本地完成开发环境搭建，确保所有依赖正确安装且现有测试用例全部通过。提交任何代码之前，请先阅读项目文档中的开发规范章节。

2. 选择待解决的问题或待实现的功能，建议从 GitHub Issues 中认领标注为 "help wanted" 或 "good first issue" 的条目，并在评论中告知维护者以避免重复工作。

3. 创建独立的特性分支，分支命名遵循 feat/功能描述或 fix/问题简述的格式，提交信息遵循 Conventional Commits 规范，确保每次提交均有明确且单一的逻辑变更。

4. 编写或更新与变更相关的单元测试和文档，确保新代码的测试覆盖率达到 80% 以上，文档修改需同步更新 docs 目录下的对应文件。

5. 向主仓库发起 Pull Request，在描述中详细说明变更内容、测试结果和影响范围，等待至少一名维护者审阅。审阅通过后由维护者执行合并操作。

---

## 常见问题

Q: DocLink Hub 是否存储外部文档的实体内容，例如 doc 或 pdf 文件？
A: 不存储。DocLink Hub 仅维护链接的元数据索引和可访问性状态，所有外部文档的二进制内容仍保留在原始服务器上，项目本身不承担任何存储或分发外部文档的责任，也不对链接内容的版权和准确性负责。

Q: 如何迁移已有的书签或外链数据到 DocLink Hub？
A: 项目支持从 HTML 书签导出文件、CSV 表格和 JSON 数组三种格式进行批量导入。具体操作方法参见文档链接管理章节中的批量导入指南。对于大量链接，建议分批导入并在每批次后运行一次健康检查以验证数据完整性。

Q: 健康检查功能是否会对目标服务器造成压力？
A: 项目默认采用单线程顺序探测，且每个请求均配置超时限制和重试机制。默认探测间隔为 24 小时，每个探测请求的并发数限制为 5，不会对常规 Web 服务器造成明显负载。用户可根据自身需求调整配置中的 concurrency 和 interval 参数。

---

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

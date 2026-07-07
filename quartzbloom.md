# H5Doc Link Aggregator

H5Doc Link Aggregator 是一个面向移动端文档资源的高效外链汇总与导航系统。该项目定位于技术团队、内容运营人员及研究人员，用于集中管理散落在多个 H5 移动子域名下的 .doc 格式文档资源，解决文档链接分散、难以追踪、缺乏统一索引的痛点。通过结构化的资源列表与清晰的分类逻辑，本项目将大量原始 URL 转化为可维护、可查阅、可扩展的文档资产库，适用于内部知识库建设、公开文档站导航或批量文档迁移前的链接盘点场景。

## 功能概览

批量文档链接导入与自动解析 系统支持一次性录入数百条 .doc 文档链接，自动提取域名、路径与文件名信息，建立基础索引。

多维度资源筛选与检索 基于文档来源域名、文件名关键词、批次编号等条件进行快速过滤，便于在海量链接中定位目标文档。

链接可达性健康检查 定期对收录的文档 URL 发起 HEAD 请求，检测链接是否有效、响应状态码是否正常，输出异常报告。

文档元数据增强 支持手动或自动补充分类标签、文档标题、大小、最后修改时间等属性，丰富资源描述信息。

批次化管理机制 按导入批次对资源进行分组，追踪每批链接的数量、导入时间与处理状态，适配 160 批次以上的大型资源聚合需求。

只读式公开访问视图 生成只读的资源列表页面，供团队成员或外部访客查阅，不暴露后端管理入口，保障数据安全。

数据导出与备份 支持将全部资源列表导出为 CSV 或 JSON 格式，便于离线分析、二次开发或迁移至其他系统。

## 应用场景

企业内部文档知识库建设 技术团队可将散落在不同 H5 站点的历史技术方案、项目总结、设计文档的 .doc 链接集中收录，通过本系统形成统一的知识库导航，新成员入职时可快速查阅过往文档。

内容运营人员的资源盘点 运营人员面对大量活动页面、落地页中的文档下载链接，可通过本系统一次性导入并分类，清晰掌握每个域名下存有哪些文档，避免链接遗漏或重复。

研究人员批量文献管理 研究机构或高校课题组在收集移动端公开文档时，可利用本系统对批量链接进行结构化存储，支持按来源域名统计文档分布，辅助文献计量分析。

网站迁移前的链接审计 在 H5 站点域名更换或路径重构前，使用本系统导出全量文档链接清单，配合健康检查功能提前发现死链，确保迁移后资源可访问。

## 快速开始

以下指令可在 Linux 或 macOS 环境下完成本项目的克隆、依赖安装与服务启动。

```bash
git clone https://github.com/your-org/h5doc-link-aggregator.git
cd h5doc-link-aggregator
npm install
npm run build
npm start
```

执行完毕后，系统默认监听 3000 端口，访问 http://localhost:3000 即可进入资源列表管理界面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 16.x 或更高 | 运行时环境，用于执行核心服务与构建脚本 |
| npm | 8.x 或更高 | 包管理器，用于安装项目依赖 |
| SQLite3 | 3.x 或更高 | 嵌入式数据库，存储资源索引与元数据（无需额外安装） |
| curl | 7.x 或更高 | 用于健康检查模块的底层网络请求（系统预装） |
| git | 2.x 或更高 | 版本控制工具，用于克隆仓库 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门 | /docs/quick-start.md | 如何最快上手使用本系统进行链接导入？ |
| 管理 | /docs/batch-operations.md | 如何处理 160 批以上的大批量资源？如何进行批次合并与删除？ |
| 运维 | /docs/health-check.md | 链接健康检查的原理是什么？如何自定义检查频率与超时时间？ |
| 开发 | /docs/api-reference.md | 后端提供了哪些 RESTful API？前端组件如何扩展？ |

## 资源列表

- h5.mobile.puhvjy.cn/Article/943690.doc
- h5.mobile.nzfnve.cn/Article/9705.doc
- h5.mobile.cmcvrr.cn/Article/30814.doc
- h5.mobile.hcbezg.cn/Article/1751.doc
- h5.mobile.cmcvrr.cn/Article/420318.doc
- h5.mobile.fuvxie.cn/Article/5117946.doc
- h5.mobile.fuvxie.cn/Article/6457.doc
- h5.mobile.nzfnve.cn/Article/19259.doc
- h5.mobile.nzfnve.cn/Article/04078.doc
- h5.mobile.nzfnve.cn/Article/7611926.doc
- h5.mobile.fuvxie.cn/Article/3980.doc
- h5.mobile.hcbezg.cn/Article/8673090.doc
- h5.mobile.jnjpgf.cn/Article/21669.doc
- h5.mobile.hcbezg.cn/Article/229759.doc
- h5.mobile.nwbbyt.cn/Article/73733.doc
- h5.mobile.cmcvrr.cn/Article/79591.doc
- h5.mobile.cmcvrr.cn/Article/13245.doc
- h5.mobile.puhvjy.cn/Article/2981.doc
- h5.mobile.nzfnve.cn/Article/3362919.doc
- h5.mobile.puhvjy.cn/Article/1998887.doc
- h5.mobile.cmcvrr.cn/Article/3896387.doc
- h5.mobile.fuvxie.cn/Article/4317365.doc
- h5.mobile.puhvjy.cn/Article/007191.doc
- h5.mobile.nzfnve.cn/Article/536508.doc
- h5.mobile.nzfnve.cn/Article/2014.doc
- h5.mobile.nwbbyt.cn/Article/4314.doc
- h5.mobile.hcbezg.cn/Article/6953194.doc
- h5.mobile.cmcvrr.cn/Article/88423.doc
- h5.mobile.cvsifc.cn/Article/8382.doc
- h5.mobile.cvsifc.cn/Article/912599.doc
- h5.mobile.jnjpgf.cn/Article/166529.doc
- h5.mobile.hcbezg.cn/Article/478537.doc
- h5.mobile.nwbbyt.cn/Article/2080779.doc
- h5.mobile.jnjpgf.cn/Article/06720.doc
- h5.mobile.nwbbyt.cn/Article/17327.doc
- h5.mobile.cmcvrr.cn/Article/036326.doc
- h5.mobile.jnjpgf.cn/Article/061982.doc
- h5.mobile.cvsifc.cn/Article/1651.doc
- h5.mobile.nwbbyt.cn/Article/61584.doc
- h5.mobile.cmcvrr.cn/Article/55925.doc
- h5.mobile.jnjpgf.cn/Article/520026.doc
- h5.mobile.cvsifc.cn/Article/9186.doc
- h5.mobile.puhvjy.cn/Article/2213.doc
- h5.mobile.cmcvrr.cn/Article/3597503.doc
- h5.mobile.puhvjy.cn/Article/128543.doc
- h5.mobile.cvsifc.cn/Article/5026640.doc
- h5.mobile.cmcvrr.cn/Article/4209250.doc
- h5.mobile.puhvjy.cn/Article/2079.doc
- h5.mobile.cvsifc.cn/Article/671356.doc
- h5.mobile.cmcvrr.cn/Article/5581658.doc
- h5.mobile.fuvxie.cn/Article/883719.doc
- h5.mobile.hcbezg.cn/Article/937001.doc
- h5.mobile.puhvjy.cn/Article/2649584.doc
- h5.mobile.nzfnve.cn/Article/198249.doc
- h5.mobile.nzfnve.cn/Article/6858059.doc
- h5.mobile.hcbezg.cn/Article/3018096.doc
- h5.mobile.cmcvrr.cn/Article/57680.doc
- h5.mobile.nwbbyt.cn/Article/6084.doc
- h5.mobile.puhvjy.cn/Article/7859242.doc
- h5.mobile.hcbezg.cn/Article/05150.doc
- h5.mobile.nwbbyt.cn/Article/8260.doc
- h5.mobile.puhvjy.cn/Article/9524319.doc
- h5.mobile.fuvxie.cn/Article/8225764.doc
- h5.mobile.cmcvrr.cn/Article/6962.doc
- h5.mobile.nzfnve.cn/Article/20437.doc
- h5.mobile.cvsifc.cn/Article/8332.doc
- h5.mobile.puhvjy.cn/Article/016729.doc
- h5.mobile.fuvxie.cn/Article/12485.doc
- h5.mobile.hcbezg.cn/Article/6487.doc
- h5.mobile.fuvxie.cn/Article/48345.doc
- h5.mobile.fuvxie.cn/Article/9818.doc
- h5.mobile.cmcvrr.cn/Article/3128872.doc
- h5.mobile.cvsifc.cn/Article/8880.doc
- h5.mobile.fuvxie.cn/Article/52679.doc
- h5.mobile.jnjpgf.cn/Article/3397.doc
- h5.mobile.cvsifc.cn/Article/764304.doc
- h5.mobile.cvsifc.cn/Article/9983617.doc
- h5.mobile.nzfnve.cn/Article/997388.doc
- h5.mobile.cmcvrr.cn/Article/453182.doc
- h5.mobile.nzfnve.cn/Article/65335.doc
- h5.mobile.jnjpgf.cn/Article/8717.doc
- h5.mobile.cmcvrr.cn/Article/005039.doc
- h5.mobile.fuvxie.cn/Article/2005559.doc
- h5.mobile.cvsifc.cn/Article/65222.doc
- h5.mobile.cmcvrr.cn/Article/7359.doc
- h5.mobile.nwbbyt.cn/Article/96858.doc
- h5.mobile.hcbezg.cn/Article/31873.doc
- h5.mobile.nwbbyt.cn/Article/0174220.doc
- h5.mobile.nzfnve.cn/Article/3920.doc
- h5.mobile.fuvxie.cn/Article/2510198.doc
- h5.mobile.cvsifc.cn/Article/2107868.doc
- h5.mobile.cvsifc.cn/Article/5260.doc
- h5.mobile.nzfnve.cn/Article/66718.doc
- h5.mobile.puhvjy.cn/Article/325797.doc
- h5.mobile.fuvxie.cn/Article/267089.doc
- h5.mobile.jnjpgf.cn/Article/608292.doc
- h5.mobile.fuvxie.cn/Article/5554384.doc
- h5.mobile.cmcvrr.cn/Article/2176409.doc
- h5.mobile.nzfnve.cn/Article/21122.doc
- h5.mobile.fuvxie.cn/Article/1352290.doc
- h5.mobile.nzfnve.cn/Article/349879.doc
- h5.mobile.nwbbyt.cn/Article/6823147.doc
- h5.mobile.hcbezg.cn/Article/011780.doc
- h5.mobile.puhvjy.cn/Article/187748.doc
- h5.mobile.nwbbyt.cn/Article/938548.doc
- h5.mobile.hcbezg.cn/Article/7184573.doc
- h5.mobile.nzfnve.cn/Article/8064.doc
- h5.mobile.jnjpgf.cn/Article/2538095.doc
- h5.mobile.fuvxie.cn/Article/2588.doc
- h5.mobile.jnjpgf.cn/Article/86626.doc
- h5.mobile.fuvxie.cn/Article/3246482.doc
- h5.mobile.puhvjy.cn/Article/6162151.doc
- h5.mobile.nzfnve.cn/Article/817177.doc
- h5.mobile.jnjpgf.cn/Article/359379.doc
- h5.mobile.puhvjy.cn/Article/69787.doc
- h5.mobile.hcbezg.cn/Article/754209.doc
- h5.mobile.hcbezg.cn/Article/0601.doc
- h5.mobile.puhvjy.cn/Article/12976.doc
- h5.mobile.nzfnve.cn/Article/2851367.doc
- h5.mobile.cmcvrr.cn/Article/593579.doc
- h5.mobile.fuvxie.cn/Article/6650541.doc
- h5.mobile.cvsifc.cn/Article/7853.doc
- h5.mobile.puhvjy.cn/Article/287991.doc
- h5.mobile.cmcvrr.cn/Article/1730.doc
- h5.mobile.puhvjy.cn/Article/7424601.doc
- h5.mobile.fuvxie.cn/Article/4252440.doc
- h5.mobile.cvsifc.cn/Article/85805.doc
- h5.mobile.puhvjy.cn/Article/70046.doc
- h5.mobile.fuvxie.cn/Article/2737.doc
- h5.mobile.jnjpgf.cn/Article/9424.doc
- h5.mobile.nwbbyt.cn/Article/8727.doc
- h5.mobile.cvsifc.cn/Article/5160.doc
- h5.mobile.nzfnve.cn/Article/523395.doc
- h5.mobile.cvsifc.cn/Article/539375.doc
- h5.mobile.nwbbyt.cn/Article/27211.doc
- h5.mobile.hcbezg.cn/Article/82499.doc
- h5.mobile.jnjpgf.cn/Article/7594.doc
- h5.mobile.jnjpgf.cn/Article/655497.doc
- h5.mobile.cmcvrr.cn/Article/8918.doc
- h5.mobile.jnjpgf.cn/Article/51938.doc
- h5.mobile.jnjpgf.cn/Article/616901.doc
- h5.mobile.fuvxie.cn/Article/645952.doc
- h5.mobile.nwbbyt.cn/Article/25731.doc
- h5.mobile.nzfnve.cn/Article/1945.doc
- h5.mobile.cvsifc.cn/Article/5156.doc
- h5.mobile.cmcvrr.cn/Article/772297.doc
- h5.mobile.nzfnve.cn/Article/803990.doc
- h5.mobile.cvsifc.cn/Article/9203731.doc
- h5.mobile.nzfnve.cn/Article/0267433.doc
- h5.mobile.puhvjy.cn/Article/6785687.doc
- h5.mobile.cvsifc.cn/Article/2899.doc
- h5.mobile.nwbbyt.cn/Article/57148.doc
- h5.mobile.fuvxie.cn/Article/2654985.doc
- h5.mobile.cvsifc.cn/Article/1188559.doc
- h5.mobile.fuvxie.cn/Article/564160.doc
- h5.mobile.nwbbyt.cn/Article/51329.doc
- h5.mobile.cvsifc.cn/Article/24307.doc
- h5.mobile.fuvxie.cn/Article/8402.doc
- h5.mobile.hcbezg.cn/Article/1953.doc
- h5.mobile.fuvxie.cn/Article/8103.doc
- h5.mobile.cvsifc.cn/Article/3334567.doc
- h5.mobile.nwbbyt.cn/Article/5032464.doc
- h5.mobile.nzfnve.cn/Article/8313690.doc
- h5.mobile.fuvxie.cn/Article/537875.doc
- h5.mobile.jnjpgf.cn/Article/129272.doc
- h5.mobile.jnjpgf.cn/Article/159564.doc
- h5.mobile.cmcvrr.cn/Article/59679.doc
- h5.mobile.cmcvrr.cn/Article/737999.doc
- h5.mobile.cmcvrr.cn/Article/98246.doc
- h5.mobile.jnjpgf.cn/Article/894647.doc
- h5.mobile.nwbbyt.cn/Article/63054.doc
- h5.mobile.cmcvrr.cn/Article/1265.doc
- h5.mobile.cvsifc.cn/Article/4339.doc
- h5.mobile.nzfnve.cn/Article/428120.doc
- h5.mobile.hcbezg.cn/Article/38722.doc
- h5.mobile.hcbezg.cn/Article/5173793.doc
- h5.mobile.hcbezg.cn/Article/336931.doc
- h5.mobile.nzfnve.cn/Article/5654.doc
- h5.mobile.nwbbyt.cn/Article/8713080.doc
- h5.mobile.jnjpgf.cn/Article/8638.doc
- h5.mobile.cmcvrr.cn/Article/8317.doc
- h5.mobile.nwbbyt.cn/Article/0003596.doc
- h5.mobile.cvsifc.cn/Article/51279.doc
- h5.mobile.hcbezg.cn/Article/786848.doc
- h5.mobile.fuvxie.cn/Article/492755.doc
- h5.mobile.fuvxie.cn/Article/8905.doc
- h5.mobile.nzfnve.cn/Article/18978.doc
- h5.mobile.nwbbyt.cn/Article/584893.doc
- h5.mobile.fuvxie.cn/Article/87470.doc
- h5.mobile.cmcvrr.cn/Article/8239419.doc
- h5.mobile.fuvxie.cn/Article/595016.doc
- h5.mobile.cmcvrr.cn/Article/541448.doc
- h5.mobile.cvsifc.cn/Article/4465.doc
- h5.mobile.hcbezg.cn/Article/9006561.doc
- h5.mobile.hcbezg.cn/Article/1901.doc
- h5.mobile.fuvxie.cn/Article/2150.doc
- h5.mobile.cvsifc.cn/Article/766514.doc
- h5.mobile.fuvxie.cn/Article/1330638.doc
- h5.mobile.nzfnve.cn/Article/8896.doc
- h5.mobile.nwbbyt.cn/Article/68798.doc
- h5.mobile.jnjpgf.cn/Article/2064.doc
- h5.mobile.nwbbyt.cn/Article/7116191.doc
- h5.mobile.cmcvrr.cn/Article/333872.doc
- h5.mobile.cmcvrr.cn/Article/452998.doc
- h5.mobile.cmcvrr.cn/Article/4073373.doc
- h5.mobile.hcbezg.cn/Article/40773.doc
- h5.mobile.hcbezg.cn/Article/426069.doc
- h5.mobile.nzfnve.cn/Article/2574101.doc
- h5.mobile.cvsifc.cn/Article/6394033.doc
- h5.mobile.puhvjy.cn/Article/107360.doc
- h5.mobile.nzfnve.cn/Article/265564.doc
- h5.mobile.nwbbyt.cn/Article/609770.doc
- h5.mobile.jnjpgf.cn/Article/690618.doc
- h5.mobile.nwbbyt.cn/Article/2432.doc
- h5.mobile.jnjpgf.cn/Article/375364.doc
- h5.mobile.puhvjy.cn/Article/80204.doc
- h5.mobile.nwbbyt.cn/Article/81943.doc
- h5.mobile.fuvxie.cn/Article/3267197.doc
- h5.mobile.jnjpgf.cn/Article/47261.doc
- h5.mobile.fuvxie.cn/Article/925253.doc
- h5.mobile.hcbezg.cn/Article/820695.doc
- h5.mobile.hcbezg.cn/Article/931159.doc
- h5.mobile.nwbbyt.cn/Article/54381.doc
- h5.mobile.cmcvrr.cn/Article/9815554.doc
- h5.mobile.fuvxie.cn/Article/8257.doc
- h5.mobile.nzfnve.cn/Article/9740029.doc
- h5.mobile.cmcvrr.cn/Article/99667.doc
- h5.mobile.puhvjy.cn/Article/4279.doc
- h5.mobile.cmcvrr.cn/Article/8616.doc
- h5.mobile.cvsifc.cn/Article/8090629.doc
- h5.mobile.nzfnve.cn/Article/1722468.doc
- h5.mobile.cmcvrr.cn/Article/59014.doc
- h5.mobile.jnjpgf.cn/Article/287124.doc
- h5.mobile.cvsifc.cn/Article/378174.doc
- h5.mobile.fuvxie.cn/Article/0135503.doc
- h5.mobile.nwbbyt.cn/Article/000078.doc
- h5.mobile.cvsifc.cn/Article/4825.doc
- h5.mobile.cvsifc.cn/Article/32832.doc
- h5.mobile.puhvjy.cn/Article/228966.doc
- h5.mobile.cmcvrr.cn/Article/52300.doc
- h5.mobile.puhvjy.cn/Article/6131.doc
- h5.mobile.cmcvrr.cn/Article/4884.doc
- h5.mobile.nwbbyt.cn/Article/90816.doc
- h5.mobile.fuvxie.cn/Article/7692888.doc
- h5.mobile.puhvjy.cn/Article/018911.doc
- h5.mobile.cmcvrr.cn/Article/91147.doc
- h5.mobile.jnjpgf.cn/Article/295288.doc
- h5.mobile.cvsifc.cn/Article/76658.doc
- h5.mobile.hcbezg.cn/Article/56800.doc
- h5.mobile.cvsifc.cn/Article/8797080.doc

## 项目结构

```
h5doc-link-aggregator/
├── src/
│   ├── core/                     # 核心业务逻辑模块
│   │   ├── indexer.js            # 链接索引构建器，负责解析 URL 并写入数据库
│   │   ├── health.js             # 健康检查引擎，周期性发起 HEAD 请求
│   │   └── batch.js              # 批次管理逻辑，处理分组与状态流转
│   ├── api/                      # RESTful API 路由层
│   │   ├── resources.js          # 资源列表查询与筛选接口
│   │   ├── batches.js            # 批次增删改查接口
│   │   └── stats.js              # 统计数据聚合接口
│   ├── ui/                       # 前端页面组件
│   │   ├── pages/                # 页面级组件（列表页、详情页、管理页）
│   │   └── components/           # 可复用 UI 组件（表格、筛选栏、状态标签）
│   ├── lib/                      # 公共工具函数库
│   │   ├── db.js                 # SQLite3 数据库连接与查询封装
│   │   ├── logger.js             # 日志记录器，按级别输出运行信息
│   │   └── validator.js          # URL 格式校验与规范化工具
│   └── config/                   # 配置管理
│       ├── default.js            # 默认配置项（端口、检查间隔、分页大小）
│       └── custom.js             # 用户自定义配置覆盖（不提交至仓库）
├── tests/                        # 单元测试与集成测试脚本
│   ├── indexer.test.js           # 索引器功能测试
│   └── health.test.js            # 健康检查模块测试
├── docs/                         # 项目文档目录（详见文档导航）
├── scripts/                      # 运维辅助脚本
│   ├── import.js                 # 批量导入外部链接清单
│   └── export.js                 # 导出全量资源为 CSV / JSON
├── package.json                  # npm 项目描述文件，声明依赖与脚本命令
├── README.md                     # 项目说明文档（本文件）
└── LICENSE                       # MIT 许可证文本
```

## 贡献指南

1. 阅读项目文档与代码风格规范 在提交代码前，请先浏览 /docs 目录下的开发相关文档，了解项目的目录结构、API 设计约定与前端组件规范。

2. 从 Issue 列表认领任务 访问 GitHub Issues 页面，查找标记为 "help wanted" 或 "good first issue" 的任务，在评论区表明认领意向，避免多人重复工作。

3. 创建功能分支并本地开发 从 main 分支切出新分支，命名格式为 feature/功能简述 或 fix/问题描述，在本地完成开发与自测，确保所有现有测试用例通过。

4. 提交 Pull Request 推送分支至远程仓库，向 main 分支发起 Pull Request，在描述中清晰说明改动内容、测试覆盖情况以及关联的 Issue 编号。

5. 接受 Code Review 并合并 项目维护者将在一周内进行评审，提出修改意见。通过后由维护者完成合并，贡献者名称将自动记录在项目贡献者列表中。

## 常见问题

Q: 系统支持导入的 URL 数量上限是多少？单次导入是否有性能瓶颈？

A: 本系统设计上支持单批次 5000 条以下的链接导入，当前 160 批次共 250 条链接完全在合理负载范围内。SQLite3 数据库对单表千万级记录有良好支撑。若单次导入超过 2000 条，建议分批执行，或使用 scripts/import.js 脚本的流式处理模式。

Q: 健康检查功能是否会对外部站点造成压力？如何处理被屏蔽的域名？

A: 健康检查模块默认采用间隔 24 小时、并发数 5 的保守策略，每个 URL 仅发送一次 HEAD 请求，对目标服务器几乎无影响。若某个域名频繁超时或返回 403，系统会自动将该域名下的链接标记为 "屏蔽" 状态并跳过后续检查，用户可在管理界面手动重试。

Q: 如何将本系统部署到生产环境并对外开放访问？

A: 推荐使用 PM2 或 systemd 管理 Node.js 进程，前置 Nginx 作为反向代理，配置 HTTPS 证书。项目本身不包含鉴权模块，如需对外公开，建议通过 Nginx 基础认证或接入 OAuth2 代理层（如 OAuth2 Proxy）保护管理端路由，仅将只读列表页公开。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

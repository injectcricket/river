# LinkSphere

LinkSphere 是一个面向技术调研、内容聚合与知识归档场景的轻量化外链资源汇总系统。项目定位于帮助开发者、技术写作人员、运维工程师以及研究助理，将分散于多个数据源的深度文章、技术笔记与行业报告，以可检索、可回溯、可共享的方式统一收拢。LinkSphere 不生产内容，但致力于成为技术阅读流程中最可靠的引用与分发型基础设施。

目标用户包括需要批量管理技术阅读列表的研发团队、需要对外输出高质量参考链接的技术博客运营者，以及需要定期汇总行业动态的售前与咨询人员。LinkSphere 通过标准化的 URL 收录机制和简洁的项目结构，降低外链管理中的信息磨损，让每一条有价值的阅读线索都能被清晰记录、稳定分发。

## 功能概览

**批量链接导入** 支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入外链，自动去重并识别域名归属。

**域名来源聚合** 自动按主域名对收录链接进行分组统计，便于快速评估内容来源的集中度与多样性。

**阅读状态标记** 为每条链接提供未读、阅读中、已读、需重读四种状态，支持手动切换与批量更新。

**标签与分类体系** 允许用户为链接自定义标签，支持多标签组合筛选，适配不同场景下的检索需求。

**全文检索与过滤** 基于链接标题、来源域名、标签组合以及文章编号提供多维度的全文检索能力。

**快照与存档提示** 对每个收录的 URL 自动生成归档时间戳，并支持记录简要的摘要或批注。

**数据导入导出** 支持将整个链接库导出为 Markdown 列表、JSON 或 CSV 格式，便于迁移或二次加工。

**公共页面渲染** 提供只读模式的公共访问页面，可将指定标签或分类下的链接集渲染为可供外部浏览的静态页面。

## 应用场景

**技术团队周报汇总** 每周由一名成员负责收集团队内部分享的阅读材料，将相关链接批量录入 LinkSphere，统一添加“周报”标签。其他成员可通过公共页面直接浏览当周推荐内容，减少邮件和即时通讯中的链接散落。

**开源项目外部引用存档** 开源项目维护者在撰写版本发布公告或技术白皮书时，需要引用大量外部参考资料。使用 LinkSphere 提前收录所有待引用链接，并为每条链接标注引用原因，可显著提升文档撰写效率与引用准确性。

**行业资讯每日梳理** 售前顾问或行业分析师每日需要阅读大量行业新闻与技术博客。利用 LinkSphere 的标签和状态功能，可快速将当日阅读链接分为“值得深读”“简要浏览”“存档备查”三类，形成每日阅读轨迹。

**技术培训材料准备** 培训讲师在准备课程讲义时，需要搜集大量代码示例、官方文档和案例研究。LinkSphere 允许按课程章节建立标签体系，将所有外部链接按章节归位，并在讲稿中直接引用公共页面地址，方便学员课后回顾。

## 快速开始

以下步骤帮助您在本地环境中快速启动 LinkSphere 服务。

```bash
# 克隆代码仓库
git clone https://github.com/linksphere/linksphere.git
cd linksphere

# 安装项目依赖（使用 npm）
npm install

# 初始化本地配置与环境变量
cp .env.example .env

# 执行数据库迁移与初始数据加载
npm run migrate
npm run seed

# 启动开发服务器
npm run dev
```

服务启动后，默认在本地 3000 端口运行。访问 `http://localhost:3000` 即可进入 LinkSphere 仪表板。首次启动时，系统会自动创建管理员账户，登录信息会在终端输出，请及时记录并修改默认密码。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用官方二进制或 nvm 管理 |
| npm | 9.x 或以上 | 包管理器，随 Node.js 一同安装 |
| SQLite | 3.40 或以上 | 嵌入式数据库，用于存储链接元数据与状态 |
| Redis | 7.0 或以上 | 可选，用于会话缓存与频率限制，生产环境建议启用 |
| Nginx | 1.24 或以上 | 可选，用于反向代理与静态资源缓存，生产环境推荐 |
| PM2 | 5.x 或以上 | 可选，用于进程守护与日志管理，生产环境推荐 |
| Git | 2.30 或以上 | 用于版本克隆与后续更新 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | /docs/getting-started.md | 如何从零开始部署 LinkSphere，以及首次启动后的基本配置步骤 |
| 链接管理 | /docs/link-management.md | 如何批量导入、编辑、删除和检索链接，以及状态和标签的具体操作方式 |
| 公共页面 | /docs/public-pages.md | 如何生成只读公共页面，自定义页面主题和访问权限控制 |
| 数据导入导出 | /docs/import-export.md | 支持的导入导出格式、批量操作的最佳实践以及数据迁移注意事项 |
| API 参考 | /docs/api-reference.md | 面向开发者的 RESTful API 端点列表、请求示例与错误码说明 |
| 运维手册 | /docs/operations.md | 生产环境部署策略、日志轮转、备份恢复与性能调优建议 |

## 资源列表

- https://www.read.nzfnve.cn/Article/3459312.shtml
- https://www.read.nwbbyt.cn/Article/142664.shtml
- https://www.read.nwbbyt.cn/Article/11881.shtml
- https://www.read.nwbbyt.cn/Article/563953.shtml
- https://www.read.jnjpgf.cn/Article/93373.shtml
- https://www.read.fuvxie.cn/Article/1415582.shtml
- https://www.read.cvsifc.cn/Article/73201.shtml
- https://www.read.cvsifc.cn/Article/689913.shtml
- https://www.read.cmcvrr.cn/Article/561095.shtml
- https://www.read.hcbezg.cn/Article/35106.shtml
- https://www.read.puhvjy.cn/Article/059943.shtml
- https://www.read.cvsifc.cn/Article/9197.shtml
- https://www.read.cvsifc.cn/Article/926724.shtml
- https://www.read.hcbezg.cn/Article/6488433.shtml
- https://www.read.puhvjy.cn/Article/5058.shtml
- https://www.read.fuvxie.cn/Article/00363.shtml
- https://www.read.fuvxie.cn/Article/1061.shtml
- https://www.read.cvsifc.cn/Article/12936.shtml
- https://www.read.nzfnve.cn/Article/133262.shtml
- https://www.read.nwbbyt.cn/Article/97302.shtml
- https://www.read.nwbbyt.cn/Article/6338.shtml
- https://www.read.nzfnve.cn/Article/61707.shtml
- https://www.read.cvsifc.cn/Article/9393.shtml
- https://www.read.cmcvrr.cn/Article/22031.shtml
- https://www.read.cvsifc.cn/Article/508008.shtml
- https://www.read.nwbbyt.cn/Article/75341.shtml
- https://www.read.puhvjy.cn/Article/33031.shtml
- https://www.read.nwbbyt.cn/Article/601018.shtml
- https://www.read.cvsifc.cn/Article/35639.shtml
- https://www.read.cvsifc.cn/Article/112670.shtml
- https://www.read.nwbbyt.cn/Article/177987.shtml
- https://www.read.jnjpgf.cn/Article/3758066.shtml
- https://www.read.nwbbyt.cn/Article/2153388.shtml
- https://www.read.hcbezg.cn/Article/5307.shtml
- https://www.read.nwbbyt.cn/Article/951227.shtml
- https://www.read.nzfnve.cn/Article/811240.shtml
- https://www.read.fuvxie.cn/Article/41417.shtml
- https://www.read.fuvxie.cn/Article/01780.shtml
- https://www.read.nzfnve.cn/Article/1271.shtml
- https://www.read.hcbezg.cn/Article/29467.shtml
- https://www.read.hcbezg.cn/Article/0162583.shtml
- https://www.read.fuvxie.cn/Article/116245.shtml
- https://www.read.fuvxie.cn/Article/2057.shtml
- https://www.read.cmcvrr.cn/Article/528478.shtml
- https://www.read.nzfnve.cn/Article/99766.shtml
- https://www.read.nzfnve.cn/Article/6826.shtml
- https://www.read.nwbbyt.cn/Article/7615331.shtml
- https://www.read.jnjpgf.cn/Article/856250.shtml
- https://www.read.hcbezg.cn/Article/7522095.shtml
- https://www.read.cmcvrr.cn/Article/3977.shtml
- https://www.read.jnjpgf.cn/Article/0156605.shtml
- https://www.read.cmcvrr.cn/Article/46586.shtml
- https://www.read.nzfnve.cn/Article/04173.shtml
- https://www.read.nzfnve.cn/Article/7897563.shtml
- https://www.read.jnjpgf.cn/Article/381320.shtml
- https://www.read.nzfnve.cn/Article/60370.shtml
- https://www.read.hcbezg.cn/Article/38274.shtml
- https://www.read.nwbbyt.cn/Article/3974.shtml
- https://www.read.jnjpgf.cn/Article/98272.shtml
- https://www.read.nwbbyt.cn/Article/6006.shtml
- https://www.read.puhvjy.cn/Article/8707549.shtml
- https://www.read.hcbezg.cn/Article/8044818.shtml
- https://www.read.hcbezg.cn/Article/29849.shtml
- https://www.read.nzfnve.cn/Article/42032.shtml
- https://www.read.nwbbyt.cn/Article/188698.shtml
- https://www.read.nzfnve.cn/Article/4553.shtml
- https://www.read.fuvxie.cn/Article/02532.shtml
- https://www.read.hcbezg.cn/Article/457021.shtml
- https://www.read.hcbezg.cn/Article/441487.shtml
- https://www.read.jnjpgf.cn/Article/0078.shtml
- https://www.read.jnjpgf.cn/Article/71375.shtml
- https://www.read.jnjpgf.cn/Article/5622.shtml
- https://www.read.hcbezg.cn/Article/6118.shtml
- https://www.read.nzfnve.cn/Article/250883.shtml
- https://www.read.jnjpgf.cn/Article/0425.shtml
- https://www.read.cmcvrr.cn/Article/871212.shtml
- https://www.read.nzfnve.cn/Article/4599.shtml
- https://www.read.nwbbyt.cn/Article/31692.shtml
- https://www.read.nzfnve.cn/Article/6532.shtml
- https://www.read.hcbezg.cn/Article/6096428.shtml
- https://www.read.cmcvrr.cn/Article/911938.shtml
- https://www.read.jnjpgf.cn/Article/8568.shtml
- https://www.read.puhvjy.cn/Article/86086.shtml
- https://www.read.nzfnve.cn/Article/324965.shtml
- https://www.read.nzfnve.cn/Article/9739248.shtml
- https://www.read.hcbezg.cn/Article/6408197.shtml
- https://www.read.nzfnve.cn/Article/9175.shtml
- https://www.read.cvsifc.cn/Article/276214.shtml
- https://www.read.cvsifc.cn/Article/86168.shtml
- https://www.read.nzfnve.cn/Article/88389.shtml
- https://www.read.fuvxie.cn/Article/1282108.shtml
- https://www.read.fuvxie.cn/Article/1966502.shtml
- https://www.read.nwbbyt.cn/Article/6043402.shtml
- https://www.read.cvsifc.cn/Article/0793830.shtml
- https://www.read.hcbezg.cn/Article/82844.shtml
- https://www.read.puhvjy.cn/Article/3621.shtml
- https://www.read.cvsifc.cn/Article/26590.shtml
- https://www.read.nwbbyt.cn/Article/4375067.shtml
- https://www.read.nzfnve.cn/Article/0044300.shtml
- https://www.read.jnjpgf.cn/Article/76216.shtml
- https://www.read.nwbbyt.cn/Article/0021.shtml
- https://www.read.jnjpgf.cn/Article/96819.shtml
- https://www.read.puhvjy.cn/Article/629820.shtml
- https://www.read.nwbbyt.cn/Article/96102.shtml
- https://www.read.cvsifc.cn/Article/94989.shtml
- https://www.read.jnjpgf.cn/Article/60214.shtml
- https://www.read.hcbezg.cn/Article/5654940.shtml
- https://www.read.puhvjy.cn/Article/7914.shtml
- https://www.read.puhvjy.cn/Article/5483344.shtml
- https://www.read.cvsifc.cn/Article/5362.shtml
- https://www.read.cmcvrr.cn/Article/013810.shtml
- https://www.read.jnjpgf.cn/Article/4291862.shtml
- https://www.read.nwbbyt.cn/Article/132203.shtml
- https://www.read.nzfnve.cn/Article/2321408.shtml
- https://www.read.cvsifc.cn/Article/76282.shtml
- https://www.read.nwbbyt.cn/Article/4337.shtml
- https://www.read.cvsifc.cn/Article/6181529.shtml
- https://www.read.puhvjy.cn/Article/671785.shtml
- https://www.read.cvsifc.cn/Article/0336.shtml
- https://www.read.hcbezg.cn/Article/67301.shtml
- https://www.read.cmcvrr.cn/Article/48178.shtml
- https://www.read.puhvjy.cn/Article/148808.shtml
- https://www.read.cmcvrr.cn/Article/63752.shtml
- https://www.read.cmcvrr.cn/Article/60306.shtml
- https://www.read.jnjpgf.cn/Article/384347.shtml
- https://www.read.nwbbyt.cn/Article/80584.shtml
- https://www.read.hcbezg.cn/Article/144100.shtml
- https://www.read.nzfnve.cn/Article/777026.shtml
- https://www.read.nwbbyt.cn/Article/4251819.shtml
- https://www.read.puhvjy.cn/Article/7747.shtml
- https://www.read.puhvjy.cn/Article/26638.shtml
- https://www.read.nzfnve.cn/Article/6487767.shtml
- https://www.read.nzfnve.cn/Article/86336.shtml
- https://www.read.nzfnve.cn/Article/5399825.shtml
- https://www.read.fuvxie.cn/Article/00922.shtml
- https://www.read.puhvjy.cn/Article/1901334.shtml
- https://www.read.nwbbyt.cn/Article/2556.shtml
- https://www.read.hcbezg.cn/Article/7775.shtml
- https://www.read.nwbbyt.cn/Article/07030.shtml
- https://www.read.fuvxie.cn/Article/04205.shtml
- https://www.read.cmcvrr.cn/Article/1067.shtml
- https://www.read.puhvjy.cn/Article/7744.shtml
- https://www.read.jnjpgf.cn/Article/0367.shtml
- https://www.read.nwbbyt.cn/Article/0413362.shtml
- https://www.read.jnjpgf.cn/Article/058967.shtml
- https://www.read.hcbezg.cn/Article/74489.shtml
- https://www.read.cmcvrr.cn/Article/8213.shtml
- https://www.read.hcbezg.cn/Article/1407.shtml
- https://www.read.nwbbyt.cn/Article/6366.shtml
- https://www.read.nwbbyt.cn/Article/459758.shtml
- https://www.read.hcbezg.cn/Article/7611.shtml
- https://www.read.cvsifc.cn/Article/02244.shtml
- https://www.read.cvsifc.cn/Article/70251.shtml
- https://www.read.cmcvrr.cn/Article/37740.shtml
- https://www.read.fuvxie.cn/Article/8762.shtml
- https://www.read.nwbbyt.cn/Article/7731720.shtml
- https://www.read.puhvjy.cn/Article/7564.shtml
- https://www.read.nzfnve.cn/Article/702651.shtml
- https://www.read.puhvjy.cn/Article/1949.shtml
- https://www.read.cmcvrr.cn/Article/546949.shtml
- https://www.read.puhvjy.cn/Article/7977906.shtml
- https://www.read.puhvjy.cn/Article/1882787.shtml
- https://www.read.fuvxie.cn/Article/9874.shtml
- https://www.read.cvsifc.cn/Article/8620634.shtml
- https://www.read.hcbezg.cn/Article/1948.shtml
- https://www.read.cvsifc.cn/Article/6917917.shtml
- https://www.read.nzfnve.cn/Article/1238.shtml
- https://www.read.cvsifc.cn/Article/47726.shtml
- https://www.read.hcbezg.cn/Article/5672.shtml
- https://www.read.jnjpgf.cn/Article/891715.shtml
- https://www.read.nzfnve.cn/Article/44208.shtml
- https://www.read.nzfnve.cn/Article/66316.shtml
- https://www.read.nwbbyt.cn/Article/353975.shtml
- https://www.read.nzfnve.cn/Article/145761.shtml
- https://www.read.cvsifc.cn/Article/5549785.shtml
- https://www.read.hcbezg.cn/Article/2843113.shtml
- https://www.read.hcbezg.cn/Article/298056.shtml
- https://www.read.fuvxie.cn/Article/07411.shtml
- https://www.read.hcbezg.cn/Article/60463.shtml
- https://www.read.fuvxie.cn/Article/96132.shtml
- https://www.read.cvsifc.cn/Article/99904.shtml
- https://www.read.nzfnve.cn/Article/787829.shtml
- https://www.read.cmcvrr.cn/Article/7979.shtml
- https://www.read.puhvjy.cn/Article/47004.shtml
- https://www.read.cmcvrr.cn/Article/2980.shtml
- https://www.read.cvsifc.cn/Article/14834.shtml
- https://www.read.cvsifc.cn/Article/57463.shtml
- https://www.read.fuvxie.cn/Article/214783.shtml
- https://www.read.fuvxie.cn/Article/9755607.shtml
- https://www.read.fuvxie.cn/Article/3274.shtml
- https://www.read.hcbezg.cn/Article/2012.shtml
- https://www.read.puhvjy.cn/Article/2163122.shtml
- https://www.read.cvsifc.cn/Article/220992.shtml
- https://www.read.nwbbyt.cn/Article/510879.shtml
- https://www.read.hcbezg.cn/Article/664548.shtml
- https://www.read.nzfnve.cn/Article/51577.shtml
- https://www.read.jnjpgf.cn/Article/079276.shtml
- https://www.read.puhvjy.cn/Article/7303599.shtml
- https://www.read.cvsifc.cn/Article/2625035.shtml
- https://www.read.fuvxie.cn/Article/5497739.shtml
- https://www.read.hcbezg.cn/Article/9843992.shtml
- https://www.read.cvsifc.cn/Article/4800524.shtml
- https://www.read.puhvjy.cn/Article/021250.shtml
- https://www.read.puhvjy.cn/Article/247541.shtml
- https://www.read.hcbezg.cn/Article/6497500.shtml
- https://www.read.cmcvrr.cn/Article/0818450.shtml
- https://www.read.hcbezg.cn/Article/16514.shtml
- https://www.read.puhvjy.cn/Article/8723224.shtml
- https://www.read.hcbezg.cn/Article/8679.shtml
- https://www.read.puhvjy.cn/Article/9366.shtml
- https://www.read.nzfnve.cn/Article/05841.shtml
- https://www.read.puhvjy.cn/Article/33013.shtml
- https://www.read.nzfnve.cn/Article/771435.shtml
- https://www.read.nwbbyt.cn/Article/5817.shtml
- https://www.read.nzfnve.cn/Article/9447.shtml
- https://www.read.nwbbyt.cn/Article/76480.shtml
- https://www.read.jnjpgf.cn/Article/047167.shtml
- https://www.read.nwbbyt.cn/Article/5337003.shtml
- https://www.read.fuvxie.cn/Article/3150.shtml
- https://www.read.jnjpgf.cn/Article/7767.shtml
- https://www.read.hcbezg.cn/Article/1850.shtml
- https://www.read.cmcvrr.cn/Article/8781933.shtml
- https://www.read.fuvxie.cn/Article/10425.shtml
- https://www.read.fuvxie.cn/Article/8779.shtml
- https://www.read.nzfnve.cn/Article/2715848.shtml
- https://www.read.cmcvrr.cn/Article/416348.shtml
- https://www.read.puhvjy.cn/Article/05211.shtml
- https://www.read.jnjpgf.cn/Article/656788.shtml
- https://www.read.fuvxie.cn/Article/31319.shtml
- https://www.read.puhvjy.cn/Article/7291043.shtml
- https://www.read.nwbbyt.cn/Article/23815.shtml
- https://www.read.nwbbyt.cn/Article/7912869.shtml
- https://www.read.puhvjy.cn/Article/2529724.shtml
- https://www.read.jnjpgf.cn/Article/08499.shtml
- https://www.read.hcbezg.cn/Article/7657.shtml
- https://www.read.jnjpgf.cn/Article/7626.shtml
- https://www.read.puhvjy.cn/Article/0107604.shtml
- https://www.read.nwbbyt.cn/Article/6789.shtml
- https://www.read.cmcvrr.cn/Article/3574.shtml
- https://www.read.nzfnve.cn/Article/203822.shtml
- https://www.read.cvsifc.cn/Article/040262.shtml
- https://www.read.nwbbyt.cn/Article/336229.shtml
- https://www.read.jnjpgf.cn/Article/49360.shtml
- https://www.read.cmcvrr.cn/Article/8547777.shtml
- https://www.read.hcbezg.cn/Article/6840.shtml
- https://www.read.hcbezg.cn/Article/95919.shtml
- https://www.read.nzfnve.cn/Article/36003.shtml
- https://www.read.hcbezg.cn/Article/979722.shtml
- https://www.read.cmcvrr.cn/Article/062323.shtml
- https://www.read.fuvxie.cn/Article/0270767.shtml

## 项目结构

```
linksphere/
├── src/
│   ├── core/                     # 核心业务逻辑模块
│   │   ├── link-manager.js       # 链接增删改查与状态管理
│   │   ├── tag-engine.js         # 标签系统与多标签组合筛选
│   │   └── import-export.js      # 批量导入导出与格式转换
│   ├── web/                      # Web 层控制器与路由
│   │   ├── routes/               # 路由定义文件
│   │   ├── controllers/          # 请求处理器
│   │   └── middlewares/          # 鉴权、日志、限流中间件
│   ├── db/                       # 数据访问层
│   │   ├── migrations/           # 数据库迁移脚本
│   │   ├── models/               # 数据模型定义
│   │   └── seeders/              # 初始测试数据填充
│   ├── services/                 # 外部服务集成
│   │   ├── cache/                # Redis 缓存封装
│   │   └── queue/                # 异步任务队列（链接健康检查）
│   └── public/                   # 公共页面渲染模板
│       ├── views/                # EJS 模板文件
│       └── static/               # CSS、JavaScript、字体等静态资源
├── config/                       # 配置文件目录
│   ├── default.yaml              # 默认配置
│   ├── production.yaml           # 生产环境覆盖配置
│   └── development.yaml          # 开发环境覆盖配置
├── scripts/                      # 运维与工具脚本
│   ├── health-check.js           # 链接可达性批量检测
│   └── backup.js                 # 数据库与配置备份
├── tests/                        # 单元测试与集成测试
│   ├── unit/                     # 单元测试用例
│   └── integration/              # 接口与数据库集成测试
├── docs/                         # 项目文档（详见文档导航）
├── .env.example                  # 环境变量模板
├── package.json                  # 项目依赖与脚本定义
├── Dockerfile                    # 容器化构建文件
├── docker-compose.yml            # 本地开发与测试用编排文件
└── README.md                     # 项目根目录说明文档（本文件）
```

## 贡献指南

LinkSphere 欢迎社区贡献，无论是问题报告、功能建议还是代码提交，均请遵循以下流程。

提交 Issue 报告问题或提出改进建议。请使用 GitHub Issues 模板，清晰描述复现步骤、预期行为与实际行为，并附上相关的环境信息（Node.js 版本、数据库版本等）。

Fork 主仓库并创建功能分支。分支命名请遵循 `feature/功能简述` 或 `fix/问题简述` 的格式。在分支上进行开发时，请确保代码通过现有的单元测试，并为新增功能补充对应的测试用例。

提交 Pull Request 前，请运行完整的测试套件并确保代码风格符合项目 ESLint 配置。PR 描述中请关联对应的 Issue 编号，并简要说明改动内容与影响范围。

更新文档。如果您的改动涉及用户可见的功能变化或配置变更，请同步更新 `docs/` 目录下的相关文档，并在 README 的文档导航中反映变更。

遵守行为准则。所有贡献者需遵守项目约定的贡献者行为准则，尊重其他参与者，保持友善与专业的沟通氛围。

## 常见问题

**LinkSphere 是否支持 HTTPS 访问？**

支持。在生产环境中，建议将 LinkSphere 部署在 Nginx 或 Caddy 等反向代理之后，由反向代理统一处理 TLS 终止。项目本身不强制要求开启 HTTPS，但生产部署时强烈建议启用。您也可以在环境变量中配置 `BASE_URL` 为 `https://` 开头的地址，公共页面和 API 响应中的链接将自动使用该前缀。

**如何迁移已有的外链数据到 LinkSphere？**

LinkSphere 提供 CSV 和 JSON 两种导入格式。您需要准备一个包含 `url`、`title`、`status`、`tags` 等字段的数据文件，通过管理后台的导入功能或使用 CLI 命令 `npm run import -- --file=data.json` 完成迁移。导入前系统会自动校验 URL 格式并去重。如果您的数据量超过一万条，建议分批导入以避免内存占用过高。

**公共页面是否可以设置访问密码？**

可以。LinkSphere 支持为每个公共页面设置独立的访问密码。您可以在生成公共页面时选择“密码保护”选项，系统会为该页面生成一个随机密码，您也可以手动指定。访问该公共页面时，访客需要输入密码才能查看链接列表。该功能依赖 Redis 存储会话状态，如果未启用 Redis，则密码保护功能将不可用。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:20

# LinkSphere 技术资源导航站

LinkSphere 是一个面向开发者、技术研究人员与内容创作者的轻量级技术资源导航与外链汇总平台。项目定位为“技术阅读的索引中枢”，通过人工筛选与社区推荐机制，持续收录高质量的技术文章、工具文档、工程实践与学术资源，帮助用户在信息过载的环境中快速定位有价值的技术内容。

项目本身不生产内容，而是以结构化目录与标签体系对分散于各个域名的技术资源进行重组与呈现，适用于个人知识管理、团队技术分享、开源项目文档聚合等场景。LinkSphere 采用静态站点生成方案，无需数据库支持，可部署于任意 Web 服务器或对象存储服务。

## 功能概览

- 多源资源聚合：支持从多个内容源自动或手动收录技术文章链接，统一展示于平台内。
- 分类与标签检索：每篇收录内容均附带分类标签（如后端架构、前端工程、运维监控、算法理论等），支持按标签筛选。
- 全文标题与摘要搜索：基于前端搜索库实现标题与摘要的实时检索，无需后端服务。
- 阅读状态标记：用户可标记“已读”、“待读”、“收藏”三种状态，数据存储于浏览器本地。
- 外部链接安全跳转：所有外链均经过中间页跳转，提示用户即将离开本站并展示目标域名，降低安全风险。
- 资源提交入口：提供公开的 GitHub Issue 模板，社区成员可提交新资源链接供审核收录。
- 导入导出功能：支持将个人收藏列表导出为 JSON 或 Markdown 格式，便于迁移与备份。

## 应用场景

个人技术阅读管理：开发者可将日常浏览到的优质技术博客、教程、案例文章统一收录到 LinkSphere 中，避免分散保存在浏览器书签或临时文档中，形成个人专属的技术阅读清单。

团队技术周报共享：技术团队负责人或成员可将本周值得关注的技术动态、版本发布公告、最佳实践文章汇总到 LinkSphere 的指定分类下，其他成员通过访问站点即可获取周报内容，减少邮件群发与即时通讯刷屏。

开源项目文档外链集合：开源项目维护者可将项目依赖的参考文档、设计决策记录、外部讨论帖、相关标准规范等链接整理到 LinkSphere 的独立页面中，作为项目 Wiki 的补充索引，方便贡献者查阅上下文。

技术培训与教学辅助：培训机构或高校教师可将课程相关的延伸阅读材料、视频资源、在线工具链接通过 LinkSphere 集中呈现，学员按目录顺序学习即可，无需在多个平台间反复跳转查找。

## 快速开始

以下步骤适用于开发环境或本地预览部署。

```bash
# 克隆代码仓库
git clone https://github.com/linksphere/linksphere.git
cd linksphere

# 安装项目依赖（使用 npm）
npm install

# 构建静态站点（生成 dist 目录）
npm run build

# 启动本地预览服务，默认访问 http://localhost:8080
npm run serve
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | >= 18.0.0 | 构建工具链与本地服务器运行环境 |
| npm | >= 9.0.0 | 包管理器，用于安装依赖与执行脚本 |
| Git | >= 2.30.0 | 代码克隆与版本控制 |
| 现代浏览器 | Chrome / Firefox / Edge 最新两个大版本 | 前端搜索与本地存储功能需要 ES2020 支持 |
| 静态 Web 服务器（生产部署） | Nginx / Caddy / Apache 或任何静态托管服务 | 仅需托管生成的静态文件，无需动态后端 |
| 网络连通性 | 任意 | 访问外部资源链接时需互联网连接 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|-----|------|-----------|
| 用户指南 | /docs/user-guide/ | 如何使用搜索、分类过滤、本地收藏与导出功能 |
| 管理员手册 | /docs/admin/ | 如何新增资源分类、调整标签体系、生成站点地图 |
| 开发者文档 | /docs/developer/ | 项目目录结构说明、核心模块 API、自定义主题方法 |
| 资源收录规范 | /docs/submission/ | 提交新资源链接的审核标准、标题摘要格式要求 |
| 部署指南 | /docs/deployment/ | 针对不同托管平台（Vercel、Netlify、Cloudflare Pages）的部署配置示例 |

## 资源列表

- https://www.read.cvsifc.cn/Article/8051.shtml
- https://www.read.fuvxie.cn/Article/699041.shtml
- https://www.read.nwbbyt.cn/Article/6584943.shtml
- https://www.read.nzfnve.cn/Article/581609.shtml
- https://www.read.cmcvrr.cn/Article/4379835.shtml
- https://www.read.nwbbyt.cn/Article/6351.shtml
- https://www.read.jnjpgf.cn/Article/4513.shtml
- https://www.read.cmcvrr.cn/Article/407487.shtml
- https://www.read.puhvjy.cn/Article/433724.shtml
- https://www.read.cvsifc.cn/Article/624195.shtml
- https://www.read.nwbbyt.cn/Article/43694.shtml
- https://www.read.nzfnve.cn/Article/0698.shtml
- https://www.read.cvsifc.cn/Article/78592.shtml
- https://www.read.cmcvrr.cn/Article/1795.shtml
- https://www.read.nwbbyt.cn/Article/4121001.shtml
- https://www.read.hcbezg.cn/Article/4438.shtml
- https://www.read.puhvjy.cn/Article/252268.shtml
- https://www.read.nwbbyt.cn/Article/394919.shtml
- https://www.read.fuvxie.cn/Article/5427.shtml
- https://www.read.nzfnve.cn/Article/546757.shtml
- https://www.read.jnjpgf.cn/Article/6517.shtml
- https://www.read.hcbezg.cn/Article/1599004.shtml
- https://www.read.nwbbyt.cn/Article/826640.shtml
- https://www.read.hcbezg.cn/Article/3878810.shtml
- https://www.read.jnjpgf.cn/Article/854215.shtml
- https://www.read.hcbezg.cn/Article/2403967.shtml
- https://www.read.puhvjy.cn/Article/4505040.shtml
- https://www.read.cmcvrr.cn/Article/5256235.shtml
- https://www.read.cvsifc.cn/Article/0246.shtml
- https://www.read.nwbbyt.cn/Article/1753732.shtml
- https://www.read.nwbbyt.cn/Article/7705086.shtml
- https://www.read.nwbbyt.cn/Article/4667.shtml
- https://www.read.cmcvrr.cn/Article/4735347.shtml
- https://www.read.fuvxie.cn/Article/658520.shtml
- https://www.read.nzfnve.cn/Article/37214.shtml
- https://www.read.nzfnve.cn/Article/1104191.shtml
- https://www.read.nzfnve.cn/Article/99353.shtml
- https://www.read.hcbezg.cn/Article/4649443.shtml
- https://www.read.nwbbyt.cn/Article/74755.shtml
- https://www.read.cmcvrr.cn/Article/52835.shtml
- https://www.read.fuvxie.cn/Article/12912.shtml
- https://www.read.cmcvrr.cn/Article/2392959.shtml
- https://www.read.jnjpgf.cn/Article/6648999.shtml
- https://www.read.nwbbyt.cn/Article/66078.shtml
- https://www.read.nzfnve.cn/Article/0298295.shtml
- https://www.read.nwbbyt.cn/Article/8726761.shtml
- https://www.read.nwbbyt.cn/Article/35712.shtml
- https://www.read.hcbezg.cn/Article/9312284.shtml
- https://www.read.hcbezg.cn/Article/22149.shtml
- https://www.read.cmcvrr.cn/Article/15479.shtml
- https://www.read.hcbezg.cn/Article/7882896.shtml
- https://www.read.jnjpgf.cn/Article/2172.shtml
- https://www.read.fuvxie.cn/Article/7848828.shtml
- https://www.read.fuvxie.cn/Article/675830.shtml
- https://www.read.hcbezg.cn/Article/6690.shtml
- https://www.read.nwbbyt.cn/Article/71018.shtml
- https://www.read.cvsifc.cn/Article/2134678.shtml
- https://www.read.hcbezg.cn/Article/041852.shtml
- https://www.read.fuvxie.cn/Article/81820.shtml
- https://www.read.nzfnve.cn/Article/5694410.shtml
- https://www.read.hcbezg.cn/Article/67960.shtml
- https://www.read.hcbezg.cn/Article/19245.shtml
- https://www.read.cvsifc.cn/Article/35499.shtml
- https://www.read.jnjpgf.cn/Article/40369.shtml
- https://www.read.jnjpgf.cn/Article/8221228.shtml
- https://www.read.nwbbyt.cn/Article/9683944.shtml
- https://www.read.cmcvrr.cn/Article/5158.shtml
- https://www.read.cvsifc.cn/Article/1706619.shtml
- https://www.read.fuvxie.cn/Article/510079.shtml
- https://www.read.puhvjy.cn/Article/6629.shtml
- https://www.read.nzfnve.cn/Article/2114648.shtml
- https://www.read.fuvxie.cn/Article/570131.shtml
- https://www.read.hcbezg.cn/Article/02480.shtml
- https://www.read.fuvxie.cn/Article/65102.shtml
- https://www.read.cvsifc.cn/Article/6138295.shtml
- https://www.read.cvsifc.cn/Article/817450.shtml
- https://www.read.nwbbyt.cn/Article/83484.shtml
- https://www.read.nwbbyt.cn/Article/939758.shtml
- https://www.read.jnjpgf.cn/Article/3994078.shtml
- https://www.read.puhvjy.cn/Article/6658533.shtml
- https://www.read.fuvxie.cn/Article/5485.shtml
- https://www.read.cmcvrr.cn/Article/676259.shtml
- https://www.read.cvsifc.cn/Article/2253457.shtml
- https://www.read.hcbezg.cn/Article/77765.shtml
- https://www.read.cvsifc.cn/Article/066712.shtml
- https://www.read.hcbezg.cn/Article/1378.shtml
- https://www.read.jnjpgf.cn/Article/41376.shtml
- https://www.read.nwbbyt.cn/Article/9455.shtml
- https://www.read.jnjpgf.cn/Article/079127.shtml
- https://www.read.cvsifc.cn/Article/83310.shtml
- https://www.read.cmcvrr.cn/Article/527591.shtml
- https://www.read.jnjpgf.cn/Article/098325.shtml
- https://www.read.nzfnve.cn/Article/789952.shtml
- https://www.read.nwbbyt.cn/Article/3380.shtml
- https://www.read.nzfnve.cn/Article/7720.shtml
- https://www.read.fuvxie.cn/Article/119497.shtml
- https://www.read.puhvjy.cn/Article/42260.shtml
- https://www.read.jnjpgf.cn/Article/93470.shtml
- https://www.read.nwbbyt.cn/Article/1666591.shtml
- https://www.read.fuvxie.cn/Article/2834.shtml
- https://www.read.cvsifc.cn/Article/5805.shtml
- https://www.read.jnjpgf.cn/Article/6077.shtml
- https://www.read.jnjpgf.cn/Article/3209.shtml
- https://www.read.hcbezg.cn/Article/357546.shtml
- https://www.read.nwbbyt.cn/Article/4583804.shtml
- https://www.read.nzfnve.cn/Article/4215.shtml
- https://www.read.jnjpgf.cn/Article/9678257.shtml
- https://www.read.fuvxie.cn/Article/63879.shtml
- https://www.read.jnjpgf.cn/Article/100062.shtml
- https://www.read.jnjpgf.cn/Article/3100.shtml
- https://www.read.nzfnve.cn/Article/0285239.shtml
- https://www.read.jnjpgf.cn/Article/3904.shtml
- https://www.read.fuvxie.cn/Article/630419.shtml
- https://www.read.cvsifc.cn/Article/04480.shtml
- https://www.read.nwbbyt.cn/Article/3493070.shtml
- https://www.read.cvsifc.cn/Article/2723447.shtml
- https://www.read.cmcvrr.cn/Article/983182.shtml
- https://www.read.fuvxie.cn/Article/7236246.shtml
- https://www.read.hcbezg.cn/Article/5880402.shtml
- https://www.read.nwbbyt.cn/Article/324704.shtml
- https://www.read.cmcvrr.cn/Article/7801209.shtml
- https://www.read.nzfnve.cn/Article/1097.shtml
- https://www.read.nwbbyt.cn/Article/9007.shtml
- https://www.read.puhvjy.cn/Article/224408.shtml
- https://www.read.cmcvrr.cn/Article/379740.shtml
- https://www.read.hcbezg.cn/Article/711161.shtml
- https://www.read.hcbezg.cn/Article/2077121.shtml
- https://www.read.nwbbyt.cn/Article/1056.shtml
- https://www.read.nzfnve.cn/Article/73807.shtml
- https://www.read.jnjpgf.cn/Article/104291.shtml
- https://www.read.nzfnve.cn/Article/9965300.shtml
- https://www.read.nwbbyt.cn/Article/5152.shtml
- https://www.read.nzfnve.cn/Article/8102.shtml
- https://www.read.cvsifc.cn/Article/5550310.shtml
- https://www.read.puhvjy.cn/Article/42129.shtml
- https://www.read.cvsifc.cn/Article/294037.shtml
- https://www.read.puhvjy.cn/Article/6367.shtml
- https://www.read.jnjpgf.cn/Article/8294.shtml
- https://www.read.hcbezg.cn/Article/30817.shtml
- https://www.read.jnjpgf.cn/Article/5366843.shtml
- https://www.read.hcbezg.cn/Article/2907.shtml
- https://www.read.nzfnve.cn/Article/99885.shtml
- https://www.read.jnjpgf.cn/Article/980626.shtml
- https://www.read.cmcvrr.cn/Article/9969584.shtml
- https://www.read.jnjpgf.cn/Article/01398.shtml
- https://www.read.hcbezg.cn/Article/5502487.shtml
- https://www.read.puhvjy.cn/Article/672777.shtml
- https://www.read.nwbbyt.cn/Article/2910081.shtml
- https://www.read.puhvjy.cn/Article/67356.shtml
- https://www.read.nwbbyt.cn/Article/2746057.shtml
- https://www.read.nzfnve.cn/Article/0375.shtml
- https://www.read.hcbezg.cn/Article/927939.shtml
- https://www.read.nwbbyt.cn/Article/7764.shtml
- https://www.read.nwbbyt.cn/Article/6330.shtml
- https://www.read.fuvxie.cn/Article/2014113.shtml
- https://www.read.nzfnve.cn/Article/50374.shtml
- https://www.read.hcbezg.cn/Article/4654277.shtml
- https://www.read.puhvjy.cn/Article/857970.shtml
- https://www.read.nwbbyt.cn/Article/73860.shtml
- https://www.read.hcbezg.cn/Article/658791.shtml
- https://www.read.nwbbyt.cn/Article/0571.shtml
- https://www.read.cmcvrr.cn/Article/5460.shtml
- https://www.read.jnjpgf.cn/Article/7513275.shtml
- https://www.read.hcbezg.cn/Article/816448.shtml
- https://www.read.hcbezg.cn/Article/6871623.shtml
- https://www.read.cvsifc.cn/Article/66470.shtml
- https://www.read.nzfnve.cn/Article/92693.shtml
- https://www.read.cvsifc.cn/Article/8856.shtml
- https://www.read.hcbezg.cn/Article/2174.shtml
- https://www.read.fuvxie.cn/Article/8620.shtml
- https://www.read.jnjpgf.cn/Article/6490.shtml
- https://www.read.fuvxie.cn/Article/822467.shtml
- https://www.read.fuvxie.cn/Article/3896452.shtml
- https://www.read.cmcvrr.cn/Article/4032313.shtml
- https://www.read.nzfnve.cn/Article/4171.shtml
- https://www.read.nwbbyt.cn/Article/7818.shtml
- https://www.read.puhvjy.cn/Article/275639.shtml
- https://www.read.hcbezg.cn/Article/1472985.shtml
- https://www.read.hcbezg.cn/Article/7863.shtml
- https://www.read.puhvjy.cn/Article/8354.shtml
- https://www.read.nwbbyt.cn/Article/1220237.shtml
- https://www.read.jnjpgf.cn/Article/3526119.shtml
- https://www.read.fuvxie.cn/Article/1384881.shtml
- https://www.read.cvsifc.cn/Article/00809.shtml
- https://www.read.nwbbyt.cn/Article/873125.shtml
- https://www.read.hcbezg.cn/Article/7824442.shtml
- https://www.read.fuvxie.cn/Article/41507.shtml
- https://www.read.cvsifc.cn/Article/836618.shtml
- https://www.read.fuvxie.cn/Article/28314.shtml
- https://www.read.cmcvrr.cn/Article/6765731.shtml
- https://www.read.puhvjy.cn/Article/67206.shtml
- https://www.read.nzfnve.cn/Article/849380.shtml
- https://www.read.hcbezg.cn/Article/921582.shtml
- https://www.read.jnjpgf.cn/Article/096221.shtml
- https://www.read.jnjpgf.cn/Article/0530.shtml
- https://www.read.cvsifc.cn/Article/6374.shtml
- https://www.read.cvsifc.cn/Article/40818.shtml
- https://www.read.puhvjy.cn/Article/71463.shtml
- https://www.read.nwbbyt.cn/Article/5013569.shtml
- https://www.read.cmcvrr.cn/Article/3426570.shtml
- https://www.read.nwbbyt.cn/Article/690070.shtml
- https://www.read.cmcvrr.cn/Article/18324.shtml
- https://www.read.fuvxie.cn/Article/3122.shtml
- https://www.read.cvsifc.cn/Article/10838.shtml
- https://www.read.cvsifc.cn/Article/957441.shtml
- https://www.read.puhvjy.cn/Article/6087.shtml
- https://www.read.nwbbyt.cn/Article/968767.shtml
- https://www.read.fuvxie.cn/Article/1129683.shtml
- https://www.read.puhvjy.cn/Article/450045.shtml
- https://www.read.hcbezg.cn/Article/715666.shtml
- https://www.read.nzfnve.cn/Article/4477.shtml
- https://www.read.puhvjy.cn/Article/547375.shtml
- https://www.read.nwbbyt.cn/Article/66637.shtml
- https://www.read.jnjpgf.cn/Article/135251.shtml
- https://www.read.hcbezg.cn/Article/0558.shtml
- https://www.read.puhvjy.cn/Article/01007.shtml
- https://www.read.cmcvrr.cn/Article/4109.shtml
- https://www.read.puhvjy.cn/Article/05782.shtml
- https://www.read.jnjpgf.cn/Article/2483.shtml
- https://www.read.nwbbyt.cn/Article/54186.shtml
- https://www.read.cmcvrr.cn/Article/3296.shtml
- https://www.read.nzfnve.cn/Article/1965490.shtml
- https://www.read.cvsifc.cn/Article/4655.shtml
- https://www.read.hcbezg.cn/Article/8836323.shtml
- https://www.read.cvsifc.cn/Article/6914.shtml
- https://www.read.hcbezg.cn/Article/87520.shtml
- https://www.read.puhvjy.cn/Article/6160706.shtml
- https://www.read.cvsifc.cn/Article/3453093.shtml
- https://www.read.nzfnve.cn/Article/1520.shtml
- https://www.read.cvsifc.cn/Article/5289.shtml
- https://www.read.jnjpgf.cn/Article/42322.shtml
- https://www.read.fuvxie.cn/Article/88535.shtml
- https://www.read.nwbbyt.cn/Article/29954.shtml
- https://www.read.fuvxie.cn/Article/74532.shtml
- https://www.read.nwbbyt.cn/Article/8452800.shtml
- https://www.read.puhvjy.cn/Article/000251.shtml
- https://www.read.hcbezg.cn/Article/520549.shtml
- https://www.read.jnjpgf.cn/Article/2899.shtml
- https://www.read.jnjpgf.cn/Article/0227664.shtml
- https://www.read.cvsifc.cn/Article/5826.shtml
- https://www.read.jnjpgf.cn/Article/8349.shtml
- https://www.read.puhvjy.cn/Article/8429.shtml
- https://www.read.puhvjy.cn/Article/8320412.shtml
- https://www.read.jnjpgf.cn/Article/18579.shtml
- https://www.read.cvsifc.cn/Article/135352.shtml
- https://www.read.fuvxie.cn/Article/465471.shtml
- https://www.read.puhvjy.cn/Article/152632.shtml
- https://www.read.cvsifc.cn/Article/37740.shtml
- https://www.read.jnjpgf.cn/Article/66268.shtml
- https://www.read.jnjpgf.cn/Article/054803.shtml

## 项目结构

```
linksphere/
├── build/                           # 构建脚本目录
│   ├── generate-index.js            # 从源数据生成首页索引
│   ├── fetch-metadata.js            # 批量获取链接标题与摘要（用于预览）
│   └── validate-urls.js             # 校验资源链接可用性与格式规范
│
├── src/                             # 前端源代码目录
│   ├── assets/                      # 静态资源（图片、字体、favicon）
│   │   ├── icons/                   # SVG 图标集（分类标识、状态标记）
│   │   └── styles/                  # 基础 CSS 样式重置与全局变量
│   ├── components/                  # 可复用 UI 组件
│   │   ├── LinkCard.js              # 单个资源链接卡片渲染组件
│   │   ├── FilterBar.js             # 分类过滤与搜索输入组件
│   │   └── Pagination.js            # 分页导航组件（每页 50 条）
│   ├── data/                        # 资源数据存储（JSON 格式）
│   │   ├── sources.json             # 收录的所有资源链接及元数据
│   │   └── categories.json          # 分类层级定义与颜色映射
│   ├── lib/                         # 工具函数与第三方库封装
│   │   ├── storage.js               # localStorage 读写封装（收藏/状态）
│   │   ├── search.js                # 前端模糊搜索实现（基于 Levenshtein）
│   │   └── export.js                # 收藏列表导出为 Markdown / JSON
│   ├── pages/                       # 多页面入口模板
│   │   ├── index.html               # 主列表页模板
│   │   ├── favorites.html           # 收藏夹独立页面
│   │   └── about.html               # 项目说明与提交指引页
│   └── main.js                      # 应用入口文件，初始化路由与事件绑定
│
├── dist/                            # 构建输出目录（部署时使用）
│   ├── index.html
│   ├── favorites.html
│   ├── about.html
│   └── assets/                      # 打包后的 CSS / JS / 图片文件
│
├── docs/                            # 项目文档（用户手册与开发指南）
│   ├── user-guide.md
│   ├── developer.md
│   └── deployment.md
│
├── scripts/                         # 辅助脚本（数据迁移、批量导入）
│   ├── import-from-csv.js           # 从 CSV 批量导入资源链接
│   └── deduplicate.js               # 检测并移除重复收录的链接
│
├── tests/                           # 单元测试与集成测试
│   ├── unit/                        # 组件与工具函数单元测试（Jest）
│   └── e2e/                         # 端到端测试（Playwright）
│
├── .github/                         # GitHub 社区配置
│   ├── ISSUE_TEMPLATE/              # 资源提交与问题反馈 Issue 模板
│   └── workflows/                   # CI 流水线（构建验证与自动化部署）
│
├── package.json                     # npm 依赖声明与脚本命令
├── vite.config.js                   # 构建工具 Vite 配置文件
├── .eslintrc.js                     # JavaScript 代码规范检查配置
├── .prettierrc                      # 代码格式化配置
└── README.md                        # 项目说明文档（本文件）
```

## 贡献指南

1. 提交资源推荐：在 GitHub Issue 中使用“资源提交”模板填写链接标题、原始 URL、分类标签及推荐理由，维护团队将在 7 个工作日内审核。审核通过后链接将被添加至 src/data/sources.json 并随下次站点构建发布。

2. 改进前端界面：如需调整搜索逻辑、卡片布局或主题样式，请基于 develop 分支创建 feature 分支进行修改，确保通过现有单元测试并提供至少一个使用示例。提交 Pull Request 时需描述改动目的与 UI 变更截图。

3. 完善文档内容：文档位于 docs/ 目录，采用 Markdown 格式。如发现使用指南、部署说明或 API 文档存在遗漏或歧义，欢迎直接提交 Pull Request 修改。文档变更无需通过单元测试，但需保持语言风格一致。

4. 报告问题或缺陷：使用 GitHub Issue 中的“问题反馈”模板，详细描述复现步骤、预期行为与实际表现，并附上浏览器版本及操作系统信息。严重安全相关问题请通过邮件联系维护组，勿公开披露。

5. 参与社区讨论：项目维护组定期在 GitHub Discussions 中发布版本规划与功能投票，社区成员可通过参与讨论影响下一批资源的收录方向与优先级排序。

## 常见问题

问：LinkSphere 需要后端数据库或云服务吗？
答：不需要。项目完全构建为静态 HTML、CSS 与 JavaScript 文件，所有数据（资源列表、分类结构）均内置于 JSON 文件中。用户收藏与阅读状态存储于浏览器 localStorage 中，无需任何后端基础设施。您可以将生成的 dist 目录托管于任何静态 Web 服务器或对象存储服务。

问：资源链接失效了怎么办？
答：项目维护组会每季度执行一次链接可用性检查（通过 scripts/validate-urls.js 脚本），失效链接将被标记并移出主列表。如您发现某个链接无法访问，可在 GitHub Issue 中提交“链接失效”反馈，维护组将在核实后更新数据并重新构建站点。您也可以自行修改本地 JSON 文件后重新构建。

问：能否在 LinkSphere 中添加自定义分类？
答：可以。您需要编辑 src/data/categories.json 文件，按照已有格式添加新的分类对象（包含 id、name、icon 和 color 字段），随后在 src/data/sources.json 中为对应的资源条目指定新分类的 id。重新运行 npm run build 即可生成包含自定义分类的站点。若您希望该分类被上游项目收录，可提交 Pull Request 供维护组评估。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:20

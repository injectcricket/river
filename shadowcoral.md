# DocLink Aggregator

DocLink Aggregator 是一个面向技术文档与业务资料的外链统一管理与快速检索系统。项目定位为轻量级文档资源网关，主要服务于需要频繁查阅分散于多个内部站点或CDN节点的Word文档的技术人员、项目经理与运维工程师。本项目不提供文档存储服务，而是通过结构化索引与统一访问入口，帮助用户从大量原始链接中快速定位目标文档，解决多源文档分散、链接难以记忆、访问状态不可视等实际问题。

系统内置静态链接索引，基于稳定的二级域名与路径规则构建，支持按文档编号、来源域名、文件类型进行筛选与预览。项目代码完全开源，可部署于任意静态托管服务，无需数据库与后端运行时，开箱即用。

## 功能概览

统一资源索引：基于给定的文档链接列表，生成结构化索引页面，支持按来源域名分组浏览。

快速文档预览：点击链接直接访问原始文档，无需额外跳转或登录验证，适用于内网与外网环境。

多维度筛选：支持按文档编号范围、来源域名关键字进行静态前端筛选，无需后端支持。

链接可用性检测：内置HEAD请求检测机制，可扫描并标记当前可访问的文档链接，生成健康状态报告。

按需导出功能：支持将筛选后的链接列表导出为纯文本或CSV格式，便于批量下载与归档。

响应式界面：采用移动优先的CSS布局，在手机、平板与桌面设备上均可正常访问与操作。

无依赖部署：项目仅由HTML、CSS与JavaScript构成，无需npm、pip或任何包管理工具，克隆即用。

## 应用场景

企业内部文档导航：企业内部常将技术方案、会议纪要、验收报告等文档存放于不同的静态资源服务器。DocLink Aggregator可作为统一入口页，将所有文档链接集中展示，团队成员无需记忆多个域名与路径。

离线文档归档辅助：运维人员在备份或迁移文档时，可使用本项目的筛选与导出功能，快速生成某一来源域名下的所有文档列表，配合wget或curl实现批量下载。

技术培训资料分发：培训讲师可将课程相关的参考文档链接通过本项目进行统一整理，学员访问聚合页即可获取全部资料，避免反复询问链接地址。

文档链接生命周期监控：项目内置的链接检测功能可定期扫描文档状态，帮助管理员发现已失效或搬迁的文档链接，及时更新索引。

## 快速开始

以下步骤适用于Linux、macOS及Windows的WSL环境。请确保系统已安装Git。

```bash
git clone https://github.com/your-org/doclink-aggregator.git
cd doclink-aggregator
cp config.example.js config.js
# 编辑config.js，将默认链接列表替换为实际所需链接
python3 -m http.server 8080
# 或使用任意静态服务器，如npx serve -p 8080
```

完成上述步骤后，在浏览器中访问 `http://localhost:8080` 即可查看聚合页面。若需部署至生产环境，将整个目录上传至Nginx、Apache或OSS静态托管即可。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|---|---|---|
| Git | 2.20 及以上 | 用于克隆项目仓库 |
| Python 3 | 3.6 及以上 | 仅用于本地开发测试的简易HTTP服务器 |
| 现代浏览器 | Chrome 80 / Firefox 78 / Edge 80 及以上 | 前端界面运行环境 |
| 磁盘空间 | 10 MB 以上 | 存放源码与生成的缓存报告 |
| 网络访问 | 可访问外网或内网文档服务器 | 用于预览文档与检测链接可用性 |
| 静态托管服务 | 无版本要求 | 生产部署时可选用Nginx、S3、OSS等 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何使用筛选、预览、导出功能，如何阅读链接健康报告 |
| 管理员手册 | docs/admin-guide.md | 如何更新链接列表、如何调整界面配置、如何部署至生产 |
| 开发者指南 | docs/developer-guide.md | 项目代码结构、如何自定义筛选器、如何扩展新的检测策略 |
| 常见问题 | docs/faq.md | 链接打不开怎么办、如何批量更新索引、如何迁移至其他域名 |

## 资源列表

- h5.mobile.puhvjy.cn/Article/1896.doc
- h5.mobile.puhvjy.cn/Article/3922.doc
- h5.mobile.fuvxie.cn/Article/1964.doc
- h5.mobile.nwbbyt.cn/Article/814766.doc
- h5.mobile.jnjpgf.cn/Article/3676102.doc
- h5.mobile.jnjpgf.cn/Article/147197.doc
- h5.mobile.cvsifc.cn/Article/0507.doc
- h5.mobile.hcbezg.cn/Article/6621.doc
- h5.mobile.cmcvrr.cn/Article/056380.doc
- h5.mobile.puhvjy.cn/Article/73012.doc
- h5.mobile.jnjpgf.cn/Article/32568.doc
- h5.mobile.cvsifc.cn/Article/2749.doc
- h5.mobile.hcbezg.cn/Article/3758.doc
- h5.mobile.nzfnve.cn/Article/8727908.doc
- h5.mobile.nwbbyt.cn/Article/77542.doc
- h5.mobile.cvsifc.cn/Article/8947434.doc
- h5.mobile.nzfnve.cn/Article/02019.doc
- h5.mobile.nwbbyt.cn/Article/7429.doc
- h5.mobile.nzfnve.cn/Article/83648.doc
- h5.mobile.cvsifc.cn/Article/58069.doc
- h5.mobile.cvsifc.cn/Article/27884.doc
- h5.mobile.hcbezg.cn/Article/7589795.doc
- h5.mobile.cvsifc.cn/Article/213996.doc
- h5.mobile.cvsifc.cn/Article/6607.doc
- h5.mobile.cmcvrr.cn/Article/8921.doc
- h5.mobile.fuvxie.cn/Article/9584.doc
- h5.mobile.hcbezg.cn/Article/61303.doc
- h5.mobile.nwbbyt.cn/Article/815533.doc
- h5.mobile.nwbbyt.cn/Article/71990.doc
- h5.mobile.nzfnve.cn/Article/9030.doc
- h5.mobile.hcbezg.cn/Article/4401801.doc
- h5.mobile.nzfnve.cn/Article/0469.doc
- h5.mobile.nwbbyt.cn/Article/73747.doc
- h5.mobile.puhvjy.cn/Article/198527.doc
- h5.mobile.cmcvrr.cn/Article/2195.doc
- h5.mobile.cmcvrr.cn/Article/3572204.doc
- h5.mobile.fuvxie.cn/Article/614481.doc
- h5.mobile.cvsifc.cn/Article/3099394.doc
- h5.mobile.cvsifc.cn/Article/37889.doc
- h5.mobile.cmcvrr.cn/Article/4702.doc
- h5.mobile.cvsifc.cn/Article/08445.doc
- h5.mobile.cmcvrr.cn/Article/2920500.doc
- h5.mobile.nwbbyt.cn/Article/724656.doc
- h5.mobile.cvsifc.cn/Article/5831854.doc
- h5.mobile.nwbbyt.cn/Article/1669772.doc
- h5.mobile.fuvxie.cn/Article/9484921.doc
- h5.mobile.nwbbyt.cn/Article/01391.doc
- h5.mobile.fuvxie.cn/Article/5575.doc
- h5.mobile.jnjpgf.cn/Article/48195.doc
- h5.mobile.fuvxie.cn/Article/1500.doc
- h5.mobile.cmcvrr.cn/Article/17031.doc
- h5.mobile.fuvxie.cn/Article/34066.doc
- h5.mobile.hcbezg.cn/Article/592416.doc
- h5.mobile.jnjpgf.cn/Article/7877.doc
- h5.mobile.hcbezg.cn/Article/98830.doc
- h5.mobile.nzfnve.cn/Article/6561866.doc
- h5.mobile.puhvjy.cn/Article/906449.doc
- h5.mobile.cmcvrr.cn/Article/0075.doc
- h5.mobile.cvsifc.cn/Article/564374.doc
- h5.mobile.nzfnve.cn/Article/013835.doc
- h5.mobile.puhvjy.cn/Article/030978.doc
- h5.mobile.hcbezg.cn/Article/17088.doc
- h5.mobile.cmcvrr.cn/Article/124118.doc
- h5.mobile.nzfnve.cn/Article/4488.doc
- h5.mobile.hcbezg.cn/Article/10608.doc
- h5.mobile.cmcvrr.cn/Article/171416.doc
- h5.mobile.jnjpgf.cn/Article/6116.doc
- h5.mobile.cvsifc.cn/Article/0799.doc
- h5.mobile.puhvjy.cn/Article/2871.doc
- h5.mobile.nzfnve.cn/Article/021586.doc
- h5.mobile.nwbbyt.cn/Article/843431.doc
- h5.mobile.cmcvrr.cn/Article/66478.doc
- h5.mobile.cmcvrr.cn/Article/825563.doc
- h5.mobile.nzfnve.cn/Article/9572166.doc
- h5.mobile.cvsifc.cn/Article/55200.doc
- h5.mobile.hcbezg.cn/Article/3949461.doc
- h5.mobile.nzfnve.cn/Article/207900.doc
- h5.mobile.nwbbyt.cn/Article/3155235.doc
- h5.mobile.jnjpgf.cn/Article/56250.doc
- h5.mobile.hcbezg.cn/Article/513385.doc
- h5.mobile.hcbezg.cn/Article/0945661.doc
- h5.mobile.cmcvrr.cn/Article/8554.doc
- h5.mobile.jnjpgf.cn/Article/4563180.doc
- h5.mobile.cmcvrr.cn/Article/5358594.doc
- h5.mobile.fuvxie.cn/Article/0833.doc
- h5.mobile.cmcvrr.cn/Article/61106.doc
- h5.mobile.jnjpgf.cn/Article/58314.doc
- h5.mobile.cvsifc.cn/Article/14332.doc
- h5.mobile.hcbezg.cn/Article/6849996.doc
- h5.mobile.puhvjy.cn/Article/49054.doc
- h5.mobile.cmcvrr.cn/Article/944570.doc
- h5.mobile.nzfnve.cn/Article/0259.doc
- h5.mobile.puhvjy.cn/Article/702647.doc
- h5.mobile.puhvjy.cn/Article/2997.doc
- h5.mobile.cmcvrr.cn/Article/7609.doc
- h5.mobile.hcbezg.cn/Article/2780.doc
- h5.mobile.nzfnve.cn/Article/18016.doc
- h5.mobile.nwbbyt.cn/Article/242315.doc
- h5.mobile.hcbezg.cn/Article/9413.doc
- h5.mobile.nwbbyt.cn/Article/6469.doc
- h5.mobile.hcbezg.cn/Article/1300878.doc
- h5.mobile.hcbezg.cn/Article/75667.doc
- h5.mobile.jnjpgf.cn/Article/0152852.doc
- h5.mobile.cmcvrr.cn/Article/759902.doc
- h5.mobile.nwbbyt.cn/Article/121431.doc
- h5.mobile.nwbbyt.cn/Article/6459215.doc
- h5.mobile.jnjpgf.cn/Article/2912951.doc
- h5.mobile.jnjpgf.cn/Article/3718838.doc
- h5.mobile.puhvjy.cn/Article/14667.doc
- h5.mobile.jnjpgf.cn/Article/072569.doc
- h5.mobile.nzfnve.cn/Article/01155.doc
- h5.mobile.puhvjy.cn/Article/6164.doc
- h5.mobile.nwbbyt.cn/Article/648647.doc
- h5.mobile.cvsifc.cn/Article/52274.doc
- h5.mobile.fuvxie.cn/Article/056742.doc
- h5.mobile.jnjpgf.cn/Article/8528083.doc
- h5.mobile.nzfnve.cn/Article/547575.doc
- h5.mobile.hcbezg.cn/Article/8024614.doc
- h5.mobile.puhvjy.cn/Article/56400.doc
- h5.mobile.cvsifc.cn/Article/630967.doc
- h5.mobile.jnjpgf.cn/Article/9403647.doc
- h5.mobile.fuvxie.cn/Article/144861.doc
- h5.mobile.fuvxie.cn/Article/473563.doc
- h5.mobile.cmcvrr.cn/Article/072750.doc
- h5.mobile.jnjpgf.cn/Article/0168.doc
- h5.mobile.puhvjy.cn/Article/1235751.doc
- h5.mobile.cmcvrr.cn/Article/803475.doc
- h5.mobile.nzfnve.cn/Article/3183951.doc
- h5.mobile.cmcvrr.cn/Article/909256.doc
- h5.mobile.jnjpgf.cn/Article/0333369.doc
- h5.mobile.hcbezg.cn/Article/7599.doc
- h5.mobile.nzfnve.cn/Article/799650.doc
- h5.mobile.hcbezg.cn/Article/050935.doc
- h5.mobile.fuvxie.cn/Article/61902.doc
- h5.mobile.cvsifc.cn/Article/70078.doc
- h5.mobile.nwbbyt.cn/Article/77084.doc
- h5.mobile.nwbbyt.cn/Article/6228983.doc
- h5.mobile.hcbezg.cn/Article/87026.doc
- h5.mobile.cmcvrr.cn/Article/6408.doc
- h5.mobile.jnjpgf.cn/Article/8000.doc
- h5.mobile.cvsifc.cn/Article/6743.doc
- h5.mobile.hcbezg.cn/Article/948588.doc
- h5.mobile.puhvjy.cn/Article/3262.doc
- h5.mobile.hcbezg.cn/Article/39766.doc
- h5.mobile.nwbbyt.cn/Article/6274296.doc
- h5.mobile.cvsifc.cn/Article/9847.doc
- h5.mobile.puhvjy.cn/Article/2931.doc
- h5.mobile.fuvxie.cn/Article/1303.doc
- h5.mobile.nwbbyt.cn/Article/377368.doc
- h5.mobile.nwbbyt.cn/Article/5133.doc
- h5.mobile.hcbezg.cn/Article/39045.doc
- h5.mobile.fuvxie.cn/Article/83640.doc
- h5.mobile.cvsifc.cn/Article/25113.doc
- h5.mobile.hcbezg.cn/Article/4401.doc
- h5.mobile.jnjpgf.cn/Article/74080.doc
- h5.mobile.puhvjy.cn/Article/440995.doc
- h5.mobile.nzfnve.cn/Article/915704.doc
- h5.mobile.nwbbyt.cn/Article/5146.doc
- h5.mobile.cvsifc.cn/Article/972030.doc
- h5.mobile.nzfnve.cn/Article/702827.doc
- h5.mobile.fuvxie.cn/Article/335058.doc
- h5.mobile.fuvxie.cn/Article/68413.doc
- h5.mobile.nzfnve.cn/Article/5498.doc
- h5.mobile.fuvxie.cn/Article/5685.doc
- h5.mobile.cvsifc.cn/Article/9334.doc
- h5.mobile.jnjpgf.cn/Article/80950.doc
- h5.mobile.cmcvrr.cn/Article/3387.doc
- h5.mobile.puhvjy.cn/Article/2863812.doc
- h5.mobile.hcbezg.cn/Article/6886719.doc
- h5.mobile.hcbezg.cn/Article/68396.doc
- h5.mobile.fuvxie.cn/Article/23537.doc
- h5.mobile.nzfnve.cn/Article/1572.doc
- h5.mobile.cmcvrr.cn/Article/128157.doc
- h5.mobile.puhvjy.cn/Article/2794.doc
- h5.mobile.nwbbyt.cn/Article/0663645.doc
- h5.mobile.hcbezg.cn/Article/07027.doc
- h5.mobile.jnjpgf.cn/Article/84316.doc
- h5.mobile.cmcvrr.cn/Article/1626.doc
- h5.mobile.hcbezg.cn/Article/09259.doc
- h5.mobile.puhvjy.cn/Article/882164.doc
- h5.mobile.puhvjy.cn/Article/164796.doc
- h5.mobile.nwbbyt.cn/Article/3456681.doc
- h5.mobile.puhvjy.cn/Article/6145133.doc
- h5.mobile.fuvxie.cn/Article/7671594.doc
- h5.mobile.hcbezg.cn/Article/58330.doc
- h5.mobile.cvsifc.cn/Article/5774748.doc
- h5.mobile.jnjpgf.cn/Article/371104.doc
- h5.mobile.hcbezg.cn/Article/4238610.doc
- h5.mobile.cvsifc.cn/Article/48729.doc
- h5.mobile.fuvxie.cn/Article/5107.doc
- h5.mobile.hcbezg.cn/Article/25306.doc
- h5.mobile.cmcvrr.cn/Article/44276.doc
- h5.mobile.fuvxie.cn/Article/302853.doc
- h5.mobile.nwbbyt.cn/Article/1862401.doc
- h5.mobile.cvsifc.cn/Article/5325.doc
- h5.mobile.fuvxie.cn/Article/5416.doc
- h5.mobile.puhvjy.cn/Article/3298391.doc
- h5.mobile.jnjpgf.cn/Article/649195.doc
- h5.mobile.jnjpgf.cn/Article/3688021.doc
- h5.mobile.hcbezg.cn/Article/0124809.doc
- h5.mobile.nzfnve.cn/Article/338451.doc
- h5.mobile.jnjpgf.cn/Article/7710.doc
- h5.mobile.hcbezg.cn/Article/4613779.doc
- h5.mobile.cvsifc.cn/Article/037786.doc
- h5.mobile.nzfnve.cn/Article/746009.doc
- h5.mobile.cvsifc.cn/Article/3510781.doc
- h5.mobile.cvsifc.cn/Article/13118.doc
- h5.mobile.fuvxie.cn/Article/8878599.doc
- h5.mobile.jnjpgf.cn/Article/3869.doc
- h5.mobile.nzfnve.cn/Article/0080.doc
- h5.mobile.puhvjy.cn/Article/9583.doc
- h5.mobile.cmcvrr.cn/Article/91270.doc
- h5.mobile.fuvxie.cn/Article/8642624.doc
- h5.mobile.cmcvrr.cn/Article/9554.doc
- h5.mobile.fuvxie.cn/Article/99982.doc
- h5.mobile.jnjpgf.cn/Article/386098.doc
- h5.mobile.nzfnve.cn/Article/5876389.doc
- h5.mobile.cmcvrr.cn/Article/0101875.doc
- h5.mobile.hcbezg.cn/Article/92386.doc
- h5.mobile.hcbezg.cn/Article/1109175.doc
- h5.mobile.jnjpgf.cn/Article/3746841.doc
- h5.mobile.cvsifc.cn/Article/9782.doc
- h5.mobile.puhvjy.cn/Article/8443.doc
- h5.mobile.cvsifc.cn/Article/4901.doc
- h5.mobile.fuvxie.cn/Article/6619735.doc
- h5.mobile.nzfnve.cn/Article/64005.doc
- h5.mobile.jnjpgf.cn/Article/2429.doc
- h5.mobile.cvsifc.cn/Article/7151.doc
- h5.mobile.jnjpgf.cn/Article/163185.doc
- h5.mobile.hcbezg.cn/Article/8031541.doc
- h5.mobile.nzfnve.cn/Article/3445447.doc
- h5.mobile.nzfnve.cn/Article/1540.doc
- h5.mobile.hcbezg.cn/Article/152867.doc
- h5.mobile.jnjpgf.cn/Article/57604.doc
- h5.mobile.fuvxie.cn/Article/3336.doc
- h5.mobile.fuvxie.cn/Article/184599.doc
- h5.mobile.fuvxie.cn/Article/97797.doc
- h5.mobile.cvsifc.cn/Article/9671479.doc
- h5.mobile.hcbezg.cn/Article/9426.doc
- h5.mobile.nzfnve.cn/Article/313139.doc
- h5.mobile.puhvjy.cn/Article/9104660.doc
- h5.mobile.hcbezg.cn/Article/132174.doc
- h5.mobile.nzfnve.cn/Article/61030.doc
- h5.mobile.nwbbyt.cn/Article/9495.doc
- h5.mobile.cvsifc.cn/Article/5356842.doc
- h5.mobile.fuvxie.cn/Article/8817.doc
- h5.mobile.puhvjy.cn/Article/978308.doc
- h5.mobile.puhvjy.cn/Article/625509.doc
- h5.mobile.jnjpgf.cn/Article/8051122.doc
- h5.mobile.jnjpgf.cn/Article/3418481.doc

## 项目结构

```
doclink-aggregator/
├── index.html                # 主界面入口，包含HTML骨架与基础样式
├── config.js                 # 用户配置文件，存放链接列表与筛选规则
├── assets/
│   ├── css/
│   │   └── style.css         # 响应式样式表，定义卡片、表格与筛选器布局
│   ├── js/
│   │   ├── app.js            # 核心应用逻辑，包含渲染、筛选与导出功能
│   │   └── health.js         # 链接健康检测模块，并发请求并记录状态
│   └── icons/
│       └── favicon.ico       # 站点图标
├── docs/
│   ├── user-guide.md         # 用户操作手册，包含截图与分步指引
│   ├── admin-guide.md        # 管理员部署与配置文档
│   ├── developer-guide.md    # 开发者扩展指南，包含API说明与自定义筛选器示例
│   └── faq.md                # 常见问题汇总
├── scripts/
│   ├── generate-index.py     # Python脚本，用于从CSV批量生成链接列表
│   └── check-links.sh        # Shell脚本，批量检测链接可达性并生成报告
├── tests/
│   ├── test-app.js           # 单元测试，使用Jest模拟DOM操作
│   └── test-health.js        # 健康检测模块的单元测试
├── .gitignore                # Git忽略规则，包含node_modules与临时文件
├── LICENSE                   # MIT许可证文件
└── README.md                 # 项目说明文档，即本文件
```

## 贡献指南

1. 复刻项目仓库至个人账号，并在本地克隆复刻后的版本。请确保使用主分支的最新代码作为基线。

2. 新建功能分支，分支名称应反映修改内容，例如 `feature/add-sort-by-size` 或 `fix/health-check-timeout`。

3. 进行代码修改时，请遵循项目现有代码风格。对于JavaScript，保持ES6语法与2空格缩进；对于CSS，采用BEM命名规范。提交前需确保所有单元测试通过。

4. 提交变更时，使用语义化提交信息格式，例如 `feat: add export to CSV functionality` 或 `docs: update admin guide with nginx config`。

5. 发起合并请求至主仓库的develop分支，并在请求描述中清楚说明变更目的、测试覆盖范围以及可能的副作用。核心维护者将在48小时内进行审查。

## 常见问题

**问：某些文档链接无法访问，页面显示超时或404，应如何处理？**

答：链接不可访问可能由多种原因导致，包括文档已被迁移、服务器临时维护或网络策略限制。首先请在浏览器中直接打开该链接，确认是否为有效地址。若链接确实已失效，您可以在config.js中注释或移除该条目，并尝试通过来源域名的上级路径寻找替代链接。项目内置的健康检测模块会以红色标记不可用链接，辅助您快速识别。

**问：如何批量更新索引中的链接列表？**

答：项目提供scripts/generate-index.py脚本，您可以将新的链接列表整理为CSV格式，每行包含域名、路径与文档编号，运行脚本后自动生成新的config.js。若您希望保留已有链接的访问状态记录，请在更新前备份config.js中的健康缓存字段。

**问：部署至生产环境时，如何配置Nginx以提供正确的MIME类型？**

答：确保Nginx配置中包含对.doc文件类型的正确映射。在mime.types中添加 `application/msword doc;`，或在location块中显式设置 `default_type application/msword`。若文档链接为跨域资源，还需配置 `add_header Access-Control-Allow-Origin *` 以允许前端检测脚本正常发起请求。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

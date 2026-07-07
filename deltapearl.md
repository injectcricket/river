# WebDocs 分布式文档资源导航系统

WebDocs 是一个面向技术研究、学术检索与文档挖掘场景的轻量化文档资源导航系统。项目定位为分布式外链资源汇总平台，不存储任何实体文档内容，仅提供标准化文档资源的元数据索引与访问路径聚合服务。目标用户包括科研辅助人员、技术情报分析师、自动化采集系统运维者以及需要批量获取结构化文档资源链接的工程团队。系统以极简的静态资源映射方式，将大量分散于不同域名的文档资源整合至统一的访问视图之下，降低人工检索与维护成本。

## 功能概览

多源域名资源聚合：系统内置多个独立域名节点的文档资源路径映射，支持跨域文档链接的统一归集与展示。

轻量化文档资源索引：所有资源以 .doc 格式链接形式存在，无需额外存储空间，仅维护 URL 索引表。

快速检索与过滤：支持按资源来源域名、文档编号特征进行模式匹配检索，便于快速定位特定批次资源。

批量链接导出：提供原始资源链接批量导出能力，便于下游系统进行批量下载、镜像备份或内容分析。

零依赖前端展示：前端界面基于原生 HTML + CSS 构建，无需任何第三方前端框架，兼容主流浏览器。

静态部署友好：全站可编译为纯静态文件，支持部署于 Nginx、Apache、CDN 或对象存储服务。

可扩展资源源配置：支持通过配置文件新增或移除文档源域名与路径映射，适应资源节点动态变化。

自动健康检查集成：提供可选的资源链接可用性探测模块，便于运维人员及时发现失效链接。

## 应用场景

技术文档镜像站点建设：技术团队可利用 WebDocs 汇聚来自不同源站点的技术白皮书、设计文档和规范说明，快速搭建内部技术文档导航门户，供团队成员查阅。

学术资源采集管道前置：学术数据采集系统可将 WebDocs 作为种子链接池，从中提取文档 URL 并进行内容抓取、全文索引与知识图谱构建。

离线文档包制作基础：运维人员可依据 WebDocs 导出的链接列表，使用 wget 或 aria2 工具批量下载文档资源，制作离线文档包用于内网分发或应急查阅。

文档资源变化监测：通过定期对比 WebDocs 中链接的可用性状态，可监测源站点文档的增删改情况，辅助进行资源生命周期管理。

自动化报告生成辅助：数据分析师可将 WebDocs 中的文档链接按域名分组统计，生成资源分布报告，用于评估各源站点的文档贡献度与可用性趋势。

## 快速开始

执行以下命令完成 WebDocs 项目的克隆、依赖安装与本地运行。

```bash
git clone https://github.com/webdocs/webdocs.git
cd webdocs
pip install -r requirements.txt
python app.py
```

上述命令执行后，本地服务将启动于 127.0.0.1:5000。浏览器访问该地址即可查看文档资源导航主界面。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 核心运行环境，用于提供本地服务与资源索引管理 |
| pip | 20.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| Flask | 2.0.0 及以上 | Web 框架，提供 HTTP 服务与路由功能 |
| requests | 2.25.0 及以上 | 用于资源链接健康检查模块中的网络请求 |
| pyyaml | 5.4.0 及以上 | 用于解析资源源配置文件，支持 YAML 格式的源定义 |
| markdown | 3.3.0 及以上 | 用于将项目文档中的 Markdown 内容渲染为 HTML 页面 |
| pytest | 6.0.0 及以上 | 单元测试框架，仅在开发测试环境中使用 |
| gunicorn | 20.0.0 及以上 | 生产环境 WSGI 服务器，用于高性能部署 |
| watchdog | 2.0.0 及以上 | 可选依赖，用于开发模式下的自动重载 |
| flake8 | 3.9.0 及以上 | 代码风格检查工具，仅在代码审查流程中使用 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | /docs/getting-started.md | 如何快速运行项目、理解核心概念与基本操作流程 |
| 配置手册 | /docs/configuration.md | 如何配置资源源域名、路径映射规则及健康检查参数 |
| API 参考 | /docs/api.md | 系统提供了哪些 HTTP 接口、如何通过 API 获取资源列表与执行导出 |
| 部署指南 | /docs/deployment.md | 如何将系统部署至生产环境、配置反向代理与开启 HTTPS |
| 运维手册 | /docs/operations.md | 如何执行资源链接健康检查、查看日志及处理常见故障 |

## 资源列表

- h5.mobile.fuvxie.cn/Article/387702.doc
- h5.mobile.cmcvrr.cn/Article/7710.doc
- h5.mobile.nzfnve.cn/Article/34546.doc
- h5.mobile.jnjpgf.cn/Article/541374.doc
- h5.mobile.cvsifc.cn/Article/63194.doc
- h5.mobile.nzfnve.cn/Article/8674545.doc
- h5.mobile.cmcvrr.cn/Article/030236.doc
- h5.mobile.jnjpgf.cn/Article/9493107.doc
- h5.mobile.cvsifc.cn/Article/40606.doc
- h5.mobile.nwbbyt.cn/Article/2782.doc
- h5.mobile.fuvxie.cn/Article/1650.doc
- h5.mobile.cvsifc.cn/Article/533626.doc
- h5.mobile.jnjpgf.cn/Article/7554498.doc
- h5.mobile.nzfnve.cn/Article/71163.doc
- h5.mobile.cmcvrr.cn/Article/7937531.doc
- h5.mobile.cvsifc.cn/Article/1798.doc
- h5.mobile.nzfnve.cn/Article/3038232.doc
- h5.mobile.hcbezg.cn/Article/05340.doc
- h5.mobile.nwbbyt.cn/Article/5867893.doc
- h5.mobile.puhvjy.cn/Article/88629.doc
- h5.mobile.puhvjy.cn/Article/5300289.doc
- h5.mobile.nwbbyt.cn/Article/1326893.doc
- h5.mobile.puhvjy.cn/Article/938618.doc
- h5.mobile.cmcvrr.cn/Article/51876.doc
- h5.mobile.cvsifc.cn/Article/2860258.doc
- h5.mobile.jnjpgf.cn/Article/5301.doc
- h5.mobile.fuvxie.cn/Article/36411.doc
- h5.mobile.jnjpgf.cn/Article/901783.doc
- h5.mobile.nzfnve.cn/Article/4283.doc
- h5.mobile.cvsifc.cn/Article/8455.doc
- h5.mobile.jnjpgf.cn/Article/3847155.doc
- h5.mobile.cmcvrr.cn/Article/8701234.doc
- h5.mobile.puhvjy.cn/Article/78095.doc
- h5.mobile.puhvjy.cn/Article/19997.doc
- h5.mobile.fuvxie.cn/Article/4362684.doc
- h5.mobile.nwbbyt.cn/Article/18063.doc
- h5.mobile.fuvxie.cn/Article/8559.doc
- h5.mobile.jnjpgf.cn/Article/9784.doc
- h5.mobile.fuvxie.cn/Article/4545982.doc
- h5.mobile.jnjpgf.cn/Article/099491.doc
- h5.mobile.jnjpgf.cn/Article/03982.doc
- h5.mobile.nzfnve.cn/Article/16572.doc
- h5.mobile.fuvxie.cn/Article/236587.doc
- h5.mobile.fuvxie.cn/Article/9283172.doc
- h5.mobile.jnjpgf.cn/Article/440613.doc
- h5.mobile.hcbezg.cn/Article/442260.doc
- h5.mobile.puhvjy.cn/Article/23840.doc
- h5.mobile.nzfnve.cn/Article/1427657.doc
- h5.mobile.puhvjy.cn/Article/908449.doc
- h5.mobile.nzfnve.cn/Article/7954.doc
- h5.mobile.puhvjy.cn/Article/5267378.doc
- h5.mobile.fuvxie.cn/Article/495239.doc
- h5.mobile.cvsifc.cn/Article/07474.doc
- h5.mobile.cmcvrr.cn/Article/1805255.doc
- h5.mobile.nwbbyt.cn/Article/706957.doc
- h5.mobile.cvsifc.cn/Article/05305.doc
- h5.mobile.puhvjy.cn/Article/5604623.doc
- h5.mobile.fuvxie.cn/Article/6065072.doc
- h5.mobile.fuvxie.cn/Article/8895.doc
- h5.mobile.hcbezg.cn/Article/5107102.doc
- h5.mobile.cvsifc.cn/Article/997992.doc
- h5.mobile.puhvjy.cn/Article/2443792.doc
- h5.mobile.fuvxie.cn/Article/0342.doc
- h5.mobile.fuvxie.cn/Article/693441.doc
- h5.mobile.cvsifc.cn/Article/5871121.doc
- h5.mobile.nwbbyt.cn/Article/7024.doc
- h5.mobile.hcbezg.cn/Article/3470858.doc
- h5.mobile.cvsifc.cn/Article/8335.doc
- h5.mobile.fuvxie.cn/Article/621416.doc
- h5.mobile.puhvjy.cn/Article/62713.doc
- h5.mobile.fuvxie.cn/Article/564712.doc
- h5.mobile.fuvxie.cn/Article/4986746.doc
- h5.mobile.fuvxie.cn/Article/7017.doc
- h5.mobile.nwbbyt.cn/Article/9207682.doc
- h5.mobile.jnjpgf.cn/Article/3588647.doc
- h5.mobile.hcbezg.cn/Article/879664.doc
- h5.mobile.nwbbyt.cn/Article/52633.doc
- h5.mobile.puhvjy.cn/Article/10529.doc
- h5.mobile.fuvxie.cn/Article/2817.doc
- h5.mobile.jnjpgf.cn/Article/8096.doc
- h5.mobile.jnjpgf.cn/Article/4897502.doc
- h5.mobile.nzfnve.cn/Article/50285.doc
- h5.mobile.cvsifc.cn/Article/0139.doc
- h5.mobile.hcbezg.cn/Article/1850951.doc
- h5.mobile.cmcvrr.cn/Article/8551.doc
- h5.mobile.fuvxie.cn/Article/160899.doc
- h5.mobile.puhvjy.cn/Article/1957877.doc
- h5.mobile.puhvjy.cn/Article/5230.doc
- h5.mobile.fuvxie.cn/Article/920894.doc
- h5.mobile.hcbezg.cn/Article/80891.doc
- h5.mobile.cmcvrr.cn/Article/3379.doc
- h5.mobile.nzfnve.cn/Article/650039.doc
- h5.mobile.cvsifc.cn/Article/0012.doc
- h5.mobile.nzfnve.cn/Article/25579.doc
- h5.mobile.nzfnve.cn/Article/9830635.doc
- h5.mobile.fuvxie.cn/Article/8602493.doc
- h5.mobile.jnjpgf.cn/Article/868135.doc
- h5.mobile.jnjpgf.cn/Article/348327.doc
- h5.mobile.cmcvrr.cn/Article/8330873.doc
- h5.mobile.jnjpgf.cn/Article/758004.doc
- h5.mobile.puhvjy.cn/Article/4984425.doc
- h5.mobile.nwbbyt.cn/Article/1737.doc
- h5.mobile.cvsifc.cn/Article/5655.doc
- h5.mobile.hcbezg.cn/Article/18491.doc
- h5.mobile.jnjpgf.cn/Article/5936243.doc
- h5.mobile.nwbbyt.cn/Article/9093.doc
- h5.mobile.nwbbyt.cn/Article/64280.doc
- h5.mobile.nzfnve.cn/Article/929095.doc
- h5.mobile.cmcvrr.cn/Article/028154.doc
- h5.mobile.cmcvrr.cn/Article/9347174.doc
- h5.mobile.nwbbyt.cn/Article/31726.doc
- h5.mobile.cvsifc.cn/Article/418570.doc
- h5.mobile.nwbbyt.cn/Article/307152.doc
- h5.mobile.nzfnve.cn/Article/50254.doc
- h5.mobile.cmcvrr.cn/Article/78585.doc
- h5.mobile.nwbbyt.cn/Article/3008.doc
- h5.mobile.fuvxie.cn/Article/4450638.doc
- h5.mobile.nwbbyt.cn/Article/468156.doc
- h5.mobile.cmcvrr.cn/Article/3142068.doc
- h5.mobile.nwbbyt.cn/Article/237722.doc
- h5.mobile.hcbezg.cn/Article/2737193.doc
- h5.mobile.jnjpgf.cn/Article/129083.doc
- h5.mobile.fuvxie.cn/Article/01363.doc
- h5.mobile.nwbbyt.cn/Article/506181.doc
- h5.mobile.puhvjy.cn/Article/7833.doc
- h5.mobile.cmcvrr.cn/Article/585280.doc
- h5.mobile.nwbbyt.cn/Article/1072675.doc
- h5.mobile.nzfnve.cn/Article/6347.doc
- h5.mobile.nwbbyt.cn/Article/5631392.doc
- h5.mobile.hcbezg.cn/Article/730652.doc
- h5.mobile.nzfnve.cn/Article/6499.doc
- h5.mobile.fuvxie.cn/Article/1533320.doc
- h5.mobile.hcbezg.cn/Article/0440.doc
- h5.mobile.cvsifc.cn/Article/5009391.doc
- h5.mobile.fuvxie.cn/Article/6422.doc
- h5.mobile.nzfnve.cn/Article/0108516.doc
- h5.mobile.hcbezg.cn/Article/020819.doc
- h5.mobile.nwbbyt.cn/Article/9733.doc
- h5.mobile.nwbbyt.cn/Article/91936.doc
- h5.mobile.fuvxie.cn/Article/8605698.doc
- h5.mobile.hcbezg.cn/Article/554470.doc
- h5.mobile.puhvjy.cn/Article/0297733.doc
- h5.mobile.fuvxie.cn/Article/451502.doc
- h5.mobile.hcbezg.cn/Article/05504.doc
- h5.mobile.cvsifc.cn/Article/78452.doc
- h5.mobile.hcbezg.cn/Article/64585.doc
- h5.mobile.nzfnve.cn/Article/00432.doc
- h5.mobile.puhvjy.cn/Article/3687285.doc
- h5.mobile.cmcvrr.cn/Article/872808.doc
- h5.mobile.nwbbyt.cn/Article/0002.doc
- h5.mobile.fuvxie.cn/Article/752681.doc
- h5.mobile.cmcvrr.cn/Article/410458.doc
- h5.mobile.hcbezg.cn/Article/3006529.doc
- h5.mobile.jnjpgf.cn/Article/9218.doc
- h5.mobile.cvsifc.cn/Article/48667.doc
- h5.mobile.fuvxie.cn/Article/46569.doc
- h5.mobile.fuvxie.cn/Article/945427.doc
- h5.mobile.hcbezg.cn/Article/727225.doc
- h5.mobile.nzfnve.cn/Article/4538265.doc
- h5.mobile.nwbbyt.cn/Article/8052026.doc
- h5.mobile.fuvxie.cn/Article/0842266.doc
- h5.mobile.jnjpgf.cn/Article/653051.doc
- h5.mobile.cvsifc.cn/Article/8451.doc
- h5.mobile.puhvjy.cn/Article/7245.doc
- h5.mobile.jnjpgf.cn/Article/645972.doc
- h5.mobile.hcbezg.cn/Article/88435.doc
- h5.mobile.nzfnve.cn/Article/7180.doc
- h5.mobile.nwbbyt.cn/Article/7481.doc
- h5.mobile.fuvxie.cn/Article/372351.doc
- h5.mobile.puhvjy.cn/Article/740934.doc
- h5.mobile.cmcvrr.cn/Article/3634500.doc
- h5.mobile.cvsifc.cn/Article/42358.doc
- h5.mobile.cmcvrr.cn/Article/405344.doc
- h5.mobile.fuvxie.cn/Article/8889.doc
- h5.mobile.puhvjy.cn/Article/8582.doc
- h5.mobile.hcbezg.cn/Article/285188.doc
- h5.mobile.cmcvrr.cn/Article/5992780.doc
- h5.mobile.nwbbyt.cn/Article/20828.doc
- h5.mobile.puhvjy.cn/Article/0240.doc
- h5.mobile.cmcvrr.cn/Article/654021.doc
- h5.mobile.hcbezg.cn/Article/83169.doc
- h5.mobile.cmcvrr.cn/Article/9144290.doc
- h5.mobile.jnjpgf.cn/Article/459941.doc
- h5.mobile.hcbezg.cn/Article/6088.doc
- h5.mobile.cvsifc.cn/Article/4454.doc
- h5.mobile.nwbbyt.cn/Article/5378679.doc
- h5.mobile.cvsifc.cn/Article/6264240.doc
- h5.mobile.nwbbyt.cn/Article/8534.doc
- h5.mobile.fuvxie.cn/Article/26584.doc
- h5.mobile.cvsifc.cn/Article/670399.doc
- h5.mobile.cvsifc.cn/Article/1512741.doc
- h5.mobile.puhvjy.cn/Article/3480180.doc
- h5.mobile.hcbezg.cn/Article/5632.doc
- h5.mobile.puhvjy.cn/Article/2607576.doc
- h5.mobile.nwbbyt.cn/Article/139198.doc
- h5.mobile.hcbezg.cn/Article/22876.doc
- h5.mobile.cmcvrr.cn/Article/7317.doc
- h5.mobile.nzfnve.cn/Article/014293.doc
- h5.mobile.cvsifc.cn/Article/36517.doc
- h5.mobile.cvsifc.cn/Article/80816.doc
- h5.mobile.hcbezg.cn/Article/1636.doc
- h5.mobile.cmcvrr.cn/Article/213618.doc
- h5.mobile.hcbezg.cn/Article/166023.doc
- h5.mobile.cvsifc.cn/Article/1719.doc
- h5.mobile.cvsifc.cn/Article/7119199.doc
- h5.mobile.nzfnve.cn/Article/5456105.doc
- h5.mobile.hcbezg.cn/Article/57904.doc
- h5.mobile.cmcvrr.cn/Article/1020859.doc
- h5.mobile.cmcvrr.cn/Article/426727.doc
- h5.mobile.nzfnve.cn/Article/7820.doc
- h5.mobile.cvsifc.cn/Article/751216.doc
- h5.mobile.cmcvrr.cn/Article/0925132.doc
- h5.mobile.hcbezg.cn/Article/3162931.doc
- h5.mobile.jnjpgf.cn/Article/46790.doc
- h5.mobile.cmcvrr.cn/Article/141632.doc
- h5.mobile.cmcvrr.cn/Article/2145.doc
- h5.mobile.puhvjy.cn/Article/57358.doc
- h5.mobile.fuvxie.cn/Article/4025089.doc
- h5.mobile.fuvxie.cn/Article/22093.doc
- h5.mobile.cmcvrr.cn/Article/9953757.doc
- h5.mobile.puhvjy.cn/Article/35294.doc
- h5.mobile.cmcvrr.cn/Article/019081.doc
- h5.mobile.hcbezg.cn/Article/2457438.doc
- h5.mobile.puhvjy.cn/Article/35264.doc
- h5.mobile.jnjpgf.cn/Article/506326.doc
- h5.mobile.nzfnve.cn/Article/5712419.doc
- h5.mobile.hcbezg.cn/Article/5296123.doc
- h5.mobile.cmcvrr.cn/Article/162499.doc
- h5.mobile.cmcvrr.cn/Article/67337.doc
- h5.mobile.nwbbyt.cn/Article/0079133.doc
- h5.mobile.puhvjy.cn/Article/521266.doc
- h5.mobile.fuvxie.cn/Article/2352940.doc
- h5.mobile.cvsifc.cn/Article/8161.doc
- h5.mobile.cmcvrr.cn/Article/49211.doc
- h5.mobile.nzfnve.cn/Article/32250.doc
- h5.mobile.nwbbyt.cn/Article/579013.doc
- h5.mobile.nzfnve.cn/Article/406349.doc
- h5.mobile.nzfnve.cn/Article/9747868.doc
- h5.mobile.cvsifc.cn/Article/7745.doc
- h5.mobile.puhvjy.cn/Article/57537.doc
- h5.mobile.fuvxie.cn/Article/25086.doc
- h5.mobile.fuvxie.cn/Article/01806.doc
- h5.mobile.puhvjy.cn/Article/000145.doc
- h5.mobile.puhvjy.cn/Article/2153486.doc
- h5.mobile.jnjpgf.cn/Article/6760000.doc
- h5.mobile.nzfnve.cn/Article/4353210.doc
- h5.mobile.cvsifc.cn/Article/568930.doc
- h5.mobile.hcbezg.cn/Article/5192461.doc
- h5.mobile.fuvxie.cn/Article/2233.doc
- h5.mobile.cvsifc.cn/Article/1307.doc

## 项目结构

```
webdocs/
├── app.py                     # Flask 应用入口，初始化路由与启动服务
├── config/
│   ├── __init__.py            # 配置模块初始化
│   ├── settings.py            # 全局配置项（调试模式、端口、缓存策略）
│   └── sources.yaml           # 资源源域名与路径映射配置文件
├── core/
│   ├── __init__.py            # 核心模块初始化
│   ├── indexer.py             # 资源索引引擎，负责加载与解析 sources.yaml
│   ├── checker.py             # 健康检查模块，探测外部链接可达性
│   └── exporter.py            # 链接导出模块，支持 JSON / CSV / TXT 格式
├── web/
│   ├── __init__.py            # Web 模块初始化
│   ├── routes.py              # 路由定义，包含首页、列表页、API 接口
│   ├── templates/             # Jinja2 模板目录
│   │   ├── base.html          # 基础页面模板，定义公共头部与底部
│   │   ├── index.html         # 首页模板，展示资源统计与快速入口
│   │   └── list.html          # 资源列表页模板，展示全量链接
│   └── static/                # 静态资源目录
│       ├── css/
│       │   └── style.css      # 自定义样式表
│       └── js/
│           └── main.js        # 前端交互脚本（搜索过滤、分页）
├── tests/
│   ├── __init__.py            # 测试模块初始化
│   ├── test_indexer.py        # 索引引擎单元测试
│   ├── test_checker.py        # 健康检查模块单元测试
│   └── test_routes.py         # Web 路由接口测试
├── docs/
│   ├── getting-started.md     # 入门指南文档
│   ├── configuration.md       # 配置说明文档
│   ├── api.md                 # API 接口文档
│   ├── deployment.md          # 部署指南文档
│   └── operations.md          # 运维手册文档
├── scripts/
│   ├── check_links.py         # 独立链接健康检查脚本（可定时执行）
│   ├── export_links.py        # 命令行导出工具
│   └── sync_sources.py        # 资源源同步脚本，用于外部源更新
├── requirements.txt           # Python 依赖声明文件
├── .flake8                    # flake8 代码风格检查配置
├── .gitignore                 # Git 忽略文件规则
└── README.md                  # 项目说明文档（本文件）
```

## 贡献指南

1. 复刻仓库并创建特性分支：访问 GitHub 项目主页，点击 Fork 按钮将仓库复制至个人账号，随后使用 git checkout -b feature/your-feature-name 创建新分支。

2. 实施变更并遵循代码风格：修改代码后，确保通过 flake8 风格检查，并补充或更新对应的单元测试用例。新增资源源需同步更新 sources.yaml 配置文件。

3. 提交变更并推送至远程仓库：使用 git commit -m "描述本次变更的简要信息" 提交修改，随后执行 git push origin feature/your-feature-name 推送至远程。

4. 创建 Pull Request 并参与讨论：在 GitHub 页面发起 Pull Request，详细描述变更目的与实现方式。项目维护者将进行代码审查，审查通过后合并至主分支。

5. 文档同步更新：若变更涉及用户使用方式或配置格式，请同步更新 docs 目录下的对应文档，确保文档与代码保持一致。

## 常见问题

Q：资源列表中的链接无法访问怎么办？

A：由于 WebDocs 仅提供链接索引，不存储文档副本，链接可用性依赖于源站点的服务状态。若发现大量链接不可用，建议先执行 scripts/check_links.py 脚本进行批量探测，确认源站是否存在整体故障。若仅个别链接失效，可在 sources.yaml 中注释或移除对应路径，等待源站恢复后重新启用。

Q：如何添加新的文档资源链接？

A：通过修改 config/sources.yaml 文件，按照既有的域名与路径格式新增条目。新增后重启服务或调用 /api/reload 接口使配置生效。注意新增的链接需为 .doc 文档格式，系统暂不支持其他文档类型。

Q：项目是否支持 HTTPS 访问？

A：WebDocs 自身服务默认以 HTTP 协议提供访问。若需开启 HTTPS，建议在应用前端部署 Nginx 或 Apache 反向代理，并在代理层配置 SSL 证书。部署指南文档中提供了详细的代理配置示例。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

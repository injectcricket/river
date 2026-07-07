# LinkSphere 技术资源索引系统

LinkSphere 是一个面向技术研究者和开发者的高密度外链资源整合平台，专注于采集、分类和呈现分布式的技术文章与文档资源。本系统不生产内容，而是作为结构化导航层，帮助用户在海量分散的技术资料中快速定位所需信息。

项目定位为技术资源的中立索引枢纽，适用于需要持续追踪多个技术博客、文档站或资讯来源的研发团队和个人。通过统一的条目化输出，消除手工整理分散链接的繁琐流程，使资源消费从"查找"升级为"筛选"。

## 功能概览

- **多源条目聚合**：系统按预设批次拉取指定域下的文章条目，每条记录包含标题、摘要、发布时间等元数据，支持后续检索与过滤。

- **原始链接直出**：所有收录的资源以原始 URL 形式呈现，不做任何跳转包装或短链压缩，保证来源可追溯且符合防屏蔽策略。

- **批次管理机制**：以 160 批为单位进行资源轮次管理，每批最多容纳 250 个有效链接，便于定期增量更新与过期链接剔除。

- **静态化输出适配**：项目核心输出为纯 Markdown 文档，可直接挂载至静态站点生成器（如 Hugo、VuePress）或作为 CI 流程的产物归档。

- **轻量级依赖**：运行时仅依赖标准 Python 3 环境与 requests、lxml 两个三方库，无数据库或消息队列等重型组件，降低运维成本。

- **结构化目录树**：源码按功能模块拆分为多个子目录，每个模块职责明确，便于二次开发或按需裁剪功能。

- **自动化检测流水线**：内置链接可达性检测脚本，可定期检查收录 URL 的 HTTP 状态码，自动标记失效资源并生成报告。

## 应用场景

- **技术团队内部知识库构建**：研发团队可将 LinkSphere 部署为内部文档聚合页的前端数据源，统一管理来自不同技术博客的参考资料，避免成员各自收藏导致的资源碎片化。

- **开源项目文档外链管理**：开源项目维护者使用本系统整理外部依赖文档、教程或参考实现的相关链接，集中存放于项目仓库的 docs/links 目录下，方便贡献者查阅。

- **个人技术阅读清单维护**：技术博主或资深工程师可利用本系统的批次分类能力，按主题（如分布式系统、编译器原理、数据库内核）组织待读文章列表，形成可持续累积的个人阅读队列。

- **自动化资源监控告警**：运维或 SRE 团队可借助内置的链接检测脚本，定时扫描收录的文档链接，当目标页面返回 404 或 5xx 时触发告警，提前发现文档迁移或下架情况。

## 快速开始

以下步骤适用于 Linux / macOS / Windows WSL 环境。确保系统已安装 Git 和 Python 3.8 以上版本。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/linksphere.git
cd linksphere

# 创建并激活 Python 虚拟环境（推荐）
python3 -m venv venv
source venv/bin/activate  # Windows 下为 venv\Scripts\activate

# 安装运行时依赖
pip install -r requirements.txt

# 运行索引生成脚本（示例：处理第 56 批次）
python scripts/generate_index.py --batch 56 --output ./output/README_56.md

# 检查输出文件
cat ./output/README_56.md
```

若需自定义资源列表，可直接编辑 `data/batch_56.urls` 文件，每行一个 URL，保存后重新运行生成脚本即可。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 或更高 | 核心运行环境，低于 3.8 将无法使用类型注解与 f-string 特性 |
| requests | 2.25.0+ | 用于发起 HTTP 请求获取页面标题及状态码检测 |
| lxml | 4.6.0+ | 高性能 HTML/XML 解析库，用于提取文章元数据 |
| Git | 2.20.0+ | 版本控制工具，用于克隆仓库和管理提交历史 |
| 磁盘空间 | 200 MB 以上 | 存放源码、虚拟环境及生成的索引文件，建议预留 500 MB |
| 网络访问 | 任意 | 需能访问收录的 URL 域名，若在内网环境需配置代理或 hosts |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速部署并生成第一个索引文件；如何理解批次与条目概念 |
| 配置手册 | docs/configuration.md | 如何修改批次大小、输出模板、请求超时与重试策略等参数 |
| 开发指南 | docs/development.md | 如何扩展解析器以支持新的文档站点；如何提交补丁或新增功能 |
| API 参考 | docs/api-reference.md | 核心模块的函数签名、参数说明与返回值结构，面向二次开发者 |
| 运维手册 | docs/operations.md | 如何配置定时任务、日志轮转、失效链接告警与数据备份策略 |
| 变更日志 | CHANGELOG.md | 记录每个版本的新增功能、修复的缺陷与不兼容变更 |

## 资源列表

- https://www.read.fuvxie.cn/Article/7742415.shtml
- https://www.read.puhvjy.cn/Article/6316.shtml
- https://www.read.jnjpgf.cn/Article/3851695.shtml
- https://www.read.hcbezg.cn/Article/6661222.shtml
- https://www.read.jnjpgf.cn/Article/765353.shtml
- https://www.read.nzfnve.cn/Article/0118316.shtml
- https://www.read.puhvjy.cn/Article/9210.shtml
- https://www.read.puhvjy.cn/Article/2765.shtml
- https://www.read.jnjpgf.cn/Article/7899249.shtml
- https://www.read.fuvxie.cn/Article/1234.shtml
- https://www.read.cvsifc.cn/Article/9290834.shtml
- https://www.read.hcbezg.cn/Article/8478095.shtml
- https://www.read.nzfnve.cn/Article/845196.shtml
- https://www.read.nwbbyt.cn/Article/704979.shtml
- https://www.read.cmcvrr.cn/Article/1791.shtml
- https://www.read.hcbezg.cn/Article/4274.shtml
- https://www.read.fuvxie.cn/Article/0399.shtml
- https://www.read.hcbezg.cn/Article/1798748.shtml
- https://www.read.cmcvrr.cn/Article/8796935.shtml
- https://www.read.puhvjy.cn/Article/4768.shtml
- https://www.read.cvsifc.cn/Article/984291.shtml
- https://www.read.jnjpgf.cn/Article/642974.shtml
- https://www.read.puhvjy.cn/Article/4436.shtml
- https://www.read.cvsifc.cn/Article/8795114.shtml
- https://www.read.nzfnve.cn/Article/0956309.shtml
- https://www.read.jnjpgf.cn/Article/399912.shtml
- https://www.read.nwbbyt.cn/Article/77368.shtml
- https://www.read.fuvxie.cn/Article/1942457.shtml
- https://www.read.jnjpgf.cn/Article/9760575.shtml
- https://www.read.hcbezg.cn/Article/733758.shtml
- https://www.read.hcbezg.cn/Article/3073617.shtml
- https://www.read.hcbezg.cn/Article/4023.shtml
- https://www.read.nzfnve.cn/Article/861609.shtml
- https://www.read.jnjpgf.cn/Article/2214234.shtml
- https://www.read.cvsifc.cn/Article/52194.shtml
- https://www.read.cmcvrr.cn/Article/1577763.shtml
- https://www.read.nwbbyt.cn/Article/140192.shtml
- https://www.read.puhvjy.cn/Article/4178561.shtml
- https://www.read.nwbbyt.cn/Article/922322.shtml
- https://www.read.puhvjy.cn/Article/95896.shtml
- https://www.read.puhvjy.cn/Article/033287.shtml
- https://www.read.puhvjy.cn/Article/47742.shtml
- https://www.read.nwbbyt.cn/Article/72959.shtml
- https://www.read.puhvjy.cn/Article/203327.shtml
- https://www.read.cvsifc.cn/Article/175878.shtml
- https://www.read.fuvxie.cn/Article/07430.shtml
- https://www.read.puhvjy.cn/Article/4355925.shtml
- https://www.read.cmcvrr.cn/Article/7919.shtml
- https://www.read.cvsifc.cn/Article/1910099.shtml
- https://www.read.puhvjy.cn/Article/6317.shtml
- https://www.read.nzfnve.cn/Article/56135.shtml
- https://www.read.puhvjy.cn/Article/9880759.shtml
- https://www.read.puhvjy.cn/Article/0491438.shtml
- https://www.read.cvsifc.cn/Article/2243.shtml
- https://www.read.puhvjy.cn/Article/4189871.shtml
- https://www.read.hcbezg.cn/Article/470382.shtml
- https://www.read.fuvxie.cn/Article/223466.shtml
- https://www.read.nwbbyt.cn/Article/184899.shtml
- https://www.read.fuvxie.cn/Article/9936.shtml
- https://www.read.cvsifc.cn/Article/676476.shtml
- https://www.read.cmcvrr.cn/Article/064329.shtml
- https://www.read.fuvxie.cn/Article/39870.shtml
- https://www.read.nwbbyt.cn/Article/54862.shtml
- https://www.read.cvsifc.cn/Article/9172725.shtml
- https://www.read.puhvjy.cn/Article/932768.shtml
- https://www.read.jnjpgf.cn/Article/4561500.shtml
- https://www.read.fuvxie.cn/Article/866369.shtml
- https://www.read.hcbezg.cn/Article/0346.shtml
- https://www.read.cmcvrr.cn/Article/9786855.shtml
- https://www.read.fuvxie.cn/Article/990286.shtml
- https://www.read.cvsifc.cn/Article/9462.shtml
- https://www.read.jnjpgf.cn/Article/6480170.shtml
- https://www.read.puhvjy.cn/Article/21089.shtml
- https://www.read.jnjpgf.cn/Article/4169.shtml
- https://www.read.hcbezg.cn/Article/7936.shtml
- https://www.read.jnjpgf.cn/Article/8298109.shtml
- https://www.read.fuvxie.cn/Article/297439.shtml
- https://www.read.cvsifc.cn/Article/6426715.shtml
- https://www.read.nwbbyt.cn/Article/9540761.shtml
- https://www.read.hcbezg.cn/Article/742298.shtml
- https://www.read.fuvxie.cn/Article/9388661.shtml
- https://www.read.cmcvrr.cn/Article/103984.shtml
- https://www.read.hcbezg.cn/Article/06997.shtml
- https://www.read.nzfnve.cn/Article/6883803.shtml
- https://www.read.nwbbyt.cn/Article/698978.shtml
- https://www.read.hcbezg.cn/Article/5138730.shtml
- https://www.read.jnjpgf.cn/Article/017442.shtml
- https://www.read.cvsifc.cn/Article/2676013.shtml
- https://www.read.cvsifc.cn/Article/9383018.shtml
- https://www.read.nwbbyt.cn/Article/73568.shtml
- https://www.read.hcbezg.cn/Article/89574.shtml
- https://www.read.nzfnve.cn/Article/11386.shtml
- https://www.read.jnjpgf.cn/Article/63805.shtml
- https://www.read.nwbbyt.cn/Article/00142.shtml
- https://www.read.nzfnve.cn/Article/73775.shtml
- https://www.read.hcbezg.cn/Article/6245028.shtml
- https://www.read.puhvjy.cn/Article/33952.shtml
- https://www.read.fuvxie.cn/Article/011917.shtml
- https://www.read.cvsifc.cn/Article/269364.shtml
- https://www.read.cmcvrr.cn/Article/5351685.shtml
- https://www.read.fuvxie.cn/Article/0428402.shtml
- https://www.read.puhvjy.cn/Article/3488.shtml
- https://www.read.hcbezg.cn/Article/7005.shtml
- https://www.read.cvsifc.cn/Article/9690701.shtml
- https://www.read.cmcvrr.cn/Article/0131597.shtml
- https://www.read.jnjpgf.cn/Article/6062.shtml
- https://www.read.cvsifc.cn/Article/3691.shtml
- https://www.read.puhvjy.cn/Article/534274.shtml
- https://www.read.puhvjy.cn/Article/377057.shtml
- https://www.read.fuvxie.cn/Article/5281513.shtml
- https://www.read.cvsifc.cn/Article/40043.shtml
- https://www.read.nwbbyt.cn/Article/959845.shtml
- https://www.read.cmcvrr.cn/Article/97610.shtml
- https://www.read.nwbbyt.cn/Article/042363.shtml
- https://www.read.hcbezg.cn/Article/1828.shtml
- https://www.read.jnjpgf.cn/Article/2103.shtml
- https://www.read.cvsifc.cn/Article/887562.shtml
- https://www.read.hcbezg.cn/Article/02484.shtml
- https://www.read.cvsifc.cn/Article/9047408.shtml
- https://www.read.nzfnve.cn/Article/13993.shtml
- https://www.read.nwbbyt.cn/Article/10140.shtml
- https://www.read.jnjpgf.cn/Article/0522.shtml
- https://www.read.fuvxie.cn/Article/0991390.shtml
- https://www.read.fuvxie.cn/Article/7335.shtml
- https://www.read.nwbbyt.cn/Article/2929853.shtml
- https://www.read.nwbbyt.cn/Article/2395163.shtml
- https://www.read.fuvxie.cn/Article/11335.shtml
- https://www.read.hcbezg.cn/Article/4427.shtml
- https://www.read.puhvjy.cn/Article/5539.shtml
- https://www.read.nwbbyt.cn/Article/0237469.shtml
- https://www.read.hcbezg.cn/Article/553765.shtml
- https://www.read.nwbbyt.cn/Article/38630.shtml
- https://www.read.cvsifc.cn/Article/8162330.shtml
- https://www.read.nwbbyt.cn/Article/14313.shtml
- https://www.read.nzfnve.cn/Article/0823983.shtml
- https://www.read.nzfnve.cn/Article/61006.shtml
- https://www.read.hcbezg.cn/Article/80718.shtml
- https://www.read.puhvjy.cn/Article/2202.shtml
- https://www.read.cvsifc.cn/Article/2725073.shtml
- https://www.read.jnjpgf.cn/Article/86259.shtml
- https://www.read.hcbezg.cn/Article/9776336.shtml
- https://www.read.jnjpgf.cn/Article/17767.shtml
- https://www.read.jnjpgf.cn/Article/1308255.shtml
- https://www.read.cmcvrr.cn/Article/9527.shtml
- https://www.read.puhvjy.cn/Article/7092.shtml
- https://www.read.cmcvrr.cn/Article/299396.shtml
- https://www.read.puhvjy.cn/Article/347113.shtml
- https://www.read.cmcvrr.cn/Article/246568.shtml
- https://www.read.puhvjy.cn/Article/4394703.shtml
- https://www.read.fuvxie.cn/Article/2775.shtml
- https://www.read.nwbbyt.cn/Article/2384.shtml
- https://www.read.nzfnve.cn/Article/693387.shtml
- https://www.read.puhvjy.cn/Article/87922.shtml
- https://www.read.fuvxie.cn/Article/3232109.shtml
- https://www.read.puhvjy.cn/Article/06286.shtml
- https://www.read.cvsifc.cn/Article/0066.shtml
- https://www.read.cvsifc.cn/Article/87142.shtml
- https://www.read.cmcvrr.cn/Article/5398518.shtml
- https://www.read.fuvxie.cn/Article/4342535.shtml
- https://www.read.fuvxie.cn/Article/31527.shtml
- https://www.read.nzfnve.cn/Article/530097.shtml
- https://www.read.nzfnve.cn/Article/8592560.shtml
- https://www.read.jnjpgf.cn/Article/631737.shtml
- https://www.read.jnjpgf.cn/Article/0037149.shtml
- https://www.read.cmcvrr.cn/Article/7376.shtml
- https://www.read.cvsifc.cn/Article/0206659.shtml
- https://www.read.puhvjy.cn/Article/769504.shtml
- https://www.read.fuvxie.cn/Article/181091.shtml
- https://www.read.hcbezg.cn/Article/951877.shtml
- https://www.read.jnjpgf.cn/Article/18601.shtml
- https://www.read.puhvjy.cn/Article/5786879.shtml
- https://www.read.fuvxie.cn/Article/291110.shtml
- https://www.read.nzfnve.cn/Article/8886.shtml
- https://www.read.jnjpgf.cn/Article/7053354.shtml
- https://www.read.fuvxie.cn/Article/52392.shtml
- https://www.read.cmcvrr.cn/Article/7962729.shtml
- https://www.read.puhvjy.cn/Article/70605.shtml
- https://www.read.cvsifc.cn/Article/9449.shtml
- https://www.read.fuvxie.cn/Article/02633.shtml
- https://www.read.fuvxie.cn/Article/0973168.shtml
- https://www.read.nzfnve.cn/Article/4634764.shtml
- https://www.read.jnjpgf.cn/Article/9988509.shtml
- https://www.read.jnjpgf.cn/Article/2495.shtml
- https://www.read.jnjpgf.cn/Article/68039.shtml
- https://www.read.fuvxie.cn/Article/495564.shtml
- https://www.read.jnjpgf.cn/Article/048207.shtml
- https://www.read.cmcvrr.cn/Article/814360.shtml
- https://www.read.nzfnve.cn/Article/6149845.shtml
- https://www.read.fuvxie.cn/Article/7222.shtml
- https://www.read.cvsifc.cn/Article/72801.shtml
- https://www.read.hcbezg.cn/Article/3661030.shtml
- https://www.read.puhvjy.cn/Article/9364174.shtml
- https://www.read.hcbezg.cn/Article/089396.shtml
- https://www.read.fuvxie.cn/Article/02879.shtml
- https://www.read.nwbbyt.cn/Article/4896280.shtml
- https://www.read.fuvxie.cn/Article/132281.shtml
- https://www.read.cmcvrr.cn/Article/9319.shtml
- https://www.read.nwbbyt.cn/Article/05996.shtml
- https://www.read.hcbezg.cn/Article/5982376.shtml
- https://www.read.puhvjy.cn/Article/586699.shtml
- https://www.read.fuvxie.cn/Article/66405.shtml
- https://www.read.cvsifc.cn/Article/94756.shtml
- https://www.read.nzfnve.cn/Article/70289.shtml
- https://www.read.jnjpgf.cn/Article/7040425.shtml
- https://www.read.cvsifc.cn/Article/7286.shtml
- https://www.read.nwbbyt.cn/Article/036533.shtml
- https://www.read.nzfnve.cn/Article/5067.shtml
- https://www.read.nzfnve.cn/Article/0235192.shtml
- https://www.read.nzfnve.cn/Article/2756674.shtml
- https://www.read.cvsifc.cn/Article/62342.shtml
- https://www.read.cvsifc.cn/Article/6188252.shtml
- https://www.read.nwbbyt.cn/Article/8573579.shtml
- https://www.read.hcbezg.cn/Article/660865.shtml
- https://www.read.cvsifc.cn/Article/190658.shtml
- https://www.read.nwbbyt.cn/Article/6848.shtml
- https://www.read.jnjpgf.cn/Article/594446.shtml
- https://www.read.fuvxie.cn/Article/7689.shtml
- https://www.read.fuvxie.cn/Article/35843.shtml
- https://www.read.cvsifc.cn/Article/7081391.shtml
- https://www.read.fuvxie.cn/Article/4912.shtml
- https://www.read.fuvxie.cn/Article/7089560.shtml
- https://www.read.nzfnve.cn/Article/70290.shtml
- https://www.read.puhvjy.cn/Article/1178036.shtml
- https://www.read.cmcvrr.cn/Article/7997.shtml
- https://www.read.cmcvrr.cn/Article/7516.shtml
- https://www.read.jnjpgf.cn/Article/9895.shtml
- https://www.read.cmcvrr.cn/Article/390414.shtml
- https://www.read.puhvjy.cn/Article/9457.shtml
- https://www.read.cmcvrr.cn/Article/1221.shtml
- https://www.read.fuvxie.cn/Article/8387228.shtml
- https://www.read.fuvxie.cn/Article/19963.shtml
- https://www.read.nwbbyt.cn/Article/063185.shtml
- https://www.read.hcbezg.cn/Article/4254.shtml
- https://www.read.cvsifc.cn/Article/1625965.shtml
- https://www.read.cmcvrr.cn/Article/0604.shtml
- https://www.read.jnjpgf.cn/Article/0142099.shtml
- https://www.read.cmcvrr.cn/Article/0236.shtml
- https://www.read.puhvjy.cn/Article/878680.shtml
- https://www.read.cvsifc.cn/Article/293144.shtml
- https://www.read.fuvxie.cn/Article/310062.shtml
- https://www.read.jnjpgf.cn/Article/283011.shtml
- https://www.read.nwbbyt.cn/Article/1100727.shtml
- https://www.read.cmcvrr.cn/Article/963086.shtml
- https://www.read.jnjpgf.cn/Article/838617.shtml
- https://www.read.nzfnve.cn/Article/0097842.shtml
- https://www.read.hcbezg.cn/Article/189471.shtml
- https://www.read.fuvxie.cn/Article/13989.shtml
- https://www.read.puhvjy.cn/Article/8731.shtml
- https://www.read.cmcvrr.cn/Article/72129.shtml
- https://www.read.puhvjy.cn/Article/5710.shtml

## 项目结构

```
linksphere/
├── README.md                     # 项目总览与快速入门文档
├── CHANGELOG.md                  # 版本迭代记录，含日期与变更摘要
├── LICENSE                       # MIT 许可证全文
├── requirements.txt              # Python 依赖列表，固定版本号
├── .gitignore                    # 忽略虚拟环境、缓存与临时输出文件
├── config/
│   ├── settings.yaml             # 全局配置：请求超时、重试次数、批次大小
│   └── domains.yaml              # 允许收录的域名白名单与别名映射
├── data/
│   ├── batch_56.urls             # 第 56 批原始链接列表，每行一个 URL
│   ├── batch_57.urls             # 后续批次链接模板
│   └── meta/                     # 各批次生成后的元数据缓存（标题、时间戳）
│       └── batch_56_meta.json
├── scripts/
│   ├── generate_index.py         # 主入口脚本：读取 URLs 并输出 Markdown 索引
│   ├── fetch_metadata.py         # 并发获取页面标题与状态码的模块
│   ├── link_checker.py           # 链接可达性检测工具，支持多线程扫描
│   └── render_template.py        # Jinja2 模板渲染引擎封装
├── templates/
│   └── index.md.j2               # 输出文档的 Jinja2 模板，含章节占位符
├── tests/
│   ├── test_fetcher.py           # 单元测试：模拟 HTTP 响应解析逻辑
│   ├── test_parser.py            # 测试 HTML 元数据提取函数
│   └── fixtures/                 # 测试用的静态 HTML 样本文件
├── docs/
│   ├── getting-started.md        # 详细入门教程，含故障排除
│   ├── configuration.md          # 每项配置参数的作用域与默认值说明
│   ├── development.md            # 开发环境搭建、代码风格与 PR 流程
│   ├── api-reference.md          # 核心类和函数的 docstring 汇总
│   └── operations.md             # 生产环境部署、监控与数据备份建议
└── output/                       # 生成的 README 文件存放目录（默认忽略）
    └── README_56.md              # 第 56 批索引输出示例
```

## 贡献指南

1. **查阅现有议题**：在提交代码或新增功能前，请先浏览 GitHub Issues 列表，确认是否有相似需求已被讨论或正在实现中。若没有相关议题，请新建一个详细描述您计划变更内容的 Issue。

2. **复刻仓库并创建分支**：将本仓库复刻至您的个人账号下，然后基于 `main` 分支创建以 `feature/` 或 `fix/` 为前缀的新分支。分支命名应简洁反映变更目的，例如 `feature/add-batch-60` 或 `fix/timeout-retry`。

3. **编写或更新测试用例**：所有新增的解析逻辑或网络请求处理函数，均需在 `tests/` 目录下补充对应的单元测试。测试覆盖率不得低于 80%。运行 `pytest tests/` 确保全部测试通过。

4. **更新文档与变更日志**：若修改了用户可见的行为（如配置项、命令行参数或输出格式），必须同步更新 `docs/` 下的相关手册，并在 `CHANGELOG.md` 的未发布版本标题下记录变更条目。

5. **提交拉取请求**：推送分支至您的复刻仓库后，向本仓库的 `main` 分支发起 Pull Request。PR 描述中须引用关联的 Issue 编号，并简要说明测试结果与文档更新情况。至少需要一名维护者审核通过后方可合并。

## 常见问题

**Q：生成的索引文件中，部分链接无法访问，系统会如何处理？**

A：`generate_index.py` 脚本默认不阻断生成流程。当链接请求超时或返回非 2xx 状态码时，脚本会将该条目标记为 `[unreachable]` 并记录至日志文件 `logs/unreachable.log`。您可以在 `config/settings.yaml` 中调整 `timeout` 和 `max_retries` 参数以改善网络条件下的成功率。对于确认失效的链接，建议手动从 `.urls` 文件中移除或替换。

**Q：如何添加新的域名来源？系统是否支持自定义解析规则？**

A：支持。您需要做两件事：第一，在 `config/domains.yaml` 的 `whitelist` 列表中加入新域名；第二，若该域名的 HTML 结构与默认解析规则（基于 `<title>` 和 `<meta name="description">`）不兼容，您可以在 `scripts/fetch_metadata.py` 中注册一个自定义解析器函数，通过 `selectors` 字段指定 CSS 选择器或 XPath 表达式。具体示例请参考 `docs/development.md` 中的"扩展解析器"章节。

**Q：输出文档中的资源列表顺序是否可以自定义？**

A：默认情况下，脚本按照 `data/batch_XX.urls` 文件中的行顺序原样输出。若需按字母序、域名分组或随机排列，您可以在 `config/settings.yaml` 中修改 `sort_mode` 参数，可选值为 `none`、`alpha`、`domain` 和 `random`。重新运行生成脚本即可生效，无需修改原始 URLs 文件。

## 许可证

MIT License

Copyright (c) 2026 LinkSphere Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

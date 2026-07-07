# ReadMaster

ReadMaster 是一个面向技术研究者与内容策展人的外链资源归集与结构化阅读平台。本项目不生产内容，而是通过人工筛选与半自动化采集，将分布于多个子域名下的深度技术文章、行业分析报告与工程实践文档进行统一索引与分类展示。项目定位为技术决策支持型资源导航站，帮助用户从碎片化的信息噪音中快速定位高价值原文。

项目目标用户包括技术团队负责人、架构师、DevOps 工程师以及技术内容运营人员。系统通过静态站点生成方式提供毫秒级页面响应，支持按文章编号、子域名来源、发布时间等维度进行检索与过滤。同时，项目内置了基于正则表达式的死链检测与更新提醒机制，确保资源列表的长期可用性。

## 功能概览

多源异构数据聚合：支持从多个独立子域名并行拉取文章元数据，自动合并为统一资源池。

智能文章编号解析：从 URL 中提取文章 ID 作为唯一标识，支持冲突检测与自动重命名。

增量更新与缓存管理：仅拉取上次同步后新增或修改的文章，降低源站请求压力。

静态页面生成引擎：基于 Jinja2 模板系统生成语义化的 HTML 页面，便于搜索引擎抓取。

全文检索接口：基于 SQLite FTS5 扩展提供轻量级中文分词搜索，支持标题与正文片段匹配。

导出与分享功能：支持将资源列表导出为 CSV、JSON 及纯文本 Markdown 格式。

运行状态监控：内置健康检查端点，实时监控各数据源的可用性与响应延迟。

## 应用场景

技术团队内部知识库建设：团队可将本系统部署在内网，定时同步外部优质技术博客与官方文档链接，形成团队统一的技术阅读清单，替代混乱的浏览器书签共享。

个人技术阅读工作流管理：开发者可利用本项目的标签过滤与搜索功能，维护个人每周技术阅读计划，通过文章编号快速回溯已读内容，结合本地笔记工具形成知识闭环。

技术会议与展览资料归档：在参加技术峰会后，组织者可将会议相关的外部报道、演讲 PPT 链接通过本系统统一录入，生成带编号的资源集合，方便参会者事后查阅。

开源项目文档链接受理：开源社区维护者可使用本项目的资源列表导出功能，将项目 README 中的外部参考链接按本项目的格式规范进行批量整理，确保所有外链格式一致且经过可用性检测。

## 快速开始

以下指令适用于 Linux / macOS 环境，Windows 用户请使用 WSL2 或 Git Bash。

```bash
# 克隆项目仓库
git clone https://github.com/readmaster/readmaster-core.git
cd readmaster-core

# 安装 Python 依赖（建议使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt

# 执行首次数据同步与静态站点生成
python cli.py sync --source-config config/sources.yaml
python cli.py build --output-dir ./public

# 启动本地预览服务
python -m http.server --directory ./public 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9.0 或更高 | 核心运行环境，低于此版本将导致类型提示解析错误 |
| SQLite | 3.35.0 或更高 | 用于存储元数据及全文索引，低版本不支持 FTS5 扩展 |
| pip | 21.0 或更高 | 依赖包管理器，用于安装 requirements.txt 中列出的库 |
| Git | 2.25.0 或更高 | 用于克隆仓库以及后续拉取更新 |
| 磁盘空间 | 至少 200 MB | 用于存放源码、虚拟环境及生成的静态页面文件 |
| 网络访问 | 可访问外网 | 数据同步阶段需访问配置文件中指定的所有子域名源站 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何进行首次同步？如何配置自定义数据源？ |
| 开发者指南 | docs/developer-guide.md | 项目模块划分是怎样的？如何新增一个解析器？ |
| 运维参考 | docs/ops-reference.md | 如何设置定时任务自动更新？如何迁移数据库？ |
| API 接口 | docs/api-endpoints.md | 对外暴露了哪些 REST 接口？调用参数是什么？ |
| 设计决策 | docs/design-decisions.md | 为什么选择 SQLite 而非 MySQL？静态生成策略如何权衡？ |

## 资源列表

- https://www.read.fuvxie.cn/Article/477661.shtml
- https://www.read.nwbbyt.cn/Article/1558.shtml
- https://www.read.puhvjy.cn/Article/1855.shtml
- https://www.read.hcbezg.cn/Article/58986.shtml
- https://www.read.puhvjy.cn/Article/9076.shtml
- https://www.read.puhvjy.cn/Article/967675.shtml
- https://www.read.nzfnve.cn/Article/1010313.shtml
- https://www.read.hcbezg.cn/Article/274531.shtml
- https://www.read.jnjpgf.cn/Article/1199495.shtml
- https://www.read.hcbezg.cn/Article/198822.shtml
- https://www.read.jnjpgf.cn/Article/39298.shtml
- https://www.read.cvsifc.cn/Article/2432891.shtml
- https://www.read.fuvxie.cn/Article/7891091.shtml
- https://www.read.jnjpgf.cn/Article/06817.shtml
- https://www.read.jnjpgf.cn/Article/0144.shtml
- https://www.read.jnjpgf.cn/Article/47599.shtml
- https://www.read.nzfnve.cn/Article/248881.shtml
- https://www.read.jnjpgf.cn/Article/1253.shtml
- https://www.read.cvsifc.cn/Article/9834124.shtml
- https://www.read.hcbezg.cn/Article/0030.shtml
- https://www.read.cvsifc.cn/Article/63410.shtml
- https://www.read.fuvxie.cn/Article/8016.shtml
- https://www.read.cmcvrr.cn/Article/8392063.shtml
- https://www.read.puhvjy.cn/Article/5593.shtml
- https://www.read.jnjpgf.cn/Article/9760.shtml
- https://www.read.hcbezg.cn/Article/77787.shtml
- https://www.read.nzfnve.cn/Article/66943.shtml
- https://www.read.puhvjy.cn/Article/9590560.shtml
- https://www.read.hcbezg.cn/Article/06416.shtml
- https://www.read.nwbbyt.cn/Article/008806.shtml
- https://www.read.cmcvrr.cn/Article/1191.shtml
- https://www.read.jnjpgf.cn/Article/417152.shtml
- https://www.read.cvsifc.cn/Article/76173.shtml
- https://www.read.nwbbyt.cn/Article/2708.shtml
- https://www.read.puhvjy.cn/Article/293413.shtml
- https://www.read.nwbbyt.cn/Article/0707.shtml
- https://www.read.fuvxie.cn/Article/92361.shtml
- https://www.read.fuvxie.cn/Article/264715.shtml
- https://www.read.cmcvrr.cn/Article/5049016.shtml
- https://www.read.jnjpgf.cn/Article/5544.shtml
- https://www.read.nwbbyt.cn/Article/9978.shtml
- https://www.read.cmcvrr.cn/Article/75989.shtml
- https://www.read.puhvjy.cn/Article/5128108.shtml
- https://www.read.cmcvrr.cn/Article/475278.shtml
- https://www.read.nzfnve.cn/Article/01532.shtml
- https://www.read.cvsifc.cn/Article/649579.shtml
- https://www.read.nwbbyt.cn/Article/7085.shtml
- https://www.read.cmcvrr.cn/Article/4918.shtml
- https://www.read.puhvjy.cn/Article/48096.shtml
- https://www.read.puhvjy.cn/Article/221124.shtml
- https://www.read.nwbbyt.cn/Article/8088579.shtml
- https://www.read.puhvjy.cn/Article/02584.shtml
- https://www.read.fuvxie.cn/Article/40151.shtml
- https://www.read.fuvxie.cn/Article/21655.shtml
- https://www.read.nwbbyt.cn/Article/7160.shtml
- https://www.read.hcbezg.cn/Article/2729.shtml
- https://www.read.jnjpgf.cn/Article/81224.shtml
- https://www.read.jnjpgf.cn/Article/6095446.shtml
- https://www.read.jnjpgf.cn/Article/9887652.shtml
- https://www.read.nzfnve.cn/Article/5779693.shtml
- https://www.read.hcbezg.cn/Article/1425.shtml
- https://www.read.fuvxie.cn/Article/4572.shtml
- https://www.read.fuvxie.cn/Article/53694.shtml
- https://www.read.cmcvrr.cn/Article/27701.shtml
- https://www.read.jnjpgf.cn/Article/5636253.shtml
- https://www.read.hcbezg.cn/Article/7977.shtml
- https://www.read.nwbbyt.cn/Article/16700.shtml
- https://www.read.fuvxie.cn/Article/44561.shtml
- https://www.read.hcbezg.cn/Article/69328.shtml
- https://www.read.jnjpgf.cn/Article/66941.shtml
- https://www.read.jnjpgf.cn/Article/36484.shtml
- https://www.read.cvsifc.cn/Article/758373.shtml
- https://www.read.fuvxie.cn/Article/31795.shtml
- https://www.read.fuvxie.cn/Article/655189.shtml
- https://www.read.cvsifc.cn/Article/03617.shtml
- https://www.read.hcbezg.cn/Article/784776.shtml
- https://www.read.cvsifc.cn/Article/222401.shtml
- https://www.read.hcbezg.cn/Article/70819.shtml
- https://www.read.cmcvrr.cn/Article/3096771.shtml
- https://www.read.hcbezg.cn/Article/2781.shtml
- https://www.read.cmcvrr.cn/Article/4434.shtml
- https://www.read.fuvxie.cn/Article/42181.shtml
- https://www.read.jnjpgf.cn/Article/11000.shtml
- https://www.read.jnjpgf.cn/Article/6720186.shtml
- https://www.read.cmcvrr.cn/Article/062539.shtml
- https://www.read.nzfnve.cn/Article/032972.shtml
- https://www.read.jnjpgf.cn/Article/876905.shtml
- https://www.read.cvsifc.cn/Article/55159.shtml
- https://www.read.cvsifc.cn/Article/476585.shtml
- https://www.read.nzfnve.cn/Article/9268.shtml
- https://www.read.cvsifc.cn/Article/618611.shtml
- https://www.read.hcbezg.cn/Article/8424437.shtml
- https://www.read.cmcvrr.cn/Article/0937.shtml
- https://www.read.fuvxie.cn/Article/61312.shtml
- https://www.read.puhvjy.cn/Article/7779247.shtml
- https://www.read.nwbbyt.cn/Article/818113.shtml
- https://www.read.puhvjy.cn/Article/3373437.shtml
- https://www.read.fuvxie.cn/Article/79251.shtml
- https://www.read.puhvjy.cn/Article/0773015.shtml
- https://www.read.fuvxie.cn/Article/35068.shtml
- https://www.read.cmcvrr.cn/Article/9670214.shtml
- https://www.read.fuvxie.cn/Article/5304.shtml
- https://www.read.cmcvrr.cn/Article/49897.shtml
- https://www.read.cvsifc.cn/Article/76793.shtml
- https://www.read.jnjpgf.cn/Article/91789.shtml
- https://www.read.hcbezg.cn/Article/705157.shtml
- https://www.read.nzfnve.cn/Article/8309926.shtml
- https://www.read.nzfnve.cn/Article/019219.shtml
- https://www.read.jnjpgf.cn/Article/48910.shtml
- https://www.read.fuvxie.cn/Article/1107373.shtml
- https://www.read.cvsifc.cn/Article/5821960.shtml
- https://www.read.nwbbyt.cn/Article/113645.shtml
- https://www.read.nwbbyt.cn/Article/9902621.shtml
- https://www.read.cvsifc.cn/Article/8701122.shtml
- https://www.read.puhvjy.cn/Article/3432.shtml
- https://www.read.hcbezg.cn/Article/84246.shtml
- https://www.read.jnjpgf.cn/Article/510541.shtml
- https://www.read.cmcvrr.cn/Article/620361.shtml
- https://www.read.nzfnve.cn/Article/5600360.shtml
- https://www.read.nzfnve.cn/Article/5355473.shtml
- https://www.read.jnjpgf.cn/Article/779446.shtml
- https://www.read.cmcvrr.cn/Article/6069.shtml
- https://www.read.jnjpgf.cn/Article/441217.shtml
- https://www.read.nwbbyt.cn/Article/218805.shtml
- https://www.read.nwbbyt.cn/Article/697990.shtml
- https://www.read.cmcvrr.cn/Article/1984439.shtml
- https://www.read.jnjpgf.cn/Article/0637.shtml
- https://www.read.fuvxie.cn/Article/56277.shtml
- https://www.read.jnjpgf.cn/Article/3936733.shtml
- https://www.read.hcbezg.cn/Article/3041827.shtml
- https://www.read.jnjpgf.cn/Article/57145.shtml
- https://www.read.fuvxie.cn/Article/926292.shtml
- https://www.read.hcbezg.cn/Article/255405.shtml
- https://www.read.puhvjy.cn/Article/7390277.shtml
- https://www.read.nwbbyt.cn/Article/8754.shtml
- https://www.read.fuvxie.cn/Article/0102237.shtml
- https://www.read.fuvxie.cn/Article/9381.shtml
- https://www.read.nwbbyt.cn/Article/9266906.shtml
- https://www.read.hcbezg.cn/Article/61279.shtml
- https://www.read.fuvxie.cn/Article/05444.shtml
- https://www.read.cmcvrr.cn/Article/0202.shtml
- https://www.read.hcbezg.cn/Article/648496.shtml
- https://www.read.fuvxie.cn/Article/8249734.shtml
- https://www.read.fuvxie.cn/Article/961347.shtml
- https://www.read.nwbbyt.cn/Article/990786.shtml
- https://www.read.cvsifc.cn/Article/2995.shtml
- https://www.read.hcbezg.cn/Article/8499.shtml
- https://www.read.hcbezg.cn/Article/819109.shtml
- https://www.read.cvsifc.cn/Article/62531.shtml
- https://www.read.cmcvrr.cn/Article/71815.shtml
- https://www.read.cvsifc.cn/Article/54536.shtml
- https://www.read.jnjpgf.cn/Article/78945.shtml
- https://www.read.nzfnve.cn/Article/7253884.shtml
- https://www.read.puhvjy.cn/Article/227094.shtml
- https://www.read.puhvjy.cn/Article/4393.shtml
- https://www.read.cvsifc.cn/Article/34393.shtml
- https://www.read.nzfnve.cn/Article/901321.shtml
- https://www.read.jnjpgf.cn/Article/732679.shtml
- https://www.read.nwbbyt.cn/Article/14797.shtml
- https://www.read.cmcvrr.cn/Article/6817778.shtml
- https://www.read.nzfnve.cn/Article/812786.shtml
- https://www.read.nwbbyt.cn/Article/64176.shtml
- https://www.read.fuvxie.cn/Article/3707432.shtml
- https://www.read.jnjpgf.cn/Article/3207.shtml
- https://www.read.puhvjy.cn/Article/1903097.shtml
- https://www.read.jnjpgf.cn/Article/3075561.shtml
- https://www.read.fuvxie.cn/Article/7871295.shtml
- https://www.read.nzfnve.cn/Article/4836.shtml
- https://www.read.jnjpgf.cn/Article/910089.shtml
- https://www.read.cmcvrr.cn/Article/38460.shtml
- https://www.read.nzfnve.cn/Article/3265346.shtml
- https://www.read.puhvjy.cn/Article/1507130.shtml
- https://www.read.puhvjy.cn/Article/5411626.shtml
- https://www.read.puhvjy.cn/Article/1063.shtml
- https://www.read.nzfnve.cn/Article/7890.shtml
- https://www.read.cmcvrr.cn/Article/792087.shtml
- https://www.read.cmcvrr.cn/Article/90154.shtml
- https://www.read.jnjpgf.cn/Article/1650.shtml
- https://www.read.nwbbyt.cn/Article/422806.shtml
- https://www.read.puhvjy.cn/Article/3165.shtml
- https://www.read.fuvxie.cn/Article/449080.shtml
- https://www.read.hcbezg.cn/Article/6926.shtml
- https://www.read.jnjpgf.cn/Article/730814.shtml
- https://www.read.cmcvrr.cn/Article/9503.shtml
- https://www.read.puhvjy.cn/Article/9810.shtml
- https://www.read.hcbezg.cn/Article/836165.shtml
- https://www.read.nwbbyt.cn/Article/312427.shtml
- https://www.read.cmcvrr.cn/Article/52101.shtml
- https://www.read.fuvxie.cn/Article/9730.shtml
- https://www.read.cvsifc.cn/Article/84711.shtml
- https://www.read.cmcvrr.cn/Article/2118.shtml
- https://www.read.jnjpgf.cn/Article/2194862.shtml
- https://www.read.cmcvrr.cn/Article/480319.shtml
- https://www.read.jnjpgf.cn/Article/9007.shtml
- https://www.read.cmcvrr.cn/Article/8013.shtml
- https://www.read.nzfnve.cn/Article/04615.shtml
- https://www.read.puhvjy.cn/Article/008238.shtml
- https://www.read.fuvxie.cn/Article/312503.shtml
- https://www.read.cvsifc.cn/Article/2022.shtml
- https://www.read.nwbbyt.cn/Article/240115.shtml
- https://www.read.cmcvrr.cn/Article/7708039.shtml
- https://www.read.nwbbyt.cn/Article/18239.shtml
- https://www.read.fuvxie.cn/Article/666441.shtml
- https://www.read.hcbezg.cn/Article/360766.shtml
- https://www.read.nwbbyt.cn/Article/5414.shtml
- https://www.read.jnjpgf.cn/Article/7873.shtml
- https://www.read.puhvjy.cn/Article/7585.shtml
- https://www.read.nwbbyt.cn/Article/619460.shtml
- https://www.read.puhvjy.cn/Article/758981.shtml
- https://www.read.nwbbyt.cn/Article/6377.shtml
- https://www.read.nzfnve.cn/Article/402948.shtml
- https://www.read.cmcvrr.cn/Article/8873.shtml
- https://www.read.jnjpgf.cn/Article/8256.shtml
- https://www.read.cmcvrr.cn/Article/5986442.shtml
- https://www.read.hcbezg.cn/Article/2228943.shtml
- https://www.read.nwbbyt.cn/Article/542930.shtml
- https://www.read.jnjpgf.cn/Article/92938.shtml
- https://www.read.hcbezg.cn/Article/4252109.shtml
- https://www.read.nzfnve.cn/Article/727826.shtml
- https://www.read.nwbbyt.cn/Article/17275.shtml
- https://www.read.nzfnve.cn/Article/156178.shtml
- https://www.read.nwbbyt.cn/Article/525686.shtml
- https://www.read.hcbezg.cn/Article/3376829.shtml
- https://www.read.puhvjy.cn/Article/45577.shtml
- https://www.read.nwbbyt.cn/Article/730547.shtml
- https://www.read.cvsifc.cn/Article/542599.shtml
- https://www.read.jnjpgf.cn/Article/8671.shtml
- https://www.read.puhvjy.cn/Article/8380017.shtml
- https://www.read.nzfnve.cn/Article/873550.shtml
- https://www.read.hcbezg.cn/Article/1164.shtml
- https://www.read.hcbezg.cn/Article/2466.shtml
- https://www.read.puhvjy.cn/Article/114526.shtml
- https://www.read.cvsifc.cn/Article/6869740.shtml
- https://www.read.jnjpgf.cn/Article/37145.shtml
- https://www.read.cmcvrr.cn/Article/2142533.shtml
- https://www.read.nzfnve.cn/Article/6762656.shtml
- https://www.read.fuvxie.cn/Article/59478.shtml
- https://www.read.hcbezg.cn/Article/7562.shtml
- https://www.read.cmcvrr.cn/Article/899077.shtml
- https://www.read.puhvjy.cn/Article/76903.shtml
- https://www.read.nzfnve.cn/Article/4725249.shtml
- https://www.read.cmcvrr.cn/Article/8482.shtml
- https://www.read.jnjpgf.cn/Article/583292.shtml
- https://www.read.puhvjy.cn/Article/4541.shtml
- https://www.read.hcbezg.cn/Article/22508.shtml
- https://www.read.cvsifc.cn/Article/352860.shtml
- https://www.read.cmcvrr.cn/Article/341087.shtml
- https://www.read.fuvxie.cn/Article/078046.shtml
- https://www.read.hcbezg.cn/Article/61956.shtml
- https://www.read.nwbbyt.cn/Article/161541.shtml

## 项目结构

```
readmaster-core/
├── cli.py                  # 命令行入口，解析 sync/build/export 子命令
├── config/
│   ├── sources.yaml        # 数据源配置文件，定义所有子域名及抓取规则
│   └── logging.conf        # 日志轮转与输出级别配置
├── core/
│   ├── fetcher.py          # 异步 HTTP 请求与重试逻辑，含超时与限速
│   ├── parser.py           # HTML 元数据提取与文章编号正则匹配
│   ├── indexer.py          # SQLite 表结构创建与 FTS5 虚拟表管理
│   └── generator.py        # 模板渲染与静态页面输出流控制
├── templates/
│   ├── base.html           # 基础布局模板，含导航与页脚
│   ├── index.html          # 资源总览页，分页显示文章列表
│   └── detail.html         # 单篇文章详情页，显示完整元数据
├── tests/
│   ├── test_fetcher.py     # 模拟 HTTP 响应的单元测试
│   ├── test_parser.py      # 正则表达式覆盖测试
│   └── fixtures/           # 测试用的静态 HTML 样本文件
├── scripts/
│   ├── cron_sync.sh        # 每日定时同步的 shell 脚本
│   └── export_json.py      # 独立导出工具，生成 JSON 格式资源清单
├── docs/                   # 完整文档目录，含用户手册与 API 文档
├── requirements.txt        # 第三方依赖清单（requests, jinja2, markdown 等）
├── README.md               # 本文件
└── LICENSE                 # MIT 许可证文本
```

## 贡献指南

欢迎各类形式的贡献，包括但不限于新增数据源适配器、优化页面模板、完善测试用例或补充文档。

1. 从 GitHub 仓库派生本项目至个人账户，在本地克隆派生的仓库，并基于 develop 分支创建新的功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式。

2. 进行代码或文档修改时，请确保新增代码包含必要的类型注解与文档字符串，并补充对应的单元测试。对于模板修改，请确认在主流浏览器中渲染效果一致。

3. 提交前运行完整的测试套件 `pytest tests/` 并确保所有测试通过，同时使用 `flake8` 与 `black` 进行代码风格检查与格式化。

4. 推送分支至个人远程仓库，在 GitHub 上向本项目的 develop 分支发起 Pull Request，PR 描述中请清晰说明变更动机、实现方式及测试结果摘要。

5. 项目维护者将在两个工作日内进行 Code Review，可能要求修改或补充测试，合并后您的贡献将列入项目贡献者列表。

## 常见问题

**问：同步过程中部分数据源返回 403 或 429 状态码，如何处理？**

答：这可能是因为源站启用了反爬机制或限流策略。项目提供了两种应对方式：一是修改 `config/sources.yaml` 中对应源头的 `request_interval` 参数，增大请求间隔至 2 秒以上；二是配置 `headers` 字段，添加常见的 User-Agent 与 Referer 头。若问题持续，建议暂时注释该源头，并联系源站管理员确认访问策略。

**问：生成的静态页面中文章标题显示为乱码，如何解决？**

答：这通常是因为源站返回的字符编码与项目默认的 UTF-8 不一致。请在 `core/parser.py` 中为对应源头指定 `encoding` 参数，例如 `encoding='gbk'` 或 `encoding='gb18030'`。同时确保模板文件本身保存为 UTF-8 无 BOM 格式。

**问：如何迁移现有数据库到另一台服务器？**

答：项目默认将 SQLite 数据库文件存放于 `./data/resources.db`。迁移时只需复制该文件至目标服务器的相同相对路径下，并确保目标服务器安装了相同版本的 SQLite。若需要更改存储路径，可在 `config/sources.yaml` 中设置 `database_path` 字段为绝对路径。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

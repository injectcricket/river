# DocLink 聚合归档系统

DocLink 聚合归档系统是一个面向技术文档、行业报告与学术资料的长效外链管理工具。项目定位为技术资源汇总站，帮助开发者、研究人员、内容运营团队将散落在多个移动端 H5 站点的 .doc 资料链接统一收录、分类标注与状态监控，避免链接失效或资源散落导致的信息流失。

目标用户包括需要长期维护技术知识库的团队、定期采集行业动态文档的分析人员，以及希望将零散外链资产化的内容管理者。系统通过轻量级脚本与静态数据格式，即可完成对批量文档链接的导入、标签化整理与可用性巡检，无需依赖复杂后端服务。

## 功能概览

批量链接导入：支持从文本文件或标准输入中一次性导入大量文档链接，自动解析域名与路径结构。

域名分组索引：按一级域名自动归类链接，便于按来源站点筛选与统计资源分布。

文档元数据提取：从链接中解析文件名、目录层级，并支持手动补充标题与描述信息。

可用性健康检查：定时发起 HEAD 请求检测文档资源是否可访问，标注异常状态并生成报告。

标签与备注系统：每条链接可绑定多个自定义标签，支持按标签快速筛选与导出。

静态站点生成：将链接数据渲染为静态 HTML 页面，可直接部署为内部知识门户或团队书签站。

导出与迁移工具：支持将链接列表导出为 CSV、JSON 与 Markdown 表格格式，便于导入其他系统。

## 应用场景

技术团队内部知识库建设：团队在多个 H5 技术博客或文档站中积累了大量操作手册与设计文档，使用 DocLink 可将这些分散的 .doc 链接统一归档，并标记所属项目模块，方便新人快速检索历史资料。

行业报告定期采集分析：市场分析人员每周从不同行业站点收集数十份 PDF 与 DOC 格式的报告，通过本系统批量导入链接后，可设置每周定时检查链接有效性，及时发现被移除或变更的文档，确保报告来源持续可用。

文档迁移前的资源盘点：企业在将文档系统从旧平台迁移至新平台前，需对现存所有外链进行梳理。DocLink 可一次性导入所有旧系统中的文档链接，生成包含域名、路径、状态等信息的完整清单，为迁移决策提供数据基础。

开源项目文档镜像索引：开源社区维护者可将分散在多个镜像站或历史存档站点的文档链接整理至 DocLink，生成统一的文档导航页，降低社区用户查找资料的难度。

## 快速开始

以下命令可在 Linux 与 macOS 环境下完成工具的克隆、安装与运行。

```bash
git clone https://github.com/doclink-archive/doclink-aggregator.git
cd doclink-aggregator
pip install -r requirements.txt
python cli.py import --input links.txt --output archive.json
python cli.py check --file archive.json --timeout 5
python cli.py serve --file archive.json --port 8080
```

其中 links.txt 为存放文档链接的文本文件，每行一个 URL。运行 serve 命令后，可通过浏览器访问本地 8080 端口查看归档页面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，用于执行 CLI 工具与调度任务 |
| pip | 22.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| requests | 2.31.0 及以上 | 发送 HTTP 请求以检测链接可用性 |
| jinja2 | 3.1.0 及以上 | 渲染静态 HTML 页面模板 |
| click | 8.1.0 及以上 | 提供命令行交互解析能力 |
| pytest | 7.4.0 及以上 | 单元测试与集成测试框架（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速导入第一批链接并生成可视化页面 |
| 命令参考 | docs/cli-commands.md | 每条 CLI 命令的具体参数与用法示例 |
| 数据格式 | docs/data-format.md | 归档 JSON 文件的字段结构与扩展约定 |
| 部署手册 | docs/deployment.md | 如何将系统部署为长期运行的后台服务或定时任务 |
| 故障排查 | docs/troubleshooting.md | 常见报错信息的原因与解决办法 |

## 资源列表

- h5.mobile.nwbbyt.cn/Article/3350.doc
- h5.mobile.cmcvrr.cn/Article/154356.doc
- h5.mobile.nwbbyt.cn/Article/692770.doc
- h5.mobile.puhvjy.cn/Article/5935371.doc
- h5.mobile.jnjpgf.cn/Article/60106.doc
- h5.mobile.hcbezg.cn/Article/5665.doc
- h5.mobile.jnjpgf.cn/Article/912936.doc
- h5.mobile.cvsifc.cn/Article/5970813.doc
- h5.mobile.cvsifc.cn/Article/4695.doc
- h5.mobile.nwbbyt.cn/Article/8937.doc
- h5.mobile.hcbezg.cn/Article/2548.doc
- h5.mobile.cmcvrr.cn/Article/762272.doc
- h5.mobile.puhvjy.cn/Article/904642.doc
- h5.mobile.hcbezg.cn/Article/8758.doc
- h5.mobile.fuvxie.cn/Article/3860.doc
- h5.mobile.fuvxie.cn/Article/46336.doc
- h5.mobile.jnjpgf.cn/Article/39655.doc
- h5.mobile.fuvxie.cn/Article/49903.doc
- h5.mobile.cvsifc.cn/Article/7221.doc
- h5.mobile.fuvxie.cn/Article/54126.doc
- h5.mobile.hcbezg.cn/Article/18774.doc
- h5.mobile.cmcvrr.cn/Article/43947.doc
- h5.mobile.cvsifc.cn/Article/1817354.doc
- h5.mobile.puhvjy.cn/Article/641631.doc
- h5.mobile.hcbezg.cn/Article/964907.doc
- h5.mobile.puhvjy.cn/Article/7696.doc
- h5.mobile.nwbbyt.cn/Article/673173.doc
- h5.mobile.fuvxie.cn/Article/151037.doc
- h5.mobile.fuvxie.cn/Article/753001.doc
- h5.mobile.jnjpgf.cn/Article/9208549.doc
- h5.mobile.jnjpgf.cn/Article/59489.doc
- h5.mobile.fuvxie.cn/Article/5562.doc
- h5.mobile.nzfnve.cn/Article/31627.doc
- h5.mobile.nwbbyt.cn/Article/2959507.doc
- h5.mobile.cvsifc.cn/Article/061878.doc
- h5.mobile.puhvjy.cn/Article/9120.doc
- h5.mobile.nwbbyt.cn/Article/988263.doc
- h5.mobile.jnjpgf.cn/Article/8159306.doc
- h5.mobile.cvsifc.cn/Article/989775.doc
- h5.mobile.nwbbyt.cn/Article/2970871.doc
- h5.mobile.nzfnve.cn/Article/8650.doc
- h5.mobile.puhvjy.cn/Article/044147.doc
- h5.mobile.puhvjy.cn/Article/37847.doc
- h5.mobile.cvsifc.cn/Article/870401.doc
- h5.mobile.jnjpgf.cn/Article/4088.doc
- h5.mobile.jnjpgf.cn/Article/4550618.doc
- h5.mobile.jnjpgf.cn/Article/0253.doc
- h5.mobile.puhvjy.cn/Article/32059.doc
- h5.mobile.hcbezg.cn/Article/98899.doc
- h5.mobile.fuvxie.cn/Article/2466590.doc
- h5.mobile.hcbezg.cn/Article/702075.doc
- h5.mobile.cmcvrr.cn/Article/6365.doc
- h5.mobile.nwbbyt.cn/Article/756078.doc
- h5.mobile.fuvxie.cn/Article/6813993.doc
- h5.mobile.fuvxie.cn/Article/56256.doc
- h5.mobile.jnjpgf.cn/Article/776636.doc
- h5.mobile.cmcvrr.cn/Article/75912.doc
- h5.mobile.puhvjy.cn/Article/226636.doc
- h5.mobile.nzfnve.cn/Article/583848.doc
- h5.mobile.hcbezg.cn/Article/957570.doc
- h5.mobile.cvsifc.cn/Article/8941.doc
- h5.mobile.jnjpgf.cn/Article/1892978.doc
- h5.mobile.fuvxie.cn/Article/532038.doc
- h5.mobile.nzfnve.cn/Article/59769.doc
- h5.mobile.jnjpgf.cn/Article/51017.doc
- h5.mobile.hcbezg.cn/Article/5037662.doc
- h5.mobile.nwbbyt.cn/Article/885103.doc
- h5.mobile.jnjpgf.cn/Article/933668.doc
- h5.mobile.hcbezg.cn/Article/2406.doc
- h5.mobile.cvsifc.cn/Article/2317.doc
- h5.mobile.cmcvrr.cn/Article/5633.doc
- h5.mobile.jnjpgf.cn/Article/287765.doc
- h5.mobile.nwbbyt.cn/Article/989488.doc
- h5.mobile.hcbezg.cn/Article/27408.doc
- h5.mobile.nwbbyt.cn/Article/13271.doc
- h5.mobile.fuvxie.cn/Article/2984.doc
- h5.mobile.cvsifc.cn/Article/7200.doc
- h5.mobile.jnjpgf.cn/Article/980196.doc
- h5.mobile.nzfnve.cn/Article/6421421.doc
- h5.mobile.puhvjy.cn/Article/8637788.doc
- h5.mobile.fuvxie.cn/Article/5461339.doc
- h5.mobile.nzfnve.cn/Article/433406.doc
- h5.mobile.nzfnve.cn/Article/92778.doc
- h5.mobile.hcbezg.cn/Article/6148.doc
- h5.mobile.nwbbyt.cn/Article/8895.doc
- h5.mobile.cvsifc.cn/Article/9680.doc
- h5.mobile.nwbbyt.cn/Article/9560076.doc
- h5.mobile.nwbbyt.cn/Article/546113.doc
- h5.mobile.nzfnve.cn/Article/63574.doc
- h5.mobile.cmcvrr.cn/Article/2670.doc
- h5.mobile.jnjpgf.cn/Article/1413893.doc
- h5.mobile.cmcvrr.cn/Article/89067.doc
- h5.mobile.jnjpgf.cn/Article/679494.doc
- h5.mobile.jnjpgf.cn/Article/0248766.doc
- h5.mobile.hcbezg.cn/Article/2363.doc
- h5.mobile.jnjpgf.cn/Article/409069.doc
- h5.mobile.cmcvrr.cn/Article/933597.doc
- h5.mobile.nwbbyt.cn/Article/78570.doc
- h5.mobile.jnjpgf.cn/Article/560018.doc
- h5.mobile.nwbbyt.cn/Article/61307.doc
- h5.mobile.hcbezg.cn/Article/67111.doc
- h5.mobile.jnjpgf.cn/Article/54594.doc
- h5.mobile.cmcvrr.cn/Article/1684510.doc
- h5.mobile.puhvjy.cn/Article/1076.doc
- h5.mobile.hcbezg.cn/Article/20502.doc
- h5.mobile.nwbbyt.cn/Article/3662.doc
- h5.mobile.hcbezg.cn/Article/9168392.doc
- h5.mobile.fuvxie.cn/Article/026531.doc
- h5.mobile.fuvxie.cn/Article/34384.doc
- h5.mobile.hcbezg.cn/Article/237293.doc
- h5.mobile.nwbbyt.cn/Article/40818.doc
- h5.mobile.fuvxie.cn/Article/7301577.doc
- h5.mobile.nzfnve.cn/Article/75701.doc
- h5.mobile.hcbezg.cn/Article/497317.doc
- h5.mobile.cvsifc.cn/Article/7166.doc
- h5.mobile.nzfnve.cn/Article/98452.doc
- h5.mobile.cmcvrr.cn/Article/1540884.doc
- h5.mobile.nzfnve.cn/Article/3639141.doc
- h5.mobile.cvsifc.cn/Article/45319.doc
- h5.mobile.cvsifc.cn/Article/2505300.doc
- h5.mobile.hcbezg.cn/Article/48567.doc
- h5.mobile.cvsifc.cn/Article/0192.doc
- h5.mobile.nwbbyt.cn/Article/83023.doc
- h5.mobile.nwbbyt.cn/Article/7515505.doc
- h5.mobile.cvsifc.cn/Article/4372461.doc
- h5.mobile.nzfnve.cn/Article/8224691.doc
- h5.mobile.nzfnve.cn/Article/5515222.doc
- h5.mobile.cmcvrr.cn/Article/515441.doc
- h5.mobile.nzfnve.cn/Article/040823.doc
- h5.mobile.fuvxie.cn/Article/0610156.doc
- h5.mobile.nzfnve.cn/Article/82586.doc
- h5.mobile.cmcvrr.cn/Article/87218.doc
- h5.mobile.jnjpgf.cn/Article/2519.doc
- h5.mobile.puhvjy.cn/Article/8370.doc
- h5.mobile.cmcvrr.cn/Article/0012750.doc
- h5.mobile.fuvxie.cn/Article/075396.doc
- h5.mobile.hcbezg.cn/Article/9116985.doc
- h5.mobile.cvsifc.cn/Article/1107391.doc
- h5.mobile.jnjpgf.cn/Article/4882213.doc
- h5.mobile.cvsifc.cn/Article/23539.doc
- h5.mobile.jnjpgf.cn/Article/81028.doc
- h5.mobile.cvsifc.cn/Article/6813205.doc
- h5.mobile.cvsifc.cn/Article/2562348.doc
- h5.mobile.cvsifc.cn/Article/5078.doc
- h5.mobile.fuvxie.cn/Article/307849.doc
- h5.mobile.fuvxie.cn/Article/0403054.doc
- h5.mobile.fuvxie.cn/Article/6221932.doc
- h5.mobile.fuvxie.cn/Article/2399772.doc
- h5.mobile.jnjpgf.cn/Article/44420.doc
- h5.mobile.cmcvrr.cn/Article/7408223.doc
- h5.mobile.nwbbyt.cn/Article/667120.doc
- h5.mobile.hcbezg.cn/Article/11454.doc
- h5.mobile.cvsifc.cn/Article/7798964.doc
- h5.mobile.hcbezg.cn/Article/5005.doc
- h5.mobile.hcbezg.cn/Article/2447.doc
- h5.mobile.cmcvrr.cn/Article/94271.doc
- h5.mobile.cmcvrr.cn/Article/3267250.doc
- h5.mobile.cmcvrr.cn/Article/034906.doc
- h5.mobile.jnjpgf.cn/Article/7296.doc
- h5.mobile.hcbezg.cn/Article/4381604.doc
- h5.mobile.cvsifc.cn/Article/699859.doc
- h5.mobile.hcbezg.cn/Article/818062.doc
- h5.mobile.puhvjy.cn/Article/581158.doc
- h5.mobile.nzfnve.cn/Article/6717.doc
- h5.mobile.nwbbyt.cn/Article/6038766.doc
- h5.mobile.cmcvrr.cn/Article/98418.doc
- h5.mobile.nzfnve.cn/Article/45724.doc
- h5.mobile.fuvxie.cn/Article/0003.doc
- h5.mobile.nwbbyt.cn/Article/1729.doc
- h5.mobile.nzfnve.cn/Article/540763.doc
- h5.mobile.fuvxie.cn/Article/5232260.doc
- h5.mobile.nzfnve.cn/Article/332368.doc
- h5.mobile.puhvjy.cn/Article/4015731.doc
- h5.mobile.hcbezg.cn/Article/053148.doc
- h5.mobile.puhvjy.cn/Article/0422.doc
- h5.mobile.puhvjy.cn/Article/137468.doc
- h5.mobile.jnjpgf.cn/Article/054594.doc
- h5.mobile.fuvxie.cn/Article/9536.doc
- h5.mobile.hcbezg.cn/Article/0178916.doc
- h5.mobile.puhvjy.cn/Article/0186.doc
- h5.mobile.jnjpgf.cn/Article/01208.doc
- h5.mobile.nzfnve.cn/Article/410942.doc
- h5.mobile.nzfnve.cn/Article/08688.doc
- h5.mobile.cmcvrr.cn/Article/5806.doc
- h5.mobile.hcbezg.cn/Article/35013.doc
- h5.mobile.nwbbyt.cn/Article/69609.doc
- h5.mobile.nwbbyt.cn/Article/53581.doc
- h5.mobile.jnjpgf.cn/Article/379676.doc
- h5.mobile.cmcvrr.cn/Article/32871.doc
- h5.mobile.cvsifc.cn/Article/273160.doc
- h5.mobile.jnjpgf.cn/Article/51813.doc
- h5.mobile.puhvjy.cn/Article/570130.doc
- h5.mobile.fuvxie.cn/Article/534262.doc
- h5.mobile.fuvxie.cn/Article/846334.doc
- h5.mobile.cmcvrr.cn/Article/818209.doc
- h5.mobile.puhvjy.cn/Article/45935.doc
- h5.mobile.fuvxie.cn/Article/8573.doc
- h5.mobile.fuvxie.cn/Article/2657199.doc
- h5.mobile.jnjpgf.cn/Article/561979.doc
- h5.mobile.puhvjy.cn/Article/84212.doc
- h5.mobile.nzfnve.cn/Article/27965.doc
- h5.mobile.cvsifc.cn/Article/3602808.doc
- h5.mobile.nzfnve.cn/Article/48584.doc
- h5.mobile.cvsifc.cn/Article/9826005.doc
- h5.mobile.hcbezg.cn/Article/5359.doc
- h5.mobile.cmcvrr.cn/Article/7261559.doc
- h5.mobile.cvsifc.cn/Article/24572.doc
- h5.mobile.cvsifc.cn/Article/1540774.doc
- h5.mobile.cmcvrr.cn/Article/76080.doc
- h5.mobile.hcbezg.cn/Article/9210.doc
- h5.mobile.nzfnve.cn/Article/1826019.doc
- h5.mobile.cvsifc.cn/Article/3456.doc
- h5.mobile.jnjpgf.cn/Article/522645.doc
- h5.mobile.hcbezg.cn/Article/4836.doc
- h5.mobile.cmcvrr.cn/Article/415498.doc
- h5.mobile.cmcvrr.cn/Article/513436.doc
- h5.mobile.puhvjy.cn/Article/4873.doc
- h5.mobile.puhvjy.cn/Article/6956479.doc
- h5.mobile.hcbezg.cn/Article/12983.doc
- h5.mobile.jnjpgf.cn/Article/74401.doc
- h5.mobile.jnjpgf.cn/Article/0489362.doc
- h5.mobile.nzfnve.cn/Article/345366.doc
- h5.mobile.jnjpgf.cn/Article/400665.doc
- h5.mobile.cvsifc.cn/Article/7127.doc
- h5.mobile.hcbezg.cn/Article/6162871.doc
- h5.mobile.fuvxie.cn/Article/995497.doc
- h5.mobile.puhvjy.cn/Article/07185.doc
- h5.mobile.nzfnve.cn/Article/2165695.doc
- h5.mobile.fuvxie.cn/Article/78250.doc
- h5.mobile.nzfnve.cn/Article/48281.doc
- h5.mobile.nzfnve.cn/Article/3034.doc
- h5.mobile.hcbezg.cn/Article/924918.doc
- h5.mobile.nzfnve.cn/Article/8892394.doc
- h5.mobile.fuvxie.cn/Article/2836755.doc
- h5.mobile.nzfnve.cn/Article/98623.doc
- h5.mobile.cmcvrr.cn/Article/9143.doc
- h5.mobile.cvsifc.cn/Article/30606.doc
- h5.mobile.cvsifc.cn/Article/6090279.doc
- h5.mobile.hcbezg.cn/Article/72432.doc
- h5.mobile.jnjpgf.cn/Article/9604.doc
- h5.mobile.cmcvrr.cn/Article/46163.doc
- h5.mobile.nzfnve.cn/Article/48791.doc
- h5.mobile.jnjpgf.cn/Article/8202012.doc
- h5.mobile.nwbbyt.cn/Article/794551.doc
- h5.mobile.puhvjy.cn/Article/3428.doc
- h5.mobile.hcbezg.cn/Article/3431089.doc
- h5.mobile.jnjpgf.cn/Article/444504.doc
- h5.mobile.nzfnve.cn/Article/432799.doc
- h5.mobile.nzfnve.cn/Article/4939.doc
- h5.mobile.nzfnve.cn/Article/837489.doc

## 项目结构

```
doclink-aggregator/
├── cli.py                      # 命令行入口，注册所有子命令
├── requirements.txt            # Python 依赖声明
├── setup.py                    # 包安装配置
├── README.md                   # 项目说明文档
├── .gitignore                  # 版本控制忽略文件
├── archive/                    # 归档数据存储目录
│   ├── sample.json             # 示例归档文件
│   └── imports/                # 按日期存放的历史导入批次
│       └── 2026-07-07.json
├── core/                       # 核心逻辑模块
│   ├── __init__.py
│   ├── importer.py             # 链接导入与解析器
│   ├── checker.py              # 可用性检测器
│   ├── tagger.py               # 标签管理模块
│   └── exporter.py             # 导出为 CSV/JSON/HTML
├── web/                        # 静态页面生成与模板
│   ├── templates/              # Jinja2 模板文件
│   │   ├── index.html.j2       # 总览页面模板
│   │   ├── detail.html.j2      # 单条链接详情模板
│   │   └── report.html.j2      # 健康检查报告模板
│   └── static/                 # 构建后生成的静态资源
│       └── css/
│           └── style.css
├── tests/                      # 单元测试与测试夹具
│   ├── test_importer.py
│   ├── test_checker.py
│   └── fixtures/
│       └── links_sample.txt
├── scripts/                    # 运维与辅助脚本
│   ├── daily_check.sh          # 每日健康检查定时任务脚本
│   └── batch_import.sh         # 批量导入包装脚本
└── docs/                       # 详细文档目录
    ├── getting-started.md
    ├── cli-commands.md
    ├── data-format.md
    ├── deployment.md
    └── troubleshooting.md
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并将克隆到本地开发环境。请确保使用 Python 3.9 及以上版本，并安装所有开发依赖。
2. 新建功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式。提交代码前请运行 `pytest tests/` 确保所有现有测试通过，并为新增功能补充对应的单元测试。
3. 若新增命令行参数或修改数据输出格式，请同步更新 `docs/cli-commands.md` 与 `docs/data-format.md` 文档，保持文档与代码行为一致。
4. 提交 Pull Request 时，请清晰描述改动目的、实现方式以及测试覆盖情况。若改动涉及链接导入、检测或导出等核心流程，需在 PR 描述中附上手动测试的步骤与结果截图。
5. 所有代码需遵循 PEP 8 编码规范，并确保无未使用的导入或变量。维护者将在 Code Review 中检查代码风格与逻辑正确性，通过后即可合并。

## 常见问题

Q: 批量导入链接时，是否支持非 .doc 扩展名的资源地址？
A: 支持。系统默认不限制文件扩展名，仅依据 URL 路径进行解析。若需要仅导入特定类型文件，可在导入时通过 `--ext` 参数指定过滤后缀，例如 `--ext .doc,.pdf`。未指定时则导入全部链接。

Q: 健康检查将链接标记为异常后，系统会自动重试吗？
A: 系统默认进行单次检查，不会自动重试。但可通过 `check` 命令的 `--retry` 参数设置重试次数，例如 `--retry 3` 将在首次失败后间隔 2 秒再次尝试，最多重试 3 次。所有检查结果均记录在归档文件中，包含状态码与响应时间字段。

Q: 如何将归档数据迁移到另一台服务器上继续使用？
A: 只需将 `archive/` 目录下的所有 JSON 文件及配置文件一同复制到新服务器的相同相对路径下，并确保 Python 环境与依赖版本一致。运行 `cli.py` 时使用 `--file` 参数指定已有的 JSON 文件路径即可继续操作，无需额外迁移步骤。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

# LinkVault Core

LinkVault Core 是一个面向技术团队与内容运营者的外链资产整理工具，用于对大规模分散 URL 进行结构化采集、分类标注与健康度监控。项目本身不生产内容，而是为内容链接提供统一的索引层、访问状态追踪与自定义元数据扩展能力。目标用户包括技术文档维护者、社区运营人员以及需要长期维护外部参考链路的开发者。

项目以“零侵入、可审计、轻量化”为设计原则：不对原始资源做任何内容快照，不修改 URL 本身，只围绕链接构建可检索的附属信息库。通过本地化 CLI 与简单的 JSON 存储，LinkVault Core 可在数分钟内完成对数千条链接的初始录入，并支持后续批量更新、筛选导出与访问可用性巡检。

## 功能概览

批量导入解析 支持从纯文本文件、CSV 或标准输入流中批量读取 URL，自动完成协议归一化与去重校验，生成初始资产清单。

自定义标签体系 允许用户为每条链接附加最多 16 个自定义标签，支持按项目、主题、语种、状态等维度建立多级分类视图。

访问可用性巡检 集成异步 HTTP HEAD 请求检测，可配置超时与重试策略，定期输出链接状态报表，标记异常或失效资源。

结构化查询过滤器 提供基于标签组合、域名前缀、路径关键词的复合筛选能力，支持将查询结果导出为 Markdown 表格或 JSON 格式。

本地存储与版本记录 所有链接元数据以 JSONL 格式存储于项目目录，每次更新自动生成差异日志，便于回溯变更历史。

扩展钩子机制 允许用户编写简单 Shell 或 Python 脚本，在导入、巡检、导出三个阶段注入自定义处理逻辑。

镜像源映射 支持为同一个原始 URL 配置多个备用访问地址，在主链路不可用时提供降级参考。

## 应用场景

技术文档外部参考归档 技术团队在编写系统设计文档或 API 说明时，常引用大量外部博客、规范草案与开源项目主页。LinkVault Core 可用于统一收录这些引用链接，并在文档发布前执行一次可用性检查，避免正式文档中出现死链。

社区资源周报自动生成 开源社区运营人员每周需要整理社区内产生的优质讨论帖、教程视频或 PR 合并记录。通过标签过滤与时间范围组合，可快速生成当周资源列表，并输出为标准化 Markdown 表格直接粘贴至周报。

多项目依赖链路审计 中大型软件工程往往依赖多个外部服务面板、监控看板与私有包仓库地址。使用 LinkVault Core 建立统一的依赖外链索引，配合巡检功能可及时发现因域名过期或证书变更导致的访问异常。

内容聚合站外链维护 内容聚合类网站需要定期检查其聚合来源的可用性与内容更新情况。LinkVault Core 的批量巡检与标签筛选能力可帮助运营者快速定位长期未响应的来源域名，辅助决策是否将其移出聚合队列。

## 快速开始

以下命令演示了从克隆仓库到完成首次链接导入并执行巡检的完整流程。

```bash
git clone https://github.com/linkvault/core.git
cd core
pip install -r requirements.txt
cp config.example.yaml config.yaml
./linkvault import --input raw_links.txt --tag initial
./linkvault check --tag initial --timeout 5 --retry 2
./linkvault export --status alive --format markdown > report.md
```

其中 `raw_links.txt` 为用户自行准备的链接列表文件，每行一个 URL。首次导入后，项目会在 `data/` 目录下生成对应的 JSONL 存储文件与 `logs/` 目录下的操作日志。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行时环境，建议使用 pyenv 管理 |
| pip | 21.0 及以上 | Python 包依赖管理工具 |
| aiohttp | 3.8.0 及以上 | 用于异步并发巡检请求 |
| pyyaml | 6.0 | 配置文件解析与序列化 |
| click | 8.1.0 及以上 | CLI 命令行交互框架 |
| pytest | 7.0 及以上 | 单元测试与集成测试（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何配置首个项目、理解核心数据模型与目录结构 |
| 命令参考 | docs/commands.md | 每个 CLI 子命令的完整参数列表与使用示例 |
| 巡检策略 | docs/check-policy.md | 如何调整超时、并发数、重试逻辑与状态判定规则 |
| 扩展开发 | docs/extend.md | 钩子脚本的编写规范、环境变量注入与调试方法 |

## 资源列表

- https://www.read.nzfnve.cn/Article/7880.shtml
- https://www.read.puhvjy.cn/Article/7157.shtml
- https://www.read.nzfnve.cn/Article/843612.shtml
- https://www.read.puhvjy.cn/Article/49854.shtml
- https://www.read.nzfnve.cn/Article/3067730.shtml
- https://www.read.puhvjy.cn/Article/182415.shtml
- https://www.read.nzfnve.cn/Article/859192.shtml
- https://www.read.nwbbyt.cn/Article/4800.shtml
- https://www.read.nwbbyt.cn/Article/102417.shtml
- https://www.read.jnjpgf.cn/Article/7195.shtml
- https://www.read.fuvxie.cn/Article/022743.shtml
- https://www.read.nwbbyt.cn/Article/842759.shtml
- https://www.read.fuvxie.cn/Article/0453915.shtml
- https://www.read.nwbbyt.cn/Article/159205.shtml
- https://www.read.puhvjy.cn/Article/09638.shtml
- https://www.read.cmcvrr.cn/Article/6324165.shtml
- https://www.read.jnjpgf.cn/Article/734150.shtml
- https://www.read.nwbbyt.cn/Article/8430.shtml
- https://www.read.nzfnve.cn/Article/0543745.shtml
- https://www.read.fuvxie.cn/Article/0053.shtml
- https://www.read.jnjpgf.cn/Article/1111754.shtml
- https://www.read.puhvjy.cn/Article/094189.shtml
- https://www.read.nwbbyt.cn/Article/234670.shtml
- https://www.read.puhvjy.cn/Article/97102.shtml
- https://www.read.cvsifc.cn/Article/971192.shtml
- https://www.read.puhvjy.cn/Article/190394.shtml
- https://www.read.jnjpgf.cn/Article/6451.shtml
- https://www.read.cvsifc.cn/Article/8302776.shtml
- https://www.read.cmcvrr.cn/Article/8285473.shtml
- https://www.read.jnjpgf.cn/Article/9926202.shtml
- https://www.read.fuvxie.cn/Article/5861.shtml
- https://www.read.nwbbyt.cn/Article/2461.shtml
- https://www.read.cvsifc.cn/Article/2582.shtml
- https://www.read.nzfnve.cn/Article/02150.shtml
- https://www.read.nzfnve.cn/Article/247448.shtml
- https://www.read.cmcvrr.cn/Article/9464544.shtml
- https://www.read.jnjpgf.cn/Article/63876.shtml
- https://www.read.puhvjy.cn/Article/423544.shtml
- https://www.read.jnjpgf.cn/Article/6599.shtml
- https://www.read.nwbbyt.cn/Article/619996.shtml
- https://www.read.jnjpgf.cn/Article/23902.shtml
- https://www.read.fuvxie.cn/Article/042677.shtml
- https://www.read.hcbezg.cn/Article/6755622.shtml
- https://www.read.nwbbyt.cn/Article/8471.shtml
- https://www.read.nwbbyt.cn/Article/9429727.shtml
- https://www.read.cvsifc.cn/Article/129218.shtml
- https://www.read.nzfnve.cn/Article/22565.shtml
- https://www.read.puhvjy.cn/Article/801479.shtml
- https://www.read.nwbbyt.cn/Article/643811.shtml
- https://www.read.cmcvrr.cn/Article/50087.shtml
- https://www.read.cvsifc.cn/Article/3380132.shtml
- https://www.read.cmcvrr.cn/Article/801965.shtml
- https://www.read.fuvxie.cn/Article/47357.shtml
- https://www.read.hcbezg.cn/Article/3988598.shtml
- https://www.read.hcbezg.cn/Article/71639.shtml
- https://www.read.nzfnve.cn/Article/70042.shtml
- https://www.read.fuvxie.cn/Article/55915.shtml
- https://www.read.jnjpgf.cn/Article/1898.shtml
- https://www.read.fuvxie.cn/Article/5082.shtml
- https://www.read.nwbbyt.cn/Article/80991.shtml
- https://www.read.jnjpgf.cn/Article/185536.shtml
- https://www.read.puhvjy.cn/Article/7922.shtml
- https://www.read.puhvjy.cn/Article/7291.shtml
- https://www.read.nwbbyt.cn/Article/20899.shtml
- https://www.read.hcbezg.cn/Article/335857.shtml
- https://www.read.nwbbyt.cn/Article/8266862.shtml
- https://www.read.jnjpgf.cn/Article/610190.shtml
- https://www.read.fuvxie.cn/Article/556229.shtml
- https://www.read.hcbezg.cn/Article/8445.shtml
- https://www.read.puhvjy.cn/Article/4596249.shtml
- https://www.read.cvsifc.cn/Article/18024.shtml
- https://www.read.cvsifc.cn/Article/9549.shtml
- https://www.read.jnjpgf.cn/Article/10089.shtml
- https://www.read.puhvjy.cn/Article/851371.shtml
- https://www.read.puhvjy.cn/Article/4973280.shtml
- https://www.read.cmcvrr.cn/Article/7359001.shtml
- https://www.read.nwbbyt.cn/Article/11609.shtml
- https://www.read.puhvjy.cn/Article/9344242.shtml
- https://www.read.nwbbyt.cn/Article/1915601.shtml
- https://www.read.jnjpgf.cn/Article/5332.shtml
- https://www.read.hcbezg.cn/Article/4072064.shtml
- https://www.read.nwbbyt.cn/Article/1470.shtml
- https://www.read.nwbbyt.cn/Article/82248.shtml
- https://www.read.hcbezg.cn/Article/2237804.shtml
- https://www.read.nwbbyt.cn/Article/25103.shtml
- https://www.read.cvsifc.cn/Article/8354069.shtml
- https://www.read.cvsifc.cn/Article/41379.shtml
- https://www.read.fuvxie.cn/Article/1175685.shtml
- https://www.read.jnjpgf.cn/Article/69846.shtml
- https://www.read.jnjpgf.cn/Article/2547.shtml
- https://www.read.cvsifc.cn/Article/0963311.shtml
- https://www.read.nwbbyt.cn/Article/4057.shtml
- https://www.read.hcbezg.cn/Article/7478096.shtml
- https://www.read.nzfnve.cn/Article/3835.shtml
- https://www.read.cmcvrr.cn/Article/4061603.shtml
- https://www.read.nwbbyt.cn/Article/17427.shtml
- https://www.read.puhvjy.cn/Article/9529723.shtml
- https://www.read.nwbbyt.cn/Article/4942453.shtml
- https://www.read.fuvxie.cn/Article/1164.shtml
- https://www.read.nzfnve.cn/Article/1950.shtml
- https://www.read.nzfnve.cn/Article/11601.shtml
- https://www.read.nwbbyt.cn/Article/85676.shtml
- https://www.read.nwbbyt.cn/Article/9317657.shtml
- https://www.read.nzfnve.cn/Article/662650.shtml
- https://www.read.cvsifc.cn/Article/1349.shtml
- https://www.read.nzfnve.cn/Article/09941.shtml
- https://www.read.hcbezg.cn/Article/46400.shtml
- https://www.read.hcbezg.cn/Article/78942.shtml
- https://www.read.nwbbyt.cn/Article/392442.shtml
- https://www.read.fuvxie.cn/Article/4973.shtml
- https://www.read.cmcvrr.cn/Article/5801.shtml
- https://www.read.nzfnve.cn/Article/3076.shtml
- https://www.read.cmcvrr.cn/Article/81910.shtml
- https://www.read.hcbezg.cn/Article/3690093.shtml
- https://www.read.jnjpgf.cn/Article/1255946.shtml
- https://www.read.nwbbyt.cn/Article/0352.shtml
- https://www.read.puhvjy.cn/Article/6010647.shtml
- https://www.read.hcbezg.cn/Article/826357.shtml
- https://www.read.fuvxie.cn/Article/41996.shtml
- https://www.read.jnjpgf.cn/Article/2707474.shtml
- https://www.read.hcbezg.cn/Article/4603357.shtml
- https://www.read.cmcvrr.cn/Article/5638.shtml
- https://www.read.cmcvrr.cn/Article/5566505.shtml
- https://www.read.jnjpgf.cn/Article/8767828.shtml
- https://www.read.hcbezg.cn/Article/0995984.shtml
- https://www.read.fuvxie.cn/Article/2434.shtml
- https://www.read.puhvjy.cn/Article/6034260.shtml
- https://www.read.nzfnve.cn/Article/27155.shtml
- https://www.read.nzfnve.cn/Article/3984603.shtml
- https://www.read.cmcvrr.cn/Article/12237.shtml
- https://www.read.nzfnve.cn/Article/8677.shtml
- https://www.read.nwbbyt.cn/Article/4614185.shtml
- https://www.read.nzfnve.cn/Article/9526399.shtml
- https://www.read.fuvxie.cn/Article/9603668.shtml
- https://www.read.nzfnve.cn/Article/4588499.shtml
- https://www.read.nwbbyt.cn/Article/4610.shtml
- https://www.read.nzfnve.cn/Article/1848337.shtml
- https://www.read.nzfnve.cn/Article/00024.shtml
- https://www.read.cvsifc.cn/Article/298360.shtml
- https://www.read.jnjpgf.cn/Article/1371.shtml
- https://www.read.puhvjy.cn/Article/232528.shtml
- https://www.read.nzfnve.cn/Article/666699.shtml
- https://www.read.jnjpgf.cn/Article/6724.shtml
- https://www.read.jnjpgf.cn/Article/324899.shtml
- https://www.read.cvsifc.cn/Article/64974.shtml
- https://www.read.fuvxie.cn/Article/841532.shtml
- https://www.read.hcbezg.cn/Article/7831369.shtml
- https://www.read.puhvjy.cn/Article/015180.shtml
- https://www.read.jnjpgf.cn/Article/075241.shtml
- https://www.read.cmcvrr.cn/Article/4299962.shtml
- https://www.read.hcbezg.cn/Article/15418.shtml
- https://www.read.cvsifc.cn/Article/126745.shtml
- https://www.read.fuvxie.cn/Article/87518.shtml
- https://www.read.jnjpgf.cn/Article/5607.shtml
- https://www.read.nwbbyt.cn/Article/656894.shtml
- https://www.read.cmcvrr.cn/Article/35092.shtml
- https://www.read.puhvjy.cn/Article/2836550.shtml
- https://www.read.hcbezg.cn/Article/98087.shtml
- https://www.read.nwbbyt.cn/Article/354568.shtml
- https://www.read.cmcvrr.cn/Article/3012618.shtml
- https://www.read.cmcvrr.cn/Article/497707.shtml
- https://www.read.cvsifc.cn/Article/0720.shtml
- https://www.read.nwbbyt.cn/Article/86955.shtml
- https://www.read.puhvjy.cn/Article/6212.shtml
- https://www.read.puhvjy.cn/Article/02626.shtml
- https://www.read.jnjpgf.cn/Article/636018.shtml
- https://www.read.cmcvrr.cn/Article/2010.shtml
- https://www.read.nwbbyt.cn/Article/1323274.shtml
- https://www.read.nzfnve.cn/Article/3579346.shtml
- https://www.read.nwbbyt.cn/Article/8507459.shtml
- https://www.read.hcbezg.cn/Article/2551954.shtml
- https://www.read.cvsifc.cn/Article/7444851.shtml
- https://www.read.cmcvrr.cn/Article/92203.shtml
- https://www.read.nwbbyt.cn/Article/77323.shtml
- https://www.read.puhvjy.cn/Article/6798.shtml
- https://www.read.cvsifc.cn/Article/10975.shtml
- https://www.read.jnjpgf.cn/Article/12566.shtml
- https://www.read.jnjpgf.cn/Article/073320.shtml
- https://www.read.cvsifc.cn/Article/05405.shtml
- https://www.read.nwbbyt.cn/Article/329443.shtml
- https://www.read.nwbbyt.cn/Article/0648.shtml
- https://www.read.jnjpgf.cn/Article/827469.shtml
- https://www.read.fuvxie.cn/Article/4566.shtml
- https://www.read.cvsifc.cn/Article/043823.shtml
- https://www.read.jnjpgf.cn/Article/19513.shtml
- https://www.read.hcbezg.cn/Article/8835052.shtml
- https://www.read.cmcvrr.cn/Article/758103.shtml
- https://www.read.jnjpgf.cn/Article/2962.shtml
- https://www.read.nzfnve.cn/Article/98099.shtml
- https://www.read.jnjpgf.cn/Article/126573.shtml
- https://www.read.cvsifc.cn/Article/89365.shtml
- https://www.read.hcbezg.cn/Article/1455348.shtml
- https://www.read.cmcvrr.cn/Article/8392090.shtml
- https://www.read.nzfnve.cn/Article/382305.shtml
- https://www.read.jnjpgf.cn/Article/91079.shtml
- https://www.read.hcbezg.cn/Article/8120.shtml
- https://www.read.jnjpgf.cn/Article/5376.shtml
- https://www.read.cvsifc.cn/Article/3887489.shtml
- https://www.read.nwbbyt.cn/Article/2569.shtml
- https://www.read.jnjpgf.cn/Article/52638.shtml
- https://www.read.fuvxie.cn/Article/3556.shtml
- https://www.read.nzfnve.cn/Article/15979.shtml
- https://www.read.hcbezg.cn/Article/66601.shtml
- https://www.read.nwbbyt.cn/Article/3806.shtml
- https://www.read.nzfnve.cn/Article/9811.shtml
- https://www.read.cmcvrr.cn/Article/839283.shtml
- https://www.read.nzfnve.cn/Article/99969.shtml
- https://www.read.jnjpgf.cn/Article/9026085.shtml
- https://www.read.nwbbyt.cn/Article/1503672.shtml
- https://www.read.cvsifc.cn/Article/9472288.shtml
- https://www.read.cmcvrr.cn/Article/29676.shtml
- https://www.read.jnjpgf.cn/Article/17090.shtml
- https://www.read.cvsifc.cn/Article/07329.shtml
- https://www.read.jnjpgf.cn/Article/1434127.shtml
- https://www.read.puhvjy.cn/Article/02876.shtml
- https://www.read.jnjpgf.cn/Article/1819.shtml
- https://www.read.cvsifc.cn/Article/5316329.shtml
- https://www.read.jnjpgf.cn/Article/45815.shtml
- https://www.read.jnjpgf.cn/Article/1381.shtml
- https://www.read.hcbezg.cn/Article/4452.shtml
- https://www.read.nwbbyt.cn/Article/203730.shtml
- https://www.read.hcbezg.cn/Article/1976.shtml
- https://www.read.nwbbyt.cn/Article/95216.shtml
- https://www.read.cvsifc.cn/Article/847811.shtml
- https://www.read.cmcvrr.cn/Article/31524.shtml
- https://www.read.fuvxie.cn/Article/4729.shtml
- https://www.read.cmcvrr.cn/Article/8493321.shtml
- https://www.read.cvsifc.cn/Article/50413.shtml
- https://www.read.cvsifc.cn/Article/83362.shtml
- https://www.read.cmcvrr.cn/Article/57444.shtml
- https://www.read.nzfnve.cn/Article/72375.shtml
- https://www.read.cvsifc.cn/Article/0147494.shtml
- https://www.read.hcbezg.cn/Article/4288.shtml
- https://www.read.cmcvrr.cn/Article/1671327.shtml
- https://www.read.nzfnve.cn/Article/882127.shtml
- https://www.read.jnjpgf.cn/Article/714648.shtml
- https://www.read.cvsifc.cn/Article/7006.shtml
- https://www.read.hcbezg.cn/Article/5843.shtml
- https://www.read.cvsifc.cn/Article/505253.shtml
- https://www.read.puhvjy.cn/Article/251875.shtml
- https://www.read.puhvjy.cn/Article/19165.shtml
- https://www.read.puhvjy.cn/Article/2898.shtml
- https://www.read.puhvjy.cn/Article/9470.shtml
- https://www.read.jnjpgf.cn/Article/1399.shtml
- https://www.read.puhvjy.cn/Article/8233415.shtml
- https://www.read.jnjpgf.cn/Article/14949.shtml
- https://www.read.nzfnve.cn/Article/26294.shtml
- https://www.read.fuvxie.cn/Article/3547060.shtml
- https://www.read.fuvxie.cn/Article/432744.shtml
- https://www.read.jnjpgf.cn/Article/66280.shtml

## 项目结构

```
linkvault-core/
├── src/                                  # 核心源码目录
│   ├── linkvault/
│   │   ├── __init__.py                   # 包初始化与版本声明
│   │   ├── cli.py                        # Click 命令入口与参数解析
│   │   ├── importer.py                   # 批量导入、去重与格式识别逻辑
│   │   ├── checker.py                    # 异步巡检引擎与状态判定
│   │   ├── exporter.py                   # 多格式导出与过滤器实现
│   │   ├── storage.py                    # JSONL 读写与差异日志管理
│   │   └── hooks.py                      # 钩子脚本加载与执行沙箱
│   └── tests/                            # 单元测试与集成测试套件
│       ├── test_importer.py              # 导入流程边界用例
│       ├── test_checker.py               # 模拟 HTTP 响应的巡检测试
│       └── test_storage.py               # 存储层读写一致性验证
├── config/                               # 配置模板与预设策略
│   ├── config.example.yaml               # 完整参数示例文件
│   └── policy.default.yaml               # 默认巡检策略（超时/重试/并发）
├── data/                                 # 运行时数据存储（用户生成）
│   ├── vault.jsonl                       # 主链接元数据存储
│   └── vault.jsonl.diff                  # 增量变更日志（每次更新追加）
├── logs/                                 # 操作日志与巡检报告归档
│   ├── import.log                        # 导入操作时间线与错误记录
│   └── check/                            # 按日期组织的巡检结果快照
│       └── 2026-07-07T10-30-00.json
├── docs/                                 # 完整文档目录（参见文档导航）
│   ├── getting-started.md
│   ├── commands.md
│   ├── check-policy.md
│   └── extend.md
├── scripts/                              # 官方维护的扩展脚本示例
│   ├── slack_notifier.py                 # 巡检异常时发送 Slack 告警
│   └── tag_auto_assign.sh                # 基于域名自动打标的辅助脚本
├── requirements.txt                      # 生产环境依赖锁
├── requirements-dev.txt                  # 开发测试额外依赖
├── setup.py                              # 可安装包配置（entry_points）
└── README.md                             # 项目概述与快速入门（本文档）
```

## 贡献指南

1. 查阅 issue 列表与 projects 看板，确认当前迭代周期内的待办事项。对于新功能或较大改动，建议先创建讨论 issue 说明设计思路，避免无效实现。

2. 克隆仓库并创建独立的特性分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式。确保本地开发环境已安装 `requirements-dev.txt` 中的全部依赖。

3. 所有代码变更需附带对应的单元测试或集成测试，确保 `pytest` 套件通过率为 100%。对于新增 CLI 参数，需同步更新 `docs/commands.md` 中的说明。

4. 提交前运行 `./scripts/lint.sh` 执行代码风格检查（基于 black 与 flake8），并确保无警告输出。commit message 采用简洁的英文描述，首行不超过 72 字符。

5. 发起 Pull Request 时填写标准模板，包含变更动机、测试方式与影响范围。PR 至少需要一名 maintainer 审核通过后方可合并。

## 常见问题

Q: 导入包含数万条链接的文件时，内存占用是否会过高？

A: LinkVault Core 采用流式逐行读取方式处理导入文件，不会将全部内容一次性载入内存。每条链接在解析后立即写入 JSONL 存储，同时内存中仅维护必要的去重索引（基于 URL 哈希）。经测试，在 8GB 内存的实例上可稳定处理 50 万条以上的链接记录。

Q: 巡检功能是否会因为目标站点反爬机制而被封锁 IP？

A: 巡检模块默认仅发送轻量级 HEAD 请求，且不携带任何自定义 User-Agent 以外的头部信息。并发数默认控制在 20 以下，并支持通过配置随机延迟（jitter）降低请求频率。对于需要更高谨慎度的场景，建议在 `config.yaml` 中启用 `check.policy.rate_limit` 选项并配合代理池使用。

Q: 如何将现有其他工具中的链接数据迁移至 LinkVault Core？

A: 项目提供了简单的转换脚本 `scripts/migrate_from_csv.py`，支持从通用 CSV 格式（列映射可配置）直接导入。若现有数据格式为 JSON 或 SQLite，可参考该脚本的实现方式自行调整字段映射。迁移完成后，建议执行一次全量巡检以建立初始可用性基线。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

# LinkVault Resource Aggregator

LinkVault 是一个面向技术研究、学术文献检索和开发文档查阅的轻量级外链资源汇总系统。该项目不对原始内容进行转载或存储，而是提供结构化分类、状态监控和快速跳转能力，帮助研究人员、技术文档编写者和运维工程师从大量分散的阅读来源中高效定位所需文章。LinkVault 定位于个人知识库辅助工具与团队共享书签管理的中间层，通过简单的目录树和标签化组织，将分散在多个阅读域名下的文章聚合为可检索、可维护的本地索引。

本项目不包含爬虫或自动抓取逻辑，所有资源链接由人工或可信数据源导入，项目本身仅维护链接元数据（标题、来源域名、导入批次、有效性状态）。LinkVault 适用于每日需要处理 50 条以上外链阅读清单的技术管理者，以及需要将外部参考资料与内部文档体系打通的知识工程团队。

## 功能概览

批量链接导入 支持按批次（当前为第 67/160 批）导入原始 URL 列表，自动解析域名并生成基础元数据记录。

域名分类视图 根据来源域名对资源进行自动分组，支持按域名快速过滤，方便识别高频阅读源。

链接有效性检查 提供可选的静态检查模式，通过 HTTP 头分析或正则匹配判断链接是否可访问，结果以状态标签呈现。

Markdown 原生输出 所有资源列表均以纯 Markdown 格式渲染，无需额外渲染引擎，兼容大多数静态站点生成器和代码托管平台。

批次管理追踪 每个资源记录均包含导入批次号（如 67/160），支持按批次回溯历史导入数据，便于增量更新和差异对比。

轻量级本地部署 无需数据库，基于文件系统存储元数据，支持单机或共享卷部署，降低运维成本。

扩展字段预留 每条记录预留备注字段，可用于记录阅读进度、重要性评分或关联内部工单编号，满足团队协作场景。

## 应用场景

技术文档团队外链归档 技术写作团队在编写产品文档时，需要引用大量外部标准或参考文章。LinkVault 可以将分散在多个阅读站点的参考链接统一纳入本地索引，每次撰写文档时通过域名或批次快速调取相关资源，避免重复搜索。

运维工程师日常巡检材料整理 运维人员每日需要查阅多个来源的变更公告、故障报告或性能分析文章。通过 LinkVault 按批次导入每日阅读清单，可在周报或故障复盘时快速回溯当周参考的所有外部链接，确保引用准确。

学术研究人员文献笔记辅助 人文或社科领域的研究者在阅读大量电子文献时，常需要记录来源链接并做简要批注。LinkVault 提供结构化的链接列表，研究者可将每条链接与本地笔记文件（如 Markdown 或 Org 模式）关联，实现文献来源的规范化管理。

开源项目外部依赖参考索引 开源项目维护者需要记录上游依赖的官方文档、社区讨论帖或替代方案对比文章。LinkVault 可作为项目仓库的 `docs/external-references.md` 补充工具，在项目根目录维护一份可版本控制的外链清单。

## 快速开始

以下命令可在任意 Unix/Linux 或 macOS 环境下完成 LinkVault 的初次部署与运行。Windows 用户建议通过 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/linkvault.git
cd linkvault

# 安装依赖（使用 Python 虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 导入当前批次资源（示例：导入第 67 批）
python linkvault.py import --batch 67 --source ./data/batch_67.txt

# 生成静态索引页面
python linkvault.py build --output ./docs/index.md

# 查看本地服务（可选）
python -m http.server 8000 --directory ./docs
```

首次运行前请确保 `data/` 目录存在，且 `batch_67.txt` 为每行一个 URL 的纯文本文件。导入完成后，可在 `docs/index.md` 中查看生成的完整资源列表。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 或更高 | 核心运行环境，用于导入、构建和检查脚本 |
| pip | 20.0 或更高 | Python 包管理器，用于安装依赖库 |
| Git | 2.25 或更高 | 用于克隆仓库和版本管理（可选，直接下载源码包亦可） |
| curl | 7.68 或更高 | 用于链接有效性检查（若启用网络检查功能） |
| make | 3.81 或更高 | 用于执行自动化任务（如 `make build`、`make test`） |
| Markdown 渲染器 | 任意 | 生成 `docs/index.md` 后可使用任何 Markdown 预览工具查看 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | `docs/user-guide.md` | 如何导入批次、查看资源列表、更新元数据？ |
| 运维指南 | `docs/operations.md` | 如何迁移数据、备份索引、更换存储目录？ |
| 开发参考 | `docs/development.md` | 如何扩展新的分类器、自定义输出模板？ |
| 常见问题 | `docs/faq.md` | 链接失效如何处理？多批次数据如何合并？ |

## 资源列表

- https://www.read.puhvjy.cn/Article/01077.shtml
- https://www.read.hcbezg.cn/Article/5346677.shtml
- https://www.read.nzfnve.cn/Article/9299934.shtml
- https://www.read.nzfnve.cn/Article/57418.shtml
- https://www.read.nwbbyt.cn/Article/39886.shtml
- https://www.read.nzfnve.cn/Article/35199.shtml
- https://www.read.nwbbyt.cn/Article/5663028.shtml
- https://www.read.nwbbyt.cn/Article/3839.shtml
- https://www.read.hcbezg.cn/Article/7601.shtml
- https://www.read.jnjpgf.cn/Article/5405.shtml
- https://www.read.nwbbyt.cn/Article/2822933.shtml
- https://www.read.puhvjy.cn/Article/673940.shtml
- https://www.read.cvsifc.cn/Article/7093447.shtml
- https://www.read.cmcvrr.cn/Article/2548227.shtml
- https://www.read.nzfnve.cn/Article/5438.shtml
- https://www.read.jnjpgf.cn/Article/348992.shtml
- https://www.read.puhvjy.cn/Article/4656.shtml
- https://www.read.nwbbyt.cn/Article/2702140.shtml
- https://www.read.cmcvrr.cn/Article/678473.shtml
- https://www.read.nwbbyt.cn/Article/4959125.shtml
- https://www.read.cmcvrr.cn/Article/4696.shtml
- https://www.read.jnjpgf.cn/Article/5668.shtml
- https://www.read.nzfnve.cn/Article/3510514.shtml
- https://www.read.puhvjy.cn/Article/533013.shtml
- https://www.read.cmcvrr.cn/Article/1594.shtml
- https://www.read.puhvjy.cn/Article/5438.shtml
- https://www.read.cvsifc.cn/Article/4612.shtml
- https://www.read.hcbezg.cn/Article/680397.shtml
- https://www.read.fuvxie.cn/Article/618095.shtml
- https://www.read.fuvxie.cn/Article/48614.shtml
- https://www.read.cvsifc.cn/Article/834265.shtml
- https://www.read.cmcvrr.cn/Article/56715.shtml
- https://www.read.nzfnve.cn/Article/5906566.shtml
- https://www.read.fuvxie.cn/Article/525891.shtml
- https://www.read.hcbezg.cn/Article/4078423.shtml
- https://www.read.cvsifc.cn/Article/4154233.shtml
- https://www.read.fuvxie.cn/Article/5737734.shtml
- https://www.read.cvsifc.cn/Article/8416216.shtml
- https://www.read.cmcvrr.cn/Article/32008.shtml
- https://www.read.cvsifc.cn/Article/78819.shtml
- https://www.read.fuvxie.cn/Article/5892.shtml
- https://www.read.jnjpgf.cn/Article/0177874.shtml
- https://www.read.nzfnve.cn/Article/036884.shtml
- https://www.read.nwbbyt.cn/Article/7791.shtml
- https://www.read.cvsifc.cn/Article/14120.shtml
- https://www.read.puhvjy.cn/Article/63489.shtml
- https://www.read.puhvjy.cn/Article/666820.shtml
- https://www.read.jnjpgf.cn/Article/549914.shtml
- https://www.read.fuvxie.cn/Article/6624948.shtml
- https://www.read.fuvxie.cn/Article/305741.shtml
- https://www.read.cmcvrr.cn/Article/9782.shtml
- https://www.read.cmcvrr.cn/Article/5768.shtml
- https://www.read.nzfnve.cn/Article/9034.shtml
- https://www.read.jnjpgf.cn/Article/159603.shtml
- https://www.read.cmcvrr.cn/Article/2259064.shtml
- https://www.read.nwbbyt.cn/Article/6354.shtml
- https://www.read.jnjpgf.cn/Article/960129.shtml
- https://www.read.cmcvrr.cn/Article/2264.shtml
- https://www.read.nzfnve.cn/Article/564205.shtml
- https://www.read.nzfnve.cn/Article/7108929.shtml
- https://www.read.puhvjy.cn/Article/3497.shtml
- https://www.read.nzfnve.cn/Article/6751.shtml
- https://www.read.jnjpgf.cn/Article/00450.shtml
- https://www.read.jnjpgf.cn/Article/9507800.shtml
- https://www.read.jnjpgf.cn/Article/83868.shtml
- https://www.read.cmcvrr.cn/Article/0375449.shtml
- https://www.read.fuvxie.cn/Article/478258.shtml
- https://www.read.nzfnve.cn/Article/2547633.shtml
- https://www.read.cmcvrr.cn/Article/7294.shtml
- https://www.read.puhvjy.cn/Article/0240397.shtml
- https://www.read.nzfnve.cn/Article/3233031.shtml
- https://www.read.fuvxie.cn/Article/0688600.shtml
- https://www.read.cmcvrr.cn/Article/3202792.shtml
- https://www.read.cmcvrr.cn/Article/152140.shtml
- https://www.read.jnjpgf.cn/Article/53386.shtml
- https://www.read.cvsifc.cn/Article/487588.shtml
- https://www.read.puhvjy.cn/Article/7288.shtml
- https://www.read.cmcvrr.cn/Article/9928.shtml
- https://www.read.nwbbyt.cn/Article/26855.shtml
- https://www.read.cvsifc.cn/Article/8558548.shtml
- https://www.read.puhvjy.cn/Article/2201714.shtml
- https://www.read.nwbbyt.cn/Article/802101.shtml
- https://www.read.jnjpgf.cn/Article/1550.shtml
- https://www.read.hcbezg.cn/Article/19699.shtml
- https://www.read.jnjpgf.cn/Article/608407.shtml
- https://www.read.jnjpgf.cn/Article/2310762.shtml
- https://www.read.nwbbyt.cn/Article/80580.shtml
- https://www.read.puhvjy.cn/Article/2136.shtml
- https://www.read.puhvjy.cn/Article/40497.shtml
- https://www.read.hcbezg.cn/Article/72554.shtml
- https://www.read.cvsifc.cn/Article/74583.shtml
- https://www.read.cvsifc.cn/Article/1489.shtml
- https://www.read.hcbezg.cn/Article/7596038.shtml
- https://www.read.nzfnve.cn/Article/7445.shtml
- https://www.read.hcbezg.cn/Article/389033.shtml
- https://www.read.hcbezg.cn/Article/9001620.shtml
- https://www.read.cvsifc.cn/Article/25493.shtml
- https://www.read.puhvjy.cn/Article/59222.shtml
- https://www.read.hcbezg.cn/Article/72113.shtml
- https://www.read.hcbezg.cn/Article/86100.shtml
- https://www.read.nwbbyt.cn/Article/55954.shtml
- https://www.read.nzfnve.cn/Article/90131.shtml
- https://www.read.jnjpgf.cn/Article/23778.shtml
- https://www.read.nwbbyt.cn/Article/58381.shtml
- https://www.read.cmcvrr.cn/Article/925017.shtml
- https://www.read.puhvjy.cn/Article/265056.shtml
- https://www.read.nwbbyt.cn/Article/1749.shtml
- https://www.read.nwbbyt.cn/Article/165370.shtml
- https://www.read.fuvxie.cn/Article/4195.shtml
- https://www.read.fuvxie.cn/Article/2804991.shtml
- https://www.read.fuvxie.cn/Article/684119.shtml
- https://www.read.jnjpgf.cn/Article/5394.shtml
- https://www.read.nzfnve.cn/Article/14269.shtml
- https://www.read.cvsifc.cn/Article/986429.shtml
- https://www.read.puhvjy.cn/Article/712820.shtml
- https://www.read.fuvxie.cn/Article/2923.shtml
- https://www.read.nwbbyt.cn/Article/14241.shtml
- https://www.read.hcbezg.cn/Article/926892.shtml
- https://www.read.cvsifc.cn/Article/47342.shtml
- https://www.read.jnjpgf.cn/Article/8237.shtml
- https://www.read.fuvxie.cn/Article/972125.shtml
- https://www.read.nwbbyt.cn/Article/12221.shtml
- https://www.read.nwbbyt.cn/Article/651993.shtml
- https://www.read.cmcvrr.cn/Article/933299.shtml
- https://www.read.nwbbyt.cn/Article/6344.shtml
- https://www.read.nzfnve.cn/Article/57888.shtml
- https://www.read.fuvxie.cn/Article/92595.shtml
- https://www.read.fuvxie.cn/Article/27006.shtml
- https://www.read.nzfnve.cn/Article/0450.shtml
- https://www.read.fuvxie.cn/Article/41281.shtml
- https://www.read.jnjpgf.cn/Article/4514.shtml
- https://www.read.cvsifc.cn/Article/9657376.shtml
- https://www.read.fuvxie.cn/Article/8400.shtml
- https://www.read.cvsifc.cn/Article/82557.shtml
- https://www.read.cmcvrr.cn/Article/31631.shtml
- https://www.read.cmcvrr.cn/Article/32182.shtml
- https://www.read.cmcvrr.cn/Article/31132.shtml
- https://www.read.nzfnve.cn/Article/22219.shtml
- https://www.read.cvsifc.cn/Article/29894.shtml
- https://www.read.nzfnve.cn/Article/7986.shtml
- https://www.read.cmcvrr.cn/Article/3265224.shtml
- https://www.read.cvsifc.cn/Article/2595.shtml
- https://www.read.fuvxie.cn/Article/4701602.shtml
- https://www.read.nzfnve.cn/Article/6554.shtml
- https://www.read.cvsifc.cn/Article/48521.shtml
- https://www.read.jnjpgf.cn/Article/2456.shtml
- https://www.read.nwbbyt.cn/Article/564200.shtml
- https://www.read.fuvxie.cn/Article/7092428.shtml
- https://www.read.fuvxie.cn/Article/552941.shtml
- https://www.read.nwbbyt.cn/Article/5304622.shtml
- https://www.read.nwbbyt.cn/Article/6833.shtml
- https://www.read.puhvjy.cn/Article/111565.shtml
- https://www.read.fuvxie.cn/Article/36618.shtml
- https://www.read.nzfnve.cn/Article/63279.shtml
- https://www.read.cvsifc.cn/Article/36158.shtml
- https://www.read.nzfnve.cn/Article/2100989.shtml
- https://www.read.jnjpgf.cn/Article/961253.shtml
- https://www.read.nzfnve.cn/Article/783271.shtml
- https://www.read.puhvjy.cn/Article/5805.shtml
- https://www.read.jnjpgf.cn/Article/9596688.shtml
- https://www.read.cmcvrr.cn/Article/1441.shtml
- https://www.read.fuvxie.cn/Article/7622.shtml
- https://www.read.cmcvrr.cn/Article/4797.shtml
- https://www.read.jnjpgf.cn/Article/73703.shtml
- https://www.read.hcbezg.cn/Article/949873.shtml
- https://www.read.jnjpgf.cn/Article/814453.shtml
- https://www.read.cvsifc.cn/Article/70795.shtml
- https://www.read.nwbbyt.cn/Article/70205.shtml
- https://www.read.nwbbyt.cn/Article/1613645.shtml
- https://www.read.nwbbyt.cn/Article/90273.shtml
- https://www.read.nwbbyt.cn/Article/7972843.shtml
- https://www.read.hcbezg.cn/Article/16994.shtml
- https://www.read.cmcvrr.cn/Article/0167.shtml
- https://www.read.fuvxie.cn/Article/29800.shtml
- https://www.read.jnjpgf.cn/Article/27840.shtml
- https://www.read.jnjpgf.cn/Article/895444.shtml
- https://www.read.puhvjy.cn/Article/580506.shtml
- https://www.read.hcbezg.cn/Article/505729.shtml
- https://www.read.hcbezg.cn/Article/5011.shtml
- https://www.read.hcbezg.cn/Article/713958.shtml
- https://www.read.nzfnve.cn/Article/180989.shtml
- https://www.read.nzfnve.cn/Article/398344.shtml
- https://www.read.puhvjy.cn/Article/74553.shtml
- https://www.read.nwbbyt.cn/Article/9482.shtml
- https://www.read.puhvjy.cn/Article/0748.shtml
- https://www.read.nzfnve.cn/Article/684175.shtml
- https://www.read.nzfnve.cn/Article/1649602.shtml
- https://www.read.nzfnve.cn/Article/25707.shtml
- https://www.read.cmcvrr.cn/Article/993274.shtml
- https://www.read.hcbezg.cn/Article/829325.shtml
- https://www.read.puhvjy.cn/Article/80892.shtml
- https://www.read.nwbbyt.cn/Article/6020211.shtml
- https://www.read.nzfnve.cn/Article/198430.shtml
- https://www.read.nzfnve.cn/Article/5669.shtml
- https://www.read.cvsifc.cn/Article/328609.shtml
- https://www.read.puhvjy.cn/Article/2295.shtml
- https://www.read.nwbbyt.cn/Article/2478.shtml
- https://www.read.cvsifc.cn/Article/8431761.shtml
- https://www.read.nzfnve.cn/Article/097811.shtml
- https://www.read.hcbezg.cn/Article/631212.shtml
- https://www.read.cmcvrr.cn/Article/767936.shtml
- https://www.read.cmcvrr.cn/Article/1365190.shtml
- https://www.read.jnjpgf.cn/Article/5860.shtml
- https://www.read.hcbezg.cn/Article/5696.shtml
- https://www.read.hcbezg.cn/Article/9990.shtml
- https://www.read.puhvjy.cn/Article/2041.shtml
- https://www.read.puhvjy.cn/Article/2572314.shtml
- https://www.read.cmcvrr.cn/Article/5882492.shtml
- https://www.read.cvsifc.cn/Article/085833.shtml
- https://www.read.nzfnve.cn/Article/22904.shtml
- https://www.read.nwbbyt.cn/Article/3717800.shtml
- https://www.read.cvsifc.cn/Article/201646.shtml
- https://www.read.puhvjy.cn/Article/27314.shtml
- https://www.read.cvsifc.cn/Article/3883909.shtml
- https://www.read.hcbezg.cn/Article/0120.shtml
- https://www.read.puhvjy.cn/Article/703491.shtml
- https://www.read.puhvjy.cn/Article/8135660.shtml
- https://www.read.fuvxie.cn/Article/6735768.shtml
- https://www.read.hcbezg.cn/Article/7052470.shtml
- https://www.read.cvsifc.cn/Article/715671.shtml
- https://www.read.cmcvrr.cn/Article/603419.shtml
- https://www.read.nwbbyt.cn/Article/362476.shtml
- https://www.read.cvsifc.cn/Article/36999.shtml
- https://www.read.jnjpgf.cn/Article/82193.shtml
- https://www.read.cvsifc.cn/Article/6503284.shtml
- https://www.read.cmcvrr.cn/Article/1960.shtml
- https://www.read.jnjpgf.cn/Article/268229.shtml
- https://www.read.nwbbyt.cn/Article/9632.shtml
- https://www.read.cmcvrr.cn/Article/9821436.shtml
- https://www.read.nwbbyt.cn/Article/6043.shtml
- https://www.read.nwbbyt.cn/Article/09101.shtml
- https://www.read.puhvjy.cn/Article/91687.shtml
- https://www.read.puhvjy.cn/Article/2834.shtml
- https://www.read.cvsifc.cn/Article/582741.shtml
- https://www.read.cvsifc.cn/Article/30501.shtml
- https://www.read.jnjpgf.cn/Article/34369.shtml
- https://www.read.nzfnve.cn/Article/4420.shtml
- https://www.read.cmcvrr.cn/Article/6174.shtml
- https://www.read.nwbbyt.cn/Article/26979.shtml
- https://www.read.nwbbyt.cn/Article/02197.shtml
- https://www.read.puhvjy.cn/Article/65108.shtml
- https://www.read.jnjpgf.cn/Article/3529802.shtml
- https://www.read.nzfnve.cn/Article/5185.shtml
- https://www.read.cvsifc.cn/Article/5452.shtml
- https://www.read.jnjpgf.cn/Article/7361847.shtml
- https://www.read.jnjpgf.cn/Article/4656609.shtml
- https://www.read.nwbbyt.cn/Article/2138257.shtml
- https://www.read.puhvjy.cn/Article/2556.shtml
- https://www.read.fuvxie.cn/Article/436211.shtml
- https://www.read.jnjpgf.cn/Article/3021816.shtml

## 项目结构

```
linkvault/
├── data/                                # 原始数据与元数据存储目录
│   ├── batches/                         # 按批次存放导入的原始 URL 文件
│   │   ├── batch_066.txt                # 上一批导入记录
│   │   ├── batch_067.txt                # 当前批次原始数据（第 67/160 批）
│   │   └── batch_068.txt                # 下一批待导入模板
│   ├── metadata/                        # 链接元数据（标题、状态、备注）
│   │   ├── domain_index.json            # 域名与文章 ID 映射索引
│   │   └── status_cache.json            # 链接有效性检查结果缓存
│   └── schemas/                         # 数据格式定义
│       ├── import_schema_v2.json        # 导入文件格式规范
│       └── metadata_schema_v2.json      # 元数据存储结构规范
├── src/                                 # 核心源代码
│   ├── importers/                       # 导入器模块
│   │   ├── base_importer.py             # 抽象基类，定义导入接口
│   │   └── txt_importer.py              # 纯文本格式导入实现
│   ├── builders/                        # 构建器模块
│   │   ├── markdown_builder.py          # Markdown 索引页生成器
│   │   └── html_builder.py              # 可选 HTML 预览生成器
│   ├── checkers/                        # 链接检查模块
│   │   ├── http_checker.py              # 基于 HTTP 状态的检查
│   │   └── regex_checker.py             # 基于正则表达式的模式检查
│   └── cli/                             # 命令行接口
│       ├── main.py                      # 入口脚本，路由子命令
│       └── commands.py                  # import / build / check 命令实现
├── tests/                               # 单元测试与集成测试
│   ├── test_importers.py                # 导入器测试
│   ├── test_builders.py                 # 构建器测试
│   └── fixtures/                        # 测试用固定数据集
│       └── sample_batch.txt             # 5 条示例 URL
├── docs/                                # 生成的文档输出目录（git 忽略）
│   ├── index.md                         # 主资源列表（由 build 命令生成）
│   └── archives/                        # 历史索引存档
│       └── index_2026_07_07.md          # 按日期生成的快照
├── scripts/                             # 辅助脚本
│   ├── validate_urls.py                 # 校验 URL 格式是否符合规范
│   └── sync_to_remote.sh                # 同步生成的文档到远程静态站点
├── requirements.txt                     # Python 依赖列表
├── Makefile                             # 自动化任务（build, test, clean）
├── README.md                            # 本文件
└── LICENSE                              # MIT 许可证
```

## 贡献指南

我们欢迎任何形式的贡献，包括但不限于新增导入格式支持、优化链接检查策略、改进 Markdown 模板样式、修复文档错误等。

1. 在 GitHub 上 Fork 本仓库，并在本地克隆您的 Fork 副本。创建新的功能分支，分支命名建议采用 `feature/描述` 或 `fix/描述` 格式，例如 `feature/support-csv-import`。

2. 编写代码或文档修改后，请确保所有现有单元测试通过。若新增功能，请在 `tests/` 目录下补充对应的测试用例。运行测试命令：`make test`。

3. 提交前请执行代码风格检查（使用 `black` 和 `flake8`），确保符合项目编码规范。可运行 `make lint` 自动检查。

4. 提交 Pull Request 时，请在描述中清晰说明改动目的、实现方式和影响范围。若涉及数据结构变更，请同时更新 `data/schemas/` 下的 JSON Schema 文件并附迁移说明。

5. 对于新增外部依赖，请在 `requirements.txt` 中标注版本号，并在 PR 描述中说明新增依赖的必要性。

## 常见问题

**问：导入的链接如果失效了怎么办？**

系统不会自动删除失效链接。您可以使用 `check` 命令对已有链接进行有效性扫描，扫描结果会写入 `metadata/status_cache.json`。您可以根据状态标签手动决定是否保留该条目。若需要定期自动化检查，可配合 cron 任务每周运行一次 `python linkvault.py check --batch 67`。

**问：多个批次的链接存在重复怎么办？**

导入器默认会对同一批次内的 URL 进行去重。对于跨批次重复，系统会在元数据中记录首次导入批次号，后导入的重复条目会标记为 `duplicate` 状态并保留原始 URL，但不会覆盖已有记录。您可以在生成索引时通过 `--dedup` 参数控制是否隐藏重复项。

**问：如何将生成的资源列表与现有的 Wiki 或文档站点整合？**

`build` 命令默认生成纯 Markdown 文件，您可以直接将该文件复制到任何支持 Markdown 的 Wiki（如 GitLab Wiki、GitHub Wiki）或静态站点生成器（如 Hugo、MkDocs）的内容目录下。若需要生成 HTML，可使用 `--format html` 选项，并配合自定义 CSS 模板。具体配置请参考 `docs/operations.md` 中的“输出集成”一节。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

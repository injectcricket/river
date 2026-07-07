# H5Mobile Docs Index

H5Mobile Docs Index 是一个面向移动端技术文档与资源的外链聚合索引系统，专为技术团队、文档维护者及内容研究者设计，用于高效管理分散在多个移动端 H5 站点中的 .doc 格式技术文档、操作手册、实施方案与培训材料。该项目通过轻量级索引机制，将跨域名、跨目录的文档资源统一归集，提供可检索、可追踪的资源清单视图，解决多源文档分散、难以追溯与批量引用的问题。

本项目不提供文件存储或代理转发服务，仅作为资源定位索引层，保持对原始文档站点的完全透明引用，适用于内部文档治理、自动化爬虫任务编排、第三方内容审计等场景。

## 功能概览

多源资源归集：支持对多个独立 H5 移动端域名下的 /Article/ 目录文档进行索引聚合，当前覆盖 cmcvrr.cn、jnjpgf.cn、hcbezg.cn、cvsifc.cn、puhvjy.cn、fuvxie.cn、nzfnve.cn、nwbbyt.cn 共八个来源节点。

原始链接直出：所有资源链接保持原始 URL 完整原样输出，不进行协议补全、域名规范化、路径重写或参数附加，确保引用路径与源站完全一致。

批量资源清单输出：以可解析的纯文本列表形式输出全部索引资源，每行独立记录，便于脚本切割、正则匹配与批量请求编排。

无状态索引结构：项目本身不依赖数据库或后端服务，所有资源清单静态维护于文档中，支持版本控制与增量更新。

轻量级快速查阅：项目文档结构清晰，包含完整的快速开始指引、环境依赖说明与目录树，帮助新维护者在五分钟内完成环境配置与索引更新。

场景化导航支持：通过文档导航表格按层面（基础、进阶、运维、治理）组织资源索引，引导不同角色用户快速定位所需内容。

贡献流程标准化：提供明确的资源增删改流程，包含链接校验、格式检查、提交前自检与合并请求规范，降低协作成本。

常见问题覆盖：针对链接失效、新域名接入、批量更新等高频问题提供标准处置方案，减少重复答疑。

## 应用场景

企业内部文档资产盘点：技术团队可利用本索引清单，对散布在多个移动端 H5 项目中的历史 .doc 文档进行统一登记与版本追踪，辅助完成文档资产台账建设。

自动化文档健康度巡检：运维或质量保障人员可基于本索引输出的 URL 列表，编写定时脚本对每个链接发起 HEAD 请求，检测失效链接、重定向异常或内容变更，并将结果反馈至监控系统。

第三方内容引用溯源：研究机构或内容合规部门在引用外部技术材料时，可通过索引清单快速定位原始出处，避免因链接分散导致的引用遗漏或来源标注错误。

文档迁移与域名整合辅助：当源站域名或路径结构发生调整时，可借助索引清单进行批量替换测试，评估影响范围，制定灰度切换策略。

## 快速开始

以下步骤指导您在本地环境中完成本项目的克隆、依赖安装与索引清单生成运行。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/h5mobile-docs-index.git

# 进入项目工作目录
cd h5mobile-docs-index

# 安装依赖（Python 3.8+ 环境，用于辅助脚本执行）
pip install -r requirements.txt

# 执行索引清单生成脚本，输出当前全部资源列表至控制台与 output/ 目录
python scripts/generate_index.py --input docs/resources.txt --output output/index.md
```

如需每日自动更新索引，可将上述命令配置为 cron 任务，具体示例参见 `scripts/cron_example.sh`。

## 安装要求

本项目的核心索引数据以纯文本形式维护，不依赖运行时服务，但辅助脚本工具链需要满足以下环境要求。

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 用于运行索引生成、链接校验与格式检查脚本 |
| Git | 2.25 及以上 | 用于版本控制与协作提交 |
| curl | 7.68 及以上 | 用于可选的外部链接可达性测试 |
| GNU Make | 3.82 及以上 | 用于执行自动化任务组合（lint, check, build） |
| Shell (bash) | 4.0 及以上 | 用于运行辅助 shell 脚本与 cron 任务编排 |

## 文档导航

为帮助不同角色的使用者快速定位所需内容，本项目文档按层面划分如下。

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 基础入门 | docs/introduction.md | 项目是什么、如何快速获取全部资源列表、如何理解索引结构 |
| 进阶使用 | docs/advanced/usage.md | 如何过滤特定域名资源、如何排除特定路径、如何生成子集索引 |
| 运维管理 | docs/operations/maintenance.md | 如何检测链接有效性、如何处理失效资源、如何接入新域名 |
| 治理规范 | docs/governance/resource-standards.md | 资源收录标准、命名规范、版本记录格式、变更审批流程 |

## 资源列表

- h5.mobile.cmcvrr.cn/Article/1184.doc
- h5.mobile.jnjpgf.cn/Article/4233.doc
- h5.mobile.hcbezg.cn/Article/43268.doc
- h5.mobile.cmcvrr.cn/Article/6089.doc
- h5.mobile.cvsifc.cn/Article/1299019.doc
- h5.mobile.cmcvrr.cn/Article/1525568.doc
- h5.mobile.cmcvrr.cn/Article/240022.doc
- h5.mobile.puhvjy.cn/Article/686107.doc
- h5.mobile.fuvxie.cn/Article/2228.doc
- h5.mobile.puhvjy.cn/Article/4562838.doc
- h5.mobile.cmcvrr.cn/Article/47624.doc
- h5.mobile.cvsifc.cn/Article/8236.doc
- h5.mobile.cmcvrr.cn/Article/62403.doc
- h5.mobile.nzfnve.cn/Article/29228.doc
- h5.mobile.nwbbyt.cn/Article/4529548.doc
- h5.mobile.hcbezg.cn/Article/7309.doc
- h5.mobile.cvsifc.cn/Article/003635.doc
- h5.mobile.cvsifc.cn/Article/13437.doc
- h5.mobile.hcbezg.cn/Article/11566.doc
- h5.mobile.hcbezg.cn/Article/35744.doc
- h5.mobile.nwbbyt.cn/Article/9069.doc
- h5.mobile.puhvjy.cn/Article/3851908.doc
- h5.mobile.cvsifc.cn/Article/776596.doc
- h5.mobile.cvsifc.cn/Article/3166486.doc
- h5.mobile.jnjpgf.cn/Article/293450.doc
- h5.mobile.cmcvrr.cn/Article/585411.doc
- h5.mobile.nzfnve.cn/Article/48998.doc
- h5.mobile.fuvxie.cn/Article/3717.doc
- h5.mobile.fuvxie.cn/Article/2725033.doc
- h5.mobile.nwbbyt.cn/Article/73918.doc
- h5.mobile.nwbbyt.cn/Article/2253.doc
- h5.mobile.nwbbyt.cn/Article/8826.doc
- h5.mobile.cmcvrr.cn/Article/045323.doc
- h5.mobile.cvsifc.cn/Article/9042.doc
- h5.mobile.nwbbyt.cn/Article/21176.doc
- h5.mobile.jnjpgf.cn/Article/2921.doc
- h5.mobile.hcbezg.cn/Article/7975996.doc
- h5.mobile.jnjpgf.cn/Article/716731.doc
- h5.mobile.cmcvrr.cn/Article/206653.doc
- h5.mobile.jnjpgf.cn/Article/08397.doc
- h5.mobile.cmcvrr.cn/Article/9530.doc
- h5.mobile.nzfnve.cn/Article/755090.doc
- h5.mobile.fuvxie.cn/Article/513971.doc
- h5.mobile.jnjpgf.cn/Article/8839062.doc
- h5.mobile.nwbbyt.cn/Article/6747953.doc
- h5.mobile.nwbbyt.cn/Article/4140232.doc
- h5.mobile.jnjpgf.cn/Article/254212.doc
- h5.mobile.nzfnve.cn/Article/8352.doc
- h5.mobile.cvsifc.cn/Article/4155959.doc
- h5.mobile.cmcvrr.cn/Article/343715.doc
- h5.mobile.fuvxie.cn/Article/3026037.doc
- h5.mobile.nwbbyt.cn/Article/114334.doc
- h5.mobile.fuvxie.cn/Article/1814.doc
- h5.mobile.nwbbyt.cn/Article/6401245.doc
- h5.mobile.cmcvrr.cn/Article/4772317.doc
- h5.mobile.hcbezg.cn/Article/8410788.doc
- h5.mobile.jnjpgf.cn/Article/2601038.doc
- h5.mobile.nzfnve.cn/Article/64028.doc
- h5.mobile.cvsifc.cn/Article/04671.doc
- h5.mobile.cmcvrr.cn/Article/708100.doc
- h5.mobile.cmcvrr.cn/Article/50259.doc
- h5.mobile.fuvxie.cn/Article/582279.doc
- h5.mobile.puhvjy.cn/Article/2172771.doc
- h5.mobile.puhvjy.cn/Article/75031.doc
- h5.mobile.cmcvrr.cn/Article/5407312.doc
- h5.mobile.cvsifc.cn/Article/30309.doc
- h5.mobile.jnjpgf.cn/Article/46865.doc
- h5.mobile.hcbezg.cn/Article/616524.doc
- h5.mobile.nwbbyt.cn/Article/921439.doc
- h5.mobile.puhvjy.cn/Article/42895.doc
- h5.mobile.jnjpgf.cn/Article/90811.doc
- h5.mobile.puhvjy.cn/Article/7686819.doc
- h5.mobile.cvsifc.cn/Article/3922174.doc
- h5.mobile.cvsifc.cn/Article/7310.doc
- h5.mobile.fuvxie.cn/Article/63892.doc
- h5.mobile.cmcvrr.cn/Article/28646.doc
- h5.mobile.jnjpgf.cn/Article/41371.doc
- h5.mobile.puhvjy.cn/Article/367368.doc
- h5.mobile.nwbbyt.cn/Article/81765.doc
- h5.mobile.cmcvrr.cn/Article/766720.doc
- h5.mobile.puhvjy.cn/Article/1182.doc
- h5.mobile.hcbezg.cn/Article/341720.doc
- h5.mobile.puhvjy.cn/Article/7529.doc
- h5.mobile.nwbbyt.cn/Article/76048.doc
- h5.mobile.puhvjy.cn/Article/4744190.doc
- h5.mobile.fuvxie.cn/Article/1371509.doc
- h5.mobile.cvsifc.cn/Article/20255.doc
- h5.mobile.nzfnve.cn/Article/75598.doc
- h5.mobile.nwbbyt.cn/Article/16316.doc
- h5.mobile.cvsifc.cn/Article/177359.doc
- h5.mobile.puhvjy.cn/Article/94615.doc
- h5.mobile.puhvjy.cn/Article/8768.doc
- h5.mobile.nzfnve.cn/Article/5690.doc
- h5.mobile.cmcvrr.cn/Article/6621574.doc
- h5.mobile.fuvxie.cn/Article/23432.doc
- h5.mobile.cvsifc.cn/Article/46120.doc
- h5.mobile.nzfnve.cn/Article/6879499.doc
- h5.mobile.hcbezg.cn/Article/5788821.doc
- h5.mobile.fuvxie.cn/Article/815275.doc
- h5.mobile.puhvjy.cn/Article/017360.doc
- h5.mobile.puhvjy.cn/Article/564206.doc
- h5.mobile.hcbezg.cn/Article/238940.doc
- h5.mobile.nzfnve.cn/Article/9853287.doc
- h5.mobile.cvsifc.cn/Article/8679.doc
- h5.mobile.cmcvrr.cn/Article/8741.doc
- h5.mobile.jnjpgf.cn/Article/650422.doc
- h5.mobile.fuvxie.cn/Article/023813.doc
- h5.mobile.cvsifc.cn/Article/1561118.doc
- h5.mobile.fuvxie.cn/Article/6098.doc
- h5.mobile.cmcvrr.cn/Article/6695630.doc
- h5.mobile.nwbbyt.cn/Article/06707.doc
- h5.mobile.nzfnve.cn/Article/9303.doc
- h5.mobile.cmcvrr.cn/Article/660421.doc
- h5.mobile.cmcvrr.cn/Article/2288.doc
- h5.mobile.nwbbyt.cn/Article/7696069.doc
- h5.mobile.fuvxie.cn/Article/5060.doc
- h5.mobile.cmcvrr.cn/Article/6598.doc
- h5.mobile.cmcvrr.cn/Article/7240.doc
- h5.mobile.nzfnve.cn/Article/1447.doc
- h5.mobile.cvsifc.cn/Article/713049.doc
- h5.mobile.hcbezg.cn/Article/1688.doc
- h5.mobile.nzfnve.cn/Article/6425874.doc
- h5.mobile.cmcvrr.cn/Article/840761.doc
- h5.mobile.nwbbyt.cn/Article/9479.doc
- h5.mobile.cmcvrr.cn/Article/34230.doc
- h5.mobile.cmcvrr.cn/Article/0811991.doc
- h5.mobile.cmcvrr.cn/Article/6086.doc
- h5.mobile.nwbbyt.cn/Article/0494.doc
- h5.mobile.nzfnve.cn/Article/0436.doc
- h5.mobile.nwbbyt.cn/Article/28978.doc
- h5.mobile.cvsifc.cn/Article/84698.doc
- h5.mobile.hcbezg.cn/Article/9244.doc
- h5.mobile.fuvxie.cn/Article/585110.doc
- h5.mobile.cvsifc.cn/Article/2992.doc
- h5.mobile.puhvjy.cn/Article/89855.doc
- h5.mobile.nwbbyt.cn/Article/46327.doc
- h5.mobile.jnjpgf.cn/Article/977864.doc
- h5.mobile.jnjpgf.cn/Article/3619.doc
- h5.mobile.nwbbyt.cn/Article/4832.doc
- h5.mobile.cvsifc.cn/Article/3185695.doc
- h5.mobile.nwbbyt.cn/Article/0018196.doc
- h5.mobile.puhvjy.cn/Article/91055.doc
- h5.mobile.nwbbyt.cn/Article/4312337.doc
- h5.mobile.nzfnve.cn/Article/646235.doc
- h5.mobile.puhvjy.cn/Article/683150.doc
- h5.mobile.cvsifc.cn/Article/41845.doc
- h5.mobile.puhvjy.cn/Article/4068558.doc
- h5.mobile.fuvxie.cn/Article/708571.doc
- h5.mobile.puhvjy.cn/Article/1659051.doc
- h5.mobile.nzfnve.cn/Article/20837.doc
- h5.mobile.jnjpgf.cn/Article/3287490.doc
- h5.mobile.cvsifc.cn/Article/46906.doc
- h5.mobile.jnjpgf.cn/Article/17755.doc
- h5.mobile.jnjpgf.cn/Article/4695.doc
- h5.mobile.jnjpgf.cn/Article/4578301.doc
- h5.mobile.nzfnve.cn/Article/60345.doc
- h5.mobile.nzfnve.cn/Article/7384.doc
- h5.mobile.fuvxie.cn/Article/9987.doc
- h5.mobile.jnjpgf.cn/Article/4065.doc
- h5.mobile.jnjpgf.cn/Article/47961.doc
- h5.mobile.fuvxie.cn/Article/3345.doc
- h5.mobile.puhvjy.cn/Article/6778.doc
- h5.mobile.hcbezg.cn/Article/77393.doc
- h5.mobile.fuvxie.cn/Article/7941586.doc
- h5.mobile.fuvxie.cn/Article/52863.doc
- h5.mobile.puhvjy.cn/Article/757256.doc
- h5.mobile.nzfnve.cn/Article/48737.doc
- h5.mobile.cvsifc.cn/Article/03155.doc
- h5.mobile.cvsifc.cn/Article/0104.doc
- h5.mobile.nzfnve.cn/Article/315440.doc
- h5.mobile.hcbezg.cn/Article/567681.doc
- h5.mobile.nzfnve.cn/Article/4600.doc
- h5.mobile.jnjpgf.cn/Article/9095.doc
- h5.mobile.hcbezg.cn/Article/14242.doc
- h5.mobile.cvsifc.cn/Article/14728.doc
- h5.mobile.cvsifc.cn/Article/6013.doc
- h5.mobile.cmcvrr.cn/Article/8012729.doc
- h5.mobile.cvsifc.cn/Article/574829.doc
- h5.mobile.puhvjy.cn/Article/976996.doc
- h5.mobile.nwbbyt.cn/Article/03975.doc
- h5.mobile.cvsifc.cn/Article/09598.doc
- h5.mobile.nwbbyt.cn/Article/830736.doc
- h5.mobile.jnjpgf.cn/Article/6543898.doc
- h5.mobile.hcbezg.cn/Article/65282.doc
- h5.mobile.jnjpgf.cn/Article/12407.doc
- h5.mobile.nzfnve.cn/Article/5406597.doc
- h5.mobile.nzfnve.cn/Article/04720.doc
- h5.mobile.hcbezg.cn/Article/4387.doc
- h5.mobile.hcbezg.cn/Article/29717.doc
- h5.mobile.nwbbyt.cn/Article/4122.doc
- h5.mobile.nwbbyt.cn/Article/4207657.doc
- h5.mobile.fuvxie.cn/Article/9635.doc
- h5.mobile.cvsifc.cn/Article/13771.doc
- h5.mobile.nwbbyt.cn/Article/19550.doc
- h5.mobile.fuvxie.cn/Article/989700.doc
- h5.mobile.hcbezg.cn/Article/73872.doc
- h5.mobile.puhvjy.cn/Article/7280.doc
- h5.mobile.cvsifc.cn/Article/512398.doc
- h5.mobile.nwbbyt.cn/Article/7993.doc
- h5.mobile.fuvxie.cn/Article/39646.doc
- h5.mobile.jnjpgf.cn/Article/0549.doc
- h5.mobile.nzfnve.cn/Article/34246.doc
- h5.mobile.hcbezg.cn/Article/8197554.doc
- h5.mobile.nwbbyt.cn/Article/7015.doc
- h5.mobile.hcbezg.cn/Article/9206627.doc
- h5.mobile.nzfnve.cn/Article/6117.doc
- h5.mobile.cmcvrr.cn/Article/9558558.doc
- h5.mobile.cmcvrr.cn/Article/72915.doc
- h5.mobile.cvsifc.cn/Article/8060.doc
- h5.mobile.cvsifc.cn/Article/4869.doc
- h5.mobile.cvsifc.cn/Article/927722.doc
- h5.mobile.hcbezg.cn/Article/1589.doc
- h5.mobile.cmcvrr.cn/Article/8600876.doc
- h5.mobile.jnjpgf.cn/Article/1845.doc
- h5.mobile.nwbbyt.cn/Article/309977.doc
- h5.mobile.nzfnve.cn/Article/5347446.doc
- h5.mobile.nzfnve.cn/Article/9834.doc
- h5.mobile.puhvjy.cn/Article/86215.doc
- h5.mobile.puhvjy.cn/Article/401839.doc
- h5.mobile.cmcvrr.cn/Article/188641.doc
- h5.mobile.hcbezg.cn/Article/8189866.doc
- h5.mobile.cvsifc.cn/Article/545803.doc
- h5.mobile.fuvxie.cn/Article/71940.doc
- h5.mobile.jnjpgf.cn/Article/37052.doc
- h5.mobile.hcbezg.cn/Article/08141.doc
- h5.mobile.puhvjy.cn/Article/3137693.doc
- h5.mobile.nwbbyt.cn/Article/372402.doc
- h5.mobile.nzfnve.cn/Article/5493.doc
- h5.mobile.jnjpgf.cn/Article/0525247.doc
- h5.mobile.nwbbyt.cn/Article/4745.doc
- h5.mobile.nwbbyt.cn/Article/066629.doc
- h5.mobile.cmcvrr.cn/Article/10440.doc
- h5.mobile.hcbezg.cn/Article/75251.doc
- h5.mobile.cvsifc.cn/Article/74344.doc
- h5.mobile.nzfnve.cn/Article/7387.doc
- h5.mobile.cvsifc.cn/Article/4631.doc
- h5.mobile.jnjpgf.cn/Article/7624517.doc
- h5.mobile.nzfnve.cn/Article/0701.doc
- h5.mobile.hcbezg.cn/Article/732603.doc
- h5.mobile.fuvxie.cn/Article/142754.doc
- h5.mobile.puhvjy.cn/Article/014478.doc
- h5.mobile.fuvxie.cn/Article/3711.doc
- h5.mobile.nwbbyt.cn/Article/37455.doc
- h5.mobile.puhvjy.cn/Article/5580532.doc
- h5.mobile.nzfnve.cn/Article/4083717.doc
- h5.mobile.jnjpgf.cn/Article/77250.doc
- h5.mobile.nwbbyt.cn/Article/7990110.doc
- h5.mobile.cmcvrr.cn/Article/9009516.doc
- h5.mobile.nwbbyt.cn/Article/0519735.doc
- h5.mobile.puhvjy.cn/Article/0307022.doc

## 项目结构

```
h5mobile-docs-index/
├── README.md                           # 项目总体说明与索引清单入口
├── LICENSE                             # MIT 许可证文件
├── requirements.txt                    # Python 依赖声明（requests, lxml, pytest）
├── Makefile                            # 自动化任务聚合（check, lint, update, clean）
├── docs/                               # 完整文档目录
│   ├── introduction.md                 # 基础入门：项目背景与快速上手
│   ├── advanced/                       # 进阶使用子目录
│   │   └── usage.md                    # 过滤、子集生成与自定义输出格式
│   ├── operations/                     # 运维管理子目录
│   │   └── maintenance.md              # 链接健康检查、失效处理与监控配置
│   └── governance/                     # 治理规范子目录
│       └── resource-standards.md       # 资源收录标准与变更审批流程
├── scripts/                            # 可执行辅助脚本目录
│   ├── generate_index.py               # 索引清单生成主脚本
│   ├── validate_links.py               # 链接格式校验与重复检测脚本
│   ├── cron_example.sh                 # 每日自动更新示例 cron 任务
│   └── utils/                          # 脚本公用工具模块
│       ├── __init__.py
│       ├── fetcher.py                  # 封装 HTTP 请求与重试逻辑
│       └── parser.py                   # 解析原始资源列表与格式化输出
├── input/                              # 原始数据输入目录
│   └── resources.txt                   # 维护者手工维护的原始 URL 列表文件
├── output/                             # 生成结果输出目录
│   ├── index.md                        # 最终发布的完整索引清单
│   └── index.json                      # JSON 格式索引，供其他系统消费
└── tests/                              # 单元测试与集成测试目录
    ├── test_parser.py                  # 针对解析器的测试用例
    └── test_validator.py               # 针对链接校验逻辑的测试用例
```

## 贡献指南

我们欢迎并鼓励社区贡献，包括但不限于新增资源链接、更新失效地址、优化脚本逻辑与完善文档。请按照以下标准流程提交贡献。

第一，在 input/resources.txt 文件中按行追加或修改资源 URL，每个 URL 独占一行，格式必须为 {domain}/Article/{id}.doc，其中 domain 为已收录的合法域名之一，id 为数字字符串。

第二，运行本地自检命令 make check 以执行格式校验、重复检测与基础可达性测试。确保所有新增或修改的链接均通过校验，无语法错误与重复条目。

第三，编写或更新对应的文档说明。若新增域名，需同步更新 docs/governance/resource-standards.md 中的收录域名列表；若调整索引生成逻辑，需补充对应单元测试至 tests/ 目录。

第四，提交 Pull Request 时，请在描述中说明变更动机、影响范围以及是否涉及破坏性变更。PR 标题应遵循 `[type]: short description` 格式，其中 type 为 add、update、fix 或 docs。

第五，等待至少一名项目维护者进行 Code Review。在 Review 通过且所有 CI 检查（包括链接校验、单元测试与格式检查）均为绿色后，由维护者合并至主分支。

## 常见问题

问题：资源列表中的部分链接返回 404 或超时，应如何处理？

回答：首先确认链接格式是否严格遵循 {domain}/Article/{id}.doc 规范。若格式无误但仍不可达，可能是源站临时维护或文档已迁移。请使用 scripts/validate_links.py 脚本进行批量检测，并根据输出结果区分临时性错误与永久失效。对于永久失效链接，请在 input/resources.txt 中注释或删除该行，并在 PR 描述中注明移除原因。

问题：如何添加新的域名来源，例如新增一个 h5.mobile.newexample.cn 站点？

回答：请先在 docs/governance/resource-standards.md 中更新允许域名列表，并说明该域名的所属团队与用途。随后在 input/resources.txt 中新增该域名下的资源链接，运行 make check 确保格式正确。提交 PR 时需附带新增域名的简要背景说明，以便维护者评估收录合理性。

问题：索引清单包含 250 个链接，更新时是否有批量操作的最佳实践？

回答：建议采用增量更新策略，即每次提交仅处理一个明确主题或来源域名的资源变更，避免单次 PR 规模过大。若需大规模重构，请先在 issue 中提出计划并与维护者沟通。可使用 scripts/generate_index.py 的 --filter 参数对特定域名进行局部生成测试，验证无误后再合并全量更新。

## 许可证

MIT License

Copyright (c) 2026 H5Mobile Docs Index Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:22

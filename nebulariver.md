# DocArchive Hub

DocArchive Hub 是一个面向技术文档、学术资料、行业报告及历史档案的轻量级外链聚合与导航系统。该项目定位于为研究人员、数据归档者、技术文档工程师以及信息检索人员提供一个集中式的文档资源入口，通过结构化分类和快速检索机制，帮助用户从海量分散的存储节点中精准定位目标文件。

项目不直接存储任何实体文件，而是作为一份可公开访问的资源索引清单，对一批历史遗留或分布式存储的文档链接进行规范化整理。通过本项目提供的目录树与分类映射，用户可以快速理解这批资源的分布规律，并借助外部下载工具或离线抓取脚本进行批量处理。DocArchive Hub 适用于搭建个人知识库的底层资源清单、企业内部文档资产盘点、或学术开源项目的数据附录管理。

## 功能概览

- 海量链接清单聚合：单批次支持收录超过 200 个外部文档链接，并提供完整的 Markdown 列表输出，便于机器读取和人工审核。
- 多维度结构映射：通过 ASCII 目录树与分类索引，将扁平的 URL 列表映射为层级化的虚拟文件系统，提升资源浏览的可理解性。
- 快速部署与运行：基于静态 Markdown 渲染，无需数据库或后端服务，克隆即用，适配 GitHub Pages、VuePress、Docsify 等常见文档框架。
- 资源状态标记扩展：支持用户自定义标签（如待下载、已归档、失效检测），通过 Issue 或 PR 维护资源活性。
- 跨域检索支持：配合浏览器书签工具或简单的 grep 命令，可实现基于文档编号、域名特征或文件名称的快速过滤。
- 标准化文档导航：内置文档导航表格，按技术层面分门别类，帮助新贡献者快速理解项目组织逻辑。
- 贡献流程自动化：提供标准化的贡献者指南，支持通过 Pull Request 新增链接、更新描述或标记失效资源。
- 许可证合规：采用 MIT 开源许可证，允许自由使用、修改和分发，仅需保留版权声明。

## 应用场景

- 学术研究辅助：研究生或科研人员在撰写文献综述时，可将本项目作为参考文献附录的原始素材库，通过链接清单快速定位不同来源的 PDF 或 DOC 文档，减少重复检索时间。
- 企业文档资产盘点：企业内部的知识管理团队可以利用本项目作为基础模板，将散落在各业务系统的历史合同、技术方案、会议记录等 DOC 文件链接统一纳入索引，形成一份可维护的资产目录。
- 开源项目数据附录：开源软件项目在发布版本时，常需附带测试报告、性能基准数据或用户手册。DocArchive Hub 可作为此类附属文档的导航页，避免将大文件直接放入代码仓库，保持仓库轻量化。
- 个人离线知识库构建：个人开发者或数字极客可通过本项目提供的 URL 列表，配合 wget 或 aria2 等批量下载工具，构建属于自己的离线文档库，用于无网络环境下的资料查阅。

## 快速开始

以下步骤帮助您在本地快速启动 DocArchive Hub 实例，浏览并管理资源清单。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/docarchive-hub.git

# 进入项目目录
cd docarchive-hub

# 安装依赖（若使用静态生成器，如 Hugo 或 MkDocs，请参照对应文档）
# 此处以 Python 内置 HTTP 服务器为例，用于本地预览 Markdown 渲染效果
pip install mkdocs
mkdocs build
mkdocs serve

# 或者直接使用 VS Code 的 Markdown 预览插件打开 README.md 和资源列表文件
```

若您仅需查看和编辑资源列表，无需安装任何依赖，直接使用任何文本编辑器打开 `resources.md` 或本文件即可。

## 安装要求

| 依赖项 | 必需 | 说明 |
|--------|------|------|
| Git | 是 | 用于克隆仓库和版本控制，推荐 2.25 及以上版本 |
| Python 3.6+ | 否 | 仅在运行本地预览服务器或脚本解析时可选 |
| MkDocs | 否 | 用于生成静态站点，若使用其他静态生成器可替换 |
| 现代 Web 浏览器 | 否 | 用于预览渲染后的文档界面，如 Chrome/Firefox/Edge |
| 文本编辑器 | 是 | 用于编辑 Markdown 文件，推荐 VSCode 或 Notepad++ |
| curl/wget | 否 | 用于批量测试链接可达性或下载文件，非必需 |

## 文档导航

| 层面 | 目录/文件 | 回答的问题 |
|------|-----------|------------|
| 入门层 | `README.md` | 项目是什么？如何快速开始？有哪些功能？ |
| 资源层 | `resources.md` 或 本文件「资源列表」章节 | 具体有哪些文档链接？链接的原始地址是什么？ |
| 维护层 | `CONTRIBUTING.md` | 如何新增链接？如何报告失效链接？审核流程是什么？ |
| 结构层 | `PROJECT_STRUCTURE.md` 或 本章节 | 项目文件和目录是如何组织的？虚拟目录树如何映射资源？ |

## 资源列表

- h5.mobile.cvsifc.cn/Article/371370.doc
- h5.mobile.nzfnve.cn/Article/595287.doc
- h5.mobile.hcbezg.cn/Article/55221.doc
- h5.mobile.jnjpgf.cn/Article/1938965.doc
- h5.mobile.puhvjy.cn/Article/00372.doc
- h5.mobile.hcbezg.cn/Article/686819.doc
- h5.mobile.fuvxie.cn/Article/948931.doc
- h5.mobile.puhvjy.cn/Article/27862.doc
- h5.mobile.nzfnve.cn/Article/2613882.doc
- h5.mobile.fuvxie.cn/Article/163195.doc
- h5.mobile.jnjpgf.cn/Article/817473.doc
- h5.mobile.cmcvrr.cn/Article/153440.doc
- h5.mobile.puhvjy.cn/Article/843456.doc
- h5.mobile.nzfnve.cn/Article/113591.doc
- h5.mobile.fuvxie.cn/Article/941785.doc
- h5.mobile.jnjpgf.cn/Article/0539376.doc
- h5.mobile.puhvjy.cn/Article/039263.doc
- h5.mobile.jnjpgf.cn/Article/3357.doc
- h5.mobile.fuvxie.cn/Article/2538039.doc
- h5.mobile.cvsifc.cn/Article/9718369.doc
- h5.mobile.cvsifc.cn/Article/9730.doc
- h5.mobile.nzfnve.cn/Article/635519.doc
- h5.mobile.cvsifc.cn/Article/85207.doc
- h5.mobile.nwbbyt.cn/Article/7773.doc
- h5.mobile.nzfnve.cn/Article/5955740.doc
- h5.mobile.puhvjy.cn/Article/33923.doc
- h5.mobile.nwbbyt.cn/Article/6592.doc
- h5.mobile.cvsifc.cn/Article/43151.doc
- h5.mobile.jnjpgf.cn/Article/51086.doc
- h5.mobile.cmcvrr.cn/Article/59243.doc
- h5.mobile.nwbbyt.cn/Article/33332.doc
- h5.mobile.cvsifc.cn/Article/035022.doc
- h5.mobile.hcbezg.cn/Article/3129.doc
- h5.mobile.hcbezg.cn/Article/3107508.doc
- h5.mobile.hcbezg.cn/Article/8914.doc
- h5.mobile.puhvjy.cn/Article/22753.doc
- h5.mobile.fuvxie.cn/Article/3896408.doc
- h5.mobile.nzfnve.cn/Article/4682.doc
- h5.mobile.fuvxie.cn/Article/155435.doc
- h5.mobile.cvsifc.cn/Article/0793728.doc
- h5.mobile.hcbezg.cn/Article/849408.doc
- h5.mobile.nwbbyt.cn/Article/0153156.doc
- h5.mobile.nwbbyt.cn/Article/89283.doc
- h5.mobile.fuvxie.cn/Article/4825126.doc
- h5.mobile.nwbbyt.cn/Article/97555.doc
- h5.mobile.nwbbyt.cn/Article/2751.doc
- h5.mobile.cvsifc.cn/Article/4841952.doc
- h5.mobile.hcbezg.cn/Article/155842.doc
- h5.mobile.hcbezg.cn/Article/60176.doc
- h5.mobile.nzfnve.cn/Article/2400523.doc
- h5.mobile.nwbbyt.cn/Article/675434.doc
- h5.mobile.cvsifc.cn/Article/20580.doc
- h5.mobile.jnjpgf.cn/Article/8321.doc
- h5.mobile.fuvxie.cn/Article/193325.doc
- h5.mobile.nwbbyt.cn/Article/8025153.doc
- h5.mobile.cmcvrr.cn/Article/1276.doc
- h5.mobile.nwbbyt.cn/Article/6580.doc
- h5.mobile.nzfnve.cn/Article/479841.doc
- h5.mobile.fuvxie.cn/Article/5949680.doc
- h5.mobile.hcbezg.cn/Article/67894.doc
- h5.mobile.jnjpgf.cn/Article/8157.doc
- h5.mobile.jnjpgf.cn/Article/75568.doc
- h5.mobile.cmcvrr.cn/Article/82738.doc
- h5.mobile.puhvjy.cn/Article/68581.doc
- h5.mobile.hcbezg.cn/Article/4923.doc
- h5.mobile.fuvxie.cn/Article/52989.doc
- h5.mobile.cvsifc.cn/Article/6295.doc
- h5.mobile.nzfnve.cn/Article/1792.doc
- h5.mobile.nzfnve.cn/Article/1799624.doc
- h5.mobile.nwbbyt.cn/Article/234013.doc
- h5.mobile.puhvjy.cn/Article/2935752.doc
- h5.mobile.fuvxie.cn/Article/8907.doc
- h5.mobile.cvsifc.cn/Article/2137014.doc
- h5.mobile.hcbezg.cn/Article/0930014.doc
- h5.mobile.cvsifc.cn/Article/301912.doc
- h5.mobile.nwbbyt.cn/Article/8442.doc
- h5.mobile.jnjpgf.cn/Article/6762886.doc
- h5.mobile.nwbbyt.cn/Article/3364792.doc
- h5.mobile.fuvxie.cn/Article/4974131.doc
- h5.mobile.puhvjy.cn/Article/758036.doc
- h5.mobile.puhvjy.cn/Article/1431480.doc
- h5.mobile.cmcvrr.cn/Article/76793.doc
- h5.mobile.fuvxie.cn/Article/0218554.doc
- h5.mobile.cvsifc.cn/Article/60320.doc
- h5.mobile.hcbezg.cn/Article/2079821.doc
- h5.mobile.jnjpgf.cn/Article/7784.doc
- h5.mobile.hcbezg.cn/Article/949534.doc
- h5.mobile.jnjpgf.cn/Article/7420.doc
- h5.mobile.cvsifc.cn/Article/732330.doc
- h5.mobile.nwbbyt.cn/Article/47173.doc
- h5.mobile.puhvjy.cn/Article/4673.doc
- h5.mobile.cvsifc.cn/Article/18622.doc
- h5.mobile.cmcvrr.cn/Article/48193.doc
- h5.mobile.jnjpgf.cn/Article/30634.doc
- h5.mobile.jnjpgf.cn/Article/1218093.doc
- h5.mobile.fuvxie.cn/Article/7314101.doc
- h5.mobile.jnjpgf.cn/Article/18362.doc
- h5.mobile.jnjpgf.cn/Article/45600.doc
- h5.mobile.fuvxie.cn/Article/8340246.doc
- h5.mobile.cvsifc.cn/Article/689603.doc
- h5.mobile.fuvxie.cn/Article/2167174.doc
- h5.mobile.fuvxie.cn/Article/295237.doc
- h5.mobile.nwbbyt.cn/Article/5848.doc
- h5.mobile.nzfnve.cn/Article/3494.doc
- h5.mobile.nwbbyt.cn/Article/049138.doc
- h5.mobile.cmcvrr.cn/Article/34436.doc
- h5.mobile.nwbbyt.cn/Article/17026.doc
- h5.mobile.nzfnve.cn/Article/4315.doc
- h5.mobile.puhvjy.cn/Article/5751732.doc
- h5.mobile.hcbezg.cn/Article/5908623.doc
- h5.mobile.hcbezg.cn/Article/5599.doc
- h5.mobile.nwbbyt.cn/Article/9173.doc
- h5.mobile.cvsifc.cn/Article/135815.doc
- h5.mobile.fuvxie.cn/Article/3766252.doc
- h5.mobile.hcbezg.cn/Article/908408.doc
- h5.mobile.hcbezg.cn/Article/0409.doc
- h5.mobile.jnjpgf.cn/Article/2800.doc
- h5.mobile.cmcvrr.cn/Article/60572.doc
- h5.mobile.puhvjy.cn/Article/0837.doc
- h5.mobile.fuvxie.cn/Article/5801370.doc
- h5.mobile.cmcvrr.cn/Article/74332.doc
- h5.mobile.nwbbyt.cn/Article/0996.doc
- h5.mobile.fuvxie.cn/Article/2779.doc
- h5.mobile.fuvxie.cn/Article/713624.doc
- h5.mobile.nwbbyt.cn/Article/201512.doc
- h5.mobile.cmcvrr.cn/Article/379361.doc
- h5.mobile.jnjpgf.cn/Article/3714.doc
- h5.mobile.cmcvrr.cn/Article/98536.doc
- h5.mobile.jnjpgf.cn/Article/1890194.doc
- h5.mobile.nzfnve.cn/Article/3945.doc
- h5.mobile.puhvjy.cn/Article/44589.doc
- h5.mobile.hcbezg.cn/Article/8463.doc
- h5.mobile.nzfnve.cn/Article/98333.doc
- h5.mobile.hcbezg.cn/Article/20816.doc
- h5.mobile.fuvxie.cn/Article/1851282.doc
- h5.mobile.cmcvrr.cn/Article/5302236.doc
- h5.mobile.nzfnve.cn/Article/1825995.doc
- h5.mobile.nwbbyt.cn/Article/9759.doc
- h5.mobile.fuvxie.cn/Article/67269.doc
- h5.mobile.cmcvrr.cn/Article/45779.doc
- h5.mobile.nwbbyt.cn/Article/16188.doc
- h5.mobile.puhvjy.cn/Article/3731.doc
- h5.mobile.nzfnve.cn/Article/12506.doc
- h5.mobile.fuvxie.cn/Article/3340.doc
- h5.mobile.puhvjy.cn/Article/7366094.doc
- h5.mobile.nwbbyt.cn/Article/8847.doc
- h5.mobile.puhvjy.cn/Article/0283276.doc
- h5.mobile.puhvjy.cn/Article/1334.doc
- h5.mobile.fuvxie.cn/Article/91895.doc
- h5.mobile.jnjpgf.cn/Article/1679269.doc
- h5.mobile.fuvxie.cn/Article/2893.doc
- h5.mobile.fuvxie.cn/Article/62339.doc
- h5.mobile.cmcvrr.cn/Article/67973.doc
- h5.mobile.nwbbyt.cn/Article/0293.doc
- h5.mobile.nwbbyt.cn/Article/83290.doc
- h5.mobile.hcbezg.cn/Article/98060.doc
- h5.mobile.hcbezg.cn/Article/3764.doc
- h5.mobile.hcbezg.cn/Article/71431.doc
- h5.mobile.hcbezg.cn/Article/64451.doc
- h5.mobile.puhvjy.cn/Article/8740441.doc
- h5.mobile.nwbbyt.cn/Article/5728398.doc
- h5.mobile.nzfnve.cn/Article/86476.doc
- h5.mobile.puhvjy.cn/Article/3089.doc
- h5.mobile.jnjpgf.cn/Article/389790.doc
- h5.mobile.hcbezg.cn/Article/7059.doc
- h5.mobile.nwbbyt.cn/Article/28146.doc
- h5.mobile.jnjpgf.cn/Article/46616.doc
- h5.mobile.nzfnve.cn/Article/07012.doc
- h5.mobile.puhvjy.cn/Article/21118.doc
- h5.mobile.jnjpgf.cn/Article/353731.doc
- h5.mobile.jnjpgf.cn/Article/46613.doc
- h5.mobile.fuvxie.cn/Article/247055.doc
- h5.mobile.jnjpgf.cn/Article/1463647.doc
- h5.mobile.jnjpgf.cn/Article/1137392.doc
- h5.mobile.nwbbyt.cn/Article/4519.doc
- h5.mobile.nwbbyt.cn/Article/818522.doc
- h5.mobile.nzfnve.cn/Article/541012.doc
- h5.mobile.fuvxie.cn/Article/121606.doc
- h5.mobile.fuvxie.cn/Article/5397207.doc
- h5.mobile.cvsifc.cn/Article/93391.doc
- h5.mobile.hcbezg.cn/Article/87611.doc
- h5.mobile.hcbezg.cn/Article/4323595.doc
- h5.mobile.nzfnve.cn/Article/167781.doc
- h5.mobile.puhvjy.cn/Article/88057.doc
- h5.mobile.nwbbyt.cn/Article/22997.doc
- h5.mobile.cvsifc.cn/Article/44307.doc
- h5.mobile.hcbezg.cn/Article/0273487.doc
- h5.mobile.fuvxie.cn/Article/83081.doc
- h5.mobile.cvsifc.cn/Article/1990489.doc
- h5.mobile.cmcvrr.cn/Article/35093.doc
- h5.mobile.nwbbyt.cn/Article/818633.doc
- h5.mobile.nzfnve.cn/Article/426997.doc
- h5.mobile.hcbezg.cn/Article/6561319.doc
- h5.mobile.cvsifc.cn/Article/2782.doc
- h5.mobile.puhvjy.cn/Article/474787.doc
- h5.mobile.cmcvrr.cn/Article/0988323.doc
- h5.mobile.nwbbyt.cn/Article/8862990.doc
- h5.mobile.jnjpgf.cn/Article/789063.doc
- h5.mobile.nwbbyt.cn/Article/1743325.doc
- h5.mobile.cmcvrr.cn/Article/96777.doc
- h5.mobile.cmcvrr.cn/Article/1936.doc
- h5.mobile.cmcvrr.cn/Article/93089.doc
- h5.mobile.fuvxie.cn/Article/9920.doc
- h5.mobile.cvsifc.cn/Article/7504.doc
- h5.mobile.jnjpgf.cn/Article/537668.doc
- h5.mobile.puhvjy.cn/Article/451099.doc
- h5.mobile.hcbezg.cn/Article/1218.doc
- h5.mobile.nzfnve.cn/Article/17802.doc
- h5.mobile.fuvxie.cn/Article/708514.doc
- h5.mobile.nwbbyt.cn/Article/93790.doc
- h5.mobile.cvsifc.cn/Article/4876.doc
- h5.mobile.cmcvrr.cn/Article/486564.doc
- h5.mobile.cvsifc.cn/Article/8070540.doc
- h5.mobile.nwbbyt.cn/Article/5301.doc
- h5.mobile.nwbbyt.cn/Article/5923270.doc
- h5.mobile.puhvjy.cn/Article/1753760.doc
- h5.mobile.nzfnve.cn/Article/2562.doc
- h5.mobile.fuvxie.cn/Article/6515.doc
- h5.mobile.cvsifc.cn/Article/383927.doc
- h5.mobile.cvsifc.cn/Article/9154.doc
- h5.mobile.cmcvrr.cn/Article/914497.doc
- h5.mobile.jnjpgf.cn/Article/870219.doc
- h5.mobile.jnjpgf.cn/Article/9324.doc
- h5.mobile.nwbbyt.cn/Article/4093173.doc
- h5.mobile.fuvxie.cn/Article/866191.doc
- h5.mobile.nwbbyt.cn/Article/64948.doc
- h5.mobile.jnjpgf.cn/Article/6349.doc
- h5.mobile.cvsifc.cn/Article/676550.doc
- h5.mobile.nzfnve.cn/Article/8291966.doc
- h5.mobile.jnjpgf.cn/Article/4433.doc
- h5.mobile.puhvjy.cn/Article/1906432.doc
- h5.mobile.nzfnve.cn/Article/142715.doc
- h5.mobile.fuvxie.cn/Article/5953294.doc
- h5.mobile.nwbbyt.cn/Article/8151828.doc
- h5.mobile.cmcvrr.cn/Article/0815.doc
- h5.mobile.fuvxie.cn/Article/4148.doc
- h5.mobile.nwbbyt.cn/Article/679214.doc
- h5.mobile.puhvjy.cn/Article/6996321.doc
- h5.mobile.hcbezg.cn/Article/942020.doc
- h5.mobile.nwbbyt.cn/Article/9070692.doc
- h5.mobile.cmcvrr.cn/Article/1632.doc
- h5.mobile.cmcvrr.cn/Article/72656.doc
- h5.mobile.puhvjy.cn/Article/53341.doc
- h5.mobile.hcbezg.cn/Article/7707980.doc
- h5.mobile.nzfnve.cn/Article/38240.doc
- h5.mobile.hcbezg.cn/Article/3441668.doc
- h5.mobile.jnjpgf.cn/Article/038804.doc
- h5.mobile.fuvxie.cn/Article/995304.doc
- h5.mobile.nzfnve.cn/Article/14375.doc
- h5.mobile.cvsifc.cn/Article/4681321.doc

## 项目结构

```
docarchive-hub/
├── README.md                 # 项目总览、快速开始、功能与场景说明
├── resources.md              # 完整资源列表，按批次分类（当前为第89/160批）
├── docs/                     # 文档站点源码目录
│   ├── index.md              # 文档站点首页
│   ├── navigation.md         # 导航地图与分类索引
│   └── maintenance.md        # 维护指南，包括链接检测脚本用法
├── scripts/                  # 辅助脚本目录
│   ├── check_links.py        # 批量检测链接可用性的 Python 脚本
│   └── generate_stats.sh     # 生成资源统计报告（总数、域名分布）
├── .github/                  # GitHub 社区配置文件
│   └── ISSUE_TEMPLATE/       # 问题报告模板（链接失效、新增建议）
│       └── link_report.md
├── CONTRIBUTING.md           # 贡献者协议与详细操作步骤
├── LICENSE                   # MIT 许可证全文
└── CHANGELOG.md              # 版本更新日志，记录每批资源的增删变动
```

## 贡献指南

1. 复刻本仓库至个人账户，并在本地克隆复刻后的副本，确保同步最新主分支代码。
2. 在 `resources.md` 或对应批次的资源列表中新增或修改 URL，若为新增链接，请保持格式一致（每行一个裸链接，不加任何前缀修饰）。
3. 若标记链接失效，请将其移动至 `deprecated_links.md` 文件，并注明检测日期与失效状态（如 404、超时等）。
4. 提交变更前，请运行 `scripts/check_links.py` 脚本对新加入的链接进行基础连通性测试，确保无严重错误。
5. 创建 Pull Request 至主仓库，在 PR 描述中清晰说明变更类型（新增/删除/更新）及影响范围，等待维护者审核合并。

## 常见问题

Q: 项目中的链接无法直接访问，该如何处理？

A: 本项目仅作为资源索引，不保证所有外部链接永久有效。若遇到无法访问的链接，您可以通过提交 Issue 或 Pull Request 将其标记为失效。同时，建议使用 `scripts/check_links.py` 脚本定期检测本地列表的活性。

Q: 我可以将本项目用于商业项目或内部文档系统吗？

A: 可以。本项目采用 MIT 许可证，允许自由使用、修改和分发，包括商业用途。您只需保留原始版权声明即可。

Q: 如何新增一批自己的文档链接？

A: 您可以直接编辑 `resources.md` 文件，按照现有格式追加新的 URL 列表。若新增数量较大，建议创建新的批次章节（如第 161/160 批），并同步更新 `README.md` 中的批次说明。

## 许可证

MIT License

Copyright (c) 2026 DocArchive Hub Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

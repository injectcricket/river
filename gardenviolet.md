# LinkVault 技术资源聚合导航站

LinkVault 是一个面向开发者与技术研究人员的结构化外链资源聚合平台，专注于对散落于各技术博客、知识库与个人站点中的高质量文章进行索引、分类与持久化访问。项目定位于解决技术资料分散、链接失效快、检索成本高的问题，通过统一的资源清单与轻量级元数据管理，帮助用户快速定位特定主题下的深度内容。本仓库本身不存储任何文章内容，仅作为导航索引层，所有资源均指向原始发布地址。

## 功能概览

**按批次归类的资源清单**：所有外链按收录批次与序号组织，支持批量导入与版本追溯。

**原始 URL 直链暴露**：每个资源条目均保留完整的原始访问地址，杜绝二次跳转与短链缩略，确保链接透明可审计。

**文章级元数据占位**：预留文章标题、作者、发布时间、标签等扩展字段，便于后续接入自动化抓取流程。

**静态站点友好结构**：基于 Markdown 与纯文本构建，无需数据库，可直接托管于任何支持静态页面的服务。

**命令行快速检索**：内置 grep/ripgrep 友好的目录结构，支持本地离线关键词查找。

**多域名源站聚合**：当前覆盖 puhvjy.cn、cmcvrr.cn、nwbbyt.cn、fuvxie.cn、nzfnve.cn、jnjpgf.cn、hcbezg.cn、cvsifc.cn 等多个内容源站。

**批次进度追踪**：提供批次编号（当前第 77/160 批）与资源总数统计，方便贡献者了解收录进度。

**零依赖部署**：项目本身不含任何后端代码或客户端脚本，开箱即用。

## 应用场景

技术团队内部知识库建设：团队技术负责人可将 LinkVault 作为基础索引，定期同步收录团队博客与外部参考文章，形成可共享的阅读清单。

个人开发者离线阅读准备：用户可通过克隆本仓库，在通勤或无网络环境下使用本地编辑器浏览资源列表，预先筛选感兴趣的文章。

开源项目文档外链附录：开源项目维护者可将 LinkVault 中的相关批次链接作为项目 README 的扩展参考资料，补充背景阅读材料。

技术社区内容推荐系统冷启动：社区运营人员可利用本项目的结构化 URL 列表作为初始种子，构建文章推荐算法的基础数据集。

学术文献综述素材收集：研究人员可快速从同一域名下的多个文章编号中，按规律提取系列内容，辅助文献调研。

## 快速开始

以下命令适用于 Linux、macOS 及 Windows WSL 环境。

```bash
# 克隆仓库
git clone https://github.com/your-org/linkvault.git
cd linkvault

# 安装依赖（无外部依赖，仅创建本地索引目录）
mkdir -p batches meta logs

# 初始化批次目录结构
for i in $(seq -f "%03g" 1 160); do
  mkdir -p "batches/$i"
done

# 将本批次资源列表导入对应批次目录
cat > batches/077/links.txt << 'EOF'
https://www.read.puhvjy.cn/Article/00026.shtml
https://www.read.cmcvrr.cn/Article/8983.shtml
...（完整列表见资源列表章节）
EOF

# 运行本地检索示例
grep -r "puhvjy" batches/077/
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Git | 2.20 及以上 | 用于克隆仓库和提交更新 |
| Bash | 4.0 及以上 | 用于运行辅助脚本（可选） |
| GNU Coreutils | 8.0 及以上 | 提供基础文件操作命令 |
| curl | 7.0 及以上 | 用于远程资源可达性检测（可选） |
| ripgrep | 13.0 及以上 | 用于高效全文检索（推荐） |
| 磁盘空间 | 10 MB 以上 | 仅存储文本链接和元数据，无大文件 |
| 操作系统 | Linux / macOS / WSL | 未在原生 Windows cmd 环境下测试 |
| 网络访问 | 外网 | 访问原始资源地址时需要 |
| Python（可选） | 3.8 及以上 | 用于运行元数据解析辅助模块 |

## 文档导航

| 层面 | 目录/文件 | 回答的问题 |
|------|-----------|------------|
| 批次总览 | batches/README.md | 当前已收录多少批次？每批次的收录时间范围是什么？ |
| 单批详情 | batches/{NNN}/links.txt | 某一批次具体包含哪些 URL？编号规则如何？ |
| 元数据定义 | meta/schema.yaml | 每个链接条目支持哪些扩展字段？数据格式如何约束？ |
| 域名索引 | meta/domains.txt | 当前覆盖哪些源站域名？各域名下收录了多少文章？ |
| 贡献流程 | CONTRIBUTING.md | 如何新增批次？如何修正失效链接？审核流程是什么？ |
| 日志归档 | logs/ | 每次更新操作的记录存放在哪里？如何追溯变更历史？ |

## 资源列表

- https://www.read.puhvjy.cn/Article/00026.shtml
- https://www.read.cmcvrr.cn/Article/8983.shtml
- https://www.read.nwbbyt.cn/Article/7560532.shtml
- https://www.read.fuvxie.cn/Article/5629397.shtml
- https://www.read.nzfnve.cn/Article/247832.shtml
- https://www.read.jnjpgf.cn/Article/69697.shtml
- https://www.read.cvsifc.cn/Article/50695.shtml
- https://www.read.cmcvrr.cn/Article/749442.shtml
- https://www.read.fuvxie.cn/Article/024786.shtml
- https://www.read.fuvxie.cn/Article/6213.shtml
- https://www.read.hcbezg.cn/Article/94282.shtml
- https://www.read.cmcvrr.cn/Article/10840.shtml
- https://www.read.cvsifc.cn/Article/905766.shtml
- https://www.read.nzfnve.cn/Article/880298.shtml
- https://www.read.cmcvrr.cn/Article/2126.shtml
- https://www.read.cvsifc.cn/Article/929729.shtml
- https://www.read.cmcvrr.cn/Article/9213.shtml
- https://www.read.puhvjy.cn/Article/9991.shtml
- https://www.read.puhvjy.cn/Article/0426649.shtml
- https://www.read.cvsifc.cn/Article/23825.shtml
- https://www.read.cmcvrr.cn/Article/7395382.shtml
- https://www.read.cmcvrr.cn/Article/185952.shtml
- https://www.read.puhvjy.cn/Article/7733.shtml
- https://www.read.cmcvrr.cn/Article/53479.shtml
- https://www.read.jnjpgf.cn/Article/260381.shtml
- https://www.read.cvsifc.cn/Article/091802.shtml
- https://www.read.cvsifc.cn/Article/318306.shtml
- https://www.read.hcbezg.cn/Article/38031.shtml
- https://www.read.fuvxie.cn/Article/443124.shtml
- https://www.read.nzfnve.cn/Article/953454.shtml
- https://www.read.jnjpgf.cn/Article/526859.shtml
- https://www.read.cmcvrr.cn/Article/062060.shtml
- https://www.read.jnjpgf.cn/Article/6336.shtml
- https://www.read.nzfnve.cn/Article/0464.shtml
- https://www.read.puhvjy.cn/Article/4853580.shtml
- https://www.read.jnjpgf.cn/Article/8729.shtml
- https://www.read.cmcvrr.cn/Article/088671.shtml
- https://www.read.jnjpgf.cn/Article/941861.shtml
- https://www.read.nzfnve.cn/Article/49548.shtml
- https://www.read.jnjpgf.cn/Article/308733.shtml
- https://www.read.puhvjy.cn/Article/37359.shtml
- https://www.read.nwbbyt.cn/Article/57270.shtml
- https://www.read.cmcvrr.cn/Article/119934.shtml
- https://www.read.nwbbyt.cn/Article/3055239.shtml
- https://www.read.puhvjy.cn/Article/9748.shtml
- https://www.read.cvsifc.cn/Article/8848788.shtml
- https://www.read.cvsifc.cn/Article/2888179.shtml
- https://www.read.nzfnve.cn/Article/3456.shtml
- https://www.read.cvsifc.cn/Article/3971445.shtml
- https://www.read.cvsifc.cn/Article/7826756.shtml
- https://www.read.cmcvrr.cn/Article/5613757.shtml
- https://www.read.jnjpgf.cn/Article/16137.shtml
- https://www.read.cvsifc.cn/Article/4897336.shtml
- https://www.read.puhvjy.cn/Article/6387.shtml
- https://www.read.jnjpgf.cn/Article/0630.shtml
- https://www.read.nzfnve.cn/Article/491523.shtml
- https://www.read.cmcvrr.cn/Article/55106.shtml
- https://www.read.nwbbyt.cn/Article/8345604.shtml
- https://www.read.jnjpgf.cn/Article/46903.shtml
- https://www.read.hcbezg.cn/Article/9032474.shtml
- https://www.read.cmcvrr.cn/Article/14580.shtml
- https://www.read.puhvjy.cn/Article/46699.shtml
- https://www.read.nzfnve.cn/Article/5694.shtml
- https://www.read.cvsifc.cn/Article/5433020.shtml
- https://www.read.cmcvrr.cn/Article/3052.shtml
- https://www.read.cmcvrr.cn/Article/397387.shtml
- https://www.read.fuvxie.cn/Article/60124.shtml
- https://www.read.fuvxie.cn/Article/4561.shtml
- https://www.read.puhvjy.cn/Article/7876211.shtml
- https://www.read.hcbezg.cn/Article/0258.shtml
- https://www.read.cmcvrr.cn/Article/12165.shtml
- https://www.read.puhvjy.cn/Article/27373.shtml
- https://www.read.cvsifc.cn/Article/332412.shtml
- https://www.read.nwbbyt.cn/Article/1530.shtml
- https://www.read.nzfnve.cn/Article/53939.shtml
- https://www.read.cvsifc.cn/Article/4343655.shtml
- https://www.read.hcbezg.cn/Article/3974.shtml
- https://www.read.nzfnve.cn/Article/164001.shtml
- https://www.read.cvsifc.cn/Article/4248043.shtml
- https://www.read.nzfnve.cn/Article/3546.shtml
- https://www.read.cvsifc.cn/Article/3602543.shtml
- https://www.read.puhvjy.cn/Article/9334.shtml
- https://www.read.nwbbyt.cn/Article/0948832.shtml
- https://www.read.nwbbyt.cn/Article/72012.shtml
- https://www.read.cmcvrr.cn/Article/65371.shtml
- https://www.read.cmcvrr.cn/Article/02018.shtml
- https://www.read.nwbbyt.cn/Article/7153599.shtml
- https://www.read.nwbbyt.cn/Article/9676101.shtml
- https://www.read.hcbezg.cn/Article/091774.shtml
- https://www.read.jnjpgf.cn/Article/993372.shtml
- https://www.read.nwbbyt.cn/Article/9626225.shtml
- https://www.read.hcbezg.cn/Article/89560.shtml
- https://www.read.cmcvrr.cn/Article/9619.shtml
- https://www.read.puhvjy.cn/Article/89072.shtml
- https://www.read.jnjpgf.cn/Article/0268072.shtml
- https://www.read.cvsifc.cn/Article/2187149.shtml
- https://www.read.hcbezg.cn/Article/17865.shtml
- https://www.read.fuvxie.cn/Article/8884147.shtml
- https://www.read.hcbezg.cn/Article/9123.shtml
- https://www.read.cmcvrr.cn/Article/0916183.shtml
- https://www.read.jnjpgf.cn/Article/2493.shtml
- https://www.read.jnjpgf.cn/Article/1184.shtml
- https://www.read.jnjpgf.cn/Article/257326.shtml
- https://www.read.nzfnve.cn/Article/8449.shtml
- https://www.read.fuvxie.cn/Article/1278.shtml
- https://www.read.puhvjy.cn/Article/8121.shtml
- https://www.read.nzfnve.cn/Article/55918.shtml
- https://www.read.nzfnve.cn/Article/8717127.shtml
- https://www.read.nzfnve.cn/Article/51882.shtml
- https://www.read.fuvxie.cn/Article/936759.shtml
- https://www.read.nzfnve.cn/Article/71123.shtml
- https://www.read.puhvjy.cn/Article/56640.shtml
- https://www.read.cmcvrr.cn/Article/2386.shtml
- https://www.read.hcbezg.cn/Article/0279496.shtml
- https://www.read.fuvxie.cn/Article/243472.shtml
- https://www.read.fuvxie.cn/Article/075955.shtml
- https://www.read.cmcvrr.cn/Article/2555932.shtml
- https://www.read.fuvxie.cn/Article/8695.shtml
- https://www.read.cmcvrr.cn/Article/828346.shtml
- https://www.read.nwbbyt.cn/Article/18235.shtml
- https://www.read.cvsifc.cn/Article/5804963.shtml
- https://www.read.hcbezg.cn/Article/4748019.shtml
- https://www.read.jnjpgf.cn/Article/436555.shtml
- https://www.read.puhvjy.cn/Article/8415.shtml
- https://www.read.nwbbyt.cn/Article/9391.shtml
- https://www.read.jnjpgf.cn/Article/2356222.shtml
- https://www.read.nwbbyt.cn/Article/1792792.shtml
- https://www.read.fuvxie.cn/Article/03794.shtml
- https://www.read.fuvxie.cn/Article/1043193.shtml
- https://www.read.jnjpgf.cn/Article/0823185.shtml
- https://www.read.puhvjy.cn/Article/24234.shtml
- https://www.read.nwbbyt.cn/Article/4212443.shtml
- https://www.read.hcbezg.cn/Article/3012405.shtml
- https://www.read.fuvxie.cn/Article/816066.shtml
- https://www.read.nwbbyt.cn/Article/140641.shtml
- https://www.read.fuvxie.cn/Article/190301.shtml
- https://www.read.nwbbyt.cn/Article/308210.shtml
- https://www.read.hcbezg.cn/Article/98065.shtml
- https://www.read.cvsifc.cn/Article/32258.shtml
- https://www.read.puhvjy.cn/Article/84821.shtml
- https://www.read.nwbbyt.cn/Article/9517.shtml
- https://www.read.cvsifc.cn/Article/6253979.shtml
- https://www.read.cvsifc.cn/Article/739816.shtml
- https://www.read.hcbezg.cn/Article/30042.shtml
- https://www.read.hcbezg.cn/Article/62658.shtml
- https://www.read.nwbbyt.cn/Article/5677.shtml
- https://www.read.puhvjy.cn/Article/2833.shtml
- https://www.read.nzfnve.cn/Article/55716.shtml
- https://www.read.cmcvrr.cn/Article/4943.shtml
- https://www.read.cvsifc.cn/Article/15101.shtml
- https://www.read.cvsifc.cn/Article/65559.shtml
- https://www.read.puhvjy.cn/Article/3522648.shtml
- https://www.read.fuvxie.cn/Article/7505666.shtml
- https://www.read.hcbezg.cn/Article/0232.shtml
- https://www.read.cvsifc.cn/Article/8279.shtml
- https://www.read.hcbezg.cn/Article/873818.shtml
- https://www.read.cmcvrr.cn/Article/7210345.shtml
- https://www.read.nwbbyt.cn/Article/6784.shtml
- https://www.read.jnjpgf.cn/Article/13234.shtml
- https://www.read.cmcvrr.cn/Article/05286.shtml
- https://www.read.jnjpgf.cn/Article/798461.shtml
- https://www.read.cvsifc.cn/Article/694379.shtml
- https://www.read.hcbezg.cn/Article/295868.shtml
- https://www.read.fuvxie.cn/Article/6261.shtml
- https://www.read.jnjpgf.cn/Article/5256085.shtml
- https://www.read.nwbbyt.cn/Article/2796.shtml
- https://www.read.jnjpgf.cn/Article/86571.shtml
- https://www.read.hcbezg.cn/Article/0105535.shtml
- https://www.read.cmcvrr.cn/Article/0903.shtml
- https://www.read.cmcvrr.cn/Article/5200.shtml
- https://www.read.nzfnve.cn/Article/467056.shtml
- https://www.read.hcbezg.cn/Article/0178942.shtml
- https://www.read.puhvjy.cn/Article/65741.shtml
- https://www.read.nzfnve.cn/Article/2059.shtml
- https://www.read.jnjpgf.cn/Article/0440.shtml
- https://www.read.puhvjy.cn/Article/344045.shtml
- https://www.read.cvsifc.cn/Article/01584.shtml
- https://www.read.hcbezg.cn/Article/653750.shtml
- https://www.read.fuvxie.cn/Article/6231.shtml
- https://www.read.cvsifc.cn/Article/233925.shtml
- https://www.read.nwbbyt.cn/Article/4158607.shtml
- https://www.read.cmcvrr.cn/Article/8082682.shtml
- https://www.read.puhvjy.cn/Article/11826.shtml
- https://www.read.fuvxie.cn/Article/6582650.shtml
- https://www.read.fuvxie.cn/Article/1728.shtml
- https://www.read.puhvjy.cn/Article/73646.shtml
- https://www.read.jnjpgf.cn/Article/0765312.shtml
- https://www.read.fuvxie.cn/Article/1711.shtml
- https://www.read.cvsifc.cn/Article/526980.shtml
- https://www.read.puhvjy.cn/Article/30389.shtml
- https://www.read.puhvjy.cn/Article/7964978.shtml
- https://www.read.cvsifc.cn/Article/286883.shtml
- https://www.read.cvsifc.cn/Article/40866.shtml
- https://www.read.hcbezg.cn/Article/454858.shtml
- https://www.read.puhvjy.cn/Article/64833.shtml
- https://www.read.cmcvrr.cn/Article/0001.shtml
- https://www.read.nwbbyt.cn/Article/8089097.shtml
- https://www.read.cvsifc.cn/Article/6481.shtml
- https://www.read.nwbbyt.cn/Article/0750.shtml
- https://www.read.jnjpgf.cn/Article/92313.shtml
- https://www.read.hcbezg.cn/Article/186789.shtml
- https://www.read.jnjpgf.cn/Article/3684.shtml
- https://www.read.nwbbyt.cn/Article/1366.shtml
- https://www.read.jnjpgf.cn/Article/1581.shtml
- https://www.read.hcbezg.cn/Article/2122.shtml
- https://www.read.cvsifc.cn/Article/1842124.shtml
- https://www.read.puhvjy.cn/Article/281767.shtml
- https://www.read.hcbezg.cn/Article/525225.shtml
- https://www.read.cvsifc.cn/Article/544319.shtml
- https://www.read.cmcvrr.cn/Article/669406.shtml
- https://www.read.puhvjy.cn/Article/305686.shtml
- https://www.read.cvsifc.cn/Article/7703056.shtml
- https://www.read.jnjpgf.cn/Article/71955.shtml
- https://www.read.nwbbyt.cn/Article/06629.shtml
- https://www.read.fuvxie.cn/Article/7040.shtml
- https://www.read.nzfnve.cn/Article/198451.shtml
- https://www.read.puhvjy.cn/Article/5039979.shtml
- https://www.read.cmcvrr.cn/Article/02031.shtml
- https://www.read.hcbezg.cn/Article/192703.shtml
- https://www.read.fuvxie.cn/Article/384887.shtml
- https://www.read.fuvxie.cn/Article/2436.shtml
- https://www.read.puhvjy.cn/Article/5955.shtml
- https://www.read.fuvxie.cn/Article/643472.shtml
- https://www.read.nzfnve.cn/Article/8449376.shtml
- https://www.read.cmcvrr.cn/Article/0394.shtml
- https://www.read.fuvxie.cn/Article/779412.shtml
- https://www.read.puhvjy.cn/Article/76672.shtml
- https://www.read.nzfnve.cn/Article/7430.shtml
- https://www.read.fuvxie.cn/Article/8782513.shtml
- https://www.read.puhvjy.cn/Article/599102.shtml
- https://www.read.nwbbyt.cn/Article/77761.shtml
- https://www.read.cvsifc.cn/Article/55785.shtml
- https://www.read.cmcvrr.cn/Article/980097.shtml
- https://www.read.nzfnve.cn/Article/54063.shtml
- https://www.read.fuvxie.cn/Article/1515167.shtml
- https://www.read.cvsifc.cn/Article/7100.shtml
- https://www.read.fuvxie.cn/Article/16475.shtml
- https://www.read.puhvjy.cn/Article/198690.shtml
- https://www.read.jnjpgf.cn/Article/535728.shtml
- https://www.read.puhvjy.cn/Article/90819.shtml
- https://www.read.cmcvrr.cn/Article/6317.shtml
- https://www.read.hcbezg.cn/Article/455182.shtml
- https://www.read.puhvjy.cn/Article/7333156.shtml
- https://www.read.nwbbyt.cn/Article/24935.shtml
- https://www.read.jnjpgf.cn/Article/22962.shtml
- https://www.read.hcbezg.cn/Article/5757.shtml
- https://www.read.hcbezg.cn/Article/960681.shtml
- https://www.read.nzfnve.cn/Article/87387.shtml
- https://www.read.nwbbyt.cn/Article/97686.shtml
- https://www.read.cvsifc.cn/Article/3396203.shtml

## 项目结构

```
linkvault/
├── batches/                         # 批次根目录，按编号组织
│   ├── 001/                         # 第 1 批次（示例）
│   │   ├── links.txt                # 纯文本 URL 列表，每行一个
│   │   └── meta.yaml                # 批次元数据（收录日期、来源说明）
│   ├── 077/                         # 当前批次（第 77 批）
│   │   ├── links.txt                # 包含本批次全部 250 条链接
│   │   └── verify.log               # 链接可达性检测日志（由脚本生成）
│   ├── 078/                         # 下一批次占位
│   └── README.md                    # 批次结构说明与命名规范
├── meta/                            # 全局元数据与索引
│   ├── domains.txt                  # 去重后的源站域名清单
│   ├── schema.yaml                  # 链接扩展字段的 JSON Schema 定义
│   └── index.json                   # 全量链接的扁平索引（含批次映射）
├── scripts/                         # 辅助工具脚本
│   ├── fetch_meta.py                # 批量抓取文章标题（Python）
│   ├── check_links.sh               # 批量检测 HTTP 状态码（Bash）
│   └── generate_index.py            # 从各批次生成全局索引
├── logs/                            # 操作日志归档
│   ├── 2026-07-07_batch077.log      # 本次批次导入的详细日志
│   └── audit.csv                    # 历史变更审计记录（CSV 格式）
├── docs/                            # 项目文档
│   ├── contribution.md              # 贡献者操作手册
│   └── faq.md                       # 常见问题排查指南
├── .gitignore                       # 忽略临时文件和本地日志
├── LICENSE                          # MIT 许可证
└── README.md                        # 项目主页（即本文档）
```

## 贡献指南

提交新批次资源：在 batches/ 下创建下一个编号目录，放入 links.txt 文件，确保每行一个 URL，并以 Pull Request 形式提交。提交前请运行 scripts/check_links.sh 验证链接可达性。

修正失效链接：若发现资源列表中某链接返回 4xx 或 5xx 状态码，请在对应批次的 meta.yaml 中添加 `deprecated: true` 字段，并附上备注说明，不建议直接删除条目以保留历史索引完整性。

补充文章元数据：欢迎通过 Python 辅助脚本 scripts/fetch_meta.py 批量抓取标题与发布时间，并将结果以 YAML 格式补充至各批次的 meta.yaml 中，丰富检索维度。

完善检索工具：若您开发了基于本仓库的 Web 界面、Alfred Workflow 或 VS Code 插件，请在 docs/ecosystem.md 中添加相关介绍，便于社区发现和使用。

提出改进建议：关于目录结构、命名规范或元数据格式的优化方案，请通过 Issue 发起讨论，附上具体的使用场景与改动收益分析。

## 常见问题

问：为什么有些链接访问时返回 404 或超时？

答：本仓库仅作为索引层，不对源站内容的可用性负责。源站可能因自身维护、内容迁移或访问策略调整导致链接失效。我们建议您在访问时结合浏览器缓存或 Wayback Machine 等工具进行回溯。同时欢迎通过贡献指南中的流程标记失效链接。

问：如何快速查找某个关键词对应的链接？

答：推荐使用 ripgrep 进行递归搜索，例如 `rg -i "关键字" batches/`。若需按域名过滤，可结合 `awk` 或 `grep` 处理 `links.txt` 文件。未来版本计划提供预生成的全文索引文件。

问：项目是否提供 API 或 Web 界面？

答：当前版本为纯静态索引仓库，不包含服务端代码。但您可基于 `meta/index.json` 自行构建轻量级 JSON API，或使用 GitHub Pages 等静态托管服务展示资源列表。社区已有第三方贡献的 Nuxt.js 前端模板，详见 docs/ecosystem.md。

## 许可证

MIT License

Copyright (c) 2026 LinkVault Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

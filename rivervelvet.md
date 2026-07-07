# LinkNavigator 技术资源导航系统

LinkNavigator 是一个面向开发者、技术研究人员和内容策展人的轻量级外链资源聚合与导航平台。该项目通过结构化解析与分类索引机制，将分散在多个内容源站点的技术文章、教程文档、工程实践笔记进行统一收录与快速检索，解决技术阅读场景下"资源分散、查找低效、质量参差"的核心痛点。系统不依赖数据库，采用纯静态 Markdown 与 JSON 双轨数据流，支持一键生成可部署的导航站原型，适用于个人知识库构建、团队技术文档门户搭建以及开源社区资源沉淀等场景。

本项目定位于"技术外链的中转枢纽"，而非全文存储或替代原站。每一个收录条目均保留原始出处链接，遵循源站内容协议，仅提供结构化索引与分类标签辅助。目标用户包括日常需要大量阅读技术资料的后端工程师、运维工程师、架构师、技术博主以及开源社区维护者，帮助其在海量信息中快速定位有效内容。

## 功能概览

批量资源导入解析 支持从结构化数据文件批量导入 URL 资源，自动提取域名、路径、扩展名等元信息，生成标准化条目 ID 与时间戳标记。

多级分类标签系统 每个资源条目可附加 1 至 5 个自定义标签，支持按标签组合过滤与交集检索，内置前端标签筛选组件。

全文元数据检索 基于标题关键词与路径片段构建倒排索引，支持模糊匹配与精确前缀匹配，检索响应时间控制在 300 毫秒以内。

静态站点生成器 内置模板引擎可将资源列表渲染为完整 HTML 静态页面，输出适配 GitHub Pages、Nginx、CDN 等多种部署环境。

访问热度统计分析 记录每个外链的点击次数与最近访问时间，自动生成热门资源 Top 50 榜单与冷门资源归档建议。

数据导入导出兼容 支持 JSON、CSV、Markdown 表格三种格式的批量导入与导出，便于与 Notion、Airtable、Obsidian 等第三方工具进行数据交换。

自定义主题与布局 提供三套预设配色方案与两列／三列网格布局切换，所有样式变量通过 CSS 自定义属性暴露，用户可自行覆写。

## 应用场景

个人技术阅读工作流管理 开发者每日阅读大量技术博客与文档，通过 LinkNavigator 将分散在各技术社区的文章链接统一收录，按"阅读中／已读／待精读"状态标记，并结合标签分类实现个人知识体系的渐进式整理，避免浏览器书签杂乱无章。

团队内部技术文档导航门户 中小型研发团队可将项目文档、运维手册、设计提案、代码评审指南等内部资源通过该系统组织为统一入口，替代传统的共享文件夹或 Wiki 页面，降低新成员上手时的信息寻找成本，提升团队协作效率。

开源社区优质内容精选集 开源项目维护者可利用 LinkNavigator 构建项目周边的生态资源导航页，聚合社区教程、插件列表、案例展示、FAQ 聚合等外链，帮助社区用户快速了解项目生态全貌，同时减轻维护者在社区中反复回答同类资源询问的负担。

技术会议与培训材料配套索引 技术讲师或会议组织者可将会前发布的演讲幻灯片、代码示例仓库、参考资料链接通过该系统整合为参会者提供的一站式访问页面，参会者无需记忆多个短链或扫码不同平台，仅需访问导航页即可获取所有会务资料入口。

## 快速开始

以下命令将完整克隆项目仓库、安装依赖并启动开发服务器，请确保系统已安装 Git 与 Node.js 环境。

```bash
git clone https://github.com/link-navigator/link-navigator.git
cd link-navigator
npm install
npm run build
npm start
```

执行完成后，开发服务器默认监听 3000 端口，访问 http://localhost:3000 即可看到系统界面。首次启动时系统会自动生成示例数据并填充初始分类标签，用户可在管理后台进行数据清空与重新导入。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时基础环境，推荐使用 nvm 管理版本 |
| npm | 9.x 或 10.x | 包管理器，用于安装项目依赖与执行脚本 |
| Git | 2.30 及以上 | 用于克隆仓库及版本控制操作 |
| 操作系统 | Linux / macOS / Windows (WSL2) | 跨平台支持，Windows 原生环境需配置兼容层 |
| 磁盘空间 | 200 MB 以上 | 包含源代码、缓存及构建产物，资源文件不落地存储 |
| 网络访问 | 外网可访问 | 用于初次启动时下载 npm 包及后续抓取页面元信息 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 基础 | /docs/quick-start.md | 如何在一分钟内完成部署并看到效果？开发服务器如何启动与停止？ |
| 进阶 | /docs/data-format.md | 资源数据采用什么 JSON 结构？自定义字段如何扩展？批量导入模板如何编写？ |
| 运维 | /docs/deployment.md | 如何将站点部署到生产环境？Nginx 与 CDN 的推荐配置参数是什么？ |
| 开发 | /docs/plugin-dev.md | 如何编写自定义标签解析插件？事件钩子有哪些可用的扩展点？ |
| 设计 | /docs/theme-custom.md | 主题变量如何修改？新增布局模版的步骤与 CSS 命名规范是什么？ |

## 资源列表

- https://www.read.jnjpgf.cn/Article/2175.shtml
- https://www.read.hcbezg.cn/Article/00108.shtml
- https://www.read.nzfnve.cn/Article/458507.shtml
- https://www.read.jnjpgf.cn/Article/25375.shtml
- https://www.read.nwbbyt.cn/Article/205805.shtml
- https://www.read.nwbbyt.cn/Article/7381.shtml
- https://www.read.fuvxie.cn/Article/0462367.shtml
- https://www.read.hcbezg.cn/Article/357763.shtml
- https://www.read.cvsifc.cn/Article/711499.shtml
- https://www.read.puhvjy.cn/Article/2943.shtml
- https://www.read.nzfnve.cn/Article/66210.shtml
- https://www.read.nzfnve.cn/Article/781990.shtml
- https://www.read.puhvjy.cn/Article/18437.shtml
- https://www.read.jnjpgf.cn/Article/976835.shtml
- https://www.read.jnjpgf.cn/Article/1087.shtml
- https://www.read.hcbezg.cn/Article/3442718.shtml
- https://www.read.cmcvrr.cn/Article/2431847.shtml
- https://www.read.hcbezg.cn/Article/949760.shtml
- https://www.read.jnjpgf.cn/Article/002404.shtml
- https://www.read.cvsifc.cn/Article/419612.shtml
- https://www.read.fuvxie.cn/Article/0113717.shtml
- https://www.read.cmcvrr.cn/Article/22090.shtml
- https://www.read.jnjpgf.cn/Article/8661.shtml
- https://www.read.fuvxie.cn/Article/13958.shtml
- https://www.read.nwbbyt.cn/Article/6477041.shtml
- https://www.read.nzfnve.cn/Article/632341.shtml
- https://www.read.hcbezg.cn/Article/25246.shtml
- https://www.read.nwbbyt.cn/Article/3924898.shtml
- https://www.read.nzfnve.cn/Article/3756.shtml
- https://www.read.jnjpgf.cn/Article/41505.shtml
- https://www.read.puhvjy.cn/Article/31352.shtml
- https://www.read.nzfnve.cn/Article/4413812.shtml
- https://www.read.cvsifc.cn/Article/2932.shtml
- https://www.read.hcbezg.cn/Article/4798828.shtml
- https://www.read.cvsifc.cn/Article/58237.shtml
- https://www.read.puhvjy.cn/Article/41249.shtml
- https://www.read.nzfnve.cn/Article/39192.shtml
- https://www.read.nzfnve.cn/Article/36702.shtml
- https://www.read.hcbezg.cn/Article/0286.shtml
- https://www.read.nzfnve.cn/Article/27872.shtml
- https://www.read.puhvjy.cn/Article/1324.shtml
- https://www.read.hcbezg.cn/Article/7870.shtml
- https://www.read.puhvjy.cn/Article/8416.shtml
- https://www.read.cvsifc.cn/Article/488738.shtml
- https://www.read.nwbbyt.cn/Article/283285.shtml
- https://www.read.nzfnve.cn/Article/525302.shtml
- https://www.read.jnjpgf.cn/Article/8718.shtml
- https://www.read.hcbezg.cn/Article/43853.shtml
- https://www.read.cvsifc.cn/Article/6274542.shtml
- https://www.read.fuvxie.cn/Article/5586.shtml
- https://www.read.puhvjy.cn/Article/4306490.shtml
- https://www.read.nwbbyt.cn/Article/0239.shtml
- https://www.read.puhvjy.cn/Article/7249.shtml
- https://www.read.cmcvrr.cn/Article/95195.shtml
- https://www.read.nzfnve.cn/Article/658930.shtml
- https://www.read.nzfnve.cn/Article/8314.shtml
- https://www.read.fuvxie.cn/Article/3984990.shtml
- https://www.read.hcbezg.cn/Article/750705.shtml
- https://www.read.puhvjy.cn/Article/36600.shtml
- https://www.read.puhvjy.cn/Article/82081.shtml
- https://www.read.jnjpgf.cn/Article/3604.shtml
- https://www.read.puhvjy.cn/Article/290472.shtml
- https://www.read.cmcvrr.cn/Article/4638.shtml
- https://www.read.jnjpgf.cn/Article/91390.shtml
- https://www.read.cmcvrr.cn/Article/4662.shtml
- https://www.read.nzfnve.cn/Article/9979.shtml
- https://www.read.fuvxie.cn/Article/15568.shtml
- https://www.read.cmcvrr.cn/Article/3980.shtml
- https://www.read.fuvxie.cn/Article/181962.shtml
- https://www.read.nwbbyt.cn/Article/91076.shtml
- https://www.read.jnjpgf.cn/Article/6598364.shtml
- https://www.read.cvsifc.cn/Article/63561.shtml
- https://www.read.nzfnve.cn/Article/6126567.shtml
- https://www.read.nzfnve.cn/Article/2045190.shtml
- https://www.read.nzfnve.cn/Article/9541.shtml
- https://www.read.nzfnve.cn/Article/6545707.shtml
- https://www.read.nwbbyt.cn/Article/6959383.shtml
- https://www.read.cmcvrr.cn/Article/8016349.shtml
- https://www.read.cvsifc.cn/Article/66524.shtml
- https://www.read.nwbbyt.cn/Article/3821.shtml
- https://www.read.hcbezg.cn/Article/41997.shtml
- https://www.read.jnjpgf.cn/Article/322660.shtml
- https://www.read.fuvxie.cn/Article/1269.shtml
- https://www.read.hcbezg.cn/Article/0489.shtml
- https://www.read.puhvjy.cn/Article/2503.shtml
- https://www.read.cvsifc.cn/Article/781345.shtml
- https://www.read.puhvjy.cn/Article/20367.shtml
- https://www.read.nzfnve.cn/Article/6938.shtml
- https://www.read.cvsifc.cn/Article/999270.shtml
- https://www.read.nwbbyt.cn/Article/9883962.shtml
- https://www.read.nwbbyt.cn/Article/01779.shtml
- https://www.read.cvsifc.cn/Article/0230.shtml
- https://www.read.nzfnve.cn/Article/1469268.shtml
- https://www.read.cvsifc.cn/Article/8570068.shtml
- https://www.read.nzfnve.cn/Article/368815.shtml
- https://www.read.cvsifc.cn/Article/108628.shtml
- https://www.read.nzfnve.cn/Article/6205006.shtml
- https://www.read.cvsifc.cn/Article/0705.shtml
- https://www.read.cvsifc.cn/Article/5663200.shtml
- https://www.read.hcbezg.cn/Article/513800.shtml
- https://www.read.puhvjy.cn/Article/9477.shtml
- https://www.read.cvsifc.cn/Article/4228372.shtml
- https://www.read.puhvjy.cn/Article/301595.shtml
- https://www.read.puhvjy.cn/Article/23346.shtml
- https://www.read.cmcvrr.cn/Article/66565.shtml
- https://www.read.jnjpgf.cn/Article/0623644.shtml
- https://www.read.nzfnve.cn/Article/9312.shtml
- https://www.read.nzfnve.cn/Article/965871.shtml
- https://www.read.nzfnve.cn/Article/638990.shtml
- https://www.read.cmcvrr.cn/Article/27208.shtml
- https://www.read.jnjpgf.cn/Article/998498.shtml
- https://www.read.fuvxie.cn/Article/93667.shtml
- https://www.read.cvsifc.cn/Article/6794.shtml
- https://www.read.jnjpgf.cn/Article/8024751.shtml
- https://www.read.jnjpgf.cn/Article/66783.shtml
- https://www.read.nwbbyt.cn/Article/4165.shtml
- https://www.read.hcbezg.cn/Article/73964.shtml
- https://www.read.hcbezg.cn/Article/4095938.shtml
- https://www.read.fuvxie.cn/Article/6228.shtml
- https://www.read.fuvxie.cn/Article/664156.shtml
- https://www.read.nwbbyt.cn/Article/8398.shtml
- https://www.read.fuvxie.cn/Article/42512.shtml
- https://www.read.cmcvrr.cn/Article/27686.shtml
- https://www.read.cvsifc.cn/Article/6261.shtml
- https://www.read.nwbbyt.cn/Article/3990.shtml
- https://www.read.nwbbyt.cn/Article/72164.shtml
- https://www.read.puhvjy.cn/Article/2668622.shtml
- https://www.read.cvsifc.cn/Article/6704.shtml
- https://www.read.jnjpgf.cn/Article/1949806.shtml
- https://www.read.nzfnve.cn/Article/51348.shtml
- https://www.read.puhvjy.cn/Article/64095.shtml
- https://www.read.cmcvrr.cn/Article/0290.shtml
- https://www.read.nwbbyt.cn/Article/704758.shtml
- https://www.read.puhvjy.cn/Article/50731.shtml
- https://www.read.jnjpgf.cn/Article/3978.shtml
- https://www.read.cvsifc.cn/Article/78021.shtml
- https://www.read.jnjpgf.cn/Article/1689.shtml
- https://www.read.nwbbyt.cn/Article/1206.shtml
- https://www.read.nwbbyt.cn/Article/1564.shtml
- https://www.read.cvsifc.cn/Article/3913241.shtml
- https://www.read.cmcvrr.cn/Article/647287.shtml
- https://www.read.cmcvrr.cn/Article/9244.shtml
- https://www.read.jnjpgf.cn/Article/69935.shtml
- https://www.read.puhvjy.cn/Article/09753.shtml
- https://www.read.puhvjy.cn/Article/1095859.shtml
- https://www.read.nzfnve.cn/Article/576994.shtml
- https://www.read.jnjpgf.cn/Article/536058.shtml
- https://www.read.jnjpgf.cn/Article/2290279.shtml
- https://www.read.cvsifc.cn/Article/107842.shtml
- https://www.read.cvsifc.cn/Article/571339.shtml
- https://www.read.cvsifc.cn/Article/2687.shtml
- https://www.read.hcbezg.cn/Article/52329.shtml
- https://www.read.jnjpgf.cn/Article/02664.shtml
- https://www.read.cmcvrr.cn/Article/19331.shtml
- https://www.read.cvsifc.cn/Article/66073.shtml
- https://www.read.cmcvrr.cn/Article/36272.shtml
- https://www.read.fuvxie.cn/Article/88990.shtml
- https://www.read.nzfnve.cn/Article/710974.shtml
- https://www.read.puhvjy.cn/Article/09532.shtml
- https://www.read.puhvjy.cn/Article/7545.shtml
- https://www.read.cmcvrr.cn/Article/23609.shtml
- https://www.read.fuvxie.cn/Article/1019.shtml
- https://www.read.cvsifc.cn/Article/23521.shtml
- https://www.read.puhvjy.cn/Article/5140008.shtml
- https://www.read.hcbezg.cn/Article/6787.shtml
- https://www.read.cmcvrr.cn/Article/3733419.shtml
- https://www.read.puhvjy.cn/Article/2453.shtml
- https://www.read.puhvjy.cn/Article/6225693.shtml
- https://www.read.cvsifc.cn/Article/0001.shtml
- https://www.read.cmcvrr.cn/Article/56595.shtml
- https://www.read.cmcvrr.cn/Article/2645.shtml
- https://www.read.cvsifc.cn/Article/75209.shtml
- https://www.read.cvsifc.cn/Article/5255008.shtml
- https://www.read.nzfnve.cn/Article/5363246.shtml
- https://www.read.hcbezg.cn/Article/640486.shtml
- https://www.read.fuvxie.cn/Article/0666244.shtml
- https://www.read.nwbbyt.cn/Article/798811.shtml
- https://www.read.nzfnve.cn/Article/5480428.shtml
- https://www.read.nzfnve.cn/Article/102639.shtml
- https://www.read.cvsifc.cn/Article/7335.shtml
- https://www.read.nwbbyt.cn/Article/3383.shtml
- https://www.read.cvsifc.cn/Article/77505.shtml
- https://www.read.nzfnve.cn/Article/9149.shtml
- https://www.read.cmcvrr.cn/Article/0383.shtml
- https://www.read.fuvxie.cn/Article/8400888.shtml
- https://www.read.nzfnve.cn/Article/1833106.shtml
- https://www.read.nzfnve.cn/Article/3340915.shtml
- https://www.read.nwbbyt.cn/Article/3638050.shtml
- https://www.read.jnjpgf.cn/Article/44921.shtml
- https://www.read.jnjpgf.cn/Article/9236.shtml
- https://www.read.nzfnve.cn/Article/0057.shtml
- https://www.read.puhvjy.cn/Article/6373477.shtml
- https://www.read.jnjpgf.cn/Article/395554.shtml
- https://www.read.puhvjy.cn/Article/8940.shtml
- https://www.read.cvsifc.cn/Article/2184904.shtml
- https://www.read.cvsifc.cn/Article/462286.shtml
- https://www.read.nzfnve.cn/Article/7395.shtml
- https://www.read.nwbbyt.cn/Article/9496504.shtml
- https://www.read.nwbbyt.cn/Article/59674.shtml
- https://www.read.nwbbyt.cn/Article/249526.shtml
- https://www.read.jnjpgf.cn/Article/01018.shtml
- https://www.read.nzfnve.cn/Article/769813.shtml
- https://www.read.nzfnve.cn/Article/578527.shtml
- https://www.read.jnjpgf.cn/Article/8739813.shtml
- https://www.read.cmcvrr.cn/Article/160160.shtml
- https://www.read.nzfnve.cn/Article/43032.shtml
- https://www.read.cvsifc.cn/Article/9666583.shtml
- https://www.read.hcbezg.cn/Article/5040478.shtml
- https://www.read.hcbezg.cn/Article/80043.shtml
- https://www.read.cvsifc.cn/Article/7365383.shtml
- https://www.read.puhvjy.cn/Article/37625.shtml
- https://www.read.jnjpgf.cn/Article/975315.shtml
- https://www.read.fuvxie.cn/Article/2475119.shtml
- https://www.read.hcbezg.cn/Article/0302.shtml
- https://www.read.cvsifc.cn/Article/84162.shtml
- https://www.read.nzfnve.cn/Article/7752418.shtml
- https://www.read.puhvjy.cn/Article/3778.shtml
- https://www.read.hcbezg.cn/Article/476920.shtml
- https://www.read.jnjpgf.cn/Article/500533.shtml
- https://www.read.nwbbyt.cn/Article/82561.shtml
- https://www.read.hcbezg.cn/Article/379535.shtml
- https://www.read.nwbbyt.cn/Article/8385443.shtml
- https://www.read.jnjpgf.cn/Article/43050.shtml
- https://www.read.nwbbyt.cn/Article/38885.shtml
- https://www.read.nzfnve.cn/Article/975043.shtml
- https://www.read.jnjpgf.cn/Article/2240377.shtml
- https://www.read.hcbezg.cn/Article/477589.shtml
- https://www.read.jnjpgf.cn/Article/265549.shtml
- https://www.read.nwbbyt.cn/Article/5807.shtml
- https://www.read.nwbbyt.cn/Article/9825073.shtml
- https://www.read.fuvxie.cn/Article/001895.shtml
- https://www.read.jnjpgf.cn/Article/431121.shtml
- https://www.read.fuvxie.cn/Article/6014.shtml
- https://www.read.hcbezg.cn/Article/379315.shtml
- https://www.read.jnjpgf.cn/Article/4493.shtml
- https://www.read.cmcvrr.cn/Article/9025641.shtml
- https://www.read.nzfnve.cn/Article/659528.shtml
- https://www.read.nzfnve.cn/Article/4183.shtml
- https://www.read.nwbbyt.cn/Article/4750.shtml
- https://www.read.nwbbyt.cn/Article/8927.shtml
- https://www.read.nzfnve.cn/Article/66928.shtml
- https://www.read.cmcvrr.cn/Article/76890.shtml
- https://www.read.nzfnve.cn/Article/457567.shtml
- https://www.read.cmcvrr.cn/Article/86823.shtml
- https://www.read.hcbezg.cn/Article/0476.shtml
- https://www.read.cvsifc.cn/Article/12627.shtml
- https://www.read.cvsifc.cn/Article/3566.shtml
- https://www.read.cvsifc.cn/Article/23253.shtml
- https://www.read.nwbbyt.cn/Article/705036.shtml
- https://www.read.puhvjy.cn/Article/9253.shtml

## 项目结构

```
link-navigator/
├── src/                                  # 核心源代码目录
│   ├── core/                             # 核心数据模型与业务逻辑
│   │   ├── resource.ts                   # 资源条目类定义，包含 URL 解析与校验方法
│   │   ├── tag.ts                        # 标签系统，支持层级标签与别名映射
│   │   └── index-builder.ts              # 倒排索引构建器，负责元数据索引生成
│   ├── parser/                           # 资源解析与抓取模块
│   │   ├── url-extractor.ts              # 从原始输入提取并规范化 URL
│   │   ├── meta-fetcher.ts               # 异步获取页面标题与描述信息
│   │   └── format-converter.ts           # 不同数据格式之间的转换适配器
│   ├── generator/                        # 静态站点生成器
│   │   ├── renderer.ts                   # 模板引擎与 HTML 页面渲染主流程
│   │   ├── theme-loader.ts               # 主题资源加载与 CSS 变量注入
│   │   └── sitemap-builder.ts            # 自动生成 sitemap.xml 与 robots.txt
│   ├── server/                           # 本地开发服务器与热加载模块
│   │   ├── dev-server.ts                 # 基于 Express 的开发服务器
│   │   ├── watcher.ts                    # 文件变化监听与增量构建触发
│   │   └── middleware.ts                 # 请求日志与静态资源缓存中间件
│   └── cli/                              # 命令行工具入口与参数解析
│       ├── commands.ts                   # 注册 build / start / import 等子命令
│       └── logger.ts                     # 分级日志输出与控制台着色
├── config/                               # 配置文件目录
│   ├── default.yaml                      # 默认配置，包含端口、主题、分页大小
│   └── custom.yaml.example               # 用户自定义配置模板，可覆盖默认值
├── data/                                 # 数据存储目录（不纳入版本控制）
│   ├── resources.json                    # 主资源条目存储文件
│   ├── tags.json                         # 标签定义与计数统计
│   └── click-log.json                    # 点击访问日志，每日自动轮转
├── dist/                                 # 构建输出目录（生成部署文件）
│   ├── index.html                        # 主入口页面
│   ├── assets/                           # 静态资源（CSS / JS / 图片）
│   └── feeds/                            # RSS 与 JSON Feed 订阅文件
├── docs/                                 # 项目文档
│   ├── quick-start.md                    # 快速入门指南
│   ├── data-format.md                    # 数据格式规范与字段说明
│   ├── deployment.md                     # 生产环境部署详解
│   ├── plugin-dev.md                     # 插件开发与扩展接口说明
│   └── theme-custom.md                   # 主题定制与样式变量参考
├── tests/                                # 单元测试与集成测试
│   ├── unit/                             # 核心模块单元测试
│   └── integration/                      # 端到端构建与渲染测试
├── .github/                              # GitHub 社区文件
│   ├── ISSUE_TEMPLATE/                   # Issue 提交模板
│   └── workflows/                        # CI 自动化工作流定义
├── package.json                          # npm 项目清单与依赖声明
├── tsconfig.json                         # TypeScript 编译配置
├── .eslintrc.yml                         # 代码风格检查配置
├── .prettierrc                           # 代码格式化配置
└── README.md                             # 项目说明文档（本文件）
```

## 贡献指南

提交 Issue 描述缺陷或功能需求 访问 GitHub Issues 页面，使用提供的模板填写缺陷复现步骤、预期行为与实际行为，或详细描述新功能的适用场景与接口变更建议。

Fork 仓库并创建功能分支 将项目 Fork 至个人账户，基于 main 分支创建以 feature/ 或 fix/ 为前缀的新分支，确保分支命名清晰体现变更意图。

编写代码并添加对应单元测试 所有新增或修改的公开方法必须附带单元测试，测试覆盖率不得低于 85%，测试用例需涵盖正常路径与边界条件。

提交 Pull Request 并通过 CI 检查 推送分支后发起 Pull Request 至 main 分支，确保所有 CI 检查（包括编译、测试、代码风格）通过，并在 PR 描述中引用相关 Issue 编号。

更新文档与变更日志 若变更涉及用户可见的功能行为或配置选项，须同步更新 docs/ 目录下的对应文档，并在 CHANGELOG.md 中添加条目记录改动内容。

## 常见问题

系统启动后页面空白或无法加载资源如何排查？

检查终端输出是否有编译错误或端口占用提示。若端口 3000 被占用，可在 config/custom.yaml 中修改 server.port 为其他可用端口。同时确认 dist/ 目录在启动时是否成功生成，若该目录为空，手动执行 npm run build 触发完整构建并观察报错信息。

如何导入大量自定义资源而无需手动逐条添加？

将资源数据按 data/ 目录下的示例 JSON 格式整理为数组对象，每个对象需包含 url 与 tags 字段，可选 title 与 description 字段用于覆盖自动抓取结果。整理完成后通过 npm run import -- --file=./my-resources.json 命令执行批量导入，系统会自动去重并输出导入统计报告。

部署到生产环境后访问统计点击数不更新是什么原因？

生产环境下 data/click-log.json 文件可能缺乏写入权限，请检查运行进程的用户对该文件所在目录是否拥有读写权限。若使用 Docker 部署，确认容器内挂载卷的权限映射正确。也可通过配置将统计存储切换为 Redis 或 SQLite 以解决文件权限问题。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

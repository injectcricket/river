# LinkNavigator 外链资源聚合系统

LinkNavigator 是一个面向技术内容聚合、外链资源整理与结构化导航的开源工具集，定位于帮助开发者、技术博主、文档维护者以及知识管理团队，将分散在多个域名下的文章链接、技术文档、教程资源进行统一收录、分类索引与快速检索。该项目并非一个传统的爬虫或采集系统，而是一个围绕外链元数据组织、标签化分类、状态监控与访问质量检测构建的轻量级管理框架，适用于需要长期维护大量外部资源链接的场景。

目标用户包括开源社区文档维护者、技术博客作者、在线教育平台内容运营人员以及企业内部知识库管理员。LinkNavigator 通过提供标准化的链接录入接口、可扩展的分类方案、自动化可用性检测脚本以及简洁的静态站点生成能力，使外链资源从散乱的收藏夹状态转化为可复用、可分享、可审计的结构化数据集。项目本身不依赖特定云服务或商业化搜索引擎，所有数据以纯文本和 Markdown 格式存储，便于版本控制与协作编辑。

## 功能概览

**多源链接统一收录** 支持从批量输入的 URL 列表中自动提取域名、路径、文章标识符等元信息，生成标准化的资源记录条目。

**自定义分类与标签体系** 允许用户为每条链接指定一个或多个分类标签，并支持基于标签的快速筛选与统计，适应不同技术领域或主题维度的组织需求。

**链接可达性周期性检测** 内置基于 HTTP 状态码的链接有效性检查脚本，可配置检测周期，输出不可达链接报告，帮助维护资源 freshness。

**元数据自动补全建议** 对符合特定域名模式（如 read.*.cn）的链接，提供基于路径模式的文章类型推断、发布日期解析和内容摘要提取的辅助工具。

**静态导航站点生成** 提供模板引擎，可将整理后的链接数据渲染为静态 HTML 导航页面，支持按分类、按域名、按更新时间等多种排序视图。

**数据导入导出兼容性** 支持 JSON、CSV、YAML 格式的链接数据导入导出，便于与其他知识管理工具或电子表格软件对接。

**链接关系图谱可视化** 提供可选的关系分析模块，可生成链接之间的域名共现图或分类关联图，辅助发现资源分布规律。

## 应用场景

技术博客的年度优质文章外链汇总 技术博主可使用 LinkNavigator 将一年内引用或推荐的外部技术文章链接统一录入，按编程语言、框架、算法等维度分类，生成可直接对外发布的导航页面，替代冗长的社交平台帖子。

开源项目文档的外部参考资源管理 开源项目维护者可将项目文档中引用的外部规范、教程、API 参考链接纳入 LinkNavigator 管理，通过自动检测功能及时发现失效链接，避免文档中出现死链影响用户体验。

企业内部技术知识库的外链审计 企业技术团队可利用 LinkNavigator 对内部知识库中引用的所有外部链接进行周期性审计，生成合规性报告，确保对外引用资源的安全性与可用性。

在线教育平台的课程扩展阅读整理 在线课程内容运营人员可批量导入课程章节中推荐的扩展阅读链接，按课程模块、难度等级、阅读时长等维度组织，生成结构化的课程配套资源目录。

技术社区的内容聚合与周报生成 技术社区运营者可定期将社区成员分享的优秀外部文章链接录入系统，自动生成带分类索引的周报或月刊内容，减少手动编排工作。

## 快速开始

以下步骤帮助您在本地环境中快速启动 LinkNavigator 服务，完成首批链接数据的导入与导航站点生成。

```bash
# 克隆项目仓库
git clone https://github.com/link-navigator/link-navigator.git
cd link-navigator

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 执行链接导入示例（使用项目自带示例数据）
python cli.py import --source samples/links_sample.json --format json

# 运行链接可用性检测（默认并发 10 个请求）
python cli.py check --workers 10 --output report.json

# 生成静态导航站点（输出至 dist 目录）
python cli.py build --template default --output dist

# 启动本地预览服务
python -m http.server 8000 --directory dist
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，推荐使用 3.11 或 3.12 以获得更好性能 |
| pip | 22.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| requests | 2.28.0 及以上 | 用于发送 HTTP 请求进行链接可达性检测 |
| PyYAML | 6.0 及以上 | 用于解析和生成 YAML 格式的配置文件与数据 |
| jinja2 | 3.1.0 及以上 | 模板引擎，用于生成静态导航页面 |
| click | 8.1.0 及以上 | 命令行交互框架，提供 CLI 命令解析 |
| pytest | 7.0.0 及以上 | 单元测试框架（仅开发环境需要） |
| black | 23.0.0 及以上 | 代码格式化工具（仅开发环境需要） |
| mypy | 1.0.0 及以上 | 静态类型检查工具（仅开发环境需要） |
| 操作系统 | Linux/macOS/Windows WSL2 | 支持主流 Unix-like 系统及 Windows 子系统 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|-----|------|-----------|
| 用户手册 | docs/user_guide.md | 如何安装、配置、导入链接、运行检测、生成站点 |
| 配置参考 | docs/configuration.md | 配置文件的结构、所有可选项及其默认值 |
| API 接口 | docs/api_reference.md | 核心模块的类与方法说明，适用于二次开发 |
| 数据格式 | docs/data_format.md | JSON/CSV/YAML 导入导出格式的字段定义与示例 |
| 模板开发 | docs/template_development.md | 如何自定义导航页面的 HTML 模板与样式 |
| 贡献指南 | CONTRIBUTING.md | 贡献代码、提交问题报告、新增功能的流程 |
| 常见问题 | docs/faq.md | 收集了用户在实际使用中遇到的典型问题与解决方案 |
| 变更日志 | CHANGELOG.md | 记录每个版本的更新内容与破坏性变更 |

## 资源列表

- https://www.read.cvsifc.cn/Article/7909.shtml
- https://www.read.nwbbyt.cn/Article/2447.shtml
- https://www.read.nwbbyt.cn/Article/212008.shtml
- https://www.read.cvsifc.cn/Article/7751084.shtml
- https://www.read.fuvxie.cn/Article/0496.shtml
- https://www.read.fuvxie.cn/Article/8201.shtml
- https://www.read.cvsifc.cn/Article/5236.shtml
- https://www.read.fuvxie.cn/Article/20956.shtml
- https://www.read.hcbezg.cn/Article/77005.shtml
- https://www.read.hcbezg.cn/Article/4084811.shtml
- https://www.read.cvsifc.cn/Article/1311.shtml
- https://www.read.fuvxie.cn/Article/088203.shtml
- https://www.read.fuvxie.cn/Article/61760.shtml
- https://www.read.cmcvrr.cn/Article/272606.shtml
- https://www.read.hcbezg.cn/Article/2328919.shtml
- https://www.read.cvsifc.cn/Article/36914.shtml
- https://www.read.hcbezg.cn/Article/691731.shtml
- https://www.read.cmcvrr.cn/Article/640048.shtml
- https://www.read.puhvjy.cn/Article/2421.shtml
- https://www.read.fuvxie.cn/Article/294181.shtml
- https://www.read.jnjpgf.cn/Article/0387765.shtml
- https://www.read.fuvxie.cn/Article/1041051.shtml
- https://www.read.jnjpgf.cn/Article/4179119.shtml
- https://www.read.nzfnve.cn/Article/211938.shtml
- https://www.read.fuvxie.cn/Article/397017.shtml
- https://www.read.nzfnve.cn/Article/1694.shtml
- https://www.read.puhvjy.cn/Article/611326.shtml
- https://www.read.fuvxie.cn/Article/8002.shtml
- https://www.read.nzfnve.cn/Article/6027.shtml
- https://www.read.puhvjy.cn/Article/6690598.shtml
- https://www.read.cmcvrr.cn/Article/55125.shtml
- https://www.read.puhvjy.cn/Article/795063.shtml
- https://www.read.nwbbyt.cn/Article/0411306.shtml
- https://www.read.nzfnve.cn/Article/066994.shtml
- https://www.read.cvsifc.cn/Article/31454.shtml
- https://www.read.cmcvrr.cn/Article/89465.shtml
- https://www.read.hcbezg.cn/Article/8830.shtml
- https://www.read.puhvjy.cn/Article/935849.shtml
- https://www.read.fuvxie.cn/Article/17798.shtml
- https://www.read.cvsifc.cn/Article/28446.shtml
- https://www.read.nzfnve.cn/Article/123244.shtml
- https://www.read.hcbezg.cn/Article/37890.shtml
- https://www.read.hcbezg.cn/Article/6544.shtml
- https://www.read.cmcvrr.cn/Article/0396.shtml
- https://www.read.cvsifc.cn/Article/73213.shtml
- https://www.read.fuvxie.cn/Article/2784191.shtml
- https://www.read.jnjpgf.cn/Article/611881.shtml
- https://www.read.cvsifc.cn/Article/6187.shtml
- https://www.read.cmcvrr.cn/Article/56670.shtml
- https://www.read.nwbbyt.cn/Article/62725.shtml
- https://www.read.fuvxie.cn/Article/7802889.shtml
- https://www.read.nzfnve.cn/Article/787011.shtml
- https://www.read.cmcvrr.cn/Article/1824562.shtml
- https://www.read.puhvjy.cn/Article/49869.shtml
- https://www.read.cmcvrr.cn/Article/748468.shtml
- https://www.read.hcbezg.cn/Article/8918.shtml
- https://www.read.fuvxie.cn/Article/65146.shtml
- https://www.read.cvsifc.cn/Article/8526.shtml
- https://www.read.jnjpgf.cn/Article/4237.shtml
- https://www.read.puhvjy.cn/Article/4394377.shtml
- https://www.read.cvsifc.cn/Article/649555.shtml
- https://www.read.nwbbyt.cn/Article/889172.shtml
- https://www.read.fuvxie.cn/Article/370433.shtml
- https://www.read.nwbbyt.cn/Article/800811.shtml
- https://www.read.nwbbyt.cn/Article/94466.shtml
- https://www.read.fuvxie.cn/Article/790996.shtml
- https://www.read.jnjpgf.cn/Article/18912.shtml
- https://www.read.puhvjy.cn/Article/244657.shtml
- https://www.read.nzfnve.cn/Article/4818.shtml
- https://www.read.cmcvrr.cn/Article/93347.shtml
- https://www.read.nzfnve.cn/Article/2590.shtml
- https://www.read.jnjpgf.cn/Article/2684285.shtml
- https://www.read.fuvxie.cn/Article/09297.shtml
- https://www.read.fuvxie.cn/Article/7014618.shtml
- https://www.read.hcbezg.cn/Article/805037.shtml
- https://www.read.cvsifc.cn/Article/4381.shtml
- https://www.read.puhvjy.cn/Article/77921.shtml
- https://www.read.nwbbyt.cn/Article/474872.shtml
- https://www.read.cmcvrr.cn/Article/2720.shtml
- https://www.read.fuvxie.cn/Article/00258.shtml
- https://www.read.puhvjy.cn/Article/359499.shtml
- https://www.read.fuvxie.cn/Article/733270.shtml
- https://www.read.jnjpgf.cn/Article/66370.shtml
- https://www.read.nwbbyt.cn/Article/488322.shtml
- https://www.read.cmcvrr.cn/Article/504920.shtml
- https://www.read.nzfnve.cn/Article/7879612.shtml
- https://www.read.nwbbyt.cn/Article/0746.shtml
- https://www.read.nwbbyt.cn/Article/17358.shtml
- https://www.read.puhvjy.cn/Article/7097898.shtml
- https://www.read.hcbezg.cn/Article/54858.shtml
- https://www.read.puhvjy.cn/Article/931946.shtml
- https://www.read.nwbbyt.cn/Article/359448.shtml
- https://www.read.nwbbyt.cn/Article/79508.shtml
- https://www.read.nzfnve.cn/Article/7393.shtml
- https://www.read.jnjpgf.cn/Article/65015.shtml
- https://www.read.jnjpgf.cn/Article/1983.shtml
- https://www.read.nzfnve.cn/Article/9800582.shtml
- https://www.read.hcbezg.cn/Article/29151.shtml
- https://www.read.puhvjy.cn/Article/63645.shtml
- https://www.read.nwbbyt.cn/Article/929401.shtml
- https://www.read.puhvjy.cn/Article/6222.shtml
- https://www.read.jnjpgf.cn/Article/858301.shtml
- https://www.read.cvsifc.cn/Article/0183.shtml
- https://www.read.puhvjy.cn/Article/849801.shtml
- https://www.read.cvsifc.cn/Article/760945.shtml
- https://www.read.puhvjy.cn/Article/25215.shtml
- https://www.read.jnjpgf.cn/Article/1475546.shtml
- https://www.read.fuvxie.cn/Article/32834.shtml
- https://www.read.nzfnve.cn/Article/4319.shtml
- https://www.read.cmcvrr.cn/Article/85999.shtml
- https://www.read.hcbezg.cn/Article/3254420.shtml
- https://www.read.cmcvrr.cn/Article/7943964.shtml
- https://www.read.cmcvrr.cn/Article/184071.shtml
- https://www.read.cvsifc.cn/Article/465092.shtml
- https://www.read.fuvxie.cn/Article/9409.shtml
- https://www.read.cvsifc.cn/Article/4943746.shtml
- https://www.read.cmcvrr.cn/Article/2083.shtml
- https://www.read.cvsifc.cn/Article/583405.shtml
- https://www.read.fuvxie.cn/Article/6560564.shtml
- https://www.read.jnjpgf.cn/Article/22913.shtml
- https://www.read.nwbbyt.cn/Article/59905.shtml
- https://www.read.cvsifc.cn/Article/1859.shtml
- https://www.read.jnjpgf.cn/Article/1096.shtml
- https://www.read.cvsifc.cn/Article/0038.shtml
- https://www.read.nzfnve.cn/Article/4598.shtml
- https://www.read.cmcvrr.cn/Article/128426.shtml
- https://www.read.puhvjy.cn/Article/9469.shtml
- https://www.read.hcbezg.cn/Article/1273.shtml
- https://www.read.cvsifc.cn/Article/7804381.shtml
- https://www.read.nwbbyt.cn/Article/4375412.shtml
- https://www.read.hcbezg.cn/Article/9240.shtml
- https://www.read.hcbezg.cn/Article/6500.shtml
- https://www.read.fuvxie.cn/Article/0410607.shtml
- https://www.read.puhvjy.cn/Article/24699.shtml
- https://www.read.cvsifc.cn/Article/59236.shtml
- https://www.read.cvsifc.cn/Article/188425.shtml
- https://www.read.hcbezg.cn/Article/201924.shtml
- https://www.read.jnjpgf.cn/Article/3363491.shtml
- https://www.read.hcbezg.cn/Article/5967.shtml
- https://www.read.fuvxie.cn/Article/44489.shtml
- https://www.read.cmcvrr.cn/Article/4408.shtml
- https://www.read.cvsifc.cn/Article/8416107.shtml
- https://www.read.hcbezg.cn/Article/3495.shtml
- https://www.read.nwbbyt.cn/Article/713232.shtml
- https://www.read.nzfnve.cn/Article/290586.shtml
- https://www.read.nwbbyt.cn/Article/39308.shtml
- https://www.read.cvsifc.cn/Article/9086083.shtml
- https://www.read.puhvjy.cn/Article/0044199.shtml
- https://www.read.puhvjy.cn/Article/4242124.shtml
- https://www.read.hcbezg.cn/Article/807713.shtml
- https://www.read.nzfnve.cn/Article/63855.shtml
- https://www.read.nwbbyt.cn/Article/5846.shtml
- https://www.read.nzfnve.cn/Article/4022.shtml
- https://www.read.cvsifc.cn/Article/17367.shtml
- https://www.read.cvsifc.cn/Article/52897.shtml
- https://www.read.jnjpgf.cn/Article/3538443.shtml
- https://www.read.puhvjy.cn/Article/8219035.shtml
- https://www.read.nzfnve.cn/Article/80955.shtml
- https://www.read.nwbbyt.cn/Article/507927.shtml
- https://www.read.cmcvrr.cn/Article/6148.shtml
- https://www.read.hcbezg.cn/Article/58412.shtml
- https://www.read.nzfnve.cn/Article/0636.shtml
- https://www.read.jnjpgf.cn/Article/6680546.shtml
- https://www.read.nwbbyt.cn/Article/5697.shtml
- https://www.read.cvsifc.cn/Article/3749.shtml
- https://www.read.fuvxie.cn/Article/245094.shtml
- https://www.read.jnjpgf.cn/Article/59372.shtml
- https://www.read.nzfnve.cn/Article/7377739.shtml
- https://www.read.hcbezg.cn/Article/0373.shtml
- https://www.read.hcbezg.cn/Article/2953.shtml
- https://www.read.jnjpgf.cn/Article/8954129.shtml
- https://www.read.nzfnve.cn/Article/8796.shtml
- https://www.read.puhvjy.cn/Article/20153.shtml
- https://www.read.cvsifc.cn/Article/6455286.shtml
- https://www.read.nwbbyt.cn/Article/2672946.shtml
- https://www.read.fuvxie.cn/Article/5470881.shtml
- https://www.read.fuvxie.cn/Article/1780476.shtml
- https://www.read.puhvjy.cn/Article/8556.shtml
- https://www.read.fuvxie.cn/Article/0930454.shtml
- https://www.read.nzfnve.cn/Article/8933523.shtml
- https://www.read.jnjpgf.cn/Article/895214.shtml
- https://www.read.hcbezg.cn/Article/5589545.shtml
- https://www.read.fuvxie.cn/Article/202553.shtml
- https://www.read.nwbbyt.cn/Article/827615.shtml
- https://www.read.jnjpgf.cn/Article/331801.shtml
- https://www.read.jnjpgf.cn/Article/293544.shtml
- https://www.read.nwbbyt.cn/Article/2374294.shtml
- https://www.read.nwbbyt.cn/Article/84044.shtml
- https://www.read.cvsifc.cn/Article/134188.shtml
- https://www.read.nzfnve.cn/Article/226578.shtml
- https://www.read.puhvjy.cn/Article/0983384.shtml
- https://www.read.puhvjy.cn/Article/3560.shtml
- https://www.read.puhvjy.cn/Article/1142303.shtml
- https://www.read.jnjpgf.cn/Article/3478.shtml
- https://www.read.cmcvrr.cn/Article/7518.shtml
- https://www.read.puhvjy.cn/Article/1758057.shtml
- https://www.read.fuvxie.cn/Article/29314.shtml
- https://www.read.nwbbyt.cn/Article/28444.shtml
- https://www.read.cmcvrr.cn/Article/165400.shtml
- https://www.read.nwbbyt.cn/Article/7250.shtml
- https://www.read.cmcvrr.cn/Article/84611.shtml
- https://www.read.nzfnve.cn/Article/956053.shtml
- https://www.read.nzfnve.cn/Article/954672.shtml
- https://www.read.nwbbyt.cn/Article/5871.shtml
- https://www.read.puhvjy.cn/Article/3140.shtml
- https://www.read.puhvjy.cn/Article/8480870.shtml
- https://www.read.puhvjy.cn/Article/84118.shtml
- https://www.read.fuvxie.cn/Article/5078001.shtml
- https://www.read.nzfnve.cn/Article/7493.shtml
- https://www.read.fuvxie.cn/Article/98516.shtml
- https://www.read.nzfnve.cn/Article/1969.shtml
- https://www.read.cvsifc.cn/Article/1353957.shtml
- https://www.read.puhvjy.cn/Article/3526.shtml
- https://www.read.nzfnve.cn/Article/89443.shtml
- https://www.read.nwbbyt.cn/Article/99325.shtml
- https://www.read.jnjpgf.cn/Article/1084772.shtml
- https://www.read.cvsifc.cn/Article/342323.shtml
- https://www.read.nwbbyt.cn/Article/32096.shtml
- https://www.read.fuvxie.cn/Article/966594.shtml
- https://www.read.cmcvrr.cn/Article/1140020.shtml
- https://www.read.fuvxie.cn/Article/220784.shtml
- https://www.read.jnjpgf.cn/Article/0417470.shtml
- https://www.read.cmcvrr.cn/Article/628528.shtml
- https://www.read.puhvjy.cn/Article/015993.shtml
- https://www.read.fuvxie.cn/Article/7906.shtml
- https://www.read.nzfnve.cn/Article/261373.shtml
- https://www.read.fuvxie.cn/Article/5883022.shtml
- https://www.read.cvsifc.cn/Article/806898.shtml
- https://www.read.jnjpgf.cn/Article/9964.shtml
- https://www.read.hcbezg.cn/Article/137281.shtml
- https://www.read.cvsifc.cn/Article/25972.shtml
- https://www.read.hcbezg.cn/Article/6616.shtml
- https://www.read.cvsifc.cn/Article/6319.shtml
- https://www.read.hcbezg.cn/Article/08277.shtml
- https://www.read.puhvjy.cn/Article/1767.shtml
- https://www.read.fuvxie.cn/Article/48440.shtml
- https://www.read.jnjpgf.cn/Article/09465.shtml
- https://www.read.cvsifc.cn/Article/822580.shtml
- https://www.read.jnjpgf.cn/Article/03762.shtml
- https://www.read.nwbbyt.cn/Article/6884.shtml
- https://www.read.jnjpgf.cn/Article/72658.shtml
- https://www.read.puhvjy.cn/Article/8207407.shtml
- https://www.read.cvsifc.cn/Article/67228.shtml
- https://www.read.hcbezg.cn/Article/618517.shtml
- https://www.read.cvsifc.cn/Article/9361337.shtml
- https://www.read.jnjpgf.cn/Article/69437.shtml
- https://www.read.jnjpgf.cn/Article/56285.shtml
- https://www.read.cvsifc.cn/Article/3128389.shtml
- https://www.read.cvsifc.cn/Article/523168.shtml
- https://www.read.cmcvrr.cn/Article/43218.shtml

## 项目结构

```
link-navigator/
├── cli.py                      # 命令行入口，注册所有子命令
├── requirements.txt            # 生产环境依赖清单
├── setup.py                    # 项目打包与安装配置
├── pyproject.toml              # 项目元数据与工具链配置（black/mypy）
│
├── src/                        # 核心源代码目录
│   ├── __init__.py
│   ├── importer/               # 链接导入模块，支持 JSON/CSV/YAML
│   │   ├── __init__.py
│   │   ├── base.py             # 导入器抽象基类
│   │   ├── json_importer.py    # JSON 格式解析器
│   │   └── csv_importer.py     # CSV 格式解析器
│   ├── checker/                # 链接检测模块，并发请求与状态分析
│   │   ├── __init__.py
│   │   ├── http_client.py      # 异步 HTTP 客户端封装
│   │   └── reporter.py         # 检测报告生成器（JSON/Markdown）
│   ├── builder/                # 静态站点生成模块
│   │   ├── __init__.py
│   │   ├── engine.py           # Jinja2 模板引擎封装
│   │   ├── default/            # 默认模板主题目录
│   │   │   ├── index.html.j2   # 首页模板
│   │   │   └── assets/         # CSS / JS 静态资源
│   │   └── exporters.py        # 数据导出为 HTML / JSON / CSV
│   ├── models/                 # 数据模型定义
│   │   ├── __init__.py
│   │   ├── link.py             # Link 数据类（url, tags, status 等）
│   │   └── collection.py       # 链接集合管理类
│   └── utils/                  # 通用工具函数
│       ├── __init__.py
│       ├── domain_parser.py    # 域名与路径解析辅助
│       └── logger.py           # 日志配置与输出
│
├── tests/                      # 单元测试与集成测试目录
│   ├── test_importer.py
│   ├── test_checker.py
│   └── fixtures/               # 测试用样本数据
│
├── samples/                    # 示例数据目录
│   ├── links_sample.json       # 导入示例 JSON
│   └── links_sample.csv        # 导入示例 CSV
│
├── docs/                       # 完整文档目录
│   ├── user_guide.md
│   ├── configuration.md
│   ├── api_reference.md
│   ├── data_format.md
│   └── template_development.md
│
├── dist/                       # 构建输出目录（静态站点）
│   └── (由 build 命令生成)
│
└── .github/                    # GitHub 社区配置文件
    └── ISSUE_TEMPLATE/         # 问题报告模板
```

## 贡献指南

提交问题报告 请在 GitHub Issues 中使用提供的模板提交问题，清晰描述复现步骤、预期行为与实际行为，并附上相关日志或数据样本。对于链接检测失败或导入格式异常的问题，请附带最小的可复现数据集。

代码贡献流程 Fork 本仓库到个人账户，在 dev 分支基础上创建功能分支，完成代码开发后提交 Pull Request。所有新增功能需包含对应的单元测试，且确保现有测试套件全部通过。代码风格需符合 black 和 mypy 的检查要求。

文档完善 欢迎对用户手册、API 文档、配置参考进行补充或修订。文档采用 Markdown 格式编写，修改后需确保目录索引与内部链接正确。对于新增功能，需同步更新对应的文档章节。

新增链接导入格式 若需支持新的数据格式（如 XML、Excel），请在 src/importer/ 目录下新建导入器类，继承 base.py 中的抽象基类，并实现 parse 方法。同时需在 cli.py 的 import 命令中注册该格式选项。

模板主题贡献 若希望提供新的导航页面主题，请在 src/builder/ 目录下新建主题文件夹，包含 index.html.j2 模板及配套静态资源。主题应保持响应式设计，并遵循默认主题的变量命名约定。

## 常见问题

**Q: 导入包含数百个链接的 JSON 文件时，内存占用过高怎么办？**

A: LinkNavigator 默认使用流式解析器处理 JSON 数组，不会一次性加载全部数据到内存。如果仍遇到内存问题，建议将 JSON 文件拆分为多个较小的文件分批导入，或使用 CSV 格式（逐行读取）。同时可通过 --batch-size 参数控制每批处理的记录数量，默认每批 100 条。

**Q: 链接检测报告显示大量超时错误，但浏览器中可以正常访问？**

A: 这通常是由于检测环境网络策略或目标服务器对并发请求的限制所致。建议采取以下措施：降低 --workers 并发数（例如从 10 降至 3）；增加 --timeout 超时时间（默认 10 秒，可调整至 30 秒）；配置 --delay 参数在每次请求之间增加固定延迟（例如 200 毫秒）。如果目标站点存在反爬机制，可考虑使用 --user-agent 自定义请求头。

**Q: 如何将现有书签文件（如浏览器导出的 HTML）导入系统？**

A: 目前尚未内置浏览器书签解析器，但可通过以下方式转换：使用浏览器书签管理工具将书签导出为 CSV 格式，或编写简单的 XPath 提取脚本将书签 HTML 转换为 LinkNavigator 接受的 JSON 格式。我们计划在后续版本中增加 Netscape 书签格式的直接支持，欢迎关注 Issue 跟踪进展。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-07 16:15:21

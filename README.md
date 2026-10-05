# 微分几何前三章 · ElegantBook

直接根据本学期微分几何教材已有的 LaTeX 原文整理，覆盖前三章的全部 16 个小节。
笔记作者：东邪。封面座右铭沿用数理统计笔记的设置。
教材依据为陈维桓编著的《微分几何》（第2版），版本信息根据教材 LaTeX 前置页核对。
正文保留定义、定理、引理、推论、性质及必要计算公式；删去证明、例题、习题、解答、历史背景及教学说明。

## 文件结构

```text
微分几何-ElegantBook/
├── main.tex                 # 总入口
├── 第一章.tex               # 预备知识
├── 第二章.tex               # 曲线论
├── 第三章.tex               # 曲面的第一基本形式
├── elegantbook.cls          # 数理统计使用的模板原件
├── reference.bib            # 模板默认加载的空文献文件
├── images/cover.png         # Manim 欧拉涡环封面原图
├── 微分几何前三章.pdf        # 编译成品
├── build.sh                 # 独立编译，自动清理副产物
├── 原文条目索引.md          # 原编号与 LaTeX 来源
├── 校验记录.md              # 条目与编译核验
├── ElegantBook-LICENSE      # 模板自带许可
└── .gitignore
```

## 与数理统计相同的环境

`elegantbook.cls` 直接复制自桌面网站项目的 `temp_repos/dx-Mathematical-Statistics/`，未修改。
文档继续使用 `\documentclass[lang=cn,10pt]{elegantbook}`。

| 内容 | 原模板环境 | 原模板颜色 |
| --- | --- | --- |
| 定义 | `definition` | 绿色 |
| 定理 | `theorem` | 橙色 |
| 引理 | `lemma` | 橙色 |
| 推论 | `corollary` | 橙色 |
| 性质与计算公式 | `proposition` | 蓝色 |

所有环境沿用模板的标题、边框、背景色、自动编号及分页方式。
正文按章自动编号；教材中的原编号记录在源码注释及原文条目索引中。
只在主文件指定 TeX Live 自带的 Fandol 中文字体，以兼容 macOS 和 Linux。
封面沿用 ElegantBook 的原版版式，图片选用 Manim 素材中的欧拉涡环，表现空间曲线的环状分布。
图片已随仓库保存，见 [图片说明](images/README.md)。

## 编译

需要包含 XeLaTeX、latexmk、Biber 和 Fandol 字体的 TeX Live 或 MacTeX。

```bash
bash build.sh
```

脚本在系统临时目录编译，完成后只把 `微分几何前三章.pdf` 放回本文件夹。
也可直接编译 `main.tex`；所有章节引用均为相对路径。

## 原文依据

整理依据是课程目录中的 `教材转换成果/微分几何/LaTeX源码/章节/第01章 预备知识/`、
`第02章 曲线论/`、`第03章 曲面的第一基本形式/` 下的 `pages/*.tex`。
未读取扫描教材 PDF。保留全部 30 个原编号定理、10 个原编号定义和 1 个原文无编号引理；
另外把散落在叙述段落中的定义、性质、公式提取为相应环境。
原文的页间续接已合并，删除了依赖 OCR 排版的包装命令及原式编号，保留定理条件与结论。
未对已有 LaTeX 原文进行全面数学纠错，整理稿继承原文中可能尚未校勘的问题。

## GitHub 与 Overleaf

公开仓库：[yangminggulab/dx-Differential-Geometry](https://github.com/yangminggulab/dx-Differential-Geometry)。
`main.tex` 位于仓库根目录；三个章节各为一个 `.tex`，模板与封面图片均包含在仓库中，使用相对路径。
源码、PDF、编译脚本和必要说明文件一起同步；编译副产物由 `.gitignore` 排除。不使用子模块或 Git LFS。

1. 在 Overleaf 账户设置中连接 GitHub，并授予此仓库访问权限。
2. 从项目列表选择 **New project → GitHub repo**，找到本仓库并导入。
3. 设置主文档为 `main.tex`，编译器为 **XeLaTeX**。
4. 后续在 Overleaf 的 **Integrations → GitHub** 中手动拉取或推送修改。

GitHub 同步需要 Overleaf 的相应高级功能权限；具体入口和限制以 [Overleaf 官方文档](https://docs.overleaf.com/integrations-and-add-ons/git-integration-and-github-synchronization/github-synchronization) 为准。
若当前账户没有同步权限，可从 GitHub 下载 ZIP 后上传至 Overleaf；这种方式只导入文件，不建立同步关联。

本地更新：先 `git pull --ff-only`，编辑分章文件并运行 `bash build.sh`，再提交和推送。
若已在 Overleaf 编辑，请先把 Overleaf 修改推送到 GitHub，再开始本地编辑，以减少冲突。

模板许可仅对应 `elegantbook.cls`；教材内容的权利归原权利人。

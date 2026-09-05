# mathematical modeling
数学建模大赛
# 1. 仓库整体目录规范（提前建好文件夹）

mathmodel-contest/
├── problem/            # 赛题原文、题目理解文档
├── data/
│   ├── raw/            # 原始数据，禁止修改！
│   └── processed/      # 清洗后导出的csv、处理后数据
├── code/               # Python / MATLAB 代码
│   ├── template/       # 通用算法模板（TOPSIS、GM(1,1)、优化算法）
│   ├── q1/             # 第1问代码
│   ├── q2/
│   └── q3/
├── output/             # 输出图片、表格、计算结果
├── paper/
│   ├── draft.md        # 论文草稿分段文本
│   └── report.docx    # 最终论文文件
└── README.md           # 项目说明、分工、运行依赖

> 硬性规则：`raw` 文件夹**永远只读，不允许任何提交修改原始数据**。
> 

## 2. 分支管理策略（轻量化，适合3天短周期比赛）

### 分支命名约定

- `main`：**最终稳定版本，保护分支，禁止直接 push**
- `dev`：开发主分支，所有人合并成果到此分支
- 个人功能分支格式：`feature/成员名-问题编号`
    - `feature/lihua-q1-model`
    - `feature/wangwu-q2-code`
    - `feature/zhaoliu-paper-write`

### 完整工作流

1. 所有人基于 `dev` 创建自己的个人分支工作
2. 完成一小块工作后提交到自己分支
3. 提交完成后发起 Pull Request（PR）合并回 `dev`
4. 小组简单核对无误后合并
5. 全部题目完成、验证正确后，由负责人合并 `dev` → `main`

> 比赛不使用复杂 release/tag，最后在 main 打一个版本标签 `final-submit`
> 

## 3. Git 常用完整指令（复制即用）

### 首次拉取仓库（组员第一次操作）

```bash
git clone <https://github.com/xxx/mathmodel-contest.git>
cd mathmodel-contest
每次开工前，同步最新代码（必做！防止冲突）
git checkout dev
git pull origin dev
创建自己的工作分支
git checkout -b feature/yourname-q1
工作完成，暂存、提交代码
git add .
git commit -m "feat(q1): 完成数据清洗与缺失值处理，导出清洗后csv"
git push origin feature/yourname-q1
更新本地分支（远程dev更新后同步）
git checkout feature/yourname-q1
git pull origin dev
合并解决冲突后提交
git add .
git commit -m "fix: 解决q1可视化代码合并冲突"
git push

## 4. Commit 提交信息规范（统一格式，方便回溯）

格式模板：类型(范围): 简短描述
类型标识 含义 示例
feat 新增模型/新增代码功能 feat(q1): 实现灰色预测GM(1,1)
fix 修复bug、修正计算错误 fix(q2): 修改熵权法权重计算bug
data 新增/导出处理数据集 data: 上传清洗完成后的数据集
plot 绘图、可视化结果输出 plot(q1): 输出灵敏度分析对比图
doc 论文草稿、文档更新 doc(paper): 完成问题一重述与模型假设
refactor 代码整理优化，逻辑重构 refactor(q3): 代码模块化整理
style 格式调整，无逻辑改动 style: 统一代码注释风格

❌ 禁止提交信息：更新文件、修改一下、最终版本

协作约定

1. 同一个文件不要多人同时编辑（尽量拆分文件：q1.py / q2.py 分开）

2. 大改动必须走 Pull Request，至少一人简单审阅再合并

3. 每次合并后在小组内口头同步一次更新内容

6. .gitignore 配置（必须添加到仓库根目录）

新建文件 .gitignore，复制下面内容，避免提交垃圾文件：
# Python缓存
__pycache__/
*.pyc
*.pyo
*.pyd
venv/
env/
*.ipynb_checkpoints

# Office临时文件
~$*.docx
~$*.xlsx

# 超大文件（原始大文件不提交git，网盘备份）
*.zip
*.rar
*.7z

# 系统垃圾
.DS_Store
Thumbs.db
重要提醒：超大数据集不提交 GitHub，使用网盘共享；仓库只放清洗脚本和小体量结果表格。
7. Pull Request（PR）填写模板

每次新建PR填写固定描述：
## 本次完成内容
1. xxx
2. xxx

## 修改文件列表
- code/q1/xxx.py
- output/xxx.png

## 校验情况
✅ 代码可运行
✅ 结果核对无误
✅ 无硬编码路径问题

Reviewer：@队友名字
8. 冲突处理规范（高频踩坑点）

1. 如果出现合并冲突，不要直接在 GitHub 网页端乱改

2. 本地拉取分支解决冲突，运行验证代码结果正确再提交

3. 论文docx文件极易冲突：优先用 Markdown 分段写，最后再合并成Word

9. 比赛收尾流程（提交前半小时）

1. 确认全部内容合并到 dev

2. 全部代码运行一次，复现全部图表结果

3. 合并 dev → main

4. 打版本标签：final-submit
git tag final-submit
git push origin final-submit
5. 截图仓库提交记录作为备份凭证

10. 禁止行为清单

1. ❌ 直接 git push 到 main 保护分支

2. ❌ 提交几百MB原始数据、压缩包

3. ❌ commit只写“更新”这种无意义文字

4. ❌ 多人同时编辑同一个docx论文

5. ❌ 本地做完不推送，最后一次性全部丢文件

6. ❌ 不拉取最新代码直接修改，制造大量冲突

```
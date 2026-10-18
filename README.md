# AI 智能判分系统（第三阶段）

本版本在第二阶段基础上增加：
- 按评分标准逐项给分，并显示每项理由；总分由逐项分数合计，避免总分和分项分数矛盾。
- 老师审核并确认最终分数。
- 老师确认后，将记录追加保存到 `grading_records.csv`，包含题目、评分标准、答案、AI 分数、教师最终分数、模型耗时和评分理由。

## 运行
1. 解压到新文件夹，不覆盖旧版本。
2. 在文件夹地址栏输入 `cmd` 并回车。
3. 创建虚拟环境：
   `python -m venv .venv`
4. 安装依赖：
   `.venv\Scripts\python.exe -m pip install -r requirements.txt`
5. 复制密钥模板：
   `copy .env.example .env`
6. 打开 `.env`：
   `notepad .env`
   将 `DEEPSEEK_API_KEY=` 后替换为自己的 API Key，保存。不要分享或上传 `.env`。
7. 启动：
   `.venv\Scripts\python.exe app.py`
8. 浏览器打开 `http://127.0.0.1:5000`。

如果你已经有第二阶段的 `.env`，可以把自己的密钥安全地复制到新文件夹的 `.env` 中；不要复制或上传任何含密钥的文件到公开仓库。

## 测试记录
每次 AI 评分后，检查分项得分与评分理由；老师确认最终分数后才保存到 `grading_records.csv`。CSV 可用 Excel 打开。不要把真实学生的敏感个人信息放进测试数据。

`grading_records.csv` 和 `.env` 已加入 `.gitignore`，不会被 Git 默认跟踪。上传 GitHub 前仍需检查仓库状态，确认密钥未进入提交历史。

## 说明
- 记录保存在本机项目目录，不是数据库，也没有多用户权限控制。
- 模型评分只能作为辅助意见，教师应检查并确认。
- 仅用于本地开发和演示，尚未做生产环境安全加固。

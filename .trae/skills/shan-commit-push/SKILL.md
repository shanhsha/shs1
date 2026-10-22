---
name: "shan-commit-push"
description: "Commits this coursework project and pushes to Gitee remote. Invoke when user asks to submit, commit, or push the project."
---

# 提交并推送项目到 Gitee

把当前《高级网页设计》课程作品集用 git 提交并推送到 Gitee 远程仓库。
本仓库无构建系统、无测试，静态 HTML + CSS，验证方式是浏览器打开页面。

## 远程仓库

- 名称: `origin`
- 地址: `https://gitee.com/shan-haisheng/307shanhaishenggaojiwangye`
  （用户给的 `http://` 会自动跳转到 `https://`，推送统一用 `https://`）
- 默认分支: `master`

## 执行前

1. 遵守 AGENTS.md：**先把本次提示词追加到 `shan_prompt.md`**（时间、模型、原文），只追加不覆盖。
2. 检查改动范围：`git status --short`、`git diff`、`git log --oneline -10`。
3. 确认 `index.html` 已与新增页面同步（作品页面数量、超链接）。

## 步骤

1. 确认/设置远程：

   ```powershell
   git remote -v
   if (-not (git remote)) { git remote add origin https://gitee.com/shan-haisheng/307shanhaishenggaojiwangye }
   ```

   若已有 `origin` 但地址不符，用 `git remote set-url origin <url>`。

2. 暂存改动（仅暂存预期文件，排除临时产物）：

   ```powershell
   git add -A
   git status --short
   ```

3. 提交，提交信息用简洁中文描述本次内容：

   ```powershell
   git commit -m "<简明中文说明>"
   ```

4. 推送（首次推送带 `-u`）：

   ```powershell
   git push -u origin master
   ```

5. 核对结果：`git status` 显示 working tree clean，`git log --oneline -3` 确认提交已在本地。

## 注意

- 中文文件名（`5-1层叠与继承.html` 等）在 PowerShell 控制台会显示乱码，属正常现象；
  用 Read 工具查看文件内容，不要用 `Get-Content` 判断编码。
- 仅在用户明确要求时提交/推送，不要自作主张。
- 不修改 git config，不使用 `--force`，不跳过 hooks。
- 认证由 git credential manager 处理；若推送提示登录，请让用户在弹窗或凭据管理器完成，不要索取/落盘密码。
- 只提交作品文件、`AGENTS.md`、`shan_prompt.md`、`img/` 等；不要提交编辑器临时文件或密钥。

---
name: "shan-github-push"
description: "Commits and pushes the coursework project to GitHub remote. Invoke when user asks to submit, commit, or push to GitHub."
---

# 提交并推送到 GitHub

把当前《高级网页设计》课程作品集用 git 提交并推送到 GitHub 远程仓库。
本仓库同时存在两个远程：`origin`（Gitee）和 `github`（GitHub），互不干扰。

## 远程仓库

- Gitee（主远程，已存在）：`origin` → `https://gitee.com/shan-haisheng/307shanhaishenggaojiwangye`
- **GitHub（本 skill 目标）**：`github` → `https://github.com/shanhsha/shs1`
- 默认分支：`master`

## 执行前

1. 遵守 AGENTS.md：**先把本次提示词追加到 `shan_prompt.md`**（时间、模型、原文），只追加不覆盖。
2. 检查改动范围：`git status --short`、`git log --oneline -5`。
3. 确认 `index.html` 已与新增页面同步（作品页面数量、超链接）。

## 步骤

1. 确认/设置 GitHub 远程：

   ```powershell
   git remote -v
   git remote remove github 2>$null   # 清除旧的 github remote（如存在）
   git remote add github https://github.com/shanhsha/shs1.git
   ```

   如果仓库还没在 GitHub 创建，先让用户在 GitHub 网页上创建 `shanhsha/shs1` 空仓库（不要勾选 README/.gitignore），再推送。

2. 暂存所有改动：

   ```powershell
   git add -A
   git status --short
   ```

3. 本地提交（如已有未推送的 commit 可跳过）：

   ```powershell
   git commit -m "<简明中文说明>"
   ```

4. 首次推送带 `-u`，后续可直接 `git push github master`：

   ```powershell
   git push -u github master
   ```

   如需同时推送到 Gitee：`git push origin master`

5. 核对结果：`git status` 显示 working tree clean，`git log --oneline -3` 确认提交已在本地。

## 注意

- 中文文件名在 PowerShell 控制台会显示乱码，属正常现象；用 Read 工具查看内容。
- 不修改 git config，不使用 `--force`，不跳过 hooks。
- GitHub 认证：可以用 HTTPS + Personal Access Token，也可以用 SSH（本机已有 `~/.ssh/id_ed25519`）。
  如果 SSH 方式推送失败，尝试 HTTPS：
  ```powershell
  git remote set-url github https://github.com/shanhsha/shs1.git
  ```
- 本 skill 只推送到 GitHub，不影响 Gitee origin。两个远程可以并存。
- 仅在用户明确要求时提交/推送，不要自作主张。

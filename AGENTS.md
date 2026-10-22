# AGENTS.md

## What this is
A static coursework portfolio for the course 《高级网页设计》. Hand-written HTML + CSS only.
No build system, no package manager, no tests, no lint/format config, no CI. Uses git only to submit;
there is a skill `.opencode/skills/shan-commit-push/SKILL.md` for committing and pushing to Gitee. To
verify a change, open the `.html` file directly in a browser.

## Hard constraints (from the assignment)
- **Native code only — no CDN, no frameworks, no external libraries.** Everything must run offline.
- **技术栈限定：原生 HTML + CSS + JavaScript**，禁止 Vue/React/jQuery/Bootstrap 等任何框架或库。
- **图标统一使用 `font/font_5244753_5641vvib7co/iconfont.css`**（iconfont 阿里巴巴矢量图标库）。
  使用时通过 `<link rel="stylesheet" href="./font/font_5244753_5641vvib7co/iconfont.css">` 引入，
  图标元素用 `class="iconfont icon-xxx"`。**禁止引入 Font Awesome、Lucide 等第三方图标库的 CDN。**
  （历史文件 `13-1~13-4.html` 已使用其他方式，暂不批量改动；新增页面必须遵守本条。）
- **异步数据获取统一使用浏览器原生 `fetch()` API**，禁止引入 axios 等库。
- Each lesson page is a standalone self-contained `.html` with its styles in an inline `<style>`
  block. `css.css` is a tiny shared stylesheet used only by `5-1层叠与继承.html`.

## Entrypoint
- `index.html` is the landing page that indexes every work page. The assignment also requires it to
  reproduce the prompt text verbatim inside the `.prompt-box` blockquote — keep that text intact.
- **Keep `index.html` in sync when pages change.** Every work page (including `10-*` and `11-*`)
  must be hyperlinked; update the "作品页面" count in the `.stats` block when adding a page.

## Naming & logging conventions (required by the author)
- **Every CSS class name, `id`, and JS variable must start with `shs_`** (e.g. `shs_card`,
  `shs_title`). JavaScript is currently absent, but apply the prefix to any that is added.
  （历史文件中的 `shan_` 前缀暂不批量替换，仅新增/修改时使用 `shs_`。）
- **Every `.html` file must include a top-of-file comment block** in Chinese, recording:
  姓名（固定为"单海晟"）、日期（YYYY-MM-DD）、功能名称（页面用途简述）。格式示例：
  ```html
  <!--
  姓名：单海晟
  日期：2026-10-22
  功能名称：Font Awesome 字体图标演示
  -->
  ```
- **Before executing any prompt/task, append it to `shan_prompt.md`** — append only, never
  overwrite. Each entry records the timestamp, the model used, and the verbatim prompt text.

## Conventions
- Work pages are named `<lesson>-<n>...`, e.g. `2-1.html`, `6-1flex.html`, `9-1transition.html`.
- Several filenames are Chinese: `5-1层叠与继承.html`, `5-2盒子模型.html`, `7-1上图下文.html`,
  `7-2左图右文.html`, `8-1css3选择器.html`. Keep names exact; links use relative `./name.html`.
- All files are UTF-8 (no BOM) and declare `<meta charset="UTF-8">`. Preserve this or Chinese text
  turns to mojibake.
- Shared images live in `img/` and are referenced with relative paths like `./img/1.jpg`.

## Environment gotcha
PowerShell 5.1 in this environment renders Chinese text as garbled mojibake in the console. The
files themselves are valid UTF-8 — use the Read tool, not raw `Get-Content` output, to inspect text.

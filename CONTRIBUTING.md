# 參與貢獻 (Contributing to contribute-2026)

歡迎來到北科程式設計研究社 (NPC)！本指南將帶領你發起你的第一個與第二個 Pull Request，帶你熟悉開源協作中「無衝突」與「有衝突」的常見情境。

---

## 前置作業

- 一個 GitHub 帳號
- 已經安裝 Git（使用 `git --version` 來驗證）
- 一個純文字編輯器 (推薦使用 VS Code)

---

## 基礎設定 (Step-by-Step Guide)

### 步驟 0 — 設定 Git 使用者與環境

在開始之前，請確保 Git 已設定正確的身分資訊。若你使用的是學校電腦，可能需要關閉 SSL 驗證以避免憑證等連線問題。

```bash
# 設定你的名字與信箱
git config --global user.name "你的名字"
git config --global user.email "你的信箱@example.com"

# 若在學校電腦遇到 SSL 憑證錯誤，請執行此行關閉驗證：
git config --global http.sslVerify false
```

### 步驟 1 — Fork 這份儲存庫

點擊頁面右上角的 **Fork** 按鈕。
這會在**你自己的** GitHub 帳號底下建立一份獨立的儲存庫複本。

### 步驟 2 — Clone 你的 Fork

```bash
# 將 YOUR_USERNAME 換成你的 GitHub 帳號
git clone https://github.com/YOUR_USERNAME/contribute-2026.git
cd contribute-2026
```

### 步驟 3 — 新增 Upstream 遠端設定

這會將你本地的儲存庫預設連結回原始的 `ntut-npc` 儲存庫，方便你之後同步進度。

```bash
git remote add upstream https://github.com/ntut-npc/contribute-2026.git
git remote -v   # 你應該會看到 origin 和 upstream 兩個都列出來了
```

---

## 任務一：無衝突 PR 練習 (No Merge Conflict)

在第一個任務中，我們將透過新增一個全新的個人檔案，來練習發起 PR 的完整流程。由於每個人新增的檔案名稱都不一樣，不會互相影響，因此**不會發生合併衝突**。

### 步驟 1-1 — 建立第一個分支 (Branch)

**絕對不要直接提交 (commit) 到 `main` 分支上。** 分支的名稱請遵循以下慣例：

```bash
git checkout -b add/profile-your_username
```

### 步驟 1-2 — 在 `participants/` 新增個人檔案

進入 `participants/` 資料夾，並建立一個以你 GitHub 帳號為名的 Markdown 檔案 (例如 `participants/YOUR_USERNAME.md`)。

複製並貼上以下模板，將中括號 `[ ]` 內的內容替換成你自己的資訊：

```md
## About Me

Hi! I'm **[你的名字或暱稱]**. 

## Contact

- **GitHub:** [https://github.com/你的帳號](https://github.com/你的帳號)
```

### 步驟 1-3 — Commit 並推送到你的 Fork

```bash
git add participants/
git commit -m "docs: add personal profile for YOUR_NAME"
git push origin add/profile-your_username
```

> **關於 commit 訊息前綴字：**
> 
> | 句首前綴 | 何時使用 |
> |--------|-------------|
> | `feat:` | 新功能 |
> | `fix:` | 修復 bug |
> | `docs:` | 文件上的更動 (← 這是你今天要做的事！) |
> | `chore:` | 不屬於以上類別的更動 |

### 步驟 1-4 — 發起 Pull Request

1. 前往在 GitHub 上屬於你 fork 的那個儲存庫。
2. 點擊螢幕上出現的 **"Compare & pull request"** 按鈕。
3. 將 base repository 設定為 `ntut-npc/contribute-2026` 並將 base branch 設為 `main`。
4. 寫下簡短的 PR 描述（例如："New profile for @YOUR_USERNAME"）。
5. 點擊 **"Create pull request"**。
6. 耐心等待最底下的 **format-check** CI 亮起綠燈完成！請等待維護者合併。

---

## 任務二：有衝突 PR 練習 (Merge Conflict)

在第二個任務中，我們所有人都要去修改**同一個檔案的同一行** (也就是 `roster.md` 的第 6 行)。只要有這份專案有另外一個人比你早把 PR 合併進去，你的 PR 就會馬上因為其他人修改了同一行而發生合併衝突 (Merge Conflict)。

這也是在開源專案中非常常見的情況！

### 步驟 2-1 — 確保你的本地 `main` 分支是最新的

在開始前，請確認你已經回到 `main` 分支，並將本地進度與官方 `upstream` 同步：

```bash
git checkout main
git pull --rebase upstream main
```

### 步驟 2-2 — 建立第二個分支

```bash
git checkout -b add/roster-your_username
```

### 步驟 2-3 — 編輯 `roster.md`

在你的編輯器中打開 `roster.md`。**精準地在第 6 行 (Line 6)** 依照以下格式加入你的條目：

```
- [Your Name](https://github.com/YOUR_USERNAME) - Your Department, Year X
```

> **重要規則 (CI 檢查器會強制規定)：**
> - 你的那一行**必須以 `- [` 開頭**（一個連字號、一個空格、然後是一個左方括號）。
> - 姓名與系所的中間**必須是一個連字號 `- `**。
> - GitHub 網址**必須是一個有效的 `https://github.com/` 連結**。
> - **切勿**留下多餘的空白行或動到檔案內的任何其他行。

### 步驟 2-4 — 發起第二個 PR

```bash
git add roster.md
git commit -m "docs: add YOUR_NAME to roster"
git push origin add/roster-your_username
```

接著像任務一一樣發起發起 PR。

---

## 還有問題嗎？

歡迎發起 GitHub Issue 或在 Discord 群組內詢問。祝貢獻愉快！

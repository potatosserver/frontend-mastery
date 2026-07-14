# 03. TS 配置模式 (TS Config Patterns)

很多初學者在安裝完 TS 後，會被 `tsconfig.json` 這個檔案搞瘋。他們覺得這是在設定複雜的伺服器 $\rightarrow$ 但實際上，`tsconfig.json` 只是在告訴編譯器：**「我希望我的代碼被翻譯成什麼樣子」**。

---

## 1. 核心設定：打造你的開發環境

你不需要背誦所有設定，只需要掌握這三個最關鍵的選項：

### A. `target` $\rightarrow$ 決定「翻譯成哪個版本的 JS」
- `ES5` $\rightarrow$ 兼容性最強 (甚至能跑在 10 年前的瀏覽器)，但代碼臃腫。
- `ESNext` $\rightarrow$ 使用最新特性，代碼簡潔，但舊瀏覽器會崩潰。
- **專業建議**：通常設定為 `ES2020` 或 `ESNext` $\rightarrow$ 優先追求開發效率。

### B. `strict` $\rightarrow$ 決定「檢查有多嚴格」
- `false` $\rightarrow$ TS 變成「寬鬆模式」，很多錯誤會被無視 $\rightarrow$ **這失去了使用 TS 的意義。**
- `true` $\rightarrow$ 啟用所有嚴格檢查 $\rightarrow$ **專業標準。** 雖然紅線會變多，但它保證了你的代碼在運行時幾乎不會崩潰。

### C. `outDir` $\rightarrow$ 決定「譯後檔案放哪」
- 防止 `.js` 檔案與 `.ts` 檔案混在同一個資料夾 $\rightarrow$ 設定為 `./dist` 或 `./build`。

---

## 2. 實作配置：建立你的第一個 config

**🚀 快速啟動指令：**
```bash
tsc --init
```
這會自動生成一個標準的 `tsconfig.json`。

**⚡️ 專業配置推薦：**
```json
{
    "compilerOptions": {
        "target": "ESNext",
        "module": "ESNext",
        "strict": true,
        "outDir": "./dist",
        "esModuleInterop": true,
        "skipLibCheck": true
    }
}
```

---

## 3. 實作流程：從編寫到部署

現在，你的開發工作流應該變成這樣：
1. **撰寫** $\rightarrow$ 在 `.ts` 檔案中開發，利用 TS 的紅線即時修正 Bug。
2. **編譯** $\rightarrow$ 執行 `tsc` 指令 $\rightarrow$ 將 TS 翻譯成 JS 並放入 `dist/` 資料夾。
3. **執行** $\rightarrow$ 瀏覽器讀取 `dist/` 裡的 JS 檔案。

---

## 🛠️ TS 配置挑戰

1. **初始化配置**：在專案根目錄執行 `tsc --init`。
2. **嚴格模式測試**：將 `strict` 設定為 `true` $\rightarrow$ 回到你的 `02-ts-types.md` 練習中 $\rightarrow$ 看看是否出現了新的紅線 $\rightarrow$ 思考如何修正。
3. **路徑隔離**：設定 `outDir` 為 `./dist` $\rightarrow$ 執行 `tsc` $\rightarrow$ 確認 `dist/` 資料夾中正確生成了對應的 `.js` 檔案。

---
<p align="center">
<a href="02-ts-types.md">02-ts-types ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/ts/03-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="../09-Modern-Framework-Architecture/01-framework-philosophy.md">01-framework-philosophy ➡️</a>
</p>

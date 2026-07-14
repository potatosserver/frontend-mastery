# 02. 類型深潛 (TypeScript Types Deep Dive)

在上一章中，我們知道了 TS 是用來「攔截錯誤」的。但如果你只會寫 `string` 和 `number`，那 TS 就像是一把只能切水果的鈍刀。要處理複雜的專業專案，你需要掌握 **「精確類型」**。

---

## 1. 聯合類型 (Union Types) $\rightarrow$ 「可以是這個，也可以是那個」

在現實世界中，一個變數並不總是單一類型。例如：一個使用者的 ID 可能是 `數字` 也可以是 `字串`。

**🚀 視覺化對比：**
- **❌ 錯誤寫法 (JS)**：`let id = 123; id = "ABC";` $\rightarrow$ 沒問題，但之後呼叫 `id.toUpperCase()` 時，如果 `id` 是數字，程式會直接崩潰。
- **✅ 專業寫法 (TS)**：
```typescript
let userId: number | string;

userId = 123;      // ✅ 正常
userId = "USER_01"; // ✅ 正常
```
**💡 關鍵點**：使用 `|` 符號，告訴 TS 這個變數有「多重身份」。

---

## 2. 介面 (Interface) $\rightarrow$ 定義「物件的形狀」

當你處理複雜物件（如使用者資料、產品資訊）時，你不能每次都寫 `object`。你需要定義一個 **「形狀標準」**。

**🚀 實作場景：定義一個「作品項目」**
```typescript
interface Project {
    title: string;
    category: 'Frontend' | 'Backend' | 'Fullstack'; // 限制只能是這三種
    year: number;
    description?: string; // 加上 ? 表示這個屬性是「可選的」
}

const myWork: Project = {
    title: "個人作品集",
    category: "Frontend",
    year: 2026
};
```
**為什麼這樣做？** 只要你定義了 `Interface`，當你輸入 `myWork.` 時，編輯器會自動彈出 `title`, `category` 等選項 $\rightarrow$ **完全不需要回頭看 HTML/JSON 定義。**

---

## 3. 泛型 (Generics) $\rightarrow$ 「打造可複用的容器」

泛型是 TS 的最高階技巧。它讓你定義一個函數時，不需要決定具體的類型，而是在 **「呼叫時」** 才決定。

**🚀 視覺化對比：**
- **❌ 沒用泛型**：你要為 `string[]` 寫一個函數，再為 `number[]` 寫一個函數 $\rightarrow$ 重複代碼。
- **✅ 使用泛型 `<T>`**：
```typescript
function getFirstElement<T>(arr: T[]): T {
    return arr[0];
}

const n = getFirstElement([1, 2, 3]);       // T 自動變成 number
const s = getFirstElement(["A", "B", "C"]); // T 自動變成 string
```
**💡 核心邏輯**：`<T>` 就像是一個「類型變數」，讓你的函數變成一個**通用模組**。

---

## 🛠️ TS 實作挑戰

請在你的 `.ts` 檔案中完成以下任務：

1. **定義 Interface**：建立一個 `User` 介面 $\rightarrow$ 包含 `name` (string), `age` (number), `email` (string, 可選)。
2. **實作 Union**：建立一個變數 `status` $\rightarrow$ 只能是 `"loading"`, `"success"`, 或 `"error"`。
3. **泛型練習**：寫一個 `wrapInArray<T>(item: T)` 函數 $\rightarrow$ 將任何傳入的東西包在陣列裡並回傳。

---
<p align="center">
<a href="01-ts-intro.md">01-ts-intro ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/ts/02-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="03-ts-config.md">03-ts-config ➡️</a>
</p>

`appearance` 是一個 CSS 屬性，用來控制使用者代理（瀏覽器或作業系統）對表單元素或其他原生 UI 元素所套用的預設外觀。設定為 `none` 時，就會移除所有原生樣式，讓你可以完全自訂樣式。

---

## 關鍵要點

1. **用途**

   * 移除瀏覽器或作業系統對 `<select>`、`<button>`、`<input>`（特別是 `type="range"`、`type="search"`）等元素的預設樣式。
   * 讓元素在不同平台下呈現更一致，並方便你套用自定義樣式。

2. **語法**

   ```css
   /* 標準屬性 */
   appearance: none;

   /* 廠商前綴（為了更廣泛的瀏覽器支援） */
   -webkit-appearance: none;
   -moz-appearance: none;
   ```

3. **瀏覽器支援**

   * 現代 Chrome、Safari、Edge（Chromium）都支援 `-webkit-appearance`。
   * Firefox 支援 `-moz-appearance`。
   * 目前僅有少數舊版瀏覽器或 IE 根本不理這個屬性。

4. **實作示例**

   ```scss
   select {
     /* 移除所有原生外觀，方便自訂下拉樣式 */
     -webkit-appearance: none;
     -moz-appearance: none;
     appearance: none;

     /* 以下為進一步的重置 */
     border: 0;
     outline: 0;
     background: none;
     color: inherit;
     box-shadow: none;
   }
   ```

---

### 為何要這麼做？

* **一致性**：不同平台的原生下拉選單樣式大相逕庭，透過 `appearance: none;`，可以先統一移除，再套用統一設計。
* **彈性**：當你需要完全客製化互動元件外觀（例如自訂箭頭、選單背景、滑鼠懸停效果等），不可或缺。

---

#### 你可能要注意

* 移除原生外觀後，套用自訂樣式時，請確保考慮可及性（accessibility），例如使用足夠的對比度、鍵盤操作與聚焦樣式。
* 若僅為移除邊框或陰影，可能不必完全取消 `appearance`，而只調整特定屬性，以保留原生可及性行為。

---
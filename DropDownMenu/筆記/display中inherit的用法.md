在 CSS 中，`display: inherit;` 的作用是讓當前元素採用其**父元素**的 `display` 屬性值，而不是使用預設值或其他指定值。這看似簡單，但在以下幾種情境下才真正有用——否則多半只是徒增複雜度，你真的需要它嗎？

---

## 1. 原理與預設行為

* 預設情況下，大多數元素的 `display` 屬性都是由瀏覽器定義（如 `<div>` 為 `block`、`<span>` 為 `inline`）。
* 若你未對子元素顯式設定 `display`，它就會用自己的預設值，不會自動繼承父元素。
* 使用 `display: inherit;` 後，子元素就會「嚴格跟隨」父元素當前的顯示模式。

---

## 2. 何時才需要用？

1. **父元素顯式設定** 某種非預設的 `display`（如 `flex`、`grid`、`table`）
2. 你希望多層子孫元素都維持同一種顯示模式，但又不想對每一個層級都重複寫相同的值
3. 在動態切換場景中（JavaScript 切換父容器的 `display`），讓所有子孫一起跟著改變

> 若父元素未設定或仍使用預設值，`inherit` 其實對結果不會有實質影響。

---

## 3. 具體範例

```html
<style>
  /* 父元素顯式設定為 flex 佈局 */
  .container {
    display: flex;
    border: 1px solid #666;
    padding: 8px;
  }

  /* 子元素繼承父元素的 display，等同於 display: flex; */
  .item {
    display: inherit;
    margin: 4px;
    background: #eef;
    padding: 8px;
  }

  /* 假若去掉 display: inherit，.item 會回到預設的 inline 狀態 */
</style>

<div class="container">
  <div class="item">A</div>
  <div class="item">B</div>
  <div class="item">C</div>
</div>
```

在上例中，`.item` 實際上會佔滿整列（flex item），如果不使用 `inherit`，它們就會變成 inline，彼此緊靠在一起。

---

## 4. 注意事項與最佳實踐

* **父元素** 必須先 **顯式** 指定了 `display`，否則子元素繼承也只是重複瀏覽器預設值，毫無意義。
* 過度使用繼承會讓 CSS 規則變得難以追蹤——你真的需要讓所有層級都同樣顯示嗎？
* 對於大多數單一層級佈局，直接在目標元素寫上想要的 `display` 更直觀，維護也更容易。

---

### 總結

`display: inherit;` 在要求多層結構都維持同一顯示模式、並且要以父層為唯一真 source of truth 時，才有存在價值。否則，與其「繼承」，不如直截了當地在需要的元素上設定 `display`，避免不必要的複雜度。

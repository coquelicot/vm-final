# Introspection-based Memory De-duplication and Migration

## [跟風]

- 故事是這樣的：

    > 這篇的 Abstract 寫的很神，說是會去讀 guest 的記憶體內容，有意義的解釋
    > 它（成資料結構），以取得 guest 的 **free memory pool**。在很多版本的
    > Linux 和 Windows 上都可以成功偵測的樣子。

    > 偵測 free memory pool 是因為這些頁面內容不重要，可以丟掉，當作 duplicate XD
    > 這樣配合他想做的 migration 應用時，這些頁面就不 migrate。

- 作法的亮點：

## 技術細節

## 實驗結果

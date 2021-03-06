# Introspection-based Memory De-duplication and Migration

## [跟風]

- 故事是這樣的：

    > 這篇的 Abstract 寫的很神，說是會去讀 guest 的記憶體內容，有意義的解釋
    > 它（成資料結構），以取得 guest 的 **free memory pool**。在很多版本的
    > Linux 和 Windows 上都可以成功偵測的樣子。

    > 偵測 free memory pool 是因為這些頁面內容不重要，可以丟掉，當作 duplicate XD
    > 這樣配合他想做的 migration 應用時，這些頁面就不 migrate。

- 作法的亮點：

    > 因為是從外部 introspec, 所以是 full virtualization. (but windows/linux only)

## 技術細節

> Windows: scan PE file -> find kernel -> get pdb file -> find desired structure -> ya!
> Linux: find real mode metadata -> get source -> compile stub -> scan -> ya!
> Beware of race condition!!

## 實驗結果

> 對於 windows guest 的 dedup 幫助不大，但是 dedup 速度有一些進步 (因為 scan overhead 比較大)
> 對於 windows guest 的 migration 幫助很大，在 guest free page 挺多時，可以省掉可能一半的 traffic.
> 對於 linux guest 的 dedup 幫助挺多，有明顯增加 shared page.
> 對於 linux guest 的 migration 幫助很大，跟 windows 差不多概念。

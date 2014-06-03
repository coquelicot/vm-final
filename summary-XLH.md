# XLH: More effective memory deduplication scanners through cross-layer hints

## [跟風]

- 用一句話形容這篇文章：

    > Hook VMM 的檔案 I/O，分析它而提出可能的 deduplication 的提示。
    > 以前的作法需要掃描記憶體，很慢。不知道是不是 paravirtualization，
    > 因為它好像是對 VMM 去追蹤（追蹤 `.vdi` 檔的讀寫之類的）。
    > 據說可以追蹤到 short-lived 頁面的重複。

- 作法的亮點：
    
    > 因為是在 Host 的 VFS intercept, 所以是 full virtualization.
    > 利用環狀 queue 來存 hint  ，可以消除過多的 stale information.
    > 在分析速度快於 hint 產率的時候可以 ondemand 切換回原本 scan memory 那樣。

## 技術細節

## 實驗結果

    > 發現的 share opportunity 明顯增加
    > 找出多數 sharable page 的速度明顯加快

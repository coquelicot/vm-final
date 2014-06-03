# Difference Engine: Harnessing Memory Redundancey in Virtual Machines

## [跟風]

- 用一句話形容這篇文章：

    > 比起原先對 page 做 copy-on-write 的作法之外，我們還去存 diff 並配上
    > 在地壓縮。聽說效果很好。

- 作法的亮點：

    > 對於 similiar page 的 search 相當神秘 (64byte blocks), overhead 小小的。
    > 避開 domain-0 的 memory 、對 ioemu 做特化。
    > 有考量到 guest 可能會把記憶體都要回去，加入了 swapping 機制。
    > 巧妙的將 C4 state 與 compressable 的 page 疊在一起。

## 技術細節

> 三不五時醒來掃一下的 clock
> R/M bit 另外加兩個 bits 計數， page 分類成 C1 - C4
> full page hash for share page, 神秘 64byte block hash for similarity
> 分段處理 hash, not necessary 每 phase 清空
> ignore 壓縮率不到一半的 patch
> 可以把東西塞進 disk 的 swapd, 注意 race condition.
> 修改 ioemu 以避免它把整個 address space map 進去 dom-0

## 實驗結果

> 對 performance 的影響沒有很大。 7% (但我覺得好像更多一點)
> 省下潮多 page!! (三個方案疊起來大勝 ESXi), 有時可以 free 掉 7x% 之類。

## 無關閒聊

快找 motion vector 然後配上 run-length encoding、ssss 還有 Huffman！（誤）

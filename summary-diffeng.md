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

## 實驗結果

    > 對 performance 的影響沒有很大。
    > 省下潮多 page!! (三個方案疊起來大勝 ESXi)

## 無關閒聊

快找 motion vector 然後配上 run-length encoding、ssss 還有 Huffman！（誤）

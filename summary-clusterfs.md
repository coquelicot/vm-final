# Decentralized Deduplication in SAN Cluster File System

## [跟風]

- 故事是這樣的：

    > as title，全文結束（X）

    > 就是把 dedup 技術專門應用在 SAN 叢集檔案系統上 @@，而且不是中央控管的

    * 不解：這裡 decentralized 跟 distributed 有什麼不同？

- 作法的亮點：

    > virtual arena (避免把底層的東西 expose 出來)
    > 你只要不跑 daemon 就可以不加入 dedup (如果已知你的東西與眾不同，就不用因此付出 overhead)
    > extensible hashing for index file.

    > 不需要中央管控機制, dedup 跟修正的作用都分散在每個 VMM

    > 利用 vmfs 原生的 copy-on-write 支援來做 share。沒有 share 的 block 因為不
    > 做 copy-on-write，所以很快，但也可能資料內容跟舊的 hash 值不符。

## 技術細節

> 每個 VMM 都有個自己的 writer moniter，也有個自己的 write log。我們蒐集一些 write
> 之後就會定時把他寫進 write log 然後尋找 duplication。

> 為了做到這點，每個 host 的 write log 都是依照 hash 值分割成很多小檔案，這樣
> 每次依照 (sorted) hash 順序更新時只要鎖一個小檔案。一旦某個檔案內容太多，我們
> 就再把它切一半。

> 一旦發現 duplicate，就把我這邊的 Unique 更新成 Shared，然後送一個 pull request
> 給對方。等對方再掃到/檢查到 pull request 時，就 merge 。

## 實驗結果

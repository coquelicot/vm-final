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

## 技術細節

## 實驗結果

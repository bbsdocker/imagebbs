# imagebbs: 印象。ＢＢＳ

![](https://i.imgur.com/IGpjoDE.png)

**注意：仍在測試階段，建請先自行檢閱過相關腳本再自行安裝，歡迎利用 issues 或 pull requests 功能提出任何建議**

## 如何使用

* 請先自行[安裝 Docker](https://docs.docker.com)

### PttBBS

* (sudo) `docker run -d -p 8888:8888 holishing/imageptt` 後，直接 `telnet localhost 8888` 即可開始測試。

### 自行建置 docker image

* [請參考此處](BUILD.md)

## 希望的用途

1. 方便讓人不用花太多步驟也能讓人體驗各版本 BBS 站台的介面

2. 只要平台環境能裝具有完整功能的 Docker 並執行相關基本操作，即可利用此 repo 測試相關服務

## 建議事項

* **目前僅嘗試能讓測試者自用**，若無相關把握不建議用來開放外連服務，若有相關架公開站台需求者，建議仍按照各 BBS 版本文件指示自行建站。

* 查閱 https://github.com/bbslist/bbslist.github.io 可查詢你有興趣 BBS 站台是以哪個版本為基礎

## 授權 (LICENSE)

* 以下引用的範例設定檔名形式：依各專案授權方式為主
  - `<BBSNAME>/<BBSNAME>_conf`
  - `<BBSNAME>/config_h`

* 相關腳本: [MIT License](LICENSE)

* 說明文件: [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.zh_TW)


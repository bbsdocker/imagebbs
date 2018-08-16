# imagebbs: 印象。ＢＢＳ

![](https://i.imgur.com/IGpjoDE.png)

**注意：仍在測試階段，建請先自行檢閱過相關腳本再自行安裝，歡迎利用 issues 或 pull requests 功能提出任何建議**

## 步驟

* 請先自行[安裝 Docker](https://docs.docker.com)

### 現成版本

#### PttBBS

* (sudo) `docker run -d -p 8888:8888 holishing/imageptt` 後，直接 `telnet localhost 8888` 即可開始測試。

### 自行建置 docker image

1. cd <指定 BBS 版本> (例：`cd pttbbs` )

2. 用 docker build 指令建立相關映像檔，並加 -t 參數自行指定像是 <你的代號/image名字> 形式的標籤名稱 (例：`sudo docker build -t yourname/localimageptt .` )

3. 等待 build 腳本執行

4. 執行你建立好的 Docker image , 測試服務！ 

執行指令形式大略是 (sudo) docker -d -p <你想要指定的port>:8888 <你的image標籤>

以 pttbbs 為例：輸入 `sudo docker run -d -p 8888:8888 yourname/localimageptt`, 然後直接 `telnet localhost 8888` 即可開始測試

5. 利用 docker ps 檢視仍在執行中的 container ，docker stop <container id> 停止相關的 container ，docker rm <container id> 則可移除指定的 container。

## 希望的用途

1. 方便讓人不用花太多步驟也能讓人體驗各版本 BBS 站台的介面

2. 只要平台環境能裝具有完整功能的 Docker 並執行相關基本操作，即可利用此 repo 測試相關服務

## 建議事項

* **目前僅嘗試能讓測試者自用**，若無相關把握不建議用來開放外連服務，若有相關架公開站台需求者，建議仍按照各 BBS 版本文件指示自行建站。

* 查閱 https://github.com/bbslist/bbslist.github.io 可查詢你有興趣 BBS 站台是以哪個版本為基礎

## 授權 (LICENSE)

* 以下引用的範例設定檔名形式：依各專案授權方式為主
  - <BBSNAME>/<BBSNAME>.conf 
  - <BBSNAME>/config.h

* 相關腳本: [MIT License](LICENSE)

* 說明文件: [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.zh_TW)


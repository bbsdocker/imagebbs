# imagebbs: 印象。ＢＢＳ

## 如何使用

* [安裝 Docker](https://docs.docker.com)

* 執行服務

  - PttBBS: (sudo) `docker run -d -p 8888:8888 -p 8889:8889 holishing/imageptt`

  - Maple3-itoc: (sudo) `docker run -d -p 8888:8888 holishing/imageitoc`

  - Maple3-WindTop-DreamBBS: (sudo) `docker run -d -p 23:23 holishing/imagedreambbs`

  - Maple2-SOB-WindDustBBS: (sudo) `docker run -d -p 8888:8888 holishing/imagewdbbs`

* 連線至站臺：

  - 請先將終端機環境設定成 Big5 編碼，或直接用 PCMan / PCManX 連線到 telnet://127.0.0.1:8888 即可連線。

  - 僅適用 PttBBS: 在 Linux / Mac OS X 終端機下直接 `telnet 127.0.0.1 8889` 即可連線。 (UTF-8 Encoding)

### 自行建置 docker image

* [請參考此處](BUILD.md)

## 建議事項

* 若有用來開放外連服務等需求，請自行研究相關細節(如網路設定、資料儲存)或另按各 BBS 版本文件指示自行架設。

* 查閱 https://github.com/bbslist/bbslist.github.io 可查詢你有興趣 BBS 站台是以哪個版本為基礎

## 授權 (LICENSE)

* 抓取之各版本 BBS 原始碼、範例設定檔(各專案 `file/` 資料夾底下之檔案)：依各專案授權方式為主

* 相關腳本(`Dockerfile`,`Dockerfile-*`): [MIT License](LICENSE)

* 說明文件: [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.zh_TW)


# 自行建置 docker image

1. cd <指定 BBS 版本> (例：`cd pttbbs` )

2. 用 docker build 指令建立相關映像檔，並加 -t 參數自行指定像是 <你的代號/image名字> 形式的標籤名稱 (例：`sudo docker build -t yourname/localimageptt .` )

3. 等待 build 腳本執行

4. 執行你建立好的 Docker image , 測試服務！ 

執行指令形式大略是 (sudo) docker -d -p <你想要指定的port>:8888 <你的image標籤>

以 pttbbs 為例：輸入 `sudo docker run -d -p 8888:8888 yourname/localimageptt`, 然後直接 `telnet localhost 8888` 即可開始測試 (需注意終端機顯示編碼為 BIG-5 或是 UTF-8)

5. 利用 docker ps 檢視仍在執行中的 container ，docker stop <container id> 停止相關的 container ，docker rm <container id> 則可移除指定的 container。


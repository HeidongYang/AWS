# 透過OCI Cloud Shell 去連到Private網段的Linux機器

[![hackmd-github-sync-badge](https://hackmd.io/pIPIN_ZsTDaVb0UvIhMlFQ/badge)](https://hackmd.io/pIPIN_ZsTDaVb0UvIhMlFQ)


1. 打開OCI主控台的Cloud Shell
![](https://hackmd.io/_uploads/SkKV4-oA3.png)
![](https://hackmd.io/_uploads/B1NL4bsRn.png)

2. 使用 `ssh-keygen` 產生金鑰，指令如下

> ssh-keygen -t rsa -N "" -b 2048 -f "這張憑證要取的名字"

https://www.linuxcool.com/ssh-keygen

![](https://hackmd.io/_uploads/SkdpBWjR3.png)

3. 使用`cat`指令去查剛剛產生出來的公鑰資訊，並複製起來。

公鑰都是在`.pub`檔案中

![](https://hackmd.io/_uploads/ryArUWsR2.png)

4. 建instance時，在最後的`Add SSH Keys`中，選擇`Paste public keys`，並將剛剛複製的公鑰貼到底下欄位中。

貼好之後就可以Create instance了
![](https://hackmd.io/_uploads/Sy7yDWjCh.png)

5. 確認剛剛建的instance的state變成`Running`後，回到Cloud Shell中，有一欄名稱為`Network:Public`，其中旁邊有向下箭頭可以點擊，點擊出來後選擇`
Ephemeral private network setup`

![](https://hackmd.io/_uploads/ryal_Wo0n.png)

6. 出現設定的介面後，選擇你要連到哪一個VCN以及哪個Subnet，選好後點擊`Use as active network`

![](https://hackmd.io/_uploads/HJkuOZs03.png)

7. 等到剛剛的`Network:Public`變成`Network:Ephemeral`後，代表你的Cloud Shell已經跟這個Subnet同網段了

![](https://hackmd.io/_uploads/HyECdZiRh.png)

8. 透過`ssh`的指令，帶私鑰去連到剛剛建的instance中

> ssh -i "剛剛透過ssh-keygen的私鑰名稱" "Linux的帳號"@"Linux的IP"

![](https://hackmd.io/_uploads/BJfDFbsR2.png)


成功連上

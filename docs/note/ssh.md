# ssh

## 產生 ssh

[referece](https://git-scm.com/book/zh-tw/v1/%E4%BC%BA%E6%9C%8D%E5%99%A8%E4%B8%8A%E7%9A%84-Git-%E7%94%9F%E6%88%90-SSH-%E5%85%AC%E9%96%8B%E9%87%91%E9%91%B0)

```sh
ssh-keygen -t rsa -b 4096
# input password (options)
```
-t: 產生的 ssh key 類型  
-b: 產生的長度

操作手冊

```sh
man ssh-keygen
```

## 修改密碼

```sh
ssh-keygen -f id_rsa -p
# input old password
# input new password
```

## 設定 SSH 到 config

1. 先進入放 ssh 的資料夾 `~/.ssh`
    ```sh
    cd ~/.ssh
    
    # 列出檔案
    ls -a
    ```
2. 編輯 `~/.ssh/config` 檔案（如果沒有可以直接創建）
    ```sh
    # `~/.ssh` 底下
    # 創建或是編輯 config
    vim config
    ```
3. 寫入的內容如下：
    ```sh
    # Host 這裡填入想要的指令名稱
    #         Hostname IP 或是 網址
    #         User 登入的用戶名稱
    #         Port 設定的 port 預設為 22
    #         IdentityFile 檔案路徑
    Host input-name
            Hostname github.com
            User xxxxxx
            Port 22
            IdentityFile ~/path/to/id_rsa
    ```

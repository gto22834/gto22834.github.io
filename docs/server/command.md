# linux 學習

> 修改 .bash_profile 需要重新啟動 terminal

## Useful command

- User
  - `whoami`: 查詢當前用戶
  - `exit`: 離開當前使用者狀態（如果是遠端連入 server 會直接會到本地 terminal）

- File management
  - `cd $FOLDER_NAME`: change directory，移動進入資料夾
    - `cd ..`: 移動至上一次所在資料夾
  - `pwd`: 當前的路徑
  - `ls`: List all file/folder
    - `ls -la`: -l 列出檔案詳細資料；-a 列出隱藏檔案
  - `mkdir $FOLDER_NAME`: 新增資料夾
    - `mkdir a`: 在當前路徑下新增 a 資料夾
  - `touch $FILE_NAME`: 建立檔案，可加入指定位置。
    - `touch b.txt`: 在當前路徑底下創建 b.txt
    - `touch b.txt`: 在當前路徑底下創建 b.txt
  - `mv $ORI_FILE_NAME1 $TARGET_FILE_NAME2`: PATH/FILENAME(原檔案位置) 移動到 PATH/FILENAME(目的檔案位置)
    - e.q. `mv blog/post.md temporary/post.md`
  - `cp $FILE_NAME $PATH`: 複製檔案到指定的位置($PATH)。
    - e.q. `cp post.md /temporary`
  - `rm $FILE_NAME` - remove file
    - `rm -rf DIRECTORY` - remove folder
  - `file $FILE_NAME`:  檢查檔案類型
  - `find ~ -name $KEYWORD`: 尋找家目錄底下指定資料夾或檔案
    - `find ~ -name $KEYWORD -type f`: 尋找家目錄底下指定檔案
    - `find . -iname *blo* -type d`: 尋找當前目錄底下包含特定字串資料夾
    - `fine . -size +2M -type f`: 尋找當前目錄底下大於2Ｍ的檔案
    - `fine . -atime +2 -type d`: 尋找當前目錄底下超過2天沒被修改或存取的資料夾
    - `fine . -amin -40 -type f`: 尋找當前目錄底下40分鐘內有修改或存取過的檔案
    - `find ~ -name "*.php" -exec grep -H "test" {} \;`: 尋找家目錄底下的php檔，並且內容包含test字串
  - `df`: 利用df指令查詢硬碟使用量
    - `df -a`: 顯示全部的檔案系統和分割區的硬碟使用情況
    - `df -T`: 顯示每個分割區所屬的檔案系統名稱
    - `df -h`: 硬碟空間使用狀況
    - `df -m`: 大小用M來表示（預設用K表示）

- FILE check/edit
  - `cat $FILE_NAME` - 顯示指定檔案內容 (Path available)
  - `vim $FILE_NAME` - 修改指定檔案，進入編輯狀態後按「i」為插入模式，可開始編輯檔案；完成編輯按「esc」跳出插入模式，並輸入「:wq!」完成檔案儲存並離開。(Path available)

- Other
  - `clear`: 清除terminal畫面
  - `ifconfig`: 可以查詢IP、子遮罩網路及網路卡的硬體等資訊
  - `route`: 查看網路封包傳送路由狀況。
  - `netstat`: 查看網路連線狀況。
  - `ping $IP_OR_DNS`: 查看目的Domain是否有網路封包回應。
    - e.q. `ping www.google.com`

- 符號
  - `;`: 用;號隔開每個命令, 每個命令按照從左到右的順序,順序執行， 彼此之間不關心是否失敗， 所有命令都會執行。
    - e.q. command1;command2
  - `|`: 上一條命令的輸出，作為下一條命令參數
    - e.q. command1 | command2

### 查看指令文檔

決大部分的查看方式有兩種:  

1. 透過 `man`

e.q.
```sh
man docsify
```

2. 透過 `-h, --help`

```sh
docsify --help
```

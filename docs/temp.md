https://軒.net/note/lang/bash/loop

TODO：
VuePress

程序员之心
https://github.com/stanzhai/be-a-professional-programmer

tmux
https://www.cnblogs.com/lizhang4/p/7325086.html

# git alias
alias.co=checkout
alias.ci=commit -v
alias.st=status
alias.br=branch
alias.lo=log --oneline --all --graph --decorate

# docker ubuntu
// ubuntu image 需要的的东西要自己安装
docker run -it --rm ubuntu:18.04 bash
apt-get upgrade
apt-get install curl -y
apt-get 是 ubuntu 的 package 管理

# GCP free
https://cloud.google.com/free/docs/gcp-free-tier

# Postgre SQL
https://www.postgresql.org/docs/

# github actions
https://juejin.im/post/5be191736fb9a049de6cd463

# CI/CD
https://ithelp.ithome.com.tw/articles/10204538
https://rickhw.github.io/2018/03/20/DevOps/First-Step-To-CICD/

travis: https://enterprise.travis-ci.com/
jenkins: https://jenkins.io/
screwdriver: https://docs.screwdriver.cd/about/
github action: https://help.github.com/cn/categories/automating-your-workflow-with-github-actions

# patreon 研究

https://www.patreon.com/

# 关于排序
1. 排序問題，要有一個參數指定要排序的 field。現在是 orderField
2. 指定最多取幾筆，或是指定一頁取幾筆，limit 或是 page size, rows per page
3. 定位要取的資料範圍（類型一 index): offset 或是 page 轉換成 offset 或是 start id 找到該 row 再往後取
4. 定位要取的資料範圍(類型 2 range): >,<.<=,>=

# 资料库
id 是為了速度 uuid 是標準 unis 是方便閱讀

譬如說我有一個資料是統計到底有幾個用戶有付費
但這個資料，實際上是從某 table 記錄著所有付費紀錄 + 用戶 table 有哪些用戶，兩個算出來的
其實就是個 cache 概念
但千萬不要覺得寫的 code 很完美，算出來的都不會錯，然後反而把紀錄都給刪了，然後把 cache 那個資料為主
因為這東西，本身也可能是在同一個資料庫
以金2 為例好惹
vit 跟 hp base 可以計算出 hp
hp 就是一個 cache

# crawl
https://www.youtube.com/watch?v=jV6eHoLzD2E

RSSHub 研究

# Icomoon

使用 icon 時候記得要將 svg 顏色清除

# vscode eslint 修復

```
"eslint.workingDirectories": [
        { "mode": "auto" }
    ],
```

https://jeffwen0105.com/linux-ssh-tunneling/

# Git

註記一些 git 指令...免得自己忘了

## Log

```sh
$ git log
```

## Filter branch

可以批量操作修改文件內容或是 commit
[Reference](https://git-scm.com/docs/git-filter-branch)

批次刪除指定的檔案：

```sh
$ git filter-branch --tree-filter 'rm -rf files_to_remove' --prune-empty -f HEAD --all
```

Import parameters:
- --tree-filter: 用於修改文件列表  
- --msg-filter: 過濾 commit 訊息  
- --index-filter: 和 `--tree-filter` 很像，但速度快很多  
- --all: 針對所有分支  

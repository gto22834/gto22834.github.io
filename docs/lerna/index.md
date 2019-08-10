# Lerna

## 說在前面

最近因為專案需求，經過團隊討論後，決定把一個項目試著使用 `mono-repo` 的方式進行管理。
所謂的 `mono-repo` 簡單來說就是把專案合併為一個 repository 的管理方法，與之相對的便是 `multi-repo/poly-repo`

由於自己的個人習慣，喜歡先看比較和缺點，增進對這種概念的了解：

[Monorepos: Please don’t!](https://medium.com/@mattklein123/monorepos-please-dont-e9a279be011b)

看得不多，但是在此總結一些個人認為的優缺點

Pros:
1. 易於管理，共用的程式碼和依賴都非常清楚地陳列在一個專案裡面
2. 新進入者容易了解整個專案的架構及狀況
3. 較不容易出現冗餘的程式碼 (容易拆出共用的程式碼)
4. 易於分享專案
5. 易於程式碼風格管理 (同樣的 linter, style 設定)
6. 易於代碼搜索及理解所有專案

Cons:
1. 權限問題
2. 當專案越來越大，開發效率會大幅降低 (包括 clone, commit, testing, build ...)
3. 更動依賴及共用組件時，容易造成不可預期的問題
4. 個別專案版本不易控制

個人認為適用的場景：

對於開發這件事沒有 `銀彈`，所有的開發協同，都仰賴團隊彼此的習性和溝通，因此我認為只能從開發的時期來找出合適的 `銀彈`

> 開發初期，偏重 `速度`

早期的開發不需要講求太多的管理及權限，而且程式碼量不高，因此使用 `monorepo` 我認為只有百利而無一害，特色包括：
1. 新進人員容易了解全貌，可以在宏觀的思維底下去進行協同開發
2. 程式碼風格一致
3. 不會發生，相關 issue/bug 不知道開在哪個專案的問題
4. 可以忽略管理權限問題
5. 忽略專案版本問題

> 開發中期，偏重 `維護`

開發中期開始，為了維護方便，共用的組件會逐漸被開發出來，`monorepo` 的优势便会越来越低：
1. 為了降低個人程式碼觀念不同而造成的維護成本，建議 `拆分` 專案增加維護性
2. 引入共用 `組件/依賴` 版本控制降低犯錯率
3. 著重功能性，透過專案拆分定義每個功能的目的性

> 開發後期，偏重 `管理`

開發後期，各個開發人員的職責分配其實已經很清楚，目的性也明確， `monorepo` 及 `multirepo` 開始並存：
1. 依據公司部門逐漸拆分 `monorepo` 為目的性更為強烈的 `monorepo`
2. 在公司文化下，漸漸產生屬於公司的的共用組件，甚至框架

幾個著名專案有使用 `monorepo`：Babel, React, Angular, Ember, Meteor, Jest

## 進入正題

> Lerna is a tool that optimizes the workflow around managing multi-package repositories with git and npm.

正如一開始說的，開發沒有 `銀彈`，所有的概念都像是工具，就像 `6W分析法` 一樣， `monorepo` 和 `multirepo` 用得好就是 `銀彈`
用得不好就是 `空包彈`。

`lerna` 是我們使用的 `monorepo` 管理工具 (不要問我為什麼選這個，因為他有名)，使用方法請自行查閱:

[lerna](https://github.com/lerna/lerna)

在這邊只簡單記錄幾個會用到的 `api`

> 初始化一個 `monorepo` 項目

```sh
lerna init
```

> 添加依賴

```sh
lerna add <package>[@version] [--dev]
```

> 發佈

```sh
lerna publish

# 發佈至相對的 dist-tag
lerna publish --npm-tag=beta
```

> 執行 package 底下的 script

[command:run](https://github.com/lerna/lerna/tree/master/commands/run#readme)

```sh
lerna run <script> -- [..args]

# scope -> Run `dev` script in `my-project`
lerna run dev --scope my-project

# stream -> Output from child processes immediately
lerna run dev --scope my-project --stream
```

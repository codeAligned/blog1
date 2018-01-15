---
title: "Even Theme Setup"
date: 2018-01-14T18:13:28+08:00
draft: true
lastmod: 2018-01-14T18:13:28+08:00
tags: ["Theme", "Even"]
categories: ["Hugo"]
---

Even theme 設定筆記

<!--more-->

## Setup

## Use this theme

1. 下載 theme `git submodule add https://github.com/olOwOlo/hugo-theme-even themes/even && git submodule update`
2. 使用此 theme 所自帶的 config file `cp themes/even/exampleSite/config.toml .`

## Config file

1. 更改 `hugo` 時的 Publish directory:
    * `config.toml` 加入 `publishdir = "docs"`，讓 Github Pages 可以從此資料夾獲取資料
2. 放置 Disqus 留言板:
    * 於 [官方網站](https://disqus.com) 註冊帳號
    * 創建一個新的網站並記錄下 _disqus_shortname_
    * `config.toml` 加入 `comment = true` 和 設置 `disqusShortname = "..."`
3. 設置 googleAnalytics


## Git submodule 小記

To remove a submodule, [do](https://stackoverflow.com/questions/29850029/what-is-the-current-way-to-remove-a-git-submodule)

```bash
git submodule deinit <asubmodule>    
git rm <asubmodule>
rm -rf .git/modules/<asubmodule>
```
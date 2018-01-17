---
title: "架設 Jupyter 於 CCU 工學院電腦"
date: 2018-01-16T19:56:09+08:00
draft: false
lastmod: 2018-01-16T19:56:09+08:00
tags: ["python", "jupyter", "ssh"]
categories: ["Python"]
---

在工學院電腦架設 Jupyter 非常麻煩，經過一番研究之後，寫成筆記，希望以後大家可以方便使用！

在此先感謝 黃鈺程 隊友的 Jupyter 安裝教學，看來我 python 真的用得太少，連這基本的 environment 都不會架...

## 安裝 miniconda 和 jupyter

* [下載](https://conda.io/miniconda.html) miniconda 並且安裝
    * 可以直接將下載網址`wget`一下

```
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
chmod +x [filename]
./[filename]
```

* `conda create -n tt python=3.6`
* `source activate tt`
* `pip install jupyter`: 安裝 Jupyter 
* 設定 Jupyter，請參考[隊友的教學](https://amoshyc.github.io/blog/zai-yuan-duan-de-yun-suan-dian-nao-jia-she-jupyter.html#start-jupyter)，或是[官方文件](http://jupyter-notebook.readthedocs.io/en/latest/public_server.html)
    * 執行 `python3` 生成 hashed password，並複製$sha1$代碼

```python
from notebook.auth import passwd
passwd("[your desired password]")
```

* 產生與修改設定檔案
    * `jupyter notebook --generate-config`
    * 記得用 `netstat -ntulp` 先找一個沒人用的 port 喔！

```
c.NotebookApp.ip = '*'
c.NotebookApp.password = 'sha1:xxxxxxx' # paste the sha1 code you generated
c.NotebookApp.open_browser = False
c.NotebookApp.port = 50507
```

* 執行 Jupyter `nohup jupyter notebook &`
    * kill: `kill $(pgrep jupyter)`

## SSH Tunnel

* 工學院電腦 `port 50507` $\leftrightarrow$ $csie1$ `port 50507` $\leftrightarrow$ 自己電腦 `port 50507`
* 在__工學院__電腦上執行 `ssh -NR 50507:0.0.0.0:50507 [workstation username]@csie1.cs.ccu.edu.tw`
    * 只有 `csie1.cs.ccu.edu.tw` 允許開 port
    * `ssh [user workstation username]@csie1.cs.ccu.edu.tw` 大家都懂，其實就是對於 `csie1.cs.ccu.edu.tw` 的 `port22` 開 ssh tunnel。
    * `-NR 50507:0.0.0.0:50507` （左邊是csie1上的port, 右邊是工學院電腦上的port） ，其實就是說: 我們走我們 `port 22` 的 ssh tunnel 傳輸資料，至於傳輸的資料是什麼呢？ 回想剛剛我們在工學院電腦上開 jupyter 指定資料都從 `port 50507` 進出，所以我們就把工學院電腦的 `port 50507` 進出資料都 forward 到 `csie1.cs.ccu.edu.tw` 上的 `port 50507`
* 在__自己__電腦上執行 `ssh -NL 50507:localhost:50507 [workstation username]@csie1.cs.ccu.edu.tw`
    * `-NL 50507:localhost:50507` （左邊是自己電腦上的port, 右邊是csie1上的port）
    * 開啟 chrome，網址輸入 `localhost:50507`: magic!

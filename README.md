# git-practice

* 基本介紹 GIT 簡略歷史、使用緣由、何為版本控制？
* 版本控制的邏輯說明
* Git 常用指令集介紹
* .gitignore 配置
* 分支的使用方法
* Commit 介紹及使用
* GitHub 使用方法：push, pull 實作
* GitFlow 介紹


基本介紹 GIT 簡略歷史、使用緣由、何為版本控制？
---
>### 歷史
```
最初由 Linus Torvalds 創作，於2005年以GPL授權條款釋出，目的是為了更好地管理Linux核心開發而設計。
最初由 Linus Torvalds 創作，於2005年以GPL授權條款釋出，目的是為了更好地管理Linux核心開發
而設計。
```

>### 使用緣由
```
git最初的開發動力來自於 BitKeeper 和 Monotone。git最初只是作為一個可以被其他前端（比如Cogito或Stgit）
包裝的後端而開發的，但後來git核心已經成熟到可以獨立地用作版本控制。很多被廣泛使用的軟體專案都使用 git 進行
版本控制，其中包括 Linux 核心、X.Org伺服器和OLPC核心等專案的開發流程。
git最初的開發動力來自於 BitKeeper 和 Monotone。git最初只是作為一個可以被其他前端（比如Cogito
或Stgit）包裝的後端而開發的，但後來git核心已經成熟到可以獨立地用作版本控制。很多被廣泛使用的軟體專
案都使用 git 進行版本控制，其中包括 Linux 核心、X.Org伺服器和OLPC核心等專案的開發流程。
```

>### 版本控制
```
是一種軟體工程的開發技巧，可以透過這個系統讓每位成員的軟體版本可以方便同步和維護管理（不然要用 email 或是其他工具傳送和管理
十分麻煩，尤其程式又常常會有不同版本修改的問題）。在沒有版本控制系統時，我們常會在編輯檔案前複製一個備份，或是在更新檔案後產生
許多重複檔案，非常不便且難以維護。
是一種軟體工程的開發技巧，可以透過這個系統讓每位成員的軟體版本可以方便同步和維護管理（不然要用 email 或是其他工具傳送和管理十分麻煩，尤其程式又常常會有不同版本修改的問題！）。在沒有版本控制系統時，我們常會在編輯檔案前複製一個備份，或是在更新檔案後產生許多重複檔案，非常不便且難以維護。
```

版本控制的邏輯說明
---
![](https://i.imgur.com/IFwIhoh.png)
```
Git 可以分為 Local 和 Remote 兩個環境，由於 Git 屬於分散式的版本控制系統，所以開發者可以在離線 local 環境下開發，等到
有網路時再將自己的程式推到 Remote環境或 pull 下其他開發者程式碼進行整合。在 Local 中我們又分為 working directory、
staging area和 repositories。
Git 可以分為 Local 和 Remote 兩個環境，由於 Git 屬於分散式的版本控制系統，所以開發者可以在離線 local 環境下開發，等到有網路時再將自己的程式推到 Remote環境或 pull 下其他開發者程式碼進行整合。在 Local 中我們又分為 working directory、staging area和 repositories
```
-->簡單來說，就是在要上傳的資料夾內產生git檔，接下來將檔案add到暫存區，再commit到本地端的repositories，最後push到指定的遠端repositories內。

-->當共同作業時，可能就較常會需要處理不同分支之間的merge。

Git 常用指令集介紹
---

>### config

| 指令 | 作用 |
| -------- | -------- | 
| ```git config --list```   | 查看設定    | 
| ==git config --list==   | 查看設定    | 
| -------- | -------- | 
| Text     | Text     | 
| -------- | -------- |
| Text     | Text     |

>### init / clone

| 指令 | 作用 |
| -------- | -------- | 
| ```git clone```   | 抓遠端儲存庫下來	    | 
| ```git init``` | Git 初始化 | 
| ```rm -rf .git```     | 移除 Git     | 
| ==git clone==   | 抓遠端儲存庫下來	    | 
| ==git init== | Git 初始化 | 
| ==rm -rf .git==     | 移除 Git     | 

>### remote

| 指令 | 作用 |
| -------- | -------- | 
| ```git remote add (origin) <your url>``` | 遠端連結	| 
| ```git remote set-url (origin) <your url>``` | 修改遠端連結 | 
| ```git remote remove (origin)```     | 移除遠端連結     | 
| ==git remote add (origin) <your url>== | 遠端連結	| 
| ==git remote set-url (origin) <your url>== | 修改遠端連結 | 
| ==git remote remove (origin)==     | 移除遠端連結     | 

>### 基本版本控制語法

| 指令 | 作用 |
| -------- | -------- | 
| ```git status``` | 觀看狀態	| 
| ```git add (file)``` | 新增指定檔案至暫存區 | 
| ```git add .```     | 新增所有檔案至暫存區     | 
| ```git commit -m 'message'``` | 將檔案提交至本地數據庫	| 
| ```git pull``` | 將遠端檔案合併到本地數據庫 | 
| ```git push -u (remote) (branch)```  | 將檔案推至遠端數據庫  | 
    
.gitignore 配置
---
於資料夾內新增一個新檔案，輸入```touch .gitignore``` 新增.gitignore檔，輸入```git status```查看檔案是否都存在，於此檔內新增想要被忽略的檔案，輸入```git status```查看檔案是否被git忽略。
| ==git status== | 觀看狀態	| 
| ==git add (file)== | 新增指定檔案至暫存區 | 
| ==git add .==     | 新增所有檔案至暫存區     | 
| ==git commit -m 'message'== | 將檔案提交至本地數據庫	| 
| ==git pull== | 將遠端檔案合併到本地數據庫 | 
| ==git push -u (remote) (branch)==  | 將檔案推至遠端數據庫  | 
    
.gitignore 配置
---
於資料夾內新增一個新檔案，輸入==touch .gitignore== 新增.gitignore檔，輸入==git status==查看檔案是否都存在，於此檔內新增想要被忽略的檔案，輸入==git status==查看檔案是否被git忽略。
![](https://i.imgur.com/SuxjmYz.jpg)

    
分支的使用方法
---
```git branch <branch name>``` 新增分支
    
```git push origin <branch name>``` 將分支推至遠端
![](https://i.imgur.com/bqyn7RJ.png)

```git merge --no-ff <branch name>``` 合併分支（--no-ff是合併後保留分支）
==git branch <branch name>== 新增分支
    
==git push origin <branch name>== 將分支推至遠端
![](https://i.imgur.com/bqyn7RJ.png)

==git merge --no-ff <branch name>== 合併分支（--no-ff是合併後保留分支）
    
Commit 介紹及使用
---
功能就是將暫存區的內容提交到儲存庫（Repository）保留
    
```git commit``` --> 將暫存區的檔案提交到儲存庫儲存
    
```git commit -m "msg"``` ＃ 說明這次的 commit 做啥事
    
使用 ```git status``` 追蹤狀態且提示訊息
==git commit== --> 將暫存區的檔案提交到儲存庫儲存
    
==git commit -m "msg"== ＃ 說明這次的 commit 做啥事
    
使用 ==git status== 追蹤狀態且提示訊息
    
![](https://i.imgur.com/t4cfHWJ.png)


GitHub 使用方法：push, pull 實作
---
>### push 
當commit完成後，便可push至遠端
![](https://i.imgur.com/6I56Gs9.png)

>### pull 
當協作夥伴更新遠端，便要於本地pull最新版下來
![](https://i.imgur.com/RFlhBd8.png)

GitFlow 介紹
---
主要的分支有 master、develop、hotfix、release 以及 feature 五種分支
![](https://i.imgur.com/Ra0eVbG.png)

#### Master 分支
    
>主要是用來放穩定、隨時可上線的版本。這個分支的來源只能從別的分支合併過來，開發者不會直接 Commit 到這個分支。

#### Develop 分支
>這個分支主要是所有開發的基礎分支，當要新增功能的時候，所有的 Feature 分支都是從這個分支切出去的。而 Feature 分支的功能完成後，會合併回來這個分支。

#### Hotfix 分支
>當線上產品發生緊急問題的時候，會從 Master 分支開一個 Hotfix 分支出來進行修復，Hotfix 分支修復完成之後，會合併回 Master 分支，也同時會合併一份到 Develop 分支。
(為什麼要合併回 Develop 分支？如果不這麼做，等到時候 Develop 分支完成並且合併回 Master 分支的時候，那個問題就又再次出現了。
那為什麼一開始不從 Develop 分支切出來修？因為 Develop 分支的功能可能尚在開發中，這時候切出去修再合併回 Master 分支，會更慘。)
    

#### Release 分支
>當認為 Develop 分支夠成熟了，就可以把 Develop 分支合併到 Release 分支，在這邊進行算是上線前的最後測試。測試完成後，Release 分支將會同時合併到 Master 以及 Develop 這兩個分支上。Master 分支是上線版本，而合併回 Develop 分支的目的，是因為可能在 Release 分支上還會測到並修正一些問題，所以需要跟 Develop 分支同步，免得之後的版本又再度出現同樣的問題。

#### Feature 分支
>當要開始新增功能的時候，便會使用到 Feature 分支。Feature 分支都是從 Develop 分支來的，完成之後會再併回 Develop 分支。

---
### 小組練習發送 PR
![](https://i.imgur.com/RacKVxo.png)

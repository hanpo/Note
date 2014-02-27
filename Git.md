# Git Note

2014/02/27 by Hanpo 

### 安裝Git

建議先裝 [Homebrew](http://brew.sh/) 管理套件  
用 Homebrew 安裝 Git 指令 `brew install git`

### 設定Git

`git config`的設定跟參數可以存放三個地方  

* `/etc/gitconfig` 包含給所有系統使用者的使用的Git設定。設定方式是`git config --system`  
* `~/.gitconfig` 給自己帳號用的Git設定。設定方式是`git config --global` 
* 專案目錄內的`.git/config` 僅給該專案使用

以上這三個層級，越後面的會優先於前面的設定。

* 設定名字  
`git config --global user.name "YOUR NAME"`  
* 設定信箱  
`git config --global user.email YOURMAIL`  
* 指定編輯器  
`git config --global core.editor emacs`  
* 設定合併工具  
`git config --global merge.tool vimdiff`  
* 檢視目前Git判斷所用的設定  
`git config`  
* 檢視所有設定值  
`git config --list`  
* 編輯目前帳號的設定值  
`vim ~/gitconfig`    
  
[Mosky 的 Git 設定參考](http://j.mp/mosky-gitconfig)


### 檢查Git版本

`git --version` 

### 新專案流程

######開專案

1. Open a new git repositories [github](https://github.com/).  
2. cd Local project folder,add a [.gitignore](https://github.com/github/gitignore/blob/master/Objective-C.gitignore). 

Download by wget:  
`wget "https://www.dropbox.com/s/ke5mfhzq1m0xh0a/.gitignore"`

######初始化

1. `git init`
2. `git add .`  
3. `git commit -m "first commit"`  
4. `git remote add <name> <url>` name一般用origin，url可以是本地
5. `git push -u origin master`

### 基本指令

* 觀看 git 狀態  
`git status`  

* 設定遠端  
`git remote <name> <url>`

* 查看遠端  
`git remote`

* 刪除遠端路徑  
`git remote remove <name>`

* 推出 git  
`git push <repos> <refspec>`  
<refspec> 通常是 branch 或 tag name  
如果本地(src)跟遠端名稱(dst)不一樣要再加上參數`[+]<src>[:<dst>]`  
如果本地為空的則為刪除遠端reference`:<dst>`

* 拉回專案並且合併   
`git pull <repos> <refspec>` 也等同於 `git fetch` 跟 `git merge`

* 刪除本地 branch  
先切回master `git checkout master`  
再執行刪除 `git branch -d feature/your-feature-name-here`  

* 刪除遠端 branch  
`git push origin :feature/some_awesome_feature` 

* 查看專案修改狀態  
`git diff` 

* 查看專案每次修改的記錄  
`git log` 

* 切換不同的版本  
`git checkout <commit>`  
<commit>是log裡的那一串數字你可以複製或只打前幾碼，另一個比較特別的是參數是HEAD，他代表目前版本(動態的)

* 使用 tag 作為 commit name  
`git tag <tagname>`  
你可以將切到某個版本`git checkout 98f9s8`，然後設定tag`git tag v0.1`，以後要切換這版只要用`git checkout v0.1`  

* 查看有哪些 tag  
`git tag` 

* 用reset回復commit  
`git reset <commit>`  
把你現在的位置即HEAD指到<commit>去(其實沒刪)，然後打 `git checkout -- <file>` 拋棄修改  
 
* 用revert回復commit  
`git revert <commit>`  
做一個跟commit相反的動作回復，會出現在log裡

* 刪除 git local repository  
`rm -rf .git`

* 建立空的git（可以做本地實驗的remote repository） 
`git init -bare`

* 修改 remote url  
`git remote set-url origin git://new.url.here`

* 強推，即利用強覆蓋方式  
`git push -f`

- - -

### git flow(開feature branch)
  
* `git checkout -b develop`  
*新開branch並切換過去* 
  
* `git flow init`  
  
* `git flow feature start change-navigationBar-color`  
*新開feature branch並切換過去*  

* `Edit your project`

* `gitx`

      stage拖拉Unstaged Changes檔案至Stage Changes撰寫Commit Message並Commit
      等同於git add filename然後git commit -m "message"
  
* `git flow feature finish change-navigationBar-color`  
*結束feature branch並跟develop做merge，最後切換到develop，如果加上-p直接push出去，-k保留分支*  
  
* `git push origin develop`  

- - -

### 更新submodule

* `git submodule init` 

* `git submodule sync` 

* `git submodule update` 

- - -

### 終端機下新增檔案

* `touch filename`

### 編輯檔案

* `open filename`

### 終端機下新增/編輯檔案

* 指令為`vi fileName`

* vi 有二種主要的操作模式, `ESC` 鍵為單向的切換鍵(由本文輸入模式回到編輯命令模式)

* 編輯命令模式 : 要 vi 做一些特定目的的動作. 如插入,附加,取代,修改,刪除,移動游標,搜尋等等. 若是存檔等動作, 則需在命令列中下達, 欲切換至命令列, 需先按 `:`

* 本文輸入模式 : 在此模式下, 任何字元, 皆被視為輸入的資料.

* commond模式下(不在命令列使用) **刪除整行** `dd` 

* commond模式下 **離開** `q`

* commond模式下 **存檔離開** `wq`

* commond模式下 **放棄離開** `q!`

* commond模式下 **在Vi中開啟檔案** `:e fileName`


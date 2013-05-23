# Git學習筆記

2011/11/15 by Hanpo 

### 基本指令 - 建立一個新的repository

1. Open a new git repositories [github](https://github.com/).  
2. cd Local project folder,add a [.gitignore](https://gist.github.com/1241699).  
Here's .gitignore content link:   

https://github.com/github/gitignore/blob/master/Objective-C.gitignore

3. git init
4. git add .  
5. git commit -m "first commit"  
6. git remote add origin *YourGitLink*  
7. git push -u origin master

- - -
 
### 修改 remote url
git remote set-url origin git://new.url.here

- - -

### 終端機下新增檔案

* 指令為`vi fileName`

* vi 有二種主要的操作模式, `ESC` 鍵為單向的切換鍵(由本文輸入模式回到編輯命令模式)

* 編輯命令模式 : 要 vi 做一些特定目的的動作. 如插入,附加,取代,修改,刪除,移動游標,搜尋等等. 若是存檔等動作, 則需在命令列中下達, 欲切換至命令列, 需先按 `:`

* 本文輸入模式 : 在此模式下, 任何字元, 皆被視為輸入的資料.

* commond模式下(不在命令列使用) **刪除整行** `dd` 

* commond模式下 **離開** `q`

* commond模式下 **存檔離開** `wq`

* commond模式下 **放棄離開** `q!`

* commond模式下 **在Vi中開啟檔案** `:e fileName`

- - -

### git flow(開feature branch)
  
* git checkout -b develop  
*新開branch並切換過去* 
  
* git flow init  
  
* git flow feature start change-navigationBar-color  
*新開feature branch並切換過去*  

* Edit your project

* gitx

      stage拖拉Unstaged Changes檔案至Stage Changes撰寫Commit Message並Commit
      等同於git add filename然後git commit -m "message"
  
* git flow feature finish change-navigationBar-color  
*結束feature branch並跟develop做merge，最後切換到develop，如果加上-p直接push出去，-k保留分支*  
  
* git push origin develop  

- - -

### 更新submodule

* git submodule init 

* git submodule sync 

* git submodule update 




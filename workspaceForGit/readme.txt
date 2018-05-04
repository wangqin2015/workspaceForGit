参考
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013743256916071d599b3aed534aaab22a0db6c4e07fd0000
This is a git respority test!
一、基础
1、初始化一个Git repository：
	git init;
2、添加文件到git仓库：
	git add <file>						//可以添加多个文件
	git commit -m "说明"
3、随时查看工作区状态：
	git status
		若文件被修改，用git diff
4、提交日志
	git log								//从最近到最远的提交日志
	git log --pretty=oneline			//如果嫌输出信息太多，看得眼花缭乱的，可以试试加上--pretty=oneline参数
5、回退到上一个版本
	git reset --hard HEAD^				//上一个版本就是HEAD^，上上一个版本就是HEAD^^，
										//当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
6、查看命令记录
	git reflog							//可以查看对应版本ID
7、根据ID回到任意版本
	git reset --hard <ID>		
8、查看当前版本内容
	cat <file>
9、撤销修改
	场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
	场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，
			分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。
	场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节（git reset ID），不过前提是没有推送到远程库。
10、删除文件
	版本库删除：rm file
	工作区和版本库删除：git rm file
	删错了：git checout --file 			//用版本库的版本替换工作区的版本
	
二、远程仓库
1、git与github
2、添加远程库
	要关联一个远程库，使用命令git remote add origin git@github.com:wangqin2015/workspaceForGit.git
	关联后，使用命令git push -u origin master第一次推送master分支的所有内容；
	此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；
3、从远程库克隆
	git clone git@github:wangqin2015/workspaceForGit.git
或	git clone https://github.com/wangqin2015/workspaceForGit.git
三、分支管理
1、创建分支
	git checkout -b <name>				//创建并切换分支
=	git branch <name>					//创建分支
	git checkout <name>					//切换分支
2、查看当前分支
	git branch
3、切换分支
	git checkout master
4、合并分支
	git merge <name>					//合并某分支到当前分支（主分支）
5、删除分支
	git branch -d <name>
6、分支管理策略
	通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。
	如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。
	下面我们实战一下--no-ff方式的git merge：
	a、创建并且换分支：
		git checkout -b workspaceFromWangqin
	b、修改并提交文件：
		git add file
		git commit -m "注释"
	c、切换回master： 	
		git checkout master
	d、合并分支并创建新的commit：		
		git merge --no-ff -m "merge with no-ff" workspaceFromWangqin 	//--no-ff表示禁用Fast forward
7、主分支发布版本，团队合作分支进行工作
	git merge --no-ff -m "merge with no-ff" workspaceFromWangqin 		//--no-ff表示禁用Fast forward
8、BUG分支
	软件开发中，bug就像家常便饭一样。有了bug就需要修复，在Git中，由于分支是如此的强大，所以，每个bug都可以通过一个新的临时分支来修复，修复后，合并分支，然后将临时分支删除。
	当你接到一个修复一个代号101的bug的任务时，很自然地，你想创建一个分支issue-101来修复它，但是，等等，当前正在dev上进行的工作还没有提交：
	并不是你不想提交，而是工作只进行到一半，还没法提交，预计完成还需1天时间。但是，必须在两个小时内修复该bug，怎么办？
	git stash 							//把当前工作现场“储藏”起来，等以后恢复现场后继续工作


	
	
	
	
	
	
	
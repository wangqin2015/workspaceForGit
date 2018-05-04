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
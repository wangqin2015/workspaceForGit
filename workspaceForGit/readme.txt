This is a git respority test!
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
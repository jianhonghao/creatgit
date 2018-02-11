安装git：

创建版本库：
注意：将一个文件放到git仓库中只需要两步：
	文件一定要放到git目录下（子目录也行），因为这是一个Git仓库，放到其他地方Git再厉害也找不到这个文件。
		第一步：使用命令  git add 告诉Git，把文件添加到仓库： eg ：git add **.txt
		第二步： 使用git commit 告诉Git ，把文件提交到仓库： eg： git commit -m “worte a readme file”
	简单解释一下git commit命令，-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，
	这样你就能从历史记录里方便地找到改动记录。	
	为什么Git添加文件需要add，commit一共两步呢？因为commit可以一次提交很多文件，所以你可以多次add不同的文件，比如：
		$ git add file1.txt
		$ git add file2.txt file3.txt
		$ git commit -m "add 3 files."
	
		
建议你下载Notepad++代替记事本，不但功能强大，而且免费！
记得把Notepad++的默认编码设置为UTF-8 without BOM即可

时光穿梭机：
	使用 git status 命令查看当前的结果
	git status命令可以让我们时刻掌握仓库当前的状态，上面的命令告诉我们，readme.txt被修改过了，但还没有准备提交的修改。
	第一天上班时，已经记不清上次怎么修改的readme.txt，所以，需要用git diff这个命令看看：
	git diff readme.txt 
	
   版本回退：
在实际工作中，我们脑子里怎么可能记得一个几千行的文件每次都改了什么内容，不然要版本控制系统干什么。版本控制系统肯定有某个命令可以告诉我们历史记录，在Git中，我们用git log命令查看：
git log命令显示从最近到最远的提交日志，我们可以看到3次提交，最近的一次是append GPL，上一次是add distributed，最早的一次是wrote a readme file。
如果嫌输出信息太多，看得眼花缭乱的，可以试试加上--pretty=oneline参数：
   
   
   现在我们启动时光穿梭机，准备把readme.txt回退到上一个版本，也就是“add distributed”的那个版本，怎么做呢？
首先，Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，也就是最新的提交3628164...882e1e0（注意我的提交ID和你的肯定不一样），上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
	现在，我们要把当前版本“append GPL”回退到上一个版本“add distributed”，就可以使用git reset命令：
	
最新的那个版本append GPL已经看不到了！好比你从21世纪坐时光穿梭机来到了19世纪，想再回去已经回不去了，肿么办？

办法其实还是有的，只要上面的命令行窗口还没有被关掉，你就可以顺着往上找啊找啊，找到那个append GPL的commit id是3628164...，于是就可以指定回到未来的某个版本：
git reset --hard 3628164
版本号没必要写全，前几位就可以了，Git会自动去找。当然也不能只写前一两位，因为Git可能会找到多个版本号，就无法确定是哪一个了。


现在，你回退到了某个版本，关掉了电脑，第二天早上就后悔了，想恢复到新版本怎么办？找不到新版本的commit id怎么办？
在Git中，总是有后悔药可以吃的。当你用$ git reset --hard HEAD^回退到add distributed版本时，再想恢复到append GPL，就必须找到append GPL的commit id。Git提供了一个命令git reflog用来记录你的每一次命令：

理解工作区和暂存区：
	工作区（Working Directory）
	就是你在电脑里能看到的目录，比如我的learngit文件夹就是一个工作区：

	版本库（Repository）
		工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。
		Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。


		
更多详情可以去查看廖雪峰的官方网站：https://www.liaoxuefeng.com

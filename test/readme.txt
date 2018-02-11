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

git diff readme.txt 查看对readme.txt做了上面修改

> https://segmentfault.com/a/1190000003728094

git log --pretty=oneline 如果嫌输出信息太多，看得眼花缭乱，试试加上--pretty=oneline参数
git reset --hard HEAD^ 会回退到上一个版本,也就是回退到上一次commit的版本，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100
vim readme.txt 可以看到此时的readme.txt文件就是版本2时候的内容，回退成功！
git reset --hard 3628164 通过命令行上的历史信息（假如你没清屏的话），找到版本3的版本号，不一定要全部的版本号，就像这个命令的例子，只要前面的约7、8位这样就可以指定回到版本3
git reflog 记录每一次命令

撤销修改

1. 未add 未commit
git checkout -- readme.txt 撤销修改，让这个文件回到最近一次git commit或git add时的状态

2. 已add, 未commit

git reset HEAD readme.txt 可以把暂存区的修改撤销掉，重新放回工作区。git reset命令既可以回退版本，也可以把暂存区的修改回退到工作区。当我们用HEAD时，表示最新的版本。
再git checkout -- readme.txt


删除文件

1. git rm test.txt，然后git commit 文件就从版本库中删除了

2. 删错 git checkout -- test.txt

强推
当神坑队友把乱七八糟的代码push到远程分支时，本地可以回滚到自己指定的分支，然后
```js
git push -f origin dev2
```

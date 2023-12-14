# git push -u origin main

+ Pushes the local 'main' branch to the 'main' branch on the remote repository (origin).
+ Sets up tracking so that your local 'main' branch will track the 'main' branch on the remote repository.

# git branch -u origin/main
+ This command sets up tracking for the current branch to track the 'main' branch on the 'origin' remote

# git remote -v
+ 检查当前的远程仓库配置，并确认是否已经存在名为 "origin" 的远程仓库.如果 "origin" 已经存在，你可以选择更改远程仓库的 URL，或者删除 "origin"，然后重新添加。以下是两种方法：
  - 方法一：更改远程仓库 URL
    - git remote set-url origin &lt;**new-url**&gt;, 用 **new-url** 替换为你的新远程仓库 URL。
  - 方法二：删除并重新添加远程仓库
    - git remote remove origin
    - git remote add origin &lt;**repository-url**&gt;

+ **Note** 以上命令中的 &lt;**repository-url**&gt;是你远程仓库的地址。你可以在 GitHub 或其他 Git 托管服务中找到这个地址。
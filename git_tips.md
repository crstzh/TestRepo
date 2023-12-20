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

# git remote add origin
+ [git remote add] (https://github.com/username/repo.git)
+ Here, &lt;**remote-name**&gt; is a short alias for the remote repository, and &lt;**remote-url**&gt; is the URL of the remote repository. After you have added a remote, you can use the remote name to refer to the repository in various Git commands, such as fetching changes from the remote or pushing changes to it.


# git pull origin master
**git pull origin master**
+ Fetching changes from a remote repository (origin in this case) 
+ Merging those changes into the current branch (master in this case).

# 创建版本库
makedir **learngit**
cd **learngit**
pwd


# 初始化版本库
- git init
## Initialized empty Git repository in /Users/michael/learngit/.git/

 - **git add** readme.txt
 - **git commit -m "readme file"** readme.txt
 


 # Code Review
 + 创建分支： 在本地仓库中创建一个新的分支，进行你的代码修改。
 + 进行代码修改： 在新的分支上进行你的代码修改，确保完成后进行提交。
 + 推送分支： 将新的分支推送到远程仓库。
 + 在 GitHub 上创建 Pull Request： 在 GitHub 界面上找到你推送的分支，点击创建 Pull Request 按钮。填写相关信息，包括标题、描述、关联的问题等。
 + 请求审阅： 在 Pull Request 页面中，点击 "Reviewers" 选项，请求特定的团队成员对你的代码进行审阅。
 + 审阅代码： 选定的审阅者将会收到通知，然后他们可以在 Pull Request 页面中查看你的代码更改，提出评论，提出问题，建议修改等。
 + 讨论和修改： 进行代码审查后，你和审阅者之间可以在 Pull Request 页面上进行讨论，并根据反馈进行代码修改。这个过程可能涉及多次提交和讨论。
 + 合并 Pull Request： 一旦代码审查通过，你可以在 GitHub 上点击 "Merge" 按钮，将你的代码合并到主分支或目标分支中。
 + 删除分支（可选）： 如果你愿意，可以删除已合并的分支。


 # Pull Request
Pull Request（PR）是协作式开发中使用的一种机制，主要用于在分布式版本控制系统中（例如 GitHub、GitLab、Bitbucket）请求其他开发者或团队合并你的代码更改。
基本流程如下：
+ 创建分支： 在你的本地仓库中创建一个新的分支，并在该分支上进行代码修改
    * git checkout -b feature-branch
+ 提交更改： 在新的分支上进行代码修改，然后提交到该分支。
    * git add .
    * git commit -m "Your commit message"
+ 推送分支： 将新的分支推送到远程仓库。
    * git push origin feature-branch
+ 创建 Pull Request： 在远程仓库界面上，找到你推送的分支，通常会有一个创建 Pull Request 的按钮。点击该按钮，填写 Pull Request 的相关信息，包括标题、描述等。
+ 等待审核： 你的 Pull Request 现在会出现在仓库的 Pull Request 列表中，其他开发者可以查看你的代码更改、提出建议，并最终决定是否合并
+ 合并 Pull Request： 如果审核通过，仓库维护者或合作者可以选择合并（merge）你的 Pull Request。这会将你的更改合并到主分支或目标分支中。
+ 删除分支（可选）： 如果你愿意，可以删除已合并的分支。


# Actions
GitHub Actions 是 GitHub 提供的一项功能，它允许你在代码仓库中设置自动化的工作流程，其中包括执行单元测试。以下是如何使用 GitHub Actions 进行单元测试的基本步骤：
+ 创建测试脚本： 在你的代码仓库中，确保已经编写了单元测试，并创建一个脚本来运行这些测试。通常，测试脚本会使用测试框架（例如JUnit、pytest、Mocha等）来执行测试。
    ```
        name: Unit Tests

        on: [push, pull_request]

        jobs:
          test:
            runs-on: ubuntu-latest

            steps:
            - name: Checkout code
              uses: actions/checkout@v2

            - name: Set up Node.js
              uses: actions/setup-node@v3
              with:
                node-version: 14

            - name: Install dependencies
              run: npm install

            - name: Run tests
              run: npm test
    ```
+ 在仓库中创建 GitHub Actions 工作流程： 在仓库的 .github/workflows 目录下创建一个 YAML 文件，例如 .github/workflows/test.yml。这个文件将包含定义你的测试工作流程的配置。
+ 提交并推送到 GitHub： 将修改的代码和新的 GitHub Actions 配置文件提交到你的代码仓库，并推送到 GitHub。
+ 触发工作流程： GitHub Actions 工作流程将会在每次推送或拉取请求时触发。你也可以手动触发它
+ 查看结果： 进入 GitHub 仓库的 "Actions" 标签页，你将看到运行的工作流程。点击进入工作流程，查看单元测试运行的输出和结果。
+ GitHub Actions 提供了一个强大的平台，允许你根据项目的需要设置自定义的 CI/CD 流程。你可以在工作流程中包括多个步骤，例如构建、测试、部署等。

# GitLab使用流程与规范
本文档基于Idea与Git Bash，用于避免Git分支混乱与代码冲突

> 目录
* [总体流程与要求](#总体流程与要求)
* [具体流程](#具体流程)
* [注意事项](#注意事项)
* [配置工程人员权限](#配置工程人员权限)
* [新建分支与合并分支（基于Idea)](#新建分支与合并分支)   
    
    

## 总体流程与要求
分支分为Master与Develop，两者均应进行Protect并保证Master以上的权限，从而避免Developer对这两个分支的更改。

Master主要用于构建稳定版本与发布，Develop分支用于日常开发。

日常开发均从Develop Clone 新的Branch，在新分支上进行开发。

完成相关功能后，首先需要先Pull远程仓库，与其他人代码进行合并，以免出现其他人修改后的文件被覆盖等文件冲突问题。

Push当前分支

与Develop分支发起Merge Request。

应由特定人员对Merge Request进行审核，通过后与Develop分支进行合并，并进行测试，确保稳定无误后再与Master分支合并。



## 具体流程
> Git Bash版本（不推荐，因为对具体文件的控制不方便）
* 切换到目标目录
    >Cd YourDirectory
* 克隆项目
    >git clone Project SSH Path
* 切换到Develop分支
    >git ckeckout developer 
* 新建本地分支
    >git checkout -b YourBranchName
* 进行开发

* 添加文件
    >git add -A
* 保存到本地仓库
    >git commit -m 'Commit Comment'
* 拉取远程仓库代码
    >git pull origin Develop
* 解决文件冲突（如果有的话）

* 提交到远程仓库
    >git push origin BranchName
* 在Gitlab页面对该分支发起Merge Request，traget branch选择Develop

>Idea版本
* 克隆项目
    >File->New->Project From Version Control->Git
    URL填写项目SSH地址，目录选择本地目录
* 切换到Develop分支
    >右下角Git:Master，点击选择Remote Branches/origin/Develop->CheckoutAs->Develop
    >右下角变为Git:Develop代表切换成功
* 新建本地分支
    >右下角Git:Develop->New Branch,输入分支名字（以NewBranch为例）
    >右下角变为Git:NewBranch代表切换成功
* 进行开发

* 添加文件
    >项目右键->Git->Add
* 保存到本地仓库
    >项目右键->Git->Commit Directory
    >填写说明
    >注意Commit的文件，请不要添加没必要的文件
* 拉取远程仓库代码
    >项目右键->Git->Repository->Pull
    >选择对应分支，然后Pull
* 解决文件冲突（如果有的话）

* 提交到远程仓库
    >项目右键->Git->Repository->Push
    >注意Push的分支，应为新建的分支
* 在Gitlab页面对该分支发起Merge Request，traget branch选择Develop


## 注意事项    
1、如果多人协作同一功能模块，应使用同一远程分支，而不要各自建立本地分支。
2、提交说明中应包含“操作者”+“操作内容”。
3、请不要提交.idea目录，请不要提交编译输出的结果文件。

## 其他问题
建议建立一个单独的分支用于日常琐碎问题的开发与修复，或者直接使用Develop分支。

仅重大功能或模块再建立新分支。



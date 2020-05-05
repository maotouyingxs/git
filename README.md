# git
## 一、git 命令基本操作

本地库初始化：git init

设置签名：

- 项目级别/仓库级别：仅在当前本地库范围内有效
  - git config user.name tom_pro
  - git config user.email good_Pro@qq.com
  - 信息保存的位置 ：./.git/config 文件
- 系统用户级别：登录当前操作系统的用户范围
  - git config --global 
  - git config --global user.email good_Pro@qq.com
  - 信息保存的位置：~/.getconfig 文件
- 级别优先级
  - 就近原则：项目级别优先于系统级别，二者都有时采用项目级别的签名

1. 查看状态

```
    git satus
```

1. 添加

```
    git add [file name]
```

```
将工作区的 “新建、修改” 添加到暂存区
```

1. 提交

```
    git commit -m "commit message" [file name ]
```

```
将暂存区的内容提交到本地仓库
```

1. 查看历史记录

```
    git log
    git log --pretty=oneline
    git log --oneline
    git reflog
```

```
HEAD@{移动到当前版本需要多少步}
```

1. 前进后退

- 基于索引值操作【推荐】

```
    git reset --hard [局部索引值]
```

- 使用 ^ 符号 ：只能后退(一个符合退一步，N 个后退 N 步)

```
    git reset --hard HEAD^
```

- 使用 ~ 符号：只能后退（n 表示后退 n 步）

```
    git reset --har HEAD~n
```

1. reset 命令的三个参数对比

- --soft 参数
  - 仅仅在本地库移动 HEAD 指针
- --mixed 参数
  - 在本地库移动 HEAD 指针 
  - 重置暂存区
- --hard 参数
  - 在本地库移动 HEAD 指针
  - 重置暂存区
  - 重置工作区

1. 删除文件并找回

- 前提：删除前，文件存在是的状态提交到了本地库
- 操作：git reset --hard [指针位置]

1. 比较文件

```
    git diff [文件名]
```

- 将工作区的文件和暂存区进行比较

```
    git diff [本地库中历史版本][文件名]
```

- 将工作区中的文件和本地库历史记录比较


- 不带文件名，比较多个文件。 

## 二、分支管理

- 什么是分支？

  在版本控制过程中，使用多条线同时推进多个任务。

![image](C:\Users\maotouying\Desktop\笔记\图片\git分支.png)



- 分支的好处？
- - 同时并行推进多个功能开发，提高开发效率。
  - 各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响。
    ​


- 分支操作

- - 创建分支

  ​        git branch [分支名]

  - 查看分支

  ​        git branch -v

  - 切换分支

  ​         git chechout [分支名]

  - 合并分支

  - - 第一步： 切换到接受修改的分支（被合并，增加新内容）上

    ​        git chechout [被合并分支名]

    - 第二步：执行 merge 命令

    ​        git merge [有新内容分支名]

  - 解决冲突

  ![image](C:\Users\maotouying\Desktop\笔记\图片\git分支冲突.png) 

  - - 第一步：编辑文件，删除特殊符号
    - 第二步：把文件修改到满意的程度，保存退出。
    - 第三步： git add [文件名]
    - 第四步： git commit -m "日志信息"
    - - 注意：此时 commit 一定不能带具体文件名




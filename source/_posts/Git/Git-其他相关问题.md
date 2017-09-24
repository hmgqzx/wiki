---
title: Git 其他常见相关问题
toc: true
---

## Github 等远程仓库的相关问题

### 将已存在的项目通过 Git 传到 GitHub 等

主要步骤概括起来就是：

- 对该已存在的本地项目 `git init`
- 对需要的文件进行提交（如有需要，可以编辑 `.gitignore` 文件、进行多次小提交等操作）
- 关联 `remote repository` （远程仓库）
- push 本地改动到 `remote repository` （远程仓库）

更详细的具体命令，请参考：[^1][^2]



## 参考

[^1]: [Adding an existing project to GitHub using the command line - User Documentation](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/)
[^2]: [如何将一个已存在的目录转换为一个 Git 项目并托管到 GitHub 仓库 - Leon's scribble.](http://leonshi.com/2016/02/01/add-existing-project-to-github/)
# git 如何上传大文件

> Git Large File Storage (Git LFS) is an open source extension to Git that allows you to work with large files the same way as other text files.

[https://git-lfs.github.com/](https://git-lfs.github.com/)

### 安装

#### GitHub release

[https://github.com/git-lfs/git-lfs/releases](https://github.com/git-lfs/git-lfs/releases)

#### macOS

```shell
brew install git-lfs
or 
port install git-lfs
```

#### Linux

下载好二进制文件之后，解压

```
./install.sh
git lfs install
```

### 用法

```
git lfs track "*.psd"
```

下一步很关键，一定要先提交 `.gitattributes` 文件，push 到远程分支，然后再 `add` 大文件

```
git add .gitattributes
git commit -m "track *.psd files using Git LFS"
git push origin master
```

```
git add my.psd
git commit -m 'add psd'
git push origin master
```

### 如果已经 commit 了大文件怎么办

可以回退到还没有 `add` 大文件的版本

```shell
# 回退一个版本
git reset HEAD^
# 回退两个版本
git reset HEAD^^
# 回退 n 个版本
git reset HEAD~2
# 回退到指定版本
git reset hashcode
```

如果你初始化之后第一次 `commit` 就添加了大文件，估计不太好解决了，可以把 `.git` 文件夹删除，再重新初始化吧。
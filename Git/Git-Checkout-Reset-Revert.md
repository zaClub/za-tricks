## Git 仓库组成

![](http://upload-images.jianshu.io/upload_images/2351420-ebf844562b749fca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 工作区：我们编写代码的地方
- 暂存区：执行 `add` 命令后将代码加入到 **暂存区**
- 提交历史：执行 `commit` 命令后将暂存区的修改提交到 **提交历史**

## reset、checkout、revert 的主要区别

> reset 和 checkout 可对**文件层面**的更改操作，也可对**提交层面**的更改操作，而 revert 只能够对对**提交层面**的更改操作

|      命令      |  文件层面常用情景   |     提交层面常用情景      |
| :----------: | :---------: | :---------------: |
|  git reset   | 将文件从缓存区中移除  | 在私有分支上舍弃一些没有提交的更改 |
| git checkout | 舍弃工作工作区中的更改 |    切换分支或查看旧版本     |
|  git revert  |      无      |    在公共分支上回滚更改     |

## 文件层面
### git reset

```bash
# 将缓存区同步到你指定的那个提交
git reset [HEAD~2] foo.js

# 最后加一点，撤销缓存区的所有更改
git reset .
```

### git checkout

```bash
# 将工作区同步到你指定的那个提交
git checkout[HEAD~2] foo.js

# 最后加一点，撤销工作区的所有更改
git checkout .
```

## 提交层面
### git reset

可通过传入几个标记来修改工作区或缓存区

- --soft – 缓存区和工作目录都不会被改变
- --mixed – 默认选项。缓存区和你指定的提交同步，但工作目录不受影响
- --hard – 缓存区和工作目录都同步到你指定的提交

### git checkout

和 `git reset` 不一样的是，`git checkout` 没有移动这些分支

- 切换到其他分支，本质上是将 HEAD 指针指向新的分支

```bash
# 将 HEAD 指针指向 hotfix 分支
git checkout hotfix
```

- 查看旧版本

```bash
# 将 HEAD 移动到前两个版本的提交
git checkout HEAD~2
```

**但要特别注意 HEAD 分离，这是非常危险的**

![](http://upload-images.jianshu.io/upload_images/2351420-684d8d98079ef520.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

比如，当前提交版本为 `2c55a13` ，此时如果执行

```bash
git checkout HEAD~1
```

![](http://upload-images.jianshu.io/upload_images/2351420-476d157534f6b035.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

那么 HEAD 指针指向了 `b5fb8c4` ，而 master 指针还是指向最新的提交，HEAD 指针此时不指向 master，就出现了 HEAD 分离，如果此时在 HEAD 指向的结点提交了更改，那么 master 指针所指向的提交就无法被找到了，所做的工作都白费了。所以，此种情况提交更改必须要创建新的分支

解决办法参考：[危险！分离头指针](https://www.jianshu.com/p/91a0f8feb45d)

### git revert

`git revert` 不会重写提交历史，而是提交一个新的版本（这个版本的状态是 **指定的版本撤销了提交** 的状态）

```bash
git revert HEAD~2
```

## 最常用

```bash
# 撤销工作区的所有更改
git checkout .

# 撤销缓存区的所有更改
git reset .

# 对提交层面的版本回退
git revert [HEAD~x]
```

## 参考
[geeeeeeeeek/git-recipes](https://github.com/geeeeeeeeek/git-recipes/wiki/5.2-%E4%BB%A3%E7%A0%81%E5%9B%9E%E6%BB%9A%EF%BC%9AReset%E3%80%81Checkout%E3%80%81Revert-%E7%9A%84%E9%80%89%E6%8B%A9)
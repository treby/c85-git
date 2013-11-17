Basic usage
======
基本的な操作を説明する。

## git init
現在のディレクトリ以下のgit管理を開始する。

```bash
% git init 
Initialized empty Git repository in /Users/treby/c85-git/.git/
```

`.git` 以下がリポジトリの実体である。

## git status
現在のワーキングツリー／ステージングの状態を確認する。

```bash
% git status
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>...\" to include in what will be committed)
#
#	README.md
#	md/
nothing added to commit but untracked files present (use "git add" to track)
```

## git add
対象ファイルをステージングに移す。

```bash
% git add .
```




## git rm
対象ファイルを削除する。
git管理に置かれているファイルを単純に削除しただけではリポジトリ上から消すことができない。

そこで `git rm` コマンドを使用することで消したという情報をステージングに移すことができる。

```bash

```



## git mv
対象ファイルを移動／名前変更する。

## git commit
ステージングにあるファイルをリポジトリに適用する。

```
% git commit -m 'Initial commit'
[master (root-commit) b08d0ef] Initial commit
 7 files changed, 125 insertions(+)
 create mode 100644 README.md
 create mode 100644 md/0_Contents.md
 create mode 100644 md/1_Introduction.md
 create mode 100644 md/2_Basic_usage.md
 create mode 100644 md/3_Remote_hosting.md
 create mode 100644 md/4_Tips.md
 create mode 100644 md/5_References.md
```

## git branch
ブランチコマンド

## git checkout
ブランチを変更する。

## git log
現在のブランチのログを表示する。

## git show
コミットごとの差分を表示する。

## git stash

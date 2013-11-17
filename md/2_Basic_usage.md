Basic usage
======
```
- の：じゃあここからは早速実際にGitを試していきましょう。
- の：Linuxは言うに及ばず、最近のMacの場合は最初からgitが入ってるからターミナル上で使えるわ。
- は：Windowsの場合はどうするのです？
- の：普通にCygwinとかでいい気がするけど、今後の課題ね。時間があったら調べましょう。
```

## git init
現在のディレクトリ以下のgit管理を開始する。

```bash
% git init 
Initialized empty Git repository in /Users/treby/c85-git/.git/
```

`.git`以下がリポジトリの実体である。

## git status
現在のワーキングツリーの状態を表示する。

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

## git diff


## git add
対象ファイルをインデックス(ステージングエリア)に移す。

```bash
% git add .
```

## git rm
ワーキングツリーとインデックスからファイルを削除する。

git管理に置かれているファイルを単純に削除しただけではリポジトリ上から消すことができない。

そこで`git rm`コマンドを使用することで消したという情報をステージングに移すことができる。

## git mv
対象ファイルを移動／名前変更する。

## git commit
ステージングにあるファイルをリポジトリに適用する。

```bash
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
ブランチをリスト表示もしくは作成もしくは削除する。

## git checkout
ブランチを変更する。

```
% git branch feature/awesome
% git checkout feature/awesome
```
上記のコマンドは
```
% git checkout -b feature/awesome
```
に置き換えることが可能である。


## git log
コミットログを表示する。

## git show
様々な種類のオブジェクト(blob, tree, tag, commit)を表示する。
オプションなしで実行するとコミットごとの差分を表示する。

## git stash
ワーキングディレクトリに加えられた変更をstashする(こっそりしまう、隠す、蓄える)。

```
- は：
- の：例えば
```

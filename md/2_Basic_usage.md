Basic usage
======
```
- の：じゃあここからは早速実際にGitを試していきましょう。
- の：Linuxは言うに及ばず、最近のMacの場合は最初からgitが入ってるからターミナル上で使えるわ。
- は：Windowsの場合はどうするのです？
- の：[Gitbash](http://git-scm.com/download/win)を導入すると良さそうね。
```

Git環境は導入できているものとして、話を進める。(Mac環境であれば、ターミナルを起動すれば使えるはず)

## git init
現在のディレクトリ以下のGit管理を開始する。

```bash
% git init
Initialized empty Git repository in /Users/treby/c85-git/.git/
```

`.git`以下がリポジトリの実体である。

具体的にはオブジェクトが入っているようなので、詳しく調べてみると面白いだろう（Referenceに細かい話が紹介されているリソースへのリンクを載せる）。

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

### Changes to be committed
コミットされる変更のことである。ここで変更とは、ファイルの作成(create)、修正(modify)、削除(delete)、名前変更(rename)などのことを指す。

### Changes not staged for commit
ステージング・エリアに上がっていない変更のことである。このままコミットを行っても、これらの変更はリポジトリに適用されない。

### Untracked files
Git管理下に置かれていないファイルのことである。


## git diff
コミットやワーキングツリー間の差分を表示する。

ステージング・エリアとワーキングツリーの差分を表示する。
```bash
% git diff
```

ステージング・エリアとコミットの差分を表示する。
```bash
% git diff --staged
```

例えば、`git add`したファイルなどを表示できる。

## git add
対象ファイルをインデックス(ステージング・エリア)に移す。

リポジトリルートから変更を全てステージング・エリアに移すには、以下のコマンドを実行すれば良い。

```bash
% git add .
```

実行前に、`git status`や`git diff`などを使って、どのような変更がステージング・エリアに移るのかを確認するよう心がけたい。

可能であれば、`git add <file>...`のようにファイル名のパスを指定すると間違いがなく確実である。

## git rm
ワーキングツリーとインデックスからファイルを削除する。

git管理に置かれているファイルを単純に削除しただけではリポジトリ上から消すことができない。

そこで`git rm`コマンドを使用することで消したという情報をステージングに移すことができる。

既に実際のファイルを消しているがリポジトリに残っている場合は、
```bash
% git rm --cached <file>...
```

のようにすれば良い。

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

ブランチを作成する。
```bash
% git branch develop
```
このコマンドにより、developブランチが作成される。

ブランチリストを表示する。
```bash
% git branch
  develop
  * master
```

## git checkout
ブランチを変更する。masterブランチからdevelopブランチに変更するには以下のようなコマンド操作をすればよい。

```bash
% git branch
  develop
  * master
% git checkout develop
Switched to branch 'develop'
% git branch
* develop
  master
```

なお、`-b`オプションを使うことでブランチの作成と変更を同時に行うことができる。すなわち、
```
% git branch feature/awesome
% git checkout feature/awesome
```
上記のコマンドは
```
% git checkout -b feature/awesome
```
に置き換えられる。

## git stash
ワーキングディレクトリに加えられた変更をstashする(こっそりしまう、隠す、蓄える)。

stashする。
```bash
% git stash
```

stashした内容を適用する。
```bash
% git stash pop
```

```
- は：git stashはどういう時に使うのです？
- の：例えばちょっと修正を入れたけれど、別の方法も試したい場合なんかに使ったりするわね。
- の：あくまで差分で保存されるから、あるブランチで一旦stashした差分を別のブランチに適用するときなどにも使えるわね。
```

## git log
コミットログを表示する。

## git show
様々な種類のオブジェクト(blob, tree, tag, commit)を表示する。
オプションなしで実行するとコミットごとの差分を表示する。

## git grep
Git管理下に置かれたファイルを検索する。現在使えていないが、将来的に使っていきたいコマンドの一つである。

Tips
======
```
- は：のどかちゃんのおかげでGitの基本が理解できた気がするのですが、やっぱり分からないところがあるのです。
- は：コマンドやそれで何ができるのかは分かるのですが、実際の開発でどう使っていけば良いのかを教えてほしいのです。
- の：そうね、確かにここまで教科書的に解説してきたけれど、それだけじゃ使えるようになるとは限らないわよね。
- の：コマンドの説明を知るだけで使えるのなら、本家のマニュアルを読めばいいという話だしね。
- は：面目ないのです……。
- の：ここからはGitを使っていて直面するであろう疑問を中心にTips形式で説明していきましょう。
```

## GitHubの機能
Contributeする上で便利なGitHubの機能。

### fork
forkボタンを押すことで、その時のリポジトリを自分のリポジトリにコピーすることができる。

### Pull Request
あるリポジトリのあるブランチに対して、コードをマージしてもらえないか依頼できる機能。
変更内容は差分としてみることができるため、ここでコードレビューをすることができる。

## Contributeの始め方
ここでは筆者がコードをコラボレーションする際にしていることを順を追って紹介する。

### 0 ユーザー情報を設定する
コミットなどに記録されるユーザー情報を設定する。

```bash
$ git config --global user.name "treby"
$ git config --global user.email treby@example.com
```

### 1 forkする
プロジェクトのGitHubページでforkボタンを押す。

### 2 ローカル環境を整える
実際に作業を始める際はオリジナルのリポジトリに`origin`、自分のリポジトリに`self`などのリモート名をつけると便利である。
`git push`などでの事故を防ぐために実務上ではオリジナルのリポジトリをあえて、`upstream`など`origin`以外の名前をつけても良いだろう。

ここで、オリジナルのリポジトリが`treby/c85-git.git`、forkしたリポジトリが`example/c85-git.git`と想定すると、
```bash
% git clone git@github.com:your-account/c85-git.git
% git remote rename origin self
% git remote add upstream git@github.com:treby/c85-git.git
```

もしくは、
```bash
% git clone git@github.com:treby/c85-git.git
% git remote add self git@github.com:example/c85-git.git
```

とすれば良いだろう。
上の`your-account`はご自身のアカウント名に読み替えてほしい。

### 3 作業用のブランチを切る
自分がいろいろソースコードをいじって遊ぶためのブランチを切ると良いだろう。

```bash
% git checkout -b feature/my_best_way
```

### 4 ソースコードの変更をコミットする
`git add`して`git commit`する。

### 5 ソースコードを更新する
本家の内容が新しくなっていることがあるので、思い立った時に行う。

```bash
% git pull --rebase origin master
```

### 6 自分のリポジトリにpushする
おおよそ以下のような感じ。

```bash
% git push self feature/my_best_way
```

### 7 Pull Requestを投げる
GitHub上で適切なところにPull Requestを投げる。

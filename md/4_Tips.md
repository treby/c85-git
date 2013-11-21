Tips
======
```
- は：のどかちゃんのおかげでGitの基本が理解できた気がするのですが、やっぱり分からないところがあるのです。
- は：GitHubにソースコードを上げる方法だったり、ブランチの命名方法だったり、どういう時に切るのかだったり。
- は：コマンドやそれで何ができるのかは分かるのですが、実際の開発でどう使っていけば良いのかを教えてほしいのです。
- の：そうね、確かにここまで教科書的に解説してきたけれど、それだけじゃ使えるようになるとは限らないわよね。
- の：コマンドの説明を知るだけで使えるのなら、本家のマニュアルを読めばいいという話だしね。
- は：面目ないのです……。
- の：ここからはGitを使っていて直面するであろう疑問を中心にTips形式で説明していきましょう。
```

## Contribute


### GitHubの機能
Contributeする上で便利なGitHubの機能。

#### fork
forkボタンを押すことで、その時のリポジトリを自分のリポジトリにコピーすることができる。

なお、実際に作業を始める際は、オリジナルのリポジトリに`origin`、自分のリポジトリに`self`などのリモート名をつけると便利。

ここで、オリジナルのリポジトリが`treby/c85-git.git`、forkしたリポジトリが`example/c85-git.git`と想定すると、
```bash
% git clone git@github.com:example/c85-git.git
% git remote rename origin self
% git remote add origin git@github.com:treby/c85-git.git
```

もしくは、
```bash
% git clone git@github.com:treby/c85-git.git
% git remote add self git@github.com:example/c85-git.git
```

とすれば良いだろう。

#### Pull Request
コードレビューの履歴を残すことができる。

### Contributeの始め方
ベストプラクティス的な。

## サブモジュール管理
`git submodule`

## ブランチのベストプラクティス
## README.md

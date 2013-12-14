Tips
======
```
- は：のどかちゃんのおかげでGitの基本が理解できた気がするのですが、やっぱり分からないところがあるのです。
- は：コマンドやそれで何ができるのかは分かるのですが、実際の開発でどう使っていけば良いのかを教えてほしいのです。
- は：GitHubにソースコードを上げる方法だったり、ブランチの命名方法だったり、どういう時に切るのかだったり。
- の：そうね、確かにここまで教科書的に解説してきたけれど、それだけじゃ使えるようになるとは限らないわよね。
- の：コマンドの説明を知るだけで使えるのなら、本家のマニュアルを読めばいいという話だしね。
- は：面目ないのです……。
- の：ここからはGitを使っていて直面するであろう疑問を中心にTips形式で説明していきましょう。
```

## GitHubの機能
Contributeする上で便利なGitHubの機能。

### Fork
Forkボタンを押すことで、その時のリポジトリを自分のリポジトリにコピーすることができる。

### Pull Request
あるリポジトリのあるブランチに対して、コードをマージしてもらえないか依頼できる機能。
変更内容は差分としてみることができるため、ここでコードレビューをすることができる。

Pull Requestを出す際にcommitを一本化すべきだという文化が一部ではあるようだ。
参考までにcommitを一つにまとめてPull Requestを投げる際のやり方を以下に示す。

まず、Pull Requestを出す先（ここではdevelopブランチ）を最新の状態に更新する。

```bash
$ git checkout develop
$ git pull --rebase origin develop
```

次にPull Request用の新しいブランチを切る。

```bash
$ git checkout -b feature/something_awesome
```

最後に実際に変更が適用されているブランチの内容を取得し、commitする。

```bash
$ git merge --squash feature/original_something_awesome
$ git commit -m 'Implemented something awesome.'
```

## Contributeの始め方
ここでは筆者がコードをコラボレーションする際にしていることを順を追って紹介する。

### 0 ユーザー情報を設定する
コミットなどに記録されるユーザー情報を設定する。

```bash
$ git config --global user.name "treby"
$ git config --global user.email treby@example.com
```

### 1 Forkする
プロジェクトのGitHubページでForkボタンを押す。

### 2 ローカル環境を整える
実際に作業を始める際はオリジナルのリポジトリに`origin`、自分のリポジトリに`self`などのリモート名をつけると便利である。
`git push`などでの事故を防ぐために実務上ではオリジナルのリポジトリをあえて、`upstream`など`origin`以外の名前をつけても良いだろう。

ここで、オリジナルのリポジトリが`treby/c85-git.git`、Forkしたリポジトリが`example/c85-git.git`と想定すると、
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

## ブランチの切り方
ブランチの切り方のベストプラクティスとして、ここでは[A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/)で紹介されているモデルを紹介する。

### メインブランチ
中央リポジトリは永遠の生涯ずっと、2つのメインブランチを保持する。

- master
- develop

originのmasterブランチの他にdevelopと呼ばれるもう一つのブランチが存在する形だ。

ここでorigin/masterは、製品として出荷可能な状態を常に反映する、ソースコードのHEADのありかであるメインブランチだと考える。

origin/developは、次のリリースのための最新の開発作業の変更を常に反映する、ソースコードのHEADのありかであるメインブランチだと考える。

developブランチのソースコードが安定し、リリースの準備ができたとき、developブランチの全ての変更はmasterブランチへマージされ、リリース番号をタグ付けされることになる。

したがって、masterへ変更がマージされるのは新しい製品がリリースされることと同義であると言える。理論的には、masterにコミットがあるときは毎回Gitのフックスクリプトで自動ビルドを行い、そしてプロダクションサーバにソフトウェアをロールアウトする。

### サポートブランチ
masterとdevelopのメインブランチのそばで、開発モデルはチームメンバ間の平行開発を助ける様々なサポートブランチを用い、機能の追跡、製品リリースの準備、製品に起きた問題を素早く修正すること、などを容易にする。メインブランチと異なり、これらのブランチは寿命が決まっており、使い終わったら最終的には削除される。

- Featureブランチ
- Releaseブランチ
- Hotfixブランチ

それぞれのブランチは特定の目的を持ち、どのブランチから分岐するか、またどのブランチへマージされるのかというのは厳密に決まっている。

技術的には、これらのブランチは特別なものではない。上記のブランチの種類はあくまで意味付けを持たせただけで、普通のGitブランチである。

#### Featureブランチ
Featureブランチはdevelopブランチから分岐し、developブランチにマージされる。ブランチ名の慣習としては、master、develop、release-\*、hotfix-\*以外なら全て使える。

Featureブランチ（もしくはTopicブランチとも呼ばれる）は今度のリリースに入る、または遠い将来のリリースに入るような新しい機能を開発するのに使われる。
ある機能を開発し始めるとき、その時点ではその機能を含めるべきリリースがどれなのか不明である。Featureブランチの本質は、機能を開発している限りは存在しているが、最後にはdevelopにマージされるか捨てられる。

Featureブランチは典型的には開発者のリポジトリにだけ存在し、originには存在しない。

#### Releaseブランチ
Releaseブランチはdevelopブランチから分岐し、developとmasterブランチにマージされる。ブランチ名の慣習としてはrelease-\*が使われる。

Releaseブランチは新しい製品リリースの準備をサポートする。リリース前のマイナーなbug fixやリリースのためのメタデータの準備までさせてくれる。これらの全ての作業をリリースブランチ上で行うことで、developブランチはきれいな状態を保つことができる。

developから新しいReleaseブランチを分岐するためのタイミングの目安としては、developブランチがおおむねリリースできる状態になっていることだ。
少なくともリリースのビルドのターゲットとされる全ての機能は、この時点でdevelopにマージされていなければならない。

#### Hotfixブランチ
Hotfixブランチはmasterから分岐し、developとmasterにマージされる。ブランチ名の慣習としては、hotfix-\*が使われる。

Hotfixブランチは現在の製品バージョンにあるクリティカルなバグを解決しなければならないときなどに使われる。

### このようにブランチを切ることで
プロジェクトの開発者で全体像を共有することができるだろう。

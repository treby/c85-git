c85-git
======

## About
エンジニアとして社会に出て8ヶ月、たまに振り落とされそうになりつつも、なんとかくらいついていけている今日この頃。<br />
まだまだ技術力的に拙い私ではあるが、日々成長している実感を持ちながら業務に取り組めていることは幸いだと思う。<br />
ことツールの使い方についてはコードに直接関係のないところとはいえ、できないと仕事にならない部分も大きい。<br />
シェル環境をはじめ、エディタやそのプラグイン、社内ツールにフレームワークなど、就職してみて自分がいかに無知だったかを思い知らされた。<br />
ここで取り扱うGitもそんなツールのうちの一つである。それまで何となく使っていたこのツールも、実務で何回も使ううちにその真価が分かり、不覚にも感動した。今回はこの感動を何らかの形に残したいという思いからキーボードを叩き始めた。

本稿は私が最低限エンジニアとしてやっていくために学んだGit/GitHubの使い方について書いたものである。
これを読んで入門者の方にGitの使い方を理解してほしいのはもちろんのこと、私自身の理解度チェックもかねて執筆している。

一つの野望として、C85で本として出したいというものがある。

## Declaration
執筆中、方針に迷わないように、本書の制作指針を設定する。

- 本稿は私がgitについて学んだことを共有するものである。
- 本稿は教科書__ではない__。読むことでgitが使えるようになるとは限らない。
- 本稿に載っている情報は必ずしも正しいとは限らない。
- 本稿ではgitの全ての機能を紹介しない。

## Target
一応の対象読者を下記のようにイメージする。

- gitを知らない人。もしくはgitを知っているが、使いこなせていない人
- GitHubを使ってみたい人
- 上記のエンジニア、もしくはそれ以外
- エンジニア新入社員

## Character
本稿に登場するマスコットキャラクターを紹介する。

### のどかたん
マスコットキャラクター(仮)。
本稿では教える側ポジション。ツインテニーソつり目系のイメージ。

### はじめちゃん
マスコットキャラクターを支える脇役。
本稿では教えられる側ポジション。なのです口調の設定。

Remote hosting
======
```
- の：Gitの基本操作を覚えたところで、今度はリモートリポジトリに対する操作を覚えましょう。
- の：Git用のホスティングサービスにGitHubというものがあるけれど、これはGitのリモートリポジトリを管理してくれるものと思ってくれていいわ。
- は：GitとGitHubって同じものだと思っていたのですが、GitはツールでGitHubはサービスなのですね。
- の：これができるようになると、最初に感じてたGitに対する障壁のようなものがなくなるんじゃないかしら。
```

## GitHubについて
[GitHubのAboutページ](https://github.com/about)には以下のようにある。

> GitHub is the best place to share code with friends, co-workers, classmates and complete strangers. Over four million people use GitHub to build amazing things together.

筆者としてはGitのリモートリポジトリを持ってくれる上に、そのリポジトリをGUIで見ることができたり、他人とコラボレートするための機能が揃っていたりするGitのホスティングサービスといった認識である。

## git clone
リポジトリを新しいディレクトリに複製する。

GitHub上などリモートにあるリポジトリをローカルに複製する時に使用することが多い。

例えば、本稿をローカルに持ってくるのであれば以下のコマンドを実行すれば良い。

```bash
% git clone git@github.com:treby/c85-git.git
```

## git submodule
リポジトリ自体が別リポジトリのコードを使用していることがある。
そのような場合、`git clone`しただけではコードが動かないといったことが起こりうる。

この現象は以下のコマンドを打つことで解決できるだろう。

```bash
% git submodule init
% git submodule update
```

## git remote
追跡中のリポジトリの管理セット。設定内容は`.git/config`ファイルに書かれているようであるが、これを直接いじるのではなくコマンドを通じて設定するのがマナーだろう。

以下のコマンドでは、登録されているリモート名一覧を表示する。
```bash
% git remote
origin
```

以下のコマンドでは、リモート登録されているものの詳細を表示する。
```bash
% git remote -v
origin  git@github.com:treby/c85-git.git (fetch)
origin  git@github.com:treby/c85-git.git (push)
```

## git fetch
他のリポジトリから参照やオブジェクトをダウンロードする。

## git merge
2つ以上の開発履歴を互いに結合する。

## git pull
`git fetch`と`git merge`を同時に行う。通常は上記の`git fetch`と`git merge`を単独に使うというよりは、`git pull`を行うことが多い(筆者の場合)。

`--rebase`オプションを用いることで、rebaseを行うことができる。

```bash
% git pull --rebase origin master
```

## git push
リモートの参照を更新する。

現在のローカルmasterブランチのリポジトリ内容をoriginに反映させるには、以下のコマンドを打てば良い。
```bash
% git push origin master
```

ちなみにpushしようとしているブランチがpush先の子孫ではない場合、pushが失敗するようになっている。

これは`-f`オプションをつけることで強制的にpushできるが、事故の元なので基本的にはやらないほうが安心だろう。

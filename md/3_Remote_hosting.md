Remote hosting
======
```
- の：Gitの基本操作を覚えたところで、今度はリモートリポジトリに対する操作を覚えましょう。
- の：Git用のホスティングサービスにGitHubというものがあるけれど、これはGitのリモートリポジトリを管理してくれるものと思ってくれていいわ。
- は：GitとGitHubって同じものだと思っていたのですが、GitはツールでGitHubはサービスなのですね。
- の：これができるようになると、最初に感じてたGitに対する障壁のようなものがなくなるんじゃないかしら。
```

## GitHubについて

## git clone
リポジトリを新しいディレクトリに複製する。

GitHub上などリモートにあるリポジトリをローカルに複製する時に使用することが多い。

```bash
% git clone git@github.com:treby/c85-git.git
Cloning into 'c85-git'...
remote: Counting objects: 24, done.
remote: Compressing objects: 100% (20/20), done.
remote: Total 24 (delta 7), reused 21 (delta 4)
Receiving objects: 100% (24/24), 7.53 KiB | 0 bytes/s, done.
Resolving deltas: 100% (7/7), done.
Checking connectivity... done
```

## git remote
追跡中のリポジトリの管理セット。設定内容は`.git/config`ファイルに書かれているようであるが、これを直接いじるのではなくコマンドを通じて設定するのがマナーだろう。

登録されているリモート名一覧を表示する。
```bash
% git remote
origin
```

リモート登録されているものの詳細を表示する。
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
`git fetch`と`git merge`を同時に行う。

`--rebase`オプションを用いることで、rebaseを行うことができる。

```bash
% git pull --rebase origin master
```

## git push
リモートの参照を更新する。
